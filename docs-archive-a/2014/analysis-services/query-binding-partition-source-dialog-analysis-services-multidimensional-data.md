---
title: 查詢系結詳細資料 (分割區來源] 對話方塊)  (Analysis Services-多維度資料) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.partitions.partitionfilterexpression.f1
ms.assetid: 697874d4-3f7a-4126-96f5-37cc8e2ee306
author: minewiskan
ms.author: owend
ms.openlocfilehash: 59d2ae1fed9d22366786e21a287a621f08418a5d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596294"
---
# <a name="query-binding-detail-partition-source-dialog-box-analysis-services---multidimensional-data"></a><span data-ttu-id="5ed46-102">查詢繫結詳細資料 (資料分割來源對話方塊) (Analysis Services - 多維度資料)</span><span class="sxs-lookup"><span data-stu-id="5ed46-102">Query Binding Detail (Partition Source Dialog Box) (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="5ed46-103">使用 **[資料分割來源]** 對話方塊中的 **[查詢繫結]** 選項，即可指定為資料分割提供資料的查詢。</span><span class="sxs-lookup"><span data-stu-id="5ed46-103">Use the **Query Binding** option in the **Partition Source** dialog box to specify the query that provides the data for the partition.</span></span> <span data-ttu-id="5ed46-104">您可以從 **[資料分割來源]** 對話方塊的 **[繫結類型]** 選項中，選取 **[查詢繫結]** 來顯示此窗格。</span><span class="sxs-lookup"><span data-stu-id="5ed46-104">You can display this pane by selecting **Query Binding** from the **Binding type** option in the **Partition Source** dialog box.</span></span>  
  
## <a name="options"></a><span data-ttu-id="5ed46-105">選項</span><span class="sxs-lookup"><span data-stu-id="5ed46-105">Options</span></span>  
 <span data-ttu-id="5ed46-106">**資料來源**</span><span class="sxs-lookup"><span data-stu-id="5ed46-106">**Data source**</span></span>  
 <span data-ttu-id="5ed46-107">在執行用來為資料分割提供事實資料的查詢上，選取資料來源。</span><span class="sxs-lookup"><span data-stu-id="5ed46-107">Select the data source on which the query is executed to provide fact data for the partition.</span></span>  
  
 <span data-ttu-id="5ed46-108">**查詢**</span><span class="sxs-lookup"><span data-stu-id="5ed46-108">**Query**</span></span>  
 <span data-ttu-id="5ed46-109">當處理資料分割時，鍵入或修改擷取事實資料時使用的 SQL 陳述式。</span><span class="sxs-lookup"><span data-stu-id="5ed46-109">Type or modify the SQL statement used when retrieving fact data when the partition is processed.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="5ed46-110">指定 WHERE 子句，就可以在這個資料分割使用記錄的子集。</span><span class="sxs-lookup"><span data-stu-id="5ed46-110">By specifying a WHERE clause, a subset of records can be used for this partition.</span></span> <span data-ttu-id="5ed46-111">當有多個分割區以單一事實資料表為基礎時，這是防止資料重複所必要的。</span><span class="sxs-lookup"><span data-stu-id="5ed46-111">This is essential to prevent duplication of data when multiple partitions are based on a single fact table.</span></span> <span data-ttu-id="5ed46-112">如需詳細資訊，請參閱 [資料[分割來源] 對話方塊 &#40;Analysis Services-多維度資料&#41;](partition-source-dialog-box-analysis-services-multidimensional-data.md)。</span><span class="sxs-lookup"><span data-stu-id="5ed46-112">For more information, see [Partition Source Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](partition-source-dialog-box-analysis-services-multidimensional-data.md).</span></span>  
  
 <span data-ttu-id="5ed46-113">**檢查**</span><span class="sxs-lookup"><span data-stu-id="5ed46-113">**Check**</span></span>  
 <span data-ttu-id="5ed46-114">按一下即可確認 [查詢]\*\*\*\* 中的陳述式是否為有效的 SQL 陳述式。</span><span class="sxs-lookup"><span data-stu-id="5ed46-114">Click to verify that the statement in **Query** is a valid SQL statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ed46-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5ed46-115">See Also</span></span>  
 [<span data-ttu-id="5ed46-116">資料分割來源對話方塊 &#40;Analysis Services-多維度資料&#41;</span><span class="sxs-lookup"><span data-stu-id="5ed46-116">Partition Source Dialog Box &#40;Analysis Services - Multidimensional Data&#41;</span></span>](partition-source-dialog-box-analysis-services-multidimensional-data.md)  
  
  
