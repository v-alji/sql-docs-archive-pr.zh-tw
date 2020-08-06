---
title: 未偵測到 IIS 回溯相容性元件 (Upgrade Advisor) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- IIS [Reporting Services]
ms.assetid: e794185a-0a77-480a-9aea-d09f8760a6b8
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: a5aad54a01b3840e121c6a63de0ea26f35921fa7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606029"
---
# <a name="iis-backward-compatibility-components-were-not-detected-upgrade-advisor"></a><span data-ttu-id="a71a3-102">未偵測到 IIS 回溯相容性元件 (Upgrade Advisor)</span><span class="sxs-lookup"><span data-stu-id="a71a3-102">IIS backward compatibility components were not detected (Upgrade Advisor)</span></span>
  <span data-ttu-id="a71a3-103">Upgrade Advisor 並未偵測到可提供安裝程式用來建立新 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] URL 之資訊的 IIS 元件和設定。</span><span class="sxs-lookup"><span data-stu-id="a71a3-103">Upgrade Advisor did not detect IIS components and settings that provide information used by Setup to create new [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] URLS.</span></span>  
  
||  
|-|  
|<span data-ttu-id="a71a3-104">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]原生模式。</span><span class="sxs-lookup"><span data-stu-id="a71a3-104">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Native mode.</span></span>|  
  
## <a name="component"></a><span data-ttu-id="a71a3-105">元件</span><span class="sxs-lookup"><span data-stu-id="a71a3-105">Component</span></span>  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a><span data-ttu-id="a71a3-106">描述</span><span class="sxs-lookup"><span data-stu-id="a71a3-106">Description</span></span>  
 <span data-ttu-id="a71a3-107">IIS 包含可提供有關報表伺服器和報表管理員虛擬目錄之資訊的元件，而且這些元件未安裝在報表伺服器電腦上。</span><span class="sxs-lookup"><span data-stu-id="a71a3-107">IIS includes components that provide information about the report server and Report Manager virtual directories, and those components are not installed on the report server computer.</span></span> <span data-ttu-id="a71a3-108">雖然升級可以繼續進行，但是升級將不會重建報表伺服器或報表管理員的 URL。</span><span class="sxs-lookup"><span data-stu-id="a71a3-108">Upgrade can continue, but URLs for the report server or Report Manager will not be recreated by upgrade.</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="a71a3-109">更正動作</span><span class="sxs-lookup"><span data-stu-id="a71a3-109">Corrective Action</span></span>  
 <span data-ttu-id="a71a3-110">升級完成之後，請使用 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 組態工具來設定報表伺服器或報表管理員的 URL。</span><span class="sxs-lookup"><span data-stu-id="a71a3-110">After upgrade finishes, use the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration tool to set the URLs for report server or Report Manager.</span></span> <span data-ttu-id="a71a3-111">您可以使用 IIS 管理員來移除不再需要的虛擬目錄。</span><span class="sxs-lookup"><span data-stu-id="a71a3-111">Use IIS Manager to remove the virtual directories you no longer need.</span></span>  
  
 <span data-ttu-id="a71a3-112">如需詳細資訊，請參閱《線上叢書》中的[Configure a URL &#40;SSRS Configuration Manager&#41;](../../reporting-services/install-windows/configure-a-url-ssrs-configuration-manager.md) [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="a71a3-112">For more information, see [Configure a URL  &#40;SSRS Configuration Manager&#41;](../../reporting-services/install-windows/configure-a-url-ssrs-configuration-manager.md) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a71a3-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a71a3-113">See Also</span></span>  
 [<span data-ttu-id="a71a3-114">&#40;Upgrade Advisor Reporting Services 升級問題&#41;</span><span class="sxs-lookup"><span data-stu-id="a71a3-114">Reporting Services Upgrade Issues &#40;Upgrade Advisor&#41;</span></span>](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md)  
  
  
