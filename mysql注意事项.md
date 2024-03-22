1. 使用命令行登录本机mysql:

   其中`-u`指的是user，`-p`指的是password，`-h`意思是host主机。

   回车后输入密码。

   ```bash
   mysql -u root -p	# 省略-h主机对象，默认对象是主机
   mysql -h 127.0.0.1 -u root -p	
   mysql -h localhost -u root -p
   ```

2. 登录其他主机mysql，不用输入端口

   ```bash
   mysql -h 192.168.1.118 -u root -p
   ```

   