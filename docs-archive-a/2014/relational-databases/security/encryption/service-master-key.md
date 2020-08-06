---
title: 服務主要金鑰 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- service master key [SQL Server]
- service master key [SQL Server], about service master key
ms.assetid: 85f2095d-2590-4f59-8a29-7e100edd02bb
author: jaszymas
ms.author: jaszymas
ms.openlocfilehash: baeeffd49ac89ce85cf64932fbfd4982d7243887
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710521"
---
# <a name="service-master-key"></a><span data-ttu-id="b98a0-102">服務主要金鑰</span><span class="sxs-lookup"><span data-stu-id="b98a0-102">Service Master Key</span></span>
  <span data-ttu-id="b98a0-103">「服務主要金鑰」是 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 加密階層的根。</span><span class="sxs-lookup"><span data-stu-id="b98a0-103">The Service Master Key is the root of the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] encryption hierarchy.</span></span> <span data-ttu-id="b98a0-104">第一次需要利用這種金鑰來加密其他金鑰時，便會自動產生服務主要金鑰。</span><span class="sxs-lookup"><span data-stu-id="b98a0-104">It is generated automatically the first time it is needed to encrypt another key.</span></span> <span data-ttu-id="b98a0-105">依預設，服務主要金鑰是以 Windows 資料保護 API 以及本機電腦金鑰加密。</span><span class="sxs-lookup"><span data-stu-id="b98a0-105">By default, the Service Master Key is encrypted using the Windows data protection API and using the local machine key.</span></span> <span data-ttu-id="b98a0-106">服務主要金鑰只能由建立此金鑰的 Windows 服務帳戶來開啟，或是由可存取服務帳戶名稱及其密碼的主體來開啟。</span><span class="sxs-lookup"><span data-stu-id="b98a0-106">The Service Master Key can only be opened by the Windows service account under which it was created or by a principal with access to both the service account name and its password.</span></span>  
  
 <span data-ttu-id="b98a0-107">重新產生或還原服務主要金鑰包括解密與重新加密完整的加密階層。</span><span class="sxs-lookup"><span data-stu-id="b98a0-107">Regenerating or restoring the Service Master Key involves decrypting and re-encrypting the complete encryption hierarchy.</span></span> <span data-ttu-id="b98a0-108">除非該金鑰已經洩密，才應該在資源需求低的時段，排程進行此項會耗用大量資源的作業。</span><span class="sxs-lookup"><span data-stu-id="b98a0-108">Unless the key has been compromised, this resource-intensive operation should be scheduled during a period of low demand.</span></span>  
  
 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] <span data-ttu-id="b98a0-109">是使用 AES 加密演算法來保護服務主要金鑰 (SMK) 及資料庫主要金鑰 (DMK)。</span><span class="sxs-lookup"><span data-stu-id="b98a0-109">uses the AES encryption algorithm to protect the service master key (SMK) and the database master key (DMK).</span></span> <span data-ttu-id="b98a0-110">與舊版中使用的 3DES 相比，AES 是一種較新的加密演算法。</span><span class="sxs-lookup"><span data-stu-id="b98a0-110">AES is a newer encryption algorithm than 3DES used in earlier versions.</span></span> <span data-ttu-id="b98a0-111">將 [!INCLUDE[ssDE](../../../includes/ssde-md.md)] 執行個體升級至 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 之後，應該會重新產生 SMK 和 DMK，以將主要金鑰升級至 AES。</span><span class="sxs-lookup"><span data-stu-id="b98a0-111">After upgrading an instance of the [!INCLUDE[ssDE](../../../includes/ssde-md.md)] to [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] the SMK and DMK should be regenerated in order to upgrade the master keys to AES.</span></span> <span data-ttu-id="b98a0-112">如需重新產生 SMK 的詳細資訊，請參閱 [ALTER SERVICE MASTER KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-service-master-key-transact-sql) 和 [ALTER MASTER KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-master-key-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="b98a0-112">For more information about regenerating the SMK, see [ALTER SERVICE MASTER KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-service-master-key-transact-sql) and [ALTER MASTER KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-master-key-transact-sql).</span></span>  
  
## <a name="best-practice"></a><span data-ttu-id="b98a0-113">最佳做法</span><span class="sxs-lookup"><span data-stu-id="b98a0-113">Best Practice</span></span>  
 <span data-ttu-id="b98a0-114">備份服務主要金鑰，然後在一個安全且位於異地的位置存放此金鑰備份。</span><span class="sxs-lookup"><span data-stu-id="b98a0-114">Back up the Service Master Key and store the backed up copy in a secure, off-site location.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="b98a0-115">相關工作</span><span class="sxs-lookup"><span data-stu-id="b98a0-115">Related Tasks</span></span>  
 [<span data-ttu-id="b98a0-116">BACKUP SERVICE MASTER KEY &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="b98a0-116">BACKUP SERVICE MASTER KEY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/backup-service-master-key-transact-sql)  
  
 [<span data-ttu-id="b98a0-117">RESTORE SERVICE MASTER KEY &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="b98a0-117">RESTORE SERVICE MASTER KEY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/restore-service-master-key-transact-sql)  
  
 [<span data-ttu-id="b98a0-118">ALTER SERVICE MASTER KEY &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="b98a0-118">ALTER SERVICE MASTER KEY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-service-master-key-transact-sql)  
  
## <a name="see-also"></a><span data-ttu-id="b98a0-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b98a0-119">See Also</span></span>  
 [<span data-ttu-id="b98a0-120">加密階層</span><span class="sxs-lookup"><span data-stu-id="b98a0-120">Encryption Hierarchy</span></span>](encryption-hierarchy.md)  
  
  
