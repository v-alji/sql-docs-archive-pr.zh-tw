---
title: 重新標記 (SQL Server 資料採礦增益集) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data preparation
- relabel
- data cleaning
ms.assetid: af041b39-fdd1-4cb5-a5ef-2f3ddab84614
author: minewiskan
ms.author: owend
ms.openlocfilehash: a625676f60e2da32e19b85a94002b51eeb9ac816
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596292"
---
# <a name="relabel-sql-server-data-mining-add-ins"></a><span data-ttu-id="a9bd1-102">重定標籤 (SQL Server 資料採礦增益集)</span><span class="sxs-lookup"><span data-stu-id="a9bd1-102">Relabel (SQL Server Data Mining Add-ins)</span></span>
  <span data-ttu-id="a9bd1-103">![[重定標籤] 工具的 Office 13 圖示](media/dm13-relabel.gif "[重定標籤] 工具的 Office 13 圖示")</span><span class="sxs-lookup"><span data-stu-id="a9bd1-103">![Office 13 icon for Relabel tool](media/dm13-relabel.gif "Office 13 icon for Relabel tool")</span></span>

 <span data-ttu-id="a9bd1-104">適用於 Excel 的資料採礦用戶端可協助您建立資料的新標籤，讓分析結果更容易理解。</span><span class="sxs-lookup"><span data-stu-id="a9bd1-104">The Data Mining Client for Excel helps you create new labels for data to make it easier to understand the results of analysis.</span></span>

 <span data-ttu-id="a9bd1-105">重定標籤的原因包括：</span><span class="sxs-lookup"><span data-stu-id="a9bd1-105">Reasons for relabeling include:</span></span>

-   <span data-ttu-id="a9bd1-106">資料包含的結果經過編碼，例如 1 代表男性，2 代表女性。</span><span class="sxs-lookup"><span data-stu-id="a9bd1-106">The data includes results that were coded, such as 1 for Male and 2 for Female.</span></span>

-   <span data-ttu-id="a9bd1-107">您要建立數值的值區，並且想要為範圍指定描述性名稱。</span><span class="sxs-lookup"><span data-stu-id="a9bd1-107">You are bucketing numeric values and want to give the ranges a descriptive name.</span></span>

-   <span data-ttu-id="a9bd1-108">您想要簡化完整名稱。</span><span class="sxs-lookup"><span data-stu-id="a9bd1-108">You want to simplify long names.</span></span>

## <a name="using-the-relabel-wizard"></a><span data-ttu-id="a9bd1-109">使用重定標籤精靈</span><span class="sxs-lookup"><span data-stu-id="a9bd1-109">Using the Relabel Wizard</span></span>

1.  <span data-ttu-id="a9bd1-110">在 [**資料採礦**] 功能區中，按一下 [**清除**]，然後選取 [**重新標籤**]。</span><span class="sxs-lookup"><span data-stu-id="a9bd1-110">In the **Data Mining** ribbon, click **Clean** and then select **Re-Label**.</span></span>

2.  <span data-ttu-id="a9bd1-111">選取含有您要修正之資料的資料表或資料範圍。</span><span class="sxs-lookup"><span data-stu-id="a9bd1-111">Select the table or data range that has the data you want to fix.</span></span>

3.  <span data-ttu-id="a9bd1-112">在嚮導的 [**重新標籤**] 頁面中，從下拉式清單中選擇資料行，或按一下 [**資料範例**] 窗格中的資料行，以選取單一資料行。</span><span class="sxs-lookup"><span data-stu-id="a9bd1-112">In the **Re-label** page of the wizard, select a single column, either by choosing the column from the dropdown list, or by clicking the column in the **Data samples** pane.</span></span>

     <span data-ttu-id="a9bd1-113">[**資料範例**] 窗格只會顯示大約50個數據列，但會進行取樣，以確保您看到值的良好散佈。</span><span class="sxs-lookup"><span data-stu-id="a9bd1-113">The **Data samples** pane only shows about 50 rows of data, but they are sampled to ensure that you see a good spread of values.</span></span>

     <span data-ttu-id="a9bd1-114">按一下 [**計數**] 的資料行標題，依每個值的計數排序。</span><span class="sxs-lookup"><span data-stu-id="a9bd1-114">Click the column header for **Count** to sort by the count of each value.</span></span>

     <span data-ttu-id="a9bd1-115">您也可以依**原始卷**標排序，如果您想要先重新標示所有最高或最低值，這會很方便。</span><span class="sxs-lookup"><span data-stu-id="a9bd1-115">You can also sort by **Original Labels**, which is handy if you want to re-label all the highest or lowest values first.</span></span>

4.  <span data-ttu-id="a9bd1-116">在嚮導的 [**重新標籤**資料] 頁面中，檢查 [**原始標籤**] 欄中的值，並決定您要將它們分組或編輯的方式。</span><span class="sxs-lookup"><span data-stu-id="a9bd1-116">In the **Re-label** data page of the wizard, review the values in the **Original Labels** column, and decide how you want to group or edit them.</span></span>

5.  <span data-ttu-id="a9bd1-117">在 [**新標籤**] 底下的資料列中輸入新的值。</span><span class="sxs-lookup"><span data-stu-id="a9bd1-117">Type a new value into the row under **New Labels**.</span></span> <span data-ttu-id="a9bd1-118">您可以從現有值的清單中選取某個值。</span><span class="sxs-lookup"><span data-stu-id="a9bd1-118">You can also choose a value from the list of existing values.</span></span> <span data-ttu-id="a9bd1-119">輸入新的值時，它們會立即成為可供重複使用。</span><span class="sxs-lookup"><span data-stu-id="a9bd1-119">As you type new values, they become available for re-use right away.</span></span>

6.  <span data-ttu-id="a9bd1-120">當您輸入足夠的資料列時，請按 **[下一步]**，然後在 [**選取目的地**] 頁面上，選擇您要儲存重新標示資料的位置。</span><span class="sxs-lookup"><span data-stu-id="a9bd1-120">When you have entered enough rows, click **Next**, and on the **Select Destination** page, choose where you'll save the relabeled data.</span></span>

    -   <span data-ttu-id="a9bd1-121">**加入目前工作表中成為新資料行**</span><span class="sxs-lookup"><span data-stu-id="a9bd1-121">**Add as a new column to the current worksheet**</span></span>

         <span data-ttu-id="a9bd1-122">按一下即可將新資料行加入包含新值的資料表。</span><span class="sxs-lookup"><span data-stu-id="a9bd1-122">Click to add a new column to the table that contains the new values.</span></span>

    -   <span data-ttu-id="a9bd1-123">**將包含變更的工作表資料複製到新工作表**</span><span class="sxs-lookup"><span data-stu-id="a9bd1-123">**Copy sheet data with changes to a new worksheet**</span></span>

         <span data-ttu-id="a9bd1-124">按一下即可建立包含更新資料的新工作表。</span><span class="sxs-lookup"><span data-stu-id="a9bd1-124">Click to create a new worksheet that contains the updated data.</span></span>

    -   <span data-ttu-id="a9bd1-125">**就地變更資料**</span><span class="sxs-lookup"><span data-stu-id="a9bd1-125">**Change data in place**</span></span>

         <span data-ttu-id="a9bd1-126">按一下即可將原始資料取代成新值。</span><span class="sxs-lookup"><span data-stu-id="a9bd1-126">Click to replace the original data with the new values.</span></span>

## <a name="see-also"></a><span data-ttu-id="a9bd1-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a9bd1-127">See Also</span></span>
 [<span data-ttu-id="a9bd1-128">瀏覽和清除資料</span><span class="sxs-lookup"><span data-stu-id="a9bd1-128">Exploring and Cleaning Data</span></span>](exploring-and-cleaning-data.md)


