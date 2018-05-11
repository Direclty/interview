# This Is The dagger2 Study:


## dagger是什么?
 
   >  注意：dagger是一个依赖注入库Dependence Injection(其中会涉及到注解Annotation)

   * [     说说依赖注入    ](https://droidyue.com/blog/2015/06/13/talk-show-about-dependency-injection/)
   
   * [ 探究Android中的注解 ](https://droidyue.com/blog/2016/08/14/android-annnotation/)
   
   * dagger2的好处
   
     * 简化前：
     
         <pre class="hljs java"><code class="java"><span class="hljs-keyword">public</span> <span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">LoginActivity</span> <span class="hljs-keyword">extends</span> <span class="hljs-title">AppCompatActivity</span> </span>{
           
               LoginActivityPresenter presenter;
           
               <span class="hljs-meta">@Override</span>
               <span class="hljs-function"><span class="hljs-keyword">protected</span> <span class="hljs-keyword">void</span> <span class="hljs-title">onCreate</span><span class="hljs-params">(Bundle savedInstanceState)</span> </span>{
                   <span class="hljs-keyword">super</span>.onCreate(savedInstanceState);
                   
                   OkHttpClient okHttpClient = <span class="hljs-keyword">new</span> OkHttpClient();
                   RestAdapter.Builder builder = <span class="hljs-keyword">new</span> RestAdapter.Builder();
                   builder.setClient(<span class="hljs-keyword">new</span> OkClient(okHttpClient));
                   RestAdapter restAdapter = builder.build();
                   ApiService apiService = restAdapter.create(ApiService.class);
                   UserManager userManager = UserManager.getInstance(apiService);
                   
                   UserDataStore userDataStore = UserDataStore.getInstance(
                           getSharedPreferences(<span class="hljs-string">"prefs"</span>, MODE_PRIVATE)
                   );
           
                   <span class="hljs-comment">//Presenter is initialized here</span>
                   presenter = <span class="hljs-keyword">new</span> LoginActivityPresenter(<span class="hljs-keyword">this</span>, userManager, userDataStore);
               }
           }
           
           </code>
         </pre>
         
     * 简化后：
     
        <pre class="hljs java"><code class="java"><span class="hljs-keyword">public</span> <span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">LoginActivity</span> <span class="hljs-keyword">extends</span> <span class="hljs-title">AppCompatActivity</span> </span>{
        
            <span class="hljs-meta">@Inject</span>
            LoginActivityPresenter presenter;
        
            <span class="hljs-meta">@Override</span>
            <span class="hljs-function"><span class="hljs-keyword">protected</span> <span class="hljs-keyword">void</span> <span class="hljs-title">onCreate</span><span class="hljs-params">(Bundle savedInstanceState)</span> </span>{
                <span class="hljs-keyword">super</span>.onCreate(savedInstanceState);
                
                <span class="hljs-comment">//Satisfy all dependencies requested by @Inject annotation</span>
                getDependenciesGraph().inject(<span class="hljs-keyword">this</span>);
            }
        }
        </code></pre>
        
   * dagger2的API：
   
        * 添加的
        
            <pre class="hljs java"><code class="java"><span class="hljs-keyword">public</span> <span class="hljs-meta">@interface</span> Component {
                Class&lt;?&gt;[] modules() <span class="hljs-keyword">default</span> {};
                Class&lt;?&gt;[] dependencies() <span class="hljs-keyword">default</span> {};
            }
            
            <span class="hljs-keyword">public</span> <span class="hljs-meta">@interface</span> Subcomponent {
                Class&lt;?&gt;[] modules() <span class="hljs-keyword">default</span> {};
            }
            
            <span class="hljs-keyword">public</span> <span class="hljs-meta">@interface</span> Module {
                Class&lt;?&gt;[] includes() <span class="hljs-keyword">default</span> {};
            }
            
            <span class="hljs-keyword">public</span> <span class="hljs-meta">@interface</span> Provides {
            }
            
            <span class="hljs-keyword">public</span> <span class="hljs-meta">@interface</span> MapKey {
                <span class="hljs-function"><span class="hljs-keyword">boolean</span> <span class="hljs-title">unwrapValue</span><span class="hljs-params">()</span> <span class="hljs-keyword">default</span> <span class="hljs-keyword">true</span></span>;
            }
            
            <span class="hljs-keyword">public</span> <span class="hljs-class"><span class="hljs-keyword">interface</span> <span class="hljs-title">Lazy</span>&lt;<span class="hljs-title">T</span>&gt; </span>{
                <span class="hljs-function">T <span class="hljs-title">get</span><span class="hljs-params">()</span></span>;
            }
            </code></pre>
        
        * 默认的：
            
            <pre class="hljs php"><code class="php"><span class="hljs-keyword">public</span> @<span class="hljs-class"><span class="hljs-keyword">interface</span> <span class="hljs-title">Inject</span> </span>{
            }
            
            <span class="hljs-keyword">public</span> @<span class="hljs-class"><span class="hljs-keyword">interface</span> <span class="hljs-title">Scope</span> </span>{
            }
            
            <span class="hljs-keyword">public</span> @<span class="hljs-class"><span class="hljs-keyword">interface</span> <span class="hljs-title">Qualifier</span> </span>{
            }
            </code></pre>
            
   
   
        
   
## dagger怎么用?

 * 1、dagger2中的@Inject和@Component的使用：
 
 * dagger1使用
 
     <pre class="hljs cpp"><code class="cpp"><span class="hljs-keyword">public</span> <span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">Rose</span> {</span>
         <span class="hljs-function"><span class="hljs-keyword">public</span> String <span class="hljs-title">whisper</span><span class="hljs-params">()</span>  </span>{
             <span class="hljs-keyword">return</span> <span class="hljs-string">"热恋"</span>;
         }
     }
     </code></pre>
 
     <pre class="hljs java"><code class="java"><span class="hljs-keyword">public</span> <span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">Pot</span> </span>{
     
         <span class="hljs-keyword">private</span> Rose rose;
     
         <span class="hljs-meta">@Inject</span>
         <span class="hljs-function"><span class="hljs-keyword">public</span> <span class="hljs-title">Pot</span><span class="hljs-params">(Rose rose)</span> </span>{
             <span class="hljs-keyword">this</span>.rose = rose;
         }
     
         <span class="hljs-function"><span class="hljs-keyword">public</span> String <span class="hljs-title">show</span><span class="hljs-params">()</span> </span>{
             <span class="hljs-keyword">return</span> rose.whisper();
         }
     }
    </code></pre>
 
     <pre class="hljs java"><code class="java"><span class="hljs-keyword">public</span> <span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">MainActivity</span> <span class="hljs-keyword">extends</span> <span class="hljs-title">AppCompatActivity</span> </span>{
     
         <span class="hljs-keyword">private</span> Pot pot;
     
         <span class="hljs-function"><span class="hljs-keyword">protected</span> <span class="hljs-keyword">void</span> <span class="hljs-title">onCreate</span><span class="hljs-params">(@Nullable Bundle savedInstanceState)</span> </span>{
             <span class="hljs-keyword">super</span>.onCreate(savedInstanceState);
     
             Rose rose = <span class="hljs-keyword">new</span> Rose();
             pot = <span class="hljs-keyword">new</span> Pot(rose);
     
             String show = pot.show();
             Toast.makeText(MainActivity.<span class="hljs-keyword">this</span>, show, Toast.LENGTH_SHORT).show();
         }
     }
    </code></pre>
    
 * dagger2使用
    
    <pre class="hljs java"><code class="java"><span class="hljs-keyword">public</span> <span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">Rose</span> </span>{
    
        <span class="hljs-meta">@Inject</span>
        <span class="hljs-function"><span class="hljs-keyword">public</span> <span class="hljs-title">Rose</span><span class="hljs-params">()</span> </span>{}
    
        <span class="hljs-function"><span class="hljs-keyword">public</span> String <span class="hljs-title">whisper</span><span class="hljs-params">()</span>  </span>{
            <span class="hljs-keyword">return</span> <span class="hljs-string">"热恋"</span>;
        }
    }
    </code></pre>
    
    <pre class="hljs java"><code class="java"><span class="hljs-keyword">public</span> <span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">Pot</span> </span>{
    
        <span class="hljs-keyword">private</span> Rose rose;
    
        <span class="hljs-meta">@Inject</span>
        <span class="hljs-function"><span class="hljs-keyword">public</span> <span class="hljs-title">Pot</span><span class="hljs-params">(Rose rose)</span> </span>{
            <span class="hljs-keyword">this</span>.rose = rose;
        }
    
        <span class="hljs-function"><span class="hljs-keyword">public</span> String <span class="hljs-title">show</span><span class="hljs-params">()</span> </span>{
            <span class="hljs-keyword">return</span> rose.whisper();
        }
    }
    </code></pre>
    
    <pre class="hljs java"><code class="java"><span class="hljs-meta">@Component</span>
    <span class="hljs-keyword">public</span> <span class="hljs-class"><span class="hljs-keyword">interface</span> <span class="hljs-title">MainActivityComponent</span> </span>{
        <span class="hljs-function"><span class="hljs-keyword">void</span> <span class="hljs-title">inject</span><span class="hljs-params">(MainActivity activity)</span></span>;
    }
    </code></pre>
    
    <pre class="hljs java"><code class="java"><span class="hljs-keyword">public</span> <span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">MainActivity</span> <span class="hljs-keyword">extends</span> <span class="hljs-title">AppCompatActivity</span> </span>{
    
        <span class="hljs-meta">@Inject</span>
        Pot pot;
    
        <span class="hljs-function"><span class="hljs-keyword">protected</span> <span class="hljs-keyword">void</span> <span class="hljs-title">onCreate</span><span class="hljs-params">(@Nullable Bundle savedInstanceState)</span> </span>{
            <span class="hljs-keyword">super</span>.onCreate(savedInstanceState);
    
            <span class="hljs-comment">// 这个类是重新编译后Dagger2自动生成的，所以写这行代码之前要先编译一次</span>
            <span class="hljs-comment">// Build --&gt; Rebuild Project</span>
            DaggerMainActivityComponent.create().inject(<span class="hljs-keyword">this</span>);
            String show = pot.show();
            Toast.makeText(MainActivity.<span class="hljs-keyword">this</span>, show, Toast.LENGTH_SHORT).show();
        }
    }
    </code></pre>
    
 * DaggerMainActivityComponent生成目录
 
    <div>
       <img src="https://upload-images.jianshu.io/upload_images/2202079-cdf20511b8e40939.png" />
    </div>
    
 * @inject使用
    
    * 1、构造注入
    
        * 构造函数上申明@inject(如上图的Rose类)
        
        * 注入构造器所需要的参数的依赖，如Pot类，构造上的Rose可被注入
        
    * 2、属性注入
        
        * 如MainActivity类，标注在属性上。被标注的属性不能用private修饰
        
        * 属性注入使用得最多
    
    * 3、方法注入
    
        * <pre class="hljs java"><code class="java"><span class="hljs-keyword">public</span> <span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">MainActivity</span> <span class="hljs-keyword">extends</span> <span class="hljs-title">AppCompatActivity</span> </span>{
          
              <span class="hljs-keyword">private</span> Pot pot;
          
              <span class="hljs-function"><span class="hljs-keyword">protected</span> <span class="hljs-keyword">void</span> <span class="hljs-title">onCreate</span><span class="hljs-params">(@Nullable Bundle savedInstanceState)</span> </span>{
                  <span class="hljs-keyword">super</span>.onCreate(savedInstanceState);
                  DaggerMainActivityComponent.create().inject(<span class="hljs-keyword">this</span>);
                  String show = pot.show();
                  Toast.makeText(MainActivity.<span class="hljs-keyword">this</span>, show, Toast.LENGTH_SHORT).show();
              }
          
              <span class="hljs-meta">@Inject</span>
              <span class="hljs-function"><span class="hljs-keyword">public</span> <span class="hljs-keyword">void</span> <span class="hljs-title">setPot</span><span class="hljs-params">(Pot pot)</span> </span>{
                  <span class="hljs-keyword">this</span>.pot = pot;
              }
          }
          </code></pre>
          
        > 注意：  标注在public方法上，Dagger2会在构造器执行之后立即调用这个方法。
                 方法注入和属性注入基本上没有区别， 那么什么时候应该使用方法注入呢？
                 比如该依赖需要this对象的时候，使用方法注入可以提供安全的this对象，因为方法注入是在构造器之后执行的。
                 
        * <pre class="hljs java"><code class="java"><span class="hljs-comment">   /**
               * Method injection is used here to safely reference {<span class="hljs-doctag">@code</span> this} after the object is created.
               * For more information, see Java Concurrency in Practice.
               */</span>
              <span class="hljs-meta">@Inject</span>
              <span class="hljs-function"><span class="hljs-keyword">void</span> <span class="hljs-title">setupListeners</span><span class="hljs-params">()</span> </span>{
                  mTasksView.setPresenter(<span class="hljs-keyword">this</span>);
              }
          </code></pre>
          
 * @Component使用
        
     * <pre class="hljs java"><code class="java"><span class="hljs-meta">   @Component</span>
          <span class="hljs-keyword">public</span> <span class="hljs-class"><span class="hljs-keyword">interface</span> <span class="hljs-title">MainActivityComponent</span> </span>{
              <span class="hljs-function"><span class="hljs-keyword">void</span> <span class="hljs-title">inject</span><span class="hljs-params">(MainActivity activity)</span></span>;
          }
       </code></pre>
 
       > 使用接口定义，并且@Component注解
       
     * 两种定义方式
        
        1. void inject(目标类 obj)，Dagger2会从目标类查找@inject注解，自动生成依赖注入的代码，调用inject可完成依赖的注入
        
        2. Object getObj()；如：Pot getPot()；
           Dagger2会到Pot类中去查找@Inject注解标注的构造器，自动生成提供Pot依赖的代码( 一个Component依赖另一个Component )
           
 * Inject和Component的关系
    
      <div>
        <img src="https://upload-images.jianshu.io/upload_images/2202079-51b78542dd3c8575.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/592" />
      </div>
    
    
   > Dagger2框架以Component中定义的方法作为入口，到目标类中寻找JSR-330定义的@Inject标注，生成一系列提供依赖的Factory类和注入依赖的Injector类。
        而Component则是联系Factory和Injector，最终完成依赖的注入。
      
      
   * 我们看下源码（请对应上面的Dagger2 apt图一起看）：
 
   * Rose_Factory和Pot_Factory分别对应Rose类和Pot类的构造器上的@Inject注解。
     而Factory其实是个Provider对象
       
       <pre class="hljs java"><code class="java"><span class="hljs-keyword">public</span> <span class="hljs-class"><span class="hljs-keyword">interface</span> <span class="hljs-title">Provider</span>&lt;<span class="hljs-title">T</span>&gt; </span>{
       
           <span class="hljs-comment">/**
            * Provides a fully-constructed and injected instance of {<span class="hljs-doctag">@code</span> T}.
            *
            * <span class="hljs-doctag">@throws</span> RuntimeException if the injector encounters an error while
            *  providing an instance. For example, if an injectable member on
            *  {<span class="hljs-doctag">@code</span> T} throws an exception, the injector may wrap the exception
            *  and throw it to the caller of {<span class="hljs-doctag">@code</span> get()}. Callers should not try
            *  to handle such exceptions as the behavior may vary across injector
            *  implementations and even different configurations of the same injector.
            */</span>
           <span class="hljs-function">T <span class="hljs-title">get</span><span class="hljs-params">()</span></span>;
       }
       </code></pre>
       
       <pre class="hljs java"><code class="java"><span class="hljs-keyword">public</span> <span class="hljs-class"><span class="hljs-keyword">interface</span> <span class="hljs-title">Factory</span>&lt;<span class="hljs-title">T</span>&gt; <span class="hljs-keyword">extends</span> <span class="hljs-title">Provider</span>&lt;<span class="hljs-title">T</span>&gt; </span>{}
       </code></pre>
       
       <pre class="hljs java"><code class="java"><span class="hljs-keyword">public</span> <span class="hljs-keyword">enum</span> Rose_Factory implements Factory&lt;Rose&gt; {
         INSTANCE;
       
         <span class="hljs-meta">@Override</span>
         <span class="hljs-function"><span class="hljs-keyword">public</span> Rose <span class="hljs-title">get</span><span class="hljs-params">()</span> </span>{
           <span class="hljs-keyword">return</span> <span class="hljs-keyword">new</span> Rose();
         }
       
         <span class="hljs-function"><span class="hljs-keyword">public</span> <span class="hljs-keyword">static</span> Factory&lt;Rose&gt; <span class="hljs-title">create</span><span class="hljs-params">()</span> </span>{
           <span class="hljs-keyword">return</span> INSTANCE;
         }
       }
       </code></pre>
   
  * Pot对象依赖Rose，所以直接将RoseProvide作为参数传入了。
  
      <pre class="hljs java"><code class="java"><span class="hljs-keyword">public</span> <span class="hljs-keyword">final</span> <span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">Pot_Factory</span> <span class="hljs-keyword">implements</span> <span class="hljs-title">Factory</span>&lt;<span class="hljs-title">Pot</span>&gt; </span>{
        <span class="hljs-keyword">private</span> <span class="hljs-keyword">final</span> Provider&lt;Rose&gt; roseProvider;
      
        <span class="hljs-function"><span class="hljs-keyword">public</span> <span class="hljs-title">Pot_Factory</span><span class="hljs-params">(Provider&lt;Rose&gt; roseProvider)</span> </span>{
          <span class="hljs-keyword">assert</span> roseProvider != <span class="hljs-keyword">null</span>;
          <span class="hljs-keyword">this</span>.roseProvider = roseProvider;
        }
      
        <span class="hljs-meta">@Override</span>
        <span class="hljs-function"><span class="hljs-keyword">public</span> Pot <span class="hljs-title">get</span><span class="hljs-params">()</span> </span>{
          <span class="hljs-keyword">return</span> <span class="hljs-keyword">new</span> Pot(roseProvider.get());
        }
      
        <span class="hljs-function"><span class="hljs-keyword">public</span> <span class="hljs-keyword">static</span> Factory&lt;Pot&gt; <span class="hljs-title">create</span><span class="hljs-params">(Provider&lt;Rose&gt; roseProvider)</span> </span>{
          <span class="hljs-keyword">return</span> <span class="hljs-keyword">new</span> Pot_Factory(roseProvider);
        }
      }
      </code></pre>
  
  * MainActivity上的@Inject属性或方法注解，则对应MainActivity_MembersInjector类
  
    <pre class="hljs java"><code class="java"><span class="hljs-keyword">public</span> <span class="hljs-class"><span class="hljs-keyword">interface</span> <span class="hljs-title">MembersInjector</span>&lt;<span class="hljs-title">T</span>&gt; </span>{
    
      <span class="hljs-comment">/**
       * Injects dependencies into the fields and methods of {<span class="hljs-doctag">@code</span> instance}. Ignores the presence or
       * absence of an injectable constructor.
       *
       * &lt;p&gt;Whenever the object graph creates an instance, it performs this injection automatically
       * (after first performing constructor injection), so if you're able to let the object graph
       * create all your objects for you, you'll never need to use this method.
       *
       * <span class="hljs-doctag">@param</span> instance into which members are to be injected
       * <span class="hljs-doctag">@throws</span> NullPointerException if {<span class="hljs-doctag">@code</span> instance} is {<span class="hljs-doctag">@code</span> null}
       */</span>
      <span class="hljs-function"><span class="hljs-keyword">void</span> <span class="hljs-title">injectMembers</span><span class="hljs-params">(T instance)</span></span>;
    }
    </code></pre>
    
    <pre class="hljs java"><code class="java"><span class="hljs-keyword">public</span> <span class="hljs-keyword">final</span> <span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">MainActivity_MembersInjector</span> <span class="hljs-keyword">implements</span> <span class="hljs-title">MembersInjector</span>&lt;<span class="hljs-title">MainActivity</span>&gt; </span>{
      <span class="hljs-keyword">private</span> <span class="hljs-keyword">final</span> Provider&lt;Pot&gt; potProvider;
    
      <span class="hljs-function"><span class="hljs-keyword">public</span> <span class="hljs-title">MainActivity_MembersInjector</span><span class="hljs-params">(Provider&lt;Pot&gt; potProvider)</span> </span>{
        <span class="hljs-keyword">assert</span> potProvider != <span class="hljs-keyword">null</span>;
        <span class="hljs-keyword">this</span>.potProvider = potProvider;
      }
    
      <span class="hljs-function"><span class="hljs-keyword">public</span> <span class="hljs-keyword">static</span> MembersInjector&lt;MainActivity&gt; <span class="hljs-title">create</span><span class="hljs-params">(Provider&lt;Pot&gt; potProvider)</span> </span>{
        <span class="hljs-keyword">return</span> <span class="hljs-keyword">new</span> MainActivity_MembersInjector(potProvider);
      }
    
      <span class="hljs-meta">@Override</span>
      <span class="hljs-function"><span class="hljs-keyword">public</span> <span class="hljs-keyword">void</span> <span class="hljs-title">injectMembers</span><span class="hljs-params">(MainActivity instance)</span> </span>{
        <span class="hljs-keyword">if</span> (instance == <span class="hljs-keyword">null</span>) {
          <span class="hljs-keyword">throw</span> <span class="hljs-keyword">new</span> NullPointerException(<span class="hljs-string">"Cannot inject members into a null reference"</span>);
        }
        instance.pot = potProvider.get();
      }
    
      <span class="hljs-function"><span class="hljs-keyword">public</span> <span class="hljs-keyword">static</span> <span class="hljs-keyword">void</span> <span class="hljs-title">injectPot</span><span class="hljs-params">(MainActivity instance, Provider&lt;Pot&gt; potProvider)</span> </span>{
        instance.pot = potProvider.get();
      }
    }
    </code></pre>
    
 * 最后是DaggerMainActivityComponent类，对应@Component注解就不多说了。这是Dagger2解析JSR-330的入口。
   它联系Factory和MainActivity两个类完成注入。
   
    <pre class="hljs java"><code class="java"><span class="hljs-keyword">public</span> <span class="hljs-keyword">final</span> <span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">DaggerMainActivityComponent</span> <span class="hljs-keyword">implements</span> <span class="hljs-title">MainActivityComponent</span> </span>{
      <span class="hljs-keyword">private</span> Provider&lt;Pot&gt; potProvider;
    
      <span class="hljs-keyword">private</span> MembersInjector&lt;MainActivity&gt; mainActivityMembersInjector;
    
      <span class="hljs-function"><span class="hljs-keyword">private</span> <span class="hljs-title">DaggerMainActivityComponent</span><span class="hljs-params">(Builder builder)</span> </span>{
        <span class="hljs-keyword">assert</span> builder != <span class="hljs-keyword">null</span>;
        initialize(builder);
      }
    
      <span class="hljs-function"><span class="hljs-keyword">public</span> <span class="hljs-keyword">static</span> Builder <span class="hljs-title">builder</span><span class="hljs-params">()</span> </span>{
        <span class="hljs-keyword">return</span> <span class="hljs-keyword">new</span> Builder();
      }
    
      <span class="hljs-function"><span class="hljs-keyword">public</span> <span class="hljs-keyword">static</span> MainActivityComponent <span class="hljs-title">create</span><span class="hljs-params">()</span> </span>{
        <span class="hljs-keyword">return</span> builder().build();
      }
    
      <span class="hljs-meta">@SuppressWarnings</span>(<span class="hljs-string">"unchecked"</span>)
      <span class="hljs-function"><span class="hljs-keyword">private</span> <span class="hljs-keyword">void</span> <span class="hljs-title">initialize</span><span class="hljs-params">(<span class="hljs-keyword">final</span> Builder builder)</span> </span>{
    
        <span class="hljs-keyword">this</span>.potProvider = Pot_Factory.create(Rose_Factory.create());
    
        <span class="hljs-keyword">this</span>.mainActivityMembersInjector = MainActivity_MembersInjector.create(potProvider);
      }
    
      <span class="hljs-meta">@Override</span>
      <span class="hljs-function"><span class="hljs-keyword">public</span> <span class="hljs-keyword">void</span> <span class="hljs-title">inject</span><span class="hljs-params">(MainActivity activity)</span> </span>{
        mainActivityMembersInjector.injectMembers(activity);
      }
    
      <span class="hljs-keyword">public</span> <span class="hljs-keyword">static</span> <span class="hljs-keyword">final</span> <span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">Builder</span> </span>{
        <span class="hljs-function"><span class="hljs-keyword">private</span> <span class="hljs-title">Builder</span><span class="hljs-params">()</span> </span>{}
    
        <span class="hljs-function"><span class="hljs-keyword">public</span> MainActivityComponent <span class="hljs-title">build</span><span class="hljs-params">()</span> </span>{
          <span class="hljs-keyword">return</span> <span class="hljs-keyword">new</span> DaggerMainActivityComponent(<span class="hljs-keyword">this</span>);
        }
      }
    }
    </code></pre>
    
   * 总结
    
       @Inject是JSR330定义的，而@Component是Dagger2框架自己定义的。
    
 * @Module和@Provides
 
    * 使用@Inject标记构造器提供依赖是有局限性的，比如注入的是第三方库提供的，我们无法在构造器上加上@Inject注解。
      或者，我们使用依赖倒置的时候，因为需要注入的对象是抽象的，@Inject也无法使用，因为抽象的类并不能实例化，比如：
      
      * <pre class="hljs java"><code class="java"><span class="hljs-keyword">public</span> <span class="hljs-keyword">abstract</span> <span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">Flower</span> </span>{
            <span class="hljs-function"><span class="hljs-keyword">public</span> <span class="hljs-keyword">abstract</span> String <span class="hljs-title">whisper</span><span class="hljs-params">()</span></span>;
        }
        </code></pre>
        
        <pre class="hljs java"><code class="java"><span class="hljs-keyword">public</span> <span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">Lily</span> <span class="hljs-keyword">extends</span> <span class="hljs-title">Flower</span> </span>{
        
            <span class="hljs-meta">@Inject</span>
            Lily() {}
        
            <span class="hljs-meta">@Override</span>
            <span class="hljs-function"><span class="hljs-keyword">public</span> String <span class="hljs-title">whisper</span><span class="hljs-params">()</span> </span>{
                <span class="hljs-keyword">return</span> <span class="hljs-string">"纯洁"</span>;
            }
        }
        </code></pre>
        
        <pre class="hljs java"><code class="java"><span class="hljs-keyword">public</span> <span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">Rose</span> <span class="hljs-keyword">extends</span> <span class="hljs-title">Flower</span> </span>{
        
            <span class="hljs-meta">@Inject</span>
            <span class="hljs-function"><span class="hljs-keyword">public</span> <span class="hljs-title">Rose</span><span class="hljs-params">()</span> </span>{}
        
            <span class="hljs-function"><span class="hljs-keyword">public</span> String <span class="hljs-title">whisper</span><span class="hljs-params">()</span>  </span>{
                <span class="hljs-keyword">return</span> <span class="hljs-string">"热恋"</span>;
            }
        }
        </code></pre>
        
        <pre class="hljs java"><code class="java"><span class="hljs-keyword">public</span> <span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">Pot</span> </span>{
        
            <span class="hljs-keyword">private</span> Flower flower;
        
            <span class="hljs-meta">@Inject</span>
            <span class="hljs-function"><span class="hljs-keyword">public</span> <span class="hljs-title">Pot</span><span class="hljs-params">(Flower flower)</span> </span>{
                <span class="hljs-keyword">this</span>.flower = flower;
            }
        
            <span class="hljs-function"><span class="hljs-keyword">public</span> String <span class="hljs-title">show</span><span class="hljs-params">()</span> </span>{
                <span class="hljs-keyword">return</span> flower.whisper();
            }
        }
        </code></pre>
        
    * 会报错 
        
        <div>
            <img src="https://upload-images.jianshu.io/upload_images/2202079-798acb053f54eb7d.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/700" />
        </div>
     
    * 用到Module解决这个问题
    
        * 清除Lily和Rose的@Inject
        
            <pre class="hljs java"><code class="java"><span class="hljs-keyword">public</span> <span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">Lily</span> <span class="hljs-keyword">extends</span> <span class="hljs-title">Flower</span> </span>{
            
                <span class="hljs-meta">@Override</span>
                <span class="hljs-function"><span class="hljs-keyword">public</span> String <span class="hljs-title">whisper</span><span class="hljs-params">()</span> </span>{
                    <span class="hljs-keyword">return</span> <span class="hljs-string">"纯洁"</span>;
                }
            }
            </code></pre>
            
        * <pre class="hljs java"><code class="java"><span class="hljs-keyword">public</span> <span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">Rose</span> <span class="hljs-keyword">extends</span> <span class="hljs-title">Flower</span> </span>{
          
              <span class="hljs-function"><span class="hljs-keyword">public</span> String <span class="hljs-title">whisper</span><span class="hljs-params">()</span>  </span>{
                  <span class="hljs-keyword">return</span> <span class="hljs-string">"热恋"</span>;
              }
          }
          </code></pre>
    
    * @Module标记在类上面，@Provodes标记在方法上，表示可以通过这个方法获取依赖。
    
        * <pre class="hljs java"><code class="java"><span class="hljs-meta">@Module</span>
          <span class="hljs-keyword">public</span> <span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">FlowerModule</span> </span>{
              <span class="hljs-meta">@Provides</span>
              <span class="hljs-function">Flower <span class="hljs-title">provideFlower</span><span class="hljs-params">()</span> </span>{
                  <span class="hljs-keyword">return</span> <span class="hljs-keyword">new</span> Rose();
              }
          }
          </code></pre>
          
        * 在@Component中指定Module 
            
            <pre class="hljs java"><code class="java"><span class="hljs-meta">@Component</span>(modules = FlowerModule.class)
            <span class="hljs-keyword">public</span> <span class="hljs-class"><span class="hljs-keyword">interface</span> <span class="hljs-title">MainActivityComponent</span> </span>{
                <span class="hljs-function"><span class="hljs-keyword">void</span> <span class="hljs-title">inject</span><span class="hljs-params">(MainActivity activity)</span></span>;
            }
            </code></pre>
         
        * 那么Module是干嘛的，我们来看看生成的类。
        
             <div>
                <img src="https://upload-images.jianshu.io/upload_images/2202079-60ef03623d0d85c6.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/401" />
             </div>
             
        * 可以看到，被@Module注解的类生成的也是Factory
        
            <pre class="hljs java"><code class="java"><span class="hljs-keyword">public</span> <span class="hljs-keyword">final</span> <span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">FlowerModule_FlowerFactory</span> <span class="hljs-keyword">implements</span> <span class="hljs-title">Factory</span>&lt;<span class="hljs-title">Flower</span>&gt; </span>{
              <span class="hljs-keyword">private</span> <span class="hljs-keyword">final</span> FlowerModule <span class="hljs-keyword">module</span>;
            
              <span class="hljs-function"><span class="hljs-keyword">public</span> <span class="hljs-title">FlowerModule_FlowerFactory</span><span class="hljs-params">(FlowerModule <span class="hljs-keyword">module</span>)</span> </span>{
                <span class="hljs-keyword">assert</span> <span class="hljs-keyword">module</span> != <span class="hljs-keyword">null</span>;
                <span class="hljs-keyword">this</span>.<span class="hljs-keyword">module</span> = <span class="hljs-keyword">module</span>;
              }
            
              <span class="hljs-meta">@Override</span>
              <span class="hljs-function"><span class="hljs-keyword">public</span> Flower <span class="hljs-title">get</span><span class="hljs-params">()</span> </span>{
                <span class="hljs-keyword">return</span> Preconditions.checkNotNull(
                    <span class="hljs-keyword">module</span>.provideFlower(), <span class="hljs-string">"Cannot return null from a non-@Nullable @Provides method"</span>);
              }
            
              <span class="hljs-function"><span class="hljs-keyword">public</span> <span class="hljs-keyword">static</span> Factory&lt;Flower&gt; <span class="hljs-title">create</span><span class="hljs-params">(FlowerModule <span class="hljs-keyword">module</span>)</span> </span>{
                <span class="hljs-keyword">return</span> <span class="hljs-keyword">new</span> FlowerModule_FlowerFactory(<span class="hljs-keyword">module</span>);
              }
            }
            </code></pre>
            
            > 注意：@Module需要和@Provide是需要一起使用的时候才具有作用的，并且@Component也需要指定了该Module的时候。
              @Module是告诉Component，可以从这里获取依赖对象。Component就会去找被@Provide标注的方法，相当于构造器的@Inject，可以提供依赖。
              还有一点要说的是，@Component可以指定多个@Module的，如果需要提供多个依赖的话。
              并且Component也可以依赖其它Component存在。
              
    * @Qualifier和@Named
        
        * @Qualifier是限定符，而@Named则是基于String的限定符。
        
        * 当我有两个相同的依赖（都继承某一个父类或者都是先某一个接口）可以提供给高层时，那么程序就不知道我们到底要提供哪一个依赖，因为它找到了两个。
          这时候我们就可以通过限定符为两个依赖分别打上标记，指定提供某个依赖。
         
        * 接着上一个Demo，例如：Module可以提供的依赖有两个。
        
            <pre class="hljs java"><code class="java"><span class="hljs-meta">@Module</span>
            <span class="hljs-keyword">public</span> <span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">FlowerModule</span> </span>{
            
                <span class="hljs-meta">@Provides</span>
                <span class="hljs-function">Flower <span class="hljs-title">provideRose</span><span class="hljs-params">()</span> </span>{
                    <span class="hljs-keyword">return</span> <span class="hljs-keyword">new</span> Rose();
                }
            
                <span class="hljs-meta">@Provides</span>
                <span class="hljs-function">Flower <span class="hljs-title">provideLily</span><span class="hljs-params">()</span> </span>{
                    <span class="hljs-keyword">return</span> <span class="hljs-keyword">new</span> Lily();
                }
            }
            </code></pre>
            
            <div>
                <img src="https://upload-images.jianshu.io/upload_images/2202079-1c4a2b616d4e8781.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/700" />
            </div>
            
      * 解决办法
        
        <pre class="hljs java"><code class="java"><span class="hljs-meta">@Module</span>
        <span class="hljs-keyword">public</span> <span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">FlowerModule</span> </span>{
        
            <span class="hljs-meta">@Provides</span>
            <span class="hljs-meta">@Named</span>(<span class="hljs-string">"Rose"</span>)
            <span class="hljs-function">Flower <span class="hljs-title">provideRose</span><span class="hljs-params">()</span> </span>{
                <span class="hljs-keyword">return</span> <span class="hljs-keyword">new</span> Rose();
            }
        
            <span class="hljs-meta">@Provides</span>
            <span class="hljs-meta">@Named</span>(<span class="hljs-string">"Lily"</span>)
            <span class="hljs-function">Flower <span class="hljs-title">provideLily</span><span class="hljs-params">()</span> </span>{
                <span class="hljs-keyword">return</span> <span class="hljs-keyword">new</span> Lily();
            }
        }
        </code></pre>
        
      * 我们是通过@Inject Pot的构造器注入Flower依赖的，在这里可以用到限定符。
      
        <pre class="hljs java"><code class="java"><span class="hljs-keyword">public</span> <span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">Pot</span> </span>{
        
            <span class="hljs-keyword">private</span> Flower flower;
        
            <span class="hljs-meta">@Inject</span>
            <span class="hljs-function"><span class="hljs-keyword">public</span> <span class="hljs-title">Pot</span><span class="hljs-params">(@Named(<span class="hljs-string">"Rose"</span>)</span> Flower flower) </span>{
                <span class="hljs-keyword">this</span>.flower = flower;
            }
        
            <span class="hljs-function"><span class="hljs-keyword">public</span> String <span class="hljs-title">show</span><span class="hljs-params">()</span> </span>{
                <span class="hljs-keyword">return</span> flower.whisper();
            }
        }
        </code></pre>
        
        > 注意：而@Qualifier的作用和@Named是完全一样的，不过更推荐使用@Qualifier，因为@Named需要手写字符串，容易出错。
          @Qualifier不是直接注解在属性上的，而是用来自定义注解的。
          
        <pre class="hljs java"><code class="java"><span class="hljs-meta">@Qualifier</span>
        <span class="hljs-meta">@Retention</span>(RetentionPolicy.RUNTIME)
        <span class="hljs-keyword">public</span> <span class="hljs-meta">@interface</span> RoseFlower {}
        </code></pre>
        
        <pre class="hljs java"><code class="java"><span class="hljs-meta">@Qualifier</span>
        <span class="hljs-meta">@Retention</span>(RetentionPolicy.RUNTIME)
        <span class="hljs-keyword">public</span> <span class="hljs-meta">@interface</span> LilyFlower {}
        </code></pre>
        
        <pre class="hljs java"><code class="java"><span class="hljs-meta">@Module</span>
        <span class="hljs-keyword">public</span> <span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">FlowerModule</span> </span>{
        
            <span class="hljs-meta">@Provides</span>
            <span class="hljs-meta">@RoseFlower</span>
            <span class="hljs-function">Flower <span class="hljs-title">provideRose</span><span class="hljs-params">()</span> </span>{
                <span class="hljs-keyword">return</span> <span class="hljs-keyword">new</span> Rose();
            }
        
            <span class="hljs-meta">@Provides</span>
            <span class="hljs-meta">@LilyFlower</span>
            <span class="hljs-function">Flower <span class="hljs-title">provideLily</span><span class="hljs-params">()</span> </span>{
                <span class="hljs-keyword">return</span> <span class="hljs-keyword">new</span> Lily();
            }
        }
        </code></pre>
        
        <pre class="hljs java"><code class="java"><span class="hljs-keyword">public</span> <span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">Pot</span> </span>{
        
            <span class="hljs-keyword">private</span> Flower flower;
        
            <span class="hljs-meta">@Inject</span>
            <span class="hljs-function"><span class="hljs-keyword">public</span> <span class="hljs-title">Pot</span><span class="hljs-params">(@RoseFlower Flower flower)</span> </span>{
                <span class="hljs-keyword">this</span>.flower = flower;
            }
        
            <span class="hljs-function"><span class="hljs-keyword">public</span> String <span class="hljs-title">show</span><span class="hljs-params">()</span> </span>{
                <span class="hljs-keyword">return</span> flower.whisper();
            }
        }
        </code></pre>
        
      * 我们也可以使用Module来管理Pot依赖，当然还是需要@Qualifier指定提供哪一个依赖
      
        <pre class="hljs java"><code class="java"><span class="hljs-meta">@Module</span>
        <span class="hljs-keyword">public</span> <span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">PotModule</span> </span>{
        
            <span class="hljs-meta">@Provides</span>
            <span class="hljs-function">Pot <span class="hljs-title">providePot</span><span class="hljs-params">(@RoseFlower Flower flower)</span> </span>{
                <span class="hljs-keyword">return</span> <span class="hljs-keyword">new</span> Pot(flower);
            }
        }
        </code></pre>
        
      * 然后MainAcitivtyComponent需要增加一个Module
      
        <pre class="hljs java"><code class="java"><span class="hljs-meta">@Component</span>(modules = {FlowerModule.class, PotModule.class})
        <span class="hljs-keyword">public</span> <span class="hljs-class"><span class="hljs-keyword">interface</span> <span class="hljs-title">MainActivityComponent</span> </span>{
            <span class="hljs-function"><span class="hljs-keyword">void</span> <span class="hljs-title">inject</span><span class="hljs-params">(MainActivity activity)</span></span>;
        }
        </code></pre>
        
    * @Component的dependence和@SubComponent
        
        [参考：SubComponent和Dependence区别](https://stackoverflow.com/questions/29587130/dagger-2-subcomponents-vs-component-dependencies)
        
        * 我们也用Component来管理FlowerModule和PotModule，并且使用dependence联系各个Component。
        
            <pre class="hljs java"><code class="java"><span class="hljs-keyword">public</span> <span class="hljs-keyword">abstract</span> <span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">Flower</span> </span>{
                <span class="hljs-function"><span class="hljs-keyword">public</span> <span class="hljs-keyword">abstract</span> String <span class="hljs-title">whisper</span><span class="hljs-params">()</span></span>;
            }
            </code></pre>
            
            <pre class="hljs java"><code class="java"><span class="hljs-keyword">public</span> <span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">Lily</span> <span class="hljs-keyword">extends</span> <span class="hljs-title">Flower</span> </span>{
            
                <span class="hljs-meta">@Override</span>
                <span class="hljs-function"><span class="hljs-keyword">public</span> String <span class="hljs-title">whisper</span><span class="hljs-params">()</span> </span>{
                    <span class="hljs-keyword">return</span> <span class="hljs-string">"纯洁"</span>;
                }
            }
            </code></pre>
            
            <pre class="hljs java"><code class="java"><span class="hljs-keyword">public</span> <span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">Rose</span> <span class="hljs-keyword">extends</span> <span class="hljs-title">Flower</span> </span>{
            
                <span class="hljs-function"><span class="hljs-keyword">public</span> String <span class="hljs-title">whisper</span><span class="hljs-params">()</span>  </span>{
                    <span class="hljs-keyword">return</span> <span class="hljs-string">"热恋"</span>;
                }
            }
            </code></pre>
            
            <pre class="hljs java"><code class="java"><span class="hljs-meta">@Module</span>
            <span class="hljs-keyword">public</span> <span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">FlowerModule</span> </span>{
            
                <span class="hljs-meta">@Provides</span>
                <span class="hljs-meta">@RoseFlower</span>
                <span class="hljs-function">Flower <span class="hljs-title">provideRose</span><span class="hljs-params">()</span> </span>{
                    <span class="hljs-keyword">return</span> <span class="hljs-keyword">new</span> Rose();
                }
            
                <span class="hljs-meta">@Provides</span>
                <span class="hljs-meta">@LilyFlower</span>
                <span class="hljs-function">Flower <span class="hljs-title">provideLily</span><span class="hljs-params">()</span> </span>{
                    <span class="hljs-keyword">return</span> <span class="hljs-keyword">new</span> Lily();
                }
            }
            </code></pre>
         
        * Component上也需要指定@Qualifier
        
            <pre class="hljs java"><code class="java"><span class="hljs-meta">@Component</span>(modules = FlowerModule.class)
            <span class="hljs-keyword">public</span> <span class="hljs-class"><span class="hljs-keyword">interface</span> <span class="hljs-title">FlowerComponent</span> </span>{
                <span class="hljs-meta">@RoseFlower</span>
                <span class="hljs-function">Flower <span class="hljs-title">getRoseFlower</span><span class="hljs-params">()</span></span>;
            
                <span class="hljs-meta">@LilyFlower</span>
                <span class="hljs-function">Flower <span class="hljs-title">getLilyFlower</span><span class="hljs-params">()</span></span>;
            }
            </code></pre>
            
            <pre class="hljs cpp"><code class="cpp"><span class="hljs-keyword">public</span> <span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">Pot</span> {</span>
            
                <span class="hljs-keyword">private</span> Flower flower;
            
                <span class="hljs-function"><span class="hljs-keyword">public</span> <span class="hljs-title">Pot</span><span class="hljs-params">(Flower flower)</span> </span>{
                    <span class="hljs-keyword">this</span>.flower = flower;
                }
            
                <span class="hljs-function"><span class="hljs-keyword">public</span> String <span class="hljs-title">show</span><span class="hljs-params">()</span> </span>{
                    <span class="hljs-keyword">return</span> flower.whisper();
                }
            }
            </code></pre>
            
        * PotModule需要依赖Flower，需要指定其中一个子类实现，这里使用RoseFlower
        
            <pre class="hljs java"><code class="java"><span class="hljs-meta">@Module</span>
            <span class="hljs-keyword">public</span> <span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">PotModule</span> </span>{
            
                <span class="hljs-meta">@Provides</span>
                <span class="hljs-function">Pot <span class="hljs-title">providePot</span><span class="hljs-params">(@RoseFlower Flower flower)</span> </span>{
                    <span class="hljs-keyword">return</span> <span class="hljs-keyword">new</span> Pot(flower);
                }
            }
            </code></pre>
            
            <pre class="hljs java"><code class="java"><span class="hljs-meta">@Component</span>(modules = PotModule.class,dependencies = FlowerComponent.class)
            <span class="hljs-keyword">public</span> <span class="hljs-class"><span class="hljs-keyword">interface</span> <span class="hljs-title">PotComponent</span> </span>{
                <span class="hljs-function">Pot <span class="hljs-title">getPot</span><span class="hljs-params">()</span></span>;
            }
            </code></pre>
            
            <pre class="hljs java"><code class="java"><span class="hljs-meta">@Component</span>(dependencies = PotComponent.class)
            <span class="hljs-keyword">public</span> <span class="hljs-class"><span class="hljs-keyword">interface</span> <span class="hljs-title">MainActivityComponent</span> </span>{
                <span class="hljs-function"><span class="hljs-keyword">void</span> <span class="hljs-title">inject</span><span class="hljs-params">(MainActivity activity)</span></span>;
            }
            </code></pre>
            
        * 而在MainActivity则需要创建其依赖的Component
        
            <pre class="hljs java"><code class="java"><span class="hljs-keyword">public</span> <span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">MainActivity</span> <span class="hljs-keyword">extends</span> <span class="hljs-title">AppCompatActivity</span> </span>{
            
                <span class="hljs-meta">@Inject</span>
                Pot pot;
            
                <span class="hljs-function"><span class="hljs-keyword">protected</span> <span class="hljs-keyword">void</span> <span class="hljs-title">onCreate</span><span class="hljs-params">(@Nullable Bundle savedInstanceState)</span> </span>{
                    <span class="hljs-keyword">super</span>.onCreate(savedInstanceState);
            
                    DaggerMainActivityComponent.builder()
                            .potComponent(DaggerPotComponent.builder()
                                    .flowerComponent(DaggerFlowerComponent.create())
                                    .build())
                            .build().inject(<span class="hljs-keyword">this</span>);
            
                    String show = pot.show();
                    Toast.makeText(MainActivity.<span class="hljs-keyword">this</span>, show, Toast.LENGTH_SHORT).show();
                }
            }
            </code></pre>
            
        * 这就是Component的dependencies的用法了，我们Component不需要重复的指定Module，可以直接依赖其它Component获得。
        
        * 分析下源码
            
            <pre class="hljs java"><code class="java"><span class="hljs-keyword">public</span> <span class="hljs-keyword">final</span> <span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">DaggerPotComponent</span> <span class="hljs-keyword">implements</span> <span class="hljs-title">PotComponent</span> </span>{
              <span class="hljs-keyword">private</span> Provider&lt;Flower&gt; getRoseFlowerProvider;
            
              <span class="hljs-keyword">private</span> Provider&lt;Pot&gt; providePotProvider;
            
              <span class="hljs-function"><span class="hljs-keyword">private</span> <span class="hljs-title">DaggerPotComponent</span><span class="hljs-params">(Builder builder)</span> </span>{
                <span class="hljs-keyword">assert</span> builder != <span class="hljs-keyword">null</span>;
                initialize(builder);
              }
            
              <span class="hljs-function"><span class="hljs-keyword">public</span> <span class="hljs-keyword">static</span> Builder <span class="hljs-title">builder</span><span class="hljs-params">()</span> </span>{
                <span class="hljs-keyword">return</span> <span class="hljs-keyword">new</span> Builder();
              }
            
              <span class="hljs-meta">@SuppressWarnings</span>(<span class="hljs-string">"unchecked"</span>)
              <span class="hljs-function"><span class="hljs-keyword">private</span> <span class="hljs-keyword">void</span> <span class="hljs-title">initialize</span><span class="hljs-params">(<span class="hljs-keyword">final</span> Builder builder)</span> </span>{
            
                <span class="hljs-keyword">this</span>.getRoseFlowerProvider =
                    <span class="hljs-keyword">new</span> Factory&lt;Flower&gt;() {
                      <span class="hljs-keyword">private</span> <span class="hljs-keyword">final</span> FlowerComponent flowerComponent = builder.flowerComponent;
            
                      <span class="hljs-meta">@Override</span>
                      <span class="hljs-function"><span class="hljs-keyword">public</span> Flower <span class="hljs-title">get</span><span class="hljs-params">()</span> </span>{
                        <span class="hljs-keyword">return</span> Preconditions.checkNotNull(
                            flowerComponent.getRoseFlower(),
                            <span class="hljs-string">"Cannot return null from a non-@Nullable component method"</span>);
                      }
                    };
            
                <span class="hljs-keyword">this</span>.providePotProvider =
                    PotModule_ProvidePotFactory.create(builder.potModule, getRoseFlowerProvider);
              }
            
              <span class="hljs-meta">@Override</span>
              <span class="hljs-function"><span class="hljs-keyword">public</span> Pot <span class="hljs-title">getPot</span><span class="hljs-params">()</span> </span>{
                <span class="hljs-keyword">return</span> providePotProvider.get();
              }
            
              <span class="hljs-keyword">public</span> <span class="hljs-keyword">static</span> <span class="hljs-keyword">final</span> <span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">Builder</span> </span>{
                <span class="hljs-keyword">private</span> PotModule potModule;
            
                <span class="hljs-keyword">private</span> FlowerComponent flowerComponent;
            
                <span class="hljs-function"><span class="hljs-keyword">private</span> <span class="hljs-title">Builder</span><span class="hljs-params">()</span> </span>{}
            
                <span class="hljs-function"><span class="hljs-keyword">public</span> PotComponent <span class="hljs-title">build</span><span class="hljs-params">()</span> </span>{
                  <span class="hljs-keyword">if</span> (potModule == <span class="hljs-keyword">null</span>) {
                    <span class="hljs-keyword">this</span>.potModule = <span class="hljs-keyword">new</span> PotModule();
                  }
                  <span class="hljs-keyword">if</span> (flowerComponent == <span class="hljs-keyword">null</span>) {
                    <span class="hljs-keyword">throw</span> <span class="hljs-keyword">new</span> IllegalStateException(FlowerComponent.class.getCanonicalName() + <span class="hljs-string">" must be set"</span>);
                  }
                  <span class="hljs-keyword">return</span> <span class="hljs-keyword">new</span> DaggerPotComponent(<span class="hljs-keyword">this</span>);
                }
            
                <span class="hljs-function"><span class="hljs-keyword">public</span> Builder <span class="hljs-title">potModule</span><span class="hljs-params">(PotModule potModule)</span> </span>{
                  <span class="hljs-keyword">this</span>.potModule = Preconditions.checkNotNull(potModule);
                  <span class="hljs-keyword">return</span> <span class="hljs-keyword">this</span>;
                }
            
                <span class="hljs-function"><span class="hljs-keyword">public</span> Builder <span class="hljs-title">flowerComponent</span><span class="hljs-params">(FlowerComponent flowerComponent)</span> </span>{
                  <span class="hljs-keyword">this</span>.flowerComponent = Preconditions.checkNotNull(flowerComponent);
                  <span class="hljs-keyword">return</span> <span class="hljs-keyword">this</span>;
                }
              }
            }
            </code></pre>
            
       
        
## dagger为什么这么用?


整体参考( 总结 )： [Dagger2 最清晰的使用教程](https://www.jianshu.com/p/24af4c102f62)