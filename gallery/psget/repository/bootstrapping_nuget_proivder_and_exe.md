---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: "資源庫,powershell,cmdlet,psget"
title: "啟動載入 NuGet 提供者和 EXE"
ms.openlocfilehash: 0036972eb9a0c20469da1aadafe223e6ec80f16a
ms.sourcegitcommit: a5c0795ca6ec9332967bff9c151a8572feb1a53a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2017
---
# <a name="bootstrap-both-nuget-provider-and-nugetexe-or-bootstrap-only-nuget-provider"></a>同時啟動載入 NuGet 提供者和 NuGet.exe 或只啟動載入 NuGet 提供者

NuGet.exe 不包含在最新的 NuGet 提供者中。
若要執行模組或指令碼的發行作業，PowerShellGet 需要二進位可執行檔 NuGet.exe。
所有其他作業 (包括「尋找」、「安裝」、「儲存」及「解除安裝」) 則只需要 NuGet 提供者。
PowerShellGet 包含可處理 NuGet 提供者與 NuGet.exe 之組合啟動載入或僅 NuGet 提供者之啟動載入的邏輯。
在上述任一情況下，都應該只會顯示單一提示訊息。
如果電腦未連線至網際網路，使用者或管理員就必須將受信任之 NuGet 提供者和/或 NuGet.exe 檔案的執行個體複製到未連線的電腦。

>**注意**：從版本 6 開始，NuGet 提供者會包含在 PowerShell 的安裝中。 [http://github.com/powershell/powershell](http://github.com/powershell/powershell)

## <a name="resolving-error-when-the-nuget-provider-has-not-been-installed-on-a-machine-that-is-internet-connected"></a>解決在已連線至網際網路之電腦上尚未安裝 NuGet 提供者時的錯誤

```powershell
PS C:\> Find-Module -Repository PSGallery -Verbose -Name Contoso

NuGet provider is required to continue
PowerShellGet requires NuGet provider version '2.8.5.201' or newer to interact with NuGet-based repositories. The NuGet provider must be available in 'C:\Program Files\PackageManagement\ProviderAssemblies' or
'C:\Users\manikb\AppData\Local\PackageManagement\ProviderAssemblies'. You can also install the NuGet provider by running 'Install-PackageProvider -Name NuGet -MinimumVersion 2.8.5.201 -Force'. Do you want PowerShellGet to install and import the NuGet provider
now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): n
Find-Module : NuGet provider is required to interact with NuGet-based repositories. Please ensure that '2.8.5.201' or newer version of NuGet provider is installed.
At line:1 char:1
+ Find-Module -Repository PSGallery -Verbose -Name Contoso
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [Find-Module], InvalidOperationException
   + FullyQualifiedErrorId : CouldNotInstallNuGetProvider,Find-Module

PS C:\> Find-Module -Repository PSGallery -Verbose -Name Contoso

NuGet provider is required to continue
PowerShellGet requires NuGet provider version '2.8.5.201' or newer to interact with NuGet-based repositories. The NuGet provider must be available in 'C:\Program Files\PackageManagement\ProviderAssemblies' or
'C:\Users\manikb\AppData\Local\PackageManagement\ProviderAssemblies'. You can also install the NuGet provider by running 'Install-PackageProvider -Name NuGet -MinimumVersion 2.8.5.201 -Force'. Do you want PowerShellGet to install and import the NuGet provider
now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): Y
VERBOSE: Installing NuGet provider.

Version    Name                                Type       Repository           Description
-------    ----                                ----       ----------           -----------
2.5        Contoso                             Module     PSGallery        Contoso module
```
## <a name="resolving-error-when-the-nuget-provider-is-available-and-nugetexe-is-not-available-during-the-publish-operation-on-a-machine-that-is-internet-connected"></a>解決在已連線至網際網路之電腦上執行發行作業的期間有 NuGet 提供者可用但沒有 NuGet.exe 可用時的錯誤

```powershell
PS C:\> Publish-Module -Name Contoso -Repository PSGallery -Verbose

NuGet.exe is required to continue
PowerShellGet requires NuGet.exe to publish an item to the NuGet-based repositories. NuGet.exe must be available under one of the paths specified in PATH environment variable value. Do you want PowerShellGet to install NuGet.exe now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): N
Publish-Module : NuGet.exe is required to interact with NuGet-based repositories. Please ensure that NuGet.exe is available under one of the paths specified in PATH environment variable value.
At line:1 char:1
+ Publish-Module -Name Contoso -Repository PSGallery -Verbose
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [Publish-Module], InvalidOperationException
    + FullyQualifiedErrorId : CouldNotInstallNuGetExe,Publish-Module

PS C:\> Publish-Module -Name Contoso -Repository PSGallery -Verbose

NuGet.exe is required to continue
PowerShellGet requires NuGet.exe to publish an item to the NuGet-based repositories. NuGet.exe must be available under one of the paths specified in PATH environment variable value. Do you want PowerShellGet to install NuGet.exe now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): Y
VERBOSE: Installing NuGet.exe.
VERBOSE: Successfully published module 'Contoso' to the module publish location 'https://www.powershellgallery.com/api/v2/'. Please allow few minutes for 'Contoso' to show up in the search results.
```

## <a name="resolving-error-when-both-nuget-provider-and-nugetexe-are-not-available-during-the-publish-operation-on-a-machine-that-is-internet-connected"></a>解決在已連線至網際網路之電腦上執行發行作業的期間既沒有 NuGet 提供者也沒有 NuGet.exe 可用時的錯誤

```powershell
PS C:\> Publish-Module -Name Contoso -Repository PSGallery -Verbose

NuGet.exe and NuGet provider are required to continue
PowerShellGet requires NuGet.exe and NuGet provider version '2.8.5.201' or newer to interact with the NuGet-based repositories. Do you want PowerShellGet to install both NuGet.exe and NuGet provider now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): N
Publish-Module : PowerShellGet requires NuGet.exe and NuGet provider version '2.8.5.201' or newer to interact with the NuGet-based repositories. Please ensure that '2.8.5.201' or newer version of NuGet provider is installed and NuGet.exe is available under 
one of the paths specified in PATH environment variable value.
At line:1 char:1
+ Publish-Module -Name Contoso -Repository PSGallery -Verbose
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [Publish-Module], InvalidOperationException
    + FullyQualifiedErrorId : CouldNotInstallNuGetBinaries,Publish-Module

PS C:\> Publish-Module -Name Contoso -Repository PSGallery -Verbose

NuGet.exe and NuGet provider are required to continue
PowerShellGet requires NuGet.exe and NuGet provider version '2.8.5.201' or newer to interact with the NuGet-based repositories. Do you want PowerShellGet to install both NuGet.exe and NuGet provider now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): Y
VERBOSE: Installing NuGet provider.
VERBOSE: Installing NuGet.exe.
VERBOSE: Successfully published module 'Contoso' to the module publish location 'https://www.powershellgallery.com/api/v2/'. Please allow few minutes for 'Contoso' to show up in the search results.
```

## <a name="manually-bootstrapping-the-nuget-provider-on-a-machine-that-is-not-connected-to-the-internet"></a>在未連線至網際網路的電腦上手動啟動載入 NuGet 提供者

上面示範的程序是假設電腦已連線至網際網路，並且可從公用位置下載檔案。
如果無法那麼做，則只能選擇使用上述程序來啟動載入電腦，然後透過受信任的離線程序將提供者手動複製到隔離的節點上。
此情況最常見的使用案例是有可用的私用資源庫來支援隔離的環境時。

依照上述程序來啟動載入已連線至網際網路的電腦之後，您將可在下列位置找到提供者檔案：
```
C:\Program Files\PackageManagement\ProviderAssemblies\
```

NuGet 提供者的資料夾/檔案結構將會是 (版本號碼可能不同):

NuGet<br>
--2.8.5.208<br>
----Microsoft.PackageManagement.NuGetProvider.dll

請使用受信任的程序將這些資料夾和檔案複製到離線電腦。

## <a name="manually-bootstrapping-nugetexe-to-support-publish-operations-on-a-machine-that-is-not-connected-to-the-internet"></a>手動啟動載入 NuGet.exe 以支援在未連線至網際網路的電腦上執行發行作業

除了手動啟動載入 NuGet 提供者的程序之外，如果將使用 *Publish-Module* 或 *Publish-Script* Cmdlet 從該電腦將模組或指令碼發行至私用資源庫，則會需要 NuGet.exe 二進位可執行檔。
此情況最常見的使用案例是有可用的私用資源庫來支援隔離的環境時。
有兩個選項可取得 NuGet.exe 檔案。

其中一個選項是啟動載入已連線至網際網路的電腦，然後使用受信任的程序將檔案複製到離線電腦。
啟動載入已連線至網際網路的電腦之後，NuGet.exe 二進位檔將會位於下列兩個資料夾其中之一：

如果使用已提升的權限 (以系統管理員身分) 來執行 *Publish-Module* 或 *Publish-Script*：
```
$env:ProgramData\Microsoft\Windows\PowerShell\PowerShellGet
```

如果以未提升權限的使用者身分執行 Cmdlet：
```
$env:userprofile\AppData\Local\Microsoft\Windows\PowerShell\PowerShellGet\
```

第二個選項是從 NuGet.Org 網站 ([https://dist.nuget.org/index.html](https://dist.nuget.org/index.html)) 下載 NuGet.exe<br>
為生產環境電腦選取 NugGet 版本時，請確定版本比 2.8.5.208 新，並認明該版本已標示為「建議使用」。
如果該檔案是透過瀏覽器下載的，請記得將檔案解除鎖定。
您可以使用 *Unblock-File* Cmdlet 來執行此操作。

不論是使用哪一個選項，都可以將 NuGet.exe 檔案複製到 *$env:path* 中的任何位置，但標準位置是：

將可執行檔設為可用，以便讓所有使用者都可使用 *Publish-Module* 和 *Publish-Script* Cmdlet：
```
$env:ProgramData\Microsoft\Windows\PowerShell\PowerShellGet
```

若要將可執行檔設為僅供特定使用者使用，請只複製到該使用者之設定檔內的位置：
```
$env:userprofile\AppData\Local\Microsoft\Windows\PowerShell\PowerShellGet\
```

