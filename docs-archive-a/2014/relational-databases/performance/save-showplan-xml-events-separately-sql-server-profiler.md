---
title: 個別儲存 Showplan XML 事件 (SQL Server Profiler) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Showplan XML events
- saving Showplan XML events
- events [SQL Server], Showplan XML
ms.assetid: 33320a7a-36e8-401c-876d-5b82c49abd85
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 240fb408bb3ed8585ecc915ba4829ac21285d241
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606240"
---
# <a name="save-showplan-xml-events-separately-sql-server-profiler"></a><span data-ttu-id="3fa42-102">個別儲存 Showplan XML 事件 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="3fa42-102">Save Showplan XML Events Separately (SQL Server Profiler)</span></span>
  <span data-ttu-id="3fa42-103">此主題描述如何利用 **，將在追蹤中擷取的** Showplan XML [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]事件儲存到個別的 .SQLPlan 檔案中。</span><span class="sxs-lookup"><span data-stu-id="3fa42-103">This topic describes how to save **Showplan XML** events that are captured in traces into separate .SQLPlan files by using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span> <span data-ttu-id="3fa42-104">您可以在 **中開啟** Showplan XML [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]事件檔案，讓您檢視每個事件的圖形化執行計畫。</span><span class="sxs-lookup"><span data-stu-id="3fa42-104">You can open the **Showplan XML** event files in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], which enables you to view the graphical execution plan for each event.</span></span>  
  
### <a name="to-save-showplan-xml-events-separately"></a><span data-ttu-id="3fa42-105">若要個別儲存 Showplan XML 事件</span><span class="sxs-lookup"><span data-stu-id="3fa42-105">To save Showplan XML events separately</span></span>  
  
1.  <span data-ttu-id="3fa42-106">在 **[檔案]** 功能表上按一下 **[新增追蹤]** ，然後連接到 SQL Server 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="3fa42-106">On the **File** menu, click **New Trace**, and then connect to an instance of SQL Server.</span></span>  
  
     <span data-ttu-id="3fa42-107">會出現 [追蹤屬性] **[追蹤屬性]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="3fa42-107">The **Trace Properties**dialog box appears.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="3fa42-108">如果選取 [進行連接後立即啟動追蹤]，將不會顯示 [追蹤屬性] 對話方塊，而是開始追蹤。</span><span class="sxs-lookup"><span data-stu-id="3fa42-108">If **Start tracing immediately after making connection**is selected, the **Trace Properties**dialog box fails to appear and the trace begins instead.</span></span> <span data-ttu-id="3fa42-109">於 [工具] 功能表，按一下 [選項]，並清除 [連接後立即啟動追蹤] 核取方塊，以關閉這項設定。</span><span class="sxs-lookup"><span data-stu-id="3fa42-109">To turn off this setting, on the **Tools**menu, click **Options**, and clear the **Start tracing immediately after making connection** check box.</span></span>  
  
2.  <span data-ttu-id="3fa42-110">在 **[追蹤屬性]** 對話方塊的 **[追蹤名稱]** 方塊中，輸入追蹤的名稱。</span><span class="sxs-lookup"><span data-stu-id="3fa42-110">In the **Trace Properties** dialog box, type a name for the trace in the **Trace name** box.</span></span>  
  
3.  <span data-ttu-id="3fa42-111">在 **[使用範本]** 清單中，選取追蹤使用為基礎的追蹤範本；若不想要使用範本，請選取 **[空白]** 。</span><span class="sxs-lookup"><span data-stu-id="3fa42-111">In the **Use the template** list, select a trace template on which to base the trace, or select **Blank** if you do not want to use a template.</span></span>  
  
4.  <span data-ttu-id="3fa42-112">請執行下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="3fa42-112">Do one of the following:</span></span>  
  
    -   <span data-ttu-id="3fa42-113">選取 [儲存至檔案]\*\*\*\* 核取方塊，將追蹤擷取至檔案。</span><span class="sxs-lookup"><span data-stu-id="3fa42-113">Select the**Save to file** check box to capture the trace to a file.</span></span> <span data-ttu-id="3fa42-114">在 **[設定最大檔案大小]** 中指定一個值。</span><span class="sxs-lookup"><span data-stu-id="3fa42-114">Specify a value for **Set maximum file size**.</span></span> <span data-ttu-id="3fa42-115">(選擇性) 選取 **[啟用檔案換用]** 與 **[伺服器處理追蹤資料]** 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="3fa42-115">Optionally, select the **Enable file rollover** and **Server processes trace data** check boxes.</span></span>  
  
    -   <span data-ttu-id="3fa42-116">選取 [儲存至資料表]\*\*\*\* 核取方塊，將追蹤擷取至資料庫資料表。</span><span class="sxs-lookup"><span data-stu-id="3fa42-116">Select the**Save to table** check box to capture the trace to a database table.</span></span> <span data-ttu-id="3fa42-117">選擇性地按一下 [**設定最大資料列數**]，然後指定一個值。</span><span class="sxs-lookup"><span data-stu-id="3fa42-117">Optionally click **Set maximum rows**, and specify a value.</span></span>  
  
5.  <span data-ttu-id="3fa42-118">(選擇性) 選取 **[啟用追蹤停止時間]** 核取方塊，然後指定停止日期和時間。</span><span class="sxs-lookup"><span data-stu-id="3fa42-118">Optionally, select the **Enable trace stop time** check box, and specify a stop date and time.</span></span>  
  
6.  <span data-ttu-id="3fa42-119">按一下 [事件選取範圍]\*\*\*\* 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="3fa42-119">Click the **Events Selection**tab.</span></span>  
  
7.  <span data-ttu-id="3fa42-120">在 [事件]\*\*\*\* 資料行中，展開 [效能]\*\*\*\* 事件類別目錄，然後選取 [Showplan XML (執行程序表 XML)]\*\*\*\* 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="3fa42-120">In the **Events**data column, expand the **Performance**event category, and then select the **Showplan XML**check box.</span></span> <span data-ttu-id="3fa42-121">如果沒有看到 **[Performance]** 事件類別目錄，請選取 **[顯示所有事件]** 來顯示它。</span><span class="sxs-lookup"><span data-stu-id="3fa42-121">If the **Performance** event category is not available, check **Show all events** to display it.</span></span>  
  
     <span data-ttu-id="3fa42-122">[事件擷取設定]\*\*\*\* 索引標籤會加入 [追蹤屬性]\*\*\*\* 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="3fa42-122">The **Events Extraction Settings**tab is added to the **Trace Properties**dialog box.</span></span>  
  
8.  <span data-ttu-id="3fa42-123">在 [事件擷取設定]\*\*\*\* 索引標籤上，按一下 [個別儲存 XML 執行程序表事件]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="3fa42-123">On the **Events Extraction Settings**tab, click **Save XML Showplan events separately**.</span></span>  
  
9. <span data-ttu-id="3fa42-124">在 **[另存新檔]** 對話方塊中，輸入儲存 **Showplan XML** 事件的檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="3fa42-124">In the **Save As** dialog box, enter the name of the file in which to store the **Showplan XML** events.</span></span>  
  
10. <span data-ttu-id="3fa42-125">按一下 [所有 XML 執行程序表批次都在單一檔案中]\*\*\*\*，以便將所有**執行程序表 XML** 事件儲存到單一 XML 檔案中，或者按一下 [每一個 XML 執行程序表批次都在相異檔案中]\*\*\*\*，針對每個**執行程序表 XML** 事件建立新的 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="3fa42-125">Click **All XML Showplan batches in a single file** to save all **Showplan XML** events in a single XML file, or click **Each XML Showplan batch in a distinct file**to create a new XML file for each **Showplan XML** event.</span></span>  
  
11. <span data-ttu-id="3fa42-126">若要在 SQL Server Management Studio 中檢視 **Showplan XML** 事件，請在 **[檔案]** 功能表上指向 **[開啟]**，然後按一下 **[檔案]**。</span><span class="sxs-lookup"><span data-stu-id="3fa42-126">To view the **Showplan XML** event file in SQL Server Management Studio, on the **File** menu, point to **Open**, and click **File**.</span></span> <span data-ttu-id="3fa42-127">導覽至您儲存 **Showplan XML** 事件檔案的目錄，以便選取一個檔案並加以開啟。</span><span class="sxs-lookup"><span data-stu-id="3fa42-127">Navigate to the directory where you saved the **Showplan XML** event file or files to select one and open it.</span></span> <span data-ttu-id="3fa42-128">**Showplan XML** 事件檔案的副檔名為 .SQLPlan。</span><span class="sxs-lookup"><span data-stu-id="3fa42-128">**Showplan XML** event files have a .SQLPlan file extension.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3fa42-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3fa42-129">See Also</span></span>  
 [<span data-ttu-id="3fa42-130">在 SQL Server Profiler 中使用 SHOWPLAN 結果分析查詢</span><span class="sxs-lookup"><span data-stu-id="3fa42-130">Analyze Queries with SHOWPLAN Results in SQL Server Profiler</span></span>](../../tools/sql-server-profiler/analyze-queries-with-showplan-results-in-sql-server-profiler.md)  
  
  
