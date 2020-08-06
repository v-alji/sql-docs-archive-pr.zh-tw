---
title: 卸離資料庫 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql12.swb.detachdatabase.f1
helpviewer_keywords:
- database detaching [SQL Server]
- detaching databases [SQL Server]
ms.assetid: f63d4107-13e4-4bfe-922d-5e4f712e472d
author: stevestein
ms.author: sstein
ms.openlocfilehash: b8acc809b881012d18f78995bb8e521337fb02ee
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606871"
---
# <a name="detach-a-database"></a><span data-ttu-id="8e838-102">卸離資料庫</span><span class="sxs-lookup"><span data-stu-id="8e838-102">Detach a Database</span></span>
  <span data-ttu-id="8e838-103">此主題描述如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中卸離資料庫。</span><span class="sxs-lookup"><span data-stu-id="8e838-103">This topic describes how to detach a database in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="8e838-104">卸離的檔案會保留下來，您可以使用 CREATE DATABASE 搭配 FOR ATTACH 或 FOR ATTACH_REBUILD_LOG 選項來重新附加它。</span><span class="sxs-lookup"><span data-stu-id="8e838-104">The detached files remain and can be reattached by using CREATE DATABASE with the FOR ATTACH or FOR ATTACH_REBUILD_LOG option.</span></span> <span data-ttu-id="8e838-105">您可以將這些檔案移到另一部伺服器，將它附加在那裡。</span><span class="sxs-lookup"><span data-stu-id="8e838-105">The files can be moved to another server and attached there.</span></span>  
  
 <span data-ttu-id="8e838-106">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="8e838-106">**In This Topic**</span></span>  
  
-   <span data-ttu-id="8e838-107">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="8e838-107">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="8e838-108">限制事項</span><span class="sxs-lookup"><span data-stu-id="8e838-108">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="8e838-109">安全性</span><span class="sxs-lookup"><span data-stu-id="8e838-109">Security</span></span>](#Security)  
  
-   <span data-ttu-id="8e838-110">**若要使用下列項目卸離資料庫：**</span><span class="sxs-lookup"><span data-stu-id="8e838-110">**To detach a database, using:**</span></span>  
  
     [<span data-ttu-id="8e838-111">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="8e838-111">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="8e838-112">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="8e838-112">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="8e838-113">開始之前</span><span class="sxs-lookup"><span data-stu-id="8e838-113">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="8e838-114">限制事項</span><span class="sxs-lookup"><span data-stu-id="8e838-114">Limitations and Restrictions</span></span>  
 <span data-ttu-id="8e838-115">如需限制事項的清單，請參閱 [資料庫卸離與附加 &#40;SQL Server&#41;](database-detach-and-attach-sql-server.md)中卸離資料庫。</span><span class="sxs-lookup"><span data-stu-id="8e838-115">For a list of limitations and restrictions, see [Database Detach and Attach &#40;SQL Server&#41;](database-detach-and-attach-sql-server.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="8e838-116">Security</span><span class="sxs-lookup"><span data-stu-id="8e838-116">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="8e838-117">權限</span><span class="sxs-lookup"><span data-stu-id="8e838-117">Permissions</span></span>  
 <span data-ttu-id="8e838-118">需要 db_owner 固定資料庫角色中的成員資格。</span><span class="sxs-lookup"><span data-stu-id="8e838-118">Requires membership in the db_owner fixed database role.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="8e838-119">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="8e838-119">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-detach-a-database"></a><span data-ttu-id="8e838-120">若要卸離資料庫</span><span class="sxs-lookup"><span data-stu-id="8e838-120">To detach a database</span></span>  
  
1.  <span data-ttu-id="8e838-121">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 物件總管中，連接到 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 執行個體，然後展開執行個體。</span><span class="sxs-lookup"><span data-stu-id="8e838-121">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] Object Explorer, connect to the instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] and then expand the instance.</span></span>  
  
2.  <span data-ttu-id="8e838-122">展開 **[資料庫]** ，並選取您想要卸離的使用者資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="8e838-122">Expand **Databases**, and select the name of the user database you want to detach.</span></span>  
  
3.  <span data-ttu-id="8e838-123">以滑鼠右鍵按一下資料庫名稱，並指向**工作**，然後按一下 [卸離]。</span><span class="sxs-lookup"><span data-stu-id="8e838-123">Right-click the database name, point to **Tasks**, and then click **Detach**.</span></span> <span data-ttu-id="8e838-124">**[卸離資料庫]** 對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="8e838-124">The **Detach Database** dialog box appears.</span></span>  
  
     <span data-ttu-id="8e838-125">**要卸離的資料庫**</span><span class="sxs-lookup"><span data-stu-id="8e838-125">**Databases to detach**</span></span>  
     <span data-ttu-id="8e838-126">列出要卸離的資料庫。</span><span class="sxs-lookup"><span data-stu-id="8e838-126">Lists the databases to detach.</span></span>  
  
     <span data-ttu-id="8e838-127">**Database Name**</span><span class="sxs-lookup"><span data-stu-id="8e838-127">**Database Name**</span></span>  
     <span data-ttu-id="8e838-128">顯示要卸離的資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="8e838-128">Displays the name of the database to be detached.</span></span>  
  
     <span data-ttu-id="8e838-129">**卸除連接**</span><span class="sxs-lookup"><span data-stu-id="8e838-129">**Drop Connections**</span></span>  
     <span data-ttu-id="8e838-130">中斷到指定資料庫的連接。</span><span class="sxs-lookup"><span data-stu-id="8e838-130">Disconnect connections to the specified database.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="8e838-131">您無法卸離具有使用中連接的資料庫。</span><span class="sxs-lookup"><span data-stu-id="8e838-131">You cannot detach a database with active connections.</span></span>  
  
     <span data-ttu-id="8e838-132">**更新統計資料**</span><span class="sxs-lookup"><span data-stu-id="8e838-132">**Update Statistics**</span></span>  
     <span data-ttu-id="8e838-133">依預設，卸離作業會在卸離資料庫時保留任何過時的最佳化統計資料。若要更新現有的最佳化統計資料，請按一下此核取方塊。</span><span class="sxs-lookup"><span data-stu-id="8e838-133">By default, the detach operation retains any out-of-date optimization statistics when detaching the database; to update the existing optimization statistics, click this check box.</span></span>  
  
     <span data-ttu-id="8e838-134">**保留全文檢索目錄**</span><span class="sxs-lookup"><span data-stu-id="8e838-134">**Keep Full-Text Catalogs**</span></span>  
     <span data-ttu-id="8e838-135">依預設，卸離作業會保留與該資料庫關聯的所有全文檢索目錄。</span><span class="sxs-lookup"><span data-stu-id="8e838-135">By default, the detach operation keeps any full-text catalogs that are associated with the database.</span></span> <span data-ttu-id="8e838-136">若要移除這些全文檢索目錄，請清除 **[保留全文檢索目錄]** 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="8e838-136">To remove them, clear the **Keep Full-Text Catalogs** check box.</span></span> <span data-ttu-id="8e838-137">只有當您從 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]升級資料庫時，才會出現這個選項。</span><span class="sxs-lookup"><span data-stu-id="8e838-137">This option appears only when you are upgrading a database from [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].</span></span>  
  
     <span data-ttu-id="8e838-138">**狀態**</span><span class="sxs-lookup"><span data-stu-id="8e838-138">**Status**</span></span>  
     <span data-ttu-id="8e838-139">顯示下列其中一個狀態：[就緒] 或 [未就緒]。</span><span class="sxs-lookup"><span data-stu-id="8e838-139">Displays one of the following states: **Ready** or **Not ready**.</span></span>  
  
     <span data-ttu-id="8e838-140">**訊息**</span><span class="sxs-lookup"><span data-stu-id="8e838-140">**Message**</span></span>  
     <span data-ttu-id="8e838-141">**[訊息]** 資料行可以顯示有關資料庫的資訊，如下所示：</span><span class="sxs-lookup"><span data-stu-id="8e838-141">The **Message** column may display information about the database, as follows:</span></span>  
  
    -   <span data-ttu-id="8e838-142">當資料庫涉及複寫時， **[狀態]** 為 **[尚未備妥]** 且 **[訊息]** 資料行會顯示 **[資料庫已複寫]** 。</span><span class="sxs-lookup"><span data-stu-id="8e838-142">When a database is involved with replication, the **Status** is **Not ready** and the **Message** column displays **Database replicated**.</span></span>  
  
    -   <span data-ttu-id="8e838-143">當資料庫有一或多個使用中的連線時，[狀態] 為 [未就緒] 且 [訊息] 資料行顯示 [<使用中連線數目> 個使用中的連線]，例如：[1 個使用中的連線]。</span><span class="sxs-lookup"><span data-stu-id="8e838-143">When a database has one or more active connections, the **Status** is **Not ready** and the **Message** column displays _<number_of_active_connections>_**Active connection(s)** - for example: **1 Active connection(s)**.</span></span> <span data-ttu-id="8e838-144">您必須選取 **[卸除連接]** 中斷任何使用中的連接之後，才能卸離資料庫。</span><span class="sxs-lookup"><span data-stu-id="8e838-144">Before you can detach the database, you need to disconnect any active connections by selecting **Drop Connections**.</span></span>  
  
     <span data-ttu-id="8e838-145">若要取得有關訊息的詳細資訊，請按一下超連結文字，以開啟活動監視器。</span><span class="sxs-lookup"><span data-stu-id="8e838-145">To obtain more information about a message, click the hyperlinked text to open Activity Monitor.</span></span>  
  
4.  <span data-ttu-id="8e838-146">當您準備卸離資料庫時，請按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="8e838-146">When you are ready to detach the database, click **OK**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8e838-147">重新整理檢視之前，仍可在 [物件總管] 的 **[資料庫]** 節點中看見最新卸離的資料庫。</span><span class="sxs-lookup"><span data-stu-id="8e838-147">The newly detached database will remain visible in the **Databases** node of Object Explorer until the view is refreshed.</span></span> <span data-ttu-id="8e838-148">您可以隨時重新整理檢視：按一下 [物件總管] 窗格，並從功能表列選取 [檢視]，然後選取 [重新整理]。</span><span class="sxs-lookup"><span data-stu-id="8e838-148">You can refresh the view at any time: Click in the Object Explorer pane, and from the menu bar select **View** and then **Refresh**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="8e838-149">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="8e838-149">Using Transact-SQL</span></span>  
  
#### <a name="to-detach-a-database"></a><span data-ttu-id="8e838-150">若要卸離資料庫</span><span class="sxs-lookup"><span data-stu-id="8e838-150">To detach a database</span></span>  
  
1.  <span data-ttu-id="8e838-151">連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="8e838-151">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="8e838-152">在標準列中，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="8e838-152">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="8e838-153">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="8e838-153">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="8e838-154">這個範例會以 skipchecks 設為 true 來卸離 AdventureWorks2012 資料庫。</span><span class="sxs-lookup"><span data-stu-id="8e838-154">This example detaches the AdventureWorks2012 database with skipchecks set to true.</span></span>  
  
```  
EXEC sp_detach_db 'AdventureWorks2012', 'true';  
```  
  
## <a name="see-also"></a><span data-ttu-id="8e838-155">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8e838-155">See Also</span></span>  
 <span data-ttu-id="8e838-156">[資料庫卸離和附加 &#40;SQL Server&#41;](database-detach-and-attach-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="8e838-156">[Database Detach and Attach &#40;SQL Server&#41;](database-detach-and-attach-sql-server.md) </span></span>  
 [<span data-ttu-id="8e838-157">sp_detach_db &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="8e838-157">sp_detach_db &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-detach-db-transact-sql)  
  
  
