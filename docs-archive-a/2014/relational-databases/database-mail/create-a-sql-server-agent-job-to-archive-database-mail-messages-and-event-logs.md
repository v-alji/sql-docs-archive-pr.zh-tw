---
title: 建立 SQL Server Agent 作業以封存 Database Mail 訊息及事件記錄檔 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- archiving mail messages and attachments [SQL Server]
- removing mail messages and attachements
- Database Mail [SQL Server], archiving
- saving mail messages and attachments
ms.assetid: 8f8f0fba-f750-4533-9b76-a9cdbcdc3b14
author: stevestein
ms.author: sstein
ms.openlocfilehash: b958b280c358a8aeb752600dee1c2aee31d14db1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594101"
---
# <a name="create-a-sql-server-agent-job-to-archive-database-mail-messages-and-event-logs"></a><span data-ttu-id="43574-102">建立 SQL Server Agent 作業以封存 Database Mail 訊息及事件記錄檔</span><span class="sxs-lookup"><span data-stu-id="43574-102">Create a SQL Server Agent Job to Archive Database Mail Messages and Event Logs</span></span>
  <span data-ttu-id="43574-103">Database Mail 訊息的副本及其附件會隨著 Database Mail 事件記錄檔一起保留在 **msdb** 資料表。</span><span class="sxs-lookup"><span data-stu-id="43574-103">Copies of Database Mail messages and their attachments are retained in **msdb** tables along with the Database Mail event log.</span></span> <span data-ttu-id="43574-104">您可能需要定期減少資料表的大小，並封存不再需要的訊息和事件。</span><span class="sxs-lookup"><span data-stu-id="43574-104">Periodically you might want to reduce the size of the tables and archive messages and events that are no longer needed.</span></span> <span data-ttu-id="43574-105">下列程序可建立 SQL Server Agent 作業以便自動執行程序。</span><span class="sxs-lookup"><span data-stu-id="43574-105">The following procedures create a SQL Server Agent job to automate the process.</span></span>  
  
-   <span data-ttu-id="43574-106">**開始之前**  ： [必要條件](#Prerequisites)、 [建議](#Recommendations)、 [權限](#Permissions)</span><span class="sxs-lookup"><span data-stu-id="43574-106">**Before you begin:**  , [Prerequisites](#Prerequisites), [Recommendations](#Recommendations), [Permissions](#Permissions)</span></span>  
  
-   <span data-ttu-id="43574-107">**使用以下方式封存 Database Mail 訊息和記錄：** [SQL Server Agent](#Process_Overview)</span><span class="sxs-lookup"><span data-stu-id="43574-107">**To Archive Database Mail messages and logs using :**  [SQL Server Agent](#Process_Overview)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="43574-108">開始之前</span><span class="sxs-lookup"><span data-stu-id="43574-108">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="43574-109">必要條件</span><span class="sxs-lookup"><span data-stu-id="43574-109">Prerequisites</span></span>  
 <span data-ttu-id="43574-110">要儲存封存資料的新資料表可能位在特殊的封存資料庫中。</span><span class="sxs-lookup"><span data-stu-id="43574-110">The new tables to store the archive data might be located in a special archive database.</span></span> <span data-ttu-id="43574-111">資料列也可以匯出至文字檔。</span><span class="sxs-lookup"><span data-stu-id="43574-111">Alternatively the rows could be exported to a text file.</span></span>  
 
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="43574-112">建議</span><span class="sxs-lookup"><span data-stu-id="43574-112">Recommendations</span></span>  
 <span data-ttu-id="43574-113">在實際執行環境中，您可能會想要加入其他錯誤檢查，並在作業失敗時傳送電子郵件訊息給操作員。</span><span class="sxs-lookup"><span data-stu-id="43574-113">In your production environment, you might want to add additional error checking and send an e-mail message to operators if the job fails.</span></span>  
  
  
###  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="43574-114">權限</span><span class="sxs-lookup"><span data-stu-id="43574-114">Permissions</span></span>  
 <span data-ttu-id="43574-115">您必須是 **系統管理員 (sysadmin)** 固定伺服器角色的成員，才能執行此主題中所描述的預存程序。</span><span class="sxs-lookup"><span data-stu-id="43574-115">You must be a member of the **sysadmin** fixed server role to execute the stored procedures described in this topic.</span></span>  
  
  
###  <a name="overview-of-the-process"></a><a name="Process_Overview"></a> <span data-ttu-id="43574-116">處理序的概觀</span><span class="sxs-lookup"><span data-stu-id="43574-116">Overview of the Process</span></span>  
  
-   <span data-ttu-id="43574-117">第一個程序會建立一個名稱為「封存 Database Mail」的作業，此作業包含下列步驟。</span><span class="sxs-lookup"><span data-stu-id="43574-117">The first procedure creates a job named Archive Database Mail with the following steps.</span></span>  
  
    1.  <span data-ttu-id="43574-118">將 Database Mail 資料表的所有訊息複製到新資料表，該新資料表是以上個月來命名，格式為 **DBMailArchive_** <年_月>。</span><span class="sxs-lookup"><span data-stu-id="43574-118">Copy all messages from the Database Mail tables to a new table named after the previous month in the format **DBMailArchive_**_<year_month>_.</span></span>  
  
    2.  <span data-ttu-id="43574-119">將第一個步驟複製之訊息的相關附件，從 Database Mail 資料表複製到新資料表，該新資料表是以上個月來命名，格式為 **DBMailArchive_Attachments_** <年_月>。</span><span class="sxs-lookup"><span data-stu-id="43574-119">Copy the attachments related to the messages copied in the first step, from the Database Mail tables to a new table named after the previous month in the format **DBMailArchive_Attachments_**_<year_month>_.</span></span>  
  
    3.  <span data-ttu-id="43574-120">將 Database Mail 事件記錄檔中第一個步驟複製之訊息的相關事件，從 Database Mail 資料表複製到新資料表，該新資料表是以上個月來命名，格式為 **DBMailArchive_Log_** <年_月>。</span><span class="sxs-lookup"><span data-stu-id="43574-120">Copy the events from the Database Mail event log that are related to the messages copied in the first step, from the Database Mail tables to a new table named after the previous month in the format **DBMailArchive_Log_**_<year_month>_.</span></span>  
  
    4.  <span data-ttu-id="43574-121">刪除 Database Mail 資料表中已轉移郵件項目的記錄。</span><span class="sxs-lookup"><span data-stu-id="43574-121">Delete the records of the transferred mail items from the Database Mail tables.</span></span>  
  
    5.  <span data-ttu-id="43574-122">刪除 Database Mail 事件記錄檔中已轉移郵件項目的相關事件。</span><span class="sxs-lookup"><span data-stu-id="43574-122">Delete the events related to the transferred mail items from the Database Mail event log.</span></span>  
  
-   <span data-ttu-id="43574-123">排程定期執行作業。</span><span class="sxs-lookup"><span data-stu-id="43574-123">Schedule the job to run periodically.</span></span>  
 
  
## <a name="to-create-a-sql-server-agent-job"></a><span data-ttu-id="43574-124">若要建立 SQL Server Agent 作業</span><span class="sxs-lookup"><span data-stu-id="43574-124">To create a SQL Server Agent job</span></span>  
  
1.  <span data-ttu-id="43574-125">在 [物件總管] 中，展開 [ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent]，以滑鼠右鍵按一下 **[作業]** ，然後按一下 **[新增作業]** 。</span><span class="sxs-lookup"><span data-stu-id="43574-125">In Object Explorer, expand [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent, right-click **Jobs**, and then click **New Job**.</span></span>  
  
2.  <span data-ttu-id="43574-126">在 **[新增作業]** 對話方塊的 **[名稱]** 方塊中，輸入 **封存 Database Mail**。</span><span class="sxs-lookup"><span data-stu-id="43574-126">In the **New Job** dialog box, in the **Name** box, type **Archive Database Mail**.</span></span>  
  
3.  <span data-ttu-id="43574-127">在 **[擁有者]** 方塊中，確認該位擁有者是 **系統管理員 (sysadmin)** 固定伺服器角色的成員。</span><span class="sxs-lookup"><span data-stu-id="43574-127">In the **Owner** box, confirm that the owner is a member of the **sysadmin** fixed server role.</span></span>  
  
4.  <span data-ttu-id="43574-128">在 **[類別目錄]** 方塊中，按一下 **[資料庫維護]** 。</span><span class="sxs-lookup"><span data-stu-id="43574-128">In the **Category** box, click the **Database Maintenance**.</span></span>  
  
5.  <span data-ttu-id="43574-129">在 **[描述]** 方塊中，輸入 **[封存 Database Mail 訊息]** ，然後按一下 **[步驟]** 。</span><span class="sxs-lookup"><span data-stu-id="43574-129">In the **Description** box, type **Archive Database Mail messages**, and then click **Steps**.</span></span>  
  
  
  
## <a name="to-create-a-step-to-archive-the-database-mail-messages"></a><span data-ttu-id="43574-130">建立封存 Database Mail 訊息的步驟</span><span class="sxs-lookup"><span data-stu-id="43574-130">To create a step to archive the Database Mail messages</span></span>  
  
1.  <span data-ttu-id="43574-131">在 **[步驟]** 頁面上，按一下 **[新增]** 。</span><span class="sxs-lookup"><span data-stu-id="43574-131">On the **Steps** page, click **New**.</span></span>  
  
2.  <span data-ttu-id="43574-132">在 **[步驟名稱]** 方塊中，輸入 **複製 Database Mail 項目**。</span><span class="sxs-lookup"><span data-stu-id="43574-132">In the **Step name** box, type **Copy Database Mail Items**.</span></span>  
  
3.  <span data-ttu-id="43574-133">在 **[類型]** 方塊中，選取 **[Transact-SQL 指令碼 (T-SQL)]** 。</span><span class="sxs-lookup"><span data-stu-id="43574-133">In the **Type** box, select **Transact-SQL script (T-SQL)**.</span></span>  
  
4.  <span data-ttu-id="43574-134">在 **[資料庫]** 方塊中，選取 **[msdb]** 。</span><span class="sxs-lookup"><span data-stu-id="43574-134">In the **Database** box, select **msdb**.</span></span>  
  
5.  <span data-ttu-id="43574-135">在 **[命令]** 方塊中，輸入下列陳述式建立一個資料表，以上一個月份命名，包含這個月之前的所有資料列：</span><span class="sxs-lookup"><span data-stu-id="43574-135">In the **Command** box, type the following statement to create a table named after the previous month, containing rows older than the start of the current month:</span></span>  
  
    ```  
    DECLARE @LastMonth nvarchar(12);  
    DECLARE @CopyDate nvarchar(20) ;  
    DECLARE @CreateTable nvarchar(250) ;  
    SET @LastMonth = (SELECT CAST(DATEPART(yyyy,GETDATE()) AS CHAR(4)) + '_' + CAST(DATEPART(mm,GETDATE())-1 AS varchar(2))) ;  
    SET @CopyDate = (SELECT CAST(CONVERT(char(8), CURRENT_TIMESTAMP- DATEPART(dd,GETDATE()-1), 112) AS datetime))  
    SET @CreateTable = 'SELECT * INTO msdb.dbo.[DBMailArchive_' + @LastMonth + '] FROM sysmail_allitems WHERE send_request_date < ''' + @CopyDate +'''';  
    EXEC sp_executesql @CreateTable ;  
    ```  
  
6.  <span data-ttu-id="43574-136">按一下 **[確定]** 以儲存步驟。</span><span class="sxs-lookup"><span data-stu-id="43574-136">Click **OK** to save the step.</span></span>  
  
  
  
## <a name="to-create-a-step-to-archive-the-database-mail-attachments"></a><span data-ttu-id="43574-137">建立封存 Database Mail 附加檔案的步驟</span><span class="sxs-lookup"><span data-stu-id="43574-137">To create a step to archive the Database Mail attachments</span></span>  
  
1.  <span data-ttu-id="43574-138">在 **[步驟]** 頁面上，按一下 **[新增]** 。</span><span class="sxs-lookup"><span data-stu-id="43574-138">On the **Steps** page, click **New**.</span></span>  
  
2.  <span data-ttu-id="43574-139">在 **[步驟名稱]** 方塊中，輸入 **複製 Database Mail 附加檔案**。</span><span class="sxs-lookup"><span data-stu-id="43574-139">In the **Step name** box, type **Copy Database Mail Attachments**.</span></span>  
  
3.  <span data-ttu-id="43574-140">在 **[類型]** 方塊中，選取 **[Transact-SQL 指令碼 (T-SQL)]** 。</span><span class="sxs-lookup"><span data-stu-id="43574-140">In the **Type** box, select **Transact-SQL script (T-SQL)**.</span></span>  
  
4.  <span data-ttu-id="43574-141">在 **[資料庫]** 方塊中，選取 **[msdb]** 。</span><span class="sxs-lookup"><span data-stu-id="43574-141">In the **Database** box, select **msdb**.</span></span>  
  
5.  <span data-ttu-id="43574-142">在 **[命令]** 方塊中，輸入下列陳述式建立一個附加檔案資料表，以上一個月份命名，包含前一步驟轉移訊息所對應的附件：</span><span class="sxs-lookup"><span data-stu-id="43574-142">In the **Command** box, type the following statement to create an attachments table named after the previous month, containing the attachments that correspond to the messages transferred in the previous step:</span></span>  
  
    ```  
    DECLARE @LastMonth nvarchar(12);  
    DECLARE @CopyDate nvarchar(20) ;  
    DECLARE @CreateTable nvarchar(250) ;  
    SET @LastMonth = (SELECT CAST(DATEPART(yyyy,GETDATE()) AS CHAR(4)) + '_' + CAST(DATEPART(mm,GETDATE())-1 AS varchar(2))) ;  
    SET @CopyDate = (SELECT CAST(CONVERT(char(8), CURRENT_TIMESTAMP- DATEPART(dd,GETDATE()-1), 112) AS datetime))  
    SET @CreateTable = 'SELECT * INTO msdb.dbo.[DBMailArchive_Attachments_' + @LastMonth + '] FROM sysmail_attachments   
     WHERE mailitem_id in (SELECT DISTINCT mailitem_id FROM [DBMailArchive_' + @LastMonth + '] )';  
    EXEC sp_executesql @CreateTable ;  
    ```  
  
6.  <span data-ttu-id="43574-143">按一下 **[確定]** 以儲存步驟。</span><span class="sxs-lookup"><span data-stu-id="43574-143">Click **OK** to save the step.</span></span>  
  
  
  
## <a name="to-create-a-step-to-archive-the-database-mail-log"></a><span data-ttu-id="43574-144">建立封存 Database Mail 記錄的步驟</span><span class="sxs-lookup"><span data-stu-id="43574-144">To create a step to archive the Database Mail log</span></span>  
  
1.  <span data-ttu-id="43574-145">在 **[步驟]** 頁面上，按一下 **[新增]** 。</span><span class="sxs-lookup"><span data-stu-id="43574-145">On the **Steps** page, click **New**.</span></span>  
  
2.  <span data-ttu-id="43574-146">在 **[步驟名稱]** 方塊中，輸入 **複製 Database Mail 記錄**。</span><span class="sxs-lookup"><span data-stu-id="43574-146">In the **Step name** box, type **Copy Database Mail Log**.</span></span>  
  
3.  <span data-ttu-id="43574-147">在 **[類型]** 方塊中，選取 **[Transact-SQL 指令碼 (T-SQL)]** 。</span><span class="sxs-lookup"><span data-stu-id="43574-147">In the **Type** box, select **Transact-SQL script (T-SQL)**.</span></span>  
  
4.  <span data-ttu-id="43574-148">在 **[資料庫]** 方塊中，選取 **[msdb]** 。</span><span class="sxs-lookup"><span data-stu-id="43574-148">In the **Database** box, select **msdb**.</span></span>  
  
5.  <span data-ttu-id="43574-149">在 **[命令]** 方塊中，輸入下列陳述式建立一個記錄資料表，以上一個月份命名，包含前面步驟轉移訊息所對應的記錄項目：</span><span class="sxs-lookup"><span data-stu-id="43574-149">In the **Command** box, type the following statement to create a log table named after the previous month, containing the log entries that correspond to the messages transferred in the earlier step:</span></span>  
  
    ```  
    DECLARE @LastMonth nvarchar(12);  
    DECLARE @CopyDate nvarchar(20) ;  
    DECLARE @CreateTable nvarchar(250) ;  
    SET @LastMonth = (SELECT CAST(DATEPART(yyyy,GETDATE()) AS CHAR(4)) + '_' + CAST(DATEPART(mm,GETDATE())-1 AS varchar(2))) ;  
    SET @CopyDate = (SELECT CAST(CONVERT(char(8), CURRENT_TIMESTAMP- DATEPART(dd,GETDATE()-1), 112) AS datetime))  
    SET @CreateTable = 'SELECT * INTO msdb.dbo.[DBMailArchive_Log_' + @LastMonth + '] FROM sysmail_Event_Log   
     WHERE mailitem_id in (SELECT DISTINCT mailitem_id FROM [DBMailArchive_' + @LastMonth + '] )';  
    EXEC sp_executesql @CreateTable ;  
    ```  
  
6.  <span data-ttu-id="43574-150">按一下 **[確定]** 以儲存步驟。</span><span class="sxs-lookup"><span data-stu-id="43574-150">Click **OK** to save the step.</span></span>  
  
  
  
## <a name="to-create-a-step-to-remove-the-archived-rows-from-database-mail"></a><span data-ttu-id="43574-151">建立從 Database Mail 移除封存資料列的步驟</span><span class="sxs-lookup"><span data-stu-id="43574-151">To create a step to remove the archived rows from Database Mail</span></span>  
  
1.  <span data-ttu-id="43574-152">在 **[步驟]** 頁面上，按一下 **[新增]** 。</span><span class="sxs-lookup"><span data-stu-id="43574-152">On the **Steps** page, click **New**.</span></span>  
  
2.  <span data-ttu-id="43574-153">在 **[步驟名稱]** 方塊中，輸入 **從 Database Mail 移除資料列**。</span><span class="sxs-lookup"><span data-stu-id="43574-153">In the **Step name** box, type **Remove rows from Database Mail**.</span></span>  
  
3.  <span data-ttu-id="43574-154">在 **[類型]** 方塊中，選取 **[Transact-SQL 指令碼 (T-SQL)]** 。</span><span class="sxs-lookup"><span data-stu-id="43574-154">In the **Type** box, select **Transact-SQL script (T-SQL)**.</span></span>  
  
4.  <span data-ttu-id="43574-155">在 **[資料庫]** 方塊中，選取 **[msdb]** 。</span><span class="sxs-lookup"><span data-stu-id="43574-155">In the **Database** box, select **msdb**.</span></span>  
  
5.  <span data-ttu-id="43574-156">在 **[命令]** 方塊中，輸入下列陳述式，從 Database Mail 資料表移除這個月之前的資料列：</span><span class="sxs-lookup"><span data-stu-id="43574-156">In the **Command** box, type the following statement to remove rows older than the current month from the Database Mail tables:</span></span>  
  
    ```  
    DECLARE @CopyDate nvarchar(20) ;  
    SET @CopyDate = (SELECT CAST(CONVERT(char(8), CURRENT_TIMESTAMP- DATEPART(dd,GETDATE()-1), 112) AS datetime)) ;  
    EXECUTE msdb.dbo.sysmail_delete_mailitems_sp @sent_before = @CopyDate ;  
    ```  
  
6.  <span data-ttu-id="43574-157">按一下 **[確定]** 以儲存步驟。</span><span class="sxs-lookup"><span data-stu-id="43574-157">Click **OK** to save the step.</span></span>  
  
  
  
## <a name="to-create-a-step-to-remove-the-archived-items-from-database-mail-event-log"></a><span data-ttu-id="43574-158">建立從 Database Mail 事件記錄檔移除封存項目的步驟</span><span class="sxs-lookup"><span data-stu-id="43574-158">To create a step to remove the archived items from Database Mail event log</span></span>  
  
1.  <span data-ttu-id="43574-159">在 **[步驟]** 頁面上，按一下 **[新增]** 。</span><span class="sxs-lookup"><span data-stu-id="43574-159">On the **Steps** page, click **New**.</span></span>  
  
2.  <span data-ttu-id="43574-160">在 **[步驟名稱]** 方塊中，輸入 **從 Database Mail 事件記錄檔移除資料列**。</span><span class="sxs-lookup"><span data-stu-id="43574-160">In the **Step Name** box type **Remove rows from Database Mail event log**.</span></span>  
  
3.  <span data-ttu-id="43574-161">在 **[類型]** 方塊中，選取 **[Transact-SQL 指令碼 (T-SQL)]** 。</span><span class="sxs-lookup"><span data-stu-id="43574-161">In the **Type** box, select **Transact-SQL script (T-SQL)**.</span></span>  
  
4.  <span data-ttu-id="43574-162">在 **[命令]** 方塊中，輸入下列陳述式，從 Database Mail 事件記錄檔移除這個月之前的資料列：</span><span class="sxs-lookup"><span data-stu-id="43574-162">In the **Command** box, type the following statement to remove rows older than the current month from the Database Mail event log:</span></span>  
  
    ```  
    DECLARE @CopyDate nvarchar(20) ;  
    SET @CopyDate = (SELECT CAST(CONVERT(char(8), CURRENT_TIMESTAMP- DATEPART(dd,GETDATE()-1), 112) AS datetime)) ;  
    EXECUTE msdb.dbo.sysmail_delete_log_sp @logged_before = @CopyDate ;  
    ```  
  
5.  <span data-ttu-id="43574-163">按一下 **[確定]** 以儲存步驟。</span><span class="sxs-lookup"><span data-stu-id="43574-163">Click **OK** to save the step.</span></span>  
  
  
  
## <a name="to-schedule-the-job-to-run-periodically"></a><span data-ttu-id="43574-164">排程定期執行作業</span><span class="sxs-lookup"><span data-stu-id="43574-164">To schedule the job to run periodically</span></span>  
  
1.  <span data-ttu-id="43574-165">在 **[新增作業]** 對話方塊中，按一下 **[排程]** 。</span><span class="sxs-lookup"><span data-stu-id="43574-165">In the **New Job** dialog box, click **Schedules**.</span></span>  
  
2.  <span data-ttu-id="43574-166">在 **[排程]** 頁面上，按一下 **[新增]** 。</span><span class="sxs-lookup"><span data-stu-id="43574-166">On the **Schedules** page, click **New**.</span></span>  
  
3.  <span data-ttu-id="43574-167">在 **[名稱]** 方塊中，輸入 **封存 Database Mail**。</span><span class="sxs-lookup"><span data-stu-id="43574-167">In the **Name** box, type **Archive Database Mail**.</span></span>  
  
4.  <span data-ttu-id="43574-168">在 **[排程類型]** 方塊中，選取 **[重複執行]** 。</span><span class="sxs-lookup"><span data-stu-id="43574-168">In the **Schedule type** box, select **Recurring**.</span></span>  
  
5.  <span data-ttu-id="43574-169">在 **[頻率]** 區域中，選取定期執行作業的選項 (例如一個月一次)。</span><span class="sxs-lookup"><span data-stu-id="43574-169">In the **Frequency** area, select the options to run the job periodically, for example once every month.</span></span>  
  
6.  <span data-ttu-id="43574-170">在 [每日頻率] 區域中，選取 [執行一次於 \<time>]。</span><span class="sxs-lookup"><span data-stu-id="43574-170">In the **Daily frequency** area, select **Occurs once at \<time>**.</span></span>  
  
7.  <span data-ttu-id="43574-171">視需要設定其他選項，然後按一下 **[確定]** 儲存排程。</span><span class="sxs-lookup"><span data-stu-id="43574-171">Verify that the other options are configured as you wish, and then click **OK** to save the schedule.</span></span>  
  
8.  <span data-ttu-id="43574-172">按一下 **[確定]** 以儲存作業。</span><span class="sxs-lookup"><span data-stu-id="43574-172">Click **OK** to save the job.</span></span>  
  
  
  
  
