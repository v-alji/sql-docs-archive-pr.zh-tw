---
title: 重新命名資料庫 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- databases [SQL Server], renaming
- renaming databases
ms.assetid: 44c69d35-abcb-4da3-9370-5e0bc9a28496
author: stevestein
ms.author: sstein
ms.openlocfilehash: dd25a78e3d3b9be2e7191ce6ed3d6bdcbb0f9606
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595097"
---
# <a name="rename-a-database"></a><span data-ttu-id="47a24-102">重新命名資料庫</span><span class="sxs-lookup"><span data-stu-id="47a24-102">Rename a Database</span></span>
  <span data-ttu-id="47a24-103">此主題描述如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中重新命名使用者定義資料庫。</span><span class="sxs-lookup"><span data-stu-id="47a24-103">This topic describes how to rename a user-defined database in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="47a24-104">資料庫的名稱可以包含任何依照識別碼規則的字元。</span><span class="sxs-lookup"><span data-stu-id="47a24-104">The name of the database can include any characters that follow the rules for identifiers.</span></span>  
  
 <span data-ttu-id="47a24-105">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="47a24-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="47a24-106">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="47a24-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="47a24-107">限制事項</span><span class="sxs-lookup"><span data-stu-id="47a24-107">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="47a24-108">安全性</span><span class="sxs-lookup"><span data-stu-id="47a24-108">Security</span></span>](#Security)  
  
-   <span data-ttu-id="47a24-109">**使用下列方法重新命名資料庫：**</span><span class="sxs-lookup"><span data-stu-id="47a24-109">**To rename a database, using:**</span></span>  
  
     [<span data-ttu-id="47a24-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="47a24-110">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="47a24-111">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="47a24-111">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   <span data-ttu-id="47a24-112">**後續操作：** [重新命名資料庫之後](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="47a24-112">**Follow Up:**  [After renaming a database](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="47a24-113">開始之前</span><span class="sxs-lookup"><span data-stu-id="47a24-113">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="47a24-114">限制事項</span><span class="sxs-lookup"><span data-stu-id="47a24-114">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="47a24-115">您無法重新命名系統資料庫。</span><span class="sxs-lookup"><span data-stu-id="47a24-115">System databases cannot be renamed.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="47a24-116">Security</span><span class="sxs-lookup"><span data-stu-id="47a24-116">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="47a24-117">權限</span><span class="sxs-lookup"><span data-stu-id="47a24-117">Permissions</span></span>  
 <span data-ttu-id="47a24-118">需要資料庫的 ALTER 權限。</span><span class="sxs-lookup"><span data-stu-id="47a24-118">Requires ALTER permission on the database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="47a24-119">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="47a24-119">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-rename-a-database"></a><span data-ttu-id="47a24-120">若要重新命名資料庫</span><span class="sxs-lookup"><span data-stu-id="47a24-120">To rename a database</span></span>  
  
1.  <span data-ttu-id="47a24-121">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]的執行個體，然後展開該執行個體。</span><span class="sxs-lookup"><span data-stu-id="47a24-121">In **Object Explorer**, connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="47a24-122">確定沒有人使用此資料庫，然後 [將資料庫設定為單一使用者模式](set-a-database-to-single-user-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="47a24-122">Make sure that no one is using the database, and then [set the database to single-user mode](set-a-database-to-single-user-mode.md).</span></span>  
  
3.  <span data-ttu-id="47a24-123">展開 [資料庫]\*\*\*\*，以滑鼠右鍵按一下要重新命名的資料庫，然後按一下 [重新命名]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="47a24-123">Expand **Databases**, right-click the database to rename, and then click **Rename**.</span></span>  
  
4.  <span data-ttu-id="47a24-124">輸入新的資料庫名稱，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="47a24-124">Enter the new database name, and then click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="47a24-125">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="47a24-125">Using Transact-SQL</span></span>  
  
#### <a name="to-rename-a-database"></a><span data-ttu-id="47a24-126">若要重新命名資料庫</span><span class="sxs-lookup"><span data-stu-id="47a24-126">To rename a database</span></span>  
  
1.  <span data-ttu-id="47a24-127">連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="47a24-127">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="47a24-128">在標準列中，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="47a24-128">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="47a24-129">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="47a24-129">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="47a24-130">這個範例會將 `AdventureWorks2012` 資料庫的名稱變更為 `Northwind`。</span><span class="sxs-lookup"><span data-stu-id="47a24-130">This example changes the name of the `AdventureWorks2012` database to `Northwind`.</span></span>  
  
```sql  
USE master;  
GO  
ALTER DATABASE AdventureWorks2012  
Modify Name = Northwind ;  
GO  
```  
  
###  <a name="TsqlExample"></a>   
##  <a name="follow-up-after-renaming-a-database"></a><a name="FollowUp"></a> <span data-ttu-id="47a24-131">待處理：重新命名資料庫之後</span><span class="sxs-lookup"><span data-stu-id="47a24-131">Follow Up: After renaming a database</span></span>  
 <span data-ttu-id="47a24-132">重新命名任何資料庫之後，請備份 **master** 資料庫。</span><span class="sxs-lookup"><span data-stu-id="47a24-132">Back up the **master** database after you rename any database.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47a24-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="47a24-133">See Also</span></span>  
 <span data-ttu-id="47a24-134">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="47a24-134">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span></span>  
 [<span data-ttu-id="47a24-135">資料庫識別碼</span><span class="sxs-lookup"><span data-stu-id="47a24-135">Database Identifiers</span></span>](database-identifiers.md)  
  
  
