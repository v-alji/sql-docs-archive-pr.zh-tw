---
title: 排序資料表中的資料 (SSAS 表格式) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 5fa6ad56-bf68-4aac-a226-52556173b7e2
author: minewiskan
ms.author: owend
ms.openlocfilehash: d9a6636c2c11fc571e8d4c1bcbc25c1e02d815fb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686485"
---
# <a name="sort-data-in-a-table-ssas-tabular"></a><span data-ttu-id="221c9-102">排序資料表中的資料 (SSAS 表格式)</span><span class="sxs-lookup"><span data-stu-id="221c9-102">Sort Data in a Table (SSAS Tabular)</span></span>
  <span data-ttu-id="221c9-103">您可以依一個或多個資料行中的文字 (A 到 Z 或 Z 到 A) 和數字 (最小到最大或最大到最小) 來排序資料。</span><span class="sxs-lookup"><span data-stu-id="221c9-103">You can sort data by text (A to Z or Z to A) and numbers (smallest to largest or largest to smallest) in one or more columns.</span></span>  
  
### <a name="to-sort-the-data-in-a-table-based-on-a-text-column"></a><span data-ttu-id="221c9-104">根據文字資料行排序資料表中的資料</span><span class="sxs-lookup"><span data-stu-id="221c9-104">To sort the data in a table based on a text column</span></span>  
  
1.  <span data-ttu-id="221c9-105">在模型設計師中，選取英數資料的資料行、資料行中的資料格範圍，或確認作用中資料格位於包含英數資料的資料表資料行中，然後按一下您要做為篩選依據的資料行標頭中的箭號。</span><span class="sxs-lookup"><span data-stu-id="221c9-105">In the model designer, select a column of alphanumeric data, a range of cells in a column, or make sure that the active cell is in a table column that contains alphanumeric data, and then click the arrow in the header of the column that you want to filter by.</span></span>  
  
2.  <span data-ttu-id="221c9-106">在 [自動篩選] 功能表中，執行下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="221c9-106">In the AutoFilter menu, do one of the following:</span></span>  
  
    -   <span data-ttu-id="221c9-107">若要以遞增的英數順序排序，按一下 **[從 A 到 Z 排序]**。</span><span class="sxs-lookup"><span data-stu-id="221c9-107">To sort in ascending alphanumeric order, click **Sort A to Z**.</span></span>  
  
    -   <span data-ttu-id="221c9-108">若要以遞減的英數順序排序，按一下 **[從 Z 到 A 排序]**。</span><span class="sxs-lookup"><span data-stu-id="221c9-108">To sort in descending alphanumeric order, click **Sort Z to A**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="221c9-109">在某些情況下，從其他應用程式匯入的資料在資料前面可能會插入開頭空白。</span><span class="sxs-lookup"><span data-stu-id="221c9-109">In some cases, data imported from another application might have leading spaces inserted before data.</span></span> <span data-ttu-id="221c9-110">您必須移除開頭空白，才能正確排序資料。</span><span class="sxs-lookup"><span data-stu-id="221c9-110">You must remove the leading spaces in order to correctly sort the data.</span></span>  
  
### <a name="to-sort-the-data-in-a-table-based-on-a-numeric-column"></a><span data-ttu-id="221c9-111">根據數字資料行排序資料表中的資料</span><span class="sxs-lookup"><span data-stu-id="221c9-111">To sort the data in a table based on a numeric column</span></span>  
  
1.  <span data-ttu-id="221c9-112">在模型設計師中，選取英數資料的資料行、資料行中的資料格範圍，或確認作用中資料格位於包含英數資料的資料表資料行中，然後按一下您要做為篩選依據的資料行標頭中的箭號。</span><span class="sxs-lookup"><span data-stu-id="221c9-112">In the model designer, select a column of alphanumeric data, a range of cells in a column, or make sure that the active cell is in a table column that contains alphanumeric data, and then click the arrow in the header of the column that you want to filter by.</span></span>  
  
2.  <span data-ttu-id="221c9-113">在 [自動篩選] 功能表中，執行下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="221c9-113">In the AutoFilter menu, do one of the following:</span></span>  
  
    -   <span data-ttu-id="221c9-114">若要從最小的數字排序到最大的數字，按一下 **[從最小到最大排序]**。</span><span class="sxs-lookup"><span data-stu-id="221c9-114">To sort from low numbers to high numbers, click **Sort Smallest to Largest**.</span></span>  
  
    -   <span data-ttu-id="221c9-115">若要從最大的數字排序到最小的數字，按一下 **[從最大到最小排序]**。</span><span class="sxs-lookup"><span data-stu-id="221c9-115">To sort from high numbers to low numbers, click **Sort Largest to Smallest**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="221c9-116">如果結果不如預期，資料行可能會包含儲存為文字而非數字的數字。</span><span class="sxs-lookup"><span data-stu-id="221c9-116">If the results are not what you expected, the column might contain numbers stored as text and not as numbers.</span></span> <span data-ttu-id="221c9-117">例如，從某些會計系統匯入的負數，或者以開頭 ' (單引號) 輸入的數字儲存為文字。</span><span class="sxs-lookup"><span data-stu-id="221c9-117">For example, negative numbers imported from some accounting systems, or a number entered with a leading ' (apostrophe), are stored as text.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="221c9-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="221c9-118">See Also</span></span>  
 <span data-ttu-id="221c9-119">[&#40;SSAS 表格式&#41;篩選和排序資料](../filter-and-sort-data-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="221c9-119">[Filter and Sort Data &#40;SSAS Tabular&#41;](../filter-and-sort-data-ssas-tabular.md) </span></span>  
 <span data-ttu-id="221c9-120">[SSAS 表格式 &#40;的觀點&#41;](perspectives-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="221c9-120">[Perspectives &#40;SSAS Tabular&#41;](perspectives-ssas-tabular.md) </span></span>  
 [<span data-ttu-id="221c9-121">角色 &#40;SSAS 表格式&#41;</span><span class="sxs-lookup"><span data-stu-id="221c9-121">Roles &#40;SSAS Tabular&#41;</span></span>](roles-ssas-tabular.md)  
  
  
