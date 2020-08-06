---
title: SMO 物件模型 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- object models [SMO]
- SMO [SQL Server], object model
- SQL Server Management Objects, object model
ms.assetid: bd6e59b6-ca46-42c0-adb2-c9d64cf6e00b
author: stevestein
ms.author: sstein
ms.openlocfilehash: c973e381a6cc7de44a0072d012147271eaa609ca
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686896"
---
# <a name="smo-object-model"></a><span data-ttu-id="43b08-102">SMO 物件模型</span><span class="sxs-lookup"><span data-stu-id="43b08-102">SMO Object Model</span></span>
  <span data-ttu-id="43b08-103">SMO 物件模型是由物件階層所組成。</span><span class="sxs-lookup"><span data-stu-id="43b08-103">The SMO object model is made up of a hierarchy of objects.</span></span> <span data-ttu-id="43b08-104"><xref:Microsoft.SqlServer.Management.Smo.Server> 物件是最上層的物件，而所有執行個體類別物件則位於 <xref:Microsoft.SqlServer.Management.Smo.Server> 物件之下。</span><span class="sxs-lookup"><span data-stu-id="43b08-104">The <xref:Microsoft.SqlServer.Management.Smo.Server> object is the top level object and all instance class objects reside under the <xref:Microsoft.SqlServer.Management.Smo.Server> object.</span></span>  
  
 <span data-ttu-id="43b08-105"><xref:Microsoft.SqlServer.Management.Smo.Wmi.ManagedComputer> 類別是包含個別物件階層的最上層類別。</span><span class="sxs-lookup"><span data-stu-id="43b08-105">The <xref:Microsoft.SqlServer.Management.Smo.Wmi.ManagedComputer> class is a top level class with a separate object hierarchy.</span></span> <span data-ttu-id="43b08-106"><xref:Microsoft.SqlServer.Management.Smo.Wmi.ManagedComputer>物件代表 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 可透過 WMI 提供者取得的服務和網路設定。</span><span class="sxs-lookup"><span data-stu-id="43b08-106">The <xref:Microsoft.SqlServer.Management.Smo.Wmi.ManagedComputer> object represents [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] services and network settings available through the WMI Provider.</span></span>  
  
 <span data-ttu-id="43b08-107">除了 <xref:Microsoft.SqlServer.Management.Smo.Server> 和 <xref:Microsoft.SqlServer.Management.Smo.Wmi.ManagedComputer> 物件之外，還有數個代表工作或或運算的數個公用程式類別，例如 <xref:Microsoft.SqlServer.Management.Smo.Transfer>、<xref:Microsoft.SqlServer.Management.Smo.Backup> 或 <xref:Microsoft.SqlServer.Management.Smo.Restore></span><span class="sxs-lookup"><span data-stu-id="43b08-107">Besides the <xref:Microsoft.SqlServer.Management.Smo.Server> and <xref:Microsoft.SqlServer.Management.Smo.Wmi.ManagedComputer> objects, there are several utility classes that represent tasks or operations, such as <xref:Microsoft.SqlServer.Management.Smo.Transfer>, <xref:Microsoft.SqlServer.Management.Smo.Backup>, or <xref:Microsoft.SqlServer.Management.Smo.Restore></span></span>  
  
 <span data-ttu-id="43b08-108">SMO 物件模型是由數個命名空間所組成。</span><span class="sxs-lookup"><span data-stu-id="43b08-108">The SMO object model is made up of several namespaces.</span></span> <span data-ttu-id="43b08-109">如需詳細資訊，請參閱 [SMO 命名空間](smo-object-model-namespaces.md)。</span><span class="sxs-lookup"><span data-stu-id="43b08-109">For more information, see [SMO Namespaces](smo-object-model-namespaces.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43b08-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="43b08-110">See Also</span></span>  
 <span data-ttu-id="43b08-111">[SMO 物件模型圖](smo-object-model-diagram.md) </span><span class="sxs-lookup"><span data-stu-id="43b08-111">[SMO Object Model Diagram](smo-object-model-diagram.md) </span></span>  
 <span data-ttu-id="43b08-112">[SMO 命名空間](smo-object-model-namespaces.md) </span><span class="sxs-lookup"><span data-stu-id="43b08-112">[SMO Namespaces](smo-object-model-namespaces.md) </span></span>  
 [<span data-ttu-id="43b08-113">組態管理的 WMI 提供者概念</span><span class="sxs-lookup"><span data-stu-id="43b08-113">WMI Provider for Configuration Management Concepts</span></span>](../wmi-provider-configuration/wmi-provider-for-configuration-management.md)  
  
  
