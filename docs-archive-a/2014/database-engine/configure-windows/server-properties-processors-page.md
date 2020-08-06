---
title: 伺服器屬性 (處理器頁面) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
f1_keywords:
- sql12.swb.serverproperties.processor.f1
ms.assetid: cc1581a2-492b-41f0-bda5-17909b65c4f7
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: c4d241f01de7ac961832e77bb09483cff275deb6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596888"
---
# <a name="server-properties-processors-page"></a><span data-ttu-id="20d51-102">伺服器屬性 (處理器頁面)</span><span class="sxs-lookup"><span data-stu-id="20d51-102">Server Properties (Processors Page)</span></span>
  <span data-ttu-id="20d51-103">使用此頁面來檢視或修改處理器選項。</span><span class="sxs-lookup"><span data-stu-id="20d51-103">Use this page to view or modify your processor options.</span></span> <span data-ttu-id="20d51-104">只有在安裝了一個以上的處理器時，處理器相似性設定才會啟用。</span><span class="sxs-lookup"><span data-stu-id="20d51-104">Processor affinity settings are only enabled when more than one processor is installed.</span></span>  
  
## <a name="options"></a><span data-ttu-id="20d51-105">選項。</span><span class="sxs-lookup"><span data-stu-id="20d51-105">Options</span></span>  
 <span data-ttu-id="20d51-106">**處理器相似性**</span><span class="sxs-lookup"><span data-stu-id="20d51-106">**Processor Affinity**</span></span>  
 <span data-ttu-id="20d51-107">將處理器指派給特定的執行緒，以避免執行處理器重新載入，並減少在處理器間進行執行緒的移轉。</span><span class="sxs-lookup"><span data-stu-id="20d51-107">Assigns processors to specific threads to eliminating processor reloads and reduce thread migration across processors.</span></span> <span data-ttu-id="20d51-108">如需詳細資訊，請參閱 [affinity mask 伺服器組態選項](affinity-mask-server-configuration-option.md)。</span><span class="sxs-lookup"><span data-stu-id="20d51-108">For more information, see [affinity mask Server Configuration Option](affinity-mask-server-configuration-option.md).</span></span>  
  
 <span data-ttu-id="20d51-109">**I/O 相似性**</span><span class="sxs-lookup"><span data-stu-id="20d51-109">**I/O Affinity**</span></span>  
 <span data-ttu-id="20d51-110">將 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 磁碟 I/O 繫結到指定 CPU 的子集。</span><span class="sxs-lookup"><span data-stu-id="20d51-110">Binds [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] disk I/Os to a specified subset of CPUs.</span></span> <span data-ttu-id="20d51-111">如需詳細資訊，請參閱 [affinity I/O mask 伺服器組態選項](affinity-input-output-mask-server-configuration-option.md)。</span><span class="sxs-lookup"><span data-stu-id="20d51-111">For more information, see [affinity Input-Output mask Server Configuration Option](affinity-input-output-mask-server-configuration-option.md).</span></span>  
  
 <span data-ttu-id="20d51-112">**自動設定所有處理器的處理器相似性遮罩**</span><span class="sxs-lookup"><span data-stu-id="20d51-112">**Automatically set processor affinity mask for all processors**</span></span>  
 <span data-ttu-id="20d51-113">允許 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 設定處理器相似性。</span><span class="sxs-lookup"><span data-stu-id="20d51-113">Allows [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to set the processor affinity.</span></span>  
  
 <span data-ttu-id="20d51-114">**自動設定所有處理器的 I/O 相似性遮罩**</span><span class="sxs-lookup"><span data-stu-id="20d51-114">**Automatically set I/O affinity mask for all processors**</span></span>  
 <span data-ttu-id="20d51-115">允許 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 設定 I/O 相似性。</span><span class="sxs-lookup"><span data-stu-id="20d51-115">Allows [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to set the I/O affinity.</span></span>  
  
 <span data-ttu-id="20d51-116">**最大工作者執行緒**</span><span class="sxs-lookup"><span data-stu-id="20d51-116">**Maximum worker threads**</span></span>  
 <span data-ttu-id="20d51-117">0 允許 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 能動態設定工作者執行緒的數目。</span><span class="sxs-lookup"><span data-stu-id="20d51-117">0 allows [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to dynamically set the number of worker threads.</span></span> <span data-ttu-id="20d51-118">此設定對大多數系統都是最佳的。</span><span class="sxs-lookup"><span data-stu-id="20d51-118">This setting is best for most systems.</span></span> <span data-ttu-id="20d51-119">然而，視系統組態而定，將此選項設定成特定的值，有時候可以提高效能。</span><span class="sxs-lookup"><span data-stu-id="20d51-119">However, depending on your system configuration, setting this option to a specific value sometimes improves performance.</span></span> <span data-ttu-id="20d51-120">如需詳細資訊，請參閱 [設定 max worker threads 伺服器組態選項](configure-the-max-worker-threads-server-configuration-option.md)。</span><span class="sxs-lookup"><span data-stu-id="20d51-120">For more information, see [Configure the max worker threads Server Configuration Option](configure-the-max-worker-threads-server-configuration-option.md).</span></span>  
  
 <span data-ttu-id="20d51-121">**提高 SQL Server 優先權**</span><span class="sxs-lookup"><span data-stu-id="20d51-121">**Boost SQL Server priority**</span></span>  
 <span data-ttu-id="20d51-122">指定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 是否要使用比同一台電腦上之其他處理序更高的 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 排序優先權來執行。</span><span class="sxs-lookup"><span data-stu-id="20d51-122">Specifies whether [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] should run at a higher [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows scheduling priority than other processes on the same computer.</span></span> <span data-ttu-id="20d51-123">如需詳細資訊，請參閱 [設定 priority boost 伺服器組態選項](configure-the-priority-boost-server-configuration-option.md)。</span><span class="sxs-lookup"><span data-stu-id="20d51-123">For more information, see [Configure the priority boost Server Configuration Option](configure-the-priority-boost-server-configuration-option.md).</span></span>  
  
 <span data-ttu-id="20d51-124">**使用 Windows Fibers (輕量型共用)**</span><span class="sxs-lookup"><span data-stu-id="20d51-124">**Use Windows fibers (lightweight pooling)**</span></span>  
 <span data-ttu-id="20d51-125">針對 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服務使用 Windows Fibers 而不用執行緒。</span><span class="sxs-lookup"><span data-stu-id="20d51-125">Use Windows fibers instead of threads for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service.</span></span> <span data-ttu-id="20d51-126">請注意，這只有在 Windows 2003 Server Edition 中才可以使用。</span><span class="sxs-lookup"><span data-stu-id="20d51-126">Note that this is only available in Windows 2003 Server Edition.</span></span> <span data-ttu-id="20d51-127">如需詳細資訊，請參閱 [輕量型共用伺服器組態選項](lightweight-pooling-server-configuration-option.md)。</span><span class="sxs-lookup"><span data-stu-id="20d51-127">For more information, see [lightweight pooling Server Configuration Option](lightweight-pooling-server-configuration-option.md).</span></span>  
  
 <span data-ttu-id="20d51-128">**設定的值**</span><span class="sxs-lookup"><span data-stu-id="20d51-128">**Configured Values**</span></span>  
 <span data-ttu-id="20d51-129">針對此窗格中的選項，顯示設定的值。</span><span class="sxs-lookup"><span data-stu-id="20d51-129">Displays the configured values for the options on this pane.</span></span> <span data-ttu-id="20d51-130">如果您變更這些值，請按一下 **[執行中的值]** ，即可查看變更是否已生效。</span><span class="sxs-lookup"><span data-stu-id="20d51-130">If you change these values, click **Running Values** to see whether the changes have taken effect.</span></span> <span data-ttu-id="20d51-131">如果沒有的話，就必須先重新啟動 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="20d51-131">If they have not, the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] must be restarted first.</span></span>  
  
 <span data-ttu-id="20d51-132">**[執行中的值]**</span><span class="sxs-lookup"><span data-stu-id="20d51-132">**Running Values**</span></span>  
 <span data-ttu-id="20d51-133">針對此窗格中的選項，檢視目前執行中的值。</span><span class="sxs-lookup"><span data-stu-id="20d51-133">View the currently running values for the options on this pane.</span></span> <span data-ttu-id="20d51-134">這些值是唯讀的。</span><span class="sxs-lookup"><span data-stu-id="20d51-134">These values are read-only.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20d51-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="20d51-135">See Also</span></span>  
 [<span data-ttu-id="20d51-136">伺服器組態選項 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="20d51-136">Server Configuration Options &#40;SQL Server&#41;</span></span>](server-configuration-options-sql-server.md)  
  
  
