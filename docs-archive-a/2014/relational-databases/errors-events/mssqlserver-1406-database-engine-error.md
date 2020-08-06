---
title: MSSQLSERVER_1406 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 1406 (Database Engine error)
ms.assetid: 915f97de-9b74-41f8-8bd5-b2d061416718
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: adaa0084b875f720c477189e0e8e085af124f4cb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87702946"
---
# <a name="mssqlserver_1406"></a><span data-ttu-id="aee39-102">MSSQLSERVER_1406</span><span class="sxs-lookup"><span data-stu-id="aee39-102">MSSQLSERVER_1406</span></span>
    
## <a name="details"></a><span data-ttu-id="aee39-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="aee39-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="aee39-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="aee39-104">Product Name</span></span>|<span data-ttu-id="aee39-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="aee39-105">SQL Server</span></span>|  
|<span data-ttu-id="aee39-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="aee39-106">Event ID</span></span>|<span data-ttu-id="aee39-107">1406</span><span class="sxs-lookup"><span data-stu-id="aee39-107">1406</span></span>|  
|<span data-ttu-id="aee39-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="aee39-108">Event Source</span></span>|<span data-ttu-id="aee39-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="aee39-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="aee39-110">元件</span><span class="sxs-lookup"><span data-stu-id="aee39-110">Component</span></span>|<span data-ttu-id="aee39-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="aee39-111">SQLEngine</span></span>|  
|<span data-ttu-id="aee39-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="aee39-112">Symbolic Name</span></span>|<span data-ttu-id="aee39-113">DBM_BADSTATEFORFORCESERVICE</span><span class="sxs-lookup"><span data-stu-id="aee39-113">DBM_BADSTATEFORFORCESERVICE</span></span>|  
|<span data-ttu-id="aee39-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="aee39-114">Message Text</span></span>|<span data-ttu-id="aee39-115">無法安全地強制服務。</span><span class="sxs-lookup"><span data-stu-id="aee39-115">Unable to force service safely.</span></span> <span data-ttu-id="aee39-116">請移除資料庫鏡像及復原資料庫 "%.\*ls"，以取得存取權。</span><span class="sxs-lookup"><span data-stu-id="aee39-116">Remove database mirroring and recover database "%.\*ls" to gain access.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="aee39-117">說明</span><span class="sxs-lookup"><span data-stu-id="aee39-117">Explanation</span></span>  
 <span data-ttu-id="aee39-118">[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 不能強制服務，因為鏡像狀態無法保證強制服務處理序會正確地運作。</span><span class="sxs-lookup"><span data-stu-id="aee39-118">The [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] cannot force service because the mirroring state cannot guarantee that the force service process would work correctly.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="aee39-119">使用者動作</span><span class="sxs-lookup"><span data-stu-id="aee39-119">User Action</span></span>  
 <span data-ttu-id="aee39-120">移除資料庫鏡像。</span><span class="sxs-lookup"><span data-stu-id="aee39-120">Remove database mirroring.</span></span> <span data-ttu-id="aee39-121">然後，您就可以復原鏡像資料庫，以取得存取權。</span><span class="sxs-lookup"><span data-stu-id="aee39-121">You can then recover the mirror database to gain access to it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aee39-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="aee39-122">See Also</span></span>  
 <span data-ttu-id="aee39-123">[在資料庫鏡像工作階段中強制服務 &#40;Transact-SQL&#41;](../../database-engine/database-mirroring/force-service-in-a-database-mirroring-session-transact-sql.md) </span><span class="sxs-lookup"><span data-stu-id="aee39-123">[Force Service in a Database Mirroring Session &#40;Transact-SQL&#41;](../../database-engine/database-mirroring/force-service-in-a-database-mirroring-session-transact-sql.md) </span></span>  
 [<span data-ttu-id="aee39-124">移除資料庫鏡像 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="aee39-124">Removing Database Mirroring &#40;SQL Server&#41;</span></span>](../../database-engine/database-mirroring/database-mirroring-sql-server.md)  
  
  
