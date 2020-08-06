---
title: 以指令碼工作處理 Excel 檔案 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- Script task [Integration Services], Excel files
- Script task [Integration Services], examples
- Excel [Integration Services]
ms.assetid: b8fa110a-2c9c-4f5a-8fe1-305555640e44
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 68a764452de548cd46e74d2a7f2f588a050a21c7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596208"
---
# <a name="working-with-excel-files-with-the-script-task"></a><span data-ttu-id="f199d-102">以指令碼工作處理 Excel 檔案</span><span class="sxs-lookup"><span data-stu-id="f199d-102">Working with Excel Files with the Script Task</span></span>
  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] <span data-ttu-id="f199d-103">提供 Excel 連接管理員、Excel 來源和 Excel 目的地，以處理 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Excel 檔案格式試算表中儲存的資料。</span><span class="sxs-lookup"><span data-stu-id="f199d-103">provides the Excel connection manager, Excel source, and Excel destination for working with data stored in spreadsheets in the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Excel file format.</span></span> <span data-ttu-id="f199d-104">本主題所述的技術會使用指令碼工作取得有關可用 Excel 資料庫 (活頁簿檔案) 與資料表 (工作表與具名範圍) 的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="f199d-104">The techniques described in this topic use the Script task to obtain information about available Excel databases (workbook files) and tables (worksheets and named ranges).</span></span> <span data-ttu-id="f199d-105">您可以輕鬆地修改這些範例，使其可與 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Jet OLE DB Provider 所支援的其他以檔案為基礎之資料來源搭配使用。</span><span class="sxs-lookup"><span data-stu-id="f199d-105">These samples can easily be modified to work with any of the other file-based data sources supported by the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Jet OLE DB Provider.</span></span>  
  
 [<span data-ttu-id="f199d-106">設定封裝以測試範例</span><span class="sxs-lookup"><span data-stu-id="f199d-106">Configuring a Package to Test the Samples</span></span>](#configuring)  
  
 [<span data-ttu-id="f199d-107">範例 1：檢查 Excel 檔案是否存在</span><span class="sxs-lookup"><span data-stu-id="f199d-107">Example1: Check Whether an Excel File Exists</span></span>](#example1)  
  
 [<span data-ttu-id="f199d-108">範例 2：檢查 Excel 資料表是否存在</span><span class="sxs-lookup"><span data-stu-id="f199d-108">Example 2: Check Whether an Excel Table Exists</span></span>](#example2)  
  
 [<span data-ttu-id="f199d-109">範例 3：取得資料夾中的 Excel 檔案清單</span><span class="sxs-lookup"><span data-stu-id="f199d-109">Example 3: Get a List of Excel Files in a Folder</span></span>](#example3)  
  
 [<span data-ttu-id="f199d-110">範例 4：取得 Excel 檔案中的資料表清單</span><span class="sxs-lookup"><span data-stu-id="f199d-110">Example 4: Get a List of Tables in an Excel File</span></span>](#example4)  
  
 [<span data-ttu-id="f199d-111">顯示範例的結果</span><span class="sxs-lookup"><span data-stu-id="f199d-111">Displaying the Results of the Samples</span></span>](#testing)  
  
> [!NOTE]  
>  <span data-ttu-id="f199d-112">如果您想要建立可更輕鬆地在多個封裝之間重複使用的工作，請考慮使用此指令碼工作範例中的程式碼做為自訂工作的起點。</span><span class="sxs-lookup"><span data-stu-id="f199d-112">If you want to create a task that you can more easily reuse across multiple packages, consider using the code in this Script task sample as the starting point for a custom task.</span></span> <span data-ttu-id="f199d-113">如需詳細資訊，請參閱 [開發自訂工作](../extending-packages-custom-objects/task/developing-a-custom-task.md)。</span><span class="sxs-lookup"><span data-stu-id="f199d-113">For more information, see [Developing a Custom Task](../extending-packages-custom-objects/task/developing-a-custom-task.md).</span></span>  
  
##  <a name="configuring-a-package-to-test-the-samples"></a><a name="configuring"></a> <span data-ttu-id="f199d-114">設定套件以測試範例</span><span class="sxs-lookup"><span data-stu-id="f199d-114">Configuring a Package to Test the Samples</span></span>  
 <span data-ttu-id="f199d-115">您可以設定單一封裝以測試本主題中的所有範例。</span><span class="sxs-lookup"><span data-stu-id="f199d-115">You can configure a single package to test all the samples in this topic.</span></span> <span data-ttu-id="f199d-116">範例使用許多相同的封裝變數與相同的 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 類別。</span><span class="sxs-lookup"><span data-stu-id="f199d-116">The samples use many of the same package variables and the same [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] classes.</span></span>  
  
#### <a name="to-configure-a-package-for-use-with-the-examples-in-this-topic"></a><span data-ttu-id="f199d-117">設定封裝與本主題中的範例搭配使用</span><span class="sxs-lookup"><span data-stu-id="f199d-117">To configure a package for use with the examples in this topic</span></span>  
  
1.  <span data-ttu-id="f199d-118">在 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 中建立新的 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 專案，並開啟預設封裝以進行編輯。</span><span class="sxs-lookup"><span data-stu-id="f199d-118">Create a new [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] project in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] and open the default package for editing.</span></span>  
  
2.  <span data-ttu-id="f199d-119">**變數**。</span><span class="sxs-lookup"><span data-stu-id="f199d-119">**Variables**.</span></span> <span data-ttu-id="f199d-120">開啟 [變數]\*\*\*\* 視窗，並定義下列變數：</span><span class="sxs-lookup"><span data-stu-id="f199d-120">Open the **Variables** window and define the following variables:</span></span>  
  
    -   <span data-ttu-id="f199d-121">類型為 `String` 的 `ExcelFile`。</span><span class="sxs-lookup"><span data-stu-id="f199d-121">`ExcelFile`, of type `String`.</span></span> <span data-ttu-id="f199d-122">輸入現有 Excel 活頁簿的完整路徑與檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="f199d-122">Enter the complete path and filename to an existing Excel workbook.</span></span>  
  
    -   <span data-ttu-id="f199d-123">類型為 `String` 的 `ExcelTable`。</span><span class="sxs-lookup"><span data-stu-id="f199d-123">`ExcelTable`, of type `String`.</span></span> <span data-ttu-id="f199d-124">輸入以 `ExcelFile` 變數值命名之活頁簿中，現有工作表或具名範圍的名稱。</span><span class="sxs-lookup"><span data-stu-id="f199d-124">Enter the name of an existing worksheet or named range in the workbook named in the value of the `ExcelFile` variable.</span></span> <span data-ttu-id="f199d-125">此值區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="f199d-125">This value is case-sensitive.</span></span>  
  
    -   <span data-ttu-id="f199d-126">類型為 `Boolean` 的 `ExcelFileExists`。</span><span class="sxs-lookup"><span data-stu-id="f199d-126">`ExcelFileExists`, of type `Boolean`.</span></span>  
  
    -   <span data-ttu-id="f199d-127">類型為 `Boolean` 的 `ExcelTableExists`。</span><span class="sxs-lookup"><span data-stu-id="f199d-127">`ExcelTableExists`, of type `Boolean`.</span></span>  
  
    -   <span data-ttu-id="f199d-128">類型為 `String` 的 `ExcelFolder`。</span><span class="sxs-lookup"><span data-stu-id="f199d-128">`ExcelFolder`, of type `String`.</span></span> <span data-ttu-id="f199d-129">輸入含有至少一個 Excel 活頁簿的資料夾完整路徑。</span><span class="sxs-lookup"><span data-stu-id="f199d-129">Enter the complete path of a folder that contains at least one Excel workbook.</span></span>  
  
    -   <span data-ttu-id="f199d-130">類型為 `Object` 的 `ExcelFiles`。</span><span class="sxs-lookup"><span data-stu-id="f199d-130">`ExcelFiles`, of type `Object`.</span></span>  
  
    -   <span data-ttu-id="f199d-131">類型為 `Object` 的 `ExcelTables`。</span><span class="sxs-lookup"><span data-stu-id="f199d-131">`ExcelTables`, of type `Object`.</span></span>  
  
3.  <span data-ttu-id="f199d-132">**Imports 陳述式**。</span><span class="sxs-lookup"><span data-stu-id="f199d-132">**Imports statements**.</span></span> <span data-ttu-id="f199d-133">大部分的程式碼範例都需要您在指令碼檔案最上方匯入下列一或兩個 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 命名空間：</span><span class="sxs-lookup"><span data-stu-id="f199d-133">Most of the code samples require you to import one or both of the following [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] namespaces at the top of your script file:</span></span>  
  
    -   <span data-ttu-id="f199d-134">`System.IO`，處理檔案系統作業。</span><span class="sxs-lookup"><span data-stu-id="f199d-134">`System.IO`, for file system operations.</span></span>  
  
    -   <span data-ttu-id="f199d-135">`System.Data.OleDb`，開啟 Excel 檔案做為資料來源。</span><span class="sxs-lookup"><span data-stu-id="f199d-135">`System.Data.OleDb`, to open Excel files as data sources.</span></span>  
  
4.  <span data-ttu-id="f199d-136">**參考**。</span><span class="sxs-lookup"><span data-stu-id="f199d-136">**References**.</span></span> <span data-ttu-id="f199d-137">從 Excel 檔案讀取結構描述資訊的程式碼範例，在指令碼專案中需要有 `System.Xml` 命名空間的參考。</span><span class="sxs-lookup"><span data-stu-id="f199d-137">The code samples that read schema information from Excel files require an additional reference in the script project to the `System.Xml` namespace.</span></span>  
  
5.  <span data-ttu-id="f199d-138">請使用 [選項]\*\*\*\* 對話方塊中 [一般]\*\*\*\* 頁面上的 [指令碼語言]\*\*\*\* 選項，為指令碼元件設定預設的指令碼語言。</span><span class="sxs-lookup"><span data-stu-id="f199d-138">Set the default scripting language for the Script component by using the **Scripting language** option on the **General** page of the **Options** dialog box.</span></span> <span data-ttu-id="f199d-139">如需相關資訊，請參閱 [General Page](../general-page-of-integration-services-designers-options.md)。</span><span class="sxs-lookup"><span data-stu-id="f199d-139">For more information, see [General Page](../general-page-of-integration-services-designers-options.md).</span></span>  
  
##  <a name="example-1-description-check-whether-an-excel-file-exists"></a><a name="example1"></a> <span data-ttu-id="f199d-140">範例 1 描述：檢查 Excel 檔案是否存在</span><span class="sxs-lookup"><span data-stu-id="f199d-140">Example 1 Description: Check Whether an Excel File Exists</span></span>  
 <span data-ttu-id="f199d-141">此範例會判斷 `ExcelFile` 變數中指定的 Excel 活頁簿檔案是否存在，然後將 `ExcelFileExists` 變數的布林值設定為結果。</span><span class="sxs-lookup"><span data-stu-id="f199d-141">This example determines whether the Excel workbook file specified in the `ExcelFile` variable exists, and then sets the Boolean value of the `ExcelFileExists` variable to the result.</span></span> <span data-ttu-id="f199d-142">您可以為封裝工作流程中的分支使用此布林值。</span><span class="sxs-lookup"><span data-stu-id="f199d-142">You can use this Boolean value for branching in the workflow of the package.</span></span>  
  
#### <a name="to-configure-this-script-task-example"></a><span data-ttu-id="f199d-143">設定此指令碼工作範例</span><span class="sxs-lookup"><span data-stu-id="f199d-143">To configure this Script Task example</span></span>  
  
1.  <span data-ttu-id="f199d-144">將新的腳本工作加入封裝，並將其名稱變更為 `ExcelFileExists` 。</span><span class="sxs-lookup"><span data-stu-id="f199d-144">Add a new Script task to the package and change its name to `ExcelFileExists`.</span></span>  
  
2.  <span data-ttu-id="f199d-145">在 [指令碼工作編輯器]\*\*\*\* 的 [指令碼]\*\*\*\* 索引標籤上，按一下 **ReadOnlyVariables**，並使用下列其中一項方法輸入屬性值：</span><span class="sxs-lookup"><span data-stu-id="f199d-145">In the **Script Task Editor**, on the **Script** tab, click **ReadOnlyVariables** and enter the property value using one of the following methods:</span></span>  
  
    -   <span data-ttu-id="f199d-146">輸入 `ExcelFile`。</span><span class="sxs-lookup"><span data-stu-id="f199d-146">Type `ExcelFile`.</span></span>  
  
         <span data-ttu-id="f199d-147">-或-</span><span class="sxs-lookup"><span data-stu-id="f199d-147">-or-</span></span>  
  
    -   <span data-ttu-id="f199d-148">按一下屬性欄位旁邊的省略號 (**...**) ] 按鈕，然後在 [**選取變數**] 對話方塊中選取 `ExcelFile` 變數。</span><span class="sxs-lookup"><span data-stu-id="f199d-148">Click the ellipsis (**...**) button next to the property field, and in the **Select variables** dialog box, select the `ExcelFile` variable.</span></span>  
  
3.  <span data-ttu-id="f199d-149">按一下 **ReadWriteVariables**，並使用下列其中一項方法輸入屬性值：</span><span class="sxs-lookup"><span data-stu-id="f199d-149">Click **ReadWriteVariables** and enter the property value using one of the following methods:</span></span>  
  
    -   <span data-ttu-id="f199d-150">輸入 `ExcelFileExists`。</span><span class="sxs-lookup"><span data-stu-id="f199d-150">Type `ExcelFileExists`.</span></span>  
  
         <span data-ttu-id="f199d-151">-或-</span><span class="sxs-lookup"><span data-stu-id="f199d-151">-or-</span></span>  
  
    -   <span data-ttu-id="f199d-152">按一下屬性欄位旁邊的省略號 (**...**) ] 按鈕，然後在 [**選取變數**] 對話方塊中選取 `ExcelFileExists` 變數。</span><span class="sxs-lookup"><span data-stu-id="f199d-152">Click the ellipsis (**...**) button next to the property field, and in the **Select variables** dialog box, select the `ExcelFileExists` variable.</span></span>  
  
4.  <span data-ttu-id="f199d-153">按一下 [編輯指令碼]\*\*\*\*，以開啟指令碼編輯器。</span><span class="sxs-lookup"><span data-stu-id="f199d-153">Click **Edit Script** to open the script editor.</span></span>  
  
5.  <span data-ttu-id="f199d-154">在指令碼檔案最上方加入 `Imports` 命名空間的 `System.IO` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="f199d-154">Add an `Imports` statement for the `System.IO` namespace at the top of the script file.</span></span>  
  
6.  <span data-ttu-id="f199d-155">加入下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="f199d-155">Add the following code.</span></span>  
  
### <a name="example-1-code"></a><span data-ttu-id="f199d-156">範例 1 程式碼</span><span class="sxs-lookup"><span data-stu-id="f199d-156">Example 1 Code</span></span>  
  
```vb  
Public Class ScriptMain  
  Public Sub Main()  
    Dim fileToTest As String  
  
    fileToTest = Dts.Variables("ExcelFile").Value.ToString  
    If File.Exists(fileToTest) Then  
      Dts.Variables("ExcelFileExists").Value = True  
    Else  
      Dts.Variables("ExcelFileExists").Value = False  
    End If  
  
    Dts.TaskResult = ScriptResults.Success  
  End Sub  
End Class  
```  
  
```csharp  
public class ScriptMain  
{  
  public void Main()  
  {  
    string fileToTest;  
  
    fileToTest = Dts.Variables["ExcelFile"].Value.ToString();  
    if (File.Exists(fileToTest))  
    {  
      Dts.Variables["ExcelFileExists"].Value = true;  
    }  
    else  
    {  
      Dts.Variables["ExcelFileExists"].Value = false;  
    }  
  
    Dts.TaskResult = (int)ScriptResults.Success;  
  }  
}  
```  
  
##  <a name="example-2-description-check-whether-an-excel-table-exists"></a><a name="example2"></a> <span data-ttu-id="f199d-157">範例 2 描述：檢查 Excel 資料表是否存在</span><span class="sxs-lookup"><span data-stu-id="f199d-157">Example 2 Description: Check Whether an Excel Table Exists</span></span>  
 <span data-ttu-id="f199d-158">此範例會判斷 `ExcelTable` 變數中指定的 Excel 工作表或具名範圍是否存在於 `ExcelFile` 變數中指定的 Excel 活頁簿檔案，然後將 `ExcelTableExists` 變數的布林值設定為結果。</span><span class="sxs-lookup"><span data-stu-id="f199d-158">This example determines whether the Excel worksheet or named range specified in the `ExcelTable` variable exists in the Excel workbook file specified in the `ExcelFile` variable, and then sets the Boolean value of the `ExcelTableExists` variable to the result.</span></span> <span data-ttu-id="f199d-159">您可以為封裝工作流程中的分支使用此布林值。</span><span class="sxs-lookup"><span data-stu-id="f199d-159">You can use this Boolean value for branching in the workflow of the package.</span></span>  
  
#### <a name="to-configure-this-script-task-example"></a><span data-ttu-id="f199d-160">設定此指令碼工作範例</span><span class="sxs-lookup"><span data-stu-id="f199d-160">To configure this Script Task example</span></span>  
  
1.  <span data-ttu-id="f199d-161">將新的腳本工作加入封裝，並將其名稱變更為 `ExcelTableExists` 。</span><span class="sxs-lookup"><span data-stu-id="f199d-161">Add a new Script task to the package and change its name to `ExcelTableExists`.</span></span>  
  
2.  <span data-ttu-id="f199d-162">在 [指令碼工作編輯器]\*\*\*\* 的 [指令碼]\*\*\*\* 索引標籤上，按一下 **ReadOnlyVariables**，並使用下列其中一項方法輸入屬性值：</span><span class="sxs-lookup"><span data-stu-id="f199d-162">In the **Script Task Editor**, on the **Script** tab, click **ReadOnlyVariables** and enter the property value using one of the following methods:</span></span>  
  
    -   <span data-ttu-id="f199d-163">輸入 `ExcelTable` 並 `ExcelFile` 以逗號分隔`.`</span><span class="sxs-lookup"><span data-stu-id="f199d-163">Type `ExcelTable` and `ExcelFile` separated by commas`.`</span></span>  
  
         <span data-ttu-id="f199d-164">-或-</span><span class="sxs-lookup"><span data-stu-id="f199d-164">-or-</span></span>  
  
    -   <span data-ttu-id="f199d-165">按一下屬性欄位旁邊的省略號 (**...**) ] 按鈕，然後在 [**選取變數**] 對話方塊中，選取 `ExcelTable` 和 `ExcelFile` 變數。</span><span class="sxs-lookup"><span data-stu-id="f199d-165">Click the ellipsis (**...**) button next to the property field, and in the **Select variables** dialog box, select the `ExcelTable` and `ExcelFile` variables.</span></span>  
  
3.  <span data-ttu-id="f199d-166">按一下 **ReadWriteVariables**，並使用下列其中一項方法輸入屬性值：</span><span class="sxs-lookup"><span data-stu-id="f199d-166">Click **ReadWriteVariables** and enter the property value using one of the following methods:</span></span>  
  
    -   <span data-ttu-id="f199d-167">輸入 `ExcelTableExists`。</span><span class="sxs-lookup"><span data-stu-id="f199d-167">Type `ExcelTableExists`.</span></span>  
  
         <span data-ttu-id="f199d-168">-或-</span><span class="sxs-lookup"><span data-stu-id="f199d-168">-or-</span></span>  
  
    -   <span data-ttu-id="f199d-169">按一下屬性欄位旁邊的省略號 (**...**) ] 按鈕，然後在 [**選取變數**] 對話方塊中選取 `ExcelTableExists` 變數。</span><span class="sxs-lookup"><span data-stu-id="f199d-169">Click the ellipsis (**...**) button next to the property field, and in the **Select variables** dialog box, select the `ExcelTableExists` variable.</span></span>  
  
4.  <span data-ttu-id="f199d-170">按一下 [編輯指令碼]\*\*\*\*，以開啟指令碼編輯器。</span><span class="sxs-lookup"><span data-stu-id="f199d-170">Click **Edit Script** to open the script editor.</span></span>  
  
5.  <span data-ttu-id="f199d-171">在指令碼專案中加入 `System.Xml` 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="f199d-171">Add a reference to the `System.Xml` assembly in the script project.</span></span>  
  
6.  <span data-ttu-id="f199d-172">在指令碼檔案最上方加入 `Imports` 與 `System.IO` 命名空間的 `System.Data.OleDb` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="f199d-172">Add `Imports` statements for the `System.IO` and `System.Data.OleDb` namespaces at the top of the script file.</span></span>  
  
7.  <span data-ttu-id="f199d-173">加入下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="f199d-173">Add the following code.</span></span>  
  
### <a name="example-2-code"></a><span data-ttu-id="f199d-174">範例 2 程式碼</span><span class="sxs-lookup"><span data-stu-id="f199d-174">Example 2 Code</span></span>  
  
```vb  
Public Class ScriptMain  
  Public Sub Main()  
    Dim fileToTest As String  
    Dim tableToTest As String  
    Dim connectionString As String  
    Dim excelConnection As OleDbConnection  
    Dim excelTables As DataTable  
    Dim excelTable As DataRow  
    Dim currentTable As String  
  
    fileToTest = Dts.Variables("ExcelFile").Value.ToString  
    tableToTest = Dts.Variables("ExcelTable").Value.ToString  
  
    Dts.Variables("ExcelTableExists").Value = False  
    If File.Exists(fileToTest) Then  
      connectionString = "Provider=Microsoft.Jet.OLEDB.4.0;" & _  
        "Data Source=" & fileToTest & _  
        ";Extended Properties=Excel 8.0"  
      excelConnection = New OleDbConnection(connectionString)  
      excelConnection.Open()  
      excelTables = excelConnection.GetSchema("Tables")  
      For Each excelTable In excelTables.Rows  
        currentTable = excelTable.Item("TABLE_NAME").ToString  
        If currentTable = tableToTest Then  
          Dts.Variables("ExcelTableExists").Value = True  
        End If  
      Next  
    End If  
  
    Dts.TaskResult = ScriptResults.Success  
  End Sub  
End Class  
```  
  
```csharp  
public class ScriptMain  
{  
    public void Main()  
        {  
            string fileToTest;  
            string tableToTest;  
            string connectionString;  
            OleDbConnection excelConnection;  
            DataTable excelTables;  
            string currentTable;  
  
            fileToTest = Dts.Variables["ExcelFile"].Value.ToString();  
            tableToTest = Dts.Variables["ExcelTable"].Value.ToString();  
  
            Dts.Variables["ExcelTableExists"].Value = false;  
            if (File.Exists(fileToTest))  
            {  
                connectionString = "Provider=Microsoft.Jet.OLEDB.4.0;" +  
                "Data Source=" + fileToTest + ";Extended Properties=Excel 8.0";  
                excelConnection = new OleDbConnection(connectionString);  
                excelConnection.Open();  
                excelTables = excelConnection.GetSchema("Tables");  
                foreach (DataRow excelTable in excelTables.Rows)  
                {  
                    currentTable = excelTable["TABLE_NAME"].ToString();  
                    if (currentTable == tableToTest)  
                    {  
                        Dts.Variables["ExcelTableExists"].Value = true;  
                    }  
                }  
            }  
  
            Dts.TaskResult = (int)ScriptResults.Success;  
  
        }  
}  
```  
  
##  <a name="example-3-description-get-a-list-of-excel-files-in-a-folder"></a><a name="example3"></a> <span data-ttu-id="f199d-175">範例 3 描述：取得資料夾中的 Excel 檔案清單</span><span class="sxs-lookup"><span data-stu-id="f199d-175">Example 3 Description: Get a List of Excel Files in a Folder</span></span>  
 <span data-ttu-id="f199d-176">此範例會使用在 `ExcelFolder` 變數值中指定的資料夾內所找到的 Excel 檔案清單，來填滿陣列，然後將陣列複製到 `ExcelFiles` 變數中。</span><span class="sxs-lookup"><span data-stu-id="f199d-176">This example fills an array with the list of Excel files found in the folder specified in the value of the `ExcelFolder` variable, and then copies the array into the `ExcelFiles` variable.</span></span> <span data-ttu-id="f199d-177">您可以使用 Foreach From Variable 列舉值來反覆運算陣列中的檔案。</span><span class="sxs-lookup"><span data-stu-id="f199d-177">You can use the Foreach from Variable enumerator to iterate over the files in the array.</span></span>  
  
#### <a name="to-configure-this-script-task-example"></a><span data-ttu-id="f199d-178">設定此指令碼工作範例</span><span class="sxs-lookup"><span data-stu-id="f199d-178">To configure this Script Task example</span></span>  
  
1.  <span data-ttu-id="f199d-179">將新指令碼工作新增至套件，並將其名稱變更為 **GetExcelFiles**。</span><span class="sxs-lookup"><span data-stu-id="f199d-179">Add a new Script task to the package and change its name to **GetExcelFiles**.</span></span>  
  
2.  <span data-ttu-id="f199d-180">開啟 [指令碼工作編輯器]\*\*\*\* 的 [指令碼]\*\*\*\* 索引標籤，並按一下 **ReadOnlyVariables**，然後使用下列其中一項方法輸入屬性值：</span><span class="sxs-lookup"><span data-stu-id="f199d-180">Open the **Script Task Editor**, on the **Script** tab, click **ReadOnlyVariables** and enter the property value using one of the following methods:</span></span>  
  
    -   <span data-ttu-id="f199d-181">輸入 `ExcelFolder`</span><span class="sxs-lookup"><span data-stu-id="f199d-181">Type `ExcelFolder`</span></span>  
  
         <span data-ttu-id="f199d-182">-或-</span><span class="sxs-lookup"><span data-stu-id="f199d-182">-or-</span></span>  
  
    -   <span data-ttu-id="f199d-183">按一下屬性欄位旁邊的省略號 (**...**) ] 按鈕，然後在 [**選取變數**] 對話方塊中選取 ExcelFolder 變數。</span><span class="sxs-lookup"><span data-stu-id="f199d-183">Click the ellipsis (**...**) button next to the property field, and in the **Select variables** dialog box, select the ExcelFolder variable.</span></span>  
  
3.  <span data-ttu-id="f199d-184">按一下 **ReadWriteVariables**，並使用下列其中一項方法輸入屬性值：</span><span class="sxs-lookup"><span data-stu-id="f199d-184">Click **ReadWriteVariables** and enter the property value using one of the following methods:</span></span>  
  
    -   <span data-ttu-id="f199d-185">輸入 `ExcelFiles`。</span><span class="sxs-lookup"><span data-stu-id="f199d-185">Type `ExcelFiles`.</span></span>  
  
         <span data-ttu-id="f199d-186">-或-</span><span class="sxs-lookup"><span data-stu-id="f199d-186">-or-</span></span>  
  
    -   <span data-ttu-id="f199d-187">按一下屬性欄位旁邊的省略號 (**...**) ] 按鈕，然後在 [**選取變數**] 對話方塊中選取 ExcelFiles 變數。</span><span class="sxs-lookup"><span data-stu-id="f199d-187">Click the ellipsis (**...**) button next to the property field, and in the **Select variables** dialog box, select the ExcelFiles variable.</span></span>  
  
4.  <span data-ttu-id="f199d-188">按一下 [編輯指令碼]\*\*\*\*，以開啟指令碼編輯器。</span><span class="sxs-lookup"><span data-stu-id="f199d-188">Click **Edit Script** to open the script editor.</span></span>  
  
5.  <span data-ttu-id="f199d-189">在指令碼檔案最上方加入 `Imports` 命名空間的 `System.IO` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="f199d-189">Add an `Imports` statement for the `System.IO` namespace at the top of the script file.</span></span>  
  
6.  <span data-ttu-id="f199d-190">加入下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="f199d-190">Add the following code.</span></span>  
  
### <a name="example-3-code"></a><span data-ttu-id="f199d-191">範例 3 程式碼</span><span class="sxs-lookup"><span data-stu-id="f199d-191">Example 3 Code</span></span>  
  
```vb  
Public Class ScriptMain  
  Public Sub Main()  
    Const FILE_PATTERN As String = "*.xls"  
  
    Dim excelFolder As String  
    Dim excelFiles As String()  
  
    excelFolder = Dts.Variables("ExcelFolder").Value.ToString  
    excelFiles = Directory.GetFiles(excelFolder, FILE_PATTERN)  
  
    Dts.Variables("ExcelFiles").Value = excelFiles  
  
    Dts.TaskResult = ScriptResults.Success  
  End Sub  
End Class  
```  
  
```csharp  
public class ScriptMain  
{  
  public void Main()  
  {  
    const string FILE_PATTERN = "*.xls";  
  
    string excelFolder;  
    string[] excelFiles;  
  
    excelFolder = Dts.Variables["ExcelFolder"].Value.ToString();  
    excelFiles = Directory.GetFiles(excelFolder, FILE_PATTERN);  
  
    Dts.Variables["ExcelFiles"].Value = excelFiles;  
  
    Dts.TaskResult = (int)ScriptResults.Success;  
  }  
}  
```  
  
### <a name="alternate-solution"></a><span data-ttu-id="f199d-192">替代方案</span><span class="sxs-lookup"><span data-stu-id="f199d-192">Alternate Solution</span></span>  
 <span data-ttu-id="f199d-193">您也可以使用 ForEach 檔案列舉值反覆運算資料夾中的所有 Excel 檔案，以代替使用指令碼工作將 Excel 檔案清單蒐集到陣列中的方式。</span><span class="sxs-lookup"><span data-stu-id="f199d-193">Instead of using a Script task to gather a list of Excel files into an array, you can also use the ForEach File enumerator to iterate over all the Excel files in a folder.</span></span> <span data-ttu-id="f199d-194">如需詳細資訊，請參閱[使用 Foreach 迴圈容器來執行 Excel 檔案和資料表迴圈](../control-flow/foreach-loop-container.md)。</span><span class="sxs-lookup"><span data-stu-id="f199d-194">For more information, see [Loop through Excel Files and Tables by Using a Foreach Loop Container](../control-flow/foreach-loop-container.md).</span></span>  
  
##  <a name="example-4-description-get-a-list-of-tables-in-an-excel-file"></a><a name="example4"></a> <span data-ttu-id="f199d-195">範例 4 描述：取得 Excel 檔案中的資料表清單</span><span class="sxs-lookup"><span data-stu-id="f199d-195">Example 4 Description: Get a List of Tables in an Excel File</span></span>  
 <span data-ttu-id="f199d-196">此範例會使用在 `ExcelFile` 變數值中指定的 Excel 活頁簿檔案內找到的工作表清單和具名範圍，來填滿陣列，然後將陣列複製到 `ExcelTables` 變數中。</span><span class="sxs-lookup"><span data-stu-id="f199d-196">This example fills an array with the list of worksheets and named ranges found in the Excel workbook file specified by the value of the `ExcelFile` variable, and then copies the array into the `ExcelTables` variable.</span></span> <span data-ttu-id="f199d-197">您可以使用 Foreach From Variable 列舉值來反覆運算陣列中的資料表。</span><span class="sxs-lookup"><span data-stu-id="f199d-197">You can use the Foreach from Variable Enumerator to iterate over the tables in the array.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f199d-198">Excel 活頁簿中資料表清單包含活頁簿 (具有 $ 後置詞) 及具名範圍。</span><span class="sxs-lookup"><span data-stu-id="f199d-198">The list of tables in an Excel workbook includes both worksheets (which have the $ suffix) and named ranges.</span></span> <span data-ttu-id="f199d-199">如果您必須只篩選清單中的工作表或具名範圍，必須加入其他程式碼以達成此目的。</span><span class="sxs-lookup"><span data-stu-id="f199d-199">If you have to filter the list for only worksheets or only named ranges, you may have to add additional code for this purpose.</span></span>  
  
#### <a name="to-configure-this-script-task-example"></a><span data-ttu-id="f199d-200">設定此指令碼工作範例</span><span class="sxs-lookup"><span data-stu-id="f199d-200">To configure this Script Task example</span></span>  
  
1.  <span data-ttu-id="f199d-201">將新指令碼工作新增至套件，並將其名稱變更為 **GetExcelTables**。</span><span class="sxs-lookup"><span data-stu-id="f199d-201">Add a new Script task to the package and change its name to **GetExcelTables**.</span></span>  
  
2.  <span data-ttu-id="f199d-202">開啟 [指令碼工作編輯器]\*\*\*\* 的 [指令碼]\*\*\*\* 索引標籤，並按一下 **ReadOnlyVariables**，然後使用下列其中一項方法輸入屬性值：</span><span class="sxs-lookup"><span data-stu-id="f199d-202">Open the **Script Task Editor**, on the **Script** tab, click **ReadOnlyVariables** and enter the property value using one of the following methods:</span></span>  
  
    -   <span data-ttu-id="f199d-203">輸入 `ExcelFile`。</span><span class="sxs-lookup"><span data-stu-id="f199d-203">Type `ExcelFile`.</span></span>  
  
         <span data-ttu-id="f199d-204">-或-</span><span class="sxs-lookup"><span data-stu-id="f199d-204">-or-</span></span>  
  
    -   <span data-ttu-id="f199d-205">按一下屬性欄位旁邊的省略號 (**...**) ] 按鈕，然後在 [**選取變數**] 對話方塊中選取 ExcelFile 變數。</span><span class="sxs-lookup"><span data-stu-id="f199d-205">Click the ellipsis (**...**) button next to the property field, and in the **Select variables** dialog box, select the ExcelFile variable.</span></span>  
  
3.  <span data-ttu-id="f199d-206">按一下 **ReadWriteVariables**，並使用下列其中一項方法輸入屬性值：</span><span class="sxs-lookup"><span data-stu-id="f199d-206">Click **ReadWriteVariables** and enter the property value using one of the following methods:</span></span>  
  
    -   <span data-ttu-id="f199d-207">輸入 `ExcelTables`。</span><span class="sxs-lookup"><span data-stu-id="f199d-207">Type `ExcelTables`.</span></span>  
  
         <span data-ttu-id="f199d-208">-或-</span><span class="sxs-lookup"><span data-stu-id="f199d-208">-or-</span></span>  
  
    -   <span data-ttu-id="f199d-209">按一下屬性欄位旁邊的省略號 (**...**) ] 按鈕，然後在 [**選取變數**] 對話方塊中選取 exceltables 變數。</span><span class="sxs-lookup"><span data-stu-id="f199d-209">Click the ellipsis (**...**) button next to the property field, and in the **Select variables** dialog box, select the ExcelTablesvariable.</span></span>  
  
4.  <span data-ttu-id="f199d-210">按一下 [編輯指令碼]\*\*\*\*，以開啟指令碼編輯器。</span><span class="sxs-lookup"><span data-stu-id="f199d-210">Click **Edit Script** to open the script editor.</span></span>  
  
5.  <span data-ttu-id="f199d-211">在指令碼專案中，加入 `System.Xml` 命名空間的參考。</span><span class="sxs-lookup"><span data-stu-id="f199d-211">Add a reference to the `System.Xml` namespace in the script project.</span></span>  
  
6.  <span data-ttu-id="f199d-212">在指令碼檔案最上方加入 `Imports` 命名空間的 `System.Data.OleDb` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="f199d-212">Add an `Imports` statement for the `System.Data.OleDb` namespace at the top of the script file.</span></span>  
  
7.  <span data-ttu-id="f199d-213">加入下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="f199d-213">Add the following code.</span></span>  
  
### <a name="example-4-code"></a><span data-ttu-id="f199d-214">範例 4 程式碼</span><span class="sxs-lookup"><span data-stu-id="f199d-214">Example 4 Code</span></span>  
  
```vb  
Public Class ScriptMain  
  Public Sub Main()  
    Dim excelFile As String  
    Dim connectionString As String  
    Dim excelConnection As OleDbConnection  
    Dim tablesInFile As DataTable  
    Dim tableCount As Integer = 0  
    Dim tableInFile As DataRow  
    Dim currentTable As String  
    Dim tableIndex As Integer = 0  
  
    Dim excelTables As String()  
  
    excelFile = Dts.Variables("ExcelFile").Value.ToString  
    connectionString = "Provider=Microsoft.Jet.OLEDB.4.0;" & _  
        "Data Source=" & excelFile & _  
        ";Extended Properties=Excel 8.0"  
    excelConnection = New OleDbConnection(connectionString)  
    excelConnection.Open()  
    tablesInFile = excelConnection.GetSchema("Tables")  
    tableCount = tablesInFile.Rows.Count  
    ReDim excelTables(tableCount - 1)  
    For Each tableInFile In tablesInFile.Rows  
      currentTable = tableInFile.Item("TABLE_NAME").ToString  
      excelTables(tableIndex) = currentTable  
      tableIndex += 1  
    Next  
  
    Dts.Variables("ExcelTables").Value = excelTables  
  
    Dts.TaskResult = ScriptResults.Success  
  End Sub  
End Class  
```  
  
```csharp  
public class ScriptMain  
{  
  public void Main()  
        {  
            string excelFile;  
            string connectionString;  
            OleDbConnection excelConnection;  
            DataTable tablesInFile;  
            int tableCount = 0;  
            string currentTable;  
            int tableIndex = 0;  
  
            string[] excelTables = new string[5];  
  
            excelFile = Dts.Variables["ExcelFile"].Value.ToString();  
            connectionString = "Provider=Microsoft.Jet.OLEDB.4.0;" +  
                "Data Source=" + excelFile + ";Extended Properties=Excel 8.0";  
            excelConnection = new OleDbConnection(connectionString);  
            excelConnection.Open();  
            tablesInFile = excelConnection.GetSchema("Tables");  
            tableCount = tablesInFile.Rows.Count;  
  
            foreach (DataRow tableInFile in tablesInFile.Rows)  
            {  
                currentTable = tableInFile["TABLE_NAME"].ToString();  
                excelTables[tableIndex] = currentTable;  
                tableIndex += 1;  
            }  
  
            Dts.Variables["ExcelTables"].Value = excelTables;  
  
            Dts.TaskResult = (int)ScriptResults.Success;  
        }  
}  
```  
  
### <a name="alternate-solution"></a><span data-ttu-id="f199d-215">替代方案</span><span class="sxs-lookup"><span data-stu-id="f199d-215">Alternate Solution</span></span>  
 <span data-ttu-id="f199d-216">您也可以使用 Foreach ADO.NET 結構描述資料列集列舉值，反覆運算在 Excel 活頁簿檔案中的所有資料表 (也就是，工作表與具名範圍)，以代替使用指令碼工作將 Excel 資料表清單蒐集到陣列中的方式。</span><span class="sxs-lookup"><span data-stu-id="f199d-216">Instead of using a Script task to gather a list of Excel tables into an array, you can also use the ForEach ADO.NET Schema Rowset Enumerator to iterate over all the tables (that is, worksheets and named ranges) in an Excel workbook file.</span></span> <span data-ttu-id="f199d-217">如需詳細資訊，請參閱[使用 Foreach 迴圈容器來執行 Excel 檔案和資料表迴圈](../control-flow/foreach-loop-container.md)。</span><span class="sxs-lookup"><span data-stu-id="f199d-217">For more information, see [Loop through Excel Files and Tables by Using a Foreach Loop Container](../control-flow/foreach-loop-container.md).</span></span>  
  
##  <a name="displaying-the-results-of-the-samples"></a><a name="testing"></a><span data-ttu-id="f199d-218">顯示範例的結果</span><span class="sxs-lookup"><span data-stu-id="f199d-218">Displaying the Results of the Samples</span></span>  
 <span data-ttu-id="f199d-219">如果您已在相同封裝中設定此主題中的每個範例，可以將所有的指令碼工作連接至其他顯示所有範例輸出的指令碼工作。</span><span class="sxs-lookup"><span data-stu-id="f199d-219">If you have configured each of the examples in this topic in the same package, you can connect all the Script tasks to an additional Script task that displays the output of all the examples.</span></span>  
  
#### <a name="to-configure-a-script-task-to-display-the-output-of-the-examples-in-this-topic"></a><span data-ttu-id="f199d-220">設定指令碼工作以顯示本主題中的範例輸出</span><span class="sxs-lookup"><span data-stu-id="f199d-220">To configure a Script task to display the output of the examples in this topic</span></span>  
  
1.  <span data-ttu-id="f199d-221">將新指令碼工作新增至套件，並將其名稱變更為 **DisplayResults**。</span><span class="sxs-lookup"><span data-stu-id="f199d-221">Add a new Script task to the package and change its name to **DisplayResults**.</span></span>  
  
2.  <span data-ttu-id="f199d-222">依序連線這四個範例指令碼工作，好讓每個工作在前一個工作順利完成之後接著執行，然後將第四個範例工作連線至 **DisplayResults** 工作。</span><span class="sxs-lookup"><span data-stu-id="f199d-222">Connect each of the four example Script tasks to one another, so that each task runs after the preceding task completes successfully, and connect the fourth example task to the **DisplayResults** task.</span></span>  
  
3.  <span data-ttu-id="f199d-223">開啟 [指令碼工作編輯器]\*\*\*\* 中的 **DisplayResults** 工作。</span><span class="sxs-lookup"><span data-stu-id="f199d-223">Open the **DisplayResults** task in the **Script Task Editor**.</span></span>  
  
4.  <span data-ttu-id="f199d-224">在 [指令碼]\*\*\*\* 索引標籤上，按一下 **ReadOnlyVariables** 並使用下列其中一個方法，新增[設定套件以測試範例](#configuring)中的所有七個變數：</span><span class="sxs-lookup"><span data-stu-id="f199d-224">On the **Script** tab, click **ReadOnlyVariables** and use one of the following methods to add all seven variables listed in [Configuring a Package to Test the Samples](#configuring):</span></span>  
  
    -   <span data-ttu-id="f199d-225">輸入每個變數名稱，並以逗號分隔。</span><span class="sxs-lookup"><span data-stu-id="f199d-225">Type the name of each variable separated by commas.</span></span>  
  
         <span data-ttu-id="f199d-226">-或-</span><span class="sxs-lookup"><span data-stu-id="f199d-226">-or-</span></span>  
  
    -   <span data-ttu-id="f199d-227">按一下屬性欄位旁邊的省略號 (**...**) ] 按鈕，然後在 [**選取變數**] 對話方塊中選取變數。</span><span class="sxs-lookup"><span data-stu-id="f199d-227">Click the ellipsis (**...**) button next to the property field, and in the **Select variables** dialog box, selecting the variables.</span></span>  
  
5.  <span data-ttu-id="f199d-228">按一下 [編輯指令碼]\*\*\*\*，以開啟指令碼編輯器。</span><span class="sxs-lookup"><span data-stu-id="f199d-228">Click **Edit Script** to open the script editor.</span></span>  
  
6.  <span data-ttu-id="f199d-229">在指令碼檔案最上方加入 `Imports` 與 `Microsoft.VisualBasic` 命名空間的 `System.Windows.Forms` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="f199d-229">Add `Imports` statements for the `Microsoft.VisualBasic` and `System.Windows.Forms` namespaces at the top of the script file.</span></span>  
  
7.  <span data-ttu-id="f199d-230">加入下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="f199d-230">Add the following code.</span></span>  
  
8.  <span data-ttu-id="f199d-231">執行封裝並檢查在訊息方塊中顯示的結果。</span><span class="sxs-lookup"><span data-stu-id="f199d-231">Run the package and examine the results displayed in a message box.</span></span>  
  
### <a name="code-to-display-the-results"></a><span data-ttu-id="f199d-232">可顯示結果的程式碼</span><span class="sxs-lookup"><span data-stu-id="f199d-232">Code to Display the Results</span></span>  
  
```vb  
Public Class ScriptMain  
  Public Sub Main()  
    Const EOL As String = ControlChars.CrLf  
  
    Dim results As String  
    Dim filesInFolder As String()  
    Dim fileInFolder As String  
    Dim tablesInFile As String()  
    Dim tableInFile As String  
  
    results = _  
      "Final values of variables:" & EOL & _  
      "ExcelFile: " & Dts.Variables("ExcelFile").Value.ToString & EOL & _  
      "ExcelFileExists: " & Dts.Variables("ExcelFileExists").Value.ToString & EOL & _  
      "ExcelTable: " & Dts.Variables("ExcelTable").Value.ToString & EOL & _  
      "ExcelTableExists: " & Dts.Variables("ExcelTableExists").Value.ToString & EOL & _  
      "ExcelFolder: " & Dts.Variables("ExcelFolder").Value.ToString & EOL & _  
      EOL  
  
    results &= "Excel files in folder: " & EOL  
    filesInFolder = DirectCast(Dts.Variables("ExcelFiles").Value, String())  
    For Each fileInFolder In filesInFolder  
      results &= " " & fileInFolder & EOL  
    Next  
    results &= EOL  
  
    results &= "Excel tables in file: " & EOL  
    tablesInFile = DirectCast(Dts.Variables("ExcelTables").Value, String())  
    For Each tableInFile In tablesInFile  
      results &= " " & tableInFile & EOL  
    Next  
  
    MessageBox.Show(results, "Results", MessageBoxButtons.OK, MessageBoxIcon.Information)  
  
    Dts.TaskResult = ScriptResults.Success  
  End Sub  
End Class  
```  
  
```csharp  
public class ScriptMain  
{  
  public void Main()  
        {  
            const string EOL = "\r";  
  
            string results;  
            string[] filesInFolder;  
            //string fileInFolder;  
            string[] tablesInFile;  
            //string tableInFile;  
  
            results = "Final values of variables:" + EOL + "ExcelFile: " + Dts.Variables["ExcelFile"].Value.ToString() + EOL + "ExcelFileExists: " + Dts.Variables["ExcelFileExists"].Value.ToString() + EOL + "ExcelTable: " + Dts.Variables["ExcelTable"].Value.ToString() + EOL + "ExcelTableExists: " + Dts.Variables["ExcelTableExists"].Value.ToString() + EOL + "ExcelFolder: " + Dts.Variables["ExcelFolder"].Value.ToString() + EOL + EOL;  
  
            results += "Excel files in folder: " + EOL;  
            filesInFolder = (string[])(Dts.Variables["ExcelFiles"].Value);  
            foreach (string fileInFolder in filesInFolder)  
            {  
                results += " " + fileInFolder + EOL;  
            }  
            results += EOL;  
  
            results += "Excel tables in file: " + EOL;  
            tablesInFile = (string[])(Dts.Variables["ExcelTables"].Value);  
            foreach (string tableInFile in tablesInFile)  
            {  
                results += " " + tableInFile + EOL;  
            }  
  
            MessageBox.Show(results, "Results", MessageBoxButtons.OK, MessageBoxIcon.Information);  
  
            Dts.TaskResult = (int)ScriptResults.Success;  
        }  
}  
```  
  
<span data-ttu-id="f199d-233">![Integration Services 圖示 (小型) ](../media/dts-16.gif "Integration Services 圖示 (小)")會**保持最**新狀態 Integration Services  </span><span class="sxs-lookup"><span data-stu-id="f199d-233">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="f199d-234">若要取得 Microsoft 的最新下載、文件、範例和影片以及社群中的精選解決方案，請瀏覽 MSDN 上的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 頁面：</span><span class="sxs-lookup"><span data-stu-id="f199d-234">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="f199d-235">瀏覽 MSDN 上的 Integration Services 頁面</span><span class="sxs-lookup"><span data-stu-id="f199d-235">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="f199d-236">若要得到這些更新的自動通知，請訂閱該頁面上所提供的 RSS 摘要。</span><span class="sxs-lookup"><span data-stu-id="f199d-236">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f199d-237">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f199d-237">See Also</span></span>  
 <span data-ttu-id="f199d-238">[Excel 連線管理員](../connection-manager/excel-connection-manager.md) </span><span class="sxs-lookup"><span data-stu-id="f199d-238">[Excel Connection Manager](../connection-manager/excel-connection-manager.md) </span></span>  
 [<span data-ttu-id="f199d-239">使用 Foreach 迴圈容器來執行 Excel 檔案和資料表迴圈</span><span class="sxs-lookup"><span data-stu-id="f199d-239">Loop through Excel Files and Tables by Using a Foreach Loop Container</span></span>](../control-flow/foreach-loop-container.md)  
  
  
