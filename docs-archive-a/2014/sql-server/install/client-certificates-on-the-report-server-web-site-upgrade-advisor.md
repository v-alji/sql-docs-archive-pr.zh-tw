---
title: 報表伺服器網站上的用戶端憑證 (Upgrade Advisor) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- report servers [Reporting Services], upgrade issues
ms.assetid: 5ecce26b-99df-4109-8e51-d150d369dff7
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 563a64e695ef552a712a5678f56d38fdfbff619f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595509"
---
# <a name="client-certificates-on-the-report-server-web-site-upgrade-advisor"></a><span data-ttu-id="1dccc-102">報表伺服器網站上的用戶端憑證 (Upgrade Advisor)</span><span class="sxs-lookup"><span data-stu-id="1dccc-102">Client certificates on the report server web site (Upgrade Advisor)</span></span>
  <span data-ttu-id="1dccc-103">Upgrade Advisor 在主控報表伺服器或報表管理員虛擬目錄的 IIS 網站上偵測到一或多個用戶端憑證。</span><span class="sxs-lookup"><span data-stu-id="1dccc-103">Upgrade Advisor detected one or more client certificates on the IIS Web site that hosts the report server or Report Manager virtual directories.</span></span>  
  
||  
|-|  
|<span data-ttu-id="1dccc-104">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]原生模式。</span><span class="sxs-lookup"><span data-stu-id="1dccc-104">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Native mode.</span></span>|  
  
## <a name="component"></a><span data-ttu-id="1dccc-105">元件</span><span class="sxs-lookup"><span data-stu-id="1dccc-105">Component</span></span>  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a><span data-ttu-id="1dccc-106">描述</span><span class="sxs-lookup"><span data-stu-id="1dccc-106">Description</span></span>  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<span data-ttu-id="1dccc-107">不 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 支援使用用戶端憑證來驗證使用者。</span><span class="sxs-lookup"><span data-stu-id="1dccc-107">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] does not support the use of client certificates to authenticate users.</span></span> <span data-ttu-id="1dccc-108">雖然升級可以繼續進行，但是升級的報表伺服器將不會使用用戶端憑證。</span><span class="sxs-lookup"><span data-stu-id="1dccc-108">Upgrade can continue, but client certificates will not be used by the upgraded report server.</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="1dccc-109">更正動作</span><span class="sxs-lookup"><span data-stu-id="1dccc-109">Corrective Action</span></span>  
 <span data-ttu-id="1dccc-110">您必須使用個別的解決方案 (例如 ISA Server) 來確保任何用戶端憑證驗證需求都會獲得處理。</span><span class="sxs-lookup"><span data-stu-id="1dccc-110">You will have to use a separate solution such as ISA Server to ensure any client certificate authentication requirements are addressed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1dccc-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1dccc-111">See Also</span></span>  
 [<span data-ttu-id="1dccc-112">&#40;Upgrade Advisor Reporting Services 升級問題&#41;</span><span class="sxs-lookup"><span data-stu-id="1dccc-112">Reporting Services Upgrade Issues &#40;Upgrade Advisor&#41;</span></span>](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md)  
  
  
