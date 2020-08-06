---
title: 開啟或關閉 Reporting Services 功能 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- Reporting Services, configuration
- security [Reporting Services], strategies
ms.assetid: b69db02a-43a7-4fdc-ad9b-438d817a7f83
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f56f9984b5b02431db23b782652e5575af557bdb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595622"
---
# <a name="turn-reporting-services-features-on-or-off"></a><span data-ttu-id="a86a5-102">開啟或關閉 Reporting Services 功能</span><span class="sxs-lookup"><span data-stu-id="a86a5-102">Turn Reporting Services Features On or Off</span></span>
  <span data-ttu-id="a86a5-103">您可以關閉鎖定策略中未使用的報表伺服器功能，以減少實際執行報表伺服器的攻擊面。</span><span class="sxs-lookup"><span data-stu-id="a86a5-103">You can turn off report server features that you do not use as part of a lockdown strategy for reducing the attack surface of a production report server.</span></span> <span data-ttu-id="a86a5-104">在大多數情況下，您會想要同時執行 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 功能，以便能夠使用 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]中所提供的所有功能。</span><span class="sxs-lookup"><span data-stu-id="a86a5-104">In most cases, you will want to run [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] features concurrently to use all of the functionality provided in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="a86a5-105">不過，根據部署模型而定，您可以停用不需要的功能。</span><span class="sxs-lookup"><span data-stu-id="a86a5-105">However, depending on your deployment model, you can disable the features that you do not require.</span></span> <span data-ttu-id="a86a5-106">例如，如果所有報表處理都設定為排程的作業，您就可以只啟用背景處理。</span><span class="sxs-lookup"><span data-stu-id="a86a5-106">For example, you can enable only the background processing if all report processing is configured as scheduled operations.</span></span> <span data-ttu-id="a86a5-107">同樣地，如果只想要視需要執行的互動式報表，可以只執行報表伺服器 Web 服務。</span><span class="sxs-lookup"><span data-stu-id="a86a5-107">Similarly, you can run just the Report Server Web service if you only want interactive, on-demand reporting.</span></span>  
  
 <span data-ttu-id="a86a5-108">本主題中的程序將示範如何關閉原生模式 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 功能。</span><span class="sxs-lookup"><span data-stu-id="a86a5-108">The procedures in this topic show you how to turn off native mode [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] features.</span></span> <span data-ttu-id="a86a5-109">您可以透過不同的方式來設定功能，例如直接編輯 `RsReportServer.config` 檔案，或是在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中，使用以原則為基礎之管理的 [Reporting Services 的介面區設定] Facet。</span><span class="sxs-lookup"><span data-stu-id="a86a5-109">Features can be configured in different ways, such as by editing the `RsReportServer.config` file directly or by using the **Surface Area Configuration for Reporting Services** facet of Policy-Based Management in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="a86a5-110">使用下列連結即可找到說明如何開啟或關閉功能的程序：</span><span class="sxs-lookup"><span data-stu-id="a86a5-110">Use the links to locate the procedure or procedures that explain how to turn a feature on or off:</span></span>  
  
-   [<span data-ttu-id="a86a5-111">報表伺服器 Web 服務</span><span class="sxs-lookup"><span data-stu-id="a86a5-111">Report Server Web service</span></span>](#RSWebSvc)  
  
-   [<span data-ttu-id="a86a5-112">排程的事件和處理</span><span class="sxs-lookup"><span data-stu-id="a86a5-112">Scheduled events and processing</span></span>](#Sched)  
  
-   [<span data-ttu-id="a86a5-113">報表管理員</span><span class="sxs-lookup"><span data-stu-id="a86a5-113">Report Manager</span></span>](#ReportManager)  
  
-   [<span data-ttu-id="a86a5-114">報表產生器</span><span class="sxs-lookup"><span data-stu-id="a86a5-114">Report Builder</span></span>](#ReportBuilder)  
  
-   [<span data-ttu-id="a86a5-115">報表資料來源的 Windows 整合式安全性</span><span class="sxs-lookup"><span data-stu-id="a86a5-115">Windows Integrated security for report data sources</span></span>](#WinIntSec)  
  
##  <a name="report-server-web-service"></a><a name="RSWebSvc"></a><span data-ttu-id="a86a5-116">報表伺服器 Web 服務</span><span class="sxs-lookup"><span data-stu-id="a86a5-116">Report Server Web Service</span></span>  
  
#### <a name="to-turn-on-or-off-the-report-server-web-service-by-editing-configuration"></a><span data-ttu-id="a86a5-117">透過編輯組態來開啟或關閉報表伺服器 Web 服務</span><span class="sxs-lookup"><span data-stu-id="a86a5-117">To turn on or off the Report Server Web service by editing configuration</span></span>  
  
1.  <span data-ttu-id="a86a5-118">在文字編輯器中開啟 `RsReportServer.config` 檔案。</span><span class="sxs-lookup"><span data-stu-id="a86a5-118">Open the `RsReportServer.config` file in a text editor.</span></span> <span data-ttu-id="a86a5-119">如需詳細資訊，請參閱《[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 線上叢書》中的[修改 Reporting Services 設定檔 &#40;RSreportserver.config&#41;](modify-a-reporting-services-configuration-file-rsreportserver-config.md)。</span><span class="sxs-lookup"><span data-stu-id="a86a5-119">For more information, see [Modify a Reporting Services Configuration File &#40;RSreportserver.config&#41;](modify-a-reporting-services-configuration-file-rsreportserver-config.md) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
2.  <span data-ttu-id="a86a5-120">若要開啟報表伺服器 Web 服務，請將 `IsWebServiceEnabled` 設定為 `true`：</span><span class="sxs-lookup"><span data-stu-id="a86a5-120">To turn on the Report Server Web service, set `IsWebServiceEnabled` to `true`:</span></span>  
  
    ```  
    <IsWebServiceEnabled>true</IsWebServiceEnabled>  
    ```  
  
3.  <span data-ttu-id="a86a5-121">若要關閉報表伺服器 Web 服務，請將 `IsWebServiceEnabled` 設定為 `false`：</span><span class="sxs-lookup"><span data-stu-id="a86a5-121">To turn off the Report Server Web service, set `IsWebServiceEnabled` to `false`:</span></span>  
  
    ```  
    <IsWebServiceEnabled>false</IsWebServiceEnabled>  
    ```  
  
4.  <span data-ttu-id="a86a5-122">儲存您的變更，然後關閉檔案。</span><span class="sxs-lookup"><span data-stu-id="a86a5-122">Save your changes and then close the file.</span></span>  
  
#### <a name="to-turn-on-or-off-the-report-server-web-service-by-using-sql-server-management-studio"></a><span data-ttu-id="a86a5-123">使用 SQL Server Management Studio 來開啟或關閉報表伺服器 Web 服務</span><span class="sxs-lookup"><span data-stu-id="a86a5-123">To turn on or off the Report Server Web service by using SQL Server Management Studio</span></span>  
  
1.  <span data-ttu-id="a86a5-124">開啟 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 並連接至您想要設定的 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="a86a5-124">Open [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] and connect to the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] instance that you want to configure.</span></span>  
  
2.  <span data-ttu-id="a86a5-125">在物件總管中，以滑鼠右鍵按一下 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 節點，指向 [**原則**]，然後按一下 [ **facet**]。</span><span class="sxs-lookup"><span data-stu-id="a86a5-125">In Object Explorer, right-click the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] node, point to **Policies**, and click **Facets**.</span></span>  
  
3.  <span data-ttu-id="a86a5-126">在 **[Facet]** 清單中，選取 **[Reporting Services 的介面區組態]**。</span><span class="sxs-lookup"><span data-stu-id="a86a5-126">In the **Facet** list, select **Surface Area Configuration for Reporting Services**.</span></span>  
  
4.  <span data-ttu-id="a86a5-127">在 **[Facet 屬性]** 底下：</span><span class="sxs-lookup"><span data-stu-id="a86a5-127">Under **Facet Properties**:</span></span>  
  
    -   <span data-ttu-id="a86a5-128">若要開啟報表伺服器 Web 服務，請將**webserviceandHTTPaccessenabled]** 設定為 `True` 。</span><span class="sxs-lookup"><span data-stu-id="a86a5-128">To turn on the Report Server Web service, set **WebServiceAndHTTPAccessEnabled** to `True`.</span></span>  
  
    -   <span data-ttu-id="a86a5-129">若要關閉報表伺服器 Web 服務，請將**webserviceandHTTPaccessenabled]** 設定為 `False` 。</span><span class="sxs-lookup"><span data-stu-id="a86a5-129">To turn off the Report Server Web service, set **WebServiceAndHTTPAccessEnabled** to `False`.</span></span>  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
##  <a name="scheduled-events-and-delivery"></a><a name="Sched"></a><span data-ttu-id="a86a5-130">Scheduled Events 和傳遞</span><span class="sxs-lookup"><span data-stu-id="a86a5-130">Scheduled Events and Delivery</span></span>  
  
#### <a name="to-turn-on-or-off-scheduled-events-and-delivery-by-editing-configuration"></a><span data-ttu-id="a86a5-131">透過編輯組態來開啟或關閉排程的事件和傳遞</span><span class="sxs-lookup"><span data-stu-id="a86a5-131">To turn on or off scheduled events and delivery by editing configuration</span></span>  
  
1.  <span data-ttu-id="a86a5-132">在文字編輯器中開啟 RsReportServer.config 檔。</span><span class="sxs-lookup"><span data-stu-id="a86a5-132">Open the RsReportServer.config file in a text editor.</span></span> <span data-ttu-id="a86a5-133">如需詳細資訊，請參閱《[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 線上叢書》中的[修改 Reporting Services 設定檔 &#40;RSreportserver.config&#41;](modify-a-reporting-services-configuration-file-rsreportserver-config.md)。</span><span class="sxs-lookup"><span data-stu-id="a86a5-133">For more information, see [Modify a Reporting Services Configuration File &#40;RSreportserver.config&#41;](modify-a-reporting-services-configuration-file-rsreportserver-config.md) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
2.  <span data-ttu-id="a86a5-134">若要開啟排程的報表處理和傳遞，請將 `IsSchedulingService`、`IsNotificationService` 和 `IsEventService` 設定為 `true`：</span><span class="sxs-lookup"><span data-stu-id="a86a5-134">To turn on scheduled report processing and delivery, set `IsSchedulingService`, `IsNotificationService`, and `IsEventService` to `true`:</span></span>  
  
    ```  
    <IsSchedulingService>true</IsSchedulingService>  
    <IsNotificationService>true</IsNotificationService>  
    <IsEventService>true</IsEventService>  
    ```  
  
3.  <span data-ttu-id="a86a5-135">若要關閉排程的報表處理和傳遞，請將 `IsSchedulingService`、`IsNotificationService` 和 `IsEventService` 設定為 `false`：</span><span class="sxs-lookup"><span data-stu-id="a86a5-135">To turn off scheduled report processing and delivery, set `IsSchedulingService`, `IsNotificationService`, and `IsEventService` to `false`:</span></span>  
  
    ```  
    <IsSchedulingService>false</IsSchedulingService>  
    <IsNotificationService>false</IsNotificationService>  
    <IsEventService>false</IsEventService>  
    ```  
  
4.  <span data-ttu-id="a86a5-136">儲存您的變更，然後關閉檔案。</span><span class="sxs-lookup"><span data-stu-id="a86a5-136">Save your changes and then close the file.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a86a5-137">您不能完全關閉背景處理，因為它提供了伺服器作業所需的資料庫維護功能。</span><span class="sxs-lookup"><span data-stu-id="a86a5-137">You cannot turn off background processing completely because it provides database maintenance functionality that is required for server operations.</span></span>  
  
#### <a name="to-turn-on-or-off-scheduled-events-and-delivery-by-using-sql-server-management-studio"></a><span data-ttu-id="a86a5-138">使用 SQL Server Management Studio 來開啟或關閉排程的事件和傳遞</span><span class="sxs-lookup"><span data-stu-id="a86a5-138">To turn on or off scheduled events and delivery by using SQL Server Management Studio</span></span>  
  
1.  <span data-ttu-id="a86a5-139">開啟 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 並連接至您想要設定的 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="a86a5-139">Open [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] and connect to the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] instance that you want to configure.</span></span>  
  
2.  <span data-ttu-id="a86a5-140">在物件總管中，以滑鼠右鍵按一下 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 節點，指向 [**原則**]，然後按一下 [ **facet**]。</span><span class="sxs-lookup"><span data-stu-id="a86a5-140">In Object Explorer, right-click the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] node, point to **Policies**, and click **Facets**.</span></span>  
  
3.  <span data-ttu-id="a86a5-141">在 **[Facet]** 清單中，選取 **[Reporting Services 的介面區組態]**。</span><span class="sxs-lookup"><span data-stu-id="a86a5-141">In the **Facet** list, select **Surface Area Configuration for Reporting Services**.</span></span>  
  
4.  <span data-ttu-id="a86a5-142">在 **[Facet 屬性]** 底下：</span><span class="sxs-lookup"><span data-stu-id="a86a5-142">Under **Facet Properties**:</span></span>  
  
    -   <span data-ttu-id="a86a5-143">若要開啟排程的事件和傳遞，請將 **[scheduleeventsandreportdeliveryenabled 設定**設定為 `True` 。</span><span class="sxs-lookup"><span data-stu-id="a86a5-143">To turn on scheduled events and delivery, set **ScheduleEventsAndReportDeliveryEnabled** to `True`.</span></span>  
  
    -   <span data-ttu-id="a86a5-144">若要關閉排程的事件和傳遞，請將 **[scheduleeventsandreportdeliveryenabled 設定**設定為 `False` 。</span><span class="sxs-lookup"><span data-stu-id="a86a5-144">To turn off scheduled events and delivery, set **ScheduleEventsAndReportDeliveryEnabled** to `False`.</span></span>  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
> [!NOTE]  
>  <span data-ttu-id="a86a5-145">您不能完全關閉背景處理，因為它提供了伺服器作業所需的資料庫維護功能。</span><span class="sxs-lookup"><span data-stu-id="a86a5-145">You cannot turn off background processing completely because it provides database maintenance functionality that is required for server operations.</span></span>  
  
##  <a name="report-manager"></a><a name="ReportManager"></a><span data-ttu-id="a86a5-146">報表管理員</span><span class="sxs-lookup"><span data-stu-id="a86a5-146">Report Manager</span></span>  
  
#### <a name="to-turn-on-or-off-report-manager-by-editing-configuration"></a><span data-ttu-id="a86a5-147">透過編輯組態來開啟或關閉報表管理員</span><span class="sxs-lookup"><span data-stu-id="a86a5-147">To turn on or off Report Manager by editing configuration</span></span>  
  
1.  <span data-ttu-id="a86a5-148">在文字編輯器中開啟 RsReportServer.config 檔。</span><span class="sxs-lookup"><span data-stu-id="a86a5-148">Open the RsReportServer.config file in a text editor.</span></span> <span data-ttu-id="a86a5-149">如需指示，請參閱《[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 線上叢書》中的[修改 Reporting Services 組態檔 &#40;RSreportserver.config&#41;](modify-a-reporting-services-configuration-file-rsreportserver-config.md)。</span><span class="sxs-lookup"><span data-stu-id="a86a5-149">For instructions, see [Modify a Reporting Services Configuration File &#40;RSreportserver.config&#41;](modify-a-reporting-services-configuration-file-rsreportserver-config.md) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
2.  <span data-ttu-id="a86a5-150">若要開啟報表管理員，請將 `IsReportManagerEnabled` 設定為 `true`：</span><span class="sxs-lookup"><span data-stu-id="a86a5-150">To turn on Report Manager, set `IsReportManagerEnabled` to `true`:</span></span>  
  
    ```  
    <IsReportManagerEnabled>true</IsReportManagerEnabled>  
    ```  
  
3.  <span data-ttu-id="a86a5-151">若要關閉報表管理員，請將 `IsReportManagerEnabled` 設定為 `false`：</span><span class="sxs-lookup"><span data-stu-id="a86a5-151">To turn off Report Manager, set `IsReportManagerEnabled` to `false`:</span></span>  
  
    ```  
    <IsReportManagerEnabled>false</IsReportManagerEnabled>  
    ```  
  
4.  <span data-ttu-id="a86a5-152">儲存您的變更，然後關閉檔案。</span><span class="sxs-lookup"><span data-stu-id="a86a5-152">Save your changes and then close the file.</span></span>  
  
#### <a name="to-turn-on-or-off-report-manager-by-using-sql-server-management-studio"></a><span data-ttu-id="a86a5-153">使用 SQL Server Management Studio 來開啟或關閉報表管理員</span><span class="sxs-lookup"><span data-stu-id="a86a5-153">To turn on or off Report Manager by using SQL Server Management Studio</span></span>  
  
1.  <span data-ttu-id="a86a5-154">開啟 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 並連接至您想要設定的 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="a86a5-154">Open [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] and connect to the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] instance that you want to configure.</span></span>  
  
2.  <span data-ttu-id="a86a5-155">在**物件總管**中，以滑鼠右鍵按一下 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 節點，指向 [原則]\*\*\*\*，然後按一下 [Facet]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="a86a5-155">In **Object Explorer**, right-click the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] node, point to **Policies**, and click **Facets**.</span></span>  
  
3.  <span data-ttu-id="a86a5-156">在 **[Facet]** 清單中，選取 **[Reporting Services 的介面區組態]**。</span><span class="sxs-lookup"><span data-stu-id="a86a5-156">In the **Facet** list, select **Surface Area Configuration for Reporting Services**.</span></span>  
  
4.  <span data-ttu-id="a86a5-157">在 **[Facet 屬性]** 底下：</span><span class="sxs-lookup"><span data-stu-id="a86a5-157">Under **Facet Properties**:</span></span>  
  
    -   <span data-ttu-id="a86a5-158">若要開啟報表管理員，請將 **[reportmanagerenabled**設定為 `True` 。</span><span class="sxs-lookup"><span data-stu-id="a86a5-158">To turn on Report Manager, set **ReportManagerEnabled** to `True`.</span></span>  
  
    -   <span data-ttu-id="a86a5-159">若要關閉報表管理員，請將 **[reportmanagerenabled**設定為 `False` 。</span><span class="sxs-lookup"><span data-stu-id="a86a5-159">To turn off Report Manager, set **ReportManagerEnabled** to `False`.</span></span>  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
##  <a name="report-builder"></a><a name="ReportBuilder"></a> <span data-ttu-id="a86a5-160">報表產生器</span><span class="sxs-lookup"><span data-stu-id="a86a5-160">Report Builder</span></span>  
  
#### <a name="to-turn-on-or-off-report-builder-by-using-sql-server-management-studio"></a><span data-ttu-id="a86a5-161">使用 SQL Server Management Studio 來開啟或關閉報表產生器</span><span class="sxs-lookup"><span data-stu-id="a86a5-161">To turn on or off Report Builder by using SQL Server Management Studio</span></span>  
  
1.  <span data-ttu-id="a86a5-162">開啟 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 並連接至您想要設定的 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="a86a5-162">Open [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] and connect to the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] instance that you want to configure.</span></span>  
  
2.  <span data-ttu-id="a86a5-163">在物件總管中，以滑鼠右鍵按一下 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 節點，然後按一下 [屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="a86a5-163">In Object Explorer, right-click the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] node, and click **Properties**.</span></span>  
  
3.  <span data-ttu-id="a86a5-164">在 **[伺服器屬性]** 對話方塊的 **[選取頁面]** 底下，按一下 **[安全性]**。</span><span class="sxs-lookup"><span data-stu-id="a86a5-164">In the **Server Properties** dialog box, under **Select a page**, click **Security**.</span></span>  
  
    -   <span data-ttu-id="a86a5-165">若要開啟報表產生器，請選取 **[啟用隨選報表執行]** 選項。</span><span class="sxs-lookup"><span data-stu-id="a86a5-165">To turn on Report Builder, select the **Enable ad hoc report executions** option.</span></span>  
  
    -   <span data-ttu-id="a86a5-166">若要關閉報表產生器，請取消選取 **[啟用隨選報表執行]** 選項。</span><span class="sxs-lookup"><span data-stu-id="a86a5-166">To turn off Report Builder, unselect the **Enable ad hoc report executions** option.</span></span>  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
##  <a name="windows-integrated-security"></a><a name="WinIntSec"></a> <span data-ttu-id="a86a5-167">Windows 整合式安全性</span><span class="sxs-lookup"><span data-stu-id="a86a5-167">Windows Integrated Security</span></span>  
  
#### <a name="to-turn-on-or-off-windows-integrated-security-by-using-sql-server-management-studio"></a><span data-ttu-id="a86a5-168">使用 SQL Server Management Studio 來開啟或關閉 Windows 整合式安全性</span><span class="sxs-lookup"><span data-stu-id="a86a5-168">To turn on or off Windows Integrated security by using SQL Server Management Studio</span></span>  
  
1.  <span data-ttu-id="a86a5-169">開啟 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 並連接至您想要設定的 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="a86a5-169">Open [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] and connect to the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] instance that you want to configure.</span></span>  
  
2.  <span data-ttu-id="a86a5-170">在物件總管中，以滑鼠右鍵按一下 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 節點，然後按一下 [屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="a86a5-170">In Object Explorer, right-click the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] node, and click **Properties**.</span></span>  
  
3.  <span data-ttu-id="a86a5-171">在 **[伺服器屬性]** 對話方塊的 **[選取頁面]** 底下，按一下 **[安全性]**。</span><span class="sxs-lookup"><span data-stu-id="a86a5-171">In the **Server Properties** dialog box, under **Select a page**, click **Security**.</span></span>  
  
    -   <span data-ttu-id="a86a5-172">若要開啟 Windows 整合式安全性，請選取 **[為報表資料來源啟用 Windows 整合式安全性]** 選項。</span><span class="sxs-lookup"><span data-stu-id="a86a5-172">To turn on Windows Integrated security, select the **Enable Windows Integrated security for report data sources** option.</span></span>  
  
    -   <span data-ttu-id="a86a5-173">若要關閉 Windows 整合式安全性，請取消選取 **[為報表資料來源啟用 Windows 整合式安全性]** 選項。</span><span class="sxs-lookup"><span data-stu-id="a86a5-173">To turn off Windows integrated security, unselect the **Enable Windows Integrated security for report data sources** option.</span></span>  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="a86a5-174">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a86a5-174">See Also</span></span>  
 [<span data-ttu-id="a86a5-175">Reporting Services 組態管理員 &#40;原生模式&#41;</span><span class="sxs-lookup"><span data-stu-id="a86a5-175">Reporting Services Configuration Manager &#40;Native Mode&#41;</span></span>](../../sql-server/install/reporting-services-configuration-manager-native-mode.md)  
  
  
