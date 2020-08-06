---
title: 建立 Master Data Services 資料庫 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: 8373bb35-f0f9-4c3c-a53c-dfaa2ce567ac
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 9ee90ac5d02489da3b411b12389e949ff3136287
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592720"
---
# <a name="create-a-master-data-services-database"></a><span data-ttu-id="b0c21-102">建立 Master Data Services 資料庫</span><span class="sxs-lookup"><span data-stu-id="b0c21-102">Create a Master Data Services Database</span></span>
  <span data-ttu-id="b0c21-103">當您需要新的資料庫支援 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] Web 應用程式及 [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] Web 服務時，請建立 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] 資料庫。</span><span class="sxs-lookup"><span data-stu-id="b0c21-103">Create a [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] database when you need a new database to support the [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] web application and [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] web service.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="b0c21-104">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="b0c21-104">Prerequisites</span></span>  
  
-   <span data-ttu-id="b0c21-105">如需主控資料庫之電腦需求的相關資訊，請參閱[資料庫需求 &#40;Master Data Services&#41;](database-requirements-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="b0c21-105">For information about the requirements for the computer that hosts the database, see [Database Requirements &#40;Master Data Services&#41;](database-requirements-master-data-services.md).</span></span>  
  
### <a name="to-create-a-master-data-services-database"></a><span data-ttu-id="b0c21-106">若要建立 Master Data Services 資料庫</span><span class="sxs-lookup"><span data-stu-id="b0c21-106">To create a Master Data Services database</span></span>  
  
1.  <span data-ttu-id="b0c21-107">開啟 [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="b0c21-107">Open [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)].</span></span>  
  
2.  <span data-ttu-id="b0c21-108">按一下左窗格中的 [資料庫組態]。</span><span class="sxs-lookup"><span data-stu-id="b0c21-108">In the left pane, click **Database Configuration**.</span></span>  
  
3.  <span data-ttu-id="b0c21-109">在 [資料庫組態]\*\*\*\* 頁面上，按一下 [建立資料庫]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b0c21-109">On the **Database Configuration** page, click **Create Database**.</span></span>  
  
4.  <span data-ttu-id="b0c21-110">完成 [建立資料庫]\*\*\*\* 精靈，建立及設定此資料庫。</span><span class="sxs-lookup"><span data-stu-id="b0c21-110">Complete the **Create Database** wizard to create and configure the database.</span></span> <span data-ttu-id="b0c21-111">如需精靈中之使用者介面 (UI) 選項的相關資訊，請參閱 [Create Database Wizard &#40;Master Data Services Configuration Manager&#41;](../create-database-wizard-master-data-services-configuration-manager.md) (建立資料庫精靈 (Master Data Services 組態管理員))。</span><span class="sxs-lookup"><span data-stu-id="b0c21-111">For information about the user interface (UI) options in the wizard, see [Create Database Wizard &#40;Master Data Services Configuration Manager&#41;](../create-database-wizard-master-data-services-configuration-manager.md).</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="b0c21-112">後續步驟</span><span class="sxs-lookup"><span data-stu-id="b0c21-112">Next Steps</span></span>  
  
-   <span data-ttu-id="b0c21-113">設定資料庫及 Web 應用程式的系統設定。</span><span class="sxs-lookup"><span data-stu-id="b0c21-113">Configure system settings for the database and web application.</span></span> <span data-ttu-id="b0c21-114">如需詳細資訊，請參閱 [系統設定 &#40;Master Data Services&#41;](../system-settings-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="b0c21-114">For more information, see [System Settings &#40;Master Data Services&#41;](../system-settings-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="b0c21-115">建立要關聯到此資料庫的 [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] Web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="b0c21-115">Create a [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] web application to associate with this database.</span></span> <span data-ttu-id="b0c21-116">如需詳細資訊，請參閱[建立主資料管理員 Web 應用程式 &#40;Master Data Services&#41;](create-a-master-data-manager-web-application-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="b0c21-116">For more information, see [Create a Master Data Manager Web Application &#40;Master Data Services&#41;](create-a-master-data-manager-web-application-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="b0c21-117">設定維護計畫來備份資料庫和交易記錄。</span><span class="sxs-lookup"><span data-stu-id="b0c21-117">Configure a maintenance plan to back up the database and transaction logs.</span></span> <span data-ttu-id="b0c21-118">如需詳細資訊，請參閱[資料庫需求 &#40;Master Data Services&#41;](database-requirements-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="b0c21-118">For more information, see [Database Requirements &#40;Master Data Services&#41;](database-requirements-master-data-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0c21-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b0c21-119">See Also</span></span>  
 [<span data-ttu-id="b0c21-120">安裝 Master Data Services</span><span class="sxs-lookup"><span data-stu-id="b0c21-120">Install Master Data Services</span></span>](install-master-data-services.md)  
  
  
