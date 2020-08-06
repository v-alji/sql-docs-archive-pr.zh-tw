---
title: 執行多個資料表的累加式載入 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- incremental load [Integration Services],multiple tables
ms.assetid: 39252dd5-09c3-46f9-a17b-15208cfd336d
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e4bf81d1d529e8102271c66839440ef712219600
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592817"
---
# <a name="perform-an-incremental-load-of-multiple-tables"></a><span data-ttu-id="f0bc9-102">執行多個資料表的累加式載入</span><span class="sxs-lookup"><span data-stu-id="f0bc9-102">Perform an Incremental Load of Multiple Tables</span></span>
  <span data-ttu-id="f0bc9-103">在 [利用異動資料擷取改善累加式載入](change-data-capture-ssis.md)主題中，圖表會說明只在一個資料表上執行累加式載入的基本封裝。</span><span class="sxs-lookup"><span data-stu-id="f0bc9-103">In the topic, [Improving Incremental Loads with Change Data Capture](change-data-capture-ssis.md), the diagram illustrates a basic package that performs an incremental load on just one table.</span></span> <span data-ttu-id="f0bc9-104">不過，載入一個資料表不如必須執行多個資料表的累加式載入那麼常見。</span><span class="sxs-lookup"><span data-stu-id="f0bc9-104">However, loading one table is not as common as having to perform an incremental load of multiple tables.</span></span>  
  
 <span data-ttu-id="f0bc9-105">執行多個資料表的累加式載入時，會針對所有資料表執行一次某些步驟，而且必須針對每個來源資料表重複其他步驟。</span><span class="sxs-lookup"><span data-stu-id="f0bc9-105">When you perform an incremental load of multiple tables, some steps have to be performed once for all the tables, and other steps have to be repeated for each source table.</span></span> <span data-ttu-id="f0bc9-106">您在 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]中實作這些步驟時有一個以上的選擇。</span><span class="sxs-lookup"><span data-stu-id="f0bc9-106">You have more than one option for implementing these steps in [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]:</span></span>  
  
-   <span data-ttu-id="f0bc9-107">使用父封裝和子封裝。</span><span class="sxs-lookup"><span data-stu-id="f0bc9-107">Use a parent package and child packages.</span></span>  
  
-   <span data-ttu-id="f0bc9-108">在單一封裝中使用多個資料流程工作。</span><span class="sxs-lookup"><span data-stu-id="f0bc9-108">Use multiple Data Flow tasks in a single package.</span></span>  
  
## <a name="loading-multiple-tables-by-using-a-parent-package-and-multiple-child-packages"></a><span data-ttu-id="f0bc9-109">使用父封裝和多個子封裝載入多個資料表</span><span class="sxs-lookup"><span data-stu-id="f0bc9-109">Loading Multiple Tables by Using a Parent Package and Multiple Child Packages</span></span>  
 <span data-ttu-id="f0bc9-110">您可以使用父封裝來執行僅需要執行一次的步驟。</span><span class="sxs-lookup"><span data-stu-id="f0bc9-110">You can use a parent package to perform those steps that only have to be done once.</span></span> <span data-ttu-id="f0bc9-111">子封裝將會執行必須針對每個來源資料表執行的步驟。</span><span class="sxs-lookup"><span data-stu-id="f0bc9-111">The child packages will perform those steps that have to be done for each source table.</span></span>  
  
#### <a name="to-create-a-parent-package-that-performs-those-steps-that-only-have-to-be-done-once"></a><span data-ttu-id="f0bc9-112">建立父封裝，執行僅需要執行一次的步驟</span><span class="sxs-lookup"><span data-stu-id="f0bc9-112">To create a parent package that performs those steps that only have to be done once</span></span>  
  
1.  <span data-ttu-id="f0bc9-113">建立父封裝。</span><span class="sxs-lookup"><span data-stu-id="f0bc9-113">Create a parent package.</span></span>  
  
2.  <span data-ttu-id="f0bc9-114">在控制流程中，使用「執行 SQL」工作或 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 運算式來計算端點。</span><span class="sxs-lookup"><span data-stu-id="f0bc9-114">In the control flow, use an Execute SQL task or [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] expressions to calculate the endpoints.</span></span>  
  
     <span data-ttu-id="f0bc9-115">如需如何計算端點的範例，請參閱 [指定變更資料的間隔](specify-an-interval-of-change-data.md)。</span><span class="sxs-lookup"><span data-stu-id="f0bc9-115">For an example of how to calculate endpoints, see [Specify an Interval of Change Data](specify-an-interval-of-change-data.md).</span></span>  
  
3.  <span data-ttu-id="f0bc9-116">如果需要，使用「For 迴圈」容器延遲執行，直到所選期間的變更資料就緒為止。</span><span class="sxs-lookup"><span data-stu-id="f0bc9-116">If needed, use a For Loop container to delay execution until change data for the selected period is ready.</span></span>  
  
     <span data-ttu-id="f0bc9-117">如需此類「For 迴圈」容器的範例，請參閱 [判斷變更資料是否就緒](determine-whether-the-change-data-is-ready.md)。</span><span class="sxs-lookup"><span data-stu-id="f0bc9-117">For an example of such a For Loop container, see [Determine Whether the Change Data Is Ready](determine-whether-the-change-data-is-ready.md).</span></span>  
  
4.  <span data-ttu-id="f0bc9-118">使用多個「執行封裝」工作，針對每個要載入的資料表執行子封裝。</span><span class="sxs-lookup"><span data-stu-id="f0bc9-118">Use multiple Execute Package tasks to execute child packages for each table to be loaded.</span></span> <span data-ttu-id="f0bc9-119">使用「父封裝變數」組態，將父封裝中計算的端點傳遞到每個子封裝。</span><span class="sxs-lookup"><span data-stu-id="f0bc9-119">Pass the endpoints calculated in the parent package to each child package by using Parent Package Variable configurations.</span></span>  
  
     <span data-ttu-id="f0bc9-120">如需詳細資訊，請參閱 [執行封裝工作](../control-flow/execute-package-task.md) 和 [在子封裝中使用變數和參數的值](../use-the-values-of-variables-and-parameters-in-a-child-package.md)。</span><span class="sxs-lookup"><span data-stu-id="f0bc9-120">For more information, see [Execute Package Task](../control-flow/execute-package-task.md) and [Use the Values of Variables and Parameters in a Child Package](../use-the-values-of-variables-and-parameters-in-a-child-package.md).</span></span>  
  
#### <a name="to-create-child-packages-to-perform-those-steps-that-have-to-be-done-for-each-source-table"></a><span data-ttu-id="f0bc9-121">建立子封裝來執行必須針對每個來源資料表執行的步驟</span><span class="sxs-lookup"><span data-stu-id="f0bc9-121">To create child packages to perform those steps that have to be done for each source table</span></span>  
  
1.  <span data-ttu-id="f0bc9-122">針對每個來源資料表建立子封裝。</span><span class="sxs-lookup"><span data-stu-id="f0bc9-122">For each source table, create a child package.</span></span>  
  
2.  <span data-ttu-id="f0bc9-123">在控制流程中，使用「指令碼」工作或「執行 SQL」工作來組合將用於查詢變更的 SQL 陳述式。</span><span class="sxs-lookup"><span data-stu-id="f0bc9-123">In the control flow, use a Script task or an Execute SQL task to assemble the SQL statement that will be used to query for changes.</span></span>  
  
     <span data-ttu-id="f0bc9-124">如需如何組合查詢的範例，請參閱 [準備查詢變更資料](prepare-to-query-for-the-change-data.md)。</span><span class="sxs-lookup"><span data-stu-id="f0bc9-124">For an example of how to assemble the query, see [Prepare to Query for the Change Data](prepare-to-query-for-the-change-data.md).</span></span>  
  
3.  <span data-ttu-id="f0bc9-125">使用每個子封裝中的單一「資料流程」工作來載入變更資料，並將其套用到目的地。</span><span class="sxs-lookup"><span data-stu-id="f0bc9-125">Use a single Data Flow task in each child package to load the change data and apply it to the destination.</span></span> <span data-ttu-id="f0bc9-126">設定「資料流程」，如下列步驟所述：</span><span class="sxs-lookup"><span data-stu-id="f0bc9-126">Configure the Data Flow as described in the following steps:</span></span>  
  
    1.  <span data-ttu-id="f0bc9-127">在資料流程中，使用來源元件來查詢所選端點內之變更的變更資料表。</span><span class="sxs-lookup"><span data-stu-id="f0bc9-127">In the data flow, use a source component to query the change tables for the changes that fall within the selected endpoints.</span></span>  
  
         <span data-ttu-id="f0bc9-128">如需如何查詢變更資料表的範例，請參閱 [擷取與了解變更資料](retrieve-and-understand-the-change-data.md)。</span><span class="sxs-lookup"><span data-stu-id="f0bc9-128">For an example of how to query the change tables, see [Retrieve and Understand the Change Data](retrieve-and-understand-the-change-data.md).</span></span>  
  
    2.  <span data-ttu-id="f0bc9-129">使用「條件式分割」轉換，將插入、更新與刪除導引到不同的輸出以便進行適當的處理。</span><span class="sxs-lookup"><span data-stu-id="f0bc9-129">Use a Conditional Split transformation to direct inserts, updates, and deletes to different outputs for appropriate processing.</span></span>  
  
         <span data-ttu-id="f0bc9-130">如需如何設定此轉換來導向輸出的範例，請參閱 [處理插入、更新與刪除](process-inserts-updates-and-deletes.md)。</span><span class="sxs-lookup"><span data-stu-id="f0bc9-130">For an example of how to configure this transformation to direct output, see [Process Inserts, Updates, and Deletes](process-inserts-updates-and-deletes.md).</span></span>  
  
    3.  <span data-ttu-id="f0bc9-131">使用目的地元件，將插入套用到目的地。</span><span class="sxs-lookup"><span data-stu-id="f0bc9-131">Use a destination component to apply the inserts to the destination.</span></span> <span data-ttu-id="f0bc9-132">搭配參數化的 UPDATE 和 DELETE 陳述式使用「OLE DB 命令」轉換，將更新與刪除套用到目的地。</span><span class="sxs-lookup"><span data-stu-id="f0bc9-132">Use OLE DB Command transformations with parameterized UPDATE and DELETE statements to apply updates and deletes to the destination.</span></span>  
  
         <span data-ttu-id="f0bc9-133">如需如何使用此轉換來套用更新與刪除的範例，請參閱 [將變更套用到目的地](apply-the-changes-to-the-destination.md)。</span><span class="sxs-lookup"><span data-stu-id="f0bc9-133">For an example of how to use this transformation to apply updates and deletes, see [Apply the Changes to the Destination](apply-the-changes-to-the-destination.md).</span></span>  
  
## <a name="loading-multiple-tables-by-using-multiple-data-flow-tasks-in-a-single-package"></a><span data-ttu-id="f0bc9-134">在單一封裝中使用多個資料流程工作來載入多個資料表</span><span class="sxs-lookup"><span data-stu-id="f0bc9-134">Loading Multiple Tables by Using Multiple Data Flow Tasks in a Single Package</span></span>  
 <span data-ttu-id="f0bc9-135">或者，您可以使用包含要載入的每個來源資料表之個別「資料流程」工作的單一封裝。</span><span class="sxs-lookup"><span data-stu-id="f0bc9-135">Alternatively, you can use a single package that contains a separate Data Flow task for each source table to be loaded.</span></span>  
  
#### <a name="to-load-multiple-tables-by-using-multiple-data-flow-tasks-in-a-single-package"></a><span data-ttu-id="f0bc9-136">在單一封裝中使用多個資料流程工作載入多個資料表</span><span class="sxs-lookup"><span data-stu-id="f0bc9-136">To load multiple tables by using multiple Data Flow tasks in a single package</span></span>  
  
1.  <span data-ttu-id="f0bc9-137">建立單一封裝。</span><span class="sxs-lookup"><span data-stu-id="f0bc9-137">Create a single package.</span></span>  
  
2.  <span data-ttu-id="f0bc9-138">在控制流程中，使用「執行 SQL」工作或 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 運算式來計算端點。</span><span class="sxs-lookup"><span data-stu-id="f0bc9-138">In the control flow, use an Execute SQL Task or [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] expressions to calculate the endpoints.</span></span>  
  
     <span data-ttu-id="f0bc9-139">如需如何計算端點的範例，請參閱 [指定變更資料的間隔](specify-an-interval-of-change-data.md)。</span><span class="sxs-lookup"><span data-stu-id="f0bc9-139">For an example of how to calculate endpoints, see [Specify an Interval of Change Data](specify-an-interval-of-change-data.md).</span></span>  
  
3.  <span data-ttu-id="f0bc9-140">如果需要，使用「For 迴圈」容器延遲執行，直到所選間隔的變更資料就緒為止。</span><span class="sxs-lookup"><span data-stu-id="f0bc9-140">If needed, use a For Loop container to delay execution until the change data for the selected interval is ready.</span></span>  
  
     <span data-ttu-id="f0bc9-141">如需此類「For 迴圈」容器的範例，請參閱 [判斷變更資料是否就緒](determine-whether-the-change-data-is-ready.md)。</span><span class="sxs-lookup"><span data-stu-id="f0bc9-141">For an example of such a For Loop container, see [Determine Whether the Change Data Is Ready](determine-whether-the-change-data-is-ready.md).</span></span>  
  
4.  <span data-ttu-id="f0bc9-142">使用「指令碼」工作或「執行 SQL」工作來組合將用於查詢變更的 SQL 陳述式。</span><span class="sxs-lookup"><span data-stu-id="f0bc9-142">Use a Script task or an Execute SQL task to assemble the SQL statement that will be used to query for changes.</span></span>  
  
     <span data-ttu-id="f0bc9-143">如需如何組合查詢的範例，請參閱 [準備查詢變更資料](prepare-to-query-for-the-change-data.md)。</span><span class="sxs-lookup"><span data-stu-id="f0bc9-143">For an example of how to assemble the query, see [Prepare to Query for the Change Data](prepare-to-query-for-the-change-data.md).</span></span>  
  
5.  <span data-ttu-id="f0bc9-144">使用多個「資料流程」工作，從每個來源資料表載入變更資料，並將其套用到目的地。</span><span class="sxs-lookup"><span data-stu-id="f0bc9-144">Use multiple Data Flow tasks to load the change data from each source table and apply it to the destination.</span></span> <span data-ttu-id="f0bc9-145">設定每個「資料流程」工作，如下列步驟所述。</span><span class="sxs-lookup"><span data-stu-id="f0bc9-145">Configure each Data Flow task as described in the following steps.</span></span>  
  
    1.  <span data-ttu-id="f0bc9-146">在每個資料流程中，使用來源元件來查詢所選端點內之變更的變更資料表。</span><span class="sxs-lookup"><span data-stu-id="f0bc9-146">In each data flow, use a source component to query the change tables for the changes that fall within the selected endpoints.</span></span>  
  
         <span data-ttu-id="f0bc9-147">如需如何查詢變更資料表的範例，請參閱 [擷取與了解變更資料](retrieve-and-understand-the-change-data.md)。</span><span class="sxs-lookup"><span data-stu-id="f0bc9-147">For an example of how to query the change tables, see [Retrieve and Understand the Change Data](retrieve-and-understand-the-change-data.md).</span></span>  
  
    2.  <span data-ttu-id="f0bc9-148">使用「條件式分割」轉換，將插入、更新與刪除導引到不同的輸出以便進行適當的處理。</span><span class="sxs-lookup"><span data-stu-id="f0bc9-148">Use a Conditional Split transformation to direct inserts, updates, and deletes to different outputs for appropriate processing.</span></span>  
  
         <span data-ttu-id="f0bc9-149">如需如何設定此轉換來導向輸出的範例，請參閱 [處理插入、更新與刪除](process-inserts-updates-and-deletes.md)。</span><span class="sxs-lookup"><span data-stu-id="f0bc9-149">For an example of how to configure this transformation to direct output, see [Process Inserts, Updates, and Deletes](process-inserts-updates-and-deletes.md).</span></span>  
  
    3.  <span data-ttu-id="f0bc9-150">使用目的地元件，將插入套用到目的地。</span><span class="sxs-lookup"><span data-stu-id="f0bc9-150">Use a destination component to apply the inserts to the destination.</span></span> <span data-ttu-id="f0bc9-151">搭配參數化的 UPDATE 和 DELETE 陳述式使用「OLE DB 命令」轉換，將更新與刪除套用到目的地。</span><span class="sxs-lookup"><span data-stu-id="f0bc9-151">Use OLE DB Command transformations with parameterized UPDATE and DELETE statements to apply updates and deletes to the destination.</span></span>  
  
         <span data-ttu-id="f0bc9-152">如需如何使用此轉換來套用更新與刪除的範例，請參閱 [將變更套用到目的地](apply-the-changes-to-the-destination.md)。</span><span class="sxs-lookup"><span data-stu-id="f0bc9-152">For an example of how to use this transformation to apply updates and deletes, see [Apply the Changes to the Destination](apply-the-changes-to-the-destination.md).</span></span>  
  
  
