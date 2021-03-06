---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "使用變數儲存物件"
ms.assetid: b1688d73-c173-491e-9ba6-6d0c1cc852de
ms.openlocfilehash: 9a95d421fa2686608a565987c16fecc41c3c6d20
ms.sourcegitcommit: f069ff0689006fece768f178c10e3e3eeaee09f0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2017
---
# <a name="using-variables-to-store-objects"></a>使用變數儲存物件
PowerShell 可以搭配物件來使用。 PowerShell 可讓您建立基本上為具名物件的變數，以保留輸出供之後使用。 如果您習慣使用其他殼層中的變數，請記得 PowerShell 變數是物件，而非文字。

變數一律會指定起始字元 $，而且可以在其名稱中包括任何英數字元或底線。

### <a name="creating-a-variable"></a>建立變數
您可以輸入有效的變數名稱來建立變數︰

```
PS> $loc
PS>
```

這不會傳回任何結果，因為 **$loc** 沒有值。 您可以在相同的步驟中建立變數並指派其值。 PowerShell 只會建立不存在的變數；否則，它會將指定的值指派給現有變數。 若要將您的目前位置儲存在變數 **$loc** 中，請輸入：

```
$loc = Get-Location
```

輸入這個命令時未顯示任何輸出，因為輸出會傳送至 $loc。 在 PowerShell 中，未導向的資料一律會傳送至螢幕，因而導致顯示輸出。 輸入 $loc 將顯示目前的位置：

```
PS> $loc

Path
----
C:\temp
```

您可以使用 **Get-Member** 顯示變數內容的相關資訊。 將 $loc 傳送到 Get-Member 將顯示它是 **PathInfo** 物件，就像 Get-Location 的輸出一樣：

```
PS> $loc | Get-Member -MemberType Property

   TypeName: System.Management.Automation.PathInfo

Name         MemberType Definition
----         ---------- ----------
Drive        Property   System.Management.Automation.PSDriveInfo Drive {get;}
Path         Property   System.String Path {get;}
Provider     Property   System.Management.Automation.ProviderInfo Provider {...
ProviderPath Property   System.String ProviderPath {get;}
```

### <a name="manipulating-variables"></a>操作變數
PowerShell 提供數個命令來操作變數。 您可以查看可讀取形式的完整清單，方法是輸入︰

```
Get-Command -Noun Variable | Format-Table -Property Name,Definition -AutoSize -Wrap
```

除了您在目前 PowerShell 工作階段中建立的變數之外，還有數個系統定義的變數。 您可以使用 **Remove-Variable** Cmdlet 來清除所有不受 PowerShell 控制的變數。 輸入下列命令以清除所有變數：

```
Remove-Variable -Name * -Force -ErrorAction SilentlyContinue
```

這將產生您在下面看到的確認提示。

```
Confirm
Are you sure you want to perform this action?
Performing operation "Remove Variable" on Target "Name: Error".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):A
```

如果之後執行 **Get-Variable** Cmdlet，就會看到其餘的 PowerShell 變數。 因為也有 PowerShell 驅動的變數，所以也可以輸入下列命令來顯示所有 PowerShell 變數︰

```
Get-ChildItem variable:
```

### <a name="using-cmdexe-variables"></a>使用 Cmd.exe 變數
雖然 PowerShell 不是 Cmd.exe，但是會在命令殼層環境中執行，而且可以在 Windows 的任何環境中使用相同的變數。 這些變數是透過名為 **env** 的磁碟機公開： 您可以檢視這些變數，方法是輸入︰

```
Get-ChildItem env:
```

雖然標準變數 Cmdlet 未設計成使用 **env:** 變數，但是您仍然可以指定 **env:** 前置詞來使用它們。 例如，若要查看作業系統根目錄，您可以輸入下列命令，以便從 PowerShell 使用命令殼層 **%SystemRoot%** 變數︰

```
PS> $env:SystemRoot
C:\WINDOWS
```

您也可以從 PowerShell 建立和修改環境變數。 從 Windows PowerShell 存取的環境變數符合 Windows 中其他位置之環境變數的一般規則。

