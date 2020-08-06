---
title: 設定備份壓縮 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
ms.assetid: 430905eb-d218-458c-bd48-aeee6fbb7446
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: f70994eb64cb6a50b538fd87f03ce7ea2fafe857
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606920"
---
# <a name="configure-backup-compression-sql-server"></a><span data-ttu-id="8ffda-102">設定備份壓縮 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="8ffda-102">Configure Backup Compression (SQL Server)</span></span>
  <span data-ttu-id="8ffda-103">進行安裝時，備份壓縮預設是關閉的。</span><span class="sxs-lookup"><span data-stu-id="8ffda-103">At installation, backup compression is off by default.</span></span> <span data-ttu-id="8ffda-104">備份壓縮的預設行為是透過 [備份壓縮預設] 伺服器層級組態選項所定義。</span><span class="sxs-lookup"><span data-stu-id="8ffda-104">The default behavior for backup compression is defined by the **backup compression default** Option server-level configuration option.</span></span> <span data-ttu-id="8ffda-105">不過，您可以在建立單一備份或排程一系列例行備份時，覆寫此伺服器層級預設值。</span><span class="sxs-lookup"><span data-stu-id="8ffda-105">However, you can override the server-level default when creating a single backup or scheduling a series of routine backups.</span></span> <span data-ttu-id="8ffda-106">若要變更伺服器層級的預設值，請參閱 [檢視或設定備份壓縮預設伺服器組態選項](../../database-engine/configure-windows/view-or-configure-the-backup-compression-default-server-configuration-option.md)。</span><span class="sxs-lookup"><span data-stu-id="8ffda-106">To change the server-level default, see [View or Configure the backup compression default Server Configuration Option](../../database-engine/configure-windows/view-or-configure-the-backup-compression-default-server-configuration-option.md).</span></span>  
  
## <a name="override-the-backup-compression-default"></a><span data-ttu-id="8ffda-107">覆寫備份壓縮預設</span><span class="sxs-lookup"><span data-stu-id="8ffda-107">Override the Backup Compression Default</span></span>  
 <span data-ttu-id="8ffda-108">您可以針對個別的備份、備份作業或記錄傳送組態來變更備份壓縮行為。</span><span class="sxs-lookup"><span data-stu-id="8ffda-108">You can change the backup compression behavior for an individual backup, backup job, or log shipping configuration.</span></span>  
  
-   **[!INCLUDE[tsql](../../includes/tsql-md.md)]**  
  
     <span data-ttu-id="8ffda-109">若要在建立備份時覆寫伺服器備份壓縮預設，請在 [BACKUP](/sql/t-sql/statements/backup-transact-sql) 陳述式中使用 WITH NO_COMPRESSION 或 WITH COMPRESSION。</span><span class="sxs-lookup"><span data-stu-id="8ffda-109">To override the server backup-compression default when creating a backup, use either WITH NO_COMPRESSION or WITH COMPRESSION in you [BACKUP](/sql/t-sql/statements/backup-transact-sql) statement.</span></span>  
  
     <span data-ttu-id="8ffda-110">如果是記錄傳送設定，您可以使用 [sp_add_log_shipping_primary_database](/sql/relational-databases/system-stored-procedures/sp-add-log-shipping-primary-database-transact-sql)[sp_change_log_shipping_primary_database &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-change-log-shipping-primary-database-transact-sql) 來控制記錄備份的備份壓縮行為。</span><span class="sxs-lookup"><span data-stu-id="8ffda-110">For a log shipping configuration, you can control the backup compression behavior of log backups by using [sp_add_log_shipping_primary_database](/sql/relational-databases/system-stored-procedures/sp-add-log-shipping-primary-database-transact-sql)[sp_change_log_shipping_primary_database &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-change-log-shipping-primary-database-transact-sql).</span></span>  
  
-   **[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]**  
  
     <span data-ttu-id="8ffda-111">如需如何檢視或設定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]執行個體之 [備份壓縮預設] 選項的資訊，請參閱[檢視或設定備份壓縮預設伺服器組態選項](../../database-engine/configure-windows/view-or-configure-the-backup-compression-default-server-configuration-option.md)。</span><span class="sxs-lookup"><span data-stu-id="8ffda-111">For information about how to view or configure the backup compression default option for an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], see [View or Configure the backup compression default Server Configuration Option](../../database-engine/configure-windows/view-or-configure-the-backup-compression-default-server-configuration-option.md).</span></span>  
  
     <span data-ttu-id="8ffda-112">在下列任何對話方塊中指定 [壓縮備份] 或 [不要壓縮備份]，就可以在建立備份時覆寫伺服器備份壓縮預設：</span><span class="sxs-lookup"><span data-stu-id="8ffda-112">You can override the server backup-compression default when creating a backup by specifying **Compress backup** or **Do not compress backup** in any of the following dialog boxes:</span></span>  
  
    -   [<span data-ttu-id="8ffda-113">備份資料庫 (選項頁面)</span><span class="sxs-lookup"><span data-stu-id="8ffda-113">Back Up Database (Options Page)</span></span>](back-up-database-backup-options-page.md)  
  
         <span data-ttu-id="8ffda-114">在備份資料庫時，您可以控制個別資料庫、檔案或記錄備份的備份壓縮。</span><span class="sxs-lookup"><span data-stu-id="8ffda-114">When backing up a database, you can control backup compression for an individual database, file, or log backup.</span></span>  
  
    -   [<span data-ttu-id="8ffda-115">使用維護計畫精靈</span><span class="sxs-lookup"><span data-stu-id="8ffda-115">Use the Maintenance Plan Wizard</span></span>](../maintenance-plans/use-the-maintenance-plan-wizard.md)  
  
         <span data-ttu-id="8ffda-116">「維護計畫精靈」可讓您針對每個排程的完整或差異資料庫備份或記錄備份，控制備份壓縮。</span><span class="sxs-lookup"><span data-stu-id="8ffda-116">The Maintenance Plan Wizard enables you to control backup compression for each set full or differential database backups or log backups that you schedule.</span></span>  
  
    -   <span data-ttu-id="8ffda-117">Integration Services (SSIS) [備份資料庫工作](../../integration-services/control-flow/back-up-database-task.md)</span><span class="sxs-lookup"><span data-stu-id="8ffda-117">Integration Services (SSIS) [Back Up Database task](../../integration-services/control-flow/back-up-database-task.md)</span></span>  
  
         <span data-ttu-id="8ffda-118">針對備份單一資料庫或多個資料庫建立封裝時，您可以控制備份壓縮行為。</span><span class="sxs-lookup"><span data-stu-id="8ffda-118">You can control the backup compression behavior when creating a package for backing up a single database or multiple databases.</span></span>  
  
    -   [<span data-ttu-id="8ffda-119">記錄傳送交易記錄備份設定</span><span class="sxs-lookup"><span data-stu-id="8ffda-119">Log Shipping Transaction Log Backup Settings</span></span>](../databases/log-shipping-transaction-log-backup-settings.md)  
  
         <span data-ttu-id="8ffda-120">您可以控制記錄備份的備份壓縮行為。</span><span class="sxs-lookup"><span data-stu-id="8ffda-120">You can control the backup compression behavior of log backups.</span></span>  
  
  
## <a name="see-also"></a><span data-ttu-id="8ffda-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8ffda-121">See Also</span></span>  
 [<span data-ttu-id="8ffda-122">備份壓縮 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="8ffda-122">Backup Compression &#40;SQL Server&#41;</span></span>](backup-compression-sql-server.md)  
  
  
