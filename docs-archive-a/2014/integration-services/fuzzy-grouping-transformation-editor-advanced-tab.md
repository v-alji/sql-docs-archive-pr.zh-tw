---
title: 模糊群組轉換編輯器 ([Advanced] 索引標籤) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.fuzzygroupingtransformation.advanced.f1
helpviewer_keywords:
- Fuzzy Grouping Transformation Editor
ms.assetid: dd820d75-b8a7-4515-aea4-3553ba5b442e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 2f5dd05eda56b4818914f659734eb3cdfb20c4d0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593442"
---
# <a name="fuzzy-grouping-transformation-editor-advanced-tab"></a><span data-ttu-id="3111c-102">模糊群組轉換編輯器 (進階索引標籤)</span><span class="sxs-lookup"><span data-stu-id="3111c-102">Fuzzy Grouping Transformation Editor (Advanced Tab)</span></span>
  <span data-ttu-id="3111c-103">使用 **[模糊群組轉換編輯器]** 對話方塊的 **[進階]** 索引標籤，即可指定輸入和輸出資料行、設定類似度臨界值，以及定義分隔符號。</span><span class="sxs-lookup"><span data-stu-id="3111c-103">Use the **Advanced** tab of the **Fuzzy Grouping Transformation Editor** dialog box to specify input and output columns, set similarity thresholds, and define delimiters.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3111c-104">[模糊群組 `Exhaustive` `MaxMemoryUsage` **轉換編輯器**] 中無法使用 [模糊群組] 轉換的和屬性，但是可以使用 [**進階編輯器**] 來設定。</span><span class="sxs-lookup"><span data-stu-id="3111c-104">The `Exhaustive` and the `MaxMemoryUsage` properties of the Fuzzy Grouping transformation are not available in the **Fuzzy Grouping Transformation Editor**, but can be set by using the **Advanced Editor**.</span></span> <span data-ttu-id="3111c-105">如需有關這些屬性的詳細資訊，請參閱＜ [Transformation Custom Properties](data-flow/transformations/transformation-custom-properties.md)＞的「模糊群組轉換」一節。</span><span class="sxs-lookup"><span data-stu-id="3111c-105">For more information on these properties, see the Fuzzy Grouping Transformation section of [Transformation Custom Properties](data-flow/transformations/transformation-custom-properties.md).</span></span>  
  
 <span data-ttu-id="3111c-106">若要深入了解模糊群組轉換，請參閱＜ [Fuzzy Grouping Transformation](data-flow/transformations/fuzzy-grouping-transformation.md)＞。</span><span class="sxs-lookup"><span data-stu-id="3111c-106">To learn more about the Fuzzy Grouping transformation, see [Fuzzy Grouping Transformation](data-flow/transformations/fuzzy-grouping-transformation.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="3111c-107">選項</span><span class="sxs-lookup"><span data-stu-id="3111c-107">Options</span></span>  
 <span data-ttu-id="3111c-108">**輸入索引鍵資料行名稱**</span><span class="sxs-lookup"><span data-stu-id="3111c-108">**Input key column name**</span></span>  
 <span data-ttu-id="3111c-109">針對每個輸入資料列，指定包含資料列之唯一識別碼的輸出資料行名稱。</span><span class="sxs-lookup"><span data-stu-id="3111c-109">Specify the name of an output column that contains the unique identifier for each input row.</span></span> <span data-ttu-id="3111c-110">`_key_in` 資料行具有能唯一識別每個資料列的值。</span><span class="sxs-lookup"><span data-stu-id="3111c-110">The `_key_in` column has a value that uniquely identifies each row.</span></span>  
  
 <span data-ttu-id="3111c-111">**輸出索引鍵資料行名稱**</span><span class="sxs-lookup"><span data-stu-id="3111c-111">**Output key column name**</span></span>  
 <span data-ttu-id="3111c-112">針對由一組重複資料列組成的標準資料列，指定包含標準資料列之唯一識別碼的輸出資料行名稱。</span><span class="sxs-lookup"><span data-stu-id="3111c-112">Specify the name of an output column that contains the unique identifier for the canonical row of a group of duplicate rows.</span></span> <span data-ttu-id="3111c-113">`_key_out` 資料行會對應至標準資料之資料列的 `_key_in` 值。</span><span class="sxs-lookup"><span data-stu-id="3111c-113">The `_key_out` column corresponds to the `_key_in` value of the canonical data row.</span></span>  
  
 <span data-ttu-id="3111c-114">**相似度分數資料行名稱**</span><span class="sxs-lookup"><span data-stu-id="3111c-114">**Similarity score column name**</span></span>  
 <span data-ttu-id="3111c-115">指定包含相似度分數之資料行的名稱。</span><span class="sxs-lookup"><span data-stu-id="3111c-115">Specify a name for the column that contains the similarity score.</span></span> <span data-ttu-id="3111c-116">相似度分數是介於 0 與 1 的值，以表示輸入資料列與標準資料列的相似度。</span><span class="sxs-lookup"><span data-stu-id="3111c-116">The similarity score is a value between 0 and 1 that indicates the similarity of the input row to the canonical row.</span></span> <span data-ttu-id="3111c-117">分數愈接近於 1，資料列與標準資料列的相符程度就愈高。</span><span class="sxs-lookup"><span data-stu-id="3111c-117">The closer the score is to 1, the more closely the row matches the canonical row.</span></span>  
  
 <span data-ttu-id="3111c-118">**相似度臨界值**</span><span class="sxs-lookup"><span data-stu-id="3111c-118">**Similarity threshold**</span></span>  
 <span data-ttu-id="3111c-119">使用滑桿來設定相似度臨界值。</span><span class="sxs-lookup"><span data-stu-id="3111c-119">Set the similarity threshold by using the slider.</span></span> <span data-ttu-id="3111c-120">臨界值越接近 1，資料列就必須彼此更相似才能判定為重複。</span><span class="sxs-lookup"><span data-stu-id="3111c-120">The closer the threshold is to 1, the more the rows must resemble each other to qualify as duplicates.</span></span> <span data-ttu-id="3111c-121">增加臨界值可以改善比對的速度，因為需要考慮的候選記錄比較少。</span><span class="sxs-lookup"><span data-stu-id="3111c-121">Increasing the threshold can improve the speed of matching because fewer candidate records have to be considered.</span></span>  
  
 <span data-ttu-id="3111c-122">**Token 分隔符號**</span><span class="sxs-lookup"><span data-stu-id="3111c-122">**Token delimiters**</span></span>  
 <span data-ttu-id="3111c-123">此項轉換提供了 Token 化資料所用的預設分隔符號集，但您可以依需要編輯清單來新增或移除分隔符號。</span><span class="sxs-lookup"><span data-stu-id="3111c-123">The transformation provides a default set of delimiters for tokenizing data, but you can add or remove delimiters as needed by editing the list.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3111c-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3111c-124">See Also</span></span>  
 <span data-ttu-id="3111c-125">[Integration Services 錯誤和訊息參考](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="3111c-125">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 [<span data-ttu-id="3111c-126">使用模糊群組轉換來識別相似的資料列</span><span class="sxs-lookup"><span data-stu-id="3111c-126">Identify Similar Data Rows by Using the Fuzzy Grouping Transformation</span></span>](data-flow/transformations/identify-similar-data-rows-by-using-the-fuzzy-grouping-transformation.md)  
  
  
