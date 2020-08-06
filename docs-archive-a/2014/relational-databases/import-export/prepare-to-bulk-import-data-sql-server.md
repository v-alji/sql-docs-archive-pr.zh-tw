---
title: 準備大量匯入資料 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- bulk importing [SQL Server], about bulk importing
- BULK INSERT statement, guidelines
- BULK INSERT statement, restrictions
- bcp utility [SQL Server], guidelines
- bcp utility [SQL Server], restrictions
- hidden characters
- OPENROWSET function, BCP guidelines
ms.assetid: a82ef43c-d006-4c71-bfca-f001a3ba1ba0
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 03d45d9c79082b255e9b8b0e4804c50855a3ad7b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708406"
---
# <a name="prepare-to-bulk-import-data-sql-server"></a><span data-ttu-id="4d8d9-102">準備大量匯入資料 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="4d8d9-102">Prepare to Bulk Import Data (SQL Server)</span></span>
  <span data-ttu-id="4d8d9-103">您可以使用 **bcp** 命令、BULK INSERT 陳述式或 OPENROWSET(BULK) 函數，僅從資料檔案大量匯入資料。</span><span class="sxs-lookup"><span data-stu-id="4d8d9-103">You can use the **bcp** command, BULK INSERT statement, or OPENROWSET(BULK) function to bulk import data from a data file only.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4d8d9-104">撰寫自訂應用程式來從物件 (而非文字檔) 大量匯入資料也是可行的。</span><span class="sxs-lookup"><span data-stu-id="4d8d9-104">It is possible to write a custom application that bulk imports data from objects other than a text file.</span></span> <span data-ttu-id="4d8d9-105">若要從記憶體緩衝區大量匯入資料，請使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client (ODBC) 應用程式開發介面 (API) 或 OLE DB **IRowsetFastLoad** 介面的 bcp 延伸模組。</span><span class="sxs-lookup"><span data-stu-id="4d8d9-105">To bulk import data from memory buffers, use either the bcp extensions to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client (ODBC) application programming interface (API) or the OLE DB **IRowsetFastLoad** interface.</span></span>  <span data-ttu-id="4d8d9-106">若要從 C# 資料表大量匯入資料，請使用 ADO.NET 大量複製 API **SqlBulkCopy**。</span><span class="sxs-lookup"><span data-stu-id="4d8d9-106">To bulk import data from a C# data table, use the ADO.NET bulk-copy API, **SqlBulkCopy**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4d8d9-107">不支援大量匯入資料到遠端資料表。</span><span class="sxs-lookup"><span data-stu-id="4d8d9-107">Bulk importing data into a remote table is not supported.</span></span>  
  
 <span data-ttu-id="4d8d9-108">當您將資料檔案中資料大量匯入到 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的執行個體時，請使用下列方針：</span><span class="sxs-lookup"><span data-stu-id="4d8d9-108">Use the following guidelines when you bulk import data from a data file to an instance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:</span></span>  
  
-   <span data-ttu-id="4d8d9-109">為您的使用者帳戶取得必要的權限。</span><span class="sxs-lookup"><span data-stu-id="4d8d9-109">Obtain required permissions for your user account.</span></span>  
  
     <span data-ttu-id="4d8d9-110">使用者帳戶，用來使用 **bcp** 公用程式、BULK INSERT 陳述式或 INSERT ...SELECT \* FROM OPENROWSET(BULK...) 陳述式的使用者帳戶必須擁有資料表的必要權限 (由資料表擁有者指派)。</span><span class="sxs-lookup"><span data-stu-id="4d8d9-110">The user account in which you use the **bcp** utility, the BULK INSERT statement, or the INSERT ... SELECT \* FROM OPENROWSET(BULK...) statement must have the required permissions on the table, which are assigned by the table owner.</span></span> <span data-ttu-id="4d8d9-111">如需每個方法所需之權限的詳細資訊，請參閱 [bcp 公用程式](../../tools/bcp-utility.md)、 [OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql)和 [BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="4d8d9-111">For more information about permissions that are required by each method, see [bcp Utility](../../tools/bcp-utility.md), [OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql), and [BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql).</span></span>  
  
-   <span data-ttu-id="4d8d9-112">使用大量記錄復原模式。</span><span class="sxs-lookup"><span data-stu-id="4d8d9-112">Use the bulk-logged recovery model.</span></span>  
  
     <span data-ttu-id="4d8d9-113">這個指導方針適用於使用完整復原模式的資料庫。</span><span class="sxs-lookup"><span data-stu-id="4d8d9-113">This guideline is for a database that uses the full recovery model.</span></span> <span data-ttu-id="4d8d9-114">大量記錄復原模式在對未編製索引的資料表 (「堆積」  ) 執行大量作業時很有用。</span><span class="sxs-lookup"><span data-stu-id="4d8d9-114">The bulk-logged recovery model is useful when performing bulk operations into an unindexed table (a *heap*).</span></span> <span data-ttu-id="4d8d9-115">因為大量記錄復原不會執行記錄檔資料列插入的作業，所以使用大量記錄復原模式，將有助於防止因記錄交易而用盡空間的情形。</span><span class="sxs-lookup"><span data-stu-id="4d8d9-115">Using bulk-logged recovery helps prevent the transaction log from running out of space because bulk-logged recovery does not perform log row inserts.</span></span> <span data-ttu-id="4d8d9-116">如需大量記錄復原模式的詳細資訊，請參閱[復原模式 &#40;SQL Server&#41;](../backup-restore/recovery-models-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="4d8d9-116">For more information about the bulk-logged recovery model, see [Recovery Models &#40;SQL Server&#41;](../backup-restore/recovery-models-sql-server.md).</span></span>  
  
     <span data-ttu-id="4d8d9-117">建議您在大量匯入作業之前，立即將資料庫變更為使用大量記錄復原模式。</span><span class="sxs-lookup"><span data-stu-id="4d8d9-117">We recommend that you change the database to use the bulk-logged recovery model immediately before the bulk import operation.</span></span> <span data-ttu-id="4d8d9-118">事後則應立刻將資料庫重設成完整復原模式。</span><span class="sxs-lookup"><span data-stu-id="4d8d9-118">Immediately afterwards, you should reset the database to the full recovery model.</span></span> <span data-ttu-id="4d8d9-119">如需詳細資訊，請參閱[檢視或變更資料庫的復原模式 &#40;SQL Server&#41;](../backup-restore/view-or-change-the-recovery-model-of-a-database-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="4d8d9-119">For more information, see [View or Change the Recovery Model of a Database &#40;SQL Server&#41;](../backup-restore/view-or-change-the-recovery-model-of-a-database-sql-server.md).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="4d8d9-120">如需如何在大量匯入作業期間盡量減少記錄的詳細資訊，請參閱 [大量匯入採用最低限度記錄的必要條件](prerequisites-for-minimal-logging-in-bulk-import.md)。</span><span class="sxs-lookup"><span data-stu-id="4d8d9-120">more information about how to minimize logging during bulk import operations, see [Prerequisites for Minimal Logging in Bulk Import](prerequisites-for-minimal-logging-in-bulk-import.md).</span></span>  
  
-   <span data-ttu-id="4d8d9-121">在大量匯入資料之後備份。</span><span class="sxs-lookup"><span data-stu-id="4d8d9-121">Back up after bulk importing data.</span></span>  
  
     <span data-ttu-id="4d8d9-122">如果是使用簡單復原模式的資料庫，我們建議您在大量匯入作業完成之後進行完整或差異備份。</span><span class="sxs-lookup"><span data-stu-id="4d8d9-122">For a database that uses the simple recovery model, we recommend that you take a full or differential backup after the bulk-import operation finishes.</span></span> <span data-ttu-id="4d8d9-123">如需詳細資訊，請參閱[建立完整資料庫備份 &#40;SQL Server&#41;](../backup-restore/create-a-full-database-backup-sql-server.md) 或[建立差異資料庫備份 &#40;SQL Server&#41;](../backup-restore/create-a-differential-database-backup-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="4d8d9-123">For more information, see [Create a Full Database Backup &#40;SQL Server&#41;](../backup-restore/create-a-full-database-backup-sql-server.md) or [Create a Differential Database Backup &#40;SQL Server&#41;](../backup-restore/create-a-differential-database-backup-sql-server.md).</span></span>  
  
     <span data-ttu-id="4d8d9-124">如果是大量記錄復原模式或完整復原模式，記錄備份便已足夠。</span><span class="sxs-lookup"><span data-stu-id="4d8d9-124">For the bulk-logged recovery model or full recovery model, a log backup is enough.</span></span> <span data-ttu-id="4d8d9-125">如需詳細資訊，請參閱[套用交易記錄備份 &#40;SQL Server&#41;](../backup-restore/transaction-log-backups-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="4d8d9-125">For more information, see [Transaction Log Backups &#40;SQL Server&#41;](../backup-restore/transaction-log-backups-sql-server.md).</span></span>  
  
-   <span data-ttu-id="4d8d9-126">卸除資料表索引以改善大型大量匯入的效能。</span><span class="sxs-lookup"><span data-stu-id="4d8d9-126">Drop table indexes to improve performance for large bulk imports.</span></span>  
  
     <span data-ttu-id="4d8d9-127">這個指導方針的使用時機，是要匯入的資料量比資料表內的資料量多出很多時。</span><span class="sxs-lookup"><span data-stu-id="4d8d9-127">This guideline is for when you are importing a large amount of data compared to the amount of data that is already in the table.</span></span> <span data-ttu-id="4d8d9-128">在此情況下，在執行大量匯入作業之前從資料表卸除索引可以大幅提高效能。</span><span class="sxs-lookup"><span data-stu-id="4d8d9-128">In this case, dropping the indexes from the table before you perform the bulk-import operation can significantly increase performance.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="4d8d9-129">但是，如果載入小量資料 (相較於已存在資料表中的資料量)，卸除索引可能會造成不良的後果。</span><span class="sxs-lookup"><span data-stu-id="4d8d9-129">If you are loading a small amount of data compared to the amount of data already in the table, dropping the indexes is counterproductive.</span></span> <span data-ttu-id="4d8d9-130">重建索引需要的時間，可能會多於大量匯入作業所省下的時間。</span><span class="sxs-lookup"><span data-stu-id="4d8d9-130">The time required to rebuild the indexes might be longer than the time saved during the bulk-import operation.</span></span>  
  
-   <span data-ttu-id="4d8d9-131">尋找並移除資料檔中的隱藏字元。</span><span class="sxs-lookup"><span data-stu-id="4d8d9-131">Find and remove hidden characters in the data file.</span></span>  
  
     <span data-ttu-id="4d8d9-132">許多公用程式和文字編輯器會顯示隱藏字元，這些字元通常是在資料檔結尾。</span><span class="sxs-lookup"><span data-stu-id="4d8d9-132">Many utilities and text editors display hidden characters, which are usually at the end of the data file.</span></span> <span data-ttu-id="4d8d9-133">大量匯入作業期間，ASCII 資料檔中的隱藏字元可能會產生問題，造成「發現非預期的 NULL」錯誤。</span><span class="sxs-lookup"><span data-stu-id="4d8d9-133">During a bulk-import operation, hidden characters in an ASCII data file can cause problems that cause an error of "unexpected null found".</span></span> <span data-ttu-id="4d8d9-134">尋找並移除所有的隱藏字元，應該有助於防止這個問題的發生。</span><span class="sxs-lookup"><span data-stu-id="4d8d9-134">Finding and removing all the hidden characters should help prevent this problem.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d8d9-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4d8d9-135">See Also</span></span>  
 <span data-ttu-id="4d8d9-136">[使用 bcp 公用程式匯入及匯出大量資料 &#40;SQL Server&#41;](import-and-export-bulk-data-by-using-the-bcp-utility-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="4d8d9-136">[Import and Export Bulk Data by Using the bcp Utility &#40;SQL Server&#41;](import-and-export-bulk-data-by-using-the-bcp-utility-sql-server.md) </span></span>  
 <span data-ttu-id="4d8d9-137">[使用 BULK INSERT 或 OPENROWSET&#40;BULK...&#41; 匯入大量資料 &#40;SQL Server&#41;](import-bulk-data-by-using-bulk-insert-or-openrowset-bulk-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="4d8d9-137">[Import Bulk Data by Using BULK INSERT or OPENROWSET&#40;BULK...&#41; &#40;SQL Server&#41;](import-bulk-data-by-using-bulk-insert-or-openrowset-bulk-sql-server.md) </span></span>  
 <span data-ttu-id="4d8d9-138">[bcp 公用程式](../../tools/bcp-utility.md) </span><span class="sxs-lookup"><span data-stu-id="4d8d9-138">[bcp Utility](../../tools/bcp-utility.md) </span></span>  
 <span data-ttu-id="4d8d9-139">[BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="4d8d9-139">[BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) </span></span>  
 <span data-ttu-id="4d8d9-140">[大量匯入或大量匯出的資料格式 &#40;SQL Server&#41;](data-formats-for-bulk-import-or-bulk-export-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="4d8d9-140">[Data Formats for Bulk Import or Bulk Export &#40;SQL Server&#41;](data-formats-for-bulk-import-or-bulk-export-sql-server.md) </span></span>  
 [<span data-ttu-id="4d8d9-141">OPENROWSET &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="4d8d9-141">OPENROWSET &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/openrowset-transact-sql)  
  
  
