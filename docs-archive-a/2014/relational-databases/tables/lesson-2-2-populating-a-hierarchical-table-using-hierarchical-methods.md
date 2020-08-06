---
title: 使用階層式方法填入階層式資料表 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- HierarchyID
helpviewer_keywords:
- HierarchyID
ms.assetid: 2c95fa60-5b8e-4a05-ac09-cffe2b05900a
author: stevestein
ms.author: sstein
ms.openlocfilehash: ef99d711a772a075f568a83f5d56fcecaaa598f0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597700"
---
# <a name="populating-a-hierarchical-table-using-hierarchical-methods"></a><span data-ttu-id="c0946-102">使用階層式方法擴展階層式資料表</span><span class="sxs-lookup"><span data-stu-id="c0946-102">Populating a Hierarchical Table Using Hierarchical Methods</span></span>
  [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] <span data-ttu-id="c0946-103">行銷部門有 8 名員工。</span><span class="sxs-lookup"><span data-stu-id="c0946-103">has 8 employees working in the Marketing department.</span></span> <span data-ttu-id="c0946-104">員工層級如下：</span><span class="sxs-lookup"><span data-stu-id="c0946-104">The employee hierarchy looks like this:</span></span>  
  
 <span data-ttu-id="c0946-105">**David**( **EmployeeID** 6) 是行銷經理。</span><span class="sxs-lookup"><span data-stu-id="c0946-105">**David**, **EmployeeID** 6, is the Marketing Manager.</span></span> <span data-ttu-id="c0946-106">**David**管理三名行銷專員：</span><span class="sxs-lookup"><span data-stu-id="c0946-106">Three Marketing Specialists report to **David**:</span></span>  
  
-   <span data-ttu-id="c0946-107">**Sariya**( **EmployeeID** 46)</span><span class="sxs-lookup"><span data-stu-id="c0946-107">**Sariya**, **EmployeeID** 46</span></span>  
  
-   <span data-ttu-id="c0946-108">**John**( **EmployeeID** 271)</span><span class="sxs-lookup"><span data-stu-id="c0946-108">**John**, **EmployeeID** 271</span></span>  
  
-   <span data-ttu-id="c0946-109">**Jill**( **EmployeeID** 119)</span><span class="sxs-lookup"><span data-stu-id="c0946-109">**Jill**, **EmployeeID** 119</span></span>  
  
 <span data-ttu-id="c0946-110">**Sariya** 管理行銷助理**Wanida** ( **EmployeeID**269)， **John** 管理行銷助理**Mary** ( **EmployeeID**272)。</span><span class="sxs-lookup"><span data-stu-id="c0946-110">Marketing Assistant **Wanida** (**EmployeeID** 269), reports to **Sariya**, and Marketing Assistant **Mary** (**EmployeeID** 272), reports to **John**.</span></span>  
  
### <a name="to-insert-the-root-of-the-hierarchy-tree"></a><span data-ttu-id="c0946-111">插入階層樹狀結構的根目錄</span><span class="sxs-lookup"><span data-stu-id="c0946-111">To insert the root of the hierarchy tree</span></span>  
  
1.  <span data-ttu-id="c0946-112">下列範例會將行銷經理 **David** 插入階層根目錄的資料表中。</span><span class="sxs-lookup"><span data-stu-id="c0946-112">The following example inserts **David** the Marketing Manager into the table at the root of the hierarchy.</span></span> <span data-ttu-id="c0946-113">**OrdLevel** 資料行為計算資料行。</span><span class="sxs-lookup"><span data-stu-id="c0946-113">The **OrdLevel** column is a computed column.</span></span> <span data-ttu-id="c0946-114">因此，不是 INSERT 陳述式的一部分。</span><span class="sxs-lookup"><span data-stu-id="c0946-114">Therefore, it is not part of the INSERT statement.</span></span> <span data-ttu-id="c0946-115">第一筆記錄使用 [GetRoot()](/sql/t-sql/data-types/getroot-database-engine) 方法，將這個第一筆記錄擴展為階層的根目錄。</span><span class="sxs-lookup"><span data-stu-id="c0946-115">This first record uses the [GetRoot()](/sql/t-sql/data-types/getroot-database-engine) method to populate this first record as the root of the hierarchy.</span></span>  
  
    ```  
    INSERT HumanResources.EmployeeOrg (OrgNode, EmployeeID, EmpName, Title)  
    VALUES (hierarchyid::GetRoot(), 6, 'David', 'Marketing Manager') ;  
    GO  
    ```  
  
2.  <span data-ttu-id="c0946-116">執行下列節點以檢查資料表中的初始資料列：</span><span class="sxs-lookup"><span data-stu-id="c0946-116">Execute the following code to examine initial row in the table:</span></span>  
  
    ```  
    SELECT OrgNode.ToString() AS Text_OrgNode,   
    OrgNode, OrgLevel, EmployeeID, EmpName, Title   
    FROM HumanResources.EmployeeOrg ;  
    ```  
  
     [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
    ```  
    Text_OrgNode OrgNode OrgLevel EmployeeID EmpName Title  
    ------------ ------- -------- ---------- ------- -----------------  
    /            Ox      0        6          David   Marketing Manager  
    ```  
  
 <span data-ttu-id="c0946-117">如同上一個課程，我們使用 `ToString()` 方法，將 `hierarchyid` 資料類型轉換為比較容易了解的格式。</span><span class="sxs-lookup"><span data-stu-id="c0946-117">As in the previous lesson, we use the `ToString()` method to convert the `hierarchyid` data type to a format that is more easily understood.</span></span>  
  
### <a name="to-insert-a-subordinate-employee"></a><span data-ttu-id="c0946-118">插入從屬員工</span><span class="sxs-lookup"><span data-stu-id="c0946-118">To insert a subordinate employee</span></span>  
  
1.  <span data-ttu-id="c0946-119">**David** 管理 **Sariya**。</span><span class="sxs-lookup"><span data-stu-id="c0946-119">**Sariya** reports to **David**.</span></span> <span data-ttu-id="c0946-120">若要插入**Sariya 的**節點，您必須建立適當的資料類型**OrgNode**值 `hierarchyid` 。</span><span class="sxs-lookup"><span data-stu-id="c0946-120">To insert **Sariya's** node, you must create an appropriate **OrgNode** value of data type `hierarchyid`.</span></span> <span data-ttu-id="c0946-121">下列程式碼會建立 `hierarchyid` 資料類型的變數，並使用資料表的 OrgNode 根目錄值擴展。</span><span class="sxs-lookup"><span data-stu-id="c0946-121">The following code creates a variable of data type `hierarchyid` and populates it with the root OrgNode value of the table.</span></span> <span data-ttu-id="c0946-122">然後，搭配 [GetDescendant()](/sql/t-sql/data-types/getdescendant-database-engine) 方法使用該變數來插入從屬節點的資料列。</span><span class="sxs-lookup"><span data-stu-id="c0946-122">Then uses that variable with the [GetDescendant()](/sql/t-sql/data-types/getdescendant-database-engine) method to insert row that is a subordinate node.</span></span> <span data-ttu-id="c0946-123">`GetDescendant` 會採用兩個引數。</span><span class="sxs-lookup"><span data-stu-id="c0946-123">`GetDescendant` takes two arguments.</span></span> <span data-ttu-id="c0946-124">檢閱下列引數值的選項：</span><span class="sxs-lookup"><span data-stu-id="c0946-124">Review the following options for the argument values:</span></span>  
  
    -   <span data-ttu-id="c0946-125">如果父系為 NULL， `GetDescendant` 會傳回 NULL。</span><span class="sxs-lookup"><span data-stu-id="c0946-125">If parent is NULL, `GetDescendant` returns NULL.</span></span>  
  
    -   <span data-ttu-id="c0946-126">如果父系不是 NULL，而 child1 和 child2 都是 NULL， `GetDescendant` 則會傳回父系的一個子系。</span><span class="sxs-lookup"><span data-stu-id="c0946-126">If parent is not NULL, and both child1 and child2 are NULL, `GetDescendant` returns a child of parent.</span></span>  
  
    -   <span data-ttu-id="c0946-127">如果父系和 child1 都不是 NULL，而 child2 是 NULL， `GetDescendant` 會傳回父系中大於 child1 的子系。</span><span class="sxs-lookup"><span data-stu-id="c0946-127">If parent and child1 are not NULL, and child2 is NULL, `GetDescendant` returns a child of parent greater than child1.</span></span>  
  
    -   <span data-ttu-id="c0946-128">如果父系和 child2 不是 NULL，而 child1 是 NULL， `GetDescendant` 會傳回父系中小於 child2 的子系。</span><span class="sxs-lookup"><span data-stu-id="c0946-128">If parent and child2 are not NULL and child1 is NULL, `GetDescendant` returns a child of parent less than child2.</span></span>  
  
    -   <span data-ttu-id="c0946-129">如果父系、child1 和 child2 都不是 NULL， `GetDescendant` 會傳回父系中大於 child1 且小於 child2 的子系。</span><span class="sxs-lookup"><span data-stu-id="c0946-129">If parent, child1, and child2 are all not NULL, `GetDescendant` returns a child of parent greater than child1 and less than child2.</span></span>  
  
     <span data-ttu-id="c0946-130">下列程式碼使用根目錄父系的 `(NULL, NULL)` 引數，因為除了根目錄之外，資料表中還沒有任何資料列。</span><span class="sxs-lookup"><span data-stu-id="c0946-130">The following code uses the `(NULL, NULL)` arguments of the root parent because there are not yet any rows in the table except the root.</span></span> <span data-ttu-id="c0946-131">執行下列程式碼以插入 **Sariya**：</span><span class="sxs-lookup"><span data-stu-id="c0946-131">Execute the following code to insert **Sariya**:</span></span>  
  
    ```  
    DECLARE @Manager hierarchyid   
    SELECT @Manager = hierarchyid::GetRoot()  
    FROM HumanResources.EmployeeOrg ;  
  
    INSERT HumanResources.EmployeeOrg (OrgNode, EmployeeID, EmpName, Title)  
    VALUES  
    (@Manager.GetDescendant(NULL, NULL), 46, 'Sariya', 'Marketing Specialist') ;  
  
    ```  
  
2.  <span data-ttu-id="c0946-132">從第一個程序開始重複查詢，以查詢資料表並查看項目如何出現：</span><span class="sxs-lookup"><span data-stu-id="c0946-132">Repeat the query from the first procedure to query the table and see how the entries appear:</span></span>  
  
    ```  
    SELECT OrgNode.ToString() AS Text_OrgNode,   
    OrgNode, OrgLevel, EmployeeID, EmpName, Title   
    FROM HumanResources.EmployeeOrg ;  
    ```  
  
     [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
    ```  
    Text_OrgNode OrgNode OrgLevel EmployeeID EmpName Title  
    ------------ ------- -------- ---------- ------- -----------------  
    /            Ox      0        6          David   Marketing Manager  
    /1/          0x58    1        46         Sariya  Marketing Specialist  
    ```  
  
### <a name="to-create-a-procedure-for-entering-new-nodes"></a><span data-ttu-id="c0946-133">建立輸入新節點的程序</span><span class="sxs-lookup"><span data-stu-id="c0946-133">To create a procedure for entering new nodes</span></span>  
  
1.  <span data-ttu-id="c0946-134">若要簡化輸入資料的方式，請建立下列預存程序，將員工新增到 **EmployeeOrg** 資料表中。</span><span class="sxs-lookup"><span data-stu-id="c0946-134">To simplify entering data, create the following stored procedure to add employees to the **EmployeeOrg** table.</span></span> <span data-ttu-id="c0946-135">該程序會接受要新增之員工的輸入值。</span><span class="sxs-lookup"><span data-stu-id="c0946-135">The procedure accepts input values about the employee being added.</span></span> <span data-ttu-id="c0946-136">這包括新員工之主管的 **EmployeeID** 、新員工的 **EmployeeID** 號碼，及其姓氏和職稱。</span><span class="sxs-lookup"><span data-stu-id="c0946-136">This includes the **EmployeeID** of the new employee's manager, the new employee's **EmployeeID** number, and their first name and title.</span></span> <span data-ttu-id="c0946-137">此程序會使用 `GetDescendant()` 以及 [GetAncestor()](/sql/t-sql/data-types/getancestor-database-engine) 方法。</span><span class="sxs-lookup"><span data-stu-id="c0946-137">The procedure uses `GetDescendant()` and also the [GetAncestor()](/sql/t-sql/data-types/getancestor-database-engine) method.</span></span> <span data-ttu-id="c0946-138">執行下列程式碼以建立程序：</span><span class="sxs-lookup"><span data-stu-id="c0946-138">Execute the following code to create the procedure:</span></span>  
  
    ```  
    CREATE PROC AddEmp(@mgrid int, @empid int, @e_name varchar(20), @title varchar(20))   
    AS   
    BEGIN  
       DECLARE @mOrgNode hierarchyid, @lc hierarchyid  
       SELECT @mOrgNode = OrgNode   
       FROM HumanResources.EmployeeOrg   
       WHERE EmployeeID = @mgrid  
       SET TRANSACTION ISOLATION LEVEL SERIALIZABLE  
       BEGIN TRANSACTION  
          SELECT @lc = max(OrgNode)   
          FROM HumanResources.EmployeeOrg   
          WHERE OrgNode.GetAncestor(1) =@mOrgNode ;  
  
          INSERT HumanResources.EmployeeOrg (OrgNode, EmployeeID, EmpName, Title)  
          VALUES(@mOrgNode.GetDescendant(@lc, NULL), @empid, @e_name, @title)  
       COMMIT  
    END ;  
    GO  
    ```  
  
2.  <span data-ttu-id="c0946-139">下列範例會加入 **David**直接或間接管理的其餘 4 名員工。</span><span class="sxs-lookup"><span data-stu-id="c0946-139">The following example adds the remaining 4 employees that report directly or indirectly to **David**.</span></span>  
  
    ```  
    EXEC AddEmp 6, 271, 'John', 'Marketing Specialist' ;  
    EXEC AddEmp 6, 119, 'Jill', 'Marketing Specialist' ;  
    EXEC AddEmp 46, 269, 'Wanida', 'Marketing Assistant' ;  
    EXEC AddEmp 271, 272, 'Mary', 'Marketing Assistant' ;  
    ```  
  
3.  <span data-ttu-id="c0946-140">再次執行下列查詢，檢查 **EmployeeOrg** 資料表中的資料列：</span><span class="sxs-lookup"><span data-stu-id="c0946-140">Again, execute the following query examine the rows in the **EmployeeOrg** table:</span></span>  
  
    ```  
    SELECT OrgNode.ToString() AS Text_OrgNode,   
    OrgNode, OrgLevel, EmployeeID, EmpName, Title   
    FROM HumanResources.EmployeeOrg ;  
    GO  
    ```  
  
     [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
    ```  
    Text_OrgNode OrgNode OrgLevel EmployeeID EmpName Title  
    ------------ ------- -------- ---------- ------- -----------------  
    /            Ox      0        6          David   Marketing Manager  
    /1/          0x58    1        46         Sariya  Marketing Specialist  
    /1/1/        0x5AC0  2        269        Wanida  Marketing Assistant  
    /2/          0x68    1        271        John    Marketing Specialist  
    /2/1/        0x6AC0  2        272        Mary    Marketing Assistant  
    /3/          0x78    1        119        Jill    Marketing Specialist  
    ```  
  
 <span data-ttu-id="c0946-141">資料表現在已經完全擴展到行銷組織了。</span><span class="sxs-lookup"><span data-stu-id="c0946-141">The table is now fully populated with the Marketing organization.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="c0946-142">本課程的下一項工作</span><span class="sxs-lookup"><span data-stu-id="c0946-142">Next Task in Lesson</span></span>  
 [<span data-ttu-id="c0946-143">使用階層方法查詢階層式資料表</span><span class="sxs-lookup"><span data-stu-id="c0946-143">Querying a Hierarchical Table Using Hierarchy Methods</span></span>](lesson-2-3-querying-a-hierarchical-table-using-hierarchy-methods.md)  
  
  
