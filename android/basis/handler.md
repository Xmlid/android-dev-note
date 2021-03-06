## Handler与Thread
- [Handler深入（分析源码，手写一套Handler）](https://www.jianshu.com/p/91aa90886347)


### 1、Handler机制（重点推荐）
- [Android的Handler消息机制详解](http://www.jianshu.com/p/c21a15aec3b1)
- [[图解法结合源码]理解、记忆Handler、Looper、MessageQueue之间的关系](http://blog.csdn.net/Shenpibaipao/article/details/70214927)
- [手把手带你从源码的角度全面理解Handler、Looper、MessageQueue之间的关系](http://blog.csdn.net/yang_song_song/article/details/76212532)

> 说明：
>
> MessageQueue，流水线上的"履带"；  
Looper，履带的"驱动轮"；  
Handler，流水线上的"工人"；  
Message，流水线上的"包裹"。  
>
> 一个线程，首先进行Looper.prepare()，就可以创建出一个绑定了MessageQueue"履带"的[唯一]的Looper+MessageQueue"流水线"；然后线程可以实例化出几个Handler"工人"。线程有要处理的信息"包裹"Message了，丢给对应的Handler"工人"；这个工人判断一下这个到底是个Runnable还是Message，如果是Runnable就包装成一个Message，再"盖章"，然后丢向流水线，让它排队；不过不是，"盖完章"不多bb直接甩进流水线。一个Message"包裹"到了流水线的队首，就要被拿出来，根据刚刚盖的章，各找各妈各回各家，该上哪上哪，然后进行msg.target.diapatchMessage()->msg.target.handleMessage()拆包处理。


### 2、消息机制原理（重要）
> 有几个主要元素：  
1.Message:用来携带子线程中的数据。  
2.MessageQueue:用来存放所有子线程发来的Message。  
3.Handler:用来在子线程中发送Message，在主线程中接受Message，处理结果。  
4.Looper:是一个消息循环器，一直循环遍历MessageQueue，从MessageQueue中取一个Message，派发给Handler处理。  

##### 面试：子线程一定不能更新UI？ 
SurfaceView ：多媒体视频播放 ,可以在子线程中更新UI； Progress（进度）相关的控件：也是可以在子线程中更新Ui；审计机制：activity完全显示的时候审计机制才会去检测子线程有没有更新Ui。


### 3、Thread线程
- [JAVA多线程实现和应用总结](http://www.cnblogs.com/yezhenhan/archive/2010/01/09/2317636.html)



