# 不同指令集架构下的相同操作系统，开发软件移植适配的难度大么？系统api？glibc什么的同版本是统一的，你可以认为“系统api”是统一的

软件是基于什么平台开发的？有没有runtime？python这种不需要修改直接跑，当然库大概率要重新编译。而且库也有差异

java这种，纯java的不用重新编译直接跑，runtime/vm抹平了指令集的差异。java里面有c库的（比如广泛使用的netty）跑在armlinux上就及其麻烦了，官方不提供的话就要自己手动编译c库；另外java没有本地/网络大小端字节序问题，相当安逸

go，代码几乎不用修改，需要重新编译。可以在x86上编译arm的binary，工具链是真好用啊泪目。。。。。。

c/c++ 没有内嵌汇编的话一般重新编译就行，一个要注意的是字节序，当然arm和x86都是小端字节序可以忽略

上层软件开发，适配不同芯片？上层软件一般不需要适配芯片，这就是操作系统内核和glibc库存在的意义

os或者编译器适配芯片要考虑的就多了，但是和上层软件几乎没关系