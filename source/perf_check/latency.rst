延时检测
===============

顶点采样

1. 采样最耗费时钟的函数
--------------------------

perf sched record sleep 10
perf sched latency --sort max

观测max delay, 如果延时过大, 说明调度有问题