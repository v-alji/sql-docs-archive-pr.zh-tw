---
title: 在 SharePoint 中啟用報表伺服器和 Power View 整合功能 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: c7f64a54-c555-4d31-bf99-3abe57dc8626
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: af5f544e959c039b0bdb85d63d0b94917254d78a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599385"
---
# <a name="activate-the-report-server-and-power-view-integration-features-in-sharepoint"></a><span data-ttu-id="adbc4-102">在 SharePoint 中啟用報表伺服器和 Power View 整合功能</span><span class="sxs-lookup"><span data-stu-id="adbc4-102">Activate the Report Server and Power View Integration Features in SharePoint</span></span>
  <span data-ttu-id="adbc4-103">在 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 您安裝 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)] 適用于 SharePoint 產品的增益集之後，通常會預設啟用網站集合功能。</span><span class="sxs-lookup"><span data-stu-id="adbc4-103">The [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] site collection features are usually activated by default after you install the [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)] Add-in for SharePoint products.</span></span> <span data-ttu-id="adbc4-104">在某些情況下，您必須手動啟用這些功能。</span><span class="sxs-lookup"><span data-stu-id="adbc4-104">In some situations you will need to manually activate the features.</span></span>  
  
 <span data-ttu-id="adbc4-105">如果您在安裝 SharePoint 產品之後安裝適用於 SharePoint 2010 產品的 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 增益集，只會針對根網站集合啟用報表伺服器整合功能和 Power View 整合功能。</span><span class="sxs-lookup"><span data-stu-id="adbc4-105">If you install the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] add-in for SharePoint 2010 Products after the installation of the SharePoint product, then the Report Server integration feature and the Power View integration feature will only be activated for root site collections.</span></span> <span data-ttu-id="adbc4-106">如果是其他網站集合，您必須手動啟用這些功能。</span><span class="sxs-lookup"><span data-stu-id="adbc4-106">For other site collections, you will need to manually activate the features.</span></span> <span data-ttu-id="adbc4-107">例如，如果您擁有 **http://[我的伺服器名稱]/sites/[網站集合名稱]** 網站集合，您需要手動啟用 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 網站集合功能。</span><span class="sxs-lookup"><span data-stu-id="adbc4-107">For example if you have a site collection of **http://[my server name]/sites/[site collection name]** you will need to manually activate the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] site collection features.</span></span>  
  
 <span data-ttu-id="adbc4-108">如果沒有根網站集合，則 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 增益集會記錄與下面類似的訊息。</span><span class="sxs-lookup"><span data-stu-id="adbc4-108">When there is no root site collection, the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] add-in will log a message similar to the following.</span></span>  
  
 <span data-ttu-id="adbc4-109">「SharePoint Web 應用程式 80 沒有根網站集合」</span><span class="sxs-lookup"><span data-stu-id="adbc4-109">"SharePoint web app 80 does not have root site collection"</span></span>  
  
 <span data-ttu-id="adbc4-110">此訊息會在增益集安裝記錄檔中找到，名稱為 "RS_SP_ # .log"，其中 # 是遞增的數位。</span><span class="sxs-lookup"><span data-stu-id="adbc4-110">The message will be found in the add-in installation log, named "RS_SP_#.log" where # is an incrementing number.</span></span> <span data-ttu-id="adbc4-111">記錄檔會在目前使用者的 Temp 資料夾中找到，例如 C:\Users \\ [使用者名稱] \appdata\local\temp。如需使用增益集記錄選項的詳細資訊，請參閱[安裝或卸載適用于 sharepoint 的 Reporting Services 增益集 &#40;sharepoint 2010 和 sharepoint 2013&#41;](install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md)。</span><span class="sxs-lookup"><span data-stu-id="adbc4-111">The log file will be found in the current users Temp folder, for example C:\Users\\[user name]\AppData\Local\Temp. For more information on logging options with the add-in, see [Install or Uninstall the Reporting Services Add-in for SharePoint &#40;SharePoint 2010 and SharePoint 2013&#41;](install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md).</span></span>  
  
 <span data-ttu-id="adbc4-112">本主題內容：</span><span class="sxs-lookup"><span data-stu-id="adbc4-112">In this topic:</span></span>  
  
-   [<span data-ttu-id="adbc4-113">若要啟用報表伺服器和 Power View 整合網站集合功能：</span><span class="sxs-lookup"><span data-stu-id="adbc4-113">To Activate the Report Server and Power View Integration Site Collection Features:</span></span>](#bkmk_features)  
  
-   [<span data-ttu-id="adbc4-114">若要啟用或停用 Reporting Services 管理中心的網站集合功能：</span><span class="sxs-lookup"><span data-stu-id="adbc4-114">To Activate or Deactivate Reporting Services Central Administration Site Collection Feature:</span></span>](#bkmk_centraladmin)  
  
##  <a name="to-activate-the-report-server-and-power-view-integration-site-collection-features"></a><a name="bkmk_features"></a><span data-ttu-id="adbc4-115">若要啟用報表伺服器和 Power View 整合網站集合功能：</span><span class="sxs-lookup"><span data-stu-id="adbc4-115">To Activate the Report Server and Power View Integration Site Collection Features:</span></span>  
  
1.  <span data-ttu-id="adbc4-116">開啟瀏覽器，移至您想要啟用 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 功能的網站。</span><span class="sxs-lookup"><span data-stu-id="adbc4-116">Open your browser to the site where you want the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] features active.</span></span>  
  
2.  <span data-ttu-id="adbc4-117">按一下 **[網站動作]** 。</span><span class="sxs-lookup"><span data-stu-id="adbc4-117">Click **Site Actions**.</span></span>  
  
3.  <span data-ttu-id="adbc4-118">按一下 **[站台設定]** 。</span><span class="sxs-lookup"><span data-stu-id="adbc4-118">Click **Site Settings**.</span></span>  
  
4.  <span data-ttu-id="adbc4-119">在網站集合管理群組中，按一下 **[網站集合功能]** 。</span><span class="sxs-lookup"><span data-stu-id="adbc4-119">Click **Site Collection Features** in the Site Collection Administration Group.</span></span>  
  
5.  <span data-ttu-id="adbc4-120">在清單中尋找 **[報表伺服器整合功能]** 或 **[Power View 整合功能]** 。</span><span class="sxs-lookup"><span data-stu-id="adbc4-120">Find **Report Server Integration Feature** or **Power View Integration Feature** in the list.</span></span>  
  
6.  <span data-ttu-id="adbc4-121">按一下 [啟用]。</span><span class="sxs-lookup"><span data-stu-id="adbc4-121">Click **Activate**.</span></span>  
  
 <span data-ttu-id="adbc4-122">若要停用功能，您可以使用相同的程序，但是要按一下 **[停用]** ，而不是 **[啟用]**。</span><span class="sxs-lookup"><span data-stu-id="adbc4-122">To deactivate the features, you can use the same procedure, but click **Deactivate** rather than **Activate.**</span></span>  
  
##  <a name="to-activate-or-deactivate-reporting-services-central-administration-site-collection-feature"></a><a name="bkmk_centraladmin"></a><span data-ttu-id="adbc4-123">若要啟用或停用 Reporting Services 管理中心網站集合功能：</span><span class="sxs-lookup"><span data-stu-id="adbc4-123">To Activate or Deactivate Reporting Services Central Administration Site Collection Feature:</span></span>  
  
1.  <span data-ttu-id="adbc4-124">開啟瀏覽器，並移至 SharePoint 管理中心。</span><span class="sxs-lookup"><span data-stu-id="adbc4-124">Open your browser to SharePoint Central Administration.</span></span>  
  
2.  <span data-ttu-id="adbc4-125">按一下 **[網站動作]** 。</span><span class="sxs-lookup"><span data-stu-id="adbc4-125">Click **Site Actions**.</span></span>  
  
3.  <span data-ttu-id="adbc4-126">按一下 **[站台設定]** 。</span><span class="sxs-lookup"><span data-stu-id="adbc4-126">Click **Site Settings**.</span></span>  
  
4.  <span data-ttu-id="adbc4-127">在網站集合管理群組中，按一下 **[網站集合功能]** 。</span><span class="sxs-lookup"><span data-stu-id="adbc4-127">Click **Site Collection Features** in the Site Collection Administration Group.</span></span>  
  
5.  <span data-ttu-id="adbc4-128">在清單中尋找 **[報表伺服器管理中心功能]** 。</span><span class="sxs-lookup"><span data-stu-id="adbc4-128">Find **Report Server Central Administration Feature** in the list.</span></span>  
  
6.  <span data-ttu-id="adbc4-129">按一下 [啟用]。</span><span class="sxs-lookup"><span data-stu-id="adbc4-129">Click **Activate**.</span></span>  
  
 <span data-ttu-id="adbc4-130">若要停用此功能，您可以使用相同的程序，但是要按一下 **[停用]** ，而不是 **[啟用]**。</span><span class="sxs-lookup"><span data-stu-id="adbc4-130">To deactivate the feature, you can use the same procedure, but click **Deactivate** rather than **Activate.**</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="adbc4-131">後續步驟</span><span class="sxs-lookup"><span data-stu-id="adbc4-131">Next Steps</span></span>  
 <span data-ttu-id="adbc4-132">當此功能啟動之後，您就可以繼續伺服器整合。</span><span class="sxs-lookup"><span data-stu-id="adbc4-132">After the feature is activated, you can continue with server integration.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="adbc4-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="adbc4-133">See Also</span></span>  
 [<span data-ttu-id="adbc4-134">安裝或卸載適用于 SharePoint &#40;SharePoint 2010 和 SharePoint 2013 的 Reporting Services 增益集&#41;</span><span class="sxs-lookup"><span data-stu-id="adbc4-134">Install or Uninstall the Reporting Services Add-in for SharePoint &#40;SharePoint 2010 and SharePoint 2013&#41;</span></span>](install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md)  
  
  
