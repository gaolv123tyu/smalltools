这个仓库用于存放我平时因工作需要而写的一些小工具，一般每个东西都比较小。采用每个分支存放一个工具的方法分隔各工具代码。 
一、本软件为绿色软件，解压即可以执行  
二、本目录下初始共有三个文件 webmonitor.exe、urls.txt、config.txt 及一个文件夹log  
其中monpage为主程序，在shell下执行就可以；urls.txt为要监控的url地址列表，一个url一行，如果该url含有动态参数 在url后使用~符号后跟过滤用正则表达式过滤动态参数  
config.txt为网页发生变更时需要发送邮件的配置文件，其中第一行配置发送服务器信息，依次为smtp服务器地址，端口号,用户名,密码,各参数用逗号分隔  
第二行开始为接收邮箱的地址列表，一个邮箱一行  
三、根据监控情况的不同可能会在log文件夹下生成如下文件  
1、curl文件：如果进行监控准备时发现有网页前后两次读取的网页不一致，该网页的url地址会保存于这个文件  
2、oldpages文件：如果进行监控准备时发现有网页前后两次读取的网页不一致，该网页第一次读取的的内容会保存于这个文件，如果有多个不一致的网页会一并保存  
3、nowpages文件：如果进行监控准备时发现有网页前后两次读取的网页不一致，该网页第二次读取的的内容会保存于这个文件，如果有多个不一致的网页会一并保存  
4、change文件：如果监控的时候发现有网页改变了，发生改变的网页的url 和发现网页改变的时间会记录在这个文件里，别外程序的启动时间也会存入该文件  
5、old.html文件：如果监控中发现某个网页发生了变化，则该网页的URL地址、发现变化的时间、变化前的内容会写入该文件  
6、now.html文件：如果监控中发现某个网页发生了变化，则该网页的URL地址、发现变化的时间、变化后的内容会写入该文件  
  
四、如何使用  
1、首先把需要监控的网页的url地址保存到urls.txt文件里，一个url一行。  
2、配置邮箱配置文件config.txt  
3、启动程序进行监控准备，如果存在有动态参数的网页，程序会退出  
4、用文件比较工具查看oldpages.txt和nowpages.txt文件的不同之处，并写出过滤动态参数的正则表达式用~符号和url地址分隔保存到urls.txt文件的对应url后面  
5、再次启动监控程序，如果过滤条件合适，程序在完成监控准备后会自动进入监控状态  
6、如果在监控时发现有网页内容发生变更，程序会发邮件给config.txt文件配置的接收邮箱（可多个）  
7、中断监控程序，确认网页内容变动的合法性后，再次启动监控程序，如果过滤条件合适，程序在完成监控准备后会自动进入井控状态  
8、程序进行监控状态后会一直运行，要中断程序请使用ctrl+c 退出监控程序  
  
注意：config.txt中的邮箱配置内容在程序运行的时候是可以动态修改的，修改的时候一次性修改正确再保存  
如果监控时网页无法打开，会发邮件提醒，如果后面网页又可以打开，会再次发邮件提醒  
如果网页发生变动，会发邮件提醒，但同时会把变动后的网页做为基准网页继续监控，所以收到网页变动的邮件后要及时处理。  
