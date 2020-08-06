---
title: 第 3 課：驗證訂閱及測量延遲 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- replication [SQL Server], tutorials
ms.assetid: 147f7b93-1804-4e0b-9e17-57a51d035b2a
author: rothja
ms.author: jroth
ms.openlocfilehash: e4893c054d25d131eb2f88f32291606b0b789af7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707373"
---
# <a name="lesson-3-validating-the-subscription-and-measuring-latency"></a><span data-ttu-id="08b53-102">第 3 課：驗證訂閱及測量延遲</span><span class="sxs-lookup"><span data-stu-id="08b53-102">Lesson 3: Validating the Subscription and Measuring Latency</span></span>
  <span data-ttu-id="08b53-103">在這一課，您將使用追蹤 Token，以確認變更正複寫至訂閱者，並決定延遲 (亦即在「發行者」端所做變更顯示在「訂閱者」上所花費的時間)。</span><span class="sxs-lookup"><span data-stu-id="08b53-103">In this lesson, you will use tracer tokens to verify that changes are being replicated to the Subscriber and to determine latency, the time it takes for a change made at the Publisher to appear to the Subscriber.</span></span> <span data-ttu-id="08b53-104">您必須先完成上一課 [第 2 課：建立交易式發行集的訂閱](lesson-2-creating-a-subscription-to-the-transactional-publication.md)，才能進行這一課。</span><span class="sxs-lookup"><span data-stu-id="08b53-104">This lesson requires that you have completed the previous lesson, [Lesson 2: Creating a Subscription to the Transactional Publication](lesson-2-creating-a-subscription-to-the-transactional-publication.md).</span></span>  
  
### <a name="to-insert-a-tracer-token-and-view-information-on-the-token"></a><span data-ttu-id="08b53-105">插入追蹤 Token 並檢視 Token 上的資訊</span><span class="sxs-lookup"><span data-stu-id="08b53-105">To insert a tracer token and view information on the token</span></span>  
  
1.  <span data-ttu-id="08b53-106">連接到 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中的「發行者」，展開伺服器節點，再以滑鼠右鍵按一下 [複寫]\*\*\*\* 資料夾，然後按一下 [啟動複寫監視器]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="08b53-106">Connect to the Publisher in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], expand the server node, right-click the **Replication** folder, and then click **Launch Replication Monitor**.</span></span>  
  
     <span data-ttu-id="08b53-107">複寫監視器隨即啟動。</span><span class="sxs-lookup"><span data-stu-id="08b53-107">Replication Monitor launches.</span></span>  
  
2.  <span data-ttu-id="08b53-108">在左窗格中展開「發行者」群組，展開「發行者」執行個體，然後按一下 **AdvWorksProductTrans** 發行集。</span><span class="sxs-lookup"><span data-stu-id="08b53-108">Expand a Publisher group in the left pane, expand the Publisher instance, and then click the **AdvWorksProductTrans** publication.</span></span>  
  
3.  <span data-ttu-id="08b53-109">按一下 **[追蹤 Token]** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="08b53-109">Click the **Tracer Tokens** tab.</span></span>  
  
4.  <span data-ttu-id="08b53-110">按一下 **[插入追蹤]**。</span><span class="sxs-lookup"><span data-stu-id="08b53-110">Click **Insert Tracer**.</span></span>  
  
5.  <span data-ttu-id="08b53-111">在下列資料行中檢視追蹤 Token 的經過時間： **[發行者到散發者]**、 **[散發者到訂閱者]**、 **[延遲總計]**。</span><span class="sxs-lookup"><span data-stu-id="08b53-111">View elapsed time for the tracer token in the following columns: **Publisher to Distributor**, **Distributor to Subscriber**, **Total Latency**.</span></span> <span data-ttu-id="08b53-112">值為 [**暫**止] 表示 token 尚未到達指定的點。</span><span class="sxs-lookup"><span data-stu-id="08b53-112">A value of **Pending** indicates that the token has not reached a given point.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="08b53-113">後續步驟</span><span class="sxs-lookup"><span data-stu-id="08b53-113">Next Steps</span></span>  
 <span data-ttu-id="08b53-114">在這一課，您已順利使用追蹤 Token，驗證資料變更正從「發行者」複寫至「訂閱者」。</span><span class="sxs-lookup"><span data-stu-id="08b53-114">In this lesson, you successfully used tracer tokens to validate that data changes are being replicated from the Publisher to the Subscriber.</span></span> <span data-ttu-id="08b53-115">您也可以在「發行者」端插入、更新或刪除 **Product** 資料表中的資料，並在複寫之後，在「訂閱者」端查詢 **Product** 資料表，檢視這些變更。</span><span class="sxs-lookup"><span data-stu-id="08b53-115">You can also insert, update, or delete data in the **Product** table at the Publisher and query the **Product** table at the Subscriber to view these changes after they are replicated.</span></span>  
  
 <span data-ttu-id="08b53-116">如此即已完成＜在連續連接的伺服器之間複寫資料＞教學課程。</span><span class="sxs-lookup"><span data-stu-id="08b53-116">This completes the Replicating Data Between Continuously Connected Servers tutorial.</span></span> <span data-ttu-id="08b53-117">如需使用合併式複寫的類似教學課程，請參閱 [教學課程：利用行動用戶端複寫資料](tutorial-replicating-data-with-mobile-clients.md)。</span><span class="sxs-lookup"><span data-stu-id="08b53-117">For a similar tutorial that uses merge replication, see [Tutorial: Replicating Data with Mobile Clients](tutorial-replicating-data-with-mobile-clients.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08b53-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="08b53-118">See Also</span></span>  
 [<span data-ttu-id="08b53-119">針對異動複寫測量延遲及驗證連接</span><span class="sxs-lookup"><span data-stu-id="08b53-119">Measure Latency and Validate Connections for Transactional Replication</span></span>](monitor/measure-latency-and-validate-connections-for-transactional-replication.md)  
  
  
