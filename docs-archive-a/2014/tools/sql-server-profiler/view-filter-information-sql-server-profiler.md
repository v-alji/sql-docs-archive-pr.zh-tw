---
title: 視圖篩選資訊 (SQL Server Profiler) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- displaying filter information
- filters [SQL Server], viewing
- filters [SQL Server], traces
- traces [SQL Server], filters
- viewing filter information
ms.assetid: 8d002dea-376a-452c-b3ca-3e93656ed75f
author: stevestein
ms.author: sstein
ms.openlocfilehash: 931b83f8087d446cfc7b08d9582cbad5b02cf671
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593738"
---
# <a name="view-filter-information-sql-server-profiler"></a><span data-ttu-id="52f64-102">檢視篩選資訊 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="52f64-102">View Filter Information (SQL Server Profiler)</span></span>
  <span data-ttu-id="52f64-103">此主題描述如何使用 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]，在事件類別的資料行上檢視篩選。</span><span class="sxs-lookup"><span data-stu-id="52f64-103">This topic describes how to view filters on data columns for event classes by using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span>  
  
### <a name="to-view-filter-information"></a><span data-ttu-id="52f64-104">若要檢視篩選資訊</span><span class="sxs-lookup"><span data-stu-id="52f64-104">To view filter information</span></span>  
  
1.  <span data-ttu-id="52f64-105">開啟追蹤檔案、追蹤資料表或 SQL 指令碼，然後在 [檔案] 功能表上按一下 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="52f64-105">Open a trace file, trace table, or SQL script, and on the **File** menu, click **Properties**.</span></span> <span data-ttu-id="52f64-106">如果您正在編輯追蹤範本或正在建立新追蹤，請略過此步驟。</span><span class="sxs-lookup"><span data-stu-id="52f64-106">If you are editing a trace template or creating a new trace, skip this step.</span></span>  
  
2.  <span data-ttu-id="52f64-107">在 [事件選取範圍] 索引標籤上，以滑鼠右鍵按一下要檢視之篩選的資料行名稱，然後按一下 [編輯資料行篩選]。</span><span class="sxs-lookup"><span data-stu-id="52f64-107">On the **Events Selection** tab, right-click the data column name for the filter you want to view, and click **Edit Column Filter**.</span></span>  
  
3.  <span data-ttu-id="52f64-108">在 [編輯篩選] 對話方塊中，展開篩選比較運算子，查看所指定條件已指派的值。</span><span class="sxs-lookup"><span data-stu-id="52f64-108">In the **Edit Filter** dialog box, expand the filter comparison operators to see the assigned value for the specified criterion.</span></span> <span data-ttu-id="52f64-109">對於您要檢視篩選資訊的所有資料行，重複步驟 2 和 3。</span><span class="sxs-lookup"><span data-stu-id="52f64-109">Repeat Steps 2 and 3 for all columns for which you want to view filter information.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="52f64-110">已指派值的比較運算子會顯示為粗體格式。</span><span class="sxs-lookup"><span data-stu-id="52f64-110">Comparison operators with assigned values are formatted bold.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52f64-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="52f64-111">See Also</span></span>  
 [<span data-ttu-id="52f64-112">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="52f64-112">SQL Server Profiler</span></span>](sql-server-profiler.md)  
  
  
