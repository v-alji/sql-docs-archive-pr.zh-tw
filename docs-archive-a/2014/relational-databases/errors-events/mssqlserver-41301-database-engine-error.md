---
title: MSSQLSERVER_41301 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 41301 (Database Engine error)
ms.assetid: c6127e1e-2846-4ee9-bc42-2d896ea9730e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d4fa78b334f32033f96df002aeaf039994b396cf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597149"
---
# <a name="mssqlserver_41301"></a><span data-ttu-id="f9191-102">MSSQLSERVER_41301</span><span class="sxs-lookup"><span data-stu-id="f9191-102">MSSQLSERVER_41301</span></span>
    
## <a name="details"></a><span data-ttu-id="f9191-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="f9191-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f9191-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="f9191-104">Product Name</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|<span data-ttu-id="f9191-105">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="f9191-105">Event ID</span></span>|<span data-ttu-id="f9191-106">41301</span><span class="sxs-lookup"><span data-stu-id="f9191-106">41301</span></span>|  
|<span data-ttu-id="f9191-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="f9191-107">Event Source</span></span>|<span data-ttu-id="f9191-108">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="f9191-108">MSSQLSERVER</span></span>|  
|<span data-ttu-id="f9191-109">元件</span><span class="sxs-lookup"><span data-stu-id="f9191-109">Component</span></span>|<span data-ttu-id="f9191-110">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="f9191-110">SQLEngine</span></span>|  
|<span data-ttu-id="f9191-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="f9191-111">Symbolic Name</span></span>|<span data-ttu-id="f9191-112">COMMIT_DEPENDENCY_FAILURE</span><span class="sxs-lookup"><span data-stu-id="f9191-112">COMMIT_DEPENDENCY_FAILURE</span></span>|  
|<span data-ttu-id="f9191-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="f9191-113">Message Text</span></span>|<span data-ttu-id="f9191-114">目前交易具有相依性的先前交易已經中止，而且目前交易無法再認可。</span><span class="sxs-lookup"><span data-stu-id="f9191-114">A previous transaction that the current transaction took a dependency on has aborted, and the current transaction can no longer commit.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="f9191-115">說明</span><span class="sxs-lookup"><span data-stu-id="f9191-115">Explanation</span></span>  
 <span data-ttu-id="f9191-116">交易發生相依性失敗，現在注定要失敗。</span><span class="sxs-lookup"><span data-stu-id="f9191-116">The transaction encountered a dependency failure, and is now doomed.</span></span>  
  
 <span data-ttu-id="f9191-117">相依交易過多可能也會造成這個錯誤。</span><span class="sxs-lookup"><span data-stu-id="f9191-117">This error can also be caused by too many dependent transactions.</span></span> <span data-ttu-id="f9191-118">任何寫入交易都可能具有有限數目的相依交易。</span><span class="sxs-lookup"><span data-stu-id="f9191-118">Any write transaction can have a limited number of dependent transactions.</span></span> <span data-ttu-id="f9191-119">例如，如果太多讀取交易嘗試相依於更新交易，就可能會發生這個錯誤。</span><span class="sxs-lookup"><span data-stu-id="f9191-119">For example, this error can occur if too many read transactions try to take a dependency on the update transaction.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="f9191-120">使用者動作</span><span class="sxs-lookup"><span data-stu-id="f9191-120">User Action</span></span>  
 <span data-ttu-id="f9191-121">請勿在交易中執行任何工作。</span><span class="sxs-lookup"><span data-stu-id="f9191-121">Don't do any work on the transaction.</span></span> <span data-ttu-id="f9191-122">呼叫 ROLLBACK TRAN 回復交易。</span><span class="sxs-lookup"><span data-stu-id="f9191-122">Call ROLLBACK TRAN to roll back the transaction.</span></span> <span data-ttu-id="f9191-123">如需詳細資訊，請參閱[記憶體內部 OLTP &#40;記憶體內部最佳化&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)。</span><span class="sxs-lookup"><span data-stu-id="f9191-123">For more information, see [In-Memory OLTP &#40;In-Memory Optimization&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9191-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f9191-124">See Also</span></span>  
 [<span data-ttu-id="f9191-125">啟用和停用 AlwaysOn 可用性群組 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="f9191-125">Enable and Disable AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](../../database-engine/availability-groups/windows/enable-and-disable-always-on-availability-groups-sql-server.md)  
  
  
