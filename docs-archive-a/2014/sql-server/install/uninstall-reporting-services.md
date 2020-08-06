---
title: 解除安裝 Reporting Services | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: 5c764a00-d4bc-465d-b32e-e4efce052ce4
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 2870f7f84ea626b96560af586602996de3657276
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595435"
---
# <a name="uninstall-reporting-services"></a><span data-ttu-id="787e4-102">解除安裝 Reporting Services</span><span class="sxs-lookup"><span data-stu-id="787e4-102">Uninstall Reporting Services</span></span>
  <span data-ttu-id="787e4-103">解除安裝 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 不會移除您已建立的內容或是您已修改的組態。</span><span class="sxs-lookup"><span data-stu-id="787e4-103">Uninstalling [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] does not remove the content you have created or configuration you have modified.</span></span> <span data-ttu-id="787e4-104">不過，如果有解除安裝完成之後需要的內容，建議您先建立內容的複本，然後再開始進行解除安裝程序。</span><span class="sxs-lookup"><span data-stu-id="787e4-104">However, if there is content you need after the uninstall is complete, it is recommended you make copies of content before you begin the uninstallation process.</span></span>

## <a name="uninstall-sharepoint-mode"></a><span data-ttu-id="787e4-105">解除安裝 SharePoint 模式</span><span class="sxs-lookup"><span data-stu-id="787e4-105">Uninstall SharePoint Mode</span></span>
 <span data-ttu-id="787e4-106">解除安裝 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint 模式時會一併移除下列各項：</span><span class="sxs-lookup"><span data-stu-id="787e4-106">When you uninstall [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint mode, the following are removed:</span></span>

-   [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="787e4-107">服務和服務 Proxy。</span><span class="sxs-lookup"><span data-stu-id="787e4-107">service and service proxy.</span></span>

-   <span data-ttu-id="787e4-108">用於 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 安裝的檔案。</span><span class="sxs-lookup"><span data-stu-id="787e4-108">Files used for the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] installation.</span></span>

 <span data-ttu-id="787e4-109">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 服務應用程式則不會移除。</span><span class="sxs-lookup"><span data-stu-id="787e4-109">The [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service applications are not removed.</span></span> <span data-ttu-id="787e4-110">如果您不再需要服務應用程式，可以使用 Windows PowerShell 或 SharePoint 管理中心刪除它們。</span><span class="sxs-lookup"><span data-stu-id="787e4-110">If you no longer want the service applications, delete them by using Windows PowerShell or SharePoint Central Administration.</span></span>

 <span data-ttu-id="787e4-111">報表項目和相關中繼資料則不會移除。</span><span class="sxs-lookup"><span data-stu-id="787e4-111">The report items and related meta data are not removed.</span></span> <span data-ttu-id="787e4-112">這項資訊包含在與 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 服務應用程式相關的內容和組態資料庫中。</span><span class="sxs-lookup"><span data-stu-id="787e4-112">This information is contained in the content and configuration databases related to the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service applications.</span></span> <span data-ttu-id="787e4-113">資料庫不會移除，而且您可以手動將資料庫移轉至 SharePoint 模式下的另一個 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 安裝。</span><span class="sxs-lookup"><span data-stu-id="787e4-113">The databases are not removed and you can manually migrate the databases to another installation of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] in SharePoint mode.</span></span> <span data-ttu-id="787e4-114">如果您不再需要資訊，請刪除資料庫。</span><span class="sxs-lookup"><span data-stu-id="787e4-114">If you no longer want the information, delete the databases.</span></span> <span data-ttu-id="787e4-115">如需詳細資訊，請參閱＜ [Upgrade and Migrate Reporting Services](../../reporting-services/install-windows/upgrade-and-migrate-reporting-services.md)＞。</span><span class="sxs-lookup"><span data-stu-id="787e4-115">For more information, see [Upgrade and Migrate Reporting Services](../../reporting-services/install-windows/upgrade-and-migrate-reporting-services.md).</span></span>

 <span data-ttu-id="787e4-116">以下是三個不會移除之 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 資料庫的範例名稱。</span><span class="sxs-lookup"><span data-stu-id="787e4-116">The following are example names of the three [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] databases that are not removed.</span></span>

-   <span data-ttu-id="787e4-117">**報表伺服器資料庫：** ReportingService_7f616e2d253040e8ab5653b3c09a065e</span><span class="sxs-lookup"><span data-stu-id="787e4-117">**Report server database:** ReportingService_7f616e2d253040e8ab5653b3c09a065e</span></span>

-   <span data-ttu-id="787e4-118">**報表伺服器暫存資料庫：** ReportingService_7f616e2d253040e8ab5653b3c09a065eTempDB</span><span class="sxs-lookup"><span data-stu-id="787e4-118">**Report server temp database:** ReportingService_7f616e2d253040e8ab5653b3c09a065eTempDB</span></span>

-   <span data-ttu-id="787e4-119">**報表伺服器警示資料庫：** ReportingService_7f616e2d253040e8ab5653b3c09a065e_Alerting</span><span class="sxs-lookup"><span data-stu-id="787e4-119">**Report server alerting database:** ReportingService_7f616e2d253040e8ab5653b3c09a065e_Alerting</span></span>

### <a name="uninstall-the-add-in-for-sharepoint-products"></a><span data-ttu-id="787e4-120">解除安裝適用於 SharePoint 產品的增益集</span><span class="sxs-lookup"><span data-stu-id="787e4-120">Uninstall the Add-in for SharePoint Products.</span></span>
 <span data-ttu-id="787e4-121">當您從電腦解除安裝增益集時，可以選擇只從伺服器陣列解除安裝檔案，或是一併移除 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 功能。</span><span class="sxs-lookup"><span data-stu-id="787e4-121">When you uninstall the add-in from a computer, you can choose to only uninstall the files or to also remove the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] feature from the farm.</span></span> <span data-ttu-id="787e4-122">如需卸載 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 適用于 sharepoint 產品之增益集的詳細資訊，請參閱[安裝或卸載適用于 sharepoint 的 Reporting Services 增益集 &#40;sharepoint 2010 和 sharepoint 2013&#41;](../../reporting-services/install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md)。</span><span class="sxs-lookup"><span data-stu-id="787e4-122">For information on uninstalling the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] add-in for SharePoint products, see [Install or Uninstall the Reporting Services Add-in for SharePoint &#40;SharePoint 2010 and SharePoint 2013&#41;](../../reporting-services/install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md).</span></span>

## <a name="uninstall-native-mode"></a><span data-ttu-id="787e4-123">解除安裝原生模式</span><span class="sxs-lookup"><span data-stu-id="787e4-123">Uninstall Native Mode</span></span>
 <span data-ttu-id="787e4-124">當您解除安裝 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 原生模式時，安裝之後所 **建立** 或 **修改** 的任何內容都會保持原狀。</span><span class="sxs-lookup"><span data-stu-id="787e4-124">When you uninstall [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] native mode, anything that was **created** or **modified** after the installation is left in place.</span></span> <span data-ttu-id="787e4-125">例如，資料庫檔案、記錄檔、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 組態檔和內容項目 (如報表和資料來源檔案)。</span><span class="sxs-lookup"><span data-stu-id="787e4-125">For example database files, log files, [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] configuration files, and content items such as reports and datasource files.</span></span>

 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="787e4-126">是執行個體功能，因此不會列在 Windows [控制台] 的 [程式和功能] 中。</span><span class="sxs-lookup"><span data-stu-id="787e4-126">is an instance feature and therefore is not listed in Windows Control Panel, Programs and Features.</span></span> <span data-ttu-id="787e4-127">若要解除安裝 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 原生模式：</span><span class="sxs-lookup"><span data-stu-id="787e4-127">To uninstall [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Native mode:</span></span>

1.  <span data-ttu-id="787e4-128">在 Windows [控制台] 中，按一下 **[程式和功能]** 。</span><span class="sxs-lookup"><span data-stu-id="787e4-128">In Windows Control Panel, click **Programs and Features**.</span></span>

2.  <span data-ttu-id="787e4-129">在 **[程式和功能]** 中，選取 **[Microsoft SQL Server 2012]**。</span><span class="sxs-lookup"><span data-stu-id="787e4-129">In **Programs and Features** select **Microsoft SQL Server 2012**.</span></span>

3.  <span data-ttu-id="787e4-130">在解除安裝精靈中，選取包含 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 執行個體功能 **RS**的執行個體。</span><span class="sxs-lookup"><span data-stu-id="787e4-130">In the uninstall wizard, select the instance that includes the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] instance feature **RS**.</span></span>

     <span data-ttu-id="787e4-131">![rs_nativemode_uninstall_selectinstance](../../../2014/sql-server/install/media/rs-nativemode-uninstall-selectinstance.gif "rs_nativemode_uninstall_selectinstance")</span><span class="sxs-lookup"><span data-stu-id="787e4-131">![rs_nativemode_uninstall_selectinstance](../../../2014/sql-server/install/media/rs-nativemode-uninstall-selectinstance.gif "rs_nativemode_uninstall_selectinstance")</span></span>

4.  <span data-ttu-id="787e4-132">當您選取執行個體之後，請選取 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 功能。</span><span class="sxs-lookup"><span data-stu-id="787e4-132">After you select the instance, select the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] feature.</span></span>

     <span data-ttu-id="787e4-133">![rs_nativemode_uninstall_selectfeatures](../../../2014/sql-server/install/media/rs-nativemode-uninstall-selectfeatures.gif "rs_nativemode_uninstall_selectfeatures")</span><span class="sxs-lookup"><span data-stu-id="787e4-133">![rs_nativemode_uninstall_selectfeatures](../../../2014/sql-server/install/media/rs-nativemode-uninstall-selectfeatures.gif "rs_nativemode_uninstall_selectfeatures")</span></span>

5.  <span data-ttu-id="787e4-134">完成精靈。</span><span class="sxs-lookup"><span data-stu-id="787e4-134">Complete the wizard.</span></span>

## <a name="see-also"></a><span data-ttu-id="787e4-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="787e4-135">See Also</span></span>
 <span data-ttu-id="787e4-136">[卸載 SQL Server 的現有實例 &#40;安裝程式&#41;](../../../2014/sql-server/install/uninstall-an-existing-instance-of-sql-server-setup.md) [安裝或卸載 PowerPivot for SharePoint 增益集 &#40;sharepoint 2013&#41;](https://docs.microsoft.com/analysis-services/instances/install-windows/install-or-uninstall-the-power-pivot-for-sharepoint-add-in-sharepoint-2013) [安裝或卸載適用于 SharePoint Reporting Services sharepoint 2010 和 sharepoint 2013 的 &#40;增益集&#41;](../../reporting-services/install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md)</span><span class="sxs-lookup"><span data-stu-id="787e4-136">[Uninstall an Existing Instance of SQL Server &#40;Setup&#41;](../../../2014/sql-server/install/uninstall-an-existing-instance-of-sql-server-setup.md) [Install or Uninstall the PowerPivot for SharePoint Add-in &#40;SharePoint 2013&#41;](https://docs.microsoft.com/analysis-services/instances/install-windows/install-or-uninstall-the-power-pivot-for-sharepoint-add-in-sharepoint-2013) [Install or Uninstall the Reporting Services Add-in for SharePoint &#40;SharePoint 2010 and SharePoint 2013&#41;](../../reporting-services/install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md)</span></span>


