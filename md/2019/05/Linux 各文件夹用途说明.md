> 其实我觉得如果了解 Windows 系统目录结构的话，Linux 应该很容易理解，可问题是我不理解啊~~(* ￣︿￣)，不过这个作为工作中的基础知识，还是需要储备一下，以下纯粹个人理解

**系统版本：** CentOS 7.4
出于篇幅考虑，这里只看主要的前面两级目录并且删除了部分不必要的
<table  bgcolor="#FCF8E3" ><tr bgcolor="#FCF8E3" ><td bgcolor="#FCF8E3" align="left">
<span bgcolor="#FCF8E3"  style="background-color: #FCF8E3;">
<font color="#005FFF">/</font> 根就在这~~！<br>
├── <font color="#005FFF">boot</font> ------------------- 内核及引导文件<br>
│      &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└── <font color="#005FFF">grub2</font><br>
├── <font color="#005FFF">dev</font> -------------------- 各种硬件设备的映射文件，例如 CPU 的子文件夹下的序号对应的是第几个 CPU<br>
│      &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;├── <font color="#005FFF">cpu</font><br>
├── <font color="#005FFF">etc</font> --------------------- 系统及软件安装后的配置文件大多默认存放在这下面<br>
│<br>
├── <font color="#005FFF">home</font> ------------------ 存放了系统各个非 root 用户各自的数据，每个用户数据是相互不可见的<br>
│      &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└── <font color="#005FFF">wong</font>----------- 例如这里是 wong 用户，打开终端是看到的 ‘~’ 目录就是这里了，不行可以用 pwd 命令看看<br>
│<br>
├── <font color="#005FFF">media</font> ------------------ DVD 等一些媒体信息会挂在到这里<br>
│<br>
├── <font color="#005FFF">mnt</font> --------------------- 和 media 类似，也是用来挂载的，例如添加了一个硬盘，可以用 mount 命令来挂载<br>
│      &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└── <font color="#005FFF">hgfs</font><br>
├── <font color="#005FFF">opt</font> ---------------------- 暂时没用到过，貌似一些软件会自动选择安装在这里，相当于绿色版软件安装目录<br>
│      &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└── <font color="#005FFF">rh</font><br>
├── <font color="#005FFF">proc</font> -------------------- 这里都是内存的映射文件，所以大小都是 0，并且例如每次打开 diskstats 文件都会变<br>
│<br>
├── <font color="#005FFF">root</font> -------------------- 和上面的 wong 类似，只不过由于 root 用户权限过高，不放在 home 目录下<br>
│<br>
├── <font color="#005FFF">run</font> --------------------- 顾名思义，存放各种运行时需要用到的文件，例如进程 id、文件锁等，重启会重新生成<br>
│<br>
├── <font color="green">sbin</font> -&gt; <font color="#005FFF">usr/sbin</font> ----- system binary 的意思，存放一些系统级别的程序、命令、脚本等<br>
│<br>
├── <font color="#005FFF">srv</font> --------------------- service 的意思，用于对外提供服务，例如多用户文件共享、ftp等，但貌似到现在也不太会用╮(╯▽╰)╭<br>
│<br>
├── <font color="#005FFF">sys</font> --------------------- 和 proc 目录类似，也是映射一些运行时系统设备、核心等信息，例如 CPU 等<br>
│<br>
├── <span style="background-color:#8AE234"><font color="#000000">tmp</font></span> -------------------- 临时目录，不能放重要的文件，一不小心可能会被清掉<br>
│<br>
├── <font color="#005FFF">usr</font> --------------------- unix software resource 的意思<br>
│   &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;├── <font color="#005FFF">bin</font> ------------- 存放一些普通用户级别的命令<br>
│      &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;├── <font color="#005FFF">etc</font> ------------- 和上面的 etc 类似，只是这是用户级别的<br>
│      &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;├── <font color="#005FFF">games</font><br>
│      &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;├── <font color="#005FFF">include</font> ------- 写过 C/C++ 的同学应该知道 include，这里面存放是一些软件开发及编译安装时需要用到的头文件<br>
│      &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;├── <font color="#005FFF">lib</font> ------------- 存放一些系统函数库<br>
│      &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;├── <font color="#005FFF">lib64</font> ---------- 存放一些 64 位的系统函数库<br>
│      &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;├── <font color="#005FFF">libexec</font> ------- 同样存放一些系统函数库、可执行文件等<br>
│      &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;├── <font color="#005FFF">local</font> ---------- 里面存放的东西竟然和 usr 目录非常像！看大家的建议是把软件安装在这里比较好管理，所以我也这么干了<br>
│      &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;├── <font color="#005FFF">sbin</font> ----------- 上面的 sbin 连接过来的目录就是这个<br>
│      &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;├── <font color="#005FFF">share</font> --------- 存放一些不影响系统运行的公共信息，例如文档说明等<br>
│      &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;├── <font color="#005FFF">src</font> ------------- 听大家说源代码建议放这里︿(￣︶￣)︿<br>
│<br>
└── <font color="#005FFF">var</font> --------------------- variable 的意思，存放一些经常变动的数据，例如缓存，数据库数据等<br>
    ├── <font color="#005FFF">cache</font><br>
    ├── <font color="#005FFF">crash</font><br>
    ├── <font color="#005FFF">db</font><br>
    ├── <font color="#005FFF">lib</font><br>
    ├── <font color="#005FFF">local</font><br>
    ├── <font color="green">lock</font> -&gt; <font color="#005FFF">../run/lock</font><br>
    ├── <font color="#005FFF">log</font><br>
    ├── <font color="green">mail</font> -&gt; <font color="#005FFF">spool/mail</font><br>
    ├── <font color="#005FFF">preserve</font><br>
    ├── <font color="green">run</font> -&gt; <font color="#005FFF">../run</font><br>
    ├── <span style="background-color:#8AE234"><font color="#000000">tmp</font></span><br>
</pre>
</td></tr></table>

上面的树结构用到 tree 命令，如果有兴趣的话可以看看
安装：
```shell
yum install tree -y
```
执行：

```shell
# '/'    从根目录开始输出
# -d     只输出目录
# -L 2   限制目录层级
# -C     输出彩色字体
tree / -d -L 2 -C
```
---
下面是在学习查资料的时候摘抄下来的，更加详细和帮助理解，from《鸟哥的Linux私房菜》
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190526152417117.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L29jcDExNA==,size_16,color_FFFFFF,t_70)![在这里插入图片描述](https://img-blog.csdnimg.cn/20190526152428451.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L29jcDExNA==,size_16,color_FFFFFF,t_70)
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190526152447106.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L29jcDExNA==,size_16,color_FFFFFF,t_70)
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190526152500769.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L29jcDExNA==,size_16,color_FFFFFF,t_70)
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190526152510911.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L29jcDExNA==,size_16,color_FFFFFF,t_70)
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190526152524307.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L29jcDExNA==,size_16,color_FFFFFF,t_70)
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190526152543401.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L29jcDExNA==,size_16,color_FFFFFF,t_70)还有一张图
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190526152834608.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L29jcDExNA==,size_16,color_FFFFFF,t_70)
