---
title: 需要更新之備份的常見動作 | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- recovery [SQL Server replication], actions requiring a backup
- restoring [SQL Server replication], actions requiring a backup
- backups [SQL Server replication], actions requiring a backup
ms.assetid: a5975bf4-183e-42e3-b7d1-ad02f89d2e1d
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 3eb10bdca8ee188f7b322a46665c38129d57052b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687757"
---
# <a name="common-actions-requiring-an-updated-backup"></a><span data-ttu-id="0abfc-102">需要更新之備份的常見動作</span><span class="sxs-lookup"><span data-stu-id="0abfc-102">Common Actions Requiring an Updated Backup</span></span>
  <span data-ttu-id="0abfc-103">如果您執行一般記錄備份，就必須在記錄備份中擷取任何複寫相關的變更。</span><span class="sxs-lookup"><span data-stu-id="0abfc-103">If you perform regular log backups, any replication-related changes should be captured in the log backups.</span></span> <span data-ttu-id="0abfc-104">如果您未執行記錄備份，請在修改複寫結構描述或拓撲之後執行發行、散發、訂閱、 **msdb**和 **master** 資料庫的備份。</span><span class="sxs-lookup"><span data-stu-id="0abfc-104">If you don't perform log backups, perform a backup of the publication, distribution, subscription, **msdb**, and **master** databases after making modifications to your replication schema or topology.</span></span>  
  
## <a name="publication-database"></a><span data-ttu-id="0abfc-105">發行集資料庫</span><span class="sxs-lookup"><span data-stu-id="0abfc-105">Publication Database</span></span>  
 <span data-ttu-id="0abfc-106">在下述動作之後備份發行集資料庫：</span><span class="sxs-lookup"><span data-stu-id="0abfc-106">Backup the publication database after:</span></span>  
  
-   <span data-ttu-id="0abfc-107">建立新的發行集。</span><span class="sxs-lookup"><span data-stu-id="0abfc-107">Creating new publications.</span></span>  
  
-   <span data-ttu-id="0abfc-108">變更包含篩選在內的任何發行集屬性。</span><span class="sxs-lookup"><span data-stu-id="0abfc-108">Changing any publication property, including filtering.</span></span>  
  
-   <span data-ttu-id="0abfc-109">新增發行項 (Article) 至現有的發行集。</span><span class="sxs-lookup"><span data-stu-id="0abfc-109">Adding articles to an existing publication.</span></span>  
  
-   <span data-ttu-id="0abfc-110">執行訂閱的發行集全區重新初始化。</span><span class="sxs-lookup"><span data-stu-id="0abfc-110">Performing a publication-wide reinitialization of subscriptions.</span></span>  
  
-   <span data-ttu-id="0abfc-111">在已發行的資料表上進行結構描述變更。</span><span class="sxs-lookup"><span data-stu-id="0abfc-111">Making a schema change on a published table.</span></span>  
  
-   <span data-ttu-id="0abfc-112">使用 [sp_addscriptexec &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addscriptexec-transact-sql)，執行隨選的指令碼。</span><span class="sxs-lookup"><span data-stu-id="0abfc-112">Performing on-demand script execution with [sp_addscriptexec &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addscriptexec-transact-sql).</span></span>  
  
-   <span data-ttu-id="0abfc-113">變更任何發行項的屬性。</span><span class="sxs-lookup"><span data-stu-id="0abfc-113">Changing any article property.</span></span>  
  
-   <span data-ttu-id="0abfc-114">卸除發行集。</span><span class="sxs-lookup"><span data-stu-id="0abfc-114">Dropping any publications.</span></span>  
  
-   <span data-ttu-id="0abfc-115">卸除發行項。</span><span class="sxs-lookup"><span data-stu-id="0abfc-115">Dropping any articles.</span></span>  
  
-   <span data-ttu-id="0abfc-116">停用複寫。</span><span class="sxs-lookup"><span data-stu-id="0abfc-116">Disabling replication.</span></span>  
  
## <a name="distribution-database"></a><span data-ttu-id="0abfc-117">散發資料庫</span><span class="sxs-lookup"><span data-stu-id="0abfc-117">Distribution Database</span></span>  
 <span data-ttu-id="0abfc-118">在下述動作之後備份散發資料庫：</span><span class="sxs-lookup"><span data-stu-id="0abfc-118">Backup the distribution database after:</span></span>  
  
-   <span data-ttu-id="0abfc-119">建立或修改複寫代理程式設定檔。</span><span class="sxs-lookup"><span data-stu-id="0abfc-119">Creating or modifying replication agent profiles.</span></span>  
  
-   <span data-ttu-id="0abfc-120">修改複寫代理程式設定檔參數。</span><span class="sxs-lookup"><span data-stu-id="0abfc-120">Modifying replication agent profile parameters.</span></span>  
  
-   <span data-ttu-id="0abfc-121">變更發送訂閱的複寫代理程式屬性 (包括排程)。</span><span class="sxs-lookup"><span data-stu-id="0abfc-121">Changing the replication agent properties (including schedules) for any push subscriptions.</span></span>  
  
-   <span data-ttu-id="0abfc-122">由自動識別範圍管理功能指派新的識別範圍。</span><span class="sxs-lookup"><span data-stu-id="0abfc-122">A new range of identities is assigned by the automatic identity range management feature.</span></span>  
  
## <a name="subscription-database"></a><span data-ttu-id="0abfc-123">訂閱資料庫</span><span class="sxs-lookup"><span data-stu-id="0abfc-123">Subscription Database</span></span>  
 <span data-ttu-id="0abfc-124">在下述動作之後備份訂閱資料庫：</span><span class="sxs-lookup"><span data-stu-id="0abfc-124">Backup the subscription database after:</span></span>  
  
-   <span data-ttu-id="0abfc-125">變更訂閱的屬性。</span><span class="sxs-lookup"><span data-stu-id="0abfc-125">Changing any subscription property.</span></span>  
  
-   <span data-ttu-id="0abfc-126">變更「發行者」端合併訂閱的優先權。</span><span class="sxs-lookup"><span data-stu-id="0abfc-126">Changing the priority for a merge subscription at the Publisher.</span></span>  
  
-   <span data-ttu-id="0abfc-127">卸除訂閱。</span><span class="sxs-lookup"><span data-stu-id="0abfc-127">Dropping any subscriptions.</span></span>  
  
-   <span data-ttu-id="0abfc-128">停用複寫。</span><span class="sxs-lookup"><span data-stu-id="0abfc-128">Disabling replication.</span></span>  
  
## <a name="msdb-database"></a><span data-ttu-id="0abfc-129">msdb 資料庫</span><span class="sxs-lookup"><span data-stu-id="0abfc-129">msdb Database</span></span>  
 <span data-ttu-id="0abfc-130">下述動作後，於適當的節點備份 **msdb** 系統資料庫：</span><span class="sxs-lookup"><span data-stu-id="0abfc-130">Backup the **msdb** system database at the appropriate node after:</span></span>  
  
-   <span data-ttu-id="0abfc-131">啟用或停用複寫。</span><span class="sxs-lookup"><span data-stu-id="0abfc-131">Enabling or disabling replication.</span></span>  
  
-   <span data-ttu-id="0abfc-132">新增或卸除散發資料庫 (於「散發者」處)。</span><span class="sxs-lookup"><span data-stu-id="0abfc-132">Adding or dropping a distribution database (at the Distributor).</span></span>  
  
-   <span data-ttu-id="0abfc-133">啟用或停用發行所使用的資料庫 (於「發行者」處)。</span><span class="sxs-lookup"><span data-stu-id="0abfc-133">Enabling or disabling a database for publishing (at the Publisher).</span></span>  
  
-   <span data-ttu-id="0abfc-134">建立或修改複寫代理程式設定檔 (於「散發者」處)。</span><span class="sxs-lookup"><span data-stu-id="0abfc-134">Creating or modifying replication agent profiles (at the Distributor).</span></span>  
  
-   <span data-ttu-id="0abfc-135">修改複寫代理程式設定檔參數 (於「散發者」處)。</span><span class="sxs-lookup"><span data-stu-id="0abfc-135">Modifying any replication agent profile parameters (at the Distributor).</span></span>  
  
-   <span data-ttu-id="0abfc-136">變更發送訂閱的複寫代理程式屬性 (包括排程) (於「散發者」處)。</span><span class="sxs-lookup"><span data-stu-id="0abfc-136">Changing the replication agent properties (including schedules) for any push subscriptions (at the Distributor).</span></span>  
  
-   <span data-ttu-id="0abfc-137">變更提取訂閱的複寫代理程式屬性 (包括排程) (於「訂閱者」處)。</span><span class="sxs-lookup"><span data-stu-id="0abfc-137">Changing the replication agent properties (including schedules) for any pull subscriptions (at the Subscriber).</span></span>  
  
-   <span data-ttu-id="0abfc-138">建立與使用可轉換訂閱的交易式發行集相關聯的 DTS 封裝 (於「散發者」和「訂閱者」端)。</span><span class="sxs-lookup"><span data-stu-id="0abfc-138">Creating a DTS package associated with a transactional publication that uses transformable subscriptions (at the Distributor and Subscriber).</span></span>  
  
-   <span data-ttu-id="0abfc-139">新增或卸除可轉換訂閱 (於「散發者」和「訂閱者」端)。</span><span class="sxs-lookup"><span data-stu-id="0abfc-139">Adding or dropping a transformable subscription (at the Distributor and Subscriber).</span></span>  
  
## <a name="master-database"></a><span data-ttu-id="0abfc-140">master 資料庫</span><span class="sxs-lookup"><span data-stu-id="0abfc-140">master Database</span></span>  
 <span data-ttu-id="0abfc-141">下述動作後，於適當的節點備份 **master** 系統資料庫：</span><span class="sxs-lookup"><span data-stu-id="0abfc-141">Backup the **master** system database at the appropriate node after:</span></span>  
  
-   <span data-ttu-id="0abfc-142">啟用或停用複寫。</span><span class="sxs-lookup"><span data-stu-id="0abfc-142">Enabling or disabling replication.</span></span>  
  
-   <span data-ttu-id="0abfc-143">新增或卸除散發資料庫 (於「散發者」處)。</span><span class="sxs-lookup"><span data-stu-id="0abfc-143">Adding or dropping a distribution database (at the Distributor).</span></span>  
  
-   <span data-ttu-id="0abfc-144">啟用或停用發行所使用的資料庫 (於「發行者」處)。</span><span class="sxs-lookup"><span data-stu-id="0abfc-144">Enabling or disabling a database for publishing (at the Publisher).</span></span>  
  
-   <span data-ttu-id="0abfc-145">在任何資料庫中新增第一個或卸除最後一個發行集 (於「發行者」處)。</span><span class="sxs-lookup"><span data-stu-id="0abfc-145">Adding the first or dropping the last publication in any database (at the Publisher).</span></span>  
  
-   <span data-ttu-id="0abfc-146">在任何資料庫中新增第一個或卸除最後一個訂閱 (於「訂閱者」處)。</span><span class="sxs-lookup"><span data-stu-id="0abfc-146">Adding the first or dropping the last subscription in any database (at the Subscriber).</span></span>  
  
-   <span data-ttu-id="0abfc-147">啟用或停用「散發發行者」的「發行者」(於「發行者」及「散發者」處)。</span><span class="sxs-lookup"><span data-stu-id="0abfc-147">Enabling or disabling a Publisher at a Distribution Publisher (at the Publisher and Distributor).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0abfc-148">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0abfc-148">See Also</span></span>  
 <span data-ttu-id="0abfc-149">[SQL Server 資料庫的備份與還原](../../backup-restore/back-up-and-restore-of-sql-server-databases.md) </span><span class="sxs-lookup"><span data-stu-id="0abfc-149">[Back Up and Restore of SQL Server Databases](../../backup-restore/back-up-and-restore-of-sql-server-databases.md) </span></span>  
 [<span data-ttu-id="0abfc-150">備份及還原複寫的資料庫</span><span class="sxs-lookup"><span data-stu-id="0abfc-150">Back Up and Restore Replicated Databases</span></span>](back-up-and-restore-replicated-databases.md)  
  
  
