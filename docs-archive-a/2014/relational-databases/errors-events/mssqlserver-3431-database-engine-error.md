---
title: MSSQLSERVER_3431 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 3431 (Database Engine error)
ms.assetid: 9541217f-e5c6-4a12-a19a-006058f1d3f3
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 9b62047a25d71ca05dc3ab03651e5672353bc0a0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598898"
---
# <a name="mssqlserver_3431"></a><span data-ttu-id="4a0af-102">MSSQLSERVER_3431</span><span class="sxs-lookup"><span data-stu-id="4a0af-102">MSSQLSERVER_3431</span></span>
    
## <a name="details"></a><span data-ttu-id="4a0af-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="4a0af-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="4a0af-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="4a0af-104">Product Name</span></span>|<span data-ttu-id="4a0af-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="4a0af-105">SQL Server</span></span>|  
|<span data-ttu-id="4a0af-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="4a0af-106">Event ID</span></span>|<span data-ttu-id="4a0af-107">3431</span><span class="sxs-lookup"><span data-stu-id="4a0af-107">3431</span></span>|  
|<span data-ttu-id="4a0af-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="4a0af-108">Event Source</span></span>|<span data-ttu-id="4a0af-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="4a0af-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="4a0af-110">元件</span><span class="sxs-lookup"><span data-stu-id="4a0af-110">Component</span></span>|<span data-ttu-id="4a0af-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="4a0af-111">SQLEngine</span></span>|  
|<span data-ttu-id="4a0af-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="4a0af-112">Symbolic Name</span></span>|<span data-ttu-id="4a0af-113">UNRESOLVED_XACT</span><span class="sxs-lookup"><span data-stu-id="4a0af-113">UNRESOLVED_XACT</span></span>|  
|<span data-ttu-id="4a0af-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="4a0af-114">Message Text</span></span>|<span data-ttu-id="4a0af-115">無法復原資料庫 '%.\*ls' (資料庫識別碼 %d)，因為有尚未解決的交易結果。</span><span class="sxs-lookup"><span data-stu-id="4a0af-115">Could not recover database '%.\*ls' (database ID %d) because of unresolved transaction outcomes.</span></span> <span data-ttu-id="4a0af-116">Microsoft 分散式交易協調器 (MS DTC) 的交易已備妥，但 MS DTC 無法決定解決方式。</span><span class="sxs-lookup"><span data-stu-id="4a0af-116">Microsoft Distributed Transaction Coordinator (MS DTC) transactions were prepared, but MS DTC was unable to determine the resolution.</span></span> <span data-ttu-id="4a0af-117">若要解決，必須修正 MS DTC、從完整備份還原，或者修復資料庫。</span><span class="sxs-lookup"><span data-stu-id="4a0af-117">To resolve, either fix MS DTC, restore from a full backup, or repair the database.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="4a0af-118">說明</span><span class="sxs-lookup"><span data-stu-id="4a0af-118">Explanation</span></span>  
 <span data-ttu-id="4a0af-119">資料庫關閉時，使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 分散式交易協調器 (MS DTC) 的一個或多個分散式交易未完成。</span><span class="sxs-lookup"><span data-stu-id="4a0af-119">One or more distributed transactions that were using [!INCLUDE[msCoName](../../includes/msconame-md.md)] Distributed Transaction Coordinator (MS DTC) were incomplete when the database was shut down.</span></span> <span data-ttu-id="4a0af-120">由於無法從 MS DTC 取得更多資訊，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 無法完成交易或回復交易，因此，此資料庫的復原失敗。</span><span class="sxs-lookup"><span data-stu-id="4a0af-120">Recovery of this database failed because [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] cannot complete the transactions or roll back the transactions without more information from MS DTC.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="4a0af-121">使用者動作</span><span class="sxs-lookup"><span data-stu-id="4a0af-121">User Action</span></span>  
 <span data-ttu-id="4a0af-122">若要復原此資料庫，您必須先解決 MS DTC 的問題。</span><span class="sxs-lookup"><span data-stu-id="4a0af-122">To recover this database, you must first resolve the problem with MS DTC.</span></span> <span data-ttu-id="4a0af-123">若要調查 MS DTC 的問題，請檢查 Windows 事件記錄檔。</span><span class="sxs-lookup"><span data-stu-id="4a0af-123">To investigate the problem with MS DTC, examine the Windows event logs.</span></span> <span data-ttu-id="4a0af-124">如果無法解決 MS DTC 問題並復原資料庫，請還原資料庫備份。</span><span class="sxs-lookup"><span data-stu-id="4a0af-124">If you cannot resolve the problem with MS DTC and recover the database, restore a backup of database.</span></span>  
  
  
