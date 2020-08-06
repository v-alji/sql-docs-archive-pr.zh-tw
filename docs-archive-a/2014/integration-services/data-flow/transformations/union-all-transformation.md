---
title: 聯集全部轉換 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.unionalltrans.f1
helpviewer_keywords:
- merging datasets [Integration Services]
- combining datasets
- Union All transformation
- datasets [Integration Services], merging
ms.assetid: 942e4b90-9c41-4e9c-a6f3-80b3afe57f2f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: eaaab1abf2587979e947cc1be24cbedf8f61b6e4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599087"
---
# <a name="union-all-transformation"></a><span data-ttu-id="c401d-102">聯集全部轉換</span><span class="sxs-lookup"><span data-stu-id="c401d-102">Union All Transformation</span></span>
  <span data-ttu-id="c401d-103">「聯集全部」轉換會將多項輸入結合至單一輸出。</span><span class="sxs-lookup"><span data-stu-id="c401d-103">The Union All transformation combines multiple inputs into one output.</span></span> <span data-ttu-id="c401d-104">例如，五個不同的「一般檔案」來源的輸出，可做為「聯集全部」轉換的輸入並組合成一個輸出。</span><span class="sxs-lookup"><span data-stu-id="c401d-104">For example, the outputs from five different Flat File sources can be inputs to the Union All transformation and combined into one output.</span></span>  
  
## <a name="inputs-and-outputs"></a><span data-ttu-id="c401d-105">輸入和輸出</span><span class="sxs-lookup"><span data-stu-id="c401d-105">Inputs and Outputs</span></span>  
 <span data-ttu-id="c401d-106">轉換輸入會逐一加入至轉換輸出；不會發生任何重新排列資料列的情形。</span><span class="sxs-lookup"><span data-stu-id="c401d-106">The transformation inputs are added to the transformation output one after the other; no reordering of rows occurs.</span></span> <span data-ttu-id="c401d-107">如果封裝需要經過排序的輸出，則您應使用「合併」轉換而非「聯集全部」轉換。</span><span class="sxs-lookup"><span data-stu-id="c401d-107">If the package requires a sorted output, you should use the Merge transformation instead of the Union All transformation.</span></span>  
  
 <span data-ttu-id="c401d-108">您連接到「聯集全部」轉換的第一個輸入，是轉換從中建立轉換輸出的輸入。</span><span class="sxs-lookup"><span data-stu-id="c401d-108">The first input that you connect to the Union All transformation is the input from which the transformation creates the transformation output.</span></span> <span data-ttu-id="c401d-109">您接著連接到轉換的輸入中的資料行，會對應至轉換輸出中的資料行。</span><span class="sxs-lookup"><span data-stu-id="c401d-109">The columns in the inputs you subsequently connect to the transformation are mapped to the columns in the transformation output.</span></span>  
  
 <span data-ttu-id="c401d-110">若要合併輸入，請將輸入中的資料行對應至輸出中的資料行。</span><span class="sxs-lookup"><span data-stu-id="c401d-110">To merge inputs, you map columns in the inputs to columns in the output.</span></span> <span data-ttu-id="c401d-111">您至少必須將一個輸入的資料行對應至各輸出資料行。</span><span class="sxs-lookup"><span data-stu-id="c401d-111">A column from at least one input must be mapped to each output column.</span></span> <span data-ttu-id="c401d-112">兩個資料行之間的對應，會要求資料行的中繼資料相符。</span><span class="sxs-lookup"><span data-stu-id="c401d-112">The mapping between two columns requires that the metadata of the columns match.</span></span> <span data-ttu-id="c401d-113">例如，對應的資料行必須擁有相同的資料類型。</span><span class="sxs-lookup"><span data-stu-id="c401d-113">For example, the mapped columns must have the same data type.</span></span>  
  
 <span data-ttu-id="c401d-114">如果對應的資料行包含字串資料，而輸出資料行的長度比輸入資料行短，則輸出資料行的長度會自動增加，以包含輸入資料行。</span><span class="sxs-lookup"><span data-stu-id="c401d-114">If the mapped columns contain string data and the output column is shorter in length than the input column, the output column is automatically increased in length to contain the input column.</span></span> <span data-ttu-id="c401d-115">未對應至輸出資料行的輸入資料行會在輸出資料行中設為 Null 值。</span><span class="sxs-lookup"><span data-stu-id="c401d-115">Input columns that are not mapped to output columns are set to null values in the output columns.</span></span>  
  
 <span data-ttu-id="c401d-116">此轉換有多個輸入和一個輸出。</span><span class="sxs-lookup"><span data-stu-id="c401d-116">This transformation has multiple inputs and one output.</span></span> <span data-ttu-id="c401d-117">它不支援錯誤輸出。</span><span class="sxs-lookup"><span data-stu-id="c401d-117">It does not support an error output.</span></span>  
  
## <a name="configuration-of-the-union-all-transformation"></a><span data-ttu-id="c401d-118">聯集全部轉換的組態</span><span class="sxs-lookup"><span data-stu-id="c401d-118">Configuration of the Union All Transformation</span></span>  
 <span data-ttu-id="c401d-119">您可以透過 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 設計師或以程式設計方式設定屬性。</span><span class="sxs-lookup"><span data-stu-id="c401d-119">You can set properties through [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="c401d-120">如需可在 [聯集全部轉換編輯器]\*\*\*\* 對話方塊中設定之屬性的詳細資訊，請參閱[聯集全部轉換編輯器](../../union-all-transformation-editor.md)。</span><span class="sxs-lookup"><span data-stu-id="c401d-120">For more information about the properties that you can set in the **Union All Transformation Editor** dialog box, see [Union All Transformation Editor](../../union-all-transformation-editor.md).</span></span>  
  
 <span data-ttu-id="c401d-121">如需可透過程式設計方式設定之屬性的詳細資訊，請參閱 [通用屬性](../../common-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="c401d-121">For more information about the properties that you can set programmatically, see [Common Properties](../../common-properties.md).</span></span>  
  
 <span data-ttu-id="c401d-122">如需有關如何設定屬性的詳細資訊，請按下列其中一個主題：</span><span class="sxs-lookup"><span data-stu-id="c401d-122">For more information about how to set properties, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="c401d-123">設定資料流程元件的屬性</span><span class="sxs-lookup"><span data-stu-id="c401d-123">Set the Properties of a Data Flow Component</span></span>](../set-the-properties-of-a-data-flow-component.md)  
  
## <a name="related-tasks"></a><span data-ttu-id="c401d-124">相關工作</span><span class="sxs-lookup"><span data-stu-id="c401d-124">Related Tasks</span></span>  
 [<span data-ttu-id="c401d-125">使用聯集全部轉換來合併資料</span><span class="sxs-lookup"><span data-stu-id="c401d-125">Merge Data by Using the Union All Transformation</span></span>](union-all-transformation.md)  
  
  
