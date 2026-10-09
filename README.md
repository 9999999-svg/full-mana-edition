# 无敌版 · 满蓝修改版

免费提供 Windows 独立 EXE 和 SWF，并公开满蓝修改的源码。最大蓝量为 **9,999,999**，每次蓝量变动后恢复到满值。两个玩家角色共用该修改。

## 下载

到 [Releases](https://github.com/9999999-svg/full-mana-edition/releases) 下载 `FullMana.exe`，双击运行；不需要安装系统 Flash 插件。`FullMana.swf` 适用于已有兼容播放器的用户。

此项目不是 Python 游戏，普通玩家无需 Python。EXE 保留用户提供的独立 Flash 播放器，未签名。仅使用本项目提供的固定游戏版本。

## 修改源码与复现

`patch_mana.py` 是独立的修改源码，只使用 Python 标准库，没有 pip 依赖。修改原 SWF 的两个字节码表达式，仅改变 16 个字节，不修改游戏资源或 SWF 长度。

蓝量上限：`50 + 等级 * 10` 改为 `9999 * 1000 + 999`。

蓝量变化：`当前蓝量 + 增减量` 改为 `最大蓝量`。

可以从发行版恢复对应的原 SWF，再复现满蓝 SWF 和 EXE：

```powershell
python patch_mana.py FullMana.swf original.swf --restore
python patch_mana.py original.swf reproduced.swf --projector FullMana.exe --exe-output reproduced.exe
```

每次写入前校验输入 SHA-256 和修改位置，拒绝其他游戏版本和已有输出路径；写入前校验输出 SHA-256。复现 EXE 时复用下载 EXE 内的播放器，不另装播放器或浏览器插件。

原始 AI 修改脚本和分析结果在用户本地项目中；此处整理为不依赖本机 XML、解压路径和工具目录的可复现版本。验证范围见 [VALIDATION.md](VALIDATION.md)。

## 许可

满蓝修改源码采用 MIT 许可。原游戏及资源、EXE 内的 Flash 播放器是独立组成部分，**不因本仓库的 MIT LICENSE 而变成 MIT 软件**。本仓库未提供原始游戏创作工程；它公开的是本次修改源码，不宣称完整游戏和播放器均开源。发布者已确认这些用户提供文件的发布权。见 [NOTICE.md](NOTICE.md)。

## 自愿赞助

下载、使用和修改源码均免费，赞助完全自愿。

<img src="assets/donate-wechat.png" alt="自愿微信赞助二维码" width="280">
