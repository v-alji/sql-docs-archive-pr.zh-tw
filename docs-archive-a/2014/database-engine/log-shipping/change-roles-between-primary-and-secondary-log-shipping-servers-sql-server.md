---
title: 變更主要與次要記錄傳送伺服器間的角色 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- log shipping [SQL Server], role changes
- secondary data files [SQL Server], roles changed between
- primary databases [SQL Server]
- initial role changes [SQL Server]
- log shipping [SQL Server], failover
- failover [SQL Server], log shipping
ms.assetid: 2d7cc40a-47e8-4419-9b2b-7c69f700e806
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 52ddb89bfd18eef4cd2140bc67cf93d1800138f2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703254"
---
# <a name="change-roles-between-primary-and-secondary-log-shipping-servers-sql-server"></a><span data-ttu-id="3ce48-102">變更主要與次要記錄傳送伺服器間的角色 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="3ce48-102">Change Roles Between Primary and Secondary Log Shipping Servers (SQL Server)</span></span>
  <span data-ttu-id="3ce48-103">將 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 記錄傳送組態容錯移轉到次要伺服器之後，您可以設定次要資料庫做為主要資料庫。</span><span class="sxs-lookup"><span data-stu-id="3ce48-103">After you have failed over a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] log shipping configuration to a secondary server, you can configure your secondary database to act as the primary database.</span></span> <span data-ttu-id="3ce48-104">接著，您就可以視需要交換主要與次要資料庫。</span><span class="sxs-lookup"><span data-stu-id="3ce48-104">Then, you will be able to swap primary and secondary databases as needed.</span></span>  
  
## <a name="performing-the-initial-role-change"></a><span data-ttu-id="3ce48-105">執行初始角色變更</span><span class="sxs-lookup"><span data-stu-id="3ce48-105">Performing the Initial Role Change</span></span>  
 <span data-ttu-id="3ce48-106">初次想要容錯移轉到次要資料庫，並將它作為主要資料庫時，您必須採取一連串的步驟。</span><span class="sxs-lookup"><span data-stu-id="3ce48-106">The first time you want to fail over to the secondary database and make it your new primary database, there is a series of steps you must take.</span></span> <span data-ttu-id="3ce48-107">遵循並完成這些初始步驟之後，您就可以輕輕鬆鬆交換主要資料庫與次要資料庫間的角色。</span><span class="sxs-lookup"><span data-stu-id="3ce48-107">After you have followed these initial steps, you will be able to swap roles between the primary database and the secondary database easily.</span></span>  
  
1.  <span data-ttu-id="3ce48-108">從主要資料庫手動容錯移轉到次要資料庫。</span><span class="sxs-lookup"><span data-stu-id="3ce48-108">Manually fail over from the primary database to a secondary database.</span></span> <span data-ttu-id="3ce48-109">請確定要使用 NORECOVERY，在主要伺服器上備份使用中的交易記錄檔。</span><span class="sxs-lookup"><span data-stu-id="3ce48-109">Be sure to back up the active transaction log on your primary server with NORECOVERY.</span></span> <span data-ttu-id="3ce48-110">如需詳細資訊，請參閱 [容錯移轉至記錄傳送次要 &#40;SQL Server&#41;](fail-over-to-a-log-shipping-secondary-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="3ce48-110">For more information, see [Fail Over to a Log Shipping Secondary &#40;SQL Server&#41;](fail-over-to-a-log-shipping-secondary-sql-server.md).</span></span>  
  
2.  <span data-ttu-id="3ce48-111">停用原始主要伺服器上的記錄傳送備份作業，以及原始次要伺服器上的複製與還原作業。</span><span class="sxs-lookup"><span data-stu-id="3ce48-111">Disable the log shipping backup job on the original primary server, and the copy and restore jobs on the original secondary server.</span></span>  
  
3.  <span data-ttu-id="3ce48-112">在次要資料庫上 (要它作為新的主要資料庫)，使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 設定記錄傳送。</span><span class="sxs-lookup"><span data-stu-id="3ce48-112">On your secondary database (the database you want to be the new primary), configure log shipping using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="3ce48-113">如需詳細資訊，請參閱[設定記錄傳送 &#40;SQL Server&#41;](configure-log-shipping-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="3ce48-113">For more information, see [Configure Log Shipping &#40;SQL Server&#41;](configure-log-shipping-sql-server.md).</span></span> <span data-ttu-id="3ce48-114">包括以下步驟：</span><span class="sxs-lookup"><span data-stu-id="3ce48-114">Include the following steps:</span></span>  
  
    1.  <span data-ttu-id="3ce48-115">使用您已為原始主要伺服器建立的相同共用，來建立備份。</span><span class="sxs-lookup"><span data-stu-id="3ce48-115">Use the same share for creating backups that you created for the original primary server.</span></span>  
  
    2.  <span data-ttu-id="3ce48-116">新增次要資料庫時，請在 **[次要資料庫設定]** 對話方塊的 **[次要資料庫]** 方塊中，輸入原始的資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="3ce48-116">When adding the secondary database, in the **Secondary Database Settings** dialog box, enter the name of the original primary database in the **Secondary database** box.</span></span>  
  
    3.  <span data-ttu-id="3ce48-117">在 **[次要資料庫設定]** 對話方中，選取 **[否，次要資料庫已初始化]**。</span><span class="sxs-lookup"><span data-stu-id="3ce48-117">In the **Secondary Database Settings** dialog box, select **No, the secondary database is initialized**.</span></span>  
  
4.  <span data-ttu-id="3ce48-118">如果您先前的記錄傳送組態已啟用記錄傳送監視，請將記錄傳送監視重新設定為監視新的記錄傳送組態。</span><span class="sxs-lookup"><span data-stu-id="3ce48-118">If log shipping monitoring was enabled on your former log shipping configuration, reconfigure log shipping monitoring to monitor the new log shipping configuration.</span></span>  <span data-ttu-id="3ce48-119">執行下列命令，以資料庫的名稱取代 *database_name* ：</span><span class="sxs-lookup"><span data-stu-id="3ce48-119">Execute the following commands, replacing *database_name* with the name of your database:</span></span>  
  
    1.  <span data-ttu-id="3ce48-120">**在新的主要伺服器上**</span><span class="sxs-lookup"><span data-stu-id="3ce48-120">**On the new primary server**</span></span>  
  
         <span data-ttu-id="3ce48-121">執行下列 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式：</span><span class="sxs-lookup"><span data-stu-id="3ce48-121">Execute the following [!INCLUDE[tsql](../../includes/tsql-md.md)] statements:</span></span>  
  
        ```  
        -- Statement to execute on the new primary server  
        USE msdb  
        GO  
        EXEC master.dbo.sp_change_log_shipping_secondary_database @secondary_database = N'database_name', @threshold_alert_enabled = 0;  
        GO  
        ```  
  
    2.  <span data-ttu-id="3ce48-122">**在新的次要伺服器上**</span><span class="sxs-lookup"><span data-stu-id="3ce48-122">**On the new secondary server**</span></span>  
  
         <span data-ttu-id="3ce48-123">執行下列 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式：</span><span class="sxs-lookup"><span data-stu-id="3ce48-123">Execute the following [!INCLUDE[tsql](../../includes/tsql-md.md)] statements:</span></span>  
  
        ```  
        -- Statement to execute on the new secondary server  
        USE msdb  
        GO  
        EXEC master.dbo.sp_change_log_shipping_primary_database @database=N'database_name', @threshold_alert_enabled = 0;  
        GO  
        ```  
  
## <a name="swapping-roles"></a><span data-ttu-id="3ce48-124">交換角色</span><span class="sxs-lookup"><span data-stu-id="3ce48-124">Swapping Roles</span></span>  
 <span data-ttu-id="3ce48-125">完成上述初始角色變更的步驟後，可遵循此節的步驟變更主要資料庫與次要資料庫間的角色。</span><span class="sxs-lookup"><span data-stu-id="3ce48-125">After you have completed the steps above for the initial role change, you can change roles between the primary database and the secondary database by following the steps in this section.</span></span> <span data-ttu-id="3ce48-126">若要執行角色變更，請遵循以下的一般步驟：</span><span class="sxs-lookup"><span data-stu-id="3ce48-126">To perform a role change, follow these general steps:</span></span>  
  
1.  <span data-ttu-id="3ce48-127">使次要資料庫連線工作，使用 NORECOVERY 備份主要伺服器上的交易記錄檔。</span><span class="sxs-lookup"><span data-stu-id="3ce48-127">Bring the secondary database online, backing up the transaction log on the primary server with NORECOVERY.</span></span>  
  
2.  <span data-ttu-id="3ce48-128">停用原始主要伺服器上的記錄傳送備份作業，以及原始次要伺服器上的複製與還原作業。</span><span class="sxs-lookup"><span data-stu-id="3ce48-128">Disable the log shipping backup job on the original primary server, and the copy and restore jobs on the original secondary server.</span></span>  
  
3.  <span data-ttu-id="3ce48-129">啟用次要伺服器 (新的主要伺服器) 上的記錄傳送備份作業，以及主要伺服器 (新的次要伺服器) 上的複製與還原工作。</span><span class="sxs-lookup"><span data-stu-id="3ce48-129">Enable the log shipping backup job on the secondary server (the new primary server), and the copy and restore jobs on the primary server (the new secondary server).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="3ce48-130">當您將次要資料庫變更為主要資料庫時，為了提供一致的經驗給使用者和應用程式，可能需要在新主要伺服器執行個體上為資料庫重新建立部份或全部的中繼資料，例如登入和作業。</span><span class="sxs-lookup"><span data-stu-id="3ce48-130">When you change a secondary database to the primary database, to provide a consistent experience to users and applications, you might have to re-create some or all of the metadata for the database, such as logins and jobs, on the new primary server instance.</span></span> <span data-ttu-id="3ce48-131">如需詳細資訊，請參閱 [在另一個伺服器執行個體上提供可用的資料庫時，管理中繼資料 &#40;SQL Server&#41;](../../relational-databases/databases/manage-metadata-when-making-a-database-available-on-another-server.md)。</span><span class="sxs-lookup"><span data-stu-id="3ce48-131">For more information, see [Manage Metadata When Making a Database Available on Another Server Instance &#40;SQL Server&#41;](../../relational-databases/databases/manage-metadata-when-making-a-database-available-on-another-server.md).</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="3ce48-132">相關工作</span><span class="sxs-lookup"><span data-stu-id="3ce48-132">Related Tasks</span></span>  
  
-   [<span data-ttu-id="3ce48-133">容錯移轉至記錄傳送次要 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="3ce48-133">Fail Over to a Log Shipping Secondary &#40;SQL Server&#41;</span></span>](fail-over-to-a-log-shipping-secondary-sql-server.md)  
  
-   [<span data-ttu-id="3ce48-134">角色切換後針對登入和作業進行管理 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="3ce48-134">Management of Logins and Jobs After Role Switching &#40;SQL Server&#41;</span></span>](../../sql-server/failover-clusters/management-of-logins-and-jobs-after-role-switching-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="3ce48-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3ce48-135">See Also</span></span>  
 [<span data-ttu-id="3ce48-136">記錄傳送資料表與預存程序</span><span class="sxs-lookup"><span data-stu-id="3ce48-136">Log Shipping Tables and Stored Procedures</span></span>](log-shipping-tables-and-stored-procedures.md)  
  
  
