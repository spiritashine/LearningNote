$四大组件:
	Activity Service BroadcastReceiver ContentProvider

$生命周期

Activity: onCreate() onStart() onResume() onPause() onStop() onRestart() onDestroy()

Fragemnt: onAttach() onCreate() onCreateView() onViewCreated() onActivityCreated() onStart() onResume() onPause() onStop() onDestroyView() onDestroy() onDetach()

I/===FirstFragment====: onAttach: 
I/===FirstFragment====: onCreate: 
I/===FirstFragment====: onCreateView: 
I/===FirstFragment====: onViewCreated: 
I/===MainActivity===: onCreate: 
I/===FirstFragment====: onActivityCreated: 
I/===FirstFragment====: onStart: 
I/===MainActivity===: onStart: 
I/===MainActivity===: onResume: 
I/===FirstFragment====: onResume: 
I/===FirstFragment====: onPause: 
I/===MainActivity===: onPause: 
I/===FirstFragment====: onStop: 
I/===MainActivity===: onStop: 
I/===MainActivity===: onRestart: 
I/===FirstFragment====: onStart: 
I/===MainActivity===: onStart: 
I/===MainActivity===: onResume: 
I/===FirstFragment====: onResume: 
I/===FirstFragment====: onPause: 
I/===MainActivity===: onPause: 
I/===FirstFragment====: onStop: 
I/===MainActivity===: onStop: 
I/===FirstFragment====: onDestroyView: 
I/===FirstFragment====: onDestroy: 
I/===FirstFragment====: onDetach: 
I/===MainActivity===: onDestroy: 

$适配
//TODO

$兼容性
//TODO

$性能优化
	1.合理的管理内存 当界面不可见时释放内存 避免内存泄漏
	2.高性能编码优化 避免创建不必要的对象 对常量使用static final修饰符
	3.布局优化 重用布局文件 仅在需要时才加载布局

$设计模式
	1.单例模式：一个类在运行期间只能创建一个实例，提供一个全局唯一的访问这个类实例的访问点。

	2.建造者模式：将一个复杂对象的构建与表示分离，使得同样的构建过程可以创建不同的表示。Builder。具有良好的封装性。

	3.适配器模式：将一个类的接口转换成客户希望的另外一个接口，Adapter使得原本由于接口不兼容而不能一起工作的那些类可以一起工作。更好的复用性，更好的扩展性。

	4.观察者模式：定义对象间的一种一对多的依赖关系，当一个对象状态发生改变时，所有依赖于它的对象都得到通知并被自动更新。ListView notifyDataChanged();

	5.工厂模式：
			工厂方法：定义一个创建对象的接口，由子类决定要实例化的类是哪一个。
			抽象工厂：提供一个借口，用于创建相关或依赖对象的家族，不需要制定具体类。

$开发模式
	MVP:Model:处理数据,View:处理布局,Presenter:处理逻辑。
		解耦和，代码逻辑清晰，Presenter复用，方便单元测试。
	MVVM:使用DataBinding,在XML中除了逻辑。	

$网络协议：
	TCP/IP协议:应用层，传输层，网络层，数据链路层。
	http与https的区别：https采用了SSL进行加密传输。
	UDP和TCP的区别:
		TCP面向有链接的通信服务	UDP面向无连接的通信服务
		TCP提供可靠的通信传输	UDP不可靠,会丢包
		TCP保证数据顺序			UDP不保证
		TCP数据无边界			UDP有边界
		TCP速度慢				UDP速度快
		TCP面向字节流			UDP面向报文
		TCP一对一				UDP可以一对一，一对多
		TCP报头至少20字节		UDP报头8字节
		TCP有流量控制，拥塞控制	UDP没有

$内存管理：原理、内存泄露、内存溢出 ?内存泄漏的原因，如何检测？
		节制的使用Service
		当界面不可见时释放内存
		当内存紧张时释放内存
		避免在Bitmap上浪费内存
		使用优化过的数据集合
		谨慎使用抽象编程
		尽量避免使用依赖注入框架ButterKnife

$缓存
	图片三级缓存:网络，内存，本地。
		首次加载时，通过网络来获取图片，之后将图片保存至本地SD卡和内存中，
		优先访问内存中的图片缓存，若内存中没有，则加载本地SD卡中的图片。

$对称加密、非对称加密、base64
	对称加密:采用单钥密码系统的加密方法，同一个密钥可以同时用作信息的加密和解密，这种加密方法称为对称加密，也称为单密钥加密。

	非对称加密:非对称加密算法需要两个密钥来进行加密和解密，这两个秘钥是公开密钥和私有密钥。

$多线程：机制原理。 Java线程和Android线程的区别

$Handler：原理
		当调用handler.sendMessage(msg)方法发送一个Message时，
		实际上这个Message是发送到与当前线程绑定的一个MessageQueue中，
		然后与当前线程绑定的Looper将会不断的从MessageQueue中取出新的Message，
		调用msg.target.dispathMessage(msg)方法      将消息分发到与Message绑定的handler.handleMessage()方法中。

$Java：继承、多态、封装
		继承：继承是从已有类得到继承信息创建新类的过程。Java只支持单继承，子类可以重写父类的方法。增强程序的复用性。
		
		封装:把数据和操作数据的方法绑定起来，对数据的访问只能通过已定义的接口。

		多态：多态性是指允许不同子类型的对象对同一消息作出不同的响应。简单的说就是用同样的对象引用调用同样的方法但是做了不同的事情。多态性分为编译时的多态性和运行时的多态性。

$常见的数据存储方式
	SharedPreference
	内部存储
	外部存储
	数据库(SQLite)
	网络存储

$SVN以及Git版本控制工具的区别
	SVN用于局域网，Git用于广域网。

$Get和post
	Post更加安全				Get会把请求的信息放到URL的后面
	Post传输量一般无大小限制	Get不能大于2KB
	Post执行效率低				Get执行效率略高

	Get将参数拼成URL,放到header消息头里传递
	Post直接以键值对的形式放到消息体中传递
	但两者的效率差距很小很小

$项目共享：登录、分享、推送、二维码、代码管理等

$安卓5.0,6.0的新特性
	材料设计:MateraialDesign.

$支付：微信支付、支付宝支付、购物车流程
 
$地图

$即时通讯

$直播