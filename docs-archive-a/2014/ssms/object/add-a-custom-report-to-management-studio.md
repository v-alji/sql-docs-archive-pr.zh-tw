---
title: 將自訂報表加入 Management Studio | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Management Studio [SQL Server], custom reports
ms.assetid: 3cf8d726-0a90-4f80-98d0-352a2a59be0f
author: stevestein
ms.author: sstein
ms.openlocfilehash: 07263edfb9b255257e0c79733c2c34b279b61cd3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584263"
---
# <a name="add-a-custom-report-to-management-studio"></a><span data-ttu-id="2689d-102">將自訂報表加入 Management Studio</span><span class="sxs-lookup"><span data-stu-id="2689d-102">Add a Custom Report to Management Studio</span></span>
  <span data-ttu-id="2689d-103">本主題描述如何建立儲存為 .rdl 檔案的簡單 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 報表，然後將該 rdl 檔案加入至 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 做為自訂報表。</span><span class="sxs-lookup"><span data-stu-id="2689d-103">This topic describes how to create a simple [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] report that is saved as an .rdl file, and then add that rdl file to [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] as a custom report.</span></span> [!INCLUDE[ssRS](../../includes/ssrs.md)] <span data-ttu-id="2689d-104">可以建立多種精密報表。</span><span class="sxs-lookup"><span data-stu-id="2689d-104">can create a wide variety of sophisticated reports.</span></span> <span data-ttu-id="2689d-105">若要使用本主題來建立報表，您必須先在電腦上安裝 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="2689d-105">To create a report by using this topic, you must have [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] installed on the computer.</span></span> <span data-ttu-id="2689d-106">您不需要在 [!INCLUDE[ssRS](../../includes/ssrs.md)] 上安裝 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，即可使用 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]執行自訂報表。</span><span class="sxs-lookup"><span data-stu-id="2689d-106">You do not have to install [!INCLUDE[ssRS](../../includes/ssrs.md)] on [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to run a custom report using [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].</span></span>  
  
  
### <a name="to-create-a-simple-report-saved-as-an-rdl-file"></a><span data-ttu-id="2689d-107">建立儲存成 .rdl 檔的簡單報表</span><span class="sxs-lookup"><span data-stu-id="2689d-107">To create a simple report saved as an .rdl file</span></span>  
  
1.  <span data-ttu-id="2689d-108">按一下 [開始]  、依序指向 [程式集]  和 [Microsoft SQL Server]  ，然後按一下 [SQL Server Data Tools]  。</span><span class="sxs-lookup"><span data-stu-id="2689d-108">Click **Start**, point to **Programs**, point to **Microsoft SQL Server**, and then click **SQL Server Data Tools**.</span></span>  
  
2.  <span data-ttu-id="2689d-109">在 **[檔案]** 功能表上，指向 **[開新檔案]** ，然後按一下 **[專案]** 。</span><span class="sxs-lookup"><span data-stu-id="2689d-109">On the **File** menu, point to **New**, and then click **Project**.</span></span>  
  
3.  <span data-ttu-id="2689d-110">在 **[專案類型]** 清單中，按一下 **[商業智慧專案]** 。</span><span class="sxs-lookup"><span data-stu-id="2689d-110">In the **Project Types** list, click **Business Intelligence Projects**.</span></span>  
  
4.  <span data-ttu-id="2689d-111">在 [範本]  清單中，按一下 [報表伺服器專案精靈]  。</span><span class="sxs-lookup"><span data-stu-id="2689d-111">In the **Templates** list, click **Report Server Project Wizard**.</span></span>  
  
5.  <span data-ttu-id="2689d-112">在 [名稱]  中，輸入 **ConnectionsReport**，然後按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="2689d-112">In **Name**, type **ConnectionsReport**, and then click **OK**.</span></span>  
  
6.  <span data-ttu-id="2689d-113">在 [報表精靈]  簡介頁面中，按一下 [下一步]  。</span><span class="sxs-lookup"><span data-stu-id="2689d-113">On the **Report Wizard** introduction page, click **Next**.</span></span>  
  
7.  <span data-ttu-id="2689d-114">在 [選取資料來源]  頁面的 [名稱] 方塊中，為 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 的這個連接輸入名稱，然後按一下 [編輯]  。</span><span class="sxs-lookup"><span data-stu-id="2689d-114">On the **Select the Data Source** page, in the Name box type a name for this connection to your [!INCLUDE[ssDE](../../includes/ssde-md.md)], and then click **Edit**.</span></span>  
  
8.  <span data-ttu-id="2689d-115">在 [連接屬性]  對話方塊的 [伺服器名稱]  方塊中，輸入您的 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 執行個體名稱。</span><span class="sxs-lookup"><span data-stu-id="2689d-115">In the **Connection Properties** dialog box, in the **Server name** box, type the name of your instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
9. <span data-ttu-id="2689d-116">在 [請選取或輸入資料庫名稱]  方塊中，輸入 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 上任何資料庫的名稱 (例如 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)])，然後按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="2689d-116">In the **Select or enter a database name** box, type the name of any database on your [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], such as [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)], and then click **OK**.</span></span>  
  
10. <span data-ttu-id="2689d-117">在 [選取資料來源]  頁面上，按一下 [下一步]  。</span><span class="sxs-lookup"><span data-stu-id="2689d-117">On the **Select the Data Source** page, click **Next**.</span></span>  
  
11. <span data-ttu-id="2689d-118">在 [設計查詢]  頁面的 [查詢字串]  方塊中，輸入下列 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式 (可列出 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 的目前連接)，然後按一下 [下一步]  。</span><span class="sxs-lookup"><span data-stu-id="2689d-118">On the **Design the Query** page, in the **Query string** box, type the following [!INCLUDE[tsql](../../includes/tsql-md.md)] statement that lists the current connections to your [!INCLUDE[ssDE](../../includes/ssde-md.md)], and then click **Next**.</span></span> <span data-ttu-id="2689d-119">[報表精靈] 的 [查詢字串] 方塊無法接受報表參數。</span><span class="sxs-lookup"><span data-stu-id="2689d-119">The Report Wizard Query string box will not accept report parameters.</span></span> <span data-ttu-id="2689d-120">您必須手動建立更複雜的自訂報表。</span><span class="sxs-lookup"><span data-stu-id="2689d-120">More complex custom reports must be created manually.</span></span>  
  
     `SELECT session_id, net_transport FROM sys.dm_exec_connections;`  
  
12. <span data-ttu-id="2689d-121">在 [選取報表類型]\*\*\*\* 頁面上，選取 [表格式]\*\*\*\*，然後按一下 [完成]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="2689d-121">On the **Select the Report Type** page, select **Tabular**, and then click **Finish**.</span></span>  
  
13. <span data-ttu-id="2689d-122">在 [正在完成精靈]\*\*\*\* 頁面的 [報表名稱]\*\*\*\* 方塊中，輸入 **ConnectionsReport**，然後按一下 [完成]\*\*\*\* 建立並儲存報表。</span><span class="sxs-lookup"><span data-stu-id="2689d-122">On the **Completing the Wizard** page, in the **Report name** box, type **ConnectionsReport**, and then click **Finish** to create and save the report.</span></span>  
  
14. <span data-ttu-id="2689d-123">關閉 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="2689d-123">Close [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)].</span></span>  
  
15. <span data-ttu-id="2689d-124">將 **ConnectionsReport.rdl** 複製到您在資料庫伺服器上針對自訂報表所建立資料夾。</span><span class="sxs-lookup"><span data-stu-id="2689d-124">Copy **ConnectionsReport.rdl** to a folder that you created on the database server for custom reports.</span></span>  
  
### <a name="to-add-a-report-to-management-studio"></a><span data-ttu-id="2689d-125">將報表加入至 Management Studio</span><span class="sxs-lookup"><span data-stu-id="2689d-125">To add a report to Management Studio</span></span>  
  
-   <span data-ttu-id="2689d-126">在 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 中，以滑鼠右鍵按一下物件總管中的節點、指向 [報表]\*\*\*\*，然後按一下 [自訂報表]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="2689d-126">In [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], right-click a node in Object Explorer, point to **Reports**, click **Custom Reports**.</span></span> <span data-ttu-id="2689d-127">在 [開啟檔案]\*\*\*\* 對話方塊中，找到自訂報表資料夾，並選取 **ConnectionsReport.rdl** 檔案，然後按一下 [開啟]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="2689d-127">In the **Open File** dialog box, locate the custom reports folder and select the **ConnectionsReport.rdl** file, and then click **Open**.</span></span>  
  
     <span data-ttu-id="2689d-128">第一次從物件總管節點開啟新的自訂報表時，該報表會新增到該節點的快速鍵功能表中，[自訂報表]\*\*\*\* 下之最近使用的清單中。</span><span class="sxs-lookup"><span data-stu-id="2689d-128">When a new custom report is first opened from an Object Explorer node, the custom report is added to the most recently used list under **Custom Reports** on the shortcut menu of that node.</span></span> <span data-ttu-id="2689d-129">第一次開啟標準報表時，該報表也會顯示在 [自訂報表]\*\*\*\* 下之最近使用的清單中。</span><span class="sxs-lookup"><span data-stu-id="2689d-129">When a standard report is opened for the first time, it will also appear on the most recently used list under **Custom Reports**.</span></span> <span data-ttu-id="2689d-130">如果您刪除了某個自訂報表檔，下次選取該項目時，系統就會提示您是否要從最近使用清單中刪除該項目。</span><span class="sxs-lookup"><span data-stu-id="2689d-130">If a custom report file is deleted, the next time that the item is selected, a prompt will appear to delete the item from the most recently used list.</span></span>  
  
    1.  <span data-ttu-id="2689d-131">若要變更最近使用清單中可顯示的檔案數目，請在 [工具]\*\*\*\* 功能表中，按一下 [選項]\*\*\*\*、展開 [環境]\*\*\*\* 資料夾，然後按一下 [一般]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="2689d-131">To change the number of files that are displayed on the recently used list, on the **Tools** menu, click **Options,** expand the **Environment** folder, and then click **General**.</span></span>  
  
    2.  <span data-ttu-id="2689d-132">調整 [顯示在最近使用的清單中的檔案數]\*\*\*\* 中的數目。</span><span class="sxs-lookup"><span data-stu-id="2689d-132">Adjust the number for **Display files in recently used list**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2689d-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2689d-133">See Also</span></span>  
 <span data-ttu-id="2689d-134">[Management Studio 中的自訂報表](custom-reports-in-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="2689d-134">[Custom Reports in Management Studio](custom-reports-in-management-studio.md) </span></span>  
 <span data-ttu-id="2689d-135">[使用具有物件總管節點屬性的自訂報表](use-custom-reports-with-object-explorer-node-properties.md) </span><span class="sxs-lookup"><span data-stu-id="2689d-135">[Use Custom Reports with Object Explorer Node Properties](use-custom-reports-with-object-explorer-node-properties.md) </span></span>  
 <span data-ttu-id="2689d-136">[取消隱藏執行自訂報表警告](unsuppress-run-custom-report-warnings.md) </span><span class="sxs-lookup"><span data-stu-id="2689d-136">[Unsuppress Run Custom Report Warnings](unsuppress-run-custom-report-warnings.md) </span></span>  
 [<span data-ttu-id="2689d-137">Reporting Services &#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="2689d-137">Reporting Services &#40;SSRS&#41;</span></span>](../../reporting-services/create-deploy-and-manage-mobile-and-paginated-reports.md)  
  
  
