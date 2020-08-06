---
title: 使用 Foreach 迴圈容器執行 Excel 檔案和資料表迴圈 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- connections [Integration Services], Excel
- Excel [Integration Services]
- connection managers [Integration Services], Excel
ms.assetid: a5393c1a-cc37-491a-a260-7aad84dbff68
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 51de779b6869d80245302741035e6169aa750c83
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594625"
---
# <a name="loop-through-excel-files-and-tables-by-using-a-foreach-loop-container"></a><span data-ttu-id="46b4b-102">使用 Foreach 迴圈容器來循環使用 Excel 檔案和資料表</span><span class="sxs-lookup"><span data-stu-id="46b4b-102">Loop through Excel Files and Tables by Using a Foreach Loop Container</span></span>
  <span data-ttu-id="46b4b-103">此主題的程序描述如何使用「Foreach 迴圈」容器搭配適當列舉值，循環使用資料夾中的 Excel 活頁簿，或循環使用 Excel 活頁簿中的資料表。</span><span class="sxs-lookup"><span data-stu-id="46b4b-103">The procedures in this topic describe how to loop through the Excel workbooks in a folder, or through the tables in an Excel workbook, by using the Foreach Loop container with the appropriate enumerator.</span></span>  
  
### <a name="to-loop-through-excel-files-by-using-the-foreach-file-enumerator"></a><span data-ttu-id="46b4b-104">使用 Foreach 檔案列舉值循環使用 Excel 檔案</span><span class="sxs-lookup"><span data-stu-id="46b4b-104">To loop through Excel files by using the Foreach File enumerator</span></span>  
  
1.  <span data-ttu-id="46b4b-105">建立字串變數，用以在迴圈的每個反覆運算上接收目前的 Excel 路徑和檔案名稱</span><span class="sxs-lookup"><span data-stu-id="46b4b-105">Create a string variable that will receive the current Excel path and file name on each iteration of the loop.</span></span> <span data-ttu-id="46b4b-106">為了避免驗證問題，請指派有效的 Excel 路徑和檔案名稱當做變數的初始值</span><span class="sxs-lookup"><span data-stu-id="46b4b-106">To avoid validation issues, assign a valid Excel path and file name as the initial value of the variable.</span></span> <span data-ttu-id="46b4b-107">(此程序後面顯示的範例運算式會使用 `ExcelFile`變數名稱)。</span><span class="sxs-lookup"><span data-stu-id="46b4b-107">(The sample expression shown later in this procedure uses the variable name, `ExcelFile`.)</span></span>  
  
2.  <span data-ttu-id="46b4b-108">(選擇性) 建立另一個字串變數，用以保存 Excel 連接字串之 [擴充屬性] 引數的值。</span><span class="sxs-lookup"><span data-stu-id="46b4b-108">Optionally, create another string variable that will hold the value for the Extended Properties argument of the Excel connection string.</span></span> <span data-ttu-id="46b4b-109">這個引數包含一系列的值，這些值指定 Excel 版本並決定第一個資料列是否包含資料行名稱，以及是否使用匯入模式。</span><span class="sxs-lookup"><span data-stu-id="46b4b-109">This argument contains a series of values that specify the Excel version and determine whether the first row contains column names, and whether import mode is used.</span></span> <span data-ttu-id="46b4b-110">(此程序後面顯示的範例運算式會使用變數名稱 `ExtProperties`，以及 "`Excel 8.0;HDR=Yes`" 的初始值)。</span><span class="sxs-lookup"><span data-stu-id="46b4b-110">(The sample expression shown later in this procedure uses the variable name `ExtProperties`, with an initial value of "`Excel 8.0;HDR=Yes`".)</span></span>  
  
     <span data-ttu-id="46b4b-111">如果您沒有針對 [擴充屬性] 引數使用變數，就必須手動將它加入至包含連接字串的運算式。</span><span class="sxs-lookup"><span data-stu-id="46b4b-111">If you do not use a variable for the Extended Properties argument, then you must add it manually to the expression that contains the connection string.</span></span>  
  
3.  <span data-ttu-id="46b4b-112">將「Foreach 迴圈」容器加入至 [**控制流程**] 索引標籤。如需如何設定「Foreach 迴圈」容器的詳細資訊，請參閱[設定 Foreach 迴圈容器](foreach-loop-container.md)。</span><span class="sxs-lookup"><span data-stu-id="46b4b-112">Add a Foreach Loop container to the **Control Flow** tab. For information about how to configure the Foreach Loop Container, see [Configure a Foreach Loop Container](foreach-loop-container.md).</span></span>  
  
4.  <span data-ttu-id="46b4b-113">在 [Foreach 迴圈編輯器] \*\*\*\* 的 [集合]\*\*\*\* 頁面上，選取 Foreach 檔案列舉值、指定 Excel 活頁簿所在位置的資料夾，並指定檔案篩選 (通常是 \*.xls)。</span><span class="sxs-lookup"><span data-stu-id="46b4b-113">On the **Collection** page of the **Foreach Loop Editor**, select the Foreach File enumerator, specify the folder in which the Excel workbooks are located, and specify the file filter (ordinarily \*.xls).</span></span>  
  
5.  <span data-ttu-id="46b4b-114">在 [變數對應]\*\*\*\* 頁面上，將 [索引 0] 對應至使用者自訂的字串變數，該變數將接收迴圈每個反覆運算上目前的 Excel 路徑和檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="46b4b-114">On the **Variable Mapping** page, map Index 0 to a user-defined string variable that will receive the current Excel path and file name on each iteration of the loop.</span></span> <span data-ttu-id="46b4b-115">(此程序後面顯示的範例運算式會使用 `ExcelFile`變數名稱)。</span><span class="sxs-lookup"><span data-stu-id="46b4b-115">(The sample expression shown later in this procedure uses the variable name `ExcelFile`.)</span></span>  
  
6.  <span data-ttu-id="46b4b-116">關閉 [Foreach 迴圈編輯器]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="46b4b-116">Close the **Foreach Loop Editor**.</span></span>  
  
7.  <span data-ttu-id="46b4b-117">如 [加入、刪除或共用封裝中的連線管理員](../add-delete-or-share-a-connection-manager-in-a-package.md)中所述，將 Excel 連線管理員加入封裝。</span><span class="sxs-lookup"><span data-stu-id="46b4b-117">Add an Excel connection manager to the package as described in [Add, Delete, or Share a Connection Manager in a Package](../add-delete-or-share-a-connection-manager-in-a-package.md).</span></span> <span data-ttu-id="46b4b-118">選取現有的 Excel 活頁簿檔案做為要連接的檔案，以避免驗證錯誤。</span><span class="sxs-lookup"><span data-stu-id="46b4b-118">Select an existing Excel workbook file for the connection to avoid validation errors.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="46b4b-119">為了避免在設定使用此 Excel 連線管理員的工作和資料流程元件時發生驗證錯誤，請在 [Excel 連線管理員編輯器]\*\*\*\* 中選取現有的 Excel 活頁簿。</span><span class="sxs-lookup"><span data-stu-id="46b4b-119">To avoid validation errors as you configure tasks and data flow components that use this Excel connection manager, select an existing Excel workbook in the **Excel Connection Manager Editor**.</span></span> <span data-ttu-id="46b4b-120">在設定了 `ConnectionString` 屬性的運算式之後 (如下列步驟所述)，連接管理員就不會在執行階段使用這個活頁簿。</span><span class="sxs-lookup"><span data-stu-id="46b4b-120">The connection manager will not use this workbook at run time after you configure an expression for the `ConnectionString` property as described in the following steps.</span></span> <span data-ttu-id="46b4b-121">在您建立和設定封裝之後，就可以在 [屬性] 視窗中清除 `ConnectionString` 屬性的值。</span><span class="sxs-lookup"><span data-stu-id="46b4b-121">After you create and configure the package, you can clear the value of the `ConnectionString` property in the Properties window.</span></span> <span data-ttu-id="46b4b-122">不過，如果您要清除這個值，除非執行「ForEach 迴圈」，否則 Excel 連接管理員的連接字串屬性將不再有效。</span><span class="sxs-lookup"><span data-stu-id="46b4b-122">However, if you clear this value, the connection string property of the Excel connection manager is no longer valid until the Foreach Loop runs.</span></span> <span data-ttu-id="46b4b-123">因此，您必須將使用連接管理員的工作或封裝的 `DelayValidation` 屬性設為 `True`，以避免驗證錯誤。</span><span class="sxs-lookup"><span data-stu-id="46b4b-123">Therefore you must set the `DelayValidation` property to `True` on the tasks in which the connection manager is used, or on the package, to avoid validation errors.</span></span>  
    >   
    >  <span data-ttu-id="46b4b-124">您也必須將 `False` 的預設值用於 Excel 連接管理員的 `RetainSameConnection` 屬性。</span><span class="sxs-lookup"><span data-stu-id="46b4b-124">You must also use the default value of `False` for the `RetainSameConnection` property of the Excel connection manager.</span></span> <span data-ttu-id="46b4b-125">如果您將此值變更為 `True`，迴圈的每個反覆運算都會繼續開啟第一個 Excel 活頁簿。</span><span class="sxs-lookup"><span data-stu-id="46b4b-125">If you change this value to `True`, each iteration of the loop will continue to open the first Excel workbook.</span></span>  
  
8.  <span data-ttu-id="46b4b-126">選取新的 Excel 連線管理員，在 [屬性] 視窗中按一下 **Expressions** 屬性，然後按一下省略符號。</span><span class="sxs-lookup"><span data-stu-id="46b4b-126">Select the new Excel connection manager, click the **Expressions** property in the Properties window, and then click the ellipsis.</span></span>  
  
9. <span data-ttu-id="46b4b-127">在 [**屬性運算式編輯器**] 中，選取 `ConnectionString` 屬性，然後按一下省略號。</span><span class="sxs-lookup"><span data-stu-id="46b4b-127">In the **Property Expressions Editor**, select the `ConnectionString` property, and then click the ellipsis.</span></span>  
  
10. <span data-ttu-id="46b4b-128">在「運算式產生器」中，輸入下列運算式：</span><span class="sxs-lookup"><span data-stu-id="46b4b-128">In the Expression Builder, enter the following expression:</span></span>  
  
    ```  
    "Provider=Microsoft.Jet.OLEDB.4.0;Data Source=" +  @[User::ExcelFile] + ";Extended Properties=\"" + @[User::ExtProperties] + "\""  
    ```  
  
     <span data-ttu-id="46b4b-129">請注意，逸出字元 "\\" 是用來逸出括住 [擴充屬性] 引數之值的內部雙引號。</span><span class="sxs-lookup"><span data-stu-id="46b4b-129">Note the use of the escape character "\\" to escape the inner quotation marks required around the value of the Extended Properties argument.</span></span>  
  
     <span data-ttu-id="46b4b-130">[擴充屬性] 引數不是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="46b4b-130">The Extended Properties argument is not optional.</span></span> <span data-ttu-id="46b4b-131">如果您沒有使用變數來包含其值，就必須手動將它加入至運算式，如 Excel 2003 檔案的下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="46b4b-131">If you do not use a variable to contain its value, then you must add it manually to the expression, as in the following example for an Excel 2003 file:</span></span>  
  
    ```  
    "Provider=Microsoft.Jet.OLEDB.4.0;Data Source=" +  @[User::ExcelFile] + ";Extended Properties=Excel 8.0"  
    ```  
  
11. <span data-ttu-id="46b4b-132">在「Foreach 迴圈」容器中建立工作，以便使用 Excel 連接管理員在符合指定之檔案位置和模式的每個 Excel 活頁簿上執行相同的作業。</span><span class="sxs-lookup"><span data-stu-id="46b4b-132">Create tasks in the Foreach Loop container that use the Excel connection manager to perform the same operations on each Excel workbook that matches the specified file location and pattern.</span></span>  
  
### <a name="to-loop-through-excel-tables-by-using-the-foreach-adonet-schema-rowset-enumerator"></a><span data-ttu-id="46b4b-133">使用 Foreach ADO.NET 結構描述資料列集列舉值來循環使用 Excel 資料表</span><span class="sxs-lookup"><span data-stu-id="46b4b-133">To loop through Excel tables by using the Foreach ADO.NET Schema Rowset enumerator</span></span>  
  
1.  <span data-ttu-id="46b4b-134">建立會使用 Microsoft Jet OLE DB 提供者連接到 Excel 活頁簿之 ADO.NET 連接管理員。</span><span class="sxs-lookup"><span data-stu-id="46b4b-134">Create an ADO.NET connection manager that uses the Microsoft Jet OLE DB Provider to connect to an Excel workbook.</span></span> <span data-ttu-id="46b4b-135">在 [連線管理員]\*\*\*\* 對話方塊的 [全部] 頁面上，確定您輸入 Excel 8.0 做為 Extended Properties 屬性的值。</span><span class="sxs-lookup"><span data-stu-id="46b4b-135">On the All page of the **Connection Manager** dialog box, make sure that you enter Excel 8.0 as the value of the Extended Properties property.</span></span> <span data-ttu-id="46b4b-136">如需詳細資訊，請參閱 [加入、刪除或共用封裝中的連線管理員](../add-delete-or-share-a-connection-manager-in-a-package.md)。</span><span class="sxs-lookup"><span data-stu-id="46b4b-136">For more information, see [Add, Delete, or Share a Connection Manager in a Package](../add-delete-or-share-a-connection-manager-in-a-package.md).</span></span>  
  
2.  <span data-ttu-id="46b4b-137">建立會接收迴圈每個反覆運算上目前資料表名稱的字串變數。</span><span class="sxs-lookup"><span data-stu-id="46b4b-137">Create a string variable that will receive the name of the current table on each iteration of the loop.</span></span>  
  
3.  <span data-ttu-id="46b4b-138">將「Foreach 迴圈」容器加入至 [**控制流程**] 索引標籤。如需如何設定「Foreach 迴圈」容器的詳細資訊，請參閱[設定 Foreach 迴圈容器](foreach-loop-container.md)。</span><span class="sxs-lookup"><span data-stu-id="46b4b-138">Add a Foreach Loop container to the **Control Flow** tab. For information about how to configure the Foreach Loop container, see [Configure a Foreach Loop Container](foreach-loop-container.md).</span></span>  
  
4.  <span data-ttu-id="46b4b-139">在 [Foreach 迴圈編輯器]\*\*\*\* 的 [集合]\*\*\*\* 頁面上，選取 [Foreach ADO.NET 結構描述資料列集] 列舉值。</span><span class="sxs-lookup"><span data-stu-id="46b4b-139">On the **Collection** page of the **Foreach Loop Editor**, select the Foreach ADO.NET Schema Rowset enumerator.</span></span>  
  
5.  <span data-ttu-id="46b4b-140">選取您先前建立的 ADO.NET 連線管理員作為 [連接]\*\*\*\* 的值。</span><span class="sxs-lookup"><span data-stu-id="46b4b-140">As the value of **Connection**, select the ADO.NET connection manager that you created previously.</span></span>  
  
6.  <span data-ttu-id="46b4b-141">選取 [資料表] 作為 [結構描述]\*\*\*\* 的值。</span><span class="sxs-lookup"><span data-stu-id="46b4b-141">As the value of **Schema**, select Tables.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="46b4b-142">Excel 活頁簿中資料表清單包含活頁簿 (具有 $ 後置詞) 及具名範圍。</span><span class="sxs-lookup"><span data-stu-id="46b4b-142">The list of tables in an Excel workbook includes both worksheets (which have the $ suffix) and named ranges.</span></span> <span data-ttu-id="46b4b-143">如果您必須只篩選清單中的活頁簿或具名範圍，必須在指令碼工作中寫入這個用途的自訂程式碼。</span><span class="sxs-lookup"><span data-stu-id="46b4b-143">If you have to filter the list for only worksheets or only named ranges, you may have to write custom code in a Script task for this purpose.</span></span> <span data-ttu-id="46b4b-144">如需詳細資訊，請參閱 [以指令碼工作處理 Excel 檔案](script-task.md)。</span><span class="sxs-lookup"><span data-stu-id="46b4b-144">For more information, see [Working with Excel Files with the Script Task](script-task.md).</span></span>  
  
7.  <span data-ttu-id="46b4b-145">在 [變數對應]\*\*\*\* 頁面上，將 [索引 2] 對應至先前建立的字串變數，以保留目前資料表的名稱。</span><span class="sxs-lookup"><span data-stu-id="46b4b-145">On the **Variable Mappings** page, map Index 2 to the string variable created earlier to hold the name of the current table.</span></span>  
  
8.  <span data-ttu-id="46b4b-146">關閉 [Foreach 迴圈編輯器]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="46b4b-146">Close the **Foreach Loop Editor**.</span></span>  
  
9. <span data-ttu-id="46b4b-147">在「Foreach 迴圈」容器中建立工作，以便使用 Excel 連接管理員在指定之活頁簿中的每個 Excel 資料表上執行相同的作業。</span><span class="sxs-lookup"><span data-stu-id="46b4b-147">Create tasks in the Foreach Loop container that use the Excel connection manager to perform the same operations on each Excel table in the specified workbook.</span></span> <span data-ttu-id="46b4b-148">如果您使用指令碼工作檢查列舉的資料表名稱，或者用來處理每個資料表，請記得將字串變數加入指令碼工作的 ReadOnlyVariables 屬性中。</span><span class="sxs-lookup"><span data-stu-id="46b4b-148">If you use a Script Task to examine the enumerated table name or to work with each table, remember to add the string variable to the ReadOnlyVariables property of the Script task.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46b4b-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="46b4b-149">See Also</span></span>  
 <span data-ttu-id="46b4b-150">[使用 SQL Server Integration Services (SSIS 從 excel 匯入資料或將資料匯出至 excel) ](../load-data-to-from-excel-with-ssis.md) [設定 Foreach 迴圈容器](foreach-loop-container.md) </span><span class="sxs-lookup"><span data-stu-id="46b4b-150">[Import data from Excel or export data to Excel with SQL Server Integration Services (SSIS)](../load-data-to-from-excel-with-ssis.md) [Configure a Foreach Loop Container](foreach-loop-container.md) </span></span>  
 <span data-ttu-id="46b4b-151">[新增或變更屬性運算式](../expressions/add-or-change-a-property-expression.md) </span><span class="sxs-lookup"><span data-stu-id="46b4b-151">[Add or Change a Property Expression](../expressions/add-or-change-a-property-expression.md) </span></span>  
 <span data-ttu-id="46b4b-152">[Excel 連線管理員](../connection-manager/excel-connection-manager.md) </span><span class="sxs-lookup"><span data-stu-id="46b4b-152">[Excel Connection Manager](../connection-manager/excel-connection-manager.md) </span></span>  
 <span data-ttu-id="46b4b-153">[Excel 來源](../data-flow/excel-source.md) </span><span class="sxs-lookup"><span data-stu-id="46b4b-153">[Excel Source](../data-flow/excel-source.md) </span></span>  
 <span data-ttu-id="46b4b-154">[Excel 目的地](../data-flow/excel-destination.md) </span><span class="sxs-lookup"><span data-stu-id="46b4b-154">[Excel Destination](../data-flow/excel-destination.md) </span></span>  
 [<span data-ttu-id="46b4b-155">以指令碼工作處理 Excel 檔案</span><span class="sxs-lookup"><span data-stu-id="46b4b-155">Working with Excel Files with the Script Task</span></span>](script-task.md)  
  
  
