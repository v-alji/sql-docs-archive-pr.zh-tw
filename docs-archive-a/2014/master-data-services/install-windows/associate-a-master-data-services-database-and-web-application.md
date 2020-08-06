---
title: 建立 Master Data Services 資料庫與 Web 應用程式的關聯 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: ccb25672-f71d-4135-b548-f50eb45d8fa5
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 01afde6aea5065a51cb9e7ae5dc4151e9f1e9fc7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687953"
---
# <a name="associate-a-master-data-services-database-and-web-application"></a><span data-ttu-id="4cb2f-102">建立 Master Data Services 資料庫與 Web 應用程式的關聯</span><span class="sxs-lookup"><span data-stu-id="4cb2f-102">Associate a Master Data Services Database and Web Application</span></span>
  <span data-ttu-id="4cb2f-103">將 [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] Web 應用程式與 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] 資料庫產生關聯，以指定要用於 Web 作業的資料庫。</span><span class="sxs-lookup"><span data-stu-id="4cb2f-103">Associate your [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] web application with a [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] database to specify the database to use for web operations.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="4cb2f-104">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="4cb2f-104">Prerequisites</span></span>  
  
-   [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)] <span data-ttu-id="4cb2f-105">必須安裝在本機電腦上。</span><span class="sxs-lookup"><span data-stu-id="4cb2f-105">must be installed on the local computer.</span></span> <span data-ttu-id="4cb2f-106">如需詳細資訊，請參閱 [安裝 Master Data Services](install-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="4cb2f-106">For more information, see [Install Master Data Services](install-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="4cb2f-107">必須存在本機 [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] Web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="4cb2f-107">A local [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] web application must exist.</span></span> <span data-ttu-id="4cb2f-108">如需詳細資訊，請參閱[建立主資料管理員 Web 應用程式 &#40;Master Data Services&#41;](create-a-master-data-manager-web-application-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="4cb2f-108">For more information, see [Create a Master Data Manager Web Application &#40;Master Data Services&#41;](create-a-master-data-manager-web-application-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="4cb2f-109">本機或遠端 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] 資料庫必須存在。</span><span class="sxs-lookup"><span data-stu-id="4cb2f-109">Either a local or remote [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] database must exist.</span></span> <span data-ttu-id="4cb2f-110">如需詳細資訊，請參閱 [建立 Master Data Services 資料庫](create-a-master-data-services-database.md)。</span><span class="sxs-lookup"><span data-stu-id="4cb2f-110">For more information, see [Create a Master Data Services Database](create-a-master-data-services-database.md).</span></span>  
  
### <a name="to-associate-a-master-data-services-database-and-web-application"></a><span data-ttu-id="4cb2f-111">將 Master Data Services 資料庫與 Web 應用程式產生關聯</span><span class="sxs-lookup"><span data-stu-id="4cb2f-111">To associate a Master Data Services database and web application</span></span>  
  
1.  <span data-ttu-id="4cb2f-112">開啟 [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="4cb2f-112">Open [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)].</span></span>  
  
2.  <span data-ttu-id="4cb2f-113">按一下左窗格中的 **[Web 組態]** 。</span><span class="sxs-lookup"><span data-stu-id="4cb2f-113">In the left pane, click **Web Configuration**.</span></span>  
  
3.  <span data-ttu-id="4cb2f-114">在 [Web 組態]\*\*\*\* 頁面的 [Web 應用程式]\*\*\*\* 底下，從 [網站]\*\*\*\* 清單中選取包含您的 [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] Web 應用程式之網站。</span><span class="sxs-lookup"><span data-stu-id="4cb2f-114">On the **Web Configuration** page, under **Web application**, from the **Website** list, select the website that contains your [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] web application.</span></span>  
  
4.  <span data-ttu-id="4cb2f-115">在 [Web 應用程式]\*\*\*\* 方塊中，選取主控 [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] 的 Web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="4cb2f-115">In the **Web application** box, select the web application that hosts [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)].</span></span>  
  
5.  <span data-ttu-id="4cb2f-116">在 [將應用程式與資料庫產生關聯]\*\*\*\* 底下，按一下 [選取]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4cb2f-116">Under **Associate Application with Database**, click **Select**.</span></span> <span data-ttu-id="4cb2f-117">[連接到資料庫]\*\*\*\* 對話方塊隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="4cb2f-117">The **Connect to Database** dialog box opens.</span></span>  
  
6.  <span data-ttu-id="4cb2f-118">為主控 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] 資料庫的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體指定連接資訊，然後按一下 [連接]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4cb2f-118">Specify connection information for the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that hosts the [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] database, and click **Connect**.</span></span>  
  
7.  <span data-ttu-id="4cb2f-119">從 [Master Data Services 資料庫]\*\*\*\* 清單，選取要與 Web 應用程式產生關聯的資料庫，然後按一下 [確定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4cb2f-119">From the **Master Data Services database** list, select the database you want to associate the web application with and then click **OK**.</span></span>  
  
8.  <span data-ttu-id="4cb2f-120">確認 [將應用程式與資料庫產生關聯]\*\*\*\* 底下的執行個體和資料庫資訊都正確無誤，然後按一下 [套用]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4cb2f-120">Under **Associate Application with Database**, verify that the instance and database information are correct, and then click **Apply**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="4cb2f-121">後續步驟</span><span class="sxs-lookup"><span data-stu-id="4cb2f-121">Next Steps</span></span>  
  
-   <span data-ttu-id="4cb2f-122">建立 Web 應用程式時，會自動啟用對 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] Web 服務的程式設計存取。</span><span class="sxs-lookup"><span data-stu-id="4cb2f-122">Programmatic access to [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] web services is automatically enabled when the web application is created.</span></span> <span data-ttu-id="4cb2f-123">為了讓開發人員可存取服務中繼資料，輕鬆地為程式設計存取產生 Proxy 類別，啟用中繼資料發佈。</span><span class="sxs-lookup"><span data-stu-id="4cb2f-123">To let developers access the service metadata to easily generate proxy classes for programmatic access, enable metadata publishing.</span></span> <span data-ttu-id="4cb2f-124">如需詳細資訊，請參閱 [建立主資料管理員 Web 服務 Proxy 類別](../develop/create-master-data-manager-web-service-proxy-classes.md)。</span><span class="sxs-lookup"><span data-stu-id="4cb2f-124">For more information, see [Create Master Data Manager Web Service Proxy Classes](../develop/create-master-data-manager-web-service-proxy-classes.md).</span></span>  
  
-   <span data-ttu-id="4cb2f-125">將使用者和群組加入至 [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="4cb2f-125">Add users and groups to [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)].</span></span> <span data-ttu-id="4cb2f-126">如果沒有使用者或群組已獲授權存取 [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)]，您必須使用 [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] 系統管理員認證來開啟 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="4cb2f-126">If no users or groups have been granted access to [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)], you must open [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] using the [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] system administrator credentials.</span></span> <span data-ttu-id="4cb2f-127">如需詳細資訊，請參閱 [Administrators &#40;Master Data Services&#41;](../administrators-master-data-services.md) (管理員 (Master Data Services)) 和 [Users and Groups &#40;Master Data Services&#41;](../users-and-groups-master-data-services.md) (使用者和群組 (Master Data Services))。</span><span class="sxs-lookup"><span data-stu-id="4cb2f-127">For more information, see [Administrators &#40;Master Data Services&#41;](../administrators-master-data-services.md) and [Users and Groups &#40;Master Data Services&#41;](../users-and-groups-master-data-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4cb2f-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4cb2f-128">See Also</span></span>  
 <span data-ttu-id="4cb2f-129">[安裝 Master Data Services](install-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="4cb2f-129">[Install Master Data Services](install-master-data-services.md) </span></span>  
 [<span data-ttu-id="4cb2f-130">Web 組態頁面 &#40;Master Data Services 組態管理員&#41;</span><span class="sxs-lookup"><span data-stu-id="4cb2f-130">Web Configuration Page &#40;Master Data Services Configuration Manager&#41;</span></span>](../web-configuration-page-master-data-services-configuration-manager.md)  
  
  
