---
title: MSSQLSERVER_845 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 845 (Database Engine error)
ms.assetid: 8fff6ad4-234c-44be-b123-e25d5e1cd63e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 24bfb8b3758d0656dad96e4af4ed3b94aa51e07f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594570"
---
# <a name="mssqlserver_845"></a><span data-ttu-id="bcffe-102">MSSQLSERVER_845</span><span class="sxs-lookup"><span data-stu-id="bcffe-102">MSSQLSERVER_845</span></span>
    
## <a name="details"></a><span data-ttu-id="bcffe-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="bcffe-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="bcffe-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="bcffe-104">Product Name</span></span>|<span data-ttu-id="bcffe-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="bcffe-105">SQL Server</span></span>|  
|<span data-ttu-id="bcffe-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="bcffe-106">Event ID</span></span>|<span data-ttu-id="bcffe-107">845</span><span class="sxs-lookup"><span data-stu-id="bcffe-107">845</span></span>|  
|<span data-ttu-id="bcffe-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="bcffe-108">Event Source</span></span>|<span data-ttu-id="bcffe-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="bcffe-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="bcffe-110">元件</span><span class="sxs-lookup"><span data-stu-id="bcffe-110">Component</span></span>|<span data-ttu-id="bcffe-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="bcffe-111">SQLEngine</span></span>|  
|<span data-ttu-id="bcffe-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="bcffe-112">Symbolic Name</span></span>|<span data-ttu-id="bcffe-113">BUFLATCH_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="bcffe-113">BUFLATCH_TIMEOUT</span></span>|  
|<span data-ttu-id="bcffe-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="bcffe-114">Message Text</span></span>|<span data-ttu-id="bcffe-115">等候緩衝閂類型 %d (資料庫識別碼 %d，頁面 %S_PGID) 時發生逾時。</span><span class="sxs-lookup"><span data-stu-id="bcffe-115">Time-out occurred while waiting for buffer latch type %d for page %S_PGID, database ID %d.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="bcffe-116">說明</span><span class="sxs-lookup"><span data-stu-id="bcffe-116">Explanation</span></span>  
 <span data-ttu-id="bcffe-117">處理序一直等候要取得閂鎖，但該處理序等候到時間限制過期卻仍無法取得。</span><span class="sxs-lookup"><span data-stu-id="bcffe-117">A process was waiting to acquire a latch, but the process waited until the time limit expired and failed to acquire one.</span></span> <span data-ttu-id="bcffe-118">如果 I/O 作業完成需要花費太長時間 (通常是因為其他工作封鎖了系統處理序)，可能就會發生這種情形。</span><span class="sxs-lookup"><span data-stu-id="bcffe-118">This can occur if an I/O operation takes too long to complete, usually as a result of other tasks blocking system processes.</span></span> <span data-ttu-id="bcffe-119">在某些情況下，這項錯誤可能是硬體故障的結果。</span><span class="sxs-lookup"><span data-stu-id="bcffe-119">In some instances, this error may be the result of hardware failure.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="bcffe-120">使用者動作</span><span class="sxs-lookup"><span data-stu-id="bcffe-120">User Action</span></span>  
 <span data-ttu-id="bcffe-121">執行下列事項或可避免此錯誤發生：</span><span class="sxs-lookup"><span data-stu-id="bcffe-121">Performing the following tasks may prevent this error:</span></span>  
  
-   <span data-ttu-id="bcffe-122">降低工作負載。</span><span class="sxs-lookup"><span data-stu-id="bcffe-122">Reduce the workload.</span></span>  
  
-   <span data-ttu-id="bcffe-123">確認錯誤記錄檔或事件記錄檔中是否有相關聯的 I/O 失敗。</span><span class="sxs-lookup"><span data-stu-id="bcffe-123">Verify whether there are associated I/O failures in the error log or event log.</span></span> <span data-ttu-id="bcffe-124">I/O 失敗通常是因磁碟異常所造成。</span><span class="sxs-lookup"><span data-stu-id="bcffe-124">I/O failures are typically caused by disk malfunction.</span></span>  
  
-   <span data-ttu-id="bcffe-125">查看錯誤記錄檔，找出沒有產量的工作和其他重大錯誤。</span><span class="sxs-lookup"><span data-stu-id="bcffe-125">Check error log for non-yielding tasks and other critical errors.</span></span>  
  
-   <span data-ttu-id="bcffe-126">如果經常發生諸如判斷提示之類的重大錯誤，請解決這些問題。</span><span class="sxs-lookup"><span data-stu-id="bcffe-126">If critical errors such as asserts frequently occur, resolve these problems.</span></span>  
  
 <span data-ttu-id="bcffe-127">如果持續發生錯誤，請連絡 Microsoft 客戶服務及支援中心。</span><span class="sxs-lookup"><span data-stu-id="bcffe-127">If the error persists, contact Microsoft Customer Service and Support.</span></span>  
  
  
