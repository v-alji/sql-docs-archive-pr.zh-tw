---
title: " (SSAS 表格式) 的計算 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 738816e3-0e1d-44a5-8d1b-81068dce8ac0
author: minewiskan
ms.author: owend
ms.openlocfilehash: 2da86ae5c5652c8b2614cae4bbb721802700d973
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594715"
---
# <a name="calculations-ssas-tabular"></a><span data-ttu-id="60d3d-102">計算 (SSAS 表格式)</span><span class="sxs-lookup"><span data-stu-id="60d3d-102">Calculations (SSAS Tabular)</span></span>
  <span data-ttu-id="60d3d-103">將資料匯入到模型之後，您可以新增計算以彙總、篩選、擴充、結合資料，以及保護資料安全。</span><span class="sxs-lookup"><span data-stu-id="60d3d-103">After you have imported data into your model, you can add calculations to aggregate, filter, extend, combine, and secure that data.</span></span> <span data-ttu-id="60d3d-104">表格式模型使用 Data Analysis Expression (DAX) 這個新的公式語言以建立自訂計算。</span><span class="sxs-lookup"><span data-stu-id="60d3d-104">Tabular models use Data Analysis Expressions (DAX), a formula language for creating custom calculations.</span></span> <span data-ttu-id="60d3d-105">在表格式模型中，您使用 DAX 公式建立的計算會用於 *「導出資料行」*(Calculated Column)、 *「量值」*(Measures) 和 *「資料列篩選」*(Row Filters)。</span><span class="sxs-lookup"><span data-stu-id="60d3d-105">In tabular models, the calculations you create by using DAX formulas are used in *Calculated Columns*, *Measures*, and *Row Filters*.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="60d3d-106">本節內容</span><span class="sxs-lookup"><span data-stu-id="60d3d-106">In This Section</span></span>  
  
|<span data-ttu-id="60d3d-107">主題</span><span class="sxs-lookup"><span data-stu-id="60d3d-107">Topic</span></span>|<span data-ttu-id="60d3d-108">描述</span><span class="sxs-lookup"><span data-stu-id="60d3d-108">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="60d3d-109">了解表格式模型中的 DAX &#40;SSAS 表格式&#41;</span><span class="sxs-lookup"><span data-stu-id="60d3d-109">Understanding DAX in Tabular Models &#40;SSAS Tabular&#41;</span></span>](understanding-dax-in-tabular-models-ssas-tabular.md)|<span data-ttu-id="60d3d-110">描述 Data Analysis Expressions (DAX) 公式語言，可用來在表格式模型中建立導出資料行、量值和資料列篩選的計算。</span><span class="sxs-lookup"><span data-stu-id="60d3d-110">Describes the Data Analysis Expressions (DAX) formula language used to create calculations for calculated columns, measures, and row filters in tabular models.</span></span>|  
|[<span data-ttu-id="60d3d-111">DirectQuery 模式中的公式相容性</span><span class="sxs-lookup"><span data-stu-id="60d3d-111">Formula Compatibility in DirectQuery Mode</span></span>](../dax-formula-compatibility-in-directquery-mode-ssas-2014.md)|<span data-ttu-id="60d3d-112">描述差異、列出 DirectQuery 模式不支援的函數，並且列出受支援但可能會傳回不同結果的函數。</span><span class="sxs-lookup"><span data-stu-id="60d3d-112">Describes the differences, lists the functions that are not supported in DirectQuery mode, and lists the functions that are supported but could return different results.</span></span>|  
|[<span data-ttu-id="60d3d-113">&#40;DAX&#41; 參考的資料分析運算式</span><span class="sxs-lookup"><span data-stu-id="60d3d-113">Data Analysis Expressions &#40;DAX&#41; Reference</span></span>](/dax/data-analysis-expressions-dax-reference)|<span data-ttu-id="60d3d-114">本節提供 DAX 語法、運算子和函數的詳細描述。</span><span class="sxs-lookup"><span data-stu-id="60d3d-114">This section provides detailed descriptions of DAX syntax, operators, and functions.</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="60d3d-115">本節中不提供建立計算的逐步工作。</span><span class="sxs-lookup"><span data-stu-id="60d3d-115">Step-by-step tasks for creating calculations are not provided in this section.</span></span> <span data-ttu-id="60d3d-116">由於計算是在導出資料行、量值和資料列篩選 (依角色) 中指定，因此在與這些功能相關的工作中，會提供建立 DAX 公式的指示。</span><span class="sxs-lookup"><span data-stu-id="60d3d-116">Because calculations are specified in calculated columns, measures, and row filters (in roles), instructions on where to create DAX formulas are provided in tasks related to those features.</span></span> <span data-ttu-id="60d3d-117">如需詳細資訊，請參閱[建立導出資料行 &#40;SSAS 表格式&#41;](ssas-calculated-columns-create-a-calculated-column.md)、[建立及管理量值 &#40;SSAS 表格式&#41;](measures-ssas-tabular.md) 和[建立及管理角色 &#40;SSAS 表格式&#41;](roles-ssas-tabular.md)。</span><span class="sxs-lookup"><span data-stu-id="60d3d-117">For more information, see [Create a Calculated Column &#40;SSAS Tabular&#41;](ssas-calculated-columns-create-a-calculated-column.md), [Create and Manage Measures &#40;SSAS Tabular&#41;](measures-ssas-tabular.md), and [Create and Manage Roles &#40;SSAS Tabular&#41;](roles-ssas-tabular.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="60d3d-118">DAX 也可以用來查詢表格式模型，因此，本節中的主題將特別著重在使用 DAX 公式建立計算。</span><span class="sxs-lookup"><span data-stu-id="60d3d-118">While DAX can also be used to query a tabular model, topics in this section focus specifically on using DAX formulas to create calculations.</span></span>  
  
  
