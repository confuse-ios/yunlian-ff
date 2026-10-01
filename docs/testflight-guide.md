# 上架 TestFlight 引导

「上架 TestFlight」是新手上架引导（TestFlight 版），以**分步向导**形式完成从环境配置、证书准备、IPA 上传到 TestFlight Beta 发布的全流程。适合需要将 App 快速推送给测试员、尚未准备正式提审的开发者。

在线阅读：[上架 TestFlight](https://yunlian-ff.com/docs/testflight-guide) · 进入引导：[yunlian-ff.com/newbie-guide-tf](https://yunlian-ff.com/newbie-guide-tf)

## 功能概述

TestFlight 是 Apple 官方 Beta 测试渠道。本引导在前 8 步完成基础设施搭建（节点、账号、证书、应用、IPA 上传），第 9 步专门提供 TestFlight 构建管理与 Beta 发布能力，无需离开平台即可完成测试版本分发。

- **TF 专属流程** — 最后一步聚焦 TestFlight 构建管理与 Beta 发布，而非 App Store 正式提审
- **构建同步** — 支持从 App Store Connect 同步构建列表，查看上传与发布状态
- **Beta 发布向导** — 配置公开链接或邮件邀请、Beta 描述、反馈邮箱、审核备注等信息
- **内外部测试** — 支持配置内部测试组（100 人）和外部测试组（10,000 人）分发
- **记录清单** — 与 App Store 引导相同，支持多条本地记录保存进度
- **构建管理跳转** — 可快速跳转至控制台「构建管理」进行高级操作

能力说明见 [TestFlight 外部 Beta 测试](testflight-beta.md)。

## 九步流程详解

| 步骤 | 名称 | 说明 |
| --- | --- | --- |
| 1 | 节点配置 | 申请公共节点授权或创建自控节点，为 TestFlight 上传任务提供执行环境 |
| 2 | IP 隔离策略 | 配置独立 IP 代理，确保访问 App Store Connect 时使用隔离出口 |
| 3 | 账号托管 | 添加 Apple 开发者账号，完成验号、绑定节点、配置 API Key |
| 4 | 证书生成 | 创建或上传 App Store Distribution 证书 |
| 5 | 开发设备 | 注册测试设备 UDID（内部测试需要，外部 Beta 可跳过） |
| 6 | 配置描述文件 | 创建 App Store 类型的 Provisioning Profile |
| 7 | 创建应用 | 在 App Store Connect 创建 App，同步 Bundle ID |
| 8 | 上传 IPA | 上传 IPA 至 TestFlight，平台任务节点自动完成 Transporter 上传 |
| 9 | 发布构建 | 管理 TestFlight 构建列表，提交 Beta 审核并发布到测试组 |

## 第 9 步：发布构建能力

TestFlight 引导的最后一步提供完整的构建管理面板，核心能力包括：

| 功能 | 说明 |
| --- | --- |
| 同步构建 | 从 Apple 拉取最新 TestFlight 构建，查看上传状态与版本信息 |
| 提交 Beta 审核 | 对未审核的构建提交 Beta App Review，等待 Apple 审核通过 |
| 发布到测试组 | 审核通过后，将构建分发到内部或外部测试组 |
| 公开链接 / 邮件邀请 | 外部测试支持生成公开链接或通过邮件邀请测试员 |
| Beta 元数据 | 填写 Beta 描述、反馈邮箱、审核备注、联系人信息等 |

## 记录清单功能

与 App Store 引导相同，左侧**记录清单**支持创建多条本地记录，分别保存不同 App 的 TestFlight 上架进度。记录数据存储在浏览器本地，切换记录即可恢复对应的步骤状态与配置数据。

## 使用前提

- **需要登录**  
  TestFlight 上架引导需要登录平台账号，未登录将跳转至登录页。
- **App Store 签名 IPA**  
  上传的 IPA 须使用 App Store Distribution 证书签名，Bundle ID 需与 App Store Connect 中创建的应用一致。
- **Beta 审核等待**  
  外部测试组分发需先通过 Apple Beta App Review（通常 24–48 小时），内部测试组无需审核。
- **IPA 上传配额**  
  第 8 步上传 IPA 消耗「IPA 上传次数」配额，请确保 VIP 套餐或加油包配额充足。详见 [VIP 与配额](vip.md)。

## 与「上架 App Store」引导的区别

两个引导前 8 步相同。TestFlight 引导第 9 步专注于**Beta 构建发布**（同步构建、提交 Beta 审核、配置测试组）；App Store 引导第 9 步为**正式提审**（通过浏览器代理访问 App Store Connect 提交审核）。若目标是先内测再上架，建议先走 TestFlight 引导，正式提审见 [上架 App Store](appstore-guide.md)。

开始引导：[进入 TestFlight 上架引导](https://yunlian-ff.com/newbie-guide-tf)

---

上一篇：[上架 App Store](appstore-guide.md) · 下一篇：[上架合规服务](compliance-service.md)
