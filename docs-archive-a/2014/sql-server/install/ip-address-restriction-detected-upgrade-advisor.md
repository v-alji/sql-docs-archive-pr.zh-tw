---
title: 偵測到 (Upgrade Advisor) 的 IP 位址限制 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- report servers [Reporting Services], upgrade issues
ms.assetid: 9a154455-c68f-4403-a3a7-b90f4d35eecb
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 2028e59e91d42bfdced2d18fa6ce129dfb108302
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87700630"
---
# <a name="ip-address-restriction-detected-upgrade-advisor"></a><span data-ttu-id="a5894-102">偵測到 IP 位址限制 (Upgrade Advisor)</span><span class="sxs-lookup"><span data-stu-id="a5894-102">IP address restriction detected (Upgrade Advisor)</span></span>
  <span data-ttu-id="a5894-103">Upgrade Advisor 在主控報表伺服器或報表管理員虛擬目錄的 IIS 網站上偵測到一個或多個 IP 位址限制。</span><span class="sxs-lookup"><span data-stu-id="a5894-103">Upgrade Advisor detected one or more IP address restrictions on the IIS Web site that hosts the report server or Report Manager virtual directories.</span></span> [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="a5894-104">不會提供 IP 位址限制的原生支援。</span><span class="sxs-lookup"><span data-stu-id="a5894-104">does not provide native support for IP address restrictions.</span></span>  
  
||  
|-|  
|<span data-ttu-id="a5894-105">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]自有.</span><span class="sxs-lookup"><span data-stu-id="a5894-105">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Native.</span></span>|  
  
## <a name="component"></a><span data-ttu-id="a5894-106">元件</span><span class="sxs-lookup"><span data-stu-id="a5894-106">Component</span></span>  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a><span data-ttu-id="a5894-107">描述</span><span class="sxs-lookup"><span data-stu-id="a5894-107">Description</span></span>  
 <span data-ttu-id="a5894-108">安裝程式無法針對升級報表伺服器所建立的 URL 定義 IP 位址限制。</span><span class="sxs-lookup"><span data-stu-id="a5894-108">Setup cannot define IP address restrictions on URLs created for an upgraded report server.</span></span> <span data-ttu-id="a5894-109">雖然升級可以繼續進行，但是不會針對 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] URL 定義 IP 位址限制。</span><span class="sxs-lookup"><span data-stu-id="a5894-109">Upgrade can continue, but IP address restrictions will not be defined on the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] URLs.</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="a5894-110">更正動作</span><span class="sxs-lookup"><span data-stu-id="a5894-110">Corrective Action</span></span>  
 <span data-ttu-id="a5894-111">升級之後，請使用 ISA Server、防火牆軟體或其他解決方案來允許或排除特定 IP 位址到報表伺服器的要求。</span><span class="sxs-lookup"><span data-stu-id="a5894-111">After upgrade, use ISA Server, your firewall software, or another solution to allow or exclude requests from specific IP addresses to the report server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5894-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a5894-112">See Also</span></span>  
 [<span data-ttu-id="a5894-113">&#40;Upgrade Advisor Reporting Services 升級問題&#41;</span><span class="sxs-lookup"><span data-stu-id="a5894-113">Reporting Services Upgrade Issues &#40;Upgrade Advisor&#41;</span></span>](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md)  
  
  
