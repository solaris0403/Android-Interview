1.activity的生命周期。
2.横竖屏切换时候activity的生命周期
  1.不设置Activity的android:configChanges时,切屏会重新调用各个生命周期,切横屏时会执行一次,切竖屏时会执行两次.
  2.设置Activity的android:configChanges="orientation"时,切屏还是会重新调用各个生命周期,切横、竖屏时只会执行一次.
  3.设置Activity的android:configChanges="orientation|keyboardHidden"时,切屏不会重新调用各个生命周期,只会执行onConfigurationChanged方法.
3.android中的动画有哪几类，它们的特点和区别是什么?
  两种，一种是Tween动画、还有一种是Frame动画。Tween动画，这种实现方式可以使视图组件移动、放大、缩小以及产生透明度的变化;另一种Frame动画，传统的动画方法，通过顺序的播放排列好的图片来实现，类似电影。
4.一条最长的短信息约占多少byte?
  中文70(包括标点)，英文160个字节。
5.handler机制的原理
    andriod提供了 Handler 和 Looper 来满足线程间的通信。Handler 先进先出原则。Looper类用来管理特定线程内对象之间的消息交换(Message Exchange)。
　　1)Looper: 一个线程可以产生一个Looper对象，由它来管理此线程里的Message Queue(消息队列)。
    2)Handler: 你可以构造Handler对象来与Looper沟通，以便push新消息到Message Queue里;或者接收Looper从Message Queue取出)所送来的消息。
　　3) Message Queue(消息队列):用来存放线程放入的消息。
　　4)线程：UI thread 通常就是main thread，而Android启动程序时会替它建立一个Message Queue。
6.什么是嵌入式实时操作系统, Android 操作系统属于实时操作系统吗?　  
  嵌入式实时操作系统是指当外界事件或数据产生时，能够接受并以足够快的速度予以处理，其处理的结果又能在规定的时间之内来控制生产过程或对处理系统作出快速响应，并控制所有实时任务协调一致运行的嵌入式操作系统。主要用于工业控制、 军事设备、 航空航天等领域对系统的响应时间有苛刻的要求，这就需要使用实时系统。又可分为软实时和硬实时两种，而android是基于linux内核的，因此属于软实时。
7.android中线程与线程，进程与进程之间如何通信
  1、一个 Android 程序开始运行时，会单独启动一个Process。
   默认情况下，所有这个程序中的Activity或者Service都会跑在这个Process。
   默认情况下，一个Android程序也只有一个Process，但一个Process下却可以有许多个Thread。
  2、一个 Android 程序开始运行时，就有一个主线程Main Thread被创建。该线程主要负责UI界面的显示、更新和控件交互，所以又叫UI Thread。
   一个Android程序创建之初，一个Process呈现的是单线程模型--即Main Thread，所有的任务都在一个线程中运行。所以，Main Thread所调用的每一个函数，其耗时应该越短越好。而对于比较费时的工作，应该设法交给子线程去做，以避免阻塞主线程（主线程被阻塞，会导致程序假死 现象）。
  3、Android单线程模型：Android UI操作并不是线程安全的并且这些操作必须在UI线程中执行。如果在子线程中直接修改UI，会导致异常。
8.Android dvm的进程和Linux的进程, 应用程序的进程是否为同一个概念
  DVM指dalivk的虚拟机。每一个Android应用程序都在它自己的进程中运行，都拥有一个独立的Dalvik虚拟机实例。而每一个DVM都是在Linux 中的一个进程，所以说可以认为是同一个概念。
9.sim卡的EF 文件有何作用
  sim卡的文件系统有自己规范，主要是为了和手机通讯，sim本 身可以有自己的操作系统，EF就是作存储并和手机通讯用的
10.android中的动画有哪几类，它们的特点和区别是什么?
  两种，一种是Tween动画、还有一种是Frame动画。Tween动画，这种实现方式可以使视图组件移动、放大、缩小以及产生透明度的变化;另一种Frame动画，传统的动画方法，通过顺序的播放排列好的图片来实现，类似电影。
11.让Activity变成一个窗口：Activity属性设定
  讲点轻松的吧,可能有人希望做出来的应用程序是一个漂浮在手机主界面的东西，那么很 简单你只需要设置 一下Activity的主题就可以了在AndroidManifest.xml 中定义 Activity的 地方一句话：
  Xml代码
  1.android :theme="@android:style/Theme.Dialog"
  　这就使你的应用程序变成对话框的形式弹出来了，或者
  Xml代码
  1.android:theme="@android:style/Theme.Translucent"
  就变成半透明的，[友情提示-.-]类似的这种activity的属性可以在android.R.styleable 类的AndroidManifestActivity 方法中看到，AndroidManifest.xml中所有元素的属性的介绍都可以参考这个类android.R.styleable
  上面说的是属性名称，具体有什么值是在android.R.style中 可以看到，比如这个"@android:style/Theme.Dialog" 就对应于android.R.style.Theme_Dialog ,('_'换成'.' < --注意：这个是文章内容不是笑脸)就可以用在描述文件 中了,找找类定义和描述文件中的对应关系就都明白了。
12.如何将SQLite数据库(dictionary.db文件)与apk文件一起发布?
  解答：可以将dictionary.db文件复制到Eclipse Android工程中的res aw目录中。所有在res aw目录中的文件不会被压缩，这样可以直接提取该目录中的文件。可以将dictionary.db文件复制到res aw目录中
13.如何将打开res aw目录中的数据库文件?
  解答：在Android中不能直接打开res aw目录中的数据库文件，而需要在程序第一次启动时将该文件复制到手机内存或SD卡的某个目录中，然后再打开该数据库文件。复制的基本方法是使用getResources().openRawResource方法获得res aw目录中资源的 InputStream对象，然后将该InputStream对象中的数据写入其他的目录中相应文件中。在Android SDK中可以使用SQLiteDatabase.openOrCreateDatabase方法来打开任意目录中的SQLite数据库文件。
14.在android中mvc的具体体现
  Android 的官方建议应用程序的开发采用MVC 模式。何谓MVC？先看看下图
  MVC 是Model,View,Controller 的缩写，从上图可以看出MVC 包含三个部分：
  .. 模型（Model）对象：是应用程序的主体部分，所有的业务逻辑都应该写在该
  层。
  .. 视图（View）对象：是应用程序中负责生成用户界面的部分。也是在整个
  MVC 架构中用户唯一可以看到的一层，接收用户的输入，显示处理结果。
  .. 控制器（Control）对象：是根据用户的输入，控制用户界面数据显示及更新
  Model 对象状态的部分，控制器更重要的一种导航功能，想用用户出发的相
  关事件，交给M 哦得了处理。
  Android 鼓励弱耦合和组件的重用，在Android 中MVC 的具体体现如下
  1)视图层（view）：一般采用xml文件进行界面的描述，使用的时候可以非常方便的引入，当然，如何你对android了解的比较的多了话，就一定可 以想到在android中也可以使用javascript+html等的方式作为view层，当然这里需要进行java和javascript之间的通 信，幸运的是，android提供了它们之间非常方便的通信实现。
  2)控制层（controller）：android的控制层的重 任通常落在了众多的acitvity的肩上，这句话也就暗含了不要在acitivity中写代码，要通过activity交割model业务逻辑层处理， 这样做的另外一个原因是android中的acitivity的响应时间是5s，如果耗时的操作放在这里，程序就很容易被回收掉。
  3)模型层（model）：对数据库的操作、对网络等的操作都应该在model里面处理，当然对业务计算等操作也是必须放在的该层的。
15.Android系统的架构
  android的系统架构和其操作系统一样，采用了分层的架构。从架构图看，android分为四个层，从高层到低层分别是应用程序层、应用程序框架层、系统运行库层和linux核心层。
  1.应用程序　Android会同一系列核心应用程序包一起发布，该应用程序包包括email客户端，SMS短消息程序，日历，地图，浏览器，联系人管理程序等。所有的应用程序都是使用JAVA语言编写的。
  2.应用程序框架　开发人员也可以完全访问核心应用程序所使用的API框架。该应用程序的架构设计简化了组件的重用;任何一个应用程序都可以发布它的功能块并且任何其它的应用程序都可以使用其所发布的功能块(不过得遵循框架的安全性限制)。同样，该应用程序重用机制也使用户可以方便的替换程序组件。
  隐藏在每个应用后面的是一系列的服务和系统, 其中包括;
  * 丰富而又可扩展的视图(Views)，可以用来构建应用程序， 它包括列表(lists)，网格(grids)，文本框(text boxes)，按钮(buttons)， 甚至可嵌入的web浏览器。
  * 内容提供器(Content Providers)使得应用程序可以访问另一个应用程序的数据(如联系人数据库)， 或者共享它们自己的数据
  * 资源管理器(Resource Manager)提供 非代码资源的访问，如本地字符串，图形，和布局文件( layout files )。
  * 通知管理器 (Notification Manager) 使得应用程序可以在状态栏中显示自定义的提示信息。
  * 活动管理器( Activity Manager) 用来管理应用程序生命周期并提供常用的导航回退功能。
  有关更多的细节和怎样从头写一个应用程序，请参考 如何编写一个 Android 应用程序.
  3.系统运行库
  1)程序库
  Android 包含一些C/C++库，这些库能被Android系统中不同的组件使用。它们通过 Android 应用程序框架为开发者提供服务。以下是一些核心库：
  * 系统 C 库 - 一个从 BSD 继承来的标准 C 系统函数库( libc )， 它是专门为基于 embedded linux 的设备定制的。
  * 媒体库 - 基于 PacketVideo OpenCORE;该库支持多种常用的音频、视频格式回放和录制，同时支持静态图像文件。编码格式包括MPEG4, H.264, MP3, AAC, AMR, JPG, PNG 。
  * Surface Manager - 对显示子系统的管理，并且为多个应用程序提 供了2D和3D图层的无缝融合。
  * LibWebCore - 一个最新的web浏览器引擎用，支持Android浏览器和一个可嵌入的web视图。
  * SGL - 底层的2D图形引擎
  * 3D libraries - 基于OpenGL ES 1.0 APIs实现;该库可以使用硬件 3D加速(如果可用)或者使用高度优化的3D软加速。
  * FreeType -位图(bitmap)和矢量(vector)字体显示。
  * SQLite - 一个对于所有应用程序可用，功能强劲的轻型关系型数据库引擎。
  2)Android 运行库
  　Android 包括了一个核心库，该核心库提供了JAVA编程语言核心库的大多数功能。
  　每一个Android应用程序都在它自己的进程中运行，都拥有一个独立的Dalvik虚拟机实例。Dalvik被设计成一个设备可以同时高效地运行多个虚拟系统。 Dalvik虚拟机执行(.dex)的Dalvik可执行文件，该格式文件针对小内存使用做了优化。同时虚拟机是基于寄存器的，所有的类都经由JAVA编译器编译，然后通过SDK中 的 “dx” 工具转化成.dex格式由虚拟机执行。
  　Dalvik虚拟机依赖于linux内核的一些功能，比如线程机制和底层内存管理机制。
  4.Linux 内核
  Android 的核心系统服务依赖于 Linux 2.6 内核，如安全性，内存管理，进程管理， 网络协议栈和驱动模型。 Linux 内核也同时作为硬件和软件栈之间的抽象层。
16.Android常用控件的信息
  单选框(RadioButton与RadioGroup)：
  RadioGroup用于对单选框进行分组，相同组内的单选框只有一个单选框被选中。
  事件：setOnCheckedChangeListener()，处理单选框被选择事件。把RadioGroup.OnCheckedChangeListener实例作为参数传入。
  多选框(CheckBox):
  每个多选框都是独立的，可以通过迭代所有的多选框，然后根据其状态是否被选中在获取其值。
  事件：setOnCheckChangeListener()处理多选框被选择事件。把CompoundButton.OnCheckedChangeListener实例作为参数传入
  下拉列表框(Spring)：
  Spinner.getItemAtPosition(Spinner.getSelectedItemPosition());获取下拉列表框的值。
  事件：setOnItemSelectedListener(),处理下拉列表框被选择事件把AdapterView.OnItemSelectedListener实例作为参数传入；
  拖动条(SeekBar)：
  SeekBar.getProgress()获取拖动条当前值
  事件:setOnSeekBarChangeListener()，处理拖动条值变化事件，把SeekBar.OnSeekBarChangeListener实例作为参数传入。
  菜单(Menu):
  重写Activity的onCreatOptionMenu(Menu menu)方法，该方法用于创建选项菜单，咋用户按下手机的"Menu"按钮时就会显示创建好的菜单，在onCreatOptionMenu(Menu Menu)方法内部可以调用Menu.add()方法实现菜单的添加。
  重写Activity的onMenuItemSelected()方法，该方法用于处理菜单被选择事件。
  进度对话框(ProgressDialog)：
  创建并显示一个进度对话框：ProgressDialog.show(ProgressDialogActivity.this,"请稍等"，"数据正在加载中...."，true)；
  设置对话框的风格：setProgressStyle()
  ProgressDialog.STYLE_SPINNER  旋转进度条风格(为默认风格)
  ProgressDialog.STYLE_HORIZONTAL 横向进度条风格
17.请介绍下Android中常用的五种布局
  Android布局是应用界面开发的重要一环，在Android中，共有五种布局方式，分别是：FrameLayout（框架布局），LinearLayout （线性布局），
  AbsoluteLayout（绝对布局），RelativeLayout（相对布局），TableLayout（表格布局）。
  1.FrameLayout   
      这个布局可以看成是墙脚堆东西，有一个四方的矩形的左上角墙脚，我们放了第一个东西，要再放一个，那就在放在原来放的位置的上面，这样依次的放，会盖住原来的东西。这个布局比较简单，也只能放一点比较简单的东西。   
  2.LinearLayout   
  线性布局，这个东西，从外框上可以理解为一个div，他首先是一个一个从上往下罗列在屏幕上。每一个LinearLayout里面又可分为垂直布局 （android:orientation="vertical"）和水平布局（android:orientation="horizontal" ）。当垂直布局时，每一行就只有一个元素，多个元素依次垂直往下；水平布局时，只有一行，每一个元素依次向右排列。   
  linearLayout中有一个重要的属性 android:layout_weight="1"，这个weight在垂直布局时，代表行距；水平的时候代表列宽；weight值越大就越大。   
  3.AbsoluteLayout   
      绝对布局犹如div指定了absolute属性，用X,Y坐标来指定元素的位置android:layout_x="20px" android:layout_y="12px" 这种布局方式也比较简单，但是在垂直随便切换时，往往会出问题，而且多个元素的时候，计算比较麻烦。   
  4.RelativeLayout   
      相对布局可以理解为某一个元素为参照物，来定位的布局方式。主要属性有：   
      相对于某一个元素   
      android:layout_below="@id/aaa" 该元素在 id为aaa的下面   
      android:layout_toLeftOf="@id/bbb" 改元素的左边是bbb   
       相对于父元素的地方   
       android:layout_alignParentLeft="true"  在父元素左对齐   
       android:layout_alignParentRight="true" 在父元素右对齐   
       还可以指定边距等，具体详见API   
  5.TableLayout   
       表格布局类似Html里面的Table。每一个TableLayout里面有表格行TableRow，TableRow里面可以具体定义每一个元素，设定他的对齐方式 android:gravity="" 。   
       每一个布局都有自己适合的方式，另外，这五个布局元素可以相互嵌套应用，做出美观的界面。
18.如何启用Service，如何停用Service
  Android中的服务和windows中的服务是类似的东西，服务一般没有用户操作界面，它运行于系统中不容易被用户发觉，可以使用它开发如监控之类的程序。服务的开发比较简单，如下：
  第一步：继承Service类
  public class SMSService extends Service {
  }
  第二步：在AndroidManifest.xml文件中的<application>节点里对服务进行配置:
  <service android:name=".SMSService" />
  服务不能自己运行，需要通过调用Context.startService()或Context.bindService()方法启动服务。这两个方法都可以启动Service，但是它们的使用场合有所不同。使用startService()方法启用服务，调用者与服务之间没有关连，即使调用者退出了，服务仍然运行。使用bindService()方法启用服务，调用者与服务绑定在了一起，调用者一旦退出，服务也就终止，大有“不求同时生，必须同时死”的特点。
  如果打算采用Context.startService()方法启动服务，在服务未被创建时，系统会先调用服务的onCreate()方法，接着调用onStart()方法。如果调用startService()方法前服务已经被创建，多次调用startService()方法并不会导致多次创建服务，但会导致多次调用onStart()方法。采用startService()方法启动的服务，只能调用Context.stopService()方法结束服务，服务结束时会调用onDestroy()方法。
  如果打算采用Context.bindService()方法启动服务，在服务未被创建时，系统会先调用服务的onCreate()方法，接着调用onBind()方法。这个时候调用者和服务绑定在一起，调用者退出了，系统就会先调用服务的onUnbind()方法，接着调用onDestroy()方法。如果调用bindService()方法前服务已经被绑定，多次调用bindService()方法并不会导致多次创建服务及绑定(也就是说onCreate()和onBind()方法并不会被多次调用)。如果调用者希望与正在绑定的服务解除绑定，可以调用unbindService()方法，调用该方法也会导致系统调用服务的onUnbind()-->onDestroy()方法。
  服务常用生命周期回调方法如下：
  onCreate() 该方法在服务被创建时调用，该方法只会被调用一次，无论调用多少次startService()或bindService()方法，服务也只被创建一次。
  onDestroy()该方法在服务被终止时调用。
  与采用Context.startService()方法启动服务有关的生命周期方法
  onStart() 只有采用Context.startService()方法启动服务时才会回调该方法。该方法在服务开始运行时被调用。多次调用startService()方法尽管不会多次创建服务，但onStart() 方法会被多次调用。
  与采用Context.bindService()方法启动服务有关的生命周期方法
  onBind()只有采用Context.bindService()方法启动服务时才会回调该方法。该方法在调用者与服务绑定时被调用，当调用者与服务已经绑定，多次调用Context.bindService()方法并不会导致该方法被多次调用。
  onUnbind()只有采用Context.bindService()方法启动服务时才会回调该方法。该方法在调用者与服务解除绑定时被调用
  采用Context. bindService()方法启动服务的代码如下：  
  public class HelloActivity extends Activity {  
       ServiceConnection conn = new ServiceConnection() {  
                public void onServiceConnected(ComponentName name, IBinder service) {  
             }  
             public void onServiceDisconnected(ComponentName name) {  
             }  
       };  
      @Override   
  public void onCreate(Bundle savedInstanceState) {   
          Button button =(Button) this.findViewById(R.id.button);  
          button.setOnClickListener(new View.OnClickListener(){  
                 public void onClick(View v) {  
                    Intent intent = new Intent(HelloActivity.this, SMSService.class);  
                    bindService(intent, conn, Context.BIND_AUTO_CREATE);  
                    //unbindService(conn);//解除绑定   
            }});         
      }  
  }  
  采用Context. bindService()方法启动服务的代码如下：  
  public class HelloActivity extends Activity {  
       ServiceConnection conn = new ServiceConnection() {  
                public void onServiceConnected(ComponentName name, IBinder service) {  
             }  
             public void onServiceDisconnected(ComponentName name) {  
             }  
       };  
      @Override   
  public void onCreate(Bundle savedInstanceState) {   
          Button button =(Button) this.findViewById(R.id.button);  
          button.setOnClickListener(new View.OnClickListener(){  
                 public void onClick(View v) {  
                    Intent intent = new Intent(HelloActivity.this, SMSService.class);  
                    bindService(intent, conn, Context.BIND_AUTO_CREATE);  
                    //unbindService(conn);//解除绑定   
            }});         
      }  
  }  
  采用Context. bindService()方法启动服务的代码如下：  
  public class HelloActivity extends Activity {  
       ServiceConnection conn = new ServiceConnection() {  
                public void onServiceConnected(ComponentName name, IBinder service) {  
             }  
             public void onServiceDisconnected(ComponentName name) {  
             }  
       };  
      @Override   
  public void onCreate(Bundle savedInstanceState) {   
          Button button =(Button) this.findViewById(R.id.button);  
          button.setOnClickListener(new View.OnClickListener(){  
                 public void onClick(View v) {  
                    Intent intent = new Intent(HelloActivity.this, SMSService.class);  
                    bindService(intent, conn, Context.BIND_AUTO_CREATE);  
                    //unbindService(conn);//解除绑定  
            }});         
      }  
  }  
19.ListView优化
  工作原理:
  ListView 针对List中每个item，要求 adapter “给我一个视图” (getView)。
  一个新的视图被返回并显示
  如果我们有上亿个项目要显示怎么办？为每个项目创建一个新视图？NO!这不可能！
  实际上Android为你缓存了视图。
  Android中有个叫做Recycler的构件，下图是他的工作原理：
  如果你有10亿个项目(item)，其中只有可见的项目存在内存中，其他的在Recycler中。
  1. ListView先请求一个type1视图(getView)然后请求其他可见的项目。convertView在getView中是空(null)的。
  2. 当item1滚出屏幕，并且一个新的项目从屏幕低端上来时，ListView再请求一个type1视图。convertView此时不是空值了，它的值是item1。你只需设定新的数据然后返回convertView，不必重新创建一个视图。
20.广播接收者生命周期
  一个广播接收者有一个回调方法：void onReceive(Context curContext, Intent broadcastMsg)。当一个广播消息到达接收者是，Android调用它的onReceive()方法并传递给它包含消息的Intent对象。广播接收者被认为仅当它执行这个方法时是活跃的。当onReceive()返回后，它是不活跃的。
  有一个活跃的广播接收者的进程是受保护的，不会被杀死。但是系统可以在任何时候杀死仅有不活跃组件的进程，当占用的内存别的进程需要时。
  这带来一个问题，当一个广播消息的响应时费时的，因此应该在独立的线程中做这些事，远离用户界面其它组件运行的主线程。如果onReceive()衍生线程然后返回，整个进程，包括新的线程，被判定为不活跃的（除非进程中的其它应用程序组件是活跃的），将使它处于被杀的危机。解决这个问题的方法是onReceive()启动一个服务，及时服务做这个工作，因此系统知道进程中有活跃的工作在做。
21.设计模式和IoC(控制反转)
  Android 框架魅力的源泉在于IoC，在开发Android 的过程中你会时刻感受到IoC 带来
  的巨大方便，就拿Activity 来说，下面的函数是框架调用自动调用的：
  protected void onCreate(Bundle savedInstanceState) ；
  不是程序编写者主动去调用，反而是用户写的代码被框架调用，这也就反转
  了！当然IoC 本身的内涵远远不止这些，但是从这个例子中也可以窥视出IoC
  带来的巨大好处。此类的例子在Android 随处可见，例如说数据库的管理类，
  例如说Android 中SAX 的Handler 的调用等。有时候，您甚至需要自己编写简
  单的IoC 实现，上面展示的多线程现在就是一个说明。
22.Android中的长度单位详解
  现在这里介绍一下dp 和sp。dp 也就是dip。这个和sp 基本类似。如果设置表示长度、高度等属性时可以使用dp 或sp。但如果设置字体，需要使用sp。dp 是与密度无关，sp 除了与密度无关外，还与scale 无关。如果屏幕密度为160，这时dp 和sp 和px 是一样的。1dp=1sp=1px，但如果使用px 作单位，如果屏幕大小不变（假设还是3.2 寸），而屏幕密度变成了320。那么原来TextView 的宽度设成160px，在密度为320 的3.2 寸屏幕里看要比在密度为160 的3.2 寸屏幕上看短了一半。但如果设置成160dp 或160sp 的话。系统会自动将width 属性值设置成320px 的。也就是160 * 320 / 160。其中320 / 160 可称为密
  度比例因子。也就是说，如果使用dp 和sp，系统会根据屏幕密度的变化自动
  进行转换。
  下面看一下其他单位的含义
  px：表示屏幕实际的象素。例如，320*480 的屏幕在横向有320个象素，
  在纵向有480 个象素。
  in：表示英寸，是屏幕的物理尺寸。每英寸等于2.54 厘米。例如，形容
  手机屏幕大小，经常说，3.2（英）寸、3.5（英）寸、4（英）寸就是指这个
  单位。这些尺寸是屏幕的对角线长度。如果手机的屏幕是3.2 英寸，表示手机
  的屏幕（可视区域）对角线长度是3.2*2.54 = 8.128 厘米。读者可以去量
  一量自己的手机屏幕，看和实际的尺寸是否一致。
23.4种activity的启动模式
  standard: 标准模式，一调用startActivity()方法就会产生一个新的实例。
  singleTop: 如果已经有一个实例位于Activity栈的顶部时，就不产生新的实例，而只是调用Activity中的newInstance()方法。如果不位于栈顶，会产生一个新的实例。
  singleTask: 会在一个新的task中产生这个实例，以后每次调用都会使用这个，不会去产生新的实例了。
  singleInstance: 这个跟singleTask基本上是一样，只有一个区别：在这个模式下的Activity实例所处的task中，只能有这个activity实例，不能有其他的实例。
24.什么是ANR 如何避免它?
  ANR：Application Not Responding，五秒
  在Android中，活动管理器和窗口管理器这两个系统服务负责监视应用程序的响应。当出现下列情况时，Android就会显示ANR对话框了：
  　　对输入事件(如按键、触摸屏事件)的响应超过5秒
  　　意向接受器(intentReceiver)超过10秒钟仍未执行完毕　Android应用程序完全运行在一个独立的线程中(例如main)。这就意味着，任何在主线程中运行的，需要消耗大量时间的操作都会引发ANR。因为此时，你的应用程序已经没有机会去响应输入事件和意向广播(Intent broadcast)。
  　　因此，任何运行在主线程中的方法，都要尽可能的只做少量的工作。特别是活动生命周期中的重要方法如onCreate()和 onResume()等更应如此。潜在的比较耗时的操作，如访问网络和数据库;或者是开销很大的计算，比如改变位图的大小，需要在一个单独的子线程中完成(或者是使用异步请求，如数据库操作)。但这并不意味着你的主线程需要进入阻塞状态已等待子线程结束 -- 也不需要调用Therad.wait()或者Thread.sleep()方法。取而代之的是，主线程为子线程提供一个句柄(Handler)，让子线程在即将结束的时候调用它(xing:可以参看Snake的例子，这种方法与以前我们所接触的有所不同)。使用这种方法涉及你的应用程序，能够保证你的程序对输入保持良好的响应，从而避免因为输入事件超过5秒钟不被处理而产生的ANR。这种实践需要应用到所有显示用户界面的线程，因为他们都面临着同样的超时问题。
25.Android Intent的使用
  在一个Android应用中，主要是由一些组件组成，（Activity,Service,ContentProvider,etc.)在这些组件之间的通讯中，由Intent协助完成。
  正如网上一些人解析所说，Intent负责对应用中一次操作的动作、动作涉及数据、附加数据进行描述，Android则根据此Intent的描述，负责找到对应的组件，将 Intent传递给调用的组件，并完成组件的调用。Intent在这里起着实现调用者与被调用者之间的解耦作用。
  Intent传递过程中，要找到目标消费者（另一个Activity,IntentReceiver或Service），也就是Intent的响应者，有两种方法来匹配：
  1，显示匹配（Explicit)：
    public TestB extents Activity  
    {  
    .........  
    };  
    public class Test extends Activity  
    {  
         ......  
         public void switchActivity()  
         {  
                Intent i = new Intent(Test.this, TestB.class);  
                this.startActivity(i);  
         }  
    }  
    public TestB extents Activity  
    {  
    .........  
    };  
    public class Test extends Activity  
    {  
         ......  
         public void switchActivity()  
         {  
                Intent i = new Intent(Test.this, TestB.class);  
                this.startActivity(i);  
         }  
    }  
    public TestB extents Activity  
    {  
    .........  
    };  
    public class Test extends Activity  
    {  
         ......  
         public void switchActivity()  
         {  
                Intent i = new Intent(Test.this, TestB.class);  
                this.startActivity(i);  
         }  
    }  
  代码简洁明了，执行了switchActivity()函数，就会马上跳转到名为TestB的Activity中。
  2，隐式匹配(Implicit):
  隐式匹配，首先要匹配Intent的几项值：Action, Category, Data/Type,Component
  如果填写了Componet就是上例中的Test.class)这就形成了显示匹配。所以此部分只讲前几种匹配。匹配规则为最大匹配规则，
  1，如果你填写了Action，如果有一个程序的Manifest.xml中的某一个Activity的IntentFilter段中定义了包含了相同的Action那么这个Intent就与这个目标Action匹配，如果这个Filter段中没有定义Type,Category，那么这个Activity就匹配了。但是如果手机中有两个以上的程序匹配，那么就会弹出一个对话可框来提示说明。
  Action的值在Android中有很多预定义，如果你想直接转到你自己定义的Intent接收者，你可以在接收者的IntentFilter中加入一个自定义的Action值（同时要设定Category值为"android.intent.category.DEFAULT"），在你的Intent中设定该值为Intent的Action,就直接能跳转到你自己的Intent接收者中。因为这个Action在系统中是唯一的。
  2,data/type，你可以用Uri来做为data,比如Uri uri = Uri.parse(http://www.google.com );
  Intent i = new Intent(Intent.ACTION_VIEW,uri);手机的Intent分发过程中，会根据http://www.google.com 的scheme判断出数据类型type
  手机的Brower则能匹配它，在Brower的Manifest.xml中的IntenFilter中首先有ACTION_VIEW Action,也能处理http:的type，
  3，至于分类Category，一般不要去在Intent中设置它，如果你写Intent的接收者，就在Manifest.xml的Activity的IntentFilter中包含android.category.DEFAULT,这样所有不设置Category（Intent.addCategory(String c);）的Intent都会与这个Category匹配。
  4,extras（附加信息），是其它所有附加信息的集合。使用extras可以为组件提供扩展信息，比如，如果要执行“发送电子邮件”这个动作，可以将电子邮件的标题、正文等保存在extras里，传给电子邮件发送组件。
26.如果后台的Activity由于某原因被系统回收了，如何在被系统回收之前保存当前状态？
  当你的程序中某一个Activity A 在运行时中，主动或被动地运行另一个新的Activity B
  这个时候A会执行
  Java代码
  public void onSaveInstanceState(Bundle outState) {    super.onSaveInstanceState(outState);    outState.putLong("id", 1234567890);}
  B 完成以后又会来找A, 这个时候就有两种情况，一种是A被回收，一种是没有被回收，被回
  收的A就要重新调用onCreate()方法，不同于直接启动的是这回onCreate()里是带上参数savedInstanceState，没被收回的就还是onResume就好了。
  savedInstanceState是一个Bundle对象，你基本上可以把他理解为系统帮你维护的一个Map对象。在onCreate()里你可能会 用到它，如果正常启动onCreate就不会有它，所以用的时候要判断一下是否为空。
  Java代码
  if(savedInstanceState != null){  
     long id = savedInstanceState.getLong("id");  
  }  
  就像官方的Notepad教程 里的情况，你正在编辑某一个note，突然被中断，那么就把这个note的id记住，再起来的时候就可以根据这个id去把那个note取出来，程序就完整 一些。这也是看你的应用需不需要保存什么，比如你的界面就是读取一个列表，那就不需要特殊记住什么，哦， 没准你需要记住滚动条的位置...
27.如何退出Activity
  对于单一Activity的应用来说，退出很简单，直接finish()即可。当然，也可以用killProcess()和System.exit()这样的方法。现提供几个方法，供参考：
  1、抛异常强制退出：该方法通过抛异常，使程序Force Close。验证可以，但是，需要解决的问题是，如何使程序结束掉，而不弹出Force Close的窗口。
  2、记录打开的Activity：每打开一个Activity，就记录下来。在需要退出时，关闭每一个Activity即可。
  3、发送特定广播：在需要结束应用时，发送一个特定的广播，每个Activity收到广播后，关闭即可。
  4、递归退出在打开新的Activity时使用startActivityForResult，然后自己加标志，在onActivityResult中处理，递归关闭。除了第一个，都是想办法把每一个Activity都结束掉，间接达到目的。但是这样做同样不完美。你会发现，如果自己的应用程序对每一个Activity都设置了nosensor，在两个Activity结束的间隙，sensor可能有效了。但至少，我们的目的达到了，而且没有影响用户使用。为了编程方便，最好定义一个Activity基类，处理这些共通问题。
28.请解释下在单线程模型中Message、Handler、Message Queue、Looper之间的关系。
    Message Queue(消息队列)：用来存放通过Handler发布的消息，通常附属于某一个创建它的线程，可以通过Looper.myQueue()得到当前线程的消息队列
　　 Handler：可以发布或者处理一个消息或者操作一个Runnable，通过Handler发布消息，消息将只会发送到与它关联的消息队列，然也只能处理该消息队列中的消息
    Looper：是Handler和消息队列之间通讯桥梁，程序组件首先通过Handler把消息传递给Looper，Looper把消息放入队列。Looper也把消息队列里的消息广播给所有的Handler，Handler接受到消息后调用handleMessage进行处理
　　 Message：消息的类型，在Handler类中的handleMessage方法中得到单个的消息进行处理.
29.你如何评价Android系统？优缺点。
答：优点：1、学习的开源性
　　 2、软件兼容性比较好
　　 3、软件发展迅速
　　 4、界面布局好
　　 缺点：1、版本过多
　　       2、先有软件少  3、商务性能差
30.谈谈android数据存储方式。
  Android提供了5种方式存储数据：
  （1）使用SharedPreferences存储数据；它是Android提供的用来存储一些简单配置信息的一种机制，采用了XML格式将数据存储到设备中。只能在同一个包内使用，不能在不同的包之间使用。
  （2）文件存储数据；文件存储方式是一种较常用的方法，在Android中读取/写入文件的方法，与Java中实现I/O的程序是完全一样的，提供了openFileInput()和openFileOutput()方法来读取设备上的文件。
  （3）SQLite数据库存储数据；SQLite是Android所带的一个标准的数据库，它支持SQL语句，它是一个轻量级的嵌入式数据库。
  （4）使用ContentProvider存储数据；主要用于应用程序之间进行数据交换，从而能够让其他的应用保存或读取此Content Provider的各种数据类型。
  （5）网络存储数据；通过网络上提供给我们的存储空间来上传(存储)和下载(获取)我们存储在网络空间中的数据信息。
31.Android中Activity, Intent, Content Provider, Service各有什么区别。
  Activity： 活动，是最基本的android应用程序组件。一个活动就是一个单独的屏幕，每一个活动都被实现为一个独立的类，并且从活动基类继承而来。
  Intent： 意图，描述应用想干什么。最重要的部分是动作和动作对应的数据。
  Content Provider：内容提供器，android应用程序能够将它们的数据保存到文件、SQLite数据库中，甚至是任何有效的设备中。当你想将你的应用数据和其他应用共享时，内容提供器就可以发挥作用了。
  Service：服务，具有一段较长生命周期且没有用户界面的程序。
32.View, surfaceView, GLSurfaceView有什么区别。
  view是最基础的，必须在UI主线程内更新画面，速度较慢。
  SurfaceView 是view的子类，类似使用双缓机制，在新的线程中更新画面所以刷新界面速度比view快
  GLSurfaceView 是SurfaceView的子类，opengl 专用的
33.Manifest.xml文件中主要包括哪些信息？
  manifest：根节点，描述了package中所有的内容。
  uses-permission：请求你的package正常运作所需赋予的安全许可。
  permission： 声明了安全许可来限制哪些程序能你package中的组件和功能。
  instrumentation：声明了用来测试此package或其他package指令组件的代码。
  application：包含package中application级别组件声明的根节点。
  activity：Activity是用来与用户交互的主要工具。
  receiver：IntentReceiver能使的application获得数据的改变或者发生的操作，即使它当前不在运行。
  service：Service是能在后台运行任意时间的组件。
  provider：ContentProvider是用来管理持久化数据并发布给其他应用程序使用的组件。
34.根据自己的理解描述下Android数字签名。
  (1)所有的应用程序都必须有数字证书，Android系统不会安装一个没有数字证书的应用程序
  (2)Android程序包使用的数字证书可以是自签名的，不需要一个权威的数字证书机构签名认证
  (3)如果要正式发布一个Android ，必须使用一个合适的私钥生成的数字证书来给程序签名，而不能使用adt插件或者ant工具生成的调试证书来发布。
  (4)数字证书都是有有效期的，Android只是在应用程序安装的时候才会检查证书的有效期。如果程序已经安装在系统中，即使证书过期也不会影响程序的正常功能。
35.AIDL的全称是什么?如何工作?能处理哪些类型的数据?
  AIDL全称Android Interface Definition Language（AndRoid接口描述语言）是一种借口描述语言; 编译器可以通过aidl文件生成一段代码，通过预先定义的接口达到两个进程内部通信进程跨界对象访问的目的.AIDL的IPC的机制和COM或CORBA类似, 是基于接口的，但它是轻量级的。它使用代理类在客户端和实现层间传递值. 如果要使用AIDL, 需要完成2件事情: 1. 引入AIDL的相关类.; 2. 调用aidl产生的class.理论上, 参数可以传递基本数据类型和String, 还有就是Bundle的派生类, 不过在Eclipse中,目前的ADT不支持Bundle做为参数,
  具体实现步骤如下:
  1、创建AIDL文件, 在这个文件里面定义接口, 该接口定义了可供客户端访问的方法和属性。
  2、编译AIDL文件, 用Ant的话, 可能需要手动, 使用Eclipse plugin的话,可以根据adil文件自动生产java文件并编译, 不需要人为介入.
  3、在Java文件中, 实现AIDL中定义的接口. 编译器会根据AIDL接口, 产生一个JAVA接口。这个接口有一个名为Stub的内部抽象类，它继承扩展了接口并实现了远程调用需要的几个方法。接下来就需要自己去实现自定义的几个接口了.
  4、向客户端提供接口ITaskBinder, 如果写的是service，扩展该Service并重载onBind ()方法来返回一个实现上述接口的类的实例。
  5、在服务器端回调客户端的函数. 前提是当客户端获取的IBinder接口的时候,要去注册回调函数, 只有这样, 服务器端才知道该调用那些函数
  AIDL语法很简单,可以用来声明一个带一个或多个方法的接口，也可以传递参数和返回值。 由于远程调用的需要, 这些参数和返回值并不是任何类型.下面是些AIDL支持的数据类型:
  1. 不需要import声明的简单Java编程语言类型(int,boolean等)
  2. String, CharSequence不需要特殊声明
  3. List, Map和Parcelables类型, 这些类型内所包含的数据成员也只能是简单数据类型, String等其他比支持的类型.
  (另外: 我没尝试Parcelables, 在Eclipse+ADT下编译不过, 或许以后会有所支持).
  实现接口时有几个原则:
  .抛出的异常不要返回给调用者. 跨进程抛异常处理是不可取的.
  .IPC调用是同步的。如果你知道一个IPC服务需要超过几毫秒的时间才能完成地话，你应该避免在Activity的主线程中调用。也就是IPC调用会挂起应用程序导致界面失去响应. 这种情况应该考虑单起一个线程来处理.
  .不能在AIDL接口中声明静态属性。
  IPC的调用步骤:
  1. 声明一个接口类型的变量，该接口类型在.aidl文件中定义。
  2. 实现ServiceConnection。
  3. 调用ApplicationContext.bindService(),并在ServiceConnection实现中进行传递.
  4. 在ServiceConnection.onServiceConnected()实现中，你会接收一个IBinder实例(被调用的Service). 调用
  YourInterfaceName.Stub.asInterface((IBinder)service)将参数转换为YourInterface类型。
  5. 调用接口中定义的方法。你总要检测到DeadObjectException异常，该异常在连接断开时被抛出。它只会被远程方法抛出。
  6. 断开连接，调用接口实例中的ApplicationContext.unbindService()
  参考：http://buaadallas.blog.51cto.com/399160/372090
36.android:gravity与android:layout_gravity的区别
  LinearLayout有两个非常相似的属性：android:gravity与android:layout_gravity。他们的区别在 于：android:gravity用于设置View组件的对齐方式，而android:layout_gravity用于设置Container组件的 对齐方式。
  举个例子，我们可以通过设置android:gravity="center"来让EditText中的文字在EditText组件中居中显示；同 时我们设置EditText的android:layout_gravity="right"来让EditText组件在LinearLayout中居中 显示。来实践以下：
  正如我们所看到的，在EditText中，其中的文字已经居中显示了，而EditText组件自己也对齐到了LinearLayout的右侧。
  <LinearLayout   
    xmlns:android="http://schemas.android.com/apk/res/android"   
    android:orientation="vertical"   
    android:layout_width="fill_parent"   
    android:layout_height="fill_parent">   
    <EditText   
        android:layout_width="wrap_content"   
        android:gravity="center"   
        android:layout_height="wrap_content"   
        android:text="one"   
        android:layout_gravity="right"/>   
        </LinearLayout>  

        <LinearLayout   
        xmlns:android="http://schemas.android.com/apk/res/android"   
        android:orientation="vertical"   
        android:layout_width="fill_parent"   
        android:layout_height="fill_parent">   
        <EditText   
            android:layout_width="wrap_content"   
            android:gravity="center"   
            android:layout_height="wrap_content"   
            android:text="one"   
            android:layout_gravity="right"/>   
    </LinearLayout>  

    <LinearLayout   
        xmlns:android="http://schemas.android.com/apk/res/android"   
        android:orientation="vertical"   
        android:layout_width="fill_parent"   
        android:layout_height="fill_parent">   
        <EditText   
            android:layout_width="wrap_content"   
            android:gravity="center"   
            android:layout_height="wrap_content"   
            android:text="one"   
            android:layout_gravity="right"/>   
    </LinearLayout>  
    这两个属性也可以用于 Framlayout Textview 等等，表示的意思大同小异
37.padding与margin的区别
  padding填充的意思，指的是view中的content与view边缘的距离，类似文本中的indent
  而margin表示的是view的左边缘与parent view的左边缘的距离
  margin一般用来描述控件间位置关系，而padding一般描述控件内容和控件的位置关系。
  简单，padding是站在父 view的角度描述问题，它规定它里面的内容必须与这个父view边界的距离。margin则是站在自己的角度描述问题，规定自己和其他（上下左右）的 view之间的距离，如果同一级只有一个view，那么它的效果基本上就和padding一样了。例如我的XML layout代码如下：
  view plaincopy to clipboardprint?
  <?xml version="1.0" encoding="utf-8"?>   
  <LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"   
      android:orientation="vertical"   
      android:layout_width="fill_parent"   
      android:layout_height="fill_parent"   
      android:paddingLeft="10dip"   
      android:paddingRight="10dip"   
      android:paddingTop="10dip"   
      android:paddingBottom="10dip"   
      >   
  <TextView      
      android:layout_width="wrap_content"     
      android:layout_height="wrap_content"     
      android:background="#FF0000"   
      android:text="@string/hello"   
      android:paddingLeft="50dip"   
      android:paddingRight="50dip"   
      android:paddingTop="50dip"   
      android:paddingBottom="50dip"   
      android:layout_marginBottom="10dip"   
      />   
      <TextView      
      android:layout_width="wrap_content"     
      android:layout_height="wrap_content"     
      android:background="#FF0000"   
      android:text="@string/hello"   
      android:paddingLeft="50dip"   
      android:paddingRight="50dip"   
      android:paddingTop="50dip"   
      android:paddingBottom="50dip"   
      android:layout_marginBottom="10dip"   
      />   
      <TextView      
      android:layout_width="wrap_content"     
      android:layout_height="wrap_content"     
      android:background="#FF0000"   
      android:text="@string/hello"   
      android:paddingLeft="50dip"   
      android:paddingRight="50dip"   
      android:paddingTop="50dip"   
      android:paddingBottom="50dip"   
      android:layout_marginBottom="10dip"   
      />   
      <TextView      
      android:layout_width="wrap_content"     
      android:layout_height="wrap_content"     
      android:background="#FF0000"   
      android:text="@string/hello"   
      android:paddingLeft="50dip"   
      android:paddingRight="50dip"   
      android:paddingTop="50dip"   
      android:paddingBottom="50dip"   
      android:layout_marginBottom="10dip"   
      />   
  </LinearLayout>    

  <?xml version="1.0" encoding="utf-8"?>   
  <LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"   
      android:orientation="vertical"   
      android:layout_width="fill_parent"   
      android:layout_height="fill_parent"   
      android:paddingLeft="10dip"   
      android:paddingRight="10dip"   
      android:paddingTop="10dip"   
      android:paddingBottom="10dip"   
      >   
  <TextView      
      android:layout_width="wrap_content"     
      android:layout_height="wrap_content"     
      android:background="#FF0000"   
      android:text="@string/hello"   
      android:paddingLeft="50dip"   
      android:paddingRight="50dip"   
      android:paddingTop="50dip"   
      android:paddingBottom="50dip"   
      android:layout_marginBottom="10dip"   
      />   
      <TextView      
      android:layout_width="wrap_content"     
      android:layout_height="wrap_content"     
      android:background="#FF0000"   
      android:text="@string/hello"   
      android:paddingLeft="50dip"   
      android:paddingRight="50dip"   
      android:paddingTop="50dip"   
      android:paddingBottom="50dip"   
      android:layout_marginBottom="10dip"   
      />   
      <TextView      
      android:layout_width="wrap_content"     
      android:layout_height="wrap_content"     
      android:background="#FF0000"   
      android:text="@string/hello"   
      android:paddingLeft="50dip"   
      android:paddingRight="50dip"   
      android:paddingTop="50dip"   
      android:paddingBottom="50dip"   
      android:layout_marginBottom="10dip"   
      />   
      <TextView      
      android:layout_width="wrap_content"     
      android:layout_height="wrap_content"     
      android:background="#FF0000"   
      android:text="@string/hello"   
      android:paddingLeft="50dip"   
      android:paddingRight="50dip"   
      android:paddingTop="50dip"   
      android:paddingBottom="50dip"   
      android:layout_marginBottom="10dip"   
      />   
  </LinearLayout>    

  <?xml version="1.0" encoding="utf-8"?>   
  <LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"   
      android:orientation="vertical"   
      android:layout_width="fill_parent"   
      android:layout_height="fill_parent"   
      android:paddingLeft="10dip"   
      android:paddingRight="10dip"   
      android:paddingTop="10dip"   
      android:paddingBottom="10dip"   
      >   
  <TextView      
      android:layout_width="wrap_content"     
      android:layout_height="wrap_content"     
      android:background="#FF0000"   
      android:text="@string/hello"   
      android:paddingLeft="50dip"   
      android:paddingRight="50dip"   
      android:paddingTop="50dip"   
      android:paddingBottom="50dip"   
      android:layout_marginBottom="10dip"   
      />   
      <TextView      
      android:layout_width="wrap_content"     
      android:layout_height="wrap_content"     
      android:background="#FF0000"   
      android:text="@string/hello"   
      android:paddingLeft="50dip"   
      android:paddingRight="50dip"   
      android:paddingTop="50dip"   
      android:paddingBottom="50dip"   
      android:layout_marginBottom="10dip"   
      />   
      <TextView      
      android:layout_width="wrap_content"     
      android:layout_height="wrap_content"     
      android:background="#FF0000"   
      android:text="@string/hello"   
      android:paddingLeft="50dip"   
      android:paddingRight="50dip"   
      android:paddingTop="50dip"   
      android:paddingBottom="50dip"   
      android:layout_marginBottom="10dip"   
      />   
      <TextView      
      android:layout_width="wrap_content"     
      android:layout_height="wrap_content"     
      android:background="#FF0000"   
      android:text="@string/hello"   
      android:paddingLeft="50dip"   
      android:paddingRight="50dip"   
      android:paddingTop="50dip"   
      android:paddingBottom="50dip"   
      android:layout_marginBottom="10dip"   
      />   
  </LinearLayout>    
  那么我会得到如下的效果，图上已经很明确的标出来区别咯。
38. 注册广播接收者两种方式的区别
  现在我们就来实现一个简单的广播程序。Android提供了两种注册广播接受者的形式，分别是在程序中动态注册和在xml中指定。他们之间的区别就是作用 的范围不同，程序动态注册的接收者只在程序运行过程中有效，而在xml注册的接收者不管你的程序有没有启动有会起作用。
39.Dalvik基于JVM的改进
  1.几个class变为一个dex，constant pool，省内存
  2.Zygote，copy-on-write shared,省内存，省cpu，省电
  3.基于寄存器的bytecode，省指令，省cpu，省电
  4.Trace-based JIT,省cpu，省电,省内存
40.android中有哪几种解析xml的类,官方推荐哪种？以及它们的原理和区别.
  Ø DOM解析
    优点:
  1.XML树在内存中完整存储,因此可以直接修改其数据和结构.
  2.可以通过该解析器随时访问XML树中的任何一个节点.
  3.DOM解析器的API在使用上也相对比较简单.
  缺点:如果XML文档体积比较大时,将文档读入内存是非常消耗系统资源的.
  使用场景:DOM 是用与平台和语言无关的方式表示 XML 文档的官方 W3C 标准.DOM 是以层次结构组织的节点的集合.这个层次结构允许开发人员在树中寻找特定信息.分析该结构通常需要加载整个文档和构造层次结构,然后才能进行任何工作.DOM是基于对象层次结构的.
  Ø SAX解析
  优点:
  SAX 对内存的要求比较低,因为它让开发人员自己来决定所要处理的标签.特别是当开发人员只需要处理文档中所包含的部分数据时,SAX 这种扩展能力得到了更好的体现.
  缺点:
  用SAX方式进行XML解析时,需要顺序执行,所以很难访问到同一文档中的不同数据.此外,在基于该方式的解析编码过程也相对复杂.
  使用场景:
  对于含有数据量十分巨大,而又不用对文档的所有数据进行遍历或者分析的时候,使用该方法十分有效.该方法不用将整个文档读入内存,而只需读取到程序所需的文档标签处即可.
  Ø Xmlpull解析
  android SDK提供了xmlpull api,xmlpull和sax类似,是基于流（stream）操作文件,然后根据节点事件回调开发者编写的处理程序.因为是基于流的处理,因此xmlpull和sax都比较节约内存资源,不会象dom那样要把所有节点以对橡树的形式展现在内存中.xmlpull比sax更简明,而且不需要扫描完整个流.
41.Android系统中GC什么情况下会出现内存泄露呢？
  出现情况:
  1. 数据库的cursor没有关闭
  2.构造adapter时,没有使用缓存contentview
     衍生listview的优化问题-----减少创建view的对象,充分使用contentview,可以使用一静态类来优化处理getview的过程/
  3.Bitmap对象不使用时采用recycle()释放内存
  4.activity中的对象的生命周期大于activity
  调试方法: DDMS==> HEAPSZIE==>dataobject==>[Total Size]
42.谈谈对Android NDK的理解
  NDK 全称: Native Development Kit
  2.误解
      误解一: NDK 发布之前, Android 不支持进行 C 开发
      在Google 中搜索 “NDK” ,很多 “Android 终于可以使用 C++ 开发 ” 之类的标题,这是一种对 Android 平台编程方式的误解.其实, Android 平台从诞生起,就已经支持 C . C++ 开发.众所周知, Android 的 SDK 基于 Java 实现,这意味着基于 Android SDK 进行开发的第三方应用都必须使用 Java 语言.但这并不等同于 “ 第三方应用只能使用 Java” .在 Android SDK 首次发布时, Google 就宣称其虚拟机 Dalvik 支持 JNI 编程方式,也就是第三方应用完全可以通过 JNI 调用自己的 C 动态库,即在 Android 平台上, “Java+C” 的编程方式是一直都可以实现的.
  当然这种误解的产生是有根源的:在Android SDK 文档里,找不到任何 JNI 方面的帮助.即使第三方应用开发者使用 JNI 完成了自己的 C 动态链接库（ so ）开发,但是 so 如何和应用程序一起打包成 apk 并发布？这里面也存在技术障碍.我曾经花了不少时间,安装交叉编译器创建 so ,并通过 asset （资源）方式,实现捆绑 so 发布.但这种方式只能属于取巧的方式,并非官方支持.所以,在 NDK 出来之前,我们将 “Java+C” 的开发模式称之为灰色模式,即官方既不声明 “ 支持这种方式 ” ,也不声明 “ 不支持这种方式 ” .
  误解二:有了 NDK ,我们可以使用纯 C 开发 Android 应用
  Android SDK采用 Java 语言发布,把众多的 C 开发人员排除在第三方应用开发外（ 注意:我们所有讨论都是基于“ 第三方应用开发 ” , Android 系统基于 Linux ,系统级别的开发肯定是支持 C 语言的. ）.NDK 的发布,许多人会误以为,类似于 Symbian . WM ,在 Android 平台上终于可以使用纯 C . C++ 开发第三方应用了！其实不然, NDK 文档明确说明: it is not a good way .因为 NDK 并没有提供各种系统事件处理支持,也没有提供应用程序生命周期维护.此外,在本次发布的 NDK 中,应用程序 UI 方面的 API 也没有提供.至少目前来说,使用纯 C . C++ 开发一个完整应用的条件还不完备.
     1.NDK 是一系列工具的集合.
  NDK提供了一系列的工具,帮助开发者快速开发 C （或 C++ ）的动态库,并能自动将 so 和 java 应用一起打包成 apk .这些工具对开发者的帮助是巨大的.
  NDK集成了交叉编译器,并提供了相应的 mk 文件隔离 CPU .平台. ABI 等差异,开发人员只需要简单修改 mk 文件（指出 “ 哪些文件需要编译 ” . “ 编译特性要求 ” 等）,就可以创建出 NDK可以自动地将 so 和 Java 应用一起打包,极大地减轻了开发人员的打包工作.
     2.NDK 提供了一份稳定.功能有限的 API 头文件声明.
  Google明确声明该 API 是稳定的,在后续所有版本中都稳定支持当前发布的 API .从该版本的 NDK 中看出,这些 API 支持的功能非常有限,包含有: C 标准库（ libc ）.标准数学库（ libm ）.压缩库（ libz ）. Log 库（ liblog ）.
  3.NDK 带来什么
  1.NDK 的发布,使 “Java+C” 的开发方式终于转正,成为官方支持的开发方式.
  使用NDK ,我们可以将要求高性能的应用逻辑使用 C 开发,从而提高应用程序的执行效率.
  使用NDK ,我们可以将需要保密的应用逻辑使用 C 开发.毕竟, Java 包都是可以反编译的.
  NDK促使专业 so 组件商的出现.（乐观猜想,要视乎 Android 用户的数量）
      2.NDK 将是 Android 平台支持 C 开发的开端. NDK提供了的开发工具集合,使开发人员可以便捷地开发.发布 C 组件.同时, Google承诺在 NDK 后续版本中提高 “ 可调式 ” 能力,即提供远程的 gdb 工具,使我们可以便捷地调试 C 源码.在支持 Android 平台 C 开发,我们能感觉到 Google 花费了很大精力,我们有理由憧憬 “C 组件支持 ” 只是 Google Android 平台上C 开发的开端.毕竟, C 程序员仍然是码农阵营中的绝对主力,将这部分人排除在 Android 应用开发之外,显然是不利于 Android 平台繁荣昌盛的.
