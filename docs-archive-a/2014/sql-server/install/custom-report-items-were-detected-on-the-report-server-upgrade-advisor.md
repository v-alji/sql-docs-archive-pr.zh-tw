---
title: 在報表伺服器上偵測到自訂報表專案 (Upgrade Advisor) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- custom report items, upgrading
ms.assetid: aee32006-65b2-4dfe-9570-d85a249d17b2
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: feacf6aa6f233f85a67b43e7b72d3a50913991bf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593771"
---
# <a name="custom-report-items-were-detected-on-the-report-server-upgrade-advisor"></a><span data-ttu-id="3a7c6-102">在報表伺服器上偵測到自訂報表項目 (Upgrade Advisor)</span><span class="sxs-lookup"><span data-stu-id="3a7c6-102">Custom report items were detected on the report server (Upgrade Advisor)</span></span>
  <span data-ttu-id="3a7c6-103">針對舊版所建立的自訂報表專案 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 與不相容 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="3a7c6-103">Custom report items that were created for previous releases of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] are not compatible with [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="3a7c6-104">雖然升級可以繼續進行，但是使用自訂報表項目的報表將無法如預期方式執行。</span><span class="sxs-lookup"><span data-stu-id="3a7c6-104">Upgrade can continue, but reports that use the custom report item will not run as expected.</span></span> <span data-ttu-id="3a7c6-105">Upgrade Advisor 偵測到自訂報表項目。</span><span class="sxs-lookup"><span data-stu-id="3a7c6-105">Upgrade Advisor detected custom report items.</span></span> <span data-ttu-id="3a7c6-106">雖然升級可以繼續進行，但是您必須在升級完成之後，手動將自訂報表項目檔案移至新的安裝資料夾。</span><span class="sxs-lookup"><span data-stu-id="3a7c6-106">Upgrade can continue, but you must manually move the custom report item files to the new installation folder after upgrade completes.</span></span>  
  
||  
|-|  
|<span data-ttu-id="3a7c6-107">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 原生模式 &#124; [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint 模式。</span><span class="sxs-lookup"><span data-stu-id="3a7c6-107">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Native mode &#124; [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint mode.</span></span>|  
  
## <a name="component"></a><span data-ttu-id="3a7c6-108">元件</span><span class="sxs-lookup"><span data-stu-id="3a7c6-108">Component</span></span>  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a><span data-ttu-id="3a7c6-109">描述</span><span class="sxs-lookup"><span data-stu-id="3a7c6-109">Description</span></span>  
 <span data-ttu-id="3a7c6-110">Upgrade Advisor 偵測到組態檔中有自訂 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 延伸模組設定，表示安裝包括報表的一個或多個自訂組件。</span><span class="sxs-lookup"><span data-stu-id="3a7c6-110">Upgrade Advisor detected custom [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] extension settings in the configuration files, indicating that your installation includes one or more custom assemblies for reports.</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="3a7c6-111">更正動作</span><span class="sxs-lookup"><span data-stu-id="3a7c6-111">Corrective Action</span></span>  
 <span data-ttu-id="3a7c6-112">升級完成之後，請手動將自訂報表項目檔案移至新的安裝資料夾。</span><span class="sxs-lookup"><span data-stu-id="3a7c6-112">After upgrade completes, manually move the custom report item files to the new installation folder.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a7c6-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3a7c6-113">See Also</span></span>  
 [<span data-ttu-id="3a7c6-114">&#40;Upgrade Advisor Reporting Services 升級問題&#41;</span><span class="sxs-lookup"><span data-stu-id="3a7c6-114">Reporting Services Upgrade Issues &#40;Upgrade Advisor&#41;</span></span>](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md)  
  
  
