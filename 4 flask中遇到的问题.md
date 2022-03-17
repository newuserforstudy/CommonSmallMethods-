《flask中遇到的问题以及解决方法》

1 OSError: [Errno 98] Address already in use

- lsof -i:5000 查看端口占用情况，记录PID
- kill -9 PID  杀死端口
- 重新启动flask  服务器，完毕。

