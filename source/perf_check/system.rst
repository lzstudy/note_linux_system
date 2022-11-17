系统性能
==========

上下文切换次数、缺页次数、分支预测效率

================= =====================================================================================
cpu-clock         CPU利用率, 该值越高, 说明程序大多事件花费在CPU计算上, 而非IO, 一个核最大利用率是1
context-switches  进程切换次数, 尽量避免进程的频繁切换
cpu-migrations    表示进程 t1 运行过程中发生了多少次 CPU 迁移，即被调度器从一个 CPU 转移到另外一个 CPU
cycles            处理器时钟, 一条机制指定运行多少个cycles
instructions      指令数目
branches          分支命中次数
branch-misses     分支失误次数
================= =====================================================================================

1. 整体系统检测
------------------

.. code-block:: shell

    $ perf stat

    Performance counter stats for 'system wide':

          20919.02 msec cpu-clock                 #    3.994 CPUs utilized          
               762      context-switches          #    0.036 K/sec                  
                 0      cpu-migrations            #    0.000 K/sec                  
                 0      page-faults               #    0.000 K/sec                  
          96557689      cycles                    #    0.005 GHz                    
          63482121      instructions              #    0.66  insn per cycle         
           9636398      branches                  #    0.461 M/sec                  
            641448      branch-misses             #    6.66% of all branches        

       5.238021625 seconds time elapsed


2. 指定线程检测
-----------------

.. code-block:: c

    # 启动某个程序
    perf stat ./a.out

    # 附着在某个pid上
    $ perf stat -p pid -d

    # 只查看某个性能
    $ perf stat -p 19736 -e L1-dcache-loads

