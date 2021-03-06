---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "wmf,powershell,設定"
ms.openlocfilehash: 2c7e718bc518b332cb4303ef73b1bf5c924ca471
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/12/2017
---
# <a name="powershell-module-discovery-install-and-inventory-with-powershellget"></a>使用 PowerShellGet 探索、安裝及清查 PowerShell 模組
 
PowerShellGet 隨附於這一版的 WMF：
-   Find-Module 可以使用 -Tag 參數篩選模組中繼資料
-   Find-Module 可以使用 -Filter 參數篩選存放庫特定的搜尋語言
-   Find-Module 可以使用 -Command、-DscResource 和 -Includes 參數根據模組內容進行篩選
-   Find-DscResource 可以在存放庫中探索個別的 DSC 資源
-   支援使用 NuGet 從檔案共用安裝和發佈至檔案共用

## <a name="example-commands"></a>範例命令
```powershell
\# Find all modules with tags Azure or DSC
Find-Module -Tag Azure, DSC

\# Find modules with a specific DscResource
Find-Module -DscResource xFirewall

\#Find modules with specific commands
Find-Module -Command Get-ScriptAnalyzerRule, Invoke-ScriptAnalyzer

\# Find all modules with Dsc resources
Find-Module -Includes DscResource

\# Find all modules with cmdlets
Find-Module -Includes Cmdlet

\# Find all modules with functions
Find-Module -Includes Function

\# Find all DSC resources
Find-DscResource

\# Find all DSC resources contained within a specific module
Find-DscResource -ModuleName xNetworking

\# Find all DSC resources in modules with DSCResourceKit or DesiredStateConfiguration
Find-DscResource -Tag DesiredStateConfiguration, DSCResourceKit

\# Find modules using -Filter parameter
\# Specified filter value is searched in Name and Description properties
Find-Module -Filter Cookbook -Repository PSGallery
Find-Module -Filter RBAC -Repository PSGallery
```

## <a name="new-features-in-powershellget"></a>PowerShellGet 的新功能
-   Windows PowerShell 5.0 或更新版本的並存版本支援
-   模組相依性安裝支援
-   三個新的 Cmdlet
    -   Get-InstalledModule
    -   Uninstall-Module
    -   Save-Module
    
