---
title: 以指令碼工作尋找安裝的印表機 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- System.Drawing.Printing namespace
- printers [Integration Services]
- SSIS Script task, printers
- locating printers
- Printing namespace
- Script task [Integration Services], examples
- finding printers [SQL Server]
- Script task [Integration Services], printers
ms.assetid: 50a55014-e2c3-4ecd-84e1-3e877c55a260
author: chugugrace
ms.author: chugu
ms.openlocfilehash: cc4bc06879a55d4d07afca1011cc479dd7e7903a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705314"
---
# <a name="finding-installed-printers-with-the-script-task"></a><span data-ttu-id="ef820-102">以指令碼工作尋找安裝的印表機</span><span class="sxs-lookup"><span data-stu-id="ef820-102">Finding Installed Printers with the Script Task</span></span>
  <span data-ttu-id="ef820-103">由 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 封裝轉換的資料通常有列印的報表，做為其最終的目的地。</span><span class="sxs-lookup"><span data-stu-id="ef820-103">The data that is transformed by [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages often has a printed report as its final destination.</span></span> <span data-ttu-id="ef820-104">`System.Drawing.Printing`中的命名空間 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 提供使用印表機的類別。</span><span class="sxs-lookup"><span data-stu-id="ef820-104">The `System.Drawing.Printing` namespace in the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] provides classes for working with printers.</span></span>

> [!NOTE]
>  <span data-ttu-id="ef820-105">如果您想要建立可更輕鬆地在多個封裝之間重複使用的工作，請考慮使用此指令碼工作範例中的程式碼做為自訂工作的起點。</span><span class="sxs-lookup"><span data-stu-id="ef820-105">If you want to create a task that you can more easily reuse across multiple packages, consider using the code in this Script task sample as the starting point for a custom task.</span></span> <span data-ttu-id="ef820-106">如需詳細資訊，請參閱 [開發自訂工作](../extending-packages-custom-objects/task/developing-a-custom-task.md)。</span><span class="sxs-lookup"><span data-stu-id="ef820-106">For more information, see [Developing a Custom Task](../extending-packages-custom-objects/task/developing-a-custom-task.md).</span></span>

## <a name="description"></a><span data-ttu-id="ef820-107">描述</span><span class="sxs-lookup"><span data-stu-id="ef820-107">Description</span></span>
 <span data-ttu-id="ef820-108">下列範例找到安裝在伺服器上支援 Legal Size 紙張 (用於美國) 的印表機。</span><span class="sxs-lookup"><span data-stu-id="ef820-108">The following example locates printers installed on the server that support legal size paper (as used in the United States).</span></span> <span data-ttu-id="ef820-109">檢查支援紙張大小的程式碼是封裝在私用函數中。</span><span class="sxs-lookup"><span data-stu-id="ef820-109">The code to check supported paper sizes is encapsulated in a private function.</span></span> <span data-ttu-id="ef820-110">為了讓您在指令碼檢查每台印表機的設定時，追蹤指令碼的進度，指令碼使用 <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Log%2A> 方法，來針對使用 Legal Size 紙張的印表機引發參考用訊息，並為沒有 Legal Size 紙張的印表機引發警告。</span><span class="sxs-lookup"><span data-stu-id="ef820-110">To enable you to track the progress of the script as it checks the settings for each printer, the script uses the <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Log%2A> method to raise an informational message for printers with legal size paper, and to raise a warning for printers without legal size paper.</span></span> <span data-ttu-id="ef820-111">當您在設計師中執行套件時，這些訊息會出現在   Tools for Applications (VSTA) IDE 的 [輸出][!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 視窗中。</span><span class="sxs-lookup"><span data-stu-id="ef820-111">These messages appear in the **Output** window of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA) IDE when you run the package in the designer.</span></span>

#### <a name="to-configure-this-script-task-example"></a><span data-ttu-id="ef820-112">設定此指令碼工作範例</span><span class="sxs-lookup"><span data-stu-id="ef820-112">To configure this Script Task example</span></span>

1.  <span data-ttu-id="ef820-113">建立名為 `PrinterList` 且類型為 `Object` 的變數。</span><span class="sxs-lookup"><span data-stu-id="ef820-113">Create the variable named `PrinterList` with type `Object`.</span></span>

2.  <span data-ttu-id="ef820-114">在 [指令碼工作編輯器] 的 [指令碼] 頁面上，將此變數加入 ReadWriteVariables 屬性。</span><span class="sxs-lookup"><span data-stu-id="ef820-114">On the **Script** page of the **Script Task Editor**, add this variable to the ReadWriteVariables property.</span></span>

3.  <span data-ttu-id="ef820-115">在指令碼專案中，加入 **System.Drawing** 命名空間的參考。</span><span class="sxs-lookup"><span data-stu-id="ef820-115">In the script project, add a reference to the **System.Drawing** namespace.</span></span>

4.  <span data-ttu-id="ef820-116">在您的程式碼中，使用 `Imports` 語句來匯入**system.web**和 `System.Drawing.Printing` 命名空間。</span><span class="sxs-lookup"><span data-stu-id="ef820-116">In your code, use `Imports` statements to import the **System.Collections** and the `System.Drawing.Printing` namespaces.</span></span>

### <a name="code"></a><span data-ttu-id="ef820-117">程式碼</span><span class="sxs-lookup"><span data-stu-id="ef820-117">Code</span></span>

```vb
Public Sub Main()

    Dim printerName As String
    Dim currentPrinter As New PrinterSettings
    Dim size As PaperSize

    Dim printerList As New ArrayList
    For Each printerName In PrinterSettings.InstalledPrinters
        currentPrinter.PrinterName = printerName
        If PrinterHasLegalPaper(currentPrinter) Then
            printerList.Add(printerName)
            Dts.Events.FireInformation(0, "Example", _
                "Printer " & printerName & " has legal paper.", _
                String.Empty, 0, False)
        Else
            Dts.Events.FireWarning(0, "Example", _
                "Printer " & printerName & " DOES NOT have legal paper.", _
                String.Empty, 0)
        End If
    Next

    Dts.Variables("PrinterList").Value = printerList

    Dts.TaskResult = ScriptResults.Success

End Sub

Private Function PrinterHasLegalPaper( _
    ByVal thisPrinter As PrinterSettings) As Boolean

    Dim size As PaperSize
    Dim hasLegal As Boolean = False

    For Each size In thisPrinter.PaperSizes
        If size.Kind = PaperKind.Legal Then
            hasLegal = True
        End If
    Next

    Return hasLegal

End Function
```

```csharp
public void Main()
        {

            PrinterSettings currentPrinter = new PrinterSettings();
            PaperSize size;
            Boolean Flag = false;

            ArrayList printerList = new ArrayList();
            foreach (string printerName in PrinterSettings.InstalledPrinters)
            {
                currentPrinter.PrinterName = printerName;
                if (PrinterHasLegalPaper(currentPrinter))
                {
                    printerList.Add(printerName);
                    Dts.Events.FireInformation(0, "Example", "Printer " + printerName + " has legal paper.", String.Empty, 0, ref Flag);
                }
                else
                {
                    Dts.Events.FireWarning(0, "Example", "Printer " + printerName + " DOES NOT have legal paper.", String.Empty, 0);
                }
            }

            Dts.Variables["PrinterList"].Value = printerList;

            Dts.TaskResult = (int)ScriptResults.Success;

        }

        private bool PrinterHasLegalPaper(PrinterSettings thisPrinter)
        {

            bool hasLegal = false;

            foreach (PaperSize size in thisPrinter.PaperSizes)
            {
                if (size.Kind == PaperKind.Legal)
                {
                    hasLegal = true;
                }
            }

            return hasLegal;

        }
```

<span data-ttu-id="ef820-118">![Integration Services 圖示 (小型) ](../media/dts-16.gif "Integration Services 圖示 (小)")會**保持最**新狀態 Integration Services  </span><span class="sxs-lookup"><span data-stu-id="ef820-118">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="ef820-119">若要取得 Microsoft 的最新下載、文件、範例和影片以及社群中的精選解決方案，請瀏覽 MSDN 上的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 頁面：</span><span class="sxs-lookup"><span data-stu-id="ef820-119">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="ef820-120">瀏覽 MSDN 上的 Integration Services 頁面</span><span class="sxs-lookup"><span data-stu-id="ef820-120">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="ef820-121">若要得到這些更新的自動通知，請訂閱該頁面上所提供的 RSS 摘要。</span><span class="sxs-lookup"><span data-stu-id="ef820-121">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>

## <a name="see-also"></a><span data-ttu-id="ef820-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ef820-122">See Also</span></span>
 [<span data-ttu-id="ef820-123">指令碼工作範例</span><span class="sxs-lookup"><span data-stu-id="ef820-123">Script Task Examples</span></span>](../extending-packages-scripting-task-examples/script-task-examples.md)


