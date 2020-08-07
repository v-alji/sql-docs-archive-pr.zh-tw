---
title: 資料品質比對資料行 (適用於 Excel 的 MDS 增益集) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: f683fdc6-0d4c-4793-8143-567616cb2094
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 939ec9727cc81ce3b206b8bc7ca3ed8dd62c3877
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584608"
---
# <a name="data-quality-matching-columns-mds-add-in-for-excel"></a><span data-ttu-id="d05c9-102">資料品質比對資料行 (適用於 Excel 的 MDS 增益集)</span><span class="sxs-lookup"><span data-stu-id="d05c9-102">Data Quality Matching Columns (MDS Add-in for Excel)</span></span>
  <span data-ttu-id="d05c9-103">在中， [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)] 當您比對資料之後，您可以在功能區的 [**資料品質**] 群組中按一下 [**顯示詳細**資料]，以顯示提供相符詳細資料的資料行。</span><span class="sxs-lookup"><span data-stu-id="d05c9-103">In the [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], after you match data, in the **Data Quality** group on the ribbon, you can click **Show Details** to display columns that provide matching details.</span></span>  
  
 <span data-ttu-id="d05c9-104">下表顯示比對資料時所顯示的資料行。</span><span class="sxs-lookup"><span data-stu-id="d05c9-104">The following table shows the columns that are displayed when matching data.</span></span>  
  
|<span data-ttu-id="d05c9-105">名稱</span><span class="sxs-lookup"><span data-stu-id="d05c9-105">Name</span></span>|<span data-ttu-id="d05c9-106">描述</span><span class="sxs-lookup"><span data-stu-id="d05c9-106">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="d05c9-107">**CLUSTER_ID**</span><span class="sxs-lookup"><span data-stu-id="d05c9-107">**CLUSTER_ID**</span></span>|<span data-ttu-id="d05c9-108">用於將相似記錄分組的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="d05c9-108">A unique identifier used to group similar records.</span></span> <span data-ttu-id="d05c9-109">所有相似的資料列都有相同的 **CLUSTER_ID**。</span><span class="sxs-lookup"><span data-stu-id="d05c9-109">All rows that are similar have the same **CLUSTER_ID**.</span></span> <span data-ttu-id="d05c9-110">如果沒有顯示資料列的 **CLUSTER_ID** ，表示找不到相似的記錄。</span><span class="sxs-lookup"><span data-stu-id="d05c9-110">If no **CLUSTER_ID** is displayed for a row, then no similar records were found.</span></span>|  
|<span data-ttu-id="d05c9-111">**RECORD_ID**</span><span class="sxs-lookup"><span data-stu-id="d05c9-111">**RECORD_ID**</span></span>|<span data-ttu-id="d05c9-112">用於識別記錄的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="d05c9-112">A unique identifier used to identify records.</span></span> <span data-ttu-id="d05c9-113">類似於 MDS 儲存機制中儲存的代碼值，它是用來識別記錄的值。</span><span class="sxs-lookup"><span data-stu-id="d05c9-113">Similar to the Code value stored in the MDS repository, it is a value used to identify a record.</span></span> <span data-ttu-id="d05c9-114">每次進行比對時，都會自動產生它。</span><span class="sxs-lookup"><span data-stu-id="d05c9-114">It is generated automatically each time matching takes place.</span></span>|  
|<span data-ttu-id="d05c9-115">**PIVOT_MARK**</span><span class="sxs-lookup"><span data-stu-id="d05c9-115">**PIVOT_MARK**</span></span>|<span data-ttu-id="d05c9-116">與其他記錄比較的任意記錄；它沒有分數值。</span><span class="sxs-lookup"><span data-stu-id="d05c9-116">An arbitrary record that other records are compared to; it does not have a score value.</span></span>|  
|<span data-ttu-id="d05c9-117">**成績**</span><span class="sxs-lookup"><span data-stu-id="d05c9-117">**SCORE**</span></span>|<span data-ttu-id="d05c9-118">表示群組中的記錄與樞紐記錄的相似度。</span><span class="sxs-lookup"><span data-stu-id="d05c9-118">Represents how similar the records in the group are to the pivot record.</span></span> <span data-ttu-id="d05c9-119">此分數由 DQS 決定。</span><span class="sxs-lookup"><span data-stu-id="d05c9-119">This score is determined by DQS.</span></span> <span data-ttu-id="d05c9-120">如果沒有顯示分數，表示記錄是其他記錄的樞紐，或是找不到相符結果。</span><span class="sxs-lookup"><span data-stu-id="d05c9-120">If no score is displayed, either the record is the pivot for other records, or no matches were found.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d05c9-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d05c9-121">See Also</span></span>  
 <span data-ttu-id="d05c9-122">[適用于 Excel 的 MDS 增益集中的資料品質比對](data-quality-matching-in-the-mds-add-in-for-excel.md) </span><span class="sxs-lookup"><span data-stu-id="d05c9-122">[Data Quality Matching in the MDS Add-in for Excel](data-quality-matching-in-the-mds-add-in-for-excel.md) </span></span>  
 <span data-ttu-id="d05c9-123">[符合適用于 Excel&#41;的類似資料 &#40;MDS 增益集](match-similar-data-mds-add-in-for-excel.md) </span><span class="sxs-lookup"><span data-stu-id="d05c9-123">[Match Similar Data &#40;MDS Add-in for Excel&#41;](match-similar-data-mds-add-in-for-excel.md) </span></span>  
 [<span data-ttu-id="d05c9-124">資料比對</span><span class="sxs-lookup"><span data-stu-id="d05c9-124">Data Matching</span></span>](../../data-quality-services/data-matching.md)  
  
  
