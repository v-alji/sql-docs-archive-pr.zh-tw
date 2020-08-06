---
title: 偵測適用于 Excel) 的資料表分析工具分類 (|Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Table Analysis tools
- clustering [data mining]
- mining model, decision tree
- category detection
ms.assetid: 3c7e9ebb-d0c9-498e-a9ba-cc13eaa43520
author: minewiskan
ms.author: owend
ms.openlocfilehash: 4874c85d7e4ab65716741e8ae9433406dfb08b74
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705697"
---
# <a name="detect-categories-table-analysis-tools-for-excel"></a><span data-ttu-id="7adc1-102">偵測類別目錄 (適用於 Excel 的資料表分析工具)</span><span class="sxs-lookup"><span data-stu-id="7adc1-102">Detect Categories (Table Analysis Tools for Excel)</span></span>
  <span data-ttu-id="7adc1-103">![功能區中的偵測類別目錄按鈕](media/tat-detectcat.gif "功能區中的偵測類別目錄按鈕")</span><span class="sxs-lookup"><span data-stu-id="7adc1-103">![Detect Categories button in ribbon](media/tat-detectcat.gif "Detect Categories button in ribbon")</span></span>

 <span data-ttu-id="7adc1-104">[偵測**類別目錄**] 工具會自動尋找資料表中具有類似特性的資料列。</span><span class="sxs-lookup"><span data-stu-id="7adc1-104">The **Detect Categories** tool automatically finds rows in a table that have similar characteristics.</span></span>

 <span data-ttu-id="7adc1-105">當工具完成時，它會建立報表，其中列出找到的類別目錄及其區別特性。</span><span class="sxs-lookup"><span data-stu-id="7adc1-105">When the tool finishes, it creates a report that lists the categories it found, together with their distinguishing characteristics.</span></span> <span data-ttu-id="7adc1-106">根據預設，它會將新的資料行加入每一個資料列都包含建議類別目錄的資料表。</span><span class="sxs-lookup"><span data-stu-id="7adc1-106">By default, it adds a new column to the data table that contains the proposed category for each row of your data.</span></span> <span data-ttu-id="7adc1-107">然後，您就可以檢閱類別目錄並將它們重新命名。</span><span class="sxs-lookup"><span data-stu-id="7adc1-107">You can then review the categories and rename them.</span></span>

## <a name="using-the-detect-categories-tool"></a><span data-ttu-id="7adc1-108">使用偵測類別目錄工具</span><span class="sxs-lookup"><span data-stu-id="7adc1-108">Using the Detect Categories Tool</span></span>

1.  <span data-ttu-id="7adc1-109">開啟 Excel 資料表。</span><span class="sxs-lookup"><span data-stu-id="7adc1-109">Open an Excel table.</span></span>

2.  <span data-ttu-id="7adc1-110">按一下 [偵測**類別**]。</span><span class="sxs-lookup"><span data-stu-id="7adc1-110">Click **Detect Categories**.</span></span>

3.  <span data-ttu-id="7adc1-111">指定要用於分析的資料行。</span><span class="sxs-lookup"><span data-stu-id="7adc1-111">Specify the columns to use in analysis.</span></span> <span data-ttu-id="7adc1-112">您可以取消選取有相異值的資料行，例如個人名稱或記錄識別碼，因為這些資料行對分析可能沒有協助。</span><span class="sxs-lookup"><span data-stu-id="7adc1-112">You can deselect columns that have distinct values, such as personal names or record IDs, because these columns might not be useful for analysis.</span></span>

4.  <span data-ttu-id="7adc1-113">選擇性地指定要建立的最大類別目錄數目。</span><span class="sxs-lookup"><span data-stu-id="7adc1-113">Optionally, specify the maximum number of categories to create.</span></span> <span data-ttu-id="7adc1-114">根據預設，此工具找到多少類別目錄，就會自動建立一樣多的類別目錄。</span><span class="sxs-lookup"><span data-stu-id="7adc1-114">By default, the tool automatically creates as many categories as it finds.</span></span>

5.  <span data-ttu-id="7adc1-115">按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="7adc1-115">Click **Run**.</span></span>

6.  <span data-ttu-id="7adc1-116">工具會建立名為「類別目錄報表」的新工作表，其中包含類別目錄清單及其特性。</span><span class="sxs-lookup"><span data-stu-id="7adc1-116">The tool creates a new worksheet, named Categories Report, which contains the list of categories and their characteristics.</span></span>

 <span data-ttu-id="7adc1-117">如需如何指定工具選項的詳細資訊，請參閱[ (適用于 Excel 的資料表分析工具) ](detect-categories-table-analysis-tools-for-excel.md)的 [偵測類別目錄] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="7adc1-117">For more information about how to specify options for the tool, see [Detect Categories Dialog Box (Table Analysis Tools for Excel)](detect-categories-table-analysis-tools-for-excel.md).</span></span>

## <a name="understanding-the-categories-report"></a><span data-ttu-id="7adc1-118">了解類別目錄報表</span><span class="sxs-lookup"><span data-stu-id="7adc1-118">Understanding the Categories Report</span></span>
 <span data-ttu-id="7adc1-119">[**類別目錄] 報表**包含兩個數據表、**類別目錄清單**和**類別目錄特性**，以及**類別設定檔**圖表。</span><span class="sxs-lookup"><span data-stu-id="7adc1-119">The **Categories Report** contains two tables, **Category List** and **Category Characteristics**, and a **Category Profiles** chart.</span></span>

### <a name="category-list"></a><span data-ttu-id="7adc1-120">類別目錄清單</span><span class="sxs-lookup"><span data-stu-id="7adc1-120">Category List</span></span>
 <span data-ttu-id="7adc1-121">第一個資料表列出找到的類別目錄。</span><span class="sxs-lookup"><span data-stu-id="7adc1-121">The first table lists the categories that were found.</span></span> <span data-ttu-id="7adc1-122">[資料列**計數**] 資料行會指出已指派給每個類別目錄的資料列數目。</span><span class="sxs-lookup"><span data-stu-id="7adc1-122">The **Row Count** column indicates how many rows of data were assigned to each category.</span></span>

 <span data-ttu-id="7adc1-123">模型會為每個類別目錄建立暫時名稱，但您可以視需要重新命名類別目錄。</span><span class="sxs-lookup"><span data-stu-id="7adc1-123">The model creates temporary names for each category, but you can rename the categories as you like.</span></span> <span data-ttu-id="7adc1-124">例如，在下列範例中，第一個類別目錄已重新命名為「**低收入**」，因為這是叢集的最上層屬性。</span><span class="sxs-lookup"><span data-stu-id="7adc1-124">For example, in the following example, the first category has been renamed **Low Income**, because that was the top attribute of the cluster.</span></span>

 <span data-ttu-id="7adc1-125">![偵測類別目錄工具建立的報表](media/dm13-tat-detectcat-report1.gif "偵測類別目錄工具建立的報表")</span><span class="sxs-lookup"><span data-stu-id="7adc1-125">![report created by Detect Categories tool](media/dm13-tat-detectcat-report1.gif "report created by Detect Categories tool")</span></span>

 <span data-ttu-id="7adc1-126">一旦您輸入新標籤，變更就會傳播至所有其他圖表以及加入來源資料工作表中的類別目錄清單。</span><span class="sxs-lookup"><span data-stu-id="7adc1-126">As soon as you type the new label, the change is propagated to all the other charts as well as to the category list added in the source data worksheet.</span></span>

### <a name="category-characteristics"></a><span data-ttu-id="7adc1-127">類別目錄特性</span><span class="sxs-lookup"><span data-stu-id="7adc1-127">Category Characteristics</span></span>
 <span data-ttu-id="7adc1-128">第二個數據表 [**類別目錄特性**] 會顯示每個類別目錄的相關詳細資料。</span><span class="sxs-lookup"><span data-stu-id="7adc1-128">The second table, **Category Characteristics**, shows details about the makeup of each category.</span></span> <span data-ttu-id="7adc1-129">按一下 [**類別目錄**] 欄頂端的 [**篩選**] 按鈕，以查看焦點在一個或少數幾個類別。</span><span class="sxs-lookup"><span data-stu-id="7adc1-129">Click the **Filter** button at the top of the **Category** column to see focus on one or just a few categories.</span></span>

 <span data-ttu-id="7adc1-130">![偵測類別目錄工具建立的報表](media/dm13-tat-detectcat-report2.gif "偵測類別目錄工具建立的報表")</span><span class="sxs-lookup"><span data-stu-id="7adc1-130">![report created by Detect Categories tool](media/dm13-tat-detectcat-report2.gif "report created by Detect Categories tool")</span></span>

 <span data-ttu-id="7adc1-131">[**相對重要性**] 資料行中的陰影表示屬性和值的組合為區別因數的重要性。</span><span class="sxs-lookup"><span data-stu-id="7adc1-131">The shading in the column, **Relative Importance**, indicates how important that combination of attribute and value is as a distinguishing factor.</span></span> <span data-ttu-id="7adc1-132">垂直線越長，此屬性代表此類別目錄的可能性就越高。</span><span class="sxs-lookup"><span data-stu-id="7adc1-132">The longer the bar, the more likely it is that this attribute is strongly representative of this category.</span></span>

### <a name="categories-profile-chart"></a><span data-ttu-id="7adc1-133">類別目錄設定檔圖表</span><span class="sxs-lookup"><span data-stu-id="7adc1-133">Categories Profile Chart</span></span>
 <span data-ttu-id="7adc1-134">[**類別目錄報表**] 工作表中的最後一個圖表 [**類別目錄設定檔**] 是互動式的**資料透視**表，您可以用來重新排列和隱藏欄位、篩選值，以及自訂圖表的外觀。</span><span class="sxs-lookup"><span data-stu-id="7adc1-134">The final chart in the **Categories Report** worksheet, **Category Profiles**, is an interactive **Pivot Chart** that you can use to rearrange and hide fields, filter on values, and customize the chart's appearance.</span></span>

 <span data-ttu-id="7adc1-135">Excel 2013 現在可直接在設計介面中提供**圖表樣式**和**圖表**專案控制項，讓您可以輕鬆地改善圖表設計。</span><span class="sxs-lookup"><span data-stu-id="7adc1-135">Excel 2013 now provides **Chart Styles** and **Chart Elements** controls right in the design surface that make it easy to improve the chart design.</span></span>

 <span data-ttu-id="7adc1-136">![偵測類別目錄工具建立的報表](media/dm13-tat-detectcat-report3.gif "偵測類別目錄工具建立的報表")</span><span class="sxs-lookup"><span data-stu-id="7adc1-136">![report created by Detect Categories tool](media/dm13-tat-detectcat-report3.gif "report created by Detect Categories tool")</span></span>

## <a name="requirements"></a><span data-ttu-id="7adc1-137">需求</span><span class="sxs-lookup"><span data-stu-id="7adc1-137">Requirements</span></span>
 <span data-ttu-id="7adc1-138">[偵測**類別目錄**] 工具沒有資料量或類型的需求。</span><span class="sxs-lookup"><span data-stu-id="7adc1-138">The **Detect Categories** tool has no requirements for the amount or type of data.</span></span>

> [!NOTE]
>  <span data-ttu-id="7adc1-139">當您使用 [偵測**類別目錄**] 工具時，它會在原始資料表中建立新的資料行 [類別]。</span><span class="sxs-lookup"><span data-stu-id="7adc1-139">When you use the **Detect Categories** tool, it creates a new column, Category, in the original data table.</span></span> <span data-ttu-id="7adc1-140">如果您將這個資料行保留在資料表中，接著執行後續的資料採礦作業，這個資料行的存在可能會影響結果。</span><span class="sxs-lookup"><span data-stu-id="7adc1-140">If you leave this column in the data table and then perform subsequent data mining operations, the presence of this column could influence your results.</span></span> <span data-ttu-id="7adc1-141">為了確保不影響其他作業，在使用其他資料採礦工具之前，您應該複製不含類別目錄資料行的資料表。</span><span class="sxs-lookup"><span data-stu-id="7adc1-141">To ensure that this does not affect other operations, you should make a copy of the data table without the Category column before using other data mining tools.</span></span>

## <a name="related-tools"></a><span data-ttu-id="7adc1-142">相關工具</span><span class="sxs-lookup"><span data-stu-id="7adc1-142">Related Tools</span></span>
 <span data-ttu-id="7adc1-143">當 [偵測**類別目錄**] 工具分析您的資料時，它會使用群集演算法建立資料採礦結構和資料採礦模型 [!INCLUDE[msCoName](../includes/msconame-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="7adc1-143">When the **Detect Categories** tool analyzes your data, it creates a data mining structure and data mining model by using the [!INCLUDE[msCoName](../includes/msconame-md.md)] Clustering algorithm.</span></span>

 <span data-ttu-id="7adc1-144">當您使用 [**分析關鍵影響**因數] 工具建立資料採礦模型之後，您可以使用適用于 Excel 的資料採礦用戶端流覽模型，並更詳細地探索關聯性。</span><span class="sxs-lookup"><span data-stu-id="7adc1-144">After you have created a data mining model by using the **Analyze Key Influencers** tool, you can use the Data Mining Client for Excel to browse the model and explore relationships in more detail.</span></span> <span data-ttu-id="7adc1-145">適用於 Excel 的資料採礦用戶端是獨立的增益集，提供更多進階資料採礦功能。</span><span class="sxs-lookup"><span data-stu-id="7adc1-145">The Data Mining Client for Excel is a separate add-in that provides more advanced data mining functionality.</span></span> <span data-ttu-id="7adc1-146">如需詳細資訊，請參閱[在 Excel 中流覽模型 &#40;SQL Server 資料採礦增益集&#41;](browsing-models-in-excel-sql-server-data-mining-add-ins.md)。</span><span class="sxs-lookup"><span data-stu-id="7adc1-146">For information, see [Browsing Models in Excel &#40;SQL Server Data Mining Add-ins&#41;](browsing-models-in-excel-sql-server-data-mining-add-ins.md).</span></span>

 <span data-ttu-id="7adc1-147">如需在適用于 Excel 的資料採礦用戶端中使用資料模型化功能的詳細資訊，請參閱[建立資料採礦模型](creating-a-data-mining-model.md)。</span><span class="sxs-lookup"><span data-stu-id="7adc1-147">For more information about using the data modeling capabilities in the Data Mining Client for Excel, see [Creating a Data Mining Model](creating-a-data-mining-model.md).</span></span>

 <span data-ttu-id="7adc1-148">如需 [偵測**類別目錄**] 工具所使用之演算法的詳細資訊，請參閱《線上叢書》中的「Microsoft 群集演算法」主題 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="7adc1-148">For more information about the algorithm used by the **Detect Categories** tool, see the topic "Microsoft Clustering Algorithm" in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Books Online.</span></span>

## <a name="see-also"></a><span data-ttu-id="7adc1-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7adc1-149">See Also</span></span>
 [<span data-ttu-id="7adc1-150">適用於 Excel 的資料表分析工具</span><span class="sxs-lookup"><span data-stu-id="7adc1-150">Table Analysis Tools for Excel</span></span>](table-analysis-tools-for-excel.md)


