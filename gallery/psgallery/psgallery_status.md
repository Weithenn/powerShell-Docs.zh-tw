---
ms.date: 2017-06-12
contributor: JKeithB
ms.topic: conceptual
keywords: gallery,powershell,cmdlet,psgallery
title: psgallery_status
ms.openlocfilehash: af6111d3c511273571bd978c6d0e7447726c2917
ms.sourcegitcommit: f069ff0689006fece768f178c10e3e3eeaee09f0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2017
---
<a name="powershell-gallery-status"></a>PowerShell 資源庫狀態
=========================
## <a name="10102017---powershell-gallery-unavailable-for-2-hours-101017"></a>2017 年 10 月 10 日 - PowerShell 資源庫於 2017 年 10 月 10 日出現 2 個小時無法使用的情況

__影響摘要__：PowerShell 資源庫有一段時間出現非常高的延遲，因而導致間歇性的連線問題。此情況於 2017 年 10 月 10 日，大約下午 5 點 (PDT) 開始出現。 為了解決此問題，網站於大約下午 10 點 (PDT) 開始離線 2 個小時。 網站已在 2017 年 10 月 10 日的午夜之前還原。 
 
__根本原因__：目前仍在調查造成高延遲的根本原因。

__解決方法__：必須使 Web 服務離線並還原以解決主要問題。 

__後續步驟__：持續調查造成原始問題的根本原因。

## <a name="06012017---deploy-to-azure-automation-currently-unavailable"></a>2017 年 6 月 1 日 - 目前無法部署至 Azure 自動化

__影響摘要__：目前無法將具有相依性的項目從「PowerShell 資源庫」部署至「Azure 自動化」。  仍然無法從「Azure 自動化」內部自「PowerShell 資源庫」匯入項目。  
 
__根本原因__：項目如果與其他項目相依且先前已部署至「Azure 自動化」，系統就不會將其部署至「Azure 自動化」。 針對「部署至 Azure 自動化」功能，工程師已找出一個與為具有相依性的項目產生 ARM 範本有關的問題。

__解決方法__：工程師正在努力解決此問題。  使用者目前的因應措施是從「Azure 自動化」內部自「PowerShell 資源庫」匯入項目。 

__後續步驟__：工程師將在稍後發行修正。  在此同時，請使用建議的因應措施。 


## <a name="04112017---users-unable-to-log-in-with-azure-active-directory-aad-accounts"></a>04/11/2017 - 使用者無法登入 Azure Active Directory (AAD) 帳戶

__影響摘要__：有些使用者過去無法使用 Azure AD 帳戶登入 PowerShell 資源庫。 
 
__根本原因__︰在更新至更安全的 AAD 互動方式期間，錯過一項設定變更。 為驗證變更而進行的測試不包括特定類型的 AAD 帳戶，所以部署會繼續進行。

__解決方法__︰工程師找到遺失的設定，並已修正問題。 

__後續步驟__︰我們會修改測試以包括更廣泛的 AAD 帳戶類型。

## <a name="03272017---resolved-unable-to-see-individual-module-and-script-pages"></a>2017 年 3 月 27 日 - 已解決：無法看到個別模組和指令碼頁面

__影響摘要__：https://www.powershellgallery.com 上個別模組和指令碼頁面的直接連結已中斷。 所有區域均回報此問題。 這並未影響任何 PowerShellGet Cmdlet，Install-Module、Install-Script、Update-Module、Update-Script、Publish-Module、Publish-Script 仍繼續運作。

__根本原因__：工程師確認原因出自將社交媒體按鈕 (例如 Facebook) 引入到頁面上。  

__解決方法__：工程師停用了 Facebook 計數資訊，以修正此問題。

__後續步驟__：我們開啟了內部追蹤問題，以修正我們的 Facebook API 使用方式。

## <a name="12152016---unable-to-send-emails-via-powershellgallery-website"></a>12/15/2016 - 無法透過 PowerShellGallery 網站傳送電子郵件

__影響的摘要__：在 12/13/2016 和 12/15/2016 之間，PowerShell 資源庫系統管理員未收到透過「連絡擁有者」、「管理擁有者」、「連絡支援人員」或「檢舉不當使用」傳送的任何訊息。  
__根本原因__︰工程師找出其肇因為 SMTP 伺服器的驗證問題。  
__解決方法__︰工程師能夠解決驗證問題並還原 SMTP 伺服器連線。  
__後續步驟__︰如果您在這段期間使用連絡「擁有者」、「管理擁有者」、「連絡支援人員」或「檢舉不當使用」連結來傳送郵件給 cgadmin@microsoft.com，而我們沒有回應，請再試一次。 造成您的不便，我們深感抱歉。  



## <a name="8102016---resolved-unable-to-send-emails-to-cgadminmicrosoftcom"></a>2016/8/10 - 已解決︰無法傳送電子郵件給 cgadmin@microsoft.com

__影響摘要__：2016 年 8 月5 日到 2016 年 8 月 10 日之間，客戶無法傳送電子郵件給 cgadmin@microsoft.com，也無法使用「與我們連絡」功能。  
__根本原因__︰工程師確認原因出自電子郵件帳戶的設定變更。  
__解決方法__︰工程師已找出解決此設定問題的方法。  
__後續步驟__︰若您曾在這段期間使用 [與我們連絡] 連結，或傳送郵件給 cgadmin@microsoft.com，但我們未回應，請再試一次。 感謝您的耐心配合。



## <a name="7132016---download-items-failed"></a>2016/7/13 -下載項目失敗

__影響摘要__：2016/7/11 到 2016/7/13 之間，有一些客戶出現無法從 PowerShell 資源庫下載項目的問題。 此問題可能會顯示在 Install-Module/Install-Script 與 Save-Module/Save-Script 傳回的下列錯誤訊息中︰

```powershell
PS C:\> Install-Module xStorage 
PackageManagement\Install-Package : Package 'xStorage' failed to be installed because: 
End of Central Directory record could not be found. At C:\Program 
Files\WindowsPowerShell\Modules\PowerShellGet\1.0.0.1\PSModule.psm1:1375 char:21 + ... 
$null = PackageManagement\Install-Package @PSBoundParameters + 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ + CategoryInfo : InvalidResult: 
(xStorage:String) [Install-Package], Exception + FullyQualifiedErrorId : Package '{0}' 
failed to be installed because: {1},Microsoft.PowerShell.PackageManagement.Cmdlets.InstallPackage 
```

__初步的根本原因__︰工程師確認這是 Azure 內容傳遞網路 (CDN) 的問題。Azure CDN 於 2016/7/11 部署到 PowerShell 資源庫。  
__緩和方法__：工程師停用了 PowerShell 資源庫中的 Azure CDN。  
__後續步驟__︰調查最根本的原因，並制定解決方法，以避免日後再次發生。


## <a name="5192016---download-items-failed"></a>2016/5/19 - 下載項目失敗
__影響摘要__：2016/5/17 到 2016/5/19 之間，有一些客戶出現無法從 PowerShell 資源庫下載項目的問題。 此問題可能會顯示在 Install-Module/Install-Script 與 Save-Module/Save-Script 傳回的下列錯誤訊息中︰

```powershell
VERBOSE: Hash for package 'AzureRM.OperationalInsights' does not match hash provided from the server.
VERBOSE: InstallPackageLocal' - name='AzureRM.OperationalInsights', version='1.0.8',
destination='C:\Users\jbritt\AppData\Local\Temp\2\1741355729'
WARNING: Package 'AzureRM.OperationalInsights' failed to be installed because: 
End of Central Directory record could not be found. 
WARNING: Dependent Package 'AzureRM.OperationalInsights' failed to install. 
WARNING: Package 'AzureRM' failed to install. 
VERBOSE: Module 'AzureRM.Network' was saved successfully. 
VERBOSE: Saving the dependency module 'AzureRM.NotificationHubs' with version '1.0.8' for the 
module 'AzureRM'. 
VERBOSE: Module 'AzureRM.NotificationHubs' was saved successfully. 
PackageManagement\Save-Package : Unable to save the module 'AzureRM'. At C:\Program 
Files\WindowsPowerShell\Modules\PowerShellGet\1.0.0.1\PSModule.psm1:1187 char:21 + 
$null = PackageManagement\Save-Package @PSBoundParameters + 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ + 
CategoryInfo : InvalidOperation: (Microsoft.Power...ets.SavePackage:SavePackage) 
[Save-Package], Exception + FullyQualifiedErrorId : ProviderFailToDownloadFile,
Microsoft.PowerShell.PackageManagement.Cmdlets.SavePackage 
```

__初步的根本原因__︰工程師確認是 Azure 內容傳遞網路 (CDN)基礎提供者中斷所致。Azure CDN 於 2016/5/17 部署到 PowerShell 資源庫。  
__緩和方法__：工程師停用了 PowerShell 資源庫中的 Azure CDN。  
__後續步驟__︰調查最根本的原因，並制定解決方法，以避免日後再次發生。

