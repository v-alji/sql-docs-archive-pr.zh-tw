---
title: 連接到來源資料 (適用于 Excel) 的資料採礦用戶端 |Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- connections
ms.assetid: 548672ce-e403-4aca-b67a-c2c797f053dd
author: minewiskan
ms.author: owend
ms.openlocfilehash: 4b4759d94043fdccacdf5b285de50697a18965e8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592999"
---
# <a name="connect-to-source-data-data-mining-client-for-excel"></a><span data-ttu-id="6d06e-102">連接到來源資料 (適用於 Excel 的資料採礦用戶端)</span><span class="sxs-lookup"><span data-stu-id="6d06e-102">Connect to Source Data (Data Mining Client for Excel)</span></span>
  <span data-ttu-id="6d06e-103">本主題將說明如何建立和使用用於儲存資料採礦模型的連接，以及用於存取 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 中儲存之外部資料的連接。</span><span class="sxs-lookup"><span data-stu-id="6d06e-103">This topic describes how to create and use connections used for storing data mining models, and for accessing external data stored in [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="6d06e-104">**資料採礦連接。**</span><span class="sxs-lookup"><span data-stu-id="6d06e-104">**Data mining connections.**</span></span> <span data-ttu-id="6d06e-105">在您啟動增益集時建立的初始連接是用於存取演算法、分析資料，以及儲存採礦結構和模型。</span><span class="sxs-lookup"><span data-stu-id="6d06e-105">The initial connection that you create when you start the add-ins is used to access algorithms, analyze data, and store mining structure and models.</span></span>  
  
 <span data-ttu-id="6d06e-106">[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 執行個體的連接是在增益集中使用模型和視覺效果工具的必要條件，因為這些增益集相依於 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 所提供的演算法和資料結構。</span><span class="sxs-lookup"><span data-stu-id="6d06e-106">A connection to an instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] is required to use the modeling and visualization tools in the add-ins, because the add-ins depend on algorithms and data structures that are provided by [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="6d06e-107">**外部資料來源的連接。**</span><span class="sxs-lookup"><span data-stu-id="6d06e-107">**Connections to external data sources.**</span></span> <span data-ttu-id="6d06e-108">您也可以在建立模型或儲存結果時建立外部資料的連接。</span><span class="sxs-lookup"><span data-stu-id="6d06e-108">You can also create connections to external data as you are building models or saving the results.</span></span> <span data-ttu-id="6d06e-109">例如，您可以在某個伺服器上建立資料採礦模型，然後使用另一個 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 執行個體、Excel 資料表或 [!INCLUDE[msCoName](../includes/msconame-md.md)] Access 之類的外部資料來源中儲存之資料，對資料採礦模型執行預測查詢。</span><span class="sxs-lookup"><span data-stu-id="6d06e-109">For example, you can create a data mining model on one server, and then perform a prediction query against the data mining model by using data stored in another instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], in an Excel data table, or in an external data source such as [!INCLUDE[msCoName](../includes/msconame-md.md)] Access.</span></span> <span data-ttu-id="6d06e-110">每次您存取新的資料來源時，系統都會提示您使用對話方塊來建立連接。</span><span class="sxs-lookup"><span data-stu-id="6d06e-110">Each time that you access a new data source, you will be prompted to create a connection by using a dialog box.</span></span>  
  
##  <a name="prerequisites"></a><a name="bkmk_prereq2"></a> <span data-ttu-id="6d06e-111">必要條件</span><span class="sxs-lookup"><span data-stu-id="6d06e-111">Prerequisites</span></span>  
 <span data-ttu-id="6d06e-112">此版本的增益集需要 SQL Server 2012 的 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="6d06e-112">This version of the add-ins requires that your instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] be SQL Server 2012.</span></span> <span data-ttu-id="6d06e-113">如果您要連接到舊版的 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]，則可以使用增益集的另一個版本。</span><span class="sxs-lookup"><span data-stu-id="6d06e-113">A separate version of the add-ins is available if you want to connect to an earlier version of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="6d06e-114">目前有其他支援 SQL Server 2005、SQL Server 2008 和 SQL Server 2008 R2 的增益集版本。</span><span class="sxs-lookup"><span data-stu-id="6d06e-114">There are versions of the add-ins that support SQL Server 2005, SQL Server 2008, and SQL Server 2008 R2.</span></span>  
  
 <span data-ttu-id="6d06e-115">若要連接到 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 資料庫，您必須擁有存取資料庫伺服器的權限。</span><span class="sxs-lookup"><span data-stu-id="6d06e-115">To connect to an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database, you must have permissions to access the database server.</span></span> <span data-ttu-id="6d06e-116">而且，資料採礦工作階段必須已啟用，您也必須有伺服器上儲存之資料庫物件的讀取或讀取/寫入權限。</span><span class="sxs-lookup"><span data-stu-id="6d06e-116">Moreover, data mining sessions must be enabled, and you must have read or read/write permissions on database objects stored on the server.</span></span>  
  
##  <a name="creating-data-mining-server-connections"></a><a name="bkmk_connect"></a><span data-ttu-id="6d06e-117">建立資料採礦伺服器連接</span><span class="sxs-lookup"><span data-stu-id="6d06e-117">Creating Data Mining Server Connections</span></span>  
 <span data-ttu-id="6d06e-118">適用于 Excel 的資料採礦用戶端和適用于 Excel 的資料表分析工具中的 [**連接**] 群組會提供工具來管理實例的連接 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="6d06e-118">The **Connections** group in the Data Mining Client for Excel and the Table Analysis Tools for Excel provides tools for managing connections to an instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="6d06e-119">您可以在安裝增益集時建立連接，或稍後新增連接。</span><span class="sxs-lookup"><span data-stu-id="6d06e-119">You can create the connection when you install the add-in, or you can add a connection later.</span></span>  
  
-   <span data-ttu-id="6d06e-120">除非您正在進行建立或查詢模型的程序，否則可以建立多個連接，並且隨時變更連接。</span><span class="sxs-lookup"><span data-stu-id="6d06e-120">You can create multiple connections, and change connections at any time, unless you are in the process of creating or querying a model.</span></span>  
  
     <span data-ttu-id="6d06e-121">在處理資料採礦模型時，不要變更或關閉連接。</span><span class="sxs-lookup"><span data-stu-id="6d06e-121">Do not change or close a connection when a data mining model is being processed.</span></span> <span data-ttu-id="6d06e-122">資料採礦模型可能會遺失資料，或模型可能會變成無法使用。</span><span class="sxs-lookup"><span data-stu-id="6d06e-122">The data mining model might lose data, or the model might become unusable.</span></span>  
  
-   <span data-ttu-id="6d06e-123">一次只能有一個作用中的連接。</span><span class="sxs-lookup"><span data-stu-id="6d06e-123">Only one connection can be active at a particular time.</span></span>  
  
### <a name="connections-in-the-excel-add-ins"></a><span data-ttu-id="6d06e-124">Excel 增益集的連接</span><span class="sxs-lookup"><span data-stu-id="6d06e-124">Connections in the Excel Add-ins</span></span>  
 <span data-ttu-id="6d06e-125">適用于 Excel 的資料採礦用戶端和適用于 Excel 的資料表分析工具中的 [**連接**] 群組，可讓您管理實例的連接 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="6d06e-125">The **Connections** group in the Data Mining Client for Excel and the Table Analysis Tools for Excel is where you manage connections to an instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span>  
  
##### <a name="create-a-new-server-connection-in-the-excel-add-ins"></a><span data-ttu-id="6d06e-126">在 Excel 增益集中建立新的伺服器連接</span><span class="sxs-lookup"><span data-stu-id="6d06e-126">Create a new server connection in the Excel add-ins</span></span>  
  
1.  <span data-ttu-id="6d06e-127">按一下 [**分析**] 或 [**資料採礦**] 功能區上的 [**連接**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="6d06e-127">Click the **Connection** button on the **Analyze** or **Data Mining** ribbon.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="6d06e-128">按鈕的文字表示連接是否存在。</span><span class="sxs-lookup"><span data-stu-id="6d06e-128">The text of the button indicates if a connection exists.</span></span> <span data-ttu-id="6d06e-129">在工作表中未進行任何連接時，按鈕會包含 " \<No connection> ." 文字。如果先前已在活頁簿中建立連接，該連接的名稱就會出現在按鈕中。</span><span class="sxs-lookup"><span data-stu-id="6d06e-129">When no connection has been made in the worksheet, the button contains the text "\<No connection>." If a connection was previously made in the workbook, the name of that connection appears in the button.</span></span>  
  
2.  <span data-ttu-id="6d06e-130">在 [ **Analysis Services 連接**] 對話方塊中，按一下 [**新增**]。</span><span class="sxs-lookup"><span data-stu-id="6d06e-130">In the **Analysis Services Connections** dialog box, click **New**.</span></span>  
  
3.  <span data-ttu-id="6d06e-131">在 [**新增 Analysis Services 連接**] 對話方塊中，輸入伺服器的名稱。</span><span class="sxs-lookup"><span data-stu-id="6d06e-131">In the **New Analysis Services Connection** dialog box, type the name of the server.</span></span>  
  
4.  <span data-ttu-id="6d06e-132">指定驗證方法。</span><span class="sxs-lookup"><span data-stu-id="6d06e-132">Specify the authentication method.</span></span>  
  
5.  <span data-ttu-id="6d06e-133">從 [**目錄名稱**] 下拉式清單中選取資料庫。</span><span class="sxs-lookup"><span data-stu-id="6d06e-133">Select a database from the **Catalog name** drop-down list.</span></span> <span data-ttu-id="6d06e-134">如果實例上沒有資料庫存在，請選取\*\* (預設) \*\*。</span><span class="sxs-lookup"><span data-stu-id="6d06e-134">If no database exists on the instance, select **(default)**.</span></span>  
  
6.  <span data-ttu-id="6d06e-135">輸入連接的易記名稱。</span><span class="sxs-lookup"><span data-stu-id="6d06e-135">Type a friendly name for the connection.</span></span>  
  
7.  <span data-ttu-id="6d06e-136">按一下 [**測試連接**]，確認伺服器和資料庫可供使用。</span><span class="sxs-lookup"><span data-stu-id="6d06e-136">Click **Test Connection** to verify that the server and database are available.</span></span>  
  
8.  <span data-ttu-id="6d06e-137">按一下 **[確定]** ，然後按一下 **[關閉]** 。</span><span class="sxs-lookup"><span data-stu-id="6d06e-137">Click **OK**, and then click **Close**.</span></span>  
  
### <a name="connections-using-a-web-service"></a><span data-ttu-id="6d06e-138">使用 Web 服務的連接</span><span class="sxs-lookup"><span data-stu-id="6d06e-138">Connections using a Web Service</span></span>  
 <span data-ttu-id="6d06e-139">如果您要使用精簡型用戶端架構來啟用 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Cube 和資料的瀏覽，也可以透過 Web 服務設定 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 伺服器的連接。</span><span class="sxs-lookup"><span data-stu-id="6d06e-139">If you are using a thin-client architecture to enable browsing of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] cubes and data, you can also configure a connection to an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] server through Web services.</span></span> <span data-ttu-id="6d06e-140">如需有關如何定義網路架構用戶端的詳細資訊，請參閱《[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 線上叢書》。</span><span class="sxs-lookup"><span data-stu-id="6d06e-140">For information about how to define a Web-based client, see [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
 <span data-ttu-id="6d06e-141">如果您可以存取已針對 Web 服務設定的伺服器，當您初次建立連接時可以指定連接類型。</span><span class="sxs-lookup"><span data-stu-id="6d06e-141">If you have access to a server that has been configured for Web services, you can specify the connection type when you first create the connection.</span></span>  
  
##### <a name="create-an-http-connection-to-analysis-services"></a><span data-ttu-id="6d06e-142">建立 Analysis Services 的 HTTP 連接</span><span class="sxs-lookup"><span data-stu-id="6d06e-142">Create an HTTP connection to Analysis Services</span></span>  
  
1.  <span data-ttu-id="6d06e-143">開啟 [**新增 Analysis Services 連接**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="6d06e-143">Open the **New Analysis Services Connection** dialog box.</span></span>  
  
2.  <span data-ttu-id="6d06e-144">對於伺服器名稱，請輸入 http://，後面接著指派給 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 伺服器的 URL。</span><span class="sxs-lookup"><span data-stu-id="6d06e-144">For the server name, type http:// followed by the URL assigned to the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] server.</span></span>  
  
3.  <span data-ttu-id="6d06e-145">輸入存取 Web 服務所需的使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="6d06e-145">Type the user name and the password that is required to access the Web service.</span></span>  
  
### <a name="connections-in-the-visio-add-in"></a><span data-ttu-id="6d06e-146">Visio 增益集的連接</span><span class="sxs-lookup"><span data-stu-id="6d06e-146">Connections in the Visio Add-In</span></span>  
 <span data-ttu-id="6d06e-147">不同於 Excel，Visio 沒有提供工具功能區，而且沒有特別用於建立或監視連接的按鈕。</span><span class="sxs-lookup"><span data-stu-id="6d06e-147">Unlike Excel, Visio does not provide a tool ribbon, and there are no buttons specifically for creating or monitoring connections.</span></span> <span data-ttu-id="6d06e-148">但在您初次選取資料採礦圖形並將它放入 Visio 頁面時，就會建立資料連接。</span><span class="sxs-lookup"><span data-stu-id="6d06e-148">Instead, the data connection is created when you first select a data mining shape and drop it onto a Visio page.</span></span> <span data-ttu-id="6d06e-149">精靈會提示您選取圖形的模型以及設定其他選項。</span><span class="sxs-lookup"><span data-stu-id="6d06e-149">A wizard will prompt you to select the model for the shape and to set other options.</span></span>  
  
 <span data-ttu-id="6d06e-150">如果您先前已在 Excel 中使用 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 資料來源的連接，這些連接會列為可從中選取的可能資料來源。</span><span class="sxs-lookup"><span data-stu-id="6d06e-150">If you have previously used a connection to an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] data source in Excel, these connections are listed as possible data sources from which to select.</span></span>  
  
##### <a name="create-a-connection-for-a-visio-shape"></a><span data-ttu-id="6d06e-151">建立 Visio 圖形的連接</span><span class="sxs-lookup"><span data-stu-id="6d06e-151">Create a connection for a Visio shape</span></span>  
  
1.  <span data-ttu-id="6d06e-152">開啟資料採礦範本，然後選取其中一個資料採礦圖形。</span><span class="sxs-lookup"><span data-stu-id="6d06e-152">Open the Data Mining Template, and select one of the data mining shapes.</span></span>  
  
2.  <span data-ttu-id="6d06e-153">將圖形拖放至空白頁面上。</span><span class="sxs-lookup"><span data-stu-id="6d06e-153">Drag and drop the shape to a blank page.</span></span>  
  
3.  <span data-ttu-id="6d06e-154">在 [**選取資料來源**] 對話方塊中，從清單中選取資料來源，或按一下 [**新增**]。</span><span class="sxs-lookup"><span data-stu-id="6d06e-154">In the **Select a data source** dialog box, select a data source from the list, or click **New**.</span></span>  
  
4.  <span data-ttu-id="6d06e-155">如果您選取 [**新增**]，請遵循先前所述的程式來指定伺服器和目錄名稱，或透過 Web 服務進行連接。</span><span class="sxs-lookup"><span data-stu-id="6d06e-155">If you select **New**, follow the procedure that is described earlier to specify a server and catalog name, or to connect through a Web service.</span></span>  
  
##  <a name="changing-connections"></a><a name="bkmk_change"></a><span data-ttu-id="6d06e-156">變更連接</span><span class="sxs-lookup"><span data-stu-id="6d06e-156">Changing Connections</span></span>  
 <span data-ttu-id="6d06e-157">您可以在相同工作表中建立多個連接，但每次只能有一個作用中的連接。</span><span class="sxs-lookup"><span data-stu-id="6d06e-157">You can create multiple connections in the same worksheet, but only one connection can be active at a time.</span></span> <span data-ttu-id="6d06e-158">目前連接的名稱會顯示在 [**連接**] 按鈕中。</span><span class="sxs-lookup"><span data-stu-id="6d06e-158">The name of the current connection is displayed in the **Connection** button.</span></span>  
  
 <span data-ttu-id="6d06e-159">在適用于 Excel 的資料採礦用戶端中，您也可以按一下 [**追蹤**]，然後按一下 [**目前連接**]，以確認目前連接的連接字串和狀態。</span><span class="sxs-lookup"><span data-stu-id="6d06e-159">In the Data Mining Client for Excel, you can also verify the connection string and status for the current connection by clicking **Trace** and then clicking **Current Connection**.</span></span>  
  
#### <a name="use-a-different-server-connection"></a><span data-ttu-id="6d06e-160">使用不同的伺服器連接</span><span class="sxs-lookup"><span data-stu-id="6d06e-160">Use a different server connection</span></span>  
  
1.  <span data-ttu-id="6d06e-161">按一下 [**連接**]。</span><span class="sxs-lookup"><span data-stu-id="6d06e-161">Click **Connection**.</span></span>  
  
2.  <span data-ttu-id="6d06e-162">在 [ **Analysis Services**連線] 窗格中，從 [**其他**連線] 清單中選取一個連接，然後按一下 [**設為目前**的]。</span><span class="sxs-lookup"><span data-stu-id="6d06e-162">In the **Analysis Services Connections** pane, select a connection from the **Other Connections** list, and click **Make Current**.</span></span>  
  
3.  <span data-ttu-id="6d06e-163">按一下 [**測試連接**] 以確認連接可以使用。</span><span class="sxs-lookup"><span data-stu-id="6d06e-163">Click **Test Connection** to verify that the connection is available.</span></span>  
  
 <span data-ttu-id="6d06e-164">在採礦模型完成處理之後，會在本機儲存結果，如果您關閉與某個伺服器的連接，然後連接到另一個伺服器，這對資料沒有影響。</span><span class="sxs-lookup"><span data-stu-id="6d06e-164">After a mining model has finished processing, the results are stored locally, and there is no effect on the data if you close the connection to one server and then connect to another server.</span></span> <span data-ttu-id="6d06e-165">不過，您應避免在處理資料採礦模型時變更連接或中斷連接，因為這可能會損毀資料。</span><span class="sxs-lookup"><span data-stu-id="6d06e-165">However, you should avoid changing connections or losing the connection when a data mining model is being processed, because this could corrupt data.</span></span>  
  
#### <a name="modify-an-existing-server-connection"></a><span data-ttu-id="6d06e-166">修改現有的伺服器連接</span><span class="sxs-lookup"><span data-stu-id="6d06e-166">Modify an existing server connection</span></span>  
  
1.  <span data-ttu-id="6d06e-167">您無法修改現有的連接。如果您想要連接到不同的資料庫或不同的伺服器，就應該建立新的連接。</span><span class="sxs-lookup"><span data-stu-id="6d06e-167">You cannot modify an existing connection; if you want to connect to a different database or a different server, you should create a new connection.</span></span>  
  
2.  <span data-ttu-id="6d06e-168">如果您必須修改連接字串以增加查詢逾時或加入 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 執行個體特有的其他參數，其中一個選項就是編輯儲存連接字串的 .dmc 檔案。</span><span class="sxs-lookup"><span data-stu-id="6d06e-168">If you must modify the connection string to increase the query timeout or add other parameters specific to your instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], one option is to edit the .dmc file, where the connection string is stored.</span></span>  
  
     <span data-ttu-id="6d06e-169">\<drive:>\Users \\<myusername \> \AppData\Local\Microsoft\Data 的挖掘增益集</span><span class="sxs-lookup"><span data-stu-id="6d06e-169">\<drive:>\Users\\<myusername\>\AppData\Local\Microsoft\Data Mining Add-in</span></span>  
  
##  <a name="connecting-to-external-data-sources"></a><a name="bkmk_extconnections"></a><span data-ttu-id="6d06e-170">連接到外部資料源</span><span class="sxs-lookup"><span data-stu-id="6d06e-170">Connecting to External Data Sources</span></span>  
 <span data-ttu-id="6d06e-171">[**分析**] 功能區中的工具僅適用于 Excel 中的資料，而 [**資料採礦**] 功能區中的工具可讓您直接連接到外部資料源，做為模型的輸入或進行取樣。</span><span class="sxs-lookup"><span data-stu-id="6d06e-171">Whereas the tools in the **Analyze** ribbon work exclusively with data in Excel, the tools in the **Data Mining** ribbon let you connect directly to external data sources to use as inputs for your model, or for sampling.</span></span>  
  
 <span data-ttu-id="6d06e-172">這些增益集中的下列工具支援使用外部資料進行資料採礦：</span><span class="sxs-lookup"><span data-stu-id="6d06e-172">The following tools in these add-ins support use of external data for data mining:</span></span>  
  
-   [<span data-ttu-id="6d06e-173">SQL Server 資料採礦增益集的範例資料 &#40;&#41;</span><span class="sxs-lookup"><span data-stu-id="6d06e-173">Sample Data &#40;SQL Server Data Mining Add-ins&#41;</span></span>](sample-data-sql-server-data-mining-add-ins.md)  
  
-   [<span data-ttu-id="6d06e-174">適用于 Excel 的資料採礦增益集&#41;的分類嚮導 &#40;</span><span class="sxs-lookup"><span data-stu-id="6d06e-174">Classify Wizard &#40;Data Mining Add-ins for Excel&#41;</span></span>](classify-wizard-data-mining-add-ins-for-excel.md)  
  
-   [<span data-ttu-id="6d06e-175">評估 Wizard &#40;適用于 Excel 的資料採礦增益集&#41;</span><span class="sxs-lookup"><span data-stu-id="6d06e-175">Estimate Wizard &#40;Data Mining Add-ins for Excel&#41;</span></span>](estimate-wizard-data-mining-add-ins-for-excel.md)  
  
-   [<span data-ttu-id="6d06e-176">叢集 Wizard &#40;適用于 Excel 的資料採礦增益集&#41;</span><span class="sxs-lookup"><span data-stu-id="6d06e-176">Cluster Wizard &#40;Data Mining Add-ins for Excel&#41;</span></span>](cluster-wizard-data-mining-add-ins-for-excel.md)  
  
-   [<span data-ttu-id="6d06e-177">&#40;適用于 Excel 的資料採礦增益集&#41;的預測 Wizard</span><span class="sxs-lookup"><span data-stu-id="6d06e-177">Forecast Wizard &#40;Data Mining Add-ins for Excel&#41;</span></span>](forecast-wizard-data-mining-add-ins-for-excel.md)  
  
-   [<span data-ttu-id="6d06e-178">建立 &#40;SQL Server 資料採礦增益集的採礦結構&#41;</span><span class="sxs-lookup"><span data-stu-id="6d06e-178">Create Mining Structure &#40;SQL Server Data Mining Add-ins&#41;</span></span>](create-mining-structure-sql-server-data-mining-add-ins.md)  
  
-   [<span data-ttu-id="6d06e-179">精確度圖表 &#40;SQL Server 資料採礦增益集&#41;</span><span class="sxs-lookup"><span data-stu-id="6d06e-179">Accuracy Chart &#40;SQL Server Data Mining Add-ins&#41;</span></span>](accuracy-chart-sql-server-data-mining-add-ins.md)  
  
-   [<span data-ttu-id="6d06e-180">收益圖 &#40;SQL Server 資料採礦增益集&#41;</span><span class="sxs-lookup"><span data-stu-id="6d06e-180">Profit Chart &#40;SQL Server Data Mining Add-ins&#41;</span></span>](profit-chart-sql-server-data-mining-add-ins.md)  
  
-   [<span data-ttu-id="6d06e-181">SQL Server 資料採礦增益集的分類矩陣 &#40;&#41;</span><span class="sxs-lookup"><span data-stu-id="6d06e-181">Classification Matrix &#40;SQL Server Data Mining Add-ins&#41;</span></span>](classification-matrix-sql-server-data-mining-add-ins.md)  
  
### <a name="using-analysis-services-as-a-data-source"></a><span data-ttu-id="6d06e-182">使用 Analysis Services 做為資料來源</span><span class="sxs-lookup"><span data-stu-id="6d06e-182">Using Analysis Services as a Data Source</span></span>  
 <span data-ttu-id="6d06e-183">您無法直接存取儲存在 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Cube 或表格式模型中的資料。</span><span class="sxs-lookup"><span data-stu-id="6d06e-183">You cannot directly access data stored in an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] cube or tabular model.</span></span> <span data-ttu-id="6d06e-184">請改在 Excel 中建立 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 伺服器的連接，然後使用資料來建立模型。</span><span class="sxs-lookup"><span data-stu-id="6d06e-184">Instead, create a connection in Excel to the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] server, and use the data to create a model.</span></span>  
  
### <a name="relational-data-sources"></a><span data-ttu-id="6d06e-185">關聯式資料來源</span><span class="sxs-lookup"><span data-stu-id="6d06e-185">Relational Data Sources</span></span>  
 <span data-ttu-id="6d06e-186">如果您想要使用關聯式來源中的資料做為模型的輸入，可以連接到下列 SQL Server 版本：</span><span class="sxs-lookup"><span data-stu-id="6d06e-186">If you want to use data from a relational source as input to your model, you can connect to the following versions of SQL Server:</span></span>  
  
-   <span data-ttu-id="6d06e-187">SQL Server 2008</span><span class="sxs-lookup"><span data-stu-id="6d06e-187">SQL Server 2008</span></span>  
  
-   <span data-ttu-id="6d06e-188">SQL Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="6d06e-188">SQL Server 2008 R2</span></span>  
  
-   <span data-ttu-id="6d06e-189">SQL Server 2012</span><span class="sxs-lookup"><span data-stu-id="6d06e-189">SQL Server 2012</span></span>  
  
 <span data-ttu-id="6d06e-190">您也可以從 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 支援當做資料來源使用的任何其他關聯式資料來源取得資料。</span><span class="sxs-lookup"><span data-stu-id="6d06e-190">You can also get data from any other relational data source that is supported as a data source by [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="6d06e-191">如需支援的資料來源的詳細資訊，請參閱多[維度模型中的資料來源](multidimensional-models/data-sources-in-multidimensional-models.md)</span><span class="sxs-lookup"><span data-stu-id="6d06e-191">For information about supported data sources, see [Data Sources in Multidimensional Models](multidimensional-models/data-sources-in-multidimensional-models.md)</span></span>  
  
 <span data-ttu-id="6d06e-192">請注意，下列資料類型無法用於資料採礦，而且如果您在建立模型時加入這些資料類型，將會產生錯誤：</span><span class="sxs-lookup"><span data-stu-id="6d06e-192">Note that the following data types cannot be used for data mining and will result in an error if included when you build a model:</span></span>  
  
-   <span data-ttu-id="6d06e-193">ntext</span><span class="sxs-lookup"><span data-stu-id="6d06e-193">ntext</span></span>  
  
-   <span data-ttu-id="6d06e-194">BINARY</span><span class="sxs-lookup"><span data-stu-id="6d06e-194">binary</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d06e-195">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6d06e-195">See Also</span></span>  
 [<span data-ttu-id="6d06e-196">適用于 Excel&#41;的追蹤 &#40;資料採礦用戶端</span><span class="sxs-lookup"><span data-stu-id="6d06e-196">Trace &#40;Data Mining Client for Excel&#41;</span></span>](trace-data-mining-client-for-excel.md)  
  
  
