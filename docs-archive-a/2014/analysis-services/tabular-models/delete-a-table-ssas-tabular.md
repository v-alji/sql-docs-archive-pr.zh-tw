---
title: 刪除 (SSAS 表格式) 的資料表 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: be4ed45f-fde3-466c-9869-49bd3ddb505e
author: minewiskan
ms.author: owend
ms.openlocfilehash: c72fa90426440c1be84318a15cf0d761ef16aca8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598518"
---
# <a name="delete-a-table-ssas-tabular"></a><span data-ttu-id="03b8e-102">刪除資料表 (SSAS 表格式)</span><span class="sxs-lookup"><span data-stu-id="03b8e-102">Delete a Table (SSAS Tabular)</span></span>
  <span data-ttu-id="03b8e-103">在模型設計師中，您可以刪除模型工作空間資料庫中不再需要的資料表。</span><span class="sxs-lookup"><span data-stu-id="03b8e-103">In the model designer, you can delete tables in your model workspace database that you no longer need.</span></span> <span data-ttu-id="03b8e-104">刪除資料表並不會影響原始來源資料，只會影響您匯入並在其中處理的資料。</span><span class="sxs-lookup"><span data-stu-id="03b8e-104">Deleting a table does not affect the original source data, only the data that you imported and were working with.</span></span> <span data-ttu-id="03b8e-105">您無法恢復資料表的刪除作業。</span><span class="sxs-lookup"><span data-stu-id="03b8e-105">You cannot undo the deletion of a table.</span></span>  
  
### <a name="to-delete-a-table"></a><span data-ttu-id="03b8e-106">刪除資料表</span><span class="sxs-lookup"><span data-stu-id="03b8e-106">To delete a table</span></span>  
  
-   <span data-ttu-id="03b8e-107">針對您要刪除的資料表，以滑鼠右鍵按一下模型設計師底部的索引標籤，然後按一下 [刪除]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="03b8e-107">Right-click the tab at the bottom of the model designer for the table that you want to delete, and then click **Delete**.</span></span>  
  
## <a name="considerations-when-deleting-tables"></a><span data-ttu-id="03b8e-108">刪除資料表時的考量</span><span class="sxs-lookup"><span data-stu-id="03b8e-108">Considerations when Deleting Tables</span></span>  
  
-   <span data-ttu-id="03b8e-109">當您刪除資料表時，資料表所在的整個索引標籤都會遭到刪除。</span><span class="sxs-lookup"><span data-stu-id="03b8e-109">When you delete a table, the entire tab that the table was on is deleted.</span></span>  
  
-   <span data-ttu-id="03b8e-110">如果有任何量值與該資料表相關聯，則也會刪除該量值的定義。</span><span class="sxs-lookup"><span data-stu-id="03b8e-110">If any measures were associated with that table, the definition of the measure will also be deleted.</span></span>  
  
-   <span data-ttu-id="03b8e-111">如果您使用該資料表建立任何導出資料行，該資料表中的資料行也會遭到刪除；其他資料表中使用已刪除資料表之資料行的所有導出資料行則會顯示錯誤。</span><span class="sxs-lookup"><span data-stu-id="03b8e-111">If you created any calculated columns using that table, columns in that table are also deleted; any calculated columns in other tables that use columns from the deleted table will display an error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03b8e-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="03b8e-112">See Also</span></span>  
 [<span data-ttu-id="03b8e-113">資料表與資料行 &#40;SSAS 表格式&#41;</span><span class="sxs-lookup"><span data-stu-id="03b8e-113">Tables and Columns &#40;SSAS Tabular&#41;</span></span>](tables-and-columns-ssas-tabular.md)  
  
  
