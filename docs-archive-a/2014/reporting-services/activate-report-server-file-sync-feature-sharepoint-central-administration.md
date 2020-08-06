---
title: 在 SharePoint 管理中心內啟用報表伺服器檔案同步處理功能 |Microsoft Docs
ms.prod: sql-server-2014
ms.technology: reporting-services
ms.topic: conceptual
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.reviewer: ''
ms.custom: ''
ms.date: 03/06/2017
ms.openlocfilehash: 55feac69da85c7287ea56f4b8245350dd7e69565
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597666"
---
# <a name="activate-the-report-server-file-sync-feature-in-sharepoint-central-administration"></a><span data-ttu-id="cf393-102">在 SharePoint 管理中心啟動報表伺服器檔案同步處理功能</span><span class="sxs-lookup"><span data-stu-id="cf393-102">Activate the Report Server File Sync Feature in SharePoint Central Administration</span></span>

<span data-ttu-id="cf393-103">[ [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 報表伺服器檔案同步處理] 功能會利用 SharePoint 事件處理常式，同步處理報表伺服器目錄與文件庫中的項目。</span><span class="sxs-lookup"><span data-stu-id="cf393-103">The [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] Report Server File Sync feature utilizes SharePoint event handlers to synchronize the report server catalog with items in document libraries.</span></span> <span data-ttu-id="cf393-104">當使用者經常直接上傳已發行的報表項目至 SharePoint 文件庫時，這項功能會很有幫助。</span><span class="sxs-lookup"><span data-stu-id="cf393-104">This feature is beneficial when users frequently upload published report items directly to SharePoint document libraries.</span></span> <span data-ttu-id="cf393-105">如果檔案同步處理功能未啟用，內容仍會同步處理，但不常頻繁。</span><span class="sxs-lookup"><span data-stu-id="cf393-105">If the file Sync feature isn't activated, content will still be synchronized but not as frequently.</span></span>  
  
<span data-ttu-id="cf393-106">安裝 SharePoint 產品的 [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)] 增益集之後，可以在 SharePoint 網站管理中啟用檔案同步處理功能。</span><span class="sxs-lookup"><span data-stu-id="cf393-106">The File Sync feature can be activated in SharePoint Site Administration after you install the [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)] Add-in for SharePoint products.</span></span>  
  
<span data-ttu-id="cf393-107">這項功能可以在每個網站以手動方式啟用及停用，但不能在網站集合層級啟用及停用。</span><span class="sxs-lookup"><span data-stu-id="cf393-107">This feature can be manually activated and deactivated per site but not at the site collection level.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="cf393-108">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="cf393-108">Prerequisites</span></span>  
 <span data-ttu-id="cf393-109">必須安裝適用於 SharePoint 的 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 增益集。</span><span class="sxs-lookup"><span data-stu-id="cf393-109">The [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] Add-in for SharePoint must be installed.</span></span> <span data-ttu-id="cf393-110">如果未安裝增益集，[網站功能清單] 中就不會顯示檔案同步功能。</span><span class="sxs-lookup"><span data-stu-id="cf393-110">If the add-in isn't installed, the file sync feature won't be visible in the site feature list.</span></span>  
  
 <span data-ttu-id="cf393-111">若要確認安裝，請檢視在 [!INCLUDE[msCoName](../includes/msconame-md.md)] Windows **[控制台]** 中已安裝應用程式的清單。</span><span class="sxs-lookup"><span data-stu-id="cf393-111">To verify installation, view the list of installed applications in [!INCLUDE[msCoName](../includes/msconame-md.md)] Windows **Control Panel**.</span></span> <span data-ttu-id="cf393-112">如果已安裝 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 增益集，請遵循本主題的指示來啟用報表伺服器同步處理功能。</span><span class="sxs-lookup"><span data-stu-id="cf393-112">If the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] Add-in is installed, follow the instructions in this topic to activate the report server file sync feature.</span></span>  
  
### <a name="to-activate-or-deactivate-the-reporting-services-file-sync-feature-on-a-site"></a><span data-ttu-id="cf393-113">在網站上啟用或停用報表伺服器檔案同步處理功能</span><span class="sxs-lookup"><span data-stu-id="cf393-113">To activate or deactivate the Reporting Services File Sync feature on a Site</span></span>  
  
1.  <span data-ttu-id="cf393-114">從網站的主頁面中，按一下 [**網站動作**] 功能表，然後按一下 [**網站設定**]。</span><span class="sxs-lookup"><span data-stu-id="cf393-114">From the main page of your site, click the **Site Actions** menu and click **Site Settings**.</span></span>  
  
2.  <span data-ttu-id="cf393-115">在 [**網站動作**] 中，按一下 [**管理網站功能**]。</span><span class="sxs-lookup"><span data-stu-id="cf393-115">In the **Site Actions**, click **Manage Site Features**.</span></span>  
  
3.  <span data-ttu-id="cf393-116">在清單中找到 **[報表伺服器檔案同步處理]** 。</span><span class="sxs-lookup"><span data-stu-id="cf393-116">Find **Report Server File Sync** in the list.</span></span>  
  
4.  <span data-ttu-id="cf393-117">按一下 [啟用]。</span><span class="sxs-lookup"><span data-stu-id="cf393-117">Click **Activate**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="cf393-118">若要停用報表伺服器檔案同步處理功能，您可以執行相同的程序，但是請按一下 [停用]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="cf393-118">To deactivate the Report Server file sync feature, you can use the same procedure but click **Deactivate**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf393-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cf393-119">See Also</span></span>  
 <span data-ttu-id="cf393-120">[&#40;報表產生器和 SSRS&#41;疑難排解報表元件](report-parts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="cf393-120">[Troubleshoot Report Parts &#40;Report Builder and SSRS&#41;](report-parts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="cf393-121">[在 SharePoint 中啟用報表伺服器和 Power View 整合功能](activate-the-report-server-and-power-view-integration-features-in-sharepoint.md) </span><span class="sxs-lookup"><span data-stu-id="cf393-121">[Activate the Report Server and Power View Integration Features in SharePoint](activate-the-report-server-and-power-view-integration-features-in-sharepoint.md) </span></span>  
 <span data-ttu-id="cf393-122">[安裝或卸載適用于 SharePoint &#40;SharePoint 2010 和 SharePoint 2013 的 Reporting Services 增益集&#41;](install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md) </span><span class="sxs-lookup"><span data-stu-id="cf393-122">[Install or Uninstall the Reporting Services Add-in for SharePoint &#40;SharePoint 2010 and SharePoint 2013&#41;](install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md) </span></span>  
 [<span data-ttu-id="cf393-123">安裝或卸載適用于 SharePoint &#40;SharePoint 2010 和 SharePoint 2013 的 Reporting Services 增益集&#41;</span><span class="sxs-lookup"><span data-stu-id="cf393-123">Install or Uninstall the Reporting Services Add-in for SharePoint &#40;SharePoint 2010 and SharePoint 2013&#41;</span></span>](install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md)  
  
  
