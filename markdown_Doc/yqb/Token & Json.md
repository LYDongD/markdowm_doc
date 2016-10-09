###Token
---

**token的生成机制**

0 token的作用

	1 屏蔽伪请求，显然没有token的请求是伪造/无效的请求
	2 防止假token， 对token进行解密，可以获取期望的信息，否则就是假token
	3 token包含了客户端的唯一标示，可以进行身份验证
	
YQB项目对token的处理方式有点`诡异`，无论token是否为空，是否过期，都会返回一个新的token；当请求token为空时，新的token标记为过期失效，userId = null，并不会单独进行处理。

1 token的原始字符串

	第一部分：firt_str = 14位随机数|用户ID|登陆时间|有效期分钟|
	第二部分：last_str = 64 - firt_str
	token_str = first_str + second_str
	

2 token的加密机制

	AES256 进行加密/解密
	
3 token过期判断
	
	对token串进行解密，获取userid和login_date, 当前时间和login_date进行分差计算，和valid_minute进行比较，超过则过期
	
`YQB项目弃用了token过期的机制，即token不为空时，永远也不会过期`


###Json
---
参考文献：

<http://www.zhihu.com/question/27242003>

简要谈一下Gson的使用

**1 new Gson().toJson(Object)**

快速将对象序列化成json字符串，可是并没有格式化pretty()

**2 使用GsonBuilder创建Gson实例，并能设置json转换的属性(`工厂模式？`)**

 	static Gson gson = null;

    static {
        GsonBuilder gsonBuilder = new  GsonBuilder().setPrettyPrinting();
        gson = gsonBuilder.create();
    }
    
使用了prettyPrint的模式，打印时将格式化json字符串


**3 比较完备的写法**

	private static Gson seriaGson = null;
	
	private static GsonBuilder gsonBuilder = new GsonBuilder(); 
	
	static{
		 gsonBuilder.setPrettyPrinting()
	    .disableHtmlEscaping()
	    .serializeNulls()
	    .setDateFormat("yyyy-MM-dd HH:mm:ss");
		 seriaGson = gsonBuilder.create();
	}