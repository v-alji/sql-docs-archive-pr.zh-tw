---
title: 為數據流效能計數器新增記錄 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- performance counters [Integration Services]
- counters [Integration Services]
- logs [Integration Services], data flow counters
ms.assetid: b500d166-33ba-4b82-a92d-b0a333924e8d
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 489bde1b0e5769f05d1063eb0af2376b659574de
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705361"
---
# <a name="add-a-log-for-data-flow-performance-counters"></a><span data-ttu-id="e6d49-102">加入資料流程效能計數器的記錄檔</span><span class="sxs-lookup"><span data-stu-id="e6d49-102">Add a Log for Data Flow Performance Counters</span></span>
  <span data-ttu-id="e6d49-103">此程序描述如何加入資料流程引擎提供之效能計數器的記錄檔。</span><span class="sxs-lookup"><span data-stu-id="e6d49-103">This procedure describes how to add a log for the performance counters that the data flow engine provides.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e6d49-104">：如果您在執行 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 的電腦上安裝 [!INCLUDE[winxpsvr](../includes/winxpsvr-md.md)]，然後將該電腦升級到 [!INCLUDE[firstref_longhorn](../includes/firstref-longhorn-md.md)]，則升級程序會從電腦中移除 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 效能計數器。</span><span class="sxs-lookup"><span data-stu-id="e6d49-104">If you install [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] on a computer that is running [!INCLUDE[winxpsvr](../includes/winxpsvr-md.md)], and then upgrade that computer to [!INCLUDE[firstref_longhorn](../includes/firstref-longhorn-md.md)], the upgrade process removes the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] performance counters from the computer.</span></span> <span data-ttu-id="e6d49-105">若要還原電腦上的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 效能計數器，請在修復模式中執行 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 安裝程式。</span><span class="sxs-lookup"><span data-stu-id="e6d49-105">To restore the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] performance counters on the computer, run [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Setup in repair mode.</span></span>  
  
### <a name="to-add-logging-of-performance-counters"></a><span data-ttu-id="e6d49-106">若要加入效能計數器的記錄</span><span class="sxs-lookup"><span data-stu-id="e6d49-106">To add logging of performance counters</span></span>  
  
1.  <span data-ttu-id="e6d49-107">在 [控制台] 中，如果使用傳統檢視，請按一下 [系統管理工具]。</span><span class="sxs-lookup"><span data-stu-id="e6d49-107">In **Control Panel**, if you are using Classic view, click **Administrative Tools**.</span></span> <span data-ttu-id="e6d49-108">如果使用類別檢視，請按一下 [效能及維護]，然後按一下 [系統管理工具]。</span><span class="sxs-lookup"><span data-stu-id="e6d49-108">If you are using Category view, click **Performance and Maintenance** and then click **Administrative Tools**.</span></span>  
  
2.  <span data-ttu-id="e6d49-109">按一下 [效能]。</span><span class="sxs-lookup"><span data-stu-id="e6d49-109">Click **Performance**.</span></span>  
  
3.  <span data-ttu-id="e6d49-110">在 [效能] 對話方塊中，展開 [效能記錄檔及警示]，以滑鼠右鍵按一下 [計數器記錄檔]，然後按一下 [新記錄檔設定]。</span><span class="sxs-lookup"><span data-stu-id="e6d49-110">In the **Performance** dialog box, expand **Performance Logs and Alerts**, right-click **Counter Logs**, and then click **New Log Settings**.</span></span> <span data-ttu-id="e6d49-111">鍵入記錄檔的名稱。</span><span class="sxs-lookup"><span data-stu-id="e6d49-111">Type the name of the log.</span></span> <span data-ttu-id="e6d49-112">例如，輸入 **MyLog**。</span><span class="sxs-lookup"><span data-stu-id="e6d49-112">For example, type **MyLog**.</span></span>  
  
4.  <span data-ttu-id="e6d49-113">按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="e6d49-113">Click **OK**.</span></span>  
  
5.  <span data-ttu-id="e6d49-114">在 [MyLog] 對話方塊中，按一下 [加入計數器]。</span><span class="sxs-lookup"><span data-stu-id="e6d49-114">In the **MyLog** dialog box, click **Add Counters**.</span></span>  
  
6.  <span data-ttu-id="e6d49-115">按一下 [使用本機電腦計數器]，以記錄本機電腦上的效能計數器，或按一下 [從下列電腦選取計數器]，然後從清單選取電腦，以記錄指定之電腦上的效能計數器。</span><span class="sxs-lookup"><span data-stu-id="e6d49-115">Click **Use local computer counters** to log performance counters on the local computer, or click **Select counters from computer** and then select a computer from the list to log performance counters on the specified computer.</span></span>  
  
7.  <span data-ttu-id="e6d49-116">在 [加入計數器] 對話方塊中，選取 [效能物件] 清單中的 [SQL Server:SSIS Pipeline]。</span><span class="sxs-lookup"><span data-stu-id="e6d49-116">In the **Add Counters** dialog box, select **SQL Server:SSIS Pipeline** in the **Performance object** list.</span></span>  
  
8.  <span data-ttu-id="e6d49-117">若要選取效能計數器，請執行下列其中之一：</span><span class="sxs-lookup"><span data-stu-id="e6d49-117">To select performance counters, do one of the following:</span></span>  
  
    -   <span data-ttu-id="e6d49-118">選取 [所有計數器]，以記錄所有效能計數器。</span><span class="sxs-lookup"><span data-stu-id="e6d49-118">Select **All Counters** to log all performance counters.</span></span>  
  
    -   <span data-ttu-id="e6d49-119">選取 [從清單選取計數器]，並選取要使用的效能計數器。</span><span class="sxs-lookup"><span data-stu-id="e6d49-119">Select **Select counters in list** and select the performance counters to use.</span></span>  
  
9. <span data-ttu-id="e6d49-120">按一下 [新增] 。</span><span class="sxs-lookup"><span data-stu-id="e6d49-120">Click **Add**.</span></span>  
  
10. <span data-ttu-id="e6d49-121">按一下 [關閉] 。</span><span class="sxs-lookup"><span data-stu-id="e6d49-121">Click **Close**.</span></span>  
  
11. <span data-ttu-id="e6d49-122">在 [MyLog] 對話方塊中，檢閱 [計數器] 清單中記錄效能計數器的清單。</span><span class="sxs-lookup"><span data-stu-id="e6d49-122">In the **MyLog** dialog box, review the list of logging performance counters in the **Counters** list.</span></span>  
  
12. <span data-ttu-id="e6d49-123">若要加入其他計數器，請重複步驟 5 至 10。</span><span class="sxs-lookup"><span data-stu-id="e6d49-123">To add additional counters, repeat steps 5 through 10.</span></span>  
  
13. <span data-ttu-id="e6d49-124">按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="e6d49-124">Click **OK**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="e6d49-125">您必須使用 Administrators 群組成員的本機帳戶或網域帳戶，啟動「效能記錄檔及警示」服務。</span><span class="sxs-lookup"><span data-stu-id="e6d49-125">You must start the Performance Logs and Alerts service using a local account or a domain account that is a member of the Administrators group.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6d49-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e6d49-126">See Also</span></span>  
 <span data-ttu-id="e6d49-127">[效能計數器](performance/performance-counters.md) </span><span class="sxs-lookup"><span data-stu-id="e6d49-127">[Performance Counters](performance/performance-counters.md) </span></span>  
 [<span data-ttu-id="e6d49-128">檢視記錄事件視窗中的記錄項目</span><span class="sxs-lookup"><span data-stu-id="e6d49-128">View Log Entries in the Log Events Window</span></span>](../../2014/integration-services/view-log-entries-in-the-log-events-window.md)  
  
  
