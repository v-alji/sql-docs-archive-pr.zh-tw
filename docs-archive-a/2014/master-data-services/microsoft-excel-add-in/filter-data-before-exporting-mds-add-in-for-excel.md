---
title: 載入 (適用于 Excel 的 MDS 增益集) 之前先篩選資料 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 9e30eae0-776b-4a09-aac3-0c0249d92ca5
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 6d0ccf667f37763326e27dcd8d0cfc005627ebc2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87699889"
---
# <a name="filter-data-before-loading-mds-add-in-for-excel"></a><span data-ttu-id="8e42c-102">在載入之前篩選資料 (適用於 Excel 的 MDS 增益集)</span><span class="sxs-lookup"><span data-stu-id="8e42c-102">Filter Data before Loading (MDS Add-in for Excel)</span></span>
  <span data-ttu-id="8e42c-103">在中 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)] ，當您想要限制載入 Excel 的資料大小或範圍時，請篩選資料。</span><span class="sxs-lookup"><span data-stu-id="8e42c-103">In [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], filter data when you want to limit the size or scope of data that you are loading into Excel.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="8e42c-104">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="8e42c-104">Prerequisites</span></span>  
 <span data-ttu-id="8e42c-105">若要執行此程序：</span><span class="sxs-lookup"><span data-stu-id="8e42c-105">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="8e42c-106">您必須擁有存取 [ **Explorer** ] 功能區域的許可權。</span><span class="sxs-lookup"><span data-stu-id="8e42c-106">You must have permission to access the **Explorer** functional area.</span></span>  
  
### <a name="to-filter-data-before-loading"></a><span data-ttu-id="8e42c-107">若要在載入之前篩選資料</span><span class="sxs-lookup"><span data-stu-id="8e42c-107">To filter data before loading</span></span>  
  
1.  <span data-ttu-id="8e42c-108">開啟 Excel，然後在 **[主要資料]** 索引標籤上，連接到 MDS 儲存機制。</span><span class="sxs-lookup"><span data-stu-id="8e42c-108">Open Excel and on the **Master Data** tab, connect to an MDS repository.</span></span> <span data-ttu-id="8e42c-109">如需詳細資訊，請參閱[連接到 MDS 儲存機制 &#40;適用於 Excel 的 MDS 增益集&#41;](connect-to-an-mds-repository-mds-add-in-for-excel.md)。</span><span class="sxs-lookup"><span data-stu-id="8e42c-109">For more information, see [Connect to an MDS Repository &#40;MDS Add-in for Excel&#41;](connect-to-an-mds-repository-mds-add-in-for-excel.md).</span></span>  
  
2.  <span data-ttu-id="8e42c-110">在 **[主資料總管]** 窗格中，選取模型和版本。</span><span class="sxs-lookup"><span data-stu-id="8e42c-110">In the **Master Data Explorer** pane, select a model and version.</span></span> <span data-ttu-id="8e42c-111">系統就會填入實體的清單。</span><span class="sxs-lookup"><span data-stu-id="8e42c-111">The list of entities is populated.</span></span>  
  
    -   <span data-ttu-id="8e42c-112">如果沒有顯示 **[主資料總管]** 窗格，請按一下 **[連接和載入]** 群組中的 **[顯示總管]**。</span><span class="sxs-lookup"><span data-stu-id="8e42c-112">If the **Master Data Explorer** pane is not visible, in the **Connect and Load** group, click **Show Explorer**.</span></span>  
  
    -   <span data-ttu-id="8e42c-113">如果 **[主資料總管]** 窗格已停用，這是因為現有的工作表已經包含 MDS 管理的資料。</span><span class="sxs-lookup"><span data-stu-id="8e42c-113">If the **Master Data Explorer** pane is disabled, it is because the existing sheet already contains MDS-managed data.</span></span> <span data-ttu-id="8e42c-114">若要啟用此窗格，請開啟新的工作表。</span><span class="sxs-lookup"><span data-stu-id="8e42c-114">To enable the pane, open a new worksheet.</span></span>  
  
3.  <span data-ttu-id="8e42c-115">在 **[主資料總管]** 窗格的實體清單中，按一下您想要篩選的實體。</span><span class="sxs-lookup"><span data-stu-id="8e42c-115">In the **Master Data Explorer** pane, in the list of entities, click the entity you want to filter.</span></span>  
  
4.  <span data-ttu-id="8e42c-116">在功能區上，按一下 **[連接和載入]** 群組中的 **[篩選]**。</span><span class="sxs-lookup"><span data-stu-id="8e42c-116">On the ribbon, in the **Connect and Load** group, click **Filter**.</span></span>  
  
5.  <span data-ttu-id="8e42c-117">選取要顯示的屬性 (資料行)、設定資料行的順序，並且視需要篩選資料以傳回較少資料列，藉以完成 **[篩選]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="8e42c-117">Complete the **Filter** dialog box by selecting the attributes (columns) to display, setting the order of the columns, and if needed, filtering the data so fewer rows are returned.</span></span> <span data-ttu-id="8e42c-118">您可以檢視 **[摘要]** 窗格，以便了解系統即將傳回的資料量。</span><span class="sxs-lookup"><span data-stu-id="8e42c-118">View the **Summary** pane for how much data will be returned.</span></span> <span data-ttu-id="8e42c-119">如需詳細資訊，請參閱[篩選對話方塊 &#40;適用於 Excel 的 MDS 增益集&#41;](filter-dialog-box-mds-add-in-for-excel.md)。</span><span class="sxs-lookup"><span data-stu-id="8e42c-119">For more information, see [Filter Dialog Box &#40;MDS Add-in for Excel&#41;](filter-dialog-box-mds-add-in-for-excel.md).</span></span>  
  
6.  <span data-ttu-id="8e42c-120">按一下 **[載入資料]**。</span><span class="sxs-lookup"><span data-stu-id="8e42c-120">Click **Load Data**.</span></span> <span data-ttu-id="8e42c-121">工作表就會填入 MDS 管理的資料。</span><span class="sxs-lookup"><span data-stu-id="8e42c-121">The sheet is populated with MDS-managed data.</span></span>  
  
    > [!NOTE]  
    >  -   <span data-ttu-id="8e42c-122">只有前 1 百萬個成員會載入 Excel 中。</span><span class="sxs-lookup"><span data-stu-id="8e42c-122">Only the first one million members are loaded into Excel.</span></span>  
    > -   <span data-ttu-id="8e42c-123">在受限制清單 (網域屬性) 的資料行中，只會載入前1000個值。</span><span class="sxs-lookup"><span data-stu-id="8e42c-123">In columns that are constrained lists (domain-based attributes), only the first 1000 values are loaded.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="8e42c-124">後續步驟</span><span class="sxs-lookup"><span data-stu-id="8e42c-124">Next Steps</span></span>  
 [<span data-ttu-id="8e42c-125">將 Excel 的資料發行至適用于 Excel 的 mds 增益集 &#40;&#41;</span><span class="sxs-lookup"><span data-stu-id="8e42c-125">Publish Data from Excel to MDS &#40;MDS Add-in for Excel&#41;</span></span>](import-data-from-excel-to-master-data-services-mds-add-in-for-excel.md)  
  
## <a name="see-also"></a><span data-ttu-id="8e42c-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8e42c-126">See Also</span></span>  
 <span data-ttu-id="8e42c-127">[載入適用于 Excel 的 MDS 增益集&#41;的資料 &#40;](overview-exporting-data-to-excel-mds-add-in-for-excel.md) </span><span class="sxs-lookup"><span data-stu-id="8e42c-127">[Loading Data &#40;MDS Add-in for Excel&#41;](overview-exporting-data-to-excel-mds-add-in-for-excel.md) </span></span>  
 <span data-ttu-id="8e42c-128">[[篩選] 對話方塊 &#40;適用于 Excel 的 MDS 增益集&#41;](filter-dialog-box-mds-add-in-for-excel.md) </span><span class="sxs-lookup"><span data-stu-id="8e42c-128">[Filter Dialog Box &#40;MDS Add-in for Excel&#41;](filter-dialog-box-mds-add-in-for-excel.md) </span></span>  
 [<span data-ttu-id="8e42c-129">重新排序資料行 &#40;適用於 Excel 的 MDS 增益集&#41;</span><span class="sxs-lookup"><span data-stu-id="8e42c-129">Reorder Columns &#40;MDS Add-in for Excel&#41;</span></span>](reorder-columns-mds-add-in-for-excel.md)  
  
  
