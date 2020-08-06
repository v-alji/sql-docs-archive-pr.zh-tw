---
title: 定義 (維度 Wizard) 的時間週期 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.dimensionwizard.timefrequency.f1
ms.assetid: 6bda6b7e-d306-4e68-9acb-84de8f44d1b4
author: minewiskan
ms.author: owend
ms.openlocfilehash: 88b69eaa265b7a98f7d32063b602897d02016fa8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87605932"
---
# <a name="define-time-periods-dimension-wizard"></a><span data-ttu-id="e1c28-102">定義時間週期 (維度精靈)</span><span class="sxs-lookup"><span data-stu-id="e1c28-102">Define Time Periods (Dimension Wizard)</span></span>
  <span data-ttu-id="e1c28-103">使用 **[定義時間週期]** 頁面，即可定義時間維度或伺服器時間維度中包含的日曆年度資訊和時間頻率。</span><span class="sxs-lookup"><span data-stu-id="e1c28-103">Use the **Define Time Periods** page to define the calendar year information and time frequencies to include in the time dimension or server time dimension.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e1c28-104"> 唯有在 **[選取維度類型]** 頁面上選取了 **[伺服器時間維度]** ，或者在 **[選取建立方法]** 頁面上選取了 **[不使用資料來源而建立維度]** ，且在 **[選取維度類型]** 頁面上選取了 **[時間維度]** ，才會顯示此頁面。</span><span class="sxs-lookup"><span data-stu-id="e1c28-104">This page will appear only if you have selected **Server time dimension** on the **Select the Dimension Type** page, or if you selected **Build the dimension without using a data source** on the **Select Build Method** page and selected **Time dimension** on the **Select the Dimension Type** page.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="e1c28-105">此頁面是用來定義時間維度的日曆年度。</span><span class="sxs-lookup"><span data-stu-id="e1c28-105">This page is for defining the calendar year of a time dimension.</span></span> <span data-ttu-id="e1c28-106">若要定義時間維度的會計日曆年、製造日曆年、報表日曆年或國際標準組織 (ISO) 8601 日曆年，請使用 [選取日曆]\*\*\*\* 頁面。</span><span class="sxs-lookup"><span data-stu-id="e1c28-106">To define a fiscal, manufacturing, reporting, or International Standards Organization (ISO) 8601 year for the time dimension, use the **Select Calendars** page.</span></span>  
  
## <a name="options"></a><span data-ttu-id="e1c28-107">選項</span><span class="sxs-lookup"><span data-stu-id="e1c28-107">Options</span></span>  
 <span data-ttu-id="e1c28-108">**日曆第一天**</span><span class="sxs-lookup"><span data-stu-id="e1c28-108">**First calendar day**</span></span>  
 <span data-ttu-id="e1c28-109">鍵入或選取今年的第一天。</span><span class="sxs-lookup"><span data-stu-id="e1c28-109">Type or select the day that begins the current year.</span></span>  
  
 <span data-ttu-id="e1c28-110">**日曆最後一天**</span><span class="sxs-lookup"><span data-stu-id="e1c28-110">**Last calendar day**</span></span>  
 <span data-ttu-id="e1c28-111">鍵入或選取今年的最後一天。</span><span class="sxs-lookup"><span data-stu-id="e1c28-111">Type or select the day that ends the current year.</span></span>  
  
 <span data-ttu-id="e1c28-112">**每週第一天**</span><span class="sxs-lookup"><span data-stu-id="e1c28-112">**First day of the week**</span></span>  
 <span data-ttu-id="e1c28-113">選取每週的第一天。</span><span class="sxs-lookup"><span data-stu-id="e1c28-113">Select the day that begins a week.</span></span>  
  
 <span data-ttu-id="e1c28-114">**時間週期**</span><span class="sxs-lookup"><span data-stu-id="e1c28-114">**Time periods**</span></span>  
 <span data-ttu-id="e1c28-115">選取時間維度之日曆年度的時間週期。</span><span class="sxs-lookup"><span data-stu-id="e1c28-115">Select the time periods for the calendar year of the time dimension.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e1c28-116">`Date` 時間週期是必要的。</span><span class="sxs-lookup"><span data-stu-id="e1c28-116">The `Date` time period is required.</span></span>  
  
 <span data-ttu-id="e1c28-117">**時間成員名稱的語言**</span><span class="sxs-lookup"><span data-stu-id="e1c28-117">**Language for time member names**</span></span>  
 <span data-ttu-id="e1c28-118">選取時間維度中之成員的語言。</span><span class="sxs-lookup"><span data-stu-id="e1c28-118">Select the language for the members in the time dimension.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1c28-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e1c28-119">See Also</span></span>  
 <span data-ttu-id="e1c28-120">[維度嚮導 F1 說明](dimension-wizard-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="e1c28-120">[Dimension Wizard F1 Help](dimension-wizard-f1-help.md) </span></span>  
 <span data-ttu-id="e1c28-121">[維度 &#40;Analysis Services 多維資料&#41;](multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="e1c28-121">[Dimensions &#40;Analysis Services - Multidimensional Data&#41;](multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="e1c28-122">[多維度模型中的維度](multidimensional-models/dimensions-in-multidimensional-models.md) </span><span class="sxs-lookup"><span data-stu-id="e1c28-122">[Dimensions in Multidimensional Models](multidimensional-models/dimensions-in-multidimensional-models.md) </span></span>  
 [<span data-ttu-id="e1c28-123">選取行事曆 &#40;維度 Wizard&#41;</span><span class="sxs-lookup"><span data-stu-id="e1c28-123">Select Calendars &#40;Dimension Wizard&#41;</span></span>](select-calendars-dimension-wizard.md)  
  
  
