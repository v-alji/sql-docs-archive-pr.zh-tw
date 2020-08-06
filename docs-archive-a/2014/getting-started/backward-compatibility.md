---
title: 回溯相容性 | Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Surface Area Configuration Tool
- command prompt [SQL Server], discontinued parameters
- discontinued functionality [SQL Server]
- compatibility [SQL Server], discontinued features
- SAC tool
- compatibility [Analysis Services]
- compatibility [Integration Services]
- SQL Server, discontinued features
- compatibility [Replication]
- compatibility [SQL Server]
- previous versions [SQL Server], (See also backward compatibility)
- backward compatibility [SQL Server]
- compatibility [Reporting Services]
- earlier versions [SQL Server], (See also backward compatibility)
ms.assetid: 15d9117e-e2fa-4985-99ea-66a117c1e9fd
author: rothja
ms.author: jroth
ms.openlocfilehash: fd8be66efd648f5b6703a76855a549a9bd30f1e3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87607014"
---
# <a name="backward-compatibility"></a><span data-ttu-id="203cd-102">回溯相容性</span><span class="sxs-lookup"><span data-stu-id="203cd-102">Backward Compatibility</span></span>
  <span data-ttu-id="203cd-103">下列章節包含 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 元件的回溯相容性資訊。</span><span class="sxs-lookup"><span data-stu-id="203cd-103">The following sections contain backward compatibility information for [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] components.</span></span> <span data-ttu-id="203cd-104">這個內容包含關於已被取代的功能、已停止的功能、重大變更和行為變更等資訊。</span><span class="sxs-lookup"><span data-stu-id="203cd-104">This content includes information about deprecated features, discontinued features, breaking changes, and behavior changes.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="203cd-105">本節內容</span><span class="sxs-lookup"><span data-stu-id="203cd-105">In This Section</span></span>  
  
|<span data-ttu-id="203cd-106">主題</span><span class="sxs-lookup"><span data-stu-id="203cd-106">Topic</span></span>|<span data-ttu-id="203cd-107">描述</span><span class="sxs-lookup"><span data-stu-id="203cd-107">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="203cd-108">SQL Server 回溯相容性</span><span class="sxs-lookup"><span data-stu-id="203cd-108">SQL Server Backward Compatibility</span></span>](../../2014/getting-started/sql-server-backward-compatibility.md)|<span data-ttu-id="203cd-109">包含描述 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 中之變更的主題，您可能需要對自己的應用程式做一些改變。</span><span class="sxs-lookup"><span data-stu-id="203cd-109">Contains topics that describe changes in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] that might require you to make changes to your applications.</span></span> <span data-ttu-id="203cd-110">本主題範圍所包含的功能包括資料可程式性、介面區組態工具、安裝程式、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 服務和其他大幅的功能變更。</span><span class="sxs-lookup"><span data-stu-id="203cd-110">Features that are included in this topic area include data programmability, surface area configuration tools, Setup, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] services, and other broad functionality changes.</span></span>|  
|[<span data-ttu-id="203cd-111">SQL Server Database Engine 回溯相容性</span><span class="sxs-lookup"><span data-stu-id="203cd-111">SQL Server Database Engine Backward Compatibility</span></span>](../database-engine/sql-server-database-engine-backward-compatibility.md)|<span data-ttu-id="203cd-112">包含一些主題，其中描述 [!INCLUDE[ssDE](../includes/ssde-md.md)] 中的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 變更，您可能需要對自己的應用程式做一些改變。</span><span class="sxs-lookup"><span data-stu-id="203cd-112">Contains topics that describe [!INCLUDE[ssDE](../includes/ssde-md.md)] changes in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] that might require you to make changes to your applications.</span></span>|  
|[<span data-ttu-id="203cd-113">Analysis Services 回溯相容性</span><span class="sxs-lookup"><span data-stu-id="203cd-113">Analysis Services Backward Compatibility</span></span>](../../2014/analysis-services/analysis-services-backward-compatibility.md)|<span data-ttu-id="203cd-114">包含一些主題，其中描述 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 中的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 變更，您可能需要對自己的應用程式做一些改變。</span><span class="sxs-lookup"><span data-stu-id="203cd-114">Contains topics that describe [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] changes in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] that might require you to make changes to your applications.</span></span>|  
|[<span data-ttu-id="203cd-115">Integration Services 回溯相容性</span><span class="sxs-lookup"><span data-stu-id="203cd-115">Integration Services Backward Compatibility</span></span>](../integration-services/integration-services-backward-compatibility.md)|<span data-ttu-id="203cd-116">描述 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 中的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 變更，您可能需要對現有的 Data Transformation Services 應用程式做一些改變。</span><span class="sxs-lookup"><span data-stu-id="203cd-116">Describes [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] changes in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] that might require you to make changes to your existing Data Transformation Services applications.</span></span>|  
|[<span data-ttu-id="203cd-117">Reporting Services 回溯相容性</span><span class="sxs-lookup"><span data-stu-id="203cd-117">Reporting Services Backward Compatibility</span></span>](../reporting-services/reporting-services-backward-compatibility.md)|<span data-ttu-id="203cd-118">包含一些主題，其中描述 [!INCLUDE[ssRS](../includes/ssrs.md)] 中的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 變更，您可能需要對現有的 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 方案做一些改變。</span><span class="sxs-lookup"><span data-stu-id="203cd-118">Contains topics that describe [!INCLUDE[ssRS](../includes/ssrs.md)] changes in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] that might require you to make changes to your existing [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] solutions.</span></span>|  
|[<span data-ttu-id="203cd-119">回溯相容性 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="203cd-119">Backward Compatibility &#40;Master Data Services&#41;</span></span>](../master-data-services/backward-compatibility-master-data-services.md)|<span data-ttu-id="203cd-120">包含一些主題，其中描述 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 中的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 變更，您可能需要對現有的 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 方案做一些改變。</span><span class="sxs-lookup"><span data-stu-id="203cd-120">Contains topics that describe [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] changes in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] that might require you to make changes to your existing [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] solutions.</span></span>|  
|[<span data-ttu-id="203cd-121">複寫回溯相容性</span><span class="sxs-lookup"><span data-stu-id="203cd-121">Replication Backward Compatibility</span></span>](../../2014/relational-databases/replication/replication-backward-compatibility.md)|<span data-ttu-id="203cd-122">包含一些主題，其中描述 [!INCLUDE[ssDE](../includes/ssde-md.md)] 中的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 變更，您可能需要對現有的複寫方案做一些改變。</span><span class="sxs-lookup"><span data-stu-id="203cd-122">Contains topics that describe [!INCLUDE[ssDE](../includes/ssde-md.md)] changes in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] that might require you to make changes to existing Replication solutions.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="203cd-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="203cd-123">See Also</span></span>  
 <span data-ttu-id="203cd-124">[安裝 SQL Server 2014](../database-engine/install-windows/install-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="203cd-124">[Install SQL Server 2014](../database-engine/install-windows/install-sql-server.md) </span></span>  
 [<span data-ttu-id="203cd-125">升級為 SQL Server 2014</span><span class="sxs-lookup"><span data-stu-id="203cd-125">Upgrade to SQL Server 2014</span></span>](../database-engine/install-windows/upgrade-sql-server.md)  
  
  
