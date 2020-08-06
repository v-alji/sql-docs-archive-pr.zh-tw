---
title: 使用 CDC 來源擷取變更資料 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 604fbafb-15fa-4d11-8487-77d7b626eed8
author: chugugrace
ms.author: chugu
ms.openlocfilehash: ef981a22e286f519c9b93b3181b47df43321548b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709802"
---
# <a name="extract-change-data-using-the-cdc-source"></a><span data-ttu-id="3c332-102">使用 CDC 來源擷取變更資料</span><span class="sxs-lookup"><span data-stu-id="3c332-102">Extract Change Data Using the CDC Source</span></span>
  <span data-ttu-id="3c332-103">若要加入及設定 CDC 來源，封裝至少必須包含一個資料流程工作及一個 CDC 控制工作。</span><span class="sxs-lookup"><span data-stu-id="3c332-103">To add and configure a CDC source, the package must already include at least one Data Flow task and a CDC Control task.</span></span>  
  
 <span data-ttu-id="3c332-104">如需 CDC 控制工作的詳細資訊，請參閱 [CDC 控制工作](../control-flow/cdc-control-task.md)。</span><span class="sxs-lookup"><span data-stu-id="3c332-104">For more information about the CDC Control task, see [CDC Control Task](../control-flow/cdc-control-task.md).</span></span>  
  
 <span data-ttu-id="3c332-105">如需 CDC 來源的詳細資訊，請參閱 [CDC 來源](cdc-source.md)。</span><span class="sxs-lookup"><span data-stu-id="3c332-105">For more information about the CDC source, see [CDC Source](cdc-source.md).</span></span>  
  
### <a name="to-extract-change-data-using-a-cdc-source"></a><span data-ttu-id="3c332-106">若要使用 CDC 來源擷取變更資料</span><span class="sxs-lookup"><span data-stu-id="3c332-106">To extract change data using a CDC source</span></span>  
  
1.  <span data-ttu-id="3c332-107">在 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]中，開啟包含所需封裝的 [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] 專案。</span><span class="sxs-lookup"><span data-stu-id="3c332-107">In [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], open the [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="3c332-108">在 [方案總管] 中，按兩下封裝加以開啟。</span><span class="sxs-lookup"><span data-stu-id="3c332-108">In the Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="3c332-109">按一下 [資料流程]  索引標籤，然後將 CDC 來源從 [工具箱]  拖曳至設計介面。</span><span class="sxs-lookup"><span data-stu-id="3c332-109">Click the **Data Flow** tab, and then from the **Toolbox**, drag the CDC source to the design surface.</span></span>  
  
4.  <span data-ttu-id="3c332-110">按兩下 CDC 來源。</span><span class="sxs-lookup"><span data-stu-id="3c332-110">Double-click the CDC source.</span></span>  
  
5.  <span data-ttu-id="3c332-111">在 [CDC 來源編輯器]  對話方塊中的 [連線管理員]  頁面上，從清單中選取現有的 ADO.NET 連線管理員，或按一下 [新增]  以建立新的連接。</span><span class="sxs-lookup"><span data-stu-id="3c332-111">In the **CDC Source Editor** dialog box, on the **Connection Manager** page, select an existing ADO.NET connection manager from the list, or click **New** to create a new connection.</span></span> <span data-ttu-id="3c332-112">連接應該指向包含要讀取之變更資料表的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫。</span><span class="sxs-lookup"><span data-stu-id="3c332-112">The connection should be to a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database that contains the change tables to read.</span></span>  
  
6.  <span data-ttu-id="3c332-113">選取您要處理變更的 **CDC 資料表** 。</span><span class="sxs-lookup"><span data-stu-id="3c332-113">Select the **CDC table** where you want to process changes.</span></span>  
  
7.  <span data-ttu-id="3c332-114">選取或輸入包含要讀取之 CDC 資料表的 **CDC 擷取執行個體** 名稱。</span><span class="sxs-lookup"><span data-stu-id="3c332-114">Select or type in the name of the **CDC capture instance** with the CDC table to be read.</span></span>  
  
     <span data-ttu-id="3c332-115">擷取的來源資料表可以具有一個或兩個擷取執行個體，以便透過結構描述變更處理資料表定義的流暢轉換。</span><span class="sxs-lookup"><span data-stu-id="3c332-115">A captured source table can have one or two captured instances to handle seamless transitioning of table definition through schema changes.</span></span> <span data-ttu-id="3c332-116">如果針對所擷取的來源資料表定義了多個擷取執行個體，請在此選取您想要使用的擷取執行個體。</span><span class="sxs-lookup"><span data-stu-id="3c332-116">If more than one capture instance is defined for the source table being captured, select the capture instance you want to use here.</span></span> <span data-ttu-id="3c332-117">[schema].[table] 資料表的預設擷取執行個體名稱是 \<schema>_\<table>，但是使用中的實際擷取執行個體名稱可能有所不同。</span><span class="sxs-lookup"><span data-stu-id="3c332-117">The default capture instance name for a table [schema].[table] is \<schema>_\<table> but that actual capture instance names in use may be different.</span></span> <span data-ttu-id="3c332-118">從中讀取的實際資料表是 CDC 資料表 **cdc .\<capture-instance>_CT**。</span><span class="sxs-lookup"><span data-stu-id="3c332-118">The actual table that is read from is the CDC table **cdc .\<capture-instance>_CT**.</span></span>  
  
8.  <span data-ttu-id="3c332-119">選取可有效處理處理需求的處理模式。</span><span class="sxs-lookup"><span data-stu-id="3c332-119">Select the processing mode that best handles your processing needs.</span></span> <span data-ttu-id="3c332-120">可能的選項包括：</span><span class="sxs-lookup"><span data-stu-id="3c332-120">The possible options are:</span></span>  
  
    -   <span data-ttu-id="3c332-121">**全部**：傳回目前 CDC 範圍中的變更，不含 [更新之前]  值。</span><span class="sxs-lookup"><span data-stu-id="3c332-121">**All**: Returns the changes in the current CDC range without the **Before Update** values.</span></span>  
  
    -   <span data-ttu-id="3c332-122">**全部 (含舊值)** ：傳回目前 CDC 處理範圍中的變更，包括舊值 ([更新之前]  )。</span><span class="sxs-lookup"><span data-stu-id="3c332-122">**All with old values**: Returns the changes in the current CDC processing range including the old values (**Before Update**).</span></span> <span data-ttu-id="3c332-123">每個更新作業都有兩個資料列：一個包含更新之前的值，另一個則包含更新之後的值。</span><span class="sxs-lookup"><span data-stu-id="3c332-123">For each Update operation, there will be two rows, one with the before-update values and one with the after-update value.</span></span>  
  
    -   <span data-ttu-id="3c332-124">**淨**：只針對目前 CDC 處理範圍中修改的每個來源資料列傳回一項變更。</span><span class="sxs-lookup"><span data-stu-id="3c332-124">**Net**: Returns only one change row per source row modified in the current CDC processing range.</span></span> <span data-ttu-id="3c332-125">如果來源資料列更新了許多次，就會產生結合的變更 (例如，插入+更新會產生為單一更新，而更新+刪除則產生為單一刪除)。</span><span class="sxs-lookup"><span data-stu-id="3c332-125">If a source row was updated multiple times, the combined change is produced (for example, insert+update is produced as a single update and update+delete is produced as a single delete).</span></span> <span data-ttu-id="3c332-126">在淨變更處理模式中工作時，您可以將變更分割成刪除、插入和更新輸出，並且以平行方式處理它們，因為單一來源資料列會出現在多個輸出中。</span><span class="sxs-lookup"><span data-stu-id="3c332-126">When working in Net change processing mode, it is possible to split the changes to Delete, Insert and Update outputs and handle them in parallel because the single source row appears in more than one output.</span></span>  
  
    -   <span data-ttu-id="3c332-127">**淨 (含更新遮罩)** ：這種模式與一般的淨模式很相似，但還新增了名稱模式為 **__$\<column-name>\__Changed** 的布林資料行，其表示目前變更資料列中的變更資料行。</span><span class="sxs-lookup"><span data-stu-id="3c332-127">**Net with update mask**: This mode is similar to the regular Net mode but it also adds boolean columns with the name pattern **__$\<column-name>\__Changed** that indicate changed columns in the current change row.</span></span>  
  
    -   <span data-ttu-id="3c332-128">**淨 (含合併)** ：這種模式與一般的淨模式很相似，但是插入和更新作業會合併成單一合併作業 (UPSERT)。</span><span class="sxs-lookup"><span data-stu-id="3c332-128">**Net with merge**: This mode is similar to the regular Net mode but with Insert and Update operations merged into a single Merge operation (UPSERT).</span></span>  
  
9. <span data-ttu-id="3c332-129">選取針對目前 CDC 內容維護 CDC 狀態的 SSIS 字串封裝變數。</span><span class="sxs-lookup"><span data-stu-id="3c332-129">Select the SSIS string package variable that maintains the CDC state for the current CDC context.</span></span> <span data-ttu-id="3c332-130">如需 CDC 狀態變數的詳細資訊，請參閱 [定義狀態變數](define-a-state-variable.md)。</span><span class="sxs-lookup"><span data-stu-id="3c332-130">For more information about the CDC state variable, see [Define a State Variable](define-a-state-variable.md).</span></span>  
  
10. <span data-ttu-id="3c332-131">選取 [Include reprocessing indicator column (包含重新處理指標資料行)]  核取方塊即可建立名為 **__$reprocessing** 的特殊輸出資料行。</span><span class="sxs-lookup"><span data-stu-id="3c332-131">Select the **Include reprocessing indicator column** check box to create a special output column called **__$reprocessing**.</span></span> <span data-ttu-id="3c332-132">當 CDC 處理範圍與初始處理範圍 (對應至初始載入週期之 LSN 的範圍) 重疊，或者上一次執行發生錯誤之後重新處理 CDC 處理範圍時，這個資料行的值就是 **true** 。</span><span class="sxs-lookup"><span data-stu-id="3c332-132">This column has a value of **true** when the CDC processing range overlaps with the initial processing range (the range of LSNs corresponding to the period of initial load) or when a CDC processing range is reprocessed following an error in a previous run.</span></span> <span data-ttu-id="3c332-133">這個指標資料行可讓 SSIS 開發人員在重新處理變更時以不同的方式處理錯誤 (例如，可以忽略刪除不存在的資料列以及在重複索引鍵上失敗的插入等動作)。</span><span class="sxs-lookup"><span data-stu-id="3c332-133">This indicator column lets the SSIS developer handle errors differently when reprocessing changes (for example, actions such as a delete of a non-existing row and an insert that failed on a duplicate key can be ignored).</span></span>  
  
     <span data-ttu-id="3c332-134">如需詳細資訊，請參閱 [CDC 來源自訂屬性](cdc-source-custom-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="3c332-134">For more information, see [CDC Source Custom Properties](cdc-source-custom-properties.md).</span></span>  
  
11. <span data-ttu-id="3c332-135">若要更新外部及輸出資料行之間的對應，請按一下 **[資料行]** ，並在 **[外部資料行]** 清單中選取不同的資料行。</span><span class="sxs-lookup"><span data-stu-id="3c332-135">To update the mapping between external and output columns, click **Columns** and select different columns in the **External Column** list.</span></span>  
  
12. <span data-ttu-id="3c332-136">(選擇性) 藉由刪除 [輸出資料行]  清單中的值，更新輸出資料行的值。</span><span class="sxs-lookup"><span data-stu-id="3c332-136">Optionally update the values of the output columns by deleting values in the **Output Column** list.</span></span>  
  
13. <span data-ttu-id="3c332-137">若要設定錯誤輸出，請按一下 **[錯誤輸出]** 。</span><span class="sxs-lookup"><span data-stu-id="3c332-137">To configure the error output, click **Error Output**.</span></span>  
  
14. <span data-ttu-id="3c332-138">您可以按一下 [預覽]  ，以檢視 CDC 來源擷取的最多 200 個資料列。</span><span class="sxs-lookup"><span data-stu-id="3c332-138">You can click **Preview** to view up to 200 rows of data extracted by the CDC source.</span></span>  
  
15. <span data-ttu-id="3c332-139">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="3c332-139">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c332-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3c332-140">See Also</span></span>  
 <span data-ttu-id="3c332-141">[CDC 來源編輯器 &#40;連線管理員頁面&#41;](../cdc-source-editor-connection-manager-page.md) </span><span class="sxs-lookup"><span data-stu-id="3c332-141">[CDC Source Editor &#40;Connection Manager Page&#41;](../cdc-source-editor-connection-manager-page.md) </span></span>  
 <span data-ttu-id="3c332-142">[CDC 來源編輯器 &#40;資料行頁面&#41;](../cdc-source-editor-columns-page.md) </span><span class="sxs-lookup"><span data-stu-id="3c332-142">[CDC Source Editor &#40;Columns Page&#41;](../cdc-source-editor-columns-page.md) </span></span>  
 [<span data-ttu-id="3c332-143">CDC 來源編輯器 &#40;錯誤輸出頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="3c332-143">CDC Source Editor &#40;Error Output Page&#41;</span></span>](../cdc-source-editor-error-output-page.md)  
  
  
