---
title: 修改篩選 (SQL Server Profiler) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- filters [SQL Server], modifying
- modifying filters, modifying
- filters [SQL Server], traces
ms.assetid: 8b317813-4918-4485-b930-77b1951aa00c
author: stevestein
ms.author: sstein
ms.openlocfilehash: 5a7bab18952820a3dc49c9479797a411521f8e71
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594885"
---
# <a name="modify-a-filter-sql-server-profiler"></a><span data-ttu-id="2784e-102">修改篩選 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="2784e-102">Modify a Filter (SQL Server Profiler)</span></span>
  <span data-ttu-id="2784e-103">您可以將篩選加入包含追蹤定義的追蹤範本，以限制追蹤所蒐集的事件數目。</span><span class="sxs-lookup"><span data-stu-id="2784e-103">You add filters to trace templates, which contain the trace definitions, to limit the number of events that are gathered by a trace.</span></span> <span data-ttu-id="2784e-104">限制蒐集的事件數目可以降低追蹤的效能影響。</span><span class="sxs-lookup"><span data-stu-id="2784e-104">Limiting the number of events gathered can reduce the performance effects of tracing.</span></span> <span data-ttu-id="2784e-105">如果您設定追蹤範本的篩選，但發現追蹤並未蒐集您所需要的資訊種類，您就可以編輯篩選。</span><span class="sxs-lookup"><span data-stu-id="2784e-105">If you set filters for a trace template and find that the trace is not gathering the kind of information that you need, you can edit the filter.</span></span>  
  
### <a name="to-modify-a-filter"></a><span data-ttu-id="2784e-106">若要修改篩選</span><span class="sxs-lookup"><span data-stu-id="2784e-106">To modify a filter</span></span>  
  
1.  <span data-ttu-id="2784e-107">在 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]中，開啟您要修改的追蹤篩選範本。</span><span class="sxs-lookup"><span data-stu-id="2784e-107">In [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)], open the template for the trace filter that you want to modify.</span></span> <span data-ttu-id="2784e-108">在 [檔案]  功能表上，按一下 [範本]  ，然後選擇 [編輯範本]  。</span><span class="sxs-lookup"><span data-stu-id="2784e-108">On the **File** menu, click **Templates**, and then choose **Edit Template**.</span></span>  
  
2.  <span data-ttu-id="2784e-109">在 [追蹤範本屬性] 對話方塊的 [一般] 索引標籤中，從 [選取範本名稱] 清單中選取範本。</span><span class="sxs-lookup"><span data-stu-id="2784e-109">In the **General** tab of the **Trace Template Properties** dialog, select a template from the **Select template name** list.</span></span>  
  
3.  <span data-ttu-id="2784e-110">按一下 [事件選取範圍]  索引標籤。</span><span class="sxs-lookup"><span data-stu-id="2784e-110">Click the **Events Selection** tab.</span></span>  
  
     <span data-ttu-id="2784e-111">**[事件選取範圍]** 索引標籤包含方格控制項。</span><span class="sxs-lookup"><span data-stu-id="2784e-111">The **Events Selection** tab contains a grid control.</span></span> <span data-ttu-id="2784e-112">方格控制項是包含每一個可追蹤事件類別的資料表。</span><span class="sxs-lookup"><span data-stu-id="2784e-112">The grid control is a table that contains each of the traceable event classes.</span></span> <span data-ttu-id="2784e-113">資料表針對每個事件類別包含一個資料列。</span><span class="sxs-lookup"><span data-stu-id="2784e-113">The table contains one row for each event class.</span></span> <span data-ttu-id="2784e-114">事件類別可能會依您所連接的伺服器類型與版本而稍有不同。</span><span class="sxs-lookup"><span data-stu-id="2784e-114">The event classes may differ slightly, depending on the type and version of server to which you are connected.</span></span> <span data-ttu-id="2784e-115">事件類別在方格的 [事件]  資料行中識別，並依事件類別目錄分組。</span><span class="sxs-lookup"><span data-stu-id="2784e-115">The event classes are identified in the **Events**column of the grid and are grouped by event category.</span></span> <span data-ttu-id="2784e-116">其餘資料行會列出可針對每個事件類別傳回的資料行。</span><span class="sxs-lookup"><span data-stu-id="2784e-116">The remaining columns list the data columns that can be returned for each event class.</span></span>  
  
4.  <span data-ttu-id="2784e-117">按一下 [資料行篩選]  。</span><span class="sxs-lookup"><span data-stu-id="2784e-117">Click **Column Filters**.</span></span>  
  
5.  <span data-ttu-id="2784e-118">在 [編輯篩選]  對話方塊中，按一下您要編輯之比較運算子旁的值，然後輸入新的值或刪除一個值。</span><span class="sxs-lookup"><span data-stu-id="2784e-118">In the **Edit Filter** dialog box, click the value next to the comparison operator that you want to edit, and type the new value or delete a value.</span></span> <span data-ttu-id="2784e-119">您也可以加入其他篩選。</span><span class="sxs-lookup"><span data-stu-id="2784e-119">You can also add additional filters.</span></span>  
  
6.  <span data-ttu-id="2784e-120">按一下 [確定]  並儲存範本。</span><span class="sxs-lookup"><span data-stu-id="2784e-120">Click **OK** and save the template.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2784e-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2784e-121">See Also</span></span>  
 [<span data-ttu-id="2784e-122">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="2784e-122">SQL Server Profiler</span></span>](sql-server-profiler.md)  
  
  
