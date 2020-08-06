---
title: 資料截斷 (SSIS) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- truncating data
- data truncation [Integration Services]
- expressions [Integration Services], data truncation
- truncate options [Integration Services]
ms.assetid: 02461e15-49ca-445b-abb3-5c369c283ec2
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e0c4280c9eacd22ebf84bf1570d485de51cab09b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606431"
---
# <a name="data-truncation-ssis"></a><span data-ttu-id="7f610-102">資料截斷 (SSIS)</span><span class="sxs-lookup"><span data-stu-id="7f610-102">Data Truncation (SSIS)</span></span>
  <span data-ttu-id="7f610-103">運算式可能不小心造成資料遭截斷。</span><span class="sxs-lookup"><span data-stu-id="7f610-103">An expression may inadvertently cause data to be truncated.</span></span> <span data-ttu-id="7f610-104">在下列情況下可能發生截斷：</span><span class="sxs-lookup"><span data-stu-id="7f610-104">Truncation can occur under the following circumstances:</span></span>  
  
-   <span data-ttu-id="7f610-105">字串。</span><span class="sxs-lookup"><span data-stu-id="7f610-105">Strings.</span></span> <span data-ttu-id="7f610-106">例如，將具有 DT_WSTR 資料類型的字串資料，翻譯成具有 DT_STR 資料類型的相同長度字串 (以字元計算) 時，如果原始字串包含雙位元組字元，則會造成資料遺失。</span><span class="sxs-lookup"><span data-stu-id="7f610-106">For example, translating string data with a DT_WSTR data type to the same length string, measured in characters, with a DT_STR data type causes data loss if the original string contains double-byte characters.</span></span>  
  
-   <span data-ttu-id="7f610-107">有效位數。</span><span class="sxs-lookup"><span data-stu-id="7f610-107">Significant digits.</span></span> <span data-ttu-id="7f610-108">例如，將整數從 DT_I4 資料類型轉換成 DT_I2 資料類型，或將不帶正負號的整數轉換成帶正負號的整數。</span><span class="sxs-lookup"><span data-stu-id="7f610-108">For example, casting an integer from a DT_I4 data type to a DT_I2 data type or an unsigned integer to a signed integer.</span></span>  
  
-   <span data-ttu-id="7f610-109">無效位數。</span><span class="sxs-lookup"><span data-stu-id="7f610-109">Insignificant digits.</span></span> <span data-ttu-id="7f610-110">例如，將實數從 DT_R8 轉換成 DT_R4，或將整數從 DT_I4 資料類型轉換成 DT_R4 資料類型。</span><span class="sxs-lookup"><span data-stu-id="7f610-110">For example, casting a real number from a DT_R8 to a DT_R4 or an integer from a DT_I4 data type to a DT_R4 data type.</span></span>  
  
 <span data-ttu-id="7f610-111">運算式評估工具會識別可能導致截斷的明確轉換，並在剖析運算式時發出警告。</span><span class="sxs-lookup"><span data-stu-id="7f610-111">The expression evaluator identifies explicit casts that may cause truncation and issues a warning when the expression is parsed.</span></span> <span data-ttu-id="7f610-112">例如，如果將 30 個字元的字串轉換成 20 個字元的字串，則運算式評估工具會向您發出警告。</span><span class="sxs-lookup"><span data-stu-id="7f610-112">For example, the expression evaluator warns you if a 30-character string is cast into a 20-character string.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7f610-113">在執行階段不會檢查截斷；資料會在沒有任何警告下遭截斷。</span><span class="sxs-lookup"><span data-stu-id="7f610-113">Truncation is not checked at run time; data is truncated without warning.</span></span> <span data-ttu-id="7f610-114">不過，多數資料配接器和轉換支援錯誤輸出，可處理錯誤資料列的配置。</span><span class="sxs-lookup"><span data-stu-id="7f610-114">However, most data adapters and transformations support error outputs that can handle the disposition of error rows.</span></span> <span data-ttu-id="7f610-115">如需處理資料截斷的詳細資訊，請參閱[處理資料中的錯誤](../data-flow/error-handling-in-data.md)。</span><span class="sxs-lookup"><span data-stu-id="7f610-115">For more information about handling truncation of data, see [Error Handling in Data](../data-flow/error-handling-in-data.md).</span></span>  
  
  
