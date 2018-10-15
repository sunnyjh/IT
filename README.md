# IT
## 1.物理CPU和逻辑CPU区别

    物理CPU：服务器插槽上CPU的个数，linux系统上可根据/proc/cpuinfo中physical id判断。
    CPU核数：每个物理CPU上处理数据的芯片组的数量，如常见的双核心CPU、四核CPU。
    逻辑CPU：linux系统上可根据/proc/cpuinfo中processor 0 - n判断。
    一般条件，逻辑CPU = 物理CPU*CPU核数
    存在超线程技术，逻辑CPU = 物理CPU*CPU核数*2 



## 2.线程与进程
