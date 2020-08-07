---
title: MSSQLSERVER_8649 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 8649 (Database Engine error)
ms.assetid: 992dbc74-7c3a-498b-9f1b-b28387640677
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b39ed0d8ffe5f7f601b6cb1393596d0d6546e557
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597855"
---
# <a name="mssqlserver_8649"></a><span data-ttu-id="0ef04-102">MSSQLSERVER_8649</span><span class="sxs-lookup"><span data-stu-id="0ef04-102">MSSQLSERVER_8649</span></span>
    
## <a name="details"></a><span data-ttu-id="0ef04-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="0ef04-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="0ef04-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="0ef04-104">Product Name</span></span>|<span data-ttu-id="0ef04-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="0ef04-105">SQL Server</span></span>|  
|<span data-ttu-id="0ef04-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="0ef04-106">Event ID</span></span>|<span data-ttu-id="0ef04-107">8649</span><span class="sxs-lookup"><span data-stu-id="0ef04-107">8649</span></span>|  
|<span data-ttu-id="0ef04-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="0ef04-108">Event Source</span></span>|<span data-ttu-id="0ef04-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="0ef04-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="0ef04-110">元件</span><span class="sxs-lookup"><span data-stu-id="0ef04-110">Component</span></span>|<span data-ttu-id="0ef04-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="0ef04-111">SQLEngine</span></span>|  
|<span data-ttu-id="0ef04-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="0ef04-112">Symbolic Name</span></span>|<span data-ttu-id="0ef04-113">COST_TOO_HIGH</span><span class="sxs-lookup"><span data-stu-id="0ef04-113">COST_TOO_HIGH</span></span>|  
|<span data-ttu-id="0ef04-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="0ef04-114">Message Text</span></span>|<span data-ttu-id="0ef04-115">查詢已經取消，因為這個查詢 (%d) 的預估成本超過了設定的臨界值 %d。</span><span class="sxs-lookup"><span data-stu-id="0ef04-115">The query has been canceled because the estimated cost of this query (%d) exceeds the configured threshold of %d.</span></span> <span data-ttu-id="0ef04-116">請連絡系統管理員。</span><span class="sxs-lookup"><span data-stu-id="0ef04-116">Contact the system administrator.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="0ef04-117">說明</span><span class="sxs-lookup"><span data-stu-id="0ef04-117">Explanation</span></span>  
 <span data-ttu-id="0ef04-118">由於查詢的預估成本超過了 QUERY_GOVERNOR_COST_LIMIT 設定的臨界值，因此已經取消查詢。</span><span class="sxs-lookup"><span data-stu-id="0ef04-118">The query was canceled because the estimated cost of this query exceeds the configured threshold set for the QUERY_GOVERNOR_COST_LIMIT.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="0ef04-119">使用者動作</span><span class="sxs-lookup"><span data-stu-id="0ef04-119">User Action</span></span>  
 <span data-ttu-id="0ef04-120">將 QUERY_GOVERNOR_COST_LIMIT 選項設定成較高的值。</span><span class="sxs-lookup"><span data-stu-id="0ef04-120">Set the QUERY_GOVERNOR_COST_LIMIT option to a higher value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ef04-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0ef04-121">See Also</span></span>  
 [<span data-ttu-id="0ef04-122">SET QUERY_GOVERNOR_COST_LIMIT &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="0ef04-122">SET QUERY_GOVERNOR_COST_LIMIT &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/set-query-governor-cost-limit-transact-sql)  
  
  
