---
title: 在執行管理中心的 Web 前端伺服器上安裝 ADOMD.NET |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: c2372180-e847-4cdb-b267-4befac3faf7e
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 0d9f52bf612c4878a8dacd4f5acfdcc135ae115e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585778"
---
# <a name="install-adomdnet-on-web-front-end-servers-running-central-administration"></a><span data-ttu-id="e080a-102">在執行管理中心的 Web 前端伺服器上安裝 ADOMD.NET</span><span class="sxs-lookup"><span data-stu-id="e080a-102">Install ADOMD.NET on Web Front-End Servers Running Central Administration</span></span>
  <span data-ttu-id="e080a-103">如果您將 PowerPivot for SharePoint 安裝到具有管理中心拓撲的伺服器陣列中 (沒有 Excel Services 或 PowerPivot for SharePoint)，若要完整存取 PowerPivot 管理儀表板中的內建報表，請下載及安裝 Microsoft ADOMD.NET 用戶端程式庫。</span><span class="sxs-lookup"><span data-stu-id="e080a-103">If you install PowerPivot for SharePoint into a farm that has the topology of Central Administration, without Excel Services or PowerPivot for SharePoint, download and install the Microsoft ADOMD.NET client library if you want full access to the built-in reports in the PowerPivot management dashboard.</span></span> <span data-ttu-id="e080a-104">儀表板中的某些報表會使用 ADOMD.NET 來存取內部資料，這些資料會提供關於在伺服陣列中 PowerPivot 查詢處理和伺服器健全狀況的報告資料。</span><span class="sxs-lookup"><span data-stu-id="e080a-104">Some reports in the dashboard use ADOMD.NET to access internal data that provides reporting data on PowerPivot query processing and server health in the farm.</span></span>  
  
 <span data-ttu-id="e080a-105">**[!INCLUDE[applies](../../includes/applies-md.md)]** SharePoint 2010</span><span class="sxs-lookup"><span data-stu-id="e080a-105">**[!INCLUDE[applies](../../includes/applies-md.md)]**  SharePoint 2010</span></span>  
  
 <span data-ttu-id="e080a-106">若為 SharePoint 2013，提供者內含在 SQL Server 功能套件中。</span><span class="sxs-lookup"><span data-stu-id="e080a-106">For SharePoint 2013, the provider is included in the SQL Server feature pack.</span></span> <span data-ttu-id="e080a-107">如需有關如何下載 spPowerPivot.msi 的詳細資訊，請參閱[Microsoft SQL Server 2014 功能套件](https://www.microsoft.com/download/details.aspx?id=35577)</span><span class="sxs-lookup"><span data-stu-id="e080a-107">For information on how to download spPowerPivot.msi, see [Microsoft SQL Server 2014 Feature Pack](https://www.microsoft.com/download/details.aspx?id=35577)</span></span>  
  
### <a name="download-and-install-the-client-library"></a><span data-ttu-id="e080a-108">下載和安裝用戶端文件庫</span><span class="sxs-lookup"><span data-stu-id="e080a-108">Download and install the client library</span></span>  
  
1.  <span data-ttu-id="e080a-109">在 [ [SQL Server 2014 功能套件] 頁面](https://go.microsoft.com/fwlink/?LinkID=296473)上，尋找 Microsoft ADOMD.NET。</span><span class="sxs-lookup"><span data-stu-id="e080a-109">On the [SQL Server 2014 Feature Pack page](https://go.microsoft.com/fwlink/?LinkID=296473), find Microsoft ADOMD.NET.</span></span>  
  
2.  <span data-ttu-id="e080a-110">下載 `SQL_AS_ADOMD.msi` 安裝程式的 x64 封裝。</span><span class="sxs-lookup"><span data-stu-id="e080a-110">Download the x64 Package of the `SQL_AS_ADOMD.msi` installation program.</span></span>  
  
3.  <span data-ttu-id="e080a-111">執行 .msi 以安裝程式庫。</span><span class="sxs-lookup"><span data-stu-id="e080a-111">Run the .msi to install the library.</span></span>  
  
4.  <span data-ttu-id="e080a-112">當安裝完成之後，重設 IIS。</span><span class="sxs-lookup"><span data-stu-id="e080a-112">Reset IIS after installation is finished.</span></span> <span data-ttu-id="e080a-113">開啟系統管理命令提示字元，並輸入**IISRESET**。</span><span class="sxs-lookup"><span data-stu-id="e080a-113">Open an administrative command prompt and type **IISRESET**.</span></span>  
  
### <a name="verify-installation"></a><span data-ttu-id="e080a-114">確認安裝</span><span class="sxs-lookup"><span data-stu-id="e080a-114">Verify installation</span></span>  
  
1.  <span data-ttu-id="e080a-115">移至 Windows\Assembly。</span><span class="sxs-lookup"><span data-stu-id="e080a-115">Go to Windows\Assembly.</span></span>  
  
2.  <span data-ttu-id="e080a-116">以滑鼠右鍵按一下 Microsoft.analysisservices Microsoft.analysisservices.adomdclient，然後選取 [**屬性**]。</span><span class="sxs-lookup"><span data-stu-id="e080a-116">Right-click Microsoft.AnalysisServices.AdomdClient and select **Properties**.</span></span>  
  
3.  <span data-ttu-id="e080a-117">按一下 **[版本]**。</span><span class="sxs-lookup"><span data-stu-id="e080a-117">Click **Version**.</span></span>  
  
4.  <span data-ttu-id="e080a-118">確認版本包含12.00。\<build number></span><span class="sxs-lookup"><span data-stu-id="e080a-118">Verify that the version includes 12.00.\<build number></span></span> <span data-ttu-id="e080a-119">而且描述是 Microsoft.analysisservice.adomdclient. Microsoft.analysisservices.adomdclient。</span><span class="sxs-lookup"><span data-stu-id="e080a-119">and that the description is Microsoft.AnalysisService.AdomdClient.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e080a-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e080a-120">See Also</span></span>  
 [<span data-ttu-id="e080a-121">PowerPivot 管理儀表板和使用量資料</span><span class="sxs-lookup"><span data-stu-id="e080a-121">PowerPivot Management Dashboard and Usage Data</span></span>](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/power-pivot-management-dashboard-and-usage-data)  
  
  
