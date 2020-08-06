---
title: 模糊查閱轉換編輯器 ([Advanced] 索引標籤) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.fuzzylookuptransformation.advanced.f1
helpviewer_keywords:
- Fuzzy Lookup Transformation Editor
ms.assetid: 0a2919be-2ea7-4c06-82b8-0ffad5f0dd83
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 68f53eb2735dc07656fc8ff2b81c3259caa4847b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688033"
---
# <a name="fuzzy-lookup-transformation-editor-advanced-tab"></a><span data-ttu-id="33e11-102">模糊查閱轉換編輯器 (進階索引標籤)</span><span class="sxs-lookup"><span data-stu-id="33e11-102">Fuzzy Lookup Transformation Editor (Advanced Tab)</span></span>
  <span data-ttu-id="33e11-103">使用 **[模糊查閱轉換編輯器]** 對話方塊的 **[進階]** 索引標籤，即可設定模糊查閱的參數。</span><span class="sxs-lookup"><span data-stu-id="33e11-103">Use the **Advanced** tab of the **Fuzzy Lookup Transformation Editor** dialog box to set parameters for the fuzzy lookup.</span></span>  
  
 <span data-ttu-id="33e11-104">若要深入了解模糊查閱轉換，請參閱＜ [Fuzzy Lookup Transformation](data-flow/transformations/lookup-transformation.md)＞。</span><span class="sxs-lookup"><span data-stu-id="33e11-104">To learn more about the Fuzzy Lookup transformation, see [Fuzzy Lookup Transformation](data-flow/transformations/lookup-transformation.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="33e11-105">選項</span><span class="sxs-lookup"><span data-stu-id="33e11-105">Options</span></span>  
 <span data-ttu-id="33e11-106">**每次查閱輸出的相符項目上限**</span><span class="sxs-lookup"><span data-stu-id="33e11-106">**Maximum number of matches to output per lookup**</span></span>  
 <span data-ttu-id="33e11-107">指定轉換針對每一個輸入資料列，可以傳回的相符項目上限。</span><span class="sxs-lookup"><span data-stu-id="33e11-107">Specify the maximum number of matches the transformation can return for each input row.</span></span> <span data-ttu-id="33e11-108">預設為 **1**。</span><span class="sxs-lookup"><span data-stu-id="33e11-108">The default is **1**.</span></span>  
  
 <span data-ttu-id="33e11-109">**相似度臨界值**</span><span class="sxs-lookup"><span data-stu-id="33e11-109">**Similarity threshold**</span></span>  
 <span data-ttu-id="33e11-110">使用滑桿設定元件層級的相似度臨界值。</span><span class="sxs-lookup"><span data-stu-id="33e11-110">Set the similarity threshold at the component level by using the slider.</span></span> <span data-ttu-id="33e11-111">此值越接近 1，查閱值與來源值的相似度必須越接近才能認定為相符。</span><span class="sxs-lookup"><span data-stu-id="33e11-111">The closer the value is to 1, the closer the resemblance of the lookup value to the source value must be to qualify as a match.</span></span> <span data-ttu-id="33e11-112">增加臨界值可改善比對速度，因為需要考慮的候選記錄越少。</span><span class="sxs-lookup"><span data-stu-id="33e11-112">Increasing the threshold can improve the speed of matching since fewer candidate records need to be considered.</span></span>  
  
 <span data-ttu-id="33e11-113">**Token 分隔符號**</span><span class="sxs-lookup"><span data-stu-id="33e11-113">**Token delimiters**</span></span>  
 <span data-ttu-id="33e11-114">指定轉換用來 Token 化資料行值的分隔符號。</span><span class="sxs-lookup"><span data-stu-id="33e11-114">Specify the delimiters that the transformation uses to tokenize column values.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33e11-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="33e11-115">See Also</span></span>  
 <span data-ttu-id="33e11-116">[Integration Services 錯誤和訊息參考](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="33e11-116">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="33e11-117">[[模糊查閱轉換編輯器] &#40;[參考資料表] 索引標籤&#41;](../../2014/integration-services/fuzzy-lookup-transformation-editor-reference-table-tab.md) </span><span class="sxs-lookup"><span data-stu-id="33e11-117">[Fuzzy Lookup Transformation Editor &#40;Reference Table Tab&#41;](../../2014/integration-services/fuzzy-lookup-transformation-editor-reference-table-tab.md) </span></span>  
 [<span data-ttu-id="33e11-118">模糊查閱轉換編輯器 &#40;資料行索引標籤&#41;</span><span class="sxs-lookup"><span data-stu-id="33e11-118">Fuzzy Lookup Transformation Editor &#40;Columns Tab&#41;</span></span>](../../2014/integration-services/fuzzy-lookup-transformation-editor-columns-tab.md)  
  
  
