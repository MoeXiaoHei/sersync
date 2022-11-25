sersync 介绍
sersync类似于inotify，同样用于监控，但它克服了inotify的缺点.

inotify最大的不足是会产生重复事件，或者同一个目录下多个文件的操作会产生多个事件，例如，当监控目录中有5个文件时，删除目录时会产生6个监控事件，从而导致重复调用rsync命令。比如：vim文件时，inotify会监控到临时文件的事件，但这些事件相对于rsync来说是不应该被监控的

sersync 优点：

sersync是使用c++编写，而且对linux系统文件系统产生的临时文件和重复的文件操作进行过滤，所以在结合rsync同步的时候，节省了运行时耗和网络资源。因此更快。
sersync配置很简单，其中提供了静态编译好的二进制文件和xml配置文件，直接使用即可
sersync使用多线程进行同步，尤其在同步较大文件时，能够保证多个服务器实时保持同步状态
sersync有出错处理机制，通过失败队列对出错的文件重新同步，如果仍旧失败，则按设定时长对同步失败的文件重新同步
sersync不仅可以实现实时同步，另外还自带crontab功能，只需在xml配置文件中开启，即也可以按要求隔一段时间整体同步一次，而无需再额外配置crontab功能
sersync 可以二次开发
sersync项目地址：
https://code.google.com/archive/p/sersync/

sersync下载地址：
https://code.google.com/archive/p/sersync/downloads
