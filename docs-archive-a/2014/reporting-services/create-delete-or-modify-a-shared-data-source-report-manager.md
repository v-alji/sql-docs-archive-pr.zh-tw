---
title: 建立、刪除或修改共用資料來源 (報表管理員) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- shared data sources [Reporting Services]
- removing shared data sources
- data sources [Reporting Services], shared
- deleting shared data sources
- modifying shared data sources
ms.assetid: cd7bace3-f8ec-4ee3-8a9f-2f217cdca9f2
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c6f4ff658e656b159995087df3121806b462e687
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596553"
---
# <a name="create-delete-or-modify-a-shared-data-source-report-manager"></a><span data-ttu-id="65e5f-102">建立、刪除或修改共用資料來源 (報表管理員)</span><span class="sxs-lookup"><span data-stu-id="65e5f-102">Create, Delete, or Modify a Shared Data Source (Report Manager)</span></span>
  <span data-ttu-id="65e5f-103">共用資料來源會指定資料來源的連接屬性。</span><span class="sxs-lookup"><span data-stu-id="65e5f-103">A shared data source specifies connection properties for a data source.</span></span> <span data-ttu-id="65e5f-104">如果您擁有大量報表、模型或資料驅動訂閱所使用的資料來源，請考慮建立共用資料來源，以便排除必須在多個位置維護相同連接資訊的負擔。</span><span class="sxs-lookup"><span data-stu-id="65e5f-104">If you have a data source that is used by a large number of reports, models, or data-driven subscriptions, consider creating a shared data source to eliminate the overhead of having to maintain the same connection information in multiple places.</span></span>  
  
 <span data-ttu-id="65e5f-105">下列圖示會指出報表管理員資料夾階層中的共用資料來源：</span><span class="sxs-lookup"><span data-stu-id="65e5f-105">The following icon indicates a shared data source in the Report Manager folder hierarchy:</span></span>  
  
 <span data-ttu-id="65e5f-106">![共用資料來源圖示](media/hlp-16datasource.png "共用資料來源圖示")</span><span class="sxs-lookup"><span data-stu-id="65e5f-106">![Shared data source icon](media/hlp-16datasource.png "Shared data source icon")</span></span>  
<span data-ttu-id="65e5f-107">共用資料來源的圖示</span><span class="sxs-lookup"><span data-stu-id="65e5f-107">shared data source icon</span></span>  
  
### <a name="to-create-a-shared-data-source"></a><span data-ttu-id="65e5f-108">若要建立共用資料來源</span><span class="sxs-lookup"><span data-stu-id="65e5f-108">To create a shared data source</span></span>  
  
1.  <span data-ttu-id="65e5f-109">啟動 [報表管理員 &#40;SSRS 原生模式&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="65e5f-109">Start [Report Manager  &#40;SSRS Native Mode&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md).</span></span>  
  
2.  <span data-ttu-id="65e5f-110">在報表管理員中，導覽至 **[內容]** 頁面。</span><span class="sxs-lookup"><span data-stu-id="65e5f-110">In Report Manager, navigate to the **Contents** page.</span></span>  
  
3.  <span data-ttu-id="65e5f-111">按一下 **[新增資料來源]**。</span><span class="sxs-lookup"><span data-stu-id="65e5f-111">Click **New Data Source**.</span></span> <span data-ttu-id="65e5f-112">[新增資料來源]\*\*\*\* 頁面隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="65e5f-112">The **New Data Source** page opens.</span></span>  
  
4.  <span data-ttu-id="65e5f-113">輸入項目的名稱。</span><span class="sxs-lookup"><span data-stu-id="65e5f-113">Type a name for the item.</span></span> <span data-ttu-id="65e5f-114">名稱必須至少包含一個字元，而且開頭必須為字母。</span><span class="sxs-lookup"><span data-stu-id="65e5f-114">A name must contain at least one character and it must start with a letter.</span></span> <span data-ttu-id="65e5f-115">它也可以包含特定符號，但不能包含空格或下列字元：; ?</span><span class="sxs-lookup"><span data-stu-id="65e5f-115">It can also include certain symbols, but not spaces or the characters ; ?</span></span> <span data-ttu-id="65e5f-116">： \@ & = +，$/\* \< > |" /.</span><span class="sxs-lookup"><span data-stu-id="65e5f-116">: \@ & = + , $ / \* \< > | " /.</span></span>  
  
5.  <span data-ttu-id="65e5f-117">選擇性地輸入描述，以提供使用者有關連接的資訊。</span><span class="sxs-lookup"><span data-stu-id="65e5f-117">Optionally type a description to provide users with information about the connection.</span></span> <span data-ttu-id="65e5f-118">此描述會出現在報表管理員的 [內容]\*\*\*\* 頁面上。</span><span class="sxs-lookup"><span data-stu-id="65e5f-118">This description will appear on the **Contents** page in Report Manager.</span></span>  
  
6.  <span data-ttu-id="65e5f-119">在 [資料來源類型]\*\*\*\* 清單中，指定用來處理資料來源中之資料的資料處理延伸模組。</span><span class="sxs-lookup"><span data-stu-id="65e5f-119">In the **Data source type** list, specify the data processing extension that is used to process data from the data source.</span></span>  
  
7.  <span data-ttu-id="65e5f-120">針對 [連接字串]\*\*\*\*，指定報表伺服器用於連線到資料來源的連接字串。</span><span class="sxs-lookup"><span data-stu-id="65e5f-120">For **Connection string**, specify the connection string that the report server uses to connect to the data source.</span></span> <span data-ttu-id="65e5f-121">建議您不要在連接字串中指定認證。</span><span class="sxs-lookup"><span data-stu-id="65e5f-121">It is recommended that you do not specify credentials in the connection string.</span></span>  
  
     <span data-ttu-id="65e5f-122">下列範例說明用來連接到本機資料庫的連接字串 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] ：</span><span class="sxs-lookup"><span data-stu-id="65e5f-122">The following example illustrates a connection string for connecting to the local [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] database:</span></span>  
  
    ```  
    data source=<localservername>; initial catalog=AdventureWorks2012  
    ```  
  
8.  <span data-ttu-id="65e5f-123">針對 **[使用下列方式連接]**，指定報表執行時要如何取得認證：</span><span class="sxs-lookup"><span data-stu-id="65e5f-123">For **Connect using**, specify how credentials are obtained when the report runs:</span></span>  
  
    -   <span data-ttu-id="65e5f-124">如果您要提示使用者輸入登入名稱和密碼，請按一下 **[執行報表的使用者所提供的認證]**。</span><span class="sxs-lookup"><span data-stu-id="65e5f-124">If you want to prompt the user for a logon name and password, click **Credentials supplied by the user running the report**.</span></span> <span data-ttu-id="65e5f-125">若要使用使用者所輸入的認證作為 Windows 認證，請按一下 [連線到資料來源時作為 Windows 認證]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="65e5f-125">To use the credentials that the user enters as Windows credentials, click **Use as Windows credentials when connecting to the data source**.</span></span> <span data-ttu-id="65e5f-126">如果使用者名稱和密碼是資料庫認證，請勿選取此選項。</span><span class="sxs-lookup"><span data-stu-id="65e5f-126">If the user name and password are database credentials, do not select this option.</span></span>  
  
    -   <span data-ttu-id="65e5f-127">如果您打算將資料來源當作具有資料來源擁有者所管理之預存認證的共用資料來源，或是在支援訂閱或其他已排程之作業 (例如自動化報表記錄產生) 的報表中使用資料來源，請按一下 [安全地儲存在報表伺服器中的認證]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="65e5f-127">If you intend to use the data source as a shared data source with saved credentials that are managed by the owner of the data source, or for reports that support subscriptions or other scheduled operations (such as automated report history generation), click **Credentials stored securely in the report server**.</span></span> <span data-ttu-id="65e5f-128">如果資料庫伺服器支援模擬或委派，您就可以選取 **[連接到資料來源後，模擬已驗證的使用者]**。</span><span class="sxs-lookup"><span data-stu-id="65e5f-128">If the database server supports impersonation or delegation, you can select **Impersonate the authenticated user after a connection has been made to the data source**.</span></span>  
  
    -   <span data-ttu-id="65e5f-129">對於存取報表的使用者提供的認證，若要讓報表伺服器將認證傳送給主控外部資料來源的伺服器，請按一下 **[Windows 整合式安全性]**。</span><span class="sxs-lookup"><span data-stu-id="65e5f-129">If you want the report server to pass the credentials of the user accessing the report to the server hosting the external data source, click **Windows Integrated Security**.</span></span> <span data-ttu-id="65e5f-130">在此情況下，不會提示使用者輸入使用者名稱或密碼。</span><span class="sxs-lookup"><span data-stu-id="65e5f-130">In this case, the user is not prompted to type a user name or password.</span></span>  
  
    -   <span data-ttu-id="65e5f-131">如果資料來源沒有使用認證 (例如，如果資料來源是從檔案系統存取的 XML 檔)，請按一下 [不需要認證]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="65e5f-131">If the data source does not use credentials (for example, if the data source is an XML file that is accessed from the file system), click **Credentials are not required**.</span></span> <span data-ttu-id="65e5f-132">只有當這種認證類型適用於資料來源時，您才應該指定此認證類型。</span><span class="sxs-lookup"><span data-stu-id="65e5f-132">You should only specify this credential type if it is valid for the data source.</span></span> <span data-ttu-id="65e5f-133">如果您針對需要驗證的資料來源選取此選項，連接將會失敗。</span><span class="sxs-lookup"><span data-stu-id="65e5f-133">If you select this option for a data source that requires authentication, the connection will fail.</span></span> <span data-ttu-id="65e5f-134">如果您選取此選項，請務必設定自動執行帳戶，以便在使用者認證無法使用時，允許報表伺服器連接至其他電腦以擷取資料或檔案。</span><span class="sxs-lookup"><span data-stu-id="65e5f-134">If you select this option, be sure to configure the unattended execution account that allows the report server to connect to other computers to retrieve data or files when user credentials are not available.</span></span>  
  
     <span data-ttu-id="65e5f-135">如需設定認證的詳細資訊，請參閱 [指定報表資料來源的認證及連接資訊](report-data/specify-credential-and-connection-information-for-report-data-sources.md)。</span><span class="sxs-lookup"><span data-stu-id="65e5f-135">For more information about configuring credentials, see [Specify Credential and Connection Information for Report Data Sources](report-data/specify-credential-and-connection-information-for-report-data-sources.md).</span></span> <span data-ttu-id="65e5f-136">如需自動執行帳戶的詳細資訊，請參閱[設定自動執行帳戶 &#40;SSRS 設定管理員&#41;](install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="65e5f-136">For more information about the unattended execution account, see [Configure the Unattended Execution Account &#40;SSRS Configuration Manager&#41;](install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md).</span></span>  
  
9. <span data-ttu-id="65e5f-137">按一下 [測試連線]\*\*\*\* 按鈕，驗證資料來源設定。</span><span class="sxs-lookup"><span data-stu-id="65e5f-137">Click the **Test Connection** button to validate the data source configuration.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="65e5f-138">[測試連接] 按鈕不支援 XML 資料來源類型。</span><span class="sxs-lookup"><span data-stu-id="65e5f-138">The Test Connection button is not supported for the XML data source type.</span></span>  
  
10. <span data-ttu-id="65e5f-139">按一下 [檔案] &gt; [新增] &gt; [專案]</span><span class="sxs-lookup"><span data-stu-id="65e5f-139">Click **OK**</span></span>  
  
### <a name="to-modify-a-shared-data-source"></a><span data-ttu-id="65e5f-140">若要修改共用資料來源</span><span class="sxs-lookup"><span data-stu-id="65e5f-140">To modify a shared data source</span></span>  
  
1.  <span data-ttu-id="65e5f-141">在報表管理員中，導覽至 [內容] 頁面。</span><span class="sxs-lookup"><span data-stu-id="65e5f-141">In Report Manager, navigate to the Contents page.</span></span>  
  
2.  <span data-ttu-id="65e5f-142">巡覽至共用資料來源項目，將滑鼠停留在該項目上，按一下下拉式清單，然後在操作功能表中按一下 [管理]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="65e5f-142">Navigate to the shared data source item, hover over the item, click the drop-down list, and from the context menu, click **Manage**.</span></span> <span data-ttu-id="65e5f-143">[屬性]\*\*\*\* 頁面隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="65e5f-143">The **Properties** page opens.</span></span>  
  
3.  <span data-ttu-id="65e5f-144">修改資料來源，然後按一下 [套用]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="65e5f-144">Modify the data source, and then click **Apply**.</span></span>  
  
### <a name="to-delete-a-shared-data-source"></a><span data-ttu-id="65e5f-145">若要刪除共用資料來源</span><span class="sxs-lookup"><span data-stu-id="65e5f-145">To delete a shared data source</span></span>  
  
-   <span data-ttu-id="65e5f-146">在報表管理員中，巡覽至 [內容]\*\*\*\* 頁面，然後執行下列其中一個動作：</span><span class="sxs-lookup"><span data-stu-id="65e5f-146">In Report Manager, navigate to the **Contents** page and do one of the following:</span></span>  
  
    -   <span data-ttu-id="65e5f-147">導覽至共用資料來源項目。</span><span class="sxs-lookup"><span data-stu-id="65e5f-147">Navigate to the shared data source item.</span></span>  
  
         <span data-ttu-id="65e5f-148">按一下項目來開啟它。</span><span class="sxs-lookup"><span data-stu-id="65e5f-148">Click the item to open it.</span></span> <span data-ttu-id="65e5f-149">[一般屬性] 頁面隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="65e5f-149">The General Properties page opens.</span></span>  
  
         <span data-ttu-id="65e5f-150">按一下 [刪除]\*\*\*\*，然後按一下 [確定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="65e5f-150">Click **Delete**, and then click **OK**.</span></span>  
  
    -   <span data-ttu-id="65e5f-151">在 [內容]\*\*\*\* 頁面中，巡覽至包含您要刪除之資料來源的資料夾。</span><span class="sxs-lookup"><span data-stu-id="65e5f-151">In the **Contents** page, navigate to the folder that contains the data source you want to delete.</span></span>  
  
         <span data-ttu-id="65e5f-152">將滑鼠停留在該項目上，按一下下拉式清單，然後在操作功能表中按一下 [刪除]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="65e5f-152">Hover over the item, click the drop-down list, and from the context menu, click **Delete**.</span></span>  
  
         [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="65e5f-153">另請參閱</span><span class="sxs-lookup"><span data-stu-id="65e5f-153">See Also</span></span>  
 <span data-ttu-id="65e5f-154">[Reporting Services 中的資料連線、資料來源及連接字串](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="65e5f-154">[Data Connections, Data Sources, and Connection Strings in Reporting Services](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-reporting-services.md) </span></span>  
 <span data-ttu-id="65e5f-155">[[內容] 頁面 &#40;報表管理員&#41;](../../2014/reporting-services/contents-page-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="65e5f-155">[Contents Page &#40;Report Manager&#41;](../../2014/reporting-services/contents-page-report-manager.md) </span></span>  
 <span data-ttu-id="65e5f-156">[建立、修改和刪除 &#40;SSRS&#41;的共用資料來源](report-data/create-modify-and-delete-shared-data-sources-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="65e5f-156">[Create, Modify, and Delete Shared Data Sources &#40;SSRS&#41;](report-data/create-modify-and-delete-shared-data-sources-ssrs.md) </span></span>  
 <span data-ttu-id="65e5f-157">[管理報表資料來源](report-data/manage-report-data-sources.md) </span><span class="sxs-lookup"><span data-stu-id="65e5f-157">[Manage Report Data Sources](report-data/manage-report-data-sources.md) </span></span>  
 [<span data-ttu-id="65e5f-158">設定報表的資料來源屬性 &#40;報表管理員&#41;</span><span class="sxs-lookup"><span data-stu-id="65e5f-158">Configure Data Source Properties for a Report  &#40;Report Manager&#41;</span></span>](report-data/configure-data-source-properties-for-a-report-report-manager.md)  
  
  
