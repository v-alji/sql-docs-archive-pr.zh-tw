---
title: 直接流覽至報表伺服器 (Upgrade Advisor) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 3d2814a4-318a-45ed-b093-1e852fab561f
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: ab4d146bba4bd87de56b30ad100b57f79eb68de3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606609"
---
# <a name="direct-browsing-to-report-server-upgrade-advisor"></a><span data-ttu-id="a1dbb-102">直接瀏覽報表伺服器 (Upgrade Advisor)</span><span class="sxs-lookup"><span data-stu-id="a1dbb-102">Direct Browsing to Report Server (Upgrade Advisor)</span></span>
  <span data-ttu-id="a1dbb-103">Upgrade Advisor 偵測到您目前的安裝 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 正在直接流覽至報表伺服器虛擬目錄。</span><span class="sxs-lookup"><span data-stu-id="a1dbb-103">Upgrade Advisor detected your current installation of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] is browsing directly to the report server virtual directory.</span></span>  
  
||  
|-|  
|<span data-ttu-id="a1dbb-104">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]SharePoint 模式。</span><span class="sxs-lookup"><span data-stu-id="a1dbb-104">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint mode.</span></span>|  
  
## <a name="component"></a><span data-ttu-id="a1dbb-105">元件</span><span class="sxs-lookup"><span data-stu-id="a1dbb-105">Component</span></span>  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a><span data-ttu-id="a1dbb-106">描述</span><span class="sxs-lookup"><span data-stu-id="a1dbb-106">Description</span></span>  
 <span data-ttu-id="a1dbb-107">Upgrade Advisor 偵測到您目前的安裝 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 正在直接流覽至報表伺服器虛擬目錄，例如**HTTP:// \<server name> /ReportServer**。</span><span class="sxs-lookup"><span data-stu-id="a1dbb-107">Upgrade Advisor detected your current installation of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] is browsing directly to the report server virtual directory, for example **http://\<server name>/ReportServer**.</span></span> <span data-ttu-id="a1dbb-108">在目前 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 版本中不支援。</span><span class="sxs-lookup"><span data-stu-id="a1dbb-108">This is not supported in current versions of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a1dbb-109">此規則是警告，升級未遭到封鎖。</span><span class="sxs-lookup"><span data-stu-id="a1dbb-109">This rule is a warning and upgrade is not blocked.</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="a1dbb-110">更正動作</span><span class="sxs-lookup"><span data-stu-id="a1dbb-110">Corrective Action</span></span>  
 <span data-ttu-id="a1dbb-111">使用文件庫的 SharePoint 使用者介面流覽，或使用**HTTP:// \<server name> /sharepoint site>/_vti_bin/reportserver**。</span><span class="sxs-lookup"><span data-stu-id="a1dbb-111">Browse using the SharePoint user interface for document libraries or use **http://\<server name>/sharepoint site>/_vti_bin/reportserver**.</span></span>  
  
  
