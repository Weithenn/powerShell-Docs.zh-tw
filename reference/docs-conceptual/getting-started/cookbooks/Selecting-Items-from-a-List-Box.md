---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "從清單方塊選取項目"
ms.assetid: 327c7cc5-21d0-4ace-b151-aa1491d1d3c2
ms.openlocfilehash: 39a5375b7f00c4b8332b28bf6ead011c4b21883e
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2017
---
# <a name="selecting-items-from-a-list-box"></a><span data-ttu-id="3fea9-103">從清單方塊選取項目</span><span class="sxs-lookup"><span data-stu-id="3fea9-103">Selecting Items from a List Box</span></span>
<span data-ttu-id="3fea9-104">使用 Windows PowerShell 3.0 和更新的版本，來建立讓使用者從清單方塊控制項選取項目的對話方塊。</span><span class="sxs-lookup"><span data-stu-id="3fea9-104">Use Windows PowerShell 3.0 and later releases to create a dialog box that lets users select items from a list box control.</span></span>

## <a name="create-a-list-box-control-and-select-items-from-it"></a><span data-ttu-id="3fea9-105">建立清單方塊控制項，並從其中選取項目。</span><span class="sxs-lookup"><span data-stu-id="3fea9-105">Create a list box control, and select items from it</span></span>
<span data-ttu-id="3fea9-106">將下列程式碼複製並貼上到 Windows PowerShell ISE，然後將它儲存為 Windows PowerShell 指令碼 (.ps1)。</span><span class="sxs-lookup"><span data-stu-id="3fea9-106">Copy and then paste the following into Windows PowerShell ISE, and then save it as a Windows PowerShell script (.ps1).</span></span>

```
Add-Type -AssemblyName System.Windows.Forms
Add-Type -AssemblyName System.Drawing

$form = New-Object System.Windows.Forms.Form 
$form.Text = "Select a Computer"
$form.Size = New-Object System.Drawing.Size(300,200) 
$form.StartPosition = "CenterScreen"

$OKButton = New-Object System.Windows.Forms.Button
$OKButton.Location = New-Object System.Drawing.Point(75,120)
$OKButton.Size = New-Object System.Drawing.Size(75,23)
$OKButton.Text = "OK"
$OKButton.DialogResult = [System.Windows.Forms.DialogResult]::OK
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)

$CancelButton = New-Object System.Windows.Forms.Button
$CancelButton.Location = New-Object System.Drawing.Point(150,120)
$CancelButton.Size = New-Object System.Drawing.Size(75,23)
$CancelButton.Text = "Cancel"
$CancelButton.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)

$label = New-Object System.Windows.Forms.Label
$label.Location = New-Object System.Drawing.Point(10,20) 
$label.Size = New-Object System.Drawing.Size(280,20) 
$label.Text = "Please select a computer:"
$form.Controls.Add($label) 

$listBox = New-Object System.Windows.Forms.ListBox 
$listBox.Location = New-Object System.Drawing.Point(10,40) 
$listBox.Size = New-Object System.Drawing.Size(260,20) 
$listBox.Height = 80

[void] $listBox.Items.Add("atl-dc-001")
[void] $listBox.Items.Add("atl-dc-002")
[void] $listBox.Items.Add("atl-dc-003")
[void] $listBox.Items.Add("atl-dc-004")
[void] $listBox.Items.Add("atl-dc-005")
[void] $listBox.Items.Add("atl-dc-006")
[void] $listBox.Items.Add("atl-dc-007")

$form.Controls.Add($listBox) 

$form.Topmost = $True

$result = $form.ShowDialog()

if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $x = $listBox.SelectedItem
    $x
}
```

<span data-ttu-id="3fea9-107">指令碼一開始會載入兩個 .NET Framework 類別：**System.Drawing** 和 **System.Windows.Forms**。</span><span class="sxs-lookup"><span data-stu-id="3fea9-107">The script begins by loading two .NET Framework classes: **System.Drawing** and **System.Windows.Forms**.</span></span> <span data-ttu-id="3fea9-108">接著，您會啟動新的 .NET Framework 類別 **System.Windows.Forms.Form** 的執行個體，這樣可以提供空白表單或視窗讓您可以開始新增控制項。</span><span class="sxs-lookup"><span data-stu-id="3fea9-108">You then start a new instance of the .NET Framework class **System.Windows.Forms.Form**; that provides a blank form or window to which you can start adding controls.</span></span>

```
Add-Type -AssemblyName System.Windows.Forms
Add-Type -AssemblyName System.Drawing
```

<span data-ttu-id="3fea9-109">建立 Form 類別的執行個體之後，指派值給此類別的三個屬性。</span><span class="sxs-lookup"><span data-stu-id="3fea9-109">After you create an instance of the Form class, assign values to three properties of this class.</span></span>

-   <span data-ttu-id="3fea9-110">**Text**。</span><span class="sxs-lookup"><span data-stu-id="3fea9-110">**Text.**</span></span> <span data-ttu-id="3fea9-111">這會成為視窗的標題。</span><span class="sxs-lookup"><span data-stu-id="3fea9-111">This becomes the title of the window.</span></span>

-   <span data-ttu-id="3fea9-112">**Size**。</span><span class="sxs-lookup"><span data-stu-id="3fea9-112">**Size.**</span></span> <span data-ttu-id="3fea9-113">這是表單的大小，單位為像素。</span><span class="sxs-lookup"><span data-stu-id="3fea9-113">This is the size of the form, in pixels.</span></span> <span data-ttu-id="3fea9-114">上述指令碼會建立 300 像素寬、200 像素高的表單。</span><span class="sxs-lookup"><span data-stu-id="3fea9-114">The preceding script creates a form that’s 300 pixels wide by 200 pixels tall.</span></span>

-   <span data-ttu-id="3fea9-115">**StartingPosition**。</span><span class="sxs-lookup"><span data-stu-id="3fea9-115">**StartingPosition.**</span></span> <span data-ttu-id="3fea9-116">此選擇性屬性在上述指令碼中是設定為 **CenterScreen**。</span><span class="sxs-lookup"><span data-stu-id="3fea9-116">This optional property is set to **CenterScreen** in the preceding script.</span></span> <span data-ttu-id="3fea9-117">若未新增此屬性，Windows 會在表單開啟時選取一個位置。</span><span class="sxs-lookup"><span data-stu-id="3fea9-117">If you don’t add this property, Windows selects a location when the form is opened.</span></span> <span data-ttu-id="3fea9-118">透過將 **StartingPosition** 設定為 **CenterScreen**，您可以在每次載入表單時，將表單自動顯示在畫面中間。</span><span class="sxs-lookup"><span data-stu-id="3fea9-118">By setting the **StartingPosition** to **CenterScreen**, you’re automatically displaying the form in the middle of the screen each time it loads.</span></span>

```
$form.Text = "Select a Computer"
$form.Size = New-Object System.Drawing.Size(300,200) 
$form.StartPosition = "CenterScreen"
```

<span data-ttu-id="3fea9-119">接著，為您的表單建立 **[確定]** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="3fea9-119">Next, create an **OK** button for your form.</span></span> <span data-ttu-id="3fea9-120">指定 **[確定]** 按鈕的大小與行為。</span><span class="sxs-lookup"><span data-stu-id="3fea9-120">Specify the size and behavior of the **OK** button.</span></span> <span data-ttu-id="3fea9-121">在此範例中，按鈕位置是距離表單上邊緣 120 像素，並距離左邊緣 75 像素。</span><span class="sxs-lookup"><span data-stu-id="3fea9-121">In this example, the button position is 120 pixels from the form’s top edge, and 75 pixels from the left edge.</span></span> <span data-ttu-id="3fea9-122">按鈕高度是 23 像素，而按鈕寬度是 75 像素。</span><span class="sxs-lookup"><span data-stu-id="3fea9-122">The button height is 23 pixels, while the button length is 75 pixels.</span></span> <span data-ttu-id="3fea9-123">指令碼會使用預先定義的 Windows Forms 類型來決定按鈕行為。</span><span class="sxs-lookup"><span data-stu-id="3fea9-123">The script uses predefined Windows Forms types to determine the button behaviors.</span></span>

```
$OKButton = New-Object System.Windows.Forms.Button
$OKButton.Location = New-Object System.Drawing.Point(75,120)
$OKButton.Size = New-Object System.Drawing.Size(75,23)
$OKButton.Text = "OK"
$OKButton.DialogResult = [System.Windows.Forms.DialogResult]::OK
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)
```

<span data-ttu-id="3fea9-124">同樣地，您也會建立 **[取消]** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="3fea9-124">Similarly, you create a **Cancel** button.</span></span> <span data-ttu-id="3fea9-125">**[取消]** 按鈕距離上邊緣 120 像素，但距離視窗左邊緣 150 像素。</span><span class="sxs-lookup"><span data-stu-id="3fea9-125">The **Cancel** button is 120 pixels from the top, but 150 pixels from the left edge of the window.</span></span>

```
$CancelButton = New-Object System.Windows.Forms.Button
$CancelButton.Location = New-Object System.Drawing.Point(150,120)
$CancelButton.Size = New-Object System.Drawing.Size(75,23)
$CancelButton.Text = "Cancel"
$CancelButton.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)
```

<span data-ttu-id="3fea9-126">接下來，在您的視窗上提供標籤文字，以描述您希望使用者提供的資訊。</span><span class="sxs-lookup"><span data-stu-id="3fea9-126">Next, provide label text on your window that describes the information you want users to provide.</span></span> <span data-ttu-id="3fea9-127">在此案例中，您希望使用者選取一部電腦。</span><span class="sxs-lookup"><span data-stu-id="3fea9-127">In this case, you want users to select a computer.</span></span>

```
$label = New-Object System.Windows.Forms.Label
$label.Location = New-Object System.Drawing.Point(10,20) 
$label.Size = New-Object System.Drawing.Size(280,20) 
$label.Text = "Please select a computer:"
$form.Controls.Add($label)
```

<span data-ttu-id="3fea9-128">新增控制項 (在此案例中為清單方塊)，讓使用者提供您在標籤文字中描述的資訊。</span><span class="sxs-lookup"><span data-stu-id="3fea9-128">Add the control (in this case, a list box) that lets users provide the information you’ve described in your label text.</span></span> <span data-ttu-id="3fea9-129">除了清單方塊外，還有許多其他您可以套用的控制項；如需更多控制項，請參閱 MSDN 上的 [System.Windows.Forms Namespace (System.Windows.Forms 命名空間)](http://msdn.microsoft.com/library/k50ex0x9(v=vs.110).aspx)。</span><span class="sxs-lookup"><span data-stu-id="3fea9-129">There are many other controls you can apply besides list boxes; for more controls, see [System.Windows.Forms Namespace](http://msdn.microsoft.com/library/k50ex0x9(v=vs.110).aspx) on MSDN.</span></span>

```
$listBox = New-Object System.Windows.Forms.ListBox 
$listBox.Location = New-Object System.Drawing.Point(10,40) 
$listBox.Size = New-Object System.Drawing.Size(260,20) 
$listBox.Height = 80
```

<span data-ttu-id="3fea9-130">在下一節中，您可以指定您希望清單方塊向使用者顯示的值。</span><span class="sxs-lookup"><span data-stu-id="3fea9-130">In the next section, you specify the values you want the list box to display to users.</span></span>

> [!NOTE]
> <span data-ttu-id="3fea9-131">此指令碼所建立的清單方塊只允許選取一個項目。</span><span class="sxs-lookup"><span data-stu-id="3fea9-131">The list box created by this script allows only one selection.</span></span> <span data-ttu-id="3fea9-132">若要建立允許多重選取的清單方塊，請指定值給 **SelectionMode** 屬性，如下所示：`$listBox.SelectionMode = "MultiExtended"`。</span><span class="sxs-lookup"><span data-stu-id="3fea9-132">To create a list box control that allows multiple selections, specify a value for the **SelectionMode** property, similarly to the following:  `$listBox.SelectionMode = "MultiExtended"`.</span></span> <span data-ttu-id="3fea9-133">如需詳細資訊，請參閱[多重選擇清單方塊](Multiple-selection-List-Boxes.md)。</span><span class="sxs-lookup"><span data-stu-id="3fea9-133">For more information, see [Multiple-selection List Boxes](Multiple-selection-List-Boxes.md).</span></span>

```
[void] $listBox.Items.Add("atl-dc-001")
[void] $listBox.Items.Add("atl-dc-002")
[void] $listBox.Items.Add("atl-dc-003")
[void] $listBox.Items.Add("atl-dc-004")
[void] $listBox.Items.Add("atl-dc-005")
[void] $listBox.Items.Add("atl-dc-006")
[void] $listBox.Items.Add("atl-dc-007")
```

<span data-ttu-id="3fea9-134">新增清單方塊控制項到您的表單，並指示 Windows 在開啟表單時，將它開啟在其他視窗與對話方塊之上。</span><span class="sxs-lookup"><span data-stu-id="3fea9-134">Add the list box control to your form, and instruct Windows to open the form atop other windows and dialog boxes when it’s opened.</span></span>

```
$form.Controls.Add($listBox) 
$form.Topmost = $True
```

<span data-ttu-id="3fea9-135">新增下面這行程式碼，以在 Windows 中顯示該表單。</span><span class="sxs-lookup"><span data-stu-id="3fea9-135">Add the following line of code to display the form in Windows.</span></span>

```
$result = $form.ShowDialog()
```

<span data-ttu-id="3fea9-136">最後，**If** 區塊內的程式碼會指示 Windows 當使用者在清單方塊中選取選項並按一下 **[確定]** 按鈕或按 **Enter** 鍵時要執行的表單動作。</span><span class="sxs-lookup"><span data-stu-id="3fea9-136">Finally, the code inside the **If** block instructs Windows what to do with the form after users select an option from the list box, and then click the **OK** button or press the **Enter** key.</span></span>

```
if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $x = $listBox.SelectedItem
    $x
}
```

## <a name="see-also"></a><span data-ttu-id="3fea9-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3fea9-137">See Also</span></span>
- [<span data-ttu-id="3fea9-138">Hey Scripting Guy：Why don’t these PowerShell GUI examples work?</span><span class="sxs-lookup"><span data-stu-id="3fea9-138">Hey Scripting Guy:  Why don’t these PowerShell GUI examples work?</span></span>](http://go.microsoft.com/fwlink/?LinkId=506644) (Hey Scripting Guy：PowerShell GUI 範例為什麼動不起來？)
- [<span data-ttu-id="3fea9-139">GitHub：Dave Wyatt's WinFormsExampleUpdates</span><span class="sxs-lookup"><span data-stu-id="3fea9-139">GitHub: Dave Wyatt's WinFormsExampleUpdates</span></span>](https://github.com/dlwyatt/WinFormsExampleUpdates) (GitHub：Dave Wyatt 的 WinFormsExampleUpdates)
- [<span data-ttu-id="3fea9-140">本週 Windows PowerShell 秘訣︰從清單方塊選取項目</span><span class="sxs-lookup"><span data-stu-id="3fea9-140">Windows PowerShell Tip of the Week:  Selecting Items from a List Box</span></span>](http://technet.microsoft.com/library/ff730949.aspx)
