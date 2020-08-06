---
title: 備份加密 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
ms.assetid: 334b95a8-6061-4fe0-9e34-b32c9f1706ce
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 6a78ae4969982fbfe5295ee4219855f48ac60793
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710698"
---
# <a name="backup-encryption"></a><span data-ttu-id="a4efd-102">備份加密</span><span class="sxs-lookup"><span data-stu-id="a4efd-102">Backup Encryption</span></span>
  <span data-ttu-id="a4efd-103">本主題提供 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 備份的加密選項概觀。</span><span class="sxs-lookup"><span data-stu-id="a4efd-103">This topic provides an overview of the encryption options for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] backups.</span></span> <span data-ttu-id="a4efd-104">內容包括在備份期間加密的用法、益處和建議做法等詳細資料。</span><span class="sxs-lookup"><span data-stu-id="a4efd-104">It includes details of the usage, benefits, and recommended practices for encrypting during backup.</span></span>  
  
  
##  <a name="overview"></a><a name="Overview"></a> <span data-ttu-id="a4efd-105">概觀</span><span class="sxs-lookup"><span data-stu-id="a4efd-105">Overview</span></span>  
 <span data-ttu-id="a4efd-106">從 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]開始，SQL Server 即擁有在建立備份時加密資料的能力。</span><span class="sxs-lookup"><span data-stu-id="a4efd-106">Starting in [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)], SQL Server has the ability to encrypt the data while creating a backup.</span></span> <span data-ttu-id="a4efd-107">在建立備份時透過指定加密演算法及加密程式 (憑證或非對稱金鑰)，即可建立加密的備份檔案。</span><span class="sxs-lookup"><span data-stu-id="a4efd-107">By specifying the encryption algorithm and the encryptor (a Certificate or Asymmetric Key) when creating a backup, you can create an encrypted backup file.</span></span> <span data-ttu-id="a4efd-108">所有儲存目的地：支援內部部署及 Window Azure 儲存體。</span><span class="sxs-lookup"><span data-stu-id="a4efd-108">All storage destinations: on-premises and Window Azure storage are supported.</span></span> <span data-ttu-id="a4efd-109">此外， [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] 作業可設定加密選項，此為 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]引進的新功能。</span><span class="sxs-lookup"><span data-stu-id="a4efd-109">In addition, encryption options can be configured for [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] operations, a new feature introduced in [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)].</span></span>  
  
 <span data-ttu-id="a4efd-110">若要在備份期間加密，您必須指定加密演算法以及確保加密金鑰的加密程式。</span><span class="sxs-lookup"><span data-stu-id="a4efd-110">To encrypt during backup, you must specify an encryption algorithm, and an encryptor to secure the encryption key.</span></span> <span data-ttu-id="a4efd-111">以下為支援的加密選項：</span><span class="sxs-lookup"><span data-stu-id="a4efd-111">The following are the supported encryption options:</span></span>  
  
-   <span data-ttu-id="a4efd-112">**加密演算法：** 支援的加密演算法包括：AES 128、AES 192、AES 256 和 Triple DES</span><span class="sxs-lookup"><span data-stu-id="a4efd-112">**Encryption Algorithm:** The supported encryption algorithms are: AES 128, AES 192, AES 256, and Triple DES</span></span>  
  
-   <span data-ttu-id="a4efd-113">**加密程式：** 憑證或非對稱金鑰</span><span class="sxs-lookup"><span data-stu-id="a4efd-113">**Encryptor:** A certificate or asymmetric Key</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="a4efd-114">備份憑證或非對稱金鑰是非常重要的，而且最好與其用以加密的備份檔案存放於不同位置。</span><span class="sxs-lookup"><span data-stu-id="a4efd-114">It is very important to back up the certificate or asymmetric key, and preferably to a different location than the backup file it was used to encrypt.</span></span> <span data-ttu-id="a4efd-115">若沒有憑證或非對稱金鑰，您將無法還原備份，而此備份檔案將無法使用。</span><span class="sxs-lookup"><span data-stu-id="a4efd-115">Without the certificate or asymmetric key, you cannot restore the backup, rendering the backup file unusable.</span></span>  
  
 <span data-ttu-id="a4efd-116">**從加密備份還原：** 在還原期間，SQL Server 還原不要求指定任何加密參數。</span><span class="sxs-lookup"><span data-stu-id="a4efd-116">**Restoring the encrypted backup:** SQL Server restore does not require any encryption parameters to be specified during restores.</span></span> <span data-ttu-id="a4efd-117">但它要求用以加密備份檔案的憑證或非對稱金鑰可用於您要進行還原的執行個體上。</span><span class="sxs-lookup"><span data-stu-id="a4efd-117">It does require that the certificate or the asymmetric key used to encrypt the backup file be available on the instance that you are restoring to.</span></span> <span data-ttu-id="a4efd-118">執行還原的使用者帳戶必須擁有憑證或金鑰的 `VIEW DEFINITION` 權限。</span><span class="sxs-lookup"><span data-stu-id="a4efd-118">The user account performing the restore must have `VIEW DEFINITION` permissions on the certificate or key.</span></span> <span data-ttu-id="a4efd-119">若您要將加密的備份還原到不同的執行個體，您必須確定憑證可用於該執行個體上。</span><span class="sxs-lookup"><span data-stu-id="a4efd-119">If you are restoring the encrypted backup to a different instance, you must make sure that the certificate is available on that instance.</span></span>  
  
 <span data-ttu-id="a4efd-120">若您要從 TDE 加密資料庫中還原備份，TDE 憑證需可用於您要進行還原的執行個體上。</span><span class="sxs-lookup"><span data-stu-id="a4efd-120">If you are restoring a backup from a TDE encrypted database, the TDE certificate should be available on the instance you are restoring to.</span></span>  
  
##  <a name="benefits"></a><a name="Benefits"></a> <span data-ttu-id="a4efd-121">優點</span><span class="sxs-lookup"><span data-stu-id="a4efd-121">Benefits</span></span>  
  
1.  <span data-ttu-id="a4efd-122">加密資料庫備份能幫助您確保資料的安全：SQL Server 提供建立備份時加密備份資料的選項。</span><span class="sxs-lookup"><span data-stu-id="a4efd-122">Encrypting the database backups helps secure the data: SQL Server provides the option to encrypt the backup data while creating a backup.</span></span>  
  
2.  <span data-ttu-id="a4efd-123">加密亦可用於使用 TDE 加密的資料庫。</span><span class="sxs-lookup"><span data-stu-id="a4efd-123">Encryption can also be used for databases that are encrypted using TDE.</span></span>  
  
3.  <span data-ttu-id="a4efd-124">[!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]建立的備份支援加密，可提供離站備份額外的安全性。</span><span class="sxs-lookup"><span data-stu-id="a4efd-124">Encryption is supported for backups done by [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)], which provides additional security for off-site backups.</span></span>  
  
4.  <span data-ttu-id="a4efd-125">此功能支援最高 AES 256 位元的多個加密演算法。</span><span class="sxs-lookup"><span data-stu-id="a4efd-125">This feature supports multiple encryption algorithms up to AES 256 bit.</span></span> <span data-ttu-id="a4efd-126">如此可提供您選項，選取符合您需求的演算法。</span><span class="sxs-lookup"><span data-stu-id="a4efd-126">This gives you the option to select an algorithm that aligns with your requirements.</span></span>  
  
5.  <span data-ttu-id="a4efd-127">您可以將加密金鑰與延伸金鑰管理 (EKM) 提供者整合。</span><span class="sxs-lookup"><span data-stu-id="a4efd-127">You can integrate encryption keys with Extended Key Management (EKM) providers.</span></span>  
  
  
##  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="a4efd-128">必要條件</span><span class="sxs-lookup"><span data-stu-id="a4efd-128">Prerequisites</span></span>  
 <span data-ttu-id="a4efd-129">下列為加密備份的必要條件：</span><span class="sxs-lookup"><span data-stu-id="a4efd-129">The following are prerequisites for encrypting a backup:</span></span>  
  
1.  <span data-ttu-id="a4efd-130">**建立 master 資料庫的資料庫主要金鑰：** 資料庫主要金鑰是一個用來保護資料庫中憑證之私密金鑰和非對稱金鑰的對稱金鑰。</span><span class="sxs-lookup"><span data-stu-id="a4efd-130">**Create a Database Master Key for the master database:** The database master key is a symmetric key that is used to protect the private keys of certificates and asymmetric keys that are present in the database.</span></span> <span data-ttu-id="a4efd-131">如需詳細資訊，請參閱 [SQL Server 和資料庫加密金鑰 &#40;Database Engine&#41;](../security/encryption/sql-server-and-database-encryption-keys-database-engine.md)。</span><span class="sxs-lookup"><span data-stu-id="a4efd-131">For more information, see [SQL Server and Database Encryption Keys &#40;Database Engine&#41;](../security/encryption/sql-server-and-database-encryption-keys-database-engine.md).</span></span>  
  
2.  <span data-ttu-id="a4efd-132">建立用來備份加密的憑證或非對稱金鑰。</span><span class="sxs-lookup"><span data-stu-id="a4efd-132">Create a certificate or asymmetric Key to use for backup encryption.</span></span> <span data-ttu-id="a4efd-133">如需建立憑證的詳細資訊，請參閱 [CREATE CERTIFICATE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-certificate-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="a4efd-133">For more information on creating a certificate, see [CREATE CERTIFICATE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-certificate-transact-sql).</span></span> <span data-ttu-id="a4efd-134">如需建立非對稱金鑰的詳細資訊，請參閱 [CREATE ASYMMETRIC KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-asymmetric-key-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="a4efd-134">For more information on creating an asymmetric key, see [CREATE ASYMMETRIC KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-asymmetric-key-transact-sql).</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="a4efd-135">僅支援位於延伸金鑰管理 (EKM) 的非對稱金鑰。</span><span class="sxs-lookup"><span data-stu-id="a4efd-135">Only asymmetric keys residing in an Extended Key Management (EKM) are supported.</span></span>  
  
##  <a name="restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="a4efd-136">限制</span><span class="sxs-lookup"><span data-stu-id="a4efd-136">Restrictions</span></span>  
 <span data-ttu-id="a4efd-137">下列為適用於加密選項的限制：</span><span class="sxs-lookup"><span data-stu-id="a4efd-137">The following are restrictions that apply to the encryption options:</span></span>  
  
-   <span data-ttu-id="a4efd-138">若您使用非對稱金鑰加密備份資料，則僅支援位於 EKM 提供者的非對稱金鑰。</span><span class="sxs-lookup"><span data-stu-id="a4efd-138">If you are using asymmetric key to encrypt the backup data, only asymmetric keys residing in the EKM provider are supported.</span></span>  
  
-   <span data-ttu-id="a4efd-139">SQL Server Express 和 SQL Server Web 不支援備份期間加密。</span><span class="sxs-lookup"><span data-stu-id="a4efd-139">SQL Server Express and SQL Server Web do not support encryption during backup.</span></span> <span data-ttu-id="a4efd-140">但是可支援從加密的備份還原到 SQL Server Express 或 SQL Server Web 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="a4efd-140">However restoring from an encrypted backup to an instance of SQL Server Express or SQL Server Web is supported.</span></span>  
  
-   <span data-ttu-id="a4efd-141">舊版 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 無法讀取加密的備份。</span><span class="sxs-lookup"><span data-stu-id="a4efd-141">Previous versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] cannot read encrypted backups.</span></span>  
  
-   <span data-ttu-id="a4efd-142">加密備份不支援附加至現有備份組的選項。</span><span class="sxs-lookup"><span data-stu-id="a4efd-142">Appending to an existing backup set option is not supported for encrypted backups.</span></span>  
  
  
##  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="a4efd-143">權限</span><span class="sxs-lookup"><span data-stu-id="a4efd-143">Permissions</span></span>  
 <span data-ttu-id="a4efd-144">**加密備份或從加密的備份還原：**</span><span class="sxs-lookup"><span data-stu-id="a4efd-144">**To encrypt a backup or to restore from an encrypted backup:**</span></span>  
  
 <span data-ttu-id="a4efd-145">用來加密資料庫備份之憑證或非對稱金鑰上的 `VIEW DEFINITION` 權限。</span><span class="sxs-lookup"><span data-stu-id="a4efd-145">`VIEW DEFINITION` permission on the certificate or asymmetric key that is used to encrypt the database backup.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a4efd-146">備份或還原 TDE 所保護的資料庫並不需要存取 TDE 憑證。</span><span class="sxs-lookup"><span data-stu-id="a4efd-146">Access to the TDE certificate is not required to back up or restore a TDE protected database.</span></span>  
  
##  <a name="backup-encryption-methods"></a><a name="Methods"></a> <span data-ttu-id="a4efd-147">備份加密方式</span><span class="sxs-lookup"><span data-stu-id="a4efd-147">Backup Encryption Methods</span></span>  
 <span data-ttu-id="a4efd-148">下列章節將簡單介紹在備份期間加密資料的步驟。</span><span class="sxs-lookup"><span data-stu-id="a4efd-148">The sections below provide a brief introduction to the steps to encrypting the data during backup.</span></span> <span data-ttu-id="a4efd-149">如需有關使用 Transact-SQL 加密備份之不同步驟的完整逐步解說，請參閱 [建立加密的備份](create-an-encrypted-backup.md)。</span><span class="sxs-lookup"><span data-stu-id="a4efd-149">For a complete walkthrough of the different steps of encrypting your backup using Transact-SQL, see [Create an Encrypted Backup](create-an-encrypted-backup.md).</span></span>  
  
### <a name="using-sql-server-management-studio"></a><span data-ttu-id="a4efd-150">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="a4efd-150">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="a4efd-151">在下列任一對話方塊中建立資料庫備份時，您可以加密備份：</span><span class="sxs-lookup"><span data-stu-id="a4efd-151">You can encrypt a backup when creating the backup of a database in any of the following dialog boxes:</span></span>  
  
1.  <span data-ttu-id="a4efd-152">[備份資料庫 &#40;備份選項頁面&#41;](back-up-database-backup-options-page.md)：您可以在 [備份選項] 頁面選取 [加密]，並指定用於加密的加密演算法以及憑證或非對稱金鑰。</span><span class="sxs-lookup"><span data-stu-id="a4efd-152">[Back Up Database &#40;Backup Options Page&#41;](back-up-database-backup-options-page.md) On the **Backup Options** page, you can select **Encryption**, and specify the encryption algorithm and the certificate or asymmetric key to use for the encryption.</span></span>  
  
2.  <span data-ttu-id="a4efd-153">[使用維護計畫精靈](../maintenance-plans/use-the-maintenance-plan-wizard.md#SSMSProcedure)：當您選取備份工作時，您可以在 [Define Backup ()Task (定義備份 () 工作)] 頁面的 [選項] 索引標籤上，選取 [備份加密]，並指定用於加密的加密演算法以及憑證或金鑰。</span><span class="sxs-lookup"><span data-stu-id="a4efd-153">[Using Maintenance Plan Wizard](../maintenance-plans/use-the-maintenance-plan-wizard.md#SSMSProcedure) When you select a backup task, on the **Options** tab of the **Define Backup ()Task** page, you can select **Backup Encryption**, and specify the encryption algorithm and the certificate or key to use for the encryption.</span></span>  
  
### <a name="using-transact-sql"></a><span data-ttu-id="a4efd-154">使用 Transact SQL</span><span class="sxs-lookup"><span data-stu-id="a4efd-154">Using Transact SQL</span></span>  
 <span data-ttu-id="a4efd-155">下列為加密備份檔案的範例 Transact-SQL 陳述式：</span><span class="sxs-lookup"><span data-stu-id="a4efd-155">Following is a sample Transact-SQL statement to encrypt the backup file:</span></span>  
  
```sql
BACKUP DATABASE [MYTestDB]  
TO DISK = N'C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Backup\MyTestDB.bak'  
WITH  
  COMPRESSION,  
  ENCRYPTION   
   (  
   ALGORITHM = AES_256,  
   SERVER CERTIFICATE = BackupEncryptCert  
   ),  
  STATS = 10  
GO
```  
  
 <span data-ttu-id="a4efd-156">如需完整 Transact-SQL 陳述式的語法，請參閱 [BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="a4efd-156">For the full Transact-SQL statement syntax, see [BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql).</span></span>  
  
### <a name="using-powershell"></a><span data-ttu-id="a4efd-157">使用 PowerShell</span><span class="sxs-lookup"><span data-stu-id="a4efd-157">Using PowerShell</span></span>  
 <span data-ttu-id="a4efd-158">此範例會建立加密選項，然後將它當作 **Backup-SqlDatabase** Cmdlet 的參數值使用，以建立加密備份。</span><span class="sxs-lookup"><span data-stu-id="a4efd-158">This example creates the encryption options and uses it as a parameter value in **Backup-SqlDatabase** cmdlet to create an encrypted backup.</span></span>  
  
```powershell
$encryptionOption = New-SqlBackupEncryptionOption -Algorithm Aes256 -EncryptorType ServerCertificate -EncryptorName "BackupCert"  
Backup-SqlDatabase -ServerInstance . -Database "MyTestDB" -BackupFile "MyTestDB.bak" -CompressionOption On -EncryptionOption $encryptionOption  
```  
  
##  <a name="recommended-practices"></a><a name="RecommendedPractices"></a> <span data-ttu-id="a4efd-159">建議的做法</span><span class="sxs-lookup"><span data-stu-id="a4efd-159">Recommended Practices</span></span>  
 <span data-ttu-id="a4efd-160">建立加密憑證和金鑰的備份至您安裝執行個體的本機電腦以外的位置。</span><span class="sxs-lookup"><span data-stu-id="a4efd-160">Create a backup of the encryption certificate and keys to a location other than your local machine where the instance is installed.</span></span> <span data-ttu-id="a4efd-161">若考量到損毀復原狀況，請考慮將憑證或金鑰的備份儲存至異地位置。</span><span class="sxs-lookup"><span data-stu-id="a4efd-161">To account for disaster recovery scenarios, consider storing a backup of the certificate or key to an off-site location.</span></span> <span data-ttu-id="a4efd-162">若沒有用來加密此備份的憑證，您就無法還原加密的備份。</span><span class="sxs-lookup"><span data-stu-id="a4efd-162">You cannot restore an encrypted backup without the certificate used to encrypt the backup.</span></span>  
  
 <span data-ttu-id="a4efd-163">若要還原加密的備份，在相符的指模取得備份時所使用的原始憑證，應可用於您要進行還原的執行個體上。</span><span class="sxs-lookup"><span data-stu-id="a4efd-163">To restore an encrypted backup, the original certificate used when the backup was taken with the matching thumbprint should be available on the instance you are restoring to.</span></span> <span data-ttu-id="a4efd-164">因此，憑證不應該更新到期日或做其他任何的變更。</span><span class="sxs-lookup"><span data-stu-id="a4efd-164">Therefore, the certificate should not be renewed on expiry or changed in any way.</span></span> <span data-ttu-id="a4efd-165">更新會導致觸發指模變更的憑證更新，而使憑證對備份檔案無效。</span><span class="sxs-lookup"><span data-stu-id="a4efd-165">Renewal can result in updating the certificate triggering the change of the thumbprint, therefore making the certificate invalid for the backup file.</span></span> <span data-ttu-id="a4efd-166">執行還原的帳戶應擁有備份時用以加密之憑證或非對稱金鑰的 VIEW DEFINITION 權限。</span><span class="sxs-lookup"><span data-stu-id="a4efd-166">The account performing the restore should have VIEW DEFINITION permissions on the certificate or the asymmetric key used to encrypt during backup.</span></span>  
  
 <span data-ttu-id="a4efd-167">可用性群組資料庫備份通常會在慣用的備份複本上執行。</span><span class="sxs-lookup"><span data-stu-id="a4efd-167">Availability Group database backups are typically performed on the preferred backup replica.</span></span>  <span data-ttu-id="a4efd-168">如果您不是在當初取得備份的複本上還原備份，請確定用於備份的原始憑證可在您要還原的目標複本上使用。</span><span class="sxs-lookup"><span data-stu-id="a4efd-168">If restoring a backup on a replica other than where the backup was taken from, ensure that the original certificate used for backup is available on the replica you are restoring to.</span></span>  
  
 <span data-ttu-id="a4efd-169">若資料庫已啟用 TDE，在加密資料庫和備份時請分別選擇不同的憑證或非對稱金鑰，以提升安全性。</span><span class="sxs-lookup"><span data-stu-id="a4efd-169">If the database is TDE enabled, choose different certificates or asymmetric keys for encrypting the database and the backup to increase security.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="a4efd-170">相關工作</span><span class="sxs-lookup"><span data-stu-id="a4efd-170">Related Tasks</span></span>  
  
|<span data-ttu-id="a4efd-171">主題/工作</span><span class="sxs-lookup"><span data-stu-id="a4efd-171">Topic/Task</span></span>|<span data-ttu-id="a4efd-172">描述</span><span class="sxs-lookup"><span data-stu-id="a4efd-172">Description</span></span>|  
|-----------------|-----------------|  
|[<span data-ttu-id="a4efd-173">建立加密的備份</span><span class="sxs-lookup"><span data-stu-id="a4efd-173">Create an Encrypted Backup</span></span>](create-an-encrypted-backup.md)|<span data-ttu-id="a4efd-174">描述建立加密備份所需的基本步驟</span><span class="sxs-lookup"><span data-stu-id="a4efd-174">Describes the basic steps required to create an encrypted backup</span></span>|  
|[<span data-ttu-id="a4efd-175">SQL Server Managed Backup 到 Azure - 保留和儲存體設定</span><span class="sxs-lookup"><span data-stu-id="a4efd-175">SQL Server Managed Backup to Azure - Retention and Storage Settings</span></span>](../../database-engine/sql-server-managed-backup-to-windows-azure-retention-and-storage-settings.md)|<span data-ttu-id="a4efd-176">描述指定加密選項時設定[!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]所需的基本步驟。</span><span class="sxs-lookup"><span data-stu-id="a4efd-176">Describes the basic steps required to configure [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] with the encryption options specified.</span></span>|  
|[<span data-ttu-id="a4efd-177">使用 Azure 金鑰保存庫進行可延伸金鑰管理 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="a4efd-177">Extensible Key Management Using Azure Key Vault &#40;SQL Server&#41;</span></span>](../security/encryption/extensible-key-management-using-azure-key-vault-sql-server.md)|<span data-ttu-id="a4efd-178">提供在 Azure 金鑰保存庫中建立受金鑰保護的加密備份範例。</span><span class="sxs-lookup"><span data-stu-id="a4efd-178">Provides an example of creating an encrypted backup protected by keys in the Azure Key Vault.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a4efd-179">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a4efd-179">See Also</span></span>  
 [<span data-ttu-id="a4efd-180">備份概觀 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="a4efd-180">Backup Overview &#40;SQL Server&#41;</span></span>](backup-overview-sql-server.md)  
  
  
