---
title: Excel 目的地編輯器 (連線管理員頁面) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.exceldestadapter.connection.f1
helpviewer_keywords:
- Excel Destination Editor
ms.assetid: fc13f725-963c-488e-91e2-20627133e842
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1556bf713c49aac31f1cc1cd624336f10dbf832f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596813"
---
# <a name="excel-destination-editor-connection-manager-page"></a><span data-ttu-id="1679e-102">Excel 目的地編輯器 (連接管理員頁面)</span><span class="sxs-lookup"><span data-stu-id="1679e-102">Excel Destination Editor (Connection Manager Page)</span></span>
  <span data-ttu-id="1679e-103">使用 **[Excel 目的地編輯器]** 對話方塊的 **[連接管理員]** 頁面，來指定資料來源資訊，以及預覽結果。</span><span class="sxs-lookup"><span data-stu-id="1679e-103">Use the **Connection Manager** page of the **Excel Destination Editor** dialog box to specify data source information, and to preview the results.</span></span> <span data-ttu-id="1679e-104">Excel 目的地會將資料載入 [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] 活頁簿中的工作表或具名範圍。</span><span class="sxs-lookup"><span data-stu-id="1679e-104">The Excel destination loads data into a worksheet or a named range in a [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] workbook.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1679e-105">在 `CommandTimeout` [ **Excel 目的地編輯器**] 中無法使用 excel 目的地的屬性，但是可以使用 [**進階編輯器**] 來設定它。</span><span class="sxs-lookup"><span data-stu-id="1679e-105">The `CommandTimeout` property of the Excel destination is not available in the **Excel Destination Editor**, but can be set by using the **Advanced Editor**.</span></span> <span data-ttu-id="1679e-106">此外，特定的快速載入選項僅適用于**進階編輯器**。</span><span class="sxs-lookup"><span data-stu-id="1679e-106">In addition, certain Fast Load options are available only in the **Advanced Editor**.</span></span> <span data-ttu-id="1679e-107">如需有關這個屬性的詳細資訊，請參閱＜ [Excel Custom Properties](data-flow/excel-custom-properties.md)＞的＜Excel 目的地＞一節。</span><span class="sxs-lookup"><span data-stu-id="1679e-107">For more information on these properties, see the Excel Destination section of [Excel Custom Properties](data-flow/excel-custom-properties.md).</span></span>  
  
 <span data-ttu-id="1679e-108">若要深入了解 Excel 目的地，請參閱＜ [Excel Destination](data-flow/excel-destination.md)＞。</span><span class="sxs-lookup"><span data-stu-id="1679e-108">To learn more about the Excel destination, see [Excel Destination](data-flow/excel-destination.md).</span></span>  
  
## <a name="static-options"></a><span data-ttu-id="1679e-109">靜態選項</span><span class="sxs-lookup"><span data-stu-id="1679e-109">Static Options</span></span>  
 <span data-ttu-id="1679e-110">**Excel 連線管理員**</span><span class="sxs-lookup"><span data-stu-id="1679e-110">**Excel connection manager**</span></span>  
 <span data-ttu-id="1679e-111">從清單中選取現有的 Excel 連線管理員，或按一下 [新增]\*\*\*\* 建立新的連線管理員。</span><span class="sxs-lookup"><span data-stu-id="1679e-111">Select an existing Excel connection manager from the list, or create a new connection by clicking **New**.</span></span>  
  
 <span data-ttu-id="1679e-112">**新增**</span><span class="sxs-lookup"><span data-stu-id="1679e-112">**New**</span></span>  
 <span data-ttu-id="1679e-113">使用 [Excel 連線管理員]\*\*\*\* 對話方塊來建立新的連線管理員。</span><span class="sxs-lookup"><span data-stu-id="1679e-113">Create a new connection manager by using the **Excel Connection Manager** dialog box.</span></span>  
  
 <span data-ttu-id="1679e-114">**資料存取模式**</span><span class="sxs-lookup"><span data-stu-id="1679e-114">**Data access mode**</span></span>  
 <span data-ttu-id="1679e-115">從來源中指定選取資料的方法。</span><span class="sxs-lookup"><span data-stu-id="1679e-115">Specify the method for selecting data from the source.</span></span>  
  
|<span data-ttu-id="1679e-116">選項</span><span class="sxs-lookup"><span data-stu-id="1679e-116">Option</span></span>|<span data-ttu-id="1679e-117">描述</span><span class="sxs-lookup"><span data-stu-id="1679e-117">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="1679e-118">資料表或檢視</span><span class="sxs-lookup"><span data-stu-id="1679e-118">Table or view</span></span>|<span data-ttu-id="1679e-119">將資料載入 Excel 資料來源中的工作表或具名範圍。</span><span class="sxs-lookup"><span data-stu-id="1679e-119">Loads data into a worksheet or named range in the Excel data source.</span></span>|  
|<span data-ttu-id="1679e-120">資料表名稱或檢視名稱變數</span><span class="sxs-lookup"><span data-stu-id="1679e-120">Table name or view name variable</span></span>|<span data-ttu-id="1679e-121">在變數中指定工作表或範圍名稱。</span><span class="sxs-lookup"><span data-stu-id="1679e-121">Specify the worksheet or range name in a variable.</span></span><br /><br /> <span data-ttu-id="1679e-122">**相關資訊**：[在套件中使用變數](../../2014/integration-services/use-variables-in-packages.md)</span><span class="sxs-lookup"><span data-stu-id="1679e-122">**Related information**: [Use Variables in Packages](../../2014/integration-services/use-variables-in-packages.md)</span></span>|  
|<span data-ttu-id="1679e-123">SQL (命令)</span><span class="sxs-lookup"><span data-stu-id="1679e-123">SQL command</span></span>|<span data-ttu-id="1679e-124">使用 SQL 查詢將資料載入 Excel 目的地。</span><span class="sxs-lookup"><span data-stu-id="1679e-124">Load data into the Excel destination by using an SQL query.</span></span>|  
  
 <span data-ttu-id="1679e-125">**Excel 工作表的名稱**</span><span class="sxs-lookup"><span data-stu-id="1679e-125">**Name of the Excel sheet**</span></span>  
 <span data-ttu-id="1679e-126">從下拉式清單中選取 Excel 目的地。</span><span class="sxs-lookup"><span data-stu-id="1679e-126">Select the excel destination from the drop-down list.</span></span> <span data-ttu-id="1679e-127">如果此清單為空，請按一下 **[新增]**。</span><span class="sxs-lookup"><span data-stu-id="1679e-127">If the list is empty, click **New**.</span></span>  
  
 <span data-ttu-id="1679e-128">**新增**</span><span class="sxs-lookup"><span data-stu-id="1679e-128">**New**</span></span>  
 <span data-ttu-id="1679e-129">按一下 [新增]\*\*\*\* 以啟動 [建立工資料表]\*\*\*\* 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="1679e-129">Click **New** to launch the **Create Table** dialog box.</span></span> <span data-ttu-id="1679e-130">按一下 **[確定]** 時，對話方塊會建立 **[Excel 連接管理員]** 指向的 Excel 檔案。</span><span class="sxs-lookup"><span data-stu-id="1679e-130">When you click **OK**, the dialog box creates the excel file that the **Excel Connection Manager** points to.</span></span>  
  
 <span data-ttu-id="1679e-131">**檢視現有的資料**</span><span class="sxs-lookup"><span data-stu-id="1679e-131">**View Existing Data**</span></span>  
 <span data-ttu-id="1679e-132">使用 [預覽查詢結果]  對話方塊來預覽結果。</span><span class="sxs-lookup"><span data-stu-id="1679e-132">Preview results by using the **Preview Query Results** dialog box.</span></span> <span data-ttu-id="1679e-133">預覽最多可顯示 200 個資料列。</span><span class="sxs-lookup"><span data-stu-id="1679e-133">Preview can display up to 200 rows.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="1679e-134"> 如果您選取的 **[Excel 連接管理員]** 指向不存在的 Excel 檔，則在您按一下此按鈕時將看到一條錯誤消息。</span><span class="sxs-lookup"><span data-stu-id="1679e-134">If the **Excel connection manager** you selected points to an excel file that does not exist, you will see an error message when you click this button.</span></span>  
  
## <a name="data-access-mode-dynamic-options"></a><span data-ttu-id="1679e-135">資料存取模式動態選項</span><span class="sxs-lookup"><span data-stu-id="1679e-135">Data Access Mode Dynamic Options</span></span>  
  
### <a name="data-access-mode--table-or-view"></a><span data-ttu-id="1679e-136">資料存取模式 = 資料表或檢視</span><span class="sxs-lookup"><span data-stu-id="1679e-136">Data access mode = Table or view</span></span>  
 <span data-ttu-id="1679e-137">**Excel 工作表的名稱**</span><span class="sxs-lookup"><span data-stu-id="1679e-137">**Name of the Excel sheet**</span></span>  
 <span data-ttu-id="1679e-138">從資料來源裡可用的資訊清單中，選取工作表或具名範圍的名稱。</span><span class="sxs-lookup"><span data-stu-id="1679e-138">Select the name of the worksheet or named range from a list of those available in the data source.</span></span>  
  
### <a name="data-access-mode--table-name-or-view-name-variable"></a><span data-ttu-id="1679e-139">資料存取模式 = 資料表名稱或檢視名稱變數</span><span class="sxs-lookup"><span data-stu-id="1679e-139">Data access mode = Table name or view name variable</span></span>  
 <span data-ttu-id="1679e-140">**變數名稱**</span><span class="sxs-lookup"><span data-stu-id="1679e-140">**Variable name**</span></span>  
 <span data-ttu-id="1679e-141">選取包含工作表名稱或具名範圍的變數。</span><span class="sxs-lookup"><span data-stu-id="1679e-141">Select the variable that contains the name of the worksheet or named range.</span></span>  
  
### <a name="data-access-mode--sql-command"></a><span data-ttu-id="1679e-142">資料存取模式 = SQL 命令</span><span class="sxs-lookup"><span data-stu-id="1679e-142">Data access mode = SQL command</span></span>  
 <span data-ttu-id="1679e-143">**SQL 命令文字**</span><span class="sxs-lookup"><span data-stu-id="1679e-143">**SQL command text**</span></span>  
 <span data-ttu-id="1679e-144">輸入 SQL 查詢的文字，按一下 [建立查詢]\*\*\*\* 來建立查詢，或是按一下 [瀏覽]\*\*\*\* 以找出包含查詢文字的檔案。</span><span class="sxs-lookup"><span data-stu-id="1679e-144">Enter the text of an SQL query, build the query by clicking **Build Query**, or locate the file that contains the query text by clicking **Browse**.</span></span>  
  
 <span data-ttu-id="1679e-145">**建立查詢**</span><span class="sxs-lookup"><span data-stu-id="1679e-145">**Build Query**</span></span>  
 <span data-ttu-id="1679e-146">使用 [查詢產生器]  對話方塊，以視覺化的方式來建構 SQL 查詢。</span><span class="sxs-lookup"><span data-stu-id="1679e-146">Use the **Query Builder** dialog box to construct the SQL query visually.</span></span>  
  
 <span data-ttu-id="1679e-147">**瀏覽**</span><span class="sxs-lookup"><span data-stu-id="1679e-147">**Browse**</span></span>  
 <span data-ttu-id="1679e-148">使用 [開啟]  對話方塊來找出包含 SQL 查詢文字的檔案。</span><span class="sxs-lookup"><span data-stu-id="1679e-148">Use the **Open** dialog box to locate the file that contains the text of the SQL query.</span></span>  
  
 <span data-ttu-id="1679e-149">**剖析查詢**</span><span class="sxs-lookup"><span data-stu-id="1679e-149">**Parse Query**</span></span>  
 <span data-ttu-id="1679e-150">請確認查詢文字的語法。</span><span class="sxs-lookup"><span data-stu-id="1679e-150">Verify the syntax of the query text.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1679e-151">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1679e-151">See Also</span></span>  
 <span data-ttu-id="1679e-152">[Integration Services 錯誤和訊息參考](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="1679e-152">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="1679e-153">[[Excel 目的地編輯器 &#40;對應] 頁面&#41;](../../2014/integration-services/excel-destination-editor-mappings-page.md) </span><span class="sxs-lookup"><span data-stu-id="1679e-153">[Excel Destination Editor &#40;Mappings Page&#41;](../../2014/integration-services/excel-destination-editor-mappings-page.md) </span></span>  
 <span data-ttu-id="1679e-154">[Excel 目的地編輯器 &#40;錯誤輸出頁面&#41;](../../2014/integration-services/excel-destination-editor-error-output-page.md) </span><span class="sxs-lookup"><span data-stu-id="1679e-154">[Excel Destination Editor &#40;Error Output Page&#41;](../../2014/integration-services/excel-destination-editor-error-output-page.md) </span></span>  
 [<span data-ttu-id="1679e-155">使用 Foreach 迴圈容器來執行 Excel 檔案和資料表迴圈</span><span class="sxs-lookup"><span data-stu-id="1679e-155">Loop through Excel Files and Tables by Using a Foreach Loop Container</span></span>](control-flow/foreach-loop-container.md)  
  
  
