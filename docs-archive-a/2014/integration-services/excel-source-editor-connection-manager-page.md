---
title: Excel 來源編輯器 (連線管理員頁面) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.excelsourceadapter.connection.f1
helpviewer_keywords:
- Excel Source Editor
ms.assetid: 428e04e0-ad98-45d0-8345-12ec1b67b2eb
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 3285b5c8b14016b91005af79542e3e2f9b6559b6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596797"
---
# <a name="excel-source-editor-connection-manager-page"></a><span data-ttu-id="33682-102">Excel 來源編輯器 (連接管理員頁面)</span><span class="sxs-lookup"><span data-stu-id="33682-102">Excel Source Editor (Connection Manager Page)</span></span>
  <span data-ttu-id="33682-103">使用 **[Excel 來源編輯器]** 對話方塊的 **[連接管理員]** 節點，以選取來源要使用的 [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] 活頁簿。</span><span class="sxs-lookup"><span data-stu-id="33682-103">Use the **Connection Manager** node of the **Excel Source Editor** dialog box to select the [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] workbook for the source to use.</span></span> <span data-ttu-id="33682-104">Excel 來源會從工作表或現有活頁簿的具名範圍中讀取資料。</span><span class="sxs-lookup"><span data-stu-id="33682-104">The Excel source reads data from a worksheet or named range in an existing workbook.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="33682-105">[Excel `CommandTimeout` **來源編輯器**] 中無法使用 excel 來源的屬性，但是可以使用 [**進階編輯器**] 來設定它。</span><span class="sxs-lookup"><span data-stu-id="33682-105">The `CommandTimeout` property of the Excel source is not available in the **Excel Source Editor**, but can be set by using the **Advanced Editor**.</span></span> <span data-ttu-id="33682-106">如需有關這個屬性的詳細資訊，請參閱＜ [Excel Custom Properties](data-flow/excel-custom-properties.md)＞的＜Excel 來源＞一節。</span><span class="sxs-lookup"><span data-stu-id="33682-106">For more information on this property, see the Excel Source section of [Excel Custom Properties](data-flow/excel-custom-properties.md).</span></span>  
  
 <span data-ttu-id="33682-107">若要深入了解 Excel 來源，請參閱＜ [Excel Source](data-flow/excel-source.md)＞。</span><span class="sxs-lookup"><span data-stu-id="33682-107">To learn more about the Excel source, see [Excel Source](data-flow/excel-source.md).</span></span>  
  
## <a name="static-options"></a><span data-ttu-id="33682-108">靜態選項</span><span class="sxs-lookup"><span data-stu-id="33682-108">Static Options</span></span>  
 <span data-ttu-id="33682-109">**[無快取]**</span><span class="sxs-lookup"><span data-stu-id="33682-109">**OLE DB connection manager**</span></span>  
 <span data-ttu-id="33682-110">從清單中選取現有的 Excel 連線管理員，或按一下 [新增]\*\*\*\* 建立新的連線管理員。</span><span class="sxs-lookup"><span data-stu-id="33682-110">Select an existing Excel connection manager from the list, or create a new connection by clicking **New**.</span></span>  
  
 <span data-ttu-id="33682-111">**新增**</span><span class="sxs-lookup"><span data-stu-id="33682-111">**New**</span></span>  
 <span data-ttu-id="33682-112">使用 [Excel 連線管理員]\*\*\*\* 對話方塊來建立新的連線管理員。</span><span class="sxs-lookup"><span data-stu-id="33682-112">Create a new connection manager by using the **Excel Connection Manager** dialog box.</span></span>  
  
 <span data-ttu-id="33682-113">**資料存取模式**</span><span class="sxs-lookup"><span data-stu-id="33682-113">**Data access mode**</span></span>  
 <span data-ttu-id="33682-114">從來源中指定選取資料的方法。</span><span class="sxs-lookup"><span data-stu-id="33682-114">Specify the method for selecting data from the source.</span></span>  
  
|<span data-ttu-id="33682-115">值</span><span class="sxs-lookup"><span data-stu-id="33682-115">Value</span></span>|<span data-ttu-id="33682-116">描述</span><span class="sxs-lookup"><span data-stu-id="33682-116">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="33682-117">資料表或檢視</span><span class="sxs-lookup"><span data-stu-id="33682-117">Table or view</span></span>|<span data-ttu-id="33682-118">從工作表或 Excel 檔案的具名範圍中擷取資料。</span><span class="sxs-lookup"><span data-stu-id="33682-118">Retrieve data from a worksheet or named range in the Excel file.</span></span>|  
|<span data-ttu-id="33682-119">資料表名稱或檢視名稱變數</span><span class="sxs-lookup"><span data-stu-id="33682-119">Table name or view name variable</span></span>|<span data-ttu-id="33682-120">在變數中指定工作表或範圍名稱。</span><span class="sxs-lookup"><span data-stu-id="33682-120">Specify the worksheet or range name in a variable.</span></span><br /><br /> <span data-ttu-id="33682-121">**相關資訊：** [在套件中使用變數](../../2014/integration-services/use-variables-in-packages.md)</span><span class="sxs-lookup"><span data-stu-id="33682-121">**Related information:** [Use Variables in Packages](../../2014/integration-services/use-variables-in-packages.md)</span></span>|  
|<span data-ttu-id="33682-122">SQL (命令)</span><span class="sxs-lookup"><span data-stu-id="33682-122">SQL command</span></span>|<span data-ttu-id="33682-123">使用 SQL 查詢從 Excel 檔案中擷取資料。</span><span class="sxs-lookup"><span data-stu-id="33682-123">Retrieve data from the Excel file by using a SQL query.</span></span> <span data-ttu-id="33682-124">如需有關查詢語法的詳細資訊，請參閱＜ [Excel Source](data-flow/excel-source.md)＞。</span><span class="sxs-lookup"><span data-stu-id="33682-124">For information about query syntax, see [Excel Source](data-flow/excel-source.md).</span></span>|  
|<span data-ttu-id="33682-125">來自變數的 SQL 命令</span><span class="sxs-lookup"><span data-stu-id="33682-125">SQL command from variable</span></span>|<span data-ttu-id="33682-126">在變數中指定 SQL 查詢文字。</span><span class="sxs-lookup"><span data-stu-id="33682-126">Specify the SQL query text in a variable.</span></span>|  
  
 <span data-ttu-id="33682-127">**預覽**</span><span class="sxs-lookup"><span data-stu-id="33682-127">**Preview**</span></span>  
 <span data-ttu-id="33682-128">使用 [資料檢視]  對話方塊來預覽結果。</span><span class="sxs-lookup"><span data-stu-id="33682-128">Preview results by using the **Data View** dialog box.</span></span> <span data-ttu-id="33682-129">預覽最多可顯示 200 個資料列。</span><span class="sxs-lookup"><span data-stu-id="33682-129">Preview can display up to 200 rows.</span></span>  
  
## <a name="data-access-mode-dynamic-options"></a><span data-ttu-id="33682-130">資料存取模式動態選項</span><span class="sxs-lookup"><span data-stu-id="33682-130">Data Access Mode Dynamic Options</span></span>  
  
### <a name="data-access-mode--table-or-view"></a><span data-ttu-id="33682-131">資料存取模式 = 資料表或檢視</span><span class="sxs-lookup"><span data-stu-id="33682-131">Data access mode = Table or view</span></span>  
 <span data-ttu-id="33682-132">**Excel 工作表的名稱**</span><span class="sxs-lookup"><span data-stu-id="33682-132">**Name of the Excel sheet**</span></span>  
 <span data-ttu-id="33682-133">從 Excel 活頁簿的可用工作表或具名範圍清單中，選取工作表或具名範圍的名稱。</span><span class="sxs-lookup"><span data-stu-id="33682-133">Select the name of the worksheet or named range from a list of those available in the Excel workbook.</span></span>  
  
### <a name="data-access-mode--table-name-or-view-name-variable"></a><span data-ttu-id="33682-134">資料存取模式 = 資料表名稱或檢視名稱變數</span><span class="sxs-lookup"><span data-stu-id="33682-134">Data access mode = Table name or view name variable</span></span>  
 <span data-ttu-id="33682-135">**變數名稱**</span><span class="sxs-lookup"><span data-stu-id="33682-135">**Variable name**</span></span>  
 <span data-ttu-id="33682-136">選取包含工作表名稱或具名範圍的變數。</span><span class="sxs-lookup"><span data-stu-id="33682-136">Select the variable that contains the name of the worksheet or named range.</span></span>  
  
### <a name="data-access-mode--sql-command"></a><span data-ttu-id="33682-137">資料存取模式 = SQL 命令</span><span class="sxs-lookup"><span data-stu-id="33682-137">Data access mode = SQL command</span></span>  
 <span data-ttu-id="33682-138">**SQL 命令文字**</span><span class="sxs-lookup"><span data-stu-id="33682-138">**SQL command text**</span></span>  
 <span data-ttu-id="33682-139">輸入 SQL 查詢的文字，按一下 [建立查詢]\*\*\*\* 建立查詢，或按一下 [瀏覽]\*\*\*\* 瀏覽至包含查詢文字的檔案。</span><span class="sxs-lookup"><span data-stu-id="33682-139">Enter the text of a SQL query, build the query by clicking **Build Query**, or browse to the file that contains the query text by clicking **Browse**.</span></span>  
  
 <span data-ttu-id="33682-140">**參數**</span><span class="sxs-lookup"><span data-stu-id="33682-140">**Parameters**</span></span>  
 <span data-ttu-id="33682-141">如果您所輸入的參數化查詢使用 ?</span><span class="sxs-lookup"><span data-stu-id="33682-141">If you have entered a parameterized query by using ?</span></span> <span data-ttu-id="33682-142">做為查詢文字中的參數預留位置，請使用 **[設定查詢參數]** 對話方塊，將查詢輸入參數對應到封裝變數。</span><span class="sxs-lookup"><span data-stu-id="33682-142">as a parameter placeholder in the query text, use the **Set Query Parameters** dialog box to map query input parameters to package variables.</span></span>  
  
 <span data-ttu-id="33682-143">**建立查詢**</span><span class="sxs-lookup"><span data-stu-id="33682-143">**Build query**</span></span>  
 <span data-ttu-id="33682-144">使用 [查詢產生器]  對話方塊，以視覺化的方式來建構 SQL 查詢。</span><span class="sxs-lookup"><span data-stu-id="33682-144">Use the **Query Builder** dialog box to construct the SQL query visually.</span></span>  
  
 <span data-ttu-id="33682-145">**瀏覽**</span><span class="sxs-lookup"><span data-stu-id="33682-145">**Browse**</span></span>  
 <span data-ttu-id="33682-146">使用 [開啟]  對話方塊來找出包含 SQL 查詢文字的檔案。</span><span class="sxs-lookup"><span data-stu-id="33682-146">Use the **Open** dialog box to locate the file that contains the text of the SQL query.</span></span>  
  
 <span data-ttu-id="33682-147">**剖析查詢**</span><span class="sxs-lookup"><span data-stu-id="33682-147">**Parse query**</span></span>  
 <span data-ttu-id="33682-148">請確認查詢文字的語法。</span><span class="sxs-lookup"><span data-stu-id="33682-148">Verify the syntax of the query text.</span></span>  
  
### <a name="data-access-mode--sql-command-from-variable"></a><span data-ttu-id="33682-149">資料存取模式 = 來自變數的 SQL 命令</span><span class="sxs-lookup"><span data-stu-id="33682-149">Data access mode = SQL command from variable</span></span>  
 <span data-ttu-id="33682-150">**變數名稱**</span><span class="sxs-lookup"><span data-stu-id="33682-150">**Variable name**</span></span>  
 <span data-ttu-id="33682-151">選取包含 SQL 查詢文字的變數。</span><span class="sxs-lookup"><span data-stu-id="33682-151">Select the variable that contains the text of the SQL query.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33682-152">另請參閱</span><span class="sxs-lookup"><span data-stu-id="33682-152">See Also</span></span>  
 <span data-ttu-id="33682-153">[Integration Services 錯誤和訊息參考](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="33682-153">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="33682-154">[Excel 來源編輯器 &#40;資料行] 頁面&#41;](../../2014/integration-services/excel-source-editor-columns-page.md) </span><span class="sxs-lookup"><span data-stu-id="33682-154">[Excel Source Editor &#40;Columns Page&#41;](../../2014/integration-services/excel-source-editor-columns-page.md) </span></span>  
 <span data-ttu-id="33682-155">[Excel 來源編輯器 &#40;錯誤輸出頁面&#41;](../../2014/integration-services/excel-source-editor-error-output-page.md) </span><span class="sxs-lookup"><span data-stu-id="33682-155">[Excel Source Editor &#40;Error Output Page&#41;](../../2014/integration-services/excel-source-editor-error-output-page.md) </span></span>  
 <span data-ttu-id="33682-156">[Excel 連線管理員](connection-manager/excel-connection-manager.md) </span><span class="sxs-lookup"><span data-stu-id="33682-156">[Excel Connection Manager](connection-manager/excel-connection-manager.md) </span></span>  
 [<span data-ttu-id="33682-157">使用 Foreach 迴圈容器來執行 Excel 檔案和資料表迴圈</span><span class="sxs-lookup"><span data-stu-id="33682-157">Loop through Excel Files and Tables by Using a Foreach Loop Container</span></span>](control-flow/foreach-loop-container.md)  
  
  
