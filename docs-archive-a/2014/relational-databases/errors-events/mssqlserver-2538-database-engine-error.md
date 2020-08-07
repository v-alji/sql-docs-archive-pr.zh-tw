---
title: MSSQLSERVER_2538 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 2538 (Database Engine error)
ms.assetid: 0a0f7d79-f1ba-4749-8804-fb660cca3492
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 9f4ae886a6fd0abee2f7aa22c6a234c0a6c2d040
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598913"
---
# <a name="mssqlserver_2538"></a><span data-ttu-id="52aeb-102">MSSQLSERVER_2538</span><span class="sxs-lookup"><span data-stu-id="52aeb-102">MSSQLSERVER_2538</span></span>
    
## <a name="details"></a><span data-ttu-id="52aeb-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="52aeb-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="52aeb-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="52aeb-104">Product Name</span></span>|<span data-ttu-id="52aeb-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="52aeb-105">SQL Server</span></span>|  
|<span data-ttu-id="52aeb-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="52aeb-106">Event ID</span></span>|<span data-ttu-id="52aeb-107">2538</span><span class="sxs-lookup"><span data-stu-id="52aeb-107">2538</span></span>|  
|<span data-ttu-id="52aeb-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="52aeb-108">Event Source</span></span>|<span data-ttu-id="52aeb-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="52aeb-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="52aeb-110">元件</span><span class="sxs-lookup"><span data-stu-id="52aeb-110">Component</span></span>|<span data-ttu-id="52aeb-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="52aeb-111">SQLEngine</span></span>|  
|<span data-ttu-id="52aeb-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="52aeb-112">Symbolic Name</span></span>|<span data-ttu-id="52aeb-113">DBCC_ALLOCATION_SUMMARY_PER_FILE</span><span class="sxs-lookup"><span data-stu-id="52aeb-113">DBCC_ALLOCATION_SUMMARY_PER_FILE</span></span>|  
|<span data-ttu-id="52aeb-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="52aeb-114">Message Text</span></span>|<span data-ttu-id="52aeb-115">檔案 FILE。</span><span class="sxs-lookup"><span data-stu-id="52aeb-115">File FILE.</span></span> <span data-ttu-id="52aeb-116">範圍數目 = EXTENTS，使用的頁面 = USED_PAGES，保留的頁面 = RESERVED_PAGES。</span><span class="sxs-lookup"><span data-stu-id="52aeb-116">Number of extents = EXTENTS, used pages = USED_PAGES, reserved pages = RESERVED_PAGES.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="52aeb-117">說明</span><span class="sxs-lookup"><span data-stu-id="52aeb-117">Explanation</span></span>  
 <span data-ttu-id="52aeb-118">這項資訊是 DBCC CHECKALLOC 命令輸出的一部分，</span><span class="sxs-lookup"><span data-stu-id="52aeb-118">This information is part of the output from the DBCC CHECKALLOC command.</span></span> <span data-ttu-id="52aeb-119">也是指定資料庫中已配置範圍、已使用頁面和已保留頁面的個別檔案摘要資訊。</span><span class="sxs-lookup"><span data-stu-id="52aeb-119">This information is the per-file summary of allocated extents, used pages, and reserved pages for the specified database.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="52aeb-120">使用者動作</span><span class="sxs-lookup"><span data-stu-id="52aeb-120">User Action</span></span>  
 <span data-ttu-id="52aeb-121">None</span><span class="sxs-lookup"><span data-stu-id="52aeb-121">None</span></span>  
  
  
