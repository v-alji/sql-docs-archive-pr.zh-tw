---
title: 篩選設定 (物件總管與公用程式總管) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.ag.job.filtersettings.f1
- sql12.swb.common.filtersettings.f1
ms.assetid: 4aab04bc-e1ab-4d4b-ab74-b287fc805bc2
author: stevestein
ms.author: sstein
ms.openlocfilehash: c31fbcbef9cbab86a7bd3ab7b2fae21e626aaa59
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584247"
---
# <a name="filter-settings-object-explorer-and-utility-explorer"></a><span data-ttu-id="46ace-102">篩選設定 (物件總管與公用程式總管)</span><span class="sxs-lookup"><span data-stu-id="46ace-102">Filter Settings (Object Explorer and Utility Explorer)</span></span>
  <span data-ttu-id="46ace-103">使用此對話方塊來指定篩選。</span><span class="sxs-lookup"><span data-stu-id="46ace-103">Use this dialog box to specify a filter.</span></span> <span data-ttu-id="46ace-104">篩選可以讓您將 [物件總管] 與 [公用程式總管] 設定為僅顯示符合特定準則的項目。</span><span class="sxs-lookup"><span data-stu-id="46ace-104">A filter allows you to configure Object Explorer and Utility Explorer to display only items that meet specific criteria.</span></span> <span data-ttu-id="46ace-105">例如，您可以使用篩選，僅顯示名稱中包含單字「Maintenance」的作業。</span><span class="sxs-lookup"><span data-stu-id="46ace-105">For example, you can use a filter to show only jobs with names that contain the word "Maintenance."</span></span> <span data-ttu-id="46ace-106">[篩選設定]  對話方塊的標頭包含伺服器的名稱，也可以包含資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="46ace-106">The header for the **Filter Settings** dialog box contains the name of the server, and it may contain the name of the database.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="46ace-107">UI 元素清單</span><span class="sxs-lookup"><span data-stu-id="46ace-107">UI element list</span></span>  
 <span data-ttu-id="46ace-108">**屬性**</span><span class="sxs-lookup"><span data-stu-id="46ace-108">**Property**</span></span>  
 <span data-ttu-id="46ace-109">顯示要根據該屬性進行篩選的屬性。</span><span class="sxs-lookup"><span data-stu-id="46ace-109">Displays the property to filter on.</span></span>  
  
 <span data-ttu-id="46ace-110">**運算子**</span><span class="sxs-lookup"><span data-stu-id="46ace-110">**Operator**</span></span>  
 <span data-ttu-id="46ace-111">選取篩選將值套用到屬性的方式。</span><span class="sxs-lookup"><span data-stu-id="46ace-111">Select the way that the filter applies the value to the property.</span></span> <span data-ttu-id="46ace-112">有下列的選項：</span><span class="sxs-lookup"><span data-stu-id="46ace-112">There are the following options:</span></span>  
  
-   <span data-ttu-id="46ace-113">**等於**</span><span class="sxs-lookup"><span data-stu-id="46ace-113">**Equals**</span></span>  
  
     <span data-ttu-id="46ace-114">篩選會顯示屬性和值完全相符的項目。</span><span class="sxs-lookup"><span data-stu-id="46ace-114">The filter shows items where the property and the value are an exact match.</span></span>  
  
-   <span data-ttu-id="46ace-115">**Contains**</span><span class="sxs-lookup"><span data-stu-id="46ace-115">**Contains**</span></span>  
  
     <span data-ttu-id="46ace-116">篩選會顯示屬性包含值的項目。</span><span class="sxs-lookup"><span data-stu-id="46ace-116">The filter shows items where the property contains the value.</span></span> <span data-ttu-id="46ace-117">屬性可以包含其他文字。</span><span class="sxs-lookup"><span data-stu-id="46ace-117">The property may contain other text.</span></span>  
  
-   <span data-ttu-id="46ace-118">**不包含**</span><span class="sxs-lookup"><span data-stu-id="46ace-118">**Does not contain**</span></span>  
  
     <span data-ttu-id="46ace-119">篩選會顯示屬性不包含值的項目。</span><span class="sxs-lookup"><span data-stu-id="46ace-119">The filter shows items that where the property does not contain the value.</span></span>  
  
-   <span data-ttu-id="46ace-120">**小於**</span><span class="sxs-lookup"><span data-stu-id="46ace-120">**Less than**</span></span>  
  
     <span data-ttu-id="46ace-121">適用於日期，此篩選會顯示日期早於所提供之值的項目。</span><span class="sxs-lookup"><span data-stu-id="46ace-121">Available for dates, this filter shows items whose date is before the value provided.</span></span>  
  
-   <span data-ttu-id="46ace-122">**小於或等於**</span><span class="sxs-lookup"><span data-stu-id="46ace-122">**Less than or equal**</span></span>  
  
     <span data-ttu-id="46ace-123">適用於日期，此篩選會顯示日期包含或早於所提供之值的項目。</span><span class="sxs-lookup"><span data-stu-id="46ace-123">Available for dates, this filter shows items whose date contains or is before the value provided.</span></span>  
  
-   <span data-ttu-id="46ace-124">**大於**</span><span class="sxs-lookup"><span data-stu-id="46ace-124">**Greater than**</span></span>  
  
     <span data-ttu-id="46ace-125">適用於日期，此篩選會顯示日期晚於所提供之值的項目。</span><span class="sxs-lookup"><span data-stu-id="46ace-125">Available for dates, this filter shows items whose date is after the value provided.</span></span>  
  
-   <span data-ttu-id="46ace-126">**大於或等於**</span><span class="sxs-lookup"><span data-stu-id="46ace-126">**Greater than or equal**</span></span>  
  
     <span data-ttu-id="46ace-127">適用於日期，此篩選會顯示日期包含或晚於所提供之值的項目。</span><span class="sxs-lookup"><span data-stu-id="46ace-127">Available for dates, this filter shows items whose date contains or is after the value provided.</span></span>  
  
-   <span data-ttu-id="46ace-128">**介於**</span><span class="sxs-lookup"><span data-stu-id="46ace-128">**Between**</span></span>  
  
     <span data-ttu-id="46ace-129">適用於日期，此篩選會顯示日期介於所提供之兩個日期之間的項目。</span><span class="sxs-lookup"><span data-stu-id="46ace-129">Available for dates, this filter shows items whose date is between two dates provided.</span></span> <span data-ttu-id="46ace-130">選取 [介於]  並按下 TAB 鍵新增另一個資料列，以輸入第二個日期。</span><span class="sxs-lookup"><span data-stu-id="46ace-130">Select **Between** and press TAB to add another row allowing entry of the second date.</span></span>  
  
-   <span data-ttu-id="46ace-131">**不介於**</span><span class="sxs-lookup"><span data-stu-id="46ace-131">**Not between**</span></span>  
  
     <span data-ttu-id="46ace-132">適用於日期，此篩選會顯示日期早於或晚於所提供之兩個日期的項目。</span><span class="sxs-lookup"><span data-stu-id="46ace-132">Available for dates, this filter shows items whose date is before or after two dates provided.</span></span> <span data-ttu-id="46ace-133">選取 [不介於]  並按下 TAB 鍵跳離 [運算子]  資料行，即可新增另一個資料列，以輸入第二個日期。</span><span class="sxs-lookup"><span data-stu-id="46ace-133">Select **Not Between** and tab out of the **Operator** column to add another row allowing entry of the second date.</span></span>  
  
 <span data-ttu-id="46ace-134">**ReplTest1**</span><span class="sxs-lookup"><span data-stu-id="46ace-134">**Value**</span></span>  
 <span data-ttu-id="46ace-135">輸入要和屬性比較的值。</span><span class="sxs-lookup"><span data-stu-id="46ace-135">Type the value to compare to the property.</span></span> <span data-ttu-id="46ace-136">針對日期，按一下向下鍵以顯示用來選取日期的日曆。</span><span class="sxs-lookup"><span data-stu-id="46ace-136">For dates, click the down arrow to show a calendar for selecting the date.</span></span>  
  
 <span data-ttu-id="46ace-137">**清除篩選**</span><span class="sxs-lookup"><span data-stu-id="46ace-137">**Clear Filter**</span></span>  
 <span data-ttu-id="46ace-138">移除所有目前的篩選設定。</span><span class="sxs-lookup"><span data-stu-id="46ace-138">Removes all current filter settings.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46ace-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="46ace-139">See Also</span></span>  
 <span data-ttu-id="46ace-140">[使用 SQL Server Management Studio](../sql-server-management-studio-ssms.md) </span><span class="sxs-lookup"><span data-stu-id="46ace-140">[Use SQL Server Management Studio](../sql-server-management-studio-ssms.md) </span></span>  
 [<span data-ttu-id="46ace-141">SQL Server 公用程式的功能與工作</span><span class="sxs-lookup"><span data-stu-id="46ace-141">SQL Server Utility Features and Tasks</span></span>](../../relational-databases/manage/sql-server-utility-features-and-tasks.md)  
  
  
