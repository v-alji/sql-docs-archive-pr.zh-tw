---
title: 選取行事曆 (維度 Wizard) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.dimensionwizard.serverSpecialCalendars.f1
ms.assetid: 6e28a020-2586-4b13-9333-b499fb1b33af
author: minewiskan
ms.author: owend
ms.openlocfilehash: 2048ee20dd91c942f01982d02f3265a6bad670dd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596924"
---
# <a name="select-calendars-dimension-wizard"></a><span data-ttu-id="7dedc-102">選取日曆 (維度精靈)</span><span class="sxs-lookup"><span data-stu-id="7dedc-102">Select Calendars (Dimension Wizard)</span></span>
  <span data-ttu-id="7dedc-103">使用 [選取日曆]\*\*\*\* 頁面來建立其他階層，其中代表時間維度的會計日曆、報表日曆、製造日曆或國際標準組織 (ISO) 8601 日曆。</span><span class="sxs-lookup"><span data-stu-id="7dedc-103">Use the **Select Calendars** page to create additional hierarchies representing fiscal, reporting, manufacturing, or International Standards Organization (ISO) 8601 calendars for the time dimension.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7dedc-104">唯有在 [選取維度類型]\*\*\*\* 頁面上選取了 [伺服器時間維度]\*\*\*\*，或者在 [維度定義]\*\*\*\* 頁面上選取了 [不使用資料來源而建立維度]\*\*\*\*，且在 [選取維度類型]\*\*\*\* 頁面上選取了 [時間維度]\*\*\*\*，才會顯示此頁面。</span><span class="sxs-lookup"><span data-stu-id="7dedc-104">This page will appear only if you have selected **Server time dimension** on the **Select the Dimension Type** page, or if you selected **Build the dimension without using a data source** on the **Dimension Definition** page and selected **Time dimension** on the **Select the Dimension Type** page.</span></span>  
  
## <a name="options"></a><span data-ttu-id="7dedc-105">選項</span><span class="sxs-lookup"><span data-stu-id="7dedc-105">Options</span></span>  
 <span data-ttu-id="7dedc-106">**會計日曆**</span><span class="sxs-lookup"><span data-stu-id="7dedc-106">**Fiscal calendar**</span></span>  
 <span data-ttu-id="7dedc-107">選取即可根據會計日曆建立時間階層。</span><span class="sxs-lookup"><span data-stu-id="7dedc-107">Select to create a time hierarchy based on a fiscal calendar.</span></span>  
  
 <span data-ttu-id="7dedc-108">**開始日期和月份**</span><span class="sxs-lookup"><span data-stu-id="7dedc-108">**Start day and month**</span></span>  
 <span data-ttu-id="7dedc-109">選取會計日曆的開始日期和月份。</span><span class="sxs-lookup"><span data-stu-id="7dedc-109">Select the day and month on which the fiscal calendar begins.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7dedc-110">唯有選取 [會計日曆]\*\*\*\* 時，才能使用此選項。</span><span class="sxs-lookup"><span data-stu-id="7dedc-110">This option is available only when **Fiscal calendar** is selected.</span></span>  
  
 <span data-ttu-id="7dedc-111">**會計日曆命名慣例**</span><span class="sxs-lookup"><span data-stu-id="7dedc-111">**Fiscal calendar naming convention**</span></span>  
 <span data-ttu-id="7dedc-112">選取會計日曆所使用的命名慣例。</span><span class="sxs-lookup"><span data-stu-id="7dedc-112">Select the naming convention used by the fiscal calendar.</span></span> <span data-ttu-id="7dedc-113">選取 [日曆年度名稱]\*\*\*\* 或 [日曆年度名稱 +1]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7dedc-113">Select either **Calendar year name** or **Calendar year name +1**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7dedc-114">唯有選取 [會計日曆]\*\*\*\* 時，才能使用此選項。</span><span class="sxs-lookup"><span data-stu-id="7dedc-114">This option is available only when **Fiscal calendar** is selected.</span></span>  
  
 <span data-ttu-id="7dedc-115">**報表 (或行銷) 日曆**</span><span class="sxs-lookup"><span data-stu-id="7dedc-115">**Reporting (or marketing) calendar**</span></span>  
 <span data-ttu-id="7dedc-116">選取即可根據報表日曆建立時間階層。</span><span class="sxs-lookup"><span data-stu-id="7dedc-116">Select to create a time hierarchy based on a reporting calendar.</span></span>  
  
 <span data-ttu-id="7dedc-117">**開始的週和月份**</span><span class="sxs-lookup"><span data-stu-id="7dedc-117">**Start week and month**</span></span>  
 <span data-ttu-id="7dedc-118">選取報表日曆開始的週和月份。</span><span class="sxs-lookup"><span data-stu-id="7dedc-118">Select the week and month on which the reporting calendar begins.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7dedc-119">選取 [報表 (或行銷) 日曆]\*\*\*\* 時，才能使用此選項。</span><span class="sxs-lookup"><span data-stu-id="7dedc-119">This option is available when **Reporting (or marketing) calendar** is selected.</span></span>  
  
 <span data-ttu-id="7dedc-120">**月份週別模式**</span><span class="sxs-lookup"><span data-stu-id="7dedc-120">**Week by month pattern**</span></span>  
 <span data-ttu-id="7dedc-121">選取報表日曆所使用的月份週別模式。</span><span class="sxs-lookup"><span data-stu-id="7dedc-121">Select the week by month pattern used by the reporting calendar.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7dedc-122">選取 [報表 (或行銷) 日曆]\*\*\*\* 時，才能使用此選項。</span><span class="sxs-lookup"><span data-stu-id="7dedc-122">This option is available when **Reporting (or marketing) calendar** is selected.</span></span>  
  
 <span data-ttu-id="7dedc-123">下表列出月份週別模式可用的選項。</span><span class="sxs-lookup"><span data-stu-id="7dedc-123">The following table lists the options available for the week by month pattern.</span></span>  
  
|<span data-ttu-id="7dedc-124">值</span><span class="sxs-lookup"><span data-stu-id="7dedc-124">Value</span></span>|<span data-ttu-id="7dedc-125">描述</span><span class="sxs-lookup"><span data-stu-id="7dedc-125">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="7dedc-126">**第 445 週**</span><span class="sxs-lookup"><span data-stu-id="7dedc-126">**Week 445**</span></span>|<span data-ttu-id="7dedc-127">該季的第一個月有 4 週，該季的第二個月有 4 週，而該季的第三個月有 5 週。</span><span class="sxs-lookup"><span data-stu-id="7dedc-127">The first month in the quarter has 4 weeks, the second month in the quarter has 4 weeks, and the third month in the quarter has 5 weeks.</span></span>|  
|<span data-ttu-id="7dedc-128">**第 454 週**</span><span class="sxs-lookup"><span data-stu-id="7dedc-128">**Week 454**</span></span>|<span data-ttu-id="7dedc-129">該季的第一個月有 4 週，該季的第二個月有 5 週，而該季的第三個月有 4 週。</span><span class="sxs-lookup"><span data-stu-id="7dedc-129">The first month in the quarter has 4 weeks, the second month in the quarter has 5 weeks, and the third month in the quarter has 4 weeks.</span></span>|  
|<span data-ttu-id="7dedc-130">**第 544 週**</span><span class="sxs-lookup"><span data-stu-id="7dedc-130">**Week 544**</span></span>|<span data-ttu-id="7dedc-131">該季的第一個月有 5 週，該季的第二個月有 4 週，而該季的第三個月有 4 週。</span><span class="sxs-lookup"><span data-stu-id="7dedc-131">The first month in the quarter has 5 weeks, the second month in the quarter has 4 weeks, and the third month in the quarter has 4 weeks.</span></span>|  
  
 <span data-ttu-id="7dedc-132">**製造日曆**</span><span class="sxs-lookup"><span data-stu-id="7dedc-132">**Manufacturing calendar**</span></span>  
 <span data-ttu-id="7dedc-133">選取即可根據製造日曆建立時間階層。</span><span class="sxs-lookup"><span data-stu-id="7dedc-133">Select to create a time hierarchy based on a manufacturing calendar.</span></span>  
  
 <span data-ttu-id="7dedc-134">**開始的週和月份**</span><span class="sxs-lookup"><span data-stu-id="7dedc-134">**Start week and month**</span></span>  
 <span data-ttu-id="7dedc-135">選取製造日曆開始的週和月份。</span><span class="sxs-lookup"><span data-stu-id="7dedc-135">Select the week and month on which the manufacturing calendar begins.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7dedc-136">選取 [製造日曆]\*\*\*\* 時，才能使用此選項。</span><span class="sxs-lookup"><span data-stu-id="7dedc-136">This option is available when **Manufacturing calendar** is selected.</span></span>  
  
 <span data-ttu-id="7dedc-137">**延長期間的季度**</span><span class="sxs-lookup"><span data-stu-id="7dedc-137">**Quarter with extra periods**</span></span>  
 <span data-ttu-id="7dedc-138">選取或鍵入會包含延長期間的季度。</span><span class="sxs-lookup"><span data-stu-id="7dedc-138">Select or type the quarter that will contain the extra periods.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7dedc-139">選取 [製造日曆]\*\*\*\* 時，才能使用此選項。</span><span class="sxs-lookup"><span data-stu-id="7dedc-139">This option is available when **Manufacturing calendar** is selected.</span></span>  
  
 <span data-ttu-id="7dedc-140">**ISO 8601 日曆**</span><span class="sxs-lookup"><span data-stu-id="7dedc-140">**ISO 8601 calendar**</span></span>  
 <span data-ttu-id="7dedc-141">選取即可根據 ISO 8601 日曆建立階層。</span><span class="sxs-lookup"><span data-stu-id="7dedc-141">Select to create a hierarchy based on the ISO 8601 calendar.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7dedc-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7dedc-142">See Also</span></span>  
 <span data-ttu-id="7dedc-143">[維度嚮導 F1 說明](dimension-wizard-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="7dedc-143">[Dimension Wizard F1 Help](dimension-wizard-f1-help.md) </span></span>  
 <span data-ttu-id="7dedc-144">[維度 &#40;Analysis Services 多維資料&#41;](multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="7dedc-144">[Dimensions &#40;Analysis Services - Multidimensional Data&#41;](multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="7dedc-145">多維度模型中的維度</span><span class="sxs-lookup"><span data-stu-id="7dedc-145">Dimensions in Multidimensional Models</span></span>](multidimensional-models/dimensions-in-multidimensional-models.md)  
  
  
