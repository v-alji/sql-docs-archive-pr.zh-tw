---
title: 在簡單復原模式下還原資料庫備份 (Transact-SQL) | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- full backups [SQL Server]
- database restores [SQL Server], full backups
- backing up databases [SQL Server], full backups
- database backups [SQL Server], full backups
- restoring databases [SQL Server], full backups
ms.assetid: a928fa36-e285-476f-9a7b-6840a8bb7283
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: e264dd380c3dff40dacc4eb576d34af5195dec01
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87698329"
---
# <a name="restore-a-database-backup-under-the-simple-recovery-model-transact-sql"></a><span data-ttu-id="3f3ad-102">在簡單復原模式下還原資料庫備份 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="3f3ad-102">Restore a Database Backup Under the Simple Recovery Model (Transact-SQL)</span></span>
  <span data-ttu-id="3f3ad-103">本主題說明如何還原完整資料庫備份。</span><span class="sxs-lookup"><span data-stu-id="3f3ad-103">This topic explains how to restore a full database backup.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="3f3ad-104">負責還原完整資料庫備份的系統管理員，必須是目前唯一正在使用即將還原之資料庫的人員。</span><span class="sxs-lookup"><span data-stu-id="3f3ad-104">The system administrator restoring the full database backup must be the only person currently using the database to be restored.</span></span>  
  
## <a name="prerequisites-and-recommendations"></a><span data-ttu-id="3f3ad-105">先決條件和建議</span><span class="sxs-lookup"><span data-stu-id="3f3ad-105">Prerequisites and Recommendations</span></span>  
  
-   <span data-ttu-id="3f3ad-106">若要還原加密的資料庫，您必須能夠存取之前用來加密資料庫的憑證或非對稱金鑰。</span><span class="sxs-lookup"><span data-stu-id="3f3ad-106">To restore a database that is encrypted, you must have access to the certificate or asymmetric key that was used to encrypt the database.</span></span> <span data-ttu-id="3f3ad-107">如果沒有該憑證或非對稱金鑰，就無法還原資料庫。</span><span class="sxs-lookup"><span data-stu-id="3f3ad-107">Without the certificate or asymmetric key, the database cannot be restored.</span></span> <span data-ttu-id="3f3ad-108">因此，只要需要備份，就必須保留用來加密資料庫加密金鑰的憑證。</span><span class="sxs-lookup"><span data-stu-id="3f3ad-108">As a result, the certificate that is used to encrypt the database encryption key must be retained as long as the backup is needed.</span></span> <span data-ttu-id="3f3ad-109">如需詳細資訊，請參閱 [SQL Server Certificates and Asymmetric Keys](../security/sql-server-certificates-and-asymmetric-keys.md)。</span><span class="sxs-lookup"><span data-stu-id="3f3ad-109">For more information, see [SQL Server Certificates and Asymmetric Keys](../security/sql-server-certificates-and-asymmetric-keys.md).</span></span>  
  
-   <span data-ttu-id="3f3ad-110">基於安全性的理由，建議您不要附加或還原來源不明或來源不受信任的資料庫。</span><span class="sxs-lookup"><span data-stu-id="3f3ad-110">For security purposes, we recommend that you do not attach or restore databases from unknown or untrusted sources.</span></span> <span data-ttu-id="3f3ad-111">這種資料庫可能包含惡意程式碼，因此可能執行非預期的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 程式碼，或是修改結構描述或實體資料庫結構而造成錯誤。</span><span class="sxs-lookup"><span data-stu-id="3f3ad-111">Such databases could contain malicious code that might execute unintended [!INCLUDE[tsql](../../includes/tsql-md.md)] code or cause errors by modifying the schema or the physical database structure.</span></span> <span data-ttu-id="3f3ad-112">使用來源不明或來源不受信任的資料庫之前，請先在非實際執行伺服器的資料庫上執行 [DBCC CHECKDB](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) ，同時檢查資料庫中的程式碼，例如預存程序或其他使用者定義程式碼。</span><span class="sxs-lookup"><span data-stu-id="3f3ad-112">Before you use a database from an unknown or untrusted source, run [DBCC CHECKDB](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) on the database on a nonproduction server and also examine the code, such as stored procedures or other user-defined code, in the database.</span></span>  
  
## <a name="database-compatibility-level-after-upgrade"></a><span data-ttu-id="3f3ad-113">升級後的資料庫相容性層級</span><span class="sxs-lookup"><span data-stu-id="3f3ad-113">Database Compatibility Level After Upgrade</span></span>  
 <span data-ttu-id="3f3ad-114">**tempdb**、 **模型**、 **msdb** 和 **資源** 資料庫的相容性層級在升級之後會設定為 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 的相容性層級。</span><span class="sxs-lookup"><span data-stu-id="3f3ad-114">The compatibility levels of the **tempdb**, **model**, **msdb** and **Resource** databases are set to the compatibility level of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] after upgrade.</span></span> <span data-ttu-id="3f3ad-115">**主要** 系統資料庫會保留升級前的相容性層級，除非層級小於 100。</span><span class="sxs-lookup"><span data-stu-id="3f3ad-115">The **master** system database retains the compatibility level it had before upgrade, unless that level was less than 100.</span></span> <span data-ttu-id="3f3ad-116">如果升級前 **主要** 的相容性層級小於 100，升級後會設定為 100。</span><span class="sxs-lookup"><span data-stu-id="3f3ad-116">If the compatibility level of **master** was less than 100 before upgrade, it is set to 100 after upgrade.</span></span>  
  
 <span data-ttu-id="3f3ad-117">如果使用者資料庫的相容性層級在升級前為 100 或更高層級，則在升級後仍會保持相同。</span><span class="sxs-lookup"><span data-stu-id="3f3ad-117">If the compatibility level of a user database was 100 or higher before upgrade, it remains the same after upgrade.</span></span> <span data-ttu-id="3f3ad-118">如果升級前的相容性層級為 90，則在升級後的資料庫中，相容性層級會設定為 100 (這是 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]所支援的最低相容性層級)。</span><span class="sxs-lookup"><span data-stu-id="3f3ad-118">If the compatibility level was 90 before upgrade, in the upgraded database, the compatibility level is set to 100, which is the lowest supported compatibility level in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3f3ad-119">新的使用者資料庫會繼承 **模型** 資料庫的相容性層級。</span><span class="sxs-lookup"><span data-stu-id="3f3ad-119">New user databases will inherit the compatibility level of the **model** database.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="3f3ad-120">程序</span><span class="sxs-lookup"><span data-stu-id="3f3ad-120">Procedures</span></span>  
  
#### <a name="to-restore-a-full-database-backup"></a><span data-ttu-id="3f3ad-121">還原完整資料庫備份</span><span class="sxs-lookup"><span data-stu-id="3f3ad-121">To restore a full database backup</span></span>  
  
1.  <span data-ttu-id="3f3ad-122">執行 RESTORE DATABASE 陳述式以還原完整資料庫備份，請指定：</span><span class="sxs-lookup"><span data-stu-id="3f3ad-122">Execute the RESTORE DATABASE statement to restore the full database backup, specifying:</span></span>  
  
    -   <span data-ttu-id="3f3ad-123">所要還原的資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="3f3ad-123">The name of the database to restore.</span></span>  
  
    -   <span data-ttu-id="3f3ad-124">將要還原完整資料庫備份的備份裝置。</span><span class="sxs-lookup"><span data-stu-id="3f3ad-124">The backup device from where the full database backup is restored.</span></span>  
  
    -   <span data-ttu-id="3f3ad-125">如果完整資料庫備份還原以後需要套用交易記錄或差異資料庫備份，則請指定 NORECOVERY 子句。</span><span class="sxs-lookup"><span data-stu-id="3f3ad-125">The NORECOVERY clause if you have a transaction log or differential database backup to apply after restoring the full database backup.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="3f3ad-126">若要還原加密的資料庫，您必須能夠存取之前用來加密資料庫的憑證或非對稱金鑰。</span><span class="sxs-lookup"><span data-stu-id="3f3ad-126">To restore a database that is encrypted, you must have access to the certificate or asymmetric key that was used to encrypt the database.</span></span> <span data-ttu-id="3f3ad-127">如果沒有該憑證或非對稱金鑰，就無法還原資料庫。</span><span class="sxs-lookup"><span data-stu-id="3f3ad-127">Without the certificate or asymmetric key, the database cannot be restored.</span></span> <span data-ttu-id="3f3ad-128">因此，只要需要備份，就必須保留用來加密資料庫加密金鑰的憑證。</span><span class="sxs-lookup"><span data-stu-id="3f3ad-128">As a result, the certificate that is used to encrypt the database encryption key must be retained as long as the backup is needed.</span></span> <span data-ttu-id="3f3ad-129">如需詳細資訊，請參閱 [SQL Server Certificates and Asymmetric Keys](../security/sql-server-certificates-and-asymmetric-keys.md)。</span><span class="sxs-lookup"><span data-stu-id="3f3ad-129">For more information, see [SQL Server Certificates and Asymmetric Keys](../security/sql-server-certificates-and-asymmetric-keys.md).</span></span>  
  
2.  <span data-ttu-id="3f3ad-130">(選擇性) 指定：</span><span class="sxs-lookup"><span data-stu-id="3f3ad-130">Optionally, specify:</span></span>  
  
    -   <span data-ttu-id="3f3ad-131">識別備份裝置上欲還原之備份組的 FILE 子句。</span><span class="sxs-lookup"><span data-stu-id="3f3ad-131">The FILE clause to identify the backup set on the backup device to restore.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3f3ad-132">如果您將舊版資料庫還原至 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]，資料庫會自動升級。</span><span class="sxs-lookup"><span data-stu-id="3f3ad-132">If you restore an earlier version database to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], the database is automatically upgraded.</span></span> <span data-ttu-id="3f3ad-133">通常，資料庫立即變為可用。</span><span class="sxs-lookup"><span data-stu-id="3f3ad-133">Typically, the database becomes available immediately.</span></span> <span data-ttu-id="3f3ad-134">不過，如果 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 資料庫具有全文檢索索引，升級程序就會根據  **upgrade_option** 伺服器屬性的設定，匯入、重設或重建這些索引。</span><span class="sxs-lookup"><span data-stu-id="3f3ad-134">However, if a [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] database has full-text indexes, the upgrade process either imports, resets, or rebuilds them, depending on the setting of the  **upgrade_option** server property.</span></span> <span data-ttu-id="3f3ad-135">如果升級選項設定為匯入 (**upgrade_option** = 2) 或重建 (**upgrade_option** = 0)，則全文檢索索引在升級期間將無法使用。</span><span class="sxs-lookup"><span data-stu-id="3f3ad-135">If the upgrade option is set to import (**upgrade_option** = 2) or rebuild (**upgrade_option** = 0), the full-text indexes will be unavailable during the upgrade.</span></span> <span data-ttu-id="3f3ad-136">根據進行索引的資料數量而定，匯入可能需要數個小時，而重建可能需要十倍以上的時間。</span><span class="sxs-lookup"><span data-stu-id="3f3ad-136">Depending the amount of data being indexed, importing can take several hours, and rebuilding can take up to ten times longer.</span></span> <span data-ttu-id="3f3ad-137">此外，請注意，當升級選項設定為 [匯入] 時，如果全文檢索目錄無法使用，系統就會重建相關聯的全文檢索索引。</span><span class="sxs-lookup"><span data-stu-id="3f3ad-137">Note also that when the upgrade option is set to import, the associated full-text indexes are rebuilt if a full-text catalog is not available.</span></span> <span data-ttu-id="3f3ad-138">若要變更 **upgrade_option** 伺服器屬性的設定，請使用 [sp_fulltext_service](/sql/relational-databases/system-stored-procedures/sp-fulltext-service-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="3f3ad-138">To change the setting of the **upgrade_option** server property, use [sp_fulltext_service](/sql/relational-databases/system-stored-procedures/sp-fulltext-service-transact-sql).</span></span>  
  
## <a name="example"></a><span data-ttu-id="3f3ad-139">範例</span><span class="sxs-lookup"><span data-stu-id="3f3ad-139">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="3f3ad-140">描述</span><span class="sxs-lookup"><span data-stu-id="3f3ad-140">Description</span></span>  
 <span data-ttu-id="3f3ad-141">此範例會從磁帶還原 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 完整資料庫備份。</span><span class="sxs-lookup"><span data-stu-id="3f3ad-141">This example restores the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] full database backup from tape.</span></span>  
  
### <a name="example"></a><span data-ttu-id="3f3ad-142">範例</span><span class="sxs-lookup"><span data-stu-id="3f3ad-142">Example</span></span>  
  
```  
USE master;  
GO  
RESTORE DATABASE AdventureWorks2012  
   FROM TAPE = '\\.\Tape0';  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="3f3ad-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3f3ad-143">See Also</span></span>  
 <span data-ttu-id="3f3ad-144">[完整資料庫還原 &#40;完整復原模式&#41;](complete-database-restores-full-recovery-model.md) </span><span class="sxs-lookup"><span data-stu-id="3f3ad-144">[Complete Database Restores &#40;Full Recovery Model&#41;](complete-database-restores-full-recovery-model.md) </span></span>  
 <span data-ttu-id="3f3ad-145">[完整資料庫還原 &#40;簡單復原模式&#41;](complete-database-restores-simple-recovery-model.md) </span><span class="sxs-lookup"><span data-stu-id="3f3ad-145">[Complete Database Restores &#40;Simple Recovery Model&#41;](complete-database-restores-simple-recovery-model.md) </span></span>  
 <span data-ttu-id="3f3ad-146">[完整資料庫備份 &#40;SQL Server&#41;](full-database-backups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="3f3ad-146">[Full Database Backups &#40;SQL Server&#41;](full-database-backups-sql-server.md) </span></span>  
 <span data-ttu-id="3f3ad-147">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="3f3ad-147">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span></span>  
 <span data-ttu-id="3f3ad-148">[備份記錄與標頭資訊 &#40;SQL Server&#41;](backup-history-and-header-information-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="3f3ad-148">[Backup History and Header Information &#40;SQL Server&#41;](backup-history-and-header-information-sql-server.md) </span></span>  
 [<span data-ttu-id="3f3ad-149">重建系統資料庫</span><span class="sxs-lookup"><span data-stu-id="3f3ad-149">Rebuild System Databases</span></span>](../databases/system-databases.md)  
  
  
