---
title: MSSQLSERVER_10737 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 10737 (Database Engine error)
ms.assetid: 208af6ed-b271-4ab8-803e-7666025385c8
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: df8a4de014552d3aca00b3eb244f7ff8df56756b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598443"
---
# <a name="mssqlserver_10737"></a><span data-ttu-id="72837-102">MSSQLSERVER_10737</span><span class="sxs-lookup"><span data-stu-id="72837-102">MSSQLSERVER_10737</span></span>
    
## <a name="details"></a><span data-ttu-id="72837-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="72837-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="72837-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="72837-104">Product Name</span></span>|<span data-ttu-id="72837-105">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="72837-105">MSSQLSERVER</span></span>|  
|<span data-ttu-id="72837-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="72837-106">Event ID</span></span>|<span data-ttu-id="72837-107">10737</span><span class="sxs-lookup"><span data-stu-id="72837-107">10737</span></span>|  
|<span data-ttu-id="72837-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="72837-108">Event Source</span></span>|<span data-ttu-id="72837-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="72837-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="72837-110">元件</span><span class="sxs-lookup"><span data-stu-id="72837-110">Component</span></span>|<span data-ttu-id="72837-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="72837-111">SQLEngine</span></span>|  
|<span data-ttu-id="72837-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="72837-112">Symbolic Name</span></span>|<span data-ttu-id="72837-113">REBUILD_PARTITION_ALL_NOT_SPECIFIED</span><span class="sxs-lookup"><span data-stu-id="72837-113">REBUILD_PARTITION_ALL_NOT_SPECIFIED</span></span>|  
|<span data-ttu-id="72837-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="72837-114">Message Text</span></span>|<span data-ttu-id="72837-115">在 ALTER TABLE REBUILD 或 ALTER INDEX REBUILD 陳述式中，如果在 DATA_COMPRESSION 子句中指定了分割區，就必須指定 PARTITION=ALL。</span><span class="sxs-lookup"><span data-stu-id="72837-115">In an ALTER TABLE REBUILD or ALTER INDEX REBUILD statement, when a partition is specified in a DATA_COMPRESSION clause, PARTITION=ALL must be specified.</span></span> <span data-ttu-id="72837-116">PARTITION=ALL 子句是用來強調即將重建資料表或索引的所有分割區，即使 DATA_COMPRESSION 子句中只有指定子集也一樣。</span><span class="sxs-lookup"><span data-stu-id="72837-116">The PARTITION=ALL clause is used to reinforce that all partitions of the table or index will be rebuilt, even if only a subset is specified in the DATA_COMPRESSION clause.</span></span>|  
  
## <a name="user-action"></a><span data-ttu-id="72837-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="72837-117">User Action</span></span>  
 <span data-ttu-id="72837-118">將 PARTITION=ALL 子句加入至 ALTER TABLE 或 ALTER INDEX 陳述式。</span><span class="sxs-lookup"><span data-stu-id="72837-118">Add the PARTITION=ALL clause to the ALTER TABLE or ALTER INDEX statement.</span></span> <span data-ttu-id="72837-119">或者，若要重建特定分割區，請使用 REBUILD PARTITION = \<partition-number-expr> WITH (DATA_COMPRESSION={ON | OFF})。</span><span class="sxs-lookup"><span data-stu-id="72837-119">Or, to rebuild a specific partition, use REBUILD PARTITION = \<partition-number-expr> WITH (DATA_COMPRESSION={ON | OFF}).</span></span>  
  
  
