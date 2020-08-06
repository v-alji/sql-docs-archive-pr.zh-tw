---
title: 設定 nested triggers 伺服器組態選項 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- nested triggers option
ms.assetid: 29d7372b-d406-4a5b-80c6-a2d231d25211
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 7b27e185b0833f2e51be16393ff4d59a81046970
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597346"
---
# <a name="configure-the-nested-triggers-server-configuration-option"></a><span data-ttu-id="66781-102">設定 nested triggers 伺服器組態選項</span><span class="sxs-lookup"><span data-stu-id="66781-102">Configure the nested triggers Server Configuration Option</span></span>
  <span data-ttu-id="66781-103">此主題描述如何使用 **或** ，在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中設定 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] nested triggers [!INCLUDE[tsql](../../includes/tsql-md.md)]伺服器組態選項。</span><span class="sxs-lookup"><span data-stu-id="66781-103">This topic describes how to configure the **nested triggers** server configuration option in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="66781-104">**nested triggers** 選項控制 AFTER 觸發程序是否可以重疊顯示。</span><span class="sxs-lookup"><span data-stu-id="66781-104">The **nested triggers** option controls whether an AFTER trigger can cascade.</span></span> <span data-ttu-id="66781-105">亦即，執行起始另一個觸發程序的動作，後者再起始另一個觸發程序等。</span><span class="sxs-lookup"><span data-stu-id="66781-105">That is, perform an action that initiates another trigger, which initiates another trigger, and so on.</span></span> <span data-ttu-id="66781-106">**nested triggers** 設定為 0 時，AFTER 觸發程序不能重疊顯示。</span><span class="sxs-lookup"><span data-stu-id="66781-106">When **nested triggers** is set to 0, AFTER triggers cannot cascade.</span></span> <span data-ttu-id="66781-107">**nested triggers** 設定為 1 (預設值) 時，AFTER 觸發程序最多可以重疊顯示 32 層。</span><span class="sxs-lookup"><span data-stu-id="66781-107">When **nested triggers** is set to 1 (the default), AFTER triggers can cascade to as many as 32 levels.</span></span> <span data-ttu-id="66781-108">不論這個選項的設定為何，INSTEAD OF 觸發程序都可以巢狀。</span><span class="sxs-lookup"><span data-stu-id="66781-108">INSTEAD OF triggers can be nested regardless of the setting of this option.</span></span>  
  
 <span data-ttu-id="66781-109">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="66781-109">**In This Topic**</span></span>  
  
-   <span data-ttu-id="66781-110">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="66781-110">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="66781-111">安全性</span><span class="sxs-lookup"><span data-stu-id="66781-111">Security</span></span>](#Security)  
  
-   <span data-ttu-id="66781-112">**使用下列方法設定 nested triggers 選項：**</span><span class="sxs-lookup"><span data-stu-id="66781-112">**To configure the nested triggers option, using:**</span></span>  
  
     [<span data-ttu-id="66781-113">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="66781-113">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="66781-114">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="66781-114">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   <span data-ttu-id="66781-115">**後續操作：** [設定巢狀觸發程序選項之後](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="66781-115">**Follow Up:**  [After you configure the nested triggers option](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="66781-116">開始之前</span><span class="sxs-lookup"><span data-stu-id="66781-116">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="66781-117">Security</span><span class="sxs-lookup"><span data-stu-id="66781-117">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="66781-118">權限</span><span class="sxs-lookup"><span data-stu-id="66781-118">Permissions</span></span>  
 <span data-ttu-id="66781-119">不含參數或只含第一個參數之 **sp_configure** 上的執行權限預設會授與所有使用者。</span><span class="sxs-lookup"><span data-stu-id="66781-119">Execute permissions on **sp_configure** with no parameters or with only the first parameter are granted to all users by default.</span></span> <span data-ttu-id="66781-120">以同時設定兩個參數的 **sp_configure** 來變更組態選項或執行 RECONFIGURE 陳述式時，使用者必須取得 ALTER SETTINGS 伺服器層級權限。</span><span class="sxs-lookup"><span data-stu-id="66781-120">To execute **sp_configure** with both parameters to change a configuration option or to run the RECONFIGURE statement, a user must be granted the ALTER SETTINGS server-level permission.</span></span> <span data-ttu-id="66781-121">**系統管理員 (sysadmin)** 及 **serveradmin** 固定伺服器角色會隱含 ALTER SETTINGS 權限。</span><span class="sxs-lookup"><span data-stu-id="66781-121">The ALTER SETTINGS permission is implicitly held by the **sysadmin** and **serveradmin** fixed server roles.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="66781-122">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="66781-122">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-configure-the-nested-triggers-option"></a><span data-ttu-id="66781-123">設定 nested triggers 選項</span><span class="sxs-lookup"><span data-stu-id="66781-123">To configure the nested triggers option</span></span>  
  
1.  <span data-ttu-id="66781-124">在物件總管中，以滑鼠右鍵按一下伺服器，然後選取 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="66781-124">In **Object Explorer**, right-click a server, and then select **Properties**.</span></span>  
  
2.  <span data-ttu-id="66781-125">在 **[進階]** 頁面上，將 **[允許觸發程序引發其他觸發程序]** 選項設定為 **[True]** (預設值) 或 **[False]** 。</span><span class="sxs-lookup"><span data-stu-id="66781-125">On the **Advanced** page, set the **Allow Triggers to Fire Others** option to **True** (the default) or **False**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="66781-126">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="66781-126">Using Transact-SQL</span></span>  
  
#### <a name="to-configure-the-nested-triggers-option"></a><span data-ttu-id="66781-127">設定 nested triggers 選項</span><span class="sxs-lookup"><span data-stu-id="66781-127">To configure the nested triggers option</span></span>  
  
1.  <span data-ttu-id="66781-128">連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="66781-128">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="66781-129">在標準列中，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="66781-129">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="66781-130">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="66781-130">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="66781-131">此範例示範如何使用 [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) 將 `nested triggers` 選項的值設定為 `0`。</span><span class="sxs-lookup"><span data-stu-id="66781-131">This example shows how to use [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) to set the value of the `nested triggers` option to `0`.</span></span>  
  
```wmimof  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE ;  
GO  
EXEC sp_configure 'nested triggers', 0 ;  
GO  
RECONFIGURE;  
GO  
  
```  
  
 <span data-ttu-id="66781-132">如需詳細資訊，請參閱 [伺服器設定選項 &#40;SQL Server&#41;](server-configuration-options-sql-server.md)伺服器組態選項。</span><span class="sxs-lookup"><span data-stu-id="66781-132">For more information, see [Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md).</span></span>  
  
##  <a name="follow-up-after-you-configure-the-nested-triggers-option"></a><a name="FollowUp"></a> <span data-ttu-id="66781-133">後續操作：設定巢狀觸發程序選項之後</span><span class="sxs-lookup"><span data-stu-id="66781-133">Follow Up: After you configure the nested triggers option</span></span>  
 <span data-ttu-id="66781-134">設定會立即生效，不需要重新啟動伺服器。</span><span class="sxs-lookup"><span data-stu-id="66781-134">The setting takes effect immediately without restarting the server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66781-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="66781-135">See Also</span></span>  
 <span data-ttu-id="66781-136">[建立巢狀觸發程序](../../relational-databases/triggers/create-nested-triggers.md) </span><span class="sxs-lookup"><span data-stu-id="66781-136">[Create Nested Triggers](../../relational-databases/triggers/create-nested-triggers.md) </span></span>  
 <span data-ttu-id="66781-137">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="66781-137">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span></span>  
 <span data-ttu-id="66781-138">[伺服器組態選項 &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="66781-138">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 [<span data-ttu-id="66781-139">sp_configure &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="66781-139">sp_configure &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
