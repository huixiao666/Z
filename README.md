检测服务器状态
Vultr VPS服务器开通后，有机率会分配到被墙的IP，但胜在Vultr是按时计费的，所以可以随时销毁机器进行新IP分配（新建的机器要5分钟后才能执行销毁）。

机器开通后大概3-5分钟（一定要3-5分钟后再检测，刚新建的机器初始化中），复制机器的IP到以下网址进行ping检测，如可以检测通过就代表这个IP可用，否则，销毁机器，按前面新建机器的步骤重新来一次，再检测IP，直到IP可用。 PING工具：ping工具（检测服务器IP是否可用）

# SSH连接工具
任选其中一个即可
FinalShell(推荐):FinalShell下载
MobaXterm:MobaXterm官网

安装X-ui面板并配置节点
1、必要更新操作(Debian/Ubuntu)
apt update -y && apt install -y curl wget
**注意：**如果是centos系统，则分别运行yum update -y和yum install -y curl socat wget

2、安装x-ui
感谢github FranzKafkaYu大佬开发如此好用的一键脚本

bash <(curl -Ls https://raw.githubusercontent.com/FranzKafkaYu/x-ui/master/install.sh)
手动开放端口
Vultr目前机器只默认开放SSH端口22，其它一些端口全部需要手动开放，依次复制以下命令运行就行!注意，以下操作仅适用于Ubuntu 20.04版本系统，请在Vultr部署时选择这个版本系统
首先，需要安装防火墙，复制以下命令到ssh中运行就行

apt-get install firewalld -y && firewall-cmd --zone=public --add-port=22/tcp --permanent && firewall-cmd --reload
根据你获取的节点信息，记下节点信息中的端口（port）号，将记下的端口号替换到下方命令中的『端口』两字中，即是完整命令，运行即可、当然，x-ui面板的端口首先要开放

firewall-cmd --zone=public --add-port=端口/tcp --permanent && firewall-cmd --reload
注意，后续如果重新配置节点信息，端口有变动，切记重新运行以上放行端口的命令，不然会导致节点无法使用，切记

参考Vultr官方文档对于放行端口的说明：https://www.vultr.com/docs/firewall-quickstart-for-vultr-cloud-servers/
