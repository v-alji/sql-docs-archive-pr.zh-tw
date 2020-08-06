---
title: Oracle 發行概觀 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- publishing [SQL Server replication], Oracle publishing
- snapshot replication [SQL Server], Oracle publishing
- Oracle publishing [SQL Server replication]
- transactional replication, Oracle publishing
- Oracle publishing [SQL Server replication], about Oracle publishing
ms.assetid: 2e013259-0022-4897-a08d-5f8deb880fa8
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b59b12dfcba1472cb6f9d6ecfc51a7df8104fb0b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598278"
---
# <a name="oracle-publishing-overview"></a><span data-ttu-id="790d0-102">Oracle Publishing Overview</span><span class="sxs-lookup"><span data-stu-id="790d0-102">Oracle Publishing Overview</span></span>
  <span data-ttu-id="790d0-103">從 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] 開始，您可以將 Oracle 發行者包含在複寫拓撲中 (從 Oracle 9i 版開始)。</span><span class="sxs-lookup"><span data-stu-id="790d0-103">Beginning with [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], you can include Oracle Publishers in your replication topology, starting with Oracle version 9i.</span></span> <span data-ttu-id="790d0-104">發行伺服器可以部署在任何 Oracle 支援的硬體和作業系統上。</span><span class="sxs-lookup"><span data-stu-id="790d0-104">Publishing servers can be deployed on any Oracle supported hardware and operating system.</span></span> <span data-ttu-id="790d0-105">此功能是建立在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 快照式複寫與異動複寫的堅實基礎上，可以提供相近的效能與可用性。</span><span class="sxs-lookup"><span data-stu-id="790d0-105">The feature is built on the well-established foundation of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] snapshot replication and transactional replication, providing similar performance and usability.</span></span>  
  
 <span data-ttu-id="790d0-106">Oracle 發行已被取代。</span><span class="sxs-lookup"><span data-stu-id="790d0-106">Oracle Publishing is deprecated.</span></span> <span data-ttu-id="790d0-107">非 SQL Server 訂閱者的異質性複寫已被取代。</span><span class="sxs-lookup"><span data-stu-id="790d0-107">Heterogeneous replication to non-SQL Server subscribers is deprecated.</span></span> <span data-ttu-id="790d0-108">若要移動資料，請使用異動資料擷取和 [!INCLUDE[ssIS](../../../includes/ssis-md.md)]建立方案。</span><span class="sxs-lookup"><span data-stu-id="790d0-108">To move data, create solutions using change data capture and [!INCLUDE[ssIS](../../../includes/ssis-md.md)].</span></span>  
  
> [!CAUTION]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../../includes/ssnotedepfutureavoid-md.md)]  
  
## <a name="snapshot-replication-for-oracle"></a><span data-ttu-id="790d0-109">Oracle 的快照式複寫</span><span class="sxs-lookup"><span data-stu-id="790d0-109">Snapshot Replication for Oracle</span></span>  
 <span data-ttu-id="790d0-110">實作 Oracle 快照式發行集的方法與 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 快照式發行集相似。</span><span class="sxs-lookup"><span data-stu-id="790d0-110">Oracle snapshot publications are implemented in a manner similar to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] snapshot publications.</span></span> <span data-ttu-id="790d0-111">針對 Oracle 發行集執行快照集代理程式時，代理程式會連接到 Oracle 發行者，並處理複寫中的每個資料表。</span><span class="sxs-lookup"><span data-stu-id="790d0-111">When the Snapshot Agent runs for an Oracle publication, it connects to the Oracle Publisher and processes each table in the publication.</span></span> <span data-ttu-id="790d0-112">代理程式在處理每個資料表時，會擷取資料表資料列並建立結構描述指令碼，然後儲存在發行集的快照集共用裡。</span><span class="sxs-lookup"><span data-stu-id="790d0-112">When processing each table, the agent retrieves the table rows and creates schema scripts, which are then stored on the publication's snapshot share.</span></span> <span data-ttu-id="790d0-113">快照集代理程式每次執行時都會建立整組資料，所以變更追蹤觸發程序不會像使用異動複寫時一樣加入 Oracle 資料表。</span><span class="sxs-lookup"><span data-stu-id="790d0-113">The entire set of data is created each time the Snapshot Agent runs, so change tracking triggers are not added to the Oracle tables as they are with transactional replication.</span></span> <span data-ttu-id="790d0-114">快照式複寫提供一個便利的方式，能在對發行系統影響最小的情形下移轉資料。</span><span class="sxs-lookup"><span data-stu-id="790d0-114">Snapshot replication provides a convenient way to migrate data with minimal impact on the publishing system.</span></span>  
  
## <a name="transactional-replication-for-oracle"></a><span data-ttu-id="790d0-115">Oracle 的異動複寫</span><span class="sxs-lookup"><span data-stu-id="790d0-115">Transactional Replication for Oracle</span></span>  
 <span data-ttu-id="790d0-116">Oracle 異動複寫是使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]的異動複寫架構實作；不過，是使用 Oracle 資料庫與記錄讀取器代理程式上的資料庫觸發程序組合來追蹤變更。</span><span class="sxs-lookup"><span data-stu-id="790d0-116">Oracle transactional publications are implemented using the transactional publishing architecture of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]; however, changes are tracked using a combination of database triggers on the Oracle database and the Log Reader Agent.</span></span> <span data-ttu-id="790d0-117">Oracle 異動複寫的訂閱者會使用快照式複寫自動初始化；發生後續變更時，會透過記錄讀取器代理程式追蹤並傳遞至訂閱者。</span><span class="sxs-lookup"><span data-stu-id="790d0-117">Subscribers to an Oracle transactional publication are automatically initialized using snapshot replication; subsequent changes are tracked and delivered to Subscribers as they occur via the Log Reader Agent.</span></span>  
  
 <span data-ttu-id="790d0-118">建立 Oracle 發行集時，會為 Oracle 資料庫中每一個發行資料表建立觸發程序與追蹤資料表。</span><span class="sxs-lookup"><span data-stu-id="790d0-118">When an Oracle publication is created, triggers and tracking tables are created for each published table within the Oracle database.</span></span> <span data-ttu-id="790d0-119">變更發行資料表中的資料時，資料表上的資料庫觸發程序會引發，並將資訊插入每個已修改之資料列的複寫追蹤資料表。</span><span class="sxs-lookup"><span data-stu-id="790d0-119">When data changes are made to the published tables, the database triggers on the tables fire and insert information into the replication tracking tables for each modified row.</span></span> <span data-ttu-id="790d0-120">然後 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 散發者上的記錄讀取器代理程式會將資料變更資訊從追蹤資料表移至散發者上的散發資料庫。</span><span class="sxs-lookup"><span data-stu-id="790d0-120">The Log Reader Agent on the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Distributor then moves the data change information from the tracking tables to the distribution database on the Distributor.</span></span> <span data-ttu-id="790d0-121">最後，如同標準異動複寫一樣，散發代理程式會將變更從散發者移至訂閱者。</span><span class="sxs-lookup"><span data-stu-id="790d0-121">Finally, as in standard transactional replication, the Distribution Agent moves changes from the Distributor to the Subscribers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="790d0-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="790d0-122">See Also</span></span>  
 <span data-ttu-id="790d0-123">[設定 Oracle 發行者](configure-an-oracle-publisher.md) </span><span class="sxs-lookup"><span data-stu-id="790d0-123">[Configure an Oracle Publisher](configure-an-oracle-publisher.md) </span></span>  
 <span data-ttu-id="790d0-124">[Oracle 發行相關術語字彙](glossary-of-terms-for-oracle-publishing.md) </span><span class="sxs-lookup"><span data-stu-id="790d0-124">[Glossary of Terms for Oracle Publishing](glossary-of-terms-for-oracle-publishing.md) </span></span>  
 [<span data-ttu-id="790d0-125">異質資料庫複寫</span><span class="sxs-lookup"><span data-stu-id="790d0-125">Heterogeneous Database Replication</span></span>](heterogeneous-database-replication.md)  
  
  
