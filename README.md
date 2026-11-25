# FolderShare

把 Mac 上的任意文件夹，一键变成一个 HTTPS 链接 + 二维码。免账号、免装 cloudflared、文件不离开本机。

**官网：<https://foldershare.top/?utm_source=github&utm_medium=readme>** · **English site: <https://foldershare.top/en/?utm_source=github&utm_medium=readme>** · **下载：见右侧 Releases** · macOS 13+（Apple Silicon / Intel）

![FolderShare](https://foldershare.top/assets/screenshots/running-light.png)

## 为什么是 FolderShare

微信不能直接发文件夹，网盘要上传、要对方登录、还会限速。FolderShare 的思路是：文件留在你的 Mac 上，只把「访问入口」通过 Cloudflare 快速隧道临时借出去。

- 拖入文件夹 → 点开始 → 得到 HTTPS 链接和二维码，对方浏览器直接打开
- 不需要 Cloudflare 账号，不需要 Homebrew，不需要终端
- 停止分享 / 到期 / 退出应用后链接立即失效
- 访问码、有效期、访客上传、ZIP 打包、视频 Range 播放、局域网直连、21 种语言
- 断线自动重连（指数退避）与运行中延长有效期
- 访客页手机端一键下载栏、上传失败重试、到期前 5 分钟提醒
- 最近分享/一键再次分享、首次启动 3 步引导
- 访客页中英双语（按浏览器语言自动切换）
- 固定入口链接（Pro）：每次分享复用同一个链接和二维码
- 固定域名（Pro）：自带 Cloudflare 账号和域名，得到长期固定地址

## 安装

1. 在 [Releases](../../releases) 下载 `FolderShare-1.11.0-universal.zip`
2. 解压，把 `FolderShare.app` 拖进 `应用程序`
3. **当前版本尚未通过 Apple 公证**：首次打开请右键点击 App →「打开」，或在「系统设置 → 隐私与安全性」点「仍要打开」
4. 如果提示需要 cloudflared：不需要，应用已内置

## Pro 与离线授权

Pro 使用离线授权码（`FS1...`），**不需要注册账号、不需要联网激活**：

- 在官网 <https://foldershare.top/#pricing> 申请开通 / 购买
- 打开 FolderShare →「升级 Pro」→ 粘贴授权码 → 激活
- 授权码由官网签名，仅在本机校验；不会上传文件、路径或设备信息

免费版包含除固定入口、固定域名之外的全部核心功能。

## 已知限制

- 应用未公证，首次启动需要手动放行；后续会补上 Apple Developer ID 签名
- Quick Tunnel 为 Cloudflare 的临时隧道：无 SLA、单隧道约 200 并发，且地址每次随机（Pro 固定入口用于解决地址随机问题）
- 部分公司/校园网或 VPN TUN 模式会拦截隧道端口 7844；应用会给出诊断提示，可切换网络或关闭 TUN 后重试
- 分享期间 Mac 需要保持开机

## 隐私

分享链路由访客直接连到你的 Mac，文件内容不经过 FolderShare 服务器。官网站点仅统计匿名页面访问与下载次数，不采集文件内容、路径或通讯录。详见 <https://foldershare.top/privacy.html>。

## 许可与第三方组件

- 本仓库仅发布编译后的应用，源码暂未公开。
- 应用内置 [cloudflared](https://github.com/cloudflare/cloudflared)（Apache License 2.0，未修改的二进制），许可文本随 App 一起分发。
- FolderShare 与 Cloudflare, Inc. 没有隶属或背书关系；Cloudflare 是 Cloudflare, Inc. 的商标。
