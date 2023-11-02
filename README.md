## 为了减小内存中buff/cache的占用
``` 
#!/bin/bash
echo "开始清除缓存"
sync;sync;sync #写入硬盘，防止数据丢失
sleep 10#延迟10秒
echo 1 > /proc/sys/vm/drop_caches
echo 2 > /proc/sys/vm/drop_caches
echo 3 > /proc/sys/vm/drop_caches
```
## 写个定时任务
crontab -e #弹出配置文件

[path]是脚本存放目录的绝对路径
``` 
#分　 时　 日　 月　 周　 命令
0 */2 * * * [path]/drop_cache.sh 
```

## 查看服务(debian 12)
systemctl status cron
### 如果没有设置开机启动则可以设置下
systemctl enable cron

## 参考链接
https://focusss.github.io/2019/02/10/Linux%E4%B8%ADbuff-cache%E5%8D%A0%E7%94%A8%E8%BF%87%E9%AB%98%E8%A7%A3%E5%86%B3%E6%89%8B%E6%AE%B5/