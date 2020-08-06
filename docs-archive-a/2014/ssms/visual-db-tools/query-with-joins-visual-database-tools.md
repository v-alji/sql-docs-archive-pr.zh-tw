---
title: 使用聯結進行查詢 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- queries [Visual Database Tools]
- View Designer, joins
- table joins [SQL Server]
- multiple table joins
- Visual Database Tools [SQL Server], queries
- Query Designer [SQL Server], joins
- joins [SQL Server], queries
ms.assetid: 8f068207-d777-4e64-8c4c-d821f0ddb450
author: stevestein
ms.author: sstein
ms.openlocfilehash: 9d0053e6786d96508be8a87347cdc0b19975a3fe
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688394"
---
# <a name="query-with-joins-visual-database-tools"></a><span data-ttu-id="fb440-102">使用聯結進行查詢 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="fb440-102">Query with Joins (Visual Database Tools)</span></span>
  <span data-ttu-id="fb440-103">查詢結果可包含來自多個資料表或表格值物件的資料。</span><span class="sxs-lookup"><span data-stu-id="fb440-103">A query result can include data from multiple tables or table-valued objects.</span></span> <span data-ttu-id="fb440-104">若要結合來自多個資料表值物件的資料，請使用 SQL 的 JOIN 作業。</span><span class="sxs-lookup"><span data-stu-id="fb440-104">To combine data from multiple table-valued objects, you use the JOIN operation from SQL.</span></span>  
  
 <span data-ttu-id="fb440-105">如需使用多個資料表建立查詢的詳細資訊，請參閱下列主題。</span><span class="sxs-lookup"><span data-stu-id="fb440-105">For information about creating queries using multiple tables, see the following topics.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="fb440-106">本節內容</span><span class="sxs-lookup"><span data-stu-id="fb440-106">In This Section</span></span>  
 [<span data-ttu-id="fb440-107">修改聯結運算子 &#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="fb440-107">Modify Join Operators &#40;Visual Database Tools&#41;</span></span>](visual-database-tools.md)  
 <span data-ttu-id="fb440-108">使用等號 (=) 以外的運算子來指定應該聯結資料表。</span><span class="sxs-lookup"><span data-stu-id="fb440-108">Specify that tables should be joined using an operator other than equal (=).</span></span>  
  
 [<span data-ttu-id="fb440-109">查詢和檢視表設計工具表示聯結的方式 &#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="fb440-109">How the Query and View Designer Represents Joins &#40;Visual Database Tools&#41;</span></span>](how-the-query-and-view-designer-represents-joins-visual-database-tools.md)  
 <span data-ttu-id="fb440-110">解釋您在 [圖表] 窗格所看到的聯結圖形表示。</span><span class="sxs-lookup"><span data-stu-id="fb440-110">Explains the graphic representation of the join as you see it in the Diagram pane.</span></span>  
  
 [<span data-ttu-id="fb440-111">自動聯結資料表 &#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="fb440-111">Join Tables Automatically &#40;Visual Database Tools&#41;</span></span>](join-tables-automatically-visual-database-tools.md)  
 <span data-ttu-id="fb440-112">讓 [查詢和檢視設計師] 判斷資料表是否應該聯結的步驟。</span><span class="sxs-lookup"><span data-stu-id="fb440-112">Steps for allowing the Query and View Designer determine if tables should be joined.</span></span>  
  
 [<span data-ttu-id="fb440-113">手動聯結資料表 &#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="fb440-113">Join Tables Manually &#40;Visual Database Tools&#41;</span></span>](join-tables-manually-visual-database-tools.md)  
 <span data-ttu-id="fb440-114">在 [圖表] 窗格中手動建立聯結的步驟。</span><span class="sxs-lookup"><span data-stu-id="fb440-114">Steps for creating a join manually in the Diagram pane.</span></span>  
  
 [<span data-ttu-id="fb440-115">以多個資料行聯結資料表 &#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="fb440-115">Join Tables on Multiple Columns &#40;Visual Database Tools&#41;</span></span>](join-tables-on-multiple-columns-visual-database-tools.md)  
 <span data-ttu-id="fb440-116">針對每個資料表使用多個準則聯結資料表的步驟。</span><span class="sxs-lookup"><span data-stu-id="fb440-116">Steps for joining tables with multiple criteria for each table.</span></span>  
  
 [<span data-ttu-id="fb440-117">建立外部聯結 &#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="fb440-117">Create Outer Joins &#40;Visual Database Tools&#41;</span></span>](create-outer-joins-visual-database-tools.md)  
 <span data-ttu-id="fb440-118">指定聯結的資料表應該包含資料列，即使它們與對應的資料表中的資料列不符時也一樣。</span><span class="sxs-lookup"><span data-stu-id="fb440-118">Specify that joined tables should include rows even when they do not match rows in the corresponding table.</span></span>  
  
 [<span data-ttu-id="fb440-119">移除聯結 &#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="fb440-119">Remove Joins &#40;Visual Database Tools&#41;</span></span>](remove-joins-visual-database-tools.md)  
 <span data-ttu-id="fb440-120">移除資料表之間聯結的步驟。</span><span class="sxs-lookup"><span data-stu-id="fb440-120">Steps for removing a join between tables.</span></span>  
  
 [<span data-ttu-id="fb440-121">自動建立自我聯結 &#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="fb440-121">Create Self-Joins Automatically &#40;Visual Database Tools&#41;</span></span>](create-self-joins-automatically-visual-database-tools.md)  
 <span data-ttu-id="fb440-122">允許 [查詢和檢視設計師] 建立自我聯結 (Self-Join) 的步驟。</span><span class="sxs-lookup"><span data-stu-id="fb440-122">Steps for allowing the Query and View Designer to create a self-join.</span></span>  
  
 [<span data-ttu-id="fb440-123">手動建立自我聯結 &#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="fb440-123">Create Self-Joins Manually &#40;Visual Database Tools&#41;</span></span>](create-self-joins-manually-visual-database-tools.md)  
 <span data-ttu-id="fb440-124">使用聯結尋找單一資料表中資料子集合的步驟。</span><span class="sxs-lookup"><span data-stu-id="fb440-124">Steps for using a join to find subsets of data within a single table.</span></span>  
  
 [<span data-ttu-id="fb440-125">檢視聯結屬性 &#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="fb440-125">View Join Properties &#40;Visual Database Tools&#41;</span></span>](view-join-properties-visual-database-tools.md)  
 <span data-ttu-id="fb440-126">檢視聯結屬性的步驟</span><span class="sxs-lookup"><span data-stu-id="fb440-126">Steps for viewing the properties of a join.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="fb440-127">相關章節</span><span class="sxs-lookup"><span data-stu-id="fb440-127">Related Sections</span></span>  
 [<span data-ttu-id="fb440-128">查詢的類型 &#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="fb440-128">Types of Queries &#40;Visual Database Tools&#41;</span></span>](types-of-queries-visual-database-tools.md)  
 <span data-ttu-id="fb440-129">提供描述支援的查詢類型之主題的連結。</span><span class="sxs-lookup"><span data-stu-id="fb440-129">Provides links to topics describing the supported query types.</span></span>  
  
 [<span data-ttu-id="fb440-130">使用查詢執行基本作業 &#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="fb440-130">Perform Basic Operations with Queries &#40;Visual Database Tools&#41;</span></span>](perform-basic-operations-with-queries-visual-database-tools.md)  
 <span data-ttu-id="fb440-131">提供包含大部份常見查詢工作之主題的連結。</span><span class="sxs-lookup"><span data-stu-id="fb440-131">Provides links to topics covering the most common query tasks.</span></span>  
  
 [<span data-ttu-id="fb440-132">指定搜尋準則 &#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="fb440-132">Specify Search Criteria &#40;Visual Database Tools&#41;</span></span>](specify-search-criteria-visual-database-tools.md)  
 <span data-ttu-id="fb440-133">提供包含各種搜尋準則以及如何使用之主題的連結。</span><span class="sxs-lookup"><span data-stu-id="fb440-133">Provides links to topics covering the various kinds of search criteria and how to use them.</span></span>  
  
  
