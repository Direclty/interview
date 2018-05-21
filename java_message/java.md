# Study The Java 

## 基础
    
## 数据结构

   * 数组 、 链表 、散列表(哈希表)   [参考： Android技能树 — 数组,链表,散列表基础小结](https://www.jianshu.com/p/be513b7507f1)
   
        * 线性表
        <br/>
        <br/>
        <div>
            <img src="https://upload-images.jianshu.io/upload_images/1529568-9230d5093d88407f.png?imageMogr2/auto-orient/" />
        </div> 
         <br/>
         
        >  线性表：零个或多个数据元素的有限序列。
        
        * 储物柜
           <br/>
           <br/>
           <div>
                <img src="https://upload-images.jianshu.io/upload_images/1529568-429afaecccb810da.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/514" />
           </div>
        
       
   >   我们在将数据存储到内存时候，你请求计算机提供存储空间，计算机会给你一个存储地址，然后你把内容存进去。就类似上面的储物柜。
   
   * 线性表顺序存储（数组）：
   
       * 线性表的顺序存储结构：用一段地址连续的存储单元依次存储线性表的数据元素。
       
       * 线性表特点 
       
            * 如果我们有四袋物品，我们已经知道了第一袋物品在N号码的抽屉，那么其他三个肯定在N+1，N+2，N+3号，所以在查询的时候十分方便，因为我们只需要知道一个的位置，其他的位置都知道了。（所以查询起来很方便，因为所有的位置都知道具体在哪个）
            
            * 如果我们把A放在01，B放在02，C放在03，这时候我们说在A和B之间插入一个D，这时候我们需要把B和C都往后移动。同理删除一个也是一样，比如我们删除了A，B和C都要往前移动。（所以插入删除比较麻烦，需要移动所有后面位置的数据）
            
            * 如果你突然多了一个需要存储的物品，而且已经不够放了，那么需要全部重新移动到新的连续的存储地方。
                <br/>
                <table>
                    <thead>
                        <tr>
                            <th>数组</th>
                            <th>时间复杂度</th>
                        </tr>
                    </thead>
                    <tbody>
                        <tr>
                            <td>读取</td>
                            <td>O(1)</td>
                        </tr>
                        <tr>
                            <td>插入/删除</td>
                            <td>O(n)</td>
                        </tr>
                    </tbody>
                </table>
   
   * 线性表链式存储（链表）：
        
       * 单链表
       
            * 它们的步骤就是先知道到了一个地点，然后到了第一个目的地A，到了A之后根据线索才知道下一个目的地B在哪里，然后再去B，然后这样下去A-- B-- C --.....这样，一直到最终的藏宝地方。没错，我们的链表就是类似这种，比如我们知道一共有四袋物品，但是你不能直接知道最后一个物品在哪里，你只能从第一个开始，一个个找下去。
            
                <div>
                    <img src="https://upload-images.jianshu.io/upload_images/1529568-0e0cb5c38d58d89b.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/367" />
                </div>
                
            * 比如我们第一个存在了01号抽屉，存储内容为A,同时告诉大家，下一个物品在05号抽屉，里面内容为B，同时再下一个在08号。
                
                <div>
                    <img src="https://upload-images.jianshu.io/upload_images/1529568-aed6f27f7cd4376e.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/700" />
                </div>
               
                <br/>
                       
                > 由上面的图我们可以知道，结点由存放数据元素的数据域和存放后继节点地址的指针域组成。
       
            * 特点：
            
                * 由上面我们举例的古墓丽影的剧情可知，我们不能直接知道最后一个线索在哪里，只能一个个从头到尾查过去，所以链表的读取会很慢；但是我们如果想要插入和删除就很方便。
                  比如我们要插入一个新的结点：    
                  
                  <div>
                     <img src="https://upload-images.jianshu.io/upload_images/1529568-5b9ab0b67900b2dd.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/700" />
                  </div>
                
                * 比如我们要删除其中一个结点：
                    
                    <div>
                        <img src="https://upload-images.jianshu.io/upload_images/1529568-bd9954cbd5471b7f.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/700" />
                    </div>
                    <br/>
                    <table>
                        <thead>
                            <tr>
                                <th>链表</th>
                                <th>时间复杂度</th>
                            </tr>
                        </thead>
                        <tbody>
                            <tr>
                                <td>读取</td>
                                <td>O(n)</td>
                            </tr>
                            <tr>
                                <td>插入/删除</td>
                                <td>O(1)</td>
                            </tr>
                        </tbody>
                    </table>
                    
     * 循环链表：
     
        <div>
            <img src="https://upload-images.jianshu.io/upload_images/1529568-b9414482a59788d3.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/700" />
        </div>
        
        <br/>
                
        > 将单链表中终端结点的指针端改为指向头结点，就使整个单链表形成一个环，这种头尾相接的单链表称为单循环链表，简称循环链表。
       
     * 双向链表：
     
        <div>
            <img src="https://upload-images.jianshu.io/upload_images/1529568-886a819f221c6efd.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/700" />
        </div>
        
        <br/>
        
        > 双向链表是在单链表的每个结点中，再设置一个指向其前驱结点的指针域。
   
     * 静态链表：
     
        * 静态链表是为了让没有指针的高级语言也能够用数组实现链表功能。
        
            <div>
                <img src="https://upload-images.jianshu.io/upload_images/1529568-4ed27bcd41d0dc1f.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/544" />
            </div>
            
            <br/>
                    
            >  静态链表是用类似于数组方法实现的，是顺序的存储结构，在物理地址上是连续的，而且需要预先分配地址空间大小。所以静态链表的初始长度一般是固定的。然后在这个里面存的时候不仅存储数据域，同时存入了下一个数组index的位置。相当于我们上面的指针域换成了数组的index值。
            
   * 散列表（哈希表）：
   
        * 由上面我们已经可以知道数组和链表各自的优势和缺点了
            <br/>
            
            <table>
            <thead>
            <tr>
            <th>操作</th>
            <th>数组</th>
            <th>链表</th>
            </tr>
            </thead>
            <tbody>
            <tr>
            <td>读取</td>
            <td>擅长（可以随机/顺序访问）</td>
            <td>不擅长（只能顺序访问）</td>
            </tr>
            <tr>
            <td>插入/删除</td>
            <td>不擅长</td>
            <td>擅长</td>
            </tr>
            </tbody>
            </table>
        
        * 什么是散列表
            
          >  如果你有一天开了一家水果店，你会拿一个本子来记各种水果的价格，因为大家知道数组对于读取来说很方便，所以我们用一个数组来记录各种水果的价格，并且是按照开头字母来进行顺序写入的。
        
            <div>
                <img src="https://upload-images.jianshu.io/upload_images/1529568-0bffdd2c83691d35.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/492" />
            </div>
            
            <br/>
            
          >  这时候，如果有人问Apple，你就查询一下价格，但是如果水果很多，甚至很多都是A开头的水果，比如有20个A开头的水果，这时候你只能知道A开头的水果是前面20个，但是具体是哪个，你又要一个个的查过来，如果我们马上就知道Apple对应的数组index值就好了，这样就马上知道在数组的哪个位置，然后马上就可以读取出来了。
          
          <div>
            <img src="https://upload-images.jianshu.io/upload_images/1529568-369c61f2539fd167.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/700" />
          </div>
          
          <div>
            <img src="https://upload-images.jianshu.io/upload_images/1529568-86943efa8b2bfc65.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/700" />
          </div>
          <br/>
          
          > 这样我们就在index为2的地方存储了苹果的价格，然后在index为8的地方存储了香蕉的价格，依次类推，所有水果都记录进去，这样顾客问你苹果价格时候，你就马上知道在index为2的地方去读取。
            
          * 而把Apple变为2是通过散列函数来实现的。
          
          * 散列函数：
          
            * 我们要实现上面的需求，这个散列函数需要一些基本要求：
              
               * 1)、 如果输入的内容相同时，每次得到的值都相同，比如你每次输入都是Apple，比如每次得到的结果都是2，不能一下子2，一下子5。
              
               * 2)、 如果不管输入什么值得到的结果都相同，那么这个函数也没用，你输入Apple和输入Banana得到的值都相同，那么没有任何分辨作用。
              
               * 3)、 散列函数需要返回有效的索引，比如上面我们的数组的长度只有40，你输入Pair时候输出100，这样是无效索引。
              
               * 4)、 根据上面的情况我们知道了，我们输入不同的值的时候，通过散列函数换算后，最好的结果是每个值都是不同，这样的话他们的index 也不同。
              
                    <div>
                        <img src="https://upload-images.jianshu.io/upload_images/1529568-6e9d746b01aaf15e.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/700" />
                    </div>
                    <br/>
                    
                   >  但是如果我们的数组只有长度为6，但是我们有7种水果，那么一定会有二个水果得到的index是相同的。这时候我们称这种情况为冲突。
                   
                   * 解决办法
                       
                       * 处理冲突的方式有很多，最简单的办法就是：如果二个键映射到了同一个位置，就在这个位置存储一个链表。
                       
                       <br/>
                       <div>    
                            <img src="https://upload-images.jianshu.io/upload_images/1529568-59633447a55560b1.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/700" />
                       </div>
                       <br/>
                       
                       > 这样，我们在查询其他水果时候还是很快，只是在查询index为0的水果时候稍微慢一点，因为要在index为0的链表中找到相应的水果。
                       
                       <br/>
                       <table>
                       <thead>
                       <tr>
                       <th>散列表操作</th>
                       <th>平均情况</th>
                       <th>最糟情况</th>
                       </tr>
                       </thead>
                       <tbody>
                       <tr>
                       <td>查找</td>
                       <td>O(1)</td>
                       <td>O(n)</td>
                       </tr>
                       <tr>
                       <td>插入</td>
                       <td>O(1)</td>
                       <td>O(n)</td>
                       </tr>
                       <tr>
                       <td>删除</td>
                       <td>O(1)</td>
                       <td>O(n)</td>
                       </tr>
                       </tbody>
                       </table>
            * 总结：
              
                 >  散列表的查找（获取给定索引处的值）速度与数组一样快，而插入和删除速度与链表一样快。但是最糟情况下，散列表的各种操作速度都很慢（比如都集中在index为0的链表下面，则查询就跟链表查询一样了。）
                 
            * 所以针对最糟的情况，我们需要：
         
                 * 1、较低的填装因子：
                         <br/>
                          散列表使用数组来存储数据，因此需要计算数组中被占用的位置数。
                         （比如，数组的长度为10，我们填入的数占用了其中三个，则填装因子为0.3;如果填入的数正好把长度占满，则填装因子为1；如果填入了20个，则填装因子为2。）
                         当填装因子太大了，说明数组长度不够了，我们就要再散列表中添加位置了。称为调整长度。（一旦填装因子大于0.7就调整散列表的长度，为此你首先创建一个更长的新数组，通常将数组增长一倍）
                         
                 * 2、良好的散列函数：<br/>
                      良好的散列好书让数组中的值呈均匀分布，糟糕的散列函数让值扎堆，导致大量的冲突。
            
   * list   
     
     * ArrayList  &  参考：[ArrayList源码解析（JDK8）](https://www.jianshu.com/p/192148ddab9f) 
        
        * 构造方法->常用API(增、删、改、查)的顺序，设计的变量的意义。了解ArrayList的特点、使用场景
        
        * ArrayList 是一个动态数组，实现了List<E>, RandomAccess（随机访问的能力）, Cloneable, java.io.Serializable接口，其中RandomAccess代表了其拥有随机快速访问的能力，ArrayList可以以O(1)的时间复杂度去根据下标访问元素。
         
        > 难点：扩容次数越多，效率就越底，如果需要扩容，手动调用public void ensureCapacity(int minCapacity{})扩容。这个方法是ArrayList的方法，使用时要强转
        
        * 步骤 
            
            * 构造方法
                
                <pre class="hljs java"><code class="java">    <span class="hljs-comment">//默认构造函数里的空数组</span>
                    <span class="hljs-keyword">private</span> <span class="hljs-keyword">static</span> <span class="hljs-keyword">final</span> Object[] DEFAULTCAPACITY_EMPTY_ELEMENTDATA = {};
                    
                    <span class="hljs-comment">//存储集合元素的底层实现：真正存放元素的数组</span>
                    <span class="hljs-keyword">transient</span> Object[] elementData; <span class="hljs-comment">// non-private to simplify nested class access</span>
                    <span class="hljs-comment">//当前元素数量</span>
                    <span class="hljs-keyword">private</span> <span class="hljs-keyword">int</span> size;
                    
                    <span class="hljs-comment">//默认构造方法</span>
                    <span class="hljs-function"><span class="hljs-keyword">public</span> <span class="hljs-title">ArrayList</span><span class="hljs-params">()</span> </span>{
                        <span class="hljs-comment">//默认构造方法只是简单的将 空数组赋值给了elementData</span>
                        <span class="hljs-keyword">this</span>.elementData = DEFAULTCAPACITY_EMPTY_ELEMENTDATA;
                    }
                    
                    <span class="hljs-comment">//空数组</span>
                    <span class="hljs-keyword">private</span> <span class="hljs-keyword">static</span> <span class="hljs-keyword">final</span> Object[] EMPTY_ELEMENTDATA = {};
                    <span class="hljs-comment">//带初始容量的构造方法</span>
                    <span class="hljs-function"><span class="hljs-keyword">public</span> <span class="hljs-title">ArrayList</span><span class="hljs-params">(<span class="hljs-keyword">int</span> initialCapacity)</span> </span>{
                        <span class="hljs-comment">//如果初始容量大于0，则新建一个长度为initialCapacity的Object数组.</span>
                        <span class="hljs-comment">//注意这里并没有修改size(对比第三个构造函数)</span>
                        <span class="hljs-keyword">if</span> (initialCapacity &gt; <span class="hljs-number">0</span>) {
                            <span class="hljs-keyword">this</span>.elementData = <span class="hljs-keyword">new</span> Object[initialCapacity];
                        } <span class="hljs-keyword">else</span> <span class="hljs-keyword">if</span> (initialCapacity == <span class="hljs-number">0</span>) {<span class="hljs-comment">//如果容量为0，直接将EMPTY_ELEMENTDATA赋值给elementData</span>
                            <span class="hljs-keyword">this</span>.elementData = EMPTY_ELEMENTDATA;
                        } <span class="hljs-keyword">else</span> {<span class="hljs-comment">//容量小于0，直接抛出异常</span>
                            <span class="hljs-keyword">throw</span> <span class="hljs-keyword">new</span> IllegalArgumentException(<span class="hljs-string">"Illegal Capacity: "</span>+
                                                               initialCapacity);
                        }
                    }
                
                    <span class="hljs-comment">//利用别的集合类来构建ArrayList的构造函数</span>
                    <span class="hljs-function"><span class="hljs-keyword">public</span> <span class="hljs-title">ArrayList</span><span class="hljs-params">(Collection&lt;? extends E&gt; c)</span> </span>{
                        <span class="hljs-comment">//直接利用Collection.toArray()方法得到一个对象数组，并赋值给elementData </span>
                        elementData = c.toArray();
                        <span class="hljs-comment">//因为size代表的是集合元素数量，所以通过别的集合来构造ArrayList时，要给size赋值</span>
                        <span class="hljs-keyword">if</span> ((size = elementData.length) != <span class="hljs-number">0</span>) {
                            <span class="hljs-comment">// c.toArray might (incorrectly) not return Object[] (see 6260652)</span>
                            <span class="hljs-keyword">if</span> (elementData.getClass() != Object[].class)<span class="hljs-comment">//这里是当c.toArray出错，没有返回Object[]时，利用Arrays.copyOf 来复制集合c中的元素到elementData数组中</span>
                                elementData = Arrays.copyOf(elementData, size, Object[].class);
                        } <span class="hljs-keyword">else</span> {
                            <span class="hljs-comment">//如果集合c元素数量为0，则将空数组EMPTY_ELEMENTDATA赋值给elementData </span>
                            <span class="hljs-comment">// replace with empty array.</span>
                            <span class="hljs-keyword">this</span>.elementData = EMPTY_ELEMENTDATA;
                        }
                    }
                </code></pre>
                ####总结：构建elementData和size
                
                > 注意：Collection.toArray()，这个方法是其他Collection子类各大集合当中高频使用的方法，获取某个Collection的所有元素；
                  Arrays.copyOf(elementData, size, Object[].class)，根据class的类型来决定是用new还是反射来构建泛型数组，同时利用native函数
                  批量赋值函数到新数组
                  
                <pre class="hljs javascript"><code class="javascript">    public <span class="hljs-keyword">static</span> &lt;T,U&gt; T[] copyOf(U[] original, int newLength, Class&lt;? extends T[]&gt; newType) {
                        @SuppressWarnings(<span class="hljs-string">"unchecked"</span>)
                        <span class="hljs-comment">//根据class的类型来决定是new 还是反射去构造一个泛型数组</span>
                        T[] copy = ((<span class="hljs-built_in">Object</span>)newType == (<span class="hljs-built_in">Object</span>)<span class="hljs-built_in">Object</span>[].class)
                            ? (T[]) <span class="hljs-keyword">new</span> <span class="hljs-built_in">Object</span>[newLength]
                            : (T[]) <span class="hljs-built_in">Array</span>.newInstance(newType.getComponentType(), newLength);
                        <span class="hljs-comment">//利用native函数，批量赋值元素至新数组中。</span>
                        System.arraycopy(original, <span class="hljs-number">0</span>, copy, <span class="hljs-number">0</span>,
                                         <span class="hljs-built_in">Math</span>.min(original.length, newLength));
                        <span class="hljs-keyword">return</span> copy;
                    }
                </code></pre>
                
                > 注意：System.arraycopy(original, 0, copy, 0,Math.min(original.length, newLength))，也是高频使用的方法
                
            * 常用API 
                
                * 增
                
                    * 每次 add之前，都会判断add后的容量，是否需要扩容。
                    <br/>
                    <br/>
                    <pre class="hljs java"><code class="java"><span class="hljs-function"><span class="hljs-keyword">public</span> <span class="hljs-keyword">boolean</span> <span class="hljs-title">add</span><span class="hljs-params">(E e)</span> </span>{
                        ensureCapacityInternal(size + <span class="hljs-number">1</span>);  <span class="hljs-comment">// Increments modCount!!</span>
                        elementData[size++] = e;<span class="hljs-comment">//在数组末尾追加一个元素，并修改size</span>
                        <span class="hljs-keyword">return</span> <span class="hljs-keyword">true</span>;
                    }
                        <span class="hljs-keyword">private</span> <span class="hljs-keyword">static</span> <span class="hljs-keyword">final</span> <span class="hljs-keyword">int</span> DEFAULT_CAPACITY = <span class="hljs-number">10</span>;<span class="hljs-comment">//默认扩容容量 10</span>
                        <span class="hljs-function"><span class="hljs-keyword">private</span> <span class="hljs-keyword">void</span> <span class="hljs-title">ensureCapacityInternal</span><span class="hljs-params">(<span class="hljs-keyword">int</span> minCapacity)</span> </span>{
                            <span class="hljs-comment">//利用 == 可以判断数组是否是用默认构造函数初始化的</span>
                            <span class="hljs-keyword">if</span> (elementData == DEFAULTCAPACITY_EMPTY_ELEMENTDATA) {
                                minCapacity = Math.max(DEFAULT_CAPACITY, minCapacity);
                            }
                    
                            ensureExplicitCapacity(minCapacity);
                        }
                    
                    
                    <span class="hljs-function"><span class="hljs-keyword">private</span> <span class="hljs-keyword">void</span> <span class="hljs-title">ensureExplicitCapacity</span><span class="hljs-params">(<span class="hljs-keyword">int</span> minCapacity)</span> </span>{
                        modCount++;<span class="hljs-comment">//如果确定要扩容，会修改modCount </span>
                    
                        <span class="hljs-comment">// overflow-conscious code</span>
                        <span class="hljs-keyword">if</span> (minCapacity - elementData.length &gt; <span class="hljs-number">0</span>)
                            grow(minCapacity);
                    }
                    
                    <span class="hljs-comment">//需要扩容的话，默认扩容一半</span>
                    <span class="hljs-function"><span class="hljs-keyword">private</span> <span class="hljs-keyword">void</span> <span class="hljs-title">grow</span><span class="hljs-params">(<span class="hljs-keyword">int</span> minCapacity)</span> </span>{
                        <span class="hljs-comment">// overflow-conscious code</span>
                        <span class="hljs-keyword">int</span> oldCapacity = elementData.length;
                        <span class="hljs-keyword">int</span> newCapacity = oldCapacity + (oldCapacity &gt;&gt; <span class="hljs-number">1</span>);<span class="hljs-comment">//默认扩容一半</span>
                        <span class="hljs-keyword">if</span> (newCapacity - minCapacity &lt; <span class="hljs-number">0</span>)<span class="hljs-comment">//如果还不够 ，那么就用 能容纳的最小的数量。（add后的容量）</span>
                            newCapacity = minCapacity;
                        <span class="hljs-keyword">if</span> (newCapacity - MAX_ARRAY_SIZE &gt; <span class="hljs-number">0</span>)
                            newCapacity = hugeCapacity(minCapacity);
                        <span class="hljs-comment">// minCapacity is usually close to size, so this is a win:</span>
                        elementData = Arrays.copyOf(elementData, newCapacity);<span class="hljs-comment">//拷贝，扩容，构建一个新数组，</span>
                    }
                    </code></pre>
                    
                    <pre class="hljs cpp"><code class="cpp">
                    <span class="hljs-function"><span class="hljs-keyword">public</span> <span class="hljs-keyword">void</span> <span class="hljs-title">add</span><span class="hljs-params">(<span class="hljs-keyword">int</span> index, E element)</span> </span>{
                        rangeCheckForAdd(index);<span class="hljs-comment">//越界判断 如果越界抛异常</span>
                    
                        ensureCapacityInternal(size + <span class="hljs-number">1</span>);  <span class="hljs-comment">// Increments modCount!!</span>
                        System.arraycopy(elementData, index, elementData, index + <span class="hljs-number">1</span>,
                                         size - index); <span class="hljs-comment">//将index开始的数据 向后移动一位</span>
                        elementData[index] = element;
                        size++;
                    }
                    </code></pre>
                    
                    <pre class="hljs java"><code class="java"><span class="hljs-function"><span class="hljs-keyword">public</span> <span class="hljs-keyword">boolean</span> <span class="hljs-title">addAll</span><span class="hljs-params">(Collection&lt;? extends E&gt; c)</span> </span>{
                        Object[] a = c.toArray();
                        <span class="hljs-keyword">int</span> numNew = a.length;
                        ensureCapacityInternal(size + numNew);  <span class="hljs-comment">// Increments modCount //确认是否需要扩容</span>
                        System.arraycopy(a, <span class="hljs-number">0</span>, elementData, size, numNew);<span class="hljs-comment">// 复制数组完成复制</span>
                        size += numNew;
                        <span class="hljs-keyword">return</span> numNew != <span class="hljs-number">0</span>;
                    }
                    </code></pre>
                    
                    <pre class="hljs java"><code class="java"><span class="hljs-function"><span class="hljs-keyword">public</span> <span class="hljs-keyword">boolean</span> <span class="hljs-title">addAll</span><span class="hljs-params">(<span class="hljs-keyword">int</span> index, Collection&lt;? extends E&gt; c)</span> </span>{
                        rangeCheckForAdd(index);<span class="hljs-comment">//越界判断</span>
                    
                        Object[] a = c.toArray();
                        <span class="hljs-keyword">int</span> numNew = a.length;
                        ensureCapacityInternal(size + numNew);  <span class="hljs-comment">// Increments modCount //确认是否需要扩容</span>
                    
                        <span class="hljs-keyword">int</span> numMoved = size - index;
                        <span class="hljs-keyword">if</span> (numMoved &gt; <span class="hljs-number">0</span>)
                            System.arraycopy(elementData, index, elementData, index + numNew,
                                             numMoved);<span class="hljs-comment">//移动（复制)数组</span>
                    
                        System.arraycopy(a, <span class="hljs-number">0</span>, elementData, index, numNew);<span class="hljs-comment">//复制数组完成批量赋值</span>
                        size += numNew;
                        <span class="hljs-keyword">return</span> numNew != <span class="hljs-number">0</span>;
                    }
                    </code></pre>
                    
                    #### 总结：
                     add、addAll。<br/>
                     先判断是否越界，是否需要扩容。<br/>
                     如果扩容， 就复制数组。<br/>
                     然后设置对应下标元素值。<br/>
                      
                     值得注意的是：<br/>
                     1 如果需要扩容的话，默认扩容一半。如果扩容一半不够，就用目标的size作为扩容后的容量。<br/>
                     2 在扩容成功后，会修改modCount
                     
                * 删 
                    
                    * 从这里我们也可以看出，当用来作为删除元素的集合里的元素多余被删除集合时，也没事，只会删除它们共同拥有的元素。
                    
                       <pre class="hljs java"><code class="java"><span class="hljs-function"><span class="hljs-keyword">public</span> E <span class="hljs-title">remove</span><span class="hljs-params">(<span class="hljs-keyword">int</span> index)</span> </span>{
                           rangeCheck(index);<span class="hljs-comment">//判断是否越界</span>
                           modCount++;<span class="hljs-comment">//修改modeCount 因为结构改变了</span>
                           E oldValue = elementData(index);<span class="hljs-comment">//读出要删除的值</span>
                           <span class="hljs-keyword">int</span> numMoved = size - index - <span class="hljs-number">1</span>;
                           <span class="hljs-keyword">if</span> (numMoved &gt; <span class="hljs-number">0</span>)
                               System.arraycopy(elementData, index+<span class="hljs-number">1</span>, elementData, index,
                                                numMoved);<span class="hljs-comment">//用复制 覆盖数组数据</span>
                           elementData[--size] = <span class="hljs-keyword">null</span>; <span class="hljs-comment">// clear to let GC do its work  //置空原尾部数据 不再强引用， 可以GC掉</span>
                           <span class="hljs-keyword">return</span> oldValue;
                       }
                           <span class="hljs-comment">//根据下标从数组取值 并强转</span>
                           <span class="hljs-function">E <span class="hljs-title">elementData</span><span class="hljs-params">(<span class="hljs-keyword">int</span> index)</span> </span>{
                               <span class="hljs-keyword">return</span> (E) elementData[index];
                           }
                       
                       <span class="hljs-comment">//删除该元素在数组中第一次出现的位置上的数据。 如果有该元素返回true，如果false。</span>
                       <span class="hljs-function"><span class="hljs-keyword">public</span> <span class="hljs-keyword">boolean</span> <span class="hljs-title">remove</span><span class="hljs-params">(Object o)</span> </span>{
                           <span class="hljs-keyword">if</span> (o == <span class="hljs-keyword">null</span>) {
                               <span class="hljs-keyword">for</span> (<span class="hljs-keyword">int</span> index = <span class="hljs-number">0</span>; index &lt; size; index++)
                                   <span class="hljs-keyword">if</span> (elementData[index] == <span class="hljs-keyword">null</span>) {
                                       fastRemove(index);<span class="hljs-comment">//根据index删除元素</span>
                                       <span class="hljs-keyword">return</span> <span class="hljs-keyword">true</span>;
                                   }
                           } <span class="hljs-keyword">else</span> {
                               <span class="hljs-keyword">for</span> (<span class="hljs-keyword">int</span> index = <span class="hljs-number">0</span>; index &lt; size; index++)
                                   <span class="hljs-keyword">if</span> (o.equals(elementData[index])) {
                                       fastRemove(index);
                                       <span class="hljs-keyword">return</span> <span class="hljs-keyword">true</span>;
                                   }
                           }
                           <span class="hljs-keyword">return</span> <span class="hljs-keyword">false</span>;
                       }
                       <span class="hljs-comment">//不会越界 不用判断 ，也不需要取出该元素。</span>
                       <span class="hljs-function"><span class="hljs-keyword">private</span> <span class="hljs-keyword">void</span> <span class="hljs-title">fastRemove</span><span class="hljs-params">(<span class="hljs-keyword">int</span> index)</span> </span>{
                           modCount++;<span class="hljs-comment">//修改modCount</span>
                           <span class="hljs-keyword">int</span> numMoved = size - index - <span class="hljs-number">1</span>;<span class="hljs-comment">//计算要移动的元素数量</span>
                           <span class="hljs-keyword">if</span> (numMoved &gt; <span class="hljs-number">0</span>)
                               System.arraycopy(elementData, index+<span class="hljs-number">1</span>, elementData, index,
                                                numMoved);<span class="hljs-comment">//以复制覆盖元素 完成删除</span>
                           elementData[--size] = <span class="hljs-keyword">null</span>; <span class="hljs-comment">// clear to let GC do its work  //置空 不再强引用</span>
                       }
                       
                       <span class="hljs-comment">//批量删除</span>
                       <span class="hljs-function"><span class="hljs-keyword">public</span> <span class="hljs-keyword">boolean</span> <span class="hljs-title">removeAll</span><span class="hljs-params">(Collection&lt;?&gt; c)</span> </span>{
                           Objects.requireNonNull(c);<span class="hljs-comment">//判空</span>
                           <span class="hljs-keyword">return</span> batchRemove(c, <span class="hljs-keyword">false</span>);
                       }
                       <span class="hljs-comment">//批量移动</span>
                       <span class="hljs-function"><span class="hljs-keyword">private</span> <span class="hljs-keyword">boolean</span> <span class="hljs-title">batchRemove</span><span class="hljs-params">(Collection&lt;?&gt; c, <span class="hljs-keyword">boolean</span> complement)</span> </span>{
                           <span class="hljs-keyword">final</span> Object[] elementData = <span class="hljs-keyword">this</span>.elementData;
                           <span class="hljs-keyword">int</span> r = <span class="hljs-number">0</span>, w = <span class="hljs-number">0</span>;<span class="hljs-comment">//w 代表批量删除后 数组还剩多少元素</span>
                           <span class="hljs-keyword">boolean</span> modified = <span class="hljs-keyword">false</span>;
                           <span class="hljs-keyword">try</span> {
                               <span class="hljs-comment">//高效的保存两个集合公有元素的算法</span>
                               <span class="hljs-keyword">for</span> (; r &lt; size; r++)
                                   <span class="hljs-keyword">if</span> (c.contains(elementData[r]) == complement) <span class="hljs-comment">// 如果 c里不包含当前下标元素， </span>
                                       elementData[w++] = elementData[r];<span class="hljs-comment">//则保留</span>
                           } <span class="hljs-keyword">finally</span> {
                               <span class="hljs-comment">// Preserve behavioral compatibility with AbstractCollection,</span>
                               <span class="hljs-comment">// even if c.contains() throws.</span>
                               <span class="hljs-keyword">if</span> (r != size) { <span class="hljs-comment">//出现异常会导致 r !=size , 则将出现异常处后面的数据全部复制覆盖到数组里。</span>
                                   System.arraycopy(elementData, r,
                                                    elementData, w,
                                                    size - r);
                                   w += size - r;<span class="hljs-comment">//修改 w数量</span>
                               }
                               <span class="hljs-keyword">if</span> (w != size) {<span class="hljs-comment">//置空数组后面的元素</span>
                                   <span class="hljs-comment">// clear to let GC do its work</span>
                                   <span class="hljs-keyword">for</span> (<span class="hljs-keyword">int</span> i = w; i &lt; size; i++)
                                       elementData[i] = <span class="hljs-keyword">null</span>;
                                   modCount += size - w;<span class="hljs-comment">//修改modCount</span>
                                   size = w;<span class="hljs-comment">// 修改size</span>
                                   modified = <span class="hljs-keyword">true</span>;
                               }
                           }
                           <span class="hljs-keyword">return</span> modified;
                       }
                       </code></pre>
                       
                    #### 小结： 
                    <br/>
                         1 删除操作一定会修改modCount，且可能涉及到数组的复制，相对低效。 <br/>
                         2 批量删除中，涉及高效的保存两个集合公有元素的算法，可以留意一下。
             <h3>改</h3>
             <p><strong>不会修改modCount，相对增删是高效的操作。</strong></p>
             <pre class="hljs cpp"><code class="cpp"><span class="hljs-function"><span class="hljs-keyword">public</span> E <span class="hljs-title">set</span><span class="hljs-params">(<span class="hljs-keyword">int</span> index, E element)</span> </span>{
                 rangeCheck(index);<span class="hljs-comment">//越界检查</span>
                 E oldValue = elementData(index); <span class="hljs-comment">//取出元素 </span>
                 elementData[index] = element;<span class="hljs-comment">//覆盖元素</span>
                 <span class="hljs-keyword">return</span> oldValue;<span class="hljs-comment">//返回元素</span>
             }
             </code></pre>
             
             <h3>查</h3>
             <p><strong>不会修改modCount，相对增删是高效的操作。</strong></p>
             <pre class="hljs cpp"><code class="cpp"><span class="hljs-function"><span class="hljs-keyword">public</span> E <span class="hljs-title">get</span><span class="hljs-params">(<span class="hljs-keyword">int</span> index)</span> </span>{
                 rangeCheck(index);<span class="hljs-comment">//越界检查</span>
                 <span class="hljs-keyword">return</span> elementData(index); <span class="hljs-comment">//下标取数据</span>
             }
             <span class="hljs-function">E <span class="hljs-title">elementData</span><span class="hljs-params">(<span class="hljs-keyword">int</span> index)</span> </span>{
                 <span class="hljs-keyword">return</span> (E) elementData[index];
             }
             </code></pre>
             
             <h3>清空，clear</h3>
             <p><strong>会修改modCount。</strong></p>
             
             <pre class="hljs java"><code class="java"><span class="hljs-function"><span class="hljs-keyword">public</span> <span class="hljs-keyword">void</span> <span class="hljs-title">clear</span><span class="hljs-params">()</span> </span>{
                 modCount++;<span class="hljs-comment">//修改modCount</span>
                 <span class="hljs-comment">// clear to let GC do its work</span>
                 <span class="hljs-keyword">for</span> (<span class="hljs-keyword">int</span> i = <span class="hljs-number">0</span>; i &lt; size; i++)  <span class="hljs-comment">//将所有元素置null</span>
                     elementData[i] = <span class="hljs-keyword">null</span>;
             
                 size = <span class="hljs-number">0</span>; <span class="hljs-comment">//修改size </span>
             }
             </code></pre>
             
             <h3>包含 contain</h3>
             <pre class="hljs java"><code class="java"><span class="hljs-comment">//普通的for循环寻找值，只不过会循环两遍。第一遍找null，第二遍找对应的值。</span>
             <span class="hljs-function"><span class="hljs-keyword">public</span> <span class="hljs-keyword">boolean</span> <span class="hljs-title">contains</span><span class="hljs-params">(Object o)</span> </span>{
                 <span class="hljs-keyword">return</span> indexOf(o) &gt;= <span class="hljs-number">0</span>;
             }
             <span class="hljs-comment">//:普通的for循环寻找值，只不过会循环两遍。第一遍找null，第二遍找对应的值。</span>
             <span class="hljs-function"><span class="hljs-keyword">public</span> <span class="hljs-keyword">int</span> <span class="hljs-title">indexOf</span><span class="hljs-params">(Object o)</span> </span>{
                 <span class="hljs-keyword">if</span> (o == <span class="hljs-keyword">null</span>) {
                     <span class="hljs-keyword">for</span> (<span class="hljs-keyword">int</span> i = <span class="hljs-number">0</span>; i &lt; size; i++)
                         <span class="hljs-keyword">if</span> (elementData[i]==<span class="hljs-keyword">null</span>)
                             <span class="hljs-keyword">return</span> i;
                 } <span class="hljs-keyword">else</span> {
                     <span class="hljs-keyword">for</span> (<span class="hljs-keyword">int</span> i = <span class="hljs-number">0</span>; i &lt; size; i++)
                         <span class="hljs-keyword">if</span> (o.equals(elementData[i]))
                             <span class="hljs-keyword">return</span> i;
                 }
                 <span class="hljs-keyword">return</span> -<span class="hljs-number">1</span>;
             }
             </code></pre>
             
             <h3>判空 isEmpty()</h3>
             <pre class="hljs java"><code class="java"><span class="hljs-function"><span class="hljs-keyword">public</span> <span class="hljs-keyword">boolean</span> <span class="hljs-title">isEmpty</span><span class="hljs-params">()</span> </span>{
                 <span class="hljs-keyword">return</span> size == <span class="hljs-number">0</span>;
             }
             </code></pre>
             
             <h3>迭代器 Iterator.</h3>
             
             <pre class="hljs java"><code class="java"><span class="hljs-function"><span class="hljs-keyword">public</span> Iterator&lt;E&gt; <span class="hljs-title">iterator</span><span class="hljs-params">()</span> </span>{
                 <span class="hljs-keyword">return</span> <span class="hljs-keyword">new</span> Itr();
             }
             <span class="hljs-comment">/**
              * An optimized version of AbstractList.Itr
              */</span>
             <span class="hljs-keyword">private</span> <span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">Itr</span> <span class="hljs-keyword">implements</span> <span class="hljs-title">Iterator</span>&lt;<span class="hljs-title">E</span>&gt; </span>{
                 <span class="hljs-keyword">int</span> cursor;       <span class="hljs-comment">// index of next element to return //默认是0</span>
                 <span class="hljs-keyword">int</span> lastRet = -<span class="hljs-number">1</span>; <span class="hljs-comment">// index of last element returned; -1 if no such  //上一次返回的元素 (删除的标志位)</span>
                 <span class="hljs-keyword">int</span> expectedModCount = modCount; <span class="hljs-comment">//用于判断集合是否修改过结构的 标志</span>
             
                 <span class="hljs-function"><span class="hljs-keyword">public</span> <span class="hljs-keyword">boolean</span> <span class="hljs-title">hasNext</span><span class="hljs-params">()</span> </span>{
                     <span class="hljs-keyword">return</span> cursor != size;
                 }
             
                 <span class="hljs-meta">@SuppressWarnings</span>(<span class="hljs-string">"unchecked"</span>)
                 <span class="hljs-function"><span class="hljs-keyword">public</span> E <span class="hljs-title">next</span><span class="hljs-params">()</span> </span>{
                     checkForComodification();
                     <span class="hljs-keyword">int</span> i = cursor;
                     <span class="hljs-keyword">if</span> (i &gt;= size)<span class="hljs-comment">//判断是否越界</span>
                         <span class="hljs-keyword">throw</span> <span class="hljs-keyword">new</span> NoSuchElementException();
                     Object[] elementData = ArrayList.<span class="hljs-keyword">this</span>.elementData;
                     <span class="hljs-keyword">if</span> (i &gt;= elementData.length)<span class="hljs-comment">//再次判断是否越界，在 我们这里的操作时，有异步线程修改了List</span>
                         <span class="hljs-keyword">throw</span> <span class="hljs-keyword">new</span> ConcurrentModificationException();
                     cursor = i + <span class="hljs-number">1</span>;<span class="hljs-comment">//游标+1</span>
                     <span class="hljs-keyword">return</span> (E) elementData[lastRet = i];<span class="hljs-comment">//返回元素 ，并设置上一次返回的元素的下标</span>
                 }
             
                 <span class="hljs-function"><span class="hljs-keyword">public</span> <span class="hljs-keyword">void</span> <span class="hljs-title">remove</span><span class="hljs-params">()</span> </span>{<span class="hljs-comment">//remove 掉 上一次next的元素</span>
                     <span class="hljs-keyword">if</span> (lastRet &lt; <span class="hljs-number">0</span>)<span class="hljs-comment">//先判断是否next过</span>
                         <span class="hljs-keyword">throw</span> <span class="hljs-keyword">new</span> IllegalStateException();
                     checkForComodification();<span class="hljs-comment">//判断是否修改过</span>
             
                     <span class="hljs-keyword">try</span> {
                         ArrayList.<span class="hljs-keyword">this</span>.remove(lastRet);<span class="hljs-comment">//删除元素 remove方法内会修改 modCount 所以后面要更新Iterator里的这个标志值</span>
                         cursor = lastRet; <span class="hljs-comment">//要删除的游标</span>
                         lastRet = -<span class="hljs-number">1</span>; <span class="hljs-comment">//不能重复删除 所以修改删除的标志位</span>
                         expectedModCount = modCount;<span class="hljs-comment">//更新 判断集合是否修改的标志，</span>
                     } <span class="hljs-keyword">catch</span> (IndexOutOfBoundsException ex) {
                         <span class="hljs-keyword">throw</span> <span class="hljs-keyword">new</span> ConcurrentModificationException();
                     }
                 }
             <span class="hljs-comment">//判断是否修改过了List的结构，如果有修改，抛出异常</span>
                 <span class="hljs-function"><span class="hljs-keyword">final</span> <span class="hljs-keyword">void</span> <span class="hljs-title">checkForComodification</span><span class="hljs-params">()</span> </span>{
                     <span class="hljs-keyword">if</span> (modCount != expectedModCount)
                         <span class="hljs-keyword">throw</span> <span class="hljs-keyword">new</span> ConcurrentModificationException();
                 }
             }
             </code></pre>
             
            #### 总结
            
            1、增删改查中， 增导致扩容，则会修改modCount，删一定会修改。改和查一定不会修改modCount。 <br/>
            2、扩容操作会导致数组复制，批量删除会导致 找出两个集合的交集，以及数组复制操作，因此，增、删都相对低效。 而 改、查都是很高效的操作。 <br/>
            3、因此，结合特点，在使用中，以Android中最常用的展示列表为例，列表滑动时需要展示每一个Item（element）的数组，所以 查 操作是最高频的。相对来说，增操作 只有在列表加载更多时才会用到 ，而且是在列表尾部插入，所以也不需要移动数据的操作。而删操作则更低频。 故选用ArrayList作为保存数据的结构。
            
            [参考：ArrayList源码解析（JDK8）](https://www.jianshu.com/p/192148ddab9f)
             
     * LinkedList
        
        <P>LinkedList和ArrayList比较：</p>
        <p>ArrayList的增删效率低，但是改查效率高。而LinkedList正好相反，增删由于不需要移动底层数组数据，其底层是链表实现的，只需要修改链表节点指针，所以效率较高。
           而改和查，都需要先定位到目标节点（由于允许null值的存在，往往要进行两个for循环遍历，时间复杂度o(n)），所以效率较低。</p>
        <p>开篇前，再说一遍Collection.toArray(); 
           这个方法很重要，不管是ArrayList、LinkedList 在批量add的时候，都会先转化成数组去做。 因为数组可以用for循环直接花式遍历。比较方便 高效</p>
     * 思路 
        
        > 构造方法->常用API（增、删、改、查）的顺序来阅读源码，并会讲解阅读方法中涉及的一些变量的意义。了解LinkedList的特点、适用场景
      
     * 慨括
        
        LinkedList 是线程不安全的，允许元素为null的双向链表。
        其底层数据结构是链表，它实现List<E>, Deque<E>, Cloneable, java.io.Serializable接口，它实现了Deque<E>,所以它也可以作为一个双端队列。和ArrayList比，没有实现RandomAccess所以其以下标，随机访问元素速度较慢。
        <br/>
        > 当每次增、删时，都会修改modCount。
        
     * 构造方法
     
        * LinkedList底层是链表
        <br/>
        <br/>
        <pre class="hljs java"><code class="java">    <span class="hljs-comment">//集合元素数量</span>
            <span class="hljs-keyword">transient</span> <span class="hljs-keyword">int</span> size = <span class="hljs-number">0</span>;
            <span class="hljs-comment">//链表头节点</span>
            <span class="hljs-keyword">transient</span> Node&lt;E&gt; first;
            <span class="hljs-comment">//链表尾节点</span>
            <span class="hljs-keyword">transient</span> Node&lt;E&gt; last;
            <span class="hljs-comment">//啥都不干</span>
            <span class="hljs-function"><span class="hljs-keyword">public</span> <span class="hljs-title">LinkedList</span><span class="hljs-params">()</span> </span>{
            }
            <span class="hljs-comment">//调用     public boolean addAll(Collection&lt;? extends E&gt; c)  将集合c所有元素插入链表中</span>
            <span class="hljs-function"><span class="hljs-keyword">public</span> <span class="hljs-title">LinkedList</span><span class="hljs-params">(Collection&lt;? extends E&gt; c)</span> </span>{
                <span class="hljs-keyword">this</span>();
                addAll(c);
            }
        </code></pre>
        
        构造方法基本没干啥。
        
        * 节点Node结构:
        
           <pre class="hljs cpp"><code class="cpp">    <span class="hljs-keyword">private</span> <span class="hljs-keyword">static</span> <span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">Node</span>&lt;E&gt; {</span>
                   E item;<span class="hljs-comment">//元素值</span>
                   Node&lt;E&gt; next;<span class="hljs-comment">//后置节点</span>
                   Node&lt;E&gt; prev;<span class="hljs-comment">//前置节点</span>
           
                   Node(Node&lt;E&gt; prev, E element, Node&lt;E&gt; next) {
                       <span class="hljs-keyword">this</span>.item = element;
                       <span class="hljs-keyword">this</span>.next = next;
                       <span class="hljs-keyword">this</span>.prev = prev;
                   }
               }
           </code></pre>
        
        * addAll方法()
            
            <pre class="hljs java"><code class="java"><span class="hljs-comment">//addAll ,在尾部批量增加</span>
            <span class="hljs-function"><span class="hljs-keyword">public</span> <span class="hljs-keyword">boolean</span> <span class="hljs-title">addAll</span><span class="hljs-params">(Collection&lt;? extends E&gt; c)</span> </span>{
                <span class="hljs-keyword">return</span> addAll(size, c);<span class="hljs-comment">//以size为插入下标，插入集合c中所有元素</span>
            }
            <span class="hljs-comment">//以index为插入下标，插入集合c中所有元素</span>
            <span class="hljs-function"><span class="hljs-keyword">public</span> <span class="hljs-keyword">boolean</span> <span class="hljs-title">addAll</span><span class="hljs-params">(<span class="hljs-keyword">int</span> index, Collection&lt;? extends E&gt; c)</span> </span>{
                checkPositionIndex(index);<span class="hljs-comment">//检查越界 [0,size] 闭区间</span>
            
                Object[] a = c.toArray();<span class="hljs-comment">//拿到目标集合数组</span>
                <span class="hljs-keyword">int</span> numNew = a.length;<span class="hljs-comment">//新增元素的数量</span>
                <span class="hljs-keyword">if</span> (numNew == <span class="hljs-number">0</span>)<span class="hljs-comment">//如果新增元素数量为0，则不增加，并返回false</span>
                    <span class="hljs-keyword">return</span> <span class="hljs-keyword">false</span>;
            
                Node&lt;E&gt; pred, succ;  <span class="hljs-comment">//index节点的前置节点，后置节点</span>
                <span class="hljs-keyword">if</span> (index == size) { <span class="hljs-comment">//在链表尾部追加数据</span>
                    succ = <span class="hljs-keyword">null</span>;  <span class="hljs-comment">//size节点（队尾）的后置节点一定是null</span>
                    pred = last;<span class="hljs-comment">//前置节点是队尾</span>
                } <span class="hljs-keyword">else</span> {
                    succ = node(index);<span class="hljs-comment">//取出index节点，作为后置节点</span>
                    pred = succ.prev; <span class="hljs-comment">//前置节点是，index节点的前一个节点</span>
                }
                <span class="hljs-comment">//链表批量增加，是靠for循环遍历原数组，依次执行插入节点操作。对比ArrayList是通过System.arraycopy完成批量增加的</span>
                <span class="hljs-keyword">for</span> (Object o : a) {<span class="hljs-comment">//遍历要添加的节点。</span>
                    <span class="hljs-meta">@SuppressWarnings</span>(<span class="hljs-string">"unchecked"</span>) E e = (E) o;
                    Node&lt;E&gt; newNode = <span class="hljs-keyword">new</span> Node&lt;&gt;(pred, e, <span class="hljs-keyword">null</span>);<span class="hljs-comment">//以前置节点 和 元素值e，构建new一个新节点，</span>
                    <span class="hljs-keyword">if</span> (pred == <span class="hljs-keyword">null</span>) <span class="hljs-comment">//如果前置节点是空，说明是头结点</span>
                        first = newNode;
                    <span class="hljs-keyword">else</span><span class="hljs-comment">//否则 前置节点的后置节点设置问新节点</span>
                        pred.next = newNode;
                    pred = newNode;<span class="hljs-comment">//步进，当前的节点为前置节点了，为下次添加节点做准备</span>
                }
            
                <span class="hljs-keyword">if</span> (succ == <span class="hljs-keyword">null</span>) {<span class="hljs-comment">//循环结束后，判断，如果后置节点是null。 说明此时是在队尾append的。</span>
                    last = pred; <span class="hljs-comment">//则设置尾节点</span>
                } <span class="hljs-keyword">else</span> {
                    pred.next = succ; <span class="hljs-comment">// 否则是在队中插入的节点 ，更新前置节点 后置节点</span>
                    succ.prev = pred; <span class="hljs-comment">//更新后置节点的前置节点</span>
                }
            
                size += numNew;  <span class="hljs-comment">// 修改数量size</span>
                modCount++;  <span class="hljs-comment">//修改modCount</span>
                <span class="hljs-keyword">return</span> <span class="hljs-keyword">true</span>;
            }
            <span class="hljs-comment">//根据index 查询出Node，</span>
            <span class="hljs-function">Node&lt;E&gt; <span class="hljs-title">node</span><span class="hljs-params">(<span class="hljs-keyword">int</span> index)</span> </span>{
                <span class="hljs-comment">// assert isElementIndex(index);</span>
            <span class="hljs-comment">//通过下标获取某个node 的时候，（增、查 ），会根据index处于前半段还是后半段 进行一个折半，以提升查询效率</span>
                <span class="hljs-keyword">if</span> (index &lt; (size &gt;&gt; <span class="hljs-number">1</span>)) {
                    Node&lt;E&gt; x = first;
                    <span class="hljs-keyword">for</span> (<span class="hljs-keyword">int</span> i = <span class="hljs-number">0</span>; i &lt; index; i++)
                        x = x.next;
                    <span class="hljs-keyword">return</span> x;
                } <span class="hljs-keyword">else</span> {
                    Node&lt;E&gt; x = last;
                    <span class="hljs-keyword">for</span> (<span class="hljs-keyword">int</span> i = size - <span class="hljs-number">1</span>; i &gt; index; i--)
                        x = x.prev;
                    <span class="hljs-keyword">return</span> x;
                }
            }
            
            <span class="hljs-function"><span class="hljs-keyword">private</span> <span class="hljs-keyword">void</span> <span class="hljs-title">checkPositionIndex</span><span class="hljs-params">(<span class="hljs-keyword">int</span> index)</span> </span>{
                <span class="hljs-keyword">if</span> (!isPositionIndex(index))
                    <span class="hljs-keyword">throw</span> <span class="hljs-keyword">new</span> IndexOutOfBoundsException(outOfBoundsMsg(index));
            }
            <span class="hljs-function"><span class="hljs-keyword">private</span> <span class="hljs-keyword">boolean</span> <span class="hljs-title">isPositionIndex</span><span class="hljs-params">(<span class="hljs-keyword">int</span> index)</span> </span>{
                <span class="hljs-keyword">return</span> index &gt;= <span class="hljs-number">0</span> &amp;&amp; index &lt;= size;  <span class="hljs-comment">//插入时的检查，下标可以是size [0,size]</span>
            }
            </code></pre>
            
        #### 小结：
          
          1)、链表批量增加，是靠for循环遍历原数组，依次执行插入节点操作。对比ArrayList是通过System.arraycopy完成批量增加的<br/>
          2)、通过下标获取某个node 的时候，（add select），会根据index处于前半段还是后半段 进行一个折半，以提升查询效率    
          
        *  插入单个节点 add
            
             <pre class="hljs java"><code class="java"><span class="hljs-comment">//在尾部插入一个节点： add</span>
               <span class="hljs-function"><span class="hljs-keyword">public</span> <span class="hljs-keyword">boolean</span> <span class="hljs-title">add</span><span class="hljs-params">(E e)</span> </span>{
                   linkLast(e);
                   <span class="hljs-keyword">return</span> <span class="hljs-keyword">true</span>;
               }
               
               <span class="hljs-comment">//生成新节点 并插入到 链表尾部， 更新 last/first 节点。</span>
               <span class="hljs-function"><span class="hljs-keyword">void</span> <span class="hljs-title">linkLast</span><span class="hljs-params">(E e)</span> </span>{ 
                   <span class="hljs-keyword">final</span> Node&lt;E&gt; l = last; <span class="hljs-comment">//记录原尾部节点</span>
                   <span class="hljs-keyword">final</span> Node&lt;E&gt; newNode = <span class="hljs-keyword">new</span> Node&lt;&gt;(l, e, <span class="hljs-keyword">null</span>);<span class="hljs-comment">//以原尾部节点为新节点的前置节点</span>
                   last = newNode;<span class="hljs-comment">//更新尾部节点</span>
                   <span class="hljs-keyword">if</span> (l == <span class="hljs-keyword">null</span>)<span class="hljs-comment">//若原链表为空链表，需要额外更新头结点</span>
                       first = newNode;
                   <span class="hljs-keyword">else</span><span class="hljs-comment">//否则更新原尾节点的后置节点为现在的尾节点（新节点）</span>
                       l.next = newNode;
                   size++;<span class="hljs-comment">//修改size</span>
                   modCount++;<span class="hljs-comment">//修改modCount</span>
               }
               </code></pre>
               
             <pre class="hljs java"><code class="java">    <span class="hljs-comment">//在指定下标，index处，插入一个节点</span>
                 <span class="hljs-function"><span class="hljs-keyword">public</span> <span class="hljs-keyword">void</span> <span class="hljs-title">add</span><span class="hljs-params">(<span class="hljs-keyword">int</span> index, E element)</span> </span>{
                     checkPositionIndex(index);<span class="hljs-comment">//检查下标是否越界[0,size]</span>
                     <span class="hljs-keyword">if</span> (index == size)<span class="hljs-comment">//在尾节点后插入</span>
                         linkLast(element);
                     <span class="hljs-keyword">else</span><span class="hljs-comment">//在中间插入</span>
                         linkBefore(element, node(index));
                 }
                 <span class="hljs-comment">//在succ节点前，插入一个新节点e</span>
                 <span class="hljs-function"><span class="hljs-keyword">void</span> <span class="hljs-title">linkBefore</span><span class="hljs-params">(E e, Node&lt;E&gt; succ)</span> </span>{
                     <span class="hljs-comment">// assert succ != null;</span>
                     <span class="hljs-comment">//保存后置节点的前置节点</span>
                     <span class="hljs-keyword">final</span> Node&lt;E&gt; pred = succ.prev;
                     <span class="hljs-comment">//以前置和后置节点和元素值e 构建一个新节点</span>
                     <span class="hljs-keyword">final</span> Node&lt;E&gt; newNode = <span class="hljs-keyword">new</span> Node&lt;&gt;(pred, e, succ);
                     <span class="hljs-comment">//新节点new是原节点succ的前置节点</span>
                     succ.prev = newNode;
                     <span class="hljs-keyword">if</span> (pred == <span class="hljs-keyword">null</span>)<span class="hljs-comment">//如果之前的前置节点是空，说明succ是原头结点。所以新节点是现在的头结点</span>
                         first = newNode;
                     <span class="hljs-keyword">else</span><span class="hljs-comment">//否则构建前置节点的后置节点为new</span>
                         pred.next = newNode;
                     size++;<span class="hljs-comment">//修改数量</span>
                     modCount++;<span class="hljs-comment">//修改modCount</span>
                 }
             </code></pre>
             
        * 删 Remove
        
            <pre class="hljs java"><code class="java"><span class="hljs-comment">//删：remove目标节点</span>
            <span class="hljs-function"><span class="hljs-keyword">public</span> E <span class="hljs-title">remove</span><span class="hljs-params">(<span class="hljs-keyword">int</span> index)</span> </span>{
                checkElementIndex(index);<span class="hljs-comment">//检查是否越界 下标[0,size)</span>
                <span class="hljs-keyword">return</span> unlink(node(index));<span class="hljs-comment">//从链表上删除某节点</span>
            }
            <span class="hljs-comment">//从链表上删除x节点</span>
            <span class="hljs-function">E <span class="hljs-title">unlink</span><span class="hljs-params">(Node&lt;E&gt; x)</span> </span>{
                <span class="hljs-comment">// assert x != null;</span>
                <span class="hljs-keyword">final</span> E element = x.item; <span class="hljs-comment">//当前节点的元素值</span>
                <span class="hljs-keyword">final</span> Node&lt;E&gt; next = x.next; <span class="hljs-comment">//当前节点的后置节点</span>
                <span class="hljs-keyword">final</span> Node&lt;E&gt; prev = x.prev;<span class="hljs-comment">//当前节点的前置节点</span>
            
                <span class="hljs-keyword">if</span> (prev == <span class="hljs-keyword">null</span>) { <span class="hljs-comment">//如果前置节点为空(说明当前节点原本是头结点)</span>
                    first = next;  <span class="hljs-comment">//则头结点等于后置节点 </span>
                } <span class="hljs-keyword">else</span> { 
                    prev.next = next;
                    x.prev = <span class="hljs-keyword">null</span>; <span class="hljs-comment">//将当前节点的 前置节点置空</span>
                }
            
                <span class="hljs-keyword">if</span> (next == <span class="hljs-keyword">null</span>) {<span class="hljs-comment">//如果后置节点为空（说明当前节点原本是尾节点）</span>
                    last = prev; <span class="hljs-comment">//则 尾节点为前置节点</span>
                } <span class="hljs-keyword">else</span> {
                    next.prev = prev;
                    x.next = <span class="hljs-keyword">null</span>;<span class="hljs-comment">//将当前节点的 后置节点置空</span>
                }
            
                x.item = <span class="hljs-keyword">null</span>; <span class="hljs-comment">//将当前元素值置空</span>
                size--; <span class="hljs-comment">//修改数量</span>
                modCount++;  <span class="hljs-comment">//修改modCount</span>
                <span class="hljs-keyword">return</span> element; <span class="hljs-comment">//返回取出的元素值</span>
            }
                <span class="hljs-function"><span class="hljs-keyword">private</span> <span class="hljs-keyword">void</span> <span class="hljs-title">checkElementIndex</span><span class="hljs-params">(<span class="hljs-keyword">int</span> index)</span> </span>{
                    <span class="hljs-keyword">if</span> (!isElementIndex(index))
                        <span class="hljs-keyword">throw</span> <span class="hljs-keyword">new</span> IndexOutOfBoundsException(outOfBoundsMsg(index));
                }
                <span class="hljs-comment">//下标[0,size)</span>
                <span class="hljs-function"><span class="hljs-keyword">private</span> <span class="hljs-keyword">boolean</span> <span class="hljs-title">isElementIndex</span><span class="hljs-params">(<span class="hljs-keyword">int</span> index)</span> </span>{
                    <span class="hljs-keyword">return</span> index &gt;= <span class="hljs-number">0</span> &amp;&amp; index &lt; size;
                }
            
            </code></pre>
            
            > 删除链表中的指定节点，也是要遍历两次：
            
            <pre class="hljs java"><code class="java">    <span class="hljs-comment">//因为要考虑 null元素，也是要遍历两次</span>
                <span class="hljs-function"><span class="hljs-keyword">public</span> <span class="hljs-keyword">boolean</span> <span class="hljs-title">remove</span><span class="hljs-params">(Object o)</span> </span>{
                    <span class="hljs-keyword">if</span> (o == <span class="hljs-keyword">null</span>) {<span class="hljs-comment">//如果要删除的是null节点(从remove和add 里 可以看出，允许元素为null)</span>
                        <span class="hljs-comment">//遍历每个节点 对比</span>
                        <span class="hljs-keyword">for</span> (Node&lt;E&gt; x = first; x != <span class="hljs-keyword">null</span>; x = x.next) {
                            <span class="hljs-keyword">if</span> (x.item == <span class="hljs-keyword">null</span>) {
                                unlink(x);
                                <span class="hljs-keyword">return</span> <span class="hljs-keyword">true</span>;
                            }
                        }
                    } <span class="hljs-keyword">else</span> {
                        <span class="hljs-keyword">for</span> (Node&lt;E&gt; x = first; x != <span class="hljs-keyword">null</span>; x = x.next) {
                            <span class="hljs-keyword">if</span> (o.equals(x.item)) {
                                unlink(x);
                                <span class="hljs-keyword">return</span> <span class="hljs-keyword">true</span>;
                            }
                        }
                    }
                    <span class="hljs-keyword">return</span> <span class="hljs-keyword">false</span>;
                }
                <span class="hljs-comment">//将节点x，从链表中删除</span>
                <span class="hljs-function">E <span class="hljs-title">unlink</span><span class="hljs-params">(Node&lt;E&gt; x)</span> </span>{
                    <span class="hljs-comment">// assert x != null;</span>
                    <span class="hljs-keyword">final</span> E element = x.item;<span class="hljs-comment">//继续元素值，供返回</span>
                    <span class="hljs-keyword">final</span> Node&lt;E&gt; next = x.next;<span class="hljs-comment">//保存当前节点的后置节点</span>
                    <span class="hljs-keyword">final</span> Node&lt;E&gt; prev = x.prev;<span class="hljs-comment">//前置节点</span>
            
                    <span class="hljs-keyword">if</span> (prev == <span class="hljs-keyword">null</span>) {<span class="hljs-comment">//前置节点为null，</span>
                        first = next;<span class="hljs-comment">//则首节点为next</span>
                    } <span class="hljs-keyword">else</span> {<span class="hljs-comment">//否则 更新前置节点的后置节点</span>
                        prev.next = next;
                        x.prev = <span class="hljs-keyword">null</span>;<span class="hljs-comment">//记得将要删除节点的前置节点置null</span>
                    }
                    <span class="hljs-comment">//如果后置节点为null，说明是尾节点</span>
                    <span class="hljs-keyword">if</span> (next == <span class="hljs-keyword">null</span>) {
                        last = prev;
                    } <span class="hljs-keyword">else</span> {<span class="hljs-comment">//否则更新 后置节点的前置节点</span>
                        next.prev = prev;
                        x.next = <span class="hljs-keyword">null</span>;<span class="hljs-comment">//记得删除节点的后置节点为null</span>
                    }
                    <span class="hljs-comment">//将删除节点的元素值置null，以便GC</span>
                    x.item = <span class="hljs-keyword">null</span>;
                    size--;<span class="hljs-comment">//修改size</span>
                    modCount++;<span class="hljs-comment">//修改modCount</span>
                    <span class="hljs-keyword">return</span> element;<span class="hljs-comment">//返回删除的元素值</span>
                }
            </code></pre>
            
            <P>删也一定会修改modCount。 按下标删，也是先根据index找到Node，然后去链表上unlink掉这个Node。 按元素删，会先去遍历链表寻找是否有该Node，考虑到允许null值，所以会遍历两遍，然后再去unlink它.</P>
            
        * 改 Set
        
            <pre class="hljs cpp"><code class="cpp"><span class="hljs-function"><span class="hljs-keyword">public</span> E <span class="hljs-title">set</span><span class="hljs-params">(<span class="hljs-keyword">int</span> index, E element)</span> </span>{
                checkElementIndex(index); <span class="hljs-comment">//检查越界[0,size)</span>
                Node&lt;E&gt; x = node(index);<span class="hljs-comment">//取出对应的Node</span>
                E oldVal = x.item;<span class="hljs-comment">//保存旧值 供返回</span>
                x.item = element;<span class="hljs-comment">//用新值覆盖旧值</span>
                <span class="hljs-keyword">return</span> oldVal;<span class="hljs-comment">//返回旧值</span>
            }
            </code></pre>
            
            > 改也是先根据index找到Node，然后替换值，改不修改modCount
         
        * 查get  
            
            * 根据index查询节点
            
                <pre class="hljs cpp"><code class="cpp"><span class="hljs-function"><span class="hljs-keyword">public</span> E <span class="hljs-title">get</span><span class="hljs-params">(<span class="hljs-keyword">int</span> index)</span> </span>{
                    checkElementIndex(index);<span class="hljs-comment">//判断是否越界 [0,size)</span>
                    <span class="hljs-keyword">return</span> node(index).item; <span class="hljs-comment">//调用node()方法 取出 Node节点，</span>
                }
                </code></pre>
                
            * 根据节点对象，查询下标,也是需要遍历两遍链表。
            
                <pre class="hljs java"><code class="java">    <span class="hljs-function"><span class="hljs-keyword">public</span> <span class="hljs-keyword">int</span> <span class="hljs-title">indexOf</span><span class="hljs-params">(Object o)</span> </span>{
                        <span class="hljs-keyword">int</span> index = <span class="hljs-number">0</span>;
                        <span class="hljs-keyword">if</span> (o == <span class="hljs-keyword">null</span>) {<span class="hljs-comment">//如果目标对象是null</span>
                        <span class="hljs-comment">//遍历链表</span>
                            <span class="hljs-keyword">for</span> (Node&lt;E&gt; x = first; x != <span class="hljs-keyword">null</span>; x = x.next) {
                                <span class="hljs-keyword">if</span> (x.item == <span class="hljs-keyword">null</span>)
                                    <span class="hljs-keyword">return</span> index;
                                index++;
                            }
                        } <span class="hljs-keyword">else</span> {<span class="hljs-comment">////遍历链表</span>
                            <span class="hljs-keyword">for</span> (Node&lt;E&gt; x = first; x != <span class="hljs-keyword">null</span>; x = x.next) {
                                <span class="hljs-keyword">if</span> (o.equals(x.item))
                                    <span class="hljs-keyword">return</span> index;
                                index++;
                            }
                        }
                        <span class="hljs-keyword">return</span> -<span class="hljs-number">1</span>;
                    }
                </code></pre>
                
            * 从尾至头遍历链表，找到目标元素值为o的节点
            
                <pre class="hljs java"><code class="java">    <span class="hljs-function"><span class="hljs-keyword">public</span> <span class="hljs-keyword">int</span> <span class="hljs-title">lastIndexOf</span><span class="hljs-params">(Object o)</span> </span>{
                        <span class="hljs-keyword">int</span> index = size;
                        <span class="hljs-keyword">if</span> (o == <span class="hljs-keyword">null</span>) {
                            <span class="hljs-keyword">for</span> (Node&lt;E&gt; x = last; x != <span class="hljs-keyword">null</span>; x = x.prev) {
                                index--;
                                <span class="hljs-keyword">if</span> (x.item == <span class="hljs-keyword">null</span>)
                                    <span class="hljs-keyword">return</span> index;
                            }
                        } <span class="hljs-keyword">else</span> {
                            <span class="hljs-keyword">for</span> (Node&lt;E&gt; x = last; x != <span class="hljs-keyword">null</span>; x = x.prev) {
                                index--;
                                <span class="hljs-keyword">if</span> (o.equals(x.item))
                                    <span class="hljs-keyword">return</span> index;
                            }
                        }
                        <span class="hljs-keyword">return</span> -<span class="hljs-number">1</span>;
                    }
                </code></pre>
              
            > 查不修改modCount
          
            * toArray()
            <br/>
            <br/>
            <pre class="hljs javascript"><code class="javascript">    public <span class="hljs-built_in">Object</span>[] toArray() {
                    <span class="hljs-comment">//new 一个新数组 然后遍历链表，将每个元素存在数组里，返回</span>
                    <span class="hljs-built_in">Object</span>[] result = <span class="hljs-keyword">new</span> <span class="hljs-built_in">Object</span>[size];
                    int i = <span class="hljs-number">0</span>;
                    <span class="hljs-keyword">for</span> (Node&lt;E&gt; x = first; x != <span class="hljs-literal">null</span>; x = x.next)
                        result[i++] = x.item;
                    <span class="hljs-keyword">return</span> result;
                }
            </code></pre>
            
            <h2>总结：</h2>
            <p>LinkedList 是双向列表。</p>
            <ul>
            <li><p>链表批量增加，是<strong>靠for循环遍历原数组，依次执行插入节点操作</strong>。对比ArrayList是通过System.arraycopy完成批量增加的。增加一定会修改modCount。</p></li>
            <li><p>通过下标获取某个node 的时候，（add select），<strong>会根据index处于前半段还是后半段 进行一个折半</strong>，以<strong>提升查询效率</strong></p></li>
            <li><p>删也一定会修改modCount。 按下标删，也是先根据index找到Node，然后去链表上unlink掉这个Node。 按元素删，会先去遍历链表寻找是否有该Node，考虑到允许null值，所以会遍历两遍，然后再去unlink它。</p></li>
            <li><p>改也是先根据index找到Node，然后替换值。改不修改modCount。</p></li>
            <li><p>查本身就是根据index找到Node。</p></li>
            <li><p>所以它的CRUD操作里，都设计到根据index去找到Node的操作。</p></li>
            </ul>
            
             [参考：LinkedList源码解析（JDK8）](https://www.jianshu.com/p/e69557b217c0)
   * set
    
     > 思路：Set -> HashSet -> LinkedHashSet -> 面试相关
     
     * set
         
        <div>
            <img src="https://upload-images.jianshu.io/upload_images/1819960-6eb6c0b399590d96.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/700" />
        </div> 
        
        特点： 
        
        Set 不允许存储重复元素，允许存储 null
        
        HashSet 底层是数组 + 单链表 + 红黑树的数据结构
        
        HashSet 存储元素是无序且不等于访问顺序
        
        LinkedHashSet 底层是 数组 + 单链表 + 红黑树 + 双向链表的数据结构
        
        LinkedHashSet 存储元素是无序的，但是由于双向链表的存在，迭代时获取元素的顺序等于元素的添加顺序，注意这里不是访问顺序
        
        * HashSet源码分析   
            
            > 思路：构造方法 -> API(增、删、改、查) 
        
          * 依赖于 HashMap，这一点充分体现在其构造方法和成员变量上。我们来看下 HashSet 的构造方法和成员变量：
            <br/>
            <br/>
            <pre class="hljs cpp"><code class="cpp"> <span class="hljs-comment">// HashSet 真实的存储元素结构</span>
             <span class="hljs-keyword">private</span> transient HashMap&lt;E,Object&gt; <span class="hljs-built_in">map</span>;
            
             <span class="hljs-comment">// 作为各个存储在 HashMap 元素的键值对中的 Value</span>
             <span class="hljs-keyword">private</span> <span class="hljs-keyword">static</span> final Object PRESENT = <span class="hljs-keyword">new</span> Object();
                
             <span class="hljs-comment">//空参数构造方法 调用 HashMap 的空构造参数  </span>
             <span class="hljs-comment">//初始化了 HashMap 中的加载因子 loadFactor = 0.75f</span>
             <span class="hljs-function"><span class="hljs-keyword">public</span> <span class="hljs-title">HashSet</span><span class="hljs-params">()</span> </span>{
                    <span class="hljs-built_in">map</span> = <span class="hljs-keyword">new</span> HashMap&lt;&gt;();
             }
             
             <span class="hljs-comment">//指定期望容量的构造方法</span>
             <span class="hljs-function"><span class="hljs-keyword">public</span> <span class="hljs-title">HashSet</span><span class="hljs-params">(<span class="hljs-keyword">int</span> initialCapacity)</span> </span>{
                <span class="hljs-built_in">map</span> = <span class="hljs-keyword">new</span> HashMap&lt;&gt;(initialCapacity);
             }
             <span class="hljs-comment">//指定期望容量和加载因子</span>
             <span class="hljs-function"><span class="hljs-keyword">public</span> <span class="hljs-title">HashSet</span><span class="hljs-params">(<span class="hljs-keyword">int</span> initialCapacity, <span class="hljs-keyword">float</span> loadFactor)</span> </span>{
                <span class="hljs-built_in">map</span> = <span class="hljs-keyword">new</span> HashMap&lt;&gt;(initialCapacity, loadFactor);
             }
             <span class="hljs-comment">//使用指定的集合填充Set</span>
             <span class="hljs-function"><span class="hljs-keyword">public</span> <span class="hljs-title">HashSet</span><span class="hljs-params">(Collection&lt;? extends E&gt; c)</span> </span>{
                    <span class="hljs-comment">//调用  new HashMap&lt;&gt;(initialCapacity) 其中初始期望容量为 16 和 c 容量 / 默认 load factor 后 + 1的较大值</span>
                    <span class="hljs-built_in">map</span> = <span class="hljs-keyword">new</span> HashMap&lt;&gt;(Math.max((<span class="hljs-keyword">int</span>) (c.size()/<span class="hljs-number">.75</span>f) + <span class="hljs-number">1</span>, <span class="hljs-number">16</span>));
                    addAll(c);
             }
            
             <span class="hljs-comment">// 该方法为 default 访问权限，不允许使用者直接调用，目的是为了初始化 LinkedHashSet 时使用</span>
             HashSet(<span class="hljs-keyword">int</span> initialCapacity, <span class="hljs-keyword">float</span> loadFactor, boolean dummy) {
                    <span class="hljs-built_in">map</span> = <span class="hljs-keyword">new</span> LinkedHashMap&lt;&gt;(initialCapacity, loadFactor);
             }
            </code></pre>
            
            总结 ：
            
             通过 HashSet 的构造参数我们可以看出每个构造方法，都调用了对应的 HashMap 的构造方法用来初始化成员变量 map ，因此我们可以知道，HashSet 的初始容量也为 1<<4 即16，加载因子默认也是 0.75f。
            
             我们都知道 Set 不允许存储重复元素，又由构造参数得出结论底层存储结构为 HashMap,那么这个不可重复的属性必然是有 HashMap 中存储键值对的 Key 来实现了。在分析 HashMap 的时候，提到过 HashMap 通过存储键值对的 Key 的 hash 值（经过扰动函数hash()处理后）来决定键值对在哈希表中的位置，当 Key 的 hash 值相同时，再通过 equals 方法判读是否是替换原来对应 key 的 Value 还是存储新的键值对。那么我们在使用 Set 方法的时候也必须保证，存储元素的 HashCode 方法以及 equals 方法被正确覆写。
           
          * 增
            
            <pre class="hljs java"><code class="java"><span class="hljs-function"><span class="hljs-keyword">public</span> <span class="hljs-keyword">boolean</span> <span class="hljs-title">add</span><span class="hljs-params">(E e)</span> </span>{
                <span class="hljs-keyword">return</span> map.put(e, PRESENT)==<span class="hljs-keyword">null</span>;
            }
            </code></pre>
            
            可以看出 add 方法调用了 HashMap 的 put 方法，构造的键值对的 key 为待添加的元素，而 Value 这时有全局变量 PRESENT 来充当，这个PRESENT只是一个 Object 对象。
            
          * 删
          
          * 改
          
          * 查
          
          实现set之后的方法：
          
          <pre class="hljs cpp"><code class="cpp"><span class="hljs-function"><span class="hljs-keyword">public</span> <span class="hljs-keyword">int</span> <span class="hljs-title">size</span><span class="hljs-params">()</span> </span>{
                  <span class="hljs-keyword">return</span> <span class="hljs-built_in">map</span>.size();
          }
          
          <span class="hljs-function"><span class="hljs-keyword">public</span> boolean <span class="hljs-title">isEmpty</span><span class="hljs-params">()</span> </span>{
             <span class="hljs-keyword">return</span> <span class="hljs-built_in">map</span>.isEmpty();
          }
          
          <span class="hljs-function"><span class="hljs-keyword">public</span> boolean <span class="hljs-title">contains</span><span class="hljs-params">(Object o)</span> </span>{
             <span class="hljs-keyword">return</span> <span class="hljs-built_in">map</span>.containsKey(o);
          }
          
          <span class="hljs-comment">//调用 remove(Object key)  方法去移除对应的键值对</span>
          <span class="hljs-function"><span class="hljs-keyword">public</span> boolean <span class="hljs-title">remove</span><span class="hljs-params">(Object o)</span> </span>{
             <span class="hljs-keyword">return</span> <span class="hljs-built_in">map</span>.remove(o)==PRESENT;
          }
          
          <span class="hljs-function"><span class="hljs-keyword">public</span> <span class="hljs-keyword">void</span> <span class="hljs-title">clear</span><span class="hljs-params">()</span> </span>{
             <span class="hljs-built_in">map</span>.clear();
          }
          
          <span class="hljs-comment">// 返回一个 map.keySet 的 HashIterator 来作为 Set 的迭代器</span>
          <span class="hljs-keyword">public</span> Iterator&lt;E&gt; iterator() {
             <span class="hljs-keyword">return</span> <span class="hljs-built_in">map</span>.keySet().iterator();
          }
          </code></pre>
          
          关于迭代器我们在讲解 HashMap 中的时候没有详细列举，其实 HashMap 提供了多种迭代方法，每个方法对应了一种迭代器，这些迭代器包括下述几种，而 HashSet 由于只关注 Key 的内容，所以使用 HashMap 的内部类 KeySet 返回了一个 KeyIterator ，这样在调用 next 方法的时候就可以直接获取下个节点的 key 了。
          
          <pre class="hljs java"><code class="java"><span class="hljs-comment">//HashMap 中的迭代器</span>
          
          <span class="hljs-keyword">final</span> <span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">KeyIterator</span> <span class="hljs-keyword">extends</span> <span class="hljs-title">HashIterator</span>
             <span class="hljs-keyword">implements</span> <span class="hljs-title">Iterator</span>&lt;<span class="hljs-title">K</span>&gt; </span>{
             <span class="hljs-function"><span class="hljs-keyword">public</span> <span class="hljs-keyword">final</span> K <span class="hljs-title">next</span><span class="hljs-params">()</span> </span>{ <span class="hljs-keyword">return</span> nextNode().key; }
          }
          
          <span class="hljs-keyword">final</span> <span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">ValueIterator</span> <span class="hljs-keyword">extends</span> <span class="hljs-title">HashIterator</span>
             <span class="hljs-keyword">implements</span> <span class="hljs-title">Iterator</span>&lt;<span class="hljs-title">V</span>&gt; </span>{
             <span class="hljs-function"><span class="hljs-keyword">public</span> <span class="hljs-keyword">final</span> V <span class="hljs-title">next</span><span class="hljs-params">()</span> </span>{ <span class="hljs-keyword">return</span> nextNode().value; }
          }
          
          <span class="hljs-keyword">final</span> <span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">EntryIterator</span> <span class="hljs-keyword">extends</span> <span class="hljs-title">HashIterator</span>
             <span class="hljs-keyword">implements</span> <span class="hljs-title">Iterator</span>&lt;<span class="hljs-title">Map</span>.<span class="hljs-title">Entry</span>&lt;<span class="hljs-title">K</span>,<span class="hljs-title">V</span>&gt;&gt; </span>{
             <span class="hljs-keyword">public</span> <span class="hljs-keyword">final</span> Map.<span class="hljs-function">Entry&lt;K,V&gt; <span class="hljs-title">next</span><span class="hljs-params">()</span> </span>{ <span class="hljs-keyword">return</span> nextNode(); }
          }
          
          </code></pre>
          
        * LinkedHashSet     
        
            > 思路： 概括 -> 构造方法 -> API(调用)
            
            概括： LinkedHashSet 由于继承自 HashSet
            
            * 构造方法： 
                
                在上述分析 HashSet 构造方法的时候，有一个 default 权限的构造方法没有讲，只说了其跟 LinkedHashSet 构造有关系，该构造方法内部调用的是 LinkedHashMap 的构造方法。
                
                LinkedHashMap 较之 HashMap 内部多维护了一个双向链表用来维护元素的添加顺序：
                
                <pre class="hljs java"><code class="java"><span class="hljs-comment">// dummy 参数没有作用这里可以忽略</span>
                HashSet(<span class="hljs-keyword">int</span> initialCapacity, <span class="hljs-keyword">float</span> loadFactor, <span class="hljs-keyword">boolean</span> dummy) {
                   map = <span class="hljs-keyword">new</span> LinkedHashMap&lt;&gt;(initialCapacity, loadFactor);
                }
                
                <span class="hljs-comment">//调用 LinkedHashMap 的构造方法，该方法初始化了初始起始容量，以及加载因子，</span>
                <span class="hljs-comment">//accessOrder = false 即迭代顺序不等于访问顺序</span>
                <span class="hljs-function"><span class="hljs-keyword">public</span> <span class="hljs-title">LinkedHashMap</span><span class="hljs-params">(<span class="hljs-keyword">int</span> initialCapacity, <span class="hljs-keyword">float</span> loadFactor)</span> </span>{
                        <span class="hljs-keyword">super</span>(initialCapacity, loadFactor);
                        accessOrder = <span class="hljs-keyword">false</span>;
                }
                
                </code></pre>
            
               LinkedHashSet的构造方法一共有四个，统一调用了父类的 HashSet(int initialCapacity, float loadFactor, boolean dummy)构造方法。
               
               <pre class="hljs java"><code class="java"><span class="hljs-comment">//初始化 LinkedHashMap 的初始容量为诶 16 加载因子为 0.75f</span>
               <span class="hljs-function"><span class="hljs-keyword">public</span> <span class="hljs-title">LinkedHashSet</span><span class="hljs-params">()</span> </span>{
                  <span class="hljs-keyword">super</span>(<span class="hljs-number">16</span>, .<span class="hljs-number">75f</span>, <span class="hljs-keyword">true</span>);
               }
               
               <span class="hljs-comment">//初始化 LinkedHashMap 的初始容量为 Math.max(2*c.size(), 11) 加载因子为 0.75f </span>
               <span class="hljs-function"><span class="hljs-keyword">public</span> <span class="hljs-title">LinkedHashSet</span><span class="hljs-params">(Collection&lt;? extends E&gt; c)</span> </span>{
                  <span class="hljs-keyword">super</span>(Math.max(<span class="hljs-number">2</span>*c.size(), <span class="hljs-number">11</span>), .<span class="hljs-number">75f</span>, <span class="hljs-keyword">true</span>);
                  addAll(c);
               }
               
               <span class="hljs-comment">//初始化 LinkedHashMap 的初始容量为参数指定值 加载因子为 0.75f </span>
               <span class="hljs-function"><span class="hljs-keyword">public</span> <span class="hljs-title">LinkedHashSet</span><span class="hljs-params">(<span class="hljs-keyword">int</span> initialCapacity)</span> </span>{
                  <span class="hljs-keyword">super</span>(initialCapacity, .<span class="hljs-number">75f</span>, <span class="hljs-keyword">true</span>);
               }
                
                <span class="hljs-comment">//初始化 LinkedHashMap 的初始容量,加载因子为参数指定值 </span>
                <span class="hljs-function"><span class="hljs-keyword">public</span> <span class="hljs-title">LinkedHashSet</span><span class="hljs-params">(<span class="hljs-keyword">int</span> initialCapacity, <span class="hljs-keyword">float</span> loadFactor)</span> </span>{
                  <span class="hljs-keyword">super</span>(initialCapacity, loadFactor, <span class="hljs-keyword">true</span>);
               }
               </code></pre>
            
       [参考：搞懂 HashSet & LinkedHashSet 源码 以及集合常见面试题目](https://www.jianshu.com/p/99ad883041d6)
   
   * map：
        
        * HashMap源码解析
            
            > 思路：1、构造方法 2、常用API(增、删、改、查)
            
            * 概括
                
                * 概括的说，HashMap 是一个关联数组、哈希表，它是线程不安全的，允许key为null,value为null。遍历时无序。
                  其底层数据结构是数组称之为哈希桶，每个桶里面放的是链表，链表中的每个节点，就是哈希表中的每个元素。
                  在JDK8中，当链表长度达到8，会转化成红黑树，以提升它的查询、插入效率，它实现了Map<K,V>, Cloneable, Serializable接口。
                  
                  <p>因其底层哈希桶的数据结构是数组，所以也会涉及到扩容的问题。</p>
                  
                   <p>当HashMap的容量达到threshold域值时，就会触发扩容。扩容前后，哈希桶的长度一定会是2的次方。
                  这样在根据key的hash值寻找对应的哈希桶时，可以用位运算替代取余操作，更加高效。 </p>
                  
                   <p>而key的hash值，并不仅仅只是key对象的hashCode()方法的返回值，还会经过扰动函数的扰动，以使hash值更加均衡。
                  因为hashCode()是int类型，取值范围是40多亿，只要哈希函数映射的比较均匀松散，碰撞几率是很小的。
                  但就算原本的hashCode()取得很好，每个key的hashCode()不同，但是由于HashMap的哈希桶的长度远比hash取值范围小，默认是16，所以当对hash值以桶的长度取余，以找到存放该key的桶的下标时，由于取余是通过与操作完成的，会忽略hash值的高位。因此只有hashCode()的低位参加运算，发生不同的hash值，但是得到的index相同的情况的几率会大大增加，这种情况称之为hash碰撞。 即，碰撞率会增大。 </p>
                  
                   <p>扰动函数就是为了解决hash碰撞的。它会综合hash值高位和低位的特征，并存放在低位，因此在与运算时，相当于高低位一起参与了运算，以减少hash碰撞的概率。（在JDK8之前，扰动函数会扰动四次，JDK8简化了这个操作） </p>
                  
                   <p>扩容操作时，会new一个新的Node数组作为哈希桶，然后将原哈希表中的所有数据(Node节点)移动到新的哈希桶中，相当于对原哈希表中所有的数据重新做了一个put操作。所以性能消耗很大，可想而知，在哈希表的容量越大时，性能消耗越明显。 </p>
                  
                   <p>扩容时，如果发生过哈希碰撞，节点数小于8个。则要根据链表上每个节点的哈希值，依次放入新哈希桶对应下标位置。
                  因为扩容是容量翻倍，所以原链表上的每个节点，现在可能存放在原来的下标，即low位， 或者扩容后的下标，即high位。 high位= low位+原哈希桶容量
                  如果追加节点后，链表数量》=8，则转化为红黑树 </p>
                  
                   <p>由迭代器的实现可以看出，遍历HashMap时，顺序是按照哈希桶从低到高，链表从前往后，依次遍历的。属于无序集合。 </p>
                  
                   <p>整个HashMap示意图：图片来源于网络，侵删： </p> 
                  
                  <div> 
                      <img src="https://upload-images.jianshu.io/upload_images/1696338-1529a68fefebc912?imageMogr2/auto-orient/strip%7CimageView2/2/w/700" />
                  </div>
                  
                  HashMap的源码中，充斥个各种位运算代替常规运算的地方，以提升效率：
                  
                  与运算替代模运算。用 hash & (table.length-1) 替代 hash % (table.length)
                  用if ((e.hash & oldCap) == 0)判断扩容后，节点e处于低区还是高区。
                  
            * 链表节点Node
            
                * 在开始之前，我们先看一下挂载在哈希表上的元素，链表的结构：
                
                    <pre class="hljs java"><code class="java">    <span class="hljs-keyword">static</span> <span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">Node</span>&lt;<span class="hljs-title">K</span>,<span class="hljs-title">V</span>&gt; <span class="hljs-keyword">implements</span> <span class="hljs-title">Map</span>.<span class="hljs-title">Entry</span>&lt;<span class="hljs-title">K</span>,<span class="hljs-title">V</span>&gt; </span>{
                            <span class="hljs-keyword">final</span> <span class="hljs-keyword">int</span> hash;<span class="hljs-comment">//哈希值</span>
                            <span class="hljs-keyword">final</span> K key;<span class="hljs-comment">//key</span>
                            V value;<span class="hljs-comment">//value</span>
                            Node&lt;K,V&gt; next;<span class="hljs-comment">//链表后置节点</span>
                    
                            Node(<span class="hljs-keyword">int</span> hash, K key, V value, Node&lt;K,V&gt; next) {
                                <span class="hljs-keyword">this</span>.hash = hash;
                                <span class="hljs-keyword">this</span>.key = key;
                                <span class="hljs-keyword">this</span>.value = value;
                                <span class="hljs-keyword">this</span>.next = next;
                            }
                    
                            <span class="hljs-function"><span class="hljs-keyword">public</span> <span class="hljs-keyword">final</span> K <span class="hljs-title">getKey</span><span class="hljs-params">()</span>        </span>{ <span class="hljs-keyword">return</span> key; }
                            <span class="hljs-function"><span class="hljs-keyword">public</span> <span class="hljs-keyword">final</span> V <span class="hljs-title">getValue</span><span class="hljs-params">()</span>      </span>{ <span class="hljs-keyword">return</span> value; }
                            <span class="hljs-function"><span class="hljs-keyword">public</span> <span class="hljs-keyword">final</span> String <span class="hljs-title">toString</span><span class="hljs-params">()</span> </span>{ <span class="hljs-keyword">return</span> key + <span class="hljs-string">"="</span> + value; }
                    
                            <span class="hljs-comment">//每一个节点的hash值，是将key的hashCode 和 value的hashCode 亦或得到的。</span>
                            <span class="hljs-function"><span class="hljs-keyword">public</span> <span class="hljs-keyword">final</span> <span class="hljs-keyword">int</span> <span class="hljs-title">hashCode</span><span class="hljs-params">()</span> </span>{
                                <span class="hljs-keyword">return</span> Objects.hashCode(key) ^ Objects.hashCode(value);
                            }
                            <span class="hljs-comment">//设置新的value 同时返回旧value</span>
                            <span class="hljs-function"><span class="hljs-keyword">public</span> <span class="hljs-keyword">final</span> V <span class="hljs-title">setValue</span><span class="hljs-params">(V newValue)</span> </span>{
                                V oldValue = value;
                                value = newValue;
                                <span class="hljs-keyword">return</span> oldValue;
                            }
                            
                            <span class="hljs-function"><span class="hljs-keyword">public</span> <span class="hljs-keyword">final</span> <span class="hljs-keyword">boolean</span> <span class="hljs-title">equals</span><span class="hljs-params">(Object o)</span> </span>{
                                <span class="hljs-keyword">if</span> (o == <span class="hljs-keyword">this</span>)
                                    <span class="hljs-keyword">return</span> <span class="hljs-keyword">true</span>;
                                <span class="hljs-keyword">if</span> (o <span class="hljs-keyword">instanceof</span> Map.Entry) {
                                    Map.Entry&lt;?,?&gt; e = (Map.Entry&lt;?,?&gt;)o;
                                    <span class="hljs-keyword">if</span> (Objects.equals(key, e.getKey()) &amp;&amp;
                                        Objects.equals(value, e.getValue()))
                                        <span class="hljs-keyword">return</span> <span class="hljs-keyword">true</span>;
                                }
                                <span class="hljs-keyword">return</span> <span class="hljs-keyword">false</span>;
                            }
                        }
                        
                    </code></pre>
                    
                    <p>由此可知，这是一个单链表~。
                       每一个节点的hash值，是将key的hashCode 和 value的hashCode 亦或得到的。</P>
                       
            * 构造函数 
            
                <pre class="hljs java"><code class="java">    <span class="hljs-comment">//最大容量 2的30次方</span>
                    <span class="hljs-keyword">static</span> <span class="hljs-keyword">final</span> <span class="hljs-keyword">int</span> MAXIMUM_CAPACITY = <span class="hljs-number">1</span> &lt;&lt; <span class="hljs-number">30</span>;
                    <span class="hljs-comment">//默认的加载因子</span>
                    <span class="hljs-keyword">static</span> <span class="hljs-keyword">final</span> <span class="hljs-keyword">float</span> DEFAULT_LOAD_FACTOR = <span class="hljs-number">0.75f</span>;
                    
                    <span class="hljs-comment">//哈希桶，存放链表。 长度是2的N次方，或者初始化时为0.</span>
                    <span class="hljs-keyword">transient</span> Node&lt;K,V&gt;[] table;
                        
                    <span class="hljs-comment">//加载因子，用于计算哈希表元素数量的阈值。  threshold = 哈希桶.length * loadFactor;</span>
                    <span class="hljs-keyword">final</span> <span class="hljs-keyword">float</span> loadFactor;
                    <span class="hljs-comment">//哈希表内元素数量的阈值，当哈希表内元素数量超过阈值时，会发生扩容resize()。</span>
                    <span class="hljs-keyword">int</span> threshold;
                
                    <span class="hljs-function"><span class="hljs-keyword">public</span> <span class="hljs-title">HashMap</span><span class="hljs-params">()</span> </span>{
                        <span class="hljs-comment">//默认构造函数，赋值加载因子为默认的0.75f</span>
                        <span class="hljs-keyword">this</span>.loadFactor = DEFAULT_LOAD_FACTOR; <span class="hljs-comment">// all other fields defaulted</span>
                    }
                    <span class="hljs-function"><span class="hljs-keyword">public</span> <span class="hljs-title">HashMap</span><span class="hljs-params">(<span class="hljs-keyword">int</span> initialCapacity)</span> </span>{
                        <span class="hljs-comment">//指定初始化容量的构造函数</span>
                        <span class="hljs-keyword">this</span>(initialCapacity, DEFAULT_LOAD_FACTOR);
                    }
                    <span class="hljs-comment">//同时指定初始化容量 以及 加载因子， 用的很少，一般不会修改loadFactor</span>
                    <span class="hljs-function"><span class="hljs-keyword">public</span> <span class="hljs-title">HashMap</span><span class="hljs-params">(<span class="hljs-keyword">int</span> initialCapacity, <span class="hljs-keyword">float</span> loadFactor)</span> </span>{
                        <span class="hljs-comment">//边界处理</span>
                        <span class="hljs-keyword">if</span> (initialCapacity &lt; <span class="hljs-number">0</span>)
                            <span class="hljs-keyword">throw</span> <span class="hljs-keyword">new</span> IllegalArgumentException(<span class="hljs-string">"Illegal initial capacity: "</span> +
                                                               initialCapacity);
                        <span class="hljs-comment">//初始容量最大不能超过2的30次方</span>
                        <span class="hljs-keyword">if</span> (initialCapacity &gt; MAXIMUM_CAPACITY)
                            initialCapacity = MAXIMUM_CAPACITY;
                        <span class="hljs-comment">//显然加载因子不能为负数</span>
                        <span class="hljs-keyword">if</span> (loadFactor &lt;= <span class="hljs-number">0</span> || Float.isNaN(loadFactor))
                            <span class="hljs-keyword">throw</span> <span class="hljs-keyword">new</span> IllegalArgumentException(<span class="hljs-string">"Illegal load factor: "</span> +
                                                               loadFactor);
                        <span class="hljs-keyword">this</span>.loadFactor = loadFactor;
                        <span class="hljs-comment">//设置阈值为  》=初始化容量的 2的n次方的值</span>
                        <span class="hljs-keyword">this</span>.threshold = tableSizeFor(initialCapacity);
                    }
                    <span class="hljs-comment">//新建一个哈希表，同时将另一个map m 里的所有元素加入表中</span>
                    <span class="hljs-function"><span class="hljs-keyword">public</span> <span class="hljs-title">HashMap</span><span class="hljs-params">(Map&lt;? extends K, ? extends V&gt; m)</span> </span>{
                        <span class="hljs-keyword">this</span>.loadFactor = DEFAULT_LOAD_FACTOR;
                        putMapEntries(m, <span class="hljs-keyword">false</span>);
                    }
                    
                </code></pre>     
                
                <pre class="hljs java"><code class="java">    <span class="hljs-comment">//根据期望容量cap，返回2的n次方形式的 哈希桶的实际容量 length。 返回值一般会&gt;=cap </span>
                    <span class="hljs-function"><span class="hljs-keyword">static</span> <span class="hljs-keyword">final</span> <span class="hljs-keyword">int</span> <span class="hljs-title">tableSizeFor</span><span class="hljs-params">(<span class="hljs-keyword">int</span> cap)</span> </span>{
                    <span class="hljs-comment">//经过下面的 或 和位移 运算， n最终各位都是1。</span>
                        <span class="hljs-keyword">int</span> n = cap - <span class="hljs-number">1</span>;
                        n |= n &gt;&gt;&gt; <span class="hljs-number">1</span>;
                        n |= n &gt;&gt;&gt; <span class="hljs-number">2</span>;
                        n |= n &gt;&gt;&gt; <span class="hljs-number">4</span>;
                        n |= n &gt;&gt;&gt; <span class="hljs-number">8</span>;
                        n |= n &gt;&gt;&gt; <span class="hljs-number">16</span>;
                        <span class="hljs-comment">//判断n是否越界，返回 2的n次方作为 table（哈希桶）的阈值</span>
                        <span class="hljs-keyword">return</span> (n &lt; <span class="hljs-number">0</span>) ? <span class="hljs-number">1</span> : (n &gt;= MAXIMUM_CAPACITY) ? MAXIMUM_CAPACITY : n + <span class="hljs-number">1</span>;
                    }
                </code></pre>
                
                <pre class="hljs java"><code class="java">    <span class="hljs-comment">//将另一个Map的所有元素加入表中，参数evict初始化时为false，其他情况为true</span>
                    <span class="hljs-function"><span class="hljs-keyword">final</span> <span class="hljs-keyword">void</span> <span class="hljs-title">putMapEntries</span><span class="hljs-params">(Map&lt;? extends K, ? extends V&gt; m, <span class="hljs-keyword">boolean</span> evict)</span> </span>{
                        <span class="hljs-comment">//拿到m的元素数量</span>
                        <span class="hljs-keyword">int</span> s = m.size();
                        <span class="hljs-comment">//如果数量大于0</span>
                        <span class="hljs-keyword">if</span> (s &gt; <span class="hljs-number">0</span>) {
                            <span class="hljs-comment">//如果当前表是空的</span>
                            <span class="hljs-keyword">if</span> (table == <span class="hljs-keyword">null</span>) { <span class="hljs-comment">// pre-size</span>
                                <span class="hljs-comment">//根据m的元素数量和当前表的加载因子，计算出阈值</span>
                                <span class="hljs-keyword">float</span> ft = ((<span class="hljs-keyword">float</span>)s / loadFactor) + <span class="hljs-number">1.0F</span>;
                                <span class="hljs-comment">//修正阈值的边界 不能超过MAXIMUM_CAPACITY</span>
                                <span class="hljs-keyword">int</span> t = ((ft &lt; (<span class="hljs-keyword">float</span>)MAXIMUM_CAPACITY) ?
                                         (<span class="hljs-keyword">int</span>)ft : MAXIMUM_CAPACITY);
                                <span class="hljs-comment">//如果新的阈值大于当前阈值</span>
                                <span class="hljs-keyword">if</span> (t &gt; threshold)
                                    <span class="hljs-comment">//返回一个 》=新的阈值的 满足2的n次方的阈值</span>
                                    threshold = tableSizeFor(t);
                            }
                            <span class="hljs-comment">//如果当前元素表不是空的，但是 m的元素数量大于阈值，说明一定要扩容。</span>
                            <span class="hljs-keyword">else</span> <span class="hljs-keyword">if</span> (s &gt; threshold)
                                resize();
                            <span class="hljs-comment">//遍历 m 依次将元素加入当前表中。</span>
                            <span class="hljs-keyword">for</span> (Map.Entry&lt;? extends K, ? extends V&gt; e : m.entrySet()) {
                                K key = e.getKey();
                                V value = e.getValue();
                                putVal(hash(key), key, value, <span class="hljs-keyword">false</span>, evict);
                            }
                        }
                    }
                </code></pre>
                
                <p>先看一下扩容函数： 这是一个重点！重点！重点！
                   初始化或加倍哈希桶大小。如果是当前哈希桶是null,分配符合当前阈值的初始容量目标。
                   否则，因为我们扩容成以前的两倍。
                   在扩容时，要注意区分以前在哈希桶相同index的节点，现在是在以前的index里，还是index+oldlength 里
                   
                <pre class="hljs java"><code class="java"><span class="hljs-keyword">final</span> Node&lt;K,V&gt;[] resize() {
                           <span class="hljs-comment">//oldTab 为当前表的哈希桶</span>
                           Node&lt;K,V&gt;[] oldTab = table;
                           <span class="hljs-comment">//当前哈希桶的容量 length</span>
                           <span class="hljs-keyword">int</span> oldCap = (oldTab == <span class="hljs-keyword">null</span>) ? <span class="hljs-number">0</span> : oldTab.length;
                           <span class="hljs-comment">//当前的阈值</span>
                           <span class="hljs-keyword">int</span> oldThr = threshold;
                           <span class="hljs-comment">//初始化新的容量和阈值为0</span>
                           <span class="hljs-keyword">int</span> newCap, newThr = <span class="hljs-number">0</span>;
                           <span class="hljs-comment">//如果当前容量大于0</span>
                           <span class="hljs-keyword">if</span> (oldCap &gt; <span class="hljs-number">0</span>) {
                               <span class="hljs-comment">//如果当前容量已经到达上限</span>
                               <span class="hljs-keyword">if</span> (oldCap &gt;= MAXIMUM_CAPACITY) {
                                   <span class="hljs-comment">//则设置阈值是2的31次方-1</span>
                                   threshold = Integer.MAX_VALUE;
                                   <span class="hljs-comment">//同时返回当前的哈希桶，不再扩容</span>
                                   <span class="hljs-keyword">return</span> oldTab;
                               }<span class="hljs-comment">//否则新的容量为旧的容量的两倍。 </span>
                               <span class="hljs-keyword">else</span> <span class="hljs-keyword">if</span> ((newCap = oldCap &lt;&lt; <span class="hljs-number">1</span>) &lt; MAXIMUM_CAPACITY &amp;&amp;
                                        oldCap &gt;= DEFAULT_INITIAL_CAPACITY)<span class="hljs-comment">//如果旧的容量大于等于默认初始容量16</span>
                                   <span class="hljs-comment">//那么新的阈值也等于旧的阈值的两倍</span>
                                   newThr = oldThr &lt;&lt; <span class="hljs-number">1</span>; <span class="hljs-comment">// double threshold</span>
                           }<span class="hljs-comment">//如果当前表是空的，但是有阈值。代表是初始化时指定了容量、阈值的情况</span>
                           <span class="hljs-keyword">else</span> <span class="hljs-keyword">if</span> (oldThr &gt; <span class="hljs-number">0</span>) <span class="hljs-comment">// initial capacity was placed in threshold</span>
                               newCap = oldThr;<span class="hljs-comment">//那么新表的容量就等于旧的阈值</span>
                           <span class="hljs-keyword">else</span> {}<span class="hljs-comment">//如果当前表是空的，而且也没有阈值。代表是初始化时没有任何容量/阈值参数的情况               // zero initial threshold signifies using defaults</span>
                               newCap = DEFAULT_INITIAL_CAPACITY;<span class="hljs-comment">//此时新表的容量为默认的容量 16</span>
                               newThr = (<span class="hljs-keyword">int</span>)(DEFAULT_LOAD_FACTOR * DEFAULT_INITIAL_CAPACITY);<span class="hljs-comment">//新的阈值为默认容量16 * 默认加载因子0.75f = 12</span>
                           }
                           <span class="hljs-keyword">if</span> (newThr == <span class="hljs-number">0</span>) {<span class="hljs-comment">//如果新的阈值是0，对应的是  当前表是空的，但是有阈值的情况</span>
                               <span class="hljs-keyword">float</span> ft = (<span class="hljs-keyword">float</span>)newCap * loadFactor;<span class="hljs-comment">//根据新表容量 和 加载因子 求出新的阈值</span>
                               <span class="hljs-comment">//进行越界修复</span>
                               newThr = (newCap &lt; MAXIMUM_CAPACITY &amp;&amp; ft &lt; (<span class="hljs-keyword">float</span>)MAXIMUM_CAPACITY ?
                                         (<span class="hljs-keyword">int</span>)ft : Integer.MAX_VALUE);
                           }
                           <span class="hljs-comment">//更新阈值 </span>
                           threshold = newThr;
                           <span class="hljs-meta">@SuppressWarnings</span>({<span class="hljs-string">"rawtypes"</span>,<span class="hljs-string">"unchecked"</span>})
                           <span class="hljs-comment">//根据新的容量 构建新的哈希桶</span>
                               Node&lt;K,V&gt;[] newTab = (Node&lt;K,V&gt;[])<span class="hljs-keyword">new</span> Node[newCap];
                           <span class="hljs-comment">//更新哈希桶引用</span>
                           table = newTab;
                           <span class="hljs-comment">//如果以前的哈希桶中有元素</span>
                           <span class="hljs-comment">//下面开始将当前哈希桶中的所有节点转移到新的哈希桶中</span>
                           <span class="hljs-keyword">if</span> (oldTab != <span class="hljs-keyword">null</span>) {
                               <span class="hljs-comment">//遍历老的哈希桶</span>
                               <span class="hljs-keyword">for</span> (<span class="hljs-keyword">int</span> j = <span class="hljs-number">0</span>; j &lt; oldCap; ++j) {
                                   <span class="hljs-comment">//取出当前的节点 e</span>
                                   Node&lt;K,V&gt; e;
                                   <span class="hljs-comment">//如果当前桶中有元素,则将链表赋值给e</span>
                                   <span class="hljs-keyword">if</span> ((e = oldTab[j]) != <span class="hljs-keyword">null</span>) {
                                       <span class="hljs-comment">//将原哈希桶置空以便GC</span>
                                       oldTab[j] = <span class="hljs-keyword">null</span>;
                                       <span class="hljs-comment">//如果当前链表中就一个元素，（没有发生哈希碰撞）</span>
                                       <span class="hljs-keyword">if</span> (e.next == <span class="hljs-keyword">null</span>)
                                           <span class="hljs-comment">//直接将这个元素放置在新的哈希桶里。</span>
                                           <span class="hljs-comment">//注意这里取下标 是用 哈希值 与 桶的长度-1 。 由于桶的长度是2的n次方，这么做其实是等于 一个模运算。但是效率更高</span>
                                           newTab[e.hash &amp; (newCap - <span class="hljs-number">1</span>)] = e;
                                           <span class="hljs-comment">//如果发生过哈希碰撞 ,而且是节点数超过8个，转化成了红黑树（暂且不谈 避免过于复杂， 后续专门研究一下红黑树）</span>
                                       <span class="hljs-keyword">else</span> <span class="hljs-keyword">if</span> (e <span class="hljs-keyword">instanceof</span> TreeNode)
                                           ((TreeNode&lt;K,V&gt;)e).split(<span class="hljs-keyword">this</span>, newTab, j, oldCap);
                                       <span class="hljs-comment">//如果发生过哈希碰撞，节点数小于8个。则要根据链表上每个节点的哈希值，依次放入新哈希桶对应下标位置。</span>
                                       <span class="hljs-keyword">else</span> { <span class="hljs-comment">// preserve order</span>
                                           <span class="hljs-comment">//因为扩容是容量翻倍，所以原链表上的每个节点，现在可能存放在原来的下标，即low位， 或者扩容后的下标，即high位。 high位=  low位+原哈希桶容量</span>
                                           <span class="hljs-comment">//低位链表的头结点、尾节点</span>
                                           Node&lt;K,V&gt; loHead = <span class="hljs-keyword">null</span>, loTail = <span class="hljs-keyword">null</span>;
                                           <span class="hljs-comment">//高位链表的头节点、尾节点</span>
                                           Node&lt;K,V&gt; hiHead = <span class="hljs-keyword">null</span>, hiTail = <span class="hljs-keyword">null</span>;
                                           Node&lt;K,V&gt; next;<span class="hljs-comment">//临时节点 存放e的下一个节点</span>
                                           <span class="hljs-keyword">do</span> {
                                               next = e.next;
                                               <span class="hljs-comment">//这里又是一个利用位运算 代替常规运算的高效点： 利用哈希值 与 旧的容量，可以得到哈希值去模后，是大于等于oldCap还是小于oldCap，等于0代表小于oldCap，应该存放在低位，否则存放在高位</span>
                                               <span class="hljs-keyword">if</span> ((e.hash &amp; oldCap) == <span class="hljs-number">0</span>) {
                                                   <span class="hljs-comment">//给头尾节点指针赋值</span>
                                                   <span class="hljs-keyword">if</span> (loTail == <span class="hljs-keyword">null</span>)
                                                       loHead = e;
                                                   <span class="hljs-keyword">else</span>
                                                       loTail.next = e;
                                                   loTail = e;
                                               }<span class="hljs-comment">//高位也是相同的逻辑</span>
                                               <span class="hljs-keyword">else</span> {
                                                   <span class="hljs-keyword">if</span> (hiTail == <span class="hljs-keyword">null</span>)
                                                       hiHead = e;
                                                   <span class="hljs-keyword">else</span>
                                                       hiTail.next = e;
                                                   hiTail = e;
                                               }<span class="hljs-comment">//循环直到链表结束</span>
                                           } <span class="hljs-keyword">while</span> ((e = next) != <span class="hljs-keyword">null</span>);
                                           <span class="hljs-comment">//将低位链表存放在原index处，</span>
                                           <span class="hljs-keyword">if</span> (loTail != <span class="hljs-keyword">null</span>) {
                                               loTail.next = <span class="hljs-keyword">null</span>;
                                               newTab[j] = loHead;
                                           }
                                           <span class="hljs-comment">//将高位链表存放在新index处</span>
                                           <span class="hljs-keyword">if</span> (hiTail != <span class="hljs-keyword">null</span>) {
                                               hiTail.next = <span class="hljs-keyword">null</span>;
                                               newTab[j + oldCap] = hiHead;
                                           }
                                       }
                                   }
                               }
                           }
                           <span class="hljs-keyword">return</span> newTab;
                       }
                </code></pre>
                
                <p><code>newNode</code>如下：构建一个链表节点</p>
                
                <pre class="hljs java"><code class="java">    <span class="hljs-comment">// Create a regular (non-tree) node</span>
                    <span class="hljs-function">Node&lt;K,V&gt; <span class="hljs-title">newNode</span><span class="hljs-params">(<span class="hljs-keyword">int</span> hash, K key, V value, Node&lt;K,V&gt; next)</span> </span>{
                        <span class="hljs-keyword">return</span> <span class="hljs-keyword">new</span> Node&lt;&gt;(hash, key, value, next);
                    }
                </code></pre>
                
                <pre class="hljs java"><code class="java">    <span class="hljs-comment">// Callbacks to allow LinkedHashMap post-actions</span>
                    <span class="hljs-function"><span class="hljs-keyword">void</span> <span class="hljs-title">afterNodeAccess</span><span class="hljs-params">(Node&lt;K,V&gt; p)</span> </span>{ }
                    <span class="hljs-function"><span class="hljs-keyword">void</span> <span class="hljs-title">afterNodeInsertion</span><span class="hljs-params">(<span class="hljs-keyword">boolean</span> evict)</span> </span>{ }
                </code></pre>
                
                <p>小结：</p>
                
                <ul>
                    <li>运算尽量都用<strong>位运算</strong>代替<strong>，更高效</strong>。</li>
                    <li>对于<strong>扩容</strong>导致需要新建数组存放更多元素时，除了要将老数组中的元素迁移过来，也记得将<strong>老数组中的引用置null</strong>，以便<strong>GC</strong>
                    </li>
                    <li>取下标 是用 <strong>哈希值 与运算 （桶的长度-1）</strong>  <code>i = (n - 1) &amp; hash</code>。 由于桶的长度是2的n次方，这么做其实是等于 一个<strong>模运算</strong>。但是<strong>效率更高</strong>
                    </li>
                    <li>扩容时，如果发生过哈希碰撞，节点数小于8个。则要根据链表上每个节点的哈希值，依次放入新哈希桶对应下标位置。</li>
                    <li>因为扩容是容量翻倍，所以原链表上的每个节点，现在可能存放在原来的下标，即low位， 或者扩容后的下标，即high位。 high位=  low位+原哈希桶容量</li>
                    <li>利用<strong>哈希值 与运算 旧的容量</strong> ，<code>if ((e.hash &amp; oldCap) == 0)</code>,可以得到哈希值去模后，是大于等于oldCap还是小于oldCap，等于0代表小于oldCap，<strong>应该存放在低位，否则存放在高位</strong>。这里又是一个利用位运算 代替常规运算的高效点</li>
                    <li>如果追加节点后，链表数量》=8，则转化为红黑树</li>
                    <li>插入节点操作时，有一些空实现的函数，用作LinkedHashMap重写使用。</li>
                </ul>
                
             <h4>增、改</h4>
             
             * 往表中插入或覆盖一个key-value      
             
                <pre class="hljs cpp"><code class="cpp">    <span class="hljs-function"><span class="hljs-keyword">public</span> V <span class="hljs-title">put</span><span class="hljs-params">(K key, V value)</span> </span>{
                        <span class="hljs-comment">//先根据key，取得hash值。 再调用上一节的方法插入节点</span>
                        <span class="hljs-keyword">return</span> putVal(hash(key), key, value, <span class="hljs-literal">false</span>, <span class="hljs-literal">true</span>);
                    }
                </code></pre>
                
             * 这个根据key取hash值的函数也要关注一下，它称之为“扰动函数”，关于这个函数的用处 开头已经总结过了：
             
                <pre class="hljs java"><code class="java">    <span class="hljs-function"><span class="hljs-keyword">static</span> <span class="hljs-keyword">final</span> <span class="hljs-keyword">int</span> <span class="hljs-title">hash</span><span class="hljs-params">(Object key)</span> </span>{
                        <span class="hljs-keyword">int</span> h;
                        <span class="hljs-keyword">return</span> (key == <span class="hljs-keyword">null</span>) ? <span class="hljs-number">0</span> : (h = key.hashCode()) ^ (h &gt;&gt;&gt; <span class="hljs-number">16</span>);
                    }
                </code></pre>
                
            * 批量增加数据
                
                <pre class="hljs cpp"><code class="cpp">    <span class="hljs-function"><span class="hljs-keyword">public</span> <span class="hljs-keyword">void</span> <span class="hljs-title">putAll</span><span class="hljs-params">(Map&lt;? extends K, ? extends V&gt; m)</span> </span>{
                        <span class="hljs-comment">//这个函数上一节也已经分析过。//将另一个Map的所有元素加入表中，参数evict初始化时为false，其他情况为true</span>
                        putMapEntries(m, <span class="hljs-literal">true</span>);
                    }
                </code></pre>
                
            * 只会往表中插入 key-value, 若key对应的value之前存在，不会覆盖。（jdk8增加的方法）
                
                <pre class="hljs java"><code class="java">    <span class="hljs-meta">@Override</span>
                    <span class="hljs-function"><span class="hljs-keyword">public</span> V <span class="hljs-title">putIfAbsent</span><span class="hljs-params">(K key, V value)</span> </span>{
                        <span class="hljs-keyword">return</span> putVal(hash(key), key, value, <span class="hljs-keyword">true</span>, <span class="hljs-keyword">true</span>);
                    }
                </code></pre>
        * 删
        
            以key为条件删除
        
            如果key对应的value存在，则删除这个键值对。 并返回value。如果不存在 返回null。
            
            <pre class="hljs java"><code class="java">    <span class="hljs-function"><span class="hljs-keyword">public</span> V <span class="hljs-title">remove</span><span class="hljs-params">(Object key)</span> </span>{
                    Node&lt;K,V&gt; e;
                    <span class="hljs-keyword">return</span> (e = removeNode(hash(key), key, <span class="hljs-keyword">null</span>, <span class="hljs-keyword">false</span>, <span class="hljs-keyword">true</span>)) == <span class="hljs-keyword">null</span> ?
                        <span class="hljs-keyword">null</span> : e.value;
                }
            </code></pre>
            
            //从哈希表中删除某个节点， 如果参数matchValue是true，则必须key 、value都相等才删除。<br/>
            //如果movable参数是false，在删除节点时，不移动其他节点
            
            <pre class="hljs java"><code class="java">    <span class="hljs-function"><span class="hljs-keyword">final</span> Node&lt;K,V&gt; <span class="hljs-title">removeNode</span><span class="hljs-params">(<span class="hljs-keyword">int</span> hash, Object key, Object value,
                                           <span class="hljs-keyword">boolean</span> matchValue, <span class="hljs-keyword">boolean</span> movable)</span> </span>{
                    <span class="hljs-comment">// p 是待删除节点的前置节点</span>
                    Node&lt;K,V&gt;[] tab; Node&lt;K,V&gt; p; <span class="hljs-keyword">int</span> n, index;
                    <span class="hljs-comment">//如果哈希表不为空，则根据hash值算出的index下 有节点的话。</span>
                    <span class="hljs-keyword">if</span> ((tab = table) != <span class="hljs-keyword">null</span> &amp;&amp; (n = tab.length) &gt; <span class="hljs-number">0</span> &amp;&amp;
                        (p = tab[index = (n - <span class="hljs-number">1</span>) &amp; hash]) != <span class="hljs-keyword">null</span>) {
                        <span class="hljs-comment">//node是待删除节点</span>
                        Node&lt;K,V&gt; node = <span class="hljs-keyword">null</span>, e; K k; V v;
                        <span class="hljs-comment">//如果链表头的就是需要删除的节点</span>
                        <span class="hljs-keyword">if</span> (p.hash == hash &amp;&amp;
                            ((k = p.key) == key || (key != <span class="hljs-keyword">null</span> &amp;&amp; key.equals(k))))
                            node = p;<span class="hljs-comment">//将待删除节点引用赋给node</span>
                        <span class="hljs-keyword">else</span> <span class="hljs-keyword">if</span> ((e = p.next) != <span class="hljs-keyword">null</span>) {<span class="hljs-comment">//否则循环遍历 找到待删除节点，赋值给node</span>
                            <span class="hljs-keyword">if</span> (p <span class="hljs-keyword">instanceof</span> TreeNode)
                                node = ((TreeNode&lt;K,V&gt;)p).getTreeNode(hash, key);
                            <span class="hljs-keyword">else</span> {
                                <span class="hljs-keyword">do</span> {
                                    <span class="hljs-keyword">if</span> (e.hash == hash &amp;&amp;
                                        ((k = e.key) == key ||
                                         (key != <span class="hljs-keyword">null</span> &amp;&amp; key.equals(k)))) {
                                        node = e;
                                        <span class="hljs-keyword">break</span>;
                                    }
                                    p = e;
                                } <span class="hljs-keyword">while</span> ((e = e.next) != <span class="hljs-keyword">null</span>);
                            }
                        }
                        <span class="hljs-comment">//如果有待删除节点node，  且 matchValue为false，或者值也相等</span>
                        <span class="hljs-keyword">if</span> (node != <span class="hljs-keyword">null</span> &amp;&amp; (!matchValue || (v = node.value) == value ||
                                             (value != <span class="hljs-keyword">null</span> &amp;&amp; value.equals(v)))) {
                            <span class="hljs-keyword">if</span> (node <span class="hljs-keyword">instanceof</span> TreeNode)
                                ((TreeNode&lt;K,V&gt;)node).removeTreeNode(<span class="hljs-keyword">this</span>, tab, movable);
                            <span class="hljs-keyword">else</span> <span class="hljs-keyword">if</span> (node == p)<span class="hljs-comment">//如果node ==  p，说明是链表头是待删除节点</span>
                                tab[index] = node.next;
                            <span class="hljs-keyword">else</span><span class="hljs-comment">//否则待删除节点在表中间</span>
                                p.next = node.next;
                            ++modCount;<span class="hljs-comment">//修改modCount</span>
                            --size;<span class="hljs-comment">//修改size</span>
                            afterNodeRemoval(node);<span class="hljs-comment">//LinkedHashMap回调函数</span>
                            <span class="hljs-keyword">return</span> node;
                        }
                    }
                    <span class="hljs-keyword">return</span> <span class="hljs-keyword">null</span>;
                }
            </code></pre>
            
             * 以key value 为条件删除
                
                <pre class="hljs java"><code class="java">    <span class="hljs-meta">@Override</span>
                    <span class="hljs-function"><span class="hljs-keyword">public</span> <span class="hljs-keyword">boolean</span> <span class="hljs-title">remove</span><span class="hljs-params">(Object key, Object value)</span> </span>{
                        <span class="hljs-comment">//这里传入了value 同时matchValue为true</span>
                        <span class="hljs-keyword">return</span> removeNode(hash(key), key, value, <span class="hljs-keyword">true</span>, <span class="hljs-keyword">true</span>) != <span class="hljs-keyword">null</span>;
                    }
                </code></pre>
                
        * 查
            
            * 以key为条件，找到返回value。没找到返回null
            
                <pre class="hljs java"><code class="java">    <span class="hljs-function"><span class="hljs-keyword">public</span> V <span class="hljs-title">get</span><span class="hljs-params">(Object key)</span> </span>{
                        Node&lt;K,V&gt; e;
                        <span class="hljs-comment">//传入扰动后的哈希值 和 key 找到目标节点Node</span>
                        <span class="hljs-keyword">return</span> (e = getNode(hash(key), key)) == <span class="hljs-keyword">null</span> ? <span class="hljs-keyword">null</span> : e.value;
                    }
                </code></pre>
                
                 <pre class="hljs java"><code class="java">    <span class="hljs-comment">//传入扰动后的哈希值 和 key 找到目标节点Node</span>
                      <span class="hljs-function"><span class="hljs-keyword">final</span> Node&lt;K,V&gt; <span class="hljs-title">getNode</span><span class="hljs-params">(<span class="hljs-keyword">int</span> hash, Object key)</span> </span>{
                          Node&lt;K,V&gt;[] tab; Node&lt;K,V&gt; first, e; <span class="hljs-keyword">int</span> n; K k;
                          <span class="hljs-comment">//查找过程和删除基本差不多， 找到返回节点，否则返回null</span>
                          <span class="hljs-keyword">if</span> ((tab = table) != <span class="hljs-keyword">null</span> &amp;&amp; (n = tab.length) &gt; <span class="hljs-number">0</span> &amp;&amp;
                              (first = tab[(n - <span class="hljs-number">1</span>) &amp; hash]) != <span class="hljs-keyword">null</span>) {
                              <span class="hljs-keyword">if</span> (first.hash == hash &amp;&amp; <span class="hljs-comment">// always check first node</span>
                                  ((k = first.key) == key || (key != <span class="hljs-keyword">null</span> &amp;&amp; key.equals(k))))
                                  <span class="hljs-keyword">return</span> first;
                              <span class="hljs-keyword">if</span> ((e = first.next) != <span class="hljs-keyword">null</span>) {
                                  <span class="hljs-keyword">if</span> (first <span class="hljs-keyword">instanceof</span> TreeNode)
                                      <span class="hljs-keyword">return</span> ((TreeNode&lt;K,V&gt;)first).getTreeNode(hash, key);
                                  <span class="hljs-keyword">do</span> {
                                      <span class="hljs-keyword">if</span> (e.hash == hash &amp;&amp;
                                          ((k = e.key) == key || (key != <span class="hljs-keyword">null</span> &amp;&amp; key.equals(k))))
                                          <span class="hljs-keyword">return</span> e;
                                  } <span class="hljs-keyword">while</span> ((e = e.next) != <span class="hljs-keyword">null</span>);
                              }
                          }
                          <span class="hljs-keyword">return</span> <span class="hljs-keyword">null</span>;
                      }
                  </code></pre>
             
            * 判断是否包含该key
                 
                 <pre class="hljs java"><code class="java">    <span class="hljs-function"><span class="hljs-keyword">public</span> <span class="hljs-keyword">boolean</span> <span class="hljs-title">containsKey</span><span class="hljs-params">(Object key)</span> </span>{
                         <span class="hljs-keyword">return</span> getNode(hash(key), key) != <span class="hljs-keyword">null</span>;
                     }
                 </code></pre>
                 
            * 判断是否包含value
            
                <pre class="hljs java"><code class="java">    <span class="hljs-function"><span class="hljs-keyword">public</span> <span class="hljs-keyword">boolean</span> <span class="hljs-title">containsValue</span><span class="hljs-params">(Object value)</span> </span>{
                        Node&lt;K,V&gt;[] tab; V v;
                        <span class="hljs-comment">//遍历哈希桶上的每一个链表</span>
                        <span class="hljs-keyword">if</span> ((tab = table) != <span class="hljs-keyword">null</span> &amp;&amp; size &gt; <span class="hljs-number">0</span>) {
                            <span class="hljs-keyword">for</span> (<span class="hljs-keyword">int</span> i = <span class="hljs-number">0</span>; i &lt; tab.length; ++i) {
                                <span class="hljs-keyword">for</span> (Node&lt;K,V&gt; e = tab[i]; e != <span class="hljs-keyword">null</span>; e = e.next) {
                                    <span class="hljs-comment">//如果找到value一致的返回true</span>
                                    <span class="hljs-keyword">if</span> ((v = e.value) == value ||
                                        (value != <span class="hljs-keyword">null</span> &amp;&amp; value.equals(v)))
                                        <span class="hljs-keyword">return</span> <span class="hljs-keyword">true</span>;
                                }
                            }
                        }
                        <span class="hljs-keyword">return</span> <span class="hljs-keyword">false</span>;
                    }
                </code></pre>
                
            * java8新增，带默认值的get方法
            
                以key为条件，找到了返回value。否则返回defaultValue
                
                <pre class="hljs java"><code class="java">    <span class="hljs-meta">@Override</span>
                    <span class="hljs-function"><span class="hljs-keyword">public</span> V <span class="hljs-title">getOrDefault</span><span class="hljs-params">(Object key, V defaultValue)</span> </span>{
                        Node&lt;K,V&gt; e;
                        <span class="hljs-keyword">return</span> (e = getNode(hash(key), key)) == <span class="hljs-keyword">null</span> ? defaultValue : e.value;
                    }
                
                </code></pre>
                
            * 遍历
                
                <pre class="hljs java"><code class="java">    <span class="hljs-comment">//缓存 entrySet</span>
                    <span class="hljs-keyword">transient</span> Set&lt;Map.Entry&lt;K,V&gt;&gt; entrySet;
                     */
                    <span class="hljs-keyword">public</span> Set&lt;Map.Entry&lt;K,V&gt;&gt; entrySet() {
                        Set&lt;Map.Entry&lt;K,V&gt;&gt; es;
                        <span class="hljs-keyword">return</span> (es = entrySet) == <span class="hljs-keyword">null</span> ? (entrySet = <span class="hljs-keyword">new</span> EntrySet()) : es;
                    }
                </code></pre>
                
                <pre class="hljs java"><code class="java">    <span class="hljs-keyword">final</span> <span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">EntrySet</span> <span class="hljs-keyword">extends</span> <span class="hljs-title">AbstractSet</span>&lt;<span class="hljs-title">Map</span>.<span class="hljs-title">Entry</span>&lt;<span class="hljs-title">K</span>,<span class="hljs-title">V</span>&gt;&gt; </span>{
                        <span class="hljs-function"><span class="hljs-keyword">public</span> <span class="hljs-keyword">final</span> <span class="hljs-keyword">int</span> <span class="hljs-title">size</span><span class="hljs-params">()</span>                 </span>{ <span class="hljs-keyword">return</span> size; }
                        <span class="hljs-function"><span class="hljs-keyword">public</span> <span class="hljs-keyword">final</span> <span class="hljs-keyword">void</span> <span class="hljs-title">clear</span><span class="hljs-params">()</span>               </span>{ HashMap.<span class="hljs-keyword">this</span>.clear(); }
                        <span class="hljs-comment">//一般我们用到EntrySet，都是为了获取iterator</span>
                        <span class="hljs-keyword">public</span> <span class="hljs-keyword">final</span> Iterator&lt;Map.Entry&lt;K,V&gt;&gt; iterator() {
                            <span class="hljs-keyword">return</span> <span class="hljs-keyword">new</span> EntryIterator();
                        }
                        <span class="hljs-comment">//最终还是调用getNode方法</span>
                        <span class="hljs-function"><span class="hljs-keyword">public</span> <span class="hljs-keyword">final</span> <span class="hljs-keyword">boolean</span> <span class="hljs-title">contains</span><span class="hljs-params">(Object o)</span> </span>{
                            <span class="hljs-keyword">if</span> (!(o <span class="hljs-keyword">instanceof</span> Map.Entry))
                                <span class="hljs-keyword">return</span> <span class="hljs-keyword">false</span>;
                            Map.Entry&lt;?,?&gt; e = (Map.Entry&lt;?,?&gt;) o;
                            Object key = e.getKey();
                            Node&lt;K,V&gt; candidate = getNode(hash(key), key);
                            <span class="hljs-keyword">return</span> candidate != <span class="hljs-keyword">null</span> &amp;&amp; candidate.equals(e);
                        }
                        <span class="hljs-comment">//最终还是调用removeNode方法</span>
                        <span class="hljs-function"><span class="hljs-keyword">public</span> <span class="hljs-keyword">final</span> <span class="hljs-keyword">boolean</span> <span class="hljs-title">remove</span><span class="hljs-params">(Object o)</span> </span>{
                            <span class="hljs-keyword">if</span> (o <span class="hljs-keyword">instanceof</span> Map.Entry) {
                                Map.Entry&lt;?,?&gt; e = (Map.Entry&lt;?,?&gt;) o;
                                Object key = e.getKey();
                                Object value = e.getValue();
                                <span class="hljs-keyword">return</span> removeNode(hash(key), key, value, <span class="hljs-keyword">true</span>, <span class="hljs-keyword">true</span>) != <span class="hljs-keyword">null</span>;
                            }
                            <span class="hljs-keyword">return</span> <span class="hljs-keyword">false</span>;
                        }
                        <span class="hljs-comment">//。。。</span>
                    }
                </code></pre>
                
                //EntryIterator的实现：
                
                    <pre class="hljs java"><code class="java">    <span class="hljs-keyword">final</span> <span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">EntryIterator</span> <span class="hljs-keyword">extends</span> <span class="hljs-title">HashIterator</span>
                            <span class="hljs-keyword">implements</span> <span class="hljs-title">Iterator</span>&lt;<span class="hljs-title">Map</span>.<span class="hljs-title">Entry</span>&lt;<span class="hljs-title">K</span>,<span class="hljs-title">V</span>&gt;&gt; </span>{
                            <span class="hljs-keyword">public</span> <span class="hljs-keyword">final</span> Map.<span class="hljs-function">Entry&lt;K,V&gt; <span class="hljs-title">next</span><span class="hljs-params">()</span> </span>{ <span class="hljs-keyword">return</span> nextNode(); }
                        }
                    </code></pre>
                    
                    <pre class="hljs java"><code class="java">    <span class="hljs-keyword">abstract</span> <span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">HashIterator</span> </span>{
                            Node&lt;K,V&gt; next;        <span class="hljs-comment">// next entry to return</span>
                            Node&lt;K,V&gt; current;     <span class="hljs-comment">// current entry</span>
                            <span class="hljs-keyword">int</span> expectedModCount;  <span class="hljs-comment">// for fast-fail</span>
                            <span class="hljs-keyword">int</span> index;             <span class="hljs-comment">// current slot</span>
                    
                            HashIterator() {
                                <span class="hljs-comment">//因为hashmap也是线程不安全的，所以要保存modCount。用于fail-fast策略</span>
                                expectedModCount = modCount;
                                Node&lt;K,V&gt;[] t = table;
                                current = next = <span class="hljs-keyword">null</span>;
                                index = <span class="hljs-number">0</span>;
                                <span class="hljs-comment">//next 初始时，指向 哈希桶上第一个不为null的链表头</span>
                                <span class="hljs-keyword">if</span> (t != <span class="hljs-keyword">null</span> &amp;&amp; size &gt; <span class="hljs-number">0</span>) { <span class="hljs-comment">// advance to first entry</span>
                                    <span class="hljs-keyword">do</span> {} <span class="hljs-keyword">while</span> (index &lt; t.length &amp;&amp; (next = t[index++]) == <span class="hljs-keyword">null</span>);
                                }
                            }
                    
                            <span class="hljs-function"><span class="hljs-keyword">public</span> <span class="hljs-keyword">final</span> <span class="hljs-keyword">boolean</span> <span class="hljs-title">hasNext</span><span class="hljs-params">()</span> </span>{
                                <span class="hljs-keyword">return</span> next != <span class="hljs-keyword">null</span>;
                            }
                    
                            <span class="hljs-comment">//由这个方法可以看出，遍历HashMap时，顺序是按照哈希桶从低到高，链表从前往后，依次遍历的。属于无序集合。</span>
                            <span class="hljs-function"><span class="hljs-keyword">final</span> Node&lt;K,V&gt; <span class="hljs-title">nextNode</span><span class="hljs-params">()</span> </span>{
                                Node&lt;K,V&gt;[] t;
                                Node&lt;K,V&gt; e = next;
                                <span class="hljs-comment">//fail-fast策略</span>
                                <span class="hljs-keyword">if</span> (modCount != expectedModCount)
                                    <span class="hljs-keyword">throw</span> <span class="hljs-keyword">new</span> ConcurrentModificationException();
                                <span class="hljs-keyword">if</span> (e == <span class="hljs-keyword">null</span>)
                                    <span class="hljs-keyword">throw</span> <span class="hljs-keyword">new</span> NoSuchElementException();
                                <span class="hljs-comment">//依次取链表下一个节点，</span>
                                <span class="hljs-keyword">if</span> ((next = (current = e).next) == <span class="hljs-keyword">null</span> &amp;&amp; (t = table) != <span class="hljs-keyword">null</span>) {
                                    <span class="hljs-comment">//如果当前链表节点遍历完了，则取哈希桶下一个不为null的链表头</span>
                                    <span class="hljs-keyword">do</span> {} <span class="hljs-keyword">while</span> (index &lt; t.length &amp;&amp; (next = t[index++]) == <span class="hljs-keyword">null</span>);
                                }
                                <span class="hljs-keyword">return</span> e;
                            }
                    
                            <span class="hljs-function"><span class="hljs-keyword">public</span> <span class="hljs-keyword">final</span> <span class="hljs-keyword">void</span> <span class="hljs-title">remove</span><span class="hljs-params">()</span> </span>{
                                Node&lt;K,V&gt; p = current;
                                <span class="hljs-keyword">if</span> (p == <span class="hljs-keyword">null</span>)
                                    <span class="hljs-keyword">throw</span> <span class="hljs-keyword">new</span> IllegalStateException();
                                <span class="hljs-comment">////fail-fast策略</span>
                                <span class="hljs-keyword">if</span> (modCount != expectedModCount)
                                    <span class="hljs-keyword">throw</span> <span class="hljs-keyword">new</span> ConcurrentModificationException();
                                current = <span class="hljs-keyword">null</span>;
                                K key = p.key;
                                <span class="hljs-comment">//最终还是利用removeNode 删除节点</span>
                                removeNode(hash(key), key, <span class="hljs-keyword">null</span>, <span class="hljs-keyword">false</span>, <span class="hljs-keyword">false</span>);
                                expectedModCount = modCount;
                            }
                        }
                    </code></pre>
                    
            *  总结：
            
                <div>
                    <img src="https://upload-images.jianshu.io/upload_images/1696338-5b6e52b6310e4430?imageMogr2/auto-orient/strip%7CimageView2/2/w/700" />
                </div>
                
            * 与HashTable的区别
            
                * 与之相比HashTable是线程安全的，且不允许key、value是null。
                
                * HashTable默认容量是11。
                
                * HashTable是直接使用key的hashCode(key.hashCode())作为hash值，不像HashMap内部使用static final int hash(Object key)扰动函数对key的hashCode进行扰动后作为hash值。
                
                * HashTable取哈希桶下标是直接用模运算%.（因为其默认容量也不是2的n次方。所以也无法用位运算替代模运算）
                
                * 扩容时，新容量是原来的2倍+1。int newCapacity = (oldCapacity << 1) + 1;
                
                * Hashtable是Dictionary的子类同时也实现了Map接口，HashMap是Map接口的一个实现类；
                
        * [参考：LinkedHashMap源码解析（JDK8）](https://www.jianshu.com/p/8724a055289b)
                
        * LinkedHashMap源码解析
        
            > 思路：构造方法 -> 常用API(增、删、改、查)
            
            * 概要
                
                * LinkedHashMap是一个关联数组、哈希表，他是线程不安全的，允许null值和null键，它继承自HashMap，实现了Map<K,V>接口。其内部还维护了一个双向链表，在每次插入数据，或者访问、修改数据时，会增加节点、或调整链表的节点顺序。以决定迭代时输出的顺序。
                
                * 默认情况，遍历时的顺序是按照插入节点的顺序。这也是其与HashMap最大的区别。也可以在构造时传入accessOrder参数，使得其遍历顺序按照访问的顺序输出。
                
                * 因继承自HashMap,所以HashMap上文分析的特点，除了输出无序，其他LinkedHashMap都有，LinkedHashMap在实现时，就是重写override了几个方法。以满足其输出序列有序的需求。
                
            示例代码: 
            
            <pre class="hljs cpp"><code class="cpp">        Map&lt;String, String&gt; <span class="hljs-built_in">map</span> = <span class="hljs-keyword">new</span> LinkedHashMap&lt;&gt;();
                    <span class="hljs-built_in">map</span>.put(<span class="hljs-string">"1"</span>, <span class="hljs-string">"a"</span>);
                    <span class="hljs-built_in">map</span>.put(<span class="hljs-string">"2"</span>, <span class="hljs-string">"b"</span>);
                    <span class="hljs-built_in">map</span>.put(<span class="hljs-string">"3"</span>, <span class="hljs-string">"c"</span>);
                    <span class="hljs-built_in">map</span>.put(<span class="hljs-string">"4"</span>, <span class="hljs-string">"d"</span>);
            
                    Iterator&lt;Map.Entry&lt;String, String&gt;&gt; iterator = <span class="hljs-built_in">map</span>.entrySet().iterator();
                    <span class="hljs-keyword">while</span> (iterator.hasNext()) {
                        System.out.println(iterator.next());
                    }
            
                    System.out.println(<span class="hljs-string">"以下是accessOrder=true的情况:"</span>);
            
                    <span class="hljs-built_in">map</span> = <span class="hljs-keyword">new</span> LinkedHashMap&lt;String, String&gt;(<span class="hljs-number">10</span>, <span class="hljs-number">0.75f</span>, <span class="hljs-literal">true</span>);
                    <span class="hljs-built_in">map</span>.put(<span class="hljs-string">"1"</span>, <span class="hljs-string">"a"</span>);
                    <span class="hljs-built_in">map</span>.put(<span class="hljs-string">"2"</span>, <span class="hljs-string">"b"</span>);
                    <span class="hljs-built_in">map</span>.put(<span class="hljs-string">"3"</span>, <span class="hljs-string">"c"</span>);
                    <span class="hljs-built_in">map</span>.put(<span class="hljs-string">"4"</span>, <span class="hljs-string">"d"</span>);
                    <span class="hljs-built_in">map</span>.get(<span class="hljs-string">"2"</span>);<span class="hljs-comment">//2移动到了内部的链表末尾</span>
                    <span class="hljs-built_in">map</span>.get(<span class="hljs-string">"4"</span>);<span class="hljs-comment">//4调整至末尾</span>
                    <span class="hljs-built_in">map</span>.put(<span class="hljs-string">"3"</span>, <span class="hljs-string">"e"</span>);<span class="hljs-comment">//3调整至末尾</span>
                    <span class="hljs-built_in">map</span>.put(null, null);<span class="hljs-comment">//插入两个新的节点 null</span>
                    <span class="hljs-built_in">map</span>.put(<span class="hljs-string">"5"</span>, null);<span class="hljs-comment">//5</span>
                    iterator = <span class="hljs-built_in">map</span>.entrySet().iterator();
                    <span class="hljs-keyword">while</span> (iterator.hasNext()) {
                        System.out.println(iterator.next());
                    }
            </code></pre>
            
            <pre class="hljs java"><code class="java"><span class="hljs-number">1</span>=a
            <span class="hljs-number">2</span>=b
            <span class="hljs-number">3</span>=c
            <span class="hljs-number">4</span>=d
            以下是accessOrder=<span class="hljs-keyword">true</span>的情况:
            <span class="hljs-number">1</span>=a
            <span class="hljs-number">2</span>=b
            <span class="hljs-number">4</span>=d
            <span class="hljs-number">3</span>=e
            <span class="hljs-keyword">null</span>=<span class="hljs-keyword">null</span>
            <span class="hljs-number">5</span>=<span class="hljs-keyword">null</span>
            </code></pre>
            
            * 节点
            
                LinkedHashMap的节点Entry<K,V>继承自HashMap.Node<K,V>，在其基础上扩展了一下。改成了一个双向链表。
                
                <pre class="hljs ruby"><code class="ruby">    static <span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">Entry</span>&lt;K,<span class="hljs-title">V</span>&gt; <span class="hljs-title">extends</span> <span class="hljs-title">HashMap</span>.<span class="hljs-title">Node</span>&lt;K,<span class="hljs-title">V</span>&gt; {</span>
                        Entry&lt;K,V&gt; before, after;
                        Entry(int hash, K key, V value, Node&lt;K,V&gt; <span class="hljs-keyword">next</span>) {
                            <span class="hljs-keyword">super</span>(hash, key, value, <span class="hljs-keyword">next</span>);
                        }
                    }
                </code></pre>
                
                同时类里有两个成员变量head tail,分别指向内部双向链表的表头、表尾。
                
                <pre class="hljs java"><code class="java">    <span class="hljs-comment">//双向链表的头结点</span>
                    <span class="hljs-keyword">transient</span> LinkedHashMap.Entry&lt;K,V&gt; head;
                
                    <span class="hljs-comment">//双向链表的尾节点</span>
                    <span class="hljs-keyword">transient</span> LinkedHashMap.Entry&lt;K,V&gt; tail;
                </code></pre>
                
            * 构造函数
            
                <pre class="hljs java"><code class="java">    <span class="hljs-comment">//默认是false，则迭代时输出的顺序是插入节点的顺序。若为true，则输出的顺序是按照访问节点的顺序。</span>
                    <span class="hljs-comment">//为true时，可以在这基础之上构建一个LruCach</span>
                    <span class="hljs-keyword">final</span> <span class="hljs-keyword">boolean</span> accessOrder;
                    
                    <span class="hljs-function"><span class="hljs-keyword">public</span> <span class="hljs-title">LinkedHashMap</span><span class="hljs-params">()</span> </span>{
                        <span class="hljs-keyword">super</span>();
                        accessOrder = <span class="hljs-keyword">false</span>;
                    }
                    <span class="hljs-comment">//指定初始化时的容量，</span>
                    <span class="hljs-function"><span class="hljs-keyword">public</span> <span class="hljs-title">LinkedHashMap</span><span class="hljs-params">(<span class="hljs-keyword">int</span> initialCapacity)</span> </span>{
                        <span class="hljs-keyword">super</span>(initialCapacity);
                        accessOrder = <span class="hljs-keyword">false</span>;
                    }
                    <span class="hljs-comment">//指定初始化时的容量，和扩容的加载因子</span>
                    <span class="hljs-function"><span class="hljs-keyword">public</span> <span class="hljs-title">LinkedHashMap</span><span class="hljs-params">(<span class="hljs-keyword">int</span> initialCapacity, <span class="hljs-keyword">float</span> loadFactor)</span> </span>{
                        <span class="hljs-keyword">super</span>(initialCapacity, loadFactor);
                        accessOrder = <span class="hljs-keyword">false</span>;
                    }
                    <span class="hljs-comment">//指定初始化时的容量，和扩容的加载因子，以及迭代输出节点的顺序</span>
                    <span class="hljs-function"><span class="hljs-keyword">public</span> <span class="hljs-title">LinkedHashMap</span><span class="hljs-params">(<span class="hljs-keyword">int</span> initialCapacity,
                                         <span class="hljs-keyword">float</span> loadFactor,
                                         <span class="hljs-keyword">boolean</span> accessOrder)</span> </span>{
                        <span class="hljs-keyword">super</span>(initialCapacity, loadFactor);
                        <span class="hljs-keyword">this</span>.accessOrder = accessOrder;
                    }
                    <span class="hljs-comment">//利用另一个Map 来构建，</span>
                    <span class="hljs-function"><span class="hljs-keyword">public</span> <span class="hljs-title">LinkedHashMap</span><span class="hljs-params">(Map&lt;? extends K, ? extends V&gt; m)</span> </span>{
                        <span class="hljs-keyword">super</span>();
                        accessOrder = <span class="hljs-keyword">false</span>;
                        <span class="hljs-comment">//该方法上文分析过，批量插入一个map中的所有数据到 本集合中。</span>
                        putMapEntries(m, <span class="hljs-keyword">false</span>);
                    }
                    
                </code></pre>
                
                #### 小结：
                
                 构造函数和HashMap相比，就是增加了一个accessOrder参数。用于控制迭代时的节点顺序。
                 
            * 增
            
                <p><code>LinkedHashMap</code>并没有重写任何put方法。但是其重写了构建新节点的<code>newNode()</code>方法.<br>
                <code>newNode()</code>会在<code>HashMap</code>的<code>putVal()</code>方法里被调用，<code>putVal()</code>方法会在批量插入数据<code>putMapEntries(Map&lt;? extends K, ? extends V&gt; m, boolean evict)</code>或者插入单个数据<code>public V put(K key, V value)</code>时被调用。</p>
                
                LinkedHashMap重写了newNode(),在每次构建新节点时，通过linkNodeLast(p);将新节点链接在内部双向链表的尾部。
                
                <pre class="hljs java"><code class="java">    <span class="hljs-comment">//在构建新节点时，构建的是`LinkedHashMap.Entry` 不再是`Node`.</span>
                    <span class="hljs-function">Node&lt;K,V&gt; <span class="hljs-title">newNode</span><span class="hljs-params">(<span class="hljs-keyword">int</span> hash, K key, V value, Node&lt;K,V&gt; e)</span> </span>{
                        LinkedHashMap.Entry&lt;K,V&gt; p =
                            <span class="hljs-keyword">new</span> LinkedHashMap.Entry&lt;K,V&gt;(hash, key, value, e);
                        linkNodeLast(p);
                        <span class="hljs-keyword">return</span> p;
                    }
                    <span class="hljs-comment">//将新增的节点，连接在链表的尾部</span>
                    <span class="hljs-function"><span class="hljs-keyword">private</span> <span class="hljs-keyword">void</span> <span class="hljs-title">linkNodeLast</span><span class="hljs-params">(LinkedHashMap.Entry&lt;K,V&gt; p)</span> </span>{
                        LinkedHashMap.Entry&lt;K,V&gt; last = tail;
                        tail = p;
                        <span class="hljs-comment">//集合之前是空的</span>
                        <span class="hljs-keyword">if</span> (last == <span class="hljs-keyword">null</span>)
                            head = p;
                        <span class="hljs-keyword">else</span> {<span class="hljs-comment">//将新节点连接在链表的尾部</span>
                            p.before = last;
                            last.after = p;
                        }
                    }
                </code></pre>
                
                以及HashMap专门预留给LinkedHashMap的afterNodeAccess() afterNodeInsertion() afterNodeRemoval() 方法。
                
                <pre class="hljs java"><code class="java">    <span class="hljs-comment">// Callbacks to allow LinkedHashMap post-actions</span>
                    <span class="hljs-function"><span class="hljs-keyword">void</span> <span class="hljs-title">afterNodeAccess</span><span class="hljs-params">(Node&lt;K,V&gt; p)</span> </span>{ }
                    <span class="hljs-function"><span class="hljs-keyword">void</span> <span class="hljs-title">afterNodeInsertion</span><span class="hljs-params">(<span class="hljs-keyword">boolean</span> evict)</span> </span>{ }
                    <span class="hljs-function"><span class="hljs-keyword">void</span> <span class="hljs-title">afterNodeRemoval</span><span class="hljs-params">(Node&lt;K,V&gt; p)</span> </span>{ }
                </code></pre>
                
                <pre class="hljs java"><code class="java">    <span class="hljs-comment">//回调函数，新节点插入之后回调 ， 根据evict 和   判断是否需要删除最老插入的节点。如果实现LruCache会用到这个方法。</span>
                    <span class="hljs-function"><span class="hljs-keyword">void</span> <span class="hljs-title">afterNodeInsertion</span><span class="hljs-params">(<span class="hljs-keyword">boolean</span> evict)</span> </span>{ <span class="hljs-comment">// possibly remove eldest</span>
                        LinkedHashMap.Entry&lt;K,V&gt; first;
                        <span class="hljs-comment">//LinkedHashMap 默认返回false 则不删除节点</span>
                        <span class="hljs-keyword">if</span> (evict &amp;&amp; (first = head) != <span class="hljs-keyword">null</span> &amp;&amp; removeEldestEntry(first)) {
                            K key = first.key;
                            removeNode(hash(key), key, <span class="hljs-keyword">null</span>, <span class="hljs-keyword">false</span>, <span class="hljs-keyword">true</span>);
                        }
                    }
                    <span class="hljs-comment">//LinkedHashMap 默认返回false 则不删除节点。 返回true 代表要删除最早的节点。通常构建一个LruCache会在达到Cache的上限是返回true</span>
                    <span class="hljs-function"><span class="hljs-keyword">protected</span> <span class="hljs-keyword">boolean</span> <span class="hljs-title">removeEldestEntry</span><span class="hljs-params">(Map.Entry&lt;K,V&gt; eldest)</span> </span>{
                        <span class="hljs-keyword">return</span> <span class="hljs-keyword">false</span>;
                    }
                </code></pre>
                
                void afterNodeInsertion(boolean evict)以及boolean removeEldestEntry(Map.Entry<K,V> eldest)是构建LruCache需要的回调，在LinkedHashMap里可以忽略它们。
            
            * 删
                
                LinkedHashMap也没有重写remove()方法，因为它的删除逻辑和HashMap并无区别。但它重写了afterNodeRemoval()这个回调方法。该方法会在Node<K,V> removeNode(int hash, Object key, Object value, boolean matchValue, boolean movable)方法中回调，removeNode()会在所有涉及到删除节点的方法中被调用，上文分析过，是删除节点操作的真正执行者。
                
                <pre class="hljs java"><code class="java">    <span class="hljs-comment">//在删除节点e时，同步将e从双向链表上删除</span>
                    <span class="hljs-function"><span class="hljs-keyword">void</span> <span class="hljs-title">afterNodeRemoval</span><span class="hljs-params">(Node&lt;K,V&gt; e)</span> </span>{ <span class="hljs-comment">// unlink</span>
                        LinkedHashMap.Entry&lt;K,V&gt; p =
                            (LinkedHashMap.Entry&lt;K,V&gt;)e, b = p.before, a = p.after;
                        <span class="hljs-comment">//待删除节点 p 的前置后置节点都置空</span>
                        p.before = p.after = <span class="hljs-keyword">null</span>;
                        <span class="hljs-comment">//如果前置节点是null，则现在的头结点应该是后置节点a</span>
                        <span class="hljs-keyword">if</span> (b == <span class="hljs-keyword">null</span>)
                            head = a;
                        <span class="hljs-keyword">else</span><span class="hljs-comment">//否则将前置节点b的后置节点指向a</span>
                            b.after = a;
                        <span class="hljs-comment">//同理如果后置节点时null ，则尾节点应是b</span>
                        <span class="hljs-keyword">if</span> (a == <span class="hljs-keyword">null</span>)
                            tail = b;
                        <span class="hljs-keyword">else</span><span class="hljs-comment">//否则更新后置节点a的前置节点为b</span>
                            a.before = b;
                    }
                </code></pre>
            
            * 查
            
               <p><code>LinkedHashMap</code>重写了<code>get()和getOrDefault()</code>方法：</p>
               
               <pre class="hljs java"><code class="java">    <span class="hljs-function"><span class="hljs-keyword">public</span> V <span class="hljs-title">get</span><span class="hljs-params">(Object key)</span> </span>{
                       Node&lt;K,V&gt; e;
                       <span class="hljs-keyword">if</span> ((e = getNode(hash(key), key)) == <span class="hljs-keyword">null</span>)
                           <span class="hljs-keyword">return</span> <span class="hljs-keyword">null</span>;
                       <span class="hljs-keyword">if</span> (accessOrder)
                           afterNodeAccess(e);
                       <span class="hljs-keyword">return</span> e.value;
                   }
                   <span class="hljs-function"><span class="hljs-keyword">public</span> V <span class="hljs-title">getOrDefault</span><span class="hljs-params">(Object key, V defaultValue)</span> </span>{
                      Node&lt;K,V&gt; e;
                      <span class="hljs-keyword">if</span> ((e = getNode(hash(key), key)) == <span class="hljs-keyword">null</span>)
                          <span class="hljs-keyword">return</span> defaultValue;
                      <span class="hljs-keyword">if</span> (accessOrder)
                          afterNodeAccess(e);
                      <span class="hljs-keyword">return</span> e.value;
                  }
               </code></pre>
               
               对比HashMap中的实现,LinkedHashMap只是增加了在成员变量(构造函数时赋值)accessOrder为true的情况下，要去回调void afterNodeAccess(Node<K,V> e)函数。
               
               <pre class="hljs java"><code class="java">    <span class="hljs-function"><span class="hljs-keyword">public</span> V <span class="hljs-title">get</span><span class="hljs-params">(Object key)</span> </span>{
                       Node&lt;K,V&gt; e;
                       <span class="hljs-keyword">return</span> (e = getNode(hash(key), key)) == <span class="hljs-keyword">null</span> ? <span class="hljs-keyword">null</span> : e.value;
                   }
               </code></pre>
               
               在afterNodeAccess()函数中，会将当前被访问到的节点e，移动至内部的双向链表的尾部。
               
               <pre class="hljs java"><code class="java">    <span class="hljs-function"><span class="hljs-keyword">void</span> <span class="hljs-title">afterNodeAccess</span><span class="hljs-params">(Node&lt;K,V&gt; e)</span> </span>{ <span class="hljs-comment">// move node to last</span>
                       LinkedHashMap.Entry&lt;K,V&gt; last;<span class="hljs-comment">//原尾节点</span>
                       <span class="hljs-comment">//如果accessOrder 是true ，且原尾节点不等于e</span>
                       <span class="hljs-keyword">if</span> (accessOrder &amp;&amp; (last = tail) != e) {
                           <span class="hljs-comment">//节点e强转成双向链表节点p</span>
                           LinkedHashMap.Entry&lt;K,V&gt; p =
                               (LinkedHashMap.Entry&lt;K,V&gt;)e, b = p.before, a = p.after;
                           <span class="hljs-comment">//p现在是尾节点， 后置节点一定是null</span>
                           p.after = <span class="hljs-keyword">null</span>;
                           <span class="hljs-comment">//如果p的前置节点是null，则p以前是头结点，所以更新现在的头结点是p的后置节点a</span>
                           <span class="hljs-keyword">if</span> (b == <span class="hljs-keyword">null</span>)
                               head = a;
                           <span class="hljs-keyword">else</span><span class="hljs-comment">//否则更新p的前直接点b的后置节点为 a</span>
                               b.after = a;
                           <span class="hljs-comment">//如果p的后置节点不是null，则更新后置节点a的前置节点为b</span>
                           <span class="hljs-keyword">if</span> (a != <span class="hljs-keyword">null</span>)
                               a.before = b;
                           <span class="hljs-keyword">else</span><span class="hljs-comment">//如果原本p的后置节点是null，则p就是尾节点。 此时 更新last的引用为 p的前置节点b</span>
                               last = b;
                           <span class="hljs-keyword">if</span> (last == <span class="hljs-keyword">null</span>) <span class="hljs-comment">//原本尾节点是null  则，链表中就一个节点</span>
                               head = p;
                           <span class="hljs-keyword">else</span> {<span class="hljs-comment">//否则 更新 当前节点p的前置节点为 原尾节点last， last的后置节点是p</span>
                               p.before = last;
                               last.after = p;
                           }
                           <span class="hljs-comment">//尾节点的引用赋值成p</span>
                           tail = p;
                           <span class="hljs-comment">//修改modCount。</span>
                           ++modCount;
                       }
                   }
               </code></pre>
               
               <pre class="hljs java"><code class="java">    <span class="hljs-function"><span class="hljs-keyword">void</span> <span class="hljs-title">afterNodeAccess</span><span class="hljs-params">(Node&lt;K,V&gt; e)</span> </span>{ <span class="hljs-comment">// move node to last</span>
                       LinkedHashMap.Entry&lt;K,V&gt; last;<span class="hljs-comment">//原尾节点</span>
                       <span class="hljs-comment">//如果accessOrder 是true ，且原尾节点不等于e</span>
                       <span class="hljs-keyword">if</span> (accessOrder &amp;&amp; (last = tail) != e) {
                           <span class="hljs-comment">//节点e强转成双向链表节点p</span>
                           LinkedHashMap.Entry&lt;K,V&gt; p =
                               (LinkedHashMap.Entry&lt;K,V&gt;)e, b = p.before, a = p.after;
                           <span class="hljs-comment">//p现在是尾节点， 后置节点一定是null</span>
                           p.after = <span class="hljs-keyword">null</span>;
                           <span class="hljs-comment">//如果p的前置节点是null，则p以前是头结点，所以更新现在的头结点是p的后置节点a</span>
                           <span class="hljs-keyword">if</span> (b == <span class="hljs-keyword">null</span>)
                               head = a;
                           <span class="hljs-keyword">else</span><span class="hljs-comment">//否则更新p的前直接点b的后置节点为 a</span>
                               b.after = a;
                           <span class="hljs-comment">//如果p的后置节点不是null，则更新后置节点a的前置节点为b</span>
                           <span class="hljs-keyword">if</span> (a != <span class="hljs-keyword">null</span>)
                               a.before = b;
                           <span class="hljs-keyword">else</span><span class="hljs-comment">//如果原本p的后置节点是null，则p就是尾节点。 此时 更新last的引用为 p的前置节点b</span>
                               last = b;
                           <span class="hljs-keyword">if</span> (last == <span class="hljs-keyword">null</span>) <span class="hljs-comment">//原本尾节点是null  则，链表中就一个节点</span>
                               head = p;
                           <span class="hljs-keyword">else</span> {<span class="hljs-comment">//否则 更新 当前节点p的前置节点为 原尾节点last， last的后置节点是p</span>
                               p.before = last;
                               last.after = p;
                           }
                           <span class="hljs-comment">//尾节点的引用赋值成p</span>
                           tail = p;
                           <span class="hljs-comment">//修改modCount。</span>
                           ++modCount;
                       }
                   }
               </code></pre>
               
               值得注意的是，afterNodeAccess()函数中，会修改modCount,因此当你正在accessOrder=true的模式下,迭代LinkedHashMap时，如果同时查询访问数据，也会导致fail-fast，因为迭代的顺序已经改变。
               
            * containsValue
            
                它重写了该方法，相比HashMap的实现，更为高效。
                
                <pre class="hljs java"><code class="java">    <span class="hljs-function"><span class="hljs-keyword">public</span> <span class="hljs-keyword">boolean</span> <span class="hljs-title">containsValue</span><span class="hljs-params">(Object value)</span> </span>{
                        <span class="hljs-comment">//遍历一遍链表，去比较有没有value相等的节点，并返回</span>
                        <span class="hljs-keyword">for</span> (LinkedHashMap.Entry&lt;K,V&gt; e = head; e != <span class="hljs-keyword">null</span>; e = e.after) {
                            V v = e.value;
                            <span class="hljs-keyword">if</span> (v == value || (value != <span class="hljs-keyword">null</span> &amp;&amp; value.equals(v)))
                                <span class="hljs-keyword">return</span> <span class="hljs-keyword">true</span>;
                        }
                        <span class="hljs-keyword">return</span> <span class="hljs-keyword">false</span>;
                    }
                </code></pre>
                
                对比HashMap，是用两个for循环遍历，相对低效。
                
                <pre class="hljs java"><code class="java">    <span class="hljs-function"><span class="hljs-keyword">public</span> <span class="hljs-keyword">boolean</span> <span class="hljs-title">containsValue</span><span class="hljs-params">(Object value)</span> </span>{
                        Node&lt;K,V&gt;[] tab; V v;
                        <span class="hljs-keyword">if</span> ((tab = table) != <span class="hljs-keyword">null</span> &amp;&amp; size &gt; <span class="hljs-number">0</span>) {
                            <span class="hljs-keyword">for</span> (<span class="hljs-keyword">int</span> i = <span class="hljs-number">0</span>; i &lt; tab.length; ++i) {
                                <span class="hljs-keyword">for</span> (Node&lt;K,V&gt; e = tab[i]; e != <span class="hljs-keyword">null</span>; e = e.next) {
                                    <span class="hljs-keyword">if</span> ((v = e.value) == value ||
                                        (value != <span class="hljs-keyword">null</span> &amp;&amp; value.equals(v)))
                                        <span class="hljs-keyword">return</span> <span class="hljs-keyword">true</span>;
                                }
                            }
                        }
                        <span class="hljs-keyword">return</span> <span class="hljs-keyword">false</span>;
                    }
                </code></pre>
                
            * 遍历 
            
                重写了entrySet()如下：
                
                    <pre class="hljs javascript"><code class="javascript">    public <span class="hljs-built_in">Set</span>&lt;<span class="hljs-built_in">Map</span>.Entry&lt;K,V&gt;&gt; entrySet() {
                            <span class="hljs-built_in">Set</span>&lt;<span class="hljs-built_in">Map</span>.Entry&lt;K,V&gt;&gt; es;
                            <span class="hljs-comment">//返回LinkedEntrySet</span>
                            <span class="hljs-keyword">return</span> (es = entrySet) == <span class="hljs-literal">null</span> ? (entrySet = <span class="hljs-keyword">new</span> LinkedEntrySet()) : es;
                        }
                        final <span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">LinkedEntrySet</span> <span class="hljs-keyword">extends</span> <span class="hljs-title">AbstractSet</span>&lt;<span class="hljs-title">Map</span>.<span class="hljs-title">Entry</span>&lt;<span class="hljs-title">K</span>,<span class="hljs-title">V</span>&gt;&gt; </span>{
                            public final Iterator&lt;<span class="hljs-built_in">Map</span>.Entry&lt;K,V&gt;&gt; iterator() {
                                <span class="hljs-keyword">return</span> <span class="hljs-keyword">new</span> LinkedEntryIterator();
                            }
                        }
                    </code></pre>
                    
                最终的EntryIterator：
                
                <pre class="hljs java"><code class="java">    <span class="hljs-keyword">final</span> <span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">LinkedEntryIterator</span> <span class="hljs-keyword">extends</span> <span class="hljs-title">LinkedHashIterator</span>
                        <span class="hljs-keyword">implements</span> <span class="hljs-title">Iterator</span>&lt;<span class="hljs-title">Map</span>.<span class="hljs-title">Entry</span>&lt;<span class="hljs-title">K</span>,<span class="hljs-title">V</span>&gt;&gt; </span>{
                        <span class="hljs-keyword">public</span> <span class="hljs-keyword">final</span> Map.<span class="hljs-function">Entry&lt;K,V&gt; <span class="hljs-title">next</span><span class="hljs-params">()</span> </span>{ <span class="hljs-keyword">return</span> nextNode(); }
                    }
                    
                    <span class="hljs-keyword">abstract</span> <span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">LinkedHashIterator</span> </span>{
                        <span class="hljs-comment">//下一个节点</span>
                        LinkedHashMap.Entry&lt;K,V&gt; next;
                        <span class="hljs-comment">//当前节点</span>
                        LinkedHashMap.Entry&lt;K,V&gt; current;
                        <span class="hljs-keyword">int</span> expectedModCount;
                
                        LinkedHashIterator() {
                            <span class="hljs-comment">//初始化时，next 为 LinkedHashMap内部维护的双向链表的扁头</span>
                            next = head;
                            <span class="hljs-comment">//记录当前modCount，以满足fail-fast</span>
                            expectedModCount = modCount;
                            <span class="hljs-comment">//当前节点为null</span>
                            current = <span class="hljs-keyword">null</span>;
                        }
                        <span class="hljs-comment">//判断是否还有next</span>
                        <span class="hljs-function"><span class="hljs-keyword">public</span> <span class="hljs-keyword">final</span> <span class="hljs-keyword">boolean</span> <span class="hljs-title">hasNext</span><span class="hljs-params">()</span> </span>{
                            <span class="hljs-comment">//就是判断next是否为null，默认next是head  表头</span>
                            <span class="hljs-keyword">return</span> next != <span class="hljs-keyword">null</span>;
                        }
                        <span class="hljs-comment">//nextNode() 就是迭代器里的next()方法 。</span>
                        <span class="hljs-comment">//该方法的实现可以看出，迭代LinkedHashMap，就是从内部维护的双链表的表头开始循环输出。</span>
                        <span class="hljs-keyword">final</span> LinkedHashMap.<span class="hljs-function">Entry&lt;K,V&gt; <span class="hljs-title">nextNode</span><span class="hljs-params">()</span> </span>{
                            <span class="hljs-comment">//记录要返回的e。</span>
                            LinkedHashMap.Entry&lt;K,V&gt; e = next;
                            <span class="hljs-comment">//判断fail-fast</span>
                            <span class="hljs-keyword">if</span> (modCount != expectedModCount)
                                <span class="hljs-keyword">throw</span> <span class="hljs-keyword">new</span> ConcurrentModificationException();
                            <span class="hljs-comment">//如果要返回的节点是null，异常</span>
                            <span class="hljs-keyword">if</span> (e == <span class="hljs-keyword">null</span>)
                                <span class="hljs-keyword">throw</span> <span class="hljs-keyword">new</span> NoSuchElementException();
                            <span class="hljs-comment">//更新当前节点为e</span>
                            current = e;
                            <span class="hljs-comment">//更新下一个节点是e的后置节点</span>
                            next = e.after;
                            <span class="hljs-comment">//返回e</span>
                            <span class="hljs-keyword">return</span> e;
                        }
                        <span class="hljs-comment">//删除方法 最终还是调用了HashMap的removeNode方法</span>
                        <span class="hljs-function"><span class="hljs-keyword">public</span> <span class="hljs-keyword">final</span> <span class="hljs-keyword">void</span> <span class="hljs-title">remove</span><span class="hljs-params">()</span> </span>{
                            Node&lt;K,V&gt; p = current;
                            <span class="hljs-keyword">if</span> (p == <span class="hljs-keyword">null</span>)
                                <span class="hljs-keyword">throw</span> <span class="hljs-keyword">new</span> IllegalStateException();
                            <span class="hljs-keyword">if</span> (modCount != expectedModCount)
                                <span class="hljs-keyword">throw</span> <span class="hljs-keyword">new</span> ConcurrentModificationException();
                            current = <span class="hljs-keyword">null</span>;
                            K key = p.key;
                            removeNode(hash(key), key, <span class="hljs-keyword">null</span>, <span class="hljs-keyword">false</span>, <span class="hljs-keyword">false</span>);
                            expectedModCount = modCount;
                        }
                    }
                    
                </code></pre>
                
               值得注意的就是：nextNode() 就是迭代器里的next()方法 。
               该方法的实现可以看出，迭代LinkedHashMap，就是从内部维护的双链表的表头开始循环输出。
               而双链表节点的顺序在LinkedHashMap的增、删、改、查时都会更新。以满足按照插入顺序输出，还是访问顺序输出。
               
               #### 总结：
               
               * LinkedHashMap相对于HashMap的源码比，是很简单的。因为大树底下好乘凉。它继承了HashMap，仅重写了几个方法，以改变它迭代遍历时的顺序。这也是其与HashMap相比最大的不同。
                 在每次插入数据，或者访问、修改数据时，会增加节点、或调整链表的节点顺序。以决定迭代时输出的顺序。
               
               * accessOrder ,默认是false，则迭代时输出的顺序是插入节点的顺序。若为true，则输出的顺序是按照访问节点的顺序。为true时，可以在这基础之上构建一个LruCache.
               
               * LinkedHashMap并没有重写任何put方法。但是其重写了构建新节点的newNode()方法.在每次构建新节点时，将新节点链接在内部双向链表的尾部
               
               * accessOrder=true的模式下,在afterNodeAccess()函数中，会将当前被访问到的节点e，移动至内部的双向链表的尾部。值得注意的是，afterNodeAccess()函数中，会修改modCount,因此当你正在accessOrder=true的模式下,迭代LinkedHashMap时，如果同时查询访问数据，也会导致fail-fast，因为迭代的顺序已经改变。
               
               * nextNode() 就是迭代器里的next()方法 。
               
               * 该方法的实现可以看出，迭代LinkedHashMap，就是从内部维护的双链表的表头开始循环输出。
                 而双链表节点的顺序在LinkedHashMap的增、删、改、查时都会更新。以满足按照插入顺序输出，还是访问顺序输出。
                 
               * 它与HashMap比，还有一个小小的优化，重写了containsValue()方法，直接遍历内部链表去比对value值是否相等。
               
               * 那么，还有最后一个小问题？为什么它不重写containsKey()方法，也去循环比对内部链表的key是否相等呢？
               
               [参考：LinkedHashMap源码解析（JDK8）](https://www.jianshu.com/p/8724a055289b)
   * Android  
         
       * ArrayMap：  
       
            > 讲解思路： 概括 -> 构造函数 -> API调用（增、删、改、查）
            
            概括的说，ArrayMap 实现了implements Map<K, V>接口，所以它也是一个关联数组、哈希表。存储以key->value 结构形式的数据。它也是线程不安全的，允许key为null,value为null。
            
            它相比HashMap，空间效率更高。
            
            它的内部实现是基于两个数组。
            一个int[]数组，用于保存每个item的hashCode.
            一个Object[]数组，保存key/value键值对。容量是上一个数组的两倍。
            它可以避免在将数据插入Map中时额外的空间消耗（对比HashMap）。
            而且它扩容的更合适，扩容时只需要数组拷贝工作，不需要重建哈希表。
            和HashMap相比，它不仅有扩容功能，在删除时，如果集合剩余元素少于一定阈值，还有收缩（shrunk）功能。减少空间占用。
            
            <div>
                <img src="https://upload-images.jianshu.io/upload_images/1696338-41b74ec253bba579?imageMogr2/auto-orient/strip%7CimageView2/2/w/388" />
            </div>
            
            但是它不适合大容量的数据存储。存储大量数据时，它的性能将退化至少50%。
            比传统的HashMap时间效率低。
            因为其会对key使用二分法进行从小到大排序，
            在添加、删除、查找数据的时候都是先使用二分查找法得到相应的index，然后通过index来进行添加、查找、删除等操作。
            所以其是按照key的排序存储的。
            
            <p>适用场景：</p>
            
            * 数据量不大
            
            * 空间比时间重要</p>
            
            * 需要使用Map</p>
            
            * <p>在Android平台，相对来说，内存容量更宝贵。而且数据量不大。所以当需要使用key是Object类型的Map时，可以考虑使用ArrayMap来替换HashMap</p>
                
            示例代码：
                
            <pre class="hljs cpp"><code class="cpp">        Map&lt;String, String&gt; <span class="hljs-built_in">map</span> = <span class="hljs-keyword">new</span> ArrayMap&lt;&gt;();
                    <span class="hljs-built_in">map</span>.put(<span class="hljs-string">"1"</span>,<span class="hljs-string">"1"</span>);
                    <span class="hljs-built_in">map</span>.put(null,<span class="hljs-string">"2"</span>);
                    <span class="hljs-built_in">map</span>.put(<span class="hljs-string">"3"</span>,null);
                    <span class="hljs-built_in">map</span>.put(<span class="hljs-string">"6"</span>,null);
                    <span class="hljs-built_in">map</span>.put(<span class="hljs-string">"5"</span>,null);
                    <span class="hljs-built_in">map</span>.put(<span class="hljs-string">"4"</span>,null);
                    Log.d(<span class="hljs-string">"TAG"</span>, <span class="hljs-string">"onCreate() called with: map = ["</span> + <span class="hljs-built_in">map</span> + <span class="hljs-string">"]"</span>);
            </code></pre>
            
            <p>输出：</p>
            
            <pre class="hljs javascript"><code class="javascript"> onCreate() called <span class="hljs-keyword">with</span>: map = [{<span class="hljs-literal">null</span>=<span class="hljs-number">2</span>, <span class="hljs-number">1</span>=<span class="hljs-number">1</span>, <span class="hljs-number">3</span>=<span class="hljs-literal">null</span>, <span class="hljs-number">4</span>=<span class="hljs-literal">null</span>, <span class="hljs-number">5</span>=<span class="hljs-literal">null</span>, <span class="hljs-number">6</span>=<span class="hljs-literal">null</span>}]
            </code></pre>
            
            * 构造函数 
                
                <pre class="hljs cpp"><code class="cpp">    <span class="hljs-comment">//扩容默认的size， 4是相对效率较高的大小</span>
                    <span class="hljs-keyword">private</span> <span class="hljs-keyword">static</span> final <span class="hljs-keyword">int</span> BASE_SIZE = <span class="hljs-number">4</span>;
                    
                    <span class="hljs-comment">//表示集合是不可变的</span>
                    <span class="hljs-keyword">static</span> final <span class="hljs-keyword">int</span>[] EMPTY_IMMUTABLE_INTS = <span class="hljs-keyword">new</span> <span class="hljs-keyword">int</span>[<span class="hljs-number">0</span>];
                    
                    <span class="hljs-comment">//是否利用System.identityHashCode(key) 获取唯一HashCode模式。    </span>
                    final boolean mIdentityHashCode;
                    <span class="hljs-comment">//保存hash值的数组</span>
                    <span class="hljs-keyword">int</span>[] mHashes;
                    <span class="hljs-comment">//保存key/value的数组。</span>
                    Object[] mArray;
                    <span class="hljs-comment">//容量</span>
                    <span class="hljs-keyword">int</span> mSize;
                    
                    <span class="hljs-comment">//创建一个空的ArrayMap，默认容量是0.当有Item被添加进来，会自动扩容</span>
                    <span class="hljs-function"><span class="hljs-keyword">public</span> <span class="hljs-title">ArrayMap</span><span class="hljs-params">()</span> </span>{
                        <span class="hljs-keyword">this</span>(<span class="hljs-number">0</span>, <span class="hljs-literal">false</span>);
                    }
                    <span class="hljs-comment">//创建一个指定容量的ArrayMap</span>
                    <span class="hljs-function"><span class="hljs-keyword">public</span> <span class="hljs-title">ArrayMap</span><span class="hljs-params">(<span class="hljs-keyword">int</span> capacity)</span> </span>{
                        <span class="hljs-keyword">this</span>(capacity, <span class="hljs-literal">false</span>);
                    }
                    <span class="hljs-comment">//指定容量和identityHashCode</span>
                    <span class="hljs-function"><span class="hljs-keyword">public</span> <span class="hljs-title">ArrayMap</span><span class="hljs-params">(<span class="hljs-keyword">int</span> capacity, boolean identityHashCode)</span> </span>{
                        mIdentityHashCode = identityHashCode;
                        <span class="hljs-comment">//数量&lt;  0，构建一个不可变的ArrayMap</span>
                        <span class="hljs-keyword">if</span> (capacity &lt; <span class="hljs-number">0</span>) {
                            mHashes = EMPTY_IMMUTABLE_INTS;
                            mArray = EmptyArray.OBJECT;
                            <span class="hljs-comment">//数量= 0，构建空的mHashes mArray</span>
                        } <span class="hljs-keyword">else</span> <span class="hljs-keyword">if</span> (capacity == <span class="hljs-number">0</span>) {
                            mHashes = EmptyArray.INT;
                            mArray = EmptyArray.OBJECT;
                        } <span class="hljs-keyword">else</span> {<span class="hljs-comment">//数量&gt;0,分配空间初始化数组</span>
                            allocArrays(capacity);
                        }
                        mSize = <span class="hljs-number">0</span>;
                    }
                        <span class="hljs-comment">//扩容</span>
                        <span class="hljs-function"><span class="hljs-keyword">private</span> <span class="hljs-keyword">void</span> <span class="hljs-title">allocArrays</span><span class="hljs-params">(final <span class="hljs-keyword">int</span> size)</span> </span>{
                        <span class="hljs-comment">//数量&lt;  0，构建一个不可变的ArrayMap</span>
                        <span class="hljs-keyword">if</span> (mHashes == EMPTY_IMMUTABLE_INTS) {
                            <span class="hljs-keyword">throw</span> <span class="hljs-keyword">new</span> UnsupportedOperationException(<span class="hljs-string">"ArrayMap is immutable"</span>);
                        }<span class="hljs-comment">//扩容数量是 8</span>
                        <span class="hljs-keyword">if</span> (size == (BASE_SIZE*<span class="hljs-number">2</span>)) {
                            synchronized (ArrayMap.class) {
                                <span class="hljs-comment">//查看之前是否有缓存的 容量为8的int[]数组和容量为16的object[]数组 </span>
                                <span class="hljs-comment">//如果有，复用给mArray mHashes</span>
                                <span class="hljs-keyword">if</span> (mTwiceBaseCache != null) {
                                    final Object[] <span class="hljs-built_in">array</span> = mTwiceBaseCache;
                                    mArray = <span class="hljs-built_in">array</span>;
                                    mTwiceBaseCache = (Object[])<span class="hljs-built_in">array</span>[<span class="hljs-number">0</span>];
                                    mHashes = (<span class="hljs-keyword">int</span>[])<span class="hljs-built_in">array</span>[<span class="hljs-number">1</span>];
                                    <span class="hljs-built_in">array</span>[<span class="hljs-number">0</span>] = <span class="hljs-built_in">array</span>[<span class="hljs-number">1</span>] = null;
                                    mTwiceBaseCacheSize--;
                                    <span class="hljs-keyword">if</span> (DEBUG) Log.d(TAG, <span class="hljs-string">"Retrieving 2x cache "</span> + mHashes
                                            + <span class="hljs-string">" now have "</span> + mTwiceBaseCacheSize + <span class="hljs-string">" entries"</span>);
                                    <span class="hljs-keyword">return</span>;
                                }
                            }
                        } <span class="hljs-keyword">else</span> <span class="hljs-keyword">if</span> (size == BASE_SIZE) {<span class="hljs-comment">//扩容数量是4</span>
                            synchronized (ArrayMap.class) {
                                <span class="hljs-comment">//查看之前是否有缓存的 容量为4的int[]数组和容量为8的object[]数组 </span>
                                <span class="hljs-comment">//如果有，复用给mArray mHashes</span>
                                <span class="hljs-keyword">if</span> (mBaseCache != null) {
                                    final Object[] <span class="hljs-built_in">array</span> = mBaseCache;
                                    mArray = <span class="hljs-built_in">array</span>;
                                    mBaseCache = (Object[])<span class="hljs-built_in">array</span>[<span class="hljs-number">0</span>];
                                    mHashes = (<span class="hljs-keyword">int</span>[])<span class="hljs-built_in">array</span>[<span class="hljs-number">1</span>];
                                    <span class="hljs-built_in">array</span>[<span class="hljs-number">0</span>] = <span class="hljs-built_in">array</span>[<span class="hljs-number">1</span>] = null;
                                    mBaseCacheSize--;
                                    <span class="hljs-keyword">if</span> (DEBUG) Log.d(TAG, <span class="hljs-string">"Retrieving 1x cache "</span> + mHashes
                                            + <span class="hljs-string">" now have "</span> + mBaseCacheSize + <span class="hljs-string">" entries"</span>);
                                    <span class="hljs-keyword">return</span>;
                                }
                            }
                        }
                        <span class="hljs-comment">//构建mHashes和mArray，mArray是mHashes的两倍。因为它既要存key还要存value。</span>
                        mHashes = <span class="hljs-keyword">new</span> <span class="hljs-keyword">int</span>[size];
                        mArray = <span class="hljs-keyword">new</span> Object[size&lt;&lt;<span class="hljs-number">1</span>];
                    }
                    <span class="hljs-comment">//利用另一个map构建ArrayMap</span>
                    <span class="hljs-function"><span class="hljs-keyword">public</span> <span class="hljs-title">ArrayMap</span><span class="hljs-params">(ArrayMap&lt;K, V&gt; <span class="hljs-built_in">map</span>)</span> </span>{
                        <span class="hljs-keyword">this</span>();
                        <span class="hljs-keyword">if</span> (<span class="hljs-built_in">map</span> != null) {
                            putAll(<span class="hljs-built_in">map</span>);
                        }
                    }
                    <span class="hljs-comment">//批量put方法：</span>
                    <span class="hljs-function"><span class="hljs-keyword">public</span> <span class="hljs-keyword">void</span> <span class="hljs-title">putAll</span><span class="hljs-params">(ArrayMap&lt;? extends K, ? extends V&gt; <span class="hljs-built_in">array</span>)</span> </span>{
                        final <span class="hljs-keyword">int</span> N = <span class="hljs-built_in">array</span>.mSize;
                        <span class="hljs-comment">//确保空间足够存放</span>
                        ensureCapacity(mSize + N);
                        <span class="hljs-comment">//如果当前是空集合，</span>
                        <span class="hljs-keyword">if</span> (mSize == <span class="hljs-number">0</span>) {
                            <span class="hljs-keyword">if</span> (N &gt; <span class="hljs-number">0</span>) {<span class="hljs-comment">//则直接复制覆盖数组内容即可。</span>
                                System.arraycopy(<span class="hljs-built_in">array</span>.mHashes, <span class="hljs-number">0</span>, mHashes, <span class="hljs-number">0</span>, N);
                                System.arraycopy(<span class="hljs-built_in">array</span>.mArray, <span class="hljs-number">0</span>, mArray, <span class="hljs-number">0</span>, N&lt;&lt;<span class="hljs-number">1</span>);
                                mSize = N;
                            }
                        } <span class="hljs-keyword">else</span> {<span class="hljs-comment">//否则需要一个一个执行插入put操作</span>
                            <span class="hljs-keyword">for</span> (<span class="hljs-keyword">int</span> i=<span class="hljs-number">0</span>; i&lt;N; i++) {
                                put(<span class="hljs-built_in">array</span>.keyAt(i), <span class="hljs-built_in">array</span>.valueAt(i));
                            }
                        }
                    }
                    <span class="hljs-comment">//确保空间足够存放 minimumCapacity 个数据</span>
                    <span class="hljs-function"><span class="hljs-keyword">public</span> <span class="hljs-keyword">void</span> <span class="hljs-title">ensureCapacity</span><span class="hljs-params">(<span class="hljs-keyword">int</span> minimumCapacity)</span> </span>{
                        <span class="hljs-comment">//如果不够扩容</span>
                        <span class="hljs-keyword">if</span> (mHashes.length &lt; minimumCapacity) {
                            <span class="hljs-comment">//暂存当前的hash array。后面复制需要</span>
                            final <span class="hljs-keyword">int</span>[] ohashes = mHashes;
                            final Object[] oarray = mArray;
                            <span class="hljs-comment">//扩容空间（开头讲过这个函数）</span>
                            allocArrays(minimumCapacity);
                            <span class="hljs-keyword">if</span> (mSize &gt; <span class="hljs-number">0</span>) {<span class="hljs-comment">//如果原集合不为空，复制原数据到新数组中</span>
                                System.arraycopy(ohashes, <span class="hljs-number">0</span>, mHashes, <span class="hljs-number">0</span>, mSize);
                                System.arraycopy(oarray, <span class="hljs-number">0</span>, mArray, <span class="hljs-number">0</span>, mSize&lt;&lt;<span class="hljs-number">1</span>);
                            }
                            <span class="hljs-comment">//释放回收临时暂存数组空间</span>
                            freeArrays(ohashes, oarray, mSize);
                        }
                    }
                    <span class="hljs-comment">//释放回收临时暂存数组空间</span>
                    <span class="hljs-function"><span class="hljs-keyword">private</span> <span class="hljs-keyword">static</span> <span class="hljs-keyword">void</span> <span class="hljs-title">freeArrays</span><span class="hljs-params">(final <span class="hljs-keyword">int</span>[] hashes, final Object[] <span class="hljs-built_in">array</span>, final <span class="hljs-keyword">int</span> size)</span> </span>{
                        <span class="hljs-comment">//如果容量是8， 则将hashes 和array 缓存起来，以便下次使用</span>
                        <span class="hljs-keyword">if</span> (hashes.length == (BASE_SIZE*<span class="hljs-number">2</span>)) {
                            synchronized (ArrayMap.class) {
                                <span class="hljs-keyword">if</span> (mTwiceBaseCacheSize &lt; CACHE_SIZE) {
                                    <span class="hljs-comment">//0存，前一个缓存的cache</span>
                                    <span class="hljs-built_in">array</span>[<span class="hljs-number">0</span>] = mTwiceBaseCache;
                                    <span class="hljs-comment">//1 存 int[]数组</span>
                                    <span class="hljs-built_in">array</span>[<span class="hljs-number">1</span>] = hashes;
                                    <span class="hljs-comment">//2+ 元素置空 以便GC</span>
                                    <span class="hljs-keyword">for</span> (<span class="hljs-keyword">int</span> i=(size&lt;&lt;<span class="hljs-number">1</span>)<span class="hljs-number">-1</span>; i&gt;=<span class="hljs-number">2</span>; i--) {
                                        <span class="hljs-built_in">array</span>[i] = null;
                                    }
                                    <span class="hljs-comment">//更新缓存引用为array</span>
                                    mTwiceBaseCache = <span class="hljs-built_in">array</span>;
                                    <span class="hljs-comment">//增加缓存过的Array的数量</span>
                                    mTwiceBaseCacheSize++;
                                    <span class="hljs-keyword">if</span> (DEBUG) Log.d(TAG, <span class="hljs-string">"Storing 2x cache "</span> + <span class="hljs-built_in">array</span>
                                            + <span class="hljs-string">" now have "</span> + mTwiceBaseCacheSize + <span class="hljs-string">" entries"</span>);
                                }
                            }<span class="hljs-comment">//相同逻辑，只不过缓存的是int[] 容量为4的数组 </span>
                        } <span class="hljs-keyword">else</span> <span class="hljs-keyword">if</span> (hashes.length == BASE_SIZE) {
                            synchronized (ArrayMap.class) {
                                <span class="hljs-keyword">if</span> (mBaseCacheSize &lt; CACHE_SIZE) {
                                    <span class="hljs-built_in">array</span>[<span class="hljs-number">0</span>] = mBaseCache;
                                    <span class="hljs-built_in">array</span>[<span class="hljs-number">1</span>] = hashes;
                                    <span class="hljs-keyword">for</span> (<span class="hljs-keyword">int</span> i=(size&lt;&lt;<span class="hljs-number">1</span>)<span class="hljs-number">-1</span>; i&gt;=<span class="hljs-number">2</span>; i--) {
                                        <span class="hljs-built_in">array</span>[i] = null;
                                    }
                                    mBaseCache = <span class="hljs-built_in">array</span>;
                                    mBaseCacheSize++;
                                    <span class="hljs-keyword">if</span> (DEBUG) Log.d(TAG, <span class="hljs-string">"Storing 1x cache "</span> + <span class="hljs-built_in">array</span>
                                            + <span class="hljs-string">" now have "</span> + mBaseCacheSize + <span class="hljs-string">" entries"</span>);
                                }
                            }
                        }
                    }
                </code></pre>
                
                #### 小结：
                
                >  扩容时，会查看之前是否有缓存的 int[]数组和object[]数组；如果有，复用给mArray mHashes
                
            * 增 、改
            
                * 单个增改 put(K key, V value)
                
                    <pre class="hljs java"><code class="java">    <span class="hljs-comment">//如果key存在，则返回oldValue</span>
                        <span class="hljs-function"><span class="hljs-keyword">public</span> V <span class="hljs-title">put</span><span class="hljs-params">(K key, V value)</span> </span>{
                            <span class="hljs-comment">//key的hash值</span>
                            <span class="hljs-keyword">final</span> <span class="hljs-keyword">int</span> hash;
                            <span class="hljs-comment">//下标</span>
                            <span class="hljs-keyword">int</span> index;
                            <span class="hljs-comment">// 如果key为null，则hash值为0.</span>
                            <span class="hljs-keyword">if</span> (key == <span class="hljs-keyword">null</span>) {
                                hash = <span class="hljs-number">0</span>;
                                <span class="hljs-comment">//寻找null的下标</span>
                                index = indexOfNull();
                            } <span class="hljs-keyword">else</span> {
                                <span class="hljs-comment">//根据mIdentityHashCode 取到 hash值</span>
                                hash = mIdentityHashCode ? System.identityHashCode(key) : key.hashCode();
                                <span class="hljs-comment">//根据hash值和key 找到合适的index</span>
                                index = indexOf(key, hash);
                            }
                            <span class="hljs-comment">//如果index&gt;=0,说明是替换（改）操作</span>
                            <span class="hljs-keyword">if</span> (index &gt;= <span class="hljs-number">0</span>) {
                                <span class="hljs-comment">//只需要更新value 不需要更新key。因为key已经存在</span>
                                index = (index&lt;&lt;<span class="hljs-number">1</span>) + <span class="hljs-number">1</span>;
                                <span class="hljs-comment">//返回旧值</span>
                                <span class="hljs-keyword">final</span> V old = (V)mArray[index];
                                mArray[index] = value;
                                <span class="hljs-keyword">return</span> old;
                            }
                            <span class="hljs-comment">//index&lt;0,说明是插入操作。 对其取反，得到应该插入的下标</span>
                            index = ~index;
                            <span class="hljs-comment">//如果需要扩容</span>
                            <span class="hljs-keyword">if</span> (mSize &gt;= mHashes.length) {
                                <span class="hljs-comment">//如果容量大于8，则扩容一半。</span>
                                <span class="hljs-comment">//否则容量大于4，则扩容到8.</span>
                                <span class="hljs-comment">//否则扩容到4</span>
                                <span class="hljs-keyword">final</span> <span class="hljs-keyword">int</span> n = mSize &gt;= (BASE_SIZE*<span class="hljs-number">2</span>) ? (mSize+(mSize&gt;&gt;<span class="hljs-number">1</span>))
                                        : (mSize &gt;= BASE_SIZE ? (BASE_SIZE*<span class="hljs-number">2</span>) : BASE_SIZE);
                                <span class="hljs-comment">//临时数组</span>
                                <span class="hljs-keyword">final</span> <span class="hljs-keyword">int</span>[] ohashes = mHashes;
                                <span class="hljs-keyword">final</span> Object[] oarray = mArray;
                                <span class="hljs-comment">//分配空间完成扩容</span>
                                allocArrays(n);
                                <span class="hljs-comment">//复制临时数组中的数组进新数组</span>
                                <span class="hljs-keyword">if</span> (mHashes.length &gt; <span class="hljs-number">0</span>) {
                                    <span class="hljs-keyword">if</span> (DEBUG) Log.d(TAG, <span class="hljs-string">"put: copy 0-"</span> + mSize + <span class="hljs-string">" to 0"</span>);
                                    System.arraycopy(ohashes, <span class="hljs-number">0</span>, mHashes, <span class="hljs-number">0</span>, ohashes.length);
                                    System.arraycopy(oarray, <span class="hljs-number">0</span>, mArray, <span class="hljs-number">0</span>, oarray.length);
                                }
                                <span class="hljs-comment">//释放临时数组空间</span>
                                freeArrays(ohashes, oarray, mSize);
                            }
                            <span class="hljs-comment">//如果index在中间，则需要移动数组，腾出中间的位置</span>
                            <span class="hljs-keyword">if</span> (index &lt; mSize) {
                                <span class="hljs-keyword">if</span> (DEBUG) Log.d(TAG, <span class="hljs-string">"put: move "</span> + index + <span class="hljs-string">"-"</span> + (mSize-index)
                                        + <span class="hljs-string">" to "</span> + (index+<span class="hljs-number">1</span>));
                                System.arraycopy(mHashes, index, mHashes, index + <span class="hljs-number">1</span>, mSize - index);
                                System.arraycopy(mArray, index &lt;&lt; <span class="hljs-number">1</span>, mArray, (index + <span class="hljs-number">1</span>) &lt;&lt; <span class="hljs-number">1</span>, (mSize - index) &lt;&lt; <span class="hljs-number">1</span>);
                            }
                            <span class="hljs-comment">//hash数组，就按照下标存哈希值</span>
                            mHashes[index] = hash;
                            <span class="hljs-comment">//array数组，根据下标，乘以2存key，乘以2+1 存value</span>
                            mArray[index&lt;&lt;<span class="hljs-number">1</span>] = key;
                            mArray[(index&lt;&lt;<span class="hljs-number">1</span>)+<span class="hljs-number">1</span>] = value;
                            mSize++;<span class="hljs-comment">//修改size</span>
                            <span class="hljs-keyword">return</span> <span class="hljs-keyword">null</span>;
                        }
                        
                        <span class="hljs-comment">//返回key为null的 下标index</span>
                        <span class="hljs-function"><span class="hljs-keyword">int</span> <span class="hljs-title">indexOfNull</span><span class="hljs-params">()</span> </span>{
                            <span class="hljs-comment">//N为当前集合size </span>
                            <span class="hljs-keyword">final</span> <span class="hljs-keyword">int</span> N = mSize;
                            <span class="hljs-comment">//如果当前集合是空的，返回~0</span>
                            <span class="hljs-keyword">if</span> (N == <span class="hljs-number">0</span>) {<span class="hljs-comment">//</span>
                                <span class="hljs-keyword">return</span> ~<span class="hljs-number">0</span>;
                            }
                            <span class="hljs-comment">//根据hash值=0，通过二分查找，查找到目标index</span>
                            <span class="hljs-keyword">int</span> index = ContainerHelpers.binarySearch(mHashes, N, <span class="hljs-number">0</span>);
                            <span class="hljs-comment">//如果index《0，则hash值=0之前没有存储过数据</span>
                            <span class="hljs-keyword">if</span> (index &lt; <span class="hljs-number">0</span>) {
                                <span class="hljs-keyword">return</span> index;
                            }
                            <span class="hljs-comment">//如果index&gt;=0,说明该hash值，之前存储过数据，找到对应的key，比对key是否等于null。相等的话，返回index。说明要替换。  </span>
                            <span class="hljs-comment">//关于array中对应数据的位置，是index*2 = key ,index*2+1 = value.</span>
                            <span class="hljs-keyword">if</span> (<span class="hljs-keyword">null</span> == mArray[index&lt;&lt;<span class="hljs-number">1</span>]) {
                                <span class="hljs-keyword">return</span> index;
                            }
                            <span class="hljs-comment">//以下两个for循环是在出现hash冲突的情况下，找到正确的index的过程：</span>
                            <span class="hljs-comment">//从index+1,遍历到数组末尾，找到hash值相等，且key相等的位置，返回</span>
                            <span class="hljs-keyword">int</span> end;
                            <span class="hljs-keyword">for</span> (end = index + <span class="hljs-number">1</span>; end &lt; N &amp;&amp; mHashes[end] == <span class="hljs-number">0</span>; end++) {
                                <span class="hljs-keyword">if</span> (<span class="hljs-keyword">null</span> == mArray[end &lt;&lt; <span class="hljs-number">1</span>]) <span class="hljs-keyword">return</span> end;
                            }
                            <span class="hljs-comment">//从index-1,遍历到数组头，找到hash值相等，且key相等的位置，返回</span>
                            <span class="hljs-keyword">for</span> (<span class="hljs-keyword">int</span> i = index - <span class="hljs-number">1</span>; i &gt;= <span class="hljs-number">0</span> &amp;&amp; mHashes[i] == <span class="hljs-number">0</span>; i--) {
                                <span class="hljs-keyword">if</span> (<span class="hljs-keyword">null</span> == mArray[i &lt;&lt; <span class="hljs-number">1</span>]) <span class="hljs-keyword">return</span> i;
                            }
                            <span class="hljs-comment">// key没有找到，返回一个负数。代表应该插入的位置</span>
                            <span class="hljs-keyword">return</span> ~end;
                        }
                        <span class="hljs-comment">//根据key和key的hash值，返回index</span>
                        <span class="hljs-function"><span class="hljs-keyword">int</span> <span class="hljs-title">indexOf</span><span class="hljs-params">(Object key, <span class="hljs-keyword">int</span> hash)</span> </span>{
                            <span class="hljs-comment">//N为当前集合size </span>
                            <span class="hljs-keyword">final</span> <span class="hljs-keyword">int</span> N = mSize;
                            <span class="hljs-comment">//如果当前集合是空的，返回~0</span>
                            <span class="hljs-keyword">if</span> (N == <span class="hljs-number">0</span>) {
                                <span class="hljs-keyword">return</span> ~<span class="hljs-number">0</span>;
                            }
                            <span class="hljs-comment">//根据hash值，通过二分查找，查找到目标index</span>
                            <span class="hljs-keyword">int</span> index = ContainerHelpers.binarySearch(mHashes, N, hash);
                            <span class="hljs-comment">//如果index《0，说明该hash值之前没有存储过数据</span>
                            <span class="hljs-keyword">if</span> (index &lt; <span class="hljs-number">0</span>) {
                                <span class="hljs-keyword">return</span> index;
                            }
                            <span class="hljs-comment">//如果index&gt;=0,说明该hash值，之前存储过数据，找到对应的key，比对key是否相等。相等的话，返回index。说明要替换。</span>
                            <span class="hljs-keyword">if</span> (key.equals(mArray[index&lt;&lt;<span class="hljs-number">1</span>])) {
                                <span class="hljs-keyword">return</span> index;
                            }
                            <span class="hljs-comment">//以下两个for循环是在出现hash冲突的情况下，找到正确的index的过程：</span>
                            <span class="hljs-comment">//从index+1,遍历到数组末尾，找到hash值相等，且key相等的位置，返回</span>
                            <span class="hljs-keyword">int</span> end;
                            <span class="hljs-keyword">for</span> (end = index + <span class="hljs-number">1</span>; end &lt; N &amp;&amp; mHashes[end] == hash; end++) {
                                <span class="hljs-keyword">if</span> (key.equals(mArray[end &lt;&lt; <span class="hljs-number">1</span>])) <span class="hljs-keyword">return</span> end;
                            }
                    
                            <span class="hljs-comment">//从index-1,遍历到数组头，找到hash值相等，且key相等的位置，返回</span>
                            <span class="hljs-keyword">for</span> (<span class="hljs-keyword">int</span> i = index - <span class="hljs-number">1</span>; i &gt;= <span class="hljs-number">0</span> &amp;&amp; mHashes[i] == hash; i--) {
                                <span class="hljs-keyword">if</span> (key.equals(mArray[i &lt;&lt; <span class="hljs-number">1</span>])) <span class="hljs-keyword">return</span> i;
                            }
                            <span class="hljs-comment">// key没有找到，返回一个负数。代表应该插入的位置</span>
                            <span class="hljs-keyword">return</span> ~end;
                        }
                    </code></pre>
                    
                * 批量增 putAll(Map<? extends K, ? extends V> map)
                    
                    除了上一张介绍过的public void putAll(ArrayMap<? extends K, ? extends V> array),还有一个批量增的方法：
                    
                    <pre class="hljs cpp"><code class="cpp">    <span class="hljs-comment">//批量增，接受更为广泛的Map参数</span>
                        <span class="hljs-function"><span class="hljs-keyword">public</span> <span class="hljs-keyword">void</span> <span class="hljs-title">putAll</span><span class="hljs-params">(Map&lt;? extends K, ? extends V&gt; <span class="hljs-built_in">map</span>)</span> </span>{
                            <span class="hljs-comment">//确保空间容量足够</span>
                            ensureCapacity(mSize + <span class="hljs-built_in">map</span>.size());
                            <span class="hljs-keyword">for</span> (Map.Entry&lt;? extends K, ? extends V&gt; entry : <span class="hljs-built_in">map</span>.entrySet()) {
                                <span class="hljs-comment">//分别调用单个增方法 add</span>
                                put(entry.getKey(), entry.getValue());
                            }
                        }
                    </code></pre>
                    
                    <pre class="hljs cpp"><code class="cpp">    <span class="hljs-comment">//批量增，接受更为广泛的Map参数</span>
                        <span class="hljs-function"><span class="hljs-keyword">public</span> <span class="hljs-keyword">void</span> <span class="hljs-title">putAll</span><span class="hljs-params">(Map&lt;? extends K, ? extends V&gt; <span class="hljs-built_in">map</span>)</span> </span>{
                            <span class="hljs-comment">//确保空间容量足够</span>
                            ensureCapacity(mSize + <span class="hljs-built_in">map</span>.size());
                            <span class="hljs-keyword">for</span> (Map.Entry&lt;? extends K, ? extends V&gt; entry : <span class="hljs-built_in">map</span>.entrySet()) {
                                <span class="hljs-comment">//分别调用单个增方法 add</span>
                                put(entry.getKey(), entry.getValue());
                            }
                        }
                    </code></pre>
                    
                    #### 小结：
                    
                    * 增的流程：1 先根据key得到hash值，2 根据hash值得到index 3 根据index正负，得知是插入还是替换 4 如果是替换直接替换值即可 5 如果是插入，则先判断是否需要扩容，并进行扩容 6 挪动数组位置，插入元素（类似ArrayList）
                    
                    * 插入允许key为null，value为null。
                    
                    * 每次插入时，根据key的哈希值，利用二分查找，去寻找key在int[] mHashes数组中的下标位置。
                    
                    * 如果出现了hash冲突，则从需要从目标点向两头遍历，找到正确的index。
                    
                    * 如果index>=0,说明之前已经存在该key，需要替换（改）。
                    
                    * 如果index<0,说明没有找到。（也是二分法特性）对index去反，可以得到这个index应该插入的位置。
                    
                    * 根据key的hash值在mHashs中的index，如何得到key、value在mArray中的下标位置呢？key的位置是index*2，value的位置是index*2+1,也就是说mArray是利用连续的两位空间去存放key、value。
                    
                    * 根据hash值的index计算，key、value的index也利用了位运算。index<<1 和 (index<<1)+1
            * 删 
                
                * 单个删                   
                    
                    <pre class="hljs java"><code class="java">    <span class="hljs-comment">//如果对应key有元素存在，返回value。否则返回null</span>
                        <span class="hljs-function"><span class="hljs-keyword">public</span> V <span class="hljs-title">remove</span><span class="hljs-params">(Object key)</span> </span>{
                            <span class="hljs-comment">//根据key，找到下标</span>
                            <span class="hljs-keyword">final</span> <span class="hljs-keyword">int</span> index = indexOfKey(key);
                            <span class="hljs-keyword">if</span> (index &gt;= <span class="hljs-number">0</span>) {
                                <span class="hljs-comment">//如果index&gt;=0,说明key有对应的元素存在，则去根据下标删除</span>
                                <span class="hljs-keyword">return</span> removeAt(index);
                            }
                            <span class="hljs-comment">//否则返回null</span>
                            <span class="hljs-keyword">return</span> <span class="hljs-keyword">null</span>;
                        }
                    </code></pre>
                    
                    <pre class="hljs java"><code class="java">    <span class="hljs-comment">//根据下标删除元素</span>
                        <span class="hljs-function"><span class="hljs-keyword">public</span> V <span class="hljs-title">removeAt</span><span class="hljs-params">(<span class="hljs-keyword">int</span> index)</span> </span>{
                            <span class="hljs-comment">//根据index，得到value</span>
                            <span class="hljs-keyword">final</span> Object old = mArray[(index &lt;&lt; <span class="hljs-number">1</span>) + <span class="hljs-number">1</span>];
                            <span class="hljs-comment">//如果之前的集合长度小于等于1，则执行过删除操作后，集合现在就是空的了</span>
                            <span class="hljs-keyword">if</span> (mSize &lt;= <span class="hljs-number">1</span>) {
                                <span class="hljs-comment">// Now empty.</span>
                                <span class="hljs-keyword">if</span> (DEBUG) Log.d(TAG, <span class="hljs-string">"remove: shrink from "</span> + mHashes.length + <span class="hljs-string">" to 0"</span>);
                                <span class="hljs-comment">//释放回收空间</span>
                                freeArrays(mHashes, mArray, mSize);
                                <span class="hljs-comment">//置空</span>
                                mHashes = EmptyArray.INT;
                                mArray = EmptyArray.OBJECT;
                                mSize = <span class="hljs-number">0</span>;
                            } <span class="hljs-keyword">else</span> {<span class="hljs-comment">//根据元素数量和集合占用的空间情况，判断是否要执行收缩操作</span>
                                <span class="hljs-comment">//如果 mHashes长度大于8，且 集合长度 小于当前空间的 1/3,则执行一个 shrunk，收缩操作，避免空间的浪费</span>
                                <span class="hljs-keyword">if</span> (mHashes.length &gt; (BASE_SIZE*<span class="hljs-number">2</span>) &amp;&amp; mSize &lt; mHashes.length/<span class="hljs-number">3</span>) {
                                    <span class="hljs-comment">// Shrunk enough to reduce size of arrays.  We dont allow it to</span>
                                    <span class="hljs-comment">// shrink smaller than (BASE_SIZE*2) to avoid flapping between</span>
                                    <span class="hljs-comment">// that and BASE_SIZE.</span>
                                    <span class="hljs-comment">//如果当前集合长度大于8，则n为当前集合长度的1.5倍。否则n为8.</span>
                                    <span class="hljs-comment">//n 为收缩后的 mHashes长度</span>
                                    <span class="hljs-keyword">final</span> <span class="hljs-keyword">int</span> n = mSize &gt; (BASE_SIZE*<span class="hljs-number">2</span>) ? (mSize + (mSize&gt;&gt;<span class="hljs-number">1</span>)) : (BASE_SIZE*<span class="hljs-number">2</span>);
                    
                                    <span class="hljs-keyword">if</span> (DEBUG) Log.d(TAG, <span class="hljs-string">"remove: shrink from "</span> + mHashes.length + <span class="hljs-string">" to "</span> + n);
                                    <span class="hljs-comment">//分配新的更小的空间（收缩操作）</span>
                                    <span class="hljs-keyword">final</span> <span class="hljs-keyword">int</span>[] ohashes = mHashes;
                                    <span class="hljs-keyword">final</span> Object[] oarray = mArray;
                                    allocArrays(n);
                                    <span class="hljs-comment">//删掉一个元素，所以修改集合元素数量</span>
                                    mSize--;
                                    <span class="hljs-comment">//因为执行了收缩操作，所以要将老数据复制到新数组中。</span>
                                    <span class="hljs-keyword">if</span> (index &gt; <span class="hljs-number">0</span>) {
                                        <span class="hljs-keyword">if</span> (DEBUG) Log.d(TAG, <span class="hljs-string">"remove: copy from 0-"</span> + index + <span class="hljs-string">" to 0"</span>);
                                        System.arraycopy(ohashes, <span class="hljs-number">0</span>, mHashes, <span class="hljs-number">0</span>, index);
                                        System.arraycopy(oarray, <span class="hljs-number">0</span>, mArray, <span class="hljs-number">0</span>, index &lt;&lt; <span class="hljs-number">1</span>);
                                    }
                                    <span class="hljs-comment">//在复制的过程中，排除不复制当前要删除的元素即可。</span>
                                    <span class="hljs-keyword">if</span> (index &lt; mSize) {
                                        <span class="hljs-keyword">if</span> (DEBUG) Log.d(TAG, <span class="hljs-string">"remove: copy from "</span> + (index+<span class="hljs-number">1</span>) + <span class="hljs-string">"-"</span> + mSize
                                                + <span class="hljs-string">" to "</span> + index);
                                        System.arraycopy(ohashes, index + <span class="hljs-number">1</span>, mHashes, index, mSize - index);
                                        System.arraycopy(oarray, (index + <span class="hljs-number">1</span>) &lt;&lt; <span class="hljs-number">1</span>, mArray, index &lt;&lt; <span class="hljs-number">1</span>,
                                                (mSize - index) &lt;&lt; <span class="hljs-number">1</span>);
                                    }
                                } <span class="hljs-keyword">else</span> {<span class="hljs-comment">//不需要收缩</span>
                                    <span class="hljs-comment">//修改集合长度</span>
                                    mSize--;
                                    <span class="hljs-comment">//类似ArrayList，用复制操作去覆盖元素达到删除的目的。</span>
                                    <span class="hljs-keyword">if</span> (index &lt; mSize) {
                                        <span class="hljs-keyword">if</span> (DEBUG) Log.d(TAG, <span class="hljs-string">"remove: move "</span> + (index+<span class="hljs-number">1</span>) + <span class="hljs-string">"-"</span> + mSize
                                                + <span class="hljs-string">" to "</span> + index);
                                        System.arraycopy(mHashes, index + <span class="hljs-number">1</span>, mHashes, index, mSize - index);
                                        System.arraycopy(mArray, (index + <span class="hljs-number">1</span>) &lt;&lt; <span class="hljs-number">1</span>, mArray, index &lt;&lt; <span class="hljs-number">1</span>,
                                                (mSize - index) &lt;&lt; <span class="hljs-number">1</span>);
                                    }
                                    <span class="hljs-comment">//记得置空，以防内存泄漏</span>
                                    mArray[mSize &lt;&lt; <span class="hljs-number">1</span>] = <span class="hljs-keyword">null</span>;
                                    mArray[(mSize &lt;&lt; <span class="hljs-number">1</span>) + <span class="hljs-number">1</span>] = <span class="hljs-keyword">null</span>;
                                }
                            }
                            <span class="hljs-comment">//返回删除的值</span>
                            <span class="hljs-keyword">return</span> (V)old;
                        }
                    </code></pre>
                
                * 批量删
                
                    <pre class="hljs cpp"><code class="cpp">    <span class="hljs-comment">//从ArrayMap中，删除Collection集合中，所有出现的key。</span>
                        <span class="hljs-comment">//返回值代表是否成功删除元素</span>
                        <span class="hljs-function"><span class="hljs-keyword">public</span> boolean <span class="hljs-title">removeAll</span><span class="hljs-params">(Collection&lt;?&gt; collection)</span> </span>{
                            <span class="hljs-keyword">return</span> MapCollections.removeAllHelper(<span class="hljs-keyword">this</span>, collection);
                        }
                        <span class="hljs-comment">//MapCollections.removeAllHelper(this, collection);</span>
                        <span class="hljs-comment">//遍历Collection，调用Map.remove(key)去删除元素;</span>
                        <span class="hljs-keyword">public</span> <span class="hljs-keyword">static</span> &lt;K, V&gt; <span class="hljs-function">boolean <span class="hljs-title">removeAllHelper</span><span class="hljs-params">(Map&lt;K, V&gt; <span class="hljs-built_in">map</span>, Collection&lt;?&gt; collection)</span> </span>{
                            <span class="hljs-keyword">int</span> oldSize = <span class="hljs-built_in">map</span>.size();
                            Iterator&lt;?&gt; it = collection.iterator();
                            <span class="hljs-keyword">while</span> (it.hasNext()) {
                                <span class="hljs-built_in">map</span>.remove(it.next());
                            }
                            <span class="hljs-comment">//如果元素不等，说明成功删除元素</span>
                            <span class="hljs-keyword">return</span> oldSize != <span class="hljs-built_in">map</span>.size();
                        }
                    </code></pre>
                    
                    * 根据元素数量和集合占用的空间情况，判断是否要执行收缩操作
                    
                    * 类似ArrayList，用复制操作去覆盖元素达到删除的目的。
            
            * 查 
            
                当你想获取某个value的时候，ArrayMap会计算输入key转换过后的hash值，然后对hash数组使用二分查找法寻找到对应的index，然后我们可以通过这个index在另外一个数组中直接访问到需要的键值对。如果在第二个数组键值对中的key和前面输入的查询key不一致，那么就认为是发生了碰撞冲突。为了解决这个问题，我们会以该key为中心点，分别上下展开，逐个去对比查找，直到找到匹配的值。如下图所示：
                
                <div>
                    <img src="https://upload-images.jianshu.io/upload_images/1696338-ad1510c87e8375db?imageMogr2/auto-orient/strip%7CimageView2/2/w/502" />
                </div>
                
                随着数组中的对象越来越多，查找访问单个对象的花费也会跟着增长，这是在内存占用与访问时间之间做权衡交换。
                
                * 单个查 
                
                    <pre class="hljs java"><code class="java">    <span class="hljs-function"><span class="hljs-keyword">public</span> V <span class="hljs-title">get</span><span class="hljs-params">(Object key)</span> </span>{
                            <span class="hljs-comment">//根据key去得到index</span>
                            <span class="hljs-keyword">final</span> <span class="hljs-keyword">int</span> index = indexOfKey(key);
                            <span class="hljs-comment">//根据 index*2+1 得到value</span>
                            <span class="hljs-keyword">return</span> index &gt;= <span class="hljs-number">0</span> ? (V)mArray[(index&lt;&lt;<span class="hljs-number">1</span>)+<span class="hljs-number">1</span>] : <span class="hljs-keyword">null</span>;
                        }
                        <span class="hljs-function"><span class="hljs-keyword">public</span> <span class="hljs-keyword">int</span> <span class="hljs-title">indexOfKey</span><span class="hljs-params">(Object key)</span> </span>{
                            <span class="hljs-comment">//判断key是否是null，并去查询key对应的index</span>
                            <span class="hljs-keyword">return</span> key == <span class="hljs-keyword">null</span> ? indexOfNull()
                                    : indexOf(key, mIdentityHashCode ? System.identityHashCode(key) : key.hashCode());
                        }
                    </code></pre>
                    
            ####ArrayMap的实现细节很多地方和ArrayList很像，由于我们之前分析过面试必备：ArrayList源码解析（JDK8）。所以对于用数组复制覆盖去完成删除等操作的细节，就比较容易理解了。
            
            * 每次插入时，根据key的哈希值，利用二分查找，去寻找key在int[] mHashes数组中的下标位置。
            
            * 如果出现了hash冲突，则从需要从目标点向两头遍历，找到正确的index。
            
            * 扩容时，会查看之前是否有缓存的 int[]数组和object[]数组
            
            * 如果有，复用给mArray mHashes
            
            * 扩容规则：如果容量大于8，则扩容一半。（类似ArrayList）
            
            * 根据key的hash值在mHashs中的index，如何得到key、value在mArray中的下标位置呢？key的位置是index*2，value的位置是index*2+1,也就是说mArray是利用连续的两位空间去存放key、value。
            
            * 根据元素数量和集合占用的空间情况，判断是否要执行收缩操作
            
            * 如果 mHashes长度大于8，且 集合长度 小于当前空间的 1/3,则执行一个 shrunk，收缩操作，避免空间的浪费
              类似ArrayList，用复制操作去覆盖元素达到删除的目的。
            
            [参考：ArrayMap源码解析](https://www.jianshu.com/p/1fb660978b14)
               
       * SparseArray源码解析
            
         > 讲解思路 慨括 -> 构造方法 ->API(增、删、改、查)
         
            * 概括的说，SparseArray<E>是用于在Android平台上替代HashMap的数据结构,更具体的说，
              是用于替代key为int类型，value为Object类型的HashMap。
              和ArrayMap类似，它的实现相比于HashMap更加节省空间，而且由于key指定为int类型，也可以节省int-Integer的装箱拆箱操作带来的性能消耗。
              
              它仅仅实现了implements Cloneable接口，所以使用时不能用Map作为声明类型来使用。
              
              它也是线程不安全的，允许value为null。
              
            * 从原理上说，
            
              它的内部实现也是基于两个数组。
              一个int[]数组mKeys，用于保存每个item的key，key本身就是int类型，所以可以理解hashCode值就是key的值.
              一个Object[]数组mValues，保存value。容量和key数组的一样。
              
              类似ArrayMap,
              它扩容的更合适，扩容时只需要数组拷贝工作，不需要重建哈希表。
              
              同样它不适合大容量的数据存储。存储大量数据时，它的性能将退化至少50%。
              
              比传统的HashMap时间效率低。
              因为其会对key从小到大排序，使用二分法查询key对应在数组中的下标。
              在添加、删除、查找数据的时候都是先使用二分查找法得到相应的index，然后通过index来进行添加、查找、删除等操作。
              
              所以其是按照key的大小排序存储的。
              
              另外，SparseArray为了提升性能，在删除操作时做了一些优化：
              当删除一个元素时，并不是立即从value数组中删除它，并压缩数组，
              而是将其在value数组中标记为已删除。这样当存储相同的key的value时，可以重用这个空间。
              如果该空间没有被重用，随后将在合适的时机里执行gc（垃圾收集）操作，将数组压缩，以免浪费空间。
              
            * 适用场景：
            
              数据量不大（千以内）
              
              空间比时间重要
              
              需要使用Map，且key为int类型。
              
              示例代码： 
              
              <pre class="hljs javascript"><code class="javascript">        SparseArray&lt;<span class="hljs-built_in">String</span>&gt; stringSparseArray = <span class="hljs-keyword">new</span> SparseArray&lt;&gt;();
                      stringSparseArray.put(<span class="hljs-number">1</span>,<span class="hljs-string">"a"</span>);
                      stringSparseArray.put(<span class="hljs-number">5</span>,<span class="hljs-string">"e"</span>);
                      stringSparseArray.put(<span class="hljs-number">4</span>,<span class="hljs-string">"d"</span>);
                      stringSparseArray.put(<span class="hljs-number">10</span>,<span class="hljs-string">"h"</span>);
                      stringSparseArray.put(<span class="hljs-number">2</span>,<span class="hljs-literal">null</span>);
              
                      Log.d(TAG, <span class="hljs-string">"onCreate() called with: stringSparseArray = ["</span> + stringSparseArray + <span class="hljs-string">"]"</span>);
              </code></pre>
              
              输出：
              
              <pre class="hljs javascript"><code class="javascript"><span class="hljs-comment">//可以看出是按照key排序的</span>
              onCreate() called <span class="hljs-keyword">with</span>: stringSparseArray = [{<span class="hljs-number">1</span>=a, <span class="hljs-number">2</span>=<span class="hljs-literal">null</span>, <span class="hljs-number">4</span>=d, <span class="hljs-number">5</span>=e, <span class="hljs-number">10</span>=h}]
              </code></pre>
              
            * 构造函数
                
                <pre class="hljs java"><code class="java">    <span class="hljs-comment">//用于标记value数组，作为已经删除的标记</span>
                    <span class="hljs-keyword">private</span> <span class="hljs-keyword">static</span> <span class="hljs-keyword">final</span> Object DELETED = <span class="hljs-keyword">new</span> Object();
                    <span class="hljs-comment">//是否需要GC </span>
                    <span class="hljs-keyword">private</span> <span class="hljs-keyword">boolean</span> mGarbage = <span class="hljs-keyword">false</span>;
                    
                    <span class="hljs-comment">//存储key 的数组</span>
                    <span class="hljs-keyword">private</span> <span class="hljs-keyword">int</span>[] mKeys;
                    <span class="hljs-comment">//存储value 的数组</span>
                    <span class="hljs-keyword">private</span> Object[] mValues;
                    <span class="hljs-comment">//集合大小</span>
                    <span class="hljs-keyword">private</span> <span class="hljs-keyword">int</span> mSize;
                    
                    <span class="hljs-comment">//默认构造函数，初始化容量为10</span>
                    <span class="hljs-function"><span class="hljs-keyword">public</span> <span class="hljs-title">SparseArray</span><span class="hljs-params">()</span> </span>{
                        <span class="hljs-keyword">this</span>(<span class="hljs-number">10</span>);
                    }
                    <span class="hljs-comment">//指定初始容量</span>
                    <span class="hljs-function"><span class="hljs-keyword">public</span> <span class="hljs-title">SparseArray</span><span class="hljs-params">(<span class="hljs-keyword">int</span> initialCapacity)</span> </span>{
                        <span class="hljs-comment">//初始容量为0的话，就赋值两个轻量级的引用</span>
                        <span class="hljs-keyword">if</span> (initialCapacity == <span class="hljs-number">0</span>) {
                            mKeys = EmptyArray.INT;
                            mValues = EmptyArray.OBJECT;
                        } <span class="hljs-keyword">else</span> {
                        <span class="hljs-comment">//初始化对应长度的数组</span>
                            mValues = ArrayUtils.newUnpaddedObjectArray(initialCapacity);
                            mKeys = <span class="hljs-keyword">new</span> <span class="hljs-keyword">int</span>[mValues.length];
                        }
                        <span class="hljs-comment">//集合大小为0</span>
                        mSize = <span class="hljs-number">0</span>;
                    }
                </code></pre>
                
                构造函数 无亮点，路过。
                
                关注一下几个变量：
                
                底层数据结构为int[]和Object[]类型数组。
                
                mGarbage: 是否需要GC
                
                DELETED: 用于标记value数组，作为已经删除的标记
                
            * 增 、改
                
                * 单个增、改
                    
                    <pre class="hljs java"><code class="java">    <span class="hljs-function"><span class="hljs-keyword">public</span> <span class="hljs-keyword">void</span> <span class="hljs-title">put</span><span class="hljs-params">(<span class="hljs-keyword">int</span> key, E value)</span> </span>{
                            <span class="hljs-comment">//利用二分查找，找到 待插入key 的 下标index</span>
                            <span class="hljs-keyword">int</span> i = ContainerHelpers.binarySearch(mKeys, mSize, key);
                            <span class="hljs-comment">//如果返回的index是正数，说明之前这个key存在，直接覆盖value即可</span>
                            <span class="hljs-keyword">if</span> (i &gt;= <span class="hljs-number">0</span>) {
                                mValues[i] = value;
                            } <span class="hljs-keyword">else</span> {
                                <span class="hljs-comment">//若返回的index是负数，说明 key不存在.</span>
                                
                                <span class="hljs-comment">//先对返回的i取反，得到应该插入的位置i</span>
                                i = ~i;
                                <span class="hljs-comment">//如果i没有越界，且对应位置是已删除的标记，则复用这个空间</span>
                                <span class="hljs-keyword">if</span> (i &lt; mSize &amp;&amp; mValues[i] == DELETED) {
                                <span class="hljs-comment">//赋值后，返回</span>
                                    mKeys[i] = key;
                                    mValues[i] = value;
                                    <span class="hljs-keyword">return</span>;
                                }
                                
                                <span class="hljs-comment">//如果需要GC，且需要扩容</span>
                                <span class="hljs-keyword">if</span> (mGarbage &amp;&amp; mSize &gt;= mKeys.length) {
                                    <span class="hljs-comment">//先触发GC</span>
                                    gc();
                                    <span class="hljs-comment">//gc后，下标i可能发生变化，所以再次用二分查找找到应该插入的位置i</span>
                                    <span class="hljs-comment">// Search again because indices may have changed.</span>
                                    i = ~ContainerHelpers.binarySearch(mKeys, mSize, key);
                                }
                                <span class="hljs-comment">//插入key（可能需要扩容）</span>
                                mKeys = GrowingArrayUtils.insert(mKeys, mSize, i, key);
                                <span class="hljs-comment">//插入value（可能需要扩容）</span>
                                mValues = GrowingArrayUtils.insert(mValues, mSize, i, value);
                                <span class="hljs-comment">//集合大小递增</span>
                                mSize++;
                            }
                        }
                        <span class="hljs-comment">//二分查找 基础知识不再详解</span>
                        <span class="hljs-function"><span class="hljs-keyword">static</span> <span class="hljs-keyword">int</span> <span class="hljs-title">binarySearch</span><span class="hljs-params">(<span class="hljs-keyword">int</span>[] array, <span class="hljs-keyword">int</span> size, <span class="hljs-keyword">int</span> value)</span> </span>{
                            <span class="hljs-keyword">int</span> lo = <span class="hljs-number">0</span>;
                            <span class="hljs-keyword">int</span> hi = size - <span class="hljs-number">1</span>;
                    
                            <span class="hljs-keyword">while</span> (lo &lt;= hi) {
                                <span class="hljs-comment">//关注一下高效位运算</span>
                                <span class="hljs-keyword">final</span> <span class="hljs-keyword">int</span> mid = (lo + hi) &gt;&gt;&gt; <span class="hljs-number">1</span>;
                                <span class="hljs-keyword">final</span> <span class="hljs-keyword">int</span> midVal = array[mid];
                    
                                <span class="hljs-keyword">if</span> (midVal &lt; value) {
                                    lo = mid + <span class="hljs-number">1</span>;
                                } <span class="hljs-keyword">else</span> <span class="hljs-keyword">if</span> (midVal &gt; value) {
                                    hi = mid - <span class="hljs-number">1</span>;
                                } <span class="hljs-keyword">else</span> {
                                    <span class="hljs-keyword">return</span> mid;  <span class="hljs-comment">// value found</span>
                                }
                            }
                            <span class="hljs-comment">//若没找到，则lo是value应该插入的位置，是一个正数。对这个正数去反，返回负数回去</span>
                            <span class="hljs-keyword">return</span> ~lo;  <span class="hljs-comment">// value not present</span>
                        }
                        
                        <span class="hljs-comment">//垃圾回收函数,压缩数组</span>
                        <span class="hljs-function"><span class="hljs-keyword">private</span> <span class="hljs-keyword">void</span> <span class="hljs-title">gc</span><span class="hljs-params">()</span> </span>{
                            <span class="hljs-comment">//保存GC前的集合大小</span>
                            <span class="hljs-keyword">int</span> n = mSize;
                            <span class="hljs-comment">//既是下标index，又是GC后的集合大小</span>
                            <span class="hljs-keyword">int</span> o = <span class="hljs-number">0</span>;
                            <span class="hljs-keyword">int</span>[] keys = mKeys;
                            Object[] values = mValues;
                            <span class="hljs-comment">//遍历values集合，以下算法 意义为 从values数组中，删除所有值为DELETED的元素</span>
                            <span class="hljs-keyword">for</span> (<span class="hljs-keyword">int</span> i = <span class="hljs-number">0</span>; i &lt; n; i++) {
                                Object val = values[i];
                                <span class="hljs-comment">//如果当前value 没有被标记为已删除</span>
                                <span class="hljs-keyword">if</span> (val != DELETED) {
                                    <span class="hljs-comment">//压缩keys、values数组</span>
                                    <span class="hljs-keyword">if</span> (i != o) {
                                        keys[o] = keys[i];
                                        values[o] = val;
                                        <span class="hljs-comment">//并将当前元素置空，防止内存泄漏</span>
                                        values[i] = <span class="hljs-keyword">null</span>;
                                    }
                                    <span class="hljs-comment">//递增o</span>
                                    o++;
                                }
                            }
                            <span class="hljs-comment">//修改 标识，不需要GC</span>
                            mGarbage = <span class="hljs-keyword">false</span>;
                            <span class="hljs-comment">//更新集合大小</span>
                            mSize = o;
                        }
                    </code></pre>
                    
                  GrowingArrayUtils.insert：
                
                    <pre class="hljs cpp"><code class="cpp">    <span class="hljs-comment">//</span>
                        <span class="hljs-keyword">public</span> <span class="hljs-keyword">static</span> <span class="hljs-keyword">int</span>[] insert(<span class="hljs-keyword">int</span>[] <span class="hljs-built_in">array</span>, <span class="hljs-keyword">int</span> currentSize, <span class="hljs-keyword">int</span> index, <span class="hljs-keyword">int</span> element) {
                            <span class="hljs-comment">//断言 确认 当前集合长度 小于等于 array数组长度</span>
                            assert currentSize &lt;= <span class="hljs-built_in">array</span>.length;
                            <span class="hljs-comment">//如果不需要扩容</span>
                            <span class="hljs-keyword">if</span> (currentSize + <span class="hljs-number">1</span> &lt;= <span class="hljs-built_in">array</span>.length) {
                                <span class="hljs-comment">//将array数组内元素，从index开始 后移一位</span>
                                System.arraycopy(<span class="hljs-built_in">array</span>, index, <span class="hljs-built_in">array</span>, index + <span class="hljs-number">1</span>, currentSize - index);
                                <span class="hljs-comment">//在index处赋值</span>
                                <span class="hljs-built_in">array</span>[index] = element;
                                <span class="hljs-comment">//返回</span>
                                <span class="hljs-keyword">return</span> <span class="hljs-built_in">array</span>;
                            }
                            <span class="hljs-comment">//需要扩容</span>
                            <span class="hljs-comment">//构建新的数组</span>
                            <span class="hljs-keyword">int</span>[] newArray = <span class="hljs-keyword">new</span> <span class="hljs-keyword">int</span>[growSize(currentSize)];
                            <span class="hljs-comment">//将原数组中index之前的数据复制到新数组中</span>
                            System.arraycopy(<span class="hljs-built_in">array</span>, <span class="hljs-number">0</span>, newArray, <span class="hljs-number">0</span>, index);
                            <span class="hljs-comment">//在index处赋值</span>
                            newArray[index] = element;
                            <span class="hljs-comment">//将原数组中index及其之后的数据赋值到新数组中</span>
                            System.arraycopy(<span class="hljs-built_in">array</span>, index, newArray, index + <span class="hljs-number">1</span>, <span class="hljs-built_in">array</span>.length - index);
                            <span class="hljs-comment">//返回</span>
                            <span class="hljs-keyword">return</span> newArray;
                        }
                        <span class="hljs-comment">//根据现在的size 返回合适的扩容后的容量</span>
                        <span class="hljs-function"><span class="hljs-keyword">public</span> <span class="hljs-keyword">static</span> <span class="hljs-keyword">int</span> <span class="hljs-title">growSize</span><span class="hljs-params">(<span class="hljs-keyword">int</span> currentSize)</span> </span>{
                            <span class="hljs-comment">//如果当前size 小于等于4，则返回8， 否则返回当前size的两倍</span>
                            <span class="hljs-keyword">return</span> currentSize &lt;= <span class="hljs-number">4</span> ? <span class="hljs-number">8</span> : currentSize * <span class="hljs-number">2</span>;
                        }
                    </code></pre>
                    
                    * 二分查找，若未找到返回下标时，与JDK里的实现不同，JDK是返回return -(low + 1); // key not found.,而这里是对 低位去反 返回。
                      这样在函数调用处，根据返回值的正负，可以判断是否找到index。对负index取反，即可得到应该插入的位置。
                    
                    * 扩容时，当前容量小于等于4，则扩容后容量为8.否则为当前容量的两倍。和ArrayList,ArrayMap不同(扩容一半)，和Vector相同(扩容一倍)。
                    
                    * 扩容操作依然是用数组的复制、覆盖完成。类似ArrayList.
                    
            * 删
            
                * 按照key删除
                
                    <pre class="hljs cpp"><code class="cpp">    <span class="hljs-comment">//按照key删除</span>
                        <span class="hljs-function"><span class="hljs-keyword">public</span> <span class="hljs-keyword">void</span> <span class="hljs-title">remove</span><span class="hljs-params">(<span class="hljs-keyword">int</span> key)</span> </span>{
                            <span class="hljs-keyword">delete</span>(key);
                        }
                        
                        <span class="hljs-function"><span class="hljs-keyword">public</span> <span class="hljs-keyword">void</span> <span class="hljs-title">delete</span><span class="hljs-params">(<span class="hljs-keyword">int</span> key)</span> </span>{
                            <span class="hljs-comment">//二分查找得到要删除的key所在index</span>
                            <span class="hljs-keyword">int</span> i = ContainerHelpers.binarySearch(mKeys, mSize, key);
                            <span class="hljs-comment">//如果&gt;=0,表示存在</span>
                            <span class="hljs-keyword">if</span> (i &gt;= <span class="hljs-number">0</span>) {
                                <span class="hljs-comment">//修改values数组对应位置为已删除的标志DELETED</span>
                                <span class="hljs-keyword">if</span> (mValues[i] != DELETED) {
                                    mValues[i] = DELETED; 
                                    <span class="hljs-comment">//并修改 mGarbage ,表示稍后需要GC</span>
                                    mGarbage = <span class="hljs-literal">true</span>;
                                }
                            }
                        }
                    </code></pre>
                    
                * 按照index删除
                
                    <pre class="hljs cpp"><code class="cpp">    <span class="hljs-function"><span class="hljs-keyword">public</span> <span class="hljs-keyword">void</span> <span class="hljs-title">removeAt</span><span class="hljs-params">(<span class="hljs-keyword">int</span> index)</span> </span>{
                            <span class="hljs-comment">//根据index直接索引到对应位置 执行删除操作</span>
                            <span class="hljs-keyword">if</span> (mValues[index] != DELETED) {
                                mValues[index] = DELETED;
                                mGarbage = <span class="hljs-literal">true</span>;
                            }
                        }
                    </code></pre>
                    
                *  批量删除
                    
                    <pre class="hljs java"><code class="java">    <span class="hljs-function"><span class="hljs-keyword">public</span> <span class="hljs-keyword">void</span> <span class="hljs-title">removeAtRange</span><span class="hljs-params">(<span class="hljs-keyword">int</span> index, <span class="hljs-keyword">int</span> size)</span> </span>{
                        <span class="hljs-comment">//越界修正</span>
                            <span class="hljs-keyword">final</span> <span class="hljs-keyword">int</span> end = Math.min(mSize, index + size);
                            <span class="hljs-comment">//for循环 执行单个删除操作</span>
                            <span class="hljs-keyword">for</span> (<span class="hljs-keyword">int</span> i = index; i &lt; end; i++) {
                                removeAt(i);
                            }
                        }
                    </code></pre>
                    
            * 查 
                
                * 按照key查询
                
                    <pre class="hljs java"><code class="java">    <span class="hljs-comment">//按照key查询，如果key不存在，返回null</span>
                        <span class="hljs-function"><span class="hljs-keyword">public</span> E <span class="hljs-title">get</span><span class="hljs-params">(<span class="hljs-keyword">int</span> key)</span> </span>{
                            <span class="hljs-keyword">return</span> get(key, <span class="hljs-keyword">null</span>);
                        }
                    
                        <span class="hljs-comment">//按照key查询，如果key不存在，返回valueIfKeyNotFound</span>
                        <span class="hljs-function"><span class="hljs-keyword">public</span> E <span class="hljs-title">get</span><span class="hljs-params">(<span class="hljs-keyword">int</span> key, E valueIfKeyNotFound)</span> </span>{
                            <span class="hljs-comment">//二分查找到 key 所在的index</span>
                            <span class="hljs-keyword">int</span> i = ContainerHelpers.binarySearch(mKeys, mSize, key);
                            <span class="hljs-comment">//不存在</span>
                            <span class="hljs-keyword">if</span> (i &lt; <span class="hljs-number">0</span> || mValues[i] == DELETED) {
                                <span class="hljs-keyword">return</span> valueIfKeyNotFound;
                            } <span class="hljs-keyword">else</span> {<span class="hljs-comment">//存在</span>
                                <span class="hljs-keyword">return</span> (E) mValues[i];
                            }
                        }
                    </code></pre>
                    
                * 按照下标查询
                
                    <pre class="hljs cpp"><code class="cpp">    <span class="hljs-function"><span class="hljs-keyword">public</span> <span class="hljs-keyword">int</span> <span class="hljs-title">keyAt</span><span class="hljs-params">(<span class="hljs-keyword">int</span> index)</span> </span>{
                        <span class="hljs-comment">//按照下标查询时，需要考虑是否先GC</span>
                            <span class="hljs-keyword">if</span> (mGarbage) {
                                gc();
                            }
                    
                            <span class="hljs-keyword">return</span> mKeys[index];
                        }
                        
                        <span class="hljs-function"><span class="hljs-keyword">public</span> E <span class="hljs-title">valueAt</span><span class="hljs-params">(<span class="hljs-keyword">int</span> index)</span> </span>{
                         <span class="hljs-comment">//按照下标查询时，需要考虑是否先GC</span>
                            <span class="hljs-keyword">if</span> (mGarbage) {
                                gc();
                            }
                    
                            <span class="hljs-keyword">return</span> (E) mValues[index];
                        }
                    </code></pre>
                    
                * 查询下标
                    
                    <pre class="hljs cpp"><code class="cpp">    <span class="hljs-function"><span class="hljs-keyword">public</span> <span class="hljs-keyword">int</span> <span class="hljs-title">indexOfKey</span><span class="hljs-params">(<span class="hljs-keyword">int</span> key)</span> </span>{
                         <span class="hljs-comment">//查询下标时，也需要考虑是否先GC</span>
                            <span class="hljs-keyword">if</span> (mGarbage) {
                                gc();
                            }
                            <span class="hljs-comment">//二分查找返回 对应的下标 ,可能是负数</span>
                            <span class="hljs-keyword">return</span> ContainerHelpers.binarySearch(mKeys, mSize, key);
                        }
                        <span class="hljs-function"><span class="hljs-keyword">public</span> <span class="hljs-keyword">int</span> <span class="hljs-title">indexOfValue</span><span class="hljs-params">(E value)</span> </span>{
                         <span class="hljs-comment">//查询下标时，也需要考虑是否先GC</span>
                            <span class="hljs-keyword">if</span> (mGarbage) {
                                gc();
                            }
                            <span class="hljs-comment">//不像key一样使用的二分查找。是直接线性遍历去比较，而且不像其他集合类使用equals比较，这里直接使用的 ==</span>
                            <span class="hljs-comment">//如果有多个key 对应同一个value，则这里只会返回一个更靠前的index</span>
                            <span class="hljs-keyword">for</span> (<span class="hljs-keyword">int</span> i = <span class="hljs-number">0</span>; i &lt; mSize; i++)
                                <span class="hljs-keyword">if</span> (mValues[i] == value)
                                    <span class="hljs-keyword">return</span> i;
                    
                            <span class="hljs-keyword">return</span> <span class="hljs-number">-1</span>;
                        }
                    </code></pre>
                    
                    按照value查询下标时，不像key一样使用的二分查找。是直接线性遍历去比较，而且不像其他集合类使用equals比较，这里直接使用的 ==
                    
                    如果有多个key 对应同一个value，则这里只会返回一个更靠前的index
                    
            ####总结 
                
            * SparseArray的源码相对来说比较简单，经过之前几个集合的源码洗礼，很轻松就可以掌握大体流程和关键思想：时间换空间。
                
            * Android sdk中，还提供了三个类似思想的集合：
                
            * SparseBooleanArray,value为boolean
               
            * SparseIntArray,value为int
                
            * SparseLongArray,value为long
                
            * 他们和SparseArray唯一的区别在于value的类型，SparseArray的value可以是任意类型。而它们是三个常使用的拆箱后的基本类型。
                
         [参考：SparseArray源码解析](https://www.jianshu.com/p/25ccfe46faf5)

    
## 线程

   > 思路 ：基本概念-> 深入理解
   
   * 基本概念
        
        * 线程
        
           线程就是进程的执行单元，就好像一个音乐软件可以听音乐，下载音乐，这些任务都是由线程来完成的。
           
        * 进程
        
            进程就是在运行过程中的程序，就好像手机运行中的微信，QQ，这些就叫做进程。
            
        * 线程和进程的关系
        
            一个进程可以拥有多个线程，一个线程必须要有一个父进程
            
            线程之间共享父进程的共享资源，相互之间协同完成进程所要完成的任务
            
            一个线程可以创建和撤销另一个线程，同一个进程的多个线程之间可以并发执行
            
        * 创建线程的方式(三种)   
            
            * 继承 Thread 类创建线程
            
                新建一个类继承 Thread 类，并重写 Thread 类的 run() 方法。
                
                创建 Thread 子类的实例。
                
                调用该子类实例的 start() 方法启动该线程。
                
                举例： 
                
                <pre><code class="hljs bash" lang="bash">public class ThreadDemo extends Thread {
                    
                    // 1. 新建一个类继承 Thread 类，并重写 Thread 类的 run() 方法。
                    @Override
                    public void <span class="hljs-function"><span class="hljs-title">run</span></span>() {
                        System.out.println(<span class="hljs-string">"Hello Thread"</span>);
                    }
                    
                    public static void main(String[] args) {
                        
                        // 2. 创建 Thread 子类的实例。
                        ThreadDemo threadDemo = new ThreadDemo();
                        // 3. 调用该子类实例的 start() 方法启动该线程。
                        threadDemo.start();
                        
                    }
                
                }
                
                </code></pre>
            
            * 实现 Runnable 接口创建线程
            
                创建一个类实现 Runnable 接口，并重写该接口的 run() 方法。
                
                创建该实现类的实例。
                
                将该实例传入 Thread(Runnable r) 构造方法中创建 Thread 实例。
                
                调用该 Thread 线程对象的 start() 方法。
                
                代码举例如下：
                
                    <pre><code class="hljs bash" lang="bash">
                    public class RunnableDemo implements Runnable {
                    
                    	// 1. 创建一个类实现 Runnable 接口，并重写该接口的 run() 方法。
                    	@Override
                    	public void <span class="hljs-function"><span class="hljs-title">run</span></span>() {
                    		System.out.println(<span class="hljs-string">"Hello Runnable"</span>);
                    	}
                    
                    	
                    	public static void main(String[] args) {
                    		
                    		// 2. 创建该实现类的实例。
                    		RunnableDemo runnableDemo = new RunnableDemo();
                    		
                    		// 3. 将该实例传入 Thread(Runnable r) 构造方法中创建 Thread 实例。
                    		Thread thread = new Thread(runnableDemo);
                    		
                    		// 4. 调用该 Thread 线程对象的 start() 方法。
                    		thread.start();
                    		
                    	}
                    	
                    
                    }
                    
                 </code></pre>
                 
                 打印结果：
                    
                    Hello Runnable
                    
            * 使用 Callable 和 FutureTask 创建线程
            
                使用这种方法创建的线程可以获取一个返回值，使用实现 Callable 和 FutureTask 创建线程步骤是：
                
                创建一个类实现 Callable 接口，并重写 call() 方法。
                
                创建该 Callable 接口实现类的实例。
                
                将 Callable 的实现类实例传入 FutureTask(Callable callable) 构造方法中创建 FutureTask 实例。
                
                将 FutureTask 实例传入 Thread(Runnable r) 构造方法中创建 Thread 实例。
                
                调用该 Thread 线程对象的 start() 方法。
                
                调用 FutureTask 实例对象的 get() 方法获取返回值。
                
                代码举例如下：
                
                <pre><code class="hljs bash" lang="bash">public class CallableDemo implements Callable&lt;String&gt; {
                
                	// 1. 创建一个类实现 Callable 接口，并重写 call() 方法。
                	@Override
                	public String call() throws Exception {
                		System.out.println(<span class="hljs-string">"CallableDemo is Running"</span>);
                		<span class="hljs-built_in">return</span> <span class="hljs-string">"Hello Callable"</span>;
                	}
                	
                	public static void main(String[] args) {
                		
                		// 2. 创建该 Callable 接口实现类的实例。
                		CallableDemo callableDemo = new CallableDemo();
                		
                		// 3. 将 Callable 的实现类实例传入 FutureTask(Callable&lt;V&gt; callable) 构造方法中创建 FutureTask 实例。
                		FutureTask&lt;String&gt; futureTask = new FutureTask&lt;&gt;(callableDemo);
                		
                		// 4. 将 FutureTask 实例传入 Thread(Runnable r) 构造方法中创建 Thread 实例。
                		Thread thread = new Thread(futureTask);
                		
                		// 5. 调用该 Thread 线程对象的 start() 方法。
                		thread.start();
                		
                		// 6. 调用 FutureTask 实例对象的 get() 方法获取返回值。
                		try {
                			System.out.println(futureTask.get());
                		} catch (Exception e) {
                			e.printStackTrace();
                		}
                		
                	}
                
                }
                </code></pre>
            
            打印结果如下：
                
                CallableDemo is Running
                Hello Callable
                
        #### 线程生命周期：
            
        > 当一个线程开启之后，它会遵循一定的生命周期，它要经过新建，就绪，运行，阻塞和死亡这五种状态，理解线程的生命周期有助于理解后面的相关的线程知识。      
        
        * 新建状态
            
            > 这个状态的意思就是线程刚刚被创建出来，这时候的线程并没有任何线程的动态特征。
        
        * 就绪状态
        
            > 当线程对象调用 start() 方法后，该线程就处于就绪状态。处于这个状态中的线程并没有开始运行，只是表示这个线程可以运行了。
        
        * 运行状态
        
            > 处于就绪状态的线程获得了 CPU 后，开始执行 run() 方法，这个线程就处于运行状态。
        
        * 阻塞状态
        
            > 当线程被暂停后，这个线程就处于阻塞状态。
        
        * 死亡状态
            
            > 当线程被停止后，这个线程就处于死亡状态。
              其实掌握多线程最主要的就是要熟悉控制线程的状态，让各个线程能更好的为我们的服务，下面就来讲解控制线程的方法。
              
        #### 控制线程   
            
        * sleep()
            
            * 线程周期变化
            
                <div>
                    <img src="https://user-gold-cdn.xitu.io/2018/1/28/1613cd8f57c4f761?imageslim" />
                </div>
                
            * 方法预览
                
                public static native void sleep(long millis)
                
                public static void sleep(long millis, int nanos)
                
                该方法的意思就是让正在运行状态的线程到阻塞状态，而这个时间就是线程处于阻塞状态的时间。millis 是毫秒的意思，nanos 是毫微秒。
                
            * 代码举例：
            
                <pre><code class="hljs bash" lang="bash">public class SleepDemo {
                	
                	public static void main(String[] args) throws Exception {
                		
                		<span class="hljs-keyword">for</span>(int i = 0; i &lt; 10; i++) {
                			System.out.println(<span class="hljs-string">"Hello Thread Sleep"</span>);
                			Thread.sleep(1000);
                		}
                		
                	}
                
                }
                </code></pre>
                
             以上代码运行后每隔一秒就输出 Hello Thread Sleep。
                
        * 线程优先级
        
           方法预览：
           
          > public final void setPriority(int newPriority)
           
          > public final int getPriority()
           
           从方法名就可以知道，以上两个方法分别就是设置和获得优先级的。值得注意的是优先级是在 1~10 范围内，也可以使用以下三个静态变量设置：
           
           MAX_PRIORITY：优先级为 10
           
           NORM_PRIORITY：优先级为 5
           
           MIN_PRIORITY：优先级为 1
        
        * yield()
        
            * 生命周期变化
            
                <div>
                    <img src="https://user-gold-cdn.xitu.io/2018/1/28/1613cd8f57d5fa31?imageslim" />
                </div>
                
            * 方法预览   
                
                public static native void yield();
                
                这个方法的意思就是让正在运行的线程回到就绪状态，并不会阻塞线程。可能会发生一种情况就是，该线程调用了 yield() 方法后，线程调度器又会继续调用该线程。 这个方法要注意的是它只会让步给比它优先级高的或者和它优先级相同并处在就绪状态的线程。
                
            * 代码举例：
                
                <pre><code class="hljs bash" lang="bash">public class YieldDemo extends Thread {
                
                	@Override
                	public void <span class="hljs-function"><span class="hljs-title">run</span></span>() {
                
                		<span class="hljs-keyword">for</span> (int i = 0; i &lt; 50; i++) {
                			System.out.println(getName() + <span class="hljs-string">" "</span> + i);
                
                			<span class="hljs-keyword">if</span> (i == 20) {
                				Thread.yield();
                			}
                		}
                
                	}
                
                	public static void main(String[] args) {
                
                		YieldDemo yieldDemo1 = new YieldDemo();
                		YieldDemo yieldDemo2 = new YieldDemo();
                
                		yieldDemo1.start();
                		yieldDemo2.start();
                
                	}
                
                }
                
                </code></pre>
                
                输出结果：
                
                <pre><code class="hljs bash" lang="bash">Thread-1 0
                Thread-1 1
                Thread-1 2
                Thread-1 3
                Thread-1 4
                Thread-1 5
                Thread-1 6
                Thread-1 7
                Thread-1 8
                Thread-1 9
                Thread-1 10
                Thread-1 11
                Thread-1 12
                Thread-1 13
                Thread-1 14
                Thread-0 0
                Thread-0 1
                Thread-0 2
                Thread-1 15
                Thread-0 3
                Thread-1 16
                Thread-1 17
                Thread-1 18
                Thread-1 19
                Thread-1 20
                Thread-0 4
                Thread-0 5
                Thread-0 6
                Thread-0 7
                Thread-1 21
                Thread-0 8
                Thread-1 22
                Thread-0 9
                Thread-1 23
                Thread-0 10
                Thread-0 11
                Thread-0 12
                Thread-1 24
                Thread-1 25
                Thread-0 13
                Thread-1 26
                Thread-1 27
                Thread-0 14
                Thread-0 15
                Thread-1 28
                Thread-0 16
                Thread-0 17
                Thread-0 18
                Thread-1 29
                Thread-0 19
                Thread-0 20
                Thread-1 30
                Thread-1 31
                Thread-0 21
                Thread-1 32
                Thread-1 33
                Thread-1 34
                Thread-1 35
                Thread-1 36
                Thread-1 37
                Thread-1 38
                Thread-1 39
                Thread-1 40
                Thread-1 41
                Thread-1 42
                Thread-1 43
                Thread-1 44
                Thread-1 45
                Thread-1 46
                Thread-1 47
                Thread-1 48
                Thread-1 49
                Thread-0 22
                Thread-0 23
                Thread-0 24
                Thread-0 25
                Thread-0 26
                Thread-0 27
                Thread-0 28
                Thread-0 29
                Thread-0 30
                Thread-0 31
                Thread-0 32
                Thread-0 33
                Thread-0 34
                Thread-0 35
                Thread-0 36
                Thread-0 37
                Thread-0 38
                Thread-0 39
                Thread-0 40
                Thread-0 41
                Thread-0 42
                Thread-0 43
                Thread-0 44
                Thread-0 45
                Thread-0 46
                Thread-0 47
                Thread-0 48
                Thread-0 49
                </code></pre>
                
               从打印结果就可以看到打印 Thread-1 20的时候，下一个执行的就是 Thread-0 4。打印 Thread-20 的时候，下一个执行的就是 Thread-1 30。
               但是要说明的是，不是每次的打印结果都是一样的，因为前面说过线程调用 yield() 方法后，线程调度器有可能会继续启动该线程。
           
        * join()    
        
            * 线程生命周期的变化
                
                <div>
                    <img src="https://user-gold-cdn.xitu.io/2018/1/28/1613cd8f5817a8a5?imageslim" />
                </div>
                
            * 方法预览 
                
                public final void join() throws InterruptedException
                public final synchronized void join(long millis) throws InterruptedException
                
                这个方法其实要有两个线程，也就是一个线程的线程执行体中有另一个线程在调用 join() 方法。举个例子，Thread1 的 run() 方法执行体中有 Thread2 在调用 join()，这时候 Thread1 就会被阻塞，必须要等到 Thread2 的线程执行完成或者
                join() 方法的时间到后才会继续执行。
             
            * join() 代码举例
                
                <pre><code class="hljs bash" lang="bash">
                public class JoinDemo extends Thread {
                	
                	@Override
                	public void <span class="hljs-function"><span class="hljs-title">run</span></span>() {
                		<span class="hljs-keyword">for</span>(int i = 0; i &lt; 50; i++) {
                			
                			System.out.println(getName() + <span class="hljs-string">" "</span> + i);
                		}
                	}
                	
                	public static void main(String[] args) throws Exception {
                		
                		JoinDemo joinDemo = new JoinDemo();
                		
                		<span class="hljs-keyword">for</span>(int i = 0; i &lt; 50; i++) {
                			
                			<span class="hljs-keyword">if</span>(i == 20) {
                				
                				joinDemo.start();
                				joinDemo.join();
                				
                			}
                			
                			System.out.println(Thread.currentThread().getName() + <span class="hljs-string">" "</span> + i);
                			
                		}
                		
                		
                	}
                
                }
                
                </code></pre>
                
                代码输出结果：
                    
                <pre><code class="hljs bash" lang="bash">main 0
                main 1
                main 2
                main 3
                main 4
                main 5
                main 6
                main 7
                main 8
                main 9
                main 10
                main 11
                main 12
                main 13
                main 14
                main 15
                main 16
                main 17
                main 18
                main 19
                main 20
                Thread-0 0
                Thread-0 1
                Thread-0 2
                Thread-0 3
                Thread-0 4
                Thread-0 5
                Thread-0 6
                Thread-0 7
                Thread-0 8
                Thread-0 9
                Thread-0 10
                Thread-0 11
                Thread-0 12
                Thread-0 13
                Thread-0 14
                Thread-0 15
                Thread-0 16
                Thread-0 17
                Thread-0 18
                Thread-0 19
                Thread-0 20
                Thread-0 21
                Thread-0 22
                Thread-0 23
                Thread-0 24
                Thread-0 25
                Thread-0 26
                Thread-0 27
                Thread-0 28
                Thread-0 29
                Thread-0 30
                Thread-0 31
                Thread-0 32
                Thread-0 33
                Thread-0 34
                Thread-0 35
                Thread-0 36
                Thread-0 37
                Thread-0 38
                Thread-0 39
                Thread-0 40
                Thread-0 41
                Thread-0 42
                Thread-0 43
                Thread-0 44
                Thread-0 45
                Thread-0 46
                Thread-0 47
                Thread-0 48
                Thread-0 49
                main 21
                main 22
                main 23
                main 24
                main 25
                main 26
                main 27
                main 28
                main 29
                main 30
                main 31
                main 32
                main 33
                main 34
                main 35
                main 36
                main 37
                main 38
                main 39
                main 40
                main 41
                main 42
                main 43
                main 44
                main 45
                main 46
                main 47
                main 48
                main 49
                
                </code></pre>
                
                以上的代码其实一个两个线程，一个是 Thread-0，另一个就是 main，main 就是主线程的意思。从打印结果可以看到，主线程执行到 main 20 的时候，就开始执行 Thread-0 0，直到 Thread-0 执行完毕，main 才继续执行。
                
            *  join(long millis) 代码举例:
                    
                <pre><code class="hljs bash" lang="bash">public class JoinDemo extends Thread {
                    
                    @Override
                    public void <span class="hljs-function"><span class="hljs-title">run</span></span>() {
                        <span class="hljs-keyword">for</span>(int i = 0; i &lt; 50; i++) {
                            
                            System.out.println(getName() + <span class="hljs-string">" "</span> + i);
                        }
                    }
                    
                    public static void main(String[] args) throws Exception {
                        
                        JoinDemo joinDemo = new JoinDemo();
                        
                        <span class="hljs-keyword">for</span>(int i = 0; i &lt; 50; i++) {
                            
                            System.out.println(Thread.currentThread().getName() + <span class="hljs-string">" "</span> + i);
                            
                            <span class="hljs-keyword">if</span>(i == 20) {
                                
                                joinDemo.start();
                                joinDemo.join(1);
                                
                            }
                            
                        }
                        
                        
                    }
                
                }
                </code></pre>
                
                打印结果：
                
                <pre><code class="hljs bash" lang="bash">main 0
                main 1
                main 2
                main 3
                main 4
                main 5
                main 6
                main 7
                main 8
                main 9
                main 10
                main 11
                main 12
                main 13
                main 14
                main 15
                main 16
                main 17
                main 18
                main 19
                main 20
                Thread-0 0
                Thread-0 1
                Thread-0 2
                Thread-0 3
                Thread-0 4
                Thread-0 5
                Thread-0 6
                Thread-0 7
                Thread-0 8
                Thread-0 9
                Thread-0 10
                Thread-0 11
                Thread-0 12
                Thread-0 13
                Thread-0 14
                Thread-0 15
                Thread-0 16
                Thread-0 17
                Thread-0 18
                Thread-0 19
                Thread-0 20
                Thread-0 21
                Thread-0 22
                Thread-0 23
                Thread-0 24
                Thread-0 25
                Thread-0 26
                Thread-0 27
                Thread-0 28
                Thread-0 29
                Thread-0 30
                Thread-0 31
                Thread-0 32
                Thread-0 33
                main 21
                main 22
                Thread-0 34
                main 23
                Thread-0 35
                Thread-0 36
                main 24
                main 25
                main 26
                Thread-0 37
                main 27
                Thread-0 38
                main 28
                Thread-0 39
                main 29
                Thread-0 40
                main 30
                Thread-0 41
                main 31
                Thread-0 42
                main 32
                main 33
                main 34
                main 35
                Thread-0 43
                Thread-0 44
                Thread-0 45
                main 36
                Thread-0 46
                main 37
                main 38
                main 39
                main 40
                main 41
                main 42
                main 43
                main 44
                main 45
                main 46
                main 47
                main 48
                main 49
                Thread-0 47
                Thread-0 48
                Thread-0 49
                </code></pre>
                
                其实这个的代码和 4.4.3 节的代码基本一样，就是将 join() 改成 join(1) ，可以看到 main 并没有等到 Thread-0 执行完就开始重新执行了。
                
        * 后台线程
        
            * 方法预览
            
                public final void setDaemon(boolean on)
                
                public final boolean isDaemon()
                
                这个方法就是将线程设置为后台线程，后台线程的特点就是当前台线程全部执行结束后，后台线程就会随之结束。此方法设置为 true 时，就是将线程设置为后台线程。 而 isDaemon() 就是返回此线程是否为后台线程。
                
            * 代码举例
                
                <pre><code class="hljs bash" lang="bash">
                public class DaemonDemo extends Thread {
                
                	@Override
                	public void <span class="hljs-function"><span class="hljs-title">run</span></span>() {
                		<span class="hljs-keyword">for</span>(int i = 0; i &lt; 100; i++) {
                			System.out.println(getName() + <span class="hljs-string">" "</span>+ isDaemon() + <span class="hljs-string">" "</span> + i);
                		}
                	}
                	
                	public static void main(String[] args) {
                		
                		DaemonDemo daemonDemo = new DaemonDemo();
                		
                		daemonDemo.setDaemon(<span class="hljs-literal">true</span>);
                		
                		daemonDemo.start();
                		
                		<span class="hljs-keyword">for</span>(int i = 0; i &lt; 10; i++) {
                			System.out.println(Thread.currentThread().getName() + <span class="hljs-string">" "</span> + i);
                		}
                		
                	}
                	
                }
                
                </code></pre>
                
            打印结果：
            
            <pre><code class="hljs bash" lang="bash">main 0
            main 1
            main 2
            main 3
            main 4
            Thread-0 <span class="hljs-literal">true</span> 0
            main 5
            main 6
            main 7
            main 8
            main 9
            Thread-0 <span class="hljs-literal">true</span> 1
            Thread-0 <span class="hljs-literal">true</span> 2
            Thread-0 <span class="hljs-literal">true</span> 3
            Thread-0 <span class="hljs-literal">true</span> 4
            Thread-0 <span class="hljs-literal">true</span> 5
            Thread-0 <span class="hljs-literal">true</span> 6
            Thread-0 <span class="hljs-literal">true</span> 7
            Thread-0 <span class="hljs-literal">true</span> 8
            Thread-0 <span class="hljs-literal">true</span> 9
            Thread-0 <span class="hljs-literal">true</span> 10
            Thread-0 <span class="hljs-literal">true</span> 11
            </code></pre>
            
            从打印结果可以看到 main 执行完后，Thread-0 没有执行完毕就结束了。
            
        * 一些注意点
            
            sleep() 和 yield() 区别
                
            <table>
            <thead>
            <tr>
            <th>作用处</th>
            <th>sleep()</th>
            <th>yield()</th>
            </tr>
            </thead>
            <tbody>
            <tr>
            <td>给其他线程执行机会</td>
            <td>会给其他线程执行机会，不会理会其他线程的优先级</td>
            <td>只会给优先级相同，或者优先级更高的线程执行机会</td>
            </tr>
            <tr>
            <td>影响当前线程的状态</td>
            <td>从阻塞到就绪状态</td>
            <td>直接进入就绪状态</td>
            </tr>
            <tr>
            <td>异常</td>
            <td>需要抛出 InterruptedException</td>
            <td>不需要抛出任何异常</td>
            </tr>
            </tbody>
            </table>
            
   * 深入理解：
        
        > 简介->java内存模型->多线程的几个重要概念->线程安全-> synchronized 修饰符
        
        * 简介
            
            在多线程中可能会出现很多预想不到的现象，要理解这些现象的产生的原因，就一定要理解以下讲解的几个概念。
   
        * Java内存模型
        
            Java 内存模型主要定义变量的访问规则，这里的变量只是指实例变量，静态变量，并不包括局部变量，因为局部变量是线程私有的，并不存在共享。在这个模型有以下几个主要的元素：
            
            线程
            
            共享变量
            
            工作内存
            
            主内存
            
            这几个元素之间还有几个要注意的地方：
            
            <table>
            <thead>
            <tr>
            <th>作用处</th>
            <th>说明</th>
            </tr>
            </thead>
            <tbody>
            <tr>
            <td>线程本身</td>
            <td>每条线程都有自己的工作内存，工作内存当中会有共享变量的副本。</td>
            </tr>
            <tr>
            <td>线程操作共享变量</td>
            <td>线程只能对自己工作内存的当中的共享变量副本进行操作，不能直接操作主内存的共享变量。</td>
            </tr>
            <tr>
            <td>不同线程间操作共享变量</td>
            <td>不同线程之间无法直接操作对方的工作内存的变量，只能通过主线程来协助完成。</td>
            </tr>
            </tbody>
            </table>
              
        * 几个元素的关系图：
        
            <div>
                <img src="https://user-gold-cdn.xitu.io/2018/2/4/161614f031866304?imageslim" />
            </div>
            
            内存间的操作：
            
            Java 定义了 8 种操作来操作变量，这 8 种操作定义如下：
        
            <table>
            <thead>
            <tr>
            <th>操作</th>
            <th>作用处</th>
            <th>说明</th>
            </tr>
            </thead>
            <tbody>
            <tr>
            <td>lock（锁定）</td>
            <td>主内存变量</td>
            <td>把一个变量标识成一条线程独占的状态</td>
            </tr>
            <tr>
            <td>unlock（解锁）</td>
            <td>主内存变量</td>
            <td>把一个处于锁定状态的变量释放出来，释放后的变量才可以被其他线程锁定</td>
            </tr>
            <tr>
            <td>read（读取）</td>
            <td>主内存变量</td>
            <td>把一个变量的值从主内存传输到线程的工作内存中，以便随后的 load 动作使用</td>
            </tr>
            <tr>
            <td>load（载入）</td>
            <td>工作内存变量</td>
            <td>把 read 操作得到的变量放入到工作内存的变量副本中</td>
            </tr>
            <tr>
            <td>use（使用）</td>
            <td>工作内存变量</td>
            <td>将工作内存中的一个变量的值传递给执行引擎</td>
            </tr>
            <tr>
            <td>assign（赋值）</td>
            <td>工作内存变量</td>
            <td>将执行引擎接收到的值赋给工作内存的变量</td>
            </tr>
            <tr>
            <td>store（存储）</td>
            <td>工作内存变量</td>
            <td>把工作内存中一个变量的值传给主内存中，以便给随后的 write 操作使用</td>
            </tr>
            <tr>
            <td>write（写入）</td>
            <td>主内存变量</td>
            <td>把 store 操作从工作内存中得到的变量的值放入主内存变量中</td>
            </tr>
            </tbody>
            </table>
        
        * 内存操作的规则
            
            Java 内存模型操作还必须满足如下规则(不用记忆)：
                
            <table>
            <thead>
            <tr>
            <th>操作方法</th>
            <th>规则</th>
            </tr>
            </thead>
            <tbody>
            <tr>
            <td>read 和 load</td>
            <td>这两个方法必须以组合的方式出现，不允许一个变量从主内存读取了但工作内存不接受情况出现</td>
            </tr>
            <tr>
            <td>store 和 write</td>
            <td>这两个方法必须以组合的方式出现，不允许从工作内存发起了存储操作但主内存不接受的情况出现</td>
            </tr>
            <tr>
            <td>assign</td>
            <td>工作内存的变量如果没有经过 assign 操作，不允许将此变量同步到主内存中</td>
            </tr>
            <tr>
            <td>load 和 use</td>
            <td>在 use 操作之前，必须经过 load 操作</td>
            </tr>
            <tr>
            <td>assign 和 store</td>
            <td>在 store 操作之前，必须经过 assign 操作</td>
            </tr>
            <tr>
            <td>lock 和 unlock</td>
            <td>1. unlock 操作只能作用于被 lock 操作锁定的变量<br>2. 一个变量被执行了多少次 lock 操作就要执行多少次 unlock 才能解锁</td>
            </tr>
            <tr>
            <td>lock</td>
            <td>1. 一个变量只能在同一时刻被一条线程进行 lock 操作<br>2. 执行 lock 操作后，工作内存的变量的值会被清空，需要重新执行 load 或 assign 操作初始化变量的值</td>
            </tr>
            <tr>
            <td>unlock</td>
            <td>对一个变量执行 unlock 操作之前，必须先把此变量同步回主内存中</td>
            </tr>
            </tbody>
            </table> 
            
        * 多线程中几个重要的概念
        
            了解完 Java 的内存模型后，还需要继续理解以下几个可以帮助理解多线程现象的重要概念。
            
             * 同步和异步
                
                同步和异步的都是形容一次方法的调用。它们的概念如下：
                
                同步：调用者必须要等到调用的方法返回后才会继续后续的行为。
                
                异步：调用者调用后，不必等调用方法返回就可以继续后续的行为。
                
                下面两个图就可以清晰表明同步和异步的区别：
                
                <div>
                    <img src="https://user-gold-cdn.xitu.io/2018/2/4/161614f031954235?imageslim" />
                </div>
                
                <br/>
                
                <div>
                    <img src="https://user-gold-cdn.xitu.io/2018/2/4/161614f0319aaf18?imageslim" />
                </div>
             
             * 并发和并行
                
                并发和并行是形容多个任务时的状态，它们的概念如下：
                
                并发：多个任务交替运行。
                
                并行：多个任务同时运行。
                
                <div>
                    <img src="https://user-gold-cdn.xitu.io/2018/2/4/161614f031bd0387?imageslim" />
                </div>
                <br/>
                <div>
                    <img src="https://user-gold-cdn.xitu.io/2018/2/4/161614f031a615d6?imageslim" />
                </div>
             
             * 原子性
             
                原子就是指化学反应当中不可分割的微粒。所以原子性概念如下：
                原子性：在 Java 中就是指一些不可分割的操作。
                比如刚刚介绍的内存操作全部都属于原子性操作。以下再举个例子帮助大家理解：
                x = 1;
                y = x;
                以上两句代码哪个是原子性操作哪个不是？
                x = 1 是，因为线程中是直接将数值 1 写入到工作内存中。
                y = x 不是，因为这里包含了两个操作：
                
                读取了 x 的值（因为 x 是变量）
                将 x 的值写入到工作内存中
                
             * 可见性
             
                可见性：指一个线程修改了共享变量的值，其他线程能够立即得知这个修改。
                    
                这里举个例子来讲解这个可见性的重要性，代码如下：    
                
                <pre><code class="hljs bash" lang="bash">public class ThreadTest {
                	
                	
                	private static boolean plus = <span class="hljs-literal">true</span>;
                	private static int a;
                	
                	static class VisibilityThread1 extends Thread {
                			
                		
                		public VisibilityThread1(String name) {
                			<span class="hljs-built_in">set</span>Name(name);
                		}
                		
                		@Override
                		public void <span class="hljs-function"><span class="hljs-title">run</span></span>() {
                			<span class="hljs-keyword">while</span>(<span class="hljs-literal">true</span>) {
                				<span class="hljs-keyword">if</span>(plus) {
                					a++;
                					plus = <span class="hljs-literal">false</span>;
                					System.out.println(getName() + <span class="hljs-string">" a = "</span> + a + <span class="hljs-string">" plus = "</span> + plus);
                				}
                			}
                		}
                		
                	}
                
                	static class VisibilityThread2 extends Thread {
                		
                		public VisibilityThread2(String name) {
                			<span class="hljs-built_in">set</span>Name(name);
                		}
                		
                		@Override
                		public void <span class="hljs-function"><span class="hljs-title">run</span></span>() {
                			<span class="hljs-keyword">while</span>(<span class="hljs-literal">true</span>) {
                				<span class="hljs-keyword">if</span>(!plus) {
                					a--;
                					plus = <span class="hljs-literal">true</span>;
                					System.out.println(getName() + <span class="hljs-string">" a = "</span> + a + <span class="hljs-string">" plus = "</span> + plus);
                				}
                			}
                
                		}
                		
                	}
                	
                	
                	public static void main(String[] args) {
                		
                		VisibilityThread1 visibilityThread1 = new VisibilityThread1(<span class="hljs-string">"线程1"</span>);
                		VisibilityThread2 visibilityThread2 = new VisibilityThread2(<span class="hljs-string">"线程2"</span>);
                		
                		visibilityThread1.start();
                		visibilityThread2.start();
                		
                	}
                	
                	
                
                }
                
                </code></pre>
                
                  这段代码的期待输出的结果应该是以下这两句循环输出：
                  
                  <pre><code class="hljs bash" lang="bash">线程1 a = 1 plus = <span class="hljs-literal">false</span>
               线程2 a = 0 plus = <span class="hljs-literal">true</span>
                  </code></pre>
                  
                  但是你会发现会出现如下的结果：
                  
               <pre><code class="hljs bash" lang="bash">线程1 a = 0 plus = <span class="hljs-literal">true</span>
               线程2 a = 1 plus = <span class="hljs-literal">false</span>
               </code></pre>
               
               出现这个错误的结果是因为两条线程同时都在修改共享变量 a 和 plus。一个线程在修改共享变量时，其他线程并不知道这个共享变量被修改了，所以多线程开发中一定要关注可见性。
             
             * 重排序
             
                > 总结 ： 重排序：编译器和处理器为了优化程序性能而对指令重新排序的一种手段。 在讲解这个概念之前要先铺垫一个概念：数据依赖性。
             
                 * 数据依赖性
                    
                    如果两个操作同时操作一个变量，其中一个操作还包括写的操作，那么这两个操作之间就存在数据依赖性了。这些组合操作看下表：
                    
                    <table>
                    <thead>
                    <tr>
                    <th>名称</th>
                    <th>说明</th>
                    <th>代码示例</th>
                    </tr>
                    </thead>
                    <tbody>
                    <tr>
                    <td>写后读</td>
                    <td>写一个变量后，再读取这个变量</td>
                    <td>a = 1;<br>b = a;</td>
                    </tr>
                    <tr>
                    <td>写后写</td>
                    <td>写一个变量后，再写入这个变量</td>
                    <td>a = 1;<br>a = 2;</td>
                    </tr>
                    <tr>
                    <td>读后写</td>
                    <td>读取一个变量后，再写入这个变量</td>
                    <td>b = a;<br>a = 2;</td>
                    </tr>
                    </tbody>
                    </table>
                    上表这三种情况如果重排序的话就会改变程序的结果了。所以编译器和处理器并不会对这些有数据依赖性的操作进行重排序的。 注意，这里所说的数据依赖性只是在单线程的才会出现，如果多线程的话，编译器和处理器并不会有数据依赖性。
                    
                 * 多线程中的重排序
                 
                    这里使用简化的代码来讲解，代码如下：
                        
                    <pre><code class="hljs bash" lang="bash">int a = 0;
                    boolean flag = <span class="hljs-literal">false</span>;
                    
                    // 线程1
                    VisibilityThread1 {
                      a = 3; // 1
                      flag = <span class="hljs-literal">true</span>; // 2
                    }
                    
                    // 线程2
                    VisibilityThread2 {
                      <span class="hljs-keyword">if</span>(flag) { // 3
                        a= a * 3; // 4
                      }
                    }
                    </code></pre>
                    
                    这里操作 1，2 和 操作 3，4 并不存在数据依赖性，所以编译器和处理器有可能会对这些操作组合进行重排序。程序的执行的其中一种情况如下图：
                 
                    <div>
                        <img src="https://user-gold-cdn.xitu.io/2018/2/4/161614f031afd873?imageView2/0/w/1280/h/960/format/webp/ignore-error/1" />
                    </div>
                    
                    因为线程 2 中的操作 5 和 6 存在控制依赖的关系，这会影响程序执行的速度，所以编译器和处理器就会猜测执行的方式来提升速度，以上的情况就是采用了这种方式，线程 2 提前读取了 a 的值，并计算出 a * 3 的值并把这个值临时保存到重排序缓冲的硬件缓存中，等待 flag 的值变为 true 后，再把存储后的值写入 a 中。但是这就会出现我们并不想要的结果了，这种情况下，a 可能还是为 1。
                    
        * 有序性
            
            如果理解了重排序后，有序性这个概念其实也是很容易理解的。 有序性：是指程序的运行顺序与编写代码的顺序一致。
             
        * 线程安全
            
            * 定义
                
                线程安全就是指某个方法在多线程环境被调用的时候，能够正确处理多个线程之间的共享变量，使程序功能能够正确执行。
                这里举个经典的线程安全的案例——多窗口卖票。假设有 30 张票，现在有两个窗口同时卖这 30 张票。这里的票就是共享变量，而窗口就是线程。这里的代码逻辑大概可以分为这几步：
                
                两条线程不停循环卖票，每次卖出一张，总票数就减去一张。
                如果发现总票数为 0，停止循环。
                
                代码如下：
                
                <pre><code class="hljs bash" lang="bash">public class SellTicketDemo implements Runnable {
                
                    private int ticketNum = 30;
                    
                    @Override
                    public void <span class="hljs-function"><span class="hljs-title">run</span></span>() {
                        <span class="hljs-keyword">while</span>(<span class="hljs-literal">true</span>) {
                            
                            <span class="hljs-keyword">if</span>(ticketNum &lt;= 0) {
                                <span class="hljs-built_in">break</span>;
                            }
                            
                            System.out.println(Thread.currentThread().getName() +<span class="hljs-string">" 卖出第  "</span> + ticketNum + <span class="hljs-string">" 张票，剩余的票数："</span> + --ticketNum);
                        }
                    }
                    
                    public static void main(String[] args) {
                        
                        SellTicketDemo sellTicketDemo = new SellTicketDemo();
                        
                        Thread thread1 = new Thread(sellTicketDemo,<span class="hljs-string">"窗口1"</span>);
                        Thread thread2 = new Thread(sellTicketDemo,<span class="hljs-string">"窗口2"</span>);
                        
                        thread1.start();
                        thread2.start();
                        
                    }
                
                }
                </code></pre>
                
                代码打印结果如下：
                
                <pre><code class="hljs bash" lang="bash">窗口1 卖出第  30 张票，剩余的票数：28
                窗口2 卖出第  30 张票，剩余的票数：29
                窗口1 卖出第  28 张票，剩余的票数：27
                窗口2 卖出第  27 张票，剩余的票数：26
                窗口1 卖出第  26 张票，剩余的票数：25
                窗口2 卖出第  25 张票，剩余的票数：24
                窗口1 卖出第  24 张票，剩余的票数：23
                窗口2 卖出第  23 张票，剩余的票数：22
                窗口2 卖出第  21 张票，剩余的票数：20
                窗口1 卖出第  22 张票，剩余的票数：21
                窗口2 卖出第  20 张票，剩余的票数：19
                窗口1 卖出第  19 张票，剩余的票数：18
                窗口1 卖出第  17 张票，剩余的票数：16
                窗口1 卖出第  16 张票，剩余的票数：15
                窗口1 卖出第  15 张票，剩余的票数：14
                窗口1 卖出第  14 张票，剩余的票数：13
                窗口1 卖出第  13 张票，剩余的票数：12
                窗口1 卖出第  12 张票，剩余的票数：11
                窗口1 卖出第  11 张票，剩余的票数：10
                窗口1 卖出第  10 张票，剩余的票数：9
                窗口1 卖出第  9 张票，剩余的票数：8
                窗口1 卖出第  8 张票，剩余的票数：7
                窗口1 卖出第  7 张票，剩余的票数：6
                窗口1 卖出第  6 张票，剩余的票数：5
                窗口1 卖出第  5 张票，剩余的票数：4
                窗口1 卖出第  4 张票，剩余的票数：3
                窗口1 卖出第  3 张票，剩余的票数：2
                窗口1 卖出第  2 张票，剩余的票数：1
                窗口1 卖出第  1 张票，剩余的票数：0
                窗口2 卖出第  18 张票，剩余的票数：17
                </code></pre>
        
        * Java中控制线程的几种方式
            
            > 思路 -> 四种方式 -> 各自优缺点
            
            [参考：应该了解的一些并发基础知识](https://mp.weixin.qq.com/s/KuKROR8c4Bc1CdXE6AxB2g)
            
            * volatile
                    
                > 总结-> 具体分析
                    
                * volatile用来保证可见性和有序性，不保证原子性。
                
                    volatile保证的可见性
                    
                    volatile修饰的属性保证每次读取都能读到最新的值，可是并不会更新已经读了的值，它也无法更新已经读了的值。
                    
                    线程A在工作内存中修改共享属性值会立即刷新到主存，线程B/C/D每次通过读写栅栏来达到类似于直接从主存中读取属性值，注意，是类似，网上有些说volatile修饰的变量读写直接在主存中操作，这种说法是不对的，只是表现出类似的行为。
                    
                    读写栅栏是一条CPU指令，插入一个读写栅栏， 相当于告诉CPU和编译器先于这个命令的必须先执行，后于这个命令的必须后执行（有序性）。读写栅栏另一个作用是强制更新一次不同CPU的缓存。例如，一个写栅栏会 把这个栅栏前写入的数据刷新到缓存，以此保证可见性。
                    
                    volatile保证的有序性
                    
                    当对volatile修饰的属性进行读/写操作时，其前面的代码必须已经执行完成且结果对后续的操作可见。在重排序时，以volatile修饰属性的读/写操作代码行为分界线，读/写操作前面的代码不许排序到后面，后面同理不许排序到前面。由此保证有序性.
                    
                    <code class="" style="margin-right: 2px;margin-left: 2px;line-height: 15px;font-size: 11px;word-spacing: -3px;letter-spacing: 0px;font-family: Consolas, Inconsolata, Courier, monospace;color: rgb(169, 183, 198);background: rgb(40, 43, 46);padding: 0.5em;display: block !important;word-wrap: normal !important;word-break: normal !important;overflow: auto !important;">{ &nbsp; <span class="" style="font-size: inherit;line-height: inherit;color: rgb(128, 128, 128);word-wrap: inherit !important;word-break: inherit !important;white-space: inherit !important;">// 线程A</span><br> &nbsp; &nbsp;bean = <span class="" style="font-size: inherit;line-height: inherit;color: rgb(248, 35, 117);word-wrap: inherit !important;word-break: inherit !important;white-space: inherit !important;">new</span> Bean(); &nbsp; &nbsp; <span class="" style="font-size: inherit;line-height: inherit;color: rgb(128, 128, 128);word-wrap: inherit !important;word-break: inherit !important;white-space: inherit !important;">// 语句A</span><br> &nbsp; &nbsp;inited = <span class="" style="font-size: inherit;line-height: inherit;color: rgb(248, 35, 117);word-wrap: inherit !important;word-break: inherit !important;white-space: inherit !important;">true</span>; &nbsp; &nbsp; &nbsp; &nbsp; <span class="" style="font-size: inherit;line-height: inherit;color: rgb(128, 128, 128);word-wrap: inherit !important;word-break: inherit !important;white-space: inherit !important;">// 语句B</span><br>}<br>{ &nbsp; <span class="" style="font-size: inherit;line-height: inherit;color: rgb(128, 128, 128);word-wrap: inherit !important;word-break: inherit !important;white-space: inherit !important;">// 线程B</span><br> &nbsp; &nbsp;<span class="" style="font-size: inherit;line-height: inherit;color: rgb(248, 35, 117);word-wrap: inherit !important;word-break: inherit !important;white-space: inherit !important;">if</span>(inited){ &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;<span class="" style="font-size: inherit;line-height: inherit;color: rgb(128, 128, 128);word-wrap: inherit !important;word-break: inherit !important;white-space: inherit !important;">// 语句C</span><br> &nbsp; &nbsp; &nbsp; &nbsp;bean.getAge(); &nbsp; &nbsp; <span class="" style="font-size: inherit;line-height: inherit;color: rgb(128, 128, 128);word-wrap: inherit !important;word-break: inherit !important;white-space: inherit !important;">// 语句D</span><br> &nbsp; &nbsp;}<br>}<br></code>
        
            * synchronized 修饰符
            
                * 语法格式
                
                synchronized(obj) {
                    // 同步代码块
                }
                
                * 使用 synchronized 代码块
                    
                    synchronized 括号的 obj 是同步监视器，Java 允许任何对象作为同步监视器，这里使用 SellTicketDemo 实例来作为同步监视器。代码如下：
                    
                    <pre><code class="hljs bash" lang="bash">public class SellTicketDemo implements Runnable {
                    
                        private int ticketNum = 30;
                        
                        @Override
                        public void <span class="hljs-function"><span class="hljs-title">run</span></span>() {
                            <span class="hljs-keyword">while</span>(<span class="hljs-literal">true</span>) {
                                synchronized(this) {
                                    <span class="hljs-keyword">if</span>(ticketNum &lt;= 0) {
                                        <span class="hljs-built_in">break</span>;
                                    }
                                    
                                    System.out.println(Thread.currentThread().getName() +<span class="hljs-string">" 卖出第  "</span> + ticketNum + <span class="hljs-string">" 张票，剩余的票数："</span> + --ticketNum);
                                }
                            }
                        }
                        
                        public static void main(String[] args) {
                            
                            SellTicketDemo sellTicketDemo = new SellTicketDemo();
                            
                            Thread thread1 = new Thread(sellTicketDemo,<span class="hljs-string">"窗口1"</span>);
                            Thread thread2 = new Thread(sellTicketDemo,<span class="hljs-string">"窗口2"</span>);
                            
                            thread1.start();
                            thread2.start();
                            
                        }
                    
                    }
                    
                    </code></pre>
                    
                    打印结果如下：
                    
                    <pre><code class="hljs bash" lang="bash">窗口1 卖出第  30 张票，剩余的票数：29
                    窗口1 卖出第  29 张票，剩余的票数：28
                    窗口1 卖出第  28 张票，剩余的票数：27
                    窗口1 卖出第  27 张票，剩余的票数：26
                    窗口1 卖出第  26 张票，剩余的票数：25
                    窗口1 卖出第  25 张票，剩余的票数：24
                    窗口1 卖出第  24 张票，剩余的票数：23
                    窗口1 卖出第  23 张票，剩余的票数：22
                    窗口1 卖出第  22 张票，剩余的票数：21
                    窗口1 卖出第  21 张票，剩余的票数：20
                    窗口2 卖出第  20 张票，剩余的票数：19
                    窗口2 卖出第  19 张票，剩余的票数：18
                    窗口2 卖出第  18 张票，剩余的票数：17
                    窗口2 卖出第  17 张票，剩余的票数：16
                    窗口2 卖出第  16 张票，剩余的票数：15
                    窗口2 卖出第  15 张票，剩余的票数：14
                    窗口2 卖出第  14 张票，剩余的票数：13
                    窗口2 卖出第  13 张票，剩余的票数：12
                    窗口2 卖出第  12 张票，剩余的票数：11
                    窗口2 卖出第  11 张票，剩余的票数：10
                    窗口2 卖出第  10 张票，剩余的票数：9
                    窗口2 卖出第  9 张票，剩余的票数：8
                    窗口2 卖出第  8 张票，剩余的票数：7
                    窗口2 卖出第  7 张票，剩余的票数：6
                    窗口2 卖出第  6 张票，剩余的票数：5
                    窗口2 卖出第  5 张票，剩余的票数：4
                    窗口2 卖出第  4 张票，剩余的票数：3
                    窗口2 卖出第  3 张票，剩余的票数：2
                    窗口2 卖出第  2 张票，剩余的票数：1
                    窗口2 卖出第  1 张票，剩余的票数：0
                    </code></pre>
            
            * synchronized 方法   
            
                 * 语法格式: 
                 
                 <pre><code class="hljs bash" lang="bash">[修饰符] synchronized [返回值] [方法名](形参...) {
                        
                 }
                 </code></pre>
                    
                 * 使用 synchronized 方法: 
                 
                   使用同步方法非常简单，直接用 synchronized 修饰多线程操作的方法即可，代码如下：
                   
                    <pre><code class="hljs bash" lang="bash">public class SellTicketDemo implements Runnable {
                    
                        private int ticketNum = 30;
                        
                        @Override
                        public void <span class="hljs-function"><span class="hljs-title">run</span></span>() {
                            <span class="hljs-keyword">while</span>(<span class="hljs-literal">true</span>) {
                    
                                sellTicket();
                                
                            }
                        }
                        
                        public synchronized void <span class="hljs-function"><span class="hljs-title">sellTicket</span></span>() {
                            <span class="hljs-keyword">if</span>(ticketNum &lt;= 0) {
                                <span class="hljs-built_in">return</span>;
                            }
                            
                            System.out.println(Thread.currentThread().getName() +<span class="hljs-string">" 卖出第  "</span> + ticketNum + <span class="hljs-string">" 张票，剩余的票数："</span> + --ticketNum);
                        }
                        
                        public static void main(String[] args) {
                            
                            SellTicketDemo sellTicketDemo = new SellTicketDemo();
                            
                            Thread thread1 = new Thread(sellTicketDemo,<span class="hljs-string">"窗口1"</span>);
                            Thread thread2 = new Thread(sellTicketDemo,<span class="hljs-string">"窗口2"</span>);
                            
                            thread1.start();
                            thread2.start();
                            
                        }
                    
                    }
                    </code></pre>
                    
                    打印如下：
                    
                    <pre><code class="hljs bash" lang="bash">窗口1 卖出第  30 张票，剩余的票数：29
                    窗口1 卖出第  29 张票，剩余的票数：28
                    窗口1 卖出第  28 张票，剩余的票数：27
                    窗口1 卖出第  27 张票，剩余的票数：26
                    窗口1 卖出第  26 张票，剩余的票数：25
                    窗口1 卖出第  25 张票，剩余的票数：24
                    窗口1 卖出第  24 张票，剩余的票数：23
                    窗口1 卖出第  23 张票，剩余的票数：22
                    窗口1 卖出第  22 张票，剩余的票数：21
                    窗口1 卖出第  21 张票，剩余的票数：20
                    窗口1 卖出第  20 张票，剩余的票数：19
                    窗口2 卖出第  19 张票，剩余的票数：18
                    窗口2 卖出第  18 张票，剩余的票数：17
                    窗口2 卖出第  17 张票，剩余的票数：16
                    窗口2 卖出第  16 张票，剩余的票数：15
                    窗口2 卖出第  15 张票，剩余的票数：14
                    窗口2 卖出第  14 张票，剩余的票数：13
                    窗口2 卖出第  13 张票，剩余的票数：12
                    窗口2 卖出第  12 张票，剩余的票数：11
                    窗口2 卖出第  11 张票，剩余的票数：10
                    窗口2 卖出第  10 张票，剩余的票数：9
                    窗口2 卖出第  9 张票，剩余的票数：8
                    窗口2 卖出第  8 张票，剩余的票数：7
                    窗口2 卖出第  7 张票，剩余的票数：6
                    窗口2 卖出第  6 张票，剩余的票数：5
                    窗口2 卖出第  5 张票，剩余的票数：4
                    窗口2 卖出第  4 张票，剩余的票数：3
                    窗口2 卖出第  3 张票，剩余的票数：2
                    窗口2 卖出第  2 张票，剩余的票数：1
                    窗口2 卖出第  1 张票，剩余的票数：0
                    </code></pre>
                    
   * Android中的线程 ：
                   
        AsyncTask：
        
        AsyncTask不同版本的区别：
                
   * 线程池
        
        * 什么是线程池
            
            * 线程池是指在初始化一个多线程应用程序过程中创建一个线程集合，然后在需要执行新的任务时重用这些线程而不是新建一个线程（提高线程复用，减少性能开销）。线程池中线程的数量通常完全取决于可用内存数量和应用程序的需求。然而，增加可用线程数量是可能的。线程池中的每个线程都有被分配一个任务，一旦任务已经完成了，线程回到池子中然后等待下一次分配任务。
            
        * 为什么要用线程池
            
            * 线程池改进了一个应用程序的响应时间。由于线程池中的线程已经准备好且等待被分配任务，应用程序可以直接拿来使用而不用新建一个线程。
             
            * 线程池节省了CLR 为每个短生存周期任务创建一个完整的线程的开销并可以在任务完成后回收资源。
            
            * 线程池根据当前在系统中运行的进程来优化线程时间片。
            
            * 线程池允许我们开启多个任务而不用为每个线程设置属性。
            
            * 线程池允许我们为正在执行的任务的程序参数传递一个包含状态信息的对象引用。
            
            * 线程池可以用来解决处理一个特定请求最大线程数量限制问题。
        
            本质上来讲，我们使用线程池主要就是为了减少了创建和销毁线程的次数，每个工作线程都可以被重复利用，可执行多个任务；节约应用内存（线程开的越多，消耗的内存也就越大，最后死机）
        
        * 线程池的作用    
        
            线程池作用就是限制系统中执行线程的数量
            
            <div>
                <img src="https://upload-images.jianshu.io/upload_images/5417430-e6280fbf9d7fd0c2.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/700" />
            </div>
            
            <div>
               <img src="https://upload-images.jianshu.io/upload_images/5417430-fd398e41f1c3b25d.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/382" />
            </div>
            
            <div>
                <img src="https://upload-images.jianshu.io/upload_images/5417430-3e68c3f1e21b3190.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/601" />
            </div>
            
          1：int corePoolSize （core：核心的） = >  该线程池中核心线程数最大值
          
          什么是核心线程：线程池新建线程的时候，如果当前线程总数小于 corePoolSize ，则新建的是核心线程；如果超过corePoolSize，则新建的是非核心线程。
          
          核心线程默认情况下会一直存活在线程池中，即使这个核心线程啥也不干(闲置状态)。
          
          如果指定ThreadPoolExecutor的 allowCoreThreadTimeOut 这个属性为true，那么核心线程如果不干活(闲置状态)的话，超过一定时间( keepAliveTime)，就会被销毁掉
          
          2：int maximumPoolSize  = >  该线程池中线程总数的最大值
          
          线程总数计算公式 = 核心线程数 + 非核心线程数。
          
          3：long keepAliveTime  = >  该线程池中非核心线程闲置超时时长
          
          注意：一个非核心线程，如果不干活(闲置状态)的时长，超过这个参数所设定的时长，就会被销毁掉。但是，如果设置了  allowCoreThreadTimeOut = true，则会作用于核心线程。
          
          4：TimeUnit unit  = > （时间单位）
          
          首先，TimeUnit是一个枚举类型，翻译过来就是时间单位，我们最常用的时间单位包括：
          
          MILLISECONDS ： 1毫秒 、SECONDS ： 秒、MINUTES ： 分、HOURS ： 小时、DAYS ： 天
          
          5：BlockingQueue<Runnable> workQueue = >( Blocking：阻塞的，queue：队列)
          
          [参考：必须要理清的Java线程池](https://www.jianshu.com/p/50fffbf21b39)
          
        * 线程池（[郭霖转载：Java线程池线程复用的秘密](https://mp.weixin.qq.com/s?__biz=MzA5MzI3NjE2MA==&mid=2650243061&idx=1&sn=89013ccef91c82edc844a57889da95ca&chksm=88638e9abf14078c881dc41ab67ddd9bb41d61291ea335a474b63d99129e9133b9f857f2a863&mpshare=1&scene=23&srcid=0521FckwVxuRXClqRKWlw6iF#rd)）       
            
            > 讲解思路 -> 创建线程池的参数 -> 构造方法 -> 
        
            * 创建线程池之后需要重写的方法
            
                * corePoolSize，核心线程的大小
                
                * runnableTaskQueue，任务队列，保存等待执行的任务的阻塞队列（对线程池运行逻辑有很大影响），可选：
                    
                    - 1、ArrayBlockingQueue：是一个基于数组的有界阻塞队列，按FIFO(先进先出)
                    
                    - 2、LinkedBlockingQueue：是一个基于链表结构的阻塞队列，按FIFO排序，吞吐量大于ArrayBlockingQueue，静态工厂方法：Executor.newFixedThreadPool()；
                    
                    - 3、SynchronousQueue：是一个不存储元素的阻塞队列，每个插入操作都必须等到上一个元素被移除，否则一直处于阻塞状态吞吐量大于LinkedBlockingQueue，静态工作方法：Executors.newCachedThreadPool使用了这个队列
                    
                    - 4、priorityQueue：是一个有优先顺序的无限阻塞队列
                
                * maximumPoolSize，线程池最大的大小：最大的线程数量
                    
                    > 注意使用无界队列之后这个参数无效
                    
                * keepAliveTime：线程结束之后，保存的时间
                
                * ThreadFactory：创建线程池的工厂类
                
                * RejectedExecutionHandler：线程池饱和后的执行方式，默认采用的是AbortPolicy：jdk提供四种方式：
                   
                   - 1、AbortPolicy，直接抛出异常
                   
                   - 1、CallerRunsPolicy，只用调用者所在的线程来运行任务
                   
                   - 2、DiscardOldesPolicy，丢弃最后一个执行的任务，并运行新的任务
                   
                   - 1、DiscardPolicy：不处理，丢弃掉
                   
                * TimeUnit：keepAlive的时间单位，天（Days） 、小时(HOURS) 、分(MINUTES) 、毫秒(MILLISECONDS)、微秒(MICROSECONDS)、和毫微秒(NANOSECONDS, 千分之一微秒)。
                
                 我们来看看 Executors.newCachedThreadPool() 里面的构造：
                
                <pre style="font-size: inherit;color: inherit;line-height: inherit;margin-top: 0px;margin-bottom: 0px;padding: 0px;"><code class="" style="margin-right: 2px;margin-left: 2px;line-height: 15px;font-size: 11px;word-spacing: -3px;letter-spacing: 0px;font-family: Consolas, Inconsolata, Courier, monospace;border-radius: 0px;padding: 0.5em;background: rgb(63, 63, 63);color: rgb(220, 220, 220);display: block !important;word-wrap: normal !important;word-break: normal !important;overflow: auto !important;"><span class="" style="font-size: inherit;color: inherit;line-height: inherit;word-wrap: inherit !important;word-break: inherit !important;"><span class="" style="font-size: inherit;line-height: inherit;color: rgb(227, 206, 171);word-wrap: inherit !important;word-break: inherit !important;">public</span> <span class="" style="font-size: inherit;line-height: inherit;color: rgb(227, 206, 171);word-wrap: inherit !important;word-break: inherit !important;">static</span> ExecutorService <span class="" style="font-size: inherit;line-height: inherit;color: rgb(239, 239, 143);word-wrap: inherit !important;word-break: inherit !important;">newCachedThreadPool</span><span class="" style="font-size: inherit;color: inherit;line-height: inherit;word-wrap: inherit !important;word-break: inherit !important;">()</span> </span>{<br> &nbsp; &nbsp; &nbsp; &nbsp;<span class="" style="font-size: inherit;line-height: inherit;color: rgb(227, 206, 171);word-wrap: inherit !important;word-break: inherit !important;">return</span> <span class="" style="font-size: inherit;line-height: inherit;color: rgb(227, 206, 171);word-wrap: inherit !important;word-break: inherit !important;">new</span> ThreadPoolExecutor(<span class="" style="font-size: inherit;line-height: inherit;color: rgb(140, 208, 211);word-wrap: inherit !important;word-break: inherit !important;">0</span>, Integer.MAX_VALUE,<br> &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;<span class="" style="font-size: inherit;line-height: inherit;color: rgb(140, 208, 211);word-wrap: inherit !important;word-break: inherit !important;">60L</span>, TimeUnit.SECONDS,<br> &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;<span class="" style="font-size: inherit;line-height: inherit;color: rgb(227, 206, 171);word-wrap: inherit !important;word-break: inherit !important;">new</span> SynchronousQueue&lt;Runnable&gt;());<br> &nbsp; &nbsp;}<br></code></pre>
                
                * 构造函数：
                    
                     - 1、corePoolSize为零，核心线程数为0
                     
                     - 2、maximumPoolSize 为Integer.MAX_VALUE => 可以无限的向线程池中添加任务不会执行reject策略
                     
                     - 3、keepAliveTime和unit决定线程的存活时间是60s，意味着一个空线程60s之后才会被回收
                     
                     - 4、reject策略默认的是AbortPolicy，但是由于CacheThreadSize没有限制，所以不会抛出异常
                     
                     - 5、runnableTaskQueue采用的是synchronousQueue，所以不存储元素的队列，没插入一个操作要等到另一个线程调用移除操作，否则插入操作一直阻塞，他是实现CacheThreadPool的关键之一
                     
                     - 扩展知识：SynchronousQueue 的详细原理参考：
                       
                        > https://blog.csdn.net/yanyan19880509/article/details/52562039
                        
                * 适用执行很多短时间的任务
                
                    - 1、CacheThreadPool如何实现，线程保留60s ？
                    
                    - 2、CacheThreadPool如何实现复用的 ？
                    
                        * code
                        
                            <span style="font-size: 14px;">首先我们向线程池提交任务一般用 execute() 方法，我们就从这里入手：</span>
                            <section class="" style="font-size: 16px;color: rgb(62, 62, 62);line-height: 1.6;letter-spacing: 0px;"><pre style="font-size: inherit;color: inherit;line-height: inherit;margin-top: 0px;margin-bottom: 0px;padding: 0px;"><code class="" style="margin-right: 2px;margin-left: 2px;line-height: 15px;font-size: 11px;word-spacing: -3px;letter-spacing: 0px;font-family: Consolas, Inconsolata, Courier, monospace;border-radius: 0px;padding: 0.5em;background: rgb(63, 63, 63);color: rgb(220, 220, 220);display: block !important;word-wrap: normal !important;word-break: normal !important;overflow: auto !important;"><span class="" style="font-size: inherit;color: inherit;line-height: inherit;word-wrap: inherit !important;word-break: inherit !important;"><span class="" style="font-size: inherit;line-height: inherit;color: rgb(227, 206, 171);word-wrap: inherit !important;word-break: inherit !important;">public</span> <span class="" style="font-size: inherit;line-height: inherit;color: rgb(227, 206, 171);word-wrap: inherit !important;word-break: inherit !important;">void</span> <span class="" style="font-size: inherit;line-height: inherit;color: rgb(239, 239, 143);word-wrap: inherit !important;word-break: inherit !important;">execute</span><span class="" style="font-size: inherit;color: inherit;line-height: inherit;word-wrap: inherit !important;word-break: inherit !important;">(Runnable command)</span> </span>{<br> &nbsp;<span class="" style="font-size: inherit;line-height: inherit;color: rgb(227, 206, 171);word-wrap: inherit !important;word-break: inherit !important;">if</span> (command == <span class="" style="font-size: inherit;line-height: inherit;color: rgb(227, 206, 171);word-wrap: inherit !important;word-break: inherit !important;">null</span>)<br> &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;<span class="" style="font-size: inherit;line-height: inherit;color: rgb(227, 206, 171);word-wrap: inherit !important;word-break: inherit !important;">throw</span> <span class="" style="font-size: inherit;line-height: inherit;color: rgb(227, 206, 171);word-wrap: inherit !important;word-break: inherit !important;">new</span> NullPointerException();<br> &nbsp; &nbsp; &nbsp; &nbsp;<span class="" style="font-size: inherit;line-height: inherit;color: rgb(127, 159, 127);word-wrap: inherit !important;word-break: inherit !important;">//1.如果当前存在的线程少于corePoolSize，会新建线程来执行任务。然后各种检查状态</span><br> &nbsp; &nbsp; &nbsp; &nbsp;<span class="" style="font-size: inherit;line-height: inherit;color: rgb(227, 206, 171);word-wrap: inherit !important;word-break: inherit !important;">int</span> c = ctl.get();<br> &nbsp; &nbsp; &nbsp; &nbsp;<span class="" style="font-size: inherit;line-height: inherit;color: rgb(227, 206, 171);word-wrap: inherit !important;word-break: inherit !important;">if</span> (workerCountOf(c) &lt; corePoolSize) {<br> &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;<span class="" style="font-size: inherit;line-height: inherit;color: rgb(227, 206, 171);word-wrap: inherit !important;word-break: inherit !important;">if</span> (addWorker(command, <span class="" style="font-size: inherit;line-height: inherit;color: rgb(227, 206, 171);word-wrap: inherit !important;word-break: inherit !important;">true</span>))<br> &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;<span class="" style="font-size: inherit;line-height: inherit;color: rgb(227, 206, 171);word-wrap: inherit !important;word-break: inherit !important;">return</span>;<br> &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;c = ctl.get();<br> &nbsp; &nbsp; &nbsp; &nbsp;}<br> &nbsp; &nbsp; &nbsp; &nbsp;<span class="" style="font-size: inherit;line-height: inherit;color: rgb(127, 159, 127);word-wrap: inherit !important;word-break: inherit !important;">//2.如果task被成功加入队列，还是要double-check</span><br> &nbsp; &nbsp; &nbsp; &nbsp;<span class="" style="font-size: inherit;line-height: inherit;color: rgb(227, 206, 171);word-wrap: inherit !important;word-break: inherit !important;">if</span> (isRunning(c) &amp;&amp; workQueue.offer(command)) {<br> &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;<span class="" style="font-size: inherit;line-height: inherit;color: rgb(227, 206, 171);word-wrap: inherit !important;word-break: inherit !important;">int</span> recheck = ctl.get();<br> &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;<span class="" style="font-size: inherit;line-height: inherit;color: rgb(227, 206, 171);word-wrap: inherit !important;word-break: inherit !important;">if</span> (! isRunning(recheck) &amp;&amp; remove(command))<br> &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;reject(command);<br> &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;<span class="" style="font-size: inherit;line-height: inherit;color: rgb(227, 206, 171);word-wrap: inherit !important;word-break: inherit !important;">else</span> <span class="" style="font-size: inherit;line-height: inherit;color: rgb(227, 206, 171);word-wrap: inherit !important;word-break: inherit !important;">if</span> (workerCountOf(recheck) == <span class="" style="font-size: inherit;line-height: inherit;color: rgb(140, 208, 211);word-wrap: inherit !important;word-break: inherit !important;">0</span>)<br> &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;addWorker(<span class="" style="font-size: inherit;line-height: inherit;color: rgb(227, 206, 171);word-wrap: inherit !important;word-break: inherit !important;">null</span>, <span class="" style="font-size: inherit;line-height: inherit;color: rgb(227, 206, 171);word-wrap: inherit !important;word-break: inherit !important;">false</span>);<br> &nbsp; &nbsp; &nbsp; &nbsp;}<br> &nbsp; &nbsp; &nbsp; &nbsp;<span class="" style="font-size: inherit;line-height: inherit;color: rgb(127, 159, 127);word-wrap: inherit !important;word-break: inherit !important;">//3.如果task不能加入到队列，会尝试创建线程。如果创建失败，走reject流程</span><br> &nbsp; &nbsp; &nbsp; &nbsp;<span class="" style="font-size: inherit;line-height: inherit;color: rgb(227, 206, 171);word-wrap: inherit !important;word-break: inherit !important;">else</span> <span class="" style="font-size: inherit;line-height: inherit;color: rgb(227, 206, 171);word-wrap: inherit !important;word-break: inherit !important;">if</span> (!addWorker(command, <span class="" style="font-size: inherit;line-height: inherit;color: rgb(227, 206, 171);word-wrap: inherit !important;word-break: inherit !important;">false</span>))<br> &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;reject(command);<br></code></pre></section>
                            
                            - 第一步：如果小于当前的核心线程数，就调用addWork()，但是由于CacheThreadPool的核心线程数为0,所以这一步跳过不会创建线程池
                           
                            - 第二步：检查是够运行，然后调用workQueue.offer()，添加task。workQueue是一个BlockingQueue，BlockingQueue.offer()，是向队列插入元素，
                            如果成功就返回true。CacheThreadPool采用的是SynchronousQueue,这里当任务入队列成功后，再次检查了线程池状态，还是运行状态就继续。然后检查当前运行线程数量，如果当前没有运行中的线程，调用 addWorker() ，第一个参数为 null 第二个参数是 false ，标明了非核心线程。
                            
                            为什么第一参数是null?
                            
                            - 查看代码
                                
                                <section class="" style="font-size: 16px;color: rgb(62, 62, 62);line-height: 1.6;letter-spacing: 0px;"><pre style="font-size: inherit;color: inherit;line-height: inherit;margin-top: 0px;margin-bottom: 0px;padding: 0px;"><code class="" style="margin-right: 2px;margin-left: 2px;line-height: 15px;font-size: 11px;word-spacing: -3px;letter-spacing: 0px;font-family: Consolas, Inconsolata, Courier, monospace;border-radius: 0px;padding: 0.5em;background: rgb(63, 63, 63);color: rgb(220, 220, 220);display: block !important;word-wrap: normal !important;word-break: normal !important;overflow: auto !important;"><span class="" style="font-size: inherit;color: inherit;line-height: inherit;word-wrap: inherit !important;word-break: inherit !important;"><span class="" style="font-size: inherit;line-height: inherit;color: rgb(227, 206, 171);word-wrap: inherit !important;word-break: inherit !important;">private</span> <span class="" style="font-size: inherit;line-height: inherit;color: rgb(227, 206, 171);word-wrap: inherit !important;word-break: inherit !important;">boolean</span> <span class="" style="font-size: inherit;line-height: inherit;color: rgb(239, 239, 143);word-wrap: inherit !important;word-break: inherit !important;">addWorker</span><span class="" style="font-size: inherit;color: inherit;line-height: inherit;word-wrap: inherit !important;word-break: inherit !important;">(Runnable firstTask, <span class="" style="font-size: inherit;line-height: inherit;color: rgb(227, 206, 171);word-wrap: inherit !important;word-break: inherit !important;">boolean</span> core)</span> </span>{<br> &nbsp; &nbsp; <span class="" style="font-size: inherit;line-height: inherit;color: rgb(127, 159, 127);word-wrap: inherit !important;word-break: inherit !important;">//...这里有一段cas代码，通过双重循环目的是通过cas增加线程池线程个数</span><br> &nbsp; &nbsp; <span class="" style="font-size: inherit;line-height: inherit;color: rgb(227, 206, 171);word-wrap: inherit !important;word-break: inherit !important;">boolean</span> workerStarted = <span class="" style="font-size: inherit;line-height: inherit;color: rgb(227, 206, 171);word-wrap: inherit !important;word-break: inherit !important;">false</span>;<br> &nbsp; &nbsp; <span class="" style="font-size: inherit;line-height: inherit;color: rgb(227, 206, 171);word-wrap: inherit !important;word-break: inherit !important;">boolean</span> workerAdded = <span class="" style="font-size: inherit;line-height: inherit;color: rgb(227, 206, 171);word-wrap: inherit !important;word-break: inherit !important;">false</span>;<br> &nbsp; &nbsp; Worker w = <span class="" style="font-size: inherit;line-height: inherit;color: rgb(227, 206, 171);word-wrap: inherit !important;word-break: inherit !important;">null</span>;<br> &nbsp; &nbsp; <span class="" style="font-size: inherit;line-height: inherit;color: rgb(227, 206, 171);word-wrap: inherit !important;word-break: inherit !important;">try</span> {<br> &nbsp; &nbsp; &nbsp; &nbsp; w = <span class="" style="font-size: inherit;line-height: inherit;color: rgb(227, 206, 171);word-wrap: inherit !important;word-break: inherit !important;">new</span> Worker(firstTask);<br> &nbsp; &nbsp; &nbsp; &nbsp; <span class="" style="font-size: inherit;line-height: inherit;color: rgb(227, 206, 171);word-wrap: inherit !important;word-break: inherit !important;">final</span> Thread t = w.thread;<br> &nbsp; &nbsp; &nbsp;<span class="" style="font-size: inherit;line-height: inherit;color: rgb(127, 159, 127);word-wrap: inherit !important;word-break: inherit !important;">//...省略部分代码</span><br> &nbsp; &nbsp; &nbsp;workers.add(w);<br> &nbsp; &nbsp; &nbsp;<span class="" style="font-size: inherit;line-height: inherit;color: rgb(127, 159, 127);word-wrap: inherit !important;word-break: inherit !important;">//...省略部分代码</span><br> &nbsp; &nbsp; &nbsp;workerAdded=<span class="" style="font-size: inherit;line-height: inherit;color: rgb(227, 206, 171);word-wrap: inherit !important;word-break: inherit !important;">true</span>;<br> &nbsp; &nbsp; &nbsp;<span class="" style="font-size: inherit;line-height: inherit;color: rgb(227, 206, 171);word-wrap: inherit !important;word-break: inherit !important;">if</span> (workerAdded) {<br> &nbsp; &nbsp; &nbsp; &nbsp;t.start();<br> &nbsp; &nbsp; &nbsp; &nbsp;workerStarted = <span class="" style="font-size: inherit;line-height: inherit;color: rgb(227, 206, 171);word-wrap: inherit !important;word-break: inherit !important;">true</span>;<br> &nbsp; &nbsp; &nbsp; &nbsp;}<br> }<br></code></pre></section>
                                
                                第一步是一段 cas 代码通过双重循环检查状态并为当前线程数扩容 +1，第二部是将任务包装成 worker 对象，用线程安全的方式添加到当前工作 HashSet() 里，并开始执行线程。
                                
                                但是我们注意到，task 为 null ，Worker 里面的 firstTask 是 null ，那么 wokrer thread 里面是怎么工作下去的呢?继续跟踪代码，Worker 类继承 Runnable 接口，因此 worker thread start 后，走的是 worker.run()方法：
                            
                                <pre style="font-size: inherit;color: inherit;line-height: inherit;margin-top: 0px;margin-bottom: 0px;padding: 0px;"><code class="" style="margin-right: 2px;margin-left: 2px;line-height: 15px;font-size: 11px;word-spacing: -3px;letter-spacing: 0px;font-family: Consolas, Inconsolata, Courier, monospace;border-radius: 0px;padding: 0.5em;background: rgb(63, 63, 63);color: rgb(220, 220, 220);display: block !important;word-wrap: normal !important;word-break: normal !important;overflow: auto !important;"><span class="" style="font-size: inherit;color: inherit;line-height: inherit;word-wrap: inherit !important;word-break: inherit !important;"><span class="" style="font-size: inherit;line-height: inherit;color: rgb(227, 206, 171);word-wrap: inherit !important;word-break: inherit !important;">public</span> <span class="" style="font-size: inherit;line-height: inherit;color: rgb(227, 206, 171);word-wrap: inherit !important;word-break: inherit !important;">void</span> <span class="" style="font-size: inherit;line-height: inherit;color: rgb(239, 239, 143);word-wrap: inherit !important;word-break: inherit !important;">run</span><span class="" style="font-size: inherit;color: inherit;line-height: inherit;word-wrap: inherit !important;word-break: inherit !important;">()</span> </span>{<br> &nbsp; &nbsp;runWorker(<span class="" style="font-size: inherit;line-height: inherit;color: rgb(227, 206, 171);word-wrap: inherit !important;word-break: inherit !important;">this</span>);<br>}<br></code></pre>
                                
                                <section class="" style="font-size: 16px;color: rgb(62, 62, 62);line-height: 1.6;letter-spacing: 0px;"><pre style="font-size: inherit;color: inherit;line-height: inherit;margin-top: 0px;margin-bottom: 0px;padding: 0px;"><code class="" style="margin-right: 2px;margin-left: 2px;line-height: 15px;font-size: 11px;word-spacing: -3px;letter-spacing: 0px;font-family: Consolas, Inconsolata, Courier, monospace;border-radius: 0px;padding: 0.5em;background: rgb(63, 63, 63);color: rgb(220, 220, 220);display: block !important;word-wrap: normal !important;word-break: normal !important;overflow: auto !important;"><span class="" style="font-size: inherit;color: inherit;line-height: inherit;word-wrap: inherit !important;word-break: inherit !important;"><span class="" style="font-size: inherit;line-height: inherit;color: rgb(227, 206, 171);word-wrap: inherit !important;word-break: inherit !important;">final</span> <span class="" style="font-size: inherit;line-height: inherit;color: rgb(227, 206, 171);word-wrap: inherit !important;word-break: inherit !important;">void</span> <span class="" style="font-size: inherit;line-height: inherit;color: rgb(239, 239, 143);word-wrap: inherit !important;word-break: inherit !important;">runWorker</span><span class="" style="font-size: inherit;color: inherit;line-height: inherit;word-wrap: inherit !important;word-break: inherit !important;">(Worker w)</span> </span>{<br> &nbsp; &nbsp; &nbsp; &nbsp;Thread wt = Thread.currentThread();<br> &nbsp; &nbsp; &nbsp; &nbsp;Runnable task = w.firstTask;<br> &nbsp; &nbsp; &nbsp; &nbsp;w.firstTask = <span class="" style="font-size: inherit;line-height: inherit;color: rgb(227, 206, 171);word-wrap: inherit !important;word-break: inherit !important;">null</span>;<br> &nbsp; &nbsp; &nbsp; &nbsp;w.unlock(); <span class="" style="font-size: inherit;line-height: inherit;color: rgb(127, 159, 127);word-wrap: inherit !important;word-break: inherit !important;">// allow interrupts</span><br> &nbsp; &nbsp; &nbsp; &nbsp;<span class="" style="font-size: inherit;line-height: inherit;color: rgb(227, 206, 171);word-wrap: inherit !important;word-break: inherit !important;">boolean</span> completedAbruptly = <span class="" style="font-size: inherit;line-height: inherit;color: rgb(227, 206, 171);word-wrap: inherit !important;word-break: inherit !important;">true</span>;<br> &nbsp; &nbsp; &nbsp;<span class="" style="font-size: inherit;line-height: inherit;color: rgb(127, 159, 127);word-wrap: inherit !important;word-break: inherit !important;">//省略代码</span><br> &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;<span class="" style="font-size: inherit;line-height: inherit;color: rgb(227, 206, 171);word-wrap: inherit !important;word-break: inherit !important;">while</span> (task != <span class="" style="font-size: inherit;line-height: inherit;color: rgb(227, 206, 171);word-wrap: inherit !important;word-break: inherit !important;">null</span> || (task = getTask()) != <span class="" style="font-size: inherit;line-height: inherit;color: rgb(227, 206, 171);word-wrap: inherit !important;word-break: inherit !important;">null</span>) {<br> &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;<span class="" style="font-size: inherit;line-height: inherit;color: rgb(127, 159, 127);word-wrap: inherit !important;word-break: inherit !important;">//..省略</span><br> &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;<span class="" style="font-size: inherit;line-height: inherit;color: rgb(227, 206, 171);word-wrap: inherit !important;word-break: inherit !important;">try</span> {<br> &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;beforeExecute(wt, task);<br> &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;Throwable thrown = <span class="" style="font-size: inherit;line-height: inherit;color: rgb(227, 206, 171);word-wrap: inherit !important;word-break: inherit !important;">null</span>;<br> &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;<span class="" style="font-size: inherit;line-height: inherit;color: rgb(227, 206, 171);word-wrap: inherit !important;word-break: inherit !important;">try</span> {<br> &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;task.run();<br> &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;} <span class="" style="font-size: inherit;line-height: inherit;color: rgb(227, 206, 171);word-wrap: inherit !important;word-break: inherit !important;">catch</span> (Exception x) {<br> &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;thrown = x; <span class="" style="font-size: inherit;line-height: inherit;color: rgb(227, 206, 171);word-wrap: inherit !important;word-break: inherit !important;">throw</span> x;<br> &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;}<br> &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;<span class="" style="font-size: inherit;line-height: inherit;color: rgb(127, 159, 127);word-wrap: inherit !important;word-break: inherit !important;">//省略代码</span><br> &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;}<br> &nbsp; &nbsp; &nbsp; &nbsp;<span class="" style="font-size: inherit;line-height: inherit;color: rgb(127, 159, 127);word-wrap: inherit !important;word-break: inherit !important;">//省略代码</span><br> &nbsp; &nbsp;}<br></code></pre></section>
                                
                                * 可以看到这里判断了 firstTask 如果为空，就调用 getTask() 方法。getTask() 方法是从 workQueue 拉取任务。所以到这里之前的疑问就解决了，调用 addWorker(null,false) 的目的是启动一个线程，然后再 workQueue 拉取任务执行。继续跟踪 getTask() 方法：
                                
                               <section class="" style="font-size: 16px;color: rgb(62, 62, 62);line-height: 1.6;letter-spacing: 0px;"><pre style="font-size: inherit;color: inherit;line-height: inherit;margin-top: 0px;margin-bottom: 0px;padding: 0px;"><code class="" style="margin-right: 2px;margin-left: 2px;line-height: 15px;font-size: 11px;word-spacing: -3px;letter-spacing: 0px;font-family: Consolas, Inconsolata, Courier, monospace;border-radius: 0px;padding: 0.5em;background: rgb(63, 63, 63);color: rgb(220, 220, 220);display: block !important;word-wrap: normal !important;word-break: normal !important;overflow: auto !important;"><span class="" style="font-size: inherit;color: inherit;line-height: inherit;word-wrap: inherit !important;word-break: inherit !important;"><span class="" style="font-size: inherit;line-height: inherit;color: rgb(227, 206, 171);word-wrap: inherit !important;word-break: inherit !important;">private</span> Runnable <span class="" style="font-size: inherit;line-height: inherit;color: rgb(239, 239, 143);word-wrap: inherit !important;word-break: inherit !important;">getTask</span><span class="" style="font-size: inherit;color: inherit;line-height: inherit;word-wrap: inherit !important;word-break: inherit !important;">()</span> </span>{<br> &nbsp; &nbsp;<span class="" style="font-size: inherit;line-height: inherit;color: rgb(227, 206, 171);word-wrap: inherit !important;word-break: inherit !important;">boolean</span> timedOut = <span class="" style="font-size: inherit;line-height: inherit;color: rgb(227, 206, 171);word-wrap: inherit !important;word-break: inherit !important;">false</span>; <span class="" style="font-size: inherit;line-height: inherit;color: rgb(127, 159, 127);word-wrap: inherit !important;word-break: inherit !important;">// Did the last poll() time out?</span><br><br> &nbsp; &nbsp;<span class="" style="font-size: inherit;line-height: inherit;color: rgb(227, 206, 171);word-wrap: inherit !important;word-break: inherit !important;">for</span> (;;) {<br> &nbsp; &nbsp; &nbsp; &nbsp;<span class="" style="font-size: inherit;line-height: inherit;color: rgb(127, 159, 127);word-wrap: inherit !important;word-break: inherit !important;">//..省略</span><br><br> &nbsp; &nbsp; &nbsp; &nbsp;<span class="" style="font-size: inherit;line-height: inherit;color: rgb(127, 159, 127);word-wrap: inherit !important;word-break: inherit !important;">// Are workers subject to culling?</span><br> &nbsp; &nbsp; &nbsp; &nbsp;<span class="" style="font-size: inherit;line-height: inherit;color: rgb(227, 206, 171);word-wrap: inherit !important;word-break: inherit !important;">boolean</span> timed = allowCoreThreadTimeOut || wc &gt; corePoolSize;<br> &nbsp; &nbsp; &nbsp; <span class="" style="font-size: inherit;line-height: inherit;color: rgb(127, 159, 127);word-wrap: inherit !important;word-break: inherit !important;">//..省略</span><br><br> &nbsp; &nbsp; &nbsp; &nbsp;<span class="" style="font-size: inherit;line-height: inherit;color: rgb(227, 206, 171);word-wrap: inherit !important;word-break: inherit !important;">try</span> {<br> &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;Runnable r = timed ?<br> &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;workQueue.poll(keepAliveTime, TimeUnit.NANOSECONDS) :<br> &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;workQueue.take();<br> &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;<span class="" style="font-size: inherit;line-height: inherit;color: rgb(227, 206, 171);word-wrap: inherit !important;word-break: inherit !important;">if</span> (r != <span class="" style="font-size: inherit;line-height: inherit;color: rgb(227, 206, 171);word-wrap: inherit !important;word-break: inherit !important;">null</span>)<br> &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;<span class="" style="font-size: inherit;line-height: inherit;color: rgb(227, 206, 171);word-wrap: inherit !important;word-break: inherit !important;">return</span> r;<br> &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;timedOut = <span class="" style="font-size: inherit;line-height: inherit;color: rgb(227, 206, 171);word-wrap: inherit !important;word-break: inherit !important;">true</span>;<br> &nbsp; &nbsp; &nbsp; &nbsp;} <span class="" style="font-size: inherit;line-height: inherit;color: rgb(227, 206, 171);word-wrap: inherit !important;word-break: inherit !important;">catch</span> (InterruptedException retry) {<br> &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;timedOut = <span class="" style="font-size: inherit;line-height: inherit;color: rgb(227, 206, 171);word-wrap: inherit !important;word-break: inherit !important;">false</span>;<br> &nbsp; &nbsp; &nbsp; &nbsp;}<br> &nbsp; &nbsp;}<br>}<br></code></pre></section>
                               
                               终于看到从 workQueue 拉取元素了。 CacheThreadPool 构造的时候 corePoolSize 是 0，allowCoreThreadTimeOut 默认是 false ，因此 timed 一直为 true ,会调用 workQueue.poll() 从队列拉取一个任务，等待 60s， 60s后超时,线程就会会被回收。如果 60s 内，进来一个任务，会发生什么情况?任务在 execute() 方法里，会被 offer() 进 workQueue ，因为目前队列是空的，所以 offer 进来后，马上会被阻塞的 worker.poll() 拉取出来，然后在 runWorker() 方法里执行，因为线程没有新建所以达到了线程的复用。至此，我们已经明白了线程复用的秘密，以及线程保留 60s 的实现方法。回到 execute() 方法，还有剩下一个逻辑
                               
                               <pre style="font-size: inherit;color: inherit;line-height: inherit;margin-top: 0px;margin-bottom: 0px;padding: 0px;"><code class="" style="margin-right: 2px;margin-left: 2px;line-height: 15px;font-size: 11px;word-spacing: -3px;letter-spacing: 0px;font-family: Consolas, Inconsolata, Courier, monospace;border-radius: 0px;padding: 0.5em;background: rgb(63, 63, 63);color: rgb(220, 220, 220);display: block !important;word-wrap: normal !important;word-break: normal !important;overflow: auto !important;"><span class="" style="font-size: inherit;line-height: inherit;color: rgb(127, 159, 127);word-wrap: inherit !important;word-break: inherit !important;">//3.如果task不能加入到队列，会尝试创建线程。如果创建失败，走reject流程</span><br><span class="" style="font-size: inherit;line-height: inherit;color: rgb(227, 206, 171);word-wrap: inherit !important;word-break: inherit !important;">else</span> <span class="" style="font-size: inherit;line-height: inherit;color: rgb(227, 206, 171);word-wrap: inherit !important;word-break: inherit !important;">if</span> (!addWorker(command, <span class="" style="font-size: inherit;line-height: inherit;color: rgb(227, 206, 171);word-wrap: inherit !important;word-break: inherit !important;">false</span>))<br> &nbsp; &nbsp;reject(command);<br></code></pre>
                               
                               因为 CacheThreadPool 用的 SynchronousQueue ,所以没有空闲线程， SynchronousQueue 有一个元素正在被阻塞，那么就不能加入到队列里。会走到 addWorker(commond,false) 这里，这个时候因为就会新建线程来执行任务。如果 addWorker() 返回 false 才会走 reject 策略。那么什么时候 addWorker() 什么时候会返回false呢？我们看代码：
                               
                               <pre style="font-size: inherit;color: inherit;line-height: inherit;margin-top: 0px;margin-bottom: 0px;padding: 0px;"><code class="" style="margin-right: 2px;margin-left: 2px;line-height: 15px;font-size: 11px;word-spacing: -3px;letter-spacing: 0px;font-family: Consolas, Inconsolata, Courier, monospace;border-radius: 0px;padding: 0.5em;background: rgb(63, 63, 63);color: rgb(220, 220, 220);display: block !important;word-wrap: normal !important;word-break: normal !important;overflow: auto !important;"><span class="" style="font-size: inherit;color: inherit;line-height: inherit;word-wrap: inherit !important;word-break: inherit !important;"><span class="" style="font-size: inherit;line-height: inherit;color: rgb(227, 206, 171);word-wrap: inherit !important;word-break: inherit !important;">private</span> <span class="" style="font-size: inherit;line-height: inherit;color: rgb(227, 206, 171);word-wrap: inherit !important;word-break: inherit !important;">boolean</span> <span class="" style="font-size: inherit;line-height: inherit;color: rgb(239, 239, 143);word-wrap: inherit !important;word-break: inherit !important;">addWorker</span><span class="" style="font-size: inherit;color: inherit;line-height: inherit;word-wrap: inherit !important;word-break: inherit !important;">(Runnable firstTask, <span class="" style="font-size: inherit;line-height: inherit;color: rgb(227, 206, 171);word-wrap: inherit !important;word-break: inherit !important;">boolean</span> core)</span> </span>{<br> &nbsp; &nbsp; &nbsp; &nbsp;retry:<br> &nbsp; &nbsp; &nbsp; &nbsp;<span class="" style="font-size: inherit;line-height: inherit;color: rgb(227, 206, 171);word-wrap: inherit !important;word-break: inherit !important;">for</span> (;;) {<br> &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;<span class="" style="font-size: inherit;line-height: inherit;color: rgb(227, 206, 171);word-wrap: inherit !important;word-break: inherit !important;">int</span> c = ctl.get();<br> &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;<span class="" style="font-size: inherit;line-height: inherit;color: rgb(227, 206, 171);word-wrap: inherit !important;word-break: inherit !important;">int</span> rs = runStateOf(c);<br> &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;<span class="" style="font-size: inherit;line-height: inherit;color: rgb(140, 208, 211);word-wrap: inherit !important;word-break: inherit !important;">1</span>.线程池已经shutdown，或者提交进来task为ull且队列也是空，返回<span class="" style="font-size: inherit;color: inherit;line-height: inherit;word-wrap: inherit !important;word-break: inherit !important;"><span class="" style="font-size: inherit;line-height: inherit;color: rgb(227, 206, 171);word-wrap: inherit !important;word-break: inherit !important;">false</span><br> &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;<span class="" style="font-size: inherit;line-height: inherit;color: rgb(239, 239, 143);word-wrap: inherit !important;word-break: inherit !important;">if</span> <span class="" style="font-size: inherit;color: inherit;line-height: inherit;word-wrap: inherit !important;word-break: inherit !important;">(rs &gt;= SHUTDOWN &amp;&amp;<br> &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;! (rs == SHUTDOWN &amp;&amp;<br> &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; firstTask == <span class="" style="font-size: inherit;line-height: inherit;color: rgb(227, 206, 171);word-wrap: inherit !important;word-break: inherit !important;">null</span> &amp;&amp;<br> &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ! workQueue.isEmpty()</span>))<br> &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;return <span class="" style="font-size: inherit;line-height: inherit;color: rgb(227, 206, 171);word-wrap: inherit !important;word-break: inherit !important;">false</span></span>;<br><br> &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;<span class="" style="font-size: inherit;line-height: inherit;color: rgb(227, 206, 171);word-wrap: inherit !important;word-break: inherit !important;">for</span> (;;) {<br> &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;<span class="" style="font-size: inherit;line-height: inherit;color: rgb(227, 206, 171);word-wrap: inherit !important;word-break: inherit !important;">int</span> wc = workerCountOf(c);<br> &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;<span class="" style="font-size: inherit;line-height: inherit;color: rgb(140, 208, 211);word-wrap: inherit !important;word-break: inherit !important;">2</span>.如果需要创建核心线程但是当前线程已经大于corePoolSize 返回<span class="" style="font-size: inherit;line-height: inherit;color: rgb(227, 206, 171);word-wrap: inherit !important;word-break: inherit !important;">false</span>，如果是非核心线程但是已经超出maximumPoolSize，返回<span class="" style="font-size: inherit;color: inherit;line-height: inherit;word-wrap: inherit !important;word-break: inherit !important;"><span class="" style="font-size: inherit;line-height: inherit;color: rgb(227, 206, 171);word-wrap: inherit !important;word-break: inherit !important;">false</span><br> &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;<span class="" style="font-size: inherit;line-height: inherit;color: rgb(239, 239, 143);word-wrap: inherit !important;word-break: inherit !important;">if</span> <span class="" style="font-size: inherit;color: inherit;line-height: inherit;word-wrap: inherit !important;word-break: inherit !important;">(wc &gt;= CAPACITY ||<br> &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;wc &gt;= (core ? corePoolSize : maximumPoolSize)</span>)<br> &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;return <span class="" style="font-size: inherit;line-height: inherit;color: rgb(227, 206, 171);word-wrap: inherit !important;word-break: inherit !important;">false</span></span>;<br> &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;<span class="" style="font-size: inherit;line-height: inherit;color: rgb(227, 206, 171);word-wrap: inherit !important;word-break: inherit !important;">if</span> (compareAndIncrementWorkerCount(c))<br> &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;<span class="" style="font-size: inherit;line-height: inherit;color: rgb(227, 206, 171);word-wrap: inherit !important;word-break: inherit !important;">break</span> retry;<br> &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;c = ctl.get(); &nbsp;<span class="" style="font-size: inherit;line-height: inherit;color: rgb(127, 159, 127);word-wrap: inherit !important;word-break: inherit !important;">// Re-read ctl</span><br> &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;<span class="" style="font-size: inherit;line-height: inherit;color: rgb(227, 206, 171);word-wrap: inherit !important;word-break: inherit !important;">if</span> (runStateOf(c) != rs)<br> &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;<span class="" style="font-size: inherit;line-height: inherit;color: rgb(227, 206, 171);word-wrap: inherit !important;word-break: inherit !important;">continue</span> retry;<br> &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;<span class="" style="font-size: inherit;line-height: inherit;color: rgb(127, 159, 127);word-wrap: inherit !important;word-break: inherit !important;">//省略代码。。。</span><br> &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;<span class="" style="font-size: inherit;line-height: inherit;color: rgb(227, 206, 171);word-wrap: inherit !important;word-break: inherit !important;">if</span> (rs &lt; SHUTDOWN ||<br> &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;(rs == SHUTDOWN &amp;&amp; firstTask == <span class="" style="font-size: inherit;line-height: inherit;color: rgb(227, 206, 171);word-wrap: inherit !important;word-break: inherit !important;">null</span>)) {<br> &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;<span class="" style="font-size: inherit;line-height: inherit;color: rgb(227, 206, 171);word-wrap: inherit !important;word-break: inherit !important;">if</span> (t.isAlive())<br> &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;<span class="" style="font-size: inherit;line-height: inherit;color: rgb(227, 206, 171);word-wrap: inherit !important;word-break: inherit !important;">throw</span> <span class="" style="font-size: inherit;line-height: inherit;color: rgb(227, 206, 171);word-wrap: inherit !important;word-break: inherit !important;">new</span> IllegalThreadStateException();<br> &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;<span class="" style="font-size: inherit;line-height: inherit;color: rgb(127, 159, 127);word-wrap: inherit !important;word-break: inherit !important;">//省略代码。。。</span><br> &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;}<br> &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;}<br> &nbsp; &nbsp; &nbsp; &nbsp;}<br> &nbsp;<span class="" style="font-size: inherit;line-height: inherit;color: rgb(127, 159, 127);word-wrap: inherit !important;word-break: inherit !important;">//省略代码。。。</span><br> &nbsp; &nbsp; &nbsp;}<br></code></pre>
                               
                               addWorker() 有以下情况会返回 false ：
                               
                               1、线程池已经 shutdown，或者提交进来 task 为ull且同时任务队列也是空，返回 false。
                               
                               2、如果需要创建核心线程但是当前线程已经大于 corePoolSize 返回 false，如果是非核心线程但是已经超出 maximumPoolSize ，返回 false。
                               
                               3、创建线程后，检查是否已经启动。
                               
                               我们逐条检查。第一点只有线程池被 shutDown() 才会出现。第二点由于 CacheThreadPool 的 corePoolSize 是 0 ， maximumPoolSize  是 Intger.MAX_VALUE ，所以也不会出现。第三点是保护性错误，我猜因为线程允许通过外部的 ThreadFactory 创建，所以检查了一下是否外部已经 start，如果开发者编码规范，一般这种情况也不会出现。
                               
                               综上，在线程池没有 shutDown 的情况下，addWorker() 不会返回 false ，不会走reject流程，所以理论上 CacheThreadPool 可以一直提交任务，符合CacheThreadPool注释里的描述。
                ### 引申
                
                Executors 还提供了这么一个方法 Executors.newFixedThreadPool(4) 来创建一个有固定线程数量的线程池，我们看看创建的参数：
                
                <pre style="font-size: inherit;color: inherit;line-height: inherit;margin-top: 0px;margin-bottom: 0px;padding: 0px;"><code class="" style="margin-right: 2px;margin-left: 2px;line-height: 15px;font-size: 11px;word-spacing: -3px;letter-spacing: 0px;font-family: Consolas, Inconsolata, Courier, monospace;border-radius: 0px;padding: 0.5em;background: rgb(63, 63, 63);color: rgb(220, 220, 220);display: block !important;word-wrap: normal !important;word-break: normal !important;overflow: auto !important;"><span class="" style="font-size: inherit;color: inherit;line-height: inherit;word-wrap: inherit !important;word-break: inherit !important;"><span class="" style="font-size: inherit;line-height: inherit;color: rgb(227, 206, 171);word-wrap: inherit !important;word-break: inherit !important;">public</span> <span class="" style="font-size: inherit;line-height: inherit;color: rgb(227, 206, 171);word-wrap: inherit !important;word-break: inherit !important;">static</span> ExecutorService <span class="" style="font-size: inherit;line-height: inherit;color: rgb(239, 239, 143);word-wrap: inherit !important;word-break: inherit !important;">newFixedThreadPool</span><span class="" style="font-size: inherit;color: inherit;line-height: inherit;word-wrap: inherit !important;word-break: inherit !important;">(<span class="" style="font-size: inherit;line-height: inherit;color: rgb(227, 206, 171);word-wrap: inherit !important;word-break: inherit !important;">int</span> nThreads)</span> </span>{<br> &nbsp; &nbsp; &nbsp; &nbsp;<span class="" style="font-size: inherit;line-height: inherit;color: rgb(227, 206, 171);word-wrap: inherit !important;word-break: inherit !important;">return</span> <span class="" style="font-size: inherit;line-height: inherit;color: rgb(227, 206, 171);word-wrap: inherit !important;word-break: inherit !important;">new</span> ThreadPoolExecutor(nThreads, nThreads,<br> &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;<span class="" style="font-size: inherit;line-height: inherit;color: rgb(140, 208, 211);word-wrap: inherit !important;word-break: inherit !important;">0L</span>, TimeUnit.MILLISECONDS,<br> &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;<span class="" style="font-size: inherit;line-height: inherit;color: rgb(227, 206, 171);word-wrap: inherit !important;word-break: inherit !important;">new</span> LinkedBlockingQueue&lt;Runnable&gt;());<br> &nbsp; &nbsp;}<br></code></pre>
                
                参数中核心线程和最大线程一样，线程保留时间 0 ，使用 LinkedBlockingQueue 作为任务队列，这样的线程池有什么样的特性呢？我们看看注释说明，大意是说这是一个有着固定线程数量且使用无界队列作为线程队列的线程池。如果有新的任务提交，但是没有线程可用，这个任务会一直等待直到有可用的线程。如果一个线程因为异常终止了，当线程不够用的时候会再创建一个出来。线程会一直保持，直到线程池 shutDown。
                
                和 CacheThreadPool 相比，FixedThreadPool 注释里描述的特性有几个不同的地方。
                
                - 1.因为 corePoolSize == maximumPoolSize ，所以FixedThreadPool只会创建核心线程。
                
                - 2.在 getTask() 方法，如果队列里没有任务可取，线程会一直阻塞在 LinkedBlockingQueue.take() ，线程不会被回收。
                
                - 3.由于线程不会被回收，会一直卡在阻塞，所以没有任务的情况下， FixedThreadPool 占用资源更多。
                
                FixedThreadPool 和 CacheThreadPool 也有相同点，都使用无界队列，意味着可用一直向线程池提交任务，不会触发 reject 策略。              
                
                ### 总结
                    
                好了,又到了总结的时候,相信各位认真看完的应该对链表的基本操作非常熟悉了.
                
                CacheThreadPool 的运行流程如下：
                
                - 1、提交任务进线程池。
                
                - 2、因为 corePoolSize 为0的关系，不创建核心线程。
                
                - 3、尝试将任务添加到 SynchronousQueue 队列。
                
                - 4、如果SynchronousQueue 入列成功，等待被当前运行的线程空闲后拉取执行。如果当前运行线程为0，调用addWorker( null , false )创建一个非核心线程出来，然后从 SynchronousQueue 拉取任务并在当前线程执行，实现线程的复用。
                
                - 5、如果 SynchronousQueue 已有任务在等待，入列失败。因为 maximumPoolSize 无上限的原因，创建新的非核心线程来执行任务。
                
                - 6、纵观整个流程，通过设置 ThreadPoolExecutor 的几个参数，并加上应用 SynchronousQueue 的特性，然后在 ThreadPoolExecutor 的运行框架下，构建出了一个可以线程复用的线程池。ThreadPoolExecutor 还有很强的扩展性，可以通过自定义参数来实现不同的线程池。这么牛X的代码，这辈子写是不可能写得出来了，争取能完全读懂吧。。
                            
                    
        
## Jvm虚拟机

   * JAVA中jvm的基本结构  
    
        * Java虚拟机是什么？   
        
           > 注意：这里我是要告诉你，一个java的application对应了一个java.exe/javaw.exe（java.exe和javaw.exe你可以把它看成java的虚拟机，一个有窗口界面一个没有）。你运行几个application就有几个java.exe/javaw.exe。或者更加具体的说，你运行了几个main函数就启动了几个java应用，同时也启动了几个java的虚拟机。
        
            什么是java虚拟机，什么是java的虚拟机实例？java的虚拟机相当于我们的一个java类，而java虚拟机实例，相当我们new一个java类，不过java虚拟机不是通过new这个关键字而是通过java.exe或者javaw.exe来启动一个虚拟机实例。
        
        * jvm的生命周期是什么？
        
            >  当main函数的for循环打印完的时候，程序居然没有退出，而等到整个new Thread()里的匿名类的run方法执行结束后，javaw.exe才退出。我们知道在c++的win32编程（CreatThread()），main函数执行完了，寄宿线程也跟着退出了，在c#中如果你用线程池（ThreadPool）的话，结论也是如此，线程都跟着宿主进程的结束而结束。但是在java中貌似和我们的认知有很大的出入，这是为什么呢？这是由于java的虚拟机种有两种线程，一种叫叫守护线程，一种叫非守护线程，main函数就是个非守护线程，虚拟机的gc就是一个守护线程。java的虚拟机中，只要有任何非守护线程还没有结束，java虚拟机的实例都不会退出，所以即使main函数这个非守护线程退出，但是由于在main函数中启动的匿名线程也是非守护线程，它还没有结束，所以jvm没办法退出(有没有想干坏事的感觉？？)。          
             
            java虚拟机的生命周期，当一个java应用main函数启动时虚拟机也同时被启动，而只有当在虚拟机实例中的所有非守护进程都结束时，java虚拟机实例才结束生命。    
             
        * java虚拟机的体系结构是什么？
        
            <img src="http://img.my.csdn.net/uploads/201212/13/1355396896_8783.jpg" />
            
            操作系统的内存基本结构：
            
            <div>
                <src="http://img.my.csdn.net/uploads/201212/14/1355455229_1817.jpg" />
            </div>
            
            操作系统中的jvm：
            
            <div>
                <src="http://img.my.csdn.net/uploads/201212/14/1355455356_5266.jpg" />
            </div>
            
            操作系统+jvm的内存简单布局：
            
            <div>
                <img src="http://img.my.csdn.net/uploads/201212/14/1355455967_5681.jpg"/>
            </div>
            
            jvm的内存结构居然和操作系统的结构惊人的一致
            
            <div>
                <img src="http://img.my.csdn.net/uploads/201212/14/1355456425_2189.jpg"/>
            </div>
            
            jvm的设计的模型其实就是操作系统的模型
            
            <div>
                <img src="http://img.my.csdn.net/uploads/201212/15/1355550019_9953.jpg" />
            </div>
            
            多了一个pc寄存器，我为什么要画出来，主要是要告诉你，所谓pc寄存器，无论是在虚拟机中还是在我们虚拟机所寄宿的操作系统中功能目的是一致的，计算机上的pc寄存器是计算机上的硬件，本来就是属于计算机，（这一点对于学过汇编的同学应该很容易理解，有很多的寄存器eax，esp之类的32位寄存器，jvm里的寄存器就相当于汇编里的esp寄存器），计算机用pc寄存器来存放“伪指令”或地址，而相对于虚拟机，pc寄存器它表现为一块内存(一个字长，虚拟机要求字长最小为32位)，虚拟机的pc寄存器的功能也是存放伪指令，更确切的说存放的是将要执行指令的地址，它甚至可以是操作系统指令的本地地址，当虚拟机正在执行的方法是一个本地方法的时候，jvm的pc寄存器存储的值是undefined，所以你现在应该很明确的知道，虚拟机的pc寄存器是用于存放下一条将要执行的指令的地址(字节码流)。
            
            在深入
            
            <div>
                <img src="http://img.my.csdn.net/uploads/201212/15/1355571501_9669.jpg" />
            </div>
            
            这个图是要告诉你，当一个classLoder启动的时候，classLoader的生存地点在jvm中的堆，然后它会去主机硬盘上将A.class装载到jvm的方法区，方法区中的这个字节文件会被虚拟机拿来new A字节码()，然后在堆内存生成了一个A字节码的对象，然后A字节码这个内存文件有两个引用一个指向A的class对象，一个指向加载自己的classLoader，如下图。
            
            <img src="http://img.my.csdn.net/uploads/201212/14/1355495666_4639.jpg" />
            
            那么方法区中的字节码内存块，除了记录一个class自己的class对象引用和一个加载自己的ClassLoader引用之外，还记录了什么信息呢？？我们还是看图，然后我会讲给你听，听过一遍之后一辈子都不会忘记。
            
            <img src="http://img.my.csdn.net/uploads/201212/15/1355531464_2120.jpg" />
            
            <div class="dp-highlighter bg_java"><div class="bar"><div class="tools"><b>[java]</b> <a href="#" class="ViewSource" title="view plain" onclick="dp.sh.Toolbar.Command('ViewSource',this);return false;">view plain</a><span data-mod="popu_168"> <a href="#" class="CopyToClipboard" title="copy" onclick="dp.sh.Toolbar.Command('CopyToClipboard',this);return false;">copy</a><div style="position: absolute; left: 498px; top: 8571px; width: 16px; height: 16px; z-index: 99;"><embed id="ZeroClipboardMovie_4" src="https://csdnimg.cn/public/highlighter/ZeroClipboard.swf" loop="false" menu="false" quality="best" bgcolor="#ffffff" width="16" height="16" name="ZeroClipboardMovie_4" align="middle" allowscriptaccess="always" allowfullscreen="false" type="application/x-shockwave-flash" pluginspage="http://www.macromedia.com/go/getflashplayer" flashvars="id=4&amp;width=16&amp;height=16" wmode="transparent"></div><div style="position: absolute; left: 498px; top: 8571px; width: 16px; height: 16px; z-index: 99;"><embed id="ZeroClipboardMovie_8" src="https://csdnimg.cn/public/highlighter/ZeroClipboard.swf" loop="false" menu="false" quality="best" bgcolor="#ffffff" width="16" height="16" name="ZeroClipboardMovie_8" align="middle" allowscriptaccess="always" allowfullscreen="false" type="application/x-shockwave-flash" pluginspage="http://www.macromedia.com/go/getflashplayer" flashvars="id=8&amp;width=16&amp;height=16" wmode="transparent"></div></span><span data-mod="popu_169"> <a href="#" class="PrintSource" title="print" onclick="dp.sh.Toolbar.Command('PrintSource',this);return false;">print</a></span><a href="#" class="About" title="?" onclick="dp.sh.Toolbar.Command('About',this);return false;">?</a></div></div><ol start="1" class="dp-j"><li class="alt"><span><span class="keyword">package</span><span>&nbsp;test;</span><span class="keyword">import</span><span>&nbsp;java.io.Serializable;</span><span class="keyword">public</span><span>&nbsp;</span><span class="keyword">final</span><span>&nbsp;</span><span class="keyword">class</span><span>&nbsp;ClassStruct&nbsp;</span><span class="keyword">extends</span><span>&nbsp;Object&nbsp;</span><span class="keyword">implements</span><span>&nbsp;Serializable&nbsp;{</span><span class="comment">//1.类信息</span><span>&nbsp;&nbsp;</span></span></li><li class=""><span>&nbsp;<span class="comment">//2.对象字段信息</span><span>&nbsp;&nbsp;</span></span></li><li class="alt"><span>&nbsp;<span class="keyword">private</span><span>&nbsp;String&nbsp;name;&nbsp;&nbsp;</span></span></li><li class=""><span>&nbsp;<span class="keyword">private</span><span>&nbsp;</span><span class="keyword">int</span><span>&nbsp;id;&nbsp;&nbsp;</span></span></li><li class="alt"><span>&nbsp;&nbsp;&nbsp;</span></li><li class=""><span>&nbsp;<span class="comment">//4.常量池</span><span>&nbsp;&nbsp;</span></span></li><li class="alt"><span>&nbsp;<span class="keyword">public</span><span>&nbsp;</span><span class="keyword">final</span><span>&nbsp;</span><span class="keyword">int</span><span>&nbsp;CONST_INT=</span><span class="number">0</span><span>;&nbsp;&nbsp;</span></span></li><li class=""><span>&nbsp;&nbsp;&nbsp;&nbsp;<span class="keyword">public</span><span>&nbsp;</span><span class="keyword">final</span><span>&nbsp;String&nbsp;CONST_STR=</span><span class="string">"CONST_STR"</span><span>;&nbsp;&nbsp;</span></span></li><li class="alt"><span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span></li><li class=""><span>&nbsp;&nbsp;&nbsp;&nbsp;<span class="comment">//5.类变量区</span><span>&nbsp;&nbsp;</span></span></li><li class="alt"><span>&nbsp;&nbsp;&nbsp;&nbsp;<span class="keyword">public</span><span>&nbsp;</span><span class="keyword">static</span><span>&nbsp;String&nbsp;static_str=</span><span class="string">"static_str"</span><span>;&nbsp;&nbsp;</span></span></li><li class=""><span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span></li><li class="alt"><span>&nbsp;&nbsp;&nbsp;</span></li><li class=""><span>&nbsp;<span class="comment">//3.方法信息</span><span>&nbsp;&nbsp;</span></span></li><li class="alt"><span>&nbsp;<span class="keyword">public</span><span>&nbsp;</span><span class="keyword">static</span><span>&nbsp;</span><span class="keyword">final</span><span>&nbsp;String&nbsp;getStatic_str&nbsp;()</span><span class="keyword">throws</span><span>&nbsp;Exception{&nbsp;&nbsp;</span></span></li><li class=""><span>&nbsp;&nbsp;<span class="keyword">return</span><span>&nbsp;ClassStruct.static_str;&nbsp;&nbsp;</span></span></li><li class="alt"><span>&nbsp;}}&nbsp;&nbsp;</span></li></ol></div>
            
            所以各个信息段记录的信息可以从我们的类结构中得到，不需要你硬背，你认真的看过我下面的描述一遍估计就不可能会忘记了：
            
           1.类信息：修饰符(public final)
    
             是类还是接口(class,interface)

             类的全限定名(Test/ClassStruct.class)

             直接父类的全限定名(java/lang/Object.class)

             直接父接口的权限定名数组(java/io/Serializable)
    
          也就是 public final class ClassStruct extends Object implements Serializable这段描述的信息提取
    
           2.字段信息：修饰符(pirvate)

             字段类型(java/lang/String.class)

             字段名(name)
    
            也就是类似private String name;这段描述信息的提取
    
           3.方法信息:修饰符(public static final)
    
             方法返回值(java/lang/String.class)

             方法名(getStatic_str)

             参数需要用到的局部变量的大小还有操作数栈大小(操作数栈我们后面会讲)

             方法体的字节码(就是花括号里的内容)

             异常表(throws Exception)
    
           也就是对方法public static final String getStatic_str ()throws Exception的字节码的提取
           4.常量池:
    
            4.1.直接常量：

             1.1CONSTANT_INGETER_INFO整型直接常量池public final int CONST_INT=0;

             1.2CONSTANT_String_info字符串直接常量池   public final String CONST_STR="CONST_STR";

             1.3CONSTANT_DOUBLE_INFO浮点型直接常量池

             等等各种基本数据类型基础常量池(待会我们会反编译一个类，来查看它的常量池等。)

             4.2.方法名、方法描述符、类名、字段名，字段描述符的符号引用

            也就是所以编译器能够被确定，能够被快速查找的内容都存放在这里，它像数组一样通过索引访问，就是专门用来做查找的。

            编译时就能确定数值的常量类型都会复制它的所有常量到自己的常量池中，或者嵌入到它的字节码流中。作为常量池或者字节码流的一部分，编译时常量保存在方法区中，就和一般的类变量一样。但是当一般的类变量作为他们的类型的一部分数据而保存的时候，编译时常量作为使用它们的类型的一部分而保存
            
            也就是所以编译器能够被确定，能够被快速查找的内容都存放在这里，它像数组一样通过索引访问，就是专门用来做查找的。
            
             编译时就能确定数值的常量类型都会复制它的所有常量到自己的常量池中，或者嵌入到它的字节码流中。作为常量池或者字节码流的一部分，编译时常量保存在方法区中，就和一般的类变量一样。但是当一般的类变量作为他们的类型的一部分数据而保存的时候，编译时常量作为使用它们的类型的一部分而保存
            
             5.类变量：
        
             就是静态字段( public static String static_str="static_str";)

             虚拟机在使用某个类之前，必须在方法区为这些类变量分配空间。
        
             6.一个到classLoader的引用，通过this.getClass().getClassLoader()来取得为什么要先经过class呢？思考一下，然后看第七点的解释，再回来思考
        
             7.一个到class对象的引用，这个对象存储了所有这个字节码内存块的相关信息。所以你能够看到的区域，比如：类信息，你可以通过this.getClass().getName()取得
        
             所有的方法信息，可以通过this.getClass().getDeclaredMethods()，字段信息可以通过this.getClass().getDeclaredFields()，等等，所以在字节码中你想得到的，调用的，通过class这个引用基本都能够帮你完成。因为他就是字节码在内存块在堆中的一个对象
        
             8.方法表，如果学习c++的人应该都知道c++的对象内存模型有一个叫虚表的东西，java本来的名字就叫c++- -，它的方法表其实说白了就是c++的虚表，它的内容就是这个类的所有实例可能被调用的所有实例方法的直接引用。也是为了动态绑定的快速定位而做的一个类似缓存的查找表，它以数组的形式存在于内存中。不过这个表不是必须存在的，取决于虚拟机的设计者，以及运行虚拟机的机器是否有足够的内存
             
             > 总结： 首先，当一个程序启动之前，它的class会被类装载器装入方法区(不好听，其实这个区我喜欢叫做Permanent区)，执行引擎读取方法区的字节码自适应解析，边解析就边运行（其中一种方式），然后pc寄存器指向了main函数所在位置，虚拟机开始为main函数在java栈中预留一个栈帧（每个方法都对应一个栈帧），然后开始跑main函数，main函数里的代码被执行引擎映射成本地操作系统里相应的实现，然后调用本地方法接口，本地方法运行的时候，操纵系统会为本地方法分配本地方法栈，用来储存一些临时变量，然后运行本地方法，调用操作系统APIi等等。          
             
        [参考：java之jvm学习笔记十三(jvm基本结构)](https://blog.csdn.net/yfqnihao/article/details/8289363)
   
#jvm讲解第二篇
   
   [参考：一篇简单易懂的原理文章，让你把JVM玩弄与手掌之中](https://www.jianshu.com/p/63fe09fe1a60)
   
   * 讲解思路：
   
        - 一、JVM的原理
            
            - 1.1、jvm组成和运行原理：
            
                - 1.1.1、jvm的组成
                    
                    - 1.1.1.1、JVM在JDK中的位置。
                    
                    - 1.1.1.2、JVM的组成
                    
                - 1.1.2、jvm运行原理简介
                    
        - 二、JVM的内存管理和垃圾回收
            
            - 2.1、栈的管理
            
            - 2.2、堆的管理
            
            - 2.3、垃圾回收
            
        - 三、JVM的数据格式规范和Class文件
           
           - 3.1、数据类型规范
           
           - 3.1、字节码文件
           
           - 3.1、jvm指令集
           
           - 3.1、数据类型规范
        
        - 四、一个java类的实例分析
        
        - 五、关于jvm优化
            
            - 5.1、gc策略
            
            - 5.2、内存申请过程
            
            - 5.3、性能考虑
            
            - 5.4、经验总结

   ## jvm原理
   
   - 一、jvm组成和运行原理：
                
        - 1.1.1、jvm的组成
            
            - 1.1.1.1、JVM在JDK中的位置。
                
               JDK是java开发的必备工具箱，JDK其中有一部分是JRE，JRE是JAVA运行环境，JVM则是JRE最核心的部分。
               
                <div>
                    <img src="https://upload-images.jianshu.io/upload_images/9727275-87684dd3e1276ae0?imageMogr2/auto-orient/strip%7CimageView2/2/w/690" />
                </div>
                
               OOM等异常的处理最终都得从JVM这儿来解决。HotSpot是Oracle关于JVM的商标，区别于IBM，HP等厂商开发的JVM。Java HotSpot Client VM和Java HotSpot Server VM是JDK关于JVM的两种不同的实现，前者可以减少启动时间和内存占用，而后者则提供更加优秀的程序运行速度。
            
            - 1.1.1.2、JVM的组成    
            
                参考上一篇：内容少一些，理解容易一点
            
        - 1.1.2、jvm运行原理简介
            
            - 1.1.2.1、 Java 程序被javac工具编译为.class字节码文件之后，我们执行java命令，该class文件便被JVM的ClassLoader加载，可以看出JVM的启动是通过JAVA Path下的java.exe或者java进行的。
             
            - 1.1.2.2、 JVM的初始化、运行到结束大概包括这么几步：
            
                调用操作系统API判断系统的CPU架构，根据对应CPU类型寻找位于JRE目录下的/lib/jvm.cfg文件，然后通过该配置文件找到对应的jvm.dll文件（如果我们参数中有-server或者-client， 则加载对应参数所指定的jvm.dll，启动指定类型的JVM），初始化jvm.dll并且挂接到JNIENV结构的实例上，之后就可以通过JNIENV实例装载并且处理class文件了。class文件是字节码文件，它按照JVM的规范，定义了变量，方法等的详细信息，JVM管理并且分配对应的内存来执行程序，同时管理垃圾回收。直到程序结束，一种情况是JVM的所有非守护线程停止，一种情况是程序调用System.exit()，JVM的生命周期也结束。
    
   - 二、VM的内存管理和垃圾回收           
    
        > JVM中的内存管理主要是指JVM对于Heap的管理，这是因为Stack，PCRegister和Native Method Stack都是和线程一样的生命周期，在线程结束时自然可以被再次使用。虽然说，Stack的管理不是重点，但是也不是完全不讲究的。
        
       - 2.1、栈的管理
       
         >  JVM允许栈的大小是固定的或者是动态变化的。在Oracle的关于参数设置的官方文档中有关于Stack的设置，是通过-Xss来设置其大小。关于Stack的默认大小对于不同机器有不同的大小，并且不同厂商或者版本号的jvm的实现其大小也不同，如下表是HotSpot的默认大小：
                 
            <div>
               <img src="https://upload-images.jianshu.io/upload_images/9727275-37e54d95032bfade.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/700" />
            </div>
             
           - 2.1.1、
                
               我们一般通过减少常量，参数的个数来减少栈的增长，在程序设计时，我们把一些常量定义到一个对象中，然后来引用他们可以体现这一点。另外，少用递归调用也可以减少栈的占用因为栈帧中会存储父栈帧，递归会导致父栈帧也在存或状态，所以如果递归调用过深就会导致栈内存被大量占用，甚至出现StackOverFlow。栈是不需要垃圾回收的，尽管说垃圾回收是java内存管理的一个很热的话题，栈中的对象如果用垃圾回收的观点来看，他永远是live状态，是可以reachable的，所以也不需要回收，他占有的空间随着Thread的结束而释放。
               
               关于栈一般会发生以下两种异常：
               
                - 1.当线程中的计算所需要的栈超过所允许大小时，会抛出StackOverflowError。
               
                - 2.当Java栈试图扩展时，没有足够的存储器来实现扩展，JVM会报OutOfMemoryError。 
               
               另外栈上有一点得注意的是，对于本地代码调用，可能会在栈中申请内存，比如C调用malloc()，而这种情况下，GC是管不着的，需要我们在程序中，手动管理栈内存，使用free()方法释放内存。
                   
       - 2.2、堆的管理
       
            <div>
                <img src="https://upload-images.jianshu.io/upload_images/9727275-e9e1e522f549e6e9?imageMogr2/auto-orient/strip%7CimageView2/2/w/548" />
            </div>
            
            上图是 Heap和PermanentSapce的组合图，其中 Eden区里面存着是新生的对象，From Space和To Space中存放着是每次垃圾回收后存活下来的对象，所以每次垃圾回收后，Eden区会被清空。 存活下来的对象先是放到From Space，当From Space满了之后移动到To Space。当To Space满了之后移动到Old Space。Survivor的两个区是对称的，没先后关系，所以同一个区中可能同时存在从Eden复制过来 对象，和从前一个Survivor复制过来的对象，而复制到年老区的只有从第一个Survivor复制过来的对象。而且，Survivor区总有一个是空的。同时，根据程序需要，jvm提供对Survivor区复制次数的配置（-XX:MaxTenuringThreshold参数），即经过多少次复制后仍然存活的对象会被放到老年区，通过增多两个Survivor区复制的次数可以增加对象在年轻代中的存在时间，减少被放到年老代的可能。
            
            Old Space中则存放生命周期比较长的对象，而且有些比较大的新生对象也放在Old Space中，通过-XX:PretenureSizeThreshold设置，超过此大小的新生对象会直接放入老年区。
            
            堆的大小通过-Xms和-Xmx来指定最小值和最大值，通过-Xmn来指定Young Generation的大小（一些老版本也用-XX:NewSize指定）， 即上图中的Eden加FromSpace和ToSpace的总大小。然后通过-XX:NewRatio来指定Eden区的大小，在Xms和Xmx相等的情况下，该参数不需要设置。通过-XX：SurvivorRatio来设置Eden和一个Survivor区的比值。
            
            堆异常分为两种，一种是Out ofMemory(OOM)，一种是Memory Leak(ML)。MemoryLeak最终将导致OOM。实际应用中表现为：从Console看，内存监控曲线一直在顶部，程序响应慢，从线程看，大部分的线程在进行GC，占用比较多的CPU，最终程序异常终止，报OOM。OOM发生的时间不定，有短的一个小时，有长的10天一个月的。关于异常的处理，确定OOM/ML异常后，一定要注意保护现场，可以dump heap，如果没有现场则开启GCFlag收集垃圾回收日志，然后进行分析，确定问题所在。如果问题不是ML的话，一般通过增加Heap，增加物理内存来解决问题，是的话，就修改程序逻辑。
            
            在此我向大家推荐一个架构学习交流群。交流学习群号：575745314 里面会分享一些资深架构师录制的视频录像：有Spring，MyBatis，Netty源码分析，高并发、高性能、分布式、微服务架构的原理，JVM性能优化、分布式架构等这些成为架构师必备的知识体系。还能领取免费的学习资源，目前受益良多
            
       - 2.3、垃圾回收
        
            - 2.3.1、触发条件：
                
               对象没有被引用，
               
               作用域发生未捕捉异常，
               
               程序正常执行完毕，
               
               程序执行了System.exit()，
               
               程序发生意外终止。
                            
            - 2.3.2、JVM中标记垃圾使用的是一种根搜索算法
                
                > 简单的说，就是从一个叫GC Roots的对象开始，向下搜索，如果一个对象不能达到GC Roots对象的时候，说明它可以被回收了。这种算法比一种叫做引用计数法的垃圾标记算法要好，因为它避免了当两个对象啊互相引用时无法被回收的现象。
                            
            - 2.3.3、JVM中对于被标记为垃圾的对象进行回收时又分为了一下3种算法：
                
                - 2.3.3.1、标记清除算法，该算法是从根集合扫描整个空间，标记存活的对象，然后在扫描整个空间对没有被标记的对象进行回收，这种算法在存活对象较多时比较高效，但会产生内存碎片。
                
                - 2.3.3.2、复制算法，该算法是从根集合扫描，并将存活的对象复制到新的空间，这种算法在存活对象少时比较高效。
                
                - 2.3.3.3、标记整理算法，标记整理算法和标记清除算法一样都会扫描并标记存活对象，在回收未标记对象的同时会整理被标记的对象，解决了内存碎片的问题。
            
            - 2.3.4、JVM中，不同的 内存区域作用和性质不一样，使用的垃圾回收算法也不一样，所以JVM中又定义了几种不同的垃圾回收器（图中连线代表两个回收器可以同时使用）：
            
                <div>
                    <img src="https://upload-images.jianshu.io/upload_images/9727275-9600e675187f8f34?imageMogr2/auto-orient/strip%7CimageView2/2/w/547" />
                </div>
            
                - 1.Serial GC。从名字上看，串行GC意味着是一种单线程的，所以它要求收集的时候所有的线程暂停。这对于高性能的应用是不合理的，所以串行GC一般用于Client模式的JVM中。
                
                - 2.ParNew GC。是在SerialGC的基础上，增加了多线程机制。但是如果机器是单CPU的，这种收集器是比SerialGC效率低的。
                
                - 3.Parrallel ScavengeGC。这种收集器又叫吞吐量优先收集器，而吞吐量=程序运行时间/(JVM执行回收的时间+程序运行时间),假设程序运行了100分钟，JVM的垃圾回收占用1分钟，那么吞吐量就是99%。ParallelScavenge GC由于可以提供比较不错的吞吐量，所以被作为了server模式JVM的默认配置。
                
                - 4.ParallelOld是老生代并行收集器的一种，使用了标记整理算法，是JDK1.6中引进的，在之前老生代只能使用串行回收收集器。
                
                - 5.Serial Old是老生代client模式下的默认收集器，单线程执行，同时也作为CMS收集器失败后的备用收集器。
                
                - 6.CMS又称响应时间优先回收器，使用标记清除算法。他的回收线程数为(CPU核心数+3)/4，所以当CPU核心数为2时比较高效些。CMS分为4个过程：初始标记、并发标记、重新标记、并发清除。
                
                - 7.GarbageFirst（G1）。比较特殊的是G1回收器既可以回收Young Generation，也可以回收Tenured Generation。它是在JDK6的某个版本中才引入的，性能比较高，同时注意了吞吐量和响应时间。
                
                对于垃圾收集器的组合使用可以通过下表中的参数指定：
                    
                 > 默认的GC种类可以通过jvm.cfg或者通过jmap dump出heap来查看，一般我们通过jstat -gcutil [pid] 1000可以查看每秒gc的大体情况，或者可以在启动参数中加入：-verbose:gc-XX:+PrintGCTimeStamps -XX:+PrintGCDetails -Xloggc:./gc.log来记录GC日志。
                 
                GC中有一种情况叫做Full GC，以下几种情况会触发Full GC：
                
                 - 1.Tenured Space空间不足以创建打的对象或者数组，会执行FullGC，并且当FullGC之后空间如果还不够，那么会OOM:java heap space。
                    
                 - 2.Permanet Generation的大小不足，存放了太多的类信息，在非CMS情况下回触发FullGC。如果之后空间还不够，会OOM:PermGen space。
                    
                 - 3.CMS GC时出现promotion failed和concurrent mode failure时，也会触发FullGC。promotion failed是在进行Minor GC时，survivor space放不下、对象只能放入旧生代，而此时旧生代也放不下造成的；concurrentmode failure是在执行CMS GC的过程中同时有对象要放入旧生代，而此时旧生代空间不足造成的，因为CMS是并发执行的，执行GC的过程中可能也会有对象被放入旧生代。
                    
                 - 4.判断MinorGC后，要晋升到TenuredSpace的对象大小大于TenuredSpace的大小，也会触发FullGC。
                    
                   可以看出，当FullGC频繁发生时，一定是内存出问题了。
                    
   - 三、JVM的数据格式规范和Class文件
   
      - 3.1、数据类型规范
      
        > 依据冯诺依曼的计算机理论，计算机最后处理的都是二进制的数，而JVM是怎么把java文件最后转化成了各个平台都可以识别的二进制呢？JVM自己定义了一个抽象的存储数据单位，叫做Word。一个字足够大以持有byte、char、short、int、float、reference或者returnAdress的一个值，两个字则足够持有更大的类型long、double。它通常是主机平台一个指针的大小，如32位的平台上，字是32位。
        
        整形：
            
        <div>
            <img src="https://upload-images.jianshu.io/upload_images/9727275-a2a0ba3ced2b4a01.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/700" />
        </div>
        
        returnAddress类型的值是Java虚拟机指令的操作码的指针。
        
        对比java的基本数据类型，jvm的规范中没有boolean类型。这是因为jvm中堆boolean的操作是通过int类型来进行处理的，而boolean数组则是通过byte数组来进行处理。
        
        至于String，我们知道它存储在常量池中，但他不是基本数据类型，之所以可以存在常量池中，是因为这是JVM的一种规定。如果查看String源码，我们就会发现，String其实就是一个基于基本数据类型char的数组。
        
      - 3.2、字节码文件
      
          通过字节码文件的格式我们可以看出jvm是如何规范数据类型的。下面是ClassFile的结构：
          
          其中u1、u2、u4分别代表1、2、4个字节无符号数。
          
             magic：
          
          魔数，魔数的唯一作用是确定这个文件是否为一个能被虚拟机所接受的Class文件。魔数值固定为0xCAFEBABE，不会改变。
          
          minor_version、major_version：
          
          分别为Class文件的副版本和主版本。它们共同构成了Class文件的格式版本号。不同版本的虚拟机实现支持的Class文件版本号也相应不同，高版本号的虚拟机可以支持低版本的Class文件，反之则不成立。
          
          constant_pool_count：
          
          常量池计数器，constant_pool_count的值等于constant_pool表中的成员数加1。
          
          constant_pool[]：
          
          常量池，constant_pool是一种表结构，它包含Class文件结构及其子结构中引用的所有字符串常量、类或接口名、字段名和其它常量。常量池不同于其他，索引从1开始到constant_pool_count -1。
          
          access_flags：
          
          访问标志，access_flags是一种掩码标志，用于表示某个类或者接口的访问权限及基础属性。access_flags的取值范围和相应含义见下表：
          
          <div>
              <img src="https://upload-images.jianshu.io/upload_images/9727275-f9247a3225a54bd2?imageMogr2/auto-orient/strip%7CimageView2/2/w/552" />
          </div>
          
          this_class：
          
          类索引，this_class的值必须是对constant_pool表中项目的一个有效索引值。constant_pool表在这个索引处的项必须为CONSTANT_Class_info类型常量，表示这个Class文件所定义的类或接口。
          
          super_class：
          
          父类索引，对于类来说，super_class的值必须为0或者是对constant_pool表中项目的一个有效索引值。如果它的值不为0，那constant_pool表在这个索引处的项必须为CONSTANT_Class_info类型常量，表示这个Class文件所定义的类的直接父类。当然，如果某个类super_class的值是0，那么它必定是java.lang.Object类，因为只有它是没有父类的。
          
          interfaces_count：
          
          接口计数器，interfaces_count的值表示当前类或接口的直接父接口数量。
          
          interfaces[]：
          
          接口表，interfaces[]数组中的每个成员的值必须是一个对constant_pool表中项目的一个有效索引值，它的长度为interfaces_count。每个成员interfaces[i] 必须为CONSTANT_Class_info类型常量。
          
          fields_count：
          
          字段计数器，fields_count的值表示当前Class文件fields[]数组的成员个数。
          
          fields[]：
          
          字段表，fields[]数组中的每个成员都必须是一个fields_info结构的数据项，用于表示当前类或接口中某个字段的完整描述。
          
          methods_count：
          
          方法计数器，methods_count的值表示当前Class文件methods[]数组的成员个数。
          
          methods[]：
          
          方法表，methods[]数组中的每个成员都必须是一个method_info结构的数据项，用于表示当前类或接口中某个方法的完整描述。
          
          attributes_count：
          
          属性计数器，attributes_count的值表示当前Class文件attributes表的成员个数。
          
          attributes[]：
          
          属性表，attributes表的每个项的值必须是attribute_info结构。
          
      - 3.1、jvm指令集
      
          在Java虚拟机的指令集中，大多数的指令都包含了其操作所对应的数据类型信息。举个例子，iload指令用于从局部变量表中加载int型的数据到操作数栈中，而fload指令加载的则是float类型的数据。这两条指令的操作可能会是由同一段代码来实现的，但它们必须拥有各自独立的操作符。
          
          对于大部分为与数据类型相关的字节码指令，他们的操作码助记符中都有特殊的字符来表明专门为哪种数据类型服务：i代表对int类型的数据操作，l代表long，s代表short，b代表byte，c代表char，f代表float，d代表double，a代表reference。也有一些指令的助记符中没有明确的指明操作类型的字母，例如arraylength指令，它没有代表数据类型的特殊字符，但操作数永远只能是一个数组类型的对象。还有另外一些指令，例如无条件跳转指令goto则是与数据类型无关的。
          
          由于Java虚拟机的操作码长度只有一个字节，所以包含了数据类型的操作码对指令集的设计带来了很大的压力（只有256个指令）：如果每一种与数据类型相关的指令都支持Java虚拟机所有运行时数据类型的话，那恐怕就会超出一个字节所能表示的数量范围了。因此，Java虚拟机的指令集对于特定的操作只提供了有限的类型相关指令去支持它，换句话说，指令集将会故意被设计成非完全独立的（Not Orthogonal，即并非每种数据类型和每一种操作都有对应的指令）。有一些单独的指令可以在必要的时候用来将一些不支持的类型转换为可被支持的类型。
          
          通过查阅jvm指令集和其对应的数据类型的关系发现，大部分的指令都没有支持整数类型byte、char和short，甚至没有任何指令支持boolean类型。编译器会在编译期或运行期会将byte和short类型的数据带符号扩展（Sign-Extend）为相应的int类型数据，将boolean和char类型数据零位扩展（Zero-Extend）为相应的int类型数据。与之类似的，在处理boolean、byte、short和char类型的数组时，也会转换为使用对应的int类型的字节码指令来处理。因此，大多数对于boolean、byte、short和char类型数据的操作，实际上都是使用相应的对int类型作为运算类型（Computational Type）。
      
      - 四、一个java类的实例分析   
      
           <div>
               <img src="https://upload-images.jianshu.io/upload_images/9727275-4d5cf3422fde4e45.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/520" />
           </div>
           
           通过javap工具我们能看到这个简单的类的结构，如下：
           
           <div>
                <img src="https://upload-images.jianshu.io/upload_images/9727275-fbb691bccf995ee8?imageMogr2/auto-orient/strip%7CimageView2/2/w/669" />
           </div>
           
           我们可以看到一些信息包括主副版本号、常量池、ACC_FLAGS等，再来打开Class文件看一下：
            
           <div>
              <img src="https://upload-images.jianshu.io/upload_images/9727275-708a8281b6c54d3b?imageMogr2/auto-orient/strip%7CimageView2/2/w/700" />
           </div>
           
           根据前面所述的ClassFile结构，我们来分析下：
           
           <div>
                <img src="https://upload-images.jianshu.io/upload_images/9727275-537f4b1103df65ef?imageMogr2/auto-orient/strip%7CimageView2/2/w/487" />
           </div>
           
           可以看到前4个字节为魔数，也就是0xCAFEBABE，这里都是十六进制。
           
           <div>
                <img src="https://upload-images.jianshu.io/upload_images/9727275-638caebdeb6adcba?imageMogr2/auto-orient/strip%7CimageView2/2/w/489" />
           </div>
           
           魔数后2个字节为副版本号，这里副版本号是0.
           
           <div>
                <img src="https://upload-images.jianshu.io/upload_images/9727275-0f8d2f9063f0b099?imageMogr2/auto-orient/strip%7CimageView2/2/w/486" />
           </div>
           
           再后2个字节是主版本号0x0033，转为十进制，主版本号是51，和Javap工具所看到的一样，这里我用的JDK版本是1.7。
           
           <div>
                <img src="https://upload-images.jianshu.io/upload_images/9727275-8f1afd626543e111?imageMogr2/auto-orient/strip%7CimageView2/2/w/489" />
           </div>
           
           这两个字节是常量池计数器，常量池的数量为0x0017，转为十进制是23，也就是说常量池的索引为1~22，这与Javap所看到的也相符。
           
           常量池计数器后面就是常量池的内容，我们根据javap所看到的信息找到最后一个常量池项java/lang/Object，在字节码中找到对应的地方：
           
           <div>
              <img src="https://upload-images.jianshu.io/upload_images/9727275-49004ff977489b74?imageMogr2/auto-orient/strip%7CimageView2/2/w/632" />
           </div>
           
           常量池后面两个字节是访问标志access_flags：
           
           <div>
               <img src="https://upload-images.jianshu.io/upload_images/9727275-00552e34a6539a73?imageMogr2/auto-orient/strip%7CimageView2/2/w/489" />
           </div>
           
           值为0x0021，在javap中我们看到这个类的标志是
                
           <div>
               <img src="https://upload-images.jianshu.io/upload_images/9727275-86244d9fe9fc04c7?imageMogr2/auto-orient/strip%7CimageView2/2/w/250" />
           </div>
           
           其中ACC_PUBLIC的值为0x0001，ACC_SUPER的值为0x0020，与字节码是相匹配的。
           
           至于ClassFile的其他结构，包括this_class、super_class、接口计数器、接口等等都可以通过同样的方法进行分析，这里就不再多说了。
           
           在此我向大家推荐一个架构学习交流群。交流学习群号：575745314 里面会分享一些资深架构师录制的视频录像：有Spring，MyBatis，Netty源码分析，高并发、高性能、分布式、微服务架构的原理，JVM性能优化、分布式架构等这些成为架构师必备的知识体系。还能领取免费的学习资源，目前受益良多
   
   - 五、关于jvm优化
   
        > 不管是YGC还是Full GC,GC过程中都会对导致程序运行中中断,正确的选择不同的GC策略,调整JVM、GC的参数，可以极大的减少由于GC工作，而导致的程序运行中断方面的问题，进而适当的提高Java程序的工作效率。但是调整GC是以个极为复杂的过程，由于各个程序具备不同的特点，如：web和GUI程序就有很大区别（Web可以适当的停顿，但GUI停顿是客户无法接受的），而且由于跑在各个机器上的配置不同（主要cup个数，内存不同），所以使用的GC种类也会不同。
          
        - 5.1、gc策略
        
            现在比较常用的是分代收集（generational collection,也是SUN VM使用的,J2SE1.2之后引入），即将内存分为几个区域，将不同生命周期的对象放在不同区域里:younggeneration，tenured generation和permanet generation。绝大部分的objec被分配在young generation(生命周期短)，并且大部分的object在这里die。当younggeneration满了之后，将引发minor collection(YGC)。在minor collection后存活的object会被移动到tenured generation(生命周期比较长)。最后，tenured generation满之后触发major collection。major collection（Full gc）会触发整个heap的回收，包括回收young generation。permanet generation区域比较稳定，主要存放classloader信息。
            
             young generation有eden、2个survivor 区域组成。其中一个survivor区域一直是空的，是eden区域和另一个survivor区域在下一次copy collection后活着的objecy的目的地。object在survivo区域被复制直到转移到tenured区。
            
            我们要尽量减少 Full gc 的次数(tenuredgeneration一般比较大,收集的时间较长,频繁的Full gc会导致应用的性能收到严重的影响)。
            
            JVM(采用分代回收的策略)，用较高的频率对年轻的对象(young generation)进行YGC，而对老对象(tenuredgeneration)较少(tenuredgeneration 满了后才进行)进行Full GC。这样就不需要每次GC都将内存中所有对象都检查一遍。
            
            GC不会在主程序运行期对PermGen Space进行清理，所以如果你的应用中有很多CLASS(特别是动态生成类，当然permgen space存放的内容不仅限于类)的话,就很可能出现PermGen Space错误。
            
        - 5.2、内存申请过程
        
            - 1.JVM会试图为相关Java对象在Eden中初始化一块内存区域；
            
            - 2.当Eden空间足够时，内存申请结束。否则到下一步；
            
            - 3.JVM试图释放在Eden中所有不活跃的对象（minor collection），释放后若Eden空间4.仍然不足以放入新对象，则试图将部分Eden中活跃对象放入Survivor区；
            
            - 5.Survivor区被用来作为Eden及old的中间交换区域，当OLD区空间足够时，Survivor区的对象会被移到Old区，否则会被保留在Survivor区；
            
            - 6.当old区空间不够时，JVM会在old区进行major collection；
            
            - 7.完全垃圾收集后，若Survivor及old区仍然无法存放从Eden复制过来的部分对象，导致JVM无法在Eden区为新对象创建内存区域，则出现"Out of memory错误"；
            
        - 5.3、性能考虑
        
            对于GC的性能主要有2个方面的指标：吞吐量throughput（工作时间不算gc的时间占总的时间比）和暂停pause（gc发生时app对外显示的无法响应）。
            
            - 1.Total Heap
            
                      默认情况下，vm会增加/减少heap大小以维持free space在整个vm中占的比例，这个比例由MinHeapFreeRatio和MaxHeapFreeRatio指定。
                
                一般而言，server端的app会有以下规则：
                
                对vm分配尽可能多的memory；
                
                将Xms和Xmx设为一样的值。如果虚拟机启动时设置使用的内存比较小，这个时候又需要初始化很多对象，虚拟机就必须重复地增加内存。
                
                处理器核数增加，内存也跟着增大。
            
            - 2.The Young Generation
            
                  另外一个对于app流畅性运行影响的因素是younggeneration的大小。young generation越大，minor collection越少；但是在固定heap size情况下，更大的young generation就意味着小的tenured generation，就意味着更多的major collection(major collection会引发minorcollection)。
            
                  NewRatio反映的是young和tenuredgeneration的大小比例。NewSize和MaxNewSize反映的是young generation大小的下限和上限，将这两个值设为一样就固定了younggeneration的大小（同Xms和Xmx设为一样）。
            
                  如果希望，SurvivorRatio也可以优化survivor的大小，不过这对于性能的影响不是很大。SurvivorRatio是eden和survior大小比例。
            
            一般而言，server端的app会有以下规则：
            
            首先决定能分配给vm的最大的heap size，然后设定最佳的young generation的大小；
            
            如果heap size固定后，增加young generation的大小意味着减小tenured generation大小。让tenured generation在任何时候够大，能够容纳所有live的data（留10%-20%的空余）。
            
        - 5.4、经验总结        