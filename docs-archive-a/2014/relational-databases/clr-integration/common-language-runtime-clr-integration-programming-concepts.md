---
title: Common Language Runtime (CLR) 整合程式設計概念 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- CLR [SQL Server] See common language runtime [SQL Server]
- Database Engine [SQL Server], .NET Framework
- .NET Framework [SQL Server], Database Engine programming
- common language runtime [SQL Server]
- .NET Framework [SQL Server]
ms.assetid: 951bf851-3e6e-4361-ae6a-2bcd5b837ebd
author: rothja
ms.author: jroth
ms.openlocfilehash: 38323b0145132ad60d59c001d5147a7d19942462
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594588"
---
# <a name="common-language-runtime-clr-integration-programming-concepts"></a><span data-ttu-id="2d84f-102">Common Language Runtime (CLR) 整合程式設計概念</span><span class="sxs-lookup"><span data-stu-id="2d84f-102">Common Language Runtime (CLR) Integration Programming Concepts</span></span>
  <span data-ttu-id="2d84f-103">從 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] 開始，[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 具備 .NET Framework for [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows 的 Common Language Runtime (CLR) 元件整合功能。</span><span class="sxs-lookup"><span data-stu-id="2d84f-103">Beginning with [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] features the integration of the common language runtime (CLR) component of the .NET Framework for [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows.</span></span> <span data-ttu-id="2d84f-104">這表示您現在可以使用任何 .NET Framework 語言 (包括 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic .NET 及 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual C#)，撰寫預存程序、觸發程序、使用者定義型別、使用者定義函數、使用者定義彙總及資料流資料表值函數。</span><span class="sxs-lookup"><span data-stu-id="2d84f-104">This means that you can now write stored procedures, triggers, user-defined types, user-defined functions, user-defined aggregates, and streaming table-valued functions, using any .NET Framework language, including [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic .NET and [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual C#.</span></span>  
  
 <span data-ttu-id="2d84f-105">Microsoft.SqlServer.Server 命名空間在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 中包含用於 CLR 程式設計的核心功能。</span><span class="sxs-lookup"><span data-stu-id="2d84f-105">The Microsoft.SqlServer.Server namespace includes core functionality for CLR programming in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="2d84f-106">不過，Microsoft.SqlServer.Server 命名空間會記載在 .NET Framework SDK 中。</span><span class="sxs-lookup"><span data-stu-id="2d84f-106">However, the Microsoft.SqlServer.Server namespace is documented in the .NET Framework SDK.</span></span> <span data-ttu-id="2d84f-107">此文件不包含在《[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 線上叢書》中。</span><span class="sxs-lookup"><span data-stu-id="2d84f-107">This documentation is not included in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="2d84f-108">根據預設，.NET Framework 會與 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 一起安裝，但是 .NET Framework SDK 則不會。</span><span class="sxs-lookup"><span data-stu-id="2d84f-108">By default, the .NET Framework is installed with [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], but the .NET Framework SDK is not.</span></span> <span data-ttu-id="2d84f-109">如果 SDK 未安裝在電腦上，也不包含在線上叢書集合中，本節中的 SDK 內容連結將不會有任何作用。</span><span class="sxs-lookup"><span data-stu-id="2d84f-109">Without the SDK installed on your computer and included in the Books Online collection, links to SDK content in this section do not work.</span></span> <span data-ttu-id="2d84f-110">請安裝 .NET Framework SDK。</span><span class="sxs-lookup"><span data-stu-id="2d84f-110">Install the .NET Framework SDK.</span></span> <span data-ttu-id="2d84f-111">安裝之後，請遵循[安裝 .NET FRAMEWORK sdk](https://technet.microsoft.com/library/bb686823\(v=SQL.105\).aspx)中的指示，將 SDK 新增至線上叢書集合和目錄。</span><span class="sxs-lookup"><span data-stu-id="2d84f-111">Once installed, add the SDK to the Books Online collection and table of contents by following the instructions in [Installing the .NET Framework SDK](https://technet.microsoft.com/library/bb686823\(v=SQL.105\).aspx).</span></span>  
  
 <span data-ttu-id="2d84f-112">下表列出本節的主題。</span><span class="sxs-lookup"><span data-stu-id="2d84f-112">The following table lists the topics in this section.</span></span>  
  
 [<span data-ttu-id="2d84f-113">Common Language Runtime &#40;CLR&#41; 整合總覽</span><span class="sxs-lookup"><span data-stu-id="2d84f-113">Common Language Runtime &#40;CLR&#41; Integration Overview</span></span>](common-language-runtime-integration-overview.md)  
 <span data-ttu-id="2d84f-114">提供 CLR 的簡短概觀，並描述在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 中使用此技術的方法和原因。</span><span class="sxs-lookup"><span data-stu-id="2d84f-114">Provides a brief overview of the CLR, and describes how and why this technology has been used in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="2d84f-115">描述使用 CLR 建立資料庫物件的優點。</span><span class="sxs-lookup"><span data-stu-id="2d84f-115">Describes the benefits of using the CLR to create database objects.</span></span>  
  
 [<span data-ttu-id="2d84f-116">組件 &#40;Database Engine&#41</span><span class="sxs-lookup"><span data-stu-id="2d84f-116">Assemblies &#40;Database Engine&#41;</span></span>](assemblies-database-engine.md)  
 <span data-ttu-id="2d84f-117">描述如何使用組件在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 中部署以 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework Common Language Runtime (CLR) 主控的其中一種 Managed 程式碼語言 (非 [!INCLUDE[tsql](../../../includes/tsql-md.md)]) 所編寫的函數、預存程序、觸發程序、使用者定義彙總，以及使用者定義型別。</span><span class="sxs-lookup"><span data-stu-id="2d84f-117">Describes how assemblies are used in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] to deploy functions, stored procedures, triggers, user-defined aggregates, and user-defined types that are written in one of the managed code languages hosted by the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework common language runtime (CLR), and not written in [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span>  
  
 [<span data-ttu-id="2d84f-118">使用 Common Language Runtime 建立資料庫物件 &#40;CLR&#41; 整合</span><span class="sxs-lookup"><span data-stu-id="2d84f-118">Building Database Objects with Common Language Runtime &#40;CLR&#41; Integration</span></span>](database-objects/building-database-objects-with-common-language-runtime-clr-integration.md)  
 <span data-ttu-id="2d84f-119">描述可以使用 CLR 建立的物件種類，並檢閱建立 CLR 資料庫物件的需求。</span><span class="sxs-lookup"><span data-stu-id="2d84f-119">Describes the kinds of objects that can be built using the CLR, and reviews the requirements for building CLR database objects.</span></span>  
  
 [<span data-ttu-id="2d84f-120">從 CLR 資料庫物件進行資料存取</span><span class="sxs-lookup"><span data-stu-id="2d84f-120">Data Access from CLR Database Objects</span></span>](data-access/data-access-from-clr-database-objects.md)  
 <span data-ttu-id="2d84f-121">描述 CLR 常式如何存取儲存在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體中的資料。</span><span class="sxs-lookup"><span data-stu-id="2d84f-121">Describes how a CLR routine can access data stored in an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
 [<span data-ttu-id="2d84f-122">CLR 整合安全性</span><span class="sxs-lookup"><span data-stu-id="2d84f-122">CLR Integration Security</span></span>](security/clr-integration-security.md)  
 <span data-ttu-id="2d84f-123">描述 CLR 整合的安全性模型。</span><span class="sxs-lookup"><span data-stu-id="2d84f-123">Describes the CLR integration security model.</span></span>  
  
 [<span data-ttu-id="2d84f-124">偵錯 CLR 資料庫物件</span><span class="sxs-lookup"><span data-stu-id="2d84f-124">Debugging CLR Database Objects</span></span>](debugging-clr-database-objects.md)  
 <span data-ttu-id="2d84f-125">描述為 CLR 資料庫物件偵錯的限制和需求。</span><span class="sxs-lookup"><span data-stu-id="2d84f-125">Describes limitations of and requirements for debugging CLR database objects.</span></span>  
  
 [<span data-ttu-id="2d84f-126">部署 CLR 資料庫物件</span><span class="sxs-lookup"><span data-stu-id="2d84f-126">Deploying CLR Database Objects</span></span>](deploying-clr-database-objects.md)  
 <span data-ttu-id="2d84f-127">描述如何將組件部署至實際伺服器。</span><span class="sxs-lookup"><span data-stu-id="2d84f-127">Describes deploying assemblies to production servers.</span></span>  
  
 [<span data-ttu-id="2d84f-128">管理 CLR 整合組件</span><span class="sxs-lookup"><span data-stu-id="2d84f-128">Managing CLR Integration Assemblies</span></span>](assemblies/managing-clr-integration-assemblies.md)  
 <span data-ttu-id="2d84f-129">描述如何建立和卸除 CLR 整合組件。</span><span class="sxs-lookup"><span data-stu-id="2d84f-129">Describes how to create and drop CLR integration assemblies.</span></span>  
  
 [<span data-ttu-id="2d84f-130">監視與疑難排解 Managed 資料庫物件</span><span class="sxs-lookup"><span data-stu-id="2d84f-130">Monitoring and Troubleshooting Managed Database Objects</span></span>](monitoring-and-troubleshooting-managed-database-objects.md)  
 <span data-ttu-id="2d84f-131">提供可用於監視和疑難排解 Managed 資料庫物件以及在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 中執行之組件的工具相關資訊。</span><span class="sxs-lookup"><span data-stu-id="2d84f-131">Provides information about the tools that can be used to monitor and troubleshoot managed database objects and assemblies running in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
 [<span data-ttu-id="2d84f-132">通用語言執行平台 &#40;CLR&#41; 整合的使用案例和範例</span><span class="sxs-lookup"><span data-stu-id="2d84f-132">Usage Scenarios and Examples for Common Language Runtime &#40;CLR&#41; Integration</span></span>](../../database-engine/dev-guide/usage-scenarios-and-examples-for-common-language-runtime-clr-integration.md)  
 <span data-ttu-id="2d84f-133">描述使用 CLR 物件的使用狀況和程式碼範例。</span><span class="sxs-lookup"><span data-stu-id="2d84f-133">Describes usage scenarios and code samples using CLR objects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d84f-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2d84f-134">See Also</span></span>  
 <span data-ttu-id="2d84f-135">[元件 &#40;資料庫引擎&#41;](assemblies-database-engine.md) </span><span class="sxs-lookup"><span data-stu-id="2d84f-135">[Assemblies &#40;Database Engine&#41;](assemblies-database-engine.md) </span></span>  
 <span data-ttu-id="2d84f-136">[安裝 .NET Framework SDK](https://technet.microsoft.com/library/bb686823\(v=SQL.105\).aspx)</span><span class="sxs-lookup"><span data-stu-id="2d84f-136">[Installing the .NET Framework SDK](https://technet.microsoft.com/library/bb686823\(v=SQL.105\).aspx)</span></span>  
  
  
