---
title: '[詞彙解壓縮轉換編輯器] ([Advanced] 索引標籤) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.termextraction.advanced.f1
helpviewer_keywords:
- Term Extraction Transformation Editor
ms.assetid: 87118281-6e3c-499e-bac4-fa4c24bb12c6
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f4be56f8ac2deeab49e43071a07894a466019287
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703121"
---
# <a name="term-extraction-transformation-editor-advanced-tab"></a><span data-ttu-id="84a12-102">詞彙擷取轉換編輯器 (進階索引標籤)</span><span class="sxs-lookup"><span data-stu-id="84a12-102">Term Extraction Transformation Editor (Advanced Tab)</span></span>
  <span data-ttu-id="84a12-103">使用 [詞彙擷取轉換編輯器]  對話方塊的 [進階]  索引標籤，即可指定擷取的屬性，例如頻率、長度和是否擷取單字或片語。</span><span class="sxs-lookup"><span data-stu-id="84a12-103">Use the **Advanced** tab of the **Term Extraction Transformation Editor** dialog box to specify properties for the extraction such as frequency, length, and whether to extract words or phrases.</span></span>  
  
 <span data-ttu-id="84a12-104">若要深入了解詞彙擷取轉換，請參閱＜ [Term Extraction Transformation](data-flow/transformations/term-extraction-transformation.md)＞。</span><span class="sxs-lookup"><span data-stu-id="84a12-104">To learn more about the Term Extraction transformation, see [Term Extraction Transformation](data-flow/transformations/term-extraction-transformation.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="84a12-105">選項。</span><span class="sxs-lookup"><span data-stu-id="84a12-105">Options</span></span>  
 <span data-ttu-id="84a12-106">**名詞**</span><span class="sxs-lookup"><span data-stu-id="84a12-106">**Noun**</span></span>  
 <span data-ttu-id="84a12-107">指定轉換只擷取個別的名詞。</span><span class="sxs-lookup"><span data-stu-id="84a12-107">Specify that the transformation extracts individual nouns only.</span></span>  
  
 <span data-ttu-id="84a12-108">**名詞片語**</span><span class="sxs-lookup"><span data-stu-id="84a12-108">**Noun phrase**</span></span>  
 <span data-ttu-id="84a12-109">指定轉換只擷取名詞片語。</span><span class="sxs-lookup"><span data-stu-id="84a12-109">Specify that the transformation extracts noun phrases only.</span></span>  
  
 <span data-ttu-id="84a12-110">**名詞和名詞片語**</span><span class="sxs-lookup"><span data-stu-id="84a12-110">**Noun and noun phrase**</span></span>  
 <span data-ttu-id="84a12-111">指定轉換同時擷取名詞和名詞片語。</span><span class="sxs-lookup"><span data-stu-id="84a12-111">Specify that the transformation extracts both nouns and noun phrases.</span></span>  
  
 <span data-ttu-id="84a12-112">**頻率**</span><span class="sxs-lookup"><span data-stu-id="84a12-112">**Frequency**</span></span>  
 <span data-ttu-id="84a12-113">指定分數是詞彙的頻率。</span><span class="sxs-lookup"><span data-stu-id="84a12-113">Specify that the score is the frequency of the term.</span></span>  
  
 <span data-ttu-id="84a12-114">**TFIDF**</span><span class="sxs-lookup"><span data-stu-id="84a12-114">**TFIDF**</span></span>  
 <span data-ttu-id="84a12-115">指定分數是詞彙的 TFIDF 值。</span><span class="sxs-lookup"><span data-stu-id="84a12-115">Specify that the score is the TFIDF value of the term.</span></span> <span data-ttu-id="84a12-116">TFIDF 分數是「詞彙頻率」和「反向文件頻率」的乘積，定義為︰詞彙 T 的 TFIDF = (T 的頻率) \* log((輸入中的資料列數) / (具有 T 的資料列數))</span><span class="sxs-lookup"><span data-stu-id="84a12-116">The TFIDF score is the product of Term Frequency and Inverse Document Frequency, defined as: TFIDF of a Term T = (frequency of T) \* log( (#rows in Input) / (#rows having T) )</span></span>  
  
 <span data-ttu-id="84a12-117">**頻率臨界值**</span><span class="sxs-lookup"><span data-stu-id="84a12-117">**Frequency threshold**</span></span>  
 <span data-ttu-id="84a12-118">指定擷取單字或片語前，該單字或片語必須出現的次數。</span><span class="sxs-lookup"><span data-stu-id="84a12-118">Specify the number of times a word or phrase must occur before extracting it.</span></span> <span data-ttu-id="84a12-119">預設值為 2。</span><span class="sxs-lookup"><span data-stu-id="84a12-119">The default value is 2.</span></span>  
  
 <span data-ttu-id="84a12-120">**詞彙最大長度**</span><span class="sxs-lookup"><span data-stu-id="84a12-120">**Maximum length of term**</span></span>  
 <span data-ttu-id="84a12-121">指定在文字中，片語的最大長度。</span><span class="sxs-lookup"><span data-stu-id="84a12-121">Specify the maximum length of a phrase in words.</span></span> <span data-ttu-id="84a12-122">此選項只會影響名詞片語。</span><span class="sxs-lookup"><span data-stu-id="84a12-122">This option affects noun phrases only.</span></span> <span data-ttu-id="84a12-123">預設值為 12。</span><span class="sxs-lookup"><span data-stu-id="84a12-123">The default value is 12.</span></span>  
  
 <span data-ttu-id="84a12-124">**使用區分大小寫的詞彙擷取**</span><span class="sxs-lookup"><span data-stu-id="84a12-124">**Use case-sensitive term extraction**</span></span>  
 <span data-ttu-id="84a12-125">指定擷取是否區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="84a12-125">Specify whether to make the extraction case-sensitive.</span></span> <span data-ttu-id="84a12-126">預設為 `False`。</span><span class="sxs-lookup"><span data-stu-id="84a12-126">The default is `False`.</span></span>  
  
 <span data-ttu-id="84a12-127">**設定錯誤輸出**</span><span class="sxs-lookup"><span data-stu-id="84a12-127">**Configure Error Output**</span></span>  
 <span data-ttu-id="84a12-128">使用 [[設定錯誤輸出]](../../2014/integration-services/configure-error-output.md) 對話方塊，即可指定造成錯誤之資料列的錯誤處理。</span><span class="sxs-lookup"><span data-stu-id="84a12-128">Use the [Configure Error Output](../../2014/integration-services/configure-error-output.md) dialog box to specify error handling for rows that cause errors.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84a12-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="84a12-129">See Also</span></span>  
 <span data-ttu-id="84a12-130">[Integration Services 錯誤和訊息參考](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="84a12-130">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="84a12-131">[[詞彙解壓縮轉換編輯器] &#40;[詞彙] [提取] 索引標籤&#41;](../../2014/integration-services/term-extraction-transformation-editor-term-extraction-tab.md) </span><span class="sxs-lookup"><span data-stu-id="84a12-131">[Term Extraction Transformation Editor &#40;Term Extraction Tab&#41;](../../2014/integration-services/term-extraction-transformation-editor-term-extraction-tab.md) </span></span>  
 <span data-ttu-id="84a12-132">[[詞彙解壓縮轉換編輯器] &#40;[排除] 索引標籤&#41;](../../2014/integration-services/term-extraction-transformation-editor-exclusion-tab.md) </span><span class="sxs-lookup"><span data-stu-id="84a12-132">[Term Extraction Transformation Editor &#40;Exclusion Tab&#41;](../../2014/integration-services/term-extraction-transformation-editor-exclusion-tab.md) </span></span>  
 [<span data-ttu-id="84a12-133">詞彙查閱轉換</span><span class="sxs-lookup"><span data-stu-id="84a12-133">Term Lookup Transformation</span></span>](data-flow/transformations/lookup-transformation.md)  
  
  
