---
title: SQL Server 管理物件 (SMO) 程式設計指南 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- SMO [SQL Server]
- SQL Server Management Objects
- programming [SMO]
ms.assetid: 4cde2b85-2a31-4cac-8d16-7a4196066193
author: stevestein
ms.author: sstein
ms.openlocfilehash: 863e3fc90f750f91611a6fa75655783c7802ec23
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686888"
---
# <a name="sql-server-management-objects-smo-programming-guide"></a><span data-ttu-id="5c9b7-102">SQL Server 管理物件 (SMO) 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="5c9b7-102">SQL Server Management Objects (SMO) Programming Guide</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="5c9b7-103">(SMO) 的管理物件是物件的集合，設計用來進行管理的所有層面 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="5c9b7-103">Management Objects (SMO) is a collection of objects that are designed for programming all aspects of managing [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="5c9b7-104">Replication Management Objects (RMO) 是封裝 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 複寫管理的物件集合。</span><span class="sxs-lookup"><span data-stu-id="5c9b7-104">Replication Management Objects (RMO) is a collection of objects that encapsulates [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] replication management.</span></span>  
  
|<span data-ttu-id="5c9b7-105">主題</span><span class="sxs-lookup"><span data-stu-id="5c9b7-105">Topic</span></span>|<span data-ttu-id="5c9b7-106">描述</span><span class="sxs-lookup"><span data-stu-id="5c9b7-106">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="5c9b7-107">建立 SMO 程式</span><span class="sxs-lookup"><span data-stu-id="5c9b7-107">Creating SMO Programs</span></span>](create-program/creating-smo-programs.md)<br /><br /> [<span data-ttu-id="5c9b7-108">程式設計特有的工作</span><span class="sxs-lookup"><span data-stu-id="5c9b7-108">Programming Specific Tasks</span></span>](tasks/programming-specific-tasks.md)|<span data-ttu-id="5c9b7-109">提供有關在 Microsoft.SqlServer.management、Microsoft.SqlServer.Management.NotificationServices、Microsoft.SqlServer.Management.Smo、Microsoft.SqlServer.Management.Smo.Agent、Microsoft.SqlServer.Management.Smo.Broker、Microsoft.SqlServer.Management.Smo.Mail、Microsoft.SqlServer.Management.Smo.RegisteredServers、Microsoft.SqlServer.Management.Smo.Wmi 和 Microsoft.SqlServer.Management.Trace 命名空間中，進行 SMO 物件程式開發的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="5c9b7-109">Provides information about programming the SMO objects in the Microsoft.SqlServer.management, Microsoft.SqlServer.Management.NotificationServices, Microsoft.SqlServer.Management.Smo, Microsoft.SqlServer.Management.Smo.Agent, Microsoft.SqlServer.Management.Smo.Broker, Microsoft.SqlServer.Management.Smo.Mail, Microsoft.SqlServer.Management.Smo.RegisteredServers, Microsoft.SqlServer.Management.Smo.Wmi, and Microsoft.SqlServer.Management.Trace namespaces.</span></span><br /><br /> <span data-ttu-id="5c9b7-110">這包含撰寫程式以定義資料庫和管理 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的指示。</span><span class="sxs-lookup"><span data-stu-id="5c9b7-110">This includes instructions to write programs that define databases and manage [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="5c9b7-111">您可以使用 SMO 來建立資料庫、執行備份、建立作業、設定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、指派權限以及執行許多其他的管理工作。</span><span class="sxs-lookup"><span data-stu-id="5c9b7-111">You can use SMO to create databases, perform backups, create jobs, configure [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], assign permissions, and to perform many other administrative tasks.</span></span>|  
|[<span data-ttu-id="5c9b7-112">&#40;複寫&#41;的開發人員指南</span><span class="sxs-lookup"><span data-stu-id="5c9b7-112">Developer's Guide &#40;Replication&#41;</span></span>](../replication/concepts/replication-developer-documentation.md)|<span data-ttu-id="5c9b7-113">提供有關在 Microsoft.SqlServer.Replication 命名空間中進行 RMO 物件程式開發的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="5c9b7-113">Provides information about programming the RMO objects in the Microsoft.SqlServer.Replication namespace.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5c9b7-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5c9b7-114">See Also</span></span>  
 [<span data-ttu-id="5c9b7-115">&#40;複寫&#41;的開發人員指南</span><span class="sxs-lookup"><span data-stu-id="5c9b7-115">Developer's Guide &#40;Replication&#41;</span></span>](../replication/concepts/replication-developer-documentation.md)  
  
  
