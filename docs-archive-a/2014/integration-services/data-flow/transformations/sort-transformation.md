---
title: 排序轉換 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.sorttrans.f1
helpviewer_keywords:
- Sort transformation
- descending sorts
- ascending sorts
- sorting data [Integration Services]
- multiple sorts
- duplicate data [Integration Services]
ms.assetid: 728c9351-84a8-4a89-be4d-d50d4adc04e0
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7039d02b6cc55355c3b27e5694474df4666570ef
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597234"
---
# <a name="sort-transformation"></a><span data-ttu-id="f1190-102">排序轉換</span><span class="sxs-lookup"><span data-stu-id="f1190-102">Sort Transformation</span></span>
  <span data-ttu-id="f1190-103">「排序」轉換會以遞增或遞減的順序排序輸入資料，並將排序的資料複製到轉換輸出。</span><span class="sxs-lookup"><span data-stu-id="f1190-103">The Sort transformation sorts input data in ascending or descending order and copies the sorted data to the transformation output.</span></span> <span data-ttu-id="f1190-104">您可以對輸入套用多項排序，而各項排序是由決定排序順序的數字識別。</span><span class="sxs-lookup"><span data-stu-id="f1190-104">You can apply multiple sorts to an input; each sort is identified by a numeral that determines the sort order.</span></span> <span data-ttu-id="f1190-105">數字最小的資料行會最先排序，接著是排序數字第二小的排序資料行，以此類推。</span><span class="sxs-lookup"><span data-stu-id="f1190-105">The column with the lowest number is sorted first, the sort column with the second lowest number is sorted next, and so on.</span></span> <span data-ttu-id="f1190-106">例如，如果名為 **CountryRegion** 的資料行排序順序為 1，且名為 **City** 的資料行排序順序為 2，則輸出會先按照 Country/Region 排序，然後才按照 City。</span><span class="sxs-lookup"><span data-stu-id="f1190-106">For example, if a column named **CountryRegion** has a sort order of 1 and a column named **City** has a sort order of 2, the output is sorted by country/region and then by city.</span></span> <span data-ttu-id="f1190-107">正數代表以遞增順序排序，負數則代表以遞減順序排序。</span><span class="sxs-lookup"><span data-stu-id="f1190-107">A positive number denotes that the sort is ascending, and a negative number denotes that the sort is descending.</span></span> <span data-ttu-id="f1190-108">未排序的資料行具有 0 的排序次序。</span><span class="sxs-lookup"><span data-stu-id="f1190-108">Columns that are not sorted have a sort order of 0.</span></span> <span data-ttu-id="f1190-109">未選取進行排序的資料行會與經過排序的資料行一起自動複製到轉換輸出。</span><span class="sxs-lookup"><span data-stu-id="f1190-109">Columns that are not selected for sorting are automatically copied to the transformation output together with the sorted columns.</span></span>  
  
 <span data-ttu-id="f1190-110">「排序」轉換包括一組比較選項，用來定義轉換處理資料行中字串資料的方式。</span><span class="sxs-lookup"><span data-stu-id="f1190-110">The Sort transformation includes a set of comparison options to define how the transformation handles the string data in a column.</span></span> <span data-ttu-id="f1190-111">如需詳細資訊，請參閱 [Comparing String Data](../comparing-string-data.md)。</span><span class="sxs-lookup"><span data-stu-id="f1190-111">For more information, see [Comparing String Data](../comparing-string-data.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f1190-112">「排序」轉換排序 GUID 時，與 ORDER BY 子句在 Transact-SQL 中排序的方式不同。</span><span class="sxs-lookup"><span data-stu-id="f1190-112">The Sort transformation does not sort GUIDs in the same order as the ORDER BY clause does in Transact-SQL.</span></span> <span data-ttu-id="f1190-113">「排序」轉換會排序以 A-F 開頭之 GUID 前，以 0-9 開頭的 GUID，而在 [!INCLUDE[ssDEnoversion](../../../includes/ssdenoversion-md.md)]中實作的 ORDER BY 子句則以不同的方式排序。</span><span class="sxs-lookup"><span data-stu-id="f1190-113">While the Sort transformation sorts GUIDs that start with 0-9 before GUIDs that start with A-F, the ORDER BY clause, as implemented in the [!INCLUDE[ssDEnoversion](../../../includes/ssdenoversion-md.md)], sorts them differently.</span></span> <span data-ttu-id="f1190-114">如需詳細資訊，請參閱 [ORDER BY 子句 &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-order-by-clause-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="f1190-114">For more information, see [ORDER BY Clause &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-order-by-clause-transact-sql).</span></span>  
  
 <span data-ttu-id="f1190-115">「排序」轉換亦可在執行排序時移除重複的資料列。</span><span class="sxs-lookup"><span data-stu-id="f1190-115">The Sort transformation can also remove duplicate rows as part of its sort.</span></span> <span data-ttu-id="f1190-116">重複的資料列為擁有相同排序索引鍵值的資料列。</span><span class="sxs-lookup"><span data-stu-id="f1190-116">Duplicate rows are rows with the same sort key values.</span></span> <span data-ttu-id="f1190-117">排序索引鍵值是根據使用的字串比較選項所產生，也就是說，不同的常值字串可能擁有相同的排序索引鍵值。</span><span class="sxs-lookup"><span data-stu-id="f1190-117">The sort key value is generated based on the string comparison options being used, which means that different literal strings may have the same sort key values.</span></span> <span data-ttu-id="f1190-118">轉換會將輸入資料行中，擁有不同值但排序索引鍵相同的資料列視為重複。</span><span class="sxs-lookup"><span data-stu-id="f1190-118">The transformation identifies rows in the input columns that have different values but the same sort key as duplicates.</span></span>  
  
 <span data-ttu-id="f1190-119">排序轉換包括 `MaximumThreads` 自訂屬性；屬性運算式可以在載入封裝時更新這個屬性。</span><span class="sxs-lookup"><span data-stu-id="f1190-119">The Sort transformation includes the `MaximumThreads` custom property that can be updated by a property expression when the package is loaded.</span></span> <span data-ttu-id="f1190-120">如需詳細資訊，請參閱 [Integration Services &#40;SSIS&#41; 運算式](../../expressions/integration-services-ssis-expressions.md)、[在封裝中使用屬性運算式](../../expressions/use-property-expressions-in-packages.md)和[轉換自訂屬性](transformation-custom-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="f1190-120">For more information, see [Integration Services &#40;SSIS&#41; Expressions](../../expressions/integration-services-ssis-expressions.md), [Use Property Expressions in Packages](../../expressions/use-property-expressions-in-packages.md), and [Transformation Custom Properties](transformation-custom-properties.md).</span></span>  
  
 <span data-ttu-id="f1190-121">此轉換有一個輸入和一個輸出。</span><span class="sxs-lookup"><span data-stu-id="f1190-121">This transformation has one input and one output.</span></span> <span data-ttu-id="f1190-122">但它不支援錯誤輸出。</span><span class="sxs-lookup"><span data-stu-id="f1190-122">It does not support error outputs.</span></span>  
  
## <a name="configuration-of-the-sort-transformation"></a><span data-ttu-id="f1190-123">設定排序轉換</span><span class="sxs-lookup"><span data-stu-id="f1190-123">Configuration of the Sort Transformation</span></span>  
 <span data-ttu-id="f1190-124">您可以透過「 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 設計師」或以程式設計方式設定屬性。</span><span class="sxs-lookup"><span data-stu-id="f1190-124">You can set properties through the [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="f1190-125">如需有關 **[排序轉換編輯器]** 對話方塊中可設定屬性的詳細資訊，請參閱＜ [Sort Transformation Editor](../../sort-transformation-editor.md)＞。</span><span class="sxs-lookup"><span data-stu-id="f1190-125">For information about the properties that you can set in the **Sort Transformation Editor** dialog box, see [Sort Transformation Editor](../../sort-transformation-editor.md).</span></span>  
  
 <span data-ttu-id="f1190-126">**[進階編輯器]** 對話方塊會反映能以程式設計的方式設定之屬性。</span><span class="sxs-lookup"><span data-stu-id="f1190-126">The **Advanced Editor** dialog box reflects the properties that can be set programmatically.</span></span> <span data-ttu-id="f1190-127">如需有關可以在 **[進階編輯器]** 對話方塊中或以程式設計方式設定之屬性的詳細資訊，請按下列其中一個主題：</span><span class="sxs-lookup"><span data-stu-id="f1190-127">For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="f1190-128">Common Properties</span><span class="sxs-lookup"><span data-stu-id="f1190-128">Common Properties</span></span>](../../common-properties.md)  
  
-   [<span data-ttu-id="f1190-129">轉換自訂屬性</span><span class="sxs-lookup"><span data-stu-id="f1190-129">Transformation Custom Properties</span></span>](transformation-custom-properties.md)  
  
## <a name="related-tasks"></a><span data-ttu-id="f1190-130">相關工作</span><span class="sxs-lookup"><span data-stu-id="f1190-130">Related Tasks</span></span>  
 <span data-ttu-id="f1190-131">如需如何設定元件屬性的詳細資訊，請參閱 [設定資料流程元件的屬性](../set-the-properties-of-a-data-flow-component.md)。</span><span class="sxs-lookup"><span data-stu-id="f1190-131">For more information about how to set properties of the component, see [Set the Properties of a Data Flow Component](../set-the-properties-of-a-data-flow-component.md).</span></span>  
  
## <a name="related-content"></a><span data-ttu-id="f1190-132">相關內容</span><span class="sxs-lookup"><span data-stu-id="f1190-132">Related Content</span></span>  
 <span data-ttu-id="f1190-133">codeplex.com 上的範例： [SortDeDuplicateDelimitedString 自訂 SSIS 元件](https://go.microsoft.com/fwlink/?LinkId=220821)。</span><span class="sxs-lookup"><span data-stu-id="f1190-133">Sample, [SortDeDuplicateDelimitedString Custom SSIS Component](https://go.microsoft.com/fwlink/?LinkId=220821), on codeplex.com.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1190-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f1190-134">See Also</span></span>  
 <span data-ttu-id="f1190-135">[資料流程](../data-flow.md) </span><span class="sxs-lookup"><span data-stu-id="f1190-135">[Data Flow](../data-flow.md) </span></span>  
 [<span data-ttu-id="f1190-136">Integration Services 轉換</span><span class="sxs-lookup"><span data-stu-id="f1190-136">Integration Services Transformations</span></span>](integration-services-transformations.md)  
  
  
