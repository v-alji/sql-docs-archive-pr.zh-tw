---
title: 報表伺服器命名空間管理方法 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- reports [Reporting Services], managing
- management methods [Reporting Services]
- methods [Reporting Services], about methods
- methods [Reporting Services]
ms.assetid: 2aa43ce9-f51e-408a-8ce0-b40d3dd62561
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 1b2dc38976406aaa0fa799e7a58ee340e5449d34
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688546"
---
# <a name="report-server-namespace-management-methods"></a><span data-ttu-id="f0c3c-102">報表伺服器命名空間管理方法</span><span class="sxs-lookup"><span data-stu-id="f0c3c-102">Report Server Namespace Management Methods</span></span>
  <span data-ttu-id="f0c3c-103">報表伺服器管理 Web 服務中包含許多方法，可用來管理報表伺服器資料庫中的報表、資料夾和資源。</span><span class="sxs-lookup"><span data-stu-id="f0c3c-103">The Report Server Management Web service contains methods that you can use to manage reports, folders, and resources in the report server database.</span></span>  
  
|<span data-ttu-id="f0c3c-104">方法</span><span class="sxs-lookup"><span data-stu-id="f0c3c-104">Method</span></span>|<span data-ttu-id="f0c3c-105">動作</span><span class="sxs-lookup"><span data-stu-id="f0c3c-105">Action</span></span>|  
|------------|------------|  
|<xref:ReportService2010.ReportingService2010.CancelJob%2A>|<span data-ttu-id="f0c3c-106">取消執行作業。</span><span class="sxs-lookup"><span data-stu-id="f0c3c-106">Cancels execution of a job.</span></span>|  
|<xref:ReportService2010.ReportingService2010.CreateFolder%2A>|<span data-ttu-id="f0c3c-107">將資料夾加入至報表伺服器資料庫或 SharePoint 文件庫。</span><span class="sxs-lookup"><span data-stu-id="f0c3c-107">Adds a folder to the report server database or SharePoint library.</span></span>|  
|<xref:ReportService2010.ReportingService2010.CreateCatalogItem%2A>|<span data-ttu-id="f0c3c-108">將新項目加入至報表伺服器資料庫或 SharePoint 文件庫。</span><span class="sxs-lookup"><span data-stu-id="f0c3c-108">Adds a new item to a report server database or SharePoint library.</span></span> <span data-ttu-id="f0c3c-109">這個方法會套用至 `Report`、`Model`、`Dataset`、`Component`、`Resource` 和 `DataSource` 項目類型。</span><span class="sxs-lookup"><span data-stu-id="f0c3c-109">This method applies to the `Report`, `Model`, `Dataset`, `Component`, `Resource`, and `DataSource` item types.</span></span>|  
|<span data-ttu-id="f0c3c-110">M:ReportService2010.ReportingService2010.CreateReportEditSession(System.String,System.String,System.Byte[],ReportService2010.Warning[]@)</span><span class="sxs-lookup"><span data-stu-id="f0c3c-110">M:ReportService2010.ReportingService2010.CreateReportEditSession(System.String,System.String,System.Byte[],ReportService2010.Warning[]@)</span></span>|<span data-ttu-id="f0c3c-111">建立新的報表編輯工作階段。</span><span class="sxs-lookup"><span data-stu-id="f0c3c-111">Creates a new report edit session.</span></span>|  
|<xref:ReportService2010.ReportingService2010.DeleteItem%2A>|<span data-ttu-id="f0c3c-112">從報表伺服器資料庫或 SharePoint 文件庫移除項目。</span><span class="sxs-lookup"><span data-stu-id="f0c3c-112">Removes an item from the report server database or SharePoint library.</span></span>|  
|<xref:ReportService2010.ReportingService2010.FindItems%2A>|<span data-ttu-id="f0c3c-113">傳回報表伺服器資料庫或 SharePoint 文件庫中符合指定搜尋準則的項目。</span><span class="sxs-lookup"><span data-stu-id="f0c3c-113">Returns the items in the report server database or SharePoint library that match the specified search criteria.</span></span>|  
|<xref:ReportService2010.ReportingService2010.FireEvent%2A>|<span data-ttu-id="f0c3c-114">根據提供的參數觸發事件。</span><span class="sxs-lookup"><span data-stu-id="f0c3c-114">Triggers an event based on the supplied parameters.</span></span>|  
|<xref:ReportService2010.ReportingService2010.GetExtensionSettings%2A>|<span data-ttu-id="f0c3c-115">傳回給定延伸模組的設定清單。</span><span class="sxs-lookup"><span data-stu-id="f0c3c-115">Returns a list of settings for a given extension.</span></span>|  
|<xref:ReportService2010.ReportingService2010.GetItemType%2A>|<span data-ttu-id="f0c3c-116">如果項目存在，便擷取報表伺服器資料庫或 SharePoint 文件庫中的項目類型。</span><span class="sxs-lookup"><span data-stu-id="f0c3c-116">Retrieves the type of an item in the report server database or SharePoint library, if the item exists.</span></span>|  
|<xref:ReportService2010.ReportingService2010.GetProperties%2A>|<span data-ttu-id="f0c3c-117">傳回報表伺服器資料庫或 SharePoint 文件庫中項目上的一個或多個屬性值。</span><span class="sxs-lookup"><span data-stu-id="f0c3c-117">Returns the values of one or more properties on an item in the report server database or SharePoint library.</span></span>|  
|<xref:ReportService2010.ReportingService2010.GetItemDefinition%2A>|<span data-ttu-id="f0c3c-118">擷取項目的定義或內容。</span><span class="sxs-lookup"><span data-stu-id="f0c3c-118">Retrieves the definition or content for an item.</span></span> <span data-ttu-id="f0c3c-119">這個方法會套用至 `Report`、`Model`、`Dataset`、`Component`、`Resource` 和 `DataSource` 項目類型。</span><span class="sxs-lookup"><span data-stu-id="f0c3c-119">This method applies to the `Report`, `Model`, `Dataset`, `Component`, `Resource`, and `DataSource` item types.</span></span>|  
|<xref:ReportService2010.ReportingService2010.GetItemReferences%2A>|<span data-ttu-id="f0c3c-120">傳回與項目關聯的目錄項目參考清單。</span><span class="sxs-lookup"><span data-stu-id="f0c3c-120">Returns a list of catalog item references associated with an item.</span></span>|  
|<xref:ReportService2010.ReportingService2010.GetReportServerConfigInfo%2A>|<span data-ttu-id="f0c3c-121">傳回有關向外延展部署中，已連接之報表伺服器執行個體或所有報表伺服器執行個體的資訊。</span><span class="sxs-lookup"><span data-stu-id="f0c3c-121">Returns information on the connected report server instance or all the report server instances in a scale-out deployment.</span></span>|  
|<xref:ReportService2010.ReportingService2010.GetSystemProperties%2A>|<span data-ttu-id="f0c3c-122">傳回一個或多個系統屬性。</span><span class="sxs-lookup"><span data-stu-id="f0c3c-122">Returns one or more system properties.</span></span>|  
|<xref:ReportService2010.ReportingService2010.ListChildren%2A>|<span data-ttu-id="f0c3c-123">取得指定之資料夾的子系清單。</span><span class="sxs-lookup"><span data-stu-id="f0c3c-123">Gets a list of children of a specified folder.</span></span>|  
|<xref:ReportService2010.ReportingService2010.ListDatabaseCredentialRetrievalOptions%2A>|<span data-ttu-id="f0c3c-124">傳回支援的認證擷取選項清單。</span><span class="sxs-lookup"><span data-stu-id="f0c3c-124">Returns a list of supported credential retrieval options.</span></span>|  
|<xref:ReportService2010.ReportingService2010.ListEvents%2A>|<span data-ttu-id="f0c3c-125">當事件延伸模組出現在報表伺服器組態檔中時，傳回這些延伸模組的清單。</span><span class="sxs-lookup"><span data-stu-id="f0c3c-125">Returns a list of event extensions as they appear in the report server configuration file.</span></span>|  
|<xref:ReportService2010.ReportingService2010.ListJobs%2A>|<span data-ttu-id="f0c3c-126">傳回在報表伺服器上執行的作業清單。</span><span class="sxs-lookup"><span data-stu-id="f0c3c-126">Returns a list of jobs running on the report server.</span></span>|  
|<xref:ReportService2010.ReportingService2010.ListExtensions%2A>|<span data-ttu-id="f0c3c-127">傳回為給定延伸模組類型所設定的延伸模組清單。</span><span class="sxs-lookup"><span data-stu-id="f0c3c-127">Returns a list of extensions that are configured for a given extension type.</span></span>|  
|<xref:ReportService2010.ReportingService2010.ListExtensionTypes%2A>|<span data-ttu-id="f0c3c-128">傳回支援的延伸模組類型清單。</span><span class="sxs-lookup"><span data-stu-id="f0c3c-128">Returns a list of supported extension types.</span></span>|  
|<xref:ReportService2010.ReportingService2010.ListItemTypes%2A>|<span data-ttu-id="f0c3c-129">傳回支援的目錄項目類型清單。</span><span class="sxs-lookup"><span data-stu-id="f0c3c-129">Returns a list of supported catalog item types.</span></span>|  
|<xref:ReportService2010.ReportingService2010.ListJobActions%2A>|<span data-ttu-id="f0c3c-130">傳回支援的作業動作清單。</span><span class="sxs-lookup"><span data-stu-id="f0c3c-130">Returns a list of supported job actions.</span></span>|  
|<xref:ReportService2010.ReportingService2010.ListJobStates%2A>|<span data-ttu-id="f0c3c-131">傳回支援的作業狀態清單。</span><span class="sxs-lookup"><span data-stu-id="f0c3c-131">Returns a list of supported job states.</span></span>|  
|<xref:ReportService2010.ReportingService2010.ListJobTypes%2A>|<span data-ttu-id="f0c3c-132">傳回支援的作業類型清單。</span><span class="sxs-lookup"><span data-stu-id="f0c3c-132">Returns a list of supported job types.</span></span>|  
|<xref:ReportService2010.ReportingService2010.ListParents%2A>|<span data-ttu-id="f0c3c-133">擷取給定項目的父項目。</span><span class="sxs-lookup"><span data-stu-id="f0c3c-133">Retrieves parent items for the given item.</span></span>|  
|<xref:ReportService2010.ReportingService2010.ListSecurityScopes%2A>|<span data-ttu-id="f0c3c-134">傳回支援的安全性範圍清單。</span><span class="sxs-lookup"><span data-stu-id="f0c3c-134">Returns a list of supported security scopes.</span></span>|  
|<xref:ReportService2010.ReportingService2010.Logoff%2A>|<span data-ttu-id="f0c3c-135">將提出 Web 服務要求的目前使用者登出。</span><span class="sxs-lookup"><span data-stu-id="f0c3c-135">Logs out the current user making Web service requests.</span></span> <span data-ttu-id="f0c3c-136">這個方法只適用於原生模式。</span><span class="sxs-lookup"><span data-stu-id="f0c3c-136">This method only applies to native mode.</span></span>|  
|<xref:ReportService2010.ReportingService2010.LogonUser%2A>|<span data-ttu-id="f0c3c-137">登入使用者，並向報表伺服器 Web 服務驗證使用者的要求。</span><span class="sxs-lookup"><span data-stu-id="f0c3c-137">Logs on a user and authenticates a user request to the Report Server Web service.</span></span> <span data-ttu-id="f0c3c-138">這個方法只適用於原生模式。</span><span class="sxs-lookup"><span data-stu-id="f0c3c-138">This method only applies to native mode.</span></span>|  
|<xref:ReportService2010.ReportingService2010.SetItemReferences%2A>|<span data-ttu-id="f0c3c-139">設定與項目關聯的目錄項目。</span><span class="sxs-lookup"><span data-stu-id="f0c3c-139">Sets the catalog items associated with an item.</span></span>|  
|<xref:ReportService2010.ReportingService2010.MoveItem%2A>|<span data-ttu-id="f0c3c-140">移動及 (或) 重新命名項目。</span><span class="sxs-lookup"><span data-stu-id="f0c3c-140">Moves and/or renames an item.</span></span>|  
|<xref:ReportService2010.ReportingService2010.SetProperties%2A>|<span data-ttu-id="f0c3c-141">設定項目的一個或多個屬性。</span><span class="sxs-lookup"><span data-stu-id="f0c3c-141">Sets one or more properties of an item.</span></span>|  
|<xref:ReportService2010.ReportingService2010.SetItemDefinition%2A>|<span data-ttu-id="f0c3c-142">設定指定之項目的定義或內容。</span><span class="sxs-lookup"><span data-stu-id="f0c3c-142">Sets the definition or content for a specified item.</span></span> <span data-ttu-id="f0c3c-143">這個方法會套用至 `Report`、`Model`、`Dataset`、`Component`、`Resource` 和 `DataSource` 項目類型。</span><span class="sxs-lookup"><span data-stu-id="f0c3c-143">This method applies to the `Report`, `Model`, `Dataset`, `Component`, `Resource`, and `DataSource` item types.</span></span>|  
|<xref:ReportService2010.ReportingService2010.SetSystemProperties%2A>|<span data-ttu-id="f0c3c-144">設定報表伺服器或 SharePoint 伺服器陣列中的一個或多個系統屬性。</span><span class="sxs-lookup"><span data-stu-id="f0c3c-144">Sets one or more system properties in the report server or SharePoint farm.</span></span>|  
|<xref:ReportService2010.ReportingService2010.ValidateExtensionSettings%2A>|<span data-ttu-id="f0c3c-145">驗證 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 延伸模組設定。</span><span class="sxs-lookup"><span data-stu-id="f0c3c-145">Validates [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] extension settings.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f0c3c-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f0c3c-146">See Also</span></span>  
 <span data-ttu-id="f0c3c-147">[使用 Web 服務和 .NET Framework 建置應用程式](../net-framework/building-applications-using-the-web-service-and-the-net-framework.md) </span><span class="sxs-lookup"><span data-stu-id="f0c3c-147">[Building Applications Using the Web Service and the .NET Framework](../net-framework/building-applications-using-the-web-service-and-the-net-framework.md) </span></span>  
 <span data-ttu-id="f0c3c-148">[報表伺服器 Web 服務](../report-server-web-service.md) </span><span class="sxs-lookup"><span data-stu-id="f0c3c-148">[Report Server Web Service](../report-server-web-service.md) </span></span>  
 <span data-ttu-id="f0c3c-149">[報表伺服器 Web 服務方法](report-server-web-service-methods.md) </span><span class="sxs-lookup"><span data-stu-id="f0c3c-149">[Report Server Web Service Methods](report-server-web-service-methods.md) </span></span>  
 [<span data-ttu-id="f0c3c-150">技術參考 &#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="f0c3c-150">Technical Reference &#40;SSRS&#41;</span></span>](../../technical-reference-ssrs.md)  
  
  
