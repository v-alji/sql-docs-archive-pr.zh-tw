---
title: MSSQLSERVER_847 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 847 (Database Engine error)
ms.assetid: 67208b7c-bd8d-48a1-9f70-a6488e0f5f9b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 6b2d5c0a35533700606a44867d2a51cf9087e399
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597864"
---
# <a name="mssqlserver_847"></a><span data-ttu-id="871ae-102">MSSQLSERVER_847</span><span class="sxs-lookup"><span data-stu-id="871ae-102">MSSQLSERVER_847</span></span>
    
## <a name="details"></a><span data-ttu-id="871ae-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="871ae-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="871ae-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="871ae-104">Product Name</span></span>|<span data-ttu-id="871ae-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="871ae-105">SQL Server</span></span>|  
|<span data-ttu-id="871ae-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="871ae-106">Event ID</span></span>|<span data-ttu-id="871ae-107">847</span><span class="sxs-lookup"><span data-stu-id="871ae-107">847</span></span>|  
|<span data-ttu-id="871ae-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="871ae-108">Event Source</span></span>|<span data-ttu-id="871ae-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="871ae-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="871ae-110">元件</span><span class="sxs-lookup"><span data-stu-id="871ae-110">Component</span></span>|<span data-ttu-id="871ae-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="871ae-111">SQLEngine</span></span>|  
|<span data-ttu-id="871ae-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="871ae-112">Symbolic Name</span></span>|<span data-ttu-id="871ae-113">N/A</span><span class="sxs-lookup"><span data-stu-id="871ae-113">N/A</span></span>|  
|<span data-ttu-id="871ae-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="871ae-114">Message Text</span></span>|<span data-ttu-id="871ae-115">等候閂鎖時發生逾時: 類別 '%ls'，識別碼 %p，類型 %d，工作 0x%p : %d，等候時間 %d，旗標 0x%I64x，主控工作 0x%p。</span><span class="sxs-lookup"><span data-stu-id="871ae-115">Time-out occurred while waiting for latch: class '%ls', id %p, type %d, Task 0x%p : %d, waittime %d, flags 0x%I64x, owning task 0x%p.</span></span> <span data-ttu-id="871ae-116">繼續等候。</span><span class="sxs-lookup"><span data-stu-id="871ae-116">Continuing to wait.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="871ae-117">說明</span><span class="sxs-lookup"><span data-stu-id="871ae-117">Explanation</span></span>  
 <span data-ttu-id="871ae-118">就在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 將緩衝閂鎖錯誤寫入 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 錯誤記錄檔的同時，電腦可能會停止回應，或者發生逾時或其他例行作業中斷。</span><span class="sxs-lookup"><span data-stu-id="871ae-118">A computer might stop responding, or a time-out or some other disruption of regular operations might occur at the same time that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] writes buffer latch errors to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log.</span></span>  
  
 <span data-ttu-id="871ae-119">如果訊息中的狀態欄位值為 0x04 on，表示 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 正等候 I/O 作業完成。</span><span class="sxs-lookup"><span data-stu-id="871ae-119">If the stat field in the message has the value of 0x04 on, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is waiting for an I/O operation.</span></span> <span data-ttu-id="871ae-120">您可能也會在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 錯誤記錄檔中看到 [MSSQLSERVER_833](mssqlserver-833-database-engine-error.md) 訊息。</span><span class="sxs-lookup"><span data-stu-id="871ae-120">You may also receive message [MSSQLSERVER_833](mssqlserver-833-database-engine-error.md) in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log.</span></span>  
  
 <span data-ttu-id="871ae-121">如果訊息中的狀態欄位值為 0x04 off，意指頁面發生嚴重的競爭問題。</span><span class="sxs-lookup"><span data-stu-id="871ae-121">If the stat field in the message has the value 0x04 off, there is heavy contention for a page.</span></span> <span data-ttu-id="871ae-122">若問題物件是資料頁，起因可能就在於程式碼設計不良。</span><span class="sxs-lookup"><span data-stu-id="871ae-122">If the object is a data page, this can be caused by inefficient code design.</span></span> <span data-ttu-id="871ae-123">反之若非資料頁，則錯誤大致是因伺服器瓶頸所造成，例如硬體資源不足。</span><span class="sxs-lookup"><span data-stu-id="871ae-123">If the page is nondata, the error might be caused by server bottlenecks, such as insufficient hardware resources.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="871ae-124">使用者動作</span><span class="sxs-lookup"><span data-stu-id="871ae-124">User Action</span></span>  
 <span data-ttu-id="871ae-125">若要解決這個問題，請依據您的環境採取下列一個或多個步驟，應可減緩或消除錯誤訊息的出現：</span><span class="sxs-lookup"><span data-stu-id="871ae-125">To work around this problem, depending on your environment, one or more of the following steps might reduce or eliminate the error messages:</span></span>  
  
-   <span data-ttu-id="871ae-126">判斷您的硬體是否有瓶頸。</span><span class="sxs-lookup"><span data-stu-id="871ae-126">Determine whether you have any hardware bottlenecks.</span></span> <span data-ttu-id="871ae-127">若有必要，請升級硬體使其足以支援所處環境的組態、查詢和負載需求。</span><span class="sxs-lookup"><span data-stu-id="871ae-127">If it is necessary, upgrade your hardware so that it can support the configuration, query, and load requirements of your environment.</span></span> <span data-ttu-id="871ae-128">如需瓶頸的詳細資訊，請參閱[找出瓶頸](../performance/identify-bottlenecks.md)。</span><span class="sxs-lookup"><span data-stu-id="871ae-128">For more information about bottlenecks, see [Identify Bottlenecks](../performance/identify-bottlenecks.md).</span></span>  
  
-   <span data-ttu-id="871ae-129">檢查所有記錄的錯誤，據以執行硬體廠商提供的任何診斷事項。</span><span class="sxs-lookup"><span data-stu-id="871ae-129">Check for any logged errors and run any diagnostics provided by your hardware vendor.</span></span>  
  
-   <span data-ttu-id="871ae-130">確定磁碟機並未壓縮。</span><span class="sxs-lookup"><span data-stu-id="871ae-130">Make sure that your disk drives are not compressed.</span></span> <span data-ttu-id="871ae-131">資料檔案和記錄檔不支援儲存在壓縮磁碟機上。</span><span class="sxs-lookup"><span data-stu-id="871ae-131">Storing data or log files on compressed drives is not supported.</span></span> <span data-ttu-id="871ae-132">如需有關檔案和檔案群組的詳細資訊，請參閱[資料庫檔案與檔案群組](../databases/database-files-and-filegroups.md)。</span><span class="sxs-lookup"><span data-stu-id="871ae-132">For more information about physical files, see [Database Files and Filegroups](../databases/database-files-and-filegroups.md).</span></span>  
  
-   <span data-ttu-id="871ae-133">將下列選項設成 off，看看錯誤訊息是否會消失：</span><span class="sxs-lookup"><span data-stu-id="871ae-133">See whether the error messages disappear when you set the following options to off:</span></span>  
  
    -   <span data-ttu-id="871ae-134">SQL Server priority boost 組態選項</span><span class="sxs-lookup"><span data-stu-id="871ae-134">SQL Server priority boost configuration option</span></span>  
  
    -   <span data-ttu-id="871ae-135">輕量型共用 (Fiber 模式) 選項</span><span class="sxs-lookup"><span data-stu-id="871ae-135">Lightweight pooling (fiber mode) option</span></span>  
  
    -   <span data-ttu-id="871ae-136">Set working set size 選項</span><span class="sxs-lookup"><span data-stu-id="871ae-136">Set working set size option</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="871ae-137">上述設定一旦變更而不再是預設值 OFF，通常會造成不利影響。</span><span class="sxs-lookup"><span data-stu-id="871ae-137">The previous settings can frequently be counter-productive if you change them from their default setting of OFF.</span></span> <span data-ttu-id="871ae-138">如需設定的詳細資訊，請參閱[伺服器組態選項 &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="871ae-138">For more information about the settings, see [Server Configuration Options &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md).</span></span>  
  
-   <span data-ttu-id="871ae-139">微調查詢以減少系統資源耗用。</span><span class="sxs-lookup"><span data-stu-id="871ae-139">Tune queries to reduce resources used on the system.</span></span> <span data-ttu-id="871ae-140">效能微調有助於減輕系統負擔，並可縮短個別查詢的回應時間。</span><span class="sxs-lookup"><span data-stu-id="871ae-140">Performance tuning will help reduce the stress on a system and improve response time for individual queries.</span></span>  
  
-   <span data-ttu-id="871ae-141">將 AUTO_SHRINK 選項設成 OFF，以使資料庫大小改變時的負擔降低。</span><span class="sxs-lookup"><span data-stu-id="871ae-141">Set the AUTO_SHRINK option to OFF to reduce the overhead of changes to the database size.</span></span>  
  
-   <span data-ttu-id="871ae-142">確定 FILEGROWTH 選項的設定值夠大，以免遞增次數過於頻繁。</span><span class="sxs-lookup"><span data-stu-id="871ae-142">Make sure that you set the FILEGROWTH option to increments that are large enough to be infrequent.</span></span> <span data-ttu-id="871ae-143">請排程作業於離峰時段檢查資料庫中可用的空間量，再據以增加資料庫大小。</span><span class="sxs-lookup"><span data-stu-id="871ae-143">Schedule a job to check the available space in the databases, and then increase the database size during nonpeak hours.</span></span>  
  
  
