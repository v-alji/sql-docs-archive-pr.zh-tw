---
title: HumanResources.myTeam 範例資料表 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- myTeam sample table [SQL Server]
- bulk importing [SQL Server], examples
- bulk exporting [SQL Server], examples
ms.assetid: 27da45a0-c1f4-4bf4-ab24-6196e80d3834
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 7d4e0cbbf42c2bdd25e3dd7c9577e4d0ec44549a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598384"
---
# <a name="humanresourcesmyteam-sample-table-sql-server"></a><span data-ttu-id="87a39-102">HumanResources.myTeam 範例資料表 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="87a39-102">HumanResources.myTeam Sample Table (SQL Server)</span></span>
  <span data-ttu-id="87a39-103">[匯入和匯出大量資料](bulk-import-and-export-of-data-sql-server.md) 中有許多程式碼範例都需要一個特殊用途的測試資料表，此資料表名為 **myTeam**。</span><span class="sxs-lookup"><span data-stu-id="87a39-103">Many of the code examples in [Importing and Exporting Bulk Data](bulk-import-and-export-of-data-sql-server.md) require a special-purpose test table named **myTeam**.</span></span> <span data-ttu-id="87a39-104">執行這些範例前，您必須先在 **資料庫的** HumanResources **結構描述中建立** myTeam [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 資料表。</span><span class="sxs-lookup"><span data-stu-id="87a39-104">Before you can run the examples, you must create the **myTeam** table in the **HumanResources** schema of the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] <span data-ttu-id="87a39-105">是 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]的其中一個範例資料庫。</span><span class="sxs-lookup"><span data-stu-id="87a39-105">is one of the sample databases in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span>  
  
 <span data-ttu-id="87a39-106">**myTeam** 資料表包含下列資料行。</span><span class="sxs-lookup"><span data-stu-id="87a39-106">The **myTeam** table is contains the following columns.</span></span>  
  
|<span data-ttu-id="87a39-107">資料行</span><span class="sxs-lookup"><span data-stu-id="87a39-107">Column</span></span>|<span data-ttu-id="87a39-108">資料類型</span><span class="sxs-lookup"><span data-stu-id="87a39-108">Data type</span></span>|<span data-ttu-id="87a39-109">Null 屬性</span><span class="sxs-lookup"><span data-stu-id="87a39-109">Nullability</span></span>|<span data-ttu-id="87a39-110">描述</span><span class="sxs-lookup"><span data-stu-id="87a39-110">Description</span></span>|  
|------------|---------------|-----------------|-----------------|  
|<span data-ttu-id="87a39-111">**EmployeeID**</span><span class="sxs-lookup"><span data-stu-id="87a39-111">**EmployeeID**</span></span>|`smallint`|<span data-ttu-id="87a39-112">非 Null</span><span class="sxs-lookup"><span data-stu-id="87a39-112">Not null</span></span>|<span data-ttu-id="87a39-113">資料列的主索引鍵。</span><span class="sxs-lookup"><span data-stu-id="87a39-113">Primary key for the rows.</span></span> <span data-ttu-id="87a39-114">小組某個成員的員工識別碼。</span><span class="sxs-lookup"><span data-stu-id="87a39-114">Employee ID of a member of my team.</span></span>|  
|<span data-ttu-id="87a39-115">**名稱**</span><span class="sxs-lookup"><span data-stu-id="87a39-115">**Name**</span></span>|`nvarchar(50)`|<span data-ttu-id="87a39-116">非 Null</span><span class="sxs-lookup"><span data-stu-id="87a39-116">Not null</span></span>|<span data-ttu-id="87a39-117">小組某個成員的名稱。</span><span class="sxs-lookup"><span data-stu-id="87a39-117">Name of a member of my team.</span></span>|  
|<span data-ttu-id="87a39-118">**Title** (標題)</span><span class="sxs-lookup"><span data-stu-id="87a39-118">**Title**</span></span>|`nvarchar(50)`|<span data-ttu-id="87a39-119">Nullable</span><span class="sxs-lookup"><span data-stu-id="87a39-119">Nullable</span></span>|<span data-ttu-id="87a39-120">小組中工作的員工之職稱。</span><span class="sxs-lookup"><span data-stu-id="87a39-120">Title the employee performs on my team.</span></span>|  
|<span data-ttu-id="87a39-121">**背景**</span><span class="sxs-lookup"><span data-stu-id="87a39-121">**Background**</span></span>|`nvarchar(50)`|<span data-ttu-id="87a39-122">非 Null</span><span class="sxs-lookup"><span data-stu-id="87a39-122">Not null</span></span>|<span data-ttu-id="87a39-123">資料列上次更新的日期和時間。</span><span class="sxs-lookup"><span data-stu-id="87a39-123">Date and time the row was last updated.</span></span> <span data-ttu-id="87a39-124">(預設值)</span><span class="sxs-lookup"><span data-stu-id="87a39-124">(Default)</span></span>|  
  
 <span data-ttu-id="87a39-125">**若要建立 HumanResources.myTeam**</span><span class="sxs-lookup"><span data-stu-id="87a39-125">**To create HumanResources.myTeam**</span></span>  
  
-   <span data-ttu-id="87a39-126">使用下列 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式：</span><span class="sxs-lookup"><span data-stu-id="87a39-126">Use the following [!INCLUDE[tsql](../../includes/tsql-md.md)] statements:</span></span>  
  
    ```  
    --Create HumanResources.MyTeam:   
    USE AdventureWorks;  
    GO  
    CREATE TABLE HumanResources.myTeam   
    (EmployeeID smallint NOT NULL,  
    Name nvarchar(50) NOT NULL,  
    Title nvarchar(50) NULL,  
    Background nvarchar(50) NOT NULL DEFAULT ''  
    );  
    GO  
    ```  
  
 <span data-ttu-id="87a39-127">**若要擴展 HumanResources.myTeam**</span><span class="sxs-lookup"><span data-stu-id="87a39-127">**To populate HumanResources.myTeam**</span></span>  
  
-   <span data-ttu-id="87a39-128">執行下列 `INSERT` 陳述式，將資料表擴展為兩個資料列：</span><span class="sxs-lookup"><span data-stu-id="87a39-128">Execute following `INSERT` statements to populate the table with two rows:</span></span>  
  
    ```  
    USE AdventureWorks;  
    GO  
    INSERT INTO HumanResources.myTeam(EmployeeID,Name,Title,Background)  
       VALUES(77,'Mia Doppleganger','Administrative Assistant','Microsoft Office');  
    GO  
    INSERT INTO HumanResources.myTeam(EmployeeID,Name,Title,Background)  
       VALUES(49,'Hirum Mollicat','I.T. Specialist','Report Writing and Data Mining');  
    GO  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="87a39-129">這些陳述式會略過第四個資料行 `Background`。</span><span class="sxs-lookup"><span data-stu-id="87a39-129">These statements skip the fourth column, `Background`.</span></span> <span data-ttu-id="87a39-130">這有預設值。</span><span class="sxs-lookup"><span data-stu-id="87a39-130">This has a default value.</span></span> <span data-ttu-id="87a39-131">略過這個資料行會造成這個 `INSERT` 陳述式將該資料行保留為空白。</span><span class="sxs-lookup"><span data-stu-id="87a39-131">Skipping this column causes this `INSERT` statement to leave this column blank.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87a39-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="87a39-132">See Also</span></span>  
 [<span data-ttu-id="87a39-133">資料的大量匯入及匯出 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="87a39-133">Bulk Import and Export of Data &#40;SQL Server&#41;</span></span>](bulk-import-and-export-of-data-sql-server.md)  
  
  
