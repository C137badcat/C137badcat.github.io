### Kali终端下的复制和粘贴

复制：使用鼠标选中内容，就可以完成复制
粘贴：移动光标到需要粘贴的位置，按下鼠标中间的滚轮，就可以粘贴

### 进入root权限

①设置root密码：  
命令：sudo passwd root  
以mk用户为例：  
![设置root密码](https://s2.loli.net/2022/03/29/zuYHqARpkdBKNMI.png)  
第一次输入的密码是mk用户的密码，第二次输入的密码和重输入的密码是给root配的密码

②进入root权限：  
以yuyi用户为例：  
此处输入的密码是之前给root配的密码  
![进入root权限](https://s2.loli.net/2022/03/29/rnUPZpKJbQkLzaB.png)  
（pwd：查看家目录，家目录变成/root说明切换成功）

### 配置apt命令在线安装包的源（可以配置为国内源）  

Kali自带的源是国外的，经常会因为网络问题，而无法安装或更新软件包，而且国外的速度很慢  
命令：vim /etc/apt/sources.list  
![配置apt](https://s2.loli.net/2022/03/29/tPzn4ByKDQxYMC8.png)

①apt update  
作用：从/etc/apt/sources.list 文件中定义的源中获取最新的软件包列表。即运行apt update 并没有更新软件，而是相当于Windows下面的检查更新，获取的是软件的状态

②apt upgrade  
③apt dist-upgrade  
![二者区别](https://s2.loli.net/2022/03/29/y5mdGKw2FJH3QtA.png)  
更新：每次更新之前，需要先运行update（获取包的一些信息，比如大小和版本号），然后才能运行upgrade和dist-upgrade（下载包），如果没有获取包的信息，那么upgrade就是无效的  

补充:  
apt和apt-get区别：  
apt-get虽然没有被弃用，但作为普通用户，应该首先使用apt，更方便使用  
apt install和apt-get install功能一样，都是安装软件包，没有区别  

![](https://s2.loli.net/2022/03/29/9lWGCSzINx8F4kK.png)  

### vim使用技巧

![](https://s2.loli.net/2022/03/29/4rRb6wTgqPJk3ln.png)  
:set nu   显示行数  
 
 不太确定的操作：  
 行号 gd    快速跳到指定行  
 shift d    快速删除  
 
 ### 查看当前使用的shell类型
 
 
 ![](https://s2.loli.net/2022/03/29/nKZfaqxO9V1QRHm.png)  
 老版本使用的是bash类型的shell，新版本使用的是zsh类型的shell  
 ![](https://s2.loli.net/2022/03/29/YpiuxagREOXnStq.png)  
 白色部分：系统中的环境变量，主要记录当前shell类型  
 
 ### 校园网等受限制的网络环境下配置Kali系统ip地址
 
 修改网卡配置文件：  
 ![](https://s2.loli.net/2022/03/29/G9gkqLDzCPeSj1U.png)  
 
 ### 配置sshd服务并使用xshell连接
 
 允许root用户登录sshd服务：  
 vim /etc/ssh/sshd_config    
 操作：把34行的"prohibit-password"改为"yes"，并把34行和39行前的"#"号删掉  
 注：  
 prohibit-password：禁止密码  
 PubkeyAuthentication：公钥身份验证，开启此项允许Xshell配置SSH密钥登录  
 
 改前：  
 ![](https://s2.loli.net/2022/03/29/P6RKu3YgqUTMspz.png)  
 改后:   
 ![](https://s2.loli.net/2022/03/29/l17daQTpZ4Mmek8.png)  
 接着重启服务（两种方式）：  
 systemctl restart ssh  
 因为是一个脚本，也可以用下面这种方式：  
 ![](https://s2.loli.net/2022/03/29/ztTNZr86UEixHPL.png)  
 注意：在Kali下是ssh，在Centos下是sshd  
 
 若不知道是什么服务，可以罗列常见服务  
 ![](https://s2.loli.net/2022/03/29/PZtpKeyaJfxTGIM.png)  
 
 设置此服务为开机自启动：  
 update-rc.d ssh enable  
 
 安装客户端：  
 
 
       
