---
title: MSSQL_ENG014152 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG014152 error
ms.assetid: 4215e2b1-cd30-441f-9671-9afc742adf6e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 615b9cf2996653d86c44d6e43a83e01e8287b110
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594501"
---
# <a name="mssql_eng014152"></a><span data-ttu-id="2d1e9-102">MSSQL_ENG014152</span><span class="sxs-lookup"><span data-stu-id="2d1e9-102">MSSQL_ENG014152</span></span>
    
## <a name="message-details"></a><span data-ttu-id="2d1e9-103">訊息詳細資料</span><span class="sxs-lookup"><span data-stu-id="2d1e9-103">Message Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="2d1e9-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="2d1e9-104">Product Name</span></span>|<span data-ttu-id="2d1e9-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="2d1e9-105">SQL Server</span></span>|  
|<span data-ttu-id="2d1e9-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="2d1e9-106">Event ID</span></span>|<span data-ttu-id="2d1e9-107">14152</span><span class="sxs-lookup"><span data-stu-id="2d1e9-107">14152</span></span>|  
|<span data-ttu-id="2d1e9-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="2d1e9-108">Event Source</span></span>|<span data-ttu-id="2d1e9-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="2d1e9-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="2d1e9-110">元件</span><span class="sxs-lookup"><span data-stu-id="2d1e9-110">Component</span></span>|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|<span data-ttu-id="2d1e9-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="2d1e9-111">Symbolic Name</span></span>||  
|<span data-ttu-id="2d1e9-112">訊息文字</span><span class="sxs-lookup"><span data-stu-id="2d1e9-112">Message Text</span></span>|<span data-ttu-id="2d1e9-113">複寫 -%s：代理程式 %s 已排程重試。</span><span class="sxs-lookup"><span data-stu-id="2d1e9-113">Replication-%s: agent %s scheduled for retry.</span></span> <span data-ttu-id="2d1e9-114">%s</span><span class="sxs-lookup"><span data-stu-id="2d1e9-114">%s</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="2d1e9-115">說明</span><span class="sxs-lookup"><span data-stu-id="2d1e9-115">Explanation</span></span>  
 <span data-ttu-id="2d1e9-116">指定的複寫代理程式已經排程重試要求的作業。</span><span class="sxs-lookup"><span data-stu-id="2d1e9-116">The specified replication agent has been scheduled to retry the requested operation.</span></span> <span data-ttu-id="2d1e9-117">處理序會繼續重試，直到到達為作業步驟所設定的最大重試嘗試次數。</span><span class="sxs-lookup"><span data-stu-id="2d1e9-117">The process continues to retry until it reaches the configured maximum number of retry attempts for the job step.</span></span>  
  
 <span data-ttu-id="2d1e9-118">重試通常是因為下列其中一個原因而發生：</span><span class="sxs-lookup"><span data-stu-id="2d1e9-118">A retry typically occurs because of one of the following reasons:</span></span>  
  
-   <span data-ttu-id="2d1e9-119">已超出 **QueryTimeout** 值。</span><span class="sxs-lookup"><span data-stu-id="2d1e9-119">The **QueryTimeout** value is exceeded.</span></span>  
  
-   <span data-ttu-id="2d1e9-120">已超出 **LoginTimeout** 值。</span><span class="sxs-lookup"><span data-stu-id="2d1e9-120">The **LoginTimeout** value is exceeded.</span></span>  
  
-   <span data-ttu-id="2d1e9-121">複寫處理序已被選擇做為死結的犧牲者。</span><span class="sxs-lookup"><span data-stu-id="2d1e9-121">The replication process was chosen as a deadlock victim.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="2d1e9-122">使用者動作</span><span class="sxs-lookup"><span data-stu-id="2d1e9-122">User Action</span></span>  
 <span data-ttu-id="2d1e9-123">如果重試訊息不頻繁，則不需要任何使用者動作。</span><span class="sxs-lookup"><span data-stu-id="2d1e9-123">If the retry message is infrequent, no user action is required.</span></span>  
  
 <span data-ttu-id="2d1e9-124">使用 [sp_help_jobstep](/sql/relational-databases/system-stored-procedures/sp-help-jobstep-transact-sql) ，檢視要為指定複寫代理程式重試 **Run agent** 步驟的目前最大次數設定。</span><span class="sxs-lookup"><span data-stu-id="2d1e9-124">Use [sp_help_jobstep](/sql/relational-databases/system-stored-procedures/sp-help-jobstep-transact-sql) to view the current setting for the maximum number of times the **Run agent** step for the specified replication agent will retry.</span></span> <span data-ttu-id="2d1e9-125">您可以使用 **@retry_attempts** [sp_update_jobstep](/sql/relational-databases/system-stored-procedures/sp-update-jobstep-transact-sql)預存程式的參數來調整作業步驟重試的次數。</span><span class="sxs-lookup"><span data-stu-id="2d1e9-125">You can use the **@retry_attempts** parameter of the [sp_update_jobstep](/sql/relational-databases/system-stored-procedures/sp-update-jobstep-transact-sql) stored procedure to adjust the number of times a job step retries.</span></span>  
  
 <span data-ttu-id="2d1e9-126">如果重試訊息經常重複出現，請根據導致重試的訊息對此問題進行疑難排解。</span><span class="sxs-lookup"><span data-stu-id="2d1e9-126">If the retry message recurs frequently, troubleshoot the issue based on the message that is causing the retry.</span></span> <span data-ttu-id="2d1e9-127">請檢查代理程式的訊息記錄，找出必須排程進行重試的原因。</span><span class="sxs-lookup"><span data-stu-id="2d1e9-127">Check the agent's history for messages that indicate why the retry had to be scheduled.</span></span> <span data-ttu-id="2d1e9-128">在某些情況下，您可能必須為複寫代理程式啟用更詳細的記錄。</span><span class="sxs-lookup"><span data-stu-id="2d1e9-128">In some cases you may have to enable more detailed logging for your replication agent.</span></span> <span data-ttu-id="2d1e9-129">如需有關如何設定複寫記錄的詳細資訊，請參閱 Microsoft 知識庫文件 [312292](https://support.microsoft.com/kb/312292)。</span><span class="sxs-lookup"><span data-stu-id="2d1e9-129">For more information about how to configure logging for replication, see the Microsoft Knowledge Base article [312292](https://support.microsoft.com/kb/312292).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d1e9-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2d1e9-130">See Also</span></span>  
 [<span data-ttu-id="2d1e9-131">錯誤和事件參考 &#40;複寫&#41;</span><span class="sxs-lookup"><span data-stu-id="2d1e9-131">Errors and Events Reference &#40;Replication&#41;</span></span>](errors-and-events-reference-replication.md)  
  
  
