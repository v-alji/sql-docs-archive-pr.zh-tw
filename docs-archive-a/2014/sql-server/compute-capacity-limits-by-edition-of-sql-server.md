---
title: SQL Server 版本的計算容量限制 | Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
helpviewer_keywords:
- processors [SQL Server], supported
- number of processors supported
- maximum number of processors supported
ms.assetid: cd308bc9-9468-40cc-ad6e-1a8a69aca6c8
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: f098b019205417d0339f426832c5683e6b8fa7cc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595608"
---
# <a name="compute-capacity-limits-by-edition-of-sql-server"></a><span data-ttu-id="e2792-102">SQL Server 版本的計算容量限制</span><span class="sxs-lookup"><span data-stu-id="e2792-102">Compute Capacity Limits by Edition of SQL Server</span></span>
  <span data-ttu-id="e2792-103">本主題討論不同 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] 版本的計算容量限制以及它們在具有超執行緒處理器的實體和虛擬化環境中有何差異。</span><span class="sxs-lookup"><span data-stu-id="e2792-103">This topic discusses compute capacity limits for different editions of [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] and how they differ in physical and virtualized environments with hyperthreaded processors.</span></span>  
  
 <span data-ttu-id="e2792-104">![對應至計算容量限制](../../2014/getting-started/media/compute-capacity-limits.gif "對應至計算容量限制")</span><span class="sxs-lookup"><span data-stu-id="e2792-104">![Mappings to compute capacity limits](../../2014/getting-started/media/compute-capacity-limits.gif "Mappings to compute capacity limits")</span></span>  
  
 <span data-ttu-id="e2792-105">下表描述上圖所使用的註解：</span><span class="sxs-lookup"><span data-stu-id="e2792-105">The following table describes the notations being used in the above diagram:</span></span>  
  
|<span data-ttu-id="e2792-106">值</span><span class="sxs-lookup"><span data-stu-id="e2792-106">Value</span></span>|<span data-ttu-id="e2792-107">描述</span><span class="sxs-lookup"><span data-stu-id="e2792-107">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="e2792-108">0..1</span><span class="sxs-lookup"><span data-stu-id="e2792-108">0..1</span></span>|<span data-ttu-id="e2792-109">零個或一個</span><span class="sxs-lookup"><span data-stu-id="e2792-109">Zero or one</span></span>|  
|<span data-ttu-id="e2792-110">1</span><span class="sxs-lookup"><span data-stu-id="e2792-110">1</span></span>|<span data-ttu-id="e2792-111">只有一個</span><span class="sxs-lookup"><span data-stu-id="e2792-111">Exactly one</span></span>|  
|<span data-ttu-id="e2792-112">1..\*</span><span class="sxs-lookup"><span data-stu-id="e2792-112">1..\*</span></span>|<span data-ttu-id="e2792-113">一個或多個</span><span class="sxs-lookup"><span data-stu-id="e2792-113">One or more</span></span>|  
|<span data-ttu-id="e2792-114">0..\*</span><span class="sxs-lookup"><span data-stu-id="e2792-114">0..\*</span></span>|<span data-ttu-id="e2792-115">零個或多個</span><span class="sxs-lookup"><span data-stu-id="e2792-115">Zero or more</span></span>|  
|<span data-ttu-id="e2792-116">1..2</span><span class="sxs-lookup"><span data-stu-id="e2792-116">1..2</span></span>|<span data-ttu-id="e2792-117">一個或兩個</span><span class="sxs-lookup"><span data-stu-id="e2792-117">One or two</span></span>|  
  
> [!IMPORTANT]
>  <span data-ttu-id="e2792-118">詳細說明：</span><span class="sxs-lookup"><span data-stu-id="e2792-118">To elaborate further:</span></span>  
> 
>  1.  <span data-ttu-id="e2792-119">一個虛擬機器會被配置一個或多個虛擬處理器。</span><span class="sxs-lookup"><span data-stu-id="e2792-119">A virtual machine is allocated one or more virtual processors.</span></span>  
> 2.  <span data-ttu-id="e2792-120">一個或多個虛擬處理器只會配置給一個虛擬機器。</span><span class="sxs-lookup"><span data-stu-id="e2792-120">One or more virtual processors are allocated to exactly one virtual machine.</span></span>  
> 3.  <span data-ttu-id="e2792-121">零個或一個虛擬處理器會對應至零個或多個邏輯處理器。</span><span class="sxs-lookup"><span data-stu-id="e2792-121">Zero or one virtual processor is mapped to zero or more logical processors.</span></span> <span data-ttu-id="e2792-122">當虛擬處理器與邏輯處理器的對應為：</span><span class="sxs-lookup"><span data-stu-id="e2792-122">When the virtual processor to logical processor mapping is:</span></span>  
> 
>      -   <span data-ttu-id="e2792-123">一對零時，表示客體作業系統並未使用的未繫結邏輯處理器。</span><span class="sxs-lookup"><span data-stu-id="e2792-123">One-to-zero, it represents an unbound logical processor not used by the guest operating systems.</span></span>  
>     -   <span data-ttu-id="e2792-124">一對多時，表示過度認可。</span><span class="sxs-lookup"><span data-stu-id="e2792-124">One-to-many, it represents an overcommit.</span></span>  
>     -   <span data-ttu-id="e2792-125">零對多時，表示虛擬機器不存在主機系統上，因此 VM 並未使用任何邏輯處理器。</span><span class="sxs-lookup"><span data-stu-id="e2792-125">Zero-to-many, it represents the absence of virtual machine on the host system, so no logical processors are used by VMs.</span></span>  
> 4.  <span data-ttu-id="e2792-126">一個插槽會對應至零個或多個核心。</span><span class="sxs-lookup"><span data-stu-id="e2792-126">A socket is mapped to zero or more cores.</span></span> <span data-ttu-id="e2792-127">當插槽與核心的對應為：</span><span class="sxs-lookup"><span data-stu-id="e2792-127">When the socket to core mapping is:</span></span>  
> 
>      -   <span data-ttu-id="e2792-128">一對零時，表示空的插槽 (未安裝晶片)。</span><span class="sxs-lookup"><span data-stu-id="e2792-128">One-to-zero, it represents an empty socket (no chip installed).</span></span>  
>     -   <span data-ttu-id="e2792-129">一對一時，表示安裝至插槽的單核心晶片 (目前非常少見)。</span><span class="sxs-lookup"><span data-stu-id="e2792-129">One-to-one, it represents a single-core chip installed into the socket (very rare these days).</span></span>  
>     -   <span data-ttu-id="e2792-130">一對多時，表示安裝至插槽的多核心晶片 (一般的值為 2、4、8)。</span><span class="sxs-lookup"><span data-stu-id="e2792-130">One-to-many, it represents a multi-core ship installed into the socket (typical values are 2,4,8).</span></span>  
> 5.  <span data-ttu-id="e2792-131">一個核心會對應至一個或兩個邏輯處理器。</span><span class="sxs-lookup"><span data-stu-id="e2792-131">A core is mapped to one or two logical processors.</span></span> <span data-ttu-id="e2792-132">當核心與邏輯處理器的對應為：</span><span class="sxs-lookup"><span data-stu-id="e2792-132">When the core to logical processor mapping is:</span></span>  
> 
>      -   <span data-ttu-id="e2792-133">一對一時，表示超執行緒已關閉。</span><span class="sxs-lookup"><span data-stu-id="e2792-133">One-to-one, hyperthreading is off.</span></span>  
>     -   <span data-ttu-id="e2792-134">一對二時，表示超執行緒已開啟。</span><span class="sxs-lookup"><span data-stu-id="e2792-134">One-to-two, hyperthreading is on.</span></span>  
  
 <span data-ttu-id="e2792-135">下列定義適用於本主題中使用的詞彙：</span><span class="sxs-lookup"><span data-stu-id="e2792-135">The following definitions apply to the terms used throughout this topic:</span></span>  
  
-   <span data-ttu-id="e2792-136">從 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]、作業系統、應用程式或驅動程式的觀點而言，執行緒或邏輯處理器都是單一邏輯運算引擎。</span><span class="sxs-lookup"><span data-stu-id="e2792-136">A thread or logical processor is one logical computing engine from the perspective of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], the operating system, an application or driver.</span></span>  
  
-   <span data-ttu-id="e2792-137">一個核心是指一個處理處理器單元，可能是由一個或多個邏輯處理器組成。</span><span class="sxs-lookup"><span data-stu-id="e2792-137">A core is a processor unit, which can consist of one or more logical processors.</span></span>  
  
-   <span data-ttu-id="e2792-138">一個實體處理器可能是由一個或多個核心組成。</span><span class="sxs-lookup"><span data-stu-id="e2792-138">A physical processor can consist of one or more cores.</span></span> <span data-ttu-id="e2792-139">實體處理器與處理器封裝或插槽相同。</span><span class="sxs-lookup"><span data-stu-id="e2792-139">A physical processor is the same as a processor package, or a socket.</span></span>  
  
 <span data-ttu-id="e2792-140">具有多個實體處理器的系統或是具有多核心及/或超執行緒之實體處理器的系統可讓作業系統同時執行多個工作。</span><span class="sxs-lookup"><span data-stu-id="e2792-140">Systems with more than one physical processor or systems with physical processors that have multiple cores and/or hyperthreads enable the operating system to execute multiple tasks simultaneously.</span></span> <span data-ttu-id="e2792-141">每個執行的執行緒都會顯示成邏輯處理器。</span><span class="sxs-lookup"><span data-stu-id="e2792-141">Each thread of execution appears as a logical processor.</span></span> <span data-ttu-id="e2792-142">例如，如果您有一部具備兩個啟用超執行緒之四核心處理器的電腦，而且每個核心都有兩個執行緒，則總共有 16 個邏輯處理器：2 個處理器 x 4 個核心 (每個處理器) x 2 個執行緒 (每個核心)。</span><span class="sxs-lookup"><span data-stu-id="e2792-142">For example, if you have a computer that has two quad-core processors with hyper-threading enabled and two threads per core, you have 16 logical processors: 2 processors x 4 cores per processor x 2 threads per core.</span></span> <span data-ttu-id="e2792-143">請注意：</span><span class="sxs-lookup"><span data-stu-id="e2792-143">It is worth noting that:</span></span>  
  
-   <span data-ttu-id="e2792-144">來自超執行緒核心之單一執行緒的邏輯處理器計算容量小於來自停用超執行緒之相同核心的邏輯處理器計算容量。</span><span class="sxs-lookup"><span data-stu-id="e2792-144">The compute capacity of a logical processor from a single thread of a hyperthreaded core is less than the compute capacity of a logical processor from that same core with hyperthreading disabled.</span></span>  
  
-   <span data-ttu-id="e2792-145">但是，超執行緒核心中 2 個邏輯處理器的計算容量大於停用超執行緒之相同核心的計算容量。</span><span class="sxs-lookup"><span data-stu-id="e2792-145">But the compute capacity of the 2 logical processors in the hyperthreaded core is greater than the compute capacity of the same core with hyperthreading disabled.</span></span>  
  
 <span data-ttu-id="e2792-146">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 的每個版本都有兩個計算容量限制：</span><span class="sxs-lookup"><span data-stu-id="e2792-146">Each edition of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] has two compute capacity limits:</span></span>  
  
1.  <span data-ttu-id="e2792-147">插槽的數目上限 (與實體處理器、插槽或處理器封裝相同)。</span><span class="sxs-lookup"><span data-stu-id="e2792-147">A maximum number of Sockets (Same as Physical processor or Socket or Processor package).</span></span>  
  
2.  <span data-ttu-id="e2792-148">作業系統所報告的核心數目上限。</span><span class="sxs-lookup"><span data-stu-id="e2792-148">A maximum number of cores as reported by the operating system.</span></span>  
  
 <span data-ttu-id="e2792-149">這些限制適用於單一 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]執行個體。</span><span class="sxs-lookup"><span data-stu-id="e2792-149">These limits apply to a single instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="e2792-150">它們代表單一執行個體將會使用的計算容量上限。</span><span class="sxs-lookup"><span data-stu-id="e2792-150">They represent the maximum compute capacity that a single instance will use.</span></span> <span data-ttu-id="e2792-151">但是，它們不會限制可部署執行個體的伺服器。</span><span class="sxs-lookup"><span data-stu-id="e2792-151">They do not constrain the server upon which the instance may be deployed.</span></span> <span data-ttu-id="e2792-152">實際上，在相同的實體伺服器上部署多個 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 執行個體可以有效地使用插槽及/或核心數目超過下列容量限制之實體伺服器的運算容量。</span><span class="sxs-lookup"><span data-stu-id="e2792-152">In fact deploying multiple instances of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] on the same physical server is an efficient way to use the compute capacity of a physical server with more sockets and/or cores than the capacity limits below.</span></span>  
  
 <span data-ttu-id="e2792-153">下表指定每個 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]版本之單一執行個體的計算容量限制：</span><span class="sxs-lookup"><span data-stu-id="e2792-153">The following table specifies the compute capacity limits for a single instance of each edition of [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]:</span></span>  
  
|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] <span data-ttu-id="e2792-154">版本</span><span class="sxs-lookup"><span data-stu-id="e2792-154">Edition</span></span>|<span data-ttu-id="e2792-155">單一執行個體所使用的計算容量上限 ([!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)][!INCLUDE[ssDE](../includes/ssde-md.md)])</span><span class="sxs-lookup"><span data-stu-id="e2792-155">Maximum Compute Capacity Used by a Single Instance ([!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)][!INCLUDE[ssDE](../includes/ssde-md.md)])</span></span>|<span data-ttu-id="e2792-156">單一執行個體所使用的計算容量上限 (AS、RS)</span><span class="sxs-lookup"><span data-stu-id="e2792-156">Maximum Compute Capacity Used by a Single Instance (AS, RS)</span></span>|  
|---------------------------------------|--------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------|  
|<span data-ttu-id="e2792-157">Enterprise Edition：以核心為基礎的授權<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="e2792-157">Enterprise Edition: Core-based Licensing<sup>1</sup></span></span>|<span data-ttu-id="e2792-158">作業系統最大值</span><span class="sxs-lookup"><span data-stu-id="e2792-158">Operating system maximum</span></span>|<span data-ttu-id="e2792-159">作業系統最大值</span><span class="sxs-lookup"><span data-stu-id="e2792-159">Operating system maximum</span></span>|  
|<span data-ttu-id="e2792-160">開發人員</span><span class="sxs-lookup"><span data-stu-id="e2792-160">Developer</span></span>|<span data-ttu-id="e2792-161">作業系統最大值</span><span class="sxs-lookup"><span data-stu-id="e2792-161">Operating system maximum</span></span>|<span data-ttu-id="e2792-162">作業系統最大值</span><span class="sxs-lookup"><span data-stu-id="e2792-162">Operating system maximum</span></span>|  
|<span data-ttu-id="e2792-163">評估</span><span class="sxs-lookup"><span data-stu-id="e2792-163">Evaluation</span></span>|<span data-ttu-id="e2792-164">作業系統最大值</span><span class="sxs-lookup"><span data-stu-id="e2792-164">Operating system maximum</span></span>|<span data-ttu-id="e2792-165">作業系統最大值</span><span class="sxs-lookup"><span data-stu-id="e2792-165">Operating system maximum</span></span>|  
|<span data-ttu-id="e2792-166">商業智慧</span><span class="sxs-lookup"><span data-stu-id="e2792-166">Business Intelligence</span></span>|<span data-ttu-id="e2792-167">限制為 4 個插槽或 16 個核心的較小者</span><span class="sxs-lookup"><span data-stu-id="e2792-167">Limited to lesser of 4 Sockets or 16 cores</span></span>|<span data-ttu-id="e2792-168">作業系統最大值</span><span class="sxs-lookup"><span data-stu-id="e2792-168">Operating system maximum</span></span>|  
|<span data-ttu-id="e2792-169">標準</span><span class="sxs-lookup"><span data-stu-id="e2792-169">Standard</span></span>|<span data-ttu-id="e2792-170">限制為 4 個插槽或 16 個核心的較小者</span><span class="sxs-lookup"><span data-stu-id="e2792-170">Limited to lesser of 4 Sockets or 16 cores</span></span>|<span data-ttu-id="e2792-171">限制為 4 個插槽或 16 個核心的較小者</span><span class="sxs-lookup"><span data-stu-id="e2792-171">Limited to lesser of 4 Sockets or 16 cores</span></span>|  
|<span data-ttu-id="e2792-172">Web</span><span class="sxs-lookup"><span data-stu-id="e2792-172">Web</span></span>|<span data-ttu-id="e2792-173">限制為 4 個插槽或 16 個核心的較小者</span><span class="sxs-lookup"><span data-stu-id="e2792-173">Limited to lesser of 4 Sockets or 16 cores</span></span>|<span data-ttu-id="e2792-174">限制為 4 個插槽或 16 個核心的較小者</span><span class="sxs-lookup"><span data-stu-id="e2792-174">Limited to lesser of 4 Sockets or 16 cores</span></span>|  
|<span data-ttu-id="e2792-175">Express</span><span class="sxs-lookup"><span data-stu-id="e2792-175">Express</span></span>|<span data-ttu-id="e2792-176">限制為 1 個插槽或 4 個核心的較小者</span><span class="sxs-lookup"><span data-stu-id="e2792-176">Limited to lesser of 1 Socket or 4 cores</span></span>|<span data-ttu-id="e2792-177">限制為 1 個插槽或 4 個核心的較小者</span><span class="sxs-lookup"><span data-stu-id="e2792-177">Limited to lesser of 1 Socket or 4 cores</span></span>|  
|<span data-ttu-id="e2792-178">Express with Tools</span><span class="sxs-lookup"><span data-stu-id="e2792-178">Express with Tools</span></span>|<span data-ttu-id="e2792-179">限制為 1 個插槽或 4 個核心的較小者</span><span class="sxs-lookup"><span data-stu-id="e2792-179">Limited to lesser of 1 Socket or 4 cores</span></span>|<span data-ttu-id="e2792-180">限制為 1 個插槽或 4 個核心的較小者</span><span class="sxs-lookup"><span data-stu-id="e2792-180">Limited to lesser of 1 Socket or 4 cores</span></span>|  
|<span data-ttu-id="e2792-181">Express with Advanced Services</span><span class="sxs-lookup"><span data-stu-id="e2792-181">Express with Advanced Services</span></span>|<span data-ttu-id="e2792-182">限制為 1 個插槽或 4 個核心的較小者</span><span class="sxs-lookup"><span data-stu-id="e2792-182">Limited to lesser of 1 Socket or 4 cores</span></span>|<span data-ttu-id="e2792-183">限制為 1 個插槽或 4 個核心的較小者</span><span class="sxs-lookup"><span data-stu-id="e2792-183">Limited to lesser of 1 Socket or 4 cores</span></span>|  
  
 <span data-ttu-id="e2792-184"><sup>1</sup> Enterprise Edition （含伺服器 + 用戶端存取許可證） (CAL) 授權 (不適用於新的合約) 限制為每個實例最多20個核心 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="e2792-184"><sup>1</sup> Enterprise Edition with Server + Client Access License (CAL) based licensing (not available for new agreements) is limited to a maximum of 20 cores per [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] instance.</span></span> <span data-ttu-id="e2792-185">核心伺服器授權模式之下沒有任何限制。</span><span class="sxs-lookup"><span data-stu-id="e2792-185">There are no limits under the Core-based Server Licensing model.</span></span>  
  
 <span data-ttu-id="e2792-186">在虛擬化環境中，計算容量限制是以邏輯處理器 (而非核心) 的數目為基礎，因為客體應用程式看不見處理器架構。</span><span class="sxs-lookup"><span data-stu-id="e2792-186">In a virtualized environment, the compute capacity limit is based on the number of logical processors, not cores, because the processor architecture is not visible to the guest applications.</span></span>  <span data-ttu-id="e2792-187">例如，如果一部伺服器的四個插槽都插入四核心處理器，而且能夠針對每個核心啟用兩個超執行緒，則在啟用超執行緒的情況下，總共包含 32 個邏輯處理器，但是在停用超執行緒的情況下，只包含 16 個邏輯處理器。</span><span class="sxs-lookup"><span data-stu-id="e2792-187">For example, a server with four sockets populated with quad-core processors and the ability to enable two hyperthreads per core contains 32 logical processors with hyperthreading enabled but only 16 logical processors with hyperthreading disabled.</span></span> <span data-ttu-id="e2792-188">這些邏輯處理器可對應至伺服器上的虛擬機器，而該邏輯處理器上的虛擬機器計算負載會對應到主機伺服器中實體處理器上的執行執行緒。</span><span class="sxs-lookup"><span data-stu-id="e2792-188">These logical processors can be mapped to virtual machines on the server with the virtual machines' compute load on that logical processor mapped into a thread of execution on the physical processor in the host server.</span></span>  
  
 <span data-ttu-id="e2792-189">當每個虛擬處理器的效能都很重要時，您可能會想要停用超執行緒。</span><span class="sxs-lookup"><span data-stu-id="e2792-189">You may want to disable hyperthreading when the performance per virtual processor is important.</span></span> <span data-ttu-id="e2792-190">雖然您可以在 BIOS 設定期間使用處理器的 BIOS 設定來啟用或停用超執行緒，不過這種伺服器範圍的作業通常會影響伺服器上執行的所有工作負載。</span><span class="sxs-lookup"><span data-stu-id="e2792-190">One can enable or disable hyperthreading using a BIOS setting for the processor during the BIOS setup, but it is typically a server scoped operation that will impact all workloads running on the server.</span></span> <span data-ttu-id="e2792-191">因此，建議您分隔在虛擬化環境中執行的工作負載以及實體作業系統環境中可從超執行緒效能提升獲益的工作負載。</span><span class="sxs-lookup"><span data-stu-id="e2792-191">This may suggest separating workloads that will run in virtualized environments from those that would benefit from the hyperthreading performance boost in a physical operating system environment.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2792-192">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e2792-192">See Also</span></span>  
 <span data-ttu-id="e2792-193">[SQL Server 2014 的版本和元件](../sql-server/editions-and-components-of-sql-server-2016.md) </span><span class="sxs-lookup"><span data-stu-id="e2792-193">[Editions and Components of SQL Server 2014](../sql-server/editions-and-components-of-sql-server-2016.md) </span></span>  
 <span data-ttu-id="e2792-194">[SQL Server 2014 版本所支援的功能](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md) </span><span class="sxs-lookup"><span data-stu-id="e2792-194">[Features Supported by the Editions of SQL Server 2014](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md) </span></span>  
 <span data-ttu-id="e2792-195">[SQL Server 的最大容量規格](../sql-server/maximum-capacity-specifications-for-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="e2792-195">[Maximum Capacity Specifications for SQL Server](../sql-server/maximum-capacity-specifications-for-sql-server.md) </span></span>  
 [<span data-ttu-id="e2792-196">SQL Server 2014 快速入門安裝</span><span class="sxs-lookup"><span data-stu-id="e2792-196">Quick-Start Installation of SQL Server 2014</span></span>](../../2014/getting-started/quick-start-installation-of-sql-server-2014.md)  
  
  
