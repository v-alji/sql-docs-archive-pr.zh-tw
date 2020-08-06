---
title: 附加資料庫 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
f1_keywords:
- sql12.swb.attachdatabase.f1
helpviewer_keywords:
- database attaching [SQL Server]
- attaching databases [SQL Server]
ms.assetid: b4efb0ae-cfe6-4d81-a4b4-6e4916885caa
author: stevestein
ms.author: sstein
ms.openlocfilehash: cb11b5c257007872e92d3f0a7eadb3e46b4969cd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709593"
---
# <a name="attach-a-database"></a><span data-ttu-id="a14cc-102">附加資料庫</span><span class="sxs-lookup"><span data-stu-id="a14cc-102">Attach a Database</span></span>
  <span data-ttu-id="a14cc-103">此主題描述如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中附加資料庫。</span><span class="sxs-lookup"><span data-stu-id="a14cc-103">This topic describes how to attach a database in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="a14cc-104">您可以使用此功能來複製、移動或升級 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫。</span><span class="sxs-lookup"><span data-stu-id="a14cc-104">You can use this feature to copy, move, or upgrade a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database.</span></span>  
  
 <span data-ttu-id="a14cc-105">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="a14cc-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="a14cc-106">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="a14cc-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="a14cc-107">先決條件</span><span class="sxs-lookup"><span data-stu-id="a14cc-107">Prerequisites</span></span>](#Prerequisites)  
  
     [<span data-ttu-id="a14cc-108">建議</span><span class="sxs-lookup"><span data-stu-id="a14cc-108">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="a14cc-109">安全性</span><span class="sxs-lookup"><span data-stu-id="a14cc-109">Security</span></span>](#Security)  
  
-   <span data-ttu-id="a14cc-110">**使用下列方法附加資料庫：**</span><span class="sxs-lookup"><span data-stu-id="a14cc-110">**To Attach a Database by using:**</span></span>  
  
     [<span data-ttu-id="a14cc-111">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="a14cc-111">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="a14cc-112">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="a14cc-112">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   <span data-ttu-id="a14cc-113">**後續操作：**  [升級資料庫之後](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="a14cc-113">**Follow Up:**  [After Upgrading a Database](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="a14cc-114">開始之前</span><span class="sxs-lookup"><span data-stu-id="a14cc-114">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="a14cc-115">必要條件</span><span class="sxs-lookup"><span data-stu-id="a14cc-115">Prerequisites</span></span>  
  
-   <span data-ttu-id="a14cc-116">資料庫必須先卸離。</span><span class="sxs-lookup"><span data-stu-id="a14cc-116">The database must first be detached.</span></span> <span data-ttu-id="a14cc-117">嘗試附加未卸離的資料庫會傳回錯誤。</span><span class="sxs-lookup"><span data-stu-id="a14cc-117">Attempting to attach a database that has not been detached will return an error.</span></span> <span data-ttu-id="a14cc-118">如需詳細資訊，請參閱 [卸離資料庫](detach-a-database.md)。</span><span class="sxs-lookup"><span data-stu-id="a14cc-118">For more information, see [Detach a Database](detach-a-database.md).</span></span>  
  
-   <span data-ttu-id="a14cc-119">當您附加資料庫時，所有的資料檔案 (MDF 和 LDF 檔案) 都必須可供使用。</span><span class="sxs-lookup"><span data-stu-id="a14cc-119">When you attach a database, all data files (MDF and LDF files) must be available.</span></span> <span data-ttu-id="a14cc-120">如果資料檔案的路徑與資料庫第一次建立或最後一次附加時的路徑不同，您必須指定檔案的目前路徑。</span><span class="sxs-lookup"><span data-stu-id="a14cc-120">If any data file has a different path from when the database was first created or last attached, you must specify the current path of the file.</span></span>  
  
-   <span data-ttu-id="a14cc-121">在您附加資料庫時，如果 MDF 和 LDF 檔案位於不同的目錄，而且其中一個路徑包括 \\\\?\GlobalRoot，作業將會失敗。</span><span class="sxs-lookup"><span data-stu-id="a14cc-121">When you attach a database, if MDF and LDF files are located in different directories and one of the paths includes \\\\?\GlobalRoot, the operation will fail.</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="a14cc-122">建議</span><span class="sxs-lookup"><span data-stu-id="a14cc-122">Recommendations</span></span>  
<span data-ttu-id="a14cc-123">建議您使用規劃的重新配置程式來移動資料庫 `ALTER DATABASE` ，而不要使用卸離和附加。</span><span class="sxs-lookup"><span data-stu-id="a14cc-123">We recommend that you move databases by using the `ALTER DATABASE` planned relocation procedure, instead of using detach and attach.</span></span> <span data-ttu-id="a14cc-124">如需詳細資訊，請參閱 [移動使用者資料庫](move-user-databases.md)。</span><span class="sxs-lookup"><span data-stu-id="a14cc-124">For more information, see [Move User Databases](move-user-databases.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="a14cc-125">Security</span><span class="sxs-lookup"><span data-stu-id="a14cc-125">Security</span></span>  
<span data-ttu-id="a14cc-126">檔案存取權限是在數個資料庫作業期間設定，包括卸離或附加資料庫。</span><span class="sxs-lookup"><span data-stu-id="a14cc-126">File access permissions are set during a number of database operations, including detaching or attaching a database.</span></span> <span data-ttu-id="a14cc-127">如需有關卸離和附加資料庫時所設定之檔案權限的詳細資訊，請參閱《 [線上叢書》中的](https://technet.microsoft.com/library/ms189128.aspx) 保護資料和記錄檔 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="a14cc-127">For information about file permissions that are set whenever a database is detached and attached, see [Securing Data and Log Files](https://technet.microsoft.com/library/ms189128.aspx) in [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] Books Online.</span></span>  
  
<span data-ttu-id="a14cc-128">建議您不要附加或還原來源不明或來源不受信任的資料庫。</span><span class="sxs-lookup"><span data-stu-id="a14cc-128">We recommend that you do not attach or restore databases from unknown or untrusted sources.</span></span> <span data-ttu-id="a14cc-129">這種資料庫可能包含惡意程式碼，因此可能執行非預期的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 程式碼，或是修改結構描述或實體資料庫結構而造成錯誤。</span><span class="sxs-lookup"><span data-stu-id="a14cc-129">Such databases could contain malicious code that might execute unintended [!INCLUDE[tsql](../../includes/tsql-md.md)] code or cause errors by modifying the schema or the physical database structure.</span></span> <span data-ttu-id="a14cc-130">使用來源不明或來源不受信任的資料庫之前，請先在非實際執行伺服器的資料庫上執行 [DBCC CHECKDB](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) ，同時檢查資料庫中的程式碼，例如預存程序或其他使用者定義程式碼。</span><span class="sxs-lookup"><span data-stu-id="a14cc-130">Before you use a database from an unknown or untrusted source, run [DBCC CHECKDB](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) on the database on a nonproduction server and also examine the code, such as stored procedures or other user-defined code, in the database.</span></span> <span data-ttu-id="a14cc-131">如需附加資料庫的詳細資訊，以及附加資料庫時，對中繼資料所做變更的相關資訊，請參閱[資料庫卸離與附加 &#40;SQL Server&#41;](database-detach-and-attach-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="a14cc-131">For more information about attaching databases and information about changes that are made to metadata when you attach a database, see [Database Detach and Attach &#40;SQL Server&#41;](database-detach-and-attach-sql-server.md).</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="a14cc-132">權限</span><span class="sxs-lookup"><span data-stu-id="a14cc-132">Permissions</span></span>  
<span data-ttu-id="a14cc-133">需要 `CREATE DATABASE`、`CREATE ANY DATABASE` 或 `ALTER ANY DATABASE` 權限。</span><span class="sxs-lookup"><span data-stu-id="a14cc-133">Requires `CREATE DATABASE`, `CREATE ANY DATABASE`, or `ALTER ANY DATABASE` permission.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="a14cc-134">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="a14cc-134">Using SQL Server Management Studio</span></span>  
  
### <a name="to-attach-a-database"></a><span data-ttu-id="a14cc-135">附加資料庫</span><span class="sxs-lookup"><span data-stu-id="a14cc-135">To Attach a Database</span></span>  
  
1.  <span data-ttu-id="a14cc-136">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 的 [物件總管] 中，連接到 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]的執行個體，然後展開該執行個體。</span><span class="sxs-lookup"><span data-stu-id="a14cc-136">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] Object Explorer, connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="a14cc-137">以滑鼠右鍵按一下 **[資料庫]** ，然後按一下 **[附加]** 。</span><span class="sxs-lookup"><span data-stu-id="a14cc-137">Right-click **Databases** and click **Attach**.</span></span>  
  
3.  <span data-ttu-id="a14cc-138">在 **[附加資料庫]** 對話方塊中，若要指定要附加的資料庫，請按一下 **[加入]** ；在 **[尋找資料庫檔案]** 對話方塊中，選取資料庫所在的磁碟機、展開目錄樹狀結構，尋找並選取資料庫的 .mdf 檔案；例如：</span><span class="sxs-lookup"><span data-stu-id="a14cc-138">In the **Attach Databases** dialog box, to specify the database to be attached, click **Add**; and in the **Locate Database Files** dialog box, select the disk drive where the database resides and expand the directory tree to find and select the .mdf file of the database; for example:</span></span>  
  
     `C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\DATA\AdventureWorks2012_Data.mdf`  
  
    > [!IMPORTANT]  
    > <span data-ttu-id="a14cc-139">嘗試選取已經附加的資料庫，會產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="a14cc-139">Trying to select a database that is already attached generates an error.</span></span>  
  
     <span data-ttu-id="a14cc-140">**[要附加的資料庫]**</span><span class="sxs-lookup"><span data-stu-id="a14cc-140">**Databases to attach**</span></span>  
     <span data-ttu-id="a14cc-141">顯示有關所選資料庫的資訊。</span><span class="sxs-lookup"><span data-stu-id="a14cc-141">Displays information about the selected databases.</span></span>  
  
     \<no column header>  
     <span data-ttu-id="a14cc-142">顯示指出附加作業之狀態的圖示。</span><span class="sxs-lookup"><span data-stu-id="a14cc-142">Displays an icon indicating the status of the attach operation.</span></span> <span data-ttu-id="a14cc-143">可能的圖示將在以下的 **[狀態]** 描述中加以描述。</span><span class="sxs-lookup"><span data-stu-id="a14cc-143">The possible icons are described in the **Status** description, below).</span></span>  
  
     <span data-ttu-id="a14cc-144">**MDF 檔案位置**</span><span class="sxs-lookup"><span data-stu-id="a14cc-144">**MDF File Location**</span></span>  
     <span data-ttu-id="a14cc-145">顯示選取之 MDF 檔的路徑和檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="a14cc-145">Displays the path and file name of the selected MDF file.</span></span>  
  
     <span data-ttu-id="a14cc-146">**Database Name**</span><span class="sxs-lookup"><span data-stu-id="a14cc-146">**Database Name**</span></span>  
     <span data-ttu-id="a14cc-147">顯示資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="a14cc-147">Displays the name of the database.</span></span>  
  
     <span data-ttu-id="a14cc-148">**附加為**</span><span class="sxs-lookup"><span data-stu-id="a14cc-148">**Attach As**</span></span>  
     <span data-ttu-id="a14cc-149">選擇性地針對要附加的資料庫指定不同的名稱。</span><span class="sxs-lookup"><span data-stu-id="a14cc-149">Optionally, specifies a different name for the database to attach as.</span></span>  
  
     <span data-ttu-id="a14cc-150">**擁有者**</span><span class="sxs-lookup"><span data-stu-id="a14cc-150">**Owner**</span></span>  
     <span data-ttu-id="a14cc-151">提供包含可能的資料庫擁有者的下拉式清單，且您可以選擇性地從中選取不同的擁有者。</span><span class="sxs-lookup"><span data-stu-id="a14cc-151">Provides a drop-down list of possible database owners from which you can optionally select a different owner.</span></span>  
  
     <span data-ttu-id="a14cc-152">**狀態**</span><span class="sxs-lookup"><span data-stu-id="a14cc-152">**Status**</span></span>  
     <span data-ttu-id="a14cc-153">根據下表顯示資料庫的狀態。</span><span class="sxs-lookup"><span data-stu-id="a14cc-153">Displays the status of the database according to the following table.</span></span>  
  
    |<span data-ttu-id="a14cc-154">圖示</span><span class="sxs-lookup"><span data-stu-id="a14cc-154">Icon</span></span>|<span data-ttu-id="a14cc-155">狀態文字</span><span class="sxs-lookup"><span data-stu-id="a14cc-155">Status text</span></span>|<span data-ttu-id="a14cc-156">描述</span><span class="sxs-lookup"><span data-stu-id="a14cc-156">Description</span></span>|  
    |----------|-----------------|-----------------|  
    |<span data-ttu-id="a14cc-157">(無圖示)</span><span class="sxs-lookup"><span data-stu-id="a14cc-157">(No icon)</span></span>|<span data-ttu-id="a14cc-158">(沒有文字)</span><span class="sxs-lookup"><span data-stu-id="a14cc-158">(No text)</span></span>|<span data-ttu-id="a14cc-159">附加作業尚未啟動或是針對此物件進行暫止。</span><span class="sxs-lookup"><span data-stu-id="a14cc-159">Attach operation has not been started or may be pending for this object.</span></span> <span data-ttu-id="a14cc-160">當對話方塊開啟時，這是預設的動作。</span><span class="sxs-lookup"><span data-stu-id="a14cc-160">This is the default when the dialog is opened.</span></span>|  
    |<span data-ttu-id="a14cc-161">綠色、指向右方的三角形</span><span class="sxs-lookup"><span data-stu-id="a14cc-161">Green, right-pointing triangle</span></span>|<span data-ttu-id="a14cc-162">進行中</span><span class="sxs-lookup"><span data-stu-id="a14cc-162">In progress</span></span>|<span data-ttu-id="a14cc-163">附加作業已啟動，但尚未完成。</span><span class="sxs-lookup"><span data-stu-id="a14cc-163">Attach operation has been started but it is not complete.</span></span>|  
    |<span data-ttu-id="a14cc-164">綠色的核取記號</span><span class="sxs-lookup"><span data-stu-id="a14cc-164">Green check mark</span></span>|<span data-ttu-id="a14cc-165">Success</span><span class="sxs-lookup"><span data-stu-id="a14cc-165">Success</span></span>|<span data-ttu-id="a14cc-166">已順利附加物件。</span><span class="sxs-lookup"><span data-stu-id="a14cc-166">The object has been attached successfully.</span></span>|  
    |<span data-ttu-id="a14cc-167">包含白色十字的紅色圓圈</span><span class="sxs-lookup"><span data-stu-id="a14cc-167">Red circle containing a white cross</span></span>|<span data-ttu-id="a14cc-168">錯誤</span><span class="sxs-lookup"><span data-stu-id="a14cc-168">Error</span></span>|<span data-ttu-id="a14cc-169">附加作業發生錯誤，且未順利完成。</span><span class="sxs-lookup"><span data-stu-id="a14cc-169">Attach operation encountered an error and did not complete successfully.</span></span>|  
    |<span data-ttu-id="a14cc-170">包含兩個黑色的象限 (在左方和右方) 以及兩個白色的象限 (在上方和下方)</span><span class="sxs-lookup"><span data-stu-id="a14cc-170">Circle containing two black quadrants (on left and right) and two white quadrants (on top and bottom)</span></span>|<span data-ttu-id="a14cc-171">已停止</span><span class="sxs-lookup"><span data-stu-id="a14cc-171">Stopped</span></span>|<span data-ttu-id="a14cc-172">附加作業未順利完成，因為使用者已停止作業。</span><span class="sxs-lookup"><span data-stu-id="a14cc-172">Attach operation was not completed successfully because the user stopped the operation.</span></span>|  
    |<span data-ttu-id="a14cc-173">包含指向逆時針方向之彎曲箭頭的圓圈</span><span class="sxs-lookup"><span data-stu-id="a14cc-173">Circle containing a curved arrow pointing counter-clockwise</span></span>|<span data-ttu-id="a14cc-174">已回復</span><span class="sxs-lookup"><span data-stu-id="a14cc-174">Rolled Back</span></span>|<span data-ttu-id="a14cc-175">附加作業已順利完成，但是因為在附加其他物件的期間發生了錯誤，所以已將其回復。</span><span class="sxs-lookup"><span data-stu-id="a14cc-175">Attach operation was successful but it has been rolled back due to an error during attachment of another object.</span></span>|  
  
     <span data-ttu-id="a14cc-176">**訊息**</span><span class="sxs-lookup"><span data-stu-id="a14cc-176">**Message**</span></span>  
     <span data-ttu-id="a14cc-177">顯示空白訊息或「找不到檔案」超連結。</span><span class="sxs-lookup"><span data-stu-id="a14cc-177">Displays either a blank message or a "File not found" hyperlink.</span></span>  
  
     <span data-ttu-id="a14cc-178">**加入**</span><span class="sxs-lookup"><span data-stu-id="a14cc-178">**Add**</span></span>  
     <span data-ttu-id="a14cc-179">尋找需要的主要資料庫檔案。</span><span class="sxs-lookup"><span data-stu-id="a14cc-179">Find the necessary main database files.</span></span> <span data-ttu-id="a14cc-180">使用者選取 .mdf 檔案之後，適用的資訊會自動填入 **[要附加的資料庫]** 方格的對應欄位中。</span><span class="sxs-lookup"><span data-stu-id="a14cc-180">When the user selects an .mdf file, applicable information is automatically filled in the respective fields of the **Databases to attach** grid.</span></span>  
  
     <span data-ttu-id="a14cc-181">**移除**</span><span class="sxs-lookup"><span data-stu-id="a14cc-181">**Remove**</span></span>  
     <span data-ttu-id="a14cc-182">從 **[要附加的資料庫]** 方格中移除選取的檔案。</span><span class="sxs-lookup"><span data-stu-id="a14cc-182">Removes the selected file from the **Databases to attach** grid.</span></span>  
  
     <span data-ttu-id="a14cc-183">**"** *<database_name>* **" database details**</span><span class="sxs-lookup"><span data-stu-id="a14cc-183">**"** *<database_name>* **" database details**</span></span>  
     <span data-ttu-id="a14cc-184">顯示要附加之檔案的名稱。</span><span class="sxs-lookup"><span data-stu-id="a14cc-184">Displays the names of the files to be attached.</span></span> <span data-ttu-id="a14cc-185">若要確認或變更檔案的路徑名稱，請按一下 [瀏覽] 按鈕 ( **...** )。</span><span class="sxs-lookup"><span data-stu-id="a14cc-185">To verify or change the pathname of a file, click the **Browse** button (**...**).</span></span>  
  
    > [!NOTE]  
    > <span data-ttu-id="a14cc-186">如果檔案不存在， **[訊息]** 資料行就會顯示「找不到」。</span><span class="sxs-lookup"><span data-stu-id="a14cc-186">If a file does not exist, the **Message** column displays "Not found."</span></span> <span data-ttu-id="a14cc-187">如果找不到記錄檔，它就存在於其他目錄中，或是已遭刪除。</span><span class="sxs-lookup"><span data-stu-id="a14cc-187">If a log file is not found, it exists in another directory or has been deleted.</span></span> <span data-ttu-id="a14cc-188">您必須更新 **[資料庫詳細資料]** 方格中的檔案路徑，以指向正確的位置，或是從方格中移除該記錄檔。</span><span class="sxs-lookup"><span data-stu-id="a14cc-188">You need to either update the file path in the **database details** grid to point to the correct location or remove the log file from the grid.</span></span> <span data-ttu-id="a14cc-189">如果找不到 .ndf 資料檔，您就必須更新該檔案在方格中的路徑，以指向正確的位置。</span><span class="sxs-lookup"><span data-stu-id="a14cc-189">If an .ndf data file is not found, you need to update its path in the grid to point to the correct location.</span></span>  
  
     <span data-ttu-id="a14cc-190">**原始檔案名稱**</span><span class="sxs-lookup"><span data-stu-id="a14cc-190">**Original File Name**</span></span>  
     <span data-ttu-id="a14cc-191">顯示屬於資料庫之附加檔案的名稱。</span><span class="sxs-lookup"><span data-stu-id="a14cc-191">Displays the name of the attached file belonging to the database.</span></span>  
  
     <span data-ttu-id="a14cc-192">**檔案類型**</span><span class="sxs-lookup"><span data-stu-id="a14cc-192">**File Type**</span></span>  
     <span data-ttu-id="a14cc-193">指出檔案的類型，即 **資料** 或 **記錄**。</span><span class="sxs-lookup"><span data-stu-id="a14cc-193">Indicates the type of file, **Data** or **Log**.</span></span>  
  
     <span data-ttu-id="a14cc-194">**目前的檔案路徑**</span><span class="sxs-lookup"><span data-stu-id="a14cc-194">**Current File Path**</span></span>  
     <span data-ttu-id="a14cc-195">顯示選取之資料庫檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="a14cc-195">Displays the path to the selected database file.</span></span> <span data-ttu-id="a14cc-196">路徑可以用手動的方式編輯。</span><span class="sxs-lookup"><span data-stu-id="a14cc-196">The path can be edited manually.</span></span>  
  
     <span data-ttu-id="a14cc-197">**訊息**</span><span class="sxs-lookup"><span data-stu-id="a14cc-197">**Message**</span></span>  
     <span data-ttu-id="a14cc-198">顯示空白訊息或 **「找不到檔案」** 超連結。</span><span class="sxs-lookup"><span data-stu-id="a14cc-198">Displays either a blank message or a "**File not found**" hyperlink.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="a14cc-199">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="a14cc-199">Using Transact-SQL</span></span>  
  
### <a name="to-attach-a-database"></a><span data-ttu-id="a14cc-200">若要附加資料庫</span><span class="sxs-lookup"><span data-stu-id="a14cc-200">To attach a database</span></span>  
  
1.  <span data-ttu-id="a14cc-201">連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="a14cc-201">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="a14cc-202">在標準列中，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="a14cc-202">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="a14cc-203">使用具有關閉的[CREATE DATABASE](/sql/t-sql/statements/create-database-sql-server-transact-sql)語句 `FOR ATTACH` 。</span><span class="sxs-lookup"><span data-stu-id="a14cc-203">Use the [CREATE DATABASE](/sql/t-sql/statements/create-database-sql-server-transact-sql) statement with the `FOR ATTACH` close.</span></span>  
  
     <span data-ttu-id="a14cc-204">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="a14cc-204">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="a14cc-205">這個範例會附加 [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] 資料庫的檔案，並將資料庫重新命名為 `MyAdventureWorks`。</span><span class="sxs-lookup"><span data-stu-id="a14cc-205">This example attaches the files of the [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] database and renames the database to `MyAdventureWorks`.</span></span>  
  
    ```sql  
    CREATE DATABASE MyAdventureWorks   
        ON (FILENAME = 'C:\MySQLServer\AdventureWorks_Data.mdf'),   
        (FILENAME = 'C:\MySQLServer\AdventureWorks_Log.ldf')   
        FOR ATTACH;  
    ```  
  
    > [!NOTE]  
    > <span data-ttu-id="a14cc-206">或者，您可以使用 [sp_attach_db](/sql/relational-databases/system-stored-procedures/sp-attach-db-transact-sql) 或 [sp_attach_single_file_db](/sql/relational-databases/system-stored-procedures/sp-attach-single-file-db-transact-sql) 預存程序。</span><span class="sxs-lookup"><span data-stu-id="a14cc-206">Alternatively, you can use the [sp_attach_db](/sql/relational-databases/system-stored-procedures/sp-attach-db-transact-sql) or [sp_attach_single_file_db](/sql/relational-databases/system-stored-procedures/sp-attach-single-file-db-transact-sql) stored procedure.</span></span> <span data-ttu-id="a14cc-207">但是，Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的未來版本將移除這些程序。</span><span class="sxs-lookup"><span data-stu-id="a14cc-207">However, these procedures will be removed in a future version of Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="a14cc-208">請避免在新的開發工作中使用這項功能，並規劃修改目前使用這項功能的應用程式。</span><span class="sxs-lookup"><span data-stu-id="a14cc-208">Avoid using this feature in new development work, and plan to modify applications that currently use this feature.</span></span> <span data-ttu-id="a14cc-209">我們建議您使用 [建立資料庫 ...]改為 [附加]。</span><span class="sxs-lookup"><span data-stu-id="a14cc-209">We recommend that you use CREATE DATABASE ... FOR ATTACH instead.</span></span>  
  
##  <a name="follow-up-after-upgrading-a-sql-server-database"></a><a name="FollowUp"></a> <span data-ttu-id="a14cc-210">後續操作：升級 SQL Server 資料庫之後</span><span class="sxs-lookup"><span data-stu-id="a14cc-210">Follow Up: After Upgrading a SQL Server Database</span></span>  
 <span data-ttu-id="a14cc-211">後方您使用 attach 方法升級資料庫之後，資料庫就會變成立即可用並自動升級。</span><span class="sxs-lookup"><span data-stu-id="a14cc-211">fter you upgrade a database by using the attach method, the database becomes available immediately and is automatically upgraded.</span></span> <span data-ttu-id="a14cc-212">如果資料庫具有全文檢索索引，升級程序就會根據 [全文檢索目錄升級選項] 伺服器屬性的設定，匯入、重設或重建這些索引。</span><span class="sxs-lookup"><span data-stu-id="a14cc-212">If the database has full-text indexes, the upgrade process either imports, resets, or rebuilds them, depending on the setting of the **Full-Text Upgrade Option** server property.</span></span> <span data-ttu-id="a14cc-213">如果升級選項設定為 [匯入] 或 [重建]，則全文檢索索引在升級期間將無法使用。</span><span class="sxs-lookup"><span data-stu-id="a14cc-213">If the upgrade option is set to **Import** or **Rebuild**, the full-text indexes will be unavailable during the upgrade.</span></span> <span data-ttu-id="a14cc-214">根據進行索引的資料數量而定，匯入可能需要數個小時，而重建可能需要十倍以上的時間。</span><span class="sxs-lookup"><span data-stu-id="a14cc-214">Depending the amount of data being indexed, importing can take several hours, and rebuilding can take up to ten times longer.</span></span> <span data-ttu-id="a14cc-215">此外，請注意，當升級選項設定為 [匯入] 時，如果全文檢索目錄無法使用，系統就會重建相關聯的全文檢索索引。</span><span class="sxs-lookup"><span data-stu-id="a14cc-215">Note also that when the upgrade option is set to **Import**, if a full-text catalog is not available, the associated full-text indexes are rebuilt.</span></span>  
  
<span data-ttu-id="a14cc-216">如果使用者資料庫的相容性層級在升級前為 100 或更高層級，則在升級後仍會保持相同。</span><span class="sxs-lookup"><span data-stu-id="a14cc-216">If the compatibility level of a user database is 100 or higher before upgrade, it remains the same after upgrade.</span></span> <span data-ttu-id="a14cc-217">如果升級前的相容性層級為 90，則在升級後的資料庫中，相容性層級會設定為 100 (這是 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]所支援的最低相容性層級)。</span><span class="sxs-lookup"><span data-stu-id="a14cc-217">If the compatibility level is 90 before upgrade, in the upgraded database, the compatibility level is set to 100, which is the lowest supported compatibility level in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="a14cc-218">如需詳細資訊，請參閱 [ALTER DATABASE 相容性層級 &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-compatibility-level)。</span><span class="sxs-lookup"><span data-stu-id="a14cc-218">For more information, see [ALTER DATABASE Compatibility Level &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-compatibility-level).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a14cc-219">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a14cc-219">See Also</span></span>  
 <span data-ttu-id="a14cc-220">[CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="a14cc-220">[CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql) </span></span>  
 [<span data-ttu-id="a14cc-221">卸離資料庫</span><span class="sxs-lookup"><span data-stu-id="a14cc-221">Detach a Database</span></span>](detach-a-database.md)  
  
  
