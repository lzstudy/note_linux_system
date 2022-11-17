定位热点函数
===============

1. 定位原理
-------------

#. 定位关键的进程/线程(top, pidstat)
#. 定位热点函数(perf)

2. 采样最耗费时钟的函数
--------------------------

2.1 基本观测
****************

.. code-block:: c

    # 采样数据
    perf record -e cpu-clock ./a.out

    # 汇报
    perf report

2.2 详细观测
***************

.. code-block:: c

    # 采样数据
    perf record -e cpu-clock -g ./a.out

    # 汇报
    perf report -g

2.3 使用top观测
****************

.. code-block:: c

    perf top -g -p pid
