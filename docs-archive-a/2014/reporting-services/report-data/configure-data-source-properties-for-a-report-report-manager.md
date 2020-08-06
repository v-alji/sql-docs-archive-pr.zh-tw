---
title: 設定報表的資料來源屬性 (報表管理員) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- data sources [Reporting Services], embedded
ms.assetid: 27af5195-c845-40e0-9a9c-efe569424022
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 42969b4667dd71e4c6413f38e4deadb96491169c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592460"
---
# <a name="configure-data-source-properties-for-a-report--report-manager"></a><span data-ttu-id="322b2-102">設定報表的資料來源屬性 (報表管理員)</span><span class="sxs-lookup"><span data-stu-id="322b2-102">Configure Data Source Properties for a Report  (Report Manager)</span></span>
  <span data-ttu-id="322b2-103">當您執行報表時，報表伺服器會擷取屬性資訊來判斷如何連接至資料來源。</span><span class="sxs-lookup"><span data-stu-id="322b2-103">When you run a report, the report server retrieves property information to determine how to connect to a data source.</span></span> <span data-ttu-id="322b2-104">資料來源類型、連接字串和認證資訊都是在已發行報表的 [資料來源] 屬性頁面中指定的。</span><span class="sxs-lookup"><span data-stu-id="322b2-104">The data source type, connection string, and credential information are specified in the Data Source property pages of the published report.</span></span> <span data-ttu-id="322b2-105">您可以設定這些屬性，讓資料來源連接資訊與建立報表時所指定的原始值不同。</span><span class="sxs-lookup"><span data-stu-id="322b2-105">You can set the properties to vary the data source connection information from the original values that were specified when the report was created.</span></span>  
  
 <span data-ttu-id="322b2-106">或者，如果您擁有已經指定您想要使用之連接資訊的預先定義共用資料來源，就可以改為指定此共用資料來源。</span><span class="sxs-lookup"><span data-stu-id="322b2-106">Alternatively, if you have a predefined shared data source that already specifies the connection information you want to use, you can specify a shared data source instead.</span></span> <span data-ttu-id="322b2-107">若要使用共用資料來源，請在報表的 [資料來源] 屬性頁面上，按一下 **[共用資料來源]** 。</span><span class="sxs-lookup"><span data-stu-id="322b2-107">To use a shared data source, click **A shared data source** on the Data Source properties page of the report.</span></span>  
  
### <a name="to-configure-an-embedded-data-source"></a><span data-ttu-id="322b2-108">若要設定內嵌資料來源</span><span class="sxs-lookup"><span data-stu-id="322b2-108">To configure an embedded data source</span></span>  
  
1.  <span data-ttu-id="322b2-109">啟動 [報表管理員 &#40;SSRS 原生模式&#41;](../report-manager-ssrs-native-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="322b2-109">Start [Report Manager  &#40;SSRS Native Mode&#41;](../report-manager-ssrs-native-mode.md).</span></span>  
  
2.  <span data-ttu-id="322b2-110">在報表管理員中，導覽至 **[內容]** 頁面。</span><span class="sxs-lookup"><span data-stu-id="322b2-110">In Report Manager, navigate to the **Contents** page.</span></span> <span data-ttu-id="322b2-111">導覽至您要為其設定報表特定資料來源的報表，然後開啟報表。</span><span class="sxs-lookup"><span data-stu-id="322b2-111">Navigate to the report that you want to configure a report-specific data source for, and open the report.</span></span>  
  
3.  <span data-ttu-id="322b2-112">按一下 [**屬性**] 索引標籤。[**一般**屬性] 頁面隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="322b2-112">Click the **Properties** tab. The **General** properties page opens.</span></span>  
  
4.  <span data-ttu-id="322b2-113">按一下 [**資料來源**] 索引標籤。這會開啟報表的 [資料來源屬性] 頁面。</span><span class="sxs-lookup"><span data-stu-id="322b2-113">Click the **Data Sources** tab. This opens the Data Source properties page of the report.</span></span>  
  
5.  <span data-ttu-id="322b2-114">按一下 **[自訂資料來源]** ，即可在報表內部指定資料來源連接資訊。</span><span class="sxs-lookup"><span data-stu-id="322b2-114">Click **A custom data source** to specify data source connection information within the report.</span></span>  
  
6.  <span data-ttu-id="322b2-115">在 **[連接類型]** 清單中，指定用來處理資料來源中之資料的資料處理延伸模組。</span><span class="sxs-lookup"><span data-stu-id="322b2-115">In the **Connection Type** list, specify the data processing extension that is used to process data from the data source.</span></span>  
  
7.  <span data-ttu-id="322b2-116">針對 [**連接字串**]，請指定報表伺服器用來連接到資料來源的連接字串。</span><span class="sxs-lookup"><span data-stu-id="322b2-116">For **Connection String**, specify the connection string that the report server uses to connect to the data source.</span></span> <span data-ttu-id="322b2-117">建議您不要在連接字串中指定認證。</span><span class="sxs-lookup"><span data-stu-id="322b2-117">It is recommended that you do not specify credentials in the connection string.</span></span>  
  
     <span data-ttu-id="322b2-118">下列範例說明用來連接到本機資料庫的連接字串 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] ：</span><span class="sxs-lookup"><span data-stu-id="322b2-118">The following example illustrates a connection string for connecting to the local [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database:</span></span>  
  
    ```  
    data source=<localservername>; initial catalog=AdventureWorks2012  
    ```  
  
8.  <span data-ttu-id="322b2-119">針對 **[使用下列方式連接]**，指定報表執行時要如何取得認證：</span><span class="sxs-lookup"><span data-stu-id="322b2-119">For **Connect using**, specify how credentials are obtained when the report runs:</span></span>  
  
    -   <span data-ttu-id="322b2-120">如果您要提示使用者輸入登入名稱和密碼，請按一下 **[執行報表的使用者所提供的認證]**。</span><span class="sxs-lookup"><span data-stu-id="322b2-120">If you want to prompt the user for a logon name and password, click **Credentials supplied by the user running the report**.</span></span>  
  
    -   <span data-ttu-id="322b2-121">如果您打算在具有支援訂閱或其他已排程之作業的報表 (例如自動化報表記錄產生) 中使用資料來源，請按一下 [安全地儲存在報表伺服器中的認證]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="322b2-121">If you intend to use the data source with reports that support subscriptions or other scheduled operations (such as automated report history generation), click **Credentials stored securely in the report server**.</span></span>  
  
    -   <span data-ttu-id="322b2-122">對於存取報表的使用者提供的認證，若要讓報表伺服器將認證傳送給主控外部資料來源的伺服器，請按一下 **[Windows 整合式安全性]**。</span><span class="sxs-lookup"><span data-stu-id="322b2-122">If you want the report server to pass the credentials of the user accessing the report to the server hosting the external data source, click **Windows Integrated Security**.</span></span> <span data-ttu-id="322b2-123">在此情況下，不會提示使用者輸入使用者名稱或密碼。</span><span class="sxs-lookup"><span data-stu-id="322b2-123">In this case, the user is not prompted to type a user name or password.</span></span>  
  
    -   <span data-ttu-id="322b2-124">如果資料來源沒有使用認證 (例如，如果資料來源是從檔案系統存取的 XML 檔)，請按一下 [不需要認證]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="322b2-124">If the data source does not use credentials (for example, if the data source is an XML file that is accessed from the file system), click **Credentials are not required**.</span></span> <span data-ttu-id="322b2-125">只有當這種認證類型適用於資料來源時，您才應該指定此認證類型。</span><span class="sxs-lookup"><span data-stu-id="322b2-125">You should only specify this credential type if it is valid for the data source.</span></span> <span data-ttu-id="322b2-126">如果您針對需要驗證的資料來源選取此選項，連接將會失敗。</span><span class="sxs-lookup"><span data-stu-id="322b2-126">If you select this option for a data source that requires authentication, the connection will fail.</span></span> <span data-ttu-id="322b2-127">如果您選取此選項，請務必設定自動執行帳戶，以便在使用者認證無法使用時，允許報表伺服器連接至其他電腦以擷取資料或檔案。</span><span class="sxs-lookup"><span data-stu-id="322b2-127">If you select this option, be sure to configure the unattended execution account that allows the report server to connect to other computers to retrieve data or files when user credentials are not available.</span></span>  
  
 <span data-ttu-id="322b2-128">如需設定認證的詳細資訊，請參閱 [指定報表資料來源的認證及連接資訊](specify-credential-and-connection-information-for-report-data-sources.md)。</span><span class="sxs-lookup"><span data-stu-id="322b2-128">For more information about configuring credentials, see [Specify Credential and Connection Information for Report Data Sources](specify-credential-and-connection-information-for-report-data-sources.md).</span></span> <span data-ttu-id="322b2-129">如需自動執行帳戶的詳細資訊，請參閱[設定自動執行帳戶 &#40;SSRS 設定管理員&#41;](../install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="322b2-129">For more information about the unattended execution account, see [Configure the Unattended Execution Account &#40;SSRS Configuration Manager&#41;](../install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="322b2-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="322b2-130">See Also</span></span>  
 <span data-ttu-id="322b2-131">[[內容] 頁面 &#40;報表管理員&#41;](../contents-page-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="322b2-131">[Contents Page &#40;Report Manager&#41;](../contents-page-report-manager.md) </span></span>  
 <span data-ttu-id="322b2-132">[新增資料來源頁面 &#40;報表管理員&#41;](../new-data-source-page-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="322b2-132">[New Data Source Page &#40;Report Manager&#41;](../new-data-source-page-report-manager.md) </span></span>  
 <span data-ttu-id="322b2-133">[建立、修改和刪除 &#40;SSRS&#41;的共用資料來源](create-modify-and-delete-shared-data-sources-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="322b2-133">[Create, Modify, and Delete Shared Data Sources &#40;SSRS&#41;](create-modify-and-delete-shared-data-sources-ssrs.md) </span></span>  
 <span data-ttu-id="322b2-134">[管理報表資料來源](manage-report-data-sources.md) </span><span class="sxs-lookup"><span data-stu-id="322b2-134">[Manage Report Data Sources](manage-report-data-sources.md) </span></span>  
 <span data-ttu-id="322b2-135">[建立、刪除或修改共用資料來源 &#40;報表管理員&#41;](../create-delete-or-modify-a-shared-data-source-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="322b2-135">[Create, Delete, or Modify a Shared Data Source &#40;Report Manager&#41;](../create-delete-or-modify-a-shared-data-source-report-manager.md) </span></span>  
 [<span data-ttu-id="322b2-136">資料來源屬性頁面 &#40;報表管理員&#41;</span><span class="sxs-lookup"><span data-stu-id="322b2-136">Data Sources Properties Page &#40;Report Manager&#41;</span></span>](../data-sources-properties-page-report-manager.md)  
  
  
