---
title: SQL Server 回溯相容性 |Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: ac47cb74-5578-417d-bcef-f970d9527705
author: rothja
ms.author: jroth
ms.openlocfilehash: a4d38041ce4daa12911dc706d382460324931c90
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87698458"
---
# <a name="sql-server-backward-compatibility"></a><span data-ttu-id="3a741-102">SQL Server 回溯相容性</span><span class="sxs-lookup"><span data-stu-id="3a741-102">SQL Server Backward Compatibility</span></span>
  <span data-ttu-id="3a741-103">「回溯相容性」一節中的主題描述 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 版本之間行為上的變更 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="3a741-103">Topics in the backward compatibility section describe changes in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] behavior between versions of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="3a741-104">本主題範圍所包含的功能包括資料可程式性、介面區組態工具、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 安裝程式、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 服務和其他大幅的功能變更。</span><span class="sxs-lookup"><span data-stu-id="3a741-104">Features included in this topic area include data programmability, surface area configuration tools, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Setup, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] services, and other broad functionality changes.</span></span>  
  
|<span data-ttu-id="3a741-105">主題</span><span class="sxs-lookup"><span data-stu-id="3a741-105">Topic</span></span>|<span data-ttu-id="3a741-106">描述</span><span class="sxs-lookup"><span data-stu-id="3a741-106">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="3a741-107">SQL Server 2014 中已被取代的 SQL Server 功能</span><span class="sxs-lookup"><span data-stu-id="3a741-107">Deprecated SQL Server Features in SQL Server 2014</span></span>](../../2014/getting-started/deprecated-sql-server-features-in-sql-server-2014.md)|<span data-ttu-id="3a741-108">這一版已被取代的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 功能。</span><span class="sxs-lookup"><span data-stu-id="3a741-108">Deprecated [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] features in this release.</span></span> <span data-ttu-id="3a741-109">本主題涵蓋 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 組態和安裝程式功能。</span><span class="sxs-lookup"><span data-stu-id="3a741-109">This topic covers [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] configuration, and Setup functionality.</span></span>|  
|[<span data-ttu-id="3a741-110">在 SQL Server 2014 中停止 SQL Server 的功能</span><span class="sxs-lookup"><span data-stu-id="3a741-110">Discontinued SQL Server Features in SQL Server 2014</span></span>](../../2014/getting-started/discontinued-sql-server-features-in-sql-server-2014.md)|<span data-ttu-id="3a741-111">這一版已停止的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 功能。</span><span class="sxs-lookup"><span data-stu-id="3a741-111">Discontinued [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] functionality in this release.</span></span> <span data-ttu-id="3a741-112">本主題涵蓋 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 組態和安裝程式功能。</span><span class="sxs-lookup"><span data-stu-id="3a741-112">This topic covers [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] configuration, and Setup functionality.</span></span>|  
|[<span data-ttu-id="3a741-113">SQL Server 2014 中 SQL Server 功能的突破性變更</span><span class="sxs-lookup"><span data-stu-id="3a741-113">Breaking Changes to SQL Server Features in SQL Server 2014</span></span>](../../2014/getting-started/breaking-changes-to-sql-server-features-in-sql-server-2014.md)|<span data-ttu-id="3a741-114">可能需要對應用程式進行改變的變更。</span><span class="sxs-lookup"><span data-stu-id="3a741-114">Changes that might require changes to applications.</span></span> <span data-ttu-id="3a741-115">本主題涵蓋 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 組態和安裝程式功能。</span><span class="sxs-lookup"><span data-stu-id="3a741-115">This topic covers [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] configuration, and Setup functionality.</span></span>|  
|[<span data-ttu-id="3a741-116">SQL Server 2014 中 SQL Server 功能的行為變更</span><span class="sxs-lookup"><span data-stu-id="3a741-116">Behavior Changes to SQL Server Features in SQL Server 2014</span></span>](../../2014/getting-started/behavior-changes-to-sql-server-features-in-sql-server-2014.md)|<span data-ttu-id="3a741-117">這一版在 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 功能上的行為變更。</span><span class="sxs-lookup"><span data-stu-id="3a741-117">Behavioral  changes to [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] features in this release.</span></span> <span data-ttu-id="3a741-118">本主題涵蓋 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 組態和安裝程式功能。</span><span class="sxs-lookup"><span data-stu-id="3a741-118">This topic covers [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] configuration, and Setup functionality.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3a741-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3a741-119">See Also</span></span>  
 [<span data-ttu-id="3a741-120">回溯相容性</span><span class="sxs-lookup"><span data-stu-id="3a741-120">Backward Compatibility</span></span>](../../2014/getting-started/backward-compatibility.md)  
  
  
