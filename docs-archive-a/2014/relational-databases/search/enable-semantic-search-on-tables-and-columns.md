---
title: 在資料表和資料行上啟用語意搜尋 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- semantic search [SQL Server], enabling
ms.assetid: 895d220c-6749-4954-9dd3-2ea4c6a321ff
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: f11ba654f7cc34f521990e8c420d41885d3c55b9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87702645"
---
# <a name="enable-semantic-search-on-tables-and-columns"></a><span data-ttu-id="70cbf-102">在資料表和資料行上啟用語意搜尋</span><span class="sxs-lookup"><span data-stu-id="70cbf-102">Enable Semantic Search on Tables and Columns</span></span>
  <span data-ttu-id="70cbf-103">描述如何針對包含文件或文字的選取資料行啟用或停用統計語意索引。</span><span class="sxs-lookup"><span data-stu-id="70cbf-103">Describes how to enable or disable statistical semantic indexing on selected columns that contain documents or text.</span></span>  
  
 <span data-ttu-id="70cbf-104">統計語意搜尋會使用全文檢索搜尋所建立的索引，並且建立其他索引。</span><span class="sxs-lookup"><span data-stu-id="70cbf-104">Statistical Semantic Search uses the indexes that are created by Full-Text Search, and creates additional indexes.</span></span> <span data-ttu-id="70cbf-105">由於全文檢索搜尋存在這種相依性，因此您可以在定義新的全文檢索索引或改變現有的全文檢索索引時，建立新的語意索引。</span><span class="sxs-lookup"><span data-stu-id="70cbf-105">As a result of this dependency on full-text search, you create a new semantic index when you define a new full-text index, or when you alter an existing full-text index.</span></span> <span data-ttu-id="70cbf-106">您可以使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中的 [全文檢索索引精靈] 和其他對話方塊來建立新的語意索引 (如本主題所述)。</span><span class="sxs-lookup"><span data-stu-id="70cbf-106">You can create a new semantic index by using [!INCLUDE[tsql](../../includes/tsql-md.md)] statements, or by using the Full-Text Indexing Wizard and other dialog boxes in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], as described in this topic.</span></span>  
  
##  <a name="creating-a-semantic-index"></a><a name="BasicEnabling"></a><span data-ttu-id="70cbf-107">建立語義索引</span><span class="sxs-lookup"><span data-stu-id="70cbf-107">Creating a Semantic Index</span></span>  
  
###  <a name="requirements-and-restrictions-for-creating-a-semantic-index"></a><a name="reqenable"></a><span data-ttu-id="70cbf-108">建立語義索引的需求和限制</span><span class="sxs-lookup"><span data-stu-id="70cbf-108">Requirements and Restrictions for Creating a Semantic Index</span></span>  
  
-   <span data-ttu-id="70cbf-109">您可以針對支援全文檢索索引的任何資料庫物件建立索引，包括資料表和索引檢視表。</span><span class="sxs-lookup"><span data-stu-id="70cbf-109">You can create an index on any of the database objects that are supported for full-text indexing, including tables and indexed views.</span></span>  
  
-   <span data-ttu-id="70cbf-110">必須具有下列必要條件，才能啟用特定資料行的語意索引。</span><span class="sxs-lookup"><span data-stu-id="70cbf-110">Before you can enable semantic indexing for specific columns, the following prerequisites must exist:</span></span>  
  
    -   <span data-ttu-id="70cbf-111">資料庫必須具有全文檢索目錄。</span><span class="sxs-lookup"><span data-stu-id="70cbf-111">A full-text catalog must exist for the database.</span></span>  
  
    -   <span data-ttu-id="70cbf-112">資料表必須具有全文檢索索引。</span><span class="sxs-lookup"><span data-stu-id="70cbf-112">The table must have a full-text index.</span></span>  
  
    -   <span data-ttu-id="70cbf-113">選取的資料行必須參與全文檢索索引。</span><span class="sxs-lookup"><span data-stu-id="70cbf-113">The selected columns must participate in the full-text index.</span></span>  
  
     <span data-ttu-id="70cbf-114">您可以同時建立並啟用所有這些需求。</span><span class="sxs-lookup"><span data-stu-id="70cbf-114">You can create and enable all these requirements at the same time.</span></span>  
  
-   <span data-ttu-id="70cbf-115">您可以針對具有支援全文檢索索引之任何資料類型的資料行建立語意索引。</span><span class="sxs-lookup"><span data-stu-id="70cbf-115">You can create a semantic index on columns that have any of the data types that are supported for full-text indexing.</span></span> <span data-ttu-id="70cbf-116">如需詳細資訊，請參閱 [建立及管理全文檢索索引](create-and-manage-full-text-indexes.md)。</span><span class="sxs-lookup"><span data-stu-id="70cbf-116">For more information, see [Create and Manage Full-Text Indexes](create-and-manage-full-text-indexes.md).</span></span>  
  
-   <span data-ttu-id="70cbf-117">您可以指定支援 `varbinary(max)` 資料行之全文檢索索引的任何文件類型。</span><span class="sxs-lookup"><span data-stu-id="70cbf-117">You can specify any document type that is supported for full-text indexing for `varbinary(max)` columns.</span></span> <span data-ttu-id="70cbf-118">如需詳細資訊，請參閱本主題的＜ [如何：決定可以進行索引的文件類型](#doctypes) ＞。</span><span class="sxs-lookup"><span data-stu-id="70cbf-118">For more information, see [How To: Determine Which Document Types Can Be Indexed](#doctypes) in this topic.</span></span>  
  
-   <span data-ttu-id="70cbf-119">語意索引會針對您所選取的資料行建立兩種索引類型：主要片語的索引，以及文件相似度的索引。</span><span class="sxs-lookup"><span data-stu-id="70cbf-119">Semantic indexing creates two types of indexes for the columns that you select - an index of key phrases, and an index of document similarity.</span></span> <span data-ttu-id="70cbf-120">當您啟用語意索引時，無法單獨選取其中一種索引類型。</span><span class="sxs-lookup"><span data-stu-id="70cbf-120">You cannot select only one type of index or the other when you enable semantic indexing.</span></span> <span data-ttu-id="70cbf-121">不過，您可以個別查詢這兩個索引。</span><span class="sxs-lookup"><span data-stu-id="70cbf-121">However you can query these two indexes independently.</span></span> <span data-ttu-id="70cbf-122">如需詳細資訊，請參閱 [使用語意搜尋找到文件中的主要片語](find-key-phrases-in-documents-with-semantic-search.md) 和 [使用語意搜尋尋找相似及相關的文件](find-similar-and-related-documents-with-semantic-search.md)。</span><span class="sxs-lookup"><span data-stu-id="70cbf-122">For more information, see [Find Key Phrases in Documents with Semantic Search](find-key-phrases-in-documents-with-semantic-search.md) and [Find Similar and Related Documents with Semantic Search](find-similar-and-related-documents-with-semantic-search.md).</span></span>  
  
-   <span data-ttu-id="70cbf-123">如果您沒有明確指定語意索引的 LCID，則只有主要語言及其相關聯的語言統計資料會用於語意索引。</span><span class="sxs-lookup"><span data-stu-id="70cbf-123">If you do not explicitly specify an LCID for a semantic index, then only the primary language and its associated language statistics are used for semantic indexing.</span></span>  
  
-   <span data-ttu-id="70cbf-124">如果您針對語言模型無法使用的資料行指定了語言，索引的建立作業就會失敗並且傳回錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="70cbf-124">If you specify a language for a column for which the language model is not available, the creation of the index fails and returns an error message.</span></span>  
  
###  <a name="how-to-create-a-semantic-index-when-there-is-no-full-text-index"></a><a name="HowToEnableCreate"></a><span data-ttu-id="70cbf-125">如何：在沒有全文檢索索引時建立語義索引</span><span class="sxs-lookup"><span data-stu-id="70cbf-125">How To: Create a Semantic Index When There Is No Full-Text Index</span></span>  
 <span data-ttu-id="70cbf-126">當您使用 **CREATE FULLTEXT INDEX** 陳述式來建立新的全文檢索索引時，可以透過指定 **STATISTICAL_SEMANTICS** 關鍵字當作資料行定義的一部分，在資料行層級中啟用語意索引。</span><span class="sxs-lookup"><span data-stu-id="70cbf-126">When you create a new full-text index with the **CREATE FULLTEXT INDEX** statement, you can enable semantic indexing at the column level by specifying the keyword **STATISTICAL_SEMANTICS** as part of the column definition.</span></span> <span data-ttu-id="70cbf-127">此外，當您使用 [全文檢索索引精靈] 來建立新的全文檢索索引時，也可以啟用語意索引。</span><span class="sxs-lookup"><span data-stu-id="70cbf-127">You can also enable semantic indexing when you use the Full-Text Indexing Wizard to create a new full-text index.</span></span>  
  
 <span data-ttu-id="70cbf-128">**使用 Transact-SQL 建立新的語意索引**</span><span class="sxs-lookup"><span data-stu-id="70cbf-128">**Create a new semantic index by using Transact-SQL**</span></span>  
 <span data-ttu-id="70cbf-129">您可以針對想要建立語意索引的每個資料行呼叫 **CREATE FULLTEXT INDEX** 陳述式並指定 **STATISTICAL_SEMANTICS**。</span><span class="sxs-lookup"><span data-stu-id="70cbf-129">Call the **CREATE FULLTEXT INDEX** statement and specify **STATISTICAL_SEMANTICS** for each column on which you want to create a semantic index.</span></span> <span data-ttu-id="70cbf-130">如需此陳述式之所有選項的詳細資訊，請參閱 [CREATE FULLTEXT INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-fulltext-index-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="70cbf-130">For more information about all the options for this statement, see [CREATE FULLTEXT INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-fulltext-index-transact-sql).</span></span>  
  
 <span data-ttu-id="70cbf-131">**範例 1：建立唯一索引、全文檢索索引及語意索引**</span><span class="sxs-lookup"><span data-stu-id="70cbf-131">**Example 1: Create a unique index, full-text index, and semantic index**</span></span>  
  
 <span data-ttu-id="70cbf-132">下列範例會建立預設全文檢索目錄 **ft**。接著，此範例會針對 AdventureWorks2012 範例資料庫中 **HumanResources.JobCandidate** 資料表的 **JobCandidateID** 資料行建立唯一索引。</span><span class="sxs-lookup"><span data-stu-id="70cbf-132">The following example creates a default full-text catalog, **ft**. The example then creates a unique index on the **JobCandidateID** column of the **HumanResources.JobCandidate** table of the AdventureWorks2012 sample database.</span></span> <span data-ttu-id="70cbf-133">這個唯一索引需要做為全文檢索索引的索引鍵資料行。</span><span class="sxs-lookup"><span data-stu-id="70cbf-133">This unique index is required as the key column for a full-text index.</span></span> <span data-ttu-id="70cbf-134">接著，此範例會針對 **Resume** 資料行建立全文檢索索引和語意索引。</span><span class="sxs-lookup"><span data-stu-id="70cbf-134">The example then creates a full-text index and a semantic index on the **Resume** column.</span></span>  
  
```sql  
CREATE FULLTEXT CATALOG ft AS DEFAULT  
GO  
  
CREATE UNIQUE INDEX ui_ukJobCand  
    ON HumanResources.JobCandidate(JobCandidateID)  
GO  
  
CREATE FULLTEXT INDEX ON HumanResources.JobCandidate  
    (Resume  
        Language 1033  
        Statistical_Semantics  
    )   
    KEY INDEX JobCandidateID   
    WITH STOPLIST = SYSTEM  
GO  
```  
  
 <span data-ttu-id="70cbf-135">**範例 2：針對許多資料行建立全文檢索和語意索引並延遲索引母體擴展**</span><span class="sxs-lookup"><span data-stu-id="70cbf-135">**Example 2: Create a full-text and semantic index on several columns with delayed index population**</span></span>  
  
 <span data-ttu-id="70cbf-136">下列範例會在 AdventureWorks2012 範例資料庫中建立全文檢索目錄 **documents_catalog**。</span><span class="sxs-lookup"><span data-stu-id="70cbf-136">The following example creates a full-text catalog, **documents_catalog**, in the AdventureWorks2012 sample database.</span></span> <span data-ttu-id="70cbf-137">接著，此範例會建立使用這個新目錄的全文檢索索引。</span><span class="sxs-lookup"><span data-stu-id="70cbf-137">The example then creates a full-text index that uses this new catalog.</span></span> <span data-ttu-id="70cbf-138">全文檢索索引是針對 **Production.Document**資料表的 **Title**、 **DocumentSummary** 及 **Document** 資料行而建立，而語意索引則只針對 **Document** 資料行而建立。</span><span class="sxs-lookup"><span data-stu-id="70cbf-138">The full-text index is created on the **Title**, **DocumentSummary**, and **Document** columns of the **Production.Document** table, while the semantic index is only created on the **Document** column.</span></span> <span data-ttu-id="70cbf-139">這個全文檢索索引會使用新建的全文檢索目錄和現有的唯一索引鍵索引 **PK_Document_DocumentID**。</span><span class="sxs-lookup"><span data-stu-id="70cbf-139">This full-text index uses the newly-created full-text catalog and an existing unique key index, **PK_Document_DocumentID**.</span></span> <span data-ttu-id="70cbf-140">根據建議，此索引鍵是建立於整數資料行 **DocumentID**上。</span><span class="sxs-lookup"><span data-stu-id="70cbf-140">As recommended, this index key is created on an integer column, **DocumentID**.</span></span> <span data-ttu-id="70cbf-141">此範例會指定英文的 LCID (1033)，這是這些資料行中資料的語言。</span><span class="sxs-lookup"><span data-stu-id="70cbf-141">The example specifies the LCID for English, 1033, which is the language of the data in the columns.</span></span>  
  
 <span data-ttu-id="70cbf-142">此範例也會指定關閉變更追蹤，而且不進行母體擴展。</span><span class="sxs-lookup"><span data-stu-id="70cbf-142">This example also specifies that change tracking is off with no population.</span></span> <span data-ttu-id="70cbf-143">之後在離峰時段，此範例會使用 **ALTER FULLTEXT INDEX** 陳述式，針對新的索引啟動完整母體擴展，並啟用自動變更追蹤。</span><span class="sxs-lookup"><span data-stu-id="70cbf-143">Later, during off-peak hours, the example uses an **ALTER FULLTEXT INDEX** statement to start a full population on the new index and enable automatic change tracking.</span></span>  
  
```sql  
CREATE FULLTEXT CATALOG documents_catalog  
GO  
  
CREATE FULLTEXT INDEX ON Production.Document  
    (   
    Title  
        Language 1033,   
    DocumentSummary  
        Language 1033,   
    Document   
        TYPE COLUMN FileExtension  
        Language 1033  
        Statistical_Semantics  
    )  
    KEY INDEX PK_Document_DocumentID  
        ON documents_catalog  
        WITH CHANGE_TRACKING OFF, NO POPULATION  
GO  
```  
  
 <span data-ttu-id="70cbf-144">之後，在離峰時段擴展索引：</span><span class="sxs-lookup"><span data-stu-id="70cbf-144">Later, at an off-peak time, the index is populated:</span></span>  
  
```sql  
ALTER FULLTEXT INDEX ON Production.Document SET CHANGE_TRACKING AUTO  
GO  
```  
  
 <span data-ttu-id="70cbf-145">**使用 SQL Server Management Studio 建立新的語意索引**</span><span class="sxs-lookup"><span data-stu-id="70cbf-145">**Create a new semantic index by using SQL Server Management Studio**</span></span>  
 <span data-ttu-id="70cbf-146">您可以針對想要建立語意索引的每個資料行執行 [全文檢索索引精靈]，並在 [選取資料表資料行] 頁面上啟用 [統計語意]。</span><span class="sxs-lookup"><span data-stu-id="70cbf-146">Run the Full-Text Indexing Wizard and enable **Statistical Semantics** on the **Select Table Columns** page for each column on which you want to create a semantic index.</span></span> <span data-ttu-id="70cbf-147">如需詳細資訊，包含如何啟動 [全文檢索索引精靈] 的相關資訊，請參閱 [使用全文檢索索引精靈](use-the-full-text-indexing-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="70cbf-147">For more information, including information about how to start the Full-Text Indexing Wizard, see [Use the Full-Text Indexing Wizard](use-the-full-text-indexing-wizard.md).</span></span>  
  
###  <a name="how-to-create-a-semantic-index-when-there-is-an-existing-full-text-index"></a><a name="HowToEnableAlter"></a><span data-ttu-id="70cbf-148">如何：在有現有全文檢索索引時建立語義索引</span><span class="sxs-lookup"><span data-stu-id="70cbf-148">How To: Create a Semantic Index When There Is an Existing Full-Text Index</span></span>  
 <span data-ttu-id="70cbf-149">當您使用 **ALTER FULLTEXT INDEX** 陳述式來改變現有的全文檢索索引時，可以加入語意索引。</span><span class="sxs-lookup"><span data-stu-id="70cbf-149">You can add semantic indexing when you alter an existing full-text index with the **ALTER FULLTEXT INDEX** statement.</span></span> <span data-ttu-id="70cbf-150">您也可以使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中的各種對話方塊來加入語意索引。</span><span class="sxs-lookup"><span data-stu-id="70cbf-150">You can also add semantic indexing by using various dialog boxes in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="70cbf-151">**使用 Transact-SQL 加入語意索引**</span><span class="sxs-lookup"><span data-stu-id="70cbf-151">**Add a semantic index by using Transact-SQL**</span></span>  
 <span data-ttu-id="70cbf-152">您可以針對想要加入語意索引的每個資料行，使用下面所述的選項來呼叫 **ALTER FULLTEXT INDEX** 陳述式。</span><span class="sxs-lookup"><span data-stu-id="70cbf-152">Call the **ALTER FULLTEXT INDEX** statement with the options described below for each column on which you want to add a semantic index.</span></span> <span data-ttu-id="70cbf-153">如需此陳述式之所有選項的詳細資訊，請參閱 [ALTER FULLTEXT INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-fulltext-index-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="70cbf-153">For more information about all the options for this statement, see [ALTER FULLTEXT INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-fulltext-index-transact-sql).</span></span>  
  
 <span data-ttu-id="70cbf-154">除非您指定其他選項，否則在呼叫 **ALTER** 之後，全文檢索和語意索引都會重新擴展。</span><span class="sxs-lookup"><span data-stu-id="70cbf-154">Both full-text and semantic indexes are repopulated after a call to **ALTER**, unless you specify otherwise.</span></span>  
  
-   <span data-ttu-id="70cbf-155">若只要將全文檢索索引加入資料行，請使用 **ADD** 語法。</span><span class="sxs-lookup"><span data-stu-id="70cbf-155">To add full-text indexing only to a column, use the **ADD** syntax.</span></span>  
  
-   <span data-ttu-id="70cbf-156">若要將全文檢索和語意索引都加入資料行，請使用 **ADD** 語法搭配 **STATISTICAL_SEMANTICS** 選項。</span><span class="sxs-lookup"><span data-stu-id="70cbf-156">To add both full-text and semantic indexing to a column, use the **ADD** syntax with the **STATISTICAL_SEMANTICS** option.</span></span>  
  
-   <span data-ttu-id="70cbf-157">若要將語意索引加入已啟用全文檢索索引的資料行，請使用 **ADD STATISTICAL_SEMANTICS** 選項。</span><span class="sxs-lookup"><span data-stu-id="70cbf-157">To add semantic indexing to a column that is already enabled for full-text indexing, use the **ADD STATISTICAL_SEMANTICS** option.</span></span> <span data-ttu-id="70cbf-158">在單一 **ALTER** 陳述式中，您只能將語意索引加入至一個資料行。</span><span class="sxs-lookup"><span data-stu-id="70cbf-158">You can only add semantic indexing to one column in a single **ALTER** statement.</span></span>  
  
 <span data-ttu-id="70cbf-159">**範例：將語意索引加入至已經具有全文檢索索引的資料行**</span><span class="sxs-lookup"><span data-stu-id="70cbf-159">**Example: Add semantic indexing to a column that already has full-text indexing**</span></span>  
  
 <span data-ttu-id="70cbf-160">下列範例會針對 AdventureWorks2012 範例資料庫中的 **Production.Document** 資料表改變現有的全文檢索索引。</span><span class="sxs-lookup"><span data-stu-id="70cbf-160">The following example alters an existing full-text index on **Production.Document** table in AdventureWorks2012 sample database.</span></span> <span data-ttu-id="70cbf-161">此範例會針對 **Production.Document** 資料表的 **Document** 資料行 (已經具有全文檢索索引) 加入語意索引。</span><span class="sxs-lookup"><span data-stu-id="70cbf-161">The example adds a semantic index on the **Document** column of the **Production.Document** table, which already has a full-text index.</span></span> <span data-ttu-id="70cbf-162">此範例會指定不要自動重新擴展索引。</span><span class="sxs-lookup"><span data-stu-id="70cbf-162">The example specifies that the index will not be repopulated automatically.</span></span>  
  
```sql  
ALTER FULLTEXT INDEX ON Production.Document  
    ALTER COLUMN Document  
        ADD Statistical_Semantics  
    WITH NO POPULATION  
GO  
```  
  
 <span data-ttu-id="70cbf-163">**使用 SQL Server Management Studio 加入語意索引**</span><span class="sxs-lookup"><span data-stu-id="70cbf-163">**Add a semantic index by using SQL Server Management Studio**</span></span>  
 <span data-ttu-id="70cbf-164">您可以在 [全文檢索索引屬性] 對話方塊的 [全文檢索索引資料行] 頁面上變更已啟用語意和全文檢索索引的資料行。</span><span class="sxs-lookup"><span data-stu-id="70cbf-164">You can change the columns that are enabled for semantic and full-text indexing on the **Full-Text Index Columns** page of the **Full-Text Index Properties** dialog box.</span></span> <span data-ttu-id="70cbf-165">如需詳細資訊，請參閱 [管理全文檢索索引](../../database-engine/manage-full-text-indexes.md)。</span><span class="sxs-lookup"><span data-stu-id="70cbf-165">For more information, see [Manage Full-Text Indexes](../../database-engine/manage-full-text-indexes.md).</span></span>  
  
###  <a name="requirements-and-restrictions-for-altering-an-existing-index"></a><a name="addreq"></a><span data-ttu-id="70cbf-166">改變現有索引的需求和限制</span><span class="sxs-lookup"><span data-stu-id="70cbf-166">Requirements and Restrictions for Altering an Existing Index</span></span>  
  
-   <span data-ttu-id="70cbf-167">當現有索引的母體擴展正在進行時，您無法改變該索引。</span><span class="sxs-lookup"><span data-stu-id="70cbf-167">You cannot alter an existing index while population of the index is in progress.</span></span> <span data-ttu-id="70cbf-168">如需監視索引母體擴展之進度的詳細資訊，請參閱 [管理及監視語意搜尋](manage-and-monitor-semantic-search.md)。</span><span class="sxs-lookup"><span data-stu-id="70cbf-168">For more information on monitoring the progress of index population, see [Manage and Monitor Semantic Search](manage-and-monitor-semantic-search.md).</span></span>  
  
-   <span data-ttu-id="70cbf-169">您無法在 **ALTER FULLTEXT INDEX** 陳述式的單一呼叫中，將索引加入至資料行，以及改變或卸除相同資料行的索引。</span><span class="sxs-lookup"><span data-stu-id="70cbf-169">You cannot add indexing to a column, and alter or drop indexing for the same column, in a single call to the **ALTER FULLTEXT INDEX** statement.</span></span>  
  
##  <a name="dropping-a-semantic-index"></a><a name="dropping"></a><span data-ttu-id="70cbf-170">卸載語義索引</span><span class="sxs-lookup"><span data-stu-id="70cbf-170">Dropping a Semantic Index</span></span>  
  
###  <a name="how-to-drop-a-semantic-index"></a><a name="drophow"></a><span data-ttu-id="70cbf-171">如何：卸載語義索引</span><span class="sxs-lookup"><span data-stu-id="70cbf-171">How to: Drop a Semantic Index</span></span>  
 <span data-ttu-id="70cbf-172">當您使用 **ALTER FULLTEXT INDEX** 陳述式來改變現有的全文檢索索引時，可以卸除語意索引。</span><span class="sxs-lookup"><span data-stu-id="70cbf-172">You can drop semantic indexing when you alter an existing full-text index with the **ALTER FULLTEXT INDEX** statement.</span></span> <span data-ttu-id="70cbf-173">您也可以使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中的各種對話方塊來卸除語意索引。</span><span class="sxs-lookup"><span data-stu-id="70cbf-173">You can also drop semantic indexing by using various dialog boxes in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="70cbf-174">**使用 Transact-SQL 卸除語意索引**</span><span class="sxs-lookup"><span data-stu-id="70cbf-174">**Drop a semantic index by using Transact-SQL**</span></span>  
 -   <span data-ttu-id="70cbf-175">若只要卸除一或多個資料行的語意索引，請使用 **ALTER COLUMN** column_name **DROP STATISTICAL_SEMANTICS***選項來呼叫***ALTER FULLTEXT INDEX** 陳述式。</span><span class="sxs-lookup"><span data-stu-id="70cbf-175">To drop semantic indexing only from a column or columns, call the **ALTER FULLTEXT INDEX** statement with the **ALTER COLUMN***column_name***DROP STATISTICAL_SEMANTICS** option.</span></span> <span data-ttu-id="70cbf-176">在單一 **ALTER** 陳述式中，您可以從多個資料行中卸除索引。</span><span class="sxs-lookup"><span data-stu-id="70cbf-176">You can drop the indexing from multiple columns in a single **ALTER** statement.</span></span>  
  
    ```sql  
    USE database_name  
    GO  
  
    ALTER FULLTEXT INDEX  
        ALTER COLUMN column_name  
        DROP STATISTICAL_SEMANTICS  
    GO  
    ```  
  
-   <span data-ttu-id="70cbf-177">若要同時卸載資料行的全文檢索和語義索引，請使用**ALTER column***column_name***drop**選項來呼叫**alter 全文檢索索引**語句。</span><span class="sxs-lookup"><span data-stu-id="70cbf-177">To drop both full-text and semantic indexing from a column, call the **ALTER FULLTEXT INDEX** statement with the **ALTER COLUMN***column_name***DROP** option.</span></span>  
  
    ```sql  
    USE database_name  
    GO  
  
    ALTER FULLTEXT INDEX  
        ALTER COLUMN column_name  
        DROP  
    GO  
    ```  
  
 <span data-ttu-id="70cbf-178">**使用 SQL Server Management Studio 卸除語意索引**</span><span class="sxs-lookup"><span data-stu-id="70cbf-178">**Drop a semantic index by using SQL Server Management Studio**</span></span>  
 <span data-ttu-id="70cbf-179">您可以在 [全文檢索索引屬性] 對話方塊的 [全文檢索索引資料行] 頁面上變更已啟用語意和全文檢索索引的資料行。</span><span class="sxs-lookup"><span data-stu-id="70cbf-179">You can change the columns that are enabled for semantic and full-text indexing on the **Full-Text Index Columns** page of the **Full-Text Index Properties** dialog box.</span></span> <span data-ttu-id="70cbf-180">如需詳細資訊，請參閱 [管理全文檢索索引](../../database-engine/manage-full-text-indexes.md)。</span><span class="sxs-lookup"><span data-stu-id="70cbf-180">For more information, see [Manage Full-Text Indexes](../../database-engine/manage-full-text-indexes.md).</span></span>  
  
###  <a name="requirements-and-restrictions-for-dropping-a-semantic-index"></a><a name="dropreq"></a><span data-ttu-id="70cbf-181">卸載語義索引的需求和限制</span><span class="sxs-lookup"><span data-stu-id="70cbf-181">Requirements and Restrictions for Dropping a Semantic Index</span></span>  
  
-   <span data-ttu-id="70cbf-182">您無法從資料行中卸除全文檢索索引，而保留語意索引。</span><span class="sxs-lookup"><span data-stu-id="70cbf-182">You cannot drop full-text indexing from a column while retaining semantic indexing.</span></span> <span data-ttu-id="70cbf-183">語意索引相依於全文檢索索引的文件相似度結果。</span><span class="sxs-lookup"><span data-stu-id="70cbf-183">Semantic indexing depends on full-text indexing for document similarity results.</span></span>  
  
-   <span data-ttu-id="70cbf-184">在已啟用語意索引的資料表中，當您從最後一個資料行中卸除語意索引時，就無法指定 **NO POPULATION** 選項。</span><span class="sxs-lookup"><span data-stu-id="70cbf-184">You cannot specify the **NO POPULATION** option when you drop semantic indexing from the last column in a table for which semantic indexing was enabled.</span></span> <span data-ttu-id="70cbf-185">若要移除先前已建立索引的結果，則需要使用母體擴展循環。</span><span class="sxs-lookup"><span data-stu-id="70cbf-185">A population cycle is required to remove the results that were indexed previously.</span></span>  
  
## <a name="checking-whether-semantic-search-is-enabled-on-database-objects"></a><span data-ttu-id="70cbf-186">檢查資料庫物件上是否啟用語意搜尋</span><span class="sxs-lookup"><span data-stu-id="70cbf-186">Checking Whether Semantic Search Is Enabled on Database Objects</span></span>  
  
###  <a name="how-to-check-whether-semantic-search-is-enabled-on-database-objects"></a><a name="HowToCheckEnabled"></a><span data-ttu-id="70cbf-187">如何：檢查是否已在資料庫物件上啟用語義搜尋</span><span class="sxs-lookup"><span data-stu-id="70cbf-187">How To: Check Whether Semantic Search Is Enabled on Database Objects</span></span>  
 <span data-ttu-id="70cbf-188">**是否已針對資料庫啟用語意搜尋？**</span><span class="sxs-lookup"><span data-stu-id="70cbf-188">**Is semantic search enabled for a database?**</span></span>  
 <span data-ttu-id="70cbf-189">查詢 [DATABASEPROPERTYEX &#40;Transact-SQL&#41;](/sql/t-sql/functions/databasepropertyex-transact-sql) 中繼資料函數的 **IsFullTextEnabled** 屬性。</span><span class="sxs-lookup"><span data-stu-id="70cbf-189">Query the **IsFullTextEnabled** property of the [DATABASEPROPERTYEX &#40;Transact-SQL&#41;](/sql/t-sql/functions/databasepropertyex-transact-sql) metadata function.</span></span>  
  
 <span data-ttu-id="70cbf-190">傳回值 1 表示已針對資料庫啟用全文檢索搜尋和語意搜尋，傳回值 0 表示未啟用這兩個搜尋。</span><span class="sxs-lookup"><span data-stu-id="70cbf-190">A return value of 1 indicates that full-text search and semantic search are enabled for the database; a return value of 0 indicates that they are not enabled.</span></span>  
  
```sql  
SELECT DATABASEPROPERTYEX('database_name', 'IsFullTextEnabled')  
GO  
```  
  
 <span data-ttu-id="70cbf-191">**是否已針對資料表啟用語意搜尋？**</span><span class="sxs-lookup"><span data-stu-id="70cbf-191">**Is semantic search enabled for a table?**</span></span>  
 <span data-ttu-id="70cbf-192">查詢 [OBJECTPROPERTYEX &#40;Transact-SQL&#41;](/sql/t-sql/functions/objectproperty-transact-sql) 中繼資料函數的 **TableFullTextSemanticExtraction** 屬性。</span><span class="sxs-lookup"><span data-stu-id="70cbf-192">Query the **TableFullTextSemanticExtraction** property of the [OBJECTPROPERTYEX &#40;Transact-SQL&#41;](/sql/t-sql/functions/objectproperty-transact-sql) metadata function.</span></span>  
  
 <span data-ttu-id="70cbf-193">傳回值 1 表示已針對資料表啟用語意搜尋，傳回值 0 表示未啟用此搜尋。</span><span class="sxs-lookup"><span data-stu-id="70cbf-193">A return value of 1 indicates that semantic search is enabled for the table; a return value of 0 indicates that it is not enabled.</span></span>  
  
```scr  
SELECT OBJECTPROPERTYEX(OBJECT_ID('table_name'), 'TableFullTextSemanticExtraction')  
GO  
```  
  
 <span data-ttu-id="70cbf-194">**是否已針對資料行啟用語意搜尋？**</span><span class="sxs-lookup"><span data-stu-id="70cbf-194">**Is semantic search enabled for a column?**</span></span>  
 <span data-ttu-id="70cbf-195">若要判斷是否已針對特定資料行啟用語意搜尋：</span><span class="sxs-lookup"><span data-stu-id="70cbf-195">To determine whether semantic search is enabled for a specific column:</span></span>  
  
-   <span data-ttu-id="70cbf-196">查詢 [COLUMNPROPERTY &#40;Transact-SQL&#41;](/sql/t-sql/functions/columnproperty-transact-sql) 中繼資料函數的 **StatisticalSemantics** 屬性。</span><span class="sxs-lookup"><span data-stu-id="70cbf-196">Query the **StatisticalSemantics** property of the [COLUMNPROPERTY &#40;Transact-SQL&#41;](/sql/t-sql/functions/columnproperty-transact-sql) metadata function.</span></span>  
  
     <span data-ttu-id="70cbf-197">傳回值 1 表示已針對資料行啟用語意搜尋，傳回值 0 表示未啟用此搜尋。</span><span class="sxs-lookup"><span data-stu-id="70cbf-197">A return value of 1 indicates that semantic search is enabled for the column; a return value of 0 indicates that it is not enabled.</span></span>  
  
    ```sql  
    SELECT COLUMNPROPERTY(OBJECT_ID('table_name'), 'column_name', 'StatisticalSemantics')  
    GO  
    ```  
  
-   <span data-ttu-id="70cbf-198">查詢目錄檢視 [sys.fulltext_index_columns &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-index-columns-transact-sql) 找出全文檢索索引。</span><span class="sxs-lookup"><span data-stu-id="70cbf-198">Query the catalog view [sys.fulltext_index_columns &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-index-columns-transact-sql) for the full-text index.</span></span>  
  
     <span data-ttu-id="70cbf-199">**statistical_semantics** 資料行中的值 1 表示指定的資料行除了啟用全文檢索索引以外，也啟用了語意索引。</span><span class="sxs-lookup"><span data-stu-id="70cbf-199">A value of 1 in the **statistical_semantics** column indicates that the specified column is enabled for semantic indexing in addition to full-text indexing.</span></span>  
  
    ```sql  
    SELECT * FROM sys.fulltext_index_columns WHERE object_id = OBJECT_ID('table_name')  
    GO  
    ```  
  
-   <span data-ttu-id="70cbf-200">在 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 的物件總管中，以滑鼠右鍵按一下資料行，然後選取 [屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="70cbf-200">In Object Explorer in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], right-click on a column and select **Properties**.</span></span> <span data-ttu-id="70cbf-201">在 **[資料行屬性]** 對話方塊的 **[一般]** 頁面上，檢查 **[Statistical Semantics]** 屬性的值。</span><span class="sxs-lookup"><span data-stu-id="70cbf-201">On the **General** page of the **Column Properties** dialog box, check the value of the **Statistical Semantics** property.</span></span>  
  
     <span data-ttu-id="70cbf-202">True 值表示指定的資料行除了啟用全文檢索索引以外，也啟用了語意索引。</span><span class="sxs-lookup"><span data-stu-id="70cbf-202">A value of True indicates that the specified column is enabled for semantic indexing in addition to full-text indexing.</span></span>  
  
## <a name="determining-what-can-be-indexed-for-semantic-search"></a><span data-ttu-id="70cbf-203">判斷可建立索引供語意搜尋使用的項目</span><span class="sxs-lookup"><span data-stu-id="70cbf-203">Determining What Can Be Indexed for Semantic Search</span></span>  
  
###  <a name="how-to-check-which-languages-are-supported-for-semantic-search"></a><a name="HowToCheckLanguages"></a><span data-ttu-id="70cbf-204">如何：檢查支援的語義搜尋語言</span><span class="sxs-lookup"><span data-stu-id="70cbf-204">How To: Check Which Languages Are Supported for Semantic Search</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="70cbf-205">支援語意索引的語言比支援全文檢索索引的語言要少。</span><span class="sxs-lookup"><span data-stu-id="70cbf-205">Fewer languages are supported for semantic indexing than for full-text indexing.</span></span> <span data-ttu-id="70cbf-206">因此，可能會有可建立索引供全文檢索搜尋，但無法用於語意搜尋的資料行。</span><span class="sxs-lookup"><span data-stu-id="70cbf-206">As a result, there may be columns that you can index for full-text search, but not for semantic search.</span></span>  
  
 <span data-ttu-id="70cbf-207">查詢目錄檢視 [sys.fulltext_semantic_languages &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-semantic-languages-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="70cbf-207">Query the catalog view [sys.fulltext_semantic_languages &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-semantic-languages-transact-sql).</span></span>  
  
```sql  
SELECT * FROM sys.fulltext_semantic_languages  
GO  
```  
  
 <span data-ttu-id="70cbf-208">下列是語意索引所支援的語言。</span><span class="sxs-lookup"><span data-stu-id="70cbf-208">The following languages are supported for semantic indexing.</span></span> <span data-ttu-id="70cbf-209">此清單代表 [sys.fulltext_semantic_languages &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-semantic-languages-transact-sql) 目錄檢視的輸出 (依據 LCID 排序)。</span><span class="sxs-lookup"><span data-stu-id="70cbf-209">This list represents the output of the catalog view [sys.fulltext_semantic_languages &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-semantic-languages-transact-sql), ordered by LCID.</span></span>  
  
|<span data-ttu-id="70cbf-210">語言</span><span class="sxs-lookup"><span data-stu-id="70cbf-210">Language</span></span>|<span data-ttu-id="70cbf-211">LCID</span><span class="sxs-lookup"><span data-stu-id="70cbf-211">LCID</span></span>|  
|--------------|----------|  
|<span data-ttu-id="70cbf-212">德文</span><span class="sxs-lookup"><span data-stu-id="70cbf-212">German</span></span>|<span data-ttu-id="70cbf-213">1031</span><span class="sxs-lookup"><span data-stu-id="70cbf-213">1031</span></span>|  
|<span data-ttu-id="70cbf-214">英文 (美國)</span><span class="sxs-lookup"><span data-stu-id="70cbf-214">English (US)</span></span>|<span data-ttu-id="70cbf-215">1033</span><span class="sxs-lookup"><span data-stu-id="70cbf-215">1033</span></span>|  
|<span data-ttu-id="70cbf-216">法文</span><span class="sxs-lookup"><span data-stu-id="70cbf-216">French</span></span>|<span data-ttu-id="70cbf-217">1036</span><span class="sxs-lookup"><span data-stu-id="70cbf-217">1036</span></span>|  
|<span data-ttu-id="70cbf-218">義大利文</span><span class="sxs-lookup"><span data-stu-id="70cbf-218">Italian</span></span>|<span data-ttu-id="70cbf-219">1040</span><span class="sxs-lookup"><span data-stu-id="70cbf-219">1040</span></span>|  
|<span data-ttu-id="70cbf-220">葡萄牙文 (巴西)</span><span class="sxs-lookup"><span data-stu-id="70cbf-220">Portuguese (Brazil)</span></span>|<span data-ttu-id="70cbf-221">1046</span><span class="sxs-lookup"><span data-stu-id="70cbf-221">1046</span></span>|  
|<span data-ttu-id="70cbf-222">俄文</span><span class="sxs-lookup"><span data-stu-id="70cbf-222">Russian</span></span>|<span data-ttu-id="70cbf-223">1049</span><span class="sxs-lookup"><span data-stu-id="70cbf-223">1049</span></span>|  
|<span data-ttu-id="70cbf-224">瑞典文</span><span class="sxs-lookup"><span data-stu-id="70cbf-224">Swedish</span></span>|<span data-ttu-id="70cbf-225">1053</span><span class="sxs-lookup"><span data-stu-id="70cbf-225">1053</span></span>|  
|<span data-ttu-id="70cbf-226">英文 (英國)</span><span class="sxs-lookup"><span data-stu-id="70cbf-226">English (UK)</span></span>|<span data-ttu-id="70cbf-227">2057</span><span class="sxs-lookup"><span data-stu-id="70cbf-227">2057</span></span>|  
|<span data-ttu-id="70cbf-228">葡萄牙文 (葡萄牙)</span><span class="sxs-lookup"><span data-stu-id="70cbf-228">Portuguese (Portugal)</span></span>|<span data-ttu-id="70cbf-229">2070</span><span class="sxs-lookup"><span data-stu-id="70cbf-229">2070</span></span>|  
|<span data-ttu-id="70cbf-230">西班牙文</span><span class="sxs-lookup"><span data-stu-id="70cbf-230">Spanish</span></span>|<span data-ttu-id="70cbf-231">3082</span><span class="sxs-lookup"><span data-stu-id="70cbf-231">3082</span></span>|  
  
###  <a name="how-to-determine-which-document-types-can-be-indexed"></a><a name="doctypes"></a><span data-ttu-id="70cbf-232">如何：判斷可以編制索引的檔案類型</span><span class="sxs-lookup"><span data-stu-id="70cbf-232">How To: Determine Which Document Types Can Be Indexed</span></span>  
 <span data-ttu-id="70cbf-233">查詢目錄檢視 [sys.fulltext_document_types &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-document-types-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="70cbf-233">Query the catalog view [sys.fulltext_document_types &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-document-types-transact-sql).</span></span>  
  
 <span data-ttu-id="70cbf-234">如果您想要索引的文件類型不在支援的類型清單中，則可能必須尋找、下載並安裝其他篩選。</span><span class="sxs-lookup"><span data-stu-id="70cbf-234">If the document type that you want to index is not in the list of supported types, then you may have to locate, download, and install additional filters.</span></span> <span data-ttu-id="70cbf-235">如需詳細資訊，請參閱 [檢視或變更已註冊的篩選與斷詞工具](view-or-change-registered-filters-and-word-breakers.md)。</span><span class="sxs-lookup"><span data-stu-id="70cbf-235">For more information, see [View or Change Registered Filters and Word Breakers](view-or-change-registered-filters-and-word-breakers.md).</span></span>  
  
##  <a name="best-practice-consider-creating-a-separate-filegroup-for-the-full-text-and-semantic-indexes"></a><a name="BestPracticeFilegroup"></a><span data-ttu-id="70cbf-236">最佳做法：請考慮為全文檢索和語義索引建立個別的檔案群組</span><span class="sxs-lookup"><span data-stu-id="70cbf-236">Best Practice: Consider Creating a Separate Filegroup for the Full-Text and Semantic Indexes</span></span>  
 <span data-ttu-id="70cbf-237">如果您有磁碟空間配置的顧慮，請考慮針對全文檢索和語意索引建立個別的檔案群組。</span><span class="sxs-lookup"><span data-stu-id="70cbf-237">Consider creating a separate filegroup for the full-text and semantic indexes if disk space allocation is a concern.</span></span> <span data-ttu-id="70cbf-238">語意索引與全文檢索索引會建立在相同的檔案群組中。</span><span class="sxs-lookup"><span data-stu-id="70cbf-238">The semantic indexes are created in the same filegroup as the full-text index.</span></span> <span data-ttu-id="70cbf-239">完整擴展的語意索引可能會包含大量資料。</span><span class="sxs-lookup"><span data-stu-id="70cbf-239">A fully populated semantic index may contain large amount of data.</span></span>  
  
##  <a name="BestPracticeUnderstand"></a>   
##  <a name="problem-searching-on-specific-column-returns-no-results"></a><a name="IssueNoResults"></a><span data-ttu-id="70cbf-240">問題：在特定資料行上搜尋不會傳回任何結果</span><span class="sxs-lookup"><span data-stu-id="70cbf-240">Problem: Searching on Specific Column Returns No Results</span></span>  
 <span data-ttu-id="70cbf-241">**您是否針對 Unicode 語言指定了非 Unicode LCID？**</span><span class="sxs-lookup"><span data-stu-id="70cbf-241">**Was a non-Unicode LCID specified for a Unicode language?**</span></span>  
 <span data-ttu-id="70cbf-242">您可以針對 LCID 代表只有 Unicode 字詞之語言 (例如俄文 LCID 1049) 的非 Unicode 資料行類型啟用語意索引。</span><span class="sxs-lookup"><span data-stu-id="70cbf-242">It is possible to enable semantic indexing on a non-Unicode column type with an LCID for a language that only has Unicode words, such as LCID 1049 for Russian.</span></span> <span data-ttu-id="70cbf-243">在此情況下，這個資料行的語意索引永遠不會傳回任何結果。</span><span class="sxs-lookup"><span data-stu-id="70cbf-243">In this case, no results will ever be returned from the semantic indexes on this column.</span></span>  
  
  
