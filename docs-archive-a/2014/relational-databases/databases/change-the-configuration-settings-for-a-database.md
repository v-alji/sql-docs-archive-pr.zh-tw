---
title: 變更資料庫的組態設定 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- database configuration [SQL Server]
- configuration options [SQL Server], databases
- modifying database configuration settings
ms.assetid: c29c3385-5043-400f-bb4e-044a4c9a9a4b
author: stevestein
ms.author: sstein
ms.openlocfilehash: f9edecefae5154bb66a65e38724d9e77a94fdbb4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709590"
---
# <a name="change-the-configuration-settings-for-a-database"></a><span data-ttu-id="6cf61-102">變更資料庫的組態設定</span><span class="sxs-lookup"><span data-stu-id="6cf61-102">Change the Configuration Settings for a Database</span></span>
  <span data-ttu-id="6cf61-103">此主題描述如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中變更資料庫層級選項。</span><span class="sxs-lookup"><span data-stu-id="6cf61-103">This topic describes how to change database-level options in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="6cf61-104">這些選項對每個資料庫都是唯一的，並不會影響其他資料庫。</span><span class="sxs-lookup"><span data-stu-id="6cf61-104">These options are unique to each database and do not affect other databases.</span></span>  
  
 <span data-ttu-id="6cf61-105">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="6cf61-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="6cf61-106">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="6cf61-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="6cf61-107">限制事項</span><span class="sxs-lookup"><span data-stu-id="6cf61-107">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="6cf61-108">安全性</span><span class="sxs-lookup"><span data-stu-id="6cf61-108">Security</span></span>](#Security)  
  
-   <span data-ttu-id="6cf61-109">**使用下列方法變更資料庫的選項設定：**</span><span class="sxs-lookup"><span data-stu-id="6cf61-109">**To change the option settings for a database, using:**</span></span>  
  
     [<span data-ttu-id="6cf61-110">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="6cf61-110">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="6cf61-111">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="6cf61-111">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="6cf61-112">開始之前</span><span class="sxs-lookup"><span data-stu-id="6cf61-112">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="6cf61-113">限制事項</span><span class="sxs-lookup"><span data-stu-id="6cf61-113">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="6cf61-114">只有系統管理員、資料庫擁有者、 **系統管理員** 與 **dbcreator** 固定伺服器角色成員，以及 **db_owner** 固定資料庫角色成員可以修改這些選項。</span><span class="sxs-lookup"><span data-stu-id="6cf61-114">Only the system administrator, database owner, members of the **sysadmin** and **dbcreator** fixed server roles and **db_owner** fixed database roles can modify these options.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="6cf61-115">Security</span><span class="sxs-lookup"><span data-stu-id="6cf61-115">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="6cf61-116">權限</span><span class="sxs-lookup"><span data-stu-id="6cf61-116">Permissions</span></span>  
 <span data-ttu-id="6cf61-117">需要資料庫的 ALTER 權限。</span><span class="sxs-lookup"><span data-stu-id="6cf61-117">Requires ALTER permission on the database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="6cf61-118">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="6cf61-118">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-change-the-option-settings-for-a-database"></a><span data-ttu-id="6cf61-119">若要變更資料庫的選項設定</span><span class="sxs-lookup"><span data-stu-id="6cf61-119">To change the option settings for a database</span></span>  
  
1.  <span data-ttu-id="6cf61-120">在物件總管中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 執行個體，依序展開伺服器和 [資料庫]，以滑鼠右鍵按一下資料庫，然後按一下 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="6cf61-120">In Object Explorer, connect to a [!INCLUDE[ssDE](../../includes/ssde-md.md)] instance, expand the server, expand **Databases**, right-click a database, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="6cf61-121">在 **[資料庫屬性]** 對話方塊中，按一下 **[選項]** 以存取大部份的組態設定。</span><span class="sxs-lookup"><span data-stu-id="6cf61-121">In the **Database Properties** dialog box, click **Options** to access most of the configuration settings.</span></span> <span data-ttu-id="6cf61-122">檔案和檔案群組組態、鏡像及記錄傳送都位在其各自的頁面上。</span><span class="sxs-lookup"><span data-stu-id="6cf61-122">File and filegroup configurations, mirroring and log shipping are on their respective pages.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="6cf61-123">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="6cf61-123">Using Transact-SQL</span></span>  
  
#### <a name="to-change-the-option-settings-for-a-database"></a><span data-ttu-id="6cf61-124">若要變更資料庫的選項設定</span><span class="sxs-lookup"><span data-stu-id="6cf61-124">To change the option settings for a database</span></span>  
  
1.  <span data-ttu-id="6cf61-125">連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="6cf61-125">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="6cf61-126">在標準列中，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="6cf61-126">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="6cf61-127">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="6cf61-127">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="6cf61-128">這個範例會設定 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 範例資料庫的復原模式和資料頁面驗證選項。</span><span class="sxs-lookup"><span data-stu-id="6cf61-128">This example sets the recovery model and data page verification options for the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] sample database.</span></span>  
  
 [!code-sql[DatabaseDDL#AlterDatabase7](../../snippets/tsql/SQL14/tsql/databaseddl/transact-sql/alterdatabase.sql#alterdatabase7)]  
  
 <span data-ttu-id="6cf61-129">如需其他範例，請參閱 [ALTER DATABASE SET 選項 &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options)。</span><span class="sxs-lookup"><span data-stu-id="6cf61-129">For more examples, see [ALTER DATABASE SET Options &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6cf61-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6cf61-130">See Also</span></span>  
 <span data-ttu-id="6cf61-131">[ALTER DATABASE 相容性層級 &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-compatibility-level) </span><span class="sxs-lookup"><span data-stu-id="6cf61-131">[ALTER DATABASE Compatibility Level &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-compatibility-level) </span></span>  
 <span data-ttu-id="6cf61-132">[ALTER DATABASE 資料庫鏡像 &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-database-mirroring) </span><span class="sxs-lookup"><span data-stu-id="6cf61-132">[ALTER DATABASE Database Mirroring &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-database-mirroring) </span></span>  
 <span data-ttu-id="6cf61-133">[ALTER DATABASE SET HADR &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-hadr) </span><span class="sxs-lookup"><span data-stu-id="6cf61-133">[ALTER DATABASE SET HADR &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-hadr) </span></span>  
 <span data-ttu-id="6cf61-134">[重新命名資料庫](rename-a-database.md) </span><span class="sxs-lookup"><span data-stu-id="6cf61-134">[Rename a Database](rename-a-database.md) </span></span>  
 [<span data-ttu-id="6cf61-135">壓縮資料庫</span><span class="sxs-lookup"><span data-stu-id="6cf61-135">Shrink a Database</span></span>](shrink-a-database.md)  
  
  
