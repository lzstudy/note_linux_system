系统调用
========

1. 介绍
-------

系统调用是一种特殊的异常，通常归于同步异。它是通过SVC指令触发的，异常处理程序可以
从异常状态寄存器(ESR)中得到SVC指令使用的立即数。定义系统用 ``SYSCALL_DEFINEX``, 其中
X表示的是参数个数...

1.1 系统调用宏展开过程
**********************

.. code:: c

   #define SYSCALL_DEFINEX(name, ...)   SYSCALL_DEFINEX(1, _##name, __VA_ARG__)
      #define SYSCALL_DEFINEX(x, sname, ...)   __SYSCALL_DEFINEX(x, sname, __VA_ARGS__)
         #define __SYSCALL_DEFINEX(x, name, ...)
            asmlinkage long sys##name(__SC_DECL##x(__VA_ARGS__)); ...
