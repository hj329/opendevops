### 快速安装

> 快速部署文档使用Shell脚本部署安装，此部署安装仅供参考，供用户快速体验使用

> 若线上使用我们建议用户一步步安装，并熟悉每个组件的用途，请参考： [分布式安装](http://docs.opendevops.cn/zh/latest/distributed_install.html)


**注意**

- 国内Github速度慢问题
- Docker默认镜像源下载慢问题

**建议配置**

- 系统： CentOS7+
- CPU：  2Core+
- 内存：  4G+
- 磁盘：  >=50+

**环境说明**

|     服务     |       描述        | 默认端口 | 健康检查                                                     | 安装 |
| :----------: | :---------------: | :------: | ------------------------------------------------------------ | ---- |
|     codo     |     项目前端      |  80/443  | openresty -t                                                 | 必须 |
|  codo-admin  |     项目后端      |   8001   | curl -I -X GET -m  10 -o /dev/null -s -w %{http_code}  http://$mg_domain:8010/are_you_ok/ | 必须 |
|  codo-cmdb   | 资产管理/跳板审计 |   8002   | curl -I -X GET -m  10 -o /dev/null -s -w %{http_code}  http://${cmdb_domain}:8002/v1/cmdb/ | 必须 |
|  codo-task   |     任务系统      |   8020   | curl -I -X GET -m  10 -o /dev/null -s -w %{http_code}  http://$task_domain:8020/are_you_ok/ | 必须 |
|  codo-cron   |     定时任务      |   9900   | curl -I -X GET -m  10 -o /dev/null -s -w %{http_code}  http://${cron_domain}:9900/are_you_ok/ | 必须 |
|   kerrigan   |     配置中心      |   8030   | curl -I -X GET -m  10 -o /dev/null -s -w %{http_code}  http://${kerrigan_domain}:8030/are_you_ok/ | 必须 |
|  codo-check  |     代码检查      |   N/A    | 提供脚本示例                                                 | 可选 |
| codo-publish |     发布脚本      |   N/A    | 提供脚本示例                                                 | 可选 |
| codo-res_app |     资源申请      |   N/A    | 提供脚本示例                                                 | 可选 |




**开始使用**

- 所有项目都放到/opt/codo/
- 修改环境变量文件env.sh,主要修改IP地址和域名信息，Token,Key可默认
- Other,由于没法完全适配环境，网络问题/其余常见报错问题请自行处理重试安装。


```
$ mkdir -p /opt/codo/
$ cd /opt/codo/ && git clone https://github.com/opendevops-cn/opendevops.git
$ cd opendevops && sh deploy.sh
```
