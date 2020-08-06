---
title: MSSQLSERVER_2511 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 2511 (Database Engine error)
ms.assetid: 9a00c0ed-eb4b-4fae-8016-192396006c37
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 23e91b0d64140329639cf57f3a336cd2eab8e4e8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87699637"
---
# <a name="mssqlserver_2511"></a><span data-ttu-id="340e3-102">MSSQLSERVER_2511</span><span class="sxs-lookup"><span data-stu-id="340e3-102">MSSQLSERVER_2511</span></span>
    
## <a name="details"></a><span data-ttu-id="340e3-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="340e3-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="340e3-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="340e3-104">Product Name</span></span>|<span data-ttu-id="340e3-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="340e3-105">SQL Server</span></span>|  
|<span data-ttu-id="340e3-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="340e3-106">Event ID</span></span>|<span data-ttu-id="340e3-107">2511</span><span class="sxs-lookup"><span data-stu-id="340e3-107">2511</span></span>|  
|<span data-ttu-id="340e3-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="340e3-108">Event Source</span></span>|<span data-ttu-id="340e3-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="340e3-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="340e3-110">元件</span><span class="sxs-lookup"><span data-stu-id="340e3-110">Component</span></span>|<span data-ttu-id="340e3-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="340e3-111">SQLEngine</span></span>|  
|<span data-ttu-id="340e3-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="340e3-112">Symbolic Name</span></span>|<span data-ttu-id="340e3-113">DBCC_KEYS_OUT_OF_ORDER</span><span class="sxs-lookup"><span data-stu-id="340e3-113">DBCC_KEYS_OUT_OF_ORDER</span></span>|  
|<span data-ttu-id="340e3-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="340e3-114">Message Text</span></span>|<span data-ttu-id="340e3-115">資料表錯誤：物件識別碼 %d，索引識別碼 %d，分割區識別碼 %I64d，配置單位識別碼 %I64d (類型 %.\*ls)。</span><span class="sxs-lookup"><span data-stu-id="340e3-115">Table error: Object ID %d, index ID %d, partition ID %I64d, alloc unit ID %I64d (type %.\*ls).</span></span> <span data-ttu-id="340e3-116">頁面 %S_PGID，位置 %d 和 %d 的索引鍵次序不對。</span><span class="sxs-lookup"><span data-stu-id="340e3-116">Keys out of order on page %S_PGID, slots %d and %d.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="340e3-117">說明</span><span class="sxs-lookup"><span data-stu-id="340e3-117">Explanation</span></span>  
 <span data-ttu-id="340e3-118">在指定的索引中偵測到次序不對的索引鍵。</span><span class="sxs-lookup"><span data-stu-id="340e3-118">Out-of-order keys were detected in the specified index.</span></span> <span data-ttu-id="340e3-119">包含索引鍵的頁面可能已損毀。</span><span class="sxs-lookup"><span data-stu-id="340e3-119">The page in which the keys are contained may be corrupted.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="340e3-120">使用者動作</span><span class="sxs-lookup"><span data-stu-id="340e3-120">User Action</span></span>  
 <span data-ttu-id="340e3-121">使用 ALTER INDEX REBUILD 陳述式來重建指定的索引。</span><span class="sxs-lookup"><span data-stu-id="340e3-121">Rebuild the specified index by using the ALTER INDEX REBUILD statement.</span></span>  
  
  
