---
title: 系統資料庫 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- system databases [SQL Server]
- displaying system database data
- modifying system data
- viewing system database data
ms.assetid: 30468a7c-4225-4d35-aa4a-ffa7da4f1282
author: stevestein
ms.author: sstein
ms.openlocfilehash: 65deee685c2205a7c6e41ed86f71c69639555d7c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686961"
---
# <a name="system-databases"></a><span data-ttu-id="1ddab-102">系統資料庫</span><span class="sxs-lookup"><span data-stu-id="1ddab-102">System Databases</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="1ddab-103">包括下列系統資料庫。</span><span class="sxs-lookup"><span data-stu-id="1ddab-103">includes the following system databases.</span></span>  
  
|<span data-ttu-id="1ddab-104">系統資料庫</span><span class="sxs-lookup"><span data-stu-id="1ddab-104">System database</span></span>|<span data-ttu-id="1ddab-105">描述</span><span class="sxs-lookup"><span data-stu-id="1ddab-105">Description</span></span>|  
|---------------------|-----------------|  
|[<span data-ttu-id="1ddab-106">master 資料庫</span><span class="sxs-lookup"><span data-stu-id="1ddab-106">master Database</span></span>](master-database.md)|<span data-ttu-id="1ddab-107">記錄 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]執行個體的所有系統層級資訊。</span><span class="sxs-lookup"><span data-stu-id="1ddab-107">Records all the system-level information for an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>|  
|[<span data-ttu-id="1ddab-108">msdb 資料庫</span><span class="sxs-lookup"><span data-stu-id="1ddab-108">msdb Database</span></span>](msdb-database.md)|<span data-ttu-id="1ddab-109">由 SQL Server Agent 用於排程警示和作業。</span><span class="sxs-lookup"><span data-stu-id="1ddab-109">Is used by SQL Server Agent for scheduling alerts and jobs.</span></span>|  
|[<span data-ttu-id="1ddab-110">model 資料庫</span><span class="sxs-lookup"><span data-stu-id="1ddab-110">model Database</span></span>](model-database.md)|<span data-ttu-id="1ddab-111">用來當作 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]執行個體上建立之所有資料庫的範本。</span><span class="sxs-lookup"><span data-stu-id="1ddab-111">Is used as the template for all databases created on the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="1ddab-112">對 **model** 資料庫進行的修改 (例如，資料庫大小、定序、復原模式和其他資料庫選項) 會套用到之後建立的任何資料庫。</span><span class="sxs-lookup"><span data-stu-id="1ddab-112">Modifications made to the **model** database, such as database size, collation, recovery model, and other database options, are applied to any databases created afterward.</span></span>|  
|[<span data-ttu-id="1ddab-113">Resource 資料庫</span><span class="sxs-lookup"><span data-stu-id="1ddab-113">Resource Database</span></span>](resource-database.md)|<span data-ttu-id="1ddab-114">是一個唯讀的資料庫，其中包含 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]擁有的系統物件。</span><span class="sxs-lookup"><span data-stu-id="1ddab-114">Is a read-only database that contains system objects that are included with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="1ddab-115">系統物件實際上會保存在 **Resource** 資料庫中，但邏輯上會出現在每個資料庫的 **sys** 結構描述中。</span><span class="sxs-lookup"><span data-stu-id="1ddab-115">System objects are physically persisted in the **Resource** database, but they logically appear in the **sys** schema of every database.</span></span>|  
|[<span data-ttu-id="1ddab-116">tempdb 資料庫</span><span class="sxs-lookup"><span data-stu-id="1ddab-116">tempdb Database</span></span>](tempdb-database.md)|<span data-ttu-id="1ddab-117">是保存暫存物件或中繼結果集的工作空間。</span><span class="sxs-lookup"><span data-stu-id="1ddab-117">Is a workspace for holding temporary objects or intermediate result sets.</span></span>|  
  
## <a name="modifying-system-data"></a><span data-ttu-id="1ddab-118">修改系統資料</span><span class="sxs-lookup"><span data-stu-id="1ddab-118">Modifying System Data</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="1ddab-119">不支援使用者直接更新系統物件中的資訊，例如系統資料表、系統預存程序和目錄檢視。</span><span class="sxs-lookup"><span data-stu-id="1ddab-119">does not support users directly updating the information in system objects such as system tables, system stored procedures, and catalog views.</span></span> <span data-ttu-id="1ddab-120">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 另外提供了一組完整的管理工具，讓使用者可以完全管理他們的系統，並管理資料庫中所有的使用者與物件。</span><span class="sxs-lookup"><span data-stu-id="1ddab-120">Instead, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provides a complete set of administrative tools that let users fully administer their system and manage all users and objects in a database.</span></span> <span data-ttu-id="1ddab-121">這些選項包括：</span><span class="sxs-lookup"><span data-stu-id="1ddab-121">These include the following:</span></span>  
  
-   <span data-ttu-id="1ddab-122">管理公用程式，例如 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="1ddab-122">Administration utilities, such as [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
-   <span data-ttu-id="1ddab-123">SQL-SMO API。</span><span class="sxs-lookup"><span data-stu-id="1ddab-123">SQL-SMO API.</span></span> <span data-ttu-id="1ddab-124">可讓程式設計人員加入完整的功能，以在應用程式中管理 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="1ddab-124">This lets programmers include complete functionality for administering [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in their applications.</span></span>  
  
-   [!INCLUDE[tsql](../../includes/tsql-md.md)] <span data-ttu-id="1ddab-125">指令碼和預存程序。</span><span class="sxs-lookup"><span data-stu-id="1ddab-125">scripts and stored procedures.</span></span> <span data-ttu-id="1ddab-126">上述項目可以使用系統預存程序和 [!INCLUDE[tsql](../../includes/tsql-md.md)] DDL 陳述式。</span><span class="sxs-lookup"><span data-stu-id="1ddab-126">These can use system stored procedures and [!INCLUDE[tsql](../../includes/tsql-md.md)] DDL statements.</span></span>  
  
 <span data-ttu-id="1ddab-127">這些工具可避免應用程式在系統物件中被變更。</span><span class="sxs-lookup"><span data-stu-id="1ddab-127">These tools shield applications from changes in the system objects.</span></span> <span data-ttu-id="1ddab-128">例如， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 有時需要在新版的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中變更系統資料表，以支援加入該版本的新功能。</span><span class="sxs-lookup"><span data-stu-id="1ddab-128">For example, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sometimes has to change the system tables in new versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to support new functionality that is being added in that version.</span></span> <span data-ttu-id="1ddab-129">提出直接參考系統資料表的 SELECT 陳述式之應用程式，它們通常依賴系統資料表的舊有格式。</span><span class="sxs-lookup"><span data-stu-id="1ddab-129">Applications issuing SELECT statements that directly reference system tables are frequently dependent on the old format of the system tables.</span></span> <span data-ttu-id="1ddab-130">站台可能要等到重寫從系統資料表選取的應用程式之後，才能夠升級到新版的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="1ddab-130">Sites may not be able to upgrade to a new version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] until they have rewritten applications that are selecting from system tables.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="1ddab-131">會考量系統預存程序、DDL 和 SQL-SMO 發行的介面，並努力維護這些介面的回溯相容性。</span><span class="sxs-lookup"><span data-stu-id="1ddab-131">considers the system stored procedures, DDL, and SQL-SMO published interfaces, and works to maintain the backward compatibility of these interfaces.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="1ddab-132">並不支援在系統資料表上定義的觸發程序，因為這些觸發程序可能會修改系統的作業。</span><span class="sxs-lookup"><span data-stu-id="1ddab-132">does not support triggers defined on the system tables, because they might modify the operation of the system.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1ddab-133">系統資料庫無法位於 UNC 共用目錄。</span><span class="sxs-lookup"><span data-stu-id="1ddab-133">System databases cannot reside on UNC share directories.</span></span>  
  
## <a name="viewing-system-database-data"></a><span data-ttu-id="1ddab-134">檢視系統資料庫資料</span><span class="sxs-lookup"><span data-stu-id="1ddab-134">Viewing System Database Data</span></span>  
 <span data-ttu-id="1ddab-135">您不應撰寫直接查詢系統資料表的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式，除非這是取得應用程式所需資訊的唯一方式。</span><span class="sxs-lookup"><span data-stu-id="1ddab-135">You should not code [!INCLUDE[tsql](../../includes/tsql-md.md)] statements that directly query the system tables, unless that is the only way to obtain the information that is required by the application.</span></span> <span data-ttu-id="1ddab-136">相反地，應用程式應使用下列方法取得目錄和系統資訊：</span><span class="sxs-lookup"><span data-stu-id="1ddab-136">Instead, applications should obtain catalog and system information by using the following:</span></span>  
  
-   <span data-ttu-id="1ddab-137">系統目錄檢視</span><span class="sxs-lookup"><span data-stu-id="1ddab-137">System catalog views</span></span>  
  
-   <span data-ttu-id="1ddab-138">SQL-SMO</span><span class="sxs-lookup"><span data-stu-id="1ddab-138">SQL-SMO</span></span>  
  
-   <span data-ttu-id="1ddab-139">Windows Management Instrumentation (WMI) 介面</span><span class="sxs-lookup"><span data-stu-id="1ddab-139">Windows Management Instrumentation (WMI) interface</span></span>  
  
-   <span data-ttu-id="1ddab-140">用於應用程式的資料 API 之 Catalog 函數、方法、屬性 (attribute) 或屬性 (property)，例如 ADO、OLE DB 或 ODBC。</span><span class="sxs-lookup"><span data-stu-id="1ddab-140">Catalog functions, methods, attributes, or properties of the data API used in the application, such as ADO, OLE DB, or ODBC.</span></span>  
  
-   [!INCLUDE[tsql](../../includes/tsql-md.md)] <span data-ttu-id="1ddab-141">系統預存程序和內建函數。</span><span class="sxs-lookup"><span data-stu-id="1ddab-141">system stored procedures and built-in functions.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="1ddab-142">相關工作</span><span class="sxs-lookup"><span data-stu-id="1ddab-142">Related Tasks</span></span>  
 [<span data-ttu-id="1ddab-143">系統資料庫的備份與還原 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="1ddab-143">Back Up and Restore of System Databases &#40;SQL Server&#41;</span></span>](../backup-restore/back-up-and-restore-of-system-databases-sql-server.md)  
  
 [<span data-ttu-id="1ddab-144">在物件總管中隱藏系統物件</span><span class="sxs-lookup"><span data-stu-id="1ddab-144">Hide System Objects in Object Explorer</span></span>](../../ssms/object/object-explorer.md)  
  
## <a name="related-content"></a><span data-ttu-id="1ddab-145">相關內容</span><span class="sxs-lookup"><span data-stu-id="1ddab-145">Related Content</span></span>  
 [<span data-ttu-id="1ddab-146">目錄檢視 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="1ddab-146">Catalog Views &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/catalog-views-transact-sql)  
  
 [<span data-ttu-id="1ddab-147">資料庫</span><span class="sxs-lookup"><span data-stu-id="1ddab-147">Databases</span></span>](databases.md)  
  
  
