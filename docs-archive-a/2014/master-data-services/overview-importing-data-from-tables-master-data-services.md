---
title: 資料匯入 (Master Data Services) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- staging process [Master Data Services], about staging process
- importing data [Master Data Services]
- staging process [Master Data Services]
ms.assetid: 181d1e22-379c-45d1-b03c-e1e22ff14164
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 403eca212611397fb3ba30f8fe12a2aa8b5e83ae
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585499"
---
# <a name="data-import-master-data-services"></a><span data-ttu-id="f4520-102">資料匯入 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="f4520-102">Data Import (Master Data Services)</span></span>
  <span data-ttu-id="f4520-103">為 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中的資料建立模型之後，即可開始加入資料，並對 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 資料庫中的資料進行變更。</span><span class="sxs-lookup"><span data-stu-id="f4520-103">Once you've created a model for your data in [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], you can start adding data and make changes to data in the [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] database.</span></span>   <span data-ttu-id="f4520-104">可以使用 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 暫存資料表、預存程序及主資料管理員。</span><span class="sxs-lookup"><span data-stu-id="f4520-104">You use [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] staging tables, stored procedures and Master Data Manager .</span></span>

 <span data-ttu-id="f4520-105">您也可以使用 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] [!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)] ，將資料加入至 MDS 儲存機制， ([!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 資料庫) 。</span><span class="sxs-lookup"><span data-stu-id="f4520-105">You can also use the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)][!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)], to add data to the MDS repository ([!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] database).</span></span> <span data-ttu-id="f4520-106">如需詳細資訊，請參閱[發行 Data &#40;適用于 Excel 的 MDS 增益集&#41;](microsoft-excel-add-in/overview-importing-data-from-excel-mds-add-in-for-excel.md)。</span><span class="sxs-lookup"><span data-stu-id="f4520-106">For more information, see [Publishing Data &#40;MDS Add-in for Excel&#41;](microsoft-excel-add-in/overview-importing-data-from-excel-mds-add-in-for-excel.md).</span></span>

 <span data-ttu-id="f4520-107">當您新增及更新資料時，可以執行下列作業。</span><span class="sxs-lookup"><span data-stu-id="f4520-107">When you add and update data, you can do the following.</span></span>

-   <span data-ttu-id="f4520-108">載入及更新成員，及更新屬性值</span><span class="sxs-lookup"><span data-stu-id="f4520-108">Load and update members, and update attribute values</span></span>

-   <span data-ttu-id="f4520-109">停用及刪除成員</span><span class="sxs-lookup"><span data-stu-id="f4520-109">Deactivate and delete members</span></span>

-   <span data-ttu-id="f4520-110">移動明確階層成員</span><span class="sxs-lookup"><span data-stu-id="f4520-110">Move explicit hierarchy members</span></span>

 <span data-ttu-id="f4520-111">新增及更新資料包含下列主要工作。</span><span class="sxs-lookup"><span data-stu-id="f4520-111">Adding and updating data  includes the following main tasks.</span></span>

1.  <span data-ttu-id="f4520-112">將資料匯入 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 資料庫中的暫存資料表。</span><span class="sxs-lookup"><span data-stu-id="f4520-112">Load data into the staging tables in the [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] database.</span></span>

2.  <span data-ttu-id="f4520-113">將資料從暫存資料表載入適當的 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 資料表。</span><span class="sxs-lookup"><span data-stu-id="f4520-113">Load the data from the staging tables into the appropriate [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] tables.</span></span>

     <span data-ttu-id="f4520-114">您可以使用暫存的預存程序或 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 來載入資料。</span><span class="sxs-lookup"><span data-stu-id="f4520-114">You use staging stored procedures or [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] to load the data.</span></span>

> [!NOTE]
>  <span data-ttu-id="f4520-115">[!INCLUDE[ssSQL14](../includes/sssql14-md.md)]已淘汰對 [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] 暫存處理序提供支援。</span><span class="sxs-lookup"><span data-stu-id="f4520-115">In [!INCLUDE[ssSQL14](../includes/sssql14-md.md)], support for the [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] staging processes is deprecated.</span></span>

## <a name="deactivating-and-deleting-members"></a><span data-ttu-id="f4520-116">停用及刪除成員</span><span class="sxs-lookup"><span data-stu-id="f4520-116">Deactivating and Deleting Members</span></span>
 <span data-ttu-id="f4520-117">停用表示可以重新啟用該成員。</span><span class="sxs-lookup"><span data-stu-id="f4520-117">Deactivating means the member can be reactivated.</span></span> <span data-ttu-id="f4520-118">如果重新啟用成員，即會還原成員在階層和集合中的屬性及成員資格。</span><span class="sxs-lookup"><span data-stu-id="f4520-118">If you reactivate a member, its attributes and its membership in hierarchies and collections are restored.</span></span> <span data-ttu-id="f4520-119">之前的所有交易會完整無缺。</span><span class="sxs-lookup"><span data-stu-id="f4520-119">All previous transactions are intact.</span></span> <span data-ttu-id="f4520-120">系統管理員可以在主要資料的 [版本管理] \*\*\*\* 功能區域中，看到停用的交易。</span><span class="sxs-lookup"><span data-stu-id="f4520-120">Deactivation transactions are visible to administrators in the **Version Management** functional area of the Master Data Manager.</span></span>

 <span data-ttu-id="f4520-121">刪除表示從系統中永久清除該成員。</span><span class="sxs-lookup"><span data-stu-id="f4520-121">Deleting means purging the member from the system permanently.</span></span> <span data-ttu-id="f4520-122">該成員的所有交易、所有關聯性及所有屬性都會遭到永久刪除。</span><span class="sxs-lookup"><span data-stu-id="f4520-122">All transactions for the member, all relationships, and all attributes are permanently deleted.</span></span>

> [!NOTE]
>  <span data-ttu-id="f4520-123">您無法使用暫存來重新啟用成員。</span><span class="sxs-lookup"><span data-stu-id="f4520-123">You cannot use staging to reactivate members.</span></span> <span data-ttu-id="f4520-124">您必須在主資料管理員中手動進行。</span><span class="sxs-lookup"><span data-stu-id="f4520-124">You must do it manually in the Master Data Manager.</span></span> <span data-ttu-id="f4520-125">如需詳細資訊，請參閱[重新啟用成員或集合 &#40;Master Data Services&#41;](reactivate-a-member-or-collection-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="f4520-125">For more information, see [Reactivate a Member or Collection &#40;Master Data Services&#41;](reactivate-a-member-or-collection-master-data-services.md).</span></span>
> 
>  <span data-ttu-id="f4520-126">您無法使用暫存來刪除或重新啟用集合。</span><span class="sxs-lookup"><span data-stu-id="f4520-126">You cannot use staging to delete or deactivate collections.</span></span> <span data-ttu-id="f4520-127">如需手動重新啟用集合的詳細資訊，請參閱[刪除成員或集合 &#40;Master Data Services&#41;](../../2014/master-data-services/delete-a-member-or-collection-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="f4520-127">For more information on manually deactivating collections, see [Delete a Member or Collection &#40;Master Data Services&#41;](../../2014/master-data-services/delete-a-member-or-collection-master-data-services.md).</span></span>

## <a name="moving-explicit-hierarchy-members"></a><span data-ttu-id="f4520-128">移動明確階層成員</span><span class="sxs-lookup"><span data-stu-id="f4520-128">Moving explicit hierarchy members</span></span>
 <span data-ttu-id="f4520-129">大量移動明確階層的成員位置時，可以指定下列項目。</span><span class="sxs-lookup"><span data-stu-id="f4520-129">When you move the location of members in explicit hierarchies in bulk, you can designate the following.</span></span>

-   <span data-ttu-id="f4520-130">合併成員做為合併成員的父系。</span><span class="sxs-lookup"><span data-stu-id="f4520-130">A consolidated member as a parent of a consolidated member.</span></span>

-   <span data-ttu-id="f4520-131">合併成員做為分葉成員的父系。</span><span class="sxs-lookup"><span data-stu-id="f4520-131">A consolidated member as a parent of a leaf member.</span></span>

-   <span data-ttu-id="f4520-132">分葉成員做為分葉或合併成員的同層級。</span><span class="sxs-lookup"><span data-stu-id="f4520-132">A leaf member as a sibling of a leaf or consolidated member.</span></span>

-   <span data-ttu-id="f4520-133">合併成員做為分葉或合併成員的同層級。</span><span class="sxs-lookup"><span data-stu-id="f4520-133">A consolidated member as a sibling of a leaf or consolidated member.</span></span>

## <a name="staging-tables-and-stored-procedures"></a><span data-ttu-id="f4520-134">暫存資料表與預存程序</span><span class="sxs-lookup"><span data-stu-id="f4520-134">Staging Tables and Stored Procedures</span></span>
 <span data-ttu-id="f4520-135">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 資料庫包含下列幾種可以填入您資料的暫存資料表類型。</span><span class="sxs-lookup"><span data-stu-id="f4520-135">The [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] database includes the following types of staging tables that you can populate with your  data.</span></span>

-   [<span data-ttu-id="f4520-136">分葉成員暫存資料表 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="f4520-136">Leaf Member Staging Table &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/leaf-member-staging-table-master-data-services.md)

-   [<span data-ttu-id="f4520-137">合併成員暫存資料表 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="f4520-137">Consolidated Member Staging Table &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/consolidated-member-staging-table-master-data-services.md)

-   [<span data-ttu-id="f4520-138">關聯性暫存資料表 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="f4520-138">Relationship Staging Table &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/relationship-staging-table-master-data-services.md)

 <span data-ttu-id="f4520-139">模型中的每個實體，都有一個暫存資料表。</span><span class="sxs-lookup"><span data-stu-id="f4520-139">For each entity in the model, there is a staging table.</span></span> <span data-ttu-id="f4520-140">資料表名稱表示對應的實體以及像是分葉成員的實體類型。</span><span class="sxs-lookup"><span data-stu-id="f4520-140">The table name indicates the corresponding entity, and the entity type such as leaf member.</span></span> <span data-ttu-id="f4520-141">下圖顯示貨幣、客戶及產品實體的暫存資料表。</span><span class="sxs-lookup"><span data-stu-id="f4520-141">The following image shows the staging tables for the currency, customer, and product entities.</span></span>

 <span data-ttu-id="f4520-142">![MDS 資料庫中的暫存資料表](../../2014/master-data-services/media/mds-stagingtables.png "MDS 資料庫中的暫存資料表")</span><span class="sxs-lookup"><span data-stu-id="f4520-142">![Staging Tables in MDS database](../../2014/master-data-services/media/mds-stagingtables.png "Staging Tables in MDS database")</span></span>

 <span data-ttu-id="f4520-143">建立實體時會指定資料表的名稱，且無法變更。</span><span class="sxs-lookup"><span data-stu-id="f4520-143">The name of the  table is specified when an entity is created and cannot be changed.</span></span> <span data-ttu-id="f4520-144">如果暫存資料表名稱包含 _1 或其他數字，則表示在建立實體時，該名稱的其他資料表已存在。</span><span class="sxs-lookup"><span data-stu-id="f4520-144">If the staging table name contains a _1 or other number, another table of that name already existed when the entity was created.</span></span>

 <span data-ttu-id="f4520-145">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 包含下列幾種類型的暫存預存程序。</span><span class="sxs-lookup"><span data-stu-id="f4520-145">The [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] includes the following types of staging stored procedures.</span></span>

-   <span data-ttu-id="f4520-146">stg.< _Leaf udp_ \<name></span><span class="sxs-lookup"><span data-stu-id="f4520-146">stg.udp_\<name>_Leaf</span></span>

-   <span data-ttu-id="f4520-147">stg.< _Consolidated udp_ \<name></span><span class="sxs-lookup"><span data-stu-id="f4520-147">stg.udp_\<name>_Consolidated</span></span>

-   <span data-ttu-id="f4520-148">stg.< _Relationship udp_ \<name></span><span class="sxs-lookup"><span data-stu-id="f4520-148">stg.udp_\<name>_Relationship</span></span>

 <span data-ttu-id="f4520-149">模型中的每個實體，都有三個對應至分葉成員、合併的成員以及關聯性暫存資料表的預存程序。</span><span class="sxs-lookup"><span data-stu-id="f4520-149">For each entity in the model, there are three stored procedures that correspond to the leaf member, consolidated member, and relationship staging tables.</span></span>  <span data-ttu-id="f4520-150">下圖顯示貨幣、客戶及產品實體的暫存預存程序。</span><span class="sxs-lookup"><span data-stu-id="f4520-150">The following image shows the staging stored procedures for the currency, customer, and product entities.</span></span>

 <span data-ttu-id="f4520-151">![MDS 資料庫中的暫存預存程序](../../2014/master-data-services/media/mds-stagingstoredprocedures.png "MDS 資料庫中的暫存預存程序")</span><span class="sxs-lookup"><span data-stu-id="f4520-151">![Staging Stored Procedures in MDS database](../../2014/master-data-services/media/mds-stagingstoredprocedures.png "Staging Stored Procedures in MDS database")</span></span>

 <span data-ttu-id="f4520-152">如需預存程序的詳細資訊，請參閱[暫存預存程序 &#40;Master Data Services&#41;](../../2014/master-data-services/staging-stored-procedure-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="f4520-152">For more information on the stored procedures, see [Staging Stored Procedure &#40;Master Data Services&#41;](../../2014/master-data-services/staging-stored-procedure-master-data-services.md).</span></span>

## <a name="logging-transactions"></a><span data-ttu-id="f4520-153">記錄交易</span><span class="sxs-lookup"><span data-stu-id="f4520-153">Logging Transactions</span></span>
 <span data-ttu-id="f4520-154">可以記錄匯入或更新資料或關聯性時發生的所有交易。</span><span class="sxs-lookup"><span data-stu-id="f4520-154">All transactions that occur when data or relationships are imported or updated can be logged.</span></span> <span data-ttu-id="f4520-155">預存程序中的選項可允許此記錄。</span><span class="sxs-lookup"><span data-stu-id="f4520-155">An option in the stored procedure allows this logging.</span></span> <span data-ttu-id="f4520-156">如果使用 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]起始暫存處理序，不會產生任何記錄。</span><span class="sxs-lookup"><span data-stu-id="f4520-156">If you initiate the staging process using [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], no logging occurs.</span></span>

 <span data-ttu-id="f4520-157">在 [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)]中， **[記錄暫存交易]** 設定不會套用至暫存資料的這個方法。</span><span class="sxs-lookup"><span data-stu-id="f4520-157">In [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)], the **Log staging transactions** setting does not apply to this method of staging data.</span></span>

## <a name="related-content"></a><span data-ttu-id="f4520-158">相關內容</span><span class="sxs-lookup"><span data-stu-id="f4520-158">Related Content</span></span>

-   [<span data-ttu-id="f4520-159">驗證 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="f4520-159">Validation &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/validation-master-data-services.md)

-   [<span data-ttu-id="f4520-160">商務規則 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="f4520-160">Business Rules &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/business-rules-master-data-services.md)


