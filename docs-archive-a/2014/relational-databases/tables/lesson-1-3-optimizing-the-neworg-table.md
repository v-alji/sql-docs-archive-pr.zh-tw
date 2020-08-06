---
title: 最佳化 NewOrg 資料表 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- optimizing tables
ms.assetid: 89ff6d37-94c0-4773-8be9-dde943fff023
author: stevestein
ms.author: sstein
ms.openlocfilehash: 39c09a3a73051e7a61f3a62a125232d83d1570c0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584341"
---
# <a name="optimizing-the-neworg-table"></a><span data-ttu-id="b2a98-102">最佳化 NewOrg 資料表</span><span class="sxs-lookup"><span data-stu-id="b2a98-102">Optimizing the NewOrg Table</span></span>
  <span data-ttu-id="b2a98-103">您在[使用現有的階層式資料填入資料表](lesson-1-2-populating-a-table-with-existing-hierarchical-data.md)工作中建立的**NewOrd**資料表包含所有員工資訊，並使用資料類型代表階層式結構 `hierarchyid` 。</span><span class="sxs-lookup"><span data-stu-id="b2a98-103">The **NewOrd** table that you created in the [Populating a Table with Existing Hierarchical Data](lesson-1-2-populating-a-table-with-existing-hierarchical-data.md) task contains all the employee information, and represents the hierarchical structure by using a `hierarchyid` data type.</span></span> <span data-ttu-id="b2a98-104">此工作會加入新索引以支援在 `hierarchyid` 資料行上進行搜尋。</span><span class="sxs-lookup"><span data-stu-id="b2a98-104">This task adds new indexes to support searches on the `hierarchyid` column.</span></span>  
  
## <a name="clustered-index"></a><span data-ttu-id="b2a98-105">叢集索引</span><span class="sxs-lookup"><span data-stu-id="b2a98-105">Clustered Index</span></span>  
 <span data-ttu-id="b2a98-106">資料 `hierarchyid` 行 (**OrgNode**) 是**NewOrg**資料表的主要索引鍵。</span><span class="sxs-lookup"><span data-stu-id="b2a98-106">The `hierarchyid` column (**OrgNode**) is the primary key for the **NewOrg** table.</span></span> <span data-ttu-id="b2a98-107">建立資料表時，它包含名為 **PK_NewOrg_OrgNode** 的叢集索引以強制 **OrgNode** 資料行的唯一性。</span><span class="sxs-lookup"><span data-stu-id="b2a98-107">When the table was created, it contained a clustered index named **PK_NewOrg_OrgNode** to enforce the uniqueness of the **OrgNode** column.</span></span> <span data-ttu-id="b2a98-108">此叢集索引也支援深度優先的資料表搜尋。</span><span class="sxs-lookup"><span data-stu-id="b2a98-108">This clustered index also supports a depth-first search of the table.</span></span>  
  
## <a name="nonclustered-index"></a><span data-ttu-id="b2a98-109">非叢集索引</span><span class="sxs-lookup"><span data-stu-id="b2a98-109">Nonclustered Index</span></span>  
 <span data-ttu-id="b2a98-110">此步驟會建立兩個非叢集索引來支援一般搜尋。</span><span class="sxs-lookup"><span data-stu-id="b2a98-110">This step creates two nonclustered indexes to support typical searches.</span></span>  
  
#### <a name="to-index-the-neworg-table-for-efficient-searches"></a><span data-ttu-id="b2a98-111">建立 NewOrg 資料表的索引以便進行有效率的搜尋</span><span class="sxs-lookup"><span data-stu-id="b2a98-111">To index the NewOrg table for efficient searches</span></span>  
  
1.  <span data-ttu-id="b2a98-112">為協助在階層的相同層級進行查詢，使用 [GetLevel](/sql/t-sql/data-types/getlevel-database-engine) 方法來建立階層中包含層級的計算資料行。</span><span class="sxs-lookup"><span data-stu-id="b2a98-112">To help queries at the same level in the hierarchy, use the [GetLevel](/sql/t-sql/data-types/getlevel-database-engine) method to create a computed column that contains the level in the hierarchy.</span></span> <span data-ttu-id="b2a98-113">然後，在層級和 `Hierarchyid` 上建立複合式索引。</span><span class="sxs-lookup"><span data-stu-id="b2a98-113">Then, create a composite index on the level and the `Hierarchyid`.</span></span> <span data-ttu-id="b2a98-114">執行下列程式碼以建立計算資料行和廣度優先的索引：</span><span class="sxs-lookup"><span data-stu-id="b2a98-114">Run the following code to create the computed column and the breadth-first index:</span></span>  
  
    ```  
    ALTER TABLE NewOrg   
       ADD H_Level AS OrgNode.GetLevel() ;  
    CREATE UNIQUE INDEX EmpBFInd   
       ON NewOrg(H_Level, OrgNode) ;  
    GO  
    ```  
  
2.  <span data-ttu-id="b2a98-115">在 **EmployeeID** 資料行上建立唯一的索引。</span><span class="sxs-lookup"><span data-stu-id="b2a98-115">Create a unique index on the **EmployeeID** column.</span></span> <span data-ttu-id="b2a98-116">這是依 **EmployeeID** 號碼之單一員工的傳統單一查閱。</span><span class="sxs-lookup"><span data-stu-id="b2a98-116">This is the traditional singleton lookup of a single employee by **EmployeeID** number.</span></span> <span data-ttu-id="b2a98-117">執行下列程式碼，在 **EmployeeID**上建立索引：</span><span class="sxs-lookup"><span data-stu-id="b2a98-117">Run the following code to create an index on **EmployeeID**:</span></span>  
  
    ```  
    CREATE UNIQUE INDEX EmpIDs_unq ON NewOrg(EmployeeID) ;  
    GO  
    ```  
  
3.  <span data-ttu-id="b2a98-118">執行下列程式碼，以全部三個索引的順序，從資料表擷取資料：</span><span class="sxs-lookup"><span data-stu-id="b2a98-118">Run the following code to retrieve data from the table in the order of each of the three indexes:</span></span>  
  
    ```  
    SELECT OrgNode.ToString() AS LogicalNode,  
    OrgNode, H_Level, EmployeeID, LoginID  
    FROM NewOrg   
    ORDER BY OrgNode;  
  
    SELECT OrgNode.ToString() AS LogicalNode,  
    OrgNode, H_Level, EmployeeID, LoginID   
    FROM NewOrg   
    ORDER BY H_Level, OrgNode;  
  
    SELECT OrgNode.ToString() AS LogicalNode,  
    OrgNode, H_Level, EmployeeID, LoginID   
    FROM NewOrg   
    ORDER BY EmployeeID;  
    GO  
    ```  
  
4.  <span data-ttu-id="b2a98-119">比較結果集以查看每個索引類型中儲存的順序。</span><span class="sxs-lookup"><span data-stu-id="b2a98-119">Compare the result sets to see how the order is stored in each type of index.</span></span> <span data-ttu-id="b2a98-120">只有每個輸出的前四個資料列遵照這個順序。</span><span class="sxs-lookup"><span data-stu-id="b2a98-120">Only the first four rows of each output follow.</span></span>  
  
     [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
     <span data-ttu-id="b2a98-121">深度優先索引：員工記錄緊接著其主管儲存。</span><span class="sxs-lookup"><span data-stu-id="b2a98-121">Depth-first index: Employee records are stored adjacent to their manager.</span></span>  
  
     `LogicalNode OrgNode    H_Level EmployeeID LoginID`  
  
     `/             0x         0         1      zarifin`  
  
     `/1/          0x58        1         2      tplate`  
  
     `/1/1/       0x5AC0       2         4      schai`  
  
     `/1/1/1/     0x5AD6       3         9      jwang`  
  
     `/1/1/2/     0x5ADA       3        10      malexander`  
  
     `/1/2/       0x5B40       2         5      elang`  
  
     `/1/3/       0x5BC0       2         6      gsmits`  
  
     `/2/         0x68         1         3      hjensen`  
  
     `/2/1/       0x6AC0       2         7      sdavis`  
  
     `/2/2/       0x6B40       2         8      norint`  
  
     <span data-ttu-id="b2a98-122">**EmployeeID**優先索引：資料列會以 **EmployeeID** 順序儲存。</span><span class="sxs-lookup"><span data-stu-id="b2a98-122">**EmployeeID**-first index: Rows are stored in **EmployeeID** sequence.</span></span>  
  
     `LogicalNode OrgNode    H_Level EmployeeID LoginID`  
  
     `/             0x         0         1      zarifin`  
  
     `/1/          0x58        1         2      tplate`  
  
     `/2/         0x68         1         3      hjensen`  
  
     `/1/1/       0x5AC0       2         4      schai`  
  
     `/1/2/       0x5B40       2         5      elang`  
  
     `/1/3/       0x5BC0       2         6      gsmits`  
  
     `/2/1/       0x6AC0       2         7      sdavis`  
  
     `/2/2/       0x6B40       2         8      norint`  
  
     `/1/1/1/     0x5AD6       3         9      jwang`  
  
     `/1/1/2/     0x5ADA       3        10      malexander`  
  
> [!NOTE]  
>  <span data-ttu-id="b2a98-123">如需顯示深度優先索引與廣度優先索引間差異的圖表，請參閱[階層式資料 &#40;SQL Server&#41;](../hierarchical-data-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="b2a98-123">For diagrams that show the difference between a depth-first index and a breadth-first index, see [Hierarchical Data &#40;SQL Server&#41;](../hierarchical-data-sql-server.md).</span></span>  
  
#### <a name="to-drop-the-unnecessary-columns"></a><span data-ttu-id="b2a98-124">卸除不必要的資料行</span><span class="sxs-lookup"><span data-stu-id="b2a98-124">To drop the unnecessary columns</span></span>  
  
1.  <span data-ttu-id="b2a98-125">**ManagerID** 資料行代表員工/主管的關聯性，此種關聯性現在以 **OrgNode** 資料行代表。</span><span class="sxs-lookup"><span data-stu-id="b2a98-125">The **ManagerID** column represents the employee/manager relationship, which is now represented by the **OrgNode** column.</span></span> <span data-ttu-id="b2a98-126">如果其他應用程式不需要 **ManagerID** 資料行，請考慮使用下列陳述式卸除該資料行：</span><span class="sxs-lookup"><span data-stu-id="b2a98-126">If other applications do not need the **ManagerID** column, consider dropping it by using the following statement:</span></span>  
  
    ```  
    ALTER TABLE NewOrg DROP COLUMN ManagerID ;  
    GO  
    ```  
  
2.  <span data-ttu-id="b2a98-127">**EmployeeID** 資料行也是多餘的。</span><span class="sxs-lookup"><span data-stu-id="b2a98-127">The **EmployeeID** column is also redundant.</span></span> <span data-ttu-id="b2a98-128">**OrgNode** 資料行可唯一識別每個員工。</span><span class="sxs-lookup"><span data-stu-id="b2a98-128">The **OrgNode** column uniquely identifies each employee.</span></span> <span data-ttu-id="b2a98-129">如果其他應用程式不需要 **EmployeeID** 資料行，請考慮使用下列程式碼先卸除索引，再卸除該資料行：</span><span class="sxs-lookup"><span data-stu-id="b2a98-129">If other applications do not need the **EmployeeID** column, consider dropping the index and then the column by using the following code:</span></span>  
  
    ```  
    DROP INDEX EmpIDs_unq ON NewOrg ;  
    ALTER TABLE NewOrg DROP COLUMN EmployeeID ;  
    GO  
    ```  
  
#### <a name="to-replace-the-original-table-with-the-new-table"></a><span data-ttu-id="b2a98-130">以新的資料表取代原始的資料表</span><span class="sxs-lookup"><span data-stu-id="b2a98-130">To replace the original table with the new table</span></span>  
  
1.  <span data-ttu-id="b2a98-131">如果您的原始資料表包含任何額外的索引或條件約束，請將它們新增到 **NewOrg** 資料表中。</span><span class="sxs-lookup"><span data-stu-id="b2a98-131">If your original table contained any additional indexes or constraints, add them to the **NewOrg** table.</span></span>  
  
2.  <span data-ttu-id="b2a98-132">以新的資料表取代舊的 **EmployeeDemo** 資料表。</span><span class="sxs-lookup"><span data-stu-id="b2a98-132">Replace the old **EmployeeDemo** table with the new table.</span></span> <span data-ttu-id="b2a98-133">執行下列程式碼卸除舊的資料表，然後以舊名稱重新命名新的資料表：</span><span class="sxs-lookup"><span data-stu-id="b2a98-133">Run the following code to drop the old table, and then rename the new table with the old name:</span></span>  
  
    ```  
    DROP TABLE EmployeeDemo ;  
    GO  
    sp_rename 'NewOrg', EmployeeDemo ;  
    GO  
    ```  
  
3.  <span data-ttu-id="b2a98-134">執行下列程式碼檢查最終的資料表：</span><span class="sxs-lookup"><span data-stu-id="b2a98-134">Run the following code to examine the final table:</span></span>  
  
    ```  
    SELECT * FROM EmployeeDemo ;  
    ```  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="b2a98-135">本課程的下一項工作</span><span class="sxs-lookup"><span data-stu-id="b2a98-135">Next Task in Lesson</span></span>  
 [<span data-ttu-id="b2a98-136">摘要：將資料表轉換為階層式結構</span><span class="sxs-lookup"><span data-stu-id="b2a98-136">Summary: Converting a Table to a Hierarchical Structure</span></span>](lesson-1-4-summary-converting-a-table-to-a-hierarchical-structure.md)  
  
  
