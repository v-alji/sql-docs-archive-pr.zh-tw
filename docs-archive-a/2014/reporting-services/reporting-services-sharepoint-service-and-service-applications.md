---
title: Reporting Services SharePoint 服務和服務應用程式 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 501aa9ee-8c13-458c-bf6f-24e00c82681b
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 5654764f7913002cdae58d3264848250a292c585
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87607262"
---
# <a name="reporting-services-sharepoint-service-and-service-applications"></a><span data-ttu-id="77f59-102">Reporting Services SharePoint 服務和服務應用程式</span><span class="sxs-lookup"><span data-stu-id="77f59-102">Reporting Services SharePoint Service and Service Applications</span></span>
  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] <span data-ttu-id="77f59-103">SharePoint 模式是以 SharePoint 服務架構為基礎進行架構，並且利用 SharePoint 服務和一對多服務應用程式。</span><span class="sxs-lookup"><span data-stu-id="77f59-103">SharePoint mode is architected on the SharePoint service architecture and utilizes a SharePoint service and one to many service applications.</span></span> <span data-ttu-id="77f59-104">建立服務應用程式可讓服務變成可用，並產生服務應用程式資料庫。</span><span class="sxs-lookup"><span data-stu-id="77f59-104">Creating a service application makes the service available and generates the service application database.</span></span> <span data-ttu-id="77f59-105">您可以建立多個 Reporting Services 服務應用程式，但是一個服務應用程式就足以應付大部分的部署狀況。</span><span class="sxs-lookup"><span data-stu-id="77f59-105">You can create multiple Reporting Services service applications but one service application is sufficient for most deployment scenarios.</span></span>  
  
 <span data-ttu-id="77f59-106">本主題涵蓋下列資訊：</span><span class="sxs-lookup"><span data-stu-id="77f59-106">This topic covers the following information:</span></span>  
  
-   [<span data-ttu-id="77f59-107">建立 Reporting Services 服務應用程式</span><span class="sxs-lookup"><span data-stu-id="77f59-107">Creating a Reporting Services Service Application</span></span>](#bkmk_createapp)  
  
-   [<span data-ttu-id="77f59-108">修改服務應用程式與 Proxy 群組的關聯</span><span class="sxs-lookup"><span data-stu-id="77f59-108">Modify the Associations of the Service Application with a proxy group</span></span>](#bkmk_associations)  
  
-   [<span data-ttu-id="77f59-109">編輯服務應用程式屬性</span><span class="sxs-lookup"><span data-stu-id="77f59-109">Edit Service Application Properties</span></span>](#bkmk_editserviceapplication)  
  
-   [<span data-ttu-id="77f59-110">使用 PowerShell 建立 Reporting Services 服務應用程式</span><span class="sxs-lookup"><span data-stu-id="77f59-110">To create a Reporting Services Service Application using PowerShell</span></span>](#bkmk_powershell_create_ssrs_serviceapp)  
  
-   [<span data-ttu-id="77f59-111">相關工作</span><span class="sxs-lookup"><span data-stu-id="77f59-111">Related Tasks</span></span>](#bkmk_related)  
  
##  <a name="creating-a-reporting-services-service-application"></a><a name="bkmk_createapp"></a><span data-ttu-id="77f59-112">建立 Reporting Services 服務應用程式</span><span class="sxs-lookup"><span data-stu-id="77f59-112">Creating a Reporting Services Service Application</span></span>  
 <span data-ttu-id="77f59-113">您可以使用 SharePoint 管理中心或 PowerShell 指令碼建立 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 服務應用程式。</span><span class="sxs-lookup"><span data-stu-id="77f59-113">You can use SharePoint Central Administration or PowerShell scripts to create the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] services applications.</span></span> <span data-ttu-id="77f59-114">如需使用 SharePoint 管理中心的詳細資訊，請參閱[安裝適用於 SharePoint 2010 的 Reporting Services SharePoint 模式](../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md)中的＜建立 Reporting Services 服務應用程式＞一節。</span><span class="sxs-lookup"><span data-stu-id="77f59-114">For more information on using SharePoint Central Administration, see the "Create a Reporting Services Service Application" section in [Install Reporting Services SharePoint Mode for SharePoint 2010](../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md).</span></span> <span data-ttu-id="77f59-115">如需建立服務應用程式的範例 PowerShell 指令碼，請參閱本主題稍後的＜PowerShell＞一節。</span><span class="sxs-lookup"><span data-stu-id="77f59-115">See the PowerShell section later in this topic for a sample PowerShell script for creating service applications.</span></span>  
  
##  <a name="modify-the-associations-of-the-service-application-with-a-proxy-group"></a><a name="bkmk_associations"></a><span data-ttu-id="77f59-116">修改服務應用程式與 proxy 群組的關聯</span><span class="sxs-lookup"><span data-stu-id="77f59-116">Modify the Associations of the Service Application with a proxy group</span></span>  
 <span data-ttu-id="77f59-117">建立服務應用程式的 [新增] 頁面包含 **[Web 應用程式關聯]** 區段。</span><span class="sxs-lookup"><span data-stu-id="77f59-117">The New page for creating a services application contains the section **Web Application Association**.</span></span> <span data-ttu-id="77f59-118">此區段可讓您在建立服務應用程式時產生關聯。</span><span class="sxs-lookup"><span data-stu-id="77f59-118">The section allows you to associate your service application as you create it.</span></span> <span data-ttu-id="77f59-119">使用下列步驟變更關聯並將客戶組態指派至服務應用程式。</span><span class="sxs-lookup"><span data-stu-id="77f59-119">Use the following steps to change the association and assign a customer configuration to the service application.</span></span> <span data-ttu-id="77f59-120">您也可以使用相同的一般程序將 Proxy 加入至預設群組，而不是將服務應用程式的關聯變更為自訂群組。</span><span class="sxs-lookup"><span data-stu-id="77f59-120">The same general process can also be used to add the proxy to the default group rather than changing the association of the service application to a custom group.</span></span>  
  
1.  <span data-ttu-id="77f59-121">在 [SharePoint 管理中心] 的 [應用程式管理] 中，按一下 **[設定服務應用程式關聯]**。</span><span class="sxs-lookup"><span data-stu-id="77f59-121">In SharePoint Central Administration, in the Application Management, click **Configure Service Application Associations**.</span></span>  
  
2.  <span data-ttu-id="77f59-122">在 [服務應用程式關聯] 頁面上，將檢視切換至 **[服務應用程式]**。</span><span class="sxs-lookup"><span data-stu-id="77f59-122">On the Service application Associations page, change the view to **Service Applications**.</span></span>  
  
3.  <span data-ttu-id="77f59-123">尋找並按一下新的 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 服務應用程式的名稱。</span><span class="sxs-lookup"><span data-stu-id="77f59-123">Find and click the name of your new [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] Service application.</span></span> <span data-ttu-id="77f59-124">您也可以按一下應用程式 Proxy 群組名稱 **default** ，將 Proxy 加入至預設群組，而不要完成下列步驟。</span><span class="sxs-lookup"><span data-stu-id="77f59-124">You could also click the application proxy group name **default** to add the proxy to default group rather than completing the following steps.</span></span>  
  
4.  <span data-ttu-id="77f59-125">在 **[編輯下列連線群組]** 選取方塊中選取 **[自訂]**。</span><span class="sxs-lookup"><span data-stu-id="77f59-125">Select **Custom** in the selection box **Edit the following group of connections**.</span></span>  
  
5.  <span data-ttu-id="77f59-126">核取您的 Proxy 的方塊，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="77f59-126">Check the box for your proxy and click **Ok**.</span></span>  
  
##  <a name="edit-service-application-properties"></a><a name="bkmk_editserviceapplication"></a><span data-ttu-id="77f59-127">編輯服務應用程式屬性</span><span class="sxs-lookup"><span data-stu-id="77f59-127">Edit Service Application Properties</span></span>  
 <span data-ttu-id="77f59-128">您可以再次開啟服務應用程式的屬性頁來修改屬性。</span><span class="sxs-lookup"><span data-stu-id="77f59-128">You can reopen the property page of the service application to modify the properties.</span></span>  
  
1.  <span data-ttu-id="77f59-129">在 [SharePoint 管理中心] 的 [應用程式管理] 群組中，按一下 [**管理服務應用程式**]。</span><span class="sxs-lookup"><span data-stu-id="77f59-129">In SharePoint Central Administration, in the Application Management group, click **Manage service applications**.</span></span>  
  
2.  <span data-ttu-id="77f59-130">按一下類型資料行選取整個資料列，藉此選取服務應用程式。</span><span class="sxs-lookup"><span data-stu-id="77f59-130">Select the service application by clicking the type column to select the entire row.</span></span> <span data-ttu-id="77f59-131">如果您按一下應用程式的名稱，則會開啟服務的 [管理] 選項頁面，而不是開啟服務應用程式的屬性。</span><span class="sxs-lookup"><span data-stu-id="77f59-131">If you click the name of the application it, the Management options page for the service opens instead of opening the properties of the service application.</span></span>  
  
3.  <span data-ttu-id="77f59-132">在 [服務應用程式] 功能區中，按一下 **[內容]**。</span><span class="sxs-lookup"><span data-stu-id="77f59-132">In the Service Applications ribbon, click **Properties**.</span></span>  
  
##  <a name="to-create-a-reporting-services-service-application-using-powershell"></a><a name="bkmk_powershell_create_ssrs_serviceapp"></a><span data-ttu-id="77f59-133">使用 PowerShell 建立 Reporting Services 服務應用程式</span><span class="sxs-lookup"><span data-stu-id="77f59-133">To create a Reporting Services Service Application using PowerShell</span></span>  
 <span data-ttu-id="77f59-134">您可以使用 PowerShell 建立服務應用程式和 Proxy。</span><span class="sxs-lookup"><span data-stu-id="77f59-134">You can use PowerShell to create the Service application and proxy.</span></span> <span data-ttu-id="77f59-135">下方範例是假設您知道要設定服務應用程式使用哪個應用程式集區。</span><span class="sxs-lookup"><span data-stu-id="77f59-135">The sample below assumes that you know what application pool you want to configure the service application to use.</span></span>  
  
1.  <span data-ttu-id="77f59-136">將應用程式集區名稱的應用程式集區物件加入至要傳遞到 [新增] 動作的變數中。</span><span class="sxs-lookup"><span data-stu-id="77f59-136">Add the application pool object of your application pool name to a variable that is passed into the New action.</span></span>  
  
    ```powershell
    $appPoolName = Get-SPServiceApplicationPool "<application pool name>"  
    ```  
  
2.  <span data-ttu-id="77f59-137">使用您提供的名稱與應用程式集區名稱建立服務應用程式。</span><span class="sxs-lookup"><span data-stu-id="77f59-137">Create the service application with a name and application pool name you provide.</span></span>  
  
    ```powershell
    New-SPRSServiceApplication -Name 'MyServiceApplication' -ApplicationPool $appPoolName -DatabaseName 'MyServiceApplicationDatabase' -DatabaseServer '<Server Name>'  
    ```  
  
3.  <span data-ttu-id="77f59-138">取得新的服務應用程式物件，並且將物件以管道傳送至 Pipe 新 Proxy Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="77f59-138">Get the new service application object, and pipe the object into the Pipe the new proxy cmdlet.</span></span>  
  
    ```powershell
    Get-SPRSServiceApplication -name MyServiceApplication | New-SPRSServiceApplicationProxy "MyServiceApplicationProxy"  
    ```  
  
##  <a name="related-tasks"></a><a name="bkmk_related"></a> <span data-ttu-id="77f59-139">相關工作</span><span class="sxs-lookup"><span data-stu-id="77f59-139">Related Tasks</span></span>  
  
|<span data-ttu-id="77f59-140">Task</span><span class="sxs-lookup"><span data-stu-id="77f59-140">Task</span></span>|<span data-ttu-id="77f59-141">連結</span><span class="sxs-lookup"><span data-stu-id="77f59-141">Link</span></span>|  
|----------|----------|  
|<span data-ttu-id="77f59-142">管理服務應用程式的設定。</span><span class="sxs-lookup"><span data-stu-id="77f59-142">Manage the settings of your Service Application.</span></span>|[<span data-ttu-id="77f59-143">Manage a Reporting Services SharePoint Service Application</span><span class="sxs-lookup"><span data-stu-id="77f59-143">Manage a Reporting Services SharePoint Service Application</span></span>](../../2014/reporting-services/manage-a-reporting-services-sharepoint-service-application.md)|  
|<span data-ttu-id="77f59-144">備份和還原服務應用程式及相關元件，例如加密金鑰和 Proxy。</span><span class="sxs-lookup"><span data-stu-id="77f59-144">Backup and restore the service application and related components such as encryption keys and proxy.</span></span>|[<span data-ttu-id="77f59-145">備份與還原 Reporting Services SharePoint 服務應用程式</span><span class="sxs-lookup"><span data-stu-id="77f59-145">Backup and Restore Reporting Services SharePoint Service Applications</span></span>](../../2014/reporting-services/backup-and-restore-reporting-services-sharepoint-service-applications.md)|  
