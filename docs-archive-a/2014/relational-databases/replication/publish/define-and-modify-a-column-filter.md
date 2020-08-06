---
title: 定義及修改資料行篩選 | Microsoft 文件
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- filters [SQL Server replication], column
- modifying filters, column
- modifying filters
- column filters [SQL Server replication]
ms.assetid: d7c3186a-9a8c-45d8-ab34-05beec4c26dd
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 3a655976f925f83d8c9446cab99016f32ab14887
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606758"
---
# <a name="define-and-modify-a-column-filter"></a><span data-ttu-id="bca00-102">定義及修改資料行篩選</span><span class="sxs-lookup"><span data-stu-id="bca00-102">Define and Modify a Column Filter</span></span>
  <span data-ttu-id="bca00-103">本主題描述如何使用 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 在 [!INCLUDE[tsql](../../../includes/tsql-md.md)]中定義及修改資料行篩選。</span><span class="sxs-lookup"><span data-stu-id="bca00-103">This topic describes how to define and modify a column filter in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="bca00-104">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="bca00-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="bca00-105">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="bca00-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="bca00-106">限制事項</span><span class="sxs-lookup"><span data-stu-id="bca00-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
-   <span data-ttu-id="bca00-107">**若要定義及修改資料行篩選，請使用：**</span><span class="sxs-lookup"><span data-stu-id="bca00-107">**To define and modify a column filter, using:**</span></span>  
  
     [<span data-ttu-id="bca00-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="bca00-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="bca00-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="bca00-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="bca00-110">開始之前</span><span class="sxs-lookup"><span data-stu-id="bca00-110">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="bca00-111">限制事項</span><span class="sxs-lookup"><span data-stu-id="bca00-111">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="bca00-112">某些資料行無法進行篩選；如需詳細資訊，請參閱[篩選發行的資料](filter-published-data.md)。</span><span class="sxs-lookup"><span data-stu-id="bca00-112">Some columns cannot be filtered; for more information, see [Filter Published Data](filter-published-data.md).</span></span> <span data-ttu-id="bca00-113">如果您要在初始化訂閱後修改資料行篩選，則必須在進行變更後產生新的快照集並重新初始化所有訂閱。</span><span class="sxs-lookup"><span data-stu-id="bca00-113">If you modify a column filter after subscriptions have been initialized, you must generate a new snapshot and reinitialize all subscriptions after making the change.</span></span> <span data-ttu-id="bca00-114">如需屬性變更需求的詳細資訊，請參閱[變更發行集與發行項屬性](change-publication-and-article-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="bca00-114">For more information about requirements for property changes, see [Change Publication and Article Properties](change-publication-and-article-properties.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="bca00-115">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="bca00-115">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="bca00-116">在「新增發行集精靈」的 **[發行項]** 頁面中定義資料行篩選。</span><span class="sxs-lookup"><span data-stu-id="bca00-116">Define column filters on the **Articles** page of the New Publication Wizard.</span></span> <span data-ttu-id="bca00-117">如需使用「新增發行集精靈」的詳細資訊，請參閱[建立發行集](create-a-publication.md)。</span><span class="sxs-lookup"><span data-stu-id="bca00-117">For more information about using the New Publication Wizard, see [Create a Publication](create-a-publication.md).</span></span>  
  
 <span data-ttu-id="bca00-118">在 [發行集屬性 - \<Publication>] 對話方塊的 [發行項] 頁面上定義及修改資料行篩選。</span><span class="sxs-lookup"><span data-stu-id="bca00-118">Define and modify column filters on the **Articles** page of the **Publication Properties - \<Publication>** dialog box.</span></span> <span data-ttu-id="bca00-119">如需發行集和發行項屬性的詳細資訊，請參閱[檢視及修改發行集屬性](view-and-modify-publication-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="bca00-119">For more information about publication and article properties, see [View and Modify Publication Properties](view-and-modify-publication-properties.md).</span></span>  
  
#### <a name="to-define-a-column-filter"></a><span data-ttu-id="bca00-120">若要定義資料行篩選</span><span class="sxs-lookup"><span data-stu-id="bca00-120">To define a column filter</span></span>  
  
1.  <span data-ttu-id="bca00-121">在「新增發行集精靈」的 **[發行項]** 頁面中，展開要在 **[發行的物件]** 窗格中篩選的資料表。</span><span class="sxs-lookup"><span data-stu-id="bca00-121">On the **Articles** page of the New Publication Wizard, expand the table to be filtered in the **Objects to publish** pane.</span></span>  
  
2.  <span data-ttu-id="bca00-122">清除您要篩選之每個資料行旁邊的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="bca00-122">Clear the check box next to each column you want to filter.</span></span>  
  
#### <a name="to-modify-column-filtering"></a><span data-ttu-id="bca00-123">若要修改資料行篩選</span><span class="sxs-lookup"><span data-stu-id="bca00-123">To modify column filtering</span></span>  
  
1.  <span data-ttu-id="bca00-124">在 [發行集屬性 - \<Publication>] 對話方塊的 [發行項] 頁面中，展開要在 [發行的物件] 窗格中篩選的資料表。</span><span class="sxs-lookup"><span data-stu-id="bca00-124">On the **Articles** page of the **Publication Properties - \<Publication>** dialog box, expand the table to be filtered in the **Objects to publish** pane.</span></span>  
  
2.  <span data-ttu-id="bca00-125">清除每個您要篩選之資料行旁邊的核取方塊，並確保為每個應包含在發行項中的資料行選取核取方塊。</span><span class="sxs-lookup"><span data-stu-id="bca00-125">Clear the check box next to each column you want to filter, and ensure that the check box is selected for each column that should be included in the article.</span></span>  
  
3.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="bca00-126">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="bca00-126">Using Transact-SQL</span></span>  
 <span data-ttu-id="bca00-127">在建立資料表發行項時，您可以定義要將哪些資料行包含在發行項中，並在定義發行項之後變更資料行。</span><span class="sxs-lookup"><span data-stu-id="bca00-127">When creating table articles, you can define which columns to include in the article and change the columns after the article has been defined.</span></span> <span data-ttu-id="bca00-128">您可以使用複寫預存程序來以程式設計的方式建立及修改篩選的資料行。</span><span class="sxs-lookup"><span data-stu-id="bca00-128">You can create and modify filtered columns programmatically using replication stored procedures.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="bca00-129">下列程序假設基礎資料表尚未變更。</span><span class="sxs-lookup"><span data-stu-id="bca00-129">The following procedures assume that the underlying table has not changed.</span></span> <span data-ttu-id="bca00-130">如需複寫已發行之資料表的資料定義語言 (DDL) 變更的詳細資訊，請參閱[對發行集資料庫進行結構描述變更](make-schema-changes-on-publication-databases.md)。</span><span class="sxs-lookup"><span data-stu-id="bca00-130">For information on replicating data definition language (DDL) changes to published tables, see [Make Schema Changes on Publication Databases](make-schema-changes-on-publication-databases.md).</span></span>  
  
#### <a name="to-define-a-column-filter-for-an-article-published-in-a-snapshot-or-transactional-publication"></a><span data-ttu-id="bca00-131">針對快照式或交易式發行集中發行的發行項定義資料行篩選</span><span class="sxs-lookup"><span data-stu-id="bca00-131">To define a column filter for an article published in a snapshot or transactional publication</span></span>  
  
1.  <span data-ttu-id="bca00-132">定義要篩選的發行項。</span><span class="sxs-lookup"><span data-stu-id="bca00-132">Define the article to filter.</span></span> <span data-ttu-id="bca00-133">如需詳細資訊，請參閱 [定義發行項](define-an-article.md)。</span><span class="sxs-lookup"><span data-stu-id="bca00-133">For more information, see [Define an Article](define-an-article.md).</span></span>  
  
2.  <span data-ttu-id="bca00-134">在發行集資料庫的發行者上，執行 [sp_articlecolumn](/sql/relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="bca00-134">At the Publisher on the publication database, execute [sp_articlecolumn](/sql/relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql).</span></span> <span data-ttu-id="bca00-135">這樣會定義要在發行項中包含或移除的資料行。</span><span class="sxs-lookup"><span data-stu-id="bca00-135">This defines the columns to include or remove from the article.</span></span>  
  
    -   <span data-ttu-id="bca00-136">如果只要從包含許多資料行的資料表發行一些資料行，請針對加入的每一個資料行執行 [sp_articlecolumn](/sql/relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql) 一次。</span><span class="sxs-lookup"><span data-stu-id="bca00-136">If publishing only a few columns from a table with many columns, execute [sp_articlecolumn](/sql/relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql) once for each column being added.</span></span> <span data-ttu-id="bca00-137">為 **\@column** 指定資料行名稱，並為 **\@operation** 指定 **add** 值。</span><span class="sxs-lookup"><span data-stu-id="bca00-137">Specify the column name for **\@column** and a value of **add** for **\@operation**.</span></span>  
  
    -   <span data-ttu-id="bca00-138">如果要在包含許多資料行的資料表中發行大多數的資料行，請執行 [sp_articlecolumn](/sql/relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql)、為 **\@column** 指定 **null** 值，以及為 **\@operation** 指定 **add** 值來新增所有資料行。</span><span class="sxs-lookup"><span data-stu-id="bca00-138">If publishing most of the columns in a table with many columns, execute [sp_articlecolumn](/sql/relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql), specifying a value of **null** for **\@column** and a value of **add** for **\@operation** to add all columns.</span></span> <span data-ttu-id="bca00-139">然後為每一個排除的資料行執行 [sp_articlecolumn](/sql/relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql) 一次，為 **\@operation** 指定 **drop** 值，並為 **\@column** 指定排除的資料行名稱。</span><span class="sxs-lookup"><span data-stu-id="bca00-139">Then execute [sp_articlecolumn](/sql/relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql), once for each column being excluded, specifying a value of **drop** for **\@operation** and the excluded column name for **\@column**.</span></span>  
  
3.  <span data-ttu-id="bca00-140">在發行集資料庫的發行者上，執行 [sp_articleview](/sql/relational-databases/system-stored-procedures/sp-articleview-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="bca00-140">At the Publisher on the publication database, execute [sp_articleview](/sql/relational-databases/system-stored-procedures/sp-articleview-transact-sql).</span></span> <span data-ttu-id="bca00-141">為 **\@publication** 指定發行集名稱，並為 **\@article** 指定篩選的發行項名稱。</span><span class="sxs-lookup"><span data-stu-id="bca00-141">Specify the publication name for **\@publication** and the name of the filtered article for **\@article**.</span></span> <span data-ttu-id="bca00-142">這樣會針對篩選的發行項建立同步處理物件。</span><span class="sxs-lookup"><span data-stu-id="bca00-142">This creates the synchronization objects for the filtered article.</span></span>  
  
#### <a name="to-change-a-column-filter-to-include-additional-columns-for-an-article-published-in-a-snapshot-or-transactional-publication"></a><span data-ttu-id="bca00-143">針對快照式或交易式發行集中發行的發行項變更要包含其他資料行的資料行篩選</span><span class="sxs-lookup"><span data-stu-id="bca00-143">To change a column filter to include additional columns for an article published in a snapshot or transactional publication</span></span>  
  
1.  <span data-ttu-id="bca00-144">在發行集資料庫的發行者上，針對每一個加入的資料行執行 [sp_articlecolumn](/sql/relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql) 一次。</span><span class="sxs-lookup"><span data-stu-id="bca00-144">At the Publisher on the publication database, execute [sp_articlecolumn](/sql/relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql) once for each column being added.</span></span> <span data-ttu-id="bca00-145">為 **\@column** 指定資料行名稱，並為 **\@operation** 指定 **add** 值。</span><span class="sxs-lookup"><span data-stu-id="bca00-145">Specify the column name for **\@column** and a value of **add** for **\@operation**.</span></span>  
  
2.  <span data-ttu-id="bca00-146">在發行集資料庫的發行者上，執行 [sp_articleview](/sql/relational-databases/system-stored-procedures/sp-articleview-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="bca00-146">At the Publisher on the publication database, execute [sp_articleview](/sql/relational-databases/system-stored-procedures/sp-articleview-transact-sql).</span></span> <span data-ttu-id="bca00-147">為 **\@publication** 指定發行集名稱，並為 **\@article** 指定篩選的發行項名稱。</span><span class="sxs-lookup"><span data-stu-id="bca00-147">Specify the publication name for **\@publication** and the name of the filtered article for **\@article**.</span></span> <span data-ttu-id="bca00-148">如果此發行集有現有的訂閱，請為 **\@change_active** 指定 **1** 值。</span><span class="sxs-lookup"><span data-stu-id="bca00-148">If the publication has existing subscriptions, specify a value of **1** for **\@change_active**.</span></span> <span data-ttu-id="bca00-149">這樣會針對篩選的發行項重新建立同步處理物件。</span><span class="sxs-lookup"><span data-stu-id="bca00-149">This re-creates the synchronization objects for the filtered article.</span></span>  
  
3.  <span data-ttu-id="bca00-150">針對此發行集重新執行快照集代理程式作業，以產生更新的快照集。</span><span class="sxs-lookup"><span data-stu-id="bca00-150">Rerun the Snapshot Agent job for the publication to generate an updated snapshot.</span></span>  
  
4.  <span data-ttu-id="bca00-151">重新初始化訂閱。</span><span class="sxs-lookup"><span data-stu-id="bca00-151">Reinitialize subscriptions.</span></span> <span data-ttu-id="bca00-152">如需詳細資訊，請參閱 [重新初始化訂閱](../reinitialize-subscriptions.md)。</span><span class="sxs-lookup"><span data-stu-id="bca00-152">For more information, see [Reinitialize Subscriptions](../reinitialize-subscriptions.md).</span></span>  
  
#### <a name="to-change-a-column-filter-to-remove-columns-for-an-article-published-in-a-snapshot-or-transactional-publication"></a><span data-ttu-id="bca00-153">針對快照式或交易式發行集中發行的發行項變更要移除資料行的資料行篩選</span><span class="sxs-lookup"><span data-stu-id="bca00-153">To change a column filter to remove columns for an article published in a snapshot or transactional publication</span></span>  
  
1.  <span data-ttu-id="bca00-154">在發行集資料庫的發行者上，針對每一個移除的資料行執行 [sp_articlecolumn](/sql/relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql) 一次。</span><span class="sxs-lookup"><span data-stu-id="bca00-154">At the Publisher on the publication database, execute [sp_articlecolumn](/sql/relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql) once for each column being removed.</span></span> <span data-ttu-id="bca00-155">為 **\@column** 指定資料行名稱，並為 **\@operation** 指定 **drop** 值。</span><span class="sxs-lookup"><span data-stu-id="bca00-155">Specify the column name for **\@column** and a value of **drop** for **\@operation**.</span></span>  
  
2.  <span data-ttu-id="bca00-156">在發行集資料庫的發行者上，執行 [sp_articleview](/sql/relational-databases/system-stored-procedures/sp-articleview-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="bca00-156">At the Publisher on the publication database, execute [sp_articleview](/sql/relational-databases/system-stored-procedures/sp-articleview-transact-sql).</span></span> <span data-ttu-id="bca00-157">為 **\@publication** 指定發行集名稱，並為 **\@article** 指定篩選的發行項名稱。</span><span class="sxs-lookup"><span data-stu-id="bca00-157">Specify the publication name for **\@publication** and the name of the filtered article for **\@article**.</span></span> <span data-ttu-id="bca00-158">如果此發行集有現有的訂閱，請為 **\@change_active** 指定 **1** 值。</span><span class="sxs-lookup"><span data-stu-id="bca00-158">If the publication has existing subscriptions, specify a value of **1** for **\@change_active**.</span></span> <span data-ttu-id="bca00-159">這樣會針對篩選的發行項重新建立同步處理物件。</span><span class="sxs-lookup"><span data-stu-id="bca00-159">This re-creates the synchronization objects for the filtered article.</span></span>  
  
3.  <span data-ttu-id="bca00-160">針對此發行集重新執行快照集代理程式作業，以產生更新的快照集。</span><span class="sxs-lookup"><span data-stu-id="bca00-160">Rerun the Snapshot Agent job for the publication to generate an updated snapshot.</span></span>  
  
4.  <span data-ttu-id="bca00-161">重新初始化訂閱。</span><span class="sxs-lookup"><span data-stu-id="bca00-161">Reinitialize subscriptions.</span></span> <span data-ttu-id="bca00-162">如需詳細資訊，請參閱 [重新初始化訂閱](../reinitialize-subscriptions.md)。</span><span class="sxs-lookup"><span data-stu-id="bca00-162">For more information, see [Reinitialize Subscriptions](../reinitialize-subscriptions.md).</span></span>  
  
#### <a name="to-define-a-column-filter-for-an-article-published-in-a-merge-publication"></a><span data-ttu-id="bca00-163">針對合併式發行集中發行的發行項定義資料行篩選</span><span class="sxs-lookup"><span data-stu-id="bca00-163">To define a column filter for an article published in a merge publication</span></span>  
  
1.  <span data-ttu-id="bca00-164">定義要篩選的發行項。</span><span class="sxs-lookup"><span data-stu-id="bca00-164">Define the article to filter.</span></span> <span data-ttu-id="bca00-165">如需詳細資訊，請參閱 [定義發行項](define-an-article.md)。</span><span class="sxs-lookup"><span data-stu-id="bca00-165">For more information, see [Define an Article](define-an-article.md).</span></span>  
  
2.  <span data-ttu-id="bca00-166">在發行集資料庫的發行者上，執行 [sp_mergearticlecolumn](/sql/relational-databases/system-stored-procedures/sp-mergearticlecolumn-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="bca00-166">At the Publisher on the publication database, execute [sp_mergearticlecolumn](/sql/relational-databases/system-stored-procedures/sp-mergearticlecolumn-transact-sql).</span></span> <span data-ttu-id="bca00-167">這樣會定義要在發行項中包含或移除的資料行。</span><span class="sxs-lookup"><span data-stu-id="bca00-167">This defines the columns to include or remove from the article.</span></span>  
  
    -   <span data-ttu-id="bca00-168">如果只要從包含許多資料行的資料表發行一些資料行，請針對加入的每一個資料行執行 [sp_mergearticlecolumn](/sql/relational-databases/system-stored-procedures/sp-mergearticlecolumn-transact-sql) 一次。</span><span class="sxs-lookup"><span data-stu-id="bca00-168">If publishing only a few columns from a table with many columns, execute [sp_mergearticlecolumn](/sql/relational-databases/system-stored-procedures/sp-mergearticlecolumn-transact-sql) once for each column being added.</span></span> <span data-ttu-id="bca00-169">為 **\@column** 指定資料行名稱，並為 **\@operation** 指定 **add** 值。</span><span class="sxs-lookup"><span data-stu-id="bca00-169">Specify the column name for **\@column** and a value of **add** for **\@operation**.</span></span>  
  
    -   <span data-ttu-id="bca00-170">如果要在包含許多資料行的資料表中發行大多數的資料行，請執行 [sp_mergearticlecolumn](/sql/relational-databases/system-stored-procedures/sp-mergearticlecolumn-transact-sql)、為 **\@column** 指定 **null** 值，以及為 **\@operation** 指定 **add** 值來新增所有資料行。</span><span class="sxs-lookup"><span data-stu-id="bca00-170">If publishing most of the columns in a table with many columns, execute [sp_mergearticlecolumn](/sql/relational-databases/system-stored-procedures/sp-mergearticlecolumn-transact-sql), specifying a value of **null** for **\@column** and a value of **add** for **\@operation** to add all columns.</span></span> <span data-ttu-id="bca00-171">然後為每一個排除的資料行執行 [sp_mergearticlecolumn](/sql/relational-databases/system-stored-procedures/sp-mergearticlecolumn-transact-sql) 一次，為 **\@operation** 指定 **drop** 值，並為 **\@column** 指定排除的資料行名稱。</span><span class="sxs-lookup"><span data-stu-id="bca00-171">Then execute [sp_mergearticlecolumn](/sql/relational-databases/system-stored-procedures/sp-mergearticlecolumn-transact-sql), once for each column being excluded, specifying a value of **drop** for **\@operation** and the excluded column name for **\@column**.</span></span>  
  
#### <a name="to-change-a-column-filter-to-include-additional-columns-for-an-article-published-in-a-merge-publication"></a><span data-ttu-id="bca00-172">針對合併式發行集中發行的發行項變更要包含其他資料行的資料行篩選</span><span class="sxs-lookup"><span data-stu-id="bca00-172">To change a column filter to include additional columns for an article published in a merge publication</span></span>  
  
1.  <span data-ttu-id="bca00-173">在發行集資料庫的發行者上，針對每一個加入的資料行執行 [sp_mergearticlecolumn](/sql/relational-databases/system-stored-procedures/sp-mergearticlecolumn-transact-sql) 一次。</span><span class="sxs-lookup"><span data-stu-id="bca00-173">At the Publisher on the publication database, execute [sp_mergearticlecolumn](/sql/relational-databases/system-stored-procedures/sp-mergearticlecolumn-transact-sql) once for each column being added.</span></span> <span data-ttu-id="bca00-174">為 **\@column** 指定資料行名稱、為 **\@operation** 指定 **add** 值，以及為 **\@force_invalidate_snapshot** 和 **\@force_reinit_subscription** 指定 **1** 值。</span><span class="sxs-lookup"><span data-stu-id="bca00-174">Specify the column name for **\@column**, a value of **add** for **\@operation** and a value of **1** for both **\@force_invalidate_snapshot** and **\@force_reinit_subscription**.</span></span>  
  
2.  <span data-ttu-id="bca00-175">針對此發行集重新執行快照集代理程式作業，以產生更新的快照集。</span><span class="sxs-lookup"><span data-stu-id="bca00-175">Rerun the Snapshot Agent job for the publication to generate an updated snapshot.</span></span>  
  
3.  <span data-ttu-id="bca00-176">重新初始化訂閱。</span><span class="sxs-lookup"><span data-stu-id="bca00-176">Reinitialize subscriptions.</span></span> <span data-ttu-id="bca00-177">如需詳細資訊，請參閱 [重新初始化訂閱](../reinitialize-subscriptions.md)。</span><span class="sxs-lookup"><span data-stu-id="bca00-177">For more information, see [Reinitialize Subscriptions](../reinitialize-subscriptions.md).</span></span>  
  
#### <a name="to-change-a-column-filter-to-remove-columns-for-an-article-published-in-a-merge-publication"></a><span data-ttu-id="bca00-178">針對合併式發行集中發行的發行項變更要移除資料行的資料行篩選</span><span class="sxs-lookup"><span data-stu-id="bca00-178">To change a column filter to remove columns for an article published in a merge publication</span></span>  
  
1.  <span data-ttu-id="bca00-179">在發行集資料庫的發行者上，針對每一個移除的資料行執行 [sp_mergearticlecolumn](/sql/relational-databases/system-stored-procedures/sp-mergearticlecolumn-transact-sql) 一次。</span><span class="sxs-lookup"><span data-stu-id="bca00-179">At the Publisher on the publication database, execute [sp_mergearticlecolumn](/sql/relational-databases/system-stored-procedures/sp-mergearticlecolumn-transact-sql) once for each column being removed.</span></span> <span data-ttu-id="bca00-180">為 **\@column** 指定資料行名稱、為 **\@operation** 指定 **drop** 值，以及為 **\@force_invalidate_snapshot** 和 **\@force_reinit_subscription** 指定 **1** 值。</span><span class="sxs-lookup"><span data-stu-id="bca00-180">Specify the column name for **\@column**, a value of **drop** for **\@operation** and a value of **1** for both **\@force_invalidate_snapshot** and **\@force_reinit_subscription**.</span></span>  
  
2.  <span data-ttu-id="bca00-181">針對此發行集重新執行快照集代理程式作業，以產生更新的快照集。</span><span class="sxs-lookup"><span data-stu-id="bca00-181">Rerun the Snapshot Agent job for the publication to generate an updated snapshot.</span></span>  
  
3.  <span data-ttu-id="bca00-182">重新初始化訂閱。</span><span class="sxs-lookup"><span data-stu-id="bca00-182">Reinitialize subscriptions.</span></span> <span data-ttu-id="bca00-183">如需詳細資訊，請參閱 [重新初始化訂閱](../reinitialize-subscriptions.md)。</span><span class="sxs-lookup"><span data-stu-id="bca00-183">For more information, see [Reinitialize Subscriptions](../reinitialize-subscriptions.md).</span></span>  
  
###  <a name="example-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="bca00-184">範例 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="bca00-184">Example (Transact-SQL)</span></span>  
 <span data-ttu-id="bca00-185">此異動複寫範例會從根據 `DaysToManufacture` 資料表的發行項中移除 `Product` 資料行。</span><span class="sxs-lookup"><span data-stu-id="bca00-185">In this transactional replication example, the `DaysToManufacture` column is removed from an article based on the `Product` table.</span></span>  
  
 [!code-sql[HowTo#sp_AddTranArticle](../../../snippets/tsql/SQL15/replication/howto/tsql/createtranpub.sql#sp_addtranarticle)]  
  
 <span data-ttu-id="bca00-186">此合併式複寫範例會從根據 `CreditCardApprovalCode` 資料表的發行項中移除 `SalesOrderHeader` 資料行。</span><span class="sxs-lookup"><span data-stu-id="bca00-186">In this merge replication example, the `CreditCardApprovalCode` column is removed from an article based on the `SalesOrderHeader` table.</span></span>  
  
 [!code-sql[HowTo#sp_AddMergeArticle](../../../snippets/tsql/SQL15/replication/howto/tsql/createmergepub.sql#sp_addmergearticle)]  
  
## <a name="see-also"></a><span data-ttu-id="bca00-187">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bca00-187">See Also</span></span>  
 <span data-ttu-id="bca00-188">[變更發行集與發行項屬性](change-publication-and-article-properties.md) </span><span class="sxs-lookup"><span data-stu-id="bca00-188">[Change Publication and Article Properties](change-publication-and-article-properties.md) </span></span>  
 <span data-ttu-id="bca00-189">[篩選發行的資料](filter-published-data.md) </span><span class="sxs-lookup"><span data-stu-id="bca00-189">[Filter Published Data](filter-published-data.md) </span></span>  
 [<span data-ttu-id="bca00-190">合併式複寫之篩選發行資料</span><span class="sxs-lookup"><span data-stu-id="bca00-190">Filter Published Data for Merge Replication</span></span>](../merge/filter-published-data-for-merge-replication.md)  
  
  
