---
title: CDC 來源編輯器 (連線管理員頁面) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.designer.cdcsource.connection.f1
ms.assetid: 304e6717-e160-4a7b-a06f-32182449fef8
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 5b0ed4792f13006bb9013771c69053b04539bc0e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599631"
---
# <a name="cdc-source-editor-connection-manager-page"></a><span data-ttu-id="75371-102">CDC 來源編輯器 (連接管理員頁面)</span><span class="sxs-lookup"><span data-stu-id="75371-102">CDC Source Editor (Connection Manager Page)</span></span>
  <span data-ttu-id="75371-103">使用 [CDC 來源編輯器]  對話方塊的 [連線管理員]  頁面，即可針對 CDC 來源從中讀取變更資料列的 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] 資料庫 (CDC 資料庫) 選取 ADO.NET 連線管理員。</span><span class="sxs-lookup"><span data-stu-id="75371-103">Use the **Connection Manager** page of the **CDC Source Editor** dialog box to select the ADO.NET connection manager for the [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] database that the CDC source reads change rows from (the CDC database).</span></span> <span data-ttu-id="75371-104">一旦選取 CDC 資料庫之後，您就必須在資料庫中選取擷取的資料表。</span><span class="sxs-lookup"><span data-stu-id="75371-104">Once the CDC database is selected you need to select a captured table in the database.</span></span>  
  
 <span data-ttu-id="75371-105">如需 CDC 來源的詳細資訊，請參閱 [CDC 來源](data-flow/cdc-source.md)。</span><span class="sxs-lookup"><span data-stu-id="75371-105">For more information about the CDC source, see [CDC Source](data-flow/cdc-source.md).</span></span>  
  
## <a name="task-list"></a><span data-ttu-id="75371-106">工作清單</span><span class="sxs-lookup"><span data-stu-id="75371-106">Task List</span></span>  
 <span data-ttu-id="75371-107">**若要開啟 CDC 來源編輯器的連接管理員頁面**</span><span class="sxs-lookup"><span data-stu-id="75371-107">**To open the CDC Source Editor Connection Manager Page**</span></span>  
  
1.  <span data-ttu-id="75371-108">在 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]中，開啟具有 CDC 來源的 [!INCLUDE[ssISCurrent](../includes/ssiscurrent-md.md)] 封裝。</span><span class="sxs-lookup"><span data-stu-id="75371-108">In [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], open the [!INCLUDE[ssISCurrent](../includes/ssiscurrent-md.md)] package that has the CDC source.</span></span>  
  
2.  <span data-ttu-id="75371-109">在 [資料流程]  索引標籤中，按兩下 CDC 來源。</span><span class="sxs-lookup"><span data-stu-id="75371-109">On the **Data Flow** tab, double-click the CDC source.</span></span>  
  
3.  <span data-ttu-id="75371-110">在 [CDC 來源編輯器]  中，按一下 [連線管理員]  。</span><span class="sxs-lookup"><span data-stu-id="75371-110">In the **CDC Source Editor**, click **Connection Manager**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="75371-111">選項。</span><span class="sxs-lookup"><span data-stu-id="75371-111">Options</span></span>  
 <span data-ttu-id="75371-112">**ADO.NET 連接管理員**</span><span class="sxs-lookup"><span data-stu-id="75371-112">**ADO.NET connection manager**</span></span>  
 <span data-ttu-id="75371-113">從清單中選取現有的連接管理員，或按一下 [新增]  建立新的連接。</span><span class="sxs-lookup"><span data-stu-id="75371-113">Select an existing connection manager from the list, or click **New** to create a new connection.</span></span> <span data-ttu-id="75371-114">此連接必須指向啟用 CDC 而且包含選取之變更資料表的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 資料庫。</span><span class="sxs-lookup"><span data-stu-id="75371-114">The connection must be to a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] database that is enabled for CDC and where the selected change table is located.</span></span>  
  
 <span data-ttu-id="75371-115">**新增**</span><span class="sxs-lookup"><span data-stu-id="75371-115">**New**</span></span>  
 <span data-ttu-id="75371-116">按一下 **[新增]** 。</span><span class="sxs-lookup"><span data-stu-id="75371-116">Click **New**.</span></span> <span data-ttu-id="75371-117">[設定 ADO.NET 連線管理員編輯器]  對話方塊隨即開啟，讓您能夠建立新的連線管理員。</span><span class="sxs-lookup"><span data-stu-id="75371-117">The **Configure ADO.NET Connection Manager Editor** dialog box opens where you can create a new connection manager</span></span>  
  
 <span data-ttu-id="75371-118">**CDC 資料表**</span><span class="sxs-lookup"><span data-stu-id="75371-118">**CDC Table**</span></span>  
 <span data-ttu-id="75371-119">選取 CDC 來源資料表，其中包含您想要讀取並饋送至下游 SSIS 元件進行處理的擷取變更。</span><span class="sxs-lookup"><span data-stu-id="75371-119">Select the CDC source table that contains the captured changes that you want read and feed to downstream SSIS components for processing.</span></span>  
  
 <span data-ttu-id="75371-120">**擷取執行個體**</span><span class="sxs-lookup"><span data-stu-id="75371-120">**Capture instance**</span></span>  
 <span data-ttu-id="75371-121">選取或輸入包含要讀取之 CDC 資料表的 CDC 擷取執行個體名稱。</span><span class="sxs-lookup"><span data-stu-id="75371-121">Select or type in the name of the CDC capture instance with the CDC table to be read.</span></span>  
  
 <span data-ttu-id="75371-122">擷取的來源資料表可以具有一個或兩個擷取執行個體，以便透過結構描述變更處理資料表定義的流暢轉換。</span><span class="sxs-lookup"><span data-stu-id="75371-122">A captured source table can have one or two captured instances to handle seamless transitioning of table definition through schema changes.</span></span> <span data-ttu-id="75371-123">如果針對所擷取的來源資料表定義了多個擷取執行個體，請在此選取您想要使用的擷取執行個體。</span><span class="sxs-lookup"><span data-stu-id="75371-123">If more than one capture instance is defined for the source table being captured, select the capture instance you want to use here.</span></span> <span data-ttu-id="75371-124">[schema].[table] 資料表的預設擷取執行個體名稱是 \<schema>_\<table>，但是使用中的實際擷取執行個體名稱可能有所不同。</span><span class="sxs-lookup"><span data-stu-id="75371-124">The default capture instance name for a table [schema].[table] is \<schema>_\<table> but that actual capture instance names in use may be different.</span></span> <span data-ttu-id="75371-125">從中讀取的實際資料表是 CDC 資料表 **cdc .\<capture-instance>_CT**。</span><span class="sxs-lookup"><span data-stu-id="75371-125">The actual table that is read from is the CDC table **cdc .\<capture-instance>_CT**.</span></span>  
  
 <span data-ttu-id="75371-126">**CDC 處理模式**</span><span class="sxs-lookup"><span data-stu-id="75371-126">**CDC Processing Mode**</span></span>  
 <span data-ttu-id="75371-127">選取可有效處理處理需求的處理模式。</span><span class="sxs-lookup"><span data-stu-id="75371-127">Select the processing mode that best handles your processing needs.</span></span> <span data-ttu-id="75371-128">可能的選項包括：</span><span class="sxs-lookup"><span data-stu-id="75371-128">The possible options are:</span></span>  
  
-   <span data-ttu-id="75371-129">**全部**：傳回目前 CDC 範圍中的變更，不含 [更新之前]  值。</span><span class="sxs-lookup"><span data-stu-id="75371-129">**All**: Returns the changes in the current CDC range without the **Before Update** values.</span></span>  
  
-   <span data-ttu-id="75371-130">**全部 (含舊值)** ：傳回目前 CDC 處理範圍中的變更，包括舊值 ([更新前]  )。</span><span class="sxs-lookup"><span data-stu-id="75371-130">**All with old values**: Returns the changes in the current CDC processing range including the old values (**Before Update**).</span></span> <span data-ttu-id="75371-131">每個更新作業都有兩個資料列：一個包含更新之前的值，另一個則包含更新之後的值。</span><span class="sxs-lookup"><span data-stu-id="75371-131">For each Update operation, there will be two rows, one with the before-update values and one with the after-update value.</span></span>  
  
-   <span data-ttu-id="75371-132">**淨**：只針對目前 CDC 處理範圍中修改的每個來源資料列傳回一項變更。</span><span class="sxs-lookup"><span data-stu-id="75371-132">**Net**: Returns only one change row per source row modified in the current CDC processing range.</span></span> <span data-ttu-id="75371-133">如果來源資料列更新了許多次，就會產生結合的變更 (例如，插入+更新會產生為單一更新，而更新+刪除則產生為單一刪除)。</span><span class="sxs-lookup"><span data-stu-id="75371-133">If a source row was updated multiple times, the combined change is produced (for example, insert+update is produced as a single update and update+delete is produced as a single delete).</span></span> <span data-ttu-id="75371-134">在淨變更處理模式中工作時，您可以將變更分割成刪除、插入和更新輸出，並且以平行方式處理它們，因為單一來源資料列會出現在多個輸出中。</span><span class="sxs-lookup"><span data-stu-id="75371-134">When working in Net change processing mode, it is possible to split the changes to Delete, Insert and Update outputs and handle them in parallel because the single source row appears in more than one output.</span></span>  
  
-   <span data-ttu-id="75371-135">**淨 (含更新遮罩)** ：這種模式與一般的淨模式很相似，但還新增了名稱模式為 **__$\<column-name>\__Changed** 的布林資料行，其表示目前變更資料列中的變更資料行。</span><span class="sxs-lookup"><span data-stu-id="75371-135">**Net with update mask**: This mode is similar to the regular Net mode but it also adds boolean columns with the name pattern **__$\<column-name>\__Changed** that indicate changed columns in the current change row.</span></span>  
  
-   <span data-ttu-id="75371-136">**淨 (含合併)** ：這種模式與一般的淨模式很相似，但是插入和更新作業會合併成單一合併作業 (UPSERT)。</span><span class="sxs-lookup"><span data-stu-id="75371-136">**Net with merge**: This mode is similar to the regular Net mode but with Insert and Update operations merged into a single Merge operation (UPSERT).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="75371-137">對於所有淨變更選項而言，來源資料表必須具有主索引鍵或唯一索引。</span><span class="sxs-lookup"><span data-stu-id="75371-137">For all Net change options, the source table must have a primary key or unique index.</span></span> <span data-ttu-id="75371-138">如果資料表沒有主索引鍵或唯一索引，您就必須使用 [全部]  選項。</span><span class="sxs-lookup"><span data-stu-id="75371-138">For tables without a primary key or unique indes, you must yse the **All** option.</span></span>  
  
 <span data-ttu-id="75371-139">**包含 CDC 狀態的變數**</span><span class="sxs-lookup"><span data-stu-id="75371-139">**Variable containing the CDC state**</span></span>  
 <span data-ttu-id="75371-140">選取針對目前 CDC 內容維護 CDC 狀態的 SSIS 字串封裝變數。</span><span class="sxs-lookup"><span data-stu-id="75371-140">Select the SSIS string package variable that maintains the CDC state for the current CDC context.</span></span> <span data-ttu-id="75371-141">如需 CDC 狀態變數的詳細資訊，請參閱 [定義狀態變數](data-flow/define-a-state-variable.md)。</span><span class="sxs-lookup"><span data-stu-id="75371-141">For more information about the CDC state variable, see [Define a State Variable](data-flow/define-a-state-variable.md).</span></span>  
  
 <span data-ttu-id="75371-142">**包含重新處理指標資料行**</span><span class="sxs-lookup"><span data-stu-id="75371-142">**Include reprocessing indicator column**</span></span>  
 <span data-ttu-id="75371-143">選取此核取方塊即可建立名為 **__$reprocessing**的特殊輸出資料行。</span><span class="sxs-lookup"><span data-stu-id="75371-143">Select this check box to create a special output column called **__$reprocessing**.</span></span>  
  
 <span data-ttu-id="75371-144">當 CDC 處理範圍與初始處理範圍 (對應至初始載入週期之 LSN 的範圍) 重疊，或者上一次執行發生錯誤之後重新處理 CDC 處理範圍時，這個資料行的值就是 **true** 。</span><span class="sxs-lookup"><span data-stu-id="75371-144">This column has a value of **true** when the CDC processing range overlaps with the initial processing range (the range of LSNs corresponding to the period of initial load) or when a CDC processing range is reprocessed following an error in a previous run.</span></span> <span data-ttu-id="75371-145">這個指標資料行可讓 SSIS 開發人員在重新處理變更時以不同的方式處理錯誤 (例如，可以忽略刪除不存在的資料列以及在重複索引鍵上失敗的插入等動作)。</span><span class="sxs-lookup"><span data-stu-id="75371-145">This indicator column lets the SSIS developer handle errors differently when reprocessing changes (for example, actions such as a delete of a non-existing row and an insert that failed on a duplicate key can be ignored).</span></span>  
  
 <span data-ttu-id="75371-146">如需詳細資訊，請參閱 [CDC 來源自訂屬性](data-flow/cdc-source-custom-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="75371-146">For more information, see [CDC Source Custom Properties](data-flow/cdc-source-custom-properties.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75371-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="75371-147">See Also</span></span>  
 <span data-ttu-id="75371-148">[CDC 來源編輯器 &#40;資料行頁面&#41;](../../2014/integration-services/cdc-source-editor-columns-page.md) </span><span class="sxs-lookup"><span data-stu-id="75371-148">[CDC Source Editor &#40;Columns Page&#41;](../../2014/integration-services/cdc-source-editor-columns-page.md) </span></span>  
 [<span data-ttu-id="75371-149">CDC 來源編輯器 &#40;錯誤輸出頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="75371-149">CDC Source Editor &#40;Error Output Page&#41;</span></span>](../../2014/integration-services/cdc-source-editor-error-output-page.md)  
  
  
