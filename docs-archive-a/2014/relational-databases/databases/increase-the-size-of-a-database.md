---
title: 增加資料庫的大小 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- databases [SQL Server], size
- increasing database size
- database size [SQL Server], increasing
- size [SQL Server], databases
ms.assetid: 14f4206d-3afa-4ba9-9849-23e81d63306d
author: stevestein
ms.author: sstein
ms.openlocfilehash: 71dcb00b3f5525f7059fc54911baed929f763008
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709549"
---
# <a name="increase-the-size-of-a-database"></a><span data-ttu-id="2a376-102">增加資料庫的大小</span><span class="sxs-lookup"><span data-stu-id="2a376-102">Increase the Size of a Database</span></span>
  <span data-ttu-id="2a376-103">此主題描述如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中增加資料庫的大小。</span><span class="sxs-lookup"><span data-stu-id="2a376-103">This topic describes how to increase the size of a database in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="2a376-104">增加現有資料或記錄檔的大小或將新檔案加入資料庫中，可擴充資料庫。</span><span class="sxs-lookup"><span data-stu-id="2a376-104">The database is expanded by either increasing the size of an existing data or log file or by adding a new file to the database.</span></span>  
  
 <span data-ttu-id="2a376-105">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="2a376-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="2a376-106">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="2a376-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="2a376-107">限制事項</span><span class="sxs-lookup"><span data-stu-id="2a376-107">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="2a376-108">安全性</span><span class="sxs-lookup"><span data-stu-id="2a376-108">Security</span></span>](#Security)  
  
-   <span data-ttu-id="2a376-109">**使用下列方法增加資料庫的大小：**</span><span class="sxs-lookup"><span data-stu-id="2a376-109">**To increase the size of a database, using:**</span></span>  
  
     [<span data-ttu-id="2a376-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="2a376-110">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="2a376-111">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="2a376-111">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="2a376-112">開始之前</span><span class="sxs-lookup"><span data-stu-id="2a376-112">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="2a376-113">限制事項</span><span class="sxs-lookup"><span data-stu-id="2a376-113">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="2a376-114">當 BACKUP 陳述式在執行中，您不能新增或移除檔案。</span><span class="sxs-lookup"><span data-stu-id="2a376-114">You cannot add or remove a file while a BACKUP statement is running.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="2a376-115">Security</span><span class="sxs-lookup"><span data-stu-id="2a376-115">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="2a376-116">權限</span><span class="sxs-lookup"><span data-stu-id="2a376-116">Permissions</span></span>  
 <span data-ttu-id="2a376-117">需要資料庫的 ALTER 權限。</span><span class="sxs-lookup"><span data-stu-id="2a376-117">Requires ALTER permission on the database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="2a376-118">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="2a376-118">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-increase-the-size-of-a-database"></a><span data-ttu-id="2a376-119">若要增加資料庫的大小</span><span class="sxs-lookup"><span data-stu-id="2a376-119">To increase the size of a database</span></span>  
  
1.  <span data-ttu-id="2a376-120">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]的執行個體，然後展開該執行個體。</span><span class="sxs-lookup"><span data-stu-id="2a376-120">In **Object Explorer**, connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="2a376-121">展開 [資料庫]  ，以滑鼠右鍵按一下要增加的資料庫，然後按一下 [屬性]  。</span><span class="sxs-lookup"><span data-stu-id="2a376-121">Expand **Databases**, right-click the database to increase, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="2a376-122">在 **[資料庫屬性]** 中，選取 **[檔案]** 頁面。</span><span class="sxs-lookup"><span data-stu-id="2a376-122">In **Database Properties**, select the **Files** page.</span></span>  
  
4.  <span data-ttu-id="2a376-123">若要增加現有檔案的大小，請在 [初始大小 (MB)]  資料行中增加該檔案的值。</span><span class="sxs-lookup"><span data-stu-id="2a376-123">To increase the size of an existing file, increase the value in the **Initial Size (MB)** column for the file.</span></span> <span data-ttu-id="2a376-124">資料庫的大小至少必須增加 1MB。</span><span class="sxs-lookup"><span data-stu-id="2a376-124">You must increase the size of the database by at least 1 megabyte.</span></span>  
  
5.  <span data-ttu-id="2a376-125">若要加入新檔案來增加資料庫的大小，請按一下 **[加入]** ，再輸入新檔案的值。</span><span class="sxs-lookup"><span data-stu-id="2a376-125">To increase the size of the database by adding a new file, click **Add** and then enter the values for the new file.</span></span> <span data-ttu-id="2a376-126">如需詳細資訊，請參閱 [將資料或記錄檔加入資料庫](add-data-or-log-files-to-a-database.md)。</span><span class="sxs-lookup"><span data-stu-id="2a376-126">For more information, see [Add Data or Log Files to a Database](add-data-or-log-files-to-a-database.md).</span></span>  
  
6.  <span data-ttu-id="2a376-127">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="2a376-127">Click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="2a376-128">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="2a376-128">Using Transact-SQL</span></span>  
  
#### <a name="to-increase-the-size-of-a-database"></a><span data-ttu-id="2a376-129">若要增加資料庫的大小</span><span class="sxs-lookup"><span data-stu-id="2a376-129">To increase the size of a database</span></span>  
  
1.  <span data-ttu-id="2a376-130">連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="2a376-130">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="2a376-131">在標準列中，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="2a376-131">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="2a376-132">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="2a376-132">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="2a376-133">這個範例會增加 `test1dat3`檔案的大小。</span><span class="sxs-lookup"><span data-stu-id="2a376-133">This example increases the size of the file `test1dat3`.</span></span>  
  
 [!code-sql[DatabaseDDL#AlterDatabase5](../../snippets/tsql/SQL14/tsql/databaseddl/transact-sql/alterdatabase.sql#alterdatabase5)]  
  
 <span data-ttu-id="2a376-134">如需其他範例，請參閱 [ALTER DATABASE 檔案及檔案群組選項 &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-file-and-filegroup-options)。</span><span class="sxs-lookup"><span data-stu-id="2a376-134">For more examples, see [ALTER DATABASE File and Filegroup Options &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-file-and-filegroup-options).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a376-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2a376-135">See Also</span></span>  
 <span data-ttu-id="2a376-136">[將資料或記錄檔加入資料庫](add-data-or-log-files-to-a-database.md) </span><span class="sxs-lookup"><span data-stu-id="2a376-136">[Add Data or Log Files to a Database](add-data-or-log-files-to-a-database.md) </span></span>  
 [<span data-ttu-id="2a376-137">壓縮資料庫</span><span class="sxs-lookup"><span data-stu-id="2a376-137">Shrink a Database</span></span>](shrink-a-database.md)  
  
  
