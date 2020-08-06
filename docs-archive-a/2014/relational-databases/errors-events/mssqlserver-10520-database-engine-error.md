---
title: MSSQLSERVER_10520 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 10520 (Database Engine error)
ms.assetid: cc8799f1-5b90-4248-b209-e1d5087f9529
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 1b8bdf080703fa6bd02fc34b8c31f59407814b93
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87699754"
---
# <a name="mssqlserver_10520"></a><span data-ttu-id="2ba19-102">MSSQLSERVER_10520</span><span class="sxs-lookup"><span data-stu-id="2ba19-102">MSSQLSERVER_10520</span></span>
    
## <a name="details"></a><span data-ttu-id="2ba19-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="2ba19-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="2ba19-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="2ba19-104">Product Name</span></span>|<span data-ttu-id="2ba19-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="2ba19-105">SQL Server</span></span>|  
|<span data-ttu-id="2ba19-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="2ba19-106">Event ID</span></span>|<span data-ttu-id="2ba19-107">10520</span><span class="sxs-lookup"><span data-stu-id="2ba19-107">10520</span></span>|  
|<span data-ttu-id="2ba19-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="2ba19-108">Event Source</span></span>|<span data-ttu-id="2ba19-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="2ba19-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="2ba19-110">元件</span><span class="sxs-lookup"><span data-stu-id="2ba19-110">Component</span></span>|<span data-ttu-id="2ba19-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="2ba19-111">SQLEngine</span></span>|  
|<span data-ttu-id="2ba19-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="2ba19-112">Symbolic Name</span></span>|<span data-ttu-id="2ba19-113">PG_PARAM_NOT_ALLOWED</span><span class="sxs-lookup"><span data-stu-id="2ba19-113">PG_PARAM_NOT_ALLOWED</span></span>|  
|<span data-ttu-id="2ba19-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="2ba19-114">Message Text</span></span>|<span data-ttu-id="2ba19-115">無法建立計畫指南 '%.\*ls'，因為已將 @type 指定為 '%ls'，而且已為參數 '%ls' 指定非 NULL 值，</span><span class="sxs-lookup"><span data-stu-id="2ba19-115">Cannot create plan guide '%.\*ls' because @type was specified as '%ls' and a non-NULL value is specified for the parameter '%ls'.</span></span> <span data-ttu-id="2ba19-116">但這種類型要求參數必須為 NULL 值。</span><span class="sxs-lookup"><span data-stu-id="2ba19-116">This type requires a NULL value for the parameter.</span></span> <span data-ttu-id="2ba19-117">請為參數指定 NULL，或將參數類型變更為允許非 NULL 值的類型。</span><span class="sxs-lookup"><span data-stu-id="2ba19-117">Specify NULL for the parameter, or change the type to one that allows a non-NULL value for the parameter.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="2ba19-118">說明</span><span class="sxs-lookup"><span data-stu-id="2ba19-118">Explanation</span></span>  
 <span data-ttu-id="2ba19-119">在 @type 中指定的類型要求指定的參數必須為 NULL 值，但是卻提供了非 NULL 值。</span><span class="sxs-lookup"><span data-stu-id="2ba19-119">The type specified in @type requires a NULL value for the specified parameter, however a non-NULL value was supplied.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="2ba19-120">使用者動作</span><span class="sxs-lookup"><span data-stu-id="2ba19-120">User Action</span></span>  
 <span data-ttu-id="2ba19-121">請為參數指定 NULL，或將參數類型變更為允許非 NULL 值的類型。</span><span class="sxs-lookup"><span data-stu-id="2ba19-121">Specify NULL for the parameter, or change the type to one that allows a non-NULL value for the parameter.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ba19-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2ba19-122">See Also</span></span>  
 <span data-ttu-id="2ba19-123">[sp_create_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="2ba19-123">[sp_create_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql) </span></span>  
 [<span data-ttu-id="2ba19-124">計畫指南</span><span class="sxs-lookup"><span data-stu-id="2ba19-124">Plan Guides</span></span>](../performance/plan-guides.md)  
  
  
