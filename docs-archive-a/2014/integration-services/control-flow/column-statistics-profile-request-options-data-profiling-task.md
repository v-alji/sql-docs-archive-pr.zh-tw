---
title: 資料行統計資料設定檔要求選項 (資料分析工作) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Data Profiling Task Editor
ms.assetid: 87205984-507a-49f3-b27c-36a0075c234d
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 9ce5c062a12e38d147f3cef95ea09b4c80f7c256
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595233"
---
# <a name="column-statistics-profile-request-options-data-profiling-task"></a><span data-ttu-id="ec799-102">資料行統計資料設定檔要求選項 (資料分析工作)</span><span class="sxs-lookup"><span data-stu-id="ec799-102">Column Statistics Profile Request Options (Data Profiling Task)</span></span>
  <span data-ttu-id="ec799-103">您可以使用 [設定檔要求]  頁面的 [要求屬性]  窗格，針對要求窗格中選取的 [資料行統計資料設定檔要求]  設定選項。</span><span class="sxs-lookup"><span data-stu-id="ec799-103">Use the **Request Properties** pane of the **Profile Requests** page to set the options for the **Column Statistics Profile Request** selected in the requests pane.</span></span> <span data-ttu-id="ec799-104">資料行統計資料設定檔會報告數值資料行的最小值、最大值、平均和標準差，以及 `datetime` 資料行的最小值和最大值等統計資料。</span><span class="sxs-lookup"><span data-stu-id="ec799-104">A Column Statistics profile reports statistics such as minimum, maximum, average, and standard deviation for numeric columns, and minimum and maximum for `datetime` columns.</span></span> <span data-ttu-id="ec799-105">這個設定檔可協助您識別資料中的問題，例如無效的日期。</span><span class="sxs-lookup"><span data-stu-id="ec799-105">This profile can help you identify problems in your data such as invalid dates.</span></span> <span data-ttu-id="ec799-106">舉例來說，您分析了歷程記錄日期的資料行，並發現屬於未來的最大日期。</span><span class="sxs-lookup"><span data-stu-id="ec799-106">For example, you profile a column of historical dates and discover a maximum date that is in the future.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ec799-107">本主題所描述的選項會顯示在 **[資料分析工作編輯器]** 的 **[設定檔要求]** 頁面上。</span><span class="sxs-lookup"><span data-stu-id="ec799-107">The options described in this topic appear on the **Profile Requests page** of the **Data Profiling Task Editor**.</span></span> <span data-ttu-id="ec799-108">如需此編輯器頁面的詳細資訊，請參閱[資料分析工作編輯器 &#40;設定檔要求頁面&#41;](data-profiling-task-editor-profile-requests-page.md)。</span><span class="sxs-lookup"><span data-stu-id="ec799-108">For more information about this page of the editor, see [Data Profiling Task Editor &#40;Profile Requests Page&#41;](data-profiling-task-editor-profile-requests-page.md).</span></span>  
  
 <span data-ttu-id="ec799-109">如需如何使用資料分析工作的詳細資訊，請參閱 [資料分析工作的設定](data-profiling-task.md)。</span><span class="sxs-lookup"><span data-stu-id="ec799-109">For more information about how to use the Data Profiling Task, see [Setup of the Data Profiling Task](data-profiling-task.md).</span></span> <span data-ttu-id="ec799-110">如需如何使用資料設定檔檢視器來分析資料分析工作輸出的詳細資訊，請參閱 [資料設定檔檢視器](data-profile-viewer.md)。</span><span class="sxs-lookup"><span data-stu-id="ec799-110">For more information about how to use the Data Profile Viewer to analyze the output of the Data Profiling Task, see [Data Profile Viewer](data-profile-viewer.md).</span></span>  
  
## <a name="request-properties-options"></a><span data-ttu-id="ec799-111">要求屬性選項</span><span class="sxs-lookup"><span data-stu-id="ec799-111">Request Properties Options</span></span>  
 <span data-ttu-id="ec799-112">[要求屬性]  窗格會針對 [資料行統計資料設定檔要求]  顯示下列選項群組：</span><span class="sxs-lookup"><span data-stu-id="ec799-112">For a **Column Statistics Profile Request**, the **Request Properties** pane displays the following groups of options:</span></span>  
  
-   <span data-ttu-id="ec799-113">**[資料]** ，其中包括 **[TableOrView]** 和 **[資料行]** 選項。</span><span class="sxs-lookup"><span data-stu-id="ec799-113">**Data**, which includes the **TableOrView** and **Column** options</span></span>  
  
-   <span data-ttu-id="ec799-114">**一般**</span><span class="sxs-lookup"><span data-stu-id="ec799-114">**General**</span></span>  
  
### <a name="data-options"></a><span data-ttu-id="ec799-115">資料選項</span><span class="sxs-lookup"><span data-stu-id="ec799-115">Data Options</span></span>  
 <span data-ttu-id="ec799-116">**ConnectionManager**</span><span class="sxs-lookup"><span data-stu-id="ec799-116">**ConnectionManager**</span></span>  
 <span data-ttu-id="ec799-117">選取現有的 [!INCLUDE[vstecado](../../includes/vstecado-md.md)] 連線管理員，以便使用 .NET Data Provider for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (SqlClient) 來連線至包含要分析之資料表或檢視表的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫。</span><span class="sxs-lookup"><span data-stu-id="ec799-117">Select the existing [!INCLUDE[vstecado](../../includes/vstecado-md.md)] connection manager that uses the .NET Data Provider for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (SqlClient) to connect to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database that contains the table or view to be profiled.</span></span>  
  
 <span data-ttu-id="ec799-118">**[TableOrView]**</span><span class="sxs-lookup"><span data-stu-id="ec799-118">**TableOrView**</span></span>  
 <span data-ttu-id="ec799-119">選取包含要分析之資料行的資料表或檢視表。</span><span class="sxs-lookup"><span data-stu-id="ec799-119">Select the existing table or view that contains the column to be profiled.</span></span>  
  
 <span data-ttu-id="ec799-120">如需詳細資訊，請參閱本主題中的「TableorView 選項」一節。</span><span class="sxs-lookup"><span data-stu-id="ec799-120">For more information, see the section, "TableorView Options," in this topic.</span></span>  
  
 <span data-ttu-id="ec799-121">**資料行**</span><span class="sxs-lookup"><span data-stu-id="ec799-121">**Column**</span></span>  
 <span data-ttu-id="ec799-122">選取要分析的現有資料行。</span><span class="sxs-lookup"><span data-stu-id="ec799-122">Select the existing column to be profiled.</span></span> <span data-ttu-id="ec799-123">您可以選取 **(\*)** 來分析所有資料行。</span><span class="sxs-lookup"><span data-stu-id="ec799-123">Select **(\*)** to profile all columns.</span></span>  
  
 <span data-ttu-id="ec799-124">如需詳細資訊，請參閱本主題中的「資料行選項」一節。</span><span class="sxs-lookup"><span data-stu-id="ec799-124">For more information, see the section, "Column Options," in this topic.</span></span>  
  
#### <a name="tableorview-options"></a><span data-ttu-id="ec799-125">TableOrView 選項</span><span class="sxs-lookup"><span data-stu-id="ec799-125">TableOrView Options</span></span>  
 <span data-ttu-id="ec799-126">**結構描述**</span><span class="sxs-lookup"><span data-stu-id="ec799-126">**Schema**</span></span>  
 <span data-ttu-id="ec799-127">指定選取之資料表所屬的結構描述。</span><span class="sxs-lookup"><span data-stu-id="ec799-127">Specifies the schema to which the selected table belongs.</span></span> <span data-ttu-id="ec799-128">此選項是唯讀的。</span><span class="sxs-lookup"><span data-stu-id="ec799-128">This option is read-only.</span></span>  
  
 <span data-ttu-id="ec799-129">**Table**</span><span class="sxs-lookup"><span data-stu-id="ec799-129">**Table**</span></span>  
 <span data-ttu-id="ec799-130">顯示選取之資料表的名稱。</span><span class="sxs-lookup"><span data-stu-id="ec799-130">Displays the name of the selected table.</span></span> <span data-ttu-id="ec799-131">此選項是唯讀的。</span><span class="sxs-lookup"><span data-stu-id="ec799-131">This option is read-only.</span></span>  
  
#### <a name="column-options"></a><span data-ttu-id="ec799-132">資料行選項</span><span class="sxs-lookup"><span data-stu-id="ec799-132">Column Options</span></span>  
 <span data-ttu-id="ec799-133">**IsWildCard**</span><span class="sxs-lookup"><span data-stu-id="ec799-133">**IsWildCard**</span></span>  
 <span data-ttu-id="ec799-134">指定是否已經選取 **(\*)** 萬用字元。</span><span class="sxs-lookup"><span data-stu-id="ec799-134">Specifies whether the **(\*)** wildcard has been selected.</span></span> <span data-ttu-id="ec799-135">如果您已選取 **(\*)** 來分析所有資料行，這個選項會設定為 [True]。</span><span class="sxs-lookup"><span data-stu-id="ec799-135">This option is set to **True** if you have selected **(\*)** to profile all columns.</span></span> <span data-ttu-id="ec799-136">如果您已選取要分析的個別資料行，它就會設定為 **[False]** 。</span><span class="sxs-lookup"><span data-stu-id="ec799-136">It is **False** if you have selected an individual column to be profiled.</span></span> <span data-ttu-id="ec799-137">此選項是唯讀的。</span><span class="sxs-lookup"><span data-stu-id="ec799-137">This option is read-only.</span></span>  
  
 <span data-ttu-id="ec799-138">**ColumnName**</span><span class="sxs-lookup"><span data-stu-id="ec799-138">**ColumnName**</span></span>  
 <span data-ttu-id="ec799-139">顯示所選取資料行的名稱。</span><span class="sxs-lookup"><span data-stu-id="ec799-139">Displays the name of the selected column.</span></span> <span data-ttu-id="ec799-140">如果您已選取 **(\*)** 來分析所有資料行，這個選項就是空白的。</span><span class="sxs-lookup"><span data-stu-id="ec799-140">This option is blank if you have selected **(\*)** to profile all columns.</span></span> <span data-ttu-id="ec799-141">此選項是唯讀的。</span><span class="sxs-lookup"><span data-stu-id="ec799-141">This option is read-only.</span></span>  
  
 <span data-ttu-id="ec799-142">**StringCompareOptions**</span><span class="sxs-lookup"><span data-stu-id="ec799-142">**StringCompareOptions**</span></span>  
 <span data-ttu-id="ec799-143">這個選項不會套用至資料行統計資料設定檔。</span><span class="sxs-lookup"><span data-stu-id="ec799-143">This option does not apply to the Column Statistics Profile.</span></span>  
  
### <a name="general-options"></a><span data-ttu-id="ec799-144">一般選項</span><span class="sxs-lookup"><span data-stu-id="ec799-144">General Options</span></span>  
 <span data-ttu-id="ec799-145">**RequestID**</span><span class="sxs-lookup"><span data-stu-id="ec799-145">**RequestID**</span></span>  
 <span data-ttu-id="ec799-146">輸入描述性名稱，以便識別這個設定檔要求。</span><span class="sxs-lookup"><span data-stu-id="ec799-146">Type a descriptive name to identify this profile request.</span></span> <span data-ttu-id="ec799-147">一般而言，您不需要變更自動產生的值。</span><span class="sxs-lookup"><span data-stu-id="ec799-147">Typically, you do not have to change the autogenerated value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec799-148">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ec799-148">See Also</span></span>  
 <span data-ttu-id="ec799-149">[資料分析工作編輯器 &#40;一般頁面&#41;](../general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="ec799-149">[Data Profiling Task Editor &#40;General Page&#41;](../general-page-of-integration-services-designers-options.md) </span></span>  
 [<span data-ttu-id="ec799-150">單一資料表快速分析表單 &#40;資料分析工作&#41;</span><span class="sxs-lookup"><span data-stu-id="ec799-150">Single Table Quick Profile Form &#40;Data Profiling Task&#41;</span></span>](single-table-quick-profile-form-data-profiling-task.md)  
  
  
