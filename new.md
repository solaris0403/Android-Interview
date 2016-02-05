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
1、一个".java"源文件中是否可以包括多个类（不是内部类）？有什么限制？ 
  可以有多个类，但只能有一个public的类，并且public的类名必须与文件名相一致。 
2、Java有没有goto?  
  java中的保留字，现在没有在java中使用。 
3、说说&和&&的区别。 
  &和&&都可以用作逻辑与的运算符，表示逻辑与（and），当运算符两边的表达式的结果都为true时，整个运算结果才为true，否则，只要有一方为false，则结果为false。
  &&还具有短路的功能，即如果第一个表达式为false，则不再计算第二个表达式，例如，对于if(str != null && !str.equals(“”))表达式，当str为null时，后面的表达式不会执行，所以不会出现NullPointerException如果将&&改为&，则会抛出NullPointerException异常。If(x==33 & ++y>0) y会增长，If(x==33 && ++y>0)不会增长
  &还可以用作位运算符，当&操作符两边的表达式不是boolean类型时，&表示按位与操作，我们通常使用0x0f来与一个整数进行&运算，来获取该整数的最低4个bit位，例如，0x31 & 0x0f的结果为0x01。
  备注：这道题先说两者的共同点，再说出&&和&的特殊之处，并列举一些经典的例子来表明自己理解透彻深入、实际经验丰富。  
6、short s1 = 1; s1 = s1 + 1;有什么错? short s1 = 1; s1 += 1;有什么错?  
  对于short s1 = 1; s1 = s1 + 1; 由于s1+1运算时会自动提升表达式的类型，所以结果是int型，再赋值给short类型s1时，编译器将报告需要强制转换类型的错误。
  对于short s1 = 1; s1 += 1;由于 += 是java语言规定的运算符，java编译器会对它进行特殊处理，因此可以正确编译。  
7、char型变量中能不能存贮一个中文汉字?为什么?  
  char型变量是用来存储Unicode编码的字符的，unicode编码字符集中包含了汉字，所以，char型变量中当然可以存储汉字啦。不过，如果某个特殊的汉字没有被包含在unicode编码字符集中，那么，这个char型变量中就不能存储这个特殊汉字。补充说明：unicode编码占用两个字节，所以，char类型的变量也是占用两个字节。
  备注：后面一部分回答虽然不是在正面回答题目，但是，为了展现自己的学识和表现自己对问题理解的透彻深入，可以回答一些相关的知识，做到知无不言，言无不尽。  
8、用最有效率的方法算出2乘以8等於几?  
  2 << 3，
  因为将一个数左移n位，就相当于乘以了2的n次方，那么，一个数乘以8只要将其左移3位即可，而位运算cpu直接支持的，效率最高，所以，2乘以8等於几的最效率的方法是2 << 3。 
10、使用final关键字修饰一个变量时，是引用不能变，还是引用的对象不能变？  
  使用final关键字修饰一个变量时，是指引用变量不能变，引用变量所指向的对象中的内容还是可以改变的。例如，对于如下语句：
  final StringBuffer a=new StringBuffer("immutable");
  执行如下语句将报告编译期错误：
  a=new StringBuffer("");
  但是，执行如下语句则可以通过编译：
  a.append(" broken!"); 

  有人在定义方法的参数时，可能想采用如下形式来阻止方法内部修改传进来的参数对象：
  public void method(final  StringBuffer  param){
  }
  实际上，这是办不到的，在该方法内部仍然可以增加如下代码来修改参数对象：
    param.append("a"); 
11、"=="和equals方法究竟有什么区别？ 
  （单独把一个东西说清楚，然后再说清楚另一个，这样，它们的区别自然就出来了，混在一起说，则很难说清楚）
  ==操作符专门用来比较两个变量的值是否相等，也就是用于比较变量所对应的内存中所存储的数值是否相同，要比较两个基本类型的数据或两个引用变量是否相等，只能用==操作符。
  如果一个变量指向的数据是对象类型的，那么，这时候涉及了两块内存，对象本身占用一块内存（堆内存），变量也占用一块内存，例如Objet obj = new Object();变量obj是一个内存，new Object()是另一个内存，此时，变量obj所对应的内存中存储的数值就是对象占用的那块内存的首地址。对于指向对象类型的变量，如果要比较两个变量是否指向同一个对象，即要看这两个变量所对应的内存中的数值是否相等，这时候就需要用==操作符进行比较。
  equals方法是用于比较两个独立对象的内容是否相同，就好比去比较两个人的长相是否相同，它比较的两个对象是独立的。例如，对于下面的代码：
  String a=new String("foo");
  String b=new String("foo");
  两条new语句创建了两个对象，然后用a,b这两个变量分别指向了其中一个对象，这是两个不同的对象，它们的首地址是不同的，即a和b中存储的数值是不相同的，所以，表达式a==b将返回false，而这两个对象中的内容是相同的，所以，表达式a.equals(b)将返回true。
  在实际开发中，我们经常要比较传递进行来的字符串内容是否等，例如，String input = …;input.equals(“quit”)，许多人稍不注意就使用==进行比较了，这是错误的，随便从网上找几个项目实战的教学视频看看，里面就有大量这样的错误。记住，字符串的比较基本上都是使用equals方法。
  如果一个类没有自己定义equals方法，那么它将继承Object类的equals方法，Object类的equals方法的实现代码如下：
  boolean equals(Object o){
  return this==o;
  }
  这说明，如果一个类没有自己定义equals方法，它默认的equals方法（从Object 类继承的）就是使用==操作符，也是在比较两个变量指向的对象是否是同一对象，这时候使用equals和使用==会得到同样的结果，如果比较的是两个独立的对象则总返回false。如果你编写的类希望能够比较该类创建的两个实例对象的内容是否相同，那么你必须覆盖equals方法，由你自己写代码来决定在什么情况即可认为两个对象的内容是相同的。 
12、静态变量和实例变量的区别？  
  在语法定义上的区别：静态变量前要加static关键字，而实例变量前则不加。
  在程序运行时的区别：实例变量属于某个对象的属性，必须创建了实例对象，其中的实例变量才会被分配空间，才能使用这个实例变量。静态变量不属于某个实例对象，而是属于类，所以也称为类变量，只要程序加载了类的字节码，不用创建任何实例对象，静态变量就会被分配空间，静态变量就可以被使用了。总之，实例变量必须创建对象后才可以通过这个对象来使用，静态变量则可以直接使用类名来引用。
  例如，对于下面的程序，无论创建多少个实例对象，永远都只分配了一个staticVar变量，并且每创建一个实例对象，这个staticVar就会加1；但是，每创建一个实例对象，就会分配一个instanceVar，即可能分配多个instanceVar，并且每个instanceVar的值都只自加了1次。
  public class VariantTest{
    public static int staticVar = 0;
    public int instanceVar = 0;
    public VariantTest(){
      staticVar++;
      instanceVar++;
      System.out.println(“staticVar=” + staticVar + ”,instanceVar=” + instanceVar);
    }
  }
  备注：这个解答除了说清楚两者的区别外，最后还用一个具体的应用例子来说明两者的差异，体现了自己有很好的解说问题和设计案例的能力，思维敏捷，超过一般程序员，有写作能力！ 
13、是否可以从一个static方法内部发出对非static方法的调用？  
  不可以。因为非static方法是要与对象关联在一起的，必须创建一个对象后，才可以在该对象上进行方法调用，而static方法调用时不需要创建对象，可以直接调用。也就是说，当一个static方法被调用时，可能还没有创建任何实例对象，如果从一个static方法中发出对非static方法的调用，那个非static方法是关联到哪个对象上的呢？这个逻辑无法成立，所以，一个static方法内部发出对非static方法的调 
14、Integer与int的区别 
  int是java提供的8种原始数据类型之一。Java为每个原始类型提供了封装类，Integer是java为int提供的封装类。int的默认值为0，而Integer的默认值为null，即Integer可以区分出未赋值和值为0的区别，int则无法表达出未赋值的情况，例如，要想表达出没有参加考试和考试成绩为0的区别，则只能使用Integer。在JSP开发中，Integer的默认为null，所以用el表达式在文本框中显示时，值为空白字符串，而int默认的默认值为0，所以用el表达式在文本框中显示时，结果为0，所以，int不适合作为web层的表单数据的类型。
  在Hibernate中，如果将OID定义为Integer类型，那么Hibernate就可以根据其值是否为null而判断一个对象是否是临时的，如果将OID定义为了int类型，还需要在hbm映射文件中设置其unsaved-value属性为0。
  另外，Integer提供了多个与整数相关的操作方法，例如，将一个字符串转换成整数，Integer中还定义了表示整数的最大值和最小值的常量。 
15、Math.round(11.5)等於多少? Math.round(-11.5)等於多少?
  Math类中提供了三个与取整有关的方法：ceil、floor、round，这些方法的作用与它们的英文名称的含义相对应，例如，ceil的英文意义是天花板，该方法就表示向上取整，Math.ceil(11.3)的结果为12,Math.ceil(-11.3)的结果是-11；floor的英文意义是地板，该方法就表示向下取整，Math.ceil(11.6)的结果为11,Math.ceil(-11.6)的结果是-12；最难掌握的是round方法，它表示“四舍五入”，算法为Math.floor(x+0.5)，即将原来的数字加上0.5后再向下取整，所以，Math.round(11.5)的结果为12，Math.round(-11.5)的结果为-11。 
17、请说出作用域public，private，protected，以及不写时的区别
  这四个作用域的可见范围如下表所示。
  说明：如果在修饰的元素上面没有写任何访问修饰符，则表示friendly。
  作用域    当前类 同一package 子孙类 其他package
  public    √     √          √       √
  protected  √     √          √      ×
  friendly   √     √          ×      ×
  private    √     ×          ×      ×
  备注：只要记住了有4种访问权限，4个访问范围，然后将全选和范围在水平和垂直方向上分别按排从小到大或从大到小的顺序排列，就很容易画出上面的图了。 
18、Overload和Override的区别。Overloaded的方法是否可以改变返回值的类型?  
  Overload是重载的意思，Override是覆盖的意思，也就是重写。
  重载Overload表示同一个类中可以有多个名称相同的方法，但这些方法的参数列表各不相同（即参数个数或类型不同）。
  重写Override表示子类中的方法可以与父类中的某个方法的名称和参数完全相同，通过子类创建的实例对象调用这个方法时，将调用子类中的定义方法，这相当于把父类中定义的那个完全相同的方法给覆盖了，这也是面向对象编程的多态性的一种表现。子类覆盖父类的方法时，只能比父类抛出更少的异常，或者是抛出父类抛出的异常的子异常，因为子类可以解决父类的一些问题，不能比父类有更多的问题。子类方法的访问权限只能比父类的更大，不能更小。如果父类的方法是private类型，那么，子类则不存在覆盖的限制，相当于子类中增加了一个全新的方法。
  至于Overloaded的方法是否可以改变返回值的类型这个问题，要看你倒底想问什么呢？这个题目很模糊。如果几个Overloaded的方法的参数列表不一样，它们的返回者类型当然也可以不一样。但我估计你想问的问题是：如果两个方法的参数列表完全一样，是否可以让它们的返回值不同来实现重载Overload。这是不行的，我们可以用反证法来说明这个问题，因为我们有时候调用一个方法时也可以不定义返回结果变量，即不要关心其返回结果，例如，我们调用map.remove(key)方法时，虽然remove方法有返回值，但是我们通常都不会定义接收返回结果的变量，这时候假设该类中有两个名称和参数列表完全相同的方法，仅仅是返回类型不同，java就无法确定编程者倒底是想调用哪个方法了，因为它无法通过返回结果类型来判断。

  override可以翻译为覆盖，从字面就可以知道，它是覆盖了一个方法并且对其重写，以求达到不同的作用。对我们来说最熟悉的覆盖就是对接口方法的实现，在接口中一般只是对方法进行了声明，而我们在实现时，就需要实现接口声明的所有方法。除了这个典型的用法以外，我们在继承中也可能会在子类覆盖父类中的方法。在覆盖要注意以下的几点：
  1、覆盖的方法的标志必须要和被覆盖的方法的标志完全匹配，才能达到覆盖的效果；
  2、覆盖的方法的返回值必须和被覆盖的方法的返回一致；
  3、覆盖的方法所抛出的异常必须和被覆盖方法的所抛出的异常一致，或者是其子类；
  4、被覆盖的方法不能为private，否则在其子类中只是新定义了一个方法，并没有对其进行覆盖。
  overload对我们来说可能比较熟悉，可以翻译为重载，它是指我们可以定义一些名称相同的方法，通过定义不同的输入参数来区分这些方法，然后再调用时，VM就会根据不同的参数样式，来选择合适的方法执行。在使用重载要注意以下的几点：
  1、在使用重载时只能通过不同的参数样式。例如，不同的参数类型，不同的参数个数，不同的参数顺序（当然，同一方法内的几个参数类型必须不一样，例如可以是fun(int,float)，但是不能为fun(int,int)）；
  2、不能通过访问权限、返回类型、抛出的异常进行重载；
  3、方法的异常类型和数目不会对重载造成影响；
  4、对于继承来说，如果某一方法在父类中是访问权限是priavte，那么就不能在子类对其进行重载，如果定义的话，也只是定义了一个新方法，而不会达到重载的效果。 
19、构造器Constructor是否可被override?
  构造器Constructor不能被继承，因此不能重写Override，但可以被重载Overload。  
20、接口是否可继承接口? 抽象类是否可实现(implements)接口? 抽象类是否可继承具体类(concrete class)? 抽象类中是否可以有静态的main方法？
  接口可以继承接口。抽象类可以实现(implements)接口，抽象类是否可继承具体类。抽象类中可以有静态的main方法。
  备注：只要明白了接口和抽象类的本质和作用，这些问题都很好回答，你想想，如果你是java语言的设计者，你是否会提供这样的支持，如果不提供的话，有什么理由吗？如果你没有道理不提供，那答案就是肯定的了。
   只有记住抽象类与普通类的唯一区别就是不能创建实例对象和允许有abstract方法。 
21、写clone()方法时，通常都有一行代码，是什么？  
  clone 有缺省行为，super.clone();因为首先要把父类中的成员复制到位，然后才是复制自己的成员。  
22、面向对象的特征有哪些方面 
  计算机软件系统是现实生活中的业务在计算机中的映射，而现实生活中的业务其实就是一个个对象协作的过程。面向对象编程就是按现实业务一样的方式将程序代码按一个个对象进行组织和编写，让计算机系统能够识别和理解用对象方式组织和编写的程序代码，这样就可以把现实生活中的业务对象映射到计算机系统中。
  面向对象的编程语言有，吗 等4个主要的特征。
  1封装：
  封装是保证软件部件具有优良的模块性的基础，封装的目标就是要实现软件部件的“高内聚、低耦合”，防止程序相互依赖性而带来的变动影响。在面向对象的编程语言中，对象是封装的最基本单位，面向对象的封装比传统语言的封装更为清晰、更为有力。面向对象的封装就是把描述一个对象的属性和行为的代码封装在一个“模块”中，也就是一个类中，属性用变量定义，行为用方法进行定义，方法可以直接访问同一个对象中的属性。通常情况下，只要记住让变量和访问这个变量的方法放在一起，将一个类中的成员变量全部定义成私有的，只有这个类自己的方法才可以访问到这些成员变量，这就基本上实现对象的封装，就很容易找出要分配到这个类上的方法了，就基本上算是会面向对象的编程了。把握一个原则：把对同一事物进行操作的方法和相关的方法放在同一个类中，把方法和它操作的数据放在同一个类中。
  例如，人要在黑板上画圆，这一共涉及三个对象：人、黑板、圆，画圆的方法要分配给哪个对象呢？由于画圆需要使用到圆心和半径，圆心和半径显然是圆的属性，如果将它们在类中定义成了私有的成员变量，那么，画圆的方法必须分配给圆，它才能访问到圆心和半径这两个属性，人以后只是调用圆的画圆方法、表示给圆发给消息而已，画圆这个方法不应该分配在人这个对象上，这就是面向对象的封装性，即将对象封装成一个高度自治和相对封闭的个体，对象状态（属性）由这个对象自己的行为（方法）来读取和改变。一个更便于理解的例子就是，司机将火车刹住了，刹车的动作是分配给司机，还是分配给火车，显然，应该分配给火车，因为司机自身是不可能有那么大的力气将一个火车给停下来的，只有火车自己才能完成这一动作，火车需要调用内部的离合器和刹车片等多个器件协作才能完成刹车这个动作，司机刹车的过程只是给火车发了一个消息，通知火车要执行刹车动作而已。

  抽象：
  抽象就是找出一些事物的相似和共性之处，然后将这些事物归为一个类，这个类只考虑这些事物的相似和共性之处，并且会忽略与当前主题和目标无关的那些方面，将注意力集中在与当前目标有关的方面。例如，看到一只蚂蚁和大象，你能够想象出它们的相同之处，那就是抽象。抽象包括行为抽象和状态抽象两个方面。例如，定义一个Person类，如下：
  class Person{
    String name;
    int age;
  }
  人本来是很复杂的事物，有很多方面，但因为当前系统只需要了解人的姓名和年龄，所以上面定义的类中只包含姓名和年龄这两个属性，这就是一种抽像，使用抽象可以避免考虑一些与目标无关的细节。我对抽象的理解就是不要用显微镜去看一个事物的所有方面，这样涉及的内容就太多了，而是要善于划分问题的边界，当前系统需要什么，就只考虑什么。

  继承：
  在定义和实现一个类的时候，可以在一个已经存在的类的基础之上来进行，把这个已经存在的类所定义的内容作为自己的内容，并可以加入若干新的内容，或修改原来的方法使之更适合特殊的需要，这就是继承。继承是子类自动共享父类数据和方法的机制，这是类之间的一种关系，提高了软件的可重用性和可扩展性。

  多态：
  多态是指程序中定义的引用变量所指向的具体类型和通过该引用变量发出的方法调用在编程时并不确定，而是在程序运行期间才确定，即一个引用变量倒底会指向哪个类的实例对象，该引用变量发出的方法调用到底是哪个类中实现的方法，必须在由程序运行期间才能决定。因为在程序运行时才确定具体的类，这样，不用修改源程序代码，就可以让引用变量绑定到各种不同的类实现上，从而导致该引用调用的具体方法随之改变，即不修改程序代码就可以改变程序运行时所绑定的具体代码，让程序可以选择多个运行状态，这就是多态性。多态性增强了软件的灵活性和扩展性。例如，下面代码中的UserDao是一个接口，它定义引用变量userDao指向的实例对象由daofactory.getDao()在执行的时候返回，有时候指向的是UserJdbcDao这个实现，有时候指向的是UserHibernateDao这个实现，这样，不用修改源代码，就可以改变userDao指向的具体类实现，从而导致userDao.insertUser()方法调用的具体代码也随之改变，即有时候调用的是UserJdbcDao的insertUser方法，有时候调用的是UserHibernateDao的insertUser方法：
  UserDao userDao = daofactory.getDao();  
  userDao.insertUser(user);
  比喻：人吃饭，你看到的是左手，还是右手？ 
23、java中实现多态的机制是什么？  
  靠的是父类或接口定义的引用变量可以指向子类或具体实现类的实例对象，而程序调用的方法在运行期才动态绑定，就是引用变量所指向的具体实例对象的方法，也就是内存里正在运行的那个对象的方法，而不是引用变量的类型中定义的方法。  
24、abstract class和interface有什么区别? 	

  含有abstract修饰符的class即为抽象类，abstract 类不能创建的实例对象。含有abstract方法的类必须定义为abstract class，abstract class类中的方法不必是抽象的。abstract class类中定义抽象方法必须在具体(Concrete)子类中实现，所以，不能有抽象构造方法或抽象静态方法。如果的子类没有实现抽象父类中的所有抽象方法，那么子类也必须定义为abstract类型。
  接口（interface）可以说成是抽象类的一种特例，接口中的所有方法都必须是抽象的。接口中的方法定义默认为public abstract类型，接口中的成员变量类型默认为public static final。
  下面比较一下两者的语法区别：
  1.抽象类可以有构造方法，接口中不能有构造方法。
  2.抽象类中可以有普通成员变量，接口中没有普通成员变量
  3.抽象类中可以包含非抽象的普通方法，接口中的所有方法必须都是抽象的，不能有非抽象的普通方法。
  4. 抽象类中的抽象方法的访问类型可以是public，protected和（默认类型,虽然
  eclipse下不报错，但应该也不行），但接口中的抽象方法只能是public类型的，并且默认即为public abstract类型。
  5. 抽象类中可以包含静态方法，接口中不能包含静态方法
  6. 抽象类和接口中都可以包含静态成员变量，抽象类中的静态成员变量的访问类型可以任意，但接口中定义的变量只能是public static final类型，并且默认即为public static final类型。
  7. 一个类可以实现多个接口，但只能继承一个抽象类。
  	下面接着再说说两者在应用上的区别：
  接口更多的是在系统架构设计方法发挥作用，主要用于定义模块之间的通信契约。而抽象类在代码实现方面发挥作用，可以实现代码的重用，例如，模板方法设计模式是抽象类的一个典型应用，假设某个项目的所有Servlet类都要用相同的方式进行权限判断、记录访问日志和处理异常，那么就可以定义一个抽象的基类，让所有的Servlet都继承这个抽象基类，在抽象基类的service方法中完成权限判断、记录访问日志和处理异常的代码，在各个子类中只是完成各自的业务逻辑代码，伪代码如下：
  public abstract class BaseServlet extends HttpServlet{
  		public final void service(HttpServletRequest request, HttpServletResponse response) throws IOExcetion,ServletException	{
  			记录访问日志
  			进行权限判断
  if(具有权限){
  	try{
  		doService(request,response);
  }
  	catch(Excetpion e)	{
  			记录异常信息
  	}
  }
  		}
  		protected abstract void doService(HttpServletRequest request, HttpServletResponse response) throws IOExcetion,ServletException;  
  //注意访问权限定义成protected，显得既专业，又严谨，因为它是专门给子类用的
  }

  public class MyServlet1 extends BaseServlet
  {
  protected void doService(HttpServletRequest request, HttpServletResponse response) throws IOExcetion,ServletException
  		{
  			本Servlet只处理的具体业务逻辑代码
  		}

  }
  父类方法中间的某段代码不确定，留给子类干，就用模板方法设计模式。
  备注：这道题的思路是先从总体解释抽象类和接口的基本概念，然后再比较两者的语法细节，最后再说两者的应用区别。比较两者语法细节区别的条理是：先从一个类中的构造方法、普通成员变量和方法（包括抽象方法），静态变量和方法，继承性等6个方面逐一去比较回答，接着从第三者继承的角度的回答，特别是最后用了一个典型的例子来展现自己深厚的技术功底。 
25、abstract的method是否可同时是static,是否可同时是native，是否可同时是synchronized?
  abstract的method 不可以是static的，因为抽象的方法是要被子类实现的，而static与子类扯不上关系！
  native方法表示该方法要用另外一种依赖平台的编程语言实现的，不存在着被子类实现的问题，所以，它也不能是抽象的，不能与abstract混用。例如，FileOutputSteam类要硬件打交道，底层的实现用的是操作系统相关的api实现，例如，在windows用c语言实现的，所以，查看jdk 的源代码，可以发现FileOutputStream的open方法的定义如下：
  private native void open(String name) throws FileNotFoundException;
  如果我们要用java调用别人写的c语言函数，我们是无法直接调用的，我们需要按照java的要求写一个c语言的函数，又我们的这个c语言函数去调用别人的c语言函数。由于我们的c语言函数是按java的要求来写的，我们这个c语言函数就可以与java对接上，java那边的对接方式就是定义出与我们这个c函数相对应的方法，java中对应的方法不需要写具体的代码，但需要在前面声明native。
  关于synchronized与abstract合用的问题，我觉得也不行，因为在我几年的学习和开发中，从来没见到过这种情况，并且我觉得synchronized应该是作用在一个具体的方法上才有意义。而且，方法上的synchronized同步所使用的同步锁对象是this，而抽象方法上无法确定this是什么。  
26、什么是内部类？Static Nested Class 和 Inner Class的不同。 
  内部类就是在一个类的内部定义的类，内部类中不能定义静态成员（静态成员不是对象的特性，只是为了找一个容身之处，所以需要放到一个类中而已，这么一点小事，你还要把它放到类内部的一个类中，过分了啊！提供内部类，不是为让你干这种事情，无聊，不让你干。我想可能是既然静态成员类似c语言的全局变量，而内部类通常是用于创建内部对象用的，所以，把“全局变量”放在内部类中就是毫无意义的事情，既然是毫无意义的事情，就应该被禁止），内部类可以直接访问外部类中的成员变量，内部类可以定义在外部类的方法外面，也可以定义在外部类的方法体中，如下所示：
  public class Outer
  {
    int out_x  = 0;
    public void method()
    {
      Inner1 inner1 = new Inner1();
      public class Inner2   //在方法体内部定义的内部类
      {
        public method()
        {
          out_x = 3;
        }
      }
      Inner2 inner2 = new Inner2();
    }

    public class Inner1   //在方法体外面定义的内部类
    {
    }

  }
  在方法体外面定义的内部类的访问类型可以是public,protecte,默认的，private等4种类型，这就好像类中定义的成员变量有4种访问类型一样，它们决定这个内部类的定义对其他类是否可见；对于这种情况，我们也可以在外面创建内部类的实例对象，创建内部类的实例对象时，一定要先创建外部类的实例对象，然后用这个外部类的实例对象去创建内部类的实例对象，代码如下：
  Outer outer = new Outer();
  Outer.Inner1 inner1 = outer.new Innner1();

  在方法内部定义的内部类前面不能有访问类型修饰符，就好像方法中定义的局部变量一样，但这种内部类的前面可以使用final或abstract修饰符。这种内部类对其他类是不可见的其他类无法引用这种内部类，但是这种内部类创建的实例对象可以传递给其他类访问。这种内部类必须是先定义，后使用，即内部类的定义代码必须出现在使用该类之前，这与方法中的局部变量必须先定义后使用的道理也是一样的。这种内部类可以访问方法体中的局部变量，但是，该局部变量前必须加final修饰符。
  对于这些细节，只要在eclipse写代码试试，根据开发工具提示的各类错误信息就可以马上了解到。

  在方法体内部还可以采用如下语法来创建一种匿名内部类，即定义某一接口或类的子类的同时，还创建了该子类的实例对象，无需为该子类定义名称：
  public class Outer
  {
    public void start()
    {
      new Thread(
  new Runable(){
          public void run(){};
  }
  ).start();
    }
  }

  最后，在方法外部定义的内部类前面可以加上static关键字，从而成为Static Nested Class，它不再具有内部类的特性，所有，从狭义上讲，它不是内部类。Static Nested Class与普通类在运行时的行为和功能上没有什么区别，只是在编程引用时的语法上有一些差别，它可以定义成public、protected、默认的、private等多种类型，而普通类只能定义成public和默认的这两种类型。在外面引用Static Nested Class类的名称为“外部类名.内部类名”。在外面不需要创建外部类的实例对象，就可以直接创建Static Nested Class，例如，假设Inner是定义在Outer类中的Static Nested Class，那么可以使用如下语句创建Inner类：
  Outer.Inner inner = new Outer.Inner();
  由于static Nested Class不依赖于外部类的实例对象，所以，static Nested Class能访问外部类的非static成员变量。当在外部类中访问Static Nested Class时，可以直接使用Static Nested Class的名字，而不需要加上外部类的名字了，在Static Nested Class中也可以直接引用外部类的static的成员变量，不需要加上外部类的名字。
  在静态方法中定义的内部类也是Static Nested Class，这时候不能在类前面加static关键字，静态方法中的Static Nested Class与普通方法中的内部类的应用方式很相似，它除了可以直接访问外部类中的static的成员变量，还可以访问静态方法中的局部变量，但是，该局部变量前必须加final修饰符。

  备注：首先根据你的印象说出你对内部类的总体方面的特点：例如，在两个地方可以定义，可以访问外部类的成员变量，不能定义静态成员，这是大的特点。然后再说一些细节方面的知识，例如，几种定义方式的语法区别，静态内部类，以及匿名内部类。 
27、内部类可以引用它的包含类的成员吗？有没有什么限制？ 
  完全可以。如果不是静态内部类，那没有什么限制！
  如果你把静态嵌套类当作内部类的一种特例，那在这种情况下不可以访问外部类的普通成员变量，而只能访问外部类中的静态成员，例如，下面的代码：
  class Outer
  {
  static int x;
  static class Inner
  {
    void test()
    {
      syso(x);
    }
  }
  }

  答题时，也要能察言观色，揣摩提问者的心思，显然人家希望你说的是静态内部类不能访问外部类的成员，但你一上来就顶牛，这不好，要先顺着人家，让人家满意，然后再说特殊情况，让人家吃惊。 
28、Anonymous Inner Class (匿名内部类) 是否可以extends(继承)其它类，是否可以implements(实现)interface(接口)?  
  可以继承其他类或实现其他接口。不仅是可以，而是必须! 
29、super.getClass()方法调用 
  下面程序的输出结果是多少？
  import java.util.Date;
  public  class Test extends Date{
  public static void main(String[] args) {
    new Test().test();
  }

  public void test(){
    System.out.println(super.getClass().getName());
  }
  }

  很奇怪，结果是Test
  这属于脑筋急转弯的题目，在一个qq群有个网友正好问过这个问题，我觉得挺有趣，就研究了一下，没想到今天还被你面到了，哈哈。
  在test方法中，直接调用getClass().getName()方法，返回的是Test类名
  由于getClass()在Object类中定义成了final，子类不能覆盖该方法，所以，在
  test方法中调用getClass().getName()方法，其实就是在调用从父类继承的getClass()方法，等效于调用super.getClass().getName()方法，所以，super.getClass().getName()方法返回的也应该是Test。
  如果想得到父类的名称，应该用如下代码：
  getClass().getSuperClass().getName(); 
30、String是最基本的数据类型吗?
  基本数据类型包括byte、int、char、long、float、double、boolean和short。
  java.lang.String类是final类型的，因此不可以继承这个类、不能修改这个类。为了提高效率节省空间，我们应该用StringBuffer类  
31、String s = "Hello";s = s + " world!";这两行代码执行后，原始的String对象中的内容到底变了没有？ 
  没有。因为String被设计成不可变(immutable)类，所以它的所有对象都是不可变对象。在这段代码中，s原先指向一个String对象，内容是 "Hello"，然后我们对s进行了+操作，那么s所指向的那个对象是否发生了改变呢？答案是没有。这时，s不指向原来那个对象了，而指向了另一个 String对象，内容为"Hello world!"，原来那个对象还存在于内存之中，只是s这个引用变量不再指向它了。
  通过上面的说明，我们很容易导出另一个结论，如果经常对字符串进行各种各样的修改，或者说，不可预见的修改，那么使用String来代表字符串的话会引起很大的内存开销。因为 String对象建立之后不能再改变，所以对于每一个不同的字符串，都需要一个String对象来表示。这时，应该考虑使用StringBuffer类，它允许修改，而不是每个不同的字符串都要生成一个新的对象。并且，这两种类的对象转换十分容易。
  同时，我们还可以知道，如果要使用内容相同的字符串，不必每次都new一个String。例如我们要在构造器中对一个名叫s的String引用变量进行初始化，把它设置为初始值，应当这样做：
  public class Demo {
  private String s;
  ...
  public Demo {
  s = "Initial Value";
  }
  ...
  }
  而非
  s = new String("Initial Value");
  后者每次都会调用构造器，生成新对象，性能低下且内存开销大，并且没有意义，因为String对象不可改变，所以对于内容相同的字符串，只要一个String对象来表示就可以了。也就说，多次调用上面的构造器创建多个对象，他们的String类型属性s都指向同一个对象。
  上面的结论还基于这样一个事实：对于字符串常量，如果内容相同，Java认为它们代表同一个String对象。而用关键字new调用构造器，总是会创建一个新的对象，无论内容是否相同。
  至于为什么要把String类设计成不可变类，是它的用途决定的。其实不只String，很多Java标准类库中的类都是不可变的。在开发一个系统的时候，我们有时候也需要设计不可变类，来传递一组相关的值，这也是面向对象思想的体现。不可变类有一些优点，比如因为它的对象是只读的，所以多线程并发访问也不会有任何问题。当然也有一些缺点，比如每个不同的状态都要一个对象来代表，可能会造成性能上的问题。所以Java标准类库还提供了一个可变版本，即 StringBuffer。 
32、是否可以继承String类?
  String类是final类故不可以继承。
 33、String s = new String("xyz");创建了几个String Object? 二者之间有什么区别？
  两个或一个，”xyz”对应一个对象，这个对象放在字符串常量缓冲区，常量”xyz”不管出现多少遍，都是缓冲区中的那一个。New String每写一遍，就创建一个新的对象，它一句那个常量”xyz”对象的内容来创建出一个新String对象。如果以前就用过’xyz’，这句代表就不会创建”xyz”自己了，直接从缓冲区拿。 
34、String 和StringBuffer的区别 
  JAVA平台提供了两个类：String和StringBuffer，它们可以储存和操作字符串，即包含多个字符的字符数据。这个String类提供了数值不可改变的字符串。而这个StringBuffer类提供的字符串进行修改。当你知道字符数据要改变的时候你就可以使用StringBuffer。典型地，你可以使用StringBuffers来动态构造字符数据。另外，String实现了equals方法，new String(“abc”).equals(new String(“abc”)的结果为true,而StringBuffer没有实现equals方法，所以，new StringBuffer(“abc”).equals(new StringBuffer(“abc”)的结果为false。

  接着要举一个具体的例子来说明，我们要把1到100的所有数字拼起来，组成一个串。
  StringBuffer sbf = new StringBuffer();  
  for(int i=0;i<100;i++)
  {
  sbf.append(i);
  }
  上面的代码效率很高，因为只创建了一个StringBuffer对象，而下面的代码效率很低，因为创建了101个对象。
  String str = new String();  
  for(int i=0;i<100;i++)
  {
  str = str + i;
  }
  在讲两者区别时，应把循环的次数搞成10000，然后用endTime-beginTime来比较两者执行的时间差异，最后还要讲讲StringBuilder与StringBuffer的区别。

  String覆盖了equals方法和hashCode方法，而StringBuffer没有覆盖equals方法和hashCode方法，所以，将StringBuffer对象存储进Java集合类中时会出现问题。 
35、如何把一段逗号分割的字符串转换成一个数组?
  如果不查jdk api，我很难写出来！我可以说说我的思路：
  	用正则表达式，代码大概为：String [] result = orgStr.split(“,”);
  	用 StingTokenizer ,代码为：StringTokenizer  tokener = StringTokenizer(orgStr,”,”);
  String [] result = new String[tokener .countTokens()];
  Int i=0;
  while(tokener.hasNext(){result[i++]=toker.nextToken();} 
36、数组有没有length()这个方法? String有没有length()这个方法？  
  数组没有length()这个方法，有length的属性。String有有length()这个方法。 
37、下面这条语句一共创建了多少个对象：String s="a"+"b"+"c"+"d"; 
  答：对于如下代码：
  String s1 = "a";
  String s2 = s1 + "b";
  String s3 = "a" + "b";
  System.out.println(s2 == "ab");
  System.out.println(s3 == "ab");
  第一条语句打印的结果为false，第二条语句打印的结果为true，这说明javac编译可以对字符串常量直接相加的表达式进行优化，不必要等到运行期去进行加法运算处理，而是在编译时去掉其中的加号，直接将其编译成一个这些常量相连的结果。
  题目中的第一行代码被编译器在编译时优化后，相当于直接定义了一个”abcd”的字符串，所以，上面的代码应该只创建了一个String对象。写如下两行代码，
    String s = "a" + "b" + "c" + "d";
    System.out.println(s == "abcd");
  最终打印的结果应该为true。  
38、try {}里有一个return语句，那么紧跟在这个try后的finally {}里的code会不会被执行，什么时候被执行，在return前还是后?  
    也许你的答案是在return之前，但往更细地说，我的答案是在return中间执行，请看下面程序代码的运行结果：
  public  class Test {

  /**
   * @param args add by zxx ,Dec 9, 2008
   */
  public static void main(String[] args) {
    // TODO Auto-generated method stub
    System.out.println(new Test().test());;
  }

  static int test()
  {
    int x = 1;
    try
    {
      return x;
    }
    finally
    {
      ++x;
    }
  }

  }

  ---------执行结果 ---------
  1

  运行结果是1，为什么呢？主函数调用子函数并得到结果的过程，好比主函数准备一个空罐子，当子函数要返回结果时，先把结果放在罐子里，然后再将程序逻辑返回到主函数。所谓返回，就是子函数说，我不运行了，你主函数继续运行吧，这没什么结果可言，结果是在说这话之前放进罐子里的。 
39、下面的程序代码输出的结果是多少？ 
  public class  smallT
  {
  public static void  main(String args[])
  {
    smallT t  = new  smallT();
    int  b  =  t.get();
    System.out.println(b);
  }

  public int  get()
  {
    try
    {
      return 1 ;
    }
    finally
    {
      return 2 ;
    }
  }
  }

  返回的结果是2。
  我可以通过下面一个例子程序来帮助我解释这个答案，从下面例子的运行结果中可以发现，try中的return语句调用的函数先于finally中调用的函数执行，也就是说return语句先执行，finally语句后执行，所以，返回的结果是2。Return并不是让函数马上返回，而是return语句执行后，将把返回结果放置进函数栈中，此时函数并不是马上返回，它要执行finally语句后才真正开始返回。
  在讲解答案时可以用下面的程序来帮助分析：
  public  class Test {

  /**
   * @param args add by zxx ,Dec 9, 2008
   */
  public static void main(String[] args) {
    // TODO Auto-generated method stub
    System.out.println(new Test().test());;
  }

  int test()
  {
    try
    {
      return func1();
    }
    finally
    {
      return func2();
    }
  }

  int func1()
  {
    System.out.println("func1");
    return 1;
  }
  int func2()
  {
    System.out.println("func2");
    return 2;
  }
  }
  -----------执行结果-----------------

  func1
  func2
  2

  结论：finally中的代码比return 和break语句后执行 
40、final, finally, finalize的区别。  
  final 用于声明属性，方法和类，分别表示属性不可变，方法不可覆盖，类不可继承。
  内部类要访问局部变量，局部变量必须定义成final类型，例如，一段代码……
  finally是异常处理语句结构的一部分，表示总是执行。
  finalize是Object类的一个方法，在垃圾收集器执行的时候会调用被回收对象的此方法，可以覆盖此方法提供垃圾收集时的其他资源回收，例如关闭文件等。JVM不保证此方法总被调用 
41、运行时异常与一般异常有何异同？ 
  异常表示程序运行过程中可能出现的非正常状态，运行时异常表示虚拟机的通常操作中可能遇到的异常，是一种常见运行错误。java编译器要求方法必须声明抛出可能发生的非运行时异常，但是并不要求必须声明抛出未被捕获的运行时异常。 
42、error和exception有什么区别?  
  error 表示恢复不是不可能但很困难的情况下的一种严重问题。比如说内存溢出。不可能指望程序能处理这样的情况。 exception 表示一种设计或实现问题。也就是说，它表示如果程序运行正常，从不会发生的情况。  
43、Java中的异常处理机制的简单原理和应用。 
  异常是指java程序运行时（非编译）所发生的非正常情况或错误，与现实生活中的事件很相似，现实生活中的事件可以包含事件发生的时间、地点、人物、情节等信息，可以用一个对象来表示，Java使用面向对象的方式来处理异常，它把程序中发生的每个异常也都分别封装到一个对象来表示的，该对象中包含有异常的信息。
  Java对异常进行了分类，不同类型的异常分别用不同的Java类表示，所有异常的根类为java.lang.Throwable，Throwable下面又派生了两个子类：Error和Exception，Error 表示应用程序本身无法克服和恢复的一种严重问题，程序只有死的份了，例如，说内存溢出和线程死锁等系统问题。Exception表示程序还能够克服和恢复的问题，其中又分为系统异常和普通异常，系统异常是软件本身缺陷所导致的问题，也就是软件开发人员考虑不周所导致的问题，软件使用者无法克服和恢复这种问题，但在这种问题下还可以让软件系统继续运行或者让软件死掉，例如，数组脚本越界（ArrayIndexOutOfBoundsException），空指针异常（NullPointerException）、类转换异常（ClassCastException）；普通异常是运行环境的变化或异常所导致的问题，是用户能够克服的问题，例如，网络断线，硬盘空间不够，发生这样的异常后，程序不应该死掉。
  java为系统异常和普通异常提供了不同的解决方案，编译器强制普通异常必须try..catch处理或用throws声明继续抛给上层调用方法处理，所以普通异常也称为checked异常，而系统异常可以处理也可以不处理，所以，编译器不强制用try..catch处理或用throws声明，所以系统异常也称为unchecked异常。
  提示答题者：就按照三个级别去思考：虚拟机必须宕机的错误，程序可以死掉也可以不死掉的错误，程序不应该死掉的错误； 
44、请写出你最常见到的5个runtime exception。 
  这道题主要考你的代码量到底多大，如果你长期写代码的，应该经常都看到过一些系统方面的异常，你不一定真要回答出5个具体的系统异常，但你要能够说出什么是系统异常，以及几个系统异常就可以了，当然，这些异常完全用其英文名称来写是最好的，如果实在写不出，那就用中文吧，有总比没有强！
  所谓系统异常，就是…..，它们都是RuntimeException的子类，在jdk doc中查RuntimeException类，就可以看到其所有的子类列表，也就是看到了所有的系统异常。我比较有印象的系统异常有：NullPointerException、ArrayIndexOutOfBoundsException、ClassCastException。ArithmeticException - 算术运算中，被0除或模除. NoClassDefFoundException - JAVA运行时系统找不到所引用的类.. OutOfMemoryException - 内存不足，通常发生于创建对象之时 
45、JAVA语言如何进行异常处理，关键字：throws,throw,try,catch,finally分别代表什么意义？在try块中可以抛出异常吗？  
46、java中有几种方法可以实现一个线程？用什么关键字修饰同步方法? stop()和suspend()方法为何不推荐使用？ 
  java5以前，有如下两种：
  第一种：
  new Thread(){}.start();这表示调用Thread子类对象的run方法，new Thread(){}表示一个Thread的匿名子类的实例对象，子类加上run方法后的代码如下：
  new Thread(){
  public void run(){
  }
  }.start();

  第二种：
  new Thread(new Runnable(){}).start();这表示调用Thread对象接受的Runnable对象的run方法，new Runnable(){}表示一个Runnable的匿名子类的实例对象,runnable的子类加上run方法后的代码如下：
  new Thread(new Runnable(){
      public void run(){
      }
    }
  ).start();
  从java5开始，还有如下一些线程池创建多线程的方式：
  ExecutorService pool = Executors.newFixedThreadPool(3)
  for(int i=0;i<10;i++)
  {
  pool.execute(new Runable(){public void run(){}});
  }
  Executors.newCachedThreadPool().execute(new Runable(){public void run(){}});
  Executors.newSingleThreadExecutor().execute(new Runable(){public void run(){}});
  有两种实现方法，分别使用new Thread()和new Thread(runnable)形式，第一种直接调用thread的run方法，所以，我们往往使用Thread子类，即new SubThread()。第二种调用runnable的run方法。
  有两种实现方法，分别是继承Thread类与实现Runnable接口
  用synchronized关键字修饰同步方法
  反对使用stop()，是因为它不安全。它会解除由线程获取的所有锁定，而且如果对象处于一种不连贯状态，那么其他线程能在那种状态下检查和修改它们。结果很难检查出真正的问题所在。suspend()方法容易发生死锁。调用suspend()的时候，目标线程会停下来，但却仍然持有在这之前获得的锁定。此时，其他任何线程都不能访问锁定的资源，除非被"挂起"的线程恢复运行。对任何线程来说，如果它们想恢复目标线程，同时又试图使用任何一个锁定的资源，就会造成死锁。所以不应该使用suspend()，而应在自己的Thread类中置入一个标志，指出线程应该活动还是挂起。若标志指出线程应该挂起，便用wait()命其进入等待状态。若标志指出线程应当恢复，则用一个notify()重新启动线程。  
47、sleep() 和 wait() 有什么区别?  
  （网上的答案：sleep是线程类（Thread）的方法，导致此线程暂停执行指定时间，给执行机会给其他线程，但是监控状态依然保持，到时后会自动恢复。调用sleep不会释放对象锁。 wait是Object类的方法，对此对象调用wait方法导致本线程放弃对象锁，进入等待此对象的等待锁定池，只有针对此对象发出notify方法（或notifyAll）后本线程才进入对象锁定池准备获得对象锁进入运行状态。）

  sleep就是正在执行的线程主动让出cpu，cpu去执行其他线程，在sleep指定的时间过后，cpu才会回到这个线程上继续往下执行，如果当前线程进入了同步锁，sleep方法并不会释放锁，即使当前线程使用sleep方法让出了cpu，但其他被同步锁挡住了的线程也无法得到执行。wait是指在一个已经进入了同步锁的线程内，让自己暂时让出同步锁，以便其他正在等待此锁的线程可以得到同步锁并运行，只有其他线程调用了notify方法（notify并不释放锁，只是告诉调用过wait方法的线程可以去参与获得锁的竞争了，但不是马上得到锁，因为锁还在别人手里，别人还没释放。如果notify方法后面的代码还有很多，需要这些代码执行完后才会释放锁，可以在notfiy方法后增加一个等待和一些代码，看看效果），调用wait方法的线程就会解除wait状态和程序可以再次得到锁后继续向下运行。对于wait的讲解一定要配合例子代码来说明，才显得自己真明白。
  package com.huawei.interview;

  public class MultiThread {

  /**
   * @param args
   */
  public static void main(String[] args) {
    // TODO Auto-generated method stub
    new Thread(new Thread1()).start();
    try {
      Thread.sleep(10);
    } catch (InterruptedException e) {
      // TODO Auto-generated catch block
      e.printStackTrace();
    }
    new Thread(new Thread2()).start();		
  }


  private static class Thread1 implements Runnable
  {

    @Override
    public void run() {
      // TODO Auto-generated method stub
  //由于这里的Thread1和下面的Thread2内部run方法要用同一对象作为监视器，我们这里不能用this，因为在Thread2里面的this和这个Thread1的this不是同一个对象。我们用MultiThread.class这个字节码对象，当前虚拟机里引用这个变量时，指向的都是同一个对象。
      synchronized (MultiThread.class) {

        System.out.println("enter thread1...");

        System.out.println("thread1 is waiting");
        try {
      //释放锁有两种方式，第一种方式是程序自然离开监视器的范围，也就是离开了synchronized关键字管辖的代码范围，另一种方式就是在synchronized关键字管辖的代码内部调用监视器对象的wait方法。这里，使用wait方法释放锁。
          MultiThread.class.wait();
        } catch (InterruptedException e) {
          // TODO Auto-generated catch block
          e.printStackTrace();
        }

        System.out.println("thread1 is going on...");
        System.out.println("thread1 is being over!");			
      }
    }

  }

  private static class Thread2 implements Runnable
  {

    @Override
    public void run() {
      // TODO Auto-generated method stub
      synchronized (MultiThread.class) {

        System.out.println("enter thread2...");

        System.out.println("thread2 notify other thread can release wait status..");
  //由于notify方法并不释放锁， 即使thread2调用下面的sleep方法休息了10毫秒，但thread1仍然不会执行，因为thread2没有释放锁，所以Thread1无法得不到锁。

        MultiThread.class.notify();

        System.out.println("thread2 is sleeping ten millisecond...");
        try {
          Thread.sleep(10);
        } catch (InterruptedException e) {
          // TODO Auto-generated catch block
          e.printStackTrace();
        }

        System.out.println("thread2 is going on...");
        System.out.println("thread2 is being over!");

      }
    }
  }
  } 
48、同步和异步有何异同，在什么情况下分别使用他们？举例说明。  
  如果数据将在线程间共享。例如正在写的数据以后可能被另一个线程读到，或者正在读的数据可能已经被另一个线程写过了，那么这些数据就是共享数据，必须进行同步存取。
  当应用程序在对象上调用了一个需要花费很长时间来执行的方法，并且不希望让程序等待方法的返回时，就应该使用异步编程，在很多情况下采用异步途径往往更有效率。  
49. 下面两个方法同步吗？（自己发明） 
  class Test
  {
  synchronized static void sayHello3()
    {

    }

    synchronized void getX(){}
  } 
50、多线程有几种实现方法?同步有几种实现方法?  
  多线程有两种实现方法，分别是继承Thread类与实现Runnable接口
  同步的实现方面有两种，分别是synchronized,wait与notify
  wait():使一个线程处于等待状态，并且释放所持有的对象的lock。
  sleep():使一个正在运行的线程处于睡眠状态，是一个静态方法，调用此方法要捕捉InterruptedException异常。
  notify():唤醒一个处于等待状态的线程，注意的是在调用此方法的时候，并不能确切的唤醒某一个等待状态的线程，而是由JVM确定唤醒哪个线程，而且不是按优先级。
  Allnotity():唤醒所有处入等待状态的线程，注意并不是给所有唤醒线程一个对象的锁，而是让它们竞争。 
51、启动一个线程是用run()还是start()? .  
  启动一个线程是调用start()方法，使线程就绪状态，以后可以被调度为运行状态，一个线程必须关联一些具体的执行代码，run()方法是该线程所关联的执行代码。  
52、当一个线程进入一个对象的一个synchronized方法后，其它线程是否可进入此对象的其它方法?  
  分几种情况：
   1.其他方法前是否加了synchronized关键字，如果没加，则能。
   2.如果这个方法内部调用了wait，则可以进入其他synchronized方法。
   3.如果其他个方法都加了synchronized关键字，并且内部没有调用wait，则不能。
  4.如果其他方法是static，它用的同步锁是当前类的字节码，与非静态的方法不能同步，因为非静态的方法用的是this。
 53、线程的基本概念、线程的基本状态以及状态之间的关系  
  一个程序中可以有多条执行线索同时执行，一个线程就是程序中的一条执行线索，每个线程上都关联有要执行的代码，即可以有多段程序代码同时运行，每个程序至少都有一个线程，即main方法执行的那个线程。如果只是一个cpu，它怎么能够同时执行多段程序呢？这是从宏观上来看的，cpu一会执行a线索，一会执行b线索，切换时间很快，给人的感觉是a,b在同时执行，好比大家在同一个办公室上网，只有一条链接到外部网线，其实，这条网线一会为a传数据，一会为b传数据，由于切换时间很短暂，所以，大家感觉都在同时上网。
  状态：就绪，运行，synchronize阻塞，wait和sleep挂起，结束。wait必须在synchronized内部调用。
  调用线程的start方法后线程进入就绪状态，线程调度系统将就绪状态的线程转为运行状态，遇到synchronized语句时，由运行状态转为阻塞，当synchronized获得锁后，由阻塞转为运行，在这种情况可以调用wait方法转为挂起状态，当线程关联的代码执行完后，线程变为结束状态。  
54、简述synchronized和java.util.concurrent.locks.Lock的异同 ？  
  主要相同点：Lock能完成synchronized所实现的所有功能
  主要不同点：Lock有比synchronized更精确的线程语义和更好的性能。synchronized会自动释放锁，而Lock一定要求程序员手工释放，并且必须在finally从句中释放。Lock还有更强大的功能，例如，它的tryLock方法可以非阻塞方式去拿锁。
  举例说明（对下面的题用lock进行了改写）：
  package com.huawei.interview;

  import java.util.concurrent.locks.Lock;
  import java.util.concurrent.locks.ReentrantLock;

  public class ThreadTest {

  /**
   * @param args
   */

  private int j;
  private Lock lock = new ReentrantLock();
  public static void main(String[] args) {
    // TODO Auto-generated method stub
    ThreadTest tt = new ThreadTest();
    for(int i=0;i<2;i++)
    {
      new Thread(tt.new Adder()).start();
      new Thread(tt.new Subtractor()).start();
    }
  }

  private class Subtractor implements Runnable
  {

    @Override
    public void run() {
      // TODO Auto-generated method stub
      while(true)
      {
        /*synchronized (ThreadTest.this) {			
          System.out.println("j--=" + j--);
          //这里抛异常了，锁能释放吗？
        }*/
        lock.lock();
        try
        {
          System.out.println("j--=" + j--);
        }finally
        {
          lock.unlock();
        }
      }
    }

  }

  private class Adder implements Runnable
  {

    @Override
    public void run() {
      // TODO Auto-generated method stub
      while(true)
      {
        /*synchronized (ThreadTest.this) {
        System.out.println("j++=" + j++);
        }*/
        lock.lock();
        try
        {
          System.out.println("j++=" + j++);
        }finally
        {
          lock.unlock();
        }				
      }			
    }

  }
  } 
55、设计4个线程，其中两个线程每次对j增加1，另外两个线程对j每次减少1。写出程序。  
  以下程序使用内部类实现线程，对j增减的时候没有考虑顺序问题。
  public class ThreadTest1
  {
  private int j;
  public static void main(String args[]){
   ThreadTest1 tt=new ThreadTest1();
   Inc inc=tt.new Inc();
   Dec dec=tt.new Dec();
   for(int i=0;i<2;i++){
       Thread t=new Thread(inc);
       t.start();
       t=new Thread(dec);
       t.start();
       }
   }
  private synchronized void inc(){
   j++;
   System.out.println(Thread.currentThread().getName()+"-inc:"+j);
   }
  private synchronized void dec(){
   j--;
   System.out.println(Thread.currentThread().getName()+"-dec:"+j);
   }
  class Inc implements Runnable{
   public void run(){
       for(int i=0;i<100;i++){
       inc();
       }
   }
  }
  class Dec implements Runnable{
   public void run(){
       for(int i=0;i<100;i++){
       dec();
       }
   }
  }
  }

  ----------随手再写的一个-------------
  class A
  {
  JManger j =new JManager();
  main()
  {
  new A().call();
  }

  void call
  {
  for(int i=0;i<2;i++)
  {
    new Thread(
      new Runnable(){ public void run(){while(true){j.accumulate()}}}
    ).start();
    new Thread(new Runnable(){ public void run(){while(true){j.sub()}}}).start();
  }
  }
  }

  class JManager
  {
  private j = 0;

  public synchronized void subtract()
  {
    j--
  }

  public synchronized void accumulate()
  {
    j++;
  }

  } 
56、子线程循环10次，接着主线程循环100，接着又回到子线程循环10次，接着再回到主线程又循环100，如此循环50次，请写出程序。  
  最终的程序代码如下：
  public class ThreadTest {

  /**
   * @param args
   */
  public static void main(String[] args) {
    // TODO Auto-generated method stub
    new ThreadTest().init();

  }

  public void init()
  {
    final Business business = new Business();
    new Thread(
        new Runnable()
        {

          public void run() {
            for(int i=0;i<50;i++)
            {
              business.SubThread(i);
            }						
          }

        }

    ).start();

    for(int i=0;i<50;i++)
    {
      business.MainThread(i);
    }		
  }

  private class Business
  {
    boolean bShouldSub = true;//这里相当于定义了控制该谁执行的一个信号灯
    public synchronized void MainThread(int i)
    {
      if(bShouldSub)
        try {
          this.wait();
        } catch (InterruptedException e) {
          // TODO Auto-generated catch block
          e.printStackTrace();
        }		

      for(int j=0;j<5;j++)
      {
        System.out.println(Thread.currentThread().getName() + ":i=" + i +",j=" + j);
      }
      bShouldSub = true;
      this.notify();

    }


    public synchronized void SubThread(int i)
    {
      if(!bShouldSub)
        try {
          this.wait();
        } catch (InterruptedException e) {
          // TODO Auto-generated catch block
          e.printStackTrace();
        }

      for(int j=0;j<10;j++)
      {
        System.out.println(Thread.currentThread().getName() + ":i=" + i +",j=" + j);
      }
      bShouldSub = false;				
      this.notify();			
    }
  }
  }

  备注：不可能一上来就写出上面的完整代码，最初写出来的代码如下，问题在于两个线程的代码要参照同一个变量，即这两个线程的代码要共享数据，所以，把这两个线程的执行代码搬到同一个类中去：

  package com.huawei.interview.lym;

  public class ThreadTest {

  private static boolean bShouldMain = false;

  public static void main(String[] args) {
    // TODO Auto-generated method stub
    /*new Thread(){
    public void run()
    {
      for(int i=0;i<50;i++)
      {
        for(int j=0;j<10;j++)
        {
          System.out.println("i=" + i + ",j=" + j);
        }
      }				
    }

  }.start();*/		


    //final String str = new String("");

    new Thread(
        new Runnable()
        {
          public void run()
          {
            for(int i=0;i<50;i++)
            {
              synchronized (ThreadTest.class) {
                if(bShouldMain)
                {
                  try {
                    ThreadTest.class.wait();}
                  catch (InterruptedException e) {
                    e.printStackTrace();
                  }
                }
                for(int j=0;j<10;j++)
                {
                  System.out.println(
                      Thread.currentThread().getName() +
                      "i=" + i + ",j=" + j);
                }
                bShouldMain = true;
                ThreadTest.class.notify();
              }							
            }						
          }
        }
    ).start();

    for(int i=0;i<50;i++)
    {
      synchronized (ThreadTest.class) {
        if(!bShouldMain)
        {
          try {
            ThreadTest.class.wait();}
          catch (InterruptedException e) {
            e.printStackTrace();
          }
        }				
        for(int j=0;j<5;j++)
        {
          System.out.println(
              Thread.currentThread().getName() + 						
              "i=" + i + ",j=" + j);
        }
        bShouldMain = false;
        ThreadTest.class.notify();				
      }			
    }
  }

  }
  下面使用jdk5中的并发库来实现的：
  import java.util.concurrent.Executors;
  import java.util.concurrent.ExecutorService;
  import java.util.concurrent.locks.Lock;
  import java.util.concurrent.locks.ReentrantLock;
  import java.util.concurrent.locks.Condition;

  public class ThreadTest
  {
  private static Lock lock = new ReentrantLock();
  private static Condition subThreadCondition = lock.newCondition();
  private static boolean bBhouldSubThread = false;
  public static void main(String [] args)
  {
    ExecutorService threadPool = Executors.newFixedThreadPool(3);
    threadPool.execute(new Runnable(){
      public void run()
      {
        for(int i=0;i<50;i++)
        {
          lock.lock();					
          try
          {					
            if(!bBhouldSubThread)
              subThreadCondition.await();
            for(int j=0;j<10;j++)
            {
              System.out.println(Thread.currentThread().getName() + ",j=" + j);
            }
            bBhouldSubThread = false;
            subThreadCondition.signal();
          }catch(Exception e)
          {						
          }
          finally
          {
            lock.unlock();
          }
        }			
      }

    });
    threadPool.shutdown();
    for(int i=0;i<50;i++)
    {
        lock.lock();					
        try
        {
          if(bBhouldSubThread)
              subThreadCondition.await();								
          for(int j=0;j<10;j++)
          {
            System.out.println(Thread.currentThread().getName() + ",j=" + j);
          }
          bBhouldSubThread = true;
          subThreadCondition.signal();					
        }catch(Exception e)
        {						
        }
        finally
        {
          lock.unlock();
        }					
    }
  }
  } 
57、介绍Collection框架的结构 
  答：随意发挥题，天南海北谁便谈，只要让别觉得你知识渊博，理解透彻即可。 
58、Collection框架中实现比较要实现什么接口 
  comparable/comparator 
59、ArrayList和Vector的区别 
  答：
  这两个类都实现了List接口（List接口继承了Collection接口），他们都是有序集合，即存储在这两个集合中的元素的位置都是有顺序的，相当于一种动态的数组，我们以后可以按位置索引号取出某个元素，，并且其中的数据是允许重复的，这是HashSet之类的集合的最大不同处，HashSet之类的集合不可以按索引号去检索其中的元素，也不允许有重复的元素（本来题目问的与hashset没有任何关系，但为了说清楚ArrayList与Vector的功能，我们使用对比方式，更有利于说明问题）。

  接着才说ArrayList与Vector的区别，这主要包括两个方面：.
  （1）同步性：
  Vector是线程安全的，也就是说是它的方法之间是线程同步的，而ArrayList是线程序不安全的，它的方法之间是线程不同步的。如果只有一个线程会访问到集合，那最好是使用ArrayList，因为它不考虑线程安全，效率会高些；如果有多个线程会访问到集合，那最好是使用Vector，因为不需要我们自己再去考虑和编写线程安全的代码。

  备注：对于Vector&ArrayList、Hashtable&HashMap，要记住线程安全的问题，记住Vector与Hashtable是旧的，是java一诞生就提供了的，它们是线程安全的，ArrayList与HashMap是java2时才提供的，它们是线程不安全的。所以，我们讲课时先讲老的。
  （2）数据增长：
  ArrayList与Vector都有一个初始的容量大小，当存储进它们里面的元素的个数超过了容量时，就需要增加ArrayList与Vector的存储空间，每次要增加存储空间时，不是只增加一个存储单元，而是增加多个存储单元，每次增加的存储单元的个数在内存空间利用与程序效率之间要取得一定的平衡。Vector默认增长为原来两倍，而ArrayList的增长策略在文档中没有明确规定（从源代码看到的是增长为原来的1.5倍）。ArrayList与Vector都可以设置初始的空间大小，Vector还可以设置增长的空间大小，而ArrayList没有提供设置增长空间的方法。
    总结：即Vector增长原来的一倍，ArrayList增加原来的0.5倍。 
60、HashMap和Hashtable的区别 
  （条理上还需要整理，也是先说相同点，再说不同点）
  HashMap是Hashtable的轻量级实现（非线程安全的实现），他们都完成了Map接口，主要区别在于HashMap允许空（null）键值（key）,由于非线程安全，在只有一个线程访问的情况下，效率要高于Hashtable。
  HashMap允许将null作为一个entry的key或者value，而Hashtable不允许。
  HashMap把Hashtable的contains方法去掉了，改成containsvalue和containsKey。因为contains方法容易让人引起误解。
  Hashtable继承自Dictionary类，而HashMap是Java1.2引进的Map interface的一个实现。
  最大的不同是，Hashtable的方法是Synchronize的，而HashMap不是，在多个线程访问Hashtable时，不需要自己为它的方法实现同步，而HashMap 就必须为之提供外同步。
  Hashtable和HashMap采用的hash/rehash算法都大概一样，所以性能不会有很大的差异。

  就HashMap与HashTable主要从三方面来说。
  一.历史原因:Hashtable是基于陈旧的Dictionary类的，HashMap是Java 1.2引进的Map接口的一个实现
  二.同步性:Hashtable是线程安全的，也就是说是同步的，而HashMap是线程序不安全的，不是同步的
  三.值：只有HashMap可以让你将空值作为一个表的条目的key或value  
61、List 和 Map 区别? 
  一个是存储单列数据的集合，另一个是存储键和值这样的双列数据的集合，List中存储的数据是有顺序，并且允许重复；Map中存储的数据是没有顺序的，其键是不能重复的，它的值是可以有重复的。 
62、List, Set, Map是否继承自Collection接口?  
  List，Set是，Map不是  
63、List、Map、Set三个接口，存取元素时，各有什么特点？  
  这样的题属于随意发挥题：这样的题比较考水平，两个方面的水平：一是要真正明白这些内容，二是要有较强的总结和表述能力。如果你明白，但表述不清楚，在别人那里则等同于不明白。

  首先，List与Set具有相似性，它们都是单列元素的集合，所以，它们有一个功共同的父接口，叫Collection。Set里面不允许有重复的元素，所谓重复，即不能有两个相等（注意，不是仅仅是相同）的对象 ，即假设Set集合中有了一个A对象，现在我要向Set集合再存入一个B对象，但B对象与A对象equals相等，则B对象存储不进去，所以，Set集合的add方法有一个boolean的返回值，当集合中没有某个元素，此时add方法可成功加入该元素时，则返回true，当集合含有与某个元素equals相等的元素时，此时add方法无法加入该元素，返回结果为false。Set取元素时，没法说取第几个，只能以Iterator接口取得所有的元素，再逐一遍历各个元素。
  List表示有先后顺序的集合， 注意，不是那种按年龄、按大小、按价格之类的排序。当我们多次调用add(Obj e)方法时，每次加入的对象就像火车站买票有排队顺序一样，按先来后到的顺序排序。有时候，也可以插队，即调用add(int index,Obj e)方法，就可以指定当前对象在集合中的存放位置。一个对象可以被反复存储进List中，每调用一次add方法，这个对象就被插入进集合中一次，其实，并不是把这个对象本身存储进了集合中，而是在集合中用一个索引变量指向这个对象，当这个对象被add多次时，即相当于集合中有多个索引指向了这个对象，如图x所示。List除了可以以Iterator接口取得所有的元素，再逐一遍历各个元素之外，还可以调用get(index i)来明确说明取第几个。
  Map与List和Set不同，它是双列的集合，其中有put方法，定义如下：put(obj key,obj value)，每次存储时，要存储一对key/value，不能存储重复的key，这个重复的规则也是按equals比较相等。取则可以根据key获得相应的value，即get(Object key)返回值为key 所对应的value。另外，也可以获得所有的key的结合，还可以获得所有的value的结合，还可以获得key和value组合成的Map.Entry对象的集合。

  List 以特定次序来持有元素，可有重复元素。Set 无法拥有重复元素,内部排序。Map 保存key-value值，value可多值。


  HashSet按照hashcode值的某种运算方式进行存储，而不是直接按hashCode值的大小进行存储。例如，"abc" ---> 78，"def" ---> 62，"xyz" ---> 65在hashSet中的存储顺序不是62,65,78，这些问题感谢以前一个叫崔健的学员提出，最后通过查看源代码给他解释清楚，看本次培训学员当中有多少能看懂源码。LinkedHashSet按插入的顺序存储，那被存储对象的hashcode方法还有什么作用呢？学员想想!hashset集合比较两个对象是否相等，首先看hashcode方法是否相等，然后看equals方法是否相等。new 两个Student插入到HashSet中，看HashSet的size，实现hashcode和equals方法后再看size。

  同一个对象可以在Vector中加入多次。往集合里面加元素，相当于集合里用一根绳子连接到了目标对象。往HashSet中却加不了多次的。  
64、说出ArrayList,Vector, LinkedList的存储性能和特性  
  ArrayList和Vector都是使用数组方式存储数据，此数组元素数大于实际存储的数据以便增加和插入元素，它们都允许直接按序号索引元素，但是插入元素要涉及数组元素移动等内存操作，所以索引数据快而插入数据慢，Vector由于使用了synchronized方法（线程安全），通常性能上较ArrayList差，而LinkedList使用双向链表实现存储，按序号索引数据需要进行前向或后向遍历，但是插入数据时只需要记录本项的前后项即可，所以插入速度较快。
  LinkedList也是线程不安全的，LinkedList提供了一些方法，使得LinkedList可以被当作堆栈和队列来使用。 
65、去掉一个Vector集合中重复的元素  
  Vector newVector = new Vector();
  For (int i=0;i<vector.size();i++)
  {
  Object obj = vector.get(i);
  if(!newVector.contains(obj);
    newVector.add(obj);
  }
  还有一种简单的方式，HashSet set = new HashSet(vector);  
66. Collection 和 Collections的区别。  
  Collection是集合类的上级接口，继承与他的接口主要有Set 和List.
  Collections是针对集合类的一个帮助类，他提供一系列静态方法实现对各种集合的搜索、排序、线程安全化等操作。
67. Set里的元素是不能重复的，那么用什么方法来区分重复与否呢? 是用==还是equals()? 它们有何区别?  
   Set里的元素是不能重复的，元素重复与否是使用equals()方法进行判断的。
   equals()和==方法决定引用值是否指向同一对象equals()在类中被覆盖，为的是当两个分离的对象的内容和类型相配的话，返回真值。 
68、你所知道的集合类都有哪些？主要方法？ 
  最常用的集合类是 List 和 Map。 List 的具体实现包括 ArrayList 和 Vector，它们是可变大小的列表，比较适合构建、存储和操作任何类型对象的元素列表。 List 适用于按数值索引访问元素的情形。
  Map 提供了一个更通用的元素存储方法。 Map 集合类用于存储元素对（称作"键"和"值"），其中每个键映射到一个值。

  ArrayList/VectorList
                    Collection
  HashSet/TreeSetSet

  PropetiesHashTable
          Map
  Treemap/HashMap

  我记的不是方法名，而是思想，我知道它们都有增删改查的方法，但这些方法的具体名称，我记得不是很清楚，对于set，大概的方法是add,remove, contains；对于map，大概的方法就是put,remove，contains等，因为，我只要在eclispe下按点操作符，很自然的这些方法就出来了。我记住的一些思想就是List类会有get(int index)这样的方法，因为它可以按顺序取元素，而set类中没有get(int index)这样的方法。List和set都可以迭代出所有元素，迭代时先要得到一个iterator对象，所以，set和list类都有一个iterator方法，用于返回那个iterator对象。map可以返回三个集合，一个是返回所有的key的集合，另外一个返回的是所有value的集合，再一个返回的key和value组合成的EntrySet对象的集合，map也有get方法，参数是key，返回值是key对应的value。  
69. 两个对象值相同(x.equals(y) == true)，但却可有不同的hash code，这句话对不对?  
  对。
  如果对象要保存在HashSet或HashMap中，它们的equals相等，那么，它们的hashcode值就必须相等。
  如果不是要保存在HashSet或HashMap，则与hashcode没有什么关系了，这时候hashcode不等是可以的，例如arrayList存储的对象就不用实现hashcode，当然，我们没有理由不实现，通常都会去实现的。 
70、TreeSet里面放对象，如果同时放入了父类和子类的实例对象，那比较时使用的是父类的compareTo方法，还是使用的子类的compareTo方法，还是抛异常！ 
  （应该是没有针对问题的确切的答案，当前的add方法放入的是哪个对象，就调用哪个对象的compareTo方法，至于这个compareTo方法怎么做，就看当前这个对象的类中是如何编写这个方法的）
  实验代码：
  public class Parent implements Comparable {
  private int age = 0;
  public Parent(int age){
    this.age = age;
  }
  public int compareTo(Object o) {
    // TODO Auto-generated method stub
    System.out.println("method of parent");
    Parent o1 = (Parent)o;
    return age>o1.age?1:age<o1.age?-1:0;
  }

  }

  public class Child extends Parent {

  public Child(){
    super(3);
  }
  public int compareTo(Object o) {

      // TODO Auto-generated method stub
      System.out.println("method of child");
  //			Child o1 = (Child)o;
      return 1;

  }
  }

  public class TreeSetTest {

  /**
   * @param args
   */
  public static void main(String[] args) {
    // TODO Auto-generated method stub
    TreeSet set = new TreeSet();
    set.add(new Parent(3));
    set.add(new Child());
    set.add(new Parent(4));
    System.out.println(set.size());
  }

  } 
71、说出一些常用的类，包，接口，请各举5个
  要让人家感觉你对java ee开发很熟，所以，不能仅仅只列core java中的那些东西，要多列你在做ssh项目中涉及的那些东西。就写你最近写的那些程序中涉及的那些类。
  常用的类：BufferedReader  BufferedWriter  FileReader  FileWirter  String  Integer
  java.util.Date，System，Class，List,HashMap
  常用的包：java.lang   java.io  java.util  java.sql ,javax.servlet,org.apache.strtuts.action,org.hibernate
  常用的接口：Remote  List  Map  Document  NodeList ,Servlet,HttpServletRequest,HttpServletResponse,Transaction(Hibernate)、Session(Hibernate),HttpSession 
72. java中有几种类型的流？JDK为每种类型的流提供了一些抽象类以供继承，请说出他们分别是哪些类？ 
  字节流，字符流。字节流继承于InputStream OutputStream，字符流继承于InputStreamReader OutputStreamWriter。在java.io包中还有许多其他的流，主要是为了提高性能和使用方便。 
73. 字节流与字符流的区别 
  要把一片二进制数据数据逐一输出到某个设备中，或者从某个设备中逐一读取一片二进制数据，不管输入输出设备是什么，我们要用统一的方式来完成这些操作，用一种抽象的方式进行描述，这个抽象描述方式起名为IO流，对应的抽象类为OutputStream和InputStream ，不同的实现类就代表不同的输入和输出设备，它们都是针对字节进行操作的。
  在应用中，经常要完全是字符的一段文本输出去或读进来，用字节流可以吗？计算机中的一切最终都是二进制的字节形式存在。对于“中国”这些字符，首先要得到其对应的字节，然后将字节写入到输出流。读取时，首先读到的是字节，可是我们要把它显示为字符，我们需要将字节转换成字符。由于这样的需求很广泛，人家专门提供了字符流的包装类。
  底层设备永远只接受字节数据，有时候要写字符串到底层设备，需要将字符串转成字节再进行写入。字符流是字节流的包装，字符流则是直接接受字符串，它内部将串转成字节，再写入底层设备，这为我们向IO设别写入或读取字符串提供了一点点方便。
  字符向字节转换时，要注意编码的问题，因为字符串转成字节数组，
  其实是转成该字符的某种编码的字节形式，读取也是反之的道理。

  讲解字节流与字符流关系的代码案例：
  import java.io.BufferedReader;
  import java.io.FileInputStream;
  import java.io.FileOutputStream;
  import java.io.FileReader;
  import java.io.FileWriter;
  import java.io.InputStreamReader;
  import java.io.PrintWriter;

  public class IOTest {
  public static void main(String[] args) throws Exception {
    String str = "中国人";
    /*FileOutputStream fos  = new FileOutputStream("1.txt");

    fos.write(str.getBytes("UTF-8"));
    fos.close();*/

    /*FileWriter fw = new FileWriter("1.txt");
    fw.write(str);
    fw.close();*/
    PrintWriter pw = new PrintWriter("1.txt","utf-8");
    pw.write(str);
    pw.close();

    /*FileReader fr = new FileReader("1.txt");
    char[] buf = new char[1024];
    int len = fr.read(buf);
    String myStr = new String(buf,0,len);
    System.out.println(myStr);*/
    /*FileInputStream fr = new FileInputStream("1.txt");
    byte[] buf = new byte[1024];
    int len = fr.read(buf);
    String myStr = new String(buf,0,len,"UTF-8");
    System.out.println(myStr);*/
    BufferedReader br = new BufferedReader(
        new InputStreamReader(
          new FileInputStream("1.txt"),"UTF-8"
          )
        );
    String myStr = br.readLine();
    br.close();
    System.out.println(myStr);
  }
  }
74. 什么是java序列化，如何实现java序列化？或者请解释Serializable接口的作用。 
  我们有时候将一个java对象变成字节流的形式传出去或者从一个字节流中恢复成一个java对象，例如，要将java对象存储到硬盘或者传送给网络上的其他计算机，这个过程我们可以自己写代码去把一个java对象变成某个格式的字节流再传输，但是，jre本身就提供了这种支持，我们可以调用OutputStream的writeObject方法来做，如果要让java 帮我们做，要被传输的对象必须实现serializable接口，这样，javac编译时就会进行特殊处理，编译的类才可以被writeObject方法操作，这就是所谓的序列化。需要被序列化的类必须实现Serializable接口，该接口是一个mini接口，其中没有需要实现的方法，implements Serializable只是为了标注该对象是可被序列化的。


  例如，在web开发中，如果对象被保存在了Session中，tomcat在重启时要把Session对象序列化到硬盘，这个对象就必须实现Serializable接口。如果对象要经过分布式系统进行网络传输或通过rmi等远程调用，这就需要在网络上传输对象，被传输的对象就必须实现Serializable接口。 
75. 描述一下JVM加载class文件的原理机制? 
  JVM中类的装载是由ClassLoader和它的子类来实现的,Java ClassLoader 是一个重要的Java运行时系统组件。它负责在运行时查找和装入类文件的类。  
76. heap和stack有什么区别。  
  java的内存分为两类，一类是栈内存，一类是堆内存。栈内存是指程序进入一个方法时，会为这个方法单独分配一块私属存储空间，用于存储这个方法内部的局部变量，当这个方法结束时，分配给这个方法的栈会释放，这个栈中的变量也将随之释放。
  堆是与栈作用不同的内存，一般用于存放不放在当前方法栈中的那些数据，例如，使用new创建的对象都放在堆里，所以，它不会随方法的结束而消失。方法中的局部变量使用final修饰后，放在堆中，而不是栈中。 
77. GC是什么? 为什么要有GC?  
  GC是垃圾收集的意思（Gabage Collection）,内存处理是编程人员容易出现问题的地方，忘记或者错误的内存回收会导致程序或系统的不稳定甚至崩溃，Java提供的GC功能可以自动监测对象是否超过作用域从而达到自动回收内存的目的，Java语言没有提供释放已分配内存的显示操作方法。 
78. 垃圾回收的优点和原理。并考虑2种回收机制。 
  Java语言中一个显著的特点就是引入了垃圾回收机制，使c++程序员最头疼的内存管理的问题迎刃而解，它使得Java程序员在编写程序的时候不再需要考虑内存管理。由于有个垃圾回收机制，Java中的对象不再有"作用域"的概念，只有对象的引用才有"作用域"。垃圾回收可以有效的防止内存泄露，有效的使用可以使用的内存。垃圾回收器通常是作为一个单独的低级别的线程运行，不可预知的情况下对内存堆中已经死亡的或者长时间没有使用的对象进行清楚和回收，程序员不能实时的调用垃圾回收器对某个对象或所有对象进行垃圾回收。回收机制有分代复制垃圾回收和标记垃圾回收，增量垃圾回收。 
79. 垃圾回收器的基本原理是什么？垃圾回收器可以马上回收内存吗？有什么办法主动通知虚拟机进行垃圾回收？  
  对于GC来说，当程序员创建对象时，GC就开始监控这个对象的地址、大小以及使用情况。通常，GC采用有向图的方式记录和管理堆(heap)中的所有对象。通过这种方式确定哪些对象是"可达的"，哪些对象是"不可达的"。当GC确定一些对象为"不可达"时，GC就有责任回收这些内存空间。可以。程序员可以手动执行System.gc()，通知GC运行，但是Java语言规范并不保证GC一定会执行。  
80、什么时候用assert。  
  assertion(断言)在软件开发中是一种常用的调试方式，很多开发语言中都支持这种机制。在实现中，assertion就是在程序中的一条语句，它对一个boolean表达式进行检查，一个正确程序必须保证这个boolean表达式的值为true；如果该值为false，说明程序已经处于不正确的状态下，assert将给出警告或退出。一般来说，assertion用于保证程序最基本、关键的正确性。assertion检查通常在开发和测试时开启。为了提高性能，在软件发布后，assertion检查通常是关闭的。
  package com.huawei.interview;

  public class AssertTest {

  /**
   * @param args
   */
  public static void main(String[] args) {
    // TODO Auto-generated method stub
    int i = 0;
    for(i=0;i<5;i++)
    {
      System.out.println(i);
    }
    //假设程序不小心多了一句--i;
    --i;
    assert i==5;		
  }
  }
81. java中会存在内存泄漏吗，请简单描述。 
  所谓内存泄露就是指一个不再被程序使用的对象或变量一直被占据在内存中。java中有垃圾回收机制，它可以保证一对象不再被引用的时候，即对象编程了孤儿的时候，对象将自动被垃圾回收器从内存中清除掉。由于Java 使用有向图的方式进行垃圾回收管理，可以消除引用循环的问题，例如有两个对象，相互引用，只要它们和根进程不可达的，那么GC也是可以回收它们的，例如下面的代码可以看到这种情况的内存回收：
  package com.huawei.interview;

  import java.io.IOException;

  public class GarbageTest {

  /**
   * @param args
   * @throws IOException
   */
  public static void main(String[] args) throws IOException {
    // TODO Auto-generated method stub
    try {
      gcTest();
    } catch (IOException e) {
      // TODO Auto-generated catch block
      e.printStackTrace();
    }
    System.out.println("has exited gcTest!");
    System.in.read();
    System.in.read();		
    System.out.println("out begin gc!");		
    for(int i=0;i<100;i++)
    {
      System.gc();
      System.in.read();
      System.in.read();
    }
  }

  private static void gcTest() throws IOException {
    System.in.read();
    System.in.read();		
    Person p1 = new Person();
    System.in.read();
    System.in.read();		
    Person p2 = new Person();
    p1.setMate(p2);
    p2.setMate(p1);
    System.out.println("before exit gctest!");
    System.in.read();
    System.in.read();		
    System.gc();
    System.out.println("exit gctest!");
  }

  private static class Person
  {
    byte[] data = new byte[20000000];
    Person mate = null;
    public void setMate(Person other)
    {
      mate = other;
    }
  }
  }

  java中的内存泄露的情况：长生命周期的对象持有短生命周期对象的引用就很可能发生内存泄露，尽管短生命周期对象已经不再需要，但是因为长生命周期对象持有它的引用而导致不能被回收，这就是java中内存泄露的发生场景，通俗地说，就是程序员可能创建了一个对象，以后一直不再使用这个对象，这个对象却一直被引用，即这个对象无用但是却无法被垃圾回收器回收的，这就是java中可能出现内存泄露的情况，例如，缓存系统，我们加载了一个对象放在缓存中(例如放在一个全局map对象中)，然后一直不再使用它，这个对象一直被缓存引用，但却不再被使用。
  检查java中的内存泄露，一定要让程序将各种分支情况都完整执行到程序结束，然后看某个对象是否被使用过，如果没有，则才能判定这个对象属于内存泄露。

  如果一个外部类的实例对象的方法返回了一个内部类的实例对象，这个内部类对象被长期引用了，即使那个外部类实例对象不再被使用，但由于内部类持久外部类的实例对象，这个外部类对象将不会被垃圾回收，这也会造成内存泄露。

  下面内容来自于网上（主要特点就是清空堆栈中的某个元素，并不是彻底把它从数组中拿掉，而是把存储的总数减少，本人写得可以比这个好，在拿掉某个元素时，顺便也让它从数组中消失，将那个元素所在的位置的值设置为null即可）：

  我实在想不到比那个堆栈更经典的例子了,以致于我还要引用别人的例子，下面的例子不是我想到的，是书上看到的，当然如果没有在书上看到，可能过一段时间我自己也想的到，可是那时我说是我自己想到的也没有人相信的。


      public class Stack {
      private Object[] elements=new Object[10];
      private int size = 0;
      public void push(Object e){
      ensureCapacity();
      elements[size++] = e;
      }
      public Object pop(){
      if( size == 0)


      throw new EmptyStackException();
      return elements[--size];
      }
      private void ensureCapacity(){
      if(elements.length == size){
      Object[] oldElements = elements;
      elements = new Object[2 * elements.length+1];
      System.arraycopy(oldElements,0, elements, 0, size);
      }
      }
      }
      上面的原理应该很简单，假如堆栈加了10个元素，然后全部弹出来，虽然堆栈是空的，没有我们要的东西，但是这是个对象是无法回收的，这个才符合了内存泄露的两个条件：无用，无法回收。


      但是就是存在这样的东西也不一定会导致什么样的后果，如果这个堆栈用的比较少，也就浪费了几个K内存而已，反正我们的内存都上G了，哪里会有什么影响，再说这个东西很快就会被回收的，有什么关系。下面看两个例子。


      例子1
      public class Bad{
      public static Stack s=Stack();
      static{
      s.push(new Object());
      s.pop(); //这里有一个对象发生内存泄露
      s.push(new Object()); //上面的对象可以被回收了，等于是自愈了
      }
      }
      因为是static，就一直存在到程序退出，但是我们也可以看到它有自愈功能，就是说如果你的Stack最多有100个对象，那么最多也就只有100个对象无法被回收其实这个应该很容易理解，Stack内部持有100个引用，最坏的情况就是他们都是无用的，因为我们一旦放新的进取，以前的引用自然消失！


  内存泄露的另外一种情况：当一个对象被存储进HashSet集合中以后，就不能修改这个对象中的那些参与计算哈希值的字段了，否则，对象修改后的哈希值与最初存储进HashSet集合中时的哈希值就不同了，在这种情况下，即使在contains方法使用该对象的当前引用作为的参数去HashSet集合中检索对象，也将返回找不到对象的结果，这也会导致无法从HashSet集合中单独删除当前对象，造成内存泄露。  
82. 能不能自己写个类，也叫java.lang.String？ 
  可以，但在应用的时候，需要用自己的类加载器去加载，否则，系统的类加载器永远只是去加载jre.jar包中的那个java.lang.String。由于在tomcat的web应用程序中，都是由webapp自己的类加载器先自己加载WEB-INF/classess目录中的类，然后才委托上级的类加载器加载，如果我们在tomcat的web应用程序中写一个java.lang.String，这时候Servlet程序加载的就是我们自己写的java.lang.String，但是这么干就会出很多潜在的问题，原来所有用了java.lang.String类的都将出现问题。

  虽然java提供了endorsed技术，可以覆盖jdk中的某些类，具体做法是….。但是，能够被覆盖的类是有限制范围，反正不包括java.lang这样的包中的类。

  （下面的例如主要是便于大家学习理解只用，不要作为答案的一部分，否则，人家怀疑是题目泄露了）例如，运行下面的程序：
  package java.lang;

  public class String {

  /**
   * @param args
   */
  public static void main(String[] args) {
    // TODO Auto-generated method stub
    System.out.println("string");
  }

  }
  报告的错误如下：
  java.lang.NoSuchMethodError: main
  Exception in thread "main"
  这是因为加载了jre自带的java.lang.String，而该类中没有main方法。 
83. Java代码查错 
    1.
    abstract class Name {
       private String name;
       public abstract boolean isStupidName(String name) {}
    }
    大侠们，这有何错误?
    答案: 错。abstract method必须以分号结尾，且不带花括号。
    2.
    public class Something {
       void doSomething () {
           private String s = "";
           int l = s.length();
       }
    }
    有错吗?
    答案: 错。局部变量前不能放置任何访问修饰符 (private，public，和protected)。final可以用来修饰局部变量
    (final如同abstract和strictfp，都是非访问修饰符，strictfp只能修饰class和method而非variable)。
    3.
    abstract class Something {
       private abstract String doSomething ();
    }
    这好像没什么错吧?
    答案: 错。abstract的methods不能以private修饰。abstract的methods就是让子类implement(实现)具体细节的，怎么可以用private把abstract
    method封锁起来呢? (同理，abstract method前不能加final)。
    4.
    public class Something {
       public int addOne(final int x) {
           return ++x;
       }
    }
    这个比较明显。
    答案: 错。int x被修饰成final，意味着x不能在addOne method中被修改。
    5.
    public class Something {
       public static void main(String[] args) {
           Other o = new Other();
           new Something().addOne(o);
       }
       public void addOne(final Other o) {
           o.i++;
       }
    }
    class Other {
       public int i;
    }
    和上面的很相似，都是关于final的问题，这有错吗?
    答案: 正确。在addOne method中，参数o被修饰成final。如果在addOne method里我们修改了o的reference
    (比如: o = new Other();)，那么如同上例这题也是错的。但这里修改的是o的member vairable
    (成员变量)，而o的reference并没有改变。
    6.
    class Something {
        int i;
        public void doSomething() {
            System.out.println("i = " + i);
        }
    }
    有什么错呢? 看不出来啊。
    答案: 正确。输出的是"i = 0"。int i属於instant variable (实例变量，或叫成员变量)。instant variable有default value。int的default value是0。
    7.
    class Something {
        final int i;
        public void doSomething() {
            System.out.println("i = " + i);
        }
    }
    和上面一题只有一个地方不同，就是多了一个final。这难道就错了吗?
    答案: 错。final int i是个final的instant variable (实例变量，或叫成员变量)。final的instant variable没有default value，必须在constructor (构造器)结束之前被赋予一个明确的值。可以修改为"final int i = 0;"。
    8.
    public class Something {
         public static void main(String[] args) {
            Something s = new Something();
            System.out.println("s.doSomething() returns " + doSomething());
        }
        public String doSomething() {
            return "Do something ...";
        }
    }
     看上去很完美。
    答案: 错。看上去在main里call doSomething没有什么问题，毕竟两个methods都在同一个class里。但仔细看，main是static的。static method不能直接call non-static methods。可改成"System.out.println("s.doSomething() returns " + s.doSomething());"。同理，static method不能访问non-static instant variable。
    9.
    此处，Something类的文件名叫OtherThing.java
    class Something {
        private static void main(String[] something_to_do) {       
            System.out.println("Do something ...");
        }
    }
     这个好像很明显。
    答案: 正确。从来没有人说过Java的Class名字必须和其文件名相同。但public class的名字必须和文件名相同。
    10．
    interface  A{
       int x = 0;
    }
    class B{
       int x =1;
    }
    class C extends B implements A {
       public void pX(){
          System.out.println(x);
       }
       public static void main(String[] args) {
          new C().pX();
       }
    }
    答案：错误。在编译时会发生错误(错误描述不同的JVM有不同的信息，意思就是未明确的x调用，两个x都匹配（就象在同时import java.util和java.sql两个包时直接声明Date一样）。对于父类的变量,可以用super.x来明确，而接口的属性默认隐含为 public static final.所以可以通过A.x来明确。
    11.
    interface Playable {
        void play();
    }
    interface Bounceable {
        void play();
    }
    interface Rollable extends Playable, Bounceable {
        Ball ball = new Ball("PingPang");
    }
    class Ball implements Rollable {
        private String name;
        public String getName() {
            return name;
        }
        public Ball(String name) {
            this.name = name;       
        }
       public void play() {
            ball = new Ball("Football");
            System.out.println(ball.getName());
        }
    }
    这个错误不容易发现。
    答案: 错。"interface Rollable extends Playable, Bounceable"没有问题。interface可继承多个interfaces，所以这里没错。问题出在interface Rollable里的"Ball ball = new Ball("PingPang");"。任何在interface里声明的interface variable (接口变量，也可称成员变量)，默认为public static final。也就是说"Ball ball = new Ball("PingPang");"实际上是"public static final Ball ball = new Ball("PingPang");"。在Ball类的Play()方法中，"ball = new Ball("Football");"改变了ball的reference，而这里的ball来自Rollable interface，Rollable interface里的ball是public static final的，final的object是不能被改变reference的。因此编译器将在"ball = new Ball("Football");"这里显示有错。 
二. 算法与编程 
1、编写一个程序，将a.txt文件中的单词与b.txt文件中的单词交替合并到c.txt文件中，a.txt文件中的单词用回车符分隔，b.txt文件中用回车或空格进行分隔。 
  答：
    package cn.itcast;

  import java.io.File;
  import java.io.FileReader;
  import java.io.FileWriter;

  public class MainClass{
  public static void main(String[] args) throws Exception{
    FileManager a = new FileManager("a.txt",new char[]{'\n'});
    FileManager b = new FileManager("b.txt",new char[]{'\n',' '});		
    FileWriter c = new FileWriter("c.txt");
    String aWord = null;
    String bWord = null;
    while((aWord = a.nextWord()) !=null ){
      c.write(aWord + "\n");
      bWord = b.nextWord();
      if(bWord != null)
        c.write(bWord + "\n");
    }

    while((bWord = b.nextWord()) != null){
      c.write(bWord + "\n");
    }
    c.close();
  }

  }


  class FileManager{

  String[] words = null;
  int pos = 0;
  public FileManager(String filename,char[] seperators) throws Exception{
    File f = new File(filename);
    FileReader reader = new FileReader(f);
    char[] buf = new char[(int)f.length()];
    int len = reader.read(buf);
    String results = new String(buf,0,len);
    String regex = null;
    if(seperators.length >1 ){
      regex = "" + seperators[0] + "|" + seperators[1];
    }else{
      regex = "" + seperators[0];
    }
    words = results.split(regex);
  }

  public String nextWord(){
    if(pos == words.length)
      return null;
    return words[pos++];
  }
  }
2、编写一个程序，将d:\java目录下的所有.java文件复制到d:\jad目录下，并将原来文件的扩展名从.java改为.jad。 
    （大家正在做上面这道题，网上迟到的朋友也请做做这道题，找工作必须能编写这些简单问题的代码！）
    答：listFiles方法接受一个FileFilter对象，这个FileFilter对象就是过虑的策略对象，不同的人提供不同的FileFilter实现，即提供了不同的过滤策略。
    import java.io.File;
    import java.io.FileInputStream;
    import java.io.FileOutputStream;
    import java.io.FilenameFilter;
    import java.io.IOException;
    import java.io.InputStream;
    import java.io.OutputStream;

    public class Jad2Java {

    public static void main(String[] args) throws Exception {
      File srcDir = new File("java");
      if(!(srcDir.exists() && srcDir.isDirectory()))
          throw new Exception("目录不存在");
      File[] files = srcDir.listFiles(
        new FilenameFilter(){

            public boolean accept(File dir, String name) {
              return name.endsWith(".java");
            }

          }
      );

      System.out.println(files.length);
      File destDir = new File("jad");
      if(!destDir.exists()) destDir.mkdir();
      for(File f :files){
        FileInputStream  fis = new FileInputStream(f);
        String destFileName = f.getName().replaceAll("\\.java$", ".jad");
        FileOutputStream fos = new FileOutputStream(new File(destDir,destFileName));
        copy(fis,fos);
        fis.close();
        fos.close();
      }
    }

    private static void copy(InputStream ips,OutputStream ops) throws Exception{
      int len = 0;
      byte[] buf = new byte[1024];
      while((len = ips.read(buf)) != -1){
        ops.write(buf,0,len);
      }

    }
    }

    由本题总结的思想及策略模式的解析：
    1.
    class jad2java{
    1. 得到某个目录下的所有的java文件集合
      1.1 得到目录 File srcDir = new File("d:\\java");
      1.2 得到目录下的所有java文件：File[] files = srcDir.listFiles(new MyFileFilter());
      1.3 只想得到.java的文件： class MyFileFilter implememyts FileFilter{
        public boolean accept(File pathname){
          return pathname.getName().endsWith(".java")
        }
      }

    2.将每个文件复制到另外一个目录，并改扩展名
      2.1 得到目标目录，如果目标目录不存在，则创建之
      2.2 根据源文件名得到目标文件名，注意要用正则表达式，注意.的转义。
      2.3 根据表示目录的File和目标文件名的字符串，得到表示目标文件的File。
        //要在硬盘中准确地创建出一个文件，需要知道文件名和文件的目录。
      2.4 将源文件的流拷贝成目标文件流，拷贝方法独立成为一个方法，方法的参数采用抽象流的形式。
        //方法接受的参数类型尽量面向父类，越抽象越好，这样适应面更宽广。
    }

    分析listFiles方法内部的策略模式实现原理
    File[] listFiles(FileFilter filter){
    File[] files = listFiles();
    //Arraylist acceptedFilesList = new ArrayList();
    File[] acceptedFiles = new File[files.length];
    int pos = 0;
    for(File file: files){
      boolean accepted = filter.accept(file);
      if(accepted){
        //acceptedFilesList.add(file);
        acceptedFiles[pos++] = file;
      }		
    }

    Arrays.copyOf(acceptedFiles,pos);
    //return (File[])accpetedFilesList.toArray();

    }  
3、编写一个截取字符串的函数，输入为一个字符串和字节数，输出为按字节截取的字符串，但要保证汉字不被截取半个，如“我ABC”，4，应该截取“我AB”，输入“我ABC汉DEF”，6，应该输出“我ABC”，而不是“我ABC+汉的半个”。 
  答：
  首先要了解中文字符有多种编码及各种编码的特征。
    假设n为要截取的字节数。
  public static void main(String[] args) throws Exception{
    String str = "我a爱中华abc我爱传智def';
    String str = "我ABC汉";
    int num = trimGBK(str.getBytes("GBK"),5);
    System.out.println(str.substring(0,num) );
  }

  public static int  trimGBK(byte[] buf,int n){
    int num = 0;
    boolean bChineseFirstHalf = false;
    for(int i=0;i<n;i++)
    {
      if(buf[i]<0 && !bChineseFirstHalf){
        bChineseFirstHalf = true;
      }else{
        num++;
        bChineseFirstHalf = false;				
      }
    }
    return num;
  } 
4. 有一个字符串，其中包含中文字符、英文字符和数字字符，请统计和打印出各个字符的个数。 
  答：哈哈，其实包含中文字符、英文字符、数字字符原来是出题者放的烟雾弹。
  String content = “中国aadf的111萨bbb菲的zz萨菲”;
  HashMap map = new HashMap();
  for(int i=0;i<content.length;i++)
  {
  char c = content.charAt(i);
  Integer num = map.get(c);
  if(num == null)
    num = 1;
  else
    num = num + 1;
  map.put(c,num);
  }
  for(Map.EntrySet entry : map)
  {
  system.out.println(entry.getkey() + “:” + entry.getValue());
  }
  估计是当初面试的那个学员表述不清楚，问题很可能是：
  如果一串字符如"aaaabbc中国1512"要分别统计英文字符的数量，中文字符的数量，和数字字符的数量，假设字符中没有中文字符、英文字符、数字字符之外的其他特殊字符。
  int engishCount;
  int chineseCount;
  int digitCount;
  for(int i=0;i<str.length;i++)
  {
  char ch = str.charAt(i);
  if(ch>=’0’ && ch<=’9’)
  {
    digitCount++
  }
  else if((ch>=’a’ && ch<=’z’) || (ch>=’A’ && ch<=’Z’))
  {
    engishCount++;
  }
  else
  {
    chineseCount++;
  }
  }
  System.out.println(……………); 
5. 说明生活中遇到的二叉树，用java实现二叉树 
  这是组合设计模式。
  我有很多个(假设10万个)数据要保存起来，以后还需要从保存的这些数据中检索是否存在某个数据，（我想说出二叉树的好处，该怎么说呢？那就是说别人的缺点），假如存在数组中，那么，碰巧要找的数字位于99999那个地方，那查找的速度将很慢，因为要从第1个依次往后取，取出来后进行比较。平衡二叉树（构建平衡二叉树需要先排序，我们这里就不作考虑了）可以很好地解决这个问题，但二叉树的遍历（前序，中序，后序）效率要比数组低很多，原理如下图：

  代码如下：
  package com.huawei.interview;

  public class Node {
  public int value;
  public Node left;
  public Node right;

  public void store(int value)
  {
    if(value<this.value)
    {
      if(left == null)
      {
        left = new Node();
        left.value=value;
      }
      else
      {
        left.store(value);
      }
    }
    else if(value>this.value)
    {
      if(right == null)
      {
        right = new Node();
        right.value=value;
      }
      else
      {
        right.store(value);
      }			
    }
  }

  public boolean find(int value)
  {
    System.out.println("happen " + this.value);
    if(value == this.value)
    {
      return true;
    }
    else if(value>this.value)
    {
      if(right == null) return false;
      return right.find(value);
    }else
    {
      if(left == null) return false;
      return left.find(value);
    }

  }

  public  void preList()
  {
    System.out.print(this.value + ",");
    if(left!=null) left.preList();
    if(right!=null) right.preList();
  }

  public void middleList()
  {
    if(left!=null) left.preList();
    System.out.print(this.value + ",");
    if(right!=null) right.preList();		
  }
  public void afterList()
  {
    if(left!=null) left.preList();
    if(right!=null) right.preList();
    System.out.print(this.value + ",");		
  }
  public static void main(String [] args)
  {
    int [] data = new int[20];
    for(int i=0;i<data.length;i++)
    {
      data[i] = (int)(Math.random()*100) + 1;
      System.out.print(data[i] + ",");
    }
    System.out.println();

    Node root = new Node();
    root.value = data[0];
    for(int i=1;i<data.length;i++)
    {
      root.store(data[i]);
    }

    root.find(data[19]);

    root.preList();
    System.out.println();
    root.middleList();
    System.out.println();		
    root.afterList();
  }
  }
  -----------------又一次临场写的代码---------------------------
  import java.util.Arrays;
  import java.util.Iterator;

  public class Node {
  private Node left;
  private Node right;
  private int value;
  //private int num;

  public Node(int value){
    this.value = value;
  }
  public void add(int value){

    if(value > this.value)
    {
      if(right != null)
        right.add(value);
      else
      {
        Node node = new Node(value);				
        right = node;
      }
    }
    else{
      if(left != null)
        left.add(value);
      else
      {
        Node node = new Node(value);				
        left = node;
      }			
    }
  }

  public boolean find(int value){
    if(value == this.value) return true;
    else if(value > this.value){
      if(right == null) return false;
      else return right.find(value);
    }else{
      if(left == null) return false;
      else return left.find(value);			
    }

  }

  public void display(){
    System.out.println(value);
    if(left != null) left.display();
    if(right != null) right.display();

  }

  /*public Iterator iterator(){

  }*/

  public static void main(String[] args){
    int[] values = new int[8];
    for(int i=0;i<8;i++){
      int num = (int)(Math.random() * 15);
      //System.out.println(num);
      //if(Arrays.binarySearch(values, num)<0)
      if(!contains(values,num))
        values[i] = num;
      else
        i--;
    }

    System.out.println(Arrays.toString(values));

    Node root  = new Node(values[0]);
    for(int i=1;i<values.length;i++){
      root.add(values[i]);
    }

    System.out.println(root.find(13));

    root.display();

  }

  public static boolean contains(int [] arr, int value){
    int i = 0;
    for(;i<arr.length;i++){
      if(arr[i] == value) return true;

    }
    return false;
  }
  }
6、从类似如下的文本文件中读取出所有的姓名，并打印出重复的姓名和重复的次数，并按重复次数排序： 
  1,张三,28
  2,李四,35
  3,张三,28
  4,王五,35
  5,张三,28
  6,李四,35
  7,赵六,28
  8,田七,35

  程序代码如下（答题要博得用人单位的喜欢，包名用该公司，面试前就提前查好该公司的网址，如果查不到，现场问也是可以的。还要加上实现思路的注释）：
  package com.huawei.interview;

  import java.io.BufferedReader;
  import java.io.IOException;
  import java.io.InputStream;
  import java.io.InputStreamReader;
  import java.util.Comparator;
  import java.util.HashMap;
  import java.util.Iterator;
  import java.util.Map;
  import java.util.TreeSet;


  public class GetNameTest {

  /**
   * @param args
   */
  public static void main(String[] args) {
    // TODO Auto-generated method stub
    //InputStream ips = GetNameTest.class.getResourceAsStream("/com/huawei/interview/info.txt");
    //用上一行注释的代码和下一行的代码都可以，因为info.txt与GetNameTest类在同一包下面，所以，可以用下面的相对路径形式

    Map results = new HashMap();
    InputStream ips = GetNameTest.class.getResourceAsStream("info.txt");
    BufferedReader in = new BufferedReader(new InputStreamReader(ips));
    String line = null;
    try {
      while((line=in.readLine())!=null)
      {
        dealLine(line,results);
      }
      sortResults(results);
    } catch (IOException e) {
      // TODO Auto-generated catch block
      e.printStackTrace();
    }
  }

  static class User
  {
    public  String name;
    public Integer value;
    public User(String name,Integer value)
    {
      this.name = name;
      this.value = value;
    }

    @Override
    public boolean equals(Object obj) {
      // TODO Auto-generated method stub

      //下面的代码没有执行，说明往treeset中增加数据时，不会使用到equals方法。
      boolean result = super.equals(obj);
      System.out.println(result);
      return result;
    }
  }

  private static void sortResults(Map results) {
    // TODO Auto-generated method stub
    TreeSet sortedResults = new TreeSet(
        new Comparator(){
          public int compare(Object o1, Object o2) {
            // TODO Auto-generated method stub
            User user1 = (User)o1;
            User user2 = (User)o2;
            /*如果compareTo返回结果0，则认为两个对象相等，新的对象不会增加到集合中去
             * 所以，不能直接用下面的代码，否则，那些个数相同的其他姓名就打印不出来。
             * */

            //return user1.value-user2.value;
            //return user1.value<user2.value?-1:user1.value==user2.value?0:1;
            if(user1.value<user2.value)
            {
              return -1;
            }else if(user1.value>user2.value)
            {
              return 1;
            }else
            {
              return user1.name.compareTo(user2.name);
            }
          }

        }
    );
    Iterator iterator = results.keySet().iterator();
    while(iterator.hasNext())
    {
      String name = (String)iterator.next();
      Integer value = (Integer)results.get(name);
      if(value > 1)
      {				
        sortedResults.add(new User(name,value));				
      }
    }

    printResults(sortedResults);
  }
  private static void printResults(TreeSet sortedResults)
  {
    Iterator iterator  = sortedResults.iterator();
    while(iterator.hasNext())
    {
      User user = (User)iterator.next();
      System.out.println(user.name + ":" + user.value);
    }
  }
  public static void dealLine(String line,Map map)
  {
    if(!"".equals(line.trim()))
    {
      String [] results = line.split(",");
      if(results.length == 3)
      {
        String name = results[1];
        Integer value = (Integer)map.get(name);
        if(value == null) value = 0;
        map.put(name,value + 1);
      }
    }
  }
  }
7、写一个Singleton出来。 
  第一种：饱汉模式
  public class SingleTon {
  private SingleTon(){
    }

  //实例化放在静态代码块里可提高程序的执行效率，但也可能更占用空间
  private final static SingleTon instance = new SingleTon();
  public static SingleTon getInstance(){
    return instance;
  }
  }

  第二种：饥汉模式
  public class SingleTon {
  private SingleTon(){}

  private static instance = null;//new SingleTon();

  public static synchronized SingleTon getInstance(){
    if(instance == null)
      instance = new SingleTon();
    return instance;
  }
  }

  第三种：用枚举
  public enum SingleTon{
    ONE;

  }

  第三：更实际的应用（在什么情况用单例）
  public class SequenceGenerator{
  //下面是该类自身的业务功能代码
  private int count = 0;

  public synchronized int getSequence(){
    ++count;
  }

  //下面是把该类变成单例的代码
  private SequenceGenerator(){}
  private final static instance = new SequenceGenerator();
  public static SingleTon getInstance(){
    return instance;
  }

  }

  第四：
  public class MemoryDao
  {
    private HashMap map = new HashMap();

    public void add(Student stu1){
        map.put(SequenceGenerator.getInstance().getSequence(),stu1);
    }

   //把MemoryDao变成单例
  }






  Singleton模式主要作用是保证在Java应用程序中，一个类Class只有一个实例存在。
  一般Singleton模式通常有几种种形式:
  第一种形式: 定义一个类，它的构造函数为private的，它有一个static的private的该类变量，在类初始化时实例话，通过一个public的getInstance方法获取对它的引用,继而调用其中的方法。
  public class Singleton {
  private Singleton(){}
  　　    //在自己内部定义自己一个实例，是不是很奇怪？
  　　    //注意这是private 只供内部调用
  　　    private static Singleton instance = new Singleton();
  　　    //这里提供了一个供外部访问本class的静态方法，可以直接访问　　
  　　    public static Singleton getInstance() {
  　　　　    return instance; 　　
  　　    }
   }
   第二种形式:
  public class Singleton {
  　　private static Singleton instance = null;
  　　public static synchronized Singleton getInstance() {
  　　//这个方法比上面有所改进，不用每次都进行生成对象，只是第一次　　　 　
  　　//使用时生成实例，提高了效率！
  　　if (instance==null)
  　　　　instance＝new Singleton();
      return instance; 　　
  }
  }
  其他形式:
  定义一个类，它的构造函数为private的，所有方法为static的。
  一般认为第一种形式要更加安全些    
8、递归算法题1 
  一个整数，大于0，不用循环和本地变量，按照n，2n，4n，8n的顺序递增，当值大于5000时，把值按照指定顺序输出来。
  例：n=1237
  则输出为：
  1237，
  2474，
  4948，
  9896，
  9896，
  4948，
  2474，
  1237，
  提示：写程序时，先致谢按递增方式的代码，写好递增的以后，再增加考虑递减部分。
  public static void doubleNum(int n)
  {
    System.out.println(n);
    if(n<=5000)
      doubleNum(n*2);
    System.out.println(n);		
  } 
9、递归算法题2 
  第1个人10，第2个比第1个人大2岁，依次递推，请用递归方式计算出第8个人多大？
  package cn.itcast;

  import java.util.Date;

  public class A1 {

  public static void main(String [] args)
  {
    System.out.println(computeAge(8));
  }

  public static int computeAge(int n)
  {
    if(n==1) return 10;
    return computeAge(n-1) + 2;
  }
  }

  public static void toBinary(int n,StringBuffer result)
  {

    if(n/2 != 0)
      toBinary(n/2,result);
    result.append(n%2);		
  } 
10、排序都有哪几种方法？请列举。用JAVA实现一个快速排序。 
  本人只研究过冒泡排序、选择排序和快速排序，下面是快速排序的代码：

  public class QuickSort {
  /**
  * 快速排序
  * @param strDate
  * @param left
  * @param right
  */
  public void quickSort(String[] strDate,int left,int right){
  String middle,tempDate;
  int i,j;
  i=left;
  j=right;
  middle=strDate[(i+j)/2];
  do{
  while(strDate[i].compareTo(middle)<0&& i<right)
  i++; //找出左边比中间值大的数
  while(strDate[j].compareTo(middle)>0&& j>left)
  j--; //找出右边比中间值小的数
  if(i<=j){ //将左边大的数和右边小的数进行替换
  tempDate=strDate[i];
  strDate[i]=strDate[j];
  strDate[j]=tempDate;
  i++;
  j--;
  }
  }while(i<=j); //当两者交错时停止

  if(i<right){
  quickSort(strDate,i,right);//从
  }
  if(j>left){
  quickSort(strDate,left,j);
  }
  }
  /**
    * @param args
    */
  public static void main(String[] args){
  String[] strVoid=new String[]{"11","66","22","0","55","22","0","32"};
  QuickSort sort=new QuickSort();
  sort.quickSort(strVoid,0,strVoid.length-1);
  for(int i=0;i<strVoid.length;i++){
  System.out.println(strVoid[i]+" ");
  }
  }


  }


11、有数组a[n]，用java代码将数组元素顺序颠倒

  //用下面的也可以
  //for(int i=0,int j=a.length-1;i<j;i++,j--) 是否等效于 for(int i=0;i<a.length/2;i++)呢？

  import java.util.Arrays;

  public class SwapDemo{

  public static void main(String[] args){
    int [] a = new int[]{
            (int)(Math.random() * 1000),
            (int)(Math.random() * 1000),
            (int)(Math.random() * 1000),
            (int)(Math.random() * 1000),						
            (int)(Math.random() * 1000)																		
    };

    System.out.println(a);
    System.out.println(Arrays.toString(a));
    swap(a);
    System.out.println(Arrays.toString(a));		
  }

  public static void swap(int a[]){
    int len = a.length;
    for(int i=0;i<len/2;i++){
      int tmp = a[i];
      a[i] = a[len-1-i];
      a[len-1-i] = tmp;
    }
  }
  } 
12．金额转换，阿拉伯数字的金额转换成中国传统的形式如：（￥1011）－>（一千零一拾一元整）输出。 
  去零的代码：
  return sb.reverse().toString().replaceAll("零[拾佰仟]","零").replaceAll("零+万","万").replaceAll("零+元","元").replaceAll("零+","零");

  public class RenMingBi {

  /**
   * @param args add by zxx ,Nov 29, 2008
   */
  private static final char[] data = new char[]{
      '零','壹','贰','叁','肆','伍','陆','柒','捌','玖'
    };
  private static final char[] units = new char[]{
    '元','拾','佰','仟','万','拾','佰','仟','亿'
  };
  public static void main(String[] args) {
    // TODO Auto-generated method stub
    System.out.println(
        convert(135689123));
  }

  public static String convert(int money)
  {
    StringBuffer sbf = new StringBuffer();
    int unit = 0;
    while(money!=0)
    {
      sbf.insert(0,units[unit++]);
      int number = money%10;
      sbf.insert(0, data[number]);
      money /= 10;
    }

    return sbf.toString();
  }
  } 
  1.    请描述下Activity的生命周期。
        必调用的三个方法：onCreate() --> onStart() --> onResume()，用AAA表示

  （1）父Activity启动子Activity，子Actvity退出，父Activity调用顺序如下
  AAA --> onFreeze() --> onPause() --> onStop() --> onRestart() --> onStart(),onResume() …
  （2）用户点击Home，Actvity调用顺序如下
  AAA --> onFreeze() --> onPause() --> onStop() -- Maybe --> onDestroy() – Maybe
  （3）调用finish()， Activity调用顺序如下
  AAA --> onPause() --> onStop() --> onDestroy()
  （4）在Activity上显示dialog， Activity调用顺序如下
  AAA
  （5）在父Activity上显示透明的或非全屏的activity，Activity调用顺序如下
  AAA --> onFreeze() --> onPause()
  （6）设备进入睡眠状态，Activity调用顺序如下
  AAA --> onFreeze() --> onPause()

  2.    如果后台的Activity由于某原因被系统回收了，如何在被系统回收之前保存当前状态？

        onSaveInstanceState()

        当你的程序中某一个Activity A在运行时，主动或被动地运行另一个新的Activity B，这个时候A会执行onSaveInstanceState()。B完成以后又会来找A，这个时候就有两种情况：一是A被回收，二是A没有被回收，被回收的A就要重新调用onCreate()方法，不同于直接启动的是这回onCreate()里是带上了参数savedInstanceState；而没被收回的就直接执行onResume()，跳过onCreate()了。 

  3.    如何将一个Activity设置成窗口的样式。

        在AndroidManifest.xml 中定义Activity的地方一句话android:theme="@android:style/Theme.Dialog"或android:theme="@android:style/Theme.Translucent"就变成半透明的

  4.    如何退出Activity？如何安全退出已调用多个Activity的Application？

  对于单一Activity的应用来说，退出很简单，直接finish()即可。
  当然，也可以用killProcess()和System.exit()这样的方法。

  但是，对于多Activity的应用来说，在打开多个Activity后，如果想在最后打开的Activity直接退出，上边的方法都是没有用的，因为上边的方法都是结束一个Activity而已。
  当然，网上也有人说可以。
  就好像有人问，在应用里如何捕获Home键，有人就会说用keyCode比较KEYCODE_HOME即可，而事实上如果不修改framework，根本不可能做到这一点一样。
  所以，最好还是自己亲自试一下。

  那么，有没有办法直接退出整个应用呢？
  在2.1之前，可以使用ActivityManager的restartPackage方法。
  它可以直接结束整个应用。在使用时需要权限android.permission.RESTART_PACKAGES。
  注意不要被它的名字迷惑。

  可是，在2.2，这个方法失效了。
  在2.2添加了一个新的方法，killBackgroundProcesses()，需要权限 android.permission.KILL_BACKGROUND_PROCESSES。
  可惜的是，它和2.2的restartPackage一样，根本起不到应有的效果。

  另外还有一个方法，就是系统自带的应用程序管理里，强制结束程序的方法，forceStopPackage()。
  它需要权限android.permission.FORCE_STOP_PACKAGES。
  并且需要添加android:sharedUserId="android.uid.system"属性
  同样可惜的是，该方法是非公开的，他只能运行在系统进程，第三方程序无法调用。
  因为需要在Android.mk中添加LOCAL_CERTIFICATE := platform。
  而Android.mk是用于在Android源码下编译程序用的。

  从以上可以看出，在2.2，没有办法直接结束一个应用，而只能用自己的办法间接办到。

  现提供几个方法，供参考：

  1、抛异常强制退出：
  该方法通过抛异常，使程序Force Close。
  验证可以，但是，需要解决的问题是，如何使程序结束掉，而不弹出Force Close的窗口。

  2、记录打开的Activity：
  每打开一个Activity，就记录下来。在需要退出时，关闭每一个Activity即可。

  3、发送特定广播：
  在需要结束应用时，发送一个特定的广播，每个Activity收到广播后，关闭即可。

  4、递归退出
  在打开新的Activity时使用startActivityForResult，然后自己加标志，在onActivityResult中处理，递归关闭。

  除了第一个，都是想办法把每一个Activity都结束掉，间接达到目的。
  但是这样做同样不完美。
  你会发现，如果自己的应用程序对每一个Activity都设置了nosensor，在两个Activity结束的间隙，sensor可能有效了。
  但至少，我们的目的达到了，而且没有影响用户使用。

  为了编程方便，最好定义一个Activity基类，处理这些共通问题。

  5.    请介绍下Android中常用的五种布局。

  FrameLayout（框架布局），LinearLayout （线性布局），AbsoluteLayout（绝对布局），RelativeLayout（相对布局），TableLayout（表格布局）

  6.    请介绍下Android的数据存储方式。

  一.SharedPreferences方式

  二.文件存储方式

  三.SQLite数据库方式

  四.内容提供器（Content provider）方式

  五. 网络存储方式

  7.    请介绍下ContentProvider是如何实现数据共享的。

  创建一个属于你自己的Content provider或者将你的数据添加到一个已经存在的Content provider中，前提是有相同数据类型并且有写入Content provider的权限。

      如何启用Service，如何停用Service。


  Android中的service类似于windows中的service，service一般没有用户操作界面，它运行于系统中不容易被用户发觉，


  可以使用它开发如监控之类的程序。


  一。步骤


  第一步：继承Service类


  public class SMSService extends Service { }


  第二步：在AndroidManifest.xml文件中的<application>节点里对服务进行配置:


  <service android:name=".DemoService" />


  二。Context.startService()和Context.bindService


  服务不能自己运行，需要通过调用Context.startService()或Context.bindService()方法启动服务。这两个方法都可


  以启动Service，但是它们的使用场合有所不同。


  1.使用startService()方法启用服务，调用者与服务之间没有关连，即使调用者退出了，服务仍然运行。


  使用bindService()方法启用服务，调用者与服务绑定在了一起，调用者一旦退出，服务也就终止。


  2.采用Context.startService()方法启动服务，在服务未被创建时，系统会先调用服务的onCreate()方法，


  接着调用onStart()方法。如果调用startService()方法前服务已经被创建，多次调用startService()方法并


  不会导致多次创建服务，但会导致多次调用onStart()方法。


  采用startService()方法启动的服务，只能调用Context.stopService()方法结束服务，服务结束时会调用


  onDestroy()方法。



  3.采用Context.bindService()方法启动服务，在服务未被创建时，系统会先调用服务的onCreate()方法，


  接着调用onBind()方法。这个时候调用者和服务绑定在一起，调用者退出了，系统就会先调用服务的onUnbind()方法，


  。接着调用onDestroy()方法。如果调用bindService()方法前服务已经被绑定，多次调用bindService()方法并不会


  导致多次创建服务及绑定(也就是说onCreate()和onBind()方法并不会被多次调用)。如果调用者希望与正在绑定的服务


  解除绑定，可以调用unbindService()方法，调用该方法也会导致系统调用服务的onUnbind()-->onDestroy()方法。


  三。Service的生命周期


  1.Service常用生命周期回调方法如下：



  onCreate() 该方法在服务被创建时调用，该方法只会被调用一次，无论调用多少次startService()或bindService()方法，


  服务也只被创建一次。 onDestroy()该方法在服务被终止时调用。



  2. Context.startService()启动Service有关的生命周期方法


  onStart() 只有采用Context.startService()方法启动服务时才会回调该方法。该方法在服务开始运行时被调用。


  多次调用startService()方法尽管不会多次创建服务，但onStart() 方法会被多次调用。



  3. Context.bindService()启动Service有关的生命周期方法


  onBind()只有采用Context.bindService()方法启动服务时才会回调该方法。该方法在调用者与服务绑定时被调用，


  当调用者与服务已经绑定，多次调用Context.bindService()方法并不会导致该方法被多次调用。


  onUnbind()只有采用Context.bindService()方法启动服务时才会回调该方法。该方法在调用者与服务解除绑定时被调用。


  备注：


  1. 采用startService()启动服务


       Intent intent = new Intent(DemoActivity.this, DemoService.class);


       startService(intent);


  2.Context.bindService()启动


      Intent intent = new Intent(DemoActivity.this, DemoService.class);


      bindService(intent, conn, Context.BIND_AUTO_CREATE);


     //unbindService(conn);//解除绑定

      注册广播有几种方式，这些方式有何优缺点？请谈谈Android引入广播机制的用意。

    Android广播机制（两种注册方法）

  在android下，要想接受广播信息，那么这个广播接收器就得我们自己来实现了，我们可以继承BroadcastReceiver，就可以有一个广播接受器了。有个接受器还不够，我们还得重写BroadcastReceiver里面的onReceiver方法，当来广播的时候我们要干什么，这就要我们自己来实现，不过我们可以搞一个信息防火墙。具体的代码：



  public class SmsBroadCastReceiver extends BroadcastReceiver    

  {   



      @Override  

      public void onReceive(Context context, Intent intent)   

      {   

          Bundle bundle = intent.getExtras();   

          Object[] object = (Object[])bundle.get("pdus");   

          SmsMessage sms[]=new SmsMessage[object.length];   

          for(int i=0;i<object.length;i++)   

          {   

              sms[0] = SmsMessage.createFromPdu((byte[])object[i]);   

              Toast.makeText(context, "来自"+sms[i].getDisplayOriginatingAddress()+" 的消息是："+sms[i].getDisplayMessageBody(), Toast.LENGTH_SHORT).show();   

          }   

          //终止广播，在这里我们可以稍微处理，根据用户输入的号码可以实现短信防火墙。   

          abortBroadcast();   

      }   



  }  



    当实现了广播接收器，还要设置广播接收器接收广播信息的类型，这里是信息：android.provider.Telephony.SMS_RECEIVED



    我们就可以把广播接收器注册到系统里面，可以让系统知道我们有个广播接收器。这里有两种，一种是代码动态注册：



  //生成广播处理   

  smsBroadCastReceiver = new SmsBroadCastReceiver();   

  //实例化过滤器并设置要过滤的广播   



  IntentFilter intentFilter = new IntentFilter("android.provider.Telephony.SMS_RECEIVED");



  //注册广播   

  BroadCastReceiverActivity.this.registerReceiver(smsBroadCastReceiver, intentFilter);  

  一种是在AndroidManifest.xml中配置广播



  <?xml version="1.0" encoding="utf-8"?>  

  <manifest xmlns:android="http://schemas.android.com/apk/res/android"  

        package="spl.broadCastReceiver"  

        android:versionCode="1"  

        android:versionName="1.0">  

      <application android:icon="@drawable/icon" android:label="@string/app_name">  

          <activity android:name=".BroadCastReceiverActivity"  

                    android:label="@string/app_name">  

              <intent-filter>  

                  <action android:name="android.intent.action.MAIN" />  

                  <category android:name="android.intent.category.LAUNCHER" />  

              </intent-filter>  

          </activity>  



          <!--广播注册-->  

          <receiver android:name=".SmsBroadCastReceiver">  

              <intent-filter android:priority="20">  

                  <action android:name="android.provider.Telephony.SMS_RECEIVED"/>  

              </intent-filter>  

          </receiver>  



      </application>  



      <uses-sdk android:minSdkVersion="7" />  



      <!-- 权限申请 -->  

      <uses-permission android:name="android.permission.RECEIVE_SMS"></uses-permission>  



  </manifest>   



    两种注册类型的区别是：



       1)第一种不是常驻型广播，也就是说广播跟随程序的生命周期。



       2)第二种是常驻型，也就是说当应用程序关闭后，如果有信息广播来，程序也会被系统调用自动运行。

      请解释下在单线程模型中Message、Handler、Message Queue、Looper之间的关系。


  Handler简介：
  一个Handler允许你发送和处理Message和Runable对象，这些对象和一个线程的MessageQueue相关联。每一个线程实例和一个单独的线程以及该线程的MessageQueue相关联。当你创建一个新的Handler时，它就和创建它的线程绑定在一起了。这里，线程我们也可以理解为线程的MessageQueue。从这一点上来看，Handler把Message和Runable对象传递给MessageQueue，而且在这些对象离开MessageQueue时，Handler负责执行他们。

  Handler有两个主要的用途：（1）确定在将来的某个时间点执行一个或者一些Message和Runnable对象。（2）在其他线程（不是Handler绑定线程）中排入一些要执行的动作。

  Scheduling Message，即（1），可以通过以下方法完成：
  post(Runnable):Runnable在handler绑定的线程上执行，也就是说不创建新线程。
  postAtTime(Runnable,long):
  postDelayed(Runnable,long):
  sendEmptyMessage(int):
  sendMessage(Message):
  sendMessageAtTime(Message,long):
  sendMessageDelayed(Message,long):
  post这个动作让你把Runnable对象排入MessageQueue,MessageQueue受到这些消息的时候执行他们，当然以一定的排序。sendMessage这个动作允许你把Message对象排成队列，这些Message对象包含一些信息，Handler的hanlerMessage(Message)会处理这些Message.当然，handlerMessage(Message)必须由Handler的子类来重写。这是编程人员需要作的事。

  当posting或者sending到一个Hanler时，你可以有三种行为：当MessageQueue准备好就处理，定义一个延迟时间，定义一个精确的时间去处理。后两者允许你实现timeout,tick,和基于时间的行为。

  当你的应用创建一个新的进程时，主线程（也就是UI线程）自带一个MessageQueue，这个MessageQueue管理顶层的应用对象（像activities,broadcast receivers等）和主线程创建的窗体。你可以创建自己的线程，并通过一个Handler和主线程进行通信。这和之前一样，通过post和sendmessage来完成，差别在于在哪一个线程中执行这么方法。在恰当的时候，给定的Runnable和Message将在Handler的MessageQueue中被Scheduled。


  Message简介：
  Message类就是定义了一个信息，这个信息中包含一个描述符和任意的数据对象，这个信息被用来传递给Handler.Message对象提供额外的两个int域和一个Object域，这可以让你在大多数情况下不用作分配的动作。
  尽管Message的构造函数是public的，但是获取Message实例的最好方法是调用Message.obtain(),或者Handler.obtainMessage()方法，这些方法会从回收对象池中获取一个。


  MessageQueue简介：
  这是一个包含message列表的底层类。Looper负责分发这些message。Messages并不是直接加到一个MessageQueue中，而是通过MessageQueue.IdleHandler关联到Looper。
  你可以通过Looper.myQueue()从当前线程中获取MessageQueue。


  Looper简介：
  Looper类被用来执行一个线程中的message循环。默认情况，没有一个消息循环关联到线程。在线程中调用prepare()创建一个Looper，然后用loop()来处理messages，直到循环终止。

  大多数和message loop的交互是通过Handler。

  下面是一个典型的带有Looper的线程实现。
    class LooperThread extends Thread {
        public Handler mHandler;

        public void run() {
            Looper.prepare();

            mHandler = new Handler() {
                public void handleMessage(Message msg) {
                    // process incoming messages here
                }
            };

            Looper.loop();
        }
    }



      AIDL的全称是什么？如何工作？能处理哪些类型的数据？

  AIDL的英文全称是Android Interface Define Language
  当A进程要去调用B进程中的service时，并实现通信，我们通常都是通过AIDL来操作的

  A工程：

  首先我们在net.blogjava.mobile.aidlservice包中创建一个RemoteService.aidl文件，在里面我们自定义一个接口，含有方法get。ADT插件会在gen目录下自动生成一个RemoteService.java文件，该类中含有一个名为RemoteService.stub的内部类，该内部类中含有aidl文件接口的get方法。

  说明一：aidl文件的位置不固定，可以任意

  然后定义自己的MyService类，在MyService类中自定义一个内部类去继承RemoteService.stub这个内部类，实现get方法。在onBind方法中返回这个内部类的对象，系统会自动将这个对象封装成IBinder对象，传递给他的调用者。

  其次需要在AndroidManifest.xml文件中配置MyService类，代码如下：

  <!-- 注册服务 -->  

  <service android:name=".MyService">

     <intent-filter>

     <!--  指定调用AIDL服务的ID  -->

         <action android:name="net.blogjava.mobile.aidlservice.RemoteService" />

      </intent-filter>

  </service>

  为什么要指定调用AIDL服务的ID,就是要告诉外界MyService这个类能够被别的进程访问，只要别的进程知道这个ID，正是有了这个ID,B工程才能找到A工程实现通信。

  说明：AIDL并不需要权限

  B工程：

        首先我们要将A工程中生成的RemoteService.java文件拷贝到B工程中，在bindService方法中绑定aidl服务

        绑定AIDL服务就是将RemoteService的ID作为intent的action参数。

        说明：如果我们单独将RemoteService.aidl文件放在一个包里，那个在我们将gen目录下的该包拷贝到B工程中。如果我们将RemoteService.aidl文件和我们的其他类存放在一起，那么我们在B工程中就要建立相应的包，以保证RmoteService.java文件的报名正确，我们不能修改RemoteService.java文件

             bindService(new Inten("net.blogjava.mobile.aidlservice.RemoteService"), serviceConnection, Context.BIND_AUTO_CREATE);

         ServiceConnection的onServiceConnected(ComponentName name, IBinder service)方法中的service参数就是A工程中MyService类中继承了RemoteService.stub类的内部类的对象。

  12.    请解释下Android程序运行时权限与文件系统权限的区别。
        运行时权限是Dalvik授权
        文件系统权限是 linux 内核授权
        http://blog.sina.com.cn/s/blog_624012330100ynit.html

  13.    系统上安装了多种浏览器，能否指定某浏览器访问指定页面？请说明原由。

          一、启动android默认浏览器
          在Android程序中我们可以通过发送隐式Intent来启动系统默认的浏览器。如果手机本身安装了多个浏览器而又没有设置默认浏览器的话，系统将让用户选择使用哪个浏览器来打开连接。关于Intent的更多内容请参考《常用Intent》
          示例1


                  Intent intent =newIntent();
                  intent.setAction("android.intent.action.VIEW");
                  Uri content_url =Uri.parse("http://www.163.com");
                  intent.setData(content_url);
                  startActivity(intent);
          这样子，android就可以调用起手机默认的浏览器访问。
          二、启动指定浏览器
          在Android程序中我们可以通过发送显式Intent来启动指定的浏览器。
          启动Android原生浏览器
          示例2


                   Intent intent =newIntent();        
                   intent.setAction("android.intent.action.VIEW");    
                   Uri content_url =Uri.parse("http://www.163.com");   
                   intent.setData(content_url);           
                   intent.setClassName("com.android.browser","com.android.browser.BrowserActivity");   
                   startActivity(intent);
          只要修改以intent.setClassName("com.android.browser","com.android.browser.BrowserActivity");
          中相应的应用程序packagename 和要启动的activity即可启动其他浏览器来
          uc浏览器"："com.uc.browser", "com.uc.browser.ActivityUpdate“
          opera浏览器："com.opera.mini.android", "com.opera.mini.android.Browser"
          qq浏览器："com.tencent.mtt", "com.tencent.mtt.MainActivity"



  14.    有一个一维整型数组int[]data保存的是一张宽为width，高为height的图片像素值信息。请写一个算法，将该图片所有的白色不透明(0xffffffff)像素点的透明度调整为50%。



  15.    你如何评价Android系统？优缺点。 
