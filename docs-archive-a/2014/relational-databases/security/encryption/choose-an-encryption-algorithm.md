---
title: 選擇加密演算法 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- cryptography [SQL Server], algorithms
- encryption [SQL Server], algorithms
- security [SQL Server], encryption
- algorithms [SQL Server encryption]
ms.assetid: 8227028c-a9c9-489d-bd27-fbf8242634ae
author: jaszymas
ms.author: jaszymas
ms.openlocfilehash: 3b2c5292b4a00a3ad81e53fdbc603bb584130613
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709082"
---
# <a name="choose-an-encryption-algorithm"></a><span data-ttu-id="9fb70-102">選擇加密演算法</span><span class="sxs-lookup"><span data-stu-id="9fb70-102">Choose an Encryption Algorithm</span></span>
  <span data-ttu-id="9fb70-103">加密是全面防禦中的一環，可提供給想要維護 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]執行個體安全的管理員使用。</span><span class="sxs-lookup"><span data-stu-id="9fb70-103">Encryption is one of several defenses-in-depth that are available to the administrator who wants to secure an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="9fb70-104">加密演算法會定義資料轉換，讓未經授權的使用者無法輕鬆地反轉資料轉換。</span><span class="sxs-lookup"><span data-stu-id="9fb70-104">Encryption algorithms define data transformations that cannot be easily reversed by unauthorized users.</span></span> [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="9fb70-105">可讓管理員和開發人員在數種演算法中進行選擇，包括 DES、Triple DES、TRIPLE_DES_3KEY、RC2、RC4、128 位元 RC4、DESX、128 位元 AES、192 位元 AES 和 256 位元 AES。</span><span class="sxs-lookup"><span data-stu-id="9fb70-105">allows administrators and developers to choose from among several algorithms, including DES, Triple DES, TRIPLE_DES_3KEY, RC2, RC4, 128-bit RC4, DESX, 128-bit AES, 192-bit AES, and 256-bit AES.</span></span>  
  
 <span data-ttu-id="9fb70-106">同一種演算法不可能適用於所有情況，各種演算法優缺點的指南也超出《 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 線上叢書》的範疇。</span><span class="sxs-lookup"><span data-stu-id="9fb70-106">No single algorithm is ideal for all situations, and guidance on the merits of each is beyond the scope of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Books Online.</span></span> <span data-ttu-id="9fb70-107">不過，下列為一般適用的原則：</span><span class="sxs-lookup"><span data-stu-id="9fb70-107">However, the following general principles apply:</span></span>  
  
-   <span data-ttu-id="9fb70-108">強式加密通常比弱式加密耗用更多 CPU 資源。</span><span class="sxs-lookup"><span data-stu-id="9fb70-108">Strong encryption generally consumes more CPU resources than weak encryption.</span></span>  
  
-   <span data-ttu-id="9fb70-109">長金鑰通常會比短金鑰產生更強的加密。</span><span class="sxs-lookup"><span data-stu-id="9fb70-109">Long keys generally yield stronger encryption than short keys.</span></span>  
  
-   <span data-ttu-id="9fb70-110">非對稱加密比使用相同金鑰長度的對稱加密更弱，而且速度相對比較慢。</span><span class="sxs-lookup"><span data-stu-id="9fb70-110">Asymmetric encryption is weaker than symmetric encryption using the same key length, but it is relatively slow.</span></span>  
  
-   <span data-ttu-id="9fb70-111">含有長金鑰的區塊密碼比串流式密碼更強。</span><span class="sxs-lookup"><span data-stu-id="9fb70-111">Block ciphers with long keys are stronger than stream ciphers.</span></span>  
  
-   <span data-ttu-id="9fb70-112">複雜的長密碼比短密碼更強。</span><span class="sxs-lookup"><span data-stu-id="9fb70-112">Long, complex passwords are stronger than short passwords.</span></span>  
  
-   <span data-ttu-id="9fb70-113">如果您要加密很多資料，應該使用對稱金鑰來加密資料，並使用非對稱金鑰來加密對稱金鑰。</span><span class="sxs-lookup"><span data-stu-id="9fb70-113">If you are encrypting lots of data, you should encrypt the data using a symmetric key, and encrypt the symmetric key with an asymmetric key.</span></span>  
  
-   <span data-ttu-id="9fb70-114">加密的資料無法壓縮，但壓縮資料可以加密。</span><span class="sxs-lookup"><span data-stu-id="9fb70-114">Encrypted data cannot be compressed, but compressed data can be encrypted.</span></span> <span data-ttu-id="9fb70-115">如果您使用壓縮，應該在加密之前先壓縮資料。</span><span class="sxs-lookup"><span data-stu-id="9fb70-115">If you use compression, you should compress data before encrypting it.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="9fb70-116">只有 RC4 演算法支援回溯相容性。</span><span class="sxs-lookup"><span data-stu-id="9fb70-116">The RC4 algorithm is only supported for backward compatibility.</span></span> <span data-ttu-id="9fb70-117">只有在資料庫相容性層級為 90 或 100 時，才能使用 RC4 或 RC4_128 加密新資料</span><span class="sxs-lookup"><span data-stu-id="9fb70-117">New material can only be encrypted using RC4 or RC4_128 when the database is in compatibility level 90 or 100.</span></span> <span data-ttu-id="9fb70-118">(不建議使用)。請改用較新的演算法，例如其中一個 AES 演算法。</span><span class="sxs-lookup"><span data-stu-id="9fb70-118">(Not recommended.) Use a newer algorithm such as one of the AES algorithms instead.</span></span> <span data-ttu-id="9fb70-119">在 [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] 和更新版本中使用 RC4 或 RC4_128 加密的資料，可以在任何相容性層級進行解密。</span><span class="sxs-lookup"><span data-stu-id="9fb70-119">In [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] and higher material encrypted using RC4 or RC4_128 can be decrypted in any compatibility level.</span></span>  
>   
>  <span data-ttu-id="9fb70-120">在不同的資料區塊上重複使用相同的 RC4 或 RC4_128 KEY_GUID，結果會是相同的 RC4 金鑰，因為 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 不會自動提供 Salt。</span><span class="sxs-lookup"><span data-stu-id="9fb70-120">Repeated use of the same RC4 or RC4_128 KEY_GUID on different blocks of data will result in the same RC4 key because [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] does not provide a salt automatically.</span></span> <span data-ttu-id="9fb70-121">重複使用相同的 RC4 金鑰是已知的錯誤，此錯誤會造成加密變弱。</span><span class="sxs-lookup"><span data-stu-id="9fb70-121">Using the same RC4 key repeatedly is a well-known error that will result in very weak encryption.</span></span> <span data-ttu-id="9fb70-122">因此，我們取代了 RC4 和 RC4_128 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="9fb70-122">Therefore, we have deprecated the RC4 and RC4_128 keywords.</span></span> [!INCLUDE[ssNoteDepFutureDontUse](../../../includes/ssnotedepfuturedontuse-md.md)]  
  
 <span data-ttu-id="9fb70-123">如需加密演算法和加密技術的詳細資訊，請參閱 MSDN 上《.NET Framework 開發人員手冊》中的 [重要的安全性概念](https://go.microsoft.com/fwlink/?LinkId=62082) 。</span><span class="sxs-lookup"><span data-stu-id="9fb70-123">For more information about encryption algorithms and encryption technology, see [Key Security Concepts](https://go.microsoft.com/fwlink/?LinkId=62082) in the .NET Framework Developer's Guide on MSDN.</span></span>  
  
 <span data-ttu-id="9fb70-124">**釐清有關 DES 演算法的資訊：**</span><span class="sxs-lookup"><span data-stu-id="9fb70-124">**Clarification regarding DES algorithms:**</span></span>  
  
-   <span data-ttu-id="9fb70-125">DESX 未正確命名。</span><span class="sxs-lookup"><span data-stu-id="9fb70-125">DESX was incorrectly named.</span></span> <span data-ttu-id="9fb70-126">以 ALGORITHM = DESX 建立的對稱金鑰實際上使用具有 192 位元金鑰的 TRIPLE DES 加密。</span><span class="sxs-lookup"><span data-stu-id="9fb70-126">Symmetric keys created with ALGORITHM = DESX actually use the TRIPLE DES cipher with a 192-bit key.</span></span> <span data-ttu-id="9fb70-127">未提供 DESX 演算法。</span><span class="sxs-lookup"><span data-stu-id="9fb70-127">The DESX algorithm is not provided.</span></span> [!INCLUDE[ssNoteDepFutureAvoid](../../../includes/ssnotedepfutureavoid-md.md)]  
  
-   <span data-ttu-id="9fb70-128">以 ALGORITHM = TRIPLE_DES_3KEY 建立的對稱金鑰使用具有 192 位元金鑰的 TRIPLE DES。</span><span class="sxs-lookup"><span data-stu-id="9fb70-128">Symmetric keys created with ALGORITHM = TRIPLE_DES_3KEY use TRIPLE DES with a 192-bit key.</span></span>  
  
-   <span data-ttu-id="9fb70-129">以 ALGORITHM = TRIPLE_DES 建立的對稱金鑰使用具有 128 位元金鑰的 TRIPLE DES。</span><span class="sxs-lookup"><span data-stu-id="9fb70-129">Symmetric keys created with ALGORITHM = TRIPLE_DES use TRIPLE DES with a 128-bit key.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="9fb70-130">相關工作</span><span class="sxs-lookup"><span data-stu-id="9fb70-130">Related Tasks</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="9fb70-131">使用對稱金鑰加密。</span><span class="sxs-lookup"><span data-stu-id="9fb70-131">Encrypting using a symmetric key.</span></span>|[<span data-ttu-id="9fb70-132">CREATE SYMMETRIC KEY &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="9fb70-132">CREATE SYMMETRIC KEY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-symmetric-key-transact-sql)|  
|<span data-ttu-id="9fb70-133">使用非對稱金鑰加密。</span><span class="sxs-lookup"><span data-stu-id="9fb70-133">Encrypting using an asymmetric key.</span></span>|[<span data-ttu-id="9fb70-134">CREATE ASYMMETRIC KEY &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="9fb70-134">CREATE ASYMMETRIC KEY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-asymmetric-key-transact-sql)|  
|<span data-ttu-id="9fb70-135">使用憑證加密。</span><span class="sxs-lookup"><span data-stu-id="9fb70-135">Encrypting using a certificate.</span></span>|[<span data-ttu-id="9fb70-136">CREATE CERTIFICATE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="9fb70-136">CREATE CERTIFICATE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-certificate-transact-sql)|  
|<span data-ttu-id="9fb70-137">使用透明資料加密來加密資料庫檔案。</span><span class="sxs-lookup"><span data-stu-id="9fb70-137">Encrypting database files using transparent data encryption.</span></span>|[<span data-ttu-id="9fb70-138">透明資料加密 &#40;TDE&#41;</span><span class="sxs-lookup"><span data-stu-id="9fb70-138">Transparent Data Encryption &#40;TDE&#41;</span></span>](transparent-data-encryption.md)|  
|<span data-ttu-id="9fb70-139">如何加密資料表的一個資料行。</span><span class="sxs-lookup"><span data-stu-id="9fb70-139">How to encrypt one column of a table.</span></span>|[<span data-ttu-id="9fb70-140">加密資料行</span><span class="sxs-lookup"><span data-stu-id="9fb70-140">Encrypt a Column of Data</span></span>](encrypt-a-column-of-data.md)|  
  
## <a name="see-also"></a><span data-ttu-id="9fb70-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9fb70-141">See Also</span></span>  
 <span data-ttu-id="9fb70-142">[SQL Server 加密](sql-server-encryption.md) </span><span class="sxs-lookup"><span data-stu-id="9fb70-142">[SQL Server Encryption](sql-server-encryption.md) </span></span>  
 [<span data-ttu-id="9fb70-143">加密階層</span><span class="sxs-lookup"><span data-stu-id="9fb70-143">Encryption Hierarchy</span></span>](encryption-hierarchy.md)  
  
  
