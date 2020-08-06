---
title: Analysis Services 回溯相容性 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- installing Analysis Services, backward compatibility
- backward compatibility [Analysis Services]
- compatibility [Analysis Services]
- Analysis Services, backward compatibility
- upgrading Analysis Services
- SSAS, backward compatibility
- SQL Server Analysis Services, backward compatibility
ms.assetid: 618b6c3a-e20d-47a9-b2c6-6d848dfba05a
author: minewiskan
ms.author: owend
ms.openlocfilehash: 44a5296bfbd2bae746eb9936d416fd696de16cb7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593217"
---
# <a name="analysis-services-backward-compatibility"></a><span data-ttu-id="15a4b-102">Analysis Services Backward Compatibility</span><span class="sxs-lookup"><span data-stu-id="15a4b-102">Analysis Services Backward Compatibility</span></span>
  <span data-ttu-id="15a4b-103">本節中的主題描述版本之間的行為變更 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="15a4b-103">The topics in this section describe the changes in behavior between versions of  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="15a4b-104">本節內容</span><span class="sxs-lookup"><span data-stu-id="15a4b-104">In This Section</span></span>  
  
|<span data-ttu-id="15a4b-105">主題</span><span class="sxs-lookup"><span data-stu-id="15a4b-105">Topics</span></span>|<span data-ttu-id="15a4b-106">描述</span><span class="sxs-lookup"><span data-stu-id="15a4b-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="15a4b-107">SQL Server 2014 中已被取代的 Analysis Services 功能</span><span class="sxs-lookup"><span data-stu-id="15a4b-107">Deprecated Analysis Services Features in SQL Server 2014</span></span>](deprecated-analysis-services-features-in-sql-server-2014.md)|<span data-ttu-id="15a4b-108">描述在目前版本中為了與舊版相容而保留，但將在 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]的未來版本中移除的功能。</span><span class="sxs-lookup"><span data-stu-id="15a4b-108">Describes features that have been retained in the current version to maintain backward compatibility,  but which will be removed in a future version of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>|  
|[<span data-ttu-id="15a4b-109">SQL Server 2014 中已停止的 Analysis Services 功能</span><span class="sxs-lookup"><span data-stu-id="15a4b-109">Discontinued Analysis Services Functionality in SQL Server 2014</span></span>](discontinued-analysis-services-functionality-in-sql-server-2014.md)|<span data-ttu-id="15a4b-110">描述存在於舊版  [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 中，但在新版中已移除的功能。</span><span class="sxs-lookup"><span data-stu-id="15a4b-110">Describes features that existed in earlier versions of  [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] but that have since been removed in later versions.</span></span>|  
|[<span data-ttu-id="15a4b-111">SQL Server 2014 中 Analysis Services 功能的重大變更</span><span class="sxs-lookup"><span data-stu-id="15a4b-111">Breaking Changes to Analysis Services Features in SQL Server 2014</span></span>](breaking-changes-to-analysis-services-features-in-sql-server-2014.md)|<span data-ttu-id="15a4b-112">描述此版本 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 中導入的程式碼變更，其可能中斷模型或自訂應用程式或在舊版軟體中建立的程式碼。</span><span class="sxs-lookup"><span data-stu-id="15a4b-112">Describes code changes introduced in this release of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] that could potentially break a model or custom applications or script created in previous versions of the software .</span></span>|  
|[<span data-ttu-id="15a4b-113">SQL Server 2014 中 Analysis Services 功能的行為變更</span><span class="sxs-lookup"><span data-stu-id="15a4b-113">Behavior Changes to Analysis Services Features in SQL Server 2014</span></span>](behavior-changes-to-analysis-services-features-in-sql-server-2014.md)|<span data-ttu-id="15a4b-114">描述在此版本 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]中行為不同的現有功能。</span><span class="sxs-lookup"><span data-stu-id="15a4b-114">Describes existing features that have different behaviors in this release of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="15a4b-115">常見的例子包括將預設變更為新值或不同的值，而導致先前允許的作業或設定無法使用，或者必須手動修改或取代在升級期間遺漏的設定。</span><span class="sxs-lookup"><span data-stu-id="15a4b-115">Common examples include changing a default to a new or different value, disallowing a previously allowable operation or configuration, or a introducing a requirement to manually revise or replace a setting or configuration that is lost during upgrade.</span></span><br /> <span data-ttu-id="15a4b-116">.</span><span class="sxs-lookup"><span data-stu-id="15a4b-116">.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="15a4b-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="15a4b-117">See Also</span></span>  
 <span data-ttu-id="15a4b-118">[Analysis Services 和商業智慧的新功能](what-s-new-in-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="15a4b-118">[What's New in Analysis Services and Business Intelligence](what-s-new-in-analysis-services.md) </span></span>  
 [<span data-ttu-id="15a4b-119">升級 Analysis Services</span><span class="sxs-lookup"><span data-stu-id="15a4b-119">Upgrade Analysis Services</span></span>](../database-engine/install-windows/upgrade-analysis-services.md)  
  
  
