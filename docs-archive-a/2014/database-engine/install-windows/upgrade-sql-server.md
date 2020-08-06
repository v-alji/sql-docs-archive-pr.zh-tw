---
title: 升級至 SQL Server 2014 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
helpviewer_keywords:
- upgrading SQL Server
ms.assetid: 5064e35b-b70d-4a0b-a9e9-fff04162f9d2
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 857bbd6d7269b7675653b11a9d7c0acd07927f62
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87698518"
---
# <a name="upgrade-to-sql-server-2014"></a><span data-ttu-id="40890-102">升級為 SQL Server 2014</span><span class="sxs-lookup"><span data-stu-id="40890-102">Upgrade to SQL Server 2014</span></span>
  <span data-ttu-id="40890-103">您可以將 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]、 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]、 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]或 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 的執行個體升級到 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="40890-103">You can upgrade instances of, [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], or [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="40890-104">執行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安裝程式以升級到 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]之前，查看《 [SQL Server 2014 升級技術指南](https://download.microsoft.com/download/7/1/5/715BDFA7-51B6-4D7B-AF17-61E78C7E538F/SQL_Server_2014_Upgrade_technical_guide.pdf) 》(PDF 下載)、檢閱本節中關於升級程序的主題，並閱讀 [SQL Server 2014 版本資訊](https://go.microsoft.com/fwlink/?LinkID=296445)。</span><span class="sxs-lookup"><span data-stu-id="40890-104">Before running [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup to upgrade to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], check out the [SQL Server 2014 Upgrade Technical Guide](https://download.microsoft.com/download/7/1/5/715BDFA7-51B6-4D7B-AF17-61E78C7E538F/SQL_Server_2014_Upgrade_technical_guide.pdf) (PDF download), review the topics about the upgrade process in this section, and read the [SQL Server 2014 Release Notes](https://go.microsoft.com/fwlink/?LinkID=296445).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="40890-105">本節內容</span><span class="sxs-lookup"><span data-stu-id="40890-105">In This Section</span></span>  
 <span data-ttu-id="40890-106">本節包含下列主題：</span><span class="sxs-lookup"><span data-stu-id="40890-106">This section contains the following topics:</span></span>  
  
-   [<span data-ttu-id="40890-107">支援的版本與版本升級</span><span class="sxs-lookup"><span data-stu-id="40890-107">Supported Version and Edition Upgrades</span></span>](supported-version-and-edition-upgrades.md)  
  
-   [<span data-ttu-id="40890-108">使用 Upgrade Advisor 來準備升級</span><span class="sxs-lookup"><span data-stu-id="40890-108">Use Upgrade Advisor to Prepare for Upgrades</span></span>](../../sql-server/install/use-upgrade-advisor-to-prepare-for-upgrades.md)  
  
-   [<span data-ttu-id="40890-109">使用 Distributed Replay Utility 來準備升級</span><span class="sxs-lookup"><span data-stu-id="40890-109">Use the Distributed Replay Utility to Prepare for Upgrades</span></span>](../../sql-server/install/use-the-distributed-replay-utility-to-prepare-for-upgrades.md)  
  
-   [<span data-ttu-id="40890-110">升級 Analysis Services</span><span class="sxs-lookup"><span data-stu-id="40890-110">Upgrade Analysis Services</span></span>](upgrade-analysis-services.md)  
  
-   [<span data-ttu-id="40890-111">升級 Database Engine</span><span class="sxs-lookup"><span data-stu-id="40890-111">Upgrade Database Engine</span></span>](upgrade-database-engine.md)  
  
-   [<span data-ttu-id="40890-112">升級 Data Quality Services</span><span class="sxs-lookup"><span data-stu-id="40890-112">Upgrade Data Quality Services</span></span>](upgrade-data-quality-services.md)  
  
-   [<span data-ttu-id="40890-113">升級 Integration Services</span><span class="sxs-lookup"><span data-stu-id="40890-113">Upgrade Integration Services</span></span>](../../integration-services/install-windows/upgrade-integration-services.md)  
  
-   [<span data-ttu-id="40890-114">升級 Master Data Services</span><span class="sxs-lookup"><span data-stu-id="40890-114">Upgrade Master Data Services</span></span>](upgrade-master-data-services.md)  
  
-   [<span data-ttu-id="40890-115">升級 PowerPivot for SharePoint</span><span class="sxs-lookup"><span data-stu-id="40890-115">Upgrade PowerPivot for SharePoint</span></span>](upgrade-power-pivot-for-sharepoint.md)  
  
-   [<span data-ttu-id="40890-116">升級複寫的資料庫</span><span class="sxs-lookup"><span data-stu-id="40890-116">Upgrade Replicated Databases</span></span>](../../database-engine/install-windows/upgrade-replicated-databases.md)  
  
-   [<span data-ttu-id="40890-117">升級和移轉 Reporting Services</span><span class="sxs-lookup"><span data-stu-id="40890-117">Upgrade and Migrate Reporting Services</span></span>](../../reporting-services/install-windows/upgrade-and-migrate-reporting-services.md)  
  
-   [<span data-ttu-id="40890-118">升級 SQL Server 管理工具</span><span class="sxs-lookup"><span data-stu-id="40890-118">Upgrade SQL Server Management Tools</span></span>](upgrade-sql-server-management-tools.md)  
  
-   [<span data-ttu-id="40890-119">升級的使用說明主題</span><span class="sxs-lookup"><span data-stu-id="40890-119">Upgrade How-to Topics</span></span>](../../../2014/sql-server/install/upgrade-how-to-topics.md)  
  
## <a name="see-also"></a><span data-ttu-id="40890-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="40890-120">See Also</span></span>  
 <span data-ttu-id="40890-121">[升級 Database Engine](upgrade-database-engine.md) </span><span class="sxs-lookup"><span data-stu-id="40890-121">[Upgrade Database Engine](upgrade-database-engine.md) </span></span>  
 <span data-ttu-id="40890-122">[升級 Analysis Services](upgrade-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="40890-122">[Upgrade Analysis Services](upgrade-analysis-services.md) </span></span>  
 <span data-ttu-id="40890-123">[升級和移轉 Reporting Services](../../reporting-services/install-windows/upgrade-and-migrate-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="40890-123">[Upgrade and Migrate Reporting Services](../../reporting-services/install-windows/upgrade-and-migrate-reporting-services.md) </span></span>  
 <span data-ttu-id="40890-124">[升級 Integration Services](../../integration-services/install-windows/upgrade-integration-services.md) </span><span class="sxs-lookup"><span data-stu-id="40890-124">[Upgrade Integration Services](../../integration-services/install-windows/upgrade-integration-services.md) </span></span>  
 <span data-ttu-id="40890-125">[升級複寫的資料庫](../../database-engine/install-windows/upgrade-replicated-databases.md) </span><span class="sxs-lookup"><span data-stu-id="40890-125">[Upgrade Replicated Databases](../../database-engine/install-windows/upgrade-replicated-databases.md) </span></span>  
 <span data-ttu-id="40890-126">[升級 Master Data Services](upgrade-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="40890-126">[Upgrade Master Data Services](upgrade-master-data-services.md) </span></span>  
 <span data-ttu-id="40890-127">[SQL Server 2012 最佳做法分析程式](https://www.microsoft.com/download/details.aspx?id=29302) </span><span class="sxs-lookup"><span data-stu-id="40890-127">[SQL Server 2012 Best Practices Analyzer](https://www.microsoft.com/download/details.aspx?id=29302) </span></span>  
 <span data-ttu-id="40890-128">[SQL Server 2008 R2 Best Practices Analyzer](https://www.microsoft.com/download/details.aspx?id=436) </span><span class="sxs-lookup"><span data-stu-id="40890-128">[SQL Server 2008 R2 Best Practices Analyzer](https://www.microsoft.com/download/details.aspx?id=436) </span></span>  
 [<span data-ttu-id="40890-129">回溯相容性</span><span class="sxs-lookup"><span data-stu-id="40890-129">Backward Compatibility</span></span>](../../../2014/getting-started/backward-compatibility.md)  
  
  
