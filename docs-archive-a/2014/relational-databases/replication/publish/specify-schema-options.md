---
title: 指定結構描述選項 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- schemas [SQL Server replication], options
- articles [SQL Server replication], transactional replication options
- articles [SQL Server replication], merge replication options
- articles [SQL Server replication], schema options
ms.assetid: 1f85a479-bd6e-4023-abf7-7435a7e5b567
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 52064cc189dc62152814436d2d11326a74c89ff6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704041"
---
# <a name="specify-schema-options"></a><span data-ttu-id="0ef4c-102">指定結構描述選項</span><span class="sxs-lookup"><span data-stu-id="0ef4c-102">Specify Schema Options</span></span>
  <span data-ttu-id="0ef4c-103">本主題描述如何使用 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] ，在 [!INCLUDE[tsql](../../../includes/tsql-md.md)]中指定結構描述選項。</span><span class="sxs-lookup"><span data-stu-id="0ef4c-103">This topic describes how to specify schema options in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span> <span data-ttu-id="0ef4c-104">當您發行資料表或檢視表時，您可以控制針對發行之物件複寫的物件建立選項。</span><span class="sxs-lookup"><span data-stu-id="0ef4c-104">When you are publishing a table or view, you can control the object creation options that are replicated for the published object.</span></span> <span data-ttu-id="0ef4c-105">您可以在建立發行項時設定這些選項，而且也可以在之後變更這些選項。</span><span class="sxs-lookup"><span data-stu-id="0ef4c-105">You can set these option when the article is created, and you can also change them at a later time.</span></span> <span data-ttu-id="0ef4c-106">如果您不明確針對發行項指定這些選項，將會定義一組預設選項。</span><span class="sxs-lookup"><span data-stu-id="0ef4c-106">If you do not explicitly specify these options for an article, a default set of options will be defined.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0ef4c-107">使用複寫預存程序時的預設結構描述選項，可能會與使用 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]加入發行項時的預設選項不同。</span><span class="sxs-lookup"><span data-stu-id="0ef4c-107">The default schema options when using replication stored procedures may differ from the default options when articles are added using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="0ef4c-108">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="0ef4c-108">**In This Topic**</span></span>  
  
-   <span data-ttu-id="0ef4c-109">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="0ef4c-109">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="0ef4c-110">限制事項</span><span class="sxs-lookup"><span data-stu-id="0ef4c-110">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="0ef4c-111">建議</span><span class="sxs-lookup"><span data-stu-id="0ef4c-111">Recommendations</span></span>](#Recommendations)  
  
-   <span data-ttu-id="0ef4c-112">**若要指定結構描述選項，請使用：**</span><span class="sxs-lookup"><span data-stu-id="0ef4c-112">**To specify schema options, using:**</span></span>  
  
     [<span data-ttu-id="0ef4c-113">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="0ef4c-113">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="0ef4c-114">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="0ef4c-114">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="0ef4c-115">開始之前</span><span class="sxs-lookup"><span data-stu-id="0ef4c-115">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="0ef4c-116">限制事項</span><span class="sxs-lookup"><span data-stu-id="0ef4c-116">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="0ef4c-117">如果在建立發行集之後變更結構描述選項，則必須產生新的快照。</span><span class="sxs-lookup"><span data-stu-id="0ef4c-117">If you change schema options after a publication is created, you must generate a new snapshot.</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="0ef4c-118">建議</span><span class="sxs-lookup"><span data-stu-id="0ef4c-118">Recommendations</span></span>  
  
-   <span data-ttu-id="0ef4c-119">如需架構選項的完整清單，請參閱[sp_addarticle &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql)和[sp_addmergearticle &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql)的\*\* \@ schema_option\*\*參數。</span><span class="sxs-lookup"><span data-stu-id="0ef4c-119">For the complete list of schema options, see the **\@schema_option** parameter of [sp_addarticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql) and [sp_addmergearticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="0ef4c-120">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="0ef4c-120">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="0ef4c-121">在 [發行項屬性 - \<Article>] 對話方塊的 [屬性] 索引標籤上指定結構描述選項，例如是否將條件約束與觸發程序複製至訂閱者。</span><span class="sxs-lookup"><span data-stu-id="0ef4c-121">Specify schema options, such as whether to copy constraints and triggers to Subscribers, on the **Properties** tab of the **Article Properties - \<Article>** dialog box.</span></span> <span data-ttu-id="0ef4c-122">[新增發行集精靈] 與 [發行集屬性 - \<Publication>] 對話方塊中都有提供此索引標籤。</span><span class="sxs-lookup"><span data-stu-id="0ef4c-122">This tab is available in the New Publication Wizard and the **Publication Properties - \<Publication>** dialog box.</span></span> <span data-ttu-id="0ef4c-123">如需使用精靈及存取對話方塊的詳細資訊，請參閱[建立發行集](create-a-publication.md)和[檢視及修改發行集屬性](view-and-modify-publication-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="0ef4c-123">For more information about using the wizard and accessing the dialog box, see [Create a Publication](create-a-publication.md) and [View and Modify Publication Properties](view-and-modify-publication-properties.md).</span></span>  
  
#### <a name="to-specify-schema-options"></a><span data-ttu-id="0ef4c-124">若要指定結構描述選項</span><span class="sxs-lookup"><span data-stu-id="0ef4c-124">To specify schema options</span></span>  
  
1.  <span data-ttu-id="0ef4c-125">在 [新增發行集精靈] 的 [發行項] 頁面上，或在 [發行集屬性 - \<Publication>] 對話方塊中，選取一個發行項，然後按一下 [發行項屬性]。</span><span class="sxs-lookup"><span data-stu-id="0ef4c-125">On the **Articles** Page of the New Publication Wizard or **Publication Properties - \<Publication>** dialog box, select an article, and then click **Article Properties**.</span></span>  
  
2.  <span data-ttu-id="0ef4c-126">選取哪些結構描述選項變更應套用至：</span><span class="sxs-lookup"><span data-stu-id="0ef4c-126">Select which articles schema option changes should apply to:</span></span>  
  
    -   <span data-ttu-id="0ef4c-127">按一下 [設定醒目提示 \<ObjectType> 發行項的屬性]，以啟動 [發行項屬性 - \<ObjectName>] 對話方塊；在這個對話方塊中所做屬性變更只會套用至 [發行項] 頁面上物件窗格中醒目提示的物件。</span><span class="sxs-lookup"><span data-stu-id="0ef4c-127">Click **Set Properties of Highlighted \<ObjectType> Article** to launch the **Article Properties - \<ObjectName>** dialog box; property changes made in this dialog box are applied only to the object that is highlighted in the object pane on the **Articles** page.</span></span>  
  
    -   <span data-ttu-id="0ef4c-128">按一下 [設定所有 \<ObjectType> 發行項的屬性] 以啟動 [所有 \<ObjectType> 發行項的屬性] 對話方塊；在這個對話方塊中所做屬性變更會套用至 [發行項] 頁面上物件窗格中屬於該類型的所有物件，包括尚未選取發行的物件。</span><span class="sxs-lookup"><span data-stu-id="0ef4c-128">Click **Set Properties of All \<ObjectType> Articles** to launch the **Properties for All \<ObjectType> Articles** dialog box; property changes made in this dialog box are applied to all objects of that type in the object pane on the **Articles** page, including ones not yet selected for publication.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="0ef4c-129">在 [所有 \<ObjectType> 發行項的屬性] 對話方塊中所做屬性變更，會覆寫先前在 [發行項屬性 - \<ObjectName>] 對話方塊中所做的任何變更。</span><span class="sxs-lookup"><span data-stu-id="0ef4c-129">Property changes made in the **Properties for All \<ObjectType> Articles** dialog box override any made previously in the **Article Properties - \<ObjectName>** dialog box.</span></span> <span data-ttu-id="0ef4c-130">例如，若要設定所有屬於某物件類型之發行項的一些預設值，但同時要設定個別物件的某些屬性，則請先設定所有發行項的預設值，</span><span class="sxs-lookup"><span data-stu-id="0ef4c-130">If, for example, you want to set a number of defaults for all articles of an object type, but also want to set some properties for individual objects, set the defaults for all articles first.</span></span> <span data-ttu-id="0ef4c-131">然後再設定個別物件的屬性。</span><span class="sxs-lookup"><span data-stu-id="0ef4c-131">Then set the properties for the individual objects.</span></span>  
  
3.  <span data-ttu-id="0ef4c-132">在 [發行項屬性 - \<Article>] 對話方塊其 [屬性] 索引標籤的 [複製物件和設定到訂閱者] 與 [目的地物件] 區段中，指定選項的值。</span><span class="sxs-lookup"><span data-stu-id="0ef4c-132">In the **Copy Objects and Settings to Subscriber** and **Destination Object** sections of the **Properties** tab of the **Article Properties - \<Article>** dialog box, specify values for the options.</span></span>  
  
4.  <span data-ttu-id="0ef4c-133">必要時修改任何屬性，然後按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="0ef4c-133">Modify any properties if necessary, and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="0ef4c-134">如果位於 [發行集屬性 - \<Publication>] 對話方塊中，請按一下 [確定] 以儲存並關閉對話方塊。</span><span class="sxs-lookup"><span data-stu-id="0ef4c-134">If you are in the **Publication Properties - \<Publication>** dialog box, click **OK** to save and close the dialog box.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="0ef4c-135">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="0ef4c-135">Using Transact-SQL</span></span>  
 <span data-ttu-id="0ef4c-136">結構描述選項會指定為十六進位值，這個值是一個或多個選項的 [| (Bitwise OR)](/sql/t-sql/language-elements/bitwise-or-transact-sql) 結果。</span><span class="sxs-lookup"><span data-stu-id="0ef4c-136">Schema options are specified as a hexadecimal value that is the [| (Bitwise OR)](/sql/t-sql/language-elements/bitwise-or-transact-sql) result of one or more options.</span></span> <span data-ttu-id="0ef4c-137">如需詳細資訊，請參閱＜ [sp_addarticle](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql) ＞和＜ [sp_addmergearticle](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql)＞。</span><span class="sxs-lookup"><span data-stu-id="0ef4c-137">For more information, see [sp_addarticle](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql) and [sp_addmergearticle](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0ef4c-138">在執行位元運算之前，您必須將結構描述選項值從 **binary** 轉換成 **int** 。</span><span class="sxs-lookup"><span data-stu-id="0ef4c-138">You must convert schema option values from **binary** to **int** before performing a bitwise operation.</span></span> <span data-ttu-id="0ef4c-139">如需詳細資訊，請參閱 [CAST 和 CONVERT &#40;Transact-SQL&#41;](/sql/t-sql/functions/cast-and-convert-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="0ef4c-139">For more information, see [CAST and CONVERT &#40;Transact-SQL&#41;](/sql/t-sql/functions/cast-and-convert-transact-sql).</span></span>  
  
#### <a name="to-specify-schema-options-when-defining-an-article-for-a-snapshot-or-transactional-publication"></a><span data-ttu-id="0ef4c-140">在針對快照式或交易式發行集定義發行項時，指定結構描述選項</span><span class="sxs-lookup"><span data-stu-id="0ef4c-140">To specify schema options when defining an article for a snapshot or transactional publication</span></span>  
  
1.  <span data-ttu-id="0ef4c-141">在發行集資料庫的發行者上，執行 [sp_addarticle](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="0ef4c-141">At the Publisher on the publication database, execute [sp_addarticle](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql).</span></span> <span data-ttu-id="0ef4c-142">指定發行項所屬的發行集\*\* \@ 名稱、發行\*\*\*\*項的名稱、 \@ 用於\*\* \*\* \@ source_object**的資料庫物件、 \*\* \@ 類型**的資料庫物件類型，以及\*\* \@ schema_option\*\*的一或多個架構選項的[| (位或) ](/sql/t-sql/language-elements/bitwise-or-transact-sql)結果。</span><span class="sxs-lookup"><span data-stu-id="0ef4c-142">Specify the name of the publication to which the article belongs for **\@publication**, a name for the article for **\@article**, the database object being published for **\@source_object**, the type of database object for **\@type**, and the [| (Bitwise OR)](/sql/t-sql/language-elements/bitwise-or-transact-sql) result of one or more schema options for **\@schema_option**.</span></span> <span data-ttu-id="0ef4c-143">如需詳細資訊，請參閱 [定義發行項](define-an-article.md)。</span><span class="sxs-lookup"><span data-stu-id="0ef4c-143">For more information, see [Define an Article](define-an-article.md).</span></span>  
  
#### <a name="to-specify-schema-options-when-defining-an-article-for-a-merge-publication"></a><span data-ttu-id="0ef4c-144">在針對合併式發行集定義發行項時，指定結構描述選項</span><span class="sxs-lookup"><span data-stu-id="0ef4c-144">To specify schema options when defining an article for a merge publication</span></span>  
  
1.  <span data-ttu-id="0ef4c-145">在發行集資料庫的發行者上，執行 [sp_addmergearticle](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="0ef4c-145">At the Publisher on the publication database, execute [sp_addmergearticle](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql).</span></span> <span data-ttu-id="0ef4c-146">針對 [ \*\* \@ 發行**集] 指定發行項所屬的發行集名稱、針對 [發行項] 建立發行項的名稱、針對** \@ source_object**發佈的資料庫** \@ 物件，以及\*\* \*\* \@ schema_option\*\*的一個或多個架構選項的[| [ (位] 或 [) ](/sql/t-sql/language-elements/bitwise-or-transact-sql)結果]。</span><span class="sxs-lookup"><span data-stu-id="0ef4c-146">Specify the name of the publication to which the article belongs for **\@publication**, a name for the article for **\@article**, the database object being published for **\@source_object**, and the [| (Bitwise OR)](/sql/t-sql/language-elements/bitwise-or-transact-sql) result of one or more schema options for **\@schema_option**.</span></span> <span data-ttu-id="0ef4c-147">如需詳細資訊，請參閱 [定義發行項](define-an-article.md)。</span><span class="sxs-lookup"><span data-stu-id="0ef4c-147">For more information, see [Define an Article](define-an-article.md).</span></span>  
  
#### <a name="to-change-schema-options-for-an-existing-article-in-a-snapshot-or-transactional-publication"></a><span data-ttu-id="0ef4c-148">針對快照式或交易式發行集中的現有發行項變更結構描述選項</span><span class="sxs-lookup"><span data-stu-id="0ef4c-148">To change schema options for an existing article in a snapshot or transactional publication</span></span>  
  
1.  <span data-ttu-id="0ef4c-149">在發行集資料庫的發行者上，執行 [sp_helparticle](/sql/relational-databases/system-stored-procedures/sp-helparticle-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="0ef4c-149">At the Publisher on the publication database, execute [sp_helparticle](/sql/relational-databases/system-stored-procedures/sp-helparticle-transact-sql).</span></span> <span data-ttu-id="0ef4c-150">指定發行項所屬的發行集名稱，以及\*\* \@ 發行\*\* \*\* \@ 項的名稱。\*\*</span><span class="sxs-lookup"><span data-stu-id="0ef4c-150">Specify the name of the publication to which the article belongs for **\@publication** and the name of the article for **\@article**.</span></span> <span data-ttu-id="0ef4c-151">請記下結果集中 **schema_option** 資料行的值。</span><span class="sxs-lookup"><span data-stu-id="0ef4c-151">Note the value of the **schema_option** column in the result set.</span></span>  
  
2.  <span data-ttu-id="0ef4c-152">請使用步驟 1 中的值及所要的結構描述選項值來執行 [& (Bitwise AND)](/sql/t-sql/language-elements/bitwise-and-transact-sql) 運算，以判斷是否已設定選項。</span><span class="sxs-lookup"><span data-stu-id="0ef4c-152">Execute a [& (Bitwise AND)](/sql/t-sql/language-elements/bitwise-and-transact-sql) operation using the value from step 1 and the desired schema option value to determine if the option is set.</span></span>  
  
    -   <span data-ttu-id="0ef4c-153">如果結果是 **0**，表示未設定此選項。</span><span class="sxs-lookup"><span data-stu-id="0ef4c-153">If the result is **0**, the option is not set.</span></span>  
  
    -   <span data-ttu-id="0ef4c-154">如果結果是此選項值，表示已設定此選項。</span><span class="sxs-lookup"><span data-stu-id="0ef4c-154">If the result is the option value, the option is already set.</span></span>  
  
3.  <span data-ttu-id="0ef4c-155">如果未設定此選項，請使用步驟 1 中的值及所要的結構描述選項值來執行 [| (Bitwise OR)](/sql/t-sql/language-elements/bitwise-or-transact-sql) 運算。</span><span class="sxs-lookup"><span data-stu-id="0ef4c-155">If the option is not set, execute a [| (Bitwise OR)](/sql/t-sql/language-elements/bitwise-or-transact-sql) operation using the value from step 1 and the desired schema option value.</span></span>  
  
4.  <span data-ttu-id="0ef4c-156">在發行集資料庫的發行者上，執行 [sp_changearticle](/sql/relational-databases/system-stored-procedures/sp-changearticle-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="0ef4c-156">At the Publisher on the publication database, execute [sp_changearticle](/sql/relational-databases/system-stored-procedures/sp-changearticle-transact-sql).</span></span> <span data-ttu-id="0ef4c-157">指定發行項所屬的發行集名稱、 \*\* \@ 發行**項的** \@ 名稱、針對\*\* \*\* \@ 屬性\*\* **schema_option**的值，以及步驟3中的十六進位結果作為 [ \*\* \@ 值\*\*]。</span><span class="sxs-lookup"><span data-stu-id="0ef4c-157">Specify the name of the publication to which the article belongs for **\@publication**, the name of the article for **\@article**, a value of **schema_option** for **\@property**, and the hexadecimal result from step 3 for **\@value**.</span></span>  
  
5.  <span data-ttu-id="0ef4c-158">執行快照集代理程式來產生新的快照集。</span><span class="sxs-lookup"><span data-stu-id="0ef4c-158">Run the Snapshot Agent to generate a new snapshot.</span></span> <span data-ttu-id="0ef4c-159">如需詳細資訊，請參閱 [建立和套用初始快照集](../create-and-apply-the-initial-snapshot.md)。</span><span class="sxs-lookup"><span data-stu-id="0ef4c-159">For more information, see [Create and Apply the Initial Snapshot](../create-and-apply-the-initial-snapshot.md).</span></span>  
  
#### <a name="to-change-schema-options-for-an-existing-article-in-a-merge-publication"></a><span data-ttu-id="0ef4c-160">變更合併發行中現有發行項的結構描述選項</span><span class="sxs-lookup"><span data-stu-id="0ef4c-160">To change schema options for an existing article in a merge publication</span></span>  
  
1.  <span data-ttu-id="0ef4c-161">在發行集資料庫的發行者上，執行 [sp_helpmergearticle](/sql/relational-databases/system-stored-procedures/sp-helpmergearticle-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="0ef4c-161">At the Publisher on the publication database, execute [sp_helpmergearticle](/sql/relational-databases/system-stored-procedures/sp-helpmergearticle-transact-sql).</span></span> <span data-ttu-id="0ef4c-162">指定發行項所屬的發行集名稱，以及\*\* \@ 發行\*\* \*\* \@ 項的名稱。\*\*</span><span class="sxs-lookup"><span data-stu-id="0ef4c-162">Specify the name of the publication to which the article belongs for **\@publication** and the name of the article for **\@article**.</span></span> <span data-ttu-id="0ef4c-163">請記下結果集中 **schema_option** 資料行的值。</span><span class="sxs-lookup"><span data-stu-id="0ef4c-163">Note the value of the **schema_option** column in the result set.</span></span>  
  
2.  <span data-ttu-id="0ef4c-164">請使用步驟 1 中的值及所要的結構描述選項值來執行 [& (Bitwise AND)](/sql/t-sql/language-elements/bitwise-and-transact-sql) 運算，以判斷是否已設定選項。</span><span class="sxs-lookup"><span data-stu-id="0ef4c-164">Execute a [& (Bitwise AND)](/sql/t-sql/language-elements/bitwise-and-transact-sql) operation using the value from step 1 and the desired schema option value to determine if the option is set.</span></span>  
  
    -   <span data-ttu-id="0ef4c-165">如果結果是 **0**，表示未設定此選項。</span><span class="sxs-lookup"><span data-stu-id="0ef4c-165">If the result is **0**, the option is not set.</span></span>  
  
    -   <span data-ttu-id="0ef4c-166">如果結果是此選項值，表示已設定此選項。</span><span class="sxs-lookup"><span data-stu-id="0ef4c-166">If the result is the option value, the option is already set.</span></span>  
  
3.  <span data-ttu-id="0ef4c-167">如果未設定此選項，請使用步驟 1 中的值及所要的結構描述選項值來執行 [| (Bitwise OR)](/sql/t-sql/language-elements/bitwise-or-transact-sql) 運算。</span><span class="sxs-lookup"><span data-stu-id="0ef4c-167">If the option is not set, execute a [| (Bitwise OR)](/sql/t-sql/language-elements/bitwise-or-transact-sql) operation using the value from step 1 and the desired schema option value.</span></span>  
  
4.  <span data-ttu-id="0ef4c-168">在發行集資料庫的發行者上，執行 [sp_changemergearticle](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="0ef4c-168">At the Publisher on the publication database, execute [sp_changemergearticle](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql).</span></span> <span data-ttu-id="0ef4c-169">指定發行項所屬的發行集名稱、 \*\* \@ 發行**項的** \@ 名稱、針對\*\* \*\* \@ 屬性\*\* **schema_option**的值，以及步驟3中的十六進位結果作為 [ \*\* \@ 值\*\*]。</span><span class="sxs-lookup"><span data-stu-id="0ef4c-169">Specify the name of the publication to which the article belongs for **\@publication**, the name of the article for **\@article**, a value of **schema_option** for **\@property**, and the hexadecimal result from step 3 for **\@value**.</span></span>  
  
5.  <span data-ttu-id="0ef4c-170">執行快照集代理程式來產生新的快照集。</span><span class="sxs-lookup"><span data-stu-id="0ef4c-170">Run the Snapshot Agent to generate a new snapshot.</span></span> <span data-ttu-id="0ef4c-171">如需詳細資訊，請參閱 [建立和套用初始快照集](../create-and-apply-the-initial-snapshot.md)。</span><span class="sxs-lookup"><span data-stu-id="0ef4c-171">For more information, see [Create and Apply the Initial Snapshot](../create-and-apply-the-initial-snapshot.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ef4c-172">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0ef4c-172">See Also</span></span>  
 <span data-ttu-id="0ef4c-173">[發行資料和資料庫物件](publish-data-and-database-objects.md) </span><span class="sxs-lookup"><span data-stu-id="0ef4c-173">[Publish Data and Database Objects](publish-data-and-database-objects.md) </span></span>  
 [<span data-ttu-id="0ef4c-174">Article Options for Transactional Replication</span><span class="sxs-lookup"><span data-stu-id="0ef4c-174">Article Options for Transactional Replication</span></span>](../transactional/article-options-for-transactional-replication.md)  
  
  
