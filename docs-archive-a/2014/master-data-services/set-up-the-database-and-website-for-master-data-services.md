---
title: 設定 Master Data Services 的資料庫和網站 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
f1_keywords:
- sql12.mds.configmanager.general.f1
ms.assetid: d50863e7-50d9-4ab8-aabb-fd68e2d132a1
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: da797bc6f9838a2baab6cc440cc7d778a7a6e186
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606952"
---
# <a name="set-up-the-database-and-website-for-master-data-services"></a><span data-ttu-id="dfe8c-102">設定 Master Data Services 的資料庫與網站</span><span class="sxs-lookup"><span data-stu-id="dfe8c-102">Set up the Database and Website for Master Data Services</span></span>
  <span data-ttu-id="dfe8c-103">使用 [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] 設定 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] (MDS) 的資料庫與網站</span><span class="sxs-lookup"><span data-stu-id="dfe8c-103">Use the [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] to set up the database and website for [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] (MDS)</span></span>  
  
 <span data-ttu-id="dfe8c-104">若要設定資料庫與網站，請完成下列工作。</span><span class="sxs-lookup"><span data-stu-id="dfe8c-104">To set up the database and website, complete the following tasks.</span></span>  
  
1.  <span data-ttu-id="dfe8c-105">使用 **中的 [資料庫組態]**[!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)]頁面，建立資料庫。</span><span class="sxs-lookup"><span data-stu-id="dfe8c-105">Create a database using the **Database Configuration** page in [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)].</span></span>  
  
     <span data-ttu-id="dfe8c-106">如需詳細資訊，請參閱[資料庫設定頁面 &#40;Master Data Services 組態管理員&#41;](../../2014/master-data-services/database-configuration-page-master-data-services-configuration-manager.md)和[Create Database Wizard &#40;Master Data Services 組態管理員&#41;](../../2014/master-data-services/create-database-wizard-master-data-services-configuration-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="dfe8c-106">For information, see [Database Configuration Page &#40;Master Data Services Configuration Manager&#41;](../../2014/master-data-services/database-configuration-page-master-data-services-configuration-manager.md) and [Create Database Wizard &#40;Master Data Services Configuration Manager&#41;](../../2014/master-data-services/create-database-wizard-master-data-services-configuration-manager.md).</span></span>  
  
2.  <span data-ttu-id="dfe8c-107">使用 **中的 [Web 組態]**[!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)]頁面，建立新的網站、選取預設網站，或選取另一個現有網站。</span><span class="sxs-lookup"><span data-stu-id="dfe8c-107">Create a new website, select the default website, or select another existing website, using the **Web Configuration** page in [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)].</span></span> <span data-ttu-id="dfe8c-108">然後將 MDS 資料庫與您選取或建立的 Web 應用程式相關聯。</span><span class="sxs-lookup"><span data-stu-id="dfe8c-108">Then associate the MDS database with the web application you select or create.</span></span>  
  
     <span data-ttu-id="dfe8c-109">如需詳細資訊，請參閱[Web 設定頁面 &#40;Master Data Services 組態管理員&#41;](../../2014/master-data-services/web-configuration-page-master-data-services-configuration-manager.md)和 [[建立網站] 對話方塊 &#40;Master Data Services 組態管理員&#41;](../../2014/master-data-services/create-website-dialog-box-master-data-services-configuration-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="dfe8c-109">For information, see [Web Configuration Page &#40;Master Data Services Configuration Manager&#41;](../../2014/master-data-services/web-configuration-page-master-data-services-configuration-manager.md) and [Create Website Dialog Box &#40;Master Data Services Configuration Manager&#41;](../../2014/master-data-services/create-website-dialog-box-master-data-services-configuration-manager.md).</span></span>  
  
3.  <span data-ttu-id="dfe8c-110">(選擇性) 使用 **中的 [Web 組態]**[!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)]頁面，啟用與 Data Quality Services 的整合。</span><span class="sxs-lookup"><span data-stu-id="dfe8c-110">(Optional) Enable integration with Data Quality Services using the **Web Configuration** page in [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)].</span></span>  
  
     <span data-ttu-id="dfe8c-111">如需詳細資訊，請參閱[Web 設定頁面 &#40;Master Data Services 組態管理員&#41;](../../2014/master-data-services/web-configuration-page-master-data-services-configuration-manager.md)並[啟用與 Master Data Services 的 Data Quality Services 整合](install-windows/enable-data-quality-services-integration-with-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="dfe8c-111">For more information, see [Web Configuration Page &#40;Master Data Services Configuration Manager&#41;](../../2014/master-data-services/web-configuration-page-master-data-services-configuration-manager.md) and [Enable Data Quality Services Integration with Master Data Services](install-windows/enable-data-quality-services-integration-with-master-data-services.md).</span></span>  
  
 <span data-ttu-id="dfe8c-112">您也可以使用 [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] 指定 Web 應用程式與 MDS 資料庫相關聯之服務的設定。</span><span class="sxs-lookup"><span data-stu-id="dfe8c-112">You can also use [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] to specify settings for the web applications and services associated with the MDS database.</span></span> <span data-ttu-id="dfe8c-113">例如，您可以指定載入資料的頻率，或傳送驗證電子郵件的頻率。</span><span class="sxs-lookup"><span data-stu-id="dfe8c-113">For example, you can specify how frequently data is loaded or how often validation emails are sent.</span></span> <span data-ttu-id="dfe8c-114">如需詳細資訊，請參閱 [系統設定 &#40;Master Data Services&#41;](../../2014/master-data-services/system-settings-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="dfe8c-114">For more information, see [System Settings &#40;Master Data Services&#41;](../../2014/master-data-services/system-settings-master-data-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dfe8c-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dfe8c-115">See Also</span></span>  
 <span data-ttu-id="dfe8c-116">[Master Data Services 資料庫](../../2014/master-data-services/master-data-services-database.md) </span><span class="sxs-lookup"><span data-stu-id="dfe8c-116">[Master Data Services Database](../../2014/master-data-services/master-data-services-database.md) </span></span>  
 [<span data-ttu-id="dfe8c-117">主資料管理員 Web 應用程式</span><span class="sxs-lookup"><span data-stu-id="dfe8c-117">Master Data Manager Web Application</span></span>](../../2014/master-data-services/master-data-manager-web-application.md)  
  
  
