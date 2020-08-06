---
title: Integration Services 服務 (SSIS 服務) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Integration Services service, about Integration Services service
- SQL Server Integration Services service
- service [Integration Services],about Integration Services service
- service [Integration Services]
- SQL Server Integration Services, service
ms.assetid: 2c785b3b-4a0c-4df7-b5cd-23756dc87842
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 04b24f0f0d54009c50654904d606a208504f229c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709750"
---
# <a name="integration-services-service-ssis-service"></a><span data-ttu-id="b4242-102">Integration Services 服務 (SSIS 服務)</span><span class="sxs-lookup"><span data-stu-id="b4242-102">Integration Services Service (SSIS Service)</span></span>
  <span data-ttu-id="b4242-103">本節中的主題討論 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 服務 (用於管理 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 封裝的 Windows 服務)。</span><span class="sxs-lookup"><span data-stu-id="b4242-103">The topics in this section discuss the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] service, a Windows service for managing [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages.</span></span> <span data-ttu-id="b4242-104">若要建立、儲存及執行 Integration Services 封裝，則不需要這項服務。</span><span class="sxs-lookup"><span data-stu-id="b4242-104">This service is not required to create, save, and run Integration Services packages.</span></span> [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] <span data-ttu-id="b4242-105">支援 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 服務能與舊版 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]回溯相容。</span><span class="sxs-lookup"><span data-stu-id="b4242-105">supports the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] service for backward compatibility with earlier releases of [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="b4242-106">從開始 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] ， [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] `SSISDB` 會針對 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 使用專案部署模型部署至伺服器的專案，將物件、設定和運算元據儲存在資料庫中。</span><span class="sxs-lookup"><span data-stu-id="b4242-106">Starting in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] stores objects, settings, and operational data in the `SSISDB` database for projects that you've deployed to the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server using the project deployment model.</span></span> <span data-ttu-id="b4242-107">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 伺服器是主控資料庫之 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Database Engine 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="b4242-107">The [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server, which is an instance of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Database Engine, hosts the database.</span></span> <span data-ttu-id="b4242-108">如需資料庫的詳細資訊，請參閱 [SSIS 目錄](../catalog/ssis-catalog.md)。</span><span class="sxs-lookup"><span data-stu-id="b4242-108">For more information about the database, see [SSIS Catalog](../catalog/ssis-catalog.md).</span></span> <span data-ttu-id="b4242-109">如需將專案部署至 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 伺服器的詳細資訊，請參閱 [將專案部署至 Integration Services 伺服器](../deploy-projects-to-integration-services-server.md)。</span><span class="sxs-lookup"><span data-stu-id="b4242-109">For more information about deploying projects to the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server, see [Deploy Projects to Integration Services Server](../deploy-projects-to-integration-services-server.md).</span></span>  
  
## <a name="management-capabilities"></a><span data-ttu-id="b4242-110">管理功能</span><span class="sxs-lookup"><span data-stu-id="b4242-110">Management Capabilities</span></span>  
 <span data-ttu-id="b4242-111">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 服務是可用於管理 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 封裝的 Windows 服務。</span><span class="sxs-lookup"><span data-stu-id="b4242-111">The [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] service is a Windows service for managing [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages.</span></span> <span data-ttu-id="b4242-112">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 服務只可以在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中使用。</span><span class="sxs-lookup"><span data-stu-id="b4242-112">The [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] service is available only in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="b4242-113">執行 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 服務會提供下列管理功能：</span><span class="sxs-lookup"><span data-stu-id="b4242-113">Running the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] service provides the following management capabilities:</span></span>  
  
-   <span data-ttu-id="b4242-114">啟動遠端和本機儲存的封裝</span><span class="sxs-lookup"><span data-stu-id="b4242-114">Starting remote and locally stored packages</span></span>  
  
-   <span data-ttu-id="b4242-115">停止遠端和本機正在執行的封裝</span><span class="sxs-lookup"><span data-stu-id="b4242-115">Stopping remote and locally running packages</span></span>  
  
-   <span data-ttu-id="b4242-116">監視遠端和本機正在執行的封裝</span><span class="sxs-lookup"><span data-stu-id="b4242-116">Monitoring remote and locally running packages</span></span>  
  
-   <span data-ttu-id="b4242-117">匯入和匯出封裝</span><span class="sxs-lookup"><span data-stu-id="b4242-117">Importing and exporting packages</span></span>  
  
-   <span data-ttu-id="b4242-118">管理封裝儲存體</span><span class="sxs-lookup"><span data-stu-id="b4242-118">Managing package storage</span></span>  
  
-   <span data-ttu-id="b4242-119">自訂儲存資料夾</span><span class="sxs-lookup"><span data-stu-id="b4242-119">Customizing storage folders</span></span>  
  
-   <span data-ttu-id="b4242-120">服務停止時停止正在執行的封裝</span><span class="sxs-lookup"><span data-stu-id="b4242-120">Stopping running packages when the service is stopped</span></span>  
  
-   <span data-ttu-id="b4242-121">檢視 Windows 事件記錄檔</span><span class="sxs-lookup"><span data-stu-id="b4242-121">Viewing the Windows Event log</span></span>  
  
-   <span data-ttu-id="b4242-122">連接多個 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 伺服器</span><span class="sxs-lookup"><span data-stu-id="b4242-122">Connecting to multiple [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] servers</span></span>  
  
## <a name="startup-type-for-integration-services-service"></a><span data-ttu-id="b4242-123">Integration Services 服務的啟動類型</span><span class="sxs-lookup"><span data-stu-id="b4242-123">Startup Type for Integration Services Service</span></span>  
 <span data-ttu-id="b4242-124">當安裝 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 元件時，會安裝 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]服務。</span><span class="sxs-lookup"><span data-stu-id="b4242-124">The [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] service is installed when you install the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] component of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="b4242-125">根據預設， [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 服務會啟動，而且服務的啟動類型會設為自動。</span><span class="sxs-lookup"><span data-stu-id="b4242-125">By default, the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] service is started and the startup type of the service is set to automatic.</span></span> <span data-ttu-id="b4242-126">該服務必須執行，才能監視儲存在「 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 封裝存放區」中的封裝。</span><span class="sxs-lookup"><span data-stu-id="b4242-126">The service must be running to monitor the packages that are stored in the [!INCLUDE[ssIS](../../includes/ssis-md.md)] Package Store.</span></span> <span data-ttu-id="b4242-127">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 封裝存放區可以是 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體中的 msdb 資料庫，也可以是檔案系統中的指定資料夾。</span><span class="sxs-lookup"><span data-stu-id="b4242-127">The [!INCLUDE[ssIS](../../includes/ssis-md.md)] Package Store can be either the msdb database in an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] or the designated folders in the file system.</span></span>  
  
 <span data-ttu-id="b4242-128">如果只想設計和執行 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 封裝，則無需執行 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 服務。</span><span class="sxs-lookup"><span data-stu-id="b4242-128">The [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] service is not required if you only want to design and execute [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages.</span></span> <span data-ttu-id="b4242-129">不過，若要使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]列出和監視封裝，則需要該服務。</span><span class="sxs-lookup"><span data-stu-id="b4242-129">However, the service is required to list and monitor packages using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="b4242-130">相關工作</span><span class="sxs-lookup"><span data-stu-id="b4242-130">Related Tasks</span></span>  
  
-   [<span data-ttu-id="b4242-131">設定 Integration Services 服務的屬性</span><span class="sxs-lookup"><span data-stu-id="b4242-131">Set the Properties of the Integration Services Service</span></span>](../set-the-properties-of-the-integration-services-service.md)  
  
-   [<span data-ttu-id="b4242-132">檢視 Integration Services 服務的事件</span><span class="sxs-lookup"><span data-stu-id="b4242-132">View Events for the Integration Services Service</span></span>](../view-events-for-the-integration-services-service.md)  
  
  
