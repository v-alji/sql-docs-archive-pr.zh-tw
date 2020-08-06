---
title: 定義局部加總行為 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- semiadditive
- Business Intelligence enhancements [Analysis Services], semiadditive behavior
- measures [Analysis Services], semiadditive
ms.assetid: b25726bc-728b-4601-ad87-9015c39dc615
author: minewiskan
ms.author: owend
ms.openlocfilehash: 9c2028c350046fdcc9f98bcd0f0612d6a91ccabb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596384"
---
# <a name="define-semiadditive-behavior"></a><span data-ttu-id="9dfee-102">定義局部加總行為</span><span class="sxs-lookup"><span data-stu-id="9dfee-102">Define Semiadditive Behavior</span></span>
  <span data-ttu-id="9dfee-103">在許多商務狀況中，經常見到局部加總量值並未跨所有維度一致地彙總。</span><span class="sxs-lookup"><span data-stu-id="9dfee-103">Semiadditive measures, which do not uniformly aggregate across all dimensions, are very common in many business scenarios.</span></span> <span data-ttu-id="9dfee-104">每個以不同時間之結餘快照集為基礎的 Cube 都會出現這個問題。</span><span class="sxs-lookup"><span data-stu-id="9dfee-104">Every cube that is based on snapshots of balances over time exhibits this problem.</span></span> <span data-ttu-id="9dfee-105">您可以在處理安全性、帳戶結餘、預算、人力資源、保險政策和理賠、以及其他許多商務領域的應用程式中發現這些快照集。</span><span class="sxs-lookup"><span data-stu-id="9dfee-105">You can find these snapshots in applications dealing with securities, account balances, budgeting, human resources, insurance policies and claims, and many other business domains.</span></span>  
  
 <span data-ttu-id="9dfee-106">將局部加總行為加入 Cube，以定義個別量值或帳戶類型屬性成員的彙總方法。</span><span class="sxs-lookup"><span data-stu-id="9dfee-106">Add semiadditive behavior to a cube to define an aggregation method for individual measures or members of the account type attribute.</span></span> <span data-ttu-id="9dfee-107">如果 Cube 包含帳戶維度，您可以根據帳戶類型自動設定局部加總行為。</span><span class="sxs-lookup"><span data-stu-id="9dfee-107">If the cube contains an account dimension, you can automatically set semiadditive behavior based on the account type.</span></span>  
  
 <span data-ttu-id="9dfee-108">若要加入局部加總行為，請在 Cube 設計師中開啟 Cube，然後從 [Cube] 功能表中選擇 [加入商業智慧]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="9dfee-108">To add semiadditive behavior, open a cube in Cube Designer and choose **Add Business Intelligence** from the Cube menu.</span></span> <span data-ttu-id="9dfee-109">請在 [商業智慧精靈] 中，選取 [選擇增強功能]\*\*\*\* 頁面上的 [定義局部加總行為]\*\*\*\* 選項。</span><span class="sxs-lookup"><span data-stu-id="9dfee-109">In the Business Intelligence Wizard, select the **Define semiadditive behavior** option on the **Choose Enhancement** page.</span></span> <span data-ttu-id="9dfee-110">然後，此精靈會引導您逐步完成識別具有局部加總行為的量值。</span><span class="sxs-lookup"><span data-stu-id="9dfee-110">This wizard then guides you through the steps of identifying which measures have semiadditive behavior.</span></span>  
  
 <span data-ttu-id="9dfee-111">除了 Standard 版中提供的 LastChild 之外，只有商業智慧或 Enterprise 版中提供局部加總行為。</span><span class="sxs-lookup"><span data-stu-id="9dfee-111">With the exception of LastChild which is available in the standard edition, semi-additive behaviors are only available in the business intelligence or enterprise editions.</span></span>  
  
## <a name="define-semiadditive-behavior"></a><span data-ttu-id="9dfee-112">定義局部加總行為</span><span class="sxs-lookup"><span data-stu-id="9dfee-112">Define Semiadditive Behavior</span></span>  
 <span data-ttu-id="9dfee-113">在精靈的 [定義局部加總行為]\*\*\*\* 頁面上，選取下列其中一個選項來選擇如何定義局部加總：</span><span class="sxs-lookup"><span data-stu-id="9dfee-113">On the **Define Semiadditive Behavior** page of the wizard, you select how to define semiadditivity by selecting one of the following options:</span></span>  
  
 <span data-ttu-id="9dfee-114">**關閉局部加總行為**</span><span class="sxs-lookup"><span data-stu-id="9dfee-114">**Turn off semiadditive behavior**</span></span>  
 <span data-ttu-id="9dfee-115">從先前定義局部加總行為的 Cube 中移除局部加總行為。</span><span class="sxs-lookup"><span data-stu-id="9dfee-115">Removes semiadditive behavior from a cube in which semiadditive behavior was previously defined.</span></span> <span data-ttu-id="9dfee-116">如果量值設成下列任何彙總函式類型，此選取項目會將其重設為 `SUM`：</span><span class="sxs-lookup"><span data-stu-id="9dfee-116">This selection resets a measure to `SUM` if it is set to any of the following aggregation function types:</span></span>  
  
-   <span data-ttu-id="9dfee-117">依帳戶</span><span class="sxs-lookup"><span data-stu-id="9dfee-117">By Account</span></span>  
  
-   <span data-ttu-id="9dfee-118">子系的平均</span><span class="sxs-lookup"><span data-stu-id="9dfee-118">Average of Children</span></span>  
  
-   <span data-ttu-id="9dfee-119">第一個子系</span><span class="sxs-lookup"><span data-stu-id="9dfee-119">First Child</span></span>  
  
-   <span data-ttu-id="9dfee-120">最後一個子系</span><span class="sxs-lookup"><span data-stu-id="9dfee-120">Last Child</span></span>  
  
-   <span data-ttu-id="9dfee-121">最後一個非空白子系</span><span class="sxs-lookup"><span data-stu-id="9dfee-121">Last Nonempty Child</span></span>  
  
-   <span data-ttu-id="9dfee-122">第一個非空白子系</span><span class="sxs-lookup"><span data-stu-id="9dfee-122">First Nonempty Child</span></span>  
  
-   <span data-ttu-id="9dfee-123">無</span><span class="sxs-lookup"><span data-stu-id="9dfee-123">None</span></span>  
  
 <span data-ttu-id="9dfee-124">此選項不會變更具有一般彙總函式的量值： `Sum` 、 `Min` 、 `Max` 、 `Count` 或 `Distinct``Count` 。</span><span class="sxs-lookup"><span data-stu-id="9dfee-124">This option does not change measures with a regular aggregation function: `Sum`, `Min`, `Max`, `Count`, or `Distinct``Count`.</span></span>  
  
 <span data-ttu-id="9dfee-125">**此 wizard 偵測到「帳戶」帳戶維度，其中包含局部加總成員。伺服器會根據為每個帳戶類型指定的局部加總行為，來匯總此維度的成員。**</span><span class="sxs-lookup"><span data-stu-id="9dfee-125">**The wizard has detected the 'Account" account dimension, which contains semiadditive members. The server will aggregate members of this dimension according to the semiadditive behavior specified for each account type.**</span></span>  
 <span data-ttu-id="9dfee-126">讓系統將帳戶類型維度所建立維度之量值群組中的所有量值設定為「依帳戶」彙總函式，而且伺服器將會根據每一個帳戶類型所指定之局部加總行為來彙總此維度的成員。</span><span class="sxs-lookup"><span data-stu-id="9dfee-126">Causes the system to set all measures from a measure group dimensioned by an Account type dimension to the By Account aggregation function and the server will aggregate members of the dimension according to the semiadditive behavior specified for each account type.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9dfee-127">依預設，如果精靈偵測到帳戶類型維度，這個選項為已選取。</span><span class="sxs-lookup"><span data-stu-id="9dfee-127">This option is selected by default if the wizard detects an Account type dimension.</span></span>  
  
 <span data-ttu-id="9dfee-128">**定義個別量值的局部加總行為**</span><span class="sxs-lookup"><span data-stu-id="9dfee-128">**Define semiadditive behavior for individual measures**</span></span>  
 <span data-ttu-id="9dfee-129">個別選取每個量值的局部加總行為。</span><span class="sxs-lookup"><span data-stu-id="9dfee-129">Selects the semiadditive behavior of each measure individually.</span></span> <span data-ttu-id="9dfee-130">預設值為 `SUM` (完整加總)。</span><span class="sxs-lookup"><span data-stu-id="9dfee-130">The default setting is `SUM` (fully additive).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9dfee-131">依預設，如果精靈沒有偵測到帳戶類型維度，這個選項為已選取。</span><span class="sxs-lookup"><span data-stu-id="9dfee-131">This option is selected by default if the wizard does not detect an Account type dimension.</span></span>  
  
 <span data-ttu-id="9dfee-132">針對每個量值，您可以從下表描述之局部加總功能的類型進行選取。</span><span class="sxs-lookup"><span data-stu-id="9dfee-132">For each measure, you can select from the types of semiadditive functionality described in the following table.</span></span>  
  
|<span data-ttu-id="9dfee-133">局部加總函數</span><span class="sxs-lookup"><span data-stu-id="9dfee-133">Semiadditive function</span></span>|<span data-ttu-id="9dfee-134">描述</span><span class="sxs-lookup"><span data-stu-id="9dfee-134">Description</span></span>|  
|---------------------------|-----------------|  
|<span data-ttu-id="9dfee-135">子系的平均</span><span class="sxs-lookup"><span data-stu-id="9dfee-135">Average of Children</span></span>|<span data-ttu-id="9dfee-136">成員的彙總是其子系的平均。</span><span class="sxs-lookup"><span data-stu-id="9dfee-136">The aggregation of a member is the average of its children.</span></span>|  
|<span data-ttu-id="9dfee-137">ByAccount</span><span class="sxs-lookup"><span data-stu-id="9dfee-137">ByAccount</span></span>|<span data-ttu-id="9dfee-138">系統會讀取帳戶類型所指定的局部加總行為。</span><span class="sxs-lookup"><span data-stu-id="9dfee-138">The system reads the semiadditive behavior specified for the account type.</span></span>|  
|<span data-ttu-id="9dfee-139">計數</span><span class="sxs-lookup"><span data-stu-id="9dfee-139">Count</span></span>|<span data-ttu-id="9dfee-140">此彙總為成員的計數。</span><span class="sxs-lookup"><span data-stu-id="9dfee-140">The aggregation is a count of members.</span></span>|  
|<span data-ttu-id="9dfee-141">Distinct Count</span><span class="sxs-lookup"><span data-stu-id="9dfee-141">Distinct Count</span></span>|<span data-ttu-id="9dfee-142">此彙總為唯一成員的計數。</span><span class="sxs-lookup"><span data-stu-id="9dfee-142">The aggregation is a count of unique members.</span></span>|  
|<span data-ttu-id="9dfee-143">第一個子系</span><span class="sxs-lookup"><span data-stu-id="9dfee-143">First Child</span></span>|<span data-ttu-id="9dfee-144">成員值判斷為時間維度第一個子系的值。</span><span class="sxs-lookup"><span data-stu-id="9dfee-144">The member value is evaluated as the value of its first child along the time dimension.</span></span>|  
|<span data-ttu-id="9dfee-145">FirstNonEmpty</span><span class="sxs-lookup"><span data-stu-id="9dfee-145">FirstNonEmpty</span></span>|<span data-ttu-id="9dfee-146">成員值判斷為包含資料之時間維度第一個子系的值。</span><span class="sxs-lookup"><span data-stu-id="9dfee-146">The member value is evaluated as the value of its first child along the time dimension that contains data.</span></span>|  
|<span data-ttu-id="9dfee-147">LastChild</span><span class="sxs-lookup"><span data-stu-id="9dfee-147">LastChild</span></span>|<span data-ttu-id="9dfee-148">成員值判斷為時間維度最後一個子系的值。</span><span class="sxs-lookup"><span data-stu-id="9dfee-148">The member value is evaluated as the value of its last child along the time dimension.</span></span>|  
|<span data-ttu-id="9dfee-149">LastNonEmpty</span><span class="sxs-lookup"><span data-stu-id="9dfee-149">LastNonEmpty</span></span>|<span data-ttu-id="9dfee-150">成員值判斷為包含資料之時間維度最後一個子系的值。</span><span class="sxs-lookup"><span data-stu-id="9dfee-150">The member value is evaluated as the value of its last child along the time dimension that contains data.</span></span>|  
|<span data-ttu-id="9dfee-151">最大值</span><span class="sxs-lookup"><span data-stu-id="9dfee-151">Max</span></span>|<span data-ttu-id="9dfee-152">套用標準最大彙總函式。</span><span class="sxs-lookup"><span data-stu-id="9dfee-152">The standard maximum aggregation function is applied.</span></span>|  
|<span data-ttu-id="9dfee-153">最小值</span><span class="sxs-lookup"><span data-stu-id="9dfee-153">Min</span></span>|<span data-ttu-id="9dfee-154">套用標準最小彙總函式。</span><span class="sxs-lookup"><span data-stu-id="9dfee-154">The standard minimum aggregation function is applied.</span></span>|  
|<span data-ttu-id="9dfee-155">無</span><span class="sxs-lookup"><span data-stu-id="9dfee-155">None</span></span>|<span data-ttu-id="9dfee-156">不套用任何彙總。</span><span class="sxs-lookup"><span data-stu-id="9dfee-156">No aggregation is applied.</span></span>|  
|<span data-ttu-id="9dfee-157">加總</span><span class="sxs-lookup"><span data-stu-id="9dfee-157">Sum</span></span>|<span data-ttu-id="9dfee-158">套用標準總和函數。</span><span class="sxs-lookup"><span data-stu-id="9dfee-158">The standard summation function is applied.</span></span>|  
  
 <span data-ttu-id="9dfee-159">當精靈完成時，會覆寫全部現有的局部加總行為。</span><span class="sxs-lookup"><span data-stu-id="9dfee-159">Any existing semiadditive behavior is overwritten when you complete the wizard.</span></span>  
  
  
