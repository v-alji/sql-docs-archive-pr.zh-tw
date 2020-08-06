---
title: 建立關聯性 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.createrelationships.f1
ms.assetid: 6ebd305f-ffd2-4a1d-b24c-e28c151b94f5
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 5a1095e193587ae7d416311031e5297a035ca37e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593462"
---
# <a name="create-relationships"></a><span data-ttu-id="c370f-102">建立關聯性</span><span class="sxs-lookup"><span data-stu-id="c370f-102">Create Relationships</span></span>
  <span data-ttu-id="c370f-103">使用 **[建立關聯性]** 對話方塊，即可編輯來源資料行與查閱資料表資料行之間的對應，而這些資料行是在模糊查閱轉換編輯器、查閱轉換編輯器和詞彙查閱轉換編輯器中進行設定。</span><span class="sxs-lookup"><span data-stu-id="c370f-103">Use the **Create Relationships** dialog box to edit mappings between the source columns and the lookup table columns that you configured in the Fuzzy Lookup Transformation Editor, the Lookup Transformation Editor, and the Term Lookup Transformation Editor.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c370f-104">從詞彙查閱轉換編輯器中叫用時，[建立關聯性]  對話方塊只會顯示 [輸入資料行]  和 [查閱資料行]  清單。</span><span class="sxs-lookup"><span data-stu-id="c370f-104">The **Create Relationships** dialog box displays only the **Input Column** and **Lookup Column** lists when invoked from the Term Lookup Transformation Editor.</span></span>  
  
 <span data-ttu-id="c370f-105">若要深入了解使用 **[建立關聯性]** 對話方塊的轉換，請參閱＜ [Fuzzy Lookup Transformation](lookup-transformation.md)＞、＜ [Lookup Transformation](lookup-transformation.md)＞和＜ [Term Lookup Transformation](term-lookup-transformation.md)＞。</span><span class="sxs-lookup"><span data-stu-id="c370f-105">To learn more about the transformations that use the **Create Relationships** dialog box, see [Fuzzy Lookup Transformation](lookup-transformation.md), [Lookup Transformation](lookup-transformation.md), and [Term Lookup Transformation](term-lookup-transformation.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="c370f-106">選項。</span><span class="sxs-lookup"><span data-stu-id="c370f-106">Options</span></span>  
 <span data-ttu-id="c370f-107">**輸入資料行**</span><span class="sxs-lookup"><span data-stu-id="c370f-107">**Input Column**</span></span>  
 <span data-ttu-id="c370f-108">從可用的輸入資料行清單中選取。</span><span class="sxs-lookup"><span data-stu-id="c370f-108">Select from the list of available input columns.</span></span>  
  
 <span data-ttu-id="c370f-109">**查閱資料行**</span><span class="sxs-lookup"><span data-stu-id="c370f-109">**Lookup Column**</span></span>  
 <span data-ttu-id="c370f-110">從可用的查閱資料行清單中選取。</span><span class="sxs-lookup"><span data-stu-id="c370f-110">Select from the list of available lookup columns.</span></span>  
  
 <span data-ttu-id="c370f-111">**對應類型**</span><span class="sxs-lookup"><span data-stu-id="c370f-111">**Mapping Type**</span></span>  
 <span data-ttu-id="c370f-112">選取模糊相符或完全相符。</span><span class="sxs-lookup"><span data-stu-id="c370f-112">Select fuzzy or exact matching.</span></span>  
  
 <span data-ttu-id="c370f-113">當您使用模糊比對時，如果所有含模糊相符類型的資料行都具有足夠的相似度，則這些資料列就會被視為重複。</span><span class="sxs-lookup"><span data-stu-id="c370f-113">When you use fuzzy matching, rows are considered duplicates if they are sufficiently similar across all columns that have a fuzzy match type.</span></span> <span data-ttu-id="c370f-114">若要從模糊比對取得較佳的結果，您可以指定某些資料行應使用完全相符而非模糊比對。</span><span class="sxs-lookup"><span data-stu-id="c370f-114">To obtain better results from fuzzy matching, you can specify that some columns should use exact matching instead of fuzzy matching.</span></span> <span data-ttu-id="c370f-115">例如，若您知道特定資料行沒有錯誤或不一致性，您就可以在該資料行指定完全相符，使得此資料行中只有包含相同值的資料列才會被視為可能重複。</span><span class="sxs-lookup"><span data-stu-id="c370f-115">For example, if you know that a certain column contains no errors or inconsistencies, you can specify exact matching on that column, so that only rows which contain identical values in this column are considered as possible duplicates.</span></span> <span data-ttu-id="c370f-116">這可在其他資料行增加模糊比對的精確度。</span><span class="sxs-lookup"><span data-stu-id="c370f-116">This increases the accuracy of fuzzy matching on other columns.</span></span>  
  
 <span data-ttu-id="c370f-117">**比較旗標**</span><span class="sxs-lookup"><span data-stu-id="c370f-117">**Comparison Flags**</span></span>  
 <span data-ttu-id="c370f-118">如需字串比較選項的資訊，請參閱 [比較字串資料](../comparing-string-data.md)。</span><span class="sxs-lookup"><span data-stu-id="c370f-118">For information about the string comparison options, see [Comparing String Data](../comparing-string-data.md).</span></span>  
  
 <span data-ttu-id="c370f-119">**最小相似度**</span><span class="sxs-lookup"><span data-stu-id="c370f-119">**Minimum Similarity**</span></span>  
 <span data-ttu-id="c370f-120">藉由使用滑桿，在資料行層級設定相似度臨界值。</span><span class="sxs-lookup"><span data-stu-id="c370f-120">Set the similarity threshold at the column level by using the slider.</span></span> <span data-ttu-id="c370f-121">這個值愈接近 1，則查閱值與來源值就必須愈相似，才能認定它們相符。</span><span class="sxs-lookup"><span data-stu-id="c370f-121">The closer the value is to 1, the more the lookup value must resemble the source value to qualify as a match.</span></span> <span data-ttu-id="c370f-122">增加臨界值可以改善比對的速度，因為需要考慮的候選記錄比較少。</span><span class="sxs-lookup"><span data-stu-id="c370f-122">Increasing the threshold can improve the speed of matching because fewer candidate records have to be considered.</span></span>  
  
 <span data-ttu-id="c370f-123">**相似度輸出別名**</span><span class="sxs-lookup"><span data-stu-id="c370f-123">**Similarity Output Alias**</span></span>  
 <span data-ttu-id="c370f-124">指定新輸出資料行的名稱，資料行中包含該選取資料行的相似度分數。</span><span class="sxs-lookup"><span data-stu-id="c370f-124">Specify the name for a new output column that contains the similarity scores for the selected column.</span></span> <span data-ttu-id="c370f-125">如果您將此值保留空白，就不會建立輸出資料行。</span><span class="sxs-lookup"><span data-stu-id="c370f-125">If you leave this value empty, the output column is not created.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c370f-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c370f-126">See Also</span></span>  
 <span data-ttu-id="c370f-127">[Integration Services 錯誤和訊息參考](../../integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="c370f-127">[Integration Services Error and Message Reference](../../integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="c370f-128">[模糊查閱轉換編輯器 &#40;資料行索引標籤&#41;](../../fuzzy-lookup-transformation-editor-columns-tab.md) </span><span class="sxs-lookup"><span data-stu-id="c370f-128">[Fuzzy Lookup Transformation Editor &#40;Columns Tab&#41;](../../fuzzy-lookup-transformation-editor-columns-tab.md) </span></span>  
 <span data-ttu-id="c370f-129">[查閱轉換編輯器 &#40;資料行頁面&#41;](../../lookup-transformation-editor-columns-page.md) </span><span class="sxs-lookup"><span data-stu-id="c370f-129">[Lookup Transformation Editor &#40;Columns Page&#41;](../../lookup-transformation-editor-columns-page.md) </span></span>  
 [<span data-ttu-id="c370f-130">詞彙查閱轉換編輯器 &#40;詞彙查閱索引標籤&#41;</span><span class="sxs-lookup"><span data-stu-id="c370f-130">Term Lookup Transformation Editor &#40;Term Lookup Tab&#41;</span></span>](../../term-lookup-transformation-editor-term-lookup-tab.md)  
  
  
