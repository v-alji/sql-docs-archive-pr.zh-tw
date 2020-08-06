---
title: 已封鎖的處理序臨界值伺服器組態選項 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- thresholds [SQL Server]
- blocked process threshold option
ms.assetid: 3d46d143-bc6a-4220-8b55-6baa37547c25
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 9d5b61aaf23a8e74cb11afbf4e8bdb958fde6abe
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705430"
---
# <a name="blocked-process-threshold-server-configuration-option"></a><span data-ttu-id="7c9b2-102">已封鎖的處理序臨界值伺服器組態選項</span><span class="sxs-lookup"><span data-stu-id="7c9b2-102">blocked process threshold Server Configuration Option</span></span>
  <span data-ttu-id="7c9b2-103">使用 **blocked process threshold** 選項，以秒為單位來指定產生已封鎖處理序報表的臨界值。</span><span class="sxs-lookup"><span data-stu-id="7c9b2-103">Use the **blocked process threshold** option to specify the threshold, in seconds, at which blocked process reports are generated.</span></span> <span data-ttu-id="7c9b2-104">此臨界值可設定為 0 到 86,400 的值。</span><span class="sxs-lookup"><span data-stu-id="7c9b2-104">The threshold can be set from 0 to 86,400.</span></span> <span data-ttu-id="7c9b2-105">預設不會針對已封鎖的處理序產生任何報告。</span><span class="sxs-lookup"><span data-stu-id="7c9b2-105">By default, no blocked process reports are produced.</span></span> <span data-ttu-id="7c9b2-106">對於系統工作或在等待不產生可偵測死結的資源的工作，並不會產生此事件。</span><span class="sxs-lookup"><span data-stu-id="7c9b2-106">This event is not generated for system tasks or for tasks that are waiting on resources that do not generate detectable deadlocks.</span></span>  
  
 <span data-ttu-id="7c9b2-107">您可以定義在產生此事件時要執行的 [警示](../../ssms/agent/alerts.md) 。</span><span class="sxs-lookup"><span data-stu-id="7c9b2-107">You can define an [alert](../../ssms/agent/alerts.md) to be executed when this event is generated.</span></span> <span data-ttu-id="7c9b2-108">例如，您可以選擇呼叫管理員，以採取適當的動作來處理此封鎖狀況。</span><span class="sxs-lookup"><span data-stu-id="7c9b2-108">So for example, you can choose to page the administrator to take appropriate action to handle the blocking situation.</span></span>  
  
 <span data-ttu-id="7c9b2-109">封鎖的處理序臨界值使用死結監視背景執行緒，瀏覽等待時間超過設定的臨界值或是臨界值的好幾倍之工作清單。</span><span class="sxs-lookup"><span data-stu-id="7c9b2-109">Blocked process threshold uses the deadlock monitor background thread to walk through the list of tasks waiting for a time greater than or multiples of the configured threshold.</span></span> <span data-ttu-id="7c9b2-110">每隔一段報告時間間隔就會為每個已封鎖的工作產生一次此事件。</span><span class="sxs-lookup"><span data-stu-id="7c9b2-110">The event is generated once per reporting interval for each of the blocked tasks.</span></span>  
  
 <span data-ttu-id="7c9b2-111">封鎖的處理序報表是以最大速率來執行。</span><span class="sxs-lookup"><span data-stu-id="7c9b2-111">The blocked process report is done on a best effort basis.</span></span> <span data-ttu-id="7c9b2-112">不保證即時或甚至接近即時的報告。</span><span class="sxs-lookup"><span data-stu-id="7c9b2-112">There is no guarantee of any real-time or even close to real-time reporting.</span></span>  
  
 <span data-ttu-id="7c9b2-113">設定立即生效，伺服器不必停止再重新啟動。</span><span class="sxs-lookup"><span data-stu-id="7c9b2-113">The setting takes effect immediately without a server stop and restart.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="7c9b2-114">範例</span><span class="sxs-lookup"><span data-stu-id="7c9b2-114">Examples</span></span>  
 <span data-ttu-id="7c9b2-115">下例範例將 `blocked process threshold` 設為 `20` 秒，為每一個封鎖的工作產生封鎖處理序報表。</span><span class="sxs-lookup"><span data-stu-id="7c9b2-115">The following example sets the `blocked process threshold` to `20` seconds, generating a blocked process report for each task that is blocked.</span></span>  
  
```  
sp_configure 'show advanced options', 1 ;  
GO  
RECONFIGURE ;  
GO  
sp_configure 'blocked process threshold', 20 ;  
GO  
RECONFIGURE ;  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="7c9b2-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7c9b2-116">See Also</span></span>  
 <span data-ttu-id="7c9b2-117">[sp_trace_setevent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="7c9b2-117">[sp_trace_setevent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql) </span></span>  
 [<span data-ttu-id="7c9b2-118">Blocked Process Report 事件類別</span><span class="sxs-lookup"><span data-stu-id="7c9b2-118">Blocked Process Report Event Class</span></span>](../../relational-databases/event-classes/blocked-process-report-event-class.md)  
  
  
