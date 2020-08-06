---
title: 在報表伺服器電腦上偵測到已淘汰的延伸模組 (Upgrade Advisor) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- report servers [Reporting Services], upgrade issues
ms.assetid: 40d245a2-0631-470e-81b3-1feb47e028cb
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 9da9c47285bf809fdf6c89d67e847304d7d29a81
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606021"
---
# <a name="obsolete-extensions-were-detected-on-the-report-server-computer-upgrade-advisor"></a><span data-ttu-id="2e7e1-102">在報表伺服器電腦上偵測到過時的延伸模組 (Upgrade Advisor)</span><span class="sxs-lookup"><span data-stu-id="2e7e1-102">Obsolete extensions were detected on the report server computer (Upgrade Advisor)</span></span>
  <span data-ttu-id="2e7e1-103">Upgrade Advisor 偵測到一個或多個在目前版本中已經無法使用的轉譯延伸模組。</span><span class="sxs-lookup"><span data-stu-id="2e7e1-103">Upgrade Advisor detected one or more rendering extensions that are no longer available in the current release.</span></span>  
  
||  
|-|  
|<span data-ttu-id="2e7e1-104">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 原生模式 &#124; [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint 模式。</span><span class="sxs-lookup"><span data-stu-id="2e7e1-104">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Native mode &#124; [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint mode.</span></span>|  
  
## <a name="component"></a><span data-ttu-id="2e7e1-105">元件</span><span class="sxs-lookup"><span data-stu-id="2e7e1-105">Component</span></span>  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a><span data-ttu-id="2e7e1-106">描述</span><span class="sxs-lookup"><span data-stu-id="2e7e1-106">Description</span></span>  
 <span data-ttu-id="2e7e1-107">報表伺服器設定為使用一或多個在這個版本中已經停止的延伸模組。</span><span class="sxs-lookup"><span data-stu-id="2e7e1-107">The report server is configured to use one or more extensions that have been discontinued in this release.</span></span> <span data-ttu-id="2e7e1-108">已停止的延伸模組包括：</span><span class="sxs-lookup"><span data-stu-id="2e7e1-108">Discontinued extensions include:</span></span>  
  
-   <span data-ttu-id="2e7e1-109">HTML OWC 轉譯延伸模組</span><span class="sxs-lookup"><span data-stu-id="2e7e1-109">HTML OWC rendering extension</span></span>  
  
-   <span data-ttu-id="2e7e1-110">HTML 3.2 轉譯延伸模組</span><span class="sxs-lookup"><span data-stu-id="2e7e1-110">HTML 3.2 rendering extension</span></span>  
  
 <span data-ttu-id="2e7e1-111">雖然升級可以繼續進行，但是不支援的功能將無法在升級的報表伺服器上使用。</span><span class="sxs-lookup"><span data-stu-id="2e7e1-111">Upgrade can continue, but the unsupported functionality will no longer be available on the upgraded report server.</span></span>  
  
 <span data-ttu-id="2e7e1-112">如果您需要使用這些延伸模組，在找到這些需求的替代方案之前，請勿進行升級。</span><span class="sxs-lookup"><span data-stu-id="2e7e1-112">If you require these extensions, do not upgrade until you find an alternate solution to these requirements.</span></span> <span data-ttu-id="2e7e1-113">您可能必須取得或建立可提供相同或類似功能的自訂轉譯延伸模組。</span><span class="sxs-lookup"><span data-stu-id="2e7e1-113">You might need to obtain or build a custom rendering extension that provides the same or similar functionality.</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="2e7e1-114">更正動作</span><span class="sxs-lookup"><span data-stu-id="2e7e1-114">Corrective Action</span></span>  
 <span data-ttu-id="2e7e1-115">評估目前 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 中所包含的功能集，以便判斷支援的功能是否符合您的需求。</span><span class="sxs-lookup"><span data-stu-id="2e7e1-115">Evaluate the current set of features that are included in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] to determine whether supported functionality meets your requirements.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e7e1-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2e7e1-116">See Also</span></span>  
 [<span data-ttu-id="2e7e1-117">&#40;Upgrade Advisor Reporting Services 升級問題&#41;</span><span class="sxs-lookup"><span data-stu-id="2e7e1-117">Reporting Services Upgrade Issues &#40;Upgrade Advisor&#41;</span></span>](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md)  
  
  
