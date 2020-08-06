---
title: 啟用 Data Quality Services 與 Master Data Services 的整合 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: ab32938d-a80e-4106-80d4-94b2de3d67dc
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 8d2fa25254cae2a129b6e08ff657d92af4ff9455
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594119"
---
# <a name="enable-data-quality-services-integration-with-master-data-services"></a><span data-ttu-id="3b95a-102">啟用 Data Quality Services 與 Master Data Services 的整合</span><span class="sxs-lookup"><span data-stu-id="3b95a-102">Enable Data Quality Services Integration with Master Data Services</span></span>
  <span data-ttu-id="3b95a-103">在 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]中，比對功能是由 Data Quality Services (DQS) 提供。</span><span class="sxs-lookup"><span data-stu-id="3b95a-103">In the [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], matching functionality is provided by Data Quality Services (DQS).</span></span> <span data-ttu-id="3b95a-104">此功能必須啟用才能使用。</span><span class="sxs-lookup"><span data-stu-id="3b95a-104">This functionality must be enabled to be used.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="3b95a-105">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="3b95a-105">Prerequisites</span></span>  
  
-   <span data-ttu-id="3b95a-106">[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] Web 應用程式和資料庫必須存在。</span><span class="sxs-lookup"><span data-stu-id="3b95a-106">A [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] web application and database must exist.</span></span>  
  
-   <span data-ttu-id="3b95a-107">Data Quality Services 功能和 Data Quality Client 必須安裝在裝載 MDS 資料庫的相同 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體上。</span><span class="sxs-lookup"><span data-stu-id="3b95a-107">The Data Quality Services feature and the Data Quality Client must be installed on the same [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance that hosts the MDS database.</span></span> <span data-ttu-id="3b95a-108">如需詳細資訊，請參閱 [安裝 Data Quality Services](../../data-quality-services/install-windows/install-data-quality-services.md)。</span><span class="sxs-lookup"><span data-stu-id="3b95a-108">For more information, see [Install Data Quality Services](../../data-quality-services/install-windows/install-data-quality-services.md).</span></span>  
  
### <a name="to-enable-data-quality-services-integration"></a><span data-ttu-id="3b95a-109">若要啟用 Data Quality Services 整合</span><span class="sxs-lookup"><span data-stu-id="3b95a-109">To enable Data Quality Services integration</span></span>  
  
1.  <span data-ttu-id="3b95a-110">開啟 [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="3b95a-110">Open [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)].</span></span>  
  
2.  <span data-ttu-id="3b95a-111">按一下左窗格中的 **[Web 組態]** 。</span><span class="sxs-lookup"><span data-stu-id="3b95a-111">In the left pane, click **Web Configuration**.</span></span>  
  
3.  <span data-ttu-id="3b95a-112">在 [Web 組態]\*\*\*\* 頁面上，選取網站和 Web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="3b95a-112">On the **Web Configuration** page, select the website and web application.</span></span>  
  
4.  <span data-ttu-id="3b95a-113">在 [啟用 DQS 整合]\*\*\*\* 區段中，按一下 [啟用與 Data Quality Services 整合]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="3b95a-113">In the **Enable DQS Integration** section, click **Enable integration with Data Quality Services**.</span></span>  
  
5.  <span data-ttu-id="3b95a-114">在確認對話方塊中按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="3b95a-114">On the confirmation dialog box, click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b95a-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3b95a-115">See Also</span></span>  
 <span data-ttu-id="3b95a-116">[適用于 Excel 的 MDS 增益集中的資料品質比對](../microsoft-excel-add-in/data-quality-matching-in-the-mds-add-in-for-excel.md) </span><span class="sxs-lookup"><span data-stu-id="3b95a-116">[Data Quality Matching in the MDS Add-in for Excel](../microsoft-excel-add-in/data-quality-matching-in-the-mds-add-in-for-excel.md) </span></span>  
 <span data-ttu-id="3b95a-117">[適用於 Microsoft Excel 的 Master Data Services 增益集](../microsoft-excel-add-in/master-data-services-add-in-for-microsoft-excel.md) </span><span class="sxs-lookup"><span data-stu-id="3b95a-117">[Master Data Services Add-in for Microsoft Excel](../microsoft-excel-add-in/master-data-services-add-in-for-microsoft-excel.md) </span></span>  
 [<span data-ttu-id="3b95a-118">安裝 Master Data Services</span><span class="sxs-lookup"><span data-stu-id="3b95a-118">Install Master Data Services</span></span>](install-master-data-services.md)  
  
  
