---
title: 清除 Analysis Services 快取 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 6bf66fdd-6a03-4cea-b7e2-eb676ff276ff
author: minewiskan
ms.author: owend
ms.openlocfilehash: e4890dd322406dcf48bc6b8eca89f292cfe132a3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688365"
---
# <a name="clear-the-analysis-services-caches"></a><span data-ttu-id="30e7b-102">清除 Analysis Services 快取</span><span class="sxs-lookup"><span data-stu-id="30e7b-102">Clear the Analysis Services Caches</span></span>
  <span data-ttu-id="30e7b-103">Analysis Services 會快取資料以提高查詢效能。</span><span class="sxs-lookup"><span data-stu-id="30e7b-103">Analysis Services caches data to boost query performance.</span></span> <span data-ttu-id="30e7b-104">此主題提供有關如何使用 XMLA ClearCache 命令，清除回應 MDX 查詢時所建立之快取的建議。</span><span class="sxs-lookup"><span data-stu-id="30e7b-104">This topic provides recommendations for using the XMLA ClearCache command to clear caches that were created in response to an MDX query.</span></span> <span data-ttu-id="30e7b-105">根據您使用的是表格式或多維度模型，執行 ClearCache 的影響有所不同。</span><span class="sxs-lookup"><span data-stu-id="30e7b-105">The effects of running ClearCache vary depending on whether you are using a tabular or multidimensional model.</span></span>  
  
 <span data-ttu-id="30e7b-106">**何時清除多維度模型的快取**</span><span class="sxs-lookup"><span data-stu-id="30e7b-106">**When to clear the cache for multidimensional models**</span></span>  
  
 <span data-ttu-id="30e7b-107">對於多維度資料庫，Analysis Services 會在評估計算時，於公式引擎和儲存引擎中建立維度查詢和量值群組查詢結果的快取。</span><span class="sxs-lookup"><span data-stu-id="30e7b-107">For multidimensional databases, Analysis Services builds caches in the formula engine when evaluating a calculation, and in the storage engine for the results of dimension queries and measure group queries.</span></span> <span data-ttu-id="30e7b-108">當公式引擎需要資料格座標或 Subcube 的量值資料時，就會發生量值群組查詢。</span><span class="sxs-lookup"><span data-stu-id="30e7b-108">Measure group queries occur when the formula engine needs measure data for a cell coordinate or subcube.</span></span> <span data-ttu-id="30e7b-109">查詢非自然階層以及套用自動存在時，就會發生維度查詢。</span><span class="sxs-lookup"><span data-stu-id="30e7b-109">Dimension queries occur when querying unnatural hierarchies and when applying autoexists.</span></span>  
  
 <span data-ttu-id="30e7b-110">建議在進行效能測試時清除快取。</span><span class="sxs-lookup"><span data-stu-id="30e7b-110">Clearing the cache is recommended when conducting performance testing.</span></span> <span data-ttu-id="30e7b-111">藉由清除測試回合之間的快取，可確保快取不會將測量查詢設計變更影響的任何測試結果扭曲。</span><span class="sxs-lookup"><span data-stu-id="30e7b-111">By clearing the cache between test runs, you ensure that caching does not skew any test results that measure the impact of a query design change.</span></span>  
  
 <span data-ttu-id="30e7b-112">**何時清除表格式模型的快取**</span><span class="sxs-lookup"><span data-stu-id="30e7b-112">**When to clear the cache for tabular models**</span></span>  
  
 <span data-ttu-id="30e7b-113">表格式模型通常儲存在記憶體中，而在執行查詢時執行彙總和其他計算。</span><span class="sxs-lookup"><span data-stu-id="30e7b-113">Tabular models are generally stored in memory, where aggregations and other calculations are performed at the time a query is executed.</span></span> <span data-ttu-id="30e7b-114">因此，ClearCache 命令對表格式模型影響有限。</span><span class="sxs-lookup"><span data-stu-id="30e7b-114">As such, the ClearCache command has a limited effect on tabular models.</span></span> <span data-ttu-id="30e7b-115">對於表格式模型，如果對它執行 MDX 查詢，資料可加入至 Analysis Services 快取。</span><span class="sxs-lookup"><span data-stu-id="30e7b-115">For a tabular model, data may be added to the Analysis Services caches if MDX queries are run against it.</span></span> <span data-ttu-id="30e7b-116">具體來說，MDX 和自動存在作業所參考的 DAX 量值會將結果分別快取在公式快取和維度快取中。</span><span class="sxs-lookup"><span data-stu-id="30e7b-116">In particular, DAX measures referenced by MDX and autoexists operations can cache results in the formula cache and dimension cache respectively.</span></span> <span data-ttu-id="30e7b-117">但請注意，非自然階層和量值群組查詢不會將結果快取在儲存引擎中。</span><span class="sxs-lookup"><span data-stu-id="30e7b-117">Note however, that unnatural hierarchies and measure group queries do not cache results in the storage engine.</span></span> <span data-ttu-id="30e7b-118">此外，務必了解 DAX 查詢不會將結果快取在公式和儲存引擎中。</span><span class="sxs-lookup"><span data-stu-id="30e7b-118">Additionally, it is important to recognize that DAX queries do not cache results in the formula and storage engine.</span></span> <span data-ttu-id="30e7b-119">另一方面來說，MDX 查詢會產生快取，而對表格式模型執行 ClearCache 會導致系統的任何快取資料無效。</span><span class="sxs-lookup"><span data-stu-id="30e7b-119">To the extent that caches exist as a result of MDX queries, running ClearCache against a tabular model will invalidate any cached data from the system.</span></span>  
  
 <span data-ttu-id="30e7b-120">執行 ClearCache 也會清除 xVelocity 記憶體中分析引擎 (VertiPaq) 中的記憶體中快取。</span><span class="sxs-lookup"><span data-stu-id="30e7b-120">Running ClearCache will also clear in-memory caches in the xVelocity in-memory analytics engine (VertiPaq).</span></span> <span data-ttu-id="30e7b-121">xVelocity 引擎維護小型的快取結果集。</span><span class="sxs-lookup"><span data-stu-id="30e7b-121">The xVelocity engine maintains a small set of cached results.</span></span> <span data-ttu-id="30e7b-122">執行 ClearCache 會導致 xVelocity 引擎中的這些快取無效。</span><span class="sxs-lookup"><span data-stu-id="30e7b-122">Running ClearCache will invalidate these caches in the xVelocity engine.</span></span>  
  
 <span data-ttu-id="30e7b-123">最後，在表格式模型重新設定為 `DirectQuery` 模式時，執行 ClearCache 也會移除記憶體中的剩餘資料。</span><span class="sxs-lookup"><span data-stu-id="30e7b-123">Finally, running ClearCache will also remove residual data that is left in memory when a tabular model is reconfigured for `DirectQuery` mode.</span></span> <span data-ttu-id="30e7b-124">如果模型包含受到嚴格控制的敏感性資料，這是特別重要的。</span><span class="sxs-lookup"><span data-stu-id="30e7b-124">This is particularly important if the model contains sensitive data that is subject to tight controls.</span></span> <span data-ttu-id="30e7b-125">在此情況下，執行 ClearCache 是可採取的預防動作，以確保敏感性資料只存在於預期的地方。</span><span class="sxs-lookup"><span data-stu-id="30e7b-125">In this case, running ClearCache is a precautionary action that you can take to ensure that sensitive data exists only where you expect it to be.</span></span> <span data-ttu-id="30e7b-126">如果您使用 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 部署模型及變更查詢模式，則需要手動清除快取。</span><span class="sxs-lookup"><span data-stu-id="30e7b-126">Clearing the cache manually is necessary if you are using [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] to deploy the model and change the query mode.</span></span> <span data-ttu-id="30e7b-127">相反地，使用 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] 在模型和資料分割上指定 `DirectQuery`，則會在您將模型切換為使用該查詢模式時自動清除快取。</span><span class="sxs-lookup"><span data-stu-id="30e7b-127">In contrast, using [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] to specify `DirectQuery` on the model and partitions will automatically clear the cache when you switch the model to use that query mode.</span></span>  
  
 <span data-ttu-id="30e7b-128">相較於效能測試期間清除多維度模型快取的建議，並沒有清除表格式模型快取的廣泛建議。</span><span class="sxs-lookup"><span data-stu-id="30e7b-128">Compared with recommendations for clearing multidimensional model caches during performance testing, there is no broad recommendation for clearing tabular model caches.</span></span> <span data-ttu-id="30e7b-129">如果您未管理包含敏感性資料的表格式模型部署，則沒有需要清除快取的特定管理工作。</span><span class="sxs-lookup"><span data-stu-id="30e7b-129">If you are not managing the deployment of a tabular model that contains sensitive data, there is no specific administrative task that calls for clearing the cache.</span></span>  
  
## <a name="clear-the-cache-for-analysis-services-models"></a><span data-ttu-id="30e7b-130">清除 Analysis Services 模型的快取</span><span class="sxs-lookup"><span data-stu-id="30e7b-130">Clear the cache for Analysis Services models</span></span>  
 <span data-ttu-id="30e7b-131">若要清除快取，請使用 XMLA 和 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="30e7b-131">To clear the cache, use XMLA and [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="30e7b-132">您可以清除資料庫、Cube、維度、資料表或量值群組層級的快取。</span><span class="sxs-lookup"><span data-stu-id="30e7b-132">You can clear the cache at the database, cube, dimension or table, or measure group level.</span></span> <span data-ttu-id="30e7b-133">下列清除資料庫層級快取的步驟適用於多維度模型和表格式模型。</span><span class="sxs-lookup"><span data-stu-id="30e7b-133">The following steps for clearing the cache at the database level apply to both multidimensional models and tabular models.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="30e7b-134">嚴格的效能測試可能需要更完整的方法來清除快取。</span><span class="sxs-lookup"><span data-stu-id="30e7b-134">Rigorous performance testing might require a more comprehensive approach to clearing the cache.</span></span> <span data-ttu-id="30e7b-135">如需如何排清 Analysis Services 和檔案系統快取的指示，請參閱 [SQL Server 2008 R2 Analysis Services Operations Guide](https://go.microsoft.com/fwlink/?linkID=https://go.microsoft.com/fwlink/?LinkID=225539)(SQL Server 2008 R2 Analysis Services 操作指南) 中關於清除快取的章節。</span><span class="sxs-lookup"><span data-stu-id="30e7b-135">For instructions on how to flush Analysis Services and file system caches, see the section on clearing caches in the [SQL Server 2008 R2 Analysis Services Operations Guide](https://go.microsoft.com/fwlink/?linkID=https://go.microsoft.com/fwlink/?LinkID=225539).</span></span>  
  
 <span data-ttu-id="30e7b-136">對於多維度和表格式模型，清除部分快取是兩步驟的程序，包含在執行 ClearCache 時導致快取無效，接著在接收下一個查詢時清空快取。</span><span class="sxs-lookup"><span data-stu-id="30e7b-136">For both multidimensional and tabular models, clearing some of these caches can be a two-step process that consists of invalidating the cache when ClearCache executes, followed by emptying the cache when the next query is received.</span></span> <span data-ttu-id="30e7b-137">記憶體耗用量只在快取實際上清空後才會明顯減少。</span><span class="sxs-lookup"><span data-stu-id="30e7b-137">A reduction in memory consumption will be evident only after the cache is actually emptied.</span></span>  
  
 <span data-ttu-id="30e7b-138">清除快取需要您在 XMLA 查詢中的 `ClearCache` 陳述式提供物件識別碼。</span><span class="sxs-lookup"><span data-stu-id="30e7b-138">Clearing the cache requires that you provide an object identifier to the `ClearCache` statement in an XMLA query.</span></span> <span data-ttu-id="30e7b-139">本主題中的第一個步驟解釋如何取得物件識別碼。</span><span class="sxs-lookup"><span data-stu-id="30e7b-139">The first step in this topic explains how to get an object identifier.</span></span>  
  
#### <a name="step-1-get-the-object-identifier"></a><span data-ttu-id="30e7b-140">步驟 1：取得物件識別碼</span><span class="sxs-lookup"><span data-stu-id="30e7b-140">Step 1: Get the object identifier</span></span>  
  
1.  <span data-ttu-id="30e7b-141">在 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 中，以滑鼠右鍵按一下物件，並選取 [屬性]\*\*\*\*，然後將 ID 屬性的值複製到 [屬性]\*\*\*\* 窗格。</span><span class="sxs-lookup"><span data-stu-id="30e7b-141">In [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], right-click an object, select **Properties**, and copy the value from the ID property in the **Properties** pane.</span></span> <span data-ttu-id="30e7b-142">這種方法適用於資料庫、Cube、維度或資料表。</span><span class="sxs-lookup"><span data-stu-id="30e7b-142">This approach works for the database, cube, dimension, or table.</span></span>  
  
2.  <span data-ttu-id="30e7b-143">若要取得量值群組識別碼，以滑鼠右鍵按一下該量值群組並選取 [編寫量值群組的指令碼為]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="30e7b-143">To get the measure group ID, right-click the measure group and select **Script Measure Group As**.</span></span> <span data-ttu-id="30e7b-144">選擇 [建立]\*\*\*\* 或 [改變]\*\*\*\*，並將查詢傳送至視窗。</span><span class="sxs-lookup"><span data-stu-id="30e7b-144">Choose either **Create** or **Alter**, and send the query to a window.</span></span> <span data-ttu-id="30e7b-145">量值群組識別碼會在物件定義中顯示。</span><span class="sxs-lookup"><span data-stu-id="30e7b-145">The ID of the measure group will be visible in the object definition.</span></span> <span data-ttu-id="30e7b-146">複製物件定義的識別碼。</span><span class="sxs-lookup"><span data-stu-id="30e7b-146">Copy the ID of the object definition.</span></span>  
  
#### <a name="step-2-run-the-query"></a><span data-ttu-id="30e7b-147">步驟 2：執行查詢</span><span class="sxs-lookup"><span data-stu-id="30e7b-147">Step 2: Run the query</span></span>  
  
1.  <span data-ttu-id="30e7b-148">在 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 中，以滑鼠右鍵按一下資料庫，並指向 [新增查詢]\*\*\*\*，然後選取 [XMLA]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="30e7b-148">In [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], right-click a database, point to **New Query**, and select **XMLA**.</span></span>  
  
2.  <span data-ttu-id="30e7b-149">將下列程式碼範例複製到 XMLA 查詢視窗。</span><span class="sxs-lookup"><span data-stu-id="30e7b-149">Copy the following code example into the XMLA query window.</span></span> <span data-ttu-id="30e7b-150">將 `DatabaseID` 變更為目前連接上的資料庫識別碼。</span><span class="sxs-lookup"><span data-stu-id="30e7b-150">Change `DatabaseID` to the ID of the database on the current connection.</span></span>  
  
    ```  
    <ClearCache xmlns="https://schemas.microsoft.com/analysisservices/2003/engine">  
      <Object>  
        <DatabaseID> Adventure Works DW Multidimensional</DatabaseID>  
      </Object>  
    </ClearCache>  
  
    ```  
  
     <span data-ttu-id="30e7b-151">或者，您也可以指定子物件 (例如量值群組) 的路徑，只清除該物件的快取。</span><span class="sxs-lookup"><span data-stu-id="30e7b-151">Alternatively, you can specify a path of a child object, such as a measure group, to clear the cache for just that object.</span></span>  
  
    ```  
    <ClearCache xmlns="https://schemas.microsoft.com/analysisservices/2003/engine">  
      <Object>  
        <DatabaseID>Adventure Works DW Multidimensional</DatabaseID>  
            <CubeID>Adventure Works</CubeID>  
            <MeasureGroupID>Fact Currency Rate</MeasureGroupID>  
      </Object>  
    </ClearCache>  
    ```  
  
3.  <span data-ttu-id="30e7b-152">按 F5 執行查詢。</span><span class="sxs-lookup"><span data-stu-id="30e7b-152">Press F5 to execute the query.</span></span> <span data-ttu-id="30e7b-153">您應該會看到下列結果：</span><span class="sxs-lookup"><span data-stu-id="30e7b-153">You should see the following result:</span></span>  
  
    ```  
    <return xmlns="urn:schemas-microsoft-com:xml-analysis">  
      <root xmlns="urn:schemas-microsoft-com:xml-analysis:empty" />  
    </return>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="30e7b-154">另請參閱</span><span class="sxs-lookup"><span data-stu-id="30e7b-154">See Also</span></span>  
 <span data-ttu-id="30e7b-155">[在 Analysis Services 中編寫管理工作的腳本](../script-administrative-tasks-in-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="30e7b-155">[Script Administrative Tasks in Analysis Services](../script-administrative-tasks-in-analysis-services.md) </span></span>  
 [<span data-ttu-id="30e7b-156">Monitor an Analysis Services Instance</span><span class="sxs-lookup"><span data-stu-id="30e7b-156">Monitor an Analysis Services Instance</span></span>](monitor-an-analysis-services-instance.md)  
  
  
