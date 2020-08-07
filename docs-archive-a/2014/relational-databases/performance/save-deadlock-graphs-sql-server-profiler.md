---
title: 儲存死結圖形 (SQL Server Profiler) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- deadlocks [SQL Server], saving deadlock graphs
- graphs [SQL Server]
- saving deadlock graphs
ms.assetid: bf1fc906-abd6-4a89-842e-da0d66b2defe
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: cdd0bd808ba4b934e5b2d91c9079909acf6e3997
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597776"
---
# <a name="save-deadlock-graphs-sql-server-profiler"></a><span data-ttu-id="21d74-102">儲存死結圖形 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="21d74-102">Save Deadlock Graphs (SQL Server Profiler)</span></span>
  <span data-ttu-id="21d74-103">此主題描述如何使用 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]儲存死結圖表。</span><span class="sxs-lookup"><span data-stu-id="21d74-103">This topic describes how to save a deadlock graph by using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span> <span data-ttu-id="21d74-104">死結圖表會儲存為 XML 檔。</span><span class="sxs-lookup"><span data-stu-id="21d74-104">Deadlock graphs are saved as XML files.</span></span>  
  
### <a name="to-save-deadlock-graph-events-separately"></a><span data-ttu-id="21d74-105">若要個別儲存死結圖表事件</span><span class="sxs-lookup"><span data-stu-id="21d74-105">To save deadlock graph events separately</span></span>  
  
1.  <span data-ttu-id="21d74-106">在 **[檔案]** 功能表上按一下 **[新增追蹤]** ，然後連接到 SQL Server 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="21d74-106">On the **File** menu, click **New Trace**, and then connect to an instance of SQL Server.</span></span>  
  
     <span data-ttu-id="21d74-107">會出現 [追蹤屬性] **[追蹤屬性]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="21d74-107">The **Trace Properties**dialog box appears.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="21d74-108">如果選取 [進行連接後立即啟動追蹤]\*\*\*\*，將不會顯示 [追蹤屬性]\*\*\*\* 對話方塊，而是開始追蹤。</span><span class="sxs-lookup"><span data-stu-id="21d74-108">If **Start tracing immediately after making connection** is selected, the **Trace Properties**dialog box fails to appear, and the trace begins instead.</span></span> <span data-ttu-id="21d74-109">於 [工具] 功能表，按一下 [選項]，並清除 [連接後立即啟動追蹤] 核取方塊，以關閉這項設定。</span><span class="sxs-lookup"><span data-stu-id="21d74-109">To turn off this setting, on the **Tools**menu, click **Options**, and clear the **Start tracing immediately after making connection** check box.</span></span>  
  
2.  <span data-ttu-id="21d74-110">在 [追蹤屬性] 對話方塊的 [追蹤名稱]\*\*\*\* 方塊中，輸入追蹤的名稱。</span><span class="sxs-lookup"><span data-stu-id="21d74-110">In the Trace Properties dialog box, type a name for the trace in the**Trace name** box.</span></span>  
  
3.  <span data-ttu-id="21d74-111">在 **[使用範本]** 清單中，選取追蹤使用為基礎的追蹤範本；若不想要使用範本，請選取 **[空白]** 。</span><span class="sxs-lookup"><span data-stu-id="21d74-111">In the **Use the template** list, select a trace template on which to base the trace, or select **Blank** if you do not want to use a template.</span></span>  
  
4.  <span data-ttu-id="21d74-112">請執行下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="21d74-112">Do one of the following:</span></span>  
  
    -   <span data-ttu-id="21d74-113">選取 [儲存至檔案]\*\*\*\* 核取方塊，將追蹤擷取至檔案。</span><span class="sxs-lookup"><span data-stu-id="21d74-113">Select the**Save to file** check box to capture the trace to a file.</span></span> <span data-ttu-id="21d74-114">在 **[設定最大檔案大小]** 中指定一個值。</span><span class="sxs-lookup"><span data-stu-id="21d74-114">Specify a value for **Set maximum file size**.</span></span>  
  
         <span data-ttu-id="21d74-115">(選擇性) 選取 [啟用檔案換用]\*\*\*\* 及 [伺服器處理追蹤資料]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="21d74-115">Optionally, select **Enable file rollover** and **Server processes trace data**.</span></span>  
  
    -   <span data-ttu-id="21d74-116">選取 [儲存至資料表]\*\*\*\* 核取方塊，將追蹤擷取至資料庫資料表。</span><span class="sxs-lookup"><span data-stu-id="21d74-116">Select the **Save to table** check box to capture the trace to a database table.</span></span>  
  
         <span data-ttu-id="21d74-117">(選擇性) 按一下 **[設定最大資料列數]**，然後指定一個值。</span><span class="sxs-lookup"><span data-stu-id="21d74-117">Optionally, click **Set maximum rows**, and specify a value.</span></span>  
  
5.  <span data-ttu-id="21d74-118">(選擇性) 選取 **[啟用追蹤停止時間]** 核取方塊，然後指定停止日期和時間。</span><span class="sxs-lookup"><span data-stu-id="21d74-118">Optionally, select the **Enable trace stop time** check box, and specify a stop date and time.</span></span>  
  
6.  <span data-ttu-id="21d74-119">按一下 [事件選取範圍]\*\*\*\* 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="21d74-119">Click the **Events Selection**tab.</span></span>  
  
7.  <span data-ttu-id="21d74-120">在 [事件]\*\*\*\* 資料行中，展開 [Locks]\*\*\*\* 事件類別目錄，然後選取 [Deadlock Graph]\*\*\*\* 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="21d74-120">In the **Events**data column, expand the **Locks**event category, and then select the **Deadlock graph**check box.</span></span> <span data-ttu-id="21d74-121">如果看不到 Locks 事件類別目錄，請核取 [顯示所有事件]\*\*\*\* 來顯示它。</span><span class="sxs-lookup"><span data-stu-id="21d74-121">If the Locks event category is not available, check **Show all events** to display it.</span></span>  
  
     <span data-ttu-id="21d74-122">[事件擷取設定]\*\*\*\* 索引標籤會加入 [追蹤屬性]\*\*\*\* 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="21d74-122">The **Events Extraction Settings**tab is added to the **Trace Properties**dialog box.</span></span>  
  
8.  <span data-ttu-id="21d74-123">在 [事件擷取設定]\*\*\*\* 索引標籤上，按一下 [個別儲存死結 XML 事件]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="21d74-123">On the **Events Extraction Settings**tab, click **Save Deadlock XML Events Separately**.</span></span>  
  
9. <span data-ttu-id="21d74-124">在 [另存新檔]\*\*\*\* 對話方塊中，輸入要儲存 Deadlock Graph 事件的檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="21d74-124">In the **Save As** dialog box, enter the name of the file in which to store the deadlock graph events.</span></span>  
  
10. <span data-ttu-id="21d74-125">按一下 [所有死結 XML 批次都在單一檔案中]\*\*\*\*，將所有 Deadlock Graph 事件儲存在單一 XML 檔案中，或按一下 [每一個死結 XML 批次都在相異檔案中]\*\*\*\*，為每一個 Deadlock Graph 建立新的 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="21d74-125">Click **All Deadlock XML batches in a single file** to save all deadlock graph events in a single XML file, or click **Each Deadlock XML batch in a distinct file**to create a new XML file for each deadlock graph.</span></span>  
  
 <span data-ttu-id="21d74-126">在儲存了死結檔案之後，您可以在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中開啟檔案。</span><span class="sxs-lookup"><span data-stu-id="21d74-126">After you have saved the deadlock file, you can open the file in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="21d74-127">如需詳細資訊，請參閱[開啟、查看和列印鎖死檔案 &#40;SQL Server Management Studio&#41;](open-view-and-print-a-deadlock-file-sql-server-management-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="21d74-127">For more information, see [Open, View, and Print a Deadlock File &#40;SQL Server Management Studio&#41;](open-view-and-print-a-deadlock-file-sql-server-management-studio.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21d74-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="21d74-128">See Also</span></span>  
 [<span data-ttu-id="21d74-129">使用 SQL Server Profiler 分析死結</span><span class="sxs-lookup"><span data-stu-id="21d74-129">Analyze Deadlocks with SQL Server Profiler</span></span>](../../tools/sql-server-profiler/analyze-deadlocks-with-sql-server-profiler.md)  
  
  
