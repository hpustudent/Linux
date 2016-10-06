## -Xms2g -Xmx2g -Xmn256m -XX:SurvivorRatio=8 -XX:ParallelGCThreads=8 -XX:PermSize=512m -XX:MaxPermSize=512m -Xss256k -XX:-DisableExplicitGC -XX:+UseCompressedOops -XX:+UseConcMarkSweepGC -XX:+CMSParallelRemarkEnabled
-  -Xms:初始堆大小， 默认为物理内存的1/64
-  -Xmx:最大堆大小
-  -Xmn:新生代内存大小 ,大小为eden+2 survivor 。官方推荐配置为整个堆的3/8
-  -XX:SurvivorRatio:新生代中Eden和Survivor区域的比值，默认是8
-  -XX:PermSize,永久代的大小，默认是物理内存的1/64
-  -XX:MaxPermSize,永久带最大值，默认是物理内存的1/4
-  -Xss:每个线程的堆栈大小

## jvm相关命令
- jmap -heap +pid 查看进程堆情况
- jmap -histo +pid 查看创建系统创建实例对象
- jmap -histo:live +pid 触发full gc 统计出活对象
- jstat -gcutil +pid +interval 检测某个进程内存情况 

- 堆内存=年轻+年老+永久
- 年轻= eden+2*survivor

    - jstat -gcutil打印出值的含义
        - S0C S1C S0U S1U :survivor 0/1区 Capacity和Usage
        - EC EU: eden区Capacity和Usage
        - OC OU:年老代Capacity和Usage
        - PC PU:永久带Capacity和Usage
        - YGC YGT：年轻代GC次数和GC耗时
        - FGC FGCT：full gc次数和耗时
        - GCT：GC总耗时
