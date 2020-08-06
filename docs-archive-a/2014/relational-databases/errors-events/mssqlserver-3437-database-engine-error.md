---
title: MSSQLSERVER_3437 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 3437 (Database Engine error)
ms.assetid: b38216e2-b650-43bd-97af-061d54f60031
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ed8f2050f6f1b38bc5f3fcb7a9700b80e52f2763
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598893"
---
# <a name="mssqlserver_3437"></a><span data-ttu-id="1e182-102">MSSQLSERVER_3437</span><span class="sxs-lookup"><span data-stu-id="1e182-102">MSSQLSERVER_3437</span></span>
    
## <a name="details"></a><span data-ttu-id="1e182-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="1e182-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="1e182-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="1e182-104">Product Name</span></span>|<span data-ttu-id="1e182-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="1e182-105">SQL Server</span></span>|  
|<span data-ttu-id="1e182-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="1e182-106">Event ID</span></span>|<span data-ttu-id="1e182-107">3437</span><span class="sxs-lookup"><span data-stu-id="1e182-107">3437</span></span>|  
|<span data-ttu-id="1e182-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="1e182-108">Event Source</span></span>|<span data-ttu-id="1e182-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="1e182-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="1e182-110">元件</span><span class="sxs-lookup"><span data-stu-id="1e182-110">Component</span></span>|<span data-ttu-id="1e182-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="1e182-111">SQLEngine</span></span>|  
|<span data-ttu-id="1e182-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="1e182-112">Symbolic Name</span></span>|<span data-ttu-id="1e182-113">NODTC</span><span class="sxs-lookup"><span data-stu-id="1e182-113">NODTC</span></span>|  
|<span data-ttu-id="1e182-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="1e182-114">Message Text</span></span>|<span data-ttu-id="1e182-115">復原資料庫 '%.\*ls' 時發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="1e182-115">An error occurred while recovering database '%.\*ls'.</span></span> <span data-ttu-id="1e182-116">無法連接 Microsoft 分散式交易協調器 (MS DTC)，檢查交易 %S_XID 的完成狀態。</span><span class="sxs-lookup"><span data-stu-id="1e182-116">Unable to connect to Microsoft Distributed Transaction Coordinator (MS DTC) to check the completion status of transaction %S_XID.</span></span> <span data-ttu-id="1e182-117">請修正 MS DTC，再次執行復原。</span><span class="sxs-lookup"><span data-stu-id="1e182-117">Fix MS DTC, and run recovery again.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="1e182-118">說明</span><span class="sxs-lookup"><span data-stu-id="1e182-118">Explanation</span></span>  
 <span data-ttu-id="1e182-119">資料庫關閉時，使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 分散式交易協調器 (MS DTC) 的一個或多個分散式交易未完成。</span><span class="sxs-lookup"><span data-stu-id="1e182-119">One or more distributed transactions that were using [!INCLUDE[msCoName](../../includes/msconame-md.md)] Distributed Transaction Coordinator (MS DTC) were incomplete when the database was shut down.</span></span> <span data-ttu-id="1e182-120">此資料庫的復原失敗，因為 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 無法連接 MS DTC 以完成或回復交易。</span><span class="sxs-lookup"><span data-stu-id="1e182-120">Recovery of this database failed because [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] cannot connect to MS DTC to complete or roll back the transactions.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="1e182-121">使用者動作</span><span class="sxs-lookup"><span data-stu-id="1e182-121">User Action</span></span>  
 <span data-ttu-id="1e182-122">若要復原此資料庫，您必須先解決 MS DTC 的問題。</span><span class="sxs-lookup"><span data-stu-id="1e182-122">To recover this database, you must first resolve the problem with MS DTC.</span></span> <span data-ttu-id="1e182-123">若要調查 MS DTC 的問題，請檢查 Windows 事件記錄檔。</span><span class="sxs-lookup"><span data-stu-id="1e182-123">To investigate the problem with MS DTC, examine the Windows event logs.</span></span> <span data-ttu-id="1e182-124">如果無法解決 MS DTC 問題並復原資料庫，請還原資料庫備份。</span><span class="sxs-lookup"><span data-stu-id="1e182-124">If you cannot resolve the problem with MS DTC and recover the database, restore a backup of database.</span></span>  
  
  
