---
title: 發行集資訊、追蹤 token (交易式發行集、SQL Server 2005 和更新版本) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.monitor.publicationinfo.tracertokens.f1
ms.assetid: a115ba95-17ae-45df-91bd-5a1a35f3745f
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: af84ab9b9122a55367780976056ce95aa597f62a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705009"
---
# <a name="publication-information-tracer-tokens-transactional-publication-sql-server-2005-and-later"></a><span data-ttu-id="6b133-102">發行集資訊、追蹤 Token (交易式發行集、SQL Server 2005 和更新的版本)</span><span class="sxs-lookup"><span data-stu-id="6b133-102">Publication Information, Tracer Tokens (Transactional Publication, SQL Server 2005 and Later)</span></span>
  <span data-ttu-id="6b133-103"> [追蹤 Token\]\*\*\** 索引標籤，可讓您驗證連線並測量使用異動複寫之系統的延遲。</span><span class="sxs-lookup"><span data-stu-id="6b133-103">The **Tracer Tokens** tab allows you to validate connections and to measure the latency of a system that uses transactional replication.</span></span> <span data-ttu-id="6b133-104">Token (即少量的資料) 會寫入發行集資料庫的交易記錄，會標示為典型的已複寫交易並且會透過系統傳送，它可允許計算：</span><span class="sxs-lookup"><span data-stu-id="6b133-104">A token (a small amount of data) is written to the transaction log of the publication database, marked as though it were a typical replicated transaction, and sent through the system, allowing a calculation of:</span></span>  
  
-   <span data-ttu-id="6b133-105">在發行者端認可交易和在散發者端之散發資料庫插入對應的命令之間，所經過的時間。</span><span class="sxs-lookup"><span data-stu-id="6b133-105">How much time elapses between a transaction being committed at the Publisher and the corresponding command being inserted in the distribution database at the Distributor.</span></span>  
  
-   <span data-ttu-id="6b133-106">在散發資料庫中插入命令和在訂閱者端認可對應的交易之間，所經過的時間。</span><span class="sxs-lookup"><span data-stu-id="6b133-106">How much time elapses between a command being inserted in the distribution database and the corresponding transaction being committed at a Subscriber.</span></span>  
  
 <span data-ttu-id="6b133-107">根據以上計算，您可以回答許多問題，包括：</span><span class="sxs-lookup"><span data-stu-id="6b133-107">From these calculations, you can answer a number of questions, including:</span></span>  
  
-   <span data-ttu-id="6b133-108">哪些訂閱者在接收發行者的變更時，所花費的時間最長？</span><span class="sxs-lookup"><span data-stu-id="6b133-108">Which Subscribers take the longest to receive a change from the Publisher?</span></span>  
  
-   <span data-ttu-id="6b133-109">預期會收到追蹤 Token 的訂閱者中，哪些沒有接收到 (如果有的話)？</span><span class="sxs-lookup"><span data-stu-id="6b133-109">Of the Subscribers expected to receive the tracer token, which, if any, have not received it?</span></span>  
  
## <a name="options"></a><span data-ttu-id="6b133-110">選項</span><span class="sxs-lookup"><span data-stu-id="6b133-110">Options</span></span>  
 <span data-ttu-id="6b133-111">若要變更方格顯示資料的方式，請以滑鼠右鍵按一下方格，然後按一下下列其中一個選項：</span><span class="sxs-lookup"><span data-stu-id="6b133-111">To change the way that the grid displays data, right-click the grid, and then click one of the following options:</span></span>  
  
-   <span data-ttu-id="6b133-112">**排序**：在 **[排序資料行]** 對話方塊中排序一個或多個資料行。</span><span class="sxs-lookup"><span data-stu-id="6b133-112">**Sort**: Sort on one or more columns in the **Sort Columns** dialog box.</span></span>  
  
-   <span data-ttu-id="6b133-113">**選擇要顯示的資料行**：選取要顯示哪些資料行，以及在 **[選擇資料行]** 對話方塊中顯示這些資料行所依循的順序。</span><span class="sxs-lookup"><span data-stu-id="6b133-113">**Choose Columns to Show**: Select which columns to display and the order in which to display them in the **Choose Columns** dialog box.</span></span>  
  
-   <span data-ttu-id="6b133-114">**篩選**：根據 **[篩選設定]** 對話方塊中的資料行值，篩選方格中的資料列。</span><span class="sxs-lookup"><span data-stu-id="6b133-114">**Filter**: Filter rows in the grid based on column values in the **Filter Settings** dialog box.</span></span>  
  
-   <span data-ttu-id="6b133-115">**清除篩選**：清除方格的所有篩選設定。</span><span class="sxs-lookup"><span data-stu-id="6b133-115">**Clear Filter**: Clear any filter settings for the grid.</span></span>  
  
 <span data-ttu-id="6b133-116">篩選設定是每個方格特有的設定。</span><span class="sxs-lookup"><span data-stu-id="6b133-116">Filter settings are specific to each grid.</span></span> <span data-ttu-id="6b133-117">資料行選取和排序會套用至所有相同類型的方格，例如每個發行者的發行集方格。</span><span class="sxs-lookup"><span data-stu-id="6b133-117">Column selection and sorting are applied to all grids of the same type, such as the publications grid for each Publisher.</span></span>  
  
 <span data-ttu-id="6b133-118">**插入追蹤**</span><span class="sxs-lookup"><span data-stu-id="6b133-118">**Insert Tracer**</span></span>  
 <span data-ttu-id="6b133-119">按一下即可在發行者端的交易記錄中插入追蹤 Token。</span><span class="sxs-lookup"><span data-stu-id="6b133-119">Click to insert a tracer token in the transaction log at the Publisher.</span></span>  
  
 <span data-ttu-id="6b133-120">**插入的時間**</span><span class="sxs-lookup"><span data-stu-id="6b133-120">**Time inserted**</span></span>  
 <span data-ttu-id="6b133-121">選取插入追蹤 Token 的時間，來顯示該時間的延遲資訊。</span><span class="sxs-lookup"><span data-stu-id="6b133-121">Select a time at which a tracer token was inserted to display latency information from that time.</span></span> <span data-ttu-id="6b133-122">依預設，會顯示最近時間的資訊。</span><span class="sxs-lookup"><span data-stu-id="6b133-122">By default, information from the most recent time is displayed.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6b133-123">追蹤 Token 資訊與其他記錄資料的保留時間週期相同，這會由散發資料庫的記錄保留期限控制。</span><span class="sxs-lookup"><span data-stu-id="6b133-123">Tracer token information is retained for the same time period as other historical data, which is governed by the history retention period of the distribution database.</span></span> <span data-ttu-id="6b133-124">如需變更散發資料庫屬性的詳細資訊，請參閱[檢視及修改散發者和發行者屬性](view-and-modify-distributor-and-publisher-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="6b133-124">For information about changing distribution database properties, see [View and Modify Distributor and Publisher Properties](view-and-modify-distributor-and-publisher-properties.md).</span></span>  
  
 <span data-ttu-id="6b133-125">**訂用帳戶**</span><span class="sxs-lookup"><span data-stu-id="6b133-125">**Subscription**</span></span>  
 <span data-ttu-id="6b133-126">發行集之每個訂閱的名稱。</span><span class="sxs-lookup"><span data-stu-id="6b133-126">The name of each subscription to the publication.</span></span>  
  
 <span data-ttu-id="6b133-127">**發行者到散發者**</span><span class="sxs-lookup"><span data-stu-id="6b133-127">**Publisher to Distributor**</span></span>  
 <span data-ttu-id="6b133-128">在發行者端認可交易和在散發者端之散發資料庫插入對應的命令之間，所經過的時間。</span><span class="sxs-lookup"><span data-stu-id="6b133-128">The elapsed time between a transaction being committed at the Publisher and the corresponding command being inserted in the distribution database at the Distributor.</span></span> <span data-ttu-id="6b133-129">值為 **[暫止]** 指出 Token 尚未到達散發者。</span><span class="sxs-lookup"><span data-stu-id="6b133-129">A value of **Pending** indicates that the token has not yet reached the Distributor.</span></span> <span data-ttu-id="6b133-130">如果暫止狀態持續，請確定記錄讀取器代理程式在執行中。</span><span class="sxs-lookup"><span data-stu-id="6b133-130">If the pending state persists, ensure that the Log Reader Agent is running.</span></span>  
  
 <span data-ttu-id="6b133-131">**散發者到訂閱者**</span><span class="sxs-lookup"><span data-stu-id="6b133-131">**Distributor to Subscriber**</span></span>  
 <span data-ttu-id="6b133-132">在散發資料庫中插入命令和在訂閱者端認可對應的交易之間，所經過的時間。</span><span class="sxs-lookup"><span data-stu-id="6b133-132">The elapsed time between a command being inserted in the distribution database and the corresponding transaction being committed at a Subscriber.</span></span> <span data-ttu-id="6b133-133">值為 **[暫止]** 指出 Token 尚未到達訂閱者。</span><span class="sxs-lookup"><span data-stu-id="6b133-133">A value of **Pending** indicates that the token has not yet reached the Subscriber.</span></span> <span data-ttu-id="6b133-134">如果暫止狀態持續，請確定散發代理程式在執行中。</span><span class="sxs-lookup"><span data-stu-id="6b133-134">If the pending state persists, ensure that the Distribution Agent is running.</span></span>  
  
 <span data-ttu-id="6b133-135">**延遲總計**</span><span class="sxs-lookup"><span data-stu-id="6b133-135">**Total Latency**</span></span>  
 <span data-ttu-id="6b133-136">在發行者端認可交易和在訂閱者端認可對應的交易之間，所經過的時間。</span><span class="sxs-lookup"><span data-stu-id="6b133-136">The elapsed time between a transaction being committed at the Publisher and the corresponding transaction being committed at the Subscriber.</span></span> <span data-ttu-id="6b133-137">這代表此時該訂閱者之複寫系統的端對端延遲。</span><span class="sxs-lookup"><span data-stu-id="6b133-137">This represents the end-to-end latency of the replication system for this Subscriber at this time.</span></span> <span data-ttu-id="6b133-138">值為 **[暫止]** 指出 Token 尚未到達訂閱者。</span><span class="sxs-lookup"><span data-stu-id="6b133-138">A value of **Pending** indicates that the token has not yet reached the Subscriber.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b133-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6b133-139">See Also</span></span>  
 <span data-ttu-id="6b133-140">[啟動及停止複寫代理程式 &#40;SQL Server Management Studio&#41;](agents/start-and-stop-a-replication-agent-sql-server-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="6b133-140">[Start and Stop a Replication Agent &#40;SQL Server Management Studio&#41;](agents/start-and-stop-a-replication-agent-sql-server-management-studio.md) </span></span>  
 <span data-ttu-id="6b133-141">[啟動複寫監視器](monitor/start-the-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="6b133-141">[Start the Replication Monitor](monitor/start-the-replication-monitor.md) </span></span>  
 <span data-ttu-id="6b133-142">[測量異動複寫的延遲並驗證連接](monitor/measure-latency-and-validate-connections-for-transactional-replication.md) </span><span class="sxs-lookup"><span data-stu-id="6b133-142">[Measure Latency and Validate Connections for Transactional Replication](monitor/measure-latency-and-validate-connections-for-transactional-replication.md) </span></span>  
 <span data-ttu-id="6b133-143">[使用複寫監視器監視效能](monitor/monitor-performance-with-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="6b133-143">[Monitor Performance with Replication Monitor](monitor/monitor-performance-with-replication-monitor.md) </span></span>  
 <span data-ttu-id="6b133-144">[監視複寫](monitoring-replication.md) </span><span class="sxs-lookup"><span data-stu-id="6b133-144">[Monitoring Replication](monitoring-replication.md) </span></span>  
 [<span data-ttu-id="6b133-145">複寫代理程式概觀</span><span class="sxs-lookup"><span data-stu-id="6b133-145">Replication Agents Overview</span></span>](agents/replication-agents-overview.md)  
  
  
