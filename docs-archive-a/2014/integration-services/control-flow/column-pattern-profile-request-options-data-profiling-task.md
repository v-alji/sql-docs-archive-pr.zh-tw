---
title: 資料行模式設定檔要求選項 (資料分析工作) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Data Profiling Task Editor
ms.assetid: 9ccb8fc5-f65e-41a2-9511-7fa55586eb8b
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f9293d19baaee95cee77b075447dcfe1061d20bb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595226"
---
# <a name="column-pattern-profile-request-options-data-profiling-task"></a><span data-ttu-id="db339-102">資料行模式設定檔要求選項 (資料分析工作)</span><span class="sxs-lookup"><span data-stu-id="db339-102">Column Pattern Profile Request Options (Data Profiling Task)</span></span>
  <span data-ttu-id="db339-103">您可以使用 [設定檔要求] 頁面的 [要求屬性] 窗格，針對要求窗格中選取的 [資料行模式設定檔要求] 設定選項。</span><span class="sxs-lookup"><span data-stu-id="db339-103">Use the **Request Properties** pane of the **Profile Requests** page to set the options for the **Column Pattern Profile Request** selected in the requests pane.</span></span> <span data-ttu-id="db339-104">資料行模式設定檔會報告一組規則運算式，其中涵蓋了字串資料行中值的指定百分比。</span><span class="sxs-lookup"><span data-stu-id="db339-104">A Column Pattern profile reports a set of regular expressions that cover the specified percentage of values in a string column.</span></span> <span data-ttu-id="db339-105">這個設定檔可協助您識別資料中的問題，例如無效的字串，而且可以建議未來可用於驗證新值的規則運算式。</span><span class="sxs-lookup"><span data-stu-id="db339-105">This profile can help you identify problems in your data, such as invalid strings, and can suggest regular expressions that can be used in the future to validate new values.</span></span> <span data-ttu-id="db339-106">舉例來說，「美國郵遞區號」資料行的模式設定檔可能會產生規則運算式 \d{5}-\d{4}、\d{5} 和 \d{9}。</span><span class="sxs-lookup"><span data-stu-id="db339-106">For example, a pattern profile of a column of United States Zip Codes might produce the regular expressions \d{5}-\d{4}, \d{5}, and \d{9}.</span></span> <span data-ttu-id="db339-107">如果您看見其他規則運算式，表示您的資料可能包含無效或格式錯誤的值。</span><span class="sxs-lookup"><span data-stu-id="db339-107">If you see other regular expressions, your data likely contains values that are invalid or in an incorrect format.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="db339-108">本主題所描述的選項會顯示在 **[資料分析工作編輯器]** 的 **[設定檔要求]** 頁面上。</span><span class="sxs-lookup"><span data-stu-id="db339-108">The options described in this topic appear on the **Profile Requests page** of the **Data Profiling Task Editor**.</span></span> <span data-ttu-id="db339-109">如需此編輯器頁面的詳細資訊，請參閱[資料分析工作編輯器 &#40;設定檔要求頁面&#41;](data-profiling-task-editor-profile-requests-page.md)。</span><span class="sxs-lookup"><span data-stu-id="db339-109">For more information about this page of the editor, see [Data Profiling Task Editor &#40;Profile Requests Page&#41;](data-profiling-task-editor-profile-requests-page.md).</span></span>  
  
 <span data-ttu-id="db339-110">如需如何使用資料分析工作的詳細資訊，請參閱 [資料分析工作的設定](data-profiling-task.md)。</span><span class="sxs-lookup"><span data-stu-id="db339-110">For more information about how to use the Data Profiling Task, see [Setup of the Data Profiling Task](data-profiling-task.md).</span></span> <span data-ttu-id="db339-111">如需如何使用資料設定檔檢視器來分析資料分析工作輸出的詳細資訊，請參閱 [資料設定檔檢視器](data-profile-viewer.md)。</span><span class="sxs-lookup"><span data-stu-id="db339-111">For more information about how to use the Data Profile Viewer to analyze the output of the Data Profiling Task, see [Data Profile Viewer](data-profile-viewer.md).</span></span>  
  
## <a name="understanding-the-use-of-delimiters-and-symbols"></a><span data-ttu-id="db339-112">了解分隔符號和符號的使用方式</span><span class="sxs-lookup"><span data-stu-id="db339-112">Understanding the Use of Delimiters and Symbols</span></span>  
 <span data-ttu-id="db339-113">針對 [資料行模式設定檔要求]  計算模式之前，資料分析工作會 Token 化資料。</span><span class="sxs-lookup"><span data-stu-id="db339-113">Before computing the patterns for a **Column Pattern Profile Request**, the Data Profiling Task tokenizes the data.</span></span> <span data-ttu-id="db339-114">也就是說，此工作會將字串值分隔成名為 Token 的較小單位。</span><span class="sxs-lookup"><span data-stu-id="db339-114">That is, the task separates the string values into smaller units known as tokens.</span></span> <span data-ttu-id="db339-115">此工作會根據您針對 [分隔符號]  和 [符號]  屬性指定的分隔符號和符號，將字串分隔成 Token：</span><span class="sxs-lookup"><span data-stu-id="db339-115">The task separates strings into tokens based on the delimiters and symbols that you specify for the **Delimiters** and **Symbols** properties:</span></span>  
  
-   <span data-ttu-id="db339-116">**分隔符號** ：根據預設，分隔符號清單包含下列字元：空格、水平定位字元 (\t)、新行字元 (\n) 和歸位字元 (\r)。</span><span class="sxs-lookup"><span data-stu-id="db339-116">**Delimiters** By default, the list of delimiters contains the following characters: space, horizontal tab (\t), new line (\n), and carriage return (\r).</span></span> <span data-ttu-id="db339-117">雖然您可以指定其他分隔符號，但是無法移除預設的分隔符號。</span><span class="sxs-lookup"><span data-stu-id="db339-117">You can specify additional delimiters, but you cannot remove the default delimiters.</span></span>  
  
-   <span data-ttu-id="db339-118">**符號**根據預設，**符號**清單包含下列字元： `,.;:-"'` ~ =&/@！？ ( # A2 # A0 [] {} | # \* ^% `. For example, if the symbols are "` ( # A4-' "，" (425) 123-4567 "的值已標記為 [" ( "，" 425 "，" ) "，" 123 "，"-"，" 4567 "，" ) "]。</span><span class="sxs-lookup"><span data-stu-id="db339-118">**Symbols** By default, the list of **Symbols** contains the following characters: `,.;:-"'`~=&/@!?()<>[]{}|#\*^%`. For example, if the symbols are "`()-\`", the value "(425) 123-4567" is tokenized as ["(", "425", ")", "123", "-", "4567", ")"].</span></span>  
  
 <span data-ttu-id="db339-119">一個字元無法同時屬於分隔符號和符號。</span><span class="sxs-lookup"><span data-stu-id="db339-119">A character cannot be both a delimiter and a symbol.</span></span>  
  
 <span data-ttu-id="db339-120">所有分隔符號都會在 Token 化程序中正規化成為單一空格，而符號則會保留。</span><span class="sxs-lookup"><span data-stu-id="db339-120">All delimiters are normalized to a single space as part of the tokenizing process, while symbols are retained.</span></span>  
  
## <a name="understanding-the-use-of-the-tag-table"></a><span data-ttu-id="db339-121">了解標記資料表的使用方式</span><span class="sxs-lookup"><span data-stu-id="db339-121">Understanding the Use of the Tag Table</span></span>  
 <span data-ttu-id="db339-122">您可以將標記和相關的詞彙儲存在您於 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫中建立的特殊資料表中，藉以選擇性地以單一標記將相關 Token 組成群組。</span><span class="sxs-lookup"><span data-stu-id="db339-122">You can optionally group related tokens with a single tag by storing tags and the related terms in a special table that you create in a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database.</span></span> <span data-ttu-id="db339-123">標記資料表必須具有兩個字串資料行：一個名為「標記」，而另一個名為「詞彙」。</span><span class="sxs-lookup"><span data-stu-id="db339-123">The tag table must have two string columns, one named "Tag" and the other named "Term".</span></span> <span data-ttu-id="db339-124">這些資料行的類型可以是 `char`、`nchar`、`varchar` 或 `nvarchar`，但不得為 `text` 或 `ntext`。</span><span class="sxs-lookup"><span data-stu-id="db339-124">These columns can be of type `char`, `nchar`, `varchar`, or `nvarchar`, but not `text` or `ntext`.</span></span> <span data-ttu-id="db339-125">您可以在單一資料表中結合多個標記和對應的詞彙。</span><span class="sxs-lookup"><span data-stu-id="db339-125">You can combine multiple tags and the corresponding terms in a single table.</span></span> <span data-ttu-id="db339-126">一個資料行模式設定檔要求只能使用一份標記資料表。</span><span class="sxs-lookup"><span data-stu-id="db339-126">A Column Pattern Profile Request can use only one tag table.</span></span> <span data-ttu-id="db339-127">您可以使用個別的 [!INCLUDE[vstecado](../../includes/vstecado-md.md)] 連線管理員來連接至標記資料表。</span><span class="sxs-lookup"><span data-stu-id="db339-127">You can use a separate [!INCLUDE[vstecado](../../includes/vstecado-md.md)] connection manager to connect to the tag table.</span></span> <span data-ttu-id="db339-128">因此，標記資料表可以位於不同的資料庫中或與來源資料位於不同的伺服器上。</span><span class="sxs-lookup"><span data-stu-id="db339-128">Therefore, the tag table can be located in a different database or on a different server than the source data.</span></span>  
  
 <span data-ttu-id="db339-129">例如，您可以使用單一標記「方向」，將可能顯示在街道地址中的「東」、「西」、「北」和「南」值組成群組。</span><span class="sxs-lookup"><span data-stu-id="db339-129">For example, you could group the values "East", "West", "North", and "South" that might appear in street addresses by using the single tag, "Direction".</span></span> <span data-ttu-id="db339-130">下表是這類標記資料表的範例。</span><span class="sxs-lookup"><span data-stu-id="db339-130">The following table is an example of such a tag table.</span></span>  
  
|<span data-ttu-id="db339-131">Tag</span><span class="sxs-lookup"><span data-stu-id="db339-131">Tag</span></span>|<span data-ttu-id="db339-132">詞彙</span><span class="sxs-lookup"><span data-stu-id="db339-132">Term</span></span>|  
|---------|----------|  
|<span data-ttu-id="db339-133">方向</span><span class="sxs-lookup"><span data-stu-id="db339-133">Direction</span></span>|<span data-ttu-id="db339-134">東</span><span class="sxs-lookup"><span data-stu-id="db339-134">East</span></span>|  
|<span data-ttu-id="db339-135">方向</span><span class="sxs-lookup"><span data-stu-id="db339-135">Direction</span></span>|<span data-ttu-id="db339-136">West</span><span class="sxs-lookup"><span data-stu-id="db339-136">West</span></span>|  
|<span data-ttu-id="db339-137">方向</span><span class="sxs-lookup"><span data-stu-id="db339-137">Direction</span></span>|<span data-ttu-id="db339-138">北</span><span class="sxs-lookup"><span data-stu-id="db339-138">North</span></span>|  
|<span data-ttu-id="db339-139">方向</span><span class="sxs-lookup"><span data-stu-id="db339-139">Direction</span></span>|<span data-ttu-id="db339-140">南</span><span class="sxs-lookup"><span data-stu-id="db339-140">South</span></span>|  
  
 <span data-ttu-id="db339-141">您可以使用另一個標記，將在街道地址中表示「街道」概念的不同字詞組成群組：</span><span class="sxs-lookup"><span data-stu-id="db339-141">You could use another tag to group the different words that express the notion of a "street" in street addresses:</span></span>  
  
|<span data-ttu-id="db339-142">Tag</span><span class="sxs-lookup"><span data-stu-id="db339-142">Tag</span></span>|<span data-ttu-id="db339-143">詞彙</span><span class="sxs-lookup"><span data-stu-id="db339-143">Term</span></span>|  
|---------|----------|  
|<span data-ttu-id="db339-144">Street</span><span class="sxs-lookup"><span data-stu-id="db339-144">Street</span></span>|<span data-ttu-id="db339-145">Street</span><span class="sxs-lookup"><span data-stu-id="db339-145">Street</span></span>|  
|<span data-ttu-id="db339-146">Street</span><span class="sxs-lookup"><span data-stu-id="db339-146">Street</span></span>|<span data-ttu-id="db339-147">道</span><span class="sxs-lookup"><span data-stu-id="db339-147">Avenue</span></span>|  
|<span data-ttu-id="db339-148">Street</span><span class="sxs-lookup"><span data-stu-id="db339-148">Street</span></span>|<span data-ttu-id="db339-149">位置</span><span class="sxs-lookup"><span data-stu-id="db339-149">Place</span></span>|  
|<span data-ttu-id="db339-150">Street</span><span class="sxs-lookup"><span data-stu-id="db339-150">Street</span></span>|<span data-ttu-id="db339-151">路</span><span class="sxs-lookup"><span data-stu-id="db339-151">Way</span></span>|  
  
 <span data-ttu-id="db339-152">根據這種標記的組合，街道地址的產生模式可能會類似於下列模式：</span><span class="sxs-lookup"><span data-stu-id="db339-152">Based on this combination of tags, the resulting pattern for a street address might resemble the following pattern:</span></span>  
  
 `\d+\ LookupTag=Direction \d+\p{L}+\ LookupTag=Street`  
  
> [!NOTE]  
>  <span data-ttu-id="db339-153">使用標記資料表會降低資料分析工作的效能。</span><span class="sxs-lookup"><span data-stu-id="db339-153">Using a tag table decreases the performance of the Data Profiling task.</span></span> <span data-ttu-id="db339-154">請勿使用超過 10 個標記或使用超過 100 個詞彙 (每個標記)。</span><span class="sxs-lookup"><span data-stu-id="db339-154">Do not use more than 10 tags or more than 100 terms per tag.</span></span>  
  
 <span data-ttu-id="db339-155">相同的詞彙可以屬於多個標記。</span><span class="sxs-lookup"><span data-stu-id="db339-155">The same term can belong to more than one tag.</span></span>  
  
## <a name="request-properties-options"></a><span data-ttu-id="db339-156">要求屬性選項</span><span class="sxs-lookup"><span data-stu-id="db339-156">Request Properties Options</span></span>  
 <span data-ttu-id="db339-157">[要求屬性]\*\*\*\* 窗格會針對 [資料行模式設定檔要求]\*\*\*\* 顯示下列選項群組：</span><span class="sxs-lookup"><span data-stu-id="db339-157">For a **Column Pattern Profile Request**, the **Request Properties** pane displays the following groups of options:</span></span>  
  
-   <span data-ttu-id="db339-158">**[資料]**，其中包括 **[TableOrView]** 和 **[資料行]** 選項。</span><span class="sxs-lookup"><span data-stu-id="db339-158">**Data**, which includes the **TableOrView** and **Column** options</span></span>  
  
-   <span data-ttu-id="db339-159">**一般**</span><span class="sxs-lookup"><span data-stu-id="db339-159">**General**</span></span>  
  
-   <span data-ttu-id="db339-160">**選項**</span><span class="sxs-lookup"><span data-stu-id="db339-160">**Options**</span></span>  
  
### <a name="data-options"></a><span data-ttu-id="db339-161">資料選項</span><span class="sxs-lookup"><span data-stu-id="db339-161">Data Options</span></span>  
 <span data-ttu-id="db339-162">**ConnectionManager**</span><span class="sxs-lookup"><span data-stu-id="db339-162">**ConnectionManager**</span></span>  
 <span data-ttu-id="db339-163">選取現有的 [!INCLUDE[vstecado](../../includes/vstecado-md.md)] 連線管理員，以便使用 .NET Data Provider for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (SqlClient) 來連線至包含要分析之資料表或檢視表的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫。</span><span class="sxs-lookup"><span data-stu-id="db339-163">Select the existing [!INCLUDE[vstecado](../../includes/vstecado-md.md)] connection manager that uses the .NET Data Provider for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (SqlClient) to connect to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database that contains the table or view to be profiled.</span></span>  
  
 <span data-ttu-id="db339-164">**Tableorview]**</span><span class="sxs-lookup"><span data-stu-id="db339-164">**TableOrView**</span></span>  
 <span data-ttu-id="db339-165">選取包含要分析之資料行的資料表或檢視表。</span><span class="sxs-lookup"><span data-stu-id="db339-165">Select the existing table or view that contains the column to be profiled.</span></span>  
  
 <span data-ttu-id="db339-166">如需詳細資訊，請參閱本主題中的「TableorView 選項」一節。</span><span class="sxs-lookup"><span data-stu-id="db339-166">For more information, see the section, "TableorView Options," in this topic.</span></span>  
  
 <span data-ttu-id="db339-167">**資料行**</span><span class="sxs-lookup"><span data-stu-id="db339-167">**Column**</span></span>  
 <span data-ttu-id="db339-168">選取要分析的現有資料行。</span><span class="sxs-lookup"><span data-stu-id="db339-168">Select the existing column to be profiled.</span></span> <span data-ttu-id="db339-169">選取\*\* (\*) \*\*來分析所有資料行。</span><span class="sxs-lookup"><span data-stu-id="db339-169">Select **(\*)** to profile all columns.</span></span>  
  
 <span data-ttu-id="db339-170">如需詳細資訊，請參閱本主題中的「資料行選項」一節。</span><span class="sxs-lookup"><span data-stu-id="db339-170">For more information, see the section, "Column Options," in this topic.</span></span>  
  
#### <a name="tableorview-options"></a><span data-ttu-id="db339-171">TableOrView 選項</span><span class="sxs-lookup"><span data-stu-id="db339-171">TableOrView Options</span></span>  
 <span data-ttu-id="db339-172">**結構描述**</span><span class="sxs-lookup"><span data-stu-id="db339-172">**Schema**</span></span>  
 <span data-ttu-id="db339-173">指定選取之資料表所屬的結構描述。</span><span class="sxs-lookup"><span data-stu-id="db339-173">Specifies the schema to which the selected table belongs.</span></span> <span data-ttu-id="db339-174">此選項是唯讀的。</span><span class="sxs-lookup"><span data-stu-id="db339-174">This option is read-only.</span></span>  
  
 <span data-ttu-id="db339-175">**資料表**</span><span class="sxs-lookup"><span data-stu-id="db339-175">**Table**</span></span>  
 <span data-ttu-id="db339-176">顯示選取之資料表的名稱。</span><span class="sxs-lookup"><span data-stu-id="db339-176">Displays the name of the selected table.</span></span> <span data-ttu-id="db339-177">此選項是唯讀的。</span><span class="sxs-lookup"><span data-stu-id="db339-177">This option is read-only.</span></span>  
  
#### <a name="column-options"></a><span data-ttu-id="db339-178">資料行選項</span><span class="sxs-lookup"><span data-stu-id="db339-178">Column Options</span></span>  
 <span data-ttu-id="db339-179">**IsWildCard**</span><span class="sxs-lookup"><span data-stu-id="db339-179">**IsWildCard**</span></span>  
 <span data-ttu-id="db339-180">指定是否已選取\*\* (\*) \*\*萬用字元。</span><span class="sxs-lookup"><span data-stu-id="db339-180">Specifies whether the **(\*)** wildcard has been selected.</span></span> <span data-ttu-id="db339-181">如果您已選取 **(\*)** 來分析所有資料行，這個選項會設定為 [True]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="db339-181">This option is set to **True** if you have selected **(\*)** to profile all columns.</span></span> <span data-ttu-id="db339-182">如果您已選取要分析的個別資料行，它就會設定為 **[False]** 。</span><span class="sxs-lookup"><span data-stu-id="db339-182">It is **False** if you have selected an individual column to be profiled.</span></span> <span data-ttu-id="db339-183">此選項是唯讀的。</span><span class="sxs-lookup"><span data-stu-id="db339-183">This option is read-only.</span></span>  
  
 <span data-ttu-id="db339-184">**ColumnName**</span><span class="sxs-lookup"><span data-stu-id="db339-184">**ColumnName**</span></span>  
 <span data-ttu-id="db339-185">顯示所選取資料行的名稱。</span><span class="sxs-lookup"><span data-stu-id="db339-185">Displays the name of the selected column.</span></span> <span data-ttu-id="db339-186">如果您已選取\*\* (\*) \*\*來分析所有資料行，這個選項就是空白的。</span><span class="sxs-lookup"><span data-stu-id="db339-186">This option is blank if you have selected **(\*)** to profile all columns.</span></span> <span data-ttu-id="db339-187">此選項是唯讀的。</span><span class="sxs-lookup"><span data-stu-id="db339-187">This option is read-only.</span></span>  
  
 <span data-ttu-id="db339-188">**StringCompareOptions**</span><span class="sxs-lookup"><span data-stu-id="db339-188">**StringCompareOptions**</span></span>  
 <span data-ttu-id="db339-189">這個選項不會套用至資料行模式設定檔。</span><span class="sxs-lookup"><span data-stu-id="db339-189">This option does not apply to the Column Pattern Profile.</span></span>  
  
### <a name="general-options"></a><span data-ttu-id="db339-190">一般選項</span><span class="sxs-lookup"><span data-stu-id="db339-190">General Options</span></span>  
 <span data-ttu-id="db339-191">**RequestID**</span><span class="sxs-lookup"><span data-stu-id="db339-191">**RequestID**</span></span>  
 <span data-ttu-id="db339-192">輸入描述性名稱，以便識別這個設定檔要求。</span><span class="sxs-lookup"><span data-stu-id="db339-192">Type a descriptive name to identify this profile request.</span></span> <span data-ttu-id="db339-193">一般而言，您不需要變更自動產生的值。</span><span class="sxs-lookup"><span data-stu-id="db339-193">Typically, you do not have to change the autogenerated value.</span></span>  
  
### <a name="options"></a><span data-ttu-id="db339-194">選項</span><span class="sxs-lookup"><span data-stu-id="db339-194">Options</span></span>  
 <span data-ttu-id="db339-195">**MaxNumberOfPatterns**</span><span class="sxs-lookup"><span data-stu-id="db339-195">**MaxNumberOfPatterns**</span></span>  
 <span data-ttu-id="db339-196">指定您想讓設定檔計算的模式數目上限。</span><span class="sxs-lookup"><span data-stu-id="db339-196">Specify the maximum number of patterns that you want the profile to compute.</span></span> <span data-ttu-id="db339-197">這個選項的預設值為 10。</span><span class="sxs-lookup"><span data-stu-id="db339-197">The default value of this option is 10.</span></span> <span data-ttu-id="db339-198">最大值為 100。</span><span class="sxs-lookup"><span data-stu-id="db339-198">The maximum value is 100.</span></span>  
  
 <span data-ttu-id="db339-199">**PercentageDataCoverageDesired**</span><span class="sxs-lookup"><span data-stu-id="db339-199">**PercentageDataCoverageDesired**</span></span>  
 <span data-ttu-id="db339-200">指定您想讓計算模式涵蓋的資料百分比。</span><span class="sxs-lookup"><span data-stu-id="db339-200">Specify the percentage of the data that you want the computed patterns to cover.</span></span> <span data-ttu-id="db339-201">這個選項的預設值為 95 (%)。</span><span class="sxs-lookup"><span data-stu-id="db339-201">The default value of this option is 95 (percent).</span></span>  
  
 <span data-ttu-id="db339-202">**CaseSensitive**</span><span class="sxs-lookup"><span data-stu-id="db339-202">**CaseSensitive**</span></span>  
 <span data-ttu-id="db339-203">指出模式是否應該區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="db339-203">Indicate whether the patterns should be case-sensitive.</span></span> <span data-ttu-id="db339-204">此選項的預設值是 **[False]**。</span><span class="sxs-lookup"><span data-stu-id="db339-204">The default value of this option is **False**.</span></span>  
  
 <span data-ttu-id="db339-205">**分隔符號**</span><span class="sxs-lookup"><span data-stu-id="db339-205">**Delimiters**</span></span>  
 <span data-ttu-id="db339-206">列出在 Token 化文字時應該視為字詞之間空格對等項目的字元。</span><span class="sxs-lookup"><span data-stu-id="db339-206">List the characters that should be treated as the equivalent of spaces between words when tokenizing text.</span></span> <span data-ttu-id="db339-207">根據預設，[分隔符號]\*\*\*\* 清單包含下列字元：空格、水平定位字元 (\t)、新行字元 (\n) 和歸位字元 (\r)。</span><span class="sxs-lookup"><span data-stu-id="db339-207">By default, the list of **Delimiters** contains the following characters: the space, horizontal tab (\t), new line (\n), and carriage return (\r).</span></span> <span data-ttu-id="db339-208">雖然您可以指定其他分隔符號，但是無法移除預設的分隔符號。</span><span class="sxs-lookup"><span data-stu-id="db339-208">You can specify additional delimiters, but you cannot remove the default delimiters.</span></span>  
  
 <span data-ttu-id="db339-209">如需詳細資訊，請參閱本主題前面的「了解分隔符號和符號的使用方式」。</span><span class="sxs-lookup"><span data-stu-id="db339-209">For more information, see "Understanding the Use of Delimiters and Symbols" earlier in this topic.</span></span>  
  
 <span data-ttu-id="db339-210">**標點符號**</span><span class="sxs-lookup"><span data-stu-id="db339-210">**Symbols**</span></span>  
 <span data-ttu-id="db339-211">列出應該保留成為模式一部分的符號。</span><span class="sxs-lookup"><span data-stu-id="db339-211">List the symbols that should be retained as part of patterns.</span></span> <span data-ttu-id="db339-212">範例可能包括 "/" (代表日期)、":" (代表時間) 和 ‘\@’ (代表電子郵件地址)。</span><span class="sxs-lookup"><span data-stu-id="db339-212">Examples might include "/" for dates, ":" for times, and "@" for e-mail addresses.</span></span> <span data-ttu-id="db339-213">根據預設，**符號**清單包含下列字元： `,.;:-"'` ~ =&/@！？ ( # A2 # A0 [] {} | # \* ^% '。</span><span class="sxs-lookup"><span data-stu-id="db339-213">By default, the list of **Symbols** contains the following characters: `,.;:-"'`~=&/@!?()<>[]{}|#\*^%\`.</span></span>  
  
 <span data-ttu-id="db339-214">如需詳細資訊，請參閱本主題前面的「了解分隔符號和符號的使用方式」。</span><span class="sxs-lookup"><span data-stu-id="db339-214">For more information, see "Understanding the Use of Delimiters and Symbols" earlier in this topic.</span></span>  
  
 <span data-ttu-id="db339-215">**TagTableConnectionManager**</span><span class="sxs-lookup"><span data-stu-id="db339-215">**TagTableConnectionManager**</span></span>  
 <span data-ttu-id="db339-216">選取現有的 [!INCLUDE[vstecado](../../includes/vstecado-md.md)] 連線管理員，以便使用 .NET Data Provider for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (SqlClient) 來連接至包含標記資料表的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫。</span><span class="sxs-lookup"><span data-stu-id="db339-216">Select the existing [!INCLUDE[vstecado](../../includes/vstecado-md.md)] connection manager that uses the .NET Data Provider for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (SqlClient) to connect to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database that contains the tag table.</span></span>  
  
 <span data-ttu-id="db339-217">如需詳細資訊，請參閱本主題前面的「了解標記資料表的使用方式」。</span><span class="sxs-lookup"><span data-stu-id="db339-217">For more information, see "Understanding the Use of the Tag Table" earlier in this topic.</span></span>  
  
 <span data-ttu-id="db339-218">**TagTableName**</span><span class="sxs-lookup"><span data-stu-id="db339-218">**TagTableName**</span></span>  
 <span data-ttu-id="db339-219">選取現有的標記資料表，其中必須具有兩個分別名為「標記」和「詞彙」的資料行。</span><span class="sxs-lookup"><span data-stu-id="db339-219">Select the existing tag table, which must have two string columns named Tag and Term.</span></span>  
  
 <span data-ttu-id="db339-220">如需詳細資訊，請參閱本主題前面的「了解標記資料表的使用方式」。</span><span class="sxs-lookup"><span data-stu-id="db339-220">For more information, see "Understanding the Use of the Tag Table" earlier in this topic.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db339-221">另請參閱</span><span class="sxs-lookup"><span data-stu-id="db339-221">See Also</span></span>  
 <span data-ttu-id="db339-222">[[資料分析工作編輯器] &#40;一般頁面&#41;](../general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="db339-222">[Data Profiling Task Editor &#40;General Page&#41;](../general-page-of-integration-services-designers-options.md) </span></span>  
 [<span data-ttu-id="db339-223">單一資料表快速分析表單 &#40;資料分析工作&#41;</span><span class="sxs-lookup"><span data-stu-id="db339-223">Single Table Quick Profile Form &#40;Data Profiling Task&#41;</span></span>](single-table-quick-profile-form-data-profiling-task.md)  
  
  
