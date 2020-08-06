---
title: " (SQL Server Profiler) 設定全域追蹤選項 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- global trace options [SQL Server]
ms.assetid: 2854608a-c3c7-4eb8-b567-034bfec4b1a9
author: stevestein
ms.author: sstein
ms.openlocfilehash: 2f0809ae11776e1bddf42c189b86f48689ff4859
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585725"
---
# <a name="set-global-trace-options-sql-server-profiler"></a><span data-ttu-id="8e338-102">設定全域追蹤選項 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="8e338-102">Set Global Trace Options (SQL Server Profiler)</span></span>
  <span data-ttu-id="8e338-103">此主題描述如何設定適用於利用特定 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]執行個體而建立之所有追蹤的選項。</span><span class="sxs-lookup"><span data-stu-id="8e338-103">This topic describes how to set options that apply to all traces that are created with a specific instance of [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span>  
  
### <a name="to-set-global-trace-options"></a><span data-ttu-id="8e338-104">若要設定全域追蹤選項</span><span class="sxs-lookup"><span data-stu-id="8e338-104">To set global trace options</span></span>  
  
1.  <span data-ttu-id="8e338-105">在 **[工具]** 功能表上，按一下 **[選項]** 。</span><span class="sxs-lookup"><span data-stu-id="8e338-105">On the **Tools** menu, click **Options**.</span></span>  
  
2.  <span data-ttu-id="8e338-106">在 [一般選項]  對話方塊中，按一下 [選擇字型]  修改顯示選項，然後按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="8e338-106">In the **General Options**dialog box, click **Choose Font**to modify the display options, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="8e338-107">(選擇性) 選取 **[進行連接後立即啟動追蹤]** 。</span><span class="sxs-lookup"><span data-stu-id="8e338-107">Optionally, select **Start tracing immediately after making connection**.</span></span>  
  
4.  <span data-ttu-id="8e338-108">(選擇性) 選取 **[提供者版本變更時，更新追蹤定義 ]** 。</span><span class="sxs-lookup"><span data-stu-id="8e338-108">Optionally, select **Update trace definition when provider version changes**.</span></span> <span data-ttu-id="8e338-109">建議使用此選項，且預設為已選取此選項。</span><span class="sxs-lookup"><span data-stu-id="8e338-109">This option is recommended and is selected by default.</span></span> <span data-ttu-id="8e338-110">選取此選項時，追蹤定義會自動更新成追蹤執行所在伺服器上的目前版本。</span><span class="sxs-lookup"><span data-stu-id="8e338-110">When this option is selected, the trace definition is automatically updated to the current version of the server where tracing is performed.</span></span>  
  
5.  <span data-ttu-id="8e338-111">(選擇性) 指定伺服器如何管理換用檔案：</span><span class="sxs-lookup"><span data-stu-id="8e338-111">Optionally, specify how the server should manage rollover files:</span></span>  
  
    -   <span data-ttu-id="8e338-112">選取 **[依序載入所有換用檔案，不另外提示 ]** ，以在重新執行期間自動載入換用檔案。</span><span class="sxs-lookup"><span data-stu-id="8e338-112">Select **Load all rollover files in sequence without prompting** to automatically load rollover files during replay.</span></span>  
  
    -   <span data-ttu-id="8e338-113">選取 **[載入換用檔案之前先提示 ]** ，以在重新執行期間控制換用檔案。</span><span class="sxs-lookup"><span data-stu-id="8e338-113">Select **Prompt before loading rollover files** to control rollover files during replay.</span></span>  
  
    -   <span data-ttu-id="8e338-114">選取 **[永不載入後續的換用檔案 ]** ，一次只重新執行一個檔案。</span><span class="sxs-lookup"><span data-stu-id="8e338-114">Select **Never load subsequent rollover files** to replay only one file at a time.</span></span>  
  
6.  <span data-ttu-id="8e338-115">(選擇性) 設定重新執行選項：</span><span class="sxs-lookup"><span data-stu-id="8e338-115">Optionally, set replay options:</span></span>  
  
    -   <span data-ttu-id="8e338-116">[預設重新執行執行緒數目]  控制重新執行期間要使用的處理器執行緒數目。</span><span class="sxs-lookup"><span data-stu-id="8e338-116">**Default number of replay threads** controls the number of processor threads to use during replay.</span></span> <span data-ttu-id="8e338-117">執行緒數目較多可使重新執行更快速完成，但會導致重新執行期間的伺服器效能降低。</span><span class="sxs-lookup"><span data-stu-id="8e338-117">A higher number of threads causes replay to complete faster, but causes server performance to degrade during replay.</span></span> <span data-ttu-id="8e338-118">建議設定是 **4**。</span><span class="sxs-lookup"><span data-stu-id="8e338-118">The recommended setting is **4**.</span></span> <span data-ttu-id="8e338-119">下表列出可用選項：</span><span class="sxs-lookup"><span data-stu-id="8e338-119">The following table lists the available options:</span></span>  
  
        |<span data-ttu-id="8e338-120">值</span><span class="sxs-lookup"><span data-stu-id="8e338-120">Value</span></span>|<span data-ttu-id="8e338-121">描述</span><span class="sxs-lookup"><span data-stu-id="8e338-121">Description</span></span>|  
        |-----------|-----------------|  
        |<span data-ttu-id="8e338-122">**2**</span><span class="sxs-lookup"><span data-stu-id="8e338-122">**2**</span></span>|<span data-ttu-id="8e338-123">最小值。</span><span class="sxs-lookup"><span data-stu-id="8e338-123">Minimum value.</span></span> <span data-ttu-id="8e338-124">使用兩個執行緒重新執行。</span><span class="sxs-lookup"><span data-stu-id="8e338-124">Use two threads to replay.</span></span>|  
        |<span data-ttu-id="8e338-125">**4**</span><span class="sxs-lookup"><span data-stu-id="8e338-125">**4**</span></span>|<span data-ttu-id="8e338-126">預設值。</span><span class="sxs-lookup"><span data-stu-id="8e338-126">Default value.</span></span>|  
        |<span data-ttu-id="8e338-127">**255**</span><span class="sxs-lookup"><span data-stu-id="8e338-127">**255**</span></span>|<span data-ttu-id="8e338-128">最大值。</span><span class="sxs-lookup"><span data-stu-id="8e338-128">Maximum value.</span></span> <span data-ttu-id="8e338-129">設為最大值會影響其他處理緒的效能。</span><span class="sxs-lookup"><span data-stu-id="8e338-129">Setting a maximum value will impede performance for other processes.</span></span>|  
  
    -   <span data-ttu-id="8e338-130">[預設健全狀況監視器等候間隔 (秒)]  設定重新執行的執行緒可封鎖其他處理序的最長時間量 (以秒為單位)。</span><span class="sxs-lookup"><span data-stu-id="8e338-130">**Default health monitor wait interval (sec)** sets the maximum amount of time that a replay thread can block another process in seconds.</span></span> <span data-ttu-id="8e338-131">下表會說明這些值。</span><span class="sxs-lookup"><span data-stu-id="8e338-131">The following table explains the values.</span></span>  
  
        |<span data-ttu-id="8e338-132">值</span><span class="sxs-lookup"><span data-stu-id="8e338-132">Value</span></span>|<span data-ttu-id="8e338-133">描述</span><span class="sxs-lookup"><span data-stu-id="8e338-133">Description</span></span>|  
        |-----------|-----------------|  
        |<span data-ttu-id="8e338-134">**0**</span><span class="sxs-lookup"><span data-stu-id="8e338-134">**0**</span></span>|<span data-ttu-id="8e338-135">最小值。</span><span class="sxs-lookup"><span data-stu-id="8e338-135">Minimum value.</span></span> <span data-ttu-id="8e338-136">設為 **0** 代表 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 永遠不會停止封鎖處理序。</span><span class="sxs-lookup"><span data-stu-id="8e338-136">A setting of **0** means that [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] will never stop a blocking process.</span></span>|  
        |<span data-ttu-id="8e338-137">**3600**</span><span class="sxs-lookup"><span data-stu-id="8e338-137">**3600**</span></span>|<span data-ttu-id="8e338-138">預設值。</span><span class="sxs-lookup"><span data-stu-id="8e338-138">Default value.</span></span> <span data-ttu-id="8e338-139">允許封鎖處理序，封鎖時間不超過 **3600** 秒或一小時。</span><span class="sxs-lookup"><span data-stu-id="8e338-139">Allow blocking processes that do not exceed **3600** seconds, or one hour.</span></span>|  
        |<span data-ttu-id="8e338-140">**86400**</span><span class="sxs-lookup"><span data-stu-id="8e338-140">**86400**</span></span>|<span data-ttu-id="8e338-141">最大值。</span><span class="sxs-lookup"><span data-stu-id="8e338-141">Maximum value.</span></span> <span data-ttu-id="8e338-142">允許封鎖處理序，封鎖時間不超過 **86400** 秒或一天。</span><span class="sxs-lookup"><span data-stu-id="8e338-142">Allow blocking processes that do not exceed **86400** seconds, or one day.</span></span>|  
  
    -   <span data-ttu-id="8e338-143">[預設健全狀況監視器輪詢間隔 (秒)]  設定輪詢重新執行的執行緒是否有封鎖處理序的頻率。</span><span class="sxs-lookup"><span data-stu-id="8e338-143">**Default health monitor poll interval (sec)** sets the frequency to poll replay threads for blocking processes.</span></span> <span data-ttu-id="8e338-144">下表會說明這些值。</span><span class="sxs-lookup"><span data-stu-id="8e338-144">The following table explains the values.</span></span>  
  
        |<span data-ttu-id="8e338-145">值</span><span class="sxs-lookup"><span data-stu-id="8e338-145">Value</span></span>|<span data-ttu-id="8e338-146">描述</span><span class="sxs-lookup"><span data-stu-id="8e338-146">Description</span></span>|  
        |-----------|-----------------|  
        |<span data-ttu-id="8e338-147">**1**</span><span class="sxs-lookup"><span data-stu-id="8e338-147">**1**</span></span>|<span data-ttu-id="8e338-148">最小值。</span><span class="sxs-lookup"><span data-stu-id="8e338-148">Minimum value.</span></span> <span data-ttu-id="8e338-149">設為 **1** 代表 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 會每秒輪詢封鎖處理序一次。</span><span class="sxs-lookup"><span data-stu-id="8e338-149">A setting of **1** means [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] will poll for blocking processes once per second.</span></span>|  
        |<span data-ttu-id="8e338-150">**60**</span><span class="sxs-lookup"><span data-stu-id="8e338-150">**60**</span></span>|<span data-ttu-id="8e338-151">預設值。</span><span class="sxs-lookup"><span data-stu-id="8e338-151">Default value.</span></span> <span data-ttu-id="8e338-152">每分鐘輪詢封鎖處理序一次。</span><span class="sxs-lookup"><span data-stu-id="8e338-152">Poll for blocking processes once per minute.</span></span>|  
        |<span data-ttu-id="8e338-153">**86400**</span><span class="sxs-lookup"><span data-stu-id="8e338-153">**86400**</span></span>|<span data-ttu-id="8e338-154">最大值。</span><span class="sxs-lookup"><span data-stu-id="8e338-154">Maximum value.</span></span> <span data-ttu-id="8e338-155">每 **86400** 秒或每日輪詢封鎖處理序一次。</span><span class="sxs-lookup"><span data-stu-id="8e338-155">Poll for blocking processes once per **86400** seconds, or one day.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8e338-156">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8e338-156">See Also</span></span>  
 <span data-ttu-id="8e338-157">[設定追蹤顯示預設值 &#40;SQL Server Profiler&#41;](sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="8e338-157">[Set Trace Display Defaults &#40;SQL Server Profiler&#41;](sql-server-profiler.md) </span></span>  
 [<span data-ttu-id="8e338-158">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="8e338-158">SQL Server Profiler</span></span>](sql-server-profiler.md)  
  
  
