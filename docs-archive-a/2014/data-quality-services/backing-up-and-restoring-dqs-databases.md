---
title: 備份與還原 DQS 資料庫 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: f3091f62-2234-4a80-a615-cf14c2a1da85
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 489664d8c64a99d1ea4dcec79b93e5b01b28f649
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592273"
---
# <a name="backing-up-and-restoring-dqs-databases"></a><span data-ttu-id="40760-102">備份及還原 DQS 資料庫</span><span class="sxs-lookup"><span data-stu-id="40760-102">Backing Up and Restoring DQS Databases</span></span>
  <span data-ttu-id="40760-103">此主題描述如何備份及還原 DQS 資料庫。</span><span class="sxs-lookup"><span data-stu-id="40760-103">This topic describes how to back up and restore the DQS databases.</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="40760-104">開始之前</span><span class="sxs-lookup"><span data-stu-id="40760-104">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="40760-105">必要條件</span><span class="sxs-lookup"><span data-stu-id="40760-105">Prerequisites</span></span>  
  
-   <span data-ttu-id="40760-106">您必須知道或記得您在 DQS 伺服器安裝期間所提供資料庫主要金鑰的密碼。</span><span class="sxs-lookup"><span data-stu-id="40760-106">You must know or remember the password for the database master key that you provided during the DQS server installation.</span></span>  
  
-   <span data-ttu-id="40760-107">請確定 DQS 中沒有任何執行中的活動或處理序。</span><span class="sxs-lookup"><span data-stu-id="40760-107">Ensure that there are no running activities or processes in DQS.</span></span> <span data-ttu-id="40760-108">這可以使用 **[活動監控]** 畫面加以確認。</span><span class="sxs-lookup"><span data-stu-id="40760-108">This can be verified using the **Activity Monitoring** screen.</span></span> <span data-ttu-id="40760-109">如需有關在此畫面工作的詳細資訊，請參閱＜ [Monitor DQS Activities](../../2014/data-quality-services/monitor-dqs-activities.md)＞。</span><span class="sxs-lookup"><span data-stu-id="40760-109">For detailed information about working in this screen, see [Monitor DQS Activities](../../2014/data-quality-services/monitor-dqs-activities.md).</span></span>  
  
-   <span data-ttu-id="40760-110">確定沒有任何使用者登入 DQS 伺服器。</span><span class="sxs-lookup"><span data-stu-id="40760-110">Ensure that there are no users logged on the DQS server.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="40760-111">Security</span><span class="sxs-lookup"><span data-stu-id="40760-111">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="40760-112">權限</span><span class="sxs-lookup"><span data-stu-id="40760-112">Permissions</span></span>  
  
-   <span data-ttu-id="40760-113">您的 Windows 使用者帳戶必須是 SQL Server 執行個體上系統管理員 (sysadmin) 固定伺服器角色的成員，才能執行備份和還原作業。</span><span class="sxs-lookup"><span data-stu-id="40760-113">Your Windows user account must be a member of the sysadmin fixed server role in the SQL Server instance to perform the backup and restore operations.</span></span>  
  
-   <span data-ttu-id="40760-114">您必須擁有 DQS_MAIN 資料庫的 dqs_administrator 角色，才能在 DQS 中終止任何執行中的活動或停止任何執行中的處理序。</span><span class="sxs-lookup"><span data-stu-id="40760-114">You must have the dqs_administrator role on the DQS_MAIN database to terminate any running activities or stop any running processes in DQS.</span></span>  
  
##  <a name="backup-and-restore-dqs-databases"></a><a name="BackupRestore"></a><span data-ttu-id="40760-115">備份和還原 DQS 資料庫</span><span class="sxs-lookup"><span data-stu-id="40760-115">Backup and Restore DQS Databases</span></span>  
  
1.  <span data-ttu-id="40760-116">啟動 Microsoft SQL Server Management Studio，並連接到適當的 SQL Server 執行個體。</span><span class="sxs-lookup"><span data-stu-id="40760-116">Start Microsoft SQL Server Management Studio, and connect to the appropriate SQL Server instance.</span></span>  
  
2.  <span data-ttu-id="40760-117">在 [物件總管] 中，展開 **[資料庫]** 節點。</span><span class="sxs-lookup"><span data-stu-id="40760-117">In Object Explorer, expand the **Databases** node.</span></span>  
  
3.  <span data-ttu-id="40760-118">備份 DQS_STAGING_DATA 資料庫。</span><span class="sxs-lookup"><span data-stu-id="40760-118">Back up the DQS_STAGING_DATA database.</span></span> <span data-ttu-id="40760-119">如需備份 SQL Server 資料庫的逐步指示，請參閱[建立完整資料庫備份 &#40;SQL Server&#41;](../relational-databases/backup-restore/create-a-full-database-backup-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="40760-119">For step-by-step instructions for backing a SQL Server database, see [Create a Full Database Backup &#40;SQL Server&#41;](../relational-databases/backup-restore/create-a-full-database-backup-sql-server.md).</span></span>  
  
4.  <span data-ttu-id="40760-120">備份 DQS_PROJECTS 資料庫。</span><span class="sxs-lookup"><span data-stu-id="40760-120">Back up the DQS_PROJECTS database.</span></span>  
  
5.  <span data-ttu-id="40760-121">備份 DQS_MAIN 資料庫。</span><span class="sxs-lookup"><span data-stu-id="40760-121">Back up the DQS_MAIN database.</span></span>  
  
6.  <span data-ttu-id="40760-122">中斷連接目前的 SQL Server 執行個體，並連接到您想要還原這些資料庫的 SQL Server 執行個體。</span><span class="sxs-lookup"><span data-stu-id="40760-122">Disconnect from the current instance of SQL Server, and connect to the SQL Server instance where you want to restore these databases.</span></span>  
  
7.  <span data-ttu-id="40760-123">還原 DQS_MAIN 資料庫。</span><span class="sxs-lookup"><span data-stu-id="40760-123">Restore DQS_MAIN database.</span></span> <span data-ttu-id="40760-124">如需還原 SQL Server 資料庫的逐步指示，請參閱將[資料庫備份還原 &#40;SQL Server Management Studio&#41;](../relational-databases/backup-restore/restore-a-database-backup-using-ssms.md)。</span><span class="sxs-lookup"><span data-stu-id="40760-124">For step-by-step instructions to restore a SQL Server database, see [Restore a Database Backup &#40;SQL Server Management Studio&#41;](../relational-databases/backup-restore/restore-a-database-backup-using-ssms.md).</span></span>  
  
8.  <span data-ttu-id="40760-125">還原 DQS_PROJECTS 資料庫。</span><span class="sxs-lookup"><span data-stu-id="40760-125">Restore the DQS_PROJECTS database.</span></span>  
  
9. <span data-ttu-id="40760-126">還原 DQS_STAGING_DATA 資料庫。</span><span class="sxs-lookup"><span data-stu-id="40760-126">Restore the DQS_STAGING_DATA database.</span></span>  
  
10. <span data-ttu-id="40760-127">在 [物件總管] 中，以滑鼠右鍵按一下伺服器，然後按一下 **[新增查詢]**。</span><span class="sxs-lookup"><span data-stu-id="40760-127">In Object Explorer, right-click the server, and then click **New Query**.</span></span>  
  
11. <span data-ttu-id="40760-128">在 [查詢編輯器] 視窗中，複製下列 SQL 語句，並將取代為 *\<PASSWORD>* 您在 DQS 安裝期間為資料庫主要金鑰提供的密碼：</span><span class="sxs-lookup"><span data-stu-id="40760-128">In the Query Editor window, copy the following SQL statements, and replace *\<PASSWORD>* with the password that you provided during the DQS installation for the database master key:</span></span>  
  
    ```sql  
    USE [DQS_MAIN]  
    GO  
    EXECUTE [internal_core].[RestoreDQDatabases] '<PASSWORD>'  
    GO  
    ```  
  
12. <span data-ttu-id="40760-129">按 F5 執行陳述式。</span><span class="sxs-lookup"><span data-stu-id="40760-129">Press F5 to execute the statements.</span></span> <span data-ttu-id="40760-130">檢查 **[結果]** 窗格，確認陳述式是否皆已成功地執行。</span><span class="sxs-lookup"><span data-stu-id="40760-130">Check the **Results** pane to verify that the statements have executed successfully.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40760-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="40760-131">See Also</span></span>  
 [<span data-ttu-id="40760-132">管理 DQS 資料庫</span><span class="sxs-lookup"><span data-stu-id="40760-132">Manage DQS Databases</span></span>](../../2014/data-quality-services/manage-dqs-databases.md)  
  
  
