# RyanWu080’s Scoop Bucket

[![Tests](https://github.com/RyanWu080/my-scoop-bucket/actions/workflows/ci.yml/badge.svg)](https://github.com/RyanWu080/my-scoop-bucket/actions/workflows/ci.yml)
[![Excavator](https://github.com/RyanWu080/my-scoop-bucket/actions/workflows/excavator.yml/badge.svg)](https://github.com/RyanWu080/my-scoop-bucket/actions/workflows/excavator.yml)

[中文](#中文) | [English](#english)

## 中文

个人 [Scoop](https://scoop.sh) 软件桶，提供 PCL CE 官方版、解除地区限制版及 HWiNFO Beta。

### 软件清单

| 包名 | 软件来源 | 更新渠道 | 架构 |
| --- | --- | --- | --- |
| `pcl-ce` | [PCL CE 官方版](https://github.com/PCL-Community/PCL-CE) | 正式版 | x64、ARM64 |
| `pcl-ce-beta` | [PCL CE 官方版](https://github.com/PCL-Community/PCL-CE) | 最新 release，含正式版和 beta | x64、ARM64 |
| `pcl-ce-unrestrict` | [解除地区限制版](https://github.com/RyanWu080/PCL-CE-unrestrict) | 正式版 | x64、ARM64 |
| `pcl-ce-unrestrict-beta` | [解除地区限制版](https://github.com/RyanWu080/PCL-CE-unrestrict) | 最新 release，含正式版和 beta | x64、ARM64 |
| `hwinfo-beta` | [HWiNFO](https://www.hwinfo.com) | Beta | x86、x64、ARM64 |

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

- **PCL CE**：需要 Microsoft .NET 10 Desktop Runtime，可通过以下命令安装：

  ```powershell
  scoop bucket add extras
  scoop install extras/windowsdesktop-runtime
  ```

- **更新渠道**：PCL CE 的 beta 包跟踪各自仓库最新发布的 release，正式版发布后也会跟进。建议关闭启动器自动下载更新，统一使用 Scoop 更新。
- **数据保存**：各 PCL CE 包使用独立命令和开始菜单快捷方式，并分别保留 `PCL`、`.minecraft` 目录；AppData 中的设置仍可能共享。
- **HWiNFO Beta**：x64、ARM64 使用官方更新接口公布的固定更新包地址。x86 仍使用官网 ZIP，部分网络可能返回 403；可改用[官方下载页](https://www.hwinfo.com/download/)在浏览器中下载。

仓库每 4 小时检查更新，并校验 HWiNFO Beta 的版本及 x64、ARM64 下载哈希。运行结果见 [Excavator](https://github.com/RyanWu080/my-scoop-bucket/actions/workflows/excavator.yml)；清单格式参考 [Scoop 文档](https://github.com/ScoopInstaller/Scoop/wiki/App-Manifests)。

## English

A personal [Scoop](https://scoop.sh) bucket for official PCL CE, a fork with regional restrictions removed, and HWiNFO Beta.

### Packages

| Package | Source | Update channel | Architectures |
| --- | --- | --- | --- |
| `pcl-ce` | [Official PCL CE](https://github.com/PCL-Community/PCL-CE) | Stable | x64, ARM64 |
| `pcl-ce-beta` | [Official PCL CE](https://github.com/PCL-Community/PCL-CE) | Latest release, including stable and beta | x64, ARM64 |
| `pcl-ce-unrestrict` | [Fork with regional restrictions removed](https://github.com/RyanWu080/PCL-CE-unrestrict) | Stable | x64, ARM64 |
| `pcl-ce-unrestrict-beta` | [Fork with regional restrictions removed](https://github.com/RyanWu080/PCL-CE-unrestrict) | Latest release, including stable and beta | x64, ARM64 |
| `hwinfo-beta` | [HWiNFO](https://www.hwinfo.com) | Beta | x86, x64, ARM64 |

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

- **PCL CE** requires Microsoft .NET 10 Desktop Runtime. Install it with:

  ```powershell
  scoop bucket add extras
  scoop install extras/windowsdesktop-runtime
  ```

- **Update channels**: PCL CE beta packages follow the most recently published release from their respective repositories, including stable releases. Disable automatic update downloads in the launcher and use Scoop for updates.
- **Data**: Each PCL CE package has a distinct command and Start Menu shortcut and preserves its own `PCL` and `.minecraft` directories. AppData settings may still be shared.
- **HWiNFO Beta**: x64 and ARM64 use fixed update archive URLs published in the official update feed. x86 still uses the official ZIP, which may return HTTP 403 on some networks; download through the [official page](https://www.hwinfo.com/download/) in a browser if needed.

Updates are checked every four hours, including HWiNFO Beta version checks and x64/ARM64 download hash verification. See [Excavator](https://github.com/RyanWu080/my-scoop-bucket/actions/workflows/excavator.yml) for results and the [Scoop documentation](https://github.com/ScoopInstaller/Scoop/wiki/App-Manifests) for manifest guidelines.
