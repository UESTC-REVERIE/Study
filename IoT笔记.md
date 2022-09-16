[TOC]



## IoT笔记

------



### 计算机网络中的一些名词

1. DoS：Denial of Service拒绝服务攻击
2. DDoS：Distributed Denial of Service分布式拒绝服务攻击
3. Mirai Botnet：被捕获的用于发起攻击的物联网设备
4. Mirai:恶意软件，能够感染智能设备，将其转变为远程控制的机器人或“僵尸”并祖成网络
5. Three Interaction Protocol：三次握手协议
6. TCPDUMP：网络分析工具
7. 彩虹表：Miral Botnet 密码本

------

## 关于shodan

### 控制台初始化shodan

1. Init:

   1. 关闭网络代理
   2. pip install shodan
   3. init shodan <API>

2. API指令：

   1. 返回搜索数量：

      shodan cout "搜索条件"

   2. 返回指定结果：

      shodan search --fields [各种信息，如：ip_str,port,org,hostnames] "搜索条件"

   3. 下载指定内容的搜索结果

      shodan download result "搜索条件"

   4. 解析文件，获得搜索结果

      shodan parse --fields [想要获取的信息] --separator , result.json.gz

   5. 搜索指定IP的信息

      shodan host [IP]

ps:通过URL获得IP地址：
命令行输入nslookup，再输入URL地址

------

### shodan常用搜索语法

1. 限定国家和城市
   限定国家country:"CN"
   限定城市city:"ShangHai"
   
2. 限定主机名或域名
   hostname:.org
   hostname:"google"
   hostname:baidu.com
   
3. 限定组织或机构
   org:"alibaba"
   
4. 限定系统OS版本
   os:"Windows Server 2008 R2"
   os:"Windows 7 or 8"
   os:"Linux 2.6.x"
   
5. 限定端口
   port:22
   port:80

6. 指定网段
   net:"59.56.19.0/24"

7. 指定使用的软件或产品
   product:"Apache httpd"
   product:"nginx"
   product:"Microsoft IIS httpd"
   product:"mysql"

8. ------
   
   指定CVE漏洞编号
   vuln:"CVE-2014-0723"
   
9. 指定网页内容
   http.html:"hello world"

10. 指定网页标题
    http.title:"hello"

11. 指定返回响应码
    http.status:200

12. 指定返回中的server类型
    http.server:Apache/2.4.7
    http.server:PHP
    
13. 指定地理位置
    geo:"31.25,121.44"

14. 指定ISP（网络服务）供应商
    isp:"China Telecom"

for example:
ssh default password
ssh default password country:"JP"
FTP anon successful

------

### 控制台指令

1. 查询计算机IP地址：ipconfig

      1. IPv4 地址 . . . . . . . . . . . . : 192.168.31.8
         1. IP地址有IPv4和IPv6 两大类，使用的绝大多数的IP地址是其中的IPv4地址。一个IPv4地址可以分为网络地址和主机地址两部分，其中网络地址可以使用如下形式描述：192.168.0.0/16，其中斜线后的数字表示网络地址部分的长度是16位，这对应2个字节，即网络地址部分是192.168.0.0。
      2. 子网掩码  . . . . . . . . . . . . : 255.255.255.0
         1. ------
         
            用来指明一个[IP地址](https://baike.baidu.com/item/IP地址)的哪些位标识的是[主机](https://baike.baidu.com/item/主机/455151)所在的子网，以及哪些位标识的是主机的位掩码。子网掩码不能单独存在，它必须结合IP地址一起使用。左边是网络位，用二进制数字“1”表示，1的数目等于网络位的长度；右边是主机位，用二进制数字“0”表示，0的数目等于主机位的长度。本机IP+子网掩码为：192.168.31.8/24
      3. 默认网关. . . . . . . . . . . . . : 192.168.31.1

2. 

------

### 计算机网络

1. TCP/IP协议栈
   1. 定义了通讯实体之间：即网络中各层（应用层、传输层、网络层、链路层和物理层）协议的总和，控制信息的意义、交换报文的格式和顺序、事件发生的顺序(语义、语法和时序)
2. TCP/IP应用层
3. TCP/IP传输层
4. TCP/IP网络层：
   1. 点分十进制记法
   2. IP地址分为两个部分：网络地址（同一网络地址传出的信号可被相互接受（广播域））、主机地址（在某个网络地址中的具体位置）
5. 

------

### VirualBox虚拟机

1. 前言：使用管理员身份运行、导入虚拟机

2. 开启给终端使用指令：
   1. 查询IP地址：ifconfig
   2. 配置虚拟机的IP地址：ifconfig eth0 [IP+子网掩码]
   3. 通过ssh连入树莓派：

3. nmap -sC -sV -oA mirai 172.16.40.173 扫描寻找漏洞指令

4. 添加或删除用户：

   - sudo adduser [用户名] [组名]
   - sudo deluser [用户名]

5. 查看账户：

   - 查看所有账户：cat /etc/passed
   - 查看现在活跃的账户：w

6. 编辑位于 /etc/ssh 目录中的 sshd_config 文件，限制允许使用 SSH 访问此设备的用户

   - sudo nano /etc/ssh/sshd_config

   - 在sshd_config文件末尾添加以下内容：

       AllowUsers kingbob （允许访问的账户）或者DenyUsers kevin（限制访问的对象）  

7. 

------

ls -l获取的文件信息

![ls -l获取的文件信息](https://img-blog.csdnimg.cn/20210206190527133.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2xpYW93ZW54aW9uZw==,size_16,color_FFFFFF,t_70#pic_center)

![image-20220608195418937](C:\Users\REVERIE\AppData\Roaming\Typora\typora-user-images\image-20220608195418937.png)

**理解chroot和qemu的使用概念**

