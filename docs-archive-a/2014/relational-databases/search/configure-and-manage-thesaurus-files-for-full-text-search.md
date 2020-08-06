---
title: 設定及管理全文檢索搜尋的同義字檔案 | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- full-text indexes [SQL Server], thesaurus files
- thesaurus [full-text search], configuring
- thesaurus [full-text search]
ms.assetid: 3ef96a63-8a52-45be-9a1f-265bff400e54
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 67f0a5af7be4f41ce33692e5f28ad5adf676980c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710542"
---
# <a name="configure-and-manage-thesaurus-files-for-full-text-search"></a><span data-ttu-id="2e486-102">設定及管理全文檢索搜尋的同義字檔案</span><span class="sxs-lookup"><span data-stu-id="2e486-102">Configure and Manage Thesaurus Files for Full-Text Search</span></span>
  <span data-ttu-id="2e486-103">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]中，全文檢索查詢可以透過使用同義字 (Thesaurus) 搜尋使用者指定之詞彙的同義字 (Synonym)。</span><span class="sxs-lookup"><span data-stu-id="2e486-103">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], full-text queries can search for synonyms of user-specified terms through the use of a thesaurus.</span></span> <span data-ttu-id="2e486-104">「同義字」[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \*\* (thesaurus) 會針對特定語言定義一組同義字 (synonym)。</span><span class="sxs-lookup"><span data-stu-id="2e486-104">A [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] *thesaurus* defines a set of synonyms for a specific language.</span></span> <span data-ttu-id="2e486-105">系統管理員可以定義兩種同義字形式：展開集和取代集。</span><span class="sxs-lookup"><span data-stu-id="2e486-105">System administrators can define two forms of synonyms: expansion sets and replacement sets.</span></span> <span data-ttu-id="2e486-106">透過開發符合全文檢索資料的同義字，您可以有效地擴大針對該資料進行全文檢索查詢的範圍。</span><span class="sxs-lookup"><span data-stu-id="2e486-106">By developing a thesaurus tailored to your full-text data, you can effectively broaden the scope of full-text queries on that data.</span></span> <span data-ttu-id="2e486-107">同義字比對會針對所有 [FREETEXT](/sql/t-sql/queries/freetext-transact-sql) 和 [FREETEXTABLE](/sql/relational-databases/system-functions/freetexttable-transact-sql) 查詢以及指定 FORMSOF THESAURUS 子句的任何 [CONTAINS](/sql/t-sql/queries/contains-transact-sql) 和 [CONTAINSTABLE](/sql/relational-databases/system-functions/containstable-transact-sql) 查詢進行。</span><span class="sxs-lookup"><span data-stu-id="2e486-107">Thesaurus matching occurs for all [FREETEXT](/sql/t-sql/queries/freetext-transact-sql) and [FREETEXTABLE](/sql/relational-databases/system-functions/freetexttable-transact-sql) queries and for any [CONTAINS](/sql/t-sql/queries/contains-transact-sql) and [CONTAINSTABLE](/sql/relational-databases/system-functions/containstable-transact-sql) queries that specify the FORMSOF THESAURUS clause.</span></span>  
  
##  <a name="basic-tasks-for-setting-up-a-thesaurus-file"></a><a name="tasks"></a><span data-ttu-id="2e486-108">設定同義字檔案的基本工作</span><span class="sxs-lookup"><span data-stu-id="2e486-108">Basic Tasks for Setting Up a Thesaurus File</span></span>  
 <span data-ttu-id="2e486-109">您必須先針對給定的語言定義同義字 (thesaurus) 對應 (同義字)，然後伺服器執行個體上的全文檢索搜詢查詢才能尋找該語言的同義字 (synonym)。</span><span class="sxs-lookup"><span data-stu-id="2e486-109">Before full-text search queries on your server instance can look for synonyms in a given language, you must define thesaurus mappings (synonyms) for that language.</span></span> <span data-ttu-id="2e486-110">您必須手動設定每個同義字，以便定義下列項目：</span><span class="sxs-lookup"><span data-stu-id="2e486-110">Each thesaurus must be manually configured to define the following:</span></span>  
  
-   <span data-ttu-id="2e486-111">變音符號設定</span><span class="sxs-lookup"><span data-stu-id="2e486-111">Diacritics setting</span></span>  
  
     <span data-ttu-id="2e486-112">針對指定的同義字，所有搜尋模式都會區分或不區分變音符號，例如波狀符號 (**~**) 、銳角 (**？？**) ，或母音 (**？？**)  (也就是區分*重音*或不*區分重音*的) 。</span><span class="sxs-lookup"><span data-stu-id="2e486-112">For a given thesaurus, all search patterns are either sensitive or insensitive to diacritical marks such as a tilde (**~**), acute accent mark (**??**), or umlaut (**??**) (that is, *accent sensitive* or *accent insensitive*).</span></span> <span data-ttu-id="2e486-113">例如，假設您指定模式 "caf？？"</span><span class="sxs-lookup"><span data-stu-id="2e486-113">For example, suppose you specify the pattern "caf??"</span></span> <span data-ttu-id="2e486-114">由其他模式取代。</span><span class="sxs-lookup"><span data-stu-id="2e486-114">to be replaced by other patterns in a full-text query.</span></span> <span data-ttu-id="2e486-115">如果同義字不區分重音，全文檢索搜尋會取代 "caf？？" 模式</span><span class="sxs-lookup"><span data-stu-id="2e486-115">If the thesaurus is accent-insensitive, full-text search replaces the patterns "caf??"</span></span> <span data-ttu-id="2e486-116">與 "cafe"。</span><span class="sxs-lookup"><span data-stu-id="2e486-116">and "cafe".</span></span> <span data-ttu-id="2e486-117">如果同義字區分重音，則全文檢索搜尋只會取代模式 "caf？？"。</span><span class="sxs-lookup"><span data-stu-id="2e486-117">If the thesaurus is accent-sensitive, full-text search replaces only the pattern "caf??".</span></span> <span data-ttu-id="2e486-118">根據預設，同義字不會區分腔調字。</span><span class="sxs-lookup"><span data-stu-id="2e486-118">By default, a thesaurus is accent-insensitive.</span></span>  
  
-   <span data-ttu-id="2e486-119">展開集</span><span class="sxs-lookup"><span data-stu-id="2e486-119">Expansion set</span></span>  
  
     <span data-ttu-id="2e486-120">展開集包含可以由全文檢索查詢彼此替代的一組同義字，例如 "writer"、"author" 和 "journalist"。</span><span class="sxs-lookup"><span data-stu-id="2e486-120">An expansion set contains a group of synonyms such as "writer", "author", and "journalist" that are substituted for one another by a full-text query.</span></span> <span data-ttu-id="2e486-121">包含展開集中任何同義字之相符項目的查詢會展開成包含展開集中的其他每個同義字。</span><span class="sxs-lookup"><span data-stu-id="2e486-121">Queries that contain a match for any synonym in an expansion set are expanded to include every other synonym in the expansion set.</span></span>  
  
     <span data-ttu-id="2e486-122">如需詳細資訊，請參閱本主題後面的「展開集的 XML 結構」。</span><span class="sxs-lookup"><span data-stu-id="2e486-122">For more information, see "XML Structure of an Expansion Set," later in this topic.</span></span>  
  
-   <span data-ttu-id="2e486-123">取代集</span><span class="sxs-lookup"><span data-stu-id="2e486-123">Replacement set</span></span>  
  
     <span data-ttu-id="2e486-124">取代集包含替代集所要取代的文字模式。</span><span class="sxs-lookup"><span data-stu-id="2e486-124">A replacement set contains a text pattern to be replaced by a substitution set.</span></span> <span data-ttu-id="2e486-125">如需範例，請參閱本主題後面的＜取代集的 XML 結構＞一節。</span><span class="sxs-lookup"><span data-stu-id="2e486-125">For an example, see the section "XML Structure of a Replacement Set" later in this topic.</span></span>  
  
  
##  <a name="initial-content-of-the-thesaurus-files"></a><a name="initial_thesaurus_files"></a><span data-ttu-id="2e486-126">同義字檔案的初始內容</span><span class="sxs-lookup"><span data-stu-id="2e486-126">Initial Content of the Thesaurus Files</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="2e486-127">提供了一組 XML 同義字檔案 (每個支援的語言都有一個檔案)。</span><span class="sxs-lookup"><span data-stu-id="2e486-127">provides a set of XML thesaurus files, one for each supported language.</span></span> <span data-ttu-id="2e486-128">這些檔案基本上都是空的。</span><span class="sxs-lookup"><span data-stu-id="2e486-128">These files are essentially empty.</span></span> <span data-ttu-id="2e486-129">它們僅包含所有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 同義字通用的最上層 XML 結構以及標記為註解的範例同義字。</span><span class="sxs-lookup"><span data-stu-id="2e486-129">They contain only the top-level XML structure that is common to all [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] thesauruses and a commented-out sample thesaurus.</span></span>  
  
 <span data-ttu-id="2e486-130">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 隨附的同義字檔案都包含下列 XML 程式碼：</span><span class="sxs-lookup"><span data-stu-id="2e486-130">The thesaurus files that are released with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] all contain the following XML code:</span></span>  
  
```  
<XML ID="Microsoft Search Thesaurus">  
  
<!--  Commented out  
  
    <thesaurus xmlns="x-schema:tsSchema.xml">  
<diacritics_sensitive>0</diacritics_sensitive>  
        <expansion>  
            <sub>Internet Explorer</sub>  
            <sub>IE</sub>  
            <sub>IE5</sub>  
        </expansion>  
        <replacement>  
            <pat>NT5</pat>  
            <pat>W2K</pat>  
            <sub>Windows 2012</sub>  
        </replacement>  
        <expansion>  
            <sub>run</sub>  
            <sub>jog</sub>  
        </expansion>  
    </thesaurus>  
-->  
</XML>  
```  
  
  
##  <a name="location-of-the-thesaurus-files"></a><a name="location"></a><span data-ttu-id="2e486-131">同義字檔案的位置</span><span class="sxs-lookup"><span data-stu-id="2e486-131">Location of the Thesaurus Files</span></span>  
 <span data-ttu-id="2e486-132">同義字檔案的預設位置為：</span><span class="sxs-lookup"><span data-stu-id="2e486-132">The default location of the thesaurus files is:</span></span>  
  
 <span data-ttu-id="2e486-133">*<SQL_Server_data_files_path>* \MSSQL12。MSSQLSERVER\MSSQL\FTDATA</span><span class="sxs-lookup"><span data-stu-id="2e486-133">*<SQL_Server_data_files_path>* \MSSQL12.MSSQLSERVER\MSSQL\FTDATA</span></span>\  
  
 <span data-ttu-id="2e486-134">這個預設位置包含下列檔案：</span><span class="sxs-lookup"><span data-stu-id="2e486-134">This default location contains the following files:</span></span>  
  
-   <span data-ttu-id="2e486-135">語言特有的同義字檔案</span><span class="sxs-lookup"><span data-stu-id="2e486-135">Language-specific thesaurus files</span></span>  
  
     <span data-ttu-id="2e486-136">安裝期間，空的同義字檔案會安裝在上述位置。</span><span class="sxs-lookup"><span data-stu-id="2e486-136">During setup, empty thesaurus files are installed in the above location.</span></span> <span data-ttu-id="2e486-137">系統會針對每個支援的語言提供一個個別的檔案。</span><span class="sxs-lookup"><span data-stu-id="2e486-137">A separate file is provided for each supported language.</span></span> <span data-ttu-id="2e486-138">系統管理員可以自訂這些檔案。</span><span class="sxs-lookup"><span data-stu-id="2e486-138">A system administrator can customize these files.</span></span>  
  
     <span data-ttu-id="2e486-139">同義字檔案的預設檔案名稱會使用下列格式：</span><span class="sxs-lookup"><span data-stu-id="2e486-139">The default file names of the thesaurus files use following format:</span></span>  
  
     <span data-ttu-id="2e486-140">' ts ' + \<three-letter language-abbreviation> + ' .xml '</span><span class="sxs-lookup"><span data-stu-id="2e486-140">'ts' + \<three-letter language-abbreviation> + '.xml'</span></span>  
  
     <span data-ttu-id="2e486-141">給定語言之同義字檔案的名稱是使用下列值指定於登錄中：HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\\<執行個體名稱>\MSSearch\\<語言縮寫>。</span><span class="sxs-lookup"><span data-stu-id="2e486-141">The name of the thesaurus file for a given language is specified in the registry in the following value HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\\<instance-name>\MSSearch\\<language-abbrev>.</span></span>  
  
-   <span data-ttu-id="2e486-142">通用同義字檔案</span><span class="sxs-lookup"><span data-stu-id="2e486-142">The global thesaurus file</span></span>  
  
     <span data-ttu-id="2e486-143">空的通用同義字檔案：tsGlobal.xml。</span><span class="sxs-lookup"><span data-stu-id="2e486-143">An empty global thesaurus file, tsGlobal.xml.</span></span>  
  
 <span data-ttu-id="2e486-144">您可以變更同義字檔案的登錄機碼，藉以變更其位置和名稱。</span><span class="sxs-lookup"><span data-stu-id="2e486-144">You can change the location and names of a thesaurus file by changing its registry key.</span></span> <span data-ttu-id="2e486-145">針對每個語言，同義字檔案的位置會指定在下列登錄值中：</span><span class="sxs-lookup"><span data-stu-id="2e486-145">For each language, the location of the thesaurus file is specified in the following value in the registry:</span></span>  
  
 <span data-ttu-id="2e486-146">HKLM/SOFTWARE/Microsoft/Microsoft SQL Server/ \<instance name> /MSSearch/Language/ \<language-abbreviation> /TsaurusFile</span><span class="sxs-lookup"><span data-stu-id="2e486-146">HKLM/SOFTWARE/Microsoft/Microsoft SQL Server/\<instance name>/MSSearch/Language/\<language-abbreviation>/TsaurusFile</span></span>  
  
 <span data-ttu-id="2e486-147">通用同義字檔案會對應至 LCID 0 的中性語言。</span><span class="sxs-lookup"><span data-stu-id="2e486-147">The global thesaurus file corresponds to the Neutral language with LCID 0.</span></span> <span data-ttu-id="2e486-148">只有管理員能夠變更這個值。</span><span class="sxs-lookup"><span data-stu-id="2e486-148">This value can be changed by administrators only.</span></span>  
  
  
##  <a name="how-queries-use-thesaurus-files"></a><a name="how_queries_use_tf"></a><span data-ttu-id="2e486-149">查詢如何使用同義字檔案</span><span class="sxs-lookup"><span data-stu-id="2e486-149">How Queries Use Thesaurus Files</span></span>  
 <span data-ttu-id="2e486-150">同義字查詢會同時使用語言特有的同義字和通用同義字。</span><span class="sxs-lookup"><span data-stu-id="2e486-150">A thesaurus query uses both a language-specific thesaurus and the global thesaurus.</span></span> <span data-ttu-id="2e486-151">首先，查詢會查閱語言特有的檔案並載入此檔案，以便進行處理 (除非已經載入此檔案)。</span><span class="sxs-lookup"><span data-stu-id="2e486-151">First, the query looks up the language-specific file and loads it for processing (unless it is already loaded).</span></span> <span data-ttu-id="2e486-152">查詢會展開成包含同義字 (Thesaurus) 檔案中展開集和取代集規則所指定的語言特有同義字 (Synonym)。</span><span class="sxs-lookup"><span data-stu-id="2e486-152">The query is expanded to include the language-specific synonyms specified by the expansion set and replacement set rules in the thesaurus file.</span></span> <span data-ttu-id="2e486-153">然後，系統會針對通用同義字重複這些步驟。</span><span class="sxs-lookup"><span data-stu-id="2e486-153">These steps are then repeated for the global thesaurus.</span></span> <span data-ttu-id="2e486-154">不過，如果某個詞彙已經是語言特有同義字檔案中相符項目的一部分，該詞彙就不適用於在通用同義字中比對。</span><span class="sxs-lookup"><span data-stu-id="2e486-154">However, if a term is already part of a match in the language specific thesaurus file, the term is ineligible for matching in the global thesaurus.</span></span>  
  
  
##  <a name="understanding-the-structure-of-a-thesaurus-file"></a><a name="structure"></a><span data-ttu-id="2e486-155">瞭解同義字檔案的結構</span><span class="sxs-lookup"><span data-stu-id="2e486-155">Understanding the Structure of a Thesaurus File</span></span>  
 <span data-ttu-id="2e486-156">每個同義字檔案都會定義識別碼為 `Microsoft Search Thesaurus` 的 XML 容器，以及包含範例同義字的 `<!--` ... `-->` 註解。</span><span class="sxs-lookup"><span data-stu-id="2e486-156">Each thesaurus file defines an XML container whose ID is `Microsoft Search Thesaurus`, and a comment, `<!--` ... `-->`, that contains a sample thesaurus.</span></span> <span data-ttu-id="2e486-157">同義字定義于 \<thesaurus> 包含子項目範例的元素中，這些專案會定義變音符號設定、擴充集和取代集，如下所示：</span><span class="sxs-lookup"><span data-stu-id="2e486-157">The thesaurus is defined in a \<thesaurus> element that contains samples of the child elements that define the diacritics setting, expansion sets, and replacement sets, as follows:</span></span>  
  
-   <span data-ttu-id="2e486-158">變音符號設定的 XML 結構</span><span class="sxs-lookup"><span data-stu-id="2e486-158">XML Structure of the Diacritical Setting</span></span>  
  
     <span data-ttu-id="2e486-159">同義字的變音符號設定指定於單一 <diacritics_sensitive> 元素中。</span><span class="sxs-lookup"><span data-stu-id="2e486-159">The diacritics setting of a thesaurus is specified in a single <diacritics_sensitive> element.</span></span> <span data-ttu-id="2e486-160">這個元素包含可控制區分腔調字的整數值，如下所示：</span><span class="sxs-lookup"><span data-stu-id="2e486-160">This element contains an integer value that controls accent sensitivity, as follows:</span></span>  
  
    |<span data-ttu-id="2e486-161">變音符號設定</span><span class="sxs-lookup"><span data-stu-id="2e486-161">Diacritics Setting</span></span>|<span data-ttu-id="2e486-162">值</span><span class="sxs-lookup"><span data-stu-id="2e486-162">Value</span></span>|<span data-ttu-id="2e486-163">XML</span><span class="sxs-lookup"><span data-stu-id="2e486-163">XML</span></span>|  
    |------------------------|-----------|---------|  
    |<span data-ttu-id="2e486-164">不區分腔調字</span><span class="sxs-lookup"><span data-stu-id="2e486-164">Accent insensitive</span></span>|<span data-ttu-id="2e486-165">0</span><span class="sxs-lookup"><span data-stu-id="2e486-165">0</span></span>|`<diacritics_sensitive>0</diacritics_sensitive>`|  
    |<span data-ttu-id="2e486-166">區分腔調字</span><span class="sxs-lookup"><span data-stu-id="2e486-166">Accent sensitive</span></span>|<span data-ttu-id="2e486-167">1</span><span class="sxs-lookup"><span data-stu-id="2e486-167">1</span></span>|`<diacritics_sensitive>1</diacritics_sensitive>`|  
  
    > [!NOTE]  
    >  <span data-ttu-id="2e486-168">此設定只能在檔案中套用一次，而且它會套用至檔案中的所有搜尋模式。</span><span class="sxs-lookup"><span data-stu-id="2e486-168">This setting can only be applied one time in the file, and it applies to all search patterns in the file.</span></span> <span data-ttu-id="2e486-169">不能針對個別模式指定此設定。</span><span class="sxs-lookup"><span data-stu-id="2e486-169">This setting cannot be specified for individual patterns.</span></span>  
  
-   <span data-ttu-id="2e486-170">展開集的 XML 結構</span><span class="sxs-lookup"><span data-stu-id="2e486-170">XML Structure of an Expansion Set</span></span>  
  
     <span data-ttu-id="2e486-171">每個展開集都是用 \<expansion> 元素括住。</span><span class="sxs-lookup"><span data-stu-id="2e486-171">Each expansion set is enclosed within an \<expansion> element.</span></span> <span data-ttu-id="2e486-172">在這個元素內，您可以使用 \<sub> 元素來指定一或多個替代項目。</span><span class="sxs-lookup"><span data-stu-id="2e486-172">Within this element, you specify one or more substitutions in a \<sub> element.</span></span> <span data-ttu-id="2e486-173">在展開集中，您可以指定一組彼此是同義字的替代項目。</span><span class="sxs-lookup"><span data-stu-id="2e486-173">In the expansion set, you can specify a group of substitutions that are synonyms of each other.</span></span>  
  
     <span data-ttu-id="2e486-174">例如，您可編輯展開區段，以將 "writer"、"author" 及 "journalist" 替代字視為同義字。</span><span class="sxs-lookup"><span data-stu-id="2e486-174">For example, you can edit the expansion section to treat the substitutions "writer", "author", and "journalist" as synonyms.</span></span> <span data-ttu-id="2e486-175">此時會展開包含某個替代項目之相符項目的全文檢索搜尋查詢，以併入展開集中指定的所有其他替代項目。</span><span class="sxs-lookup"><span data-stu-id="2e486-175">full-text search queries that contain matches in one substitution are expanded to include all other substitutions specified in the expansion set.</span></span> <span data-ttu-id="2e486-176">因此，在上個範例中，發出 FORMS OF THESAURUS 或 FREETEXT 查詢以尋找 "author" 這個字時，全文檢索搜尋也會傳回內含 "writer" 和 "journalist" 這些字的搜尋結果。</span><span class="sxs-lookup"><span data-stu-id="2e486-176">Therefore, in the preceding example, when you issue a FORMS OF THESAURUS or a FREETEXT query for the word "author", full-text search also returns search results containing the words "writer" and "journalist".</span></span>  
  
     <span data-ttu-id="2e486-177">這是上例之展開集區段的樣子：</span><span class="sxs-lookup"><span data-stu-id="2e486-177">This is what the expansion set section would look like for the above example:</span></span>  
  
    ```  
    <expansion>  
            <sub>writer</sub>  
            <sub>author</sub>  
            <sub>journalist</sub>  
    </expansion>  
    ```  
  
-   <span data-ttu-id="2e486-178">取代集的 XML 結構</span><span class="sxs-lookup"><span data-stu-id="2e486-178">XML Structure of a Replacement Set</span></span>  
  
     <span data-ttu-id="2e486-179">每個取代集都是用 \<replacement> 元素括住。</span><span class="sxs-lookup"><span data-stu-id="2e486-179">Each replacement set is enclosed within a \<replacement> element.</span></span> <span data-ttu-id="2e486-180">在這個元素內，您可以使用 \<pat> 元素來指定一或多個模式，並使用 \<sub> 元素來指定零或多個替代項目 (每個同義字指定一個)。</span><span class="sxs-lookup"><span data-stu-id="2e486-180">Within this element you can specify one or more patterns in a \<pat> element and zero or more substitutions in \<sub> elements, one per synonym.</span></span> <span data-ttu-id="2e486-181">您也可以指定要用替代集取代的模式。</span><span class="sxs-lookup"><span data-stu-id="2e486-181">You can specify a pattern to be replaced by a substitution set.</span></span> <span data-ttu-id="2e486-182">模式和替代項目都可以包含單字或一串文字。</span><span class="sxs-lookup"><span data-stu-id="2e486-182">Patterns and substitutions can contain a word, or a sequence of words.</span></span> <span data-ttu-id="2e486-183">如果沒有針對某個模式指定替代項目，其作用就是從使用者查詢中移除該模式。</span><span class="sxs-lookup"><span data-stu-id="2e486-183">If there is no substitution specified for a pattern, it has the effect of removing the pattern from the user query.</span></span>  
  
     <span data-ttu-id="2e486-184">例如，假設您想要查詢 "Win8" (模式) 以將其取代為 "Windows Server 2012" 或 "Windows 8.0" (替代項目)。</span><span class="sxs-lookup"><span data-stu-id="2e486-184">For example, suppose you want queries for "Win8", the pattern, to be replaced by "Windows Server 2012" or "Windows 8.0", the substitutions.</span></span> <span data-ttu-id="2e486-185">如果您要執行全文檢索查詢以找出 "Win8"，則全文檢索搜尋只會傳回內含 "Windows Server 2012" 或 "Windows 8.0" 的搜尋結果。</span><span class="sxs-lookup"><span data-stu-id="2e486-185">If you run a full-text query for "Win8", full-text search only returns search results containing "Windows Server 2012" or "Windows 8.0".</span></span> <span data-ttu-id="2e486-186">它不會傳回內含 "Win8" 的結果。</span><span class="sxs-lookup"><span data-stu-id="2e486-186">It does not return results containing "Win8".</span></span> <span data-ttu-id="2e486-187">這是因為 "Win8" 模式已「取代」為 "Windows Server 2012" 和 "Windows 8.0" 模式。</span><span class="sxs-lookup"><span data-stu-id="2e486-187">This is because the pattern "Win8" has been "replaced" by the patterns "Windows Server 2012" and "Windows 8.0".</span></span>  
  
     <span data-ttu-id="2e486-188">這是上例之取代集區段的樣子：</span><span class="sxs-lookup"><span data-stu-id="2e486-188">This is what the replacement set section would look like for the above example:</span></span>  
  
    ```  
    <replacement>  
            <pat>Win8</pat>  
            <sub>Windows Server 2012</sub>  
            <sub>Windows 8.0</sub>  
    </replacement>  
    ```  
  
     <span data-ttu-id="2e486-189">如果您有兩個相似模式相符的取代集，則這兩個取代集中長度較長之取代集的優先順序較高。</span><span class="sxs-lookup"><span data-stu-id="2e486-189">If you have two replacement sets with similar patterns being matched, the longer of the two takes precedence.</span></span> <span data-ttu-id="2e486-190">例如，如果您執行 FORMS OF THESAURUS 查詢以找出 "Internet Explorer online community" 且具有下列取代集，則 "Internet Explorer" 取代集的優先順序高於 "Internet" 取代集。</span><span class="sxs-lookup"><span data-stu-id="2e486-190">For example, if you run a FORMS OF THESAURUS query for "Internet Explorer online community" and you have the following replacement sets, the "Internet Explorer" replacement set takes precedence over the "Internet" replacement set.</span></span> <span data-ttu-id="2e486-191">因此，系統會將該查詢處理為 "IE online community" 或 "IE 9 online community"。</span><span class="sxs-lookup"><span data-stu-id="2e486-191">The query will therefore be processed as "IE online community" or "IE 9 online community".</span></span>  
  
    ```  
    <replacement>  
             <pat>Internet</pat>  
             <sub>intranet</sub>  
    </replacement>  
    ```  
  
     <span data-ttu-id="2e486-192">和</span><span class="sxs-lookup"><span data-stu-id="2e486-192">and</span></span>  
  
    ```  
    <replacement>  
             <pat>Internet Explorer</pat>  
             <sub>IE</sub>  
             <sub>IE 9</sub>  
    </replacement>  
    ```  
  
  
##  <a name="working-with-thesaurus-files"></a><a name="working_with_thesaurus_files"></a><span data-ttu-id="2e486-193">使用同義字檔案</span><span class="sxs-lookup"><span data-stu-id="2e486-193">Working with Thesaurus Files</span></span>  
 <span data-ttu-id="2e486-194">**編輯同義字檔案**</span><span class="sxs-lookup"><span data-stu-id="2e486-194">**To edit a thesaurus file**</span></span>  
  
-   [<span data-ttu-id="2e486-195">編輯同義字檔案</span><span class="sxs-lookup"><span data-stu-id="2e486-195">Editing a Thesaurus File</span></span>](#editing)  
  
 <span data-ttu-id="2e486-196">**載入更新的同義字檔案**</span><span class="sxs-lookup"><span data-stu-id="2e486-196">**To load an updated thesaurus file**</span></span>  
  
-   [<span data-ttu-id="2e486-197">sp_fulltext_load_thesaurus_file &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="2e486-197">sp_fulltext_load_thesaurus_file &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-fulltext-load-thesaurus-file-transact-sql)  
  
 <span data-ttu-id="2e486-198">**檢視斷詞工具、同義字及停用字詞表組合的 Token 化結果**</span><span class="sxs-lookup"><span data-stu-id="2e486-198">**To view the tokenization result of a word breaker, thesaurus, and stoplist combination**</span></span>  
  
-   [<span data-ttu-id="2e486-199">sys.dm_fts_parser &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="2e486-199">sys.dm_fts_parser &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-parser-transact-sql)  
  
  
##  <a name="editing-a-thesaurus-file"></a><a name="editing"></a><span data-ttu-id="2e486-200">編輯同義字檔案</span><span class="sxs-lookup"><span data-stu-id="2e486-200">Editing a Thesaurus File</span></span>  
 <span data-ttu-id="2e486-201">您可以透過編輯給定語言的同義字檔案 (XML 檔案)，設定同義字。</span><span class="sxs-lookup"><span data-stu-id="2e486-201">The thesaurus for a given language can be configured by editing its thesaurus file (an XML file).</span></span> <span data-ttu-id="2e486-202">在安裝期間， \<xml> 會安裝只包含容器和已標記為批註之範例元素的空白同義字檔案 \<thesaurus> 。</span><span class="sxs-lookup"><span data-stu-id="2e486-202">During setup, empty thesaurus files that contain only the \<xml> container and a commented-out sample \<thesaurus> element are installed.</span></span> <span data-ttu-id="2e486-203">為了讓搜尋同義字的全文檢索搜尋查詢能夠正常運作，您必須建立 \<thesaurus> 定義一組同義字的實際元素。</span><span class="sxs-lookup"><span data-stu-id="2e486-203">In order for full-text search queries that look for synonyms to work properly, you must create an actual \<thesaurus> element that defines a set of synonyms.</span></span> <span data-ttu-id="2e486-204">您可以定義兩種同義字形式：展開集和取代集。</span><span class="sxs-lookup"><span data-stu-id="2e486-204">You can define two forms of synonyms, expansion sets and replacement sets.</span></span>  
  
 <span data-ttu-id="2e486-205">**同義字檔案的限制**</span><span class="sxs-lookup"><span data-stu-id="2e486-205">**Restrictions for thesaurus files**</span></span>  
  
 <span data-ttu-id="2e486-206">當您編輯同義字檔案時，就會適用下列限制：</span><span class="sxs-lookup"><span data-stu-id="2e486-206">The following restrictions apply to editing a thesaurus file:</span></span>  
  
-   <span data-ttu-id="2e486-207">只有系統管理員能夠更新、修改或刪除同義字檔案。</span><span class="sxs-lookup"><span data-stu-id="2e486-207">Only system administrators can update, modify, or delete thesaurus files.</span></span>  
  
-   <span data-ttu-id="2e486-208">當您使用文字編輯器工具編輯同義字檔案時，必須以 Unicode 格式儲存這些檔案，而且必須指定位元組順序標示 (BOM)。</span><span class="sxs-lookup"><span data-stu-id="2e486-208">When editing thesaurus files using text editor tools, the files must be saved in Unicode format, and Byte Order Marks must be specified.</span></span>  
  
-   <span data-ttu-id="2e486-209">同義字項目不得為空白或斷詞為空字串。</span><span class="sxs-lookup"><span data-stu-id="2e486-209">Thesaurus entries cannot be empty or word break to an empty string.</span></span>  
  
-   <span data-ttu-id="2e486-210">同義字檔案中的片語長度不得超過 512 個字元。</span><span class="sxs-lookup"><span data-stu-id="2e486-210">Phrases in the thesaurus file must be no longer than 512 characters.</span></span>  
  
-   <span data-ttu-id="2e486-211">在展開集的 \<sub> 項目與取代集的 \<pat> 元素之間，同義字不得包含任何重複的項目。</span><span class="sxs-lookup"><span data-stu-id="2e486-211">A thesaurus must not contain any duplicate entries among the \<sub> entries of expansion sets and the \<pat> elements of replacement sets.</span></span>  
  
 <span data-ttu-id="2e486-212">**同義字檔案的建議**</span><span class="sxs-lookup"><span data-stu-id="2e486-212">**Recommendations for thesaurus files**</span></span>  
  
 <span data-ttu-id="2e486-213">我們建議同義字檔案中的項目不應該包含任何特殊字元。</span><span class="sxs-lookup"><span data-stu-id="2e486-213">We recommend that entries in the thesaurus file contain no special characters.</span></span> <span data-ttu-id="2e486-214">這是因為斷詞工具在處理特殊字元方面具有難以察覺的行為。</span><span class="sxs-lookup"><span data-stu-id="2e486-214">This is because word breakers have subtle behaviors with respect to special characters.</span></span> <span data-ttu-id="2e486-215">如果某個同義字項目包含任何特殊字元，與該項目搭配使用的斷詞工具可能會針對全文檢索查詢產生難以察覺的行為隱含。</span><span class="sxs-lookup"><span data-stu-id="2e486-215">If a thesaurus entry contains any special characters, word breakers used in combination with that entry can have subtle behavioral implications for a full-text query.</span></span>  
  
 <span data-ttu-id="2e486-216">建議您不要在 \<sub> 項目中包含任何停用字詞，因為全文檢索索引會省略停用字詞。</span><span class="sxs-lookup"><span data-stu-id="2e486-216">We recommend that \<sub> entries contain no stopwords since stopwords are omitted from the full-text index.</span></span> <span data-ttu-id="2e486-217">系統會展開查詢以包含來自同義字檔案的 \<sub> 項目；如果 \<sub> 項目包含停用字詞，就會不必要地增加查詢的大小。</span><span class="sxs-lookup"><span data-stu-id="2e486-217">Queries are expanded to include the \<sub> entries from a thesaurus file, and if a \<sub> entry contains stopwords, query size increases unnecessarily.</span></span>  
  
#### <a name="to-edit-a-thesaurus-file"></a><span data-ttu-id="2e486-218">編輯同義字檔案</span><span class="sxs-lookup"><span data-stu-id="2e486-218">To edit a thesaurus file</span></span>  
  
1.  <span data-ttu-id="2e486-219">在 [記事本] 中，開啟同義字檔案。</span><span class="sxs-lookup"><span data-stu-id="2e486-219">Open the thesaurus file in Notepad.</span></span>  
  
2.  <span data-ttu-id="2e486-220">如果是第一次編輯同義字檔案，則請分別移除檔案開頭及結尾處的下列註解行：</span><span class="sxs-lookup"><span data-stu-id="2e486-220">If you are editing the thesaurus file for the first time, remove the following comment lines at the beginning and end of the file, respectively:</span></span>  
  
    ```  
    <!--Commented out  
    -->  
    ```  
  
3.  <span data-ttu-id="2e486-221">加入、修改或刪除取代集或展開集。</span><span class="sxs-lookup"><span data-stu-id="2e486-221">Add, modify, or delete a replacement set, or expansion set.</span></span>  
  
4.  <span data-ttu-id="2e486-222">儲存檔案並關閉記事本。</span><span class="sxs-lookup"><span data-stu-id="2e486-222">Save the file and close Notepad.</span></span>  
  
5.  <span data-ttu-id="2e486-223">使用 [sp_fulltext_load_thesaurus_file](/sql/relational-databases/system-stored-procedures/sp-fulltext-load-thesaurus-file-transact-sql) ，將同義字檔案的內容載入 tempdb，並指定對應至同義字檔案語言的地區設定識別碼 (LCID)。</span><span class="sxs-lookup"><span data-stu-id="2e486-223">Use [sp_fulltext_load_thesaurus_file](/sql/relational-databases/system-stored-procedures/sp-fulltext-load-thesaurus-file-transact-sql) to load the content of the thesaurus file into tempdb, specifying the local identifier (LCID) that corresponds to the language of the thesaurus file.</span></span> <span data-ttu-id="2e486-224">例如，英文同義字檔案 tsenu.xml 的對應 LCID 就是 1033。</span><span class="sxs-lookup"><span data-stu-id="2e486-224">For example, for the English thesaurus file, tsenu.xml, the corresponding LCID is 1033.</span></span>  
  
    ```  
    USE AdventureWorks2012 ;  
    EXEC sys.sp_fulltext_load_thesaurus_file 1033;  
    GO  
    ```  
  
  
## <a name="see-also"></a><span data-ttu-id="2e486-225">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2e486-225">See Also</span></span>  
 <span data-ttu-id="2e486-226">[CONTAINS &#40;Transact-SQL&#41;](/sql/t-sql/queries/contains-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="2e486-226">[CONTAINS &#40;Transact-SQL&#41;](/sql/t-sql/queries/contains-transact-sql) </span></span>  
 <span data-ttu-id="2e486-227">[CONTAINSTABLE &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/containstable-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="2e486-227">[CONTAINSTABLE &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/containstable-transact-sql) </span></span>  
 <span data-ttu-id="2e486-228">[FREETEXT &#40;Transact-SQL&#41;](/sql/t-sql/queries/freetext-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="2e486-228">[FREETEXT &#40;Transact-SQL&#41;](/sql/t-sql/queries/freetext-transact-sql) </span></span>  
 <span data-ttu-id="2e486-229">[FREETEXTTABLE &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/freetexttable-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="2e486-229">[FREETEXTTABLE &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/freetexttable-transact-sql) </span></span>  
 [<span data-ttu-id="2e486-230">全文檢索搜尋</span><span class="sxs-lookup"><span data-stu-id="2e486-230">Full-Text Search</span></span>](full-text-search.md)  
  
  
