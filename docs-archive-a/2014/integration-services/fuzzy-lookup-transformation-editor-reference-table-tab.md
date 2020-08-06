---
title: '[模糊查閱轉換編輯器] ([參考資料表] 索引標籤) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.fuzzylookuptransformation.referencetable.f1
helpviewer_keywords:
- Fuzzy Lookup Transformation Editor
ms.assetid: 451f4e7d-1c8e-4784-b540-df0806509bf1
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 9ce51dd64c9c5807ab23ac645694cfec29a36d52
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592132"
---
# <a name="fuzzy-lookup-transformation-editor-reference-table-tab"></a><span data-ttu-id="88a96-102">模糊查閱轉換編輯器 (參考資料表索引標籤)</span><span class="sxs-lookup"><span data-stu-id="88a96-102">Fuzzy Lookup Transformation Editor (Reference Table Tab)</span></span>
  <span data-ttu-id="88a96-103">使用 **[模糊查閱轉換編輯器]** 對話方塊的 **[參考資料表]** 索引標籤，指定來源資料表和用於查閱的索引。</span><span class="sxs-lookup"><span data-stu-id="88a96-103">Use the **Reference Table** tab of the **Fuzzy Lookup Transformation Editor** dialog box to specify the source table and the index to use for the lookup.</span></span> <span data-ttu-id="88a96-104">參考資料來源必須是 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 資料庫中的資料表。</span><span class="sxs-lookup"><span data-stu-id="88a96-104">The reference data source must be a table in a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] database.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="88a96-105">模糊查閱轉換會建立參考資料表的工作副本。</span><span class="sxs-lookup"><span data-stu-id="88a96-105">The Fuzzy Lookup transformation creates a working copy of the reference table.</span></span> <span data-ttu-id="88a96-106">下面描述的索引是使用特殊資料表，而非使用一般 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 索引在此工作資料表上建立的。</span><span class="sxs-lookup"><span data-stu-id="88a96-106">The indexes described below are created on this working table by using a special table, not an ordinary [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] index.</span></span> <span data-ttu-id="88a96-107">除非您選取 **[維護儲存的索引]**，否則轉換不會修改現有的來源資料表。</span><span class="sxs-lookup"><span data-stu-id="88a96-107">The transformation does not modify the existing source tables unless you select **Maintain stored index**.</span></span> <span data-ttu-id="88a96-108">在此情況下，它會在參考資料表上建立觸發程序，以根據參考資料表的變更來更新工作資料表和查閱索引資料表。</span><span class="sxs-lookup"><span data-stu-id="88a96-108">In this case, it creates a trigger on the reference table that updates the working table and the lookup index table based on changes to the reference table.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="88a96-109">[模糊查閱 `Exhaustive` `MaxMemoryUsage` **轉換編輯器**] 中不提供 [模糊查閱] 轉換的和屬性，但是可以使用 [**進階編輯器**] 來設定。</span><span class="sxs-lookup"><span data-stu-id="88a96-109">The `Exhaustive` and the `MaxMemoryUsage` properties of the Fuzzy Lookup transformation are not available in the **Fuzzy Lookup Transformation Editor**, but can be set by using the **Advanced Editor**.</span></span> <span data-ttu-id="88a96-110">此外，您只能 `MaxOutputMatchesPerInput` 在**進階編輯器**中指定大於100的值。</span><span class="sxs-lookup"><span data-stu-id="88a96-110">In addition, a value greater than 100 for `MaxOutputMatchesPerInput` can be specified only in the **Advanced Editor**.</span></span> <span data-ttu-id="88a96-111">如需有關這些屬性的詳細資訊，請參閱＜ [Transformation Custom Properties](data-flow/transformations/transformation-custom-properties.md)＞的「模糊查閱轉換」一節。</span><span class="sxs-lookup"><span data-stu-id="88a96-111">For more information on these properties, see the Fuzzy Lookup Transformation section of [Transformation Custom Properties](data-flow/transformations/transformation-custom-properties.md).</span></span>  
  
 <span data-ttu-id="88a96-112">若要深入了解模糊查閱轉換，請參閱＜ [Fuzzy Lookup Transformation](data-flow/transformations/lookup-transformation.md)＞。</span><span class="sxs-lookup"><span data-stu-id="88a96-112">To learn more about the Fuzzy Lookup transformation, see [Fuzzy Lookup Transformation](data-flow/transformations/lookup-transformation.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="88a96-113">選項。</span><span class="sxs-lookup"><span data-stu-id="88a96-113">Options</span></span>  
 <span data-ttu-id="88a96-114">**[無快取]**</span><span class="sxs-lookup"><span data-stu-id="88a96-114">**OLE DB connection manager**</span></span>  
 <span data-ttu-id="88a96-115">從清單中選取現有的 OLE DB 連線管理員，或按一下 [新增]\*\*\*\* 來建立新連線。</span><span class="sxs-lookup"><span data-stu-id="88a96-115">Select an existing OLE DB connection manager from the list, or create a new connection by clicking **New**.</span></span>  
  
 <span data-ttu-id="88a96-116">**新增**</span><span class="sxs-lookup"><span data-stu-id="88a96-116">**New**</span></span>  
 <span data-ttu-id="88a96-117">使用 [設定 OLE DB 連接管理員]  對話方塊來建立新的連接。</span><span class="sxs-lookup"><span data-stu-id="88a96-117">Create a new connection by using the **Configure OLE DB Connection Manager** dialog box.</span></span>  
  
 <span data-ttu-id="88a96-118">**產生新的索引**</span><span class="sxs-lookup"><span data-stu-id="88a96-118">**Generate new index**</span></span>  
 <span data-ttu-id="88a96-119">指定轉換應建立新的索引以用來查閱。</span><span class="sxs-lookup"><span data-stu-id="88a96-119">Specify that the transformation should create a new index to use for the lookup.</span></span>  
  
 <span data-ttu-id="88a96-120">**參考資料表名稱**</span><span class="sxs-lookup"><span data-stu-id="88a96-120">**Reference table name**</span></span>  
 <span data-ttu-id="88a96-121">選取要用來作為參考 (查閱) 資料表的現有資料表。</span><span class="sxs-lookup"><span data-stu-id="88a96-121">Select the existing table to use as the reference (lookup) table.</span></span>  
  
 <span data-ttu-id="88a96-122">**儲存新的索引**</span><span class="sxs-lookup"><span data-stu-id="88a96-122">**Store new index**</span></span>  
 <span data-ttu-id="88a96-123">如果您要儲存新的查閱索引，請選取此選項。</span><span class="sxs-lookup"><span data-stu-id="88a96-123">Select this option if you want to save the new lookup index.</span></span>  
  
 <span data-ttu-id="88a96-124">**新增索引名稱**</span><span class="sxs-lookup"><span data-stu-id="88a96-124">**New index name**</span></span>  
 <span data-ttu-id="88a96-125">如果您已選擇要儲存新的查閱索引，請輸入該索引的描述性名稱。</span><span class="sxs-lookup"><span data-stu-id="88a96-125">If you have chosen to save the new lookup index, type a descriptive name for the index.</span></span>  
  
 <span data-ttu-id="88a96-126">**[維護儲存的索引]**</span><span class="sxs-lookup"><span data-stu-id="88a96-126">**Maintain stored index**</span></span>  
 <span data-ttu-id="88a96-127">如果您已選擇要儲存新的查閱索引，請指定是否也要 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 維護該索引。</span><span class="sxs-lookup"><span data-stu-id="88a96-127">If you have chosen to save the new lookup index, specify whether you also want [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] to maintain the index.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="88a96-128">當您在 **[模糊查閱轉換編輯器]** 的 **[參考資料表]** 索引標籤上選取 **[維護儲存的索引]** 時，轉換會使用具名預存程序來維護索引。</span><span class="sxs-lookup"><span data-stu-id="88a96-128">When you select **Maintain stored index** on the **Reference Table** tab of the **Fuzzy Lookup Transformation Editor**, the transformation uses managed stored procedures to maintain the index.</span></span> <span data-ttu-id="88a96-129">這些 Managed 預存程序會使用 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]中的 Common Language Runtime (CLR) 整合功能。</span><span class="sxs-lookup"><span data-stu-id="88a96-129">These managed stored procedures use the common language runtime (CLR) integration feature in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="88a96-130">根據預設，不會啟用 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 中的 CLR 整合功能。</span><span class="sxs-lookup"><span data-stu-id="88a96-130">By default, CLR integration in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] is not enabled.</span></span> <span data-ttu-id="88a96-131">若要使用 **[維護儲存的索引]** 功能，您必須啟用 CLR 整合。</span><span class="sxs-lookup"><span data-stu-id="88a96-131">To use the **Maintain stored index** functionality, you must enable CLR integration.</span></span> <span data-ttu-id="88a96-132">如需詳細資訊，請參閱 [Enabling CLR Integration](../relational-databases/clr-integration/clr-integration-enabling.md)。</span><span class="sxs-lookup"><span data-stu-id="88a96-132">For more information, see [Enabling CLR Integration](../relational-databases/clr-integration/clr-integration-enabling.md).</span></span>  
>   
>  <span data-ttu-id="88a96-133">因為 **[維護儲存的索引]** 選項需要 CLR 整合，因此只有當您在已啟用 CLR 整合的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 執行個體上選取參考資料表時，這項功能才有效。</span><span class="sxs-lookup"><span data-stu-id="88a96-133">Because the **Maintain stored index** option requires CLR integration, this feature works only when you select a reference table on an instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] where CLR integration is enabled.</span></span>  
  
 <span data-ttu-id="88a96-134">**使用現有的索引**</span><span class="sxs-lookup"><span data-stu-id="88a96-134">**Use existing index**</span></span>  
 <span data-ttu-id="88a96-135">指定轉換應使用現有的索引來查閱。</span><span class="sxs-lookup"><span data-stu-id="88a96-135">Specify that the transformation should use an existing index for the lookup.</span></span>  
  
 <span data-ttu-id="88a96-136">**現有索引的名稱**</span><span class="sxs-lookup"><span data-stu-id="88a96-136">**Name of an existing index**</span></span>  
 <span data-ttu-id="88a96-137">從清單中選取先前建立的查閱索引。</span><span class="sxs-lookup"><span data-stu-id="88a96-137">Select a previously created lookup index from the list.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88a96-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="88a96-138">See Also</span></span>  
 <span data-ttu-id="88a96-139">[Integration Services 錯誤和訊息參考](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="88a96-139">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="88a96-140">[模糊查閱轉換編輯器 &#40;資料行] 索引標籤&#41;](../../2014/integration-services/fuzzy-lookup-transformation-editor-columns-tab.md) </span><span class="sxs-lookup"><span data-stu-id="88a96-140">[Fuzzy Lookup Transformation Editor &#40;Columns Tab&#41;](../../2014/integration-services/fuzzy-lookup-transformation-editor-columns-tab.md) </span></span>  
 [<span data-ttu-id="88a96-141">模糊查閱轉換編輯器 &#40;進階索引標籤&#41;</span><span class="sxs-lookup"><span data-stu-id="88a96-141">Fuzzy Lookup Transformation Editor &#40;Advanced Tab&#41;</span></span>](../../2014/integration-services/fuzzy-lookup-transformation-editor-advanced-tab.md)  
  
  
