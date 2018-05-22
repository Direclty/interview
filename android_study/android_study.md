#Android面试知识
   
## 基础

### 四大组件

   * Activity

       - 1.1 activity 启动流程
            
           - 1.1.1、大致流程
            
                <pre class="highlight"><code class="hljs coffeescript">frameworks<span class="hljs-regexp">/base/services/core/java/com/android/server/am/</span>
                  - ActivityManagerService.java
                  - ActivityStackSupervisor.java
                  - ActivityStack.java
                  - ActivityRecord.java
                  - ProcessRecord.java
                
                frameworks<span class="hljs-regexp">/base/core/java/android/app/</span>
                  - IActivityManager.java
                  - ActivityManagerNative.java (内含AMP)
                  - ActivityManager.java
                  
                  - IApplicationThread.java
                  - ApplicationThreadNative.java (内含ATP)
                  - ActivityThread.java (内含ApplicationThread)
                  
                  - ContextImpl.java
                </code></pre>
                
                <div>
                    <img src="http://gityuan.com/images/activity/start_activity.jpg" />
                </div>
                
                - 1.1.1.1、流程：
                    
                    > Activity有2种启动的方式，前者是在Launcher界面点击应用的图标、后者是在应用中通过Intent进行跳转。我们主要介绍与后者相关的启动流程。
                    
                    从Activity的startActivity()开始，这个方法会在内部调用startActivityForResult()，其中的核心代码长这样
                    
                    <pre class="highlight"><code class="hljs java"><span class="hljs-function"><span class="hljs-keyword">public</span> <span class="hljs-keyword">void</span> <span class="hljs-title">startActivity</span><span class="hljs-params">(Intent intent)</span> </span>{
                        <span class="hljs-keyword">this</span>.startActivity(intent, <span class="hljs-keyword">null</span>);
                    }
                    
                    <span class="hljs-function"><span class="hljs-keyword">public</span> <span class="hljs-keyword">void</span> <span class="hljs-title">startActivity</span><span class="hljs-params">(Intent intent, @Nullable Bundle options)</span> </span>{
                        <span class="hljs-keyword">if</span> (options != <span class="hljs-keyword">null</span>) {
                            startActivityForResult(intent, -<span class="hljs-number">1</span>, options);
                        } <span class="hljs-keyword">else</span> {
                            <span class="hljs-comment">//[见小节2.2]</span>
                            startActivityForResult(intent, -<span class="hljs-number">1</span>);
                        }
                    }
                    </code></pre>
                    
                   ####startActivityForResult：
                    
                   <pre class="highlight"><code class="hljs java"><span class="hljs-function"><span class="hljs-keyword">public</span> <span class="hljs-keyword">void</span> <span class="hljs-title">startActivityForResult</span><span class="hljs-params">(Intent intent, <span class="hljs-keyword">int</span> requestCode)</span> </span>{
                       startActivityForResult(intent, requestCode, <span class="hljs-keyword">null</span>);
                   }
                   
                   <span class="hljs-function"><span class="hljs-keyword">public</span> <span class="hljs-keyword">void</span> <span class="hljs-title">startActivityForResult</span><span class="hljs-params">(Intent intent, <span class="hljs-keyword">int</span> requestCode, @Nullable Bundle options)</span> </span>{
                       <span class="hljs-keyword">if</span> (mParent == <span class="hljs-keyword">null</span>) {
                           <span class="hljs-comment">//[见小节2.3]</span>
                         <span>//----------------------这是主要的代码----------------------------</span>
                         
                           Instrumentation.ActivityResult ar =
                               mInstrumentation.execStartActivity(
                                   <span class="hljs-keyword">this</span>, mMainThread.getApplicationThread(), mToken, <span class="hljs-keyword">this</span>,
                                   intent, requestCode, options);
                                   
                         <span>//----------------------这是主要的代码----------------------------</span>
                         
                           <span class="hljs-keyword">if</span> (ar != <span class="hljs-keyword">null</span>) {
                               mMainThread.sendActivityResult(
                                   mToken, mEmbeddedID, requestCode, ar.getResultCode(),
                                   ar.getResultData());
                           }
                           <span class="hljs-comment">//此时requestCode =-1</span>
                           <span class="hljs-keyword">if</span> (requestCode &gt;= <span class="hljs-number">0</span>) {
                               mStartedActivity = <span class="hljs-keyword">true</span>;
                           }
                           cancelInputsAndStartExitTransition(options);
                       } <span class="hljs-keyword">else</span> {
                           ...
                       }
                   }
                   </code></pre>
                   
                   ####execStartActivity()方法的参数：
                   
                     - 1、mAppThread: 数据类型为ApplicationThread，通过mMainThread.getApplicationThread()方法获取。
                   
                     - 2、mToken: 数据类型为IBinder.

                    也就是说，Activity是由mInstrumentation来启动的。查看Instrumentation类的
                    execStartActivity()
                    
                    <pre class="highlight"><code class="hljs java"><span class="hljs-function"><span class="hljs-keyword">public</span> ActivityResult <span class="hljs-title">execStartActivity</span><span class="hljs-params">(
                            Context who, IBinder contextThread, IBinder token, Activity target,
                            Intent intent, <span class="hljs-keyword">int</span> requestCode, Bundle options)</span> </span>{
                    
                        IApplicationThread whoThread = (IApplicationThread) contextThread;
                        ...
                    
                        <span class="hljs-keyword">if</span> (mActivityMonitors != <span class="hljs-keyword">null</span>) {
                            <span class="hljs-keyword">synchronized</span> (mSync) {
                                <span class="hljs-keyword">final</span> <span class="hljs-keyword">int</span> N = mActivityMonitors.size();
                                <span class="hljs-keyword">for</span> (<span class="hljs-keyword">int</span> i=<span class="hljs-number">0</span>; i&lt;N; i++) {
                                    <span class="hljs-keyword">final</span> ActivityMonitor am = mActivityMonitors.get(i);
                                    <span class="hljs-keyword">if</span> (am.match(who, <span class="hljs-keyword">null</span>, intent)) {
                                        am.mHits++;
                                        <span class="hljs-comment">//当该monitor阻塞activity启动,则直接返回</span>
                                        <span class="hljs-keyword">if</span> (am.isBlocking()) {
                                            <span class="hljs-keyword">return</span> requestCode &gt;= <span class="hljs-number">0</span> ? am.getResult() : <span class="hljs-keyword">null</span>;
                                        }
                                        <span class="hljs-keyword">break</span>;
                                    }
                                }
                            }
                        }
                        <span class="hljs-keyword">try</span> {
                            intent.migrateExtraStreamToClipData();
                            intent.prepareToLeaveProcess();
                            <span class="hljs-comment">//[见小节2.4]</span>
                        <span>//-------------------------重点代码------------------------------</span>
                            
                            <span class="hljs-keyword">int</span> result = ActivityManagerNative.getDefault()
                                .startActivity(whoThread, who.getBasePackageName(), intent,
                                        intent.resolveTypeIfNeeded(who.getContentResolver()),
                                        token, target != <span class="hljs-keyword">null</span> ? target.mEmbeddedID : <span class="hljs-keyword">null</span>,
                                        requestCode, <span class="hljs-number">0</span>, <span class="hljs-keyword">null</span>, options);
                            <span class="hljs-comment">//检查activity是否启动成功</span>
                            checkStartActivityResult(result, intent);
                            
                        <span>//-------------------------重点代码------------------------------</span>
                        } <span class="hljs-keyword">catch</span> (RemoteException e) {
                            <span class="hljs-keyword">throw</span> <span class="hljs-keyword">new</span> RuntimeException(<span class="hljs-string">"Failure from system"</span>, e);
                        }
                        <span class="hljs-keyword">return</span> <span class="hljs-keyword">null</span>;
                    }
                    </code></pre>
                    
                    关于 ActivityManagerNative.getDefault()返回的是ActivityManagerProxy对象. 此处startActivity()的共有10个参数, 下面说说每个参数传递AMP.startActivity()每一项的对应值:
                    
                    - 1、caller: 当前应用的ApplicationThread对象mAppThread;
                    
                    - 2、callingPackage: 调用当前ContextImpl.getBasePackageName(),获取当前Activity所在包名;
                    
                    - 3、intent: 这便是启动Activity时,传递过来的参数;
                    
                    - 4、resolvedType: 调用intent.resolveTypeIfNeeded而获取;
                    
                    - 5、resultTo: 来自于当前Activity.mToken
                    
                    - 6、resultWho: 来自于当前Activity.mEmbeddedID
                    
                    - 7、requestCode = -1;
                    
                    - 8、startFlags = 0;
                    
                    - 9、profilerInfo = null;
                    
                    - 10、options = null;

                   ####AMP.startActivity：
                   
                   <p>[-&gt; ActivityManagerNative.java :: ActivityManagerProxy]</p>
                    
                    <pre class="highlight"><code class="hljs java"><span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">ActivityManagerProxy</span> <span class="hljs-keyword">implements</span> <span class="hljs-title">IActivityManager</span>
                    </span>{
                        ...
                        <span class="hljs-function"><span class="hljs-keyword">public</span> <span class="hljs-keyword">int</span> <span class="hljs-title">startActivity</span><span class="hljs-params">(IApplicationThread caller, String callingPackage, Intent intent,
                                String resolvedType, IBinder resultTo, String resultWho, <span class="hljs-keyword">int</span> requestCode,
                                <span class="hljs-keyword">int</span> startFlags, ProfilerInfo profilerInfo, Bundle options)</span> <span class="hljs-keyword">throws</span> RemoteException </span>{
                            Parcel data = Parcel.obtain();
                            Parcel reply = Parcel.obtain();
                            data.writeInterfaceToken(IActivityManager.descriptor);
                            data.writeStrongBinder(caller != <span class="hljs-keyword">null</span> ? caller.asBinder() : <span class="hljs-keyword">null</span>);
                            data.writeString(callingPackage);
                            intent.writeToParcel(data, <span class="hljs-number">0</span>);
                            data.writeString(resolvedType);
                            data.writeStrongBinder(resultTo);
                            data.writeString(resultWho);
                            data.writeInt(requestCode);
                            data.writeInt(startFlags);
                            <span class="hljs-keyword">if</span> (profilerInfo != <span class="hljs-keyword">null</span>) {
                                data.writeInt(<span class="hljs-number">1</span>);
                                profilerInfo.writeToParcel(data, Parcelable.PARCELABLE_WRITE_RETURN_VALUE);
                            } <span class="hljs-keyword">else</span> {
                                data.writeInt(<span class="hljs-number">0</span>);
                            }
                            <span class="hljs-keyword">if</span> (options != <span class="hljs-keyword">null</span>) {
                                data.writeInt(<span class="hljs-number">1</span>);
                                options.writeToParcel(data, <span class="hljs-number">0</span>);
                            } <span class="hljs-keyword">else</span> {
                                data.writeInt(<span class="hljs-number">0</span>);
                            }
                            <span class="hljs-comment">//[见流程2.5]</span>
                            mRemote.transact(START_ACTIVITY_TRANSACTION, data, reply, <span class="hljs-number">0</span>);
                            reply.readException();
                            <span class="hljs-keyword">int</span> result = reply.readInt();
                            reply.recycle();
                            data.recycle();
                            <span class="hljs-keyword">return</span> result;
                        }
                        ...
                    }
                    </code></pre>
                    
                    AMP经过binder IPC,进入ActivityManagerNative(简称AMN)。接下来程序进入了system_servr进程，开始继续执行。
                    
                    ####AMN.onTransact：
                    
                    <p>[-&gt; ActivityManagerNative.java]</p>
                    
                    <pre class="highlight"><code class="hljs java"><span class="hljs-function"><span class="hljs-keyword">public</span> <span class="hljs-keyword">boolean</span> <span class="hljs-title">onTransact</span><span class="hljs-params">(<span class="hljs-keyword">int</span> code, Parcel data, Parcel reply, <span class="hljs-keyword">int</span> flags)</span>
                          <span class="hljs-keyword">throws</span> RemoteException </span>{
                        <span class="hljs-keyword">switch</span> (code) {
                        <span class="hljs-keyword">case</span> START_ACTIVITY_TRANSACTION:
                        {
                          data.enforceInterface(IActivityManager.descriptor);
                          IBinder b = data.readStrongBinder();
                          IApplicationThread app = ApplicationThreadNative.asInterface(b);
                          String callingPackage = data.readString();
                          Intent intent = Intent.CREATOR.createFromParcel(data);
                          String resolvedType = data.readString();
                          IBinder resultTo = data.readStrongBinder();
                          String resultWho = data.readString();
                          <span class="hljs-keyword">int</span> requestCode = data.readInt();
                          <span class="hljs-keyword">int</span> startFlags = data.readInt();
                          ProfilerInfo profilerInfo = data.readInt() != <span class="hljs-number">0</span>
                                  ? ProfilerInfo.CREATOR.createFromParcel(data) : <span class="hljs-keyword">null</span>;
                          Bundle options = data.readInt() != <span class="hljs-number">0</span>
                                  ? Bundle.CREATOR.createFromParcel(data) : <span class="hljs-keyword">null</span>;
                          <span class="hljs-comment">//[见流程2.6]</span>
                          <span class="hljs-keyword">int</span> result = startActivity(app, callingPackage, intent, resolvedType,
                                  resultTo, resultWho, requestCode, startFlags, profilerInfo, options);
                          reply.writeNoException();
                          reply.writeInt(result);
                          <span class="hljs-keyword">return</span> <span class="hljs-keyword">true</span>;
                        }
                        ...
                        }    }
                    </code></pre>
                    
                    ####AMS.startActivity
                    
                    <p>[-&gt; ActivityManagerService.java]</p>
                    
                    <pre class="highlight"><code class="hljs java"><span class="hljs-function"><span class="hljs-keyword">public</span> <span class="hljs-keyword">final</span> <span class="hljs-keyword">int</span> <span class="hljs-title">startActivity</span><span class="hljs-params">(IApplicationThread caller, String callingPackage,
                            Intent intent, String resolvedType, IBinder resultTo, String resultWho, <span class="hljs-keyword">int</span> requestCode,
                            <span class="hljs-keyword">int</span> startFlags, ProfilerInfo profilerInfo, Bundle options)</span> </span>{
                        <span class="hljs-keyword">return</span> startActivityAsUser(caller, callingPackage, intent, resolvedType, resultTo,
                            resultWho, requestCode, startFlags, profilerInfo, options,
                            UserHandle.getCallingUserId());
                    }
                    
                    <span class="hljs-function"><span class="hljs-keyword">public</span> <span class="hljs-keyword">final</span> <span class="hljs-keyword">int</span> <span class="hljs-title">startActivityAsUser</span><span class="hljs-params">(IApplicationThread caller, String callingPackage,
                        Intent intent, String resolvedType, IBinder resultTo, String resultWho, <span class="hljs-keyword">int</span> requestCode,
                        <span class="hljs-keyword">int</span> startFlags, ProfilerInfo profilerInfo, Bundle options, <span class="hljs-keyword">int</span> userId)</span> </span>{
                        enforceNotIsolatedCaller(<span class="hljs-string">"startActivity"</span>);
                        userId = handleIncomingUser(Binder.getCallingPid(), Binder.getCallingUid(), userId,
                                <span class="hljs-keyword">false</span>, ALLOW_FULL_ONLY, <span class="hljs-string">"startActivity"</span>, <span class="hljs-keyword">null</span>);
                        <span class="hljs-comment">//[见小节2.7]</span>
                        <span class="hljs-keyword">return</span> mStackSupervisor.startActivityMayWait(caller, -<span class="hljs-number">1</span>, callingPackage, intent,
                                resolvedType, <span class="hljs-keyword">null</span>, <span class="hljs-keyword">null</span>, resultTo, resultWho, requestCode, startFlags,
                                profilerInfo, <span class="hljs-keyword">null</span>, <span class="hljs-keyword">null</span>, options, <span class="hljs-keyword">false</span>, userId, <span class="hljs-keyword">null</span>, <span class="hljs-keyword">null</span>);
                    }
                    </code></pre>
                    
                    此处mStackSupervisor的数据类型为ActivityStackSupervisor
                    
                    ####ActivityStackSupervisor   
                        
                    > 这是一个Activity栈的管理类，其中有许多不同类型的list用来存放ActivityRecord。
                      在Android系统中，每个应用都有许多自己的栈以及相对应的Activity们，应用自己是不会管理这些仔们的生命周期的，它也管不来。每个应用所作的，就是将Activity的状态信息封装到ActivityRecord并交给系统级的服务——ActivityStackSupervisor来统一管理。因此ActivityStackSupervisor可以很轻松的获取到各种Activity。
                    
                    <p>[-&gt; ActivityStackSupervisor.java]</p>
                    
                    <pre class="highlight"><code class="hljs java"><span class="hljs-function"><span class="hljs-keyword">final</span> <span class="hljs-keyword">int</span> <span class="hljs-title">startActivityMayWait</span><span class="hljs-params">(IApplicationThread caller, <span class="hljs-keyword">int</span> callingUid,
                            String callingPackage, Intent intent, String resolvedType,
                            IVoiceInteractionSession voiceSession, IVoiceInteractor voiceInteractor,
                            IBinder resultTo, String resultWho, <span class="hljs-keyword">int</span> requestCode, <span class="hljs-keyword">int</span> startFlags,
                            ProfilerInfo profilerInfo, WaitResult outResult, Configuration config,
                            Bundle options, <span class="hljs-keyword">boolean</span> ignoreTargetSecurity, <span class="hljs-keyword">int</span> userId,
                            IActivityContainer iContainer, TaskRecord inTask)</span> </span>{
                        ...
                        <span class="hljs-keyword">boolean</span> componentSpecified = intent.getComponent() != <span class="hljs-keyword">null</span>;
                        <span class="hljs-comment">//创建新的Intent对象，即便intent被修改也不受影响</span>
                        intent = <span class="hljs-keyword">new</span> Intent(intent);
                    
                        <span class="hljs-comment">//收集Intent所指向的Activity信息, 当存在多个可供选择的Activity,则直接向用户弹出resolveActivity [见2.7.1]</span>
                        ActivityInfo aInfo = resolveActivity(intent, resolvedType, startFlags, profilerInfo, userId);
                    
                        ActivityContainer container = (ActivityContainer)iContainer;
                        <span class="hljs-keyword">synchronized</span> (mService) {
                            <span class="hljs-keyword">if</span> (container != <span class="hljs-keyword">null</span> &amp;&amp; container.mParentActivity != <span class="hljs-keyword">null</span> &amp;&amp;
                                    container.mParentActivity.state != RESUMED) {
                                ... <span class="hljs-comment">//不进入该分支, container == nul</span>
                            }
                    
                            <span class="hljs-keyword">final</span> <span class="hljs-keyword">int</span> realCallingPid = Binder.getCallingPid();
                            <span class="hljs-keyword">final</span> <span class="hljs-keyword">int</span> realCallingUid = Binder.getCallingUid();
                            <span class="hljs-keyword">int</span> callingPid;
                            <span class="hljs-keyword">if</span> (callingUid &gt;= <span class="hljs-number">0</span>) {
                                callingPid = -<span class="hljs-number">1</span>;
                            } <span class="hljs-keyword">else</span> <span class="hljs-keyword">if</span> (caller == <span class="hljs-keyword">null</span>) {
                                callingPid = realCallingPid;
                                callingUid = realCallingUid;
                            } <span class="hljs-keyword">else</span> {
                                callingPid = callingUid = -<span class="hljs-number">1</span>;
                            }
                    
                            <span class="hljs-keyword">final</span> ActivityStack stack;
                            <span class="hljs-keyword">if</span> (container == <span class="hljs-keyword">null</span> || container.mStack.isOnHomeDisplay()) {
                                stack = mFocusedStack; <span class="hljs-comment">// 进入该分支</span>
                            } <span class="hljs-keyword">else</span> {
                                stack = container.mStack;
                            }
                    
                            <span class="hljs-comment">//此时mConfigWillChange = false</span>
                            stack.mConfigWillChange = config != <span class="hljs-keyword">null</span> &amp;&amp; mService.mConfiguration.diff(config) != <span class="hljs-number">0</span>;
                    
                            <span class="hljs-keyword">final</span> <span class="hljs-keyword">long</span> origId = Binder.clearCallingIdentity();
                    
                            <span class="hljs-keyword">if</span> (aInfo != <span class="hljs-keyword">null</span> &amp;&amp;
                                    (aInfo.applicationInfo.privateFlags
                                            &amp;ApplicationInfo.PRIVATE_FLAG_CANT_SAVE_STATE) != <span class="hljs-number">0</span>) {
                                <span class="hljs-comment">// heavy-weight进程处理流程, 一般情况下不进入该分支</span>
                                <span class="hljs-keyword">if</span> (aInfo.processName.equals(aInfo.applicationInfo.packageName)) {
                                    ...
                                }
                            }
                    
                            <span class="hljs-comment">//[见流程2.8]</span>
                            <span class="hljs-keyword">int</span> res = startActivityLocked(caller, intent, resolvedType, aInfo,
                                    voiceSession, voiceInteractor, resultTo, resultWho,
                                    requestCode, callingPid, callingUid, callingPackage,
                                    realCallingPid, realCallingUid, startFlags, options, ignoreTargetSecurity,
                                    componentSpecified, <span class="hljs-keyword">null</span>, container, inTask);
                    
                            Binder.restoreCallingIdentity(origId);
                    
                            <span class="hljs-keyword">if</span> (stack.mConfigWillChange) {
                                ... <span class="hljs-comment">//不进入该分支</span>
                            }
                    
                            <span class="hljs-keyword">if</span> (outResult != <span class="hljs-keyword">null</span>) {
                                ... <span class="hljs-comment">//不进入该分支</span>
                            }
                    
                            <span class="hljs-keyword">return</span> res;
                        }
                    }
                    </code></pre>
                    
                    <pre class="hljs php"><code class="php">
                        <span class="hljs-comment">/** List of processes waiting to find out about the next visible activity. */</span>
                        <span class="hljs-keyword">final</span> ArrayList&lt;IActivityManager.WaitResult&gt; mWaitingActivityVisible = <span class="hljs-keyword">new</span> ArrayList&lt;&gt;();
                    
                        <span class="hljs-comment">/** List of processes waiting to find out about the next launched activity. */</span>
                        <span class="hljs-keyword">final</span> ArrayList&lt;IActivityManager.WaitResult&gt; mWaitingActivityLaunched = <span class="hljs-keyword">new</span> ArrayList&lt;&gt;();
                    
                        <span class="hljs-comment">/** List of activities that are ready to be stopped, but waiting for the next activity to
                         * settle down before doing so. */</span>
                        <span class="hljs-keyword">final</span> ArrayList&lt;ActivityRecord&gt; mStoppingActivities = <span class="hljs-keyword">new</span> ArrayList&lt;&gt;();
                        ...
                      
                    </code></pre>
                    
                    startActivityMayWait()比较长，前面大段代码都是用来获取Activity的相关信息，比如FLAG、PID、UID等，关键代码1如下：
                    
                    <pre class="hljs java"><code class="java"> ResolveInfo rInfo =
                                      AppGlobals.getPackageManager().resolveIntent(
                                                intent, <span class="hljs-keyword">null</span>,
                                                PackageManager.MATCH_DEFAULT_ONLY
                                                | ActivityManagerService.STOCK_PM_FLAGS, userId);
                                                aInfo = rInfo != <span class="hljs-keyword">null</span> ? rInfo.activityInfo : <span class="hljs-keyword">null</span>;
                                                aInfo = mService.getActivityInfoForUser(aInfo, userId);
                    </code></pre>
                        
                    - 1、ASS.startActivityMayWait
                        
                        当程序运行到这里时, ASS.startActivityMayWait的各个参数取值如下:
                        
                         - 1、caller = ApplicationThreadProxy, 用于跟调用者进程ApplicationThread进行通信的binder代理类.
                         
                         - 2、callingUid = -1;
                         
                         - 3、callingPackage = ContextImpl.getBasePackageName(),获取调用者Activity所在包名
                         
                         - 4、intent: 这是启动Activity时传递过来的参数;
                         
                         - 5、resolvedType = intent.resolveTypeIfNeeded
                         
                         - 6、voiceSession = null;
                         
                         - 7、voiceInteractor = null;
                         
                         - 8、resultTo = Activity.mToken, 其中Activity是指调用者所在Activity, mToken对象保存自己所处的ActivityRecord信息
                         
                         - 9、resultWho = Activity.mEmbeddedID, 其中Activity是指调用者所在Activity
                         
                         - 10、requestCode = -1;
                         
                         - 11、startFlags = 0;
                         
                         - 12、profilerInfo = null;
                         
                         - 13、outResult = null;
                         
                         - 14、config = null;
                         
                         - 15、options = null;
                         
                         - 16、ignoreTargetSecurity = false;
                         
                         - 17、userId = AMS.handleIncomingUser, 当调用者userId跟当前处于同一个userId,则直接返回该userId;当不相等时则根据调用者userId来决定是否需要将callingUserId转换为mCurrentUserId.
                         
                         - 18、iContainer = null;
                         
                         - 19、inTask = null;
                         
                    (接ActivityStackSupervisor类)该过程主要功能：通过resolveActivity来获取ActivityInfo信息, 然后再进入ASS.startActivityLocked().先来看看
                    
                    ####ASS.resolveActivity
                    
                    <pre class="highlight"><code class="hljs java"><span class="hljs-comment">// startFlags = 0; profilerInfo = null; userId代表caller UserId</span>
                    <span class="hljs-function">ActivityInfo <span class="hljs-title">resolveActivity</span><span class="hljs-params">(Intent intent, String resolvedType, <span class="hljs-keyword">int</span> startFlags,
                            ProfilerInfo profilerInfo, <span class="hljs-keyword">int</span> userId)</span> </span>{
                        ActivityInfo aInfo;
                        ResolveInfo rInfo =
                            AppGlobals.getPackageManager().resolveIntent(
                                    intent, resolvedType,
                                    PackageManager.MATCH_DEFAULT_ONLY
                                                | ActivityManagerService.STOCK_PM_FLAGS, userId);
                        aInfo = rInfo != <span class="hljs-keyword">null</span> ? rInfo.activityInfo : <span class="hljs-keyword">null</span>;
                        <span class="hljs-keyword">if</span> (aInfo != <span class="hljs-keyword">null</span>) {
                            intent.setComponent(<span class="hljs-keyword">new</span> ComponentName(
                                    aInfo.applicationInfo.packageName, aInfo.name));
                    
                            <span class="hljs-keyword">if</span> (!aInfo.processName.equals(<span class="hljs-string">"system"</span>)) {
                                ... <span class="hljs-comment">//对于非system进程，根据flags来设置相应的debug信息</span>
                            }
                        }
                        <span class="hljs-keyword">return</span> aInfo;
                    }
                    </code></pre>
                    
                    ActivityManager类有如下4个flags用于调试：
                    
                    START_FLAG_DEBUG：用于调试debug app
                    
                    START_FLAG_OPENGL_TRACES：用于调试OpenGL tracing
                    
                    START_FLAG_NATIVE_DEBUGGING：用于调试native
                    
                    START_FLAG_TRACK_ALLOCATION: 用于调试allocation tracking
                    
                #### PKMS.resolveIntent
                
                AppGlobals.getPackageManager()经过函数层层调用，获取的是ApplicationPackageManager对象。经过binder IPC调用，最终会调用PackageManagerService对象。故此时调用方法为PMS.resolveIntent().
                
                <p>[-&gt; PackageManagerService.java]</p>
                
                <pre class="highlight"><code class="hljs java"><span class="hljs-function"><span class="hljs-keyword">public</span> ResolveInfo <span class="hljs-title">resolveIntent</span><span class="hljs-params">(Intent intent, String resolvedType,
                         <span class="hljs-keyword">int</span> flags, <span class="hljs-keyword">int</span> userId)</span> </span>{
                     <span class="hljs-keyword">if</span> (!sUserManager.exists(userId)) <span class="hljs-keyword">return</span> <span class="hljs-keyword">null</span>;
                     enforceCrossUserPermission(Binder.getCallingUid(), userId, <span class="hljs-keyword">false</span>, <span class="hljs-keyword">false</span>, <span class="hljs-string">"resolve intent"</span>);
                     <span class="hljs-comment">//[见流程2.7.3]</span>
                     List&lt;ResolveInfo&gt; query = queryIntentActivities(intent, resolvedType, flags, userId);
                     <span class="hljs-comment">//根据priority，preferred选择最佳的Activity</span>
                     <span class="hljs-keyword">return</span> chooseBestActivity(intent, resolvedType, flags, query, userId);
                 }
                </code></pre>
                
                #### PMS.queryIntentActivities
                
                <pre class="highlight"><code class="hljs php"><span class="hljs-keyword">public</span> <span class="hljs-keyword">List</span>&lt;ResolveInfo&gt; queryIntentActivities(Intent intent,
                        String resolvedType, int flags, int userId) {
                    ...
                    ComponentName comp = intent.getComponent();
                    <span class="hljs-keyword">if</span> (comp == <span class="hljs-keyword">null</span>) {
                        <span class="hljs-keyword">if</span> (intent.getSelector() != <span class="hljs-keyword">null</span>) {
                            intent = intent.getSelector();
                            comp = intent.getComponent();
                        }
                    }
                
                    <span class="hljs-keyword">if</span> (comp != <span class="hljs-keyword">null</span>) {
                        <span class="hljs-keyword">final</span> <span class="hljs-keyword">List</span>&lt;ResolveInfo&gt; <span class="hljs-keyword">list</span> = <span class="hljs-keyword">new</span> ArrayList&lt;ResolveInfo&gt;(<span class="hljs-number">1</span>);
                        <span class="hljs-comment">//获取Activity信息</span>
                        <span class="hljs-keyword">final</span> ActivityInfo ai = getActivityInfo(comp, flags, userId);
                        <span class="hljs-keyword">if</span> (ai != <span class="hljs-keyword">null</span>) {
                            <span class="hljs-keyword">final</span> ResolveInfo ri = <span class="hljs-keyword">new</span> ResolveInfo();
                            ri.activityInfo = ai;
                            <span class="hljs-keyword">list</span>.add(ri);
                        }
                        <span class="hljs-keyword">return</span> <span class="hljs-keyword">list</span>;
                    }
                    ...
                }
                </code></pre>
                
                ASS.resolveActivity()方法的核心功能是找到相应的Activity组件，并保存到intent对象。
                
                #### ASS.startActivityLocked
                
                <p>[-&gt; ActivityStackSupervisor.java]</p>
                
                <pre class="highlight"><code class="hljs java"><span class="hljs-function"><span class="hljs-keyword">final</span> <span class="hljs-keyword">int</span> <span class="hljs-title">startActivityLocked</span><span class="hljs-params">(IApplicationThread caller,
                        Intent intent, String resolvedType, ActivityInfo aInfo,
                        IVoiceInteractionSession voiceSession, IVoiceInteractor voiceInteractor,
                        IBinder resultTo, String resultWho, <span class="hljs-keyword">int</span> requestCode,
                        <span class="hljs-keyword">int</span> callingPid, <span class="hljs-keyword">int</span> callingUid, String callingPackage,
                        <span class="hljs-keyword">int</span> realCallingPid, <span class="hljs-keyword">int</span> realCallingUid, <span class="hljs-keyword">int</span> startFlags, Bundle options,
                        <span class="hljs-keyword">boolean</span> ignoreTargetSecurity, <span class="hljs-keyword">boolean</span> componentSpecified, ActivityRecord[] outActivity,
                        ActivityContainer container, TaskRecord inTask)</span> </span>{
                    <span class="hljs-keyword">int</span> err = ActivityManager.START_SUCCESS;
                
                    <span class="hljs-comment">//获取调用者的进程记录对象</span>
                    ProcessRecord callerApp = <span class="hljs-keyword">null</span>;
                    <span class="hljs-keyword">if</span> (caller != <span class="hljs-keyword">null</span>) {
                        callerApp = mService.getRecordForAppLocked(caller);
                        <span class="hljs-keyword">if</span> (callerApp != <span class="hljs-keyword">null</span>) {
                            callingPid = callerApp.pid;
                            callingUid = callerApp.info.uid;
                        } <span class="hljs-keyword">else</span> {
                            err = ActivityManager.START_PERMISSION_DENIED;
                        }
                    }
                
                    <span class="hljs-keyword">final</span> <span class="hljs-keyword">int</span> userId = aInfo != <span class="hljs-keyword">null</span> ?  UserHandle.getUserId(aInfo.applicationInfo.uid) : <span class="hljs-number">0</span>;
                
                    ActivityRecord sourceRecord = <span class="hljs-keyword">null</span>;
                    ActivityRecord resultRecord = <span class="hljs-keyword">null</span>;
                    <span class="hljs-keyword">if</span> (resultTo != <span class="hljs-keyword">null</span>) {
                        <span class="hljs-comment">//获取调用者所在的Activity</span>
                        sourceRecord = isInAnyStackLocked(resultTo);
                        <span class="hljs-keyword">if</span> (sourceRecord != <span class="hljs-keyword">null</span>) {
                            <span class="hljs-keyword">if</span> (requestCode &gt;= <span class="hljs-number">0</span> &amp;&amp; !sourceRecord.finishing) {
                                ... <span class="hljs-comment">//requestCode = -1 则不进入</span>
                            }
                        }
                    }
                
                    <span class="hljs-keyword">final</span> <span class="hljs-keyword">int</span> launchFlags = intent.getFlags();
                
                    <span class="hljs-keyword">if</span> ((launchFlags &amp; Intent.FLAG_ACTIVITY_FORWARD_RESULT) != <span class="hljs-number">0</span> &amp;&amp; sourceRecord != <span class="hljs-keyword">null</span>) {
                        ... <span class="hljs-comment">// activity执行结果的返回由源Activity转换到新Activity, 不需要返回结果则不会进入该分支</span>
                    }
                
                    <span class="hljs-keyword">if</span> (err == ActivityManager.START_SUCCESS &amp;&amp; intent.getComponent() == <span class="hljs-keyword">null</span>) {
                        <span class="hljs-comment">//从Intent中无法找到相应的Component</span>
                        err = ActivityManager.START_INTENT_NOT_RESOLVED;
                    }
                
                    <span class="hljs-keyword">if</span> (err == ActivityManager.START_SUCCESS &amp;&amp; aInfo == <span class="hljs-keyword">null</span>) {
                        <span class="hljs-comment">//从Intent中无法找到相应的ActivityInfo</span>
                        err = ActivityManager.START_INTENT_NOT_RESOLVED;
                    }
                
                    <span class="hljs-keyword">if</span> (err == ActivityManager.START_SUCCESS
                            &amp;&amp; !isCurrentProfileLocked(userId)
                            &amp;&amp; (aInfo.flags &amp; FLAG_SHOW_FOR_ALL_USERS) == <span class="hljs-number">0</span>) {
                        <span class="hljs-comment">//尝试启动一个后台Activity, 但该Activity对当前用户不可见</span>
                        err = ActivityManager.START_NOT_CURRENT_USER_ACTIVITY;
                    }
                    ...
                
                    <span class="hljs-comment">//执行后resultStack = null</span>
                    <span class="hljs-keyword">final</span> ActivityStack resultStack = resultRecord == <span class="hljs-keyword">null</span> ? <span class="hljs-keyword">null</span> : resultRecord.task.stack;
                
                    ... <span class="hljs-comment">//权限检查</span>
                
                    <span class="hljs-comment">// ActivityController不为空的情况，比如monkey测试过程</span>
                    <span class="hljs-keyword">if</span> (mService.mController != <span class="hljs-keyword">null</span>) {
                        Intent watchIntent = intent.cloneFilter();
                        abort |= !mService.mController.activityStarting(watchIntent,
                                aInfo.applicationInfo.packageName);
                    }
                
                    <span class="hljs-keyword">if</span> (abort) {
                        ... <span class="hljs-comment">//权限检查不满足,才进入该分支则直接返回；</span>
                        <span class="hljs-keyword">return</span> ActivityManager.START_SUCCESS;
                    }
                
                    <span class="hljs-comment">// 创建Activity记录对象</span>
                    ActivityRecord r = <span class="hljs-keyword">new</span> ActivityRecord(mService, callerApp, callingUid, callingPackage,
                            intent, resolvedType, aInfo, mService.mConfiguration, resultRecord, resultWho,
                            requestCode, componentSpecified, voiceSession != <span class="hljs-keyword">null</span>, <span class="hljs-keyword">this</span>, container, options);
                    <span class="hljs-keyword">if</span> (outActivity != <span class="hljs-keyword">null</span>) {
                        outActivity[<span class="hljs-number">0</span>] = r;
                    }
                
                    <span class="hljs-keyword">if</span> (r.appTimeTracker == <span class="hljs-keyword">null</span> &amp;&amp; sourceRecord != <span class="hljs-keyword">null</span>) {
                        r.appTimeTracker = sourceRecord.appTimeTracker;
                    }
                    <span class="hljs-comment">// 将mFocusedStack赋予当前stack</span>
                    <span class="hljs-keyword">final</span> ActivityStack stack = mFocusedStack;
                
                    <span class="hljs-keyword">if</span> (voiceSession == <span class="hljs-keyword">null</span> &amp;&amp; (stack.mResumedActivity == <span class="hljs-keyword">null</span>
                            || stack.mResumedActivity.info.applicationInfo.uid != callingUid)) {
                        <span class="hljs-comment">// 前台stack还没有resume状态的Activity时, 则检查app切换是否允许 [见流程2.8.1]</span>
                        <span class="hljs-keyword">if</span> (!mService.checkAppSwitchAllowedLocked(callingPid, callingUid,
                                realCallingPid, realCallingUid, <span class="hljs-string">"Activity start"</span>)) {
                            PendingActivityLaunch pal =
                                    <span class="hljs-keyword">new</span> PendingActivityLaunch(r, sourceRecord, startFlags, stack);
                            <span class="hljs-comment">// 当不允许切换,则把要启动的Activity添加到mPendingActivityLaunches对象, 并且直接返回.</span>
                            mPendingActivityLaunches.add(pal);
                            ActivityOptions.abort(options);
                            <span class="hljs-keyword">return</span> ActivityManager.START_SWITCHES_CANCELED;
                        }
                    }
                
                    <span class="hljs-keyword">if</span> (mService.mDidAppSwitch) {
                        <span class="hljs-comment">//从上次禁止app切换以来,这是第二次允许app切换,因此将允许切换时间设置为0,则表示可以任意切换app</span>
                        mService.mAppSwitchesAllowedTime = <span class="hljs-number">0</span>;
                    } <span class="hljs-keyword">else</span> {
                        mService.mDidAppSwitch = <span class="hljs-keyword">true</span>;
                    }
                
                    <span class="hljs-comment">//处理 pendind Activity的启动, 这些Activity是由于app switch禁用从而被hold的等待启动activity [见流程2.8.2]</span>
                    doPendingActivityLaunchesLocked(<span class="hljs-keyword">false</span>);
                
                    <span class="hljs-comment">//[见流程2.9]</span>
                    err = startActivityUncheckedLocked(r, sourceRecord, voiceSession, voiceInteractor,
                            startFlags, <span class="hljs-keyword">true</span>, options, inTask);
                
                    <span class="hljs-keyword">if</span> (err &lt; <span class="hljs-number">0</span>) {
                        notifyActivityDrawnForKeyguard();
                    }
                    <span class="hljs-keyword">return</span> err;
                }
                </code></pre>
                
                其中有两个返回值代表启动Activity失败：
                
                <ul>
                  <li>START_INTENT_NOT_RESOLVED: 从Intent中无法找到相应的Component或者ActivityInfo</li>
                  <li>START_NOT_CURRENT_USER_ACTIVITY：该Activity对当前用户不可见</li>
                </ul>
                
                #### AMS.checkAppSwitchAllowedLocked
                
                <pre class="highlight"><code class="hljs java"><span class="hljs-function"><span class="hljs-keyword">boolean</span> <span class="hljs-title">checkAppSwitchAllowedLocked</span><span class="hljs-params">(<span class="hljs-keyword">int</span> sourcePid, <span class="hljs-keyword">int</span> sourceUid,
                        <span class="hljs-keyword">int</span> callingPid, <span class="hljs-keyword">int</span> callingUid, String name)</span> </span>{
                    <span class="hljs-keyword">if</span> (mAppSwitchesAllowedTime &lt; SystemClock.uptimeMillis()) {
                        <span class="hljs-keyword">return</span> <span class="hljs-keyword">true</span>;
                    }
                
                    <span class="hljs-keyword">int</span> perm = checkComponentPermission(
                            android.Manifest.permission.STOP_APP_SWITCHES, sourcePid,
                            sourceUid, -<span class="hljs-number">1</span>, <span class="hljs-keyword">true</span>);
                    <span class="hljs-keyword">if</span> (perm == PackageManager.PERMISSION_GRANTED) {
                        <span class="hljs-keyword">return</span> <span class="hljs-keyword">true</span>;
                    }
                
                    <span class="hljs-keyword">if</span> (callingUid != -<span class="hljs-number">1</span> &amp;&amp; callingUid != sourceUid) {
                        perm = checkComponentPermission(
                                android.Manifest.permission.STOP_APP_SWITCHES, callingPid,
                                callingUid, -<span class="hljs-number">1</span>, <span class="hljs-keyword">true</span>);
                        <span class="hljs-keyword">if</span> (perm == PackageManager.PERMISSION_GRANTED) {
                            <span class="hljs-keyword">return</span> <span class="hljs-keyword">true</span>;
                        }
                    }
                
                    <span class="hljs-keyword">return</span> <span class="hljs-keyword">false</span>;
                }
                </code></pre>
                
                当mAppSwitchesAllowedTime时间小于当前时长,或者具有STOP_APP_SWITCHES的权限,则允许app发生切换操作
                
                其中mAppSwitchesAllowedTime, 在AMS.stopAppSwitches()的过程中会设置为:mAppSwitchesAllowedTime = SystemClock.uptimeMillis() + APP_SWITCH_DELAY_TIME. 禁止app切换的timeout时长为5s(APP_SWITCH_DELAY_TIME = 5s).
                
                当发送5秒超时或者执行AMS.resumeAppSwitches()过程会将mAppSwitchesAllowedTime设置0, 都会开启允许app执行切换的操作.另外,禁止App切换的操作,对于同一个app是不受影响的,有兴趣可以进一步查看checkComponentPermission过程.
                
                ####  ASS.doPendingActivityLaunchesLocked
                
                <p>[-&gt; ActivityStackSupervisor.java]</p>
                
                <pre class="highlight"><code class="hljs java"><span class="hljs-function"><span class="hljs-keyword">final</span> <span class="hljs-keyword">void</span> <span class="hljs-title">doPendingActivityLaunchesLocked</span><span class="hljs-params">(<span class="hljs-keyword">boolean</span> doResume)</span> </span>{
                    <span class="hljs-keyword">while</span> (!mPendingActivityLaunches.isEmpty()) {
                        PendingActivityLaunch pal = mPendingActivityLaunches.remove(<span class="hljs-number">0</span>);
                        <span class="hljs-keyword">try</span> {
                            <span class="hljs-comment">//[见流程2.9]</span>
                            startActivityUncheckedLocked(pal.r, pal.sourceRecord, <span class="hljs-keyword">null</span>, <span class="hljs-keyword">null</span>, pal.startFlags,
                                                         doResume &amp;&amp; mPendingActivityLaunches.isEmpty(), <span class="hljs-keyword">null</span>, <span class="hljs-keyword">null</span>);
                        } <span class="hljs-keyword">catch</span> (Exception e) {
                            ...
                        }
                    }
                }
                </code></pre>
                
                mPendingActivityLaunches记录着所有将要启动的Activity, 是由于在startActivityLocked的过程时App切换功能被禁止, 也就是不运行切换Activity, 那么此时便会把相应的Activity加入到mPendingActivityLaunches队列. 该队列的成员在执行完doPendingActivityLaunchesLocked便会清空.
                
                启动mPendingActivityLaunches中所有的Activity, 由于doResume = false, 那么这些activtity并不会进入resume状态,而是设置delayedResume = true, 会延迟resume.
                
                ####ASS.startActivityUncheckedLocked
                
                <p>[-&gt; ActivityStackSupervisor.java]</p>
                
                <pre class="highlight"><code class="hljs java"><span class="hljs-comment">// sourceRecord是指调用者， r是指本次将要启动的Activity</span>
                <span class="hljs-function"><span class="hljs-keyword">final</span> <span class="hljs-keyword">int</span> <span class="hljs-title">startActivityUncheckedLocked</span><span class="hljs-params">(<span class="hljs-keyword">final</span> ActivityRecord r, ActivityRecord sourceRecord,
                        IVoiceInteractionSession voiceSession, IVoiceInteractor voiceInteractor, <span class="hljs-keyword">int</span> startFlags,
                        <span class="hljs-keyword">boolean</span> doResume, Bundle options, TaskRecord inTask)</span> </span>{
                    <span class="hljs-keyword">final</span> Intent intent = r.intent;
                    <span class="hljs-keyword">final</span> <span class="hljs-keyword">int</span> callingUid = r.launchedFromUid;
                
                    <span class="hljs-keyword">if</span> (inTask != <span class="hljs-keyword">null</span> &amp;&amp; !inTask.inRecents) {
                        inTask = <span class="hljs-keyword">null</span>;
                    }
                
                    <span class="hljs-keyword">final</span> <span class="hljs-keyword">boolean</span> launchSingleTop = r.launchMode == ActivityInfo.LAUNCH_SINGLE_TOP;
                    <span class="hljs-keyword">final</span> <span class="hljs-keyword">boolean</span> launchSingleInstance = r.launchMode == ActivityInfo.LAUNCH_SINGLE_INSTANCE;
                    <span class="hljs-keyword">final</span> <span class="hljs-keyword">boolean</span> launchSingleTask = r.launchMode == ActivityInfo.LAUNCH_SINGLE_TASK;
                
                    <span class="hljs-keyword">int</span> launchFlags = intent.getFlags();
                    <span class="hljs-comment">// 当intent和activity manifest存在冲突，则manifest优先</span>
                    <span class="hljs-keyword">if</span> ((launchFlags &amp; Intent.FLAG_ACTIVITY_NEW_DOCUMENT) != <span class="hljs-number">0</span> &amp;&amp;
                            (launchSingleInstance || launchSingleTask)) {
                        launchFlags &amp;=
                                ~(Intent.FLAG_ACTIVITY_NEW_DOCUMENT | Intent.FLAG_ACTIVITY_MULTIPLE_TASK);
                    } <span class="hljs-keyword">else</span> {
                        ...
                    }
                
                    <span class="hljs-keyword">final</span> <span class="hljs-keyword">boolean</span> launchTaskBehind = r.mLaunchTaskBehind
                            &amp;&amp; !launchSingleTask &amp;&amp; !launchSingleInstance
                            &amp;&amp; (launchFlags &amp; Intent.FLAG_ACTIVITY_NEW_DOCUMENT) != <span class="hljs-number">0</span>;
                
                    <span class="hljs-keyword">if</span> (r.resultTo != <span class="hljs-keyword">null</span> &amp;&amp; (launchFlags &amp; Intent.FLAG_ACTIVITY_NEW_TASK) != <span class="hljs-number">0</span>
                            &amp;&amp; r.resultTo.task.stack != <span class="hljs-keyword">null</span>) {
                        r.resultTo.task.stack.sendActivityResultLocked(-<span class="hljs-number">1</span>,
                                r.resultTo, r.resultWho, r.requestCode,
                                Activity.RESULT_CANCELED, <span class="hljs-keyword">null</span>);
                        r.resultTo = <span class="hljs-keyword">null</span>;
                    }
                
                    <span class="hljs-keyword">if</span> ((launchFlags &amp; Intent.FLAG_ACTIVITY_NEW_DOCUMENT) != <span class="hljs-number">0</span> &amp;&amp; r.resultTo == <span class="hljs-keyword">null</span>) {
                        launchFlags |= Intent.FLAG_ACTIVITY_NEW_TASK;
                    }
                
                    <span class="hljs-keyword">if</span> ((launchFlags &amp; Intent.FLAG_ACTIVITY_NEW_TASK) != <span class="hljs-number">0</span>) {
                        <span class="hljs-keyword">if</span> (launchTaskBehind
                                || r.info.documentLaunchMode == ActivityInfo.DOCUMENT_LAUNCH_ALWAYS) {
                            launchFlags |= Intent.FLAG_ACTIVITY_MULTIPLE_TASK;
                        }
                    }
                
                    mUserLeaving = (launchFlags &amp; Intent.FLAG_ACTIVITY_NO_USER_ACTION) == <span class="hljs-number">0</span>;
                    <span class="hljs-comment">//当本次不需要resume，则设置为延迟resume的状态</span>
                    <span class="hljs-keyword">if</span> (!doResume) {
                        r.delayedResume = <span class="hljs-keyword">true</span>;
                    }
                
                    ActivityRecord notTop =
                            (launchFlags &amp; Intent.FLAG_ACTIVITY_PREVIOUS_IS_TOP) != <span class="hljs-number">0</span> ? r : <span class="hljs-keyword">null</span>;
                
                    <span class="hljs-keyword">if</span> ((startFlags&amp;ActivityManager.START_FLAG_ONLY_IF_NEEDED) != <span class="hljs-number">0</span>) {
                        ActivityRecord checkedCaller = sourceRecord;
                        <span class="hljs-keyword">if</span> (checkedCaller == <span class="hljs-keyword">null</span>) {
                            checkedCaller = mFocusedStack.topRunningNonDelayedActivityLocked(notTop);
                        }
                        <span class="hljs-keyword">if</span> (!checkedCaller.realActivity.equals(r.realActivity)) {
                            <span class="hljs-comment">//调用者 与将要启动的Activity不相同时，进入该分支。</span>
                            startFlags &amp;= ~ActivityManager.START_FLAG_ONLY_IF_NEEDED;
                        }
                    }
                
                    <span class="hljs-keyword">boolean</span> addingToTask = <span class="hljs-keyword">false</span>;
                    TaskRecord reuseTask = <span class="hljs-keyword">null</span>;
                
                    <span class="hljs-comment">//当调用者不是来自activity，而是明确指定task的情况。</span>
                    <span class="hljs-keyword">if</span> (sourceRecord == <span class="hljs-keyword">null</span> &amp;&amp; inTask != <span class="hljs-keyword">null</span> &amp;&amp; inTask.stack != <span class="hljs-keyword">null</span>) {
                        ... <span class="hljs-comment">//目前sourceRecord不为空，则不进入该分支</span>
                    } <span class="hljs-keyword">else</span> {
                        inTask = <span class="hljs-keyword">null</span>;
                    }
                
                    <span class="hljs-keyword">if</span> (inTask == <span class="hljs-keyword">null</span>) {
                        <span class="hljs-keyword">if</span> (sourceRecord == <span class="hljs-keyword">null</span>) {
                            <span class="hljs-comment">//调用者并不是Activity context,则强制创建新task</span>
                            <span class="hljs-keyword">if</span> ((launchFlags &amp; Intent.FLAG_ACTIVITY_NEW_TASK) == <span class="hljs-number">0</span> &amp;&amp; inTask == <span class="hljs-keyword">null</span>) {
                                launchFlags |= Intent.FLAG_ACTIVITY_NEW_TASK;
                            }
                        } <span class="hljs-keyword">else</span> <span class="hljs-keyword">if</span> (sourceRecord.launchMode == ActivityInfo.LAUNCH_SINGLE_INSTANCE) {
                            <span class="hljs-comment">//调用者activity带有single instance，则创建新task</span>
                            launchFlags |= Intent.FLAG_ACTIVITY_NEW_TASK;
                        } <span class="hljs-keyword">else</span> <span class="hljs-keyword">if</span> (launchSingleInstance || launchSingleTask) {
                            <span class="hljs-comment">//目标activity带有single instance或者single task，则创建新task</span>
                            launchFlags |= Intent.FLAG_ACTIVITY_NEW_TASK;
                        }
                    }
                
                    ActivityInfo newTaskInfo = <span class="hljs-keyword">null</span>;
                    Intent newTaskIntent = <span class="hljs-keyword">null</span>;
                    ActivityStack sourceStack;
                    <span class="hljs-keyword">if</span> (sourceRecord != <span class="hljs-keyword">null</span>) {
                        <span class="hljs-keyword">if</span> (sourceRecord.finishing) {
                            <span class="hljs-comment">//调用者处于即将finish状态，则创建新task</span>
                            <span class="hljs-keyword">if</span> ((launchFlags &amp; Intent.FLAG_ACTIVITY_NEW_TASK) == <span class="hljs-number">0</span>) {
                                launchFlags |= Intent.FLAG_ACTIVITY_NEW_TASK;
                                newTaskInfo = sourceRecord.info;
                                newTaskIntent = sourceRecord.task.intent;
                            }
                            sourceRecord = <span class="hljs-keyword">null</span>;
                            sourceStack = <span class="hljs-keyword">null</span>;
                        } <span class="hljs-keyword">else</span> {
                            <span class="hljs-comment">//当调用者Activity不为空，且不处于finishing状态，则其所在栈赋于sourceStack</span>
                            sourceStack = sourceRecord.task.stack;
                        }
                    } <span class="hljs-keyword">else</span> {
                        sourceStack = <span class="hljs-keyword">null</span>;
                    }
                
                    <span class="hljs-keyword">boolean</span> movedHome = <span class="hljs-keyword">false</span>;
                    ActivityStack targetStack;
                
                    intent.setFlags(launchFlags);
                    <span class="hljs-keyword">final</span> <span class="hljs-keyword">boolean</span> noAnimation = (launchFlags &amp; Intent.FLAG_ACTIVITY_NO_ANIMATION) != <span class="hljs-number">0</span>;
                
                    <span class="hljs-keyword">if</span> (((launchFlags &amp; Intent.FLAG_ACTIVITY_NEW_TASK) != <span class="hljs-number">0</span> &amp;&amp;
                            (launchFlags &amp; Intent.FLAG_ACTIVITY_MULTIPLE_TASK) == <span class="hljs-number">0</span>)
                            || launchSingleInstance || launchSingleTask) {
                        <span class="hljs-keyword">if</span> (inTask == <span class="hljs-keyword">null</span> &amp;&amp; r.resultTo == <span class="hljs-keyword">null</span>) {
                            <span class="hljs-comment">//从mActivityDisplays开始查询是否有相应ActivityRecord</span>
                            ActivityRecord intentActivity = !launchSingleInstance ?
                                    findTaskLocked(r) : findActivityLocked(intent, r.info);
                            <span class="hljs-keyword">if</span> (intentActivity != <span class="hljs-keyword">null</span>) {
                                <span class="hljs-keyword">if</span> (isLockTaskModeViolation(intentActivity.task,
                                        (launchFlags &amp; (FLAG_ACTIVITY_NEW_TASK | FLAG_ACTIVITY_CLEAR_TASK))
                                        == (FLAG_ACTIVITY_NEW_TASK | FLAG_ACTIVITY_CLEAR_TASK))) {
                                    <span class="hljs-keyword">return</span> ActivityManager.START_RETURN_LOCK_TASK_MODE_VIOLATION;
                                }
                                <span class="hljs-keyword">if</span> (r.task == <span class="hljs-keyword">null</span>) {
                                    r.task = intentActivity.task;
                                }
                                <span class="hljs-keyword">if</span> (intentActivity.task.intent == <span class="hljs-keyword">null</span>) {
                                    intentActivity.task.setIntent(r);
                                }
                                targetStack = intentActivity.task.stack;
                                targetStack.mLastPausedActivity = <span class="hljs-keyword">null</span>;
                
                                <span class="hljs-keyword">final</span> ActivityStack focusStack = getFocusedStack();
                                ActivityRecord curTop = (focusStack == <span class="hljs-keyword">null</span>)
                                        ? <span class="hljs-keyword">null</span> : focusStack.topRunningNonDelayedActivityLocked(notTop);
                                <span class="hljs-keyword">boolean</span> movedToFront = <span class="hljs-keyword">false</span>;
                                <span class="hljs-keyword">if</span> (curTop != <span class="hljs-keyword">null</span> &amp;&amp; (curTop.task != intentActivity.task ||
                                        curTop.task != focusStack.topTask())) {
                                    r.intent.addFlags(Intent.FLAG_ACTIVITY_BROUGHT_TO_FRONT);
                                    <span class="hljs-keyword">if</span> (sourceRecord == <span class="hljs-keyword">null</span> || (sourceStack.topActivity() != <span class="hljs-keyword">null</span> &amp;&amp;
                                            sourceStack.topActivity().task == sourceRecord.task)) {
                                        <span class="hljs-keyword">if</span> (launchTaskBehind &amp;&amp; sourceRecord != <span class="hljs-keyword">null</span>) {
                                            intentActivity.setTaskToAffiliateWith(sourceRecord.task);
                                        }
                                        movedHome = <span class="hljs-keyword">true</span>;
                                        <span class="hljs-comment">//将该task移至前台</span>
                                        targetStack.moveTaskToFrontLocked(intentActivity.task, noAnimation,
                                                options, r.appTimeTracker, <span class="hljs-string">"bringingFoundTaskToFront"</span>);
                                        movedToFront = <span class="hljs-keyword">true</span>;
                                        <span class="hljs-keyword">if</span> ((launchFlags &amp;
                                                (FLAG_ACTIVITY_NEW_TASK | FLAG_ACTIVITY_TASK_ON_HOME))
                                                == (FLAG_ACTIVITY_NEW_TASK | FLAG_ACTIVITY_TASK_ON_HOME)) {
                                            <span class="hljs-comment">//将toReturnTo设置为home</span>
                                            intentActivity.task.setTaskToReturnTo(HOME_ACTIVITY_TYPE);
                                        }
                                        options = <span class="hljs-keyword">null</span>;
                                    }
                                }
                                <span class="hljs-keyword">if</span> (!movedToFront) {
                                    targetStack.moveToFront(<span class="hljs-string">"intentActivityFound"</span>);
                                }
                
                                <span class="hljs-keyword">if</span> ((launchFlags&amp;Intent.FLAG_ACTIVITY_RESET_TASK_IF_NEEDED) != <span class="hljs-number">0</span>) {
                                    <span class="hljs-comment">//重置目标task</span>
                                    intentActivity = targetStack.resetTaskIfNeededLocked(intentActivity, r);
                                }
                                <span class="hljs-keyword">if</span> ((startFlags &amp; ActivityManager.START_FLAG_ONLY_IF_NEEDED) != <span class="hljs-number">0</span>) {
                                    <span class="hljs-keyword">if</span> (doResume) {
                                        resumeTopActivitiesLocked(targetStack, <span class="hljs-keyword">null</span>, options);
                                        <span class="hljs-comment">//当没有启动至前台，则通知Keyguard</span>
                                        <span class="hljs-keyword">if</span> (!movedToFront) {
                                            notifyActivityDrawnForKeyguard();
                                        }
                                    } <span class="hljs-keyword">else</span> {
                                        ActivityOptions.abort(options);
                                    }
                                    <span class="hljs-keyword">return</span> ActivityManager.START_RETURN_INTENT_TO_CALLER;
                                }
                                <span class="hljs-keyword">if</span> ((launchFlags &amp; (FLAG_ACTIVITY_NEW_TASK | FLAG_ACTIVITY_CLEAR_TASK))
                                        == (FLAG_ACTIVITY_NEW_TASK | FLAG_ACTIVITY_CLEAR_TASK)) {
                                    reuseTask = intentActivity.task;
                                    <span class="hljs-comment">//移除所有跟已存在的task有关联的activity</span>
                                    reuseTask.performClearTaskLocked();
                                    reuseTask.setIntent(r);
                                } <span class="hljs-keyword">else</span> <span class="hljs-keyword">if</span> ((launchFlags &amp; FLAG_ACTIVITY_CLEAR_TOP) != <span class="hljs-number">0</span>
                                        || launchSingleInstance || launchSingleTask) {
                                    ActivityRecord top =
                                            intentActivity.task.performClearTaskLocked(r, launchFlags);
                                    <span class="hljs-keyword">if</span> (top != <span class="hljs-keyword">null</span>) {
                                        <span class="hljs-keyword">if</span> (top.frontOfTask) {
                                            top.task.setIntent(r);
                                        }
                                        <span class="hljs-comment">//触发onNewIntent()</span>
                                        top.deliverNewIntentLocked(callingUid, r.intent, r.launchedFromPackage);
                                    } <span class="hljs-keyword">else</span> {
                                        sourceRecord = intentActivity;
                                        TaskRecord task = sourceRecord.task;
                                        <span class="hljs-keyword">if</span> (task != <span class="hljs-keyword">null</span> &amp;&amp; task.stack == <span class="hljs-keyword">null</span>) {
                                            targetStack = computeStackFocus(sourceRecord, <span class="hljs-keyword">false</span> <span class="hljs-comment">/* newTask */</span>);
                                            targetStack.addTask(
                                                    task, !launchTaskBehind <span class="hljs-comment">/* toTop */</span>, <span class="hljs-keyword">false</span> <span class="hljs-comment">/* moving */</span>);
                                        }
                
                                    }
                                } <span class="hljs-keyword">else</span> <span class="hljs-keyword">if</span> (r.realActivity.equals(intentActivity.task.realActivity)) {
                                    <span class="hljs-keyword">if</span> (((launchFlags&amp;Intent.FLAG_ACTIVITY_SINGLE_TOP) != <span class="hljs-number">0</span> || launchSingleTop)
                                            &amp;&amp; intentActivity.realActivity.equals(r.realActivity)) {
                                        <span class="hljs-keyword">if</span> (intentActivity.frontOfTask) {
                                            intentActivity.task.setIntent(r);
                                        }
                                        <span class="hljs-comment">//触发onNewIntent()</span>
                                        intentActivity.deliverNewIntentLocked(callingUid, r.intent,
                                                r.launchedFromPackage);
                                    } <span class="hljs-keyword">else</span> <span class="hljs-keyword">if</span> (!r.intent.filterEquals(intentActivity.task.intent)) {
                                        addingToTask = <span class="hljs-keyword">true</span>;
                                        sourceRecord = intentActivity;
                                    }
                                } <span class="hljs-keyword">else</span> <span class="hljs-keyword">if</span> ((launchFlags&amp;Intent.FLAG_ACTIVITY_RESET_TASK_IF_NEEDED) == <span class="hljs-number">0</span>) {
                                    addingToTask = <span class="hljs-keyword">true</span>;
                                    sourceRecord = intentActivity;
                                } <span class="hljs-keyword">else</span> <span class="hljs-keyword">if</span> (!intentActivity.task.rootWasReset) {
                                    intentActivity.task.setIntent(r);
                                }
                                <span class="hljs-keyword">if</span> (!addingToTask &amp;&amp; reuseTask == <span class="hljs-keyword">null</span>) {
                                    <span class="hljs-keyword">if</span> (doResume) {
                                        targetStack.resumeTopActivityLocked(<span class="hljs-keyword">null</span>, options);
                                        <span class="hljs-keyword">if</span> (!movedToFront) {
                                            notifyActivityDrawnForKeyguard();
                                        }
                                    } <span class="hljs-keyword">else</span> {
                                        ActivityOptions.abort(options);
                                    }
                                    <span class="hljs-keyword">return</span> ActivityManager.START_TASK_TO_FRONT;
                                }
                            }
                        }
                    }
                
                    <span class="hljs-keyword">if</span> (r.packageName != <span class="hljs-keyword">null</span>) {
                        <span class="hljs-comment">//当启动的activity跟前台显示是同一个的情况</span>
                        ActivityStack topStack = mFocusedStack;
                        ActivityRecord top = topStack.topRunningNonDelayedActivityLocked(notTop);
                        <span class="hljs-keyword">if</span> (top != <span class="hljs-keyword">null</span> &amp;&amp; r.resultTo == <span class="hljs-keyword">null</span>) {
                            <span class="hljs-keyword">if</span> (top.realActivity.equals(r.realActivity) &amp;&amp; top.userId == r.userId) {
                                <span class="hljs-keyword">if</span> (top.app != <span class="hljs-keyword">null</span> &amp;&amp; top.app.thread != <span class="hljs-keyword">null</span>) {
                                    <span class="hljs-keyword">if</span> ((launchFlags &amp; Intent.FLAG_ACTIVITY_SINGLE_TOP) != <span class="hljs-number">0</span>
                                        || launchSingleTop || launchSingleTask) {
                                        topStack.mLastPausedActivity = <span class="hljs-keyword">null</span>;
                                        <span class="hljs-keyword">if</span> (doResume) {
                                            resumeTopActivitiesLocked();
                                        }
                                        ActivityOptions.abort(options);
                                        <span class="hljs-keyword">if</span> ((startFlags&amp;ActivityManager.START_FLAG_ONLY_IF_NEEDED) != <span class="hljs-number">0</span>) {
                                        }
                                        <span class="hljs-comment">//触发onNewIntent()</span>
                                        top.deliverNewIntentLocked(callingUid, r.intent, r.launchedFromPackage);
                                        <span class="hljs-keyword">return</span> ActivityManager.START_DELIVERED_TO_TOP;
                                    }
                                }
                            }
                        }
                
                    } <span class="hljs-keyword">else</span> {
                        <span class="hljs-keyword">if</span> (r.resultTo != <span class="hljs-keyword">null</span> &amp;&amp; r.resultTo.task.stack != <span class="hljs-keyword">null</span>) {
                            r.resultTo.task.stack.sendActivityResultLocked(-<span class="hljs-number">1</span>, r.resultTo, r.resultWho,
                                    r.requestCode, Activity.RESULT_CANCELED, <span class="hljs-keyword">null</span>);
                        }
                        ActivityOptions.abort(options);
                        <span class="hljs-keyword">return</span> ActivityManager.START_CLASS_NOT_FOUND;
                    }
                
                    <span class="hljs-keyword">boolean</span> newTask = <span class="hljs-keyword">false</span>;
                    <span class="hljs-keyword">boolean</span> keepCurTransition = <span class="hljs-keyword">false</span>;
                
                    TaskRecord taskToAffiliate = launchTaskBehind &amp;&amp; sourceRecord != <span class="hljs-keyword">null</span> ?
                            sourceRecord.task : <span class="hljs-keyword">null</span>;
                
                    <span class="hljs-keyword">if</span> (r.resultTo == <span class="hljs-keyword">null</span> &amp;&amp; inTask == <span class="hljs-keyword">null</span> &amp;&amp; !addingToTask
                            &amp;&amp; (launchFlags &amp; Intent.FLAG_ACTIVITY_NEW_TASK) != <span class="hljs-number">0</span>) {
                        newTask = <span class="hljs-keyword">true</span>;
                        targetStack = computeStackFocus(r, newTask);
                        targetStack.moveToFront(<span class="hljs-string">"startingNewTask"</span>);
                
                        <span class="hljs-keyword">if</span> (reuseTask == <span class="hljs-keyword">null</span>) {
                            r.setTask(targetStack.createTaskRecord(getNextTaskId(),
                                    newTaskInfo != <span class="hljs-keyword">null</span> ? newTaskInfo : r.info,
                                    newTaskIntent != <span class="hljs-keyword">null</span> ? newTaskIntent : intent,
                                    voiceSession, voiceInteractor, !launchTaskBehind <span class="hljs-comment">/* toTop */</span>),
                                    taskToAffiliate);
                        } <span class="hljs-keyword">else</span> {
                            r.setTask(reuseTask, taskToAffiliate);
                        }
                        <span class="hljs-keyword">if</span> (isLockTaskModeViolation(r.task)) {
                            <span class="hljs-keyword">return</span> ActivityManager.START_RETURN_LOCK_TASK_MODE_VIOLATION;
                        }
                        <span class="hljs-keyword">if</span> (!movedHome) {
                            <span class="hljs-keyword">if</span> ((launchFlags &amp;
                                    (FLAG_ACTIVITY_NEW_TASK | FLAG_ACTIVITY_TASK_ON_HOME))
                                    == (FLAG_ACTIVITY_NEW_TASK | FLAG_ACTIVITY_TASK_ON_HOME)) {
                                r.task.setTaskToReturnTo(HOME_ACTIVITY_TYPE);
                            }
                        }
                    } <span class="hljs-keyword">else</span> <span class="hljs-keyword">if</span> (sourceRecord != <span class="hljs-keyword">null</span>) {
                        <span class="hljs-keyword">final</span> TaskRecord sourceTask = sourceRecord.task;
                        <span class="hljs-keyword">if</span> (isLockTaskModeViolation(sourceTask)) {
                            <span class="hljs-keyword">return</span> ActivityManager.START_RETURN_LOCK_TASK_MODE_VIOLATION;
                        }
                        targetStack = sourceTask.stack;
                        targetStack.moveToFront(<span class="hljs-string">"sourceStackToFront"</span>);
                        <span class="hljs-keyword">final</span> TaskRecord topTask = targetStack.topTask();
                        <span class="hljs-keyword">if</span> (topTask != sourceTask) {
                            targetStack.moveTaskToFrontLocked(sourceTask, noAnimation, options,
                                    r.appTimeTracker, <span class="hljs-string">"sourceTaskToFront"</span>);
                        }
                        <span class="hljs-keyword">if</span> (!addingToTask &amp;&amp; (launchFlags&amp;Intent.FLAG_ACTIVITY_CLEAR_TOP) != <span class="hljs-number">0</span>) {
                            ActivityRecord top = sourceTask.performClearTaskLocked(r, launchFlags);
                            keepCurTransition = <span class="hljs-keyword">true</span>;
                            <span class="hljs-keyword">if</span> (top != <span class="hljs-keyword">null</span>) {
                                <span class="hljs-comment">//触发onNewIntent()</span>
                                top.deliverNewIntentLocked(callingUid, r.intent, r.launchedFromPackage);
                                targetStack.mLastPausedActivity = <span class="hljs-keyword">null</span>;
                                <span class="hljs-keyword">if</span> (doResume) {
                                    targetStack.resumeTopActivityLocked(<span class="hljs-keyword">null</span>);
                                }
                                ActivityOptions.abort(options);
                                <span class="hljs-keyword">return</span> ActivityManager.START_DELIVERED_TO_TOP;
                            }
                        } <span class="hljs-keyword">else</span> <span class="hljs-keyword">if</span> (!addingToTask &amp;&amp;
                                (launchFlags&amp;Intent.FLAG_ACTIVITY_REORDER_TO_FRONT) != <span class="hljs-number">0</span>) {
                            <span class="hljs-keyword">final</span> ActivityRecord top = sourceTask.findActivityInHistoryLocked(r);
                            <span class="hljs-keyword">if</span> (top != <span class="hljs-keyword">null</span>) {
                                <span class="hljs-keyword">final</span> TaskRecord task = top.task;
                                task.moveActivityToFrontLocked(top);
                                top.updateOptionsLocked(options);
                                <span class="hljs-comment">//触发onNewIntent()</span>
                                top.deliverNewIntentLocked(callingUid, r.intent, r.launchedFromPackage);
                                targetStack.mLastPausedActivity = <span class="hljs-keyword">null</span>;
                                <span class="hljs-keyword">if</span> (doResume) {
                                    targetStack.resumeTopActivityLocked(<span class="hljs-keyword">null</span>);
                                }
                                <span class="hljs-keyword">return</span> ActivityManager.START_DELIVERED_TO_TOP;
                            }
                        }
                        r.setTask(sourceTask, <span class="hljs-keyword">null</span>);
                    } <span class="hljs-keyword">else</span> <span class="hljs-keyword">if</span> (inTask != <span class="hljs-keyword">null</span>) {
                        <span class="hljs-keyword">if</span> (isLockTaskModeViolation(inTask)) {
                            <span class="hljs-keyword">return</span> ActivityManager.START_RETURN_LOCK_TASK_MODE_VIOLATION;
                        }
                        targetStack = inTask.stack;
                        targetStack.moveTaskToFrontLocked(inTask, noAnimation, options, r.appTimeTracker,
                                <span class="hljs-string">"inTaskToFront"</span>);
                
                        ActivityRecord top = inTask.getTopActivity();
                        <span class="hljs-keyword">if</span> (top != <span class="hljs-keyword">null</span> &amp;&amp; top.realActivity.equals(r.realActivity) &amp;&amp; top.userId == r.userId) {
                            <span class="hljs-keyword">if</span> ((launchFlags &amp; Intent.FLAG_ACTIVITY_SINGLE_TOP) != <span class="hljs-number">0</span>
                                    || launchSingleTop || launchSingleTask) {
                                <span class="hljs-keyword">if</span> ((startFlags&amp;ActivityManager.START_FLAG_ONLY_IF_NEEDED) != <span class="hljs-number">0</span>) {
                                    <span class="hljs-keyword">return</span> ActivityManager.START_RETURN_INTENT_TO_CALLER;
                                }
                                <span class="hljs-comment">//触发onNewIntent()</span>
                                top.deliverNewIntentLocked(callingUid, r.intent, r.launchedFromPackage);
                                <span class="hljs-keyword">return</span> ActivityManager.START_DELIVERED_TO_TOP;
                            }
                        }
                
                        <span class="hljs-keyword">if</span> (!addingToTask) {
                            ActivityOptions.abort(options);
                            <span class="hljs-keyword">return</span> ActivityManager.START_TASK_TO_FRONT;
                        }
                
                        r.setTask(inTask, <span class="hljs-keyword">null</span>);
                
                    } <span class="hljs-keyword">else</span> {
                        targetStack = computeStackFocus(r, newTask);
                        targetStack.moveToFront(<span class="hljs-string">"addingToTopTask"</span>);
                        ActivityRecord prev = targetStack.topActivity();
                        r.setTask(prev != <span class="hljs-keyword">null</span> ? prev.task : targetStack.createTaskRecord(getNextTaskId(),
                                        r.info, intent, <span class="hljs-keyword">null</span>, <span class="hljs-keyword">null</span>, <span class="hljs-keyword">true</span>), <span class="hljs-keyword">null</span>);
                        mWindowManager.moveTaskToTop(r.task.taskId);
                    }
                
                    mService.grantUriPermissionFromIntentLocked(callingUid, r.packageName,
                            intent, r.getUriPermissionsLocked(), r.userId);
                
                    <span class="hljs-keyword">if</span> (sourceRecord != <span class="hljs-keyword">null</span> &amp;&amp; sourceRecord.isRecentsActivity()) {
                        r.task.setTaskToReturnTo(RECENTS_ACTIVITY_TYPE);
                    }
                
                    targetStack.mLastPausedActivity = <span class="hljs-keyword">null</span>;
                    <span class="hljs-comment">//创建activity [见流程2.10]</span>
                    targetStack.startActivityLocked(r, newTask, doResume, keepCurTransition, options);
                    <span class="hljs-keyword">if</span> (!launchTaskBehind) {
                        mService.setFocusedActivityLocked(r, <span class="hljs-string">"startedActivity"</span>);
                    }
                    <span class="hljs-keyword">return</span> ActivityManager.START_SUCCESS;
                }
                </code></pre>
                
                找到或创建新的Activit所属于的Task对象，之后调用AS.startActivityLocked
                
                #### Launch Mode
                
                <p>先来说说在ActivityInfo.java中定义了4类Launch Mode：</p>
                
                <ul>
                  <li>LAUNCH_MULTIPLE(standard)：最常见的情形，每次启动Activity都是创建新的Activity;</li>
                  <li>LAUNCH_SINGLE_TOP: 当Task顶部存在同一个Activity则不再重新创建；其余情况同上；</li>
                  <li>LAUNCH_SINGLE_TASK：当Task栈存在同一个Activity(不在task顶部)，则不重新创建，而移除该Activity上面其他的Activity；其余情况同上；</li>
                  <li>LAUNCH_SINGLE_INSTANCE：每个Task只有一个Activity.</li>
                </ul>
                    
                <p>再来说说几个常见的flag含义：</p>
                
                <ul>
                  <li>FLAG_ACTIVITY_NEW_TASK：将Activity放入一个新启动的Task；</li>
                  <li>FLAG_ACTIVITY_CLEAR_TASK：启动Activity时，将目标Activity关联的Task清除，再启动新Task，将该Activity放入该Task。该flags跟FLAG_ACTIVITY_NEW_TASK配合使用。</li>
                  <li>FLAG_ACTIVITY_CLEAR_TOP：启动非栈顶Activity时，先清除该Activity之上的Activity。例如Task已有A、B、C3个Activity，启动A，则清除B，C。类似于SingleTop。</li>
                </ul>
                
                <p>最后再说说：设置<code class="highlighter-rouge">FLAG_ACTIVITY_NEW_TASK</code>的几个情况：</p>
                
                <ul>
                  <li>调用者并不是Activity context；</li>
                  <li>调用者activity带有single instance；</li>
                  <li>目标activity带有single instance或者single task；</li>
                  <li>调用者处于finishing状态；</li>
                </ul>
                
                #### AS.startActivityLocked
                
                <p>[-&gt; ActivityStack.java]</p>
                
                <pre class="highlight"><code class="hljs java"><span class="hljs-function"><span class="hljs-keyword">final</span> <span class="hljs-keyword">void</span> <span class="hljs-title">startActivityLocked</span><span class="hljs-params">(ActivityRecord r, <span class="hljs-keyword">boolean</span> newTask,
                        <span class="hljs-keyword">boolean</span> doResume, <span class="hljs-keyword">boolean</span> keepCurTransition, Bundle options)</span> </span>{
                    TaskRecord rTask = r.task;
                    <span class="hljs-keyword">final</span> <span class="hljs-keyword">int</span> taskId = rTask.taskId;
                    <span class="hljs-keyword">if</span> (!r.mLaunchTaskBehind &amp;&amp; (taskForIdLocked(taskId) == <span class="hljs-keyword">null</span> || newTask)) {
                        <span class="hljs-comment">//task中的上一个activity已被移除，或者ams重用该task,则将该task移到顶部</span>
                        insertTaskAtTop(rTask, r);
                        mWindowManager.moveTaskToTop(taskId);
                    }
                    TaskRecord task = <span class="hljs-keyword">null</span>;
                    <span class="hljs-keyword">if</span> (!newTask) {
                        <span class="hljs-keyword">boolean</span> startIt = <span class="hljs-keyword">true</span>;
                        <span class="hljs-keyword">for</span> (<span class="hljs-keyword">int</span> taskNdx = mTaskHistory.size() - <span class="hljs-number">1</span>; taskNdx &gt;= <span class="hljs-number">0</span>; --taskNdx) {
                            task = mTaskHistory.get(taskNdx);
                            <span class="hljs-keyword">if</span> (task.getTopActivity() == <span class="hljs-keyword">null</span>) {
                                <span class="hljs-comment">//该task所有activity都finishing</span>
                                <span class="hljs-keyword">continue</span>;
                            }
                            <span class="hljs-keyword">if</span> (task == r.task) {
                                <span class="hljs-keyword">if</span> (!startIt) {
                                    task.addActivityToTop(r);
                                    r.putInHistory();
                                    mWindowManager.addAppToken(task.mActivities.indexOf(r), r.appToken,
                                            r.task.taskId, mStackId, r.info.screenOrientation, r.fullscreen,
                                            (r.info.flags &amp; ActivityInfo.FLAG_SHOW_FOR_ALL_USERS) != <span class="hljs-number">0</span>,
                                            r.userId, r.info.configChanges, task.voiceSession != <span class="hljs-keyword">null</span>,
                                            r.mLaunchTaskBehind);
                                    ActivityOptions.abort(options);
                                    <span class="hljs-keyword">return</span>;
                                }
                                <span class="hljs-keyword">break</span>;
                            } <span class="hljs-keyword">else</span> <span class="hljs-keyword">if</span> (task.numFullscreen &gt; <span class="hljs-number">0</span>) {
                                startIt = <span class="hljs-keyword">false</span>;
                            }
                        }
                    }
                
                    <span class="hljs-keyword">if</span> (task == r.task &amp;&amp; mTaskHistory.indexOf(task) != (mTaskHistory.size() - <span class="hljs-number">1</span>)) {
                        mStackSupervisor.mUserLeaving = <span class="hljs-keyword">false</span>;
                    }
                
                    task = r.task;
                    task.addActivityToTop(r);
                    task.setFrontOfTask();
                
                    r.putInHistory();
                    mActivityTrigger.activityStartTrigger(r.intent, r.info, r.appInfo);
                    <span class="hljs-keyword">if</span> (!isHomeStack() || numActivities() &gt; <span class="hljs-number">0</span>) {
                        <span class="hljs-comment">//当切换到新的task，或者下一个activity进程目前并没有运行，则</span>
                        <span class="hljs-keyword">boolean</span> showStartingIcon = newTask;
                        ProcessRecord proc = r.app;
                        <span class="hljs-keyword">if</span> (proc == <span class="hljs-keyword">null</span>) {
                            proc = mService.mProcessNames.get(r.processName, r.info.applicationInfo.uid);
                        }
                
                        <span class="hljs-keyword">if</span> (proc == <span class="hljs-keyword">null</span> || proc.thread == <span class="hljs-keyword">null</span>) {
                            showStartingIcon = <span class="hljs-keyword">true</span>;
                        }
                        <span class="hljs-keyword">if</span> ((r.intent.getFlags() &amp; Intent.FLAG_ACTIVITY_NO_ANIMATION) != <span class="hljs-number">0</span>) {
                            mWindowManager.prepareAppTransition(AppTransition.TRANSIT_NONE, keepCurTransition);
                            mNoAnimActivities.add(r);
                        } <span class="hljs-keyword">else</span> {
                            mWindowManager.prepareAppTransition(newTask
                                    ? r.mLaunchTaskBehind
                                            ? AppTransition.TRANSIT_TASK_OPEN_BEHIND
                                            : AppTransition.TRANSIT_TASK_OPEN
                                    : AppTransition.TRANSIT_ACTIVITY_OPEN, keepCurTransition);
                            mNoAnimActivities.remove(r);
                        }
                        mWindowManager.addAppToken(task.mActivities.indexOf(r),
                                r.appToken, r.task.taskId, mStackId, r.info.screenOrientation, r.fullscreen,
                                (r.info.flags &amp; ActivityInfo.FLAG_SHOW_FOR_ALL_USERS) != <span class="hljs-number">0</span>, r.userId,
                                r.info.configChanges, task.voiceSession != <span class="hljs-keyword">null</span>, r.mLaunchTaskBehind);
                        <span class="hljs-keyword">boolean</span> doShow = <span class="hljs-keyword">true</span>;
                        <span class="hljs-keyword">if</span> (newTask) {
                            <span class="hljs-keyword">if</span> ((r.intent.getFlags() &amp; Intent.FLAG_ACTIVITY_RESET_TASK_IF_NEEDED) != <span class="hljs-number">0</span>) {
                                resetTaskIfNeededLocked(r, r);
                                doShow = topRunningNonDelayedActivityLocked(<span class="hljs-keyword">null</span>) == r;
                            }
                        } <span class="hljs-keyword">else</span> <span class="hljs-keyword">if</span> (options != <span class="hljs-keyword">null</span> &amp;&amp; <span class="hljs-keyword">new</span> ActivityOptions(options).getAnimationType()
                                == ActivityOptions.ANIM_SCENE_TRANSITION) {
                            doShow = <span class="hljs-keyword">false</span>;
                        }
                        <span class="hljs-keyword">if</span> (r.mLaunchTaskBehind) {
                            mWindowManager.setAppVisibility(r.appToken, <span class="hljs-keyword">true</span>);
                            ensureActivitiesVisibleLocked(<span class="hljs-keyword">null</span>, <span class="hljs-number">0</span>);
                        } <span class="hljs-keyword">else</span> <span class="hljs-keyword">if</span> (SHOW_APP_STARTING_PREVIEW &amp;&amp; doShow) {
                            ActivityRecord prev = mResumedActivity;
                            <span class="hljs-keyword">if</span> (prev != <span class="hljs-keyword">null</span>) {
                                <span class="hljs-comment">//当前activity所属不同的task</span>
                                <span class="hljs-keyword">if</span> (prev.task != r.task) {
                                    prev = <span class="hljs-keyword">null</span>;
                                }
                                <span class="hljs-comment">//当前activity已经displayed</span>
                                <span class="hljs-keyword">else</span> <span class="hljs-keyword">if</span> (prev.nowVisible) {
                                    prev = <span class="hljs-keyword">null</span>;
                                }
                            }
                
                            mWindowManager.setAppStartingWindow(
                                    r.appToken, r.packageName, r.theme,
                                    mService.compatibilityInfoForPackageLocked(
                                             r.info.applicationInfo), r.nonLocalizedLabel,
                                    r.labelRes, r.icon, r.logo, r.windowFlags,
                                    prev != <span class="hljs-keyword">null</span> ? prev.appToken : <span class="hljs-keyword">null</span>, showStartingIcon);
                            r.mStartingWindowShown = <span class="hljs-keyword">true</span>;
                        }
                    } <span class="hljs-keyword">else</span> {
                        mWindowManager.addAppToken(task.mActivities.indexOf(r), r.appToken,
                                r.task.taskId, mStackId, r.info.screenOrientation, r.fullscreen,
                                (r.info.flags &amp; ActivityInfo.FLAG_SHOW_FOR_ALL_USERS) != <span class="hljs-number">0</span>, r.userId,
                                r.info.configChanges, task.voiceSession != <span class="hljs-keyword">null</span>, r.mLaunchTaskBehind);
                        ActivityOptions.abort(options);
                        options = <span class="hljs-keyword">null</span>;
                    }
                
                    <span class="hljs-keyword">if</span> (doResume) {
                        <span class="hljs-comment">// [见流程2.11]</span>
                        mStackSupervisor.resumeTopActivitiesLocked(<span class="hljs-keyword">this</span>, r, options);
                    }
                }
                </code></pre>
                
                #### ASS.resumeTopActivitiesLocked
                
                <pre class="highlight"><code class="hljs java"><span class="hljs-function"><span class="hljs-keyword">boolean</span> <span class="hljs-title">resumeTopActivitiesLocked</span><span class="hljs-params">(ActivityStack targetStack, ActivityRecord target,
                        Bundle targetOptions)</span> </span>{
                    <span class="hljs-keyword">if</span> (targetStack == <span class="hljs-keyword">null</span>) {
                        targetStack = mFocusedStack;
                    }
                
                    <span class="hljs-keyword">boolean</span> result = <span class="hljs-keyword">false</span>;
                    <span class="hljs-keyword">if</span> (isFrontStack(targetStack)) {
                        <span class="hljs-comment">//[见流程2.12]</span>
                        result = targetStack.resumeTopActivityLocked(target, targetOptions);
                    }
                
                    <span class="hljs-keyword">for</span> (<span class="hljs-keyword">int</span> displayNdx = mActivityDisplays.size() - <span class="hljs-number">1</span>; displayNdx &gt;= <span class="hljs-number">0</span>; --displayNdx) {
                        <span class="hljs-keyword">final</span> ArrayList&lt;ActivityStack&gt; stacks = mActivityDisplays.valueAt(displayNdx).mStacks;
                        <span class="hljs-keyword">for</span> (<span class="hljs-keyword">int</span> stackNdx = stacks.size() - <span class="hljs-number">1</span>; stackNdx &gt;= <span class="hljs-number">0</span>; --stackNdx) {
                            <span class="hljs-keyword">final</span> ActivityStack stack = stacks.get(stackNdx);
                            <span class="hljs-keyword">if</span> (stack == targetStack) {
                                <span class="hljs-comment">//上面刚已启动</span>
                                <span class="hljs-keyword">continue</span>;
                            }
                            <span class="hljs-keyword">if</span> (isFrontStack(stack)) {
                                stack.resumeTopActivityLocked(<span class="hljs-keyword">null</span>);
                            }
                        }
                    }
                    <span class="hljs-keyword">return</span> result;
                }
                </code></pre>
                
                #### AS.resumeTopActivityLocked
                    
                <pre class="highlight"><code class="hljs java"><span class="hljs-function"><span class="hljs-keyword">final</span> <span class="hljs-keyword">boolean</span> <span class="hljs-title">resumeTopActivityLocked</span><span class="hljs-params">(ActivityRecord prev, Bundle options)</span> </span>{
                    <span class="hljs-keyword">if</span> (mStackSupervisor.inResumeTopActivity) {
                        <span class="hljs-keyword">return</span> <span class="hljs-keyword">false</span>; <span class="hljs-comment">//防止递归启动</span>
                    }
                
                    <span class="hljs-keyword">boolean</span> result = <span class="hljs-keyword">false</span>;
                    <span class="hljs-keyword">try</span> {
                        mStackSupervisor.inResumeTopActivity = <span class="hljs-keyword">true</span>;
                        <span class="hljs-keyword">if</span> (mService.mLockScreenShown == ActivityManagerService.LOCK_SCREEN_LEAVING) {
                            mService.mLockScreenShown = ActivityManagerService.LOCK_SCREEN_HIDDEN;
                            mService.updateSleepIfNeededLocked();
                        }
                        <span class="hljs-comment">//[见流程2.13]</span>
                        result = resumeTopActivityInnerLocked(prev, options);
                    } <span class="hljs-keyword">finally</span> {
                        mStackSupervisor.inResumeTopActivity = <span class="hljs-keyword">false</span>;
                    }
                    <span class="hljs-keyword">return</span> result;
                }
                </code></pre>
                
                inResumeTopActivity用于保证每次只有一个Activity执行resumeTopActivityLocked()操作.
                
                ####AS.resumeTopActivityInnerLocked
                
                <pre class="highlight"><code class="hljs java"><span class="hljs-function"><span class="hljs-keyword">private</span> <span class="hljs-keyword">boolean</span> <span class="hljs-title">resumeTopActivityInnerLocked</span><span class="hljs-params">(ActivityRecord prev, Bundle options)</span> </span>{
                    ... <span class="hljs-comment">//系统没有进入booting或booted状态，则不允许启动Activity</span>
                
                    ActivityRecord parent = mActivityContainer.mParentActivity;
                    <span class="hljs-keyword">if</span> ((parent != <span class="hljs-keyword">null</span> &amp;&amp; parent.state != ActivityState.RESUMED) ||
                            !mActivityContainer.isAttachedLocked()) {
                        <span class="hljs-keyword">return</span> <span class="hljs-keyword">false</span>;
                    }
                    <span class="hljs-comment">//top running之后的任意处于初始化状态且有显示StartingWindow, 则移除StartingWindow</span>
                    cancelInitializingActivities();
                
                    <span class="hljs-comment">//找到第一个没有finishing的栈顶activity</span>
                    <span class="hljs-keyword">final</span> ActivityRecord next = topRunningActivityLocked(<span class="hljs-keyword">null</span>);
                
                    <span class="hljs-keyword">final</span> <span class="hljs-keyword">boolean</span> userLeaving = mStackSupervisor.mUserLeaving;
                    mStackSupervisor.mUserLeaving = <span class="hljs-keyword">false</span>;
                
                    <span class="hljs-keyword">final</span> TaskRecord prevTask = prev != <span class="hljs-keyword">null</span> ? prev.task : <span class="hljs-keyword">null</span>;
                    <span class="hljs-keyword">if</span> (next == <span class="hljs-keyword">null</span>) {
                        <span class="hljs-keyword">final</span> String reason = <span class="hljs-string">"noMoreActivities"</span>;
                        <span class="hljs-keyword">if</span> (!mFullscreen) {
                            <span class="hljs-comment">//当该栈没有全屏，则尝试聚焦到下一个可见的stack</span>
                            <span class="hljs-keyword">final</span> ActivityStack stack = getNextVisibleStackLocked();
                            <span class="hljs-keyword">if</span> (adjustFocusToNextVisibleStackLocked(stack, reason)) {
                                <span class="hljs-keyword">return</span> mStackSupervisor.resumeTopActivitiesLocked(stack, prev, <span class="hljs-keyword">null</span>);
                            }
                        }
                        ActivityOptions.abort(options);
                        <span class="hljs-keyword">final</span> <span class="hljs-keyword">int</span> returnTaskType = prevTask == <span class="hljs-keyword">null</span> || !prevTask.isOverHomeStack() ?
                                HOME_ACTIVITY_TYPE : prevTask.getTaskToReturnTo();
                        <span class="hljs-comment">//启动home桌面activity</span>
                        <span class="hljs-keyword">return</span> isOnHomeDisplay() &amp;&amp;
                                mStackSupervisor.resumeHomeStackTask(returnTaskType, prev, reason);
                    }
                
                    next.delayedResume = <span class="hljs-keyword">false</span>;
                
                    <span class="hljs-keyword">if</span> (mResumedActivity == next &amp;&amp; next.state == ActivityState.RESUMED &amp;&amp;
                                mStackSupervisor.allResumedActivitiesComplete()) {
                        mWindowManager.executeAppTransition();
                        mNoAnimActivities.clear();
                        ActivityOptions.abort(options);
                        <span class="hljs-keyword">return</span> <span class="hljs-keyword">false</span>;
                    }
                
                    <span class="hljs-keyword">final</span> TaskRecord nextTask = next.task;
                    <span class="hljs-keyword">if</span> (prevTask != <span class="hljs-keyword">null</span> &amp;&amp; prevTask.stack == <span class="hljs-keyword">this</span> &amp;&amp;
                            prevTask.isOverHomeStack() &amp;&amp; prev.finishing &amp;&amp; prev.frontOfTask) {
                        <span class="hljs-keyword">if</span> (prevTask == nextTask) {
                            prevTask.setFrontOfTask();
                        } <span class="hljs-keyword">else</span> <span class="hljs-keyword">if</span> (prevTask != topTask()) {
                            <span class="hljs-keyword">final</span> <span class="hljs-keyword">int</span> taskNdx = mTaskHistory.indexOf(prevTask) + <span class="hljs-number">1</span>;
                            mTaskHistory.get(taskNdx).setTaskToReturnTo(HOME_ACTIVITY_TYPE);
                        } <span class="hljs-keyword">else</span> <span class="hljs-keyword">if</span> (!isOnHomeDisplay()) {
                            <span class="hljs-keyword">return</span> <span class="hljs-keyword">false</span>;
                        } <span class="hljs-keyword">else</span> <span class="hljs-keyword">if</span> (!isHomeStack()){
                            <span class="hljs-keyword">final</span> <span class="hljs-keyword">int</span> returnTaskType = prevTask == <span class="hljs-keyword">null</span> || !prevTask.isOverHomeStack() ?
                                    HOME_ACTIVITY_TYPE : prevTask.getTaskToReturnTo();
                            <span class="hljs-keyword">return</span> isOnHomeDisplay() &amp;&amp;
                                    mStackSupervisor.resumeHomeStackTask(returnTaskType, prev, <span class="hljs-string">"prevFinished"</span>);
                        }
                    }
                
                    <span class="hljs-comment">//处于睡眠或者关机状态，top activity已暂停的情况下</span>
                    <span class="hljs-keyword">if</span> (mService.isSleepingOrShuttingDown()
                            &amp;&amp; mLastPausedActivity == next
                            &amp;&amp; mStackSupervisor.allPausedActivitiesComplete()) {
                        mWindowManager.executeAppTransition();
                        mNoAnimActivities.clear();
                        ActivityOptions.abort(options);
                        <span class="hljs-keyword">return</span> <span class="hljs-keyword">false</span>;
                    }
                
                    <span class="hljs-keyword">if</span> (mService.mStartedUsers.get(next.userId) == <span class="hljs-keyword">null</span>) {
                        <span class="hljs-keyword">return</span> <span class="hljs-keyword">false</span>; <span class="hljs-comment">//拥有该activity的用户没有启动则直接返回</span>
                    }
                
                    mStackSupervisor.mStoppingActivities.remove(next);
                    mStackSupervisor.mGoingToSleepActivities.remove(next);
                    next.sleeping = <span class="hljs-keyword">false</span>;
                    mStackSupervisor.mWaitingVisibleActivities.remove(next);
                
                    mActivityTrigger.activityResumeTrigger(next.intent, next.info, next.appInfo);
                
                    <span class="hljs-keyword">if</span> (!mStackSupervisor.allPausedActivitiesComplete()) {
                        <span class="hljs-keyword">return</span> <span class="hljs-keyword">false</span>; <span class="hljs-comment">//当正处于暂停activity，则直接返回</span>
                    }
                
                    mStackSupervisor.setLaunchSource(next.info.applicationInfo.uid);
                
                    <span class="hljs-comment">//需要等待暂停当前activity完成，再resume top activity</span>
                    <span class="hljs-keyword">boolean</span> dontWaitForPause = (next.info.flags&amp;ActivityInfo.FLAG_RESUME_WHILE_PAUSING) != <span class="hljs-number">0</span>;
                    <span class="hljs-comment">//暂停其他Activity[见小节2.13.1]</span>
                    <span class="hljs-keyword">boolean</span> pausing = mStackSupervisor.pauseBackStacks(userLeaving, <span class="hljs-keyword">true</span>, dontWaitForPause);
                    <span class="hljs-keyword">if</span> (mResumedActivity != <span class="hljs-keyword">null</span>) {
                        <span class="hljs-comment">//当前resumd状态activity不为空，则需要先暂停该Activity</span>
                        pausing |= startPausingLocked(userLeaving, <span class="hljs-keyword">false</span>, <span class="hljs-keyword">true</span>, dontWaitForPause);
                    }
                    <span class="hljs-keyword">if</span> (pausing) {
                        <span class="hljs-keyword">if</span> (next.app != <span class="hljs-keyword">null</span> &amp;&amp; next.app.thread != <span class="hljs-keyword">null</span>) {
                            mService.updateLruProcessLocked(next.app, <span class="hljs-keyword">true</span>, <span class="hljs-keyword">null</span>);
                        }
                        <span class="hljs-keyword">return</span> <span class="hljs-keyword">true</span>;
                    }
                
                    <span class="hljs-keyword">if</span> (mService.isSleeping() &amp;&amp; mLastNoHistoryActivity != <span class="hljs-keyword">null</span> &amp;&amp;
                            !mLastNoHistoryActivity.finishing) {
                        requestFinishActivityLocked(mLastNoHistoryActivity.appToken, Activity.RESULT_CANCELED,
                                <span class="hljs-keyword">null</span>, <span class="hljs-string">"resume-no-history"</span>, <span class="hljs-keyword">false</span>);
                        mLastNoHistoryActivity = <span class="hljs-keyword">null</span>;
                    }
                
                    <span class="hljs-keyword">if</span> (prev != <span class="hljs-keyword">null</span> &amp;&amp; prev != next) {
                        <span class="hljs-keyword">if</span> (!mStackSupervisor.mWaitingVisibleActivities.contains(prev)
                                &amp;&amp; next != <span class="hljs-keyword">null</span> &amp;&amp; !next.nowVisible) {
                            mStackSupervisor.mWaitingVisibleActivities.add(prev);
                        } <span class="hljs-keyword">else</span> {
                            <span class="hljs-keyword">if</span> (prev.finishing) {
                                mWindowManager.setAppVisibility(prev.appToken, <span class="hljs-keyword">false</span>);
                            }
                        }
                    }
                
                    AppGlobals.getPackageManager().setPackageStoppedState(
                            next.packageName, <span class="hljs-keyword">false</span>, next.userId);
                
                    <span class="hljs-keyword">boolean</span> anim = <span class="hljs-keyword">true</span>;
                    <span class="hljs-keyword">if</span> (mIsAnimationBoostEnabled == <span class="hljs-keyword">true</span> &amp;&amp; mPerf == <span class="hljs-keyword">null</span>) {
                        mPerf = <span class="hljs-keyword">new</span> BoostFramework();
                    }
                    <span class="hljs-keyword">if</span> (prev != <span class="hljs-keyword">null</span>) {
                        <span class="hljs-keyword">if</span> (prev.finishing) {
                            <span class="hljs-keyword">if</span> (mNoAnimActivities.contains(prev)) {
                                anim = <span class="hljs-keyword">false</span>;
                                mWindowManager.prepareAppTransition(AppTransition.TRANSIT_NONE, <span class="hljs-keyword">false</span>);
                            } <span class="hljs-keyword">else</span> {
                                mWindowManager.prepareAppTransition(prev.task == next.task
                                        ? AppTransition.TRANSIT_ACTIVITY_CLOSE
                                        : AppTransition.TRANSIT_TASK_CLOSE, <span class="hljs-keyword">false</span>);
                                <span class="hljs-keyword">if</span>(prev.task != next.task &amp;&amp; mPerf != <span class="hljs-keyword">null</span>) {
                                   mPerf.perfLockAcquire(aBoostTimeOut, aBoostParamVal);
                                }
                            }
                            mWindowManager.setAppWillBeHidden(prev.appToken);
                            mWindowManager.setAppVisibility(prev.appToken, <span class="hljs-keyword">false</span>);
                        } <span class="hljs-keyword">else</span> {
                            <span class="hljs-keyword">if</span> (mNoAnimActivities.contains(next)) {
                                anim = <span class="hljs-keyword">false</span>;
                                mWindowManager.prepareAppTransition(AppTransition.TRANSIT_NONE, <span class="hljs-keyword">false</span>);
                            } <span class="hljs-keyword">else</span> {
                                mWindowManager.prepareAppTransition(prev.task == next.task
                                        ? AppTransition.TRANSIT_ACTIVITY_OPEN
                                        : next.mLaunchTaskBehind
                                                ? AppTransition.TRANSIT_TASK_OPEN_BEHIND
                                                : AppTransition.TRANSIT_TASK_OPEN, <span class="hljs-keyword">false</span>);
                                <span class="hljs-keyword">if</span>(prev.task != next.task &amp;&amp; mPerf != <span class="hljs-keyword">null</span>) {
                                    mPerf.perfLockAcquire(aBoostTimeOut, aBoostParamVal);
                                }
                            }
                        }
                    } <span class="hljs-keyword">else</span> {
                        <span class="hljs-keyword">if</span> (mNoAnimActivities.contains(next)) {
                            anim = <span class="hljs-keyword">false</span>;
                            mWindowManager.prepareAppTransition(AppTransition.TRANSIT_NONE, <span class="hljs-keyword">false</span>);
                        } <span class="hljs-keyword">else</span> {
                            mWindowManager.prepareAppTransition(AppTransition.TRANSIT_ACTIVITY_OPEN, <span class="hljs-keyword">false</span>);
                        }
                    }
                
                    Bundle resumeAnimOptions = <span class="hljs-keyword">null</span>;
                    <span class="hljs-keyword">if</span> (anim) {
                        ActivityOptions opts = next.getOptionsForTargetActivityLocked();
                        <span class="hljs-keyword">if</span> (opts != <span class="hljs-keyword">null</span>) {
                            resumeAnimOptions = opts.toBundle();
                        }
                        next.applyOptionsLocked();
                    } <span class="hljs-keyword">else</span> {
                        next.clearOptionsLocked();
                    }
                
                    ActivityStack lastStack = mStackSupervisor.getLastStack();
                    <span class="hljs-comment">//进程已存在的情况</span>
                    <span class="hljs-keyword">if</span> (next.app != <span class="hljs-keyword">null</span> &amp;&amp; next.app.thread != <span class="hljs-keyword">null</span>) {
                        <span class="hljs-comment">//activity正在成为可见</span>
                        mWindowManager.setAppVisibility(next.appToken, <span class="hljs-keyword">true</span>);
                
                        next.startLaunchTickingLocked();
                
                        ActivityRecord lastResumedActivity = lastStack == <span class="hljs-keyword">null</span> ? <span class="hljs-keyword">null</span> :lastStack.mResumedActivity;
                        ActivityState lastState = next.state;
                
                        mService.updateCpuStats();
                        <span class="hljs-comment">//设置Activity状态为resumed</span>
                        next.state = ActivityState.RESUMED;
                        mResumedActivity = next;
                        next.task.touchActiveTime();
                        mRecentTasks.addLocked(next.task);
                        mService.updateLruProcessLocked(next.app, <span class="hljs-keyword">true</span>, <span class="hljs-keyword">null</span>);
                        updateLRUListLocked(next);
                        mService.updateOomAdjLocked();
                
                        <span class="hljs-keyword">boolean</span> notUpdated = <span class="hljs-keyword">true</span>;
                        <span class="hljs-keyword">if</span> (mStackSupervisor.isFrontStack(<span class="hljs-keyword">this</span>)) {
                            Configuration config = mWindowManager.updateOrientationFromAppTokens(
                                    mService.mConfiguration,
                                    next.mayFreezeScreenLocked(next.app) ? next.appToken : <span class="hljs-keyword">null</span>);
                            <span class="hljs-keyword">if</span> (config != <span class="hljs-keyword">null</span>) {
                                next.frozenBeforeDestroy = <span class="hljs-keyword">true</span>;
                            }
                            notUpdated = !mService.updateConfigurationLocked(config, next, <span class="hljs-keyword">false</span>, <span class="hljs-keyword">false</span>);
                        }
                
                        <span class="hljs-keyword">if</span> (notUpdated) {
                            ActivityRecord nextNext = topRunningActivityLocked(<span class="hljs-keyword">null</span>);
                
                            <span class="hljs-keyword">if</span> (nextNext != next) {
                                mStackSupervisor.scheduleResumeTopActivities();
                            }
                            <span class="hljs-keyword">if</span> (mStackSupervisor.reportResumedActivityLocked(next)) {
                                mNoAnimActivities.clear();
                                <span class="hljs-keyword">return</span> <span class="hljs-keyword">true</span>;
                            }
                            <span class="hljs-keyword">return</span> <span class="hljs-keyword">false</span>;
                        }
                
                        <span class="hljs-keyword">try</span> {
                            <span class="hljs-comment">//分发所有pending结果.</span>
                            ArrayList&lt;ResultInfo&gt; a = next.results;
                            <span class="hljs-keyword">if</span> (a != <span class="hljs-keyword">null</span>) {
                                <span class="hljs-keyword">final</span> <span class="hljs-keyword">int</span> N = a.size();
                                <span class="hljs-keyword">if</span> (!next.finishing &amp;&amp; N &gt; <span class="hljs-number">0</span>) {
                                    next.app.thread.scheduleSendResult(next.appToken, a);
                                }
                            }
                
                            <span class="hljs-keyword">if</span> (next.newIntents != <span class="hljs-keyword">null</span>) {
                                next.app.thread.scheduleNewIntent(next.newIntents, next.appToken);
                            }
                
                            next.sleeping = <span class="hljs-keyword">false</span>;
                            mService.showAskCompatModeDialogLocked(next);
                            next.app.pendingUiClean = <span class="hljs-keyword">true</span>;
                            next.app.forceProcessStateUpTo(mService.mTopProcessState);
                            next.clearOptionsLocked();
                            <span class="hljs-comment">//触发onResume()</span>
                            next.app.thread.scheduleResumeActivity(next.appToken, next.app.repProcState,
                                    mService.isNextTransitionForward(), resumeAnimOptions);
                
                            mStackSupervisor.checkReadyForSleepLocked();
                
                        } <span class="hljs-keyword">catch</span> (Exception e) {
                            ...
                            <span class="hljs-keyword">return</span> <span class="hljs-keyword">true</span>;
                        }
                        next.visible = <span class="hljs-keyword">true</span>;
                        completeResumeLocked(next);
                        next.stopped = <span class="hljs-keyword">false</span>;
                
                    } <span class="hljs-keyword">else</span> {
                        <span class="hljs-keyword">if</span> (!next.hasBeenLaunched) {
                            next.hasBeenLaunched = <span class="hljs-keyword">true</span>;
                        } <span class="hljs-keyword">else</span> {
                            <span class="hljs-keyword">if</span> (SHOW_APP_STARTING_PREVIEW) {
                                mWindowManager.setAppStartingWindow(
                                        next.appToken, next.packageName, next.theme,
                                        mService.compatibilityInfoForPackageLocked(
                                                next.info.applicationInfo),
                                        next.nonLocalizedLabel,
                                        next.labelRes, next.icon, next.logo, next.windowFlags,
                                        <span class="hljs-keyword">null</span>, <span class="hljs-keyword">true</span>);
                            }
                        }
                        mStackSupervisor.startSpecificActivityLocked(next, <span class="hljs-keyword">true</span>, <span class="hljs-keyword">true</span>);
                    }
                    <span class="hljs-keyword">return</span> <span class="hljs-keyword">true</span>;
                }
                </code></pre>
                
                - 1.1.1.2、生命周期：
                
                - 1.1.1.3、Activity的Task：
            
           - 1.1.2、 加载速度的优化方案
        
       - 1.2 activity 启动模式
        
           * Stand
           
           * SingleTop
           
           * SingleTask
           
           * SingleInstance
       
       - 1.3 进程通信binder
       
       参考：
       
        Android 源码设计模式解析与实战
        <br/>
        <br/>
        Android 开发艺术探
        <br/>
        <br/>
        [Activity启动流程简直丧心病狂](https://www.jianshu.com/p/2bed70245c76)
        
        [ startActivity启动过程分析 ](http://gityuan.com/2016/03/12/start-activity/)

### Handler

   * ThreadLocal
   
   * HandlerThread
   
   * IntentService

### 系统服务
    
   * ActivityManagerService
   
   * WindowManagerService
   
   * 其他服务
   
   * AIDL和binder

### View
    
   * 自定义View
    
        * View的绘制
        
        * View的OnMeasure()
        
        * View的OnLayout()
        
        * View的OnDraw()
        
        * 自定义view滑动冲突解决
   
   * SurfaceView原理
   
   * ListView和RecycleView的区别缓存机制
   
   * ViewPager的页数缓存实现原理
    
### 内存优化
    
   * Android Studio工具使用
   
   * 布局优化
   
   * 查找内存泄漏
   
   * 大图处理
   
   * 图片处理和图片框架的缓存原理
   
        - LruCache
        
        - DiskLruCache
        
        - 列表的优化方案

### 项目经验   
    
   * 开源库的使用
   
   * 源码分析
        
        * Retrofit：
            
            - 1、Retrofit的设计风格
            
            - 2、RestfulApi的概念
            
            - 3、Retrofit的核心实现方式动态代理
            
            - 4、动态代理的优缺点
            
            - 5、如何优化
            
        * RxJava：
        
        * OkHttp：
        
### 数据库
    
 
### 架构考虑 
    
   * MVC   
   
   * MVP    
   
        - 1、to-do-mvp：
        
        - 2、dagger2-mvp：
        
        - 3、data-mvp 
   
   * MvvM
   
   * 插件化，设计思想和实现方案的理解
   
   * 组件化，设计思想和实现方案的理解
        
        * [组件化在项目中的使用姿势](https://www.jianshu.com/p/63fe09fe1a60)
   
### Android以外的技能
    
   * kotlin
   
   * js
   
   * React Native
   
   * Weex