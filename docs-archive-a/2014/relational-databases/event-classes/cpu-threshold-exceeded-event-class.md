---
title: CPU Threshold Exceeded 事件類別 | Microsoft 文件
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- CPU Threshold Exceeded Event Class
ms.assetid: eb106f7d-baa3-4a2b-96b2-f9fe0844057d
author: stevestein
ms.author: sstein
ms.openlocfilehash: 07b51e1a6f08f48c601b00d2dcb67bc6d09006f6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592054"
---
# <a name="cpu-threshold-exceeded-event-class"></a><span data-ttu-id="4c6f8-102">CPU Threshold Exceeded 事件類別</span><span class="sxs-lookup"><span data-stu-id="4c6f8-102">CPU Threshold Exceeded Event Class</span></span>
  <span data-ttu-id="4c6f8-103">CPU Threshold Exceeded 事件類別會指出資源管理員偵測到某個查詢已經超過針對 REQUEST_MAX_CPU_TIME_SEC 所指定的 CPU 臨界值。</span><span class="sxs-lookup"><span data-stu-id="4c6f8-103">The CPU Threshold Exceeded event class indicates that Resource Governor detects a query that exceeds the CPU threshold specified for REQUEST_MAX_CPU_TIME_SEC.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4c6f8-104">這個事件的偵測間隔為五秒。</span><span class="sxs-lookup"><span data-stu-id="4c6f8-104">The detection interval for this event is five seconds.</span></span> <span data-ttu-id="4c6f8-105">這樣會保證如果某個查詢超過指定的限制至少達五秒，就會產生事件。</span><span class="sxs-lookup"><span data-stu-id="4c6f8-105">It is guaranteed that an event will be generated if a query exceeds the specified limit by at least five seconds.</span></span> <span data-ttu-id="4c6f8-106">不過，如果某個查詢超過指定的臨界值少於五秒，根據查詢的時間和上一次偵測清除的時間，可能會遺漏偵測。</span><span class="sxs-lookup"><span data-stu-id="4c6f8-106">However, if a query exceeds the specified threshold by less than five seconds, its detection might be missed depending on the timing of the query and the time of last detection sweep.</span></span>  
  
## <a name="cpu-threshold-exceeded-data-columns"></a><span data-ttu-id="4c6f8-107">CPU Threshold Exceeded 資料行</span><span class="sxs-lookup"><span data-stu-id="4c6f8-107">CPU Threshold Exceeded Data Columns</span></span>  
  
|<span data-ttu-id="4c6f8-108">資料行名稱</span><span class="sxs-lookup"><span data-stu-id="4c6f8-108">Data column name</span></span>|<span data-ttu-id="4c6f8-109">資料類型</span><span class="sxs-lookup"><span data-stu-id="4c6f8-109">Data type</span></span>|<span data-ttu-id="4c6f8-110">描述</span><span class="sxs-lookup"><span data-stu-id="4c6f8-110">Description</span></span>|<span data-ttu-id="4c6f8-111">資料行識別碼</span><span class="sxs-lookup"><span data-stu-id="4c6f8-111">Column ID</span></span>|<span data-ttu-id="4c6f8-112">可篩選</span><span class="sxs-lookup"><span data-stu-id="4c6f8-112">Filterable</span></span>|  
|----------------------|---------------|-----------------|---------------|----------------|  
|<span data-ttu-id="4c6f8-113">CPU</span><span class="sxs-lookup"><span data-stu-id="4c6f8-113">CPU</span></span>|`int`|<span data-ttu-id="4c6f8-114">CPU 使用量 (以毫秒為單位)。</span><span class="sxs-lookup"><span data-stu-id="4c6f8-114">CPU usage in milliseconds.</span></span>|<span data-ttu-id="4c6f8-115">18</span><span class="sxs-lookup"><span data-stu-id="4c6f8-115">18</span></span>|<span data-ttu-id="4c6f8-116">是</span><span class="sxs-lookup"><span data-stu-id="4c6f8-116">Yes</span></span>|  
|<span data-ttu-id="4c6f8-117">EventClass</span><span class="sxs-lookup"><span data-stu-id="4c6f8-117">EventClass</span></span>|`int`|<span data-ttu-id="4c6f8-118">214</span><span class="sxs-lookup"><span data-stu-id="4c6f8-118">214</span></span>|<span data-ttu-id="4c6f8-119">27</span><span class="sxs-lookup"><span data-stu-id="4c6f8-119">27</span></span>|<span data-ttu-id="4c6f8-120">否</span><span class="sxs-lookup"><span data-stu-id="4c6f8-120">No</span></span>|  
|<span data-ttu-id="4c6f8-121">EventSubClass</span><span class="sxs-lookup"><span data-stu-id="4c6f8-121">EventSubClass</span></span>|`int`|<span data-ttu-id="4c6f8-122">CPU 限制違規。</span><span class="sxs-lookup"><span data-stu-id="4c6f8-122">CPU limit violation.</span></span>|<span data-ttu-id="4c6f8-123">21</span><span class="sxs-lookup"><span data-stu-id="4c6f8-123">21</span></span>|<span data-ttu-id="4c6f8-124">是</span><span class="sxs-lookup"><span data-stu-id="4c6f8-124">Yes</span></span>|  
|<span data-ttu-id="4c6f8-125">GroupID</span><span class="sxs-lookup"><span data-stu-id="4c6f8-125">GroupID</span></span>|`int`|<span data-ttu-id="4c6f8-126">發生違規的群組識別碼。</span><span class="sxs-lookup"><span data-stu-id="4c6f8-126">Group ID where the violation occurred.</span></span>|<span data-ttu-id="4c6f8-127">66</span><span class="sxs-lookup"><span data-stu-id="4c6f8-127">66</span></span>|<span data-ttu-id="4c6f8-128">是</span><span class="sxs-lookup"><span data-stu-id="4c6f8-128">Yes</span></span>|  
|<span data-ttu-id="4c6f8-129">OwnerID</span><span class="sxs-lookup"><span data-stu-id="4c6f8-129">OwnerID</span></span>|`int`|<span data-ttu-id="4c6f8-130">導致違規之處理序的 SPID。</span><span class="sxs-lookup"><span data-stu-id="4c6f8-130">SPID of the process that caused the violation.</span></span>|<span data-ttu-id="4c6f8-131">58</span><span class="sxs-lookup"><span data-stu-id="4c6f8-131">58</span></span>|<span data-ttu-id="4c6f8-132">是</span><span class="sxs-lookup"><span data-stu-id="4c6f8-132">Yes</span></span>|  
|<span data-ttu-id="4c6f8-133">SPID</span><span class="sxs-lookup"><span data-stu-id="4c6f8-133">SPID</span></span>|`int`|<span data-ttu-id="4c6f8-134">引發此事件之伺服器處理序的識別碼。</span><span class="sxs-lookup"><span data-stu-id="4c6f8-134">ID of the server process that fires this event.</span></span><br /><br /> <span data-ttu-id="4c6f8-135">注意：如果系統執行緒將 CPU 使用量驗證為背景工作，這個識別碼可能會與實際的使用者 SPID 不同。</span><span class="sxs-lookup"><span data-stu-id="4c6f8-135">Note: This can differ from the actual user SPID if a system thread validates CPU usage as a background task.</span></span>|<span data-ttu-id="4c6f8-136">12</span><span class="sxs-lookup"><span data-stu-id="4c6f8-136">12</span></span>|<span data-ttu-id="4c6f8-137">是</span><span class="sxs-lookup"><span data-stu-id="4c6f8-137">Yes</span></span>|  
|<span data-ttu-id="4c6f8-138">StartTime</span><span class="sxs-lookup"><span data-stu-id="4c6f8-138">StartTime</span></span>|`datetime`|<span data-ttu-id="4c6f8-139">引發此事件的時間。</span><span class="sxs-lookup"><span data-stu-id="4c6f8-139">The time when this event fired.</span></span>|<span data-ttu-id="4c6f8-140">14</span><span class="sxs-lookup"><span data-stu-id="4c6f8-140">14</span></span>|<span data-ttu-id="4c6f8-141">是</span><span class="sxs-lookup"><span data-stu-id="4c6f8-141">Yes</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4c6f8-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4c6f8-142">See Also</span></span>  
 [<span data-ttu-id="4c6f8-143">sp_trace_setevent &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="4c6f8-143">sp_trace_setevent &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)  
  
  
