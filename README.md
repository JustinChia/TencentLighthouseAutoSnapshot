# TencentLighthouseAutoSnapshot
腾讯云轻量应用服务器自动备份脚本
https://cloud.tencent.com/developer/article/1937280

腾讯轻量云自动创建快照-使用腾讯云函数实现
相信大家有很多人都买了腾讯云轻量云，轻量云不能自动创建快照，今天就使用腾讯的云函数自动创建快照，每天备份，自动删除最早的备份或者删除一个最新的备份，保留一个固定备份，保护数据。

进入云函数界面：https://console.cloud.tencent.com/scf/list
新建云函数

选择自定义函数，事件函数，运行环境选择Python2.7；然后上传zip代码包。下载地址

上传完成之后，进入函数管理-函数配置，点击右上角编辑。

修改初始化超时时间、执行超时时间、环境变量两个超时时间尽量长点，环境变量需要参数参数；
Regions_InstanceIds、SecretId、SecretKey，Instanceidx
Instanceidx要求：
0：总是删除最新备份保留最早，这样可以有一个固定备份，
1：总是删除最早备份，这是滚动备份
其中Regions_InstanceIds格式要求：实例地域1:轻量云实例ID1,轻量云实例ID2;实例地域2:轻量云实例ID3,轻量云实例ID4，然后保存。

进入函数代码，点击测试，没问题就可以进入触发管理设置定

创建触发器

这样就ok了，轻量云也能使用自动创建快照，按天备份。
