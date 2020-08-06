---
title: 準備要在 Tablix 資料區中顯示的資料 (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: fbb00dc6-7887-480c-b771-cab6fecb8dcc
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 72ac150f2dcd227b1e3afb624a5ca5866fb4c360
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599355"
---
# <a name="preparing-data-for-display-in-a-tablix-data-region-report-builder-and-ssrs"></a><span data-ttu-id="c2ffc-102">準備要在 Tablix 資料區中顯示的資料 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="c2ffc-102">Preparing Data for Display in a Tablix Data Region (Report Builder and SSRS)</span></span>
  <span data-ttu-id="c2ffc-103">Tablix 資料區域會顯示資料集中的資料。</span><span class="sxs-lookup"><span data-stu-id="c2ffc-103">A tablix data region displays data from a dataset.</span></span> <span data-ttu-id="c2ffc-104">您可以檢視針對資料集擷取的所有資料，或者您可以建立篩選，讓您僅能看到資料的子集。</span><span class="sxs-lookup"><span data-stu-id="c2ffc-104">You can view all the data retrieved for the dataset or you can create filters so that you see only a subset of the data.</span></span> <span data-ttu-id="c2ffc-105">您也可以加入條件式運算式來填入 Null 值，或修改資料集的查詢來包含定義現有資料行之排序次序的資料行。</span><span class="sxs-lookup"><span data-stu-id="c2ffc-105">You can also add conditional expressions to fill in null values or modify the query for a dataset to include columns that define the sort order for an existing column.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="working-with-nulls-and-blanks-in-field-values"></a><span data-ttu-id="c2ffc-106">在欄位值中使用 Null 和空白</span><span class="sxs-lookup"><span data-stu-id="c2ffc-106">Working with Nulls and Blanks in Field Values</span></span>  
 <span data-ttu-id="c2ffc-107">資料集中欄位集合的資料包含在執行階段從資料來源擷取的所有值，包括 Null 值和空白。</span><span class="sxs-lookup"><span data-stu-id="c2ffc-107">Data for the field collection in a dataset includes all values retrieved from the data source at run time, including null values and blanks.</span></span> <span data-ttu-id="c2ffc-108">Null 值和空白通常無法分辨。</span><span class="sxs-lookup"><span data-stu-id="c2ffc-108">Normally null values and blanks are indistinguishable.</span></span> <span data-ttu-id="c2ffc-109">在大部分的情況下，這是所要的行為。</span><span class="sxs-lookup"><span data-stu-id="c2ffc-109">In most cases, this is the desired behavior.</span></span> <span data-ttu-id="c2ffc-110">例如， [Sum](report-builder-functions-sum-function.md) 和 [Avg](report-builder-functions-avg-function.md) 之類的數值彙總函式會忽略 Null 值。</span><span class="sxs-lookup"><span data-stu-id="c2ffc-110">For example, Numeric aggregate functions like [Sum](report-builder-functions-sum-function.md) and [Avg](report-builder-functions-avg-function.md) ignore null values.</span></span> <span data-ttu-id="c2ffc-111">如需詳細資訊，請參閱 [彙總函式參考 &#40;報表產生器和 SSRS&#41;](report-builder-functions-aggregate-functions-reference.md)。</span><span class="sxs-lookup"><span data-stu-id="c2ffc-111">For more information, see [Aggregate Functions Reference &#40;Report Builder and SSRS&#41;](report-builder-functions-aggregate-functions-reference.md).</span></span>  
  
 <span data-ttu-id="c2ffc-112">如果您不想要以不同的方式處理 Null 值，可以使用條件式運算式或自訂程式碼，將自訂值取代為 Null 值。</span><span class="sxs-lookup"><span data-stu-id="c2ffc-112">If you do want to handle null values differently, you can use conditional expressions or custom code to substitute a custom value for the null value.</span></span> <span data-ttu-id="c2ffc-113">例如，下列運算式會在 `Null` 欄位中出現 Null 值的每個位置，取代文字 `[Size]`。</span><span class="sxs-lookup"><span data-stu-id="c2ffc-113">For example, the following expression substitutes the text `Null` wherever a null value occurs in the field `[Size]`.</span></span>  
  
```  
=IIF(Fields!Size.Value IS NOTHING,"Null",Fields!Size.Value)  
```  
  
 <span data-ttu-id="c2ffc-114">如需有關使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 查詢從 [!INCLUDE[tsql](../../includes/tsql-md.md)] 資料來源擷取資料之前，排除資料中 Null 值的詳細資訊，請參閱《 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SQL Server 線上叢書 [》中](https://go.microsoft.com/fwlink/?linkid=120955)文件集的＜Null 值＞和＜Null 值與聯結＞。</span><span class="sxs-lookup"><span data-stu-id="c2ffc-114">For more information about eliminating nulls in your data before retrieving the data from a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data source using [!INCLUDE[tsql](../../includes/tsql-md.md)] queries, see "Null Values" and "Null Values and Joins" in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] documentation in [SQL Server Books Online](https://go.microsoft.com/fwlink/?linkid=120955).</span></span>  
  
## <a name="handling-null-field-names"></a><span data-ttu-id="c2ffc-115">處理 Null 欄位名稱</span><span class="sxs-lookup"><span data-stu-id="c2ffc-115">Handling Null Field Names</span></span>  
 <span data-ttu-id="c2ffc-116">只要欄位本身存在於查詢結果集中，就可以在運算式中測試 Null 值。</span><span class="sxs-lookup"><span data-stu-id="c2ffc-116">Testing for null values in an expression is fine as long as the field itself exists in the query result set.</span></span> <span data-ttu-id="c2ffc-117">您可以從自訂程式碼中，測試欄位本身是否出現在執行階段從資料來源傳回的集合欄位中。</span><span class="sxs-lookup"><span data-stu-id="c2ffc-117">From custom code, you can test whether the field itself is present in the collection fields returned from the data source at run time.</span></span> <span data-ttu-id="c2ffc-118">如需詳細資訊，請參閱[資料集 Fields 集合參考 &#40;報表產生器及 SSRS&#41;](built-in-collections-dataset-fields-collection-references-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="c2ffc-118">For more information, see [Dataset Fields Collection References &#40;Report Builder and SSRS&#41;](built-in-collections-dataset-fields-collection-references-report-builder.md).</span></span>  
  
## <a name="adding-a-sort-order-column"></a><span data-ttu-id="c2ffc-119">加入排序次序資料行</span><span class="sxs-lookup"><span data-stu-id="c2ffc-119">Adding a Sort Order Column</span></span>  
 <span data-ttu-id="c2ffc-120">根據預設，您可以依字母順序排序資料集欄位中的值。</span><span class="sxs-lookup"><span data-stu-id="c2ffc-120">By default, you can alphabetically sort values in a dataset field.</span></span> <span data-ttu-id="c2ffc-121">若要以不同的次序進行排序，您可以將新的資料行加入到資料集，定義您要在資料區域中使用的排序次序。</span><span class="sxs-lookup"><span data-stu-id="c2ffc-121">To sort in a different order, you can add a new column to your dataset that defines the sort order you want in a data region.</span></span> <span data-ttu-id="c2ffc-122">例如，若要先針對 `[Color]` 欄位進行排序並排序白色與黑色的項目，您可以加入 `[ColorSortOrder]`資料行，如以下查詢所示：</span><span class="sxs-lookup"><span data-stu-id="c2ffc-122">For example, to sort on the field `[Color]` and sort white and black items first, you can add a column `[ColorSortOrder]`, shown in the following query:</span></span>  
  
```  
SELECT ProductID, p.Name, Color,  
   CASE  
      WHEN p.Color = 'White' THEN 1  
      WHEN p.Color = 'Black' THEN 2  
      WHEN p.Color = 'Blue' THEN 3  
      WHEN p.Color = 'Yellow' THEN 4  
      ELSE 5  
   END As ColorSortOrder  
FROM Production.Product p  
```  
  
 <span data-ttu-id="c2ffc-123">若要根據此排序次序排序資料表資料區域，將詳細資料群組的排序運算式設定為 `=Fields!ColorSortOrder.Value`。</span><span class="sxs-lookup"><span data-stu-id="c2ffc-123">To sort a table data region according to this sort order, set the sort expression on the detail group to `=Fields!ColorSortOrder.Value`.</span></span> <span data-ttu-id="c2ffc-124">如需詳細資訊，請參閱[在資料區中排序資料 &#40;報表產生器及 SSRS&#41;](sort-data-in-a-data-region-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="c2ffc-124">For more information, see [Sort Data in a Data Region &#40;Report Builder and SSRS&#41;](sort-data-in-a-data-region-report-builder-and-ssrs.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2ffc-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c2ffc-125">See Also</span></span>  
 <span data-ttu-id="c2ffc-126">[資料集欄位集合 &#40;報表產生器及 SSRS&#41;](../report-data/dataset-fields-collection-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="c2ffc-126">[Dataset Fields Collection &#40;Report Builder and SSRS&#41;](../report-data/dataset-fields-collection-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="c2ffc-127">[運算式 &#40;報表產生器及 SSRS&#41;](expressions-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="c2ffc-127">[Expressions &#40;Report Builder and SSRS&#41;](expressions-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="c2ffc-128">篩選、分組和排序資料 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="c2ffc-128">Filter, Group, and Sort Data &#40;Report Builder and SSRS&#41;</span></span>](filter-group-and-sort-data-report-builder-and-ssrs.md)  
  
  
