---
title: 篩選合併式複寫之發行的資料 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- merge replication [SQL Server replication], filtering published data
- replication [SQL Server], filtering published data
ms.assetid: 46c5023d-7a3b-4455-becc-e159fcb5d6c4
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ad9ad45a64f57a6bef8255373180ea943af9893f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584446"
---
# <a name="filter-published-data-for-merge-replication"></a><span data-ttu-id="ef56a-102">篩選合併式複寫之發行的資料</span><span class="sxs-lookup"><span data-stu-id="ef56a-102">Filter Published Data for Merge Replication</span></span>
  <span data-ttu-id="ef56a-103">除了可以使用其他複寫類型定義的靜態資料列篩選和資料行篩選之外，合併式複寫還提供了參數化資料列篩選器和聯結篩選。</span><span class="sxs-lookup"><span data-stu-id="ef56a-103">In addition to the static row filters and column filters you can define with other types of replication, merge replication offers parameterized row filters and join filters.</span></span> <span data-ttu-id="ef56a-104">如需靜態資料列篩選和資料行篩選的詳細資訊，請參閱[篩選發行的資料](../publish/filter-published-data.md)。</span><span class="sxs-lookup"><span data-stu-id="ef56a-104">For more information about static row filters and column filters, see [Filter Published Data](../publish/filter-published-data.md).</span></span>  
  
 <span data-ttu-id="ef56a-105">合併式複寫用於許多支援行動使用者的應用程式；這些應用程式通常具有大量的訂閱，且每個訂閱接收唯一的資料集。</span><span class="sxs-lookup"><span data-stu-id="ef56a-105">Merge replication is used in many applications that support mobile users; these applications usually have a large number of subscriptions with each subscription receiving a unique data set.</span></span> <span data-ttu-id="ef56a-106">參數化篩選與聯結篩選的組合允許管理員設定一個發行集 (或至多幾個發行集)，並向使用者提供不同的資料集，降低了建立多個發行集時所帶來的管理負擔。</span><span class="sxs-lookup"><span data-stu-id="ef56a-106">Parameterized filters combined with join filters allow an administrator to set up one publication (or at most a small number of publications) and yet provide different data sets to users, reducing the management overhead introduced by creating multiple publications.</span></span>  
  
-   <span data-ttu-id="ef56a-107">參數化篩選允許將不同資料分割傳送到不同「訂閱者」，而無需建立多個發行集。</span><span class="sxs-lookup"><span data-stu-id="ef56a-107">Parameterized filters allow different partitions of data to be sent to different Subscribers without requiring multiple publications to be created.</span></span> <span data-ttu-id="ef56a-108">例如，資料表可進行篩選，以便給定銷售代表的資料僅複寫至該代表。</span><span class="sxs-lookup"><span data-stu-id="ef56a-108">For example, a table can be filtered so that data for a given sales representative is replicated only to that representative.</span></span> <span data-ttu-id="ef56a-109">參數化篩選具有各種不同的選項，允許您修改篩選，以最佳化效能並使資料和應用程式需求的相符達到最佳。</span><span class="sxs-lookup"><span data-stu-id="ef56a-109">Parameterized filters have a variety of options that allow you to tailor filtering to optimize performance and best match your data and application requirements.</span></span> <span data-ttu-id="ef56a-110">如需詳細資訊，請參閱＜ [參數化資料列篩選器](parameterized-filters-parameterized-row-filters.md)＞。</span><span class="sxs-lookup"><span data-stu-id="ef56a-110">For more information, see [Parameterized Row Filters](parameterized-filters-parameterized-row-filters.md).</span></span>  
  
-   <span data-ttu-id="ef56a-111">聯結篩選通常配合參數化篩選使用，以將篩選擴充至相關聯的資料表 (也可與靜態篩選配合使用)。</span><span class="sxs-lookup"><span data-stu-id="ef56a-111">Join filters are typically used in conjunction with parameterized filters to extend filtering to related tables (they can also be used in conjunction with static filters).</span></span> <span data-ttu-id="ef56a-112">例如，銷售代表通常在其他資料表 (如客戶和訂單資料表) 中也有資料。</span><span class="sxs-lookup"><span data-stu-id="ef56a-112">For example, the sales representative typically has data in other tables such as customer and order tables.</span></span> <span data-ttu-id="ef56a-113">這些資料可進行篩選，這樣銷售代表便僅接收其客戶和客戶訂單的相關資料。</span><span class="sxs-lookup"><span data-stu-id="ef56a-113">This data can be filtered so the sales representative receives only the data on her customers and her customers' orders.</span></span> <span data-ttu-id="ef56a-114">如需相關資訊，請參閱 [Join Filters](join-filters.md)。</span><span class="sxs-lookup"><span data-stu-id="ef56a-114">For more information, see [Join Filters](join-filters.md).</span></span>  
  
 <span data-ttu-id="ef56a-115">篩選不得包含複寫識別資料列所使用的 `rowguidcol`。</span><span class="sxs-lookup"><span data-stu-id="ef56a-115">A filter must not include the `rowguidcol` used by replication to identify rows.</span></span> <span data-ttu-id="ef56a-116">根據預設，這是在您設定合併式複寫時加入，且名稱為 **rowguid**的資料行。</span><span class="sxs-lookup"><span data-stu-id="ef56a-116">By default this is the column added at the time you set up merge replication and is named **rowguid**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef56a-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ef56a-117">See Also</span></span>  
 [<span data-ttu-id="ef56a-118">發行資料和資料庫物件</span><span class="sxs-lookup"><span data-stu-id="ef56a-118">Publish Data and Database Objects</span></span>](../publish/publish-data-and-database-objects.md)  
  
  
