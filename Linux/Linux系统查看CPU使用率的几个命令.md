在linux的系统维护中，可能需要经常查看cpu使用率，分析系统整体的运行情况。而监控CPU的性能一般包括以下3点：运行队列、CPU使用率和上下文切换。

对于每一个CPU来说运行队列最好不要超过3，例如，如果是双核CPU就不要超过6。如果队列长期保持在3以上，说明任何一个进程运行时都不能马上得到cpu的响应，这时可能需要考虑升级cpu。另外满负荷运行cpu的使用率最好是user空间保持在65%～70%，system空间保持在30%，空闲保持在0%~5% 。

下面总结下查看CPU使用率常用的几个命令。

### 1、top

这个命令很常用，在第三行有显示CPU当前的使用情况。

```prettyprint
[root@li676-235 ~]# top -bn 1 -i -c
top - 14:19:51 up 138 days, 7:15, 1 user, load average: 0.20, 0.33, 0.39
Tasks: 115 total, 1 running, 114 sleeping, 0 stopped, 0 zombie
Cpu(s): 4.5%us, 3.8%sy, 0.0%ni, 91.0%id, 0.6%wa, 0.0%hi, 0.0%si, 0.0%st
Mem: 1014660k total, 880512k used, 134148k free, 264904k buffers
Swap: 262140k total, 34788k used, 227352k free, 217144k cached
PID USER PR NI VIRT RES SHR S %CPU %MEM TIME+ COMMAND 
12760 root 20 0 15084 1944 1632 R 2.0 0.2 0:00.01 top -bn 1 -i -c


root@li676-235 ~]# top -bn 1 -i -c
top - 14:19:51 up 138 days, 7:15, 1 user, load average: 0.20, 0.33, 0.39
Tasks: 115 total, 1 running, 114 sleeping, 0 stopped, 0 zombie
Cpu(s): 4.5%us, 3.8%sy, 0.0%ni, 91.0%id, 0.6%wa, 0.0%hi, 0.0%si, 0.0%st
Mem: 1014660k total, 880512k used, 134148k free, 264904k buffers
Swap: 262140k total, 34788k used, 227352k free, 217144k cached
PID USER PR NI VIRT RES SHR S %CPU %MEM TIME+ COMMAND 
12760 root 20 0 15084 1944 1632 R 2.0 0.2 0:00.01 top -bn 1 -i -c
```

如上所示，top命令可以看到总体的系统运行状态和cpu的使用率 。

%us：表示用户空间程序的cpu使用率（没有通过nice调度）

%sy：表示系统空间的cpu使用率，主要是内核程序。

%ni：表示用户空间且通过nice调度过的程序的cpu使用率。

%id：空闲cpu

%wa：cpu运行时在等待io的时间

%hi：cpu处理硬中断的数量

%si：cpu处理软中断的数量

%st：被虚拟机偷走的cpu

### 2、vmstat

之前在本博客中有介绍过[vmstat](http://www.sijitao.net/1925.html)的使用，详细使用和参数介绍参考网址：http://www.sijitao.net/1925.html 。

```prettyprint
[root@li676-235 ~]# vmstat 1 5



procs -----------memory---------- ---swap-- -----io---- --system-- -----cpu-----



 r b swpd free buff cache si so bi bo in cs us sy id wa st



 2 0 34792 68376 147688 356132 16 16 421 385 2 2 5 4 91 1 0



 3 0 34792 97368 147688 326884 0 0 0 0 133 134 15 6 79 0 0



 1 0 34792 62432 147696 360704 0 0 0 88 267 278 63 18 19 0 0



 0 0 34792 97160 147696 326904 0 0 0 0 71 82 12 4 84 0 0



 1 0 34792 56572 147696 364540 0 0 0 4 261 246 61 23 16 0 0root@li676-235 ~]# vmstat 1 5
procs -----------memory---------- ---swap-- -----io---- --system-- -----cpu-----
 r b swpd free buff cache si so bi bo in cs us sy id wa st
 2 0 34792 68376 147688 356132 16 16 421 385 2 2 5 4 91 1 0
 3 0 34792 97368 147688 326884 0 0 0 0 133 134 15 6 79 0 0
 1 0 34792 62432 147696 360704 0 0 0 88 267 278 63 18 19 0 0
 0 0 34792 97160 147696 326904 0 0 0 0 71 82 12 4 84 0 0
 1 0 34792 56572 147696 364540 0 0 0 4 261 246 61 23 16 0 0
```

### 3、sar

sar命令语法和vmstat一样。命令不存在时需要安装sysstat包，这个包很有用。

CPU使用率

例如每1秒采集一次CPU使用率，共采集5次。

```prettyprint
[root@li676-235 ~]# sar -u 1 5



Linux 3.18.5-x86_64-linode52 (li676-235) 07/20/2015 _x86_64_ (1 CPU)



02:41:25 PM CPU %user %nice %system %iowait %steal %idle



02:41:26 PM all 64.71 0.00 18.63 0.00 0.98 15.69



02:41:27 PM all 29.47 0.00 22.11 14.74 0.00 33.68



02:41:28 PM all 67.33 0.00 31.68 0.99 0.00 0.00



02:41:29 PM all 7.00 0.00 2.00 0.00 0.00 91.00



02:41:30 PM all 69.00 0.00 23.00 0.00 0.00 8.00



Average: all 47.79 0.00 19.48 3.01 0.20 29.52root@li676-235 ~]# sar -u 1 5
Linux 3.18.5-x86_64-linode52 (li676-235) 07/20/2015 _x86_64_ (1 CPU)
02:41:25 PM CPU %user %nice %system %iowait %steal %idle
02:41:26 PM all 64.71 0.00 18.63 0.00 0.98 15.69
02:41:27 PM all 29.47 0.00 22.11 14.74 0.00 33.68
02:41:28 PM all 67.33 0.00 31.68 0.99 0.00 0.00
02:41:29 PM all 7.00 0.00 2.00 0.00 0.00 91.00
02:41:30 PM all 69.00 0.00 23.00 0.00 0.00 8.00
Average: all 47.79 0.00 19.48 3.01 0.20 29.52
```

和top一样，可以看到所有cpu的使用情况。如果需要查看某颗cpu的使用可以用-P参数。例如指定显示0号cpu 的使用情况。

```prettyprint
[root@li676-235 ~]# sar -P 0 -u 1 5



Linux 3.18.5-x86_64-linode52 (li676-235) 07/20/2015 _x86_64_ (1 CPU)



02:45:14 PM CPU %user %nice %system %iowait %steal %idle



02:45:15 PM 0 44.00 0.00 52.00 4.00 0.00 0.00



02:45:16 PM 0 9.28 0.00 26.80 62.89 1.03 0.00



02:45:17 PM 0 3.06 0.00 14.29 81.63 1.02 0.00



02:45:18 PM 0 4.12 0.00 22.68 72.16 1.03 0.00



02:45:19 PM 0 4.12 0.00 22.68 72.16 1.03 0.00



Average: 0 13.09 0.00 27.81 58.28 0.82 0.00root@li676-235 ~]# sar -P 0 -u 1 5
Linux 3.18.5-x86_64-linode52 (li676-235) 07/20/2015 _x86_64_ (1 CPU)
02:45:14 PM CPU %user %nice %system %iowait %steal %idle
02:45:15 PM 0 44.00 0.00 52.00 4.00 0.00 0.00
02:45:16 PM 0 9.28 0.00 26.80 62.89 1.03 0.00
02:45:17 PM 0 3.06 0.00 14.29 81.63 1.02 0.00
02:45:18 PM 0 4.12 0.00 22.68 72.16 1.03 0.00
02:45:19 PM 0 4.12 0.00 22.68 72.16 1.03 0.00
Average: 0 13.09 0.00 27.81 58.28 0.82 0.00
```

进程队列长度和平均负载状态

例如每1秒采集一次，共采集5次。

```prettyprint
[root@li676-235 ~]# sar -q 1 5



Linux 3.18.5-x86_64-linode52 (li676-235) 07/20/2015 _x86_64_ (1 CPU)



02:48:47 PM runq-sz plist-sz ldavg-1 ldavg-5 ldavg-15



02:48:48 PM 1 133 0.34 0.43 0.41



02:48:49 PM 2 132 0.34 0.43 0.41



02:48:50 PM 1 133 0.34 0.43 0.41



02:48:51 PM 2 134 0.31 0.42 0.40



02:48:52 PM 1 133 0.31 0.42 0.40



Average: 1 133 0.33 0.43 0.41root@li676-235 ~]# sar -q 1 5
Linux 3.18.5-x86_64-linode52 (li676-235) 07/20/2015 _x86_64_ (1 CPU)
02:48:47 PM runq-sz plist-sz ldavg-1 ldavg-5 ldavg-15
02:48:48 PM 1 133 0.34 0.43 0.41
02:48:49 PM 2 132 0.34 0.43 0.41
02:48:50 PM 1 133 0.34 0.43 0.41
02:48:51 PM 2 134 0.31 0.42 0.40
02:48:52 PM 1 133 0.31 0.42 0.40
Average: 1 133 0.33 0.43 0.41
```

输出项：

runq-sz：运行队列的长度（等待运行的进程数）

plist-sz：进程列表中进程（processes）和线程（threads）的数量

ldavg-1：最后1分钟的系统平均负载（System load average）

ldavg-5：过去5分钟的系统平均负载

ldavg-15：过去15分钟的系统平均负载

进程创建的平均值和上下文切换的次数

例如每1秒收集一次，共收集5次。

```prettyprint
[root@li676-235 ~]# sar -w 1 5 



Linux 3.18.5-x86_64-linode52 (li676-235) 07/20/2015 _x86_64_ (1 CPU)



02:54:03 PM proc/s cswch/s



02:54:04 PM 1.01 156.57



02:54:05 PM 1.00 132.00



02:54:06 PM 2.00 201.00



02:54:07 PM 2.02 126.26



02:54:08 PM 2.00 114.00



Average: 1.61 145.98root@li676-235 ~]# sar -w 1 5 
Linux 3.18.5-x86_64-linode52 (li676-235) 07/20/2015 _x86_64_ (1 CPU)
02:54:03 PM proc/s cswch/s
02:54:04 PM 1.01 156.57
02:54:05 PM 1.00 132.00
02:54:06 PM 2.00 201.00
02:54:07 PM 2.02 126.26
02:54:08 PM 2.00 114.00
Average: 1.61 145.98
```

sar命令也可以获取过去指定日期的性能参数。

```prettyprint
[root@li676-235 ~]# sar -u -f /var/log/sa/sa20 



Linux 3.18.5-x86_64-linode52 (li676-235) 07/20/2015 _x86_64_ (1 CPU)



01:10:01 PM CPU %user %nice %system %iowait %steal %idle



01:20:02 PM all 25.78 0.00 8.88 3.59 0.15 61.60



01:30:01 PM all 26.06 0.00 9.96 3.33 0.10 60.55



01:40:01 PM all 25.73 0.00 9.17 3.70 0.09 61.32



01:50:01 PM all 25.70 0.00 9.50 2.79 0.12 61.89



02:00:01 PM all 26.70 0.00 9.73 2.20 0.10 61.28



02:10:01 PM all 26.16 0.00 9.56 4.34 0.11 59.82



02:20:01 PM all 25.49 0.00 9.61 2.76 0.07 62.07



02:30:01 PM all 26.47 0.00 9.94 0.64 0.30 62.65



02:40:02 PM all 27.32 0.00 10.37 3.86 0.15 58.30



02:50:02 PM all 26.98 0.00 10.38 4.56 0.13 57.95



Average: all 26.24 0.00 9.71 3.18 0.13 60.74root@li676-235 ~]# sar -u -f /var/log/sa/sa20 
Linux 3.18.5-x86_64-linode52 (li676-235) 07/20/2015 _x86_64_ (1 CPU)
01:10:01 PM CPU %user %nice %system %iowait %steal %idle
01:20:02 PM all 25.78 0.00 8.88 3.59 0.15 61.60
01:30:01 PM all 26.06 0.00 9.96 3.33 0.10 60.55
01:40:01 PM all 25.73 0.00 9.17 3.70 0.09 61.32
01:50:01 PM all 25.70 0.00 9.50 2.79 0.12 61.89
02:00:01 PM all 26.70 0.00 9.73 2.20 0.10 61.28
02:10:01 PM all 26.16 0.00 9.56 4.34 0.11 59.82
02:20:01 PM all 25.49 0.00 9.61 2.76 0.07 62.07
02:30:01 PM all 26.47 0.00 9.94 0.64 0.30 62.65
02:40:02 PM all 27.32 0.00 10.37 3.86 0.15 58.30
02:50:02 PM all 26.98 0.00 10.38 4.56 0.13 57.95
Average: all 26.24 0.00 9.71 3.18 0.13 60.74
```

### 4、mpstat

这个命令也在sysstat包中，语法类似。

例如每1秒收集一次，共5次。

```prettyprint
[root@li676-235 ~]# mpstat 1 5



Linux 3.18.5-x86_64-linode52 (li676-235) 07/20/2015 _x86_64_ (1 CPU)



03:01:18 PM CPU %usr %nice %sys %iowait %irq %soft %steal %guest %idle



03:01:19 PM all 52.53 0.00 23.23 0.00 0.00 0.00 0.00 0.00 24.24



03:01:20 PM all 21.00 0.00 4.00 0.00 0.00 0.00 0.00 0.00 75.00



03:01:21 PM all 53.00 0.00 18.00 0.00 0.00 0.00 0.00 0.00 29.00



03:01:22 PM all 26.00 0.00 3.00 0.00 0.00 0.00 0.00 0.00 71.00



03:01:23 PM all 46.00 0.00 18.00 0.00 0.00 0.00 0.00 0.00 36.00



Average: all 39.68 0.00 13.23 0.00 0.00 0.00 0.00 0.00 47.09root@li676-235 ~]# mpstat 1 5
Linux 3.18.5-x86_64-linode52 (li676-235) 07/20/2015 _x86_64_ (1 CPU)
03:01:18 PM CPU %usr %nice %sys %iowait %irq %soft %steal %guest %idle
03:01:19 PM all 52.53 0.00 23.23 0.00 0.00 0.00 0.00 0.00 24.24
03:01:20 PM all 21.00 0.00 4.00 0.00 0.00 0.00 0.00 0.00 75.00
03:01:21 PM all 53.00 0.00 18.00 0.00 0.00 0.00 0.00 0.00 29.00
03:01:22 PM all 26.00 0.00 3.00 0.00 0.00 0.00 0.00 0.00 71.00
03:01:23 PM all 46.00 0.00 18.00 0.00 0.00 0.00 0.00 0.00 36.00
Average: all 39.68 0.00 13.23 0.00 0.00 0.00 0.00 0.00 47.09
```

cpu使用情况比sar更加详细些，也可以用-P指定某颗cpu 。

### 5、iostat

这个命令主要用来查看io使用情况，也可以来查看cpu，个人感觉不常用。

```prettyprint
[root@li676-235 ~]# iostat -c 1 2



Linux 3.18.5-x86_64-linode52 (li676-235) 07/20/2015 _x86_64_ (1 CPU)



avg-cpu: %user %nice %system %iowait %steal %idle



 4.53 0.01 3.81 0.63 0.04 90.99



avg-cpu: %user %nice %system %iowait %steal %idle



 38.00 0.00 14.00 0.00 0.00 48.00root@li676-235 ~]# iostat -c 1 2
Linux 3.18.5-x86_64-linode52 (li676-235) 07/20/2015 _x86_64_ (1 CPU)
avg-cpu: %user %nice %system %iowait %steal %idle
 4.53 0.01 3.81 0.63 0.04 90.99
avg-cpu: %user %nice %system %iowait %steal %idle
 38.00 0.00 14.00 0.00 0.00 48.00
```

### 6、dstat

每秒cpu使用率情况获取

```prettyprint
[root@li676-235 ~]# dstat -c



----total-cpu-usage----



usr sys idl wai hiq siq



 5 4 91 1 0 0



 27 11 62 0 0 0



 52 11 37 0 0 0



 26 10 63 0 0 1



 50 13 37 0 0 1



 21 6 72 0 0 0root@li676-235 ~]# dstat -c
----total-cpu-usage----
usr sys idl wai hiq siq
 5 4 91 1 0 0
 27 11 62 0 0 0
 52 11 37 0 0 0
 26 10 63 0 0 1
 50 13 37 0 0 1
 21 6 72 0 0 0
```

最占cpu的进程获取

```prettyprint
[root@li676-235 ~]# dstat --top-cpu



-most-expensive-



 cpu process 



mysqld 1.5



php-fpm: pool 24



mysqld 59root@li676-235 ~]# dstat --top-cpu
-most-expensive-
 cpu process 
mysqld 1.5
php-fpm: pool 24
mysqld 59
```