---
title: 連接到資料採礦伺服器 |Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- connections
- getting started
ms.assetid: 85962ad6-d840-4bc6-905e-c667c3276944
author: minewiskan
ms.author: owend
ms.openlocfilehash: 528dee62e9074b0d9df6668182c04282500639e5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593034"
---
# <a name="connect-to-a-data-mining-server"></a><span data-ttu-id="52bbd-102">連接到資料採礦伺服器</span><span class="sxs-lookup"><span data-stu-id="52bbd-102">Connect to a Data Mining Server</span></span>
  <span data-ttu-id="52bbd-103">![連接按鈕](media/misc-connection.gif "連接按鈕")</span><span class="sxs-lookup"><span data-stu-id="52bbd-103">![Connections button](media/misc-connection.gif "Connections button")</span></span>  
  
 <span data-ttu-id="52bbd-104">按一下 [**連接**] 按鈕，以選取現有的連接，或建立與實例的新連接 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="52bbd-104">Click the **Connection** button to select an existing connection, or to create a new connection to an instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="52bbd-105">**為什麼需要連接到伺服器？**</span><span class="sxs-lookup"><span data-stu-id="52bbd-105">**Why do I need to connect to a server?**</span></span>  
  
 <span data-ttu-id="52bbd-106">當您建立連接時，便能讓您使用 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 伺服器所提供的資料採礦演算法，以及利用伺服器的最佳化處理。</span><span class="sxs-lookup"><span data-stu-id="52bbd-106">When you create a connection, it enables you to use the data mining algorithms that are provided by the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] server, and to take advantage of the optimized processing of the server.</span></span>  
  
 <span data-ttu-id="52bbd-107">您並不需要將資料或結果保存在 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 資料庫，或是 SQL Server 資料庫中。</span><span class="sxs-lookup"><span data-stu-id="52bbd-107">You do not have to keep your data or your results in an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database, or in a SQL Server database.</span></span> <span data-ttu-id="52bbd-108">Excel 資料採礦增益集只能和儲存在 Excel 中的資料搭配使用，或是和您以 Excel 資料來源的方式所連接的資料搭配使用。</span><span class="sxs-lookup"><span data-stu-id="52bbd-108">The Excel data mining add-ins can work with data stored only in Excel, or data that you connect to as an Excel data source.</span></span>  
  
## <a name="how-to-create-a-new-connection"></a><span data-ttu-id="52bbd-109">如何建立新的連接</span><span class="sxs-lookup"><span data-stu-id="52bbd-109">How to Create a New Connection</span></span>  
  
1.  <span data-ttu-id="52bbd-110">按一下 [**連接**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="52bbd-110">Click the **Connection** button.</span></span>  
  
2.  <span data-ttu-id="52bbd-111">在 [ **Analysis Services 連接**] 對話方塊中，按一下 [**新增**]。</span><span class="sxs-lookup"><span data-stu-id="52bbd-111">In the **Analysis Services Connections** dialog box, click **New**.</span></span>  
  
3.  <span data-ttu-id="52bbd-112">在 [**連接到 Analysis Services** ] 對話方塊中，輸入伺服器名稱。</span><span class="sxs-lookup"><span data-stu-id="52bbd-112">In the **Connect to Analysis Services** dialog box, type a server name.</span></span>  
  
4.  <span data-ttu-id="52bbd-113">指定驗證方法。</span><span class="sxs-lookup"><span data-stu-id="52bbd-113">Specify the authentication method.</span></span>  
  
5.  <span data-ttu-id="52bbd-114">指定將在其中存放資料採礦模型的目錄或 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 資料庫。</span><span class="sxs-lookup"><span data-stu-id="52bbd-114">Specify the catalog, or [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database, where you will store your data mining models.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="52bbd-115">如果您尚未建立任何資料庫，則可以使用 (預設值) 建立連接再加以測試；不過，您不能將採礦模型加入至預設連接。</span><span class="sxs-lookup"><span data-stu-id="52bbd-115">If you have not created any databases yet, you can use (default) to create and then test the connection; however, you cannot add mining models to the default connection.</span></span> <span data-ttu-id="52bbd-116">在建立任何採礦模型之前，應該先與現有的資料庫建立連接。</span><span class="sxs-lookup"><span data-stu-id="52bbd-116">Before you create any mining models, you should create a connection to an existing database.</span></span>  
  
6.  <span data-ttu-id="52bbd-117">如果您是透過 Web 服務連接到伺服器，請輸入 Web 服務所需要的使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="52bbd-117">If you are connecting to the server via a Web service, type the user name and password required by the Web service.</span></span>  
  
7.  <span data-ttu-id="52bbd-118">輸入新連接的易記名稱。</span><span class="sxs-lookup"><span data-stu-id="52bbd-118">Type a friendly name for the new connection.</span></span>  
  
8.  <span data-ttu-id="52bbd-119">按一下 [**測試連接**]，確認伺服器可供使用。</span><span class="sxs-lookup"><span data-stu-id="52bbd-119">Click **Test Connection** to verify that the server is available.</span></span>  
  
## <a name="troubleshooting-connections"></a><span data-ttu-id="52bbd-120">疑難排解連接</span><span class="sxs-lookup"><span data-stu-id="52bbd-120">Troubleshooting Connections</span></span>  
 <span data-ttu-id="52bbd-121">本節將提供有關連接到 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 的一些常見問題的解答。</span><span class="sxs-lookup"><span data-stu-id="52bbd-121">This section provides answers to some common questions about connections to [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="52bbd-122">**我收到一則訊息，指出「找不到連接」。**</span><span class="sxs-lookup"><span data-stu-id="52bbd-122">**I get a message saying "No connection found."**</span></span>  
  
 <span data-ttu-id="52bbd-123">如果按鈕下半部的文字顯示 [**沒有連接**]，表示您沒有建立資料庫的連接 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ，或連接失敗。</span><span class="sxs-lookup"><span data-stu-id="52bbd-123">If the text in the lower part of the button says **No Connection**, it means that you have not created a connection to an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database, or that the connection failed.</span></span> <span data-ttu-id="52bbd-124">您可以繼續從 Access 或其他來源使用 Excel 中的資料，但是若要建立資料採礦模型或執行預測查詢，便必須要有使用中的連接。</span><span class="sxs-lookup"><span data-stu-id="52bbd-124">You can continue to work with data in Excel from Access or other sources, but to create a data mining model or run a prediction query you must have an active connection.</span></span>  
  
 <span data-ttu-id="52bbd-125">**假設我沒有使用伺服器的許可權嗎？**</span><span class="sxs-lookup"><span data-stu-id="52bbd-125">**Suppose I don't have permission to use the server?**</span></span>  
  
 <span data-ttu-id="52bbd-126">如果您沒有足夠的權限將採礦模型存放在伺服器上，或是想要對資料採礦進行實驗而不要儲存工作，則可以使用資料表分析工具建立暫時性資料結構和暫時性模型。</span><span class="sxs-lookup"><span data-stu-id="52bbd-126">If you do not have sufficient permissions to store your mining models on the server, or if you want to experiment with data mining and not save your work, you can use the Table Analysis Tools, which create temporary data structures and temporary models.</span></span> <span data-ttu-id="52bbd-127">您仍然需要能夠將暫時性模型存放在伺服器上。</span><span class="sxs-lookup"><span data-stu-id="52bbd-127">You still need to be able to store temporary models on the server.</span></span> <span data-ttu-id="52bbd-128">請要求您的系統管理員啟用伺服器上的*會話採礦模型*使用。</span><span class="sxs-lookup"><span data-stu-id="52bbd-128">Ask your administrator to enable use of *session mining models* on the server.</span></span>  
  
 <span data-ttu-id="52bbd-129">若要確保儲存您的模型，您可以將使用暫時性模型的選項停用，或者也可使用資料採礦用戶端所提供的精靈。</span><span class="sxs-lookup"><span data-stu-id="52bbd-129">If you want to ensure that your models are saved, you can disable the option to use temporary models, or you can use the wizards in the Data Mining Client.</span></span> <span data-ttu-id="52bbd-130">這些精靈會將所有模型儲存在伺服器上。</span><span class="sxs-lookup"><span data-stu-id="52bbd-130">These wizards store all models on the server.</span></span> <span data-ttu-id="52bbd-131">您需要對儲存模型的資料庫具備系統管理存取權，因此建議您請系統管理員為使用增益集所建立的採礦模型建立一個專用的資料庫。</span><span class="sxs-lookup"><span data-stu-id="52bbd-131">You will need administrative access to the database where the models are stored, so we recommend that you get the administrator to create a database especially for creating mining models with the add-ins.</span></span>  
  
 <span data-ttu-id="52bbd-132">**我的連接中斷了，這樣是否會遺失我所有的工作成果？**</span><span class="sxs-lookup"><span data-stu-id="52bbd-132">**I lost my connection; did I lose all my work?**</span></span>  
  
 <span data-ttu-id="52bbd-133">如果您終止與伺服器的連接，您的結果與資料並不會遺失，因為它們是儲存在 Excel 中。</span><span class="sxs-lookup"><span data-stu-id="52bbd-133">If you terminate the connection to the server, your results and data will not be lost, because they are stored in Excel.</span></span> <span data-ttu-id="52bbd-134">不過，如果您建立了一些暫時性模型，則過不久後就會從伺服器中刪除這些模型。</span><span class="sxs-lookup"><span data-stu-id="52bbd-134">However, if you created some temporary models, those models will be deleted from the server after a short time.</span></span> <span data-ttu-id="52bbd-135">因此，如果您暫時失去連線，就不會刪除模型。</span><span class="sxs-lookup"><span data-stu-id="52bbd-135">So if you lose the connection temporarily, sometime the models won't be deleted yet.</span></span>  
  
 <span data-ttu-id="52bbd-136">任何產生的資料或結果都不會遺失，因為所有報表和資料表都是儲存在 Excel 中。</span><span class="sxs-lookup"><span data-stu-id="52bbd-136">Any data or results that were generated will not be lost, because all reports and tables are stored in Excel.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="52bbd-137">當增益集與 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 伺服器進行通訊時，請勿中斷與伺服器或網路的連接。</span><span class="sxs-lookup"><span data-stu-id="52bbd-137">Do not disconnect from the server or from the network while the add-in is communicating with the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] server.</span></span> <span data-ttu-id="52bbd-138">例如，絕不要在建立模型或處理資料時中斷連接。</span><span class="sxs-lookup"><span data-stu-id="52bbd-138">For example, never disconnect when a model is being created, or when the data is being processed.</span></span> <span data-ttu-id="52bbd-139">在某些情況下，您的資料可能會因而損毀。</span><span class="sxs-lookup"><span data-stu-id="52bbd-139">In some situations your data could be corrupted.</span></span>  
  
 <span data-ttu-id="52bbd-140">**我無法使用 Visio 工具連接到模型**</span><span class="sxs-lookup"><span data-stu-id="52bbd-140">**I cannot connect to the model using the Visio tools**</span></span>  
  
 <span data-ttu-id="52bbd-141">適用於 Visio 的資料採礦範本無法使用暫存採礦結構和模型。</span><span class="sxs-lookup"><span data-stu-id="52bbd-141">The Data Mining Templates for Visio cannot use temporary mining structures and models.</span></span> <span data-ttu-id="52bbd-142">若要建立採礦模型的圖表，此模型必須存放在伺服器上。</span><span class="sxs-lookup"><span data-stu-id="52bbd-142">To create a diagram of a mining model, the model must be stored on a server.</span></span>  
  
 <span data-ttu-id="52bbd-143">**如何監視連接的使用方式？**</span><span class="sxs-lookup"><span data-stu-id="52bbd-143">**How can I monitor usage of the connection?**</span></span>  
  
 <span data-ttu-id="52bbd-144">[適用于 Excel&#41;工具 &#40;資料採礦用戶端的追蹤](trace-data-mining-client-for-excel.md)會在增益集與指定的伺服器之間建立所有活動的記錄檔。</span><span class="sxs-lookup"><span data-stu-id="52bbd-144">The [Trace &#40;Data Mining Client for Excel&#41;](trace-data-mining-client-for-excel.md) tool creates a log of all activity between the add-ins and the specified server.</span></span>  
  
 <span data-ttu-id="52bbd-145">若要啟用會話模型的監視，請在 [**追蹤**] 對話方塊中選取 [**使用會話模型**] 選項。</span><span class="sxs-lookup"><span data-stu-id="52bbd-145">To enable monitoring of session models, select the **Use session models** option in the **Tracer** dialog box.</span></span>  
  
 <span data-ttu-id="52bbd-146">追蹤可讓您檢視模型和結構建立時所產生的 DMX 和 XMLA 命令。</span><span class="sxs-lookup"><span data-stu-id="52bbd-146">The trace lets you view the DMX and XMLA commands generated while models and structures are being created.</span></span> <span data-ttu-id="52bbd-147">您也可以檢視用戶端所傳送的查詢，藉此在 Excel 中產生結果和報表。</span><span class="sxs-lookup"><span data-stu-id="52bbd-147">You can also view the queries that are sent by the client to generate results and reports in Excel.</span></span>  
  
 <span data-ttu-id="52bbd-148">**什麼是暫時性模型？如何儲存暫時性模型？**</span><span class="sxs-lookup"><span data-stu-id="52bbd-148">**What is a temporary model? How can I save a temporary model?**</span></span>  
  
 <span data-ttu-id="52bbd-149">適用於 Excel 的資料表分析工具預設會建立暫時性資料結構和採礦模型。</span><span class="sxs-lookup"><span data-stu-id="52bbd-149">The Table Analysis Tools for Excel by default creates temporary data structures and mining models.</span></span> <span data-ttu-id="52bbd-150">只要將活頁簿保持開啟，而且不中斷與 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 的連接，就可以繼續瀏覽及查詢暫時性模型。</span><span class="sxs-lookup"><span data-stu-id="52bbd-150">You can continue to browse and query temporary models as long as you keep the workbook open and do not disconnect from [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="52bbd-151">如果關閉 Excel 活頁簿或變更或是結束與 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 的連接，您所建立的結構與模型就會遭到刪除。</span><span class="sxs-lookup"><span data-stu-id="52bbd-151">The structures and models that you have created will be deleted as soon as you close the Excel workbook, or if you change or end your connection to [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="52bbd-152">當您完成適用於 Excel 的資料採礦用戶端所提供的精靈時，模型預設會儲存至伺服器，但在每個精靈的最後一頁都會有可讓您使用暫時性模型的選項。</span><span class="sxs-lookup"><span data-stu-id="52bbd-152">When you complete a wizard in the Data Mining Client for Excel, models are saved to the server by default, but on the final page of each wizard there is the option to use a temporary model.</span></span> <span data-ttu-id="52bbd-153">如果選取了這個選項，您所建立的資料採礦結構和模型都會存放在暫存檔中。</span><span class="sxs-lookup"><span data-stu-id="52bbd-153">If you select this option, the data mining structure and model that you created are stored in a temporary file.</span></span> <span data-ttu-id="52bbd-154">只要 Excel 維持開啟狀態，您就能夠瀏覽、管理及修改結構與模型。</span><span class="sxs-lookup"><span data-stu-id="52bbd-154">You can browse, manage, and modify the structure and model as long as Excel remains open.</span></span> <span data-ttu-id="52bbd-155">但是，一旦您關閉 Excel 後，結構和所有相關的模型便會遭到刪除。</span><span class="sxs-lookup"><span data-stu-id="52bbd-155">However, once you close Excel, the structure and any related models are deleted.</span></span>  
  
 <span data-ttu-id="52bbd-156">您也可以使用 [**資料採礦] [高級查詢編輯器**]，並選取其中一個 DMX 範本，以明確建立暫存結構或模型。</span><span class="sxs-lookup"><span data-stu-id="52bbd-156">You can also explicitly create a temporary structure or model by using the **Data Mining Advanced Query Editor** and selecting one of the DMX templates.</span></span> <span data-ttu-id="52bbd-157">加入 `USE SESSION MODELS` 子句以指定物件是暫時性的。</span><span class="sxs-lookup"><span data-stu-id="52bbd-157">Add the `USE SESSION MODELS` clause to specify that objects be temporary.</span></span>   
  
### <a name="creating-backups-of-mining-models-and-structures"></a><span data-ttu-id="52bbd-158">建立採礦模型和結構的備份</span><span class="sxs-lookup"><span data-stu-id="52bbd-158">Creating Backups of Mining Models and Structures</span></span>  
 <span data-ttu-id="52bbd-159">若要建立模型或結構的備份，您可以在適用于 Excel 的資料採礦用戶端中，使用 [[管理模型] &#40;SQL Server 資料採礦增益集&#41;](manage-models-sql-server-data-mining-add-ins.md)進行匯出。</span><span class="sxs-lookup"><span data-stu-id="52bbd-159">To create a backup of a model or structure, you can export it by using [Manage Models &#40;SQL Server Data Mining Add-ins&#41;](manage-models-sql-server-data-mining-add-ins.md), in the Data Mining Client for Excel.</span></span>  
  
 <span data-ttu-id="52bbd-160">如果您建立的是暫時性採礦模型，它通常會有一個很難理解的名稱，例如 Table5_593679_TS_62446。</span><span class="sxs-lookup"><span data-stu-id="52bbd-160">If you created a temporary mining model, it typically has a name that is difficult to understand, such as Table5_593679_TS_62446.</span></span> <span data-ttu-id="52bbd-161">不過，您可以使用[追蹤 &#40;適用于 Excel 的資料採礦用戶端&#41;](trace-data-mining-client-for-excel.md)工具來探索資料表分析工具所建立之暫存結構和模型的名稱，然後使用 [**管理模型**] 加以備份。</span><span class="sxs-lookup"><span data-stu-id="52bbd-161">However, you can use the [Trace &#40;Data Mining Client for Excel&#41;](trace-data-mining-client-for-excel.md) tool to discover the names of temporary structures and models that were created by the Table Analysis Tools and then back them up using **Manage Models**.</span></span>  
  
##### <a name="identify-and-export-a-temporary-model"></a><span data-ttu-id="52bbd-162">識別及匯出暫時性模型</span><span class="sxs-lookup"><span data-stu-id="52bbd-162">Identify and export a temporary model</span></span>  
  
1.  <span data-ttu-id="52bbd-163">在適用于 Excel 的資料採礦用戶端的 [**連接**] 群組中，按一下 [**追蹤**]。</span><span class="sxs-lookup"><span data-stu-id="52bbd-163">In the **Connections** group of the Data Mining Client for Excel, click **Trace**.</span></span>  
  
2.  <span data-ttu-id="52bbd-164">檢視連接活動記錄檔，並透過檢閱資料行和可預測的輸出找出模型 (舉例來說)。</span><span class="sxs-lookup"><span data-stu-id="52bbd-164">View the connection activity log, and locate the model by reviewing the columns and predictable outputs (for example).</span></span>  
  
     <span data-ttu-id="52bbd-165">進階使用者：如果您很熟悉 DMX 或 XMLA，可以將陳述式複製到檔案以供稍後使用。</span><span class="sxs-lookup"><span data-stu-id="52bbd-165">Advanced users: If you are familiar with DMX or XMLA, you can copy the statements to a file for later use.</span></span>  
  
3.  <span data-ttu-id="52bbd-166">當您找到暫時模型和結構的名稱時，請開啟 [**管理模型**] 並選取模型。</span><span class="sxs-lookup"><span data-stu-id="52bbd-166">When you have found the name of the temporary model and structure, open **Manage Model** and select the model.</span></span>  
  
4.  <span data-ttu-id="52bbd-167">按一下 [匯出這個採礦模型]，在您指定的位置產生指令碼檔案。</span><span class="sxs-lookup"><span data-stu-id="52bbd-167">Click Export this mining model to generate a script file in a location you specify.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52bbd-168">另請參閱</span><span class="sxs-lookup"><span data-stu-id="52bbd-168">See Also</span></span>  
 <span data-ttu-id="52bbd-169">[連接到來源資料 &#40;適用于 Excel 的資料採礦用戶端&#41;](connect-to-source-data-data-mining-client-for-excel.md) </span><span class="sxs-lookup"><span data-stu-id="52bbd-169">[Connect to Source Data &#40;Data Mining Client for Excel&#41;](connect-to-source-data-data-mining-client-for-excel.md) </span></span>  
 [<span data-ttu-id="52bbd-170">伺服器設定公用程式 &#40;適用于 Excel 的資料採礦增益集&#41;</span><span class="sxs-lookup"><span data-stu-id="52bbd-170">Server Configuration Utility &#40;Data Mining Add-ins for Excel&#41;</span></span>](server-configuration-utility-data-mining-add-ins-for-excel.md)  
  
  
