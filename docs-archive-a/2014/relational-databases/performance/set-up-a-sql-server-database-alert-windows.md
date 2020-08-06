---
title: 設定 SQL Server 資料庫警示 (Windows) | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- alerts [SQL Server], creating
ms.assetid: 65d2c5c1-921f-4eff-9ef7-149170ab61e8
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 090eeda2c134857df18d083ce06d460214aa4dfb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606807"
---
# <a name="set-up-a-sql-server-database-alert-windows"></a><span data-ttu-id="87902-102">設定 SQL Server 資料庫警示 (Windows)</span><span class="sxs-lookup"><span data-stu-id="87902-102">Set Up a SQL Server Database Alert (Windows)</span></span>
  <span data-ttu-id="87902-103">您可以使用「系統監視器」來建立警示，在達到「系統監視器」計數器的臨界值時引發警示。</span><span class="sxs-lookup"><span data-stu-id="87902-103">Using System Monitor, you can create an alert to be raised when a threshold value for a System Monitor counter has been reached.</span></span> <span data-ttu-id="87902-104">為了回應此警示，「系統監視器」可啟動某個應用程式，諸如可處理此警示狀況的自訂應用程式。</span><span class="sxs-lookup"><span data-stu-id="87902-104">In response to the alert, System Monitor can launch an application, such as a custom application written to handle the alert condition.</span></span> <span data-ttu-id="87902-105">例如，您可以建立在死結數目超出特定值時引發的警示。</span><span class="sxs-lookup"><span data-stu-id="87902-105">For example, you can create an alert that is raised when the number of deadlocks exceeds a specific value.</span></span>  
  
 <span data-ttu-id="87902-106">也可以利用 Microsoft [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 和 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 定義警示。</span><span class="sxs-lookup"><span data-stu-id="87902-106">Alerts also can be defined using Microsoft [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.</span></span> <span data-ttu-id="87902-107">如需詳細資訊，請參閱 [警示](../../ssms/agent/alerts.md)。</span><span class="sxs-lookup"><span data-stu-id="87902-107">For more information, see [Alerts](../../ssms/agent/alerts.md).</span></span>  
  
### <a name="to-set-up-a-sql-server-database-alert"></a><span data-ttu-id="87902-108">若要設定 SQL Server 資料庫警示</span><span class="sxs-lookup"><span data-stu-id="87902-108">To set up a SQL Server database alert</span></span>  
  
1.  <span data-ttu-id="87902-109">在 [效能] 視窗的流覽樹狀目錄中，展開 [**效能記錄檔及警示**]。</span><span class="sxs-lookup"><span data-stu-id="87902-109">On the navigation tree of the Performance window, expand **Performance Logs and Alerts**.</span></span>  
  
2.  <span data-ttu-id="87902-110">以滑鼠右鍵按一下 [警示]\*\*\*\*，然後按一下 [New Alert Settings (新增警示設定)]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="87902-110">Right-click **Alerts**, and then click **New Alert Settings**.</span></span>  
  
3.  <span data-ttu-id="87902-111">在 [New Alert Settings (新增警示設定)]\*\*\*\* 對話方塊中，輸入新警示的名稱，然後按一下 [確定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="87902-111">In the **New Alert Settings** dialog box, type a name for the new alert, and then click **OK**.</span></span>  
  
4.  <span data-ttu-id="87902-112">在新警示對話方塊的 [一般]\*\*\*\* 索引標籤上，加入 [註解]\*\*\*\*，按一下 [新增]\*\*\*\* 將計數器加入警示中。</span><span class="sxs-lookup"><span data-stu-id="87902-112">On the **General** tab of the dialog box for the new alert, add a **Comment**, and click **Add** to add a counter to the alert.</span></span>  
  
     <span data-ttu-id="87902-113">所有警示必須至少要有一個計數器。</span><span class="sxs-lookup"><span data-stu-id="87902-113">All alerts must have at least one counter.</span></span>  
  
5.  <span data-ttu-id="87902-114">在 [新增計數器] 對話方塊中，從 [效能物件]\*\*\*\* 清單選取 SQL Server 物件，然後在 [從清單選取計數器]\*\*\*\* 中選取計數器。</span><span class="sxs-lookup"><span data-stu-id="87902-114">In the Add Counters dialog box, select a SQL Server object from the **Performance Object** list, and then select a counter from the **Select counters from list**.</span></span>  
  
6.  <span data-ttu-id="87902-115">若要將計數器加入警示中，請按一下 [新增]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="87902-115">To add the counter to the alert, click **Add**.</span></span> <span data-ttu-id="87902-116">您可以繼續加入計數器，也可以按一下 [關閉]\*\*\*\* 返回新的警示對話方塊。</span><span class="sxs-lookup"><span data-stu-id="87902-116">You can continue to add counters, or you can click **Close** to return to the dialog box for the new alert.</span></span>  
  
7.  <span data-ttu-id="87902-117">在新的警示對話方塊中，與 [Alert when the value is (達到這個值就發出警示)]\*\*\*\* 清單中按一下 [超過]\*\*\*\* 或 [低於]\*\*\*\*，然後在 [限制]\*\*\*\* 中輸入臨界值。</span><span class="sxs-lookup"><span data-stu-id="87902-117">In the new alert dialog box, click either **Over** or **Under**in the **Alert when the value is** list, and then enter a threshold value in **Limit**.</span></span>  
  
     <span data-ttu-id="87902-118">當計數器的值超過或低於臨界值時，就會產生警示 (依據您之前按一下 [超過]\*\*\*\* 或 [低於]\*\*\*\* 而定)。</span><span class="sxs-lookup"><span data-stu-id="87902-118">The alert is generated when the value for the counter is more than or less than the threshold value (depending on whether you clicked **Over** or **Under**).</span></span>  
  
8.  <span data-ttu-id="87902-119">在 [Sample data every (依下列週期進行資料取樣)] 方塊中，設定取樣頻率。</span><span class="sxs-lookup"><span data-stu-id="87902-119">In the **Sample data every** boxes, set the sampling frequency.</span></span>  
  
9. <span data-ttu-id="87902-120">在 [動作] 索引標籤上，設定每次觸發警示時要採取的行動。</span><span class="sxs-lookup"><span data-stu-id="87902-120">On the **Action** tab, set actions to occur every time the alert is triggered.</span></span>  
  
10. <span data-ttu-id="87902-121">在 [排程] 索引標籤上，設定警示掃描的開始與停止排程。</span><span class="sxs-lookup"><span data-stu-id="87902-121">On the **Schedule** tab, set the start and stop schedule for the alert scan.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87902-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="87902-122">See Also</span></span>  
 [<span data-ttu-id="87902-123">建立 SQL Server 資料庫警示</span><span class="sxs-lookup"><span data-stu-id="87902-123">Create a SQL Server Database Alert</span></span>](../performance-monitor/create-a-sql-server-database-alert.md)  
  
  
