---
title: 以指令碼工作偵測空的一般檔案 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- flat files
- Script task [Integration Services], empty flat files
- SSIS Script task, empty flat files
- Script task [Integration Services], examples
ms.assetid: 1b4defb8-886a-483d-8056-d1b91d37bc90
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 379b11bd18752ad648fc5f24d11d9ed5bfb63e14
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596774"
---
# <a name="detecting-an-empty-flat-file-with-the-script-task"></a><span data-ttu-id="11c12-102">以指令碼工作偵測空的一般檔案</span><span class="sxs-lookup"><span data-stu-id="11c12-102">Detecting an Empty Flat File with the Script Task</span></span>
  <span data-ttu-id="11c12-103">一般檔案來源不會在嘗試處理一般檔案之前，判斷它是否包含資料列。</span><span class="sxs-lookup"><span data-stu-id="11c12-103">The Flat File source does not determine whether a flat file contains rows of data before attempting to process it.</span></span> <span data-ttu-id="11c12-104">您可能會想要略過不包含任何資料列的檔案，藉以改善封裝的效率，尤其是逐一查看許多一般檔案的封裝。</span><span class="sxs-lookup"><span data-stu-id="11c12-104">You may want to improve the efficiency of a package, especially of a package that iterates over numerous flat files, by skipping files that do not contain any rows of data.</span></span> <span data-ttu-id="11c12-105">指令碼工作可以在封裝開始處理資料流程之前，尋找空白的一般檔案。</span><span class="sxs-lookup"><span data-stu-id="11c12-105">The Script task can look for an empty flat file before the package begins to process the data flow.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="11c12-106">如果您想要建立可更輕鬆地在多個封裝之間重複使用的工作，請考慮使用此指令碼工作範例中的程式碼做為自訂工作的起點。</span><span class="sxs-lookup"><span data-stu-id="11c12-106">If you want to create a task that you can more easily reuse across multiple packages, consider using the code in this Script task sample as the starting point for a custom task.</span></span> <span data-ttu-id="11c12-107">如需詳細資訊，請參閱 [開發自訂工作](../extending-packages-custom-objects/task/developing-a-custom-task.md)。</span><span class="sxs-lookup"><span data-stu-id="11c12-107">For more information, see [Developing a Custom Task](../extending-packages-custom-objects/task/developing-a-custom-task.md).</span></span>  
  
## <a name="description"></a><span data-ttu-id="11c12-108">描述</span><span class="sxs-lookup"><span data-stu-id="11c12-108">Description</span></span>  
 <span data-ttu-id="11c12-109">下列範例會使用 `System.IO` 命名空間的方法來測試一般檔案連接管理員中指定的一般檔案，以便判斷此檔案是否空白，或者它是否僅包含預期的非資料列，例如資料行標頭或空白的行。</span><span class="sxs-lookup"><span data-stu-id="11c12-109">The following example uses methods from the `System.IO` namespace to test the flat file specified in a Flat File connection manager to determine whether the file is empty, or whether it contains only expected non-data rows such as column headers or an empty line.</span></span> <span data-ttu-id="11c12-110">此指令碼會先檢查檔案的大小。如果大小為零個位元組，表示檔案是空白的。</span><span class="sxs-lookup"><span data-stu-id="11c12-110">The script checks the size of the file first; if the size is zero bytes, the file is empty.</span></span> <span data-ttu-id="11c12-111">如果檔案大小大於零，此指令碼就會從檔案中讀取各行，直到沒有其他行為止，或者直到行數超過預期的非資料列數目為止。</span><span class="sxs-lookup"><span data-stu-id="11c12-111">If the file size is greater than zero, the script reads lines from the file until there are no more lines, or until the number of lines exceeds the expected number of non-data rows.</span></span> <span data-ttu-id="11c12-112">如果檔案中的行數小於或等於預期的非資料列數目，此檔案就會被視為空白。</span><span class="sxs-lookup"><span data-stu-id="11c12-112">If the number of lines in the file is less than or equal to the expected number of non-data rows, then the file is considered empty.</span></span> <span data-ttu-id="11c12-113">結果會以布林值的形式傳入使用者變數中，而這個變數的值可用於在封裝的控制流程中分支。</span><span class="sxs-lookup"><span data-stu-id="11c12-113">The result is returned as a Boolean value in a user variable, the value of which can be used for branching in the package's control flow.</span></span> <span data-ttu-id="11c12-114">此 `FireInformation` 方法也會在**Output** [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA) 的 [輸出] 視窗中顯示結果。</span><span class="sxs-lookup"><span data-stu-id="11c12-114">The `FireInformation` method also displays the result in the **Output** window of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA).</span></span>  
  
#### <a name="to-configure-this-script-task-example"></a><span data-ttu-id="11c12-115">設定此指令碼工作範例</span><span class="sxs-lookup"><span data-stu-id="11c12-115">To configure this Script Task example</span></span>  
  
1.  <span data-ttu-id="11c12-116">建立並設定名為的一般檔案連線管理員 `EmptyFlatFileTest` 。</span><span class="sxs-lookup"><span data-stu-id="11c12-116">Create and configure a flat file connection manager named `EmptyFlatFileTest`.</span></span>  
  
2.  <span data-ttu-id="11c12-117">建立名為 `FFNonDataRows` 的整數變數並將其值設定為一般檔案中預期的非資料列數目。</span><span class="sxs-lookup"><span data-stu-id="11c12-117">Create an integer variable named `FFNonDataRows` and set its value to the number of non-data rows expected in the flat file.</span></span>  
  
3.  <span data-ttu-id="11c12-118">建立名為 `FFIsEmpty` 的布林值變數。</span><span class="sxs-lookup"><span data-stu-id="11c12-118">Create a Boolean variable named `FFIsEmpty`.</span></span>  
  
4.  <span data-ttu-id="11c12-119">將 `FFNonDataRows` 變數新增至指令碼工作的 **ReadOnlyVariables** 屬性。</span><span class="sxs-lookup"><span data-stu-id="11c12-119">Add the `FFNonDataRows` variable to the Script task's **ReadOnlyVariables** property.</span></span>  
  
5.  <span data-ttu-id="11c12-120">將 `FFIsEmpty` 變數新增至指令碼工作的 **ReadWriteVariables** 屬性。</span><span class="sxs-lookup"><span data-stu-id="11c12-120">Add the `FFIsEmpty` variable to the Script task's **ReadWriteVariables** property.</span></span>  
  
6.  <span data-ttu-id="11c12-121">在您的程式碼中，匯入 `System.IO` 命名空間。</span><span class="sxs-lookup"><span data-stu-id="11c12-121">In your code, import the `System.IO` namespace.</span></span>  
  
 <span data-ttu-id="11c12-122">如果您要使用 Foreach 檔案列舉值 (而非使用單一一般檔案連接管理員) 來逐一查看檔案，就必須修改下列範例程式碼，以便從儲存列舉值的變數 (而非從連接管理員) 中取得檔案名稱和路徑。</span><span class="sxs-lookup"><span data-stu-id="11c12-122">If you are iterating over files with a Foreach File enumerator, instead of using a single Flat File connection manager, you will need to modify the sample code below to obtain the file name and path from the variable in which the enumerated value is stored instead of from the connection manager.</span></span>  
  
### <a name="code"></a><span data-ttu-id="11c12-123">程式碼</span><span class="sxs-lookup"><span data-stu-id="11c12-123">Code</span></span>  
  
```vb  
Public Sub Main()  
  
  Dim nonDataRows As Integer = _  
      DirectCast(Dts.Variables("FFNonDataRows").Value, Integer)  
  Dim ffConnection As String = _  
      DirectCast(Dts.Connections("EmptyFlatFileTest").AcquireConnection(Nothing), _  
      String)  
  Dim flatFileInfo As New FileInfo(ffConnection)  
  ' If file size is 0 bytes, flat file does not contain data.  
  Dim fileSize As Long = flatFileInfo.Length  
  If fileSize > 0 Then  
    Dim lineCount As Integer = 0  
    Dim line As String  
    Dim fsFlatFile As New StreamReader(ffConnection)  
    Do Until fsFlatFile.EndOfStream  
      line = fsFlatFile.ReadLine  
      lineCount += 1  
      ' If line count > expected number of non-data rows,  
      '  flat file contains data (default value).  
      If lineCount > nonDataRows Then  
        Exit Do  
      End If  
      ' If line count <= expected number of non-data rows,  
      '  flat file does not contain data.  
      If lineCount <= nonDataRows Then  
        Dts.Variables("FFIsEmpty").Value = True  
      End If  
    Loop  
  Else  
    Dts.Variables("FFIsEmpty").Value = True  
  End If  
  
  Dim fireAgain As Boolean = False  
  Dts.Events.FireInformation(0, "Script Task", _  
      String.Format("{0}: {1}", ffConnection, _  
      Dts.Variables("FFIsEmpty").Value.ToString), _  
      String.Empty, 0, fireAgain)  
  
  Dts.TaskResult = ScriptResults.Success  
  
End Sub  
```  
  
```csharp  
public void Main()  
        {  
  
            int nonDataRows = (int)(Dts.Variables["FFNonDataRows"].Value);  
            string ffConnection = (string)(Dts.Connections["EmptyFlatFileTest"].AcquireConnection(null) as String);  
            FileInfo flatFileInfo = new FileInfo(ffConnection);  
            // If file size is 0 bytes, flat file does not contain data.  
            long fileSize = flatFileInfo.Length;  
            if (fileSize > 0)  
            {  
  
                int lineCount = 0;  
                string line;  
                StreamReader fsFlatFile = new StreamReader(ffConnection);  
                while (!(fsFlatFile.EndOfStream))  
                {  
                    Console.WriteLine (fsFlatFile.ReadLine());  
                    lineCount += 1;  
                    // If line count > expected number of non-data rows,  
                    //  flat file contains data (default value).  
                    if (lineCount > nonDataRows)  
                    {  
                        break;  
                    }  
                    // If line count <= expected number of non-data rows,  
                    //  flat file does not contain data.  
                    if (lineCount <= nonDataRows)  
                    {  
                        Dts.Variables["FFIsEmpty"].Value = true;  
                    }  
                }  
            }  
            else  
            {  
                Dts.Variables["FFIsEmpty"].Value = true;  
            }  
  
            bool fireAgain = false;  
            Dts.Events.FireInformation(0, "Script Task", String.Format("{0}: {1}", ffConnection, Dts.Variables["FFIsEmpty"].Value), String.Empty, 0, ref fireAgain);  
  
            Dts.TaskResult = (int)ScriptResults.Success;  
  
        }  
```  
  
<span data-ttu-id="11c12-124">![Integration Services 圖示 (小型) ](../media/dts-16.gif "Integration Services 圖示 (小)")會**保持最**新狀態 Integration Services  </span><span class="sxs-lookup"><span data-stu-id="11c12-124">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="11c12-125">若要取得 Microsoft 的最新下載、文件、範例和影片以及社群中的精選解決方案，請瀏覽 MSDN 上的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 頁面：</span><span class="sxs-lookup"><span data-stu-id="11c12-125">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="11c12-126">瀏覽 MSDN 上的 Integration Services 頁面</span><span class="sxs-lookup"><span data-stu-id="11c12-126">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="11c12-127">若要得到這些更新的自動通知，請訂閱該頁面上所提供的 RSS 摘要。</span><span class="sxs-lookup"><span data-stu-id="11c12-127">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11c12-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="11c12-128">See Also</span></span>  
 [<span data-ttu-id="11c12-129">指令碼工作範例</span><span class="sxs-lookup"><span data-stu-id="11c12-129">Script Task Examples</span></span>](../extending-packages-scripting-task-examples/script-task-examples.md)  
  
  
