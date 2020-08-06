---
title: 量值群組 (資料分割索引標籤、Cube 設計工具)  (Analysis Services 多維度資料) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.partitions.partitionspane.measuregroupdetail.f1
ms.assetid: 58e44b24-cfcd-4908-b445-d4374b961b98
author: minewiskan
ms.author: owend
ms.openlocfilehash: 0b73b77bd62c38881be20450f0b7506917014461
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708829"
---
# <a name="measure-groups-partitions-tab-cube-designer-analysis-services---multidimensional-data"></a><span data-ttu-id="d1436-102">量值群組 (資料分割索引標籤，Cube 設計工具) (Analysis Services - 多維度資料)</span><span class="sxs-lookup"><span data-stu-id="d1436-102">Measure Groups (Partitions Tab, Cube Designer) (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="d1436-103">在 Cube 設計師的 [資料分割]\*\*\*\* 索引標籤上，使用 [量值群組]\*\*\*\* 窗格來管理與 Cube 中每個量值群組相關聯的資料分割。</span><span class="sxs-lookup"><span data-stu-id="d1436-103">Use the **Measure Groups** pane on the **Partitions** tab in Cube Designer to manage the partitions associated with each measure group in the cube.</span></span>  
  
## <a name="options"></a><span data-ttu-id="d1436-104">選項</span><span class="sxs-lookup"><span data-stu-id="d1436-104">Options</span></span>  
 <span data-ttu-id="d1436-105">**資料分割**</span><span class="sxs-lookup"><span data-stu-id="d1436-105">**Partitions**</span></span>  
 <span data-ttu-id="d1436-106">顯示包含支援選取之量值群組之資料分割清單的窗格。</span><span class="sxs-lookup"><span data-stu-id="d1436-106">Displays a grid containing the list of partitions that support the selected measure group.</span></span> <span data-ttu-id="d1436-107">方格包含下列資料行：</span><span class="sxs-lookup"><span data-stu-id="d1436-107">The grid contains the following columns:</span></span>  
  
 <span data-ttu-id="d1436-108">\*\* (序數) \*\*</span><span class="sxs-lookup"><span data-stu-id="d1436-108">**(Ordinal)**</span></span>  
 <span data-ttu-id="d1436-109">顯示在量值群組內資料分割的序數位置。</span><span class="sxs-lookup"><span data-stu-id="d1436-109">Displays the ordinal position of the partition within the measure group.</span></span>  
  
 <span data-ttu-id="d1436-110">按一下即可選取資料分割的整個資料列。</span><span class="sxs-lookup"><span data-stu-id="d1436-110">Click to select the entire row for the partition.</span></span>  
  
 <span data-ttu-id="d1436-111">**分割區名稱**</span><span class="sxs-lookup"><span data-stu-id="d1436-111">**Partition Name**</span></span>  
 <span data-ttu-id="d1436-112">鍵入選取之資料分割的名稱。</span><span class="sxs-lookup"><span data-stu-id="d1436-112">Type the name of the selected partition.</span></span>  
  
 <span data-ttu-id="d1436-113">**Source**</span><span class="sxs-lookup"><span data-stu-id="d1436-113">**Source**</span></span>  
 <span data-ttu-id="d1436-114">鍵入為選取之資料分割提供事實資料表資料的資料表名稱 (適用於資料表繫結) 或查詢 (適用於查詢繫結)。</span><span class="sxs-lookup"><span data-stu-id="d1436-114">Type the table name (for table binding) or query (for query binding) that provides the fact table data for the selected partition.</span></span>  
  
 <span data-ttu-id="d1436-115">按一下 [...]\*\*\*\* 按鈕即可顯示 [資料分割來源]\*\*\*\* 對話方塊，並為選取的資料分割定義來源。</span><span class="sxs-lookup"><span data-stu-id="d1436-115">Click the **...** button to display the **Partition Source** dialog box and define the source for the selected partition.</span></span>  
  
 <span data-ttu-id="d1436-116">**累積**</span><span class="sxs-lookup"><span data-stu-id="d1436-116">**Aggregation**</span></span>  
 <span data-ttu-id="d1436-117">顯示分割區的彙總模式和儲存模式。</span><span class="sxs-lookup"><span data-stu-id="d1436-117">Displays the aggregation mode and the storage mode of the partition.</span></span> <span data-ttu-id="d1436-118">先顯示儲存模式：關聯式線上分析處理 (ROLAP)、多維度線上分析處理 (MOLAP) 或混合式線上分析處理 (HOLAP)。</span><span class="sxs-lookup"><span data-stu-id="d1436-118">The storage mode is displayed first: relational online analytical processing (ROLAP), multidimensional online analytical processing (MOLAP), or hybrid online analytical processing (HOLAP).</span></span> <span data-ttu-id="d1436-119">彙總模式會顯示為要求最佳化的百分比、要求或使用之空間的量值、或建立的彙總數目。</span><span class="sxs-lookup"><span data-stu-id="d1436-119">The aggregation mode is displayed as a percentage of optimization requested, as a measure of space requested or used, or as the number of aggregations created.</span></span> <span data-ttu-id="d1436-120">按一下 [...]\*\*\*\* 按鈕即可顯示 [彙總設計精靈]\*\*\*\*，並為指定的資料分割定義彙總設計。</span><span class="sxs-lookup"><span data-stu-id="d1436-120">Click the **...** button to display the **Aggregation Design Wizard** and define the aggregation design for the specified partition.</span></span>  
  
 <span data-ttu-id="d1436-121">**說明**</span><span class="sxs-lookup"><span data-stu-id="d1436-121">**Description**</span></span>  
 <span data-ttu-id="d1436-122">鍵入分割區的選擇性描述。</span><span class="sxs-lookup"><span data-stu-id="d1436-122">Type the optional description of the partition.</span></span>  
  
 <span data-ttu-id="d1436-123">**新增資料分割...**</span><span class="sxs-lookup"><span data-stu-id="d1436-123">**New Partition...**</span></span>  
 <span data-ttu-id="d1436-124">按一下即可顯示 [資料分割精靈]\*\*\*\*，並在選取的量值群組中建立新的資料分割。</span><span class="sxs-lookup"><span data-stu-id="d1436-124">Click to display the **Partition Wizard** and create a new partition in the selected measure group.</span></span>  
  
 <span data-ttu-id="d1436-125">**儲存設定 .。。**</span><span class="sxs-lookup"><span data-stu-id="d1436-125">**Storage settings...**</span></span>  
 <span data-ttu-id="d1436-126">按一下即可顯示 [儲存設定]\*\*\*\* 對話方塊，並為選取的資料分割指定儲存模式、主動式快取和通知設定。</span><span class="sxs-lookup"><span data-stu-id="d1436-126">Click to display the **Storage Settings** dialog box and specify storage mode, proactive caching, and notification settings for the selected partition.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d1436-127">只有在選取之量值群組的 [資料分割]\*\*\*\* 方格中已選取資料分割的任何資料格時，才能啟用此選項。</span><span class="sxs-lookup"><span data-stu-id="d1436-127">This option is enabled only if any cell of a partition is selected in the **Partitions** grid of the selected measure group.</span></span>  
  
 <span data-ttu-id="d1436-128">**回寫設定 .。。**</span><span class="sxs-lookup"><span data-stu-id="d1436-128">**Writeback settings...**</span></span>  
 <span data-ttu-id="d1436-129">按一下即可顯示 [啟用/停用回寫]\*\*\*\* 對話方塊，並為選取的量值群組指定回寫設定。</span><span class="sxs-lookup"><span data-stu-id="d1436-129">Click to display the **Enable/Disable Writeback** dialog box and specify writeback settings for the selected measure group.</span></span>  
  
## <a name="context-menu"></a><span data-ttu-id="d1436-130">操作功能表</span><span class="sxs-lookup"><span data-stu-id="d1436-130">Context Menu</span></span>  
 <span data-ttu-id="d1436-131">在選取之量值群組的 [資料分割]\*\*\*\* 窗格中，以滑鼠右鍵按一下資料列，即可顯示提供下列選項的操作功能表：</span><span class="sxs-lookup"><span data-stu-id="d1436-131">The following options are available in the context menu displayed by right-clicking a row in the **Partitions** grid of a selected measure group:</span></span>  
  
|<span data-ttu-id="d1436-132">選項</span><span class="sxs-lookup"><span data-stu-id="d1436-132">Option</span></span>|<span data-ttu-id="d1436-133">定義</span><span class="sxs-lookup"><span data-stu-id="d1436-133">Definition</span></span>|  
|------------|----------------|  
|<span data-ttu-id="d1436-134">**加入商業智慧**</span><span class="sxs-lookup"><span data-stu-id="d1436-134">**Add Business Intelligence**</span></span>|<span data-ttu-id="d1436-135">按一下以顯示 **[商業智慧精靈]** ，並將商業智慧功能加入至 Cube。</span><span class="sxs-lookup"><span data-stu-id="d1436-135">Click to display the **Business Intelligence Wizard** and add business intelligence features to the cube.</span></span> <span data-ttu-id="d1436-136">如需 [商業智慧精靈]\*\*\*\* 的詳細資訊，請參閱[商業智慧精靈 F1 說明](business-intelligence-wizard-f1-help.md)。</span><span class="sxs-lookup"><span data-stu-id="d1436-136">For more information about the **Business Intelligence Wizard**, see [Business Intelligence Wizard F1 Help](business-intelligence-wizard-f1-help.md).</span></span>|  
|<span data-ttu-id="d1436-137">**新增分割區**</span><span class="sxs-lookup"><span data-stu-id="d1436-137">**New Partition**</span></span>|<span data-ttu-id="d1436-138">按一下即可顯示 [資料分割精靈]\*\*\*\*，並在選取的量值群組中建立新的資料分割。</span><span class="sxs-lookup"><span data-stu-id="d1436-138">Click to display the **Partition Wizard** and create a new partition in the selected measure group.</span></span>|  
|<span data-ttu-id="d1436-139">**重新命名分割區**</span><span class="sxs-lookup"><span data-stu-id="d1436-139">**Rename Partition**</span></span>|<span data-ttu-id="d1436-140">選取即可重新命名選取的分割區。</span><span class="sxs-lookup"><span data-stu-id="d1436-140">Select to rename the selected partition.</span></span>|  
|<span data-ttu-id="d1436-141">**刪除**</span><span class="sxs-lookup"><span data-stu-id="d1436-141">**Delete**</span></span>|<span data-ttu-id="d1436-142">按一下以顯示 [刪除物件]\*\*\*\* 對話方塊，然後刪除選取的動作。</span><span class="sxs-lookup"><span data-stu-id="d1436-142">Click to display the **Delete Objects** dialog box and delete the selected action.</span></span><br /><br /> <span data-ttu-id="d1436-143">注意：如果已選取回寫分割區，則會停用此選項。</span><span class="sxs-lookup"><span data-stu-id="d1436-143">Note: This option is disabled if a writeback partition is selected.</span></span>|  
|<span data-ttu-id="d1436-144">**設計彙總**</span><span class="sxs-lookup"><span data-stu-id="d1436-144">**Design Aggregations**</span></span>|<span data-ttu-id="d1436-145">按一下即可顯示 [彙總設計精靈]\*\*\*\*，並為選取的資料分割建立彙總設計。</span><span class="sxs-lookup"><span data-stu-id="d1436-145">Click to display the **Aggregation Design Wizard** and create an aggregation design for the selected partition.</span></span><br /><br /> <span data-ttu-id="d1436-146">注意：如果已選取回寫分割區，則會停用此選項。</span><span class="sxs-lookup"><span data-stu-id="d1436-146">Note: This option is disabled if a writeback partition is selected.</span></span>|  
|<span data-ttu-id="d1436-147">**儲存設定**</span><span class="sxs-lookup"><span data-stu-id="d1436-147">**Storage Settings**</span></span>|<span data-ttu-id="d1436-148">按一下即可顯示 [儲存設定]\*\*\*\* 對話方塊，並為選取的資料分割指定儲存模式、主動式快取和通知設定。</span><span class="sxs-lookup"><span data-stu-id="d1436-148">Click to display the **Storage Settings** dialog box and specify storage mode, proactive caching, and notification settings for the selected partition.</span></span>|  
|<span data-ttu-id="d1436-149">**回寫設定**</span><span class="sxs-lookup"><span data-stu-id="d1436-149">**Writeback Settings**</span></span>|<span data-ttu-id="d1436-150">按一下即可顯示 [啟用/停用回寫]\*\*\*\* 對話方塊，並為包含選取之資料分割的量值群組指定回寫設定。</span><span class="sxs-lookup"><span data-stu-id="d1436-150">Click to display the **Enable/Disable Writeback** dialog box and specify writeback settings for the measure group containing the selected partition.</span></span>|  
|<span data-ttu-id="d1436-151">**基於使用方式的最佳化**</span><span class="sxs-lookup"><span data-stu-id="d1436-151">**Usage Based Optimization**</span></span>|<span data-ttu-id="d1436-152">按一下即可顯示 [基於使用方式的最佳化精靈]\*\*\*\*，並根據現有的使用模式，為選取的資料分割建立彙總設計。</span><span class="sxs-lookup"><span data-stu-id="d1436-152">Click to display the **Usage-Based Optimization Wizard** and create an aggregation design based on existing usage patterns for the selected partition.</span></span><br /><br /> <span data-ttu-id="d1436-153">注意：如果已選取回寫分割區，則會停用此選項。</span><span class="sxs-lookup"><span data-stu-id="d1436-153">Note: This option is disabled if a writeback partition is selected.</span></span>|  
|<span data-ttu-id="d1436-154">**處理程序**</span><span class="sxs-lookup"><span data-stu-id="d1436-154">**Process**</span></span>|<span data-ttu-id="d1436-155">按一下即可顯示 [處理]\*\*\*\* 對話方塊，並處理選取的資料分割。</span><span class="sxs-lookup"><span data-stu-id="d1436-155">Click to display the **Process** dialog box and process the selected partition.</span></span>|  
|<span data-ttu-id="d1436-156">**複製**</span><span class="sxs-lookup"><span data-stu-id="d1436-156">**Copy**</span></span>|<span data-ttu-id="d1436-157">已停用此選項。</span><span class="sxs-lookup"><span data-stu-id="d1436-157">This option is disabled.</span></span>|  
|<span data-ttu-id="d1436-158">**貼上**</span><span class="sxs-lookup"><span data-stu-id="d1436-158">**Paste**</span></span>|<span data-ttu-id="d1436-159">已停用此選項。</span><span class="sxs-lookup"><span data-stu-id="d1436-159">This option is disabled.</span></span>|  
|<span data-ttu-id="d1436-160">**屬性**</span><span class="sxs-lookup"><span data-stu-id="d1436-160">**Properties**</span></span>|<span data-ttu-id="d1436-161">選取即可在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 中，顯示選取之資料分割的 [屬性]\*\*\*\* 視窗。</span><span class="sxs-lookup"><span data-stu-id="d1436-161">Select to display the **Properties** window in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] for the selected partition.</span></span>|  
  
  
