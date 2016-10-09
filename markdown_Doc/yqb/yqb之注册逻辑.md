###YQB之注册逻辑
---

1 发送验证码
	
	1 校验手机号码合法性: tele
	2 核对手机签名: sign
	3 判断手机号是否已经被注册
	4 发送验证码，发送之前检查验证码发送的次数
	

**核对手机签名**

	salt: "luckin"
	sign = （telephone + salt）进行MD5加密
	
**检查发送验证码的次数**

从msyql中，根据注册电话查询当天至今`Announce`（发送验证码的记录）的个数，如果个数大于5，则提示已达验证码发送次数上限

	奇怪的是，发送验证码后，并没有插入Announce？
	
**发送验证码**

`MessageQueueProducer`

sendSmsProducer.sendMessage(json);


	