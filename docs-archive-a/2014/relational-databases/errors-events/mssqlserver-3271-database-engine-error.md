---
title: MSSQLSERVER_3271 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 3271 (Database Engine error)
ms.assetid: 21b8de4b-6624-4163-9561-1a6cc8fe3d51
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 56bdb5875dbba3fbe5037a308d713170a9b6f9ea
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595064"
---
# <a name="mssqlserver_3271"></a><span data-ttu-id="6159f-102">MSSQLSERVER_3271</span><span class="sxs-lookup"><span data-stu-id="6159f-102">MSSQLSERVER_3271</span></span>
    
## <a name="details"></a><span data-ttu-id="6159f-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="6159f-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="6159f-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="6159f-104">Product Name</span></span>|<span data-ttu-id="6159f-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="6159f-105">SQL Server</span></span>|  
|<span data-ttu-id="6159f-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="6159f-106">Event ID</span></span>|<span data-ttu-id="6159f-107">3271</span><span class="sxs-lookup"><span data-stu-id="6159f-107">3271</span></span>|  
|<span data-ttu-id="6159f-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="6159f-108">Event Source</span></span>|<span data-ttu-id="6159f-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="6159f-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="6159f-110">元件</span><span class="sxs-lookup"><span data-stu-id="6159f-110">Component</span></span>|<span data-ttu-id="6159f-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="6159f-111">SQLEngine</span></span>|  
|<span data-ttu-id="6159f-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="6159f-112">Symbolic Name</span></span>|<span data-ttu-id="6159f-113">DMPIO_IO_ERROR</span><span class="sxs-lookup"><span data-stu-id="6159f-113">DMPIO_IO_ERROR</span></span>|  
|<span data-ttu-id="6159f-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="6159f-114">Message Text</span></span>|<span data-ttu-id="6159f-115">檔案 "%ls:" %ls 上發生無法復原的 I/O 錯誤。</span><span class="sxs-lookup"><span data-stu-id="6159f-115">A nonrecoverable I/O error occurred on file "%ls:" %ls.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="6159f-116">說明</span><span class="sxs-lookup"><span data-stu-id="6159f-116">Explanation</span></span>  
 <span data-ttu-id="6159f-117">這是作業系統在備份或還原作業期間執行 I/O 時引發錯誤時所發生的一般錯誤。</span><span class="sxs-lookup"><span data-stu-id="6159f-117">This is a general error that occurs when the operating system raises an error while performing I/O during a backup or restore operation.</span></span> <span data-ttu-id="6159f-118">大部分情況下，造成這項錯誤的原因純粹因為備份媒體已滿。</span><span class="sxs-lookup"><span data-stu-id="6159f-118">In most situations the cause is simply that the backup medium is full.</span></span>  
  
 <span data-ttu-id="6159f-119">此錯誤可能包括作業系統指出磁碟已滿的其他文字。</span><span class="sxs-lookup"><span data-stu-id="6159f-119">The error may include additional text from the operating system indicating that the disk is full.</span></span> <span data-ttu-id="6159f-120">以協力廠商軟體執行備份或還原作業時，可能會出現另一則訊息，指出備份已經失敗。</span><span class="sxs-lookup"><span data-stu-id="6159f-120">When performing a backup or restore operation with third-party backup software an additional message may occur indicating that the backup failed.</span></span> <span data-ttu-id="6159f-121">這則訊息看起來可能與下列文字類似：</span><span class="sxs-lookup"><span data-stu-id="6159f-121">The message may look similar to the following text:</span></span>  
  
```  
"2005-08-02 16:05:16.04 spid55 Error: 18210, Severity: 16, State: 1.  
 2005-08-02 16:05:16.04 spid55 BackupVirtualDeviceFile  
::RequestDurableMedia: Flush failure on backup device 'VDINULL'.   
Operating system error 995(The I/O operation has been aborted because   
of either a thread exit or an application request.)."  
```  
  
 <span data-ttu-id="6159f-122">這則訊息代表備份軟體要求您結束備份或還原作業。</span><span class="sxs-lookup"><span data-stu-id="6159f-122">This is an indication that the backup software requested a termination of the backup or restore operation.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="6159f-123">使用者動作</span><span class="sxs-lookup"><span data-stu-id="6159f-123">User Action</span></span>  
 <span data-ttu-id="6159f-124">依照需要執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="6159f-124">Perform the following tasks as appropriate:</span></span>  
  
-   <span data-ttu-id="6159f-125">檢閱這則訊息之前的基本系統錯誤訊息和 SQL Server 錯誤訊息，找出失敗的原因。</span><span class="sxs-lookup"><span data-stu-id="6159f-125">Review the underlying system error messages and SQL Server error messages preceding this one to identify the cause of the failure.</span></span>  
  
-   <span data-ttu-id="6159f-126">確定備份和還原媒體具有足夠的空間。</span><span class="sxs-lookup"><span data-stu-id="6159f-126">Ensure that the backup and restore medium has sufficient space.</span></span>  
  
-   <span data-ttu-id="6159f-127">更正協力廠商備份和還原軟體引發的任何錯誤。</span><span class="sxs-lookup"><span data-stu-id="6159f-127">Correct any errors raised by third-party backup and restore software.</span></span>  
  
  
