# QT_IOTSystem
一个物联网控制管理系统，也即控制管理的上位机程序，能够做到对物联网设备端的监控和控制。

# 前言
此篇文章是本人面向对象课程大作业的一个讲述，主要是对用到的知识和模块做一个总结和回顾。

# 功能及界面介绍
## 物联网控制管理系统
### 一、	选题背景

随着社会的进步和科技的发展，人们对于生活品质的要求越来越强烈，而物联网的出现极大地提升了人们的生活质量，比如智能窗帘、智能灯泡等一系列智能家居。通过物联网的方式，人们可以实现远程控制这些电子产品，方便了人们的使用，提升了用户体验，同时通过物联网系统采集数据，并通过系统分析数据，利用数据来为用户提供更加舒适的居住环境，也提升了用户的满意度。
本设计欲设计一个物联网控制管理系统，也即控制管理的上位机程序，能够做到对物联网设备端的监控和控制。

### 二、	系统说明

**实现环境、开发工具**：
	Windows平台
	Qt5.14.2 (MinGW 64-bit)
**功能规划**：

-  登录以及注册
- 对物联网设备端采集到的数据进行检测，控制设备端的可控模块的控制
- 	对控制命令可以记录、保存以及删除，方便用户查看以及管理
- 	用户分为管理员以及普通用户，管理员可以对设备进行相应得控制，而普通用户只能对设备情况进行查看
- 	管理员可对反馈的采集信号设置阈值，当所采集信号值达到设定阈值，会对登录用户进行提醒。
- 	具有定时控制功能，能够实现对设备的定时操作。

### 三、	系统设计
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210216205628779.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM3NDI5MzEz,size_16,color_FFFFFF,t_70)

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210216205639431.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM3NDI5MzEz,size_16,color_FFFFFF,t_70)

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210216205649588.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM3NDI5MzEz,size_16,color_FFFFFF,t_70)

### 四、	系统实现
**登录界面:**
首先是UI界面，当中有对密码的保护显示，有输入账号密码的输入编辑框，以及登录、忘记密码和注册的按钮，下面分别对几个部分进行展示

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210216210040463.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM3NDI5MzEz,size_16,color_FFFFFF,t_70#pic_center)


**密码保护**
用户可以点击选择框，决定密码是否显示

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210216210339667.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM3NDI5MzEz,size_16,color_FFFFFF,t_70#pic_center)


![在这里插入图片描述](https://img-blog.csdnimg.cn/20210216210359350.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM3NDI5MzEz,size_16,color_FFFFFF,t_70#pic_center)


**忘记密码：**
点击忘记密码按钮后，弹出子窗口，询问用户用户名，为了查看方便，这里密码未采用加密。当用户输入用户名后，会对用户名进行查询，当查询到用户名后，将密码显示到屏幕上面

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210216210905982.png#pic_center)

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210216210914466.png#pic_center)

**注册：**
点击注册按钮后，会对用户输入参数进行检查，当输入账号不为空的时候，检查用户名和密码是否相同、密码是否低于四位，若这些条件都得到满足，注册成功，将用户名和密码进行保存

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210216210940954.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM3NDI5MzEz,size_16,color_FFFFFF,t_70#pic_center)
**登录：**
点击登录按钮后，会对输入用户名和密码和系统保存的信息作对比，当信息符合一致的时候，登录成功。并且在登录的时候会对用户名做检查，当是管理员登录的时候，会开放所有权限，而当非管理员登录的时候，则只会开放查看权限，而不会开放控制权限。

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210216211011559.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM3NDI5MzEz,size_16,color_FFFFFF,t_70#pic_center)

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210216211019702.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM3NDI5MzEz,size_16,color_FFFFFF,t_70#pic_center)

当登录后，首先系统会获取当前硬件信息和状态，将当前系统时间显示在正上方以及获取已经设定的温度上下限和记录的命令，并且将其显示在窗口中这个时候普通用户就可以查看到信息，但是当是管理员登录的时候是获取所有的权限的，可以对硬件端进行控制、定时以及对温度上下限进行改变，下面对控制部分进行说明。

**温度上下限部分：**
当检测到的温度超过温度上限，或者低于温度下限的时候，温度标签会高亮，通知用户温度超过阈值了。此部分管理员可以通过更改按钮，改变温度上下限。

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210216211049541.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM3NDI5MzEz,size_16,color_FFFFFF,t_70#pic_center)

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210216211058129.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM3NDI5MzEz,size_16,color_FFFFFF,t_70#pic_center)

**控制部分：**
当管理员对当前的硬件进行操控的时候，会将当前的控制命令进行记录，并将信息传到硬件端，对硬件进行控制。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210216211122864.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM3NDI5MzEz,size_16,color_FFFFFF,t_70#pic_center)

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210216211130297.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM3NDI5MzEz,size_16,color_FFFFFF,t_70#pic_center)

**定时部分：**
管理员能够通过添加定时器按钮对硬件端的控制做出定时，点击添加定时器按钮后，会弹出子窗口，让用户选择定时的大小，并且选择硬件是定时开还是定时关。当点击确定按钮后，将当前定时器的消息加入定时器列表中，当到达指定的系统时间，就会执行指定的控制命令，并且将命令记录在命令记录表中，删除已经执行的定时器。当然管理员对已经添加的定时器可以选择并且点击删除定时器即可取消已经选中的定时器。

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210216211155431.png#pic_center)

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210216211205642.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM3NDI5MzEz,size_16,color_FFFFFF,t_70#pic_center)

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210216211216873.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM3NDI5MzEz,size_16,color_FFFFFF,t_70#pic_center)

# 贝壳物联对接部分

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210228154647599.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM3NDI5MzEz,size_16,color_FFFFFF,t_70)


- [非实时通讯，以传统http(S) API 方式实现](https://www.bigiot.net/help/34.html)
- 
- [实时通讯，以tcp、websocket长连接方式实现](https://www.bigiot.net/help/1.html)
- 

因为考虑到要实时通讯的问题，这里选择的是使用tcp、websocket长连接的方式去实现。

## 连接
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210228155720354.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM3NDI5MzEz,size_16,color_FFFFFF,t_70)

1. 因此在使用QT实现socket连接的时候要使用加密的连接

```cpp
void ControlWindow::socketLink(void)
{
	QJsonObject jsondata;
	socket->abort();
	socket->connectToHostEncrypted("www.bigiot.net",8585);
	if(!socket->waitForConnected(30000))
	{
		qDebug()<<"error";
	}
	else
	{
		socketState = STATE_SININ;
		jsondata.insert("M","xxxx");
		jsondata.insert("ID","xxxx");
		jsondata.insert("K","xxxx");
		socket->write((QJsonDocument(jsondata).toJson(QJsonDocument::Compact)).append('\n'));
	}
}
```

2. 需要一定时间发送心跳包，保持socket连接

![在这里插入图片描述](https://img-blog.csdnimg.cn/2021022815595081.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM3NDI5MzEz,size_16,color_FFFFFF,t_70)


```cpp
//发送心跳
void ControlWindow::pollStart()
{
	socket->write("{\"M\":\"beat\"}\n");

}
```

## 通信数据格式
![在这里插入图片描述](https://img-blog.csdnimg.cn/2021022816001331.png)

```cpp
	socketState = STATE_SEDN;
	QJsonObject jsondata;
	jsondata.insert("M","say");
	jsondata.insert("ID","D16443");
	jsondata.insert("C","ledon");
	socket->write((QJsonDocument(jsondata).toJson(QJsonDocument::Compact)).append('\n'));
	ui->label_light->setStyleSheet("image: url(:/img/beepon.png)");
```

关于命令，在官网有，这里就不介绍了。

---

## 代码信息更改



![在这里插入图片描述](https://img-blog.csdnimg.cn/20210228203107835.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM3NDI5MzEz,size_16,color_FFFFFF,t_70)

**ID：**是用户ID
**IDKEY:**是用户APIKEY
**DEVICEID:**是设备ID
在[个人信息查看](https://www.bigiot.net/User/profile.html)

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210228203310400.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM3NDI5MzEz,size_16,color_FFFFFF,t_70)

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210228203404662.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM3NDI5MzEz,size_16,color_FFFFFF,t_70)

命令cmd是定制的，在esp8266固件里面可以更改

---

# 文件部分
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210228204129613.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM3NDI5MzEz,size_16,color_FFFFFF,t_70)

这部分会根据linux还是windows系统来选择密码，温度上下限设置以及命令记录的文件，这部分我没有采用数据库的方式(还没有怎么学习数据库),因此这个必须进行相应的更改;

---

# ESP8266部分
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210228204812671.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM3NDI5MzEz,size_16,color_FFFFFF,t_70)

硬件部分lua语言参考了贝壳物联的代码
[链接](https://www.bigiot.net/help.html)

**init.lua文件**
主要需要修改wifiname以及passwd,然后程序就会跳到control.上面
```python
--init.lua
print("set up wifi mode")
wifi.setmode(wifi.STATION)
wifi.sta.config("wifiname","passwd")
--here SSID and PassWord should be modified according your wireless router
wifi.sta.connect()
tmr.alarm(1, 1000, 1, function()
if wifi.sta.getip()== nil then
print("IP unavaiable, Waiting...")
else
tmr.stop(1)
print("Config done, IP is "..wifi.sta.getip())
dofile("control.lua")
end
end)
```

**control.lua文件**
涉及设备控制以及温度检测
```python
--use sjson
_G.cjson = sjson
--modify DEVICEID1 INPUTID APIKEY1

DEVICEID1 = "16443"
APIKEY1 = "2615effe4"

INPUTID = "36"
host = host or "www.bigiot.net"
port = port or 8181
LED1 = 1
SWITCH1 = 2

pin = 4
isConnect1 = false
--初始化
gpio.mode(LED1,gpio.INPUT) 
gpio.mode(SWITCH1,gpio.INPUT) 

gpio.write(LED1,gpio.LOW)
gpio.write(SWITCH1,gpio.LOW)
--建立连接
cu1 = net.createConnection(net.TCP)
isConnect1 = true
local function run1() 
  --接收到消息时间响应
  cu1:on("receive", function(cu1, c) 
    print(c)
    isConnect1 = true
    r = cjson.decode(c)
    if r.M == "say" then
      if r.C == "ledon" then   
        gpio.write(LED1, gpio.HIGH)  
        ok, played = pcall(cjson.encode, {M="say",ID=r.ID,C="LED1 turn on!"})
        cu1:send( played.."\n" )
      end
      if r.C == "switchon" then   
        gpio.write(SWITCH1, gpio.HIGH)  
        ok, played = pcall(cjson.encode, {M="say",ID=r.ID,C="SWITCH1 turn on!"})
        cu1:send( played.."\n" )
      end

      if r.C == "ledoff" then   
        gpio.write(LED1, gpio.LOW)
        ok, stoped = pcall(cjson.encode, {M="say",ID=r.ID,C="LED1 turn off!"})
        cu1:send( stoped.."\n" ) 
      end
      
      if r.C == "switchoff" then   
        gpio.write(SWITCH1, gpio.LOW)
        ok, stoped = pcall(cjson.encode, {M="say",ID=r.ID,C="SWITCH1 turn off!"})
        cu1:send( stoped.."\n" ) 
      end
      
    end
  end)
  --断开连接响应
  cu1:on('disconnection',function(scu)
    cu1 = nil
    isConnect1 = false
    --停止心跳包发送定时器，5秒后重试
    tmr.stop(1)
    tmr.alarm(6, 3000, 0, run1)
  end)
  cu1:connect(port, host)
  ok, s = pcall(cjson.encode, {M="checkin",ID=DEVICEID1,K=APIKEY1})
  if ok then
    print(s)
  else
    print("failed to encode!")
  end
  tmr.delay(10000)
  if isConnect1 then
    cu1:send(s.."\n")
  end
  tmr.alarm(1, 25000, 1, function()
    if isConnect1 then
      cu1:send(s.."\n")
    end
  end)
end
--定时获取温度
tmr.alarm(0, 10000, 1, function()
status, temp, humi, temp_dec, humi_dec = dht.read(pin)
if status == dht.OK then
   if isConnect1 then
    if temp > 10 then
    cu1:send(string.format("{\"M\":\"update\",\"ID\":\"主设备ID\",\"V\":{\"所属设备1ID\":\"%d\",\"所属设备2ID\":\"%d\"}}\n",
            ( math.floor(temp)*0.0406 - 3 ), --减去补偿
            ( math.floor(humi)*0.041 )  
      ))
    end
   end
 --   print(string.format("DHT Temperature:%d;Humidity:%d\r\n",
 --         ( math.floor(temp)*0.0406 ),
 --         ( math.floor(humi)*0.041 )  
 --   ))
elseif status == dht.ERROR_CHECKSUM then
    print( "DHT Checksum error." )
elseif status == dht.ERROR_TIMEOUT then
    print( "DHT timed out." )
end
end)

run1()
```

其中主设备ID为

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210228210320873.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM3NDI5MzEz,size_16,color_FFFFFF,t_70)

从设备在**添加数据接口处添加**

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210228210356743.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM3NDI5MzEz,size_16,color_FFFFFF,t_70)

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210228210451673.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM3NDI5MzEz,size_16,color_FFFFFF,t_70)

温度上传的形式为官网给出文档有

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210228210620314.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM3NDI5MzEz,size_16,color_FFFFFF,t_70)
# github链接

[QT_IOTSystem](https://github.com/JUSTWILLPOWER/QT_IOTSystem)
有用可以点击收藏
