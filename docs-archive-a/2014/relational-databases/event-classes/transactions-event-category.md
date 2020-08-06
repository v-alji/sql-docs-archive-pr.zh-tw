---
title: Transactions 事件類別 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- SQL Server event classes, Transactions event category
- event classes [SQL Server], Transactions event category
- Transactions event category [SQL Server]
ms.assetid: bfc75c5b-7115-49d8-9148-a0c84ee66a9a
author: stevestein
ms.author: sstein
ms.openlocfilehash: 3b68a91fb166797c220cb0c4f5cf2607ca267538
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598412"
---
# <a name="transactions-event-category"></a><span data-ttu-id="a4da8-102">Transaction 事件類別目錄</span><span class="sxs-lookup"><span data-stu-id="a4da8-102">Transactions Event Category</span></span>
  <span data-ttu-id="a4da8-103">**Transactions** 事件類別可以用來監視交易狀態。</span><span class="sxs-lookup"><span data-stu-id="a4da8-103">The **Transactions** event classes can be used to monitor the status of transactions.</span></span> <span data-ttu-id="a4da8-104">以 **TM:** 作為前置詞的事件類別名稱是用來追蹤與交易相關的作業，這些作業是透過交易管理介面來傳送。</span><span class="sxs-lookup"><span data-stu-id="a4da8-104">The event class names that are prefixed with **TM:** are used to track the transaction-related operations that are sent through the transaction management interface.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a4da8-105">本節內容</span><span class="sxs-lookup"><span data-stu-id="a4da8-105">In This Section</span></span>  
  
|<span data-ttu-id="a4da8-106">主題</span><span class="sxs-lookup"><span data-stu-id="a4da8-106">Topic</span></span>|<span data-ttu-id="a4da8-107">描述</span><span class="sxs-lookup"><span data-stu-id="a4da8-107">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="a4da8-108">DTCTransaction 事件類別</span><span class="sxs-lookup"><span data-stu-id="a4da8-108">DTCTransaction Event Class</span></span>](dtctransaction-event-class.md)|<span data-ttu-id="a4da8-109">追蹤 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 分散式交易協調器 (MS DTC) 所協調的交易。</span><span class="sxs-lookup"><span data-stu-id="a4da8-109">Tracks transactions coordinated by the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Distributed Transaction Coordinator (MS DTC).</span></span> <span data-ttu-id="a4da8-110">這些是散發於 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]的二或多個資料庫或執行個體之間的交易。</span><span class="sxs-lookup"><span data-stu-id="a4da8-110">These are transactions distributed between two or more databases or instances of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].</span></span>|  
|[<span data-ttu-id="a4da8-111">SQLTransaction 事件類別</span><span class="sxs-lookup"><span data-stu-id="a4da8-111">SQLTransaction Event Class</span></span>](sqltransaction-event-class.md)|<span data-ttu-id="a4da8-112">追蹤 [!INCLUDE[tsql](../../includes/tsql-md.md)] BEGIN TRAN、COMMIT TRAN、SAVE TRAN 與 ROLLBACK TRAN 陳述式。</span><span class="sxs-lookup"><span data-stu-id="a4da8-112">Tracks [!INCLUDE[tsql](../../includes/tsql-md.md)] BEGIN TRAN, COMMIT TRAN, SAVE TRAN, and ROLLBACK TRAN statements.</span></span>|  
|[<span data-ttu-id="a4da8-113">TM: Begin Tran Completed 事件類別</span><span class="sxs-lookup"><span data-stu-id="a4da8-113">TM: Begin Tran Completed Event Class</span></span>](tm-begin-tran-completed-event-class.md)|<span data-ttu-id="a4da8-114">表示已完成 BEGIN TRANSACTION 要求。</span><span class="sxs-lookup"><span data-stu-id="a4da8-114">Indicates that a BEGIN TRANSACTION request has completed.</span></span>|  
|[<span data-ttu-id="a4da8-115">TM: Begin Tran Starting 事件類別</span><span class="sxs-lookup"><span data-stu-id="a4da8-115">TM: Begin Tran Starting Event Class</span></span>](tm-begin-tran-starting-event-class.md)|<span data-ttu-id="a4da8-116">表示正在啟動 BEGIN TRANSACTION 要求。</span><span class="sxs-lookup"><span data-stu-id="a4da8-116">Indicates that a BEGIN TRANSACTION request is starting.</span></span>|  
|[<span data-ttu-id="a4da8-117">TM: Commit Tran Completed 事件類別</span><span class="sxs-lookup"><span data-stu-id="a4da8-117">TM: Commit Tran Completed Event Class</span></span>](tm-commit-tran-completed-event-class.md)|<span data-ttu-id="a4da8-118">表示已完成 COMMIT TRANSACTION 要求。</span><span class="sxs-lookup"><span data-stu-id="a4da8-118">Indicates that a COMMIT TRANSACTION request has completed.</span></span>|  
|[<span data-ttu-id="a4da8-119">TM: Commit Tran Starting 事件類別</span><span class="sxs-lookup"><span data-stu-id="a4da8-119">TM: Commit Tran Starting Event Class</span></span>](tm-commit-tran-starting-event-class.md)|<span data-ttu-id="a4da8-120">表示正在啟動 COMMIT TRANSACTION 要求。</span><span class="sxs-lookup"><span data-stu-id="a4da8-120">Indicates that a COMMIT TRANSACTION request is starting.</span></span>|  
|[<span data-ttu-id="a4da8-121">TM: Promote Tran Completed 事件類別</span><span class="sxs-lookup"><span data-stu-id="a4da8-121">TM: Promote Tran Completed Event Class</span></span>](tm-promote-tran-completed-event-class.md)|<span data-ttu-id="a4da8-122">表示已完成 PROMOTE TRANSACTION 要求。</span><span class="sxs-lookup"><span data-stu-id="a4da8-122">Indicates that a PROMOTE TRANSACTION request has completed.</span></span>|  
|[<span data-ttu-id="a4da8-123">TM: Promote Tran Starting 事件類別</span><span class="sxs-lookup"><span data-stu-id="a4da8-123">TM: Promote Tran Starting Event Class</span></span>](tm-promote-tran-starting-event-class.md)|<span data-ttu-id="a4da8-124">表示正在啟動 PROMOTE TRANSACTION 要求。</span><span class="sxs-lookup"><span data-stu-id="a4da8-124">Indicates that a PROMOTE TRANSACTION request is starting.</span></span>|  
|[<span data-ttu-id="a4da8-125">TM: Rollback Tran Completed 事件類別</span><span class="sxs-lookup"><span data-stu-id="a4da8-125">TM: Rollback Tran Completed Event Class</span></span>](tm-rollback-tran-completed-event-class.md)|<span data-ttu-id="a4da8-126">表示已完成 ROLLBACK TRANSACTION 要求。</span><span class="sxs-lookup"><span data-stu-id="a4da8-126">Indicates that a ROLLBACK TRANSACTION request has completed.</span></span>|  
|[<span data-ttu-id="a4da8-127">TM: Rollback Tran Starting 事件類別</span><span class="sxs-lookup"><span data-stu-id="a4da8-127">TM: Rollback Tran Starting Event Class</span></span>](tm-rollback-tran-starting-event-class.md)|<span data-ttu-id="a4da8-128">表示正在啟動 ROLLBACK TRANSACTION 要求。</span><span class="sxs-lookup"><span data-stu-id="a4da8-128">Indicates that a ROLLBACK TRANSACTION request is starting.</span></span>|  
|[<span data-ttu-id="a4da8-129">TM: Save Tran Completed 事件類別</span><span class="sxs-lookup"><span data-stu-id="a4da8-129">TM: Save Tran Completed Event Class</span></span>](tm-save-tran-completed-event-class.md)|<span data-ttu-id="a4da8-130">表示已完成 SAVE TRANSACTION 要求。</span><span class="sxs-lookup"><span data-stu-id="a4da8-130">Indicates that a SAVE TRANSACTION request has completed.</span></span>|  
|[<span data-ttu-id="a4da8-131">TM: Save Tran Starting 事件類別</span><span class="sxs-lookup"><span data-stu-id="a4da8-131">TM: Save Tran Starting Event Class</span></span>](tm-save-tran-starting-event-class.md)|<span data-ttu-id="a4da8-132">表示正在啟動 SAVE TRANSACTION 要求。</span><span class="sxs-lookup"><span data-stu-id="a4da8-132">Indicates that a SAVE TRANSACTION request is starting.</span></span>|  
|[<span data-ttu-id="a4da8-133">TransactionLog 事件類別</span><span class="sxs-lookup"><span data-stu-id="a4da8-133">TransactionLog Event Class</span></span>](transactionlog-event-class.md)|<span data-ttu-id="a4da8-134">追蹤交易何時寫入資料庫交易記錄檔。</span><span class="sxs-lookup"><span data-stu-id="a4da8-134">Tracks when transactions are written to a database transaction log.</span></span>|  
  
  
