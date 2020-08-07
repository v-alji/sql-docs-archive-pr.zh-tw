---
title: Reporting Services 回溯相容性 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- Reporting Services, backward compatibility
- SSRS, backward compatibility
- SQL Server Reporting Services, backward compatibility
- backward compatibility [Reporting Services]
ms.assetid: 675b0e0e-cfee-4790-9675-80fc3ea6d30f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 7203740ba7f52dfc2cd3793a20fed9fecf5f9468
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703813"
---
# <a name="reporting-services-backward-compatibility"></a><span data-ttu-id="85e92-102">Reporting Services 回溯相容性</span><span class="sxs-lookup"><span data-stu-id="85e92-102">Reporting Services Backward Compatibility</span></span>
  <span data-ttu-id="85e92-103">本節描述版本之間的行為變更 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="85e92-103">This section describes changes in behavior between versions of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="85e92-104">它涵蓋不能再使用或已排程在未來版本中移除的功能。</span><span class="sxs-lookup"><span data-stu-id="85e92-104">It covers features that are no longer available or are scheduled to be removed in a future release.</span></span> <span data-ttu-id="85e92-105">也將描述產品的基礎性變更，已知這些變更會中斷包含 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 功能的自訂應用程式。</span><span class="sxs-lookup"><span data-stu-id="85e92-105">It also describes fundamental changes to the product that are known to break a custom application that includes [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] functionality.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="85e92-106">本節內容</span><span class="sxs-lookup"><span data-stu-id="85e92-106">In This Section</span></span>  
  
|<span data-ttu-id="85e92-107">主題</span><span class="sxs-lookup"><span data-stu-id="85e92-107">Topic</span></span>|<span data-ttu-id="85e92-108">描述</span><span class="sxs-lookup"><span data-stu-id="85e92-108">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="85e92-109">SQL Server 2014 中已中止的 SQL Server Reporting Services 功能</span><span class="sxs-lookup"><span data-stu-id="85e92-109">Discontinued Functionality to SQL Server Reporting Services in SQL Server 2014</span></span>](discontinued-functionality-to-sql-server-reporting-services-in-sql-server.md)|<span data-ttu-id="85e92-110">描述存在於舊版 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 中，但已在新版中移除的功能。</span><span class="sxs-lookup"><span data-stu-id="85e92-110">Describes features that existed in earlier versions of [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] but that have been removed in later versions.</span></span>|  
|[<span data-ttu-id="85e92-111">SQL Server 2014 中已淘汰的 SQL Server Reporting Services 功能</span><span class="sxs-lookup"><span data-stu-id="85e92-111">Deprecated Features in SQL Server Reporting Services in SQL Server 2014</span></span>](deprecated-features-in-sql-server-reporting-services-ssrs.md)|<span data-ttu-id="85e92-112">描述在這個 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 版本中為了與舊版相容而保留，但將在 SQL Server 的未來版本中移除的功能。</span><span class="sxs-lookup"><span data-stu-id="85e92-112">Describes features that exist this release of [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] for backward compatibility, but which will be removed in a future version of SQL Server.</span></span>|  
|[<span data-ttu-id="85e92-113">SQL Server 2014 中 SQL Server Reporting Services 的重大變更</span><span class="sxs-lookup"><span data-stu-id="85e92-113">Breaking Changes in SQL Server Reporting Services in SQL Server 2014</span></span>](breaking-changes-in-sql-server-reporting-services-in-sql-server-2016.md)|<span data-ttu-id="85e92-114">描述當升級 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]時可能會遇到的問題。</span><span class="sxs-lookup"><span data-stu-id="85e92-114">Describes issues that you might encounter when you upgrade [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)].</span></span>|  
|[<span data-ttu-id="85e92-115">SQL Server 2014 中 SQL Server Reporting Services 的行為變更</span><span class="sxs-lookup"><span data-stu-id="85e92-115">Behavior Changes to SQL Server Reporting Services  in SQL Server 2014</span></span>](behavior-changes-to-sql-server-reporting-services-in-sql-server-2016.md)|<span data-ttu-id="85e92-116">描述 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]中已變更的功能。</span><span class="sxs-lookup"><span data-stu-id="85e92-116">Describes features that have changed in [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)].</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="85e92-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="85e92-117">See Also</span></span>  
 <span data-ttu-id="85e92-118">[回溯相容性](../../2014/getting-started/backward-compatibility.md) </span><span class="sxs-lookup"><span data-stu-id="85e92-118">[Backward Compatibility](../../2014/getting-started/backward-compatibility.md) </span></span>  
 [<span data-ttu-id="85e92-119">Analysis Services 回溯相容性</span><span class="sxs-lookup"><span data-stu-id="85e92-119">Analysis Services Backward Compatibility</span></span>](../../2014/analysis-services/analysis-services-backward-compatibility.md)  
  
  
