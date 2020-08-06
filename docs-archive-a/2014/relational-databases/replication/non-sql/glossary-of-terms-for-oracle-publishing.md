---
title: Oracle 發行相關術語字彙 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- Oracle publishing [SQL Server replication], glossary
ms.assetid: e21dfa4b-6144-4be7-9cbf-ca2709b2bd9f
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d135fb8ea3c1678f5ef31f0d7da6a717ab628999
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705014"
---
# <a name="glossary-of-terms-for-oracle-publishing"></a><span data-ttu-id="964b0-102">Oracle 發行相關術語字彙</span><span class="sxs-lookup"><span data-stu-id="964b0-102">Glossary of Terms for Oracle Publishing</span></span>
  <span data-ttu-id="964b0-103">在設定與管理 Oracle 發行時，應熟悉下列 Oracle 術語。</span><span class="sxs-lookup"><span data-stu-id="964b0-103">You should be familiar with the following Oracle terms when configuring and administering Oracle publishing.</span></span> <span data-ttu-id="964b0-104">如需完整的 Oracle 術語清單，請參閱 Oracle 線上文件集。</span><span class="sxs-lookup"><span data-stu-id="964b0-104">For a complete list of Oracle terms, see the Oracle online documentation.</span></span>  
  
 <span data-ttu-id="964b0-105">按索引組織的資料表 (IOT)</span><span class="sxs-lookup"><span data-stu-id="964b0-105">Index Organized Tables (IOT)</span></span>  
 <span data-ttu-id="964b0-106">其資料按索引順序實際儲存在磁碟中的資料表；類似於具有叢集索引的 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 資料表。</span><span class="sxs-lookup"><span data-stu-id="964b0-106">A table whose data is physically sorted on disk in index order; it is similar to a [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] table with a clustered index.</span></span> <span data-ttu-id="964b0-107">將 IOT 做為具有叢集索引的資料表複寫到「訂閱者」。</span><span class="sxs-lookup"><span data-stu-id="964b0-107">An IOT is replicated to a Subscriber as a table with a clustered index.</span></span>  
  
 <span data-ttu-id="964b0-108">執行個體</span><span class="sxs-lookup"><span data-stu-id="964b0-108">Instance</span></span>  
 <span data-ttu-id="964b0-109">Oracle 資料庫與執行個體相關聯。</span><span class="sxs-lookup"><span data-stu-id="964b0-109">An Oracle database is associated with an instance.</span></span> <span data-ttu-id="964b0-110">執行個體包含記憶體與支援資料庫的背景處理序。</span><span class="sxs-lookup"><span data-stu-id="964b0-110">The instance comprises the memory and background processes supporting the database.</span></span> <span data-ttu-id="964b0-111">Oracle 執行個體始終對應到單一資料庫，而 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 的執行個體可能包含多個資料庫。</span><span class="sxs-lookup"><span data-stu-id="964b0-111">An Oracle instance always maps to a single database, whereas an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] can contain many databases.</span></span> <span data-ttu-id="964b0-112">也存在一個 Oracle 資料庫含有多個執行個體的情況。</span><span class="sxs-lookup"><span data-stu-id="964b0-112">There are circumstances in which an Oracle database can have multiple instances.</span></span>  
  
 <span data-ttu-id="964b0-113">Oracle 接聽程式</span><span class="sxs-lookup"><span data-stu-id="964b0-113">Oracle Listener</span></span>  
 <span data-ttu-id="964b0-114">處理 Oracle 資料庫執行個體的連入網路流量。</span><span class="sxs-lookup"><span data-stu-id="964b0-114">Handles incoming network traffic for an Oracle database instance.</span></span> <span data-ttu-id="964b0-115">在設定到 Oracle 資料庫的網路連接時，您需指定用來傳送流量的通訊協定以及接聽程式接聽流量的通訊埠。</span><span class="sxs-lookup"><span data-stu-id="964b0-115">When you configure network connectivity to an Oracle database, you specify the protocol through which traffic is sent and the port on which the Listener listens for traffic.</span></span> <span data-ttu-id="964b0-116">接聽程式通常設定為在與 Oracle 資料庫執行個體所處電腦相同的電腦上執行，還可以設定為服務於一個或多個執行個體。</span><span class="sxs-lookup"><span data-stu-id="964b0-116">The Listener is typically configured to run on the same computer as the Oracle database instance and can be configured to serve one or more instances.</span></span>  
  
 <span data-ttu-id="964b0-117">ROWID</span><span class="sxs-lookup"><span data-stu-id="964b0-117">ROWID</span></span>  
 <span data-ttu-id="964b0-118">指向資料庫中特定資料列位置的指標。</span><span class="sxs-lookup"><span data-stu-id="964b0-118">A pointer to the location of a specific row in a database.</span></span> <span data-ttu-id="964b0-119">因為使用 ROWID 擷取資料列比使用資料表掃描或索引要快，所以複寫在處理已發行的資料表變更時暫時使用 ROWID。</span><span class="sxs-lookup"><span data-stu-id="964b0-119">Because retrieving rows using the ROWID is faster than using a table scan or index, replication uses the ROWID temporarily during processing of published table changes.</span></span>  
  
 <span data-ttu-id="964b0-120">順序</span><span class="sxs-lookup"><span data-stu-id="964b0-120">Sequence</span></span>  
 <span data-ttu-id="964b0-121">用來產生唯一數字的資料庫物件。</span><span class="sxs-lookup"><span data-stu-id="964b0-121">A database object that is used to generate unique numbers.</span></span> <span data-ttu-id="964b0-122">複寫使用序列對已發行資料表的變更進行排序。</span><span class="sxs-lookup"><span data-stu-id="964b0-122">Replication uses sequences to order changes made to published tables.</span></span>  
  
 <span data-ttu-id="964b0-123">SQL\*Plus</span><span class="sxs-lookup"><span data-stu-id="964b0-123">SQL\*Plus</span></span>  
 <span data-ttu-id="964b0-124">用來存取與查詢 Oracle 資料庫的應用程式。</span><span class="sxs-lookup"><span data-stu-id="964b0-124">An application used to access and query Oracle databases.</span></span> <span data-ttu-id="964b0-125">類似於 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] **sqlcmd**。</span><span class="sxs-lookup"><span data-stu-id="964b0-125">It is similar to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] **sqlcmd**.</span></span>  
  
 <span data-ttu-id="964b0-126">同義字</span><span class="sxs-lookup"><span data-stu-id="964b0-126">Synonym</span></span>  
 <span data-ttu-id="964b0-127">物件的別名。</span><span class="sxs-lookup"><span data-stu-id="964b0-127">An alias for an object.</span></span> <span data-ttu-id="964b0-128">在設定「Oracle 發行者」時會自動建立特殊的公用同義字 **MSSQLSERVERDISTRIBUTOR** 。</span><span class="sxs-lookup"><span data-stu-id="964b0-128">The special public synonym **MSSQLSERVERDISTRIBUTOR** is automatically created when an Oracle Publisher is configured.</span></span> <span data-ttu-id="964b0-129">同義字參考 **HREPL_Distributor** 資料表，並提供指向服務於「發行者」之「 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 散發者」的邏輯指標。</span><span class="sxs-lookup"><span data-stu-id="964b0-129">The synonym references the **HREPL_Distributor** table and provides a logical pointer to the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Distributor that services the Publisher.</span></span>  
  
 <span data-ttu-id="964b0-130">發行 Oracle 資料庫之後，就無法將此「發行者」設定為使用不同的「 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 散發者」，因為此公用同義字識別出已將特定「散發者」設定為服務於「發行者」。</span><span class="sxs-lookup"><span data-stu-id="964b0-130">After an Oracle database has been published, subsequent attempts to configure this Publisher to use a different [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Distributor will fail, because this public synonym identifies the particular Distributor already configured to service the Publisher.</span></span>  
  
 <span data-ttu-id="964b0-131">資料表空間</span><span class="sxs-lookup"><span data-stu-id="964b0-131">Tablespace</span></span>  
 <span data-ttu-id="964b0-132">資料庫的儲存單位，大致相當於 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]中的檔案群組。</span><span class="sxs-lookup"><span data-stu-id="964b0-132">A unit of database storage that is roughly equivalent to a filegroup in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="964b0-133">TNS 服務名稱</span><span class="sxs-lookup"><span data-stu-id="964b0-133">TNS Service Name</span></span>  
 <span data-ttu-id="964b0-134">TNS (Transparent Network Substrate) 是 Oracle 資料庫所使用的通訊層。</span><span class="sxs-lookup"><span data-stu-id="964b0-134">TNS (Transparent Network Substrate) is a communication layer used by Oracle databases.</span></span> <span data-ttu-id="964b0-135">TNS Service Name 是 Oracle 資料庫執行個體在網路上使用的名稱。</span><span class="sxs-lookup"><span data-stu-id="964b0-135">The TNS Service Name is the name by which an Oracle database instance is known on a network.</span></span> <span data-ttu-id="964b0-136">您可以在為 Oracle 資料庫設定連接時，指派 TNS Service Name。</span><span class="sxs-lookup"><span data-stu-id="964b0-136">You assign a TNS Service Name when you configure connectivity to the Oracle database.</span></span> <span data-ttu-id="964b0-137">複寫使用「TNS 服務」名稱來識別「發行者」並建立連接。</span><span class="sxs-lookup"><span data-stu-id="964b0-137">Replication uses the TNS Service name to identify the Publisher and to establish connections.</span></span>  
  
 <span data-ttu-id="964b0-138">使用者結構描述</span><span class="sxs-lookup"><span data-stu-id="964b0-138">User schema</span></span>  
 <span data-ttu-id="964b0-139">可以將使用者結構描述想像成擁有特定資料庫物件集的資料庫使用者。</span><span class="sxs-lookup"><span data-stu-id="964b0-139">A user schema can be thought of as a database user who owns a particular set of database objects.</span></span> <span data-ttu-id="964b0-140">複寫管理的使用者結構描述在 Oracle 資料庫中擁有 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 複寫處理所建立的所有物件，但公用同義字 **MSSQLSERVERDISTRIBUTOR** 除外。</span><span class="sxs-lookup"><span data-stu-id="964b0-140">The replication administrative user schema owns all objects created by the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] replication process in the Oracle database, with the exception of the **MSSQLSERVERDISTRIBUTOR** public synonym.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="964b0-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="964b0-141">See Also</span></span>  
 <span data-ttu-id="964b0-142">[設定 Oracle 發行者](configure-an-oracle-publisher.md) </span><span class="sxs-lookup"><span data-stu-id="964b0-142">[Configure an Oracle Publisher](configure-an-oracle-publisher.md) </span></span>  
 <span data-ttu-id="964b0-143">[在 Oracle 發行者上建立的物件](objects-created-on-the-oracle-publisher.md) </span><span class="sxs-lookup"><span data-stu-id="964b0-143">[Objects Created on the Oracle Publisher](objects-created-on-the-oracle-publisher.md) </span></span>  
 <span data-ttu-id="964b0-144">[非 SQL Server 發行者](non-sql-server-publishers.md) </span><span class="sxs-lookup"><span data-stu-id="964b0-144">[Non-SQL Server Publishers](non-sql-server-publishers.md) </span></span>  
 [<span data-ttu-id="964b0-145">Oracle 發行概觀</span><span class="sxs-lookup"><span data-stu-id="964b0-145">Oracle Publishing Overview</span></span>](oracle-publishing-overview.md)  
  
  
