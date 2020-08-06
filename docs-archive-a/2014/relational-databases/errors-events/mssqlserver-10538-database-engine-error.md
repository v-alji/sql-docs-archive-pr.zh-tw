---
title: MSSQLSERVER_10538 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 10538 (Database Engine error)
ms.assetid: 284d19b4-4979-4cbe-a9be-ac1104433c69
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: edc6abf192a3341f9b84c99e99071343cc882c3d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87699721"
---
# <a name="mssqlserver_10538"></a><span data-ttu-id="67224-102">MSSQLSERVER_10538</span><span class="sxs-lookup"><span data-stu-id="67224-102">MSSQLSERVER_10538</span></span>
    
## <a name="details"></a><span data-ttu-id="67224-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="67224-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="67224-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="67224-104">Product Name</span></span>|<span data-ttu-id="67224-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="67224-105">SQL Server</span></span>|  
|<span data-ttu-id="67224-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="67224-106">Event ID</span></span>|<span data-ttu-id="67224-107">10538</span><span class="sxs-lookup"><span data-stu-id="67224-107">10538</span></span>|  
|<span data-ttu-id="67224-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="67224-108">Event Source</span></span>|<span data-ttu-id="67224-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="67224-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="67224-110">元件</span><span class="sxs-lookup"><span data-stu-id="67224-110">Component</span></span>|<span data-ttu-id="67224-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="67224-111">SQLEngine</span></span>|  
|<span data-ttu-id="67224-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="67224-112">Symbolic Name</span></span>|<span data-ttu-id="67224-113">PG_INVALID_PLANGUIDE_HANDLE</span><span class="sxs-lookup"><span data-stu-id="67224-113">PG_INVALID_PLANGUIDE_HANDLE</span></span>|  
|<span data-ttu-id="67224-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="67224-114">Message Text</span></span>|<span data-ttu-id="67224-115">找不到計畫指南，可能是因為指定的計畫指南識別碼是 NULL 或無效，或是因為您對計畫指南參考的物件不具有權限。</span><span class="sxs-lookup"><span data-stu-id="67224-115">Cannot find the plan guide either because the specified plan guide ID is NULL or invalid, or you do not have permission on the object referenced by the plan guide.</span></span> <span data-ttu-id="67224-116">請確認計畫指南識別碼是否有效、目前工作階段是否設定為正確的資料庫內容，以及您是否具有計畫指南所參考物件的 ALTER DATABASE 權限或 ALTER 權限。</span><span class="sxs-lookup"><span data-stu-id="67224-116">Verify that the plan guide ID is valid, the current session is set to the correct database context, and you have either ALTER DATABASE permission or ALTER permission on the object referenced by the plan guide.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="67224-117">說明</span><span class="sxs-lookup"><span data-stu-id="67224-117">Explanation</span></span>  
 <span data-ttu-id="67224-118">指定之計畫指南的識別碼為 NULL 或無效，或者您對計畫指南所參考的物件沒有權限。</span><span class="sxs-lookup"><span data-stu-id="67224-118">The ID of the specified plan guide is NULL or invalid, or you do not have permission on the object referenced by the plan guide.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="67224-119">使用者動作</span><span class="sxs-lookup"><span data-stu-id="67224-119">User Action</span></span>  
 <span data-ttu-id="67224-120">請確認計畫指南識別碼是否有效、目前工作階段是否設定為正確的資料庫內容，以及您是否具有計畫指南所參考物件的 ALTER DATABASE 權限或 ALTER 權限。</span><span class="sxs-lookup"><span data-stu-id="67224-120">Verify that the plan guide ID is valid, the current session is set to the correct database context, and you have ALTER DATABASE permission or ALTER permission on the object referenced by the plan guide.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67224-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="67224-121">See Also</span></span>  
 <span data-ttu-id="67224-122">[sp_create_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="67224-122">[sp_create_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql) </span></span>  
 <span data-ttu-id="67224-123">[計劃指南](../performance/plan-guides.md) </span><span class="sxs-lookup"><span data-stu-id="67224-123">[Plan Guides](../performance/plan-guides.md) </span></span>  
 [<span data-ttu-id="67224-124">sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="67224-124">sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql)  
  
  
