---
title: 將資料或記錄檔新增至資料庫 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- logs [SQL Server], files
- adding data files
- adding files
- adding log files
- file additions [SQL Server], steps
- files [SQL Server], adding
- data additions [SQL Server]
ms.assetid: 8ead516a-1334-4f40-84b2-509d0a8ffa45
author: stevestein
ms.author: sstein
ms.openlocfilehash: f72e00f9dab422652237b4b85579c544d0cda9fb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709598"
---
# <a name="add-data-or-log-files-to-a-database"></a><span data-ttu-id="11545-102">將資料或記錄檔加入資料庫</span><span class="sxs-lookup"><span data-stu-id="11545-102">Add Data or Log Files to a Database</span></span>
  <span data-ttu-id="11545-103">此主題描述如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中將資料或記錄檔加入至資料庫。</span><span class="sxs-lookup"><span data-stu-id="11545-103">This topic describes how to add data or log files to a database in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="11545-104">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="11545-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="11545-105">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="11545-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="11545-106">限制事項</span><span class="sxs-lookup"><span data-stu-id="11545-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="11545-107">安全性</span><span class="sxs-lookup"><span data-stu-id="11545-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="11545-108">**使用下列方法，將資料或記錄檔加入資料庫：**</span><span class="sxs-lookup"><span data-stu-id="11545-108">**To add data or log files to a database, using:**</span></span>  
  
     [<span data-ttu-id="11545-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="11545-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="11545-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="11545-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="11545-111">開始之前</span><span class="sxs-lookup"><span data-stu-id="11545-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="11545-112">限制事項</span><span class="sxs-lookup"><span data-stu-id="11545-112">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="11545-113">當 BACKUP 陳述式在執行中，您不能新增或移除檔案。</span><span class="sxs-lookup"><span data-stu-id="11545-113">You cannot add or remove a file while a BACKUP statement is running.</span></span>  
  
-   <span data-ttu-id="11545-114">每個資料庫最多可以指定 32,767 個檔案和 32,767 個檔案群組。</span><span class="sxs-lookup"><span data-stu-id="11545-114">A maximum of 32,767 files and 32,767 filegroups can be specified for each database.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="11545-115">Security</span><span class="sxs-lookup"><span data-stu-id="11545-115">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="11545-116">權限</span><span class="sxs-lookup"><span data-stu-id="11545-116">Permissions</span></span>  
 <span data-ttu-id="11545-117">需要資料庫的 ALTER 權限。</span><span class="sxs-lookup"><span data-stu-id="11545-117">Requires ALTER permission on the database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="11545-118">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="11545-118">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-add-data-or-log-files-to-a-database"></a><span data-ttu-id="11545-119">若要將資料或記錄檔加入資料庫</span><span class="sxs-lookup"><span data-stu-id="11545-119">To add data or log files to a database</span></span>  
  
1.  <span data-ttu-id="11545-120">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 的執行個體，然後展開該執行個體。</span><span class="sxs-lookup"><span data-stu-id="11545-120">In **Object Explorer**, connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="11545-121">展開 [資料庫]，以滑鼠右鍵按一下要加入檔案的來源資料庫，然後按一下 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="11545-121">Expand **Databases**, right-click the database from which to add the files, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="11545-122">在 **[資料庫屬性]** 對話方塊中，選取 **[檔案]** 頁面。</span><span class="sxs-lookup"><span data-stu-id="11545-122">In the **Database Properties** dialog box, select the **Files** page.</span></span>  
  
4.  <span data-ttu-id="11545-123">若要加入資料或交易記錄檔，請按一下 **[加入]** 。</span><span class="sxs-lookup"><span data-stu-id="11545-123">To add a data or transaction log file, click **Add**.</span></span>  
  
5.  <span data-ttu-id="11545-124">在 **[資料庫檔案]** 方格中，輸入檔案的邏輯名稱。</span><span class="sxs-lookup"><span data-stu-id="11545-124">In the **Database files** grid, enter a logical name for the file.</span></span> <span data-ttu-id="11545-125">檔案名稱在資料庫中必須是唯一的。</span><span class="sxs-lookup"><span data-stu-id="11545-125">The file name must be unique within the database.</span></span>  
  
6.  <span data-ttu-id="11545-126">選取檔案類型：資料或記錄檔。</span><span class="sxs-lookup"><span data-stu-id="11545-126">Select the file type, data or log.</span></span>  
  
7.  <span data-ttu-id="11545-127">針對資料檔，請選取檔案群組，其中所包含的檔案該位於清單中，或選取 **\<new filegroup>** 以建立新檔案群組。</span><span class="sxs-lookup"><span data-stu-id="11545-127">For a data file, select the filegroup in which the file should be included from the list, or select **\<new filegroup>** to create a new filegroup.</span></span> <span data-ttu-id="11545-128">交易記錄檔無法放在檔案群組中。</span><span class="sxs-lookup"><span data-stu-id="11545-128">Transaction logs cannot be put in filegroups.</span></span>  
  
8.  <span data-ttu-id="11545-129">指定檔案的起始大小。</span><span class="sxs-lookup"><span data-stu-id="11545-129">Specify the initial size of the file.</span></span> <span data-ttu-id="11545-130">可根據預期的資料庫最大資料量，儘可能將資料檔設為最大。</span><span class="sxs-lookup"><span data-stu-id="11545-130">Make the data file as large as possible, based on the maximum amount of data you expect in the database.</span></span>  
  
9. <span data-ttu-id="11545-131">若要指定檔案應該如何成長，請按一下 [自動成長] 資料行中的 ( **…** )。</span><span class="sxs-lookup"><span data-stu-id="11545-131">To specify how the file should grow, click (**...**) in the **Autogrowth** column.</span></span> <span data-ttu-id="11545-132">然後選取下列選項：</span><span class="sxs-lookup"><span data-stu-id="11545-132">Select from the following options:</span></span>  
  
    1.  <span data-ttu-id="11545-133">若要允許目前選取的檔案依所需的資料空間成長，請選取 **[啟用自動成長]** 核取方塊，然後選取下列選項：</span><span class="sxs-lookup"><span data-stu-id="11545-133">To allow for the currently selected file to grow as more data space is required, select the **Enable Autogrowth** check box and then select from the following options:</span></span>  
  
    2.  <span data-ttu-id="11545-134">若要指定檔案以固定遞增值成長，請選取 **[以 MB 表示]** ，然後指定一個值。</span><span class="sxs-lookup"><span data-stu-id="11545-134">To specify that the file should grow by fixed increments, select **In Megabytes** and specify a value.</span></span>  
  
    3.  <span data-ttu-id="11545-135">若要指定檔案依照目前檔案大小的百分比成長，請選取 **[以百分比表示]** ，然後指定一個值。</span><span class="sxs-lookup"><span data-stu-id="11545-135">To specify that the file should grow by a percentage of the current file size, select **In Percent** and specify a value.</span></span>  
  
10. <span data-ttu-id="11545-136">若要指定檔案大小上限，請選取下列些選項：</span><span class="sxs-lookup"><span data-stu-id="11545-136">To specify the maximum file size limit, select from the following options:</span></span>  
  
    1.  <span data-ttu-id="11545-137">若要指定檔案大小可以成長的上限，請選取 [限制的檔案成長 (MB)]，然後指定一個值。</span><span class="sxs-lookup"><span data-stu-id="11545-137">To specify the maximum size the file should be able to grow to, select **Restricted File Growth (MB)** and specify a value.</span></span>  
  
    2.  <span data-ttu-id="11545-138">若要讓檔案依照需要成長，請選取 **[不限制檔案成長]** 。</span><span class="sxs-lookup"><span data-stu-id="11545-138">To allow for the file to grow as much as needed, select **Unrestricted File Growth**.</span></span>  
  
    3.  <span data-ttu-id="11545-139">若要防止檔案成長，請清除 **[啟用自動成長]** 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="11545-139">To prevent the file from growing, clear the **Enable Autogrowth** check box.</span></span> <span data-ttu-id="11545-140">檔案成長的大小將不會超過 [初始大小 (MB)] 資料行中所指定的值。</span><span class="sxs-lookup"><span data-stu-id="11545-140">The size of the file will not grow beyond the value specified in the **Initial Size (MB)** column.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="11545-141">資料庫大小的上限取決於可用的磁碟空間，及所使用的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 版本的授權限制。</span><span class="sxs-lookup"><span data-stu-id="11545-141">The maximum database size is determined by the amount of disk space available and the licensing limits determined by the version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that you are using.</span></span>  
  
11. <span data-ttu-id="11545-142">指定檔案位置的路徑。</span><span class="sxs-lookup"><span data-stu-id="11545-142">Specify the path for the file location.</span></span> <span data-ttu-id="11545-143">在加入檔案之前必須先指定路徑。</span><span class="sxs-lookup"><span data-stu-id="11545-143">The specified path must exist before adding the file.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="11545-144">依預設，資料和交易記錄是放在相同的磁碟及路徑中以配合單一磁碟系統，但在實際執行環境中可能不是最理想的。</span><span class="sxs-lookup"><span data-stu-id="11545-144">By default, the data and transaction logs are put on the same drive and path to accommodate single-disk systems, but may not be optimal for production environments.</span></span> <span data-ttu-id="11545-145">如需相關資訊，請參閱 [Database Files and Filegroups](database-files-and-filegroups.md)。</span><span class="sxs-lookup"><span data-stu-id="11545-145">For more information, see [Database Files and Filegroups](database-files-and-filegroups.md).</span></span>  
  
12. <span data-ttu-id="11545-146">按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="11545-146">Click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="11545-147">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="11545-147">Using Transact-SQL</span></span>  
  
#### <a name="to-add-data-or-log-files-to-a-database"></a><span data-ttu-id="11545-148">若要將資料或記錄檔加入資料庫</span><span class="sxs-lookup"><span data-stu-id="11545-148">To add data or log files to a database</span></span>  
  
1.  <span data-ttu-id="11545-149">連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="11545-149">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="11545-150">在標準列中，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="11545-150">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="11545-151">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="11545-151">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="11545-152">此範例會將含有兩個檔案的檔案群組加入資料庫中。</span><span class="sxs-lookup"><span data-stu-id="11545-152">The example adds a filegroup with two files to a database.</span></span> <span data-ttu-id="11545-153">此範例會在 `Test1FG1` 資料庫中建立 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 檔案群組，且會將兩個 5 MB 的檔案加入檔案群組中。</span><span class="sxs-lookup"><span data-stu-id="11545-153">The example creates the filegroup `Test1FG1` in the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database and adds two 5-MB files to the filegroup.</span></span>  
  
 [!code-sql[DatabaseDDL#AlterDatabase2](../../snippets/tsql/SQL14/tsql/databaseddl/transact-sql/alterdatabase.sql#alterdatabase2)]  
  
 <span data-ttu-id="11545-154">如需其他範例，請參閱 [ALTER DATABASE 檔案及檔案群組選項 &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-file-and-filegroup-options)。</span><span class="sxs-lookup"><span data-stu-id="11545-154">For more examples, see [ALTER DATABASE File and Filegroup Options &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-file-and-filegroup-options).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11545-155">另請參閱</span><span class="sxs-lookup"><span data-stu-id="11545-155">See Also</span></span>  
 <span data-ttu-id="11545-156">[Database Files and Filegroups](database-files-and-filegroups.md) </span><span class="sxs-lookup"><span data-stu-id="11545-156">[Database Files and Filegroups](database-files-and-filegroups.md) </span></span>  
 <span data-ttu-id="11545-157">[刪除資料庫的資料或記錄檔](delete-data-or-log-files-from-a-database.md) </span><span class="sxs-lookup"><span data-stu-id="11545-157">[Delete Data or Log Files from a Database](delete-data-or-log-files-from-a-database.md) </span></span>  
 [<span data-ttu-id="11545-158">增加資料庫的大小</span><span class="sxs-lookup"><span data-stu-id="11545-158">Increase the Size of a Database</span></span>](increase-the-size-of-a-database.md)  
  
  
