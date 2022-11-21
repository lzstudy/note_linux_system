观测进程和线程
===============

1. 查看某个进程中线程信息
-------------------------

.. code-block:: shell

    # 方法1 ps查看
    $ ps -T -p <pid>

    # 方法2 top
    $ top -H -p <pid>

    # 方法3 Htop

    # 方法4 查看目录
    $ ls /proc/<pid>/task
    1500/  1503/  1504/  1505/  1506/  1507/

    # 方法5 使用pstree
    $ pstree -p 1500
    main(1500)-+-{zwt0}(1503)
               |-{zwt1}(1504)
               |-{zwt2}(1505)
               |-{zwt3}(1506)
               `-{zwt4}(1507)

2. 查看线程数量
------------------

.. code-block:: c

    # 如果top不显示的情况
    ps -ef | wc -l

    # pstree
    pstree

3. 查看线程运行信息
---------------------

.. code-block:: c

    # 方法1 top

    # 方法2
    $ cat /proc/stat
    processes 1473
    procs_running 1
    procs_blocked 0


