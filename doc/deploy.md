# 部署

- [部署](#部署)
  - [手动部署 (推荐)](#手动部署-推荐)
    - [安装](#安装)
    - [启动](#启动)
  - [Huggingface 部署](#huggingface-部署)
    - [我承认你的代码写的确实很nb，但对我来说还是太吃操作了 (已过时)](#我承认你的代码写的确实很nb但对我来说还是太吃操作了-已过时)

## 手动部署 (推荐)

本方式理论上全平台通用, 安装了 Python >= **3.6** 即可 (建议: **3.10+**)

### 安装

1. Clone 本仓库 (建议先 Fork / Use this template)

```shell
git clone --depth=1 -b main https://github.com/wyf9/sleepy.git
```

2. 安装依赖

```shell
pip install -r requirements.txt
```

3. 编辑配置文件

在目录下新建 `.env` 文件 (参考 `.env.example` 填写), 也可以直接设置相应的环境变量

> [!IMPORTANT]
> **[配置示例](./.env.example)** <br/>
> **Windows 用户请确保 `.env` 文件以 UTF-8 编码而非 GBK 编码保存，否则读取可能出现问题!** *(如错误读入行尾注释)* <br/>
> *注意: 环境变量的优先级**高于** `.env` 文件* <br/>

### 启动

> **使用宝塔面板 (uwsgi) 等部署时，请确定只为本程序分配了 1 个进程, 如设置多个服务进程可能导致数据不同步!!!**

有两种启动方式:

```shell
# 直接启动
python3 server.py
# 简易启动器
python3 start.py
```
默认服务 http 端口: **`9010`**

## Huggingface 部署

> 适合没有服务器部署的同学使用

只需三步:

1. 复制 Space `wyf9/sleepy` ([点击直达](https://huggingface.co/spaces/wyf9/sleepy?duplicate=true&visibility=public))
2. 在复制页面设置 secret 和页面信息等环境变量
3. 点击部署，等待完成后点击右上角三点 -> `Embed this space`，即可获得你的部署地址 (类似 `https://wyf9-sleepy.hf.space`)

> [!IMPORTANT]
> **在创建时请务必选择 Space 类型为公开 (`Public`)，否则无法获取部署地址 (他人无法访问)!** <br/>
> *HUgging Face 部署如几天未访问将会休眠，建议使用定时请求平台 (如 `cron-job.org`, `Uptime Kuma` 等) 保活 Space*

### 我承认你的代码写的确实很nb，但对我来说还是太吃操作了 (已过时)

<details>

***<summary>点!此!展!开! (大图警告)</summary>***

有没有更简单无脑的方法推荐一下
**有的兄弟，有的！**
这样的方法有很多个，各个都是`GitHub` T<sub>0.5</sub>的操作
我怕教太多了你学不会，现在只要点
[这里](https://huggingface.co/spaces/sadg456/s?duplicate=true&visibility=public)  
然后自己去注册一个账号
参考`.env.example`在Setting==>Variables and secrets添加环境变量配置
然后在这里:
![链接](https://files.catbox.moe/svvdt6.png)
就可以复制你的`URL`，填入你选择的 **[`/client`](./client/README.md)** 对应的url配置中即可快速开始

</details>