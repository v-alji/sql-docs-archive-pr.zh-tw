---
title: 查看 Integration Services 服務的事件 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- events [Integration Services]
- service [Integration Services], events
- Integration Services service, events
ms.assetid: 37e23946-10d1-4116-8568-8fd24067102e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a513c8fc917da2987f3619c8eb9011e1170f7dcf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599056"
---
# <a name="view-events-for-the-integration-services-service"></a><span data-ttu-id="646f1-102">檢視 Integration Services 服務的事件</span><span class="sxs-lookup"><span data-stu-id="646f1-102">View Events for the Integration Services Service</span></span>
  <span data-ttu-id="646f1-103">目前有兩個工具可讓您用來檢視 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 服務的事件：</span><span class="sxs-lookup"><span data-stu-id="646f1-103">There are two tools in which you can view events for the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service:</span></span>  
  
-   <span data-ttu-id="646f1-104">**中的** [記錄檔檢視器] [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]對話方塊。</span><span class="sxs-lookup"><span data-stu-id="646f1-104">The **Log File Viewer** dialog box in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="646f1-105">**[記錄檔檢視器]** 對話方塊包括匯出、篩選和搜尋記錄檔的選項。</span><span class="sxs-lookup"><span data-stu-id="646f1-105">The **Log File Viewer** dialog box includes options to export, filter, and search the log.</span></span> <span data-ttu-id="646f1-106">如需 [記錄檔檢視器][**中選項的詳細資訊，請參閱**記錄檔檢視器 F1 說明](../relational-databases/logs/log-file-viewer-f1-help.md)。</span><span class="sxs-lookup"><span data-stu-id="646f1-106">For more information about the options in the **Log File Viewer**, see [Log File Viewer F1 Help](../relational-databases/logs/log-file-viewer-f1-help.md).</span></span>  
  
-   <span data-ttu-id="646f1-107">Windows 事件檢視器。</span><span class="sxs-lookup"><span data-stu-id="646f1-107">The Windows Event Viewer.</span></span>  
  
 <span data-ttu-id="646f1-108">如需 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 服務所記錄之事件的描述，請參閱 [Integration Services 服務所記錄的事件](service/events-logged-by-the-integration-services-service.md)。</span><span class="sxs-lookup"><span data-stu-id="646f1-108">For descriptions of the events logged by the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service, see [Events Logged by the Integration Services Service](service/events-logged-by-the-integration-services-service.md).</span></span>  
  
### <a name="to-view-service-events-for-integration-services-in-sql-server-management-studio"></a><span data-ttu-id="646f1-109">在 SQL Server Management Studio 中檢視 Integration Services 的服務事件</span><span class="sxs-lookup"><span data-stu-id="646f1-109">To view service events for Integration Services in SQL Server Management Studio</span></span>  
  
1.  <span data-ttu-id="646f1-110">開啟 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="646f1-110">Open [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span>  
  
2.  <span data-ttu-id="646f1-111">在 **[檔案]** 功能表上，按一下 **[連接物件總管]**。</span><span class="sxs-lookup"><span data-stu-id="646f1-111">On the **File** menu, click **Connect Object Explorer**.</span></span>  
  
3.  <span data-ttu-id="646f1-112">在 **[連接到伺服器]** 對話方塊中，選取 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 伺服器類型，選取或尋找要連接的伺服器，然後按一下 **[連接]**。</span><span class="sxs-lookup"><span data-stu-id="646f1-112">In the **Connect to Server** dialog box, select the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] server type, select or locate the server to connect to, and then click **Connect**.</span></span>  
  
4.  <span data-ttu-id="646f1-113">在物件總管中，以滑鼠右鍵按一下 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]，然後按一下 [檢視記錄]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="646f1-113">In Object Explorer, right-click [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] and click **View Logs**.</span></span>  
  
5.  <span data-ttu-id="646f1-114">若要檢視 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 事件，請選取 **[SQL Server Integration Services]**。</span><span class="sxs-lookup"><span data-stu-id="646f1-114">To view [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] events, select **SQL Server Integration Services**.</span></span> <span data-ttu-id="646f1-115">**[NT 事件]** 選項會隨 **[SQL Server Integration Services]** 選項的選取和清除而自動選取和清除。</span><span class="sxs-lookup"><span data-stu-id="646f1-115">The **NT Events** option is automatically selected and cleared with the **SQL Server Integration Services** option.</span></span>  
  
### <a name="to-view-service-events-for-integration-services-in-windows-event-viewer"></a><span data-ttu-id="646f1-116">在 Windows 事件檢視器中檢視 Integration Services 的服務事件</span><span class="sxs-lookup"><span data-stu-id="646f1-116">To view service events for Integration Services in Windows Event Viewer</span></span>  
  
1.  <span data-ttu-id="646f1-117">在 **[控制台]** 中，如果您使用「一般檢視」，請按一下 **[系統管理工具]**，如果您使用「類別檢視」，請按一下 **[效能及維護]** ，然後按一下 **[系統管理工具]**。</span><span class="sxs-lookup"><span data-stu-id="646f1-117">In **Control Panel**, if you are using Classic View, click **Administrative Tools**, or, if you are using Category View, click **Performance and Maintenance** and then click **Administrative Tools**.</span></span>  
  
2.  <span data-ttu-id="646f1-118">按一下 **[事件檢視器]**。</span><span class="sxs-lookup"><span data-stu-id="646f1-118">Click **Event Viewer**.</span></span>  
  
3.  <span data-ttu-id="646f1-119">在 **[事件檢視器]** 對話方塊中，按一下 **[應用程式]**。</span><span class="sxs-lookup"><span data-stu-id="646f1-119">In the **Event Viewer** dialog box, click **Application**.</span></span>  
  
4.  <span data-ttu-id="646f1-120">在 [應用程式]\*\*\*\* 嵌入式管理單元中，尋找 [來源]\*\*\*\* 資料行中值為 **SQLISService** 的項目，以滑鼠右鍵按一下該項目，然後按一下 [屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="646f1-120">In the **Application** snap-in, locate an entry in the **Source** column that has the value **SQLISService**, right-click the entry, and then click **Properties**.</span></span>  
  
5.  <span data-ttu-id="646f1-121">選擇性地按一下向上箭頭或向下箭頭，以顯示上一個或下一個事件。</span><span class="sxs-lookup"><span data-stu-id="646f1-121">Optionally, click the up or down arrow to show the previous or next event.</span></span>  
  
6.  <span data-ttu-id="646f1-122">選擇性地按一下 [複製至剪貼簿] 圖示，以複製事件資訊。</span><span class="sxs-lookup"><span data-stu-id="646f1-122">Optionally, click the Copy to Clipboard icon to copy the event information.</span></span>  
  
7.  <span data-ttu-id="646f1-123">選擇使用位元組或文字顯示事件資料。</span><span class="sxs-lookup"><span data-stu-id="646f1-123">Choose to display event data using bytes or words.</span></span>  
  
8.  <span data-ttu-id="646f1-124">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="646f1-124">Click **OK**.</span></span>  
  
9. <span data-ttu-id="646f1-125">在 **[檔案]** 功能表上，按一下 **[結束]** ，以關閉 **[事件檢視器]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="646f1-125">On the **File** menu, click **Exit** to close the **Event Viewer** dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="646f1-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="646f1-126">See Also</span></span>  
 <span data-ttu-id="646f1-127">[管理 Integration Services 服務](../../2014/integration-services/manage-the-integration-services-service.md) </span><span class="sxs-lookup"><span data-stu-id="646f1-127">[Manage the Integration Services Service](../../2014/integration-services/manage-the-integration-services-service.md) </span></span>  
 [<span data-ttu-id="646f1-128">加入資料流程效能計數器的記錄檔</span><span class="sxs-lookup"><span data-stu-id="646f1-128">Add a Log for Data Flow Performance Counters</span></span>](performance/performance-counters.md)  
  
  
