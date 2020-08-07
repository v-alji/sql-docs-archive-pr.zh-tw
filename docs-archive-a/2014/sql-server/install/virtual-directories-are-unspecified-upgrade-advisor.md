---
title: 未指定 (Upgrade Advisor) 的虛擬目錄 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- virtual directories [Reporting Services]
ms.assetid: 7d32b560-49d6-4558-b5d6-9127067f82d6
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: e20c48d0bf58d28cb2894baa26c2e11db26fab96
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595410"
---
# <a name="virtual-directories-are-unspecified-upgrade-advisor"></a><span data-ttu-id="ef31d-102">未指定虛擬目錄 (Upgrade Advisor)</span><span class="sxs-lookup"><span data-stu-id="ef31d-102">Virtual directories are unspecified (Upgrade Advisor)</span></span>
  <span data-ttu-id="ef31d-103">Upgrade Advisor 未偵測到報表伺服器 Web 服務或報表管理員的虛擬目錄設定。</span><span class="sxs-lookup"><span data-stu-id="ef31d-103">Upgrade Advisor did not detect virtual directory settings for the Report Server Web service or Report Manager.</span></span> <span data-ttu-id="ef31d-104">升級完成之後，您必須使用 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 組態管理員來設定報表伺服器的 URL 保留項目。</span><span class="sxs-lookup"><span data-stu-id="ef31d-104">After upgrade completes, you must configure URL reservations for the report server by using the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager.</span></span>  
  
||  
|-|  
|<span data-ttu-id="ef31d-105">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]原生模式。</span><span class="sxs-lookup"><span data-stu-id="ef31d-105">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Native mode.</span></span>|  
  
## <a name="component"></a><span data-ttu-id="ef31d-106">元件</span><span class="sxs-lookup"><span data-stu-id="ef31d-106">Component</span></span>  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a><span data-ttu-id="ef31d-107">描述</span><span class="sxs-lookup"><span data-stu-id="ef31d-107">Description</span></span>  
 <span data-ttu-id="ef31d-108">升級 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 安裝包括保留報表伺服器 Web 服務和報表管理員的新 URL。</span><span class="sxs-lookup"><span data-stu-id="ef31d-108">Upgrading a [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] installation includes reserving new URLs for the Report Server Web service and Report Manager.</span></span> <span data-ttu-id="ef31d-109">Upgrade Advisor 未偵測到要升級之執行個體的報表伺服器或報表管理員的虛擬目錄，因此升級程序的資訊不足，無法建立升級報表伺服器的 URL 保留項目。</span><span class="sxs-lookup"><span data-stu-id="ef31d-109">Upgrade Advisor did not detect virtual directories for the report server or Report Manager for the instance to be upgraded, and therefore the upgrade process has insufficient information to create URL reservations for the upgraded report server.</span></span> <span data-ttu-id="ef31d-110">雖然升級可以繼續進行，但是在升級的安裝之後，報表伺服器或報表管理員虛擬目錄將處於未定義狀態。</span><span class="sxs-lookup"><span data-stu-id="ef31d-110">Upgrade can continue, but the report server or Report Manager virtual directory will be undefined after the upgraded installation.</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="ef31d-111">更正動作</span><span class="sxs-lookup"><span data-stu-id="ef31d-111">Corrective Action</span></span>  
 <span data-ttu-id="ef31d-112">升級完成之後，請使用 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 組態管理員來設定報表伺服器和報表管理員的 URL。</span><span class="sxs-lookup"><span data-stu-id="ef31d-112">After upgrade finishes, use the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager to set the URLs for report server and Report Manager.</span></span> <span data-ttu-id="ef31d-113">您可以使用 IIS 管理員來移除任何不再需要的虛擬目錄。</span><span class="sxs-lookup"><span data-stu-id="ef31d-113">Use IIS Manager to remove any virtual directories you no longer need.</span></span>  
  
 <span data-ttu-id="ef31d-114">如需詳細資訊，請參閱《線上叢書》中的[Configure a URL &#40;SSRS Configuration Manager&#41;](../../reporting-services/install-windows/configure-a-url-ssrs-configuration-manager.md) [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="ef31d-114">For more information, see [Configure a URL  &#40;SSRS Configuration Manager&#41;](../../reporting-services/install-windows/configure-a-url-ssrs-configuration-manager.md) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef31d-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ef31d-115">See Also</span></span>  
 [<span data-ttu-id="ef31d-116">&#40;Upgrade Advisor Reporting Services 升級問題&#41;</span><span class="sxs-lookup"><span data-stu-id="ef31d-116">Reporting Services Upgrade Issues &#40;Upgrade Advisor&#41;</span></span>](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md)  
  
  
