---
title: 使用現有的階層式資料填入資料表 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- HierarchyID
ms.assetid: fd943d84-dbe6-4a05-912b-c88164998d80
author: stevestein
ms.author: sstein
ms.openlocfilehash: 966548b11ad4697abc06de5c5c239a511f80b7af
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687746"
---
# <a name="populating-a-table-with-existing-hierarchical-data"></a><span data-ttu-id="4d268-102">使用現有的階層式資料填入資料表</span><span class="sxs-lookup"><span data-stu-id="4d268-102">Populating a Table with Existing Hierarchical Data</span></span>
  <span data-ttu-id="4d268-103"> 此工作會建立一個新的資料表，並以 **EmployeeDemo** 資料表中的資料填入該資料表。</span><span class="sxs-lookup"><span data-stu-id="4d268-103">This task creates a new table and populates it with the data in the **EmployeeDemo** table.</span></span> <span data-ttu-id="4d268-104">此工作的步驟如下：</span><span class="sxs-lookup"><span data-stu-id="4d268-104">This task has the following steps:</span></span>  
  
-   <span data-ttu-id="4d268-105">建立包含 `hierarchyid` 資料行的新資料表。</span><span class="sxs-lookup"><span data-stu-id="4d268-105">Create a new table that contains a `hierarchyid` column.</span></span> <span data-ttu-id="4d268-106">此資料行可以取代現有的 **EmployeeID** 和 **ManagerID** 資料行。</span><span class="sxs-lookup"><span data-stu-id="4d268-106">This column could replace the existing **EmployeeID** and **ManagerID** columns.</span></span> <span data-ttu-id="4d268-107">不過，您將會保留這些資料行。</span><span class="sxs-lookup"><span data-stu-id="4d268-107">However, you will retain those columns.</span></span> <span data-ttu-id="4d268-108">這是因為現有的應用程式可能會參考這些資料行，而且這些資料行也可以在轉換後，協助您了解資料。</span><span class="sxs-lookup"><span data-stu-id="4d268-108">This is because existing applications might refer to those columns, and also to help you understand the data after the transfer.</span></span> <span data-ttu-id="4d268-109">資料表定義指定 **OrgNode** 為主索引鍵，其會要求該資料行所包含的值不得重複。</span><span class="sxs-lookup"><span data-stu-id="4d268-109">The table definition specifies that **OrgNode** is the primary key, which requires the column to contain unique values.</span></span> <span data-ttu-id="4d268-110">**OrgNode** 資料行上的叢集索引將以 **OrgNode** 順序儲存資料。</span><span class="sxs-lookup"><span data-stu-id="4d268-110">The clustered index on the **OrgNode** column will store the date in **OrgNode** sequence.</span></span>  
  
-   <span data-ttu-id="4d268-111">建立暫存資料表，該資料表可用於追蹤各個主管手下的直屬員工人數。</span><span class="sxs-lookup"><span data-stu-id="4d268-111">Create a temporary table that is used to track how many employees report directly to each manager.</span></span>  
  
-   <span data-ttu-id="4d268-112">使用 **EmployeeDemo** 資料表中的資料，填入新資料表。</span><span class="sxs-lookup"><span data-stu-id="4d268-112">Populate the new table by using data from the **EmployeeDemo** table.</span></span>  
  
### <a name="to-create-a-new-table-named-neworg"></a><span data-ttu-id="4d268-113">若要建立名稱為 NewOrg 的新資料表</span><span class="sxs-lookup"><span data-stu-id="4d268-113">To create a new table named NewOrg</span></span>  
  
-   <span data-ttu-id="4d268-114">在 [查詢編輯器] 視窗中，執行下列程式碼以建立名稱為 **HumanResources.NewOrg**的新資料表：</span><span class="sxs-lookup"><span data-stu-id="4d268-114">In a Query Editor window, run the following code to create a new table named **HumanResources.NewOrg**:</span></span>  
  
    ```  
    CREATE TABLE NewOrg  
    (  
      OrgNode hierarchyid,  
      EmployeeID int,  
      LoginID nvarchar(50),  
      ManagerID int  
    CONSTRAINT PK_NewOrg_OrgNode  
      PRIMARY KEY CLUSTERED (OrgNode)  
    );  
    GO  
    ```  
  
### <a name="to-create-a-temporary-table-named-children"></a><span data-ttu-id="4d268-115">建立名稱為 #Children 的暫存資料表</span><span class="sxs-lookup"><span data-stu-id="4d268-115">To create a temporary table named #Children</span></span>  
  
1.  <span data-ttu-id="4d268-116">建立名為 **#Children** 的暫存資料表，以及名稱為 **Num** 的資料行，該資料行將包含每個節點的子系數目：</span><span class="sxs-lookup"><span data-stu-id="4d268-116">Create a temporary table named **#Children** with a column named **Num** that will contain the number of children for each node:</span></span>  
  
    ```  
    CREATE TABLE #Children   
       (  
        EmployeeID int,  
        ManagerID int,  
        Num int  
    );  
    GO  
    ```  
  
2.  <span data-ttu-id="4d268-117">新增索引以大幅提高填入 **NewOrg** 資料表的查詢速度：</span><span class="sxs-lookup"><span data-stu-id="4d268-117">Add an index that will significantly speed up the query that populates the **NewOrg** table:</span></span>  
  
    ```  
    CREATE CLUSTERED INDEX tmpind ON #Children(ManagerID, EmployeeID);  
    GO  
    ```  
  
### <a name="to-populate-the-neworg-table"></a><span data-ttu-id="4d268-118">填入 NewOrg 資料表</span><span class="sxs-lookup"><span data-stu-id="4d268-118">To populate the NewOrg table</span></span>  
  
1.  <span data-ttu-id="4d268-119">遞迴查詢禁止包含彙總的子查詢。</span><span class="sxs-lookup"><span data-stu-id="4d268-119">Recursive queries forbid subqueries with aggregates.</span></span> <span data-ttu-id="4d268-120">反之，會使用下列程式碼填入 **#Children** 資料表；該程式碼是使用 [ROW_NUMBER()](/sql/t-sql/functions/row-number-transact-sql) 方法填入 **Num** 資料行：</span><span class="sxs-lookup"><span data-stu-id="4d268-120">Instead, populate the **#Children** table with the following code, which uses the [ROW_NUMBER()](/sql/t-sql/functions/row-number-transact-sql) method to populate the **Num** column:</span></span>  
  
    ```  
    INSERT #Children (EmployeeID, ManagerID, Num)  
    SELECT EmployeeID, ManagerID,  
      ROW_NUMBER() OVER (PARTITION BY ManagerID ORDER BY ManagerID)   
    FROM EmployeeDemo  
    GO  
  
    ```  
  
2.  <span data-ttu-id="4d268-121">檢閱 **#Children** 資料表。</span><span class="sxs-lookup"><span data-stu-id="4d268-121">Review the **#Children** table.</span></span> <span data-ttu-id="4d268-122">請注意 **Num** 資料行如何包含每個主管的序號。</span><span class="sxs-lookup"><span data-stu-id="4d268-122">Note how the **Num** column contains sequential numbers for each manager.</span></span>  
  
    ```  
    SELECT * FROM #Children ORDER BY ManagerID, Num  
    GO  
  
    ```  
  
     [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
     `EmployeeID ManagerID Num`  
  
     `---------- --------- ---`  
  
     `1        NULL       1`  
  
     `2         1         1`  
  
     `3         1         2`  
  
     `4         2         1`  
  
     `5         2         2`  
  
     `6         2         3`  
  
     `7         3         1`  
  
     `8         3         2`  
  
     `9         4         1`  
  
     `10        4         2`  
  
3.  <span data-ttu-id="4d268-123">填入**NewOrg**資料表。</span><span class="sxs-lookup"><span data-stu-id="4d268-123">Populate the **NewOrg** table.</span></span> <span data-ttu-id="4d268-124">使用 GetRoot 和 ToString 方法，將**Num**值串連成 `hierarchyid` 格式，然後以產生的階層式值更新**OrgNode**資料行：</span><span class="sxs-lookup"><span data-stu-id="4d268-124">Use the GetRoot and ToString methods to concatenate the **Num** values into the `hierarchyid` format, and then update the **OrgNode** column with the resultant hierarchical values:</span></span>  
  
    ```  
    WITH paths(path, EmployeeID)   
    AS (  
    -- This section provides the value for the root of the hierarchy  
    SELECT hierarchyid::GetRoot() AS OrgNode, EmployeeID   
    FROM #Children AS C   
    WHERE ManagerID IS NULL   
  
    UNION ALL   
    -- This section provides values for all nodes except the root  
    SELECT   
    CAST(p.path.ToString() + CAST(C.Num AS varchar(30)) + '/' AS hierarchyid),   
    C.EmployeeID  
    FROM #Children AS C   
    JOIN paths AS p   
       ON C.ManagerID = P.EmployeeID   
    )  
    INSERT NewOrg (OrgNode, O.EmployeeID, O.LoginID, O.ManagerID)  
    SELECT P.path, O.EmployeeID, O.LoginID, O.ManagerID  
    FROM EmployeeDemo AS O   
    JOIN Paths AS P   
       ON O.EmployeeID = P.EmployeeID  
    GO  
  
    ```  
  
4.  <span data-ttu-id="4d268-125">將 `hierarchyid` 資料行轉換為字元格式時，會比較容易了解該資料行。</span><span class="sxs-lookup"><span data-stu-id="4d268-125">A `hierarchyid` column is more understandable when you convert it to character format.</span></span> <span data-ttu-id="4d268-126">執行下列程式碼 (其中包含 **OrgNode** 資料行之兩種表示法)，以檢閱 **NewOrg** 資料表中的資料：</span><span class="sxs-lookup"><span data-stu-id="4d268-126">Review the data in the **NewOrg** table by executing the following code, which contains two representations of the **OrgNode** column:</span></span>  
  
    ```  
    SELECT OrgNode.ToString() AS LogicalNode, *   
    FROM NewOrg   
    ORDER BY LogicalNode;  
    GO  
  
    ```  
  
     <span data-ttu-id="4d268-127">**LogicalNode**資料行會將此資料 `hierarchyid` 行轉換成更容易閱讀的文字格式，以代表階層。</span><span class="sxs-lookup"><span data-stu-id="4d268-127">The **LogicalNode** column converts the `hierarchyid` column into a more readable text form that represents the hierarchy.</span></span> <span data-ttu-id="4d268-128">在其餘工作中，您將使用 `ToString()` 方法，顯示 `hierarchyid` 資料行的邏輯格式。</span><span class="sxs-lookup"><span data-stu-id="4d268-128">In the remaining tasks, you will use the `ToString()` method to show the logical format of the `hierarchyid` columns.</span></span>  
  
5.  <span data-ttu-id="4d268-129">卸除不再需要的暫存資料表：</span><span class="sxs-lookup"><span data-stu-id="4d268-129">Drop the temporary table, which is no longer needed:</span></span>  
  
    ```  
    DROP TABLE #Children  
    GO  
    ```  
  
 <span data-ttu-id="4d268-130">下一個工作將是建立索引以支援階層式結構。</span><span class="sxs-lookup"><span data-stu-id="4d268-130">The next task will create indexes to support the hierarchical structure.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="4d268-131">本課程的下一項工作</span><span class="sxs-lookup"><span data-stu-id="4d268-131">Next Task in Lesson</span></span>  
 [<span data-ttu-id="4d268-132">最佳化 NewOrg 資料表</span><span class="sxs-lookup"><span data-stu-id="4d268-132">Optimizing the NewOrg Table</span></span>](lesson-1-3-optimizing-the-neworg-table.md)  
  
  
