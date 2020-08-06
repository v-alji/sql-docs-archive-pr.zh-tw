---
title: MSSQLSERVER_844 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 844 (Database Engine error)
ms.assetid: 2060c886-1226-4066-bc0c-de90a1cfb82b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c4870d6e43ec12b49033ea3b5f88fa0d0cdd597a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594574"
---
# <a name="mssqlserver_844"></a><span data-ttu-id="ba53d-102">MSSQLSERVER_844</span><span class="sxs-lookup"><span data-stu-id="ba53d-102">MSSQLSERVER_844</span></span>
    
## <a name="details"></a><span data-ttu-id="ba53d-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="ba53d-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ba53d-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="ba53d-104">Product Name</span></span>|<span data-ttu-id="ba53d-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="ba53d-105">SQL Server</span></span>|  
|<span data-ttu-id="ba53d-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="ba53d-106">Event ID</span></span>|<span data-ttu-id="ba53d-107">844</span><span class="sxs-lookup"><span data-stu-id="ba53d-107">844</span></span>|  
|<span data-ttu-id="ba53d-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="ba53d-108">Event Source</span></span>|<span data-ttu-id="ba53d-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="ba53d-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="ba53d-110">元件</span><span class="sxs-lookup"><span data-stu-id="ba53d-110">Component</span></span>|<span data-ttu-id="ba53d-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="ba53d-111">SQLEngine</span></span>|  
|<span data-ttu-id="ba53d-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="ba53d-112">Symbolic Name</span></span>|<span data-ttu-id="ba53d-113">BUFLATCH_TIMEOUT_CONTINUE</span><span class="sxs-lookup"><span data-stu-id="ba53d-113">BUFLATCH_TIMEOUT_CONTINUE</span></span>|  
|<span data-ttu-id="ba53d-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="ba53d-114">Message Text</span></span>|<span data-ttu-id="ba53d-115">等候緩衝閂時發生逾時 -- 類型 %d，bp %p，頁面 %d:%d，狀態 %#x，資料庫識別碼: %d，配置單位識別碼: %I64d%ls，工作 0x%p : %d，等候時間 %d，旗標 0x%I64x，主控工作 0x%p。</span><span class="sxs-lookup"><span data-stu-id="ba53d-115">Time-out occurred while waiting for buffer latch -- type %d, bp %p, page %d:%d, stat %#x, database id: %d, allocation unit id: %I64d%ls, task 0x%p : %d, waittime %d, flags 0x%I64x, owning task 0x%p.</span></span>  <span data-ttu-id="ba53d-116">繼續等候。</span><span class="sxs-lookup"><span data-stu-id="ba53d-116">Continuing to wait.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="ba53d-117">說明</span><span class="sxs-lookup"><span data-stu-id="ba53d-117">Explanation</span></span>  
 <span data-ttu-id="ba53d-118">處理序正在等候取得閂鎖。</span><span class="sxs-lookup"><span data-stu-id="ba53d-118">A process is waiting to acquire a latch.</span></span> <span data-ttu-id="ba53d-119">造成這個問題的原因可能是由於 I/O 作業花費太多時間才完成。</span><span class="sxs-lookup"><span data-stu-id="ba53d-119">This problem can be caused by an I/O operation taking too long to complete.</span></span> <span data-ttu-id="ba53d-120">這種錯誤通常是其他工作封鎖了系統處理序所造成的結果。</span><span class="sxs-lookup"><span data-stu-id="ba53d-120">Typically this type of error is the result of other tasks blocking system processes.</span></span> <span data-ttu-id="ba53d-121">在某些情況下，這項錯誤可能是硬體故障的結果。</span><span class="sxs-lookup"><span data-stu-id="ba53d-121">In some instances, this error may be the result of hardware failure.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="ba53d-122">使用者動作</span><span class="sxs-lookup"><span data-stu-id="ba53d-122">User Action</span></span>  
 <span data-ttu-id="ba53d-123">請嘗試下列方法，以避免發生這項錯誤：</span><span class="sxs-lookup"><span data-stu-id="ba53d-123">Try the following to prevent this error from occurring:</span></span>  
  
-   <span data-ttu-id="ba53d-124">減少工作負載。</span><span class="sxs-lookup"><span data-stu-id="ba53d-124">Reduce workload.</span></span>  
  
-   <span data-ttu-id="ba53d-125">查看錯誤記錄檔或事件記錄檔中相關聯的 I/O 失敗。</span><span class="sxs-lookup"><span data-stu-id="ba53d-125">Check for associated I/O failures in error log or event log.</span></span> <span data-ttu-id="ba53d-126">I/O 失敗通常表示磁碟功能有問題。</span><span class="sxs-lookup"><span data-stu-id="ba53d-126">I/O failures typically point to a disk malfunction.</span></span>  
  
-   <span data-ttu-id="ba53d-127">查看錯誤記錄檔，找出沒有產量的工作和其他重大錯誤。</span><span class="sxs-lookup"><span data-stu-id="ba53d-127">Check the error log for non-yielding tasks and other critical errors.</span></span>  
  
-   <span data-ttu-id="ba53d-128">如果經常發生諸如判斷提示之類的重大錯誤，請解決這些問題。</span><span class="sxs-lookup"><span data-stu-id="ba53d-128">If critical errors such as asserts frequently occur, resolve these problems.</span></span>  
  
 <span data-ttu-id="ba53d-129">如果持續發生錯誤，請連絡 Microsoft 客戶服務及支援中心。</span><span class="sxs-lookup"><span data-stu-id="ba53d-129">If the error persists, contact Microsoft Customer Service and Support.</span></span>  
  
  
