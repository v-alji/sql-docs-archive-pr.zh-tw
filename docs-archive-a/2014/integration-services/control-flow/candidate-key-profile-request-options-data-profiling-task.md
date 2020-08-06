---
title: 候選索引鍵設定檔要求選項 (資料分析工作) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Data Profiling Task Editor
ms.assetid: 8632dbc4-4394-4dc7-b19c-f9adeb21ba52
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 86d7135059a315ad6504beb8e7a9408ef20e4fcc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592805"
---
# <a name="candidate-key-profile-request-options-data-profiling-task"></a><span data-ttu-id="10a87-102">候選索引鍵設定檔要求選項 (資料分析工作)</span><span class="sxs-lookup"><span data-stu-id="10a87-102">Candidate Key Profile Request Options (Data Profiling Task)</span></span>
  <span data-ttu-id="10a87-103">您可以使用 [設定檔要求]  頁面的 [要求屬性]  窗格，針對要求窗格中選取的 [候選索引鍵設定檔要求]  設定選項。</span><span class="sxs-lookup"><span data-stu-id="10a87-103">Use the **Request Properties** pane of the **Profile Requests** page to set the options for the **Candidate Key Profile Request** that is selected in the requests pane.</span></span> <span data-ttu-id="10a87-104">候選索引鍵設定檔會報告資料行或資料行集合是否為選取之資料表的索引鍵或近似索引鍵。</span><span class="sxs-lookup"><span data-stu-id="10a87-104">A Candidate Key profile reports whether a column or set of columns is a key, or an approximate key, for the selected table.</span></span> <span data-ttu-id="10a87-105">這個設定檔也可協助您識別資料中的問題，例如潛在索引鍵資料行中重複的值。</span><span class="sxs-lookup"><span data-stu-id="10a87-105">This profile can also help you identify problems in your data such as duplicate values in a potential key column.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="10a87-106">本主題所描述的選項會顯示在 **[資料分析工作編輯器]** 的 **[設定檔要求]** 頁面上。</span><span class="sxs-lookup"><span data-stu-id="10a87-106">The options described in this topic appear on the **Profile Requests page** of the **Data Profiling Task Editor**.</span></span> <span data-ttu-id="10a87-107">如需此編輯器頁面的詳細資訊，請參閱[資料分析工作編輯器 &#40;設定檔要求頁面&#41;](data-profiling-task-editor-profile-requests-page.md)。</span><span class="sxs-lookup"><span data-stu-id="10a87-107">For more information about this page of the editor, see [Data Profiling Task Editor &#40;Profile Requests Page&#41;](data-profiling-task-editor-profile-requests-page.md).</span></span>  
  
 <span data-ttu-id="10a87-108">如需如何使用資料分析工作的詳細資訊，請參閱 [資料分析工作的設定](data-profiling-task.md)。</span><span class="sxs-lookup"><span data-stu-id="10a87-108">For more information about how to use the Data Profiling Task, see [Setup of the Data Profiling Task](data-profiling-task.md).</span></span> <span data-ttu-id="10a87-109">如需如何使用資料設定檔檢視器來分析資料分析工作輸出的詳細資訊，請參閱 [資料設定檔檢視器](data-profile-viewer.md)。</span><span class="sxs-lookup"><span data-stu-id="10a87-109">For more information about how to use the Data Profile Viewer to analyze the output of the Data Profiling Task, see [Data Profile Viewer](data-profile-viewer.md).</span></span>  
  
## <a name="understanding-the-selection-of-columns-for-the-keycolumns-property"></a><span data-ttu-id="10a87-110">了解 KeyColumns 屬性之資料行的選擇</span><span class="sxs-lookup"><span data-stu-id="10a87-110">Understanding the Selection of Columns for the KeyColumns Property</span></span>  
 <span data-ttu-id="10a87-111">每個 [候選索引鍵設定檔要求]  都會計算包含單一資料行或多個資料行之單一索引鍵候選的索引鍵強度：</span><span class="sxs-lookup"><span data-stu-id="10a87-111">Each **Candidate Key Profile Request** computes the key strength of a single key candidate that consists of a single column or of multiple columns:</span></span>  
  
-   <span data-ttu-id="10a87-112">當您在 [KeyColumns]  中僅選取一個資料行時，此工作會計算該單一資料行的索引鍵強度。</span><span class="sxs-lookup"><span data-stu-id="10a87-112">When you select only one column in **KeyColumns**, the task computes the key strength of that one column.</span></span>  
  
-   <span data-ttu-id="10a87-113">當您在 [KeyColumns]  中選取多個資料行時，此工作會計算包含所有選取資料行之複合索引鍵的索引鍵強度。</span><span class="sxs-lookup"><span data-stu-id="10a87-113">When you select multiple columns in **KeyColumns**, the task computes the key strength of the composite key that consists of all the selected columns.</span></span>  
  
-   <span data-ttu-id="10a87-114">當您在 [KeyColumns] 中選取 **(\*)** 萬用字元時，此工作會計算資料表或檢視表中每個資料行的索引鍵強度。</span><span class="sxs-lookup"><span data-stu-id="10a87-114">When you select the wildcard character, **(\*)**, in **KeyColumns**, the task computers the key strength of each column in the table or view.</span></span>  
  
 <span data-ttu-id="10a87-115">例如，假設有一個包含 A、B 和 C 資料行的範例資料表。您針對 [KeyColumns]  進行下列選擇：</span><span class="sxs-lookup"><span data-stu-id="10a87-115">For example, consider a sample table that contains columns A, B, and C. You make the following selections for **KeyColumns**:</span></span>  
  
-   <span data-ttu-id="10a87-116">您在 [KeyColumns] 中選取了 (\*) 和 C 資料行。</span><span class="sxs-lookup"><span data-stu-id="10a87-116">You select (\*) and column C in **KeyColumns**.</span></span> <span data-ttu-id="10a87-117">此工作會計算 C 資料行的索引鍵強度，然後計算複合索引鍵候選 (A, C) 和 (B, C) 的強度。</span><span class="sxs-lookup"><span data-stu-id="10a87-117">The task computes the key strength of column C, and then of composite key candidates (A, C) and (B, C).</span></span>  
  
-   <span data-ttu-id="10a87-118">您在 [KeyColumns] 中選取了 (\*) 和 (\*)。</span><span class="sxs-lookup"><span data-stu-id="10a87-118">You select (\*) and (\*) in **KeyColumns**.</span></span> <span data-ttu-id="10a87-119">此工作會計算 A、B 和 C 個別資料行的索引鍵強度，然後計算複合索引鍵候選 (A, B)、(A, C) 和 (B, C) 的強度。</span><span class="sxs-lookup"><span data-stu-id="10a87-119">The task computes the key strength of individual columns A, B, and C, and then of composite key candidates (A, B), (A, C) and (B, C).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="10a87-120">如果您選取 (\*)，這個選項可能會產生大量計算並降低工作的效能。</span><span class="sxs-lookup"><span data-stu-id="10a87-120">If you select (\*), this option might result in a large number of computations and decrease the performance of the task.</span></span> <span data-ttu-id="10a87-121">不過，如果此工作找到滿足索引鍵臨界值的子集，它就不會分析其他組合。</span><span class="sxs-lookup"><span data-stu-id="10a87-121">However, if the task finds a subset that satisfies the threshold for a key, the task does not analyze additional combinations.</span></span> <span data-ttu-id="10a87-122">例如，在上述範例資料表中，如果此工作決定 C 資料行是索引鍵，它就不會繼續分析複合索引鍵候選。</span><span class="sxs-lookup"><span data-stu-id="10a87-122">For example, in the sample table described above, if the task determines that column C is a key, the task does not continue to analyze the composite key candidates.</span></span>  
  
## <a name="request-properties-options"></a><span data-ttu-id="10a87-123">要求屬性選項</span><span class="sxs-lookup"><span data-stu-id="10a87-123">Request Properties Options</span></span>  
 <span data-ttu-id="10a87-124">[要求屬性]  窗格會針對 [候選索引鍵設定檔要求]  顯示下列選項群組：</span><span class="sxs-lookup"><span data-stu-id="10a87-124">For a **Candidate Key Profile Request**, the **Request Properties** pane displays the following groups of options:</span></span>  
  
-   <span data-ttu-id="10a87-125">[資料]  ，其中包括 [TableOrView]  和 [KeyColumns]  選項</span><span class="sxs-lookup"><span data-stu-id="10a87-125">**Data**, which includes the **TableOrView** and **KeyColumns** options</span></span>  
  
-   <span data-ttu-id="10a87-126">**一般**</span><span class="sxs-lookup"><span data-stu-id="10a87-126">**General**</span></span>  
  
-   <span data-ttu-id="10a87-127">**選項**</span><span class="sxs-lookup"><span data-stu-id="10a87-127">**Options**</span></span>  
  
### <a name="data-options"></a><span data-ttu-id="10a87-128">資料選項</span><span class="sxs-lookup"><span data-stu-id="10a87-128">Data Options</span></span>  
 <span data-ttu-id="10a87-129">**ConnectionManager**</span><span class="sxs-lookup"><span data-stu-id="10a87-129">**ConnectionManager**</span></span>  
 <span data-ttu-id="10a87-130">選取現有的 [!INCLUDE[vstecado](../../includes/vstecado-md.md)] 連線管理員，以便使用 .NET Data Provider for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (SqlClient) 來連線至包含要分析之資料表或檢視表的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫。</span><span class="sxs-lookup"><span data-stu-id="10a87-130">Select the existing [!INCLUDE[vstecado](../../includes/vstecado-md.md)] connection manager that uses the .NET Data Provider for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (SqlClient) to connect to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database that contains the table or view to be profiled.</span></span>  
  
 <span data-ttu-id="10a87-131">**[TableOrView]**</span><span class="sxs-lookup"><span data-stu-id="10a87-131">**TableOrView**</span></span>  
 <span data-ttu-id="10a87-132">選取要分析的現有資料表或檢視表。</span><span class="sxs-lookup"><span data-stu-id="10a87-132">Select the existing table or view to be profiled.</span></span>  
  
 <span data-ttu-id="10a87-133">如需詳細資訊，請參閱本主題中的「TableorView 選項」一節。</span><span class="sxs-lookup"><span data-stu-id="10a87-133">For more information, see the section, "TableorView Options," in this topic.</span></span>  
  
 <span data-ttu-id="10a87-134">**KeyColumns**</span><span class="sxs-lookup"><span data-stu-id="10a87-134">**KeyColumns**</span></span>  
 <span data-ttu-id="10a87-135">選取要分析的現有資料行。</span><span class="sxs-lookup"><span data-stu-id="10a87-135">Select the existing column or columns to be profiled.</span></span> <span data-ttu-id="10a87-136">您可以選取 **(\*)** 來分析所有資料行。</span><span class="sxs-lookup"><span data-stu-id="10a87-136">Select **(\*)** to profile all columns.</span></span>  
  
 <span data-ttu-id="10a87-137">如需詳細資訊，請參閱本主題的「了解 KeyColumns 屬性之資料行的選擇」和「KeyColumns 選項」章節。</span><span class="sxs-lookup"><span data-stu-id="10a87-137">For more information, see the sections, "Understanding the Selection of Columns for the KeyColumns Property" and "KeyColumns Options," in this topic.</span></span>  
  
#### <a name="tableorview-options"></a><span data-ttu-id="10a87-138">TableOrView 選項</span><span class="sxs-lookup"><span data-stu-id="10a87-138">TableOrView Options</span></span>  
 <span data-ttu-id="10a87-139">**結構描述**</span><span class="sxs-lookup"><span data-stu-id="10a87-139">**Schema**</span></span>  
 <span data-ttu-id="10a87-140">指定選取之資料表所屬的結構描述。</span><span class="sxs-lookup"><span data-stu-id="10a87-140">Specify the schema to which the selected table belongs.</span></span> <span data-ttu-id="10a87-141">此選項是唯讀的。</span><span class="sxs-lookup"><span data-stu-id="10a87-141">This option is read-only.</span></span>  
  
 <span data-ttu-id="10a87-142">**Table**</span><span class="sxs-lookup"><span data-stu-id="10a87-142">**Table**</span></span>  
 <span data-ttu-id="10a87-143">顯示選取之資料表的名稱。</span><span class="sxs-lookup"><span data-stu-id="10a87-143">Displays the name of the selected table.</span></span> <span data-ttu-id="10a87-144">此選項是唯讀的。</span><span class="sxs-lookup"><span data-stu-id="10a87-144">This option is read-only.</span></span>  
  
#### <a name="keycolumns-options"></a><span data-ttu-id="10a87-145">KeyColumns 選項</span><span class="sxs-lookup"><span data-stu-id="10a87-145">KeyColumns Options</span></span>  
 <span data-ttu-id="10a87-146">下列選項會呈現給在 [KeyColumns]  中選取待分析的每個資料行或 **(\*)** 選項。</span><span class="sxs-lookup"><span data-stu-id="10a87-146">The following options are presented for each column selected for profiling in **KeyColumns**, or for the **(\*)** option.</span></span>  
  
 <span data-ttu-id="10a87-147">如需詳細資訊，請參閱本主題前面的「了解 KeyColumns 屬性之資料行的選擇」章節。</span><span class="sxs-lookup"><span data-stu-id="10a87-147">For more information, see the section, "Understanding the Selection of Columns for the KeyColumns Property," earlier in this topic.</span></span>  
  
 <span data-ttu-id="10a87-148">**IsWildcard**</span><span class="sxs-lookup"><span data-stu-id="10a87-148">**IsWildcard**</span></span>  
 <span data-ttu-id="10a87-149">指定是否已經選取 **(\*)** 萬用字元。</span><span class="sxs-lookup"><span data-stu-id="10a87-149">Specifies whether the **(\*)** wildcard has been selected.</span></span> <span data-ttu-id="10a87-150">如果您已選取 **(\*)** 來分析所有資料行，這個選項會設定為 [True]。</span><span class="sxs-lookup"><span data-stu-id="10a87-150">This option is set to **True** if you have selected **(\*)** to profile all columns.</span></span> <span data-ttu-id="10a87-151">如果您已選取要分析的個別資料行，它就會設定為 **[False]** 。</span><span class="sxs-lookup"><span data-stu-id="10a87-151">It is **False** if you have selected an individual column to be profiled.</span></span> <span data-ttu-id="10a87-152">此選項是唯讀的。</span><span class="sxs-lookup"><span data-stu-id="10a87-152">This option is read-only.</span></span>  
  
 <span data-ttu-id="10a87-153">**ColumnName**</span><span class="sxs-lookup"><span data-stu-id="10a87-153">**ColumnName**</span></span>  
 <span data-ttu-id="10a87-154">顯示所選取資料行的名稱。</span><span class="sxs-lookup"><span data-stu-id="10a87-154">Displays the name of the selected column.</span></span> <span data-ttu-id="10a87-155">如果您已選取 **(\*)** 來分析所有資料行，這個選項就是空白的。</span><span class="sxs-lookup"><span data-stu-id="10a87-155">This option is blank if you have selected **(\*)** to profile all columns.</span></span> <span data-ttu-id="10a87-156">此選項是唯讀的。</span><span class="sxs-lookup"><span data-stu-id="10a87-156">This option is read-only.</span></span>  
  
 <span data-ttu-id="10a87-157">**StringCompareOptions**</span><span class="sxs-lookup"><span data-stu-id="10a87-157">**StringCompareOptions**</span></span>  
 <span data-ttu-id="10a87-158">選取比較字串值的選項。</span><span class="sxs-lookup"><span data-stu-id="10a87-158">Select options for comparing string values.</span></span> <span data-ttu-id="10a87-159">這個屬性具有下表中所列的選項。</span><span class="sxs-lookup"><span data-stu-id="10a87-159">This property has the options listed in the following table.</span></span> <span data-ttu-id="10a87-160">這個選項的預設值為 **預設值**頁面上。</span><span class="sxs-lookup"><span data-stu-id="10a87-160">The default value of this option is **Default**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="10a87-161">當您針對 [ColumnName] 使用 **(\*)** 萬用字元時，[CompareOptions] 就是唯讀的，而且它會設定為 [預設值] 設定。</span><span class="sxs-lookup"><span data-stu-id="10a87-161">When you use a **(\*)** wildcard for **ColumnName**, **CompareOptions** is read-only and is set to the **Default** setting.</span></span>  
  
|<span data-ttu-id="10a87-162">值</span><span class="sxs-lookup"><span data-stu-id="10a87-162">Value</span></span>|<span data-ttu-id="10a87-163">描述</span><span class="sxs-lookup"><span data-stu-id="10a87-163">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="10a87-164">**預設值**</span><span class="sxs-lookup"><span data-stu-id="10a87-164">**Default**</span></span>|<span data-ttu-id="10a87-165">根據來源資料表中的資料行定序來排序和比較資料。</span><span class="sxs-lookup"><span data-stu-id="10a87-165">Sorts and compares data based on the column's collation in the source table.</span></span>|  
|<span data-ttu-id="10a87-166">**BinarySort**</span><span class="sxs-lookup"><span data-stu-id="10a87-166">**BinarySort**</span></span>|<span data-ttu-id="10a87-167">根據針對每個字元所定義的位元模式來排序和比較資料。</span><span class="sxs-lookup"><span data-stu-id="10a87-167">Sorts and compares data based on the bit patterns defined for each character.</span></span> <span data-ttu-id="10a87-168">二進位排序順序為區分大小寫和區分腔調字。</span><span class="sxs-lookup"><span data-stu-id="10a87-168">Binary sort order is case sensitive and accent sensitive.</span></span> <span data-ttu-id="10a87-169">二進位也是最快的排序順序。</span><span class="sxs-lookup"><span data-stu-id="10a87-169">Binary is also the fastest sorting order.</span></span>|  
|<span data-ttu-id="10a87-170">**DictionarySort**</span><span class="sxs-lookup"><span data-stu-id="10a87-170">**DictionarySort**</span></span>|<span data-ttu-id="10a87-171">根據相關聯之語言或字母字典中所定義的排序和比較規則來排序和比較資料。</span><span class="sxs-lookup"><span data-stu-id="10a87-171">Sorts and compares data based on the sorting and comparison rules as defined in dictionaries for the associated language or alphabet.</span></span>|  
  
 <span data-ttu-id="10a87-172">如果您選取 [DictionarySort]  ，也可以選取下表中所列的任何選項組合。</span><span class="sxs-lookup"><span data-stu-id="10a87-172">If you select **DictionarySort**, you can also select any combination of the options listed in the following table.</span></span> <span data-ttu-id="10a87-173">根據預設，系統不會選取這些額外的選項。</span><span class="sxs-lookup"><span data-stu-id="10a87-173">By default, none of these additional options are selected.</span></span>  
  
|<span data-ttu-id="10a87-174">值</span><span class="sxs-lookup"><span data-stu-id="10a87-174">Value</span></span>|<span data-ttu-id="10a87-175">描述</span><span class="sxs-lookup"><span data-stu-id="10a87-175">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="10a87-176">**IgnoreCase**</span><span class="sxs-lookup"><span data-stu-id="10a87-176">**IgnoreCase**</span></span>|<span data-ttu-id="10a87-177">指定比較是否區分大寫與小寫字母。</span><span class="sxs-lookup"><span data-stu-id="10a87-177">Specifies whether the comparison distinguishes between uppercase and lowercase letters.</span></span> <span data-ttu-id="10a87-178">如果設定此選項，則字串比較會忽略大小寫。</span><span class="sxs-lookup"><span data-stu-id="10a87-178">If this option is set, the string comparison ignores case.</span></span> <span data-ttu-id="10a87-179">例如，「ABC」與「abc」視為一樣。</span><span class="sxs-lookup"><span data-stu-id="10a87-179">For example, "ABC" becomes the same as "abc".</span></span>|  
|<span data-ttu-id="10a87-180">**IgnoreNonSpace**</span><span class="sxs-lookup"><span data-stu-id="10a87-180">**IgnoreNonSpace**</span></span>|<span data-ttu-id="10a87-181">指定比較是否區分空格字元與變音。</span><span class="sxs-lookup"><span data-stu-id="10a87-181">Specifies whether the comparison distinguishes between spacing characters and diacritics.</span></span> <span data-ttu-id="10a87-182">如果設定此選項，則比較會忽略變音符號。</span><span class="sxs-lookup"><span data-stu-id="10a87-182">If this option is set, the comparison ignores diacritics.</span></span> <span data-ttu-id="10a87-183">例如，"å" 等於 "a"。</span><span class="sxs-lookup"><span data-stu-id="10a87-183">For example, "å" is equal to "a".</span></span>|  
|<span data-ttu-id="10a87-184">**IgnoreKanaType**</span><span class="sxs-lookup"><span data-stu-id="10a87-184">**IgnoreKanaType**</span></span>|<span data-ttu-id="10a87-185">指定比較是否區分兩類日文的假名字元：平假名與片假名。</span><span class="sxs-lookup"><span data-stu-id="10a87-185">Specifies whether the comparison distinguishes between the two types of Japanese kana characters: hiragana and katakana.</span></span> <span data-ttu-id="10a87-186">如果設定此選項，則字串比較會忽略假名類型。</span><span class="sxs-lookup"><span data-stu-id="10a87-186">If this option is set, the string comparison ignores kana type.</span></span>|  
|<span data-ttu-id="10a87-187">**IgnoreWidth**</span><span class="sxs-lookup"><span data-stu-id="10a87-187">**IgnoreWidth**</span></span>|<span data-ttu-id="10a87-188">指定比較是否區分單一位元組字元和表示為雙位元組字元的相同字元。</span><span class="sxs-lookup"><span data-stu-id="10a87-188">Specifies whether the comparison distinguishes between a single-byte character and the same character when it is represented as a double-byte character.</span></span> <span data-ttu-id="10a87-189">如果設定此選項，則字串比較會將同一字元的單一位元組表示法和雙位元組表示法視為一樣。</span><span class="sxs-lookup"><span data-stu-id="10a87-189">If this option is set, the string comparison treats single-byte and double-byte representations of the same character as identical.</span></span>|  
  
### <a name="general-options"></a><span data-ttu-id="10a87-190">一般選項</span><span class="sxs-lookup"><span data-stu-id="10a87-190">General Options</span></span>  
 <span data-ttu-id="10a87-191">**RequestID**</span><span class="sxs-lookup"><span data-stu-id="10a87-191">**RequestID**</span></span>  
 <span data-ttu-id="10a87-192">輸入描述性名稱，以便識別這個設定檔要求。</span><span class="sxs-lookup"><span data-stu-id="10a87-192">Type a descriptive name to identify this profile request.</span></span> <span data-ttu-id="10a87-193">一般而言，您不需要變更自動產生的值。</span><span class="sxs-lookup"><span data-stu-id="10a87-193">Typically, you do not have to change the autogenerated value.</span></span>  
  
### <a name="options"></a><span data-ttu-id="10a87-194">選項。</span><span class="sxs-lookup"><span data-stu-id="10a87-194">Options</span></span>  
 <span data-ttu-id="10a87-195">**ThresholdSetting**</span><span class="sxs-lookup"><span data-stu-id="10a87-195">**ThresholdSetting**</span></span>  
 <span data-ttu-id="10a87-196">這個屬性具有下表中所列的選項。</span><span class="sxs-lookup"><span data-stu-id="10a87-196">This property has the options listed in the following table.</span></span> <span data-ttu-id="10a87-197">這個屬性的預設值為 [已指定]  。</span><span class="sxs-lookup"><span data-stu-id="10a87-197">The default value of this property is **Specified**.</span></span>  
  
|<span data-ttu-id="10a87-198">值</span><span class="sxs-lookup"><span data-stu-id="10a87-198">Value</span></span>|<span data-ttu-id="10a87-199">描述</span><span class="sxs-lookup"><span data-stu-id="10a87-199">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="10a87-200">**None**</span><span class="sxs-lookup"><span data-stu-id="10a87-200">**None**</span></span>|<span data-ttu-id="10a87-201">沒有指定臨界值。</span><span class="sxs-lookup"><span data-stu-id="10a87-201">No threshold is specified.</span></span> <span data-ttu-id="10a87-202">不論索引鍵強度為何，系統都會報告此值。</span><span class="sxs-lookup"><span data-stu-id="10a87-202">The key strength is reported regardless of its value.</span></span>|  
|<span data-ttu-id="10a87-203">**已指定**</span><span class="sxs-lookup"><span data-stu-id="10a87-203">**Specified**</span></span>|<span data-ttu-id="10a87-204">臨界值是在 [KeyStrengthThreshold]  中指定的。</span><span class="sxs-lookup"><span data-stu-id="10a87-204">A threshold is specified in **KeyStrengthThreshold**.</span></span> <span data-ttu-id="10a87-205">只有當索引鍵強度大於臨界值時，系統才會報告此值。</span><span class="sxs-lookup"><span data-stu-id="10a87-205">The key strength is reported only if it is greater than the threshold.</span></span>|  
|<span data-ttu-id="10a87-206">**精確**</span><span class="sxs-lookup"><span data-stu-id="10a87-206">**Exact**</span></span>|<span data-ttu-id="10a87-207">沒有指定臨界值。</span><span class="sxs-lookup"><span data-stu-id="10a87-207">No threshold is specified.</span></span> <span data-ttu-id="10a87-208">只有當選取的資料行是精確索引鍵時，系統才會報告索引鍵強度。</span><span class="sxs-lookup"><span data-stu-id="10a87-208">The key strength is reported only if the selected columns are an exact key.</span></span>|  
  
 <span data-ttu-id="10a87-209">**KeyStrengthThreshold**</span><span class="sxs-lookup"><span data-stu-id="10a87-209">**KeyStrengthThreshold**</span></span>  
 <span data-ttu-id="10a87-210">指定臨界值 (使用介於 0 與 1 之間的值)，而且超過此值就應該報告索引鍵強度。</span><span class="sxs-lookup"><span data-stu-id="10a87-210">Specify the threshold (by using a value between 0 and 1) above which the key strength should be reported.</span></span> <span data-ttu-id="10a87-211">這個屬性的預設值為 0.95。</span><span class="sxs-lookup"><span data-stu-id="10a87-211">The default value of this property is 0.95.</span></span> <span data-ttu-id="10a87-212">只有當 [已指定]  選取成為 [KeyStrengthThresholdSetting]  時，這個選項才會啟用。</span><span class="sxs-lookup"><span data-stu-id="10a87-212">This option is enabled only when **Specified** is selected as the **KeyStrengthThresholdSetting**.</span></span>  
  
 <span data-ttu-id="10a87-213">**MaxNumberOfViolations**</span><span class="sxs-lookup"><span data-stu-id="10a87-213">**MaxNumberOfViolations**</span></span>  
 <span data-ttu-id="10a87-214">指定可在輸出中報告的候選索引鍵違規數目上限。</span><span class="sxs-lookup"><span data-stu-id="10a87-214">Specify the maximum number of candidate key violations to report in the output.</span></span> <span data-ttu-id="10a87-215">這個屬性的預設值為 100。</span><span class="sxs-lookup"><span data-stu-id="10a87-215">The default value of this property is 100.</span></span> <span data-ttu-id="10a87-216">當 [精確]  選取成為 [KeyStrengthThresholdSetting]  時，這個選項會停用。</span><span class="sxs-lookup"><span data-stu-id="10a87-216">This option is disabled when **Exact** is selected as the **KeyStrengthThresholdSetting**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10a87-217">另請參閱</span><span class="sxs-lookup"><span data-stu-id="10a87-217">See Also</span></span>  
 <span data-ttu-id="10a87-218">[資料分析工作編輯器 &#40;一般頁面&#41;](../general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="10a87-218">[Data Profiling Task Editor &#40;General Page&#41;](../general-page-of-integration-services-designers-options.md) </span></span>  
 [<span data-ttu-id="10a87-219">單一資料表快速分析表單 &#40;資料分析工作&#41;</span><span class="sxs-lookup"><span data-stu-id="10a87-219">Single Table Quick Profile Form &#40;Data Profiling Task&#41;</span></span>](single-table-quick-profile-form-data-profiling-task.md)  
  
  
