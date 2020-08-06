---
title: 複寫發行模型概觀 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- replication [SQL Server], publishing model
- subscriptions [SQL Server replication], about subscriptions
- articles [SQL Server replication]
- publications [SQL Server replication]
- Publishers [SQL Server replication], about Publishers
- Subscribers [SQL Server replication]
- Distributors [SQL Server replication], about Distributors
- Subscribers [SQL Server replication], about Subscribers
- articles [SQL Server replication], about articles
- publications [SQL Server replication], about publications
- Distributors [SQL Server replication]
ms.assetid: b9567832-e6a8-45b2-a3ed-ea12aa002f4b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: a6b6bd555cf87a8dcb334db2c44e17ed99aa845d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596655"
---
# <a name="replication-publishing-model-overview"></a><span data-ttu-id="38595-102">複寫發行模型概觀</span><span class="sxs-lookup"><span data-stu-id="38595-102">Replication Publishing Model Overview</span></span>
  <span data-ttu-id="38595-103">複寫使用出版業比喻來表示複寫拓撲中的元件，包括發行者、散發者、訂閱者、發行集、發行項和訂閱。</span><span class="sxs-lookup"><span data-stu-id="38595-103">Replication uses a publishing industry metaphor to represent the components in a replication topology, which include Publisher, Distributor, Subscribers, publications, articles, and subscriptions.</span></span> <span data-ttu-id="38595-104">從雜誌的角度設想一下 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 複寫非常有幫助：</span><span class="sxs-lookup"><span data-stu-id="38595-104">It is helpful to think of [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] replication in terms of a magazine:</span></span>

-   <span data-ttu-id="38595-105">雜誌發行者可產生一個或多個發行集</span><span class="sxs-lookup"><span data-stu-id="38595-105">A magazine publisher produces one or more publications</span></span>

-   <span data-ttu-id="38595-106">發行集包含發行項</span><span class="sxs-lookup"><span data-stu-id="38595-106">A publication contains articles</span></span>

-   <span data-ttu-id="38595-107">發行者直接或使用散發者散發雜誌</span><span class="sxs-lookup"><span data-stu-id="38595-107">The publisher either distributes the magazine directly or uses a distributor</span></span>

-   <span data-ttu-id="38595-108">訂閱者接收他們已訂閱的發行集</span><span class="sxs-lookup"><span data-stu-id="38595-108">Subscribers receive publications to which they have subscribed</span></span>

 <span data-ttu-id="38595-109">儘管雜誌比喻對於理解複寫非常有用，但須注意， [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 複寫還包含此比喻中未表示的功能，特別是「訂閱者」進行更新以及「發行者」將累加變更傳送至發行集中發行項的能力。</span><span class="sxs-lookup"><span data-stu-id="38595-109">Although the magazine metaphor is useful for understanding replication, it is important to note that [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] replication includes functionality that is not represented in this metaphor, particularly the ability for a Subscriber to make updates and for a Publisher to send out incremental changes to the articles in a publication.</span></span>

 <span data-ttu-id="38595-110">*「複寫拓撲」* 定義伺服器與資料副本間的關聯性，並且用以明定伺服器之間資料流動方式的邏輯。</span><span class="sxs-lookup"><span data-stu-id="38595-110">A *replication topology* defines the relationship between servers and copies of data and clarifies the logic that determines how data flows between servers.</span></span> <span data-ttu-id="38595-111">還有數項複寫處理 (稱為 *「代理程式」* ) 負責「發行者」與「訂閱者」之間的資料複製及移動。</span><span class="sxs-lookup"><span data-stu-id="38595-111">There are several replication processes (referred to as *agents*) that are responsible for copying and moving data between the Publisher and Subscribers.</span></span> <span data-ttu-id="38595-112">下圖提供了複寫所涉及之元件與處理的概觀。</span><span class="sxs-lookup"><span data-stu-id="38595-112">The following illustration is an overview of the components and processes involved in replication.</span></span>

 <span data-ttu-id="38595-113">![複寫元件和資料流程](../media/replintro1.gif "複寫元件和資料流程")</span><span class="sxs-lookup"><span data-stu-id="38595-113">![Replication components and data flow](../media/replintro1.gif "Replication components and data flow")</span></span>

## <a name="publisher"></a><span data-ttu-id="38595-114">發行者</span><span class="sxs-lookup"><span data-stu-id="38595-114">Publisher</span></span>
 <span data-ttu-id="38595-115">「發行者」是一個可透過複寫使資料可用於其他位置的資料庫執行個體。</span><span class="sxs-lookup"><span data-stu-id="38595-115">The Publisher is a database instance that makes data available to other locations through replication.</span></span> <span data-ttu-id="38595-116">發行者可以有一個或多個發行集，每個發行集各定義一組邏輯相關的物件及要複寫的資料。</span><span class="sxs-lookup"><span data-stu-id="38595-116">The Publisher can have one or more publications, each defining a logically related set of objects and data to replicate.</span></span>

## <a name="distributor"></a><span data-ttu-id="38595-117">散發者</span><span class="sxs-lookup"><span data-stu-id="38595-117">Distributor</span></span>
 <span data-ttu-id="38595-118">「散發者」是一個作為儲存器的資料庫執行個體，用於儲存與一個或多個「發行者」相關聯的複寫特定資料。</span><span class="sxs-lookup"><span data-stu-id="38595-118">The Distributor is a database instance that acts as a store for replication specific data associated with one or more Publishers.</span></span> <span data-ttu-id="38595-119">每個發行者都會關聯於散發者端的單一資料庫 (稱為散發資料庫)。</span><span class="sxs-lookup"><span data-stu-id="38595-119">Each Publisher is associated with a single database (known as a distribution database) at the Distributor.</span></span> <span data-ttu-id="38595-120">散發資料庫儲存複寫狀態資料和有關發行集的中繼資料，有時它還作為從「發行者」移動至「訂閱者」之資料的佇列。</span><span class="sxs-lookup"><span data-stu-id="38595-120">The distribution database stores replication status data, metadata about the publication, and, in some cases, acts as a queue for data moving from the Publisher to the Subscribers.</span></span> <span data-ttu-id="38595-121">在許多情況下，單一資料庫伺服器執行個體可同時作為「發行者」和「散發者」，</span><span class="sxs-lookup"><span data-stu-id="38595-121">In many cases, a single database server instance acts as both the Publisher and the Distributor.</span></span> <span data-ttu-id="38595-122">稱之為 *「本機散發者」* 。</span><span class="sxs-lookup"><span data-stu-id="38595-122">This is known as a *local Distributor*.</span></span> <span data-ttu-id="38595-123">當在單獨的資料庫伺服器執行個體上設定「發行者」與「散發者」時，「散發者」稱為 *「遠端散發者」* 。</span><span class="sxs-lookup"><span data-stu-id="38595-123">When the Publisher and the Distributor are configured on separate database server instances, the Distributor is known as a *remote Distributor*.</span></span>

## <a name="subscribers"></a><span data-ttu-id="38595-124">訂閱者</span><span class="sxs-lookup"><span data-stu-id="38595-124">Subscribers</span></span>
 <span data-ttu-id="38595-125">「訂閱者」是接收已複寫資料的資料庫執行個體。</span><span class="sxs-lookup"><span data-stu-id="38595-125">A Subscriber is a database instance that receives replicated data.</span></span> <span data-ttu-id="38595-126">訂閱者可以接收多個發行者和發行集的資料。</span><span class="sxs-lookup"><span data-stu-id="38595-126">A Subscriber can receive data from multiple Publishers and publications.</span></span> <span data-ttu-id="38595-127">依所選的複寫類型而定，訂閱者也可以將資料變更傳回發行者，或將資料重新發行到其他訂閱者。</span><span class="sxs-lookup"><span data-stu-id="38595-127">Depending on the type of replication chosen, the Subscriber can also pass data changes back to the Publisher or republish the data to other Subscribers.</span></span>

## <a name="article"></a><span data-ttu-id="38595-128">發行項</span><span class="sxs-lookup"><span data-stu-id="38595-128">Article</span></span>
 <span data-ttu-id="38595-129">用以識別包含在發行集中資料庫物件的發行項。</span><span class="sxs-lookup"><span data-stu-id="38595-129">An article identifies a database object that is included in a publication.</span></span> <span data-ttu-id="38595-130">發行集可包含不同類型的發行項，其中包括資料表、檢視、預存程序和其他物件。</span><span class="sxs-lookup"><span data-stu-id="38595-130">A publication can contain different types of articles, including tables, views, stored procedures, and other objects.</span></span> <span data-ttu-id="38595-131">當您將資料表當作發行項來發行時，您可以利用篩選來限制傳送給訂閱者之資料的資料行和資料列。</span><span class="sxs-lookup"><span data-stu-id="38595-131">When tables are published as articles, filters can be used to restrict the columns and rows of the data sent to Subscribers.</span></span>

## <a name="publication"></a><span data-ttu-id="38595-132">發行集</span><span class="sxs-lookup"><span data-stu-id="38595-132">Publication</span></span>
 <span data-ttu-id="38595-133">發行集是單一資料庫之一個或多個發行項的集合。</span><span class="sxs-lookup"><span data-stu-id="38595-133">A publication is a collection of one or more articles from one database.</span></span> <span data-ttu-id="38595-134">將多個發行項分組到單一發行集，會比較容易指定一組當作一個單元來複寫的邏輯相關之資料庫物件和資料。</span><span class="sxs-lookup"><span data-stu-id="38595-134">The grouping of multiple articles into a publication makes it easier to specify a logically related set of database objects and data that are replicated as a unit.</span></span>

## <a name="subscription"></a><span data-ttu-id="38595-135">訂用帳戶</span><span class="sxs-lookup"><span data-stu-id="38595-135">Subscription</span></span>
 <span data-ttu-id="38595-136">訂閱是對要傳遞給「訂閱者」之發行集副本的要求。</span><span class="sxs-lookup"><span data-stu-id="38595-136">A subscription is a request for a copy of a publication to be delivered to a Subscriber.</span></span> <span data-ttu-id="38595-137">訂閱會定義將在何時、何處收到什麼發行集。</span><span class="sxs-lookup"><span data-stu-id="38595-137">The subscription defines what publication will be received, where, and when.</span></span> <span data-ttu-id="38595-138">訂閱的類型有兩種：發送和提取。</span><span class="sxs-lookup"><span data-stu-id="38595-138">There are two types of subscriptions: push and pull.</span></span> <span data-ttu-id="38595-139">如需發送和提取訂閱的詳細資訊，請參閱[訂閱發行集](../subscribe-to-publications.md)。</span><span class="sxs-lookup"><span data-stu-id="38595-139">For more information about push and pull subscriptions, see [Subscribe to Publications](../subscribe-to-publications.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="38595-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="38595-140">See Also</span></span>
 <span data-ttu-id="38595-141">複寫[代理程式總覽](../agents/replication-agents-overview.md)[類型的](../types-of-replication.md)複寫[設定複寫以進行 AlwaysOn 可用性群組 (SQL Server) ](../../../database-engine/availability-groups/windows/always-on-availability-groups-sql-server.md) [維護 AlwaysOn 發行集資料庫 &#40;](../../../database-engine/availability-groups/windows/maintaining-an-always-on-publication-database-sql-server.md) SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="38595-141">[Replication Agents Overview](../agents/replication-agents-overview.md) [Types of Replication](../types-of-replication.md) [Configure Replication for AlwaysOn Availability Groups (SQL Server)](../../../database-engine/availability-groups/windows/always-on-availability-groups-sql-server.md) [Maintaining an AlwaysOn Publication Database &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/maintaining-an-always-on-publication-database-sql-server.md)</span></span>


