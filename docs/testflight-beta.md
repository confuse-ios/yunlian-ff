# TestFlight 外部 Beta 测试

TestFlight 是 Apple 官方提供的 Beta 测试分发渠道。云链分发支持自动化上传 IPA 到 TestFlight，并协助完成 Beta 审核与外部测试组分发，大幅缩短测试版本发布周期。

在线阅读：[TestFlight Beta](https://yunlian-ff.com/docs/testflight-beta) · 上架引导：[上架 TestFlight](https://yunlian-ff.com/newbie-guide-tf)

## 外部 Beta 测试流程

1. **准备构建**  
   在 Xcode 或 CI 中打包 IPA，确保使用 App Store 分发证书签名，Bundle ID 与 App Store Connect 中注册的一致。
2. **上传至 TestFlight**  
   通过「TestFlight 上传」功能或「新手上架 TestFlight」引导，选择 Apple 账号和应用，上传 IPA。平台任务节点自动完成 Transporter 上传流程。
3. **等待 Beta 审核**  
   Apple 对 TestFlight 构建进行 Beta App Review（通常 24–48 小时）。平台支持自动提交 Beta 审核，审核通过后可配置自动分发。
4. **配置外部测试组**  
   在 App Store Connect 中创建外部测试组，添加测试员邮箱。外部测试组最多 10,000 名测试员，无需收集 UDID。
5. **测试员安装**  
   测试员收到邮件邀请，在 iOS 设备上安装 TestFlight App，即可下载测试版本并提供反馈。

## 外部 Beta 能满足的需求

- **大规模测试覆盖**  
  最多 10,000 名外部测试员，无需注册设备 UDID，通过邮箱邀请即可参与测试。
- **官方崩溃与反馈**  
  TestFlight 内置崩溃报告和截图反馈功能，测试员可直接在 App 内提交问题，开发者可在 App Store Connect 查看。
- **版本迭代验证**  
  每个 App 最多保留 100 个 TestFlight 构建，支持多版本并行测试和 A/B 对比。
- **发布前最终验证**  
  在提交 App Store 正式审核前，通过外部 Beta 进行最后一轮真实用户验证，降低正式版拒审风险。
- **自动化 CI/CD 集成**  
  配合平台 API Token，可将 TestFlight 上传集成到 Jenkins、GitHub Actions 等 CI 流水线，实现构建即分发。
- **合规的公开测试**  
  相比企业签分发，TestFlight 是 Apple 官方认可的测试渠道，不存在证书吊销风险，适合需要面向较多测试用户的场景。

## 内部测试 vs 外部测试

**内部测试**：最多 100 名成员（需在 App Store Connect 用户权限中添加），无需 Beta 审核，上传后立即可用，适合团队内部快速验证。

**外部测试**：最多 10,000 名测试员（通过邮箱邀请），需要 Beta App Review，审核通过后测试员才能安装，适合面向真实用户的公开 Beta 测试。

分步操作见 [上架 TestFlight](testflight-guide.md)。

---

上一篇：[内测应用分发](internal-distribution.md) · 下一篇：[重签名功能](resign.md)
