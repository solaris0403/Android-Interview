# Android面试试题
### 一般简单题
1. Android dvm的进程和Linux的进程，应用程序的进程是否为同一个概念？  
  DVM指Dalivk的虚拟机，每一个Android应用程序都在它自己的进程中运行，都拥有一个独立的Dalivk虚拟机实例。而每一个DVM都是在Linux中的一个进程，所以说可以认为是同一个概念。
2. SIM卡的 EF 文件有何作用？  
  sim卡的文件系统有自己的规范，主要是为了和手机通讯，sim本身可以有自己的操作系统，EF就是做存储并和手机通讯用的。
3. 嵌入式操作系统内存管理有哪几种，各有何特性？  
  页式，段式，段页，用到了MMU，虚拟控件等技术。
4. 什么是嵌入式实时操作系统，Android 操作系统属于实时操作系统吗？  
  嵌入式实时操作系统是指当外界事件或数据产生时，能够接受并以足够快的速度予以处理，其处理的结果又能在规定的时间之内来控制生产过程或对处理系统作出快速响应，并控制所有实时任务协调一致运行的嵌入式操作系统。主要用于工业控制、军事设备、航空航天等领域对系统的响应时间有苛刻的要求，这就需要使用实时系统。又可分为软实时和硬实时两种，而android是基于linux内核的，因此属于软实时。
5. 一条最长的短信息约占多少byte？  
  中文70(包括标点)，英文占160字节。
6. Android中的动画有哪几类，它们的特点和区别是什么？  
  两种，一中是Tween动画，一种是Frame动画。这种实现方式可以使视图组件移动、放大、缩小以及产生透明度的变化；另一种Frame动画，传统的动画方法，通过顺序的播放排列好的图片来实现，类似电影。
7. Handler机制的原理  
  Andriod提供了 Handler 和 Looper 来满足线程间的通信。Handler 先进先出原则。Looper类用来管理特定线程内对象之间的消息交换(Message Exchange)。  
  Looper: 一个线程可以产生一个Looper对象，由它来管理此线程里的Message Queue(消息队列)。  
  Handler: 你可以构造Handler对象来与Looper沟通，以便push新消息到Message Queue里；或者接收Looper从Message Queue取出)所送来的消息。  
  Message Queue(消息队列):用来存放线程放入的消息。  
  线程：UI thread 通常就是main thread，而Android启动程序时会替它建立一个Message Queue。  
8. 说说MVC模式的原理，它在Android中的运用  
  MVC(Model_view_controller)” 模型-视图-控制器”。 MVC应用程序总是由这三个部分组成。Event(事件)导致Controller改变Model或View，或者同时改变两者。只要 Controller改变了Models的数据或者属性，所有依赖的View都会自动更新。类似的，只要Controller改变了View，View会从潜在的Model中获取数据来刷新自己。  
---
### View重绘和内存泄露
9. View的刷新  
  在需要刷新的地方，使用Handler.sendmessage发送消息，然后在Handler的getmessage里面执行invalidate或者invalidate  
10. GC内存泄露  
  出现情况：  
  * 数据库的cursor没有关闭。
  * 构造adapter时，没有使用缓存contentview。衍生listview的优化问题：减少创建view的对象，充分使用contentview，可以使用一静态类来优化处理getview的过程。
  * Bitmap对象不使用时采用recycle()释放内存。
  * activity中的对象的生命周期大于activity。  
---  
### Activity
11. Activity的生命周期  
  ```
  @Override
   protected void onCreate(Bundle savedInstanceState) {
       super.onCreate(savedInstanceState);
       setContentView(R.layout.activity_main);
       //在这里创建界面，做一些数据的初始化工作。
   }

   @Override
   protected void onStart() {
       super.onStart();
       //到这一步变成用户可见不可交互的。
   }

   @Override
   protected void onRestart() {
       super.onRestart();
       //從stop重新開始
   }

   @Override
   protected void onResume() {
       super.onResume();
       //变成和用户可交互的
   }

   @Override
   protected void onPause() {
       super.onPause();
       //到这一步是可见但不可交互的，系统会停止动画等消耗CPU的事情从上文的描述已经知道，应该在这里保存你的一些数据，
       // 因为这个时候你的程序的优先级降低，有可能被系统收回。在这里保存的数据，应该在 onResume里读出来，
       // 注意：这个方法里做的事情时间要短，因为下一个activity不会等到这个方法完成才启动。
   }

   @Override
   protected void onStop() {
       super.onStop();
       //变得不可见，被下一个activity覆盖了。
   }

   @Override
   protected void onDestroy() {
       super.onDestroy();
       //这是activity被干掉前最后一个被调用方法了，可能是外面类调用finish方法或者是系统为了
       // 节省空间将它暂时性的干掉，可以用isFinishing()来判断它，
       // 如果你有一个Progress Dialog在线程中转动，请在onDestroy里把他cancel掉，
       // 不然等线程结束的时候，调用Dialog的cancel方法会抛异常的。
   }
  ```  
12. 让Activity变成一个窗口：Activity属性设定  
  可能有人希望做出来的应用程序是一个漂浮在手机主界面的东西，那么很简单你只需要设置一下Activity的主题就可以了在AndroidManifest.xml 中定义 Activity的地方一句话：
  ```
  android:theme="@android:style/Theme.Dialog"
  ```
  这就使你的应用程序变成对话框的形式弹出来了，或者
  ```
  android:theme="@android:style/Theme.Translucent"
  ```
  就变成半透明的，类似的这种activity的属性可以在android.R.styleable 类的AndroidManifestActivity 方法中看到，AndroidManifest.xml中所有元素的属性的介绍都可以参考这个类android.R.styleable上面说的是属性名称，具体有什么值是在android.R.style中可以看到，比如这个"@android:style/Theme.Dialog"就对应于android.R.style.Theme_Dialog ,（'_'换成'.' ）就可以用在描述文件中了，找找类定义和描述文件中的对应关系就都明白了。   
13. 你后台的Activity被系统回收怎么办：onSaveInstanceState
  当你的程序中某一个Activity A 在运行时中，主动或被动地运行另一个新的Activity B 这个时候A会执行Java代码：   
  ```
  @Override
  protected void onSaveInstanceState(Bundle outState) {
    super.onSaveInstanceState(outState);
  }
  ```
14. 面試流程[!http://www.bubuko.com/infodetail-992911.html]   http://www.testtao.com/thread-32127-1-1.html
14. java.io包中定义了多个流类型来实现输入和输出功能，可以从不同的角度对其进行分                   类,按功能分为：(节点流和处理流),如果为读取的内容进行处理后再输出，需要使用下列哪种流?    Filter stream   
15. 下列代码的执行结果是：(B)   
  ```
  public class Test3{
    public static void main(String args[]){
      System.out.print(100%3);
      System.out.print(",");
      System.out.println(100%3.0);
      }
    }
  ```
  A、1,1 B、1,1.0 C、1.0,1 D、1.0,1.0
16. 在继承中，关于构造方法的说明，下列说法错误的是(D)
    A、子类无条件的继承父类的无参构造方法，   
　　B、子类可以引用父类中的有参构造方法，使用super关键字，   
　　C、如果子类没有构造方法，则父类无参构造方法作为自已的构造方法，   
　　D、如果子类有无参构造方法，而父类的无参构造方法则被覆盖。
17. 以下程序的运行结果为(B)
  ```
  public class IfTest{

　　public static void main(String args[]){

　　int x=3;

　　int y=1;

　　if(x==y)

　　System.out.println("Not equal");

　　else

　　System.out.println("Equal");

　　}
　　}
  ```
  A、Not equal B、Equal C、无输出 D、编译出错
18. Java语言中字符串“学Java”所占的内存空间是(a)   
  A. 6个字节 B. 7个字节 C. 10个字节 D. 11个字节
19. 关于下列程序段的输出结果，说法正确的是：( D)
  ```
  public class MyClass{

　　static int i; public static void main(Stringargv[]){ System.out.println(i); } }
  ```
  A、有错误，变量i没有初始化。 B、null C、1 D、0   
20. 下列哪些语句关于内存回收的说明是正确的? (B )   
    A、 程序员必须创建一个线程来释放内存

　　B、 内存回收程序负责释放无用内存

　　C、 内存回收程序允许程序员直接释放内存

　　D、 内存回收程序可以在指定的时间释放内存对象
21. 下面异常是属于Runtime Exception 的是(ABCD)(多选)   
    A、ArithmeticException

　　B、IllegalArgumentException

　　C、NullPointerException

　　D、BufferUnderflowException
22. Math.round(11.5)等于多少(). Math.round(-11.5)等于多少(C).   
  A、11 ,-11 B、11 ,-12 C、12 ,-11 D、12 ,-12
23. 下列程序段的输出结果是：(B )   
  ```
  void complicatedexpression_r(){ int x=20, y=30; boolean b; b=x>50&&y>60||x>50&&y<-60||x<-50&&y>60||x<-50&&y<-60; System.out.println(b); }
  ```
  A、true B、false C、1 D、0
24. activity对一些资源以及状态的操作保存，最好是保存在生命周期的哪个函数中进行(A)
  A、onPause() B、onCreate() C、 onResume() D、onStart()
25. Intent传递数据时，下列的数据类型哪些可以被传递(ABCD)(多选)
  A、Serializable B、charsequence C、Parcelable D、Bundle
26. android 中下列属于Intent的作用的是(C)   
    A、实现应用程序间的数据共享

　　B、是一段长的生命周期，没有用户界面的程序，可以保持应用在后台运行，而不会因为切换页面而消失

　　C、可以实现界面间的切换，可以包含动作和动作数据，连接四大组件的纽带

　　D、处理一个应用程序整体性的工作
27. 下列属于SAX解析xml文件的优点的是(B)   
    A、将整个文档树在内存中，便于操作，支持删除，修改，重新排列等多种功能

　　B、不用事先调入整个文档，占用资源少

　　C、整个文档调入内存，浪费时间和空间

　　D、不是长久驻留在内存，数据不是持久的，事件过后，若没有保存数据，数据就会

　　消失
28. 在android中使用Menu时可能需要重写的方法有(AC)。(多选)
    A、onCreateOptionsMenu(AC)

　　B、onCreateMenu()

　　C、onOptionsItemSelected()

　　D、onItemSelected()
29. 在android中使用SQLiteOpenHelper这个辅助类时，可以生成一个数据库，并可以对数 据库版本进行管理的方法可以是(AB)   
    A、getWriteableDatabase()

　　B、getReadableDatabase()

　　C、getDatabase()

　　D、getAbleDatabase()   
30. android 关于service生命周期的onCreate()和onStart()说法正确的是(AD)(多选题)   
    A、当第一次启动的时候先后调用onCreate()和onStart()方法

　　B、当第一次启动的时候只会调用onCreate()方法

　　C、如果service已经启动，将先后调用onCreate()和onStart()方法

　　D、如果service已经启动，只会执行onStart()方法，不在执行onCreate()方法
31. 下面是属于GLSurFaceView特性的是(ABC)(多选)   
    A、管理一个surface，这个surface就是一块特殊的内存，能直接排版到android的视图

　　view上。

　　B、管理一个EGL display，它能让opengl把内容渲染到上述的surface上。

　　C、让渲染器在独立的线程里运作，和UI线程分离。

　　D、可以直接从内存或者DMA等硬件接口取得图像数据   
32. 关于ContenValues类说法正确的是(A)   
    A、他和Hashtable比较类似，也是负责存储一些名值对，但是他存储的名值对当中的

　　名是String类型，而值都是基本类型

　　B、他和Hashtable比较类似，也是负责存储一些名值对，但是他存储的名值对当中的

　　名是任意类型，而值都是基本类型

　　C、他和Hashtable比较类似，也是负责存储一些名值对，但是他存储的名值对当中的

　　名，可以为空，而值都是String类型

　　D、他和Hashtable比较类似，也是负责存储一些名值对，但是他存储的名值对当中

　　的名是String类型，而值也是String类型
33. 我们都知道Hanlder是线程与Activity通信的桥梁,如果线程处理不当，你的机器

　　就会变得越慢，那么线程销毁的方法是(A)   
    A、onDestroy()

　　B、onClear()

　　C、onFinish()

　　D、onStop()
34. 下面退出Activity错误的方法是(C)   
    A、finish()

　　B、抛异常强制退出

　　C、System.exit()

　　D、onStop()
35. 下面属于android的动画分类的有(AB)(多项)
  A、Tween B、FrameC、Draw D、Animation
36. Android项目工程下面的assets目录的作用是什么   B
    A、放置应用到的图片资源。

　　B、主要放置多媒体等数据文件

　　C、放置字符串，颜色，数组等常量数据

　　D、放置一些与UI相应的布局文件，都是xml文件
37. 关于res/raw目录说法正确的是   A
    A、 这里的文件是原封不动的存储到设备上不会转换为二进制的格式

　　B、 这里的文件是原封不动的存储到设备上会转换为二进制的格式

　　C、 这里的文件最终以二进制的格式存储到指定的包中

　　D、 这里的文件最终不会以二进制的格式存储到指定的包中
38. 下列对android NDK的理解正确的是(ABCD )
    A、 NDK是一系列工具的集合

　　B、 NDK 提供了一份稳定、功能有限的 API 头文件声明。

　　C、 使“Java+C” 的开发方式终于转正，成为官方支持的开发方式

　　D、 NDK 将是 Android 平台支持 C 开发的开端
http://android.chinatarena.com/zhaopinmst/1558.html
