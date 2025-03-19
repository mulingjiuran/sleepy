# sleepy

一个用于 ~~*视奸*~~ 查看个人在线状态 (以及正在使用软件) 的 Flask 应用，让他人能知道你不在而不是故意吊他/她

[**功能**](#功能) / [**TODO**](#todo) / [演示](#preview) / [**部署**](#部署) / [**使用**](#使用) / [**关于**](#关于)

## 功能

- 自行设置在线状态
- 实时更新设备打开应用 (名称)
- 美观的展示页面 [见 [Preview](#preview)]
- 开放的 Query / Metrics [接口](./doc/api.md), 方便统计

### 功能

- [x] 手动设置在线状态 *(活着 / 似了 等, 也可[自定义](./setting/README.md#status_listjson))*
- [x] 设备使用状态 *(包括 是否正在使用 / 打开的应用名)*
- [x] 网页使用 SSE *(Server Send Events)* 刷新状态
- [x] 网页使用 api 请求，并实现定时轮询刷新 *(备选方案)*
- [x] Windows 客户端 (Python)
- [x] Android 客户端 ([Autox.js](https://github.com/aiselp/AutoX))
- [x] [查看更多客户端 (如浏览器脚本等)](./client/README.md)
- [x] [Metrics API](./doc/api.md#metrics) (统计页面访问 / 接口调用次数)

> [!TIP]
> **最新开发进度/ TODOs 见: [Discord](https://discord.gg/DyBY6gwkeg)** / [Telegram](https://t.me/wyf9_sleepy) / [QQ](https://qm.qq.com/q/uItkv96Wn6)<br/>
> 如有 Bug / 建议, 可 [issue](https://github.com/wyf9/sleepy/issues/new) 或 [More contact](https://wyf9.top/#/contact) *(注明来意)*.

对智能家居 / Home Assistant 感兴趣的朋友，一定要看看 WinMEMZ 的 [sleepy 重生版](https://maao.cc/project-sleepy/): [maoawa/project-sleepy](https://github.com/maoawa/project-sleepy)!

### Preview

演示站 (*较*稳定): [sleepy.wyf9.top](https://sleepy.wyf9.top)

开发预览 (*不保证可用*): [sleepy-preview.wyf9.top](https://sleepy-preview.wyf9.top)

> 区别: 演示站为 wyf9 个人站点; 预览站允许测试 API，且直接运行开发版本 (**密钥 `wyf9test`**)

> [!WARNING]
> 不要拿演示站做坏事 (比如 js 注入，已由 DeepSeek 强力修复) ~~，没准哪天我会加访问日志~~

## 部署 / 更新

请移步 [部署教程](./doc/deploy.md) 或 [更新教程](./doc/update.md)

## Client

如果你想直接开始使用，可在 **[`/client`](./client/README.md)** 找到客户端 (用于**手动更新状态**/**自动更新设备打开应用**)

## API

详细的 API 文档见 [doc/api.md](./doc/api.md).

## 优化站点

见 [Best Practice](./doc/best_practice.md).

> [!TIP]
> 想自定义你的状态列表 / metrics 统计白名单? **[见 `setting` 目录](./setting/README.md)**

## Star History

[![Star History Chart](https://api.star-history.com/svg?repos=wyf9/sleepy&type=Date)](https://star-history.com/#wyf9/sleepy&Date)

## 关于

本项目灵感由 Bilibili UP [@WinMEMZ](https://space.bilibili.com/417031122) 而来: [site](https://maao.cc/sleepy/) / [blog](https://www.maodream.com/archives/192/), 并~~部分借鉴~~使用了前端代码, 在此十分感谢。

[`templates/steam.html`](./templates/steam.html) 来自项目 [gamer2810/steam-miniprofile](https://github.com/gamer2810/steam-miniprofile).

也欢迎参观 WinMEMZ *(GitHub: [maoawa](https://github.com/maoawa))* 的原版！[maoawa/sleepy](https://github.com/maoawa/sleepy)

感谢 [@1812z](https://github.com/1812z) 的 B 站视频推广~ ([BV1LjB9YjEi3](https://www.bilibili.com/video/BV1LjB9YjEi3))
