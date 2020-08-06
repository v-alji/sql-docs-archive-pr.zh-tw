---
title: MSSQLSERVER_2593 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 2593 (Database Engine error)
ms.assetid: 2e25bc43-606a-40de-8b87-3b55b96f4a91
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ecd231f38fbb36e2f98a1e9ce254165002bb56e2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687909"
---
# <a name="mssqlserver_2593"></a><span data-ttu-id="1e799-102">MSSQLSERVER_2593</span><span class="sxs-lookup"><span data-stu-id="1e799-102">MSSQLSERVER_2593</span></span>
    
## <a name="details"></a><span data-ttu-id="1e799-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="1e799-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="1e799-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="1e799-104">Product Name</span></span>|<span data-ttu-id="1e799-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="1e799-105">SQL Server</span></span>|  
|<span data-ttu-id="1e799-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="1e799-106">Event ID</span></span>|<span data-ttu-id="1e799-107">2593</span><span class="sxs-lookup"><span data-stu-id="1e799-107">2593</span></span>|  
|<span data-ttu-id="1e799-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="1e799-108">Event Source</span></span>|<span data-ttu-id="1e799-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="1e799-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="1e799-110">元件</span><span class="sxs-lookup"><span data-stu-id="1e799-110">Component</span></span>|<span data-ttu-id="1e799-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="1e799-111">SQLEngine</span></span>|  
|<span data-ttu-id="1e799-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="1e799-112">Symbolic Name</span></span>|<span data-ttu-id="1e799-113">DBCC_OBJECT_ROW_PAGE_SUMMARY</span><span class="sxs-lookup"><span data-stu-id="1e799-113">DBCC_OBJECT_ROW_PAGE_SUMMARY</span></span>|  
|<span data-ttu-id="1e799-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="1e799-114">Message Text</span></span>|<span data-ttu-id="1e799-115">物件 'OBJECT' 在 PAGECOUNT 頁面中有 ROWCOUNT 個資料列。</span><span class="sxs-lookup"><span data-stu-id="1e799-115">There are ROWCOUNT rows in PAGECOUNT pages for object 'OBJECT'.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="1e799-116">說明</span><span class="sxs-lookup"><span data-stu-id="1e799-116">Explanation</span></span>  
 <span data-ttu-id="1e799-117">這則訊息是 DBCC CHECKALLOC 以外所有 DBCC 檢查傳回之參考用輸出的一部分，而且它會指出指定之物件的資料列和頁面計數。</span><span class="sxs-lookup"><span data-stu-id="1e799-117">This message is part of the informational output that is returned by all DBCC checks, except DBCC CHECKALLOC, and indicates the row and page counts for a specified object.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="1e799-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="1e799-118">User Action</span></span>  
 <span data-ttu-id="1e799-119">None</span><span class="sxs-lookup"><span data-stu-id="1e799-119">None</span></span>  
  
  
