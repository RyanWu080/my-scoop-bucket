# RyanWu080 的 Scoop 软件桶

[![Tests](https://github.com/RyanWu080/my-scoop-bucket/actions/workflows/ci.yml/badge.svg)](https://github.com/RyanWu080/my-scoop-bucket/actions/workflows/ci.yml)
[![Excavator](https://github.com/RyanWu080/my-scoop-bucket/actions/workflows/excavator.yml/badge.svg)](https://github.com/RyanWu080/my-scoop-bucket/actions/workflows/excavator.yml)

用于 [Scoop](https://scoop.sh) 的个人 Windows 软件桶，提供 PCL CE 官方版、解限版及 HWiNFO Beta 的安装与更新清单。

## 软件清单

| 包名 | 软件来源 | 更新渠道 | 支持架构 |
| --- | --- | --- | --- |
| `pcl-ce` | [PCL CE 官方版](https://github.com/PCL-Community/PCL-CE) | 仅正式版 | x64、ARM64 |
| `pcl-ce-beta` | [PCL CE 官方版](https://github.com/PCL-Community/PCL-CE) | 最新 release，包含正式版和 beta | x64、ARM64 |
| `pcl-ce-unrestrict` | [PCL CE 解限版](https://github.com/RyanWu080/PCL-CE-unrestrict) | 仅正式版 | x64、ARM64 |
| `pcl-ce-unrestrict-beta` | [PCL CE 解限版](https://github.com/RyanWu080/PCL-CE-unrestrict) | 最新 release，包含正式版和 beta | x64、ARM64 |
| `hwinfo-beta` | [HWiNFO](https://www.hwinfo.com) | Beta | x86、x64、ARM64 |

## 安装

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

# PCL CE 解限正式版
scoop install my-scoop-bucket/pcl-ce-unrestrict

# PCL CE 解限版最新 release，包含 beta
scoop install my-scoop-bucket/pcl-ce-unrestrict-beta

# HWiNFO Beta 硬件检测与监控工具
scoop install my-scoop-bucket/hwinfo-beta
```

## PCL CE 使用说明

### 运行环境

四个 PCL CE 软件包均需要 Microsoft .NET 10 Desktop Runtime。若尚未安装，可执行：

```powershell
scoop bucket add extras
scoop install extras/windowsdesktop-runtime
```

### 更新渠道

`pcl-ce` 和 `pcl-ce-unrestrict` 仅跟踪各自仓库的正式版。

`pcl-ce-beta` 和 `pcl-ce-unrestrict-beta` 按发布时间跟踪各自仓库的最新 release，同时检查正式版和 beta，自动匹配 `Release` 或 `Beta` 可执行文件。正式版发布晚于 beta 时，会更新到正式版；后续发布新 beta 时，继续跟踪新 beta。

建议通过 Scoop 更新，并在启动器设置中关闭自动下载更新：

```powershell
scoop update
# 将包名替换为实际安装的版本
scoop update pcl-ce-unrestrict-beta
```

### 命令与数据保存

四个 PCL CE 软件包使用不同的命令和开始菜单快捷方式，命令与包名一致。

各包的 `PCL` 和 `.minecraft` 目录会分别持久化，更新时保留。启动器存放在 AppData 中的设置仍可能在不同版本之间共享。

## 清单维护

仓库配置了 CI 检查，以及每 4 小时运行一次的 Excavator 自动更新工作流。清单中的 `checkver` 用于检测版本，`autoupdate` 用于生成新版下载地址。

新增或修改清单时，可参考 Scoop 的 [App Manifests 文档](https://github.com/ScoopInstaller/Scoop/wiki/App-Manifests)和[贡献指南](https://github.com/ScoopInstaller/.github/blob/main/.github/CONTRIBUTING.md)。
