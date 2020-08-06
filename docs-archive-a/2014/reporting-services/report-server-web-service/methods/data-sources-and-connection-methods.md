---
title: 資料來源和連線方法 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- connections [Reporting Services], data sources
- reports [Reporting Services], data
- data sources [Reporting Services], methods
ms.assetid: 50999b52-fc7c-4333-9fb0-d04c37a4c90f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 29dd8dd1c002ab3b7d4594a4e25ec44bdb2cc8ad
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704873"
---
# <a name="data-sources-and-connection-methods"></a><span data-ttu-id="0e6b1-102">資料來源和連接方法</span><span class="sxs-lookup"><span data-stu-id="0e6b1-102">Data Sources and Connection Methods</span></span>
  <span data-ttu-id="0e6b1-103">您可以使用這些方法來設定和管理資料來源連接與認證。</span><span class="sxs-lookup"><span data-stu-id="0e6b1-103">You can use these methods to set and manage data source connections and credentials.</span></span>  
  
|<span data-ttu-id="0e6b1-104">方法</span><span class="sxs-lookup"><span data-stu-id="0e6b1-104">Method</span></span>|<span data-ttu-id="0e6b1-105">動作</span><span class="sxs-lookup"><span data-stu-id="0e6b1-105">Action</span></span>|  
|------------|------------|  
|<xref:ReportService2010.ReportingService2010.CreateDataSource%2A>|<span data-ttu-id="0e6b1-106">在報表伺服器資料庫或 SharePoint 文件庫中建立新的資料來源。</span><span class="sxs-lookup"><span data-stu-id="0e6b1-106">Creates a new data source in the report server database or SharePoint library.</span></span>|  
|<xref:ReportService2010.ReportingService2010.DisableDataSource%2A>|<span data-ttu-id="0e6b1-107">停用已啟用的資料來源。</span><span class="sxs-lookup"><span data-stu-id="0e6b1-107">Disables a data source that is enabled.</span></span>|  
|<xref:ReportService2010.ReportingService2010.EnableDataSource%2A>|<span data-ttu-id="0e6b1-108">啟用已停用的資料來源。</span><span class="sxs-lookup"><span data-stu-id="0e6b1-108">Enables a data source that is disabled.</span></span>|  
|<xref:ReportService2010.ReportingService2010.GetDataSourceContents%2A>|<span data-ttu-id="0e6b1-109">傳回資料來源的內容。</span><span class="sxs-lookup"><span data-stu-id="0e6b1-109">Returns the contents of a data source.</span></span>|  
|<xref:ReportService2010.ReportingService2010.GetItemDataSourcePrompts%2A>|<span data-ttu-id="0e6b1-110">取得指定之項目的資料來源提示。</span><span class="sxs-lookup"><span data-stu-id="0e6b1-110">Gets the data source prompts for a specified item.</span></span>|  
|<xref:ReportService2010.ReportingService2010.GetItemDataSources%2A>|<span data-ttu-id="0e6b1-111">傳回目錄中項目的資料來源。</span><span class="sxs-lookup"><span data-stu-id="0e6b1-111">Returns the data sources for an item in the catalog.</span></span>|  
|<xref:ReportService2010.ReportingService2010.ListDependentItems%2A>|<span data-ttu-id="0e6b1-112">傳回參考指定之目錄項目的目錄項目清單。</span><span class="sxs-lookup"><span data-stu-id="0e6b1-112">Returns a list of catalog items that reference a specified catalog item.</span></span>|  
|<xref:ReportService2010.ReportingService2010.ListSubscriptionsUsingDataSource%2A>|<span data-ttu-id="0e6b1-113">傳回與給定資料來源關聯的訂閱清單。</span><span class="sxs-lookup"><span data-stu-id="0e6b1-113">Returns a list of subscriptions that are associated with a given data source.</span></span>|  
|<xref:ReportService2010.ReportingService2010.SetDataSourceContents%2A>|<span data-ttu-id="0e6b1-114">設定與資料來源關聯的連接屬性。</span><span class="sxs-lookup"><span data-stu-id="0e6b1-114">Sets the connection properties that are associated with a data source.</span></span>|  
|<xref:ReportService2010.ReportingService2010.SetItemDataSources%2A>|<span data-ttu-id="0e6b1-115">設定報表伺服器資料庫或 SharePoint 文件庫中項目的資料來源。</span><span class="sxs-lookup"><span data-stu-id="0e6b1-115">Sets the data sources for an item in a report server database or SharePoint library.</span></span>|  
|<xref:ReportService2010.ReportingService2010.TestConnectForDataSourceDefinition%2A>|<span data-ttu-id="0e6b1-116">測試資料來源的連接。</span><span class="sxs-lookup"><span data-stu-id="0e6b1-116">Tests the connection for a data source.</span></span> <span data-ttu-id="0e6b1-117">這個方法支援資料來源的直接測試。</span><span class="sxs-lookup"><span data-stu-id="0e6b1-117">This method supports the direct testing of the data source.</span></span>|  
|<xref:ReportService2010.ReportingService2010.TestConnectForItemDataSource%2A>|<span data-ttu-id="0e6b1-118">測試資料來源的連接。</span><span class="sxs-lookup"><span data-stu-id="0e6b1-118">Tests the connection for a data source.</span></span> <span data-ttu-id="0e6b1-119">這個方法支援報表或模型及共用資料來源所使用已發行資料來源的測試。</span><span class="sxs-lookup"><span data-stu-id="0e6b1-119">This method supports the testing of published data sources that are used by reports or models and shared data sources.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0e6b1-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0e6b1-120">See Also</span></span>  
 <span data-ttu-id="0e6b1-121">[使用 Web 服務和 .NET Framework 建置應用程式](../net-framework/building-applications-using-the-web-service-and-the-net-framework.md) </span><span class="sxs-lookup"><span data-stu-id="0e6b1-121">[Building Applications Using the Web Service and the .NET Framework](../net-framework/building-applications-using-the-web-service-and-the-net-framework.md) </span></span>  
 <span data-ttu-id="0e6b1-122">[報表伺服器 Web 服務](../report-server-web-service.md) </span><span class="sxs-lookup"><span data-stu-id="0e6b1-122">[Report Server Web Service](../report-server-web-service.md) </span></span>  
 <span data-ttu-id="0e6b1-123">[報表伺服器 Web 服務方法](report-server-web-service-methods.md) </span><span class="sxs-lookup"><span data-stu-id="0e6b1-123">[Report Server Web Service Methods](report-server-web-service-methods.md) </span></span>  
 [<span data-ttu-id="0e6b1-124">技術參考 &#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="0e6b1-124">Technical Reference &#40;SSRS&#41;</span></span>](../../technical-reference-ssrs.md)  
  
  
