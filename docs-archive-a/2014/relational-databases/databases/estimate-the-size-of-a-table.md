---
title: 估計資料表的大小 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- pages [SQL Server], space
- space [SQL Server], tables
- row size [SQL Server]
- size [SQL Server], tables
- column size [SQL Server]
- predicting table size [SQL Server]
- table size [SQL Server]
- estimating table size
- clustered indexes, table size
- disk space [SQL Server], tables
- space allocation [SQL Server], table size
- designing databases [SQL Server], estimating size
- reserved free rows per page [SQL Server]
- calculating table size
ms.assetid: 15c17c92-616f-402e-894b-907a296efe5f
author: stevestein
ms.author: sstein
ms.openlocfilehash: 4a16d439d3b2bc59479866b7bb36295ec4fc8950
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705158"
---
# <a name="estimate-the-size-of-a-table"></a><span data-ttu-id="78c77-102">估計資料表的大小</span><span class="sxs-lookup"><span data-stu-id="78c77-102">Estimate the Size of a Table</span></span>
  <span data-ttu-id="78c77-103">您可以使用下列步驟來估計將資料儲存於資料表中所需的空間量：</span><span class="sxs-lookup"><span data-stu-id="78c77-103">You can use the following steps to estimate the amount of space required to store data in a table:</span></span>  
  
1.  <span data-ttu-id="78c77-104">遵循 [估計堆積的大小](estimate-the-size-of-a-heap.md) 或 [估計叢集索引的大小](estimate-the-size-of-a-clustered-index.md)中的指示，來計算堆積或叢集索引所需的空間。</span><span class="sxs-lookup"><span data-stu-id="78c77-104">Calculate the space required for the heap or clustered index following the instructions in [Estimate the Size of a Heap](estimate-the-size-of-a-heap.md) or [Estimate the Size of a Clustered Index](estimate-the-size-of-a-clustered-index.md).</span></span>  
  
2.  <span data-ttu-id="78c77-105">對於每個非叢集索引，請遵循 [估計非叢集索引的大小](estimate-the-size-of-a-nonclustered-index.md)中的指示，來計算其所需的空間。</span><span class="sxs-lookup"><span data-stu-id="78c77-105">For each nonclustered index, calculate the space required for it by following the instructions in [Estimate the Size of a Nonclustered Index](estimate-the-size-of-a-nonclustered-index.md).</span></span>  
  
3.  <span data-ttu-id="78c77-106">新增步驟 1 和 2 中計算的值。</span><span class="sxs-lookup"><span data-stu-id="78c77-106">Add the values calculated in steps 1 and 2.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78c77-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="78c77-107">See Also</span></span>  
 <span data-ttu-id="78c77-108">[估計資料庫的大小](estimate-the-size-of-a-database.md) </span><span class="sxs-lookup"><span data-stu-id="78c77-108">[Estimate the Size of a Database](estimate-the-size-of-a-database.md) </span></span>  
 <span data-ttu-id="78c77-109">[估計堆積的大小](estimate-the-size-of-a-heap.md) </span><span class="sxs-lookup"><span data-stu-id="78c77-109">[Estimate the Size of a Heap](estimate-the-size-of-a-heap.md) </span></span>  
 <span data-ttu-id="78c77-110">[估計叢集索引的大小](estimate-the-size-of-a-clustered-index.md) </span><span class="sxs-lookup"><span data-stu-id="78c77-110">[Estimate the Size of a Clustered Index](estimate-the-size-of-a-clustered-index.md) </span></span>  
 [<span data-ttu-id="78c77-111">估計非叢集索引的大小</span><span class="sxs-lookup"><span data-stu-id="78c77-111">Estimate the Size of a Nonclustered Index</span></span>](estimate-the-size-of-a-nonclustered-index.md)  
  
  
