---
title: 建立以查詢範圍計算的成員 (MDX) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- WITH keyword
- query-scoped calculated members [MDX]
ms.assetid: c4507149-e67b-4e5d-9192-cc911acd9adc
author: minewiskan
ms.author: owend
ms.openlocfilehash: 9c0b3e7184f3cc6abd189344bbce1b6e1f948ebb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594740"
---
# <a name="creating-query-scoped-calculated-members-mdx"></a><span data-ttu-id="01e11-102">建立查詢範圍導出成員 (MDX)</span><span class="sxs-lookup"><span data-stu-id="01e11-102">Creating Query-Scoped Calculated Members (MDX)</span></span>
  <span data-ttu-id="01e11-103">如果單一多維度運算式 (MDX) 查詢只需要有導出成員，您可以使用 WITH 關鍵字來定義導出成員。</span><span class="sxs-lookup"><span data-stu-id="01e11-103">If a calculated member is only required for a single Multidimensional Expressions (MDX) query, you can define that calculated member by using the WITH keyword.</span></span> <span data-ttu-id="01e11-104">查詢完成執行之後，使用 WITH 關鍵字建立的導出成員就不再存在。</span><span class="sxs-lookup"><span data-stu-id="01e11-104">A calculated member that is created by using the WITH keyword no longer exists after the query has finished running.</span></span>  
  
 <span data-ttu-id="01e11-105">如同本主題所討論，WITH 關鍵字的語法很有彈性，甚至允許導出成員以另一個導出成員為基底。</span><span class="sxs-lookup"><span data-stu-id="01e11-105">As discussed in this topic, the syntax of the WITH keyword is quite flexible, even allowing a calculated member to be based on another calculated member.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="01e11-106">如需建立導出成員的詳細資訊，請參閱[在 MDX 中建立導出成員 &#40;MDX&#41;](mdx-calculated-members-building-calculated-members.md)。</span><span class="sxs-lookup"><span data-stu-id="01e11-106">For more information about calculated members, see [Building Calculated Members in MDX &#40;MDX&#41;](mdx-calculated-members-building-calculated-members.md).</span></span>  
  
## <a name="with-keyword-syntax"></a><span data-ttu-id="01e11-107">WITH 關鍵字語法</span><span class="sxs-lookup"><span data-stu-id="01e11-107">WITH Keyword Syntax</span></span>  
 <span data-ttu-id="01e11-108">使用以下語法將 WITH 關鍵字加入 MDX SELECT  陳述式：</span><span class="sxs-lookup"><span data-stu-id="01e11-108">Use the following syntax to add the WITH keyword to an MDX SELECT statement:</span></span>  
  
```  
[ WITH <SELECT WITH clause> [ , <SELECT WITH clause> ... ] ] SELECT [ * | ( <SELECT query axis clause> [ , <SELECT query axis clause> ... ] ) ]FROM <SELECT subcube clause> [ <SELECT slicer axis clause> ][ <SELECT cell property list clause> ]  
<SELECT WITH clause> ::=  
   ( [ CALCULATED ] MEMBER <CREATE MEMBER body clause>) | <CREATE MEMBER body clause> ::= Member_Identifier AS 'MDX_Expression'  
   [ <CREATE MEMBER property clause> [ , <CREATE MEMBER property clause> ... ] ]  
<CREATE MEMBER property clause> ::=  
   ( MemberProperty_Identifier = Scalar_Expression )  
  
```  
  
 <span data-ttu-id="01e11-109">在 WITH 關鍵字的語法中， `Member_Identifier` 值是導出成員的完整名稱。</span><span class="sxs-lookup"><span data-stu-id="01e11-109">In the syntax for the WITH keyword, the `Member_Identifier` value is the fully qualified name of the calculated member.</span></span> <span data-ttu-id="01e11-110">此完整名稱包括與導出成員相關的維度或層級。</span><span class="sxs-lookup"><span data-stu-id="01e11-110">This fully qualified name includes the dimension or level to which the calculated member is associated.</span></span> <span data-ttu-id="01e11-111">`MDX_Expression` 值會在評估過運算式後，傳回導出成員的值。</span><span class="sxs-lookup"><span data-stu-id="01e11-111">The `MDX_Expression` value returns the value of the calculated member after the expression value has been evaluated.</span></span> <span data-ttu-id="01e11-112">導出成員的內建資料格屬性值也可以選擇性地藉由在 `MemberProperty_Identifier` 值中提供資料格屬性名稱，以及在 `Scalar_Expression` 值中提供資料格屬性的值來指定。</span><span class="sxs-lookup"><span data-stu-id="01e11-112">The values of intrinsic cell properties for a calculated member can be optionally specified by supplying the name of the cell property in the `MemberProperty_Identifier` value and the value of the cell property in the `Scalar_Expression` value.</span></span>  
  
## <a name="with-keyword-examples"></a><span data-ttu-id="01e11-113">WITH 關鍵字範例</span><span class="sxs-lookup"><span data-stu-id="01e11-113">WITH Keyword Examples</span></span>  
 <span data-ttu-id="01e11-114">下列 MDX 查詢定義導出成員， `[Measures].[Special Discount]`，根據原始折扣量計算特殊折扣。</span><span class="sxs-lookup"><span data-stu-id="01e11-114">The following MDX query defines a calculated member, `[Measures].[Special Discount]`, calculating a special discount based on the original discount amount.</span></span>  
  
```  
WITH   
   MEMBER [Measures].[Special Discount] AS  
   [Measures].[Discount Amount] * 1.5  
SELECT   
   [Measures].[Special Discount] on COLUMNS,  
   NON EMPTY [Product].[Product].MEMBERS  ON Rows  
FROM [Adventure Works]  
WHERE [Product].[Category].[Bikes]  
```  
  
 <span data-ttu-id="01e11-115">您也可以在階層內的任意點建立導出成員。</span><span class="sxs-lookup"><span data-stu-id="01e11-115">You can also create calculated members at any point within a hierarchy.</span></span> <span data-ttu-id="01e11-116">例如，下列 MDX 查詢定義假設之 Sales Cube 的 `[BigSeller]` 導出成員。</span><span class="sxs-lookup"><span data-stu-id="01e11-116">For example, the following MDX query defines the `[BigSeller]` calculated member for a hypothetical Sales cube.</span></span> <span data-ttu-id="01e11-117">此導出成員可決定指定的商店是否至少賣出 100.00 單位的啤酒與葡萄酒。</span><span class="sxs-lookup"><span data-stu-id="01e11-117">This calculated member determines whether a specified store has at least 100.00 in unit sales for beer and wine.</span></span> <span data-ttu-id="01e11-118">但是，查詢建立的 `[BigSeller]` 導出成員不是 `[Product]` 維度的子成員，而是 `[Beer and Wine]` 成員的子成員。</span><span class="sxs-lookup"><span data-stu-id="01e11-118">However, the query creates the `[BigSeller]` calculated member not as a child member of the `[Product]` dimension, but instead as a child member of the `[Beer and Wine]` member.</span></span>  
  
```  
WITH   
   MEMBER [Product].[Beer and Wine].[BigSeller] AS  
  IIf([Product].[Beer and Wine] > 100, "Yes","No")  
SELECT  
   {[Product].[BigSeller]} ON COLUMNS,  
   Store.[Store Name].Members ON ROWS  
FROM Sales  
  
```  
  
 <span data-ttu-id="01e11-119">導出成員不必只相依於 Cube 中的現有成員。</span><span class="sxs-lookup"><span data-stu-id="01e11-119">Calculated members do not have to depend only on existing members in a cube.</span></span> <span data-ttu-id="01e11-120">導出成員也能以相同 MDX 運算式中定義的其他導出成員為基底。</span><span class="sxs-lookup"><span data-stu-id="01e11-120">Calculated member can also be based on other calculated members defined in the same MDX expression.</span></span> <span data-ttu-id="01e11-121">例如，以下 MDX 查詢使用第一個導出成員 `[Measures].[Special Discount]`中建立的值，來產生第二個導出成員 `[Measures].[Special Discounted Amount]`的值。</span><span class="sxs-lookup"><span data-stu-id="01e11-121">For example, the following MDX query uses the value created in the first calculated member, `[Measures].[Special Discount]`, to generate the value of the second calculated member, `[Measures].[Special Discounted Amount]`.</span></span>  
  
```  
WITH   
   MEMBER [Measures].[Special Discount] AS  
   [Measures].[Discount Percentage] * 1.5,   
   FORMAT_STRING = 'Percent'  
  
   MEMBER [Measures].[Special Discounted Amount] AS  
   [Measures].[Reseller Average Unit Price] * [Measures].[Special Discount],   
   FORMAT_STRING = 'Currency'  
  
SELECT   
   {[Measures].[Special Discount], [Measures].[Special Discounted Amount]} on COLUMNS,  
   NON EMPTY [Product].[Product].MEMBERS  ON Rows  
FROM [Adventure Works]  
WHERE [Product].[Category].[Bikes]  
  
```  
  
## <a name="see-also"></a><span data-ttu-id="01e11-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="01e11-122">See Also</span></span>  
 <span data-ttu-id="01e11-123">[Mdx 函數參考 &#40;MDX&#41;](/sql/mdx/mdx-function-reference-mdx) </span><span class="sxs-lookup"><span data-stu-id="01e11-123">[MDX Function Reference &#40;MDX&#41;](/sql/mdx/mdx-function-reference-mdx) </span></span>  
 <span data-ttu-id="01e11-124">[SELECT 語句 &#40;MDX&#41;](/sql/mdx/mdx-data-manipulation-select) </span><span class="sxs-lookup"><span data-stu-id="01e11-124">[SELECT Statement &#40;MDX&#41;](/sql/mdx/mdx-data-manipulation-select) </span></span>  
 [<span data-ttu-id="01e11-125">建立工作階段範圍導出成員 &#40;MDX&#41;</span><span class="sxs-lookup"><span data-stu-id="01e11-125">Creating Session-Scoped Calculated Members &#40;MDX&#41;</span></span>](mdx-calculated-members-session-scoped-calculated-members.md)  
  
  
