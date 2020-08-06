---
title: MSSQLSERVER_7711 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 7711 (Database Engine error)
ms.assetid: a5c7cd6e-18d6-47ef-902b-db9dd64bba34
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e29b2ea993e8e5332ef03b05f628dc791e20aba9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596019"
---
# <a name="mssqlserver_7711"></a><span data-ttu-id="7293f-102">MSSQLSERVER_7711</span><span class="sxs-lookup"><span data-stu-id="7293f-102">MSSQLSERVER_7711</span></span>
    
## <a name="details"></a><span data-ttu-id="7293f-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="7293f-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="7293f-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="7293f-104">Product Name</span></span>|<span data-ttu-id="7293f-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="7293f-105">SQL Server</span></span>|  
|<span data-ttu-id="7293f-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="7293f-106">Event ID</span></span>|<span data-ttu-id="7293f-107">7711</span><span class="sxs-lookup"><span data-stu-id="7293f-107">7711</span></span>|  
|<span data-ttu-id="7293f-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="7293f-108">Event Source</span></span>|<span data-ttu-id="7293f-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="7293f-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="7293f-110">元件</span><span class="sxs-lookup"><span data-stu-id="7293f-110">Component</span></span>|<span data-ttu-id="7293f-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="7293f-111">SQLEngine</span></span>|  
|<span data-ttu-id="7293f-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="7293f-112">Symbolic Name</span></span>|<span data-ttu-id="7293f-113">PRT_RANGE_OVERLAP</span><span class="sxs-lookup"><span data-stu-id="7293f-113">PRT_RANGE_OVERLAP</span></span>|  
|<span data-ttu-id="7293f-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="7293f-114">Message Text</span></span>|<span data-ttu-id="7293f-115">資料表或索引或是它的其中一個資料分割已指定 DATA_COMPRESSION 選項一次以上。</span><span class="sxs-lookup"><span data-stu-id="7293f-115">The DATA_COMPRESSION option was specified more than once for the table or index or one of its partitions.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="7293f-116">說明</span><span class="sxs-lookup"><span data-stu-id="7293f-116">Explanation</span></span>  
 <span data-ttu-id="7293f-117">下列其中一個陳述式中的 DATA_COMPRESSION 選項發生錯誤：</span><span class="sxs-lookup"><span data-stu-id="7293f-117">An error occurred in the DATA_COMPRESSION option in one of the following statements:</span></span>  
  
-   <span data-ttu-id="7293f-118">CREATE TABLE</span><span class="sxs-lookup"><span data-stu-id="7293f-118">CREATE TABLE</span></span>  
  
-   <span data-ttu-id="7293f-119">ALTER TABLE</span><span class="sxs-lookup"><span data-stu-id="7293f-119">ALTER TABLE</span></span>  
  
-   <span data-ttu-id="7293f-120">CREATE INDEX</span><span class="sxs-lookup"><span data-stu-id="7293f-120">CREATE INDEX</span></span>  
  
-   <span data-ttu-id="7293f-121">ALTER INDEX</span><span class="sxs-lookup"><span data-stu-id="7293f-121">ALTER INDEX</span></span>  
  
 <span data-ttu-id="7293f-122">如果分割了引用的資料表或索引，則表示其中至少一個分割區已列出 DATA_COMPRESSION 選項一次以上。</span><span class="sxs-lookup"><span data-stu-id="7293f-122">If the table or index cited is partitioned, the DATA_COMPRESSION option was listed more than one time for at least one of the partitions.</span></span> <span data-ttu-id="7293f-123">如果此資料表或索引未分割，則表示 DATA_COMPRESSION 選項已經引用一次以上。</span><span class="sxs-lookup"><span data-stu-id="7293f-123">If the table or index is not partitioned, the DATA_COMPRESSION option was cited more than one time.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="7293f-124">使用者動作</span><span class="sxs-lookup"><span data-stu-id="7293f-124">User Action</span></span>  
 <span data-ttu-id="7293f-125">如果是已分割的資料表或索引，請確定每一個分割區只指定 DATA_COMPRESSION 選項一次。</span><span class="sxs-lookup"><span data-stu-id="7293f-125">For a partitioned table or index, make sure that the DATA_COMPRESSION option is specified only one time for each partition.</span></span> <span data-ttu-id="7293f-126">如果是未分割的資料表或索引，只能在陳述式中使用 DATA_COMPRESSION 選項一次。</span><span class="sxs-lookup"><span data-stu-id="7293f-126">For a table or index that is not partitioned, use the DATA_COMPRESSION option only one time in the statement.</span></span>  
  
  
