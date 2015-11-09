---
layout: post
category: 杂谈
title:  基于深度学习的装机配置单(手动整理)
date:   2015-06-05
tagline: by WuBin 武斌
tags: [DeepLearning, Computer DIV, caffe]
author: wubin
published: true
---
一份为了学习和使用caffe所设计深度学习装机配置单，仅供参考。

<!--more-->

#基于深度学习的装机配置单#

目前可以选择的显卡是NVIDIA的三个不同系列的，第一个是Tesla系列的K40，第二个是GeForce系列的GTX TITAN X，第三个是GeForce系列的GTX 980 Ti。

通过浏览相关信息，个人最倾向于GTX 980 Ti，这个的性能同Titan X差不多，价格比较合理。至于K40，性价比不高，暂时忽略。
关于SLI技术，可以参考[百科页面](http://zh.wikipedia.org/wiki/NVIDIA_SLI)和[官方页面](http://www.geforce.cn/hardware/technology/sli)。


##1. 基于GTX 980 Ti的装机配置##

1. 显卡：4个[华硕GTX 980Ti-6GD5](http://detail.zol.com.cn/vga/index402453.shtml)显卡
	
		芯片厂商: NVIDIA
		显卡芯片: GeForce GTX 980Ti
		显示芯片系列: NVIDIA GTX 900系列
		制作工艺: 28纳米
		核心代号: GM200
		显存类型: GDDR5
		显存容量: 6144MB
		显存位宽: 384bit
		最大分辨率: 4096×2160
		接口类型: PCI Express 3.0 16X
		I/O接口: HDMI接口/DVI接口/3个DisplayPort接口
		电源接口: 8pin+6pin
		产品尺寸：266.7×111.2×38.1mm
		参考报价：5999*4=23996
		
2. CPU：1个 [Intel 酷睿i7 5960X](http://detail.zol.com.cn/cpu/index384514.shtml)
		
		CPU主频：3GHz
		最高睿频：3.5GHz 
		总线类型：QPI总线
		总线频率：8GT/s
		插槽：LGA 2011-v3 
		CPU架构：Haswell
		核心：八核心十六线程
		制作工艺： 22纳米
		功耗： 140W
		三级缓存： 20MB
		最大支持内存：64G
		指令集：SSE4.2，AVX 2.0，AES
		内存控制器：四通道：DDR4 1333/1600/2133
		参考报价： 7699 RMB

3. 主板：1个[华硕X99-E WS主板](http://detail.zol.com.cn/motherboard/index391193.shtml)（考虑到4个显卡SLI技术）
		
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
		版型：**E-ATX板型**
		外形尺寸：30.5×26.7cm 
		多显卡技术：**支持NVIDIA 4-Way SLI四路交火技术**
		RAID功能：支持RAID 0，1，5，10 
		尺寸：30.5 厘米 x 26.7 厘米
		参考报价： 4799 RMB
		
		
4. 内存：2个[海盗船32GB DDR4 2666 统治者铂金 CMD32GX4M4A2666C16)](http://www.corsair.com/zh-cn/dominator-platinum-series-32gb-4-x-8gb-ddr4-dram-2666mhz-c16-memory-kit-cmd32gx4m4a2666c16)
		
		内存容量：套装（4×8GB）
		内存类型：DDR4
		内存主频：2666MHz
		针脚数：288pin
		参考报价：5000*2=10000 RMB
		
5. 硬盘: 3个 [西部数据4TB ](http://detail.zol.com.cn/hard_drives/index368122.shtml)  组RAID5
		
		硬盘容量：4000G
		缓存：64M
		转速：7200rpm
		接口类型：SATA3.0
		接口速率：6Gb/s
		其他：黑盘（WD4003FZEX）
		参考报机：1799*3=5397 RMB
				
6. 固态硬盘For RAID：1个[浦科特PX-G512M6e（512GB）](http://detail.zol.com.cn/solid_state_drive/index383241.shtml)或者[三星SSD SM951](http://detail.zol.com.cn/395/394804/param.shtml)PCI-E M.2 SSD cache for RAID，Intel RST in Linux技术  
		
		参考报价：2799 RMB/3450RMB
		
6. 固态硬盘：1个 [三星SSD 850PRO （512GB） ](http://detail.zol.com.cn/solid_state_drive/index384146.shtml) 

		接口类型：SATA3
		硬盘尺寸：2.5英寸
		参考报价：2999 RMB

7. 机箱：1个[海盗船900D](http://detail.zol.com.cn/case/index359466.shtml)（为了EATX）

		机箱样式：台式机箱（全塔）
		适用主板：**EATX板型**，ATX板型，MATX板型
		电源类型：标准ATX PS2电源（选配）
		电源设计：下置电源
		显卡限长：400mm
		5.25英寸仓位：4个
		3.5英寸仓位：9个
		2.5英寸仓位：9个
		扩展插槽：10
		前置接口：4*USB 2.0；2*USB 3.0
		散热性能：前：3×120mm风扇（标配）
				顶：4×120mm或3*140mm风扇（选配）
				后：1×140mm风扇（标配）
				底：8×120mm或6*140mm风扇（选配）
		尺寸：649.6×252×691.6mm 
		参考报价：2499 RMB
		
9. 电源：1个[海盗船AX1500i](http://detail.zol.com.cn/power/index379507.shtml)   
		
		功率：1500W
		风扇描述：14cm风扇
		电源尺寸：150x86x225mm
		参考报价：3599 RMB
		
10. 光驱：1个[华硕DRW-24D1ST](http://detail.zol.com.cn/dvdrw/index306395.shtml)   
		
		参考报价：120 RMB

11. 显示器： 1个[华硕PA238Q](http://detail.zol.com.cn/lcd/index291422.shtml)显示器   
  
		参考报价：1999 RMB

12. 键盘鼠标：1个罗技MK520键鼠套装   
  
		参考报价：263 RMB

13. 散热器：1个 [海盗船H110](http://detail.zol.com.cn/cooling_product/index347677.shtml)  CPU散热器
  
		参考报价：999 RMB

14. 风扇：12个[海盗船AF120静音版](http://detail.zol.com.cn/cooling_product/index334550.shtml)  
  
		参考报价：89*12=1068 RMB
		
15. CPU导热硅脂：冷酷至尊 黄金硅脂 PTK-L01 2g 28 RMB
		
16. 关于水冷设备，根据实际使用情况决定是否购买。
17. 3个九州风神风扇集线器 100 RMB
18. Tt（Thermaltake）Commander FT 机箱风扇控制器 299 RMB
19. 配件  
  
		线材扎带 4*159 mm 1包 20RMB
		乔思伯 指环王MOD 螺丝套装 1盒 30RMB
		 

总计：69994元，七万左右

##2. 基于Titan X的装机配置##


1. 显卡：4个[影驰GeForce GTX Titan X](http://detail.zol.com.cn/vga/index398289.shtml)显卡
	
		芯片厂商: NVIDIA
		显卡芯片: GeForce GTX Titan X
		显示芯片系列: NVIDIA GTX Titan X系列
		制作工艺: 28纳米
		核心代号: GM200
		显存频率：7012MHz 
		显存类型: GDDR5
		显存容量: 12288MB
		显存位宽: 384bit
		最大分辨率: 4096×2160
		接口类型: PCI Express 3.0 16X
		I/O接口: HDMI 2.0接口/DVI接口/3×DisplayPort 1.2接口 
		电源接口: 8pin+6pin
		最大功耗：250W
		参考报价：8699*4=34796 RMB
		
2. CPU：1个 [Intel 酷睿i7 5960X](http://detail.zol.com.cn/cpu/index384514.shtml)
		
		CPU主频：3GHz
		最高睿频：3.5GHz 
		总线类型：QPI总线
		总线频率：8GT/s
		插槽：LGA 2011-v3 
		CPU架构：Haswell
		核心：八核心十六线程
		制作工艺： 22纳米
		功耗： 140W
		三级缓存： 20MB
		最大支持内存：64G
		指令集：SSE4.2，AVX 2.0，AES
		内存控制器：四通道：DDR4 1333/1600/2133
		参考报价： 7699 RMB

3. 主板：1个[华硕X99-E WS主板](http://detail.zol.com.cn/motherboard/index391193.shtml)（考虑到4个显卡SLI技术）
		
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
		版型：**E-ATX板型**
		外形尺寸：30.5×26.7cm 
		多显卡技术：**支持NVIDIA 4-Way SLI四路交火技术**
		RAID功能：支持RAID 0，1，5，10 
		尺寸：30.5 厘米 x 26.7 厘米
		参考报价： 4799 RMB
		
4. 内存：[海盗船64GB DDR4 2133 复仇者LPX](http://detail.zol.com.cn/memory/index396855.shtml)（CMK64GX4M8A2133C13)
		
		内存容量：套装（8×8GB）
		内存类型：DDR4
		内存主频：2133MHz
		针脚数：288pin
		参考报价：7699 RMB
		
5. 硬盘: 3个 [西部数据4TB ](http://detail.zol.com.cn/hard_drives/index346787.shtml)  组RAID5
		
		硬盘容量：4000G
		缓存：64M
		转速：7200rpm
		接口类型：SATA3.0
		接口速率：6Gb/s
		其他：黑盘（WD4001FAEX）
		参考报机：1699*3=5097 RMB

6. 固态硬盘For RAID：1个[浦科特PX-G512M6e（512GB）](http://detail.zol.com.cn/solid_state_drive/)index383241.shtml)PCI-E M.2 SSD cache for RAID  
		
		参考报价：2799 RMB
		
6. 固态硬盘：1个 [三星SSD 850PRO （256GB） ](http://detail.zol.com.cn/solid_state_drive/index384145.shtml) 

		接口类型：SATA3
		硬盘尺寸：2.5英寸
		参考报价：1799 RMB

7. 机箱：1个[酷冷至尊克斯摩2超跑版（RC-1200-KKN1）](http://detail.zol.com.cn/case/index309948.shtml)（为了EATX）

		机箱样式：立式
		适用主板：**EATX板型**，ATX板型，MATX板型
		电源类型：ATX PS2/EPS 12V（选配）
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
		尺寸：664×334×704mm 
		参考报价：2999 RMB
		
9. 电源：1个[海盗船AX1500i](http://detail.zol.com.cn/power/index379507.shtml)   
		
		功率：1500W
		风扇描述：14cm风扇
		电源尺寸：150x86x225mm
		参考报价：3599
		
9. 散热器：1个 [Tt 零度水冷装备（Pacific RL240）](http://detail.zol.com.cn/cooling_product/index395677.shtml)  
  
		参考报价：2899 RMB


10. 显示器： 1个戴尔P2314H显示器 1299 RMB

11. 键盘鼠标：1个罗技MK520键鼠套装 263 RMB

总计：75747元

考虑到实际价格以及具体调整，在9W左右。
