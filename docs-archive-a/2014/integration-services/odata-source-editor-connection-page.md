---
title: '[OData 來源編輯器] (連接頁面) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- Sql12.dts.designer.odatasource.connection.f1
ms.assetid: 20bcd347-4547-4fad-b182-9571030101df
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 6ecd0d060ea2197ae7174325b654645fefa23505
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597203"
---
# <a name="odata-source-editor-connection-page"></a><span data-ttu-id="e5981-102">OData 來源編輯器 (連接頁面)</span><span class="sxs-lookup"><span data-stu-id="e5981-102">OData Source Editor (Connection Page)</span></span>
  <span data-ttu-id="e5981-103">使用 **[OData 來源編輯器]** 對話方塊的 **[連接]** 頁面，選取 OData 來源的 OData 連接管理員。</span><span class="sxs-lookup"><span data-stu-id="e5981-103">Use the **Connection** page of the **OData Source Editor** dialog box to select the OData connection manager for the OData source.</span></span> <span data-ttu-id="e5981-104">此頁面也可讓您指定集合或資源路徑及任何查詢選項，以指示需要從 OData 來源擷取哪些資料。</span><span class="sxs-lookup"><span data-stu-id="e5981-104">This page also lets you specify a collection or a resource path and any query options to indicate what data needs to be retrieved from the OData source.</span></span> <span data-ttu-id="e5981-105">若要深入了解 OData 來源，請參閱＜ [OData Source](data-flow/odata-source.md)＞。</span><span class="sxs-lookup"><span data-stu-id="e5981-105">To learn more about the OData source, see [OData Source](data-flow/odata-source.md).</span></span>  
  
## <a name="static-options"></a><span data-ttu-id="e5981-106">靜態選項</span><span class="sxs-lookup"><span data-stu-id="e5981-106">Static Options</span></span>  
 <span data-ttu-id="e5981-107">**OData 連線管理員**</span><span class="sxs-lookup"><span data-stu-id="e5981-107">**OData connection manager**</span></span>  
 <span data-ttu-id="e5981-108">從清單中選取現有的連線管理員，或按一下 [新增]  來建立新的連線。</span><span class="sxs-lookup"><span data-stu-id="e5981-108">Select an existing connection manager from the list, or create a new connection by clicking **New**.</span></span>  
  
 <span data-ttu-id="e5981-109">**新增**</span><span class="sxs-lookup"><span data-stu-id="e5981-109">**New**</span></span>  
 <span data-ttu-id="e5981-110">使用 [OData 連線管理員編輯器]\*\*\*\* 對話方塊建立新的連線管理員。</span><span class="sxs-lookup"><span data-stu-id="e5981-110">Create a new connection manager by using the **OData Connection Manager Editor** dialog box.</span></span>  
  
 <span data-ttu-id="e5981-111">**使用集合或資源路徑**</span><span class="sxs-lookup"><span data-stu-id="e5981-111">**Use collection or resource path**</span></span>  
 <span data-ttu-id="e5981-112">從來源中指定選取資料的方法。</span><span class="sxs-lookup"><span data-stu-id="e5981-112">Specify the method for selecting data from the source.</span></span>  
  
|<span data-ttu-id="e5981-113">選項</span><span class="sxs-lookup"><span data-stu-id="e5981-113">Option</span></span>|<span data-ttu-id="e5981-114">描述</span><span class="sxs-lookup"><span data-stu-id="e5981-114">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="e5981-115">集合</span><span class="sxs-lookup"><span data-stu-id="e5981-115">Collection</span></span>|<span data-ttu-id="e5981-116">使用集合名稱從 OData 來源擷取資料。</span><span class="sxs-lookup"><span data-stu-id="e5981-116">Retrieve data from the OData source by using a collection name.</span></span>|  
|<span data-ttu-id="e5981-117">資源路徑</span><span class="sxs-lookup"><span data-stu-id="e5981-117">Resource Path</span></span>|<span data-ttu-id="e5981-118">使用資源路徑從 OData 來源擷取資料。</span><span class="sxs-lookup"><span data-stu-id="e5981-118">Retrieve data from the OData source by using a resource path.</span></span>|  
  
 <span data-ttu-id="e5981-119">**查詢選項**</span><span class="sxs-lookup"><span data-stu-id="e5981-119">**Query options**</span></span>  
 <span data-ttu-id="e5981-120">指定查詢的選項。</span><span class="sxs-lookup"><span data-stu-id="e5981-120">Specify options for the query.</span></span>  <span data-ttu-id="e5981-121">例如：$top=5</span><span class="sxs-lookup"><span data-stu-id="e5981-121">For example: $top=5</span></span>  
  
 <span data-ttu-id="e5981-122">**摘要 url**</span><span class="sxs-lookup"><span data-stu-id="e5981-122">**Feed url**</span></span>  
 <span data-ttu-id="e5981-123">根據您在此對話方塊中選取的選項顯示唯讀摘要 URL。</span><span class="sxs-lookup"><span data-stu-id="e5981-123">Displays the read-only Feed URL based on options you selected on this dialog box.</span></span>  
  
 <span data-ttu-id="e5981-124">**預覽**</span><span class="sxs-lookup"><span data-stu-id="e5981-124">**Preview**</span></span>  
 <span data-ttu-id="e5981-125">使用 [預覽]\*\*\*\* 對話方塊來預覽結果。</span><span class="sxs-lookup"><span data-stu-id="e5981-125">Preview results by using the **Preview** dialog box.</span></span> <span data-ttu-id="e5981-126">**[預覽]** 最多可顯示 20 個資料列。</span><span class="sxs-lookup"><span data-stu-id="e5981-126">**Preview** can display up to 20 rows.</span></span>  
  
## <a name="dynamic-options"></a><span data-ttu-id="e5981-127">動態選項</span><span class="sxs-lookup"><span data-stu-id="e5981-127">Dynamic Options</span></span>  
  
### <a name="use-collection-or-resource-path--collection"></a><span data-ttu-id="e5981-128">使用集合或資源路徑 = 集合</span><span class="sxs-lookup"><span data-stu-id="e5981-128">Use collection or resource path = Collection</span></span>  
 <span data-ttu-id="e5981-129">**集合**</span><span class="sxs-lookup"><span data-stu-id="e5981-129">**Collection**</span></span>  
 <span data-ttu-id="e5981-130">從下拉式清單中選取集合。</span><span class="sxs-lookup"><span data-stu-id="e5981-130">Select a collection from the drop-down list.</span></span>  
  
### <a name="use-collection-or-resource-path--resource-path"></a><span data-ttu-id="e5981-131">使用集合或資源路徑 = 資源路徑</span><span class="sxs-lookup"><span data-stu-id="e5981-131">Use collection or resource path = Resource Path</span></span>  
 <span data-ttu-id="e5981-132">**資源路徑**</span><span class="sxs-lookup"><span data-stu-id="e5981-132">**Resource path**</span></span>  
 <span data-ttu-id="e5981-133">輸入資源路徑。</span><span class="sxs-lookup"><span data-stu-id="e5981-133">Type a resource path.</span></span> <span data-ttu-id="e5981-134">例如：員工</span><span class="sxs-lookup"><span data-stu-id="e5981-134">For example: Employees</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5981-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e5981-135">See Also</span></span>  
 <span data-ttu-id="e5981-136">[[OData 來源編輯器 &#40;資料行] 頁面&#41;](../../2014/integration-services/odata-source-editor-columns-page.md) </span><span class="sxs-lookup"><span data-stu-id="e5981-136">[OData Source Editor &#40;Columns Page&#41;](../../2014/integration-services/odata-source-editor-columns-page.md) </span></span>  
 <span data-ttu-id="e5981-137">[[OData 來源編輯器] &#40;錯誤輸出頁面&#41;](../../2014/integration-services/odata-source-editor-error-output-page.md) </span><span class="sxs-lookup"><span data-stu-id="e5981-137">[OData Source Editor &#40;Error Output Page&#41;](../../2014/integration-services/odata-source-editor-error-output-page.md) </span></span>  
 [<span data-ttu-id="e5981-138">OData 連接管理員</span><span class="sxs-lookup"><span data-stu-id="e5981-138">OData Connection Manager</span></span>](connection-manager/odata-connection-manager.md)  
  
  
