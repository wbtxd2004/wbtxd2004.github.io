---
layout: post
title:  基于深度学习的装机配置单(手动整理)
date:   2015-06-05
categories:  杂谈
published: true
author: wubin
---

#基于深度学习的装机配置单#

目前可以选择的显卡是NVIDIA的三个不同系列的，第一个是Tesla系列的K40，第二个是GeForce系列的GTX TITAN X，第三个是GeForce系列的GTX 980 Ti (这个是2015年三月份发布的，目前还没有卖的，暂时用980替代，性能落后很多)。

通过浏览相关信息，个人最倾向于GTX 980 Ti，这个的性能同Titan X差不多，价格比较合理。至于K40，性价比不高，暂时忽略。

##1. 基于GTX 980 Ti的装机配置##

1. 显卡：4个“[七彩虹GTX 980Ti CH-6GD5](http://detail.zol.com.cn/vga/index401989.shtml)”显卡
	
		芯片厂商: NVIDIA
		显卡芯片: GeForce GTX 980Ti
		显示芯片系列: NVIDIA GTX 900系列
		制作工艺: 28纳米
		核心代号: GM200
		显存类型: GDDR5
		显存容量: 6144MB
		显存位宽: 384bit
		最大分辨率: 5120×3200
		接口类型: PCI Express 3.0 16X
		I/O接口: HDMI接口/DVI接口/3个DisplayPort接口
		电源接口: 8pin+6pin
		参考报价：5199*4=20796
		
2. CPU：1个Intel [酷睿i7 5930K](http://detail.zol.com.cn/cpu/index384515.shtml)
		
		插槽：LGA 2011-v3 
		核心：六核心十二线程
		频率：3.5GHz 
		架构： Haswell
		制作工艺： 22纳米
		功耗： 140W
		三级缓存： 15MB
		最大支持内存：32G
		指令集：SSE4.2，AVX 2.0，AES
		内存控制器：四通道：DDR4 1333/1600/2133
		参考报价： 4599元

3. 主板：1个[华硕X99-E WS主板](http://detail.zol.com.cn/motherboard/index391193.shtml)或者1个[技嘉GA-X99-Gaming 5主板](http://detail.zol.com.cn/motherboard/index388017.shtml)（考虑到4个显卡SLI技术）
		
		
		1.华硕X99-E WS主板
			主芯片组：IntelX99
			CPU插槽：LGA 2011-3
			支持CPU数量： 1颗
			内存类型： DDR4
			内存插槽： 8*DDR4 DIMM
			最大内存容量: 128GB
			内存描述：支持四通道DDR4 3000(超频)/3200(O.C.)/2800(超频)/2666(超频)/2400(超频)/2133MHz内存
			显卡插槽： PCI-E 3.0标准
			PCI-E插槽：7×PCI-E X16显卡插槽
			SATA接口： 8×SATA III接口；1×SATA Express接口；1×M.2接口（10Gb/s）
			USB接口： 12×USB3.0接口（10背板+2内置）；4×USB2.0接口（2背板+2内置）
			版型： E-ATX板型
			外形尺寸：30.5×26.7cm 
			多显卡技术：**支持NVIDIA 4-Way SLI四路交火技术**
			参考报价： 4799
		
		2.技嘉GA-X99-Gaming 5主板
			主芯片组：IntelX99
			CPU类型：Core i7
			CPU插槽：LGA 2011-3
			支持CPU数量： 1颗
			内存类型： DDR4
			内存插槽： 8*DDR4 DIMM
			最大内存容量: 64GB
			内存描述：支持四通道DDR4 2133/1866/1600/1333MHz内存
			显卡插槽： PCI-E 3.0标准
			PCI-E插槽：4×PCI-E X16显卡插槽
			SATA接口： 10×SATA III接口；1×SATA Express接口；1×M.2接口（10Gb/s）
			USB接口： 4×USB3.0接口（2背板+2内置）；8×USB2.0接口（4背板+4内置）
			版型： ATX板型
			外形尺寸：30.5x24.4cm
			多显卡技术：**支持NVIDIA 4-Way SLI四路交火技术**
			参考报价： 3288
		
		
4. 内存：[金士顿HyperX 32GB DDR4 2666](http://detail.zol.com.cn/memory/index400497.shtml)（HX426C15FBK4/32)
		
		内存容量：套装（4×8GB）
		内存类型：DDR5
		内存主频：2666MHz
		针脚数：240pin
		插槽类型：DIMM
		参考报价：3599
		
5. 硬盘: 1个 [西部数据4TB ](http://detail.zol.com.cn/hard_drives/index346787.shtml)  
		
		硬盘容量：4000G
		缓存：64M
		转速：7200rpm
		接口类型：SATA3.0
		接口速率：6Gb/s
		其他：黑盘（WD4001FAEX）
		参考报机：1699

6. 固态硬盘：1个 [三星SSD 850PRO （256GB） ](http://detail.zol.com.cn/solid_state_drive/index384145.shtml) 

		接口类型：SATA3
		硬盘尺寸：2.5英寸
		参考报价：1799

7. 机箱：1个 [先马坦克（透彻标准版）](http://detail.zol.com.cn/case/index400499.shtml)机箱或者1个[酷冷至尊克斯摩2超跑版（RC-1200-KKN1）](http://detail.zol.com.cn/case/index309948.shtml)（为了EATX）

		1.先马坦克
			机箱样式：立式
			适用主板：ATX，M-ATX
			电源设计：下置电源
			显卡限长：425mm
			CPU散热器限高：161mm
			5.25英寸仓位：2个
			3.5英寸仓位：2个
			2.5英寸仓位：5个，其中两个与3.5通用
			扩展插槽：7
			前置接口：2*USB 2.0；1*USB 3.0
			散热性能：前：2*120/240mm风扇
					前：2*120/240mm风扇
					前：2*120/240mm风扇
			参考报价：219
		2.酷冷至尊克斯摩2超跑版
			机箱样式：立式
			适用主板：**EATX板型**，ATX板型，MATX板型
			电源设计：下置电源
			显卡限长：385mmmm
			CPU散热器限高：161mm
			5.25英寸仓位：3个
			3.5英寸仓位：13个
			2.5英寸仓位：11个
			扩展插槽：11
			前置接口：4*USB 2.0；2*USB 3.0
			散热性能：前：1×200mmLED风扇
					顶：1×120mm黑色风扇
					后：1×140mm风扇
					侧：2×120mm风扇（选配）
					底：2×120mm风扇
			参考报价：219
		
9. 电源：1个[海盗船AX1500i](http://detail.zol.com.cn/power/index379507.shtml)   
		
		功率：1500W
		风扇描述：14cm风扇
		电源尺寸：150x86x225mm
		参考报价：3599
		
9. 散热器：1个 九州风神（DEEPCOOL）大霜塔 双12CM风扇6热管双塔式 全平台CPU散热器 209
10. 显示器： 1个戴尔P2314H显示器 1299
11. 键盘鼠标：1个罗技 MK260键鼠套装 120

总计：45517元

##2. 基于Titan X的装机配置##

只将显卡换为4个[影驰GeForce GTX Titan X](http://detail.zol.com.cn/vga/index398289.shtml)显卡,单卡价格为8699.