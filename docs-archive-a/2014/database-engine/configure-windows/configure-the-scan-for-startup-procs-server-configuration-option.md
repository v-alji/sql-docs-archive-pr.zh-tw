---
title: 設定 scan for startup procs 伺服器組態選項 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- scan for startup procs option
ms.assetid: 6bf9d252-e766-458d-9dcd-23d895f032a2
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: fbf46fc7476e6e879991cfe3f649fd5617f3275e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594169"
---
# <a name="configure-the-scan-for-startup-procs-server-configuration-option"></a><span data-ttu-id="d0b68-102">設定 scan for startup procs 伺服器組態選項</span><span class="sxs-lookup"><span data-stu-id="d0b68-102">Configure the scan for startup procs Server Configuration Option</span></span>
  <span data-ttu-id="d0b68-103">此主題描述如何使用 **或** ，在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中設定 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] scan for startup procs [!INCLUDE[tsql](../../includes/tsql-md.md)]伺服器組態選項。</span><span class="sxs-lookup"><span data-stu-id="d0b68-103">This topic describes how to configure the **scan for startup procs** server configuration option in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="d0b68-104">您可以使用 **scan for startup procs** 選項，在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 啟動期間掃描預存程序的自動執行。</span><span class="sxs-lookup"><span data-stu-id="d0b68-104">Use the **scan for startup procs** option to scan for automatic execution of stored procedures at [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] startup time.</span></span> <span data-ttu-id="d0b68-105">如果這個選項設定為 1， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 會掃描及執行伺服器上所定義的所有自動執行預存程序。</span><span class="sxs-lookup"><span data-stu-id="d0b68-105">If this option is set to 1, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] scans for and runs all automatically run stored procedures that are defined on the server.</span></span> <span data-ttu-id="d0b68-106">**掃描啟動程序** 的預設值是 0 (不掃描)。</span><span class="sxs-lookup"><span data-stu-id="d0b68-106">The default value for **scan for startup procs** is 0 (do not scan).</span></span>  
  
 <span data-ttu-id="d0b68-107">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="d0b68-107">**In This Topic**</span></span>  
  
-   <span data-ttu-id="d0b68-108">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="d0b68-108">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="d0b68-109">建議</span><span class="sxs-lookup"><span data-stu-id="d0b68-109">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="d0b68-110">安全性</span><span class="sxs-lookup"><span data-stu-id="d0b68-110">Security</span></span>](#Security)  
  
-   <span data-ttu-id="d0b68-111">**使用下列方法設定 scan for startup procs 選項：**</span><span class="sxs-lookup"><span data-stu-id="d0b68-111">**To configure the scan for startup procs option, using:**</span></span>  
  
     [<span data-ttu-id="d0b68-112">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="d0b68-112">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="d0b68-113">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="d0b68-113">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   <span data-ttu-id="d0b68-114">**後續操作：** [設定掃描啟動程序選項之後](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="d0b68-114">**Follow Up:**  [After you configure the scan for startup procs option](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="d0b68-115">開始之前</span><span class="sxs-lookup"><span data-stu-id="d0b68-115">Before You Begin</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="d0b68-116">建議</span><span class="sxs-lookup"><span data-stu-id="d0b68-116">Recommendations</span></span>  
  
-   <span data-ttu-id="d0b68-117">這個選項是進階選項，只有有經驗的資料庫管理員或通過認證的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 技術人員才可變更。</span><span class="sxs-lookup"><span data-stu-id="d0b68-117">This option is an advanced option and should be changed only by an experienced database administrator or certified [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] technician.</span></span>  
  
-   <span data-ttu-id="d0b68-118">您可以使用 **sp_configure**來設定這個選項的值；然而如果您使用 **sp_procoption**(用以標示或取消標示自動執行的預存程序)，這個選項的值就會自動設定。</span><span class="sxs-lookup"><span data-stu-id="d0b68-118">The value for this option can be set by using **sp_configure**; however, it will be set automatically if you use **sp_procoption**, which is used to mark or unmark automatically run stored procedures.</span></span> <span data-ttu-id="d0b68-119">當 **sp_procoption** 用來將第一個預存程序標示為 autoproc 時，這個選項會自動設定為值 1。</span><span class="sxs-lookup"><span data-stu-id="d0b68-119">When **sp_procoption** is used to mark the first stored procedure as an autoproc, this option is set automatically to a value of 1.</span></span> <span data-ttu-id="d0b68-120">當 **sp_procoption** 用來將最後一個預存程序取消標示 autoproc 時，這個選項會自動設定為值 0。</span><span class="sxs-lookup"><span data-stu-id="d0b68-120">When **sp_procoption** is used to unmark the last stored procedure as an autoproc, this option is automatically set to a value of 0.</span></span> <span data-ttu-id="d0b68-121">如果您使用 **sp_procoption** 標示和取消標示 autoproc，而且固定在捨棄 autoproc 之前取消其標示，則不需要手動設定這個選項。</span><span class="sxs-lookup"><span data-stu-id="d0b68-121">If you use **sp_procoption** to mark and unmark autoprocs, and if you always unmark autoprocs before dropping them, there is no need to set this option manually.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="d0b68-122">Security</span><span class="sxs-lookup"><span data-stu-id="d0b68-122">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="d0b68-123">權限</span><span class="sxs-lookup"><span data-stu-id="d0b68-123">Permissions</span></span>  
 <span data-ttu-id="d0b68-124">不含參數或只含第一個參數之 **sp_configure** 上的執行權限預設會授與所有使用者。</span><span class="sxs-lookup"><span data-stu-id="d0b68-124">Execute permissions on **sp_configure** with no parameters or with only the first parameter are granted to all users by default.</span></span> <span data-ttu-id="d0b68-125">以同時設定兩個參數的 **sp_configure** 來變更組態選項或執行 RECONFIGURE 陳述式時，使用者必須取得 ALTER SETTINGS 伺服器層級權限。</span><span class="sxs-lookup"><span data-stu-id="d0b68-125">To execute **sp_configure** with both parameters to change a configuration option or to run the RECONFIGURE statement, a user must be granted the ALTER SETTINGS server-level permission.</span></span> <span data-ttu-id="d0b68-126">**系統管理員 (sysadmin)** 及 **serveradmin** 固定伺服器角色會隱含 ALTER SETTINGS 權限。</span><span class="sxs-lookup"><span data-stu-id="d0b68-126">The ALTER SETTINGS permission is implicitly held by the **sysadmin** and **serveradmin** fixed server roles.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="d0b68-127">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="d0b68-127">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-configure-the-scan-for-startup-procs-option"></a><span data-ttu-id="d0b68-128">若要設定 scan for startup procs 選項</span><span class="sxs-lookup"><span data-stu-id="d0b68-128">To configure the scan for startup procs option</span></span>  
  
1.  <span data-ttu-id="d0b68-129">在物件總管中，請以滑鼠右鍵按一下伺服器，然後選取 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="d0b68-129">In Object Explorer, right-click a server and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="d0b68-130">按一下 **[進階]** 節點。</span><span class="sxs-lookup"><span data-stu-id="d0b68-130">Click the **Advanced** node.</span></span>  
  
3.  <span data-ttu-id="d0b68-131">在 **[其他]** 下方，從下拉式清單方塊中選取所需的值，將 **[掃描啟動程序]** 選項的值變更為 True 或 False。</span><span class="sxs-lookup"><span data-stu-id="d0b68-131">Under **Miscellaneous**, change the **Scan for Startup Procs** option to True or False by selecting the value you want from the drop-down list box.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="d0b68-132">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="d0b68-132">Using Transact-SQL</span></span>  
  
#### <a name="to-configure-the-scan-for-startup-procs-option"></a><span data-ttu-id="d0b68-133">若要設定 scan for startup procs 選項</span><span class="sxs-lookup"><span data-stu-id="d0b68-133">To configure the scan for startup procs option</span></span>  
  
1.  <span data-ttu-id="d0b68-134">連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="d0b68-134">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="d0b68-135">在標準列中，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="d0b68-135">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="d0b68-136">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="d0b68-136">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="d0b68-137">此範例示範如何使用 [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) 將 `scan for startup procs` 選項的值設定為 `1`。</span><span class="sxs-lookup"><span data-stu-id="d0b68-137">This example shows how to use [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) to set the value of the `scan for startup procs` option to `1`.</span></span>  
  
```sql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'show advanced options', 1 ;  
GO  
RECONFIGURE  
GO  
EXEC sp_configure 'scan for startup procs', 1 ;  
GO  
RECONFIGURE  
GO  
  
```  
  
##  <a name="follow-up-after-you-configure-the-scan-for-startup-procs-option"></a><a name="FollowUp"></a> <span data-ttu-id="d0b68-138">後續操作：設定掃描啟動程序選項之後</span><span class="sxs-lookup"><span data-stu-id="d0b68-138">Follow Up: After you configure the scan for startup procs option</span></span>  
 <span data-ttu-id="d0b68-139">伺服器必須重新啟動之後，設定才能生效。</span><span class="sxs-lookup"><span data-stu-id="d0b68-139">The server must be restarted before the setting can take effect.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0b68-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d0b68-140">See Also</span></span>  
 <span data-ttu-id="d0b68-141">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="d0b68-141">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span></span>  
 <span data-ttu-id="d0b68-142">[伺服器組態選項 &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="d0b68-142">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 <span data-ttu-id="d0b68-143">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="d0b68-143">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span></span>  
 [<span data-ttu-id="d0b68-144">sp_procoption &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="d0b68-144">sp_procoption &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-procoption-transact-sql)  
  
  
