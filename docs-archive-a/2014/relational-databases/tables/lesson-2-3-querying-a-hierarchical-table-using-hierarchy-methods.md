---
title: 使用階層方法查詢階層式資料表 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- HierarchyID
ms.assetid: 3b4f7dae-65b5-4d8d-8641-87aba9aa692d
author: stevestein
ms.author: sstein
ms.openlocfilehash: 6c86c8e8678fc821dc3796a511349c1c3498bdb7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597035"
---
# <a name="querying-a-hierarchical-table-using-hierarchy-methods"></a><span data-ttu-id="8a375-102">使用階層方法查詢階層式資料表</span><span class="sxs-lookup"><span data-stu-id="8a375-102">Querying a Hierarchical Table Using Hierarchy Methods</span></span>
  <span data-ttu-id="8a375-103">既然 HumanResources.EmployeeOrg 資料表會完全擴展，此工作將會顯示如何使用某些階層式方法查詢階層。</span><span class="sxs-lookup"><span data-stu-id="8a375-103">Now that the HumanResources.EmployeeOrg table is fully populated, this task will show you how to query the hierarchy using some of the hierarchical methods.</span></span>  
  
### <a name="to-find-subordinate-nodes"></a><span data-ttu-id="8a375-104">尋找從屬節點</span><span class="sxs-lookup"><span data-stu-id="8a375-104">To find subordinate nodes</span></span>  
  
1.  <span data-ttu-id="8a375-105">Sariya 有一個從屬員工。</span><span class="sxs-lookup"><span data-stu-id="8a375-105">Sariya has one subordinate employee.</span></span> <span data-ttu-id="8a375-106">若要查詢 Sariya 的部屬，請執行使用 [IsDescendantOf](/sql/t-sql/data-types/isdescendantof-database-engine) 方法的下列查詢：</span><span class="sxs-lookup"><span data-stu-id="8a375-106">To query for Sariya's subordinates, execute the following query that uses the [IsDescendantOf](/sql/t-sql/data-types/isdescendantof-database-engine) method:</span></span>  
  
    ```  
    DECLARE @CurrentEmployee hierarchyid  
  
    SELECT @CurrentEmployee = OrgNode  
    FROM HumanResources.EmployeeOrg  
    WHERE EmployeeID = 46 ;  
  
    SELECT *  
    FROM HumanResources.EmployeeOrg  
    WHERE OrgNode.IsDescendantOf(@CurrentEmployee ) = 1 ;  
    ```  
  
     <span data-ttu-id="8a375-107">結果會同時列出 Sariya 和 Wanida。</span><span class="sxs-lookup"><span data-stu-id="8a375-107">The result lists both Sariya and Wanida.</span></span> <span data-ttu-id="8a375-108">Sariya 是層級 0 的下階，因此會被列出。</span><span class="sxs-lookup"><span data-stu-id="8a375-108">Sariya is listed because she is the descendant at the 0 level.</span></span> <span data-ttu-id="8a375-109">Wanida 是層級 1 的下階。</span><span class="sxs-lookup"><span data-stu-id="8a375-109">Wanida is the descendant at the 1 level.</span></span>  
  
2.  <span data-ttu-id="8a375-110">您也可以使用 [GetAncestor](/sql/t-sql/data-types/getancestor-database-engine) 方法來查詢這項資訊。</span><span class="sxs-lookup"><span data-stu-id="8a375-110">You can also query for this information by using the [GetAncestor](/sql/t-sql/data-types/getancestor-database-engine) method.</span></span> <span data-ttu-id="8a375-111">`GetAncestor` 會針對您嘗試傳回的層級傳回一個引數。</span><span class="sxs-lookup"><span data-stu-id="8a375-111">`GetAncestor` takes an argument for the level that you are trying to return.</span></span> <span data-ttu-id="8a375-112">由於 Wanida 是 Sariya 下的一個層級，請按照下列程式碼的示範，使用 `GetAncestor(1)` ：</span><span class="sxs-lookup"><span data-stu-id="8a375-112">Since Wanida is one level underneath Sariya, use `GetAncestor(1)` as demonstrated in the following code:</span></span>  
  
    ```  
    DECLARE @CurrentEmployee hierarchyid  
  
    SELECT @CurrentEmployee = OrgNode  
    FROM HumanResources.EmployeeOrg  
    WHERE EmployeeID = 46 ;  
  
    SELECT OrgNode.ToString() AS Text_OrgNode, *  
    FROM HumanResources.EmployeeOrg  
    WHERE OrgNode.GetAncestor(1) = @CurrentEmployee  
    ```  
  
     <span data-ttu-id="8a375-113">這次結果列出只 Wanida。</span><span class="sxs-lookup"><span data-stu-id="8a375-113">This time the result lists only Wanida.</span></span>  
  
3.  <span data-ttu-id="8a375-114">現在，將 `@CurrentEmployee` 變更為 David (EmployeeID 6)，並將層級變更為 2。</span><span class="sxs-lookup"><span data-stu-id="8a375-114">Now change the `@CurrentEmployee` to David (EmployeeID 6) and the level to 2.</span></span> <span data-ttu-id="8a375-115">執行下列程式碼也可以傳回 Wanida：</span><span class="sxs-lookup"><span data-stu-id="8a375-115">Execute the following to also return Wanida:</span></span>  
  
    ```  
    DECLARE @CurrentEmployee hierarchyid  
  
    SELECT @CurrentEmployee = OrgNode  
    FROM HumanResources.EmployeeOrg  
    WHERE EmployeeID = 6 ;  
  
    SELECT OrgNode.ToString() AS Text_OrgNode, *  
    FROM HumanResources.EmployeeOrg  
    WHERE OrgNode.GetAncestor(2) = @CurrentEmployee  
    ```  
  
     <span data-ttu-id="8a375-116">這次，您也可以接收到兩個層級下的 Mary，她也是回報給 David。</span><span class="sxs-lookup"><span data-stu-id="8a375-116">This time, you also receive Mary who also reports to David, two levels down.</span></span>  
  
### <a name="to-use-getroot-and-getlevel"></a><span data-ttu-id="8a375-117">使用 GetRoot 與 GetLevel</span><span class="sxs-lookup"><span data-stu-id="8a375-117">To use GetRoot, and GetLevel</span></span>  
  
1.  <span data-ttu-id="8a375-118">階層成長得越大時，判斷成員在階層中的位置時，也就變得更加困難。</span><span class="sxs-lookup"><span data-stu-id="8a375-118">As the hierarchy grows larger it is more difficult to determine where the members are in the hierarchy.</span></span> <span data-ttu-id="8a375-119">使用 [GetLevel](/sql/t-sql/data-types/getlevel-database-engine) 方法，尋找階層中，每個資料列下有多少層級。</span><span class="sxs-lookup"><span data-stu-id="8a375-119">Use the [GetLevel](/sql/t-sql/data-types/getlevel-database-engine) method to find how many levels down each row is in the hierarchy.</span></span> <span data-ttu-id="8a375-120">執行下列程式碼以檢視所有資料列的層級：</span><span class="sxs-lookup"><span data-stu-id="8a375-120">Execute the following code to view the levels of all the rows:</span></span>  
  
    ```  
    SELECT OrgNode.ToString() AS Text_OrgNode,   
    OrgNode.GetLevel() AS EmpLevel, *  
    FROM HumanResources.EmployeeOrg ;  
    GO  
  
    ```  
  
2.  <span data-ttu-id="8a375-121">使用 [GetRoot](/sql/t-sql/data-types/getroot-database-engine) 方法，尋找階層中的根節點。</span><span class="sxs-lookup"><span data-stu-id="8a375-121">Use the [GetRoot](/sql/t-sql/data-types/getroot-database-engine) method to find the root node in the hierarchy.</span></span> <span data-ttu-id="8a375-122">下列程式碼範例會傳回根目錄的單一資料列：</span><span class="sxs-lookup"><span data-stu-id="8a375-122">The following code returns the single row which is the root:</span></span>  
  
    ```  
    SELECT OrgNode.ToString() AS Text_OrgNode, *  
    FROM HumanResources.EmployeeOrg  
    WHERE OrgNode = hierarchyid::GetRoot() ;  
    GO  
  
    ```  
  
 <span data-ttu-id="8a375-123">下一個工作將會重新組織階層。</span><span class="sxs-lookup"><span data-stu-id="8a375-123">The next task will reorganize the hierarchy.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="8a375-124">本課程的下一項工作</span><span class="sxs-lookup"><span data-stu-id="8a375-124">Next Task in Lesson</span></span>  
 [<span data-ttu-id="8a375-125">使用階層式方法重新排列階層式資料表中的資料順序</span><span class="sxs-lookup"><span data-stu-id="8a375-125">Reordering Data in a Hierarchical Table Using Hierarchical Methods</span></span>](lesson-2-4-reordering-data-in-a-hierarchical-table-using-hierarchical-methods.md)  
  
  
