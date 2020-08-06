---
title: 虛擬目錄具有不支援的驗證方法 (Upgrade Advisor) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- virtual directories [Reporting Services]
ms.assetid: 216eca6f-9a66-42e1-aa54-dcf99cec9f7d
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 67b1c027b8ed020f65fdea7c093f6d5454f02c5e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595408"
---
# <a name="virtual-directory-has-unsupported-authentication-method-upgrade-advisor"></a><span data-ttu-id="e6842-102">虛擬目錄具有不支援的驗證方法 (Upgrade Advisor)</span><span class="sxs-lookup"><span data-stu-id="e6842-102">Virtual directory has unsupported authentication method (Upgrade Advisor)</span></span>
  <span data-ttu-id="e6842-103">Upgrade Advisor 在報表管理員或報表伺服器虛擬目錄上偵測到不支援的驗證方法。</span><span class="sxs-lookup"><span data-stu-id="e6842-103">Upgrade Advisor detected an unsupported authentication method on the Report Manager or report server virtual directory.</span></span> <span data-ttu-id="e6842-104">升級不支援的驗證方法包括匿名驗證、摘要式驗證和 .NET Passport。</span><span class="sxs-lookup"><span data-stu-id="e6842-104">Authentication methods that are not supported by upgrade include Anonymous, Digest, and .NET Passport.</span></span>  
  
||  
|-|  
|<span data-ttu-id="e6842-105">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]原生模式。</span><span class="sxs-lookup"><span data-stu-id="e6842-105">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Native mode.</span></span>|  
  
## <a name="component"></a><span data-ttu-id="e6842-106">元件</span><span class="sxs-lookup"><span data-stu-id="e6842-106">Component</span></span>  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a><span data-ttu-id="e6842-107">描述</span><span class="sxs-lookup"><span data-stu-id="e6842-107">Description</span></span>  
 <span data-ttu-id="e6842-108">安裝程式無法升級使用下列其中一種驗證方法的 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 安裝</span><span class="sxs-lookup"><span data-stu-id="e6842-108">Setup cannot upgrade a [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] installation that uses one of the following authentication methods</span></span>  
  
-   <span data-ttu-id="e6842-109">匿名</span><span class="sxs-lookup"><span data-stu-id="e6842-109">Anonymous</span></span>  
  
-   <span data-ttu-id="e6842-110">Digest</span><span class="sxs-lookup"><span data-stu-id="e6842-110">Digest</span></span>  
  
-   <span data-ttu-id="e6842-111">.NET Passport</span><span class="sxs-lookup"><span data-stu-id="e6842-111">.NET Passport</span></span>  
  
 <span data-ttu-id="e6842-112">若要繼續進行，您可以修改 Internet Information Services (IIS) 中針對 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 虛擬目錄指定的驗證方法，也可以移轉安裝。</span><span class="sxs-lookup"><span data-stu-id="e6842-112">To continue, you can either modify the Authentication method that is specified for the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] virtual directories in Internet Information Services (IIS), or you can migrate your installation.</span></span> <span data-ttu-id="e6842-113">如需有關移轉安裝的詳細資訊，請參閱《[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 線上叢書》。</span><span class="sxs-lookup"><span data-stu-id="e6842-113">For more information about migrating your installation, see [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="e6842-114">更正動作</span><span class="sxs-lookup"><span data-stu-id="e6842-114">Corrective Action</span></span>  
 <span data-ttu-id="e6842-115">若要繼續進行升級，請在 IIS 中針對 ReportServer 和 Reports 虛擬目錄修改驗證方法。</span><span class="sxs-lookup"><span data-stu-id="e6842-115">To continue with upgrade, modify the Authentication method in IIS for the ReportServer and Reports virtual directories.</span></span> <span data-ttu-id="e6842-116">如需有關在 IIS 中修改驗證方法的詳細資訊，請參閱 IIS 文件集。</span><span class="sxs-lookup"><span data-stu-id="e6842-116">For more information about modifying Authentication methods in IIS, see the IIS documentation.</span></span> <span data-ttu-id="e6842-117">在您針對 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 虛擬目錄修改驗證方法之後，請重新執行 Upgrade Advisor 來確認沒有其他升級問題。</span><span class="sxs-lookup"><span data-stu-id="e6842-117">After you modify the Authentication method for the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] virtual directories, re-run Upgrade Advisor to confirm that there are no other upgrade issues.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6842-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e6842-118">See Also</span></span>  
 [<span data-ttu-id="e6842-119">&#40;Upgrade Advisor Reporting Services 升級問題&#41;</span><span class="sxs-lookup"><span data-stu-id="e6842-119">Reporting Services Upgrade Issues &#40;Upgrade Advisor&#41;</span></span>](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md)  
  
  
