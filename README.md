# moni-swas
监控阿里云轻量应用服务器，并通过调用官方 API 让服务器在宕机（无法回应 HTTP 请求）时自动重启，同时通过 Web 页面实时展示一些信息。

## 工作原理
把 Moni 部署在一个**确保稳定**的监控服务器上（比如你的 GCP 免费层级美国小鸡），Moni 会每隔几秒请求从被监控服务器下载一个极小的文件。
你可以设置一个超时时间（比如两秒），若连续一定次数出现超时错误或其它错误，则监控服务器会向阿里云发送重启目标服务器的请求，并等待 5 分钟，然后继续监测。

## 注意
Moni 会开机自启动而且占用极小，不过请确保你的监控服务器不会宕机。你可以方便地通过 Web 页面来查看 Moni 的实时监控报告。
