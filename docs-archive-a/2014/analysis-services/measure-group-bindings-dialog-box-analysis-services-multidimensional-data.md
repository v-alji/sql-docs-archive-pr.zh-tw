---
title: 量值群組系結對話方塊 (Analysis Services-多維度資料) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.dimensionusage.definerelationship.measuregroupbindings.f1
helpviewer_keywords:
- Measure Group Bindings dialog box
ms.assetid: ed642780-5350-438e-af73-b9ceab3f876d
author: minewiskan
ms.author: owend
ms.openlocfilehash: 78693901a5898b140d6efeed16b6f0eaa7577e69
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708825"
---
# <a name="measure-group-bindings-dialog-box-analysis-services---multidimensional-data"></a><span data-ttu-id="4f279-102">量值群組繫結對話方塊 (Analysis Services - 多維度資料)</span><span class="sxs-lookup"><span data-stu-id="4f279-102">Measure Group Bindings Dialog Box (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="4f279-103">使用 [量值群組繫結]\*\*\*\* 對話方塊，即可針對一般維度關聯性，建立及修改 Cube 維度中之非資料粒度屬性，與量值群組中之資料行之間的直接關聯性；以及從 [定義關聯性]\*\*\*\* 對話方塊中，指定 Cube 維度中之任何屬性的 Null 處理選項。</span><span class="sxs-lookup"><span data-stu-id="4f279-103">Use the **Measure Group Bindings** dialog box to create and modify direct relationships between non-granularity attributes in a cube dimension and columns in a measure group for a regular dimension relationship, as well as to specify null processing options for any attribute in a cube dimension, from the **Define Relationship** dialog box.</span></span>  
  
## <a name="options"></a><span data-ttu-id="4f279-104">選項</span><span class="sxs-lookup"><span data-stu-id="4f279-104">Options</span></span>  
 <span data-ttu-id="4f279-105">**量值群組資料表**</span><span class="sxs-lookup"><span data-stu-id="4f279-105">**Measure group table**</span></span>  
 <span data-ttu-id="4f279-106">顯示所選取量值群組之事實資料表的名稱。</span><span class="sxs-lookup"><span data-stu-id="4f279-106">Displays the name of the fact table for the selected measure group.</span></span>  
  
 <span data-ttu-id="4f279-107">**屬性**</span><span class="sxs-lookup"><span data-stu-id="4f279-107">**Attributes**</span></span>  
 <span data-ttu-id="4f279-108">顯示屬性和維度資料表組成的方格。</span><span class="sxs-lookup"><span data-stu-id="4f279-108">Displays a grid of attributes and dimension tables.</span></span> <span data-ttu-id="4f279-109">選取屬性 (Attribute)，即可針對所選取的屬性 (Attribute) 建立或修改 **[關聯性]** 中的屬性 (Property)。</span><span class="sxs-lookup"><span data-stu-id="4f279-109">Select an attribute to create or modify properties in **Relationship** for the selected attribute.</span></span> <span data-ttu-id="4f279-110">方格包含下列資料行：</span><span class="sxs-lookup"><span data-stu-id="4f279-110">The grid contains the following columns:</span></span>  
  
|<span data-ttu-id="4f279-111">選項</span><span class="sxs-lookup"><span data-stu-id="4f279-111">Option</span></span>|<span data-ttu-id="4f279-112">定義</span><span class="sxs-lookup"><span data-stu-id="4f279-112">Definition</span></span>|  
|------------|----------------|  
|<span data-ttu-id="4f279-113">**屬性名稱**</span><span class="sxs-lookup"><span data-stu-id="4f279-113">**Attribute Name**</span></span>|<span data-ttu-id="4f279-114">顯示屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="4f279-114">Displays the name of the attribute.</span></span>|  
|<span data-ttu-id="4f279-115">**維度資料表**</span><span class="sxs-lookup"><span data-stu-id="4f279-115">**Dimension Table**</span></span>|<span data-ttu-id="4f279-116">顯示作為屬性基礎之維度資料表的名稱。</span><span class="sxs-lookup"><span data-stu-id="4f279-116">Displays the name of the dimension table on which the attribute is based.</span></span>|  
  
 <span data-ttu-id="4f279-117">**關聯性**</span><span class="sxs-lookup"><span data-stu-id="4f279-117">**Relationship**</span></span>  
 <span data-ttu-id="4f279-118">顯示由選取之屬性的維度資料表資料行，與選取之量值群組的事實資料表資料行之間的關聯性所組成的方格，以及關聯性的 Null 處理選項。</span><span class="sxs-lookup"><span data-stu-id="4f279-118">Displays a grid of relationships between dimension table columns for the selected attribute and fact table columns for the selected measure group as well as the null processing option for the relationship.</span></span> <span data-ttu-id="4f279-119">方格包含下列資料行：</span><span class="sxs-lookup"><span data-stu-id="4f279-119">The grid contains the following columns:</span></span>  
  
|<span data-ttu-id="4f279-120">選項</span><span class="sxs-lookup"><span data-stu-id="4f279-120">Option</span></span>|<span data-ttu-id="4f279-121">定義</span><span class="sxs-lookup"><span data-stu-id="4f279-121">Definition</span></span>|  
|------------|----------------|  
|<span data-ttu-id="4f279-122">**維度資料行**</span><span class="sxs-lookup"><span data-stu-id="4f279-122">**Dimension Columns**</span></span>|<span data-ttu-id="4f279-123">顯示來自維度資料表中，作為 **[屬性]** 中所選取屬性之基礎的資料行。</span><span class="sxs-lookup"><span data-stu-id="4f279-123">Displays the columns from the dimension table on which the attribute selected in **Attributes** is based.</span></span>|  
|<span data-ttu-id="4f279-124">**量值群組資料行**</span><span class="sxs-lookup"><span data-stu-id="4f279-124">**Measure Group Columns**</span></span>|<span data-ttu-id="4f279-125">選取 **[繼承自維度]** 即可使用繼承自維度的量值群組關聯性；或者從作為量值群組之基礎的事實資料表中選取資料行，即可明確地定義關聯性。</span><span class="sxs-lookup"><span data-stu-id="4f279-125">Select either **Inherited from dimension** to use the measure group relationship inherited from the dimension, or select a column from the fact table on which the measure group is based to explicitly define a relationship.</span></span>|  
|<span data-ttu-id="4f279-126">**Null 處理**</span><span class="sxs-lookup"><span data-stu-id="4f279-126">**Null Processing**</span></span>|<span data-ttu-id="4f279-127">為屬性選取 Null 處理選項。</span><span class="sxs-lookup"><span data-stu-id="4f279-127">Select a null processing option for the attribute.</span></span> <span data-ttu-id="4f279-128">如需 Null 處理選項的詳細資訊，請參閱 [NullProcessing 元素 &#40;ASSL&#41;](https://docs.microsoft.com/bi-reference/assl/properties/nullprocessing-element-assl)。</span><span class="sxs-lookup"><span data-stu-id="4f279-128">For more information about null processing options, see [NullProcessing Element &#40;ASSL&#41;](https://docs.microsoft.com/bi-reference/assl/properties/nullprocessing-element-assl).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4f279-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4f279-129">See Also</span></span>  
 <span data-ttu-id="4f279-130">[[定義關聯性] 對話方塊 &#40;Analysis Services-多維度資料&#41;](define-relationship-dialog-box-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="4f279-130">[Define Relationship Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](define-relationship-dialog-box-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="4f279-131">Analysis Services 的設計工具和對話方塊 &#40;多維度資料&#41;</span><span class="sxs-lookup"><span data-stu-id="4f279-131">Analysis Services Designers and Dialog Boxes &#40;Multidimensional Data&#41;</span></span>](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)  
  
  
