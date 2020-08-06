---
title: MSSQLSERVER_8689 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 8689 (Database Engine error)
ms.assetid: 99467a32-6576-4272-a076-b16c06933f2a
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 2cdca0a3cd9ce47ccb39ebeaf8fd1cd260aafbd9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87698221"
---
# <a name="mssqlserver_8689"></a><span data-ttu-id="ab871-102">MSSQLSERVER_8689</span><span class="sxs-lookup"><span data-stu-id="ab871-102">MSSQLSERVER_8689</span></span>
    
## <a name="details"></a><span data-ttu-id="ab871-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="ab871-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ab871-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="ab871-104">Product Name</span></span>|<span data-ttu-id="ab871-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="ab871-105">SQL Server</span></span>|  
|<span data-ttu-id="ab871-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="ab871-106">Event ID</span></span>|<span data-ttu-id="ab871-107">8689</span><span class="sxs-lookup"><span data-stu-id="ab871-107">8689</span></span>|  
|<span data-ttu-id="ab871-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="ab871-108">Event Source</span></span>|<span data-ttu-id="ab871-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="ab871-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="ab871-110">元件</span><span class="sxs-lookup"><span data-stu-id="ab871-110">Component</span></span>|<span data-ttu-id="ab871-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="ab871-111">SQLEngine</span></span>|  
|<span data-ttu-id="ab871-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="ab871-112">Symbolic Name</span></span>|<span data-ttu-id="ab871-113">USEPLAN_ERR_NO_DB</span><span class="sxs-lookup"><span data-stu-id="ab871-113">USEPLAN_ERR_NO_DB</span></span>|  
|<span data-ttu-id="ab871-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="ab871-114">Message Text</span></span>|<span data-ttu-id="ab871-115">USE PLAN 提示中指定的資料庫 '%.\*ls' 不存在。</span><span class="sxs-lookup"><span data-stu-id="ab871-115">Database '%.\*ls', specified in the USE PLAN hint, does not exist.</span></span> <span data-ttu-id="ab871-116">請指定現有的資料庫。</span><span class="sxs-lookup"><span data-stu-id="ab871-116">Specify an existing database.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="ab871-117">說明</span><span class="sxs-lookup"><span data-stu-id="ab871-117">Explanation</span></span>  
 <span data-ttu-id="ab871-118">在 USE PLAN 提示中指定的資料庫不存在。</span><span class="sxs-lookup"><span data-stu-id="ab871-118">A database that is specified in the USE PLAN hint does not exist.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="ab871-119">使用者動作</span><span class="sxs-lookup"><span data-stu-id="ab871-119">User Action</span></span>  
 <span data-ttu-id="ab871-120">請確定在 USE PLAN 提示中指定的所有資料庫都存在。</span><span class="sxs-lookup"><span data-stu-id="ab871-120">Ensure all databases that are specified in the USE PLAN hint exist.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab871-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ab871-121">See Also</span></span>  
 <span data-ttu-id="ab871-122">[查詢提示 &#40;Transact-SQL&#41;](/sql/t-sql/queries/hints-transact-sql-query) </span><span class="sxs-lookup"><span data-stu-id="ab871-122">[Query Hints &#40;Transact-SQL&#41;](/sql/t-sql/queries/hints-transact-sql-query) </span></span>  
 [<span data-ttu-id="ab871-123">計畫指南</span><span class="sxs-lookup"><span data-stu-id="ab871-123">Plan Guides</span></span>](../performance/plan-guides.md)  
  
  
