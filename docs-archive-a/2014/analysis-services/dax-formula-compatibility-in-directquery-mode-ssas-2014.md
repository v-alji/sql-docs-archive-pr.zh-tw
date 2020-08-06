---
title: DirectQuery 模式中的 DAX 公式相容性 (SSAS 2014) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: de83cfa9-9ffe-4e24-9c74-96a3876cb4bd
author: minewiskan
ms.author: owend
ms.openlocfilehash: acaac82d6930787a45281c0e942def8df764f4f3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594820"
---
# <a name="dax-formula-compatibility-in-directquery-mode-ssas-2014"></a><span data-ttu-id="375d4-102">DirectQuery 模式中的 DAX 公式相容性 (SSAS 2014)</span><span class="sxs-lookup"><span data-stu-id="375d4-102">DAX Formula Compatibility in DirectQuery Mode (SSAS 2014)</span></span>
<span data-ttu-id="375d4-103"> (DAX) 的資料分析運算式語言，可以用來建立量值和其他自訂公式，以用於 Analysis Services 表格式模型、 [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] Excel 活頁簿中的資料模型，以及 Power BI Desktop 資料模型。</span><span class="sxs-lookup"><span data-stu-id="375d4-103">The Data Analysis Expression language (DAX) can be used to create measures and other custom formulas for use in Analysis Services Tabular models, [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] data models in Excel workbooks, and Power BI Desktop data models.</span></span> <span data-ttu-id="375d4-104">在大部分的情況下，您在這些環境中建立的模型是相同的，而且您可以使用相同的量值、關聯性和 Kpi 等。不過，如果您撰寫 Analysis Services 表格式模型，並在 DirectQuery 模式中部署，則可以使用的公式有一些限制。</span><span class="sxs-lookup"><span data-stu-id="375d4-104">In most respects, the models you create in these environments are identical, and you can use the same measures, relationships, and KPIs, etc. However, if you author an Analysis Services Tabular model and deploy it in DirectQuery mode, there are some restrictions on the formulas that you can use.</span></span> <span data-ttu-id="375d4-105">本主題提供這些差異的總覽，列出在相容性層級1100或1103和 DirectQuery 模式下 SQL Server 2014 Analysis Services tabulars 模型中不支援的函式，並列出支援但可能會傳回不同結果的函數。</span><span class="sxs-lookup"><span data-stu-id="375d4-105">This topic provides an overview of those differences, lists the functions that are not supported in SQL Server 2014 Analysis Services tabulars model at compatibility level 1100 or 1103 and in DirectQuery mode, and lists the functions that are supported but might return different results.</span></span>  
  
<span data-ttu-id="375d4-106">在本主題中，我們會使用「*記憶體中模型*」一詞來參考表格式模型，這會在以表格式模式執行的 Analysis Services 伺服器上完全裝載記憶體內部快取資料。</span><span class="sxs-lookup"><span data-stu-id="375d4-106">Within this topic, we use the term *in-memory model* to refer to  Tabular models, which are fully hosted in-memory cached data on an Analysis Services server running in Tabular mode.</span></span> <span data-ttu-id="375d4-107">我們使用*directquery 模型*來參考在 DirectQuery 模式中撰寫及/或部署的表格式模型。</span><span class="sxs-lookup"><span data-stu-id="375d4-107">We use *DirectQuery models* to refer to Tabular models that have been authored and/or deployed in DirectQuery mode.</span></span> <span data-ttu-id="375d4-108">如需 DirectQuery 模式的相關資訊，請參閱[Directquery 模式 (SSAS 表格式) ](https://msdn.microsoft.com/45ad2965-05ec-4fb1-a164-d8060b562ea5)。</span><span class="sxs-lookup"><span data-stu-id="375d4-108">For information about DirectQuery mode, see [DirectQuery Mode (SSAS Tabular)](https://msdn.microsoft.com/45ad2965-05ec-4fb1-a164-d8060b562ea5).</span></span>  
  
  
## <a name="differences-between-in-memory-and-directquery-mode"></a><a name="bkmk_SemanticDifferences"></a><span data-ttu-id="375d4-109">記憶體內部與 DirectQuery 模式之間的差異</span><span class="sxs-lookup"><span data-stu-id="375d4-109">Differences between in-memory and DirectQuery mode</span></span>  
<span data-ttu-id="375d4-110">在 DirectQuery 模式中部署之模型的查詢，可能會傳回與在記憶體內部模式中部署之相同模型的不同結果。</span><span class="sxs-lookup"><span data-stu-id="375d4-110">Queries on a model deployed in DirectQuery mode can return different results than the same model deployed in in-memory mode.</span></span> <span data-ttu-id="375d4-111">這是因為使用 DirectQuery 時，會直接從關聯式資料存放區查詢資料，而且公式所需的匯總會使用相關的關聯式引擎來執行，而不是使用 xVelocity 的記憶體內部分析引擎 (VertiPaq) 進行儲存和計算。</span><span class="sxs-lookup"><span data-stu-id="375d4-111">This is because with DirectQuery, data is queried directly from a relational data store and aggregations required by formulas are performed using the relevant relational engine, rather than using the xVelocity in-memory analytics engine (VertiPaq) for storage and calculation.</span></span>  
  
<span data-ttu-id="375d4-112">例如，某些關聯式資料存放區處理數值、日期、Null 等項目的方式就有差異。</span><span class="sxs-lookup"><span data-stu-id="375d4-112">For example, there are differences in the way that certain relational data stores handle numeric values, dates, nulls, and so forth.</span></span>  
  
<span data-ttu-id="375d4-113">相較之下，DAX 語言的目的是要盡可能模擬 Microsoft Excel 中函數的行為。</span><span class="sxs-lookup"><span data-stu-id="375d4-113">In contrast, the DAX language is intended to emulate as closely as possible the behavior of functions in Microsoft Excel.</span></span> <span data-ttu-id="375d4-114">例如，在處理 Null、空字串和零值時，Excel 會嘗試提供最佳答案，而不考慮精確的資料類型，因此 xVelocity 引擎會執行相同的處理方式。</span><span class="sxs-lookup"><span data-stu-id="375d4-114">For example, when handling nulls, empty strings and zero values, Excel attempts to provide the best answer regardless of the precise data type, and therefore the xVelocity engine does the same.</span></span> <span data-ttu-id="375d4-115">不過，當表格式模型以 DirectQuery 模式部署並且將公式傳遞給關聯式資料來源進行評估時，系統就必須根據關聯式資料來源的語意處理資料，而這通常需要以不同的方式處理空字串與 Null。</span><span class="sxs-lookup"><span data-stu-id="375d4-115">However, when a tabular model is deployed in DirectQuery mode and passes formulas to a relational data source for evaluation, the data must be handled according to the semantics of the relational data source, which typically require distinct handling of empty strings vs. nulls.</span></span> <span data-ttu-id="375d4-116">因此，根據快取的資料以及完全從關聯式存放區中傳回的資料進行評估時，相同的公式可能會傳回不同的結果。</span><span class="sxs-lookup"><span data-stu-id="375d4-116">For this reason, the same formula might return a different result when evaluated against cached data and against data returned solely from the relational store.</span></span>  
  
<span data-ttu-id="375d4-117">此外，某些函數無法在 DirectQuery 模式中使用，因為計算需要將目前內容中的資料當做參數傳送到關聯式資料來源。</span><span class="sxs-lookup"><span data-stu-id="375d4-117">Additionally, some functions cannot be used at all in DirectQuery mode because the calculation would require the data in the current context be sent to the relational data source as a parameter.</span></span> <span data-ttu-id="375d4-118">例如，活頁簿中的量值 [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] 通常會使用參考活頁簿內可用日期範圍的時間智慧函數。</span><span class="sxs-lookup"><span data-stu-id="375d4-118">For example, measures in a [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] workbook often use time-intelligence functions that reference date ranges available within the workbook.</span></span> <span data-ttu-id="375d4-119">這類公式通常無法用於 DirectQuery 模式。</span><span class="sxs-lookup"><span data-stu-id="375d4-119">Such formulas generally cannot be used in DirectQuery mode.</span></span>  
  
## <a name="semantic-differences"></a><span data-ttu-id="375d4-120">語意差異</span><span class="sxs-lookup"><span data-stu-id="375d4-120">Semantic differences</span></span>  
<span data-ttu-id="375d4-121">本節將列出您可以預期的語意差異類型，並且描述可能適用於函數使用方式或查詢結果的任何限制。</span><span class="sxs-lookup"><span data-stu-id="375d4-121">This section lists the types of semantic differences that you can expect, and describes any limitations that might apply to the usage of functions or to query results.</span></span>  
  
### <a name="comparisons"></a><a name="bkmk_Comparisons"></a><span data-ttu-id="375d4-122">比較</span><span class="sxs-lookup"><span data-stu-id="375d4-122">Comparisons</span></span>  
<span data-ttu-id="375d4-123">記憶體內部模型中的 DAX 支援比較兩個解析為不同資料類型之純量值的運算式。</span><span class="sxs-lookup"><span data-stu-id="375d4-123">DAX in in-memory models support comparisons of two expressions that resolve to scalar values of different data types.</span></span> <span data-ttu-id="375d4-124">不過，在 DirectQuery 模式中部署的模型會使用關聯式引擎的資料類型和比較運算子，因此可能會傳回不同的結果。</span><span class="sxs-lookup"><span data-stu-id="375d4-124">However, models that are deployed in DirectQuery mode use the data types and comparison operators of the relational engine, and therefore might return different results.</span></span>  
  
<span data-ttu-id="375d4-125">在 DirectQuery 資料來源的計算中使用時，下列比較一定會傳回錯誤：</span><span class="sxs-lookup"><span data-stu-id="375d4-125">The following comparisons will always return an error when used in a calculation on a DirectQuery data source:</span></span>  
  
-   <span data-ttu-id="375d4-126">將數值資料類型與任何字串資料類型相比較</span><span class="sxs-lookup"><span data-stu-id="375d4-126">Numeric data type compared to any string data type</span></span>  
  
-   <span data-ttu-id="375d4-127">將數值資料類型與布林值相比較</span><span class="sxs-lookup"><span data-stu-id="375d4-127">Numeric data type compared to a Boolean value</span></span>  
  
-   <span data-ttu-id="375d4-128">將任何字串資料類型與布林值相比較</span><span class="sxs-lookup"><span data-stu-id="375d4-128">Any string data type compared to a Boolean value</span></span>  
  
<span data-ttu-id="375d4-129">一般而言，DAX 比較能夠容許記憶體內部模型的資料類型不符，而且將嘗試針對值進行隱含轉換 (最多兩次)，如本節所述。</span><span class="sxs-lookup"><span data-stu-id="375d4-129">In general, DAX is more forgiving of data type mismatches in in-memory models and will attempt an implicit cast of values up to two times, as described in this section.</span></span> <span data-ttu-id="375d4-130">不過，在 DirectQuery 模式中，傳送至關聯式資料存放區的公式會依照關聯式引擎的規則，以較嚴格的方式進行評估，而且比較可能會失敗。</span><span class="sxs-lookup"><span data-stu-id="375d4-130">However, formulas sent to a relational data store in DirectQuery mode are evaluated more strictly, following the rules of the relational engine, and are more likely to fail.</span></span>  
  
<span data-ttu-id="375d4-131">**字串和數字的比較**</span><span class="sxs-lookup"><span data-stu-id="375d4-131">**Comparisons of strings and numbers**</span></span>  
<span data-ttu-id="375d4-132">範例： `"2" < 3`</span><span class="sxs-lookup"><span data-stu-id="375d4-132">EXAMPLE: `"2" < 3`</span></span>  
  
<span data-ttu-id="375d4-133">此公式會比較文字字串與數字。</span><span class="sxs-lookup"><span data-stu-id="375d4-133">The formula compares a text string to a number.</span></span> <span data-ttu-id="375d4-134">在 DirectQuery 模式和記憶體內部模型中，此運算式都是 **true** 。</span><span class="sxs-lookup"><span data-stu-id="375d4-134">The expression is **true** in both DirectQuery mode and in-memory models.</span></span>  
  
<span data-ttu-id="375d4-135">在記憶體內部模型中，結果為 **true** ，因為作為字串的數字會隱含轉換成數值資料類型，以便與其他數字進行比較。</span><span class="sxs-lookup"><span data-stu-id="375d4-135">In an in-memory model, the result is **true** because numbers as strings are implicitly cast to a numerical data type for comparisons with other numbers.</span></span> <span data-ttu-id="375d4-136">SQL 也會將文字數字隱含轉換成數字，以便與數值資料類型相比較。</span><span class="sxs-lookup"><span data-stu-id="375d4-136">SQL also implicitly casts text numbers as numbers for comparison to numerical data types.</span></span>  
  
<span data-ttu-id="375d4-137">請注意，這代表第一版的行為變更 [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] ，這會傳回**false**，因為文字 "2" 一定會被視為大於任何數位。</span><span class="sxs-lookup"><span data-stu-id="375d4-137">Note that this represents a change in behavior from the first version of [!INCLUDE[ssGemini](../includes/ssgemini-md.md)], which would return **false**, because the text "2" would always be considered larger than any number.</span></span>  
  
<span data-ttu-id="375d4-138">**文字與布林值的比較**</span><span class="sxs-lookup"><span data-stu-id="375d4-138">**Comparison of text with Boolean**</span></span>  
<span data-ttu-id="375d4-139">範例： `"VERDADERO" = TRUE`</span><span class="sxs-lookup"><span data-stu-id="375d4-139">EXAMPLE: `"VERDADERO" = TRUE`</span></span>  
  
<span data-ttu-id="375d4-140">此運算式會比較文字字串與布林值。</span><span class="sxs-lookup"><span data-stu-id="375d4-140">This expression compares a text string with a Boolean value.</span></span> <span data-ttu-id="375d4-141">通常，對於 DirectQuery 或記憶體中模型而言，將字串值與布林值相比較會產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="375d4-141">In general, for DirectQuery or In-Memory models, comparing a string value to a Boolean value results in an error.</span></span> <span data-ttu-id="375d4-142">此規則的唯一例外狀況是，當字串包含 **true** 或 **false**一字時。如果字串包含任何 true 或 false 值，就會轉換成布林值並且進行比較，並提供邏輯結果。</span><span class="sxs-lookup"><span data-stu-id="375d4-142">The only exceptions to the rule are when the string contains the word **true** or the word **false**; if the string contains any of true or false values, a conversion to Boolean is made and the comparison takes place giving the logical result.</span></span>  
  
<span data-ttu-id="375d4-143">**Null 的比較**</span><span class="sxs-lookup"><span data-stu-id="375d4-143">**Comparison of nulls**</span></span>  
<span data-ttu-id="375d4-144">範例： `EVALUATE ROW("X", BLANK() = BLANK())`</span><span class="sxs-lookup"><span data-stu-id="375d4-144">EXAMPLE: `EVALUATE ROW("X", BLANK() = BLANK())`</span></span>  
  
<span data-ttu-id="375d4-145">此公式會比較兩個 Null 是否為 SQL 對等項目。</span><span class="sxs-lookup"><span data-stu-id="375d4-145">This formula compares the SQL equivalent of a null to a null.</span></span> <span data-ttu-id="375d4-146">在記憶體內部模型和 DirectQuery 模型中，它會傳回 **true** 。DirectQuery 模型會進行佈建，確保記憶體內部模型具有相似的行為。</span><span class="sxs-lookup"><span data-stu-id="375d4-146">It returns **true** in in-memory and DirectQuery models; a provision is made in DirectQuery model to guarantee similar behavior to in-memory model.</span></span>  
  
<span data-ttu-id="375d4-147">請注意，在 Transact-SQL 中，Null 永遠不等於 Null。</span><span class="sxs-lookup"><span data-stu-id="375d4-147">Note that in Transact-SQL, a null is never equal to a null.</span></span> <span data-ttu-id="375d4-148">不過，在 DAX 中，某個空白會等於另一個空白。</span><span class="sxs-lookup"><span data-stu-id="375d4-148">However, in DAX, a blank is equal to another blank.</span></span> <span data-ttu-id="375d4-149">這種行為對於所有記憶體中模型都相同。</span><span class="sxs-lookup"><span data-stu-id="375d4-149">This behavior is the same for all in-memory models.</span></span> <span data-ttu-id="375d4-150">請務必注意，DirectQuery 模式會使用 SQL Server 的大部分語意。不過，在此情況下，它會針對 NULL 比較提供新的行為，藉以區別。</span><span class="sxs-lookup"><span data-stu-id="375d4-150">It is important to note that DirectQuery mode uses, most of, the semantics of SQL Server; but, in this case it separates from it giving a new behavior to NULL comparisons.</span></span>  
  
### <a name="casts"></a><a name="bkmk_Casts"></a><span data-ttu-id="375d4-151">廣播</span><span class="sxs-lookup"><span data-stu-id="375d4-151">Casts</span></span>  
  
<span data-ttu-id="375d4-152">雖然 DAX 沒有這類轉換函數，不過在許多比較和算術運算中，它會執行隱含轉換。</span><span class="sxs-lookup"><span data-stu-id="375d4-152">There is no cast function as such in DAX, but implicit casts are performed in many comparison and arithmetic operations.</span></span> <span data-ttu-id="375d4-153">這就是決定結果資料類型的比較或算術運算。</span><span class="sxs-lookup"><span data-stu-id="375d4-153">It is the comparison or arithmetic operation that determines the data type of the result.</span></span> <span data-ttu-id="375d4-154">例如</span><span class="sxs-lookup"><span data-stu-id="375d4-154">For example,</span></span>  
  
-   <span data-ttu-id="375d4-155">在算術運算中，布林值會被視為數值 (例如 TRUE + 1) 或是套用至布林值資料行的 MIN 函數。</span><span class="sxs-lookup"><span data-stu-id="375d4-155">Boolean values are treated as numeric in arithmetic operations, such as TRUE + 1, or the function MIN applied to a column of Boolean values.</span></span> <span data-ttu-id="375d4-156">NOT 運算也會傳回數值。</span><span class="sxs-lookup"><span data-stu-id="375d4-156">A NOT operation also returns a numeric value.</span></span>  
  
-   <span data-ttu-id="375d4-157">進行比較而且搭配 EXACT、AND、OR、 &amp;&amp;或 || 使用時，布林值一定會被視為邏輯值。</span><span class="sxs-lookup"><span data-stu-id="375d4-157">Boolean values are always treated as logical values in comparisons and when used with EXACT, AND, OR, &amp;&amp;, or ||.</span></span>  
  
<span data-ttu-id="375d4-158">**從字串轉換成布林值**</span><span class="sxs-lookup"><span data-stu-id="375d4-158">**Cast from string to Boolean**</span></span>  
<span data-ttu-id="375d4-159">在記憶體內部和 DirectQuery 模型中，只允許從這些字串轉換成布林值： **""** (空字串) 、" **true"**、 **"false"**;其中空字串會轉換成 false 值。</span><span class="sxs-lookup"><span data-stu-id="375d4-159">In in-memory and DirectQuery models, casts are permitted to Boolean values from these strings only: **""** (empty string), **"true"**, **"false"**; where an empty string casts to false value.</span></span>  
  
<span data-ttu-id="375d4-160">轉換成任何其他字串的布林資料類型會產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="375d4-160">Casts to the Boolean data type of any other string results in an error.</span></span>  
  
<span data-ttu-id="375d4-161">**從字串轉換成日期/時間**</span><span class="sxs-lookup"><span data-stu-id="375d4-161">**Cast from string to date/time**</span></span>  
<span data-ttu-id="375d4-162">在 DirectQuery 模式中，從日期和時間的字串表示轉換成實際的 **datetime** 值時，其行為方式與 SQL Server 相同。</span><span class="sxs-lookup"><span data-stu-id="375d4-162">In DirectQuery mode, casts from string representations of dates and times to actual **datetime** values behave the same way as they do in SQL Server.</span></span>  
  
<span data-ttu-id="375d4-163">如需在模型中管理從字串轉換成**datetime**資料類型之規則的相關資訊 [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] ，請參閱[DAX 語法參考](/dax/dax-syntax-reference)。</span><span class="sxs-lookup"><span data-stu-id="375d4-163">For information about the rules governing casts from string to **datetime** data types in [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] models, see the [DAX Syntax Reference](/dax/dax-syntax-reference).</span></span>
  
<span data-ttu-id="375d4-164">使用記憶體中資料存放區之模型所支援的日期文字格式範圍比 SQL Server 所支援的日期字串格式更有限。</span><span class="sxs-lookup"><span data-stu-id="375d4-164">Models that use the in-memory data store support a more limited range of text formats for dates than the string formats for dates that are supported by SQL Server.</span></span> <span data-ttu-id="375d4-165">不過，DAX 支援自訂日期和時間格式。</span><span class="sxs-lookup"><span data-stu-id="375d4-165">However, DAX supports custom date and time formats.</span></span>  
  
<span data-ttu-id="375d4-166">**從字串轉換成其他非布林值**</span><span class="sxs-lookup"><span data-stu-id="375d4-166">**Cast from string to other non Boolean values**</span></span>  
<span data-ttu-id="375d4-167">從字串轉換成非布林值時，DirectQuery 模式的行為與 SQL Server 相同。</span><span class="sxs-lookup"><span data-stu-id="375d4-167">When casting from strings to non-Boolean values, DirectQuery mode behaves the same as SQL Server.</span></span> <span data-ttu-id="375d4-168">如需詳細資訊，請參閱 [CAST 和 CONVERT (Transact-SQL)](https://msdn.microsoft.com/a87d0850-c670-4720-9ad5-6f5a22343ea8)。</span><span class="sxs-lookup"><span data-stu-id="375d4-168">For more information, see [CAST and CONVERT (Transact-SQL)](https://msdn.microsoft.com/a87d0850-c670-4720-9ad5-6f5a22343ea8).</span></span>  
  
<span data-ttu-id="375d4-169">**不允許從數字轉換成字串**</span><span class="sxs-lookup"><span data-stu-id="375d4-169">**Cast from numbers to string not allowed**</span></span>  
<span data-ttu-id="375d4-170">範例： `CONCATENATE(102,",345")`</span><span class="sxs-lookup"><span data-stu-id="375d4-170">EXAMPLE: `CONCATENATE(102,",345")`</span></span>  
  
<span data-ttu-id="375d4-171">SQL Server 不允許從數字轉換成字串。</span><span class="sxs-lookup"><span data-stu-id="375d4-171">Casting from numbers to strings is not allowed in SQL Server.</span></span>  
  
<span data-ttu-id="375d4-172">在表格式模型和 DirectQuery 模式中，此公式會傳回錯誤。不過，在 [!INCLUDE[ssGemini](../includes/ssgemini-md.md)]中，此公式會產生結果。</span><span class="sxs-lookup"><span data-stu-id="375d4-172">This formula returns an error in tabular models and in DirectQuery mode; however, the formula produces a result in [!INCLUDE[ssGemini](../includes/ssgemini-md.md)].</span></span>  
  
<span data-ttu-id="375d4-173">**在 DirectQuery 中不支援兩次嘗試轉換**</span><span class="sxs-lookup"><span data-stu-id="375d4-173">**No support for two-try casts in DirectQuery**</span></span>  
<span data-ttu-id="375d4-174">當第一次轉換失敗時，記憶體中模型通常會嘗試第二次轉換。</span><span class="sxs-lookup"><span data-stu-id="375d4-174">In-memory models often attempt a second cast when the first one fails.</span></span> <span data-ttu-id="375d4-175">這在 DirectQuery 模式中絕對不會發生。</span><span class="sxs-lookup"><span data-stu-id="375d4-175">This never happens in DirectQuery mode.</span></span>  
  
<span data-ttu-id="375d4-176">範例： `TODAY() + "13:14:15"`</span><span class="sxs-lookup"><span data-stu-id="375d4-176">EXAMPLE: `TODAY() + "13:14:15"`</span></span>  
  
<span data-ttu-id="375d4-177">在此運算式中，第一個參數的類型為 **datetime** ，而第二個參數的類型為 **string**。</span><span class="sxs-lookup"><span data-stu-id="375d4-177">In this expression, the first parameter has type **datetime** and second parameter has type **string**.</span></span> <span data-ttu-id="375d4-178">不過，結合運算元時，系統將以不同的方式處理轉換。</span><span class="sxs-lookup"><span data-stu-id="375d4-178">However, the casts when combining the operands are handled differently.</span></span> <span data-ttu-id="375d4-179">DAX 將執行從 **string** 到 **double**的隱含轉換。</span><span class="sxs-lookup"><span data-stu-id="375d4-179">DAX will perform an implicit cast from **string** to **double**.</span></span> <span data-ttu-id="375d4-180">在記憶體內部模型中，公式引擎會嘗試直接轉換成 **double**，而且如果轉換失敗，它會嘗試將字串轉換成 **datetime**。</span><span class="sxs-lookup"><span data-stu-id="375d4-180">In in-memory models, the formula engine attempts to cast directly to **double**, and if that fails, it will try to cast the string to **datetime**.</span></span>  
  
<span data-ttu-id="375d4-181">在 DirectQuery 模式中，系統只會套用從 **string** 到 **double** 的直接轉換。</span><span class="sxs-lookup"><span data-stu-id="375d4-181">In DirectQuery mode, only the direct cast from **string** to **double** will be applied.</span></span> <span data-ttu-id="375d4-182">如果這項轉換失敗，公式將傳回錯誤。</span><span class="sxs-lookup"><span data-stu-id="375d4-182">If this cast fails, the formula will return an error.</span></span>  
  
### <a name="math-functions-and-arithmetic-operations"></a><a name="bkmk_Math"></a><span data-ttu-id="375d4-183">數學函數和算術運算</span><span class="sxs-lookup"><span data-stu-id="375d4-183">Math functions and arithmetic operations</span></span>  
<span data-ttu-id="375d4-184">在 DirectQuery 模式中，某些數學函數會由於可在運算中套用之基礎資料類型或轉換的差異而傳回不同的結果。</span><span class="sxs-lookup"><span data-stu-id="375d4-184">Some mathematical functions will return different results in DirectQuery mode because of differences in the underlying data type or the casts that can be applied in operations.</span></span> <span data-ttu-id="375d4-185">此外，上述有關允許值範圍的限制可能也會影響算術運算的結果。</span><span class="sxs-lookup"><span data-stu-id="375d4-185">Also, the restrictions described above on the allowed range of values might affect the outcome of arithmetic operations.</span></span>  
  
<span data-ttu-id="375d4-186">**加法順序**</span><span class="sxs-lookup"><span data-stu-id="375d4-186">**Order of addition**</span></span>  
<span data-ttu-id="375d4-187">當您建立將一連串數字相加的公式時，記憶體中模型處理這些數字的順序可能與 DirectQuery 模型不同。</span><span class="sxs-lookup"><span data-stu-id="375d4-187">When you create a formula that adds a series of numbers, an in-memory model might process the numbers in a different order than a DirectQuery model.</span></span>  <span data-ttu-id="375d4-188">因此，當您設有許多非常龐大的正數和負數時，可能會在某個運算中收到錯誤，而在另一個運算中取得結果。</span><span class="sxs-lookup"><span data-stu-id="375d4-188">Therefore, when you have many very large positive numbers and very large negative numbers, you may get an error in one operation and results in another operation.</span></span>  
  
<span data-ttu-id="375d4-189">**POWER 函數的用法**</span><span class="sxs-lookup"><span data-stu-id="375d4-189">**Use of the POWER function**</span></span>  
<span data-ttu-id="375d4-190">範例： `POWER(-64, 1/3)`</span><span class="sxs-lookup"><span data-stu-id="375d4-190">EXAMPLE: `POWER(-64, 1/3)`</span></span>  
  
<span data-ttu-id="375d4-191">在 DirectQuery 模式中，當 POWER 函數提升為分數指數時，無法使用負值做為底數。</span><span class="sxs-lookup"><span data-stu-id="375d4-191">In DirectQuery mode, the POWER function cannot use negative values as the base when raised to a fractional exponent.</span></span> <span data-ttu-id="375d4-192">這是 SQL Server 的預期行為。</span><span class="sxs-lookup"><span data-stu-id="375d4-192">This is the expected behavior in SQL Server.</span></span>  
  
<span data-ttu-id="375d4-193">在記憶體中模型中，此公式會傳回 -4。</span><span class="sxs-lookup"><span data-stu-id="375d4-193">In an in-memory model, the formula returns -4.</span></span>  
  
<span data-ttu-id="375d4-194">**數值溢位運算**</span><span class="sxs-lookup"><span data-stu-id="375d4-194">**Numerical overflow operations**</span></span>  
<span data-ttu-id="375d4-195">在 Transact-SQL 中，產生數值溢位的運算會傳回溢位錯誤。因此，產生溢位的公式也會在 DirectQuery 模式中引發錯誤。</span><span class="sxs-lookup"><span data-stu-id="375d4-195">In Transact-SQL, operations that result in a numerical overflow return an overflow error; therefore, formulas that result in an overflow also raise an error in DirectQuery mode.</span></span>  
  
<span data-ttu-id="375d4-196">不過，在記憶體中模型中使用相同的公式時，則會傳回八位元組整數。</span><span class="sxs-lookup"><span data-stu-id="375d4-196">However, the same formula when used in an in-memory model returns an eight-byte integer.</span></span> <span data-ttu-id="375d4-197">這是因為公式引擎不會執行數值溢位的檢查。</span><span class="sxs-lookup"><span data-stu-id="375d4-197">That is because the formula engine does not perform checks for numerical overflows.</span></span>  
  
<span data-ttu-id="375d4-198">**含有空白的 LOG 函數會傳回不同的結果**</span><span class="sxs-lookup"><span data-stu-id="375d4-198">**LOG functions with blanks return different results**</span></span>  
<span data-ttu-id="375d4-199">SQL Server 處理 Null 和空白的方式與 xVelocity 引擎不同。</span><span class="sxs-lookup"><span data-stu-id="375d4-199">SQL Server handles nulls and blanks differently than the xVelocity engine.</span></span> <span data-ttu-id="375d4-200">因此，下列公式會在 DirectQuery 模式中傳回錯誤，但會在記憶體中模式中傳回無限大的 (-inf) 。</span><span class="sxs-lookup"><span data-stu-id="375d4-200">As a result, the following formula returns an error in DirectQuery mode, but return infinity (-inf) in in-memory mode.</span></span>  
  
`EXAMPLE: LOG(blank())`  
  
<span data-ttu-id="375d4-201">相同的限制也適用於其他對數函數：LOG10 和 LN。</span><span class="sxs-lookup"><span data-stu-id="375d4-201">The same limitations apply to the other logarithmic functions: LOG10 and LN.</span></span>  
  
<span data-ttu-id="375d4-202">如需 DAX 中 **blank** 資料類型的詳細資訊，請參閱 [DAX 語法參考](/dax/dax-syntax-reference)。</span><span class="sxs-lookup"><span data-stu-id="375d4-202">For more information about the **blank** data type in DAX, see [DAX Syntax Reference](/dax/dax-syntax-reference).</span></span>
  
<span data-ttu-id="375d4-203">**除以 0 和除以空白**</span><span class="sxs-lookup"><span data-stu-id="375d4-203">**Division by 0 and division by Blank**</span></span>  
<span data-ttu-id="375d4-204">在 DirectQuery 模式中，除以零 (0) 或除以 BLANK 都一定會產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="375d4-204">In DirectQuery mode, division by zero (0) or division by BLANK will always result in an error.</span></span> <span data-ttu-id="375d4-205">SQL Server 不支援無限大的概念，而且因為任何除以 0 的自然結果都是無限大，所以結果就是錯誤。</span><span class="sxs-lookup"><span data-stu-id="375d4-205">SQL Server does not support the notion of infinity, and because the natural result of any division by 0 is infinity, the result is an error.</span></span> <span data-ttu-id="375d4-206">不過，SQL Server 支援除以 Null，而且結果一定等於 Null。</span><span class="sxs-lookup"><span data-stu-id="375d4-206">However, SQL Server supports division by nulls, and the result must always equal null.</span></span>  
  
<span data-ttu-id="375d4-207">在 DirectQuery 模式中，這兩種運算類型 (除以零和除以 Null) 都會傳回錯誤，而非傳回不同的結果。</span><span class="sxs-lookup"><span data-stu-id="375d4-207">Rather than return different results for these operations, in DirectQuery mode, both types of operations (division by zero and division by null) return an error.</span></span>  
  
<span data-ttu-id="375d4-208">請注意，在 Excel 和 [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] 模型中，除以零也會傳回錯誤。</span><span class="sxs-lookup"><span data-stu-id="375d4-208">Note that, in Excel and in [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] models, division by zero also returns an error.</span></span> <span data-ttu-id="375d4-209">除以空白則傳回空白。</span><span class="sxs-lookup"><span data-stu-id="375d4-209">Division by a blank returns a blank.</span></span>  
  
<span data-ttu-id="375d4-210">下列運算式在記憶體中模型中全部有效，但是在 DirectQuery 模式中則會失敗：</span><span class="sxs-lookup"><span data-stu-id="375d4-210">The following expressions are all valid in in-memory models, but will fail in DirectQuery mode:</span></span>  
  
`1/BLANK`  
  
`1/0`  
  
`0.0/BLANK`  
  
`0/0`  
  
<span data-ttu-id="375d4-211">運算式 `BLANK/BLANK` 是特殊案例，它會針對記憶體中模型和 DirectQuery 模式傳回 `BLANK` 。</span><span class="sxs-lookup"><span data-stu-id="375d4-211">The expression `BLANK/BLANK` is a special case that returns `BLANK` in both for in-memory models, and in DirectQuery mode.</span></span>  
  
### <a name="supported-numeric-and-date-time-ranges"></a><a name="bkmk_Ranges"></a><span data-ttu-id="375d4-212">支援的數值和日期-時間範圍</span><span class="sxs-lookup"><span data-stu-id="375d4-212">Supported numeric and date-time ranges</span></span>  
<span data-ttu-id="375d4-213">[!INCLUDE[ssGemini](../includes/ssgemini-md.md)]和表格式模型中的公式會受到與 Excel 相同的限制，如同實際數位和日期允許的最大值。</span><span class="sxs-lookup"><span data-stu-id="375d4-213">Formulas in [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] and tabular models in-memory are subject to the same limitations as Excel with regard to maximum allowed values for real numbers and dates.</span></span> <span data-ttu-id="375d4-214">不過，當最大值是從計算或查詢傳回，或者系統轉換、轉型、四捨五入或截斷值時，可能會發生差異。</span><span class="sxs-lookup"><span data-stu-id="375d4-214">However, differences can arise when the maximum value is returned from a calculation or query, or when values are converted, cast, rounded, or truncated.</span></span>  
  
-   <span data-ttu-id="375d4-215">如果 **Currency** 和 **Real** 類型的值相乘，而且結果大於最大可能值，則在 DirectQuery 模式中，不會引發錯誤，而且會傳回 Null。</span><span class="sxs-lookup"><span data-stu-id="375d4-215">If values of types **Currency** and **Real** are multiplied, and the result is larger than the maximum possible value, in DirectQuery mode, no error is raised, and a null is returned.</span></span>  
  
-   <span data-ttu-id="375d4-216">在記憶體中模型中，不會引發錯誤，但是會傳回最大值。</span><span class="sxs-lookup"><span data-stu-id="375d4-216">In in-memory models, no error is raised, but the maximum value is returned.</span></span>  
  
<span data-ttu-id="375d4-217">一般而言，因為 Excel 和 SQL Server 所接受的日期範圍不同，所以只有當日期位於共通日期範圍 (包括下列日期) 內時，才能保證結果相符：</span><span class="sxs-lookup"><span data-stu-id="375d4-217">In general, because the accepted date ranges are different for Excel and SQL Server, results can be guaranteed to match only when dates are within the common date range, which is inclusive of the following dates:</span></span>  
  
-   <span data-ttu-id="375d4-218">最早日期：1990 年 3 月 1 日</span><span class="sxs-lookup"><span data-stu-id="375d4-218">Earliest date: March 1, 1990</span></span>  
  
-   <span data-ttu-id="375d4-219">最晚日期：9999 年 12 月 31 日</span><span class="sxs-lookup"><span data-stu-id="375d4-219">Latest date: December 31, 9999</span></span>  
  
<span data-ttu-id="375d4-220">如果公式中使用的任何日期超過這個範圍，則公式會產生錯誤，或者結果不符。</span><span class="sxs-lookup"><span data-stu-id="375d4-220">If any dates used in formulas fall outside this range, either the formula will result in an error, or the results will not match.</span></span>  
  
<span data-ttu-id="375d4-221">**CEILING 支援的浮點值**</span><span class="sxs-lookup"><span data-stu-id="375d4-221">**Floating point values supported by CEILING**</span></span>  
<span data-ttu-id="375d4-222">範例： `EVALUATE ROW("x", CEILING(-4.398488E+30, 1))`</span><span class="sxs-lookup"><span data-stu-id="375d4-222">EXAMPLE: `EVALUATE ROW("x", CEILING(-4.398488E+30, 1))`</span></span>  
  
<span data-ttu-id="375d4-223">DAX CEILING 函數的 Transact-SQL 對等項目僅支援大小為 10^19 以下的值。</span><span class="sxs-lookup"><span data-stu-id="375d4-223">The Transact-SQL equivalent of the DAX CEILING function only supports values with magnitude of 10^19 or less.</span></span> <span data-ttu-id="375d4-224">基本原則是，浮點值應該能夠納入 **bigint**中。</span><span class="sxs-lookup"><span data-stu-id="375d4-224">A rule of thumb is that floating point values should be able to fit into **bigint**.</span></span>  
  
<span data-ttu-id="375d4-225">**所含日期超出範圍的 Datepart 函數**</span><span class="sxs-lookup"><span data-stu-id="375d4-225">**Datepart functions with dates that are out of range**</span></span>  
<span data-ttu-id="375d4-226">只有當做為引數使用的日期位於有效的日期範圍內時，才能保證 DirectQuery 模式的結果與記憶體中模型的結果相符。</span><span class="sxs-lookup"><span data-stu-id="375d4-226">Results in DirectQuery mode are guaranteed to match those in in-memory models only when the date used as the argument is in the valid date range.</span></span> <span data-ttu-id="375d4-227">如果沒有滿足這些條件，則會引發錯誤，或者公式會在 DirectQuery 與記憶體中模式中傳回不同的結果。</span><span class="sxs-lookup"><span data-stu-id="375d4-227">If these conditions are not satisfied, either an error will be raised, or the formula will return different results in DirectQuery than in in-memory mode.</span></span>  
  
<span data-ttu-id="375d4-228">範例： `MONTH(0)` 或 `YEAR(0)`</span><span class="sxs-lookup"><span data-stu-id="375d4-228">EXAMPLE: `MONTH(0)` or `YEAR(0)`</span></span>  
  
<span data-ttu-id="375d4-229">在 DirectQuery 模式中，這些運算式會分別傳回 12 和 1899。</span><span class="sxs-lookup"><span data-stu-id="375d4-229">In DirectQuery mode, the expressions return 12 and 1899, respectively.</span></span>  
  
<span data-ttu-id="375d4-230">在記憶體中模型中，這些運算式會分別傳回 1 和 1900。</span><span class="sxs-lookup"><span data-stu-id="375d4-230">In in-memory models, the expressions return 1 and 1900, respectively.</span></span>  
  
<span data-ttu-id="375d4-231">範例：  `EOMONTH(0.0001, 1)`</span><span class="sxs-lookup"><span data-stu-id="375d4-231">EXAMPLE:  `EOMONTH(0.0001, 1)`</span></span>  
  
<span data-ttu-id="375d4-232">只有當提供做為參數的日期位於有效的日期範圍內時，此運算式的結果才會相符。</span><span class="sxs-lookup"><span data-stu-id="375d4-232">The results of this expression will match only when the data supplied as a parameter is within the valid date range.</span></span>  
  
<span data-ttu-id="375d4-233">範例： `EOMONTH(blank(), blank())` 或 `EDATE(blank(), blank())`</span><span class="sxs-lookup"><span data-stu-id="375d4-233">EXAMPLE: `EOMONTH(blank(), blank())` or `EDATE(blank(), blank())`</span></span>  
  
<span data-ttu-id="375d4-234">在 DirectQuery 模式和記憶體中模式中，此運算式的結果應該都相同。</span><span class="sxs-lookup"><span data-stu-id="375d4-234">The results of this expression should be the same in DirectQuery mode and in-memory mode.</span></span>  
  
<span data-ttu-id="375d4-235">**截斷時間值**</span><span class="sxs-lookup"><span data-stu-id="375d4-235">**Truncation of time values**</span></span>  
<span data-ttu-id="375d4-236">範例： `SECOND(1231.04097222222)`</span><span class="sxs-lookup"><span data-stu-id="375d4-236">EXAMPLE: `SECOND(1231.04097222222)`</span></span>  
  
<span data-ttu-id="375d4-237">在 DirectQuery 模式中，系統會依照 SQL Server 的規則截斷結果，而且此運算式會評估為 59。</span><span class="sxs-lookup"><span data-stu-id="375d4-237">In DirectQuery mode, the result is truncated, following the rules of SQL Server, and the expression evaluates to 59.</span></span>  
  
<span data-ttu-id="375d4-238">在記憶體中模型中，每個暫時運算的結果都會四捨五入。因此，運算式會評估為 0。</span><span class="sxs-lookup"><span data-stu-id="375d4-238">In in-memory models, the results of each interim operation are rounded; therefore, the expression evaluates to 0.</span></span>  
  
<span data-ttu-id="375d4-239">下列範例將示範如何計算此值：</span><span class="sxs-lookup"><span data-stu-id="375d4-239">The following example demonstrates how this value is calculated:</span></span>  
  
1.  <span data-ttu-id="375d4-240">輸入的小數部分 (0.04097222222) 乘以 24。</span><span class="sxs-lookup"><span data-stu-id="375d4-240">The fraction of the input (0.04097222222) is multiplied by 24.</span></span>  
  
2.  <span data-ttu-id="375d4-241">產生的小時值 (0.98333333328) 乘以 60。</span><span class="sxs-lookup"><span data-stu-id="375d4-241">The resulting hour value (0.98333333328) is multiplied by 60.</span></span>  
  
3.  <span data-ttu-id="375d4-242">產生的分鐘值為 58.9999999968。</span><span class="sxs-lookup"><span data-stu-id="375d4-242">The resulting minute value is 58.9999999968.</span></span>  
  
4.  <span data-ttu-id="375d4-243">分鐘值的小數部分 (0.9999999968) 乘以 60。</span><span class="sxs-lookup"><span data-stu-id="375d4-243">The fraction of the minute value (0.9999999968) is multiplied by 60.</span></span>  
  
5.  <span data-ttu-id="375d4-244">產生的秒鐘值 (59.999999808) 四捨五入成 60。</span><span class="sxs-lookup"><span data-stu-id="375d4-244">The resulting second value (59.999999808) rounds up to 60.</span></span>  
  
6.  <span data-ttu-id="375d4-245">60 等於 0。</span><span class="sxs-lookup"><span data-stu-id="375d4-245">60 is equivalent to 0.</span></span>  
  
<span data-ttu-id="375d4-246">**不支援 SQL Time 資料類型**</span><span class="sxs-lookup"><span data-stu-id="375d4-246">**SQL Time data type not supported**</span></span>  
<span data-ttu-id="375d4-247">記憶體內部模型不支援使用新的 SQL **Time** 資料類型。</span><span class="sxs-lookup"><span data-stu-id="375d4-247">In-memory models do not support use of the new SQL **Time** data type.</span></span> <span data-ttu-id="375d4-248">在 DirectQuery 模式中，參考含有此資料類型之資料行的公式會傳回錯誤。</span><span class="sxs-lookup"><span data-stu-id="375d4-248">In DirectQuery mode, formulas that reference columns with this data type will return an error.</span></span> <span data-ttu-id="375d4-249">時間資料行無法匯入記憶體中模型。</span><span class="sxs-lookup"><span data-stu-id="375d4-249">Time data columns cannot be imported into an in-memory model.</span></span>  
  
<span data-ttu-id="375d4-250">不過，在 [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] 和的快取模型中，有時候引擎會將時間值轉換成可接受的資料類型，而且公式會傳回結果。</span><span class="sxs-lookup"><span data-stu-id="375d4-250">However, in [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] and in cached models, sometimes the engine casts the time value to an acceptable data type, and the formula returns a result.</span></span>  
  
<span data-ttu-id="375d4-251">這種行為會影響將日期資料行當做參數使用的所有函數。</span><span class="sxs-lookup"><span data-stu-id="375d4-251">This behavior affects all functions that use a date column as a parameter.</span></span>  
  
### <a name="currency"></a><a name="bkmk_Currency"></a><span data-ttu-id="375d4-252">符號</span><span class="sxs-lookup"><span data-stu-id="375d4-252">Currency</span></span>  
<span data-ttu-id="375d4-253">在 DirectQuery 模式中，如果算術運算的結果為 **Currency**類型，此值就必須位於下列範圍內：</span><span class="sxs-lookup"><span data-stu-id="375d4-253">In DirectQuery mode, if the result of an arithmetic operation has the type **Currency**, the value must be within the following range:</span></span>  
  
-   <span data-ttu-id="375d4-254">最小值：-922337203685477.5808</span><span class="sxs-lookup"><span data-stu-id="375d4-254">Minimum: -922337203685477.5808</span></span>  
  
-   <span data-ttu-id="375d4-255">最大值：922337203685477.5807</span><span class="sxs-lookup"><span data-stu-id="375d4-255">Maximum: 922337203685477.5807</span></span>  
  
<span data-ttu-id="375d4-256">**結合 Currency 與 REAL 資料類型**</span><span class="sxs-lookup"><span data-stu-id="375d4-256">**Combining currency and REAL data types**</span></span>  
<span data-ttu-id="375d4-257">範例： `Currency sample 1`</span><span class="sxs-lookup"><span data-stu-id="375d4-257">EXAMPLE: `Currency sample 1`</span></span>  
  
<span data-ttu-id="375d4-258">如果 **Currency** 和 **Real** 類型相乘，結果大於 9223372036854774784 (0x7ffffffffffffc00)，DirectQuery 模式不會引發錯誤。</span><span class="sxs-lookup"><span data-stu-id="375d4-258">If **Currency** and **Real** types are multiplied, and the result is larger than 9223372036854774784 (0x7ffffffffffffc00), DirectQuery mode will not raise an error.</span></span>  
  
<span data-ttu-id="375d4-259">在記憶體內部模型中，如果結果的絕對值大於 922337203685477.4784，則會引發錯誤。</span><span class="sxs-lookup"><span data-stu-id="375d4-259">In an in-memory model, an error is raised if the absolute value of the result is larger than 922337203685477.4784.</span></span>  
  
<span data-ttu-id="375d4-260">**運算產生超出範圍的值**</span><span class="sxs-lookup"><span data-stu-id="375d4-260">**Operation results in an out-of-range value**</span></span>  
<span data-ttu-id="375d4-261">範例： `Currency sample 2`</span><span class="sxs-lookup"><span data-stu-id="375d4-261">EXAMPLE: `Currency sample 2`</span></span>  
  
<span data-ttu-id="375d4-262">如果任兩個貨幣值的運算產生了超過指定範圍的值，記憶體中模型就會引發錯誤，但是 DirectQuery 模型不會引發錯誤。</span><span class="sxs-lookup"><span data-stu-id="375d4-262">If operations on any two currency values result in a value that is outside the specified range, an error is raised in in-memory models, but not in DirectQuery models.</span></span>  
  
<span data-ttu-id="375d4-263">**結合 Currency 與其他資料類型**</span><span class="sxs-lookup"><span data-stu-id="375d4-263">**Combining currency with other data types**</span></span>  
<span data-ttu-id="375d4-264">將貨幣值除以其他數值類型的值可能會產生不同的結果。</span><span class="sxs-lookup"><span data-stu-id="375d4-264">Division of currency values by values of other numeric types can result in different results.</span></span>  
  
### <a name="aggregation-functions"></a><a name="bkmk_Aggregations"></a><span data-ttu-id="375d4-265">彙總函式</span><span class="sxs-lookup"><span data-stu-id="375d4-265">Aggregation functions</span></span>  
<span data-ttu-id="375d4-266">含有一個資料列之資料表的統計函數會傳回不同的結果。</span><span class="sxs-lookup"><span data-stu-id="375d4-266">Statistical functions on a table with one row return different results.</span></span> <span data-ttu-id="375d4-267">此外，空白資料表的彙總函式在記憶體中模型中表現的行為也與 DirectQuery 模式不同。</span><span class="sxs-lookup"><span data-stu-id="375d4-267">Aggregation functions over empty tables also behave differently in in-memory models than they do in DirectQuery mode.</span></span>  
  
<span data-ttu-id="375d4-268">**含有單一資料列之資料表的統計函數**</span><span class="sxs-lookup"><span data-stu-id="375d4-268">**Statistical functions over a table with a single row**</span></span>  
<span data-ttu-id="375d4-269">如果當做引數使用的資料表包含單一資料列，在 DirectQuery 模式中，STDEV 和 VAR 等統計函數會傳回 Null。</span><span class="sxs-lookup"><span data-stu-id="375d4-269">If the table that is used as argument contains a single row, in DirectQuery mode, statistical functions such as STDEV and VAR return null.</span></span>  
  
<span data-ttu-id="375d4-270">在記憶體中模型中，針對含有單一資料列之資料表使用 STDEV 或 VAR 的公式會傳回除以零錯誤。</span><span class="sxs-lookup"><span data-stu-id="375d4-270">In an in-memory model, a formula that uses STDEV or VAR over a table with a single row returns a division by zero error.</span></span>  
  
### <a name="text-functions"></a><a name="bkmk_Text"></a><span data-ttu-id="375d4-271">文字函數</span><span class="sxs-lookup"><span data-stu-id="375d4-271">Text functions</span></span>  
<span data-ttu-id="375d4-272">因為關聯式資料存放區所提供的文字資料類型與 Excel 不同，所以當您搜尋字串或使用子字串時，可能會看見不同的結果。</span><span class="sxs-lookup"><span data-stu-id="375d4-272">Because relational data stores provide different text data types than does Excel, you may see different results when searching strings or working with substrings.</span></span> <span data-ttu-id="375d4-273">字串的長度可能也不同。</span><span class="sxs-lookup"><span data-stu-id="375d4-273">The length of strings also can be different.</span></span>  
  
<span data-ttu-id="375d4-274">一般而言，任何使用固定大小資料行做為引數的字串操作函數都可能具有不同的結果。</span><span class="sxs-lookup"><span data-stu-id="375d4-274">In general, any string manipulation functions that use fixed-size columns as arguments can have different results.</span></span>  
  
<span data-ttu-id="375d4-275">此外，在 SQL Server 中，某些文字函數支援 Excel 並未提供的其他引數。</span><span class="sxs-lookup"><span data-stu-id="375d4-275">Additionally, in SQL Server, some text functions support additional arguments that are not provided in Excel.</span></span> <span data-ttu-id="375d4-276">如果公式需要遺漏的引數，您可能會在記憶體中模型中取得不同的結果或錯誤。</span><span class="sxs-lookup"><span data-stu-id="375d4-276">If the formula requires the missing argument you can get different results or errors in the in-memory model.</span></span>  
  
<span data-ttu-id="375d4-277">**使用 LEFT、RIGHT 等函數傳回字元的運算可能會傳回正確但大小寫不同的字元，或者不傳回任何結果**</span><span class="sxs-lookup"><span data-stu-id="375d4-277">**Operations that return a character using LEFT, RIGHT, etc. may return the correct character but in a different case, or no results**</span></span>  
<span data-ttu-id="375d4-278">範例： `LEFT(["text"], 2)`</span><span class="sxs-lookup"><span data-stu-id="375d4-278">EXAMPLE: `LEFT(["text"], 2)`</span></span>  
  
<span data-ttu-id="375d4-279">在 DirectQuery 模式中，傳回之字元的大小寫一定與儲存在資料庫中的字母完全相同。</span><span class="sxs-lookup"><span data-stu-id="375d4-279">In DirectQuery mode, the case of the character that is returned is always exactly the same as the letter that is stored in the database.</span></span> <span data-ttu-id="375d4-280">不過，xVelocity 引擎會使用不同的演算法來壓縮值並建立索引，以便改善效能。</span><span class="sxs-lookup"><span data-stu-id="375d4-280">However, the xVelocity engine uses a different algorithm for compression and indexing of values, to improve performance.</span></span>  
  
<span data-ttu-id="375d4-281">根據預設，系統會使用 Latin1_General 定序，這種定序不區分大小寫，但是區分腔調字。</span><span class="sxs-lookup"><span data-stu-id="375d4-281">By default, the Latin1_General collation is used, which is case-insensitive but accent-sensitive.</span></span> <span data-ttu-id="375d4-282">因此，如果某個文字字串具有多個採用小寫、大寫或混合大小寫的執行個體，所有執行個體都會被視為相同的字串，而且只有字串的第一個執行個體會儲存在索引中。</span><span class="sxs-lookup"><span data-stu-id="375d4-282">Therefore, if there are multiple instances of a text string in lower case, upper case, or mixed case, all instances are considered the same string, and only the first instance of the string is stored in the index.</span></span> <span data-ttu-id="375d4-283">針對預存字串運作的所有文字函數都會擷取索引格式的指定部分。</span><span class="sxs-lookup"><span data-stu-id="375d4-283">All text functions that operate on stored strings will retrieve the specified portion of the indexed form.</span></span> <span data-ttu-id="375d4-284">因此，範例公式會使用第一個執行個體做為輸入，針對整個資料行傳回相同的值。</span><span class="sxs-lookup"><span data-stu-id="375d4-284">Therefore, the example formula would return the same value for the entire column, using the first instance as the input.</span></span>  
  
[<span data-ttu-id="375d4-285">表格式模型中的字串儲存和定序</span><span class="sxs-lookup"><span data-stu-id="375d4-285">String Storage and Collation in Tabular Models</span></span>](https://msdn.microsoft.com/8516f0ad-32ee-4688-a304-e705143642ca)  
  
<span data-ttu-id="375d4-286">這種行為也適用於其他文字函數，包括 RIGHT、MID 等等。</span><span class="sxs-lookup"><span data-stu-id="375d4-286">This behavior also applies to other text functions, including RIGHT, MID, and so forth.</span></span>  
  
<span data-ttu-id="375d4-287">**字串長度會影響結果**</span><span class="sxs-lookup"><span data-stu-id="375d4-287">**String length affects results**</span></span>  
<span data-ttu-id="375d4-288">範例： `SEARCH("within string", "sample target  text", 1, 1)`</span><span class="sxs-lookup"><span data-stu-id="375d4-288">EXAMPLE: `SEARCH("within string", "sample target  text", 1, 1)`</span></span>  
  
<span data-ttu-id="375d4-289">如果您使用 SEARCH 函數來搜尋字串，而且目標字串的長度超過 within string，DirectQuery 模式就會引發錯誤。</span><span class="sxs-lookup"><span data-stu-id="375d4-289">If you search for a string using the SEARCH function, and the target string is longer than the within string, DirectQuery mode raises an error.</span></span>  
  
<span data-ttu-id="375d4-290">在記憶體內部模型中，系統會傳回搜尋的字串，但是其長度會截斷至 &lt;within text&gt;的長度。</span><span class="sxs-lookup"><span data-stu-id="375d4-290">In an in-memory model, the searched string is returned, but with its length truncated to the length of &lt;within text&gt;.</span></span>  
  
<span data-ttu-id="375d4-291">範例： `EVALUATE ROW("X", REPLACE("CA", 3, 2, "California") )`</span><span class="sxs-lookup"><span data-stu-id="375d4-291">EXAMPLE: `EVALUATE ROW("X", REPLACE("CA", 3, 2, "California") )`</span></span>  
  
<span data-ttu-id="375d4-292">如果取代字串的長度大於原始字串的長度，在 DirectQuery 模式中，此公式會傳回 Null。</span><span class="sxs-lookup"><span data-stu-id="375d4-292">If the length of the replacement string is greater than the length of the original string, in DirectQuery mode, the formula returns null.</span></span>  
  
<span data-ttu-id="375d4-293">在記憶體中模型中，此公式會依照 Excel 的行為 (串連來源字串與取代字串)，並且傳回 CACalifornia。</span><span class="sxs-lookup"><span data-stu-id="375d4-293">In in-memory models, the formula follows the behavior of Excel, which concatenates the source string and the replacement string, which returns CACalifornia.</span></span>  
  
<span data-ttu-id="375d4-294">**字串中間的隱含 TRIM**</span><span class="sxs-lookup"><span data-stu-id="375d4-294">**Implicit TRIM in the middle of strings**</span></span>  
<span data-ttu-id="375d4-295">範例： `TRIM(" A sample sentence with leading white space")`</span><span class="sxs-lookup"><span data-stu-id="375d4-295">EXAMPLE: `TRIM(" A sample sentence with leading white space")`</span></span>  
  
<span data-ttu-id="375d4-296">DirectQuery 模式會將 DAX TRIM 函數轉譯成 SQL 陳述式 `LTRIM(RTRIM(<column>))`。</span><span class="sxs-lookup"><span data-stu-id="375d4-296">DirectQuery mode translates the DAX TRIM function to the SQL statement `LTRIM(RTRIM(<column>))`.</span></span> <span data-ttu-id="375d4-297">因此，只會移除開頭和尾端空白字元。</span><span class="sxs-lookup"><span data-stu-id="375d4-297">As a result, only leading and trailing white space is removed.</span></span>  
  
<span data-ttu-id="375d4-298">相較之下，記憶體中模型中的相同公式會依照 Excel 的行為，移除字串內的空格。</span><span class="sxs-lookup"><span data-stu-id="375d4-298">In contrast, the same formula in an in-memory model removes spaces within the string, following the behavior of Excel.</span></span>  
  
<span data-ttu-id="375d4-299">**搭配 LEN 函數使用的隱含 RTRIM**</span><span class="sxs-lookup"><span data-stu-id="375d4-299">**Implicit RTRIM with use of LEN function**</span></span>  
<span data-ttu-id="375d4-300">範例： `LEN('string_column')`</span><span class="sxs-lookup"><span data-stu-id="375d4-300">EXAMPLE: `LEN('string_column')`</span></span>  
  
<span data-ttu-id="375d4-301">與 SQL Server 相同的是，DirectQuery 模式會自動從字串資料行的結尾移除空白字元：也就是說，它會執行隱含 RTRIM。</span><span class="sxs-lookup"><span data-stu-id="375d4-301">Like SQL Server, DirectQuery mode automatically removes white space from the end of string columns: that is, it performs an implicit RTRIM.</span></span> <span data-ttu-id="375d4-302">因此，如果字串具有尾端空格，使用 LEN 函數的公式可能會傳回不同的結果。</span><span class="sxs-lookup"><span data-stu-id="375d4-302">Therefore, formulas that use the LEN function can return different values if the string has trailing spaces.</span></span>  
  
<span data-ttu-id="375d4-303">**記憶體支援 SUBSTITUTE 的其他參數**</span><span class="sxs-lookup"><span data-stu-id="375d4-303">**In-memory supports additional parameters for SUBSTITUTE**</span></span>  
<span data-ttu-id="375d4-304">範例： `SUBSTITUTE([Title],"Doctor","Dr.")`</span><span class="sxs-lookup"><span data-stu-id="375d4-304">EXAMPLE: `SUBSTITUTE([Title],"Doctor","Dr.")`</span></span>  
  
<span data-ttu-id="375d4-305">範例： `SUBSTITUTE([Title],"Doctor","Dr.", 2)`</span><span class="sxs-lookup"><span data-stu-id="375d4-305">EXAMPLE: `SUBSTITUTE([Title],"Doctor","Dr.", 2)`</span></span>  
  
<span data-ttu-id="375d4-306">在 DirectQuery 模式中，您只能使用這個具有三個 (3) 參數的函數版本：資料行的參考、舊文字和新文字。</span><span class="sxs-lookup"><span data-stu-id="375d4-306">In DirectQuery mode, you can use only the version of this function that has three (3) parameters: a reference to a column, the old text, and the new text.</span></span> <span data-ttu-id="375d4-307">如果您使用第二個公式，就會引發錯誤。</span><span class="sxs-lookup"><span data-stu-id="375d4-307">If you use the second formula, an error is raised.</span></span>  
  
<span data-ttu-id="375d4-308">在記憶體中模型中，您可以使用選擇性的第四個參數來指定要取代之字串的執行個體編號。</span><span class="sxs-lookup"><span data-stu-id="375d4-308">In in-memory models, you can use an optional fourth parameter to specify the instance number of the string to replace.</span></span> <span data-ttu-id="375d4-309">例如，您可以單獨取代第二個執行個體。</span><span class="sxs-lookup"><span data-stu-id="375d4-309">For example, you can replace only the second instance, etc.</span></span>  
  
<span data-ttu-id="375d4-310">**REPT 運算的字串長度限制**</span><span class="sxs-lookup"><span data-stu-id="375d4-310">**Restrictions on string lengths for REPT operations**</span></span>  
<span data-ttu-id="375d4-311">在記憶體中模型中，使用 REPT 之運算所產生的字串長度必須小於 32,767 個字元。</span><span class="sxs-lookup"><span data-stu-id="375d4-311">In in-memory models, the length of a string resulting from an operation using REPT must be less than 32,767 characters.</span></span>  
  
<span data-ttu-id="375d4-312">這項限制不適用於 DirectQuery 模式。</span><span class="sxs-lookup"><span data-stu-id="375d4-312">This limitation does not apply in DirectQuery mode.</span></span>  
  
<span data-ttu-id="375d4-313">**子字串運算會根據字元類型傳回不同的結果**</span><span class="sxs-lookup"><span data-stu-id="375d4-313">**Substring operations return different results depending on character type**</span></span>  
<span data-ttu-id="375d4-314">範例： `MID([col], 2, 5)`</span><span class="sxs-lookup"><span data-stu-id="375d4-314">EXAMPLE: `MID([col], 2, 5)`</span></span>  
  
<span data-ttu-id="375d4-315">如果輸入文字為 **varchar** 或 **nvarchar**，公式的結果一定相同。</span><span class="sxs-lookup"><span data-stu-id="375d4-315">If the input text is **varchar** or **nvarchar**, the result of the formula is always the same.</span></span>  
  
<span data-ttu-id="375d4-316">不過，如果文字是固定長度字元，而\* &lt; num_chars &gt; \*的值大於目標字串的長度，在 DirectQuery 模式中，就會在結果字串的結尾加入空白。</span><span class="sxs-lookup"><span data-stu-id="375d4-316">However, if the text is a fixed-length character and the value for *&lt;num_chars&gt;* is greater than the length of the target string, in DirectQuery mode, a blank is added at the end of the result string.</span></span>  
  
<span data-ttu-id="375d4-317">在記憶體中模型中，結果會在最後一個字串字元處終止，而且沒有填補。</span><span class="sxs-lookup"><span data-stu-id="375d4-317">In an in-memory model, the result terminates at the last string character, with no padding.</span></span>  
  
## <a name="functions-supported-in-directquery-mode"></a><a name="bkmk_SupportedFunc"></a><span data-ttu-id="375d4-318">DirectQuery 模式中支援的函式</span><span class="sxs-lookup"><span data-stu-id="375d4-318">Functions supported in DirectQuery mode</span></span>  
<span data-ttu-id="375d4-319">下列 DAX 函數可用於 DirectQuery 模式，但是使用條件如上一節所述。</span><span class="sxs-lookup"><span data-stu-id="375d4-319">The following DAX functions can be used in DirectQuery mode, but with the qualifications as described in the preceding section.</span></span>  
  
<span data-ttu-id="375d4-320">**文字函數**</span><span class="sxs-lookup"><span data-stu-id="375d4-320">**Text functions**</span></span>  
  
<span data-ttu-id="375d4-321">CONCATENATE</span><span class="sxs-lookup"><span data-stu-id="375d4-321">CONCATENATE</span></span>  
  
<span data-ttu-id="375d4-322">FIND</span><span class="sxs-lookup"><span data-stu-id="375d4-322">FIND</span></span>  
  
<span data-ttu-id="375d4-323">LEFT</span><span class="sxs-lookup"><span data-stu-id="375d4-323">LEFT</span></span>  
  
<span data-ttu-id="375d4-324">LEN</span><span class="sxs-lookup"><span data-stu-id="375d4-324">LEN</span></span>  
  
<span data-ttu-id="375d4-325">MID</span><span class="sxs-lookup"><span data-stu-id="375d4-325">MID</span></span>  
  
<span data-ttu-id="375d4-326">REPLACE</span><span class="sxs-lookup"><span data-stu-id="375d4-326">REPLACE</span></span>  
  
<span data-ttu-id="375d4-327">REPT</span><span class="sxs-lookup"><span data-stu-id="375d4-327">REPT</span></span>  
  
<span data-ttu-id="375d4-328">RIGHT</span><span class="sxs-lookup"><span data-stu-id="375d4-328">RIGHT</span></span>  
  
<span data-ttu-id="375d4-329">SUBSTITUTE</span><span class="sxs-lookup"><span data-stu-id="375d4-329">SUBSTITUTE</span></span>  
  
<span data-ttu-id="375d4-330">TRIM</span><span class="sxs-lookup"><span data-stu-id="375d4-330">TRIM</span></span>  
  
<span data-ttu-id="375d4-331">**統計函式**</span><span class="sxs-lookup"><span data-stu-id="375d4-331">**Statistical functions**</span></span>  
  
<span data-ttu-id="375d4-332">COUNT</span><span class="sxs-lookup"><span data-stu-id="375d4-332">COUNT</span></span>  
  
<span data-ttu-id="375d4-333">STDEV.P</span><span class="sxs-lookup"><span data-stu-id="375d4-333">STDEV.P</span></span>  
  
<span data-ttu-id="375d4-334">STDEV.S</span><span class="sxs-lookup"><span data-stu-id="375d4-334">STDEV.S</span></span>  
  
<span data-ttu-id="375d4-335">STDEVX.P</span><span class="sxs-lookup"><span data-stu-id="375d4-335">STDEVX.P</span></span>  
  
<span data-ttu-id="375d4-336">STDEVX.S</span><span class="sxs-lookup"><span data-stu-id="375d4-336">STDEVX.S</span></span>  
  
<span data-ttu-id="375d4-337">VAR.P</span><span class="sxs-lookup"><span data-stu-id="375d4-337">VAR.P</span></span>  
  
<span data-ttu-id="375d4-338">VAR.S</span><span class="sxs-lookup"><span data-stu-id="375d4-338">VAR.S</span></span>  
  
<span data-ttu-id="375d4-339">VARX.P</span><span class="sxs-lookup"><span data-stu-id="375d4-339">VARX.P</span></span>  
  
<span data-ttu-id="375d4-340">VARX.S</span><span class="sxs-lookup"><span data-stu-id="375d4-340">VARX.S</span></span>  
  
<span data-ttu-id="375d4-341">**日期/時間函數**</span><span class="sxs-lookup"><span data-stu-id="375d4-341">**Date/time functions**</span></span>  
  
<span data-ttu-id="375d4-342">日期</span><span class="sxs-lookup"><span data-stu-id="375d4-342">DATE</span></span>  
  
<span data-ttu-id="375d4-343">EDATE</span><span class="sxs-lookup"><span data-stu-id="375d4-343">EDATE</span></span>  
  
<span data-ttu-id="375d4-344">EOMONTH</span><span class="sxs-lookup"><span data-stu-id="375d4-344">EOMONTH</span></span>  
  
<span data-ttu-id="375d4-345">日期</span><span class="sxs-lookup"><span data-stu-id="375d4-345">DATE</span></span>  
  
<span data-ttu-id="375d4-346">TIME</span><span class="sxs-lookup"><span data-stu-id="375d4-346">TIME</span></span>  
  
<span data-ttu-id="375d4-347">SECOND</span><span class="sxs-lookup"><span data-stu-id="375d4-347">SECOND</span></span>  
  
<span data-ttu-id="375d4-348">**數學與數字函數**</span><span class="sxs-lookup"><span data-stu-id="375d4-348">**Math and number functions**</span></span>  
  
<span data-ttu-id="375d4-349">CEILING</span><span class="sxs-lookup"><span data-stu-id="375d4-349">CEILING</span></span>  
  
<span data-ttu-id="375d4-350">LN</span><span class="sxs-lookup"><span data-stu-id="375d4-350">LN</span></span>  
  
<span data-ttu-id="375d4-351">記錄</span><span class="sxs-lookup"><span data-stu-id="375d4-351">LOG</span></span>  
  
<span data-ttu-id="375d4-352">LOG10</span><span class="sxs-lookup"><span data-stu-id="375d4-352">LOG10</span></span>  
  
<span data-ttu-id="375d4-353">POWER</span><span class="sxs-lookup"><span data-stu-id="375d4-353">POWER</span></span>  
  
<span data-ttu-id="375d4-354">**DAX 資料表查詢**</span><span class="sxs-lookup"><span data-stu-id="375d4-354">**DAX Table queries**</span></span>  
  
<span data-ttu-id="375d4-355">當您使用 DAX 資料表查詢，針對 DirectQuery 模型評估公式時，具有一些限制。</span><span class="sxs-lookup"><span data-stu-id="375d4-355">There are some limitations when you evaluate formulas against a DirectQuery model by using DAX Table queries.</span></span> <span data-ttu-id="375d4-356">DirectQuery 不支援在 ORDER BY 子句中參考相同的資料行兩次。</span><span class="sxs-lookup"><span data-stu-id="375d4-356">DirectQuery does not support referring to the same column twice in an ORDER BY clause.</span></span> <span data-ttu-id="375d4-357">您無法建立對等的 Transact-SQL 陳述式，而且查詢會失敗。</span><span class="sxs-lookup"><span data-stu-id="375d4-357">The equivalent Transact-SQL statement cannot be created and the query fails.</span></span>  
  
<span data-ttu-id="375d4-358">在記憶體中模型中，重複 ORDER BY 子句不會影響結果。</span><span class="sxs-lookup"><span data-stu-id="375d4-358">In an in-memory model, repeating the ORDER by clause has no effect on the results.</span></span>  
  
## <a name="functions-not-supported-in-directquery-mode"></a><a name="bkmk_NotSupportedFunc"></a><span data-ttu-id="375d4-359">DirectQuery 模式不支援的函數</span><span class="sxs-lookup"><span data-stu-id="375d4-359">Functions not supported in DirectQuery Mode</span></span>  
<span data-ttu-id="375d4-360">在 DirectQuery 模式中部署的模型不支援某些 DAX 函數。</span><span class="sxs-lookup"><span data-stu-id="375d4-360">Some DAX functions are not supported in models that are deployed in DirectQuery mode.</span></span> <span data-ttu-id="375d4-361">不支援特定函數的原因可能包括下列任何一個原因或這些原因的組合：</span><span class="sxs-lookup"><span data-stu-id="375d4-361">The reasons that a particular function is not supported can include any or a combination of these reasons:</span></span>  
  
-   <span data-ttu-id="375d4-362">基礎關聯式引擎無法執行相當於 xVelocity 引擎所執行的計算。</span><span class="sxs-lookup"><span data-stu-id="375d4-362">The underlying relational engine cannot perform calculations equivalent to those performed by the xVelocity engine.</span></span>  
  
-   <span data-ttu-id="375d4-363">公式無法轉換成對等的 SQL 運算式。</span><span class="sxs-lookup"><span data-stu-id="375d4-363">The formula cannot be converted to en equivalent SQL expression.</span></span>  
  
-   <span data-ttu-id="375d4-364">無法接受轉換的運算式以及產生的計算效能。</span><span class="sxs-lookup"><span data-stu-id="375d4-364">The performance of the converted expression and the resulting calculations would be unacceptable.</span></span>  
  
<span data-ttu-id="375d4-365">下列 DAX 函數無法用於 DirectQuery 模型。</span><span class="sxs-lookup"><span data-stu-id="375d4-365">The following DAX functions cannot be used in DirectQuery models.</span></span>  
  
<span data-ttu-id="375d4-366">**路徑函數**</span><span class="sxs-lookup"><span data-stu-id="375d4-366">**Path functions**</span></span>  
  
<span data-ttu-id="375d4-367">PATH</span><span class="sxs-lookup"><span data-stu-id="375d4-367">PATH</span></span>  
  
<span data-ttu-id="375d4-368">PATHCONTAINS</span><span class="sxs-lookup"><span data-stu-id="375d4-368">PATHCONTAINS</span></span>  
  
<span data-ttu-id="375d4-369">PATHITEM</span><span class="sxs-lookup"><span data-stu-id="375d4-369">PATHITEM</span></span>  
  
<span data-ttu-id="375d4-370">PATHITEMREVERSE</span><span class="sxs-lookup"><span data-stu-id="375d4-370">PATHITEMREVERSE</span></span>  
  
<span data-ttu-id="375d4-371">PATHLENGTH</span><span class="sxs-lookup"><span data-stu-id="375d4-371">PATHLENGTH</span></span>  
  
<span data-ttu-id="375d4-372">**其他函數**</span><span class="sxs-lookup"><span data-stu-id="375d4-372">**Misc functions**</span></span>  
  
<span data-ttu-id="375d4-373">COUNTBLANK</span><span class="sxs-lookup"><span data-stu-id="375d4-373">COUNTBLANK</span></span>  
  
<span data-ttu-id="375d4-374">FIXED</span><span class="sxs-lookup"><span data-stu-id="375d4-374">FIXED</span></span>  
  
<span data-ttu-id="375d4-375">FORMAT</span><span class="sxs-lookup"><span data-stu-id="375d4-375">FORMAT</span></span>  
  
<span data-ttu-id="375d4-376">RAND</span><span class="sxs-lookup"><span data-stu-id="375d4-376">RAND</span></span>  
  
<span data-ttu-id="375d4-377">RANDBETWEEN</span><span class="sxs-lookup"><span data-stu-id="375d4-377">RANDBETWEEN</span></span>  
  
<span data-ttu-id="375d4-378">**時間智慧函數：開始和結束日期**</span><span class="sxs-lookup"><span data-stu-id="375d4-378">**Time intelligence functions: Start and end dates**</span></span>  
  
<span data-ttu-id="375d4-379">DATESQTD</span><span class="sxs-lookup"><span data-stu-id="375d4-379">DATESQTD</span></span>  
  
<span data-ttu-id="375d4-380">DATESYTD</span><span class="sxs-lookup"><span data-stu-id="375d4-380">DATESYTD</span></span>  
  
<span data-ttu-id="375d4-381">DATESMTD</span><span class="sxs-lookup"><span data-stu-id="375d4-381">DATESMTD</span></span>  
  
<span data-ttu-id="375d4-382">DATESQTD</span><span class="sxs-lookup"><span data-stu-id="375d4-382">DATESQTD</span></span>  
  
<span data-ttu-id="375d4-383">DATESINPERIOD</span><span class="sxs-lookup"><span data-stu-id="375d4-383">DATESINPERIOD</span></span>  
  
<span data-ttu-id="375d4-384">TOTALMTD</span><span class="sxs-lookup"><span data-stu-id="375d4-384">TOTALMTD</span></span>  
  
<span data-ttu-id="375d4-385">TOTALQTD</span><span class="sxs-lookup"><span data-stu-id="375d4-385">TOTALQTD</span></span>  
  
<span data-ttu-id="375d4-386">TOTALYTD</span><span class="sxs-lookup"><span data-stu-id="375d4-386">TOTALYTD</span></span>  
  
<span data-ttu-id="375d4-387">DATESINPERIOD</span><span class="sxs-lookup"><span data-stu-id="375d4-387">DATESINPERIOD</span></span>  
  
<span data-ttu-id="375d4-388">SAMEPERIODLASTYEAR</span><span class="sxs-lookup"><span data-stu-id="375d4-388">SAMEPERIODLASTYEAR</span></span>  
  
<span data-ttu-id="375d4-389">PARALLELPERIOD</span><span class="sxs-lookup"><span data-stu-id="375d4-389">PARALLELPERIOD</span></span>  
  
<span data-ttu-id="375d4-390">**時間智慧函數：餘額**</span><span class="sxs-lookup"><span data-stu-id="375d4-390">**Time-intelligence functions: Balances**</span></span>  
  
<span data-ttu-id="375d4-391">OPENINGBALANCEMONTH</span><span class="sxs-lookup"><span data-stu-id="375d4-391">OPENINGBALANCEMONTH</span></span>  
  
<span data-ttu-id="375d4-392">OPENINGBALANCEQUARTER</span><span class="sxs-lookup"><span data-stu-id="375d4-392">OPENINGBALANCEQUARTER</span></span>  
  
<span data-ttu-id="375d4-393">OPENINGBALANCEYEAR</span><span class="sxs-lookup"><span data-stu-id="375d4-393">OPENINGBALANCEYEAR</span></span>  
  
<span data-ttu-id="375d4-394">CLOSINGBALANCEMONTH</span><span class="sxs-lookup"><span data-stu-id="375d4-394">CLOSINGBALANCEMONTH</span></span>  
  
<span data-ttu-id="375d4-395">CLOSINGBALANCEQUARTER</span><span class="sxs-lookup"><span data-stu-id="375d4-395">CLOSINGBALANCEQUARTER</span></span>  
  
<span data-ttu-id="375d4-396">CLOSINGBALANCEYEAR</span><span class="sxs-lookup"><span data-stu-id="375d4-396">CLOSINGBALANCEYEAR</span></span>  
  
<span data-ttu-id="375d4-397">**時間智慧函數：上一個和下一個週期**</span><span class="sxs-lookup"><span data-stu-id="375d4-397">**Time intelligence functions: Previous and next periods**</span></span>  
  
<span data-ttu-id="375d4-398">PREVIOUSDAY</span><span class="sxs-lookup"><span data-stu-id="375d4-398">PREVIOUSDAY</span></span>  
  
<span data-ttu-id="375d4-399">PREVIOUSMONTH</span><span class="sxs-lookup"><span data-stu-id="375d4-399">PREVIOUSMONTH</span></span>  
  
<span data-ttu-id="375d4-400">PREVIOUSQUARTER</span><span class="sxs-lookup"><span data-stu-id="375d4-400">PREVIOUSQUARTER</span></span>  
  
<span data-ttu-id="375d4-401">PREVIOUSYEAR</span><span class="sxs-lookup"><span data-stu-id="375d4-401">PREVIOUSYEAR</span></span>  
  
<span data-ttu-id="375d4-402">NEXTDAY</span><span class="sxs-lookup"><span data-stu-id="375d4-402">NEXTDAY</span></span>  
  
<span data-ttu-id="375d4-403">NEXTMONTH</span><span class="sxs-lookup"><span data-stu-id="375d4-403">NEXTMONTH</span></span>  
  
<span data-ttu-id="375d4-404">NEXTQUARTER</span><span class="sxs-lookup"><span data-stu-id="375d4-404">NEXTQUARTER</span></span>  
  
<span data-ttu-id="375d4-405">NEXTYEAR</span><span class="sxs-lookup"><span data-stu-id="375d4-405">NEXTYEAR</span></span>  
  
<span data-ttu-id="375d4-406">**時間智慧函數：週期和週期的計算**</span><span class="sxs-lookup"><span data-stu-id="375d4-406">**Time intelligence functions: Periods and calculations over periods**</span></span>  
  
<span data-ttu-id="375d4-407">STARTOFMONTH</span><span class="sxs-lookup"><span data-stu-id="375d4-407">STARTOFMONTH</span></span>  
  
<span data-ttu-id="375d4-408">STARTOFQUARTER</span><span class="sxs-lookup"><span data-stu-id="375d4-408">STARTOFQUARTER</span></span>  
  
<span data-ttu-id="375d4-409">STARTOFYEAR</span><span class="sxs-lookup"><span data-stu-id="375d4-409">STARTOFYEAR</span></span>  
  
<span data-ttu-id="375d4-410">ENDOFMONTH</span><span class="sxs-lookup"><span data-stu-id="375d4-410">ENDOFMONTH</span></span>  
  
<span data-ttu-id="375d4-411">ENDOFQUARTER</span><span class="sxs-lookup"><span data-stu-id="375d4-411">ENDOFQUARTER</span></span>  
  
<span data-ttu-id="375d4-412">ENDOFYEAR</span><span class="sxs-lookup"><span data-stu-id="375d4-412">ENDOFYEAR</span></span>  
  
<span data-ttu-id="375d4-413">FIRSTDATE</span><span class="sxs-lookup"><span data-stu-id="375d4-413">FIRSTDATE</span></span>  
  
<span data-ttu-id="375d4-414">LASTDATE</span><span class="sxs-lookup"><span data-stu-id="375d4-414">LASTDATE</span></span>  
  
<span data-ttu-id="375d4-415">DATEADD</span><span class="sxs-lookup"><span data-stu-id="375d4-415">DATEADD</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="375d4-416">另請參閱</span><span class="sxs-lookup"><span data-stu-id="375d4-416">See also</span></span>  
[<span data-ttu-id="375d4-417">DirectQuery 模式 (SSAS 表格式)</span><span class="sxs-lookup"><span data-stu-id="375d4-417">DirectQuery Mode (SSAS Tabular)</span></span>](https://msdn.microsoft.com/45ad2965-05ec-4fb1-a164-d8060b562ea5)  
  

