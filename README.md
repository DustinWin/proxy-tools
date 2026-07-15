# 更新 [mihomo 内核](https://github.com/MetaCubeX/mihomo)、[sing-box 内核](https://github.com/SagerNet/sing-box)、[sing-box reF1nd 版内核](https://github.com/reF1nd/sing-box)、Dashboard 面板和 [AdGuard Home](https://github.com/AdguardTeam/AdGuardHome)
# 一、 说明
每天凌晨（北京时间 UTC+8）自动构建生成：
1. mihomo [Meta 版](https://github.com/MetaCubeX/mihomo/tree/Meta)和 [Alpha 版](https://github.com/MetaCubeX/mihomo/tree/Alpha)内核
2. [reF1nd-Stable 版](https://github.com/reF1nd/sing-box/tree/reF1nd-stable)和 [reF1nd-Testing 版](https://github.com/reF1nd/sing-box/tree/reF1nd-testing)内核和 Android 安装包（支持[提供者](https://sing-boxr.dustinwin.cc.cd/zh/configuration/provider/) `providers`，类似于 mihomo 内核的[代理集合](https://wiki.metacubex.one/config/proxy-providers/) `proxy-providers`）
3. sing-box [Stable 版](https://github.com/SagerNet/sing-box/tree/stable)和 [Testing 版](https://github.com/SagerNet/sing-box/tree/testing)内核
4. Dashboard 面板：[Yacd-meta](https://github.com/MetaCubeX/Yacd-meta)、[metacubexd](https://github.com/MetaCubeX/metacubexd)、[zashboard](https://github.com/Zephyruso/zashboard) 和 [sing-box dashboard](https://github.com/SagerNet/sing-box-dashboard)
5. AdGuard Home [Release 版](https://github.com/AdguardTeam/AdGuardHome/tree/beta-v0.107)和 [Beta 版](https://github.com/AdguardTeam/AdGuardHome/tree/beta-v0.108)

**注：**
- 1. 本教程中的下载链接以 CPU 架构 ARM64 为例，请注意修改链接后缀
- 2. 查看 CPU 架构可连接 SSH 后执行命令 `uname -ms`，若执行结果是“linux aarch64”，就是搭载的 ARM64 架构
- 3. 本项目中 mihomo 内核和 sing-box 内核 Linux 端已精简 `gvisor` 和 `tailscale`
- 4. 本项目中 mihomo 内核、sing-box 内核和 AdGuard Home 的 Linux 端均采用 [UPX](https://github.com/upx/upx) 压缩方式
- 5. 对下载源的说明，可[点此](https://proxy-tutorials.dustinwin.cc.cd/about/#%E5%AF%B9%E4%B8%8B%E8%BD%BD%E6%BA%90%E7%9A%84%E8%AF%B4%E6%98%8E)了解

# 二、 使用方法
## 1. 导入内核（以 [ShellCrash](https://github.com/juewuy/ShellCrash) 导入内核为例）
<details>
<summary>① 首次导入</summary>

连接 SSH 后执行如下命令：
```shell
# mihomo 内核 Meta 版
curl -sS -o /tmp/CrashCore.upx -L https://ghfast.top/https://github.com/DustinWin/proxy-tools/releases/download/mihomo/mihomo-meta-linux-arm64.upx && sc
# mihomo 内核 Alpha 版
curl -sS -o /tmp/CrashCore.upx -L https://ghfast.top/https://github.com/DustinWin/proxy-tools/releases/download/mihomo/mihomo-alpha-linux-arm64.upx && sc
# sing-box 内核 reF1nd-Stable 版
curl -sS -o /tmp/CrashCore.upx -L https://ghfast.top/https://github.com/DustinWin/proxy-tools/releases/download/sing-box/sing-box-ref1nd-stable-linux-arm64.upx && sc
# sing-box 内核 reF1nd-Testing 版
curl -sS -o /tmp/CrashCore.upx -L https://ghfast.top/https://github.com/DustinWin/proxy-tools/releases/download/sing-box/sing-box-ref1nd-testing-linux-arm64.upx && sc
# sing-box 内核 Stable 版
curl -sS -o /tmp/CrashCore.upx -L https://ghfast.top/https://github.com/DustinWin/proxy-tools/releases/download/sing-box/sing-box-stable-linux-arm64.upx && sc
# sing-box 内核 Testing 版
curl -sS -o /tmp/CrashCore.upx -L https://ghfast.top/https://github.com/DustinWin/proxy-tools/releases/download/sing-box/sing-box-testing-linux-arm64.upx && sc
```
此时脚本会自动“发现可用的内核文件”，选择 1 加载，后选择对应的内核  
</details>
<details>
<summary>② 升级导入（ShellCrash → 9 更新/卸载 → 2 切换内核文件，内核版本不会刷新）</summary>

连接 SSH 后执行如下命令：
```shell
# mihomo 内核 Meta 版
curl -sS -o $CRASHDIR/CrashCore.upx -L https://ghfast.top/https://github.com/DustinWin/proxy-tools/releases/download/mihomo/mihomo-meta-linux-arm64.upx && $CRASHDIR/start.sh restart
# mihomo 内核 Alpha 版
curl -sS -o $CRASHDIR/CrashCore.upx -L https://ghfast.top/https://github.com/DustinWin/proxy-tools/releases/download/mihomo/mihomo-alpha-linux-arm64.upx && $CRASHDIR/start.sh restart
# sing-box 内核 reF1nd-Stable 版
curl -sS -o $CRASHDIR/CrashCore.upx -L https://ghfast.top/https://github.com/DustinWin/proxy-tools/releases/download/sing-box/sing-box-ref1nd-stable-linux-arm64.upx && $CRASHDIR/start.sh restart
# sing-box 内核 reF1nd-Testing 版
curl -sS -o $CRASHDIR/CrashCore.upx -L https://ghfast.top/https://github.com/DustinWin/proxy-tools/releases/download/sing-box/sing-box-ref1nd-testing-linux-arm64.upx && $CRASHDIR/start.sh restart
# sing-box 内核 Stable 版
curl -sS -o $CRASHDIR/CrashCore.upx -L https://ghfast.top/https://github.com/DustinWin/proxy-tools/releases/download/sing-box/sing-box-stable-linux-arm64.upx && $CRASHDIR/start.sh restart
# sing-box 内核 Testing 版
curl -sS -o $CRASHDIR/CrashCore.upx -L https://ghfast.top/https://github.com/DustinWin/proxy-tools/releases/download/sing-box/sing-box-testing-linux-arm64.upx && $CRASHDIR/start.sh restart
```
</details>

## 2. 安装 Dashboard 面板
**Dashboard 面板对应文件名和网址关系如下表：**
|面板名称|文件名|网址|
|-----|-----|-----|
|Yacd-meta|`Yacd-meta.tar.gz`|<https://yacd.metacubex.one>|
|metacubexd|`metacubexd.tar.gz`|<https://metacubex.github.io/metacubexd/>|
|zashboard|`zashboard.tar.gz`|<https://board.zash.run.place>|
|sing-box dashboard|`sing-box-dashboard.tar.gz`|<https://sing-box-dashboard.sagernet.org>|

连接 SSH 后执行如下命令：
```shell
# Yacd-meta
curl -sS -L https://ghfast.top/https://github.com/DustinWin/proxy-tools/releases/download/Dashboard/Yacd-meta.tar.gz | tar -zx -C $CRASHDIR/ui/ && $CRASHDIR/start.sh restart
# metacubexd
curl -sS -L https://ghfast.top/https://github.com/DustinWin/proxy-tools/releases/download/Dashboard/metacubexd.tar.gz | tar -zx -C $CRASHDIR/ui/ && $CRASHDIR/start.sh restart
# zashboard
curl -sS -L https://ghfast.top/https://github.com/DustinWin/proxy-tools/releases/download/Dashboard/zashboard.tar.gz | tar -zx -C $CRASHDIR/ui/ && $CRASHDIR/start.sh restart
# sing-box dashboard
curl -sS -L https://ghfast.top/https://github.com/DustinWin/proxy-tools/releases/download/Dashboard/sing-box-dashboard.tar.gz | tar -zx -C $CRASHDIR/ui/ && $CRASHDIR/start.sh restart
```
- 注：若使用基于 [Chromium 项目](https://www.chromium.org/Home/)开发的浏览器无法访问在线 Dashboard 面板时，以 [Chrome 浏览器](https://www.google.com/chrome/)为例，需要设置该网址域名“允许显示不安全内容”。方法如下：  
进入设置 → 隐私和安全 → 网站设置 → 更多内容设置 → 不安全内容（或者地址栏直接打开 chrome://settings/content/insecureContent 进行设置），在“允许显示不安全内容”内添加网址域名如：`board.zash.run.place`

## 3. 安装 AdGuard Home
<details>
<summary>① 安装 AdGuard Home</summary>

连接 SSH 后执行如下命令：
```shell
mkdir -p /data/AdGuardHome
# AdGuard Home Release 版
curl -sS -o /data/AdGuardHome/AdGuardHome -L https://ghfast.top/https://github.com/DustinWin/proxy-tools/releases/download/AdGuardHome/AdGuardHome_release_linux_arm64
# AdGuard Home Beta 版
curl -sS -o /data/AdGuardHome/AdGuardHome -L https://ghfast.top/https://github.com/DustinWin/proxy-tools/releases/download/AdGuardHome/AdGuardHome_beta_linux_arm64
chmod +x /data/AdGuardHome/AdGuardHome
/data/AdGuardHome/AdGuardHome -s install
/data/AdGuardHome/AdGuardHome -s start
# 将所有发往 53 端口的流量重定向到本地的 5353 端口
iptables -t nat -A PREROUTING -p tcp --dport 53 -j REDIRECT --to-ports 5353
iptables -t nat -A PREROUTING -p udp --dport 53 -j REDIRECT --to-ports 5353
ip6tables -t nat -A PREROUTING -p tcp --dport 53 -j REDIRECT --to-ports 5353
ip6tables -t nat -A PREROUTING -p udp --dport 53 -j REDIRECT --to-ports 5353
# 添加开机启动
cat <<EOF >> /data/auto_ssh/auto_ssh.sh

sleep 10s
/data/AdGuardHome/AdGuardHome -s install
/data/AdGuardHome/AdGuardHome -s start
iptables -t nat -A PREROUTING -p tcp --dport 53 -j REDIRECT --to-ports 5353
iptables -t nat -A PREROUTING -p udp --dport 53 -j REDIRECT --to-ports 5353
ip6tables -t nat -A PREROUTING -p tcp --dport 53 -j REDIRECT --to-ports 5353
ip6tables -t nat -A PREROUTING -p udp --dport 53 -j REDIRECT --to-ports 5353
EOF
```
</details>
<details>
<summary>② 升级 AdGuard Home</summary>

连接 SSH 后执行如下命令：
```shell
# AdGuard Home Release 版
curl -sS -o /data/AdGuardHome/AdGuardHome -L https://ghfast.top/https://github.com/DustinWin/proxy-tools/releases/download/AdGuardHome/AdGuardHome_release_linux_arm64
# AdGuard Home Beta 版
curl -sS -o /data/AdGuardHome/AdGuardHome -L https://ghfast.top/https://github.com/DustinWin/proxy-tools/releases/download/AdGuardHome/AdGuardHome_beta_linux_arm64
/data/AdGuardHome/AdGuardHome -s restart
```
</details>

# 三、 扩展（以 ShellCrash 配置定时任务为例）
可在 ShellCrash 里添加定时更新 mihomo 内核、sing-box 内核、zashboard 和 AdGuard Home 的任务
1. 连接 SSH 后执行 `vi $CRASHDIR/configs/task/task.user`，按一下 Ins 键（Insert 键），粘贴如下内容：  
注：
- 1. 留意链接后缀是否与 CPU 架构匹配
- 2. 须重启 ShellCrash 和 AdGuard Home 服务后生效

```shell
201#curl -sS -o $CRASHDIR/CrashCore.upx -L https://ghfast.top/https://github.com/DustinWin/proxy-tools/releases/download/mihomo/mihomo-meta-linux-arm64.upx >/dev/null 2>&1#更新mihomo内核
202#curl -sS -o $CRASHDIR/CrashCore.upx -L https://ghfast.top/https://github.com/DustinWin/proxy-tools/releases/download/sing-box/sing-box-ref1nd-stable-linux-arm64.upx >/dev/null 2>&1#更新sing-boxr内核
203#curl -sS -o $CRASHDIR/CrashCore.upx -L https://ghfast.top/https://github.com/DustinWin/proxy-tools/releases/download/sing-box/sing-box-stable-linux-arm64.upx >/dev/null 2>&1#更新sing-box内核
204#curl -sS -L https://ghfast.top/https://github.com/DustinWin/proxy-tools/releases/download/Dashboard/zashboard.tar.gz | tar -zx -C $CRASHDIR/ui/ >/dev/null 2>&1#更新zashboard
205#curl -sS -o /data/AdGuardHome/AdGuardHome -L https://ghfast.top/https://github.com/DustinWin/proxy-tools/releases/download/AdGuardHome/AdGuardHome_beta_linux_arm64 >/dev/null 2>&1#更新AdGuardHome
```
2. 按一下 Esc 键（退出键），输入英文冒号 `:`，继续输入 `wq` 并回车
3. 执行 `sc`，进入 ShellCrash → 5 配置自动任务 → 1 添加自动任务，可以看到末尾就有添加的定时任务，输入对应的数字并回车后可设置执行条件

# 给作者加鸡腿
<img src="https://github.com/user-attachments/assets/e640fdf6-0990-421f-8ec6-2d263b533b89" alt="支付宝" width="30%" />
<img src="https://github.com/user-attachments/assets/470f501c-5a59-45d8-8e0f-6e034376f107" alt="微信" width="30%" />

# 机场推荐
[Bitz Net](https://red.bnaffred.com/#/register?code=HT0ALWZq)（仅次于一线机场，推荐打折时购买）  
