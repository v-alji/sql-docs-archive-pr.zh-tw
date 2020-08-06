---
title: 透明資料加密 (TDE) | Microsoft 文件
ms.custom: ''
ms.date: 11/23/2015
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Transparent Data Encryption
- database encryption key, about
- TDE
- database encryption key
- TDE, about
- Transparent Data Encryption, about
- encryption [SQL Server], transparent data encryption
ms.assetid: c75d0d4b-4008-4e71-9a9d-cee2a566bd3b
author: jaszymas
ms.author: jaszymas
ms.openlocfilehash: a8118f0781d7c9e3d839c029c6bdaf8b01e074b0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596611"
---
# <a name="transparent-data-encryption-tde"></a><span data-ttu-id="a739d-102">透明資料加密 (TDE)</span><span class="sxs-lookup"><span data-stu-id="a739d-102">Transparent Data Encryption (TDE)</span></span>
  <span data-ttu-id="a739d-103">*透明資料加密* (TDE) 會加密 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 和 [!INCLUDE[ssSDSfull](../../../includes/sssdsfull-md.md)] 資料檔案，一般稱之為靜止的加密資料。</span><span class="sxs-lookup"><span data-stu-id="a739d-103">*Transparent Data Encryption* (TDE) encrypts [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] and [!INCLUDE[ssSDSfull](../../../includes/sssdsfull-md.md)] data files, known as encrypting data at rest.</span></span> <span data-ttu-id="a739d-104">您可以採取數個預防措施來協助保護資料庫，例如設定安全系統、加密機密資產，以及建置圍繞資料庫伺服器的防火牆。</span><span class="sxs-lookup"><span data-stu-id="a739d-104">You can take several precautions to help secure the database such as designing a secure system, encrypting confidential assets, and building a firewall around the database servers.</span></span> <span data-ttu-id="a739d-105">不過，在實體媒體 (例如磁碟機或備份磁帶) 遭竊的案例中，惡意人士可能會直接還原或附加資料庫，然後瀏覽資料。</span><span class="sxs-lookup"><span data-stu-id="a739d-105">However, in a scenario where the physical media (such as drives or backup tapes) are stolen, a malicious party can just restore or attach the database and browse the data.</span></span> <span data-ttu-id="a739d-106">一個解決方案是加密資料庫中的敏感性資料，並使用憑證來保護用來加密資料的金鑰。</span><span class="sxs-lookup"><span data-stu-id="a739d-106">One solution is to encrypt the sensitive data in the database and protect the keys that are used to encrypt the data with a certificate.</span></span> <span data-ttu-id="a739d-107">如此可防止沒有金鑰的任何人使用資料，但是這種防護類型必須事先規劃。</span><span class="sxs-lookup"><span data-stu-id="a739d-107">This prevents anyone without the keys from using the data, but this kind of protection must be planned in advance.</span></span>

 <span data-ttu-id="a739d-108">TDE 會執行資料和記錄檔的即時 I/O 加密和解密。</span><span class="sxs-lookup"><span data-stu-id="a739d-108">TDE performs real-time I/O encryption and decryption of the data and log files.</span></span> <span data-ttu-id="a739d-109">加密會使用資料庫加密金鑰 (DEK)，此金鑰會儲存在資料庫開機記錄中，以在復原期間提供可用性。</span><span class="sxs-lookup"><span data-stu-id="a739d-109">The encryption uses a database encryption key (DEK), which is stored in the database boot record for availability during recovery.</span></span> <span data-ttu-id="a739d-110">DEK 是對稱金鑰，而其維護安全的方式是使用儲存於伺服器之 master 資料庫內的憑證或是受到 EKM 模組所保護的非對稱金鑰。</span><span class="sxs-lookup"><span data-stu-id="a739d-110">The DEK is a symmetric key secured by using a certificate stored in the master database of the server or an asymmetric key protected by an EKM module.</span></span> <span data-ttu-id="a739d-111">TDE 會保護休眠的資料，也就是資料檔和記錄檔。</span><span class="sxs-lookup"><span data-stu-id="a739d-111">TDE protects data "at rest", meaning the data and log files.</span></span> <span data-ttu-id="a739d-112">它提供了與各個不同業界內建立的許多法令、規章和指導方針相符的能力，</span><span class="sxs-lookup"><span data-stu-id="a739d-112">It provides the ability to comply with many laws, regulations, and guidelines established in various industries.</span></span> <span data-ttu-id="a739d-113">如此可讓軟體開發人員使用 AES 和 3DES 加密演算法加密資料，而不需要變更現有的應用程式。</span><span class="sxs-lookup"><span data-stu-id="a739d-113">This enables software developers to encrypt data by using AES and 3DES encryption algorithms without changing existing applications.</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="a739d-114">TDE 不會提供跨通訊通道的加密。</span><span class="sxs-lookup"><span data-stu-id="a739d-114">TDE does not provide encryption across communication channels.</span></span> <span data-ttu-id="a739d-115">如需如何跨通訊通道加密資料的詳細資訊，請參閱[啟用 Database Engine 的加密連接 &#40;SQL Server 組態管理員&#41;](../../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md)。</span><span class="sxs-lookup"><span data-stu-id="a739d-115">For more information about how to encrypt data across communication channels, see [Enable Encrypted Connections to the Database Engine &#40;SQL Server Configuration Manager&#41;](../../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md).</span></span>
> 
>  <span data-ttu-id="a739d-116">**相關主題：**</span><span class="sxs-lookup"><span data-stu-id="a739d-116">**Related topics:**</span></span>
> 
>  -   [<span data-ttu-id="a739d-117">Azure SQL Database 的透明資料加密</span><span class="sxs-lookup"><span data-stu-id="a739d-117">Transparent Data Encryption with Azure SQL Database</span></span>](../../../database-engine/transparent-data-encryption-with-azure-sql-database.md)
> -   [<span data-ttu-id="a739d-118">將 TDE 保護的資料庫移至另一個 SQL Server</span><span class="sxs-lookup"><span data-stu-id="a739d-118">Move a TDE Protected Database to Another SQL Server</span></span>](move-a-tde-protected-database-to-another-sql-server.md)
> -   [<span data-ttu-id="a739d-119">使用 EKM 啟用 TDE</span><span class="sxs-lookup"><span data-stu-id="a739d-119">Enable TDE Using EKM</span></span>](enable-tde-on-sql-server-using-ekm.md)

## <a name="about-tde"></a><span data-ttu-id="a739d-120">關於 TDE</span><span class="sxs-lookup"><span data-stu-id="a739d-120">About TDE</span></span>
 <span data-ttu-id="a739d-121">資料庫檔案的加密會在頁面層級執行。</span><span class="sxs-lookup"><span data-stu-id="a739d-121">Encryption of the database file is performed at the page level.</span></span> <span data-ttu-id="a739d-122">加密資料庫中的頁面會在寫入磁碟前先加密，並在讀入記憶體時進行解密。</span><span class="sxs-lookup"><span data-stu-id="a739d-122">The pages in an encrypted database are encrypted before they are written to disk and decrypted when read into memory.</span></span> <span data-ttu-id="a739d-123">TDE 並不會讓加密之資料庫的大小增加。</span><span class="sxs-lookup"><span data-stu-id="a739d-123">TDE does not increase the size of the encrypted database.</span></span>

 <span data-ttu-id="a739d-124">**適用于的資訊[!INCLUDE[ssSDS](../../../includes/sssds-md.md)]**</span><span class="sxs-lookup"><span data-stu-id="a739d-124">**Information applicable to [!INCLUDE[ssSDS](../../../includes/sssds-md.md)]**</span></span>

 <span data-ttu-id="a739d-125">在搭配使用 TDE 與 [!INCLUDE[sqldbesa](../../../includes/sqldbesa-md.md)] V12 ([某些區域處於預覽階段](https://azure.microsoft.com/documentation/articles/sql-database-preview-whats-new/?WT.mc_id=TSQL_GetItTag)) 時， [!INCLUDE[ssSDS](../../../includes/sssds-md.md)]會自動為您建立儲存在主要資料庫中的伺服器層級憑證。</span><span class="sxs-lookup"><span data-stu-id="a739d-125">When using TDE with [!INCLUDE[sqldbesa](../../../includes/sqldbesa-md.md)] V12  ([Preview in some regions](https://azure.microsoft.com/documentation/articles/sql-database-preview-whats-new/?WT.mc_id=TSQL_GetItTag)) the server-level certificate stored in the master database is automatically created for you by [!INCLUDE[ssSDS](../../../includes/sssds-md.md)].</span></span> <span data-ttu-id="a739d-126">若要在 [!INCLUDE[ssSDS](../../../includes/sssds-md.md)] 上移動 TDE 資料庫，您必須解密資料庫、移動資料庫，然後在目的地 [!INCLUDE[ssSDS](../../../includes/sssds-md.md)]上重新啟用 TDE。</span><span class="sxs-lookup"><span data-stu-id="a739d-126">To move a TDE database on [!INCLUDE[ssSDS](../../../includes/sssds-md.md)] you must decrypt the database, move the database, and then re-enable TDE on the destination [!INCLUDE[ssSDS](../../../includes/sssds-md.md)].</span></span> <span data-ttu-id="a739d-127">如需在 [!INCLUDE[ssSDS](../../../includes/sssds-md.md)]上使用 TDE 的逐步解說，請參閱 [Transparent Data Encryption with Azure SQL Database](../../../database-engine/transparent-data-encryption-with-azure-sql-database.md)＞。</span><span class="sxs-lookup"><span data-stu-id="a739d-127">For step-by-step instructions for TDE on [!INCLUDE[ssSDS](../../../includes/sssds-md.md)], see [Transparent Data Encryption with Azure SQL Database](../../../database-engine/transparent-data-encryption-with-azure-sql-database.md).</span></span>

 <span data-ttu-id="a739d-128">TDE 狀態預覽即使在 [!INCLUDE[ssSDS](../../../includes/sssds-md.md)] 版本系列 V12 已宣佈為目前處於公開可用狀態的地理區域也適用。</span><span class="sxs-lookup"><span data-stu-id="a739d-128">The preview of status of TDE applies even in the subset of geographic regions where version family V12 of [!INCLUDE[ssSDS](../../../includes/sssds-md.md)] is announced as now being in general availability status.</span></span> <span data-ttu-id="a739d-129">在 [!INCLUDE[ssSDS](../../../includes/sssds-md.md)] 宣佈 TDE 從預覽版升級至 GA 前， [!INCLUDE[msCoName](../../../includes/msconame-md.md)] 的 TDE 並不適用於生產資料庫。</span><span class="sxs-lookup"><span data-stu-id="a739d-129">TDE for [!INCLUDE[ssSDS](../../../includes/sssds-md.md)] is not intended for use in production databases until [!INCLUDE[msCoName](../../../includes/msconame-md.md)] announces that TDE is promoted from preview to GA.</span></span> <span data-ttu-id="a739d-130">如需有關 [!INCLUDE[ssSDS](../../../includes/sssds-md.md)] V12 的詳細資訊，請參閱 [Azure SQL Database 的新功能](https://azure.microsoft.com/documentation/articles/sql-database-preview-whats-new/)。</span><span class="sxs-lookup"><span data-stu-id="a739d-130">For more information about [!INCLUDE[ssSDS](../../../includes/sssds-md.md)] V12, see [What's new in Azure SQL Database](https://azure.microsoft.com/documentation/articles/sql-database-preview-whats-new/).</span></span>

 <span data-ttu-id="a739d-131">**適用于的資訊[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]**</span><span class="sxs-lookup"><span data-stu-id="a739d-131">**Information applicable to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]**</span></span>

 <span data-ttu-id="a739d-132">在設定資料庫安全性之後，可以使用正確的憑證將它還原。</span><span class="sxs-lookup"><span data-stu-id="a739d-132">After it is secured, the database can be restored by using the correct certificate.</span></span> <span data-ttu-id="a739d-133">如需有關憑證的詳細資訊，請參閱＜ [SQL Server Certificates and Asymmetric Keys](../sql-server-certificates-and-asymmetric-keys.md)＞。</span><span class="sxs-lookup"><span data-stu-id="a739d-133">For more information about certificates, see [SQL Server Certificates and Asymmetric Keys](../sql-server-certificates-and-asymmetric-keys.md).</span></span>

 <span data-ttu-id="a739d-134">當啟用 TDE 時，您應該立即備份憑證以及與此憑證有關的私密金鑰。</span><span class="sxs-lookup"><span data-stu-id="a739d-134">When enabling TDE, you should immediately back up the certificate and the private key associated with the certificate.</span></span> <span data-ttu-id="a739d-135">如果此憑證無法使用或是您必須在另一部伺服器上還原或附加資料庫，您必須同時擁有此憑證和私密金鑰的備份，否則將無法開啟資料庫。</span><span class="sxs-lookup"><span data-stu-id="a739d-135">If the certificate ever becomes unavailable or if you must restore or attach the database on another server, you must have backups of both the certificate and the private key or you will not be able to open the database.</span></span> <span data-ttu-id="a739d-136">即使資料庫上不再啟用 TDE，還是應該保留加密憑證。</span><span class="sxs-lookup"><span data-stu-id="a739d-136">The encrypting certificate should be retained even if TDE is no longer enabled on the database.</span></span> <span data-ttu-id="a739d-137">就算資料庫並未加密，交易記錄的某些部分可能仍受到保護，因而有些作業截至資料庫執行完整備份為止或許都需要此憑證。</span><span class="sxs-lookup"><span data-stu-id="a739d-137">Even though the database is not encrypted, parts of the transaction log may still remain protected, and the certificate may be needed for some operations until the full backup of the database is performed.</span></span> <span data-ttu-id="a739d-138">已經超過到期日的憑證仍然可用來搭配 TDE 加密和解密資料。</span><span class="sxs-lookup"><span data-stu-id="a739d-138">A certificate that has exceeded its expiration date can still be used to encrypt and decrypt data with TDE.</span></span>

 <span data-ttu-id="a739d-139">**加密階層**</span><span class="sxs-lookup"><span data-stu-id="a739d-139">**Encryption Hierarchy**</span></span>

 <span data-ttu-id="a739d-140">下圖顯示 TDE 加密的架構。</span><span class="sxs-lookup"><span data-stu-id="a739d-140">The following illustration shows the architecture of TDE encryption.</span></span> <span data-ttu-id="a739d-141">在 [!INCLUDE[ssSDS](../../../includes/sssds-md.md)]上使用 TDE 時，只有資料庫層級項目 (資料庫加密金鑰) 和 ALTER DATABASE 部分是使用者可設定的。</span><span class="sxs-lookup"><span data-stu-id="a739d-141">Only the database level items (the database encryption key and ALTER DATABASE portions are user-configurable when using TDE on [!INCLUDE[ssSDS](../../../includes/sssds-md.md)].</span></span>

 <span data-ttu-id="a739d-142">![顯示主題中所描述的階層。](../../../database-engine/media/tde-architecture.gif "顯示主題中所描述的階層。")</span><span class="sxs-lookup"><span data-stu-id="a739d-142">![Displays the hierarchy described in the topic.](../../../database-engine/media/tde-architecture.gif "Displays the hierarchy described in the topic.")</span></span>

## <a name="using-transparent-data-encryption"></a><span data-ttu-id="a739d-143">使用透明資料加密</span><span class="sxs-lookup"><span data-stu-id="a739d-143">Using Transparent Data Encryption</span></span>
 <span data-ttu-id="a739d-144">若要使用 TDE，請遵循下列步驟。</span><span class="sxs-lookup"><span data-stu-id="a739d-144">To use TDE, follow these steps.</span></span>

||
|-|
|<span data-ttu-id="a739d-145">**適用於**： [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="a739d-145">**Applies to**: [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>|

-   <span data-ttu-id="a739d-146">建立主要金鑰</span><span class="sxs-lookup"><span data-stu-id="a739d-146">Create a master key</span></span>

-   <span data-ttu-id="a739d-147">建立或取得受到主要金鑰保護的憑證</span><span class="sxs-lookup"><span data-stu-id="a739d-147">Create or obtain a certificate protected by the master key</span></span>

-   <span data-ttu-id="a739d-148">建立資料庫加密金鑰，並使用憑證保護它</span><span class="sxs-lookup"><span data-stu-id="a739d-148">Create a database encryption key and protect it by the certificate</span></span>

-   <span data-ttu-id="a739d-149">設定資料庫使用加密</span><span class="sxs-lookup"><span data-stu-id="a739d-149">Set the database to use encryption</span></span>

 <span data-ttu-id="a739d-150">下列範例說明如何使用 `AdventureWorks2012` 伺服器上安裝的憑證來加密和解密 `MyServerCert`資料庫。</span><span class="sxs-lookup"><span data-stu-id="a739d-150">The following example illustrates encrypting and decrypting the `AdventureWorks2012` database using a certificate installed on the server named `MyServerCert`.</span></span>

```
USE master;
GO
CREATE MASTER KEY ENCRYPTION BY PASSWORD = '<UseStrongPasswordHere>';
go
CREATE CERTIFICATE MyServerCert WITH SUBJECT = 'My DEK Certificate';
go
USE AdventureWorks2012;
GO
CREATE DATABASE ENCRYPTION KEY
WITH ALGORITHM = AES_128
ENCRYPTION BY SERVER CERTIFICATE MyServerCert;
GO
ALTER DATABASE AdventureWorks2012
SET ENCRYPTION ON;
GO
```

 <span data-ttu-id="a739d-151">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]會將加密和解密作業排定在背景執行緒上。</span><span class="sxs-lookup"><span data-stu-id="a739d-151">The encryption and decryption operations are scheduled on background threads by [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="a739d-152">您可以使用本主題稍後出現之清單內的目錄檢視和動態管理檢視，以檢視這些作業的狀態。</span><span class="sxs-lookup"><span data-stu-id="a739d-152">You can view the status of these operations using the catalog views and dynamic management views in the list that appears later in this topic.</span></span>

> [!CAUTION]
>  <span data-ttu-id="a739d-153">啟用了 TDE 的資料庫備份檔案也會使用資料庫加密金鑰來加密。</span><span class="sxs-lookup"><span data-stu-id="a739d-153">Backup files of databases that have TDE enabled are also encrypted by using the database encryption key.</span></span> <span data-ttu-id="a739d-154">因此，當您要還原這些備份時，保護資料庫加密金鑰的憑證必須可以使用。</span><span class="sxs-lookup"><span data-stu-id="a739d-154">As a result, when you restore these backups, the certificate protecting the database encryption key must be available.</span></span> <span data-ttu-id="a739d-155">這表示，除了備份資料庫以外，您也必須確定可維護伺服器憑證的備份，以免資料遺失。</span><span class="sxs-lookup"><span data-stu-id="a739d-155">This means that in addition to backing up the database, you have to make sure that you maintain backups of the server certificates to prevent data loss.</span></span> <span data-ttu-id="a739d-156">如果此憑證無法再使用，就會造成資料遺失。</span><span class="sxs-lookup"><span data-stu-id="a739d-156">Data loss will result if the certificate is no longer available.</span></span> <span data-ttu-id="a739d-157">如需詳細資訊，請參閱 [SQL Server Certificates and Asymmetric Keys](../sql-server-certificates-and-asymmetric-keys.md)。</span><span class="sxs-lookup"><span data-stu-id="a739d-157">For more information, see [SQL Server Certificates and Asymmetric Keys](../sql-server-certificates-and-asymmetric-keys.md).</span></span>

## <a name="commands-and-functions"></a><span data-ttu-id="a739d-158">命令與函數</span><span class="sxs-lookup"><span data-stu-id="a739d-158">Commands and Functions</span></span>
 <span data-ttu-id="a739d-159">TDE 憑證必須由資料庫主要金鑰來加密，才能由下列陳述式所接受。</span><span class="sxs-lookup"><span data-stu-id="a739d-159">The TDE certificates must be encrypted by the database master key to be accepted by the following statements.</span></span> <span data-ttu-id="a739d-160">如果只由密碼加密，下列陳述式將會拒絕它們當做加密程式。</span><span class="sxs-lookup"><span data-stu-id="a739d-160">If they are encrypted by password only, the statements will reject them as encryptors.</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="a739d-161">如果在 TDE 使用這些憑證之後，更改這些憑證使其受到密碼保護，將會造成資料庫重新啟動之後無法存取。</span><span class="sxs-lookup"><span data-stu-id="a739d-161">Altering the certificates to be password-protected after they are used by TDE will cause the database to become inaccessible after a restart.</span></span>

 <span data-ttu-id="a739d-162">下表提供 TDE 命令和函數的連結與說明。</span><span class="sxs-lookup"><span data-stu-id="a739d-162">The following table provides links and explanations of TDE commands and functions.</span></span>

|<span data-ttu-id="a739d-163">命令或函數</span><span class="sxs-lookup"><span data-stu-id="a739d-163">Command or function</span></span>|<span data-ttu-id="a739d-164">目的</span><span class="sxs-lookup"><span data-stu-id="a739d-164">Purpose</span></span>|
|-------------------------|-------------|
|[<span data-ttu-id="a739d-165">CREATE DATABASE ENCRYPTION KEY &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="a739d-165">CREATE DATABASE ENCRYPTION KEY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-database-encryption-key-transact-sql)|<span data-ttu-id="a739d-166">建立用於加密資料庫的金鑰</span><span class="sxs-lookup"><span data-stu-id="a739d-166">Creates a key that is used to encrypt a database.</span></span>|
|[<span data-ttu-id="a739d-167">ALTER DATABASE ENCRYPTION KEY &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="a739d-167">ALTER DATABASE ENCRYPTION KEY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-database-encryption-key-transact-sql)|<span data-ttu-id="a739d-168">變更用於加密資料庫的金鑰</span><span class="sxs-lookup"><span data-stu-id="a739d-168">Changes the key that is used to encrypt a database.</span></span>|
|[<span data-ttu-id="a739d-169">DROP DATABASE ENCRYPTION KEY &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="a739d-169">DROP DATABASE ENCRYPTION KEY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/drop-database-transact-sql)|<span data-ttu-id="a739d-170">移除用於加密資料庫的金鑰。</span><span class="sxs-lookup"><span data-stu-id="a739d-170">Removes the key that was used to encrypt a database.</span></span>|
|[<span data-ttu-id="a739d-171">ALTER DATABASE SET 選項 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="a739d-171">ALTER DATABASE SET Options &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-database-transact-sql-set-options)|<span data-ttu-id="a739d-172">說明用來啟用 TDE 的 `ALTER DATABASE` 選項。</span><span class="sxs-lookup"><span data-stu-id="a739d-172">Explains the `ALTER DATABASE` option that is used to enable TDE.</span></span>|

## <a name="catalog-views-and-dynamic-management-views"></a><span data-ttu-id="a739d-173">目錄檢視和動態管理檢視</span><span class="sxs-lookup"><span data-stu-id="a739d-173">Catalog Views and Dynamic Management Views</span></span>
 <span data-ttu-id="a739d-174">下表顯示 TDE 目錄檢視和動態管理檢視。</span><span class="sxs-lookup"><span data-stu-id="a739d-174">The following table shows TDE catalog views and dynamic management views.</span></span>

|<span data-ttu-id="a739d-175">目錄檢視或動態管理檢視</span><span class="sxs-lookup"><span data-stu-id="a739d-175">Catalog view or dynamic management view</span></span>|<span data-ttu-id="a739d-176">目的</span><span class="sxs-lookup"><span data-stu-id="a739d-176">Purpose</span></span>|
|---------------------------------------------|-------------|
|[<span data-ttu-id="a739d-177">sys.databases &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="a739d-177">sys.databases &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql)|<span data-ttu-id="a739d-178">顯示資料庫資訊的目錄檢視。</span><span class="sxs-lookup"><span data-stu-id="a739d-178">Catalog view that displays database information.</span></span>|
|[<span data-ttu-id="a739d-179">sys.certificates &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="a739d-179">sys.certificates &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-certificates-transact-sql)|<span data-ttu-id="a739d-180">顯示資料庫中之憑證的目錄檢視。</span><span class="sxs-lookup"><span data-stu-id="a739d-180">Catalog view that shows the certificates in a database.</span></span>|
|[<span data-ttu-id="a739d-181">sys.dm_database_encryption_keys &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="a739d-181">sys.dm_database_encryption_keys &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-database-encryption-keys-transact-sql)|<span data-ttu-id="a739d-182">提供了用於資料庫之加密金鑰及資料庫之加密狀態相關資訊的動態管理檢視。</span><span class="sxs-lookup"><span data-stu-id="a739d-182">Dynamic management view that provides information about the encryption keys used in a database, and the state of encryption of a database.</span></span>|

## <a name="permissions"></a><span data-ttu-id="a739d-183">權限</span><span class="sxs-lookup"><span data-stu-id="a739d-183">Permissions</span></span>
 <span data-ttu-id="a739d-184">TDE 的每一項功能和命令都有個別的權限需求，如同之前所示的表格所述。</span><span class="sxs-lookup"><span data-stu-id="a739d-184">Each TDE feature and command has individual permission requirements, described in the tables shown earlier.</span></span>

 <span data-ttu-id="a739d-185">檢視與 TDE 有關的中繼資料將需要憑證的 VIEW DEFINITION 權限。</span><span class="sxs-lookup"><span data-stu-id="a739d-185">Viewing the metadata involved with TDE requires the VIEW DEFINITION permission on the certificate.</span></span>

## <a name="considerations"></a><span data-ttu-id="a739d-186">考量</span><span class="sxs-lookup"><span data-stu-id="a739d-186">Considerations</span></span>
 <span data-ttu-id="a739d-187">當資料庫加密作業的重新加密掃描正在進行時，對資料庫的維護作業將會停用。</span><span class="sxs-lookup"><span data-stu-id="a739d-187">While a re-encryption scan for a database encryption operation is in progress, maintenance operations to the database are disabled.</span></span> <span data-ttu-id="a739d-188">您可以使用資料庫的單一使用者模式設定來執行維護作業。</span><span class="sxs-lookup"><span data-stu-id="a739d-188">You can use the single user mode setting for the database to perform the maintenance operation.</span></span> <span data-ttu-id="a739d-189">如需詳細資訊，請參閱 [將資料庫設定為單一使用者模式](../../databases/set-a-database-to-single-user-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="a739d-189">For more information, see [Set a Database to Single-user Mode](../../databases/set-a-database-to-single-user-mode.md).</span></span>

 <span data-ttu-id="a739d-190">您可以使用 sys.dm_database_encryption_keys 動態管理檢視來尋找資料庫加密的狀態。</span><span class="sxs-lookup"><span data-stu-id="a739d-190">You can find the state of the database encryption using the sys.dm_database_encryption_keys dynamic management view.</span></span> <span data-ttu-id="a739d-191">如需詳細資訊，請參閱本主題前面的＜目錄檢視和動態管理檢視＞一節。</span><span class="sxs-lookup"><span data-stu-id="a739d-191">For more information, see the "Catalog Views and Dynamic Management Views"section earlier in this topic).</span></span>

 <span data-ttu-id="a739d-192">在 TDE 中，資料庫內的所有檔案和檔案群組都會加密。</span><span class="sxs-lookup"><span data-stu-id="a739d-192">In TDE, all files and filegroups in the database are encrypted.</span></span> <span data-ttu-id="a739d-193">如果資料庫內有任何檔案群組標示為 READ ONLY，則資料庫加密作業將會失敗。</span><span class="sxs-lookup"><span data-stu-id="a739d-193">If any filegroups in a database are marked READ ONLY, the database encryption operation will fail.</span></span>

 <span data-ttu-id="a739d-194">如果在資料庫鏡像或記錄傳送中使用資料庫，這兩個資料庫都會加密。</span><span class="sxs-lookup"><span data-stu-id="a739d-194">If a database is being used in database mirroring or log shipping, both databases will be encrypted.</span></span> <span data-ttu-id="a739d-195">記錄交易在這兩者之間傳送時將會加密。</span><span class="sxs-lookup"><span data-stu-id="a739d-195">The log transactions will be encrypted when sent between them.</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="a739d-196">當設定資料庫進行加密時，所有新的全文檢索索引都會加密。</span><span class="sxs-lookup"><span data-stu-id="a739d-196">Any new full-text indexes will be encrypted when a database is set for encryption.</span></span> <span data-ttu-id="a739d-197">之前建立的全文檢索索引將會在升級期間匯入，而且一旦資料載入 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]之後，這些索引將會使用 TDE。</span><span class="sxs-lookup"><span data-stu-id="a739d-197">Previously-created full-text indexes will be imported during upgrade and they will be in TDE after the data is loaded into [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="a739d-198">在資料行上啟用全文檢索索引會造成該資料行的資料在全文檢索索引掃描期間，以純文字格式寫入磁碟上。</span><span class="sxs-lookup"><span data-stu-id="a739d-198">Enabling a full-text index on a column can cause that column's data to be written in plain text onto the disk during a full-text indexing scan.</span></span> <span data-ttu-id="a739d-199">我們建議您不要在敏感性加密資料上建立全文檢索索引。</span><span class="sxs-lookup"><span data-stu-id="a739d-199">We recommend that you do not create a full-text index on sensitive encrypted data.</span></span>

 <span data-ttu-id="a739d-200">加密資料的壓縮比大幅低於對等的未加密資料。</span><span class="sxs-lookup"><span data-stu-id="a739d-200">Encrypted data compresses significantly less than equivalent unencrypted data.</span></span> <span data-ttu-id="a739d-201">如果使用 TDE 來加密資料庫，則備份壓縮將無法大幅壓縮備份儲存體。</span><span class="sxs-lookup"><span data-stu-id="a739d-201">If TDE is used to encrypt a database, backup compression will not be able to significantly compress the backup storage.</span></span> <span data-ttu-id="a739d-202">因此，不建議您同時使用 TDE 與備份壓縮。</span><span class="sxs-lookup"><span data-stu-id="a739d-202">Therefore, using TDE and backup compression together is not recommended.</span></span>

### <a name="restrictions"></a><span data-ttu-id="a739d-203">限制</span><span class="sxs-lookup"><span data-stu-id="a739d-203">Restrictions</span></span>
 <span data-ttu-id="a739d-204">在初始資料庫加密、金鑰變更或資料庫解密期間，不允許以下作業：</span><span class="sxs-lookup"><span data-stu-id="a739d-204">The following operations are not allowed during initial database encryption, key change, or database decryption:</span></span>

-   <span data-ttu-id="a739d-205">從資料庫中的檔案群組卸除檔案</span><span class="sxs-lookup"><span data-stu-id="a739d-205">Dropping a file from a filegroup in the database</span></span>

-   <span data-ttu-id="a739d-206">卸除資料庫</span><span class="sxs-lookup"><span data-stu-id="a739d-206">Dropping the database</span></span>

-   <span data-ttu-id="a739d-207">讓資料庫離線</span><span class="sxs-lookup"><span data-stu-id="a739d-207">Taking the database offline</span></span>

-   <span data-ttu-id="a739d-208">卸離資料庫</span><span class="sxs-lookup"><span data-stu-id="a739d-208">Detaching a database</span></span>

-   <span data-ttu-id="a739d-209">將資料庫或檔案群組轉換成 READ ONLY 狀態</span><span class="sxs-lookup"><span data-stu-id="a739d-209">Transitioning a database or filegroup into a READ ONLY state</span></span>

 <span data-ttu-id="a739d-210">在執行 CREATE DATABASE ENCRYPTION KEY、ALTER DATABASE ENCRYPTION KEY、DROP DATABASE ENCRYPTION KEY 或 ALTER DATABASE...SET ENCRYPTION 陳述式期間，不允許下列作業。</span><span class="sxs-lookup"><span data-stu-id="a739d-210">The following operations are not allowed during the CREATE DATABASE ENCRYPTION KEY, ALTER DATABASE ENCRYPTION KEY, DROP DATABASE ENCRYPTION KEY, or ALTER DATABASE...SET ENCRYPTION statements.</span></span>

-   <span data-ttu-id="a739d-211">從資料庫中的檔案群組卸除檔案。</span><span class="sxs-lookup"><span data-stu-id="a739d-211">Dropping a file from a filegroup in the database.</span></span>

-   <span data-ttu-id="a739d-212">卸除資料庫。</span><span class="sxs-lookup"><span data-stu-id="a739d-212">Dropping the database.</span></span>

-   <span data-ttu-id="a739d-213">讓資料庫離線。</span><span class="sxs-lookup"><span data-stu-id="a739d-213">Taking the database offline.</span></span>

-   <span data-ttu-id="a739d-214">卸離資料庫。</span><span class="sxs-lookup"><span data-stu-id="a739d-214">Detaching a database.</span></span>

-   <span data-ttu-id="a739d-215">將資料庫或檔案群組轉換成 READ ONLY 狀態。</span><span class="sxs-lookup"><span data-stu-id="a739d-215">Transitioning a database or filegroup into a READ ONLY state.</span></span>

-   <span data-ttu-id="a739d-216">使用 ALTER DATABASE 命令。</span><span class="sxs-lookup"><span data-stu-id="a739d-216">Using an ALTER DATABASE command.</span></span>

-   <span data-ttu-id="a739d-217">啟動資料庫或資料庫檔案備份。</span><span class="sxs-lookup"><span data-stu-id="a739d-217">Starting a database or database file backup.</span></span>

-   <span data-ttu-id="a739d-218">啟動資料庫或資料庫檔案還原。</span><span class="sxs-lookup"><span data-stu-id="a739d-218">Starting a database or database file restore.</span></span>

-   <span data-ttu-id="a739d-219">建立快照集。</span><span class="sxs-lookup"><span data-stu-id="a739d-219">Creating a snapshot.</span></span>

 <span data-ttu-id="a739d-220">下列作業或條件會讓 CREATE DATABASE ENCRYPTION KEY、ALTER DATABASE ENCRYPTION KEY、DROP DATABASE ENCRYPTION KEY 或 ALTER DATABASE...SET ENCRYPTION 陳述式無法執行。</span><span class="sxs-lookup"><span data-stu-id="a739d-220">The following operations or conditions will prevent the CREATE DATABASE ENCRYPTION KEY, ALTER DATABASE ENCRYPTION KEY, DROP DATABASE ENCRYPTION KEY, or ALTER DATABASE...SET ENCRYPTION statements.</span></span>

-   <span data-ttu-id="a739d-221">資料庫是唯讀的，或是具有任何唯讀的檔案群組。</span><span class="sxs-lookup"><span data-stu-id="a739d-221">The database is read-only or has any read-only file groups.</span></span>

-   <span data-ttu-id="a739d-222">正在執行 ALTER DATABASE 命令。</span><span class="sxs-lookup"><span data-stu-id="a739d-222">An ALTER DATABASE command is executing.</span></span>

-   <span data-ttu-id="a739d-223">正在執行任何資料備份。</span><span class="sxs-lookup"><span data-stu-id="a739d-223">Any data backup is running.</span></span>

-   <span data-ttu-id="a739d-224">資料庫處於離線或還原狀況。</span><span class="sxs-lookup"><span data-stu-id="a739d-224">The database is in an offline or restore condition.</span></span>

-   <span data-ttu-id="a739d-225">快照集正在進行中。</span><span class="sxs-lookup"><span data-stu-id="a739d-225">A snapshot is in progress.</span></span>

-   <span data-ttu-id="a739d-226">資料庫維護工作。</span><span class="sxs-lookup"><span data-stu-id="a739d-226">Database maintenance tasks.</span></span>

 <span data-ttu-id="a739d-227">在建立資料庫檔案時，啟用 TDE 時無法使用立即檔案初始化功能。</span><span class="sxs-lookup"><span data-stu-id="a739d-227">When creating database files, instant file initialization is not available when TDE is enabled.</span></span>

 <span data-ttu-id="a739d-228">為了利用非對稱金鑰加密資料庫加密金鑰，非對稱金鑰必須位在可延伸金鑰管理提供者上。</span><span class="sxs-lookup"><span data-stu-id="a739d-228">In order to encrypt the database encryption key with an asymmetric key, the asymmetric key must reside on an extensible key management provider.</span></span>

### <a name="transparent-data-encryption-and-transaction-logs"></a><span data-ttu-id="a739d-229">透明資料加密和交易記錄</span><span class="sxs-lookup"><span data-stu-id="a739d-229">Transparent Data Encryption and Transaction Logs</span></span>
 <span data-ttu-id="a739d-230">讓資料庫使用 TDE 會產生讓虛擬交易記錄的其餘部分歸零的結果，以強制使用下一個虛擬交易記錄。</span><span class="sxs-lookup"><span data-stu-id="a739d-230">Enabling a database to use TDE has the effect of "zeroing out" the remaining part of the virtual transaction log to force the next virtual transaction log.</span></span> <span data-ttu-id="a739d-231">這樣可確保在設定資料庫進行加密之後，交易記錄中不會留下任何純文字。</span><span class="sxs-lookup"><span data-stu-id="a739d-231">This guarantees that no clear text is left in the transaction logs after the database is set for encryption.</span></span> <span data-ttu-id="a739d-232">您可以尋找記錄檔加密的狀態，其方式是檢視 `encryption_state` 檢視中的 `sys.dm_database_encryption_keys` 資料行，如以下範例所示：</span><span class="sxs-lookup"><span data-stu-id="a739d-232">You can find the status of the log file encryption by viewing the `encryption_state` column in the `sys.dm_database_encryption_keys` view, as in this example:</span></span>

```
USE AdventureWorks2012;
GO
/* The value 3 represents an encrypted state 
   on the database and transaction logs. */
SELECT *
FROM sys.dm_database_encryption_keys
WHERE encryption_state = 3;
GO
```

 <span data-ttu-id="a739d-233">如需 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 記錄檔架構的詳細資訊，請參閱 [&#40;SQL Server&#41;](../../logs/the-transaction-log-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="a739d-233">For more information about the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] log file architecture, see [The Transaction Log &#40;SQL Server&#41;](../../logs/the-transaction-log-sql-server.md).</span></span>

 <span data-ttu-id="a739d-234">在資料庫加密金鑰變更之前寫入交易記錄的所有資料，都會使用之前的資料庫加密金鑰進行加密。</span><span class="sxs-lookup"><span data-stu-id="a739d-234">All data written to the transaction log before a change in the database encryption key will be encrypted by using the previous database encryption key.</span></span>

 <span data-ttu-id="a739d-235">當資料庫加密金鑰已經修改兩次之後，您就必須先執行記錄備份，然後才能再次修改資料庫加密金鑰。</span><span class="sxs-lookup"><span data-stu-id="a739d-235">After a database encryption key has been modified twice, a log backup must be performed before the database encryption key can be modified again.</span></span>

### <a name="transparent-data-encryption-and-the-tempdb-system-database"></a><span data-ttu-id="a739d-236">透明資料加密和 tempdb 系統資料庫</span><span class="sxs-lookup"><span data-stu-id="a739d-236">Transparent Data Encryption and the tempdb System Database</span></span>
 <span data-ttu-id="a739d-237">如果 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體上的任何其他資料庫是使用 TDE 進行加密，則 tempdb 系統資料庫將會加密。</span><span class="sxs-lookup"><span data-stu-id="a739d-237">The tempdb system database will be encrypted if any other database on the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] is encrypted by using TDE.</span></span> <span data-ttu-id="a739d-238">這可能會對於相同 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]執行個體上未加密的資料庫造成效能上的影響。</span><span class="sxs-lookup"><span data-stu-id="a739d-238">This might have a performance effect for unencrypted databases on the same instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="a739d-239">如需 tempdb 系統資料庫的詳細資訊，請參閱 [tempdb 資料庫](../../databases/tempdb-database.md)。</span><span class="sxs-lookup"><span data-stu-id="a739d-239">For more information about the tempdb system database, see [tempdb Database](../../databases/tempdb-database.md).</span></span>

### <a name="transparent-data-encryption-and-replication"></a><span data-ttu-id="a739d-240">透明資料加密和複寫</span><span class="sxs-lookup"><span data-stu-id="a739d-240">Transparent Data Encryption and Replication</span></span>
 <span data-ttu-id="a739d-241">複寫不會自動使用加密形式來複寫啟用 TDE 之資料庫內的資料。</span><span class="sxs-lookup"><span data-stu-id="a739d-241">Replication does not automatically replicate data from a TDE-enabled database in an encrypted form.</span></span> <span data-ttu-id="a739d-242">如果您想要保護散發資料庫和訂閱者資料庫，必須個別啟用 TDE。</span><span class="sxs-lookup"><span data-stu-id="a739d-242">You must separately enable TDE if you want to protect the distribution and subscriber databases.</span></span> <span data-ttu-id="a739d-243">快照式複寫及異動複寫和合併式複寫之資料的初始散發都可以將資料儲存在未加密的中繼檔案中，例如 bcp 檔案。</span><span class="sxs-lookup"><span data-stu-id="a739d-243">Snapshot replication, as well as the initial distribution of data for transactional and merge replication, can store data in unencrypted intermediate files; for example, the bcp files.</span></span>  <span data-ttu-id="a739d-244">在異動複寫或合併式複寫期間，可以啟用加密來保護通訊通道。</span><span class="sxs-lookup"><span data-stu-id="a739d-244">During transactional or merge replication, encryption can be enabled to protect the communication channel.</span></span> <span data-ttu-id="a739d-245">如需詳細資訊，請參閱[啟用 Database Engine 的加密連接 &#40;SQL Server 組態管理員&#41;](../../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md)。</span><span class="sxs-lookup"><span data-stu-id="a739d-245">For more information, see [Enable Encrypted Connections to the Database Engine &#40;SQL Server Configuration Manager&#41;](../../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md).</span></span>

### <a name="transparent-data-encryption-and-filestream-data"></a><span data-ttu-id="a739d-246">透明資料加密和 FILESTREAM DATA</span><span class="sxs-lookup"><span data-stu-id="a739d-246">Transparent Data Encryption and FILESTREAM DATA</span></span>
 <span data-ttu-id="a739d-247">即使啟用了 TDE，FILESTREAM 資料也不會加密。</span><span class="sxs-lookup"><span data-stu-id="a739d-247">FILESTREAM data is not encrypted even when TDE is enabled.</span></span>

### <a name="transparent-data-encryption-and-buffer-pool-extension"></a><span data-ttu-id="a739d-248">透明資料加密和緩衝集區擴充</span><span class="sxs-lookup"><span data-stu-id="a739d-248">Transparent Data Encryption and Buffer Pool Extension</span></span>
 <span data-ttu-id="a739d-249">使用 TDE 將資料庫加密時，與緩衝集區擴充 (BPE) 相關的檔案未受到加密。</span><span class="sxs-lookup"><span data-stu-id="a739d-249">Files related to buffer pool extension (BPE) are not encrypted when database is encrypted using TDE.</span></span> <span data-ttu-id="a739d-250">您必須針對 BPE 相關檔案使用 Bitlocker 或 EFS 等檔案系統層級加密工具。</span><span class="sxs-lookup"><span data-stu-id="a739d-250">You must use file system level encryption tools like Bitlocker or EFS for BPE related files.</span></span>

## <a name="transparent-data-encryption-and-in-memory-oltp"></a><span data-ttu-id="a739d-251">透明資料加密和記憶體中 OLTP</span><span class="sxs-lookup"><span data-stu-id="a739d-251">Transparent Data Encryption and In-Memory OLTP</span></span>
 <span data-ttu-id="a739d-252">TDE 可在具有記憶體中 OLTP 物件的資料庫上啟用。</span><span class="sxs-lookup"><span data-stu-id="a739d-252">TDE can be enabled on a database that has In-Memory OLTP objects.</span></span> <span data-ttu-id="a739d-253">如果啟用 TDE，則會加密記憶體中 OLTP 記錄。</span><span class="sxs-lookup"><span data-stu-id="a739d-253">In-Memory OLTP log records are encrypted if TDE is enabled.</span></span> <span data-ttu-id="a739d-254">啟用 TDE 時，並不會加密 MEMORY_OPTIMIZED_DATA 檔案群組中的資料。</span><span class="sxs-lookup"><span data-stu-id="a739d-254">Data in a MEMORY_OPTIMIZED_DATA filegroup is not encrypted if TDE is enabled.</span></span>

## <a name="see-also"></a><span data-ttu-id="a739d-255">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a739d-255">See Also</span></span>
 <span data-ttu-id="a739d-256">[將 TDE 保護的資料庫移至另一個 SQL Server](move-a-tde-protected-database-to-another-sql-server.md) [使用 EKM](enable-tde-on-sql-server-using-ekm.md) [透明資料加密 Azure SQL Database](../../../database-engine/transparent-data-encryption-with-azure-sql-database.md) [SQL Server 加密](sql-server-encryption.md) [SQL Server 和資料庫加密金鑰 &#40;](sql-server-and-database-encryption-keys-database-engine.md)資料庫引擎&#41;資訊安全中心 SQL Server 資料庫引擎和[Azure SQL Database](../security-center-for-sql-server-database-engine-and-azure-sql-database.md) [FILESTREAM &#40;](../../blob/filestream-sql-server.md) SQL Server&#41;，以啟用 TDE</span><span class="sxs-lookup"><span data-stu-id="a739d-256">[Move a TDE Protected Database to Another SQL Server](move-a-tde-protected-database-to-another-sql-server.md) [Enable TDE Using EKM](enable-tde-on-sql-server-using-ekm.md) [Transparent Data Encryption with Azure SQL Database](../../../database-engine/transparent-data-encryption-with-azure-sql-database.md) [SQL Server Encryption](sql-server-encryption.md) [SQL Server and Database Encryption Keys &#40;Database Engine&#41;](sql-server-and-database-encryption-keys-database-engine.md) [Security Center for SQL Server Database Engine and Azure SQL Database](../security-center-for-sql-server-database-engine-and-azure-sql-database.md) [FILESTREAM &#40;SQL Server&#41;](../../blob/filestream-sql-server.md)</span></span>


