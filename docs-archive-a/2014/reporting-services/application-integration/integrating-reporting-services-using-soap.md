---
title: 使用 SOAP 整合 Reporting Services | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- Report Server Web service, application integration
- SOAP [Reporting Services]
- SOAP [Reporting Services], about report integration
- integrating reports [Reporting Services]
- Web service [Reporting Services], application integration
ms.assetid: 6bc17af5-883c-4bfa-87d9-48cd7056d145
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 7b6fffd65b22900d7c505c4b50ec290b95fe9ab4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585155"
---
# <a name="integrating-reporting-services-using-soap"></a><span data-ttu-id="3d9ee-102">使用 SOAP 整合 Reporting Services</span><span class="sxs-lookup"><span data-stu-id="3d9ee-102">Integrating Reporting Services Using SOAP</span></span>
  <span data-ttu-id="3d9ee-103">[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SOAP API 提供數個 Web 服務端點，用於開發自訂報表方案。</span><span class="sxs-lookup"><span data-stu-id="3d9ee-103">The [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SOAP API provides several Web service endpoints for developing custom reporting solutions.</span></span> <span data-ttu-id="3d9ee-104">這些端點目前分為兩個類別：管理與執行。</span><span class="sxs-lookup"><span data-stu-id="3d9ee-104">The endpoints currently fall into two categories: management and execution.</span></span> <span data-ttu-id="3d9ee-105">管理功能是透過 <xref:ReportService2005>、<xref:ReportService2006> 和 <xref:ReportService2010> 端點公開。</span><span class="sxs-lookup"><span data-stu-id="3d9ee-105">The management functionality is exposed through the <xref:ReportService2005>, <xref:ReportService2006>, and <xref:ReportService2010> endpoints.</span></span> <span data-ttu-id="3d9ee-106"><xref:ReportService2005> 端點是用於管理以原生模式設定的報表伺服器，而 <xref:ReportService2006> 端點則是用於管理為 SharePoint 整合模式所設定的報表伺服器。</span><span class="sxs-lookup"><span data-stu-id="3d9ee-106">The <xref:ReportService2005> endpoint is used for managing a report server that is configured in native mode and the <xref:ReportService2006> endpoint is used for managing a report server that is configured for SharePoint integrated mode.</span></span> <span data-ttu-id="3d9ee-107"><xref:ReportService2010> 合併了 <xref:ReportService2005> 和 <xref:ReportService2006> 的功能，並能管理以原生模式或 SharePoint 整合模式設定的報表伺服器。</span><span class="sxs-lookup"><span data-stu-id="3d9ee-107">The <xref:ReportService2010> merges the functionalities of <xref:ReportService2005> and <xref:ReportService2006> and can manage a report server that is configured for either native or SharePoint integrated mode.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3d9ee-108"><xref:ReportService2005> 和 <xref:ReportService2006> 端點是在 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] 中被取代。</span><span class="sxs-lookup"><span data-stu-id="3d9ee-108">The <xref:ReportService2005> and <xref:ReportService2006> endpoints are deprecated in [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)].</span></span> <span data-ttu-id="3d9ee-109"><xref:ReportService2010> 端點包含這兩個端點的功能，並包含額外的管理功能。</span><span class="sxs-lookup"><span data-stu-id="3d9ee-109">The <xref:ReportService2010> endpoint includes the functionalities of both endpoints and contains additional management features.</span></span>  
  
 <span data-ttu-id="3d9ee-110">執行功能是透過 <xref:ReportExecution2005> 端點來公開，並在以原生模式或 SharePoint 整合模式設定報表伺服器時使用該功能。</span><span class="sxs-lookup"><span data-stu-id="3d9ee-110">The execution functionality is exposed through the <xref:ReportExecution2005> endpoint and it is used when the report server is configured in native or SharePoint integrated mode.</span></span> <span data-ttu-id="3d9ee-111">下列主題顯示如何使用這些端點在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows、SharePoint 與 Web 應用程式中開發報表方案。</span><span class="sxs-lookup"><span data-stu-id="3d9ee-111">The following topics show how these endpoints can be used for developing reporting solutions in [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows, SharePoint, and Web applications.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3d9ee-112">本節內容</span><span class="sxs-lookup"><span data-stu-id="3d9ee-112">In This Section</span></span>  
 [<span data-ttu-id="3d9ee-113">在 Windows 應用程式中使用 SOAP API</span><span class="sxs-lookup"><span data-stu-id="3d9ee-113">Using the SOAP API in a Windows Application</span></span>](integrating-reporting-services-using-soap-windows-application.md)  
 <span data-ttu-id="3d9ee-114">描述如何使用 SOAP API 將 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 整合到 Windows 環境中。</span><span class="sxs-lookup"><span data-stu-id="3d9ee-114">Describes how to use the SOAP API to integrate [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] into a Windows environment.</span></span>  
  
 [<span data-ttu-id="3d9ee-115">在 Web 應用程式中使用 SOAP API</span><span class="sxs-lookup"><span data-stu-id="3d9ee-115">Using the SOAP API in a Web Application</span></span>](integrating-reporting-services-using-soap-web-application.md)  
 <span data-ttu-id="3d9ee-116">描述如何使用 SOAP API 將 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 整合到 Web 環境。</span><span class="sxs-lookup"><span data-stu-id="3d9ee-116">Describes how to use the SOAP API to integrate [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] into a Web environment.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d9ee-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3d9ee-117">See Also</span></span>  
 <span data-ttu-id="3d9ee-118">[將 Reporting Services 整合至應用程式](../application-integration/integrating-reporting-services-into-applications.md) </span><span class="sxs-lookup"><span data-stu-id="3d9ee-118">[Integrating Reporting Services into Applications](../application-integration/integrating-reporting-services-into-applications.md) </span></span>  
 <span data-ttu-id="3d9ee-119">[報表伺服器 Web 服務](../report-server-web-service/report-server-web-service.md) </span><span class="sxs-lookup"><span data-stu-id="3d9ee-119">[Report Server Web Service](../report-server-web-service/report-server-web-service.md) </span></span>  
 [<span data-ttu-id="3d9ee-120">使用 Web 服務和 .NET Framework 建置應用程式</span><span class="sxs-lookup"><span data-stu-id="3d9ee-120">Building Applications Using the Web Service and the .NET Framework</span></span>](../report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)  
  
  
