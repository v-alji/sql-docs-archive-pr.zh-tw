---
title: 資料集屬性對話方塊、欄位 |Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptdesigner.datasetproperties.fields.f1
- "10140"
ms.assetid: e1367556-736e-4a6b-b9e7-10432a3e50b5
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 1b9d315f85751c0f73896e809a522613fefece5e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592537"
---
# <a name="dataset-properties-dialog-box-fields"></a><span data-ttu-id="b683e-102">資料集屬性對話方塊、欄位</span><span class="sxs-lookup"><span data-stu-id="b683e-102">Dataset Properties Dialog Box, Fields</span></span>
  <span data-ttu-id="b683e-103">選取 **[資料集屬性]** 對話方塊上的 **[欄位]** ，即可變更報表資料集的欄位集合。</span><span class="sxs-lookup"><span data-stu-id="b683e-103">Select **Fields** on the **Dataset Properties** dialog box to change the field collection for the report dataset.</span></span> <span data-ttu-id="b683e-104">欄位清單會自動擴展，但您可以使用 **[欄位]** 來加入、編輯和刪除查詢與導出欄位。</span><span class="sxs-lookup"><span data-stu-id="b683e-104">The fields list is automatically populated, but you can use **Fields** to add, edit, and delete query and calculated fields.</span></span>  
  
## <a name="options"></a><span data-ttu-id="b683e-105">選項。</span><span class="sxs-lookup"><span data-stu-id="b683e-105">Options</span></span>  
 <span data-ttu-id="b683e-106">**加入**</span><span class="sxs-lookup"><span data-stu-id="b683e-106">**Add**</span></span>  
 <span data-ttu-id="b683e-107">將新的查詢欄位或導出欄位加入到資料集中。</span><span class="sxs-lookup"><span data-stu-id="b683e-107">Add a new query field or calculated field to the dataset.</span></span>  
  
 <span data-ttu-id="b683e-108">**刪除**</span><span class="sxs-lookup"><span data-stu-id="b683e-108">**Delete**</span></span>  
 <span data-ttu-id="b683e-109">從資料集中刪除選取的欄位。</span><span class="sxs-lookup"><span data-stu-id="b683e-109">Delete the selected field from the dataset.</span></span>  
  
 <span data-ttu-id="b683e-110">**功能變數名稱**</span><span class="sxs-lookup"><span data-stu-id="b683e-110">**Field Name**</span></span>  
 <span data-ttu-id="b683e-111">輸入欄位的名稱。</span><span class="sxs-lookup"><span data-stu-id="b683e-111">Type a name for the field.</span></span> <span data-ttu-id="b683e-112">此欄位在資料集內必須是唯一的。</span><span class="sxs-lookup"><span data-stu-id="b683e-112">The field must be unique within the dataset.</span></span> <span data-ttu-id="b683e-113">對於資料集查詢中每個現有的欄位，系統都會預先填入名稱。</span><span class="sxs-lookup"><span data-stu-id="b683e-113">For each existing field in the dataset query, the name is pre-populated.</span></span>  
  
 <span data-ttu-id="b683e-114">**欄位來源**</span><span class="sxs-lookup"><span data-stu-id="b683e-114">**Field Source**</span></span>  
 <span data-ttu-id="b683e-115">輸入欄位的值。</span><span class="sxs-lookup"><span data-stu-id="b683e-115">Enter a value for the field.</span></span>  
  
 <span data-ttu-id="b683e-116">對導出欄位而言，欄位來源必須是資料集查詢所擷取之現有欄位的名稱，或是您建立的運算式。</span><span class="sxs-lookup"><span data-stu-id="b683e-116">For a calculated field, the field source must be the name of an existing field retrieved by the dataset query, or an expression that you create.</span></span> <span data-ttu-id="b683e-117">例如，若要建立欄位來代表查詢欄位 Sales 之值的 10 倍，請使用運算式 `=10 * Fields!Sales.Value`。</span><span class="sxs-lookup"><span data-stu-id="b683e-117">For example, to create a field that represents 10 times the value in the query field Sales, use the expression `=10 * Fields!Sales.Value`.</span></span>  
  
 <span data-ttu-id="b683e-118">對查詢欄位而言，欄位來源必須是由資料集查詢所擷取之現有欄位的名稱。</span><span class="sxs-lookup"><span data-stu-id="b683e-118">For a query field, the field source must be the name of an existing field retrieved by the dataset query.</span></span>  
  
 <span data-ttu-id="b683e-119">**運算式 (fx)**</span><span class="sxs-lookup"><span data-stu-id="b683e-119">**Expression (fx)**</span></span>  
 <span data-ttu-id="b683e-120">為導出欄位加入或變更運算式。</span><span class="sxs-lookup"><span data-stu-id="b683e-120">Add or change an expression for the calculated field.</span></span> <span data-ttu-id="b683e-121">只有在您按一下 **[加入]** ，並選取 **[導出欄位]** 時，此按鈕才會出現。</span><span class="sxs-lookup"><span data-stu-id="b683e-121">This button only appears when you click **Add** and select **Calculated Field**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b683e-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b683e-122">See Also</span></span>  
 <span data-ttu-id="b683e-123">[資料集欄位集合 &#40;報表產生器及 SSRS&#41;](report-data/dataset-fields-collection-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="b683e-123">[Dataset Fields Collection &#40;Report Builder and SSRS&#41;](report-data/dataset-fields-collection-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="b683e-124">[將資料加入報表 &#40;報表產生器和 SSRS&#41;](report-data/report-datasets-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="b683e-124">[Add Data to a Report &#40;Report Builder and SSRS&#41;](report-data/report-datasets-ssrs.md) </span></span>  
 [<span data-ttu-id="b683e-125">運算式 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="b683e-125">Expressions &#40;Report Builder and SSRS&#41;</span></span>](report-design/expressions-report-builder-and-ssrs.md)  
  
  
