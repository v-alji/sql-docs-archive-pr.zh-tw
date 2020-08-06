---
title: 備份與還原 Reporting Services 加密金鑰 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- backing up encryption keys [Reporting Services]
- restoring encryption keys [Reporting Services]
- encryption keys [Reporting Services]
- symmetric keys [Reporting Services]
ms.assetid: 6773d5df-03ef-4781-beb7-9f6825bac979
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c8e7e61f58632898fc6150210598a671157639a3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710302"
---
# <a name="back-up-and-restore-reporting-services-encryption-keys"></a><span data-ttu-id="dd55e-102">備份與還原 Reporting Services 加密金鑰</span><span class="sxs-lookup"><span data-stu-id="dd55e-102">Back Up and Restore Reporting Services Encryption Keys</span></span>
  <span data-ttu-id="dd55e-103">在報表伺服器組態中，建立用於加密機密資訊的對稱金鑰備份副本是很重要的一部分。</span><span class="sxs-lookup"><span data-stu-id="dd55e-103">An important part of report server configuration is creating a backup copy of the symmetric key used for encrypting sensitive information.</span></span> <span data-ttu-id="dd55e-104">許多例行作業都需要金鑰的備份副本，這備份副本可以讓您在新安裝中重複使用現有的報表伺服器資料庫。</span><span class="sxs-lookup"><span data-stu-id="dd55e-104">A backup copy of the key is required for many routine operations, and enables you to reuse an existing report server database in a new installation.</span></span>  
  
 <span data-ttu-id="dd55e-105">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 原生模式 | [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint 模式</span><span class="sxs-lookup"><span data-stu-id="dd55e-105">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Native Mode | [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint mode</span></span>  
  
 <span data-ttu-id="dd55e-106">發生下列任何事件時，就必須還原加密金鑰的備份副本。</span><span class="sxs-lookup"><span data-stu-id="dd55e-106">It is necessary to restore the backup copy of the encryption key when any of the following events occur:</span></span>  
  
-   <span data-ttu-id="dd55e-107">變更報表伺服器 Windows 服務帳戶名稱或重設密碼。</span><span class="sxs-lookup"><span data-stu-id="dd55e-107">Changing the Report Server Windows service account name or resetting the password.</span></span> <span data-ttu-id="dd55e-108">當您使用 Reporting Services 組態管理員時，備份金鑰是服務帳戶名稱變更作業的一部分。</span><span class="sxs-lookup"><span data-stu-id="dd55e-108">When you use the Reporting Services Configuration Manager, backing up the key is part of a service account name change operation.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="dd55e-109">重設密碼和變更密碼不同。</span><span class="sxs-lookup"><span data-stu-id="dd55e-109">Resetting the password is not the same as changing the password.</span></span> <span data-ttu-id="dd55e-110">密碼重設需要覆寫網域控制站上之帳戶資訊的權限。</span><span class="sxs-lookup"><span data-stu-id="dd55e-110">A password reset requires permission to overwrite account information on the domain controller.</span></span> <span data-ttu-id="dd55e-111">您忘記密碼或不知道特定密碼時，會由系統管理員執行密碼重設。</span><span class="sxs-lookup"><span data-stu-id="dd55e-111">Password resets are performed by a system administrator when you forget or do not know a particular password.</span></span> <span data-ttu-id="dd55e-112">只有密碼重設需要對稱金鑰還原。</span><span class="sxs-lookup"><span data-stu-id="dd55e-112">Only password resets require symmetric key restoration.</span></span> <span data-ttu-id="dd55e-113">定期變更帳戶密碼並不需要重設對稱金鑰。</span><span class="sxs-lookup"><span data-stu-id="dd55e-113">Periodically changing an account password does not require you to reset the symmetric key.</span></span>  
  
-   <span data-ttu-id="dd55e-114">重新命名主控報表伺服器的電腦或執行個體 (報表伺服器執行個體是以 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體名稱為基礎)。</span><span class="sxs-lookup"><span data-stu-id="dd55e-114">Renaming the computer or instance that hosts the report server (a report server instance is based on a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance name).</span></span>  
  
-   <span data-ttu-id="dd55e-115">移轉報表伺服器安裝或設定報表伺服器，以使用其他報表伺服器資料庫。</span><span class="sxs-lookup"><span data-stu-id="dd55e-115">Migrating a report server installation or configuring a report server to use a different report server database.</span></span>  
  
-   <span data-ttu-id="dd55e-116">由於硬體故障而復原報表伺服器安裝。</span><span class="sxs-lookup"><span data-stu-id="dd55e-116">Recovering a report server installation due to hardware failure.</span></span>  
  
 <span data-ttu-id="dd55e-117">您只需要備份對稱金鑰的一個副本。</span><span class="sxs-lookup"><span data-stu-id="dd55e-117">You only need to back up one copy of the symmetric key.</span></span> <span data-ttu-id="dd55e-118">報表伺服器資料庫與對稱金鑰之間有一對一對應。</span><span class="sxs-lookup"><span data-stu-id="dd55e-118">There is a one-to-one correspondence between a report server database and a symmetric key.</span></span> <span data-ttu-id="dd55e-119">雖然您只需要備份一個副本，但是如果您在向外延展部署模型中執行多個報表伺服器，就可能需要多次還原金鑰。</span><span class="sxs-lookup"><span data-stu-id="dd55e-119">Although you only need to back up one copy, you might need to restore the key multiple times if you are running multiple report servers in a scale-out deployment model.</span></span> <span data-ttu-id="dd55e-120">每個報表伺服器執行個體都需要其對稱金鑰的副本，才能鎖定和解除鎖定報表伺服器資料庫中的資料。</span><span class="sxs-lookup"><span data-stu-id="dd55e-120">Each report server instance will need its copy of the symmetric key to lock and unlock data in the report server database.</span></span>  
  
  
## <a name="backing-up-the-encryption-keys"></a><span data-ttu-id="dd55e-121">備份加密金鑰</span><span class="sxs-lookup"><span data-stu-id="dd55e-121">Backing Up the Encryption Keys</span></span>  
 <span data-ttu-id="dd55e-122">備份對稱金鑰的程序是將金鑰寫入您指定的檔案，然後使用您提供的密碼將金鑰加密。</span><span class="sxs-lookup"><span data-stu-id="dd55e-122">Backing up the symmetric key is a process that writes the key to a file that you specify, and then scrambles the key using a password that you provide.</span></span> <span data-ttu-id="dd55e-123">對稱金鑰絕不能以未加密的狀態儲存，因此您將金鑰儲存到磁碟時，必須提供密碼將其加密。</span><span class="sxs-lookup"><span data-stu-id="dd55e-123">The symmetric key can never be stored in an unencrypted state so you must provide a password to encrypt the key when you save it to disk.</span></span> <span data-ttu-id="dd55e-124">檔案建立之後，您必須將其儲存在安全的位置，並 **記住用來解除檔案鎖定的密碼** 。</span><span class="sxs-lookup"><span data-stu-id="dd55e-124">After the file is created, you must store it in a secure location **and remember the password** that is used to unlock the file.</span></span> <span data-ttu-id="dd55e-125">若要備份對稱金鑰，您可以使用下列工具：</span><span class="sxs-lookup"><span data-stu-id="dd55e-125">To backup the symmetric key, you can use the following tools:</span></span>  
  
 <span data-ttu-id="dd55e-126">**原生模式** ：Reporting Services 組態管理員或 **rskeymgmt** 公用程式。</span><span class="sxs-lookup"><span data-stu-id="dd55e-126">**Native mode:** Either the Reporting Services Configuration Manager or the **rskeymgmt** utility.</span></span>  
  
 <span data-ttu-id="dd55e-127">**SharePoint 模式** ：SharePoint 管理中心頁面或 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="dd55e-127">**SharePoint mode:** SharePoint Central Administration pages or PowerShell.</span></span>  
  
####  <a name="backup-sharepoint-mode-report-servers"></a><a name="bkmk_backup_sharepoint"></a> <span data-ttu-id="dd55e-128">備份 SharePoint 模式報表伺服器</span><span class="sxs-lookup"><span data-stu-id="dd55e-128">Backup SharePoint Mode Report Servers</span></span>  
 <span data-ttu-id="dd55e-129">對於 SharePoint 模式報表伺服器，您可以使用 PowerShell 命令，或使用適用於 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 服務應用程式的管理頁面。</span><span class="sxs-lookup"><span data-stu-id="dd55e-129">For SharePoint mode report servers you can either use PowerShell commands or use the management pages for the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service application.</span></span> <span data-ttu-id="dd55e-130">如需詳細資訊，請參閱[管理 Reporting Services SharePoint 服務應用程式](../manage-a-reporting-services-sharepoint-service-application.md)的＜金鑰管理＞一節</span><span class="sxs-lookup"><span data-stu-id="dd55e-130">For more information, see the "Key Management" section of [Manage a Reporting Services SharePoint Service Application](../manage-a-reporting-services-sharepoint-service-application.md)</span></span>  
  
####  <a name="back-up-encryption-keys--reporting-services-configuration-manager-native-mode"></a><a name="bkmk_backup_configuration_manager"></a> <span data-ttu-id="dd55e-131">備份加密金鑰 - Reporting Services 組態管理員 (原生模式)</span><span class="sxs-lookup"><span data-stu-id="dd55e-131">Back up encryption keys -Reporting Services Configuration Manager (Native Mode)</span></span>  
  
1.  <span data-ttu-id="dd55e-132">啟動 Reporting Services 組態管理員，然後連接到您要設定的報表伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="dd55e-132">Start the Reporting Services Configuration Manager, and then connect to the report server instance you want to configure.</span></span>  
  
2.  <span data-ttu-id="dd55e-133">按一下 **[加密金鑰]**，然後按一下 **[備份]**。</span><span class="sxs-lookup"><span data-stu-id="dd55e-133">Click **Encryption Keys**, and then click **Back Up**.</span></span>  
  
3.  <span data-ttu-id="dd55e-134">輸入增強式密碼。</span><span class="sxs-lookup"><span data-stu-id="dd55e-134">Type a strong password.</span></span>  
  
4.  <span data-ttu-id="dd55e-135">指定要包含儲存之金鑰的檔案。</span><span class="sxs-lookup"><span data-stu-id="dd55e-135">Specify a file to contain the stored key.</span></span> [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="dd55e-136">會將 .snk 副檔名附加到這個檔案。</span><span class="sxs-lookup"><span data-stu-id="dd55e-136">appends a .snk file extension to the file.</span></span> <span data-ttu-id="dd55e-137">可以考慮將檔案儲存到磁碟上，使其與報表伺服器分開。</span><span class="sxs-lookup"><span data-stu-id="dd55e-137">Consider storing the file on a disk separate from the report server.</span></span>  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
####  <a name="back-up-encryption-keys--rskeymgmt-native-mode"></a><a name="bkmk_backup_rskeymgmt"></a><span data-ttu-id="dd55e-138">備份加密金鑰-rskeymgmt (原生模式) </span><span class="sxs-lookup"><span data-stu-id="dd55e-138">Back up encryption keys -rskeymgmt (Native Mode)</span></span>  
  
1.  <span data-ttu-id="dd55e-139">在主控報表伺服器的本機電腦上，執行 **[rskeymgmt.exe]** 。</span><span class="sxs-lookup"><span data-stu-id="dd55e-139">Run **rskeymgmt.exe** locally on the computer that hosts the report server.</span></span> <span data-ttu-id="dd55e-140">您必須使用 `-e` 擷取引數來複製金鑰、提供檔案名稱，並指定密碼。</span><span class="sxs-lookup"><span data-stu-id="dd55e-140">You must use the `-e` extract argument to copy the key, provide a file name, and specify a password.</span></span> <span data-ttu-id="dd55e-141">下列範例說明您必須指定的引數：</span><span class="sxs-lookup"><span data-stu-id="dd55e-141">The following example illustrates the arguments you must specify:</span></span>  
  
    ```cmd
    rskeymgmt -e -f d:\rsdbkey.snk -p<password>  
    ```  
  
## <a name="restore-encryption-keys"></a><span data-ttu-id="dd55e-142">還原加密金鑰</span><span class="sxs-lookup"><span data-stu-id="dd55e-142">Restore Encryption Keys</span></span>  
 <span data-ttu-id="dd55e-143">還原對稱金鑰會覆寫儲存在報表伺服器資料庫中的現有對稱金鑰。</span><span class="sxs-lookup"><span data-stu-id="dd55e-143">Restoring the symmetric key overwrites the existing symmetric key that is stored in the report server database.</span></span> <span data-ttu-id="dd55e-144">還原加密金鑰會以您先前儲存到磁碟的副本，取代無法使用的金鑰。</span><span class="sxs-lookup"><span data-stu-id="dd55e-144">Restoring an encryption key replaces an unusable key with a copy that you previously saved to disk.</span></span> <span data-ttu-id="dd55e-145">還原加密金鑰會導致下列動作：</span><span class="sxs-lookup"><span data-stu-id="dd55e-145">Restoring encryption keys results in the following actions:</span></span>  
  
-   <span data-ttu-id="dd55e-146">從密碼保護的備份檔案開啟對稱金鑰。</span><span class="sxs-lookup"><span data-stu-id="dd55e-146">The symmetric key is opened from the password protected backup file.</span></span>  
  
-   <span data-ttu-id="dd55e-147">使用報表伺服器 Windows 服務的公開金鑰，將對稱金鑰加密。</span><span class="sxs-lookup"><span data-stu-id="dd55e-147">The symmetric key is encrypted using the public key of the Report Server Windows service.</span></span>  
  
-   <span data-ttu-id="dd55e-148">將加密的對稱金鑰儲存在報表伺服器資料庫中。</span><span class="sxs-lookup"><span data-stu-id="dd55e-148">The encrypted symmetric key is stored in the report server database.</span></span>  
  
-   <span data-ttu-id="dd55e-149">刪除先前儲存的對稱金鑰資料 (例如，先前部署中已存在於報表伺服器資料庫中的金鑰資訊)。</span><span class="sxs-lookup"><span data-stu-id="dd55e-149">The previously stored symmetric key data (for example, key information that was already in the report server database from a previous deployment) is deleted.</span></span>  
  
 <span data-ttu-id="dd55e-150">若要還原加密金鑰，檔案上必須有一個加密金鑰的副本。</span><span class="sxs-lookup"><span data-stu-id="dd55e-150">To restore the encryption key, you must have a copy of the encryption key on file.</span></span> <span data-ttu-id="dd55e-151">您也必須知道解除鎖定儲存之副本的密碼。</span><span class="sxs-lookup"><span data-stu-id="dd55e-151">You must also know the password that unlocks the stored copy.</span></span> <span data-ttu-id="dd55e-152">如果您有金鑰和密碼，就可以執行 Reporting Services 組態工具或 **rskeymgmt** 公用程式來還原金鑰。</span><span class="sxs-lookup"><span data-stu-id="dd55e-152">If you have the key and the password, you can run the Reporting Services Configuration tool or **rskeymgmt** utility to restore the key.</span></span> <span data-ttu-id="dd55e-153">對稱金鑰必須和鎖定與解除鎖定目前儲存在報表伺服器資料庫中之加密資料的金鑰相同。</span><span class="sxs-lookup"><span data-stu-id="dd55e-153">The symmetric key must be the same one that locks and unlocks encrypted data currently stored in the report server database.</span></span> <span data-ttu-id="dd55e-154">如果您還原無效的副本，報表伺服器將無法存取目前儲存在報表伺服器資料庫中的加密資料。</span><span class="sxs-lookup"><span data-stu-id="dd55e-154">If you restore a copy that is not valid, the report server cannot access the encrypted data currently stored in the report server database.</span></span> <span data-ttu-id="dd55e-155">萬一發生這種情形，如果無法還原有效的金鑰，就必須刪除所有的加密值。</span><span class="sxs-lookup"><span data-stu-id="dd55e-155">If this occurs, you might need to delete all encrypted values if you cannot restore a valid key.</span></span> <span data-ttu-id="dd55e-156">如果因故無法還原加密金鑰 (例如，您若沒有備份副本)，則必須刪除現有的金鑰和加密內容。</span><span class="sxs-lookup"><span data-stu-id="dd55e-156">If for some reason you cannot restore the encryption key (for example, if you do not have a backup copy), you must delete the existing key and encrypted content.</span></span> <span data-ttu-id="dd55e-157">如需詳細資訊，請參閱[刪除和重新建立加密金鑰 &#40;SSRS 設定管理員&#41;](ssrs-encryption-keys-delete-and-re-create-encryption-keys.md)。</span><span class="sxs-lookup"><span data-stu-id="dd55e-157">For more information, see [Delete and Re-create Encryption Keys  &#40;SSRS Configuration Manager&#41;](ssrs-encryption-keys-delete-and-re-create-encryption-keys.md).</span></span> <span data-ttu-id="dd55e-158">如需建立對稱金鑰的詳細資訊，請參閱[初始化報表伺服器 &#40;SSRS 組態管理員&#41;](ssrs-encryption-keys-initialize-a-report-server.md)。</span><span class="sxs-lookup"><span data-stu-id="dd55e-158">For more information about creating symmetric keys, see [Initialize a Report Server &#40;SSRS Configuration Manager&#41;](ssrs-encryption-keys-initialize-a-report-server.md).</span></span>  
  
####  <a name="restore-encryption-keys--reporting-services-configuration-manager-native-mode"></a><a name="bkmk_restore_configuration_manager"></a><span data-ttu-id="dd55e-159">還原加密金鑰-Reporting Services 組態管理員 (原生模式) </span><span class="sxs-lookup"><span data-stu-id="dd55e-159">Restore encryption keys -Reporting Services Configuration Manager (Native Mode)</span></span>  
  
1.  <span data-ttu-id="dd55e-160">啟動 Reporting Services 組態管理員，然後連接到您要設定的報表伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="dd55e-160">Start the Reporting Services Configuration Manager, and then connect to the report server instance you want to configure.</span></span>  
  
2.  <span data-ttu-id="dd55e-161">在 [加密金鑰] 頁面上，按一下 [**還原**]。</span><span class="sxs-lookup"><span data-stu-id="dd55e-161">On the Encryption Keys page, click **Restore**.</span></span>  
  
3.  <span data-ttu-id="dd55e-162">選取包含備份副本的 .snk 檔案。</span><span class="sxs-lookup"><span data-stu-id="dd55e-162">Select the .snk file that contains the back up copy.</span></span>  
  
4.  <span data-ttu-id="dd55e-163">輸入解除檔案鎖定的密碼。</span><span class="sxs-lookup"><span data-stu-id="dd55e-163">Type the password that unlocks the file.</span></span>  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
####  <a name="restore-encryption-keys---rskeymgmt-native-mode"></a><a name="bkmk_restore_rskeymgmt"></a> <span data-ttu-id="dd55e-164">還原加密金鑰 - rskeymgmt (原生模式)</span><span class="sxs-lookup"><span data-stu-id="dd55e-164">Restore encryption keys - rskeymgmt (Native Mode)</span></span>  
  
1.  <span data-ttu-id="dd55e-165">在主控報表伺服器的本機電腦上，執行 **[rskeymgmt.exe]** 。</span><span class="sxs-lookup"><span data-stu-id="dd55e-165">Run **rskeymgmt.exe** locally on the computer that hosts the report server.</span></span> <span data-ttu-id="dd55e-166">使用 `-a` 引數還原金鑰。</span><span class="sxs-lookup"><span data-stu-id="dd55e-166">Use the `-a` argument to restore the keys.</span></span> <span data-ttu-id="dd55e-167">您必須提供完整的檔案名稱，並指定密碼。</span><span class="sxs-lookup"><span data-stu-id="dd55e-167">You must provide a fully-qualified file name and specify a password.</span></span> <span data-ttu-id="dd55e-168">下列範例說明您必須指定的引數：</span><span class="sxs-lookup"><span data-stu-id="dd55e-168">The following example illustrates the arguments you must specify:</span></span>  
  
    ```cmd
    rskeymgmt -a -f d:\rsdbkey.snk -p<password>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="dd55e-169">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dd55e-169">See Also</span></span>  
 [<span data-ttu-id="dd55e-170">設定和管理加密金鑰 &#40;SSRS 組態管理員&#41;</span><span class="sxs-lookup"><span data-stu-id="dd55e-170">Configure and Manage Encryption Keys &#40;SSRS Configuration Manager&#41;</span></span>](ssrs-encryption-keys-manage-encryption-keys.md)  
