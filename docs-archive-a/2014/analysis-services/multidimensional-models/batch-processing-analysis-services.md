---
title: 批次處理 (Analysis Services) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- batches [Analysis Services]
ms.assetid: ba4dcf72-0667-41d0-816b-ab8ff9a7d9cb
author: minewiskan
ms.author: owend
ms.openlocfilehash: c777339f41f5f9029e4d03d47cc7f682e00032b8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585647"
---
# <a name="batch-processing-analysis-services"></a><span data-ttu-id="55b85-102">批次處理 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="55b85-102">Batch Processing (Analysis Services)</span></span>
  <span data-ttu-id="55b85-103">在 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]中，您可以使用 [批次] 命令，以單一要求將多個處理命令傳送至伺服器。</span><span class="sxs-lookup"><span data-stu-id="55b85-103">In [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], you can use the Batch command to send multiple processing commands to the server in a single request.</span></span> <span data-ttu-id="55b85-104">批次處理讓您可以控制要處理的物件和處理順序。</span><span class="sxs-lookup"><span data-stu-id="55b85-104">Batch processing gives you a way to control which objects are to be processed, and in what order.</span></span> <span data-ttu-id="55b85-105">此外，批次可以當做一系列獨立的作業來執行，或是做為交易執行，其中若有一個處理序失敗，就會造成整個批次全部回復。</span><span class="sxs-lookup"><span data-stu-id="55b85-105">Also, a batch can run as a series of stand-alone jobs, or as a transaction in which the failure of one process causes a rollback of the complete batch.</span></span>  
  
 <span data-ttu-id="55b85-106">批次處理透過合併及縮短認可變更所需的時間，來提高資料可用性。</span><span class="sxs-lookup"><span data-stu-id="55b85-106">Batch processing maximizes data availability by consolidating and reducing the amount of time taken to commit changes.</span></span> <span data-ttu-id="55b85-107">當您完整處理維度時，任何使用該維度的分割區都會標示為尚未處理。</span><span class="sxs-lookup"><span data-stu-id="55b85-107">When you fully process a dimension, any partition using that dimension is marked as unprocessed.</span></span> <span data-ttu-id="55b85-108">因此，包含尚未處理之分割區的 Cube 都無法瀏覽。</span><span class="sxs-lookup"><span data-stu-id="55b85-108">As a result, cubes that contain the unprocessed partitions are unavailable for browsing.</span></span> <span data-ttu-id="55b85-109">您可以同時處理維度和受影響的分割區，藉由批次處理作業的方式處理解決這種狀況。</span><span class="sxs-lookup"><span data-stu-id="55b85-109">You can address this with a batch processing job by processing the dimensions together with the affected partitions.</span></span> <span data-ttu-id="55b85-110">將批次處理工作當做交易執行，可確保包含在交易中的所有物件保持可供查詢，直到所有處理完成為止。</span><span class="sxs-lookup"><span data-stu-id="55b85-110">Running the batch processing job as a transaction makes sure that all objects included in the transaction remain available for queries until all processing is completed.</span></span> <span data-ttu-id="55b85-111">當交易認可有所變更時，受影響的物件上會遭到鎖定，讓物件暫時無法使用，但是認可變更所使用的整體時間會比您個別處理物件還短。</span><span class="sxs-lookup"><span data-stu-id="55b85-111">As the transaction commits the changes, locks are put on the affected objects, making the objects temporarily unavailable, but overall the amount of time used to commit the changes is less than if you processed objects individually.</span></span>  
  
 <span data-ttu-id="55b85-112">本主題中的程序示範完整處理維度和分割區的步驟。</span><span class="sxs-lookup"><span data-stu-id="55b85-112">The procedures in this topic show the steps for fully processing dimensions and partitions.</span></span> <span data-ttu-id="55b85-113">批次處理也可以包含其他處理選項，如累加式處理。</span><span class="sxs-lookup"><span data-stu-id="55b85-113">Batch processing can also include other processing options, such as incremental processing.</span></span> <span data-ttu-id="55b85-114">若要讓這些程序正確運作，必須使用至少包含兩個維度和一個分割區的現有 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 資料庫。</span><span class="sxs-lookup"><span data-stu-id="55b85-114">For these procedures to work correctly, you should use an existing [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database that contains at least two dimensions and one partition.</span></span>  
  
 <span data-ttu-id="55b85-115">這個主題包括下列各節：</span><span class="sxs-lookup"><span data-stu-id="55b85-115">This topic includes the following sections:</span></span>  
  
 [<span data-ttu-id="55b85-116">SQL Server Data Tools 中的批次處理</span><span class="sxs-lookup"><span data-stu-id="55b85-116">Batch Processing in SQL Server Data Tools</span></span>](#bkmk_ssdt)  
  
 [<span data-ttu-id="55b85-117">在 Management Studio 中使用 XMLA 執行批次處理</span><span class="sxs-lookup"><span data-stu-id="55b85-117">Batch Processing using XMLA in Management Studio</span></span>](#bkmk_xmla)  
  
##  <a name="batch-processing-in-sql-server-data-tools"></a><a name="bkmk_ssdt"></a> <span data-ttu-id="55b85-118">SQL Server 資料工具中的批次處理</span><span class="sxs-lookup"><span data-stu-id="55b85-118">Batch Processing in SQL Server Data Tools</span></span>  
 <span data-ttu-id="55b85-119">在 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]中處理物件之前，必須先部署包含該物件的專案。</span><span class="sxs-lookup"><span data-stu-id="55b85-119">Before objects can be processed in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], the project that contains the objects must be deployed.</span></span> <span data-ttu-id="55b85-120">如需詳細資訊，請參閱[部署 Analysis Services 專案 &#40;SSDT&#41;](deploy-analysis-services-projects-ssdt.md)。</span><span class="sxs-lookup"><span data-stu-id="55b85-120">For more information, see [Deploy Analysis Services Projects &#40;SSDT&#41;](deploy-analysis-services-projects-ssdt.md).</span></span>  
  
1.  <span data-ttu-id="55b85-121">開啟 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="55b85-121">Open [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)].</span></span>  
  
2.  <span data-ttu-id="55b85-122">開啟已部署的專案。</span><span class="sxs-lookup"><span data-stu-id="55b85-122">Open a project that has been deployed.</span></span>  
  
3.  <span data-ttu-id="55b85-123">在 [方案總管] 中，已部署的專案之下，展開 **[維度]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="55b85-123">In Solution Explorer, under the deployed project, expand the **Dimensions** folder.</span></span>  
  
4.  <span data-ttu-id="55b85-124">按住 Ctrl 鍵，並按一下 **[維度]** 資料夾中列出的每個維度。</span><span class="sxs-lookup"><span data-stu-id="55b85-124">Holding the Ctrl key, click each dimension listed in the **Dimensions** folder.</span></span>  
  
5.  <span data-ttu-id="55b85-125">以滑鼠右鍵按一下選取的維度，然後按一下 [處理]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="55b85-125">Right-click the selected dimensions, and then click **Process**.</span></span>  
  
6.  <span data-ttu-id="55b85-126">按住 Ctrl 鍵，並按一下 **[物件清單]** 中列出的每個維度。</span><span class="sxs-lookup"><span data-stu-id="55b85-126">Holding the Ctrl key, click each dimension listed in the **Object list**.</span></span>  
  
7.  <span data-ttu-id="55b85-127">以滑鼠右鍵按一下選取的維度，然後選取 [完整處理]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="55b85-127">Right-click the selected dimensions and select **Process Full**.</span></span>  
  
8.  <span data-ttu-id="55b85-128">若要自訂批次處理作業，請按一下 **[變更設定]**。</span><span class="sxs-lookup"><span data-stu-id="55b85-128">To customize the batch process job, click **Change Settings.**</span></span>  
  
9. <span data-ttu-id="55b85-129">在 **[處理選項]** 下標示下列設定：</span><span class="sxs-lookup"><span data-stu-id="55b85-129">Under **Processing options**, mark the following settings:</span></span>  
  
    -   <span data-ttu-id="55b85-130">將 **[處理順序]** 設定為 **[循序]**，並將 **[交易模式]** 設定為 **[一筆交易]**。</span><span class="sxs-lookup"><span data-stu-id="55b85-130">**Processing Order** is set to **Sequential**, and **Transaction mode** is set to **One Transaction**.</span></span>  
  
    -   <span data-ttu-id="55b85-131">將 **[回寫資料表選項]** 設定為 **[使用現有的]**。</span><span class="sxs-lookup"><span data-stu-id="55b85-131">**Writeback Table Option** is set to **Use existing**.</span></span>  
  
    -   <span data-ttu-id="55b85-132">在 **[受影響的物件]** 下，選取 **[處理受影響的物件]** 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="55b85-132">Under **Affected Objects**, select the **Process affected objects** check box.</span></span>  
  
10. <span data-ttu-id="55b85-133">按一下 [**維度索引鍵錯誤**] 索引標籤。請確認已選取 [**使用預設錯誤**設定]。</span><span class="sxs-lookup"><span data-stu-id="55b85-133">Click the **Dimension key errors** tab. Verify that **Use default error configuration** is selected.</span></span>  
  
11. <span data-ttu-id="55b85-134">按一下 **[確定]** ，關閉 **[變更設定]** 畫面。</span><span class="sxs-lookup"><span data-stu-id="55b85-134">Click **OK** to close the **Change Settings** screen.</span></span>  
  
12. <span data-ttu-id="55b85-135">在 **[處理物件]** 畫面中按一下 **[執行]** ，以啟動處理作業。</span><span class="sxs-lookup"><span data-stu-id="55b85-135">Click **Run** in the **Process Objects** screen to start the processing job.</span></span>  
  
13. <span data-ttu-id="55b85-136">當 **[狀態]** 方塊顯示 **[處理成功]** 時，按一下 **[關閉]**。</span><span class="sxs-lookup"><span data-stu-id="55b85-136">When the **Status** box shows **Process succeeded**, click **Close**.</span></span>  
  
14. <span data-ttu-id="55b85-137">按一下 **[處理物件]** 畫面上的 **[關閉]** 。</span><span class="sxs-lookup"><span data-stu-id="55b85-137">Click **Close** on the **Process Objects** screen.</span></span>  
  
##  <a name="batch-processing-using-xmla-in-management-studio"></a><a name="bkmk_xmla"></a><span data-ttu-id="55b85-138">在 Management Studio 中使用 XMLA 的批次處理</span><span class="sxs-lookup"><span data-stu-id="55b85-138">Batch Processing using XMLA in Management Studio</span></span>  
 <span data-ttu-id="55b85-139">您可以建立執行批次處理的 XMLA 指令碼。</span><span class="sxs-lookup"><span data-stu-id="55b85-139">You can create an XMLA script that performs batch processing.</span></span> <span data-ttu-id="55b85-140">首先在 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 中為每個物件產生 XMLA 指令碼，然後將它們結合為可以互動方式執行或在排程工作內執行的單一 XMLA 查詢。</span><span class="sxs-lookup"><span data-stu-id="55b85-140">Start by generating an XMLA script in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] for each object, and then combine them into a single XMLA Query that you run interactively or inside a scheduled task.</span></span>  
  
 <span data-ttu-id="55b85-141">如需逐步指示，請參閱 **使用 SQL Server Agent 排程 SSAS 管理工作** 中的 [範例 2](../instances/schedule-ssas-administrative-tasks-with-sql-server-agent.md)</span><span class="sxs-lookup"><span data-stu-id="55b85-141">For step by step instructions, see **Example 2** in [Schedule SSAS Administrative Tasks with SQL Server Agent](../instances/schedule-ssas-administrative-tasks-with-sql-server-agent.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55b85-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="55b85-142">See Also</span></span>  
 [<span data-ttu-id="55b85-143">多維度模型物件處理</span><span class="sxs-lookup"><span data-stu-id="55b85-143">Multidimensional Model Object Processing</span></span>](processing-a-multidimensional-model-analysis-services.md)  
  
  
