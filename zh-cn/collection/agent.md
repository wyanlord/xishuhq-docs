# Agent安装

 Agent可以在本地主机（Linux、Windows、MacOS）、容器化环境（Docker、Kubernetes）和本地数据中心运行。您可以全界面化管理 Agent 的运行状态、启停、升级和卸载。


## Linux 安装 Agent

 现支持的Linux操作系统以及它们对应的 CPU 架构如下：

 支持：✅，不支持：✖️，未验证：❓  
 
| 操作系统                  | 处理器架构                | 支持情况| Keta-Agent支持版本 | APM自动注入 | 备注                                    |
|-|-|-|-|-|-|
| Kylin（银河麒麟） V10     | x86_64                    | ✅ |v1.3.3.2 ~ newest       | ✅           |                                            |
| Kylin（银河麒麟） V10     | aarch64                   | ✅| v1.3.3.2 ~ newest       | ✅           |                                            |
|Kylin（银河麒麟） V10   | 海光（基于x86_64）        | ✅| v1.3.3.2 ~ newest       | ❓           |                                            |
|Kylin（银河麒麟） V10   | 鲲鹏（基于aarch64）        | ✅| v1.3.3.2 ~ newest       |  ✅            |                                            |
| CentOS/RHEL6.x            | x86_64、aarch64           | ✅| v1.3.4.2 ~ newest      | ✖️          | 安装时请确保关闭“链路数据采集”                |
| CentOS/RHEL7.x            | x86_64                    | ✅ |v1.2.3 ~ newest         | ✅           |                                            |
| CentOS8.x                 | x86_64、aarch64           | ✅| v1.2.3 ~ newest         | ✅           |                                            |
| RHEL8.x                   | x86_64、aarch64           | ✅| v1.2.3 ~ newest         | ✖️          |                                            |
| Ubuntu14.04               | x86_64                    | ✅| v1.2.3 ~ newest         | ✅           |                                            |
| Ubuntu16.04               | x86_64                    | ✅| v1.2.3 ~ newest         | ✅           |                                            |
| Ubuntu18.04               | x86_64                    | ✅| v1.2.3 ~ newest         | ✅           |                                            |
| Ubuntu20.04               | x86_64、aarch64           | ✅| v1.2.3 ~ newest         | ✅           |                                            |
| Ubuntu22.04               | x86_64、aarch64           | ✅ |v1.2.3 ~ newest         | ✅           |                                            |
| Debian7.4                 | x86_64                    | ✅| v1.2.3 ~ newest         | ✅           |                                            |
| Debian8.11                | x86_64                    | ✅| v1.2.3 ~ newest         | ✅           |                                            |
| Debian9.0                 | x86_64                    | ✅| v1.2.3 ~ newest         | ✅           |                                            |
| Debian10.12               | x86_64                    | ✅| v1.2.3 ~ newest         | ✅           |                                            |
| Debian11.4                | x86_64                    | ✅ |v1.2.3 ~ newest         | ✅           |                                            |
| Debian12.0                | x86_64                    | ✅ |v1.2.3 ~ newest         | ✅           |                                            |
| Debian12.0                           | aarch64                   | ✅ |v1.2.3 ~ newest         | ✅           |                                            |

Linux支持手动安装和自动安装
- 手动安装：在机器上通过安装脚本手动安装新的Agent。可以选择或新建标签，填写网卡名称，选择是否开机自启（安装客户端用户需为root账户），点击获取安装密码命令，在对应机器上安装即可。
- 自动安装：通过ssh连接自动安装方式安装Agent，需要被录入机器开启ssh功能，且机器IP能够被Agent服务访问。

### 手动安装
在机器上通过安装脚本手动安装新的客户端。可以选择或新建标签，填写网卡名称，选择是否开机自启（安装Agent用户需为root账户），点击获取安装命令，在对应机器上安装即可。

安装步骤如下：

1.  机器管理 > 点击添加机器
2. 选择Linux >手动安装，完成如下配置获取安装命令：
![选择机器.png](/appassets/keta_docs/image/static/assets/agent_machine/197d9258-3300-4df8-aeb2-8e59726cd613.png)

|配置项|说明|
|-|-|
|机器标签|填写要安装采集客户端的机器所属标签，标签作为客户端分组属性，便于用户从机器组维度统一管理机器资源及分发采集任务，多个使用","隔开|
|网卡名称|输入网卡名称，不填写则系统自动检测可用网卡|
|安装路径|指定客户端安装路径，不填写则系统将默认安装到默认路径下, root 用户：`/usr/local/ketad/agent`, 非 root 用户：`$HOME/ketad/agent`|
|系统架构|根据选择的操作系统类型，选择系统架构，默认选中最新版本|
|Agent版本|根据选择的操作系统类型和系统架构，选择要安装的Agent版本，默认选中最新版本|
|开机自启|选择开启开机自启后，服务器开机后客户端可以自行启动运行|

3. 点击获取安装，复制安装命令，在机器上安装部署。
4. 在机器上完成安装部署后，返回机器管理页，刷新即可查看所添加机器。

### 自动安装 
通过ssh连接自动安装方式安装Agent，需要被录入机器开启ssh功能，且机器IP能够被Agent服务访问。
安装步骤如下：
1. 机器管理 > 点击添加机器
2. 选择Linux >自动安装，完成如下配置：
![linux手动.png](/appassets/keta_docs/image/static/assets/agent_machine/513dc2bb-239b-4998-9580-97ddfda49fc5.png)

|配置项|说明|
|-|-|
|机器IP|填写要安装客户端的机器IP地址，多个使用","隔开|
|网卡名称|服务器存在多张网卡的情况，指定安装的服务器使用的网卡名称，不填写则系统自动检测使用可用网卡|
|安装路径|指定客户端安装路径，不填写则系统将默认安装到系统根目录下|
|SSH端口|输入SSH端口号，不填写则默认使用22端口|
|登录方式|登录机器方式，包括密钥或密码，①选择密码则填写用户名及密码选；②择密钥则填写用户名并上传私钥文件。密钥生成步骤如下：1、使用ssh-keygen -m PEM生成密钥；2、将公钥: id_rsa.pub文件中的内容写至keta-agent安装机器的～/.ssh/authorized_keys文件中；将私钥[id_rsa]文件上传到KetaOps|
|机器标签|填写要安装采集客户端的机器所属标签，标签作为客户端分组属性，便于用户从机器组维度统一管理机器资源及分发采集任务，多个使用","隔开|
|系统架构|根据选择的操作系统类型，选择系统架构，默认选中最新版本|
|Agent版本|根据选择的操作系统类型和系统架构，选择要安装的Agent版本，默认选中最新版本|

3. 点击验证连通性可以预览ssh连通性，机器连通情况下才能进行Agent安装。
4. 确认连通性后点击安装完成自动安装流程，客户端安装需要一段时间，点击关闭可以退出当前界面在后台进行安装，安装完成后您可在通知中心查看安装情况。
5. 返回机器管理页，刷新即可查看所添加机器。

注意，自动安装的本地目录为：

- Linux用户root权限：`/usr/local/ketad/agent`
- Linux用户非root权限：`$HOME/ketad/agent`当前用户的主目录下。
 
 
 ## Windows 安装 Agent
Windows需要手动安装Agent，在机器上通过安装脚本手动安装新的Agent。可以选择或新建标签，填写网卡名称，选择是否开机自启（安装Agent用户需为Administrator账户），点击获取安装脚本和命令，在对应机器上安装即可。

 现支持的Windows 操作系统以及它们对应的 CPU 架构如下：
 
|windows操作系统|版本|cpu架构|
|-|-|-|
|windows server |2008、2012、2016、2019、2022|x86_64|
|windows  |7、10|x86_64|


安装步骤如下：

1.  机器管理 > 点击添加机器
2. 选择Windows ，完成如下配置获取安装命令和脚本：
![windowsagent.png](/appassets/keta_docs/image/static/assets/agent_machine/c72a8a3d-eb08-40a7-b678-f360d3067fab.png)

|配置项|说明|
|-|-|
|机器标签|填写要安装采集客户端的机器所属标签，标签作为客户端分组属性，便于用户从机器组维度统一管理机器资源及分发采集任务，多个使用","隔开|
|网卡名称|输入网卡名称，不填写则系统自动检测可用网卡|
|安装路径|指定客户端安装路径，不填写则系统将默认安装到默认路径下。Administrator 用户权限：`C:\Program File\ketad\agent`, 非 Administrator 权限：`C:\ketad\agent`|
|系统架构|根据选择的操作系统类型，选择系统架构，默认选中最新版本|
|Agent版本|根据选择的操作系统类型和系统架构，选择要安装的Agent版本，默认选中最新版本|
|开机自启|选择开启开机自启后，服务器开机后客户端可以自行启动运行|
|Windows服务|选择Windows服务模式后，Agent将以windows服务的模式运行（推荐）|

3. 点击获取安装，复制安装命令，在机器上安装部署。

说明：
`a.PowerShell 3.0及以上版本（windows10、windows server2012及以上默认使用的PowerShell版本为3.0+）：直接执行安装命令。
b.PowerShell 3.0以下版本：先手动下载installer.vbs的安装脚本，然后执行安装命令。`

4. 在机器上完成安装部署后，返回机器管理页，刷新即可查看所添加机器。


## MacOS 安装 Agent
MacOS支持手动安装和自动安装
- 手动安装：在机器上通过安装脚本手动安装新的Agent。可以选择或新建标签，填写网卡名称，点击获取安装密码命令，在对应机器上安装即可。
- 自动安装：通过ssh连接自动安装方式安装Agent，需要被录入机器开启ssh功能，且机器IP能够被Agent服务访问。

### 手动安装
在机器上通过安装脚本手动安装新的客户端。可以选择或新建标签，填写网卡名称，点击获取安装命令，在对应机器上安装即可。

安装步骤如下：

1.  机器管理 > 点击添加机器
2. 选择MacOS >手动安装，完成如下配置获取安装命令：
![MacOS_手动.png](/appassets/keta_docs/image/static/assets/agent_machine/be8dc5dc-124d-4201-9293-a90978fcef68.png)

|配置项|说明|
|-|-|
|机器标签|填写要安装采集客户端的机器所属标签，标签作为客户端分组属性，便于用户从机器组维度统一管理机器资源及分发采集任务，多个使用","隔开|
|网卡名称|输入网卡名称，不填写则系统自动检测可用网卡|
|安装路径|指定客户端安装路径，不填写则系统将默认安装到系统默认目录下：`$HOME/ketad/agent`|
|系统架构|根据选择的操作系统类型，选择系统架构，默认选中最新版本|
|Agent版本|根据选择的操作系统类型和系统架构，选择要安装的Agent版本，默认选中最新版本|
|开机自启|选择开启开机自启后，服务器开机后客户端可以自行启动运行|

3. 点击获取安装，复制安装命令，在机器上安装部署。
4. 在机器上完成安装部署后，返回机器管理页，刷新即可查看所添加机器。

### 自动安装 
通过ssh连接自动安装方式安装Agent，需要被录入机器开启ssh功能，且机器IP能够被Agent服务访问。
安装步骤如下：
1. 机器管理 > 点击添加机器
2. 选择MacOS >自动安装，完成如下配置：
![MacOS_自动.png](/appassets/keta_docs/image/static/assets/agent_machine/f88b38a6-83bd-498b-8ed1-eca171db41b4.png)

|配置项|说明|
|-|-|
|机器IP|填写要安装客户端的机器IP地址，多个使用","隔开|
|网卡名称|服务器存在多张网卡的情况，指定安装的服务器使用的网卡名称，不填写则系统自动检测使用可用网卡|
|安装路径|指定客户端安装路径，不填写则系统将默认安装到系统根目录下|
|SSH端口|输入SSH端口号，不填写则默认使用22端口|
|登录方式|登录机器方式，包括密钥或密码，①选择密码则填写用户名及密码选；②择密钥则填写用户名并上传私钥文件。密钥生成步骤如下：1、使用ssh-keygen -m PEM生成密钥；2、将公钥: id_rsa.pub文件中的内容写至keta-agent安装机器的～/.ssh/authorized_keys文件中；将私钥[id_rsa]文件上传到KetaOps|
|机器标签|填写要安装采集客户端的机器所属标签，标签作为客户端分组属性，便于用户从机器组维度统一管理机器资源及分发采集任务，多个使用","隔开|
|系统架构|根据选择的操作系统类型，选择系统架构，默认选中最新版本|
|Agent版本|根据选择的操作系统类型和系统架构，选择要安装的Agent版本，默认选中最新版本|

3. 点击验证连通性可以预览ssh连通性，机器连通情况下才能进行Agent安装。
4. 确认连通性后点击安装完成自动安装流程，客户端安装需要一段时间，点击关闭可以退出当前界面在后台进行安装，安装完成后您可在通知中心查看安装情况。
5. 返回机器管理页，刷新即可查看所添加机器。

注意，自动安装的本地目录为：`$HOME/ketad/agent`当前用户的主目录下。

##  Ansible 安装 Agent

支持通过 ansible-play 进行部署.可直接按照页面步骤进行操作。

### 配置
![ansible.png](/appassets/keta_docs/image/static/assets/agent_machine/1f0d4c83-7bd9-46a1-ba75-3d5e1a34f78a.png)

|配置项|说明|
|-|-|
|机器标签|填写要安装采集客户端的机器所属标签，标签作为客户端分组属性，便于用户从机器组维度统一管理机器资源及分发采集任务，多个使用","隔开|
|网卡名称|输入网卡名称，不填写则系统自动检测可用网卡|
|安装路径|指定客户端安装路径，不填写则系统将默认安装到系统根目录下|
|系统架构|根据选择的操作系统类型，选择系统架构，默认选中最新版本|
|Agent版本|根据选择的操作系统类型和系统架构，选择要安装的Agent版本，默认选中最新版本|
|开机自启|选择开启开机自启后，服务器开机后客户端可以自行启动运行|

 要求

- Ansible v2.6+
- 支持 Linux, macOS

具体的 [Ansible](https://www.ansible.com/) 部署和环境准备请参考 [Ansible 文档](https://docs.ansible.com/)

### 安装

首先通过页面下载并配置 keta-Agent role.

在 `配置->Agent 采集->机器->添加机器` 页面, 切换到 Ansible 标签页, 通过页面上的链接下载 keta-Agent 的 ansible-role 压缩包. 将压缩包解压到当前用户的 `.ansible/roles` 下, 或者放置到 `/etc/ansible/roles` 下.

使用 keta-Agent role 来部署 keta-Agent, 可以在 Ansible 标签页配置并生成类似如下的 ansible-play 执行脚本:

```yaml
- hosts: servers
  roles:
    - { role: xishuhq.keta-Agent, become: yes }
  vars:
    keta_url: "<YOUR_KETA_DB_URL>" # required, like: "http://ketadb"
    keta_token: "<YOUR_KETA_DC_TOKEN>" # required
    keta_endpoints: "<YOUR_KETA_DC_ENDPOINTS>" # required, like: "ip1:port ip2:port"
    keta_tags: "<YOUR_KETA_DC_TAGS>" # required, like "a b c"
    keta_ketad_arch: "<YOUR_KETA_DC_ARCH>" # optional, default use host architecture
    keta_ketad_version: "<YOUR_KETA_DC_VERSION>" # optional, default use the lastest ketad
    keta_ketad_path: "<YOUR_KETAD_PATH>" # optional
    keta_ketad_boot: "<TRUE_OR_FALSE>" # optional, default false, only work with root user
    keta_region: "<YOUR_KETA_DC_REGION>" # optional
    keta_net_interface: "<YOUR_KETA_DC_NET_INTERFACE>" # optional
```

保存上述脚本为任意名称, 如 `installer.yaml`, 之后可以通过如下命令在客户端主机上进行部署:
```shell
# 检查配置
ansible-playbook installer.yaml --check
# 运行下载的安装脚本
ansible-playbook installer.yaml
# 如果你的主机需要密码，可通过下面命令安装
ansible-playbook installer.yaml --ask-pass
```

## Docker 环境安装 Agent

### 配置

如果你需要通过 docker 方式安装 keta-agent, 可以通过以下命令进行:

```
docker run -d --name keta-agent \
--network host \
-v /var/run/docker.sock:/var/run/docker.sock:ro \
-v /:/hostfs:ro \
-e KETAD_HOST_PROC="/hostfs/proc" \
-e KETAD_HOST_SYS="/hostfs/sys" \
-e KETAD_HOST_ETC="/hostfs/etc" \
-e KETAD_HOST_VAR="/hostfs/var" \
-e KETAD_HOST_RUN="/hostfs/run" \
-e KETAD_HOST_DEV="/hostfs/dev" \
-e KETAD_TOKEN=<KETA_COLLECT_TOKEN> \
-e KETAD_ENDPOINTS=<KETA_ENDPOINTS> \
-e KETAD_TAGS=<KETA_TAGS> \
-e KETAD_STANDALONE="false" \
-e KETAD_RUNTIME="docker" \
ccr.ccs.tencentyun.com/ketaops/keta-agent:latest
```

### 环境变量

#### 全局

| ENV VARIABLE      | DESCRIPTION                                           |
| ----------------- | ----------------------------------------------------- |
| KETAD_META_PATH   | 自定义采集 meta 文件路径                              |
| KETAD_MAX_PROCS   | 设置 agent 可使用的最大 cpu 数量                      |
| KETAD_KETAD_PPROF | 设置 ketad pprof 服务, 默认不开启:`0.0.0.0:1234`      |
| KETAD_AGENT_PPROF | 设置 keta-agent pprof 服务, 默认不开启:`0.0.0.0:1234` |
| KETAD_TAGS        | agent tags, 通过空格分割:`tag1 tag2`                  |
| KETAD_ID_FILE     | 自定义采集 agent id 文件路径                          |

#### 网络

| ENV VARIABLE        | DESCRIPTION                                               |
| ------------------- | --------------------------------------------------------- |
| KETAD_STANDALONE    | bool, 是否独立运行, 为 true 时, 不连接 ketadb, 默认 false |
| KETAD_ENDPOINTS     | ketadb 地址, 通过空格分割:`1.1.1.1:1234 2.2.2.2:1234`     |
| KETAD_TOKEN         | 连接 ketadb 使用的 token                                  |
| KETAD_NET_INTERFACE | 设置注册时使用的网卡名称                                  |

#### 日志

| ENV VARIABLE                | DESCRIPTION                                                  |
| --------------------------- | ------------------------------------------------------------ |
| KETAD_KETAD_LOG_LEVEL       | agent 的 log 等级:debuginfo(default)warnerrorpanicfatal      |
| KETAD_KETAD_LOG_FILE        | ketad 日志路径                                               |
| KETAD_KETAD_LOG_MAX_SIZE    | ketad 日志最大大小, 单位 MB, 默认 100MB                      |
| KETAD_KETAD_LOG_MAX_AGE     | ketad 日志最大保存天数, 默认                                 |
| KETAD_KETAD_LOG_MAX_BACKAGE | ketad 日志最大保存数量                                       |
| KETAD_AGENT_LOG_LEVEL       | keta-agent 的 log 等级:debuginfo(default)warnerrorpanicfatal |
| KETAD_AGENT_LOG_FILE        | ketad 日志路径                                               |
| KETAD_AGENT_LOG_MAX_SIZE    | keta-agent 日志最大大小, 单位 MB, 默认 100MB                 |
| KETAD_AGENT_LOG_MAX_AGE     | keta-agent 日志最大保存天数, 默认                            |
| KETAD_AGENT_LOG_MAX_BACKAGE | keta-agent 日志最大保存数量                                  |

#### 杂项

| ENV VARIABLE            | DESCRIPTION               |
| ----------------------- | ------------------------- |
| KETAD_KETAD_CONFIG_FILE | ketad 的配置文件路径      |
| KETAD_AGENT_CONFIG_FILE | keta-agent 的配置文件路径 |

## Kubernetes 环境下安装 Agent

### 依赖

在 k8s 环境下安装 ketad 需要如下依赖:

- Kubernetes Cluster version >= v1.14.x

- [`Helm`](https://helm.sh/) >= v3.x, 用于部署和管理 keta-agent 集群
- [`Kubectl` CLI](https://kubernetes.io/docs/tasks/tools/install-kubectl/) 用于管理 keta-agent 节点

### 部署

1. helm 本地仓库添加 keta-agent chart 源:

   ```
   helm repo add keta-chart http://chart-prod.ketaops.cc
   ```

   同时可以通过以下命令更新 keta-agent chart 版本:

   ```
   helm repo update keta-chart
   ```

2. 创建一个配置文件, 其中包含 keta-agent 部署所需要的配置. 示例配置如下:

    ```yaml
    # 设置集群名称
   cluster: default
   
   # 环境变量
   env:
     ## 设置采集器注册时的 tags
     KETAD_TAGS:
     ## 设置采集器连接的 ketadb 地址
     KETAD_ENDPOINTS:
     ## 设置采集器连接使用的 token
     KETAD_TOKEN:
     ## 采集器使用的 cpu 数量
     KETAD_MAX_PROCS: 1
     ## 设置 ketad 的 pprof 地址, 不填写时不开启 pprof
     KETAD_KETAD_PPROF:
     ## 设置 keta-agent 的 pprof 地址, 不填写时不开启 pprof
     KETAD_AGENT_PPROF:
     ## 设置采集器独立运行(无需连接 ketadb)
     KETAD_STANDALONE: false
     ## 设置采集器使用的网卡信息, 默认无需设置, 自动选择网卡信息
     KETAD_NET_INTERFACE:
     ## ketad 日志级别, 支持 debug, info, warn, error, dpanic, panic, fatal
     KETAD_KETAD_LOG_LEVEL: info
     ## ketad 日志输出文件, stdout 代表往 stdout端输出, 默认为 ketad.log
     KETAD_KETAD_LOG_FILE: stdout
     ## ketad 日志最大大小，单位MB
     KETAD_KETAD_LOG_MAX_SIZE: 100
     ## ketad 日志最大保存数量
     KETAD_KETAD_LOG_MAX_BACKUPS: 3
     ## ketad 日志最大保存天数
     KETAD_KETAD_LOG_MAX_AGE: 3
     ## keta agent 日志级别, 支持 debug, info, warn, error, dpanic, panic, fatal
     KETAD_AGENT_LOG_LEVEL: info
     ## keta agent 日志输出文件, stdout 代表往 stdout端输出, 默认为 keta-agent.log
     KETAD_AGENT_LOG_FILE:
     ## keta agent 日志最大大小，单位MB
     KETAD_AGENT_LOG_MAX_SIZE: 100
     ## keta agent 日志最大保存数量
     KETAD_AGENT_LOG_MAX_BACKUPS: 3
     ## keta agent 日志最大保存天数
     KETAD_AGENT_LOG_MAX_AGE: 3
     ## ketad 配置文件路径, 默认无需设置
     KETAD_KETAD_CONFIG_FILE:
     ## keta agent 配置文件路径, 默认无需设置
     KETAD_AGENT_CONFIG_FILE:
   
   image:
     ## 采集器镜像仓库地址
     repository: docker.ketaops.cc/ketaops/keta-agent
     ## 采集器镜像版本
     tag: "v1.2.0"
     ## 镜像的拉取策略(Kubernetes imagePullPolicy)
     pullPolicy: Always
   
   # 覆盖 app 名称
   nameOverride: ""
   # 覆盖 app 名称
   fullnameOverride: ""
   
   # 添加控制账号
   serviceAccount:
     ## 添加到服务帐户的注释
     annotations: {}
     ## 要使用的服务帐户的名称。如果未设置且 create 为真，则使用全名模板生成名称
     name: ""
   
   # 支持使用Deployment部署和使用DaemonSet方式部署，另外指定为k8s-monitor时将同时部署DaemonSet和Deployment
   deployMethod: k8s-monitor
   
   # 指定部署 Deployment 集群 agent 数量
   replicaCount: 1
   
   
   # Agent 集群 pod 的注释信息
   podAnnotations: {}
   #   key: "value"
   
   metaCache:
     enabled: true  # 是否持久化meta文件，开启后，可指定meta信息存放路径和.agentid文件存放路径，启用此配置时需要将securityContext.runAsUser设置为0，否则将无权限写入host主机目录
     mountPath: /home/ketad/agent-cache  # 容器内部meta文件以及.agentid所在目录
     hostPath: /var/keta-agent  # 宿主机中meta文件挂载目录，实际目录: {{ .Values.metaCache.hostPath }}/{{ .Release.Namesapce }}/{{ .Release.Name }}
   
   
   # 资源限制
   resources:
     limits:
       cpu: 1
       memory: 1Gi
     requests:
       cpu: 100m
       memory: 128Mi
   
   # 允许 DaemonSet 在选定的节点上进行调度
   # 参考: https://kubernetes.io/docs/user-guide/node-selection/
   nodeSelector: {}
   
   # 允许在污点节点上进行调度（需要 Kubernetes >= 1.6）
   tolerations: 
   - operator: "Exists"
   
   # 允许 DaemonSet 使用关联规则进行调度
   # 参考: https://kubernetes.io/docs/concepts/configuration/assign-pod-node/#affinity-and-anti-affinity
   affinity: {}
   
   # 是否采集k8s指标，使用DaemonSet部署时采集每个节点的kubelet指标，使用Deployment部署时采集k8s集群的指标
   kubernetesMetric:
     enabled: true
   
   hostMetric:
     enabled: true
     env:
       KETAD_HOST_PROC: /hostfs/proc
       KETAD_HOST_SYS: /hostfs/sys
       KETAD_HOST_ETC: /hostfs/etc
       KETAD_HOST_VAR: /hostfs/var
       KETAD_HOST_RUN: /hostfs/run
       KETAD_HOST_DEV: /hostfs/dev
     volumes:
       - name: root-dir
         hostPath:
           path: /
     volumeMounts:
       - name: root-dir
         mountPath: /hostfs
         readOnly: true
   
   # 设置自动发现kubernetes功能, 仅在 DaemonSet 模式下生效
   discoveryKubernetes:
     enabled: true
     env:
       # 设置 kubernetes 采集连接配置路径, 默认无需设置使用容器内 k8s 环境变量进行连接
       #KETAD_DISCOVERY_KUBERNETES_KUBECONFIG: ".kube/config"
       # 设置 kubernetes 采集节点名称限制
       #KETAD_DISCOVERY_KUBERNETES_NODE_NAME: ""
       # 设置 kubernetes 节点运行时环境, 支持 Docker, CRI-O, ContainerD, 默认会自动探测无需设置, 参数 "docker, crio, containerd"
       #KETAD_DISCOVERY_KUBERNETES_CONTAINER_RUNTIME: ""
       # 设置 kubernetes 节点运行时 socket 连接路径, 不填写默认会使用默认路径
       # Docker 的默认路径为 "unix:///var/run/docker.sock"
       # CRI-O 的默认路径为 "unix:///var/run/crio/crio.sock"
       # ContainerD 的默认路径为 "unix:///var/run/containerd/containerd.sock"
       #KETAD_DISCOVERY_KUBERNETES_RUNTIME_ENDPOINTS: ""
       # 设置 kubernetes pod 日志存储路径前缀, 容器 stdout 日志路径相关
       KETAD_DISCOVERY_KUBERNETES_POD_LOG_DIR_PREFIX: "/var/log/pods"
       # 设置 kubernetes 主机 proc 映射路径前缀, 容器内日志路径相关
       KETAD_DISCOVERY_KUBERNETES_PROC_DIR_PREFIX: "/hostfs/proc"
       # 设置日志监听采集功能
       KETAD_DISCOVERY_KUBERNETES_EVENTS_COLLECT_LOG_ENABLED: true
     volumes:
       # need map container's storage, e.g. host:/var/lib/docker to container:/var/lib/docker
       - name: containerfs
         hostPath:
           path: /var/lib/docker
       - name: pod-log-dir
         hostPath:
           path: /var/log/pods
       - name: dockersocket
         hostPath:
           path: /var/run/docker.sock
       - name: containerdsocket
         hostPath:
           path: /var/run/containerd/containerd.sock
       - name: criosocket
         hostPath:
           path: /var/run/crio/crio.sock
       - name: root-dir
         hostPath:
           path: /
     volumeMounts:
       # need map container's storage, e.g. host:/var/lib/docker to container:/var/lib/docker
       - name: containerfs
         mountPath: /var/lib/docker
         readOnly: true
       - name: pod-log-dir
         mountPath: /var/log/pods
         readOnly: true
       - name: dockersocket
         mountPath: /var/run/docker.sock
         readOnly: true
       - name: containerdsocket
         mountPath: /var/run/containerd/containerd.sock
         readOnly: true
       - name: criosocket
         mountPath: /var/run/crio/crio.sock
         readOnly: true
       - name: root-dir
         mountPath: /hostfs
         readOnly: true
   
   # 事件监听开关
   eventListen:
     enabled: true
     service:
       labels: {}
       type: NodePort
       nodePort: ""
       annotations: {}
       ports:
         collect: "10007"
         preview: "10006"
       loadBalancerIP: ""
       loadBalancerSourceRanges: []
       extraPorts: []
   
     ingress:
       enabled: false
       annotations:
         nginx.ingress.kubernetes.io/proxy-body-size: "1024m"
         kubernetes.io/ingress.class: nginx
   
       path: /
       hostsSuffix:
         - example.com  # {{ .Release.Name }}.{{ Release.Namespace }}.example.com
   
   
   # 指定是否使用宿主机网络, 为 true 时需同时指定 pandoraHeartBeat 参数为外部地址
   hostNetwork: true
   
   volumes:
   #   - name: varlibdockercontainers
   #     hostPath:
   #       path: /var/lib/docker/containers
   #       type: Directory
   #   - name: varlogs
   #     hostPath:
   #       path: /var/log
   #       type: Directory
   #   - name: apiservertestlog
   #     hostPath:
   #       path: /root/test-apiserver
   #       type: DirectoryOrCreate
   #   - name: docker-sock
   #     hostPath:
   #       path: /var/run/docker.sock
   
   volumeMounts:
   #   - name: varlibdockercontainers
   #     mountPath: /var/lib/docker/containers
   #     readOnly: true
   #   - name: varlogs
   #     mountPath: /var/log
   #     readOnly: true
   #   - name: apiservertestlog
   #     mountPath: /root/test-apiserver
   #     readOnly:  true
   #   - name: docker-sock
   #     mountPath: /var/run/docker.sock
   
   # 覆盖默认的 Agent 就绪探测设置
   readinessProbe:
     initialDelaySeconds: 5
     periodSeconds: 5
    ```

3. 通过以下命令检查 keta-agent 部署配置文件是否可以正常运行:

   ```shell
   helm install ketad keta-chart/ketad --dry-run -f /path/to/your/keta-agent.yaml -n <namespace> --set env.KETAD_TOKEN=<KETAD_TOKEN> --set env.KETAD_ENDPOINTS=<KETAD_ENDPOINTS> --set env.KETAD_TAGS=<KETAD_TAGS> --set env.KETAD_RUNTIME="kubernetes"
   ```

4. 通过以下命令部署 keta-agent:

   ```shell
    helm install ketad keta-chart/ketad -f /path/to/your/keta-agent.yaml -n <namespace> --set env.KETAD_TOKEN=<KETAD_TOKEN> --set env.KETAD_ENDPOINTS=<KETAD_ENDPOINTS> --set env.KETAD_TAGS=<KETAD_TAGS> --set env.KETAD_RUNTIME="kubernetes"
   ```

### 清理

通过以下命令清理 keta-agent 使用的 Kubernetes 资源:

```shell
helm uninstall ketad -n <namespace>
```

## OpenShift 环境部署 Agent

从1.2.0版本开始，KetaAgent 支持 OpenShift。

RedHat OpenShift 是一个基于 Kubernetes 容器编排器的开源容器应用平台，用于企业应用的开发和部署。

要安装 Agent，请参阅适用于 Kubernetes 的 Agent 安装说明。默认配置针对 OpenShift 4.7+。

部署 KetaAgent 前, 需要针对 KetaAgent 的命名空间设置权限:

```
## 将 preivileged scc 赋予 serviceaccount，确保 ketad 拥有最高权限
## system:serviceaccount:{namespace}:{serviceaccount}
$ oc adm policy add-scc-to-user privileged system:serviceaccount:keta-agent:ketad

## 卸载时可以删除相应的 scc
$ oc adm policy remove-scc-from-user privileged system:serviceaccount:keta-agent:ketad
```

## Universal Agent 安装 
为确保广泛的兼容性，Universal版本适用于Linux 、Windows、MacOS X、Java8的系统中的较低版本、具体支持的版本信息可参考[OpenJDK1.8支持系统版本](https://www.java.com/zh-CN/download/help/sysreq.html)。

Universal Agent依赖：jdk1.8+

### 支持功能
* 控制：注册、心跳、采集任务管理
* 采集：日志(file)、指标(cpu/mem/diskio/net)(仅限linux amd64系统)
* 发送：直接丢弃(discard)、本地文件(file)、KetaDB(keta)

### 特别说明
1.当前仅linux amd64机器可通过页面生成的安装命令一键安装，其他操作系统可通过手动安装的方式进行安装，具体步骤如下：
- AIX/MacOS

    1.确认已安装 java 环境（jdk>=1.8）
    ```
     java -version
    ```
    2.下载并解压 agent 安装包
    ```
     tar -xvf universal-agent.tar.gz
    ```    
    3.进入安装目录，修改配置
    ```
     cd universal-agent/
     vim config/config.yml
    ```
    配置示例如下：
    ```
    ---
    global:
        tags:
        - "universal"
        meta: "/usr/local/ketad/universal-agent/meta"
        status: "online"
        agent_id: "/usr/local/ketad/universal-agent/.agentid"
        biz_systems: []
    server:
        endpoints:
        - "10.68.213.64:9400"
        token: "collect_95634039-9bfb-41ed-ac7a-57e50291ece9"
        subnets: []
        region: "default"
        net_interface: ""
    config_path: "/usr/local/ketad/universal-agent/.ketaconfs"
    ```
    4.启动 universal-agent
    ```
     ./bin/universal-agent -d
    ```    
## 离线安装

当环境完全没有外网的情况下，只能通过移动硬盘（U 盘）等方式将安装包从公网下载到内网。

离线安装需要三个资源:

- KetaAgent 安装包
- KetaAgent 安装脚本
- KetaAgent 安装命令

目前离线安装支持以下操作系统:

- Linux
- MacOS
- AIX

### 获取资源

#### 获取 KetaAgent 安装包

通过主站-配置-数据管理-Agent采集-安装包页面导出需要的 KetaAgent 安装包.

#### 获取 KetaAgent 安装脚本

可以访问以下地址获取安装脚本:

- Linux 系统

  ```
  https://<ketadb>/api/v1/dc/install/script?os=linux
  ```

- MacOS 系统

  ```
  https://<ketadb>/api/v1/dc/install/script?os=darwin
  ```

- AIX 系统

  ```
  https://<ketadb>/api/v1/dc/install/script?os=aix
  ```

### 安装 KetaAgent

上述获取到的脚本名称为 `install.sh`, 通过以下命令进行安装:

```
KETAD_TOKEN='<KETA_TOKEN>' KETAD_ENDPOINTS='<KETA_ENDPOINTS>' KETAD_TAGS='<KETA_TAGS>' ./install.sh --mode 'offline' --pkg '<KETA_AGENT_PKG_PATH>'
```

KETA_TOKEN, KETA_ENDPOINTS, KETA_TAGS 可以通过在线安装的命令中获取,

KETA_AGENT_PKG_PATH 为 KetaAgent 的安装包存放路径, 不使用 `--pkg` 指定安装包时会默认使用当前路径下的 `./ketad.tar.gz` 安装包.