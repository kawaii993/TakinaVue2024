# Node


# package.json
```
{ //项目名称
  //不能有空格、汉字，并且不能与npmjs.org官网的包重名
  "name": "Hello World",
  //项目版本号
  //v3.2.1
  //3 大版本 我们的代码、ui界面有颠覆性的改变
  //2 小版本 新增功能，修复bug
  //1 修复bug、缺陷 提升用户体验
  "version": "0.0.1",
  //作者
  "author": "张三",
  //项目描述，包含一些关键字、功能描述
  "description": "第一个node.js程序",
  //放简介，字符串。方便在 npm search中搜索。
  //项目的关键字，用于seo优化
  "keywords": [
  "node.js",
  "javascript"
  ],
  //指定你的代码存放的地方
  "repository": {
  "type": "git",
  "url": "https://path/to/url"
  },
  //应该要指定一个许可证，让人知道使用的权利和限制的。
  //版权信息
  "license": "MIT",
  //入口文件
  "main": "index.js",
  //可以指定工作的node的版本
  "engines": {
  "node": "0.10.x"
  },
  //项目的提交问题的url和（或）邮件地址
  "bugs": {
  "url": "http://path/to/bug",
  "email": "bug@example.com"
  },
  //贡献者
  "contributors": [
  {
  "name": "李四",
  "email": "lisi@example.com"
  }
  ],
  //快捷启动命令
  //可以通过npm run test 来执行test关键字的命令
  "scripts": {
  "start": "node index.js"
  },
  //生产依赖
  "dependencies": {
  "express": "latest",
  "mongoose": "~3.8.3",
  "handlebars-runtime": "~1.0.12",
  "express3-handlebars": "~0.5.0",
  "MD5": "~1.2.0"
  },
  //开发依赖
  "devDependencies": {
  "bower": "~1.2.8",
  "grunt": "~0.4.1",
  "grunt-contrib-concat": "~0.3.0",
  "grunt-contrib-jshint": "~0.7.2",
  "grunt-contrib-uglify": "~0.2.7",
  "grunt-contrib-clean": "~0.5.0",
  "browserify": "2.36.1",
  "grunt-browserify": "~1.3.0",
  }
}
```

# 
commonjs中require的查找机制

1. 接收一个路径作为参数
2. 接收一个包名
- 去当前文件夹下查找node_modules
- 如果找见了，去就该文件夹下找名字为包名的文件夹
- 接着在包名文件夹下找 index.js
- 找package.json 中的main属性
- 引用main的路径
- 如果当前目录没有，就依次向上级寻找
- 如果依次查找到磁盘的根目录都找不见，那表名在该磁盘下没有这个包
- 如果在本地磁盘没找见，就去找NODE_PATH中的路径

# npm常用命令
**npm -v**检测npm版本号
**下包**:npm install 包名
npm install 包名@版本号
**卸包:**npm uninstall 包名
xxx 卸载xxx。多个依赖可用空格分割。
xxx -D 卸载xxx，并将依赖信息从package.json中的devDependencies中清除。
**npm init:**创建package.json文件 锁定你包的位置 (初始化Node包的信息，会创建package.json文件)
npm init -y
一键生成package.json文件
**npm install:**一键配置清单上所有的包
npm i 包名
npm i 包名 --save
npm i 包名 --save-dev
线上环境 生产依赖 "dependencies"
npm i 包名 -D
npm i 包名 --dev
开发环境 开发依赖 "devDependencies":
**npm run 命令名:**动态命令执行 scripts (运行脚本)
**npm list/npm ls:**列出本地包 列出已安装依赖（快捷方式：ls）
**npm config ls:**包的源地址 -node/nm版本号 npm默认配置
**npm config get cache:**获取缓存路径
**npm config get prefix:**获取第三方包的路径
**先改缓存 后改路径**
**npm config set cache "D:/node "**设置缓存路径
**npm config set prefix "D:/modules"**设置第三方包的路径
**npm root **查看依赖安装路径（也就是node_modules的路径）默认查看局部安装路径。-g 查看全局安装路径。
**npm config get registry**切换淘宝源 获取npm源地址
**npm config set registry**淘宝镜像 "淘宝地址" 修改npm源为淘宝源
**npm update (-g) [package]**更新依赖 （快捷方式：up）
**npm outdated [package]**检查过期依赖 (检查包是否已经过时，此命令会列出所有已经过时的包，可以及时进行包的更新)
**npm view**查看模块的注册信息
**npm view moudleName dependencies：**查看包的依赖关系
**npm view moduleName repository.url**：查看包的源文件地址
npm view moduleName engines：查看包所依赖的Node的版本
xxx versions 列出xxx的所有版本， 如：npm view jquery versions。
xxx dependencies 列出xxx的所有依赖， 如：npm view gulp dependencies。
注意事项：如果想要查看package.json文件夹下某个标签的内容，可以使用$npm view moduleName labelName
npm search
搜索（快捷方式：find, s） xxx 搜索xxx 如：npm search jquery。
npm help xxx
查看xxx命令的帮助信息。
npm help folders
查看npm使用的所有文件夹
npm pubilsh
发包；把在一个package.json文件中定义的模块发布到npmjs.org注册表
npm unpublish myModule
取消发包；取消发布您已发布到注册表的一个模块（在某些情况下，还需使用 --force 选项）
允许您在存储库中添加、删除包和列出包的所有者
npm add  myModule
npm rm  myModule
npm ls myModule
npm whoami
用户名：（根据指定注册表模块）打印用户名
npm owner
一个包的作者
npm adduser
将用户信息添加到当前的开发环境
npm login
登录；等同于adduser(将用户信息添加到当前的开发环境)
npm logout
将用户信息从当前的开发环境中清除
npm pack
把在一个package.json文件中定义的模块封装成.tgz文件
npm rebuild moduleName
npm link
npm link的用途可以用于自己本地开发的模块调试过程 避免每次都publish npm包，然后安装调试。
这时候就可以先将该模块link到全局，然后在需要调试的项目里，将该命令链接到本地node_modules下面

# 镜像源
官方镜像源 [https://registry.npmjs.org/](https://registry.npmjs.org/)
淘宝镜像源 [https://registry.npm.taobao.org/](https://registry.npm.taobao.org/)

# 内置模块

## fs

引入：const fs=require(fs)
api:

--加Sync的为同步方式

--异步方式最后一个参数为回调函数 必须传

src--源文件路径

dist--目标文件路径

data--获取到的数据

cb--回调函数
1.读取文件

异步方式：

fs.readFile(src,"utf8"(err,data)=>{
if(err){
throw err;
}

```
    //data:读取的内容 buffer流
}) //返回undefined
```

同步方式:

fs.readFileSync(src)
//返回读取的内容。数据类型为buffer流，是二进制表达方式，需要res.tostring()或者传入第二个参数'uft-8'；
2.写入文件

异步方式:

fs.writeFile(dist,data，err=>{});
同步方式：

fs.writeFileSync(dist,data)
3.判断文件是否存在

fs.esistsSync(src)//返回布尔类型
4.查看文件信息 唯一的文件、文件夹都适用的

fs.statSync(src) //返回一个对象
fs.statSync(src).size//返回查看的文件/文件夹的大小
fs.statSync(src).isFile()//返回查看的路径是不是文件
fs.statSync(src).isDirectory()//返回查看的路径是不是文件夹
5.读取大文件==>流的方式

fs.createReadStream(src)
6.写入大文件

fs.createWriteStream(dist)
7.大文件拷贝

let rs=fs.createReadStream(src)
let ws=fs.createWriteStream(dist)
rs.pipe(ws)
8.读取文件夹

//异步方式：
fs.readdir(src,cb)
//同步方式：
fs.readdirSync(src)//返回一个由文件夹里的每一项文件名组成的数组；
9.创建文件夹

fs.mkdirSync(dist)
10.删除文件

fs.unlinkSync(src)
11.删除空文件夹

fs.rmdirSync(src)
12. copy

//同步
fs.copyFileSync(源文件，目标文件)
//异步
fs.copyFile(源文件，目标文件，(err) => {
if (err) throw err;
})

## url 模块

## path模块

path.dirname() 方法返回 path 的目录名
path.dirname('/foo/bar/baz/asdf/quux');
// 返回: '/foo/bar/baz/asdf'
path.extname()
方法返回 path 的扩展名，从最后一次出现 .（句点）字符到 path 最后一部分的字符串结束。
如果在 path 的最后一部分中没有 . ，或者如果 path 的基本名称（参阅 path.basename()）除了第一个字符以外没有 .，则返回空字符串。
path.extname('index.html');
// 返回: '.html'

path.extname('index.coffee.md');
// 返回: '.md'

path.extname('index.');
// 返回: '.'

path.extname('index');
// 返回: ''

path.extname('.index');
// 返回: ''

path.extname('.index.md');
// 返回: '.md'

## 
http 模块


## process
process api
process.arch()     返回当前的系统类型，一个操作系统CPU架构的字符串（系统的处理器），x64代表64位，x84代表32位
process.platform   返回当前系统的平台  分window和苹果
process.events      事件对象
process.argv()       返回一个数组,获取的命令行的参数
process.argv0       获取nodejs启动时传入的argv[0]的原始值只读副本
process.config      返回一个js对象，此对象描述了用于编译当前nodejs执行程序时涉及的配置项信息
process.cpuUsage 获取到当前进程用的CPU时间和系统CPU时间的对象
process..memoryUsage()  返回内存使用情况
process.cwd()        返回nodejs进程的当前工作目录//路径
process.version     返回node的版本
process.pid()         当前的进程号
process.ppid()         当前的进程号
process.versions    返回nodejs及其依赖项的版本，是一个对象
process.title          返回命令行参数
process.env           返回系统的环境变量，指向当前shell的环境变量
process.execPath   返回运行当前进程的可执行文件的绝对路径
process.stderr        输出错误
process.stderr.write( str )
process.stdout       命令行的输出
console.log = function(d) {
process.stdout.write(d + '\n');
};
[//实现了console.log](//xn--console-rp4k968guk4c.log)()
process.stdin         命令行的输入
//会在使用 ctrl + c的时候触发次信号：        process.stdin.resume();
//使用Control+C键，可以触发SIGINT信号
process.on('SIGINT', function() {
console.log('收到SIGINT信号，按Control+D键可以退出进程');
});
process.nexrTick    讲一个回调函数放在下次事件循环的顶部  效果更好，描述更准确
process.nextTick(function () {
console.log('Next event loop!');
});
process.exit()        退出当前进程
process.on('exit',function(code){
fs.writeFileSync('/tmp/myfile','this must be saves on exit')
})//进程正常退出，其退出码code为0;非正常退出的码为1
process.abort()    触发abort事件，会让nodejs进程立即结束，并生成一个core文件
process.getgid()  获取进程的GID，GID为Gropld即组ID，用来标识用户组的唯一标识符
process.setgid()   设置进程的GID
process.getuid()   获取用户的ID
process.setuid(id) 设置用户的ID
process.initgroups(user,extra_group)    初始化group分组访问列表
process.kill           向指定进程pid发送一个信息singnal
process.hrtime      返回当前的好精度事件
process.uptime     返回node程序已经运行的描述
process.umask      设置或者读取进程文件的权限掩码
process.chdir        改变工作目录，process.cwd()查看目录切换是否成功，process.chdir('/home/bbb')
process.uncaughtException   当前进程抛出一个没有被捕捉的意外时，会触发uncaughtException事件。
process.on('uncaughtException', function (err) {
console.error('An uncaught error occurred!');
console.error(err.stack);
});
//一个未定义的方法，用来制造异常
//nonexistentFunc();
process.on('end',(code)=>{//code:程序退出码}
process.mainModule   指向启动脚本的模块

# 子进程
创建子进程
exec/execFile 　　exec(command, options, callback) 和 execFile(file, args, options, callback) 比较类似，会使用一个 Buffer 来存储进程执行后的标准输出结果，他们可以一次性在callback里面获取到。不太适合数据量大的场景。 　　另外，exec会首先创建一个新的shell进程出来，然后执行command； execFile则是直接将可执行的file创建为新进程执行。 所以，execfile 会比 exec 高效一些（后者多了一个shell步骤，前者是直接拿到execfile就执行了）。 　　exec比较适合来执行 shell 命令， 然后获取输出（比如： exec('ps aux | grep "node" ')），但是 execFile 没有这么实用， 因为它实际上只接受了一个可执行的命令，然后执行（没法使用shell里面的管道之类的东西）。
spawn 　　spawn(command, args, options)适合用在进程的输入、输出数据量比较大的情况（因为它支持steam的方式，而刚才的exec/execFile都是Buffer，而不支持stream的方式）， 可以用于任何命令。
fork 　　fork(modulePath, args, options)实际上是spawn的一个“特例”， 会创建一个新的V8实例。新创建的进程只能用来运行node脚本，不能运行其他命令。
nodejs提供的内置模块 child-process 1.child_process.spawn(,[...args String],[options Object])

command  要运行的命令。

args <string[]> 字符串参数的列表。

options 

cwd  子进程的当前工作目录。
env 

//　exec(command, options, callback)
exec(
"copy 1.txt 2.txt",// 执行的命令
{
cwd:__dirname
},//配置项
(err)=>{
console.log(err,err.code,err.signal)
})

//spawn(command, args, options)
const p = spawn(
'node', // 需要执行的命令
["child.js"], // 传递的参数
{}
);

//execFile(file, args, options, callback)
execFile("node",["--version"],(err,stdout,stderr)=>{
if(err) return console.log(err);
console.log(stdout)
})

//fork(modulePath, args, options)
//直接传路径
//衍生新的 Node.js 进程衍生 返回childeProcess 对象
const worker=fork("server/server.js")

demo1

执行Dos命令

const {exec,spawn}=require("child_process")
//复制文件
//使用child_process.exec() 执行windows的dos命令
exec("copy 1.txt 2.txt",{
cwd:__dirname
},(err)=>{
console.log(err)
})

//删除文件
exec("DEL 1.txt", {
cwd: __dirname
}, (err) => {
console.log(err)
})

//移动文件
exec("mv ./1.txt ./move",(err)=>{
console.log(err)
})

//复制目录
exec("cp -r move move2",{
cwd:__dirname
},(err)=>{
console.log(err)
})

//使用child_process.spawn() 执行windows的dos命令
//ls 显示当前路径下的文件名
const showInfo=spawn("ls")
//通过子进程的实例对象，监听执行子进程的输出内容，并且在主进程中打印出来
showInfo.stdout.on("data",data=>{
console.log(data.toString())
})
demo2

将异步函数转为promise的函数

const {execFile,exec}=require("child_process")
//将异步函数转为promise的函数
const {promisify}=require("util")

const _execFile=promisify(require("child_process").execFile)

_execFile("node",["--version"]).then(res=>{
[//console.log](//console.log)(res)//{stdout:"",stderr:""}
console.log(res.stdout)
[//console.log](//console.log)(res.stderr)
}).catch(err=>{
console.log(err)
})

execFile("node",["--version"],(err,stdout,stderr)=>{
if(err) return console.log(err);
console.log(stdout)
})
exec("node --version",(err,stdout,stderr)=>{
if(err) return console.log(err);
console.log(stdout)
})
demo3

通过子进程spawn创建多个服务

守护进程

const { exec, spawn, fork ,execFile} = require("child_process")
let count=1;
// const worker=exec("node ./server.js",(err,stdout,stderr)=>{
//     console.log(stdout)
// })
// worker.stdout.on("data",(data)=>{
//     console.log(data)
// })

//封装起服务函数
//通过子进程exec创建多个服务
// function server(cmd) {
//     //创建线程
//     const worker = exec(cmd, (error, stdout, stderr) => {
//     if (error) return console.log(error);
//         console.log(stdout)
//         [//console.log](//console.log)(stderr)
//     })
//     worker.stdout.on("data", (data) => {
//         console.log(data)
//     })
//     //守护进程
//     worker.on("exit",(code,signal)=>{
//         if(code===1){
//             //if(count>=3) return console.log("please try again later");
//             count++
//             setTimeout(()=>{
//                 server(cmd)
//             },1000)

//         }
//     })
// }
// const serverList=["server","server1"]
// serverList.forEach(serverName=>{
//     server(`node ./server/${serverName}.js`)
// })

//通过子进程execFile创建多个服务
// function server(cmd){
//     const worker=execFile("node",[cmd],(error,stdout,stderr)=>{
//         if (error) return console.log(error);
//         console.log(stdout)
//     })
//     worker.stdout.on("data",data=>{
//         console.log(data.toString())
//     })
//     worker.on("exit",code=>{
//         console.log(code)
//         if(code===1){
//             setTimeout(()=>{
//                 server(cmd)
//             },3000)

//         }
//     })
// }
// let serverList=["server","server1"]
// serverList.forEach(serverName=>{
//     server(`server/${serverName}.js`)
// })

//通过子进程spawn创建多个服务

function server(cmd) {
//创建线程
const worker = spawn("node", [cmd])
worker.stdout.on("data", (data) => {
console.log(data.toString())
})
//守护进程
worker.on("exit", (code,signal) => {
if (code === 1) {
if (count >= 3) return console.log("please try again later");
count++
console.log("error")
setTimeout(() => {
console.log("error")
server(cmd)
}, 3000)
}
})
}
const serverList = ["server", "server1"]
serverList.forEach(serverName => {
server(`server/${serverName}.js`)
})

// //通过子进程fork创建多个服务

// function server(cmd) {
//     //创建线程
//     const worker = fork(cmd)
//     worker.on("data", (data) => {
//         console.log(data.toString())
//     })
//     //守护进程
//     worker.on("exit",code=>{
//         if(code===1){
//             if(count>=3) return console.log("please try again later");
//             count++
//             setTimeout(()=>{
//                 server(cmd)
//             },3000)
//         }
//     })
// }
// const serverList=["server","server1"]
// serverList.forEach(serverName=>{
//     server(`./server/${serverName}.js`)
// })
express

基于node.js平台，快速、开发、极简的web开发框架
koa


# koa快速上手

Koa 学习总结（链接）
下包

cnpm i --save koa koa-router koa-views koa-bodyparser
const Koa=require("koa")
const fs=require("fs")
const path=require("path")
const koaRouter=require("koa-router")
const koaViews=require("koa-views")

const app=new Koa()
const router=new koaRouter()
const views=path.join(__dirname,"./views")
//将ejs挂载到全局
app.use(
koaViews(views,{
extension:"ejs"
})
)
router.get("/api",ctx=>{
//请求接口
ctx.body=[
{
name:"zs",
age:14
}
]
})
router.get("/home",async ctx=>{
//引入静态页面
const homePage=fs.readFileSync(path.join(__dirname,"./views/home.html"))
ctx.body=homePage.toString()
//await ctx.render("home")
})
router.get("/login",async ctx=>{
//渲染ejs页面
await ctx.render("login")
})
router.get("/main",async ctx=>{
await ctx.render("main")
})
//使用路由页面
app.use(router.routes())
app.use(router.allowedMethods())

app.listen(9090,()=>{
console.log("9090端口已开启")
})

# 
分模块 koa

koa目录结构:

save.js 主进程
server目录
app.js 子进程
router目录
index.js
user.js 分的模块 可以更改
class.js 分的模块 可以更改
config目录
index.js 数据的基本配置参数
controller目录
mysql.js 封装数据库方法
views
login.ejs静态页面
package.json
node_modules
save.js主进程

const cpuNum = require("os").cpus().length //cpu的数量
const cluster = require("cluster")
const logs=[]//保存日志列表
//主进程
if (cluster.isMaster) {
let worker;
//根据CPU的数量创建子进程
for(let i = 0; i < cpuNum; i++) {
//子进程
worker=cluster.fork()
//监听子进程传递的任务 并保存到日志列表中
worker.on("message",data=>{
let {task}=data
logs.push(task)
console.log(logs)
})
}
//子进程监听地址端口号
worker.on("listening",(address)=>{
console.log(address.port)
})
} else {
//引入子进程
require("./server/app")
[//console.log](//console.log)(process.id)
}

app.js 子进程

const Koa = require("koa")
const bodyParser = require("koa-bodyparser")
const koaViews=require("koa-views")
const static=require("koa-static")
const PORT = process.env.PORT || 3000;
const app = new Koa()
const staticPath="./views"
const views=path.join(__dirname,"./views")
//加载静态资源文件
app.use(static(path.join(__dirname,staticPath)))
//引入主路由模块
const indexRouter = require("./server/router/index")
//使用ejs模板引擎
app.use(
koaViews(views,{
extension:"ejs"
})
)

/**

- 引入了body-parser模块处理请求体,
- 模块会处理application/x-www-form-urlencoded、application/json两种格式的请求体。
- 经过这个中间件后，就可以在所有路由处理器的req.body中访问请求参数
- 位置必须在开启路由的上面
*/
app.use(bodyParser())
//启动路由
//在app中注册根路由
app.use(indexRouter.routes(), indexRouter.allowedMethods())

/*

- router.allowedMethods()作用： 这是官方文档的推荐用法,我们可以
- 看到 router.allowedMethods()用在了路由匹配 router.routes()之后,所以在当所有
- 路由中间件最后调用.此时根据 ctx.status 设置 response 响应头
*/

app.listen(PORT, () => {
console.log("port is" + PORT)
})
get请求获取参数

/*在 koa2 中 GET 传值通过 request 接收，但是接收的方法有两种：query 和 querystring。
query：返回的是格式化好的参数对象。
querystring：返回的是请求字符串。*/

//获取get传值
//http://localhost:3000/newscontent?aid=123

router.get('/newscontent',async (ctx)=>{

```
//从ctx中读取get传值

console.log(ctx.query);  //{ aid: '123' }       获取的是对象   用的最多的方式  **推荐
console.log(ctx.querystring);  //aid=123&name=zhangsan      获取的是一个字符串
console.log(ctx.url);   //获取url地址

//ctx里面的request里面获取get传值

console.log(ctx.request.url);
console.log(ctx.request.query);   //{ aid: '123', name: 'zhangsan' }  对象
console.log(ctx.request.querystring);   //aid=123&name=zhangsan
```

})

post请求获取参数

router.post("/addUser",ctx=>{
//当使用koa-bodyparser模块
[//可以直接使用ctx.request.body获取参数](//xn--ctx-vs9do1ay8qpy4azj3ahnd.request.xn--body-880g6d748kuv4c)
console.log(ctx.request.body)
})

动态路由

类似于vue-router，可以将参数直接以 /path/parma 的形式传递参数。 路由的param参数通过ctx.params获取。

router.get(‘/:category/:page/:id‘, function (ctx, next) {
ctx.body = ctx.params
})
app.use(router.routes(), router.allowedMethods())
app.listen(8000)
module.exports = app
//浏览器访问localhost:8000/story/99/195c6f5b-2f71-4412-9634-bfd05f80c7c4：
{
"category": "story",
"page": "99",
"id": "195c6f5b-2f71-4412-9634-bfd05f80c7c4"
}

config/index.js

配置数据库基本参数
module.exports={
host:"localhost",
user:"root",
password:"123321",
database:"management"
}
controller/mysql.js

const mysql=require("mysql")
const mysqlConfig=require("../config/index")
const connection=mysql.createConnection({
...mysqlConfig
})

connection.connect((error)=>{
if(error){
console.log(error)
return;
}
console.log("连接数据库成功")
})
//封装数据库语句
/**
*

-  [@param ](/param ) {*} sqlstr 数据库语句  
-  [@param ](/param ) {*} options 需要用到的参数 
*/
//将数据库语法封装成promise形式的方法
const query=(sqlstr,options)=>{
return new Promise((reslove,reject)=>{
let callback=(error,result)=>{
if(error){
reject(error)
return;
}
reslove(result);
}
//options 参数
//如果传了参数 那么第二个参数为options 第三个参数为callback
//否则第二个参数为callback 第三个参数为null
options=options?options:callback;
callback=options?callback:null;
connection.query(sqlstr,options,callback)
})
}
module.exports={query}
router/index.js 

const koaRouter=require("koa-router");
const router=new koaRouter()
//引入子路由
const userRouter=require("./user")
const classRouter=require("./class")

//为路由分层
//在根路由中注册子路由
router.use("/user",userRouter.routes(),userRouter.allowedMethods())
router.use("/class",classRouter.routes(),classRouter.allowedMethods())

module.exports=router

为router配置路由前缀

//访问的路由接口为/pre/接口
router.prefix("/pre")
router/user.js

const {query}=require("../controller/mysql")
const koaRouter=require("koa-router");
const router=new koaRouter()
router.post("/adduser",async ctx=>{
//结构传递过来的参数
let {username,department,position,date,class:classname,school}=ctx.request.body
let result=await query(`insert into user(username,department,position,date,class,school) values(?,?,?,?,?,?)`,[
username,department,position,date,classname,school
])
console.log(result,"pppppppp")
ctx.body=result
})
router.post("/removeUser",async ctx=>{
//结构传递过来的id
let {id}=ctx.request.body;
let result=await query(`delete from user where id=${id}`)
ctx.body=result

})

module.exports=router;
router/class.js

const {query}=require("../controller/mysql")
const koaRouter=require("koa-router");
const router=new koaRouter()
//多表联查
router.post("/search",async ctx=>{
//结构出传递的username参数
let {username}=ctx.request.body
//通过传递的username查询user表中的结果 得到的是一个数组
let res=await query(`select * from user where username='${username}'`)
//通过得到的res返回结果 解构出需要用到的id
let {id}=res[0]
//通过id在class表中查询对应的时间
let times=await query(`select * from class where uid=${id}`)
ctx.body={
showInfo:res[0],
times:times[0]
}
})

module.exports=router;
egg

下包

npm i -g egg-init
npm i --save egg egg-bin
脚手架

cnpm init egg --type=simple
目录结构

名字必须完全一致
1、package.json 设置字段

"scripts": {
"dev": "egg-bin dev"
},
执行 npm run dev 自动生成logs目录、run目录

app目录
controller目录 请求的逻辑代码
home.js
user.js
public目录 自动生成
service 目录 服务端的
home.js
router.js
middleware目录
oauth.js 进行请求拦截
config目录
config.default.js
plugin.js
package.json
logs目录 自动生成
run目录 自动生成
View：作为用户的 视图表现 部分，常见的展示形式如浏览器作为载体的网页、原生APP应用界面、桌面应用界面等，用于提供用户界面以便收集、响应用户行为产生的数据；

Controller：作为 控制器层 部分，控制用户界面（View）的数据流转途径，主要行为包含接收用户数据请求、发送请求至业务层（Service）、获取业务层（Service）数据响应，将响应数据发送至用户界面（View），或生成相应的模板界面发送至用户；

Service：作为 业务处理层 部分，主要负责收集及对数据进行相应的运算处理，主要行为包含收集控制器请求数据、数据有效性验证、运算、请求数据模型（Model）、接收数据模型（Model）响应消息、响应结果至控制器等；service的加载是异步的

Model：作为 数据模型层 部分，主要用于将数据持久化（OUT）、查询持久化数据（IN），常见行为如对数据库进行操作、缓存数据库数据等；
app/router.js

module.exports=(app)=>{
let {controller,router,middleware}=app
//创建接口 连接到controller/home.js 的product方法
const oauth=middleware.oauth()
//将中间件在路由中使用 请求productList进行请求拦截
router.get("/getProdectList",oauth,controller.home.product)
router.get("/getDetail",controller.home.detail)
//post请求 在config.default.js中设置
router.post("/login",controller.user.login)
}
config/config.default.js

let config={}

config.keys = '123321'
//设置post请求的body获取请求参数
config.bodyParser = {
jsonLimit: "lmb",
formLimit: "lmb"
}
//关闭安全防护 有post请求时设置
config.security={
csrf: {
enable: false
}
}
//设置数据库的基本参数
config.mysql= {
// 单数据库信息配置
client: {
// host
host: 'localhost',
// 端口号
port: '3306',
// 用户名
user: 'root',
// 密码
password: '123321',
// 数据库名
database: 'gxb',
},
// 是否加载到 app 上，默认开启
app: true,
// 是否加载到 agent 上，默认关闭
agent: false,
}
module.exports=config  }
}
config/plugin.js

//连接数据库
//开启插件
exports.mysql = {
enable: true,
package: 'egg-mysql',
};
controller/home.js

//控制器
const {Controller}=require("egg")
class Home extends Controller{
product(){
const {ctx}=this
ctx.body=[{
name:"zhangsan",
age:"22"
}]
}
async detail(){
const {ctx}=this
let {query}=ctx.request
const {id}=query
const {user}=await ctx.service.home.find(id)
console.log(user)
ctx.body={
user
}
}
}
module.exports=Home
controller/user.js

const {Controller}=require("egg")

class User extends Controller{
login(){
const {ctx} =this
const {id}=ctx.request.body
[//console.log](//console.log)(body,"pppppppppp")
console.log(id)
ctx.body={
code:221,

```
    }
}
```

}

module.exports=User
service/home.js(与controller下需要建立连接的文件同名)

与controller/home.js建立连接
const { Service } = require("egg")
class HomeService extends Service {
async find(id) {
// 假如 我们拿到用户 id 从数据库获取用户详细信息
const user = await this.app.mysql.get('new', { id: id})
return { user };
}
}
module.exports = HomeService
middleware/oauth.js

module.exports = (options) => {
return async function (ctx, next) {

```
    let { header } = ctx.request
    //header可以获取到客户端通过axios设置的headers传递过来的信息
    if (!header.token) {
        ctx.status = 401
        ctx.body = {
            code: 0,
            msg: "没有权限 缺少token"
        }
    } else if (!header.id) {
        ctx.status = 401
        ctx.body = {
            code: 0,
            msg: "没有权限 缺少id"
        }
    } else {
    //将传递过来的token与通过传递过来的id在数据库中获取的token进行比较
        let { token } = await ctx.service.user.verify(header.id)

        if (token === header.token) {
            await next()
        } else {
            ctx.status = 401
            ctx.body = {
                code: 0,
                msg: "没有权限,用户信息不一致"
            }
        }

    }

}
```

}
总结

连接数据库

config/config.default.js 设置数据库的基本配置
config/plugin.js 连接数据库
service 目录创建连接
通过 Controller 获取 Service 层拿到的数据。
post请求

config.default.js 设置bodyParser、关闭关闭安全防护


> 原文: <https://www.yuque.com/guxinbo/ps8gra/mtagnu>