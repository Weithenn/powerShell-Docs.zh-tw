---
ms.date: 2017-06-12
contributor: JKeithB
ms.topic: conceptual
keywords: gallery,powershell,cmdlet,psgallery
title: psgallery_deploy_to_azure_automation
ms.openlocfilehash: 91f48fb43d7fb099e34ce5d3b3b632e3cb119d64
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/12/2017
---
<a name="deploy-to-azure-automation"></a>部署至 Azure 自動化
===========================

項目詳細資料頁面上的 [Deploy to Azure Automation] \(部署至 Azure 自動化) 按鈕會將項目從 PowerShell Gallery 部署至 Azure 自動化。

![Deploy to Azure Automation (部署至 Azure 自動化) 按鈕](Images/DeployToAzureAutomationButton.png)

按一下時，會將您重新導向至使用 Azure 帳戶認證所登入的 Azure 管理入口網站。
如果項目包含相依性，則也會將所有相依性部署至 Azure 自動化。

警告︰如果相同的項目和版本已存在於您的自動化帳戶，則再次從 PowerShell Gallery 部署它將會覆寫自動化帳戶中的項目。

如果您部署模組，則它會出現在 [Azure 自動化] 的 [模組] 區段中。  如果您部署指令碼，則它會出現在 [Azure 自動化] 的 [Runbook] 區段中。

將 AzureAutomationNotSupported 標記新增至項目中繼資料，即可停用 [Deploy to Azure Automation] \(部署至 Azure 自動化) 按鈕。

若要深入了解 Azure 自動化，請參閱 [Azure 自動化網站](http://azure.microsoft.com/en-us/services/automation/)。

