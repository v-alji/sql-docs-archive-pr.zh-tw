---
title: 使用商業智慧 Wizard 定義時間智慧計算 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- period over period growth [Analysis Services]
- parallel period comparisons [Analysis Services]
- Business Intelligence enhancements [Analysis Services], time intelligence
- time views [Analysis Services]
- hierarchies [Analysis Services], time
- time periods [Analysis Services]
- moving averages
- time [Analysis Services]
- period to date [Analysis Services]
- calculations [Analysis Services], time
- time hierarchies [Analysis Services]
- time intelligence [Analysis Services]
ms.assetid: be36e8fc-f46e-4553-8623-b27d695c330b
author: minewiskan
ms.author: owend
ms.openlocfilehash: 222efb572c227e6a8ca3d1e2295b662cb586184a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592304"
---
# <a name="define-time-intelligence-calculations-using-the-business-intelligence-wizard"></a><span data-ttu-id="6708c-102">使用商業智慧精靈定義時間智慧計算</span><span class="sxs-lookup"><span data-stu-id="6708c-102">Define Time Intelligence Calculations using the Business Intelligence Wizard</span></span>
  <span data-ttu-id="6708c-103">時間智慧增強功能是一種 Cube 增強功能，用於將時間計算 (時間檢視) 加入至選取的階層。</span><span class="sxs-lookup"><span data-stu-id="6708c-103">The time intelligence enhancement is a cube enhancement that adds time calculations (or time views) to a selected hierarchy.</span></span> <span data-ttu-id="6708c-104">此增強功能支援下列計算類別目錄：</span><span class="sxs-lookup"><span data-stu-id="6708c-104">This enhancement supports the following categories of calculations:</span></span>  
  
-   <span data-ttu-id="6708c-105">至今的期間數。</span><span class="sxs-lookup"><span data-stu-id="6708c-105">Period to date.</span></span>  
  
-   <span data-ttu-id="6708c-106">期間的成長。</span><span class="sxs-lookup"><span data-stu-id="6708c-106">Period over period growth.</span></span>  
  
-   <span data-ttu-id="6708c-107">移動平均。</span><span class="sxs-lookup"><span data-stu-id="6708c-107">Moving averages.</span></span>  
  
-   <span data-ttu-id="6708c-108">平行期間比較。</span><span class="sxs-lookup"><span data-stu-id="6708c-108">Parallel period comparisons.</span></span>  
  
 <span data-ttu-id="6708c-109">您將時間智慧套用到具有時間維度的 Cube。</span><span class="sxs-lookup"><span data-stu-id="6708c-109">You apply time intelligence to cubes that have a time dimension.</span></span> <span data-ttu-id="6708c-110">(時間維度是 `Type` 屬性設成 `Time` 的維度)。</span><span class="sxs-lookup"><span data-stu-id="6708c-110">(A time dimension is a dimension whose `Type` property is set to `Time`).</span></span> <span data-ttu-id="6708c-111">另外，該維度時間屬性的， `Type` 屬性，也必須有適當的設定 (例如，年份或月份)。</span><span class="sxs-lookup"><span data-stu-id="6708c-111">Additionally, the time attributes of that dimension must also have the appropriate setting (such as, Years or Months) for their `Type` property.</span></span> <span data-ttu-id="6708c-112">如果您使用維度精靈來建立時間維度，維度及其屬性的 `Type` 屬性都會正確地設定。</span><span class="sxs-lookup"><span data-stu-id="6708c-112">The `Type` property of both the dimension and its attributes will be set correctly if you use the Dimension Wizard to create the time dimension.</span></span>  
  
 <span data-ttu-id="6708c-113">若要將時間智慧加入 Cube，您可使用 [商業智慧精靈]，並於 [選擇增強功能]\*\*\*\* 頁面上選取 [定義時間智慧]\*\*\*\* 選項。</span><span class="sxs-lookup"><span data-stu-id="6708c-113">To add time intelligence to a cube, you use the Business Intelligence Wizard, and select the **Define time intelligence** option on the **Choose Enhancement** page.</span></span> <span data-ttu-id="6708c-114">然後，此精靈會引導您逐步完成選取要加入時間智慧的階層，並在將會套用時間智慧的階層內指定成員。</span><span class="sxs-lookup"><span data-stu-id="6708c-114">This wizard then guides you through the steps of selecting a hierarchy to which you are adding time intelligence and specifying which members in the hierarchy will have time intelligence applied to them.</span></span> <span data-ttu-id="6708c-115">在 wizard 的最後一頁，您可以看到將對資料庫進行的變更， [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 以加入選取的時間智慧。</span><span class="sxs-lookup"><span data-stu-id="6708c-115">On the last page of the wizard, you can see the changes that will be made to the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database to add the selected time intelligence.</span></span>  
  
## <a name="selecting-a-time-hierarchy"></a><span data-ttu-id="6708c-116">選取時間階層</span><span class="sxs-lookup"><span data-stu-id="6708c-116">Selecting a Time Hierarchy</span></span>  
 <span data-ttu-id="6708c-117">在 [選擇目標階層與計算]\*\*\*\* 頁面上，您可以選取時間增強功能套用的時間階層。</span><span class="sxs-lookup"><span data-stu-id="6708c-117">On the **Choose Target Hierarchy and Calculations** page, you select the time hierarchy to which the time enhancement applies.</span></span> <span data-ttu-id="6708c-118">每一次執行商業智慧精靈時，您只可以套用時間增強功能到一個時間階層。</span><span class="sxs-lookup"><span data-stu-id="6708c-118">You can apply the time enhancement to only one time hierarchy every time that you run the Business Intelligence Wizard.</span></span> <span data-ttu-id="6708c-119">如果您要套用增強功能到多個時間階層，就要再次執行精靈。</span><span class="sxs-lookup"><span data-stu-id="6708c-119">If you want to apply the enhancement to more than one time hierarchy, you run the wizard again.</span></span>  
  
 <span data-ttu-id="6708c-120">選取時間階層後，在 [可用的時間計算]\*\*\*\* 清單中，您可選取套用至階層的計算。</span><span class="sxs-lookup"><span data-stu-id="6708c-120">After you select a time hierarchy, in the **Available time calculations** list, you select the calculations that apply to the hierarchy.</span></span> <span data-ttu-id="6708c-121">根據階層中的層級與針對每個層級之屬性的 `Type` 屬性設定，決定列出的計算。</span><span class="sxs-lookup"><span data-stu-id="6708c-121">The calculations that are listed depend on the levels in the hierarchy, and on the `Type` property setting for the attribute for each level.</span></span> <span data-ttu-id="6708c-122">例如，年度階層支援年初至今與年的成長，但是季階層則否。</span><span class="sxs-lookup"><span data-stu-id="6708c-122">For example, a Years hierarchy supports Year to Date and Year Over Year Growth, but a Quarters hierarchy does not.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6708c-123">Timeintelligence.xml 範本檔案定義 [可用的時間計算]\*\*\*\* 中列出的時間計算。</span><span class="sxs-lookup"><span data-stu-id="6708c-123">The Timeintelligence.xml template file defines the time calculations that are listed in **Available time calculations**.</span></span> <span data-ttu-id="6708c-124">如果列出的計算不符合您的需求，您可以變更現有的計算，或將新的計算加入 Timeintelligence.xml 檔案中。</span><span class="sxs-lookup"><span data-stu-id="6708c-124">If the listed calculations do not meet your needs, you can either change the existing calculations or add new calculations to the Timeintelligence.xml file.</span></span>  
  
> [!TIP]  
>  <span data-ttu-id="6708c-125">若要檢視計算的描述，請使用向上與向下箭號以反白顯示該計算。</span><span class="sxs-lookup"><span data-stu-id="6708c-125">To view a description for a calculation, use the up and down arrows to highlight that calculation.</span></span>  
  
## <a name="apply-time-views-to-members"></a><span data-ttu-id="6708c-126">將時間檢視套用至成員</span><span class="sxs-lookup"><span data-stu-id="6708c-126">Apply Time Views to Members</span></span>  
 <span data-ttu-id="6708c-127">在 [定義計算範圍]\*\*\*\* 頁面上，您可以指定要套用新時間檢視的成員。</span><span class="sxs-lookup"><span data-stu-id="6708c-127">On the **Define Scope of Calculations** page, you specify the members to which the new time views apply.</span></span> <span data-ttu-id="6708c-128">您可將新時間檢視套用到下列物件之一：</span><span class="sxs-lookup"><span data-stu-id="6708c-128">You can apply the new time views to one of the following objects:</span></span>  
  
-   <span data-ttu-id="6708c-129">**帳戶維度的成員**：在 [定義計算範圍]\*\*\*\* 頁面上，[可用的量值]\*\*\*\* 清單中包含帳戶維度。</span><span class="sxs-lookup"><span data-stu-id="6708c-129">**Members of an account dimension** On the **Define Scope of Calculations** page, the **Available measures** list includes account dimensions.</span></span> <span data-ttu-id="6708c-130">帳戶維度之 `Type` 屬性設定成 `Accounts`。</span><span class="sxs-lookup"><span data-stu-id="6708c-130">Account dimensions have their `Type` properties set to `Accounts`.</span></span> <span data-ttu-id="6708c-131">如果您有帳戶維度，但該維度並未在 [可用的量值]\*\*\*\* 清單中顯示，您可以使用 [商業智慧精靈] 將帳戶智慧套用至該維度。</span><span class="sxs-lookup"><span data-stu-id="6708c-131">If you have an accounts dimension but that dimension does not appear in the **Available measures** list, you can use the Business Intelligence Wizard to apply the account intelligence to that dimension.</span></span> <span data-ttu-id="6708c-132">如需詳細資訊，請參閱 [將帳戶智慧加入至維度中](bi-wizard-add-account-intelligence-to-a-dimension.md)。</span><span class="sxs-lookup"><span data-stu-id="6708c-132">For more information, see [Add Account Intelligence to a Dimension](bi-wizard-add-account-intelligence-to-a-dimension.md).</span></span>  
  
-   <span data-ttu-id="6708c-133">**量值** ：您可以指定時間檢視套用的量值，而非指定帳戶維度。</span><span class="sxs-lookup"><span data-stu-id="6708c-133">**Measures** Instead of specifying an account dimension, you can specify the measures to which the time views apply.</span></span> <span data-ttu-id="6708c-134">在此狀況下，請選取所選的時間計算套用的檢視。</span><span class="sxs-lookup"><span data-stu-id="6708c-134">In this case, select the views to which selected time calculations apply.</span></span> <span data-ttu-id="6708c-135">例如，資產和負債是年度至今的資料；因此，您不會將年度至今計算套用到資產或負債量值。</span><span class="sxs-lookup"><span data-stu-id="6708c-135">For example, assets and liabilities are year-to-date data; therefore, you do not apply a Year-to-Date calculation to assets or liabilities measures.</span></span>  
  
## <a name="viewing-the-time-intelligence-enhancement"></a><span data-ttu-id="6708c-136">檢視時間智慧增強功能</span><span class="sxs-lookup"><span data-stu-id="6708c-136">Viewing the Time Intelligence Enhancement</span></span>  
 <span data-ttu-id="6708c-137">在 [商業智慧精靈] 的最後一頁，您可以檢視將會對 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 資料庫進行的變更。</span><span class="sxs-lookup"><span data-stu-id="6708c-137">On the final page of the Business Intelligence Wizard, you can view the changes that will be made to the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database.</span></span> <span data-ttu-id="6708c-138">針對時間智慧增強功能，精靈會變更選取的時間維度、關聯的資料來源檢視以及關聯的 Cube，如下表所述。</span><span class="sxs-lookup"><span data-stu-id="6708c-138">For a time intelligence enhancement, the wizard will change the selected time dimension, associated data source view, and associated cube as described in the following table.</span></span>  
  
|<span data-ttu-id="6708c-139">Object</span><span class="sxs-lookup"><span data-stu-id="6708c-139">Object</span></span>|<span data-ttu-id="6708c-140">變更</span><span class="sxs-lookup"><span data-stu-id="6708c-140">Change</span></span>|  
|------------|------------|  
|<span data-ttu-id="6708c-141">時間維度</span><span class="sxs-lookup"><span data-stu-id="6708c-141">Time dimension</span></span>|<span data-ttu-id="6708c-142">針對每個計算 (或檢視) 加入屬性。</span><span class="sxs-lookup"><span data-stu-id="6708c-142">Adds an attribute for each calculation (or view).</span></span>|  
|<span data-ttu-id="6708c-143">資料來源檢視</span><span class="sxs-lookup"><span data-stu-id="6708c-143">Data source view</span></span>|<span data-ttu-id="6708c-144">針對時間維度中的每個新屬性，在時間資料表內加入導出資料行。</span><span class="sxs-lookup"><span data-stu-id="6708c-144">Adds a calculated column in the time table for each new attribute in the time dimension.</span></span>|  
|<span data-ttu-id="6708c-145">Cube</span><span class="sxs-lookup"><span data-stu-id="6708c-145">Cube</span></span>|<span data-ttu-id="6708c-146">加入定義多維度運算式 (MDX) 程式碼的導出成員以執行計算。</span><span class="sxs-lookup"><span data-stu-id="6708c-146">Adds a calculated member that defines the Multidimensional Expressions (MDX) code to perform the calculation.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6708c-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6708c-147">See Also</span></span>  
 [<span data-ttu-id="6708c-148">建立導出成員</span><span class="sxs-lookup"><span data-stu-id="6708c-148">Create Calculated Members</span></span>](create-calculated-members.md)  
  
  
