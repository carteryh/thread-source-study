# thread-source-study
# 一、对象内存布局

​		在 Hotspot 虚拟机中，对象在内存中的存储布局，可以分 为三个区域:对象头(Header)、实例数据(Instance Data)、对 齐填充(Padding)。

​		![对象内存布局](/Users/chenyouhong/Desktop/study/thread-source-study/对象内存布局.png)