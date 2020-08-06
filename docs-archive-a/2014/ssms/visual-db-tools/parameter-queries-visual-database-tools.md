---
title: 參數查詢 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- parameter queries [SQL Server]
ms.assetid: 4897c41a-324a-47b8-a30b-cbc9e9e19a8b
author: stevestein
ms.author: sstein
ms.openlocfilehash: 7f6fd94ef180a34ae91d52c213092898612dc77d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597496"
---
# <a name="parameter-queries-visual-database-tools"></a><span data-ttu-id="c7e80-102">參數查詢 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="c7e80-102">Parameter Queries (Visual Database Tools)</span></span>
  <span data-ttu-id="c7e80-103">有時候您想要建立可以使用多次的查詢，但每次都使用不同的值。</span><span class="sxs-lookup"><span data-stu-id="c7e80-103">In some cases you want to create a query that you can use many times, but with a different value each time.</span></span> <span data-ttu-id="c7e80-104">例如，您可能經常執行查詢尋找由某位作者所寫的所有 `title_ids` 。</span><span class="sxs-lookup"><span data-stu-id="c7e80-104">For example, you might frequently run a query to find all the `title_ids` written by one author.</span></span> <span data-ttu-id="c7e80-105">除了每次使用的作者 ID 或名稱不同外，每次要求時您可以執行相同的查詢。</span><span class="sxs-lookup"><span data-stu-id="c7e80-105">You could run the same query for each request, except that the author's ID or name would be different each time.</span></span>  
  
 <span data-ttu-id="c7e80-106">若要建立不同時候具有不同值的查詢，您必須在查詢中使用參數。</span><span class="sxs-lookup"><span data-stu-id="c7e80-106">To create a query that can have different values at different times, you use parameters in the query.</span></span> <span data-ttu-id="c7e80-107">參數為一預留位置，執行查詢時提供參數值即可。</span><span class="sxs-lookup"><span data-stu-id="c7e80-107">A parameter is a placeholder for a value that is supplied when the query runs.</span></span> <span data-ttu-id="c7e80-108">使用參數的 SQL 陳述式將如下所示，其中「?」是指作者的 ID 之參數：</span><span class="sxs-lookup"><span data-stu-id="c7e80-108">An SQL statement with a parameter might look like the following, where "?" represents the parameter for the author's ID:</span></span>  
  
```  
SELECT title_id  
FROM titleauthor  
WHERE (au_id = ?)  
```  
  
## <a name="where-you-can-use-parameters"></a><span data-ttu-id="c7e80-109">使用參數的位置</span><span class="sxs-lookup"><span data-stu-id="c7e80-109">Where You Can Use Parameters</span></span>  
 <span data-ttu-id="c7e80-110">您可以使用參數作為常值的預留位置 (不論是文字或數值)。</span><span class="sxs-lookup"><span data-stu-id="c7e80-110">You can use parameters as placeholders for literal values - for either text or numeric values.</span></span> <span data-ttu-id="c7e80-111">通常參數可做為個別資料列或群組的搜尋條件中之預留位置 (即在 SQL 陳述式的 WHERE 或 HAVING 子句中)。</span><span class="sxs-lookup"><span data-stu-id="c7e80-111">Most commonly, parameters are used as placeholders in search conditions for individual rows or for groups (that is, in the WHERE or HAVING clauses of an SQL statement).</span></span>  
  
 <span data-ttu-id="c7e80-112">您可以使用參數當做運算式中的預留位置。</span><span class="sxs-lookup"><span data-stu-id="c7e80-112">You can use parameters as placeholders in expressions.</span></span> <span data-ttu-id="c7e80-113">例如，您可以利用每次執行查詢時都提供不同折扣值來計算折扣價格。</span><span class="sxs-lookup"><span data-stu-id="c7e80-113">For example, you might want to calculate discounted prices by supplying a different discount value each time you run a query.</span></span> <span data-ttu-id="c7e80-114">若要完成這項作業，您可以指定下列運算式：</span><span class="sxs-lookup"><span data-stu-id="c7e80-114">To do so, you could specify the following expression:</span></span>  
  
```  
(price * ?)  
```  
  
## <a name="specifying-unnamed-and-named-parameters"></a><span data-ttu-id="c7e80-115">指定未具名和具名參數</span><span class="sxs-lookup"><span data-stu-id="c7e80-115">Specifying Unnamed and Named Parameters</span></span>  
 <span data-ttu-id="c7e80-116">您可以指定兩種類型的參數：未具名和具名。</span><span class="sxs-lookup"><span data-stu-id="c7e80-116">You can specify two types of parameters: unnamed and named.</span></span> <span data-ttu-id="c7e80-117">未具名參數為問號 (?)，您可以放在查詢中需要提示或取代常值的位置。</span><span class="sxs-lookup"><span data-stu-id="c7e80-117">An unnamed parameter is a question mark (?) that you put anywhere in the query that you want to prompt for or substitute a literal value.</span></span> <span data-ttu-id="c7e80-118">例如，如果使用未具名參數搜尋 `titleauthor` 資料表中的作者 ID， [SQL 窗格](visual-database-tools.md) 中產生的結果陳述式將如下所示：</span><span class="sxs-lookup"><span data-stu-id="c7e80-118">For example, if you use an unnamed parameter to search for an author's id in the `titleauthor` table, the resulting statement in the [SQL Pane](visual-database-tools.md) might look like this:</span></span>  
  
```  
SELECT title_id  
FROM titleauthor  
WHERE (au_id = ?)  
```  
  
 <span data-ttu-id="c7e80-119">當您在 [查詢和檢視表設計工具](query-and-view-designer-tools-visual-database-tools.md)執行查詢時， [查詢參數對話方塊](query-parameters-dialog-box-visual-database-tools.md) 會出現「?」作為參數的名稱。</span><span class="sxs-lookup"><span data-stu-id="c7e80-119">When you run the query in the [Query and View Designer](query-and-view-designer-tools-visual-database-tools.md), the [Query Parameters Dialog Box](query-parameters-dialog-box-visual-database-tools.md) appears with "?" as the name of the parameter.</span></span>  
  
 <span data-ttu-id="c7e80-120">或者您也可以指定參數名稱。</span><span class="sxs-lookup"><span data-stu-id="c7e80-120">Alternatively, you can assign a name to a parameter.</span></span> <span data-ttu-id="c7e80-121">如果查詢中有多個參數，具名參數則特別有用。</span><span class="sxs-lookup"><span data-stu-id="c7e80-121">Named parameters are particularly useful if you have multiple parameters in a query.</span></span> <span data-ttu-id="c7e80-122">例如，如果您使用具名參數在 `authors` 資料表中搜尋作者的名字和姓氏，SQL 窗格中產生的結果陳述式將如下所示：</span><span class="sxs-lookup"><span data-stu-id="c7e80-122">For example, if you use named parameters to search for an author's first and last names in the `authors` table, the resulting statement in the SQL pane might look like this:</span></span>  
  
```  
SELECT au_id  
FROM authors  
WHERE au_fname = %first name% AND  
      au_lname = %last name%  
```  
  
> [!TIP]  
>  <span data-ttu-id="c7e80-123">在建立具名參數查詢之前，必須先定義前置和後置字元。</span><span class="sxs-lookup"><span data-stu-id="c7e80-123">You must define prefix and suffix characters before creating a named parameter query.</span></span>  
  
 <span data-ttu-id="c7e80-124">當您在查詢和檢視表設計工具執行查詢時， [查詢參數對話方塊](query-parameters-dialog-box-visual-database-tools.md) 會出現具名參數清單。</span><span class="sxs-lookup"><span data-stu-id="c7e80-124">When you run the query in the Query and View Designer, the [Query Parameters Dialog Box](query-parameters-dialog-box-visual-database-tools.md) appears with a list of named parameters.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7e80-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c7e80-125">See Also</span></span>  
 <span data-ttu-id="c7e80-126">[使用 &#40;Visual Database Tools&#41;的參數查詢](query-with-parameters-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="c7e80-126">[Query with Parameters &#40;Visual Database Tools&#41;](query-with-parameters-visual-database-tools.md) </span></span>  
 <span data-ttu-id="c7e80-127">[支援的查詢類型 &#40;Visual Database Tools&#41;](supported-query-types-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="c7e80-127">[Supported Query Types &#40;Visual Database Tools&#41;](supported-query-types-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="c7e80-128">設計查詢和檢視使用說明主題 &#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="c7e80-128">Design Queries and Views How-to Topics &#40;Visual Database Tools&#41;</span></span>](design-queries-and-views-how-to-topics-visual-database-tools.md)  
  
  
