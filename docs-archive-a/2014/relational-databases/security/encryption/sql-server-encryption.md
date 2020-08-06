---
title: SQL Server 加密 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- encryption [SQL Server], about encryption
- security [SQL Server], encryption
- cryptography [SQL Server], about cryptography
ms.assetid: ead0150e-4943-4ad5-84c8-36f85c7278f4
author: jaszymas
ms.author: jaszymas
ms.openlocfilehash: 6fc68e6f3280a8e23d6a1bf4f364aadfffd69f85
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710510"
---
# <a name="sql-server-encryption"></a><span data-ttu-id="30994-102">SQL Server 加密</span><span class="sxs-lookup"><span data-stu-id="30994-102">SQL Server Encryption</span></span>
  <span data-ttu-id="30994-103">加密是透過金鑰或密碼的使用讓資料模糊化的程序。</span><span class="sxs-lookup"><span data-stu-id="30994-103">Encryption is the process of obfuscating data by the use of a key or password.</span></span> <span data-ttu-id="30994-104">這樣可以讓資料變成毫無用處，而不需要對應的解密金鑰或密碼。</span><span class="sxs-lookup"><span data-stu-id="30994-104">This can make the data useless without the corresponding decryption key or password.</span></span> <span data-ttu-id="30994-105">加密並不能解決存取控制問題。</span><span class="sxs-lookup"><span data-stu-id="30994-105">Encryption does not solve access control problems.</span></span> <span data-ttu-id="30994-106">但是，若發生存取控制失靈的情形，加密可限縮資料遺失的風險以增強安全性。</span><span class="sxs-lookup"><span data-stu-id="30994-106">However, it enhances security by limiting data loss even if access controls are bypassed.</span></span> <span data-ttu-id="30994-107">例如，只要資料已加密，即使資料庫主機電腦設定不當而遭駭客取得敏感性資料，失竊的資訊就可能毫無用處。</span><span class="sxs-lookup"><span data-stu-id="30994-107">For example, if the database host computer is misconfigured and a hacker obtains sensitive data, that stolen information might be useless if it is encrypted.</span></span>  
  
 <span data-ttu-id="30994-108">您可以在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 中針對連接、資料和預存程序使用加密。</span><span class="sxs-lookup"><span data-stu-id="30994-108">You can use encryption in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] for connections, data, and stored procedures.</span></span> <span data-ttu-id="30994-109">下表包含 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]中加密的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="30994-109">The following table contains more information about encryption in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="30994-110">雖然加密是維護安全性的寶貴工具，但是不應該將它用於所有的資料或連接。</span><span class="sxs-lookup"><span data-stu-id="30994-110">Although encryption is a valuable tool to help ensure security, it should not be considered for all data or connections.</span></span> <span data-ttu-id="30994-111">當您決定是否要實作加密時，請考慮使用者將如何存取資料。</span><span class="sxs-lookup"><span data-stu-id="30994-111">When you are deciding whether to implement encryption, consider how users will access data.</span></span> <span data-ttu-id="30994-112">如果使用者透過公用網路存取資料，可能需要資料加密來提高安全性。</span><span class="sxs-lookup"><span data-stu-id="30994-112">If users access data over a public network, data encryption might be required to increase security.</span></span> <span data-ttu-id="30994-113">但是，如果所有的存取都與安全的內部網路組態有關，則可能不需要加密。</span><span class="sxs-lookup"><span data-stu-id="30994-113">However, if all access involves a secure intranet configuration, encryption might not be required.</span></span> <span data-ttu-id="30994-114">每次使用加密時，都應該包含密碼、金鑰和憑證的維護策略。</span><span class="sxs-lookup"><span data-stu-id="30994-114">Any use of encryption should also include a maintenance strategy for passwords, keys, and certificates.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="30994-115">本節內容</span><span class="sxs-lookup"><span data-stu-id="30994-115">In This Section</span></span>  
 [<span data-ttu-id="30994-116">加密階層</span><span class="sxs-lookup"><span data-stu-id="30994-116">Encryption Hierarchy</span></span>](encryption-hierarchy.md)  
 <span data-ttu-id="30994-117">有關 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]中加密階層的資訊。</span><span class="sxs-lookup"><span data-stu-id="30994-117">Information about the encryption hierarchy in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
 [<span data-ttu-id="30994-118">選擇加密演算法</span><span class="sxs-lookup"><span data-stu-id="30994-118">Choose an Encryption Algorithm</span></span>](choose-an-encryption-algorithm.md)  
 <span data-ttu-id="30994-119">有關如何選取有效加密演算法的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="30994-119">Information about how to select an effective encrypting algorithm.</span></span>  
  
 [<span data-ttu-id="30994-120">透明資料加密 &#40;TDE&#41;</span><span class="sxs-lookup"><span data-stu-id="30994-120">Transparent Data Encryption &#40;TDE&#41;</span></span>](transparent-data-encryption.md)  
 <span data-ttu-id="30994-121">有關如何以透明方式加密資料的一般資訊。</span><span class="sxs-lookup"><span data-stu-id="30994-121">General information about how to encrypt data transparently.</span></span>  
  
 [<span data-ttu-id="30994-122">SQL Server 和資料庫加密金鑰 &#40;Database Engine&#41;</span><span class="sxs-lookup"><span data-stu-id="30994-122">SQL Server and Database Encryption Keys &#40;Database Engine&#41;</span></span>](sql-server-and-database-encryption-keys-database-engine.md)  
 <span data-ttu-id="30994-123">在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]中，加密金鑰包括用於保護機密資料的公開、私密和對稱金鑰的組合。</span><span class="sxs-lookup"><span data-stu-id="30994-123">In [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], encryption keys include a combination of public, private, and symmetric keys that are used to protect sensitive data.</span></span> <span data-ttu-id="30994-124">本節將說明如何實作及管理加密金鑰。</span><span class="sxs-lookup"><span data-stu-id="30994-124">This section explains how to implement and manage encryption keys.</span></span>  
  
## <a name="related-content"></a><span data-ttu-id="30994-125">相關內容</span><span class="sxs-lookup"><span data-stu-id="30994-125">Related Content</span></span>  
 [<span data-ttu-id="30994-126">保護 SQL Server 的安全</span><span class="sxs-lookup"><span data-stu-id="30994-126">Securing SQL Server</span></span>](../securing-sql-server.md)  
 <span data-ttu-id="30994-127">如何有助於維護 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 平台安全及如何處理使用者與安全性物件的概觀。</span><span class="sxs-lookup"><span data-stu-id="30994-127">Overview of how to help secure the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] platform, and how to work with users and securable objects.</span></span>  
  
 [<span data-ttu-id="30994-128">密碼編譯函數 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="30994-128">Cryptographic Functions &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/cryptographic-functions-transact-sql)  
 <span data-ttu-id="30994-129">有關如何實作密碼編譯函數的資訊。</span><span class="sxs-lookup"><span data-stu-id="30994-129">Information about how to implement cryptographic functions.</span></span>  
  
 [<span data-ttu-id="30994-130">ENCRYPTBYPASSPHRASE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="30994-130">ENCRYPTBYPASSPHRASE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/encryptbypassphrase-transact-sql)  
 <span data-ttu-id="30994-131">有關如何使用密碼來加密資料的資訊。</span><span class="sxs-lookup"><span data-stu-id="30994-131">Information about how to use a password to encrypt data.</span></span>  
  
 [<span data-ttu-id="30994-132">ENCRYPTBYKEY &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="30994-132">ENCRYPTBYKEY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/encryptbykey-transact-sql)  
 <span data-ttu-id="30994-133">有關如何使用對稱金鑰來加密資料的資訊。</span><span class="sxs-lookup"><span data-stu-id="30994-133">Information about how to use a symmetric key to encrypt data.</span></span>  
  
 [<span data-ttu-id="30994-134">ENCRYPTBYASYMKEY &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="30994-134">ENCRYPTBYASYMKEY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/encryptbyasymkey-transact-sql)  
 <span data-ttu-id="30994-135">有關如何使用非對稱金鑰來加密資料的資訊。</span><span class="sxs-lookup"><span data-stu-id="30994-135">Information about how to use an asymmetric key to encrypt data.</span></span>  
  
 [<span data-ttu-id="30994-136">ENCRYPTBYCERT &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="30994-136">ENCRYPTBYCERT &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/encryptbycert-transact-sql)  
 <span data-ttu-id="30994-137">有關如何使用憑證來加密資料的資訊。</span><span class="sxs-lookup"><span data-stu-id="30994-137">Information about how to use a certificate to encrypt data.</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="30994-138">外部資源</span><span class="sxs-lookup"><span data-stu-id="30994-138">External Resources</span></span>  
 [<span data-ttu-id="30994-139">SQL Server 2005 安全性的10個步驟</span><span class="sxs-lookup"><span data-stu-id="30994-139">10 Steps to SQL Server 2005 Security</span></span>](https://www.itprotoday.com/sql-server/10-steps-sql-server-2005-security)  
 <span data-ttu-id="30994-140">有關 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 安全性的最新資訊。</span><span class="sxs-lookup"><span data-stu-id="30994-140">Current information about [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] security.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30994-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="30994-141">See Also</span></span>  
 <span data-ttu-id="30994-142">[sys.key_encryptions &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-key-encryptions-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="30994-142">[sys.key_encryptions &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-key-encryptions-transact-sql) </span></span>  
 <span data-ttu-id="30994-143">[SQL Server 和資料庫加密金鑰 &#40;Database Engine&#41;](sql-server-and-database-encryption-keys-database-engine.md) </span><span class="sxs-lookup"><span data-stu-id="30994-143">[SQL Server and Database Encryption Keys &#40;Database Engine&#41;](sql-server-and-database-encryption-keys-database-engine.md) </span></span>  
 [<span data-ttu-id="30994-144">備份與還原 Reporting Services 加密金鑰</span><span class="sxs-lookup"><span data-stu-id="30994-144">Back Up and Restore Reporting Services Encryption Keys</span></span>](../../../reporting-services/install-windows/ssrs-encryption-keys-back-up-and-restore-encryption-keys.md)  
  
  
