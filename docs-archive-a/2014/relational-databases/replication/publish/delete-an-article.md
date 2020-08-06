---
title: 刪除發行項 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- articles [SQL Server replication], dropping
- sp_droparticle
- sp_dropmergearticle
- deleting articles
- removing articles
- dropping articles
ms.assetid: 185b58fc-38c0-4abe-822e-6ec20066c863
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 082f90d33c2b8dedfae34dcada9b3935bed134ef
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592616"
---
# <a name="delete-an-article"></a><span data-ttu-id="ab96d-102">刪除發行項</span><span class="sxs-lookup"><span data-stu-id="ab96d-102">Delete an Article</span></span>
  <span data-ttu-id="ab96d-103">本主題描述如何使用 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 或 Replication Management Objects (RMO)，在 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 中刪除發行項。</span><span class="sxs-lookup"><span data-stu-id="ab96d-103">This topic describes how to delete an article in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[tsql](../../../includes/tsql-md.md)] or Replication Management Objects (RMO).</span></span> <span data-ttu-id="ab96d-104">如需可以卸除發行項的情況以及發行項是否需要新快照集或重新初始化訂閱的詳細資訊，請參閱[在現有發行集中加入和卸除發行項](add-articles-to-and-drop-articles-from-existing-publications.md)。</span><span class="sxs-lookup"><span data-stu-id="ab96d-104">For information about the conditions under which articles can be dropped and whether dropping an article requires a new snapshot or the reinitialization of subscriptions, see [Add Articles to and Drop Articles from Existing Publications](add-articles-to-and-drop-articles-from-existing-publications.md).</span></span>  
  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="ab96d-105">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="ab96d-105">Using Transact-SQL</span></span>  
 <span data-ttu-id="ab96d-106">您可以使用複寫預存程序來以程式設計的方式刪除發行項。</span><span class="sxs-lookup"><span data-stu-id="ab96d-106">Articles can be deleted programmatically using replication stored procedures.</span></span> <span data-ttu-id="ab96d-107">使用哪些預存程序要依發行項所屬的發行集類型而定。</span><span class="sxs-lookup"><span data-stu-id="ab96d-107">The stored procedures that you use depend on the type of publication to which the article belongs.</span></span>  
  
#### <a name="to-delete-an-article-from-a-snapshot-or-transactional-publication"></a><span data-ttu-id="ab96d-108">從快照式或交易式發行集中刪除發行項</span><span class="sxs-lookup"><span data-stu-id="ab96d-108">To delete an article from a snapshot or transactional publication</span></span>  
  
1.  <span data-ttu-id="ab96d-109">從 **\@publication** 指定的發行集執行 [sp_droparticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-droparticle-transact-sql) 來刪除 **\@article** 指定的發行項。</span><span class="sxs-lookup"><span data-stu-id="ab96d-109">Execute [sp_droparticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-droparticle-transact-sql) to delete an article, specified by **\@article**, from a publication, specified by **\@publication**.</span></span> <span data-ttu-id="ab96d-110">為\*\* \@ force_invalidate_snapshot**指定**1\*\*的值。</span><span class="sxs-lookup"><span data-stu-id="ab96d-110">Specify a value of **1** for **\@force_invalidate_snapshot**.</span></span>  
  
2.  <span data-ttu-id="ab96d-111">(選擇性) 若要從資料庫完全移除發行的物件，請在發行集資料庫的發行者上執行 `DROP <objectname>` 命令。</span><span class="sxs-lookup"><span data-stu-id="ab96d-111">(Optional) To remove the published object from the database entirely, execute the `DROP <objectname>` command at the Publisher on the publication database.</span></span>  
  
#### <a name="to-delete-an-article-from-a-merge-publication"></a><span data-ttu-id="ab96d-112">從合併式發行集中刪除發行項</span><span class="sxs-lookup"><span data-stu-id="ab96d-112">To delete an article from a merge publication</span></span>  
  
1.  <span data-ttu-id="ab96d-113">從 **\@publication** 指定的發行集執行 [sp_dropmergearticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropmergearticle-transact-sql) 來刪除 **\@article** 指定的發行項。</span><span class="sxs-lookup"><span data-stu-id="ab96d-113">Execute [sp_dropmergearticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropmergearticle-transact-sql) to delete an article, specified by **\@article**, from a publication, specified by **\@publication**.</span></span> <span data-ttu-id="ab96d-114">如有需要，請為\*\* \@ force_invalidate_snapshot**指定**1**的值，並為** \@ force_reinit_subscription**指定**1\*\*的值。</span><span class="sxs-lookup"><span data-stu-id="ab96d-114">If necessary, specify a value of **1** for **\@force_invalidate_snapshot** and a value of **1** for **\@force_reinit_subscription**.</span></span>  
  
2.  <span data-ttu-id="ab96d-115">(選擇性) 若要從資料庫完全移除發行的物件，請在發行集資料庫的發行者上執行 `DROP <objectname>` 命令。</span><span class="sxs-lookup"><span data-stu-id="ab96d-115">(Optional) To remove the published object from the database entirely, execute the `DROP <objectname>` command at the Publisher on the publication database.</span></span>  
  
###  <a name="examples-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="ab96d-116">範例 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="ab96d-116">Examples (Transact-SQL)</span></span>  
 <span data-ttu-id="ab96d-117">下列範例會刪除交易式發行集中的發行項。</span><span class="sxs-lookup"><span data-stu-id="ab96d-117">The following example deletes an article from a transactional publication.</span></span> <span data-ttu-id="ab96d-118">因為這項變更會使現有的快照集失效，所以會為\*\* \@ force_invalidate_snapshot**參數指定**1\*\*的值。</span><span class="sxs-lookup"><span data-stu-id="ab96d-118">Because this change invalidates the existing snapshot, a value of **1** is specified for the **\@force_invalidate_snapshot** parameter.</span></span>  
  
 [!code-sql[HowTo#sp_droparticle](../../../snippets/tsql/SQL15/replication/howto/tsql/droptranpub.sql#sp_droparticle)]  
  
 <span data-ttu-id="ab96d-119">下列範例會刪除合併式發行集中的兩個發行項。</span><span class="sxs-lookup"><span data-stu-id="ab96d-119">The following example deletes two articles from a merge publication.</span></span> <span data-ttu-id="ab96d-120">因為這些變更會使現有的快照集失效，所以會為\*\* \@ force_invalidate_snapshot**參數指定**1\*\*的值。</span><span class="sxs-lookup"><span data-stu-id="ab96d-120">Because these changes invalidate the existing snapshot, a value of **1** is specified for the **\@force_invalidate_snapshot** parameter.</span></span>  
  
 [!code-sql[HowTo#sp_dropmergearticle](../../../snippets/tsql/SQL15/replication/howto/tsql/dropmergepub.sql#sp_dropmergearticle)]
 [!code-sql[HowTo#sp_dropmergearticle](../../../snippets/tsql/SQL15/replication/howto/tsql/dropmergearticles.sql#sp_dropmergearticle)]  
  
##  <a name="using-replication-management-objects-rmo"></a><a name="RMOProcedure"></a> <span data-ttu-id="ab96d-121">使用 Replication Management Objects (RMO)</span><span class="sxs-lookup"><span data-stu-id="ab96d-121">Using Replication Management Objects (RMO)</span></span>  
 <span data-ttu-id="ab96d-122">您可以使用 Replication Management Objects (RMO) 以程式設計的方式刪除發行項。</span><span class="sxs-lookup"><span data-stu-id="ab96d-122">You can delete articles programmatically by using Replication Management Objects (RMO).</span></span> <span data-ttu-id="ab96d-123">用於刪除發行項的 RMO 類別，將取決於發行項所屬的發行集類型而定。</span><span class="sxs-lookup"><span data-stu-id="ab96d-123">The RMO classes you use to delete an article depend on the type of publication to which the article belongs.</span></span>  
  
#### <a name="to-delete-an-article-that-belongs-to-a-snapshot-or-transactional-publication"></a><span data-ttu-id="ab96d-124">刪除屬於快照式或交易式發行集的發行項</span><span class="sxs-lookup"><span data-stu-id="ab96d-124">To delete an article that belongs to a snapshot or transactional publication</span></span>  
  
1.  <span data-ttu-id="ab96d-125">使用 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 類別建立與發行者的連接。</span><span class="sxs-lookup"><span data-stu-id="ab96d-125">Create a connection to the Publisher by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
2.  <span data-ttu-id="ab96d-126">建立 <xref:Microsoft.SqlServer.Replication.TransArticle> 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="ab96d-126">Create an instance of the <xref:Microsoft.SqlServer.Replication.TransArticle> class.</span></span>  
  
3.  <span data-ttu-id="ab96d-127">設定 <xref:Microsoft.SqlServer.Replication.Article.Name%2A>、 <xref:Microsoft.SqlServer.Replication.Article.PublicationName%2A>和 <xref:Microsoft.SqlServer.Replication.Article.DatabaseName%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="ab96d-127">Set the <xref:Microsoft.SqlServer.Replication.Article.Name%2A>, <xref:Microsoft.SqlServer.Replication.Article.PublicationName%2A>, and <xref:Microsoft.SqlServer.Replication.Article.DatabaseName%2A> properties.</span></span>  
  
4.  <span data-ttu-id="ab96d-128">針對 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> 屬性設定步驟 1 中的連接。</span><span class="sxs-lookup"><span data-stu-id="ab96d-128">Set the connection from step 1 for the <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> property.</span></span>  
  
5.  <span data-ttu-id="ab96d-129">檢查 <xref:Microsoft.SqlServer.Replication.ReplicationObject.IsExistingObject%2A> 屬性，確認該發行項存在。</span><span class="sxs-lookup"><span data-stu-id="ab96d-129">Check the <xref:Microsoft.SqlServer.Replication.ReplicationObject.IsExistingObject%2A> property to verify that the article exists.</span></span> <span data-ttu-id="ab96d-130">如果這個屬性的值為 `false`，則表示步驟 3 中的發行項屬性定義錯誤或是此發行項不存在。</span><span class="sxs-lookup"><span data-stu-id="ab96d-130">If the value of this property is `false`, either the article properties in step 3 were defined incorrectly or the article does not exist.</span></span>  
  
6.  <span data-ttu-id="ab96d-131">呼叫 <xref:Microsoft.SqlServer.Replication.Article.Remove%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="ab96d-131">Call the <xref:Microsoft.SqlServer.Replication.Article.Remove%2A> method.</span></span>  
  
7.  <span data-ttu-id="ab96d-132">關閉所有連接。</span><span class="sxs-lookup"><span data-stu-id="ab96d-132">Close all connections.</span></span>  
  
#### <a name="to-delete-an-article-that-belongs-to-a-merge-publication"></a><span data-ttu-id="ab96d-133">刪除屬於合併式發行集的發行項</span><span class="sxs-lookup"><span data-stu-id="ab96d-133">To delete an article that belongs to a merge publication</span></span>  
  
1.  <span data-ttu-id="ab96d-134">使用 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 類別建立與發行者的連接。</span><span class="sxs-lookup"><span data-stu-id="ab96d-134">Create a connection to the Publisher by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
2.  <span data-ttu-id="ab96d-135">建立 <xref:Microsoft.SqlServer.Replication.MergeArticle> 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="ab96d-135">Create an instance of the <xref:Microsoft.SqlServer.Replication.MergeArticle> class.</span></span>  
  
3.  <span data-ttu-id="ab96d-136">設定 <xref:Microsoft.SqlServer.Replication.Article.Name%2A>、 <xref:Microsoft.SqlServer.Replication.Article.PublicationName%2A>和 <xref:Microsoft.SqlServer.Replication.Article.DatabaseName%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="ab96d-136">Set the <xref:Microsoft.SqlServer.Replication.Article.Name%2A>, <xref:Microsoft.SqlServer.Replication.Article.PublicationName%2A>, and <xref:Microsoft.SqlServer.Replication.Article.DatabaseName%2A> properties.</span></span>  
  
4.  <span data-ttu-id="ab96d-137">針對 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> 屬性設定步驟 1 中的連接。</span><span class="sxs-lookup"><span data-stu-id="ab96d-137">Set the connection from step 1 for the <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> property.</span></span>  
  
5.  <span data-ttu-id="ab96d-138">檢查 <xref:Microsoft.SqlServer.Replication.ReplicationObject.IsExistingObject%2A> 屬性，確認該發行項存在。</span><span class="sxs-lookup"><span data-stu-id="ab96d-138">Check the <xref:Microsoft.SqlServer.Replication.ReplicationObject.IsExistingObject%2A> property to verify that the article exists.</span></span> <span data-ttu-id="ab96d-139">如果這個屬性的值為 `false`，則表示步驟 3 中的發行項屬性定義錯誤或是此發行項不存在。</span><span class="sxs-lookup"><span data-stu-id="ab96d-139">If the value of this property is `false`, either the article properties in step 3 were defined incorrectly or the article does not exist.</span></span>  
  
6.  <span data-ttu-id="ab96d-140">呼叫 <xref:Microsoft.SqlServer.Replication.Article.Remove%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="ab96d-140">Call the <xref:Microsoft.SqlServer.Replication.Article.Remove%2A> method.</span></span>  
  
7.  <span data-ttu-id="ab96d-141">關閉所有連接。</span><span class="sxs-lookup"><span data-stu-id="ab96d-141">Close all connections.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab96d-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ab96d-142">See Also</span></span>  
 <span data-ttu-id="ab96d-143">[在現有發行集中加入和卸除發行項](add-articles-to-and-drop-articles-from-existing-publications.md) </span><span class="sxs-lookup"><span data-stu-id="ab96d-143">[Add Articles to and Drop Articles from Existing Publications](add-articles-to-and-drop-articles-from-existing-publications.md) </span></span>  
 [<span data-ttu-id="ab96d-144">Replication System Stored Procedures Concepts</span><span class="sxs-lookup"><span data-stu-id="ab96d-144">Replication System Stored Procedures Concepts</span></span>](../concepts/replication-system-stored-procedures-concepts.md)  
  
  
