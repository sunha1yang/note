### Nginx操作

#### nginx重启和关闭
重启 nginx

- nginx -s reload：修改配置后重起
- nginx -s reopen：重新打开日志文件
- nginx -t -c /path/to/nginx.conf：测试nginx配置文件是否正确

关闭 nginx：
- nginx -s stop：快速停止nginx
- nginx -s quit：完整有序的停止nginx

其他的停止 nginx 方式：
- ps -ef | grep nginx
- kill -QUIT 主进程号：从容停止nginx
- kill -TERM 主进程号：快速停止nginx
- pkill -9 nginx    ：强制停止nginx
