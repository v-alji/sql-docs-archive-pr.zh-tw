---
title: 適用於 Excel 的 MDS 增益集中的資料品質比對 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: be78d051-0d56-46d3-bb89-327e218dadd6
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 037e535452e7f19644837e0cbcfd02efec5422b6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599038"
---
# <a name="data-quality-matching-in-the-mds-add-in-for-excel"></a><span data-ttu-id="de97d-102">適用於 Excel 的 MDS 增益集中的資料品質比對</span><span class="sxs-lookup"><span data-stu-id="de97d-102">Data Quality Matching in the MDS Add-in for Excel</span></span>
  <span data-ttu-id="de97d-103">經過一段時間後，您需要將更多的資料加入至 MDS 儲存機制。</span><span class="sxs-lookup"><span data-stu-id="de97d-103">Over time, you will want to add more data to the MDS repository.</span></span> <span data-ttu-id="de97d-104">在新增資料之前，比較新資料與已在 MDS 中受控的資料，有助於確保不會新增重複或不精準的資料。</span><span class="sxs-lookup"><span data-stu-id="de97d-104">Before adding data, it can be useful to compare the new data to the data that's already managed in MDS, to ensure you are not adding duplicate or inaccurate data.</span></span>  
  
 <span data-ttu-id="de97d-105">MDS [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)] 使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的 Data Quality Services (DQS) 功能來比較相似的資料。</span><span class="sxs-lookup"><span data-stu-id="de97d-105">The MDS [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)] uses the Data Quality Services (DQS) feature of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to match data that's similar.</span></span> <span data-ttu-id="de97d-106">當您使用增益集的比對功能時，相似記錄會群組在一起，而且會顯示代表結果精確度的分數。</span><span class="sxs-lookup"><span data-stu-id="de97d-106">When you use the matching functionality in the Add-in, similar records are grouped together and a score that represents the accuracy of the result is displayed.</span></span> <span data-ttu-id="de97d-107">如需有關 DQS 所提供之比對功能的詳細資訊，請參閱＜ [Data Matching](../../data-quality-services/data-matching.md)＞。</span><span class="sxs-lookup"><span data-stu-id="de97d-107">For more information about the matching functionality provided by DQS, see [Data Matching](../../data-quality-services/data-matching.md).</span></span>  
  
## <a name="workflow-for-data-quality-matching"></a><span data-ttu-id="de97d-108">資料品質比對的工作流程</span><span class="sxs-lookup"><span data-stu-id="de97d-108">Workflow for Data Quality Matching</span></span>  
 <span data-ttu-id="de97d-109">搭配使用 DQS 與 MDS [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]時，請使用下列工作流程：</span><span class="sxs-lookup"><span data-stu-id="de97d-109">When using DQS with the MDS [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], use the following workflow:</span></span>  
  
1.  <span data-ttu-id="de97d-110">擷取 MDS 管理之資料的清單，並將它與不在 MDS 中管理之資料的清單結合。</span><span class="sxs-lookup"><span data-stu-id="de97d-110">Retrieve a list of MDS-managed data and combine it with a list that is not managed in MDS.</span></span> <span data-ttu-id="de97d-111">如需詳細資訊，請參閱 [結合資料 &#40;適用於 Excel 的 MDS 增益集&#41;](combine-data-mds-add-in-for-excel.md)＞。</span><span class="sxs-lookup"><span data-stu-id="de97d-111">For more information, see [Combine Data &#40;MDS Add-in for Excel&#41;](combine-data-mds-add-in-for-excel.md).</span></span>  
  
2.  <span data-ttu-id="de97d-112">使用 DQS 知識，比較合併清單中的資料。</span><span class="sxs-lookup"><span data-stu-id="de97d-112">Use DQS knowledge to compare the data in the combined list.</span></span> <span data-ttu-id="de97d-113">如需詳細資訊，請參閱 [比對相似資料 &#40;適用於 Excel 的 MDS 增益集&#41;](match-similar-data-mds-add-in-for-excel.md)＞。</span><span class="sxs-lookup"><span data-stu-id="de97d-113">For more information, see [Match Similar Data &#40;MDS Add-in for Excel&#41;](match-similar-data-mds-add-in-for-excel.md).</span></span>  
  
3.  <span data-ttu-id="de97d-114">若要檢視 DQS 所找到之相似度的詳細資料，請顯示詳細資料資料行。</span><span class="sxs-lookup"><span data-stu-id="de97d-114">To view more details about the similarities found by DQS, show the detail columns.</span></span>  
  
4.  <span data-ttu-id="de97d-115">瀏覽結果，判斷哪些資料應該加入至 MDS 儲存機制，哪些資料是重複的。</span><span class="sxs-lookup"><span data-stu-id="de97d-115">Go through the results and determine which data should be added to the MDS repository and which data is duplicated.</span></span>  
  
5.  <span data-ttu-id="de97d-116">將新的和/或已更新的資料發行到 MDS 儲存機制。</span><span class="sxs-lookup"><span data-stu-id="de97d-116">Publish the new and/or updated data to the MDS repository.</span></span>  
  
## <a name="knowledge-bases"></a><span data-ttu-id="de97d-117">知識庫</span><span class="sxs-lookup"><span data-stu-id="de97d-117">Knowledge Bases</span></span>  
 <span data-ttu-id="de97d-118">增益集所提供的比對結果是以 DQS 知識庫為基礎。</span><span class="sxs-lookup"><span data-stu-id="de97d-118">The matching results provided in the Add-in are based on a DQS knowledge base.</span></span>  
  
-   <span data-ttu-id="de97d-119">安裝 DQS 時，會建立預設知識庫 (DQS 資料)。</span><span class="sxs-lookup"><span data-stu-id="de97d-119">The default knowledge base (DQS Data) is created when DQS is installed.</span></span> <span data-ttu-id="de97d-120">若您選擇使用預設知識庫 (而沒有透過 Data Quality Client 將比對原則加入預設知識庫)，您必須將工作表中的資料行對應至知識庫的網域，然後再指派權數值給您所選擇的網域。</span><span class="sxs-lookup"><span data-stu-id="de97d-120">If you choose to use the default knowledge base (without adding a matching policy to the default knowledge base in the Data Quality Client), you must map columns in the worksheet to domains in the knowledge base, and then assign a weight value to the domains you choose.</span></span>  
  
-   <span data-ttu-id="de97d-121">您可以使用 Data Quality Client 建立含有比對原則的新知識庫，或是將比對原則加入預設知識庫。</span><span class="sxs-lookup"><span data-stu-id="de97d-121">You can use the Data Quality Client to create a new knowledge base with a matching policy, or to add a matching policy to the default knowledge base.</span></span> <span data-ttu-id="de97d-122">在此情況下，加權值是由您已建立的比對原則所決定，您只需要將資料行對應至定義域。</span><span class="sxs-lookup"><span data-stu-id="de97d-122">In this case, the weight values are determined by the matching policy you already created and you need only to map the columns to the domains.</span></span> <span data-ttu-id="de97d-123">如需相關資訊，請參閱 [建立訂閱](../../data-quality-services/create-a-matching-policy.md)。</span><span class="sxs-lookup"><span data-stu-id="de97d-123">For more information, see [Create a Matching Policy](../../data-quality-services/create-a-matching-policy.md).</span></span>  
  
 <span data-ttu-id="de97d-124">如需有關知識庫的詳細資訊，請參閱＜ [DQS Knowledge Bases and Domains](../../data-quality-services/dqs-knowledge-bases-and-domains.md)＞。</span><span class="sxs-lookup"><span data-stu-id="de97d-124">For more information about knowledge bases, see [DQS Knowledge Bases and Domains](../../data-quality-services/dqs-knowledge-bases-and-domains.md).</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="de97d-125">相關工作</span><span class="sxs-lookup"><span data-stu-id="de97d-125">Related Tasks</span></span>  
  
|<span data-ttu-id="de97d-126">工作描述</span><span class="sxs-lookup"><span data-stu-id="de97d-126">Task Description</span></span>|<span data-ttu-id="de97d-127">主題</span><span class="sxs-lookup"><span data-stu-id="de97d-127">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="de97d-128">結合外部資料與 MDS 管理的資料，準備進行比較。</span><span class="sxs-lookup"><span data-stu-id="de97d-128">Combine external data with MDS-managed data in preparation to compare it.</span></span>|[<span data-ttu-id="de97d-129">結合資料 &#40;適用於 Excel 的 MDS 增益集&#41;</span><span class="sxs-lookup"><span data-stu-id="de97d-129">Combine Data &#40;MDS Add-in for Excel&#41;</span></span>](combine-data-mds-add-in-for-excel.md)|  
|<span data-ttu-id="de97d-130">使用 DQS 知識來尋找資料中的相似度。</span><span class="sxs-lookup"><span data-stu-id="de97d-130">Use DQS knowledge to find similarities in your data.</span></span>|[<span data-ttu-id="de97d-131">比對相似資料 &#40;適用於 Excel 的 MDS 增益集&#41;</span><span class="sxs-lookup"><span data-stu-id="de97d-131">Match Similar Data &#40;MDS Add-in for Excel&#41;</span></span>](match-similar-data-mds-add-in-for-excel.md)|  
  
## <a name="related-content"></a><span data-ttu-id="de97d-132">相關內容</span><span class="sxs-lookup"><span data-stu-id="de97d-132">Related Content</span></span>  
  
-   [<span data-ttu-id="de97d-133">發行資料 &#40;適用于 Excel 的 MDS 增益集&#41;</span><span class="sxs-lookup"><span data-stu-id="de97d-133">Publishing Data &#40;MDS Add-in for Excel&#41;</span></span>](overview-importing-data-from-excel-mds-add-in-for-excel.md)  
  
-   [<span data-ttu-id="de97d-134">資料比對</span><span class="sxs-lookup"><span data-stu-id="de97d-134">Data Matching</span></span>](../../data-quality-services/data-matching.md)  
  
  
