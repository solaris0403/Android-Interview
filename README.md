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
  MVC(Model_view_controller)” 模型_视图_控制器”。 MVC应用程序总是由这三个部分组成。Event(事件)导致Controller改变Model或View，或者同时改变两者。只要 Controller改变了Models的数据或者属性，所有依赖的View都会自动更新。类似的，只要Controller改变了View，View会从潜在的Model中获取数据来刷新自己。  
***
### View重绘和内存泄露
9. View的刷新  
  在需要刷新的地方，使用Handler.sendmessage发送消息，然后在Handler的getmessage里面执行invalidate或者invalidate  
10. GC内存泄露  
  出现情况：  
  * 数据库的cursor没有关闭。
  * 构造adapter时，没有使用缓存contentview。衍生listview的优化问题：减少创建view的对象，充分使用contentview，可以使用一静态类来优化处理getview的过程。
  * Bitmap对象不使用时采用recycle()释放内存。
  * activity中的对象的生命周期大于activity。
![http://www.wtoutiao.com/a/1278539.html]
