---
title: SQL Server 和資料庫加密金鑰 (Database Engine) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- keys [SQL Server], database encryption
ms.assetid: 15c0a5e8-9177-484c-ae75-8c552dc0dac0
author: jaszymas
ms.author: jaszymas
ms.openlocfilehash: f846e74e0afd89c6bb10a4aa9a23a6420b6a613a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710514"
---
# <a name="sql-server-and-database-encryption-keys-database-engine"></a><span data-ttu-id="db5e5-102">SQL Server 和資料庫加密金鑰 (Database Engine)</span><span class="sxs-lookup"><span data-stu-id="db5e5-102">SQL Server and Database Encryption Keys (Database Engine)</span></span>
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="db5e5-103">會使用加密金鑰來保護儲存於伺服器資料庫中之資料、認證和連接資訊的安全。</span><span class="sxs-lookup"><span data-stu-id="db5e5-103">uses encryption keys to help secure data, credentials, and connection information that is stored in a server database.</span></span> [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="db5e5-104">有兩種類型的金鑰： *「對稱」* (Symmetric) 與 *「非對稱」* (Asymmetric)。</span><span class="sxs-lookup"><span data-stu-id="db5e5-104">has two kinds of keys: *symmetric* and *asymmetric*.</span></span> <span data-ttu-id="db5e5-105">對稱金鑰會使用相同的密碼為資料加密與解密。</span><span class="sxs-lookup"><span data-stu-id="db5e5-105">Symmetric keys use the same password to encrypt and decrypt data.</span></span> <span data-ttu-id="db5e5-106">非對稱金鑰會使用某個密碼來加密資料 (稱為「公開」金鑰)，並使用另一個密碼來解密資料 (稱為「私密」金鑰)。</span><span class="sxs-lookup"><span data-stu-id="db5e5-106">Asymmetric keys use one password to encrypt data (called the *public* key) and another to decrypt data (called the *private* key).</span></span>  
  
 <span data-ttu-id="db5e5-107">在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]中，加密金鑰包括用於保護機密資料的公開、私密和對稱金鑰的組合。</span><span class="sxs-lookup"><span data-stu-id="db5e5-107">In [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], encryption keys include a combination of public, private, and symmetric keys that are used to protect sensitive data.</span></span> <span data-ttu-id="db5e5-108">當您初次啟動 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體時，會在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 初始化期間建立對稱金鑰。</span><span class="sxs-lookup"><span data-stu-id="db5e5-108">The symmetric key is created during [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] initialization when you first start the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance.</span></span> <span data-ttu-id="db5e5-109">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 會使用此金鑰來加密 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]內所儲存的敏感性資料。</span><span class="sxs-lookup"><span data-stu-id="db5e5-109">The key is used by [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] to encrypt sensitive data that is stored in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="db5e5-110">公開金鑰和私密金鑰是由作業系統所建立，可用來保護對稱金鑰。</span><span class="sxs-lookup"><span data-stu-id="db5e5-110">Public and private keys are created by the operating system and they are used to protect the symmetric key.</span></span> <span data-ttu-id="db5e5-111">針對負責儲存資料庫中之敏感性資料的每一個 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體，建立一組公開金鑰和私密金鑰。</span><span class="sxs-lookup"><span data-stu-id="db5e5-111">A public and private key pair is created for each [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance that stores sensitive data in a database.</span></span>  
  
## <a name="applications-for-sql-server-and-database-keys"></a><span data-ttu-id="db5e5-112">SQL Server 和資料庫金鑰的套用</span><span class="sxs-lookup"><span data-stu-id="db5e5-112">Applications for SQL Server and Database Keys</span></span>  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="db5e5-113">對於金鑰有兩個主要的應用：針對 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體產生「服務主要金鑰」(SMK)，並將「資料庫主要金鑰」(DMK) 用於資料庫。</span><span class="sxs-lookup"><span data-stu-id="db5e5-113">has two primary applications for keys: a *service master key* (SMK) generated on and for a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance, and a *database master key* (DMK) used for a database.</span></span>  
  
 <span data-ttu-id="db5e5-114">SMK 會在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體第一次啟動時自動產生，並用來加密連結伺服器密碼、認證和資料庫主要金鑰。</span><span class="sxs-lookup"><span data-stu-id="db5e5-114">The SMK is automatically generated the first time the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance is started and is used to encrypt a linked server password, credentials, and the database master key.</span></span> <span data-ttu-id="db5e5-115">SMK 的加密方式，是使用透過 Windows Data Protection API (DPAPI) 的本機電腦金鑰。</span><span class="sxs-lookup"><span data-stu-id="db5e5-115">The SMK is encrypted by using the local computer key using the Windows Data Protection API (DPAPI).</span></span> <span data-ttu-id="db5e5-116">DPAPI 會使用一個衍生自 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 服務帳戶和電腦認證之 Windows 認證的金鑰。</span><span class="sxs-lookup"><span data-stu-id="db5e5-116">The DPAPI uses a key that is derived from the Windows credentials of the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] service account and the computer's credentials.</span></span> <span data-ttu-id="db5e5-117">服務主要金鑰只能由建立它時所使用的服務帳戶解密，或是只能由可以存取電腦認證的主體解密。</span><span class="sxs-lookup"><span data-stu-id="db5e5-117">The service master key can only be decrypted by the service account under which it was created or by a principal that has access to the machine's credentials.</span></span>  
  
 <span data-ttu-id="db5e5-118">資料庫主要金鑰是一個用來保護資料庫中憑證之私密金鑰和非對稱金鑰的對稱金鑰。</span><span class="sxs-lookup"><span data-stu-id="db5e5-118">The database master key is a symmetric key that is used to protect the private keys of certificates and asymmetric keys that are present in the database.</span></span> <span data-ttu-id="db5e5-119">它也可以用來加密資料，但是有長度上的限制，因此與對稱金鑰相較之下，它用於資料時比較不實用。</span><span class="sxs-lookup"><span data-stu-id="db5e5-119">It can also be used to encrypt data, but it has length limitations that make it less practical for data than using a symmetric key.</span></span>  
  
 <span data-ttu-id="db5e5-120">建立資料庫主要金鑰時，會利用三重 DES 演算法和使用者提供的密碼來加密主要金鑰。</span><span class="sxs-lookup"><span data-stu-id="db5e5-120">When it is created, the master key is encrypted by using the Triple DES algorithm and a user-supplied password.</span></span> <span data-ttu-id="db5e5-121">若要啟用主要金鑰的自動解密，就要使用 SMK 來加密此金鑰的複本。</span><span class="sxs-lookup"><span data-stu-id="db5e5-121">To enable the automatic decryption of the master key, a copy of the key is encrypted by using the SMK.</span></span> <span data-ttu-id="db5e5-122">這個複本會同時存放在使用它的資料庫和 `master` 系統資料庫中。</span><span class="sxs-lookup"><span data-stu-id="db5e5-122">It is stored in both the database where it is used and in the `master` system database.</span></span>  
  
 <span data-ttu-id="db5e5-123">每當 DMK 變更時，也會以無訊息模式更新儲存於 `master` 系統資料庫中的 DMK 複本。</span><span class="sxs-lookup"><span data-stu-id="db5e5-123">The copy of the DMK stored in the `master` system database is silently updated whenever the DMK is changed.</span></span> <span data-ttu-id="db5e5-124">但是，此預設值可以使用 `DROP ENCRYPTION BY SERVICE MASTER KEY` 陳述式的 `ALTER MASTER KEY` 選項來加以變更。</span><span class="sxs-lookup"><span data-stu-id="db5e5-124">However, this default can be changed by using the `DROP ENCRYPTION BY SERVICE MASTER KEY` option of the `ALTER MASTER KEY` statement.</span></span> <span data-ttu-id="db5e5-125">未以服務主要金鑰加密的 DMK 必須使用 `OPEN MASTER KEY` 陳述式和密碼來開啟。</span><span class="sxs-lookup"><span data-stu-id="db5e5-125">A DMK that is not encrypted by the service master key must be opened by using the `OPEN MASTER KEY` statement and a password.</span></span>  
  
## <a name="managing-sql-server-and-database-keys"></a><span data-ttu-id="db5e5-126">管理 SQL Server 和資料庫金鑰</span><span class="sxs-lookup"><span data-stu-id="db5e5-126">Managing SQL Server and Database Keys</span></span>  
 <span data-ttu-id="db5e5-127">加密金鑰的管理包括建立新的資料庫金鑰、建立伺服器和資料庫金鑰的備份，以及了解還原、刪除或變更金鑰的時機和方法。</span><span class="sxs-lookup"><span data-stu-id="db5e5-127">Managing encryption keys consists of creating new database keys, creating a backup of the server and database keys, and knowing when and how to restore, delete, or change the keys.</span></span>  
  
 <span data-ttu-id="db5e5-128">若要管理對稱金鑰，您可以使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 所包含的工具執行以下作業：</span><span class="sxs-lookup"><span data-stu-id="db5e5-128">To manage symmetric keys, you can use the tools included in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] to do the following:</span></span>  
  
-   <span data-ttu-id="db5e5-129">備份伺服器和資料庫金鑰的複本，讓您能夠使用它們來復原伺服器安裝，或當做計劃移轉的一部分。</span><span class="sxs-lookup"><span data-stu-id="db5e5-129">Back up a copy of the server and database keys so that you can use them to recover a server installation, or as part of a planned migration.</span></span>  
  
-   <span data-ttu-id="db5e5-130">將之前儲存的金鑰還原至資料庫。</span><span class="sxs-lookup"><span data-stu-id="db5e5-130">Restore a previously saved key to a database.</span></span> <span data-ttu-id="db5e5-131">如此可讓新的伺服器執行個體存取它原先未加密的現有資料。</span><span class="sxs-lookup"><span data-stu-id="db5e5-131">This enables a new server instance to access existing data that it did not originally encrypt.</span></span>  
  
-   <span data-ttu-id="db5e5-132">當發生無法再存取加密資料的罕見事件中，刪除資料庫中的加密資料。</span><span class="sxs-lookup"><span data-stu-id="db5e5-132">Delete the encrypted data in a database in the unlikely event that you can no longer access encrypted data.</span></span>  
  
-   <span data-ttu-id="db5e5-133">在金鑰受到危害的罕見事件中，重新建立金鑰並重新加密資料。</span><span class="sxs-lookup"><span data-stu-id="db5e5-133">Re-create keys and re-encrypt data in the unlikely event that the key is compromised.</span></span> <span data-ttu-id="db5e5-134">就安全性最佳作法而言，您應定期重新建立金鑰 (例如，每隔幾個月)，以保護伺服器免於駭客進行破解金鑰的攻擊。</span><span class="sxs-lookup"><span data-stu-id="db5e5-134">As a security best practice, you should re-create the keys periodically (for example, every few months) to protect the server from attacks that try to decipher the keys.</span></span>  
  
-   <span data-ttu-id="db5e5-135">在伺服器向外延展部署中加入或移除伺服器執行個體，其中多部伺服器會共用單一資料庫以及能加解密該資料庫的金鑰。</span><span class="sxs-lookup"><span data-stu-id="db5e5-135">Add or remove a server instance from a server scale-out deployment where multiple servers share both a single database and the key that provides reversible encryption for that database.</span></span>  
  
## <a name="important-security-information"></a><span data-ttu-id="db5e5-136">重要安全性資訊</span><span class="sxs-lookup"><span data-stu-id="db5e5-136">Important Security Information</span></span>  
 <span data-ttu-id="db5e5-137">存取由服務主要金鑰維護安全的物件需要之前用來建立此金鑰的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 服務帳戶或是電腦帳戶。</span><span class="sxs-lookup"><span data-stu-id="db5e5-137">Accessing objects secured by the service master key requires either the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Service account that was used to create the key or the computer (machine) account.</span></span> <span data-ttu-id="db5e5-138">也就是說，電腦會與金鑰建立所在的系統繫結在一起。</span><span class="sxs-lookup"><span data-stu-id="db5e5-138">That is, the computer is tied to the system where the key was created.</span></span> <span data-ttu-id="db5e5-139">您可以變更 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 服務帳戶 *或* 電腦帳戶，而不會遺失對此金鑰的存取權。</span><span class="sxs-lookup"><span data-stu-id="db5e5-139">You can change the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Service account *or* the computer account without losing access to the key.</span></span> <span data-ttu-id="db5e5-140">但是，如果您變更這兩者，您將會遺失對服務主要金鑰的存取權。</span><span class="sxs-lookup"><span data-stu-id="db5e5-140">However, if you change both, you will lose access to the service master key.</span></span> <span data-ttu-id="db5e5-141">如果您在沒有這兩個元素之其中一個的情況下遺失對服務主要金鑰的存取權，您將無法使用原始金鑰來解密資料和物件。</span><span class="sxs-lookup"><span data-stu-id="db5e5-141">If you lose access to the service master key without one of these two elements, you be unable to decrypt data and objects encrypted by using the original key.</span></span>  
  
 <span data-ttu-id="db5e5-142">以服務主要金鑰維護安全的連接一定要有服務主要金鑰，才能進行還原。</span><span class="sxs-lookup"><span data-stu-id="db5e5-142">Connections secured with the service master key cannot be restored without the service master key.</span></span>  
  
 <span data-ttu-id="db5e5-143">當存取以資料庫主要金鑰維護安全的物件和資料時，只需要用來維護此金鑰安全的密碼。</span><span class="sxs-lookup"><span data-stu-id="db5e5-143">Access to objects and data secured with the database master key require only the password that is used to help secure the key.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="db5e5-144">如果您遺失對上述金鑰的所有存取權，您也會遺失用這些金鑰維護安全之物件、連接和資料的存取權。</span><span class="sxs-lookup"><span data-stu-id="db5e5-144">If you lose all access to the keys described earlier, you will lose access to the objects, connections, and data secured by those keys.</span></span> <span data-ttu-id="db5e5-145">您可以還原服務主要金鑰 (如這裡所顯示的連結中所述)，或者回到原始加密系統來復原存取。</span><span class="sxs-lookup"><span data-stu-id="db5e5-145">You can restore the service master key, as described in the links that are shown here, or you can go back to the original encrypting system to recover the access.</span></span> <span data-ttu-id="db5e5-146">並沒有其他「捷徑」可復原存取。</span><span class="sxs-lookup"><span data-stu-id="db5e5-146">There is no "back-door" to recover the access.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="db5e5-147">本節內容</span><span class="sxs-lookup"><span data-stu-id="db5e5-147">In This Section</span></span>  
 [<span data-ttu-id="db5e5-148">服務主要金鑰</span><span class="sxs-lookup"><span data-stu-id="db5e5-148">Service Master Key</span></span>](service-master-key.md)  
 <span data-ttu-id="db5e5-149">提供服務主要金鑰和其最佳作法的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="db5e5-149">Provides a brief explanation for the service master key and its best practices.</span></span>  
  
 [<span data-ttu-id="db5e5-150">可延伸金鑰管理 &#40;EKM&#41;</span><span class="sxs-lookup"><span data-stu-id="db5e5-150">Extensible Key Management &#40;EKM&#41;</span></span>](extensible-key-management-ekm.md)  
 <span data-ttu-id="db5e5-151">說明如何搭配 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]使用協力廠商金鑰管理系統。</span><span class="sxs-lookup"><span data-stu-id="db5e5-151">Explains how to use third-party key management systems with [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="db5e5-152">相關工作</span><span class="sxs-lookup"><span data-stu-id="db5e5-152">Related Tasks</span></span>  
 [<span data-ttu-id="db5e5-153">備份服務主要金鑰</span><span class="sxs-lookup"><span data-stu-id="db5e5-153">Back Up the Service Master Key</span></span>](back-up-the-service-master-key.md)  
  
 [<span data-ttu-id="db5e5-154">還原服務主要金鑰</span><span class="sxs-lookup"><span data-stu-id="db5e5-154">Restore the Service Master Key</span></span>](restore-the-service-master-key.md)  
  
 [<span data-ttu-id="db5e5-155">建立資料庫主要金鑰</span><span class="sxs-lookup"><span data-stu-id="db5e5-155">Create a Database Master Key</span></span>](create-a-database-master-key.md)  
  
 [<span data-ttu-id="db5e5-156">備份資料庫主要金鑰</span><span class="sxs-lookup"><span data-stu-id="db5e5-156">Back Up a Database Master Key</span></span>](back-up-a-database-master-key.md)  
  
 [<span data-ttu-id="db5e5-157">還原資料庫主要金鑰</span><span class="sxs-lookup"><span data-stu-id="db5e5-157">Restore a Database Master Key</span></span>](restore-a-database-master-key.md)  
  
 [<span data-ttu-id="db5e5-158">在兩部伺服器上建立相同的對稱金鑰</span><span class="sxs-lookup"><span data-stu-id="db5e5-158">Create Identical Symmetric Keys on Two Servers</span></span>](create-identical-symmetric-keys-on-two-servers.md)  
  
 [<span data-ttu-id="db5e5-159">使用 Azure 金鑰保存庫進行可延伸金鑰管理 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="db5e5-159">Extensible Key Management Using Azure Key Vault &#40;SQL Server&#41;</span></span>](extensible-key-management-using-azure-key-vault-sql-server.md)  
  
 [<span data-ttu-id="db5e5-160">使用 EKM 啟用 TDE</span><span class="sxs-lookup"><span data-stu-id="db5e5-160">Enable TDE Using EKM</span></span>](enable-tde-on-sql-server-using-ekm.md)  
  
## <a name="related-content"></a><span data-ttu-id="db5e5-161">相關內容</span><span class="sxs-lookup"><span data-stu-id="db5e5-161">Related Content</span></span>  
 [<span data-ttu-id="db5e5-162">CREATE MASTER KEY &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="db5e5-162">CREATE MASTER KEY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-master-key-transact-sql)  
  
 [<span data-ttu-id="db5e5-163">ALTER SERVICE MASTER KEY &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="db5e5-163">ALTER SERVICE MASTER KEY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-service-master-key-transact-sql)  
  
 [<span data-ttu-id="db5e5-164">還原資料庫主要金鑰</span><span class="sxs-lookup"><span data-stu-id="db5e5-164">Restore a Database Master Key</span></span>](restore-a-database-master-key.md)  
  
## <a name="see-also"></a><span data-ttu-id="db5e5-165">另請參閱</span><span class="sxs-lookup"><span data-stu-id="db5e5-165">See Also</span></span>  
 <span data-ttu-id="db5e5-166">[備份與還原 Reporting Services 加密金鑰](../../../reporting-services/install-windows/ssrs-encryption-keys-back-up-and-restore-encryption-keys.md) </span><span class="sxs-lookup"><span data-stu-id="db5e5-166">[Back Up and Restore Reporting Services Encryption Keys](../../../reporting-services/install-windows/ssrs-encryption-keys-back-up-and-restore-encryption-keys.md) </span></span>  
 <span data-ttu-id="db5e5-167">[刪除和重新建立加密金鑰 &#40;SSRS 組態管理員&#41;](../../../reporting-services/install-windows/ssrs-encryption-keys-delete-and-re-create-encryption-keys.md) </span><span class="sxs-lookup"><span data-stu-id="db5e5-167">[Delete and Re-create Encryption Keys  &#40;SSRS Configuration Manager&#41;](../../../reporting-services/install-windows/ssrs-encryption-keys-delete-and-re-create-encryption-keys.md) </span></span>  
 <span data-ttu-id="db5e5-168">[加入和移除向外延展部署的加密金鑰 &#40;SSRS 組態管理員&#41;](../../../reporting-services/install-windows/add-and-remove-encryption-keys-for-scale-out-deployment.md) </span><span class="sxs-lookup"><span data-stu-id="db5e5-168">[Add and Remove Encryption Keys for Scale-Out Deployment &#40;SSRS Configuration Manager&#41;](../../../reporting-services/install-windows/add-and-remove-encryption-keys-for-scale-out-deployment.md) </span></span>  
 [<span data-ttu-id="db5e5-169">透明資料加密 &#40;TDE&#41;</span><span class="sxs-lookup"><span data-stu-id="db5e5-169">Transparent Data Encryption &#40;TDE&#41;</span></span>](transparent-data-encryption.md)  
  
  
