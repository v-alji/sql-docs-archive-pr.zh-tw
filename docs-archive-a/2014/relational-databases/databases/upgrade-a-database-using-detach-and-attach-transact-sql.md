---
title: 使用卸離與附加來升級資料庫 (Transact-SQL) | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- database attaching [SQL Server]
- upgrading databases
- database upgrades [SQL Server]
- database detaching [SQL Server]
- detaching databases [SQL Server]
- attaching databases [SQL Server]
ms.assetid: 99f66ed9-3a75-4e38-ad7d-6c27cc3529a9
author: stevestein
ms.author: sstein
ms.openlocfilehash: d430825fd862ff49b867790f366200a524df3c1c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594100"
---
# <a name="upgrade-a-database-using-detach-and-attach-transact-sql"></a><span data-ttu-id="63f95-102">使用卸離與附加來升級資料庫 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="63f95-102">Upgrade a Database Using Detach and Attach (Transact-SQL)</span></span>
  <span data-ttu-id="63f95-103">本主題描述如何使用卸離和附加作業升級 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]中的資料庫。</span><span class="sxs-lookup"><span data-stu-id="63f95-103">This topic describes how to use detach and attach operations to upgrade a database in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="63f95-104">附加至 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]之後，資料庫可立即使用並自動進行升級。</span><span class="sxs-lookup"><span data-stu-id="63f95-104">After being attached to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], the database is available immediately and is automatically upgraded.</span></span>  
  
 <span data-ttu-id="63f95-105">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="63f95-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="63f95-106">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="63f95-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="63f95-107">限制事項</span><span class="sxs-lookup"><span data-stu-id="63f95-107">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="63f95-108">建議</span><span class="sxs-lookup"><span data-stu-id="63f95-108">Recommendations</span></span>](#Recommendations)  
  
-   <span data-ttu-id="63f95-109">**升級 SQL Server 資料庫：**</span><span class="sxs-lookup"><span data-stu-id="63f95-109">**To Upgrade a SQL Server Database:**</span></span>  
  
     [<span data-ttu-id="63f95-110">使用卸離和附加作業</span><span class="sxs-lookup"><span data-stu-id="63f95-110">Using detach and attach operations</span></span>](#SSMSProcedure)  
  
-   <span data-ttu-id="63f95-111">**Follow Up:**  [After Upgrading a SQL Server Database](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="63f95-111">**Follow Up:**  [After Upgrading a SQL Server Database](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="63f95-112">開始之前</span><span class="sxs-lookup"><span data-stu-id="63f95-112">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="63f95-113">限制事項</span><span class="sxs-lookup"><span data-stu-id="63f95-113">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="63f95-114">您無法附加系統資料庫。</span><span class="sxs-lookup"><span data-stu-id="63f95-114">The system databases cannot be attached.</span></span>  
  
-   <span data-ttu-id="63f95-115">若將資料庫的 [跨資料庫擁有權鏈結]\*\*\*\* 選項設為 0，附加與卸離會停用資料庫的跨資料庫擁有權鏈結。</span><span class="sxs-lookup"><span data-stu-id="63f95-115">Attach and detach disable cross-database ownership chaining for the database by setting its **cross db ownership chaining** option to 0.</span></span> <span data-ttu-id="63f95-116">如需啟用鏈結的資訊，請參閱 [跨資料庫擁有權鏈結伺服器組態選項](../../database-engine/configure-windows/cross-db-ownership-chaining-server-configuration-option.md)。</span><span class="sxs-lookup"><span data-stu-id="63f95-116">For information about enabling chaining, see [cross db ownership chaining Server Configuration Option](../../database-engine/configure-windows/cross-db-ownership-chaining-server-configuration-option.md).</span></span>  
  
-   <span data-ttu-id="63f95-117">當附加複製的而非卸離的複寫資料庫時：</span><span class="sxs-lookup"><span data-stu-id="63f95-117">When attaching a replicated database that was copied instead of detached:</span></span>  
  
    -   <span data-ttu-id="63f95-118">如果您附加資料庫到相同伺服器執行個體的升級版本，則必須在附加作業完成後執行 **sp_vupgrade_replication** 以升級複寫。</span><span class="sxs-lookup"><span data-stu-id="63f95-118">If you attach the database to an upgraded version of the same server instance, you must execute **sp_vupgrade_replication** to upgrade replication after the attach operation finishes.</span></span> <span data-ttu-id="63f95-119">如需詳細資訊，請參閱 [sp_vupgrade_replication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-vupgrade-replication-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="63f95-119">For more information, see [sp_vupgrade_replication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-vupgrade-replication-transact-sql).</span></span>  
  
    -   <span data-ttu-id="63f95-120">如果您附加資料庫到不同的伺服器執行個體 (不論版本為何)，則必須在附加作業完成後執行 **sp_removedbreplication** 以移除複寫。</span><span class="sxs-lookup"><span data-stu-id="63f95-120">If you attach the database to a different server instance (regardless of version), you must execute **sp_removedbreplication** to remove replication after the attach operation finishes.</span></span> <span data-ttu-id="63f95-121">如需詳細資訊，請參閱 [sp_removedbreplication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="63f95-121">For more information, see [sp_removedbreplication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql).</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="63f95-122">建議</span><span class="sxs-lookup"><span data-stu-id="63f95-122">Recommendations</span></span>  
 <span data-ttu-id="63f95-123">建議您不要附加或還原來源不明或來源不受信任的資料庫。</span><span class="sxs-lookup"><span data-stu-id="63f95-123">We recommend that you do not attach or restore databases from unknown or untrusted sources.</span></span> <span data-ttu-id="63f95-124">這種資料庫可能包含惡意程式碼，因此可能執行非預期的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 程式碼，或是修改結構描述或實體資料庫結構而造成錯誤。</span><span class="sxs-lookup"><span data-stu-id="63f95-124">Such databases could contain malicious code that might execute unintended [!INCLUDE[tsql](../../includes/tsql-md.md)] code or cause errors by modifying the schema or the physical database structure.</span></span> <span data-ttu-id="63f95-125">使用來源不明或來源不受信任的資料庫之前，請先在非實際執行伺服器的資料庫上執行 [DBCC CHECKDB](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) ，同時檢查資料庫中的程式碼，例如預存程序或其他使用者定義程式碼。</span><span class="sxs-lookup"><span data-stu-id="63f95-125">Before you use a database from an unknown or untrusted source, run [DBCC CHECKDB](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) on the database on a nonproduction server and also examine the code, such as stored procedures or other user-defined code, in the database.</span></span>  
  
##  <a name="to-upgrade-a-database-by-using-detach-and-attach"></a><a name="SSMSProcedure"></a> <span data-ttu-id="63f95-126">使用卸離和附加來升級資料庫</span><span class="sxs-lookup"><span data-stu-id="63f95-126">To Upgrade a Database by Using Detach and Attach</span></span>  
  
1.  <span data-ttu-id="63f95-127">卸離資料庫。</span><span class="sxs-lookup"><span data-stu-id="63f95-127">Detach the database.</span></span> <span data-ttu-id="63f95-128">如需詳細資訊，請參閱 [卸離資料庫](detach-a-database.md)。</span><span class="sxs-lookup"><span data-stu-id="63f95-128">For more information, see [Detach a Database](detach-a-database.md).</span></span>  
  
2.  <span data-ttu-id="63f95-129">另外，也可以移動卸離的資料庫檔案與記錄檔。</span><span class="sxs-lookup"><span data-stu-id="63f95-129">Optionally, move the detached database file or files and the log file or files.</span></span>  
  
     <span data-ttu-id="63f95-130">即使您要建立新的記錄檔，仍應連同資料檔案一併移動記錄檔。</span><span class="sxs-lookup"><span data-stu-id="63f95-130">You should move the log files along with the data files, even if you intend to create new log files.</span></span> <span data-ttu-id="63f95-131">在某些情況下，重新附加資料庫需要其現有的記錄檔。</span><span class="sxs-lookup"><span data-stu-id="63f95-131">In some cases, reattaching a database requires its existing log files.</span></span> <span data-ttu-id="63f95-132">因此，一律保留所有卸離的記錄檔，直到資料庫在沒有這些檔案的情形下成功附加為止。</span><span class="sxs-lookup"><span data-stu-id="63f95-132">Therefore, always keep all the detached log files until the database has been successfully attached without them.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="63f95-133">如果您嘗試在不指定記錄檔的情形下附加資料庫，附加作業會在其原始位置中尋找記錄檔。</span><span class="sxs-lookup"><span data-stu-id="63f95-133">If you try to attach the database without specifying the log file, the attach operation will look for the log file in its original location.</span></span> <span data-ttu-id="63f95-134">如果記錄的原始副本仍在原處，則會附加該副本。</span><span class="sxs-lookup"><span data-stu-id="63f95-134">If the original copy of the log still exists in that location, that copy is attached.</span></span> <span data-ttu-id="63f95-135">若要避免使用原始記錄檔，請指定新記錄檔的路徑，或者移除記錄檔的原始副本 (在將記錄檔複製到新位置後)。</span><span class="sxs-lookup"><span data-stu-id="63f95-135">To avoid using the original log file, either specify the path of the new log file or remove the original copy of the log file (after copying it to the new location).</span></span>  
  
3.  <span data-ttu-id="63f95-136">將複製的檔案附加至 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]執行個體。</span><span class="sxs-lookup"><span data-stu-id="63f95-136">Attach the copied files to the instance of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="63f95-137">如需詳細資訊，請參閱 [Attach a Database](attach-a-database.md)。</span><span class="sxs-lookup"><span data-stu-id="63f95-137">For more information, see [Attach a Database](attach-a-database.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="63f95-138">範例</span><span class="sxs-lookup"><span data-stu-id="63f95-138">Example</span></span>  
 <span data-ttu-id="63f95-139">下列範例會從舊版 SQL Server 升級資料庫的副本。</span><span class="sxs-lookup"><span data-stu-id="63f95-139">The following example upgrades a copy of a database from an earlier version of SQL Server.</span></span> <span data-ttu-id="63f95-140">[!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式會在 [查詢編輯器] 視窗中執行，此視窗連接到附加的伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="63f95-140">The [!INCLUDE[tsql](../../includes/tsql-md.md)] statements are executed in a Query Editor window that is connected to the server instance to which is attached.</span></span>  
  
1.  <span data-ttu-id="63f95-141">執行下列 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式卸離資料庫：</span><span class="sxs-lookup"><span data-stu-id="63f95-141">Detach the database by executing the following [!INCLUDE[tsql](../../includes/tsql-md.md)] statements:</span></span>  
  
    ```  
    USE master;  
    GO  
    EXEC sp_detach_db @dbname = N'MyDatabase';  
    GO  
    ```  
  
2.  <span data-ttu-id="63f95-142">使用您選擇的方法，將資料和記錄檔複製到新的位置。</span><span class="sxs-lookup"><span data-stu-id="63f95-142">Using the method of your choice, copy the data and log files to the new location.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="63f95-143">針對實際執行的資料庫，將資料庫與交易記錄放在不同的磁碟上。</span><span class="sxs-lookup"><span data-stu-id="63f95-143">For a production database, place the database and transaction log on separate disks.</span></span>  
  
     <span data-ttu-id="63f95-144">若要經由網路將檔案複製到遠端電腦的磁碟，請使用遠端位置的通用命名慣例 (UNC) 名稱。</span><span class="sxs-lookup"><span data-stu-id="63f95-144">To copy files over the network to a disk on a remote computer, use the universal naming convention (UNC) name of the remote location.</span></span> <span data-ttu-id="63f95-145">UNC 名稱的格式為 **\\\\** _Servername_ **\\** _共用_ **\\** _路徑_ **\\** _Filename_。</span><span class="sxs-lookup"><span data-stu-id="63f95-145">A UNC name takes the form **\\\\**_Servername_**\\**_Sharename_**\\**_Path_**\\**_Filename_.</span></span> <span data-ttu-id="63f95-146">如同將檔案寫入本機硬碟一樣，您必須將在遠端磁碟讀取或寫入檔案所需的適當權限，授與 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]執行個體所用的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="63f95-146">As with writing files to the local hard disk, the appropriate permissions that are required to read or write to a file on the remote disk must be granted to the user account used by the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
3.  <span data-ttu-id="63f95-147">若要附加已移動的資料庫和記錄檔 (選擇性)，請執行下列 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式：</span><span class="sxs-lookup"><span data-stu-id="63f95-147">Attach the moved database and, optionally, its log by executing the following [!INCLUDE[tsql](../../includes/tsql-md.md)] statement:</span></span>  
  
    ```  
    USE master;  
    GO  
    CREATE DATABASE MyDatabase   
        ON (FILENAME = 'C:\MySQLServer\MyDatabase.mdf'),  
        (FILENAME = 'C:\MySQLServer\Database.ldf')  
        FOR ATTACH;  
    GO  
    ```  
  
     <span data-ttu-id="63f95-148">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中，新附加的資料庫無法立即在 [物件總管] 中可見。</span><span class="sxs-lookup"><span data-stu-id="63f95-148">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], a newly attached database is not immediately visible in Object Explorer.</span></span> <span data-ttu-id="63f95-149">若要檢視資料庫，請在 [物件總管] 中按一下 **[檢視]** ，然後按一下 **[重新整理]**。</span><span class="sxs-lookup"><span data-stu-id="63f95-149">To view the database, in Object Explorer, click **View,** and then **Refresh**.</span></span> <span data-ttu-id="63f95-150">在 [物件總管] 中展開 **[資料庫]** 節點時，剛才附加的資料庫就會出現在資料庫清單中。</span><span class="sxs-lookup"><span data-stu-id="63f95-150">When the **Databases** node is expanded in Object Explorer, the newly attached database now appears in the list of databases.</span></span>  
  
##  <a name="follow-up-after-upgrading-a-sql-server-database"></a><a name="FollowUp"></a> <span data-ttu-id="63f95-151">後續操作：升級 SQL Server 資料庫之後</span><span class="sxs-lookup"><span data-stu-id="63f95-151">Follow Up: After Upgrading a SQL Server Database</span></span>  
 <span data-ttu-id="63f95-152">如果資料庫具有全文檢索索引，升級程序就會根據 **upgrade_option** 伺服器屬性的設定，匯入、重設或重建這些索引。</span><span class="sxs-lookup"><span data-stu-id="63f95-152">If the database has full-text indexes, the upgrade process either imports, resets, or rebuilds them, depending on the setting of the **upgrade_option** server property.</span></span> <span data-ttu-id="63f95-153">如果升級選項設定為匯入 (**upgrade_option** = 2) 或重建 (**upgrade_option** = 0)，則全文檢索索引在升級期間將無法使用。</span><span class="sxs-lookup"><span data-stu-id="63f95-153">If the upgrade option is set to import (**upgrade_option** = 2) or rebuild (**upgrade_option** = 0), the full-text indexes will be unavailable during the upgrade.</span></span> <span data-ttu-id="63f95-154">根據進行索引的資料數量而定，匯入可能需要數個小時，而重建可能需要十倍以上的時間。</span><span class="sxs-lookup"><span data-stu-id="63f95-154">Depending the amount of data being indexed, importing can take several hours, and rebuilding can take up to ten times longer.</span></span> <span data-ttu-id="63f95-155">此外，請注意，當升級選項設定為 [匯入] 時，如果全文檢索目錄無法使用，系統就會重建相關聯的全文檢索索引。</span><span class="sxs-lookup"><span data-stu-id="63f95-155">Note also that when the upgrade option is set to import, the associated full-text indexes are rebuilt if a full-text catalog is not available.</span></span> <span data-ttu-id="63f95-156">若要變更 **upgrade_option** 伺服器屬性的設定，請使用 [sp_fulltext_service](/sql/relational-databases/system-stored-procedures/sp-fulltext-service-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="63f95-156">To change the setting of the **upgrade_option** server property, use [sp_fulltext_service](/sql/relational-databases/system-stored-procedures/sp-fulltext-service-transact-sql).</span></span>  
  
### <a name="database-compatibility-level-after-upgrade"></a><span data-ttu-id="63f95-157">升級後的資料庫相容性層級</span><span class="sxs-lookup"><span data-stu-id="63f95-157">Database Compatibility Level After Upgrade</span></span>  
 <span data-ttu-id="63f95-158">如果使用者資料庫的相容性層級在升級前為 100 或更高層級，則在升級後仍會保持相同。</span><span class="sxs-lookup"><span data-stu-id="63f95-158">If the compatibility level of a user database is 100 or higher before upgrade, it remains the same after upgrade.</span></span> <span data-ttu-id="63f95-159">如果升級前的相容性層級為 90，則在升級後的資料庫中，相容性層級會設定為 100 (這是 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]所支援的最低相容性層級)。</span><span class="sxs-lookup"><span data-stu-id="63f95-159">If the compatibility level is 90 before upgrade in the upgraded database, the compatibility level is set to 100, which is the lowest supported compatibility level in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="63f95-160">如需詳細資訊，請參閱 [ALTER DATABASE 相容性層級 &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-compatibility-level)。</span><span class="sxs-lookup"><span data-stu-id="63f95-160">For more information, see [ALTER DATABASE Compatibility Level &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-compatibility-level).</span></span>  
  
### <a name="managing-metadata-on-the-upgraded-server-instance"></a><span data-ttu-id="63f95-161">在升級的伺服器執行個體上管理中繼資料</span><span class="sxs-lookup"><span data-stu-id="63f95-161">Managing Metadata on the Upgraded Server Instance</span></span>  
 <span data-ttu-id="63f95-162">將資料庫附加至另一個伺服器執行個體時，為了提供一致的經驗給使用者和應用程式，您可能需要在其他伺服器執行個體上為資料庫重新建立部分或所有的中繼資料，例如登入、作業和權限。</span><span class="sxs-lookup"><span data-stu-id="63f95-162">When you attach a database onto another server instance, to provide a consistent experience to users and applications, you might have to re-create some or all of the metadata for the database, such as logins, jobs, and permissions, on the other server instance.</span></span> <span data-ttu-id="63f95-163">如需詳細資訊，請參閱 [在另一個伺服器執行個體上提供可用的資料庫時，管理中繼資料 &#40;SQL Server&#41;](manage-metadata-when-making-a-database-available-on-another-server.md)。</span><span class="sxs-lookup"><span data-stu-id="63f95-163">For more information, see [Manage Metadata When Making a Database Available on Another Server Instance &#40;SQL Server&#41;](manage-metadata-when-making-a-database-available-on-another-server.md).</span></span>  
  
### <a name="service-master-key-and-database-master-key-encryption-changes-from-3des-to-aes"></a><span data-ttu-id="63f95-164">服務主要金鑰和資料庫主要金鑰加密從 3DES 到 AES 的變化</span><span class="sxs-lookup"><span data-stu-id="63f95-164">Service Master Key and Database Master Key Encryption changes from 3DES to AES</span></span>  
 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] <span data-ttu-id="63f95-165">和更新版本會使用 AES 加密演算法來保護服務主要金鑰 (SMK) 及資料庫主要金鑰 (DMK)。</span><span class="sxs-lookup"><span data-stu-id="63f95-165">and higher versions uses the AES encryption algorithm to protect the service master key (SMK) and the database master key (DMK).</span></span> <span data-ttu-id="63f95-166">與舊版中使用的 3DES 相比，AES 是一種較新的加密演算法。</span><span class="sxs-lookup"><span data-stu-id="63f95-166">AES is a newer encryption algorithm than 3DES used in earlier versions.</span></span> <span data-ttu-id="63f95-167">當資料庫第一次連接或還原到新的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]執行個體時，資料庫主要金鑰複本 (由服務主要金鑰加密) 尚未儲存在伺服器中。</span><span class="sxs-lookup"><span data-stu-id="63f95-167">When a database is first attached or restored to a new instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], a copy of the database master key (encrypted by the service master key) is not yet stored in the server.</span></span> <span data-ttu-id="63f95-168">您必須利用 `OPEN MASTER KEY` 陳述式來解密資料庫主要金鑰 (DMK)。</span><span class="sxs-lookup"><span data-stu-id="63f95-168">You must use the `OPEN MASTER KEY` statement to decrypt the database master key (DMK).</span></span> <span data-ttu-id="63f95-169">DMK 解密之後，您便可以選擇利用 `ALTER MASTER KEY REGENERATE` 陳述式來提供服務主要金鑰 (SMK) 所加密的 DMK 複本給伺服器，以在未來啟用自動解密。</span><span class="sxs-lookup"><span data-stu-id="63f95-169">Once the DMK has been decrypted, you have the option of enabling automatic decryption in the future by using the `ALTER MASTER KEY REGENERATE` statement to provision the server with a copy of the DMK, encrypted with the service master key (SMK).</span></span> <span data-ttu-id="63f95-170">當資料庫從舊版升級時，應該會重新產生 DMK 以使用較新的 AES 演算法。</span><span class="sxs-lookup"><span data-stu-id="63f95-170">When a database has been upgraded from an earlier version, the DMK should be regenerated to use the newer AES algorithm.</span></span> <span data-ttu-id="63f95-171">如需重新產生 DMK 的詳細資訊，請參閱 [ALTER MASTER KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-master-key-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="63f95-171">For more information about regenerating the DMK, see [ALTER MASTER KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-master-key-transact-sql).</span></span> <span data-ttu-id="63f95-172">重新產生 DMK 金鑰以升級至 AES 所需的時間是取決於 DMK 所保護的物件數目而定。</span><span class="sxs-lookup"><span data-stu-id="63f95-172">The time required to regenerate the DMK key to upgrade to AES depends upon the number of objects protected by the DMK.</span></span> <span data-ttu-id="63f95-173">重新產生 DMK 金鑰以升級至 AES 只需執行一次，且不會影響金鑰循環策略中後續的重新產生。</span><span class="sxs-lookup"><span data-stu-id="63f95-173">Regenerating the DMK key to upgrade to AES is only necessary once, and has no impact on future regenerations as part of a key rotation strategy.</span></span>  
  
  
