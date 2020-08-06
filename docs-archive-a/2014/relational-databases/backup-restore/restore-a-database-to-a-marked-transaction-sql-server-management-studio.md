---
title: 還原資料庫至標示的交易 (SQL Server Management Studio) | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
f1_keywords:
- sql12.swb.restoretlog.markedtransaction.f1
helpviewer_keywords:
- database restores [SQL Server], marked transactions
- restoring databases [SQL Server], marked transactions
- marked transactions [SQL Server], restoring
ms.assetid: 8f0ea144-1819-4832-905f-e5d0f49b066b
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 8de9ef5bed389f020f14e60ccd99f39698e7110f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598469"
---
# <a name="restore-a-database-to-a-marked-transaction-sql-server-management-studio"></a><span data-ttu-id="26ea1-102">還原資料庫至標示的異動 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="26ea1-102">Restore a Database to a Marked Transaction (SQL Server Management Studio)</span></span>
  <span data-ttu-id="26ea1-103">當資料庫處於還原中狀態時，您可以利用 [還原交易記錄]  對話方塊，將資料庫還原成可用記錄備份中標示的交易。</span><span class="sxs-lookup"><span data-stu-id="26ea1-103">When a database is in the restoring state, you can use the **Restore Transaction Log** dialog box to restore the database to a marked transaction in the available log backups.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="26ea1-104">如需詳細資訊，請參閱[使用標示的交易以一致的方式復原相關資料庫 &#40;完整復原模式&#41;](use-marked-transactions-to-recover-related-databases-consistently.md) 和[復原包含標示之交易的相關資料庫](recovery-of-related-databases-that-contain-marked-transaction.md)。</span><span class="sxs-lookup"><span data-stu-id="26ea1-104">For more information, see [Use Marked Transactions to Recover Related Databases Consistently &#40;Full Recovery Model&#41;](use-marked-transactions-to-recover-related-databases-consistently.md) and [Recovery of Related  Databases That Contain Marked Transaction](recovery-of-related-databases-that-contain-marked-transaction.md).</span></span>  
  
### <a name="to-restore-a-marked-transaction"></a><span data-ttu-id="26ea1-105">若要還原標示的交易</span><span class="sxs-lookup"><span data-stu-id="26ea1-105">To restore a marked transaction</span></span>  
  
1.  <span data-ttu-id="26ea1-106">連線到適當的 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 執行個體之後，在物件總管中按一下伺服器名稱，以展開伺服器樹狀目錄。</span><span class="sxs-lookup"><span data-stu-id="26ea1-106">After connecting to the appropriate instance of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], in Object Explorer, click the server name to expand the server tree.</span></span>  
  
2.  <span data-ttu-id="26ea1-107">展開 **[資料庫]** ，然後視資料庫而定，選取使用者資料庫，或者展開 **[系統資料庫]** 並選取一個系統資料庫。</span><span class="sxs-lookup"><span data-stu-id="26ea1-107">Expand **Databases**, and, depending on the database, either select a user database or expand **System Databases** and select a system database.</span></span>  
  
3.  <span data-ttu-id="26ea1-108">以滑鼠右鍵按一下資料庫，指向 [工作]  ，然後按一下 [還原]  。</span><span class="sxs-lookup"><span data-stu-id="26ea1-108">Right-click the database, point to **Tasks**, and then click **Restore**.</span></span>  
  
4.  <span data-ttu-id="26ea1-109">按一下 [交易記錄]  ，這會開啟 [還原交易記錄]  對話方塊。</span><span class="sxs-lookup"><span data-stu-id="26ea1-109">Click **Transaction Log**, which opens the **Restore Transaction Log** dialog box.</span></span>  
  
5.  <span data-ttu-id="26ea1-110">在 [一般]  頁面的 [還原至]  區段中，選取 [標示的交易]  ，這會開啟 [選取標示的交易]  對話方塊。</span><span class="sxs-lookup"><span data-stu-id="26ea1-110">On the **General** page, in the **Restore To** section, select **Marked transaction**, which opens the **Select Marked Transaction** dialog box.</span></span> <span data-ttu-id="26ea1-111">這個對話方塊會顯示一個方格，其中列出在選取的交易記錄備份中，可用之標示的交易。</span><span class="sxs-lookup"><span data-stu-id="26ea1-111">This dialog box displays a grid listing the marked transactions available in the selected transaction log backups.</span></span>  
  
     <span data-ttu-id="26ea1-112">依預設，會還原到標示的交易，但是不含該交易。</span><span class="sxs-lookup"><span data-stu-id="26ea1-112">By default, the restore is up to, but excluding, the marked transaction.</span></span> <span data-ttu-id="26ea1-113">若也要還原標示的交易，請選取 **[包含標示的交易]** 。</span><span class="sxs-lookup"><span data-stu-id="26ea1-113">To restore the marked transaction also, select **Include marked transaction**.</span></span>  
  
     <span data-ttu-id="26ea1-114">下表列出方格的各資料行標頭，並描述各標頭的值。</span><span class="sxs-lookup"><span data-stu-id="26ea1-114">The following table lists the column headers of the grid and describes their values.</span></span>  
  
    |<span data-ttu-id="26ea1-115">頁首</span><span class="sxs-lookup"><span data-stu-id="26ea1-115">Header</span></span>|<span data-ttu-id="26ea1-116">值</span><span class="sxs-lookup"><span data-stu-id="26ea1-116">Value</span></span>|  
    |------------|-----------|  
    |\<blank>|<span data-ttu-id="26ea1-117">顯示選取標示的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="26ea1-117">Displays a checkbox for selecting the mark.</span></span>|  
    |<span data-ttu-id="26ea1-118">**交易標示**</span><span class="sxs-lookup"><span data-stu-id="26ea1-118">**Transaction Mark**</span></span>|<span data-ttu-id="26ea1-119">在認可交易時，由使用者所指定之標示交易的名稱。</span><span class="sxs-lookup"><span data-stu-id="26ea1-119">Name of the marked transaction specified by the user when the transaction was committed.</span></span>|  
    |<span data-ttu-id="26ea1-120">**日期**</span><span class="sxs-lookup"><span data-stu-id="26ea1-120">**Date**</span></span>|<span data-ttu-id="26ea1-121">認可交易的日期和時間。</span><span class="sxs-lookup"><span data-stu-id="26ea1-121">Date and time of the transaction when it was committed.</span></span> <span data-ttu-id="26ea1-122">交易日期和時間是依照 **msdbgmarkhistory** 資料表中記錄的顯示，而非依照用戶端電腦的日期和時間。</span><span class="sxs-lookup"><span data-stu-id="26ea1-122">Transaction date and time are displayed as recorded in the **msdbgmarkhistory** table, not in the client computer's date and time.</span></span>|  
    |<span data-ttu-id="26ea1-123">**說明**</span><span class="sxs-lookup"><span data-stu-id="26ea1-123">**Description**</span></span>|<span data-ttu-id="26ea1-124">在認可交易時，由使用者所指定之標示交易的描述 (如果有的話)。</span><span class="sxs-lookup"><span data-stu-id="26ea1-124">Description of marked transaction specified by the user when the transaction was committed (if any).</span></span>|  
    |<span data-ttu-id="26ea1-125">**LSN**</span><span class="sxs-lookup"><span data-stu-id="26ea1-125">**LSN**</span></span>|<span data-ttu-id="26ea1-126">標示之交易的記錄序號。</span><span class="sxs-lookup"><span data-stu-id="26ea1-126">Log sequence number of the marked transaction.</span></span>|  
    |<span data-ttu-id="26ea1-127">**Database**</span><span class="sxs-lookup"><span data-stu-id="26ea1-127">**Database**</span></span>|<span data-ttu-id="26ea1-128">認可標示的交易之資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="26ea1-128">Name of the database where the marked transaction was committed.</span></span>|  
    |<span data-ttu-id="26ea1-129">**使用者名稱**</span><span class="sxs-lookup"><span data-stu-id="26ea1-129">**User Name**</span></span>|<span data-ttu-id="26ea1-130">認可標示的交易之資料庫使用者的名稱。</span><span class="sxs-lookup"><span data-stu-id="26ea1-130">Name of the database user who committed the marked transaction.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="26ea1-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="26ea1-131">See Also</span></span>  
 <span data-ttu-id="26ea1-132">[還原資料庫備份 &#40;SQL Server Management Studio&#41;](restore-a-database-backup-using-ssms.md) </span><span class="sxs-lookup"><span data-stu-id="26ea1-132">[Restore a Database Backup &#40;SQL Server Management Studio&#41;](restore-a-database-backup-using-ssms.md) </span></span>  
 [<span data-ttu-id="26ea1-133">還原交易記錄備份 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="26ea1-133">Restore a Transaction Log Backup &#40;SQL Server&#41;</span></span>](restore-a-transaction-log-backup-sql-server.md)  
  
  
