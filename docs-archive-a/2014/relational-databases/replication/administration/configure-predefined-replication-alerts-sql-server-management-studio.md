---
title: 設定預先定義的複寫警示 (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- alerts [SQL Server replication]
- predefined replication alerts [SQL Server replication]
ms.assetid: c0414147-7ffe-4f9a-908c-71c1b5201584
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: aa78a08757cc7bbe809c5e3a1808c9632b76763a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709257"
---
# <a name="configure-predefined-replication-alerts-sql-server-management-studio"></a><span data-ttu-id="24921-102">設定預先定義的複寫警示 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="24921-102">Configure Predefined Replication Alerts (SQL Server Management Studio)</span></span>
  <span data-ttu-id="24921-103">複寫提供下列預先定義的警示，這些警示可設定為回應複寫事件：</span><span class="sxs-lookup"><span data-stu-id="24921-103">Replication offers the following predefined alerts, which can be configured to respond to replication events:</span></span>  
  
-   <span data-ttu-id="24921-104">**複寫: 代理程式成功**</span><span class="sxs-lookup"><span data-stu-id="24921-104">**Replication: agent success**</span></span>    
-   <span data-ttu-id="24921-105">**複寫: 代理程式失敗**</span><span class="sxs-lookup"><span data-stu-id="24921-105">**Replication: agent failure**</span></span>    
-   <span data-ttu-id="24921-106">**複寫: 代理程式重試**</span><span class="sxs-lookup"><span data-stu-id="24921-106">**Replication: agent retry**</span></span>    
-   <span data-ttu-id="24921-107">**複寫: 已卸除逾期的訂閱**</span><span class="sxs-lookup"><span data-stu-id="24921-107">**Replication: expired subscription dropped**</span></span>    
-   <span data-ttu-id="24921-108">**複寫：驗證失敗後重新初始化訂閱**</span><span class="sxs-lookup"><span data-stu-id="24921-108">**Replication: Subscription reinitialized after validation failure**</span></span>    
-   <span data-ttu-id="24921-109">**複寫：訂閱者資料驗證失敗**</span><span class="sxs-lookup"><span data-stu-id="24921-109">**Replication: Subscriber has failed data validation**</span></span>    
-   <span data-ttu-id="24921-110">**複寫：訂閱者已經通過資料驗證**</span><span class="sxs-lookup"><span data-stu-id="24921-110">**Replication: Subscriber has passed data validation**</span></span>    
-   <span data-ttu-id="24921-111">**複寫: 代理程式自訂關閉**</span><span class="sxs-lookup"><span data-stu-id="24921-111">**Replication: agent custom shutdown**</span></span>  
  
 <span data-ttu-id="24921-112">從 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 中的 [警示] 資料夾或複寫監視器中的 [警告] 索引標籤設定這些警示。</span><span class="sxs-lookup"><span data-stu-id="24921-112">Configure these alerts from the **Alerts** folder in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] or the **Warnings** tab in Replication Monitor.</span></span> <span data-ttu-id="24921-113">如需存取此索引標籤的詳細資訊，請參閱[使用複寫監視器來查看資訊及執行](../monitor/view-information-and-perform-tasks-replication-monitor.md)工作。</span><span class="sxs-lookup"><span data-stu-id="24921-113">For more information about accessing this tab, see [View Information and Perform Tasks using Replication Monitor](../monitor/view-information-and-perform-tasks-replication-monitor.md).</span></span>  
  
 <span data-ttu-id="24921-114">除了這些警示外，複寫監視器還提供與狀態和效能相關的警告與警示集合。</span><span class="sxs-lookup"><span data-stu-id="24921-114">In addition to these alerts, Replication Monitor provides a set of warnings and alerts related to status and performance.</span></span> <span data-ttu-id="24921-115">如需詳細資訊，請參閱在複寫監視器警示基礎結構[中設定臨界值和警告](../monitor/set-thresholds-and-warnings-in-replication-monitor.md)。</span><span class="sxs-lookup"><span data-stu-id="24921-115">For more information, see [Set Thresholds and Warnings in Replication Monitor](../monitor/set-thresholds-and-warnings-in-replication-monitor.md) alerts infrastructure.</span></span> <span data-ttu-id="24921-116">如需詳細資訊，請參閱[建立使用者定義的事件](../../../ssms/agent/create-a-user-defined-event.md)。</span><span class="sxs-lookup"><span data-stu-id="24921-116">For more information, see [Create a User-Defined Event](../../../ssms/agent/create-a-user-defined-event.md).</span></span>  
  
### <a name="to-configure-a-predefined-replication-alert-in-management-studio"></a><span data-ttu-id="24921-117">若要在 Management Studio 中設定預先定義的複寫警示</span><span class="sxs-lookup"><span data-stu-id="24921-117">To configure a predefined replication alert in Management Studio</span></span>  
  
1.  <span data-ttu-id="24921-118">連接到 [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)]中的散發者，然後展開伺服器節點。</span><span class="sxs-lookup"><span data-stu-id="24921-118">Connect to the Distributor in [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)], and then expand the server node.</span></span>    
2.  <span data-ttu-id="24921-119">展開 **[SQL Server Agent]** 資料夾，然後展開 **[警示]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="24921-119">Expand the **SQL Server Agent** folder, and then expand the **Alerts** folder.</span></span>    
3.  <span data-ttu-id="24921-120">以滑鼠右鍵按一下複寫警示，然後按一下 **[屬性]** 。</span><span class="sxs-lookup"><span data-stu-id="24921-120">Right-click a replication alert, and then click **Properties**.</span></span>    
4.  <span data-ttu-id="24921-121">在 [\<AlertName> 警示屬性] 對話方塊中設定選項：</span><span class="sxs-lookup"><span data-stu-id="24921-121">Set options in the **\<AlertName> alert properties** dialog box:</span></span>    
    -   <span data-ttu-id="24921-122">在 **[一般]** 頁面上，按一下 **[啟用]** ；指定警示應套用至哪個資料庫。</span><span class="sxs-lookup"><span data-stu-id="24921-122">On the **General** page, click **Enable**; specify which database the alert should apply to.</span></span>    
    -   <span data-ttu-id="24921-123">在 **[回應]** 頁面上，指定是否應傳送電子郵件及 (或) 是否應執行作業。</span><span class="sxs-lookup"><span data-stu-id="24921-123">On the **Response** page, specify whether an e-mail should be sent and/or a job should be executed.</span></span>  
  
         <span data-ttu-id="24921-124">若警示是**複寫：** 訂閱者資料驗證失敗」，您可以指定複寫為此警示提供的回應作業：選取 [執行作業]，然後按一下瀏覽按鈕 ( **...** )。在 **[尋找作業]** 對話方塊中，按一下 **[瀏覽]** 。</span><span class="sxs-lookup"><span data-stu-id="24921-124">If the alert is **Replication: Subscriber has failed data validation**, you can specify the response job that replication provides for this alert: Select **Execute job**, and then click the browse button (**...**). In the **Locate Job** dialog box, click **Browse**.</span></span> <span data-ttu-id="24921-125">在 **[瀏覽物件]** 對話方塊中，選取 **[重新初始化具有資料驗證失敗的訂閱]** 。</span><span class="sxs-lookup"><span data-stu-id="24921-125">In the **Browse for Objects** dialog box, select **Reinitialize subscriptions having data validation failures**.</span></span> <span data-ttu-id="24921-126">在兩個開啟的對話方塊中按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="24921-126">Click **OK** in both open dialog boxes.</span></span> <span data-ttu-id="24921-127">執行作業時，它會使用對預存程序的遠端程序呼叫 (RPC) 重新初始化訂閱。</span><span class="sxs-lookup"><span data-stu-id="24921-127">When the job executes, it uses a remote procedure call (RPC) to a stored procedure that reinitializes the subscription.</span></span> <span data-ttu-id="24921-128">如果「發行者」使用遠端「散發者」，則必須定義「發行者」端的遠端伺服器登入，以便建立從「散發者」到「發行者」的 RPC。</span><span class="sxs-lookup"><span data-stu-id="24921-128">If the Publisher uses a remote Distributor, you must define a remote server login at the Publisher, so that the RPC from the Distributor to the Publisher can be made.</span></span>   
    -   <span data-ttu-id="24921-129">在 **[選項]** 頁面上，自訂回應的文字。</span><span class="sxs-lookup"><span data-stu-id="24921-129">On the **Options** page, customize the text of the response.</span></span>    
5.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
### <a name="to-configure-an-alert-for-a-threshold-in-replication-monitor"></a><span data-ttu-id="24921-130">若要在複寫監視器中設定臨界值的警示</span><span class="sxs-lookup"><span data-stu-id="24921-130">To configure an alert for a threshold in Replication Monitor</span></span>  
  
1.  <span data-ttu-id="24921-131">在 **[警告]** 索引標籤上，按一下 **[設定警示]** 。</span><span class="sxs-lookup"><span data-stu-id="24921-131">On the **Warnings** tab click **Configure Alerts**.</span></span>    
2.  <span data-ttu-id="24921-132">在 **[設定複寫警示]** 對話方塊中選取一個警示，然後按一下 **[設定]** 。</span><span class="sxs-lookup"><span data-stu-id="24921-132">In the **Configure Replication Alerts** dialog box, select an alert, and then click **Configure**.</span></span>    
3.  <span data-ttu-id="24921-133">在 [\<AlertName> 警示屬性] 對話方塊中設定選項：</span><span class="sxs-lookup"><span data-stu-id="24921-133">Set options in the **\<AlertName> alert properties** dialog box:</span></span>    
    -   <span data-ttu-id="24921-134">在 **[一般]** 頁面上，按一下 **[啟用]** ；指定警示應套用至哪個資料庫。</span><span class="sxs-lookup"><span data-stu-id="24921-134">On the **General** page, click **Enable**; specify which database the alert should apply to.</span></span>    
    -   <span data-ttu-id="24921-135">在 **[回應]** 頁面上，指定是否應傳送電子郵件及 (或) 是否應執行作業。</span><span class="sxs-lookup"><span data-stu-id="24921-135">On the **Response** page, specify whether an e-mail should be sent and/or a job should be executed.</span></span>    
         <span data-ttu-id="24921-136">若警示是**複寫：** 訂閱者資料驗證失敗」，您可以指定複寫為此警示提供的回應作業：選取 [執行作業]，然後按一下瀏覽按鈕 ( **...** )。在 **[尋找作業]** 對話方塊中，按一下 **[瀏覽]** 。</span><span class="sxs-lookup"><span data-stu-id="24921-136">If the alert is **Replication: Subscriber has failed data validation**, you can specify the response job that replication provides for this alert: Select **Execute job**, and then click the browse button (**...**). In the **Locate Job** dialog box, click **Browse**.</span></span> <span data-ttu-id="24921-137">在 **[瀏覽物件]** 對話方塊中，選取 **[重新初始化具有資料驗證失敗的訂閱]** 。</span><span class="sxs-lookup"><span data-stu-id="24921-137">In the **Browse for Objects** dialog box, select **Reinitialize subscriptions having data validation failures**.</span></span> <span data-ttu-id="24921-138">在兩個開啟的對話方塊中按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="24921-138">Click **OK** in both open dialog boxes.</span></span> <span data-ttu-id="24921-139">執行作業時，它會使用對預存程序的遠端程序呼叫 (RPC) 重新初始化訂閱。</span><span class="sxs-lookup"><span data-stu-id="24921-139">When the job executes, it uses a remote procedure call (RPC) to a stored procedure that reinitializes the subscription.</span></span> <span data-ttu-id="24921-140">如果「發行者」使用遠端「散發者」，則必須定義「發行者」端的遠端伺服器登入，以便建立從「散發者」到「發行者」的 RPC。</span><span class="sxs-lookup"><span data-stu-id="24921-140">If the Publisher uses a remote Distributor, you must define a remote server login at the Publisher, so that the RPC from the Distributor to the Publisher can be made.</span></span>   
    -   <span data-ttu-id="24921-141">在 **[選項]** 頁面上，自訂回應的文字。</span><span class="sxs-lookup"><span data-stu-id="24921-141">On the **Options** page, customize the text of the response.</span></span>    
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]    
5.  <span data-ttu-id="24921-142">按一下 [關閉] 。</span><span class="sxs-lookup"><span data-stu-id="24921-142">Click **Close**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24921-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="24921-143">See Also</span></span>  
 [<span data-ttu-id="24921-144">使用針對複寫代理程式事件的警示</span><span class="sxs-lookup"><span data-stu-id="24921-144">Use Alerts for Replication Agent Events</span></span>](../agents/use-alerts-for-replication-agent-events.md)  
  
  
