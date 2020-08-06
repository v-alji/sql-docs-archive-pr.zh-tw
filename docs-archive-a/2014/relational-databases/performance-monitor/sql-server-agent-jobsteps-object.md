---
title: SQL Server Agent、JobSteps 物件 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- JobSteps object
- SQLAgent:JobSteps
ms.assetid: 44f9983c-1753-4fe0-8475-973aa2460b3a
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 3759303807714e2bb7f71f59e644bc485d36cfcb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593342"
---
# <a name="sql-server-agent-jobsteps-object"></a><span data-ttu-id="4c2c1-102">SQL Server Agent、JobSteps 物件</span><span class="sxs-lookup"><span data-stu-id="4c2c1-102">SQL Server Agent, JobSteps Object</span></span>
  <span data-ttu-id="4c2c1-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 的 **JobSteps** 效能物件包含可報告 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 作業步驟相關資訊的效能計數器。</span><span class="sxs-lookup"><span data-stu-id="4c2c1-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent **JobSteps** performance object contains performance counters that report information about [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job steps.</span></span> <span data-ttu-id="4c2c1-104">下表列出這個物件包含的計數器。</span><span class="sxs-lookup"><span data-stu-id="4c2c1-104">The table below lists the counters that this object contains.</span></span>  
  
 <span data-ttu-id="4c2c1-105">下表包含 **SQLAgent:JobSteps** 計數器。</span><span class="sxs-lookup"><span data-stu-id="4c2c1-105">The table below contains the **SQLAgent:JobSteps** counters.</span></span>  
  
|<span data-ttu-id="4c2c1-106">Name</span><span class="sxs-lookup"><span data-stu-id="4c2c1-106">Name</span></span>|<span data-ttu-id="4c2c1-107">描述</span><span class="sxs-lookup"><span data-stu-id="4c2c1-107">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="4c2c1-108">**Active steps**</span><span class="sxs-lookup"><span data-stu-id="4c2c1-108">**Active steps**</span></span>|<span data-ttu-id="4c2c1-109">此計數器會報告目前在執行中的作業步驟數目。</span><span class="sxs-lookup"><span data-stu-id="4c2c1-109">This counter reports the number of job steps currently running.</span></span>|  
|<span data-ttu-id="4c2c1-110">**Queued steps**</span><span class="sxs-lookup"><span data-stu-id="4c2c1-110">**Queued steps**</span></span>|<span data-ttu-id="4c2c1-111">此計數器會報告準備供 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 執行，但尚未開始執行的作業步驟數目。</span><span class="sxs-lookup"><span data-stu-id="4c2c1-111">This counter reports the number of job steps that are ready for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent to run, but which have not yet started running.</span></span>|  
|<span data-ttu-id="4c2c1-112">**Total step retries**</span><span class="sxs-lookup"><span data-stu-id="4c2c1-112">**Total step retries**</span></span>|<span data-ttu-id="4c2c1-113">此計數器會報告自從伺服器上次重新啟動之後，[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 重試作業步驟的總次數。</span><span class="sxs-lookup"><span data-stu-id="4c2c1-113">This counter reports the total number of times that [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] has retried a job step since the last server restart.</span></span>|  
  
 <span data-ttu-id="4c2c1-114">物件中的每個計數器均包含下列執行個體：</span><span class="sxs-lookup"><span data-stu-id="4c2c1-114">Each counter in the object contains the following instances:</span></span>  
  
|<span data-ttu-id="4c2c1-115">執行個體</span><span class="sxs-lookup"><span data-stu-id="4c2c1-115">Instance</span></span>|<span data-ttu-id="4c2c1-116">描述</span><span class="sxs-lookup"><span data-stu-id="4c2c1-116">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="4c2c1-117">**_Total**</span><span class="sxs-lookup"><span data-stu-id="4c2c1-117">**_Total**</span></span>|<span data-ttu-id="4c2c1-118">所有作業步驟的資訊。</span><span class="sxs-lookup"><span data-stu-id="4c2c1-118">Information for all job steps.</span></span>|  
|<span data-ttu-id="4c2c1-119">**ActiveScripting**</span><span class="sxs-lookup"><span data-stu-id="4c2c1-119">**ActiveScripting**</span></span>|<span data-ttu-id="4c2c1-120">使用 **ActiveScripting** 子系統之作業步驟的資訊。</span><span class="sxs-lookup"><span data-stu-id="4c2c1-120">Information for job steps that use the **ActiveScripting** subsystem.</span></span>|  
|<span data-ttu-id="4c2c1-121">**ANALYSISCOMMAND**</span><span class="sxs-lookup"><span data-stu-id="4c2c1-121">**ANALYSISCOMMAND**</span></span>|<span data-ttu-id="4c2c1-122">使用 ANALYSISCOMMAND 子系統之作業步驟的資訊。</span><span class="sxs-lookup"><span data-stu-id="4c2c1-122">Information for job steps that use the ANALYSISCOMMAND subsystem.</span></span>|  
|<span data-ttu-id="4c2c1-123">**ANALYSISQUERY**</span><span class="sxs-lookup"><span data-stu-id="4c2c1-123">**ANALYSISQUERY**</span></span>|<span data-ttu-id="4c2c1-124">使用 ANALYSISQUERY 子系統之作業步驟的資訊。</span><span class="sxs-lookup"><span data-stu-id="4c2c1-124">Information for job steps that use the ANALYSISQUERY subsystem.</span></span>|  
|<span data-ttu-id="4c2c1-125">**CmdExec**</span><span class="sxs-lookup"><span data-stu-id="4c2c1-125">**CmdExec**</span></span>|<span data-ttu-id="4c2c1-126">使用 **CmdExec** 子系統之作業步驟的資訊。</span><span class="sxs-lookup"><span data-stu-id="4c2c1-126">Information for job steps that use the **CmdExec** subsystem.</span></span>|  
|<span data-ttu-id="4c2c1-127">**Distribution**</span><span class="sxs-lookup"><span data-stu-id="4c2c1-127">**Distribution**</span></span>|<span data-ttu-id="4c2c1-128">使用 **Distribution** 子系統之作業步驟的資訊。</span><span class="sxs-lookup"><span data-stu-id="4c2c1-128">Information for job steps that use the **Distribution** subsystem.</span></span>|  
|<span data-ttu-id="4c2c1-129">**Dts**</span><span class="sxs-lookup"><span data-stu-id="4c2c1-129">**Dts**</span></span>|<span data-ttu-id="4c2c1-130">使用 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 子系統之作業步驟的資訊。</span><span class="sxs-lookup"><span data-stu-id="4c2c1-130">Information for job steps that use the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] subsystem.</span></span>|  
|<span data-ttu-id="4c2c1-131">**LogReader**</span><span class="sxs-lookup"><span data-stu-id="4c2c1-131">**LogReader**</span></span>|<span data-ttu-id="4c2c1-132">使用 **LogReader** 子系統之作業步驟的資訊。</span><span class="sxs-lookup"><span data-stu-id="4c2c1-132">Information for job steps that use the **LogReader** subsystem.</span></span>|  
|<span data-ttu-id="4c2c1-133">**合併式**</span><span class="sxs-lookup"><span data-stu-id="4c2c1-133">**Merge**</span></span>|<span data-ttu-id="4c2c1-134">使用 **Merge** 子系統之作業步驟的資訊。</span><span class="sxs-lookup"><span data-stu-id="4c2c1-134">Information for job steps that use the **Merge** subsystem.</span></span>|  
|<span data-ttu-id="4c2c1-135">**PowerShell**</span><span class="sxs-lookup"><span data-stu-id="4c2c1-135">**PowerShell**</span></span>|<span data-ttu-id="4c2c1-136">使用 **PowerShell** 子系統之作業步驟的資訊。</span><span class="sxs-lookup"><span data-stu-id="4c2c1-136">Information for job steps that use the **PowerShell** subsystem.</span></span>|  
|<span data-ttu-id="4c2c1-137">**QueueReader**</span><span class="sxs-lookup"><span data-stu-id="4c2c1-137">**QueueReader**</span></span>|<span data-ttu-id="4c2c1-138">使用 **QueueReader** 子系統之作業步驟的資訊。</span><span class="sxs-lookup"><span data-stu-id="4c2c1-138">Information for job steps that use the **QueueReader** subsystem.</span></span>|  
|<span data-ttu-id="4c2c1-139">**快照式**</span><span class="sxs-lookup"><span data-stu-id="4c2c1-139">**Snapshot**</span></span>|<span data-ttu-id="4c2c1-140">使用 **Snapshot** 子系統之作業步驟的資訊。</span><span class="sxs-lookup"><span data-stu-id="4c2c1-140">Information for job steps that use the **Snapshot** subsystem.</span></span>|  
|<span data-ttu-id="4c2c1-141">**TSQL**</span><span class="sxs-lookup"><span data-stu-id="4c2c1-141">**TSQL**</span></span>|<span data-ttu-id="4c2c1-142">執行 [!INCLUDE[tsql](../../includes/tsql-md.md)]之作業步驟的資訊。</span><span class="sxs-lookup"><span data-stu-id="4c2c1-142">Information for job steps that execute [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4c2c1-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4c2c1-143">See Also</span></span>  
 <span data-ttu-id="4c2c1-144">[管理作業步驟](../../ssms/agent/manage-job-steps.md) </span><span class="sxs-lookup"><span data-stu-id="4c2c1-144">[Manage Job Steps](../../ssms/agent/manage-job-steps.md) </span></span>  
 <span data-ttu-id="4c2c1-145">[使用效能物件](../../ssms/agent/use-performance-objects.md) </span><span class="sxs-lookup"><span data-stu-id="4c2c1-145">[Use Performance Objects](../../ssms/agent/use-performance-objects.md) </span></span>  
 [<span data-ttu-id="4c2c1-146">監視資源使用狀況 &#40;System Monitor&#41;</span><span class="sxs-lookup"><span data-stu-id="4c2c1-146">Monitor Resource Usage &#40;System Monitor&#41;</span></span>](monitor-resource-usage-system-monitor.md)  
  
  
