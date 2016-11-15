# 关于
一个扫描指定的WEB二级目录是否存在的小工具。

## 原理
当 http:<b></b>//127.0.0.1/ 下存在一个目录 test 时，访问 http:<b></b>//127.0.0.1/test 时，服务器会返回状态码301或302，并重定向到 http:<b></b>//127.0.0.1/test/ 。根据此特征可判断指定目录是否存在。  
**注：该方式并不绝对可靠**  

## 场景
适用于对多个目标进行少量目录猜解。
> 1. 多线程是为多目标设置的，对单个目标不起作用；
> 2. 为了减少超时目标引的时间消耗，猜解过程中一个目标连续2次出现网络错误会终止对该目标的猜解，因而对同一目标来说，待猜解目录越多中断的概率越大。  

## 使用
python dirscan.py --targets=urls.txt --dict=common_dirs.txt --go  
python dirscan.py --target=http://target/a/ --dict=common_dirs.txt --go  
> 参数：
  * --recursive: 递归模式，当url为http://target/a/时，分别以http://target/a/、http://target/为根路径进行猜解。
  * --nogreedy: 不贪婪模式，当猜解出一个二级目录时，不再对此目标进行其它目录猜解。

