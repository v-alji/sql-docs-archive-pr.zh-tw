---
title: 使用全文檢索索引精靈 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
f1_keywords:
- sql12.swb.fulltextindexingwizard.selecttablecolumns.f1
- sql12.swb.fulltextindexingwizard.welcome.f1
- sql12.swb.fulltextindexingwizard.selectacatalog.f1
- sql12.swb.fulltextindexingwizard.progress.f1
- sql12.swb.fulltextindexingwizard.selectorcreatepopschedules.f1
- sql12.swb.fulltextindexingwizard.selectatableorview.f1
- sql12.swb.fulltextindexingwizard.selectchangetracking.f1
- sql12.swb.fulltextindexingwizard.selectanindex.f1
- sql12.swb.fulltextindexingwizard.summary.f1
helpviewer_keywords:
- Full-Text Indexing Wizard
- full-text search [SQL Server], Full-Text Indexing Wizard
ms.assetid: 3e9d9605-6525-4781-9168-fdaa06db3459
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 5ef8a23c4d85cbe47bf6bdb47eb3f45723f1559d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87697819"
---
# <a name="use-the-full-text-indexing-wizard"></a><span data-ttu-id="db708-102">使用全文檢索索引精靈</span><span class="sxs-lookup"><span data-stu-id="db708-102">Use the Full-Text Indexing Wizard</span></span>
  <span data-ttu-id="db708-103">全文檢索索引精靈會提供一系列的逐步說明，以協助您建立全文檢索索引。</span><span class="sxs-lookup"><span data-stu-id="db708-103">The Full-Text Indexing Wizard walks you through a series of steps designed to help you create a full-text index.</span></span>  
  
#### <a name="to-use-the-full-text-indexing-wizard"></a><span data-ttu-id="db708-104">使用全文檢索索引精靈</span><span class="sxs-lookup"><span data-stu-id="db708-104">To use the Full-Text Indexing wizard</span></span>  
  
1.  <span data-ttu-id="db708-105">在物件總管中，以滑鼠右鍵按一下您要建立全文檢索索引的資料表、指向 [全文檢索索引]  ，然後按一下 [Define Full-Text Index (定義全文檢索索引)]  。</span><span class="sxs-lookup"><span data-stu-id="db708-105">In Object Explorer, right-click the table on which you want to create a full-text index, point to **Full-Text index**, and then click **Define Full-Text Index**.</span></span>  
  
     <span data-ttu-id="db708-106">**唯一索引**</span><span class="sxs-lookup"><span data-stu-id="db708-106">**Unique Index**</span></span>  
     <span data-ttu-id="db708-107">從下拉式清單中選取索引。</span><span class="sxs-lookup"><span data-stu-id="db708-107">Select an index from the drop down list.</span></span> <span data-ttu-id="db708-108">索引必須是單一索引鍵資料行、唯一的且不可以是 Null 的索引。</span><span class="sxs-lookup"><span data-stu-id="db708-108">The index must be a single-key-column, unique, non-nullable index.</span></span> <span data-ttu-id="db708-109">請選取最小的唯一索引鍵索引來當做全文檢索唯一索引鍵。</span><span class="sxs-lookup"><span data-stu-id="db708-109">Select the smallest unique key index for the full-text unique key.</span></span> <span data-ttu-id="db708-110">為求最佳效能，建議使用叢集索引。</span><span class="sxs-lookup"><span data-stu-id="db708-110">For best performance, a clustered index is recommended.</span></span>  
  
     <span data-ttu-id="db708-111">**可用的資料行**</span><span class="sxs-lookup"><span data-stu-id="db708-111">**Available Columns**</span></span>  
     <span data-ttu-id="db708-112">若要在索引中包含資料行，請選取資料行名稱旁邊的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="db708-112">To include a column in the index, select the check box next to the column name.</span></span> <span data-ttu-id="db708-113">不適合全文檢索索引的資料行會以灰色顯示，並會停用其核取方塊。</span><span class="sxs-lookup"><span data-stu-id="db708-113">Columns that are not eligible for full-text indexing appear in grey with their check boxes disabled.</span></span>  
  
     <span data-ttu-id="db708-114">**斷詞工具的語言**</span><span class="sxs-lookup"><span data-stu-id="db708-114">**Language for Word Breaker**</span></span>  
     <span data-ttu-id="db708-115">從下拉式清單中選取語言。</span><span class="sxs-lookup"><span data-stu-id="db708-115">Select a language from the drop-down list.</span></span> <span data-ttu-id="db708-116">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 將使用此選擇來識別索引的正確斷詞工具。</span><span class="sxs-lookup"><span data-stu-id="db708-116">This choice will be used by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to identify the correct word breakers for the index.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="db708-117">使用斷詞工具來識別全文檢索索引資料中的字詞界限。</span><span class="sxs-lookup"><span data-stu-id="db708-117">uses word breakers to identify word boundaries in the full-text indexed data.</span></span>  
  
     <span data-ttu-id="db708-118">**類型資料行**</span><span class="sxs-lookup"><span data-stu-id="db708-118">**Type Column**</span></span>  
     <span data-ttu-id="db708-119">選取資料行的名稱，其中包含要建立全文檢索索引之資料行的文件類型。</span><span class="sxs-lookup"><span data-stu-id="db708-119">Select the name of the column that holds the document type of column being full-text indexed.</span></span>  
  
     <span data-ttu-id="db708-120">只有在 [**可用**的資料行] 資料行中名為的資料行類型為或時，才會啟用**類型資料行** `varbinary(max)` `image` 。</span><span class="sxs-lookup"><span data-stu-id="db708-120">The  **Type Column** is only enabled when the column named in the **Available Columns** column is of type `varbinary(max)` or `image`.</span></span>  
  
     <span data-ttu-id="db708-121">**統計語意**</span><span class="sxs-lookup"><span data-stu-id="db708-121">**Statistical Semantics**</span></span>  
     <span data-ttu-id="db708-122">選取是否要針對選取的資料行啟用語意索引。</span><span class="sxs-lookup"><span data-stu-id="db708-122">Select whether to enable semantic indexing for the selected column.</span></span> <span data-ttu-id="db708-123">如需詳細資訊，請參閱[語意搜尋 &#40;SQL Server&#41;](semantic-search-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="db708-123">For more information, see [Semantic Search &#40;SQL Server&#41;](semantic-search-sql-server.md).</span></span>  
  
     <span data-ttu-id="db708-124">如果您在選取 **[統計語意]** 之前選取 **[語言]**，而且選取的語言沒有相關聯的語意語言模型，則會停用 **[統計語意]** 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="db708-124">If you select a **Language** prior to selecting **Statistical Semantics**, and the selected language does not have an associated Semantic Language Model, then the **Statistical Semantics** checkbox is disabled.</span></span> <span data-ttu-id="db708-125">如果您在選取 [語言]\*\*\*\* 之前選取 [統計語意]\*\*\*\*，則下拉式方塊中提供的語言將受限為有語意語言模型支援的語言。</span><span class="sxs-lookup"><span data-stu-id="db708-125">If you select **Statistical Semantics** prior to selecting a **Language**, the languages available in the drop-down combo box will be restricted to those for which there is Semantic Language Model support.</span></span>  
  
2.  <span data-ttu-id="db708-126">選取變更追蹤選項。</span><span class="sxs-lookup"><span data-stu-id="db708-126">Select the change tracking options.</span></span>  
  
     <span data-ttu-id="db708-127">**自動**</span><span class="sxs-lookup"><span data-stu-id="db708-127">**Automatically**</span></span>  
     <span data-ttu-id="db708-128">選取此選項按鈕，以使基礎資料發生變更時自動更新全文檢索索引。</span><span class="sxs-lookup"><span data-stu-id="db708-128">Select this radio button to have the full-text index updated automatically as changes occur to the underlying data.</span></span>  
  
     <span data-ttu-id="db708-129">**人工**</span><span class="sxs-lookup"><span data-stu-id="db708-129">**Manually**</span></span>  
     <span data-ttu-id="db708-130">選取此選項按鈕，以使基礎資料發生變更時不會自動更新全文檢索索引。</span><span class="sxs-lookup"><span data-stu-id="db708-130">Select this radio button if you do not want the full-text index to be updated automatically as changes occur to the underlying data.</span></span> <span data-ttu-id="db708-131">基礎資料的變更會被保留。</span><span class="sxs-lookup"><span data-stu-id="db708-131">Changes to the underlying data are maintained.</span></span> <span data-ttu-id="db708-132">不過，若要將變更套用至全文檢索索引，您必須手動啟動或手動排程此處理序。</span><span class="sxs-lookup"><span data-stu-id="db708-132">However, to apply the changes to the full-text index you must start or schedule this process manually.</span></span>  
  
     <span data-ttu-id="db708-133">**不要追蹤變更**</span><span class="sxs-lookup"><span data-stu-id="db708-133">**Do not track changes**</span></span>  
     <span data-ttu-id="db708-134">選取此選項按鈕，以使基礎資料變更時不會更新全文檢索索引。</span><span class="sxs-lookup"><span data-stu-id="db708-134">Select this radio button if you do not want the full-text index to be updated with changes to the underlying data.</span></span>  
  
     <span data-ttu-id="db708-135">**建立索引後啟動完整母體擴展**</span><span class="sxs-lookup"><span data-stu-id="db708-135">**Start full population when index is created**</span></span>  
     <span data-ttu-id="db708-136">選取此選項按鈕，以在此精靈順利完成時開始完整母體擴展。</span><span class="sxs-lookup"><span data-stu-id="db708-136">Select this radio button to kick off a full population at the successful completion of this wizard.</span></span> <span data-ttu-id="db708-137">這會由在目錄中建立全文檢索索引結構，然後使用全文檢索索引資料進行擴展來組成。</span><span class="sxs-lookup"><span data-stu-id="db708-137">This will consist of creating the full-text index structure in the catalog and populating it with full-text indexed data.</span></span>  
  
3.  <span data-ttu-id="db708-138">選取目錄、索引檔案群組和停用字詞表。</span><span class="sxs-lookup"><span data-stu-id="db708-138">Select the catalog, index filegroup and stoplist.</span></span>  
  
     <span data-ttu-id="db708-139">**選取全文檢索目錄**</span><span class="sxs-lookup"><span data-stu-id="db708-139">**Select full-text catalog**</span></span>  
     <span data-ttu-id="db708-140">從清單中選取全文檢索目錄。</span><span class="sxs-lookup"><span data-stu-id="db708-140">Select a full-text catalog from the list.</span></span> <span data-ttu-id="db708-141">資料庫的預設目錄是清單中預設選取的項目。</span><span class="sxs-lookup"><span data-stu-id="db708-141">The default catalog for the database will be the selected item by default in the list.</span></span> <span data-ttu-id="db708-142">如果沒有任何目錄可以使用，系統就會停用此清單，而且會核取及停用 **[建立新的目錄]** 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="db708-142">If no catalogs are available, the list will be disabled, and the **Create a new catalog** checkbox will be checked and disabled.</span></span>  
  
    |||  
    |-|-|  
    |<span data-ttu-id="db708-143">**[建立新的目錄]**</span><span class="sxs-lookup"><span data-stu-id="db708-143">**Create a new catalog**</span></span>|<span data-ttu-id="db708-144">選取即可建立新的全文檢索目錄。</span><span class="sxs-lookup"><span data-stu-id="db708-144">Select to create a new full-text catalog.</span></span>|  
  
     <span data-ttu-id="db708-145">**名稱**</span><span class="sxs-lookup"><span data-stu-id="db708-145">**Name**</span></span>  
     <span data-ttu-id="db708-146">輸入新的全文檢索目錄的名稱。</span><span class="sxs-lookup"><span data-stu-id="db708-146">Enter a name for the new full-text catalog.</span></span>  
  
     <span data-ttu-id="db708-147">**設定為預設目錄**</span><span class="sxs-lookup"><span data-stu-id="db708-147">**Set as default catalog**</span></span>  
     <span data-ttu-id="db708-148">選取即可讓此目錄成為這個資料庫的預設目錄。</span><span class="sxs-lookup"><span data-stu-id="db708-148">Select to make the catalog the default for this database.</span></span>  
  
     <span data-ttu-id="db708-149">**區分腔調字**</span><span class="sxs-lookup"><span data-stu-id="db708-149">**Accent sensitivity**</span></span>  
     <span data-ttu-id="db708-150">指定新目錄是要區分腔調字或不區分腔調字。</span><span class="sxs-lookup"><span data-stu-id="db708-150">Specify whether the new catalog will be accent-sensitive or accent-insensitive.</span></span> <span data-ttu-id="db708-151">如果資料庫有區分腔調字，預設就會選取 [區分]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="db708-151">If the database is accent-sensitive, **Sensitive** will be selected by default.</span></span>  
  
     <span data-ttu-id="db708-152">**選取索引檔案群組**</span><span class="sxs-lookup"><span data-stu-id="db708-152">**Select index filegroup**</span></span>  
     <span data-ttu-id="db708-153">指定要在上面建立全文檢索索引的檔案群組。</span><span class="sxs-lookup"><span data-stu-id="db708-153">Specify the filegroup on which to create the full-text index.</span></span>  
  
     <span data-ttu-id="db708-154">選取下列其中一個值：</span><span class="sxs-lookup"><span data-stu-id="db708-154">Select one of the following values:</span></span>  
  
    |<span data-ttu-id="db708-155">值</span><span class="sxs-lookup"><span data-stu-id="db708-155">Value</span></span>|<span data-ttu-id="db708-156">描述</span><span class="sxs-lookup"><span data-stu-id="db708-156">Description</span></span>|  
    |-----------|-----------------|  
    |**\<default>**|<span data-ttu-id="db708-157">如果資料表或檢視未分割，請選取此值，以便與基礎資料表或檢視使用的相同檔案群組。</span><span class="sxs-lookup"><span data-stu-id="db708-157">If the table or view is not partitioned, select to use the same filegroup as the underlying table or view.</span></span> <span data-ttu-id="db708-158">如果資料表或檢視表已分割，則會使用主要檔案群組。</span><span class="sxs-lookup"><span data-stu-id="db708-158">If the table or view is partitioned, the primary filegroup is used.</span></span>|  
    |<span data-ttu-id="db708-159">**PRIMARY**</span><span class="sxs-lookup"><span data-stu-id="db708-159">**PRIMARY**</span></span>|<span data-ttu-id="db708-160">選取即可針對新的全文檢索索引使用主要檔案群組。</span><span class="sxs-lookup"><span data-stu-id="db708-160">Select to use the primary filegroup for the new full-text index.</span></span>|  
    |<span data-ttu-id="db708-161">*使用者指定的預設檔案群組*</span><span class="sxs-lookup"><span data-stu-id="db708-161">*user-specified default filegroup*</span></span>|<span data-ttu-id="db708-162">如果使用者定義的預設停用字詞表已存在，請從清單中選取其名稱，以便針對新的全文檢索索引使用該檔案群組。</span><span class="sxs-lookup"><span data-stu-id="db708-162">If a user-defined default stoplist exists, select its name from the list to use that filegroup for the new full-text index.</span></span>|  
  
     <span data-ttu-id="db708-163">**選取全文檢索停用字詞表**</span><span class="sxs-lookup"><span data-stu-id="db708-163">**Select full-text stoplist**</span></span>  
     <span data-ttu-id="db708-164">指定要針對全文檢索索引使用的停用字詞表，或停用停用字詞表。</span><span class="sxs-lookup"><span data-stu-id="db708-164">Specify a stoplist to use for the full-text index, or disable stoplist use.</span></span>  
  
     <span data-ttu-id="db708-165">在 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 及更新的版本中，停用字詞在資料庫中是使用稱為停用字詞表的物件來管理。</span><span class="sxs-lookup"><span data-stu-id="db708-165">In [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] and later versions, stopwords are managed in databases using objects called stoplists.</span></span> <span data-ttu-id="db708-166">停用*字*詞表是停用字詞的清單，與全文檢索索引相關聯時，會套用至該索引上的全文檢索查詢。</span><span class="sxs-lookup"><span data-stu-id="db708-166">A *stoplist* is a list of stopwords that, when associated with a full-text index, is applied to full-text queries on that index.</span></span> <span data-ttu-id="db708-167">如需詳細資訊，請參閱 [設定及管理全文檢索搜尋的停用字詞與停用字詞表](configure-and-manage-stopwords-and-stoplists-for-full-text-search.md)。</span><span class="sxs-lookup"><span data-stu-id="db708-167">For more information, see [Configure and Manage Stopwords and Stoplists for Full-Text Search](configure-and-manage-stopwords-and-stoplists-for-full-text-search.md).</span></span>  
  
     <span data-ttu-id="db708-168">選取下列其中一個值：</span><span class="sxs-lookup"><span data-stu-id="db708-168">Select one of the following values:</span></span>  
  
    |<span data-ttu-id="db708-169">值</span><span class="sxs-lookup"><span data-stu-id="db708-169">Value</span></span>|<span data-ttu-id="db708-170">描述</span><span class="sxs-lookup"><span data-stu-id="db708-170">Description</span></span>|  
    |-----------|-----------------|  
    |**\<system>**|<span data-ttu-id="db708-171">選取即可針對新的全文檢索索引使用系統停用字詞表。</span><span class="sxs-lookup"><span data-stu-id="db708-171">Select to use the system stoplist on the new full-text index.</span></span> <span data-ttu-id="db708-172">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="db708-172">This is the default</span></span>|  
    |**\<off>**|<span data-ttu-id="db708-173">選取即可針對新的全文檢索索引停用停用字詞表。</span><span class="sxs-lookup"><span data-stu-id="db708-173">Select to disable stoplists for the new full-text index.</span></span>|  
    |<span data-ttu-id="db708-174">*user-defined-stoplist-name*</span><span class="sxs-lookup"><span data-stu-id="db708-174">*user-defined-stoplist-name*</span></span>|<span data-ttu-id="db708-175">此清單會顯示已經在資料庫上建立之每個使用者定義停用字詞表的名稱 (如果有的話)。</span><span class="sxs-lookup"><span data-stu-id="db708-175">The list displays the name of each user-defined stoplist, if any, that has been created on the database.</span></span> <span data-ttu-id="db708-176">選取要針對新的全文檢索索引使用的任何使用者定義停用字詞表。</span><span class="sxs-lookup"><span data-stu-id="db708-176">Select any user-defined stoplist to use for the new full-text index.</span></span>|  
  
4.  <span data-ttu-id="db708-177">選擇性地定義母體擴展排程。</span><span class="sxs-lookup"><span data-stu-id="db708-177">Optionally, define the population schedule.</span></span> <span data-ttu-id="db708-178">除非索引作業已排程於未來執行，否則會立即開始索引作業。</span><span class="sxs-lookup"><span data-stu-id="db708-178">Indexing operations will begin immediately unless they have been scheduled for future execution.</span></span> <span data-ttu-id="db708-179">排程本身會立即建立，不過要等排程時間到了才會執行。</span><span class="sxs-lookup"><span data-stu-id="db708-179">Schedules will be created immediately, although they will not run until their scheduled time.</span></span>  
  
     <span data-ttu-id="db708-180">**新增資料表排程**</span><span class="sxs-lookup"><span data-stu-id="db708-180">**New Table Schedule**</span></span>  
     <span data-ttu-id="db708-181">定義資料表的母體擴展排程。</span><span class="sxs-lookup"><span data-stu-id="db708-181">Define a population schedule for a table.</span></span>  
  
     <span data-ttu-id="db708-182">**新增目錄排程**</span><span class="sxs-lookup"><span data-stu-id="db708-182">**New Catalog Schedule**</span></span>  
     <span data-ttu-id="db708-183">定義全文檢索目錄的母體擴展排程。</span><span class="sxs-lookup"><span data-stu-id="db708-183">Define a population schedule for a full-text catalog.</span></span>  
  
     <span data-ttu-id="db708-184">**編輯**</span><span class="sxs-lookup"><span data-stu-id="db708-184">**Edit**</span></span>  
     <span data-ttu-id="db708-185">編輯排程。</span><span class="sxs-lookup"><span data-stu-id="db708-185">Edit a schedule.</span></span>  
  
     <span data-ttu-id="db708-186">**刪除**</span><span class="sxs-lookup"><span data-stu-id="db708-186">**Delete**</span></span>  
     <span data-ttu-id="db708-187">刪除排程。</span><span class="sxs-lookup"><span data-stu-id="db708-187">Delete a schedule.</span></span>  
  
5.  <span data-ttu-id="db708-188">檢視或控制全文檢索索引精靈的進度。</span><span class="sxs-lookup"><span data-stu-id="db708-188">View or control the progress of the Full-Text Indexing Wizard.</span></span>  
  
     <span data-ttu-id="db708-189">**停止**</span><span class="sxs-lookup"><span data-stu-id="db708-189">**Stop**</span></span>  
     <span data-ttu-id="db708-190">中斷目前的作業，並防止精靈在此工作階段期間執行後續的全文檢索作業。</span><span class="sxs-lookup"><span data-stu-id="db708-190">Interrupts the current operation and prevents subsequent full-text operations from being performed by the wizard during this session.</span></span>  
  
     <span data-ttu-id="db708-191">**Report**</span><span class="sxs-lookup"><span data-stu-id="db708-191">**Report**</span></span>  
     <span data-ttu-id="db708-192">當所有作業都執行完成後，按一下此按鈕以存取所執行作業的報表。</span><span class="sxs-lookup"><span data-stu-id="db708-192">When all of the operations have finished executing, click this button to access a report on the operations performed.</span></span> <span data-ttu-id="db708-193">您可以檢視報表、將其列印至檔案、將其複製到剪貼簿或以電子郵件傳送報表。</span><span class="sxs-lookup"><span data-stu-id="db708-193">You can view the report, print it to a file, copy it to the clipboard, or e-mail the report.</span></span>  
  
  
