# IT
## 1.物理CPU和逻辑CPU区别

    物理CPU：服务器插槽上CPU的个数，linux系统上可根据/proc/cpuinfo中physical id判断。
    CPU核数：每个物理CPU上处理数据的芯片组的数量，如常见的双核心CPU、四核CPU。
    逻辑CPU：即总CPU核数，当存在超线程技术时，一个CPU核用起来顶两个CPU核。linux系统上可根据/proc/cpuinfo中processor 0 - n判断。
    一般条件，逻辑CPU = 物理CPU*CPU核数
    存在超线程技术，逻辑CPU = 物理CPU*CPU核数*2 
    
## 2.多线程与并行计算的区别

    (1)多核心CPU情况下，多线程可以作并行计算，因不同的线程可以在不同的CPU核运行。Linux自从2.6内核开始，就会把不同的线程交给不同的核心去处理。Windows也从NT.4.0开始支持这一特性。
    (2)单核心CPU情况下，多线程多用来降低阻塞带来的CPU资源闲置。
   
    概念：
    1）阻塞：由于进程所需资源得不到满足，并会最终导致进程被挂起。
    阻塞在什么时候发生呢？一般是等待IO操作（磁盘，数据库，网络等等）。此时如果单线程，CPU会干转不干实事（与本程序无关的事情都算不干实事，因为执行其他程序对我来说没意义），效率低下（针对这个程序而言），例如一个IO操作要耗时10毫秒，CPU就会被阻塞接近10毫秒，这是何等的浪费啊！要知道CPU是数着纳秒过日子的。
    https://www.cnblogs.com/hitwhhw09/p/4718404.html
    https://www.cnblogs.com/hitwhhw09/p/4718328.html

## 3.python的并发与并行
    

## 4.python的共享内存（shared memory)
https://docs.python.org/3/library/array.html
