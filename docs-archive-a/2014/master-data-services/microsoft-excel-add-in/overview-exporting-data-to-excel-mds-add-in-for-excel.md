---
title: 載入適用于 Excel 的 MDS 增益集) 的資料 (|Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: b628548b-982b-4e45-abf4-c8e83e3ab1c2
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: c01bbbc90fcc68c3de976332721b69ad26e606e3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606379"
---
# <a name="loading-data-mds-add-in-for-excel"></a><span data-ttu-id="00ee7-102">載入資料 (適用於 Excel 的 MDS 增益集)</span><span class="sxs-lookup"><span data-stu-id="00ee7-102">Loading Data (MDS Add-in for Excel)</span></span>
  <span data-ttu-id="00ee7-103">在中 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)] ，您必須先將資料從 MDS 儲存機制載入作用中的 Excel 工作表，才能使用它。</span><span class="sxs-lookup"><span data-stu-id="00ee7-103">In the [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], you must load data from the MDS repository into an active Excel worksheet before you can work with it.</span></span> <span data-ttu-id="00ee7-104">當您使用資料完成之後，請將它發行至 MDS 儲存機制，讓其他使用者能夠共用資料。</span><span class="sxs-lookup"><span data-stu-id="00ee7-104">When you are done working with the data, publish it to the MDS repository so other users can share it.</span></span>  
  
 <span data-ttu-id="00ee7-105">您可以載入的資料限制為您有權存取的資料。</span><span class="sxs-lookup"><span data-stu-id="00ee7-105">The data you can load is limited to the data you have permission to access.</span></span> <span data-ttu-id="00ee7-106">存取資料的權限是在 [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] Web 應用程式中設定，或以程式設計方式設定。</span><span class="sxs-lookup"><span data-stu-id="00ee7-106">Permission to access data is set in the [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] web application or set programmatically.</span></span>  
  
 <span data-ttu-id="00ee7-107">當您載入大量資料時，可以設定資料載入時間可能很長時所顯示的警告。</span><span class="sxs-lookup"><span data-stu-id="00ee7-107">When you load large amounts of data, you can set warnings that are displayed when the data that might take a long time to load.</span></span> <span data-ttu-id="00ee7-108">若要這樣做，請按一下 [選項]\*\*\*\* 群組中的 [設定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="00ee7-108">To do this, in the **Options** group, click **Settings**.</span></span> <span data-ttu-id="00ee7-109">在 [資料]\*\*\*\* 索引標籤上，選取 [顯示大型資料集的篩選警告]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="00ee7-109">On the **Data** tab, select the **Display filter warning for large data sets**.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="00ee7-110">啟用 MDS 的活頁簿僅能在 Excel 中使用適用於 Excel 的 MDS 增益集開啟並更新。</span><span class="sxs-lookup"><span data-stu-id="00ee7-110">An MDS-enabled workbook must be opened and updated only in Excel with the MDS Add-in for Excel.</span></span> <span data-ttu-id="00ee7-111">不支援在未安裝 MDS Excel 增益集所在電腦上的 Excel 中開啟啟用 MDS 的活頁簿，而且可能會造成活頁簿檔案損毀。</span><span class="sxs-lookup"><span data-stu-id="00ee7-111">Opening an MDS-enabled workbook in Excel on a computer in which the MDS Excel Add-in is not installed is not supported, and could cause corruption of the workbook file.</span></span> <span data-ttu-id="00ee7-112">如果您要與其他人共用資料，請以電子郵件傳送捷徑查詢檔案給他們，而不要儲存工作表後以電子郵件傳送該工作表。</span><span class="sxs-lookup"><span data-stu-id="00ee7-112">If you want to share data with someone else, email a shortcut query file to them, rather than saving the worksheet and emailing it.</span></span> <span data-ttu-id="00ee7-113">如需查詢的詳細資訊，請參閱[以電子郵件傳送捷徑查詢檔案 &#40;適用於 Excel 的 MDS 增益集&#41;](email-a-shortcut-query-file-mds-add-in-for-excel.md)。</span><span class="sxs-lookup"><span data-stu-id="00ee7-113">For more information on the query, see [Email a Shortcut Query File &#40;MDS Add-in for Excel&#41;](email-a-shortcut-query-file-mds-add-in-for-excel.md).</span></span>  
  
## <a name="filtering-data"></a><span data-ttu-id="00ee7-114">篩選資料</span><span class="sxs-lookup"><span data-stu-id="00ee7-114">Filtering Data</span></span>  
 <span data-ttu-id="00ee7-115">您可以在載入之前篩選資料，以限制您要下載的資料量。</span><span class="sxs-lookup"><span data-stu-id="00ee7-115">You can filter data before loading to limit the amount of data that you're going to download.</span></span> <span data-ttu-id="00ee7-116">這包括選擇您想要載入的屬性 (資料行)、您想要顯示屬性的順序，以及您想要使用的成員 (資料列)。</span><span class="sxs-lookup"><span data-stu-id="00ee7-116">This includes choosing which attributes (columns) you want to load, the order you want to display the attributes, and the members (rows of data) you want to work with.</span></span> <span data-ttu-id="00ee7-117">如需詳細資訊，請參閱[&#40;適用于 Excel 的 MDS 增益集&#41;載入之前篩選資料](filter-data-before-exporting-mds-add-in-for-excel.md)。</span><span class="sxs-lookup"><span data-stu-id="00ee7-117">For more info see [Filter Data before Loading &#40;MDS Add-in for Excel&#41;](filter-data-before-exporting-mds-add-in-for-excel.md).</span></span>  
  
## <a name="connect-automatically-and-load-frequently-used-data"></a><span data-ttu-id="00ee7-118">自動連接並載入經常使用的資料</span><span class="sxs-lookup"><span data-stu-id="00ee7-118">Connect Automatically and Load Frequently-Used Data</span></span>  
 <span data-ttu-id="00ee7-119">如果您想要永遠連接到相同的伺服器並且載入相同的資料集，可以建立包含連接和篩選資訊的捷徑查詢檔案。</span><span class="sxs-lookup"><span data-stu-id="00ee7-119">If you want to always connect to the same server and load the same set of data, you can create shortcut query files, which contain connection and filter information.</span></span> <span data-ttu-id="00ee7-120">如需查詢檔案的詳細資訊，請參閱 [捷徑查詢檔案 &#40;適用於 Excel 的 MDS 增益集&#41;](shortcut-query-files-mds-add-in-for-excel.md)。</span><span class="sxs-lookup"><span data-stu-id="00ee7-120">For more information about query files, see [Shortcut Query Files &#40;MDS Add-in for Excel&#41;](shortcut-query-files-mds-add-in-for-excel.md).</span></span>  
  
## <a name="refreshing-data"></a><span data-ttu-id="00ee7-121">重新整理資料</span><span class="sxs-lookup"><span data-stu-id="00ee7-121">Refreshing Data</span></span>  
 <span data-ttu-id="00ee7-122">其他使用者可能會在您載入之後更新 MDS 儲存機制中的資料。</span><span class="sxs-lookup"><span data-stu-id="00ee7-122">Data in the MDS repository may be updated by other users after you load it.</span></span> <span data-ttu-id="00ee7-123">您可以擷取這項資料，而不遺失已經對非 MDS 資料所做的變更。</span><span class="sxs-lookup"><span data-stu-id="00ee7-123">You can retrieve this data without losing changes you've made to non-MDS data.</span></span> <span data-ttu-id="00ee7-124">如需詳細資訊，請參閱[重新整理資料 &#40;適用於 Excel 的 MDS 增益集&#41;](refreshing-data-mds-add-in-for-excel.md)。</span><span class="sxs-lookup"><span data-stu-id="00ee7-124">For more information, see [Refreshing Data &#40;MDS Add-in for Excel&#41;](refreshing-data-mds-add-in-for-excel.md).</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="00ee7-125">相關工作</span><span class="sxs-lookup"><span data-stu-id="00ee7-125">Related Tasks</span></span>  
  
|<span data-ttu-id="00ee7-126">工作描述</span><span class="sxs-lookup"><span data-stu-id="00ee7-126">Task Description</span></span>|<span data-ttu-id="00ee7-127">主題</span><span class="sxs-lookup"><span data-stu-id="00ee7-127">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="00ee7-128">在將 MDS 資料載入 Excel 之前篩選資料。</span><span class="sxs-lookup"><span data-stu-id="00ee7-128">Filter MDS data before you load it into Excel.</span></span>|[<span data-ttu-id="00ee7-129">載入 &#40;適用于 Excel 的 MDS 增益集之前先篩選資料&#41;</span><span class="sxs-lookup"><span data-stu-id="00ee7-129">Filter Data before Loading &#40;MDS Add-in for Excel&#41;</span></span>](filter-data-before-exporting-mds-add-in-for-excel.md)|  
|<span data-ttu-id="00ee7-130">將 MDS 資料載入 Excel 中。</span><span class="sxs-lookup"><span data-stu-id="00ee7-130">Load MDS data into Excel.</span></span>|[<span data-ttu-id="00ee7-131">將資料從 MDS 載入 Excel 中</span><span class="sxs-lookup"><span data-stu-id="00ee7-131">Load Data from MDS into Excel</span></span>](export-data-to-excel-from-master-data-services.md)|  
|<span data-ttu-id="00ee7-132">在下載資料之前變更資料行的順序。</span><span class="sxs-lookup"><span data-stu-id="00ee7-132">Change the order of columns before you download data.</span></span>|[<span data-ttu-id="00ee7-133">重新排序資料行 &#40;適用於 Excel 的 MDS 增益集&#41;</span><span class="sxs-lookup"><span data-stu-id="00ee7-133">Reorder Columns &#40;MDS Add-in for Excel&#41;</span></span>](reorder-columns-mds-add-in-for-excel.md)|  
  
## <a name="related-content"></a><span data-ttu-id="00ee7-134">相關內容</span><span class="sxs-lookup"><span data-stu-id="00ee7-134">Related Content</span></span>  
  
-   [<span data-ttu-id="00ee7-135">連接 &#40;適用於 Excel 的 MDS 增益集&#41;</span><span class="sxs-lookup"><span data-stu-id="00ee7-135">Connections &#40;MDS Add-in for Excel&#41;</span></span>](connections-mds-add-in-for-excel.md)  
  
-   [<span data-ttu-id="00ee7-136">捷徑查詢檔案 &#40;適用於 Excel 的 MDS 增益集&#41;</span><span class="sxs-lookup"><span data-stu-id="00ee7-136">Shortcut Query Files &#40;MDS Add-in for Excel&#41;</span></span>](shortcut-query-files-mds-add-in-for-excel.md)  
  
-   [<span data-ttu-id="00ee7-137">適用於 Microsoft Excel 的 Master Data Services 增益集</span><span class="sxs-lookup"><span data-stu-id="00ee7-137">Master Data Services Add-in for Microsoft Excel</span></span>](master-data-services-add-in-for-microsoft-excel.md)  
  
-   [<span data-ttu-id="00ee7-138">安全性 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="00ee7-138">Security &#40;Master Data Services&#41;</span></span>](../security-master-data-services.md)  
  
  
