---
title: 關於變更追蹤 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- data changes [SQL Server]
- tracking data changes [SQL Server]
- change tracking [SQL Server], about change tracking
- change tracking [SQL Server]
- data [SQL Server], changing
ms.assetid: 5e0ef05a-8317-4c98-be20-b19d4cd78f12
author: rothja
ms.author: jroth
ms.openlocfilehash: 4e8a817421aeca7906d31e4a70c25a12b6af7c0d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597695"
---
# <a name="about-change-tracking-sql-server"></a><span data-ttu-id="99471-102">關於變更追蹤 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="99471-102">About Change Tracking (SQL Server)</span></span>
  <span data-ttu-id="99471-103">變更追蹤是為應用程式提供高效率變更追蹤機制的輕量型方案。</span><span class="sxs-lookup"><span data-stu-id="99471-103">Change tracking is a lightweight solution that provides an efficient change tracking mechanism for applications.</span></span> <span data-ttu-id="99471-104">一般而言，若要讓應用程式查詢對資料庫中之資料所做的變更並且存取與這些變更有關的資訊，應用程式開發人員就必須實作自訂變更追蹤機制。</span><span class="sxs-lookup"><span data-stu-id="99471-104">Typically, to enable applications to query for changes to data in a database and access information that is related to the changes, application developers had to implement custom change tracking mechanisms.</span></span> <span data-ttu-id="99471-105">建立這些機制通常牽涉到很多工作，而且經常涉及使用觸發程式、資料 `timestamp` 行、用來儲存追蹤資訊的新資料表和自訂清除進程的組合。</span><span class="sxs-lookup"><span data-stu-id="99471-105">Creating these mechanisms usually involved a lot of work and frequently involved using a combination of triggers, `timestamp` columns, new tables to store tracking information, and custom cleanup processes.</span></span>  
  
 <span data-ttu-id="99471-106">對於有關變更的所需資訊量，不同的應用程式類型具有不同的需求。</span><span class="sxs-lookup"><span data-stu-id="99471-106">Different types of applications have different requirements for how much information they need about the changes.</span></span> <span data-ttu-id="99471-107">應用程式可以使用變更追蹤來回答下列有關已經對使用者資料表所做變更的問題：</span><span class="sxs-lookup"><span data-stu-id="99471-107">Applications can use change tracking to answer the following questions about the changes that have been made to a user table:</span></span>  
  
-   <span data-ttu-id="99471-108">使用者資料表的哪些資料列已經變更？</span><span class="sxs-lookup"><span data-stu-id="99471-108">What rows have changed for a user table?</span></span>  
  
    -   <span data-ttu-id="99471-109">只需要某個資料列已經變更的事實，而不需要該資料列變更多少次或任何中繼變更的值。</span><span class="sxs-lookup"><span data-stu-id="99471-109">Only the fact that a row has changed is required, not how many times the row has changed or the values of any intermediate changes.</span></span>  
  
    -   <span data-ttu-id="99471-110">您可以直接從追蹤的資料表中取得最新的資料。</span><span class="sxs-lookup"><span data-stu-id="99471-110">The latest data can be obtained directly from the table that is being tracked.</span></span>  
  
-   <span data-ttu-id="99471-111">某個資料列是否已經變更？</span><span class="sxs-lookup"><span data-stu-id="99471-111">Has a row changed?</span></span>  
  
    -   <span data-ttu-id="99471-112">在相同的交易中進行變更時，某個資料列已經變更的事實以及變更的相關資訊必須可用而且已記錄。</span><span class="sxs-lookup"><span data-stu-id="99471-112">The fact that a row has changed and information about the change must be available and recorded at the time that the change was made in the same transaction.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="99471-113">如果應用程式需要所做之所有變更的相關資訊以及變更之資料的中繼值，則使用異動資料擷取來取代變更追蹤可能會很適合。</span><span class="sxs-lookup"><span data-stu-id="99471-113">If an application requires information about all the changes that were made and the intermediate values of the changed data, using change data capture, instead of change tracking, might be appropriate.</span></span> <span data-ttu-id="99471-114">如需詳細資訊，請參閱[關於異動資料擷取 &#40;SQL Server&#41;](../track-changes/about-change-data-capture-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="99471-114">For more information, see [About Change Data Capture &#40;SQL Server&#41;](../track-changes/about-change-data-capture-sql-server.md).</span></span>  
  
## <a name="one-way-and-two-way-synchronization-applications"></a><span data-ttu-id="99471-115">單向和雙向同步處理應用程式</span><span class="sxs-lookup"><span data-stu-id="99471-115">One-Way and Two-Way Synchronization Applications</span></span>  
 <span data-ttu-id="99471-116">必須與 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 執行個體同步處理資料的應用程式必須能夠查詢變更。</span><span class="sxs-lookup"><span data-stu-id="99471-116">Applications that have to synchronize data with an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] must be able to query for changes.</span></span> <span data-ttu-id="99471-117">變更追蹤可當做單向和雙向同步處理應用程式的基礎。</span><span class="sxs-lookup"><span data-stu-id="99471-117">Change tracking can be used as a foundation for both one-way and two-way synchronization applications.</span></span>  
  
### <a name="one-way-synchronization-applications"></a><span data-ttu-id="99471-118">單向同步處理應用程式</span><span class="sxs-lookup"><span data-stu-id="99471-118">One-Way Synchronization Applications</span></span>  
 <span data-ttu-id="99471-119">您可以建立使用變更追蹤的單向同步處理應用程式 (例如用戶端或中層快取應用程式)。</span><span class="sxs-lookup"><span data-stu-id="99471-119">One-way synchronization applications, such as a client or mid-tier caching application, can be built that use change tracking.</span></span> <span data-ttu-id="99471-120">如下圖所示，快取應用程式會要求資料在 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 中儲存以及在其他資料存放區中快取。</span><span class="sxs-lookup"><span data-stu-id="99471-120">As shown in the following illustration, a caching application requires data to be stored in the [!INCLUDE[ssDE](../../includes/ssde-md.md)] and to be cached in other data stores.</span></span> <span data-ttu-id="99471-121">此應用程式必須能夠使用已經對資料庫資料表所做的任何變更，讓快取保持在最新狀態。</span><span class="sxs-lookup"><span data-stu-id="99471-121">The application must be able to keep the cache up-to-date with any changes that have been made to the database tables.</span></span> <span data-ttu-id="99471-122">沒有任何變更要傳回 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="99471-122">There are no changes to pass back to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
 <span data-ttu-id="99471-123">![顯示單向同步處理應用程式](../../database-engine/media/one-waysync.gif "顯示單向同步處理應用程式")</span><span class="sxs-lookup"><span data-stu-id="99471-123">![Shows one-way synchronization applications](../../database-engine/media/one-waysync.gif "Shows one-way synchronization applications")</span></span>  
  
### <a name="two-way-synchronization-applications"></a><span data-ttu-id="99471-124">雙向同步處理應用程式</span><span class="sxs-lookup"><span data-stu-id="99471-124">Two-Way Synchronization Applications</span></span>  
 <span data-ttu-id="99471-125">您也可以建立使用變更追蹤的雙向同步處理應用程式。</span><span class="sxs-lookup"><span data-stu-id="99471-125">Two-way synchronization applications can also be built that use change tracking.</span></span> <span data-ttu-id="99471-126">在這個狀況中， [!INCLUDE[ssDE](../../includes/ssde-md.md)] 執行個體中的資料會與一或多個資料存放區同步處理。</span><span class="sxs-lookup"><span data-stu-id="99471-126">In this scenario, the data in an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] is synchronized with one or more data stores.</span></span> <span data-ttu-id="99471-127">這些存放區中的資料可以更新，而且這些變更必須同步處理回 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="99471-127">The data in those stores can be updated and the changes must be synchronized back to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
 <span data-ttu-id="99471-128">![顯示雙向同步處理應用程式](../../database-engine/media/two-waysync.gif "顯示雙向同步處理應用程式")</span><span class="sxs-lookup"><span data-stu-id="99471-128">![Shows two-way synchronization applications](../../database-engine/media/two-waysync.gif "Shows two-way synchronization applications")</span></span>  
  
 <span data-ttu-id="99471-129">雙向同步處理應用程式有個很好的範例，那就是偶爾連接的應用程式。</span><span class="sxs-lookup"><span data-stu-id="99471-129">A good example of two-way synchronization application is an occasionally connected application.</span></span> <span data-ttu-id="99471-130">在這種應用程式中，用戶端應用程式會查詢並更新本機存放區。</span><span class="sxs-lookup"><span data-stu-id="99471-130">In this type of application, a client application queries and updates a local store.</span></span> <span data-ttu-id="99471-131">當用戶端與伺服器之間的連接可用時，應用程式就會與伺服器同步處理，而且變更的資料會雙向流動。</span><span class="sxs-lookup"><span data-stu-id="99471-131">When a connection is available between a client and server, the application will synchronize with a server, and changed data flows in both directions.</span></span>  
  
 <span data-ttu-id="99471-132">雙向同步處理應用程式必須能夠偵測衝突。</span><span class="sxs-lookup"><span data-stu-id="99471-132">The two-way synchronization applications must be able to detect conflicts.</span></span> <span data-ttu-id="99471-133">如果在同步處理期間，兩個資料存放區中的相同資料已變更，就會發生衝突。</span><span class="sxs-lookup"><span data-stu-id="99471-133">A conflict would occur if the same data was changed in both data stores in the time between synchronizations.</span></span> <span data-ttu-id="99471-134">透過偵測衝突的功能，應用程式就可以確保變更不會遺失。</span><span class="sxs-lookup"><span data-stu-id="99471-134">With the ability to detect conflicts, an application can make sure that changes are not lost.</span></span>  
  
## <a name="how-change-tracking-works"></a><span data-ttu-id="99471-135">變更追蹤的運作方式</span><span class="sxs-lookup"><span data-stu-id="99471-135">How Change Tracking Works</span></span>  
 <span data-ttu-id="99471-136">若要設定變更追蹤，您可以使用 DDL 陳述式或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="99471-136">To configure change tracking, you can use DDL statements or [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="99471-137">如需詳細資訊，請參閱 [啟用和停用變更追蹤 &#40;SQL Server&#41;](../track-changes/enable-and-disable-change-tracking-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="99471-137">For more information, see [Enable and Disable Change Tracking &#40;SQL Server&#41;](../track-changes/enable-and-disable-change-tracking-sql-server.md).</span></span> <span data-ttu-id="99471-138">若要追蹤變更，您必須先針對資料庫啟用變更追蹤，然後再針對該資料庫內要追蹤的資料表啟用變更追蹤。</span><span class="sxs-lookup"><span data-stu-id="99471-138">To track changes, change tracking must first be enabled for the database and then enabled for the tables that you want to track within that database.</span></span> <span data-ttu-id="99471-139">您不需要變更任何資料表定義，而且不會建立任何觸發程序。</span><span class="sxs-lookup"><span data-stu-id="99471-139">The table definition does not have to be changed in any way, and no triggers are created.</span></span>  
  
 <span data-ttu-id="99471-140">對資料表設定變更追蹤之後，任何會影響資料表內資料列的 DML 陳述式都會讓每一個修改之資料列的變更追蹤資訊得以記錄下來。</span><span class="sxs-lookup"><span data-stu-id="99471-140">After change tracking is configured for a table, any DML statement that affects rows in the table will cause change tracking information for each modified row to be recorded.</span></span> <span data-ttu-id="99471-141">若要查詢已經變更的資料列以及取得有關變更的資訊，您可以使用 [變更追蹤函數](/sql/relational-databases/system-functions/change-tracking-functions-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="99471-141">To query for the rows that have changed and to obtain information about the changes, you can use [change tracking functions](/sql/relational-databases/system-functions/change-tracking-functions-transact-sql).</span></span>  
  
 <span data-ttu-id="99471-142">主索引鍵資料行的值就是追蹤資料表內與變更資訊一起記錄的唯一資訊。</span><span class="sxs-lookup"><span data-stu-id="99471-142">The values of the primary key column is only information from the tracked table that is recorded with the change information.</span></span> <span data-ttu-id="99471-143">這些值會識別已經變更的資料列。</span><span class="sxs-lookup"><span data-stu-id="99471-143">These values identify the rows that have been changed.</span></span> <span data-ttu-id="99471-144">若要取得這些資料列的最新資料，應用程式可以使用主索引鍵資料行的值來聯結來源資料表與追蹤資料表。</span><span class="sxs-lookup"><span data-stu-id="99471-144">To obtain the latest data for those rows, an application can use the primary key column values to join the source table with the tracked table.</span></span>  
  
 <span data-ttu-id="99471-145">您也可以使用變更追蹤來取得對每個資料列所做變更的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="99471-145">Information about the change that was made to each row can also be obtained by using change tracking.</span></span> <span data-ttu-id="99471-146">例如，導致變更 (插入、更新或刪除) 的 DML 作業類型，或在更新作業中變更的資料行。</span><span class="sxs-lookup"><span data-stu-id="99471-146">For example, the type of DML operation that caused the change (insert, update, or delete) or the columns that were changed as part of an update operation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99471-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="99471-147">See Also</span></span>  
 <span data-ttu-id="99471-148">[啟用和停用變更追蹤 &#40;SQL Server&#41;](../track-changes/enable-and-disable-change-tracking-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="99471-148">[Enable and Disable Change Tracking &#40;SQL Server&#41;](../track-changes/enable-and-disable-change-tracking-sql-server.md) </span></span>  
 <span data-ttu-id="99471-149">[使用變更追蹤 &#40;SQL Server&#41;](../track-changes/work-with-change-tracking-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="99471-149">[Work with Change Tracking &#40;SQL Server&#41;](../track-changes/work-with-change-tracking-sql-server.md) </span></span>  
 <span data-ttu-id="99471-150">[管理變更追蹤 &#40;SQL Server&#41;](../track-changes/manage-change-tracking-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="99471-150">[Manage Change Tracking &#40;SQL Server&#41;](../track-changes/manage-change-tracking-sql-server.md) </span></span>  
 [<span data-ttu-id="99471-151">追蹤資料變更 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="99471-151">Track Data Changes &#40;SQL Server&#41;</span></span>](../track-changes/track-data-changes-sql-server.md)  
  
  
