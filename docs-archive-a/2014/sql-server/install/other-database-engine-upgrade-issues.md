---
title: 其他資料庫引擎升級問題 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Database Engine [SQL Server], upgrading
ms.assetid: 78a1d8e8-fa97-476f-8777-84617d145340
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: db496112fc975304bb2d7da9d9ea1c52e6dd8bec
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593769"
---
# <a name="other-database-engine-upgrade-issues"></a><span data-ttu-id="573fc-102">其他 Database Engine 升級問題</span><span class="sxs-lookup"><span data-stu-id="573fc-102">Other Database Engine Upgrade Issues</span></span>
  <span data-ttu-id="573fc-103">目前的 Upgrade Advisor 版本無法偵測到下列升級問題。</span><span class="sxs-lookup"><span data-stu-id="573fc-103">The following upgrade issues cannot be detected by the current version of Upgrade Advisor.</span></span> <span data-ttu-id="573fc-104">請檢閱下列問題，以便評估它們可能對您系統造成的影響。</span><span class="sxs-lookup"><span data-stu-id="573fc-104">Review the issues listed below to evaluate their potential impact to your systems.</span></span>  
  
## <a name="multiple-database-engine-deprecated-features"></a><span data-ttu-id="573fc-105">多個 Database Engine 已被取代的功能</span><span class="sxs-lookup"><span data-stu-id="573fc-105">Multiple Database Engine Deprecated Features</span></span>  
 <span data-ttu-id="573fc-106">下列 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式或選項會被取代：</span><span class="sxs-lookup"><span data-stu-id="573fc-106">The following [!INCLUDE[tsql](../../includes/tsql-md.md)] statements or options are deprecated:</span></span>  
  
-   <span data-ttu-id="573fc-107">BACKUP LOG 的 NO_LOG 和 TRUNCATE_ONLY 選項</span><span class="sxs-lookup"><span data-stu-id="573fc-107">NO_LOG and TRUNCATE_ONLY options of BACKUP LOG</span></span>  
  
-   <span data-ttu-id="573fc-108">BACKUP TRANSACTION </span><span class="sxs-lookup"><span data-stu-id="573fc-108">BACKUP TRANSACTION</span></span>  
  
-   <span data-ttu-id="573fc-109">RESTORE TRANSACTION</span><span class="sxs-lookup"><span data-stu-id="573fc-109">RESTORE TRANSACTION</span></span>  
  
-   <span data-ttu-id="573fc-110">DUMP</span><span class="sxs-lookup"><span data-stu-id="573fc-110">DUMP</span></span>  
  
-   <span data-ttu-id="573fc-111">LOAD</span><span class="sxs-lookup"><span data-stu-id="573fc-111">LOAD</span></span>  
  
-   <span data-ttu-id="573fc-112">DBCC CONCURRENCYVIOLATION</span><span class="sxs-lookup"><span data-stu-id="573fc-112">DBCC CONCURRENCYVIOLATION</span></span>  
  
-   <span data-ttu-id="573fc-113">sp_addalias</span><span class="sxs-lookup"><span data-stu-id="573fc-113">sp_addalias</span></span>  
  
-   <span data-ttu-id="573fc-114">sp_addgroup</span><span class="sxs-lookup"><span data-stu-id="573fc-114">sp_addgroup</span></span>  
  
-   <span data-ttu-id="573fc-115">sp_changegroup</span><span class="sxs-lookup"><span data-stu-id="573fc-115">sp_changegroup</span></span>  
  
-   <span data-ttu-id="573fc-116">sp_dropgroup</span><span class="sxs-lookup"><span data-stu-id="573fc-116">sp_dropgroup</span></span>  
  
-   <span data-ttu-id="573fc-117">sp_helpgroup</span><span class="sxs-lookup"><span data-stu-id="573fc-117">sp_helpgroup</span></span>  
  
-   <span data-ttu-id="573fc-118">syssegments</span><span class="sxs-lookup"><span data-stu-id="573fc-118">syssegments</span></span>  
  
 <span data-ttu-id="573fc-119">使用 VIA 通訊協定連接至 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 已被取代。</span><span class="sxs-lookup"><span data-stu-id="573fc-119">Use of the VIA protocol to connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)] is deprecated.</span></span>  
  
## <a name="new-data-types"></a><span data-ttu-id="573fc-120">新的資料類型</span><span class="sxs-lookup"><span data-stu-id="573fc-120">New Data Types</span></span>  
 <span data-ttu-id="573fc-121">下面是保留的系統類型。</span><span class="sxs-lookup"><span data-stu-id="573fc-121">The following will be reserved system types.</span></span> <span data-ttu-id="573fc-122">請在升級之前或之後，重新命名現有且衝突的使用者定義型別。</span><span class="sxs-lookup"><span data-stu-id="573fc-122">Rename the existing conflicting user defined types either before or after upgrade.</span></span>  
  
-   <span data-ttu-id="573fc-123">[地理位置]</span><span class="sxs-lookup"><span data-stu-id="573fc-123">Geography</span></span>  
  
-   <span data-ttu-id="573fc-124">幾何形狀</span><span class="sxs-lookup"><span data-stu-id="573fc-124">Geometry</span></span>  
  
-   <span data-ttu-id="573fc-125">Datetime2</span><span class="sxs-lookup"><span data-stu-id="573fc-125">Datetime2</span></span>  
  
-   <span data-ttu-id="573fc-126">HierarchyID</span><span class="sxs-lookup"><span data-stu-id="573fc-126">HierarchyID</span></span>  
  
## <a name="target-table-of-the-output-into-clause-cannot-have-any-defined-triggers"></a><span data-ttu-id="573fc-127">OUTPUT INTO 子句的目標資料表不得具有任何已定義的觸發程序</span><span class="sxs-lookup"><span data-stu-id="573fc-127">Target Table of the OUTPUT INTO Clause Cannot Have Any Defined Triggers</span></span>  
 <span data-ttu-id="573fc-128">當資料表有任何啟用的觸發程式不受支援時，輸出至目標資料表。</span><span class="sxs-lookup"><span data-stu-id="573fc-128">OUTPUT INTO a target table when the table has any enabled triggers is not supported.</span></span>  
  
## <a name="compile-time-error-for-udfs-when-the-target-of-an-output-into-clause-is-a-table"></a><span data-ttu-id="573fc-129">當 OUTPUT INTO 子句的目標是資料表時，就會針對 UDF 發生編譯時間錯誤</span><span class="sxs-lookup"><span data-stu-id="573fc-129">Compile Time Error for UDFs When the Target of an OUTPUT INTO Clause is a Table</span></span>  
 <span data-ttu-id="573fc-130">使用者定義函數 (UDF) 無法用於執行修改資料庫狀態的動作。</span><span class="sxs-lookup"><span data-stu-id="573fc-130">User-defined functions (UDF) cannot be used to perform actions that modify the database state.</span></span> <span data-ttu-id="573fc-131">例如，UDF 無法針對任何物件 (資料表變數除外) 執行任何 DDL (CREATE/ALTER/DROP) 或 DML (INSERT/UPDATE/DELETE) 動作。</span><span class="sxs-lookup"><span data-stu-id="573fc-131">For example, a UDF cannot perform any DDL (CREATE/ALTER/DROP) or DML (INSERT/UPDATE/DELETE) actions on any objects, except for table variables.</span></span>  
  
## <a name="merge-is-a-reserved-keyword"></a><span data-ttu-id="573fc-132">MERGE 是保留關鍵字</span><span class="sxs-lookup"><span data-stu-id="573fc-132">MERGE is a Reserved Keyword</span></span>  
 <span data-ttu-id="573fc-133">MERGE 現在是完整的保留關鍵字。</span><span class="sxs-lookup"><span data-stu-id="573fc-133">MERGE is now a fully-reserved keyword.</span></span> <span data-ttu-id="573fc-134">應用程式不能再具有名為 MERGE 的物件 (資料表、資料行等等)。</span><span class="sxs-lookup"><span data-stu-id="573fc-134">Applications can no longer have objects (table, column, etc.) called MERGE.</span></span>  
  
## <a name="rename-cdc-schema"></a><span data-ttu-id="573fc-135">重新命名 CDC 結構描述</span><span class="sxs-lookup"><span data-stu-id="573fc-135">Rename CDC Schema</span></span>  
 <span data-ttu-id="573fc-136">有名稱為 CDC 的結構描述。</span><span class="sxs-lookup"><span data-stu-id="573fc-136">There is a schema name called CDC.</span></span> <span data-ttu-id="573fc-137">如果已針對資料庫啟用**變更資料捕獲**，就不能使用這個架構名稱。</span><span class="sxs-lookup"><span data-stu-id="573fc-137">This schema name cannot be in used if **Change Data Capture** is enabled for the database.</span></span>  
  
 <span data-ttu-id="573fc-138">您必須先卸載 CDC 架構，才能啟用資料庫的**變更資料捕獲**。</span><span class="sxs-lookup"><span data-stu-id="573fc-138">You must drop the CDC schema before you enable **Change Data Capture** for the database.</span></span> <span data-ttu-id="573fc-139">您可以在升級之前或之後完成此步驟。</span><span class="sxs-lookup"><span data-stu-id="573fc-139">This step can be done before or after the upgrade.</span></span> <span data-ttu-id="573fc-140">若要卸除此結構描述，請使用下列步驟：</span><span class="sxs-lookup"><span data-stu-id="573fc-140">To drop the schema, use the following steps:</span></span>  
  
1.  <span data-ttu-id="573fc-141">使用 ALTER SCHEMA，將這些物件從 CDC 結構描述傳送至新的結構描述名稱。</span><span class="sxs-lookup"><span data-stu-id="573fc-141">Transfer the objects from CDC schema to a new schema name using ALTER SCHEMA.</span></span>  
  
2.  <span data-ttu-id="573fc-142">確認新結構描述中物件的權限。</span><span class="sxs-lookup"><span data-stu-id="573fc-142">Verify permissions for the objects in the new schema.</span></span>  
  
3.  <span data-ttu-id="573fc-143">針對應用程式進行必要的修改。</span><span class="sxs-lookup"><span data-stu-id="573fc-143">Make necessary modifications to the application.</span></span>  
  
4.  <span data-ttu-id="573fc-144">使用 DROP SCHEMA 來卸除 CDC 結構描述。</span><span class="sxs-lookup"><span data-stu-id="573fc-144">Drop the CDC schema using DROP SCHEMA.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="573fc-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="573fc-145">See Also</span></span>  
 [<span data-ttu-id="573fc-146">資料庫引擎升級問題</span><span class="sxs-lookup"><span data-stu-id="573fc-146">Database Engine Upgrade Issues</span></span>](../../../2014/sql-server/install/database-engine-upgrade-issues.md)  
  
  
