## 优化方法

### 程序流程优化

1. 多线程实现部分。Frame Thread/Tile Thread/Main Thread。后来又实现了 Postfilter Thread。
2. Film Grain 属于后处理部分，不会影响其他帧的解码。因此，可以把这一部分单独创建一个线程。
3. 减少内存 copy，dav1d 比 aom 少了很多的内存 copy 吧。
4. 

### 程序代码优化
1. 分支预测。比如一个数组a[512]，这个数组内包含的是0-512之间的随机数。每次取数组中的一个值，然后判断值是否大于 256， 进行其他操作。如果这个数组时排序好后，在从数组的第一个-第512个值，进行其他操作。第二种操作更快。
2. 局部性原理。二维数组按行取值，比按列取值，更快。LoopRestoration 中，维纳滤波有这个优化。计算机存储层级结构。例子 for (int i = 0; i < 16 i++) sum += a[i];

### 