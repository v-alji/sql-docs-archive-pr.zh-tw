---
title: 流覽資料 (SQL Server 資料採礦增益集) |Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data preparation
- histogram [data mining]
- data visualization
ms.assetid: 714845a9-4c27-461a-9ba3-149e1e818386
author: minewiskan
ms.author: owend
ms.openlocfilehash: 2572c11e92dcf99dfa3adf661603e8f65f05116e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703390"
---
# <a name="explore-data-sql-server-data-mining-add-ins"></a><span data-ttu-id="92f10-102">瀏覽資料 (SQL Server 資料採礦增益集)</span><span class="sxs-lookup"><span data-stu-id="92f10-102">Explore Data (SQL Server Data Mining Add-ins)</span></span>
  <span data-ttu-id="92f10-103">![瀏覽資料精靈](media/dmc-explore.gif "瀏覽資料精靈")</span><span class="sxs-lookup"><span data-stu-id="92f10-103">![Explore Data wizard](media/dmc-explore.gif "Explore Data wizard")</span></span>  
  
 <span data-ttu-id="92f10-104">[**流覽資料**] wizard 可協助您瞭解資料表中的資料類型和數量。</span><span class="sxs-lookup"><span data-stu-id="92f10-104">The **Explore Data** wizard helps you understand the type and amount of data in your data table.</span></span> <span data-ttu-id="92f10-105">此精靈會一次繪製一個選定資料行的分佈和值。</span><span class="sxs-lookup"><span data-stu-id="92f10-105">The wizard graphs the distribution and values for the selected columns, one column at a time.</span></span> <span data-ttu-id="92f10-106">然後，您可以試驗變更資料的分組方式，或是將顯示內容的圖表複製到 Excel 活頁簿進行檢閱。</span><span class="sxs-lookup"><span data-stu-id="92f10-106">You can then experiment with changing the way that data is grouped, or copy the chart that shows the content to an Excel workbook for review.</span></span>  
  
 <span data-ttu-id="92f10-107">如果您的資料包含連續數值資料，您可以在下列兩種檢視之間切換：</span><span class="sxs-lookup"><span data-stu-id="92f10-107">If your data contains continuous numeric data, you can toggle between these two views:</span></span>  
  
-   <span data-ttu-id="92f10-108">**折線圖。**</span><span class="sxs-lookup"><span data-stu-id="92f10-108">**Line graph.**</span></span> <span data-ttu-id="92f10-109">這種圖表會在 X 軸繪製資料值，在 Y 軸繪製案例數目。</span><span class="sxs-lookup"><span data-stu-id="92f10-109">This graph charts the data values on the X-axis and the number of cases on the y-axis.</span></span>  
  
-   <span data-ttu-id="92f10-110">**橫條圖。**</span><span class="sxs-lookup"><span data-stu-id="92f10-110">**Bar chart.**</span></span> <span data-ttu-id="92f10-111">這種圖形會依每個值的案例數目來分組值。</span><span class="sxs-lookup"><span data-stu-id="92f10-111">This graph groups values by the number of cases for each value.</span></span>  
  
 <span data-ttu-id="92f10-112">當精靈尋找資料的群組時，它會使用資料值的實際分佈。</span><span class="sxs-lookup"><span data-stu-id="92f10-112">When the wizard finds groups in the data, it uses the actual distribution of data values.</span></span> <span data-ttu-id="92f10-113">因此，橫條圖不會顯示常見的整數值座標軸標記 (例如 10 或 100)。</span><span class="sxs-lookup"><span data-stu-id="92f10-113">Therefore, the bar chart does not show typical whole-number numeric axis markers such as 10 or 100.</span></span> <span data-ttu-id="92f10-114">而是，橫條圖中顯示的範圍可能比較類似於 43521-55603 ([收入] 資料行)。</span><span class="sxs-lookup"><span data-stu-id="92f10-114">Instead, the ranges shown in the bar chart might be something like 43521-55603 (for the Income column).</span></span>  
  
 <span data-ttu-id="92f10-115">如果您要將資料分組成其他範圍，就應該先在 Excel 中進行這項處理，然後再分析資料。</span><span class="sxs-lookup"><span data-stu-id="92f10-115">If you want to group your data into other ranges, you should do this in Excel before analyzing the data.</span></span> <span data-ttu-id="92f10-116">或者，您可以使用重新[標記](relabel-sql-server-data-mining-add-ins.md)的 wizard 來重新標示資料。</span><span class="sxs-lookup"><span data-stu-id="92f10-116">Or, you can relabel the data by using the [Relabel](relabel-sql-server-data-mining-add-ins.md) wizard.</span></span>  
  
## <a name="using-the-explore-data-wizard"></a><span data-ttu-id="92f10-117">使用瀏覽資料精靈</span><span class="sxs-lookup"><span data-stu-id="92f10-117">Using the Explore Data Wizard</span></span>  
  
1.  <span data-ttu-id="92f10-118">在 [**資料採礦**] 功能區中，按一下 [**流覽資料**]。</span><span class="sxs-lookup"><span data-stu-id="92f10-118">In the **Data Mining** ribbon, click **Explore Data**.</span></span>  
  
2.  <span data-ttu-id="92f10-119">在 [**選取來源**] 對話方塊中，選取包含您資料的資料表或儲存格範圍。</span><span class="sxs-lookup"><span data-stu-id="92f10-119">In the **Select Source** dialog box, select the table or range of cells that contains your data.</span></span>  
  
3.  <span data-ttu-id="92f10-120">在 [**選取資料行**] 對話方塊中，從窗格中顯示的範例資料中，選擇要分析的資料行。</span><span class="sxs-lookup"><span data-stu-id="92f10-120">In the **Select Column** dialog box, choose the column to analyze, from the sample data displayed in the pane.</span></span>  
  
4.  <span data-ttu-id="92f10-121">在 [**流覽資料**] 對話方塊中，選擇用於顯示資料分佈的圖表類型。</span><span class="sxs-lookup"><span data-stu-id="92f10-121">In the **Explore Data** dialog box, choose the chart types for displaying the distribution of data.</span></span>  
  
5.  <span data-ttu-id="92f10-122">您可以選擇將新資料行加入資料、變更資料分割的方式，或是將圖表複製到 Excel。</span><span class="sxs-lookup"><span data-stu-id="92f10-122">Optionally, you can add new columns to the data, change the way that the data is segmented, or copy the chart to Excel.</span></span>  
  
### <a name="requirements"></a><span data-ttu-id="92f10-123">需求</span><span class="sxs-lookup"><span data-stu-id="92f10-123">Requirements</span></span>  
 <span data-ttu-id="92f10-124">若要使用 [**流覽資料**] wizard，您的資料必須在 Excel 資料表中。</span><span class="sxs-lookup"><span data-stu-id="92f10-124">To use the **Explore Data** wizard, your data must be in an Excel data table.</span></span>   
  
## <a name="see-also"></a><span data-ttu-id="92f10-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="92f10-125">See Also</span></span>  
 [<span data-ttu-id="92f10-126">資料採礦準備檢查清單</span><span class="sxs-lookup"><span data-stu-id="92f10-126">Checklist of Preparation for Data Mining</span></span>](checklist-of-preparation-for-data-mining.md)  
  
  
