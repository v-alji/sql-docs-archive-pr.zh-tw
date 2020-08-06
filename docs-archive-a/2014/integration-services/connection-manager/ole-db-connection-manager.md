---
title: OLE DB 連線管理員 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- OLE DB connection manager
- data sources [Integration Services], connections
- connection managers [Integration Services], OLE DB
- connections [Integration Services], OLE DB
ms.assetid: 91e3622e-4b1a-439a-80c7-a00b90d66979
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 5431de956a1039c2978688982792f190b0abc544
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597267"
---
# <a name="ole-db-connection-manager"></a><span data-ttu-id="9ca92-102">OLE DB 連接管理員</span><span class="sxs-lookup"><span data-stu-id="9ca92-102">OLE DB Connection Manager</span></span>
  <span data-ttu-id="9ca92-103">OLE DB 連接管理員可透過使用 OLE DB 提供者讓封裝連接到資料來源。</span><span class="sxs-lookup"><span data-stu-id="9ca92-103">An OLE DB connection manager enables a package to connect to a data source by using an OLE DB provider.</span></span> <span data-ttu-id="9ca92-104">例如，與 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 連接的 OLE DB 連線管理員可以使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] OLE DB Provider for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="9ca92-104">For example, an OLE DB connection manager that connects to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] can use the [!INCLUDE[msCoName](../../includes/msconame-md.md)] OLE DB Provider for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9ca92-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 11.0 OLEDB 提供者不支援多重子網路容錯移轉叢集的新連接字串關鍵字 (MultiSubnetFailover=True)。</span><span class="sxs-lookup"><span data-stu-id="9ca92-105">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 11.0 OLEDB provider does not support the new connection string key words (MultiSubnetFailover=True) for Multi-Subnet Failover Clustering.</span></span> <span data-ttu-id="9ca92-106">如需詳細資訊，請參閱 www.mattmasson.com 上的[SQL Server 版本](https://go.microsoft.com/fwlink/?LinkId=247824)資訊和記錄文章： [AlwaysOn 多重子網容錯移轉和 SSIS](https://www.mattmasson.com/2012/03/alwayson-multi-subnet-failover-and-ssis/)。</span><span class="sxs-lookup"><span data-stu-id="9ca92-106">For more information, see the [SQL Server Release  Notes](https://go.microsoft.com/fwlink/?LinkId=247824) and the blog post, [AlwaysOn Multi-Subnet Failover and SSIS](https://www.mattmasson.com/2012/03/alwayson-multi-subnet-failover-and-ssis/), on www.mattmasson.com.</span></span>  
  
 <span data-ttu-id="9ca92-107">有數個工作 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 和資料流程元件會使用 OLE DB 連線管理員。</span><span class="sxs-lookup"><span data-stu-id="9ca92-107">Several [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] tasks and data flow components use an OLE DB connection manager.</span></span> <span data-ttu-id="9ca92-108">例如，OLE DB 來源和 OLE DB 目的地使用此連線管理員來擷取和載入資料，Execute SQL 工作則可以使用此連線管理員來連接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫以執行查詢。</span><span class="sxs-lookup"><span data-stu-id="9ca92-108">For example, the OLE DB source and OLE DB destination use this connection manager to extract and load data, and the Execute SQL task can use this connection manager to connect to a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database to run queries.</span></span>  
  
 <span data-ttu-id="9ca92-109">OLE DB 連接管理員還可用來存取 Unmanaged 程式碼 (使用如 C++ 等語言) 撰寫之自訂工作中的 OLE DB 資料來源。</span><span class="sxs-lookup"><span data-stu-id="9ca92-109">The OLE DB connection manager is also used to access OLE DB data sources in custom tasks written in unmanaged code that uses a language such as C++.</span></span>  
  
 <span data-ttu-id="9ca92-110">當您將 OLE DB 連接管理員加入封裝時，[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 會建立在執行階段解析為 OLE DB 連接的連接管理員、設定連接管理員屬性，並將連接管理員加入封裝上的 `Connections` 集合。</span><span class="sxs-lookup"><span data-stu-id="9ca92-110">When you add an OLE DB connection manager to a package, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] creates a connection manager that will resolve to an OLE DB connection at run time, sets the connection manager properties, and adds the connection manager to the `Connections` collection on the package.</span></span>  
  
 <span data-ttu-id="9ca92-111">連接管理員的 `ConnectionManagerType` 屬性會設為 `OLEDB`。</span><span class="sxs-lookup"><span data-stu-id="9ca92-111">The `ConnectionManagerType` property of the connection manager is set to `OLEDB`.</span></span>  
  
 <span data-ttu-id="9ca92-112">您可以利用下列方式來設定 OLE DB 連接管理員：</span><span class="sxs-lookup"><span data-stu-id="9ca92-112">The OLE DB connection manager can be configured in the following ways:</span></span>  
  
-   <span data-ttu-id="9ca92-113">提供設定的特定連接字串，以符合所選取提供者的需求。</span><span class="sxs-lookup"><span data-stu-id="9ca92-113">Provide a specific connection string configured to meet the requirements of the selected provider.</span></span>  
  
-   <span data-ttu-id="9ca92-114">視提供者而定，包含要連接的資料來源名稱。</span><span class="sxs-lookup"><span data-stu-id="9ca92-114">Depending on the provider, include the name of the data source to connect to.</span></span>  
  
-   <span data-ttu-id="9ca92-115">為所選的提供者提供適當的安全性認證。</span><span class="sxs-lookup"><span data-stu-id="9ca92-115">Provide security credentials as appropriate for the selected provider.</span></span>  
  
-   <span data-ttu-id="9ca92-116">指示是否在執行階段保留從連接管理員建立的連接。</span><span class="sxs-lookup"><span data-stu-id="9ca92-116">Indicate whether the connection that is created from the connection manager is retained at run time.</span></span>  
  
## <a name="logging"></a><span data-ttu-id="9ca92-117">記錄</span><span class="sxs-lookup"><span data-stu-id="9ca92-117">Logging</span></span>  
 <span data-ttu-id="9ca92-118">您可以記錄 OLE DB 連接管理員對外部資料提供者執行的呼叫。</span><span class="sxs-lookup"><span data-stu-id="9ca92-118">You can log the calls that the OLE DB connection manager makes to external data providers.</span></span> <span data-ttu-id="9ca92-119">您可以使用這項記錄功能，疑難排解 OLE DB 連接管理員對外部資料來源執行的連接。</span><span class="sxs-lookup"><span data-stu-id="9ca92-119">You can use this logging capability to troubleshoot the connections that the OLE DB connection manager makes to external data sources.</span></span> <span data-ttu-id="9ca92-120">若要記錄 OLE DB 連接管理員對外部資料提供者執行的呼叫，請啟用封裝記錄，然後在封裝層級選取 [**診斷**] 事件。</span><span class="sxs-lookup"><span data-stu-id="9ca92-120">To log the calls that the OLE DB connection manager makes to external data providers, enable package logging and select the **Diagnostic** event at the package level.</span></span> <span data-ttu-id="9ca92-121">如需詳細資訊，請參閱 [封裝執行的疑難排解工具](../troubleshooting/troubleshooting-tools-for-package-execution.md)。</span><span class="sxs-lookup"><span data-stu-id="9ca92-121">For more information, see [Troubleshooting Tools for Package Execution](../troubleshooting/troubleshooting-tools-for-package-execution.md).</span></span>  
  
## <a name="configuration-of-the-oledb-connection-manager"></a><span data-ttu-id="9ca92-122">OLEDB 連接管理員的組態</span><span class="sxs-lookup"><span data-stu-id="9ca92-122">Configuration of the OLEDB Connection Manager</span></span>  
 <span data-ttu-id="9ca92-123">您可以透過 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師或以程式設計方式設定屬性。</span><span class="sxs-lookup"><span data-stu-id="9ca92-123">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span> <span data-ttu-id="9ca92-124">如需可在 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師中設定之屬性的詳細資訊，請參閱 [設定 OLE DB 連線管理員](../configure-ole-db-connection-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="9ca92-124">For more information about the properties that you can set in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, see [Configure OLE DB Connection Manager](../configure-ole-db-connection-manager.md).</span></span> <span data-ttu-id="9ca92-125">如需以程式設計方式設定連線管理員的相關資訊，請參閱《開發人員指南》中 **T:Microsoft.SqlServer.Dts.Runtime.ConnectionManager** 類別的文件集。</span><span class="sxs-lookup"><span data-stu-id="9ca92-125">For information about configuring a connection manager programmatically, see the documentation for **T:Microsoft.SqlServer.Dts.Runtime.ConnectionManager** class in the Developer Guide.</span></span>  
  
## <a name="related-content"></a><span data-ttu-id="9ca92-126">相關內容</span><span class="sxs-lookup"><span data-stu-id="9ca92-126">Related Content</span></span>  
  
-   <span data-ttu-id="9ca92-127">Social.technet.microsoft.com 上的 Wiki 文章： [SSIS 與 Oracle 連接器](https://go.microsoft.com/fwlink/?LinkId=220670)。</span><span class="sxs-lookup"><span data-stu-id="9ca92-127">Wiki article, [SSIS with Oracle Connectors](https://go.microsoft.com/fwlink/?LinkId=220670) on social.technet.microsoft.com.</span></span>  
  
-   <span data-ttu-id="9ca92-128">carlprothman.net 上的技術文件： [Connection Strings for OLE DB Providers](https://go.microsoft.com/fwlink/?LinkId=220744)(OLE DB 提供者的連接字串)。</span><span class="sxs-lookup"><span data-stu-id="9ca92-128">Technical article, [Connection Strings for OLE DB Providers](https://go.microsoft.com/fwlink/?LinkId=220744), on carlprothman.net.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ca92-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9ca92-129">See Also</span></span>  
 <span data-ttu-id="9ca92-130">[OLE DB 來源](../data-flow/ole-db-source.md) </span><span class="sxs-lookup"><span data-stu-id="9ca92-130">[OLE DB Source](../data-flow/ole-db-source.md) </span></span>  
 <span data-ttu-id="9ca92-131">[OLE DB 目的地](../data-flow/ole-db-destination.md) </span><span class="sxs-lookup"><span data-stu-id="9ca92-131">[OLE DB Destination](../data-flow/ole-db-destination.md) </span></span>  
 <span data-ttu-id="9ca92-132">[執行 SQL 工作](../control-flow/execute-sql-task.md) </span><span class="sxs-lookup"><span data-stu-id="9ca92-132">[Execute SQL Task](../control-flow/execute-sql-task.md) </span></span>  
 [<span data-ttu-id="9ca92-133">Integration Services &#40;SSIS&#41; 連接</span><span class="sxs-lookup"><span data-stu-id="9ca92-133">Integration Services &#40;SSIS&#41; Connections</span></span>](integration-services-ssis-connections.md)  
  
  
