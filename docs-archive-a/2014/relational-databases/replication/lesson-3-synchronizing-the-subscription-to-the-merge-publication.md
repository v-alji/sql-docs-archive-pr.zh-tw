---
title: 第 3 課：同步處理合併式發行集的訂閱 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- replication [SQL Server], tutorials
ms.assetid: 49008384-2c55-4080-a890-9bceb40e4d6d
author: rothja
ms.author: jroth
ms.openlocfilehash: bf0256c69d69d1236869fa83285bf4dbf5c462da
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707374"
---
# <a name="lesson-3-synchronizing-the-subscription-to-the-merge-publication"></a><span data-ttu-id="fe859-102">第 3 課：同步處理合併式發行集的訂閱</span><span class="sxs-lookup"><span data-stu-id="fe859-102">Lesson 3: Synchronizing the Subscription to the Merge Publication</span></span>
  <span data-ttu-id="fe859-103">在這一課，您將啟動合併代理程式，以使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]來初始化訂閱。</span><span class="sxs-lookup"><span data-stu-id="fe859-103">In this lesson, you will start the Merge Agent to initialize the subscription using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="fe859-104">此外，您會使用此程序與發行者進行同步處理。</span><span class="sxs-lookup"><span data-stu-id="fe859-104">You also use this procedure to synchronize with the Publisher.</span></span> <span data-ttu-id="fe859-105">您必須先完成上一課 [第 2 課：建立合併式發行集的訂閱](lesson-2-creating-a-subscription-to-the-merge-publication.md)，才能進行這一課。</span><span class="sxs-lookup"><span data-stu-id="fe859-105">This lesson requires that you have completed the previous lesson, [Lesson 2: Creating a Subscription to the Merge Publication](lesson-2-creating-a-subscription-to-the-merge-publication.md).</span></span>  
  
### <a name="to-start-synchronization-and-initialize-the-subscription"></a><span data-ttu-id="fe859-106">啟動同步處理並初始化訂閱</span><span class="sxs-lookup"><span data-stu-id="fe859-106">To start synchronization and initialize the subscription</span></span>  
  
1.  <span data-ttu-id="fe859-107">連接到 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中的「訂閱者」，展開伺服器節點，然後展開 **[複寫]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="fe859-107">Connect to the Subscriber in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], expand the server node, and then expand the **Replication** folder.</span></span>  
  
2.  <span data-ttu-id="fe859-108">在 **[本機訂閱]** 資料夾中，以滑鼠右鍵按一下 **SalesOrdersReplica** 資料庫中的訂閱，然後按一下 **[檢視同步處理的狀態]**。</span><span class="sxs-lookup"><span data-stu-id="fe859-108">In the **Local Subscriptions** folder, right-click the subscription in the **SalesOrdersReplica** database, and then click **View Synchronization Status**.</span></span>  
  
3.  <span data-ttu-id="fe859-109">按一下 **[啟動]** ，以初始化訂閱。</span><span class="sxs-lookup"><span data-stu-id="fe859-109">Click **Start** to initialize the subscription.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="fe859-110">後續步驟</span><span class="sxs-lookup"><span data-stu-id="fe859-110">Next Steps</span></span>  
 <span data-ttu-id="fe859-111">您已順利執行合併代理程式，以啟動同步處理並初始化訂閱。</span><span class="sxs-lookup"><span data-stu-id="fe859-111">You have successfully run the Merge Agent to start synchronization and initialize the subscription.</span></span> <span data-ttu-id="fe859-112">您也可以在「發行者」或「訂閱者」端插入、更新或刪除 **SalesOrderHeader** 或 **SalesOrderDetail** 資料表中的資料，並且在可以使用網路連接來同步處理「發行者」或「訂閱者」之間的資料時，重複此程序，然後在其他伺服器上查詢 **SalesOrderHeader** 或 **SalesOrderDetail** 資料表，以檢視複寫的變更。</span><span class="sxs-lookup"><span data-stu-id="fe859-112">You can also insert, update, or delete data in the **SalesOrderHeader** or **SalesOrderDetail** tables at the Publisher or Subscriber, repeat this procedure when network connectivity is available to synchronize data between the Publisher and the Subscriber, and then query the **SalesOrderHeader** or **SalesOrderDetail** tables at the other server to view the replicated changes.</span></span>  
  
 <span data-ttu-id="fe859-113">如此即完成「利用行動用戶端複寫資料」教學課程。</span><span class="sxs-lookup"><span data-stu-id="fe859-113">This completes the Replicating Data with Mobile Clients tutorial.</span></span> <span data-ttu-id="fe859-114">如需使用異動複寫的類似教學課程，請參閱＜ [Tutorial: Replicating Data Between Continuously Connected Servers](tutorial-replicating-data-between-continuously-connected-servers.md)＞。</span><span class="sxs-lookup"><span data-stu-id="fe859-114">For a similar tutorial that uses transactional replication, see [Tutorial: Replicating Data Between Continuously Connected Servers](tutorial-replicating-data-between-continuously-connected-servers.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe859-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fe859-115">See Also</span></span>  
 <span data-ttu-id="fe859-116">[使用快照集初始化訂閱](initialize-a-subscription-with-a-snapshot.md) </span><span class="sxs-lookup"><span data-stu-id="fe859-116">[Initialize a Subscription with a Snapshot](initialize-a-subscription-with-a-snapshot.md) </span></span>  
 <span data-ttu-id="fe859-117">[同步處理資料](synchronize-data.md) </span><span class="sxs-lookup"><span data-stu-id="fe859-117">[Synchronize Data](synchronize-data.md) </span></span>  
 [<span data-ttu-id="fe859-118">同步處理提取訂閱</span><span class="sxs-lookup"><span data-stu-id="fe859-118">Synchronize a Pull Subscription</span></span>](synchronize-a-pull-subscription.md)  
  
  
