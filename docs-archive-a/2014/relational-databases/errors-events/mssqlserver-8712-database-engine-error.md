---
title: MSSQLSERVER_8712 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 8712 (Database Engine error)
ms.assetid: 292fb3bc-062e-41e4-a566-b5d3d0b21977
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 9285d4846cac5af2dd6e87ab55d5fd0610586d07
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87607406"
---
# <a name="mssqlserver_8712"></a><span data-ttu-id="9ac0b-102">MSSQLSERVER_8712</span><span class="sxs-lookup"><span data-stu-id="9ac0b-102">MSSQLSERVER_8712</span></span>
    
## <a name="details"></a><span data-ttu-id="9ac0b-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="9ac0b-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="9ac0b-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="9ac0b-104">Product Name</span></span>|<span data-ttu-id="9ac0b-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="9ac0b-105">SQL Server</span></span>|  
|<span data-ttu-id="9ac0b-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="9ac0b-106">Event ID</span></span>|<span data-ttu-id="9ac0b-107">8712</span><span class="sxs-lookup"><span data-stu-id="9ac0b-107">8712</span></span>|  
|<span data-ttu-id="9ac0b-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="9ac0b-108">Event Source</span></span>|<span data-ttu-id="9ac0b-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="9ac0b-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="9ac0b-110">元件</span><span class="sxs-lookup"><span data-stu-id="9ac0b-110">Component</span></span>|<span data-ttu-id="9ac0b-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="9ac0b-111">SQLEngine</span></span>|  
|<span data-ttu-id="9ac0b-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="9ac0b-112">Symbolic Name</span></span>|<span data-ttu-id="9ac0b-113">USEPLAN_ERR_NO_INDEX</span><span class="sxs-lookup"><span data-stu-id="9ac0b-113">USEPLAN_ERR_NO_INDEX</span></span>|  
|<span data-ttu-id="9ac0b-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="9ac0b-114">Message Text</span></span>|<span data-ttu-id="9ac0b-115">USE PLAN 提示中指定的索引 '%.\*ls' 不存在。</span><span class="sxs-lookup"><span data-stu-id="9ac0b-115">Index '%.\*ls', specified in the USE PLAN hint, does not exist.</span></span> <span data-ttu-id="9ac0b-116">請指定現有的索引，或用指定的名稱建立索引。</span><span class="sxs-lookup"><span data-stu-id="9ac0b-116">Specify an existing index, or create an index with the specified name.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="9ac0b-117">說明</span><span class="sxs-lookup"><span data-stu-id="9ac0b-117">Explanation</span></span>  
 <span data-ttu-id="9ac0b-118">在 USE PLAN 提示中指定的索引不存在。</span><span class="sxs-lookup"><span data-stu-id="9ac0b-118">An index that is specified in the USE PLAN hint does not exist.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="9ac0b-119">使用者動作</span><span class="sxs-lookup"><span data-stu-id="9ac0b-119">User Action</span></span>  
 <span data-ttu-id="9ac0b-120">請確定在 USE PLAN 提示中指定的所有索引都存在。</span><span class="sxs-lookup"><span data-stu-id="9ac0b-120">Ensure all indexes that are specified in the USE PLAN hint exist.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ac0b-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9ac0b-121">See Also</span></span>  
 <span data-ttu-id="9ac0b-122">[查詢提示 &#40;Transact-SQL&#41;](/sql/t-sql/queries/hints-transact-sql-query) </span><span class="sxs-lookup"><span data-stu-id="9ac0b-122">[Query Hints &#40;Transact-SQL&#41;](/sql/t-sql/queries/hints-transact-sql-query) </span></span>  
 [<span data-ttu-id="9ac0b-123">計畫指南</span><span class="sxs-lookup"><span data-stu-id="9ac0b-123">Plan Guides</span></span>](../performance/plan-guides.md)  
  
  
