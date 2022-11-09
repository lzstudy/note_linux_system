驱动信息
=========

1. 内核模块
-------------

1.1 查看内置到内核中的模块
***************************

.. code-block:: shell

    cat /lib/modules/$(uname -r)/modules.builtin

1.2 查看手动加载的模块
***********************

.. code-block:: shell

    lsmod

1.3 查看模块信息
******************

.. code-block:: c

    # 手动加载模块
    modinfo xxx

    # 内置模块
    # 需要先到模块的路径下
    modinfo xxx.ko


