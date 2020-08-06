---
title: 建立 (SQL Server Profiler) 的追蹤範本 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- templates [SQL Server], traces
- trace templates [SQL Server]
- saving trace template
ms.assetid: 025868b0-3790-4cda-8757-5a58327bfba0
author: stevestein
ms.author: sstein
ms.openlocfilehash: 355f97c7fecd8a9e31f10de881d1ae6df3b8f122
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686595"
---
# <a name="create-a-trace-template-sql-server-profiler"></a><span data-ttu-id="4b583-102">建立追蹤範本 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="4b583-102">Create a Trace Template (SQL Server Profiler)</span></span>
  <span data-ttu-id="4b583-103">此主題描述如何使用 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]來建立新追蹤範本。</span><span class="sxs-lookup"><span data-stu-id="4b583-103">This topic describes how to create a new trace template by using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span>  
  
### <a name="to-create-a-trace-template"></a><span data-ttu-id="4b583-104">若要建立追蹤範本</span><span class="sxs-lookup"><span data-stu-id="4b583-104">To create a trace template</span></span>  
  
1.  <span data-ttu-id="4b583-105">在 **[檔案]** 功能表上，指向 **[範本]** ，然後按一下 **[新增範本]** 。</span><span class="sxs-lookup"><span data-stu-id="4b583-105">On the **File** menu, point to **Templates**, and then click **New Template**.</span></span>  
  
2.  <span data-ttu-id="4b583-106">在 [追蹤範本屬性]  對話方塊中，從 [選取伺服器類型]  清單中選取伺服器類型。</span><span class="sxs-lookup"><span data-stu-id="4b583-106">In the **Trace Template Properties** dialog box, select a server type from the **Select server type**list.</span></span>  
  
3.  <span data-ttu-id="4b583-107">在 **[新範本名稱]** 方塊中，輸入範本名稱。</span><span class="sxs-lookup"><span data-stu-id="4b583-107">In the **New template name** box, enter a template name.</span></span>  
  
4.  <span data-ttu-id="4b583-108">(選擇性) 按一下 **[以現有的範本作為新範本的基礎]** ，然後從清單中選取範本。</span><span class="sxs-lookup"><span data-stu-id="4b583-108">Optionally, click **Base new template on existing one**, and then select a template from the list.</span></span>  
  
     <span data-ttu-id="4b583-109">所有事件、資料行與篩選會依所選取範本的指定來初始設定。</span><span class="sxs-lookup"><span data-stu-id="4b583-109">All events, data columns, and filters are initially set as specified in the selected template.</span></span>  
  
5.  <span data-ttu-id="4b583-110">(選擇性) 按一下 **[作為所選取伺服器類型的預設範本]** 。</span><span class="sxs-lookup"><span data-stu-id="4b583-110">Optionally, click **Use as a default template for selected server type**.</span></span>  
  
6.  <span data-ttu-id="4b583-111">在 **[事件選取範圍]** 索引標籤上，新增、移除或修改事件、資料行或篩選。</span><span class="sxs-lookup"><span data-stu-id="4b583-111">On the **Events Selection** tab, add, remove, or modify events, data columns, or filters.</span></span>  
  
7.  <span data-ttu-id="4b583-112">在 **[事件選取範圍]** 索引標籤上，使用方格控制項，在追蹤檔案中新增或移除事件和資料行，如下所示：</span><span class="sxs-lookup"><span data-stu-id="4b583-112">On the **Events Selection**tab, use the grid control to add or remove events and data columns from the trace file as follows:</span></span>  
  
    -   <span data-ttu-id="4b583-113">若要加入事件，請在 **[事件]** 資料行中展開適當的事件類別目錄，然後選取事件名稱。</span><span class="sxs-lookup"><span data-stu-id="4b583-113">To add an event, expand the appropriate event category in the **Events** column, and then select the event name.</span></span>  
  
    -   <span data-ttu-id="4b583-114">當您加入事件時，依預設將包含所有有關的資料行。</span><span class="sxs-lookup"><span data-stu-id="4b583-114">When you add an event, all relevant data columns are included by default.</span></span> <span data-ttu-id="4b583-115">若要從追蹤中移除某個事件的資料行，請清除該事件在資料行中的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="4b583-115">To remove a data column for an event from a trace, clear the check box in the data column for the event.</span></span>  
  
    -   <span data-ttu-id="4b583-116">若要加入篩選，在 **[編輯篩選]** 對話方塊中按一下資料行名稱，然後指定篩選準則。</span><span class="sxs-lookup"><span data-stu-id="4b583-116">To add filters, click the data column name and specify the filter criteria in the **Edit Filter** dialog box.</span></span> <span data-ttu-id="4b583-117">您也可以用滑鼠右鍵按一下資料行名稱，然後按一下 [編輯資料行篩選]  以啟動 [編輯篩選]  對話方塊。</span><span class="sxs-lookup"><span data-stu-id="4b583-117">You can also right-click the data column name, and click **Edit Column Filter** to launch the **Edit Filter** dialog box.</span></span> <span data-ttu-id="4b583-118">按一下 **[確定]** 以加入篩選。</span><span class="sxs-lookup"><span data-stu-id="4b583-118">Click **OK** to add the filter.</span></span>  
  
8.  <span data-ttu-id="4b583-119">按一下 [儲存]  。</span><span class="sxs-lookup"><span data-stu-id="4b583-119">Click **Save.**</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b583-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4b583-120">See Also</span></span>  
 <span data-ttu-id="4b583-121">[指定追蹤檔案的事件及資料行 &#40;SQL Server Profiler&#41;](specify-events-and-data-columns-for-a-trace-file-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="4b583-121">[Specify Events and Data Columns for a Trace File &#40;SQL Server Profiler&#41;](specify-events-and-data-columns-for-a-trace-file-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="4b583-122">[從執行中的追蹤衍生範本 &#40;SQL Server Profiler&#41;](derive-a-template-from-a-running-trace-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="4b583-122">[Derive a Template from a Running Trace &#40;SQL Server Profiler&#41;](derive-a-template-from-a-running-trace-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="4b583-123">[從追蹤檔案或追蹤資料表衍生範本 &#40;SQL Server Profiler&#41;](derive-a-template-from-a-trace-file-or-trace-table-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="4b583-123">[Derive a Template from a Trace File or Trace Table &#40;SQL Server Profiler&#41;](derive-a-template-from-a-trace-file-or-trace-table-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="4b583-124">[SQL Server Profiler 範本和權限](sql-server-profiler-templates-and-permissions.md) </span><span class="sxs-lookup"><span data-stu-id="4b583-124">[SQL Server Profiler Templates and Permissions](sql-server-profiler-templates-and-permissions.md) </span></span>  
 [<span data-ttu-id="4b583-125">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="4b583-125">SQL Server Profiler</span></span>](sql-server-profiler.md)  
  
  
