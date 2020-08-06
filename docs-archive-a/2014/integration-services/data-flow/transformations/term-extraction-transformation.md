---
title: 詞彙擷取轉換 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.termextractiontrans.f1
helpviewer_keywords:
- word boundaries [Integration Services]
- extracting data [Integration Services]
- sentence boundaries
- word extractions [Integration Services]
- Term Extraction transformation
- tagging words
- normalized data [Integration Services]
- tokenizing text [Integration Services]
- parts of speech [Integration Services]
- text extraction [Integration Services]
- term extractions [Integration Services]
- stemming words [Integration Services]
ms.assetid: d0821526-1603-4ea6-8322-2d901568fbeb
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 8215b53de7da43bbdbcbe29a9bb7f5ad8edc0d61
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706605"
---
# <a name="term-extraction-transformation"></a><span data-ttu-id="cc3fa-102">詞彙擷取轉換</span><span class="sxs-lookup"><span data-stu-id="cc3fa-102">Term Extraction Transformation</span></span>
  <span data-ttu-id="cc3fa-103">「詞彙擷取」轉換會從轉換輸入資料行的文字中擷取詞彙，然後將這些詞彙寫入轉換輸出資料行。</span><span class="sxs-lookup"><span data-stu-id="cc3fa-103">The Term Extraction transformation extracts terms from text in a transformation input column, and then writes the terms to a transformation output column.</span></span> <span data-ttu-id="cc3fa-104">轉換只適用於英文字，它使用自己的英文字典和有關英文的語言資訊。</span><span class="sxs-lookup"><span data-stu-id="cc3fa-104">The transformation works only with English text and it uses its own English dictionary and linguistic information about English.</span></span>  
  
 <span data-ttu-id="cc3fa-105">您可以使用「詞彙擷取」轉換來探索資料集的內容。</span><span class="sxs-lookup"><span data-stu-id="cc3fa-105">You can use the Term Extraction transformation to discover the content of a data set.</span></span> <span data-ttu-id="cc3fa-106">例如，包含電子郵件訊息的文字可能會提供有關產品的有用意見反應，這樣您可以使用「詞彙擷取」轉換來擷取訊息中討論的主題，做為分析意見反應的方法。</span><span class="sxs-lookup"><span data-stu-id="cc3fa-106">For example, text that contains e-mail messages may provide useful feedback about products, so that you could use the Term Extraction transformation to extract the topics of discussion in the messages, as a way of analyzing the feedback.</span></span>  
  
## <a name="extracted-terms-and-data-types"></a><span data-ttu-id="cc3fa-107">擷取的詞彙和資料類型</span><span class="sxs-lookup"><span data-stu-id="cc3fa-107">Extracted Terms and Data Types</span></span>  
 <span data-ttu-id="cc3fa-108">「詞彙擷取」轉換可以僅擷取名詞、僅擷取名詞片語，或同時擷取名詞和名詞片語。</span><span class="sxs-lookup"><span data-stu-id="cc3fa-108">The Term Extraction transformation can extract nouns only, noun phrases only, or both nouns and noun phases.</span></span> <span data-ttu-id="cc3fa-109">名詞為單個名詞；名詞片語則至少為兩個單字，其中一個為名詞，另一個為名詞或形容詞。</span><span class="sxs-lookup"><span data-stu-id="cc3fa-109">A noun is a single noun; a noun phrases is at least two words, of which one is a noun and the other is a noun or an adjective.</span></span> <span data-ttu-id="cc3fa-110">例如，如果轉換使用「單獨名詞」選項，則它會擷取類似 *bicycle* 和 *landscape*的詞彙；如果轉換使用名詞片語選項，則它會擷取類似 *new blue bicycle*、 *bicycle helmet*和 *boxed bicycles*的詞彙。</span><span class="sxs-lookup"><span data-stu-id="cc3fa-110">For example, if the transformation uses the nouns-only option, it extracts terms like *bicycle* and *landscape*; if the transformation uses the noun phrase option, it extracts terms like *new blue bicycle*, *bicycle helmet*, and *boxed bicycles*.</span></span>  
  
 <span data-ttu-id="cc3fa-111">轉換不會擷取冠詞和代名詞。</span><span class="sxs-lookup"><span data-stu-id="cc3fa-111">Articles and pronouns are not extracted.</span></span> <span data-ttu-id="cc3fa-112">例如，「詞彙擷取」轉換會從文字 *the bicycle* 、 *my bicycle*，及 *that bicycle*中擷取詞彙 *bicycle*。</span><span class="sxs-lookup"><span data-stu-id="cc3fa-112">For example, the Term Extraction transformation extracts the term *bicycle* from the text *the bicycle*, *my bicycle*, and *that bicycle*.</span></span>  
  
 <span data-ttu-id="cc3fa-113">「詞彙擷取」轉換會為其擷取的每個詞彙產生一個分數。</span><span class="sxs-lookup"><span data-stu-id="cc3fa-113">The Term Extraction transformation generates a score for each term that it extracts.</span></span> <span data-ttu-id="cc3fa-114">此分數可以是 TFIDF 值或原始頻率，表示正規化詞彙在輸入中出現的次數。</span><span class="sxs-lookup"><span data-stu-id="cc3fa-114">The score can be either a TFIDF value or the raw frequency, meaning the number of times the normalized term appears in the input.</span></span> <span data-ttu-id="cc3fa-115">在任何一種情況下，分數都會由大於 0 的實數來表示。</span><span class="sxs-lookup"><span data-stu-id="cc3fa-115">In either case, the score is represented by a real number that is greater than 0.</span></span> <span data-ttu-id="cc3fa-116">例如，TFIDF 分數可能是值 0.5，而頻率則可能是類似 1.0 或 2.0 的值。</span><span class="sxs-lookup"><span data-stu-id="cc3fa-116">For example, the TFIDF score might have the value 0.5, and the frequency would be a value like 1.0 or 2.0.</span></span>  
  
 <span data-ttu-id="cc3fa-117">「詞彙擷取」轉換的輸出僅包含兩個資料行。</span><span class="sxs-lookup"><span data-stu-id="cc3fa-117">The output of the Term Extraction transformation includes only two columns.</span></span> <span data-ttu-id="cc3fa-118">一個資料行包含擷取的詞彙，另一資料行則包含分數。</span><span class="sxs-lookup"><span data-stu-id="cc3fa-118">One column contains the extracted terms and the other column contains the score.</span></span> <span data-ttu-id="cc3fa-119">資料行的預設名稱是**Term**和 `Score` 。</span><span class="sxs-lookup"><span data-stu-id="cc3fa-119">The default names of the columns are **Term** and `Score`.</span></span> <span data-ttu-id="cc3fa-120">因為輸入中的文字資料行可能包含多個詞彙，所以「詞彙擷取」轉換的輸出一般比輸入擁有更多的資料列。</span><span class="sxs-lookup"><span data-stu-id="cc3fa-120">Because the text column in the input may contain multiple terms, the output of the Term Extraction transformation typically has more rows than the input.</span></span>  
  
 <span data-ttu-id="cc3fa-121">如果將擷取的詞彙寫入資料表，則它們可以被其他查閱轉換 (例如「詞彙查閱」、「模糊查閱」和「查閱」轉換) 使用。</span><span class="sxs-lookup"><span data-stu-id="cc3fa-121">If the extracted terms are written to a table, they can be used by other lookup transformation such as the Term Lookup, Fuzzy Lookup, and Lookup transformations.</span></span>  
  
 <span data-ttu-id="cc3fa-122">「詞彙擷取」轉換僅能使用資料類型為 DT_WSTR 或 DT_NTEXT 之資料行中的文字。</span><span class="sxs-lookup"><span data-stu-id="cc3fa-122">The Term Extraction transformation can work only with text in a column that has either the DT_WSTR or the DT_NTEXT data type.</span></span> <span data-ttu-id="cc3fa-123">如果資料行包含文字，但不具有這些資料類型的其中之一，則可以使用「資料轉換」將資料類型為 DT_WSTR 或 DT_NTEXT 的資料行加入資料流程，並將資料行值複製到新資料行。</span><span class="sxs-lookup"><span data-stu-id="cc3fa-123">If a column contains text but does not have one of these data types, the Data Conversion transformation can be used to add a column with the DT_WSTR or DT_NTEXT data type to the data flow and copy the column values to the new column.</span></span> <span data-ttu-id="cc3fa-124">然後，「資料轉換」的輸出可以用作「詞彙擷取」轉換的輸入。</span><span class="sxs-lookup"><span data-stu-id="cc3fa-124">The output from the Data Conversion transformation can then be used as the input to the Term Extraction transformation.</span></span> <span data-ttu-id="cc3fa-125">如需詳細資訊，請參閱 [Data Conversion Transformation](data-conversion-transformation.md)。</span><span class="sxs-lookup"><span data-stu-id="cc3fa-125">For more information, see [Data Conversion Transformation](data-conversion-transformation.md).</span></span>  
  
## <a name="exclusion-terms"></a><span data-ttu-id="cc3fa-126">排除詞彙</span><span class="sxs-lookup"><span data-stu-id="cc3fa-126">Exclusion Terms</span></span>  
 <span data-ttu-id="cc3fa-127">(選擇性)「詞彙擷取」轉換可以參考包含排除詞彙 (是指當轉換從資料集中擷取詞彙時應略過的詞彙) 之資料表中的資料行。</span><span class="sxs-lookup"><span data-stu-id="cc3fa-127">Optionally, the Term Extraction transformation can reference a column in a table that contains exclusion terms, meaning terms that the transformation should skip when it extracts terms from a data set.</span></span> <span data-ttu-id="cc3fa-128">如果一組詞彙在特殊商務和產業中視為不合理 (通常因為該詞彙出現的頻率太高，而成為一個非搜尋字)，則這個功能會非常有用。</span><span class="sxs-lookup"><span data-stu-id="cc3fa-128">This is useful when a set of terms has already been identified as inconsequential in a particular business and industry, typically because the term occurs with such high frequency that it becomes a noise word.</span></span> <span data-ttu-id="cc3fa-129">例如，當從包含有關特殊品牌汽車的客戶支援資訊之資料集中擷取詞彙時，該品牌名稱自身可能會被排除，因為它被提及的頻率太高，而失去意義。</span><span class="sxs-lookup"><span data-stu-id="cc3fa-129">For example, when extracting terms from a data set that contains customer support information about a particular brand of cars, the brand name itself might be excluded because it is mentioned too frequently to have significance.</span></span> <span data-ttu-id="cc3fa-130">因此，排除清單中的值必須自訂到您要使用的資料集。</span><span class="sxs-lookup"><span data-stu-id="cc3fa-130">Therefore, the values in the exclusion list must be customized to the data set you are working with.</span></span>  
  
 <span data-ttu-id="cc3fa-131">當您將詞彙新增至排除清單時，包含該詞彙的所有詞彙 (單字或名詞片語) 也會被排除。</span><span class="sxs-lookup"><span data-stu-id="cc3fa-131">When you add a term to the exclusion list, all the terms-words or noun phrases-that contain the term are also excluded.</span></span> <span data-ttu-id="cc3fa-132">例如，如果排除清單包含單一字 *data*，則包含這個字的所有詞彙 (例如 *data*、 *data mining*、 *data integrity*和 *data validation* ) 也會被排除。</span><span class="sxs-lookup"><span data-stu-id="cc3fa-132">For example, if the exclusion list includes the single word *data*, then all the terms that contain this word, such as *data*, *data mining*, *data integrity*, and *data validation* will also be excluded.</span></span> <span data-ttu-id="cc3fa-133">如果您只想排除包含 *data*單字的複合字，則必須明確將這些複合詞彙加入至排除清單。</span><span class="sxs-lookup"><span data-stu-id="cc3fa-133">If you want to exclude only compounds that contain the word *data*, you must explicitly add those compound terms to the exclusion list.</span></span> <span data-ttu-id="cc3fa-134">例如，如果您要擷取含 *data*的個體，但要排除 *data validation*，則將 *data validation* 加入至排除清單，並確定 *data* 已從排除清單中移除。</span><span class="sxs-lookup"><span data-stu-id="cc3fa-134">For example, if you want to extract incidences of *data*, but exclude *data validation*, you would add *data validation* to the exclusion list, and make sure that *data* is removed from the exclusion list.</span></span>  
  
 <span data-ttu-id="cc3fa-135">參考資料表必須是 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 或 Access 資料庫中的資料表。</span><span class="sxs-lookup"><span data-stu-id="cc3fa-135">The reference table must be a table in a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] or an Access database.</span></span> <span data-ttu-id="cc3fa-136">「詞彙擷取」轉換會使用個別 OLE DB 連接，以連接到參考資料表。</span><span class="sxs-lookup"><span data-stu-id="cc3fa-136">The Term Extraction transformation uses a separate OLE DB connection to connect to the reference table.</span></span> <span data-ttu-id="cc3fa-137">如需相關資訊，請參閱 [OLE DB Connection Manager](../../connection-manager/ole-db-connection-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="cc3fa-137">For more information, see [OLE DB Connection Manager](../../connection-manager/ole-db-connection-manager.md).</span></span>  
  
 <span data-ttu-id="cc3fa-138">「詞彙擷取」轉換以完全預先快取模式運作。</span><span class="sxs-lookup"><span data-stu-id="cc3fa-138">The Term Extraction transformation works in a fully precached mode.</span></span> <span data-ttu-id="cc3fa-139">在執行階段，「詞彙擷取」轉換在處理任何轉換輸入資料列之前，會從參考資料表讀取排除詞彙，並將其儲存於其私用記憶體中。</span><span class="sxs-lookup"><span data-stu-id="cc3fa-139">At run time, the Term Extraction transformation reads the exclusion terms from the reference table and stores them in its private memory before it processes any transformation input rows.</span></span>  
  
## <a name="extraction-of-terms-from-text"></a><span data-ttu-id="cc3fa-140">從文字中擷取詞彙</span><span class="sxs-lookup"><span data-stu-id="cc3fa-140">Extraction of Terms from Text</span></span>  
 <span data-ttu-id="cc3fa-141">若要從文字中擷取詞彙，「詞彙擷取」轉換則需執行下列工作。</span><span class="sxs-lookup"><span data-stu-id="cc3fa-141">To extract terms from text, the Term Extraction transformation performs the following tasks.</span></span>  
  
### <a name="identification-of-words"></a><span data-ttu-id="cc3fa-142">單字的識別</span><span class="sxs-lookup"><span data-stu-id="cc3fa-142">Identification of Words</span></span>  
 <span data-ttu-id="cc3fa-143">首先，「詞彙擷取」轉換透過執行下列工作來識別單字：</span><span class="sxs-lookup"><span data-stu-id="cc3fa-143">First, the Term Extraction transformation identifies words by performing the following tasks:</span></span>  
  
-   <span data-ttu-id="cc3fa-144">使用空格、分行符號和英文中的其他單字結束字元將文字分隔成單字。</span><span class="sxs-lookup"><span data-stu-id="cc3fa-144">Separating text into words by using spaces, line breaks, and other word terminators in the English language.</span></span> <span data-ttu-id="cc3fa-145">例如，類似 *?*</span><span class="sxs-lookup"><span data-stu-id="cc3fa-145">For example, punctuation marks such as *?*</span></span> <span data-ttu-id="cc3fa-146">和 *:* 等標點符號是斷字字元。</span><span class="sxs-lookup"><span data-stu-id="cc3fa-146">and *:* are word-breaking characters.</span></span>  
  
-   <span data-ttu-id="cc3fa-147">保留由連字號或底線符號連接的單字。</span><span class="sxs-lookup"><span data-stu-id="cc3fa-147">Preserving words that are connected by hyphens or underscores.</span></span> <span data-ttu-id="cc3fa-148">例如，單字 *copy-protected* 和 *read-only* 保留為一個單字。</span><span class="sxs-lookup"><span data-stu-id="cc3fa-148">For example, the words *copy-protected* and *read-only* remain one word.</span></span>  
  
-   <span data-ttu-id="cc3fa-149">保留包含句號的完整縮寫字。</span><span class="sxs-lookup"><span data-stu-id="cc3fa-149">Keeping intact acronyms that include periods.</span></span> <span data-ttu-id="cc3fa-150">例如， *A.B.C* Company 會 Token 化為 **ABC** 和 **Company**。</span><span class="sxs-lookup"><span data-stu-id="cc3fa-150">For example, the *A.B.C* Company would be tokenized as **ABC** and **Company**.</span></span>  
  
-   <span data-ttu-id="cc3fa-151">分割特殊字元的單字。</span><span class="sxs-lookup"><span data-stu-id="cc3fa-151">Splitting words on special characters.</span></span> <span data-ttu-id="cc3fa-152">例如，單字 *date/time* 會擷取為 *date* 和 *time*， *(bicycle)* 會擷取為 *bicycle*，而 C# 則會處理為 C。特殊字元會被捨棄，不能詞彙化。</span><span class="sxs-lookup"><span data-stu-id="cc3fa-152">For example, the word *date/time* is extracted as *date* and *time*, *(bicycle)* as *bicycle*, and C# is treated as C. Special characters are discarded and cannot be lexicalized.</span></span>  
  
-   <span data-ttu-id="cc3fa-153">辨識特殊字元 (例如撇號) 不應分割單字的情況。</span><span class="sxs-lookup"><span data-stu-id="cc3fa-153">Recognizing when special characters such as the apostrophe should not split words.</span></span> <span data-ttu-id="cc3fa-154">例如，單字 *bicycle's* 不會分割為兩個單字，而會產生單一詞彙 *bicycle* (名詞)。</span><span class="sxs-lookup"><span data-stu-id="cc3fa-154">For example, the word *bicycle's* is not split into two words, and yields the single term *bicycle* (noun).</span></span>  
  
-   <span data-ttu-id="cc3fa-155">分割時間運算式、貨幣運算式、電子郵件地址和郵遞地址。</span><span class="sxs-lookup"><span data-stu-id="cc3fa-155">Splitting time expressions, monetary expressions, e-mail addresses, and postal addresses.</span></span> <span data-ttu-id="cc3fa-156">例如，日期 *January 31, 2004* 會分割為三個 Token， *January*、 *31*和 *2004*。</span><span class="sxs-lookup"><span data-stu-id="cc3fa-156">For example, the date *January 31, 2004* is separated into the three tokens *January*, *31*, and *2004*.</span></span>  
  
### <a name="tagged-words"></a><span data-ttu-id="cc3fa-157">標記的單字</span><span class="sxs-lookup"><span data-stu-id="cc3fa-157">Tagged Words</span></span>  
 <span data-ttu-id="cc3fa-158">第二，「詞彙擷取」轉換會將單字標記為下列其中一種詞類：</span><span class="sxs-lookup"><span data-stu-id="cc3fa-158">Second, the Term Extraction transformation tags words as one of the following parts of speech:</span></span>  
  
-   <span data-ttu-id="cc3fa-159">單數形式的名詞。</span><span class="sxs-lookup"><span data-stu-id="cc3fa-159">A noun in the singular form.</span></span> <span data-ttu-id="cc3fa-160">例如， *bicycle* 和 *potato*。</span><span class="sxs-lookup"><span data-stu-id="cc3fa-160">For example, *bicycle* and *potato*.</span></span>  
  
-   <span data-ttu-id="cc3fa-161">複數形式的名詞。</span><span class="sxs-lookup"><span data-stu-id="cc3fa-161">A noun in the plural form.</span></span> <span data-ttu-id="cc3fa-162">例如， *bicycles* 和 *potatoes*。</span><span class="sxs-lookup"><span data-stu-id="cc3fa-162">For example, *bicycles* and *potatoes*.</span></span> <span data-ttu-id="cc3fa-163">所有未還原的複數名詞都會進行詞幹分析。</span><span class="sxs-lookup"><span data-stu-id="cc3fa-163">All plural nouns that are not lemmatized are subject to stemming.</span></span>  
  
-   <span data-ttu-id="cc3fa-164">單數形式的專有名詞。</span><span class="sxs-lookup"><span data-stu-id="cc3fa-164">A proper noun in the singular form.</span></span> <span data-ttu-id="cc3fa-165">例如， *April* 和 *Peter*。</span><span class="sxs-lookup"><span data-stu-id="cc3fa-165">For example, *April* and *Peter*.</span></span>  
  
-   <span data-ttu-id="cc3fa-166">複數形式的專有名詞。</span><span class="sxs-lookup"><span data-stu-id="cc3fa-166">A proper noun in the plural form.</span></span> <span data-ttu-id="cc3fa-167">例如， *April* 和 *Peters*。</span><span class="sxs-lookup"><span data-stu-id="cc3fa-167">For example *Aprils* and *Peters*.</span></span> <span data-ttu-id="cc3fa-168">要進行詞幹分析的專有名詞必須是內部詞素的一部分 (限於標準英文單字)。</span><span class="sxs-lookup"><span data-stu-id="cc3fa-168">For a proper noun to be subject to stemming, it must be a part of the internal lexicon, which is limited to standard English words.</span></span>  
  
-   <span data-ttu-id="cc3fa-169">形容詞。</span><span class="sxs-lookup"><span data-stu-id="cc3fa-169">An adjective.</span></span> <span data-ttu-id="cc3fa-170">例如， *blue*。</span><span class="sxs-lookup"><span data-stu-id="cc3fa-170">For example, *blue*.</span></span>  
  
-   <span data-ttu-id="cc3fa-171">比較兩項事物的比較級形容詞。</span><span class="sxs-lookup"><span data-stu-id="cc3fa-171">A comparative adjective that compares two things.</span></span> <span data-ttu-id="cc3fa-172">例如， *higher* 和 *taller*。</span><span class="sxs-lookup"><span data-stu-id="cc3fa-172">For example, *higher* and *taller*.</span></span>  
  
-   <span data-ttu-id="cc3fa-173">識別一項事物具有高於或低於其他至少兩項事物之品質的最高級形容詞。</span><span class="sxs-lookup"><span data-stu-id="cc3fa-173">A superlative adjective that identifies a thing that has a quality above or below the level of at least two others.</span></span> <span data-ttu-id="cc3fa-174">例如， *highest* 和 *tallest*。</span><span class="sxs-lookup"><span data-stu-id="cc3fa-174">For example, *highest* and *tallest*.</span></span>  
  
-   <span data-ttu-id="cc3fa-175">數字。</span><span class="sxs-lookup"><span data-stu-id="cc3fa-175">A number.</span></span> <span data-ttu-id="cc3fa-176">例如， *62* 和 *2004*。</span><span class="sxs-lookup"><span data-stu-id="cc3fa-176">For example, *62* and *2004*.</span></span>  
  
 <span data-ttu-id="cc3fa-177">不屬於這些詞性的單字會被捨棄。</span><span class="sxs-lookup"><span data-stu-id="cc3fa-177">Words that are not one of these parts of speech are discarded.</span></span> <span data-ttu-id="cc3fa-178">例如，動詞和代名詞會被捨棄。</span><span class="sxs-lookup"><span data-stu-id="cc3fa-178">For example, verbs and pronouns are discarded.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="cc3fa-179">部分詞類的標記以統計模型為基礎，標記可能不完全精確。</span><span class="sxs-lookup"><span data-stu-id="cc3fa-179">The tagging of parts of speech is based on a statistical model and the tagging may not be completely accurate.</span></span>  
  
 <span data-ttu-id="cc3fa-180">如果「詞彙擷取」轉換設定為僅擷取名詞，則僅會擷取標記為單數或複數形式之名詞和專有名詞的單字。</span><span class="sxs-lookup"><span data-stu-id="cc3fa-180">If the Term Extraction transformation is configured to extract only nouns, only the words that are tagged as singular or plural forms of nouns and proper nouns are extracted.</span></span>  
  
 <span data-ttu-id="cc3fa-181">如果「詞彙擷取」轉換設定為僅擷取名詞片語，則標記為名詞、專有名詞、形容和數字的單字可以組合成名詞片語，但片語必須包含至少一個標記為單數或複數形式之名詞和專有名詞的單字。</span><span class="sxs-lookup"><span data-stu-id="cc3fa-181">If the Term Extraction transformation is configured to extract only noun phrases, words that are tagged as nouns, proper nouns, adjectives, and numbers may be combined to make a noun phrase, but the phrase must include at least one word that is tagged as a singular or plural form of a noun or a proper noun.</span></span> <span data-ttu-id="cc3fa-182">例如，名詞片語 *highest mountain* 由標記為最高級形容詞的單字 (*highest*) 和標記為名詞的單字 (*mountain*) 組成。</span><span class="sxs-lookup"><span data-stu-id="cc3fa-182">For example, the noun phrase *highest mountain* combines a word tagged as a superlative adjective (*highest*) and a word tagged as noun (*mountain*).</span></span>  
  
 <span data-ttu-id="cc3fa-183">如果「詞彙擷取」設定為擷取名詞和名詞片語，則會套用名詞規則和名詞片語規則。</span><span class="sxs-lookup"><span data-stu-id="cc3fa-183">If the Term Extraction is configured to extract both nouns and noun phrases, both the rules for nouns and the rules for noun phrases apply.</span></span> <span data-ttu-id="cc3fa-184">例如，轉換會從文字 *many beautiful blue bicycles* 中擷取 *bicycle* 和 *beautiful blue bicycle*。</span><span class="sxs-lookup"><span data-stu-id="cc3fa-184">For example, the transformation extracts *bicycle* and *beautiful blue bicycle* from the text *many beautiful blue bicycles*.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="cc3fa-185">擷取的詞彙依然受限於轉換使用的最大詞彙長度和頻率臨界值。</span><span class="sxs-lookup"><span data-stu-id="cc3fa-185">The extracted terms remain subject to the maximum term length and frequency threshold that the transformation uses.</span></span>  
  
### <a name="stemmed-words"></a><span data-ttu-id="cc3fa-186">詞幹分析的單字</span><span class="sxs-lookup"><span data-stu-id="cc3fa-186">Stemmed Words</span></span>  
 <span data-ttu-id="cc3fa-187">「詞彙擷取」轉換也會分析名詞的詞幹，僅擷取名詞的單數形式。</span><span class="sxs-lookup"><span data-stu-id="cc3fa-187">The Term Extraction transformation also stems nouns to extract only the singular form of a noun.</span></span> <span data-ttu-id="cc3fa-188">例如，轉換從 *men* 擷取 *man*，從 *mice* 擷取 *mouse*，從 *bicycles* 擷取 *bicycle*。</span><span class="sxs-lookup"><span data-stu-id="cc3fa-188">For example, the transformation extracts *man* from *men*, *mouse* from *mice*, and *bicycle* from *bicycles*.</span></span> <span data-ttu-id="cc3fa-189">轉換會使用其字典來分析名詞的詞幹。</span><span class="sxs-lookup"><span data-stu-id="cc3fa-189">The transformation uses its dictionary to stem nouns.</span></span> <span data-ttu-id="cc3fa-190">如果動名詞存在於字典中，則它們將做為名詞進行處理。</span><span class="sxs-lookup"><span data-stu-id="cc3fa-190">Gerunds are treated as nouns if they are in the dictionary.</span></span>  
  
 <span data-ttu-id="cc3fa-191">「詞彙擷取」轉換會透過使用「詞彙擷取」轉換內部的字典，對單字進行詞幹分析 (如以下範例所示)，使之成為在其字典中的形式。</span><span class="sxs-lookup"><span data-stu-id="cc3fa-191">The Term Extraction transformation stems words to their dictionary form as shown in these examples by using the dictionary internal to the Term Extraction transformation.</span></span>  
  
-   <span data-ttu-id="cc3fa-192">移除名詞中的 *s* 。</span><span class="sxs-lookup"><span data-stu-id="cc3fa-192">Removing *s* from nouns.</span></span> <span data-ttu-id="cc3fa-193">例如， *bicycles* 會成為 *bicycle*。</span><span class="sxs-lookup"><span data-stu-id="cc3fa-193">For example, *bicycles* becomes *bicycle*.</span></span>  
  
-   <span data-ttu-id="cc3fa-194">移除名詞中的 *es* 。</span><span class="sxs-lookup"><span data-stu-id="cc3fa-194">Removing *es* from nouns.</span></span> <span data-ttu-id="cc3fa-195">例如， *stories* 會成為 *story*。</span><span class="sxs-lookup"><span data-stu-id="cc3fa-195">For example, *stories* becomes *story*.</span></span>  
  
-   <span data-ttu-id="cc3fa-196">從字典中擷取不規則名詞的單數形式。</span><span class="sxs-lookup"><span data-stu-id="cc3fa-196">Retrieving the singular form for irregular nouns from the dictionary.</span></span> <span data-ttu-id="cc3fa-197">例如， *geese* 會成為 *goose*。</span><span class="sxs-lookup"><span data-stu-id="cc3fa-197">For example, *geese* becomes *goose*.</span></span>  
  
### <a name="normalized-words"></a><span data-ttu-id="cc3fa-198">正規化單字</span><span class="sxs-lookup"><span data-stu-id="cc3fa-198">Normalized Words</span></span>  
 <span data-ttu-id="cc3fa-199">「詞彙擷取」轉換會正規化僅由於在句子中的位置而大寫的詞彙，改用它們的小寫形式。</span><span class="sxs-lookup"><span data-stu-id="cc3fa-199">The Term Extraction transformation normalizes terms that are capitalized only because of their position in a sentence, and uses their non-capitalized form instead.</span></span> <span data-ttu-id="cc3fa-200">例如，在片語 *Dogs chase cats* 和 *Mountain paths are steep*中， *Dogs* 和 *Mountain* 將會標準化為 *dog* 和 *mountain*。</span><span class="sxs-lookup"><span data-stu-id="cc3fa-200">For example, in the phrases *Dogs chase cats* and *Mountain paths are steep*, *Dogs* and *Mountain* would be normalized to *dog* and *mountain*.</span></span>  
  
 <span data-ttu-id="cc3fa-201">「詞彙擷取」轉換會正規化單字，這樣單字的大寫版本和小寫版本就不會視作不同的詞彙進行處理。</span><span class="sxs-lookup"><span data-stu-id="cc3fa-201">The Term Extraction transformation normalizes words so that the capitalized and noncapitalized versions of words are not treated as different terms.</span></span> <span data-ttu-id="cc3fa-202">例如，在文字 *You see many bicycles in Seattle* 和 *Bicycles are blue*中， *bicycles* 和 *Bicycles* 被視為相同的詞彙，轉換僅會保留 *bicycle*。</span><span class="sxs-lookup"><span data-stu-id="cc3fa-202">For example, in the text *You see many bicycles in Seattle* and *Bicycles are blue*, *bicycles* and *Bicycles* are recognized as the same term and the transformation keeps only *bicycle*.</span></span> <span data-ttu-id="cc3fa-203">沒有列在內部字典中的專有名詞和單字不會被正規化。</span><span class="sxs-lookup"><span data-stu-id="cc3fa-203">Proper nouns and words that are not listed in the internal dictionary are not normalized.</span></span>  
  
### <a name="case-sensitive-normalization"></a><span data-ttu-id="cc3fa-204">區分大小寫正規化</span><span class="sxs-lookup"><span data-stu-id="cc3fa-204">Case-Sensitive Normalization</span></span>  
 <span data-ttu-id="cc3fa-205">「詞彙擷取」轉換可以設定為將小寫和大寫單字視為不同的詞彙，或做為同一個詞彙的不同變數。</span><span class="sxs-lookup"><span data-stu-id="cc3fa-205">The Term Extraction transformation can be configured to consider lowercase and uppercase words as either distinct terms, or as different variants of the same term.</span></span>  
  
-   <span data-ttu-id="cc3fa-206">如果設定轉換辨識大小寫的不同，則類似 *Method* 和 *method* 的詞彙將作為兩個不同的詞彙進行擷取。</span><span class="sxs-lookup"><span data-stu-id="cc3fa-206">If the transformation is configured to recognize differences in case, terms like *Method* and *method* are extracted as two different terms.</span></span> <span data-ttu-id="cc3fa-207">並非句子中第一個單字的大寫單詞絕不會正規化，而是標記為專有名詞。</span><span class="sxs-lookup"><span data-stu-id="cc3fa-207">Capitalized words that are not the first word in a sentence are never normalized, and are tagged as proper nouns.</span></span>  
  
-   <span data-ttu-id="cc3fa-208">如果設定轉換不區分大小寫，則類似 *Method* 和 *method* 的詞彙將視為一個詞彙的兩個不同變數。</span><span class="sxs-lookup"><span data-stu-id="cc3fa-208">If the transformation is configured to be case-insensitive, terms like *Method* and *method* are recognized as variants of a single term.</span></span> <span data-ttu-id="cc3fa-209">擷取的詞彙之清單可能包含 *Method* 或 *method*，視哪個單字第一個出現在輸入資料集中而定。</span><span class="sxs-lookup"><span data-stu-id="cc3fa-209">The list of extracted terms might include either *Method* or *method*, depending on which word occurs first in the input data set.</span></span> <span data-ttu-id="cc3fa-210">如果 *Method* 僅因為是句子中的第一個單字而大寫，則它將會以正規化的形式擷取。</span><span class="sxs-lookup"><span data-stu-id="cc3fa-210">If *Method* is capitalized only because it is the first word in a sentence, it is extracted in normalized form.</span></span>  
  
## <a name="sentence-and-word-boundaries"></a><span data-ttu-id="cc3fa-211">句子和單字的界限</span><span class="sxs-lookup"><span data-stu-id="cc3fa-211">Sentence and Word Boundaries</span></span>  
 <span data-ttu-id="cc3fa-212">「詞彙擷取」轉換使用下列字元作為句子界限，將文字分隔為句子：</span><span class="sxs-lookup"><span data-stu-id="cc3fa-212">The Term Extraction transformation separates text into sentences using the following characters as sentence boundaries:</span></span>  
  
-   <span data-ttu-id="cc3fa-213">ASCII 分行符號字元 0x0d (歸位字元) 和 0x0a (換行字元)。</span><span class="sxs-lookup"><span data-stu-id="cc3fa-213">ASCII line-break characters 0x0d (carriage return) and 0x0a (line feed).</span></span> <span data-ttu-id="cc3fa-214">若要使用此字元作為句子界限，則資料列中必須有兩個或兩個以上的分行符號字元。</span><span class="sxs-lookup"><span data-stu-id="cc3fa-214">To use this character as a sentence boundary, there must be two or more line-break characters in a row.</span></span>  
  
-   <span data-ttu-id="cc3fa-215">連字號 (-)。</span><span class="sxs-lookup"><span data-stu-id="cc3fa-215">Hyphens (-).</span></span> <span data-ttu-id="cc3fa-216">若要使用此字元作為句子界限，則連字號左邊或右邊字元都不能是字母。</span><span class="sxs-lookup"><span data-stu-id="cc3fa-216">To use this character as a sentence boundary, neither the character to the left nor to the right of the hyphen can be a letter.</span></span>  
  
-   <span data-ttu-id="cc3fa-217">底線符號 (_)。</span><span class="sxs-lookup"><span data-stu-id="cc3fa-217">Underscore (_).</span></span> <span data-ttu-id="cc3fa-218">若要使用此字元作為句子界限，則連字號左邊或右邊字元都不能是字母。</span><span class="sxs-lookup"><span data-stu-id="cc3fa-218">To use this character as a sentence boundary, neither the character to the left nor to the right of the hyphen can be a letter.</span></span>  
  
-   <span data-ttu-id="cc3fa-219">所有小於或等於 0x19 或者大於或等於 0x7b 的 Unicode 字元。</span><span class="sxs-lookup"><span data-stu-id="cc3fa-219">All Unicode characters that are less than or equal to 0x19, or greater than or equal to 0x7b.</span></span>  
  
-   <span data-ttu-id="cc3fa-220">數字、標點符號和字母字元的組合。</span><span class="sxs-lookup"><span data-stu-id="cc3fa-220">Combinations of numbers, punctuation marks, and alphabetical characters.</span></span> <span data-ttu-id="cc3fa-221">例如， *A23B#99* 會傳回詞彙 *A23B*。</span><span class="sxs-lookup"><span data-stu-id="cc3fa-221">For example, *A23B#99* returns the term *A23B*.</span></span>  
  
-   <span data-ttu-id="cc3fa-222">字元 %、@、&、$、#、\*、:、;、.、 **,** 、!、?、\<, >、+、=、^、~、|、\\、/、(、)、[、]、{、}、" 和 '。</span><span class="sxs-lookup"><span data-stu-id="cc3fa-222">The characters, %, @, &, $, #, \*, :, ;, ., **,** , !, ?, \<, >, +, =, ^, ~, |, \\, /, (, ), [, ], {, }, ", and '.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="cc3fa-223">包含一或多個句號 (.) 的縮寫字不會分隔為多個句子。</span><span class="sxs-lookup"><span data-stu-id="cc3fa-223">Acronyms that include one or more periods (.) are not separated into multiple sentences.</span></span>  
  
 <span data-ttu-id="cc3fa-224">然後「詞彙擷取」轉換會使用下列單字界限，將句子分隔為單字：</span><span class="sxs-lookup"><span data-stu-id="cc3fa-224">The Term Extraction transformation then separates the sentence into words using the following word boundaries:</span></span>  
  
-   <span data-ttu-id="cc3fa-225">Space</span><span class="sxs-lookup"><span data-stu-id="cc3fa-225">Space</span></span>  
  
-   <span data-ttu-id="cc3fa-226">索引標籤</span><span class="sxs-lookup"><span data-stu-id="cc3fa-226">Tab</span></span>  
  
-   <span data-ttu-id="cc3fa-227">ASCII 0x0d (歸位字元)</span><span class="sxs-lookup"><span data-stu-id="cc3fa-227">ASCII 0x0d (carriage return)</span></span>  
  
-   <span data-ttu-id="cc3fa-228">ASCII 0x0a (換行字元)</span><span class="sxs-lookup"><span data-stu-id="cc3fa-228">ASCII 0x0a (line feed)</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="cc3fa-229">如果撇號在縮寫字的單字中，例如 *we're* 或 *it's*，則該單字會在撇號處斷開；否則，撇號後面的字母將被刪除。</span><span class="sxs-lookup"><span data-stu-id="cc3fa-229">If an apostrophe is in a word that is a contraction, such as *we're* or *it's*, the word is broken at the apostrophe; otherwise, the letters following the apostrophe are trimmed.</span></span> <span data-ttu-id="cc3fa-230">例如， *we're* 會分割為 *we* 和 *'re*，而 *bicycle's* 則會刪減為 *bicycle*。</span><span class="sxs-lookup"><span data-stu-id="cc3fa-230">For example, *we're* is split into *we* and *'re*, and *bicycle's* is trimmed to *bicycle*.</span></span>  
  
## <a name="configuration-of-the-term-extraction-transformation"></a><span data-ttu-id="cc3fa-231">詞彙擷取轉換的組態</span><span class="sxs-lookup"><span data-stu-id="cc3fa-231">Configuration of the Term Extraction Transformation</span></span>  
 <span data-ttu-id="cc3fa-232">「詞彙擷取」轉換會使用內部演算法和統計模型來產生結果。</span><span class="sxs-lookup"><span data-stu-id="cc3fa-232">The Text Extraction transformation uses internal algorithms and statistical models to generate its results.</span></span> <span data-ttu-id="cc3fa-233">您可能須執行「詞彙擷取」轉換多次，並檢查結果來設定轉換，以便產生對您的文字採礦解決方案有效的結果類型。</span><span class="sxs-lookup"><span data-stu-id="cc3fa-233">You may have to run the Term Extraction transformation several times and examine the results to configure the transformation to generate the type of results that works for your text mining solution.</span></span>  
  
 <span data-ttu-id="cc3fa-234">「詞彙擷取」轉換有一個規則輸入、一個輸出及一個錯誤輸出。</span><span class="sxs-lookup"><span data-stu-id="cc3fa-234">The Term Extraction transformation has one regular input, one output, and one error output.</span></span>  
  
 <span data-ttu-id="cc3fa-235">您可以透過 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 設計師或以程式設計方式設定屬性。</span><span class="sxs-lookup"><span data-stu-id="cc3fa-235">You can set properties through [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="cc3fa-236">如需可在 [詞彙擷取轉換編輯器]\*\*\*\* 對話方塊中設定之屬性的詳細資訊，請按一下下列其中一個主題：</span><span class="sxs-lookup"><span data-stu-id="cc3fa-236">For more information about the properties that you can set in the **Term Extraction Transformation Editor** dialog box, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="cc3fa-237">詞彙擷取轉換編輯器 &#40;詞彙擷取索引標籤&#41;</span><span class="sxs-lookup"><span data-stu-id="cc3fa-237">Term Extraction Transformation Editor &#40;Term Extraction Tab&#41;</span></span>](../../term-extraction-transformation-editor-term-extraction-tab.md)  
  
-   [<span data-ttu-id="cc3fa-238">詞彙擷取轉換編輯器 &#40;排除索引標籤&#41;</span><span class="sxs-lookup"><span data-stu-id="cc3fa-238">Term Extraction Transformation Editor &#40;Exclusion Tab&#41;</span></span>](../../term-extraction-transformation-editor-exclusion-tab.md)  
  
-   [<span data-ttu-id="cc3fa-239">詞彙擷取轉換編輯器 &#40;進階索引標籤&#41;</span><span class="sxs-lookup"><span data-stu-id="cc3fa-239">Term Extraction Transformation Editor &#40;Advanced Tab&#41;</span></span>](../../term-extraction-transformation-editor-advanced-tab.md)  
  
 <span data-ttu-id="cc3fa-240">如需有關可以在 **[進階編輯器]** 對話方塊中或以程式設計方式設定之屬性的詳細資訊，請按下列其中一個主題：</span><span class="sxs-lookup"><span data-stu-id="cc3fa-240">For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="cc3fa-241">Common Properties</span><span class="sxs-lookup"><span data-stu-id="cc3fa-241">Common Properties</span></span>](../../common-properties.md)  
  
-   [<span data-ttu-id="cc3fa-242">轉換自訂屬性</span><span class="sxs-lookup"><span data-stu-id="cc3fa-242">Transformation Custom Properties</span></span>](transformation-custom-properties.md)  
  
 <span data-ttu-id="cc3fa-243">如需如何設定屬性的詳細資訊，請參閱 [設定資料流程元件的屬性](../set-the-properties-of-a-data-flow-component.md)。</span><span class="sxs-lookup"><span data-stu-id="cc3fa-243">For more information about how to set properties, see [Set the Properties of a Data Flow Component](../set-the-properties-of-a-data-flow-component.md).</span></span>  
  
  
