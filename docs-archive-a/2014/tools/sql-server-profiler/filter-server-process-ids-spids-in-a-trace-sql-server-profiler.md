---
title: 篩選追蹤中的伺服器處理序識別碼 (SPID) (SQL Server Profiler) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- filters [SQL Server], traces
- filters [SQL Server], SPIDs
- traces [SQL Server], filters
ms.assetid: f5945c39-be6b-4632-91cb-92066c80e188
author: stevestein
ms.author: sstein
ms.openlocfilehash: 99ae7eac6f19bd942a04f97b0a7da580eadc9dbf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706922"
---
# <a name="filter-server-process-ids-spids-in-a-trace-sql-server-profiler"></a><span data-ttu-id="19be4-102">篩選追蹤中的伺服器處理序識別碼 (SPID) (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="19be4-102">Filter Server Process IDs (SPIDs) in a Trace (SQL Server Profiler)</span></span>
  <span data-ttu-id="19be4-103">此主題描述如何使用 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]，篩選追蹤中的伺服器處理序識別碼 (SPID)。</span><span class="sxs-lookup"><span data-stu-id="19be4-103">This topic describes how to filter server process identifiers (SPIDs) in a trace by using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span>  
  
### <a name="to-filter-system-ids-in-a-trace"></a><span data-ttu-id="19be4-104">若要篩選追蹤系統識別碼</span><span class="sxs-lookup"><span data-stu-id="19be4-104">To filter system IDs in a trace</span></span>  
  
1.  <span data-ttu-id="19be4-105">在 **[檔案]** 功能表上按一下 **[新增追蹤]** ，然後連接到 SQL Server 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="19be4-105">On the **File** menu, click **New Trace**, and then connect to an instance of SQL Server.</span></span>  
  
     <span data-ttu-id="19be4-106">會出現 [追蹤屬性] **[追蹤屬性]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="19be4-106">The **Trace Properties**dialog box appears.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="19be4-107">如果選取 [**進行連接後立即啟動追蹤**]，則不會顯示 [**追蹤屬性**] 對話方塊，而是開始追蹤。</span><span class="sxs-lookup"><span data-stu-id="19be4-107">if **Start tracing immediately after making connection**is selected, the **Trace Properties**dialog box fails to appear, and the trace begins instead.</span></span> <span data-ttu-id="19be4-108">於 [工具] 功能表，按一下 [選項]，並清除 [連接後立即啟動追蹤] 核取方塊，以關閉這項設定。</span><span class="sxs-lookup"><span data-stu-id="19be4-108">To turn off this setting, on the **Tools**menu, click **Options**, and clear the **Start tracing immediately after making connection** check box.</span></span>  
  
2.  <span data-ttu-id="19be4-109">在 **[追蹤名稱]** 方塊中，輸入追蹤的名稱。</span><span class="sxs-lookup"><span data-stu-id="19be4-109">In the **Trace name** box, type a name for the trace.</span></span>  
  
3.  <span data-ttu-id="19be4-110">在 [使用範本]\*\*\*\* 名稱清單中，選取追蹤範本。</span><span class="sxs-lookup"><span data-stu-id="19be4-110">In the **Use the template**name list, select a trace template.</span></span>  
  
4.  <span data-ttu-id="19be4-111">選擇性，指定要儲存追蹤結果的目的地檔案或資料表。</span><span class="sxs-lookup"><span data-stu-id="19be4-111">Optionally, specify a destination file or table in which to save the trace results.</span></span>  
  
5.  <span data-ttu-id="19be4-112">在 [事件選取範圍]\*\*\*\* 索引標籤上，按一下 [SPID]\*\*\*\* 資料行標題，以啟動 [編輯篩選]\*\*\*\* 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="19be4-112">On the **Events Selection**tab, click the **SPID**column heading to launch the **Edit Filter** dialog box.</span></span> <span data-ttu-id="19be4-113">您也可以用滑鼠右鍵按一下資料行標題，然後選擇 [編輯資料行篩選]。</span><span class="sxs-lookup"><span data-stu-id="19be4-113">You can also right-click the column heading and choose **Edit Column Filter**.</span></span> <span data-ttu-id="19be4-114">如果 [SPID] 資料行未出現，請核取 [顯示所有資料行] 方塊。</span><span class="sxs-lookup"><span data-stu-id="19be4-114">If the **SPID** column does not appear, check the **Show all columns** box.</span></span>  
  
6.  <span data-ttu-id="19be4-115">在 [編輯篩選] 對話方塊中，展開適當的比較運算子，然後輸入 SPID 作為比較的值。</span><span class="sxs-lookup"><span data-stu-id="19be4-115">In the **Edit Filter** dialog box, expand the appropriate comparison operator, and enter a SPID as a value for the comparison.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19be4-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="19be4-116">See Also</span></span>  
 [<span data-ttu-id="19be4-117">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="19be4-117">SQL Server Profiler</span></span>](sql-server-profiler.md)  
  
  
