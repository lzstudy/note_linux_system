系统信息
========

1. 查看当前控制台使用的哪个终端
-------------------------------

.. code:: c

   # cat /proc/device-tree/chosen/bootargs
   console=ttymxc1,115200 root=/dev/mmcblk2p2 rootwait rw
