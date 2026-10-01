# 重签名功能

重签名功能允许你使用已有的证书和描述文件，对 IPA 包重新签名，更换 Bundle ID、应用名称或签名身份，适用于证书轮换、多证书分发、企业签分发等场景。

在线阅读：[重签名功能](https://yunlian-ff.com/docs/resign) · 使用平台：[云链分发](https://yunlian-ff.com)

## 能做什么

### 证书轮换

- 旧证书即将过期时，使用新证书对已有 IPA 重新签名
- 无需重新编译源码，节省打包时间
- 支持批量处理多个 IPA 包

### 多证书分发

- 同一份 IPA 使用不同证书签名，生成多个分发版本
- 适配不同客户或不同分发渠道
- 支持 Ad-Hoc、Enterprise 等多种证书类型

### Bundle ID 修改

- 更换 IPA 的 Bundle Identifier
- 修改应用显示名称和图标（需配置）
- 用于分身小包分发或版本差异化

### 企业签分发

- 使用 Enterprise 证书签名，生成免 UDID 限制的安装包
- 配合 [内测应用分发](internal-distribution.md)，快速生成下载链接
- 适合企业内部大规模部署

## 使用前必读

- 重签名前请确保已在「证书托管」中上传或创建所需的**证书（.p12）**和**描述文件（.mobileprovision）**。
- Ad-Hoc 重签名需确保目标设备的 UDID 已包含在描述文件中，否则安装会失败。收集方式见 [获取设备 UDID](get-udid.md)。
- 修改 Bundle ID 后，应用将被 iOS 视为全新 App，无法覆盖安装原 Bundle ID 的版本。
- 重签名不会改变 App 的功能逻辑，如需修改代码需重新编译 IPA。
- 每次重签名任务消耗 1 次「重签名」配额，配额不足时可购买加油包。详见 [VIP 与配额](vip.md)。
- 企业证书重签名需遵守 Apple 企业开发者计划条款，不得用于公开分发。
- 重签名任务在任务节点上执行，请确保账号已绑定在线节点。详见 [任务节点](task-nodes.md)。

---

上一篇：[TestFlight Beta](testflight-beta.md) · 下一篇：[IPA 相似度分析](ipa-similarity.md)
