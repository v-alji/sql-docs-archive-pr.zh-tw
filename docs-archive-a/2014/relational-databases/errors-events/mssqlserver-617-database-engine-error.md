---
title: MSSQLSERVER_617 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 617 (Database Engine error)
ms.assetid: 213545d9-08a7-4427-bfd1-8b7e16644281
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 88e9feb7c3ac5d8cf646d2243319b2b160b7757e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87702910"
---
# <a name="mssqlserver_617"></a><span data-ttu-id="dd169-102">MSSQLSERVER_617</span><span class="sxs-lookup"><span data-stu-id="dd169-102">MSSQLSERVER_617</span></span>
    
## <a name="details"></a><span data-ttu-id="dd169-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="dd169-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="dd169-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="dd169-104">Product Name</span></span>|<span data-ttu-id="dd169-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="dd169-105">SQL Server</span></span>|  
|<span data-ttu-id="dd169-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="dd169-106">Event ID</span></span>|<span data-ttu-id="dd169-107">617</span><span class="sxs-lookup"><span data-stu-id="dd169-107">617</span></span>|  
|<span data-ttu-id="dd169-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="dd169-108">Event Source</span></span>|<span data-ttu-id="dd169-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="dd169-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="dd169-110">元件</span><span class="sxs-lookup"><span data-stu-id="dd169-110">Component</span></span>|<span data-ttu-id="dd169-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="dd169-111">SQLEngine</span></span>|  
|<span data-ttu-id="dd169-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="dd169-112">Symbolic Name</span></span>|<span data-ttu-id="dd169-113">NODESHASH</span><span class="sxs-lookup"><span data-stu-id="dd169-113">NODESHASH</span></span>|  
|<span data-ttu-id="dd169-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="dd169-114">Message Text</span></span>|<span data-ttu-id="dd169-115">嘗試取消資料庫識別碼 %d 中物件識別碼 %ld 的雜湊時，在雜湊表中找不到該描述項。</span><span class="sxs-lookup"><span data-stu-id="dd169-115">Descriptor for object ID %ld in database ID %d not found in the hash table during attempt to unhash it.</span></span> <span data-ttu-id="dd169-116">工作資料表遺漏一個項目。</span><span class="sxs-lookup"><span data-stu-id="dd169-116">A work table is missing an entry.</span></span> <span data-ttu-id="dd169-117">請重新執行查詢。</span><span class="sxs-lookup"><span data-stu-id="dd169-117">Rerun the query.</span></span> <span data-ttu-id="dd169-118">如果資料指標與此有關，請先關閉，然後重新開啟資料指標。</span><span class="sxs-lookup"><span data-stu-id="dd169-118">If a cursor is involved, close and reopen the cursor.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="dd169-119">說明</span><span class="sxs-lookup"><span data-stu-id="dd169-119">Explanation</span></span>  
 <span data-ttu-id="dd169-120">SQL Server 找不到特定項目的工作資料表。</span><span class="sxs-lookup"><span data-stu-id="dd169-120">SQL Server cannot locate the work table for a specific entry.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="dd169-121">使用者動作</span><span class="sxs-lookup"><span data-stu-id="dd169-121">User Action</span></span>  
  
1.  <span data-ttu-id="dd169-122">如果資料指標與此有關，請先關閉資料指標，然後重新開啟資料指標。</span><span class="sxs-lookup"><span data-stu-id="dd169-122">If a cursor is involved, close the cursor and re-open the cursor.</span></span>  
  
2.  <span data-ttu-id="dd169-123">再次執行查詢。</span><span class="sxs-lookup"><span data-stu-id="dd169-123">Run the query again.</span></span>  
  
  
