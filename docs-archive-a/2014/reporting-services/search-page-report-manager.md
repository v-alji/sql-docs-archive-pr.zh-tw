---
title: 搜尋頁面 (報表管理員) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 51ffdc07-e1b9-4ed7-acb3-dd98d7cce273
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 2528133f5b2ecc4bed4c16fdd476591b3bab52d2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596490"
---
# <a name="search-page-report-manager"></a><span data-ttu-id="04a73-102">搜尋頁面 (報表管理員)</span><span class="sxs-lookup"><span data-stu-id="04a73-102">Search Page (Report Manager)</span></span>
  <span data-ttu-id="04a73-103">使用 [搜尋結果] 頁面可以檢視為報表、連結報表、報表模型、共用資料來源、資料夾或資源指定之搜尋作業的結果。</span><span class="sxs-lookup"><span data-stu-id="04a73-103">Use the Search Results page to view the results of a search operation specified for a report, linked report, report model, shared data source, folder, or resource.</span></span> <span data-ttu-id="04a73-104">搜尋結果會依字母順序列出。</span><span class="sxs-lookup"><span data-stu-id="04a73-104">Search results are listed alphabetically.</span></span> <span data-ttu-id="04a73-105">您可以依類型、名稱或描述來排序。</span><span class="sxs-lookup"><span data-stu-id="04a73-105">You can sort by type, name, or description.</span></span>  
  
 <span data-ttu-id="04a73-106">下列項目會從搜尋作業排除：報表記錄所包含的報表快照集、訂閱和共用排程。</span><span class="sxs-lookup"><span data-stu-id="04a73-106">The following items are excluded from a search operation: report snapshots contained in report history, subscriptions, and shared schedules.</span></span> <span data-ttu-id="04a73-107">同樣地，在沒有檢視資料夾或報表的足夠權限時，就會從搜尋中排除該項目。</span><span class="sxs-lookup"><span data-stu-id="04a73-107">Similarly, insufficient permission to view a folder or report excludes that item from a search.</span></span>  
  
 <span data-ttu-id="04a73-108">您無法搜尋報表或模型中的文字。</span><span class="sxs-lookup"><span data-stu-id="04a73-108">You cannot search for text within a report or model.</span></span> <span data-ttu-id="04a73-109">若要搜尋報表中的特定文字，請使用報表上方的工具列。</span><span class="sxs-lookup"><span data-stu-id="04a73-109">To search for specific text within a report, use the toolbar at the top of the report.</span></span>  
  
## <a name="navigation"></a><span data-ttu-id="04a73-110">導覽</span><span class="sxs-lookup"><span data-stu-id="04a73-110">Navigation</span></span>  
 <span data-ttu-id="04a73-111">您可以使用下列程序，在使用者介面 (UI) 中導覽至這個位置。</span><span class="sxs-lookup"><span data-stu-id="04a73-111">Use the following procedure to navigate to this location in the user interface (UI).</span></span>  
  
###### <a name="to-open-the-search-results-page"></a><span data-ttu-id="04a73-112">若要開啟搜尋結果頁面</span><span class="sxs-lookup"><span data-stu-id="04a73-112">To open the Search Results page</span></span>  
  
1.  <span data-ttu-id="04a73-113">開啟報表管理員。</span><span class="sxs-lookup"><span data-stu-id="04a73-113">Open Report Manager.</span></span>  
  
2.  <span data-ttu-id="04a73-114">在頁面的頂端，於 **[搜尋]** 方塊中輸入您的搜尋準則。</span><span class="sxs-lookup"><span data-stu-id="04a73-114">At the top of the page, type your search criteria in the **Search** box.</span></span> <span data-ttu-id="04a73-115">然後，按 Enter 鍵，或按一下搜尋箭頭。</span><span class="sxs-lookup"><span data-stu-id="04a73-115">Then press Enter or click the Search arrow.</span></span>  
  
## <a name="options"></a><span data-ttu-id="04a73-116">選項</span><span class="sxs-lookup"><span data-stu-id="04a73-116">Options</span></span>  
 <span data-ttu-id="04a73-117">**刪除**</span><span class="sxs-lookup"><span data-stu-id="04a73-117">**Delete**</span></span>  
 <span data-ttu-id="04a73-118">按一下即可從報表伺服器資料庫中移除項目。</span><span class="sxs-lookup"><span data-stu-id="04a73-118">Click to remove an item from a report server database.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="04a73-119">這個按鈕只有 **[詳細資料檢視]** 才有提供。</span><span class="sxs-lookup"><span data-stu-id="04a73-119">This button is available only in **Details View**.</span></span> <span data-ttu-id="04a73-120">不過，您可以將滑鼠停留在某個項目上，然後使用功能表來存取 **[詳細資料檢視]** 或 **[清單檢視]** 中的刪除功能。</span><span class="sxs-lookup"><span data-stu-id="04a73-120">However, you can hover over an item and use the menu to access the delete functionality in either **Details View** or in **List View**.</span></span>  
  
 <span data-ttu-id="04a73-121">**移動**</span><span class="sxs-lookup"><span data-stu-id="04a73-121">**Move**</span></span>  
 <span data-ttu-id="04a73-122">按一下即可重新定位項目。</span><span class="sxs-lookup"><span data-stu-id="04a73-122">Click to relocate an item.</span></span> <span data-ttu-id="04a73-123">這樣做會開啟 [移動項目] 頁面，如此您就可以在其中選取不同的資料夾位置。</span><span class="sxs-lookup"><span data-stu-id="04a73-123">This opens the Move Items page, where you can select a different folder location.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="04a73-124">這個按鈕只有 **[詳細資料檢視]** 才有提供。</span><span class="sxs-lookup"><span data-stu-id="04a73-124">This button is available only in **Details View**.</span></span> <span data-ttu-id="04a73-125">不過，您可以將滑鼠停留在某個項目上，然後使用功能表來存取 **[詳細資料檢視]** 或 **[清單檢視]** 中的移動功能。</span><span class="sxs-lookup"><span data-stu-id="04a73-125">However, you can hover over an item and use the menu to access the move functionality in either **Details View** or in **List View**.</span></span>  
  
 <span data-ttu-id="04a73-126">搜尋方塊</span><span class="sxs-lookup"><span data-stu-id="04a73-126">Search box</span></span>  
 <span data-ttu-id="04a73-127">輸入您要尋找之項目的全部或部份名稱，然後按一下 **[執行]** 來開始搜尋。</span><span class="sxs-lookup"><span data-stu-id="04a73-127">Type all or part of the name of an item that you want to locate, and then click **Go** to start the search.</span></span> <span data-ttu-id="04a73-128">您可以搜尋的最長字串為 128 個字元。</span><span class="sxs-lookup"><span data-stu-id="04a73-128">The longest string you can search for is 128 characters.</span></span>  
  
 <span data-ttu-id="04a73-129">在文字值的任何位置包含整個搜尋字串的項目名稱或描述，都包含在搜尋結果中。</span><span class="sxs-lookup"><span data-stu-id="04a73-129">Item names or descriptions that contain the entire search string anywhere in the text value are included in the search results.</span></span>  
  
 <span data-ttu-id="04a73-130">不支援布林運算子，例如加號字元 (+)。</span><span class="sxs-lookup"><span data-stu-id="04a73-130">Boolean operators such as the plus character (+) are not supported.</span></span>  
  
 <span data-ttu-id="04a73-131">**詳細資料檢視**</span><span class="sxs-lookup"><span data-stu-id="04a73-131">**Details View**</span></span>  
 <span data-ttu-id="04a73-132">按一下即可在清單中顯示 [搜尋結果] 頁面，其中包含有關項目的其他資訊，例如項目類型、名稱、描述、項目所在的資料夾，以及上一次執行項目的時間。</span><span class="sxs-lookup"><span data-stu-id="04a73-132">Click to display the Search Results page in a list that contains additional information about items, such as the item type, name, description, the folder in which the item is located, and when it was last run.</span></span> <span data-ttu-id="04a73-133">在 **[詳細資料檢視]** 中，您可以使用 **[刪除]** 和 **[移動]** 按鈕來移除和重新定位資料夾中的項目。</span><span class="sxs-lookup"><span data-stu-id="04a73-133">In **Details View**, you can use **Delete** and **Move** buttons to remove and relocate items in the folder.</span></span>  
  
 <span data-ttu-id="04a73-134">將滑鼠停留在某個項目上，然後按一下下拉箭號，即可開啟下拉式功能表，以便從中存取和設定所選取之項目的屬性。</span><span class="sxs-lookup"><span data-stu-id="04a73-134">Hover over an item and click the drop-down arrow to open the drop-down menu from which you can access and configure properties of the selected item.</span></span>  
  
 <span data-ttu-id="04a73-135">**清單視圖**</span><span class="sxs-lookup"><span data-stu-id="04a73-135">**List View**</span></span>  
 <span data-ttu-id="04a73-136">按一下即可顯示 [搜尋結果] 頁面，但是沒有 **[詳細資料檢視]** 中的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="04a73-136">Click to display the Search Results page without details as in **Details View**.</span></span> <span data-ttu-id="04a73-137">[清單檢視] 是 [搜尋結果] 頁面開啟時的預設檢視。</span><span class="sxs-lookup"><span data-stu-id="04a73-137">List View is the default view when the Search Results page opens.</span></span>  
  
 <span data-ttu-id="04a73-138">將滑鼠停留在某個項目上，然後按一下下拉箭號，即可開啟下拉式功能表，以便從中存取和設定所選取之項目的屬性。</span><span class="sxs-lookup"><span data-stu-id="04a73-138">Hover over an item and click the drop-down arrow to open the drop-down menu from which you can access and configure properties of the selected item.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04a73-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="04a73-139">See Also</span></span>  
 <span data-ttu-id="04a73-140">[報表管理員 &#40;SSRS 原生模式&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="04a73-140">[Report Manager  &#40;SSRS Native Mode&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md) </span></span>  
 [<span data-ttu-id="04a73-141">報表管理員 F1 說明</span><span class="sxs-lookup"><span data-stu-id="04a73-141">Report Manager F1 Help</span></span>](../../2014/reporting-services/report-manager-f1-help.md)  
  
  
