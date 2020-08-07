---
title: 更新結果的規則 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- View Designer, Results pane
- updating query results
- Query Designer [SQL Server], Results pane
- Results pane
ms.assetid: de131ef0-ccbd-446f-9400-b93c7b8fa537
author: stevestein
ms.author: sstein
ms.openlocfilehash: 5cc6befc6571f29be95b176f8de6d7dcfaed9108
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703701"
---
# <a name="rules-for-updating-results-visual-database-tools"></a><span data-ttu-id="a59aa-102">更新結果的規格 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="a59aa-102">Rules for Updating Results (Visual Database Tools)</span></span>
  <span data-ttu-id="a59aa-103">大多數的情形下，您可以更新 [結果窗格](visual-database-tools.md)所顯示的結果集。</span><span class="sxs-lookup"><span data-stu-id="a59aa-103">In many cases, you can update the result set displayed in the [Results Pane](visual-database-tools.md).</span></span> <span data-ttu-id="a59aa-104">不過也有些情形無法更新。</span><span class="sxs-lookup"><span data-stu-id="a59aa-104">However, in some cases you cannot.</span></span>  
  
 <span data-ttu-id="a59aa-105">一般說來，為了更新結果， [查詢和檢視表設計工具](query-and-view-designer-tools-visual-database-tools.md) 必須要有足夠的資訊才能唯一識別資料表中的資料列。</span><span class="sxs-lookup"><span data-stu-id="a59aa-105">In general, in order to update results, the [Query and View Designer](query-and-view-designer-tools-visual-database-tools.md) must have sufficient information to uniquely identify the row in the table.</span></span> <span data-ttu-id="a59aa-106">一個例子是輸出清單中的查詢包含主索引鍵。</span><span class="sxs-lookup"><span data-stu-id="a59aa-106">An example is if the query includes a primary key in the output list.</span></span> <span data-ttu-id="a59aa-107">此外，也必須要有足夠的使用權限可更新資料庫。</span><span class="sxs-lookup"><span data-stu-id="a59aa-107">In addition, you must have sufficient permission to update the database.</span></span>  
  
 <span data-ttu-id="a59aa-108">如果查詢以檢視做為依據，可能可以更新。</span><span class="sxs-lookup"><span data-stu-id="a59aa-108">If your query is based on a view, you might be able to update it.</span></span> <span data-ttu-id="a59aa-109">同樣的原則不只套用至檢視本身，但檢視中套用至基礎資料表除外。</span><span class="sxs-lookup"><span data-stu-id="a59aa-109">The same guidelines apply, except that they apply to the underlying tables in the view, not just to the view itself.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a59aa-110">[查詢和檢視設計師] 無法事先判斷以檢視做為依據的結果集是否能更新。</span><span class="sxs-lookup"><span data-stu-id="a59aa-110">The Query and View Designer cannot determine in advance whether you can update a result set based on a view.</span></span> <span data-ttu-id="a59aa-111">因此即使不能更新，也會顯示出所有的檢視。</span><span class="sxs-lookup"><span data-stu-id="a59aa-111">Therefore, it displays all views, even though you might not be able to update them.</span></span>  
  
 <span data-ttu-id="a59aa-112">下表是具體例項的摘要，說明 [結果] 窗格中的查詢結果有的可以、有的不能更新。</span><span class="sxs-lookup"><span data-stu-id="a59aa-112">The following table summarizes specific instances in which you might and might not be able to update query results in the Results pane.</span></span> <span data-ttu-id="a59aa-113">在許多情況下，使用的資料庫會指定查詢結果是否能更新。</span><span class="sxs-lookup"><span data-stu-id="a59aa-113">In many cases, the database you are using dictates whether you can update query results.</span></span>  
  
|<span data-ttu-id="a59aa-114">查詢</span><span class="sxs-lookup"><span data-stu-id="a59aa-114">Query</span></span>|<span data-ttu-id="a59aa-115">結果能否更新？</span><span class="sxs-lookup"><span data-stu-id="a59aa-115">Can results be updated?</span></span>|  
|-----------|-----------------------------|  
|<span data-ttu-id="a59aa-116">查詢是根據輸出清單中有主索引鍵的一份資料表</span><span class="sxs-lookup"><span data-stu-id="a59aa-116">Query based on one table with primary key in the output list</span></span>|<span data-ttu-id="a59aa-117">能 (不含下列清單)。</span><span class="sxs-lookup"><span data-stu-id="a59aa-117">Yes (except as listed below).</span></span>|  
|<span data-ttu-id="a59aa-118">查詢是根據不含唯一索引，也沒有主索引鍵的一份資料表</span><span class="sxs-lookup"><span data-stu-id="a59aa-118">Query based on a table with no unique index and without a primary key</span></span>|<span data-ttu-id="a59aa-119">依照查詢和資料庫而定。</span><span class="sxs-lookup"><span data-stu-id="a59aa-119">Depends on query and database.</span></span> <span data-ttu-id="a59aa-120">如果有足夠的資訊則可單獨識別出記錄，有些資料庫允許更新。</span><span class="sxs-lookup"><span data-stu-id="a59aa-120">Some databases allow updates if sufficient information is available to uniquely identify records.</span></span>|  
|<span data-ttu-id="a59aa-121">查詢是根據未相連結的多份資料表</span><span class="sxs-lookup"><span data-stu-id="a59aa-121">Query based on multiple tables which are not joined</span></span>|<span data-ttu-id="a59aa-122">否。</span><span class="sxs-lookup"><span data-stu-id="a59aa-122">No.</span></span>|  
|<span data-ttu-id="a59aa-123">查詢是根據資料庫中標記為唯讀的資料</span><span class="sxs-lookup"><span data-stu-id="a59aa-123">Query based on data marked as read-only in the database</span></span>|<span data-ttu-id="a59aa-124">否。</span><span class="sxs-lookup"><span data-stu-id="a59aa-124">No.</span></span>|  
|<span data-ttu-id="a59aa-125">查詢是根據一份檢視，牽涉無條件約束 (Constraint) 的一份資料表</span><span class="sxs-lookup"><span data-stu-id="a59aa-125">Query based on a view that involves one table with no constraints</span></span>|<span data-ttu-id="a59aa-126">能 (不含下列清單)。</span><span class="sxs-lookup"><span data-stu-id="a59aa-126">Yes (except as listed below).</span></span>|  
|<span data-ttu-id="a59aa-127">查詢是根據一對一關聯性 (One-To-One Relationship) 所連結的資料表</span><span class="sxs-lookup"><span data-stu-id="a59aa-127">Query based on tables joined with a one-to-one relationship</span></span>|<span data-ttu-id="a59aa-128">能 (不含下列清單)。</span><span class="sxs-lookup"><span data-stu-id="a59aa-128">Yes (except as listed below).</span></span>|  
|<span data-ttu-id="a59aa-129">查詢是根據一對多關聯性 (One-To-Many Relationship) 所連結的資料表</span><span class="sxs-lookup"><span data-stu-id="a59aa-129">Query based on tables joined with a one-to-many relationship</span></span>|<span data-ttu-id="a59aa-130">通常可以。</span><span class="sxs-lookup"><span data-stu-id="a59aa-130">Usually.</span></span>|  
|<span data-ttu-id="a59aa-131">查詢是根據三份以上的資料表，具有多對多關聯性 (Many-To-Many Relationship)</span><span class="sxs-lookup"><span data-stu-id="a59aa-131">Query based on three or more tables in which there is a many-to-many relationship</span></span>|<span data-ttu-id="a59aa-132">否。</span><span class="sxs-lookup"><span data-stu-id="a59aa-132">No.</span></span>|  
|<span data-ttu-id="a59aa-133">查詢是根據未獲得更新使用權限的一份資料表</span><span class="sxs-lookup"><span data-stu-id="a59aa-133">Query based on a table for which update permission is not granted</span></span>|<span data-ttu-id="a59aa-134">可刪除但不能更新。</span><span class="sxs-lookup"><span data-stu-id="a59aa-134">Can delete but not update.</span></span>|  
|<span data-ttu-id="a59aa-135">查詢是根據未獲得刪除使用權限的一份資料表</span><span class="sxs-lookup"><span data-stu-id="a59aa-135">Query based on a table for which delete permission is not granted</span></span>|<span data-ttu-id="a59aa-136">可更新但不能刪除。</span><span class="sxs-lookup"><span data-stu-id="a59aa-136">Can update but not delete.</span></span>|  
|<span data-ttu-id="a59aa-137">彙總查詢 (Aggregate Query)</span><span class="sxs-lookup"><span data-stu-id="a59aa-137">Aggregate query</span></span>|<span data-ttu-id="a59aa-138">否。</span><span class="sxs-lookup"><span data-stu-id="a59aa-138">No.</span></span>|  
|<span data-ttu-id="a59aa-139">查詢是根據包含總計或彙總函式 (Aggregate Function) 的子查詢 (Subquery)</span><span class="sxs-lookup"><span data-stu-id="a59aa-139">Query based on a subquery that contains totals or aggregate functions</span></span>|<span data-ttu-id="a59aa-140">否。</span><span class="sxs-lookup"><span data-stu-id="a59aa-140">No.</span></span>|  
|<span data-ttu-id="a59aa-141">查詢包含有 DISTINCT 關鍵字，以排除重複的資料列</span><span class="sxs-lookup"><span data-stu-id="a59aa-141">Query that includes the DISTINCT keyword to exclude duplicate rows</span></span>|<span data-ttu-id="a59aa-142">否。</span><span class="sxs-lookup"><span data-stu-id="a59aa-142">No.</span></span>|  
|<span data-ttu-id="a59aa-143">查詢的 FROM 子句包含使用者自訂的函數，可傳回資料表，而且此使用者自訂的函數並包含多選陳述式</span><span class="sxs-lookup"><span data-stu-id="a59aa-143">Query whose FROM clause includes a user-defined function that returns a table and the user-defined function contains multiple select statements</span></span>|<span data-ttu-id="a59aa-144">否。</span><span class="sxs-lookup"><span data-stu-id="a59aa-144">No.</span></span>|  
|<span data-ttu-id="a59aa-145">查詢的 FROM 子句包含使用者自訂的內嵌 (Inline) 函數</span><span class="sxs-lookup"><span data-stu-id="a59aa-145">Query whose FROM clause includes an inline user-defined function</span></span>|<span data-ttu-id="a59aa-146">是。</span><span class="sxs-lookup"><span data-stu-id="a59aa-146">Yes.</span></span>|  
  
 <span data-ttu-id="a59aa-147">此外，查詢結果中可能有特定的資料行無法更新。</span><span class="sxs-lookup"><span data-stu-id="a59aa-147">In addition, you might not be able to update specific columns in the query results.</span></span> <span data-ttu-id="a59aa-148">以下的清單是資料行特定類型的摘要，[結果] 窗格不能更新。</span><span class="sxs-lookup"><span data-stu-id="a59aa-148">The following list summarizes specific types of columns that you cannot update in the Results pane.</span></span>  
  
-   <span data-ttu-id="a59aa-149">資料行是根據運算式</span><span class="sxs-lookup"><span data-stu-id="a59aa-149">Columns based on expressions</span></span>  
  
-   <span data-ttu-id="a59aa-150">資料行是根據純量的使用者自訂函數</span><span class="sxs-lookup"><span data-stu-id="a59aa-150">Columns based on scalar user-defined functions</span></span>  
  
-   <span data-ttu-id="a59aa-151">資料列或資料行由其他使用者刪除</span><span class="sxs-lookup"><span data-stu-id="a59aa-151">Rows or columns deleted by another user</span></span>  
  
-   <span data-ttu-id="a59aa-152">資料列或資料行由其他使用者鎖定 (鎖定的資料列通常解除鎖定即可更新)</span><span class="sxs-lookup"><span data-stu-id="a59aa-152">Rows or columns locked by another user (locked rows can usually be updated as soon as they are unlocked)</span></span>  
  
-   <span data-ttu-id="a59aa-153">時間戳記或 BLOB 資料行</span><span class="sxs-lookup"><span data-stu-id="a59aa-153">Timestamp or BLOB columns</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a59aa-154">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a59aa-154">See Also</span></span>  
 [<span data-ttu-id="a59aa-155">設計查詢和檢視使用說明主題 &#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="a59aa-155">Design Queries and Views How-to Topics &#40;Visual Database Tools&#41;</span></span>](design-queries-and-views-how-to-topics-visual-database-tools.md)  
  
  
