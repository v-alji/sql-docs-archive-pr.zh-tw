---
title: 複寫結構描述變更 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- replication [SQL Server], schema changes
- schemas [SQL Server replication], replicating changes
ms.assetid: c09007f0-9374-4f60-956b-8a87670cd043
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: bec2f363cd8c4f7dea45935568a88722b19323fc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596653"
---
# <a name="replicate-schema-changes"></a><span data-ttu-id="eb2a4-102">複寫結構描述變更</span><span class="sxs-lookup"><span data-stu-id="eb2a4-102">Replicate Schema Changes</span></span>
  <span data-ttu-id="eb2a4-103">本主題描述如何使用 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] ，在 [!INCLUDE[tsql](../../../includes/tsql-md.md)]中複寫結構描述變更。</span><span class="sxs-lookup"><span data-stu-id="eb2a4-103">This topic describes how to replicate schema changes in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="eb2a4-104">如果您要針對發佈的發行項進行下列結構描述變更，則這些變更預設會傳播到 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 訂閱者：</span><span class="sxs-lookup"><span data-stu-id="eb2a4-104">If you make the following schema changes to a published article, they are propagated, by default, to [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Subscribers:</span></span>  
  
-   <span data-ttu-id="eb2a4-105">ALTER TABLE</span><span class="sxs-lookup"><span data-stu-id="eb2a4-105">ALTER TABLE</span></span>  
  
-   <span data-ttu-id="eb2a4-106">ALTER VIEW</span><span class="sxs-lookup"><span data-stu-id="eb2a4-106">ALTER VIEW</span></span>  
  
-   <span data-ttu-id="eb2a4-107">ALTER PROCEDURE</span><span class="sxs-lookup"><span data-stu-id="eb2a4-107">ALTER PROCEDURE</span></span>  
  
-   <span data-ttu-id="eb2a4-108">ALTER FUNCTION</span><span class="sxs-lookup"><span data-stu-id="eb2a4-108">ALTER FUNCTION</span></span>  
  
-   <span data-ttu-id="eb2a4-109">ALTER TRIGGER</span><span class="sxs-lookup"><span data-stu-id="eb2a4-109">ALTER TRIGGER</span></span>  
  
 <span data-ttu-id="eb2a4-110">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="eb2a4-110">**In This Topic**</span></span>  
  
-   <span data-ttu-id="eb2a4-111">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="eb2a4-111">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="eb2a4-112">限制事項</span><span class="sxs-lookup"><span data-stu-id="eb2a4-112">Limitations and Restrictions</span></span>](#Restrictions)  
  
-   <span data-ttu-id="eb2a4-113">**若要複寫結構描述變更，請使用：**</span><span class="sxs-lookup"><span data-stu-id="eb2a4-113">**To replicate schema changes, using:**</span></span>  
  
     [<span data-ttu-id="eb2a4-114">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="eb2a4-114">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="eb2a4-115">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="eb2a4-115">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="eb2a4-116">開始之前</span><span class="sxs-lookup"><span data-stu-id="eb2a4-116">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="eb2a4-117">限制事項</span><span class="sxs-lookup"><span data-stu-id="eb2a4-117">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="eb2a4-118">ALTER TABLE ...DROP COLUMN 陳述式一定會複寫至訂閱包含要卸除之資料行的所有「訂閱者」，即使您停用結構描述變更的複寫也是如此。</span><span class="sxs-lookup"><span data-stu-id="eb2a4-118">The ALTER TABLE ... DROP COLUMN statement is always replicated to all Subscribers whose subscription contains the columns being dropped, even if you disable the replication of schema changes.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="eb2a4-119">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="eb2a4-119">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="eb2a4-120">如果不想複寫發行集的結構描述變更，請在 [發行集屬性 - \<Publication>] 對話方塊中停用結構描述變更的複寫。</span><span class="sxs-lookup"><span data-stu-id="eb2a4-120">If you do not want to replicate schema changes for a publication, disable the replication of schema changes in the **Publication Properties - \<Publication>** dialog box.</span></span> <span data-ttu-id="eb2a4-121">如需有關存取這個對話方塊的詳細資訊，請參閱＜ [View and Modify Publication Properties](view-and-modify-publication-properties.md)＞。</span><span class="sxs-lookup"><span data-stu-id="eb2a4-121">For more information about accessing this dialog box, see [View and Modify Publication Properties](view-and-modify-publication-properties.md).</span></span>  
  
#### <a name="to-disable-replication-of-schema-changes"></a><span data-ttu-id="eb2a4-122">若要停用結構描述變更的複寫</span><span class="sxs-lookup"><span data-stu-id="eb2a4-122">To disable replication of schema changes</span></span>  
  
1.  <span data-ttu-id="eb2a4-123">在 [發行集屬性 - \<Publication>] 對話方塊的 [訂閱選項] 頁面上，將 [複寫結構描述變更] 屬性的值設定為 [False]。</span><span class="sxs-lookup"><span data-stu-id="eb2a4-123">On the **Subscription Options** page of the **Publication Properties - \<Publication>** dialog box, set the value of the **Replicate schema changes** property to **False**.</span></span>  
  
2.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
     <span data-ttu-id="eb2a4-124">若只要傳播特定的結構描述變更，請在結構描述變更之前將屬性設定為 **[True]** ，然後在進行變更後將屬性設定為 **[False]** 。</span><span class="sxs-lookup"><span data-stu-id="eb2a4-124">To propagate only specific schema changes, set the property to **True** before a schema change, and then set it to **False** after the change is made.</span></span> <span data-ttu-id="eb2a4-125">相反的，若要傳播大多數結構描述變更，而不是給定變更，請在結構描述變更之前將屬性設定為 **[False]** ，然後在進行變更後將屬性設定為 **[True]** 。</span><span class="sxs-lookup"><span data-stu-id="eb2a4-125">Conversely, to propagate most schema changes, but not a given change, set the property to **False** before the schema change, and then set it to **True** after the change is made.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="eb2a4-126">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="eb2a4-126">Using Transact-SQL</span></span>  
 <span data-ttu-id="eb2a4-127">您可以使用複寫預存程序來指定是否要複寫這些結構描述變更。</span><span class="sxs-lookup"><span data-stu-id="eb2a4-127">You can use replication stored procedures to specify whether these schema changes are replicated.</span></span> <span data-ttu-id="eb2a4-128">您使用的預存程序取決於發行集的類型而定。</span><span class="sxs-lookup"><span data-stu-id="eb2a4-128">The stored procedure that you use depends on the type of publication.</span></span>  
  
#### <a name="to-create-a-snapshot-or-transactional-publication-that-does-not-replicate-schema-changes"></a><span data-ttu-id="eb2a4-129">建立不會複寫結構描述變更的快照式或交易式發行集</span><span class="sxs-lookup"><span data-stu-id="eb2a4-129">To create a snapshot or transactional publication that does not replicate schema changes</span></span>  
  
1.  <span data-ttu-id="eb2a4-130">在發行集資料庫的發行者上，執行[sp_addpublication &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-addpublication-transact-sql)，為\*\* \@ replicate_ddl**指定**0\*\*的值。</span><span class="sxs-lookup"><span data-stu-id="eb2a4-130">At the Publisher on the publication database, execute [sp_addpublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addpublication-transact-sql), specifying a value of **0** for **\@replicate_ddl**.</span></span> <span data-ttu-id="eb2a4-131">如需詳細資訊，請參閱[建立發行集](create-a-publication.md)。</span><span class="sxs-lookup"><span data-stu-id="eb2a4-131">For more information, see [Create a Publication](create-a-publication.md).</span></span>  
  
#### <a name="to-create-a-merge-publication-that-does-not-replicate-schema-changes"></a><span data-ttu-id="eb2a4-132">建立不會複寫結構描述變更的合併式發行集</span><span class="sxs-lookup"><span data-stu-id="eb2a4-132">To create a merge publication that does not replicate schema changes</span></span>  
  
1.  <span data-ttu-id="eb2a4-133">在發行集資料庫的發行者上，執行[sp_addmergepublication &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql)，為\*\* \@ replicate_ddl**指定**0\*\*的值。</span><span class="sxs-lookup"><span data-stu-id="eb2a4-133">At the Publisher on the publication database, execute [sp_addmergepublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql), specifying a value of **0** for **\@replicate_ddl**.</span></span> <span data-ttu-id="eb2a4-134">如需詳細資訊，請參閱[建立發行集](create-a-publication.md)。</span><span class="sxs-lookup"><span data-stu-id="eb2a4-134">For more information, see [Create a Publication](create-a-publication.md).</span></span>  
  
#### <a name="to-temporarily-disable-replicating-schema-changes-for-a-snapshot-or-transactional-publication"></a><span data-ttu-id="eb2a4-135">暫時停用快照式或交易式發行集的複寫結構描述變更</span><span class="sxs-lookup"><span data-stu-id="eb2a4-135">To temporarily disable replicating schema changes for a snapshot or transactional publication</span></span>  
  
1.  <span data-ttu-id="eb2a4-136">針對具有架構變更複寫的發行集，請執行[sp_changepublication &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql)，為\*\* \@ 屬性**指定**replicate_ddl**的值，並為** \@ 值**指定**0\*\*的值。</span><span class="sxs-lookup"><span data-stu-id="eb2a4-136">For a publication with replication of schema changes, execute [sp_changepublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql), specifying a value of **replicate_ddl** for **\@property** and a value of **0** for **\@value**.</span></span>  
  
2.  <span data-ttu-id="eb2a4-137">在發行的物件上執行 DDL 命令。</span><span class="sxs-lookup"><span data-stu-id="eb2a4-137">Execute the DDL command on the published object.</span></span>  
  
3.  <span data-ttu-id="eb2a4-138"> (選擇性) 藉由執行[sp_changepublication &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql)來重新啟用複寫架構變更，並針對 [\ \** \@ 屬性**] 指定 [ **replicate_ddl** ] 的值，並針對 [\ \** \@ 值**] 指定**1**的值。</span><span class="sxs-lookup"><span data-stu-id="eb2a4-138">(Optional) Re-enable replicating schema changes by executing [sp_changepublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql), specifying a value of **replicate_ddl** for **\@property** and a value of **1** for **\@value**.</span></span>  
  
#### <a name="to-temporarily-disable-replicating-schema-changes-for-a-merge-publication"></a><span data-ttu-id="eb2a4-139">暫時停用合併式發行集的複寫結構描述變更</span><span class="sxs-lookup"><span data-stu-id="eb2a4-139">To temporarily disable replicating schema changes for a merge publication</span></span>  
  
1.  <span data-ttu-id="eb2a4-140">針對具有架構變更複寫的發行集，請執行[sp_changemergepublication &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql)，為\*\* \@ 屬性**指定**replicate_ddl**的值，並為** \@ 值**指定**0\*\*的值。</span><span class="sxs-lookup"><span data-stu-id="eb2a4-140">For a publication with replication of schema changes, execute [sp_changemergepublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql), specifying a value of **replicate_ddl** for **\@property** and a value of **0** for **\@value**.</span></span>  
  
2.  <span data-ttu-id="eb2a4-141">在發行的物件上執行 DDL 命令。</span><span class="sxs-lookup"><span data-stu-id="eb2a4-141">Execute the DDL command on the published object.</span></span>  
  
3.  <span data-ttu-id="eb2a4-142"> (選擇性) 藉由執行[sp_changemergepublication &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql)來重新啟用複寫架構變更，並針對 [\ \** \@ 屬性**] 指定 [ **replicate_ddl** ] 的值，並針對 [\ \** \@ 值**] 指定**1**的值。</span><span class="sxs-lookup"><span data-stu-id="eb2a4-142">(Optional) Re-enable replicating schema changes by executing [sp_changemergepublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql), specifying a value of **replicate_ddl** for **\@property** and a value of **1** for **\@value**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb2a4-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="eb2a4-143">See Also</span></span>  
 <span data-ttu-id="eb2a4-144">[對發行集資料庫進行結構描述變更](make-schema-changes-on-publication-databases.md) </span><span class="sxs-lookup"><span data-stu-id="eb2a4-144">[Make Schema Changes on Publication Databases](make-schema-changes-on-publication-databases.md) </span></span>  
 [<span data-ttu-id="eb2a4-145">對發行集資料庫進行結構描述變更</span><span class="sxs-lookup"><span data-stu-id="eb2a4-145">Make Schema Changes on Publication Databases</span></span>](make-schema-changes-on-publication-databases.md)  
  
  
