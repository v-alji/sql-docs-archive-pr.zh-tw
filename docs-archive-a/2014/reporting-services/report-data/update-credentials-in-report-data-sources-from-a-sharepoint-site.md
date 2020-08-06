---
title: 從 SharePoint 網站更新報表資料來源的認證 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: e0c50b6e-89e7-4b4d-8fe5-c90682c5d1b1
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 923fee5656ed6032201fb4276fcca75be799e42d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585055"
---
# <a name="update-credentials-in-report-data-sources-from-a-sharepoint-site"></a><span data-ttu-id="5ea29-102">從 SharePoint 網站更新報表資料來源的認證</span><span class="sxs-lookup"><span data-stu-id="5ea29-102">Update Credentials in Report Data Sources from a SharePoint Site</span></span>
  <span data-ttu-id="5ea29-103">本主題描述如何更新內嵌於報表內的資料來源，以及儲存在 SharePoint 文件庫中的共用資料來源。</span><span class="sxs-lookup"><span data-stu-id="5ea29-103">This topic describes how to update data sources embedded in reports and shared data sources that are saved in a SharePoint document library.</span></span>  
  
 <span data-ttu-id="5ea29-104">許多報表可能包含資料來源或使用設定為使用 Windows 驗證的共用資料來源。</span><span class="sxs-lookup"><span data-stu-id="5ea29-104">Many of your reports might include data sources or use shared data sources that are configured to use Windows Authentication.</span></span> <span data-ttu-id="5ea29-105">在某些情況下 (例如在儲存到 SharePoint 文件庫的報表上建立資料警示)，您需要將資料來源認證更新至預存認證或是不需要認證。</span><span class="sxs-lookup"><span data-stu-id="5ea29-105">Under some circumstances, such as creating data alerts on reports saved to a SharePoint document library, you need to update the data source credentials to stored credentials or require no credentials.</span></span>  
  
 <span data-ttu-id="5ea29-106">為了使用報表中的預存認證，您可能會決定建立並使用新的 SQL Server 登入。</span><span class="sxs-lookup"><span data-stu-id="5ea29-106">To use stored credentials in reports, you might decide to create and use a new SQL Server login.</span></span> <span data-ttu-id="5ea29-107">如需詳細資訊，請參閱 [建立登入](../../relational-databases/security/authentication-access/create-a-login.md)。</span><span class="sxs-lookup"><span data-stu-id="5ea29-107">For more information, see [Create a Login](../../relational-databases/security/authentication-access/create-a-login.md).</span></span>  
  
### <a name="to-update-an-embedded-data-source-to-use-stored-credentials"></a><span data-ttu-id="5ea29-108">更新內嵌資料來源以使用預存認證</span><span class="sxs-lookup"><span data-stu-id="5ea29-108">To update an embedded data source to use stored credentials</span></span>  
  
1.  <span data-ttu-id="5ea29-109">移至儲存報表所在的 SharePoint 文件庫。</span><span class="sxs-lookup"><span data-stu-id="5ea29-109">Go to the SharePoint document library where you saved the report.</span></span>  
  
2.  <span data-ttu-id="5ea29-110">按一下報表上用來展開下拉式功能表的圖示，然後按一下 [管理資料來源]  。</span><span class="sxs-lookup"><span data-stu-id="5ea29-110">Click the icon for the expand drop-down menu on the report and then click **Manage Data Sources**.</span></span>  
  
     <span data-ttu-id="5ea29-111">[管理資料來源] 頁面隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="5ea29-111">The Manage Data Sources page opens.</span></span>  
  
3.  <span data-ttu-id="5ea29-112">在 [名稱]  資料行中，按一下資料來源。</span><span class="sxs-lookup"><span data-stu-id="5ea29-112">In the **Name** column, click the data source.</span></span>  
  
4.  <span data-ttu-id="5ea29-113">確認已針對 [連線類型]  選取 [自訂資料來源]  選項。</span><span class="sxs-lookup"><span data-stu-id="5ea29-113">For **Connection Type** verify that the **Custom data source** option is selected.</span></span>  
  
     <span data-ttu-id="5ea29-114">這個選項表示資料來源內嵌於報表中。</span><span class="sxs-lookup"><span data-stu-id="5ea29-114">This option indicates that the data source is embedded in the report.</span></span>  
  
5.  <span data-ttu-id="5ea29-115">除非您要將報表連接到其他類型的資料來源、其他伺服器或資料存放區，否則讓 [資料來源類型]  和 [連接字串]  選項保持不變。</span><span class="sxs-lookup"><span data-stu-id="5ea29-115">Leave the **Data Source Type** and **Connection string** options as they are, unless you want the report to connect to different type of data source, a different server, or data store.</span></span>  
  
6.  <span data-ttu-id="5ea29-116">針對 [認證]  選取 [預存認證]  。</span><span class="sxs-lookup"><span data-stu-id="5ea29-116">For **Credentials**, select **Stored credentials**.</span></span> <span data-ttu-id="5ea29-117">只有在資料來源未接受認證，或是使用一些其他方式傳送認證時，這個選項才有用。</span><span class="sxs-lookup"><span data-stu-id="5ea29-117">This option works only if the data source does not accept credentials or if you are passing credentials some other way.</span></span>  
  
     <span data-ttu-id="5ea29-118">在某些情況下也可以使用 [不需要認證]  選項。</span><span class="sxs-lookup"><span data-stu-id="5ea29-118">The **Credentials are not required** option can also be used under some circumstances.</span></span>  
  
     <span data-ttu-id="5ea29-119">針對某些資料來源類型，必須在報表伺服器上設定自動執行帳戶。</span><span class="sxs-lookup"><span data-stu-id="5ea29-119">From some data source types, the unattended execution account must be configured on the report server.</span></span> <span data-ttu-id="5ea29-120">如需詳細資訊，請參閱[從外部資料來源新增資料 &#40;SSRS&#41;](add-data-from-external-data-sources-ssrs.md) 和[設定自動執行帳戶 &#40;SSRS 設定管理員&#41;](../install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md) 中對應資料來源類型的主題。</span><span class="sxs-lookup"><span data-stu-id="5ea29-120">For more information, see the topic for the corresponding data source type in [Add Data from External Data Sources &#40;SSRS&#41;](add-data-from-external-data-sources-ssrs.md) and [Configure the Unattended Execution Account &#40;SSRS Configuration Manager&#41;](../install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md).</span></span>  
  
7.  <span data-ttu-id="5ea29-121">輸入使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="5ea29-121">Type a user name and password.</span></span>  
  
    -   <span data-ttu-id="5ea29-122">如果帳戶是 Windows 網域使用者帳戶，請使用下列格式來指定它： \<domain> \\<帳戶 \> ，然後選取 **[連接到資料來源時做為 Windows 認證**]。</span><span class="sxs-lookup"><span data-stu-id="5ea29-122">If the account is a Windows domain user account, specify it in this format: \<domain>\\<account\>, and then select **Use as Windows credentials when connecting to the data source**.</span></span>  
  
    -   <span data-ttu-id="5ea29-123">如果使用者名稱和密碼是資料庫認證，請勿選取 **[連接到資料來源時做為 Windows 認證]** 。</span><span class="sxs-lookup"><span data-stu-id="5ea29-123">If the user name and password are database credentials, do not select **Use as Windows credentials when connecting to the data source**.</span></span> <span data-ttu-id="5ea29-124">如果資料庫伺服器支援模擬或委派，您可以選取 **[設定執行內容到這個帳戶]** 。</span><span class="sxs-lookup"><span data-stu-id="5ea29-124">If the database server supports impersonation or delegation, you can select **Set execution context to this account**.</span></span>  
  
8.  <span data-ttu-id="5ea29-125">若要驗證資料來源能夠使用更新的認證連接，請按一下 [測試連線]  。</span><span class="sxs-lookup"><span data-stu-id="5ea29-125">To verify the data source can connect by using the updated credentials, click **Test connection**.</span></span>  
  
9. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-update-a-shared-data-source-to-use-stored-credentials"></a><span data-ttu-id="5ea29-126">更新共用資料來源以使用預存認證</span><span class="sxs-lookup"><span data-stu-id="5ea29-126">To update a shared data source to use stored credentials</span></span>  
  
1.  <span data-ttu-id="5ea29-127">移至儲存共用資料來源所在的 SharePoint 文件庫。</span><span class="sxs-lookup"><span data-stu-id="5ea29-127">Go to the SharePoint document library where you saved the shared data source.</span></span>  
  
2.  <span data-ttu-id="5ea29-128">按一下共用資料來源上用來展開下拉式功能表的圖示，然後按一下 [編輯資料來源定義]  。</span><span class="sxs-lookup"><span data-stu-id="5ea29-128">Click the icon for the expand drop-down menu on shared data source, and then click **Edit Data Source Definition**.</span></span>  
  
     <span data-ttu-id="5ea29-129">[資料來源] 頁面隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="5ea29-129">The Data Source page opens.</span></span>  
  
3.  <span data-ttu-id="5ea29-130">除非您要將共用資料來源連線到其他類型的資料來源、其他伺服器或資料存放區，否則讓 [資料來源類型]  和 [連接字串]  選項保持不變。</span><span class="sxs-lookup"><span data-stu-id="5ea29-130">Leave the **Data Source Type** and **Connection string** options as they are, unless you want the shared data source to connect to different type of data source, a different server, or data store.</span></span>  
  
4.  <span data-ttu-id="5ea29-131">針對 [認證]  選取 [預存認證]  。</span><span class="sxs-lookup"><span data-stu-id="5ea29-131">For **Credentials**, select **Stored credentials**.</span></span>  
  
     <span data-ttu-id="5ea29-132">在某些情況下也可以使用 [不需要認證]  選項。</span><span class="sxs-lookup"><span data-stu-id="5ea29-132">The **Credentials are not required** option can also be used under some circumstances.</span></span> <span data-ttu-id="5ea29-133">只有在資料來源未接受認證，或是使用一些其他方式傳送認證時，這個選項才有用。</span><span class="sxs-lookup"><span data-stu-id="5ea29-133">This option works only if the data source does not accept credentials or if you are passing credentials some other way.</span></span>  
  
     <span data-ttu-id="5ea29-134">針對某些資料來源類型，必須在報表伺服器上設定自動執行帳戶。</span><span class="sxs-lookup"><span data-stu-id="5ea29-134">From some data source types, the unattended execution account must be configured on the report server.</span></span> <span data-ttu-id="5ea29-135">如需詳細資訊，請參閱[從外部資料來源新增資料 &#40;SSRS&#41;](add-data-from-external-data-sources-ssrs.md) 和[設定自動執行帳戶 &#40;SSRS 設定管理員&#41;](../install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md) 中對應資料來源類型的主題。</span><span class="sxs-lookup"><span data-stu-id="5ea29-135">For more information, see the topic for the corresponding data source type in [Add Data from External Data Sources &#40;SSRS&#41;](add-data-from-external-data-sources-ssrs.md) and [Configure the Unattended Execution Account &#40;SSRS Configuration Manager&#41;](../install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md).</span></span>  
  
5.  <span data-ttu-id="5ea29-136">輸入使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="5ea29-136">Type a user name and password.</span></span>  
  
    -   <span data-ttu-id="5ea29-137">如果帳戶是 Windows 網域使用者帳戶，請使用下列格式來指定它： \<domain> \\<帳戶 \> ，然後選取 **[連接到資料來源時做為 Windows 認證]。**</span><span class="sxs-lookup"><span data-stu-id="5ea29-137">If the account is a Windows domain user account, specify it in this format: \<domain>\\<account\>, and then select **Use as Windows credentials when connecting to the data source.**</span></span>  
  
    -   <span data-ttu-id="5ea29-138">如果使用者名稱和密碼是資料庫認證，請勿選取 **[連接到資料來源時做為 Windows 認證]** 。</span><span class="sxs-lookup"><span data-stu-id="5ea29-138">If the user name and password are database credentials, do not select **Use as Windows credentials when connecting to the data source**.</span></span> <span data-ttu-id="5ea29-139">如果資料庫伺服器支援模擬或委派，您可以選取 **[設定執行內容到這個帳戶]** 。</span><span class="sxs-lookup"><span data-stu-id="5ea29-139">If the database server supports impersonation or delegation, you can select **Set execution context to this account**.</span></span>  
  
6.  <span data-ttu-id="5ea29-140">若要驗證資料來源能夠使用更新的認證連線，請使用 [測試連接]  。</span><span class="sxs-lookup"><span data-stu-id="5ea29-140">To verify the data source can connect using the updated credentials, **Test connection**.</span></span>  
  
7.  <span data-ttu-id="5ea29-141">驗證是否已選取 [啟用此資料來源]。</span><span class="sxs-lookup"><span data-stu-id="5ea29-141">Verify that Enable this data source is selected.</span></span>  
  
8.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="5ea29-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5ea29-142">See Also</span></span>  
 [<span data-ttu-id="5ea29-143">將文件上傳到 SharePoint 文件庫 &#40;SharePoint 模式的 Reporting Services&#41;</span><span class="sxs-lookup"><span data-stu-id="5ea29-143">Upload Documents to a SharePoint Library &#40;Reporting Services in SharePoint Mode&#41;</span></span>](../upload-documents-to-a-sharepoint-library-reporting-services-in-sharepoint-mode.md)  
  
  
