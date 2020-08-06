---
title: 詞彙查閱轉換 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.termlookuptrans.f1
helpviewer_keywords:
- extracting data [Integration Services]
- match extracted terms [Integration Services]
- text extraction [Integration Services]
- term extractions [Integration Services]
- lookups [Integration Services]
- counting extracted items
- Term Lookup transformation
ms.assetid: 3c0fa2f8-cb6a-4371-b184-7447be001de1
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a679f9e191b2b1ec54d982a715085fe5b6bddfc5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706598"
---
# <a name="term-lookup-transformation"></a><span data-ttu-id="848dd-102">詞彙查閱轉換</span><span class="sxs-lookup"><span data-stu-id="848dd-102">Term Lookup Transformation</span></span>
  <span data-ttu-id="848dd-103">「詞彙查閱」轉換會比對從轉換輸入資料行的文字中擷取的詞彙，以及參考資料表中的詞彙。</span><span class="sxs-lookup"><span data-stu-id="848dd-103">The Term Lookup transformation matches terms extracted from text in a transformation input column with terms in a reference table.</span></span> <span data-ttu-id="848dd-104">然後，它會計算查閱資料表中的詞彙在輸入資料集中出現的次數，並將計數與參考資料表的詞彙一起寫入轉換輸出中的資料行。</span><span class="sxs-lookup"><span data-stu-id="848dd-104">It then counts the number of times a term in the lookup table occurs in the input data set, and writes the count together with the term from the reference table to columns in the transformation output.</span></span> <span data-ttu-id="848dd-105">此轉換包括單字頻率統計資料，對基於輸入文字建立自訂單字清單很有用處。</span><span class="sxs-lookup"><span data-stu-id="848dd-105">This transformation is useful for creating a custom word list based on the input text, complete with word frequency statistics.</span></span>  
  
 <span data-ttu-id="848dd-106">在「詞彙查閱」轉換執行查閱之前，它會使用與「詞彙擷取」轉換相同的方法從輸入資料行的文字中擷取單字：</span><span class="sxs-lookup"><span data-stu-id="848dd-106">Before the Term Lookup transformation performs a lookup, it extracts words from the text in an input column using the same method as the Term Extraction transformation:</span></span>  
  
-   <span data-ttu-id="848dd-107">文字分解為句子。</span><span class="sxs-lookup"><span data-stu-id="848dd-107">Text is broken into sentences.</span></span>  
  
-   <span data-ttu-id="848dd-108">句子分解為單字。</span><span class="sxs-lookup"><span data-stu-id="848dd-108">Sentences are broken into words.</span></span>  
  
-   <span data-ttu-id="848dd-109">單字會正規化。</span><span class="sxs-lookup"><span data-stu-id="848dd-109">Words are normalized.</span></span>  
  
 <span data-ttu-id="848dd-110">若要進一步自訂要比對的詞彙，可以設定「詞彙查閱」轉換，以執行區分大小寫的比對。</span><span class="sxs-lookup"><span data-stu-id="848dd-110">To further customize which terms to match, the Term Lookup transformation can be configured to perform a case-sensitive match.</span></span>  
  
## <a name="matches"></a><span data-ttu-id="848dd-111">比對</span><span class="sxs-lookup"><span data-stu-id="848dd-111">Matches</span></span>  
 <span data-ttu-id="848dd-112">「詞彙查閱」會使用下列規則執行查閱並傳回值：</span><span class="sxs-lookup"><span data-stu-id="848dd-112">The Term Lookup performs a lookup and returns a value using the following rules:</span></span>  
  
-   <span data-ttu-id="848dd-113">如果設定轉換執行區分大小寫的比對，則會捨棄使區分大小寫比較失敗的比對。</span><span class="sxs-lookup"><span data-stu-id="848dd-113">If the transformation is configured to perform case-sensitive matches, matches that fail a case-sensitive comparison are discarded.</span></span> <span data-ttu-id="848dd-114">例如，會將 *student* 及 *STUDENT* 視為不同的單字。</span><span class="sxs-lookup"><span data-stu-id="848dd-114">For example, *student* and *STUDENT* are treated as separate words.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="848dd-115">未大寫的單字可與在句子開頭大寫的單字進行比對。</span><span class="sxs-lookup"><span data-stu-id="848dd-115">A non-capitalized word can be matched with a word that is capitalized at the beginning of a sentence.</span></span> <span data-ttu-id="848dd-116">例如，當 *Student* 為句子第一個單字時， *student* 與 *Student* 之間的比對則會成功。</span><span class="sxs-lookup"><span data-stu-id="848dd-116">For example, the match between *student* and *Student* succeeds when *Student* is the first word in a sentence.</span></span>  
  
-   <span data-ttu-id="848dd-117">如果名詞或名詞片語的複數形式存在於參考資料表中，則查閱只會比對名詞或名詞片語的複數形式。</span><span class="sxs-lookup"><span data-stu-id="848dd-117">If a plural form of the noun or noun phrase exists in the reference table, the lookup matches only the plural form of the noun or noun phrase.</span></span> <span data-ttu-id="848dd-118">例如， *students* 的所有執行個體都會在 *student*的執行個體之外另行計數。</span><span class="sxs-lookup"><span data-stu-id="848dd-118">For example, all instances of *students* would be counted separately from the instances of *student*.</span></span>  
  
-   <span data-ttu-id="848dd-119">如果在參考資料表中找到單字的單數形式，則單字或片語的單數及複數形式都會與單數形式比對。</span><span class="sxs-lookup"><span data-stu-id="848dd-119">If only the singular form of the word is found in the reference table, both the singular and the plural forms of the word or phrase are matched to the singular form.</span></span> <span data-ttu-id="848dd-120">例如，如果查閱資料表包含 *student*，且轉換找到單字 *student* 及 *students*，則會將這兩個單字作為查閱詞彙 *student*的相符部份進行計數。</span><span class="sxs-lookup"><span data-stu-id="848dd-120">For example, if the lookup table contains *student*, and the transformation finds the words *student* and *students*, both words would be counted as a match for the lookup term *student*.</span></span>  
  
-   <span data-ttu-id="848dd-121">如果輸入資料行中的文字是還原的名詞片語，則只有該名詞片語中的最後一個單字會受正規化影響。</span><span class="sxs-lookup"><span data-stu-id="848dd-121">If the text in the input column is a lemmatized noun phrase, only the last word in the noun phrase is affected by normalization.</span></span> <span data-ttu-id="848dd-122">例如， *doctors appointments* 的還原版本是 *doctors appointment*。</span><span class="sxs-lookup"><span data-stu-id="848dd-122">For example, the lemmatized version of *doctors appointments* is *doctors appointment*.</span></span>  
  
 <span data-ttu-id="848dd-123">當查閱項目在參考集中包含重疊的詞彙 (即，在一個以上參考記錄中找到子詞彙) 時，「詞彙查閱」轉換只會傳回一個查閱結果。</span><span class="sxs-lookup"><span data-stu-id="848dd-123">When a lookup item contains terms that overlap in the reference set-that is, a sub-term is found in more than one reference record-the Term Lookup transformation returns only one lookup result.</span></span> <span data-ttu-id="848dd-124">下列範例顯示查閱項目包含重疊子詞彙時的結果。</span><span class="sxs-lookup"><span data-stu-id="848dd-124">The following example shows the result when a lookup item contains an overlapping sub-term.</span></span> <span data-ttu-id="848dd-125">此處的重疊子詞彙為 *Windows*，其在兩個參考詞彙中均有找到。</span><span class="sxs-lookup"><span data-stu-id="848dd-125">The overlapping sub-term in this case is *Windows*, which is found within two reference terms.</span></span> <span data-ttu-id="848dd-126">但轉換不會傳回兩個結果，而只會傳回單一參考詞彙 *Windows*。</span><span class="sxs-lookup"><span data-stu-id="848dd-126">However, the transformation does not return two results, but returns only a single reference term, *Windows*.</span></span> <span data-ttu-id="848dd-127">第二個參考詞彙 *Windows 7 Professional*不會傳回。</span><span class="sxs-lookup"><span data-stu-id="848dd-127">The second reference term, *Windows 7 Professional*, is not returned.</span></span>  
  
|<span data-ttu-id="848dd-128">Item</span><span class="sxs-lookup"><span data-stu-id="848dd-128">Item</span></span>|<span data-ttu-id="848dd-129">值</span><span class="sxs-lookup"><span data-stu-id="848dd-129">Value</span></span>|  
|----------|-----------|  
|<span data-ttu-id="848dd-130">輸入詞彙</span><span class="sxs-lookup"><span data-stu-id="848dd-130">Input term</span></span>|<span data-ttu-id="848dd-131">Windows 7 Professional</span><span class="sxs-lookup"><span data-stu-id="848dd-131">Windows 7 Professional</span></span>|  
|<span data-ttu-id="848dd-132">參考詞彙</span><span class="sxs-lookup"><span data-stu-id="848dd-132">Reference terms</span></span>|<span data-ttu-id="848dd-133">Windows、Windows 7 Professional</span><span class="sxs-lookup"><span data-stu-id="848dd-133">Windows, Windows 7 Professional</span></span>|  
|<span data-ttu-id="848dd-134">輸出</span><span class="sxs-lookup"><span data-stu-id="848dd-134">Output</span></span>|<span data-ttu-id="848dd-135">Windows</span><span class="sxs-lookup"><span data-stu-id="848dd-135">Windows</span></span>|  
  
 <span data-ttu-id="848dd-136">「詞彙查閱」轉換可以比對包含特殊字元的名詞及名詞片語，且參考資料表中的資料可能包含這些字元。</span><span class="sxs-lookup"><span data-stu-id="848dd-136">The Term Lookup transformation can match nouns and noun phrases that contain special characters, and the data in the reference table may include these characters.</span></span> <span data-ttu-id="848dd-137">特殊字元如下：%、@、&、$、#、\*、:、;、.、 **,** 、!、?、\<, >、+、=、^、~、|、\\、/、(、)、[、]、{、}、" 和 '。</span><span class="sxs-lookup"><span data-stu-id="848dd-137">The special characters are as follows: %, @, &, $, #, \*, :, ;, ., **,** , !, ?, \<, >, +, =, ^, ~, |, \\, /, (, ), [, ], {, }, ", and '.</span></span>  
  
## <a name="data-types"></a><span data-ttu-id="848dd-138">資料類型</span><span class="sxs-lookup"><span data-stu-id="848dd-138">Data Types</span></span>  
 <span data-ttu-id="848dd-139">「詞彙查閱」轉換只可以使用具有 DT_WSTR 或 DT_NTEXT 資料類型的資料行。</span><span class="sxs-lookup"><span data-stu-id="848dd-139">The Term Lookup transformation can only use a column that has either the DT_WSTR or the DT_NTEXT data type.</span></span> <span data-ttu-id="848dd-140">如果資料行包含文字，但不具有這些資料類型的其中之一，則「資料轉換」可以將具有 DT_WSTR 或 DT_NTEXT 資料類型的資料行加入資料流程，並將資料行值複製至新資料行。</span><span class="sxs-lookup"><span data-stu-id="848dd-140">If a column contains text, but does not have one of these data types, the Data Conversion transformation can add a column with the DT_WSTR or DT_NTEXT data type to the data flow and copy the column values to the new column.</span></span> <span data-ttu-id="848dd-141">然後，「資料轉換」的輸出可以用作「詞彙查閱」轉換的輸入。</span><span class="sxs-lookup"><span data-stu-id="848dd-141">The output from the Data Conversion transformation can then be used as the input to the Term Lookup transformation.</span></span> <span data-ttu-id="848dd-142">如需詳細資訊，請參閱 [Data Conversion Transformation](data-conversion-transformation.md)。</span><span class="sxs-lookup"><span data-stu-id="848dd-142">For more information, see [Data Conversion Transformation](data-conversion-transformation.md).</span></span>  
  
## <a name="configuration-the-term-lookup-transformation"></a><span data-ttu-id="848dd-143">設定詞彙查閱轉換</span><span class="sxs-lookup"><span data-stu-id="848dd-143">Configuration the Term Lookup Transformation</span></span>  
 <span data-ttu-id="848dd-144">「詞彙查閱」轉換輸入資料行包含可指出資料行用法的 InputColumnType 屬性。</span><span class="sxs-lookup"><span data-stu-id="848dd-144">The Term Lookup transformation input columns includes the InputColumnType property, which indicates the use of the column.</span></span> <span data-ttu-id="848dd-145">InputColumnType 可包含下列值：</span><span class="sxs-lookup"><span data-stu-id="848dd-145">InputColumnType can contain the following values:</span></span>  
  
-   <span data-ttu-id="848dd-146">值 0 表示資料行只傳遞至輸出，且不在查閱中使用。</span><span class="sxs-lookup"><span data-stu-id="848dd-146">The value 0 indicates the column is passed through to the output only and is not used in the lookup.</span></span>  
  
-   <span data-ttu-id="848dd-147">值 1 表示資料行只在查閱中使用。</span><span class="sxs-lookup"><span data-stu-id="848dd-147">The value 1 indicates the column is used in the lookup only.</span></span>  
  
-   <span data-ttu-id="848dd-148">值 2 表示資料行傳遞至輸出，且亦在查閱中使用。</span><span class="sxs-lookup"><span data-stu-id="848dd-148">The value 2 indicates the column is passed through to the output, and is also used in the lookup.</span></span>  
  
 <span data-ttu-id="848dd-149">InputColumnType 屬性設為 0 或 2 的轉換輸出資料行包含資料行的 CustomLineageID 屬性，其包含上游資料流程元件指派給該資料行的歷程識別碼。</span><span class="sxs-lookup"><span data-stu-id="848dd-149">Transformation output columns whose InputColumnType property is set to 0 or 2 include the CustomLineageID property for a column, which contains the lineage identifier assigned to the column by an upstream data flow component.</span></span>  
  
 <span data-ttu-id="848dd-150">「詞彙查閱」轉換會將兩個資料行新增到轉換輸出，以預設的 `Term` 和 `Frequency` 來命名。</span><span class="sxs-lookup"><span data-stu-id="848dd-150">The Term Lookup transformation adds two columns to the transformation output, named by default `Term` and `Frequency`.</span></span> <span data-ttu-id="848dd-151">`Term` 包含了查閱資料表中的詞彙，而 `Frequency` 包含了參考資料表中的詞彙發生在輸入資料集內的次數。</span><span class="sxs-lookup"><span data-stu-id="848dd-151">`Term` contains a term from the lookup table and `Frequency` contains the number of times the term in the reference table occurs in the input data set.</span></span> <span data-ttu-id="848dd-152">這些資料行不包含 CustomLineageID 屬性。</span><span class="sxs-lookup"><span data-stu-id="848dd-152">These columns do not include the CustomLineageID property.</span></span>  
  
 <span data-ttu-id="848dd-153">查閱資料表必須是 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 或 Access 資料庫中的資料表。</span><span class="sxs-lookup"><span data-stu-id="848dd-153">The lookup table must be a table in a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] or an Access database.</span></span> <span data-ttu-id="848dd-154">如果將「詞彙擷取」轉換的輸出儲存為資料表，不僅可將此資料表用為參考資料表，也可以使用其他資料表。</span><span class="sxs-lookup"><span data-stu-id="848dd-154">If the output of the Term Extraction transformation is saved to a table, this table can be used as the reference table, but other tables can also be used.</span></span> <span data-ttu-id="848dd-155">在您可以使用「詞彙查閱」轉換之前，一般檔案、Excel 活頁簿或其他來源中的文字必須匯入至 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 資料庫或 Access 資料庫。</span><span class="sxs-lookup"><span data-stu-id="848dd-155">Text in flat files, Excel workbooks or other sources must be imported to a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] database or an Access database before you can use the Term Lookup transformation.</span></span>  
  
 <span data-ttu-id="848dd-156">「詞彙查閱」轉換會使用個別 OLE DB 連接，以連接到參考資料表。</span><span class="sxs-lookup"><span data-stu-id="848dd-156">The Term Lookup transformation uses a separate OLE DB connection to connect to the reference table.</span></span> <span data-ttu-id="848dd-157">如需相關資訊，請參閱 [OLE DB Connection Manager](../../connection-manager/ole-db-connection-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="848dd-157">For more information, see [OLE DB Connection Manager](../../connection-manager/ole-db-connection-manager.md).</span></span>  
  
 <span data-ttu-id="848dd-158">「詞彙查閱」轉換以完全預先快取模式運作。</span><span class="sxs-lookup"><span data-stu-id="848dd-158">The Term Lookup transformation works in a fully precached mode.</span></span> <span data-ttu-id="848dd-159">在執行階段，「詞彙查閱」轉換在處理任何轉換輸入資料列之前，會從參考資料表讀取詞彙，並將其儲存於其私用記憶體中。</span><span class="sxs-lookup"><span data-stu-id="848dd-159">At run time, the Term Lookup transformation reads the terms from the reference table and stores them in its private memory before it processes any transformation input rows.</span></span>  
  
 <span data-ttu-id="848dd-160">因為輸入資料行資料列中的詞彙可能重複，所以「詞彙查閱」轉換的輸出一般比轉換輸入擁有更多的資料列。</span><span class="sxs-lookup"><span data-stu-id="848dd-160">Because the terms in an input column row may repeat, the output of the Term Lookup transformation typically has more rows than the transformation input.</span></span>  
  
 <span data-ttu-id="848dd-161">轉換擁有一項輸入和一項輸出，</span><span class="sxs-lookup"><span data-stu-id="848dd-161">The transformation has one input and one output.</span></span> <span data-ttu-id="848dd-162">但它不支援錯誤輸出。</span><span class="sxs-lookup"><span data-stu-id="848dd-162">It does not support error outputs.</span></span>  
  
 <span data-ttu-id="848dd-163">您可以透過 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 設計師或以程式設計方式設定屬性。</span><span class="sxs-lookup"><span data-stu-id="848dd-163">You can set properties through [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="848dd-164">如需有關可在 **[詞彙查閱轉換編輯器]** 對話方塊中設定之屬性的詳細資訊，請按一下下列主題之一：</span><span class="sxs-lookup"><span data-stu-id="848dd-164">For more information about the properties that you can set in the **Term Lookup Transformation Editor** dialog box, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="848dd-165">詞彙查閱轉換編輯器 &#40;參考資料表索引標籤&#41;</span><span class="sxs-lookup"><span data-stu-id="848dd-165">Term Lookup Transformation Editor &#40;Reference Table Tab&#41;</span></span>](../../term-lookup-transformation-editor-reference-table-tab.md)  
  
-   [<span data-ttu-id="848dd-166">詞彙查閱轉換編輯器 &#40;詞彙查閱索引標籤&#41;</span><span class="sxs-lookup"><span data-stu-id="848dd-166">Term Lookup Transformation Editor &#40;Term Lookup Tab&#41;</span></span>](../../term-lookup-transformation-editor-term-lookup-tab.md)  
  
-   [<span data-ttu-id="848dd-167">詞彙查閱轉換編輯器 &#40;進階索引標籤&#41;</span><span class="sxs-lookup"><span data-stu-id="848dd-167">Term Lookup Transformation Editor &#40;Advanced Tab&#41;</span></span>](../../term-lookup-transformation-editor-advanced-tab.md)  
  
 <span data-ttu-id="848dd-168">如需有關可以在 **[進階編輯器]** 對話方塊中或以程式設計方式設定之屬性的詳細資訊，請按下列其中一個主題：</span><span class="sxs-lookup"><span data-stu-id="848dd-168">For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="848dd-169">Common Properties</span><span class="sxs-lookup"><span data-stu-id="848dd-169">Common Properties</span></span>](../../common-properties.md)  
  
-   [<span data-ttu-id="848dd-170">轉換自訂屬性</span><span class="sxs-lookup"><span data-stu-id="848dd-170">Transformation Custom Properties</span></span>](transformation-custom-properties.md)  
  
 <span data-ttu-id="848dd-171">如需如何設定屬性的詳細資訊，請參閱 [設定資料流程元件的屬性](../set-the-properties-of-a-data-flow-component.md)。</span><span class="sxs-lookup"><span data-stu-id="848dd-171">For more information about how to set properties, see [Set the Properties of a Data Flow Component](../set-the-properties-of-a-data-flow-component.md).</span></span>  
  
  
