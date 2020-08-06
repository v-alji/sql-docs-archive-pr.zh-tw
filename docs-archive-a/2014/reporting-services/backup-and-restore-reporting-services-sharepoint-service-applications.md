---
title: 備份和還原 Reporting Services SharePoint 服務應用程式 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: dfb4ed77-90e5-4273-b690-89a945508ed2
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 488659d269542381be9bcf1b1b6115acf89f8a98
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595816"
---
# <a name="backup-and-restore-reporting-services-sharepoint-service-applications"></a><span data-ttu-id="9d7f5-102">備份與還原 Reporting Services SharePoint 服務應用程式</span><span class="sxs-lookup"><span data-stu-id="9d7f5-102">Backup and Restore Reporting Services SharePoint Service Applications</span></span>
  <span data-ttu-id="9d7f5-103">本主題描述如何使用 SharePoint 管理中心或 PowerShell 備份和還原 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 服務應用程式。</span><span class="sxs-lookup"><span data-stu-id="9d7f5-103">This topic describes how to backup and restore a [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] services application using SharePoint Central Administration or PowerShell.</span></span> <span data-ttu-id="9d7f5-104">本主題包含：</span><span class="sxs-lookup"><span data-stu-id="9d7f5-104">The topic contains:</span></span>  
  
-   [<span data-ttu-id="9d7f5-105">限制事項</span><span class="sxs-lookup"><span data-stu-id="9d7f5-105">Limitations and Restrictions</span></span>](#bkmk_Restrictions)  
  
-   [<span data-ttu-id="9d7f5-106">備份服務應用程式</span><span class="sxs-lookup"><span data-stu-id="9d7f5-106">Backup The Service application</span></span>](#bkmk_backup)  
  
-   [<span data-ttu-id="9d7f5-107">還原服務應用程式</span><span class="sxs-lookup"><span data-stu-id="9d7f5-107">Restore the Service Application</span></span>](#bkmk_restore)  
  
##  <a name="before-you-begin"></a><a name="bkmk_BeforeYouBegin"></a> <span data-ttu-id="9d7f5-108">開始之前</span><span class="sxs-lookup"><span data-stu-id="9d7f5-108">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="bkmk_Restrictions"></a> <span data-ttu-id="9d7f5-109">限制事項</span><span class="sxs-lookup"><span data-stu-id="9d7f5-109">Limitations and Restrictions</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9d7f5-110">使用 SharePoint 備份和還原功能，就可以部分備份和還原 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 服務應用程式。</span><span class="sxs-lookup"><span data-stu-id="9d7f5-110">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] service applications can partially be backed up and restored using the SharePoint backup and restore functionality.</span></span> <span data-ttu-id="9d7f5-111">**需要執行其他步驟** ，且這些步驟記錄在本主題中。</span><span class="sxs-lookup"><span data-stu-id="9d7f5-111">**Additional steps are required** and the steps are documented in this topic.</span></span> <span data-ttu-id="9d7f5-112">目前備份程序 **不會** 將自動執行帳戶 (UEA) 或 Windows 驗證的加密金鑰和認證備份至 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 資料庫。</span><span class="sxs-lookup"><span data-stu-id="9d7f5-112">Currently the backup process **does not** backup encryption keys and credentials for unattended execution accounts (UEA) or windows authentication to the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] database.</span></span>  
  
###  <a name="recommendations"></a><a name="bkmk_recommendations"></a> <span data-ttu-id="9d7f5-113">建議</span><span class="sxs-lookup"><span data-stu-id="9d7f5-113">Recommendations</span></span>  
  
-   <span data-ttu-id="9d7f5-114">開始 SharePoint 備份之前，請先備份加密金鑰。</span><span class="sxs-lookup"><span data-stu-id="9d7f5-114">Backup the encryption keys before starting the SharePoint backup.</span></span> <span data-ttu-id="9d7f5-115">如果您未備份加密金鑰，則在還原服務應用程式之後，將無法存取加密的資料。</span><span class="sxs-lookup"><span data-stu-id="9d7f5-115">If you do not backup the encryption keys, then you will not be able to access your encrypted data, following the restore of the service application.</span></span> <span data-ttu-id="9d7f5-116">您將需要刪除加密的資料。</span><span class="sxs-lookup"><span data-stu-id="9d7f5-116">You will need to delete your encrypted data.</span></span>  
  
-   <span data-ttu-id="9d7f5-117">請確認您的 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 服務應用程式是否使用 UEA 或 Windows 驗證進行資料庫存取。</span><span class="sxs-lookup"><span data-stu-id="9d7f5-117">Verify if your [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] service application is using UEA or Windows authentication for database access.</span></span> <span data-ttu-id="9d7f5-118">如果是使用其中一種方式，請確定正確的認證為何，如此就能在還原程序之後正確設定服務應用程式。</span><span class="sxs-lookup"><span data-stu-id="9d7f5-118">If it is using either, verify what the proper credentials are so you can correctly configure the service application after the restore process.</span></span>  
  
-   <span data-ttu-id="9d7f5-119">檢閱 SharePoint 備份記錄確實是在備份檔案所在的資料夾中建立。</span><span class="sxs-lookup"><span data-stu-id="9d7f5-119">Review the SharePoint backup log is created in the same folder as the backup file.</span></span> <span data-ttu-id="9d7f5-120">這個檔案通常命名為 **spbackup.log**</span><span class="sxs-lookup"><span data-stu-id="9d7f5-120">The file is typically named **spbackup.log**</span></span>  
  
##  <a name="backup-the-service-application"></a><a name="bkmk_backup"></a><span data-ttu-id="9d7f5-121">備份服務應用程式</span><span class="sxs-lookup"><span data-stu-id="9d7f5-121">Backup The Service application</span></span>  
 <span data-ttu-id="9d7f5-122">依序完成下列步驟：</span><span class="sxs-lookup"><span data-stu-id="9d7f5-122">Complete the following steps in order:</span></span>  
  
1.  <span data-ttu-id="9d7f5-123">備份加密金鑰</span><span class="sxs-lookup"><span data-stu-id="9d7f5-123">Backup the encryption keys</span></span>  
  
2.  <span data-ttu-id="9d7f5-124">備份服務應用程式</span><span class="sxs-lookup"><span data-stu-id="9d7f5-124">Backup the Service application</span></span>  
  
3.  <span data-ttu-id="9d7f5-125">確認您的服務應用程式是否使用 UEA 或 Windows 驗證進行資料庫存取。</span><span class="sxs-lookup"><span data-stu-id="9d7f5-125">Verify if you service application uses an UEA or Windows authentication for database access.</span></span> <span data-ttu-id="9d7f5-126">如果是的話，請記下認證，以便在還原服務應用程式之後使用認證進行設定。</span><span class="sxs-lookup"><span data-stu-id="9d7f5-126">If it does, make a note of the credentials so you can use them to configure the service application after it is restored.</span></span>  
  
### <a name="backup-the-encryption-keys-using-central-administration"></a><span data-ttu-id="9d7f5-127">使用管理中心備份加密金鑰</span><span class="sxs-lookup"><span data-stu-id="9d7f5-127">Backup the Encryption Keys using Central Administration</span></span>  
 <span data-ttu-id="9d7f5-128">如需備份 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 加密金鑰的資訊，請參閱[管理 Reporting Services SharePoint 服務應用程式](../../2014/reporting-services/manage-a-reporting-services-sharepoint-service-application.md)的＜加密金鑰＞一節。</span><span class="sxs-lookup"><span data-stu-id="9d7f5-128">For information on backing up the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] encryption keys, see the "Encryption Keys" section of [Manage a Reporting Services SharePoint Service Application](../../2014/reporting-services/manage-a-reporting-services-sharepoint-service-application.md).</span></span>  
  
###  <a name="backup-the-service-application-using-sharepoint-central-administration"></a><a name="bkmk_centraladmin"></a><span data-ttu-id="9d7f5-129">使用 SharePoint 管理中心備份服務應用程式</span><span class="sxs-lookup"><span data-stu-id="9d7f5-129">Backup the Service application Using SharePoint Central Administration</span></span>  
 <span data-ttu-id="9d7f5-130">若要備份服務應用程式，請完成下列步驟：</span><span class="sxs-lookup"><span data-stu-id="9d7f5-130">To back up the Service Application, complete the following steps:</span></span>  
  
1.  <span data-ttu-id="9d7f5-131">在 [SharePoint 管理中心] 中，按一下 **[備份與還原]** 群組中的 **[執行備份]** 。</span><span class="sxs-lookup"><span data-stu-id="9d7f5-131">In SharePoint Central Administration Click **Perform a backup** in the **Backup and Restore** group.</span></span>  
  
2.  <span data-ttu-id="9d7f5-132">在 **[共用服務]** 節點底下，展開 **[共用服務應用程式]** ，然後選取您的服務應用程式。</span><span class="sxs-lookup"><span data-stu-id="9d7f5-132">Under the **Shared Services** node, expand **Shared Service Applications** and select your service application.</span></span> <span data-ttu-id="9d7f5-133">其類型會是 **[SQL Server Reporting Services 服務應用程式]**。</span><span class="sxs-lookup"><span data-stu-id="9d7f5-133">It will have a type of **SQL Server Reporting Services Service Application**.</span></span>  
  
3.  <span data-ttu-id="9d7f5-134">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="9d7f5-134">Click **Next**.</span></span>  
  
4.  <span data-ttu-id="9d7f5-135">輸入 **[備份位置:]** 的路徑，然後按一下 **[開始備份]**。</span><span class="sxs-lookup"><span data-stu-id="9d7f5-135">Type the path for the **Backup location:** and click **Start Backup**</span></span>  
  
5.  <span data-ttu-id="9d7f5-136">重複上述程序，但是不要選取服務應用程式，而是展開 **[共用服務 Proxy]** 節點，然後選取服務應用程式 Proxy。</span><span class="sxs-lookup"><span data-stu-id="9d7f5-136">Repeat the process above but instead of selecting the service application, expand the **Shared Services Proxies** node, and select service application proxy.</span></span> <span data-ttu-id="9d7f5-137">其類型會是 **[SQL Server Reporting Services 服務應用程式 Proxy]**。</span><span class="sxs-lookup"><span data-stu-id="9d7f5-137">It will have a type of **SQL Server Reporting Services Service Application Proxy**.</span></span>  
  
 <span data-ttu-id="9d7f5-138">如需詳細資訊，請參閱 SharePoint 文件中的下列主題：</span><span class="sxs-lookup"><span data-stu-id="9d7f5-138">For more information, see the following topics in the SharePoint documentation:</span></span>  
  
 <span data-ttu-id="9d7f5-139">SharePoint 文件中的[備份服務應用程式 (SharePoint Foundation 2010)](https://msdn.microsoft.com/library/ee748601.aspx)。</span><span class="sxs-lookup"><span data-stu-id="9d7f5-139">[Back up a service application (SharePoint Foundation 2010) in the SharePoint documenttation](https://msdn.microsoft.com/library/ee748601.aspx).</span></span>  
  
 [<span data-ttu-id="9d7f5-140">備份服務應用程式 (SharePoint Server 2010)</span><span class="sxs-lookup"><span data-stu-id="9d7f5-140">Back up a service application (SharePoint Server 2010)</span></span>](https://technet.microsoft.com/library/ee428318.aspx)  
  
### <a name="verify-execution-account-and-database-authentication"></a><span data-ttu-id="9d7f5-141">驗證執行帳戶和資料庫驗證</span><span class="sxs-lookup"><span data-stu-id="9d7f5-141">Verify Execution Account and Database Authentication</span></span>  
 <span data-ttu-id="9d7f5-142">**執行帳戶** ：若要驗證您的服務應用程式是否使用執行帳戶：</span><span class="sxs-lookup"><span data-stu-id="9d7f5-142">**Execution Account:** To verify if your service application is using an execution account:</span></span>  
  
1.  <span data-ttu-id="9d7f5-143">在 SharePoint 管理中心內，按一下 [**應用程式管理**] 群組中的 [**管理服務應用程式**]。</span><span class="sxs-lookup"><span data-stu-id="9d7f5-143">In SharePoint Central Administration, click **Manage Service Applications** in the **Application Management** group.</span></span>  
  
2.  <span data-ttu-id="9d7f5-144">按一下服務應用程式的名稱，然後按一下 SharePoint 功能區中的 [**管理**]。</span><span class="sxs-lookup"><span data-stu-id="9d7f5-144">Click the name of your service application and then click **Manage** in the SharePoint Ribbon.</span></span>  
  
3.  <span data-ttu-id="9d7f5-145">按一下 **[執行帳戶]**。</span><span class="sxs-lookup"><span data-stu-id="9d7f5-145">Click **Execution Account**.</span></span>  
  
4.  <span data-ttu-id="9d7f5-146">如果設定了執行帳戶，則在還原服務應用程式備份時需要知道認證。</span><span class="sxs-lookup"><span data-stu-id="9d7f5-146">If an execution account is configured, you need to know the credentials when it is time to restore the service application backup.</span></span> <span data-ttu-id="9d7f5-147">如果不知道正確的認證，請不要進行備份和還原程序。</span><span class="sxs-lookup"><span data-stu-id="9d7f5-147">Do not proceed with the backup and restore procedure until you know the correct credentials.</span></span>  
  
 <span data-ttu-id="9d7f5-148">**資料庫驗證** ：若要確認您的服務應用程式是否使用 Windows 驗證進行資料庫驗證：</span><span class="sxs-lookup"><span data-stu-id="9d7f5-148">**Database Authentication:** To verify if your service application is using Windows Authentication for the database authentication:</span></span>  
  
1.  <span data-ttu-id="9d7f5-149">在 SharePoint 管理中心內，按一下 [**應用程式管理**] 群組中的 [**管理服務應用程式**]。</span><span class="sxs-lookup"><span data-stu-id="9d7f5-149">In SharePoint Central Administration, click **Manage Service Applications** in the **Application Management** group.</span></span>  
  
2.  <span data-ttu-id="9d7f5-150">按一下服務應用程式的名稱，然後按一下 SharePoint 功能區中的 **[屬性]** 。</span><span class="sxs-lookup"><span data-stu-id="9d7f5-150">Click the name of your service application and then click **Properties** in the SharePoint Ribbon.</span></span>  
  
3.  <span data-ttu-id="9d7f5-151">檢閱 **[Reporting Services (SSRS) 服務資料庫]** 區段。</span><span class="sxs-lookup"><span data-stu-id="9d7f5-151">Review the **Reporting Services (SSRS) Service Database** section.</span></span>  
  
4.  <span data-ttu-id="9d7f5-152">如果設定了 Windows 驗證，則您必須知道認證，才能在還原之後設定服務應用程式。</span><span class="sxs-lookup"><span data-stu-id="9d7f5-152">If Windows Authentication is configured, you need to know the credentials so you can configure the service application after you restore it.</span></span> <span data-ttu-id="9d7f5-153">如果不知道正確的認證，請不要進行備份和還原程序。</span><span class="sxs-lookup"><span data-stu-id="9d7f5-153">Do not proceed with the backup and restore procedure until you know the correct credentials.</span></span>  
  
##  <a name="restore-the-service-application"></a><a name="bkmk_restore"></a><span data-ttu-id="9d7f5-154">還原服務應用程式</span><span class="sxs-lookup"><span data-stu-id="9d7f5-154">Restore the Service Application</span></span>  
 <span data-ttu-id="9d7f5-155">依序完成下列步驟：</span><span class="sxs-lookup"><span data-stu-id="9d7f5-155">Complete the following steps in order:</span></span>  
  
1.  <span data-ttu-id="9d7f5-156">還原 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 服務應用程式。</span><span class="sxs-lookup"><span data-stu-id="9d7f5-156">Restore the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] service application.</span></span>  
  
2.  <span data-ttu-id="9d7f5-157">還原加密金鑰</span><span class="sxs-lookup"><span data-stu-id="9d7f5-157">Restore the encryption keys</span></span>  
  
3.  <span data-ttu-id="9d7f5-158">如果您的服務應用程式使用執行帳戶或 Windows 驗證進行資料庫存取，請設定認證。</span><span class="sxs-lookup"><span data-stu-id="9d7f5-158">If your service application was using an execution account or Windows authentication for database access, configure the credentials.</span></span>  
  
### <a name="restore-the-service-application-using-sharepoint-central-administration"></a><span data-ttu-id="9d7f5-159">使用 SharePoint 管理中心還原服務應用程式</span><span class="sxs-lookup"><span data-stu-id="9d7f5-159">Restore the Service application Using SharePoint Central Administration</span></span>  
  
1.  <span data-ttu-id="9d7f5-160">在 [SharePoint 管理中心] 中，按一下 **[備份與還原]** 群組中的 **[從備份還原]** 。</span><span class="sxs-lookup"><span data-stu-id="9d7f5-160">In SharePoint Central Administration Click **Restore from a backup** in the **Backup and Restore** group.</span></span>  
  
2.  <span data-ttu-id="9d7f5-161">在 **[備份目錄位置]** 方塊中輸入備份檔案的路徑，然後按一下 **[重新整理]**。</span><span class="sxs-lookup"><span data-stu-id="9d7f5-161">Type the path to your backup file in **Backup Directory Location** box and click **Refresh**.</span></span>  
  
3.  <span data-ttu-id="9d7f5-162">從 **[上層元件]** 清單中選取服務應用程式備份，然後按 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="9d7f5-162">Select your service application backup from the **Top Component** list and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="9d7f5-163">選取您的 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 應用程式，然後按 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="9d7f5-163">Select your [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] application and then click **Next**.</span></span>  
  
5.  <span data-ttu-id="9d7f5-164">在 **[登錄名稱與密碼]** 區段中，輸入登入名稱的密碼。</span><span class="sxs-lookup"><span data-stu-id="9d7f5-164">In the **Login Names and Passwords** section type the password for the login name.</span></span> <span data-ttu-id="9d7f5-165">[登入名稱] 方塊應填入服務應用程式在備份之前使用的登入。</span><span class="sxs-lookup"><span data-stu-id="9d7f5-165">The login name box should be populated with the login the service application was using prior to the backup.</span></span>  
  
6.  <span data-ttu-id="9d7f5-166">按一下 **[開始還原]**。</span><span class="sxs-lookup"><span data-stu-id="9d7f5-166">Click **Start Restore**.</span></span>  
  
7.  <span data-ttu-id="9d7f5-167">重複上述程序，但是不要還原服務應用程式，而是展開 **[共用服務]** 節點，然後展開 **[共用服務應用程式]** 節點。</span><span class="sxs-lookup"><span data-stu-id="9d7f5-167">Repeat the process above but instead of restoring the service application, expand the **Shared Services** node and then expand the **Shared Service Applications** node.</span></span>  
  
 <span data-ttu-id="9d7f5-168">如需詳細資訊，請參閱 SharePoint 文件中的下列主題：</span><span class="sxs-lookup"><span data-stu-id="9d7f5-168">For more information, see the following topics in the SharePoint documentation:</span></span>  
  
 <span data-ttu-id="9d7f5-169">[還原服務應用程式 (SharePoint Foundation 2010)](https://msdn.microsoft.com/library/ee748615.aspx)。</span><span class="sxs-lookup"><span data-stu-id="9d7f5-169">[Restore a service application (SharePoint Foundation 2010)](https://msdn.microsoft.com/library/ee748615.aspx).</span></span>  
  
 <span data-ttu-id="9d7f5-170">[Restore a service application (SharePoint Server 2010)](https://technet.microsoft.com/library/ee428305.aspx)(還原服務應用程式 (SharePoint Server 2010))。</span><span class="sxs-lookup"><span data-stu-id="9d7f5-170">[Restore a service application (SharePoint Server 2010)](https://technet.microsoft.com/library/ee428305.aspx).</span></span>  
  
### <a name="restore-the-encryption-keys-using-central-administration"></a><span data-ttu-id="9d7f5-171">使用管理中心還原加密金鑰</span><span class="sxs-lookup"><span data-stu-id="9d7f5-171">Restore the Encryption Keys using Central Administration</span></span>  
 <span data-ttu-id="9d7f5-172">如需還原 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 加密金鑰的資訊，請參閱[管理 Reporting Services SharePoint 服務應用程式](../../2014/reporting-services/manage-a-reporting-services-sharepoint-service-application.md)的＜加密金鑰＞一節。</span><span class="sxs-lookup"><span data-stu-id="9d7f5-172">For information on restoring the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] encryption keys, see the "Encryption Keys" section of [Manage a Reporting Services SharePoint Service Application](../../2014/reporting-services/manage-a-reporting-services-sharepoint-service-application.md).</span></span>  
  
### <a name="configure-the-execution-account-and-database-authentication"></a><span data-ttu-id="9d7f5-173">設定執行帳戶和資料庫驗證</span><span class="sxs-lookup"><span data-stu-id="9d7f5-173">Configure the Execution Account and Database Authentication</span></span>  
 <span data-ttu-id="9d7f5-174">**執行帳戶** ：如果您的服務應用程式使用執行帳戶，請完成下列步驟設定該帳戶：</span><span class="sxs-lookup"><span data-stu-id="9d7f5-174">**Execution Account:** If your service application was using an execution account complete the following steps to configure it:</span></span>  
  
1.  <span data-ttu-id="9d7f5-175">在 SharePoint 管理中心內，按一下 [**應用程式管理**] 群組中的 [**管理服務應用程式**]。</span><span class="sxs-lookup"><span data-stu-id="9d7f5-175">In SharePoint Central Administration, click **Manage Service Applications** in the **Application Management** group.</span></span>  
  
2.  <span data-ttu-id="9d7f5-176">按一下服務應用程式的名稱，然後按一下 SharePoint 功能區中的 [**管理**]。</span><span class="sxs-lookup"><span data-stu-id="9d7f5-176">Click the name of your service application and then click **Manage** in the SharePoint Ribbon.</span></span>  
  
3.  <span data-ttu-id="9d7f5-177">按一下 **[執行帳戶]**。</span><span class="sxs-lookup"><span data-stu-id="9d7f5-177">Click **Execution Account**.</span></span>  
  
4.  <span data-ttu-id="9d7f5-178">輸入帳戶、密碼，然後選取 **[指定執行帳戶]** 方塊。</span><span class="sxs-lookup"><span data-stu-id="9d7f5-178">Type the account, password, and select the **Specify and Execution Account** box.</span></span>  
  
5.  <span data-ttu-id="9d7f5-179">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="9d7f5-179">Click **OK**.</span></span>  
  
 <span data-ttu-id="9d7f5-180">**資料庫驗證** ：如果您的服務應用程式使用 Windows 驗證進行資料庫驗證，請完成下列步驟：</span><span class="sxs-lookup"><span data-stu-id="9d7f5-180">**Database Authentication:** If your service application was using Windows Authentication for the database authentication complete the following steps:</span></span>  
  
1.  <span data-ttu-id="9d7f5-181">在 [SharePoint 管理中心] 中，按一下 [管理**應用程式管理**群組中的**服務應用程式**]。</span><span class="sxs-lookup"><span data-stu-id="9d7f5-181">In SharePoint Central Administration click **Manage Service Applications** in the **Application Management** group.</span></span>  
  
2.  <span data-ttu-id="9d7f5-182">按一下服務應用程式的名稱，然後按一下 SharePoint 功能區中的 **[屬性]** 。</span><span class="sxs-lookup"><span data-stu-id="9d7f5-182">Click the name of your service application and then click **Properties** in the SharePoint Ribbon.</span></span>  
  
3.  <span data-ttu-id="9d7f5-183">檢閱 **[Reporting Services (SSRS) 服務資料庫]** 區段。</span><span class="sxs-lookup"><span data-stu-id="9d7f5-183">Review the **Reporting Services (SSRS) Service Database** section.</span></span>  
  
4.  <span data-ttu-id="9d7f5-184">選取 **[Windows 驗證]**。</span><span class="sxs-lookup"><span data-stu-id="9d7f5-184">Select **Windows Authentication**.</span></span>  
  
5.  <span data-ttu-id="9d7f5-185">輸入帳戶和密碼。</span><span class="sxs-lookup"><span data-stu-id="9d7f5-185">Type the account and password.</span></span> <span data-ttu-id="9d7f5-186">選取 **[當做 Windows 認證使用]** (如果適用)。</span><span class="sxs-lookup"><span data-stu-id="9d7f5-186">Select **Use as Windows Credentials** if appropriate.</span></span>  
  
6.  <span data-ttu-id="9d7f5-187">按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="9d7f5-187">Click **Ok**</span></span>  
  
  
