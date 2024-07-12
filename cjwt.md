# 特别鸣谢：该文档出至 MAA 的常见问题，简单修改后的，在此特别感谢 MAA 和 Maafw 的开发者们，赞美~

# 常见问题

## 软件无法运行/闪退/报错

### MWA和模拟器安装路径不要有中文，否则可能会有问题。

### 下载/安装问题

- 完整 MWA 软件压缩包命名格式为 "MWA-`版本`-`平台`-`架构`.zip"，其余均为无法单独使用的“零部件”，请仔细阅读。
  在大部分情况下，您需要使用 x64 架构的 MWA，即您需要下载 `MWA-*-win-x64.zip`，而非 `MWA-*-win-arm64.zip`。
- 若在某次自动更新后无法使用或缺失功能，可能是自动更新出现了问题, 请尝试重新下载并解压完整包后手动迁移 `config` 文件夹。

### 运行库问题

此处仅列出官方安装方法，我们无法保证第三方整合包的可靠性。

- 请安装 [Visual C++ 可再发行程序包](https://aka.ms/vs/17/release/vc_redist.x64.exe) 和 [.NET 桌面运行时 8](https://dotnet.microsoft.com/zh-cn/download/dotnet/8.0#:~:text=%E4%BA%8C%E8%BF%9B%E5%88%B6%E6%96%87%E4%BB%B6-,Windows,-Arm64) 并重新启动计算机后再次运行 MWA。  
  推荐使用 Windows 10 或 11 的用户使用 winget 工具进行安装，只需在终端中运行以下命令。

  ```sh
  winget install Microsoft.VCRedist.2015+.x64 Microsoft.DotNet.DesktopRuntime.8
  ```

- 若软件在某次更新后无法运行，也有可能是因运行库版本导致的问题，同样可以尝试再次安装或更新运行库。

### 系统问题

- MAA 不支持 32 位操作系统。
- 以上运行库安装均需要依赖组件存储服务（CBS、TrustedInstaller/TiWorker、WinSxS）。如果组件存储服务被破坏，将不能正常安装。
  我们无法提供除重装系统以外的修复建议，请避免使用未标明精简项及精简风险的“精简版”系统，亦或万年前的旧版系统（1809 等）。

#### Windows N/KN

对于 Windows N/KN（欧洲/韩国），还需安装[媒体功能包](https://support.microsoft.com/zh-cn/topic/c1c6fffa-d052-8338-7a79-a4bb980a700a)。

#### Windows 7

对于 Windows 7，在安装上文提到的运行库之前，还需检查以下补丁是否已安装：

1. [Windows 7 Service Pack 1](https://support.microsoft.com/zh-cn/windows/b3da2c0f-cdb6-0572-8596-bab972897f61)
2. SHA-2 代码签名补丁：
   - KB4474419：[下载链接 1](https://catalog.s.download.windowsupdate.com/c/msdownload/update/software/secu/2019/09/windows6.1-kb4474419-v3-x64_b5614c6cea5cb4e198717789633dca16308ef79c.msu)、[下载链接 2](http://download.windowsupdate.com/c/msdownload/update/software/secu/2019/09/windows6.1-kb4474419-v3-x64_b5614c6cea5cb4e198717789633dca16308ef79c.msu)
   - KB4490628：[下载链接 1](https://catalog.s.download.windowsupdate.com/c/msdownload/update/software/secu/2019/03/windows6.1-kb4490628-x64_d3de52d6987f7c8bdc2c015dca69eac96047c76e.msu)、[下载链接 2](http://download.windowsupdate.com/c/msdownload/update/software/secu/2019/03/windows6.1-kb4490628-x64_d3de52d6987f7c8bdc2c015dca69eac96047c76e.msu)
3. Platform Update for Windows 7（DXGI 1.2、Direct3D 11.1，KB2670838）：[下载链接 1](https://catalog.s.download.windowsupdate.com/msdownload/update/software/ftpk/2013/02/windows6.1-kb2670838-x64_9f667ff60e80b64cbed2774681302baeaf0fc6a6.msu)、[下载链接 2](http://download.windowsupdate.com/msdownload/update/software/ftpk/2013/02/windows6.1-kb2670838-x64_9f667ff60e80b64cbed2774681302baeaf0fc6a6.msu)

##### .NET 8 应用在 Windows 7 上运行异常的缓解措施 [#8238](https://github.com/MaaAssistantArknights/MaaAssistantArknights/issues/8238)

1. 打开 `计算机`，右键空白处，点击属性，点击左侧 `高级系统设置`，点击 `环境变量`。
2. 新建一个系统变量，变量名 `DOTNET_EnableWriteXorExecute`，变量值 `0`。
3. 重启电脑。

我们无法保证将来的版本对 Windows 7 的兼容性，~~都是微软的错~~。

## 连接错误

### 确认 ADB 及连接地址正确

参阅 [连接设置](./connection.md)。

### 关闭现有 ADB 进程

关闭 MwA 后查找 `任务管理器` - `详细信息` 中有无名称包含 `adb` 的进程，如有，结束它后重试连接。

### 正确使用多个 ADB

当 ADB 版本不同时，新启动的进程会关闭旧的进程。因此在需要同时运行多个 ADB，如 Android Studio、Alas、手机助手时，请确认它们的版本相同。

### 避免游戏加速器

部分加速器在启动加速和停止加速之后，都需要重启 MAA、ADB 和模拟器再连接。

同时使用 UU 加速器 和 MuMu 12 可以参考[官方文档](https://mumu.163.com/help/20240321/35047_1144608.html)。

### 重启电脑

重启能解决 97% 的问题。（确信

### 换模拟器

请参阅 [模拟器和设备支持](./device/)。


## 下载到一半提示“登陆”/“鉴权”

请使用 浏览器 / IDM / FDM 等下载器下载文件，**不要用 ↑↓ 迅雷！**

若不行请开梯子后再尝试下载

# [使用教程](https://github.com/MAWHA/MWA/blob/main/%E4%BD%BF%E7%94%A8%E6%95%99%E7%A8%8B.md)
