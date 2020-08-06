---
title: 使用階層式方法重新排列階層式資料表中的資料順序 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- HierarchyID
ms.assetid: 7b8064c7-62c6-488d-84d2-57a5828fb907
author: stevestein
ms.author: sstein
ms.openlocfilehash: ac6c93f359a81a80af81182120f213564680de0d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585217"
---
# <a name="reordering-data-in-a-hierarchical-table-using-hierarchical-methods"></a><span data-ttu-id="84229-102">使用階層式方法重新排列階層式資料表中的資料順序</span><span class="sxs-lookup"><span data-stu-id="84229-102">Reordering Data in a Hierarchical Table Using Hierarchical Methods</span></span>
  <span data-ttu-id="84229-103">重新組織階層是常見的維護工作。</span><span class="sxs-lookup"><span data-stu-id="84229-103">Reorganizing a hierarchy is a common maintenance task.</span></span> <span data-ttu-id="84229-104">在這項工作中，我們將會使用 UPDATE 陳述式搭配 [GetReparentedValue](/sql/t-sql/data-types/getreparentedvalue-database-engine) 方法，先將單一資料列移到階層中的新位置。</span><span class="sxs-lookup"><span data-stu-id="84229-104">In this task, we will use an UPDATE statement with the [GetReparentedValue](/sql/t-sql/data-types/getreparentedvalue-database-engine) method to first move a single row to a new location in the hierarchy.</span></span> <span data-ttu-id="84229-105">然後，我們會將整個子樹移到新位置。</span><span class="sxs-lookup"><span data-stu-id="84229-105">Then we will move an entire sub-tree to a new location.</span></span>  
  
 <span data-ttu-id="84229-106">`GetReparentedValue` 方法會使用兩個引數。</span><span class="sxs-lookup"><span data-stu-id="84229-106">The `GetReparentedValue` method takes two arguments.</span></span> <span data-ttu-id="84229-107">第一個引數描述要修改的階層部分。</span><span class="sxs-lookup"><span data-stu-id="84229-107">The first argument describes the part of the hierarchy to be modified.</span></span> <span data-ttu-id="84229-108">例如，如果階層為 **/1/4/2/3/** 而您想要變更 **/1/4/** 區段，讓該階層變成 **/2/1/2/3/**，留下最後兩個節點 (**2/3/**) 不變，您必須提供變更的節點 (**/1/4/**) 作為第一個引數。</span><span class="sxs-lookup"><span data-stu-id="84229-108">For example, if a hierarchy is **/1/4/2/3/** and you want to change the **/1/4/** section, the hierarchy becomes **/2/1/2/3/**, leaving the last two nodes (**2/3/**) unchanged, you must provide the changing nodes (**/1/4/**) as the first argument.</span></span> <span data-ttu-id="84229-109">第二個引數會提供新的階層層級，在範例中為 **/2/1/**。</span><span class="sxs-lookup"><span data-stu-id="84229-109">The second argument provides the new hierarchy level, in our example **/2/1/**.</span></span> <span data-ttu-id="84229-110">兩個引數不必包含相同的層級數目。</span><span class="sxs-lookup"><span data-stu-id="84229-110">The two arguments do not have to contain the same number of levels.</span></span>  
  
### <a name="to-move-a-single-row-to-a-new-location-in-the-hierarchy"></a><span data-ttu-id="84229-111">將單一資料列移到階層中的新位置</span><span class="sxs-lookup"><span data-stu-id="84229-111">To move a single row to a new location in the hierarchy</span></span>  
  
1.  <span data-ttu-id="84229-112">目前 Wanida 回報給 Sariya。</span><span class="sxs-lookup"><span data-stu-id="84229-112">Currently Wanida reports to Sariya.</span></span> <span data-ttu-id="84229-113">在此程序中，您會從目前的節點 **/1/1/,** 移動 Wanida，因此她會回報給 Jill。</span><span class="sxs-lookup"><span data-stu-id="84229-113">In this procedure, you move Wanida from her current node **/1/1/,** so that she reports to Jill.</span></span> <span data-ttu-id="84229-114">她的新節點將會變成 **/3/1/** ，因此 **/1/** 是第一個引數，而 **/3/** 是第二個引數。</span><span class="sxs-lookup"><span data-stu-id="84229-114">Her new node will become **/3/1/** so **/1/** is the first argument and **/3/** is the second.</span></span> <span data-ttu-id="84229-115">這些引數會對應到 Sariya 和 Jill 的 **OrgNode** 值。</span><span class="sxs-lookup"><span data-stu-id="84229-115">These correspond to the **OrgNode** values of Sariya and Jill.</span></span> <span data-ttu-id="84229-116">執行下列程式碼，將 Wanida 從 Sariya 的組織移到 Jill 的組織：</span><span class="sxs-lookup"><span data-stu-id="84229-116">Execute the following code to move Wanida from Sariya's organization to Jill's:</span></span>  
  
    ```  
    DECLARE @CurrentEmployee hierarchyid , @OldParent hierarchyid, @NewParent hierarchyid  
    SELECT @CurrentEmployee = OrgNode FROM HumanResources.EmployeeOrg  
      WHERE EmployeeID = 269 ;   
    SELECT @OldParent = OrgNode FROM HumanResources.EmployeeOrg  
      WHERE EmployeeID = 46 ;   
    SELECT @NewParent = OrgNode FROM HumanResources.EmployeeOrg  
      WHERE EmployeeID = 119 ;   
  
    UPDATE HumanResources.EmployeeOrg  
    SET OrgNode = @CurrentEmployee. GetReparentedValue(@OldParent, @NewParent)   
    WHERE OrgNode = @CurrentEmployee ;  
    GO  
    ```  
  
2.  <span data-ttu-id="84229-117">執行下列程式碼以查看結果：</span><span class="sxs-lookup"><span data-stu-id="84229-117">Execute the following code to see the result:</span></span>  
  
    ```  
    SELECT OrgNode.ToString() AS Text_OrgNode,   
    OrgNode, OrgLevel, EmployeeID, EmpName, Title   
    FROM HumanResources.EmployeeOrg ;  
    GO  
    ```  
  
     <span data-ttu-id="84229-118">Wanida 現在是在節點 **/3/1/**。</span><span class="sxs-lookup"><span data-stu-id="84229-118">Wanida is now at node **/3/1/**.</span></span>  
  
### <a name="to-reorganize-a-section-of-a-hierarchy"></a><span data-ttu-id="84229-119">重新組織階層的區段</span><span class="sxs-lookup"><span data-stu-id="84229-119">To reorganize a section of a hierarchy</span></span>  
  
1.  <span data-ttu-id="84229-120">為示範如何同時移動大量的人員，請先執行下列程式碼，以便加一位實習生回報給 Wanida：</span><span class="sxs-lookup"><span data-stu-id="84229-120">To demonstrate how to move a larger number of people at the same time, first execute the following code to add an intern reporting to Wanida:</span></span>  
  
    ```  
    EXEC AddEmp 269, 291, 'Kevin', 'Marketing Intern'  ;  
    GO  
    ```  
  
2.  <span data-ttu-id="84229-121">現在，Kevin 回報給 Wanida，Wanida 回報給 Jill，而 Jill 回報給 David。</span><span class="sxs-lookup"><span data-stu-id="84229-121">Now Kevin reports to Wanida, who reports to Jill, who reports to David.</span></span> <span data-ttu-id="84229-122">也就是說，Kevin 位於層級 **/3/1/1/**。</span><span class="sxs-lookup"><span data-stu-id="84229-122">That means that Kevin is at level **/3/1/1/**.</span></span> <span data-ttu-id="84229-123">若要將 Jill 的所有部屬移到新的主管之下，我們會將讓 **/3/** 當作其 **OrgNode** 的所有節點更新為新值。</span><span class="sxs-lookup"><span data-stu-id="84229-123">To move all of Jill's subordinates to a new manager, we will update all nodes that have **/3/** as their **OrgNode** to a new value.</span></span> <span data-ttu-id="84229-124">執行下列程式碼，將 Wanida 更新為回報給 Sariya，但是讓 Kevin 回報給 Wanida：</span><span class="sxs-lookup"><span data-stu-id="84229-124">Execute the following code to update Wanida to report to Sariya, but keep  Kevin reporting to Wanida:</span></span>  
  
    ```  
    DECLARE @OldParent hierarchyid, @NewParent hierarchyid  
    SELECT @OldParent = OrgNode FROM HumanResources.EmployeeOrg  
    WHERE EmployeeID = 119 ; -- Jill  
    SELECT @NewParent = OrgNode FROM HumanResources.EmployeeOrg  
    WHERE EmployeeID = 46 ; -- Sariya  
    DECLARE children_cursor CURSOR FOR  
    SELECT OrgNode FROM HumanResources.EmployeeOrg  
    WHERE OrgNode.GetAncestor(1) = @OldParent;  
    DECLARE @ChildId hierarchyid;  
    OPEN children_cursor  
    FETCH NEXT FROM children_cursor INTO @ChildId;  
    WHILE @@FETCH_STATUS = 0  
    BEGIN  
    START:  
        DECLARE @NewId hierarchyid;  
        SELECT @NewId = @NewParent.GetDescendant(MAX(OrgNode), NULL)  
        FROM HumanResources.EmployeeOrg WHERE OrgNode.GetAncestor(1) = @NewParent;  
  
        UPDATE HumanResources.EmployeeOrg  
        SET OrgNode = OrgNode.GetReparentedValue(@ChildId, @NewId)  
        WHERE OrgNode.IsDescendantOf(@ChildId) = 1;  
        IF @@error <> 0 GOTO START -- On error, retry  
            FETCH NEXT FROM children_cursor INTO @ChildId;  
    END  
    CLOSE children_cursor;  
    DEALLOCATE children_cursor;  
  
    ```  
  
3.  <span data-ttu-id="84229-125">執行下列程式碼以查看結果：</span><span class="sxs-lookup"><span data-stu-id="84229-125">Execute the following code to see the result:</span></span>  
  
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
/1/1//2      0x5AD0  3        291        Kevin   Marketing Intern  
/2/          0x68    1        271        John    Marketing Specialist  
/2/1/        0x6AC0  2        272        Mary    Marketing Assistant  
/3/          0x78    1        119        Jill    Marketing Specialist  
```  
  
 <span data-ttu-id="84229-126">曾經回報給 Jill (Wanida 和 Kevin) 的整個組織樹狀結構現在會回報給 Sariya。</span><span class="sxs-lookup"><span data-stu-id="84229-126">The entire organizational tree that had reported to Jill (both Wanida and Kevin) now reports to Sariya.</span></span>  
  
 <span data-ttu-id="84229-127">若要讓預存程序辨識階層的區段，請參閱 [移動子樹](../hierarchical-data-sql-server.md#BKMK_MovingSubtrees)的＜移動子樹＞一節。</span><span class="sxs-lookup"><span data-stu-id="84229-127">For a stored procedure to reorganize a section of a hierarchy, see the "Moving Subtrees" section of [Moving Subtrees](../hierarchical-data-sql-server.md#BKMK_MovingSubtrees).</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="84229-128">本課程的下一項工作</span><span class="sxs-lookup"><span data-stu-id="84229-128">Next Task in Lesson</span></span>  
 [<span data-ttu-id="84229-129">摘要：在階層式資料表中管理資料</span><span class="sxs-lookup"><span data-stu-id="84229-129">Summary: Managing Data in a Hierarchical Table</span></span>](lesson-2-5-summary-managing-data-in-a-hierarchical-table.md)  
  
  
