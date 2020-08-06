---
title: 異動資料擷取 (SSIS) | Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- incremental loads [SQL Server change data capture]
- change data capture [SQL Server], Integration Services and
ms.assetid: c4aaba1b-73e5-4187-a97b-61c10069cc5a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 55293d4e2caa4c31cb004a2cdf1cda99769c77e2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704354"
---
# <a name="change-data-capture-ssis"></a><span data-ttu-id="4e5bc-102">異動資料擷取 (SSIS)</span><span class="sxs-lookup"><span data-stu-id="4e5bc-102">Change Data Capture (SSIS)</span></span>
  <span data-ttu-id="4e5bc-103">在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 中，異動資料擷取會針對將累加式載入從來源資料表有效執行到資料超市和資料倉儲的挑戰，提供有效的方案。</span><span class="sxs-lookup"><span data-stu-id="4e5bc-103">In [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], change data capture offers an effective solution to the challenge of efficiently performing incremental loads from source tables to data marts and data warehouses.</span></span>

## <a name="what-is-change-data-capture"></a><span data-ttu-id="4e5bc-104">什麼是異動資料擷取？</span><span class="sxs-lookup"><span data-stu-id="4e5bc-104">What is Change Data Capture?</span></span>
 <span data-ttu-id="4e5bc-105">來源資料表會隨著時間變更。</span><span class="sxs-lookup"><span data-stu-id="4e5bc-105">Source tables change over time.</span></span> <span data-ttu-id="4e5bc-106">以這些資料表為基礎的資料超市或資料倉儲必須反映這些變更。</span><span class="sxs-lookup"><span data-stu-id="4e5bc-106">A data mart or data warehouse that is based on those tables needs to reflect these changes.</span></span> <span data-ttu-id="4e5bc-107">不過，定期複製完整來源之快照集的程序會耗費太多時間和資源。</span><span class="sxs-lookup"><span data-stu-id="4e5bc-107">However, a process that periodically copies a snapshot of the entire source consumes too much time and resources.</span></span> <span data-ttu-id="4e5bc-108">包括時間戳記資料行、觸發程序或複雜查詢的替代方式通常有損效能並增加複雜度。</span><span class="sxs-lookup"><span data-stu-id="4e5bc-108">Alternate approaches that include timestamp columns, triggers, or complex queries often hurt performance and increase complexity.</span></span> <span data-ttu-id="4e5bc-109">需要的是變更資料結構化的可靠資料流，讓消費者可以將其輕鬆地套用到資料的目標表示法。</span><span class="sxs-lookup"><span data-stu-id="4e5bc-109">What is needed is a reliable stream of change data that is structured so that it can easily be applied by consumers to target representations of the data.</span></span> <span data-ttu-id="4e5bc-110">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 中的異動資料擷取會提供這個解決方案。</span><span class="sxs-lookup"><span data-stu-id="4e5bc-110">Change data capture in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] provides this solution.</span></span>

 <span data-ttu-id="4e5bc-111">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 的異動資料擷取功能會擷取套用到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 資料表的插入、更新與刪除活動，並以容易取用的關聯式格式，提供變更的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="4e5bc-111">The change data capture feature of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] captures insert, update, and delete activity applied to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] tables, and makes the details of the changes available in an easily-consumed, relational format.</span></span> <span data-ttu-id="4e5bc-112">異動資料擷取所使用的變更資料表包含鏡像追蹤來源資料表之資料行結構的資料行，以及了解逐資料列發生之變更所需的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="4e5bc-112">The change tables used by change data capture contain columns that mirror the column structure of the tracked source tables, along with the metadata needed to understand the changes that have occurred on a row by row basis.</span></span>

> [!NOTE]
>  <span data-ttu-id="4e5bc-113">並非每個 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]版本中都無法異動資料擷取。</span><span class="sxs-lookup"><span data-stu-id="4e5bc-113">Change data capture is not available in every edition of [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="4e5bc-114">如需版本支援的功能清單 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ，請參閱[SQL Server 2014 版本支援的功能](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)。</span><span class="sxs-lookup"><span data-stu-id="4e5bc-114">For a list of features that are supported by the editions of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], see [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>

## <a name="how-change-data-capture-works-in-integration-services"></a><span data-ttu-id="4e5bc-115">異動資料擷取在 Integration Services 中的運作方式</span><span class="sxs-lookup"><span data-stu-id="4e5bc-115">How Change Data Capture Works in Integration Services</span></span>
 <span data-ttu-id="4e5bc-116">[!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 封裝可以輕易地收集 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 資料庫中的異動資料，從而對資料倉儲執行有效率的累加式載入。</span><span class="sxs-lookup"><span data-stu-id="4e5bc-116">An [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] package can easily harvest the change data in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] databases to perform efficient incremental loads to a data warehouse.</span></span> <span data-ttu-id="4e5bc-117">不過，在您可以使用 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 載入變更資料前，管理員必須在您要擷取變更的資料庫和資料表上啟用異動資料擷取。</span><span class="sxs-lookup"><span data-stu-id="4e5bc-117">However, before you can use [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] to load change data, an administrator must enable change data capture on the database and the tables from which you want to capture changes.</span></span> <span data-ttu-id="4e5bc-118">如需如何在資料庫上設定異動資料擷取的詳細資訊，請參閱[啟用和停用異動資料擷取 &#40;SQL Server&#41;](../../relational-databases/track-changes/enable-and-disable-change-data-capture-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="4e5bc-118">For more information on how to configure change data capture on a database, see [Enable and Disable Change Data Capture &#40;SQL Server&#41;](../../relational-databases/track-changes/enable-and-disable-change-data-capture-sql-server.md).</span></span>

 <span data-ttu-id="4e5bc-119">一旦管理員已經在資料庫上啟用異動資料擷取，您就可以建立執行累加式變更資料載入的封裝。</span><span class="sxs-lookup"><span data-stu-id="4e5bc-119">Once an administrator has enabled change data capture on the database, you can create a package that performs an incremental load of the change data.</span></span> <span data-ttu-id="4e5bc-120">下圖顯示建立可從單一資料表執行累加式載入這種封裝的步驟：</span><span class="sxs-lookup"><span data-stu-id="4e5bc-120">The following diagram shows the steps for creating such a package that performs an incremental load from a single table:</span></span>

 <span data-ttu-id="4e5bc-121">![異動資料擷取套件建立步驟](../media/cdc-package-creation.gif "異動資料擷取套件建立步驟")</span><span class="sxs-lookup"><span data-stu-id="4e5bc-121">![Change Data Capture Package Creation Steps](../media/cdc-package-creation.gif "Change Data Capture Package Creation Steps")</span></span>

 <span data-ttu-id="4e5bc-122">如上圖所示，建立可執行累加式變更資料載入的封裝包含下列步驟：</span><span class="sxs-lookup"><span data-stu-id="4e5bc-122">As shown in the previous diagram, creating a package that performs an incremental load of changed data involves the following steps:</span></span>

 <span data-ttu-id="4e5bc-123">**步驟1：設計控制流程**在封裝的控制流程中，必須定義下列工作：</span><span class="sxs-lookup"><span data-stu-id="4e5bc-123">**Step 1: Designing the Control Flow** In the control flow in the package, the following tasks need to be defined:</span></span>

-   <span data-ttu-id="4e5bc-124">針對您要擷取的來源資料，計算變更間隔的開始和結束 `datetime` 值。</span><span class="sxs-lookup"><span data-stu-id="4e5bc-124">Calculate the starting and ending `datetime` values for the interval of changes to the source data that you want to retrieve.</span></span>

     <span data-ttu-id="4e5bc-125">若要計算這些值，請搭配 `datetime` 函數使用「執行 SQL」工作或 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 運算式。</span><span class="sxs-lookup"><span data-stu-id="4e5bc-125">To calculate these values, use an Execute SQL task or [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] expressions with `datetime` functions.</span></span> <span data-ttu-id="4e5bc-126">然後您可以用封裝變數儲存這些端點，以便稍後在封裝中使用。</span><span class="sxs-lookup"><span data-stu-id="4e5bc-126">You then store these endpoints in package variables for use later in the package.</span></span>

     <span data-ttu-id="4e5bc-127">**如需詳細資訊，請參閱**  [指定變更資料的間隔](specify-an-interval-of-change-data.md)</span><span class="sxs-lookup"><span data-stu-id="4e5bc-127">**For more information:**  [Specify an Interval of Change Data](specify-an-interval-of-change-data.md)</span></span>

-   <span data-ttu-id="4e5bc-128">判斷所選間隔的變更資料是否就緒。</span><span class="sxs-lookup"><span data-stu-id="4e5bc-128">Determine whether the change data for the selected interval is ready.</span></span> <span data-ttu-id="4e5bc-129">由於非同步的擷取程序可能還沒有達到所選的端點，因此這是必要的步驟。</span><span class="sxs-lookup"><span data-stu-id="4e5bc-129">This step is necessary because the asynchronous capture process might not yet have reached the selected endpoint.</span></span>

     <span data-ttu-id="4e5bc-130">若要判斷資料是否就緒，如果必要，開始使用「For 迴圈」容器延遲執行，直到所選間隔的變更資料就緒為止。</span><span class="sxs-lookup"><span data-stu-id="4e5bc-130">To determine whether the data is ready, start with a For Loop container to delay execution, if necessary, until the change data for the selected interval is ready.</span></span> <span data-ttu-id="4e5bc-131">在迴圈容器內部，使用「執行 SQL」工作查詢由異動資料擷取所維護的時間對應資料表。</span><span class="sxs-lookup"><span data-stu-id="4e5bc-131">Inside the loop container, use an Execute SQL task to query the time mapping tables maintained by change data capture.</span></span> <span data-ttu-id="4e5bc-132">然後，使用呼叫 `Thread.Sleep` 方法的「指令碼」工作，或搭配 `WAITFOR` 陳述式使用另一個「執行 SQL」工作，暫時延遲封裝的執行 (如有必要)。</span><span class="sxs-lookup"><span data-stu-id="4e5bc-132">Then, use a Script task that calls the `Thread.Sleep` method, or another Execute SQL task with a `WAITFOR` statement, to delay the execution of the package temporarily, if necessary.</span></span> <span data-ttu-id="4e5bc-133">或者，使用其他「指令碼」工作記錄錯誤條件或逾時。</span><span class="sxs-lookup"><span data-stu-id="4e5bc-133">Optionally, use another Script task to log an error condition or a timeout.</span></span>

     <span data-ttu-id="4e5bc-134">**如需詳細資訊，請參閱**  [判斷變更資料是否就緒](determine-whether-the-change-data-is-ready.md)</span><span class="sxs-lookup"><span data-stu-id="4e5bc-134">**For more information:**  [Determine Whether the Change Data Is Ready](determine-whether-the-change-data-is-ready.md)</span></span>

-   <span data-ttu-id="4e5bc-135">準備將用於查詢變更資料的查詢字串。</span><span class="sxs-lookup"><span data-stu-id="4e5bc-135">Prepare the query string that will be used to query for the change data.</span></span>

     <span data-ttu-id="4e5bc-136">使用「指令碼」工作或「執行 SQL」工作來組合將用於查詢變更的 SQL 陳述式。</span><span class="sxs-lookup"><span data-stu-id="4e5bc-136">Use a Script task or an Execute SQL task to assemble the SQL statement that will be used to query for changes.</span></span>

     <span data-ttu-id="4e5bc-137">**如需詳細資訊，請參閱**  [準備查詢變更資料](prepare-to-query-for-the-change-data.md)</span><span class="sxs-lookup"><span data-stu-id="4e5bc-137">**For more information:**  [Prepare to Query for the Change Data](prepare-to-query-for-the-change-data.md)</span></span>

 <span data-ttu-id="4e5bc-138">**步驟2：設定變更資料的查詢**建立將查詢資料的資料表值函數。</span><span class="sxs-lookup"><span data-stu-id="4e5bc-138">**Step 2: Setting Up the Query for Change Data** Create the table-valued function that will query for the data.</span></span>

 <span data-ttu-id="4e5bc-139">使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 來開發及儲存查詢。</span><span class="sxs-lookup"><span data-stu-id="4e5bc-139">Use [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to develop and save the query.</span></span>

 <span data-ttu-id="4e5bc-140">**如需詳細資訊，請參閱**  [擷取與了解變更資料](retrieve-and-understand-the-change-data.md)</span><span class="sxs-lookup"><span data-stu-id="4e5bc-140">**For more information:**  [Retrieve and Understand the Change Data](retrieve-and-understand-the-change-data.md)</span></span>

 <span data-ttu-id="4e5bc-141">**步驟3：設計資料流程**在封裝的資料流程中，必須定義下列工作：</span><span class="sxs-lookup"><span data-stu-id="4e5bc-141">**Step 3: Designing the Data Flow** In the data flow of the package, the following tasks need to be defined:</span></span>

-   <span data-ttu-id="4e5bc-142">從變更資料表擷取變更資料。</span><span class="sxs-lookup"><span data-stu-id="4e5bc-142">Retrieve the change data from the change tables.</span></span>

     <span data-ttu-id="4e5bc-143">若要擷取資料，使用來源元件來查詢所選間隔內之變更的變更資料表。</span><span class="sxs-lookup"><span data-stu-id="4e5bc-143">To retrieve the data, use a source component to query the change tables for the changes that fall within the selected interval.</span></span> <span data-ttu-id="4e5bc-144">此來源會呼叫您必須在先前已經建立的 Transact-SQL 資料表值函數。</span><span class="sxs-lookup"><span data-stu-id="4e5bc-144">The source calls a Transact-SQL table-valued function that you must have previously created.</span></span>

     <span data-ttu-id="4e5bc-145">**如需詳細資訊，請參閱**  [擷取與了解變更資料](retrieve-and-understand-the-change-data.md)</span><span class="sxs-lookup"><span data-stu-id="4e5bc-145">**For more information:**  [Retrieve and Understand the Change Data](retrieve-and-understand-the-change-data.md)</span></span>

-   <span data-ttu-id="4e5bc-146">將變更分割為要處理的插入、更新與刪除。</span><span class="sxs-lookup"><span data-stu-id="4e5bc-146">Split the changes into inserts, updates, and deletes for processing.</span></span>

     <span data-ttu-id="4e5bc-147">若要分割變更，使用「條件式分割」轉換，將插入、更新與刪除導引到不同的輸出以便進行適當的處理。</span><span class="sxs-lookup"><span data-stu-id="4e5bc-147">To split the changes, use a Conditional Split transformation to direct inserts, updates, and deletes to different outputs for appropriate processing.</span></span>

     <span data-ttu-id="4e5bc-148">**如需詳細資訊，請參閱**  [處理插入、更新與刪除](process-inserts-updates-and-deletes.md)</span><span class="sxs-lookup"><span data-stu-id="4e5bc-148">**For more information:**  [Process Inserts, Updates, and Deletes](process-inserts-updates-and-deletes.md)</span></span>

-   <span data-ttu-id="4e5bc-149">將插入、刪除與更新套用到目的地。</span><span class="sxs-lookup"><span data-stu-id="4e5bc-149">Apply the inserts, deletes, and updates to the destination.</span></span>

     <span data-ttu-id="4e5bc-150">若要將變更套用到目的地，請使用目的地元件，將插入套用到目的地。</span><span class="sxs-lookup"><span data-stu-id="4e5bc-150">To apply the changes to the destination, use a destination component to apply the inserts to the destination.</span></span> <span data-ttu-id="4e5bc-151">同時，搭配參數化的 UPDATE 和 DELETE 陳述式使用「OLE DB 命令」轉換，將更新與刪除套用到目的地。</span><span class="sxs-lookup"><span data-stu-id="4e5bc-151">Also, use OLE DB Command transformations with parameterized UPDATE and DELETE statements to apply updates and deletes to the destination.</span></span> <span data-ttu-id="4e5bc-152">您也可以使用目的地元件來套用更新與刪除，以便將資料列儲存到暫存資料表中。</span><span class="sxs-lookup"><span data-stu-id="4e5bc-152">You can also apply updates and deletes by using destination components to save the rows to temporary tables.</span></span> <span data-ttu-id="4e5bc-153">接著，使用「執行 SQL」工作，根據暫存資料表的目的地，執行大量更新與大量刪除作業。</span><span class="sxs-lookup"><span data-stu-id="4e5bc-153">Then, use Execute SQL tasks to perform bulk update and bulk delete operations against the destination from the temporary tables.</span></span>

     <span data-ttu-id="4e5bc-154">**如需詳細資訊，請參閱**  [將變更套用到目的地](apply-the-changes-to-the-destination.md)</span><span class="sxs-lookup"><span data-stu-id="4e5bc-154">**For more information:**  [Apply the Changes to the Destination](apply-the-changes-to-the-destination.md)</span></span>

### <a name="change-data-from-multiple-tables"></a><span data-ttu-id="4e5bc-155">多個資料表的資料變更</span><span class="sxs-lookup"><span data-stu-id="4e5bc-155">Change Data from Multiple Tables</span></span>
 <span data-ttu-id="4e5bc-156">在上圖與上述步驟中所述的程序包含來自單一資料表的累加式載入。</span><span class="sxs-lookup"><span data-stu-id="4e5bc-156">The process outlined in the previous diagram and steps involves an incremental load from a single table.</span></span> <span data-ttu-id="4e5bc-157">當您必須從多個資料表執行累加式載入時，整個程序都相同。</span><span class="sxs-lookup"><span data-stu-id="4e5bc-157">When having to perform an incremental load from multiple tables, the overall process is the same.</span></span> <span data-ttu-id="4e5bc-158">不過，必須變更封裝的設計以配合多個資料表的處理。</span><span class="sxs-lookup"><span data-stu-id="4e5bc-158">However, the design of the package needs to be changed to accommodate the processing of multiple tables.</span></span> <span data-ttu-id="4e5bc-159">如需如何建立可從多個資料表執行累加式載入之封裝的詳細資訊，請參閱 [執行多個資料表的累加式載入](perform-an-incremental-load-of-multiple-tables.md)。</span><span class="sxs-lookup"><span data-stu-id="4e5bc-159">For more information on how to create a package that performs an incremental load from multiples tables, see [Perform an Incremental Load of Multiple Tables](perform-an-incremental-load-of-multiple-tables.md).</span></span>

## <a name="samples-of-change-data-capture-packages"></a><span data-ttu-id="4e5bc-160">異動資料擷取封裝的範例</span><span class="sxs-lookup"><span data-stu-id="4e5bc-160">Samples of Change Data Capture Packages</span></span>
 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] <span data-ttu-id="4e5bc-161">提供兩個範例，示範如何在封裝中使用異動資料擷取。</span><span class="sxs-lookup"><span data-stu-id="4e5bc-161">provides two samples that demonstrate how to use change data capture in packages.</span></span> <span data-ttu-id="4e5bc-162">如需詳細資訊，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="4e5bc-162">For more information, see the following topics:</span></span>

-   [<span data-ttu-id="4e5bc-163">讀我檔案_指定之間隔的異動資料擷取封裝範例</span><span class="sxs-lookup"><span data-stu-id="4e5bc-163">Readme_Change Data Capture for Specified Interval Package Sample</span></span>](https://go.microsoft.com/fwlink/?LinkId=133507)

-   [<span data-ttu-id="4e5bc-164">讀我檔案_自上次要求後的異動資料擷取封裝範例</span><span class="sxs-lookup"><span data-stu-id="4e5bc-164">Readme_Change Data Capture since Last Request Package Sample</span></span>](https://go.microsoft.com/fwlink/?LinkId=133508)

## <a name="related-tasks"></a><span data-ttu-id="4e5bc-165">相關工作</span><span class="sxs-lookup"><span data-stu-id="4e5bc-165">Related Tasks</span></span>

-   [<span data-ttu-id="4e5bc-166">指定變更資料的間隔</span><span class="sxs-lookup"><span data-stu-id="4e5bc-166">Specify an Interval of Change Data</span></span>](specify-an-interval-of-change-data.md)

-   [<span data-ttu-id="4e5bc-167">判斷變更資料是否就緒</span><span class="sxs-lookup"><span data-stu-id="4e5bc-167">Determine Whether the Change Data Is Ready</span></span>](determine-whether-the-change-data-is-ready.md)

-   [<span data-ttu-id="4e5bc-168">準備查詢變更資料</span><span class="sxs-lookup"><span data-stu-id="4e5bc-168">Prepare to Query for the Change Data</span></span>](prepare-to-query-for-the-change-data.md)

-   [<span data-ttu-id="4e5bc-169">建立函數以擷取變更資料</span><span class="sxs-lookup"><span data-stu-id="4e5bc-169">Create the Function to Retrieve the Change Data</span></span>](create-the-function-to-retrieve-the-change-data.md)

-   [<span data-ttu-id="4e5bc-170">擷取與了解變更資料</span><span class="sxs-lookup"><span data-stu-id="4e5bc-170">Retrieve and Understand the Change Data</span></span>](retrieve-and-understand-the-change-data.md)

-   [<span data-ttu-id="4e5bc-171">處理插入、更新與刪除</span><span class="sxs-lookup"><span data-stu-id="4e5bc-171">Process Inserts, Updates, and Deletes</span></span>](process-inserts-updates-and-deletes.md)

-   [<span data-ttu-id="4e5bc-172">將變更套用到目的地</span><span class="sxs-lookup"><span data-stu-id="4e5bc-172">Apply the Changes to the Destination</span></span>](apply-the-changes-to-the-destination.md)

-   [<span data-ttu-id="4e5bc-173">執行多個資料表的累加式載入</span><span class="sxs-lookup"><span data-stu-id="4e5bc-173">Perform an Incremental Load of Multiple Tables</span></span>](perform-an-incremental-load-of-multiple-tables.md)

## <a name="related-content"></a><span data-ttu-id="4e5bc-174">相關內容</span><span class="sxs-lookup"><span data-stu-id="4e5bc-174">Related Content</span></span>
 <span data-ttu-id="4e5bc-175">sqlblog.com 上的部落格文章：[SSIS Design Pattern – Incremental Load](https://go.microsoft.com/fwlink/?LinkId=217679)(SSIS 設計模式 - 累加式載入)</span><span class="sxs-lookup"><span data-stu-id="4e5bc-175">Blog entry, [SSIS Design Pattern - Incremental Load](https://go.microsoft.com/fwlink/?LinkId=217679), on sqlblog.com</span></span>


