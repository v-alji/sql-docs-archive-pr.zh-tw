---
title: 檢視邏輯備份裝置的屬性和內容 (SQL Server) | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- displaying backup content
- viewing backup content
- database backups [SQL Server], viewing content
- backing up databases [SQL Server], viewing content
- backing up databases [SQL Server], properties
- displaying backup properties
- backup devices [SQL Server], viewing information
- viewing backup properties
- database backups [SQL Server], properties
ms.assetid: 3a309074-e816-454d-b6c3-fcfdde0cbf74
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: f2bdf41e3dbda079e3627ff7a7c1c3c78103b728
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87702997"
---
# <a name="view-the-properties-and-contents-of-a-logical-backup-device-sql-server"></a><span data-ttu-id="cc90c-102">檢視邏輯備份裝置的屬性和內容 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="cc90c-102">View the Properties and Contents of a Logical Backup Device (SQL Server)</span></span>
  <span data-ttu-id="cc90c-103">此主題描述如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中檢視邏輯備份裝置的屬性和內容。</span><span class="sxs-lookup"><span data-stu-id="cc90c-103">This topic describes how to view the properties and contents of a logical backup device in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="cc90c-104">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="cc90c-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="cc90c-105">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="cc90c-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="cc90c-106">安全性</span><span class="sxs-lookup"><span data-stu-id="cc90c-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="cc90c-107">**若要使用下列項目檢視邏輯備份裝置的屬性和內容：**</span><span class="sxs-lookup"><span data-stu-id="cc90c-107">**To view the properties and contents of a logical backup device, using:**</span></span>  
  
     [<span data-ttu-id="cc90c-108">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="cc90c-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="cc90c-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="cc90c-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="cc90c-110">開始之前</span><span class="sxs-lookup"><span data-stu-id="cc90c-110">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="cc90c-111">Security</span><span class="sxs-lookup"><span data-stu-id="cc90c-111">Security</span></span>  
 <span data-ttu-id="cc90c-112">如需安全性的相關資訊，請參閱 [RESTORE LABELONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-labelonly-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="cc90c-112">For information about security, see [RESTORE LABELONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-labelonly-transact-sql).</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="cc90c-113">權限</span><span class="sxs-lookup"><span data-stu-id="cc90c-113">Permissions</span></span>  
 <span data-ttu-id="cc90c-114">在 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 及更新版本中，取得有關備份組或備份裝置的資訊需要 CREATE DATABASE 權限。</span><span class="sxs-lookup"><span data-stu-id="cc90c-114">In [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] and later versions, obtaining information about a backup set or backup device requires CREATE DATABASE permission.</span></span> <span data-ttu-id="cc90c-115">如需詳細資訊，請參閱 [GRANT 資料庫權限 &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-database-permissions-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="cc90c-115">For more information, see [GRANT Database Permissions &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-database-permissions-transact-sql).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="cc90c-116">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="cc90c-116">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-view-the-properties-and-contents-of-a-logical-backup-device"></a><span data-ttu-id="cc90c-117">若要檢視邏輯備份裝置的屬性和內容</span><span class="sxs-lookup"><span data-stu-id="cc90c-117">To view the properties and contents of a logical backup device</span></span>  
  
1.  <span data-ttu-id="cc90c-118">連線到適當的 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 執行個體之後，在物件總管中按一下伺服器名稱，以展開伺服器樹狀目錄。</span><span class="sxs-lookup"><span data-stu-id="cc90c-118">After connecting to the appropriate instance of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], in Object Explorer, click the server name to expand the server tree.</span></span>  
  
2.  <span data-ttu-id="cc90c-119">展開 **[伺服器物件]** ，然後展開 **[備份裝置]** 。</span><span class="sxs-lookup"><span data-stu-id="cc90c-119">Expand **Server Objects**, and expand **Backup Devices**.</span></span>  
  
3.  <span data-ttu-id="cc90c-120">按一下裝置，然後以滑鼠右鍵按一下 [屬性]  ，這時會開啟 [備份裝置]  對話方塊。</span><span class="sxs-lookup"><span data-stu-id="cc90c-120">Click the device and right-click **Properties**, which opens the **Backup Device** dialog box.</span></span>  
  
4.  <span data-ttu-id="cc90c-121">**[一般]** 頁面會顯示裝置名稱和目的地 (可能是磁帶裝置或檔案路徑)。</span><span class="sxs-lookup"><span data-stu-id="cc90c-121">The **General** page displays the device name and destination, which is either a tape device or file path.</span></span>  
  
5.  <span data-ttu-id="cc90c-122">在 **[選取頁面]** 窗格中，按一下 **[媒體內容]** 。</span><span class="sxs-lookup"><span data-stu-id="cc90c-122">In the **Select a Page** pane, click **Media Contents**.</span></span>  
  
6.  <span data-ttu-id="cc90c-123">右窗格會顯示在下列屬性面板中：</span><span class="sxs-lookup"><span data-stu-id="cc90c-123">The right-hand pane displays in the following properties panels:</span></span>  
  
    -   <span data-ttu-id="cc90c-124">**媒體**</span><span class="sxs-lookup"><span data-stu-id="cc90c-124">**Media**</span></span>  
  
         <span data-ttu-id="cc90c-125">媒體順序資訊 (如果有的話，則為媒體序號、家族序號及鏡像識別碼) 及媒體建立的日期和時間。</span><span class="sxs-lookup"><span data-stu-id="cc90c-125">Media sequence information (the media sequence number, the family sequence number, and the mirror identifier, if any) and the media creation date and time.</span></span>  
  
    -   <span data-ttu-id="cc90c-126">**媒體集**</span><span class="sxs-lookup"><span data-stu-id="cc90c-126">**Media set**</span></span>  
  
         <span data-ttu-id="cc90c-127">媒體集資訊：媒體集名稱和描述 (如果有的話)，以及媒體集的家族數目。</span><span class="sxs-lookup"><span data-stu-id="cc90c-127">Media set information: the media set name and description, if any, and the number of families in the media set.</span></span>  
  
7.  <span data-ttu-id="cc90c-128">**[備份組]** 方格會顯示媒體集內容的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="cc90c-128">The **Backup sets** grid displays information about the contents of the media set.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="cc90c-129">如需詳細資訊，請參閱 [媒體內容頁面](backup-device-media-contents-page.md)。</span><span class="sxs-lookup"><span data-stu-id="cc90c-129">For more information, see [Media Contents Page](backup-device-media-contents-page.md).</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="cc90c-130">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="cc90c-130">Using Transact-SQL</span></span>  
  
#### <a name="to-view-the-properties-and-contents-of-a-logical-backup-device"></a><span data-ttu-id="cc90c-131">若要檢視邏輯備份裝置的屬性和內容</span><span class="sxs-lookup"><span data-stu-id="cc90c-131">To view the properties and contents of a logical backup device</span></span>  
  
1.  <span data-ttu-id="cc90c-132">連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="cc90c-132">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="cc90c-133">在標準列中，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="cc90c-133">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="cc90c-134">使用 [RESTORE LABELONLY](/sql/t-sql/statements/restore-statements-labelonly-transact-sql) 陳述式。</span><span class="sxs-lookup"><span data-stu-id="cc90c-134">Use the [RESTORE LABELONLY](/sql/t-sql/statements/restore-statements-labelonly-transact-sql) statement.</span></span> <span data-ttu-id="cc90c-135">此範例會傳回 `AdvWrks2008R2Backup` 邏輯備份裝置的資訊。</span><span class="sxs-lookup"><span data-stu-id="cc90c-135">This example returns information about the `AdvWrks2008R2Backup` logical backup device.</span></span>  
  
```sql  
USE AdventureWorks2012 ;  
RESTORE LABELONLY  
   FROM AdvWrks2008R2Backup ;  
GO  
  
```  
  
## <a name="see-also"></a><span data-ttu-id="cc90c-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cc90c-136">See Also</span></span>  
 <span data-ttu-id="cc90c-137">[backupfilegroup &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupfilegroup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="cc90c-137">[backupfilegroup &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupfilegroup-transact-sql) </span></span>  
 <span data-ttu-id="cc90c-138">[backupfile &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupfile-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="cc90c-138">[backupfile &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupfile-transact-sql) </span></span>  
 <span data-ttu-id="cc90c-139">[backupset &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupset-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="cc90c-139">[backupset &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupset-transact-sql) </span></span>  
 <span data-ttu-id="cc90c-140">[backupmediaset &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupmediaset-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="cc90c-140">[backupmediaset &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupmediaset-transact-sql) </span></span>  
 <span data-ttu-id="cc90c-141">[backupmediafamily &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupmediafamily-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="cc90c-141">[backupmediafamily &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupmediafamily-transact-sql) </span></span>  
 <span data-ttu-id="cc90c-142">[sp_addumpdevice &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="cc90c-142">[sp_addumpdevice &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql) </span></span>  
 [<span data-ttu-id="cc90c-143">備份裝置 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="cc90c-143">Backup Devices &#40;SQL Server&#41;</span></span>](backup-devices-sql-server.md)  
  
  
