---
title: MSSQLSERVER_9004 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 9004 (Database Engine error)
ms.assetid: b528bb49-340c-4a81-9c8d-cefce6562f16
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 910665b4349e5b13c5abb4fd687dcf0c6fc122cc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595044"
---
# <a name="mssqlserver_9004"></a><span data-ttu-id="53d4d-102">MSSQLSERVER_9004</span><span class="sxs-lookup"><span data-stu-id="53d4d-102">MSSQLSERVER_9004</span></span>
    
## <a name="details"></a><span data-ttu-id="53d4d-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="53d4d-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="53d4d-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="53d4d-104">Product Name</span></span>|<span data-ttu-id="53d4d-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="53d4d-105">SQL Server</span></span>|  
|<span data-ttu-id="53d4d-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="53d4d-106">Event ID</span></span>|<span data-ttu-id="53d4d-107">9004</span><span class="sxs-lookup"><span data-stu-id="53d4d-107">9004</span></span>|  
|<span data-ttu-id="53d4d-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="53d4d-108">Event Source</span></span>|<span data-ttu-id="53d4d-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="53d4d-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="53d4d-110">元件</span><span class="sxs-lookup"><span data-stu-id="53d4d-110">Component</span></span>|<span data-ttu-id="53d4d-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="53d4d-111">SQLEngine</span></span>|  
|<span data-ttu-id="53d4d-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="53d4d-112">Symbolic Name</span></span>|<span data-ttu-id="53d4d-113">LOG_CORRUPT</span><span class="sxs-lookup"><span data-stu-id="53d4d-113">LOG_CORRUPT</span></span>|  
|<span data-ttu-id="53d4d-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="53d4d-114">Message Text</span></span>|<span data-ttu-id="53d4d-115">在處理資料庫 '%.\*ls' 的記錄檔時，發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="53d4d-115">An error occurred while processing the log for database '%.\*ls'.</span></span>  <span data-ttu-id="53d4d-116">If possible, restore from backup.</span><span class="sxs-lookup"><span data-stu-id="53d4d-116">If possible, restore from backup.</span></span> <span data-ttu-id="53d4d-117">若備份無法使用，可能需要重建記錄檔。</span><span class="sxs-lookup"><span data-stu-id="53d4d-117">If a backup is not available, it might be necessary to rebuild the log.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="53d4d-118">說明</span><span class="sxs-lookup"><span data-stu-id="53d4d-118">Explanation</span></span>  
 <span data-ttu-id="53d4d-119">在回復、復原或複寫期間處理記錄檔時發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="53d4d-119">An error was encountered while processing the log during rollback, recovery, or replication.</span></span> <span data-ttu-id="53d4d-120">這可能代表作業系統偵測到的錯誤，或是 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 偵測到的內部一致性錯誤。</span><span class="sxs-lookup"><span data-stu-id="53d4d-120">This could indicate an error detected by the operating system-or an internal consistency error detected by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="53d4d-121">使用者動作</span><span class="sxs-lookup"><span data-stu-id="53d4d-121">User Action</span></span>  
 <span data-ttu-id="53d4d-122">您可以執行下列其中一項動作來更正此錯誤：</span><span class="sxs-lookup"><span data-stu-id="53d4d-122">One of the following actions will correct this error:</span></span>  
  
-   <span data-ttu-id="53d4d-123">從備份進行還原。</span><span class="sxs-lookup"><span data-stu-id="53d4d-123">Restore from a backup.</span></span>  
  
-   <span data-ttu-id="53d4d-124">重建記錄檔。</span><span class="sxs-lookup"><span data-stu-id="53d4d-124">Rebuild the log.</span></span>  
  
 <span data-ttu-id="53d4d-125">此外，請檢查系統事件和錯誤記錄檔，以找出可能造成問題的系統內部問題。</span><span class="sxs-lookup"><span data-stu-id="53d4d-125">Also, check system event and error logs to identify issues within the system that may have caused the problem.</span></span>  
  
  
