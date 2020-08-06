---
title: 限制資料列 (分割區 Wizard) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.partitionwizard.typefilterexpression.f1
ms.assetid: eec8da8f-eab4-4ac4-a81d-995c814f88ca
author: minewiskan
ms.author: owend
ms.openlocfilehash: 9b0acc9ab24cfe92877d9abcd86353c85b4f8905
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592942"
---
# <a name="restrict-rows-partition-wizard"></a><span data-ttu-id="672c9-102">限制資料列 (資料分割精靈)</span><span class="sxs-lookup"><span data-stu-id="672c9-102">Restrict Rows (Partition Wizard)</span></span>
  <span data-ttu-id="672c9-103">使用 [限制資料列]\*\*\*\* 頁面，即可限制從指定之資料表中擷取且將彙總並納入資料分割中的資料列。</span><span class="sxs-lookup"><span data-stu-id="672c9-103">Use the **Restrict Rows** page to restrict the rows that will be retrieved from the specified table and will be aggregated and included in the partition.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="672c9-104">唯有在 [指定來源資訊]\*\*\*\* 頁面中選取了單一資料表之後，才會顯示此頁面。</span><span class="sxs-lookup"><span data-stu-id="672c9-104">This page is appears only if you selected a single table in the **Specify Source Information** page.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="672c9-105">如果在其他分割區所使用的 [指定來源資訊]\*\*\*\* 頁面上，指定了 [可用的資料表]\*\*\*\* 中的某資料表，您就必須在 [限制資料列]\*\*\*\* 頁面中提供查詢，或者接受在 Cube 中可能會有重複資料的風險。</span><span class="sxs-lookup"><span data-stu-id="672c9-105">If you specified a table in **Available Tables** on the **Specify Source Information** page that is used by another partition, you must provide a query in the **Restrict Rows** page or risk duplicating data in the cube.</span></span>  
  
## <a name="options"></a><span data-ttu-id="672c9-106">選項</span><span class="sxs-lookup"><span data-stu-id="672c9-106">Options</span></span>  
 <span data-ttu-id="672c9-107">**指定查詢來限制資料列**</span><span class="sxs-lookup"><span data-stu-id="672c9-107">**Specify a query to restrict rows**</span></span>  
 <span data-ttu-id="672c9-108">選取即可在 [查詢]\*\*\*\* 方塊中，輸入限制資料列的查詢。</span><span class="sxs-lookup"><span data-stu-id="672c9-108">Select to enter a query that restricts rows into the **Query** box.</span></span>  
  
 <span data-ttu-id="672c9-109">如果在選取此選項時，[提供 WHERE 子句]\*\*\*\* 是空的，該選項就會使用 SQL 陳述式，從先前選取之資料表中擷取所有的資料行與資料列來進行擴展。</span><span class="sxs-lookup"><span data-stu-id="672c9-109">If **Supply a WHERE clause** is empty when this option is selected, that option is populated with an SQL statement that retrieves all columns and all rows from the previously selected table.</span></span>  
  
 <span data-ttu-id="672c9-110">**查詢**</span><span class="sxs-lookup"><span data-stu-id="672c9-110">**Query**</span></span>  
 <span data-ttu-id="672c9-111">鍵入或修改處理資料分割時，從資料表中擷取資料列所使用的 SQL 陳述式。</span><span class="sxs-lookup"><span data-stu-id="672c9-111">Type or modify the SQL statement used when retrieving rows from the table when the partition is processed.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="672c9-112">指定 WHERE 子句，就可以在這個資料分割使用記錄的子集。</span><span class="sxs-lookup"><span data-stu-id="672c9-112">By specifying a WHERE clause, a subset of records can be used for this partition.</span></span> <span data-ttu-id="672c9-113">當有多個分割區以單一事實資料表為基礎時，這是防止資料重複所必要的。</span><span class="sxs-lookup"><span data-stu-id="672c9-113">This is essential to prevent duplication of data when multiple partitions are based on a single fact table.</span></span>  
  
 <span data-ttu-id="672c9-114">**檢查**</span><span class="sxs-lookup"><span data-stu-id="672c9-114">**Check**</span></span>  
 <span data-ttu-id="672c9-115">驗證 [查詢]\*\*\*\* 中的陳述式是否為有效的 SQL 陳述式。</span><span class="sxs-lookup"><span data-stu-id="672c9-115">Verifies that the statement in **Query** is a valid SQL statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="672c9-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="672c9-116">See Also</span></span>  
 [<span data-ttu-id="672c9-117">資料分割 &#40;Analysis Services - 多維度資料&#41;</span><span class="sxs-lookup"><span data-stu-id="672c9-117">Partitions &#40;Analysis Services - Multidimensional Data&#41;</span></span>](multidimensional-models-olap-logical-cube-objects/partitions-analysis-services-multidimensional-data.md)  
  
  
