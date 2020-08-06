---
title: SQL Server 憑證與非對稱金鑰 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- security [SQL Server], certificates and asymmetric keys
ms.assetid: 8519aa2f-f09c-4c1c-96b5-abc24811e60c
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: e8af2d92b31fee4f220b4c950fb6b7bd9c519885
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688709"
---
# <a name="sql-server-certificates-and-asymmetric-keys"></a><span data-ttu-id="049ef-102">SQL Server 憑證與非對稱金鑰</span><span class="sxs-lookup"><span data-stu-id="049ef-102">SQL Server Certificates and Asymmetric Keys</span></span>
  <span data-ttu-id="049ef-103"> 公開金鑰加密 (PKI) 是一種訊息加密形式，使用者可用此加密形式來建立「公開\」\** 金鑰和「私密\」\** 金鑰。</span><span class="sxs-lookup"><span data-stu-id="049ef-103">Public Key Cryptography (PKI) is a form of message secrecy in which a user creates a *public* key and a *private* key.</span></span> <span data-ttu-id="049ef-104">私密金鑰會保留在私密位置，而公開金鑰則可以散發給使用者。</span><span class="sxs-lookup"><span data-stu-id="049ef-104">The private key is kept secret, whereas the public key can be distributed to others.</span></span> <span data-ttu-id="049ef-105">雖然這些金鑰在數學上具有相關性，但是私密金鑰無法使用公開金鑰來輕鬆地衍生。</span><span class="sxs-lookup"><span data-stu-id="049ef-105">Although the keys are mathematically related, the private key cannot be easily derived by using the public key.</span></span> <span data-ttu-id="049ef-106">公開金鑰是用來加密資料，而私密金鑰則是用來解密資料。</span><span class="sxs-lookup"><span data-stu-id="049ef-106">The public key is used to encrypt data and the private key is used to decrypt data.</span></span> <span data-ttu-id="049ef-107">使用公開金鑰加密的訊息只能使用正確的私密金鑰來加以解密。</span><span class="sxs-lookup"><span data-stu-id="049ef-107">A message that is encrypted by using the public key can only be decrypted by using the correct private key.</span></span> <span data-ttu-id="049ef-108">由於有兩種不同的金鑰，所以這些金鑰為「非對稱」\*\*(Asymmetric)。</span><span class="sxs-lookup"><span data-stu-id="049ef-108">Since there are two different keys, these keys are *asymmetric*.</span></span>  
  
 <span data-ttu-id="049ef-109">憑證和非對稱金鑰是使用非對稱加密的兩種方式。</span><span class="sxs-lookup"><span data-stu-id="049ef-109">Certificates and asymmetric keys are both ways to use asymmetric encryption.</span></span> <span data-ttu-id="049ef-110">憑證經常當做非對稱金鑰的容器使用，因為它們可以包含類似到期日和簽發者等其他資訊。</span><span class="sxs-lookup"><span data-stu-id="049ef-110">Certificates are often used as containers for asymmetric keys because they can contain more information such as expiry dates and issuers.</span></span> <span data-ttu-id="049ef-111">密碼編譯演算法的兩個機制之間沒有任何差異，而且當提供相同的金鑰長度時，強度不會有任何差異。</span><span class="sxs-lookup"><span data-stu-id="049ef-111">There is no difference between the two mechanisms for the cryptographic algorithm, and no difference in strength given the same key length.</span></span> <span data-ttu-id="049ef-112">一般來說，您可以使用憑證來加密資料庫中的其他加密金鑰類型，或是簽署程式碼模組。</span><span class="sxs-lookup"><span data-stu-id="049ef-112">Generally, you use a certificate to encrypt other types of encryption keys in a database, or to sign code modules.</span></span>  
  
 <span data-ttu-id="049ef-113">憑證和非對稱金鑰可以解密其他金鑰加密的資料。</span><span class="sxs-lookup"><span data-stu-id="049ef-113">Certificates and asymmetric keys can decrypt data that the other encrypts.</span></span> <span data-ttu-id="049ef-114">一般來說，非對稱加密可用來加密對稱金鑰，以儲存在資料庫中。</span><span class="sxs-lookup"><span data-stu-id="049ef-114">Generally, you use asymmetric encryption to encrypt a symmetric key for storage in a database.</span></span>  
  
 <span data-ttu-id="049ef-115">公開金鑰並沒有與憑證一樣的特定格式，而且您無法將它匯出到檔案中。</span><span class="sxs-lookup"><span data-stu-id="049ef-115">A public key does not have a particular format like a certificate would have, and you cannot export it to a file.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="049ef-116">包含的功能可讓您建立與管理要與伺服器和資料庫搭配使用的憑證和金鑰。</span><span class="sxs-lookup"><span data-stu-id="049ef-116">contains features that enable you to create and manage certificates and keys for use with the server and database.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="049ef-117">無法與其他應用程式搭配使用或無法用來在作業系統中建立與管理憑證和金鑰。</span><span class="sxs-lookup"><span data-stu-id="049ef-117">cannot be used to create and manage certificates and keys with other applications or in the operating system.</span></span>  
  
## <a name="certificates"></a><span data-ttu-id="049ef-118">憑證</span><span class="sxs-lookup"><span data-stu-id="049ef-118">Certificates</span></span>  
 <span data-ttu-id="049ef-119">憑證是數位簽署的安全性物件，其中包含 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的公開金鑰 (以及選擇性的私密金鑰)。</span><span class="sxs-lookup"><span data-stu-id="049ef-119">A certificate is a digitally signed security object that contains a public (and optionally a private) key for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="049ef-120">您可以使用外部產生的憑證，或者 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 也可以產生憑證。</span><span class="sxs-lookup"><span data-stu-id="049ef-120">You can use externally generated certificates or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] can generate certificates.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="049ef-121">憑證符合 IETF X.509v3 憑證標準的規則。</span><span class="sxs-lookup"><span data-stu-id="049ef-121">certificates comply with the IETF X.509v3 certificate standard.</span></span>  
  
 <span data-ttu-id="049ef-122">因為可以選擇將金鑰匯出及匯入成 X.509 憑證檔案，所以憑證會非常實用。</span><span class="sxs-lookup"><span data-stu-id="049ef-122">Certificates are useful because of the option of both exporting and importing keys to X.509 certificate files.</span></span> <span data-ttu-id="049ef-123">建立憑證的語法可讓您建立憑證的選項 (如到期日)。</span><span class="sxs-lookup"><span data-stu-id="049ef-123">The syntax for creating certificates allows for creation options for certificates such as an expiry date.</span></span>  
  
### <a name="using-a-certificate-in-sql-server"></a><span data-ttu-id="049ef-124">在 SQL Server 中使用憑證</span><span class="sxs-lookup"><span data-stu-id="049ef-124">Using a Certificate in SQL Server</span></span>  
 <span data-ttu-id="049ef-125">憑證可用來維護連接的安全、在資料庫鏡像中用來簽署封裝和其他物件，或是加密資料或連接。</span><span class="sxs-lookup"><span data-stu-id="049ef-125">Certificates can be used to help secure connections, in database mirroring, to sign packages and other objects, or to encrypt data or connections.</span></span> <span data-ttu-id="049ef-126">下表列出 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]中憑證的其他資源。</span><span class="sxs-lookup"><span data-stu-id="049ef-126">The following table lists additional resources for certificates in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
|<span data-ttu-id="049ef-127">主題</span><span class="sxs-lookup"><span data-stu-id="049ef-127">Topic</span></span>|<span data-ttu-id="049ef-128">描述</span><span class="sxs-lookup"><span data-stu-id="049ef-128">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="049ef-129">CREATE CERTIFICATE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="049ef-129">CREATE CERTIFICATE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-certificate-transact-sql)|<span data-ttu-id="049ef-130">說明用來建立憑證的命令。</span><span class="sxs-lookup"><span data-stu-id="049ef-130">Explains the command for creating certificates.</span></span>|  
|[<span data-ttu-id="049ef-131">使用數位簽章來識別封裝的來源</span><span class="sxs-lookup"><span data-stu-id="049ef-131">Identify the Source of Packages with Digital Signatures</span></span>](../../integration-services/security/identify-the-source-of-packages-with-digital-signatures.md)|<span data-ttu-id="049ef-132">顯示有關如何使用憑證來簽署軟體封裝的資訊。</span><span class="sxs-lookup"><span data-stu-id="049ef-132">Shows information about how to use certificates to sign software packages.</span></span>|  
|[<span data-ttu-id="049ef-133">使用資料庫鏡像端點憑證 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="049ef-133">Use Certificates for a Database Mirroring Endpoint &#40;Transact-SQL&#41;</span></span>](../../database-engine/database-mirroring/use-certificates-for-a-database-mirroring-endpoint-transact-sql.md)|<span data-ttu-id="049ef-134">涵蓋如何搭配資料庫鏡像使用憑證的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="049ef-134">Covers information about how to use certificates with Database Mirroring.</span></span>|  
  
## <a name="asymmetric-keys"></a><span data-ttu-id="049ef-135">非對稱金鑰</span><span class="sxs-lookup"><span data-stu-id="049ef-135">Asymmetric Keys</span></span>  
 <span data-ttu-id="049ef-136">非對稱金鑰是用來維護對稱金鑰的安全，</span><span class="sxs-lookup"><span data-stu-id="049ef-136">Asymmetric keys are used for securing symmetric keys.</span></span> <span data-ttu-id="049ef-137">也可用於有限制的資料加密及數位簽署資料庫物件。</span><span class="sxs-lookup"><span data-stu-id="049ef-137">They can also be used for limited data encryption and to digitally sign database objects.</span></span> <span data-ttu-id="049ef-138">非對稱金鑰是由私密金鑰與對應的公開金鑰所組成。</span><span class="sxs-lookup"><span data-stu-id="049ef-138">An asymmetric key consists of a private key and a corresponding public key.</span></span> <span data-ttu-id="049ef-139">如需非對稱金鑰的詳細資訊，請參閱 [CREATE ASYMMETRIC KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-asymmetric-key-transact-sql)的公開金鑰 (以及選擇性的私密金鑰)。</span><span class="sxs-lookup"><span data-stu-id="049ef-139">For more information about asymmetric keys, see [CREATE ASYMMETRIC KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-asymmetric-key-transact-sql).</span></span>  
  
 <span data-ttu-id="049ef-140">非對稱金鑰可從強式名稱金鑰檔案匯入，但是無法匯出。</span><span class="sxs-lookup"><span data-stu-id="049ef-140">Asymmetric keys can be imported from strong name key files, but they cannot be exported.</span></span> <span data-ttu-id="049ef-141">此外，它們也沒有到期選項。</span><span class="sxs-lookup"><span data-stu-id="049ef-141">They also do not have expiry options.</span></span> <span data-ttu-id="049ef-142">非對稱金鑰無法為連接加密。</span><span class="sxs-lookup"><span data-stu-id="049ef-142">Asymmetric keys cannot encrypt connections.</span></span>  
  
### <a name="using-an-asymmetric-key-in-sql-server"></a><span data-ttu-id="049ef-143">在 SQL Server 中使用非對稱金鑰</span><span class="sxs-lookup"><span data-stu-id="049ef-143">Using an Asymmetric Key in SQL Server</span></span>  
 <span data-ttu-id="049ef-144">非對稱金鑰可用來維護資料的安全或是簽署純文字。</span><span class="sxs-lookup"><span data-stu-id="049ef-144">Asymmetric keys can be used to help secure data or sign plaintext.</span></span> <span data-ttu-id="049ef-145">下表列出 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]中非對稱金鑰的其他資源。</span><span class="sxs-lookup"><span data-stu-id="049ef-145">The following table lists additional resources for asymmetric keys in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
|<span data-ttu-id="049ef-146">主題</span><span class="sxs-lookup"><span data-stu-id="049ef-146">Topic</span></span>|<span data-ttu-id="049ef-147">描述</span><span class="sxs-lookup"><span data-stu-id="049ef-147">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="049ef-148">CREATE ASYMMETRIC KEY &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="049ef-148">CREATE ASYMMETRIC KEY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-asymmetric-key-transact-sql)|<span data-ttu-id="049ef-149">說明用來建立非對稱金鑰的命令。</span><span class="sxs-lookup"><span data-stu-id="049ef-149">Explains the command for creating asymmetric keys.</span></span>|  
|[<span data-ttu-id="049ef-150">SIGNBYASYMKEY &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="049ef-150">SIGNBYASYMKEY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/signbyasymkey-transact-sql)|<span data-ttu-id="049ef-151">顯示用來簽署物件的選項。</span><span class="sxs-lookup"><span data-stu-id="049ef-151">Displays the options for signing objects.</span></span>|  
  
## <a name="tools"></a><span data-ttu-id="049ef-152">工具</span><span class="sxs-lookup"><span data-stu-id="049ef-152">Tools</span></span>  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="049ef-153">提供了將會產生憑證和強式名稱金鑰檔案的工具和公用程式。</span><span class="sxs-lookup"><span data-stu-id="049ef-153">provides tools and utilities that will generate certificates and strong name key files.</span></span> <span data-ttu-id="049ef-154">這些工具在金鑰產生的程序中，提供了比 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 語法更豐富的彈性。</span><span class="sxs-lookup"><span data-stu-id="049ef-154">These tools offer a richer amount of flexibility in the key generation process than the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] syntax.</span></span> <span data-ttu-id="049ef-155">您可以使用這些工具來建立具有更複雜金鑰長度的 RSA 金鑰，並將其匯入 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="049ef-155">You can use these tools to create RSA keys with more complex key lengths and then import them into [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="049ef-156">下表說明要在哪裡找到這些工具。</span><span class="sxs-lookup"><span data-stu-id="049ef-156">The following table explains shows where to find these tools.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="049ef-157">工具</span><span class="sxs-lookup"><span data-stu-id="049ef-157">Tool</span></span>|<span data-ttu-id="049ef-158">目的</span><span class="sxs-lookup"><span data-stu-id="049ef-158">Purpose</span></span>|  
|<span data-ttu-id="049ef-159">[makecert](https://msdn2.microsoft.com/library/bfsktky3\(VS.80\).aspx)</span><span class="sxs-lookup"><span data-stu-id="049ef-159">[makecert](https://msdn2.microsoft.com/library/bfsktky3\(VS.80\).aspx)</span></span>|<span data-ttu-id="049ef-160">建立憑證。</span><span class="sxs-lookup"><span data-stu-id="049ef-160">Creates certificates.</span></span>|  
|<span data-ttu-id="049ef-161">[sn](https://msdn2.microsoft.com/library/k5b5tt23\(VS.80\).aspx)</span><span class="sxs-lookup"><span data-stu-id="049ef-161">[sn](https://msdn2.microsoft.com/library/k5b5tt23\(VS.80\).aspx)</span></span>|<span data-ttu-id="049ef-162">為對稱金鑰建立強式名稱。</span><span class="sxs-lookup"><span data-stu-id="049ef-162">Creates strong names for symmetric keys.</span></span>|  
  
## <a name="related-tasks"></a><span data-ttu-id="049ef-163">相關工作</span><span class="sxs-lookup"><span data-stu-id="049ef-163">Related Tasks</span></span>  
 [<span data-ttu-id="049ef-164">選擇加密演算法</span><span class="sxs-lookup"><span data-stu-id="049ef-164">Choose an Encryption Algorithm</span></span>](encryption/choose-an-encryption-algorithm.md)  
  
 [<span data-ttu-id="049ef-165">CREATE SYMMETRIC KEY &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="049ef-165">CREATE SYMMETRIC KEY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-symmetric-key-transact-sql)  
  
 [<span data-ttu-id="049ef-166">CREATE CERTIFICATE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="049ef-166">CREATE CERTIFICATE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-certificate-transact-sql)  
  
## <a name="see-also"></a><span data-ttu-id="049ef-167">另請參閱</span><span class="sxs-lookup"><span data-stu-id="049ef-167">See Also</span></span>  
 <span data-ttu-id="049ef-168">[sys.certificates &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-certificates-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="049ef-168">[sys.certificates &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-certificates-transact-sql) </span></span>  
 [<span data-ttu-id="049ef-169">透明資料加密 &#40;TDE&#41;</span><span class="sxs-lookup"><span data-stu-id="049ef-169">Transparent Data Encryption &#40;TDE&#41;</span></span>](encryption/transparent-data-encryption.md)  
  
