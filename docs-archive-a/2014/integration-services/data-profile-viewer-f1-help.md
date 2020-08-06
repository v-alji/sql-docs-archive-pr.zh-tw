---
title: 資料設定檔檢視器 F1 說明 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.dataprofileviewer.f1
helpviewer_keywords:
- Data Profile Viewer [Integration Services]
- Data Profiling task [Integration Services], viewer
ms.assetid: 3469c60a-8f4f-46ba-999a-cb9070197fea
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7003e1299938bd53a6d16a5597d4566ba5c46579
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592777"
---
# <a name="data-profile-viewer-f1-help"></a><span data-ttu-id="aa1de-102">資料設定檔檢視器 F1 說明</span><span class="sxs-lookup"><span data-stu-id="aa1de-102">Data Profile Viewer F1 Help</span></span>
  <span data-ttu-id="aa1de-103">您可以使用資料設定檔檢視器來檢視資料分析工作的輸出。</span><span class="sxs-lookup"><span data-stu-id="aa1de-103">Use the Data Profile Viewer to view the output of the Data Profiling task.</span></span>  
  
 <span data-ttu-id="aa1de-104">如需如何使用資料設定檔檢視器的詳細資訊，請參閱 [資料設定檔檢視器](control-flow/data-profile-viewer.md)。</span><span class="sxs-lookup"><span data-stu-id="aa1de-104">For more information about how to use the Data Profile Viewer, see [Data Profile Viewer](control-flow/data-profile-viewer.md).</span></span> <span data-ttu-id="aa1de-105">如需如何使用資料分析工作 (建立您在資料設定檔檢視器中分析的設定檔輸出) 的詳細資訊，請參閱 [資料分析工作的設定](control-flow/data-profiling-task.md)。</span><span class="sxs-lookup"><span data-stu-id="aa1de-105">For more information about how to use the Data Profiling task, which creates the profile output that you analyze in the Data Profile Viewer, see [Setup of the Data Profiling Task](control-flow/data-profiling-task.md).</span></span>  
  
## <a name="static-options"></a><span data-ttu-id="aa1de-106">靜態選項</span><span class="sxs-lookup"><span data-stu-id="aa1de-106">Static Options</span></span>  
 <span data-ttu-id="aa1de-107">**開啟**</span><span class="sxs-lookup"><span data-stu-id="aa1de-107">**Open**</span></span>  
 <span data-ttu-id="aa1de-108">按一下即可瀏覽包含資料分析工作之輸出的已儲存檔案。</span><span class="sxs-lookup"><span data-stu-id="aa1de-108">Click to browse for the saved file that contains the output of the Data Profiling task.</span></span>  
  
 <span data-ttu-id="aa1de-109">**設定檔** 窗格</span><span class="sxs-lookup"><span data-stu-id="aa1de-109">**Profiles** pane</span></span>  
 <span data-ttu-id="aa1de-110">展開 [設定檔]  窗格中的樹狀結構，即可查看輸出中所包含的設定檔。</span><span class="sxs-lookup"><span data-stu-id="aa1de-110">Expand the tree in the **Profiles** pane to see the profiles that are included in the output.</span></span> <span data-ttu-id="aa1de-111">選取設定檔，即可檢視該設定檔的結果。</span><span class="sxs-lookup"><span data-stu-id="aa1de-111">Select a profile to view the results for that profile.</span></span>  
  
 <span data-ttu-id="aa1de-112">**訊息** 窗格</span><span class="sxs-lookup"><span data-stu-id="aa1de-112">**Message** pane</span></span>  
 <span data-ttu-id="aa1de-113">顯示狀態訊息。</span><span class="sxs-lookup"><span data-stu-id="aa1de-113">Displays status messages.</span></span>  
  
 <span data-ttu-id="aa1de-114">**向下鑽研** 窗格</span><span class="sxs-lookup"><span data-stu-id="aa1de-114">**Drilldown** pane</span></span>  
 <span data-ttu-id="aa1de-115">顯示符合輸出中某個值的資料列 (如果資料分析工作所使用的資料來源可用的話)。</span><span class="sxs-lookup"><span data-stu-id="aa1de-115">Displays the rows of data that match a value in the output, if the data source that is used by the Data Profiling task is available.</span></span>  
  
 <span data-ttu-id="aa1de-116">例如，如果您要針對「美國州名」資料行檢視資料行值散發設定檔的輸出， **[詳細值散發]** 窗格可能會包含 "WA" 的資料列。</span><span class="sxs-lookup"><span data-stu-id="aa1de-116">For example, if you are viewing the output of a Column Value Distribution profile for a US State column, the **Detailed Value Distribution** pane might contain a row for "WA".</span></span> <span data-ttu-id="aa1de-117">在 [詳細值散發]  窗格中按兩下該資料列，即可利用 [向下鑽研] 窗格查看 [州] 資料行值為 "WA" 的資料列。</span><span class="sxs-lookup"><span data-stu-id="aa1de-117">Double-click the row in the **Detailed Value Distribution** pane to see the rows of data where the value of the state column is "WA" in the drilldown pane.</span></span>  
  
## <a name="dynamic-options"></a><span data-ttu-id="aa1de-118">動態選項</span><span class="sxs-lookup"><span data-stu-id="aa1de-118">Dynamic Options</span></span>  
  
### <a name="profile-type--column-length-distribution-profile"></a><span data-ttu-id="aa1de-119">設定檔類型 = 資料行長度散發設定檔</span><span class="sxs-lookup"><span data-stu-id="aa1de-119">Profile Type = Column Length Distribution Profile</span></span>  
  
#### <a name="column-length-distribution-profile---column-pane"></a><span data-ttu-id="aa1de-120">資料行長度散發設定檔 - \<column> 窗格</span><span class="sxs-lookup"><span data-stu-id="aa1de-120">Column Length Distribution Profile - \<column> pane</span></span>  
 <span data-ttu-id="aa1de-121">**最小長度**</span><span class="sxs-lookup"><span data-stu-id="aa1de-121">**Minimum Length**</span></span>  
 <span data-ttu-id="aa1de-122">顯示這個資料行中值的最小長度。</span><span class="sxs-lookup"><span data-stu-id="aa1de-122">Displays the minimum length of values in this column.</span></span>  
  
 <span data-ttu-id="aa1de-123">**最大長度**</span><span class="sxs-lookup"><span data-stu-id="aa1de-123">**Maximum Length**</span></span>  
 <span data-ttu-id="aa1de-124">顯示這個資料行中值的最大長度。</span><span class="sxs-lookup"><span data-stu-id="aa1de-124">Displays the maximum length of values in this column.</span></span>  
  
 <span data-ttu-id="aa1de-125">**忽略開頭空白**</span><span class="sxs-lookup"><span data-stu-id="aa1de-125">**Ignore Leading Spaces**</span></span>  
 <span data-ttu-id="aa1de-126">顯示這個設定檔會以 `IgnoreLeadingSpaces` 值為 True 或 False 的情況進行計算。</span><span class="sxs-lookup"><span data-stu-id="aa1de-126">Displays whether this profile was computed with an `IgnoreLeadingSpaces` value of True or False.</span></span> <span data-ttu-id="aa1de-127">這個屬性是在 [資料分析工作編輯器] 的 **[設定檔要求]** 頁面上設定的。</span><span class="sxs-lookup"><span data-stu-id="aa1de-127">This property was set on the **Profile Requests** page of the Data Profiling Task Editor.</span></span>  
  
 <span data-ttu-id="aa1de-128">**忽略尾端空白**</span><span class="sxs-lookup"><span data-stu-id="aa1de-128">**Ignore Trailing Spaces**</span></span>  
 <span data-ttu-id="aa1de-129">顯示這個設定檔會以 `IgnoreTrailingSpaces` 值為 True 或 False 的情況進行計算。</span><span class="sxs-lookup"><span data-stu-id="aa1de-129">Displays whether this profile was computed with an `IgnoreTrailingSpaces` value of True or False.</span></span> <span data-ttu-id="aa1de-130">這個屬性是在 [資料分析工作編輯器] 的 **[設定檔要求]** 頁面上設定的。</span><span class="sxs-lookup"><span data-stu-id="aa1de-130">This property was set on the **Profile Requests** page of the Data Profiling Task Editor.</span></span>  
  
 <span data-ttu-id="aa1de-131">**資料列計數**</span><span class="sxs-lookup"><span data-stu-id="aa1de-131">**Row Count**</span></span>  
 <span data-ttu-id="aa1de-132">顯示資料表或檢視表中的資料列數目。</span><span class="sxs-lookup"><span data-stu-id="aa1de-132">Displays the number of rows in the table or view.</span></span>  
  
#### <a name="detailed-length-distribution-pane"></a><span data-ttu-id="aa1de-133">詳細長度散發窗格</span><span class="sxs-lookup"><span data-stu-id="aa1de-133">Detailed Length Distribution pane</span></span>  
 <span data-ttu-id="aa1de-134">**長度**</span><span class="sxs-lookup"><span data-stu-id="aa1de-134">**Length**</span></span>  
 <span data-ttu-id="aa1de-135">顯示在已分析資料行中找到的資料行長度。</span><span class="sxs-lookup"><span data-stu-id="aa1de-135">Displays the column lengths found in the profiled column.</span></span>  
  
 <span data-ttu-id="aa1de-136">**Count**</span><span class="sxs-lookup"><span data-stu-id="aa1de-136">**Count**</span></span>  
 <span data-ttu-id="aa1de-137">顯示已分析資料行的值具有 [長度]  資料行中所顯示之長度的資料列數目。</span><span class="sxs-lookup"><span data-stu-id="aa1de-137">Displays the number of rows in which the value of the profiled column has the length shown in the **Length** column.</span></span>  
  
 <span data-ttu-id="aa1de-138">**百分比**</span><span class="sxs-lookup"><span data-stu-id="aa1de-138">**Percentage**</span></span>  
 <span data-ttu-id="aa1de-139">顯示已分析資料行的值具有 [長度]  資料行中所顯示之長度的資料列百分比。</span><span class="sxs-lookup"><span data-stu-id="aa1de-139">Displays the percentage of rows in which the value of the profiled column has the length shown in the **Length** column.</span></span>  
  
### <a name="profile-type--column-null-ratio-profile"></a><span data-ttu-id="aa1de-140">設定檔類型 = 資料行 Null 比例設定檔</span><span class="sxs-lookup"><span data-stu-id="aa1de-140">Profile Type = Column Null Ratio Profile</span></span>  
  
#### <a name="column-null-ratio-profile---column-pane"></a><span data-ttu-id="aa1de-141">資料行 Null 比例設定檔 - \<column> 窗格</span><span class="sxs-lookup"><span data-stu-id="aa1de-141">Column Null Ratio Profile - \<column> pane</span></span>  
 <span data-ttu-id="aa1de-142">**Null 計數**</span><span class="sxs-lookup"><span data-stu-id="aa1de-142">**Null Count**</span></span>  
 <span data-ttu-id="aa1de-143">顯示已分析資料行具有 Null 值的資料列數目。</span><span class="sxs-lookup"><span data-stu-id="aa1de-143">Displays the number of rows in which the profiled column has a null value.</span></span>  
  
 <span data-ttu-id="aa1de-144">**Null 百分比**</span><span class="sxs-lookup"><span data-stu-id="aa1de-144">**Null Percentage**</span></span>  
 <span data-ttu-id="aa1de-145">顯示已分析資料行具有 Null 值的資料列百分比。</span><span class="sxs-lookup"><span data-stu-id="aa1de-145">Displays the percentage of rows in which the profiled column has a null value.</span></span>  
  
 <span data-ttu-id="aa1de-146">**資料列計數**</span><span class="sxs-lookup"><span data-stu-id="aa1de-146">**Row Count**</span></span>  
 <span data-ttu-id="aa1de-147">顯示資料表或檢視表中的資料列數目。</span><span class="sxs-lookup"><span data-stu-id="aa1de-147">Displays the number of rows in the table or view.</span></span>  
  
### <a name="profile-type--column-pattern-profile"></a><span data-ttu-id="aa1de-148">設定檔類型 = 資料行模式設定檔</span><span class="sxs-lookup"><span data-stu-id="aa1de-148">Profile Type = Column Pattern Profile</span></span>  
  
#### <a name="column-pattern-profile---column-pane"></a><span data-ttu-id="aa1de-149">資料行模式設定檔 - \<column> 窗格</span><span class="sxs-lookup"><span data-stu-id="aa1de-149">Column Pattern Profile - \<column> pane</span></span>  
 <span data-ttu-id="aa1de-150">**資料列計數**</span><span class="sxs-lookup"><span data-stu-id="aa1de-150">**Row Count**</span></span>  
 <span data-ttu-id="aa1de-151">顯示資料表或檢視表中的資料列數目。</span><span class="sxs-lookup"><span data-stu-id="aa1de-151">Displays the number of rows in the table or view.</span></span>  
  
#### <a name="pattern-distribution-pane"></a><span data-ttu-id="aa1de-152">模式散發窗格</span><span class="sxs-lookup"><span data-stu-id="aa1de-152">Pattern Distribution pane</span></span>  
 <span data-ttu-id="aa1de-153">**模式**</span><span class="sxs-lookup"><span data-stu-id="aa1de-153">**Pattern**</span></span>  
 <span data-ttu-id="aa1de-154">顯示針對已分析資料行所計算的模式。</span><span class="sxs-lookup"><span data-stu-id="aa1de-154">Displays the patterns computed for the profiled column.</span></span>  
  
 <span data-ttu-id="aa1de-155">**百分比**</span><span class="sxs-lookup"><span data-stu-id="aa1de-155">**Percentage**</span></span>  
 <span data-ttu-id="aa1de-156">顯示值符合 [模式]  資料行中所顯示之模式的資料列百分比。</span><span class="sxs-lookup"><span data-stu-id="aa1de-156">Displays the percentage of rows whose values match the pattern displayed in the **Pattern** column.</span></span>  
  
### <a name="profile-type--column-statistics-profile"></a><span data-ttu-id="aa1de-157">設定檔類型 = 資料行統計資料設定檔</span><span class="sxs-lookup"><span data-stu-id="aa1de-157">Profile Type = Column Statistics Profile</span></span>  
  
#### <a name="column-statistics-profile---column-pane"></a><span data-ttu-id="aa1de-158">資料行統計資料設定檔 - \<column> 窗格</span><span class="sxs-lookup"><span data-stu-id="aa1de-158">Column Statistics Profile - \<column> pane</span></span>  
 <span data-ttu-id="aa1de-159">**最低**</span><span class="sxs-lookup"><span data-stu-id="aa1de-159">**Minimum**</span></span>  
 <span data-ttu-id="aa1de-160">顯示在已分析資料行中找到的最小值。</span><span class="sxs-lookup"><span data-stu-id="aa1de-160">Displays the minimum value found in the profiled column.</span></span>  
  
 <span data-ttu-id="aa1de-161">**最大值**</span><span class="sxs-lookup"><span data-stu-id="aa1de-161">**Maximum**</span></span>  
 <span data-ttu-id="aa1de-162">顯示在已分析資料行中找到的最大值。</span><span class="sxs-lookup"><span data-stu-id="aa1de-162">Displays the maximum value found in the profiled column.</span></span>  
  
 <span data-ttu-id="aa1de-163">**平均數**</span><span class="sxs-lookup"><span data-stu-id="aa1de-163">**Mean**</span></span>  
 <span data-ttu-id="aa1de-164">顯示在已分析資料行中找到之值的平均數。</span><span class="sxs-lookup"><span data-stu-id="aa1de-164">Displays the mean of the values found in the profiled column.</span></span>  
  
 <span data-ttu-id="aa1de-165">**標準差**</span><span class="sxs-lookup"><span data-stu-id="aa1de-165">**Standard Deviation**</span></span>  
 <span data-ttu-id="aa1de-166">顯示在已分析資料行中找到之值的標準差。</span><span class="sxs-lookup"><span data-stu-id="aa1de-166">Displays the standard deviation of the values found in the profiled column.</span></span>  
  
### <a name="profile-type--column-value-distribution-profile"></a><span data-ttu-id="aa1de-167">設定檔類型 = 資料行值散發設定檔</span><span class="sxs-lookup"><span data-stu-id="aa1de-167">Profile Type = Column Value Distribution Profile</span></span>  
  
#### <a name="column-value-distribution-profile---column-pane"></a><span data-ttu-id="aa1de-168">資料行值散發設定檔 - \<column> 窗格</span><span class="sxs-lookup"><span data-stu-id="aa1de-168">Column Value Distribution Profile - \<column> pane</span></span>  
 <span data-ttu-id="aa1de-169">**相異值的數目**</span><span class="sxs-lookup"><span data-stu-id="aa1de-169">**Number of Distinct Values**</span></span>  
 <span data-ttu-id="aa1de-170">顯示在已分析資料行中找到之相異值的計數。</span><span class="sxs-lookup"><span data-stu-id="aa1de-170">Displays the count of distinct values found in the profiled column.</span></span>  
  
 <span data-ttu-id="aa1de-171">**資料列計數**</span><span class="sxs-lookup"><span data-stu-id="aa1de-171">**Row Count**</span></span>  
 <span data-ttu-id="aa1de-172">顯示資料表或檢視表中的資料列數目。</span><span class="sxs-lookup"><span data-stu-id="aa1de-172">Displays the number of rows in the table or view.</span></span>  
  
#### <a name="detailed-value-distribution-pane"></a><span data-ttu-id="aa1de-173">詳細值散發窗格</span><span class="sxs-lookup"><span data-stu-id="aa1de-173">Detailed Value Distribution pane</span></span>  
 <span data-ttu-id="aa1de-174">**ReplTest1**</span><span class="sxs-lookup"><span data-stu-id="aa1de-174">**Value**</span></span>  
 <span data-ttu-id="aa1de-175">顯示在已分析資料行中找到的相異值。</span><span class="sxs-lookup"><span data-stu-id="aa1de-175">Displays the distinct values found in the profiled column.</span></span>  
  
 <span data-ttu-id="aa1de-176">**Count**</span><span class="sxs-lookup"><span data-stu-id="aa1de-176">**Count**</span></span>  
 <span data-ttu-id="aa1de-177">顯示已分析資料行具有 [值]  資料行中所顯示之值的資料列數目。</span><span class="sxs-lookup"><span data-stu-id="aa1de-177">Displays the number of rows in which the profiled column has the value shown in the **Value** column.</span></span>  
  
 <span data-ttu-id="aa1de-178">**百分比**</span><span class="sxs-lookup"><span data-stu-id="aa1de-178">**Percentage**</span></span>  
 <span data-ttu-id="aa1de-179">顯示已分析資料行具有 [值]  資料行中所顯示之值的資料列百分比。</span><span class="sxs-lookup"><span data-stu-id="aa1de-179">Displays the percentage of rows in which the profiled column has the value shown in the **Value** column.</span></span>  
  
### <a name="profile-type--candidate-key-profile"></a><span data-ttu-id="aa1de-180">設定檔類型 = 候選索引鍵設定檔</span><span class="sxs-lookup"><span data-stu-id="aa1de-180">Profile Type = Candidate Key Profile</span></span>  
  
#### <a name="candidate-key-profile---table-pane"></a><span data-ttu-id="aa1de-181">候選索引鍵設定檔 - \<table> 窗格</span><span class="sxs-lookup"><span data-stu-id="aa1de-181">Candidate Key Profile - \<table> pane</span></span>  
 <span data-ttu-id="aa1de-182">**索引鍵資料行**</span><span class="sxs-lookup"><span data-stu-id="aa1de-182">**Key Columns**</span></span>  
 <span data-ttu-id="aa1de-183">顯示針對分析成候選索引鍵所選取的資料行。</span><span class="sxs-lookup"><span data-stu-id="aa1de-183">Displays the columns that were selected for profiling as a candidate key.</span></span>  
  
 <span data-ttu-id="aa1de-184">**索引鍵強度**</span><span class="sxs-lookup"><span data-stu-id="aa1de-184">**Key Strength**</span></span>  
 <span data-ttu-id="aa1de-185">顯示候選索引鍵資料行或資料行組合的強度 (以百分比為單位)。</span><span class="sxs-lookup"><span data-stu-id="aa1de-185">Displays the strength (as a percentage) of the candidate key column or combination of columns.</span></span> <span data-ttu-id="aa1de-186">小於 100% 的索引鍵強度表示存在重複的值。</span><span class="sxs-lookup"><span data-stu-id="aa1de-186">A key strength of less than 100% indicates that duplicate values exist.</span></span>  
  
#### <a name="key-violations-pane"></a><span data-ttu-id="aa1de-187">索引鍵違規窗格</span><span class="sxs-lookup"><span data-stu-id="aa1de-187">Key Violations pane</span></span>  
 <span data-ttu-id="aa1de-188">**\<column1>、\<column2> 等。**</span><span class="sxs-lookup"><span data-stu-id="aa1de-188">**\<column1>, \<column2>, etc.**</span></span>  
 <span data-ttu-id="aa1de-189">顯示在已分析資料行中找到的重複值。</span><span class="sxs-lookup"><span data-stu-id="aa1de-189">Displays the duplicate values that were found in the profiled column.</span></span>  
  
 <span data-ttu-id="aa1de-190">**Count**</span><span class="sxs-lookup"><span data-stu-id="aa1de-190">**Count**</span></span>  
 <span data-ttu-id="aa1de-191">顯示指定之資料行具有第一個資料行中所顯示之值的資料列數目。</span><span class="sxs-lookup"><span data-stu-id="aa1de-191">Displays the number of rows in which the specified column has the value shown in the first column.</span></span>  
  
### <a name="profile-type--functional-dependency-profile"></a><span data-ttu-id="aa1de-192">設定檔類型 = 功能相依性設定檔</span><span class="sxs-lookup"><span data-stu-id="aa1de-192">Profile Type = Functional Dependency Profile</span></span>  
  
#### <a name="functional-dependency-profile-pane"></a><span data-ttu-id="aa1de-193">功能相依性設定檔窗格</span><span class="sxs-lookup"><span data-stu-id="aa1de-193">Functional Dependency Profile pane</span></span>  
 <span data-ttu-id="aa1de-194">**[行列式資料行]**</span><span class="sxs-lookup"><span data-stu-id="aa1de-194">**Determinant Columns**</span></span>  
 <span data-ttu-id="aa1de-195">顯示選取成為行列式資料行的資料行。</span><span class="sxs-lookup"><span data-stu-id="aa1de-195">Displays the column or columns selected as the determinant column.</span></span> <span data-ttu-id="aa1de-196">在相同美國郵遞區號應該永遠具有相同州名的範例中，郵遞區號就是行列式資料行。</span><span class="sxs-lookup"><span data-stu-id="aa1de-196">In the example where the same United States Zip Code should always have the same state, the Zip Code is the determinant column.</span></span>  
  
 <span data-ttu-id="aa1de-197">**相依資料行**</span><span class="sxs-lookup"><span data-stu-id="aa1de-197">**Dependent Columns**</span></span>  
 <span data-ttu-id="aa1de-198">顯示選取成為相依資料行的資料行。</span><span class="sxs-lookup"><span data-stu-id="aa1de-198">Displays the column or columns selected as the dependent column.</span></span> <span data-ttu-id="aa1de-199">在相同美國郵遞區號應該永遠具有相同州名的範例中，州名就是相依資料行。</span><span class="sxs-lookup"><span data-stu-id="aa1de-199">In the example where the same United States Zip Code should always have the same state, the state is the dependent column.</span></span>  
  
 <span data-ttu-id="aa1de-200">**功能相依性強度**</span><span class="sxs-lookup"><span data-stu-id="aa1de-200">**Functional Dependency Strength**</span></span>  
 <span data-ttu-id="aa1de-201">顯示資料行之間功能相依性的強度 (以百分比為單位)。</span><span class="sxs-lookup"><span data-stu-id="aa1de-201">Displays the strength (as a percentage) of the functional dependency between columns.</span></span> <span data-ttu-id="aa1de-202">小於 100% 的索引鍵強度表示發生了行列式值無法決定相依值的情況。</span><span class="sxs-lookup"><span data-stu-id="aa1de-202">A key strength of less than 100% indicates that there are cases where the determinant value does not determine the dependent value.</span></span> <span data-ttu-id="aa1de-203">在相同美國郵遞區號應該永遠具有相同州名的範例中，這可能表示某些州名的值無效。</span><span class="sxs-lookup"><span data-stu-id="aa1de-203">In the example where the same United States Zip Code should always have the same state, this probably indicates some state values are not valid.</span></span>  
  
#### <a name="functional-dependency-violations-pane"></a><span data-ttu-id="aa1de-204">功能相依性違規窗格</span><span class="sxs-lookup"><span data-stu-id="aa1de-204">Functional Dependency Violations pane</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="aa1de-205">如果資料中錯誤值的百分比很高，可能會導致功能相依性設定檔產生非預期的結果。</span><span class="sxs-lookup"><span data-stu-id="aa1de-205">A high percentage of erroneous values in the data could lead to unexpected results from a Functional Dependency profile.</span></span> <span data-ttu-id="aa1de-206">例如，在 90% 的資料列中，州值 "WI" 代表郵遞區號值 "98052"。</span><span class="sxs-lookup"><span data-stu-id="aa1de-206">For example, 90% of the rows have a State value of "WI" for a Postal Code value of "98052."</span></span> <span data-ttu-id="aa1de-207">此設定檔會將包含正確州值 "WA" 的資料列回報成違規。</span><span class="sxs-lookup"><span data-stu-id="aa1de-207">The profile reports rows that contain the correct state value of "WA" as violations.</span></span>  
  
 **\<determinant column name>**  
 <span data-ttu-id="aa1de-208">顯示這個功能相依性違規的執行個體中行列式資料行或資料行組合的值。</span><span class="sxs-lookup"><span data-stu-id="aa1de-208">Displays the value of the determinant column or combination of columns in this instance of a functional dependency violation.</span></span>  
  
 **\<dependent column name>**  
 <span data-ttu-id="aa1de-209">顯示這個功能相依性違規的執行個體中相依資料行的值。</span><span class="sxs-lookup"><span data-stu-id="aa1de-209">Displays the value of the dependent column in this instance of a functional dependency violation.</span></span>  
  
 <span data-ttu-id="aa1de-210">**支持度計數**</span><span class="sxs-lookup"><span data-stu-id="aa1de-210">**Support Count**</span></span>  
 <span data-ttu-id="aa1de-211">顯示行列式資料行值會決定相依資料行的資料列數目。</span><span class="sxs-lookup"><span data-stu-id="aa1de-211">Displays the number of rows in which the determinant column value determines the dependent column.</span></span>  
  
 <span data-ttu-id="aa1de-212">**違規計數**</span><span class="sxs-lookup"><span data-stu-id="aa1de-212">**Violation Count**</span></span>  
 <span data-ttu-id="aa1de-213">顯示行列式資料行值無法決定相依資料行的資料列數目</span><span class="sxs-lookup"><span data-stu-id="aa1de-213">Displays the number of rows in which the determinant column value does not determine the dependent column.</span></span> <span data-ttu-id="aa1de-214">(這些是相依值為 **\<dependent column name>** 資料行中顯示值的資料列。)</span><span class="sxs-lookup"><span data-stu-id="aa1de-214">(These are the rows where the dependent value is the value shown in the **\<dependent column name>** column.)</span></span>  
  
 <span data-ttu-id="aa1de-215">**支持度百分比**</span><span class="sxs-lookup"><span data-stu-id="aa1de-215">**Support Percentage**</span></span>  
 <span data-ttu-id="aa1de-216">顯示行列式資料行會決定相依資料行的資料列百分比。</span><span class="sxs-lookup"><span data-stu-id="aa1de-216">Displays the percentage of rows in which the determinant column determines the dependent column.</span></span>  
  
### <a name="profile-type--value-inclusion-profile"></a><span data-ttu-id="aa1de-217">設定檔類型 = 值包含設定檔</span><span class="sxs-lookup"><span data-stu-id="aa1de-217">Profile Type = Value Inclusion Profile</span></span>  
  
#### <a name="value-inclusion-profile-pane"></a><span data-ttu-id="aa1de-218">值包含設定檔窗格</span><span class="sxs-lookup"><span data-stu-id="aa1de-218">Value Inclusion Profile pane</span></span>  
 <span data-ttu-id="aa1de-219">**[子集資料行]**</span><span class="sxs-lookup"><span data-stu-id="aa1de-219">**Subset Side Columns**</span></span>  
 <span data-ttu-id="aa1de-220">顯示經過分析以便判斷是否位於超集資料行中的資料行或資料行組合。</span><span class="sxs-lookup"><span data-stu-id="aa1de-220">Displays the column or combination of columns that were profiled to determine whether they are in the superset columns.</span></span>  
  
 <span data-ttu-id="aa1de-221">**[超集資料行]**</span><span class="sxs-lookup"><span data-stu-id="aa1de-221">**Superset Side Columns**</span></span>  
 <span data-ttu-id="aa1de-222">顯示經過分析以便判斷是否包含子集資料行中之值的資料行或資料行組合。</span><span class="sxs-lookup"><span data-stu-id="aa1de-222">Displays the column or combination of columns that were profiled to determine whether they include the values in the subset columns.</span></span>  
  
 <span data-ttu-id="aa1de-223">**包含強度**</span><span class="sxs-lookup"><span data-stu-id="aa1de-223">**Inclusion Strength**</span></span>  
 <span data-ttu-id="aa1de-224">顯示資料行之間重疊的強度 (以百分比為單位)。</span><span class="sxs-lookup"><span data-stu-id="aa1de-224">Displays the strength (as a percentage) of the overlap between columns.</span></span> <span data-ttu-id="aa1de-225">小於 100% 的索引鍵強度表示發生了在超集值中找不到子集值的情況。</span><span class="sxs-lookup"><span data-stu-id="aa1de-225">A key strength of less than 100% indicates that there are cases where the subset value is not found among the superset values.</span></span>  
  
#### <a name="inclusion-violations-pane"></a><span data-ttu-id="aa1de-226">包含違規窗格</span><span class="sxs-lookup"><span data-stu-id="aa1de-226">Inclusion Violations pane</span></span>  
 <span data-ttu-id="aa1de-227">**\<column1>、\<column2> 等。**</span><span class="sxs-lookup"><span data-stu-id="aa1de-227">**\<column1>, \<column2>, etc.**</span></span>  
 <span data-ttu-id="aa1de-228">顯示子集資料行中的值，但這些值在超集資料行中找不到。</span><span class="sxs-lookup"><span data-stu-id="aa1de-228">Displays the values in the subset column or columns that were not found in the superset column or columns.</span></span>  
  
 <span data-ttu-id="aa1de-229">**Count**</span><span class="sxs-lookup"><span data-stu-id="aa1de-229">**Count**</span></span>  
 <span data-ttu-id="aa1de-230">顯示指定之資料行具有第一個資料行中所顯示之值的資料列數目。</span><span class="sxs-lookup"><span data-stu-id="aa1de-230">Displays the number of rows in which the specified column has the value shown in the first column.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa1de-231">另請參閱</span><span class="sxs-lookup"><span data-stu-id="aa1de-231">See Also</span></span>  
 <span data-ttu-id="aa1de-232">[資料設定檔檢視器](control-flow/data-profile-viewer.md) </span><span class="sxs-lookup"><span data-stu-id="aa1de-232">[Data Profile Viewer](control-flow/data-profile-viewer.md) </span></span>  
 [<span data-ttu-id="aa1de-233">資料分析工作和檢視器</span><span class="sxs-lookup"><span data-stu-id="aa1de-233">Data Profiling Task and Viewer</span></span>](control-flow/data-profiling-task-and-viewer.md)  
  
  
