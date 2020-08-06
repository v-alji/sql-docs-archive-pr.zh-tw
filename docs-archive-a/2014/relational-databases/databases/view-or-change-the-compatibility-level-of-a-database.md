---
title: 檢視或變更資料庫的相容性層級 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- compatibility levels [SQL Server], viewing
- compatibility [SQL Server], databases
- compatibility levels [SQL Server], changing
ms.assetid: 579867ec-57cb-4cb8-af35-9688c1e9e15d
author: stevestein
ms.author: sstein
ms.openlocfilehash: 35cf7af50eba333440c42a1bac428df1fff156b4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708441"
---
# <a name="view-or-change-the-compatibility-level-of-a-database"></a><span data-ttu-id="6bc69-102">檢視或變更資料庫的相容性層級</span><span class="sxs-lookup"><span data-stu-id="6bc69-102">View or Change the Compatibility Level of a Database</span></span>
  <span data-ttu-id="6bc69-103">此主題描述如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中檢視或變更資料庫的相容性層級。</span><span class="sxs-lookup"><span data-stu-id="6bc69-103">This topic describes how to view or change the compatibility level of a database in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="6bc69-104">在變更資料庫的相容性層級之前，您應該先了解此變更對應用程式的影響。</span><span class="sxs-lookup"><span data-stu-id="6bc69-104">Before you change the compatibility level of a database, you should understand the impact of the change on your applications.</span></span> <span data-ttu-id="6bc69-105">如需詳細資訊，請參閱 [ALTER DATABASE 相容性層級 &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-compatibility-level)。</span><span class="sxs-lookup"><span data-stu-id="6bc69-105">For more information, see [ALTER DATABASE Compatibility Level &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-compatibility-level).</span></span>  
  
 <span data-ttu-id="6bc69-106">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="6bc69-106">**In This Topic**</span></span>  
  
-   <span data-ttu-id="6bc69-107">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="6bc69-107">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="6bc69-108">安全性</span><span class="sxs-lookup"><span data-stu-id="6bc69-108">Security</span></span>](#Security)  
  
-   <span data-ttu-id="6bc69-109">**使用下列方法檢視或變更資料庫的相容性層級：**</span><span class="sxs-lookup"><span data-stu-id="6bc69-109">**To view or change the compatibility level of a database, using:**</span></span>  
  
     [<span data-ttu-id="6bc69-110">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="6bc69-110">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="6bc69-111">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="6bc69-111">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="6bc69-112">開始之前</span><span class="sxs-lookup"><span data-stu-id="6bc69-112">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="6bc69-113">Security</span><span class="sxs-lookup"><span data-stu-id="6bc69-113">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="6bc69-114">權限</span><span class="sxs-lookup"><span data-stu-id="6bc69-114">Permissions</span></span>  
 <span data-ttu-id="6bc69-115">需要資料庫的 ALTER 權限。</span><span class="sxs-lookup"><span data-stu-id="6bc69-115">Requires ALTER permission on the database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="6bc69-116">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="6bc69-116">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-view-or-change-the-compatibility-level-of-a-database"></a><span data-ttu-id="6bc69-117">檢視或變更資料庫的相容性層級</span><span class="sxs-lookup"><span data-stu-id="6bc69-117">To view or change the compatibility level of a database</span></span>  
  
1.  <span data-ttu-id="6bc69-118">連接到適當的 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]執行個體之後，請在 [物件總管] 中按一下伺服器名稱。</span><span class="sxs-lookup"><span data-stu-id="6bc69-118">After connecting to the appropriate instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], in Object Explorer, click the server name.</span></span>  
  
2.  <span data-ttu-id="6bc69-119">展開 **[資料庫]** ，然後視資料庫而定，選取使用者資料庫，或者展開 **[系統資料庫]** 並選取一個系統資料庫。</span><span class="sxs-lookup"><span data-stu-id="6bc69-119">Expand **Databases**, and, depending on the database, either select a user database or expand **System Databases** and select a system database.</span></span>  
  
3.  <span data-ttu-id="6bc69-120">以滑鼠右鍵按一下此資料庫，然後按一下 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="6bc69-120">Right-click the database, and then click **Properties**.</span></span>  
  
     <span data-ttu-id="6bc69-121">**[資料庫屬性]** 對話方塊隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="6bc69-121">The **Database Properties** dialog box opens.</span></span>  
  
4.  <span data-ttu-id="6bc69-122">在 **[選取頁面]** 窗格中，按一下 **[選項]** 。</span><span class="sxs-lookup"><span data-stu-id="6bc69-122">In the **Select a page** pane, click **Options**.</span></span>  
  
     <span data-ttu-id="6bc69-123">目前的相容性層級會顯示在 **[相容性層級]** 清單方塊中。</span><span class="sxs-lookup"><span data-stu-id="6bc69-123">The current compatibility level is displayed in the **Compatibility level** list box.</span></span>  
  
5.  <span data-ttu-id="6bc69-124">若要變更相容性層級，請從清單中選取其他選項。</span><span class="sxs-lookup"><span data-stu-id="6bc69-124">To change the compatibility level, select a different option from the list.</span></span> <span data-ttu-id="6bc69-125">這些選項包括 [SQL Server 2008 (100)]\*\*\*\*、[SQL Server 2012 (110)]\*\*\*\* 或 [SQL Server 2014 (120)]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="6bc69-125">The choices are **SQL Server 2008 (100)**, **SQL Server 2012 (110)**, or **SQL Server 2014 (120)**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="6bc69-126">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="6bc69-126">Using Transact-SQL</span></span>  
  
#### <a name="to-view-the-compatibility-level-of-a-database"></a><span data-ttu-id="6bc69-127">檢視資料庫的相容性層級</span><span class="sxs-lookup"><span data-stu-id="6bc69-127">To view the compatibility level of a database</span></span>  
  
1.  <span data-ttu-id="6bc69-128">連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="6bc69-128">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="6bc69-129">在標準列中，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="6bc69-129">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="6bc69-130">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="6bc69-130">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="6bc69-131">這個範例會傳回 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 資料庫的相容性層級。</span><span class="sxs-lookup"><span data-stu-id="6bc69-131">This example returns the compatibility level of the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database.</span></span>  
  
```sql  
USE AdventureWorks2012;  
GO  
SELECT compatibility_level  
FROM sys.databases WHERE name = 'AdventureWorks2012';  
GO  
  
```  
  
#### <a name="to-change-the-compatibility-level-of-a-database"></a><span data-ttu-id="6bc69-132">變更資料庫的相容性層級</span><span class="sxs-lookup"><span data-stu-id="6bc69-132">To change the compatibility level of a database</span></span>  
  
1.  <span data-ttu-id="6bc69-133">連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="6bc69-133">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="6bc69-134">在標準列中，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="6bc69-134">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="6bc69-135">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="6bc69-135">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="6bc69-136">這個範例會變更的相容性層級 [!INCLUDE[ssSampleDBobject](../../includes/sssql14-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="6bc69-136">This example changes the compatibility level of the [!INCLUDE[ssSampleDBobject](../../includes/sssql14-md.md)].</span></span>  
  
```sql  
ALTER DATABASE AdventureWorks2012  
SET COMPATIBILITY_LEVEL = 120;  
GO  
```  
  
  
