---
title: 為交易式發行集啟用使用備份進行初始化， (SQL Server Management Studio) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- manual subscription initialization [SQL Server replication]
- subscriptions [SQL Server replication], initializing
- initializing subscriptions [SQL Server replication], without snapshots
- transactional replication, backup and restore
- backups [SQL Server replication], transactional replication
ms.assetid: 9df00514-aa9d-4ac6-9766-d226c9958175
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f5e22614c8c4f5250db3966e747b686091512774
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585851"
---
# <a name="enable-initialization-with-a-backup-for-transactional-publications-sql-server-management-studio"></a><span data-ttu-id="e1891-102">為交易式發行集啟用使用備份的初始化 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="e1891-102">Enable Initialization with a Backup for Transactional Publications (SQL Server Management Studio)</span></span>
  <span data-ttu-id="e1891-103">若要從備份初始化交易式發行集的訂閱，請啟用發行集以允許從備份進行初始化，然後在建立訂閱時指定備份資訊：</span><span class="sxs-lookup"><span data-stu-id="e1891-103">To initialize a subscription to a transactional publication from a backup, enable the publication to allow initialization from a backup, and then specify backup information when creating the subscription:</span></span>  
  
-   <span data-ttu-id="e1891-104">在 [發行集屬性 - \<Publication>] 對話方塊的 [訂閱選項] 頁面上啟用發行集。</span><span class="sxs-lookup"><span data-stu-id="e1891-104">Enable the publication on the **Subscription Options** page of the **Publication Properties - \<Publication>** dialog box.</span></span> <span data-ttu-id="e1891-105">如需有關存取這個對話方塊的詳細資訊，請參閱＜ [View and Modify Publication Properties](publish/view-and-modify-publication-properties.md)＞。</span><span class="sxs-lookup"><span data-stu-id="e1891-105">For more information about accessing this dialog box, see [View and Modify Publication Properties](publish/view-and-modify-publication-properties.md).</span></span>  
  
-   <span data-ttu-id="e1891-106">使用預存程序 [sp_addsubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addsubscription-transact-sql) 指定備份資訊。</span><span class="sxs-lookup"><span data-stu-id="e1891-106">Specify backup information with the stored procedure [sp_addsubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addsubscription-transact-sql).</span></span> <span data-ttu-id="e1891-107">如需 **sp_addsubscription** 所需參數的詳細資訊，請參閱[從備份初始化交易式訂閱 &#40;複寫 Transact-SQL 程式設計&#41;](initialize-a-transactional-subscription-from-a-backup.md)。</span><span class="sxs-lookup"><span data-stu-id="e1891-107">For more information about the parameters required by **sp_addsubscription**, see [Initialize a Transactional Subscription from a Backup &#40;Replication Transact-SQL Programming&#41;](initialize-a-transactional-subscription-from-a-backup.md).</span></span>  
  
### <a name="to-enable-initialization-with-a-backup"></a><span data-ttu-id="e1891-108">若要啟用使用備份的初始化</span><span class="sxs-lookup"><span data-stu-id="e1891-108">To enable initialization with a backup</span></span>  
  
1.  <span data-ttu-id="e1891-109">在 [發行集屬性 - \<Publication>] 對話方塊的 [訂閱選項] 頁面上，將 [允許從備份檔案初始化] 選項選取為值 [True]。</span><span class="sxs-lookup"><span data-stu-id="e1891-109">On the **Subscription Options** page of the **Publication Properties - \<Publication>** dialog box, select a value of **True** for the **Allow initialization from backup files** option.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1891-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e1891-110">See Also</span></span>  
 [<span data-ttu-id="e1891-111">不使用快照集初始化交易式訂閱</span><span class="sxs-lookup"><span data-stu-id="e1891-111">Initialize a Transactional Subscription Without a Snapshot</span></span>](initialize-a-transactional-subscription-without-a-snapshot.md)  
  
  
