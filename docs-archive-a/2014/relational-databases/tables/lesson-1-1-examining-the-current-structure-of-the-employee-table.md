---
title: 檢查 Employee 資料表的目前結構 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- examining the current structure of the employee
ms.assetid: d546a820-105a-417d-ac35-44a6d1d70ac6
author: stevestein
ms.author: sstein
ms.openlocfilehash: b7f63773ebc1f28fb24f8f1000c3f87ee4d50544
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584344"
---
# <a name="examining-the-current-structure-of-the-employee-table"></a><span data-ttu-id="6ba6b-102">檢查 Employee 資料表的目前結構</span><span class="sxs-lookup"><span data-stu-id="6ba6b-102">Examining the Current Structure of the Employee Table</span></span>
  <span data-ttu-id="6ba6b-103">[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 範例資料庫在 **HumanResources** 結構描述中包含一個 **Employee** 資料表。</span><span class="sxs-lookup"><span data-stu-id="6ba6b-103">The sample [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database contains an **Employee** table in the **HumanResources** schema.</span></span> <span data-ttu-id="6ba6b-104">為避免變更原始資料表，此步驟會製作一個名為 **EmployeeDemo** 的 **Employee**資料表複本。</span><span class="sxs-lookup"><span data-stu-id="6ba6b-104">To avoid changing the original table, this step makes a copy of the **Employee** table named **EmployeeDemo**.</span></span> <span data-ttu-id="6ba6b-105">若要簡化範例，您僅能從原始資料表複製五個資料行。</span><span class="sxs-lookup"><span data-stu-id="6ba6b-105">To simplify the example, you only copy five columns from the original table.</span></span> <span data-ttu-id="6ba6b-106">然後，您可以查詢**HumanResources. EmployeeDemo**資料表，以查看資料在資料表中的結構，而不需要使用 `hierarchyid` 資料類型。</span><span class="sxs-lookup"><span data-stu-id="6ba6b-106">Then, you query the **HumanResources.EmployeeDemo** table to review how the data is structured in a table without using the `hierarchyid` data type.</span></span>  
  
### <a name="to-copy-the-employee-table"></a><span data-ttu-id="6ba6b-107">複製 Employee 資料表</span><span class="sxs-lookup"><span data-stu-id="6ba6b-107">To copy the Employee table</span></span>  
  
1.  <span data-ttu-id="6ba6b-108">在 [查詢編輯器] 視窗中執行下列程式碼，以便將資料表結構和資料從 **Employee** 資料表複製到名稱為 **EmployeeDemo**的新資料表。</span><span class="sxs-lookup"><span data-stu-id="6ba6b-108">In a Query Editor window, run the following code to copy the table structure and data from the **Employee** table into a new table named **EmployeeDemo**.</span></span>  
  
    ```  
    USE AdventureWorks ;  
    GO  
  
    SELECT EmployeeID, LoginID, ManagerID, Title, HireDate   
    INTO HumanResources.EmployeeDemo   
    FROM HumanResources.Employee ;  
    GO  
    ```  
  
### <a name="to-examine-the-structure-and-data-of-the-employeedemo-table"></a><span data-ttu-id="6ba6b-109">檢查 EmployeeDemo 資料表的結構和資料</span><span class="sxs-lookup"><span data-stu-id="6ba6b-109">To examine the structure and data of the EmployeeDemo table</span></span>  
  
-   <span data-ttu-id="6ba6b-110">這個新的 **EmployeeDemo** 資料表代表現有的資料庫中，您想要移轉成新結構的一般資料表。</span><span class="sxs-lookup"><span data-stu-id="6ba6b-110">This new **EmployeeDemo** table represents a typical table in an existing database that you might want to migrate to a new structure.</span></span> <span data-ttu-id="6ba6b-111">在 [查詢編輯器] 視窗中，執行下列程式碼以顯示資料表如何使用自我聯結來顯示員工/主管關聯性：</span><span class="sxs-lookup"><span data-stu-id="6ba6b-111">In a Query Editor window, run the following code to show how the table uses a self join to display the employee/manager relationships:</span></span>  
  
    ```  
    SELECT   
         Mgr.EmployeeID AS MgrID, Mgr.LoginID AS Manager,   
         Emp.EmployeeID AS E_ID, Emp.LoginID, Emp.Title  
    FROM HumanResources.EmployeeDemo AS Emp  
    LEFT JOIN HumanResources.EmployeeDemo AS Mgr  
    ON Emp.ManagerID = Mgr.EmployeeID  
    ORDER BY MgrID, E_ID  
    ```  
  
     [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
    ```  
    MgrID Manager                 E_ID LoginID                  Title  
    NULL NULL                      109 adventure-works\ken0     Chief Executive Officer  
    3    adventure-works\roberto0  4   adventure-works\rob0     Senior Tool Designer  
    3    adventure-works\roberto0  9   adventure-works\gail0    Design Engineer  
    3    adventure-works\roberto0  11  adventure-works\jossef0  Design Engineer  
    3    adventure-works\roberto0  158 adventure-works\dylan0   Research and Development Manager  
    3    adventure-works\roberto0  263 adventure-works\ovidiu0  Senior Tool Designer  
    3    adventure-works\roberto0  267 adventure-works\michael8 Senior Design Engineer  
    3    adventure-works\roberto0  270 adventure-works\sharon0  Design Engineer  
    6    adventure-works\david0    2   adventure-works\kevin0   Marketing Assistant  
    ...  
    ```  
  
     <span data-ttu-id="6ba6b-112">會繼續顯示結果，總共包含 290 個資料列。</span><span class="sxs-lookup"><span data-stu-id="6ba6b-112">The results continue for a total of 290 rows.</span></span>  
  
 <span data-ttu-id="6ba6b-113">請注意，`ORDER BY` 子句會使輸出將每個管理層級的下屬列在一起。</span><span class="sxs-lookup"><span data-stu-id="6ba6b-113">Notice that the `ORDER BY` clause caused the output to list the direct reports of each management level together.</span></span> <span data-ttu-id="6ba6b-114">例如， **MgrID** 3 (roberto0) 的全部七個直屬員工會緊接著彼此列出。</span><span class="sxs-lookup"><span data-stu-id="6ba6b-114">For instance, all seven of the direct reports of **MgrID** 3 (roberto0) are listed adjacent to each other.</span></span> <span data-ttu-id="6ba6b-115">雖然並非不可能，但是要將最終回報給 **MgrID** 3 的所有人群組在一起更為困難。</span><span class="sxs-lookup"><span data-stu-id="6ba6b-115">Although not impossible, it is much more difficult to group all those who eventually report to **MgrID** 3.</span></span>  
  
 <span data-ttu-id="6ba6b-116">在下一項工作中，我們將建立資料類型為 `hierarchyid` 的新資料表，然後將資料移到這個新資料表中。</span><span class="sxs-lookup"><span data-stu-id="6ba6b-116">In the next task, we will create a new table with a `hierarchyid` data type, and move the data into the new table.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="6ba6b-117">本課程的下一項工作</span><span class="sxs-lookup"><span data-stu-id="6ba6b-117">Next Task in Lesson</span></span>  
 [<span data-ttu-id="6ba6b-118">使用現有的階層式資料填入資料表</span><span class="sxs-lookup"><span data-stu-id="6ba6b-118">Populating a Table with Existing Hierarchical Data</span></span>](lesson-1-2-populating-a-table-with-existing-hierarchical-data.md)  
  
  
