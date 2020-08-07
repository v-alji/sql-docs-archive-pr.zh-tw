---
title: 第3課：重新命名資料行 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 5fc8ba1a-2b30-4775-9b3b-c09dee711b3e
author: minewiskan
ms.author: owend
ms.openlocfilehash: 59904f1110455b65679b3d19e6e8b7c731465ee9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584743"
---
# <a name="lesson-3-rename-columns"></a><span data-ttu-id="95f2b-102">第 3 課：重新命名資料行</span><span class="sxs-lookup"><span data-stu-id="95f2b-102">Lesson 3: Rename Columns</span></span>
  <span data-ttu-id="95f2b-103">在這一課，您將重新命名匯入的每個資料表中的多個資料行。</span><span class="sxs-lookup"><span data-stu-id="95f2b-103">In this lesson, you will rename many of the columns in each table you imported.</span></span> <span data-ttu-id="95f2b-104">重新命名可讓資料行更容易識別，且更容易在模型設計師中以及藉由使用者在用戶端應用程式中選取欄位的方式進行導覽。</span><span class="sxs-lookup"><span data-stu-id="95f2b-104">Renaming makes columns more identifiable and easier to navigate in both the model designer as well by users selecting fields in a client application.</span></span> <span data-ttu-id="95f2b-105">若要深入了解，請參閱[重新命名資料表或資料行 &#40;SSAS 表格式&#41;](tabular-models/rename-a-table-or-column-ssas-tabular.md)。</span><span class="sxs-lookup"><span data-stu-id="95f2b-105">To learn more, see [Rename a Table or Column &#40;SSAS Tabular&#41;](tabular-models/rename-a-table-or-column-ssas-tabular.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="95f2b-106">重新命名資料行不是完成本教學課程的必要工作；不過，在其餘課程 (尤其是包含建立關聯性的課程，以及使用 DAX 公式建立導出資料行和量值的課程) 會參考本課程中所述的資料行易記名稱。</span><span class="sxs-lookup"><span data-stu-id="95f2b-106">Renaming columns is not necessary to complete this tutorial; however, remaining lessons, in particular those that include creating relationships and creating calculated columns and measures using DAX formulas, refer to the column friendly names described in this lesson.</span></span> <span data-ttu-id="95f2b-107">如果您選擇不重新命名資料行，則必須在第 5、6 和 7 課中編輯 DAX 公式，以便使用本課中提供的原始來源資料行名稱。</span><span class="sxs-lookup"><span data-stu-id="95f2b-107">If you choose not to rename columns, you will have to edit the DAX formulas in lessons 5, 6, and 7 to use the original source column names provided in this lesson.</span></span>  
  
 <span data-ttu-id="95f2b-108">這堂課的預估完成時間：**20 分鐘**</span><span class="sxs-lookup"><span data-stu-id="95f2b-108">Estimated time to complete this lesson: **20 minutes**</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="95f2b-109">先決條件</span><span class="sxs-lookup"><span data-stu-id="95f2b-109">Prerequisites</span></span>  
 <span data-ttu-id="95f2b-110">本主題是表格式模型教學課程的一部分，請依序完成。</span><span class="sxs-lookup"><span data-stu-id="95f2b-110">This topic is part of a tabular modeling tutorial, which should be completed in order.</span></span> <span data-ttu-id="95f2b-111">在執行本課中的工作之前，您應已完成上一課： [第 2 課：新增資料](lesson-2-add-data.md)。</span><span class="sxs-lookup"><span data-stu-id="95f2b-111">Before performing the tasks in this lesson, you should have completed the previous lesson: [Lesson 2: Add Data](lesson-2-add-data.md).</span></span>  
  
## <a name="rename-columns"></a><span data-ttu-id="95f2b-112">重新命名資料行</span><span class="sxs-lookup"><span data-stu-id="95f2b-112">Rename Columns</span></span>  
  
#### <a name="to-rename-columns"></a><span data-ttu-id="95f2b-113">若要重新命名資料行</span><span class="sxs-lookup"><span data-stu-id="95f2b-113">To rename columns</span></span>  
  
1.  <span data-ttu-id="95f2b-114">在模型設計師中，按一下 [Customer]\*\*\*\* 資料表 (索引標籤)。</span><span class="sxs-lookup"><span data-stu-id="95f2b-114">In the model designer, click the **Customer** table (tab).</span></span>  
  
     <span data-ttu-id="95f2b-115">當您按一下某個索引標籤時，該資料表會在模型設計師視窗中變成使用中。</span><span class="sxs-lookup"><span data-stu-id="95f2b-115">When you click a tab, that table becomes active in the model designer window.</span></span>  
  
2.  <span data-ttu-id="95f2b-116">按兩下 [ **CustomerKey** ] 資料行名稱，然後輸入 `Customer  Id` ，再按 enter 鍵。</span><span class="sxs-lookup"><span data-stu-id="95f2b-116">Double click the **CustomerKey** column name, then type `Customer  Id`, and then press ENTER.</span></span>  
  
    > [!TIP]  
    >  <span data-ttu-id="95f2b-117">您也可以在資料行的 [**屬性**] 視窗或 [圖表視圖] 中，重新命名資料行**名稱**屬性中的資料行。</span><span class="sxs-lookup"><span data-stu-id="95f2b-117">You can also rename a column in the **Column Name** property in the column's **Properties** window, or in Diagram View.</span></span>  
  
3.  <span data-ttu-id="95f2b-118">重新命名 [Customer]\*\*\*\* 資料表中的其餘資料行以及其餘資料表中的資料行，使用易記名稱取帶來原名稱：</span><span class="sxs-lookup"><span data-stu-id="95f2b-118">Rename the remaining columns in the **Customer** table, as well as the columns in the remaining tables, replacing the source name with the friendly name:</span></span>  
  
     <span data-ttu-id="95f2b-119">**客戶資料表**</span><span class="sxs-lookup"><span data-stu-id="95f2b-119">**Customer Table**</span></span>  
  
    |<span data-ttu-id="95f2b-120">來源名稱</span><span class="sxs-lookup"><span data-stu-id="95f2b-120">Source Name</span></span>|<span data-ttu-id="95f2b-121">易記名稱</span><span class="sxs-lookup"><span data-stu-id="95f2b-121">Friendly Name</span></span>|  
    |-----------------|-------------------|  
    |<span data-ttu-id="95f2b-122">GeographyKey</span><span class="sxs-lookup"><span data-stu-id="95f2b-122">GeographyKey</span></span>|<span data-ttu-id="95f2b-123">Geography Id</span><span class="sxs-lookup"><span data-stu-id="95f2b-123">Geography Id</span></span>|  
    |<span data-ttu-id="95f2b-124">CustomerAlternateKey</span><span class="sxs-lookup"><span data-stu-id="95f2b-124">CustomerAlternateKey</span></span>|<span data-ttu-id="95f2b-125">Customer Alternate Id</span><span class="sxs-lookup"><span data-stu-id="95f2b-125">Customer Alternate Id</span></span>|  
    |<span data-ttu-id="95f2b-126">名字</span><span class="sxs-lookup"><span data-stu-id="95f2b-126">FirstName</span></span>|<span data-ttu-id="95f2b-127">名字</span><span class="sxs-lookup"><span data-stu-id="95f2b-127">First Name</span></span>|  
    |<span data-ttu-id="95f2b-128">MiddleName</span><span class="sxs-lookup"><span data-stu-id="95f2b-128">MiddleName</span></span>|<span data-ttu-id="95f2b-129">Middle Name</span><span class="sxs-lookup"><span data-stu-id="95f2b-129">Middle Name</span></span>|  
    |<span data-ttu-id="95f2b-130">姓氏</span><span class="sxs-lookup"><span data-stu-id="95f2b-130">LastName</span></span>|<span data-ttu-id="95f2b-131">姓氏</span><span class="sxs-lookup"><span data-stu-id="95f2b-131">Last Name</span></span>|  
    |<span data-ttu-id="95f2b-132">NameStyle</span><span class="sxs-lookup"><span data-stu-id="95f2b-132">NameStyle</span></span>|<span data-ttu-id="95f2b-133">Name Style</span><span class="sxs-lookup"><span data-stu-id="95f2b-133">Name Style</span></span>|  
    |<span data-ttu-id="95f2b-134">BirthDate</span><span class="sxs-lookup"><span data-stu-id="95f2b-134">BirthDate</span></span>|<span data-ttu-id="95f2b-135">Birth Date</span><span class="sxs-lookup"><span data-stu-id="95f2b-135">Birth Date</span></span>|  
    |<span data-ttu-id="95f2b-136">MaritalStatus</span><span class="sxs-lookup"><span data-stu-id="95f2b-136">MaritalStatus</span></span>|<span data-ttu-id="95f2b-137">Marital Status</span><span class="sxs-lookup"><span data-stu-id="95f2b-137">Marital Status</span></span>|  
    |<span data-ttu-id="95f2b-138">EmailAddress</span><span class="sxs-lookup"><span data-stu-id="95f2b-138">EmailAddress</span></span>|<span data-ttu-id="95f2b-139">電子郵件地址</span><span class="sxs-lookup"><span data-stu-id="95f2b-139">Email Address</span></span>|  
    |<span data-ttu-id="95f2b-140">YearlyIncome</span><span class="sxs-lookup"><span data-stu-id="95f2b-140">YearlyIncome</span></span>|<span data-ttu-id="95f2b-141">Yearly Income</span><span class="sxs-lookup"><span data-stu-id="95f2b-141">Yearly Income</span></span>|  
    |<span data-ttu-id="95f2b-142">TotalChildren</span><span class="sxs-lookup"><span data-stu-id="95f2b-142">TotalChildren</span></span>|<span data-ttu-id="95f2b-143">Total Children</span><span class="sxs-lookup"><span data-stu-id="95f2b-143">Total Children</span></span>|  
    |<span data-ttu-id="95f2b-144">NumberChildrenAtHome</span><span class="sxs-lookup"><span data-stu-id="95f2b-144">NumberChildrenAtHome</span></span>|<span data-ttu-id="95f2b-145">Number of Children At Home</span><span class="sxs-lookup"><span data-stu-id="95f2b-145">Number of Children At Home</span></span>|  
    |<span data-ttu-id="95f2b-146">EnglishEducation</span><span class="sxs-lookup"><span data-stu-id="95f2b-146">EnglishEducation</span></span>|<span data-ttu-id="95f2b-147">教育訓練</span><span class="sxs-lookup"><span data-stu-id="95f2b-147">Education</span></span>|  
    |<span data-ttu-id="95f2b-148">EnglishOccupation</span><span class="sxs-lookup"><span data-stu-id="95f2b-148">EnglishOccupation</span></span>|<span data-ttu-id="95f2b-149">Occupation</span><span class="sxs-lookup"><span data-stu-id="95f2b-149">Occupation</span></span>|  
    |<span data-ttu-id="95f2b-150">HouseOwnerFlag</span><span class="sxs-lookup"><span data-stu-id="95f2b-150">HouseOwnerFlag</span></span>|<span data-ttu-id="95f2b-151">Owns House</span><span class="sxs-lookup"><span data-stu-id="95f2b-151">Owns House</span></span>|  
    |<span data-ttu-id="95f2b-152">NumberCarsOwned</span><span class="sxs-lookup"><span data-stu-id="95f2b-152">NumberCarsOwned</span></span>|<span data-ttu-id="95f2b-153">Number of Cars Owned</span><span class="sxs-lookup"><span data-stu-id="95f2b-153">Number of Cars Owned</span></span>|  
    |<span data-ttu-id="95f2b-154">AddressLine1</span><span class="sxs-lookup"><span data-stu-id="95f2b-154">AddressLine1</span></span>|<span data-ttu-id="95f2b-155">Address Line 1</span><span class="sxs-lookup"><span data-stu-id="95f2b-155">Address Line 1</span></span>|  
    |<span data-ttu-id="95f2b-156">AddressLine2</span><span class="sxs-lookup"><span data-stu-id="95f2b-156">AddressLine2</span></span>|<span data-ttu-id="95f2b-157">Address Line 2</span><span class="sxs-lookup"><span data-stu-id="95f2b-157">Address Line 2</span></span>|  
    |<span data-ttu-id="95f2b-158">電話</span><span class="sxs-lookup"><span data-stu-id="95f2b-158">Phone</span></span>|<span data-ttu-id="95f2b-159">電話號碼</span><span class="sxs-lookup"><span data-stu-id="95f2b-159">Phone Number</span></span>|  
    |<span data-ttu-id="95f2b-160">DateFirstPurchase</span><span class="sxs-lookup"><span data-stu-id="95f2b-160">DateFirstPurchase</span></span>|<span data-ttu-id="95f2b-161">Date of First Purchase</span><span class="sxs-lookup"><span data-stu-id="95f2b-161">Date of First Purchase</span></span>|  
    |<span data-ttu-id="95f2b-162">CommuteDistance</span><span class="sxs-lookup"><span data-stu-id="95f2b-162">CommuteDistance</span></span>|<span data-ttu-id="95f2b-163">Commute Distance</span><span class="sxs-lookup"><span data-stu-id="95f2b-163">Commute Distance</span></span>|  
  
     <span data-ttu-id="95f2b-164">**日期**</span><span class="sxs-lookup"><span data-stu-id="95f2b-164">**Date**</span></span>  
  
    |<span data-ttu-id="95f2b-165">來源名稱</span><span class="sxs-lookup"><span data-stu-id="95f2b-165">Source Name</span></span>|<span data-ttu-id="95f2b-166">易記名稱</span><span class="sxs-lookup"><span data-stu-id="95f2b-166">Friendly Name</span></span>|  
    |-----------------|-------------------|  
    |<span data-ttu-id="95f2b-167">FullDateAlternateKey</span><span class="sxs-lookup"><span data-stu-id="95f2b-167">FullDateAlternateKey</span></span>|<span data-ttu-id="95f2b-168">日期</span><span class="sxs-lookup"><span data-stu-id="95f2b-168">Date</span></span>|  
    |<span data-ttu-id="95f2b-169">DayNumberOfWeek</span><span class="sxs-lookup"><span data-stu-id="95f2b-169">DayNumberOfWeek</span></span>|<span data-ttu-id="95f2b-170">Day Number of Week</span><span class="sxs-lookup"><span data-stu-id="95f2b-170">Day Number of Week</span></span>|  
    |<span data-ttu-id="95f2b-171">EnglishDayNameOfWeek</span><span class="sxs-lookup"><span data-stu-id="95f2b-171">EnglishDayNameOfWeek</span></span>|<span data-ttu-id="95f2b-172">Day Name</span><span class="sxs-lookup"><span data-stu-id="95f2b-172">Day Name</span></span>|  
    |<span data-ttu-id="95f2b-173">DayNumberOfMonth</span><span class="sxs-lookup"><span data-stu-id="95f2b-173">DayNumberOfMonth</span></span>|<span data-ttu-id="95f2b-174">月中的日</span><span class="sxs-lookup"><span data-stu-id="95f2b-174">Day of Month</span></span>|  
    |<span data-ttu-id="95f2b-175">DayNumberOfYear</span><span class="sxs-lookup"><span data-stu-id="95f2b-175">DayNumberOfYear</span></span>|<span data-ttu-id="95f2b-176">年中的日</span><span class="sxs-lookup"><span data-stu-id="95f2b-176">Day of Year</span></span>|  
    |<span data-ttu-id="95f2b-177">WeekNumberOfYear</span><span class="sxs-lookup"><span data-stu-id="95f2b-177">WeekNumberOfYear</span></span>|<span data-ttu-id="95f2b-178">Week Number of Year</span><span class="sxs-lookup"><span data-stu-id="95f2b-178">Week Number of Year</span></span>|  
    |<span data-ttu-id="95f2b-179">EnglishMonthName</span><span class="sxs-lookup"><span data-stu-id="95f2b-179">EnglishMonthName</span></span>|<span data-ttu-id="95f2b-180">月份名稱</span><span class="sxs-lookup"><span data-stu-id="95f2b-180">Month Name</span></span>|  
    |<span data-ttu-id="95f2b-181">MonthNumberOfYear</span><span class="sxs-lookup"><span data-stu-id="95f2b-181">MonthNumberOfYear</span></span>|<span data-ttu-id="95f2b-182">Month</span><span class="sxs-lookup"><span data-stu-id="95f2b-182">Month</span></span>|  
    |<span data-ttu-id="95f2b-183">CalendarQuarter</span><span class="sxs-lookup"><span data-stu-id="95f2b-183">CalendarQuarter</span></span>|<span data-ttu-id="95f2b-184">Calendar Quarter</span><span class="sxs-lookup"><span data-stu-id="95f2b-184">Calendar Quarter</span></span>|  
    |<span data-ttu-id="95f2b-185">CalendarYear</span><span class="sxs-lookup"><span data-stu-id="95f2b-185">CalendarYear</span></span>|<span data-ttu-id="95f2b-186">Calendar Year</span><span class="sxs-lookup"><span data-stu-id="95f2b-186">Calendar Year</span></span>|  
    |<span data-ttu-id="95f2b-187">CalendarSemester</span><span class="sxs-lookup"><span data-stu-id="95f2b-187">CalendarSemester</span></span>|<span data-ttu-id="95f2b-188">Calendar Semester</span><span class="sxs-lookup"><span data-stu-id="95f2b-188">Calendar Semester</span></span>|  
    |<span data-ttu-id="95f2b-189">FiscalQuarter</span><span class="sxs-lookup"><span data-stu-id="95f2b-189">FiscalQuarter</span></span>|<span data-ttu-id="95f2b-190">Fiscal Quarter</span><span class="sxs-lookup"><span data-stu-id="95f2b-190">Fiscal Quarter</span></span>|  
    |<span data-ttu-id="95f2b-191">FiscalYear</span><span class="sxs-lookup"><span data-stu-id="95f2b-191">FiscalYear</span></span>|<span data-ttu-id="95f2b-192">Fiscal Year</span><span class="sxs-lookup"><span data-stu-id="95f2b-192">Fiscal Year</span></span>|  
    |<span data-ttu-id="95f2b-193">FiscalSemester</span><span class="sxs-lookup"><span data-stu-id="95f2b-193">FiscalSemester</span></span>|<span data-ttu-id="95f2b-194">Fiscal Semester</span><span class="sxs-lookup"><span data-stu-id="95f2b-194">Fiscal Semester</span></span>|  
  
     <span data-ttu-id="95f2b-195">**地理位置**</span><span class="sxs-lookup"><span data-stu-id="95f2b-195">**Geography**</span></span>  
  
    |<span data-ttu-id="95f2b-196">來源名稱</span><span class="sxs-lookup"><span data-stu-id="95f2b-196">Source Name</span></span>|<span data-ttu-id="95f2b-197">易記名稱</span><span class="sxs-lookup"><span data-stu-id="95f2b-197">Friendly Name</span></span>|  
    |-----------------|-------------------|  
    |<span data-ttu-id="95f2b-198">GeographyKey</span><span class="sxs-lookup"><span data-stu-id="95f2b-198">GeographyKey</span></span>|<span data-ttu-id="95f2b-199">Geography Id</span><span class="sxs-lookup"><span data-stu-id="95f2b-199">Geography Id</span></span>|  
    |<span data-ttu-id="95f2b-200">StateProvinceCode</span><span class="sxs-lookup"><span data-stu-id="95f2b-200">StateProvinceCode</span></span>|<span data-ttu-id="95f2b-201">State Province Code</span><span class="sxs-lookup"><span data-stu-id="95f2b-201">State Province Code</span></span>|  
    |<span data-ttu-id="95f2b-202">StateProvinceName</span><span class="sxs-lookup"><span data-stu-id="95f2b-202">StateProvinceName</span></span>|<span data-ttu-id="95f2b-203">State Province Name</span><span class="sxs-lookup"><span data-stu-id="95f2b-203">State Province Name</span></span>|  
    |<span data-ttu-id="95f2b-204">CountryRegionCode</span><span class="sxs-lookup"><span data-stu-id="95f2b-204">CountryRegionCode</span></span>|<span data-ttu-id="95f2b-205">Country Region Code</span><span class="sxs-lookup"><span data-stu-id="95f2b-205">Country Region Code</span></span>|  
    |<span data-ttu-id="95f2b-206">EnglishCountryRegionName</span><span class="sxs-lookup"><span data-stu-id="95f2b-206">EnglishCountryRegionName</span></span>|<span data-ttu-id="95f2b-207">Country Region Name</span><span class="sxs-lookup"><span data-stu-id="95f2b-207">Country Region Name</span></span>|  
    |<span data-ttu-id="95f2b-208">郵遞區號</span><span class="sxs-lookup"><span data-stu-id="95f2b-208">PostalCode</span></span>|<span data-ttu-id="95f2b-209">郵遞區號</span><span class="sxs-lookup"><span data-stu-id="95f2b-209">Postal Code</span></span>|  
    |<span data-ttu-id="95f2b-210">SalesTerritoryKey</span><span class="sxs-lookup"><span data-stu-id="95f2b-210">SalesTerritoryKey</span></span>|<span data-ttu-id="95f2b-211">Sales Territory Id</span><span class="sxs-lookup"><span data-stu-id="95f2b-211">Sales Territory Id</span></span>|  
  
     <span data-ttu-id="95f2b-212">**產品**</span><span class="sxs-lookup"><span data-stu-id="95f2b-212">**Product**</span></span>  
  
    |<span data-ttu-id="95f2b-213">來源名稱</span><span class="sxs-lookup"><span data-stu-id="95f2b-213">Source Name</span></span>|<span data-ttu-id="95f2b-214">易記名稱</span><span class="sxs-lookup"><span data-stu-id="95f2b-214">Friendly Name</span></span>|  
    |-----------------|-------------------|  
    |<span data-ttu-id="95f2b-215">ProductKey</span><span class="sxs-lookup"><span data-stu-id="95f2b-215">ProductKey</span></span>|<span data-ttu-id="95f2b-216">Product Id</span><span class="sxs-lookup"><span data-stu-id="95f2b-216">Product Id</span></span>|  
    |<span data-ttu-id="95f2b-217">ProductAlternateKey</span><span class="sxs-lookup"><span data-stu-id="95f2b-217">ProductAlternateKey</span></span>|<span data-ttu-id="95f2b-218">Product Alternate Id</span><span class="sxs-lookup"><span data-stu-id="95f2b-218">Product Alternate Id</span></span>|  
    |<span data-ttu-id="95f2b-219">ProductSubcategoryKey</span><span class="sxs-lookup"><span data-stu-id="95f2b-219">ProductSubcategoryKey</span></span>|<span data-ttu-id="95f2b-220">Product Subcategory Id</span><span class="sxs-lookup"><span data-stu-id="95f2b-220">Product Subcategory Id</span></span>|  
    |<span data-ttu-id="95f2b-221">WeightUnitMeasureCode</span><span class="sxs-lookup"><span data-stu-id="95f2b-221">WeightUnitMeasureCode</span></span>|<span data-ttu-id="95f2b-222">Weight Unit Code</span><span class="sxs-lookup"><span data-stu-id="95f2b-222">Weight Unit Code</span></span>|  
    |<span data-ttu-id="95f2b-223">SizeUnitMeasureCode</span><span class="sxs-lookup"><span data-stu-id="95f2b-223">SizeUnitMeasureCode</span></span>|<span data-ttu-id="95f2b-224">Size Unit Code</span><span class="sxs-lookup"><span data-stu-id="95f2b-224">Size Unit Code</span></span>|  
    |<span data-ttu-id="95f2b-225">EnglishProductName</span><span class="sxs-lookup"><span data-stu-id="95f2b-225">EnglishProductName</span></span>|<span data-ttu-id="95f2b-226">產品名稱</span><span class="sxs-lookup"><span data-stu-id="95f2b-226">Product Name</span></span>|  
    |<span data-ttu-id="95f2b-227">StandardCost</span><span class="sxs-lookup"><span data-stu-id="95f2b-227">StandardCost</span></span>|<span data-ttu-id="95f2b-228">Standard Cost</span><span class="sxs-lookup"><span data-stu-id="95f2b-228">Standard Cost</span></span>|  
    |<span data-ttu-id="95f2b-229">FinishedGoodsFlag</span><span class="sxs-lookup"><span data-stu-id="95f2b-229">FinishedGoodsFlag</span></span>|<span data-ttu-id="95f2b-230">Is Finished Product</span><span class="sxs-lookup"><span data-stu-id="95f2b-230">Is Finished Product</span></span>|  
    |<span data-ttu-id="95f2b-231">SafetyStockLevel</span><span class="sxs-lookup"><span data-stu-id="95f2b-231">SafetyStockLevel</span></span>|<span data-ttu-id="95f2b-232">Safety Stock Level</span><span class="sxs-lookup"><span data-stu-id="95f2b-232">Safety Stock Level</span></span>|  
    |<span data-ttu-id="95f2b-233">ReorderPoint</span><span class="sxs-lookup"><span data-stu-id="95f2b-233">ReorderPoint</span></span>|<span data-ttu-id="95f2b-234">Reorder Point</span><span class="sxs-lookup"><span data-stu-id="95f2b-234">Reorder Point</span></span>|  
    |<span data-ttu-id="95f2b-235">ListPrice</span><span class="sxs-lookup"><span data-stu-id="95f2b-235">ListPrice</span></span>|<span data-ttu-id="95f2b-236">List Price</span><span class="sxs-lookup"><span data-stu-id="95f2b-236">List Price</span></span>|  
    |<span data-ttu-id="95f2b-237">SizeRange</span><span class="sxs-lookup"><span data-stu-id="95f2b-237">SizeRange</span></span>|<span data-ttu-id="95f2b-238">Size Range</span><span class="sxs-lookup"><span data-stu-id="95f2b-238">Size Range</span></span>|  
    |<span data-ttu-id="95f2b-239">DaysToManufacture</span><span class="sxs-lookup"><span data-stu-id="95f2b-239">DaysToManufacture</span></span>|<span data-ttu-id="95f2b-240">Days to Manufacture</span><span class="sxs-lookup"><span data-stu-id="95f2b-240">Days to Manufacture</span></span>|  
    |<span data-ttu-id="95f2b-241">ProductLine</span><span class="sxs-lookup"><span data-stu-id="95f2b-241">ProductLine</span></span>|<span data-ttu-id="95f2b-242">Product Line</span><span class="sxs-lookup"><span data-stu-id="95f2b-242">Product Line</span></span>|  
    |<span data-ttu-id="95f2b-243">Dealer Price</span><span class="sxs-lookup"><span data-stu-id="95f2b-243">Dealer Price</span></span>|<span data-ttu-id="95f2b-244">Dealer Price</span><span class="sxs-lookup"><span data-stu-id="95f2b-244">Dealer Price</span></span>|  
    |<span data-ttu-id="95f2b-245">ModelName</span><span class="sxs-lookup"><span data-stu-id="95f2b-245">ModelName</span></span>|<span data-ttu-id="95f2b-246">模型名稱</span><span class="sxs-lookup"><span data-stu-id="95f2b-246">Model Name</span></span>|  
    |<span data-ttu-id="95f2b-247">LargePhoto</span><span class="sxs-lookup"><span data-stu-id="95f2b-247">LargePhoto</span></span>|<span data-ttu-id="95f2b-248">Large Photo</span><span class="sxs-lookup"><span data-stu-id="95f2b-248">Large Photo</span></span>|  
    |<span data-ttu-id="95f2b-249">EnglishDescription</span><span class="sxs-lookup"><span data-stu-id="95f2b-249">EnglishDescription</span></span>|<span data-ttu-id="95f2b-250">Description</span><span class="sxs-lookup"><span data-stu-id="95f2b-250">Description</span></span>|  
    |<span data-ttu-id="95f2b-251">StartDate</span><span class="sxs-lookup"><span data-stu-id="95f2b-251">StartDate</span></span>|<span data-ttu-id="95f2b-252">Product Start Date</span><span class="sxs-lookup"><span data-stu-id="95f2b-252">Product Start Date</span></span>|  
    |<span data-ttu-id="95f2b-253">EndDate</span><span class="sxs-lookup"><span data-stu-id="95f2b-253">EndDate</span></span>|<span data-ttu-id="95f2b-254">Product End Date</span><span class="sxs-lookup"><span data-stu-id="95f2b-254">Product End Date</span></span>|  
    |<span data-ttu-id="95f2b-255">狀態</span><span class="sxs-lookup"><span data-stu-id="95f2b-255">Status</span></span>|<span data-ttu-id="95f2b-256">Product Status</span><span class="sxs-lookup"><span data-stu-id="95f2b-256">Product Status</span></span>|  
  
     <span data-ttu-id="95f2b-257">**產品類別**</span><span class="sxs-lookup"><span data-stu-id="95f2b-257">**Product Category**</span></span>  
  
    |<span data-ttu-id="95f2b-258">來源名稱</span><span class="sxs-lookup"><span data-stu-id="95f2b-258">Source Name</span></span>|<span data-ttu-id="95f2b-259">易記名稱</span><span class="sxs-lookup"><span data-stu-id="95f2b-259">Friendly Name</span></span>|  
    |-----------------|-------------------|  
    |<span data-ttu-id="95f2b-260">ProductCategoryKey</span><span class="sxs-lookup"><span data-stu-id="95f2b-260">ProductCategoryKey</span></span>|<span data-ttu-id="95f2b-261">Product Category Id</span><span class="sxs-lookup"><span data-stu-id="95f2b-261">Product Category Id</span></span>|  
    |<span data-ttu-id="95f2b-262">ProductCategoryAlternateKey</span><span class="sxs-lookup"><span data-stu-id="95f2b-262">ProductCategoryAlternateKey</span></span>|<span data-ttu-id="95f2b-263">Product Category Alternate Id</span><span class="sxs-lookup"><span data-stu-id="95f2b-263">Product Category Alternate Id</span></span>|  
    |<span data-ttu-id="95f2b-264">EnglishProductCategoryName</span><span class="sxs-lookup"><span data-stu-id="95f2b-264">EnglishProductCategoryName</span></span>|<span data-ttu-id="95f2b-265">Product Category Name</span><span class="sxs-lookup"><span data-stu-id="95f2b-265">Product Category Name</span></span>|  
  
     <span data-ttu-id="95f2b-266">**產品子類別目錄**</span><span class="sxs-lookup"><span data-stu-id="95f2b-266">**Product Subcategory**</span></span>  
  
    |<span data-ttu-id="95f2b-267">來源名稱</span><span class="sxs-lookup"><span data-stu-id="95f2b-267">Source Name</span></span>|<span data-ttu-id="95f2b-268">易記名稱</span><span class="sxs-lookup"><span data-stu-id="95f2b-268">Friendly Name</span></span>|  
    |-----------------|-------------------|  
    |<span data-ttu-id="95f2b-269">ProductSubcategoryKey</span><span class="sxs-lookup"><span data-stu-id="95f2b-269">ProductSubcategoryKey</span></span>|<span data-ttu-id="95f2b-270">Product Subcategory Id</span><span class="sxs-lookup"><span data-stu-id="95f2b-270">Product Subcategory Id</span></span>|  
    |<span data-ttu-id="95f2b-271">ProductSubcategoryAlternateKey</span><span class="sxs-lookup"><span data-stu-id="95f2b-271">ProductSubcategoryAlternateKey</span></span>|<span data-ttu-id="95f2b-272">Product Subcategory Alternate Id</span><span class="sxs-lookup"><span data-stu-id="95f2b-272">Product Subcategory Alternate Id</span></span>|  
    |<span data-ttu-id="95f2b-273">EnglishProductSubcategoryName</span><span class="sxs-lookup"><span data-stu-id="95f2b-273">EnglishProductSubcategoryName</span></span>|<span data-ttu-id="95f2b-274">Product Subcategory Name</span><span class="sxs-lookup"><span data-stu-id="95f2b-274">Product Subcategory Name</span></span>|  
    |<span data-ttu-id="95f2b-275">ProductCategoryKey</span><span class="sxs-lookup"><span data-stu-id="95f2b-275">ProductCategoryKey</span></span>|<span data-ttu-id="95f2b-276">Product Category Id</span><span class="sxs-lookup"><span data-stu-id="95f2b-276">Product Category Id</span></span>|  
  
     <span data-ttu-id="95f2b-277">**Internet Sales**</span><span class="sxs-lookup"><span data-stu-id="95f2b-277">**Internet Sales**</span></span>  
  
    |<span data-ttu-id="95f2b-278">來源名稱</span><span class="sxs-lookup"><span data-stu-id="95f2b-278">Source Name</span></span>|<span data-ttu-id="95f2b-279">易記名稱</span><span class="sxs-lookup"><span data-stu-id="95f2b-279">Friendly Name</span></span>|  
    |-----------------|-------------------|  
    |<span data-ttu-id="95f2b-280">ProductKey</span><span class="sxs-lookup"><span data-stu-id="95f2b-280">ProductKey</span></span>|<span data-ttu-id="95f2b-281">Product Id</span><span class="sxs-lookup"><span data-stu-id="95f2b-281">Product Id</span></span>|  
    |<span data-ttu-id="95f2b-282">CustomerKey</span><span class="sxs-lookup"><span data-stu-id="95f2b-282">CustomerKey</span></span>|<span data-ttu-id="95f2b-283">Customer Id</span><span class="sxs-lookup"><span data-stu-id="95f2b-283">Customer Id</span></span>|  
    |<span data-ttu-id="95f2b-284">PromotionKey</span><span class="sxs-lookup"><span data-stu-id="95f2b-284">PromotionKey</span></span>|<span data-ttu-id="95f2b-285">Promotion Id</span><span class="sxs-lookup"><span data-stu-id="95f2b-285">Promotion Id</span></span>|  
    |<span data-ttu-id="95f2b-286">CurrencyKey</span><span class="sxs-lookup"><span data-stu-id="95f2b-286">CurrencyKey</span></span>|<span data-ttu-id="95f2b-287">Currency Id</span><span class="sxs-lookup"><span data-stu-id="95f2b-287">Currency Id</span></span>|  
    |<span data-ttu-id="95f2b-288">SalesTerritoryKey</span><span class="sxs-lookup"><span data-stu-id="95f2b-288">SalesTerritoryKey</span></span>|<span data-ttu-id="95f2b-289">Sales Territory Id</span><span class="sxs-lookup"><span data-stu-id="95f2b-289">Sales Territory Id</span></span>|  
    |<span data-ttu-id="95f2b-290">SalesOrderNumber</span><span class="sxs-lookup"><span data-stu-id="95f2b-290">SalesOrderNumber</span></span>|<span data-ttu-id="95f2b-291">Sales Order Number</span><span class="sxs-lookup"><span data-stu-id="95f2b-291">Sales Order Number</span></span>|  
    |<span data-ttu-id="95f2b-292">SalesOrderLineNumber</span><span class="sxs-lookup"><span data-stu-id="95f2b-292">SalesOrderLineNumber</span></span>|<span data-ttu-id="95f2b-293">Sales Order Line Number</span><span class="sxs-lookup"><span data-stu-id="95f2b-293">Sales Order Line Number</span></span>|  
    |<span data-ttu-id="95f2b-294">RevisionNumber</span><span class="sxs-lookup"><span data-stu-id="95f2b-294">RevisionNumber</span></span>|<span data-ttu-id="95f2b-295">修訂號碼</span><span class="sxs-lookup"><span data-stu-id="95f2b-295">Revision Number</span></span>|  
    |<span data-ttu-id="95f2b-296">OrderQuantity</span><span class="sxs-lookup"><span data-stu-id="95f2b-296">OrderQuantity</span></span>|<span data-ttu-id="95f2b-297">Order Quantity</span><span class="sxs-lookup"><span data-stu-id="95f2b-297">Order Quantity</span></span>|  
    |<span data-ttu-id="95f2b-298">UnitPrice</span><span class="sxs-lookup"><span data-stu-id="95f2b-298">UnitPrice</span></span>|<span data-ttu-id="95f2b-299">單價</span><span class="sxs-lookup"><span data-stu-id="95f2b-299">Unit Price</span></span>|  
    |<span data-ttu-id="95f2b-300">ExtendedAmount</span><span class="sxs-lookup"><span data-stu-id="95f2b-300">ExtendedAmount</span></span>|<span data-ttu-id="95f2b-301">擴充量</span><span class="sxs-lookup"><span data-stu-id="95f2b-301">Extended Amount</span></span>|  
    |<span data-ttu-id="95f2b-302">UnitPriceDiscountPct</span><span class="sxs-lookup"><span data-stu-id="95f2b-302">UnitPriceDiscountPct</span></span>|<span data-ttu-id="95f2b-303">Unit Price Discount Pct</span><span class="sxs-lookup"><span data-stu-id="95f2b-303">Unit Price Discount Pct</span></span>|  
    |<span data-ttu-id="95f2b-304">DiscountAmount</span><span class="sxs-lookup"><span data-stu-id="95f2b-304">DiscountAmount</span></span>|<span data-ttu-id="95f2b-305">折扣量</span><span class="sxs-lookup"><span data-stu-id="95f2b-305">Discount Amount</span></span>|  
    |<span data-ttu-id="95f2b-306">ProductStandardCost</span><span class="sxs-lookup"><span data-stu-id="95f2b-306">ProductStandardCost</span></span>|<span data-ttu-id="95f2b-307">產品標準成本</span><span class="sxs-lookup"><span data-stu-id="95f2b-307">Product Standard Cost</span></span>|  
    |<span data-ttu-id="95f2b-308">TotalProductCost</span><span class="sxs-lookup"><span data-stu-id="95f2b-308">TotalProductCost</span></span>|<span data-ttu-id="95f2b-309">產品總成本</span><span class="sxs-lookup"><span data-stu-id="95f2b-309">Total Product Cost</span></span>|  
    |<span data-ttu-id="95f2b-310">SalesAmount</span><span class="sxs-lookup"><span data-stu-id="95f2b-310">SalesAmount</span></span>|<span data-ttu-id="95f2b-311">銷售量</span><span class="sxs-lookup"><span data-stu-id="95f2b-311">Sales Amount</span></span>|  
    |<span data-ttu-id="95f2b-312">TaxAmt</span><span class="sxs-lookup"><span data-stu-id="95f2b-312">TaxAmt</span></span>|<span data-ttu-id="95f2b-313">稅額</span><span class="sxs-lookup"><span data-stu-id="95f2b-313">Tax Amt</span></span>|  
    |<span data-ttu-id="95f2b-314">CarrierTrackingNumber</span><span class="sxs-lookup"><span data-stu-id="95f2b-314">CarrierTrackingNumber</span></span>|<span data-ttu-id="95f2b-315">Carrier Tracking Number</span><span class="sxs-lookup"><span data-stu-id="95f2b-315">Carrier Tracking Number</span></span>|  
    |<span data-ttu-id="95f2b-316">CustomerPONumber</span><span class="sxs-lookup"><span data-stu-id="95f2b-316">CustomerPONumber</span></span>|<span data-ttu-id="95f2b-317">Customer PO Number</span><span class="sxs-lookup"><span data-stu-id="95f2b-317">Customer PO Number</span></span>|  
    |<span data-ttu-id="95f2b-318">OrderDate</span><span class="sxs-lookup"><span data-stu-id="95f2b-318">OrderDate</span></span>|<span data-ttu-id="95f2b-319">Order Date</span><span class="sxs-lookup"><span data-stu-id="95f2b-319">Order Date</span></span>|  
    |<span data-ttu-id="95f2b-320">DueDate</span><span class="sxs-lookup"><span data-stu-id="95f2b-320">DueDate</span></span>|<span data-ttu-id="95f2b-321">Due Date</span><span class="sxs-lookup"><span data-stu-id="95f2b-321">Due Date</span></span>|  
    |<span data-ttu-id="95f2b-322">ShipDate</span><span class="sxs-lookup"><span data-stu-id="95f2b-322">ShipDate</span></span>|<span data-ttu-id="95f2b-323">Ship Date</span><span class="sxs-lookup"><span data-stu-id="95f2b-323">Ship Date</span></span>|  
  
## <a name="next-step"></a><span data-ttu-id="95f2b-324">後續步驟</span><span class="sxs-lookup"><span data-stu-id="95f2b-324">Next Step</span></span>  
 <span data-ttu-id="95f2b-325">若要繼續進行本教學課程，請前往下一課： [第 4 課：標記為日期資料表](lesson-3-mark-as-date-table.md)。</span><span class="sxs-lookup"><span data-stu-id="95f2b-325">To continue this tutorial, go to the next lesson: [Lesson 4: Mark as Date Table](lesson-3-mark-as-date-table.md).</span></span>  
  
  
