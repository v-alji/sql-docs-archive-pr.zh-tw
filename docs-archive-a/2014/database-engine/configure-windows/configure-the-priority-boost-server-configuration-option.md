---
title: 設定 priority boost 伺服器組態選項 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- priority boost option
ms.assetid: 765f1e83-dd52-44fb-b0c8-1078f213607b
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: f42d7d2022e07dcac3039557295dc70e4500583d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594173"
---
# <a name="configure-the-priority-boost-server-configuration-option"></a><span data-ttu-id="4e62a-102">設定 priority boost 伺服器組態選項</span><span class="sxs-lookup"><span data-stu-id="4e62a-102">Configure the priority boost Server Configuration Option</span></span>
  <span data-ttu-id="4e62a-103">此主題描述如何使用 **或** ，在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中設定 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] priority boost [!INCLUDE[tsql](../../includes/tsql-md.md)]伺服器組態選項。</span><span class="sxs-lookup"><span data-stu-id="4e62a-103">This topic describes how to configure the **priority boost** configuration option in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="4e62a-104">使用 [優先權提升] 選項，指定 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 是否應以高於同一部電腦上其他處理序的 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 2008 或 Windows 2008 R2 排程優先權執行。</span><span class="sxs-lookup"><span data-stu-id="4e62a-104">Use the **priority boost** option to specify whether [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] should run at a higher [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 2008 or Windows 2008 R2 scheduling priority than other processes on the same computer.</span></span> <span data-ttu-id="4e62a-105">如果將此選項設定為 1， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 在 Windows 2008 或 Windows Server 2008 R2 排程器中會以優先權基底 13 執行。</span><span class="sxs-lookup"><span data-stu-id="4e62a-105">If you set this option to 1, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] runs at a priority base of 13 in the Windows 2008 or Windows Server 2008 R2 scheduler.</span></span> <span data-ttu-id="4e62a-106">預設值是 0，也就是優先權基底 7。</span><span class="sxs-lookup"><span data-stu-id="4e62a-106">The default is 0, which is a priority base of 7.</span></span>  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]  
  
 <span data-ttu-id="4e62a-107">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="4e62a-107">**In This Topic**</span></span>  
  
-   <span data-ttu-id="4e62a-108">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="4e62a-108">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="4e62a-109">限制事項</span><span class="sxs-lookup"><span data-stu-id="4e62a-109">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="4e62a-110">安全性</span><span class="sxs-lookup"><span data-stu-id="4e62a-110">Security</span></span>](#Security)  
  
-   <span data-ttu-id="4e62a-111">**使用下列方法設定 priority boost 選項：**</span><span class="sxs-lookup"><span data-stu-id="4e62a-111">**To configure the priority boost option, using:**</span></span>  
  
     [<span data-ttu-id="4e62a-112">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="4e62a-112">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="4e62a-113">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="4e62a-113">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   <span data-ttu-id="4e62a-114">**後續操作：** [設定優先權提升選項之後](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="4e62a-114">**Follow Up:**  [After you configure the priority boost option](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="4e62a-115">開始之前</span><span class="sxs-lookup"><span data-stu-id="4e62a-115">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="4e62a-116">限制事項</span><span class="sxs-lookup"><span data-stu-id="4e62a-116">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="4e62a-117">過度提高優先權可能會耗盡必要作業系統和網路功能的資源，導致 SQL Server 關機時或使用伺服器上的其他作業系統工作時出現問題。</span><span class="sxs-lookup"><span data-stu-id="4e62a-117">Raising the priority too high may drain resources from essential operating system and network functions, resulting in problems shutting down SQL Server or using other operating system tasks on the server.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="4e62a-118">Security</span><span class="sxs-lookup"><span data-stu-id="4e62a-118">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="4e62a-119">權限</span><span class="sxs-lookup"><span data-stu-id="4e62a-119">Permissions</span></span>  
 <span data-ttu-id="4e62a-120">不含參數或只含第一個參數之 **sp_configure** 上的執行權限預設會授與所有使用者。</span><span class="sxs-lookup"><span data-stu-id="4e62a-120">Execute permissions on **sp_configure** with no parameters or with only the first parameter are granted to all users by default.</span></span> <span data-ttu-id="4e62a-121">以同時設定兩個參數的 **sp_configure** 來變更組態選項或執行 RECONFIGURE 陳述式時，使用者必須取得 ALTER SETTINGS 伺服器層級權限。</span><span class="sxs-lookup"><span data-stu-id="4e62a-121">To execute **sp_configure** with both parameters to change a configuration option or to run the RECONFIGURE statement, a user must be granted the ALTER SETTINGS server-level permission.</span></span> <span data-ttu-id="4e62a-122">**系統管理員 (sysadmin)** 及 **serveradmin** 固定伺服器角色會隱含 ALTER SETTINGS 權限。</span><span class="sxs-lookup"><span data-stu-id="4e62a-122">The ALTER SETTINGS permission is implicitly held by the **sysadmin** and **serveradmin** fixed server roles.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="4e62a-123">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="4e62a-123">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-configure-the-priority-boost-option"></a><span data-ttu-id="4e62a-124">若要設定 priority boost 選項</span><span class="sxs-lookup"><span data-stu-id="4e62a-124">To configure the priority boost option</span></span>  
  
1.  <span data-ttu-id="4e62a-125">在物件總管中，請以滑鼠右鍵按一下伺服器，然後選取 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="4e62a-125">In Object Explorer, right-click a server and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="4e62a-126">按一下 **[處理器]** 節點。</span><span class="sxs-lookup"><span data-stu-id="4e62a-126">Click the **Processors** node.</span></span>  
  
3.  <span data-ttu-id="4e62a-127">在 **[執行緒]** 下，選取 **[提高 SQL Server 優先權]** 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="4e62a-127">Under **Threads**, select the **Boost SQL Server priority** check box.</span></span>  
  
4.  <span data-ttu-id="4e62a-128">停止 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]並重新啟動。</span><span class="sxs-lookup"><span data-stu-id="4e62a-128">Stop and restart [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="4e62a-129">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="4e62a-129">Using Transact-SQL</span></span>  
  
#### <a name="to-configure-the-priority-boost-option"></a><span data-ttu-id="4e62a-130">若要設定 priority boost 選項</span><span class="sxs-lookup"><span data-stu-id="4e62a-130">To configure the priority boost option</span></span>  
  
1.  <span data-ttu-id="4e62a-131">連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="4e62a-131">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="4e62a-132">在標準列中，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="4e62a-132">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="4e62a-133">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="4e62a-133">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="4e62a-134">此範例示範如何使用 [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) 將 `priority boost` 選項的值設定為 `1`。</span><span class="sxs-lookup"><span data-stu-id="4e62a-134">This example shows how to use [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) to set the value of the `priority boost` option to `1`.</span></span>  
  
```sql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE ;  
GO  
EXEC sp_configure 'priority boost', 1 ;  
GO  
RECONFIGURE;  
GO  
  
```  
  
 <span data-ttu-id="4e62a-135">如需詳細資訊，請參閱 [伺服器設定選項 &#40;SQL Server&#41;](server-configuration-options-sql-server.md)伺服器組態選項。</span><span class="sxs-lookup"><span data-stu-id="4e62a-135">For more information, see [Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md).</span></span>  
  
##  <a name="follow-up-after-you-configure-the-priority-boost-option"></a><a name="FollowUp"></a> <span data-ttu-id="4e62a-136">後續操作：設定優先權提升選項之後</span><span class="sxs-lookup"><span data-stu-id="4e62a-136">Follow Up: After you configure the priority boost option</span></span>  
 <span data-ttu-id="4e62a-137">伺服器必須重新啟動之後，設定才能生效。</span><span class="sxs-lookup"><span data-stu-id="4e62a-137">The server must be restarted before the setting can take effect.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e62a-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4e62a-138">See Also</span></span>  
 <span data-ttu-id="4e62a-139">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="4e62a-139">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span></span>  
 <span data-ttu-id="4e62a-140">[伺服器組態選項 &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="4e62a-140">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 [<span data-ttu-id="4e62a-141">sp_configure &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="4e62a-141">sp_configure &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
