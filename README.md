# beego学习
## beego.go
### initBeforeHTTPRun函数
* AddAPPStartHook 添加初始化钩子函数  
  1. sync.Once.Do() 函数只会执行一次  
  2. strings的一些用法
```
// sync.Once.Do()
var once sync.Once
for i:=0;i<3;i++{
     once.Do(a)  //只会打印一次1，因为只会执行一次
}
func a (){
    fmt.Print(1)
}
```
```
// strings
 strings.HasPrefix(ext,".")  是否已.作为前缀
 strings.Index("NLT_abc", "abc") //返回4
 strings.Index("NLT_abc", "aaa") 存在返回 -1
 strings.TrimSpace()  //去除空格
    s := " Hello 世界! "  
    ts := strings.TrimSpace(s)  
    fmt.Printf("%q\n", ts) // "Hello 世界!"  
```
* 注册Mime
* 添加默认错误
* 初始化AppConfig
  1. 文件路径问题  
  假设文件在/home/XXX/a  
  os.Args[0]获取的是相对路径，或者说，就是你使用什么命令启动的。  
  如果你用./a启动的话，args[0]就是./a，不是绝对路径。  
  如果你用./XXX/a启动的话，args[0]就是./XXX/a，不是绝对路径。  
  如果用/home/XXX/a启动，那么获取到的就是/home/XXX/a。  
  获取可执行文件的绝对路径(不包括文件名)，请用：  
  filepath.Abs(filepath.Dir(os.Args[0]))  
  返回：/home/XXX  
  补充：获取可执行文件的绝对路径（包括文件名），请用：  
  filepath.Abs(os.Args[0])  
  返回：/home/XXX/a  
  os.Getwd() //显示当前的目录  
  2. os.Getenv("abc") //获取环境变量
  3. 相关代码截取  
     ![configInit](https://source.prod-v1.nightplus.cn/075b1596a50d4b2ebd838336c7dbc001.jpg)  


   
* 初始化GlobalSession
* 添加模板

## router.go  
### 一些方法  
* path.Clean  
通过纯粹的词法处理， 返回一个等价于 path 的最短路径。 Clean 函数会根据以下规则进行迭代， 直到没有任何规则可以应用为止：  
使用单个斜杠代替多个斜杠。  
移除所有 . 路径名元素（当前目录）  
移除所有内含的 .. 路径名元素（父目录），以及先于它的非 .. 元素。  
移除所有以根路径方式存在的 .. 元素，也即是，使用 “/” 去替换路径开头的 “/..”  
* [reflect反射的一些用法](https://github.com/shadow88sky/golang-study/blob/master/reflect)
