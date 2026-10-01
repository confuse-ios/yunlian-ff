# 平台介绍

云链分发是一站式 iOS 应用分发与上架平台，面向独立开发者、中小团队及企业客户，提供从账号托管、证书管理、TestFlight 自动化、内测分发到 App Store 上架辅助的全链路能力。

在线阅读：[平台介绍](https://yunlian-ff.com/docs/platform) · 使用平台：[云链分发](https://yunlian-ff.com)

## 核心能力

- Apple 开发者账号托管与多账号管理
- 证书 / 描述文件全生命周期管理
- TestFlight 自动化上传与外部 Beta 分发
- 内测应用快速分发（链接 + 二维码）
- IPA 重签名与企业签分发
- IPA 相似度分析（4.3 风险评估）
- IP 隔离策略，降低账号关联风险
- App Store Connect 代理访问与构建上传

## 适用人群

- 需要频繁发布 TestFlight 版本的 iOS 开发者
- 运营多个 Apple 开发者账号的团队
- 需要快速内测分发、绕过 TestFlight 审核的场景
- 面临 App Store 审核拒审、需要合规上架的 App
- 使用企业证书或 Ad-Hoc 证书进行内部分发

## 分布式技术架构

平台采用**控制面 + 任务节点**的分布式架构。控制面（Web 控制台）负责账号管理、任务调度、权限控制与资源配额；任务节点（Task Node）负责执行实际的 IPA 解析、签名、上传等重计算操作，部署在独立的服务器或用户自建的自控节点上。

```text
Web 控制台 → 任务调度层 → 任务节点 → Apple 服务
任务创建      负载均衡      IPA 解析     App Store Connect
状态监控      节点路由      签名         TestFlight
配额管理      失败重试      上传 Apple
```

## 任务节点

平台采用控制面 + 任务节点的分布式架构，节点负责 IPA 处理、Apple 账号交互等重计算任务。支持公共节点与自控节点两种模式，详见 [任务节点](task-nodes.md)。

## IP 隔离中转

每个 Apple 账号可绑定独立的 IP 隔离策略（住宅 IP / 固定 IP 代理），确保访问 App Store Connect 时使用独立出口 IP，避免多账号关联。详见 [账号关联隔离](account-isolation.md)。

---

上一篇：[文档首页](README.md) · 下一篇：[任务节点](task-nodes.md)
