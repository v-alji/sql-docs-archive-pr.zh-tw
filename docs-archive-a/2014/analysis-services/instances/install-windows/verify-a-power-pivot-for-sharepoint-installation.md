---
title: 確認 PowerPivot for SharePoint 安裝 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 855bd055-5ad3-493f-9c5b-1f5297b2e6e2
author: minewiskan
ms.author: owend
ms.openlocfilehash: 0f45e1aa1d48dd5a50b7ce38dc364089d438f215
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598047"
---
# <a name="verify-a-powerpivot-for-sharepoint-installation"></a><span data-ttu-id="db7c0-102">確認 PowerPivot for SharePoint 安裝</span><span class="sxs-lookup"><span data-stu-id="db7c0-102">Verify a PowerPivot for SharePoint Installation</span></span>
  <span data-ttu-id="db7c0-103">您在 SharePoint 伺服器陣列中安裝的 PowerPivot for SharePoint 執行個體是透過 SharePoint 管理中心來進行管理。</span><span class="sxs-lookup"><span data-stu-id="db7c0-103">A PowerPivot for SharePoint instance that you install in a SharePoint farm is administered through SharePoint Central Administration.</span></span> <span data-ttu-id="db7c0-104">您至少可以檢查管理中心和 SharePoint 網站上的頁面，以確認 PowerPivot 伺服器元件和功能是可用的。</span><span class="sxs-lookup"><span data-stu-id="db7c0-104">At a minimum, you can check pages in Central Administration and on SharePoint sites to verify that PowerPivot server components and features are available.</span></span> <span data-ttu-id="db7c0-105">但是，為了完整確認安裝作業，您必須擁有可以發行到 SharePoint 並從文件庫存取的 PowerPivot 活頁簿。</span><span class="sxs-lookup"><span data-stu-id="db7c0-105">However, to fully verify an installation, you must have a PowerPivot workbook that you can publish to SharePoint and access from a library.</span></span> <span data-ttu-id="db7c0-106">為了測試用途，您可以發行已經包含 PowerPivot 資料的範例活頁簿，並用它來確認 SharePoint 整合已正確設定。</span><span class="sxs-lookup"><span data-stu-id="db7c0-106">For testing purposes, you can publish a sample workbook that already contains PowerPivot data and use it to confirm that SharePoint integration is correctly configured.</span></span>  
  
##  <a name="verify-central-administration-integration"></a><a name="verifyinstall"></a> <span data-ttu-id="db7c0-107">確認管理中心整合</span><span class="sxs-lookup"><span data-stu-id="db7c0-107">Verify Central Administration Integration</span></span>  
 <span data-ttu-id="db7c0-108">若要確認 PowerPivot 可與管理中心整合，請執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="db7c0-108">To verify PowerPivot integration with Central Administration, do the following:</span></span>  
  
1.  <span data-ttu-id="db7c0-109">在 [開始] 功能表上，按一下 [**所有程式**]，開啟 [Microsoft SharePoint 2010 產品]，然後按一下 [ **SharePoint 2010 管理中心**]。</span><span class="sxs-lookup"><span data-stu-id="db7c0-109">On the Start menu, click **All Programs**, open Microsoft SharePoint 2010 Products, and click **SharePoint 2010 Central Administration**.</span></span>  
  
2.  <span data-ttu-id="db7c0-110">輸入您的使用者名稱和密碼，然後按一下 [確定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="db7c0-110">Enter your user name and password, and then click **OK**.</span></span>  
  
     <span data-ttu-id="db7c0-111">您可以選擇修改瀏覽器設定，這樣一來，當您每次開啟管理中心時，就不必輸入使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="db7c0-111">Optionally, you can modify browser settings to avoid having to enter a user name and password each time you open Central Administration.</span></span> <span data-ttu-id="db7c0-112">若要將管理中心當做信任的網站加入，請執行下列動作。</span><span class="sxs-lookup"><span data-stu-id="db7c0-112">To add Central Administration as a trusted site, do the following.</span></span>  
  
    1.  <span data-ttu-id="db7c0-113">在 Internet Explorer 的 [工具] 功能表上，按一下 [**網際網路選項**]。</span><span class="sxs-lookup"><span data-stu-id="db7c0-113">In Internet Explorer, on the Tools menu, click **Internet options**.</span></span>  
  
    2.  <span data-ttu-id="db7c0-114">在 [安全性] 索引標籤的 [選取要檢視或變更安全性設定的區域]\*\*\*\* 區段中，按一下 [信任的網站]，然後按一下 [網站]。</span><span class="sxs-lookup"><span data-stu-id="db7c0-114">On the Security tab, in the **Select a zone to view or change security settings** section, click Trusted Sites, and then click Sites.</span></span>  
  
    3.  <span data-ttu-id="db7c0-115">清除 [此區域內的所有網站需要伺服器驗證 (https:)]\*\*\*\* 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="db7c0-115">Clear the **Require server verification (https:) for all sites in this zone** checkbox.</span></span>  
  
    4.  <span data-ttu-id="db7c0-116">在 [將這個網站新增到區域]\*\*\*\* 中，輸入網站的 URL，然後按一下 [新增]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="db7c0-116">In **Add this Web site to the zone**, type the URL to your site, and then click **Add**.</span></span>  
  
    5.  <span data-ttu-id="db7c0-117">按一下 [關閉]\*\*\*\*，然後按一下 [確定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="db7c0-117">Click **Close**, and then click **OK**.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="db7c0-118">SharePoint 安裝文件集包括用來解決 Proxy 伺服器錯誤以及停用 Internet Explorer 中 [增強式安全性設定] 的其他指示，好讓您可以下載及安裝更新。</span><span class="sxs-lookup"><span data-stu-id="db7c0-118">SharePoint installation documentation includes additional instructions for working around proxy server errors and for disabling Internet Explorer Enhanced Security Configuration so that you can download and install updates.</span></span> <span data-ttu-id="db7c0-119">如需詳細資訊，請參閱 Microsoft 網站上 **以 SQL Server 部署單一伺服器** 中的 " [Perform additional tasks](https://go.microsoft.com/fwlink/?LinkId=177754) " 一節。</span><span class="sxs-lookup"><span data-stu-id="db7c0-119">For more information, see the **Perform additional tasks** section in [Deploy a single server with SQL Server](https://go.microsoft.com/fwlink/?LinkId=177754) on the Microsoft web site.</span></span>  
  
3.  <span data-ttu-id="db7c0-120">在管理中心的 [系統設定] 中，按一下 **[管理伺服器陣列功能]**。</span><span class="sxs-lookup"><span data-stu-id="db7c0-120">In Central Administration, in System Settings, click **Manage farm features**.</span></span>  
  
4.  <span data-ttu-id="db7c0-121">確認 **[PowerPivot 整合功能]** 為 **[使用中]**。</span><span class="sxs-lookup"><span data-stu-id="db7c0-121">Verify that **PowerPivot Integration Feature** is **Active**.</span></span>  
  
5.  <span data-ttu-id="db7c0-122">在 [管理中心] 的 [系統設定] 中，按一下 [**管理伺服器上的服務**]。</span><span class="sxs-lookup"><span data-stu-id="db7c0-122">In Central Administration, in System Settings, click **Manage services on server**.</span></span>  
  
6.  <span data-ttu-id="db7c0-123">確認 **SQL Server Analysis Services** 和 **SQL Server PowerPivot 系統服務** 都已啟動。</span><span class="sxs-lookup"><span data-stu-id="db7c0-123">Verify that **SQL Server Analysis Services** and **SQL Server PowerPivot System Service** are started.</span></span>  
  
7.  <span data-ttu-id="db7c0-124">在 [管理中心] 的 [應用程式管理] 中，按一下 **[管理服務應用程式]** 。</span><span class="sxs-lookup"><span data-stu-id="db7c0-124">In Central Administration, in Application Management, click **Manage service applications**.</span></span>  
  
8.  <span data-ttu-id="db7c0-125">按一下 [**預設的 Powerpivot 服務應用程式**]，開啟此應用程式的 PowerPivot 管理儀表板。</span><span class="sxs-lookup"><span data-stu-id="db7c0-125">Click **Default PowerPivot Service Application** to open PowerPivot Management Dashboard for this application.</span></span> <span data-ttu-id="db7c0-126">在第一次使用時，需要數分鐘才能載入儀表板。</span><span class="sxs-lookup"><span data-stu-id="db7c0-126">On first use, the dashboard takes several minutes to load.</span></span>  
  
     <span data-ttu-id="db7c0-127">或者，按一下 [**預設 PowerPivot 服務應用程式**] 旁邊的空白處來選取資料列，然後按一下 [**屬性**] 以查看此服務應用程式的設定。</span><span class="sxs-lookup"><span data-stu-id="db7c0-127">Alternatively, click the empty space next to **Default PowerPivot Service Application** to select the row, and click **Properties** to view the configuration settings for this service application.</span></span> <span data-ttu-id="db7c0-128">您可以修改組態設定與應用程式屬性來變更您的伺服器組態。</span><span class="sxs-lookup"><span data-stu-id="db7c0-128">You can modify both configuration settings and application properties to change your server configuration.</span></span> <span data-ttu-id="db7c0-129">如需這些設定的詳細資訊，請參閱[在管理中心建立和設定 PowerPivot 服務應用程式](../../power-pivot-sharepoint/create-and-configure-power-pivot-service-application-in-ca.md)。</span><span class="sxs-lookup"><span data-stu-id="db7c0-129">For more information about these settings, see [Create and Configure a PowerPivot Service Application in Central Administration](../../power-pivot-sharepoint/create-and-configure-power-pivot-service-application-in-ca.md).</span></span>  
  
## <a name="verify-integration-at-the-site-level"></a><span data-ttu-id="db7c0-130">確認網站層級的整合</span><span class="sxs-lookup"><span data-stu-id="db7c0-130">Verify Integration at the Site Level</span></span>  
 <span data-ttu-id="db7c0-131">若要確認 PowerPivot 可與 SharePoint 網站整合，請執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="db7c0-131">To verify PowerPivot integration with a SharePoint site, do the following:</span></span>  
  
1.  <span data-ttu-id="db7c0-132">在瀏覽器中，開啟您建立的 Web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="db7c0-132">In a browser, open the Web application you created.</span></span> <span data-ttu-id="db7c0-133">如果您使用預設值，您可以 \<your computer name> 在 URL 位址中指定 HTTP://。</span><span class="sxs-lookup"><span data-stu-id="db7c0-133">If you used default values, you can specify http://\<your computer name> in the URL address.</span></span>  
  
2.  <span data-ttu-id="db7c0-134">確認應用程式中可以使用 PowerPivot 資料存取和處理功能。</span><span class="sxs-lookup"><span data-stu-id="db7c0-134">Verify that PowerPivot data access and processing features are available in the application.</span></span> <span data-ttu-id="db7c0-135">若要這樣做，您可以確認 PowerPivot 提供的文件庫範本是否存在：</span><span class="sxs-lookup"><span data-stu-id="db7c0-135">You can do this by verifying the presence of PowerPivot-provided library templates:</span></span>  
  
    1.  <span data-ttu-id="db7c0-136">在 [網站動作] 上，按一下 [**更多選項**]。</span><span class="sxs-lookup"><span data-stu-id="db7c0-136">On Site Actions, click **More Options..**.</span></span>  
  
    2.  <span data-ttu-id="db7c0-137">在 [程式庫] 中，您應該會看到**資料摘要庫**和**PowerPivot 圖庫**。</span><span class="sxs-lookup"><span data-stu-id="db7c0-137">In Libraries, you should see **Data Feed Library** and **PowerPivot Gallery**.</span></span> <span data-ttu-id="db7c0-138">這些文件庫範本是由 PowerPivot 功能所提供，如果此功能已正確整合，就可以在文件庫清單中看到這些範本。</span><span class="sxs-lookup"><span data-stu-id="db7c0-138">These library templates are provided by the PowerPivot feature and will be visible in the Libraries list if the feature is integrated correctly.</span></span>  
  
## <a name="verify-data-access-on-the-server"></a><span data-ttu-id="db7c0-139">確認伺服器上的資料存取。</span><span class="sxs-lookup"><span data-stu-id="db7c0-139">Verify Data Access on the Server</span></span>  
 <span data-ttu-id="db7c0-140">若要在伺服器上確認 PowerPivot 資料存取，請執行以下作業：</span><span class="sxs-lookup"><span data-stu-id="db7c0-140">To verify PowerPivot data access on the server, do the following:</span></span>  
  
1.  <span data-ttu-id="db7c0-141">[下載](https://go.microsoft.com/fwlink/?LinkID=219108) Reporting Services 教學課程隨附的野餐資料範例。</span><span class="sxs-lookup"><span data-stu-id="db7c0-141">[Download](https://go.microsoft.com/fwlink/?LinkID=219108) the Picnic data sample that accompanies a Reporting Services tutorial.</span></span> <span data-ttu-id="db7c0-142">您將使用此下載中的範例活頁簿確認 PowerPivot 資料存取。</span><span class="sxs-lookup"><span data-stu-id="db7c0-142">You will use the sample workbook in this download to verify PowerPivot data access.</span></span> <span data-ttu-id="db7c0-143">將檔案解壓縮。</span><span class="sxs-lookup"><span data-stu-id="db7c0-143">Extract the files.</span></span>  
  
2.  <span data-ttu-id="db7c0-144">將 Excel 活頁簿 (.xlsx) 上傳至 Shared Documents。</span><span class="sxs-lookup"><span data-stu-id="db7c0-144">Upload the Excel workbook (.xlsx) to Shared Documents.</span></span> <span data-ttu-id="db7c0-145">此活頁簿包含內嵌的 PowerPivot 資料。</span><span class="sxs-lookup"><span data-stu-id="db7c0-145">The workbook contains embedded PowerPivot data.</span></span>  
  
3.  <span data-ttu-id="db7c0-146">按一下文件，從文件庫中加以開啟。</span><span class="sxs-lookup"><span data-stu-id="db7c0-146">Click on the document to open it from the library.</span></span>  
  
4.  <span data-ttu-id="db7c0-147">按一下活頁簿頂端的交叉分析篩選器或篩選。</span><span class="sxs-lookup"><span data-stu-id="db7c0-147">Click on a slicer or filter at the top of the workbook.</span></span> <span data-ttu-id="db7c0-148">月份、色彩和類型是此活頁簿中的交叉分析篩選器。</span><span class="sxs-lookup"><span data-stu-id="db7c0-148">Month, color, and type are slicers in this workbook.</span></span> <span data-ttu-id="db7c0-149">按一下交叉分析篩選器會啟動 PowerPivot 查詢並證明您的伺服器可以運作。</span><span class="sxs-lookup"><span data-stu-id="db7c0-149">Clicking a slicer starts a PowerPivot query and proves that your server is operational.</span></span> <span data-ttu-id="db7c0-150">伺服器將會在背景載入 PowerPivot 資料，然後傳回結果。</span><span class="sxs-lookup"><span data-stu-id="db7c0-150">The server will load PowerPivot data in the background and return the results.</span></span>  
  
5.  <span data-ttu-id="db7c0-151">回到文件庫。</span><span class="sxs-lookup"><span data-stu-id="db7c0-151">Go back to the library.</span></span> <span data-ttu-id="db7c0-152">選取活頁簿右邊的向下箭號，然後按一下 [啟動 Power View]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="db7c0-152">Select the down arrow to the right of the workbook, and then click **Launch Power View**.</span></span> <span data-ttu-id="db7c0-153">此步驟會確認 Reporting Services 中的 [!INCLUDE[ssCrescent](../../../includes/sscrescent-md.md)] 功能可以運作。</span><span class="sxs-lookup"><span data-stu-id="db7c0-153">This step confirms that the [!INCLUDE[ssCrescent](../../../includes/sscrescent-md.md)] feature in Reporting Services is operational.</span></span> <span data-ttu-id="db7c0-154">如果您未安裝 Reporting Services，請略過此步驟。</span><span class="sxs-lookup"><span data-stu-id="db7c0-154">If you did not install Reporting Services, skip this step.</span></span>  
  
     <span data-ttu-id="db7c0-155">在下一個步驟中，您將會連接到 Management Studio 中的伺服器，並確認已經載入及快取資料。</span><span class="sxs-lookup"><span data-stu-id="db7c0-155">In the next step, you will connect to the server in Management Studio to verify the data is loaded and cached.</span></span>  
  
6.  <span data-ttu-id="db7c0-156">在 [開始] 功能表中，從 [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] 程式群組啟動 SQL Server Management Studio。</span><span class="sxs-lookup"><span data-stu-id="db7c0-156">Start SQL Server Management Studio from the [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] program group in the Start menu.</span></span> <span data-ttu-id="db7c0-157">如果伺服器上未安裝此工具，您可以向前跳到最後一個步驟，確認快取檔案存在。</span><span class="sxs-lookup"><span data-stu-id="db7c0-157">If this tool is not installed on your server, you can skip ahead to the last step to confirm the presence of cached files.</span></span>  
  
7.  <span data-ttu-id="db7c0-158">在 [伺服器類型] 中，選取 [ **Analysis Services**]。</span><span class="sxs-lookup"><span data-stu-id="db7c0-158">In Server Type, select **Analysis Services**.</span></span>  
  
8.  <span data-ttu-id="db7c0-159">在 [伺服器名稱] 中，輸入\*\* \<server-name> \powerpivot\*\*，其中 **\<server-name>** 是具有 PowerPivot for SharePoint 安裝的電腦名稱稱。</span><span class="sxs-lookup"><span data-stu-id="db7c0-159">In Server Name, enter **\<server-name>\powerpivot**, where **\<server-name>** is the name of the computer that has the PowerPivot for SharePoint installation.</span></span>  
  
9. <span data-ttu-id="db7c0-160">按一下 [ **連接**]。</span><span class="sxs-lookup"><span data-stu-id="db7c0-160">Click **Connect**.</span></span> <span data-ttu-id="db7c0-161">這樣會確認可以使用 Analysis Services 伺服器。</span><span class="sxs-lookup"><span data-stu-id="db7c0-161">This verifies that the Analysis Services server is available.</span></span>  
  
10. <span data-ttu-id="db7c0-162">在物件總管中，您可以按一下 [**資料庫**]，以查看已載入的 PowerPivot 資料檔案清單。</span><span class="sxs-lookup"><span data-stu-id="db7c0-162">In Object Explorer, you can click **Databases** to view the list of PowerPivot data files that are loaded.</span></span>  
  
11. <span data-ttu-id="db7c0-163">在電腦檔案系統上，檢查下列資料夾來決定檔案是否要快取到磁碟。</span><span class="sxs-lookup"><span data-stu-id="db7c0-163">On the computer file system, check the following folder to determine whether files are cached to disk.</span></span> <span data-ttu-id="db7c0-164">快取檔案的存在會進一步驗證您的部署是否可以運作。</span><span class="sxs-lookup"><span data-stu-id="db7c0-164">The presence of cached files is further verification that your deployment is operational.</span></span> <span data-ttu-id="db7c0-165">若要查看檔案快取，請移至 \<drive> ： \Program FILES\MICROSOFT SQL Server\MSAS11。POWERPIVOT\OLAP\Backup\Sandboxes\Default PowerPivot 服務應用程式資料夾。</span><span class="sxs-lookup"><span data-stu-id="db7c0-165">To view the file cache, go to the \<drive>:\Program Files\Microsoft SQL Server\MSAS11.POWERPIVOT\OLAP\Backup\Sandboxes\Default PowerPivot Service Application folder.</span></span> <span data-ttu-id="db7c0-166">每個快取的資料庫都會使用以 GUID 為基礎的命名慣例，儲存在自己的資料夾中，以確保名稱是唯一的。</span><span class="sxs-lookup"><span data-stu-id="db7c0-166">Each cached database is stored in its own folder, using a GUID-based naming convention to ensure a unique name.</span></span>  
  
  
