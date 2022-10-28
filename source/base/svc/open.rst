open
====

1 调用流程
----------

.. code::

   # 应用层
   open(tty) -> sys_open -> SyS_open

   # 内核层
   kernel_ventry 1, sync                                [中断向量表 第三部分sync, entry.S]
     el0_sync -> el0_svc -> el0_svc_handler             [entry.S]
	    el0_svc_common                                  [syscall.c]
          invoke_syscall -> do_sys_open -> do_filp_open [open.c]
		    path_openat -> vfs_open -> do_dentry_open   [open.c]
			  chrdev_open -> filp->f_op->open           [char_dev.c]
			    tty_open                                [tty_io.c]

   # 驱动层
   tty_open -> tty_init_dev -> driver->ops->install     [tty_io.c]
     uart_install                                       [tty_core.c]
	   tty_init_termios(tty) -> tty_termios_baud_rate   [tty_io.c]
	 tty_ldisc_setup -> n_tty_open -> n_tty_set_termios
	 uart_open                                          [serial_core.c]
	   tty_port_open -> uart_port_activate              [serial_core.c]
	     uart_startup -> imx_uart_startup               [imx.c]
		  imx_uart_dma_init -> dma_request_slave_channel[imx.c]




