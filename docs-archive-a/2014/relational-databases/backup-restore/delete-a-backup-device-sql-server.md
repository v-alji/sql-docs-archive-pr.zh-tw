---
title: 刪除備份裝置 (SQL Server) | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- database backups [SQL Server], deleting devices
- backup devices [SQL Server], deleting
- deleting backup devices
- removing backup devices
- backing up databases [SQL Server], backup devices
ms.assetid: 7be62480-ed6a-4262-a071-1feba73b1c02
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: e8734e587a8ecde315fb17120511455a59e38901
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595139"
---
# <a name="delete-a-backup-device-sql-server"></a><span data-ttu-id="0acbd-102">刪除備份裝置 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="0acbd-102">Delete a Backup Device (SQL Server)</span></span>
  <span data-ttu-id="0acbd-103">此主題描述如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 來刪除 [!INCLUDE[tsql](../../includes/tsql-md.md)]中的備份裝置。</span><span class="sxs-lookup"><span data-stu-id="0acbd-103">This topic describes how to delete a backup device in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="0acbd-104">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="0acbd-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="0acbd-105">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="0acbd-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="0acbd-106">安全性</span><span class="sxs-lookup"><span data-stu-id="0acbd-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="0acbd-107">**若要使用下列項目刪除備份裝置：**</span><span class="sxs-lookup"><span data-stu-id="0acbd-107">**To delete a backup device, using:**</span></span>  
  
     [<span data-ttu-id="0acbd-108">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="0acbd-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="0acbd-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="0acbd-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="0acbd-110">開始之前</span><span class="sxs-lookup"><span data-stu-id="0acbd-110">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="0acbd-111">Security</span><span class="sxs-lookup"><span data-stu-id="0acbd-111">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="0acbd-112">權限</span><span class="sxs-lookup"><span data-stu-id="0acbd-112">Permissions</span></span>  
 <span data-ttu-id="0acbd-113">需要 **diskadmin** 固定伺服器角色的成員資格。</span><span class="sxs-lookup"><span data-stu-id="0acbd-113">Requires membership in the **diskadmin** fixed server role.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="0acbd-114">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="0acbd-114">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-delete-a-backup-device"></a><span data-ttu-id="0acbd-115">刪除備份裝置</span><span class="sxs-lookup"><span data-stu-id="0acbd-115">To delete a backup device</span></span>  
  
1.  <span data-ttu-id="0acbd-116">連接到適當的 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]執行個體之後，請在 [物件總管] 中按一下伺服器名稱以展開伺服器樹狀目錄。</span><span class="sxs-lookup"><span data-stu-id="0acbd-116">After connecting to the appropriate instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], in Object Explorer, click the server name to expand the server tree.</span></span>  
  
2.  <span data-ttu-id="0acbd-117">展開 **[伺服器物件]** ，然後展開 **[備份裝置]** 。</span><span class="sxs-lookup"><span data-stu-id="0acbd-117">Expand **Server Objects**, and then expand **Backup Devices**.</span></span>  
  
3.  <span data-ttu-id="0acbd-118">以滑鼠右鍵按一下所要的裝置，然後按一下 [刪除]  。</span><span class="sxs-lookup"><span data-stu-id="0acbd-118">Right-click the device you want, and then click **Delete**.</span></span>  
  
4.  <span data-ttu-id="0acbd-119">在 **[刪除物件]** 對話方塊，確認 **[物件名稱]** 資料行中所顯示的裝置名稱是正確的。</span><span class="sxs-lookup"><span data-stu-id="0acbd-119">In the **Delete Object** dialog box, verify that the correct device name appears in the **Object Name** column.</span></span>  
  
5.  <span data-ttu-id="0acbd-120">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="0acbd-120">Click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="0acbd-121">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="0acbd-121">Using Transact-SQL</span></span>  
  
#### <a name="to-delete-a-backup-device"></a><span data-ttu-id="0acbd-122">刪除備份裝置</span><span class="sxs-lookup"><span data-stu-id="0acbd-122">To delete a backup device</span></span>  
  
1.  <span data-ttu-id="0acbd-123">連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="0acbd-123">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="0acbd-124">在標準列中，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="0acbd-124">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="0acbd-125">複製下列範例並貼入查詢中。</span><span class="sxs-lookup"><span data-stu-id="0acbd-125">Copy and paste the following example into the query.</span></span> <span data-ttu-id="0acbd-126">此範例示範如何使用 [sp_dropdevice](/sql/relational-databases/system-stored-procedures/sp-dropdevice-transact-sql) 刪除備份裝置。</span><span class="sxs-lookup"><span data-stu-id="0acbd-126">This example shows how to use [sp_dropdevice](/sql/relational-databases/system-stored-procedures/sp-dropdevice-transact-sql) to delete a backup device.</span></span> <span data-ttu-id="0acbd-127">執行第一個範例，建立 `mybackupdisk` 備份裝置和實體名稱 `c:\backup\backup1.bak`。</span><span class="sxs-lookup"><span data-stu-id="0acbd-127">Execute the first example to create the `mybackupdisk` backup device and the physical name `c:\backup\backup1.bak`.</span></span> <span data-ttu-id="0acbd-128">執行 `sp_dropdevice` 刪除 `mybackupdisk` 備份裝置。</span><span class="sxs-lookup"><span data-stu-id="0acbd-128">Execute `sp_dropdevice` to delete the `mybackupdisk` backup device.</span></span> <span data-ttu-id="0acbd-129">`delfile` 參數會刪除實體名稱。</span><span class="sxs-lookup"><span data-stu-id="0acbd-129">The `delfile` parameter deletes the physical name.</span></span>  
  
```sql  
--Define a backup device and physical name.   
USE AdventureWorks2012 ;  
GO  
EXEC sp_addumpdevice 'disk', 'mybackupdisk', 'c:\backup\backup1.bak' ;  
GO  
--Delete the backup device and the physical name.  
USE AdventureWorks2012 ;  
GO  
EXEC sp_dropdevice ' mybackupdisk ', 'delfile' ;  
GO  
  
```  
  
## <a name="see-also"></a><span data-ttu-id="0acbd-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0acbd-130">See Also</span></span>  
 <span data-ttu-id="0acbd-131">[檢視邏輯備份裝置的屬性和內容 &#40;SQL Server&#41;](view-the-properties-and-contents-of-a-logical-backup-device-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="0acbd-131">[View the Properties and Contents of a Logical Backup Device &#40;SQL Server&#41;](view-the-properties-and-contents-of-a-logical-backup-device-sql-server.md) </span></span>  
 <span data-ttu-id="0acbd-132">[sys.backup_devices &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-backup-devices-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="0acbd-132">[sys.backup_devices &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-backup-devices-transact-sql) </span></span>  
 <span data-ttu-id="0acbd-133">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="0acbd-133">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 <span data-ttu-id="0acbd-134">[備份裝置 &#40;SQL Server&#41;](backup-devices-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="0acbd-134">[Backup Devices &#40;SQL Server&#41;](backup-devices-sql-server.md) </span></span>  
 [<span data-ttu-id="0acbd-135">sp_addumpdevice &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="0acbd-135">sp_addumpdevice &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql)  
  
  
