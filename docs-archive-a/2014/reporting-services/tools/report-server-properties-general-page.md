---
title: 伺服器屬性 (一般頁面) | Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.swb.reportserver.serverproperties.general.f1
ms.assetid: 23537d52-4356-450f-a671-5921cef2431f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 66199e35c180790cba5120cb839be67e43052be6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710186"
---
# <a name="server-properties-general-page"></a><span data-ttu-id="1246e-102">伺服器屬性 (一般頁面)</span><span class="sxs-lookup"><span data-stu-id="1246e-102">Server Properties (General Page)</span></span>
  <span data-ttu-id="1246e-103">您可以使用這個頁面來檢視或修改在報表管理員中使用的標題、啟用或停用 [我的報表]、針對 [我的報表] 安全性選取角色定義，以及啟用或停用用戶端列印控制項。</span><span class="sxs-lookup"><span data-stu-id="1246e-103">Use this page to view or modify the title used in Report Manager, enable or disable My Reports, select a role definition for My Reports security, and enable or disable the client print control.</span></span>  
  
 <span data-ttu-id="1246e-104">若要開啟此頁面，請啟動 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 、連接至報表伺服器實例、以滑鼠右鍵按一下報表伺服器名稱，然後選取 [**屬性**]。</span><span class="sxs-lookup"><span data-stu-id="1246e-104">To open this page, start [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connect to a report server instance, right-click the report server name, and then select **Properties**.</span></span>  
  
 <span data-ttu-id="1246e-105">伺服器模式會決定您可以設定的伺服器屬性。</span><span class="sxs-lookup"><span data-stu-id="1246e-105">The server mode determines which server properties you can set.</span></span> <span data-ttu-id="1246e-106">如果您要管理針對 SharePoint 整合模式所設定的報表伺服器，便無法啟用 [我的報表] 或設定報表管理員的應用程式標題。</span><span class="sxs-lookup"><span data-stu-id="1246e-106">If you are managing a report server that is configured for SharePoint integrated mode, you cannot enable My Reports or set the application title for Report Manager.</span></span>  
  
## <a name="options"></a><span data-ttu-id="1246e-107">選項。</span><span class="sxs-lookup"><span data-stu-id="1246e-107">Options</span></span>  
 <span data-ttu-id="1246e-108">**名稱**</span><span class="sxs-lookup"><span data-stu-id="1246e-108">**Name**</span></span>  
 <span data-ttu-id="1246e-109">鍵入報表管理員中顯示的應用程式名稱。</span><span class="sxs-lookup"><span data-stu-id="1246e-109">Type an application name that appears in Report Manager.</span></span> <span data-ttu-id="1246e-110">根據預設，此值為 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="1246e-110">By default, this value is [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="1246e-111">所指定的名稱只會出現在報表管理員中。</span><span class="sxs-lookup"><span data-stu-id="1246e-111">The name that you specify appears only in Report Manager.</span></span>  
  
 <span data-ttu-id="1246e-112">**版本**</span><span class="sxs-lookup"><span data-stu-id="1246e-112">**Version**</span></span>  
 <span data-ttu-id="1246e-113">這個屬性是唯讀的。</span><span class="sxs-lookup"><span data-stu-id="1246e-113">This property is read-only.</span></span> <span data-ttu-id="1246e-114">指定您要使用的版本 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="1246e-114">Specifies the version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] that you are using.</span></span>  
  
 <span data-ttu-id="1246e-115">**版本(Edition)**</span><span class="sxs-lookup"><span data-stu-id="1246e-115">**Edition**</span></span>  
 <span data-ttu-id="1246e-116">這個屬性是唯讀的。</span><span class="sxs-lookup"><span data-stu-id="1246e-116">This property is read-only.</span></span> <span data-ttu-id="1246e-117">指定目前的報表伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="1246e-117">Specifies the current report server instance.</span></span> <span data-ttu-id="1246e-118">並非所有 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="1246e-118">Report Manager is not available in every edition of [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="1246e-119">如需版本支援的功能清單 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，請參閱[SQL Server 2014 版本支援的功能](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)。</span><span class="sxs-lookup"><span data-stu-id="1246e-119">For a list of features that are supported by the editions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], see [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>  
  
 <span data-ttu-id="1246e-120">**驗證模式**</span><span class="sxs-lookup"><span data-stu-id="1246e-120">**Authentication Mode**</span></span>  
 <span data-ttu-id="1246e-121">這個屬性是唯讀的。</span><span class="sxs-lookup"><span data-stu-id="1246e-121">This property is read-only.</span></span> <span data-ttu-id="1246e-122">它會識別報表伺服器執行個體所接受之驗證要求的類型。</span><span class="sxs-lookup"><span data-stu-id="1246e-122">It identifies the types of authentication requests accepted by the report server instance.</span></span> <span data-ttu-id="1246e-123">若要變更驗證模式，您必須編輯 RSReportServer.config 檔。</span><span class="sxs-lookup"><span data-stu-id="1246e-123">To change the authentication mode, you must edit the RSReportServer.config file.</span></span> <span data-ttu-id="1246e-124">如需詳細資訊，請參閱 [Authentication with the Report Server](../security/authentication-with-the-report-server.md)。</span><span class="sxs-lookup"><span data-stu-id="1246e-124">For more information, see [Authentication with the Report Server](../security/authentication-with-the-report-server.md).</span></span>  
  
 <span data-ttu-id="1246e-125">**URL**</span><span class="sxs-lookup"><span data-stu-id="1246e-125">**URL**</span></span>  
 <span data-ttu-id="1246e-126">這個屬性是唯讀的。</span><span class="sxs-lookup"><span data-stu-id="1246e-126">This property is read-only.</span></span> <span data-ttu-id="1246e-127">指定報表伺服器 Web 服務的 URL。</span><span class="sxs-lookup"><span data-stu-id="1246e-127">Specifies the URL to the Report Server Web service.</span></span> <span data-ttu-id="1246e-128">這個值是在 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 組態工具中指定的。</span><span class="sxs-lookup"><span data-stu-id="1246e-128">This value is specified in the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration tool.</span></span> <span data-ttu-id="1246e-129">如需詳細資訊，請參閱[設定 URL &#40;SSRS 組態管理員&#41;](../install-windows/configure-a-url-ssrs-configuration-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="1246e-129">For more information, see [Configure a URL  &#40;SSRS Configuration Manager&#41;](../install-windows/configure-a-url-ssrs-configuration-manager.md).</span></span>  
  
 <span data-ttu-id="1246e-130">**為每個使用者啟用 [我的報表] 資料夾**</span><span class="sxs-lookup"><span data-stu-id="1246e-130">**Enable a My Reports folder for each user**</span></span>  
 <span data-ttu-id="1246e-131">讓使用者可以使用 [我的報表]。</span><span class="sxs-lookup"><span data-stu-id="1246e-131">Make My Reports available to users.</span></span> <span data-ttu-id="1246e-132">這個選項僅適用於原生模式報表伺服器。</span><span class="sxs-lookup"><span data-stu-id="1246e-132">This option is only available for native mode report servers.</span></span>  
  
 <span data-ttu-id="1246e-133">**選取要套用至每個 [我的報表] 資料夾的角色**</span><span class="sxs-lookup"><span data-stu-id="1246e-133">**Select the role to apply to each My Reports folder**</span></span>  
 <span data-ttu-id="1246e-134">指定要用於 [我的報表] 安全性的角色定義。</span><span class="sxs-lookup"><span data-stu-id="1246e-134">Specify a role definition to use for My Reports security.</span></span> <span data-ttu-id="1246e-135">角色定義會識別每個 [我的報表] 資料夾中所支援的這組工作。</span><span class="sxs-lookup"><span data-stu-id="1246e-135">The role definition identifies the set of tasks that are supported in each My Reports folder.</span></span>  
  
 <span data-ttu-id="1246e-136">**啟用 ActiveX 用戶端列印控制項的下載**</span><span class="sxs-lookup"><span data-stu-id="1246e-136">**Enable download for the ActiveX client print control**</span></span>  
 <span data-ttu-id="1246e-137">設定 `EnableClientPrinting` 報表伺服器系統屬性。</span><span class="sxs-lookup"><span data-stu-id="1246e-137">Sets the `EnableClientPrinting` report server system property.</span></span> <span data-ttu-id="1246e-138">如果您啟用了用戶端列印，則擁有本機管理員權限的使用者會有選項可下載已簽署的 ActiveX 控制項以便列印 HTML 報表。</span><span class="sxs-lookup"><span data-stu-id="1246e-138">If you enable client printing, users who have local administrator permissions have the option of downloading a signed ActiveX control for printing HTML reports.</span></span> <span data-ttu-id="1246e-139">如需詳細資訊，請參閱 [啟用和停用 Reporting Services 的用戶端列印](../report-server/enable-and-disable-client-side-printing-for-reporting-services.md)。</span><span class="sxs-lookup"><span data-stu-id="1246e-139">For more information, see [Enable and Disable Client-Side Printing for Reporting Services](../report-server/enable-and-disable-client-side-printing-for-reporting-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1246e-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1246e-140">See Also</span></span>  
 <span data-ttu-id="1246e-141">[將報表伺服器屬性設定 &#40;Management Studio&#41;](set-report-server-properties-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="1246e-141">[Set Report Server Properties &#40;Management Studio&#41;](set-report-server-properties-management-studio.md) </span></span>  
 <span data-ttu-id="1246e-142">[連接到 Management Studio 中的報表伺服器](connect-to-a-report-server-in-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="1246e-142">[Connect to a Report Server in Management Studio](connect-to-a-report-server-in-management-studio.md) </span></span>  
 <span data-ttu-id="1246e-143">[啟用和停用我的報表](../report-server/enable-and-disable-my-reports.md) </span><span class="sxs-lookup"><span data-stu-id="1246e-143">[Enable and Disable My Reports](../report-server/enable-and-disable-my-reports.md) </span></span>  
 <span data-ttu-id="1246e-144">[Management Studio F1 說明中的報表伺服器](report-server-in-management-studio-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="1246e-144">[Report Server in Management Studio F1 Help](report-server-in-management-studio-f1-help.md) </span></span>  
 [<span data-ttu-id="1246e-145">保護我的報表</span><span class="sxs-lookup"><span data-stu-id="1246e-145">Secure My Reports</span></span>](../security/secure-my-reports.md)  
  
  
