---
title: 啟用 SQL Server Data Tools 中的封裝記錄 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- logs [Integration Services], enabling
ms.assetid: b69a8593-5bb0-4f04-87d2-f8e7bd7eb4fc
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d73dbca034047e853669dd503a62e105d1dd7b45
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596815"
---
# <a name="enable-package-logging-in-sql-server-data-tools"></a><span data-ttu-id="34b04-102">在 SQL Server Data Tools 中啟用封裝記錄功能</span><span class="sxs-lookup"><span data-stu-id="34b04-102">Enable Package Logging in SQL Server Data Tools</span></span>
  <span data-ttu-id="34b04-103">本程序描述如何將記錄檔加入封裝、設定封裝層級的記錄，以及將記錄組態儲存至 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="34b04-103">This procedure describes how to add logs to a package, configure package-level logging, and save the logging configuration to an XML file.</span></span> <span data-ttu-id="34b04-104">您可以僅在封裝層級加入記錄檔，但封裝無需執行記錄即可啟用封裝所包含之容器中的記錄。</span><span class="sxs-lookup"><span data-stu-id="34b04-104">You can add logs only at the package level, but the package does not have to perform logging to enable logging in the containers that the package includes.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="34b04-105">如果您將 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 專案部署到 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 伺服器，則您為封裝執行設定的記錄層次會覆寫您使用 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]設定的封裝記錄。</span><span class="sxs-lookup"><span data-stu-id="34b04-105">If you deploy the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project to the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] server, the logging level that you set for the package execution overrides the package logging that you configure using [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="34b04-106">依預設，封裝中的容器使用與其父容器相同的記錄組態。</span><span class="sxs-lookup"><span data-stu-id="34b04-106">By default, the containers in the package use the same logging configuration as their parent container.</span></span> <span data-ttu-id="34b04-107">如需設定個別容器之記錄選項的資訊，請參閱 [使用已儲存的組態檔來設定記錄](../../2014/integration-services/configure-logging-by-using-a-saved-configuration-file.md)。</span><span class="sxs-lookup"><span data-stu-id="34b04-107">For information about setting logging options for individual containers, see [Configure Logging by Using a Saved Configuration File](../../2014/integration-services/configure-logging-by-using-a-saved-configuration-file.md).</span></span>  
  
### <a name="to-enable-logging-in-a-package"></a><span data-ttu-id="34b04-108">若要啟用封裝中的記錄</span><span class="sxs-lookup"><span data-stu-id="34b04-108">To enable logging in a package</span></span>  
  
1.  <span data-ttu-id="34b04-109">在 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]中，開啟包含所需封裝的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 專案。</span><span class="sxs-lookup"><span data-stu-id="34b04-109">In [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="34b04-110">在 **[SSIS]** 功能表上，按一下 **[記錄]** 。</span><span class="sxs-lookup"><span data-stu-id="34b04-110">On the **SSIS** menu, click **Logging**.</span></span>  
  
3.  <span data-ttu-id="34b04-111">在 [提供者類型]  清單中選取記錄提供者，然後按一下 [加入]  。</span><span class="sxs-lookup"><span data-stu-id="34b04-111">Select a log provider in the **Provider type** list, and then click **Add**.</span></span>  
  
4.  <span data-ttu-id="34b04-112">在 [組態] 資料行中，選取連線管理員，或按一下 **\<New connection>** ，為記錄提供者建立適當類型的新連線管理員。</span><span class="sxs-lookup"><span data-stu-id="34b04-112">In the **Configuration** column, select a connection manager or click **\<New connection>** to create a new connection manager of the appropriate type for the log provider.</span></span> <span data-ttu-id="34b04-113">因所選提供者的不同，使用下列連接管理員之一：</span><span class="sxs-lookup"><span data-stu-id="34b04-113">Depending on the selected provider, use one of the following connection managers:</span></span>  
  
    -   <span data-ttu-id="34b04-114">若為「文字」檔案，請使用「檔案」連接管理員。</span><span class="sxs-lookup"><span data-stu-id="34b04-114">For Text files, use a File connection manager.</span></span> <span data-ttu-id="34b04-115">如需詳細資訊，請參閱 [檔案連線管理員](connection-manager/file-connection-manager.md)</span><span class="sxs-lookup"><span data-stu-id="34b04-115">For more information, see [File Connection Manager](connection-manager/file-connection-manager.md)</span></span>  
  
    -   <span data-ttu-id="34b04-116">若為 [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)]，請使用檔案連線管理員。</span><span class="sxs-lookup"><span data-stu-id="34b04-116">For [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)], use a File connection manager.</span></span>  
  
    -   <span data-ttu-id="34b04-117">若為 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]，請使用 OLE DB 連接管理員。</span><span class="sxs-lookup"><span data-stu-id="34b04-117">For [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], use an OLE DB connection manager.</span></span> <span data-ttu-id="34b04-118">如需相關資訊，請參閱 [OLE DB Connection Manager](connection-manager/ole-db-connection-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="34b04-118">For more information, see [OLE DB Connection Manager](connection-manager/ole-db-connection-manager.md).</span></span>  
  
    -   <span data-ttu-id="34b04-119">若為 Windows 事件記錄檔，不需任何動作。</span><span class="sxs-lookup"><span data-stu-id="34b04-119">For Windows Event Log, do nothing.</span></span> [!INCLUDE[ssIS](../includes/ssis-md.md)] <span data-ttu-id="34b04-120">會自動建立記錄檔。</span><span class="sxs-lookup"><span data-stu-id="34b04-120">automatically creates the log.</span></span>  
  
    -   <span data-ttu-id="34b04-121">若為 XML 檔案，請使用「檔案」連接管理員。</span><span class="sxs-lookup"><span data-stu-id="34b04-121">For XML files, use a File connection manager.</span></span>  
  
5.  <span data-ttu-id="34b04-122">針對封裝中要使用的每個記錄檔重複步驟 3 和 4。</span><span class="sxs-lookup"><span data-stu-id="34b04-122">Repeat steps 3 and 4 for each log to use in the package.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="34b04-123">封裝可以使用每種類型一個以上的記錄檔。</span><span class="sxs-lookup"><span data-stu-id="34b04-123">A package can use more than one log of each type.</span></span>  
  
6.  <span data-ttu-id="34b04-124">選擇性地選取封裝層級核取方塊，並選取要用於封裝層級記錄的記錄檔，然後按一下 [詳細資料]  索引標籤。</span><span class="sxs-lookup"><span data-stu-id="34b04-124">Optionally, select the package-level check box, select the logs to use for package-level logging, and then click the **Details** tab.</span></span>  
  
7.  <span data-ttu-id="34b04-125">在 [詳細資料]  索引標籤上，選取 [事件]  ，以記錄所有記錄項目，或清除 [事件]  ，以選取個別事件。</span><span class="sxs-lookup"><span data-stu-id="34b04-125">On the **Details** tab, select **Events** to log all log entries, or clear **Events** to select individual events.</span></span>  
  
8.  <span data-ttu-id="34b04-126">選擇性地按一下 [進階]  ，以指定要記錄哪些資訊。</span><span class="sxs-lookup"><span data-stu-id="34b04-126">Optionally, click **Advanced** to specify which information to log.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="34b04-127">依預設，會記錄所有資訊。</span><span class="sxs-lookup"><span data-stu-id="34b04-127">By default, all information is logged.</span></span>  
  
9. <span data-ttu-id="34b04-128">在 [詳細資料]  索引標籤上，按一下 [儲存]  。</span><span class="sxs-lookup"><span data-stu-id="34b04-128">On the **Details** tab, click **Save.**</span></span> <span data-ttu-id="34b04-129">[另存新檔]  對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="34b04-129">The **Save As** dialog box appears.</span></span> <span data-ttu-id="34b04-130">尋找要儲存記錄組態的資料夾，輸入新記錄組態的檔案名稱，然後按一下 [儲存]  。</span><span class="sxs-lookup"><span data-stu-id="34b04-130">Locate the folder in which to save the logging configuration, type a file name for the new log configuration, and then click **Save**.</span></span>  
  
10. <span data-ttu-id="34b04-131">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="34b04-131">Click **OK**.</span></span>  
  
11. <span data-ttu-id="34b04-132">若要儲存已更新的封裝，請在 **[檔案]** 功能表上，按一下 **[儲存選取項目]** 。</span><span class="sxs-lookup"><span data-stu-id="34b04-132">To save the updated package, click **Save Selected Items** on the **File** menu.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34b04-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="34b04-133">See Also</span></span>  
 <span data-ttu-id="34b04-134">[Integration Services &#40;SSIS&#41; 記錄](performance/integration-services-ssis-logging.md) </span><span class="sxs-lookup"><span data-stu-id="34b04-134">[Integration Services &#40;SSIS&#41; Logging](performance/integration-services-ssis-logging.md) </span></span>  
 [<span data-ttu-id="34b04-135">Integration Services &#40;SSIS&#41; 記錄</span><span class="sxs-lookup"><span data-stu-id="34b04-135">Integration Services &#40;SSIS&#41; Logging</span></span>](performance/integration-services-ssis-logging.md)  
  
  
