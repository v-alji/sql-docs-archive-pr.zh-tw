---
title: 在 Reporting Services 資料來源中儲存認證 | Microsoft Docs
ms.custom: ''
ms.date: 09/23/2015
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- credentials [Reporting Services]
- security [Analysis Services], data sources
- stored credentials [Reporting Services]
- data sources [Reporting Services], stored credentials
ms.assetid: dc700922-97fa-4b30-9547-05bbbec4f09c
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: fccf8669d1f39d19a26b443ffcead8e86db66a34
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598227"
---
# <a name="store-credentials-in-a-reporting-services-data-source"></a><span data-ttu-id="15ca3-102">Store Credentials in a Reporting Services Data Source</span><span class="sxs-lookup"><span data-stu-id="15ca3-102">Store Credentials in a Reporting Services Data Source</span></span>
  <span data-ttu-id="15ca3-103">您可以設定預存認證，讓 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 報表伺服器用來存取報表的外部資料。</span><span class="sxs-lookup"><span data-stu-id="15ca3-103">You can configure stored credentials that a [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] report server uses to access external data for a report.</span></span> <span data-ttu-id="15ca3-104">如果報表會自動執行，便是使用預存認證 (例如以電子郵件形式發行報表的 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 訂閱)。</span><span class="sxs-lookup"><span data-stu-id="15ca3-104">Stored credentials are used if the report runs unattended, for example a [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] subscription that publishes a report as an e-mail.</span></span> <span data-ttu-id="15ca3-105">排定或觸發報表處理時，報表伺服器會擷取和使用認證。</span><span class="sxs-lookup"><span data-stu-id="15ca3-105">The report server retrieves and uses the credentials when report processing is scheduled or triggered.</span></span> <span data-ttu-id="15ca3-106">本主題會逐步引導您完成為原生模式和 SharePoint 模式報表伺服器設定預存認證的程序。</span><span class="sxs-lookup"><span data-stu-id="15ca3-106">This topic walks you through configuring stored credentials for both Native mode and SharePoint mode report servers.</span></span>

||
|-|
|<span data-ttu-id="15ca3-107">**[!INCLUDE[applies](../../includes/applies-md.md)]** [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 原生模式 &#124; [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] SharePoint 模式</span><span class="sxs-lookup"><span data-stu-id="15ca3-107">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] Native mode &#124; [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] SharePoint mode</span></span>|

 <span data-ttu-id="15ca3-108">**本主題內容：**</span><span class="sxs-lookup"><span data-stu-id="15ca3-108">**In this topic:**</span></span>

-   [<span data-ttu-id="15ca3-109">為報表特定的資料來源設定預存認證 (原生模式) </span><span class="sxs-lookup"><span data-stu-id="15ca3-109">Configure stored credentials for a report-specific data source (Native mode)</span></span>](#bkmk_stored_credentials_data_source_native)

-   [<span data-ttu-id="15ca3-110">為報表特定的資料來源設定預存認證 (SharePoint 模式) </span><span class="sxs-lookup"><span data-stu-id="15ca3-110">Configure stored credentials for a report-specific data source (SharePoint mode)</span></span>](#bkmk_stored_credentials_data_source_sharepoint)

-   [<span data-ttu-id="15ca3-111"> (原生模式設定共用資料來源的預存認證) </span><span class="sxs-lookup"><span data-stu-id="15ca3-111">Configure stored credentials for a shared data source (Native mode)</span></span>](#bkmk_stored_credentials_shared_data_source_native)

-   [<span data-ttu-id="15ca3-112"> (SharePoint 模式設定共用資料來源的預存認證) </span><span class="sxs-lookup"><span data-stu-id="15ca3-112">Configure stored credentials for a shared data source (SharePoint mode)</span></span>](#bkmk_stored_credentials_shared_data_source_sharepoint)

##  <a name="security-policy-requirements-for-stored-credentials"></a><a name="bkmk_top"></a> <span data-ttu-id="15ca3-113">預存認證的安全性原則需求</span><span class="sxs-lookup"><span data-stu-id="15ca3-113">Security policy requirements for stored credentials</span></span>
 <span data-ttu-id="15ca3-114">![as_powerpivot_refresh_sss_set_key](../../analysis-services/media/as-powerpivot-refresh-sss-set-key.gif "as_powerpivot_refresh_sss_set_key") 您必須在報表伺服器上，為預存認證所使用的帳戶設定下列其中一項安全性原則。</span><span class="sxs-lookup"><span data-stu-id="15ca3-114">![as_powerpivot_refresh_sss_set_key](../../analysis-services/media/as-powerpivot-refresh-sss-set-key.gif "as_powerpivot_refresh_sss_set_key") It is required that the account you use for stored credentials, is configured for one of the following security policies on the report server.</span></span> <span data-ttu-id="15ca3-115">建議您為您的環境選取具備需要的最低層級權限的原則。</span><span class="sxs-lookup"><span data-stu-id="15ca3-115">It is recommended you select the policy with the minimum level of permissions you require for your environment.</span></span>

1.  <span data-ttu-id="15ca3-116">**允許本機登**入。</span><span class="sxs-lookup"><span data-stu-id="15ca3-116">**Allow log on locally**.</span></span> <span data-ttu-id="15ca3-117">如需詳細資訊，請參閱 [允許本機登入](https://technet.microsoft.com/library/cc756809\(v=WS.10\).aspx)。</span><span class="sxs-lookup"><span data-stu-id="15ca3-117">For more information, see [Allow log on locally](https://technet.microsoft.com/library/cc756809\(v=WS.10\).aspx).</span></span>

2.  <span data-ttu-id="15ca3-118">**以批次工作登入**。</span><span class="sxs-lookup"><span data-stu-id="15ca3-118">**Log on as a batch job**.</span></span> <span data-ttu-id="15ca3-119">如需詳細資訊，請參閱 [以批次工作登入](https://technet.microsoft.com/library/cc755659\(v=ws.10\).aspx)。</span><span class="sxs-lookup"><span data-stu-id="15ca3-119">For more information, see [Log on as a batch job](https://technet.microsoft.com/library/cc755659\(v=ws.10\).aspx).</span></span>

3.  <span data-ttu-id="15ca3-120">如需原則的一般資訊，請參閱 [編輯群組原則物件的安全性設定](https://technet.microsoft.com/library/cc736516\(v=ws.10\).aspx)。</span><span class="sxs-lookup"><span data-stu-id="15ca3-120">For general information on policies, see [Edit security settings on a Group Policy object](https://technet.microsoft.com/library/cc736516\(v=ws.10\).aspx).</span></span>

##  <a name="configure-stored-credentials-for-a-report-specific-data-source-native-mode"></a><a name="bkmk_stored_credentials_data_source_native"></a> <span data-ttu-id="15ca3-121">為報表特定的資料來源設定預存認證 (原生模式)</span><span class="sxs-lookup"><span data-stu-id="15ca3-121">Configure stored credentials for a report-specific data source (Native mode)</span></span>

1.  <span data-ttu-id="15ca3-122">在原生模式報表管理員中，瀏覽至包含報表的資料夾。</span><span class="sxs-lookup"><span data-stu-id="15ca3-122">In Native mode Report Manager, browse to the folder that contains the report.</span></span> <span data-ttu-id="15ca3-123">![針對 ssrs 專案，按一下報表管理員中](../media/ssrs-report-manager-item-context-menu.png "報表管理員中適用於 SSRS 項目的內容功能表")的專案內容功能表內容功能表。</span><span class="sxs-lookup"><span data-stu-id="15ca3-123">Click the item context menu ![context menu in report manager for ssrs items](../media/ssrs-report-manager-item-context-menu.png "context menu in report manager for ssrs items").</span></span>

2.  <span data-ttu-id="15ca3-124">按一下 [管理] \*\*\*\* ，然後按一下 [資料來源] \*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="15ca3-124">Click **Manage** and then click **Data Sources**.</span></span>

3.  <span data-ttu-id="15ca3-125">選取 **[自訂資料來源]**。</span><span class="sxs-lookup"><span data-stu-id="15ca3-125">Select **A custom data source**.</span></span>

4.  <span data-ttu-id="15ca3-126">在 [資料來源類型] \*\*\*\* 清單中，選取用來處理資料來源中之資料的資料處理延伸模組。</span><span class="sxs-lookup"><span data-stu-id="15ca3-126">In the **Data Source Type** list, select the data processing extension that is used to process data from the data source.</span></span>

5.  <span data-ttu-id="15ca3-127">針對 [**連接字串**]，請指定報表伺服器用來連接到資料來源的連接字串。</span><span class="sxs-lookup"><span data-stu-id="15ca3-127">For **Connection String**, specify the connection string that the report server uses to connect to the data source.</span></span> <span data-ttu-id="15ca3-128">下列範例說明用來連接到資料庫的連接字串 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] ：</span><span class="sxs-lookup"><span data-stu-id="15ca3-128">The following example illustrates a connection string used to connect to the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] database:</span></span>

    ```
    data source=<servername>;initial catalog=AdventureWorks2012
    ```

6.  <span data-ttu-id="15ca3-129">針對 [連接方式] \*\*\*\*，選取 [安全地儲存在報表伺服器中的認證] \*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="15ca3-129">For **Connect Using**, select **Credentials stored securely in the report server**.</span></span>

7.  <span data-ttu-id="15ca3-130">輸入使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="15ca3-130">Type a user name and password.</span></span>

    -   <span data-ttu-id="15ca3-131">如果帳戶是 Windows 網域使用者帳戶，請使用下列格式來指定它： \<domain> \\<帳戶 \> ，然後選取 **[連接到資料來源時做為 Windows 認證]。**</span><span class="sxs-lookup"><span data-stu-id="15ca3-131">If the account is a Windows domain user account, specify it in this format: \<domain>\\<account\>, and then select **Use as Windows credentials when connecting to the data source.**</span></span>

    -   <span data-ttu-id="15ca3-132">如果使用者名稱和密碼是資料庫認證，請勿選取 **[連接到資料來源時做為 Windows 認證]**。</span><span class="sxs-lookup"><span data-stu-id="15ca3-132">If the user name and password are database credentials, do not select **Use as Windows credentials when connecting to the data source**.</span></span> <span data-ttu-id="15ca3-133">如果資料庫伺服器支援模擬或委派，您就可以選取 **[連接到資料來源後，模擬已驗證的使用者]**。</span><span class="sxs-lookup"><span data-stu-id="15ca3-133">If the database server supports impersonation or delegation, you can select **Impersonate the authenticated user after a connection has been made to the data source**.</span></span>

8.  <span data-ttu-id="15ca3-134">按一下 [套用]。</span><span class="sxs-lookup"><span data-stu-id="15ca3-134">Click **Apply**.</span></span>

     <span data-ttu-id="15ca3-135">![搭配 [回到頁首] 連結使用的箭頭圖示](../../2014-toc/media/uparrow16x16.gif "與 [回到頁首] 連結搭配使用的箭頭圖示") [預存認證的安全性原則需求](#bkmk_top)</span><span class="sxs-lookup"><span data-stu-id="15ca3-135">![Arrow icon used with Back to Top link](../../2014-toc/media/uparrow16x16.gif "Arrow icon used with Back to Top link") [Security policy requirements for stored credentials](#bkmk_top)</span></span>

##  <a name="configure-stored-credentials-for-a-report-specific-data-source-sharepoint-mode"></a><a name="bkmk_stored_credentials_data_source_sharepoint"></a> <span data-ttu-id="15ca3-136">為報表特定的資料來源設定預存認證 (SharePoint 模式)</span><span class="sxs-lookup"><span data-stu-id="15ca3-136">Configure stored credentials for a report-specific data source (SharePoint mode)</span></span>

1.  <span data-ttu-id="15ca3-137">瀏覽至包含報表的文件庫，然後按一下開啟的功能表 ![適用於 SSRS 項目的文件庫操作功能表](../media/ssrs-sharepoint-item-context-menu.png "適用於 SSRS 項目的文件庫操作功能表")。</span><span class="sxs-lookup"><span data-stu-id="15ca3-137">Browse to the document library that contains the report and then click the open menu ![document library context menu for ssrs items](../media/ssrs-sharepoint-item-context-menu.png "document library context menu for ssrs items").</span></span>

2.  <span data-ttu-id="15ca3-138">按一下第二個開啟的功能表 ![適用於 SSRS 項目的文件庫操作功能表](../media/ssrs-sharepoint-item-context-menu.png "適用於 SSRS 項目的文件庫操作功能表")，然後按一下 [管理資料來源]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="15ca3-138">Click second open menu ![document library context menu for ssrs items](../media/ssrs-sharepoint-item-context-menu.png "document library context menu for ssrs items") and then click **Manage Data Sources**.</span></span>

3.  <span data-ttu-id="15ca3-139">按一下您要設定預存認證的 [自訂] \*\*\*\* 資料來源的名稱。</span><span class="sxs-lookup"><span data-stu-id="15ca3-139">Click the name of the **Custom** data source you want to configure with stored credentials.</span></span>

4.  <span data-ttu-id="15ca3-140">在 [資料來源類型] \*\*\*\* 清單中，選取用來處理資料來源中之資料的資料處理延伸模組。</span><span class="sxs-lookup"><span data-stu-id="15ca3-140">In the **Data Source Type** list, select the data processing extension that is used to process data from the data source.</span></span>

5.  <span data-ttu-id="15ca3-141">針對 [**連接字串**]，請指定報表伺服器用來連接到資料來源的連接字串。</span><span class="sxs-lookup"><span data-stu-id="15ca3-141">For **Connection String**, specify the connection string that the report server uses to connect to the data source.</span></span> <span data-ttu-id="15ca3-142">下列範例說明用來連接到資料庫的連接字串 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] ：</span><span class="sxs-lookup"><span data-stu-id="15ca3-142">The following example illustrates a connection string used to connect to the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] database:</span></span>

    ```
    data source=<servername>;initial catalog=AdventureWorks2012
    ```

6.  <span data-ttu-id="15ca3-143">針對 [認證] \*\*\*\* 選取 [預存認證] \*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="15ca3-143">For **Credentials**, select **Stored Credentials**.</span></span>

7.  <span data-ttu-id="15ca3-144">輸入**使用者名稱**和**密碼**。</span><span class="sxs-lookup"><span data-stu-id="15ca3-144">Type a **user name** and **password**.</span></span>

    -   <span data-ttu-id="15ca3-145">如果帳戶是 Windows 網域使用者帳戶，請使用下列格式來指定它： \<domain> \\<帳戶 \> ，然後選取 **[連接到資料來源時做為 Windows 認證]。**</span><span class="sxs-lookup"><span data-stu-id="15ca3-145">If the account is a Windows domain user account, specify it in this format: \<domain>\\<account\>, and then select **Use as Windows credentials when connecting to the data source.**</span></span>

    -   <span data-ttu-id="15ca3-146">如果使用者名稱和密碼是資料庫認證，請勿選取 [當做 Windows 認證使用] \*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="15ca3-146">If the user name and password are database credentials, do not select **Use as Windows credentials**.</span></span> <span data-ttu-id="15ca3-147">如果資料庫伺服器支援模擬或委派，您可以選取 [**設定執行內容到這個帳戶**]。</span><span class="sxs-lookup"><span data-stu-id="15ca3-147">If the database server supports impersonation or delegation, you can select **Set execution context to this account**.</span></span>

8.  <span data-ttu-id="15ca3-148">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="15ca3-148">Click **ok**.</span></span>

     <span data-ttu-id="15ca3-149">![搭配 [回到頁首] 連結使用的箭頭圖示](../../2014-toc/media/uparrow16x16.gif "與 [回到頁首] 連結搭配使用的箭頭圖示") [預存認證的安全性原則需求](#bkmk_top)</span><span class="sxs-lookup"><span data-stu-id="15ca3-149">![Arrow icon used with Back to Top link](../../2014-toc/media/uparrow16x16.gif "Arrow icon used with Back to Top link") [Security policy requirements for stored credentials](#bkmk_top)</span></span>

##  <a name="configure-stored-credentials-for-a-shared-data-source-native-mode"></a><a name="bkmk_stored_credentials_shared_data_source_native"></a> <span data-ttu-id="15ca3-150">為共用資料來源設定預存認證 (原生模式)</span><span class="sxs-lookup"><span data-stu-id="15ca3-150">Configure stored credentials for a shared data source (Native mode)</span></span>

1.  <span data-ttu-id="15ca3-151">在原生模式報表管理員中，瀏覽至共用資料來源項目。</span><span class="sxs-lookup"><span data-stu-id="15ca3-151">In Native mode Report Manager, browse to the shared data source item.</span></span> <span data-ttu-id="15ca3-152">![共用資料來源圖示](../media/hlp-16datasource.png "共用資料來源圖示")</span><span class="sxs-lookup"><span data-stu-id="15ca3-152">![Shared data source icon](../media/hlp-16datasource.png "Shared data source icon")</span></span>

2.  <span data-ttu-id="15ca3-153">![在 [報表管理員] 中按一下 [ssrs 專案](../media/ssrs-report-manager-item-context-menu.png "報表管理員中適用於 SSRS 項目的內容功能表")] 的操作功能表內容功能表，然後按一下 [**管理**]。</span><span class="sxs-lookup"><span data-stu-id="15ca3-153">Click the context menu ![context menu in report manager for ssrs items](../media/ssrs-report-manager-item-context-menu.png "context menu in report manager for ssrs items") and then click **Manage**.</span></span>

3.  <span data-ttu-id="15ca3-154">在 [**資料來源類型**] 清單中，指定用來處理資料來源中之資料的資料處理延伸模組。</span><span class="sxs-lookup"><span data-stu-id="15ca3-154">In the **Data Source Type** list, specify the data processing extension that is used to process data from the data source.</span></span>

4.  <span data-ttu-id="15ca3-155">針對 [**連接字串**]，請指定報表伺服器用來連接到資料來源的連接字串。</span><span class="sxs-lookup"><span data-stu-id="15ca3-155">For **Connection String**, specify the connection string that the report server uses to connect to the data source.</span></span> [!INCLUDE[msCoName](../../../includes/msconame-md.md)] <span data-ttu-id="15ca3-156">建議您不要在連接字串中指定認證。</span><span class="sxs-lookup"><span data-stu-id="15ca3-156">recommends that you do not specify credentials in the connection string.</span></span>

     <span data-ttu-id="15ca3-157">下列範例說明用來連接到本機資料庫的連接字串 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] ：</span><span class="sxs-lookup"><span data-stu-id="15ca3-157">The following example illustrates a connection string used to connect to the local [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] database:</span></span>

    ```
    data source=<localservername>; initial catalog=AdventureWorks2012
    ```

5.  <span data-ttu-id="15ca3-158">輸入使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="15ca3-158">Type a user name and password.</span></span>

    -   <span data-ttu-id="15ca3-159">如果帳戶是 Windows 網域使用者帳戶，請使用下列格式來指定它： \<domain> \\<帳戶 \> ，然後選取 **[連接到資料來源時做為 Windows 認證]。**</span><span class="sxs-lookup"><span data-stu-id="15ca3-159">If the account is a Windows domain user account, specify it in this format: \<domain>\\<account\>, and then select **Use as Windows credentials when connecting to the data source.**</span></span>

    -   <span data-ttu-id="15ca3-160">如果使用者名稱和密碼是資料庫認證，請勿選取 **[連接到資料來源時做為 Windows 認證]**。</span><span class="sxs-lookup"><span data-stu-id="15ca3-160">If the user name and password are database credentials, do not select **Use as Windows credentials when connecting to the data source**.</span></span> <span data-ttu-id="15ca3-161">如果資料庫伺服器支援模擬或委派，您就可以選取 **[連接到資料來源後，模擬已驗證的使用者]**。</span><span class="sxs-lookup"><span data-stu-id="15ca3-161">If the database server supports impersonation or delegation, you can select **Impersonate the authenticated user after a connection has been made to the data source**.</span></span>

6.  <span data-ttu-id="15ca3-162">按一下 [套用]。</span><span class="sxs-lookup"><span data-stu-id="15ca3-162">Click **Apply**.</span></span>

     <span data-ttu-id="15ca3-163">![搭配 [回到頁首] 連結使用的箭頭圖示](../../2014-toc/media/uparrow16x16.gif "與 [回到頁首] 連結搭配使用的箭頭圖示") [預存認證的安全性原則需求](#bkmk_top)</span><span class="sxs-lookup"><span data-stu-id="15ca3-163">![Arrow icon used with Back to Top link](../../2014-toc/media/uparrow16x16.gif "Arrow icon used with Back to Top link") [Security policy requirements for stored credentials](#bkmk_top)</span></span>

##  <a name="configure-stored-credentials-for-a-shared-data-source-sharepoint-mode"></a><a name="bkmk_stored_credentials_shared_data_source_sharepoint"></a> <span data-ttu-id="15ca3-164">為共用資料來源設定預存認證 (SharePoint 模式)</span><span class="sxs-lookup"><span data-stu-id="15ca3-164">Configure stored credentials for a shared data source (SharePoint mode)</span></span>

1.  <span data-ttu-id="15ca3-165">在文件庫中，瀏覽至共用資料來源項目。![共用資料來源圖示](../media/hlp-16datasource.png "共用資料來源圖示")</span><span class="sxs-lookup"><span data-stu-id="15ca3-165">In the document library, browse to the shared data source item.![Shared data source icon](../media/hlp-16datasource.png "Shared data source icon")</span></span>

2.  <span data-ttu-id="15ca3-166">按一下操作功能表 ![適用於 SSRS 項目的文件庫操作功能表](../media/ssrs-sharepoint-item-context-menu.png "適用於 SSRS 項目的文件庫操作功能表")，然後按一下第二個操作功能表 ![適用於 SSRS 項目的文件庫操作功能表](../media/ssrs-sharepoint-item-context-menu.png "適用於 SSRS 項目的文件庫操作功能表")。</span><span class="sxs-lookup"><span data-stu-id="15ca3-166">Click the context menu ![document library context menu for ssrs items](../media/ssrs-sharepoint-item-context-menu.png "document library context menu for ssrs items") and then click the second context menu ![document library context menu for ssrs items](../media/ssrs-sharepoint-item-context-menu.png "document library context menu for ssrs items").</span></span>

3.  <span data-ttu-id="15ca3-167">按一下 [編輯資料來源定義] \*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="15ca3-167">Click **Edit Data Source Definition**.</span></span>

4.  <span data-ttu-id="15ca3-168">在 [**資料來源類型**] 清單中，指定用來處理資料來源中之資料的資料處理延伸模組。</span><span class="sxs-lookup"><span data-stu-id="15ca3-168">In the **Data Source Type** list, specify the data processing extension that is used to process data from the data source.</span></span>

5.  <span data-ttu-id="15ca3-169">針對 [**連接字串**]，請指定報表伺服器用來連接到資料來源的連接字串。</span><span class="sxs-lookup"><span data-stu-id="15ca3-169">For **Connection String**, specify the connection string that the report server uses to connect to the data source.</span></span> [!INCLUDE[msCoName](../../../includes/msconame-md.md)] <span data-ttu-id="15ca3-170">建議您不要在連接字串中指定認證。</span><span class="sxs-lookup"><span data-stu-id="15ca3-170">recommends that you do not specify credentials in the connection string.</span></span>

     <span data-ttu-id="15ca3-171">下列範例說明用來連接到本機資料庫的連接字串 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] ：</span><span class="sxs-lookup"><span data-stu-id="15ca3-171">The following example illustrates a connection string used to connect to the local [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] database:</span></span>

    ```
    data source=<localservername>; initial catalog=AdventureWorks2012
    ```

6.  <span data-ttu-id="15ca3-172">輸入使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="15ca3-172">Type a user name and password.</span></span>

    -   <span data-ttu-id="15ca3-173">如果帳戶是 Windows 網域使用者帳戶，請使用下列格式來指定它： \<domain> \\<帳戶] \> ，然後選取 [**做為 Windows 認證]。**</span><span class="sxs-lookup"><span data-stu-id="15ca3-173">If the account is a Windows domain user account, specify it in this format: \<domain>\\<account\>, and then select **Use as Windows credentials.**</span></span>

    -   <span data-ttu-id="15ca3-174">如果使用者名稱和密碼是資料庫認證，請勿選取 [當做 Windows 認證使用] \*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="15ca3-174">If the user name and password are database credentials, do not select **Use as Windows credentials**.</span></span> <span data-ttu-id="15ca3-175">如果資料庫伺服器支援模擬或委派，您可以選取 **Set Execution context to this account**。</span><span class="sxs-lookup"><span data-stu-id="15ca3-175">If the database server supports impersonation or delegation, you can select **Set Execution context to this account**.</span></span>

7.  <span data-ttu-id="15ca3-176">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="15ca3-176">Click **Ok**.</span></span>

     <span data-ttu-id="15ca3-177">![搭配 [回到頁首] 連結使用的箭頭圖示](../../2014-toc/media/uparrow16x16.gif "與 [回到頁首] 連結搭配使用的箭頭圖示") [預存認證的安全性原則需求](#bkmk_top)</span><span class="sxs-lookup"><span data-stu-id="15ca3-177">![Arrow icon used with Back to Top link](../../2014-toc/media/uparrow16x16.gif "Arrow icon used with Back to Top link") [Security policy requirements for stored credentials](#bkmk_top)</span></span>

## <a name="see-also"></a><span data-ttu-id="15ca3-178">另請參閱</span><span class="sxs-lookup"><span data-stu-id="15ca3-178">See Also</span></span>
 <span data-ttu-id="15ca3-179">[指定報表資料來源的認證和連接資訊](../../integration-services/connection-manager/data-sources.md)[設定報表的資料來源屬性 &#40;報表管理員&#41;](configure-data-source-properties-for-a-report-report-manager.md) [建立、刪除或修改共用資料來源 &#40;報表管理員](../create-delete-or-modify-a-shared-data-source-report-manager.md)&#41;[資料來源屬性頁面 &#40;](../data-sources-properties-page-report-manager.md)報表管理員&#41;[新增資料來源頁面](../new-data-source-page-report-manager.md)&#40;報表管理員&#41;</span><span class="sxs-lookup"><span data-stu-id="15ca3-179">[Specify Credential and Connection Information for Report Data Sources](../../integration-services/connection-manager/data-sources.md) [Configure Data Source Properties for a Report  &#40;Report Manager&#41;](configure-data-source-properties-for-a-report-report-manager.md) [Create, Delete, or Modify a Shared Data Source &#40;Report Manager&#41;](../create-delete-or-modify-a-shared-data-source-report-manager.md) [Data Sources Properties Page &#40;Report Manager&#41;](../data-sources-properties-page-report-manager.md) [New Data Source Page &#40;Report Manager&#41;](../new-data-source-page-report-manager.md)</span></span>


