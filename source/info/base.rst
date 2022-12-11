系统信息
=========

1 查看控制台使用的那个终端
---------------------------

.. code-block:: shell

    $ cat /proc/device-tree/chosen/bootargs
    console=ttymxc1,115200 root=/dev/mmcblk2p2 rootwait rw

2 查看系统中的设备号
---------------------

.. code-block:: shell

    cat /proc/devices


