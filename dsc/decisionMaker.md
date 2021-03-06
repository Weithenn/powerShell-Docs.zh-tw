---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "dsc,powershell,設定,安裝"
title: "適合決策者的預期狀態設定概觀"
ms.openlocfilehash: e39ab5138b20653e46ac35fa32b99d268f96b2df
ms.sourcegitcommit: f069ff0689006fece768f178c10e3e3eeaee09f0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2017
---
# <a name="desired-state-configuration-overview-for-decision-makers"></a>適合決策者的預期狀態設定概觀

本文件說明使用 PowerShell 預期狀態設定 (DSC) 的商業優勢。 這不是技術指南。

## <a name="what-is-desired-state-configuration"></a>什麼是預期狀態設定？

Windows PowerShell 預期狀態設定 (DSC) 是 Windows 內建的開放式標準設定管理平台。 DSC 的彈性足以因應部署生命週期 (開發、測試、生產階段前，生產環境) 各階段穩定且一致的運作，向外延展時亦然。 

DSC 的中心概念是「[設定](https://msdn.microsoft.com/en-us/powershell/dsc/configurations)」。
設定是容易讀取的文件，描述由特定特性的電腦 (「節點」) 組成的環境。 這些特性可以簡單到像是確保已啟用特定的 Windows 功能，也可以複雜到像是部署 SharePoint。 

DSC 也有內建的監視和報告。 如果系統不再相容，DSC 會引發警示，採取動作更正系統。 

## <a name="benefits-of-using-desired-state-configuration"></a>使用預期狀態設定的優勢

設定應設計為易於讀取、儲存及更新。 設定會宣告目標裝置應有的狀態，不需要撰寫如何成就裝置狀態的指示。 這可讓您以更經濟的成本透過 DSC 了解、採用、實作和維護設定。 

建立設定即表示，已在單一位置將複雜的部署步驟擷取為「單一事實來源」。 這讓特定電腦集合的重複部署更不容易出錯。 也因此可讓部署更快速且更可靠，藉此縮短複雜部署的完成時間。

設定也可透過 [PowerShell 資源庫](https://powershellgallery.com) \(英文\) 來分享，亦即針對您要完成的工作，可能已經有共同的案例與最佳做法。


## <a name="desired-state-configuration-and-devops"></a>預期狀態設定和 DevOps

[DevOps (英文)](http://blogs.technet.com/b/ashleymcglone/archive/2015/11/20/devops-for-n00bs-ie-windows-people.aspx) 是人員、技術和文化特性的組合，以利快速部署和反覆運算。 DSC 在設計時即已考慮到 DevOps。 讓單一設定定義環境即表示，開發人員可以將需求編碼成設定、將此設定簽入原始檔控制，而作業小組可以輕鬆部署程式碼，不必進行可能會出錯的手動程序。 

設定也是[資料導向](https://msdn.microsoft.com/en-us/powershell/dsc/configdata)，讓作業小組更容易識別及變更環境，不用開發人員介入。 

## <a name="desired-state-configuration-on--and-off-premises"></a>內部部署及外部部署的預期狀態設定

DSC 可同時用來管理內部部署及外部部署的部署。 在內部部署解決方案方面，DSC 具有[提取伺服器](https://msdn.microsoft.com/en-us/powershell/dsc/pullserver)，可用來集中管理電腦並回報其狀態。 在雲端解決方案方面，只要能夠使用 Windows 的地方都可以使用 DSC。 建置在預期狀態設定之上的 Azure 也有特定項目，例如能集中 DSC 報告的 [Azure 自動化](https://azure.microsoft.com/en-us/documentation/services/automation/)。 

## <a name="dsc-and-compatibility"></a>DSC 和相容性

DSC 雖是在 Windows Server 2012 R2 引進，卻是透過 Windows Management Framework (WMF) 封裝供低階的作業系統使用。 WMF 詳細資訊請參閱 [PowerShell 首頁](https://msdn.microsoft.com/en-us/powershell/)。 

DSC 也可用來管理 Linux。 如需詳細資訊，請參閱[開始使用 DSC for Linux](https://msdn.microsoft.com/en-us/powershell/dsc/lnxgettingstarted)。

