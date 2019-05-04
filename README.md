# 搭建了一个与树莓派开发板远程交互的web体系
## 功能
与树莓派开发板相连接的温湿度传感器的数值实时推送到web端，现场设备如电机、LED亦可通过web操纵
## 通信方式
因为要解决局域网穿透的问题，由于树莓派开发板要部署在局域网中，在局域网以外不能通过IP地址直接找到它，所以用Mongodb数据库做数据中转。一端以http轮询将传感器数据或控制量写入数据库，另一端以同样的方式将数据取出。传输延迟平均1秒左右，还可以啦。
## 驱动单片机
用到的树莓派引脚号在singleChipComputerProgram目录下各脚本文件中已用注释标明，各脚本文件对应各类设备。可按既定引脚连接也可以自行修改引脚号。
例如将DHT11传感器的信号端接到树莓派的11号引脚，正负极分别接电和接地即匹配了AdafruitDHT.py脚本文件，命令行运行Python AdafruitDHT.py 11 17即可将温湿度信号以2秒间隔采样并写入Mongodb之中，web端将数据轮询读出并显示在图表上。
## 使用
测试账号：zhangwuji   
密码：emm   
有时会登陆不上，大概率是因为连接Mongodb失败，通常重启后端程序能解决😓…………

![avatar](https://i.loli.net/2019/05/04/5ccd9073d4d2b.jpg)
