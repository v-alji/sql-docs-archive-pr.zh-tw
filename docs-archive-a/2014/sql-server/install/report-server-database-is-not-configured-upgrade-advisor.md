---
title: 未設定報表伺服器資料庫 (Upgrade Advisor) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- report servers [Reporting Services], upgrade issues
ms.assetid: b964300c-b220-4244-9fa6-c0c6a57760f6
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 072e689da3f43222396f071e607214a2ec494749
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584987"
---
# <a name="report-server-database-is-not-configured-upgrade-advisor"></a><span data-ttu-id="6083c-102">未設定報表伺服器資料庫 (Upgrade Advisor)</span><span class="sxs-lookup"><span data-stu-id="6083c-102">Report server database is not configured (Upgrade Advisor)</span></span>
  <span data-ttu-id="6083c-103">由於報表伺服器組態不完整，因此系統封鎖了升級。</span><span class="sxs-lookup"><span data-stu-id="6083c-103">Upgrade is blocked due to an incomplete report server configuration.</span></span> <span data-ttu-id="6083c-104">未設定報表伺服器資料庫。</span><span class="sxs-lookup"><span data-stu-id="6083c-104">The report server database is not configured.</span></span>  
  
||  
|-|  
|<span data-ttu-id="6083c-105">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 原生模式 &#124; [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint 模式。</span><span class="sxs-lookup"><span data-stu-id="6083c-105">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Native mode &#124; [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint mode.</span></span>|  
  
## <a name="component"></a><span data-ttu-id="6083c-106">元件</span><span class="sxs-lookup"><span data-stu-id="6083c-106">Component</span></span>  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a><span data-ttu-id="6083c-107">描述</span><span class="sxs-lookup"><span data-stu-id="6083c-107">Description</span></span>  
 <span data-ttu-id="6083c-108">安裝程式只能升級已完全設定的報表伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="6083c-108">Setup can only upgrade a fully configured report server instance.</span></span> <span data-ttu-id="6083c-109">若要繼續，您必須設定報表伺服器資料庫，或使用 Microsoft Windows [**控制台**]，從安裝中移除報表伺服器功能 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="6083c-109">To continue, you must either configure the report server database, or use Microsoft Windows **Control Panel** to remove the report server feature from the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installation.</span></span> <span data-ttu-id="6083c-110">在您移除 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 之後，就可以升級其他 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 元件。</span><span class="sxs-lookup"><span data-stu-id="6083c-110">After you remove [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], you can upgrade other [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] components.</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="6083c-111">更正動作</span><span class="sxs-lookup"><span data-stu-id="6083c-111">Corrective Action</span></span>  
 <span data-ttu-id="6083c-112">如果您並未設定報表伺服器資料庫，報表伺服器便無法運作，而且您應該在升級之前移除它。</span><span class="sxs-lookup"><span data-stu-id="6083c-112">If you did not configure the report server database, the report server is not operational and should be removed prior to upgrade.</span></span>  
  
 <span data-ttu-id="6083c-113">如需卸載的詳細資訊 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ，請參閱[卸載 Reporting Services 2012](https://technet.microsoft.com/library/hh479745.aspx\(v=sql.11\))。</span><span class="sxs-lookup"><span data-stu-id="6083c-113">For additional information on uninstalling [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , see [Uninstall Reporting Services 2012](https://technet.microsoft.com/library/hh479745.aspx\(v=sql.11\)).</span></span> <span data-ttu-id="6083c-114">該主題描述如何解除安裝特定版本，而且程序與舊版的程序相似。</span><span class="sxs-lookup"><span data-stu-id="6083c-114">the topic describes how to uninstall a specific version and the procedures are similar for previous versions as well.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6083c-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6083c-115">See Also</span></span>  
 [<span data-ttu-id="6083c-116">&#40;Upgrade Advisor Reporting Services 升級問題&#41;</span><span class="sxs-lookup"><span data-stu-id="6083c-116">Reporting Services Upgrade Issues &#40;Upgrade Advisor&#41;</span></span>](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md)  
  
  
