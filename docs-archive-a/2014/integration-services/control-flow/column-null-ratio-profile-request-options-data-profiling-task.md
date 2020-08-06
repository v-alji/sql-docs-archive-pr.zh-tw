---
title: 資料行 Null 比例設定檔要求選項 (資料分析工作) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Data Profiling Task Editor
ms.assetid: 157ef8e4-fd23-4f81-8194-eebf74e9fd86
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 0e47c09a9a19eae4aed21c0c518430bc19a45648
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595236"
---
# <a name="column-null-ratio-profile-request-options-data-profiling-task"></a><span data-ttu-id="a900f-102">資料行 Null 比例設定檔要求選項 (資料分析工作)</span><span class="sxs-lookup"><span data-stu-id="a900f-102">Column Null Ratio Profile Request Options (Data Profiling Task)</span></span>
  <span data-ttu-id="a900f-103">您可以使用 **[設定檔要求]** 頁面的 **[要求屬性]** 窗格，針對要求窗格中選取的 **[資料行 Null 比例要求]** 設定選項。</span><span class="sxs-lookup"><span data-stu-id="a900f-103">Use the **Request Properties** pane of the **Profile Requests** page to set the options for the **Column Null Ratio Request** selected in the requests pane.</span></span> <span data-ttu-id="a900f-104">資料行 Null 比例設定檔會報告選取之資料行中 Null 值的百分比。</span><span class="sxs-lookup"><span data-stu-id="a900f-104">A Column Null Ratio profile reports the percentage of null values in the selected column.</span></span> <span data-ttu-id="a900f-105">這個設定檔可協助您識別資料中的問題，例如某個資料行中 Null 值的比例過高。</span><span class="sxs-lookup"><span data-stu-id="a900f-105">This profile can help you identify problems in your data such as an unexpectedly high ratio of null values in a column.</span></span> <span data-ttu-id="a900f-106">舉例來說，資料行 Null 比例設定檔可能會分析「郵遞區號」資料行並發現遺漏郵遞區號的百分比過高。</span><span class="sxs-lookup"><span data-stu-id="a900f-106">For example, a Column Null Ratio profile can profile a ZIP Code/Postal Code column and discover an unacceptably high percentage of missing postal codes.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a900f-107">本主題所描述的選項會顯示在 **[資料分析工作編輯器]** 的 **[設定檔要求]** 頁面上。</span><span class="sxs-lookup"><span data-stu-id="a900f-107">The options described in this topic appear on the **Profile Requests page** of the **Data Profiling Task Editor**.</span></span> <span data-ttu-id="a900f-108">如需此編輯器頁面的詳細資訊，請參閱[資料分析工作編輯器 &#40;設定檔要求頁面&#41;](data-profiling-task-editor-profile-requests-page.md)。</span><span class="sxs-lookup"><span data-stu-id="a900f-108">For more information about this page of the editor, see [Data Profiling Task Editor &#40;Profile Requests Page&#41;](data-profiling-task-editor-profile-requests-page.md).</span></span>  
  
 <span data-ttu-id="a900f-109">如需如何使用資料分析工作的詳細資訊，請參閱 [資料分析工作的設定](data-profiling-task.md)。</span><span class="sxs-lookup"><span data-stu-id="a900f-109">For more information about how to use the Data Profiling Task, see [Setup of the Data Profiling Task](data-profiling-task.md).</span></span> <span data-ttu-id="a900f-110">如需如何使用資料設定檔檢視器來分析資料分析工作輸出的詳細資訊，請參閱 [資料設定檔檢視器](data-profile-viewer.md)。</span><span class="sxs-lookup"><span data-stu-id="a900f-110">For more information about how to use the Data Profile Viewer to analyze the output of the Data Profiling Task, see [Data Profile Viewer](data-profile-viewer.md).</span></span>  
  
## <a name="request-properties-options"></a><span data-ttu-id="a900f-111">要求屬性選項</span><span class="sxs-lookup"><span data-stu-id="a900f-111">Request Properties Options</span></span>  
 <span data-ttu-id="a900f-112">**[要求屬性]** 窗格會針對 **[資料行 Null 比例要求]** 顯示下列選項群組：</span><span class="sxs-lookup"><span data-stu-id="a900f-112">For a **Column Null Ratio Request**, the **Request Properties** pane displays the following groups of options:</span></span>  
  
-   <span data-ttu-id="a900f-113">**[資料]** ，其中包括 **[TableOrView]** 和 **[資料行]** 選項。</span><span class="sxs-lookup"><span data-stu-id="a900f-113">**Data**, which includes the **TableOrView** and **Column** options</span></span>  
  
-   <span data-ttu-id="a900f-114">**一般**</span><span class="sxs-lookup"><span data-stu-id="a900f-114">**General**</span></span>  
  
### <a name="data-options"></a><span data-ttu-id="a900f-115">資料選項</span><span class="sxs-lookup"><span data-stu-id="a900f-115">Data Options</span></span>  
 <span data-ttu-id="a900f-116">**ConnectionManager**</span><span class="sxs-lookup"><span data-stu-id="a900f-116">**ConnectionManager**</span></span>  
 <span data-ttu-id="a900f-117">選取現有的 [!INCLUDE[vstecado](../../includes/vstecado-md.md)] 連線管理員，以便使用 .NET Data Provider for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (SqlClient) 來連接至包含要分析之資料表或檢視表的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫。</span><span class="sxs-lookup"><span data-stu-id="a900f-117">Select the existing [!INCLUDE[vstecado](../../includes/vstecado-md.md)] connection manager that uses the.NET Data Provider for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (SqlClient) to connect to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database that contains the table or view to be profiled.</span></span>  
  
 <span data-ttu-id="a900f-118">**[TableOrView]**</span><span class="sxs-lookup"><span data-stu-id="a900f-118">**TableOrView**</span></span>  
 <span data-ttu-id="a900f-119">選取包含要分析之資料行的資料表或檢視表。</span><span class="sxs-lookup"><span data-stu-id="a900f-119">Select the existing table or view that contains the column to be profiled.</span></span>  
  
 <span data-ttu-id="a900f-120">如需詳細資訊，請參閱本主題中的「TableorView 選項」一節。</span><span class="sxs-lookup"><span data-stu-id="a900f-120">For more information, see the section, "TableorView Options," in this topic.</span></span>  
  
 <span data-ttu-id="a900f-121">**資料行**</span><span class="sxs-lookup"><span data-stu-id="a900f-121">**Column**</span></span>  
 <span data-ttu-id="a900f-122">選取要分析的現有資料行。</span><span class="sxs-lookup"><span data-stu-id="a900f-122">Select the existing column to be profiled.</span></span> <span data-ttu-id="a900f-123">您可以選取 **(\*)** 來分析所有資料行。</span><span class="sxs-lookup"><span data-stu-id="a900f-123">Select **(\*)** to profile all columns.</span></span>  
  
 <span data-ttu-id="a900f-124">如需詳細資訊，請參閱本主題中的「資料行選項」一節。</span><span class="sxs-lookup"><span data-stu-id="a900f-124">For more information, see the section, "Column Options," in this topic.</span></span>  
  
#### <a name="tableorview-options"></a><span data-ttu-id="a900f-125">TableOrView 選項</span><span class="sxs-lookup"><span data-stu-id="a900f-125">TableOrView Options</span></span>  
 <span data-ttu-id="a900f-126">**結構描述**</span><span class="sxs-lookup"><span data-stu-id="a900f-126">**Schema**</span></span>  
 <span data-ttu-id="a900f-127">指定選取之資料表所屬的結構描述。</span><span class="sxs-lookup"><span data-stu-id="a900f-127">Specifies the schema to which the selected table belongs.</span></span> <span data-ttu-id="a900f-128">此選項是唯讀的。</span><span class="sxs-lookup"><span data-stu-id="a900f-128">This option is read-only.</span></span>  
  
 <span data-ttu-id="a900f-129">**Table**</span><span class="sxs-lookup"><span data-stu-id="a900f-129">**Table**</span></span>  
 <span data-ttu-id="a900f-130">顯示選取之資料表的名稱。</span><span class="sxs-lookup"><span data-stu-id="a900f-130">Displays the name of the selected table.</span></span> <span data-ttu-id="a900f-131">此選項是唯讀的。</span><span class="sxs-lookup"><span data-stu-id="a900f-131">This option is read-only.</span></span>  
  
#### <a name="column-options"></a><span data-ttu-id="a900f-132">資料行選項</span><span class="sxs-lookup"><span data-stu-id="a900f-132">Column Options</span></span>  
 <span data-ttu-id="a900f-133">**IsWildCard**</span><span class="sxs-lookup"><span data-stu-id="a900f-133">**IsWildCard**</span></span>  
 <span data-ttu-id="a900f-134">指定是否已經選取 **(\*)** 萬用字元。</span><span class="sxs-lookup"><span data-stu-id="a900f-134">Specifies whether the **(\*)** wildcard has been selected.</span></span> <span data-ttu-id="a900f-135">如果您已選取 **(\*)** 來分析所有資料行，這個選項會設定為 [True]。</span><span class="sxs-lookup"><span data-stu-id="a900f-135">This option is set to **True** if you have selected **(\*)** to profile all columns.</span></span> <span data-ttu-id="a900f-136">如果您已選取要分析的個別資料行，它就會設定為 **[False]** 。</span><span class="sxs-lookup"><span data-stu-id="a900f-136">It is **False** if you have selected an individual column to be profiled.</span></span> <span data-ttu-id="a900f-137">此選項是唯讀的。</span><span class="sxs-lookup"><span data-stu-id="a900f-137">This option is read-only.</span></span>  
  
 <span data-ttu-id="a900f-138">**ColumnName**</span><span class="sxs-lookup"><span data-stu-id="a900f-138">**ColumnName**</span></span>  
 <span data-ttu-id="a900f-139">顯示所選取資料行的名稱。</span><span class="sxs-lookup"><span data-stu-id="a900f-139">Displays the name of the selected column.</span></span> <span data-ttu-id="a900f-140">如果您已選取 **(\*)** 來分析所有資料行，這個選項就是空白的。</span><span class="sxs-lookup"><span data-stu-id="a900f-140">This option is blank if you have selected **(\*)** to profile all columns.</span></span> <span data-ttu-id="a900f-141">此選項是唯讀的。</span><span class="sxs-lookup"><span data-stu-id="a900f-141">This option is read-only.</span></span>  
  
 <span data-ttu-id="a900f-142">**StringCompareOptions**</span><span class="sxs-lookup"><span data-stu-id="a900f-142">**StringCompareOptions**</span></span>  
 <span data-ttu-id="a900f-143">這個選項不會套用至資料行 Null 比例設定檔。</span><span class="sxs-lookup"><span data-stu-id="a900f-143">This option does not apply to the Column Null Ratio Profile.</span></span>  
  
### <a name="general-options"></a><span data-ttu-id="a900f-144">一般選項</span><span class="sxs-lookup"><span data-stu-id="a900f-144">General Options</span></span>  
 <span data-ttu-id="a900f-145">**RequestID**</span><span class="sxs-lookup"><span data-stu-id="a900f-145">**RequestID**</span></span>  
 <span data-ttu-id="a900f-146">輸入描述性名稱，以便識別這個設定檔要求。</span><span class="sxs-lookup"><span data-stu-id="a900f-146">Type a descriptive name to identify this profile request.</span></span> <span data-ttu-id="a900f-147">一般而言，您不需要變更自動產生的值。</span><span class="sxs-lookup"><span data-stu-id="a900f-147">Typically, you do not have to change the autogenerated value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a900f-148">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a900f-148">See Also</span></span>  
 <span data-ttu-id="a900f-149">[資料分析工作編輯器 &#40;一般頁面&#41;](../general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="a900f-149">[Data Profiling Task Editor &#40;General Page&#41;](../general-page-of-integration-services-designers-options.md) </span></span>  
 [<span data-ttu-id="a900f-150">單一資料表快速分析表單 &#40;資料分析工作&#41;</span><span class="sxs-lookup"><span data-stu-id="a900f-150">Single Table Quick Profile Form &#40;Data Profiling Task&#41;</span></span>](single-table-quick-profile-form-data-profiling-task.md)  
  
  
