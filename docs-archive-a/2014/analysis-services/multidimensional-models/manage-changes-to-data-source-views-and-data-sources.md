---
title: 管理資料來源視圖和資料來源的變更 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- modifying data sources
- modifying data source views
- data source views [Analysis Services], schema updates
- data sources [Analysis Services], schema updates
ms.assetid: 928c9f63-365a-43fd-9bbd-78828cc7e54d
author: minewiskan
ms.author: owend
ms.openlocfilehash: 0f558ce6aaf9e57576d5773322352d33b81a3392
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87698641"
---
# <a name="manage-changes-to-data-source-views-and-data-sources"></a><span data-ttu-id="53fd5-102">管理對資料來源檢視及資料來源所做的變更</span><span class="sxs-lookup"><span data-stu-id="53fd5-102">Manage Changes to Data Source Views and Data Sources</span></span>
  <span data-ttu-id="53fd5-103">當結構描述產生精靈重新執行時，會重新使用它在原始產生所使用的相同資料來源和資料來源檢視。</span><span class="sxs-lookup"><span data-stu-id="53fd5-103">When the Schema Generation Wizard is rerun, it reuses the same data source and data source view that it used for the original generation.</span></span> <span data-ttu-id="53fd5-104">如果您加入資料來源或資料來源檢視，精靈不會使用它。</span><span class="sxs-lookup"><span data-stu-id="53fd5-104">If you add a data source or a data source view, the wizard does not use it.</span></span> <span data-ttu-id="53fd5-105">如果您在初始產生之後刪除原始資料來源或資料來源檢視，您必須從頭開始執行精靈。</span><span class="sxs-lookup"><span data-stu-id="53fd5-105">If you delete the original data source or data source view after the initial generation, you must run the wizard from the beginning.</span></span> <span data-ttu-id="53fd5-106">精靈中所有先前的設定也會被刪除。</span><span class="sxs-lookup"><span data-stu-id="53fd5-106">All previous settings in the wizard are also deleted.</span></span> <span data-ttu-id="53fd5-107">下次您執行結構描述產生精靈時，對於基礎資料庫中任何繫結到已刪除之資料來源或資料來源檢視的現有物件，將視同使用者建立的物件來處理。</span><span class="sxs-lookup"><span data-stu-id="53fd5-107">Any existing objects in an underlying database that were bound to a deleted data source or data source view are treated as user-created objects the next time you run the Schema Generation Wizard.</span></span>  
  
 <span data-ttu-id="53fd5-108">如果資料來源檢視在產生時不會反映基礎資料庫的實際狀態，則當「結構描述產生精靈」產生主題領域資料庫的結構描述時，可能會遇到錯誤。</span><span class="sxs-lookup"><span data-stu-id="53fd5-108">If the data source view does not reflect the actual state of the underlying database at the time of generation, the Schema Generation Wizard may encounter errors when it generates the schema for the subject area database.</span></span> <span data-ttu-id="53fd5-109">例如，如果資料來源檢視指定資料行的資料類型為 **int**，但是該資料行的資料類型實際上是 **string**，則「結構描述產生精靈」會將外部索引鍵的資料類型設為 **INT** ，以符合此資料來源檢視，但是當它建立關聯性時會失敗，因為實際資料類型是 **string**。</span><span class="sxs-lookup"><span data-stu-id="53fd5-109">For example, if the data source view specifies that the data type for a column is **int**, but data type for the column is actually **string**, the Schema Generation Wizard sets the data type for the foreign key to **INT** to match the data source view and then fails when it creates the relationship because the actual type is **string**.</span></span>  
  
 <span data-ttu-id="53fd5-110">相反地，如果您將資料來源連接字串，變更為與前一次產生不同的資料庫，則不會產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="53fd5-110">On the other hand, if you change the data source connection string to a different database from the previous generation, no error is generated.</span></span> <span data-ttu-id="53fd5-111">這時會使用新資料庫，且先前的資料庫不會產生任何變更。</span><span class="sxs-lookup"><span data-stu-id="53fd5-111">The new database is used, and no change is made to the previous database.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53fd5-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="53fd5-112">See Also</span></span>  
 [<span data-ttu-id="53fd5-113">了解累加式產生</span><span class="sxs-lookup"><span data-stu-id="53fd5-113">Understanding Incremental Generation</span></span>](understanding-incremental-generation.md)  
  
  
