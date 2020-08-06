---
title: 資料集屬性對話方塊、欄位 (報表產生器) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10021"
ms.assetid: 75c7e54a-3d20-4c9a-88da-ab36dce2ce42
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 2b766aa23cce390bc3ffdcf10efdb38efc91f3e9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592538"
---
# <a name="dataset-properties-dialog-box-fields-report-builder"></a><span data-ttu-id="37dbc-102">資料集屬性對話方塊、欄位 (報表產生器)</span><span class="sxs-lookup"><span data-stu-id="37dbc-102">Dataset Properties Dialog Box, Fields (Report Builder)</span></span>
  <span data-ttu-id="37dbc-103">選取 **[資料集屬性]** 對話方塊上的 **[欄位]** ，即可變更報表資料集的欄位集合。</span><span class="sxs-lookup"><span data-stu-id="37dbc-103">Select **Fields** on the **Dataset Properties** dialog box to change the field collection for the report dataset.</span></span> <span data-ttu-id="37dbc-104">欄位清單會自動擴展，但您可以使用 **[欄位]** 來加入、編輯和刪除查詢與導出欄位。</span><span class="sxs-lookup"><span data-stu-id="37dbc-104">The fields list is automatically populated, but you can use **Fields** to add, edit, and delete query and calculated fields.</span></span>  
  
 <span data-ttu-id="37dbc-105">只有在內嵌資料集上才支援導出欄位。</span><span class="sxs-lookup"><span data-stu-id="37dbc-105">Calculated fields are supported only on embedded datasets.</span></span> <span data-ttu-id="37dbc-106">如需詳細資訊，請參閱 [報表內嵌資料集和共用資料集 &#40;報表產生器及 SSRS&#41;](report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="37dbc-106">For more information, see [Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;](report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="37dbc-107">選項。</span><span class="sxs-lookup"><span data-stu-id="37dbc-107">Options</span></span>  
 <span data-ttu-id="37dbc-108">**加入**</span><span class="sxs-lookup"><span data-stu-id="37dbc-108">**Add**</span></span>  
 <span data-ttu-id="37dbc-109">將新的查詢或導出欄位加入到資料集中。</span><span class="sxs-lookup"><span data-stu-id="37dbc-109">Add a new query or calculated field to the dataset.</span></span>  
  
 <span data-ttu-id="37dbc-110">**刪除**</span><span class="sxs-lookup"><span data-stu-id="37dbc-110">**Delete**</span></span>  
 <span data-ttu-id="37dbc-111">從資料集中刪除選取的欄位。</span><span class="sxs-lookup"><span data-stu-id="37dbc-111">Delete the selected field from the dataset.</span></span>  
  
 <span data-ttu-id="37dbc-112">**功能變數名稱**</span><span class="sxs-lookup"><span data-stu-id="37dbc-112">**Field Name**</span></span>  
 <span data-ttu-id="37dbc-113">輸入欄位的名稱。</span><span class="sxs-lookup"><span data-stu-id="37dbc-113">Type a name for the field.</span></span> <span data-ttu-id="37dbc-114">此欄位在資料集內必須是唯一的。</span><span class="sxs-lookup"><span data-stu-id="37dbc-114">The field must be unique within the dataset.</span></span> <span data-ttu-id="37dbc-115">對於資料集中每個現有的欄位，系統都會預先填入名稱。</span><span class="sxs-lookup"><span data-stu-id="37dbc-115">For each existing field in the dataset, the name is pre-populated.</span></span>  
  
 <span data-ttu-id="37dbc-116">**欄位來源**</span><span class="sxs-lookup"><span data-stu-id="37dbc-116">**Field Source**</span></span>  
 <span data-ttu-id="37dbc-117">輸入欄位的值。</span><span class="sxs-lookup"><span data-stu-id="37dbc-117">Enter a value for the field.</span></span>  
  
 <span data-ttu-id="37dbc-118">對導出欄位而言，欄位來源必須是資料集查詢所擷取之現有欄位的名稱，或是您建立的運算式。</span><span class="sxs-lookup"><span data-stu-id="37dbc-118">For a calculated field, the field source must be the name of an existing field retrieved by the dataset query, or an expression that you create.</span></span> <span data-ttu-id="37dbc-119">例如，若要建立欄位來代表查詢欄位 Sales 之值的 10 倍，請使用運算式 `=10 * Fields!Sales.Value`。</span><span class="sxs-lookup"><span data-stu-id="37dbc-119">For example, to create a field that represents 10 times the value in the query field Sales, use the expression `=10 * Fields!Sales.Value`.</span></span>  
  
 <span data-ttu-id="37dbc-120">對查詢欄位而言，欄位來源必須是由資料集查詢所擷取之現有欄位的名稱。</span><span class="sxs-lookup"><span data-stu-id="37dbc-120">For a query field, the field source must be the name of an existing field retrieved by the dataset query.</span></span>  
  
 <span data-ttu-id="37dbc-121">**運算式 (fx)**</span><span class="sxs-lookup"><span data-stu-id="37dbc-121">**Expression (fx)**</span></span>  
 <span data-ttu-id="37dbc-122">為新的導出欄位加入或變更運算式。</span><span class="sxs-lookup"><span data-stu-id="37dbc-122">Add or change an expression for the new calculated field.</span></span> <span data-ttu-id="37dbc-123">只有在您按一下 **[加入]** ，並選取 **[導出欄位]** 時，此按鈕才會出現。</span><span class="sxs-lookup"><span data-stu-id="37dbc-123">This button only appears when you click **Add** and select **Calculated Field**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37dbc-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="37dbc-124">See Also</span></span>  
 <span data-ttu-id="37dbc-125">[資料集欄位集合 &#40;報表產生器及 SSRS&#41;](report-data/dataset-fields-collection-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="37dbc-125">[Dataset Fields Collection &#40;Report Builder and SSRS&#41;](report-data/dataset-fields-collection-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="37dbc-126">[建立共用資料集或內嵌資料集 &#40;報表產生器和 SSRS&#41;](report-data/create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="37dbc-126">[Create a Shared Dataset or Embedded Dataset &#40;Report Builder and SSRS&#41;](report-data/create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="37dbc-127">[對話方塊、窗格和嚮導的報表產生器說明](../../2014/reporting-services/report-builder-help-for-dialog-boxes-panes-and-wizards.md) </span><span class="sxs-lookup"><span data-stu-id="37dbc-127">[Report Builder Help for Dialog Boxes, Panes, and Wizards](../../2014/reporting-services/report-builder-help-for-dialog-boxes-panes-and-wizards.md) </span></span>  
 <span data-ttu-id="37dbc-128">[資料集屬性對話方塊、選項 &#40;報表產生器&#41;](report-data/dataset-properties-dialog-box-options-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="37dbc-128">[Dataset Properties Dialog Box, Options &#40;Report Builder&#41;](report-data/dataset-properties-dialog-box-options-report-builder.md) </span></span>  
 <span data-ttu-id="37dbc-129">[資料集屬性對話方塊、篩選 &#40;報表產生器&#41;](../../2014/reporting-services/dataset-properties-dialog-box-filters-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="37dbc-129">[Dataset Properties Dialog Box, Filters &#40;Report Builder&#41;](../../2014/reporting-services/dataset-properties-dialog-box-filters-report-builder.md) </span></span>  
 <span data-ttu-id="37dbc-130">[資料集屬性對話方塊、參數 &#40;報表產生器&#41;](../../2014/reporting-services/dataset-properties-dialog-box-parameters-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="37dbc-130">[Dataset Properties Dialog Box, Parameters &#40;Report Builder&#41;](../../2014/reporting-services/dataset-properties-dialog-box-parameters-report-builder.md) </span></span>  
 <span data-ttu-id="37dbc-131">[資料集屬性對話方塊、查詢 &#40;報表產生器&#41;](report-data/dataset-properties-dialog-box-query-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="37dbc-131">[Dataset Properties Dialog Box, Query &#40;Report Builder&#41;](report-data/dataset-properties-dialog-box-query-report-builder.md) </span></span>  
 <span data-ttu-id="37dbc-132">[運算式 &#40;報表產生器及 SSRS&#41;](report-design/expressions-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="37dbc-132">[Expressions &#40;Report Builder and SSRS&#41;](report-design/expressions-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="37dbc-133">報表產生器中的資料連接、資料來源及連接字串</span><span class="sxs-lookup"><span data-stu-id="37dbc-133">Data Connections, Data Sources, and Connection Strings in Report Builder</span></span>](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-report-builder.md)  
  
  
