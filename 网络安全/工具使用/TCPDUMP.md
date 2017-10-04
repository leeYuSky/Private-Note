## TCPDUMP 抓包

#### 抓包
> * 抓包
> 	* 默认只抓68字节
> 	* `-i`, 指定接口 ;
> 	* `-s`, 指定数据包大小, 默认大小68, `-s 0`,表示包有多大抓多大, 
> 	* `-w`, 将抓到的数据包保存到一个文件中
> 	* `-r`, 读取一个文件
> 	* `-n`, 不将ip地址显示成域名
> 	* `-A`, 以`ascii`形式将包的内容显示出来
> 	* `-X`, 以16进制的形式将包的内容显示出来
> 	* `tcpdump -i en0 -s 0 -w a.cap`
> 	* `tcpdump -A -r a.cap `
> * 抓包筛选
> 	* `tcpdump -i en0 tcp port 80`, 只抓80端口的tcp协议

#### 显示筛选
> * `tcpdump -n -r a.cap | awk '{print $3}' | sort -u`, awk 筛选某一列, sort -u 去重排序
> * `tcpdump -n src host 1.1.1.1 -r a.cap`
> * `tcpdump -n dst host 1.1.1.1 -r a.cap`
> * `tcpdump -n tcp port 80 -r a.cap`
> * `tcpdump -n -X tcp port 80 -r a.cap`