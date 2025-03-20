# Sleepy

实时在线状态监测 Flask 应用——清晰传达你的空闲状态，避免沟通误解

**[功能](#功能) | [演示](#演示) | [部署指南](#部署指南) | [客户端使用](#客户端) | [API文档](#API接口) | [致谢](#致谢)** 

---

## 功能亮点
✔️ **多状态自定义**  
预设「在线/离线」状态，支持[自定义状态标签](setting/README.md#status_listjson)

✔️ **设备动态感知**  
实时显示设备使用情况（活跃状态/当前运行应用）

✔️ **数据可视化**  
- 优雅的状态展示界面  
- 开放[指标查询接口](./doc/api.md)供数据分析

✔️ **多平台兼容**  
提供[客户端程序](./client/README.md)支持Windows/macOS/Linux

> 📢 开发动态：[Discord](https://discord.gg/DyBY6gwkeg)｜[Telegram](https://t.me/wyf9_sleepy)｜[问题反馈](https://github.com/wyf9/sleepy/issues)

---

## 演示站点
| 环境        | 地址                                                       | 状态监控                                                     |
| ----------- | ---------------------------------------------------------- | ------------------------------------------------------------ |
| 稳定版      | [sleepy.wyf9.top](https://sleepy.wyf9.top)                 | ![](E:/Notes/TyporaNotes/pictrue/status.svg+xml)             |
| 开发版      | [sleepy-preview.wyf9.top](https://sleepy-preview.wyf9.top) | [![Status](E:/Notes/TyporaNotes/pictrue/status-1742444568506-1.svg+xml)](https://uptime.wyf9.top) |
| HuggingFace | [wyf9-sleepy.hf.space](https://wyf9-sleepy.hf.space)       | [![Status](E:/Notes/TyporaNotes/pictrue/status-1742444568506-2.svg+xml)](https://uptime.wyf9.top) |

⚠️ 警告：禁止对演示站点进行JS注入等攻击行为

---

## 部署指南
▸ [完整部署教程](./doc/deploy.md)  
▸ [版本更新说明](./doc/update.md)  
▸ [性能优化建议](./doc/best_practice.md)

---

## 客户端
[客户端程序](./client/README.md) 支持：
- 手动更新在线状态
- 自动捕获应用使用记录
- 多平台支持（Windows/macOS/Linux）

---

## API接口
提供标准化的数据查询接口：
▸ [接口文档](./doc/api.md)  
▸ 自定义[统计白名单](./setting/README.md)

---

## 项目演进
[![Star History](E:/Notes/TyporaNotes/pictrue/sleepy&type=Date.svg+xml)](https://star-history.com/#wyf9/sleepy&Date)

---

## 致谢
灵感源于 B站UP主 [@WinMEMZ](https://space.bilibili.com/417031122) 的 [初始项目](https://maao.cc/sleepy/)  
前端界面借鉴 [steam-miniprofile](https://github.com/gamer2810/steam-miniprofile)  
特别推荐 WinMEMZ 的 [智能家居版](https://github.com/maoawa/project-sleepy)

📺 感谢 [@1812z](https://github.com/1812z) 的 [推广视频](https://www.bilibili.com/video/BV1LjB9YjEi3)