接口速度测试
=============

1. 基本介绍
-----------

开发时有时需要对磁盘或者flash等进行速度测试, 使用简单的dd命令即可测试性能

- 测试磁盘的读写速度
- 读速度往往会比写速度快很多


2. nor flash读写速度测试
---------------------------

.. code-block:: c

    # 测试读速度, 从/dev/xxx读取10M数据
    $ dd if=/dev/mtdblock0 of=/dev/null bs=1M count=10
    16+0 records in
    16+0 records out
    16777216 bytes (17 MB, 16 MiB) copied, 0.862374 s, 19.5 MB/s

    # 测试写速度
    $ dd if=/dev/zero of=/dev/mtdblock0 bs=1M count=10
    10+0 records in
    10+0 records out
    10485760 bytes (10 MB, 10 MiB) copied, 56.8988 s, 184 kB/s


3 TF读写速度测试
------------------

.. code-block:: c

    # 假设U盘设备为/run/media/mmcblk1p1

    # 写入测试
    $  dd if=/dev/zero of=/run/media/mmcblk1p1/test bs=1M count=50 oflag=direct

    # 读取测试
    $ dd if=/run/media/mmcblk1p1/test of=/dev/null bs=1M iflag=direct

4 emmc读写速度测试
---------------------

如果我们的设备使用的是emmc存储, 那么指定读写某个文件即可

.. code-block:: c

    # 写入测试
    $ dd if=/dev/zero of=test bs=1M count=500 conv=fsync oflag=direct
    500+0 records in
    500+0 records out
    524288000 bytes (524 MB, 500 MiB) copied, 6.2658 s, 83.7 MB/s

    # 读取测试
    $ dd if=test of=/dev/zero bs=1M iflag=direct
    500+0 records in
    500+0 records out
    524288000 bytes (524 MB, 500 MiB) copied, 2.00463 s, 262 MB/s
