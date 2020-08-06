---
title: MSSQLSERVER_605 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 605 (Database Engine error)
ms.assetid: d8d3a22e-1ff8-48a4-891f-4c8619437e24
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e196fba84af492b25e798629d3e808b1bf22857e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598884"
---
# <a name="mssqlserver_605"></a><span data-ttu-id="19dd4-102">MSSQLSERVER_605</span><span class="sxs-lookup"><span data-stu-id="19dd4-102">MSSQLSERVER_605</span></span>
    
## <a name="details"></a><span data-ttu-id="19dd4-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="19dd4-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="19dd4-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="19dd4-104">Product Name</span></span>|<span data-ttu-id="19dd4-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="19dd4-105">SQL Server</span></span>|  
|<span data-ttu-id="19dd4-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="19dd4-106">Event ID</span></span>|<span data-ttu-id="19dd4-107">605</span><span class="sxs-lookup"><span data-stu-id="19dd4-107">605</span></span>|  
|<span data-ttu-id="19dd4-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="19dd4-108">Event Source</span></span>|<span data-ttu-id="19dd4-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="19dd4-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="19dd4-110">元件</span><span class="sxs-lookup"><span data-stu-id="19dd4-110">Component</span></span>|<span data-ttu-id="19dd4-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="19dd4-111">SQLEngine</span></span>|  
|<span data-ttu-id="19dd4-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="19dd4-112">Symbolic Name</span></span>|<span data-ttu-id="19dd4-113">WRONGPAGE</span><span class="sxs-lookup"><span data-stu-id="19dd4-113">WRONGPAGE</span></span>|  
|<span data-ttu-id="19dd4-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="19dd4-114">Message Text</span></span>|<span data-ttu-id="19dd4-115">嘗試提取邏輯頁 %S_PGID 失敗，資料庫：%d。</span><span class="sxs-lookup"><span data-stu-id="19dd4-115">Attempt to fetch logical page %S_PGID in database %d failed.</span></span> <span data-ttu-id="19dd4-116">它屬於配置單位 %I64d，而非屬於 %I64d。</span><span class="sxs-lookup"><span data-stu-id="19dd4-116">It belongs to allocation unit %I64d not to %I64d.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="19dd4-117">說明</span><span class="sxs-lookup"><span data-stu-id="19dd4-117">Explanation</span></span>  
 <span data-ttu-id="19dd4-118">這個錯誤通常表示指定的資料庫發生頁面或配置損毀。</span><span class="sxs-lookup"><span data-stu-id="19dd4-118">This error generally signifies page or allocation corruption in the specified database.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="19dd4-119">在讀取屬於資料表的頁面時，會循著頁面連結或利用索引配置對應 (IAM) 來偵測是否有損毀。</span><span class="sxs-lookup"><span data-stu-id="19dd4-119">detects corruption when reading pages belonging to a table either by following the page linkages or by using the Index Allocation Map (IAM).</span></span> <span data-ttu-id="19dd4-120">所有配置到給定資料表的頁面，都必須屬於與該資料表關聯的其中一個配置單位。</span><span class="sxs-lookup"><span data-stu-id="19dd4-120">All pages allocated to a table must belong to one of the allocation units associated with the table.</span></span> <span data-ttu-id="19dd4-121">包含在頁首中的配置單位識別碼若與資料表的關聯配置單位識別碼不相符，便會引發此例外狀況。</span><span class="sxs-lookup"><span data-stu-id="19dd4-121">If the allocation unit ID contained in the page header does not match an allocation unit ID associated with the table, this exception is raised.</span></span> <span data-ttu-id="19dd4-122">錯誤訊息所列的第一個配置單位識別碼是存在頁首中的識別碼，而第二個配置單位值則是資料表的關聯識別碼。</span><span class="sxs-lookup"><span data-stu-id="19dd4-122">The first allocation unit ID listed in the error message is the ID present in the page header, and the second allocation unit value is the ID associated with the table.</span></span>  
  
 <span data-ttu-id="19dd4-123">**資料損毀錯誤**</span><span class="sxs-lookup"><span data-stu-id="19dd4-123">**Data Corruption Errors**</span></span>  
  
 <span data-ttu-id="19dd4-124">嚴重性層級 21 表示資料可能已損毀。</span><span class="sxs-lookup"><span data-stu-id="19dd4-124">A severity level of 21 indicates potential data corruption.</span></span> <span data-ttu-id="19dd4-125">原因大致包括：頁面鏈結損壞、IAM 損毀，或是該物件的 [sys.objects](/sql/relational-databases/system-catalog-views/sys-objects-transact-sql) 目錄檢視包含無效的項目。</span><span class="sxs-lookup"><span data-stu-id="19dd4-125">Possible causes are a damaged page chain, a corrupt IAM, or an invalid entry in the [sys.objects](/sql/relational-databases/system-catalog-views/sys-objects-transact-sql) catalog view for that object.</span></span> <span data-ttu-id="19dd4-126">這些錯誤通常是因為硬體或磁碟裝置驅動程式失效所造成。</span><span class="sxs-lookup"><span data-stu-id="19dd4-126">These errors are often caused by hardware or disk device driver failure.</span></span>  
  
 <span data-ttu-id="19dd4-127">**暫時性錯誤**</span><span class="sxs-lookup"><span data-stu-id="19dd4-127">**Transient Errors**</span></span>  
  
 <span data-ttu-id="19dd4-128">嚴重性層級 12 表示可能發生暫時性錯誤，亦即快取有問題而不代表磁碟上的資料損壞。</span><span class="sxs-lookup"><span data-stu-id="19dd4-128">A severity level of 12 indicates a potential transient error; that is, it occurs in the cache and does not indicate damage to data on disk.</span></span> <span data-ttu-id="19dd4-129">暫時性 605 錯誤可能是因為下列狀況所造成：</span><span class="sxs-lookup"><span data-stu-id="19dd4-129">Transient 605 errors can be caused by the following conditions:</span></span>  
  
-   <span data-ttu-id="19dd4-130">作業系統向 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 誤報 I/O 作業已完成；即使資料其實並未損毀也會顯示錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="19dd4-130">The operating system prematurely notifies [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that an I/O operation has completed; the error message is displayed even though no actual data corruption exists.</span></span>  
  
 <span data-ttu-id="19dd4-131">以最佳化工具提示 NOLOCK 執行查詢，或將交易隔離等級設定為 READ UNCOMMITTED。</span><span class="sxs-lookup"><span data-stu-id="19dd4-131">Running a query with the Optimizer hint NOLOCK or setting the transaction isolation level to READ UNCOMMITTED.</span></span> <span data-ttu-id="19dd4-132">使用 NOLOCK 的查詢或者 READ UNCOMMITTED 若嘗試讀取其他使用者正在搬移或變更的資料，便會發生 605 錯誤。</span><span class="sxs-lookup"><span data-stu-id="19dd4-132">When a query that is using NOLOCK or READ UNCOMMITTED tries to read data that is being moved or changed by another user, a 605 error occurs.</span></span> <span data-ttu-id="19dd4-133">若要確認是否發生暫時性 605 錯誤，請稍後再執行一次查詢。</span><span class="sxs-lookup"><span data-stu-id="19dd4-133">To verify that it is a transient 605 error, rerun the query later.</span></span> <span data-ttu-id="19dd4-134">如需詳細資訊，請參閱這篇知識庫文章 [235880](https://support.microsoft.com/kb/235880/en-us)："You receive an "Error 605" error message when you run a query with the optimizer hint NOLOCK or you set the transaction isolation level to READ UNCOMMITTED in SQL Server" (當您使用最佳化器提示 NOLOCK 執行查詢，或在 SQL Server 中將交易隔離等級設定為 READ UNCOMMITTED 時，收到「錯誤 605」錯誤訊息)。</span><span class="sxs-lookup"><span data-stu-id="19dd4-134">For more information, see this KB article [235880](https://support.microsoft.com/kb/235880/en-us): "You receive an "Error 605" error message when you run a query with the optimizer hint NOLOCK or you set the transaction isolation level to READ UNCOMMITTED in SQL Server."</span></span>  
  
 <span data-ttu-id="19dd4-135">一般而言，如果錯誤僅在資料存取期間發生，但後續的 DBCC CHECKDB 作業均順利完成而沒有錯誤，605 錯誤可能就是暫時性錯誤。</span><span class="sxs-lookup"><span data-stu-id="19dd4-135">In general, if the error occurs during data access but subsequent DBCC CHECKDB operations complete without error, the 605 error was probably transient.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="19dd4-136">使用者動作</span><span class="sxs-lookup"><span data-stu-id="19dd4-136">User Action</span></span>  
 <span data-ttu-id="19dd4-137">如果 605 錯誤並非暫時性錯誤，問題就非常嚴重，您必須執行下列工作加以更正：</span><span class="sxs-lookup"><span data-stu-id="19dd4-137">If the 605 error is not transient, the problem is severe and must be corrected by performing the following tasks:</span></span>  
  
1.  <span data-ttu-id="19dd4-138">執行下列查詢，找出與訊息中指定的配置單位關聯的資料表。</span><span class="sxs-lookup"><span data-stu-id="19dd4-138">Identify the tables associated with the allocation units specified in the message by running the following query.</span></span> <span data-ttu-id="19dd4-139">請將 `allocation_unit_id` 改為錯誤訊息中指定的配置單位。</span><span class="sxs-lookup"><span data-stu-id="19dd4-139">Replace `allocation_unit_id` with the allocation units specified in the error message.</span></span>  
  
     <span data-ttu-id="19dd4-140">USE`database_name`;</span><span class="sxs-lookup"><span data-stu-id="19dd4-140">USE`database_name`;</span></span>  
  
     <span data-ttu-id="19dd4-141">GO</span><span class="sxs-lookup"><span data-stu-id="19dd4-141">GO</span></span>  
  
     <span data-ttu-id="19dd4-142">SELECT au.allocation_unit_id, OBJECT_NAME(p.object_id) AS table_name, fg.name AS filegroup_name,</span><span class="sxs-lookup"><span data-stu-id="19dd4-142">SELECT au.allocation_unit_id, OBJECT_NAME(p.object_id) AS table_name, fg.name AS filegroup_name,</span></span>  
  
     <span data-ttu-id="19dd4-143">au.type_desc AS allocation_type, au.data_pages, partition_number</span><span class="sxs-lookup"><span data-stu-id="19dd4-143">au.type_desc AS allocation_type, au.data_pages, partition_number</span></span>  
  
     <span data-ttu-id="19dd4-144">FROM sys.allocation_units AS au</span><span class="sxs-lookup"><span data-stu-id="19dd4-144">FROM sys.allocation_units AS au</span></span>  
  
     <span data-ttu-id="19dd4-145">JOIN sys.partitions AS p ON au.container_id = p.partition_id</span><span class="sxs-lookup"><span data-stu-id="19dd4-145">JOIN sys.partitions AS p ON au.container_id = p.partition_id</span></span>  
  
     <span data-ttu-id="19dd4-146">JOIN sys.filegroups AS fg ON fg.data_space_id = au.data_space_id</span><span class="sxs-lookup"><span data-stu-id="19dd4-146">JOIN sys.filegroups AS fg ON fg.data_space_id = au.data_space_id</span></span>  
  
     <span data-ttu-id="19dd4-147">WHERE au.allocation_unit_id = `allocation_unit_id` OR au.allocation_unit_id = `allocation_unit_id`</span><span class="sxs-lookup"><span data-stu-id="19dd4-147">WHERE au.allocation_unit_id = `allocation_unit_id` OR au.allocation_unit_id = `allocation_unit_id`</span></span>  
  
     <span data-ttu-id="19dd4-148">ORDER BY au.allocation_unit_id;</span><span class="sxs-lookup"><span data-stu-id="19dd4-148">ORDER BY au.allocation_unit_id;</span></span>  
  
     <span data-ttu-id="19dd4-149">GO</span><span class="sxs-lookup"><span data-stu-id="19dd4-149">GO</span></span>  
  
2.  <span data-ttu-id="19dd4-150">找出與錯誤訊息中指定的第二個配置單位識別碼關聯的資料表之後，對該資料表執行不含 REPAIR 子句的 DBCC CHECKTABLE。</span><span class="sxs-lookup"><span data-stu-id="19dd4-150">Execute DBCC CHECKTABLE without a REPAIR clause on the table associated with the second allocation unit ID specified in the error message.</span></span>  
  
3.  <span data-ttu-id="19dd4-151">儘快執行不含 REPAIR 子句的 DBCC CHECKDB，以了解整個資料的損毀程度有多大。</span><span class="sxs-lookup"><span data-stu-id="19dd4-151">Execute DBCC CHECKDB without a REPAIR clause as soon as possible to determine the full extent of the corruption in the entire database.</span></span>  
  
4.  <span data-ttu-id="19dd4-152">檢查錯誤記錄檔中是否有經常伴隨 605 錯誤連帶發生的其他錯誤，並查看 Windows 事件記錄檔中是否有任何的系統或硬體相關問題。</span><span class="sxs-lookup"><span data-stu-id="19dd4-152">Check the error log for other errors that often accompany a 605 error and examine the Windows Event Log for any system or hardware related issues.</span></span> <span data-ttu-id="19dd4-153">請修正前述記錄檔中所包含的任何硬體相關問題。</span><span class="sxs-lookup"><span data-stu-id="19dd4-153">Fix any hardware-related problems that are contained in the logs.</span></span>  
  
 <span data-ttu-id="19dd4-154">如果問題與硬體無關，請執行下列其中一項工作：</span><span class="sxs-lookup"><span data-stu-id="19dd4-154">If the problem is not hardware related, perform one of the following tasks:</span></span>  
  
1.  <span data-ttu-id="19dd4-155">從未受影響的備份還原資料庫。</span><span class="sxs-lookup"><span data-stu-id="19dd4-155">Restore the database from a known clean backup.</span></span> <span data-ttu-id="19dd4-156">您可以利用分頁還原備份功能，只還原損毀的頁面。</span><span class="sxs-lookup"><span data-stu-id="19dd4-156">You can leverage the page restore backup feature to restore just the damaged pages.</span></span>  
  
2.  <span data-ttu-id="19dd4-157">根據您在步驟 3 中執行 DBCC CHECKDB 作業後獲得的建議，執行內含 REPAIR 子句的 DBCC CHECKDB 以修復損毀的部分。</span><span class="sxs-lookup"><span data-stu-id="19dd4-157">Run DBCC CHECKDB with the REPAIR clause recommended by the DBCC CHECKDB operation performed in step 3 to repair the corruption.</span></span> <span data-ttu-id="19dd4-158">如果執行含 REPAIR 子句的 DBCC CHECKDB 並未修正這個問題，請與您的主要支援提供者連絡，再執行這個陳述式。</span><span class="sxs-lookup"><span data-stu-id="19dd4-158">If running DBCC CHECKDB with one of the REPAIR clauses does not correct the problem, contact your primary support provider.</span></span> <span data-ttu-id="19dd4-159">請備妥 DBCC CHECKDB 的輸出結果以供檢閱。</span><span class="sxs-lookup"><span data-stu-id="19dd4-159">Have the output from DBCC CHECKDB available for review.</span></span>  
  
    > [!CAUTION]  
    >  <span data-ttu-id="19dd4-160">如果不確定內含 REPAIR 子句之 DBCC CHECKDB 的效果為何，執行此陳述式之前請先與主要支援提供者連絡。</span><span class="sxs-lookup"><span data-stu-id="19dd4-160">If you are not sure what effect DBCC CHECKDB with a REPAIR clause has on your data, contact your primary support provider before running this statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19dd4-161">另請參閱</span><span class="sxs-lookup"><span data-stu-id="19dd4-161">See Also</span></span>  
 [<span data-ttu-id="19dd4-162">DBCC CHECKTABLE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="19dd4-162">DBCC CHECKTABLE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/database-console-commands/dbcc-checktable-transact-sql)  
  
  
