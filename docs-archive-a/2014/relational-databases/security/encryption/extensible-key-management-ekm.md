---
title: 可延伸金鑰管理 (EKM) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Key Management
- Extensible Key Management
- EKM, described
ms.assetid: 9bfaf500-2d1e-4c02-b041-b8761a9e695b
author: jaszymas
ms.author: jaszymas
ms.openlocfilehash: 4fc9b002b57f8118494709f8fe27a8b19ce28d8e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87700936"
---
# <a name="extensible-key-management-ekm"></a><span data-ttu-id="8f3b5-102">可延伸金鑰管理 (EKM)</span><span class="sxs-lookup"><span data-stu-id="8f3b5-102">Extensible Key Management (EKM)</span></span>
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="8f3b5-103">會針對加密和金鑰產生使用「Microsoft 密碼編譯 API」(MSCAPI) 提供者，藉以提供加密功能以及「可延伸金鑰管理」(EKM)。</span><span class="sxs-lookup"><span data-stu-id="8f3b5-103">provides data encryption capabilities together with *Extensible Key Management* (EKM), using the *Microsoft Cryptographic API* (MSCAPI) provider for encryption and key generation.</span></span> <span data-ttu-id="8f3b5-104">用於資料和金鑰加密的加密金鑰會建立於暫時性金鑰容器中，而且您必須先從提供者中匯出這些金鑰，然後再將它們儲存於資料庫中。</span><span class="sxs-lookup"><span data-stu-id="8f3b5-104">Encryption keys for data and key encryption are created in transient key containers, and they must be exported from a provider before they are stored in the database.</span></span> <span data-ttu-id="8f3b5-105">這個方法會讓 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]處理金鑰管理 (包括加密金鑰階層和金鑰備份)。</span><span class="sxs-lookup"><span data-stu-id="8f3b5-105">This approach enables key management that includes an encryption key hierarchy and key backup, to be handled by [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="8f3b5-106">隨著法規相符的需求和資料隱私權的考量逐漸增加，許多組織便運用加密技術來提供「深度防護」解決方案。</span><span class="sxs-lookup"><span data-stu-id="8f3b5-106">With the growing demand for regulatory compliance and concern for data privacy, organizations are taking advantage of encryption as a way to provide a "defense in depth" solution.</span></span> <span data-ttu-id="8f3b5-107">這種方法通常不實用，因為它僅使用資料庫加密管理工具。</span><span class="sxs-lookup"><span data-stu-id="8f3b5-107">This approach is often impractical using only database encryption management tools.</span></span> <span data-ttu-id="8f3b5-108">硬體廠商會提供使用「硬體安全模組」(HSM) 來處理企業金鑰管理的產品。</span><span class="sxs-lookup"><span data-stu-id="8f3b5-108">Hardware vendors provide products that address enterprise key management by using *Hardware Security Modules* (HSM).</span></span> <span data-ttu-id="8f3b5-109">HSM 裝置會將加密金鑰儲存在硬體或軟體模組上。</span><span class="sxs-lookup"><span data-stu-id="8f3b5-109">HSM devices store encryption keys on hardware or software modules.</span></span> <span data-ttu-id="8f3b5-110">這是較安全的解決方案，因為加密金鑰不會與加密資料一起存放。</span><span class="sxs-lookup"><span data-stu-id="8f3b5-110">This is a more secure solution because the encryption keys do not reside with encryption data.</span></span>  
  
 <span data-ttu-id="8f3b5-111">目前許多廠商會針對金鑰管理和加密速度提供 HSM。</span><span class="sxs-lookup"><span data-stu-id="8f3b5-111">A number of vendors offer HSM for both key management and encryption acceleration.</span></span> <span data-ttu-id="8f3b5-112">HSM 裝置會使用硬體介面搭配伺服器處理序，當做應用程式與 HSM 之間的中繼。</span><span class="sxs-lookup"><span data-stu-id="8f3b5-112">HSM devices use hardware interfaces with a server process as an intermediary between an application and an HSM.</span></span> <span data-ttu-id="8f3b5-113">此外，廠商也會在模組 (可能是硬體或軟體) 上實作 MSCAPI 提供者。</span><span class="sxs-lookup"><span data-stu-id="8f3b5-113">Vendors also implement MSCAPI providers over their modules, which might be hardware or software.</span></span> <span data-ttu-id="8f3b5-114">MSCAPI 通常只會提供 HSM 所提供的部分功能。</span><span class="sxs-lookup"><span data-stu-id="8f3b5-114">MSCAPI often offers only a subset of the functionality that is offered by an HSM.</span></span> <span data-ttu-id="8f3b5-115">而且，廠商也可以針對 HSM、金鑰組態和金鑰存取提供管理軟體。</span><span class="sxs-lookup"><span data-stu-id="8f3b5-115">Vendors can also provide management software for HSM, key configuration, and key access.</span></span>  
  
 <span data-ttu-id="8f3b5-116">HSM 實作方式會因廠商而不同，而且若要使用它們搭配 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ，就需要公用介面。</span><span class="sxs-lookup"><span data-stu-id="8f3b5-116">HSM implementations vary from vendor to vendor, and to use them with [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] requires a common interface.</span></span> <span data-ttu-id="8f3b5-117">雖然 MSCAPI 會提供此介面，但是它僅支援部分 HSM 功能。</span><span class="sxs-lookup"><span data-stu-id="8f3b5-117">Although the MSCAPI provides this interface, it supports only a subset of the HSM features.</span></span> <span data-ttu-id="8f3b5-118">此外，它也具有其他限制，例如無法以原生方式保存對稱金鑰，而且缺乏工作階段導向的支援。</span><span class="sxs-lookup"><span data-stu-id="8f3b5-118">It also has other limitations, such as the inability to natively persist symmetric keys, and a lack of session-oriented support.</span></span>  
  
 <span data-ttu-id="8f3b5-119">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 可延伸金鑰管理可讓 EKM/HSM 協力廠商在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]中註冊其模組。</span><span class="sxs-lookup"><span data-stu-id="8f3b5-119">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Extensible Key Management enables third-party EKM/HSM vendors to register their modules in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="8f3b5-120">註冊之後， [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 使用者就可以使用儲存在 EKM 模組上的加密金鑰。</span><span class="sxs-lookup"><span data-stu-id="8f3b5-120">When registered, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] users can use the encryption keys stored on EKM modules.</span></span> <span data-ttu-id="8f3b5-121">這可讓 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 存取這些模組支援的進階加密功能 (例如大量加密和解密) 和金鑰管理函數 (例如金鑰過時和金鑰輪替)。</span><span class="sxs-lookup"><span data-stu-id="8f3b5-121">This enables [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] to access the advanced encryption features these modules support such as bulk encryption and decryption, and key management functions such as key aging and key rotation.</span></span>  
  
 <span data-ttu-id="8f3b5-122">在 Azure VM 中執行 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 時， [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 可以使用儲存在 [Azure 金鑰保存庫](https://go.microsoft.com/fwlink/?LinkId=521401)中的金鑰。</span><span class="sxs-lookup"><span data-stu-id="8f3b5-122">When running [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in an Azure VM, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] can use keys stored in the [Azure Key Vault](https://go.microsoft.com/fwlink/?LinkId=521401).</span></span> <span data-ttu-id="8f3b5-123">如需詳細資訊，請參閱 [使用 Azure 金鑰保存庫進行可延伸金鑰管理 &#40;SQL Server&#41;](extensible-key-management-using-azure-key-vault-sql-server.md)處理金鑰管理 (包括加密金鑰階層和金鑰備份)。</span><span class="sxs-lookup"><span data-stu-id="8f3b5-123">For more information, see [Extensible Key Management Using Azure Key Vault &#40;SQL Server&#41;](extensible-key-management-using-azure-key-vault-sql-server.md).</span></span>  
  
## <a name="ekm-configuration"></a><span data-ttu-id="8f3b5-124">EKM 組態</span><span class="sxs-lookup"><span data-stu-id="8f3b5-124">EKM Configuration</span></span>  
 <span data-ttu-id="8f3b5-125">並非每一個 [!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]版本都可使用可延伸金鑰管理。</span><span class="sxs-lookup"><span data-stu-id="8f3b5-125">Extensible Key Management is not available in every edition of [!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="8f3b5-126">如需版本支援的功能清單 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ，請參閱[SQL Server 2014 版本支援的功能](../../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)。</span><span class="sxs-lookup"><span data-stu-id="8f3b5-126">For a list of features that are supported by the editions of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], see [Features Supported by the Editions of SQL Server 2014](../../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>  
  
 <span data-ttu-id="8f3b5-127">根據預設，可延伸金鑰管理處於關閉狀態。</span><span class="sxs-lookup"><span data-stu-id="8f3b5-127">By default, Extensible Key Management is off.</span></span> <span data-ttu-id="8f3b5-128">若要啟用這項功能，請使用具有下列選項和值的 sp_configure 命令，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="8f3b5-128">To enable this feature, use the sp_configure command that has the following option and value, as in the following example:</span></span>  
  
```  
sp_configure 'show advanced', 1  
GO  
RECONFIGURE  
GO  
sp_configure 'EKM provider enabled', 1  
GO  
RECONFIGURE  
GO  
```  
  
> [!NOTE]  
>  <span data-ttu-id="8f3b5-129">如果您在不支援 EKM 的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 版本上，針對這個選項使用 sp_configure 命令，將會收到錯誤。</span><span class="sxs-lookup"><span data-stu-id="8f3b5-129">If you use the sp_configure command for this option on editions of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] that do not support EKM, you will receive an error.</span></span>  
  
 <span data-ttu-id="8f3b5-130">若要停用此功能，請將值設定為 **0**。</span><span class="sxs-lookup"><span data-stu-id="8f3b5-130">To disable the feature, set the value to **0**.</span></span> <span data-ttu-id="8f3b5-131">如需如何設定伺服器選項的詳細資訊，請參閱 [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="8f3b5-131">For more information about how to set server options, see [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql).</span></span>  
  
## <a name="how-to-use-ekm"></a><span data-ttu-id="8f3b5-132">如何使用 EKM</span><span class="sxs-lookup"><span data-stu-id="8f3b5-132">How to Use EKM</span></span>  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="8f3b5-133">可延伸金鑰管理可讓保護資料庫檔案的加密金鑰儲存在外部裝置中，例如智慧卡、USB 裝置或 EKM/HSM 模組。</span><span class="sxs-lookup"><span data-stu-id="8f3b5-133">Extensible Key Management enables the encryption keys that protect the database files to be stored in an off-box device such as a smartcard, USB device, or EKM/HSM module.</span></span> <span data-ttu-id="8f3b5-134">這也會讓資料庫管理員 (系統管理員群組的成員除外) 能夠保護資料。</span><span class="sxs-lookup"><span data-stu-id="8f3b5-134">This also enables data protection from database administrators (except members of the sysadmin group).</span></span> <span data-ttu-id="8f3b5-135">資料可以使用只有資料庫使用者可在外部 EKM/HSM 模組上存取的加密金鑰進行加密。</span><span class="sxs-lookup"><span data-stu-id="8f3b5-135">Data can be encrypted by using encryption keys that only the database user has access to on the external EKM/HSM module.</span></span>  
  
 <span data-ttu-id="8f3b5-136">可延伸金鑰管理也會提供下列優點：</span><span class="sxs-lookup"><span data-stu-id="8f3b5-136">Extensible Key Management also provides the following benefits:</span></span>  
  
-   <span data-ttu-id="8f3b5-137">額外的授權檢查 (啟用責任分隔)。</span><span class="sxs-lookup"><span data-stu-id="8f3b5-137">Additional authorization check (enabling separation of duties).</span></span>  
  
-   <span data-ttu-id="8f3b5-138">硬體架構加密/解密的效能較高。</span><span class="sxs-lookup"><span data-stu-id="8f3b5-138">Higher performance for hardware-based encryption/decryption.</span></span>  
  
-   <span data-ttu-id="8f3b5-139">外部加密金鑰產生。</span><span class="sxs-lookup"><span data-stu-id="8f3b5-139">External encryption key generation.</span></span>  
  
-   <span data-ttu-id="8f3b5-140">外部加密金鑰儲存 (實體分隔資料和金鑰)。</span><span class="sxs-lookup"><span data-stu-id="8f3b5-140">External encryption key storage (physical separation of data and keys).</span></span>  
  
-   <span data-ttu-id="8f3b5-141">加密金鑰擷取。</span><span class="sxs-lookup"><span data-stu-id="8f3b5-141">Encryption key retrieval.</span></span>  
  
-   <span data-ttu-id="8f3b5-142">外部加密金鑰保留 (啟用加密金鑰循環)。</span><span class="sxs-lookup"><span data-stu-id="8f3b5-142">External encryption key retention (enables encryption key rotation).</span></span>  
  
-   <span data-ttu-id="8f3b5-143">加密金鑰復原更容易。</span><span class="sxs-lookup"><span data-stu-id="8f3b5-143">Easier encryption key recovery.</span></span>  
  
-   <span data-ttu-id="8f3b5-144">可管理的加密金鑰散發。</span><span class="sxs-lookup"><span data-stu-id="8f3b5-144">Manageable encryption key distribution.</span></span>  
  
-   <span data-ttu-id="8f3b5-145">安全的加密金鑰處置。</span><span class="sxs-lookup"><span data-stu-id="8f3b5-145">Secure encryption key disposal.</span></span>  
  
 <span data-ttu-id="8f3b5-146">您可以將可延伸金鑰管理用於使用者名稱和密碼組合，或是 EKM 驅動程式所定義的其他方法。</span><span class="sxs-lookup"><span data-stu-id="8f3b5-146">You can use Extensible Key Management for a username and password combination or other methods defined by the EKM driver.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="8f3b5-147">若要進行疑難排解， [!INCLUDE[msCoName](../../../includes/msconame-md.md)] 技術支援部門可能會需要 EKM 提供者的加密金鑰。</span><span class="sxs-lookup"><span data-stu-id="8f3b5-147">For troubleshooting, [!INCLUDE[msCoName](../../../includes/msconame-md.md)] technical support might require the encryption key from the EKM provider.</span></span> <span data-ttu-id="8f3b5-148">此時，您可能也需要存取廠商工具或處理序來協助解決問題。</span><span class="sxs-lookup"><span data-stu-id="8f3b5-148">You might also need to access vendor tools or processes to help resolve an issue.</span></span>  
  
### <a name="authentication-with-an-ekm-device"></a><span data-ttu-id="8f3b5-149">使用 EKM 裝置進行驗證</span><span class="sxs-lookup"><span data-stu-id="8f3b5-149">Authentication with an EKM Device</span></span>  
 <span data-ttu-id="8f3b5-150">EKM 模組可以支援多種驗證類型。</span><span class="sxs-lookup"><span data-stu-id="8f3b5-150">An EKM module can support more than one type of authentication.</span></span> <span data-ttu-id="8f3b5-151">但是，每個提供者只會公開一種驗證類型給 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]，也就是說，如果此模組支援基本驗證或其他驗證類型，它就會公開其中一種驗證類型，而不會同時公開這兩種。</span><span class="sxs-lookup"><span data-stu-id="8f3b5-151">Each provider exposes only one type of authentication to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], that is if the module supports Basic or Other authentication types, it exposes one or the other, but not both.</span></span>  
  
#### <a name="ekm-device-specific-basic-authentication-using-usernamepassword"></a><span data-ttu-id="8f3b5-152">使用使用者名稱/密碼的 EKM 裝置特有基本驗證</span><span class="sxs-lookup"><span data-stu-id="8f3b5-152">EKM Device-Specific Basic Authentication Using username/password</span></span>  
 <span data-ttu-id="8f3b5-153">對於這些使用「使用者名稱/密碼」配對來支援基本驗證的 EKM 模組而言，[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 會使用認證來提供透明驗證。</span><span class="sxs-lookup"><span data-stu-id="8f3b5-153">For those EKM modules that support Basic authentication using a *username/password* pair, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] provides transparent authentication using credentials.</span></span> <span data-ttu-id="8f3b5-154">如需認證的詳細資訊，請參閱[認證 &#40;Database Engine&#41;](../authentication-access/credentials-database-engine.md)。</span><span class="sxs-lookup"><span data-stu-id="8f3b5-154">For more information about credentials, see [Credentials &#40;Database Engine&#41;](../authentication-access/credentials-database-engine.md).</span></span>  
  
 <span data-ttu-id="8f3b5-155">您可以針對 EKM 提供者建立認證，並將它對應至登入 (Windows 和 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 帳戶)，以便按照登入存取 EKM 模組。</span><span class="sxs-lookup"><span data-stu-id="8f3b5-155">A credential can be created for an EKM provider and mapped to a login (both Windows and [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] accounts) to access an EKM module on per-login basis.</span></span> <span data-ttu-id="8f3b5-156">認證的 [身分識別]\*\* 欄位包含使用者名稱，而 [密碼]\*\* 欄位則包含用來連接至 EKM 模組的密碼。</span><span class="sxs-lookup"><span data-stu-id="8f3b5-156">The *Identify* field of the credential contains the username; the *secret* field contains a password to connect to an EKM module.</span></span>  
  
 <span data-ttu-id="8f3b5-157">如果 EKM 提供者沒有任何登入對應認證，系統就會使用對應至 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 服務帳戶的認證。</span><span class="sxs-lookup"><span data-stu-id="8f3b5-157">If there is no login mapped credential for the EKM provider, the credential mapped to the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] service account is used.</span></span>  
  
 <span data-ttu-id="8f3b5-158">一個登入可以具有多個對應認證，只要這些認證用於不同的 EKM 提供者即可。</span><span class="sxs-lookup"><span data-stu-id="8f3b5-158">A login can have multiple credentials mapped to it, as long as they are used for distinctive EKM providers.</span></span> <span data-ttu-id="8f3b5-159">但是，每個登入的每個 EKM 提供者必須只有一個對應認證。</span><span class="sxs-lookup"><span data-stu-id="8f3b5-159">There must be only one mapped credential per EKM provider per login.</span></span> <span data-ttu-id="8f3b5-160">相同的認證可對應至其他登入。</span><span class="sxs-lookup"><span data-stu-id="8f3b5-160">The same credential can be mapped to other logins.</span></span>  
  
#### <a name="other-types-of-ekm-device-specific-authentication"></a><span data-ttu-id="8f3b5-161">其他 EKM 裝置特有的驗證類型</span><span class="sxs-lookup"><span data-stu-id="8f3b5-161">Other Types of EKM Device-Specific Authentication</span></span>  
 <span data-ttu-id="8f3b5-162">對於具有 Windows 或「使用者/密碼」組合以外驗證的 EKM 模組而言，就必須獨立於 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 以外執行驗證。</span><span class="sxs-lookup"><span data-stu-id="8f3b5-162">For EKM modules that have authentication other than Windows or *user/password* combinations, authentication must be performed independently from [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
### <a name="encryption-and-decryption-by-an-ekm-device"></a><span data-ttu-id="8f3b5-163">EKM 裝置的加密和解密</span><span class="sxs-lookup"><span data-stu-id="8f3b5-163">Encryption and Decryption by an EKM Device</span></span>  
 <span data-ttu-id="8f3b5-164">您可以使用下列函數和功能搭配對稱與非對稱金鑰，加密和解密資料：</span><span class="sxs-lookup"><span data-stu-id="8f3b5-164">You can use the following functions and features to encrypt and decrypt data by using symmetric and asymmetric keys:</span></span>  
  
|<span data-ttu-id="8f3b5-165">函數或功能</span><span class="sxs-lookup"><span data-stu-id="8f3b5-165">Function or feature</span></span>|<span data-ttu-id="8f3b5-166">參考</span><span class="sxs-lookup"><span data-stu-id="8f3b5-166">Reference</span></span>|  
|-------------------------|---------------|  
|<span data-ttu-id="8f3b5-167">對稱金鑰加密</span><span class="sxs-lookup"><span data-stu-id="8f3b5-167">Symmetric key encryption</span></span>|[<span data-ttu-id="8f3b5-168">CREATE SYMMETRIC KEY &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="8f3b5-168">CREATE SYMMETRIC KEY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-symmetric-key-transact-sql)|  
|<span data-ttu-id="8f3b5-169">非對稱金鑰加密</span><span class="sxs-lookup"><span data-stu-id="8f3b5-169">Asymmetric Key encryption</span></span>|[<span data-ttu-id="8f3b5-170">CREATE ASYMMETRIC KEY &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="8f3b5-170">CREATE ASYMMETRIC KEY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-asymmetric-key-transact-sql)|  
|<span data-ttu-id="8f3b5-171">EncryptByKey(key_guid, '純文字', ...)</span><span class="sxs-lookup"><span data-stu-id="8f3b5-171">EncryptByKey(key_guid, 'cleartext', ...)</span></span>|[<span data-ttu-id="8f3b5-172">ENCRYPTBYKEY &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="8f3b5-172">ENCRYPTBYKEY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/encryptbykey-transact-sql)|  
|<span data-ttu-id="8f3b5-173">DecryptByKey(加密文字, ...)</span><span class="sxs-lookup"><span data-stu-id="8f3b5-173">DecryptByKey(ciphertext, ...)</span></span>|[<span data-ttu-id="8f3b5-174">DECRYPTBYKEY &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="8f3b5-174">DECRYPTBYKEY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/decryptbykey-transact-sql)|  
|<span data-ttu-id="8f3b5-175">EncryptByAsmKey(key_guid, 'cleartext')</span><span class="sxs-lookup"><span data-stu-id="8f3b5-175">EncryptByAsmKey(key_guid, 'cleartext')</span></span>|[<span data-ttu-id="8f3b5-176">ENCRYPTBYASYMKEY &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="8f3b5-176">ENCRYPTBYASYMKEY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/encryptbyasymkey-transact-sql)|  
|<span data-ttu-id="8f3b5-177">DecryptByAsmKey(ciphertext)</span><span class="sxs-lookup"><span data-stu-id="8f3b5-177">DecryptByAsmKey(ciphertext)</span></span>|[<span data-ttu-id="8f3b5-178">DECRYPTBYASYMKEY &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="8f3b5-178">DECRYPTBYASYMKEY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/decryptbyasymkey-transact-sql)|  
  
#### <a name="database-keys-encryption-by-ekm-keys"></a><span data-ttu-id="8f3b5-179">EKM 金鑰的資料庫金鑰加密</span><span class="sxs-lookup"><span data-stu-id="8f3b5-179">Database Keys Encryption by EKM Keys</span></span>  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="8f3b5-180">可以使用 EKM 金鑰來加密資料庫中的其他金鑰。</span><span class="sxs-lookup"><span data-stu-id="8f3b5-180">can use EKM keys to encrypt other keys in a database.</span></span> <span data-ttu-id="8f3b5-181">您可以在 EKM 裝置上建立及使用對稱和非對稱金鑰。</span><span class="sxs-lookup"><span data-stu-id="8f3b5-181">You can create and use both symmetric and asymmetric keys on an EKM device.</span></span> <span data-ttu-id="8f3b5-182">您可以使用 EKM 非對稱金鑰來加密原生 (非 EKM) 對稱金鑰。</span><span class="sxs-lookup"><span data-stu-id="8f3b5-182">You can encrypt native (non-EKM) symmetric keys with EKM asymmetric keys.</span></span>  
  
 <span data-ttu-id="8f3b5-183">下列範例會建立資料庫對稱金鑰，然後使用 EKM 模組上的金鑰來加密該資料庫對稱金鑰。</span><span class="sxs-lookup"><span data-stu-id="8f3b5-183">The following example creates a database symmetric key and encrypts it using a key on an EKM module.</span></span>  
  
```  
CREATE SYMMETRIC KEY Key1  
WITH ALGORITHM = AES_256  
ENCRYPTION BY EKM_AKey1;  
GO  
--Open database key  
OPEN SYMMETRIC KEY Key1  
DECRYPTION BY EKM_AKey1  
```  
  
 <span data-ttu-id="8f3b5-184">如需 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 中資料庫和伺服器金鑰的詳細資訊，請參閱 [SQL Server 和資料庫加密金鑰 &#40;Database Engine&#41;](sql-server-and-database-encryption-keys-database-engine.md)。</span><span class="sxs-lookup"><span data-stu-id="8f3b5-184">For more information about Database and Server Keys in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], see [SQL Server and Database Encryption Keys &#40;Database Engine&#41;](sql-server-and-database-encryption-keys-database-engine.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8f3b5-185">您無法使用某個 EKM 金鑰來加密另一個 EKM 金鑰。</span><span class="sxs-lookup"><span data-stu-id="8f3b5-185">You cannot encrypt one EKM key with another EKM key.</span></span>  
>   
>  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="8f3b5-186">不支援使用 EKM 提供者產生的非對稱金鑰來簽署模組。</span><span class="sxs-lookup"><span data-stu-id="8f3b5-186">does not support signing modules with asymmetric keys generated from EKM provider.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="8f3b5-187">相關工作</span><span class="sxs-lookup"><span data-stu-id="8f3b5-187">Related Tasks</span></span>  
 [<span data-ttu-id="8f3b5-188">EKM provider enabled 伺服器組態選項</span><span class="sxs-lookup"><span data-stu-id="8f3b5-188">EKM provider enabled Server Configuration Option</span></span>](../../../database-engine/configure-windows/ekm-provider-enabled-server-configuration-option.md)  
  
 [<span data-ttu-id="8f3b5-189">使用 EKM 啟用 TDE</span><span class="sxs-lookup"><span data-stu-id="8f3b5-189">Enable TDE Using EKM</span></span>](enable-tde-on-sql-server-using-ekm.md)  
  
 [<span data-ttu-id="8f3b5-190">使用 Azure 金鑰保存庫進行可延伸金鑰管理 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="8f3b5-190">Extensible Key Management Using Azure Key Vault &#40;SQL Server&#41;</span></span>](extensible-key-management-using-azure-key-vault-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="8f3b5-191">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8f3b5-191">See Also</span></span>  
 <span data-ttu-id="8f3b5-192">[CREATE CRYPTOGRAPHIC PROVIDER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-cryptographic-provider-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="8f3b5-192">[CREATE CRYPTOGRAPHIC PROVIDER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-cryptographic-provider-transact-sql) </span></span>  
 <span data-ttu-id="8f3b5-193">[DROP CRYPTOGRAPHIC PROVIDER &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-cryptographic-provider-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="8f3b5-193">[DROP CRYPTOGRAPHIC PROVIDER &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-cryptographic-provider-transact-sql) </span></span>  
 <span data-ttu-id="8f3b5-194">[ALTER CRYPTOGRAPHIC PROVIDER &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-cryptographic-provider-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="8f3b5-194">[ALTER CRYPTOGRAPHIC PROVIDER &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-cryptographic-provider-transact-sql) </span></span>  
 <span data-ttu-id="8f3b5-195">[sys.cryptographic_providers &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-cryptographic-providers-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="8f3b5-195">[sys.cryptographic_providers &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-cryptographic-providers-transact-sql) </span></span>  
 <span data-ttu-id="8f3b5-196">[sys.dm_cryptographic_provider_sessions &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-cryptographic-provider-sessions-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="8f3b5-196">[sys.dm_cryptographic_provider_sessions &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-cryptographic-provider-sessions-transact-sql) </span></span>  
 <span data-ttu-id="8f3b5-197">[sys.dm_cryptographic_provider_properties &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-cryptographic-provider-properties-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="8f3b5-197">[sys.dm_cryptographic_provider_properties &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-cryptographic-provider-properties-transact-sql) </span></span>  
 <span data-ttu-id="8f3b5-198">[sys.dm_cryptographic_provider_algorithms &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-cryptographic-provider-algorithms-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="8f3b5-198">[sys.dm_cryptographic_provider_algorithms &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-cryptographic-provider-algorithms-transact-sql) </span></span>  
 <span data-ttu-id="8f3b5-199">[sys.dm_cryptographic_provider_keys &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-cryptographic-provider-keys-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="8f3b5-199">[sys.dm_cryptographic_provider_keys &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-cryptographic-provider-keys-transact-sql) </span></span>  
 <span data-ttu-id="8f3b5-200">[sys.credentials &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-credentials-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="8f3b5-200">[sys.credentials &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-credentials-transact-sql) </span></span>  
 <span data-ttu-id="8f3b5-201">[CREATE CREDENTIAL &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-credential-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="8f3b5-201">[CREATE CREDENTIAL &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-credential-transact-sql) </span></span>  
 <span data-ttu-id="8f3b5-202">[ALTER LOGIN &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-login-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="8f3b5-202">[ALTER LOGIN &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-login-transact-sql) </span></span>  
 <span data-ttu-id="8f3b5-203">[CREATE ASYMMETRIC KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-asymmetric-key-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="8f3b5-203">[CREATE ASYMMETRIC KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-asymmetric-key-transact-sql) </span></span>  
 <span data-ttu-id="8f3b5-204">[ALTER ASYMMETRIC KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-asymmetric-key-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="8f3b5-204">[ALTER ASYMMETRIC KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-asymmetric-key-transact-sql) </span></span>  
 <span data-ttu-id="8f3b5-205">[DROP ASYMMETRIC KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-asymmetric-key-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="8f3b5-205">[DROP ASYMMETRIC KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-asymmetric-key-transact-sql) </span></span>  
 <span data-ttu-id="8f3b5-206">[CREATE SYMMETRIC KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-symmetric-key-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="8f3b5-206">[CREATE SYMMETRIC KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-symmetric-key-transact-sql) </span></span>  
 <span data-ttu-id="8f3b5-207">[ALTER SYMMETRIC KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-symmetric-key-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="8f3b5-207">[ALTER SYMMETRIC KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-symmetric-key-transact-sql) </span></span>  
 <span data-ttu-id="8f3b5-208">[DROP SYMMETRIC KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-symmetric-key-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="8f3b5-208">[DROP SYMMETRIC KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-symmetric-key-transact-sql) </span></span>  
 <span data-ttu-id="8f3b5-209">[OPEN SYMMETRIC KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/open-symmetric-key-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="8f3b5-209">[OPEN SYMMETRIC KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/open-symmetric-key-transact-sql) </span></span>  
 <span data-ttu-id="8f3b5-210">[備份與還原 Reporting Services 加密金鑰](../../../reporting-services/install-windows/ssrs-encryption-keys-back-up-and-restore-encryption-keys.md) </span><span class="sxs-lookup"><span data-stu-id="8f3b5-210">[Back Up and Restore Reporting Services Encryption Keys](../../../reporting-services/install-windows/ssrs-encryption-keys-back-up-and-restore-encryption-keys.md) </span></span>  
 <span data-ttu-id="8f3b5-211">[刪除和重新建立加密金鑰 &#40;SSRS 組態管理員&#41;](../../../reporting-services/install-windows/ssrs-encryption-keys-delete-and-re-create-encryption-keys.md) </span><span class="sxs-lookup"><span data-stu-id="8f3b5-211">[Delete and Re-create Encryption Keys  &#40;SSRS Configuration Manager&#41;](../../../reporting-services/install-windows/ssrs-encryption-keys-delete-and-re-create-encryption-keys.md) </span></span>  
 <span data-ttu-id="8f3b5-212">[加入和移除向外延展部署的加密金鑰 &#40;SSRS 組態管理員&#41;](../../../reporting-services/install-windows/add-and-remove-encryption-keys-for-scale-out-deployment.md) </span><span class="sxs-lookup"><span data-stu-id="8f3b5-212">[Add and Remove Encryption Keys for Scale-Out Deployment &#40;SSRS Configuration Manager&#41;](../../../reporting-services/install-windows/add-and-remove-encryption-keys-for-scale-out-deployment.md) </span></span>  
 <span data-ttu-id="8f3b5-213">[備份服務主要金鑰](service-master-key.md) </span><span class="sxs-lookup"><span data-stu-id="8f3b5-213">[Back Up the Service Master Key](service-master-key.md) </span></span>  
 <span data-ttu-id="8f3b5-214">[還原服務主要金鑰](restore-the-service-master-key.md) </span><span class="sxs-lookup"><span data-stu-id="8f3b5-214">[Restore the Service Master Key](restore-the-service-master-key.md) </span></span>  
 <span data-ttu-id="8f3b5-215">[建立資料庫主要金鑰](create-a-database-master-key.md) </span><span class="sxs-lookup"><span data-stu-id="8f3b5-215">[Create a Database Master Key](create-a-database-master-key.md) </span></span>  
 <span data-ttu-id="8f3b5-216">[備份資料庫主要金鑰](back-up-a-database-master-key.md) </span><span class="sxs-lookup"><span data-stu-id="8f3b5-216">[Back Up a Database Master Key](back-up-a-database-master-key.md) </span></span>  
 <span data-ttu-id="8f3b5-217">[還原資料庫主要金鑰](restore-a-database-master-key.md) </span><span class="sxs-lookup"><span data-stu-id="8f3b5-217">[Restore a Database Master Key](restore-a-database-master-key.md) </span></span>  
 [<span data-ttu-id="8f3b5-218">在兩部伺服器上建立相同的對稱金鑰</span><span class="sxs-lookup"><span data-stu-id="8f3b5-218">Create Identical Symmetric Keys on Two Servers</span></span>](create-identical-symmetric-keys-on-two-servers.md)  
  
  
