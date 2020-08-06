---
title: 使用 SQL Server Profiler 建立及測試計畫指南 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- checking plan guides
- plan guides [SQL Server], testing
- plan guides [SQL Server], SQL Server Profiler
- matching queries to plan guides [SQL Server]
- testing plan guides
- SQL Server Profiler, plan guides
- plan guides [SQL Server], creating
- capturing query text [SQL Server]
- verifying plan guides
- Profiler [SQL Server Profiler], plan guides
- query-to-plan guide matching [SQL Server]
ms.assetid: 7018dbf0-1a1a-411a-88af-327bedf9cfbd
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 543905343d74c9fbabe5f671d9021657ea5f76b5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87701077"
---
# <a name="use-sql-server-profiler-to-create-and-test-plan-guides"></a><span data-ttu-id="f66b6-102">使用 SQL Server Profiler 建立及測試計畫指南</span><span class="sxs-lookup"><span data-stu-id="f66b6-102">Use SQL Server Profiler to Create and Test Plan Guides</span></span>
  <span data-ttu-id="f66b6-103">當您建立計畫指南時，可使用 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 來擷取精確的查詢文字，以供使用於 **sp_create_plan_guide** 預存程序的 <陳述式文字> 引數。</span><span class="sxs-lookup"><span data-stu-id="f66b6-103">When you are creating a plan guide, you can use [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] to capture the exact query text for use in the *statement_text* argument of the **sp_create_plan_guide** stored procedure.</span></span> <span data-ttu-id="f66b6-104">這有助於確保計畫指南符合編譯時期的查詢。</span><span class="sxs-lookup"><span data-stu-id="f66b6-104">This helps make sure that the plan guide will be matched to the query at compile time.</span></span> <span data-ttu-id="f66b6-105">在建立計畫指南之後， [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 也可用來測試計畫指南實際上是否符合查詢。</span><span class="sxs-lookup"><span data-stu-id="f66b6-105">After the plan guide is created, [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] can also be used to test that the plan guide is, in fact, being matched to the query.</span></span> <span data-ttu-id="f66b6-106">一般而言，您應該使用 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 來測試計畫指南，以確認查詢符合您的計畫指南。</span><span class="sxs-lookup"><span data-stu-id="f66b6-106">Generally, you should test plan guides by using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] to verify that your query is being matched to your plan guide.</span></span>  
  
## <a name="capturing-query-text-by-using-sql-server-profiler"></a><span data-ttu-id="f66b6-107">使用 SQL Server Profiler 擷取查詢文字</span><span class="sxs-lookup"><span data-stu-id="f66b6-107">Capturing Query Text by Using SQL Server Profiler</span></span>  
 <span data-ttu-id="f66b6-108">如果您執行查詢並使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 來擷取與提交至 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]完全相同的文字，您可以建立 SQL 或 TEMPLATE 類型的計畫指南來完全符合查詢文字。</span><span class="sxs-lookup"><span data-stu-id="f66b6-108">If you run a query and capture the text exactly as it was submitted to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] by using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)], you can create a plan guide of type SQL or TEMPLATE that will match the query text exactly.</span></span> <span data-ttu-id="f66b6-109">這可確保計畫指南是由查詢最佳化工具使用。</span><span class="sxs-lookup"><span data-stu-id="f66b6-109">This makes sure that the plan guide is used by the query optimizer.</span></span>  
  
 <span data-ttu-id="f66b6-110">請看應用程式以獨立批次提交的下列查詢：</span><span class="sxs-lookup"><span data-stu-id="f66b6-110">Consider the following query that is submitted by an application as a stand-alone batch:</span></span>  
  
```  
SELECT COUNT(*) AS c  
FROM Sales.SalesOrderHeader AS h  
INNER JOIN Sales.SalesOrderDetail AS d  
  ON h.SalesOrderID = d.SalesOrderID  
WHERE h.OrderDate BETWEEN '20000101' and '20050101';  
```  
  
 <span data-ttu-id="f66b6-111">假設您要此查詢使用合併聯結作業執行，但 SHOWPLAN 指出該查詢不是使用合併聯結。</span><span class="sxs-lookup"><span data-stu-id="f66b6-111">Suppose you want this query to execute using a merge join operation, but SHOWPLAN indicates that the query is not using a merge join.</span></span> <span data-ttu-id="f66b6-112">您不能在應用程式中直接變更查詢，而是要建立計畫指南來指定在編譯時期將 MERGE JOIN 查詢提示附加至查詢。</span><span class="sxs-lookup"><span data-stu-id="f66b6-112">You cannot change the query directly in the application, so instead you create a plan guide to specify that the MERGE JOIN query hint be appended to the query at compile time.</span></span>  
  
 <span data-ttu-id="f66b6-113">若要擷取和 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 所接收的一模一樣的查詢文字，請遵循這些步驟：</span><span class="sxs-lookup"><span data-stu-id="f66b6-113">To capture the text of the query exactly as [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] receives it, follow these steps:</span></span>  
  
1.  <span data-ttu-id="f66b6-114">啟動 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 追蹤，確定已選取 [SQL:BatchStarting] 事件類型。</span><span class="sxs-lookup"><span data-stu-id="f66b6-114">Start a [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] trace, making sure that the **SQL:BatchStarting** event type is selected.</span></span>  
  
2.  <span data-ttu-id="f66b6-115">讓應用程式執行查詢。</span><span class="sxs-lookup"><span data-stu-id="f66b6-115">Have the application run the query.</span></span>  
  
3.  <span data-ttu-id="f66b6-116">暫停 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 追蹤。</span><span class="sxs-lookup"><span data-stu-id="f66b6-116">Pause the [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] Trace.</span></span>  
  
4.  <span data-ttu-id="f66b6-117">按一下對應到此查詢的 [SQL:BatchStarting] 事件。</span><span class="sxs-lookup"><span data-stu-id="f66b6-117">Click the **SQL:BatchStarting** event that corresponds to the query.</span></span>  
  
5.  <span data-ttu-id="f66b6-118">以滑鼠右鍵按一下，並選取 [擷取事件資料]。</span><span class="sxs-lookup"><span data-stu-id="f66b6-118">Right-click and select **Extract Event Data**.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="f66b6-119">請勿嘗試從 Profiler 追蹤視窗的下方窗格選取要複製的批次文字。</span><span class="sxs-lookup"><span data-stu-id="f66b6-119">Do not try to copy the batch text by selecting it from the lower pane of the Profiler trace window.</span></span> <span data-ttu-id="f66b6-120">這可能造成建立的計畫指南與原始批次不符。</span><span class="sxs-lookup"><span data-stu-id="f66b6-120">This might cause the plan guide that you create to not match the original batch.</span></span>  
  
6.  <span data-ttu-id="f66b6-121">將事件資料儲存至檔案。</span><span class="sxs-lookup"><span data-stu-id="f66b6-121">Save the event data to a file.</span></span> <span data-ttu-id="f66b6-122">這是批次文字。</span><span class="sxs-lookup"><span data-stu-id="f66b6-122">This is the batch text.</span></span>  
  
7.  <span data-ttu-id="f66b6-123">在 [記事本] 中開啟批次文字檔，將文字複製到「複製與貼上緩衝區」。</span><span class="sxs-lookup"><span data-stu-id="f66b6-123">Open the batch text file in Notepad and copy the text to the copy and paste buffer.</span></span>  
  
8.  <span data-ttu-id="f66b6-124">建立計畫指南，並將所複製的文字貼到 **@stmt**引數所指定的引號內 ( **@stmt** )。</span><span class="sxs-lookup"><span data-stu-id="f66b6-124">Create the plan guide and paste the copied text inside the quotation marks (**''**) specified for the **@stmt** argument.</span></span> <span data-ttu-id="f66b6-125">您必須在引數中的單引號前面加上另一個單引號，以將 **@stmt** 其轉義。</span><span class="sxs-lookup"><span data-stu-id="f66b6-125">You must escape any single quotation marks in the **@stmt** argument by preceding them with another single quotation mark.</span></span> <span data-ttu-id="f66b6-126">當您插入這些單引號的時候，請小心不要加入或移除任何其他字元。</span><span class="sxs-lookup"><span data-stu-id="f66b6-126">Be careful not to add or remove any other characters when you insert these single quotation marks.</span></span> <span data-ttu-id="f66b6-127">例如，您必須將 **'** 20000101 **'** 日期常值分隔為 **''** 20000101 **''** 。</span><span class="sxs-lookup"><span data-stu-id="f66b6-127">For example, the date literal **'** 20000101 **'** must be delimited as **''** 20000101 **''**.</span></span>  
  
 <span data-ttu-id="f66b6-128">以下是計畫指南：</span><span class="sxs-lookup"><span data-stu-id="f66b6-128">Here is the plan guide:</span></span>  
  
```  
EXEC sp_create_plan_guide   
    @name = N'MyGuide1',  
    @stmt = N'<paste the text copied from the batch text file here>',  
    @type = N'SQL',  
    @module_or_batch = NULL,  
    @params = NULL,  
    @hints = N'OPTION (MERGE JOIN)';  
```  
  
## <a name="testing-plan-guides-by-using-sql-server-profiler"></a><span data-ttu-id="f66b6-129">使用 SQL Server Profiler 測試計畫指南</span><span class="sxs-lookup"><span data-stu-id="f66b6-129">Testing Plan Guides by Using SQL Server Profiler</span></span>  
 <span data-ttu-id="f66b6-130">若要確認計畫指南符合查詢，請遵循這些步驟：</span><span class="sxs-lookup"><span data-stu-id="f66b6-130">To verify that a plan guide is being matched to a query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="f66b6-131">啟動 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 追蹤，確定已選取 [執行程序表 XML] 事件類型 (位於 [效能] 節點之下)。</span><span class="sxs-lookup"><span data-stu-id="f66b6-131">Start a [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] trace, making certain that the **Showplan XML** event type is selected (located under the **Performance** node).</span></span>  
  
2.  <span data-ttu-id="f66b6-132">讓應用程式執行查詢。</span><span class="sxs-lookup"><span data-stu-id="f66b6-132">Have the application run the query.</span></span>  
  
3.  <span data-ttu-id="f66b6-133">暫停 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 追蹤。</span><span class="sxs-lookup"><span data-stu-id="f66b6-133">Pause the [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] Trace.</span></span>  
  
4.  <span data-ttu-id="f66b6-134">為受影響的查詢尋找 [執行程序表 XML] 事件。</span><span class="sxs-lookup"><span data-stu-id="f66b6-134">Find the **Showplan XML** event for the affected query.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="f66b6-135">不可使用 [Showplan XML for Query Compile] 事件。</span><span class="sxs-lookup"><span data-stu-id="f66b6-135">The **Showplan XML for Query Compile** event cannot be used.</span></span> <span data-ttu-id="f66b6-136">[PlanGuideDB] 不存在該事件中。</span><span class="sxs-lookup"><span data-stu-id="f66b6-136">**PlanGuideDB** does not exist in that event.</span></span>  
  
5.  <span data-ttu-id="f66b6-137">如果計畫指南的類型為 OBJECT 或 SQL，請確認 [執行程序表 XML] 事件包含您預期符合查詢之計畫指南的 **PlanGuideDB** 和 **PlanGuideName** 屬性。</span><span class="sxs-lookup"><span data-stu-id="f66b6-137">If the plan guide is of type OBJECT or SQL, verify that the **Showplan XML** event contains the **PlanGuideDB** and **PlanGuideName** attributes for the plan guide that you expected to match the query.</span></span> <span data-ttu-id="f66b6-138">若為 TEMPLATE 計畫指南，則請確認 [執行程序表 XML] 事件包含預期計畫指南的 **TemplatePlanGuideDB** 和 **TemplatePlanGuideName** 屬性。</span><span class="sxs-lookup"><span data-stu-id="f66b6-138">Or, in the case of a TEMPLATE plan guide, verify that the **Showplan XML** event contains the **TemplatePlanGuideDB** and **TemplatePlanGuideName** attributes for the expected plan guide.</span></span> <span data-ttu-id="f66b6-139">這可確認計畫指南有用。</span><span class="sxs-lookup"><span data-stu-id="f66b6-139">This verifies that the plan guide is working.</span></span> <span data-ttu-id="f66b6-140">這些屬性包含在計畫的 **\<StmtSimple>** 元素下。</span><span class="sxs-lookup"><span data-stu-id="f66b6-140">These attributes are contained under the **\<StmtSimple>** element of the plan.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f66b6-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f66b6-141">See Also</span></span>  
 [<span data-ttu-id="f66b6-142">sp_create_plan_guide &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="f66b6-142">sp_create_plan_guide &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql)  
  
  
