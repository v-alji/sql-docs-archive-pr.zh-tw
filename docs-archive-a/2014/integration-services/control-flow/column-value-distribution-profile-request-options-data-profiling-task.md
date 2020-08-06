---
title: 資料行值散發設定檔要求選項 (資料分析工作) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Data Profiling Task Editor
ms.assetid: c1e5f5de-04f5-4d00-a9f0-55817186bdf9
author: chugugrace
ms.author: chugu
ms.openlocfilehash: bba231bf46600d9608e1a55ad3a084534fec75e0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595225"
---
# <a name="column-value-distribution-profile-request-options-data-profiling-task"></a><span data-ttu-id="c6418-102">資料行值散發設定檔要求選項 (資料分析工作)</span><span class="sxs-lookup"><span data-stu-id="c6418-102">Column Value Distribution Profile Request Options (Data Profiling Task)</span></span>
  <span data-ttu-id="c6418-103">您可以使用 [設定檔要求] 頁面的 [要求屬性] 窗格，針對要求窗格中選取的 [資料行值散發設定檔要求] 設定選項。</span><span class="sxs-lookup"><span data-stu-id="c6418-103">Use the **Request Properties** pane of the **Profile Requests** page to set the options for the **Column Value Distribution Profile Request** selected in the requests pane.</span></span> <span data-ttu-id="c6418-104">資料行值散發設定檔會報告選取之資料行中的所有相異值，以及該資料表中每個值所代表之資料列的百分比。</span><span class="sxs-lookup"><span data-stu-id="c6418-104">A Column Value Distribution profile reports all the distinct values in the selected column and the percentage of rows in the table that each value represents.</span></span> <span data-ttu-id="c6418-105">此設定檔也可以報告代表超過資料表中指定之資料列百分比的值。</span><span class="sxs-lookup"><span data-stu-id="c6418-105">The profile can also report values that represent more than a specified percentage of rows in the table.</span></span> <span data-ttu-id="c6418-106">這個設定檔可協助您識別資料中的問題，例如某個資料行中相異值的數目不正確。</span><span class="sxs-lookup"><span data-stu-id="c6418-106">This profile can help you identify problems in your data such as an incorrect number of distinct values in a column.</span></span> <span data-ttu-id="c6418-107">舉例來說，您分析了「美國州名」資料行並發現超過 50 個相異值。</span><span class="sxs-lookup"><span data-stu-id="c6418-107">For example, you profile a United States state column and discover more than 50 distinct values.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c6418-108">本主題所描述的選項會顯示在 **[資料分析工作編輯器]** 的 **[設定檔要求]** 頁面上。</span><span class="sxs-lookup"><span data-stu-id="c6418-108">The options described in this topic appear on the **Profile Requests page** of the **Data Profiling Task Editor**.</span></span> <span data-ttu-id="c6418-109">如需此編輯器頁面的詳細資訊，請參閱[資料分析工作編輯器 &#40;設定檔要求頁面&#41;](data-profiling-task-editor-profile-requests-page.md)。</span><span class="sxs-lookup"><span data-stu-id="c6418-109">For more information about this page of the editor, see [Data Profiling Task Editor &#40;Profile Requests Page&#41;](data-profiling-task-editor-profile-requests-page.md).</span></span>  
  
 <span data-ttu-id="c6418-110">如需如何使用資料分析工作的詳細資訊，請參閱 [資料分析工作的設定](data-profiling-task.md)。</span><span class="sxs-lookup"><span data-stu-id="c6418-110">For more information about how to use the Data Profiling Task, see [Setup of the Data Profiling Task](data-profiling-task.md).</span></span> <span data-ttu-id="c6418-111">如需如何使用資料設定檔檢視器來分析資料分析工作輸出的詳細資訊，請參閱 [資料設定檔檢視器](data-profile-viewer.md)。</span><span class="sxs-lookup"><span data-stu-id="c6418-111">For more information about how to use the Data Profile Viewer to analyze the output of the Data Profiling Task, see [Data Profile Viewer](data-profile-viewer.md).</span></span>  
  
## <a name="request-properties-options"></a><span data-ttu-id="c6418-112">要求屬性選項</span><span class="sxs-lookup"><span data-stu-id="c6418-112">Request Properties Options</span></span>  
 <span data-ttu-id="c6418-113">[要求屬性] 窗格會針對 [資料行值散發設定檔要求] 顯示下列選項群組：</span><span class="sxs-lookup"><span data-stu-id="c6418-113">For a **Column Value Distribution Profile Request**, the **Request Properties** pane displays the following groups of options:</span></span>  
  
-   <span data-ttu-id="c6418-114">**[資料]** ，其中包括 **[TableOrView]** 和 **[資料行]** 選項。</span><span class="sxs-lookup"><span data-stu-id="c6418-114">**Data**, which includes the **TableOrView** and **Column** options</span></span>  
  
-   <span data-ttu-id="c6418-115">**一般**</span><span class="sxs-lookup"><span data-stu-id="c6418-115">**General**</span></span>  
  
-   <span data-ttu-id="c6418-116">**選項**</span><span class="sxs-lookup"><span data-stu-id="c6418-116">**Options**</span></span>  
  
### <a name="data-options"></a><span data-ttu-id="c6418-117">資料選項</span><span class="sxs-lookup"><span data-stu-id="c6418-117">Data Options</span></span>  
 <span data-ttu-id="c6418-118">**ConnectionManager**</span><span class="sxs-lookup"><span data-stu-id="c6418-118">**ConnectionManager**</span></span>  
 <span data-ttu-id="c6418-119">選取現有的 [!INCLUDE[vstecado](../../includes/vstecado-md.md)] 連線管理員，以便使用 .NET Data Provider for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (SqlClient) 來連線至包含要分析之資料表或檢視表的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫。</span><span class="sxs-lookup"><span data-stu-id="c6418-119">Select the existing [!INCLUDE[vstecado](../../includes/vstecado-md.md)] connection manager that uses the .NET Data Provider for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (SqlClient) to connect to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database that contains the table or view to be profiled.</span></span>  
  
 <span data-ttu-id="c6418-120">**[TableOrView]**</span><span class="sxs-lookup"><span data-stu-id="c6418-120">**TableOrView**</span></span>  
 <span data-ttu-id="c6418-121">選取包含要分析之資料行的資料表或檢視表。</span><span class="sxs-lookup"><span data-stu-id="c6418-121">Select the existing table or view that contains the column to be profiled.</span></span>  
  
 <span data-ttu-id="c6418-122">如需詳細資訊，請參閱本主題中的「TableorView 選項」一節。</span><span class="sxs-lookup"><span data-stu-id="c6418-122">For more information, see the section, "TableorView Options," in this topic.</span></span>  
  
 <span data-ttu-id="c6418-123">**資料行**</span><span class="sxs-lookup"><span data-stu-id="c6418-123">**Column**</span></span>  
 <span data-ttu-id="c6418-124">選取要分析的現有資料行。</span><span class="sxs-lookup"><span data-stu-id="c6418-124">Select the existing column to be profiled.</span></span> <span data-ttu-id="c6418-125">您可以選取 **(\*)** 來分析所有資料行。</span><span class="sxs-lookup"><span data-stu-id="c6418-125">Select **(\*)** to profile all columns.</span></span>  
  
 <span data-ttu-id="c6418-126">如需詳細資訊，請參閱本主題中的「資料行選項」一節。</span><span class="sxs-lookup"><span data-stu-id="c6418-126">For more information, see the section, "Column Options," in this topic.</span></span>  
  
#### <a name="tableorview-options"></a><span data-ttu-id="c6418-127">TableOrView 選項</span><span class="sxs-lookup"><span data-stu-id="c6418-127">TableOrView Options</span></span>  
 <span data-ttu-id="c6418-128">**結構描述**</span><span class="sxs-lookup"><span data-stu-id="c6418-128">**Schema**</span></span>  
 <span data-ttu-id="c6418-129">指定選取之資料表所屬的結構描述。</span><span class="sxs-lookup"><span data-stu-id="c6418-129">Specifies the schema to which the selected table belongs.</span></span> <span data-ttu-id="c6418-130">此選項是唯讀的。</span><span class="sxs-lookup"><span data-stu-id="c6418-130">This option is read-only.</span></span>  
  
 <span data-ttu-id="c6418-131">**Table**</span><span class="sxs-lookup"><span data-stu-id="c6418-131">**Table**</span></span>  
 <span data-ttu-id="c6418-132">顯示選取之資料表的名稱。</span><span class="sxs-lookup"><span data-stu-id="c6418-132">Displays the name of the selected table.</span></span> <span data-ttu-id="c6418-133">此選項是唯讀的。</span><span class="sxs-lookup"><span data-stu-id="c6418-133">This option is read-only.</span></span>  
  
#### <a name="column-options"></a><span data-ttu-id="c6418-134">資料行選項</span><span class="sxs-lookup"><span data-stu-id="c6418-134">Column Options</span></span>  
 <span data-ttu-id="c6418-135">**IsWildCard**</span><span class="sxs-lookup"><span data-stu-id="c6418-135">**IsWildCard**</span></span>  
 <span data-ttu-id="c6418-136">指定是否已經選取 **(\*)** 萬用字元。</span><span class="sxs-lookup"><span data-stu-id="c6418-136">Specifies whether the **(\*)** wildcard has been selected.</span></span> <span data-ttu-id="c6418-137">如果您已選取 **(\*)** 來分析所有資料行，這個選項會設定為 [True]。</span><span class="sxs-lookup"><span data-stu-id="c6418-137">This option is set to **True** if you have selected **(\*)** to profile all columns.</span></span> <span data-ttu-id="c6418-138">如果您已選取要分析的個別資料行，它就會設定為 **[False]** 。</span><span class="sxs-lookup"><span data-stu-id="c6418-138">It is **False** if you have selected an individual column to be profiled.</span></span> <span data-ttu-id="c6418-139">此選項是唯讀的。</span><span class="sxs-lookup"><span data-stu-id="c6418-139">This option is read-only.</span></span>  
  
 <span data-ttu-id="c6418-140">**ColumnName**</span><span class="sxs-lookup"><span data-stu-id="c6418-140">**ColumnName**</span></span>  
 <span data-ttu-id="c6418-141">顯示所選取資料行的名稱。</span><span class="sxs-lookup"><span data-stu-id="c6418-141">Displays the name of the selected column.</span></span> <span data-ttu-id="c6418-142">如果您已選取 **(\*)** 來分析所有資料行，這個選項就是空白的。</span><span class="sxs-lookup"><span data-stu-id="c6418-142">This option is blank if you have selected **(\*)** to profile all columns.</span></span> <span data-ttu-id="c6418-143">此選項是唯讀的。</span><span class="sxs-lookup"><span data-stu-id="c6418-143">This option is read-only.</span></span>  
  
 <span data-ttu-id="c6418-144">**StringCompareOptions**</span><span class="sxs-lookup"><span data-stu-id="c6418-144">**StringCompareOptions**</span></span>  
 <span data-ttu-id="c6418-145">選取比較字串值的選項。</span><span class="sxs-lookup"><span data-stu-id="c6418-145">Select options for comparing string values.</span></span> <span data-ttu-id="c6418-146">這個屬性具有下表中所列的選項。</span><span class="sxs-lookup"><span data-stu-id="c6418-146">This property has the options listed in the following table.</span></span> <span data-ttu-id="c6418-147">這個選項的預設值為 **預設值**頁面上。</span><span class="sxs-lookup"><span data-stu-id="c6418-147">The default value of this option is **Default**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c6418-148">如果您針對 **ColumnName** 使用 **(\*)** 萬用字元，**CompareOptions** 就是唯讀的，而且它會設定為 [預設值] 設定。</span><span class="sxs-lookup"><span data-stu-id="c6418-148">If the **(\*)** wildcard is used for **ColumnName**, **CompareOptions** is read-only and is set to the **Default** setting.</span></span>  
  
|<span data-ttu-id="c6418-149">值</span><span class="sxs-lookup"><span data-stu-id="c6418-149">Value</span></span>|<span data-ttu-id="c6418-150">描述</span><span class="sxs-lookup"><span data-stu-id="c6418-150">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="c6418-151">**預設值**</span><span class="sxs-lookup"><span data-stu-id="c6418-151">**Default**</span></span>|<span data-ttu-id="c6418-152">根據來源資料表中的資料行定序來排序和比較資料。</span><span class="sxs-lookup"><span data-stu-id="c6418-152">Sorts and compares data based on the column's collation in the source table.</span></span>|  
|<span data-ttu-id="c6418-153">**BinarySort**</span><span class="sxs-lookup"><span data-stu-id="c6418-153">**BinarySort**</span></span>|<span data-ttu-id="c6418-154">根據針對每個字元所定義的位元模式來排序和比較資料。</span><span class="sxs-lookup"><span data-stu-id="c6418-154">Sorts and compares data based on the bit patterns defined for each character.</span></span> <span data-ttu-id="c6418-155">二進位排序順序為區分大小寫和區分腔調字。</span><span class="sxs-lookup"><span data-stu-id="c6418-155">Binary sort order is case sensitive and accent sensitive.</span></span> <span data-ttu-id="c6418-156">二進位也是最快的排序順序。</span><span class="sxs-lookup"><span data-stu-id="c6418-156">Binary is also the fastest sorting order.</span></span>|  
|<span data-ttu-id="c6418-157">**DictionarySort**</span><span class="sxs-lookup"><span data-stu-id="c6418-157">**DictionarySort**</span></span>|<span data-ttu-id="c6418-158">根據相關聯之語言或字母字典中所定義的排序和比較規則來排序和比較資料。</span><span class="sxs-lookup"><span data-stu-id="c6418-158">Sorts and compares data based on the sorting and comparison rules as defined in dictionaries for the associated language or alphabet.</span></span>|  
  
 <span data-ttu-id="c6418-159">如果您選取 [DictionarySort]  ，也可以選取下表中所列的任何選項組合。</span><span class="sxs-lookup"><span data-stu-id="c6418-159">If you select **DictionarySort**, you can also select any combination of the options listed in the following table.</span></span> <span data-ttu-id="c6418-160">根據預設，系統不會選取這些額外的選項。</span><span class="sxs-lookup"><span data-stu-id="c6418-160">By default, none of these additional options are selected.</span></span>  
  
|<span data-ttu-id="c6418-161">值</span><span class="sxs-lookup"><span data-stu-id="c6418-161">Value</span></span>|<span data-ttu-id="c6418-162">描述</span><span class="sxs-lookup"><span data-stu-id="c6418-162">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="c6418-163">**IgnoreCase**</span><span class="sxs-lookup"><span data-stu-id="c6418-163">**IgnoreCase**</span></span>|<span data-ttu-id="c6418-164">指定比較是否區分大寫與小寫字母。</span><span class="sxs-lookup"><span data-stu-id="c6418-164">Specifies whether the comparison distinguishes between uppercase and lowercase letters.</span></span> <span data-ttu-id="c6418-165">如果設定此選項，則字串比較會忽略大小寫。</span><span class="sxs-lookup"><span data-stu-id="c6418-165">If this option is set, the string comparison ignores case.</span></span> <span data-ttu-id="c6418-166">例如，「ABC」與「abc」視為一樣。</span><span class="sxs-lookup"><span data-stu-id="c6418-166">For example, "ABC" becomes the same as "abc".</span></span>|  
|<span data-ttu-id="c6418-167">**IgnoreNonSpace**</span><span class="sxs-lookup"><span data-stu-id="c6418-167">**IgnoreNonSpace**</span></span>|<span data-ttu-id="c6418-168">指定比較是否區分空格字元與變音。</span><span class="sxs-lookup"><span data-stu-id="c6418-168">Specifies whether the comparison distinguishes between spacing characters and diacritics.</span></span> <span data-ttu-id="c6418-169">如果設定此選項，則比較會忽略變音符號。</span><span class="sxs-lookup"><span data-stu-id="c6418-169">If this option is set, the comparison ignores diacritics.</span></span> <span data-ttu-id="c6418-170">例如，"å" 等於 "a"。</span><span class="sxs-lookup"><span data-stu-id="c6418-170">For example, "å" is equal to "a".</span></span>|  
|<span data-ttu-id="c6418-171">**IgnoreKanaType**</span><span class="sxs-lookup"><span data-stu-id="c6418-171">**IgnoreKanaType**</span></span>|<span data-ttu-id="c6418-172">指定比較是否區分兩類日文的假名字元：平假名與片假名。</span><span class="sxs-lookup"><span data-stu-id="c6418-172">Specifies whether the comparison distinguishes between the two types of Japanese kana characters: hiragana and katakana.</span></span> <span data-ttu-id="c6418-173">如果設定此選項，則字串比較會忽略假名類型。</span><span class="sxs-lookup"><span data-stu-id="c6418-173">If this option is set, the string comparison ignores kana type.</span></span>|  
|<span data-ttu-id="c6418-174">**IgnoreWidth**</span><span class="sxs-lookup"><span data-stu-id="c6418-174">**IgnoreWidth**</span></span>|<span data-ttu-id="c6418-175">指定比較是否區分單一位元組字元和表示為雙位元組字元的相同字元。</span><span class="sxs-lookup"><span data-stu-id="c6418-175">Specifies whether the comparison distinguishes between a single-byte character and the same character when it is represented as a double-byte character.</span></span> <span data-ttu-id="c6418-176">如果設定此選項，則字串比較會將同一字元的單一位元組表示法和雙位元組表示法視為一樣。</span><span class="sxs-lookup"><span data-stu-id="c6418-176">If this option is set, the string comparison treats single-byte and double-byte representations of the same character as identical.</span></span>|  
  
### <a name="general-options"></a><span data-ttu-id="c6418-177">一般選項</span><span class="sxs-lookup"><span data-stu-id="c6418-177">General Options</span></span>  
 <span data-ttu-id="c6418-178">**RequestID**</span><span class="sxs-lookup"><span data-stu-id="c6418-178">**RequestID**</span></span>  
 <span data-ttu-id="c6418-179">輸入描述性名稱，以便識別這個設定檔要求。</span><span class="sxs-lookup"><span data-stu-id="c6418-179">Type a descriptive name to identify this profile request.</span></span> <span data-ttu-id="c6418-180">一般而言，您不需要變更自動產生的值。</span><span class="sxs-lookup"><span data-stu-id="c6418-180">Typically, you do not have to change the autogenerated value.</span></span>  
  
### <a name="options"></a><span data-ttu-id="c6418-181">選項。</span><span class="sxs-lookup"><span data-stu-id="c6418-181">Options</span></span>  
 <span data-ttu-id="c6418-182">**ValueDistributionOption**</span><span class="sxs-lookup"><span data-stu-id="c6418-182">**ValueDistributionOption**</span></span>  
 <span data-ttu-id="c6418-183">指定是否要計算所有資料行值的散發。</span><span class="sxs-lookup"><span data-stu-id="c6418-183">Specify whether to compute the distribution for all column values.</span></span> <span data-ttu-id="c6418-184">這個選項的預設值為 **FrequentValues**。</span><span class="sxs-lookup"><span data-stu-id="c6418-184">The default value of this option is **FrequentValues**.</span></span>  
  
|<span data-ttu-id="c6418-185">值</span><span class="sxs-lookup"><span data-stu-id="c6418-185">Value</span></span>|<span data-ttu-id="c6418-186">描述</span><span class="sxs-lookup"><span data-stu-id="c6418-186">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="c6418-187">**AllValues**</span><span class="sxs-lookup"><span data-stu-id="c6418-187">**AllValues**</span></span>|<span data-ttu-id="c6418-188">計算所有資料行值的散發。</span><span class="sxs-lookup"><span data-stu-id="c6418-188">The distribution is computed for all column values.</span></span>|  
|<span data-ttu-id="c6418-189">**FrequentValues**</span><span class="sxs-lookup"><span data-stu-id="c6418-189">**FrequentValues**</span></span>|<span data-ttu-id="c6418-190">僅針對頻率超過 **FrequentValueThreshold**中指定之最小值的值計算散發。</span><span class="sxs-lookup"><span data-stu-id="c6418-190">The distribution is computed only for values whose frequency exceeds the minimum value specified in **FrequentValueThreshold**.</span></span> <span data-ttu-id="c6418-191">輸出報表會排除不符合 **FrequentValueThreshold** 的值。</span><span class="sxs-lookup"><span data-stu-id="c6418-191">Values that do not meet the **FrequentValueThreshold** are excluded from the output report.</span></span>|  
  
 <span data-ttu-id="c6418-192">**FrequentValueThreshold**</span><span class="sxs-lookup"><span data-stu-id="c6418-192">**FrequentValueThreshold**</span></span>  
 <span data-ttu-id="c6418-193">指定臨界值 (使用介於 0 與 1 之間的值)，而且超過此值就應該報告資料行值。</span><span class="sxs-lookup"><span data-stu-id="c6418-193">Specify the threshold (by using a value between 0 and 1) above which the column value should be reported.</span></span> <span data-ttu-id="c6418-194">當您選取 **AllValues** 當作 **ValueDistributionOption**時，這個選項是停用的。</span><span class="sxs-lookup"><span data-stu-id="c6418-194">This option is disabled when you select **AllValues** as the **ValueDistributionOption**.</span></span> <span data-ttu-id="c6418-195">這個選項的預設值為 0.001。</span><span class="sxs-lookup"><span data-stu-id="c6418-195">The default value of this option is 0.001.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6418-196">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c6418-196">See Also</span></span>  
 <span data-ttu-id="c6418-197">[資料分析工作編輯器 &#40;一般頁面&#41;](../general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="c6418-197">[Data Profiling Task Editor &#40;General Page&#41;](../general-page-of-integration-services-designers-options.md) </span></span>  
 [<span data-ttu-id="c6418-198">單一資料表快速分析表單 &#40;資料分析工作&#41;</span><span class="sxs-lookup"><span data-stu-id="c6418-198">Single Table Quick Profile Form &#40;Data Profiling Task&#41;</span></span>](single-table-quick-profile-form-data-profiling-task.md)  
  
  
