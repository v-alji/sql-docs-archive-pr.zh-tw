---
title: 設定和管理加密金鑰 (SSRS 設定管理員) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- encryption keys [Reporting Services]
- private keys [Reporting Services]
- cryptography [Reporting Services]
- symmetric keys [Reporting Services]
- encryption [Reporting Services]
- public keys [Reporting Services]
ms.assetid: 58e61636-88a2-4338-ae5f-3dd210aee887
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: afe9edff22c67b9b27c1fca88c9413f5a9ed98de
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710298"
---
# <a name="configure-and-manage-encryption-keys-ssrs-configuration-manager"></a><span data-ttu-id="c794a-102">設定和管理加密金鑰 (SSRS 組態管理員)</span><span class="sxs-lookup"><span data-stu-id="c794a-102">Configure and Manage Encryption Keys (SSRS Configuration Manager)</span></span>
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="c794a-103">會使用加密金鑰來保護儲存於報表伺服器資料庫中之認證和連線資訊的安全。</span><span class="sxs-lookup"><span data-stu-id="c794a-103">uses encryption keys to secure credentials and connection information that is stored in a report server database.</span></span> <span data-ttu-id="c794a-104">在 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]中，可透過用於保護敏感性資料的公開、私密和對稱金鑰組合來支援加密。</span><span class="sxs-lookup"><span data-stu-id="c794a-104">In [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], encryption is supported through a combination of public, private, and symmetric keys that are used to protect sensitive data.</span></span> <span data-ttu-id="c794a-105">當您安裝或設定報表伺服器時，對稱金鑰會在報表伺服器起始設定期間建立，供報表伺服器用來對儲存於報表伺服器中之機密資料進行加密。</span><span class="sxs-lookup"><span data-stu-id="c794a-105">The symmetric key is created during report server initialization when you install or configure the report server, and it is used by the report server to encrypt sensitive data that is stored in the report server.</span></span> <span data-ttu-id="c794a-106">公開金鑰和私密金鑰是由作業系統所建立，可用來保護對稱金鑰。</span><span class="sxs-lookup"><span data-stu-id="c794a-106">Public and private keys are created by the operating system, and they are used to protect the symmetric key.</span></span> <span data-ttu-id="c794a-107">針對負責儲存報表伺服器資料庫中之機密資料的每一個報表伺服器執行個體，建立一組公開金鑰和私密金鑰。</span><span class="sxs-lookup"><span data-stu-id="c794a-107">A public and private key pair is created for each report server instance that stores sensitive data in a report server database.</span></span>  
  
 <span data-ttu-id="c794a-108">加密金鑰的管理包括建立對稱金鑰的備份副本，以及了解還原、刪除或變更金鑰的時機和方法。</span><span class="sxs-lookup"><span data-stu-id="c794a-108">Managing the encryption keys consists of creating a backup copy of the symmetric key, and knowing when and how to restore, delete, or change the keys.</span></span> <span data-ttu-id="c794a-109">如果您移轉報表伺服器安裝架構或設定向外延展部署，您必須擁有一份對稱金鑰的備份，才能將其套用於新的安裝架構。</span><span class="sxs-lookup"><span data-stu-id="c794a-109">If you migrate a report server installation or configure a scale-out deployment, you must have a backup copy of the symmetric key so that you can apply it to the new installation.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="c794a-110">定期變更 Reporting Services 加密金鑰是安全性最佳作法。</span><span class="sxs-lookup"><span data-stu-id="c794a-110">Periodically changing the Reporting Services encryption key is a security best practice.</span></span> <span data-ttu-id="c794a-111">建議您在進行 Reporting Services 的主要版本升級之後，立即變更金鑰。</span><span class="sxs-lookup"><span data-stu-id="c794a-111">A recommended time to change the key is immediately following a major version upgrade of Reporting Services.</span></span> <span data-ttu-id="c794a-112">在升級之後變更金鑰可將升級循環以外，由變更 Reporting Services 加密金鑰所造成的其他服務中斷減至最少。</span><span class="sxs-lookup"><span data-stu-id="c794a-112">Changing the key after an upgrade minimizes additional service interruption caused by changing the Reporting Services encryption key outside of the upgrade cycle.</span></span>  
  
 <span data-ttu-id="c794a-113">若要管理對稱金鑰，可以使用 Reporting Services 組態工具或 **rskeymgmt** 公用程式。</span><span class="sxs-lookup"><span data-stu-id="c794a-113">To manage symmetric keys, you can use the Reporting Services Configuration tool or the **rskeymgmt** utility.</span></span> <span data-ttu-id="c794a-114">隨附於 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 中的工具只能用來管理對稱金鑰 (公開金鑰和私密金鑰則由作業系統負責管理)。</span><span class="sxs-lookup"><span data-stu-id="c794a-114">The tools included in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] are used to manage the symmetric key only (the public and private keys are managed by the operating system).</span></span> <span data-ttu-id="c794a-115">Reporting Services 組態工具和 **rskeymgmt** 公用程式皆支援下列工作：</span><span class="sxs-lookup"><span data-stu-id="c794a-115">Both the Reporting Services Configuration tool and the **rskeymgmt** utility support the following tasks:</span></span>  
  
-   <span data-ttu-id="c794a-116">備份對稱金鑰的副本，讓您能夠使用金鑰來復原報表伺服器安裝，或做為計劃移轉的一部分。</span><span class="sxs-lookup"><span data-stu-id="c794a-116">Back up a copy of the symmetric key so that you can use it to recover a report server installation or as part of a planned migration.</span></span>  
  
-   <span data-ttu-id="c794a-117">還原先前儲存的對稱金鑰到報表伺服器資料庫，可以讓新報表伺服器執行個體存取它原先未加密的現有資料。</span><span class="sxs-lookup"><span data-stu-id="c794a-117">Restore a previously saved symmetric key to a report server database, allowing a new report server instance to access existing data that it did not originally encrypt.</span></span>  
  
-   <span data-ttu-id="c794a-118">在極罕見的無法再存取加密資料的事件中，刪除報表伺服器資料庫中的加密金鑰。</span><span class="sxs-lookup"><span data-stu-id="c794a-118">Delete the encrypted data in a report server database in the unlikely event that you can no longer access encrypted data.</span></span>  
  
-   <span data-ttu-id="c794a-119">在極罕見的對稱金鑰受到危害的事件中，重新建立對稱金鑰並重新將資料加密。</span><span class="sxs-lookup"><span data-stu-id="c794a-119">Re-create symmetric keys and re-encrypt data in the unlikely event that the symmetric key is compromised.</span></span> <span data-ttu-id="c794a-120">就安全性最佳做法而言，您應定期重新建立對稱金鑰 (例如，每幾個月)，以保護報表伺服器資料庫免於駭客進行破解金鑰的攻擊。</span><span class="sxs-lookup"><span data-stu-id="c794a-120">As a security best practice, you should recreate the symmetric key periodically (for example, every few months) to protect the report server database from cyber attacks that attempt to decipher the key.</span></span>  
  
-   <span data-ttu-id="c794a-121">在向外延展部署中加入或移除報表伺服器執行個體，其中多個報表伺服器共用單一報表伺服器資料庫和能加解密該資料庫的對稱金鑰。</span><span class="sxs-lookup"><span data-stu-id="c794a-121">Add or remove a report server instance from a report server scale-out deployment where multiple report servers share both a single report server database and the symmetric key that provides reversible encryption for that database.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c794a-122">本節內容</span><span class="sxs-lookup"><span data-stu-id="c794a-122">In This Section</span></span>  
 [<span data-ttu-id="c794a-123">將報表伺服器初始化 &#40;SSRS 組態管理員&#41;</span><span class="sxs-lookup"><span data-stu-id="c794a-123">Initialize a Report Server &#40;SSRS Configuration Manager&#41;</span></span>](ssrs-encryption-keys-initialize-a-report-server.md)  
 <span data-ttu-id="c794a-124">說明如何建立加密金鑰。</span><span class="sxs-lookup"><span data-stu-id="c794a-124">Explains how encryption keys are created.</span></span>  
  
 [<span data-ttu-id="c794a-125">備份與還原 Reporting Services 加密金鑰</span><span class="sxs-lookup"><span data-stu-id="c794a-125">Back Up and Restore Reporting Services Encryption Keys</span></span>](ssrs-encryption-keys-back-up-and-restore-encryption-keys.md)  
 <span data-ttu-id="c794a-126">說明如何備份加密金鑰，並還原金鑰以復原或移轉報表伺服器安裝。</span><span class="sxs-lookup"><span data-stu-id="c794a-126">Explains how to back up encryption keys and restore them to recover or migrate a report server installation.</span></span>  
  
 [<span data-ttu-id="c794a-127">儲存加密的報表伺服器資料 &#40;SSRS 組態管理員&#41;</span><span class="sxs-lookup"><span data-stu-id="c794a-127">Store Encrypted Report Server Data &#40;SSRS Configuration Manager&#41;</span></span>](ssrs-encryption-keys-store-encrypted-report-server-data.md)  
 <span data-ttu-id="c794a-128">描述報表伺服器的加密。</span><span class="sxs-lookup"><span data-stu-id="c794a-128">Describes encryption on a report server.</span></span>  
  
 [<span data-ttu-id="c794a-129">刪除和重新建立加密金鑰 &#40;SSRS 組態管理員&#41;</span><span class="sxs-lookup"><span data-stu-id="c794a-129">Delete and Re-create Encryption Keys  &#40;SSRS Configuration Manager&#41;</span></span>](ssrs-encryption-keys-delete-and-re-create-encryption-keys.md)  
 <span data-ttu-id="c794a-130">說明如何以新版本取代對稱金鑰，以及如果無法驗證對稱金鑰，應如何重新建立。</span><span class="sxs-lookup"><span data-stu-id="c794a-130">Explains how you can replace a symmetric key with a new version, and how to start over if symmetric keys cannot be validated.</span></span>  
  
 [<span data-ttu-id="c794a-131">加入和移除向外延展部署的加密金鑰 &#40;SSRS 組態管理員&#41;</span><span class="sxs-lookup"><span data-stu-id="c794a-131">Add and Remove Encryption Keys for Scale-Out Deployment &#40;SSRS Configuration Manager&#41;</span></span>](add-and-remove-encryption-keys-for-scale-out-deployment.md)  
 <span data-ttu-id="c794a-132">說明如何加入和移除加密金鑰，以控制哪些報表伺服器屬於向外延展部署的一部分。</span><span class="sxs-lookup"><span data-stu-id="c794a-132">Explains how to add and remove encryption keys to control which report servers are part of a scale-out deployment.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c794a-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c794a-133">See Also</span></span>  
 [<span data-ttu-id="c794a-134">儲存加密的報表伺服器資料 &#40;SSRS 組態管理員&#41;</span><span class="sxs-lookup"><span data-stu-id="c794a-134">Store Encrypted Report Server Data &#40;SSRS Configuration Manager&#41;</span></span>](ssrs-encryption-keys-store-encrypted-report-server-data.md)  
  
  
