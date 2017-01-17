# netty源码理解 #
	netty读取基本原理
- 解码器继承ByteToMessageDecoder;
- 解码器把每次从channel读取到的字节数据存入到内部的累加缓存buffer;
- 调用子类的解码方法进行解码; 
- 两种情况: 
- 1 子类解码出了消息,调用下一个handler进行处理,然后循环解码,直到积累buffer耗尽或者无法解码出消息了,结束本次处理,等待下一次累加数据后继续解码 
- 2 子类解码器直接没有解码出消息(返回null)，结束本次处理,等待下一次累加数据后继续解码 
