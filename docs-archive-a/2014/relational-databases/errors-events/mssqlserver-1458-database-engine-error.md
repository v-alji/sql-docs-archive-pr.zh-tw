---
title: MSSQLSERVER_1458 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 1458 (Database Engine error)
ms.assetid: adc78c59-a6f2-432b-9a07-fdd1dc2b9026
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: efa45177a92402b25099be5bb3e3dcc91a5fa6d2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598953"
---
# <a name="mssqlserver_1458"></a><span data-ttu-id="d7b82-102">MSSQLSERVER_1458</span><span class="sxs-lookup"><span data-stu-id="d7b82-102">MSSQLSERVER_1458</span></span>
    
## <a name="details"></a><span data-ttu-id="d7b82-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="d7b82-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d7b82-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="d7b82-104">Product Name</span></span>|<span data-ttu-id="d7b82-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="d7b82-105">SQL Server</span></span>|  
|<span data-ttu-id="d7b82-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="d7b82-106">Event ID</span></span>|<span data-ttu-id="d7b82-107">1458</span><span class="sxs-lookup"><span data-stu-id="d7b82-107">1458</span></span>|  
|<span data-ttu-id="d7b82-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="d7b82-108">Event Source</span></span>|<span data-ttu-id="d7b82-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="d7b82-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="d7b82-110">元件</span><span class="sxs-lookup"><span data-stu-id="d7b82-110">Component</span></span>|<span data-ttu-id="d7b82-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="d7b82-111">SQLEngine</span></span>|  
|<span data-ttu-id="d7b82-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="d7b82-112">Symbolic Name</span></span>|<span data-ttu-id="d7b82-113">DBM_FAILREDO_ON_PRIMARY</span><span class="sxs-lookup"><span data-stu-id="d7b82-113">DBM_FAILREDO_ON_PRIMARY</span></span>|  
|<span data-ttu-id="d7b82-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="d7b82-114">Message Text</span></span>|<span data-ttu-id="d7b82-115">'%.\*ls' 資料庫的主體副本發現錯誤 %d，狀態 %d，嚴重性 %d。</span><span class="sxs-lookup"><span data-stu-id="d7b82-115">The principal copy of the '%.\*ls' database encountered error %d, status %d, severity %d.</span></span> <span data-ttu-id="d7b82-116">資料庫鏡像已暫停。</span><span class="sxs-lookup"><span data-stu-id="d7b82-116">Database mirroring has been suspended.</span></span> <span data-ttu-id="d7b82-117">請嘗試解決錯誤狀況，然後繼續執行鏡像。</span><span class="sxs-lookup"><span data-stu-id="d7b82-117">Try to resolve the error condition, and resume mirroring.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="d7b82-118">說明</span><span class="sxs-lookup"><span data-stu-id="d7b82-118">Explanation</span></span>  
 <span data-ttu-id="d7b82-119">這個訊息表示主體資料庫遭遇錯誤，導致資料庫鏡像暫停。</span><span class="sxs-lookup"><span data-stu-id="d7b82-119">This messages indicates that the principal database encountered an error that caused database mirroring to be suspended.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="d7b82-120">使用者動作</span><span class="sxs-lookup"><span data-stu-id="d7b82-120">User Action</span></span>  
 <span data-ttu-id="d7b82-121">在大部分情況下，這個錯誤都會自動修正。</span><span class="sxs-lookup"><span data-stu-id="d7b82-121">Most cases of this error are self correcting.</span></span> <span data-ttu-id="d7b82-122">如果問題持續發生，重新啟動資料庫或伺服器執行個體通常就能修正問題。</span><span class="sxs-lookup"><span data-stu-id="d7b82-122">If the problem persists, restarting the database or server instance typically corrects the problem.</span></span> <span data-ttu-id="d7b82-123">如需詳細資訊，請查看每個夥伴的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 錯誤記錄檔，以取得在此訊息之前發生的相關錯誤。</span><span class="sxs-lookup"><span data-stu-id="d7b82-123">For more information, look in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log on each partner for the associated error that preceded this message.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7b82-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d7b82-124">See Also</span></span>  
 [<span data-ttu-id="d7b82-125">監視資料庫鏡像 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="d7b82-125">Monitoring Database Mirroring &#40;SQL Server&#41;</span></span>](../../database-engine/database-mirroring/database-mirroring-sql-server.md)  
  
  
