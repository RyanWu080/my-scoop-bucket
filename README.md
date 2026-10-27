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

### HWiNFO Beta 更新来源

`hwinfo-beta` 从 HWiNFO 官方更新接口 [`ver.txt`](https://www.hwinfo.com/ver.txt) 检测 Beta 版本。接口第一行为正式版，第二行为 Beta；清单读取第二行，并据此生成官网 ZIP 下载地址。

2026-10-27 已在 GitHub 托管的 Windows runner 中验证该接口可用于 Scoop 自动检测。官网及 dAppCDN 的下载网页此前均返回 HTTP 403，因此不再依赖网页抓取。当前清单使用 `8.55-6110`，官网 ZIP 已通过下载、完整性及 SHA-256 校验。

Excavator 每 4 小时检测更新，并在更新后检查官方 Beta 版本是否与清单一致。接口访问失败、格式不匹配或新版未成功写入清单时，工作流会报错，具体原因可查看 [Excavator 日志](https://github.com/RyanWu080/my-scoop-bucket/actions/workflows/excavator.yml)。

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

### HWiNFO Beta update source

`hwinfo-beta` detects Beta versions from the official HWiNFO update feed, [`ver.txt`](https://www.hwinfo.com/ver.txt). Its first line contains the stable version and its second line contains the Beta version. The manifest reads the second line and uses it to generate the official ZIP download URL.

Verified on 2026-10-27: Scoop successfully accessed and parsed this feed on a GitHub-hosted Windows runner. The official and dAppCDN download webpages previously returned HTTP 403, so detection no longer depends on scraping those pages. The current manifest uses `8.55-6110`; its official ZIP passed download, integrity, and SHA-256 checks.

Excavator checks every four hours and verifies that the manifest matches the official Beta version after updating. Feed access failures, unexpected feed formats, or updates that were not applied cause the workflow to fail. See the [Excavator logs](https://github.com/RyanWu080/my-scoop-bucket/actions/workflows/excavator.yml) for details.

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
