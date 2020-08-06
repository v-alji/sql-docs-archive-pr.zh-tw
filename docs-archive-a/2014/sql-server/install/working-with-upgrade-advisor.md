---
title: 使用 Upgrade Advisor |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Upgrade Advisor [SQL Server], when to use
- SQL Server Upgrade Advisor, when to use
- when to use Upgrade Advisor
ms.assetid: 5f26a7b9-1ac2-442c-8316-87b078db3baf
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 75a16e57734493cdd7ac00e7bad3124eb7a99d84
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595376"
---
# <a name="working-with-upgrade-advisor"></a><span data-ttu-id="07b3e-102">使用 Upgrade Advisor</span><span class="sxs-lookup"><span data-stu-id="07b3e-102">Working with Upgrade Advisor</span></span>
  <span data-ttu-id="07b3e-103">為了確保能夠成功升級至 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]，Upgrade Advisor 提供了中央主控台，可識別在升級至 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 之前，安裝中需要處理的問題。</span><span class="sxs-lookup"><span data-stu-id="07b3e-103">To help ensure that your upgrade to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] is successful, Upgrade Advisor provides a central console to identify issues to address in your installations before upgrading to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span>  
  
 <span data-ttu-id="07b3e-104">您可以使用 Upgrade Advisor 來執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="07b3e-104">You can use Upgrade Advisor to perform the following tasks:</span></span>  
  
-   <span data-ttu-id="07b3e-105">在本機或遠端伺服器上分析舊版元件。</span><span class="sxs-lookup"><span data-stu-id="07b3e-105">Analyze previous version's components on local or remote servers.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="07b3e-106">您無法分析 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 的遠端執行個體。</span><span class="sxs-lookup"><span data-stu-id="07b3e-106">You cannot analyze remote instances of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="07b3e-107">檢視分析的結果。</span><span class="sxs-lookup"><span data-stu-id="07b3e-107">View the results of the analysis.</span></span>  
  
 <span data-ttu-id="07b3e-108">Upgrade Advisor 含有一個分析器和一個檢視器。</span><span class="sxs-lookup"><span data-stu-id="07b3e-108">Upgrade Advisor includes an analyzer and a viewer.</span></span> <span data-ttu-id="07b3e-109">Upgrade Advisor 分析精靈會分析您所選取的元件。</span><span class="sxs-lookup"><span data-stu-id="07b3e-109">The Upgrade Advisor Analysis Wizard analyzes the components you select.</span></span> <span data-ttu-id="07b3e-110">然後，分析器會針對您必須處理才能升級至 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 的問題產生相關的自訂報表。</span><span class="sxs-lookup"><span data-stu-id="07b3e-110">The analyzer then generates custom reports about issues that you must handle before you can upgrade to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="07b3e-111">您可以使用 Upgrade Advisor 報表檢視器來檢視這些自訂報表。</span><span class="sxs-lookup"><span data-stu-id="07b3e-111">You use the Upgrade Advisor Report Viewer to view the custom reports.</span></span> <span data-ttu-id="07b3e-112">如需 Upgrade Advisor 分析所偵測到的詳細資訊，請參閱[解決升級問題](../../../2014/sql-server/install/resolving-upgrade-issues.md)。</span><span class="sxs-lookup"><span data-stu-id="07b3e-112">For more information about what Upgrade Advisor analysis detects, see [Resolving Upgrade Issues](../../../2014/sql-server/install/resolving-upgrade-issues.md).</span></span>  
  
 <span data-ttu-id="07b3e-113">本節中的主題提供 Upgrade Advisor 功能的概觀，以及有關如何使用 Upgrade Advisor 和 Upgrade Advisor 報表的資訊。</span><span class="sxs-lookup"><span data-stu-id="07b3e-113">The topics in this section provide an overview of Upgrade Advisor functionality and information about how to use Upgrade Advisor and Upgrade Advisor reports.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="07b3e-114">本節內容</span><span class="sxs-lookup"><span data-stu-id="07b3e-114">In This Section</span></span>  
  
|<span data-ttu-id="07b3e-115">主題</span><span class="sxs-lookup"><span data-stu-id="07b3e-115">Topic</span></span>|<span data-ttu-id="07b3e-116">描述</span><span class="sxs-lookup"><span data-stu-id="07b3e-116">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="07b3e-117">升級建議程式概觀</span><span class="sxs-lookup"><span data-stu-id="07b3e-117">Overview of Upgrade Advisor</span></span>](../../../2014/sql-server/install/overview-of-upgrade-advisor.md)|<span data-ttu-id="07b3e-118">提供升級程序、Upgrade Advisor 分析精靈和 Upgrade Advisor 報表檢視器的概觀。</span><span class="sxs-lookup"><span data-stu-id="07b3e-118">Provides an overview of the upgrade process, the Upgrade Advisor Analysis Wizard, and the Upgrade Advisor Report Viewer.</span></span>|  
|[<span data-ttu-id="07b3e-119">升級建議程式使用說明主題</span><span class="sxs-lookup"><span data-stu-id="07b3e-119">Upgrade Advisor How-to Topics</span></span>](../../../2014/sql-server/install/upgrade-advisor-how-to-topics.md)|<span data-ttu-id="07b3e-120">提供執行常見 Upgrade Advisor 程序的指示。</span><span class="sxs-lookup"><span data-stu-id="07b3e-120">Provides instructions to perform common Upgrade Advisor procedures.</span></span>|  
|[<span data-ttu-id="07b3e-121">Upgrade Advisor 使用者介面參考</span><span class="sxs-lookup"><span data-stu-id="07b3e-121">Upgrade Advisor User Interface Reference</span></span>](../../../2014/sql-server/install/upgrade-advisor-user-interface-reference.md)|<span data-ttu-id="07b3e-122">包含當您按下 F1 鍵或在 Upgrade Advisor 分析 Wizard**頁面上按一下**[說明] 時所顯示的主題。</span><span class="sxs-lookup"><span data-stu-id="07b3e-122">Contains topics that appear if you press the F1 key or click **Help** on the Upgrade Advisor Analysis Wizard pages.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="07b3e-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="07b3e-123">See Also</span></span>  
 <span data-ttu-id="07b3e-124">[安裝 Upgrade Advisor](../../../2014/sql-server/install/installing-upgrade-advisor.md) </span><span class="sxs-lookup"><span data-stu-id="07b3e-124">[Installing Upgrade Advisor](../../../2014/sql-server/install/installing-upgrade-advisor.md) </span></span>  
 [<span data-ttu-id="07b3e-125">解決升級問題</span><span class="sxs-lookup"><span data-stu-id="07b3e-125">Resolving Upgrade Issues</span></span>](../../../2014/sql-server/install/resolving-upgrade-issues.md)  
  
  
