---
title: 異動複寫的發行項選項 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- articles [SQL Server replication], transactional replication options
- transactional replication, article options
ms.assetid: 3469b185-0ea5-4690-a71c-717230d886b6
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 1cc13a3d11e35ed47eac4ff401fb8b7cb607b32b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596639"
---
# <a name="article-options-for-transactional-replication"></a><span data-ttu-id="d18e9-102">異動複寫的發行項選項</span><span class="sxs-lookup"><span data-stu-id="d18e9-102">Article Options for Transactional Replication</span></span>
  <span data-ttu-id="d18e9-103">針對交易式發行集中的發行項提供了一些選項。</span><span class="sxs-lookup"><span data-stu-id="d18e9-103">There are a number of options for articles in transactional publications.</span></span> <span data-ttu-id="d18e9-104">使用異動複寫，您可以執行下列項目：</span><span class="sxs-lookup"><span data-stu-id="d18e9-104">With transactional replication, you can do the following:</span></span>  
  
-   <span data-ttu-id="d18e9-105">指定變更從「發行者」傳播到「訂閱者」的方式。</span><span class="sxs-lookup"><span data-stu-id="d18e9-105">Specify how changes are propagated from the Publisher to Subscribers.</span></span> <span data-ttu-id="d18e9-106">如需詳細資訊，請參閱[指定交易式發行項變更的傳播方式](transactional-articles-specify-how-changes-are-propagated.md)。</span><span class="sxs-lookup"><span data-stu-id="d18e9-106">For more information, see [Specify How Changes Are Propagated for Transactional Articles](transactional-articles-specify-how-changes-are-propagated.md).</span></span>  
  
-   <span data-ttu-id="d18e9-107">指定複寫預存程序的執行。</span><span class="sxs-lookup"><span data-stu-id="d18e9-107">Specify that the execution of a stored procedure be replicated.</span></span> <span data-ttu-id="d18e9-108">針對會影響大量資料的維護導向預存程序複寫結果時很有用。</span><span class="sxs-lookup"><span data-stu-id="d18e9-108">This is useful in replicating the results of maintenance-oriented stored procedures that affect large amounts of data.</span></span> <span data-ttu-id="d18e9-109">如需詳細資訊，請參閱 [Publishing Stored Procedure Execution in Transactional Replication](publishing-stored-procedure-execution-in-transactional-replication.md)。</span><span class="sxs-lookup"><span data-stu-id="d18e9-109">For more information, see [Publishing Stored Procedure Execution in Transactional Replication](publishing-stored-procedure-execution-in-transactional-replication.md).</span></span>  
  
-   <span data-ttu-id="d18e9-110">指定結構描述選項，如條件約束和觸發程序是否複製到訂閱者。</span><span class="sxs-lookup"><span data-stu-id="d18e9-110">Specify schema options, such as whether constraints and triggers are copied to the Subscriber.</span></span> <span data-ttu-id="d18e9-111">如需詳細資訊，請參閱 [指定結構描述選項](../publish/specify-schema-options.md)。</span><span class="sxs-lookup"><span data-stu-id="d18e9-111">For more information, see [Specify Schema Options](../publish/specify-schema-options.md).</span></span>  
  
-   <span data-ttu-id="d18e9-112">使用資料列篩選與資料行篩選。</span><span class="sxs-lookup"><span data-stu-id="d18e9-112">Use row filters and column filters.</span></span> <span data-ttu-id="d18e9-113">篩選資料表發行項可讓您建立即將發行的資料分割。</span><span class="sxs-lookup"><span data-stu-id="d18e9-113">Filtering table articles enables you to create partitions of data to be published.</span></span> <span data-ttu-id="d18e9-114">如需詳細資訊，請參閱[篩選發行的資料](../publish/filter-published-data.md)。</span><span class="sxs-lookup"><span data-stu-id="d18e9-114">For more information, see [Filter Published Data](../publish/filter-published-data.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d18e9-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d18e9-115">See Also</span></span>  
 [<span data-ttu-id="d18e9-116">發行資料和資料庫物件</span><span class="sxs-lookup"><span data-stu-id="d18e9-116">Publish Data and Database Objects</span></span>](../publish/publish-data-and-database-objects.md)  
  
  
