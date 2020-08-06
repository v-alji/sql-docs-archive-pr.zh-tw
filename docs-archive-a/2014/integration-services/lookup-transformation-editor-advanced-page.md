---
title: 查閱轉換編輯器 (Advanced Page) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.lookuptransformation.advanced.f1
helpviewer_keywords:
- Lookup Transformation Editor
ms.assetid: f3395c65-0320-47f9-8d83-daaa082d8713
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 23f235ef0506da7ac808d832db6ac36d53cfa604
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596107"
---
# <a name="lookup-transformation-editor-advanced-page"></a><span data-ttu-id="e127c-102">查閱轉換編輯器 (進階頁面)</span><span class="sxs-lookup"><span data-stu-id="e127c-102">Lookup Transformation Editor (Advanced Page)</span></span>
  <span data-ttu-id="e127c-103">使用 [查閱轉換編輯器]\*\*\*\* 對話方塊的 [進階]\*\*\*\* 頁面，即可設定部分快取並修改查閱轉換的 SQL 陳述式。</span><span class="sxs-lookup"><span data-stu-id="e127c-103">Use the **Advanced** page of the **Lookup Transformation Editor** dialog box to configure partial caching and to modify the SQL statement for the Lookup transformation.</span></span>  
  
 <span data-ttu-id="e127c-104">若要深入了解查閱轉換，請參閱＜ [Lookup Transformation](data-flow/transformations/lookup-transformation.md)＞。</span><span class="sxs-lookup"><span data-stu-id="e127c-104">To learn more about the Lookup transformation, see [Lookup Transformation](data-flow/transformations/lookup-transformation.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="e127c-105">選項</span><span class="sxs-lookup"><span data-stu-id="e127c-105">Options</span></span>  
 <span data-ttu-id="e127c-106">**快取大小 (32 位元)**</span><span class="sxs-lookup"><span data-stu-id="e127c-106">**Cache size (32-bit)**</span></span>  
 <span data-ttu-id="e127c-107">調整 32 位元電腦的快取大小 (以 MB 為單位)。</span><span class="sxs-lookup"><span data-stu-id="e127c-107">Adjust the  cache size (in megabytes) for 32-bit computers.</span></span> <span data-ttu-id="e127c-108">預設值是 5 MB。</span><span class="sxs-lookup"><span data-stu-id="e127c-108">The default value is 5 megabytes.</span></span>  
  
 <span data-ttu-id="e127c-109">**快取大小 (64 位元)**</span><span class="sxs-lookup"><span data-stu-id="e127c-109">**Cache size (64-bit)**</span></span>  
 <span data-ttu-id="e127c-110">調整 64 位元電腦的快取大小 (以 MB 為單位)。</span><span class="sxs-lookup"><span data-stu-id="e127c-110">Adjust the cache size (in megabytes) for 64-bit computers.</span></span> <span data-ttu-id="e127c-111">預設值是 5 MB。</span><span class="sxs-lookup"><span data-stu-id="e127c-111">The default value is 5 megabytes.</span></span>  
  
 <span data-ttu-id="e127c-112">**針對無相符項目的資料列啟用快取**</span><span class="sxs-lookup"><span data-stu-id="e127c-112">**Enable cache for rows with no matching entries**</span></span>  
 <span data-ttu-id="e127c-113">將參考資料集中沒有相符項目的資料列存入快取。</span><span class="sxs-lookup"><span data-stu-id="e127c-113">Cache rows with no matching entries in the reference dataset.</span></span>  
  
 <span data-ttu-id="e127c-114">**來自快取的配置**</span><span class="sxs-lookup"><span data-stu-id="e127c-114">**Allocation from cache**</span></span>  
 <span data-ttu-id="e127c-115">指定針對在資料集中沒有相符項目的資料列所配置的快取百分比。</span><span class="sxs-lookup"><span data-stu-id="e127c-115">Specify the percentage of the cache to allocate for rows with no matching entries in the reference dataset.</span></span>  
  
 <span data-ttu-id="e127c-116">**修改 SQL 陳述式**</span><span class="sxs-lookup"><span data-stu-id="e127c-116">**Modify the SQL statement**</span></span>  
 <span data-ttu-id="e127c-117">修改用來產生參考資料集的 SQL 陳述式。</span><span class="sxs-lookup"><span data-stu-id="e127c-117">Modify the SQL statement that is used to generate the reference dataset.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e127c-118">在此頁面上所指定的選擇性 SQL 陳述式會覆寫並取代在 [查閱轉換編輯器]\*\*\*\* 的 [連接]\*\*\*\* 頁面上所指定的資料表名稱。</span><span class="sxs-lookup"><span data-stu-id="e127c-118">The optional SQL statement that you specify on this page overrides and replaces the table name that you specified on the **Connection** page of the **Lookup Transformation Editor**.</span></span> <span data-ttu-id="e127c-119">如需詳細資訊，請參閱 [查閱轉換編輯器 &#40;連接頁面&#41;](../../2014/integration-services/lookup-transformation-editor-connection-page.md)＞。</span><span class="sxs-lookup"><span data-stu-id="e127c-119">For more information, see [Lookup Transformation Editor &#40;Connection Page&#41;](../../2014/integration-services/lookup-transformation-editor-connection-page.md).</span></span>  
  
 <span data-ttu-id="e127c-120">**設定參數**</span><span class="sxs-lookup"><span data-stu-id="e127c-120">**Set Parameters**</span></span>  
 <span data-ttu-id="e127c-121">使用 [設定查詢參數]\*\*\*\* 對話方塊，即可將輸入資料行對應至參數。</span><span class="sxs-lookup"><span data-stu-id="e127c-121">Map input columns to parameters by using the **Set Query Parameters** dialog box.</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="e127c-122">外部資源</span><span class="sxs-lookup"><span data-stu-id="e127c-122">External Resources</span></span>  
 <span data-ttu-id="e127c-123">blogs.msdn.com 上的部落格文章： [查閱快取模式](https://go.microsoft.com/fwlink/?LinkId=219518)</span><span class="sxs-lookup"><span data-stu-id="e127c-123">Blog entry, [Lookup cache modes](https://go.microsoft.com/fwlink/?LinkId=219518) on blogs.msdn.com</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e127c-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e127c-124">See Also</span></span>  
 <span data-ttu-id="e127c-125">[查閱轉換編輯器 &#40;一般頁面&#41;](general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="e127c-125">[Lookup Transformation Editor &#40;General Page&#41;](general-page-of-integration-services-designers-options.md) </span></span>  
 <span data-ttu-id="e127c-126">[查閱轉換編輯器 &#40;連接頁面&#41;](../../2014/integration-services/lookup-transformation-editor-connection-page.md) </span><span class="sxs-lookup"><span data-stu-id="e127c-126">[Lookup Transformation Editor &#40;Connection Page&#41;](../../2014/integration-services/lookup-transformation-editor-connection-page.md) </span></span>  
 <span data-ttu-id="e127c-127">[查閱轉換編輯器 &#40;資料行頁面&#41;](../../2014/integration-services/lookup-transformation-editor-columns-page.md) </span><span class="sxs-lookup"><span data-stu-id="e127c-127">[Lookup Transformation Editor &#40;Columns Page&#41;](../../2014/integration-services/lookup-transformation-editor-columns-page.md) </span></span>  
 <span data-ttu-id="e127c-128">[查閱轉換編輯器 &#40;錯誤輸出頁面&#41;](../../2014/integration-services/lookup-transformation-editor-error-output-page.md) </span><span class="sxs-lookup"><span data-stu-id="e127c-128">[Lookup Transformation Editor &#40;Error Output Page&#41;](../../2014/integration-services/lookup-transformation-editor-error-output-page.md) </span></span>  
 <span data-ttu-id="e127c-129">[Integration Services 錯誤和訊息參考](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="e127c-129">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 [<span data-ttu-id="e127c-130">模糊查閱轉換</span><span class="sxs-lookup"><span data-stu-id="e127c-130">Fuzzy Lookup Transformation</span></span>](data-flow/transformations/fuzzy-lookup-transformation.md)  
  
  
