---
title: 設定合併式發行集的相容性層級 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- compatibility [SQL Server], replication
- backward compatibility [SQL Server], replication
- publications [SQL Server replication], backward compatibility
ms.assetid: db47ac73-948b-4d77-b272-bb3565135ea5
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 04ad80b0c99e7282ff2acfa459a08665efbdee1c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606753"
---
# <a name="set-the-compatibility-level-for-merge-publications"></a><span data-ttu-id="91b95-102">設定合併式發行集的相容性層級</span><span class="sxs-lookup"><span data-stu-id="91b95-102">Set the Compatibility Level for Merge Publications</span></span>
  <span data-ttu-id="91b95-103">本主題描述如何使用 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] ，在 [!INCLUDE[tsql](../../../includes/tsql-md.md)]中設定合併式發行集的相容性層級。</span><span class="sxs-lookup"><span data-stu-id="91b95-103">This topic describes how to set the compatibility level for merge publications in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span> <span data-ttu-id="91b95-104">合併式複寫使用發行集相容性層級，來確定發行集可在給定資料庫中使用的功能。</span><span class="sxs-lookup"><span data-stu-id="91b95-104">Merge replication uses the publication compatibility level to determine which features can be used by publications in a given database.</span></span>  
  
 <span data-ttu-id="91b95-105">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="91b95-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="91b95-106">**若要設定合併式發行集的相容性層級，請使用：**</span><span class="sxs-lookup"><span data-stu-id="91b95-106">**To set the compatibility level for merge publications, using:**</span></span>  
  
     [<span data-ttu-id="91b95-107">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="91b95-107">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="91b95-108">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="91b95-108">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="91b95-109">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="91b95-109">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="91b95-110">在「新增發行集精靈」的 **[訂閱者類型]** 頁面中設定相容性層級。</span><span class="sxs-lookup"><span data-stu-id="91b95-110">Set the compatibility level on the **Subscriber Types** page of the New Publication Wizard.</span></span> <span data-ttu-id="91b95-111">如需存取此精靈的詳細資訊，請參閱＜ [Create a Publication](create-a-publication.md)中設定合併式發行集的相容性層級。</span><span class="sxs-lookup"><span data-stu-id="91b95-111">For more information on accessing this wizard, see [Create a Publication](create-a-publication.md).</span></span> <span data-ttu-id="91b95-112">建立發行集快照集後，可以提高相容性層級，但不能降低。</span><span class="sxs-lookup"><span data-stu-id="91b95-112">After a publication snapshot is created, the compatibility level can be increased but cannot be decreased.</span></span> <span data-ttu-id="91b95-113">您可在 [發行集屬性 - \<Publication>] 對話方塊的 [一般] 頁面上增加相容性層級。</span><span class="sxs-lookup"><span data-stu-id="91b95-113">Increase the compatibility level on the **General** page of the **Publication Properties - \<Publication>** dialog box.</span></span> <span data-ttu-id="91b95-114">如需有關存取這個對話方塊的詳細資訊，請參閱＜ [View and Modify Publication Properties](view-and-modify-publication-properties.md)＞。</span><span class="sxs-lookup"><span data-stu-id="91b95-114">For more information about accessing this dialog box, see [View and Modify Publication Properties](view-and-modify-publication-properties.md).</span></span> <span data-ttu-id="91b95-115">如果提高發行集的相容性層級，則對於執行相容性層級之前版本的伺服器，其上的所有現有訂閱均無法再同步處理。</span><span class="sxs-lookup"><span data-stu-id="91b95-115">If you increase the publication compatibility level, any existing subscriptions at servers running versions prior to the compatibility level will no longer be able to synchronize.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="91b95-116">因為相容性層級對其他發行集屬性有影響，並且發行項屬性對其有效，所以不要變更相容性層級以及對話方塊中相同用途的其他屬性。</span><span class="sxs-lookup"><span data-stu-id="91b95-116">Because the compatibility level has implications for other publication properties and for which article properties are valid, do not change the compatibility level and other properties in the same use of the dialog box.</span></span> <span data-ttu-id="91b95-117">發行集的快照集應在變更屬性後重新產生。</span><span class="sxs-lookup"><span data-stu-id="91b95-117">The snapshot for the publication should be regenerated after the property is changed.</span></span>  
  
#### <a name="to-set-the-publication-compatibility-level"></a><span data-ttu-id="91b95-118">若要設定發行集相容性層級</span><span class="sxs-lookup"><span data-stu-id="91b95-118">To set the publication compatibility level</span></span>  
  
-   <span data-ttu-id="91b95-119">在「新增發行集精靈」的 **[訂閱者類型]** 頁面中，選取發行集應支援的「訂閱者」類型。</span><span class="sxs-lookup"><span data-stu-id="91b95-119">On the **Subscriber Types** page of the New Publication Wizard, select the types of Subscribers that the publication should support.</span></span>  
  
#### <a name="to-increase-the-publication-compatibility-level"></a><span data-ttu-id="91b95-120">若要提高發行集相容性層級</span><span class="sxs-lookup"><span data-stu-id="91b95-120">To increase the publication compatibility level</span></span>  
  
-   <span data-ttu-id="91b95-121">您可在 [發行集屬性 - \<Publication>] 對話方塊的 [一般] 頁面上選取 [相容性層級]。</span><span class="sxs-lookup"><span data-stu-id="91b95-121">On the **General** page of the **Publication Properties - \<Publication>** dialog box, select for **Compatibility level**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="91b95-122">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="91b95-122">Using Transact-SQL</span></span>  
 <span data-ttu-id="91b95-123">合併式發行集的相容性層級可以在建立發行集時以程式設計方式加以設定，或是在之後以程式設計方式加以修改。</span><span class="sxs-lookup"><span data-stu-id="91b95-123">The compatibility level for a merge publication can either be set programmatically when a publication is created or modified programmatically at a later time.</span></span> <span data-ttu-id="91b95-124">您可以使用複寫預存程序來設定或變更此發行集屬性。</span><span class="sxs-lookup"><span data-stu-id="91b95-124">You can use replication stored procedures to set or change this publication property.</span></span>  
  
#### <a name="to-set-the-publication-compatibility-level-for-a-merge-publication"></a><span data-ttu-id="91b95-125">設定合併式發行集的發行集相容性層級</span><span class="sxs-lookup"><span data-stu-id="91b95-125">To set the publication compatibility level for a merge publication</span></span>  
  
1.  <span data-ttu-id="91b95-126">在發行者上，執行[sp_addmergepublication &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql)，指定的值， **@publication_compatibility_level** 讓發行集與舊版相容 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="91b95-126">At the Publisher, execute [sp_addmergepublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql), specifying a value for **@publication_compatibility_level** to make the publication compatible with older versions of [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="91b95-127">如需詳細資訊，請參閱[建立發行集](create-a-publication.md)。</span><span class="sxs-lookup"><span data-stu-id="91b95-127">For more information, see [Create a Publication](create-a-publication.md).</span></span>  
  
#### <a name="to-change-the-publication-compatibility-level-of-a-merge-publication"></a><span data-ttu-id="91b95-128">變更合併式發行集的發行集相容性層級</span><span class="sxs-lookup"><span data-stu-id="91b95-128">To change the publication compatibility level of a merge publication</span></span>  
  
1.  <span data-ttu-id="91b95-129">執行[sp_changemergepublication &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql)，指定的**publication_compatibility_level** **@property** 和的適當發行集相容性層級 **@value** 。</span><span class="sxs-lookup"><span data-stu-id="91b95-129">Execute [sp_changemergepublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql), specifying **publication_compatibility_level** for **@property** and the appropriate publication compatibility level for **@value**.</span></span>  
  
#### <a name="to-determine-the-publication-compatibility-level-of-a-merge-publication"></a><span data-ttu-id="91b95-130">判斷合併式發行集的發行集相容性層級</span><span class="sxs-lookup"><span data-stu-id="91b95-130">To determine the publication compatibility level of a merge publication</span></span>  
  
1.  <span data-ttu-id="91b95-131">執行 [sp_helpmergepublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql)，指定所需的發行集。</span><span class="sxs-lookup"><span data-stu-id="91b95-131">Execute [sp_helpmergepublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql), specifying the desired publication.</span></span>  
  
2.  <span data-ttu-id="91b95-132">在結果集的 **backward_comp_level** 欄中尋找發行集相容性層級。</span><span class="sxs-lookup"><span data-stu-id="91b95-132">Locate the publication compatibility level in the **backward_comp_level** column in the result set.</span></span>  
  
###  <a name="examples-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="91b95-133">範例 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="91b95-133">Examples (Transact-SQL)</span></span>  
 <span data-ttu-id="91b95-134">此範例會建立合併式發行集，並設定發行集相容性層級。</span><span class="sxs-lookup"><span data-stu-id="91b95-134">This example creates a merge publication and sets the publication compatibility level.</span></span>  
  
```  
-- To avoid storing the login and password in the script file, the values   
-- are passed into SQLCMD as scripting variables. For information about   
-- how to use scripting variables on the command line and in SQL Server  
-- Management Studio, see the "Executing Replication Scripts" section in  
-- the topic "Programming Replication Using System Stored Procedures".  
  
--Add a new merge publication.  
DECLARE @publicationDB AS sysname;  
DECLARE @publication AS sysname;  
DECLARE @login AS sysname;  
DECLARE @password AS sysname;  
SET @publicationDB = N'AdventureWorks2012';   
SET @publication = N'AdvWorksSalesOrdersMerge'   
SET @login = $(Login);  
SET @password = $(Password);  
  
-- Create a new merge publication.   
USE [AdventureWorks2012]  
EXEC sp_addmergepublication   
@publication = @publication,   
-- Set the compatibility level to SQL Server 2014.  
@publication_compatibility_level = '120RTM';   
  
-- Create the snapshot job for the publication.  
EXEC sp_addpublication_snapshot   
@publication = @publication,  
@job_login = @login,  
@job_password = @password;  
GO  
```  
  
 <span data-ttu-id="91b95-135">此範例會變更合併式發行集的發行集相容性層級。</span><span class="sxs-lookup"><span data-stu-id="91b95-135">This example changes the publication compatibility level for the merge publication.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="91b95-136">如果發行集使用任何需要特定相容性層級的功能，則可能不允許變更發行集相容性層級。</span><span class="sxs-lookup"><span data-stu-id="91b95-136">Changing the publication compatibility level might not be allowed if the publication uses any features that require a particular compatibility level.</span></span> <span data-ttu-id="91b95-137">如需詳細資訊，請參閱[複寫回溯相容性](../replication-backward-compatibility.md)。</span><span class="sxs-lookup"><span data-stu-id="91b95-137">For more information, see [Replication Backward Compatibility](../replication-backward-compatibility.md).</span></span>  
  
```  
DECLARE @publication AS sysname;  
SET @publication = N'AdvWorksSalesOrdersMerge' ;  
  
-- Change the publication compatibility level to   
-- SQL Server 2012.  
EXEC sp_changemergepublication   
@publication = @publication,   
@property = N'publication_compatibility_level',   
@value = N'110RTM';  
GO  
  
```  
  
 <span data-ttu-id="91b95-138">此範例會傳回合併式發行集的正確發行集相容性層級。</span><span class="sxs-lookup"><span data-stu-id="91b95-138">This example returns the current publication compatibility level for the merge publication.</span></span>  
  
```  
DECLARE @publication AS sysname;  
SET @publication = N'AdvWorksSalesOrdersMerge' ;  
EXEC sp_helpmergepublication   
@publication = @publication;  
GO  
  
```  
  
## <a name="see-also"></a><span data-ttu-id="91b95-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="91b95-139">See Also</span></span>  
 [<span data-ttu-id="91b95-140">建立發行集</span><span class="sxs-lookup"><span data-stu-id="91b95-140">Create a Publication</span></span>](create-a-publication.md)  
  
  
