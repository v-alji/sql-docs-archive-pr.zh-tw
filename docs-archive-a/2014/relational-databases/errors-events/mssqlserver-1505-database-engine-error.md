---
title: MSSQLSERVER_1505 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 1505 (Database Engine error)
ms.assetid: ef4df75d-0f36-4c8b-b36c-e427f65f91ca
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 74c152404cf2d3710bbe98b29da7a96d86f58859
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87698278"
---
# <a name="mssqlserver_1505"></a><span data-ttu-id="1f65b-102">MSSQLSERVER_1505</span><span class="sxs-lookup"><span data-stu-id="1f65b-102">MSSQLSERVER_1505</span></span>
    
## <a name="details"></a><span data-ttu-id="1f65b-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="1f65b-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="1f65b-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="1f65b-104">Product Name</span></span>|<span data-ttu-id="1f65b-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="1f65b-105">SQL Server</span></span>|  
|<span data-ttu-id="1f65b-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="1f65b-106">Event ID</span></span>|<span data-ttu-id="1f65b-107">1505</span><span class="sxs-lookup"><span data-stu-id="1f65b-107">1505</span></span>|  
|<span data-ttu-id="1f65b-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="1f65b-108">Event Source</span></span>|<span data-ttu-id="1f65b-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="1f65b-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="1f65b-110">元件</span><span class="sxs-lookup"><span data-stu-id="1f65b-110">Component</span></span>|<span data-ttu-id="1f65b-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="1f65b-111">SQLEngine</span></span>|  
|<span data-ttu-id="1f65b-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="1f65b-112">Symbolic Name</span></span>|<span data-ttu-id="1f65b-113">DUP_KEY</span><span class="sxs-lookup"><span data-stu-id="1f65b-113">DUP_KEY</span></span>|  
|<span data-ttu-id="1f65b-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="1f65b-114">Message Text</span></span>|<span data-ttu-id="1f65b-115">發現物件名稱 '%.\*ls' 和索引名稱 '%.\*ls' 的重複索引鍵，CREATE UNIQUE INDEX 已結束。</span><span class="sxs-lookup"><span data-stu-id="1f65b-115">CREATE UNIQUE INDEX terminated because a duplicate key was found for object name '%.\*ls' and index name '%.\*ls'.</span></span>  <span data-ttu-id="1f65b-116">重複的索引鍵值為 %ls。</span><span class="sxs-lookup"><span data-stu-id="1f65b-116">The duplicate key value is %ls.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="1f65b-117">說明</span><span class="sxs-lookup"><span data-stu-id="1f65b-117">Explanation</span></span>  
 <span data-ttu-id="1f65b-118">當您嘗試建立唯一索引，而且資料表中的多個資料列包含指定的重複值時，就會發生這項錯誤。</span><span class="sxs-lookup"><span data-stu-id="1f65b-118">This error occurs when you attempt to create a unique index and more than one row in the table contains the specified duplicate value.</span></span> <span data-ttu-id="1f65b-119">當您建立索引並指定 UNIQUE 關鍵字，或者建立 UNIQUE 條件約束時，就會建立唯一索引。</span><span class="sxs-lookup"><span data-stu-id="1f65b-119">A unique index is created when you create an index and specify the UNIQUE keyword, or when you create a UNIQUE constraint.</span></span> <span data-ttu-id="1f65b-120">資料表無法包含在索引或條件約束中定義的資料行內具有重複值的任何資料列。</span><span class="sxs-lookup"><span data-stu-id="1f65b-120">The table cannot contain any rows that have duplicate values in the columns defined in the index or constraint.</span></span>  
  
 <span data-ttu-id="1f65b-121">請考慮下列 **Employee** 資料表中的資料：</span><span class="sxs-lookup"><span data-stu-id="1f65b-121">Consider the data in the following **Employee** table:</span></span>  
  
|<span data-ttu-id="1f65b-122">姓氏</span><span class="sxs-lookup"><span data-stu-id="1f65b-122">LastName</span></span>|<span data-ttu-id="1f65b-123">名字</span><span class="sxs-lookup"><span data-stu-id="1f65b-123">FirstName</span></span>|<span data-ttu-id="1f65b-124">JobTitle</span><span class="sxs-lookup"><span data-stu-id="1f65b-124">JobTitle</span></span>|<span data-ttu-id="1f65b-125">HireDate</span><span class="sxs-lookup"><span data-stu-id="1f65b-125">HireDate</span></span>|  
|--------------|---------------|--------------|--------------|  
|<span data-ttu-id="1f65b-126">Walters</span><span class="sxs-lookup"><span data-stu-id="1f65b-126">Walters</span></span>|<span data-ttu-id="1f65b-127">Rob</span><span class="sxs-lookup"><span data-stu-id="1f65b-127">Rob</span></span>|<span data-ttu-id="1f65b-128">Senior Tool Designer</span><span class="sxs-lookup"><span data-stu-id="1f65b-128">Senior Tool Designer</span></span>|<span data-ttu-id="1f65b-129">2004-11-19</span><span class="sxs-lookup"><span data-stu-id="1f65b-129">2004-11-19</span></span>|  
|<span data-ttu-id="1f65b-130">Brown</span><span class="sxs-lookup"><span data-stu-id="1f65b-130">Brown</span></span>|<span data-ttu-id="1f65b-131">Kevin</span><span class="sxs-lookup"><span data-stu-id="1f65b-131">Kevin</span></span>|<span data-ttu-id="1f65b-132">Marketing Assistant</span><span class="sxs-lookup"><span data-stu-id="1f65b-132">Marketing Assistant</span></span>|<span data-ttu-id="1f65b-133">NULL</span><span class="sxs-lookup"><span data-stu-id="1f65b-133">NULL</span></span>|  
|<span data-ttu-id="1f65b-134">Brown</span><span class="sxs-lookup"><span data-stu-id="1f65b-134">Brown</span></span>|<span data-ttu-id="1f65b-135">Jo</span><span class="sxs-lookup"><span data-stu-id="1f65b-135">Jo</span></span>|<span data-ttu-id="1f65b-136">Design Engineer</span><span class="sxs-lookup"><span data-stu-id="1f65b-136">Design Engineer</span></span>|<span data-ttu-id="1f65b-137">NULL</span><span class="sxs-lookup"><span data-stu-id="1f65b-137">NULL</span></span>|  
|<span data-ttu-id="1f65b-138">Walters</span><span class="sxs-lookup"><span data-stu-id="1f65b-138">Walters</span></span>|<span data-ttu-id="1f65b-139">Rob</span><span class="sxs-lookup"><span data-stu-id="1f65b-139">Rob</span></span>|<span data-ttu-id="1f65b-140">Tool Designer</span><span class="sxs-lookup"><span data-stu-id="1f65b-140">Tool Designer</span></span>|<span data-ttu-id="1f65b-141">2001-08-09</span><span class="sxs-lookup"><span data-stu-id="1f65b-141">2001-08-09</span></span>|  
  
 <span data-ttu-id="1f65b-142">由於資料列含有重複值，因此無法在資料行組合 **LastName** 或 **LastName**、**FirstName** 上建立唯一索引。</span><span class="sxs-lookup"><span data-stu-id="1f65b-142">A unique index can not be created on the column combinations **LastName** or **LastName**, **FirstName** because of duplicate values in the rows.</span></span>  
  
 <span data-ttu-id="1f65b-143">**HireDate** 資料行違反唯一性的可能較不明顯。</span><span class="sxs-lookup"><span data-stu-id="1f65b-143">Less obvious is the potential for a uniqueness violation in the **HireDate** column.</span></span> <span data-ttu-id="1f65b-144">執行索引時，NULL 值會當做相等值進行比較。</span><span class="sxs-lookup"><span data-stu-id="1f65b-144">For indexing purposes, NULL values compare as equal.</span></span> <span data-ttu-id="1f65b-145">因此，如果有多個資料行中的索引鍵值為 NULL，您就無法建立唯一索引或條件約束。</span><span class="sxs-lookup"><span data-stu-id="1f65b-145">Therefore, you cannot create a unique index or constraint if the key values are NULL in more than one row.</span></span> <span data-ttu-id="1f65b-146">基於上述資料，因此您無法在資料行組合 **HireDate** 或 **LastName**、**HireDate** 上建立唯一索引。</span><span class="sxs-lookup"><span data-stu-id="1f65b-146">Given the data above, a unique index cannot be created on the column combinations **HireDate** or **LastName**, **HireDate**.</span></span>  
  
 <span data-ttu-id="1f65b-147">錯誤訊息 1505 會傳回違反唯一性條件約束的第一個資料列。</span><span class="sxs-lookup"><span data-stu-id="1f65b-147">Error message 1505 returns the first row that violates the uniqueness constraint.</span></span> <span data-ttu-id="1f65b-148">資料表可能含有其他重複的資料列。</span><span class="sxs-lookup"><span data-stu-id="1f65b-148">There may be other duplicate rows in the table.</span></span> <span data-ttu-id="1f65b-149">若要尋找所有重複的資料列，請查詢指定的資料表並使用 GROUP BY 和 HAVING 子句來報告重複的資料列。</span><span class="sxs-lookup"><span data-stu-id="1f65b-149">To find all duplicate rows, query the specified table and use the GROUP BY and HAVING clauses to report the duplicate rows.</span></span> <span data-ttu-id="1f65b-150">例如，下列查詢會傳回 **Employee** 資料表中具有重複名字和姓氏的資料列。</span><span class="sxs-lookup"><span data-stu-id="1f65b-150">For example, the following query returns the rows in the **Employee** table that have duplicate first and last names.</span></span>  
  
 <span data-ttu-id="1f65b-151">從 dbo 選取 [LastName]、[FirstName]、[count (] \*) 。員工群組依據 LastName、FirstName 的計數 (\*) > 1;</span><span class="sxs-lookup"><span data-stu-id="1f65b-151">SELECT LastName, FirstName, count(\*) FROM dbo.Employee GROUP BY LastName, FirstName HAVING count(\*) > 1;</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="1f65b-152">使用者動作</span><span class="sxs-lookup"><span data-stu-id="1f65b-152">User Action</span></span>  
 <span data-ttu-id="1f65b-153">請考慮下列解決方案。</span><span class="sxs-lookup"><span data-stu-id="1f65b-153">Consider the following solutions.</span></span>  
  
-   <span data-ttu-id="1f65b-154">在索引或條件約束定義中加入或移除資料行，以便建立唯一複合索引。</span><span class="sxs-lookup"><span data-stu-id="1f65b-154">Add or remove columns in the index or constraint definition to create a unique composite.</span></span> <span data-ttu-id="1f65b-155">在上述範例中，於索引或條件約束定義中新增 **MiddleName** 資料行，應該就可以解決重複值的問題。</span><span class="sxs-lookup"><span data-stu-id="1f65b-155">In the previous example, adding a **MiddleName** column to the index or constraint definition might resolve the duplication problem.</span></span>  
  
-   <span data-ttu-id="1f65b-156">當您選擇唯一索引或條件約束的資料行時，請選取已定義為 NOT NULL 的資料行。</span><span class="sxs-lookup"><span data-stu-id="1f65b-156">Select columns that are defined as NOT NULL when you choose columns for a unique index or constraint.</span></span> <span data-ttu-id="1f65b-157">這樣做可以排除多個資料列的索引鍵值包含 NULL 而導致違反唯一性的可能。</span><span class="sxs-lookup"><span data-stu-id="1f65b-157">This eliminates the possibility of a uniqueness violation caused when more than one row contains NULL in the key values.</span></span>  
  
-   <span data-ttu-id="1f65b-158">若重複值是因資料輸入錯誤所造成，請手動更正資料，然後再建立索引或約束條件。</span><span class="sxs-lookup"><span data-stu-id="1f65b-158">If the duplicate values are the result of data entry errors, manually correct the data and then create the index or constraint.</span></span> <span data-ttu-id="1f65b-159">如需有關移除資料表中重複資料列的資訊，請參閱知識庫文件 139444：[如何在 SQL Server 中移除資料表中的重複資料列](https://support.microsoft.com/kb/139444) \(英文\)。</span><span class="sxs-lookup"><span data-stu-id="1f65b-159">For information about removing duplicate rows in a table, see Knowledge Base article 139444: [How to remove duplicate rows from a table in SQL Server](https://support.microsoft.com/kb/139444).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f65b-160">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1f65b-160">See Also</span></span>  
 <span data-ttu-id="1f65b-161">[CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="1f65b-161">[CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql) </span></span>  
 <span data-ttu-id="1f65b-162">[建立唯一索引](../indexes/indexes.md) </span><span class="sxs-lookup"><span data-stu-id="1f65b-162">[Create Unique Indexes](../indexes/indexes.md) </span></span>  
 [<span data-ttu-id="1f65b-163">建立唯一的條件約束</span><span class="sxs-lookup"><span data-stu-id="1f65b-163">Create Unique Constraints</span></span>](../tables/create-unique-constraints.md)  
  
  
