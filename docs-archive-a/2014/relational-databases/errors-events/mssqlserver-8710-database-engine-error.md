---
title: MSSQLSERVER_8710 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 8710 (Database Engine error)
ms.assetid: 78b9f9da-5489-4be0-94df-f065d86ed18c
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 65fb6b3efb42c282347f560353a2b21edc337859
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87607410"
---
# <a name="mssqlserver_8710"></a><span data-ttu-id="8b5cd-102">MSSQLSERVER_8710</span><span class="sxs-lookup"><span data-stu-id="8b5cd-102">MSSQLSERVER_8710</span></span>
    
## <a name="details"></a><span data-ttu-id="8b5cd-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="8b5cd-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8b5cd-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="8b5cd-104">Product Name</span></span>|<span data-ttu-id="8b5cd-105">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="8b5cd-105">MSSQLSERVER</span></span>|  
|<span data-ttu-id="8b5cd-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="8b5cd-106">Event ID</span></span>|<span data-ttu-id="8b5cd-107">8710</span><span class="sxs-lookup"><span data-stu-id="8b5cd-107">8710</span></span>|  
|<span data-ttu-id="8b5cd-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="8b5cd-108">Event Source</span></span>|<span data-ttu-id="8b5cd-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="8b5cd-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="8b5cd-110">元件</span><span class="sxs-lookup"><span data-stu-id="8b5cd-110">Component</span></span>|<span data-ttu-id="8b5cd-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="8b5cd-111">SQLEngine</span></span>|  
|<span data-ttu-id="8b5cd-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="8b5cd-112">Symbolic Name</span></span>|<span data-ttu-id="8b5cd-113">QUERY2_CUBE_ILLEGAL_AGG_FUNC</span><span class="sxs-lookup"><span data-stu-id="8b5cd-113">QUERY2_CUBE_ILLEGAL_AGG_FUNC</span></span>|  
|<span data-ttu-id="8b5cd-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="8b5cd-114">Message Text</span></span>|<span data-ttu-id="8b5cd-115">必須提供搭配 CUBE、ROLLUP 或 GROUPING SET 查詢使用的彙總函式才能進行合併子彙總。</span><span class="sxs-lookup"><span data-stu-id="8b5cd-115">Aggregate functions that are used with CUBE, ROLLUP, or GROUPING SET queries must provide for the merging of subaggregates.</span></span> <span data-ttu-id="8b5cd-116">如果要修正這個問題，請移除彙總函式或在 GROUP BY 子句之上使用 UNION ALL 來撰寫查詢。</span><span class="sxs-lookup"><span data-stu-id="8b5cd-116">To fix this problem, remove the aggregate function or write the query using UNION ALL over GROUP BY clauses.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="8b5cd-117">說明</span><span class="sxs-lookup"><span data-stu-id="8b5cd-117">Explanation</span></span>  
 <span data-ttu-id="8b5cd-118">已搭配 CUBE、ROLLUP 或 GROUPING SETS 使用的彙總函式未提供合併子彙總的方法。</span><span class="sxs-lookup"><span data-stu-id="8b5cd-118">An aggregate function has been used with CUBE, ROLLUP, or GROUPING SETS that does not provide a method for merging subaggregates.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="8b5cd-119">使用者動作</span><span class="sxs-lookup"><span data-stu-id="8b5cd-119">User Action</span></span>  
 <span data-ttu-id="8b5cd-120">如果要修正這個問題，請移除彙總函式或在 GROUP BY 子句之上使用 UNION ALL 來撰寫查詢。</span><span class="sxs-lookup"><span data-stu-id="8b5cd-120">To fix this problem, remove the aggregate function or write the query using UNION ALL over GROUP BY clauses.</span></span>  
  
  
