# RyanWu080’s Scoop Bucket

[![Tests](https://github.com/RyanWu080/my-scoop-bucket/actions/workflows/ci.yml/badge.svg)](https://github.com/RyanWu080/my-scoop-bucket/actions/workflows/ci.yml)
[![Excavator](https://github.com/RyanWu080/my-scoop-bucket/actions/workflows/excavator.yml/badge.svg)](https://github.com/RyanWu080/my-scoop-bucket/actions/workflows/excavator.yml)

[中文](#中文) | [English](#english)

## 中文

用于 [Scoop](https://scoop.sh) 的个人 Windows 软件桶，提供 PCL CE 官方版、解除地区限制版及 HWiNFO Beta 的安装与更新清单。

### 软件清单

| 包名 | 软件来源 | 更新渠道 | 支持架构 |
| --- | --- | --- | --- |
| `pcl-ce` | [PCL CE 官方版](https://github.com/PCL-Community/PCL-CE) | 仅正式版 | x64、ARM64 |
| `pcl-ce-beta` | [PCL CE 官方版](https://github.com/PCL-Community/PCL-CE) | 最新 release，包含正式版和 beta | x64、ARM64 |
| `pcl-ce-unrestrict` | [PCL CE 解除地区限制版](https://github.com/RyanWu080/PCL-CE-unrestrict) | 仅正式版 | x64、ARM64 |
| `pcl-ce-unrestrict-beta` | [PCL CE 解除地区限制版](https://github.com/RyanWu080/PCL-CE-unrestrict) | 最新 release，包含正式版和 beta | x64、ARM64 |
| `hwinfo-beta` | [HWiNFO](https://www.hwinfo.com) | Beta | x86、x64、ARM64 |

### 安装

先安装 Scoop，再添加此软件桶：

```powershell
scoop bucket add my-scoop-bucket https://github.com/RyanWu080/my-scoop-bucket
```

按需选择软件包安装：

```powershell
# PCL CE 官方正式版
scoop install my-scoop-bucket/pcl-ce

# PCL CE 官方最新 release，包含 beta
scoop install my-scoop-bucket/pcl-ce-beta

# PCL CE 解除地区限制版（正式版）
scoop install my-scoop-bucket/pcl-ce-unrestrict

# PCL CE 解除地区限制版最新 release，包含 beta
scoop install my-scoop-bucket/pcl-ce-unrestrict-beta

# HWiNFO Beta 硬件检测与监控工具
scoop install my-scoop-bucket/hwinfo-beta
```

### HWiNFO Beta 更新与下载状态

`hwinfo-beta` 配置为从 [HWiNFO 官方下载页](https://www.hwinfo.com/download/)检测 Beta 版本，并从官网下载 ZIP。

2026-10-27 实测：当前清单已更新为 `8.55-6110`，其官网 ZIP 下载成功、完整性检查通过，SHA-256 与 [dAppCDN 页面](https://dappcdn.com/download/utilities/hwinfo)公布的值一致。旧版 `8.55-6095` 下载地址已返回 HTTP 404。

**定时自动检测目前仍受阻。** GitHub 托管的 Windows runner 访问官网版本页和 dAppCDN 页面均返回 HTTP 403；更换浏览器 User-Agent 或使用 `curl` 也未解决 dAppCDN 的访问问题。因此暂时不能保证定时自动更新。若需持续跟随官网，需要使用已验证可访问这些页面的自托管 runner，或另行验证可用的版本源。

软件安装时的下载访问情况取决于实际网络环境。遇到问题请查看官方下载页和 [Excavator 运行日志](https://github.com/RyanWu080/my-scoop-bucket/actions/workflows/excavator.yml)。工作流显示成功不代表所有软件都成功检查了更新，仍需确认日志中的 `hwinfo-beta` 结果。

### PCL CE 使用说明

#### 运行环境

四个 PCL CE 软件包均需要 Microsoft .NET 10 Desktop Runtime。若尚未安装，可执行：

```powershell
scoop bucket add extras
scoop install extras/windowsdesktop-runtime
```

#### 更新渠道

`pcl-ce` 和 `pcl-ce-unrestrict` 仅跟踪各自仓库的正式版。

`pcl-ce-beta` 和 `pcl-ce-unrestrict-beta` 按发布时间跟踪各自仓库的最新 release，同时检查正式版和 beta，自动匹配 `Release` 或 `Beta` 可执行文件。正式版发布晚于 beta 时，会更新到正式版；后续发布新 beta 时，继续跟踪新 beta。

建议通过 Scoop 更新，并在启动器设置中关闭自动下载更新：

```powershell
scoop update
# 将包名替换为实际安装的版本
scoop update pcl-ce-unrestrict-beta
```

#### 命令与数据保存

四个 PCL CE 软件包使用不同的命令和开始菜单快捷方式，命令与包名一致。

各包的 `PCL` 和 `.minecraft` 目录会分别持久化，更新时保留。启动器存放在 AppData 中的设置仍可能在不同版本之间共享。

### 清单维护

仓库配置了 CI 检查，以及每 4 小时运行一次的 Excavator 自动更新工作流。清单中的 `checkver` 用于检测版本，`autoupdate` 用于生成新版下载地址。

新增或修改清单时，可参考 Scoop 的 [App Manifests 文档](https://github.com/ScoopInstaller/Scoop/wiki/App-Manifests)和[贡献指南](https://github.com/ScoopInstaller/.github/blob/main/.github/CONTRIBUTING.md)。

## English

A personal Windows software bucket for [Scoop](https://scoop.sh), providing installation and update manifests for official PCL CE, a fork with regional restrictions removed, and HWiNFO Beta.

### Packages

| Package | Source | Update channel | Architectures |
| --- | --- | --- | --- |
| `pcl-ce` | [Official PCL CE](https://github.com/PCL-Community/PCL-CE) | Stable releases only | x64, ARM64 |
| `pcl-ce-beta` | [Official PCL CE](https://github.com/PCL-Community/PCL-CE) | Latest release, including stable and beta | x64, ARM64 |
| `pcl-ce-unrestrict` | [PCL CE fork with regional restrictions removed](https://github.com/RyanWu080/PCL-CE-unrestrict) | Stable releases only | x64, ARM64 |
| `pcl-ce-unrestrict-beta` | [PCL CE fork with regional restrictions removed](https://github.com/RyanWu080/PCL-CE-unrestrict) | Latest release, including stable and beta | x64, ARM64 |
| `hwinfo-beta` | [HWiNFO](https://www.hwinfo.com) | Beta | x86, x64, ARM64 |

### Installation

Install Scoop first, then add this bucket:

```powershell
scoop bucket add my-scoop-bucket https://github.com/RyanWu080/my-scoop-bucket
```

Choose the packages you want to install:

```powershell
# Official PCL CE: stable releases
scoop install my-scoop-bucket/pcl-ce

# Official PCL CE: latest release, including betas
scoop install my-scoop-bucket/pcl-ce-beta

# PCL CE fork with regional restrictions removed: stable releases
scoop install my-scoop-bucket/pcl-ce-unrestrict

# PCL CE fork with regional restrictions removed: latest release, including betas
scoop install my-scoop-bucket/pcl-ce-unrestrict-beta

# HWiNFO Beta: hardware analysis and monitoring
scoop install my-scoop-bucket/hwinfo-beta
```

### HWiNFO Beta updates and downloads

`hwinfo-beta` is configured to detect Beta versions on the [official HWiNFO download page](https://www.hwinfo.com/download/) and download ZIP archives from the official website.

Verified on 2026-10-27: the manifest now uses `8.55-6110`. Its official ZIP downloaded successfully, passed integrity checks, and matched the SHA-256 published on [dAppCDN](https://dappcdn.com/download/utilities/hwinfo). The old `8.55-6095` download URL returned HTTP 404.

**Scheduled version detection is currently blocked.** The GitHub-hosted Windows runner received HTTP 403 from both the official version page and dAppCDN. A browser User-Agent and `curl` also failed to access dAppCDN. Scheduled automatic updates therefore remain unreliable. Continuous tracking requires a self-hosted runner with verified access to these pages, or another verified version source.

Installation download availability depends on the user's network. Check the official download page and [Excavator logs](https://github.com/RyanWu080/my-scoop-bucket/actions/workflows/excavator.yml) if problems occur. A successful workflow does not establish that every package was checked successfully; inspect the `hwinfo-beta` log output.

### PCL CE requirements

All four PCL CE packages require Microsoft .NET 10 Desktop Runtime. If needed, install it with:

```powershell
scoop bucket add extras
scoop install extras/windowsdesktop-runtime
```

### PCL CE updates

`pcl-ce` and `pcl-ce-unrestrict` track stable releases only, each from its own upstream repository.

`pcl-ce-beta` and `pcl-ce-unrestrict-beta` track the most recently published release from their respective repositories, including both stable and beta releases. They automatically select the matching `Release` or `Beta` executable. When a stable release is published after a beta, these packages update to that stable release and continue tracking future betas.

Use Scoop for updates and disable automatic update downloads in the launcher's settings:

```powershell
scoop update
# Replace the package name with the one you installed
scoop update pcl-ce-unrestrict-beta
```

### PCL CE commands and data

Each PCL CE package has a distinct command and Start Menu shortcut. The command matches the package name.

Each package preserves its own `PCL` and `.minecraft` directories across updates. Settings stored by the launcher in AppData may still be shared between packages.

### Manifest maintenance

The repository includes CI checks and an Excavator workflow scheduled to run every four hours. Manifest `checkver` rules detect new versions, and `autoupdate` rules generate updated download URLs.

For new or updated manifests, see Scoop's [App Manifests documentation](https://github.com/ScoopInstaller/Scoop/wiki/App-Manifests) and [contribution guide](https://github.com/ScoopInstaller/.github/blob/main/.github/CONTRIBUTING.md).
