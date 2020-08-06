---
title: 合併轉換 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.mergetrans.f1
helpviewer_keywords:
- merging datasets [Integration Services]
- merging data [Integration Services]
- Merge transformation
- combining datasets
- datasets [Integration Services], merging
ms.assetid: cff8690c-07ac-46a0-aab5-20bd4848c677
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7d1d35e92b5978016b6a53956e5b6f1f6642f5ee
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707694"
---
# <a name="merge-transformation"></a><span data-ttu-id="80256-102">合併轉換</span><span class="sxs-lookup"><span data-stu-id="80256-102">Merge Transformation</span></span>
  <span data-ttu-id="80256-103">「合併」轉換會將兩個已排序的資料集結合成單一資料集。</span><span class="sxs-lookup"><span data-stu-id="80256-103">The Merge transformation combines two sorted datasets into a single dataset.</span></span> <span data-ttu-id="80256-104">各資料集的資料列會根據其索引鍵資料行的值插入輸出中。</span><span class="sxs-lookup"><span data-stu-id="80256-104">The rows from each dataset are inserted into the output based on values in their key columns.</span></span>  
  
 <span data-ttu-id="80256-105">藉由在資料流程中加入「合併」轉換，即可執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="80256-105">By including the Merge transformation in a data flow, you can perform the following tasks:</span></span>  
  
-   <span data-ttu-id="80256-106">合併兩個資料來源的資料，例如資料表和檔案。</span><span class="sxs-lookup"><span data-stu-id="80256-106">Merge data from two data sources, such as tables and files.</span></span>  
  
-   <span data-ttu-id="80256-107">藉由建立巢狀「合併」轉換，建立複雜的資料集。</span><span class="sxs-lookup"><span data-stu-id="80256-107">Create complex datasets by nesting Merge transformations.</span></span>  
  
-   <span data-ttu-id="80256-108">更正資料中的錯誤之後重新合併資料列。</span><span class="sxs-lookup"><span data-stu-id="80256-108">Remerge rows after correcting errors in the data.</span></span>  
  
 <span data-ttu-id="80256-109">「合併」轉換與「聯集全部」轉換類似。</span><span class="sxs-lookup"><span data-stu-id="80256-109">The Merge transformation is similar to the Union All transformations.</span></span> <span data-ttu-id="80256-110">在下列情況中，請使用「聯集全部」轉換取代「合併」轉換：</span><span class="sxs-lookup"><span data-stu-id="80256-110">Use the Union All transformation instead of the Merge transformation in the following situations:</span></span>  
  
-   <span data-ttu-id="80256-111">轉換輸入未經排序時。</span><span class="sxs-lookup"><span data-stu-id="80256-111">The transformation inputs are not sorted.</span></span>  
  
-   <span data-ttu-id="80256-112">結合的輸出不需要經過排序時。</span><span class="sxs-lookup"><span data-stu-id="80256-112">The combined output does not need to be sorted.</span></span>  
  
-   <span data-ttu-id="80256-113">轉換擁有超過兩個輸入時。</span><span class="sxs-lookup"><span data-stu-id="80256-113">The transformation has more than two inputs.</span></span>  
  
## <a name="input-requirements"></a><span data-ttu-id="80256-114">輸入需求</span><span class="sxs-lookup"><span data-stu-id="80256-114">Input Requirements</span></span>  
 <span data-ttu-id="80256-115">合併轉換針對其輸入需要已排序的資料。</span><span class="sxs-lookup"><span data-stu-id="80256-115">The Merge Transformation requires sorted data for its inputs.</span></span> <span data-ttu-id="80256-116">如需這項重要需求的詳細資訊，請參閱 [排序合併和合併聯結轉換的資料](sort-data-for-the-merge-and-merge-join-transformations.md)。</span><span class="sxs-lookup"><span data-stu-id="80256-116">For more information about this important requirement, see [Sort Data for the Merge and Merge Join Transformations](sort-data-for-the-merge-and-merge-join-transformations.md).</span></span>  
  
 <span data-ttu-id="80256-117">「合併」轉換也需要其輸入的合併資料行擁有相符的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="80256-117">The Merge transformation also requires that the merged columns in its inputs have matching metadata.</span></span> <span data-ttu-id="80256-118">例如，您無法合併數值資料類型的資料行，與字元資料類型的資料行。</span><span class="sxs-lookup"><span data-stu-id="80256-118">For example, you cannot merge a column that has a numeric data type with a column that has a character data type.</span></span> <span data-ttu-id="80256-119">如果資料是字串資料類型，第二個輸入中的資料行長度就必須小於或等於與其合併之第一個輸入中的資料行長度。</span><span class="sxs-lookup"><span data-stu-id="80256-119">If the data has a string data type, the length of the column in the second input must be less than or equal to the length of the column in the first input with which it is merged.</span></span>  
  
 <span data-ttu-id="80256-120">在 [ [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 設計師] 中，「合併」轉換的使用者介面會自動對應擁有相同中繼資料的資料行。</span><span class="sxs-lookup"><span data-stu-id="80256-120">In the [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer, the user interface for the Merge transformation automatically maps columns that have the same metadata.</span></span> <span data-ttu-id="80256-121">您可接著手動對應其他擁有相容資料類型的資料行。</span><span class="sxs-lookup"><span data-stu-id="80256-121">You can then manually map other columns that have compatible data types.</span></span>  
  
 <span data-ttu-id="80256-122">這個轉換有兩個輸入與一個輸出。</span><span class="sxs-lookup"><span data-stu-id="80256-122">This transformation has two inputs and one output.</span></span> <span data-ttu-id="80256-123">它不支援錯誤輸出。</span><span class="sxs-lookup"><span data-stu-id="80256-123">It does not support an error output.</span></span>  
  
## <a name="configuration-of-the-merge-transformation"></a><span data-ttu-id="80256-124">合併轉換的組態</span><span class="sxs-lookup"><span data-stu-id="80256-124">Configuration of the Merge Transformation</span></span>  
 <span data-ttu-id="80256-125">您可以透過「 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 設計師」或以程式設計方式設定屬性。</span><span class="sxs-lookup"><span data-stu-id="80256-125">You can set properties through the [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="80256-126">如需可在 [合併轉換編輯器]\*\*\*\* 對話方塊中設定之屬性的詳細資訊，請參閱[合併轉換編輯器](../../merge-transformation-editor.md)。</span><span class="sxs-lookup"><span data-stu-id="80256-126">For more information about the properties that you can set in the **Merge Transformation Editor** dialog box, see [Merge Transformation Editor](../../merge-transformation-editor.md).</span></span>  
  
 <span data-ttu-id="80256-127">如需可以用程式設計的方式設定之屬性的詳細資訊，請按下列其中一個主題：</span><span class="sxs-lookup"><span data-stu-id="80256-127">For more information about the properties that you can programmatically, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="80256-128">Common Properties</span><span class="sxs-lookup"><span data-stu-id="80256-128">Common Properties</span></span>](../../common-properties.md)  
  
-   [<span data-ttu-id="80256-129">轉換自訂屬性</span><span class="sxs-lookup"><span data-stu-id="80256-129">Transformation Custom Properties</span></span>](transformation-custom-properties.md)  
  
## <a name="related-tasks"></a><span data-ttu-id="80256-130">相關工作</span><span class="sxs-lookup"><span data-stu-id="80256-130">Related Tasks</span></span>  
 <span data-ttu-id="80256-131">如需有關如何設定屬性的詳細資訊，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="80256-131">For details about how to set properties, see the following topics:</span></span>  
  
-   [<span data-ttu-id="80256-132">設定資料流程元件的屬性</span><span class="sxs-lookup"><span data-stu-id="80256-132">Set the Properties of a Data Flow Component</span></span>](../set-the-properties-of-a-data-flow-component.md)  
  
-   [<span data-ttu-id="80256-133">排序合併和合併聯結轉換的資料</span><span class="sxs-lookup"><span data-stu-id="80256-133">Sort Data for the Merge and Merge Join Transformations</span></span>](sort-data-for-the-merge-and-merge-join-transformations.md)  
  
## <a name="see-also"></a><span data-ttu-id="80256-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="80256-134">See Also</span></span>  
 <span data-ttu-id="80256-135">[合併聯結轉換](merge-join-transformation.md) </span><span class="sxs-lookup"><span data-stu-id="80256-135">[Merge Join Transformation](merge-join-transformation.md) </span></span>  
 <span data-ttu-id="80256-136">[聯集全部轉換](union-all-transformation.md) </span><span class="sxs-lookup"><span data-stu-id="80256-136">[Union All Transformation](union-all-transformation.md) </span></span>  
 <span data-ttu-id="80256-137">[資料流程](../data-flow.md) </span><span class="sxs-lookup"><span data-stu-id="80256-137">[Data Flow](../data-flow.md) </span></span>  
 [<span data-ttu-id="80256-138">Integration Services 轉換</span><span class="sxs-lookup"><span data-stu-id="80256-138">Integration Services Transformations</span></span>](integration-services-transformations.md)  
  
  
