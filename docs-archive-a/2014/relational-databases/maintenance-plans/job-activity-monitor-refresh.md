---
title: 作業活動監視器重新整理 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql12.swb.jobactivitymon.refresh.f1
ms.assetid: 413a368e-fd2b-4e1f-b370-002cdbc85bab
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 5f290825f8a776c954ef802b184f7600aea5dc9d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595978"
---
# <a name="job-activity-monitor-refresh"></a><span data-ttu-id="673fa-102">作業活動監視器重新整理</span><span class="sxs-lookup"><span data-stu-id="673fa-102">Job Activity Monitor Refresh</span></span>
  <span data-ttu-id="673fa-103">使用 **[重新整理設定]** 對話方塊，設定作業活動監視器取得有關伺服器活動新資訊的頻率。</span><span class="sxs-lookup"><span data-stu-id="673fa-103">Use the **Refresh Settings** dialog box to configure how often Job Activity Monitor obtains new information about server activity.</span></span> <span data-ttu-id="673fa-104">作業活動監視器必須在監視的伺服器上執行查詢，以取得作業活動監視器方格的資訊。</span><span class="sxs-lookup"><span data-stu-id="673fa-104">Job Activity Monitor must run queries on the monitored server to obtain information for the Job Activity Monitor grid.</span></span> <span data-ttu-id="673fa-105">自動重新整理間隔的設定小於 30 秒時，用來執行這些查詢的時間就會影響伺服器效能。</span><span class="sxs-lookup"><span data-stu-id="673fa-105">When the auto-refresh interval is set to less than 30 seconds, the time used to run these queries can affect server performance.</span></span>  
  
 <span data-ttu-id="673fa-106">若要開啟此對話方塊，請在作業活動監視器的 **[狀態]** 區段中按一下 **[檢視重新整理設定]** 。</span><span class="sxs-lookup"><span data-stu-id="673fa-106">To open this dialog, click **View refresh settings**, in the **Status** section of Job Activity Monitor.</span></span>  
  
## <a name="options"></a><span data-ttu-id="673fa-107">選項。</span><span class="sxs-lookup"><span data-stu-id="673fa-107">Options</span></span>  
 <span data-ttu-id="673fa-108">**自動重新整理間隔**</span><span class="sxs-lookup"><span data-stu-id="673fa-108">**Auto-refresh every**</span></span>  
 <span data-ttu-id="673fa-109">勾選即可起始活動監視器資訊的自動重新整理功能。</span><span class="sxs-lookup"><span data-stu-id="673fa-109">Check to initiate automatic refreshing of Activity Monitor information.</span></span> <span data-ttu-id="673fa-110">依預設，此功能是關閉的。</span><span class="sxs-lookup"><span data-stu-id="673fa-110">This is off by default.</span></span>  
  
 <span data-ttu-id="673fa-111">**seconds**</span><span class="sxs-lookup"><span data-stu-id="673fa-111">**seconds**</span></span>  
 <span data-ttu-id="673fa-112">嘗試進行自動重新整理的間隔秒數。</span><span class="sxs-lookup"><span data-stu-id="673fa-112">The number of seconds between auto-refresh attempts.</span></span> <span data-ttu-id="673fa-113">預設值是 60 秒。</span><span class="sxs-lookup"><span data-stu-id="673fa-113">Defaults to 60 seconds.</span></span> <span data-ttu-id="673fa-114">值設定為 5 或小於 5 時，表示每隔 5 秒進行重新整理。</span><span class="sxs-lookup"><span data-stu-id="673fa-114">Refreshes every 5 seconds when set to 5 or less.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="673fa-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="673fa-115">See Also</span></span>  
 [<span data-ttu-id="673fa-116">監視作業活動</span><span class="sxs-lookup"><span data-stu-id="673fa-116">Monitor Job Activity</span></span>](../../ssms/agent/monitor-job-activity.md)  
  
  
