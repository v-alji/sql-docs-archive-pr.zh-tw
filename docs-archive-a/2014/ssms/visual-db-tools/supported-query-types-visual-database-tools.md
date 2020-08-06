---
title: 支援的查詢類型 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- Delete query
- queries [SQL Server], types
- Update query
- Query Designer [SQL Server], query types
- Criteria pane
- Insert Values query
- Select query
- Make Table query
- Insert Results query
- Diagram pane [Visual Database Tools]
- View Designer, query types
ms.assetid: 72b9116c-c128-4078-a78d-257a2955a3f6
author: stevestein
ms.author: sstein
ms.openlocfilehash: b00b7018fc6d0b631696811bd1870e09842b4162
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704614"
---
# <a name="supported-query-types-visual-database-tools"></a><span data-ttu-id="30e7c-102">支援的查詢類型 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="30e7c-102">Supported Query Types (Visual Database Tools)</span></span>
  <span data-ttu-id="30e7c-103">在 [查詢和檢視表設計工具](visual-database-tools.md)的 [圖表] 和 [準則] 窗格 (圖形窗格) 中，您可以建立下列查詢類型：</span><span class="sxs-lookup"><span data-stu-id="30e7c-103">You can create the following types of queries in the Diagram and Criteria panes (the graphical panes) of the [Query and View Designer](visual-database-tools.md):</span></span>  
  
-   <span data-ttu-id="30e7c-104">**選取查詢** ：從一或多個資料表或檢視擷取資料。</span><span class="sxs-lookup"><span data-stu-id="30e7c-104">**Select query** Retrieves data from one or more tables or views.</span></span> <span data-ttu-id="30e7c-105">此類查詢將建立 SQL SELECT 陳述式。</span><span class="sxs-lookup"><span data-stu-id="30e7c-105">This type of query creates an SQL SELECT statement.</span></span>  
  
-   <span data-ttu-id="30e7c-106">**插入結果** ：將一個資料表的現有資料列複製到另一個資料表，或複製到同一個資料表中做為新的資料列，以建立新的資料列。</span><span class="sxs-lookup"><span data-stu-id="30e7c-106">**Insert Results** Creates new rows by copying existing rows from one table into another, or into the same table as new rows.</span></span> <span data-ttu-id="30e7c-107">此類查詢將建立 SQL INSERT INTO...SELECT 陳述式。</span><span class="sxs-lookup"><span data-stu-id="30e7c-107">This type of query creates an SQL INSERT INTO...SELECT statement.</span></span>  
  
-   <span data-ttu-id="30e7c-108">**插入值** ：建立新資料列，並將新值插入至指定的資料行。</span><span class="sxs-lookup"><span data-stu-id="30e7c-108">**Insert Values** Creates a new row and inserts values into specified columns.</span></span> <span data-ttu-id="30e7c-109">此類查詢將建立 SQL INSERT INTO...VALUES 陳述式。</span><span class="sxs-lookup"><span data-stu-id="30e7c-109">This type of query creates an SQL INSERT INTO...VALUES statement.</span></span>  
  
-   <span data-ttu-id="30e7c-110">**更新查詢** ：變更資料表中一或多個現有資料列中的個別資料行值。</span><span class="sxs-lookup"><span data-stu-id="30e7c-110">**Update query** Changes the values of individual columns in one or more existing rows in a table.</span></span> <span data-ttu-id="30e7c-111">此類查詢會建立 SQL UPDATE...SET 陳述式。</span><span class="sxs-lookup"><span data-stu-id="30e7c-111">This type of query creates an SQL UPDATE...SET statement.</span></span>  
  
-   <span data-ttu-id="30e7c-112">**刪除查詢** ：從資料表移除一或多個資料列。</span><span class="sxs-lookup"><span data-stu-id="30e7c-112">**Delete query** Removes one or more rows from a table.</span></span> <span data-ttu-id="30e7c-113">這類查詢將建立 SQL DELETE 陳述式。</span><span class="sxs-lookup"><span data-stu-id="30e7c-113">This type of query creates an SQL DELETE statement.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="30e7c-114">[刪除查詢] 會刪除資料表中的整個資料列。</span><span class="sxs-lookup"><span data-stu-id="30e7c-114">A Delete query removes entire rows from the table.</span></span> <span data-ttu-id="30e7c-115">如果您要刪除個別的資料欄值，請使用 UPDATE 查詢。</span><span class="sxs-lookup"><span data-stu-id="30e7c-115">If you want to delete values from individual data columns, use an Update query.</span></span>  
  
-   <span data-ttu-id="30e7c-116">**製成資料表查詢** ：建立新資料表，並且將查詢結果複製到該新資料表中來建立資料列。</span><span class="sxs-lookup"><span data-stu-id="30e7c-116">**Make Table query** Creates a new table and creates rows in it by copying the results of a query into it.</span></span> <span data-ttu-id="30e7c-117">此類查詢將建立 SQL SELECT...INTO 陳述式。</span><span class="sxs-lookup"><span data-stu-id="30e7c-117">This type of query creates an SQL SELECT...INTO statement.</span></span>  
  
 <span data-ttu-id="30e7c-118">除了使用圖形窗格來建立查詢外，您可以將任何 SQL 陳述式輸入 SQL 窗格，如聯合查詢 (Union Query)。</span><span class="sxs-lookup"><span data-stu-id="30e7c-118">In addition to the queries you can create using the graphical panes, you can enter any SQL statement into the SQL pane, such as Union queries.</span></span>  
  
 <span data-ttu-id="30e7c-119">當您使用 SQL 陳述式建立的查詢無法在圖形窗格顯示時，查詢和檢視設計師將使這些窗格變成暗灰色，表示他們無法反映您所建立的查詢。</span><span class="sxs-lookup"><span data-stu-id="30e7c-119">When you create queries using SQL statements that cannot be represented in the graphical panes, the Query and View Designer dims those panes to indicate that they do not reflect the query you are creating.</span></span> <span data-ttu-id="30e7c-120">但這些暗灰色的窗格仍處於作用中狀態，而且在許多情況下，您可以在這些窗格中變更查詢。</span><span class="sxs-lookup"><span data-stu-id="30e7c-120">However, the dimmed panes are still active and, in many cases, you can make changes to the query in those panes.</span></span> <span data-ttu-id="30e7c-121">如果您的變更使得圖形窗格可以顯示查詢，這些窗格就不再是暗灰色了。</span><span class="sxs-lookup"><span data-stu-id="30e7c-121">If the changes you make result in a query that can be represented in the graphical panes, those panes are no longer dimmed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30e7c-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="30e7c-122">See Also</span></span>  
 <span data-ttu-id="30e7c-123">[設計查詢和觀看 how to 主題 &#40;Visual Database Tools&#41;](design-queries-and-views-how-to-topics-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="30e7c-123">[Design Queries and Views How-to Topics &#40;Visual Database Tools&#41;](design-queries-and-views-how-to-topics-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="30e7c-124">查詢的類型 &#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="30e7c-124">Types of Queries &#40;Visual Database Tools&#41;</span></span>](types-of-queries-visual-database-tools.md)  
  
  
