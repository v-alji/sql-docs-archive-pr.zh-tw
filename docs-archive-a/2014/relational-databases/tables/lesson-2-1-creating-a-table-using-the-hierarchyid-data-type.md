---
title: 使用 hierarchyid 資料類型建立資料表 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- HierarchyID
ms.assetid: 0d1f361f-336c-4571-99d1-f4813b2d9fc4
author: stevestein
ms.author: sstein
ms.openlocfilehash: 2c9b59795949e11cabd21b0be8de844b33d73c37
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708149"
---
# <a name="creating-a-table-using-the-hierarchyid-data-type"></a><span data-ttu-id="4bd53-102">使用 hierarchyid 資料類型建立資料表</span><span class="sxs-lookup"><span data-stu-id="4bd53-102">Creating a Table Using the hierarchyid Data Type</span></span>
  <span data-ttu-id="4bd53-103">以下範例會建立名稱為 EmployeeOrg 的資料表，其中同時包含員工資料及其回報的階層。</span><span class="sxs-lookup"><span data-stu-id="4bd53-103">The following example creates a table named EmployeeOrg, which includes employee data together with their reporting hierarchy.</span></span> <span data-ttu-id="4bd53-104">這個範例會在 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 資料庫中建立資料表，但是這是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="4bd53-104">The example creates the table in the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database, but that is optional.</span></span> <span data-ttu-id="4bd53-105">為了要維持此範例的簡單性，此資料表僅包含五個資料行：</span><span class="sxs-lookup"><span data-stu-id="4bd53-105">To keep the example simple, this table includes only five columns:</span></span>  
  
-   <span data-ttu-id="4bd53-106">OrgNode 是一個 `hierarchyid` 資料行，其中儲存階層式關聯性。</span><span class="sxs-lookup"><span data-stu-id="4bd53-106">OrgNode is a `hierarchyid` column that stores the hierarchical relationship.</span></span>  
  
-   <span data-ttu-id="4bd53-107">OrgLevel 是一個以 OrgNode 資料行為基礎的計算資料行，後者可將每個節點層級儲存在階層中。</span><span class="sxs-lookup"><span data-stu-id="4bd53-107">OrgLevel is a computed column, based on the OrgNode column that stores each nodes level in the hierarchy.</span></span> <span data-ttu-id="4bd53-108">它將會用於廣度優先的索引。</span><span class="sxs-lookup"><span data-stu-id="4bd53-108">It will be used for a breadth-first index.</span></span>  
  
-   <span data-ttu-id="4bd53-109">EmployeeID 包含用於應用程式 (例如，薪資) 的一般員工識別碼。</span><span class="sxs-lookup"><span data-stu-id="4bd53-109">EmployeeID contains the typical employee identification number that is used for applications such as payroll.</span></span> <span data-ttu-id="4bd53-110">在開發新應用程式時，這些應用程式可以使用 OrgNode 資料行，因此不需要另外的這個 EmployeeID 資料行。</span><span class="sxs-lookup"><span data-stu-id="4bd53-110">In new application development, applications can use the OrgNode column and this separate EmployeeID column is not needed.</span></span>  
  
-   <span data-ttu-id="4bd53-111">EmpName 包含員工的名稱。</span><span class="sxs-lookup"><span data-stu-id="4bd53-111">EmpName contains the name of the employee.</span></span>  
  
-   <span data-ttu-id="4bd53-112">Title 包含員工的職稱。</span><span class="sxs-lookup"><span data-stu-id="4bd53-112">Title contains the title of the employee.</span></span>  
  
### <a name="to-create-the-employeeorg-table"></a><span data-ttu-id="4bd53-113">若要建立 EmployeeOrg 資料表</span><span class="sxs-lookup"><span data-stu-id="4bd53-113">To create the EmployeeOrg table</span></span>  
  
1.  <span data-ttu-id="4bd53-114">在 [查詢編輯器] 視窗中，執行下列程式碼來建立 `EmployeeOrg` 資料表。</span><span class="sxs-lookup"><span data-stu-id="4bd53-114">In a Query Editor window, run the following code to create the `EmployeeOrg` table.</span></span> <span data-ttu-id="4bd53-115">指定 `OrgNode` 資料行做為具有叢集索引的主要索引鍵將會建立深度優先的索引：</span><span class="sxs-lookup"><span data-stu-id="4bd53-115">Specifying the `OrgNode` column as the primary key with a clustered index will create a depth-first index:</span></span>  
  
    ```  
    USE AdventureWorks2012 ;  
    GO  
    CREATE TABLE HumanResources.EmployeeOrg  
    (  
       OrgNode hierarchyid PRIMARY KEY CLUSTERED,  
       OrgLevel AS OrgNode.GetLevel(),  
       EmployeeID int UNIQUE NOT NULL,  
       EmpName varchar(20) NOT NULL,  
       Title varchar(20) NULL  
    ) ;  
    GO  
    ```  
  
2.  <span data-ttu-id="4bd53-116">執行下列程式碼，在 `OrgLevel` 和 `OrgNode` 資料行上建立複合式索引，以支援有效的廣度優先搜尋：</span><span class="sxs-lookup"><span data-stu-id="4bd53-116">Run the following code to create a composite index on the `OrgLevel` and `OrgNode` columns to support efficient breadth-first searches:</span></span>  
  
    ```  
    CREATE UNIQUE INDEX EmployeeOrgNc1   
    ON HumanResources.EmployeeOrg(OrgLevel, OrgNode) ;  
    GO  
    ```  
  
 <span data-ttu-id="4bd53-117">資料表現在已經準備好可以填寫資料。</span><span class="sxs-lookup"><span data-stu-id="4bd53-117">The table is now ready for data.</span></span> <span data-ttu-id="4bd53-118">下一個工作將是使用階層式方法擴展資料表。</span><span class="sxs-lookup"><span data-stu-id="4bd53-118">The next task will populate the table by using hierarchical methods.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="4bd53-119">本課程的下一項工作</span><span class="sxs-lookup"><span data-stu-id="4bd53-119">Next Task in Lesson</span></span>  
 [<span data-ttu-id="4bd53-120">使用階層式方法擴展階層式資料表</span><span class="sxs-lookup"><span data-stu-id="4bd53-120">Populating a Hierarchical Table Using Hierarchical Methods</span></span>](lesson-2-2-populating-a-hierarchical-table-using-hierarchical-methods.md)  
  
  
