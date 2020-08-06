---
title: 取消樞紐轉換 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.unpivottrans.f1
helpviewer_keywords:
- Unpivot transformation
- more normalized data set [Integration Services]
- normalized data [Integration Services]
- datasets [Integration Services], normalized data
ms.assetid: f635c64b-a9c5-4f11-9c40-9cd9d5298c5d
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e605dc4827a885b5dc65fbb680cce8a434b89fd5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599083"
---
# <a name="unpivot-transformation"></a><span data-ttu-id="77974-102">取消樞紐轉換</span><span class="sxs-lookup"><span data-stu-id="77974-102">Unpivot Transformation</span></span>
  <span data-ttu-id="77974-103">「取消樞紐」轉換可以使非正規化的資料集變成較正規化的版本，方法是將單一記錄中多個資料行的值擴充為單一資料行中具有同一值的多個記錄。</span><span class="sxs-lookup"><span data-stu-id="77974-103">The Unpivot transformation makes an unnormalized dataset into a more normalized version by expanding values from multiple columns in a single record into multiple records with the same values in a single column.</span></span> <span data-ttu-id="77974-104">例如，列出客戶名稱的資料集對每個客戶都具有一個資料列，同時產品及購買數量會顯示在資料列的資料行中。</span><span class="sxs-lookup"><span data-stu-id="77974-104">For example, a dataset that lists customer names has one row for each customer, with the products and the quantity purchased shown in columns in the row.</span></span> <span data-ttu-id="77974-105">當「取消樞紐」轉換將資料集正規化之後，資料集便會對客戶購買的每種產品包含不同的資料列。</span><span class="sxs-lookup"><span data-stu-id="77974-105">After the Unpivot transformation normalizes the data set, the data set contains a different row for each product that the customer purchased.</span></span>  
  
 <span data-ttu-id="77974-106">下圖顯示資料在 Product 資料行上取消樞紐之前的資料集。</span><span class="sxs-lookup"><span data-stu-id="77974-106">The following diagram shows a data set before the data is unpivoted on the Product column.</span></span>  
  
 <span data-ttu-id="77974-107">![取消樞紐之後的資料集](../../media/mw-dts-18.gif "取消樞紐之後的資料集")</span><span class="sxs-lookup"><span data-stu-id="77974-107">![Dataset after it is unpivoted](../../media/mw-dts-18.gif "Dataset after it is unpivoted")</span></span>  
  
 <span data-ttu-id="77974-108">下圖顯示在 Product 資料行上取消樞紐之後的資料集。</span><span class="sxs-lookup"><span data-stu-id="77974-108">The following diagram shows a data set after it has been unpivoted on the Product column.</span></span>  
  
 <span data-ttu-id="77974-109">![取消樞紐之前的資料集](../../media/mw-dts-17.gif "取消樞紐之前的資料集")</span><span class="sxs-lookup"><span data-stu-id="77974-109">![Dataset before it is unpivoted](../../media/mw-dts-17.gif "Dataset before it is unpivoted")</span></span>  
  
 <span data-ttu-id="77974-110">在某些情況下，取消樞紐結果可能會包含非預期之值的資料列。</span><span class="sxs-lookup"><span data-stu-id="77974-110">Under some circumstances, the unpivot results may contain rows with unexpected values.</span></span> <span data-ttu-id="77974-111">例如，如果圖表中顯示為要取消樞紐的範例資料中，Fred 的所有 Qty 資料行中都有 Null 值，那麼在輸出中只會包含一個 Fred 的資料列，而不是五個。</span><span class="sxs-lookup"><span data-stu-id="77974-111">For example, if the sample data to unpivot shown in the diagram had null values in all the Qty columns for Fred, then the output would include only one row for Fred, not five.</span></span> <span data-ttu-id="77974-112">視資料行資料類型而定，Qty 資料行可能包含 Null 或零。</span><span class="sxs-lookup"><span data-stu-id="77974-112">The Qty column would contain either null or zero, depending on the column data type.</span></span>  
  
## <a name="configuration-of-the-unpivot-transformation"></a><span data-ttu-id="77974-113">設定取消樞紐轉換</span><span class="sxs-lookup"><span data-stu-id="77974-113">Configuration of the Unpivot Transformation</span></span>  
 <span data-ttu-id="77974-114">取消樞紐轉換包括 `PivotKeyValue` 自訂屬性。</span><span class="sxs-lookup"><span data-stu-id="77974-114">The Unpivot transformation includes the `PivotKeyValue` custom property.</span></span> <span data-ttu-id="77974-115">屬性運算式可以在載入封裝時更新這個屬性。</span><span class="sxs-lookup"><span data-stu-id="77974-115">This property can be updated by a property expression when the package is loaded.</span></span> <span data-ttu-id="77974-116">如需詳細資訊，請參閱 [Integration Services &#40;SSIS&#41; 運算式](../../expressions/integration-services-ssis-expressions.md)、[在封裝中使用屬性運算式](../../expressions/use-property-expressions-in-packages.md)和[轉換自訂屬性](transformation-custom-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="77974-116">For more information, see [Integration Services &#40;SSIS&#41; Expressions](../../expressions/integration-services-ssis-expressions.md), [Use Property Expressions in Packages](../../expressions/use-property-expressions-in-packages.md), and [Transformation Custom Properties](transformation-custom-properties.md).</span></span>  
  
 <span data-ttu-id="77974-117">此轉換有一個輸入和一個輸出。</span><span class="sxs-lookup"><span data-stu-id="77974-117">This transformation has one input and one output.</span></span> <span data-ttu-id="77974-118">但沒有錯誤輸出。</span><span class="sxs-lookup"><span data-stu-id="77974-118">It has no error output.</span></span>  
  
 <span data-ttu-id="77974-119">您可以透過 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 設計師或以程式設計方式設定屬性。</span><span class="sxs-lookup"><span data-stu-id="77974-119">You can set properties through [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="77974-120">如需可在 [取消樞紐轉換編輯器]\*\*\*\* 對話方塊中設定之屬性的詳細資訊，請按下列其中一個主題：</span><span class="sxs-lookup"><span data-stu-id="77974-120">For more information about the properties that you can set in the **Unpivot Transformation Editor** dialog box, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="77974-121">取消樞紐轉換編輯器</span><span class="sxs-lookup"><span data-stu-id="77974-121">Unpivot Transformation Editor</span></span>](../../unpivot-transformation-editor.md)  
  
 <span data-ttu-id="77974-122">如需有關可以在 **[進階編輯器]** 對話方塊中或以程式設計方式設定之屬性的詳細資訊，請按下列其中一個主題：</span><span class="sxs-lookup"><span data-stu-id="77974-122">For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="77974-123">Common Properties</span><span class="sxs-lookup"><span data-stu-id="77974-123">Common Properties</span></span>](../../common-properties.md)  
  
-   [<span data-ttu-id="77974-124">轉換自訂屬性</span><span class="sxs-lookup"><span data-stu-id="77974-124">Transformation Custom Properties</span></span>](transformation-custom-properties.md)  
  
 <span data-ttu-id="77974-125">如需如何設定屬性的詳細資訊，請參閱 [設定資料流程元件的屬性](../set-the-properties-of-a-data-flow-component.md)。</span><span class="sxs-lookup"><span data-stu-id="77974-125">For more information about how to set the properties, see [Set the Properties of a Data Flow Component](../set-the-properties-of-a-data-flow-component.md).</span></span>  
  
  
