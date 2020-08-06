---
title: 修改追蹤範本 (SQL Server Profiler) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- templates [SQL Server], traces
- trace templates [SQL Server]
- modifying traces
ms.assetid: b81df2a1-e202-43d8-92b0-0beb145f0116
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 2a93baedb1875ac740e74065ae7188f9b576e083
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592192"
---
# <a name="modify-a-trace-template-sql-server-profiler"></a><span data-ttu-id="350ac-102">修改追蹤範本 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="350ac-102">Modify a Trace Template (SQL Server Profiler)</span></span>
  <span data-ttu-id="350ac-103">本主題說明如何使用 [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)]來修改追蹤範本。</span><span class="sxs-lookup"><span data-stu-id="350ac-103">This topic describes how to modify a trace template by using [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)].</span></span>  
  
### <a name="to-modify-a-trace-template"></a><span data-ttu-id="350ac-104">若要修改追蹤範本</span><span class="sxs-lookup"><span data-stu-id="350ac-104">To modify a trace template</span></span>  
  
1.  <span data-ttu-id="350ac-105">在 [檔案]\*\*\*\* 功能表上，指向 [範本]\*\*\*\*，再按一下 [編輯範本]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="350ac-105">On the **File** menu, point to **Templates**, and then click **Edit Template**.</span></span>  
  
2.  <span data-ttu-id="350ac-106">在 [追蹤範本屬性]\*\*\*\* 對話方塊的 [一般]\*\*\*\* 索引標籤上，您可以修改伺服器類型和範本名稱，或選擇使用該伺服器類型的預設範本。</span><span class="sxs-lookup"><span data-stu-id="350ac-106">In the **Trace Template Properties** dialog box, on the **General** tab, you can modify the server type and template name, or choose to use a default template for the server type.</span></span>  
  
3.  <span data-ttu-id="350ac-107">在 [事件選取範圍]\*\*\*\* 索引標籤上，使用方格控制項，在追蹤檔案中新增或移除事件和資料行，如下所示：</span><span class="sxs-lookup"><span data-stu-id="350ac-107">On the **Events Selection**tab, use the grid control to add or remove events and data columns from the trace file as follows.</span></span>  
  
    -   <span data-ttu-id="350ac-108">若要加入事件，請在 **[事件]** 資料行中展開適當的事件類別目錄，然後選取事件名稱。</span><span class="sxs-lookup"><span data-stu-id="350ac-108">To add an event, expand the appropriate event category in the **Events** column, and then select the event name.</span></span>  
  
    -   <span data-ttu-id="350ac-109">當您加入事件時，依預設將包含所有有關的資料行。</span><span class="sxs-lookup"><span data-stu-id="350ac-109">When you add an event, all relevant data columns are included by default.</span></span> <span data-ttu-id="350ac-110">若要從追蹤中移除某個事件的資料行，請清除該事件在資料行中的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="350ac-110">To remove a data column for an event from a trace, clear the check box in the data column for the event.</span></span>  
  
    -   <span data-ttu-id="350ac-111">若要加入篩選，在 **[編輯篩選]** 對話方塊中按一下資料行名稱，然後指定篩選準則。</span><span class="sxs-lookup"><span data-stu-id="350ac-111">To add filters, click the data column name and specify the filter criteria in the **Edit Filter** dialog box.</span></span> <span data-ttu-id="350ac-112">您也可以用滑鼠右鍵按一下資料行名稱，然後按一下 [編輯資料行篩選]\*\*\*\* 以啟動 [編輯篩選]\*\*\*\* 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="350ac-112">You can also right-click the data column name, and click **Edit Column Filter** to launch the **Edit Filter** dialog box.</span></span> <span data-ttu-id="350ac-113">按一下 **[確定]** 以加入篩選。</span><span class="sxs-lookup"><span data-stu-id="350ac-113">Click **OK** to add the filter.</span></span>  
  
4.  <span data-ttu-id="350ac-114">按一下 [儲存]\*\*\*\*，或按一下 [另存新檔]\*\*\*\*，以另一個名稱儲存追蹤範本。</span><span class="sxs-lookup"><span data-stu-id="350ac-114">Click **Save**, or click **Save As**to save the trace template under another name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="350ac-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="350ac-115">See Also</span></span>  
 <span data-ttu-id="350ac-116">[指定追蹤檔案的事件和資料行 &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/specify-events-and-data-columns-for-a-trace-file-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="350ac-116">[Specify Events and Data Columns for a Trace File &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/specify-events-and-data-columns-for-a-trace-file-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="350ac-117">[從執行中的追蹤衍生範本 &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/derive-a-template-from-a-running-trace-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="350ac-117">[Derive a Template from a Running Trace &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/derive-a-template-from-a-running-trace-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="350ac-118">[從追蹤檔案或追蹤資料表衍生範本 &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/derive-a-template-from-a-trace-file-or-trace-table-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="350ac-118">[Derive a Template from a Trace File or Trace Table &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/derive-a-template-from-a-trace-file-or-trace-table-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="350ac-119">[SQL Server Profiler 範本和權限](../tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md) </span><span class="sxs-lookup"><span data-stu-id="350ac-119">[SQL Server Profiler Templates and Permissions](../tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md) </span></span>  
 [<span data-ttu-id="350ac-120">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="350ac-120">SQL Server Profiler</span></span>](../tools/sql-server-profiler/sql-server-profiler.md)  
  
  
