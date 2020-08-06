---
title: 比對相似資料 (適用於 Excel 的 MDS 增益集) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: f6fd6fc1-3569-42a5-b6cb-87a921c88f3b
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 70dea36de557c6fda909d06ee19ff8fa2ed6908d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87699880"
---
# <a name="match-similar-data-mds-add-in-for-excel"></a><span data-ttu-id="49514-102">比對相似資料 (適用於 Excel 的 MDS 增益集)</span><span class="sxs-lookup"><span data-stu-id="49514-102">Match Similar Data (MDS Add-in for Excel)</span></span>
  <span data-ttu-id="49514-103">在 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]中，使用 Data Quality Services (DQS) 功能來尋找資料中的相似度。</span><span class="sxs-lookup"><span data-stu-id="49514-103">In the [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], use Data Quality Services (DQS) functionality to find similarities in your data.</span></span>  
  
 <span data-ttu-id="49514-104">若要執行此程序，您可以：</span><span class="sxs-lookup"><span data-stu-id="49514-104">To perform this procedure, you can:</span></span>  
  
-   <span data-ttu-id="49514-105">使用預設 Data Quality Services 知識庫。</span><span class="sxs-lookup"><span data-stu-id="49514-105">Use the default Data Quality Services knowledge base, or</span></span>  
  
-   <span data-ttu-id="49514-106">建立您自己的自訂 DQS 知識庫和比對原則。</span><span class="sxs-lookup"><span data-stu-id="49514-106">Create your own custom DQS knowledge base and matching policy.</span></span> <span data-ttu-id="49514-107">如需相關資訊，請參閱 [建立訂閱](../../data-quality-services/create-a-matching-policy.md)。</span><span class="sxs-lookup"><span data-stu-id="49514-107">For more information, see [Create a Matching Policy](../../data-quality-services/create-a-matching-policy.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="49514-108">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="49514-108">Prerequisites</span></span>  
  
-   <span data-ttu-id="49514-109">您必須擁有包含 MDS 管理之資料的工作表。</span><span class="sxs-lookup"><span data-stu-id="49514-109">You must have a worksheet that contains MDS-managed data.</span></span> <span data-ttu-id="49514-110">如需詳細資訊，請參閱將[資料從 MDS 載入 Excel](export-data-to-excel-from-master-data-services.md)中。</span><span class="sxs-lookup"><span data-stu-id="49514-110">For more information, see [Load Data from MDS into Excel](export-data-to-excel-from-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="49514-111">選擇性。</span><span class="sxs-lookup"><span data-stu-id="49514-111">Optional.</span></span> <span data-ttu-id="49514-112">檢查相似度之前，您可以將其他資料與 MDS 管理的資料結合。</span><span class="sxs-lookup"><span data-stu-id="49514-112">You can combine other data with the MDS-managed data before checking for similarities.</span></span> <span data-ttu-id="49514-113">如需詳細資訊，請參閱 [結合資料 &#40;適用於 Excel 的 MDS 增益集&#41;](combine-data-mds-add-in-for-excel.md)＞。</span><span class="sxs-lookup"><span data-stu-id="49514-113">For more information, see [Combine Data &#40;MDS Add-in for Excel&#41;](combine-data-mds-add-in-for-excel.md).</span></span>  
  
### <a name="to-find-similarities-by-using-the-default-knowledge-base"></a><span data-ttu-id="49514-114">若要使用預設知識庫尋找相似度</span><span class="sxs-lookup"><span data-stu-id="49514-114">To find similarities by using the default knowledge base</span></span>  
  
1.  <span data-ttu-id="49514-115">從包含 MDS 管理之資料的工作表中，按一下 [資料品質]\*\*\*\* 群組中的 [比對資料]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="49514-115">From the worksheet that contains MDS-managed data, in the **Data Quality** group, click **Match Data**.</span></span>  
  
2.  <span data-ttu-id="49514-116">在 [比對資料]\*\*\*\* 對話方塊中，從 [DQS 知識庫]\*\*\*\* 清單中選取 [DQS 資料 (預設值)]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="49514-116">In the **Match Data** dialog box, from the **DQS Knowledge Base** list, select **DQS Data (default)**.</span></span>  
  
3.  <span data-ttu-id="49514-117">為包含要比對之資料的每個資料行，在對話方塊中加入一個資料列。</span><span class="sxs-lookup"><span data-stu-id="49514-117">For each column that contains data you want to match, add a row in the dialog box.</span></span> <span data-ttu-id="49514-118">如需此對話方塊中的欄位資訊，請參閱 [如何設定比對規則參數](../../data-quality-services/create-a-matching-policy.md#MatchingRules)。</span><span class="sxs-lookup"><span data-stu-id="49514-118">For information about the fields in this dialog box, see [How to Set Matching Rule Parameters](../../data-quality-services/create-a-matching-policy.md#MatchingRules).</span></span>  
  
4.  <span data-ttu-id="49514-119">當所有加權值的總和等於 100% 時，按一下 [確定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="49514-119">When the total of all weight values equals 100 percent, click **OK**.</span></span>  
  
### <a name="to-find-similarities-by-using-a-custom-knowledge-base"></a><span data-ttu-id="49514-120">若要使用自訂知識庫尋找相似度</span><span class="sxs-lookup"><span data-stu-id="49514-120">To find similarities by using a custom knowledge base</span></span>  
  
1.  <span data-ttu-id="49514-121">從包含 MDS 管理之資料的工作表中，按一下 [資料品質]\*\*\*\* 群組中的 [比對資料]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="49514-121">From the worksheet that contains MDS-managed data, in the **Data Quality** group, click **Match Data**.</span></span>  
  
2.  <span data-ttu-id="49514-122">從 [DQS 知識庫]\*\*\*\* 清單中，選取自訂知識庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="49514-122">From the **DQS Knowledge Base** list, select the name of your custom knowledge base.</span></span>  
  
3.  <span data-ttu-id="49514-123">為工作表中的每個資料行，選取 DQS 定義域。</span><span class="sxs-lookup"><span data-stu-id="49514-123">For each column in the worksheet, select a DQS domain.</span></span>  
  
4.  <span data-ttu-id="49514-124">當所有 DQS 定義域都對應到工作表中的資料行時，請按一下 [確定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="49514-124">When all DQS domains are mapped to columns in the worksheet, click **OK**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="49514-125">後續步驟</span><span class="sxs-lookup"><span data-stu-id="49514-125">Next Steps</span></span>  
  
-   <span data-ttu-id="49514-126">檢視其他資訊來判斷哪些資料是相似。</span><span class="sxs-lookup"><span data-stu-id="49514-126">View additional information to determine which data is similar.</span></span> <span data-ttu-id="49514-127">如需詳細資訊，請參閱[資料品質比對資料行 &#40;適用於 Excel 的 MDS 增益集&#41;](data-quality-matching-columns-mds-add-in-for-excel.md)。</span><span class="sxs-lookup"><span data-stu-id="49514-127">For more information, see [Data Quality Matching Columns &#40;MDS Add-in for Excel&#41;](data-quality-matching-columns-mds-add-in-for-excel.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49514-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="49514-128">See Also</span></span>  
 <span data-ttu-id="49514-129">[適用于 Excel 的 MDS 增益集中的資料品質比對](data-quality-matching-in-the-mds-add-in-for-excel.md) </span><span class="sxs-lookup"><span data-stu-id="49514-129">[Data Quality Matching in the MDS Add-in for Excel](data-quality-matching-in-the-mds-add-in-for-excel.md) </span></span>  
 [<span data-ttu-id="49514-130">資料比對</span><span class="sxs-lookup"><span data-stu-id="49514-130">Data Matching</span></span>](../../data-quality-services/data-matching.md)  
  
  
