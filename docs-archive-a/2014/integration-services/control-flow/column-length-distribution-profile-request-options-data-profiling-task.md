---
title: 資料行長度散發設定檔要求選項 (資料分析工作) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Data Profiling Task Editor
ms.assetid: 1a4de41f-f38d-40ea-ba1b-6c0ef67ea52a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 4c0ebb6f1e0a6df2c0e47311f7b8217c5ce6f2df
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595238"
---
# <a name="column-length-distribution-profile-request-options-data-profiling-task"></a><span data-ttu-id="44429-102">資料行長度散發設定檔要求選項 (資料分析工作)</span><span class="sxs-lookup"><span data-stu-id="44429-102">Column Length Distribution Profile Request Options (Data Profiling Task)</span></span>
  <span data-ttu-id="44429-103">您可以使用 **[設定檔要求]** 頁面的 **[要求屬性]** 窗格，針對要求窗格中選取的 **[資料行長度散發設定檔要求]** 設定選項。</span><span class="sxs-lookup"><span data-stu-id="44429-103">Use the **Request Properties** pane of the **Profile Requests** page to set the options for the **Column Length Distribution Profile Request** selected in the requests pane.</span></span> <span data-ttu-id="44429-104">資料行長度散發設定檔會報告選取之資料行中字串值的所有相異長度，以及該資料表中每個長度所代表之資料列的百分比。</span><span class="sxs-lookup"><span data-stu-id="44429-104">A Column Length Distribution profile reports all the distinct lengths of string values in the selected column and the percentage of rows in the table that each length represents.</span></span> <span data-ttu-id="44429-105">這個設定檔可協助您識別資料中的問題，例如無效的值。</span><span class="sxs-lookup"><span data-stu-id="44429-105">This profile can help you identify problems in your data such as invalid values.</span></span> <span data-ttu-id="44429-106">舉例來說，您分析了美國州名二字元代碼的資料行並發現長度超過兩個字元的值。</span><span class="sxs-lookup"><span data-stu-id="44429-106">For example, you profile a column of two-character United States state codes and discover values longer than two characters.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="44429-107">本主題所描述的選項會顯示在 **[資料分析工作編輯器]** 的 **[設定檔要求]** 頁面上。</span><span class="sxs-lookup"><span data-stu-id="44429-107">The options described in this topic appear on the **Profile Requests page** of the **Data Profiling Task Editor**.</span></span> <span data-ttu-id="44429-108">如需此編輯器頁面的詳細資訊，請參閱[資料分析工作編輯器 &#40;設定檔要求頁面&#41;](data-profiling-task-editor-profile-requests-page.md)。</span><span class="sxs-lookup"><span data-stu-id="44429-108">For more information about this page of the editor, see [Data Profiling Task Editor &#40;Profile Requests Page&#41;](data-profiling-task-editor-profile-requests-page.md).</span></span>  
  
 <span data-ttu-id="44429-109">如需如何使用資料分析工作的詳細資訊，請參閱 [資料分析工作的設定](data-profiling-task.md)。</span><span class="sxs-lookup"><span data-stu-id="44429-109">For more information about how to use the Data Profiling Task, see [Setup of the Data Profiling Task](data-profiling-task.md).</span></span> <span data-ttu-id="44429-110">如需如何使用資料設定檔檢視器來分析資料分析工作輸出的詳細資訊，請參閱 [資料設定檔檢視器](data-profile-viewer.md)。</span><span class="sxs-lookup"><span data-stu-id="44429-110">For more information about how to use the Data Profile Viewer to analyze the output of the Data Profiling Task, see [Data Profile Viewer](data-profile-viewer.md).</span></span>  
  
## <a name="request-properties-options"></a><span data-ttu-id="44429-111">要求屬性選項</span><span class="sxs-lookup"><span data-stu-id="44429-111">Request Properties Options</span></span>  
 <span data-ttu-id="44429-112">**[要求屬性]** 窗格會針對 **[資料行長度散發設定檔要求]** 顯示下列選項群組：</span><span class="sxs-lookup"><span data-stu-id="44429-112">For a **Column Length Distribution Profile Request**, the **Request Properties** pane displays the following groups of options:</span></span>  
  
-   <span data-ttu-id="44429-113">**[資料]** ，其中包括 **[TableOrView]** 和 **[資料行]** 選項。</span><span class="sxs-lookup"><span data-stu-id="44429-113">**Data**, which includes the **TableOrView** and **Column** options</span></span>  
  
-   <span data-ttu-id="44429-114">**一般**</span><span class="sxs-lookup"><span data-stu-id="44429-114">**General**</span></span>  
  
-   <span data-ttu-id="44429-115">**選項**</span><span class="sxs-lookup"><span data-stu-id="44429-115">**Options**</span></span>  
  
### <a name="data-options"></a><span data-ttu-id="44429-116">資料選項</span><span class="sxs-lookup"><span data-stu-id="44429-116">Data Options</span></span>  
 <span data-ttu-id="44429-117">**ConnectionManager**</span><span class="sxs-lookup"><span data-stu-id="44429-117">**ConnectionManager**</span></span>  
 <span data-ttu-id="44429-118">選取現有的 [!INCLUDE[vstecado](../../includes/vstecado-md.md)] 連線管理員，以便使用 .NET Data Provider for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (SqlClient) 來連線至包含要分析之資料表或檢視表的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫。</span><span class="sxs-lookup"><span data-stu-id="44429-118">Select the existing [!INCLUDE[vstecado](../../includes/vstecado-md.md)] connection manager that uses the .NET Data Provider for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (SqlClient) to connect to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database that contains the table or view to be profiled.</span></span>  
  
 <span data-ttu-id="44429-119">**[TableOrView]**</span><span class="sxs-lookup"><span data-stu-id="44429-119">**TableOrView**</span></span>  
 <span data-ttu-id="44429-120">選取包含要分析之資料行的資料表或檢視表。</span><span class="sxs-lookup"><span data-stu-id="44429-120">Select the existing table or view that contains the column to be profiled.</span></span>  
  
 <span data-ttu-id="44429-121">如需詳細資訊，請參閱本主題中的「TableorView 選項」一節。</span><span class="sxs-lookup"><span data-stu-id="44429-121">For more information, see the section, "TableorView Options," in this topic.</span></span>  
  
 <span data-ttu-id="44429-122">**資料行**</span><span class="sxs-lookup"><span data-stu-id="44429-122">**Column**</span></span>  
 <span data-ttu-id="44429-123">選取要分析的現有資料行。</span><span class="sxs-lookup"><span data-stu-id="44429-123">Select the existing column to be profiled.</span></span> <span data-ttu-id="44429-124">您可以選取 **(\*)** 來分析所有資料行。</span><span class="sxs-lookup"><span data-stu-id="44429-124">Select **(\*)** to profile all columns.</span></span>  
  
 <span data-ttu-id="44429-125">如需詳細資訊，請參閱本主題中的「資料行選項」一節。</span><span class="sxs-lookup"><span data-stu-id="44429-125">For more information, see the section, "Column Options," in this topic.</span></span>  
  
#### <a name="tableorview-options"></a><span data-ttu-id="44429-126">TableOrView 選項</span><span class="sxs-lookup"><span data-stu-id="44429-126">TableOrView Options</span></span>  
 <span data-ttu-id="44429-127">**結構描述**</span><span class="sxs-lookup"><span data-stu-id="44429-127">**Schema**</span></span>  
 <span data-ttu-id="44429-128">指定選取之資料表所屬的結構描述。</span><span class="sxs-lookup"><span data-stu-id="44429-128">Specify the schema to which the selected table belongs.</span></span> <span data-ttu-id="44429-129">此選項是唯讀的。</span><span class="sxs-lookup"><span data-stu-id="44429-129">This option is read-only.</span></span>  
  
 <span data-ttu-id="44429-130">**Table**</span><span class="sxs-lookup"><span data-stu-id="44429-130">**Table**</span></span>  
 <span data-ttu-id="44429-131">顯示選取之資料表的名稱。</span><span class="sxs-lookup"><span data-stu-id="44429-131">Displays the name of the selected table.</span></span> <span data-ttu-id="44429-132">此選項是唯讀的。</span><span class="sxs-lookup"><span data-stu-id="44429-132">This option is read-only.</span></span>  
  
#### <a name="column-options"></a><span data-ttu-id="44429-133">資料行選項</span><span class="sxs-lookup"><span data-stu-id="44429-133">Column Options</span></span>  
 <span data-ttu-id="44429-134">**IsWildCard**</span><span class="sxs-lookup"><span data-stu-id="44429-134">**IsWildCard**</span></span>  
 <span data-ttu-id="44429-135">指定是否已經選取 **(\*)** 萬用字元。</span><span class="sxs-lookup"><span data-stu-id="44429-135">Specifies whether the **(\*)** wildcard has been selected.</span></span> <span data-ttu-id="44429-136">如果您已選取 **(\*)** 來分析所有資料行，這個選項會設定為 [True]。</span><span class="sxs-lookup"><span data-stu-id="44429-136">This option is set to **True** if you have selected **(\*)** to profile all columns.</span></span> <span data-ttu-id="44429-137">如果您已選取要分析的個別資料行，它就會設定為 **[False]** 。</span><span class="sxs-lookup"><span data-stu-id="44429-137">It is **False** if you have selected an individual column to be profiled.</span></span> <span data-ttu-id="44429-138">此選項是唯讀的。</span><span class="sxs-lookup"><span data-stu-id="44429-138">This option is read-only.</span></span>  
  
 <span data-ttu-id="44429-139">**ColumnName**</span><span class="sxs-lookup"><span data-stu-id="44429-139">**ColumnName**</span></span>  
 <span data-ttu-id="44429-140">顯示所選取資料行的名稱。</span><span class="sxs-lookup"><span data-stu-id="44429-140">Displays the name of the selected column.</span></span> <span data-ttu-id="44429-141">如果您已選取 **(\*)** 來分析所有資料行，這個選項就是空白的。</span><span class="sxs-lookup"><span data-stu-id="44429-141">This option is blank if you have selected **(\*)** to profile all columns.</span></span> <span data-ttu-id="44429-142">此選項是唯讀的。</span><span class="sxs-lookup"><span data-stu-id="44429-142">This option is read-only.</span></span>  
  
 <span data-ttu-id="44429-143">**StringCompareOptions**</span><span class="sxs-lookup"><span data-stu-id="44429-143">**StringCompareOptions**</span></span>  
 <span data-ttu-id="44429-144">這個選項不會套用至資料行長度散發設定檔。</span><span class="sxs-lookup"><span data-stu-id="44429-144">This option does not apply to the Column Length Distribution Profile.</span></span>  
  
### <a name="general-options"></a><span data-ttu-id="44429-145">一般選項</span><span class="sxs-lookup"><span data-stu-id="44429-145">General Options</span></span>  
 <span data-ttu-id="44429-146">**RequestID**</span><span class="sxs-lookup"><span data-stu-id="44429-146">**RequestID**</span></span>  
 <span data-ttu-id="44429-147">輸入描述性名稱，以便識別這個設定檔要求。</span><span class="sxs-lookup"><span data-stu-id="44429-147">Type a descriptive name to identify this profile request.</span></span> <span data-ttu-id="44429-148">一般而言，您不需要變更自動產生的值。</span><span class="sxs-lookup"><span data-stu-id="44429-148">Typically, you do not have to change the autogenerated value.</span></span>  
  
### <a name="options"></a><span data-ttu-id="44429-149">選項。</span><span class="sxs-lookup"><span data-stu-id="44429-149">Options</span></span>  
 <span data-ttu-id="44429-150">**IgnoreLeadingSpaces**</span><span class="sxs-lookup"><span data-stu-id="44429-150">**IgnoreLeadingSpaces**</span></span>  
 <span data-ttu-id="44429-151">指出當設定檔比較字串值時是否要忽略開頭空白。</span><span class="sxs-lookup"><span data-stu-id="44429-151">Indicate whether to ignore leading spaces when the profile compares string values.</span></span> <span data-ttu-id="44429-152">此選項的預設值是 **[False]** 。</span><span class="sxs-lookup"><span data-stu-id="44429-152">The default value of this option is **False**.</span></span>  
  
 <span data-ttu-id="44429-153">**IgnoreTrailingSpaces**</span><span class="sxs-lookup"><span data-stu-id="44429-153">**IgnoreTrailingSpaces**</span></span>  
 <span data-ttu-id="44429-154">指出當設定檔比較字串值時是否要忽略尾端空白。</span><span class="sxs-lookup"><span data-stu-id="44429-154">Indicate whether to ignore trailing spaces when the profile compares string values.</span></span> <span data-ttu-id="44429-155">此選項的預設值是 **[True]** 。</span><span class="sxs-lookup"><span data-stu-id="44429-155">The default value of this option is **True**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44429-156">另請參閱</span><span class="sxs-lookup"><span data-stu-id="44429-156">See Also</span></span>  
 <span data-ttu-id="44429-157">[資料分析工作編輯器 &#40;一般頁面&#41;](../general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="44429-157">[Data Profiling Task Editor &#40;General Page&#41;](../general-page-of-integration-services-designers-options.md) </span></span>  
 [<span data-ttu-id="44429-158">單一資料表快速分析表單 &#40;資料分析工作&#41;</span><span class="sxs-lookup"><span data-stu-id="44429-158">Single Table Quick Profile Form &#40;Data Profiling Task&#41;</span></span>](single-table-quick-profile-form-data-profiling-task.md)  
  
  
