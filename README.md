# RyanWu080’s Scoop Bucket

[![Tests](https://github.com/RyanWu080/my-scoop-bucket/actions/workflows/ci.yml/badge.svg)](https://github.com/RyanWu080/my-scoop-bucket/actions/workflows/ci.yml)
[![Excavator](https://github.com/RyanWu080/my-scoop-bucket/actions/workflows/excavator.yml/badge.svg)](https://github.com/RyanWu080/my-scoop-bucket/actions/workflows/excavator.yml)

[中文](#中文) | [English](#english)

## 中文

个人 [Scoop](https://scoop.sh) 软件桶，提供 PCL CE 官方版、解除地区限制版、HWiNFO Beta、DLSS 5 Manager、QuickInput、Server Picker X 及 XboxDownload。

### 软件清单

| 包名 | 软件来源 | 更新渠道 | 架构 |
| --- | --- | --- | --- |
| `pcl-ce` | [PCL CE 官方版](https://github.com/PCL-Community/PCL-CE) | 正式版 | x64、ARM64 |
| `pcl-ce-beta` | [PCL CE 官方版](https://github.com/PCL-Community/PCL-CE) | 最新 release，含正式版和 beta | x64、ARM64 |
| `pcl-ce-unrestrict` | [解除地区限制版](https://github.com/RyanWu080/PCL-CE-unrestrict) | 正式版 | x64、ARM64 |
| `pcl-ce-unrestrict-beta` | [解除地区限制版](https://github.com/RyanWu080/PCL-CE-unrestrict) | 最新 release，含正式版和 beta | x64、ARM64 |
| `hwinfo-beta` | [HWiNFO](https://www.hwinfo.com) | Beta | x64、ARM64 |
| `dlss-5-manager` | [DLSS 5 Manager](https://github.com/NODIX-TECH/DLSS-5-MANAGER) | 正式版 | x64 |
| `quickinput` | [QuickInput](https://github.com/ChiyukiGana/Quickinput) | 正式版 | x64 |
| `server-picker-x` | [Server Picker X](https://github.com/FN-FAL113/server-picker-x) | 正式版 | x64 |
| `xboxdownload` | [XboxDownload](https://github.com/skydevil88/XboxDownload) | 正式版 | x64、ARM64 |

### 安装与更新

安装 Scoop 后，添加软件桶并选择上表中的包名。以下以 `pcl-ce-unrestrict-beta` 为例：

```powershell
scoop bucket add my-scoop-bucket https://github.com/RyanWu080/my-scoop-bucket
scoop install my-scoop-bucket/pcl-ce-unrestrict-beta

# 刷新清单并更新软件
scoop update
scoop update pcl-ce-unrestrict-beta
```

### 使用说明

- **XboxDownload**：Xbox、微软商店等游戏平台的下载助手，使用 x64 或 ARM64 便携包。运行 `scoop install my-scoop-bucket/xboxdownload` 安装，从开始菜单启动并允许管理员权限；配置保存在 `%LOCALAPPDATA%\XboxDownload`，使用 Scoop 更新软件。

- **Server Picker X**：CS2、Deadlock 等游戏的服务器选择工具，使用自带 .NET 运行时的 x64 便携包。运行 `scoop install my-scoop-bucket/server-picker-x` 安装，从开始菜单启动并允许管理员权限，以便管理防火墙规则；更新时保留设置和预设。

- **QuickInput**：键盘鼠标宏自动化工具，需要 Windows 10 1903 或更高版本。运行 `scoop install my-scoop-bucket/quickinput` 安装，通过 `quickinput` 命令或开始菜单启动；更新时保留配置、宏、语言、样式及 OCR 目录。OCR 模型请从[官方下载页面](https://chiyukigana.github.io/ChiyukiGana/pages/qinput/versions.html)下载。

- **DLSS 5 Manager**：使用自带 .NET 8 运行时的 x64 免安装包。运行 `scoop install my-scoop-bucket/dlss-5-manager` 安装，使用 `dlss-5-manager` 命令或开始菜单快捷方式启动；配置、缓存及备份保存在 `%LOCALAPPDATA%\DLSS5Manager`。

- **PCL CE**：需要 Microsoft .NET 10 Desktop Runtime，可通过以下命令安装：

  ```powershell
  scoop bucket add extras
  scoop install extras/windowsdesktop-runtime
  ```

- **更新渠道**：PCL CE 的 beta 包跟踪各自仓库最新发布的 release，正式版发布后也会跟进。建议关闭启动器自动下载更新，统一使用 Scoop 更新。
- **数据保存**：各 PCL CE 包使用独立命令和开始菜单快捷方式，并分别保留 `PCL`、`.minecraft` 目录；AppData 中的设置仍可能共享。
- **HWiNFO Beta**：x64、ARM64 使用官方更新接口公布的固定更新包地址。官网 ZIP 返回 403，会阻塞自动更新，因此此清单暂不提供 x86；如需 x86，请查看[官方下载页](https://www.hwinfo.com/download/)。

仓库每 4 小时检查更新，每次复核 HWiNFO Beta 版本，仅在版本更新后额外下载并校验 x64、ARM64 包的哈希。运行结果见 [Excavator](https://github.com/RyanWu080/my-scoop-bucket/actions/workflows/excavator.yml)；清单格式参考 [Scoop 文档](https://github.com/ScoopInstaller/Scoop/wiki/App-Manifests)。

## English

A personal [Scoop](https://scoop.sh) bucket for official PCL CE, a fork with regional restrictions removed, HWiNFO Beta, DLSS 5 Manager, QuickInput, Server Picker X, and XboxDownload.

### Packages

| Package | Source | Update channel | Architectures |
| --- | --- | --- | --- |
| `pcl-ce` | [Official PCL CE](https://github.com/PCL-Community/PCL-CE) | Stable | x64, ARM64 |
| `pcl-ce-beta` | [Official PCL CE](https://github.com/PCL-Community/PCL-CE) | Latest release, including stable and beta | x64, ARM64 |
| `pcl-ce-unrestrict` | [Fork with regional restrictions removed](https://github.com/RyanWu080/PCL-CE-unrestrict) | Stable | x64, ARM64 |
| `pcl-ce-unrestrict-beta` | [Fork with regional restrictions removed](https://github.com/RyanWu080/PCL-CE-unrestrict) | Latest release, including stable and beta | x64, ARM64 |
| `hwinfo-beta` | [HWiNFO](https://www.hwinfo.com) | Beta | x64, ARM64 |
| `dlss-5-manager` | [DLSS 5 Manager](https://github.com/NODIX-TECH/DLSS-5-MANAGER) | Stable | x64 |
| `quickinput` | [QuickInput](https://github.com/ChiyukiGana/Quickinput) | Stable | x64 |
| `server-picker-x` | [Server Picker X](https://github.com/FN-FAL113/server-picker-x) | Stable | x64 |
| `xboxdownload` | [XboxDownload](https://github.com/skydevil88/XboxDownload) | Stable | x64, ARM64 |

### Installation and updates

After installing Scoop, add this bucket and choose a package from the table. This example uses `pcl-ce-unrestrict-beta`:

```powershell
scoop bucket add my-scoop-bucket https://github.com/RyanWu080/my-scoop-bucket
scoop install my-scoop-bucket/pcl-ce-unrestrict-beta

# Refresh manifests and update the package
scoop update
scoop update pcl-ce-unrestrict-beta
```

### Notes

- **XboxDownload**: Download assistant for Xbox, Microsoft Store and other gaming platforms, using the x64 or ARM64 portable archive. Install with `scoop install my-scoop-bucket/xboxdownload`, then launch from the Start Menu and allow administrator privileges. Settings are stored in `%LOCALAPPDATA%\XboxDownload`; use Scoop to update the application.

- **Server Picker X**: Server picker for CS2, Deadlock and other Steam Datagram Relay games. Uses the self-contained x64 portable archive. Install with `scoop install my-scoop-bucket/server-picker-x`, then launch from the Start Menu and allow administrator privileges to manage firewall rules. Settings and presets persist across updates.

- **QuickInput**: Keyboard and mouse macro automation tool requiring Windows 10 1903 or later. Install with `scoop install my-scoop-bucket/quickinput` and launch via `quickinput` or the Start Menu. Configuration, macros, languages, styles, and the OCR directory persist across updates. Download OCR models from the [official download page](https://chiyukigana.github.io/ChiyukiGana/pages/qinput/versions.html).

- **DLSS 5 Manager**: Uses the portable x64 archive with the .NET 8 runtime included. Install with `scoop install my-scoop-bucket/dlss-5-manager` and launch via `dlss-5-manager` or the Start Menu shortcut. Settings, caches, and backups are stored in `%LOCALAPPDATA%\DLSS5Manager`.

- **PCL CE** requires Microsoft .NET 10 Desktop Runtime. Install it with:

  ```powershell
  scoop bucket add extras
  scoop install extras/windowsdesktop-runtime
  ```

- **Update channels**: PCL CE beta packages follow the most recently published release from their respective repositories, including stable releases. Disable automatic update downloads in the launcher and use Scoop for updates.
- **Data**: Each PCL CE package has a distinct command and Start Menu shortcut and preserves its own `PCL` and `.minecraft` directories. AppData settings may still be shared.
- **HWiNFO Beta**: x64 and ARM64 use fixed update archive URLs published in the official update feed. The official ZIP returns HTTP 403 and blocks automatic updates, so this manifest temporarily excludes x86; see the [official download page](https://www.hwinfo.com/download/) if you need x86.

Updates are checked every four hours, with HWiNFO Beta version verification on every run; additional x64/ARM64 downloads and hash verification run only after a version update. See [Excavator](https://github.com/RyanWu080/my-scoop-bucket/actions/workflows/excavator.yml) for results and the [Scoop documentation](https://github.com/ScoopInstaller/Scoop/wiki/App-Manifests) for manifest guidelines.
