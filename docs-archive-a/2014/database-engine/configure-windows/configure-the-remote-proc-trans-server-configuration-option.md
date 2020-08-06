---
title: 設定 remote proc trans 伺服器組態選項 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- remote proc trans option
- distributed transactions [SQL Server], enforcing
ms.assetid: cfbc6158-ab96-44b4-87eb-ea278c1b0c6b
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 54fcaafa51eef33acb1ae8d1e2f36022840b76a1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594170"
---
# <a name="configure-the-remote-proc-trans-server-configuration-option"></a><span data-ttu-id="a423a-102">設定 remote proc trans 伺服器組態選項</span><span class="sxs-lookup"><span data-stu-id="a423a-102">Configure the remote proc trans Server Configuration Option</span></span>
  <span data-ttu-id="a423a-103">此主題描述如何使用 **或** ，在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中設定 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] remote proc trans [!INCLUDE[tsql](../../includes/tsql-md.md)]伺服器組態選項。</span><span class="sxs-lookup"><span data-stu-id="a423a-103">This topic describes how to configure the **remote proc trans** server configuration option in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="a423a-104">**remote proc trans** 選項有助於保護透過 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 分散式交易協調器 (MS DTC) 交易的伺服器對伺服器程序的動作。</span><span class="sxs-lookup"><span data-stu-id="a423a-104">The **remote proc trans** option helps protect the actions of a server-to-server procedure through a [!INCLUDE[msCoName](../../includes/msconame-md.md)] Distributed Transaction Coordinator (MS DTC) transaction.</span></span>  
  
 <span data-ttu-id="a423a-105">將 **remote proc trans** 的值設為 1，可提供 MS DTC 協調分散式交易來保護交易的 ACID (不可部分完成的、一致的、隔離的和持久的) 屬性。</span><span class="sxs-lookup"><span data-stu-id="a423a-105">Set the value of **remote proc trans** to 1 to provide an MS DTC-coordinated distributed transaction that protects the ACID (atomic, consistent, isolated, and durable) properties of transactions.</span></span> <span data-ttu-id="a423a-106">在此選項設為 1 之後開始的工作階段會繼承此組態設定做為其預設值。</span><span class="sxs-lookup"><span data-stu-id="a423a-106">Sessions begun after setting this option to 1 inherit the configuration setting as their default.</span></span>  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepNextAvoid](../../includes/ssnotedepnextavoid-md.md)]  
  
 <span data-ttu-id="a423a-107">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="a423a-107">**In This Topic**</span></span>  
  
-   <span data-ttu-id="a423a-108">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="a423a-108">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="a423a-109">先決條件</span><span class="sxs-lookup"><span data-stu-id="a423a-109">Prerequisites</span></span>](#Prerequisites)  
  
     [<span data-ttu-id="a423a-110">建議</span><span class="sxs-lookup"><span data-stu-id="a423a-110">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="a423a-111">安全性</span><span class="sxs-lookup"><span data-stu-id="a423a-111">Security</span></span>](#Security)  
  
-   <span data-ttu-id="a423a-112">**使用下列方法設定 remote proc trans 選項：**</span><span class="sxs-lookup"><span data-stu-id="a423a-112">**To configure the remote proc trans option, using:**</span></span>  
  
     [<span data-ttu-id="a423a-113">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="a423a-113">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="a423a-114">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="a423a-114">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   <span data-ttu-id="a423a-115">**後續操作：** [設定遠端程序交易選項之後](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="a423a-115">**Follow Up:**  [After you configure the remote proc trans option](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="a423a-116">開始之前</span><span class="sxs-lookup"><span data-stu-id="a423a-116">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="a423a-117">必要條件</span><span class="sxs-lookup"><span data-stu-id="a423a-117">Prerequisites</span></span>  
  
-   <span data-ttu-id="a423a-118">設定這個數值之前必須先允許遠端伺服器連接。</span><span class="sxs-lookup"><span data-stu-id="a423a-118">Remote server connections must be allowed before this value can be set.</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="a423a-119">建議</span><span class="sxs-lookup"><span data-stu-id="a423a-119">Recommendations</span></span>  
  
-   <span data-ttu-id="a423a-120">此選項主要是針對使用遠端預存程序的應用程式提供舊版 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 相容性。</span><span class="sxs-lookup"><span data-stu-id="a423a-120">This option is provided for compatibility with earlier versions of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] for applications that use remote stored procedures.</span></span> <span data-ttu-id="a423a-121">請使用參考連結的伺服器 (使用 [sp_addlinkedserver](/sql/relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql)定義的) 之分散式查詢，而不要發出遠端預存程序呼叫。</span><span class="sxs-lookup"><span data-stu-id="a423a-121">Instead of issuing remote stored procedure calls, use distributed queries that reference linked servers, which are defined by using [sp_addlinkedserver](/sql/relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="a423a-122">Security</span><span class="sxs-lookup"><span data-stu-id="a423a-122">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="a423a-123">權限</span><span class="sxs-lookup"><span data-stu-id="a423a-123">Permissions</span></span>  
 <span data-ttu-id="a423a-124">不含參數或只含第一個參數之 **sp_configure** 上的執行權限預設會授與所有使用者。</span><span class="sxs-lookup"><span data-stu-id="a423a-124">Execute permissions on **sp_configure** with no parameters or with only the first parameter are granted to all users by default.</span></span> <span data-ttu-id="a423a-125">以同時設定兩個參數的 **sp_configure** 來變更組態選項或執行 RECONFIGURE 陳述式時，使用者必須取得 ALTER SETTINGS 伺服器層級權限。</span><span class="sxs-lookup"><span data-stu-id="a423a-125">To execute **sp_configure** with both parameters to change a configuration option or to run the RECONFIGURE statement, a user must be granted the ALTER SETTINGS server-level permission.</span></span> <span data-ttu-id="a423a-126">**系統管理員 (sysadmin)** 及 **serveradmin** 固定伺服器角色會隱含 ALTER SETTINGS 權限。</span><span class="sxs-lookup"><span data-stu-id="a423a-126">The ALTER SETTINGS permission is implicitly held by the **sysadmin** and **serveradmin** fixed server roles.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="a423a-127">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="a423a-127">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-configure-the-remote-proc-trans-option"></a><span data-ttu-id="a423a-128">設定 remote proc trans 選項</span><span class="sxs-lookup"><span data-stu-id="a423a-128">To configure the remote proc trans option</span></span>  
  
1.  <span data-ttu-id="a423a-129">在物件總管中，請以滑鼠右鍵按一下伺服器，然後選取 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="a423a-129">In Object Explorer, right-click a server and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="a423a-130">按一下 **[連接]** 節點。</span><span class="sxs-lookup"><span data-stu-id="a423a-130">Click the **Connections** node.</span></span>  
  
3.  <span data-ttu-id="a423a-131">在 **[遠端伺服器連接]** 之下，選取 **[需要伺服器對伺服器通訊的分散式交易]** 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="a423a-131">Under **Remote server connections**, select the **Require Distributed Transactions for server to server communication** check box.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="a423a-132">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="a423a-132">Using Transact-SQL</span></span>  
  
#### <a name="to-configure-the-remote-proc-trans-option"></a><span data-ttu-id="a423a-133">設定 remote proc trans 選項</span><span class="sxs-lookup"><span data-stu-id="a423a-133">To configure the remote proc trans option</span></span>  
  
1.  <span data-ttu-id="a423a-134">連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="a423a-134">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="a423a-135">在標準列中，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="a423a-135">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="a423a-136">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="a423a-136">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="a423a-137">此範例示範如何使用 [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) 將 `remote proc trans` 選項的值設定為 `1`。</span><span class="sxs-lookup"><span data-stu-id="a423a-137">This example shows how to use [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) to set the value of the `remote proc trans` option to `1`.</span></span>  
  
```sql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'remote proc trans', 1 ;  
GO  
RECONFIGURE ;  
GO  
  
```  
  
 <span data-ttu-id="a423a-138">如需詳細資訊，請參閱 [伺服器設定選項 &#40;SQL Server&#41;](server-configuration-options-sql-server.md)伺服器組態選項。</span><span class="sxs-lookup"><span data-stu-id="a423a-138">For more information, see [Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md).</span></span>  
  
##  <a name="follow-up-after-you-configure-the-remote-proc-trans-option"></a><a name="FollowUp"></a> <span data-ttu-id="a423a-139">後續操作：設定遠端程序交易選項之後</span><span class="sxs-lookup"><span data-stu-id="a423a-139">Follow Up: After you configure the remote proc trans option</span></span>  
 <span data-ttu-id="a423a-140">設定會立即生效，不需要重新啟動伺服器。</span><span class="sxs-lookup"><span data-stu-id="a423a-140">The setting takes effect immediately without restarting the server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a423a-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a423a-141">See Also</span></span>  
 <span data-ttu-id="a423a-142">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="a423a-142">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span></span>  
 <span data-ttu-id="a423a-143">[伺服器組態選項 &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="a423a-143">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 [<span data-ttu-id="a423a-144">sp_configure &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="a423a-144">sp_configure &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
