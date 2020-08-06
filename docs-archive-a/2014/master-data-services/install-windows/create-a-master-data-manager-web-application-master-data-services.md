---
title: 建立主資料管理員 Web 應用程式 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: 241d46d7-8008-47f6-bebd-0dfff1cc856a
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: fd81188b499850397aa8ffd2e40cfcb91c648288
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592721"
---
# <a name="create-a-master-data-manager-web-application-master-data-services"></a><span data-ttu-id="821ab-102">建立主資料管理員 Web 應用程式 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="821ab-102">Create a Master Data Manager Web Application (Master Data Services)</span></span>
  <span data-ttu-id="821ab-103">[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] Web 應用程式提供了一個介面，可讓使用者處理主資料並且讓管理員設定及管理 MDS。</span><span class="sxs-lookup"><span data-stu-id="821ab-103">The [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] web application provides an interface for users to work with master data and for administrators to configure and administer MDS.</span></span>  
  
 <span data-ttu-id="821ab-104">網站中一定要包含 Web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="821ab-104">A web application must always be contained by a website.</span></span> <span data-ttu-id="821ab-105">若要建立 Web 應用程式，您必須：</span><span class="sxs-lookup"><span data-stu-id="821ab-105">To create a web application, you must either:</span></span>  
  
-   <span data-ttu-id="821ab-106">使用預設網站，然後建立 Web 應用程式；</span><span class="sxs-lookup"><span data-stu-id="821ab-106">Use the Default website and then create the web application,</span></span>  
  
-   <span data-ttu-id="821ab-107">使用現有網站，然後建立 Web 應用程式；或者</span><span class="sxs-lookup"><span data-stu-id="821ab-107">Use an existing website and then create the web application, or</span></span>  
  
-   <span data-ttu-id="821ab-108">建立新網站，這樣就會自動建立 Web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="821ab-108">Create a new website, which automatically creates a web application.</span></span>  
  
 <span data-ttu-id="821ab-109">建立 Web 應用程式之後，將它與 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] 資料庫產生關聯。</span><span class="sxs-lookup"><span data-stu-id="821ab-109">After you create the web application, you associate it with the [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] database.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="821ab-110">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="821ab-110">Prerequisites</span></span>  
  
-   <span data-ttu-id="821ab-111">如需主控此 Web 應用程式之電腦需求的資訊，請參閱 [Web 應用程式需求 &#40;Master Data Services&#41;](web-application-requirements-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="821ab-111">For information about the requirements for the computer that hosts the web application, see [Web Application Requirements &#40;Master Data Services&#41;](web-application-requirements-master-data-services.md).</span></span>  
  
## <a name="to-create-a-master-data-manager-web-application-in-a-new-website"></a><span data-ttu-id="821ab-112">在新網站上建立主資料管理員 Web 應用程式</span><span class="sxs-lookup"><span data-stu-id="821ab-112">To create a Master Data Manager web application in a new website</span></span>  
 <span data-ttu-id="821ab-113">當您建立新網站時，根 Web 應用程式會是 [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] Web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="821ab-113">When you create a new website, the root web application is the [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] web application.</span></span> <span data-ttu-id="821ab-114">此 Web 應用程式也會加入至新的應用程式集區。</span><span class="sxs-lookup"><span data-stu-id="821ab-114">The web application is also added to a new application pool.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="821ab-115">如果您依照此程序進行，將無法指定 [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] Web 應用程式的虛擬路徑和別名。</span><span class="sxs-lookup"><span data-stu-id="821ab-115">If you follow this procedure, you cannot specify a virtual path and alias of the [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] web application.</span></span> <span data-ttu-id="821ab-116">如果要指定 [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)]的虛擬路徑及別名，則必須在尚未設定為 [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] Web 應用程式的現有網站上建立 Web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="821ab-116">If you want to specify a virtual path and alias for [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)], you must create a web application in an existing website that is not already configured as a [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] web application.</span></span>  
  
 <span data-ttu-id="821ab-117">此外， [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)] 只支援建立具有 HTTP 繫結的網站。</span><span class="sxs-lookup"><span data-stu-id="821ab-117">Additionally, [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)] supports creating sites with HTTP bindings only.</span></span> <span data-ttu-id="821ab-118">若要加入 HTTPS 繫結，請在 [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)] 中建立新的網站和應用程式，然後參閱 [保護主資料管理員 Web 應用程式](secure-a-master-data-manager-web-application.md) 取得詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="821ab-118">To add an HTTPS binding, create a new site and application in [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)] and then see [Secure a Master Data Manager Web Application](secure-a-master-data-manager-web-application.md) for more information.</span></span>  
  
#### <a name="to-create-a-master-data-manager-web-application-in-a-new-website"></a><span data-ttu-id="821ab-119">在新網站上建立主資料管理員 Web 應用程式</span><span class="sxs-lookup"><span data-stu-id="821ab-119">To create a Master Data Manager web application in a new website</span></span>  
  
1.  <span data-ttu-id="821ab-120">開啟 [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="821ab-120">Open [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)].</span></span>  
  
2.  <span data-ttu-id="821ab-121">按一下左窗格中的 **[Web 組態]** 。</span><span class="sxs-lookup"><span data-stu-id="821ab-121">In the left pane, click **Web Configuration**.</span></span>  
  
3.  <span data-ttu-id="821ab-122">在 **[Web 組態]** 頁面上的網站清單中，選取 **[建立新網站]**。</span><span class="sxs-lookup"><span data-stu-id="821ab-122">On the **Web Configuration** page, in the Website list, select **Create new website**.</span></span>  
  
4.  <span data-ttu-id="821ab-123">在 **[建立網站]** 對話方塊中，指定新網站的資訊。</span><span class="sxs-lookup"><span data-stu-id="821ab-123">On the **Create Website** dialog box, specify information for a new website.</span></span> <span data-ttu-id="821ab-124">如需此對話方塊之使用者介面 (UI) 選項的詳細資訊，請參閱[建立網站對話方塊 &#40;Master Data Services 組態管理員&#41;](../create-website-dialog-box-master-data-services-configuration-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="821ab-124">For more information about the user interface (UI) options in the dialog box, see [Create Website Dialog Box &#40;Master Data Services Configuration Manager&#41;](../create-website-dialog-box-master-data-services-configuration-manager.md).</span></span>  
  
5.  <span data-ttu-id="821ab-125">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="821ab-125">Click **OK**.</span></span>  
  
## <a name="to-create-a-master-data-manager-web-application-in-an-existing-website"></a><span data-ttu-id="821ab-126">在現有網站上建立主資料管理員 Web 應用程式</span><span class="sxs-lookup"><span data-stu-id="821ab-126">To create a Master Data Manager web application in an existing website</span></span>  
 <span data-ttu-id="821ab-127">當您在現有網站上建立 Web 應用程式時，可以選擇 Web 應用程式的虛擬路徑及別名。</span><span class="sxs-lookup"><span data-stu-id="821ab-127">When you create a web application in an existing website, you can choose the virtual path and alias of the web application.</span></span> <span data-ttu-id="821ab-128">此 Web 應用程式會加入至新的應用程式集區。</span><span class="sxs-lookup"><span data-stu-id="821ab-128">The web application is added to a new application pool.</span></span>  
  
#### <a name="to-create-a-master-data-manager-web-application-in-an-existing-website"></a><span data-ttu-id="821ab-129">在現有網站上建立主資料管理員 Web 應用程式</span><span class="sxs-lookup"><span data-stu-id="821ab-129">To create a Master Data Manager web application in an existing website</span></span>  
  
1.  <span data-ttu-id="821ab-130">開啟 [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="821ab-130">Open [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)].</span></span>  
  
2.  <span data-ttu-id="821ab-131">按一下左窗格中的 **[Web 組態]** 。</span><span class="sxs-lookup"><span data-stu-id="821ab-131">In the left pane, click **Web Configuration**.</span></span>  
  
3.  <span data-ttu-id="821ab-132">在 **[Web 組態]** 頁面的 **[網站]** 清單中，選取建立 [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] Web 應用程式所在的網站。</span><span class="sxs-lookup"><span data-stu-id="821ab-132">On the **Web Configuration** page, from the **Website** list, select the website in which you want to create the [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] web application.</span></span>  
  
4.  <span data-ttu-id="821ab-133">按一下 **[建立應用程式]**。</span><span class="sxs-lookup"><span data-stu-id="821ab-133">Click **Create Application**.</span></span>  
  
5.  <span data-ttu-id="821ab-134">在 **[建立 Web 應用程式]** 對話方塊中，指定新 Web 應用程式的資訊。</span><span class="sxs-lookup"><span data-stu-id="821ab-134">On the **Create Web Application** dialog box, specify information for a new web application.</span></span> <span data-ttu-id="821ab-135">如需此對話方塊之使用者介面 (UI) 選項的詳細資訊，請參閱[建立 Web 應用程式對話方塊 &#40;Master Data Services 組態管理員&#41;](../create-web-application-dialog-box-master-data-services-configuration-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="821ab-135">For more information about the user interface (UI) options in the dialog box, see [Create Web Application Dialog Box &#40;Master Data Services Configuration Manager&#41;](../create-web-application-dialog-box-master-data-services-configuration-manager.md).</span></span>  
  
6.  <span data-ttu-id="821ab-136">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="821ab-136">Click **OK**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="821ab-137">後續步驟</span><span class="sxs-lookup"><span data-stu-id="821ab-137">Next Steps</span></span>  
  
-   <span data-ttu-id="821ab-138">將此 Web 應用程式關聯至 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] 資料庫。</span><span class="sxs-lookup"><span data-stu-id="821ab-138">Associate the web application with a [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] database.</span></span> <span data-ttu-id="821ab-139">如需詳細資訊，請參閱 [將 Master Data Services 資料庫與 Web 應用程式產生關聯](associate-a-master-data-services-database-and-web-application.md)。</span><span class="sxs-lookup"><span data-stu-id="821ab-139">For more information, see [Associate a Master Data Services Database and Web Application](associate-a-master-data-services-database-and-web-application.md).</span></span>  
  
-   <span data-ttu-id="821ab-140">如果要使用安全通訊端層 (SSL) 加密內容，可以選擇將主控 [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] Web 應用程式的網站設定成使用 HTTPS 繫結。</span><span class="sxs-lookup"><span data-stu-id="821ab-140">Optionally, configure the website that hosts the [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] web application to use an HTTPS binding if you want to encrypt content by using Secure Sockets Layer (SSL).</span></span> <span data-ttu-id="821ab-141">您必須使用 Internet Information Services (IIS) 工具 (如 IIS 管理員)，才可設定 Web 伺服器的伺服器憑證，以及設定 HTTPS 繫結與網站的 SSL 設定。</span><span class="sxs-lookup"><span data-stu-id="821ab-141">You must use an Internet Information Services (IIS) tool, such as IIS Manager, to configure the server certificate for the web server, and to configure an HTTPS binding and the SSL settings for the site.</span></span> <span data-ttu-id="821ab-142">如需詳細資訊，請參閱 [Secure a Master Data Manager Web Application](secure-a-master-data-manager-web-application.md)。</span><span class="sxs-lookup"><span data-stu-id="821ab-142">For more information, see [Secure a Master Data Manager Web Application](secure-a-master-data-manager-web-application.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="821ab-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="821ab-143">See Also</span></span>  
 [<span data-ttu-id="821ab-144">安裝 Master Data Services</span><span class="sxs-lookup"><span data-stu-id="821ab-144">Install Master Data Services</span></span>](install-master-data-services.md)  
  
  
