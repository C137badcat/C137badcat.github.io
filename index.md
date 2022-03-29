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

### 配置apt命令在线安装包的源（可以配置为国内源）：  

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
