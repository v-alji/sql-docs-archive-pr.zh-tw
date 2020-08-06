---
title: 備份資料庫 (備份選項頁面) | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
f1_keywords:
- sql12.swb.backupdatabase.options.f1
- swb.backupdatabase.options.f1
ms.assetid: df0ddcdb-c94e-472b-b786-469ae8117b93
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: ffd527ba4334244c7fd4c5d4a73099093cb8520b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606936"
---
# <a name="back-up-database-backup-options-page"></a><span data-ttu-id="1c909-102">備份資料庫 (備份選項頁面)</span><span class="sxs-lookup"><span data-stu-id="1c909-102">Back Up Database (Backup Options Page)</span></span>
  <span data-ttu-id="1c909-103">使用 [備份資料庫]  對話方塊的 [備份選項]  頁面，即可檢視或修改資料庫備份選項。</span><span class="sxs-lookup"><span data-stu-id="1c909-103">Use the  **Backup Options** page of the **Back Up Database** dialog box to view or modify database backup options.</span></span>  
  
 <span data-ttu-id="1c909-104">**若要使用 SQL Server Management Studio 建立備份**</span><span class="sxs-lookup"><span data-stu-id="1c909-104">**To create a backup by using SQL Server Management Studio**</span></span>  
  
-   [<span data-ttu-id="1c909-105">建立完整資料庫備份 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="1c909-105">Create a Full Database Backup &#40;SQL Server&#41;</span></span>](create-a-full-database-backup-sql-server.md)  
  
-   [<span data-ttu-id="1c909-106">建立差異資料庫備份 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="1c909-106">Create a Differential Database Backup &#40;SQL Server&#41;</span></span>](create-a-differential-database-backup-sql-server.md)  
  
> [!IMPORTANT]  
>  <span data-ttu-id="1c909-107">您可以定義資料庫維護計畫來建立資料庫備份。</span><span class="sxs-lookup"><span data-stu-id="1c909-107">You can define a database maintenance plan to create database backups.</span></span> <span data-ttu-id="1c909-108">如需詳細資訊，請參閱[維護計劃](../maintenance-plans/maintenance-plans.md)和[使用維護計畫精靈](../maintenance-plans/use-the-maintenance-plan-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="1c909-108">For more information, see [Maintenance Plans](../maintenance-plans/maintenance-plans.md) and [Use the Maintenance Plan Wizard](../maintenance-plans/use-the-maintenance-plan-wizard.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1c909-109">使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 指定備份工作時，您可以按下 [指令碼]  按鈕，然後選取指令碼的目的地，以產生相對應的 [!INCLUDE[tsql](../../includes/tsql-md.md)][BACKUP](/sql/t-sql/statements/backup-transact-sql) 指令碼。</span><span class="sxs-lookup"><span data-stu-id="1c909-109">When you specify a backup task by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], you can generate the corresponding [!INCLUDE[tsql](../../includes/tsql-md.md)][BACKUP](/sql/t-sql/statements/backup-transact-sql) script by clicking the **Script** button and then selecting a destination for the script.</span></span>  
  
## <a name="options"></a><span data-ttu-id="1c909-110">選項。</span><span class="sxs-lookup"><span data-stu-id="1c909-110">Options</span></span>  
  
### <a name="backup-set"></a><span data-ttu-id="1c909-111">備份組</span><span class="sxs-lookup"><span data-stu-id="1c909-111">Backup set</span></span>  
 <span data-ttu-id="1c909-112">[備份組]  面板的選項可以讓您指定與備份作業建立之備份組相關的選擇性資訊。</span><span class="sxs-lookup"><span data-stu-id="1c909-112">The options of the **Backup set** panel allow for you to specify optional information about the backup set created by the back up operation.</span></span>  
  
 <span data-ttu-id="1c909-113">**名稱**</span><span class="sxs-lookup"><span data-stu-id="1c909-113">**Name**</span></span>  
 <span data-ttu-id="1c909-114">指定備份組名稱。</span><span class="sxs-lookup"><span data-stu-id="1c909-114">Specify the backup set name.</span></span> <span data-ttu-id="1c909-115">系統會根據資料庫名稱與備份類型自動建議預設名稱。</span><span class="sxs-lookup"><span data-stu-id="1c909-115">The system automatically suggests a default name based on the database name and the backup type.</span></span>  
  
 <span data-ttu-id="1c909-116">如需備份組的相關資訊，請參閱[媒體集、媒體家族與備份組 &#40;SQL Server&#41;](media-sets-media-families-and-backup-sets-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="1c909-116">For information about backup sets, see [Media Sets, Media Families, and Backup Sets &#40;SQL Server&#41;](media-sets-media-families-and-backup-sets-sql-server.md).</span></span>  
  
 <span data-ttu-id="1c909-117">**說明**</span><span class="sxs-lookup"><span data-stu-id="1c909-117">**Description**</span></span>  
 <span data-ttu-id="1c909-118">輸入備份組的描述。</span><span class="sxs-lookup"><span data-stu-id="1c909-118">Enter a description of the backup set.</span></span>  
  
 <span data-ttu-id="1c909-119">**備份組逾期時間**</span><span class="sxs-lookup"><span data-stu-id="1c909-119">**Backup set will expire**</span></span>  
 <span data-ttu-id="1c909-120">選擇下列逾期選項其中之一。</span><span class="sxs-lookup"><span data-stu-id="1c909-120">Choose one of the following expiration options.</span></span> <span data-ttu-id="1c909-121">如果選擇 [URL]  作為備份目的地，便會停用此選項。</span><span class="sxs-lookup"><span data-stu-id="1c909-121">This option is disabled if **URL** is chosen as the backup destination.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="1c909-122">**之後**</span><span class="sxs-lookup"><span data-stu-id="1c909-122">**After**</span></span>|<span data-ttu-id="1c909-123">指定必須經過多少天之後，這個備份組才會逾期而能夠覆寫。</span><span class="sxs-lookup"><span data-stu-id="1c909-123">Specify the number of days that must elapse before this backup set expires and can be overwritten.</span></span> <span data-ttu-id="1c909-124">這個值可以介於 0 到 99999 日之間；值為 0 日意指備份組永遠不會過期。</span><span class="sxs-lookup"><span data-stu-id="1c909-124">This value can be from 0 to 99999 days; a value of 0 days means that the backup set will never expire.</span></span><br /><br /> <span data-ttu-id="1c909-125">備份逾期的預設值是設定在 [預設備份媒體保留期限 (以天為單位)]  選項中的值。</span><span class="sxs-lookup"><span data-stu-id="1c909-125">The default value for backup expiration is the value set in the **Default backup media retention (in days)** option.</span></span> <span data-ttu-id="1c909-126">若要存取，請以滑鼠右鍵按一下 [物件總管] 中的伺服器名稱並選取 [屬性]  ；然後按一下 [伺服器屬性]  對話方塊的 [資料庫設定]  頁面。</span><span class="sxs-lookup"><span data-stu-id="1c909-126">To access this, right-click the server name in Object Explorer and select **Properties**; then click the **Database Settings** page of the **Server Properties** dialog box.</span></span>|  
|<span data-ttu-id="1c909-127">**開啟**</span><span class="sxs-lookup"><span data-stu-id="1c909-127">**On**</span></span>|<span data-ttu-id="1c909-128">指定備份組過期而可以被覆寫的特定日期。</span><span class="sxs-lookup"><span data-stu-id="1c909-128">Specify a specific date when the backup set expires and can be overwritten.</span></span>|  
  
### <a name="compression"></a><span data-ttu-id="1c909-129">壓縮</span><span class="sxs-lookup"><span data-stu-id="1c909-129">Compression</span></span>  
 [!INCLUDE[ssEnterpriseEd10](../../../includes/ssenterpriseed10-md.md)] <span data-ttu-id="1c909-130">(或更新版本) 支援 [備份壓縮](backup-compression-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="1c909-130">(or a later version) supports [backup compression](backup-compression-sql-server.md).</span></span>  
  
 <span data-ttu-id="1c909-131">**設定備份壓縮**</span><span class="sxs-lookup"><span data-stu-id="1c909-131">**Set backup compression**</span></span>  
 <span data-ttu-id="1c909-132">在 [!INCLUDE[ssEnterpriseEd10](../../../includes/ssenterpriseed10-md.md)] (或更新的版本) 中，選取下列其中一個備份壓縮值：</span><span class="sxs-lookup"><span data-stu-id="1c909-132">In [!INCLUDE[ssEnterpriseEd10](../../../includes/ssenterpriseed10-md.md)] (or a later version), select one of the following backup compression values:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="1c909-133">**使用預設伺服器設定**</span><span class="sxs-lookup"><span data-stu-id="1c909-133">**Use the default server setting**</span></span>|<span data-ttu-id="1c909-134">按一下即可使用伺服器層級的預設值。</span><span class="sxs-lookup"><span data-stu-id="1c909-134">Click to use the server-level default.</span></span><br /><br /> <span data-ttu-id="1c909-135">此預設值是由 [備份壓縮預設] 伺服器組態選項所設定。</span><span class="sxs-lookup"><span data-stu-id="1c909-135">This default is set by the **backup compression default** server-configuration option.</span></span> <span data-ttu-id="1c909-136">有關如何檢視這個選項目前之設定的詳細資訊，請參閱 [檢視或設定備份壓縮預設伺服器組態選項](../../database-engine/configure-windows/view-or-configure-the-backup-compression-default-server-configuration-option.md)。</span><span class="sxs-lookup"><span data-stu-id="1c909-136">For information about how to view the current setting of this option, see [View or Configure the backup compression default Server Configuration Option](../../database-engine/configure-windows/view-or-configure-the-backup-compression-default-server-configuration-option.md).</span></span>|  
|<span data-ttu-id="1c909-137">**壓縮備份**</span><span class="sxs-lookup"><span data-stu-id="1c909-137">**Compress backup**</span></span>|<span data-ttu-id="1c909-138">不論目前的伺服器層級預設值為何，按一下即可壓縮備份。</span><span class="sxs-lookup"><span data-stu-id="1c909-138">Click to compress the backup, regardless of the server-level default.</span></span><br /><br /> <span data-ttu-id="1c909-139">**\*\* 重要 \*\*** 根據預設，壓縮會大幅增加 CPU 使用量，而且壓縮程序所耗用的額外 CPU 可能會對並行作業造成不良的影響。</span><span class="sxs-lookup"><span data-stu-id="1c909-139">**\*\* Important \*\*** By default, compression significantly increases CPU usage, and the additional CPU consumed by the compression process might adversely impact concurrent operations.</span></span> <span data-ttu-id="1c909-140">因此，您可能會想要在由[資源管理員](../resource-governor/resource-governor.md)所限制之 CPU 使用量的工作階段中建立低優先權的壓縮備份。</span><span class="sxs-lookup"><span data-stu-id="1c909-140">Therefore, you might want to create low-priority compressed backups in a session whose CPU usage is limited by [Resource Governor](../resource-governor/resource-governor.md).</span></span> <span data-ttu-id="1c909-141">如需詳細資訊，請參閱本主題稍後介紹的＜ [使用資源管理員進行備份壓縮，以限制 CPU 使用率 &#40;Transact-SQL&#41;](use-resource-governor-to-limit-cpu-usage-by-backup-compression-transact-sql.md)限制的工作階段中，建立低優先權的壓縮備份。</span><span class="sxs-lookup"><span data-stu-id="1c909-141">For more information, see [Use Resource Governor to Limit CPU Usage by Backup Compression &#40;Transact-SQL&#41;](use-resource-governor-to-limit-cpu-usage-by-backup-compression-transact-sql.md).</span></span>|  
|<span data-ttu-id="1c909-142">**不要壓縮備份**</span><span class="sxs-lookup"><span data-stu-id="1c909-142">**Do not compress backup**</span></span>|<span data-ttu-id="1c909-143">不論目前的伺服器層級預設值為何，按一下即可建立未壓縮備份。</span><span class="sxs-lookup"><span data-stu-id="1c909-143">Click to create an uncompressed backup, regardless of the server-level default.</span></span>|  
  
### <a name="encryption"></a><span data-ttu-id="1c909-144">加密</span><span class="sxs-lookup"><span data-stu-id="1c909-144">Encryption</span></span>  
 <span data-ttu-id="1c909-145">若要建立加密的備份，請核取 [加密備份]  核取方塊。</span><span class="sxs-lookup"><span data-stu-id="1c909-145">To create an encrypted backup, check the **Encrypt backup** check box.</span></span> <span data-ttu-id="1c909-146">選取要加密步驟所要使用的加密演算法，並提供現有憑證或非對稱金鑰清單中的憑證或非對稱金鑰。</span><span class="sxs-lookup"><span data-stu-id="1c909-146">Select an encryption algorithm to use for the encryption step, and provide a Certificate or Asymmetric key from a list of existing certificates or asymmetric keys.</span></span> <span data-ttu-id="1c909-147">可用於加密的演算法包括：</span><span class="sxs-lookup"><span data-stu-id="1c909-147">The available algorithms for encryption are:</span></span>  
  
-   <span data-ttu-id="1c909-148">AES 128</span><span class="sxs-lookup"><span data-stu-id="1c909-148">AES 128</span></span>  
  
-   <span data-ttu-id="1c909-149">AES 192</span><span class="sxs-lookup"><span data-stu-id="1c909-149">AES 192</span></span>  
  
-   <span data-ttu-id="1c909-150">AES 256</span><span class="sxs-lookup"><span data-stu-id="1c909-150">AES 256</span></span>  
  
-   <span data-ttu-id="1c909-151">三重 DES</span><span class="sxs-lookup"><span data-stu-id="1c909-151">Triple DES</span></span>  
  
> [!TIP]  
>  <span data-ttu-id="1c909-152">如果選擇附加至現有的備份集，則會停用加密選項。</span><span class="sxs-lookup"><span data-stu-id="1c909-152">The encryption option is disabled if you selected to append to existing backup set.</span></span>  
>   
>  <span data-ttu-id="1c909-153">這建議作法是讓您備份憑證或金鑰，並將其儲存在不同位置，而不是加密備份。</span><span class="sxs-lookup"><span data-stu-id="1c909-153">It is recommended practice to back up your certificate or keys and store them in a different location than the backup you encrypted.</span></span>  
>   
>  <span data-ttu-id="1c909-154">僅支援位於可延伸金鑰管理 (EKM) 中的金鑰。</span><span class="sxs-lookup"><span data-stu-id="1c909-154">Only keys residing in the Extensible Key Management (EKM) are supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c909-155">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1c909-155">See Also</span></span>  
 <span data-ttu-id="1c909-156">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="1c909-156">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 <span data-ttu-id="1c909-157">[備份交易記錄 &#40;SQL Server&#41;](back-up-a-transaction-log-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="1c909-157">[Back Up a Transaction Log &#40;SQL Server&#41;](back-up-a-transaction-log-sql-server.md) </span></span>  
 <span data-ttu-id="1c909-158">[備份檔案和檔案群組 &#40;SQL Server&#41;](back-up-files-and-filegroups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="1c909-158">[Back Up Files and Filegroups &#40;SQL Server&#41;](back-up-files-and-filegroups-sql-server.md) </span></span>  
 [<span data-ttu-id="1c909-159">資料庫損毀時備份交易記錄 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="1c909-159">Back Up the Transaction Log When the Database Is Damaged &#40;SQL Server&#41;</span></span>](back-up-the-transaction-log-when-the-database-is-damaged-sql-server.md)  
  
  
