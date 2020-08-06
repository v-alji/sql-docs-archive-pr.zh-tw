---
title: 合併聯結轉換編輯器 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.mergejointransformation.f1
helpviewer_keywords:
- Merge Join Transformation Editor
ms.assetid: ac06f419-30b3-42aa-8b34-42000bec4285
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e0d15d1233c2e0ff836e9dbd17459e56c48183f6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597206"
---
# <a name="merge-join-transformation-editor"></a><span data-ttu-id="74238-102">合併聯結轉換編輯器</span><span class="sxs-lookup"><span data-stu-id="74238-102">Merge Join Transformation Editor</span></span>
  <span data-ttu-id="74238-103">使用 [合併聯結轉換編輯器]  對話方塊，即可指定合併兩個由聯結組合之輸入的聯結類型、聯結資料行以及輸出資料行。</span><span class="sxs-lookup"><span data-stu-id="74238-103">Use the **Merge Join Transformation Editor** dialog box to specify the join type, the join columns, and the output columns for merging two inputs combined by a join.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="74238-104">合併聯結轉換針對其輸入需要已排序的資料。</span><span class="sxs-lookup"><span data-stu-id="74238-104">The Merge Join Transformation requires sorted data for its inputs.</span></span> <span data-ttu-id="74238-105">如需這項重要需求的詳細資訊，請參閱 [排序合併和合併聯結轉換的資料](data-flow/transformations/sort-data-for-the-merge-and-merge-join-transformations.md)。</span><span class="sxs-lookup"><span data-stu-id="74238-105">For more information about this important requirement, see [Sort Data for the Merge and Merge Join Transformations](data-flow/transformations/sort-data-for-the-merge-and-merge-join-transformations.md).</span></span>  
  
 <span data-ttu-id="74238-106">若要深入了解合併聯結轉換，請參閱 [合併聯結轉換](data-flow/transformations/merge-join-transformation.md)。</span><span class="sxs-lookup"><span data-stu-id="74238-106">To learn more about the Merge Join transformation, see [Merge Join Transformation](data-flow/transformations/merge-join-transformation.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="74238-107">選項。</span><span class="sxs-lookup"><span data-stu-id="74238-107">Options</span></span>  
 <span data-ttu-id="74238-108">**聯結類型**</span><span class="sxs-lookup"><span data-stu-id="74238-108">**Join type**</span></span>  
 <span data-ttu-id="74238-109">指定要使用內部聯結、左方外部聯結或完整聯結。</span><span class="sxs-lookup"><span data-stu-id="74238-109">Specify whether you want to use an inner join, left outer join, or full join.</span></span>  
  
 <span data-ttu-id="74238-110">**交換輸入**</span><span class="sxs-lookup"><span data-stu-id="74238-110">**Swap Inputs**</span></span>  
 <span data-ttu-id="74238-111">使用 [交換輸入]  按鈕，來切換輸入之間的順序。</span><span class="sxs-lookup"><span data-stu-id="74238-111">Switch the order between inputs by using the **Swap Inputs** button.</span></span> <span data-ttu-id="74238-112">此選取項目對於左方外部聯結選項可能非常有用。</span><span class="sxs-lookup"><span data-stu-id="74238-112">This selection may be useful with the Left outer join option.</span></span>  
  
 <span data-ttu-id="74238-113">**輸入**</span><span class="sxs-lookup"><span data-stu-id="74238-113">**Input**</span></span>  
 <span data-ttu-id="74238-114">針對您要放入合併輸出中的每個資料行，首先從可用的輸入清單中選取。</span><span class="sxs-lookup"><span data-stu-id="74238-114">For each column that you want in the merged output, first select from the list of available inputs.</span></span>  
  
 <span data-ttu-id="74238-115">輸入會以兩個個別的資料表來顯示。</span><span class="sxs-lookup"><span data-stu-id="74238-115">Inputs are displayed in two separate tables.</span></span> <span data-ttu-id="74238-116">選取要包含在輸出中的資料行。</span><span class="sxs-lookup"><span data-stu-id="74238-116">Select columns to include in the output.</span></span> <span data-ttu-id="74238-117">拖曳資料行以建立資料表之間的聯結。</span><span class="sxs-lookup"><span data-stu-id="74238-117">Drag columns to create a join between the tables.</span></span> <span data-ttu-id="74238-118">若要刪除聯結，請選取聯結然後按下 DELETE 鍵。</span><span class="sxs-lookup"><span data-stu-id="74238-118">To delete a join, select it and then press the DELETE key.</span></span>  
  
 <span data-ttu-id="74238-119">**輸入資料行**</span><span class="sxs-lookup"><span data-stu-id="74238-119">**Input Column**</span></span>  
 <span data-ttu-id="74238-120">從所選輸入上之可用的資料行清單中，選取要包含在合併輸出中的資料行。</span><span class="sxs-lookup"><span data-stu-id="74238-120">Select a column to include in the merged output from the list of available columns on the selected input.</span></span>  
  
 <span data-ttu-id="74238-121">**輸出別名**</span><span class="sxs-lookup"><span data-stu-id="74238-121">**Output Alias**</span></span>  
 <span data-ttu-id="74238-122">輸入每一個輸出資料行的別名。</span><span class="sxs-lookup"><span data-stu-id="74238-122">Type an alias for each output column.</span></span> <span data-ttu-id="74238-123">預設是輸入資料行的名稱；但是，您可以選擇任何唯一的、描述性名稱。</span><span class="sxs-lookup"><span data-stu-id="74238-123">The default is the name of the input column; however, you can choose any unique, descriptive name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74238-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="74238-124">See Also</span></span>  
 <span data-ttu-id="74238-125">[Integration Services 錯誤和訊息參考](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="74238-125">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="74238-126">[排序合併和合併聯結轉換的資料](data-flow/transformations/sort-data-for-the-merge-and-merge-join-transformations.md) </span><span class="sxs-lookup"><span data-stu-id="74238-126">[Sort Data for the Merge and Merge Join Transformations](data-flow/transformations/sort-data-for-the-merge-and-merge-join-transformations.md) </span></span>  
 <span data-ttu-id="74238-127">[使用合併聯結轉換來擴充資料集](data-flow/transformations/extend-a-dataset-by-using-the-merge-join-transformation.md) </span><span class="sxs-lookup"><span data-stu-id="74238-127">[Extend a Dataset by Using the Merge Join Transformation](data-flow/transformations/extend-a-dataset-by-using-the-merge-join-transformation.md) </span></span>  
 <span data-ttu-id="74238-128">[合併轉換](data-flow/transformations/merge-transformation.md) </span><span class="sxs-lookup"><span data-stu-id="74238-128">[Merge Transformation](data-flow/transformations/merge-transformation.md) </span></span>  
 [<span data-ttu-id="74238-129">聯集全部轉換</span><span class="sxs-lookup"><span data-stu-id="74238-129">Union All Transformation</span></span>](data-flow/transformations/union-all-transformation.md)  
  
  
