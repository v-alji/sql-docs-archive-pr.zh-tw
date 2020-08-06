---
title: 在指令碼工作中使用變數 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- Foreach Loop containers
- Script task [Integration Services], variables
- scripts [Integration Services], variables
- Variables property
- Variable object
- SSIS Script task, variables
- variables [Integration Services], Script task
ms.assetid: 593b5961-4bfa-4ce1-9531-a251c34e89d3
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 2cd8fee5741c3d0e28e52c8712c3896428a05e8a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710745"
---
# <a name="using-variables-in-the-script-task"></a><span data-ttu-id="b60ce-102">在指令碼工作中使用變數</span><span class="sxs-lookup"><span data-stu-id="b60ce-102">Using Variables in the Script Task</span></span>
  <span data-ttu-id="b60ce-103">變數讓指令碼工作可以和封裝中的其他物件交換資料。</span><span class="sxs-lookup"><span data-stu-id="b60ce-103">Variables make it possible for the Script task to exchange data with other objects in the package.</span></span> <span data-ttu-id="b60ce-104">如需詳細資訊，請參閱 [Integration Services &#40;SSIS&#41; 變數](../../integration-services-ssis-variables.md)。</span><span class="sxs-lookup"><span data-stu-id="b60ce-104">For more information, see [Integration Services &#40;SSIS&#41; Variables](../../integration-services-ssis-variables.md).</span></span>  
  
 <span data-ttu-id="b60ce-105">指令碼工作使用 `Dts` 物件的 <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Variables%2A> 屬性，讀取和寫入封裝中的 <xref:Microsoft.SqlServer.Dts.Runtime.Variable> 物件。</span><span class="sxs-lookup"><span data-stu-id="b60ce-105">The Script task uses the <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Variables%2A> property of the `Dts` object to read from and write to <xref:Microsoft.SqlServer.Dts.Runtime.Variable> objects in the package.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b60ce-106"><xref:Microsoft.SqlServer.Dts.Runtime.Variable.Value%2A> 類別的 <xref:Microsoft.SqlServer.Dts.Runtime.Variable> 屬性其類別為 `Object`。</span><span class="sxs-lookup"><span data-stu-id="b60ce-106">The <xref:Microsoft.SqlServer.Dts.Runtime.Variable.Value%2A> property of the <xref:Microsoft.SqlServer.Dts.Runtime.Variable> class is of type `Object`.</span></span> <span data-ttu-id="b60ce-107">因為指令碼工作已啟用 `Option Strict`，所以您必須在使用它之前將 <xref:Microsoft.SqlServer.Dts.Runtime.Variable.Value%2A> 屬性轉換為適當的類型。</span><span class="sxs-lookup"><span data-stu-id="b60ce-107">Because the Script task has `Option Strict` enabled, you must cast the <xref:Microsoft.SqlServer.Dts.Runtime.Variable.Value%2A> property to the appropriate type before you can use it.</span></span>  
  
 <span data-ttu-id="b60ce-108">您將現有的變數新增至 [指令碼工作編輯器] 的 <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptTask.ReadOnlyVariables%2A> 與 <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptTask.ReadWriteVariables%2A> 清單中，讓它們可供自訂指令碼使用。</span><span class="sxs-lookup"><span data-stu-id="b60ce-108">You add existing variables to the <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptTask.ReadOnlyVariables%2A> and <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptTask.ReadWriteVariables%2A> lists in the **Script Task Editor** to make them available to the custom script.</span></span> <span data-ttu-id="b60ce-109">請記住變數名稱有區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="b60ce-109">Keep in mind that variable names are case-sensitive.</span></span> <span data-ttu-id="b60ce-110">在指令碼中，您可以透過 `Dts` 物件的 <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Variables%2A> 屬性存取兩種類型的變數。</span><span class="sxs-lookup"><span data-stu-id="b60ce-110">Within the script, you access variables of both types through the <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Variables%2A> property of the `Dts` object.</span></span> <span data-ttu-id="b60ce-111">使用 `Value` 屬性讀取和寫入個別變數。</span><span class="sxs-lookup"><span data-stu-id="b60ce-111">Use the `Value` property to read from and write to individual variables.</span></span> <span data-ttu-id="b60ce-112">指令碼工作會以透明的方式管理鎖定，因為指令碼會讀取和修改變數值。</span><span class="sxs-lookup"><span data-stu-id="b60ce-112">The Script task transparently manages locking as the script reads and modifies the values of variables.</span></span>  
  
 <span data-ttu-id="b60ce-113">您可以在程式碼中使用變數之前，先透過 <xref:Microsoft.SqlServer.Dts.Runtime.Variables.Contains%2A> 屬性傳回的 <xref:Microsoft.SqlServer.Dts.Runtime.Variables> 集合之 <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Variables%2A> 方法，檢查變數是否存在。</span><span class="sxs-lookup"><span data-stu-id="b60ce-113">You can use the <xref:Microsoft.SqlServer.Dts.Runtime.Variables.Contains%2A> method of the <xref:Microsoft.SqlServer.Dts.Runtime.Variables> collection returned by the <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Variables%2A> property to check for the existence of a variable before using it in your code.</span></span>  
  
 <span data-ttu-id="b60ce-114">您也可以使用 <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.VariableDispenser%2A> 屬性 (Dts.VariableDispenser) 使用指令碼工作中的變數。</span><span class="sxs-lookup"><span data-stu-id="b60ce-114">You can also use the <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.VariableDispenser%2A> property (Dts.VariableDispenser) to work with variables in the Script task.</span></span> <span data-ttu-id="b60ce-115">在使用 <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.VariableDispenser%2A>時，您必須在自己的程式碼中處理變數值的鎖定語意和資料類型的轉換。</span><span class="sxs-lookup"><span data-stu-id="b60ce-115">When using the <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.VariableDispenser%2A>, you must handle both the locking semantics and the casting of data types for variable values in your own code.</span></span> <span data-ttu-id="b60ce-116">如果您想要使用在設計階段無法使用，但是會在執行階段以程式設計方式建立的變數，可能需要使用 <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.VariableDispenser%2A> 屬性，而不是 <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Variables%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="b60ce-116">You may need to use the <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.VariableDispenser%2A> property instead of the <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Variables%2A> property if you want to work with a variable that is not available at design time but is created programmatically at run time.</span></span>  
  
## <a name="using-the-script-task-within-a-foreach-loop-container"></a><span data-ttu-id="b60ce-117">使用 Foreach 迴圈容器中的指令碼工作</span><span class="sxs-lookup"><span data-stu-id="b60ce-117">Using the Script Task within a Foreach Loop Container</span></span>  
 <span data-ttu-id="b60ce-118">當在 Foreach 迴圈容器中重複地執行指令碼工作時，指令碼通常需要使用列舉值中目前項目的內容。</span><span class="sxs-lookup"><span data-stu-id="b60ce-118">When a Script task runs repeatedly within a Foreach Loop container, the script usually needs to work with the contents of the current item in the enumerator.</span></span> <span data-ttu-id="b60ce-119">例如，在使用 Foreach 檔案列舉值時，指令碼需要知道目前的檔案名稱；在使用 Foreach ADO 列舉值時，指令碼需要知道目前資料列中的資料行內容。</span><span class="sxs-lookup"><span data-stu-id="b60ce-119">For example, when using a Foreach File enumerator, the script needs to know the current file name; when using a Foreach ADO enumerator, the script needs to know the contents of the columns in the current row of data.</span></span>  
  
 <span data-ttu-id="b60ce-120">變數使得在 Foreach 迴圈容器與指令碼工作之間的此通訊變得可能。</span><span class="sxs-lookup"><span data-stu-id="b60ce-120">Variables make this communication between the Foreach Loop container and the Script task possible.</span></span> <span data-ttu-id="b60ce-121">在 [Foreach 迴圈編輯器] 的 [變數對應] 頁面上，將變數指派給單一列舉項目所傳回的每個資料項目。</span><span class="sxs-lookup"><span data-stu-id="b60ce-121">On the **Variable Mappings** page of the **Foreach Loop Editor**, assign variables to each item of data that is returned by a single enumerated item.</span></span> <span data-ttu-id="b60ce-122">例如，Foreach 檔案列舉值只會傳回在索引 0 的檔案名稱，因此只需要一個變數對應，然而傳回每個資料列中數個資料行的列舉值，需要您將不同的變數對應到在指令碼工作中要使用的每個資料行。</span><span class="sxs-lookup"><span data-stu-id="b60ce-122">For example, a Foreach File enumerator returns only a file name at Index 0 and therefore requires only one variable mapping, whereas an enumerator that returns several columns of data in each row requires you to map a different variable to each column that you want to use in the Script task.</span></span>  
  
 <span data-ttu-id="b60ce-123">將列舉專案對應到變數之後，您必須在 [腳本工作編輯器] 的 [腳本] 頁面上，將對應變數加入至 `ReadOnlyVariables` 屬性，才能讓腳本使用它們。 **Script** **Script Task Editor**</span><span class="sxs-lookup"><span data-stu-id="b60ce-123">After you have mapped enumerated items to variables, then you must add the mapped variables to the `ReadOnlyVariables` property on the **Script** page of the **Script Task Editor** to make them available to your script.</span></span> <span data-ttu-id="b60ce-124">如需處理資料夾中影像檔之 Foreach 迴圈容器中指令碼工作的範例，請參閱[以指令碼工作處理影像](../../extending-packages-scripting-task-examples/working-with-images-with-the-script-task.md)。</span><span class="sxs-lookup"><span data-stu-id="b60ce-124">For an example of a Script task within a Foreach Loop container that processes the image files in a folder, see [Working with Images with the Script Task](../../extending-packages-scripting-task-examples/working-with-images-with-the-script-task.md).</span></span>  
  
## <a name="variables-example"></a><span data-ttu-id="b60ce-125">變數範例</span><span class="sxs-lookup"><span data-stu-id="b60ce-125">Variables Example</span></span>  
 <span data-ttu-id="b60ce-126">下列範例示範如何存取和使用指令碼工作中的變數，以決定封裝工作流程的路徑。</span><span class="sxs-lookup"><span data-stu-id="b60ce-126">The following example demonstrates how to access and use variables in a Script task to determine the path of package workflow.</span></span> <span data-ttu-id="b60ce-127">此範例假設您已建立名為和的整數變數 `CustomerCount` `MaxRecordCount` ，並將它們加入至 `ReadOnlyVariables` [**腳本工作編輯器**] 中的集合。</span><span class="sxs-lookup"><span data-stu-id="b60ce-127">The sample assumes that you have created integer variables named `CustomerCount` and `MaxRecordCount` and added them to the `ReadOnlyVariables` collection in the **Script Task Editor**.</span></span> <span data-ttu-id="b60ce-128">`CustomerCount` 變數包含要匯入的客戶記錄數目。</span><span class="sxs-lookup"><span data-stu-id="b60ce-128">The `CustomerCount` variable contains the number of customer records to be imported.</span></span> <span data-ttu-id="b60ce-129">如果其值大於 `MaxRecordCount` 的值，指令碼工作會報告失敗。</span><span class="sxs-lookup"><span data-stu-id="b60ce-129">If its value is greater than the value of `MaxRecordCount`, the Script task reports failure.</span></span> <span data-ttu-id="b60ce-130">當因為已超過 `MaxRecordCount` 臨界值而發生失敗時，工作流程的錯誤路徑可以實作任何所需的清除。</span><span class="sxs-lookup"><span data-stu-id="b60ce-130">When a failure occurs because the `MaxRecordCount` threshold has been exceeded, the error path of the workflow can implement any required clean-up.</span></span>  
  
 <span data-ttu-id="b60ce-131">若要成功地編譯範例，您需要加入 Microsoft.SqlServer.ScriptTask 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="b60ce-131">To successfully compile the sample, you need to add a reference to the Microsoft.SqlServer.ScriptTask assembly.</span></span>  
  
```vb  
Public Sub Main()  
  
    Dim customerCount As Integer  
    Dim maxRecordCount As Integer  
  
    If Dts.Variables.Contains("CustomerCount") = True AndAlso _  
        Dts.Variables.Contains("MaxRecordCount") = True Then  
  
        customerCount = _  
            CType(Dts.Variables("CustomerCount").Value, Integer)  
        maxRecordCount = _  
            CType(Dts.Variables("MaxRecordCount").Value, Integer)  
  
    End If  
  
    If customerCount > maxRecordCount Then  
            Dts.TaskResult = ScriptResults.Failure  
    Else  
            Dts.TaskResult = ScriptResults.Success  
    End If  
  
End Sub  
```  
  
```csharp  
using System;  
using System.Data;  
using Microsoft.SqlServer.Dts.Runtime;  
  
public class ScriptMain  
{  
  
    public void Main()  
    {  
        int customerCount;  
        int maxRecordCount;  
  
        if (Dts.Variables.Contains("CustomerCount")==true&&Dts.Variables.Contains("MaxRecordCount")==true)  
  
        {  
            customerCount = (int) Dts.Variables["CustomerCount"].Value;  
            maxRecordCount = (int) Dts.Variables["MaxRecordCount"].Value;  
  
        }  
  
        if (customerCount>maxRecordCount)  
        {  
            Dts.TaskResult = (int)ScriptResults.Failure;  
        }  
        else  
        {  
            Dts.TaskResult = (int)ScriptResults.Success;  
        }  
  
    }  
  
}  
  
```  
  
<span data-ttu-id="b60ce-132">![Integration Services 圖示 (小型) ](../../media/dts-16.gif "Integration Services 圖示 (小)")會**保持最**新狀態 Integration Services  </span><span class="sxs-lookup"><span data-stu-id="b60ce-132">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="b60ce-133">若要取得 Microsoft 的最新下載、文件、範例和影片以及社群中的精選解決方案，請瀏覽 MSDN 上的 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 頁面：</span><span class="sxs-lookup"><span data-stu-id="b60ce-133">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="b60ce-134">瀏覽 MSDN 上的 Integration Services 頁面</span><span class="sxs-lookup"><span data-stu-id="b60ce-134">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="b60ce-135">若要得到這些更新的自動通知，請訂閱該頁面上所提供的 RSS 摘要。</span><span class="sxs-lookup"><span data-stu-id="b60ce-135">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b60ce-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b60ce-136">See Also</span></span>  
 <span data-ttu-id="b60ce-137">[Integration Services &#40;SSIS&#41; 變數](../../integration-services-ssis-variables.md) </span><span class="sxs-lookup"><span data-stu-id="b60ce-137">[Integration Services &#40;SSIS&#41; Variables](../../integration-services-ssis-variables.md) </span></span>  
 [<span data-ttu-id="b60ce-138">在封裝中使用變數</span><span class="sxs-lookup"><span data-stu-id="b60ce-138">Use Variables in Packages</span></span>](../../use-variables-in-packages.md)  
  
  
