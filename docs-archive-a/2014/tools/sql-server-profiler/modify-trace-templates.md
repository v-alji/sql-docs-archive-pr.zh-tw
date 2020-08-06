---
title: 修改追蹤範本 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- templates [SQL Server], SQL Server Profiler
- Profiler [SQL Server Profiler], templates
- trace templates [SQL Server]
- modifying trace templates
- SQL Server Profiler, templates
ms.assetid: 75b62a54-8d16-4599-bd2d-c42cfcc209f4
author: stevestein
ms.author: sstein
ms.openlocfilehash: 4a26d0a70f65b6ff60dcf42ffb98e67dc0d2b52d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585726"
---
# <a name="modify-trace-templates"></a><span data-ttu-id="db911-102">修改追蹤範本</span><span class="sxs-lookup"><span data-stu-id="db911-102">Modify Trace Templates</span></span>
  <span data-ttu-id="db911-103">您可以在執行 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 的本機電腦上，修改儲存於檔案中的範本。</span><span class="sxs-lookup"><span data-stu-id="db911-103">You can modify templates that are saved in a file on the local computer on which [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] is running.</span></span> <span data-ttu-id="db911-104">您也可以修改從這些檔案中衍生的範本。</span><span class="sxs-lookup"><span data-stu-id="db911-104">You can also modify templates derived from those files.</span></span> <span data-ttu-id="db911-105">當您修改現有的範本時，可在 [追蹤屬性]  對話方塊的 [事件選取範圍]  索引標籤上，以原本設定屬性的相同順序來編輯範本屬性，如事件類別與資料行。</span><span class="sxs-lookup"><span data-stu-id="db911-105">When you modify existing templates, you edit template properties such as event classes and data columns, in the same order that the properties were set originally, on the **Events Selection** tab of the **Trace Properties** dialog box.</span></span> <span data-ttu-id="db911-106">事件類別與資料行可以新增或移除，且篩選也可以變更。</span><span class="sxs-lookup"><span data-stu-id="db911-106">Event classes and data columns can be added or removed, and filters can be changed.</span></span> <span data-ttu-id="db911-107">範本遭修改後，即會建立使用者特定範本，而原始系統範本則不受影響。</span><span class="sxs-lookup"><span data-stu-id="db911-107">After the template is modified, a user-specific template is created and the original system template is left intact.</span></span> <span data-ttu-id="db911-108">如需詳細資訊，請參閱 [儲存追蹤及追蹤範本](save-traces-and-trace-templates.md)。</span><span class="sxs-lookup"><span data-stu-id="db911-108">For more information, see [Save Traces and Trace Templates](save-traces-and-trace-templates.md).</span></span>  
  
 <span data-ttu-id="db911-109">如果您不記得用來建立追蹤的原始範本 (或未儲存)，或者您日後想要執行相同的追蹤時，您可能需要從現有的追蹤檔中衍生範本。</span><span class="sxs-lookup"><span data-stu-id="db911-109">You may need to derive a template from an existing trace file if you cannot remember (or have not saved) the original template that was used to create the trace, or if you want to run the same trace at a later date.</span></span> <span data-ttu-id="db911-110">使用現有的追蹤時，您可以檢視屬性，但是不能修改屬性。</span><span class="sxs-lookup"><span data-stu-id="db911-110">When working with existing traces, you can view the properties, but you cannot modify the properties.</span></span> <span data-ttu-id="db911-111">若要修改屬性，請停止或暫停追蹤。</span><span class="sxs-lookup"><span data-stu-id="db911-111">To modify the properties, stop or pause the trace.</span></span> <span data-ttu-id="db911-112">如需詳細資訊，請參閱[從追蹤檔案或追蹤資料表衍生範本 &#40;SQL Server Profiler&#41;](sql-server-profiler.md) 和[從執行中的追蹤衍生範本 &#40;SQL Server Profiler&#41;](derive-a-template-from-a-running-trace-sql-server-profiler.md)。</span><span class="sxs-lookup"><span data-stu-id="db911-112">For more information, see [Derive a Template from a Trace File or Trace Table &#40;SQL Server Profiler&#41;](sql-server-profiler.md) and [Derive a Template from a Running Trace &#40;SQL Server Profiler&#41;](derive-a-template-from-a-running-trace-sql-server-profiler.md).</span></span>  
  
 <span data-ttu-id="db911-113">**若要建立追蹤範本**</span><span class="sxs-lookup"><span data-stu-id="db911-113">**To create a trace template**</span></span>  
  
 [<span data-ttu-id="db911-114">建立追蹤範本 &#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="db911-114">Create a Trace Template &#40;SQL Server Profiler&#41;</span></span>](create-a-trace-template-sql-server-profiler.md)  
  
 <span data-ttu-id="db911-115">**從追蹤範本執行追蹤**</span><span class="sxs-lookup"><span data-stu-id="db911-115">**To run a trace from a trace template**</span></span>  
  
 [<span data-ttu-id="db911-116">建立追蹤 &#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="db911-116">Create a Trace &#40;SQL Server Profiler&#41;</span></span>](create-a-trace-sql-server-profiler.md)  
  
 <span data-ttu-id="db911-117">**若要修改追蹤範本**</span><span class="sxs-lookup"><span data-stu-id="db911-117">**To modify a trace template**</span></span>  
  
 [<span data-ttu-id="db911-118">使用 SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="db911-118">Using SQL Server Profiler</span></span>](../../database-engine/modify-a-trace-template-sql-server-profiler.md)  
  
 [<span data-ttu-id="db911-119">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="db911-119">Using Transact-SQL</span></span>](../../relational-databases/sql-trace/modify-an-existing-trace-transact-sql.md)  
  
 <span data-ttu-id="db911-120">**若要從追蹤範本或追蹤檔中新增或移除事件**</span><span class="sxs-lookup"><span data-stu-id="db911-120">**To add or remove events from a trace template or trace file**</span></span>  
  
 [<span data-ttu-id="db911-121">使用 SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="db911-121">Using SQL Server Profiler</span></span>](specify-events-and-data-columns-for-a-trace-file-sql-server-profiler.md)  
  
 [<span data-ttu-id="db911-122">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="db911-122">Using Transact-SQL</span></span>](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)  
  
## <a name="see-also"></a><span data-ttu-id="db911-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="db911-123">See Also</span></span>  
 [<span data-ttu-id="db911-124">啟動追蹤</span><span class="sxs-lookup"><span data-stu-id="db911-124">Start a Trace</span></span>](start-a-trace.md)  
  
  
