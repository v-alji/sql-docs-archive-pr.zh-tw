---
title: ADO NET 來源編輯器 (連線管理員頁面) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.adonetsource.connection.f1
ms.assetid: 7de3f438-bdd6-49b5-937a-47369e754943
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 19dd9c256f15bc9022f7267cb38b6f91bd4d8a5c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705365"
---
# <a name="ado-net-source-editor-connection-manager-page"></a><span data-ttu-id="458d6-102">ADO NET 來源編輯器 (連接管理員頁面)</span><span class="sxs-lookup"><span data-stu-id="458d6-102">ADO NET Source Editor (Connection Manager Page)</span></span>
  <span data-ttu-id="458d6-103">使用 [ADO NET 來源編輯器]  對話方塊的 [連線管理員]  頁面，即可選取來源的 [!INCLUDE[vstecado](../includes/vstecado-md.md)] 連線管理員。</span><span class="sxs-lookup"><span data-stu-id="458d6-103">Use the **Connection Manager** page of the **ADO NET Source Editor** dialog box to select the [!INCLUDE[vstecado](../includes/vstecado-md.md)] connection manager for the source.</span></span> <span data-ttu-id="458d6-104">這個頁面也可以讓您從資料庫中選取資料表或檢視。</span><span class="sxs-lookup"><span data-stu-id="458d6-104">This page also lets you select a table or view from the database.</span></span>  
  
 <span data-ttu-id="458d6-105">若要深入了解 ADO NET 來源，請參閱＜ [ADO NET Source](data-flow/ado-net-source.md)＞。</span><span class="sxs-lookup"><span data-stu-id="458d6-105">To learn more about the ADO NET source, see [ADO NET Source](data-flow/ado-net-source.md).</span></span>  
  
 <span data-ttu-id="458d6-106">**開啟連接管理員頁面**</span><span class="sxs-lookup"><span data-stu-id="458d6-106">**To open the Connection Manager page**</span></span>  
  
1.  <span data-ttu-id="458d6-107">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中，開啟具有 ADO NET 來源的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 封裝。</span><span class="sxs-lookup"><span data-stu-id="458d6-107">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] package that has the ADO NET source.</span></span>  
  
2.  <span data-ttu-id="458d6-108">在 [資料流程]  索引標籤上，按兩下 ADO NET 來源。</span><span class="sxs-lookup"><span data-stu-id="458d6-108">On the **Data Flow** tab, double-click the ADO NET source.</span></span>  
  
3.  <span data-ttu-id="458d6-109">在 [ADO NET 來源編輯器]  中，按一下 [連線管理員]  。</span><span class="sxs-lookup"><span data-stu-id="458d6-109">In the **ADO NET Source Editor**, click **Connection Manager**.</span></span>  
  
## <a name="static-options"></a><span data-ttu-id="458d6-110">靜態選項</span><span class="sxs-lookup"><span data-stu-id="458d6-110">Static Options</span></span>  
 <span data-ttu-id="458d6-111">**ADO.NET 連接管理員**</span><span class="sxs-lookup"><span data-stu-id="458d6-111">**ADO.NET connection manager**</span></span>  
 <span data-ttu-id="458d6-112">從清單中選取現有的連線管理員，或按一下 [新增]  來建立新的連線。</span><span class="sxs-lookup"><span data-stu-id="458d6-112">Select an existing connection manager from the list, or create a new connection by clicking **New**.</span></span>  
  
 <span data-ttu-id="458d6-113">**新增**</span><span class="sxs-lookup"><span data-stu-id="458d6-113">**New**</span></span>  
 <span data-ttu-id="458d6-114">使用 [設定 ADO.NET 連線管理員]  對話方塊建立新的連線管理員。</span><span class="sxs-lookup"><span data-stu-id="458d6-114">Create a new connection manager by using the **Configure ADO.NET Connection Manager** dialog box.</span></span>  
  
 <span data-ttu-id="458d6-115">**資料存取模式**</span><span class="sxs-lookup"><span data-stu-id="458d6-115">**Data access mode**</span></span>  
 <span data-ttu-id="458d6-116">從來源中指定選取資料的方法。</span><span class="sxs-lookup"><span data-stu-id="458d6-116">Specify the method for selecting data from the source.</span></span>  
  
|<span data-ttu-id="458d6-117">選項</span><span class="sxs-lookup"><span data-stu-id="458d6-117">Option</span></span>|<span data-ttu-id="458d6-118">描述</span><span class="sxs-lookup"><span data-stu-id="458d6-118">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="458d6-119">資料表或檢視</span><span class="sxs-lookup"><span data-stu-id="458d6-119">Table or view</span></span>|<span data-ttu-id="458d6-120">從 [!INCLUDE[vstecado](../includes/vstecado-md.md)] 資料來源中的資料表或檢視擷取資料。</span><span class="sxs-lookup"><span data-stu-id="458d6-120">Retrieve data from a table or view in the [!INCLUDE[vstecado](../includes/vstecado-md.md)] data source.</span></span>|  
|<span data-ttu-id="458d6-121">SQL (命令)</span><span class="sxs-lookup"><span data-stu-id="458d6-121">SQL command</span></span>|<span data-ttu-id="458d6-122">使用 SQL 查詢從 [!INCLUDE[vstecado](../includes/vstecado-md.md)] 資料來源中擷取資料。</span><span class="sxs-lookup"><span data-stu-id="458d6-122">Retrieve data from the [!INCLUDE[vstecado](../includes/vstecado-md.md)] data source by using a SQL query.</span></span>|  
  
 <span data-ttu-id="458d6-123">**預覽**</span><span class="sxs-lookup"><span data-stu-id="458d6-123">**Preview**</span></span>  
 <span data-ttu-id="458d6-124">使用 [資料檢視]  對話方塊來預覽結果。</span><span class="sxs-lookup"><span data-stu-id="458d6-124">Preview results by using the **Data View** dialog box.</span></span> <span data-ttu-id="458d6-125">[預覽]  最多可顯示 200 個資料列。</span><span class="sxs-lookup"><span data-stu-id="458d6-125">**Preview** can display up to 200 rows.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="458d6-126">在預覽資料時，具有 CLR 使用者定義型別的資料行不會包含資料。</span><span class="sxs-lookup"><span data-stu-id="458d6-126">When you preview data, columns with a CLR user-defined type do not contain data.</span></span> <span data-ttu-id="458d6-127">而會顯示值 \<value too big to display> 或 System.Byte[]。</span><span class="sxs-lookup"><span data-stu-id="458d6-127">Instead the values \<value too big to display> or System.Byte[] display.</span></span> <span data-ttu-id="458d6-128">使用 [!INCLUDE[vstecado](../includes/vstecado-md.md)] 提供者存取資料來源時會顯示前者，而使用 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Native Client 提供者時會顯示後者。</span><span class="sxs-lookup"><span data-stu-id="458d6-128">The former displays when the data source is accessed by using the [!INCLUDE[vstecado](../includes/vstecado-md.md)] provider, the latter when using the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Native Client provider.</span></span>  
  
## <a name="data-access-mode-dynamic-options"></a><span data-ttu-id="458d6-129">資料存取模式動態選項</span><span class="sxs-lookup"><span data-stu-id="458d6-129">Data Access Mode Dynamic Options</span></span>  
  
### <a name="data-access-mode--table-or-view"></a><span data-ttu-id="458d6-130">資料存取模式 = 資料表或檢視</span><span class="sxs-lookup"><span data-stu-id="458d6-130">Data access mode = Table or view</span></span>  
 <span data-ttu-id="458d6-131">**資料表或檢視的名稱**</span><span class="sxs-lookup"><span data-stu-id="458d6-131">**Name of the table or the view**</span></span>  
 <span data-ttu-id="458d6-132">從資料來源中可用的清單中選取資料表或檢視名稱。</span><span class="sxs-lookup"><span data-stu-id="458d6-132">Select the name of the table or view from a list of those available in the data source.</span></span>  
  
### <a name="data-access-mode--sql-command"></a><span data-ttu-id="458d6-133">資料存取模式 = SQL 命令</span><span class="sxs-lookup"><span data-stu-id="458d6-133">Data access mode = SQL command</span></span>  
 <span data-ttu-id="458d6-134">**SQL 命令文字**</span><span class="sxs-lookup"><span data-stu-id="458d6-134">**SQL command text**</span></span>  
 <span data-ttu-id="458d6-135">輸入 SQL 查詢文字，按一下 [建立查詢]  建立查詢，或按一下 [瀏覽]  找到包含查詢文字的檔案。</span><span class="sxs-lookup"><span data-stu-id="458d6-135">Enter the text of a SQL query, build the query by clicking **Build Query**, or locate the file that contains the query text by clicking **Browse**.</span></span>  
  
 <span data-ttu-id="458d6-136">**建立查詢**</span><span class="sxs-lookup"><span data-stu-id="458d6-136">**Build query**</span></span>  
 <span data-ttu-id="458d6-137">使用 [查詢產生器]  對話方塊，以視覺化的方式來建構 SQL 查詢。</span><span class="sxs-lookup"><span data-stu-id="458d6-137">Use the **Query Builder** dialog box to construct the SQL query visually.</span></span>  
  
 <span data-ttu-id="458d6-138">**瀏覽**</span><span class="sxs-lookup"><span data-stu-id="458d6-138">**Browse**</span></span>  
 <span data-ttu-id="458d6-139">使用 [開啟]  對話方塊來找出包含 SQL 查詢文字的檔案。</span><span class="sxs-lookup"><span data-stu-id="458d6-139">Use the **Open** dialog box to locate the file that contains the text of the SQL query.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="458d6-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="458d6-140">See Also</span></span>  
 <span data-ttu-id="458d6-141">[ADO NET 來源編輯器 &#40;資料行] 頁面&#41;](../../2014/integration-services/ado-net-source-editor-columns-page.md) </span><span class="sxs-lookup"><span data-stu-id="458d6-141">[ADO NET Source Editor &#40;Columns Page&#41;](../../2014/integration-services/ado-net-source-editor-columns-page.md) </span></span>  
 <span data-ttu-id="458d6-142">[ADO NET 來源編輯器 &#40;錯誤輸出頁面&#41;](../../2014/integration-services/ado-net-source-editor-error-output-page.md) </span><span class="sxs-lookup"><span data-stu-id="458d6-142">[ADO NET Source Editor &#40;Error Output Page&#41;](../../2014/integration-services/ado-net-source-editor-error-output-page.md) </span></span>  
 [<span data-ttu-id="458d6-143">ADO.NET 連線管理員</span><span class="sxs-lookup"><span data-stu-id="458d6-143">ADO.NET Connection Manager</span></span>](connection-manager/ado-net-connection-manager.md)  
  
  
