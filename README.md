# 穷玩组屏幕测试工具箱（PoorPlayersScreenTestLab）

iOS / iPadOS 屏幕测试工具箱，移植自安卓应用「穷玩组屏幕测试工具箱」，**已获得原作者 PoorPlayers 穷玩组授权**。

适配 iPhone 与 iPad（原生 universal），声明 `UIRequiresFullScreen`，iPad 上进入全屏测试时状态栏与 Home 指示条可完整隐藏。支持 ProMotion 120Hz 锁频。

## 功能

| 工具 | 说明 |
| --- | --- |
| **画面信号接收器** | 监听 TCP 20002 端口，实时接收 CalMAN / ColourSpace 的 Resolve XML 指令显示测试图案；支持 SDR（sRGB / Display P3）/ EDR / HDR10（PQ + 元数据） |
| **拖影测试** | 三档灰度文字垂直滚动（灰阶组合可切换），CADisplayLink 锁定 60/90/120Hz，实测刷新率显示，检测拖影 / 残影 / 像素过冲 |
| **APL 测试** | 屏幕正中渲染与屏幕等比的白色矩形，占宽 1%~100% 可调，测量屏幕有效显示区域；可导出 SDR PNG 与 HDR（Gain Map）HEIC |
| **均匀度测试** | 全屏铺满单一灰阶（0~255），检查背光不均、漏光、暗角与亮度衰减 |
| **次像素渲染测试** | 严格按物理像素绘制的线组 / 米字星 / 5×7 像素字「PPS DASHI」，检查次像素排列与渲染锐利度，支持 1×~8× 最近邻放大 |
| **RGB 测试** | 广色域对比（左 P3 右 sRGB）/ HDR RGB 增益条（左 4×、右 1×/2×/3×）/ 极低灰阶截断（W/R/G/B 0→30），可导出 P3 PNG、HEIC + Gain Map |
| **FPS Flicker** | 锁定目标刷新率（24~120Hz）持续刷新纯色画面，观察闪烁；支持多档刷新率按设定间隔自动轮换，观察切换瞬间的 flicker |

## 系统要求

- iOS / iPadOS 16.0+
- HDR / EDR / 广色域相关功能需要支持对应能力的屏幕（iPhone X 之后 / 2018 年后的 iPad Pro 等）
- ProMotion 锁频（120Hz）需要 120Hz 设备；已在 Info.plist 声明 `CADisableMinimumFrameDurationOnPhone`

## 构建方法

1. Xcode 15+ 打开 `PoorPlayersScreenTestLab.xcodeproj`
2. 在 Signing & Capabilities 里选择你自己的 Team（免费个人 Apple ID 即可）
3. Run 到真机

> 免费个人团队签名的 App 有效期 7 天，到期需重新安装。

## 安装未签名 IPA（不走 Xcode）

GitHub Releases 提供**未签名**的 `.ipa`（无任何证书 / 描述文件）。你可以自行签名后安装：

- [AltStore](https://altstore.io/) / [SideStore](https://sidestore.io/)
- [Sideloadly](https://sideloadly.io/)（配合 Apple ID 签名）
- [TrollStore](https://github.com/opa334/TrollStore)（如设备支持）
- 或解包后用任意开发者证书重签

也可以直接克隆仓库用 Xcode 构建安装。

## 授权与致谢

- 原作：安卓「穷玩组屏幕测试工具箱」，作者 **PoorPlayers 穷玩组**，本项目的功能、图案协议与阈值均按原作复刻并获其授权
  - 微博：<https://weibo.com/u/7369143916>
  - B站：<https://b23.tv/J7HSKeG>
- iOS 移植：**A宝（知乎：昂首阔步）**
  - 知乎：<https://www.zhihu.com/people/ang-shou-kuo-bu-24>
  - 小红书：<https://xhslink.cn/m/5EslDdKZoXd>
  - 微博：<https://weibo.com/7516633331>
  - 抖音：<https://v.douyin.com/XTEdVMxd7JM/>
  - B站：<https://b23.tv/entru4E>
  - 酷安：<http://www.coolapk.com/u/3987328>
  - 什么值得买：<https://zhiyou.m.smzdm.com/member/4935269722>

本工具仅用于屏幕显示质量调试与研究，请勿用于商业用途；转载请注明原作者与移植作者。
