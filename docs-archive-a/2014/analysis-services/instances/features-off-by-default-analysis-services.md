---
title: 功能預設為關閉 (Analysis Services) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: a9529edf-337e-4fdd-9a13-99cfe96b4fa1
author: minewiskan
ms.author: owend
ms.openlocfilehash: 87752b8760ffc80e80c87ac1132cae36f2f151b4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87698785"
---
# <a name="features-off-by-default-analysis-services"></a><span data-ttu-id="e89be-102">預設關閉的功能 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="e89be-102">Features off by default (Analysis Services)</span></span>
  <span data-ttu-id="e89be-103">依預設， [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 執行個體的設計是安全的。</span><span class="sxs-lookup"><span data-stu-id="e89be-103">An instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] is designed to be secure by default.</span></span> <span data-ttu-id="e89be-104">因此，依預設會停用有可能危及安全性的功能。</span><span class="sxs-lookup"><span data-stu-id="e89be-104">Therefore, features that might compromise security are disabled by default.</span></span> <span data-ttu-id="e89be-105">下列功能會以停用狀態安裝，如果您想要使用這些功能，必須特地加以啟用：</span><span class="sxs-lookup"><span data-stu-id="e89be-105">The following features are installed in a disabled state and must specifically be enabled if you want to use them.</span></span>  
  
## <a name="feature-list"></a><span data-ttu-id="e89be-106">功能清單</span><span class="sxs-lookup"><span data-stu-id="e89be-106">Feature List</span></span>  
 <span data-ttu-id="e89be-107">若要啟用下列功能，請使用 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 連接至 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="e89be-107">To enable the following features, connect to [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="e89be-108">以滑鼠右鍵按一下執行個體名稱，然後選擇 [Facet]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e89be-108">Right-click the instance name and choose **Facets**.</span></span> <span data-ttu-id="e89be-109">或者，可利用下節中所述的伺服器屬性，啟用這些功能。</span><span class="sxs-lookup"><span data-stu-id="e89be-109">Alternatively, you can enable these features through server properties, as described in the next section.</span></span>  
  
-   <span data-ttu-id="e89be-110">特定資料採礦 (OpenRowset) 查詢</span><span class="sxs-lookup"><span data-stu-id="e89be-110">Ad Hoc Data Mining (OpenRowset) Queries</span></span>  
  
-   <span data-ttu-id="e89be-111">連結物件 (To)</span><span class="sxs-lookup"><span data-stu-id="e89be-111">Linked Objects (To)</span></span>  
  
-   <span data-ttu-id="e89be-112">連結物件 (From)</span><span class="sxs-lookup"><span data-stu-id="e89be-112">Linked Objects (From)</span></span>  
  
-   <span data-ttu-id="e89be-113">只接聽本機連接</span><span class="sxs-lookup"><span data-stu-id="e89be-113">Listen Only On Local Connections</span></span>  
  
-   <span data-ttu-id="e89be-114">使用者定義的函式</span><span class="sxs-lookup"><span data-stu-id="e89be-114">User Defined Functions</span></span>  
  
## <a name="server-properties"></a><span data-ttu-id="e89be-115">伺服器屬性</span><span class="sxs-lookup"><span data-stu-id="e89be-115">Server properties</span></span>  
 <span data-ttu-id="e89be-116">其他依預設關閉的功能，均可透過伺服器屬性加以啟用。</span><span class="sxs-lookup"><span data-stu-id="e89be-116">Additional features that are off by default can be enabled through server properties.</span></span> <span data-ttu-id="e89be-117">使用 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 連接到 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="e89be-117">Connect to [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="e89be-118">以滑鼠右鍵按一下執行個體名稱，然後選擇 [屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e89be-118">Right-click the instance name and choose **Properties**.</span></span> <span data-ttu-id="e89be-119">按一下 [一般] \*\*\*\*，然後按一下 [顯示進階] \*\*\*\* 即可顯示更大的屬性清單。</span><span class="sxs-lookup"><span data-stu-id="e89be-119">Click **General**, and then click **Show Advanced** to display a larger property list.</span></span>  
  
-   <span data-ttu-id="e89be-120">特定資料採礦 (OpenRowset) 查詢</span><span class="sxs-lookup"><span data-stu-id="e89be-120">Ad Hoc Data Mining (OpenRowset) Queries</span></span>  
  
-   <span data-ttu-id="e89be-121">允許工作階段採礦模型 (資料採礦)</span><span class="sxs-lookup"><span data-stu-id="e89be-121">Allow Session Mining Models (Data Mining)</span></span>  
  
-   <span data-ttu-id="e89be-122">連結物件 (To)</span><span class="sxs-lookup"><span data-stu-id="e89be-122">Linked Objects (To)</span></span>  
  
-   <span data-ttu-id="e89be-123">連結物件 (From)</span><span class="sxs-lookup"><span data-stu-id="e89be-123">Linked Objects (From)</span></span>  
  
-   <span data-ttu-id="e89be-124">以 COM 為基礎的使用者定義函式</span><span class="sxs-lookup"><span data-stu-id="e89be-124">COM based user-defined functions</span></span>  
  
-   <span data-ttu-id="e89be-125">飛行記錄器追蹤定義 (範本)。</span><span class="sxs-lookup"><span data-stu-id="e89be-125">Flight Recorder Trace Definitions (templates).</span></span>  
  
-   <span data-ttu-id="e89be-126">查詢記錄</span><span class="sxs-lookup"><span data-stu-id="e89be-126">Query logging</span></span>  
  
-   <span data-ttu-id="e89be-127">只接聽本機連接</span><span class="sxs-lookup"><span data-stu-id="e89be-127">Listen Only On Local Connections</span></span>  
  
-   <span data-ttu-id="e89be-128">二進位 XML</span><span class="sxs-lookup"><span data-stu-id="e89be-128">Binary XML</span></span>  
  
-   <span data-ttu-id="e89be-129">壓縮</span><span class="sxs-lookup"><span data-stu-id="e89be-129">Compression</span></span>  
  
-   <span data-ttu-id="e89be-130">群組相似性。</span><span class="sxs-lookup"><span data-stu-id="e89be-130">Group affinity.</span></span> <span data-ttu-id="e89be-131">如需詳細資訊，請參閱＜ [Thread Pool Properties](../server-properties/thread-pool-properties.md) ＞。</span><span class="sxs-lookup"><span data-stu-id="e89be-131">See [Thread Pool Properties](../server-properties/thread-pool-properties.md) for details.</span></span>  
  
  
