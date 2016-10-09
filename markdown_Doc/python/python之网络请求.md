###Python之网络请求
---

1 关于`or`的用法

参考 <http://blog.sina.com.cn/s/blog_3fe961ae0100nuzg.html>

事实上，python中的 `and` 和 `or` 运算符并不会返回布尔值，而是返回一个具体的比较值： 对于or而言，遇到第一个真的返回，否则返回最后一个假的；

例： 

result = "" or "hello"

result == "hello