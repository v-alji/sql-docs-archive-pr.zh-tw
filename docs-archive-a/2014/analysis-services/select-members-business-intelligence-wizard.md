---
title: " (商業智慧 Wizard) 選取成員 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.biwizard.currencyconversion.memberconversion.f1
ms.assetid: 1a147461-d594-41e7-a41d-09d2d003e1e0
author: minewiskan
ms.author: owend
ms.openlocfilehash: fd5f184e0d9670725609531b6d0a101f8e7f8647
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593629"
---
# <a name="select-members-business-intelligence-wizard"></a><span data-ttu-id="e8cf8-102">選取成員 (商業智慧精靈)</span><span class="sxs-lookup"><span data-stu-id="e8cf8-102">Select Members (Business Intelligence Wizard)</span></span>
  <span data-ttu-id="e8cf8-103">使用 **[選取成員]** 頁面，即可決定商業智慧精靈應該對哪些成員套用 **[設定貨幣轉換選項]** 頁面所指定的貨幣轉換功能。</span><span class="sxs-lookup"><span data-stu-id="e8cf8-103">Use the **Select Members** page to determine to which members the Business Intelligence Wizard should apply the currency conversion functionality specified on the **Set Currency Conversion Options** page.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e8cf8-104">如果 [商業智慧精靈] 是從 [維度設計師] 啟動，或是在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中方案總管的某維度上按一下滑鼠右鍵來啟動，則不會出現此頁面。</span><span class="sxs-lookup"><span data-stu-id="e8cf8-104">This page does not appear if the Business Intelligence Wizard was started from Dimension Designer or by right-clicking a dimension in Solution Explorer in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span>  
  
## <a name="options"></a><span data-ttu-id="e8cf8-105">選項</span><span class="sxs-lookup"><span data-stu-id="e8cf8-105">Options</span></span>  
 <span data-ttu-id="e8cf8-106">**量值維度**</span><span class="sxs-lookup"><span data-stu-id="e8cf8-106">**Measures dimension**</span></span>  
 <span data-ttu-id="e8cf8-107">選取即可套用貨幣轉換功能至 Cube 中的一個或多個量值。</span><span class="sxs-lookup"><span data-stu-id="e8cf8-107">Select to apply the currency conversion functionality to one or more measures in the cube.</span></span>  
  
 <span data-ttu-id="e8cf8-108">若選取，方格會顯示下表列出的選項。</span><span class="sxs-lookup"><span data-stu-id="e8cf8-108">If selected, the grid displays the options listed in the following table.</span></span>  
  
|<span data-ttu-id="e8cf8-109">選項</span><span class="sxs-lookup"><span data-stu-id="e8cf8-109">Option</span></span>|<span data-ttu-id="e8cf8-110">描述</span><span class="sxs-lookup"><span data-stu-id="e8cf8-110">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="e8cf8-111">**內建量值類型**</span><span class="sxs-lookup"><span data-stu-id="e8cf8-111">**Built-in Measure Types**</span></span>|<span data-ttu-id="e8cf8-112">選取即可包含指定量值的貨幣轉換功能。</span><span class="sxs-lookup"><span data-stu-id="e8cf8-112">Select to include currency conversion functionality for the specified measure.</span></span>|  
|<span data-ttu-id="e8cf8-113">**評估**</span><span class="sxs-lookup"><span data-stu-id="e8cf8-113">**Measures**</span></span>|<span data-ttu-id="e8cf8-114">從比率量值群組中選取量值，此群組包含 [內建量值類型]\*\*\*\* 中所選取量值在轉換時使用的匯率。</span><span class="sxs-lookup"><span data-stu-id="e8cf8-114">Select the measure from the rate measure group that contains the exchange rate to use when the measure selected in **Built-in Measure Types** is converted.</span></span>|  
  
 <span data-ttu-id="e8cf8-115">**帳戶階層**</span><span class="sxs-lookup"><span data-stu-id="e8cf8-115">**Account hierarchy**</span></span>  
 <span data-ttu-id="e8cf8-116">選取即可套用貨幣轉換功能至 Cube 所包含帳戶維度之帳戶階層中的一個或多個成員。</span><span class="sxs-lookup"><span data-stu-id="e8cf8-116">Select to apply the currency conversion functionality to one or more members in the account hierarchy of the account dimension included in the cube.</span></span> <span data-ttu-id="e8cf8-117">帳戶階層是帳戶維度內其 `Type` 屬性設定為*account*的階層。</span><span class="sxs-lookup"><span data-stu-id="e8cf8-117">The account hierarchy is the hierarchy within the account dimension whose `Type` property is set to *Account*.</span></span>  
  
 <span data-ttu-id="e8cf8-118">若選取，方格會顯示下表列出的選項。</span><span class="sxs-lookup"><span data-stu-id="e8cf8-118">If selected, the grid displays the options listed in the following table.</span></span>  
  
|<span data-ttu-id="e8cf8-119">選項</span><span class="sxs-lookup"><span data-stu-id="e8cf8-119">Option</span></span>|<span data-ttu-id="e8cf8-120">描述</span><span class="sxs-lookup"><span data-stu-id="e8cf8-120">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="e8cf8-121">**帳戶成員**</span><span class="sxs-lookup"><span data-stu-id="e8cf8-121">**Account Member**</span></span>|<span data-ttu-id="e8cf8-122">選取即可包含帳戶階層所指定成員的貨幣轉換功能。</span><span class="sxs-lookup"><span data-stu-id="e8cf8-122">Select to include currency conversion functionality for the specified member of the account hierarchy.</span></span>|  
|<span data-ttu-id="e8cf8-123">**評估**</span><span class="sxs-lookup"><span data-stu-id="e8cf8-123">**Measures**</span></span>|<span data-ttu-id="e8cf8-124">從比率量值群組中選取量值，此群組包含 **[帳戶成員]** 中所選取成員之量值在轉換時使用的匯率。</span><span class="sxs-lookup"><span data-stu-id="e8cf8-124">Select the measure from the rate measure group that contains the exchange rate to use when the measures for the member selected in **Account Member** are converted.</span></span>|  
  
 <span data-ttu-id="e8cf8-125">**依據類型的帳戶階層**</span><span class="sxs-lookup"><span data-stu-id="e8cf8-125">**Account hierarchy based on type**</span></span>  
 <span data-ttu-id="e8cf8-126">選取即可套用貨幣轉換功能至帳戶階層中、`Type` 屬性設定為指定之帳戶類型的所有屬性成員。</span><span class="sxs-lookup"><span data-stu-id="e8cf8-126">Select to apply the currency conversion functionality to all members of attributes in the account hierarchy whose `Type` property is set to a specified account type.</span></span>  
  
 <span data-ttu-id="e8cf8-127">若選取，方格會顯示下表列出的選項。</span><span class="sxs-lookup"><span data-stu-id="e8cf8-127">If selected, the grid displays the options listed in the following table.</span></span>  
  
|<span data-ttu-id="e8cf8-128">選項</span><span class="sxs-lookup"><span data-stu-id="e8cf8-128">Option</span></span>|<span data-ttu-id="e8cf8-129">描述</span><span class="sxs-lookup"><span data-stu-id="e8cf8-129">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="e8cf8-130">**帳戶類型**</span><span class="sxs-lookup"><span data-stu-id="e8cf8-130">**Account Type**</span></span>|<span data-ttu-id="e8cf8-131">選取即可包含所指定帳戶類型的貨幣轉換功能。</span><span class="sxs-lookup"><span data-stu-id="e8cf8-131">Select to include currency conversion functionality for the specified account type.</span></span>|  
|<span data-ttu-id="e8cf8-132">**評估**</span><span class="sxs-lookup"><span data-stu-id="e8cf8-132">**Measures**</span></span>|<span data-ttu-id="e8cf8-133">從比率量值群組中選取量值，此群組包含使用 **[帳戶類型]** 中所選取帳戶類型之屬性成員的量值在轉換時使用的匯率。</span><span class="sxs-lookup"><span data-stu-id="e8cf8-133">Select the measure from the rate measure group that contains the exchange rate to use when measures for the members of attributes using the account type selected in **Account Type** are converted.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e8cf8-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e8cf8-134">See Also</span></span>  
 <span data-ttu-id="e8cf8-135">[商業智慧 Wizard F1 說明](business-intelligence-wizard-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="e8cf8-135">[Business Intelligence Wizard F1 Help](business-intelligence-wizard-f1-help.md) </span></span>  
 <span data-ttu-id="e8cf8-136">[Cube 設計工具 &#40;Analysis Services-多維度資料&#41;](cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="e8cf8-136">[Cube Designer &#40;Analysis Services - Multidimensional Data&#41;](cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="e8cf8-137">維度設計師 &#40;Analysis Services 多維資料&#41;</span><span class="sxs-lookup"><span data-stu-id="e8cf8-137">Dimension Designer &#40;Analysis Services - Multidimensional Data&#41;</span></span>](dimension-designer-analysis-services-multidimensional-data.md)  
  
  
