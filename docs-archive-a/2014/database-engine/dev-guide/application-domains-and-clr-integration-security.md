---
title: 應用程式域和 CLR 整合安全性 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: reference
helpviewer_keywords:
- security [CLR integration]
- application domains [CLR integration]
ms.assetid: 54ee904e-e21a-4ee7-b4ad-a6f6f71bd473
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 85d6e66b1d51cc9d7c5829b8e83c510bea750e2a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593550"
---
# <a name="application-domains-and-clr-integration-security"></a><span data-ttu-id="e02f3-102">應用程式網域和 CLR 整合安全性</span><span class="sxs-lookup"><span data-stu-id="e02f3-102">Application Domains and CLR Integration Security</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="e02f3-103">會載入屬於同一應用程式網域中相同擁有者的組件。</span><span class="sxs-lookup"><span data-stu-id="e02f3-103">loads assemblies belonging to the same owner in the same application domain.</span></span> <span data-ttu-id="e02f3-104">組件可透過在同一應用程式網域中執行的一組組件，使用 .NET Framework Reflection 應用程式開發介面或其他方式在執行時互相發現對方，並能夠以晚期繫結方式呼叫彼此內部。</span><span class="sxs-lookup"><span data-stu-id="e02f3-104">By virtue of a set of assemblies running in the same application domain, assemblies are able to discover each other at execution time using the.NET Framework reflection application programming interfaces or other means, and can call into them in late-bound fashion.</span></span> <span data-ttu-id="e02f3-105">因為此類呼叫是針對屬於同一擁有者的組件而進行，所以不會檢查這些呼叫的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 權限。</span><span class="sxs-lookup"><span data-stu-id="e02f3-105">Because such calls are occurring against assemblies belonging to the same owner, there are no [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] permissions checked for these calls.</span></span> <span data-ttu-id="e02f3-106">應用程式網域中組件的位置配置設計主要是為達成延展性、安全性及隔離目的，並可能在以後的版本中變更。</span><span class="sxs-lookup"><span data-stu-id="e02f3-106">The placement scheme of assemblies in application domains is designed primarily to achieve scalability, security, and isolation goals, and can potentially change in future releases.</span></span> <span data-ttu-id="e02f3-107">因此，您不應依賴透過晚期繫結機制，在同一應用程式網域中尋找組件。</span><span class="sxs-lookup"><span data-stu-id="e02f3-107">Hence, you should not rely on finding assemblies in the same application domain through late-bound mechanisms.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e02f3-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e02f3-108">See Also</span></span>  
 [<span data-ttu-id="e02f3-109">CLR 整合安全性</span><span class="sxs-lookup"><span data-stu-id="e02f3-109">CLR Integration Security</span></span>](../../relational-databases/clr-integration/security/clr-integration-security.md)  
  
  
