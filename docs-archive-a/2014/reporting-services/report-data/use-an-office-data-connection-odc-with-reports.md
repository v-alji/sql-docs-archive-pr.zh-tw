---
title: 使用 Office 資料連線 ( .odc) 與 SharePoint 整合模式中的報表 (Reporting Services) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- Office Data Connection (.odc) files
- SharePoint integration [Reporting Services], shared data sources
- .odc files
ms.assetid: e8d6896d-f886-4390-8b5d-96f0a50c250c
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d795c46f46b45511079ac03add2d18214ac54489
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585053"
---
# <a name="use-an-office-data-connection-odc-with-reports-reporting-services-in-sharepoint-integrated-mode"></a><span data-ttu-id="c6772-102">搭配報表使用 Office 資料連線 (.odc) (SharePoint 整合模式的 Reporting Services)</span><span class="sxs-lookup"><span data-stu-id="c6772-102">Use an Office Data Connection (.odc) with Reports (Reporting Services in SharePoint Integrated Mode)</span></span>
  <span data-ttu-id="c6772-103">在少數情況下，您可以使用現有的 Office 資料連線 (.odc) 檔案來提供連接資訊給 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 報表。</span><span class="sxs-lookup"><span data-stu-id="c6772-103">For limited scenarios, you can use an existing Office Data Connection (.odc) file to provide connection information to a [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] report.</span></span> <span data-ttu-id="c6772-104">建立共用資料來源時，您可以使用 .odc 檔案來取代 .rsds 檔案。</span><span class="sxs-lookup"><span data-stu-id="c6772-104">An .odc file can be used in place of an .rsds file when you create a shared data source.</span></span> <span data-ttu-id="c6772-105">報表伺服器使用 .odc 檔案的方式與使用 .rsds 檔案相同。報表伺服器會讀取檔案，找出資料來源類型、連接字串和認證資訊。</span><span class="sxs-lookup"><span data-stu-id="c6772-105">The report server uses an .odc file in the same way it uses an .rsds file; it reads the file for the data source type, a connection string, and credential information.</span></span>  
  
 <span data-ttu-id="c6772-106">並非所有 .odc 檔案都可用於 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 報表。</span><span class="sxs-lookup"><span data-stu-id="c6772-106">Not all .odc files can be used with a [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] report.</span></span> <span data-ttu-id="c6772-107">.odc 可用與否取決於資料處理延伸模組以及報表和 .odc 檔案的特性：</span><span class="sxs-lookup"><span data-stu-id="c6772-107">The data processing extension and characteristics of the report and .odc file determine whether an .odc can be used:</span></span>  
  
-   <span data-ttu-id="c6772-108">報表必須設計成可以使用 OLE DB 或 ODBC 資料提供者。</span><span class="sxs-lookup"><span data-stu-id="c6772-108">The report must be designed to work with an OLE DB or ODBC data provider.</span></span> <span data-ttu-id="c6772-109">如果您使用不同的資料處理延伸模組建立報表，則報表及其查詢可能會包含 OLE DB 或 ODBC 資料提供者不支援的功能。</span><span class="sxs-lookup"><span data-stu-id="c6772-109">If you used a different data processing extension to create the report, the report or its queries might include functionality that is not supported by the OLE DB or ODBC data provider.</span></span>  
  
-   <span data-ttu-id="c6772-110">.odc 檔案必須擁有必要的元素和結構。</span><span class="sxs-lookup"><span data-stu-id="c6772-110">The .odc file must have the expected elements and structure.</span></span> <span data-ttu-id="c6772-111">檔案中必須明確設定資料提供者和認證設定，以供報表伺服器讀取。</span><span class="sxs-lookup"><span data-stu-id="c6772-111">The data provider and credential settings must be set explicitly in the file so that they can be read by the report server.</span></span> <span data-ttu-id="c6772-112">設定這些值的最佳方式是先匯出 .odc 檔案，再將檔案上傳到 SharePoint 程式庫。</span><span class="sxs-lookup"><span data-stu-id="c6772-112">The best way to set these values is to export the .odc file before uploading it to the SharePoint library.</span></span>  
  
-   <span data-ttu-id="c6772-113">.odc 檔案必須指定 OLE DB 或 ODBC 連接類型。</span><span class="sxs-lookup"><span data-stu-id="c6772-113">The .odc file must specify a connection type of OLE DB or ODBC.</span></span>  
  
-   <span data-ttu-id="c6772-114">.odc 檔案必須指定連接字串。</span><span class="sxs-lookup"><span data-stu-id="c6772-114">The .odc file must specify a connection string.</span></span>  
  
-   <span data-ttu-id="c6772-115">認證可設定為 `None`、`Stored` 或 `Integrated`。</span><span class="sxs-lookup"><span data-stu-id="c6772-115">Credentials can be set to `None`, `Stored`, or `Integrated`.</span></span> <span data-ttu-id="c6772-116">如果認證方法設定為 `Stored`，報表伺服器將會提示使用者輸入認證，而不會使用預存認證。</span><span class="sxs-lookup"><span data-stu-id="c6772-116">If the credentials method is set to `Stored`, the report server will prompt the user for credentials instead of using the stored credentials.</span></span> <span data-ttu-id="c6772-117">報表伺服器無法依照 .odc 檔案的定義使用預存認證。</span><span class="sxs-lookup"><span data-stu-id="c6772-117">The report server cannot use stored credentials as defined in the .odc file.</span></span>  
  
-   <span data-ttu-id="c6772-118">資料來源擁有的結構描述必須與用來建立報表的結構描述相同。</span><span class="sxs-lookup"><span data-stu-id="c6772-118">The data source must have schema that is identical to the one used to create the report.</span></span> <span data-ttu-id="c6772-119">如果資料結構不同，報表便無法執行。</span><span class="sxs-lookup"><span data-stu-id="c6772-119">If the data structures are different, the report will not run.</span></span>  
  
-   <span data-ttu-id="c6772-120">您必須在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Office 2007 (舊版 .odc 與報表定義檔不相容) 中建立此 .odc 檔案。</span><span class="sxs-lookup"><span data-stu-id="c6772-120">The .odc file must be created in [!INCLUDE[msCoName](../../includes/msconame-md.md)] Office 2007 (older versions of .odc are not compatible with report definition files).</span></span>  
  
 <span data-ttu-id="c6772-121">即使 .odc 資料來源類型看起來和支援的資料來源類型非常相似，您使用的 .odc 檔案也不能指定無法在報表伺服器上處理之資料來源的連接。</span><span class="sxs-lookup"><span data-stu-id="c6772-121">You cannot use .odc files that specify connections to data sources that cannot be processed on a report server, even if the .odc data source types look similar to supported data source types.</span></span> <span data-ttu-id="c6772-122">具體而言，如果您在 Microsoft Excel 2007 中建立了從 Microsoft Access、網路或文字檔擷取資料的 .odc 檔案，便無法使用該 .odc 檔案來提供資料給報表。</span><span class="sxs-lookup"><span data-stu-id="c6772-122">Specifically, if you created an .odc file in Microsoft Excel 2007 that retrieves data from Microsoft Access, the Web, or a text file, you cannot use that .odc file to provide data to a report.</span></span>  
  
 <span data-ttu-id="c6772-123">報表產生器報表及模型無法使用 .odc 檔案。</span><span class="sxs-lookup"><span data-stu-id="c6772-123">Report Builder reports and models do not work with .odc file.</span></span> <span data-ttu-id="c6772-124">您不能使用 .odc 檔案產生模型，也不能將模型設定為使用連結到 .odc 檔案的共用資料來源。</span><span class="sxs-lookup"><span data-stu-id="c6772-124">You cannot use an .odc file to generate a model, and you cannot configure the model to use a shared data source that links to an .odc file.</span></span>  
  
 <span data-ttu-id="c6772-125">如果您不熟悉 .odc 檔案，可以依照下列指示來建立及匯出檔案。</span><span class="sxs-lookup"><span data-stu-id="c6772-125">If you are not familiar with .odc files, you can use the following instructions to create and export one.</span></span> <span data-ttu-id="c6772-126">為 OLE DB 資料來源建立 .odc 檔案的簡單方式為使用 Excel 2007 和資料連線精靈。</span><span class="sxs-lookup"><span data-stu-id="c6772-126">One easy way to create an .odc file for an OLE DB data source is to use Excel 2007 and the Data Connection Wizard.</span></span> <span data-ttu-id="c6772-127">但請注意，這個精靈並不會建立資料來源，您必須擁有已經定義的外部資料來源。</span><span class="sxs-lookup"><span data-stu-id="c6772-127">Note that the wizard does not create a data source; you must have an external data source that is already defined.</span></span>  
  
 <span data-ttu-id="c6772-128">現有的 .odc 檔案必須與報表與查詢完全相容，您才能使用該檔案。</span><span class="sxs-lookup"><span data-stu-id="c6772-128">An existing .odc file should only be used if it is fully compatible with the report and queries.</span></span> <span data-ttu-id="c6772-129">如果發生需要大幅修改報表或 .odc 檔案的錯誤，則應為報表建立新的 .rsds 檔案。</span><span class="sxs-lookup"><span data-stu-id="c6772-129">If you run into errors that require significant modifications to either the report or to the .odc file, you should create a new .rsds file for the report.</span></span> <span data-ttu-id="c6772-130">如需如何建立使用 .rsds 檔案之共用資料來源的詳細資訊，請參閱[建立和管理共用資料來源 &#40;SharePoint 整合模式的 Reporting Services&#41;](../create-manage-shared-data-sources-reporting-services-sharepoint-integrated-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="c6772-130">For more information about how to create a shared data source that uses an .rsds file, see [Create and Manage Shared Data Sources &#40;Reporting Services in SharePoint Integrated Mode&#41;](../create-manage-shared-data-sources-reporting-services-sharepoint-integrated-mode.md).</span></span>  
  
### <a name="to-create-and-export-an-odc-file"></a><span data-ttu-id="c6772-131">建立及匯出 .odc 檔案</span><span class="sxs-lookup"><span data-stu-id="c6772-131">To create and export an .odc file</span></span>  
  
1.  <span data-ttu-id="c6772-132">啟動 Excel 2007。</span><span class="sxs-lookup"><span data-stu-id="c6772-132">Start Excel 2007.</span></span>  
  
2.  <span data-ttu-id="c6772-133">在 [資料]  索引標籤的 [取得外部資料]  群組中，按一下 [從其他來源]  ，然後按一下 [從資料連線精靈]  。</span><span class="sxs-lookup"><span data-stu-id="c6772-133">On the **Data** tab, in the **Get External Data** group, click **From Other Sources**, and then click **From Data Connection Wizard**.</span></span>  
  
3.  <span data-ttu-id="c6772-134">選取 [其他/進階]  ，然後按一下 [下一步]  。</span><span class="sxs-lookup"><span data-stu-id="c6772-134">Select **Other/Advanced**, and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="c6772-135">選取 [Microsoft OLE DB Provider for SQL Server]  ，然後按一下 [下一步]  。</span><span class="sxs-lookup"><span data-stu-id="c6772-135">Select **Microsoft OLE DB Provider for SQL Server**, and then click **Next**.</span></span>  
  
5.  <span data-ttu-id="c6772-136">輸入伺服器的名稱 (根據預設，此名稱為電腦的網路名稱) 以及具備有效登入和資料庫權限的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="c6772-136">Enter the name of the server (by default, it is the network name of the computer) and a user account that has a valid login and database permissions.</span></span> <span data-ttu-id="c6772-137">按 [下一步]  。</span><span class="sxs-lookup"><span data-stu-id="c6772-137">Click **Next**.</span></span>  
  
6.  <span data-ttu-id="c6772-138">選取資料庫，然後按一下 [確定]  關閉 [資料連結]  對話方塊。</span><span class="sxs-lookup"><span data-stu-id="c6772-138">Select a database, and then click **OK** to close the **Data Link** dialog box.</span></span>  
  
7.  <span data-ttu-id="c6772-139">[連線至特定資料表]  核取方塊為預設選取項目，</span><span class="sxs-lookup"><span data-stu-id="c6772-139">The **Connect to specific table** check box is selected by default.</span></span> <span data-ttu-id="c6772-140">並且用來結取特定資料表中的資料。</span><span class="sxs-lookup"><span data-stu-id="c6772-140">It is used to retrieve data from a specific table.</span></span> <span data-ttu-id="c6772-141">報表伺服器會忽略 .odc 檔案中的所有查詢，因此不論您選取或清除這個核取方塊都不會有影響。</span><span class="sxs-lookup"><span data-stu-id="c6772-141">The report server ignores all queries in an .odc file, so it does not matter whether you select or clear the check box.</span></span> <span data-ttu-id="c6772-142">為報表擷取資料的查詢會包含在報表定義檔案中，而非外部檔案中。</span><span class="sxs-lookup"><span data-stu-id="c6772-142">Queries that retrieve data for a report are included in a report definition file and not in external files.</span></span>  
  
8.  <span data-ttu-id="c6772-143">當連線開啟時，您可以編輯屬性並將它匯出。</span><span class="sxs-lookup"><span data-stu-id="c6772-143">While the connection is open, you can edit properties and export it.</span></span> <span data-ttu-id="c6772-144">請在 [資料]  索引標籤的 [連線]  群組中，按一下 [屬性]  ，然後按一下連線名稱旁的 [連線屬性]  按鈕。</span><span class="sxs-lookup"><span data-stu-id="c6772-144">On the **Data** tab, in the **Connections** group, click **Properties**, and then click the **Connection Properties** button next to the connection name.</span></span>  
  
9. <span data-ttu-id="c6772-145">在 [定義]  索引標籤上，按一下[匯出連線檔案]  。</span><span class="sxs-lookup"><span data-stu-id="c6772-145">On the **Definition** tab, click **Export Connection File**.</span></span>  
  
10. <span data-ttu-id="c6772-146">輸入檔案名稱，然後按一下 [儲存]  。</span><span class="sxs-lookup"><span data-stu-id="c6772-146">Enter a name for the file, and then click **Save**.</span></span> <span data-ttu-id="c6772-147">接著關閉應用程式和所有已開啟的檔案。</span><span class="sxs-lookup"><span data-stu-id="c6772-147">Close the application and all open files.</span></span>  
  
### <a name="to-upload-and-use-an-odc-file"></a><span data-ttu-id="c6772-148">上傳及使用 .odc 檔案</span><span class="sxs-lookup"><span data-stu-id="c6772-148">To upload and use an .odc file</span></span>  
  
1.  <span data-ttu-id="c6772-149">開啟您要上傳連接檔案的目標文件庫。</span><span class="sxs-lookup"><span data-stu-id="c6772-149">Open the library into which you want to upload the connection file.</span></span>  
  
2.  <span data-ttu-id="c6772-150">在 [上傳]  功能表上，按一下 [上傳文件]  。</span><span class="sxs-lookup"><span data-stu-id="c6772-150">On the **Upload** menu, click **Upload document**.</span></span>  
  
3.  <span data-ttu-id="c6772-151">按一下 **[瀏覽]** 。</span><span class="sxs-lookup"><span data-stu-id="c6772-151">Click **Browse**.</span></span>  
  
4.  <span data-ttu-id="c6772-152">選取您建立的 .odc 檔案。</span><span class="sxs-lookup"><span data-stu-id="c6772-152">Select the .odc file you created.</span></span> <span data-ttu-id="c6772-153">依預設，.odc 檔案位於 [我的文件] 資料夾的 [我的資料來源] 中。</span><span class="sxs-lookup"><span data-stu-id="c6772-153">By default, the .odc file is in the My Documents folder, in My Data Sources.</span></span>  
  
5.  <span data-ttu-id="c6772-154">按一下 [開啟]  選取檔案，然後按一下 [確定]  儲存所選項目。</span><span class="sxs-lookup"><span data-stu-id="c6772-154">Click **Open** to select the file, click **OK** to save the selection.</span></span> <span data-ttu-id="c6772-155">新項目的屬性頁會自動開啟。</span><span class="sxs-lookup"><span data-stu-id="c6772-155">The properties page for the new item opens automatically.</span></span>  
  
6.  <span data-ttu-id="c6772-156">在 [內容類型] 中，選取 [報表資料來源]  ，然後按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="c6772-156">In Content Type, select **Report Data Source**, and then click **OK**.</span></span>  
  
7.  <span data-ttu-id="c6772-157">指向報表。</span><span class="sxs-lookup"><span data-stu-id="c6772-157">Point to a report.</span></span>  
  
8.  <span data-ttu-id="c6772-158">按一下向下箭頭，然後選取 [管理資料來源]  。</span><span class="sxs-lookup"><span data-stu-id="c6772-158">Click the down arrow, and select **Manage Data Sources**.</span></span>  
  
9. <span data-ttu-id="c6772-159">按一下資料來源名稱。</span><span class="sxs-lookup"><span data-stu-id="c6772-159">Click the data source name.</span></span>  
  
10. <span data-ttu-id="c6772-160">如果報表使用自訂資料來源資訊，請按一下 [共用]  。</span><span class="sxs-lookup"><span data-stu-id="c6772-160">If the report uses custom data source information, click **Shared**.</span></span>  
  
11. <span data-ttu-id="c6772-161">在 [資料來源連結]  中，按一下瀏覽 ( **...** ) 按鈕。</span><span class="sxs-lookup"><span data-stu-id="c6772-161">In **Data Source Link**, click the browse (**...**) button.</span></span>  
  
12. <span data-ttu-id="c6772-162">選取剛才上傳的 .odc 檔案。</span><span class="sxs-lookup"><span data-stu-id="c6772-162">Select the .odc file you just uploaded.</span></span>  
  
13. <span data-ttu-id="c6772-163">按一下 [確定]  選取檔案，然後按一下 [確定]  儲存變更。</span><span class="sxs-lookup"><span data-stu-id="c6772-163">Click **OK** to select the file, and then click **OK** to save your changes.</span></span>  
  
     <span data-ttu-id="c6772-164">如果您使用 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 範本資料庫和範本報表嘗試執行上述步驟，請注意只有 Company Sales 報表能夠直接使用 .odc 檔案。</span><span class="sxs-lookup"><span data-stu-id="c6772-164">If you are trying these steps with the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] sample database and sample reports, be aware that only the Company Sales report will work out-of-the-box with an .odc file.</span></span> <span data-ttu-id="c6772-165">其他範例報表包含無法處理 OLE DB 提供者的查詢參數和功能。</span><span class="sxs-lookup"><span data-stu-id="c6772-165">The other sample reports contain query parameters and features that do not work with the OLE DB provider.</span></span> <span data-ttu-id="c6772-166">不過，您可以先在「報表設計師」中進行修改，使報表能夠使用 OLE DB 提供者。</span><span class="sxs-lookup"><span data-stu-id="c6772-166">However, you can make the reports work with the OLE DB provider if you modify them first in Report Designer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6772-167">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c6772-167">See Also</span></span>  
 [<span data-ttu-id="c6772-168">建立、修改和刪除共用資料來源 &#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="c6772-168">Create, Modify, and Delete Shared Data Sources &#40;SSRS&#41;</span></span>](create-modify-and-delete-shared-data-sources-ssrs.md)  
  
  
