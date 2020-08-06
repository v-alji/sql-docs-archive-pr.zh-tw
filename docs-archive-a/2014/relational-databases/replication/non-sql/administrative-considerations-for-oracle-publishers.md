---
title: Oracle 發行者的管理考量 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- Oracle publishing [SQL Server replication], administrative considerations
- administering replication, Oracle publishing
ms.assetid: cfd81fb5-419b-4a1b-97c4-be7c9d4ee289
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 3104b507987a4a236d39dd0ae1f8e3c29358c730
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598281"
---
# <a name="administrative-considerations-for-oracle-publishers"></a><span data-ttu-id="29e19-102">Oracle 發行者的管理考量</span><span class="sxs-lookup"><span data-stu-id="29e19-102">Administrative Considerations for Oracle Publishers</span></span>
  <span data-ttu-id="29e19-103">在設定「Oracle 發行者」並且複寫變更追蹤機制到位之後，Oracle 資料庫系統的管理員仍可使用標準 Oracle 資料庫公用程式並執行一般的系統管理工作。</span><span class="sxs-lookup"><span data-stu-id="29e19-103">After an Oracle Publisher is configured and the replication change tracking mechanisms are in place, administrators of the Oracle database system can still use standard Oracle database utilities and perform typical system administration tasks.</span></span> <span data-ttu-id="29e19-104">但是，您應該留意執行特定管理工作對已發行資料的影響。</span><span class="sxs-lookup"><span data-stu-id="29e19-104">However, you should be aware of the effects on the published data of performing certain administrative tasks.</span></span>  
  
 <span data-ttu-id="29e19-105">卸除或修改為複寫發行的資料行，或者卸除或修改任何複寫物件除外，這些考量不會套用至快照式發行集。</span><span class="sxs-lookup"><span data-stu-id="29e19-105">With the exception of dropping or modifying a column that is published for replication, or dropping or modifying any replication objects, these considerations do not apply to snapshot publications.</span></span>  
  
## <a name="importing-and-loading-data"></a><span data-ttu-id="29e19-106">匯入與載入資料</span><span class="sxs-lookup"><span data-stu-id="29e19-106">Importing and loading data</span></span>  
 <span data-ttu-id="29e19-107">為 Oracle 上的交易式發行集變更追蹤使用觸發程序。</span><span class="sxs-lookup"><span data-stu-id="29e19-107">Triggers are used in change tracking for transactional publications on Oracle.</span></span> <span data-ttu-id="29e19-108">僅在出現更新、插入或刪除時引發複寫觸發程序的情況下，方可將對已發行資料表所作的變更複寫給「訂閱者」。</span><span class="sxs-lookup"><span data-stu-id="29e19-108">Changes to published tables can be replicated to Subscribers only if the replication triggers fire when an update, insert, or delete occurs.</span></span> <span data-ttu-id="29e19-109">Oracle 公用程式 Oracle Import 與 SQL\*Loader 均有在使用這些公用程式將資料列插入複寫資料表時，決定是否引發觸發程序的選項。</span><span class="sxs-lookup"><span data-stu-id="29e19-109">The Oracle utilities Oracle Import and SQL\*Loader both have options that affect whether triggers will fire when rows are inserted into replicated tables with these utilities.</span></span>  
  
### <a name="oracle-import"></a><span data-ttu-id="29e19-110">Oracle Import</span><span class="sxs-lookup"><span data-stu-id="29e19-110">Oracle Import</span></span>  
 <span data-ttu-id="29e19-111">使用 Oracle Import，您可以將選項 **忽略** 設定為 y 或 n (預設值為 n)。</span><span class="sxs-lookup"><span data-stu-id="29e19-111">With Oracle Import, you can set the option **ignore** to 'y' or 'n' (the default is 'n').</span></span> <span data-ttu-id="29e19-112">如果 **忽略** 設定為 n，則資料表將卸除並在匯入期間重新建立。</span><span class="sxs-lookup"><span data-stu-id="29e19-112">If **ignore** is set to 'n', the table is dropped and re-created during import.</span></span> <span data-ttu-id="29e19-113">這將會移除複寫觸發程序並停用複寫。</span><span class="sxs-lookup"><span data-stu-id="29e19-113">This removes replication triggers and disables replication.</span></span> <span data-ttu-id="29e19-114">如果將 **忽略** 設定為 y，匯入會嘗試將資料列載入現有的資料表，這將引發複寫觸發程序。</span><span class="sxs-lookup"><span data-stu-id="29e19-114">If **ignore** is set to 'y', import will attempt to load the rows into the existing table, which fires the replication triggers.</span></span> <span data-ttu-id="29e19-115">因此，在使用「匯入」工具匯入複寫資料表時，務必將 **忽略** 設定為 y。</span><span class="sxs-lookup"><span data-stu-id="29e19-115">Therefore, ensure **ignore** is set to 'y' when importing into a replicated table with the Import tool.</span></span>  
  
### <a name="sqlloader"></a><span data-ttu-id="29e19-116">SQL\*Loader</span><span class="sxs-lookup"><span data-stu-id="29e19-116">SQL\*Loader</span></span>  
 <span data-ttu-id="29e19-117">使用 SQL\*Loader，您可以將選項**導向**設定為 true 或 false (預設值為 false)。</span><span class="sxs-lookup"><span data-stu-id="29e19-117">With SQL\*Loader, you can set the option **direct** to 'true' or 'false' (the default is 'false').</span></span> <span data-ttu-id="29e19-118">如果將 **導向** 設定為 false，資料列會使用傳統的 INSERT 陳述式插入，這將引發複寫觸發程序。</span><span class="sxs-lookup"><span data-stu-id="29e19-118">If **direct** is set to 'false', rows are inserted using conventional INSERT statements, which fire replication triggers.</span></span> <span data-ttu-id="29e19-119">如果將 **導向** 設定為 true，載入將最佳化，並且不引發觸發程序。</span><span class="sxs-lookup"><span data-stu-id="29e19-119">If **direct** is set to 'true', the load is optimized, and triggers are not fired.</span></span> <span data-ttu-id="29e19-120">因此，在使用 SQL\*Loader 工具載入複寫資料表時，務必將 **導向** 設定為 false。</span><span class="sxs-lookup"><span data-stu-id="29e19-120">Therefore, ensure **direct** is set to 'false' when loading into a replicated table with the SQL\*Loader tool.</span></span>  
  
## <a name="making-changes-to-published-objects"></a><span data-ttu-id="29e19-121">變更已發行物件</span><span class="sxs-lookup"><span data-stu-id="29e19-121">Making changes to published objects</span></span>  
 <span data-ttu-id="29e19-122">執行下列動作無需特殊考量：</span><span class="sxs-lookup"><span data-stu-id="29e19-122">The following actions require no special considerations:</span></span>  
  
-   <span data-ttu-id="29e19-123">在已發行資料表上重建索引。</span><span class="sxs-lookup"><span data-stu-id="29e19-123">Rebuilding indexes on published tables.</span></span>  
  
-   <span data-ttu-id="29e19-124">將使用者觸發程序新增至已發行資料表。</span><span class="sxs-lookup"><span data-stu-id="29e19-124">Adding user triggers to a published table.</span></span>  
  
 <span data-ttu-id="29e19-125">下列動作要求您停止已發行資料表上的所有活動：</span><span class="sxs-lookup"><span data-stu-id="29e19-125">The following action requires you to stop all activity on the published tables:</span></span>  
  
-   <span data-ttu-id="29e19-126">移動已發行資料表。</span><span class="sxs-lookup"><span data-stu-id="29e19-126">Moving a published table.</span></span>  
  
 <span data-ttu-id="29e19-127">下列動作要求您卸除發行集、執行作業，然後重新建立發行集：</span><span class="sxs-lookup"><span data-stu-id="29e19-127">The following actions require you to drop the publication, perform the operation, and then recreate the publication:</span></span>  
  
-   <span data-ttu-id="29e19-128">截斷已發行資料表。</span><span class="sxs-lookup"><span data-stu-id="29e19-128">Truncating a published table.</span></span>  
  
-   <span data-ttu-id="29e19-129">重新命名已發行資料表。</span><span class="sxs-lookup"><span data-stu-id="29e19-129">Renaming a published table.</span></span>  
  
-   <span data-ttu-id="29e19-130">將資料行新增至已發行資料表。</span><span class="sxs-lookup"><span data-stu-id="29e19-130">Adding a column to a published table.</span></span>  
  
-   <span data-ttu-id="29e19-131">卸除或修改為複寫發行的資料行。</span><span class="sxs-lookup"><span data-stu-id="29e19-131">Dropping or modifying a column that is published for replication.</span></span>  
  
-   <span data-ttu-id="29e19-132">執行非記錄作業。</span><span class="sxs-lookup"><span data-stu-id="29e19-132">Performing non-logged operations.</span></span>  
  
## <a name="dropping-or-modifying-replication-objects"></a><span data-ttu-id="29e19-133">卸除或修改複寫物件</span><span class="sxs-lookup"><span data-stu-id="29e19-133">Dropping or modifying replication objects</span></span>  
 <span data-ttu-id="29e19-134">如果您卸除或修改任何「發行者」層級追蹤資料表、觸發程序、順序或預存程序，則必須卸除並重新設定「發行者」。</span><span class="sxs-lookup"><span data-stu-id="29e19-134">You must drop and reconfigure the Publisher if you drop or modify any Publisher level tracking tables, triggers, sequences, or stored procedures.</span></span> <span data-ttu-id="29e19-135">如需這些物件的部分清單，請參閱[在 Oracle 發行者端建立的物件](objects-created-on-the-oracle-publisher.md)。</span><span class="sxs-lookup"><span data-stu-id="29e19-135">For a partial list of these objects, see [Objects Created on the Oracle Publisher](objects-created-on-the-oracle-publisher.md).</span></span>  
  
 <span data-ttu-id="29e19-136">如需卸除並重新設定「發行者」的詳細資訊，請參閱主題＜ [Troubleshooting Oracle Publishers](troubleshooting-oracle-publishers.md)＞中的「變更要求重新設定發行者」一節。</span><span class="sxs-lookup"><span data-stu-id="29e19-136">For information about dropping and reconfiguring the Publisher, see the section "Changes are made that require reconfiguration of the Publisher" in the topic [Troubleshooting Oracle Publishers](troubleshooting-oracle-publishers.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29e19-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="29e19-137">See Also</span></span>  
 <span data-ttu-id="29e19-138">[設定 Oracle 發行者](configure-an-oracle-publisher.md) </span><span class="sxs-lookup"><span data-stu-id="29e19-138">[Configure an Oracle Publisher](configure-an-oracle-publisher.md) </span></span>  
 <span data-ttu-id="29e19-139">[Oracle 發行者的設計考量與限制](design-considerations-and-limitations-for-oracle-publishers.md) </span><span class="sxs-lookup"><span data-stu-id="29e19-139">[Design Considerations and Limitations for Oracle Publishers](design-considerations-and-limitations-for-oracle-publishers.md) </span></span>  
 [<span data-ttu-id="29e19-140">Oracle 發行概觀</span><span class="sxs-lookup"><span data-stu-id="29e19-140">Oracle Publishing Overview</span></span>](oracle-publishing-overview.md)  
  
  
