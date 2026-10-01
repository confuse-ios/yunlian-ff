# 获取设备 UDID

UDID（Unique Device Identifier）是 iOS 设备的唯一标识符。开发者需将测试设备的 UDID 注册到 Apple 开发者账号，才能通过 Ad-Hoc 描述文件安装内测包。云链分发提供**免安装 App、免连接电脑**的 UDID 获取方式，测试员在 iPhone / iPad 上即可完成。

在线阅读：[获取设备 UDID](https://yunlian-ff.com/docs/get-udid) · 打开获取页：[yunlian-ff.com/udid](https://yunlian-ff.com/udid)

## 什么是 UDID

UDID 是 Apple 为每台 iOS 设备分配的唯一 40 位十六进制字符串（部分旧设备为 24 位格式）。它与设备硬件绑定，不会因 App 卸载或系统升级而改变。Apple 不允许 App 或普通网页直接读取 UDID，因此需要通过**描述文件（.mobileconfig）**这一 Apple 官方支持的 Profile Service 流程来获取。

## 使用场景

| 场景 | 说明 |
| --- | --- |
| Ad-Hoc 内测分发 | Ad-Hoc 证书签名的 IPA 仅能在描述文件中已注册 UDID 的设备上安装，需提前收集测试员设备 UDID |
| 开发者后台注册设备 | 在 Apple Developer → Devices 中添加测试设备，每个账号每年有 100 台设备注册额度 |
| Provisioning Profile 更新 | 新增测试设备后，需重新生成包含新 UDID 的描述文件，并重新签名 IPA |
| 企业签分发（可选） | Enterprise 证书分发通常无需 UDID，但 Ad-Hoc 和部分内测场景仍需要 |

## 获取流程

1. **在真机 Safari 打开获取页**  
   测试员需使用 iPhone 或 iPad 的 **Safari 浏览器**打开 [UDID 获取页面](https://yunlian-ff.com/udid)。请勿在电脑浏览器或微信内置浏览器中操作。
2. **下载描述文件**  
   点击「下载描述文件」，系统会下载名为 `Get-UDID.mobileconfig` 的配置描述文件。
3. **安装描述文件**  
   打开「设置 → 通用 → VPN 与设备管理」，找到「获取设备 UDID」描述文件，连续点击「安装」并完成确认（可能需输入锁屏密码）。
4. **自动返回并展示 UDID**  
   安装完成后，系统会自动跳转回 Safari 页面并展示该设备的 UDID 字符串。
5. **复制并提供给开发者**  
   测试员点击「复制 UDID」，将字符串发送给开发者。开发者在 Apple Developer 后台注册该设备，并更新描述文件后重新签名 IPA。

## 两种打开方式

### 扫码打开（推荐）

- 在电脑端打开 UDID 获取页，页面会显示二维码
- 测试员用 iPhone / iPad 相机或 Safari 扫描二维码
- 直接在真机上打开获取页面，无需手动输入网址

### 直接分享链接

- 将 UDID 获取页链接（[https://yunlian-ff.com/udid](https://yunlian-ff.com/udid)）通过 IM、邮件等方式发给测试员
- 测试员在 Safari 中点击链接打开
- 适合远程收集、批量测试场景

## 开发者侧操作

收到测试员的 UDID 后，在云链分发平台或 Apple Developer 后台完成以下步骤：

1. **注册测试设备**  
   在 Apple Developer → Certificates, Identifiers & Profiles → Devices 中添加新设备，粘贴 UDID。
2. **更新描述文件**  
   在「证书托管」中重新生成或更新 Ad-Hoc 类型的 Provisioning Profile，确保包含新设备 UDID。
3. **重新签名 IPA**  
   使用更新后的描述文件对 IPA 重签名，或通过 Xcode 重新 Archive 导出。见 [重签名功能](resign.md)。
4. **分发安装**  
   通过 [内测应用分发](internal-distribution.md) 或 Ad-Hoc 方式将新 IPA 发给测试员安装。

## 注意事项

- **必须使用 Safari**  
  微信、QQ、Chrome 等 App 内置浏览器无法正常完成描述文件安装流程，请提醒测试员复制链接到 Safari 打开，或使用扫码方式。
- **网络地址可达**  
  测试员手机必须能访问 UDID 获取页的域名。本地开发时请勿分享 localhost 链接，局域网测试请使用电脑的局域网 IP 地址。
- **无需重复获取**  
  同一设备 UDID 固定不变。获取成功后浏览器会记住结果，再次打开页面无需重新安装描述文件。换设备或清除网站数据后需重新获取。
- **设备注册额度**  
  Apple 开发者账号每年可注册 100 台测试设备（Membership 年度重置）。请合理规划测试设备数量，移除不再使用的旧设备以释放额度。
- **隐私与安全**  
  描述文件仅用于读取 UDID 等设备标识信息，不会安装任何 App 或修改系统设置。安装完成后可在「VPN 与设备管理」中移除该描述文件。
- **与 TestFlight 的区别**  
  TestFlight 外部测试通过邮箱邀请，无需收集 UDID。仅 Ad-Hoc 内测分发和企业签部分场景需要 UDID，请根据分发方式选择是否需要收集。

## 获取失败？

- 确认使用的是 iPhone / iPad 原生 Safari 浏览器
- 确认已在「设置 → 通用 → VPN 与设备管理」中完成描述文件安装
- 确认手机网络能正常访问本站域名（非 localhost）
- 若页面提示「未能获取到设备 UDID」，点击「重新获取」后重试安装流程

获取页公开可用，无需登录。流程基于 Apple 官方 Profile Service，支持二维码分享，方便批量收集测试设备。

打开获取页：[https://yunlian-ff.com/udid](https://yunlian-ff.com/udid)

---

上一篇：[IPA 相似度分析](ipa-similarity.md) · 下一篇：[上架 App Store](appstore-guide.md)
