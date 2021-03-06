---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "執行遠端命令"
ms.assetid: d6938b56-7dc8-44ba-b4d4-cd7b169fd74d
ms.openlocfilehash: 5cf9690b8fe4549a99186f172cb6f0de156a4dea
ms.sourcegitcommit: c5251755c4442487f99ff74fadf7e37bbf039089
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="running-remote-commands"></a>執行遠端命令
您可以使用單一 Windows PowerShell 命令，在一或數百部電腦上執行命令。 Windows PowerShell 透過使用各種技術 (包括 WMI、RPC 與 WS) 支援遠端運算。

## <a name="remoting-without-configuration"></a>不需要進行設定的遠端執行功能
許多 Windows PowerShell Cmdlet 都有 ComputerName 參數，可讓您收集資料，並變更一或多部遠端電腦的設定。 它們使用各種通訊技術，且許多都能在 Windows PowerShell 支援的所有 Windows 作業系統上運作，而不需要特殊設定。

這些 Cmdlet 包含：
* [Restart-Computer](https://go.microsoft.com/fwlink/?LinkId=821625)
* [Test-Connection](https://go.microsoft.com/fwlink/?LinkId=821646)
* [Clear-EventLog](https://go.microsoft.com/fwlink/?LinkId=821568)
* [Get-EventLog](https://go.microsoft.com/fwlink/?LinkId=821585)
* [Get-HotFix](https://go.microsoft.com/fwlink/?LinkId=821586)
  - [Get-Process](https://go.microsoft.com/fwlink/?linkid=821590)
* [Get-Service](https://go.microsoft.com/fwlink/?LinkId=821593)
* [Set-Service](https://go.microsoft.com/fwlink/?LinkId=821633)
* [Get-WinEvent](https://go.microsoft.com/fwlink/?linkid=821529)
* [Get-WmiObject](https://go.microsoft.com/fwlink/?LinkId=821595)

一般而言，支援遠端處理而不需要特殊設定的 Cmdlet 具有 ComputerName 參數，而沒有 Session 參數。 若要在您的工作階段中尋找這些 Cmdlet，請輸入：

```
Get-Command | where { $_.parameters.keys -contains "ComputerName" -and $_.parameters.keys -notcontains "Session"}
```

## <a name="windows-powershell-remoting"></a>Windows PowerShell 遠端執行功能
Windows PowerShell 遠端執行功能使用 WS-Management 通訊協定，可讓您在一或多部遠端電腦上執行任何 Windows PowerShell 命令。 它可讓您建立持續連線、啟動 1:1 互動式工作階段，以及在多部電腦上執行指令碼。

若要使用 Windows PowerShell 遠端執行功能，必須針對遠端管理設定遠端電腦。 如需包括指示的詳細資訊，請參閱[關於遠端需求](https://technet.microsoft.com/en-us/library/dd315349.aspx)。

設定 Windows PowerShell 遠端執行功能之後，許多遠端處理策略就可供您使用。 這份文件的其餘部分只列出其中幾個。 如需詳細資訊，請參閱[關於遠端](https://technet.microsoft.com/en-us/library/dd347744.aspx)與[關於遠端常見問題集](https://technet.microsoft.com/en-us/library/dd347744.aspx)。

### <a name="start-an-interactive-session"></a>啟動互動式工作階段
若要啟動與單一遠端電腦的互動式工作階段，請使用 [Enter-PSSession](https://go.microsoft.com/fwlink/?LinkId=821477) Cmdlet。
例如，若要啟動與 Server01 遠端電腦的互動式工作階段，請輸入：

```
Enter-PSSession Server01
```

命令提示字元將變更為顯示您所連線之電腦的名稱。 從那時開始，您在提示字元中輸入的所有命令都會在遠端電腦上執行，而結果會顯示本機電腦上。

若要結束互動式工作階段，請輸入：

```
Exit-PSSession
```

如需 Enter-PSSession 與 Exit-PSSession Cmdlet 的詳細資訊，請參閱 [Enter-PSSession](https://go.microsoft.com/fwlink/?LinkId=821477) 與 [Exit-PSSession](https://go.microsoft.com/fwlink/?LinkID=821478)。

### <a name="run-a-remote-command"></a>執行遠端命令
若要在一或多部遠端電腦上執行任何命令，請使用 [Invoke-Command](https://go.microsoft.com/fwlink/?LinkId=821493) Cmdlet。
例如，若要在 Server01 與 Server02 遠端電腦上執行 [Get-UICulture](https://go.microsoft.com/fwlink/?LinkId=821806) 命令，請輸入：

```
Invoke-Command -ComputerName Server01, Server02 -ScriptBlock {Get-UICulture}
```

輸出會傳回到您的電腦。

```
LCID    Name     DisplayName               PSComputerName
----    ----     -----------               --------------
1033    en-US    English (United States)   server01.corp.fabrikam.com
1033    en-US    English (United States)   server02.corp.fabrikam.com
```
如需 Invoke-Command Cmdlet 的詳細資訊，請參閱 [Invoke-Command](https://go.microsoft.com/fwlink/?LinkId=821493)。

### <a name="run-a-script"></a>執行指令碼
若要在一或多部遠端電腦上執行指令碼，請使用 Invoke-Command Cmdlet 的 FilePath 參數。 您的本機電腦上必須有該指令碼或可存取該指令碼。 結果會傳回到您的本機電腦。

例如，下列命令會在 Server01 與 Server02 遠端電腦上執行 DiskCollect.ps1 指令碼。

```
Invoke-Command -ComputerName Server01, Server02 -FilePath c:\Scripts\DiskCollect.ps1
```

如需 Invoke-Command Cmdlet 的詳細資訊，請參閱 [Invoke-Command](https://go.microsoft.com/fwlink/?LinkId=821493)。

### <a name="establish-a-persistent-connection"></a>建立持續連線
若要執行一系列共用資料的相關命令，請在遠端電腦上建立工作階段，然後使用 Invoke-Command Cmdlet 在您建立的工作階段中執行命令。 若要建立遠端工作階段，請使用 New-PSSession Cmdlet。

例如，下列命令會在 Server01 電腦上建立遠端工作階段，並在 Server02 電腦上建立另一個遠端工作階段。 它會將該工作階段物件儲存於 $s 變數中。

```
$s = New-PSSession -ComputerName Server01, Server02
```

現在，工作階段已建立，您可以在其中執行任何命令。 因為工作階段是持續性，您可以在單一命令中收集資料，並將它用於後續的命令。

例如，下列命令會在 $s 變數的工作階段中執行 Get-HotFix 命令，並將結果儲存在 $h 變數中。 $h 變數會建立在 $s 的各個工作階段中，但不會存在於本機工作階段。

```
Invoke-Command -Session $s {$h = Get-HotFix}
```

現在您可以在後續命令中使用 $h 變數中的資料，例如下列範例。 結果會顯示在本機電腦上。

```
Invoke-Command -Session $s {$h | where {$_.InstalledBy -ne "NTAUTHORITY\SYSTEM"}}
```

### <a name="advanced-remoting"></a>進階遠端處理
Windows PowerShell 遠端管理在這裡開始。 使用 Windows PowerShell 安裝的 Cmdlet，您可以同時建立及設定本機與遠端電腦的遠端工作階段、建立自訂與受限制的工作階段、允許使用者從實際隱含執行於遠端工作階段的遠端工作階段匯入命令，以及設定遠端工作階段安全性等。

為簡化遠端設定，Windows PowerShell 包含 WSMan 提供者。 提供者建立的 WSMAN: 磁碟機可讓您瀏覽本機電腦與遠端電腦上組態設定的階層。
如需 WSMan 提供者的詳細資訊，請參閱 [WSMan 提供者](https://technet.microsoft.com/en-us/library/dd819476.aspx)與[關於 WS-Management Cmdlet](https://technet.microsoft.com/en-us/library/dd819481.aspx)，或在 Windows PowerShell 主控台中，輸入 "Get-Help wsman"。

如需詳細資訊，請參閱：
- [關於遠端常見問題集](https://technet.microsoft.com/en-us/library/dd315359.aspx)
- [Register-PSSessionConfiguration](https://go.microsoft.com/fwlink/?LinkId=821508)
- [Import-PSSession](https://go.microsoft.com/fwlink/?LinkId=821821)

如需遠端處理錯誤的說明，請參閱 [about_Remote_Troubleshooting](https://technet.microsoft.com/en-us/library/dd347642.aspx)。

## <a name="see-also"></a>另請參閱
- [about_Remote](https://technet.microsoft.com/en-us/library/9b4a5c87-9162-4adf-bdfe-fbc80b9b8970)
- [about_Remote_FAQ](https://technet.microsoft.com/en-us/library/e23702fd-9415-4a98-9975-390a4d3adc42)
- [about_Remote_Requirements](https://technet.microsoft.com/en-us/library/da213949-134c-4741-b307-81f4492ba1bd)
- [about_Remote_Troubleshooting](https://technet.microsoft.com/en-us/library/2f890148-8578-49ed-85ea-79a489dd6317)
- [about_PSSessions](https://technet.microsoft.com/en-us/library/7a9b4e0e-fa1b-47b0-92f6-6e2995d70acb)
- [about_WS-Management_Cmdlets](https://technet.microsoft.com/en-us/library/6ed3370a-ea10-45a5-9493-696aeace27ed)
- [Invoke-Command](https://go.microsoft.com/fwlink/?LinkId=821493)
- [Import-PSSession](https://go.microsoft.com/fwlink/?LinkId=821821)
- [New-PSSession](https://go.microsoft.com/fwlink/?LinkId=821498)
- [Register-PSSessionConfiguration](https://go.microsoft.com/fwlink/?LinkId=821508)
- [WSMan 提供者](https://technet.microsoft.com/en-us/library/66fe1241-e08f-49ca-832f-a84c33ca8735)
