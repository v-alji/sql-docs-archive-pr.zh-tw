---
title: 建立報表資料來源 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: bd6662c7-ffbe-479d-8944-3dc858340998
author: minewiskan
ms.author: owend
ms.openlocfilehash: 9205eac497fc047b471f5b80becec36495474d88
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705606"
---
# <a name="create-a-report-data-source"></a><span data-ttu-id="672fd-102">建立報表資料來源</span><span class="sxs-lookup"><span data-stu-id="672fd-102">Create a Report Data Source</span></span>
  <span data-ttu-id="672fd-103">為了讓 Power View 連接到多維度模型，您必須在 SharePoint 文件庫中建立共用報表資料來源定義，也稱為 .rsds 檔。</span><span class="sxs-lookup"><span data-stu-id="672fd-103">In order for Power View to connect to a multidimensional model, you must create a shared report data source definition, also known as an .rsds file, in a SharePoint library.</span></span> <span data-ttu-id="672fd-104">.rsds 檔會指定 Analysis Services 伺服器執行個體的名稱、連接類型、連接字串，以及用來連接到多維度模型的認證。</span><span class="sxs-lookup"><span data-stu-id="672fd-104">The .rsds file specifies the name of an Analysis Services server instance, connection type, connection string, and credentials used to connect to the multidimensional model.</span></span> <span data-ttu-id="672fd-105">當使用者按下 .rsds 時，新的空白 Power View 報表 (.rdlx 檔) 就會在瀏覽器中開啟。</span><span class="sxs-lookup"><span data-stu-id="672fd-105">When a user clicks on the .rsds, a new blank Power View report (an .rdlx file) opens in the browser.</span></span>  
  
 <span data-ttu-id="672fd-106">若要建立 .rsds 連接，您必須已安裝 SQL Server 2012 (或更新版本) Reporting Services 以及適用於 SharePoint 2010 或 SharePoint 2013 的 Reporting Services 增益集。</span><span class="sxs-lookup"><span data-stu-id="672fd-106">In order to create an .rsds connection, you must have SQL Server 2012 (or later) Reporting Services and the Reporting Services add-in for SharePoint 2010 or SharePoint 2013 installed.</span></span>  
  
## <a name="create-a-report-data-source-rsds-connection-to-a-multidimensional-model"></a><span data-ttu-id="672fd-107">建立多維度模型的報表資料來源 (.rsds) 連接</span><span class="sxs-lookup"><span data-stu-id="672fd-107">Create a Report Data Source (.rsds) connection to a multidimensional model</span></span>  
 <span data-ttu-id="672fd-108">在開始進行之前，您需要先了解：</span><span class="sxs-lookup"><span data-stu-id="672fd-108">Before you begin, you need to know:</span></span>  
  
-   <span data-ttu-id="672fd-109">以多維度模式執行之 Analysis Services 伺服器執行個體的名稱。</span><span class="sxs-lookup"><span data-stu-id="672fd-109">The name of the Analysis Services server instance running in Multidimensional mode.</span></span>  
  
-   <span data-ttu-id="672fd-110">要連接的多維度資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="672fd-110">The name of the multidimensional database you want to connect to.</span></span>  
  
-   <span data-ttu-id="672fd-111">Cube 的名稱 (如果有多個的話)。</span><span class="sxs-lookup"><span data-stu-id="672fd-111">The name of the cube, if there is more than one.</span></span>  
  
-   <span data-ttu-id="672fd-112">(選擇性) 檢視方塊名稱。</span><span class="sxs-lookup"><span data-stu-id="672fd-112">(Optional) Perspective name.</span></span>  
  
-   <span data-ttu-id="672fd-113">(選擇性) 地區設定識別碼。</span><span class="sxs-lookup"><span data-stu-id="672fd-113">(Optional) Locale Identifier.</span></span>  
  
#### <a name="to-create-a-shared-report-data-source-rsds-file-sharepoint-2010"></a><span data-ttu-id="672fd-114">若要建立共用報表資料來源 (.rsds) 檔案 (SharePoint 2010)</span><span class="sxs-lookup"><span data-stu-id="672fd-114">To create a shared Report Data Source (.rsds) file (SharePoint 2010)</span></span>  
  
1.  <span data-ttu-id="672fd-115">按一下文件庫功能區上的 [文件]\*\*\*\* 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="672fd-115">Click the **Documents** tab on the library ribbon.</span></span>  
  
2.  <span data-ttu-id="672fd-116">按一下 [**新增檔**] [報表] [  >  **資料來源**]。</span><span class="sxs-lookup"><span data-stu-id="672fd-116">Click **New Document** > **Report Data Source**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="672fd-117">如果您沒有在功能表上看見 [報表資料來源]\*\*\*\* 項目，表示此文件庫的報表資料來源內容類型尚未啟用。</span><span class="sxs-lookup"><span data-stu-id="672fd-117">If you do not see the **Report Data Source** item on the menu, the report data source content type has not been enabled for this library.</span></span> <span data-ttu-id="672fd-118">如需詳細資訊，請參閱[將報表伺服器內容類型加入至程式庫 &#40;SharePoint 整合模式中的 Reporting Services&#41;](../../reporting-services/add-reporting-services-content-types-to-a-sharepoint-library.md)。</span><span class="sxs-lookup"><span data-stu-id="672fd-118">For more information, see [Add Report Server Content Types to a Library &#40;Reporting Services in SharePoint Integrated Mode&#41;](../../reporting-services/add-reporting-services-content-types-to-a-sharepoint-library.md).</span></span>  
  
3.  <span data-ttu-id="672fd-119">在 [資料來源屬性]\*\*\*\* 頁面的 [名稱]\*\*\*\* 中，輸入連接 .rsds 檔案的名稱。</span><span class="sxs-lookup"><span data-stu-id="672fd-119">On the **Data Source Properties** page, in **Name**, type a name for the connection .rsds file.</span></span>  
  
4.  <span data-ttu-id="672fd-120">在 [資料來源類型]\*\*\*\* 中，選取 [Power View 的 Microsoft 商業智慧語意模型]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="672fd-120">In **Data Source Type**, select **Microsoft BI Semantic Model for Power View**.</span></span>  
  
5.  <span data-ttu-id="672fd-121">在 [連接字串]\*\*\*\* 中，指定 Analysis Services 伺服器名稱、資料庫名稱、Cube 名稱及任何選擇性設定。</span><span class="sxs-lookup"><span data-stu-id="672fd-121">In **Connection String**, specify the Analysis Services server name, database name, cube name, and any optional settings.</span></span>  
  
     <span data-ttu-id="672fd-122">連接字串： `Data source=<servername>;initial catalog=<multidimensionaldatabasename>-ee;cube='<cubename>'`</span><span class="sxs-lookup"><span data-stu-id="672fd-122">Connection String: `Data source=<servername>;initial catalog=<multidimensionaldatabasename>-ee;cube='<cubename>'`</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="672fd-123">如果有多個 Cube，則必須指定 Cube 名稱。</span><span class="sxs-lookup"><span data-stu-id="672fd-123">If there is more than one cube, you must specify a cube name.</span></span>  
  
     <span data-ttu-id="672fd-124">(選擇性) Cube 可以包含檢視方塊，為使用者提供在用戶端中只看到某些維度和/或量值群組的精選檢視。</span><span class="sxs-lookup"><span data-stu-id="672fd-124">(Optional) Cubes can have perspectives that provide users a select view where only certain dimensions and/or measure groups are visible in the client.</span></span> <span data-ttu-id="672fd-125">若要指定檢視方塊，請輸入檢視方塊名稱做為 Cube 屬性的值： `Data source=<servername>;initial catalog=<multidimensionaldatabasename>-ee;cube='<perspectivename>'`</span><span class="sxs-lookup"><span data-stu-id="672fd-125">To specify a perspective, enter the perspective name as a value to the Cube property: `Data source=<servername>;initial catalog=<multidimensionaldatabasename>-ee;cube='<perspectivename>'`</span></span>  
  
     <span data-ttu-id="672fd-126">(選擇性) 在模型中，可以指定各種語言的 Cube 中繼資料和資料翻譯。</span><span class="sxs-lookup"><span data-stu-id="672fd-126">(Optional) Cubes can have metadata and data translations specified for various languages within the model.</span></span> <span data-ttu-id="672fd-127">若要查看翻譯 (的資料和中繼資料) 您必須將 [地區設定識別碼] 屬性加入至連接字串：`Data source=<servername>;initial catalog=<multidimensionaldatabasename>-ee;cube='<cubename>'; Locale Identifier=<identifier number>`</span><span class="sxs-lookup"><span data-stu-id="672fd-127">In order to see the translations (data and metadata) you need to add the "Locale Identifier" property to the connection string: `Data source=<servername>;initial catalog=<multidimensionaldatabasename>-ee;cube='<cubename>'; Locale Identifier=<identifier number>`</span></span>  
  
6.  <span data-ttu-id="672fd-128">在 [認證]\*\*\*\* 中，指定報表伺服器取得認證來存取外部資料來源的方式。</span><span class="sxs-lookup"><span data-stu-id="672fd-128">In **Credentials**, specify how the report server obtains credentials to access the external data source.</span></span>  
  
    -   <span data-ttu-id="672fd-129">如果您想要使用開啟報表之使用者的認證來存取資料，請選取 [Windows 驗證 (整合式)]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="672fd-129">Select **Windows authentication (integrated)** if you want to access the data using the credentials of the user who opened the report.</span></span> <span data-ttu-id="672fd-130">如果 SharePoint 網站或伺服陣列使用表單驗證或透過受信任帳戶連接到報表伺服器，請勿選取這個選項。</span><span class="sxs-lookup"><span data-stu-id="672fd-130">Do not select this option if the SharePoint site or farm uses forms authentication or connects to the report server through a trusted account.</span></span> <span data-ttu-id="672fd-131">如果您想要排程這個報表的訂閱或資料處理，請勿選取這個選項。</span><span class="sxs-lookup"><span data-stu-id="672fd-131">Do not select this option if you want to schedule subscription or data processing for this report.</span></span> <span data-ttu-id="672fd-132">在針對網域啟用 Kerberos 驗證時，或者資料來源與報表伺服器是在同一部電腦上時，此選項具有最佳的效能。</span><span class="sxs-lookup"><span data-stu-id="672fd-132">This option works best when Kerberos authentication is enabled for your domain, or when the data source is on the same computer as the report server.</span></span> <span data-ttu-id="672fd-133">如果未啟用 Kerberos 驗證，Windows 認證只能傳遞至一部其他電腦。</span><span class="sxs-lookup"><span data-stu-id="672fd-133">If Kerberos authentication is not enabled, Windows credentials can only be passed to one other computer.</span></span> <span data-ttu-id="672fd-134">這表示，如果外部資料來源位於另一部需要其他連接的電腦上，您就會收到錯誤而非所預期的資料。</span><span class="sxs-lookup"><span data-stu-id="672fd-134">This means that if the external data source is on another computer, requiring an additional connection, you will get an error instead of the data you expect.</span></span>  
  
    -   <span data-ttu-id="672fd-135">如果您希望使用者在每次執行報表時輸入自己的認證，請選取 [提示認證]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="672fd-135">Select **Prompt for credentials** if you want the user to enter his or her credentials each time he or she runs the report.</span></span> <span data-ttu-id="672fd-136">如果您想要排程這個報表的訂閱或資料處理，請勿選取這個選項。</span><span class="sxs-lookup"><span data-stu-id="672fd-136">Do not select this option if you want to schedule subscription or data processing for this report.</span></span>  
  
    -   <span data-ttu-id="672fd-137">如果您想要使用單一認證集來存取這個資料，請選取 [預存認證]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="672fd-137">Select **Stored credentials** if you want to access the data using a single set of credentials.</span></span> <span data-ttu-id="672fd-138">認證會先經過加密，然後再儲存。</span><span class="sxs-lookup"><span data-stu-id="672fd-138">The credentials are encrypted before they are stored.</span></span> <span data-ttu-id="672fd-139">您可以選取決定預存認證之驗證方式的選項。</span><span class="sxs-lookup"><span data-stu-id="672fd-139">You can select options that determine how the stored credentials are authenticated.</span></span> <span data-ttu-id="672fd-140">如果預存認證屬於 Windows 使用者帳戶，請選取 [當做 Windows 認證使用]。</span><span class="sxs-lookup"><span data-stu-id="672fd-140">Select Use as Windows credentials if the stored credentials belong to a Windows user account.</span></span> <span data-ttu-id="672fd-141">如果您想在資料庫伺服器上設定執行內容，請選取 [設定執行內容到這個帳戶]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="672fd-141">Select **Set execution context to this account** if you want to set the execution context on the database server.</span></span>  
  
    -   <span data-ttu-id="672fd-142">如果您在連接字串中指定認證，或是想要使用最低權限帳戶來執行報表，請選取 [不需要認證]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="672fd-142">Select **Credentials are not required** if you specify credentials in the connection string, or if you want to run the report using a least-privilege account.</span></span>  
  
7.  <span data-ttu-id="672fd-143">按一下 [測試連接]\*\*\*\* 進行驗證。</span><span class="sxs-lookup"><span data-stu-id="672fd-143">Click **Test Connection** to validate.</span></span>  
  
8.  <span data-ttu-id="672fd-144">如果您想要讓資料來源成為使用中，請選取 [啟用此資料來源]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="672fd-144">Select **Enable this data source** if you want the data source to be active.</span></span> <span data-ttu-id="672fd-145">如果資料來源已設定，但是非使用中，當使用者嘗試建立報表時，就會收到錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="672fd-145">If the data source is configured but not active, users will receive an error message when they attempt to create a report.</span></span>  
  
  
