---
title: 結合資料 (適用於 Excel 的 MDS 增益集) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: a867dc15-5a0d-457c-8304-ac323bcf9377
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: bc2d5bffb6d7a12164a8643e9a790b32538f8979
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87698386"
---
# <a name="combine-data-mds-add-in-for-excel"></a><span data-ttu-id="ea139-102">結合資料 (適用於 Excel 的 MDS 增益集)</span><span class="sxs-lookup"><span data-stu-id="ea139-102">Combine Data (MDS Add-in for Excel)</span></span>
  <span data-ttu-id="ea139-103">在 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]中，當您要在發行前比較資料時，可以結合兩個工作表的資料。</span><span class="sxs-lookup"><span data-stu-id="ea139-103">In the [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], combine data from two worksheets when you want to compare data before publishing.</span></span> <span data-ttu-id="ea139-104">在此程序中，將兩個工作表中的資料結合為一個工作表。</span><span class="sxs-lookup"><span data-stu-id="ea139-104">In this procedure, you combine data from a two worksheets into one.</span></span> <span data-ttu-id="ea139-105">然後可以進一步進行比較，並判斷哪些資料 (如果有) 將發行到 MDS 儲存機制。</span><span class="sxs-lookup"><span data-stu-id="ea139-105">Then you can perform further comparisons and determine which data, if any, to publish to the MDS repository.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="ea139-106">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="ea139-106">Prerequisites</span></span>  
  
-   <span data-ttu-id="ea139-107">您必須擁有包含 MDS 管理之資料的工作表。</span><span class="sxs-lookup"><span data-stu-id="ea139-107">You must have a worksheet that contains MDS-managed data.</span></span> <span data-ttu-id="ea139-108">如需詳細資訊，請參閱將[資料從 MDS 載入 Excel](export-data-to-excel-from-master-data-services.md)中。</span><span class="sxs-lookup"><span data-stu-id="ea139-108">For more information, see [Load Data from MDS into Excel](export-data-to-excel-from-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="ea139-109">您必須擁有另一個工作表，其資料將要與 MDS 管理之資料結合。</span><span class="sxs-lookup"><span data-stu-id="ea139-109">You must have a worksheet that contains data you want to combine with MDS-managed data.</span></span> <span data-ttu-id="ea139-110">此工作表必須具有標頭資料列。</span><span class="sxs-lookup"><span data-stu-id="ea139-110">This sheet must have a header row.</span></span>  
  
### <a name="to-combine-non-managed-data-into-an-mds-managed-sheet"></a><span data-ttu-id="ea139-111">若要將非管理的資料合併到 MDS 管理的工作表中</span><span class="sxs-lookup"><span data-stu-id="ea139-111">To combine non-managed data into an MDS-managed sheet</span></span>  
  
1.  <span data-ttu-id="ea139-112">在包含 MDS 管理之資料的工作表上，按一下 **[發行和驗證]** 群組中的 **[結合資料]**。</span><span class="sxs-lookup"><span data-stu-id="ea139-112">On the sheet that contains MDS-managed data, in the **Publish and Validate** group, click **Combine Data**.</span></span>  
  
2.  <span data-ttu-id="ea139-113">在 **[結合資料]** 對話方塊中，按一下 **[要與 MDS 資料結合的範圍]** 文字方塊旁邊的圖示。</span><span class="sxs-lookup"><span data-stu-id="ea139-113">In the **Combine Data** dialog box, next to the **Range to combine with MDS data** text box, click the icon.</span></span> <span data-ttu-id="ea139-114">此對話方塊會收縮。</span><span class="sxs-lookup"><span data-stu-id="ea139-114">The dialog box contracts.</span></span>  
  
3.  <span data-ttu-id="ea139-115">按一下包含您要結合之資料的工作表。</span><span class="sxs-lookup"><span data-stu-id="ea139-115">Click the sheet that contains the data you want to combine.</span></span>  
  
4.  <span data-ttu-id="ea139-116">反白顯示工作表上要結合的所有資料格，包括標頭資料列。</span><span class="sxs-lookup"><span data-stu-id="ea139-116">Highlight all cells on the sheet that you want to combine, including the header row.</span></span>  
  
5.  <span data-ttu-id="ea139-117">在 **[結合資料]** 對話方塊中，按一下圖示。</span><span class="sxs-lookup"><span data-stu-id="ea139-117">In the **Combine Data** dialog box, click the icon.</span></span> <span data-ttu-id="ea139-118">此對話方塊會展開。</span><span class="sxs-lookup"><span data-stu-id="ea139-118">The dialog box expands.</span></span>  
  
6.  <span data-ttu-id="ea139-119">對於為 MDS 實體列出的資料行，選取 **[對應資料行]** 底下的資料行。</span><span class="sxs-lookup"><span data-stu-id="ea139-119">For a column listed for the MDS entity, select a column under **Corresponding Column**.</span></span> <span data-ttu-id="ea139-120">並不是所有 MDS 資料行都需要對應資料行。</span><span class="sxs-lookup"><span data-stu-id="ea139-120">All MDS columns do not need corresponding columns.</span></span>  
  
7.  <span data-ttu-id="ea139-121">按一下 **[合併]**。</span><span class="sxs-lookup"><span data-stu-id="ea139-121">Click **Combine**.</span></span> <span data-ttu-id="ea139-122">**SOURCE** 資料行將顯示，表示資料來自 MDS 或外部來源。</span><span class="sxs-lookup"><span data-stu-id="ea139-122">A **SOURCE** column is displayed, indicating whether the data is from MDS or an external source.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="ea139-123">後續步驟</span><span class="sxs-lookup"><span data-stu-id="ea139-123">Next Steps</span></span>  
  
-   <span data-ttu-id="ea139-124">若要尋找 MDS 管理之資料和外部資料之間的相似性，請參閱[比對相似資料 &#40;適用於 Excel 的 MDS 增益集&#41;](match-similar-data-mds-add-in-for-excel.md)。</span><span class="sxs-lookup"><span data-stu-id="ea139-124">To find similarities between the MDS-managed and external data, see [Match Similar Data &#40;MDS Add-in for Excel&#41;](match-similar-data-mds-add-in-for-excel.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea139-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ea139-125">See Also</span></span>  
 <span data-ttu-id="ea139-126">[載入適用于 Excel 的 MDS 增益集&#41;的資料 &#40;](overview-exporting-data-to-excel-mds-add-in-for-excel.md) </span><span class="sxs-lookup"><span data-stu-id="ea139-126">[Loading Data &#40;MDS Add-in for Excel&#41;](overview-exporting-data-to-excel-mds-add-in-for-excel.md) </span></span>  
 [<span data-ttu-id="ea139-127">適用於 Excel 的 MDS 增益集中的資料品質比對</span><span class="sxs-lookup"><span data-stu-id="ea139-127">Data Quality Matching in the MDS Add-in for Excel</span></span>](data-quality-matching-in-the-mds-add-in-for-excel.md)  
  
  
