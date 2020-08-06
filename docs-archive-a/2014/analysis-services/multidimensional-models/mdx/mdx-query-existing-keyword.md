---
title: 現有關鍵詞 (MDX) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- EXISTING
helpviewer_keywords:
- Existing keyword
ms.assetid: 651ee9ac-04ef-4316-87c9-a3df5ac27d22
author: minewiskan
ms.author: owend
ms.openlocfilehash: 115444c832fe8fe9b258a0c23b97b97553f32e8e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585631"
---
# <a name="existing-keyword-mdx"></a><span data-ttu-id="2e0bb-102">EXISTING 關鍵字 (MDX)</span><span class="sxs-lookup"><span data-stu-id="2e0bb-102">EXISTING Keyword (MDX)</span></span>
  <span data-ttu-id="2e0bb-103">強制在目前內容內評估指定的集合。</span><span class="sxs-lookup"><span data-stu-id="2e0bb-103">Forces a specified set to be evaluated within the current context.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2e0bb-104">語法</span><span class="sxs-lookup"><span data-stu-id="2e0bb-104">Syntax</span></span>  
  
```  
  
Existing Set_Expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="2e0bb-105">引數</span><span class="sxs-lookup"><span data-stu-id="2e0bb-105">Arguments</span></span>  
 <span data-ttu-id="2e0bb-106">*Set_Expression*</span><span class="sxs-lookup"><span data-stu-id="2e0bb-106">*Set_Expression*</span></span>  
 <span data-ttu-id="2e0bb-107">有效的多維度運算式 (MDX) 集合運算式。</span><span class="sxs-lookup"><span data-stu-id="2e0bb-107">A valid Multidimensional Expressions (MDX) set expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2e0bb-108">備註</span><span class="sxs-lookup"><span data-stu-id="2e0bb-108">Remarks</span></span>  
 <span data-ttu-id="2e0bb-109">根據預設，會在包含集合成員的 Cube 內容內評估集合。</span><span class="sxs-lookup"><span data-stu-id="2e0bb-109">By default, sets are evaluated within the context of the cube that contains the members of the set.</span></span> <span data-ttu-id="2e0bb-110">但是 `Existing` 關鍵字會強制在目前的內容內評估指定的集合。</span><span class="sxs-lookup"><span data-stu-id="2e0bb-110">The `Existing` keyword forces a specified set to be evaluated within the current context instead.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2e0bb-111">範例</span><span class="sxs-lookup"><span data-stu-id="2e0bb-111">Example</span></span>  
 <span data-ttu-id="2e0bb-112">下列範例會根據使用 `Aggregate` 函數評估之使用者選取的 State-Province 成員值，傳回上一個時間週期銷售值衰退的轉售商計數。</span><span class="sxs-lookup"><span data-stu-id="2e0bb-112">The following example returns the count of the resellers whose sales have declined over the previous time period, based on user-selected State-Province member values evaluated using the `Aggregate` function.</span></span> <span data-ttu-id="2e0bb-113">但是 [Hierarchize &#40;MDX&#41;](/sql/mdx/hierarchize-mdx) 和 [DrilldownLevel (MDX)](/sql/mdx/drilldownlevel-mdx) 函數是用來傳回 Product 維度中產品類別目錄的衰退銷售值。</span><span class="sxs-lookup"><span data-stu-id="2e0bb-113">The [Hierarchize &#40;MDX&#41;](/sql/mdx/hierarchize-mdx) and [DrilldownLevel (MDX)](/sql/mdx/drilldownlevel-mdx) functions are used to return values for declining sales for product categories in the Product dimension.</span></span> <span data-ttu-id="2e0bb-114">`Existing`關鍵字會強制在目前的內容中評估函式中的集合， `Filter` 也就是州/省屬性階層的華盛頓州和俄勒岡成員。</span><span class="sxs-lookup"><span data-stu-id="2e0bb-114">The `Existing` keyword forces the set in the `Filter` function to be evaluated in the current context - that is, for the Washington and Oregon members of the State-Province attribute hierarchy.</span></span>  
  
```  
WITH MEMBER Measures.[Declining Reseller Sales] AS  
   Count  
      (Filter  
         (Existing  
            (Reseller.Reseller.Reseller)  
         , [Measures].[Reseller Sales Amount] <   
            ([Measures].[Reseller Sales Amount]  
               ,[Date].Calendar.PrevMember  
            )  
        )  
      )  
MEMBER [Geography].[State-Province].x AS   
   Aggregate   
      ( {[Geography].[State-Province].&[WA]&[US]  
         , [Geography].[State-Province].&[OR]&[US] }   
      )  
SELECT NON EMPTY HIERARCHIZE   
      (AddCalculatedMembers   
         (   
            {DrillDownLevel  
               ({[Product].[All Products]}  
               )  
            }   
         )   
      ) DIMENSION PROPERTIES PARENT_UNIQUE_NAME ON COLUMNS   
FROM [Adventure Works]  
WHERE   
      ( [Geography].[State-Province].x  
        , [Date].[Calendar].[Calendar Quarter].&[2003]&[4]  
        ,[Measures].[Declining Reseller Sales]  
      )  
  
```  
  
## <a name="see-also"></a><span data-ttu-id="2e0bb-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2e0bb-115">See Also</span></span>  
 <span data-ttu-id="2e0bb-116">[&#40;&#41; &#40;MDX&#41;設定計數](/sql/mdx/count-set-mdx) </span><span class="sxs-lookup"><span data-stu-id="2e0bb-116">[Count &#40;Set&#41; &#40;MDX&#41;](/sql/mdx/count-set-mdx) </span></span>  
 <span data-ttu-id="2e0bb-117">[AddCalculatedMembers &#40;MDX&#41;](/sql/mdx/addcalculatedmembers-mdx) </span><span class="sxs-lookup"><span data-stu-id="2e0bb-117">[AddCalculatedMembers &#40;MDX&#41;](/sql/mdx/addcalculatedmembers-mdx) </span></span>  
 <span data-ttu-id="2e0bb-118">[匯總 &#40;MDX&#41;](/sql/mdx/aggregate-mdx) </span><span class="sxs-lookup"><span data-stu-id="2e0bb-118">[Aggregate &#40;MDX&#41;](/sql/mdx/aggregate-mdx) </span></span>  
 <span data-ttu-id="2e0bb-119">[篩選 &#40;MDX&#41;](/sql/mdx/filter-mdx) </span><span class="sxs-lookup"><span data-stu-id="2e0bb-119">[Filter &#40;MDX&#41;](/sql/mdx/filter-mdx) </span></span>  
 <span data-ttu-id="2e0bb-120">[MDX&#41;的屬性 &#40;](/sql/mdx/properties-mdx) </span><span class="sxs-lookup"><span data-stu-id="2e0bb-120">[Properties &#40;MDX&#41;](/sql/mdx/properties-mdx) </span></span>  
 <span data-ttu-id="2e0bb-121">[DrilldownLevel &#40;MDX&#41;](/sql/mdx/drilldownlevel-mdx) </span><span class="sxs-lookup"><span data-stu-id="2e0bb-121">[DrilldownLevel &#40;MDX&#41;](/sql/mdx/drilldownlevel-mdx) </span></span>  
 <span data-ttu-id="2e0bb-122">[Hierarchize &#40;MDX&#41;](/sql/mdx/hierarchize-mdx) </span><span class="sxs-lookup"><span data-stu-id="2e0bb-122">[Hierarchize &#40;MDX&#41;](/sql/mdx/hierarchize-mdx) </span></span>  
 [<span data-ttu-id="2e0bb-123">MDX 函數參考 &#40;MDX&#41;</span><span class="sxs-lookup"><span data-stu-id="2e0bb-123">MDX Function Reference &#40;MDX&#41;</span></span>](/sql/mdx/mdx-function-reference-mdx)  
  
  
