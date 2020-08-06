---
title: 備份加密金鑰 (SSRS 原生模式) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- SQL12.rsconfigtool.backupencryptionkey.F1
ms.assetid: eb8c82be-323b-4d86-ab10-c1bf69a4abe3
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: d82a9b594e4a7ef7ceeb6737932e7e42a7f6fb74
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595529"
---
# <a name="backup-encryption-key-ssrs-native-mode"></a><span data-ttu-id="a0444-102">備份加密金鑰 (SSRS 原生模式)</span><span class="sxs-lookup"><span data-stu-id="a0444-102">Backup Encryption Key (SSRS Native Mode)</span></span>
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="a0444-103">會使用加密金鑰來保護儲存於報表伺服器資料庫中的敏感性資料安全。</span><span class="sxs-lookup"><span data-stu-id="a0444-103">uses an encryption key to secure sensitive data that is stored in the report server database.</span></span> <span data-ttu-id="a0444-104">擁有此金鑰的備份對於確保對加密連接字串和認證的持續存取權非常重要。</span><span class="sxs-lookup"><span data-stu-id="a0444-104">Having a backup of this key is essential for ensuring continued access to encrypted connection strings and credentials.</span></span> <span data-ttu-id="a0444-105">如果您要將報表伺服器資料庫移到另一部電腦，或是您要變更報表伺服器服務帳戶的使用者名稱或密碼，您必須擁有此金鑰的備份副本。</span><span class="sxs-lookup"><span data-stu-id="a0444-105">You must have a backup copy of this key if you move the report server database to another computer or if you change the user name or password of the Report Server service account.</span></span> <span data-ttu-id="a0444-106">這兩個作業都需要從您之前建立的備份副本還原此金鑰。</span><span class="sxs-lookup"><span data-stu-id="a0444-106">Both operations require that you restore the key from a backup copy that you previously created.</span></span>  
  
 [!INCLUDE[applies](../../includes/applies-md.md)]<span data-ttu-id="a0444-107">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]原生模式。</span><span class="sxs-lookup"><span data-stu-id="a0444-107">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Native mode.</span></span>  
  
 <span data-ttu-id="a0444-108">若要開啟 [備份加密金鑰] 對話方塊，請按一下 **組態管理員導覽窗格內的** [加密金鑰] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ，然後按一下 **[備份]**。</span><span class="sxs-lookup"><span data-stu-id="a0444-108">To open the Backup Encryption Key dialog box, click **Encryption Keys** in the navigation pane of the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager, and then click **Backup**.</span></span> <span data-ttu-id="a0444-109">當您使用 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 組態管理員內的 [服務帳戶] 頁面來更新服務帳戶時，這個對話方塊也會出現。</span><span class="sxs-lookup"><span data-stu-id="a0444-109">This dialog box also appears when you update the service account using the Service Account page in the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager.</span></span> <span data-ttu-id="a0444-110">如需 Configuration Manager 的詳細資訊 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ，請參閱[Reporting Services 組態管理員 &#40;原生模式&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="a0444-110">For more information on the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager, see [Reporting Services Configuration Manager &#40;Native Mode&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="a0444-111">選項</span><span class="sxs-lookup"><span data-stu-id="a0444-111">Options</span></span>  
 <span data-ttu-id="a0444-112">**檔案位置**</span><span class="sxs-lookup"><span data-stu-id="a0444-112">**File Location**</span></span>  
 <span data-ttu-id="a0444-113">為對稱金鑰指定 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 的檔案名稱和位置。</span><span class="sxs-lookup"><span data-stu-id="a0444-113">Specify a file name and location for [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] to the symmetric key.</span></span> <span data-ttu-id="a0444-114">對稱金鑰絕不會以純文字的方式儲存。</span><span class="sxs-lookup"><span data-stu-id="a0444-114">The symmetric key is never stored in plain text.</span></span> <span data-ttu-id="a0444-115">您必須輸入密碼來保護該檔案。</span><span class="sxs-lookup"><span data-stu-id="a0444-115">You must type a password to protect the file.</span></span>  
  
 <span data-ttu-id="a0444-116">**密碼**</span><span class="sxs-lookup"><span data-stu-id="a0444-116">**Password**</span></span>  
 <span data-ttu-id="a0444-117">請輸入可保護檔案的密碼，以防止未經授權的存取。</span><span class="sxs-lookup"><span data-stu-id="a0444-117">Type a password that protects the file against unauthorized access.</span></span> <span data-ttu-id="a0444-118">只有知道此密碼的使用者才能夠還原在檔案內鎖定的金鑰。</span><span class="sxs-lookup"><span data-stu-id="a0444-118">Only users who know the password will be able to restore the key that is locked inside the file.</span></span> [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="a0444-119">會強制實施增強式密碼原則。</span><span class="sxs-lookup"><span data-stu-id="a0444-119">enforces a strong password policy.</span></span> <span data-ttu-id="a0444-120">此密碼至少必須為 8 個字元，以及包含大小寫英數字元和至少一個符號字元的組合。</span><span class="sxs-lookup"><span data-stu-id="a0444-120">The password must be at least 8 characters and include a combination of uppercase and lowercase alphanumeric characters and at least one symbol character.</span></span>  
  
 <span data-ttu-id="a0444-121">**確認密碼**</span><span class="sxs-lookup"><span data-stu-id="a0444-121">**Confirm Password**</span></span>  
 <span data-ttu-id="a0444-122">重新輸入您剛剛輸入的密碼。</span><span class="sxs-lookup"><span data-stu-id="a0444-122">Re-type the password you entered.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0444-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a0444-123">See Also</span></span>  
 <span data-ttu-id="a0444-124">[Reporting Services 組態管理員 &#40;SSRS 原生模式的 F1 說明主題&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-f1-help-topics-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="a0444-124">[Reporting Services Configuration Manager F1 Help Topics &#40;SSRS Native Mode&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-f1-help-topics-ssrs-native-mode.md) </span></span>  
 <span data-ttu-id="a0444-125">[備份與還原 Reporting Services 加密金鑰](../../reporting-services/install-windows/ssrs-encryption-keys-back-up-and-restore-encryption-keys.md) </span><span class="sxs-lookup"><span data-stu-id="a0444-125">[Back Up and Restore Reporting Services Encryption Keys](../../reporting-services/install-windows/ssrs-encryption-keys-back-up-and-restore-encryption-keys.md) </span></span>  
 <span data-ttu-id="a0444-126">[刪除和重新建立加密金鑰 &#40;SSRS 組態管理員&#41;](../../reporting-services/install-windows/ssrs-encryption-keys-delete-and-re-create-encryption-keys.md) </span><span class="sxs-lookup"><span data-stu-id="a0444-126">[Delete and Re-create Encryption Keys  &#40;SSRS Configuration Manager&#41;](../../reporting-services/install-windows/ssrs-encryption-keys-delete-and-re-create-encryption-keys.md) </span></span>  
 <span data-ttu-id="a0444-127">[將報表伺服器初始化 &#40;SSRS 組態管理員&#41;](../../reporting-services/install-windows/ssrs-encryption-keys-initialize-a-report-server.md) </span><span class="sxs-lookup"><span data-stu-id="a0444-127">[Initialize a Report Server &#40;SSRS Configuration Manager&#41;](../../reporting-services/install-windows/ssrs-encryption-keys-initialize-a-report-server.md) </span></span>  
 <span data-ttu-id="a0444-128">[儲存加密的報表伺服器資料 &#40;SSRS 組態管理員&#41;](../../reporting-services/install-windows/ssrs-encryption-keys-store-encrypted-report-server-data.md) </span><span class="sxs-lookup"><span data-stu-id="a0444-128">[Store Encrypted Report Server Data &#40;SSRS Configuration Manager&#41;](../../reporting-services/install-windows/ssrs-encryption-keys-store-encrypted-report-server-data.md) </span></span>  
 [<span data-ttu-id="a0444-129">&#40;SSRS 原生模式的加密金鑰&#41;</span><span class="sxs-lookup"><span data-stu-id="a0444-129">Encryption Keys &#40;SSRS Native Mode&#41;</span></span>](../../../2014/sql-server/install/encryption-keys-ssrs-native-mode.md)  
  
  
