---
title: 定義) 的商業智慧 Wizard (局部加總行為 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.biwizard.semiadditivememberdetection.f1
ms.assetid: e57080ba-ce96-40f8-bca7-6701d1725b3c
author: minewiskan
ms.author: owend
ms.openlocfilehash: 5a3c46de038a7e45dcb39805e324260676a03228
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687354"
---
# <a name="define-semiadditive-behavior-business-intelligence-wizard"></a><span data-ttu-id="548cb-102">定義局部加總行為 (商業智慧精靈)</span><span class="sxs-lookup"><span data-stu-id="548cb-102">Define Semiadditive Behavior (Business Intelligence Wizard)</span></span>
  <span data-ttu-id="548cb-103">使用 [定義局部加總行為]\*\*\*\* 頁面，即可啟用或停用量值的局部加總行為。</span><span class="sxs-lookup"><span data-stu-id="548cb-103">Use the **Define Semiadditive Behavior** page to enable or disable semi-additive behavior on measures.</span></span> <span data-ttu-id="548cb-104">局部加總行為會決定 Cube 所包含的維度，將如何在時間維度上進行彙總。</span><span class="sxs-lookup"><span data-stu-id="548cb-104">Semi-additive behavior determines how measures that are contained by a cube are aggregated over a time dimension.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="548cb-105">除了 Standard 版中提供的 LastChild 之外，只有商業智慧或 Enterprise 版中提供局部加總行為。</span><span class="sxs-lookup"><span data-stu-id="548cb-105">With the exception of LastChild which is available in the standard edition, semi-additive behaviors are only available in the business intelligence or enterprise editions.</span></span> <span data-ttu-id="548cb-106">此外，由於局部加總行為只會定義在量值上，而不會定義在維度上，如果此行為之前是從維度設計師啟動，或是以滑鼠右鍵按一下 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中方案總管的某維度來啟動，則此頁面將不會出現在商業智慧精靈中。</span><span class="sxs-lookup"><span data-stu-id="548cb-106">Furthermore, because semiadditive behavior is defined only on measures and not dimensions, you will not find this page in the Business Intelligence Wizard if it was started from Dimension Designer or by right-clicking a dimension in Solution Explorer in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span>  
  
## <a name="options"></a><span data-ttu-id="548cb-107">選項</span><span class="sxs-lookup"><span data-stu-id="548cb-107">Options</span></span>  
 <span data-ttu-id="548cb-108">**關閉局部加總行為**</span><span class="sxs-lookup"><span data-stu-id="548cb-108">**Turn off semiadditive behavior**</span></span>  
 <span data-ttu-id="548cb-109">停用 Cube 所包含之所有量值中的局部加總行為。</span><span class="sxs-lookup"><span data-stu-id="548cb-109">Disables semi-additive behavior in all measures contained by the cube.</span></span>  
  
 <span data-ttu-id="548cb-110">**Wizard 已偵測到包含局部加總 \<dimension name> 成員的帳戶維度。伺服器會根據為每個帳戶類型指定的局部加總行為，來匯總此維度的成員。**</span><span class="sxs-lookup"><span data-stu-id="548cb-110">**The wizard has detected the \<dimension name> account dimension, which contains semiadditive members. The server will aggregate members of this dimension according to the semiadditive behavior specified for each account type.**</span></span>  
 <span data-ttu-id="548cb-111">針對包含局部加總成員的帳戶維度，啟用局部加總行為。</span><span class="sxs-lookup"><span data-stu-id="548cb-111">Enables semi-additive behavior for account dimensions that contain semi-additive members.</span></span> <span data-ttu-id="548cb-112">選取此選項會將參考帳戶維度之量值群組中所有量值的彙總函式設定為 `ByAccount`。</span><span class="sxs-lookup"><span data-stu-id="548cb-112">Selecting this option sets the aggregation function of all measures in measure groups that reference the account dimension to `ByAccount`.</span></span>  
  
 <span data-ttu-id="548cb-113">如需帳戶維度的詳細資訊，請參閱 [建立父子式類型維度的財務帳戶](multidimensional-models/database-dimensions-finance-account-of-parent-child-type.md)。</span><span class="sxs-lookup"><span data-stu-id="548cb-113">For more information about account dimensions, see [Create a Finance Account of parent-child type Dimension](multidimensional-models/database-dimensions-finance-account-of-parent-child-type.md).</span></span>  
  
 <span data-ttu-id="548cb-114">**定義個別成員的局部加總行為**</span><span class="sxs-lookup"><span data-stu-id="548cb-114">**Define semiadditive behavior for individual members**</span></span>  
 <span data-ttu-id="548cb-115">啟用局部加總行為，並為特定量值指定局部加總彙總函式。</span><span class="sxs-lookup"><span data-stu-id="548cb-115">Enables semi-additive behavior and specifies the semi-additive aggregation function for specific measures.</span></span> <span data-ttu-id="548cb-116">彙總函式適用於包含量值之量值群組所參考的所有維度。</span><span class="sxs-lookup"><span data-stu-id="548cb-116">The aggregation function applies to all dimensions that are referenced by the measure group that contains the measure.</span></span>  
  
 <span data-ttu-id="548cb-117">**評估**</span><span class="sxs-lookup"><span data-stu-id="548cb-117">**Measures**</span></span>  
 <span data-ttu-id="548cb-118">顯示 Cube 所包含之量值的名稱。</span><span class="sxs-lookup"><span data-stu-id="548cb-118">Displays the name of a measure contained by the cube.</span></span>  
  
 <span data-ttu-id="548cb-119">**局部加總函數**</span><span class="sxs-lookup"><span data-stu-id="548cb-119">**Semiadditive Function**</span></span>  
 <span data-ttu-id="548cb-120">為選取的量值選取彙總函式。</span><span class="sxs-lookup"><span data-stu-id="548cb-120">Select the aggregation function for the selected measure.</span></span> <span data-ttu-id="548cb-121">下表列出可用的彙總函式。</span><span class="sxs-lookup"><span data-stu-id="548cb-121">The following table lists the aggregation functions that are available.</span></span>  
  
|<span data-ttu-id="548cb-122">值</span><span class="sxs-lookup"><span data-stu-id="548cb-122">Value</span></span>|<span data-ttu-id="548cb-123">描述</span><span class="sxs-lookup"><span data-stu-id="548cb-123">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="548cb-124">**AverageOfChildren**</span><span class="sxs-lookup"><span data-stu-id="548cb-124">**AverageOfChildren**</span></span>|<span data-ttu-id="548cb-125">藉由傳回量值之子系的平均值來進行彙總。</span><span class="sxs-lookup"><span data-stu-id="548cb-125">Aggregated by returning the average of the measure's children.</span></span>|  
|`ByAccount`|<span data-ttu-id="548cb-126">藉由與帳戶維度中屬性之指定帳戶類型相關聯的彙總函式來進行彙總。</span><span class="sxs-lookup"><span data-stu-id="548cb-126">Aggregated by the aggregation function associated with the specified account type of an attribute in an account dimension.</span></span>|  
|`Count`|<span data-ttu-id="548cb-127">使用 `Count` 函數來進行彙總。</span><span class="sxs-lookup"><span data-stu-id="548cb-127">Aggregated using the `Count` function.</span></span>|  
|`DistinctCount`|<span data-ttu-id="548cb-128">使用 `DistinctCount` 函數來進行彙總。</span><span class="sxs-lookup"><span data-stu-id="548cb-128">Aggregated using the `DistinctCount` function.</span></span>|  
|<span data-ttu-id="548cb-129">**FirstChild**</span><span class="sxs-lookup"><span data-stu-id="548cb-129">**FirstChild**</span></span>|<span data-ttu-id="548cb-130">藉由傳回量值在某個時間維度的第一個子成員進行彙總。</span><span class="sxs-lookup"><span data-stu-id="548cb-130">Aggregated by returning the measure's first child member over a time dimension.</span></span>|  
|<span data-ttu-id="548cb-131">**FirstNonEmpty**</span><span class="sxs-lookup"><span data-stu-id="548cb-131">**FirstNonEmpty**</span></span>|<span data-ttu-id="548cb-132">藉由傳回量值在某個時間維度的第一個非空白成員進行彙總。</span><span class="sxs-lookup"><span data-stu-id="548cb-132">Aggregated by returning the measure's first nonempty member over a time dimension.</span></span>|  
|<span data-ttu-id="548cb-133">**LastChild**</span><span class="sxs-lookup"><span data-stu-id="548cb-133">**LastChild**</span></span>|<span data-ttu-id="548cb-134">藉由傳回量值在某個時間維度的最後一個子成員進行彙總。</span><span class="sxs-lookup"><span data-stu-id="548cb-134">Aggregated by returning the measure's last child member over a time dimension.</span></span>|  
|<span data-ttu-id="548cb-135">**LastNonEmpty**</span><span class="sxs-lookup"><span data-stu-id="548cb-135">**LastNonEmpty**</span></span>|<span data-ttu-id="548cb-136">藉由傳回量值在某個時間維度的最後一個非空白成員進行彙總。</span><span class="sxs-lookup"><span data-stu-id="548cb-136">Aggregated by returning the measure's last nonempty member over a time dimension.</span></span>|  
|`Max`|<span data-ttu-id="548cb-137">使用 `Max` 函數來進行彙總。</span><span class="sxs-lookup"><span data-stu-id="548cb-137">Aggregated using the `Max` function.</span></span>|  
|`Min`|<span data-ttu-id="548cb-138">使用 `Min` 函數來進行彙總。</span><span class="sxs-lookup"><span data-stu-id="548cb-138">Aggregated using the `Min` function.</span></span>|  
|<span data-ttu-id="548cb-139">**None**</span><span class="sxs-lookup"><span data-stu-id="548cb-139">**None**</span></span>|<span data-ttu-id="548cb-140">不執行彙總。</span><span class="sxs-lookup"><span data-stu-id="548cb-140">No aggregation performed.</span></span>|  
|`Sum`|<span data-ttu-id="548cb-141">使用 `Sum` 函數來進行彙總。</span><span class="sxs-lookup"><span data-stu-id="548cb-141">Aggregated using the `Sum` function.</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="548cb-142">唯有在選取 [定義個別成員的局部加總行為]\*\*\*\* 之後，才適用於針對此選項所做的選擇。</span><span class="sxs-lookup"><span data-stu-id="548cb-142">Selections made for this option apply only if **Define semiadditive behavior for individual members** is selected.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="548cb-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="548cb-143">See Also</span></span>  
 <span data-ttu-id="548cb-144">[商業智慧 Wizard F1 說明](business-intelligence-wizard-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="548cb-144">[Business Intelligence Wizard F1 Help](business-intelligence-wizard-f1-help.md) </span></span>  
 <span data-ttu-id="548cb-145">[Cube 設計工具 &#40;Analysis Services-多維度資料&#41;](cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="548cb-145">[Cube Designer &#40;Analysis Services - Multidimensional Data&#41;](cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="548cb-146">維度設計師 &#40;Analysis Services 多維資料&#41;</span><span class="sxs-lookup"><span data-stu-id="548cb-146">Dimension Designer &#40;Analysis Services - Multidimensional Data&#41;</span></span>](dimension-designer-analysis-services-multidimensional-data.md)  
  
  
