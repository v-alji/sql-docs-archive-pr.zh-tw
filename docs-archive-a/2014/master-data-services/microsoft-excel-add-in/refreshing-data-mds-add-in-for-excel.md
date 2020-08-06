---
title: 重新整理資料 (適用於 Excel 的 MDS 增益集) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 58dbe99a-288d-4f1c-9cd5-704d6836c945
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 49b6e7bc19c41911c626965b9d1de132796367f0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708473"
---
# <a name="refreshing-data-mds-add-in-for-excel"></a><span data-ttu-id="6a1dd-102">重新整理資料 (適用於 Excel 的 MDS 增益集)</span><span class="sxs-lookup"><span data-stu-id="6a1dd-102">Refreshing Data (MDS Add-in for Excel)</span></span>
  <span data-ttu-id="6a1dd-103">在 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]中，當您想要從 MDS 存放庫取得最新資訊，而不開啟新的工作表時，請重新整理資料。</span><span class="sxs-lookup"><span data-stu-id="6a1dd-103">In [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], refresh data when you want to get the latest information from the MDS repository without opening a new worksheet.</span></span> <span data-ttu-id="6a1dd-104">您可以重新整理所有資料格或資料格的選取範圍。</span><span class="sxs-lookup"><span data-stu-id="6a1dd-104">You can refresh either all cells or a selection of cells.</span></span> <span data-ttu-id="6a1dd-105">當您已經插入含有自訂公式或不在 MDS 中管理之資料的資料行，而且想要加以保留時，這樣做可能很有用。</span><span class="sxs-lookup"><span data-stu-id="6a1dd-105">This can be useful when you have inserted columns with custom formulas or other data that is not managed in MDS and you want to preserve it.</span></span>  
  
## <a name="when-you-can-refresh-mds-managed-data"></a><span data-ttu-id="6a1dd-106">何時能夠重新整理 MDS 管理的資料</span><span class="sxs-lookup"><span data-stu-id="6a1dd-106">When You Can Refresh MDS-Managed Data</span></span>  
 <span data-ttu-id="6a1dd-107">如果使用中工作表已經包含 MDS 管理的資料，您就可以在使用中工作表中重新整理 MDS 管理的資料。</span><span class="sxs-lookup"><span data-stu-id="6a1dd-107">You can refresh MDS-managed data in an active worksheet if the active worksheet already contains MDS-managed data.</span></span> <span data-ttu-id="6a1dd-108">如果您已經變更屬性值或將成員加入至工作表，就必須先發行變更，然後才能重新整理。</span><span class="sxs-lookup"><span data-stu-id="6a1dd-108">If you have changed attribute values or added members to the worksheet, you must publish your changes before you can refresh.</span></span>  
  
## <a name="refreshing-a-selection"></a><span data-ttu-id="6a1dd-109">重新整理選取範圍</span><span class="sxs-lookup"><span data-stu-id="6a1dd-109">Refreshing a Selection</span></span>  
 <span data-ttu-id="6a1dd-110">您可以選擇重新整理所有資料格或只重新整理選取的資料格。</span><span class="sxs-lookup"><span data-stu-id="6a1dd-110">You have the choice of refreshing all cells or refreshing only selected cells.</span></span> <span data-ttu-id="6a1dd-111">選取的資料格必須是連續的。</span><span class="sxs-lookup"><span data-stu-id="6a1dd-111">The selected cells must be contiguous.</span></span> <span data-ttu-id="6a1dd-112">如果選取一組連續的資料格，該集合中所有 MDS 管理的資料格都會更新，以顯示目前儲存在伺服器上的值。</span><span class="sxs-lookup"><span data-stu-id="6a1dd-112">If a set of contiguous cells is selected, all MDS managed cells in that set will be updated to display the values currently stored on the server.</span></span> <span data-ttu-id="6a1dd-113">未變更且 MDS 未管理的資料列與資料行無論如何都不受影響。</span><span class="sxs-lookup"><span data-stu-id="6a1dd-113">Unchanged rows and columns that are not managed by MDS are not affected in any way.</span></span>  
  
## <a name="what-happens-when-you-refresh-mds-managed-data"></a><span data-ttu-id="6a1dd-114">重新整理 MDS 管理的資料時會發生什麼狀況</span><span class="sxs-lookup"><span data-stu-id="6a1dd-114">What Happens When You Refresh MDS-Managed Data</span></span>  
 <span data-ttu-id="6a1dd-115">當您在 [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]中重新整理資料時，工作表處理 MDS 管理之資料的方式，取決從您上次載入資料之後 MDS 存放庫變更了哪些內容而定。</span><span class="sxs-lookup"><span data-stu-id="6a1dd-115">When you refresh data in the [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], what happens to the MDS-managed data in the sheet depends on what has changed in the MDS repository since you last loaded the data.</span></span>  
  
-   <span data-ttu-id="6a1dd-116">如果新的成員已經加入至儲存機制，它們就會加入至工作表的結尾並且以綠色反白顯示。</span><span class="sxs-lookup"><span data-stu-id="6a1dd-116">If new members have been added to repository, they are added to the end of the worksheet and are highlighted in green.</span></span>  
  
-   <span data-ttu-id="6a1dd-117">如果儲存機制已刪除成員，系統就會從工作表中刪除它們。</span><span class="sxs-lookup"><span data-stu-id="6a1dd-117">If members were deleted from the repository, they are deleted from the worksheet.</span></span>  
  
-   <span data-ttu-id="6a1dd-118">如果 MDS 儲存機制中的某個屬性值已變更，工作表中的值就會使用 MDS 儲存機制中的值來更新。</span><span class="sxs-lookup"><span data-stu-id="6a1dd-118">If an attribute value has changed in the MDS repository, the value in the worksheet is updated with value from the MDS repository.</span></span> <span data-ttu-id="6a1dd-119">資料格色彩不會變更。</span><span class="sxs-lookup"><span data-stu-id="6a1dd-119">The cell color does not change.</span></span>  
  
> [!WARNING]
>  -   <span data-ttu-id="6a1dd-120">在使用中工作表中，如果非管理的資料存在 MDS 管理之資料下方的資料列中，系統可能會覆寫非管理的資料。</span><span class="sxs-lookup"><span data-stu-id="6a1dd-120">In the active worksheet, if non-managed data exists in rows beneath the MDS-managed data, the non-managed data may be overwritten.</span></span> <span data-ttu-id="6a1dd-121">當您重新整理工作表，而且加入 MDS 管理之資料的新資料列 (與非管理的資料重疊) 時，就會發生這種狀況。</span><span class="sxs-lookup"><span data-stu-id="6a1dd-121">This occurs when you refresh the sheet and new rows of MDS-managed data, which overlap with the non-managed data, are added.</span></span>  
> -   <span data-ttu-id="6a1dd-122">當您重新整理時，系統會刪除 MDS 管理之資料格的註解。</span><span class="sxs-lookup"><span data-stu-id="6a1dd-122">When you refresh, comments on MDS-managed cells are deleted.</span></span>  
  
## <a name="how-to-refresh-mds-managed-data"></a><span data-ttu-id="6a1dd-123">如何重新整理 MDS 管理的資料</span><span class="sxs-lookup"><span data-stu-id="6a1dd-123">How to Refresh MDS-Managed Data</span></span>  
 <span data-ttu-id="6a1dd-124">在功能區的 [連接和載入]\*\*\*\* 群組中，[重新整理]\*\*\*\* 按鈕有兩個選項，分別是 [全部重新整理]\*\*\*\* 和 [重新整理選取項目]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="6a1dd-124">In the **Connect and Load** group on the ribbon, the **Refresh** button has two options, **Refresh All** and **Refresh Selection**.</span></span> <span data-ttu-id="6a1dd-125">功能區按鈕的預設動作是 [全部重新整理]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="6a1dd-125">The default action of the ribbon button is **Refresh All**.</span></span> <span data-ttu-id="6a1dd-126">若要使用來自伺服器的值重新整理整份工作表，按一下 [重新整理]\*\*\*\* 按鈕，或選擇 [全部重新整理]\*\*\*\* 選項。</span><span class="sxs-lookup"><span data-stu-id="6a1dd-126">To refresh the entire sheet with values from the server, click the **Refresh** button or choose the **Refresh All** option.</span></span> <span data-ttu-id="6a1dd-127">若僅要重新整理工作表中的部分資料格，請選取資料格 (必須是一個連續的選取範圍)，然後選擇 [重新整理選取項目]\*\*\*\* 選項。</span><span class="sxs-lookup"><span data-stu-id="6a1dd-127">To refresh only some of the cells in a sheet, select the cells (must be one contiguous selection) and choose the **Refresh Selection** option.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="6a1dd-128">相關工作</span><span class="sxs-lookup"><span data-stu-id="6a1dd-128">Related Tasks</span></span>  
  
|<span data-ttu-id="6a1dd-129">工作描述</span><span class="sxs-lookup"><span data-stu-id="6a1dd-129">Task Description</span></span>|<span data-ttu-id="6a1dd-130">主題</span><span class="sxs-lookup"><span data-stu-id="6a1dd-130">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="6a1dd-131">建立 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] 資料庫的連接。</span><span class="sxs-lookup"><span data-stu-id="6a1dd-131">Create a connection to a [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] database.</span></span>|[<span data-ttu-id="6a1dd-132">連接到 MDS 儲存機制 &#40;適用於 Excel 的 MDS 增益集&#41;</span><span class="sxs-lookup"><span data-stu-id="6a1dd-132">Connect to an MDS Repository &#40;MDS Add-in for Excel&#41;</span></span>](connect-to-an-mds-repository-mds-add-in-for-excel.md)|  
|<span data-ttu-id="6a1dd-133">將 MDS 資料載入 Excel 中。</span><span class="sxs-lookup"><span data-stu-id="6a1dd-133">Load MDS data into Excel.</span></span>|[<span data-ttu-id="6a1dd-134">將資料從 MDS 載入 Excel 中</span><span class="sxs-lookup"><span data-stu-id="6a1dd-134">Load Data from MDS into Excel</span></span>](export-data-to-excel-from-master-data-services.md)|  
  
## <a name="related-content"></a><span data-ttu-id="6a1dd-135">相關內容</span><span class="sxs-lookup"><span data-stu-id="6a1dd-135">Related Content</span></span>  
  
-   [<span data-ttu-id="6a1dd-136">連接 &#40;適用於 Excel 的 MDS 增益集&#41;</span><span class="sxs-lookup"><span data-stu-id="6a1dd-136">Connections &#40;MDS Add-in for Excel&#41;</span></span>](connections-mds-add-in-for-excel.md)  
  
-   [<span data-ttu-id="6a1dd-137">載入適用于 Excel 的 MDS 增益集&#41;的資料 &#40;</span><span class="sxs-lookup"><span data-stu-id="6a1dd-137">Loading Data &#40;MDS Add-in for Excel&#41;</span></span>](overview-exporting-data-to-excel-mds-add-in-for-excel.md)  
  
-   [<span data-ttu-id="6a1dd-138">適用於 Microsoft Excel 的 Master Data Services 增益集</span><span class="sxs-lookup"><span data-stu-id="6a1dd-138">Master Data Services Add-in for Microsoft Excel</span></span>](master-data-services-add-in-for-microsoft-excel.md)  
  
  
