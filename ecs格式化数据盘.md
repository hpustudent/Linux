1. `fdisk -l`查看是否存在数据盘

2. 创建单分区数据盘
  `fdisk /dev/vdb`对数据盘分区
  
  ```
   Command (m for help):        输入 n 创建新分区
   p   primary (0 primary, 0 extended, 4 free)：输入p创建主分区
   Partition number (1-4):      输入1分区编号
   命令(输入 m 获取帮助)：         输入wq
  ```
3. 执行`fdisk -l`可以看到创建的分区

4. 执行`mkfs.ext3 /dev/vdb1`在新分区创建文件系统

5. （建议）执行`cp /etc/fstab /etc/fstab.bak`备份 /etc/fstab

6. 执行`echo /dev/vdb1 /mnt ext3 defaults 0 0 >>/etc/fstab`向fstab中写入新分区信息

7. 执行`mount /dev/vdb1 /mnt`挂载文件系统，挂载到/mnt或者你自己指定的目录下

8. `df -h`查看文件系统
