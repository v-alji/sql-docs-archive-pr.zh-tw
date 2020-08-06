---
title: 檢視或設定遠端伺服器連線選項 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- remote servers [SQL Server], connection options
- servers [SQL Server], remote
- connections [SQL Server], remote servers
ms.assetid: 356d3e6b-8514-4bd2-a683-9de147949b2b
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 73fe5e484d62cde025d1a560937e8cbcf5ec361d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688189"
---
# <a name="view-or-configure-remote-server-connection-options-sql-server"></a><span data-ttu-id="07a30-102">檢視或設定遠端伺服器連接選項 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="07a30-102">View or Configure Remote Server Connection Options (SQL Server)</span></span>
  <span data-ttu-id="07a30-103">此主題描述如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中檢視或設定伺服器層級的遠端伺服器連接選項。</span><span class="sxs-lookup"><span data-stu-id="07a30-103">This topic describes how to view or configure remote server connection options at the server level in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="07a30-104">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="07a30-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="07a30-105">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="07a30-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="07a30-106">安全性</span><span class="sxs-lookup"><span data-stu-id="07a30-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="07a30-107">**若要使用下列項目檢視或設定遠端伺服器連接選項：**</span><span class="sxs-lookup"><span data-stu-id="07a30-107">**To view or configure remote server connection options, using:**</span></span>  
  
     [<span data-ttu-id="07a30-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="07a30-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="07a30-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="07a30-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   <span data-ttu-id="07a30-110">**後續操作：** [設定遠端伺服器連線選項之後](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="07a30-110">**Follow Up:**  [After you configure remote server connection options](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="07a30-111">開始之前</span><span class="sxs-lookup"><span data-stu-id="07a30-111">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="07a30-112">Security</span><span class="sxs-lookup"><span data-stu-id="07a30-112">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="07a30-113">權限</span><span class="sxs-lookup"><span data-stu-id="07a30-113">Permissions</span></span>  
 <span data-ttu-id="07a30-114">執行 **sp_serveroption** 需要伺服器的 ALTER ANY LINKED SERVER 權限。</span><span class="sxs-lookup"><span data-stu-id="07a30-114">Executing **sp_serveroption** requires ALTER ANY LINKED SERVER permission on the server.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="07a30-115">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="07a30-115">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-view-or-configure-remote-server-connection-options"></a><span data-ttu-id="07a30-116">若要檢視或設定遠端伺服器連接選項</span><span class="sxs-lookup"><span data-stu-id="07a30-116">To view or configure remote server connection options</span></span>  
  
1.  <span data-ttu-id="07a30-117">在物件總管中，以滑鼠右鍵按一下伺服器，然後按一下 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="07a30-117">In Object Explorer, right-click a server, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="07a30-118">在 [SQL Server 屬性 - \<***server_name***>] 對話方塊中，按一下 [連線]。</span><span class="sxs-lookup"><span data-stu-id="07a30-118">In the **SQL Server Properties - \<***server_name***>** dialog box, click **Connections**.</span></span>  
  
3.  <span data-ttu-id="07a30-119">檢閱 **[連接]** 頁面上的 **[遠端伺服器連接]** 設定，並視需要加以修改。</span><span class="sxs-lookup"><span data-stu-id="07a30-119">On the **Connections** page, review the **Remote server connections** settings, and modify them if necessary.</span></span>  
  
4.  <span data-ttu-id="07a30-120">對遠端伺服器組的另一部伺服器重複步驟 1 到步驟 3。</span><span class="sxs-lookup"><span data-stu-id="07a30-120">Repeat steps 1 through 3 on the other server of the remote server pair.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="07a30-121">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="07a30-121">Using Transact-SQL</span></span>  
  
#### <a name="to-view-remote-server-connection-options"></a><span data-ttu-id="07a30-122">若要檢視遠端伺服器連接選項</span><span class="sxs-lookup"><span data-stu-id="07a30-122">To view remote server connection options</span></span>  
  
1.  <span data-ttu-id="07a30-123">連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="07a30-123">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="07a30-124">在標準列中，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="07a30-124">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="07a30-125">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="07a30-125">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="07a30-126">這個範例使用 [sp_helpserver](/sql/relational-databases/system-stored-procedures/sp-helpserver-transact-sql) 傳回所有遠端伺服器的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="07a30-126">This example uses [sp_helpserver](/sql/relational-databases/system-stored-procedures/sp-helpserver-transact-sql) to return information about all remote servers.</span></span>  
  
```sql  
USE master;  
GO  
EXEC sp_helpserver ;  
```  
  
#### <a name="to-configure-remote-server-connection-options"></a><span data-ttu-id="07a30-127">若要設定遠端伺服器連接選項</span><span class="sxs-lookup"><span data-stu-id="07a30-127">To configure remote server connection options</span></span>  
  
1.  <span data-ttu-id="07a30-128">連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="07a30-128">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="07a30-129">在標準列中，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="07a30-129">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="07a30-130">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="07a30-130">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="07a30-131">這個範例示範如何使用 [sp_serveroption](/sql/relational-databases/system-stored-procedures/sp-serveroption-transact-sql) 設定遠端伺服器。</span><span class="sxs-lookup"><span data-stu-id="07a30-131">This example shows how to use [sp_serveroption](/sql/relational-databases/system-stored-procedures/sp-serveroption-transact-sql) to configure a remote server.</span></span> <span data-ttu-id="07a30-132">範例會將對應於另一個 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]執行個體 ( `SEATTLE3`) 的遠端伺服器，設定成定序相容於 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的本機執行個體。</span><span class="sxs-lookup"><span data-stu-id="07a30-132">The example configures a remote server corresponding to another instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], `SEATTLE3`, to be collation compatible with the local instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
```sql  
USE master;  
EXEC sp_serveroption 'SEATTLE3', 'collation compatible', 'true';  
```  
  
##  <a name="follow-up-after-you-configure-remote-server-connection-options"></a><a name="FollowUp"></a> <span data-ttu-id="07a30-133">後續操作：設定遠端伺服器連線選項之後</span><span class="sxs-lookup"><span data-stu-id="07a30-133">Follow Up: After you configure remote server connection options</span></span>  
 <span data-ttu-id="07a30-134">遠端伺服器必須停止並重新啟動之後，設定才能生效。</span><span class="sxs-lookup"><span data-stu-id="07a30-134">The remote server must be stopped and restarted before the setting can take effect.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07a30-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="07a30-135">See Also</span></span>  
 <span data-ttu-id="07a30-136">[伺服器組態選項 &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="07a30-136">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 <span data-ttu-id="07a30-137">[遠端伺服器](remote-servers.md) </span><span class="sxs-lookup"><span data-stu-id="07a30-137">[Remote Servers](remote-servers.md) </span></span>  
 <span data-ttu-id="07a30-138">[連結的伺服器 &#40;Database Engine&#41;](../../relational-databases/linked-servers/linked-servers-database-engine.md) </span><span class="sxs-lookup"><span data-stu-id="07a30-138">[Linked Servers &#40;Database Engine&#41;](../../relational-databases/linked-servers/linked-servers-database-engine.md) </span></span>  
 <span data-ttu-id="07a30-139">[sp_linkedservers &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-linkedservers-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="07a30-139">[sp_linkedservers &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-linkedservers-transact-sql) </span></span>  
 <span data-ttu-id="07a30-140">[sp_helpserver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helpserver-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="07a30-140">[sp_helpserver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helpserver-transact-sql) </span></span>  
 [<span data-ttu-id="07a30-141">sp_serveroption &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="07a30-141">sp_serveroption &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-serveroption-transact-sql)  
  
  
