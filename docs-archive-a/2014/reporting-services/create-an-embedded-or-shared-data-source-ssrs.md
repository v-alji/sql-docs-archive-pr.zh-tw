---
title: 建立 (SSRS) 的內嵌或共用資料來源 |Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- data sources [Reporting Services], creating
ms.assetid: b111a8d0-a60d-4c8b-b00a-51644b19c34b
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 52c5263859ad16ed725065bce4998d08bddaf5f7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703933"
---
# <a name="create-an-embedded-or-shared-data-source-ssrs"></a><span data-ttu-id="c608b-102">建立內嵌或共用資料來源 (SSRS)</span><span class="sxs-lookup"><span data-stu-id="c608b-102">Create an Embedded or Shared Data Source (SSRS)</span></span>
  <span data-ttu-id="c608b-103">報表資料來源會指定名稱及連接資訊。</span><span class="sxs-lookup"><span data-stu-id="c608b-103">A report data source specifies a name and connection information.</span></span> [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] <span data-ttu-id="c608b-104">可支援兩種類型的資料來源：內嵌和共用。</span><span class="sxs-lookup"><span data-stu-id="c608b-104">supports two types of data sources: embedded and shared.</span></span> <span data-ttu-id="c608b-105">內嵌資料來源是定義在報表定義中，而且只能供該報表使用。</span><span class="sxs-lookup"><span data-stu-id="c608b-105">An embedded data source is defined in a report definition and used only by that report.</span></span> <span data-ttu-id="c608b-106">共用資料來源會定義成個別的項目，而且可以供多個報表使用。</span><span class="sxs-lookup"><span data-stu-id="c608b-106">A shared data source is defined as a separate item and can be used by multiple reports.</span></span> <span data-ttu-id="c608b-107">如需詳細資訊，請參閱[內嵌和共用資料連線或資料來源 &#40;報表產生器和 SSRS&#41;](../../2014/reporting-services/embedded-and-shared-data-connections-or-data-sources-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="c608b-107">For more information, see [Embedded and Shared Data Connections or Data Sources &#40;Report Builder and SSRS&#41;](../../2014/reporting-services/embedded-and-shared-data-connections-or-data-sources-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="c608b-108">在報表產生器中，您可以瀏覽至報表伺服器或 SharePoint 網站，然後選取資料來源或建立內嵌資料來源。</span><span class="sxs-lookup"><span data-stu-id="c608b-108">In Report Builder, you browse to the report server or SharePoint site and select data sources or create embedded data sources.</span></span> <span data-ttu-id="c608b-109">您無法在報表產生器中建立共用資料來源。</span><span class="sxs-lookup"><span data-stu-id="c608b-109">You cannot create shared data sources in Report Builder.</span></span>  
  
 <span data-ttu-id="c608b-110">在報表設計師中，您可以建立共用或內嵌資料來源。</span><span class="sxs-lookup"><span data-stu-id="c608b-110">In Report Designer, you can create shared or embedded data sources.</span></span> <span data-ttu-id="c608b-111">從 [報表資料] 窗格中，開始建立資料來源參考，然後選取 [**新增**] 選項。</span><span class="sxs-lookup"><span data-stu-id="c608b-111">From the Report Data pane, begin to create a data source reference, and then select the **New** option.</span></span> <span data-ttu-id="c608b-112">建立資料來源參考之後，新的共用資料來源就會自動加入至 [方案總管] 的 [共用資料來源] 資料夾底下。</span><span class="sxs-lookup"><span data-stu-id="c608b-112">After you create the data source reference, a new shared data source will automatically be added to Solution Explorer under the Shared Data Sources folder.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../includes/ssrbrddup-md.md)]  
  
 <span data-ttu-id="c608b-113">您也可以直接在報表伺服器或 SharePoint 網站上建立共用資料來源。</span><span class="sxs-lookup"><span data-stu-id="c608b-113">You can also create shared data sources directly on a report server or SharePoint site.</span></span> <span data-ttu-id="c608b-114">如需詳細資訊，請參閱[建立、刪除或修改共用資料來源 &#40;報表管理員&#41;](../../2014/reporting-services/create-delete-or-modify-a-shared-data-source-report-manager.md) [，或建立和管理 SharePoint 整合模式 Reporting Services 中 &#40;&#41;的共用資料](../../2014/reporting-services/create-manage-shared-data-sources-reporting-services-sharepoint-integrated-mode.md)源。</span><span class="sxs-lookup"><span data-stu-id="c608b-114">For more information, see [Create, Delete, or Modify a Shared Data Source &#40;Report Manager&#41;](../../2014/reporting-services/create-delete-or-modify-a-shared-data-source-report-manager.md) or [Create and Manage Shared Data Sources &#40;Reporting Services in SharePoint Integrated Mode&#41;](../../2014/reporting-services/create-manage-shared-data-sources-reporting-services-sharepoint-integrated-mode.md).</span></span>  
  
### <a name="to-create-an-embedded-or-shared-data-source"></a><span data-ttu-id="c608b-115">建立內嵌或共用資料來源</span><span class="sxs-lookup"><span data-stu-id="c608b-115">To create an embedded or shared data source</span></span>  
  
1.  <span data-ttu-id="c608b-116">在 [報表資料] 窗格的工具列上，按一下 [**新增**]，然後按一下 [**資料來源**]。</span><span class="sxs-lookup"><span data-stu-id="c608b-116">On the toolbar in the Report Data pane, click **New** and then click **Data Source**.</span></span> <span data-ttu-id="c608b-117">**[資料來源屬性]** 對話方塊隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="c608b-117">The **Data Source Properties** dialog box opens.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="c608b-118">如果看不到 [報表資料] 窗格，請按一下 [檢視]\*\*\*\* 功能表上的 [報表資料]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="c608b-118">If the Report Data pane is not visible, click **Report Data** on the **View** menu.</span></span>  
  
2.  <span data-ttu-id="c608b-119">在 **[名稱]** 文字方塊中，輸入資料來源的名稱或接受預設值。</span><span class="sxs-lookup"><span data-stu-id="c608b-119">In the **Name** text box, type a name for the data source or accept the default.</span></span> <span data-ttu-id="c608b-120">資料來源名稱是在報表內部使用。</span><span class="sxs-lookup"><span data-stu-id="c608b-120">The data source name is used internally within the report.</span></span> <span data-ttu-id="c608b-121">為了清楚起見，我們建議資料來源的名稱要包含連接字串中所指定的資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="c608b-121">For clarity, we recommend that the name of the data source contain the name of the database specified in the connection string.</span></span>  
  
3.  <span data-ttu-id="c608b-122">若為內嵌資料來源，請確認已選取 [**內嵌連接**]。</span><span class="sxs-lookup"><span data-stu-id="c608b-122">For an embedded data source, verify that **Embedded connection** is selected.</span></span>  
  
    1.  <span data-ttu-id="c608b-123">從 [類型]\*\*\*\* 下拉式清單中，選取資料來源類型，例如 [Microsoft SQL Server]\*\*\*\* 或 [OLE DB]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="c608b-123">From the **Type** drop-down list, select a data source type; for example, **Microsoft SQL Server** or **OLE DB**.</span></span>  
  
    2.  <span data-ttu-id="c608b-124">使用以下其中一個替代方式指定連接字串：</span><span class="sxs-lookup"><span data-stu-id="c608b-124">Specify a connection string using one of the following alternatives:</span></span>  
  
    -   <span data-ttu-id="c608b-125">在 **[連接字串]** 文字方塊中直接輸入連接字串。</span><span class="sxs-lookup"><span data-stu-id="c608b-125">Type the connection string directly in the **Connection string** text box.</span></span> <span data-ttu-id="c608b-126">如需範例連接字串的清單，請參閱 Reporting Services 中報表產生器或[資料連線、資料來源和連接字串](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-reporting-services.md)[中的資料連線、資料來源和連接](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-report-builder.md)字串。</span><span class="sxs-lookup"><span data-stu-id="c608b-126">For a list of example connection strings, see [Data Connections, Data Sources, and Connection Strings in Report Builder](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-report-builder.md) or [Data Connections, Data Sources, and Connection Strings in Reporting Services](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-reporting-services.md).</span></span>  
  
    -   <span data-ttu-id="c608b-127">按一下運算式 (**fx)** 按鈕，即可建立一個評估為連接字串的運算式。</span><span class="sxs-lookup"><span data-stu-id="c608b-127">Click the expression (**fx)** button to create an expression that evaluates to a connection string.</span></span> <span data-ttu-id="c608b-128">在 **[運算式]** 對話方塊的 [運算式] 窗格內，輸入運算式。</span><span class="sxs-lookup"><span data-stu-id="c608b-128">In the **Expression** dialog box, type the expression in the Expression pane.</span></span> [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
    -   <span data-ttu-id="c608b-129">按一下 **[編輯]** ，針對您在步驟 2 中選擇的資料來源類型開啟 **[連接屬性]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="c608b-129">Click **Edit** to open the **Connection Properties** dialog box for the data source type you chose in step 2.</span></span>  
  
         <span data-ttu-id="c608b-130">依照此資料來源類型適合的情況，填入 **[連接屬性]** 對話方塊中的欄位。</span><span class="sxs-lookup"><span data-stu-id="c608b-130">Fill in the fields in the **Connection Properties** dialog box as appropriate for the data source type.</span></span> <span data-ttu-id="c608b-131">連接屬性包括資料來源的類型、資料來源的名稱以及要使用的認證。</span><span class="sxs-lookup"><span data-stu-id="c608b-131">Connection properties include the type of data source, the name of the data source, and the credentials to use.</span></span> <span data-ttu-id="c608b-132">當您在此對話方塊中指定值之後，請按一下 **[測試連接]** 來確認此資料來源確實可用，而且您指定的認證正確無誤。</span><span class="sxs-lookup"><span data-stu-id="c608b-132">After you specify values in this dialog box, click **Test Connection** to verify that the data source is available and that the credentials you specified are correct.</span></span> <span data-ttu-id="c608b-133">如需特定資料來源類型的詳細資訊，請參閱[從外部資料來源新增資料 &#40;SSRS&#41;](report-data/add-data-from-external-data-sources-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="c608b-133">For more information about specific data source types, see topics in [Add Data from External Data Sources &#40;SSRS&#41;](report-data/add-data-from-external-data-sources-ssrs.md).</span></span>  
  
4.  <span data-ttu-id="c608b-134">若為共用資料來源，請確認已選取 [**使用共用資料來源參考**]。</span><span class="sxs-lookup"><span data-stu-id="c608b-134">For a shared data source, verify that **Use shared data source reference** is selected.</span></span>  
  
    1.  <span data-ttu-id="c608b-135">按一下 **[新增]** 。</span><span class="sxs-lookup"><span data-stu-id="c608b-135">Click **New**.</span></span> <span data-ttu-id="c608b-136">在 [共用資料來源]\*\*\*\* 屬性對話方塊中，遵循步驟 2 和 3 來建立新的資料來源。</span><span class="sxs-lookup"><span data-stu-id="c608b-136">In the **Shared Data Source** properties dialog box, follow steps 2 and 3 to create a new data source.</span></span>  
  
    2.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
         <span data-ttu-id="c608b-137">新的共用資料來源會出現在 [方案總管] 的 [共用資料來源] 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="c608b-137">The new shared data source appears in the Shared Data Sources folder in Solution Explorer.</span></span>  
  
5.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
     <span data-ttu-id="c608b-138">資料來源會出現在 [報表資料] 窗格中。</span><span class="sxs-lookup"><span data-stu-id="c608b-138">The data source appears in the Report Data pane.</span></span> <span data-ttu-id="c608b-139">在 [報表資料] 窗格中，共用資料來源會指向資料來源定義。</span><span class="sxs-lookup"><span data-stu-id="c608b-139">In the Report Data pane, a shared data source points to the data source definition.</span></span> <span data-ttu-id="c608b-140">在報表產生器中，資料來源定義位於報表伺服器或 SharePoint 網站上。</span><span class="sxs-lookup"><span data-stu-id="c608b-140">In Report Builder, the data source definition is on a report server or SharePoint site.</span></span> <span data-ttu-id="c608b-141">在報表設計師中，資料來源定義是 [方案總管] 中 [共用資料來源] 資料夾底下的檔案。</span><span class="sxs-lookup"><span data-stu-id="c608b-141">In Report Designer, the data source definition is a file in Solution Explorer under the Shared Data Sources folder.</span></span>  
  
### <a name="to-import-an-existing-data-source-in-report-designer"></a><span data-ttu-id="c608b-142">若要在報表設計師中匯入現有的資料來源</span><span class="sxs-lookup"><span data-stu-id="c608b-142">To import an existing data source in Report Designer</span></span>  
  
1.  <span data-ttu-id="c608b-143">在方案總管中，以滑鼠右鍵按一下報表伺服器專案中的 [共用資料來源]\*\*\*\* 資料夾，然後按一下 [加入現有項目]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="c608b-143">In Solution Explorer, right-click the **Shared Data Sources** folder in the report server project, and then click **Add Existing Item**.</span></span> <span data-ttu-id="c608b-144">[新增現有項目]\*\*\*\* 對話方塊隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="c608b-144">The **Add Existing Item** dialog box opens.</span></span>  
  
2.  <span data-ttu-id="c608b-145">巡覽至現有的報表定義共用資料來源 (rds) 檔案，然後按一下 [開啟]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="c608b-145">Navigate to an existing Report Definition Shared data source (rds) file and then click **Open**.</span></span>  
  
3.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
### <a name="to-convert-an-embedded-data-source-to-a-shared-data-source-in-report-designer"></a><span data-ttu-id="c608b-146">若要在報表設計師中，將內嵌資料來源轉換成共用資料來源</span><span class="sxs-lookup"><span data-stu-id="c608b-146">To convert an embedded data source to a shared data source in Report Designer</span></span>  
  
-   <span data-ttu-id="c608b-147">在 [報表資料] 窗格中，以滑鼠右鍵按一下資料來源，然後按一下 [**轉換為共用資料來源**]。</span><span class="sxs-lookup"><span data-stu-id="c608b-147">In the Report Data pane, right-click the data source and then click **Convert to Shared Data Source**.</span></span>  
  
### <a name="to-convert-a-shared-data-source-to-an-embedded-data-source-in-report-builder"></a><span data-ttu-id="c608b-148">若要在報表產生器中，將共用資料來源轉換成內嵌資料來源</span><span class="sxs-lookup"><span data-stu-id="c608b-148">To convert a shared data source to an embedded data source in Report Builder</span></span>  
  
-   <span data-ttu-id="c608b-149">在 [報表資料] 窗格中，以滑鼠右鍵按一下資料來源，然後開啟 [**資料來源屬性**]。</span><span class="sxs-lookup"><span data-stu-id="c608b-149">In the Report Data pane, right-click the data source and open **Data Source Properties**.</span></span>  
  
-   <span data-ttu-id="c608b-150">按一下 [**內嵌連接**]，然後完成建立內嵌資料來源，如先前的程式所述。</span><span class="sxs-lookup"><span data-stu-id="c608b-150">Click **Embedded Connection** and finish creating the embedded data source as described in an earlier procedure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c608b-151">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c608b-151">See Also</span></span>  
 <span data-ttu-id="c608b-152">[將認證儲存在 Reporting Services 資料來源中](report-data/store-credentials-in-a-reporting-services-data-source.md) </span><span class="sxs-lookup"><span data-stu-id="c608b-152">[Store Credentials in a Reporting Services Data Source](report-data/store-credentials-in-a-reporting-services-data-source.md) </span></span>  
 <span data-ttu-id="c608b-153">[內嵌和共用資料連線或資料來源 &#40;報表產生器和 SSRS&#41;](../../2014/reporting-services/embedded-and-shared-data-connections-or-data-sources-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="c608b-153">[Embedded and Shared Data Connections or Data Sources &#40;Report Builder and SSRS&#41;](../../2014/reporting-services/embedded-and-shared-data-connections-or-data-sources-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="c608b-154">[將資料來源從內嵌轉換成共用 &#40;報表產生器和 SSRS&#41;](report-data/convert-data-sources-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="c608b-154">[Convert a Data Source from Embedded to Shared &#40;Report Builder and SSRS&#41;](report-data/convert-data-sources-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="c608b-155">[將報表或模型系結至 &#40;SSRS&#41;的共用資料來源](report-data/bind-a-report-or-model-to-a-shared-data-source-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="c608b-155">[Bind a Report or Model to a Shared Data Source &#40;SSRS&#41;](report-data/bind-a-report-or-model-to-a-shared-data-source-ssrs.md) </span></span>  
 <span data-ttu-id="c608b-156">[設定報表的資料來源屬性 &#40;報表管理員&#41;](report-data/configure-data-source-properties-for-a-report-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="c608b-156">[Configure Data Source Properties for a Report  &#40;Report Manager&#41;](report-data/configure-data-source-properties-for-a-report-report-manager.md) </span></span>  
 [<span data-ttu-id="c608b-157">Reporting Services 支援的資料來源 &#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="c608b-157">Data Sources Supported by Reporting Services &#40;SSRS&#41;</span></span>](create-deploy-and-manage-mobile-and-paginated-reports.md)  
  
  
