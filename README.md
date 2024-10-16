# chatgpt网关私有化部署方案

## 写在前面
~~本安装教程仅用来体验私有化部署流程，不建议生产环境大规模使用，有本地化部署诉求联系vx~~

~~注意：：**网关支持转API，详情联系vx**~~

2024年10月15日更新，本项目转为闭源免费使用，可一键部署个人chatgpt网关

机器剩余时长提供免费备用网关，大家自行使用，从哪里来到哪里去，感谢demo.xyhelper社区

免费网关地址：https://demo.closeoai.com

chat2api-plus：https://github.com/hanglegehang/chat2api-plus

自建v6代理池教程：编写中

欢迎加v探讨技术问题，随时欢迎👏🏻

<img width="200" alt="image" src="https://github.com/user-attachments/assets/57e790ce-de17-4247-8b6a-0b754585b36b">


## 部署流程

### 安装网关

执行一键部署脚本

```
curl -sSfL -o gateway-node-quick-install.sh https://raw.githubusercontent.com/wm-chatgpt/chatgpt-gateway-node-deploy/main/gateway-node-quick-install.sh && bash gateway-node-quick-install.sh

```
##### 安装说明
AuthKey : 接口访问秘钥，对应share配置中的AuthKey，填写free为裸奔模式，忽略鉴权

Licence : "xiaohuasheng666"

脚本安装成功后会打印网关地址，可以自行配置反代、https等，处理完成后修改share启动参数即可：

```
CHATPROXY: "http://部署节点机器IP:8100"

AUTHKEY: "你配置的值"
```
#### 配置项说明
配置文件目录`/root/chatgpt-gateway-node/config.yaml`
```
LICENCE : "xiaohuasheng666"

# 代理节点地址，默认无代理，v4和v6均可
PROXY_URL :
  - socks5://xx:yy@111.222.333.444:8443

# 管理后台密码
WEB_PASSWORD: "123789"

AUTH_KEY : 网关访问秘钥，填free，则忽视鉴权，开启裸奔模式

#网关节点参与代理，默认参与，不支持热更新
GATEWAY_ENABLE_PROXY: true

# POW计算节点地址，分布式计算pow，节点安装见下方
POW_URL_LIST:
  - "http://ip:8900"
```
