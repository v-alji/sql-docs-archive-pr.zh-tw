---
title: 查閱轉換編輯器 (連接頁面) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.lookuptransformation.referencetable.f1
helpviewer_keywords:
- Lookup Transformation Editor
ms.assetid: e90d6b69-5a26-43c5-8433-5c3c9588e08c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 381378ac1aca85c6bca825033bc439ebc39fb063
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596105"
---
# <a name="lookup-transformation-editor-connection-page"></a><span data-ttu-id="d06e1-102">查閱轉換編輯器 (連接頁面)</span><span class="sxs-lookup"><span data-stu-id="d06e1-102">Lookup Transformation Editor (Connection Page)</span></span>
  <span data-ttu-id="d06e1-103">使用 **[查閱轉換編輯器]** 對話方塊的 **[連接]** 頁面，來選取連接管理員。</span><span class="sxs-lookup"><span data-stu-id="d06e1-103">Use the **Connection** page of the **Lookup Transformation Editor** dialog box to select a connection manager.</span></span> <span data-ttu-id="d06e1-104">如果您選取 OLE DB 連接管理員，也可以選取查詢、資料表或檢視來產生參考資料集。</span><span class="sxs-lookup"><span data-stu-id="d06e1-104">If you select an OLE DB connection manager, you also select a query, table, or view to generate the reference dataset.</span></span>  
  
 <span data-ttu-id="d06e1-105">若要深入了解查閱轉換，請參閱＜ [Lookup Transformation](data-flow/transformations/lookup-transformation.md)＞。</span><span class="sxs-lookup"><span data-stu-id="d06e1-105">To learn more about the Lookup transformation, see [Lookup Transformation](data-flow/transformations/lookup-transformation.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="d06e1-106">選項</span><span class="sxs-lookup"><span data-stu-id="d06e1-106">Options</span></span>  
 <span data-ttu-id="d06e1-107">當您在 **[查閱轉換編輯器]** 對話方塊的 [一般] 頁面上選取 **[完整快取]** 和 **[快取連接管理員]** 時，可使用下列選項：</span><span class="sxs-lookup"><span data-stu-id="d06e1-107">The following options are available when you select **Full cache** and **Cache connection manager** on the General page of the **Lookup Transformation Editor** dialog box.</span></span>  
  
 <span data-ttu-id="d06e1-108">**快取連線管理員**</span><span class="sxs-lookup"><span data-stu-id="d06e1-108">**Cache connection manager**</span></span>  
 <span data-ttu-id="d06e1-109">從清單中選取現有的快取連線管理員，或按一下 [新增]\*\*\*\* 來建立新的連線。</span><span class="sxs-lookup"><span data-stu-id="d06e1-109">Select an existing Cache connection manager from the list, or create a new connection by clicking **New**.</span></span>  
  
 <span data-ttu-id="d06e1-110">**新增**</span><span class="sxs-lookup"><span data-stu-id="d06e1-110">**New**</span></span>  
 <span data-ttu-id="d06e1-111">使用 [快取連線管理員編輯器]\*\*\*\* 對話方塊來建立新的連線。</span><span class="sxs-lookup"><span data-stu-id="d06e1-111">Create a new connection by using the **Cache Connection Manager Editor** dialog box.</span></span>  
  
 <span data-ttu-id="d06e1-112">當您在 **[查閱轉換編輯器]** 對話方塊的 [一般] 頁面上選取 **[完整快取]**、 **[部分快取]** 或 **[無快取]** 以及 **[OLE DB 連接管理員]** 時，可以使用下列選項。</span><span class="sxs-lookup"><span data-stu-id="d06e1-112">The following options are available when you select **Full cache**, **Partial cache**, or **No cache**, and **OLE DB connection manager**, on the General page of the **Lookup Transformation Editor** dialog box.</span></span>  
  
 <span data-ttu-id="d06e1-113">**[無快取]**</span><span class="sxs-lookup"><span data-stu-id="d06e1-113">**OLE DB connection manager**</span></span>  
 <span data-ttu-id="d06e1-114">從清單中選取現有的 OLE DB 連線管理員，或按一下 [新增]\*\*\*\* 來建立新連線。</span><span class="sxs-lookup"><span data-stu-id="d06e1-114">Select an existing OLE DB connection manager from the list, or create a new connection by clicking **New**.</span></span>  
  
 <span data-ttu-id="d06e1-115">**新增**</span><span class="sxs-lookup"><span data-stu-id="d06e1-115">**New**</span></span>  
 <span data-ttu-id="d06e1-116">使用 [設定 OLE DB 連接管理員]  對話方塊來建立新的連接。</span><span class="sxs-lookup"><span data-stu-id="d06e1-116">Create a new connection by using the **Configure OLE DB Connection Manager** dialog box.</span></span>  
  
 <span data-ttu-id="d06e1-117">**使用資料表或檢視**</span><span class="sxs-lookup"><span data-stu-id="d06e1-117">**Use a table or view**</span></span>  
 <span data-ttu-id="d06e1-118">從清單中選取現有的資料表或視圖，或按一下 [**新增**] 來建立新的資料表。</span><span class="sxs-lookup"><span data-stu-id="d06e1-118">Select an existing table or view from the list, or create a new table by clicking **New**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d06e1-119">如果在 **[查閱轉換編輯器]** 的 **[進階]** 頁面上指定 SQL 陳述式，則該 SQL 陳述式會覆寫並取代此處所選取的資料表名稱。</span><span class="sxs-lookup"><span data-stu-id="d06e1-119">If you specify a SQL statement on the **Advanced** page of the **Lookup Transformation Editor**, that SQL statement overrides and replaces the table name selected here.</span></span> <span data-ttu-id="d06e1-120">如需詳細資訊，請參閱 [查閱轉換編輯器 &#40;進階頁面&#41;](../../2014/integration-services/lookup-transformation-editor-advanced-page.md)＞。</span><span class="sxs-lookup"><span data-stu-id="d06e1-120">For more information, see [Lookup Transformation Editor &#40;Advanced Page&#41;](../../2014/integration-services/lookup-transformation-editor-advanced-page.md).</span></span>  
  
 <span data-ttu-id="d06e1-121">**新增**</span><span class="sxs-lookup"><span data-stu-id="d06e1-121">**New**</span></span>  
 <span data-ttu-id="d06e1-122">使用 [建立資料表]  對話方塊建立新的資料表。</span><span class="sxs-lookup"><span data-stu-id="d06e1-122">Create a new table by using the **Create Table** dialog box.</span></span>  
  
 <span data-ttu-id="d06e1-123">**使用 SQL 查詢的結果**</span><span class="sxs-lookup"><span data-stu-id="d06e1-123">**Use results of an SQL query**</span></span>  
 <span data-ttu-id="d06e1-124">選擇此選項以瀏覽至預先存在的查詢、建立新查詢、檢查查詢語法，以及預覽查詢結果。</span><span class="sxs-lookup"><span data-stu-id="d06e1-124">Choose this option to browse to a preexisting query, build a new query, check query syntax, and preview query results.</span></span>  
  
 <span data-ttu-id="d06e1-125">**建立查詢**</span><span class="sxs-lookup"><span data-stu-id="d06e1-125">**Build query**</span></span>  
 <span data-ttu-id="d06e1-126">使用 [查詢產生器]\*\*\*\* (用來以瀏覽資料的方式建立查詢的圖形化工具)，來建立要執行的 Transact-SQL 陳述式。</span><span class="sxs-lookup"><span data-stu-id="d06e1-126">Create the Transact-SQL statement to run by using **Query Builder**, a graphical tool that is used to create queries by browsing through data.</span></span>  
  
 <span data-ttu-id="d06e1-127">**瀏覽**</span><span class="sxs-lookup"><span data-stu-id="d06e1-127">**Browse**</span></span>  
 <span data-ttu-id="d06e1-128">使用此選項即可瀏覽至預先存在且已儲存為檔案的查詢。</span><span class="sxs-lookup"><span data-stu-id="d06e1-128">Use this option to browse to a preexisting query saved as a file.</span></span>  
  
 <span data-ttu-id="d06e1-129">**剖析查詢**</span><span class="sxs-lookup"><span data-stu-id="d06e1-129">**Parse Query**</span></span>  
 <span data-ttu-id="d06e1-130">檢查查詢的語法。</span><span class="sxs-lookup"><span data-stu-id="d06e1-130">Check the syntax of the query.</span></span>  
  
 <span data-ttu-id="d06e1-131">**預覽**</span><span class="sxs-lookup"><span data-stu-id="d06e1-131">**Preview**</span></span>  
 <span data-ttu-id="d06e1-132">使用 [預覽查詢結果]  對話方塊來預覽結果。</span><span class="sxs-lookup"><span data-stu-id="d06e1-132">Preview results by using the **Preview Query Results** dialog box.</span></span> <span data-ttu-id="d06e1-133">此選項最多可顯示 200 個資料列。</span><span class="sxs-lookup"><span data-stu-id="d06e1-133">This option displays up to 200 rows.</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="d06e1-134">外部資源</span><span class="sxs-lookup"><span data-stu-id="d06e1-134">External Resources</span></span>  
 <span data-ttu-id="d06e1-135">blogs.msdn.com 上的部落格文章： [查閱快取模式](https://go.microsoft.com/fwlink/?LinkId=219518)</span><span class="sxs-lookup"><span data-stu-id="d06e1-135">Blog entry, [Lookup cache modes](https://go.microsoft.com/fwlink/?LinkId=219518) on blogs.msdn.com</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d06e1-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d06e1-136">See Also</span></span>  
 <span data-ttu-id="d06e1-137">[查閱轉換編輯器 &#40;一般頁面&#41;](general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="d06e1-137">[Lookup Transformation Editor &#40;General Page&#41;](general-page-of-integration-services-designers-options.md) </span></span>  
 <span data-ttu-id="d06e1-138">[查閱轉換編輯器 &#40;資料行頁面&#41;](../../2014/integration-services/lookup-transformation-editor-columns-page.md) </span><span class="sxs-lookup"><span data-stu-id="d06e1-138">[Lookup Transformation Editor &#40;Columns Page&#41;](../../2014/integration-services/lookup-transformation-editor-columns-page.md) </span></span>  
 <span data-ttu-id="d06e1-139">[查閱轉換編輯器 &#40;Advanced Page&#41;](../../2014/integration-services/lookup-transformation-editor-advanced-page.md) </span><span class="sxs-lookup"><span data-stu-id="d06e1-139">[Lookup Transformation Editor &#40;Advanced Page&#41;](../../2014/integration-services/lookup-transformation-editor-advanced-page.md) </span></span>  
 <span data-ttu-id="d06e1-140">[查閱轉換編輯器 &#40;錯誤輸出頁面&#41;](../../2014/integration-services/lookup-transformation-editor-error-output-page.md) </span><span class="sxs-lookup"><span data-stu-id="d06e1-140">[Lookup Transformation Editor &#40;Error Output Page&#41;](../../2014/integration-services/lookup-transformation-editor-error-output-page.md) </span></span>  
 [<span data-ttu-id="d06e1-141">模糊查閱轉換</span><span class="sxs-lookup"><span data-stu-id="d06e1-141">Fuzzy Lookup Transformation</span></span>](data-flow/transformations/fuzzy-lookup-transformation.md)  
  
  
