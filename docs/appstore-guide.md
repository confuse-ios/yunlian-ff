# 上架 App Store 引导

「上架 App Store」是新手上架引导功能，以**分步向导**形式串联账号托管、证书管理、应用创建、IPA 上传到提交 App Store 审核的全流程。适合首次上架或希望在一个页面内完成全部准备工作的开发者。

在线阅读：[上架 App Store](https://yunlian-ff.com/docs/appstore-guide) · 进入引导：[yunlian-ff.com/newbie-guide](https://yunlian-ff.com/newbie-guide)

## 功能概述

传统 App Store 上架需要在 Apple Developer 后台、App Store Connect、Xcode 等多个平台之间反复切换。本引导将平台核心能力整合为 9 个连续步骤，按顺序操作即可完成从环境配置到提交审核的全部流程。

- **分步引导** — 9 步可视化流程，按顺序完成上架所需的全部准备工作
- **进度追踪** — 右侧步骤面板实时显示当前进度，已完成步骤可自由回看
- **记录清单** — 支持创建多条本地记录，保存各 App 的上架进度，随时切换继续
- **一站式操作** — 节点、账号、证书、设备、描述文件、应用创建、上传均在同一页面完成
- **前置校验** — 步骤切换时自动检查节点绑定、验号状态、API Key 等必要条件
- **代理提审** — 最后一步集成 App Store 访问代理，通过隔离 IP 安全访问 App Store Connect

## 九步流程详解

| 步骤 | 名称 | 说明 |
| --- | --- | --- |
| 1 | 节点配置 | 申请公共节点授权或创建自控节点，为后续自动化任务提供执行环境 |
| 2 | IP 隔离策略 | 添加并配置 IP 代理策略，降低多账号关联风险（可选但推荐） |
| 3 | 账号托管 | 添加 Apple 开发者账号，完成验号、绑定节点与 IP 策略、配置 API Key |
| 4 | 证书生成 | 在平台创建或上传 Distribution 证书，用于 App Store 签名 |
| 5 | 开发设备 | 注册测试设备 UDID，管理开发者账号下的设备列表 |
| 6 | 配置描述文件 | 创建或上传 App Store 类型的 Provisioning Profile |
| 7 | 创建应用 | 在 App Store Connect 中创建 App 记录，同步 Bundle ID 与元数据 |
| 8 | 上传 IPA | 选择账号与应用，上传 App Store 分发证书签名的 IPA 构建包 |
| 9 | 提交审核 | 通过 App Store 访问代理扩展，在隔离 IP 环境下登录并完成提审操作 |

相关说明：[任务节点](task-nodes.md)、[账号关联隔离](account-isolation.md)、[获取设备 UDID](get-udid.md)。

## 记录清单功能

引导页左侧提供**记录清单**面板，可将不同 App 的上架进度保存为独立记录（存储在浏览器本地）。每个记录包含当前步骤、已配置的账号 / 证书 / 设备等数据快照，方便：

- 同时推进多个 App 的上架准备工作
- 中断后随时加载记录，从上次步骤继续
- 为每个记录添加名称和备注，便于区分管理

## 使用前提

- **需要登录**  
  上架引导功能需要登录平台账号后使用，未登录用户访问将跳转至登录页。
- **Apple 开发者账号**  
  需拥有有效的 Apple Developer Program 会员资格（$99/年），并已创建 App Store Connect 访问权限。
- **任务节点必须配置**  
  步骤 3 进入步骤 4 前，需确保已绑定任务节点（公共节点授权或自控节点），否则无法继续。
- **账号验号**  
  Apple 账号需完成验号（2FA 认证），确保平台可正常代操作 App Store Connect API。

## 与「上架 TestFlight」引导的区别

两个引导的前 8 步流程基本一致（节点 → 证书 → 上传）。App Store 引导的第 9 步为**提交 App Store 正式审核**，需通过浏览器代理访问 App Store Connect 完成提审；TestFlight 引导的第 9 步为**发布构建到 TestFlight**，管理 Beta 分发。请根据目标选择对应引导。

若目标是先内测再上架，建议先走 [上架 TestFlight](testflight-guide.md)。

开始引导：[进入 App Store 上架引导](https://yunlian-ff.com/newbie-guide)

---

上一篇：[获取设备 UDID](get-udid.md) · 下一篇：[上架 TestFlight](testflight-guide.md)
