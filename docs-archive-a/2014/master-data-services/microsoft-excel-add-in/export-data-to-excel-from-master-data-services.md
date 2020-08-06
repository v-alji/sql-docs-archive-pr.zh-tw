---
title: 將資料從 MDS 載入 Excel 中 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: dd29389b-928c-4e50-995c-c6af27f97805
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 35672807d5bb108e9386f892aea1847d45ebeb33
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87699892"
---
# <a name="load-data-from-mds-into-excel"></a><span data-ttu-id="813e4-102">將資料從 MDS 載入 Excel 中</span><span class="sxs-lookup"><span data-stu-id="813e4-102">Load Data from MDS into Excel</span></span>
  <span data-ttu-id="813e4-103">在中 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)] ，您必須從 MDS 儲存機制載入資料，才能使用它。</span><span class="sxs-lookup"><span data-stu-id="813e4-103">In the [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], you must load data from the MDS repository in order to work with it.</span></span>  
  
 <span data-ttu-id="813e4-104">如果您想要在載入之前篩選資料集，請[先參閱先篩選資料，然後再載入適用于 Excel 的 &#40;MDS 增益集&#41;](filter-data-before-exporting-mds-add-in-for-excel.md) 。</span><span class="sxs-lookup"><span data-stu-id="813e4-104">If you want to filter the dataset before loading, see [Filter Data before Loading &#40;MDS Add-in for Excel&#41;](filter-data-before-exporting-mds-add-in-for-excel.md) instead.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="813e4-105">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="813e4-105">Prerequisites</span></span>  
 <span data-ttu-id="813e4-106">若要執行此程序：</span><span class="sxs-lookup"><span data-stu-id="813e4-106">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="813e4-107">您必須擁有存取 [ **Explorer** ] 功能區域的許可權。</span><span class="sxs-lookup"><span data-stu-id="813e4-107">You must have permission to access the **Explorer** functional area.</span></span>  
  
### <a name="to-load-data-from-mds-into-excel"></a><span data-ttu-id="813e4-108">若要將資料從 MDS 載入 Excel 中</span><span class="sxs-lookup"><span data-stu-id="813e4-108">To load data from MDS into Excel</span></span>  
  
1.  <span data-ttu-id="813e4-109">開啟 Excel，然後在 **[主要資料]** 索引標籤上，連接到 MDS 儲存機制。</span><span class="sxs-lookup"><span data-stu-id="813e4-109">Open Excel and on the **Master Data** tab, connect to an MDS repository.</span></span> <span data-ttu-id="813e4-110">如需詳細資訊，請參閱[連接到 MDS 儲存機制 &#40;適用於 Excel 的 MDS 增益集&#41;](connect-to-an-mds-repository-mds-add-in-for-excel.md)。</span><span class="sxs-lookup"><span data-stu-id="813e4-110">For more information, see [Connect to an MDS Repository &#40;MDS Add-in for Excel&#41;](connect-to-an-mds-repository-mds-add-in-for-excel.md).</span></span>  
  
2.  <span data-ttu-id="813e4-111">在 **[主資料總管]** 窗格中，選取模型和版本。</span><span class="sxs-lookup"><span data-stu-id="813e4-111">In the **Master Data Explorer** pane, select a model and version.</span></span> <span data-ttu-id="813e4-112">系統就會填入實體的清單。</span><span class="sxs-lookup"><span data-stu-id="813e4-112">The list of entities is populated.</span></span>  
  
    -   <span data-ttu-id="813e4-113">如果沒有顯示 **[主資料總管]** 窗格，請按一下 **[連接和載入]** 群組中的 **[顯示總管]**。</span><span class="sxs-lookup"><span data-stu-id="813e4-113">If the **Master Data Explorer** pane is not visible, in the **Connect and Load** group, click **Show Explorer**.</span></span>  
  
    -   <span data-ttu-id="813e4-114">如果 **[主資料總管]** 窗格已停用，這是因為現有的工作表已經包含 MDS 管理的資料。</span><span class="sxs-lookup"><span data-stu-id="813e4-114">If the **Master Data Explorer** pane is disabled, it is because the existing sheet already contains MDS-managed data.</span></span> <span data-ttu-id="813e4-115">若要啟用此窗格，請開啟新的工作表。</span><span class="sxs-lookup"><span data-stu-id="813e4-115">To enable the pane, open a new worksheet.</span></span>  
  
3.  <span data-ttu-id="813e4-116">在 [主資料總管]\*\*\*\* 窗格的實體清單中，按兩下您想要載入的實體。</span><span class="sxs-lookup"><span data-stu-id="813e4-116">In the **Master Data Explorer** pane, in the list of entities, double-click the entity you want to load.</span></span>  
  
    > [!NOTE]  
    >  -   <span data-ttu-id="813e4-117">只有前 1 百萬個成員會載入 Excel 中。</span><span class="sxs-lookup"><span data-stu-id="813e4-117">Only the first one million members are loaded into Excel.</span></span> <span data-ttu-id="813e4-118">若要在載入之前篩選清單，在功能區上，按一下 [連接和載入]\*\*\*\* 群組中的 [篩選]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="813e4-118">To filter the list before loading, on the ribbon in the **Connect and Load** group, click **Filter**.</span></span>  
    > -   <span data-ttu-id="813e4-119">在屬於受條件約束之清單 (網域屬性) 的資料行中，只會載入前 25,000 個值。</span><span class="sxs-lookup"><span data-stu-id="813e4-119">In columns that are constrained lists (domain-based attributes), only the first 25,000 values are loaded.</span></span> <span data-ttu-id="813e4-120">您可以在安裝 Excel 所在電腦上的 excelusersettings.config 檔案內，變更 MaximumDbaEntitySize 屬性中的這個數字。</span><span class="sxs-lookup"><span data-stu-id="813e4-120">You can change this number in the MaximumDbaEntitySize property in the excelusersettings.config file located on the computer that Excel is installed on.</span></span> <span data-ttu-id="813e4-121">此檔案位於 C:\Users \\<user \> \AppData\Local\Microsoft\Microsoft SQL Server\120\MasterDataServices \\ 。</span><span class="sxs-lookup"><span data-stu-id="813e4-121">This file is located in C:\Users\\<user\>\AppData\Local\Microsoft\Microsoft SQL Server\120\MasterDataServices\\.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="813e4-122">如果您使用適用於 Microsoft Excel (32 位元 Excel) 的增益集載入以文字分隔的資料，而且 [Cell Count to Load (要載入的資料格計數)]\*\*\*\* 和 [Cell Count to Publish (要發行的資料格計數)]\*\*\*\* 屬性的值都設為最大值 1000，將會發生記憶體不足的錯誤。</span><span class="sxs-lookup"><span data-stu-id="813e4-122">When you load text-delimited data using the Add-in for Microsoft Excel with 32-bit Excel, and the settings for the **Cell Count to Load** and **Cell Count to Publish** properties are both set to the maximum of 1000, an out-of-memory error will occur.</span></span> <span data-ttu-id="813e4-123">您必須使用 64 位元 Excel，才能使用 [Cell Count to Load (要載入的資料格計數)]\*\*\*\* 和 [Cell Count to Publish (要發行的資料格計數)]\*\*\*\* 的最大值設定。</span><span class="sxs-lookup"><span data-stu-id="813e4-123">You have to use 64-bit Excel to use the maximum settings for **Cell Count to Load** and **Cell Count to Publish**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="813e4-124">後續步驟</span><span class="sxs-lookup"><span data-stu-id="813e4-124">Next Steps</span></span>  
 [<span data-ttu-id="813e4-125">將 Excel 的資料發行至適用于 Excel 的 mds 增益集 &#40;&#41;</span><span class="sxs-lookup"><span data-stu-id="813e4-125">Publish Data from Excel to MDS &#40;MDS Add-in for Excel&#41;</span></span>](import-data-from-excel-to-master-data-services-mds-add-in-for-excel.md)  
  
## <a name="see-also"></a><span data-ttu-id="813e4-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="813e4-126">See Also</span></span>  
 <span data-ttu-id="813e4-127">[載入適用于 Excel 的 MDS 增益集&#41;的資料 &#40;](overview-exporting-data-to-excel-mds-add-in-for-excel.md) </span><span class="sxs-lookup"><span data-stu-id="813e4-127">[Loading Data &#40;MDS Add-in for Excel&#41;](overview-exporting-data-to-excel-mds-add-in-for-excel.md) </span></span>  
 <span data-ttu-id="813e4-128">[[篩選] 對話方塊 &#40;適用于 Excel 的 MDS 增益集&#41;](filter-dialog-box-mds-add-in-for-excel.md) </span><span class="sxs-lookup"><span data-stu-id="813e4-128">[Filter Dialog Box &#40;MDS Add-in for Excel&#41;](filter-dialog-box-mds-add-in-for-excel.md) </span></span>  
 [<span data-ttu-id="813e4-129">發行資料 &#40;適用于 Excel 的 MDS 增益集&#41;</span><span class="sxs-lookup"><span data-stu-id="813e4-129">Publishing Data &#40;MDS Add-in for Excel&#41;</span></span>](overview-importing-data-from-excel-mds-add-in-for-excel.md)  
  
  
