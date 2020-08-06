---
title: 刪除資料庫的資料或記錄檔 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- logs [SQL Server], files
- deleting files
- removing files
- removing data
- data deletions [SQL Server]
- file deletion [SQL Server]
- deleting data
ms.assetid: 0db4018c-ce2c-4ba1-bb29-1e4f3791c925
author: stevestein
ms.author: sstein
ms.openlocfilehash: 6f7bd170e085e9bc94b00446545850e905efaa34
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709557"
---
# <a name="delete-data-or-log-files-from-a-database"></a><span data-ttu-id="3d403-102">刪除資料庫的資料或記錄檔</span><span class="sxs-lookup"><span data-stu-id="3d403-102">Delete Data or Log Files from a Database</span></span>
  <span data-ttu-id="3d403-103">此主題描述如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 來刪除 [!INCLUDE[tsql](../../includes/tsql-md.md)]中的資料或記錄檔。</span><span class="sxs-lookup"><span data-stu-id="3d403-103">This topic describes how to delete data or log files in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="3d403-104">開始之前</span><span class="sxs-lookup"><span data-stu-id="3d403-104">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="3d403-105">必要條件</span><span class="sxs-lookup"><span data-stu-id="3d403-105">Prerequisites</span></span>  
  
-   <span data-ttu-id="3d403-106">在刪除檔案之前，檔案必須空白。</span><span class="sxs-lookup"><span data-stu-id="3d403-106">A file must be empty before it can be deleted.</span></span> <span data-ttu-id="3d403-107">如需詳細資訊，請參閱 [壓縮檔案](shrink-a-file.md)。</span><span class="sxs-lookup"><span data-stu-id="3d403-107">For more information, see [Shrink a File](shrink-a-file.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="3d403-108">Security</span><span class="sxs-lookup"><span data-stu-id="3d403-108">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="3d403-109">權限</span><span class="sxs-lookup"><span data-stu-id="3d403-109">Permissions</span></span>  
 <span data-ttu-id="3d403-110">需要資料庫的 ALTER 權限。</span><span class="sxs-lookup"><span data-stu-id="3d403-110">Requires ALTER permission on the database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="3d403-111">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="3d403-111">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-delete-data-or-log-files-from-a-database"></a><span data-ttu-id="3d403-112">若要刪除資料庫的資料或記錄檔</span><span class="sxs-lookup"><span data-stu-id="3d403-112">To delete data or log files from a database</span></span>  
  
1.  <span data-ttu-id="3d403-113">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 的執行個體，然後展開該執行個體。</span><span class="sxs-lookup"><span data-stu-id="3d403-113">In **Object Explorer**, connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="3d403-114">展開 **[資料庫]** ，以滑鼠右鍵按一下要從中刪除檔案的資料庫，再按一下 **[屬性]** 。</span><span class="sxs-lookup"><span data-stu-id="3d403-114">Expand **Databases**, right-click the database from which to delete the file, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="3d403-115">選取 **[檔案]** 頁面。</span><span class="sxs-lookup"><span data-stu-id="3d403-115">Select the **Files** page.</span></span>  
  
4.  <span data-ttu-id="3d403-116">在 **[資料庫檔案]** 方格中，選取要刪除的檔案，再按一下 **[移除]** 。</span><span class="sxs-lookup"><span data-stu-id="3d403-116">In the **Database files** grid, select the file to delete and then click **Remove**.</span></span>  
  
5.  <span data-ttu-id="3d403-117">按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="3d403-117">Click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="3d403-118">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="3d403-118">Using Transact-SQL</span></span>  
  
#### <a name="to-delete-data-or-log-files-from-a-database"></a><span data-ttu-id="3d403-119">若要刪除資料庫的資料或記錄檔</span><span class="sxs-lookup"><span data-stu-id="3d403-119">To delete data or log files from a database</span></span>  
  
1.  <span data-ttu-id="3d403-120">連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="3d403-120">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="3d403-121">在標準列中，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="3d403-121">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="3d403-122">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="3d403-122">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="3d403-123">這個範例會移除 `test1dat4`檔案。</span><span class="sxs-lookup"><span data-stu-id="3d403-123">This example removes the file `test1dat4`.</span></span>  
  
 [!code-sql[DatabaseDDL#AlterDatabase4](../../snippets/tsql/SQL14/tsql/databaseddl/transact-sql/alterdatabase.sql#alterdatabase4)]  
  
 <span data-ttu-id="3d403-124">如需其他範例，請參閱 [ALTER DATABASE 檔案及檔案群組選項 &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-file-and-filegroup-options)。</span><span class="sxs-lookup"><span data-stu-id="3d403-124">For more examples, see [ALTER DATABASE File and Filegroup Options &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-file-and-filegroup-options).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d403-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3d403-125">See Also</span></span>  
 <span data-ttu-id="3d403-126">[壓縮資料庫](shrink-a-database.md) </span><span class="sxs-lookup"><span data-stu-id="3d403-126">[Shrink a Database](shrink-a-database.md) </span></span>  
 [<span data-ttu-id="3d403-127">將資料或記錄檔加入資料庫</span><span class="sxs-lookup"><span data-stu-id="3d403-127">Add Data or Log Files to a Database</span></span>](add-data-or-log-files-to-a-database.md)  
  
  
