---
title: 加密階層 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- encryption [SQL Server], hierarchies
- cryptography [SQL Server], hierarchies
- encryption keys [SQL Server]
- security [SQL Server], encryption
- hierarchies [SQL Server], encryption
ms.assetid: 96c276d5-1bba-4e95-b678-10f059f1fbcf
author: jaszymas
ms.author: jaszymas
ms.openlocfilehash: d38bb83c2f6a2487e547c4686be5c65bc012e33e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709053"
---
# <a name="encryption-hierarchy"></a><span data-ttu-id="4cc43-102">加密階層</span><span class="sxs-lookup"><span data-stu-id="4cc43-102">Encryption Hierarchy</span></span>
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="4cc43-103">會使用階層式加密與金鑰管理基礎結構來加密資料。</span><span class="sxs-lookup"><span data-stu-id="4cc43-103">encrypts data with a hierarchical encryption and key management infrastructure.</span></span> <span data-ttu-id="4cc43-104">在某一階層執行加密時，會使用憑證、非對稱金鑰、對稱金鑰的組合來加密該階層下的所有階層。</span><span class="sxs-lookup"><span data-stu-id="4cc43-104">Each layer encrypts the layer below it by using a combination of certificates, asymmetric keys, and symmetric keys.</span></span> <span data-ttu-id="4cc43-105">非對稱金鑰和對稱金鑰可以儲存在可延伸金鑰管理 (EKM) 模組內 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 的外部。</span><span class="sxs-lookup"><span data-stu-id="4cc43-105">Asymmetric keys and symmetric keys can be stored outside of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in an Extensible Key Management (EKM) module.</span></span>  
  
 <span data-ttu-id="4cc43-106">下圖顯示每一層的加密階層為該層以下的所有階層進行加密，並顯示最常見的加密組態。</span><span class="sxs-lookup"><span data-stu-id="4cc43-106">The following illustration shows that each layer of the encryption hierarchy encrypts the layer beneath it, and displays the most common encryption configurations.</span></span> <span data-ttu-id="4cc43-107">階層開始的存取通常受到密碼保護。</span><span class="sxs-lookup"><span data-stu-id="4cc43-107">The access to the start of the hierarchy is usually protected by a password.</span></span>  
  
 <span data-ttu-id="4cc43-108">![在堆疊中顯示部分加密組合。](../../../database-engine/media/encryption-hierarchy-stack.gif "在堆疊中顯示部分加密組合。")</span><span class="sxs-lookup"><span data-stu-id="4cc43-108">![Displays some encryption combinations in a stack.](../../../database-engine/media/encryption-hierarchy-stack.gif "Displays some encryption combinations in a stack.")</span></span>  
  
 <span data-ttu-id="4cc43-109">請記住以下概念：</span><span class="sxs-lookup"><span data-stu-id="4cc43-109">Keep in mind the following concepts:</span></span>  
  
-   <span data-ttu-id="4cc43-110">為了取得最佳效能，請使用對稱金鑰加密資料，而不要使用憑證或非對稱金鑰。</span><span class="sxs-lookup"><span data-stu-id="4cc43-110">For best performance, encrypt data using symmetric keys instead of certificates or asymmetric keys.</span></span>  
  
-   <span data-ttu-id="4cc43-111">資料庫主要金鑰受到服務主要金鑰的保護。</span><span class="sxs-lookup"><span data-stu-id="4cc43-111">Database master keys are protected by the Service Master Key.</span></span> <span data-ttu-id="4cc43-112">服務主要金鑰是由 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 安裝程式所建立，而且是以 Windows 資料保護 API (DPAPI) 來加密。</span><span class="sxs-lookup"><span data-stu-id="4cc43-112">The Service Master Key is created by [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] setup and is encrypted with the Windows Data Protection API (DPAPI).</span></span>  
  
-   <span data-ttu-id="4cc43-113">堆疊其他層的其他加密階層是可行的。</span><span class="sxs-lookup"><span data-stu-id="4cc43-113">Other encryption hierarchies stacking additional layers are possible.</span></span>  
  
-   <span data-ttu-id="4cc43-114">Extensible Key Management (EKM) 模組會將對稱金鑰或非對稱金鑰保存在 SQL Server 的外部。</span><span class="sxs-lookup"><span data-stu-id="4cc43-114">An Extensible Key Management (EKM) module holds symmetric or asymmetric keys outside of SQL Server.</span></span>  
  
-   <span data-ttu-id="4cc43-115">透明資料加密 (TDE) 必須使用稱為資料庫加密金鑰的對稱金鑰，該金鑰受到由 master 資料庫之資料庫主要金鑰所保護之憑證的保護，或是受到 EKM 內儲存之非對稱金鑰的保護。</span><span class="sxs-lookup"><span data-stu-id="4cc43-115">Transparent Data Encryption (TDE) must use a symmetric key called the database encryption key which is protected by either a certificate protected by the database master key of the master database, or by an asymmetric key stored in an EKM.</span></span>  
  
-   <span data-ttu-id="4cc43-116">服務主要金鑰和所有資料庫主要金鑰都是對稱金鑰。</span><span class="sxs-lookup"><span data-stu-id="4cc43-116">The Service Master Key and all Database Master Keys are symmetric keys.</span></span>  
  
 <span data-ttu-id="4cc43-117">下圖以其他方式顯示相同的資訊。</span><span class="sxs-lookup"><span data-stu-id="4cc43-117">The following illustration shows the same information in an alternative manner.</span></span>  
  
 <span data-ttu-id="4cc43-118">![在滾輪中顯示部分加密組合。](../../../database-engine/media/encryption-hierarchy-wheel.gif "在滾輪中顯示部分加密組合。")</span><span class="sxs-lookup"><span data-stu-id="4cc43-118">![Displays some encryption combinations in a wheel.](../../../database-engine/media/encryption-hierarchy-wheel.gif "Displays some encryption combinations in a wheel.")</span></span>  
  
 <span data-ttu-id="4cc43-119">此圖說明下列其他概念：</span><span class="sxs-lookup"><span data-stu-id="4cc43-119">This diagram illustrates the following additional concepts:</span></span>  
  
-   <span data-ttu-id="4cc43-120">在此圖中，箭號表示常見的加密階層。</span><span class="sxs-lookup"><span data-stu-id="4cc43-120">In this illustration, arrows indicate common encryption hierarchies.</span></span>  
  
-   <span data-ttu-id="4cc43-121">EKM 中的對稱和非對稱金鑰可以保護 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]內儲存之對稱和非對稱金鑰的存取。</span><span class="sxs-lookup"><span data-stu-id="4cc43-121">Symmetric and asymmetric keys in the EKM can protect access to the symmetric and asymmetric keys stored in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="4cc43-122">與 EKM 相關的虛線表示 EKM 內的金鑰可以取代 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]內儲存的對稱和非對稱金鑰。</span><span class="sxs-lookup"><span data-stu-id="4cc43-122">The dotted line associated with EKM indicates that keys in the EKM could replace the symmetric and asymmetric keys stored in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="encryption-mechanisms"></a><span data-ttu-id="4cc43-123">加密機制</span><span class="sxs-lookup"><span data-stu-id="4cc43-123">Encryption Mechanisms</span></span>  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="4cc43-124">提供下列加密機制：</span><span class="sxs-lookup"><span data-stu-id="4cc43-124">provides the following mechanisms for encryption:</span></span>  
  
-   [!INCLUDE[tsql](../../../includes/tsql-md.md)] <span data-ttu-id="4cc43-125">函數</span><span class="sxs-lookup"><span data-stu-id="4cc43-125">functions</span></span>  
  
-   <span data-ttu-id="4cc43-126">非對稱金鑰</span><span class="sxs-lookup"><span data-stu-id="4cc43-126">Asymmetric keys</span></span>  
  
-   <span data-ttu-id="4cc43-127">對稱金鑰</span><span class="sxs-lookup"><span data-stu-id="4cc43-127">Symmetric keys</span></span>  
  
-   <span data-ttu-id="4cc43-128">憑證</span><span class="sxs-lookup"><span data-stu-id="4cc43-128">Certificates</span></span>  
  
-   <span data-ttu-id="4cc43-129">透明資料加密</span><span class="sxs-lookup"><span data-stu-id="4cc43-129">Transparent Data Encryption</span></span>  
  
### <a name="transact-sql-functions"></a><span data-ttu-id="4cc43-130">Transact-SQL 函數</span><span class="sxs-lookup"><span data-stu-id="4cc43-130">Transact-SQL Functions</span></span>  
 <span data-ttu-id="4cc43-131">當使用 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 函數插入或更新個別項目時，可以進行加密。</span><span class="sxs-lookup"><span data-stu-id="4cc43-131">Individual items can be encrypted as they are inserted or updated using [!INCLUDE[tsql](../../../includes/tsql-md.md)] functions.</span></span> <span data-ttu-id="4cc43-132">如需詳細資訊，請參閱 [ENCRYPTBYPASSPHRASE &#40;Transact-SQL&#41;](/sql/t-sql/functions/encryptbypassphrase-transact-sql) 和 [DECRYPTBYPASSPHRASE &#40;Transact-SQL&#41;](/sql/t-sql/functions/decryptbypassphrase-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="4cc43-132">For more information, see [ENCRYPTBYPASSPHRASE &#40;Transact-SQL&#41;](/sql/t-sql/functions/encryptbypassphrase-transact-sql) and [DECRYPTBYPASSPHRASE &#40;Transact-SQL&#41;](/sql/t-sql/functions/decryptbypassphrase-transact-sql).</span></span>  
  
### <a name="certificates"></a><span data-ttu-id="4cc43-133">憑證</span><span class="sxs-lookup"><span data-stu-id="4cc43-133">Certificates</span></span>  
 <span data-ttu-id="4cc43-134">「公開金鑰憑證」(通常只簡稱為「憑證」) 是經過數位簽署的聲明，憑證會將公開金鑰的值繫結到擁有對應私密金鑰之人員、裝置或服務的識別。</span><span class="sxs-lookup"><span data-stu-id="4cc43-134">A public key certificate, usually just called a certificate, is a digitally-signed statement that binds the value of a public key to the identity of the person, device, or service that holds the corresponding private key.</span></span> <span data-ttu-id="4cc43-135">憑證是由憑證授權單位 (CA) 所發行與簽署。</span><span class="sxs-lookup"><span data-stu-id="4cc43-135">Certificates are issued and signed by a certification authority (CA).</span></span> <span data-ttu-id="4cc43-136">收到 CA 發行之憑證的實體稱為憑證的主體。</span><span class="sxs-lookup"><span data-stu-id="4cc43-136">The entity that receives a certificate from a CA is the subject of that certificate.</span></span> <span data-ttu-id="4cc43-137">一般而言，憑證中包含下列資訊。</span><span class="sxs-lookup"><span data-stu-id="4cc43-137">Typically, certificates contain the following information.</span></span>  
  
-   <span data-ttu-id="4cc43-138">主體的公開金鑰。</span><span class="sxs-lookup"><span data-stu-id="4cc43-138">The public key of the subject.</span></span>  
  
-   <span data-ttu-id="4cc43-139">主體的識別資訊，例如：姓名與電子郵件地址。</span><span class="sxs-lookup"><span data-stu-id="4cc43-139">The identifier information of the subject, such as the name and e-mail address.</span></span>  
  
-   <span data-ttu-id="4cc43-140">有效期間。</span><span class="sxs-lookup"><span data-stu-id="4cc43-140">The validity period.</span></span> <span data-ttu-id="4cc43-141">憑證在這段期間內都會視為有效。</span><span class="sxs-lookup"><span data-stu-id="4cc43-141">This is the length of time that the certificate is considered valid.</span></span>  
  
     <span data-ttu-id="4cc43-142">超過這段期間憑證則無效；每個憑證都包含 [有效期限自]與 [有效期限至]日期。</span><span class="sxs-lookup"><span data-stu-id="4cc43-142">A certificate is valid only for the period of time specified within it; every certificate contains **Valid From** and **Valid To** dates.</span></span> <span data-ttu-id="4cc43-143">這些日期會指定有效期間。</span><span class="sxs-lookup"><span data-stu-id="4cc43-143">These dates set the boundaries of the validity period.</span></span> <span data-ttu-id="4cc43-144">當憑證的有效期過期時，憑證的主體應該要求取得新憑證。</span><span class="sxs-lookup"><span data-stu-id="4cc43-144">When the validity period for a certificate has passed, a new certificate must be requested by the subject of the now-expired certificate.</span></span>  
  
-   <span data-ttu-id="4cc43-145">簽發者識別資訊。</span><span class="sxs-lookup"><span data-stu-id="4cc43-145">Issuer identifier information.</span></span>  
  
-   <span data-ttu-id="4cc43-146">簽發者的數位簽章。</span><span class="sxs-lookup"><span data-stu-id="4cc43-146">The digital signature of the issuer.</span></span>  
  
     <span data-ttu-id="4cc43-147">此簽章可證明公開金鑰與主體識別資訊間之繫結關係的有效性。</span><span class="sxs-lookup"><span data-stu-id="4cc43-147">This signature attests to the validity of the binding between the public key and the identifier information of the subject.</span></span> <span data-ttu-id="4cc43-148">(為資訊加上數位簽章的過程包括將相關資訊以及寄件者的某些機密資訊寫入稱為「簽章」的標記中。)</span><span class="sxs-lookup"><span data-stu-id="4cc43-148">(The process of digitally signing information entails transforming the information, as well as some secret information held by the sender, into a tag called a signature.)</span></span>  
  
 <span data-ttu-id="4cc43-149">憑證的主要好處是可以減輕主機儲存個別主體密碼的負擔。</span><span class="sxs-lookup"><span data-stu-id="4cc43-149">A primary benefit of certificates is that they relieve hosts of the need to maintain a set of passwords for individual subjects.</span></span> <span data-ttu-id="4cc43-150">使用憑證時，主機只要與憑證簽發者 (憑證簽發者可能會簽署不限數目的憑證) 建立信任關係即可。</span><span class="sxs-lookup"><span data-stu-id="4cc43-150">Instead, the host merely establishes trust in a certificate issuer, which may then sign an unlimited number of certificates.</span></span>  
  
 <span data-ttu-id="4cc43-151">當主機 (例如：安全的 Web 伺服器) 指定某個簽發者做為信任的根授權單位時，該主機即隱含信任該簽發者用來建立其所發行之憑證的繫結關係的原則。</span><span class="sxs-lookup"><span data-stu-id="4cc43-151">When a host, such as a secure Web server, designates an issuer as a trusted root authority, the host implicitly trusts the policies that the issuer has used to establish the bindings of certificates it issues.</span></span> <span data-ttu-id="4cc43-152">在實務上，主機會信任簽發者已驗證憑證主體的識別。</span><span class="sxs-lookup"><span data-stu-id="4cc43-152">In effect, the host trusts that the issuer has verified the identity of the certificate subject.</span></span> <span data-ttu-id="4cc43-153">主機會將簽發者的自行簽署憑證 (其中包含簽發者的公開金鑰) 放到主機電腦信任的根憑證授權單位憑證存放區，指定簽發者做為信任的根授權單位。</span><span class="sxs-lookup"><span data-stu-id="4cc43-153">A host designates an issuer as a trusted root authority by putting the self-signed certificate of the issuer, which contains the public key of the issuer, into the trusted root certification authority certificate store of the host computer.</span></span> <span data-ttu-id="4cc43-154">除非中繼與從屬憑證授權單位具有有效信任根憑證授權單位路徑，否則不會被信任。</span><span class="sxs-lookup"><span data-stu-id="4cc43-154">Intermediate or subordinate certification authorities are trusted only if they have a valid certification path from a trusted root certification authority.</span></span>  
  
 <span data-ttu-id="4cc43-155">簽發者可以在憑證到期之前予以撤銷。</span><span class="sxs-lookup"><span data-stu-id="4cc43-155">The issuer can revoke a certificate before it expires.</span></span> <span data-ttu-id="4cc43-156">撤銷動作會取消公開金鑰與憑證主體識別資訊之間的繫結。</span><span class="sxs-lookup"><span data-stu-id="4cc43-156">Revocation cancels the binding of a public key to an identity that is asserted in the certificate.</span></span> <span data-ttu-id="4cc43-157">每個簽發者都會維護一份憑證撤銷清單，供程式檢查特定憑證的有效性時使用。</span><span class="sxs-lookup"><span data-stu-id="4cc43-157">Each issuer maintains a certificate revocation list that can be used by programs when they are checking the validity of any given certificate.</span></span>  
  
 <span data-ttu-id="4cc43-158">由 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 建立的自行簽署憑證遵循 X.509 標準，且支援 X.509 v1 欄位。</span><span class="sxs-lookup"><span data-stu-id="4cc43-158">The self-signed certificates created by [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] follow the X.509 standard and support the X.509 v1 fields.</span></span>  
  
### <a name="asymmetric-keys"></a><span data-ttu-id="4cc43-159">非對稱金鑰</span><span class="sxs-lookup"><span data-stu-id="4cc43-159">Asymmetric Keys</span></span>  
 <span data-ttu-id="4cc43-160">非對稱金鑰是由私密金鑰與對應的公開金鑰所組成。</span><span class="sxs-lookup"><span data-stu-id="4cc43-160">An asymmetric key is made up of a private key and the corresponding public key.</span></span> <span data-ttu-id="4cc43-161">每個金鑰都可以用來解密由另一個金鑰所加密的資料。</span><span class="sxs-lookup"><span data-stu-id="4cc43-161">Each key can decrypt data encrypted by the other.</span></span> <span data-ttu-id="4cc43-162">非對稱加密與解密非常耗資源，但能提供比對稱加密更好的安全性層級。</span><span class="sxs-lookup"><span data-stu-id="4cc43-162">Asymmetric encryption and decryption are relatively resource-intensive, but they provide a higher level of security than symmetric encryption.</span></span> <span data-ttu-id="4cc43-163">非對稱金鑰可用來加密對稱金鑰以儲存在資料庫中。</span><span class="sxs-lookup"><span data-stu-id="4cc43-163">An asymmetric key can be used to encrypt a symmetric key for storage in a database.</span></span>  
  
### <a name="symmetric-keys"></a><span data-ttu-id="4cc43-164">對稱金鑰</span><span class="sxs-lookup"><span data-stu-id="4cc43-164">Symmetric Keys</span></span>  
 <span data-ttu-id="4cc43-165">對稱金鑰是用來加密與解密的一個金鑰。</span><span class="sxs-lookup"><span data-stu-id="4cc43-165">A symmetric key is one key that is used for both encryption and decryption.</span></span> <span data-ttu-id="4cc43-166">使用對稱金鑰來加密與解密非常快速，且適合用來針對資料庫中的機密資料進行日常加密。</span><span class="sxs-lookup"><span data-stu-id="4cc43-166">Encryption and decryption by using a symmetric key is fast, and suitable for routine use with sensitive data in the database.</span></span>  
  
### <a name="transparent-data-encryption"></a><span data-ttu-id="4cc43-167">透明資料加密</span><span class="sxs-lookup"><span data-stu-id="4cc43-167">Transparent Data Encryption</span></span>  
 <span data-ttu-id="4cc43-168">透明資料加密 (TDE) 是使用對稱金鑰的特殊加密案例。</span><span class="sxs-lookup"><span data-stu-id="4cc43-168">Transparent Data Encryption (TDE) is a special case of encryption using a symmetric key.</span></span> <span data-ttu-id="4cc43-169">TDE 會使用稱為資料庫加密金鑰的對稱金鑰加密整個資料庫。</span><span class="sxs-lookup"><span data-stu-id="4cc43-169">TDE encrypts an entire database using that symmetric key called the database encryption key.</span></span> <span data-ttu-id="4cc43-170">資料庫加密金鑰受到其他金鑰或憑證的保護，這些金鑰或憑證則受到資料庫主要金鑰或是儲存於 EKM 模組內的非對稱金鑰的保護。</span><span class="sxs-lookup"><span data-stu-id="4cc43-170">The database encryption key is protected by other keys or certificates which are protected either by the database master key or by an asymmetric key stored in an EKM module.</span></span> <span data-ttu-id="4cc43-171">如需詳細資訊，請參閱[透明資料加密 &#40;TDE&#41;](transparent-data-encryption.md)。</span><span class="sxs-lookup"><span data-stu-id="4cc43-171">For more information, see [Transparent Data Encryption &#40;TDE&#41;](transparent-data-encryption.md).</span></span>  
  
## <a name="related-content"></a><span data-ttu-id="4cc43-172">相關內容</span><span class="sxs-lookup"><span data-stu-id="4cc43-172">Related Content</span></span>  
 [<span data-ttu-id="4cc43-173">保護 SQL Server 的安全</span><span class="sxs-lookup"><span data-stu-id="4cc43-173">Securing SQL Server</span></span>](../securing-sql-server.md)  
  
 [<span data-ttu-id="4cc43-174">安全性函數 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="4cc43-174">Security Functions &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/security-functions-transact-sql)  
  
## <a name="see-also"></a><span data-ttu-id="4cc43-175">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4cc43-175">See Also</span></span>  
 <span data-ttu-id="4cc43-176">[權限階層 &#40;Database Engine&#41;](../permissions-hierarchy-database-engine.md) </span><span class="sxs-lookup"><span data-stu-id="4cc43-176">[Permissions Hierarchy &#40;Database Engine&#41;](../permissions-hierarchy-database-engine.md) </span></span>  
 [<span data-ttu-id="4cc43-177">安全性實體</span><span class="sxs-lookup"><span data-stu-id="4cc43-177">Securables</span></span>](../securables.md)  
  
  
