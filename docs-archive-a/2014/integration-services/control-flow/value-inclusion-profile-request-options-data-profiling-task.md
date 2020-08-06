---
title: 值包含設定檔要求選項 (資料分析工作) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Data Profiling Task Editor
ms.assetid: ca94da82-a4c9-4e87-9cba-c2d85bd31f01
author: chugugrace
ms.author: chugu
ms.openlocfilehash: cbbd40dd4a2c0b1abca6dd18166f823d5fec8904
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592806"
---
# <a name="value-inclusion-profile-request-options-data-profiling-task"></a><span data-ttu-id="9bac9-102">值包含設定檔要求選項 (資料分析工作)</span><span class="sxs-lookup"><span data-stu-id="9bac9-102">Value Inclusion Profile Request Options (Data Profiling Task)</span></span>
  <span data-ttu-id="9bac9-103">您可以使用 [設定檔要求] 頁面的 [要求屬性] 窗格，針對要求窗格中選取的 [值包含設定檔要求] 設定選項。</span><span class="sxs-lookup"><span data-stu-id="9bac9-103">Use the **Request Properties** pane of the **Profile Requests** page to set the options for the **Value Inclusion Profile Request** selected in the requests pane.</span></span> <span data-ttu-id="9bac9-104">值包含設定檔會計算兩個資料行或資料行集合之間值的重疊。</span><span class="sxs-lookup"><span data-stu-id="9bac9-104">A Value Inclusion profile computes the overlap in the values between two columns or sets of columns.</span></span> <span data-ttu-id="9bac9-105">因此，它也可以判斷資料行或資料行集合是否適合當做選取之資料表之間的外部索引鍵。</span><span class="sxs-lookup"><span data-stu-id="9bac9-105">Thus, it can also determine whether a column or set of columns is appropriate to serve as a foreign key between the selected tables.</span></span> <span data-ttu-id="9bac9-106">這個設定檔也可協助您識別資料中的問題，例如無效的值。</span><span class="sxs-lookup"><span data-stu-id="9bac9-106">This profile can also help you identify problems in your data such as invalid values.</span></span> <span data-ttu-id="9bac9-107">舉例來說，您使用了值包含設定檔來分析 Sales 資料表的 ProductID 資料行。</span><span class="sxs-lookup"><span data-stu-id="9bac9-107">For example, you use a value inclusion profile to profile the ProductID column of a Sales table.</span></span> <span data-ttu-id="9bac9-108">此設定檔發現該資料行包含在 Products 資料表之 ProductID 資料行中找不到的值。</span><span class="sxs-lookup"><span data-stu-id="9bac9-108">The profile discovers that the column contains values that are not found in the ProductID column of the Products table.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9bac9-109">本主題所描述的選項會顯示在 **[資料分析工作編輯器]** 的 **[設定檔要求]** 頁面上。</span><span class="sxs-lookup"><span data-stu-id="9bac9-109">The options described in this topic appear on the **Profile Requests page** of the **Data Profiling Task Editor**.</span></span> <span data-ttu-id="9bac9-110">如需此編輯器頁面的詳細資訊，請參閱[資料分析工作編輯器 &#40;設定檔要求頁面&#41;](data-profiling-task-editor-profile-requests-page.md)。</span><span class="sxs-lookup"><span data-stu-id="9bac9-110">For more information about this page of the editor, see [Data Profiling Task Editor &#40;Profile Requests Page&#41;](data-profiling-task-editor-profile-requests-page.md).</span></span>  
  
 <span data-ttu-id="9bac9-111">如需如何使用資料分析工作的詳細資訊，請參閱 [資料分析工作的設定](data-profiling-task.md)。</span><span class="sxs-lookup"><span data-stu-id="9bac9-111">For more information about how to use the Data Profiling Task, see [Setup of the Data Profiling Task](data-profiling-task.md).</span></span> <span data-ttu-id="9bac9-112">如需如何使用資料設定檔檢視器來分析資料分析工作輸出的詳細資訊，請參閱 [資料設定檔檢視器](data-profile-viewer.md)。</span><span class="sxs-lookup"><span data-stu-id="9bac9-112">For more information about how to use the Data Profile Viewer to analyze the output of the Data Profiling Task, see [Data Profile Viewer](data-profile-viewer.md).</span></span>  
  
## <a name="understanding-the-selection-of-columns-for-the-inclusioncolumns-property"></a><span data-ttu-id="9bac9-113">了解 InclusionColumns 屬性之資料行的選擇</span><span class="sxs-lookup"><span data-stu-id="9bac9-113">Understanding the Selection of Columns for the InclusionColumns Property</span></span>  
 <span data-ttu-id="9bac9-114">[值包含設定檔要求]  會計算某個子集中的所有值是否都會出現在超集中。</span><span class="sxs-lookup"><span data-stu-id="9bac9-114">A **Value Inclusion Profile Request** computes whether all the values in a subset are present in the superset.</span></span> <span data-ttu-id="9bac9-115">超集通常是查閱或參考資料表。</span><span class="sxs-lookup"><span data-stu-id="9bac9-115">The superset is often a lookup or reference table.</span></span> <span data-ttu-id="9bac9-116">例如，地址資料表中的州名資料行就是子集資料表。</span><span class="sxs-lookup"><span data-stu-id="9bac9-116">For example, the state column in a table of addresses is the subset table.</span></span> <span data-ttu-id="9bac9-117">這個資料行中的每個二字元州名代碼也應該可在美國郵遞服務州名代碼的資料表 (超集資料表) 中找到。</span><span class="sxs-lookup"><span data-stu-id="9bac9-117">Every two-character state code in this column should also be found in the table of United States Postal Service state codes, which is the superset table.</span></span>  
  
 <span data-ttu-id="9bac9-118">當您使用 (\*) 萬用字元當做子集資料行或超集資料行的值時，資料分析工作會比較該端的每個資料行與另一端指定的資料行。</span><span class="sxs-lookup"><span data-stu-id="9bac9-118">When you use the (\*) wildcard as the value of the subset column or the superset column, the Data Profiling task compares each column on that side against the column specified on the other side.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9bac9-119">如果您選取 (\*)，這個選項可能會產生大量計算並降低工作的效能。</span><span class="sxs-lookup"><span data-stu-id="9bac9-119">If you select (\*), this option might result in a large number of computations and decrease the performance of the task.</span></span>  
  
## <a name="understanding-the-threshold-settings"></a><span data-ttu-id="9bac9-120">了解臨界值設定</span><span class="sxs-lookup"><span data-stu-id="9bac9-120">Understanding the Threshold Settings</span></span>  
 <span data-ttu-id="9bac9-121">您可以使用兩個不同的臨界值設定來精簡值包含設定檔要求的輸出。</span><span class="sxs-lookup"><span data-stu-id="9bac9-121">You can use two different threshold settings to refine the output of a Value Inclusion Profile Request.</span></span>  
  
 <span data-ttu-id="9bac9-122">當您針對 [InclusionThresholdSetting]  指定 **None** 以外的值時，只有在下列其中一項條件底下，此設定檔才會報告超集中子集的包含強度：</span><span class="sxs-lookup"><span data-stu-id="9bac9-122">When you specify a value other than **None** for **InclusionThresholdSetting**, the profile reports the inclusion strength of the subset in the superset only under one of the following conditions:</span></span>  
  
-   <span data-ttu-id="9bac9-123">當包含強度超過 [InclusionStrengthThreshold]  中指定的臨界值時。</span><span class="sxs-lookup"><span data-stu-id="9bac9-123">When the inclusion strength exceeds the threshold specified in **InclusionStrengthThreshold**.</span></span>  
  
-   <span data-ttu-id="9bac9-124">當包含強度具有 1.0 的值，而且 [InclusionStrengthThreshold]  設定為 [精確]  時。</span><span class="sxs-lookup"><span data-stu-id="9bac9-124">When the inclusion strength has a value of 1.0 and the **InclusionStrengthThreshold** is set to **Exact**.</span></span>  
  
 <span data-ttu-id="9bac9-125">您可以透過篩選出超集資料行並非超集資料表之適當索引鍵的組合 (因為非唯一的值)，進一步精簡輸出。</span><span class="sxs-lookup"><span data-stu-id="9bac9-125">You can refine the output more by filtering out combinations where the superset column is not an appropriate key for the superset table because of non-unique values.</span></span> <span data-ttu-id="9bac9-126">當您針對 [SupersetColumnsKeyThresholdSetting] 指定 **None** 以外的值時，只有在下列其中一項條件底下，此設定檔才會報告超集中子集的包含強度：</span><span class="sxs-lookup"><span data-stu-id="9bac9-126">When you specify a value other than **None** for **SupersetColumnsKeyThresholdSetting**, the profile reports the inclusion strength of the subset in the superset only under one of the following conditions:</span></span>  
  
-   <span data-ttu-id="9bac9-127">當超集資料行當作超集資料表之索引鍵的適合性超過 [SupersetColumnsKeyThreshold]  中指定的臨界值時</span><span class="sxs-lookup"><span data-stu-id="9bac9-127">When the suitability of the superset columns as a key in the superset table exceeds the threshold specified in **SupersetColumnsKeyThreshold**</span></span>  
  
-   <span data-ttu-id="9bac9-128">當包含強度具有 1.0 的值，而且 [SupersetColumnsKeyThreshold]  設定為 [精確]  時。</span><span class="sxs-lookup"><span data-stu-id="9bac9-128">When the inclusion strength has a value or 1.0 and the **SupersetColumnsKeyThreshold** is set to **Exact**.</span></span>  
  
## <a name="request-properties-options"></a><span data-ttu-id="9bac9-129">要求屬性選項</span><span class="sxs-lookup"><span data-stu-id="9bac9-129">Request Properties Options</span></span>  
 <span data-ttu-id="9bac9-130">[要求屬性] 窗格會針對 [值包含設定檔要求] 顯示下列選項群組：</span><span class="sxs-lookup"><span data-stu-id="9bac9-130">For a **Value Inclusion Profile Request**, the **Request Properties** pane displays the following groups of options:</span></span>  
  
-   <span data-ttu-id="9bac9-131">[資料]  ，其中包括 [SubsetTableOrView]  、[SupersetTableOrView]  和 [InclusionColumns]  選項</span><span class="sxs-lookup"><span data-stu-id="9bac9-131">**Data**, which includes the **SubsetTableOrView**, **SupersetTableOrView**, and **InclusionColumns** options</span></span>  
  
-   <span data-ttu-id="9bac9-132">**一般**</span><span class="sxs-lookup"><span data-stu-id="9bac9-132">**General**</span></span>  
  
-   <span data-ttu-id="9bac9-133">**選項**</span><span class="sxs-lookup"><span data-stu-id="9bac9-133">**Options**</span></span>  
  
### <a name="data-options"></a><span data-ttu-id="9bac9-134">資料選項</span><span class="sxs-lookup"><span data-stu-id="9bac9-134">Data Options</span></span>  
 <span data-ttu-id="9bac9-135">**ConnectionManager**</span><span class="sxs-lookup"><span data-stu-id="9bac9-135">**ConnectionManager**</span></span>  
 <span data-ttu-id="9bac9-136">選取現有的 [!INCLUDE[vstecado](../../includes/vstecado-md.md)] 連線管理員，以便使用 .NET Data Provider for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (SqlClient) 來連線至包含要分析之資料表或檢視表的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫。</span><span class="sxs-lookup"><span data-stu-id="9bac9-136">Select the existing [!INCLUDE[vstecado](../../includes/vstecado-md.md)] connection manager that uses the .NET Data Provider for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (SqlClient) to connect to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database that contains the table or view to be profiled.</span></span>  
  
 <span data-ttu-id="9bac9-137">**SubsetTableOrView**</span><span class="sxs-lookup"><span data-stu-id="9bac9-137">**SubsetTableOrView**</span></span>  
 <span data-ttu-id="9bac9-138">選取要分析的現有資料表或檢視表。</span><span class="sxs-lookup"><span data-stu-id="9bac9-138">Select the existing table or view to be profiled.</span></span>  
  
 <span data-ttu-id="9bac9-139">如需詳細資訊，請參閱這個主題中的「SubsetTableOrView 和 SupersetTableOrView 選項」一節。</span><span class="sxs-lookup"><span data-stu-id="9bac9-139">For more information, see the section, "SubsetTableOrView and SupersetTableOrView Options," in this topic.</span></span>  
  
 <span data-ttu-id="9bac9-140">**SupersetTableOrView**</span><span class="sxs-lookup"><span data-stu-id="9bac9-140">**SupersetTableOrView**</span></span>  
 <span data-ttu-id="9bac9-141">選取要分析的現有資料表或檢視表。</span><span class="sxs-lookup"><span data-stu-id="9bac9-141">Select the existing table or view to be profiled.</span></span>  
  
 <span data-ttu-id="9bac9-142">如需詳細資訊，請參閱這個主題中的「SubsetTableOrView 和 SupersetTableOrView 選項」一節。</span><span class="sxs-lookup"><span data-stu-id="9bac9-142">For more information, see the section, "SubsetTableOrView and SupersetTableOrView Options," in this topic.</span></span>  
  
 <span data-ttu-id="9bac9-143">**InclusionColumns**</span><span class="sxs-lookup"><span data-stu-id="9bac9-143">**InclusionColumns**</span></span>  
 <span data-ttu-id="9bac9-144">從子集和超集資料表中選取資料行或資料行集合。</span><span class="sxs-lookup"><span data-stu-id="9bac9-144">Select the columns or sets of columns from the subset and superset tables.</span></span>  
  
 <span data-ttu-id="9bac9-145">如需詳細資訊，請參閱本主題的「了解 InclusionColumns 屬性之資料行的選擇」和「InclusionColumns 選項」章節。</span><span class="sxs-lookup"><span data-stu-id="9bac9-145">For more information, see the sections, "Understanding the Selection of Columns for the InclusionColumns Property" and "InclusionColumns Options," in this topic.</span></span>  
  
#### <a name="subsettableorview-and-supersettableorview-options"></a><span data-ttu-id="9bac9-146">SubsetTableOrView 和 SupersetTableOrView 選項</span><span class="sxs-lookup"><span data-stu-id="9bac9-146">SubsetTableOrView and SupersetTableOrView Options</span></span>  
 <span data-ttu-id="9bac9-147">**結構描述**</span><span class="sxs-lookup"><span data-stu-id="9bac9-147">**Schema**</span></span>  
 <span data-ttu-id="9bac9-148">指定選取之資料表所屬的結構描述。</span><span class="sxs-lookup"><span data-stu-id="9bac9-148">Specifies the schema to which the selected table belongs.</span></span> <span data-ttu-id="9bac9-149">此選項是唯讀的。</span><span class="sxs-lookup"><span data-stu-id="9bac9-149">This option is read-only.</span></span>  
  
 <span data-ttu-id="9bac9-150">**[TableOrView]**</span><span class="sxs-lookup"><span data-stu-id="9bac9-150">**TableOrView**</span></span>  
 <span data-ttu-id="9bac9-151">顯示選取之資料表的名稱。</span><span class="sxs-lookup"><span data-stu-id="9bac9-151">Displays the name of the selected table.</span></span> <span data-ttu-id="9bac9-152">此選項是唯讀的。</span><span class="sxs-lookup"><span data-stu-id="9bac9-152">This option is read-only.</span></span>  
  
#### <a name="inclusioncolumns-options"></a><span data-ttu-id="9bac9-153">InclusionColumns 選項</span><span class="sxs-lookup"><span data-stu-id="9bac9-153">InclusionColumns Options</span></span>  
 <span data-ttu-id="9bac9-154">下列選項會呈現給在 **[InclusionColumns]** 中選取待分析的每個資料行集合。</span><span class="sxs-lookup"><span data-stu-id="9bac9-154">The following options are presented for each set of columns selected for profiling in **InclusionColumns**.</span></span>  
  
 <span data-ttu-id="9bac9-155">如需詳細資訊，請參閱本主題前面的「了解 InclusionColumns 屬性之資料行的選擇」一節。</span><span class="sxs-lookup"><span data-stu-id="9bac9-155">For more information, see the section, "Understanding the Selection of Columns for the InclusionColumns Property," earlier in this topic.</span></span>  
  
 <span data-ttu-id="9bac9-156">**IsWildcard**</span><span class="sxs-lookup"><span data-stu-id="9bac9-156">**IsWildcard**</span></span>  
 <span data-ttu-id="9bac9-157">指定是否已經選取 **(\*)** 萬用字元。</span><span class="sxs-lookup"><span data-stu-id="9bac9-157">Specifies whether the **(\*)** wildcard has been selected.</span></span> <span data-ttu-id="9bac9-158">如果您已選取 **(\*)** 來分析所有資料行，這個選項會設定為 [True]。</span><span class="sxs-lookup"><span data-stu-id="9bac9-158">This option is set to **True** if you have selected **(\*)** to profile all columns.</span></span> <span data-ttu-id="9bac9-159">如果您已選取要分析的個別資料行，它就會設定為 **[False]** 。</span><span class="sxs-lookup"><span data-stu-id="9bac9-159">It is **False** if you have selected an individual column to be profiled.</span></span> <span data-ttu-id="9bac9-160">此選項是唯讀的。</span><span class="sxs-lookup"><span data-stu-id="9bac9-160">This option is read-only.</span></span>  
  
 <span data-ttu-id="9bac9-161">**ColumnName**</span><span class="sxs-lookup"><span data-stu-id="9bac9-161">**ColumnName**</span></span>  
 <span data-ttu-id="9bac9-162">顯示所選取資料行的名稱。</span><span class="sxs-lookup"><span data-stu-id="9bac9-162">Displays the name of the selected column.</span></span> <span data-ttu-id="9bac9-163">如果您已選取 **(\*)** 來分析所有資料行，這個選項就是空白的。</span><span class="sxs-lookup"><span data-stu-id="9bac9-163">This option is blank if you have selected **(\*)** to profile all columns.</span></span> <span data-ttu-id="9bac9-164">此選項是唯讀的。</span><span class="sxs-lookup"><span data-stu-id="9bac9-164">This option is read-only.</span></span>  
  
 <span data-ttu-id="9bac9-165">**StringCompareOptions**</span><span class="sxs-lookup"><span data-stu-id="9bac9-165">**StringCompareOptions**</span></span>  
 <span data-ttu-id="9bac9-166">選取比較字串值的選項。</span><span class="sxs-lookup"><span data-stu-id="9bac9-166">Select options for comparing string values.</span></span> <span data-ttu-id="9bac9-167">這個屬性具有下表中所列的選項。</span><span class="sxs-lookup"><span data-stu-id="9bac9-167">This property has the options listed in the following table.</span></span> <span data-ttu-id="9bac9-168">這個選項的預設值為 **預設值**頁面上。</span><span class="sxs-lookup"><span data-stu-id="9bac9-168">The default value of this option is **Default**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9bac9-169">當您針對 **ColumnName** 使用 **(\*)** 萬用字元時，**CompareOptions** 就是唯讀的，而且它會設定為 [預設值] 設定。</span><span class="sxs-lookup"><span data-stu-id="9bac9-169">When you use the **(\*)** wildcard for **ColumnName**, **CompareOptions** is read-only and is set to the **Default** setting.</span></span>  
  
|<span data-ttu-id="9bac9-170">值</span><span class="sxs-lookup"><span data-stu-id="9bac9-170">Value</span></span>|<span data-ttu-id="9bac9-171">描述</span><span class="sxs-lookup"><span data-stu-id="9bac9-171">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="9bac9-172">**預設值**</span><span class="sxs-lookup"><span data-stu-id="9bac9-172">**Default**</span></span>|<span data-ttu-id="9bac9-173">根據來源資料表中的資料行定序來排序和比較資料。</span><span class="sxs-lookup"><span data-stu-id="9bac9-173">Sorts and compares data based on the column's collation in the source table.</span></span>|  
|<span data-ttu-id="9bac9-174">**BinarySort**</span><span class="sxs-lookup"><span data-stu-id="9bac9-174">**BinarySort**</span></span>|<span data-ttu-id="9bac9-175">根據針對每個字元所定義的位元模式來排序和比較資料。</span><span class="sxs-lookup"><span data-stu-id="9bac9-175">Sorts and compares data based on the bit patterns defined for each character.</span></span> <span data-ttu-id="9bac9-176">二進位排序順序為區分大小寫和區分腔調字。</span><span class="sxs-lookup"><span data-stu-id="9bac9-176">Binary sort order is case sensitive and accent sensitive.</span></span> <span data-ttu-id="9bac9-177">二進位也是最快的排序順序。</span><span class="sxs-lookup"><span data-stu-id="9bac9-177">Binary is also the fastest sorting order.</span></span>|  
|<span data-ttu-id="9bac9-178">**DictionarySort**</span><span class="sxs-lookup"><span data-stu-id="9bac9-178">**DictionarySort**</span></span>|<span data-ttu-id="9bac9-179">根據相關聯之語言或字母字典中所定義的排序和比較規則來排序和比較資料。</span><span class="sxs-lookup"><span data-stu-id="9bac9-179">Sorts and compares data based on the sorting and comparison rules as defined in dictionaries for the associated language or alphabet.</span></span>|  
  
 <span data-ttu-id="9bac9-180">如果您選取 [DictionarySort]  ，也可以選取下表中所列的任何選項組合。</span><span class="sxs-lookup"><span data-stu-id="9bac9-180">If you select **DictionarySort**, you can also select any combination of the options listed in the following table.</span></span> <span data-ttu-id="9bac9-181">根據預設，系統不會選取這些額外的選項。</span><span class="sxs-lookup"><span data-stu-id="9bac9-181">By default, none of these additional options are selected.</span></span>  
  
|<span data-ttu-id="9bac9-182">值</span><span class="sxs-lookup"><span data-stu-id="9bac9-182">Value</span></span>|<span data-ttu-id="9bac9-183">描述</span><span class="sxs-lookup"><span data-stu-id="9bac9-183">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="9bac9-184">**IgnoreCase**</span><span class="sxs-lookup"><span data-stu-id="9bac9-184">**IgnoreCase**</span></span>|<span data-ttu-id="9bac9-185">指定比較是否區分大寫與小寫字母。</span><span class="sxs-lookup"><span data-stu-id="9bac9-185">Specifies whether the comparison distinguishes between uppercase and lowercase letters.</span></span> <span data-ttu-id="9bac9-186">如果設定此選項，則字串比較會忽略大小寫。</span><span class="sxs-lookup"><span data-stu-id="9bac9-186">If this option is set, the string comparison ignores case.</span></span> <span data-ttu-id="9bac9-187">例如，「ABC」與「abc」視為一樣。</span><span class="sxs-lookup"><span data-stu-id="9bac9-187">For example, "ABC" becomes the same as "abc".</span></span>|  
|<span data-ttu-id="9bac9-188">**IgnoreNonSpace**</span><span class="sxs-lookup"><span data-stu-id="9bac9-188">**IgnoreNonSpace**</span></span>|<span data-ttu-id="9bac9-189">指定比較是否區分空格字元與變音。</span><span class="sxs-lookup"><span data-stu-id="9bac9-189">Specifies whether the comparison distinguishes between spacing characters and diacritics.</span></span> <span data-ttu-id="9bac9-190">如果設定此選項，則比較會忽略變音符號。</span><span class="sxs-lookup"><span data-stu-id="9bac9-190">If this option is set, the comparison ignores diacritics.</span></span> <span data-ttu-id="9bac9-191">例如，"å" 等於 "a"。</span><span class="sxs-lookup"><span data-stu-id="9bac9-191">For example, "å" is equal to "a".</span></span>|  
|<span data-ttu-id="9bac9-192">**IgnoreKanaType**</span><span class="sxs-lookup"><span data-stu-id="9bac9-192">**IgnoreKanaType**</span></span>|<span data-ttu-id="9bac9-193">指定比較是否區分兩類日文的假名字元：平假名與片假名。</span><span class="sxs-lookup"><span data-stu-id="9bac9-193">Specifies whether the comparison distinguishes between the two types of Japanese kana characters: hiragana and katakana.</span></span> <span data-ttu-id="9bac9-194">如果設定此選項，則字串比較會忽略假名類型。</span><span class="sxs-lookup"><span data-stu-id="9bac9-194">If this option is set, the string comparison ignores kana type.</span></span>|  
|<span data-ttu-id="9bac9-195">**IgnoreWidth**</span><span class="sxs-lookup"><span data-stu-id="9bac9-195">**IgnoreWidth**</span></span>|<span data-ttu-id="9bac9-196">指定比較是否區分單一位元組字元和表示為雙位元組字元的相同字元。</span><span class="sxs-lookup"><span data-stu-id="9bac9-196">Specifies whether the comparison distinguishes between a single-byte character and the same character when it is represented as a double-byte character.</span></span> <span data-ttu-id="9bac9-197">如果設定此選項，則字串比較會將同一字元的單一位元組表示法和雙位元組表示法視為一樣。</span><span class="sxs-lookup"><span data-stu-id="9bac9-197">If this option is set, the string comparison treats single-byte and double-byte representations of the same character as identical.</span></span>|  
  
### <a name="general-options"></a><span data-ttu-id="9bac9-198">一般選項</span><span class="sxs-lookup"><span data-stu-id="9bac9-198">General Options</span></span>  
 <span data-ttu-id="9bac9-199">**RequestID**</span><span class="sxs-lookup"><span data-stu-id="9bac9-199">**RequestID**</span></span>  
 <span data-ttu-id="9bac9-200">輸入描述性名稱，以便識別這個設定檔要求。</span><span class="sxs-lookup"><span data-stu-id="9bac9-200">Type a descriptive name to identify this profile request.</span></span> <span data-ttu-id="9bac9-201">一般而言，您不需要變更自動產生的值。</span><span class="sxs-lookup"><span data-stu-id="9bac9-201">Typically, you do not have to change the autogenerated value.</span></span>  
  
### <a name="options"></a><span data-ttu-id="9bac9-202">選項。</span><span class="sxs-lookup"><span data-stu-id="9bac9-202">Options</span></span>  
 <span data-ttu-id="9bac9-203">**InclusionThresholdSetting**</span><span class="sxs-lookup"><span data-stu-id="9bac9-203">**InclusionThresholdSetting**</span></span>  
 <span data-ttu-id="9bac9-204">選取臨界值設定，以便精簡設定檔的輸出。</span><span class="sxs-lookup"><span data-stu-id="9bac9-204">Select the threshold setting to refine the output of the profile.</span></span> <span data-ttu-id="9bac9-205">這個屬性的預設值為 [已指定]  。</span><span class="sxs-lookup"><span data-stu-id="9bac9-205">The default value of this property is **Specified**.</span></span> <span data-ttu-id="9bac9-206">如需詳細資訊，請參閱本主題前面的「了解臨界值設定」一節。</span><span class="sxs-lookup"><span data-stu-id="9bac9-206">For more information, see the section, "Understanding the Threshold Settings," earlier in this topic.</span></span>  
  
|<span data-ttu-id="9bac9-207">值</span><span class="sxs-lookup"><span data-stu-id="9bac9-207">Value</span></span>|<span data-ttu-id="9bac9-208">描述</span><span class="sxs-lookup"><span data-stu-id="9bac9-208">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="9bac9-209">**None**</span><span class="sxs-lookup"><span data-stu-id="9bac9-209">**None**</span></span>|<span data-ttu-id="9bac9-210">沒有指定臨界值。</span><span class="sxs-lookup"><span data-stu-id="9bac9-210">Does not specify a threshold.</span></span> <span data-ttu-id="9bac9-211">不論索引鍵強度為何，系統都會報告此值。</span><span class="sxs-lookup"><span data-stu-id="9bac9-211">The key strength is reported regardless of its value.</span></span>|  
|<span data-ttu-id="9bac9-212">**已指定**</span><span class="sxs-lookup"><span data-stu-id="9bac9-212">**Specified**</span></span>|<span data-ttu-id="9bac9-213">使用 **InclusionStrengthThreshold**中指定的臨界值。</span><span class="sxs-lookup"><span data-stu-id="9bac9-213">Use the threshold that is specified in **InclusionStrengthThreshold**.</span></span> <span data-ttu-id="9bac9-214">只有當包含強度大於臨界值時，系統才會報告此值。</span><span class="sxs-lookup"><span data-stu-id="9bac9-214">The inclusion strength is reported only if it is greater than the threshold.</span></span>|  
|<span data-ttu-id="9bac9-215">**精確**</span><span class="sxs-lookup"><span data-stu-id="9bac9-215">**Exact**</span></span>|<span data-ttu-id="9bac9-216">沒有指定臨界值。</span><span class="sxs-lookup"><span data-stu-id="9bac9-216">Does not specify a threshold.</span></span> <span data-ttu-id="9bac9-217">只有當子集值完全包含在超集值中時，系統才會報告包含強度。</span><span class="sxs-lookup"><span data-stu-id="9bac9-217">The inclusion strength is reported only if the subset values are completedly included in the upserset values.</span></span>|  
  
 <span data-ttu-id="9bac9-218">**InclusionStrengthThreshold**</span><span class="sxs-lookup"><span data-stu-id="9bac9-218">**InclusionStrengthThreshold**</span></span>  
 <span data-ttu-id="9bac9-219">指定臨界值 (使用介於 0 與 1 之間的值)，而且超過此值就應該報告包含強度。</span><span class="sxs-lookup"><span data-stu-id="9bac9-219">Specify the threshold (by using a value between 0 and 1) above which the inclusion strength should be reported.</span></span> <span data-ttu-id="9bac9-220">這個屬性的預設值為 0.95。</span><span class="sxs-lookup"><span data-stu-id="9bac9-220">The default value of this property is 0.95.</span></span> <span data-ttu-id="9bac9-221">只有當 [已指定]  選取成為 [InclusionThresholdSetting]  時，這個選項才會啟用。</span><span class="sxs-lookup"><span data-stu-id="9bac9-221">This option is enabled only when **Specified** is selected as the **InclusionThresholdSetting**.</span></span>  
  
 <span data-ttu-id="9bac9-222">如需詳細資訊，請參閱本主題前面的「了解臨界值設定」一節。</span><span class="sxs-lookup"><span data-stu-id="9bac9-222">For more information, see the section, "Understanding the Threshold Settings," earlier in this topic.</span></span>  
  
 <span data-ttu-id="9bac9-223">**SupersetColumnsKeyThresholdSetting**</span><span class="sxs-lookup"><span data-stu-id="9bac9-223">**SupersetColumnsKeyThresholdSetting**</span></span>  
 <span data-ttu-id="9bac9-224">指定超集臨界值。</span><span class="sxs-lookup"><span data-stu-id="9bac9-224">Specify the superset threshold.</span></span> <span data-ttu-id="9bac9-225">這個屬性的預設值為 [已指定]  。</span><span class="sxs-lookup"><span data-stu-id="9bac9-225">The default value of this property is **Specified**.</span></span> <span data-ttu-id="9bac9-226">如需詳細資訊，請參閱本主題前面的「了解臨界值設定」一節。</span><span class="sxs-lookup"><span data-stu-id="9bac9-226">For more information, see the section, "Understanding the Threshold Settings," earlier in this topic.</span></span>  
  
|<span data-ttu-id="9bac9-227">值</span><span class="sxs-lookup"><span data-stu-id="9bac9-227">Value</span></span>|<span data-ttu-id="9bac9-228">描述</span><span class="sxs-lookup"><span data-stu-id="9bac9-228">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="9bac9-229">**None**</span><span class="sxs-lookup"><span data-stu-id="9bac9-229">**None**</span></span>|<span data-ttu-id="9bac9-230">沒有指定臨界值。</span><span class="sxs-lookup"><span data-stu-id="9bac9-230">Does not specify a threshold.</span></span> <span data-ttu-id="9bac9-231">不論超集資料行的索引鍵強度為何，系統都會報告包含強度。</span><span class="sxs-lookup"><span data-stu-id="9bac9-231">The inclusion strength is reported regardless of the key strength of the superset column.</span></span>|  
|<span data-ttu-id="9bac9-232">**已指定**</span><span class="sxs-lookup"><span data-stu-id="9bac9-232">**Specified**</span></span>|<span data-ttu-id="9bac9-233">使用 **SupersetColumnsKeyThreshold**頁面上。</span><span class="sxs-lookup"><span data-stu-id="9bac9-233">Use the threshold that is specified in **SupersetColumnsKeyThreshold**.</span></span> <span data-ttu-id="9bac9-234">只有當超集資料行的索引鍵強度大於臨界值時，系統才會報告包含強度。</span><span class="sxs-lookup"><span data-stu-id="9bac9-234">The inclusion strength is reported only if the key strength of the superset column is greater than the threshold.</span></span>|  
|<span data-ttu-id="9bac9-235">**精確**</span><span class="sxs-lookup"><span data-stu-id="9bac9-235">**Exact**</span></span>|<span data-ttu-id="9bac9-236">沒有指定臨界值。</span><span class="sxs-lookup"><span data-stu-id="9bac9-236">Does not specify a threshold.</span></span> <span data-ttu-id="9bac9-237">只有當超集資料行是超集資料表中的精確索引鍵時，系統才會報告包含強度。</span><span class="sxs-lookup"><span data-stu-id="9bac9-237">The inclusion strength is reported only if the supserset columns are an exact key in the superset table.</span></span>|  
  
 <span data-ttu-id="9bac9-238">**SupersetColumnsKeyThreshold**</span><span class="sxs-lookup"><span data-stu-id="9bac9-238">**SupersetColumnsKeyThreshold**</span></span>  
 <span data-ttu-id="9bac9-239">指定臨界值 (使用介於 0 與 1 之間的值)，而且超過此值就應該報告包含強度。</span><span class="sxs-lookup"><span data-stu-id="9bac9-239">Specify the threshold (by using a value between 0 and 1) above which the inclusion strength should be reported.</span></span> <span data-ttu-id="9bac9-240">這個屬性的預設值為 0.95。</span><span class="sxs-lookup"><span data-stu-id="9bac9-240">The default value of this property is 0.95.</span></span> <span data-ttu-id="9bac9-241">只有當 [已指定]  選取成為 [SupersetColumnsKeyThresholdSetting]  時，這個選項才會啟用。</span><span class="sxs-lookup"><span data-stu-id="9bac9-241">This option is enabled only when **Specified** is selected as the **SupersetColumnsKeyThresholdSetting**.</span></span>  
  
 <span data-ttu-id="9bac9-242">如需詳細資訊，請參閱本主題前面的「了解臨界值設定」一節。</span><span class="sxs-lookup"><span data-stu-id="9bac9-242">For more information, see the section, "Understanding the Threshold Settings," earlier in this topic.</span></span>  
  
 <span data-ttu-id="9bac9-243">**MaxNumberOfViolations**</span><span class="sxs-lookup"><span data-stu-id="9bac9-243">**MaxNumberOfViolations**</span></span>  
 <span data-ttu-id="9bac9-244">指定可在輸出中報告的包含違規數目上限。</span><span class="sxs-lookup"><span data-stu-id="9bac9-244">Specify the maximum number of inclusion violations to report in the output.</span></span> <span data-ttu-id="9bac9-245">這個屬性的預設值為 100。</span><span class="sxs-lookup"><span data-stu-id="9bac9-245">The default value of this property is 100.</span></span> <span data-ttu-id="9bac9-246">當 [精確]  選取成為 [InclusionThresholdSetting]  時，這個選項會停用。</span><span class="sxs-lookup"><span data-stu-id="9bac9-246">This option is disabled when **Exact** is selected as the **InclusionThresholdSetting**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9bac9-247">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9bac9-247">See Also</span></span>  
 <span data-ttu-id="9bac9-248">[資料分析工作編輯器 &#40;一般頁面&#41;](../general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="9bac9-248">[Data Profiling Task Editor &#40;General Page&#41;](../general-page-of-integration-services-designers-options.md) </span></span>  
 [<span data-ttu-id="9bac9-249">單一資料表快速分析表單 &#40;資料分析工作&#41;</span><span class="sxs-lookup"><span data-stu-id="9bac9-249">Single Table Quick Profile Form &#40;Data Profiling Task&#41;</span></span>](single-table-quick-profile-form-data-profiling-task.md)  
  
  
