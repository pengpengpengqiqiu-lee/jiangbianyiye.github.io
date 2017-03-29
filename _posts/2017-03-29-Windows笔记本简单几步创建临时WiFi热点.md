#Windows笔记本简单几步创建临时WiFi热点
###1.打开命令提示符
- 如果当前用户是管理员直接win+r打开运行窗口输入cmd后回车。
- win10或者win8可以直接右键开始菜单点选“命令提示符（管理员）”。
- win7单击“开始”按钮，选择“所有程序”，选择“附件”，选择“命令提示符”,右键以管理员身份打开。
###2.开启系统承载网络模块和新建无线网络
在命令行中输入：
`netsh wlan set hostednetwork mode=allow ssid=Wifi名 key=密码`
**注意**：将上述需要*“Wifi名”*改为你的wifi名称，**Wifi名称需为英文**不然可能会导致乱码问题，**密码最少8位**。

+ 回车后提示成功进入下一步
###3.开启无线网
输入`netsh wlan start hostednetwork `开启无线网

+ 回车后提示成功进入下一步
###4.配置共享网络
1. 打开**网络共享中心**
2. 点击**更改适配器设置**
3. 右键你当前已联网适配器一般为**以太网**，点选**属性**
4. 点击**共享**进入共享设置界面
5. 点选**允许其他网络用户通过此计算机的Internet连接来连接(N)**
6. 下拉请选择一个专用网络连接选择刚**创建出来的网络连接**(有无线网络标识，在网络名称下面有刚才输入的wifi名，实在找不到可以在命令行中执行`netsh wlan stop hostednetwork `，看看哪个消失了，然后再执行`netsh wlan start hostednetwork `后继续设置）

***恭喜！到此你就可以登录wifi了***

###5.关闭无线网和承载网络模块
当不需要使用无线网络时
使用命令`netsh wlan stop hostednetwork `即可关闭无线网。
使用命令`netsh wlan set hostednetwork mode=disallow `即可关闭网络承载模块。