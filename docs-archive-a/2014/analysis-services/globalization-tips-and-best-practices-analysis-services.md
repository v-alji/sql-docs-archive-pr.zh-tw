---
title: " (Analysis Services) 的全球化秘訣和最佳作法 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- translations [Analysis Services], client applications
- date comparisons
- day-of-week comparisons [Analysis Services]
- time [Analysis Services]
- month comparisons [Analysis Services]
ms.assetid: 71a8c438-1370-4c69-961e-d067ee4e47c2
author: minewiskan
ms.author: owend
ms.openlocfilehash: c5bf99878a08e3d2ca57b76e3f902fded2099381
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606481"
---
# <a name="globalization-tips-and-best-practices-analysis-services"></a><span data-ttu-id="a3c8c-102">全球化秘訣和最佳作法 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="a3c8c-102">Globalization Tips and Best Practices (Analysis Services)</span></span>
  <span data-ttu-id="a3c8c-103">**[!INCLUDE[applies](../includes/applies-md.md)]** 僅限多維度</span><span class="sxs-lookup"><span data-stu-id="a3c8c-103">**[!INCLUDE[applies](../includes/applies-md.md)]**  Multidimensional only</span></span>  
  
 <span data-ttu-id="a3c8c-104">下列秘訣和指導方針有助於提高商業智慧方案的可攜性，並避免發生與語言和定序設定直接相關的錯誤。</span><span class="sxs-lookup"><span data-stu-id="a3c8c-104">These tips and guidelines can help increase the portability of your business intelligence solutions and avoid errors that are directly related to language and collation settings.</span></span>  
  
-   [<span data-ttu-id="a3c8c-105">在整個堆疊中使用類似的定序</span><span class="sxs-lookup"><span data-stu-id="a3c8c-105">Use similar collations throughout the stack</span></span>](#bkmk_sameColl)  
  
-   [<span data-ttu-id="a3c8c-106">常見的定序建議</span><span class="sxs-lookup"><span data-stu-id="a3c8c-106">Common collation recommendations</span></span>](#bkmk_recos)  
  
-   [<span data-ttu-id="a3c8c-107">物件識別碼區分大小寫</span><span class="sxs-lookup"><span data-stu-id="a3c8c-107">Case sensitivity of object identifiers</span></span>](#bkmk_objid)  
  
-   [<span data-ttu-id="a3c8c-108">使用 Excel 和 SQL Server Profiler 測試地區設定</span><span class="sxs-lookup"><span data-stu-id="a3c8c-108">Locale testing using Excel and SQL Server Profiler</span></span>](#bkmk_test)  
  
-   [<span data-ttu-id="a3c8c-109">在包含翻譯的方案中撰寫 MDX 查詢</span><span class="sxs-lookup"><span data-stu-id="a3c8c-109">Writing MDX queries in a solution containing Translations</span></span>](#bkmk_mdx)  
  
-   [<span data-ttu-id="a3c8c-110">撰寫包含日期和時間值的 MDX 查詢</span><span class="sxs-lookup"><span data-stu-id="a3c8c-110">Writing MDX queries containing Date and Time Values</span></span>](#bkmk_datetime)  
  
##  <a name="use-similar-collations-throughout-the-stack"></a><a name="bkmk_sameColl"></a><span data-ttu-id="a3c8c-111">在整個堆疊中使用類似的定序</span><span class="sxs-lookup"><span data-stu-id="a3c8c-111">Use similar collations throughout the stack</span></span>  
 <span data-ttu-id="a3c8c-112">請盡可能嘗試在 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 中使用針對資料庫引擎所使用的相同定序設定，力求在區分全半形、大小寫和腔調字方面保持一致。</span><span class="sxs-lookup"><span data-stu-id="a3c8c-112">If possible, try to use the same collation settings in [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] that you use for the database engine, striving for correspondence in width-sensitivity and case-sensitivity, and access-sensitivity.</span></span>  
  
 <span data-ttu-id="a3c8c-113">每項服務都有自己的定序設定，其中資料庫引擎預設為 SQL_Latin1_General_CP1_CI_AS，而 Analysis Services 設為 Latin1_General_AS。</span><span class="sxs-lookup"><span data-stu-id="a3c8c-113">Each service has its own collation settings, with the database engine default set to SQL_Latin1_General_CP1_CI_AS and Analysis Services set to Latin1_General_AS.</span></span> <span data-ttu-id="a3c8c-114">這些預設值在區分大小寫、全半形和腔調字方面保持一致。</span><span class="sxs-lookup"><span data-stu-id="a3c8c-114">The defaults are compatible in term of case, width, and accent sensitivity.</span></span> <span data-ttu-id="a3c8c-115">請注意，如果您改變任何一個定序的設定，當定序屬性基本上有所分歧時，可能會發生問題。</span><span class="sxs-lookup"><span data-stu-id="a3c8c-115">Be forewarned that if you vary the settings of either collation, you can run into problems when the collation properties diverge in fundamental ways.</span></span>  
  
 <span data-ttu-id="a3c8c-116">即使定序設定的功能相同，您還是可能會遇到每項服務以不同方式解譯字串中任何位置之空格的特殊大小寫情況。</span><span class="sxs-lookup"><span data-stu-id="a3c8c-116">Even when collation settings are functionally equivalent, you can run into a special case where an empty space anywhere within a string is interpreted differently by each service.</span></span>  
  
 <span data-ttu-id="a3c8c-117">由於空格字元可以半形 (SBCS) 或全形 (DBCS) Unicode 字元集來表示，因此是「特殊大小寫」。</span><span class="sxs-lookup"><span data-stu-id="a3c8c-117">The space character is a 'special case' because it can be represented as a single-byte (SBCS) or double-byte character set (DBCS) in Unicode.</span></span> <span data-ttu-id="a3c8c-118">在關聯式引擎中，兩個以空格分隔的複合字串 (一個使用 SBCS，另一個使用 DBCS) 會視為相同。</span><span class="sxs-lookup"><span data-stu-id="a3c8c-118">In the relational engine, two compound strings separated by a space -- one using SBCS, the other in DBCS -- are considered identical.</span></span> <span data-ttu-id="a3c8c-119">在 Analysis Services 中，兩個相同的複合字串在處理期間並不相同，並且第二個執行個體會標示為重複項目。</span><span class="sxs-lookup"><span data-stu-id="a3c8c-119">In Analysis Services, during processing, the same two compound strings are not identical, and the second instance will be flagged as a duplicate.</span></span>  
  
 <span data-ttu-id="a3c8c-120">如需詳細資訊和建議的解決方法，請參閱 [Unicode 字串中的空格根據定序而有不同的處理結果](https://social.technet.microsoft.com/wiki/contents/articles/23979.ssas-processing-error-blanks-in-a-unicode-string-have-different-processing-outcomes-based-on-collation-and-character-set.aspx)。</span><span class="sxs-lookup"><span data-stu-id="a3c8c-120">For more details and suggested workarounds, see [Blanks in a Unicode string have different processing outcomes based on collation](https://social.technet.microsoft.com/wiki/contents/articles/23979.ssas-processing-error-blanks-in-a-unicode-string-have-different-processing-outcomes-based-on-collation-and-character-set.aspx).</span></span>  
  
##  <a name="common-collation-recommendations"></a><a name="bkmk_recos"></a> <span data-ttu-id="a3c8c-121">常見的定序建議</span><span class="sxs-lookup"><span data-stu-id="a3c8c-121">Common collation recommendations</span></span>  
 <span data-ttu-id="a3c8c-122">Analysis Services 一律會顯示所有可用語言和定序的完整清單，而不會依據您所選取的語言篩選定序。</span><span class="sxs-lookup"><span data-stu-id="a3c8c-122">Analysis Services always presents the full list of all available languages and collations; it does not filter the collations based on the language you selected.</span></span> <span data-ttu-id="a3c8c-123">請務必選擇可用的組合。</span><span class="sxs-lookup"><span data-stu-id="a3c8c-123">Be sure to choose a workable combination.</span></span>  
  
 <span data-ttu-id="a3c8c-124">某些較常用的定序包含下列清單中的定序。</span><span class="sxs-lookup"><span data-stu-id="a3c8c-124">Some of the more commonly used collations include those in the following list.</span></span>  
  
 <span data-ttu-id="a3c8c-125">您應該將這份清單視為進一步調查的起點，而不是排除其他選項的最終建議。</span><span class="sxs-lookup"><span data-stu-id="a3c8c-125">You should consider this list to be a starting point for further investigation, rather than a definitive recommendation that excludes other options.</span></span> <span data-ttu-id="a3c8c-126">您可能會發現未特別建議的定序是最適合您資料的定序。</span><span class="sxs-lookup"><span data-stu-id="a3c8c-126">You might find that a collation not specifically recommended is the one that works best for your data.</span></span> <span data-ttu-id="a3c8c-127">若要驗證資料值是否經過適當地排序和比較，唯一方式是進行徹底測試。</span><span class="sxs-lookup"><span data-stu-id="a3c8c-127">Thorough testing is the only way to verify whether data values are sorted and compared appropriately.</span></span> <span data-ttu-id="a3c8c-128">一如往常，請務必在測試定序時，同時執行處理和查詢工作負載。</span><span class="sxs-lookup"><span data-stu-id="a3c8c-128">As always, be sure to run both processing and query workloads when testing collation.</span></span>  
  
-   <span data-ttu-id="a3c8c-129">Latin1_General_100_AS 通常會用於使用 [ISO 基本拉丁字母](http://en.wikipedia.org/wiki/ISO_basic_Latin_alphabet)之 26 個字元的應用程式。</span><span class="sxs-lookup"><span data-stu-id="a3c8c-129">Latin1_General_100_AS is often used for applications that use the 26 characters of the [ISO basic Latin alphabet](http://en.wikipedia.org/wiki/ISO_basic_Latin_alphabet).</span></span>  
  
-   <span data-ttu-id="a3c8c-130">包含斯堪地那維亞字母 (例如 ø) 的北歐語言可以使用 Finnish_Swedish_100。</span><span class="sxs-lookup"><span data-stu-id="a3c8c-130">North European languages that include Scandinavian letters (such as ø) can use Finnish_Swedish_100.</span></span>  
  
-   <span data-ttu-id="a3c8c-131">東歐語言 (例如俄文) 通常會使用 Cyrillic_General_100。</span><span class="sxs-lookup"><span data-stu-id="a3c8c-131">East European languages, such as Russian, often use Cyrillic_General_100.</span></span>  
  
-   <span data-ttu-id="a3c8c-132">中文語言和定序因地區而異，但通常會是簡體中文或繁體中文。</span><span class="sxs-lookup"><span data-stu-id="a3c8c-132">Chinese language and collations vary by region, but are generally either Chinese Simplified or Chinese Traditional.</span></span>  
  
     <span data-ttu-id="a3c8c-133">在中國和新加坡，Microsoft 支援通常會以簡體中文顯示，並以拼音做為慣用的排序次序。</span><span class="sxs-lookup"><span data-stu-id="a3c8c-133">In PRC and Singapore, Microsoft Support tends to see Simplified Chinese, with Pinyin as the preferred sort order.</span></span> <span data-ttu-id="a3c8c-134">建議的定序為 Chinese_PRC (適用於 SQL Server 2000)、Chinese_PRC_90 (適用於 SQL Server 2005) 或 Chinese_Simplified_Pinyin_100 (適用於 SQL Server 2008 及更新版本)。</span><span class="sxs-lookup"><span data-stu-id="a3c8c-134">The recommended collations are Chinese_PRC (for SQL Server 2000), Chinese_PRC_90 (for SQL Server 2005) or Chinese_Simplified_Pinyin_100 (for SQL Server 2008 and later).</span></span>  
  
     <span data-ttu-id="a3c8c-135">在台灣，則較常看到繁體中文，且建議的排序次序是依據筆劃數：Chinese_Taiwan_Stroke (適用於 SQL Server 2000)、Chinese_Taiwan_Stroke_90 (適用於 SQL Server 2005) 或 Chinese_Traditional_Stroke_Count_100 (適用於 SQL Server 2008 及更新版本)。</span><span class="sxs-lookup"><span data-stu-id="a3c8c-135">In Taiwan, it is more common to see Traditional Chinese with the recommended sort order is based on Stroke Count: Chinese_Taiwan_Stroke (for SQL Server 2000), Chinese_Taiwan_Stroke_90 (for SQL Server 2005) or Chinese_Traditional_Stroke_Count_100 (for SQL Server 2008 and later).</span></span>  
  
     <span data-ttu-id="a3c8c-136">其他區域 (例如香港特別行政區和澳門特別行政區) 也會使用繁體中文。</span><span class="sxs-lookup"><span data-stu-id="a3c8c-136">Other regions (such as Hong Kong SAR and Macao SAR) also use Traditional Chinese.</span></span> <span data-ttu-id="a3c8c-137">在香港特別行政區，還很常會看到 Chinese_Hong_Kong_Stroke_90 (在 SQL Server 2005 上) 的定序。</span><span class="sxs-lookup"><span data-stu-id="a3c8c-137">For collations, in Hong Kong, it's not unusual to see Chinese_Hong_Kong_Stroke_90 (on SQL Server 2005).</span></span> <span data-ttu-id="a3c8c-138">在澳門特別行政區，SQL Server 2008 和更新) 版本的 Chinese_Traditional_Stroke_Count_100 (會相當頻繁地使用。</span><span class="sxs-lookup"><span data-stu-id="a3c8c-138">In Macao, Chinese_Traditional_Stroke_Count_100 (on SQL Server 2008 and later) is used fairly often.</span></span>  
  
-   <span data-ttu-id="a3c8c-139">日文的最常用定序是 Japanese_CI_AS。</span><span class="sxs-lookup"><span data-stu-id="a3c8c-139">For Japanese, the most commonly used collation is Japanese_CI_AS.</span></span> <span data-ttu-id="a3c8c-140">Japanese_XJIS_100 可用於支援 [JIS2004](http://en.wikipedia.org/wiki/JIS_X_0213)的安裝。</span><span class="sxs-lookup"><span data-stu-id="a3c8c-140">Japanese_XJIS_100 is used in installations supporting [JIS2004](http://en.wikipedia.org/wiki/JIS_X_0213).</span></span> <span data-ttu-id="a3c8c-141">在資料移轉專案中通常會看到 Japanese_BIN2，其資料源自於非 Windows 平台，或源自於 SQL Server 關聯式資料庫引擎以外的資料來源。</span><span class="sxs-lookup"><span data-stu-id="a3c8c-141">Japanese_BIN2 is typically seen in data migration projects, with data originating from non-Windows platforms, or from data sources other than the SQL Server relational database engine.</span></span>  
  
     <span data-ttu-id="a3c8c-142">在執行 Analysis Services 工作負載的伺服器上很少會看到 Japanese_Bushu_Kakusu_100。</span><span class="sxs-lookup"><span data-stu-id="a3c8c-142">Japanese_Bushu_Kakusu_100 is rarely seen in servers that run Analysis Services workloads.</span></span>  
  
-   <span data-ttu-id="a3c8c-143">建議針對韓文使用 Korean_100。</span><span class="sxs-lookup"><span data-stu-id="a3c8c-143">Korean_100 is recommended for Korean.</span></span> <span data-ttu-id="a3c8c-144">雖然 Korean_Wansung_Unicode 在清單中仍然可用，但是它已被取代。</span><span class="sxs-lookup"><span data-stu-id="a3c8c-144">Although Korean_Wansung_Unicode is still available in the list, it has been deprecated.</span></span>  
  
##  <a name="case-sensitivity-of-object-identifiers"></a><a name="bkmk_objid"></a> <span data-ttu-id="a3c8c-145">物件識別碼的區分大小寫</span><span class="sxs-lookup"><span data-stu-id="a3c8c-145">Case sensitivity of object identifiers</span></span>  
 <span data-ttu-id="a3c8c-146">自 SQL Server 2012 SP2 開始，會強制與定序分開執行物件識別碼的區分大小寫，但行為會視語言而異：</span><span class="sxs-lookup"><span data-stu-id="a3c8c-146">Starting in SQL Server 2012 SP2, case sensitivity of object IDs is enforced independently of the collation, but the behavior varies by language:</span></span>  
  
|<span data-ttu-id="a3c8c-147">字集</span><span class="sxs-lookup"><span data-stu-id="a3c8c-147">Language script</span></span>|<span data-ttu-id="a3c8c-148">區分大小寫</span><span class="sxs-lookup"><span data-stu-id="a3c8c-148">Case sensitivity</span></span>|  
|---------------------|----------------------|  
|<span data-ttu-id="a3c8c-149">**基本拉丁字母**</span><span class="sxs-lookup"><span data-stu-id="a3c8c-149">**Basic Latin alphabet**</span></span>|<span data-ttu-id="a3c8c-150">以拉丁文字 (26 個英文大小寫字母的任何幾個字母) 表示的物件識別碼會視為區分大小寫，而不論定序為何。</span><span class="sxs-lookup"><span data-stu-id="a3c8c-150">Object identifiers expressed in Latin script (any of the 26 English upper or lower case letters) are treated as case-insensitive, regardless of collation.</span></span> <span data-ttu-id="a3c8c-151">例如，下列物件識別碼會視為相同：54321**abcdef**、54321**ABCDEF**、54321**AbCdEf**。</span><span class="sxs-lookup"><span data-stu-id="a3c8c-151">For example, the following object IDs are considered identical: 54321**abcdef**, 54321**ABCDEF**, 54321**AbCdEf**.</span></span> <span data-ttu-id="a3c8c-152">Analysis Services 會在內部將字串中的字元視為全部大寫，然後執行與語言無關的簡單全半形比較。</span><span class="sxs-lookup"><span data-stu-id="a3c8c-152">Internally, Analysis Services treats the characters in the string as if all are uppercase, and then performs a simple byte comparison that is independent of language.</span></span><br /><br /> <span data-ttu-id="a3c8c-153">請注意，只有 26 個字元會受到影響。</span><span class="sxs-lookup"><span data-stu-id="a3c8c-153">Note that only the 26 characters are affected.</span></span> <span data-ttu-id="a3c8c-154">如果是西歐語言，但使用斯堪地那維亞字元，其他字元不會使用大寫。</span><span class="sxs-lookup"><span data-stu-id="a3c8c-154">If the language is West European, but uses Scandinavian characters, the additional character will not be upper-cased.</span></span>|  
|<span data-ttu-id="a3c8c-155">**斯拉夫文、希臘文、科普特文、亞美尼亞文**</span><span class="sxs-lookup"><span data-stu-id="a3c8c-155">**Cyrillic, Greek, Coptic, Armenian**</span></span>|<span data-ttu-id="a3c8c-156">非拉丁文複合字集的物件識別碼 (例如斯拉夫文) 則一律會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="a3c8c-156">Object identifiers in non-Latin bicameral script, such as Cyrillic, are always case-sensitive.</span></span> <span data-ttu-id="a3c8c-157">例如，Измерение 和 измерение 的唯一差異是第一個字母的大小寫，即便如此，這兩個字仍會視為兩個相異值。</span><span class="sxs-lookup"><span data-stu-id="a3c8c-157">For example, Измерение and измерение are considered two distinct values, even though the only difference is the case of the first letter.</span></span>|  
  
 <span data-ttu-id="a3c8c-158">**物件識別碼的區分大小寫含意**</span><span class="sxs-lookup"><span data-stu-id="a3c8c-158">**Implications of case-sensitivity for object identifiers**</span></span>  
  
 <span data-ttu-id="a3c8c-159">只有物件識別碼會受到表格中所述之大小寫行為的影響，物件名稱則不會受到影響。</span><span class="sxs-lookup"><span data-stu-id="a3c8c-159">Only object identifiers, and not object names, are subject to the casing behaviors described in the table.</span></span> <span data-ttu-id="a3c8c-160">如果您發現方案效果有所改變 (比較前和比較後 - 安裝SQL Server 2012 SP2 或更新版本之後)，很有可能是處理問題。</span><span class="sxs-lookup"><span data-stu-id="a3c8c-160">If you see a change in how your solution works (a before and after comparison -- after installing SQL Server 2012 SP2 or later), it will most likely be a processing issue.</span></span> <span data-ttu-id="a3c8c-161">查詢不會受到物件識別碼的影響。</span><span class="sxs-lookup"><span data-stu-id="a3c8c-161">Queries are not impacted by object identifiers.</span></span> <span data-ttu-id="a3c8c-162">針對這兩種查詢語言 (DAX 和 MDX)，公式引擎會使用物件名稱 (而不是識別碼)。</span><span class="sxs-lookup"><span data-stu-id="a3c8c-162">For both query languages (DAX and MDX), the formula engine uses the object name (not the identifier).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a3c8c-163">與區分大小寫相關的程式碼變更對於某些應用程式而言向來是個中斷變更。</span><span class="sxs-lookup"><span data-stu-id="a3c8c-163">Code changes related to case-sensitivity have been a breaking change for some applications.</span></span> <span data-ttu-id="a3c8c-164">如需詳細資訊，請參閱[SQL Server 2014 中 Analysis Services 功能的重大變更](breaking-changes-to-analysis-services-features-in-sql-server-2014.md)。</span><span class="sxs-lookup"><span data-stu-id="a3c8c-164">See [Breaking Changes to Analysis Services Features in SQL Server 2014](breaking-changes-to-analysis-services-features-in-sql-server-2014.md) for more information.</span></span>  
  
##  <a name="locale-testing-using-excel-sql-server-profiler-and-sql-server-management-studio"></a><a name="bkmk_test"></a> <span data-ttu-id="a3c8c-165">使用 Excel、SQL Server Profiler 和 SQL Server Management Studio 測試地區設定</span><span class="sxs-lookup"><span data-stu-id="a3c8c-165">Locale testing using Excel, SQL Server Profiler and SQL Server Management Studio</span></span>  
 <span data-ttu-id="a3c8c-166">測試翻譯時，連接必須指定翻譯的 LCID。</span><span class="sxs-lookup"><span data-stu-id="a3c8c-166">When testing translations, the connection must specify the LCID of the translation.</span></span> <span data-ttu-id="a3c8c-167">如 [從 SSAS 取得不同的語言並加入 Excel](http://extremeexperts.com/sql/Tips/ExcelDiffLocale.aspx)中所述，您可以使用 Excel 來測試翻譯。</span><span class="sxs-lookup"><span data-stu-id="a3c8c-167">As documented in [Get Different Language from SSAS into Excel](http://extremeexperts.com/sql/Tips/ExcelDiffLocale.aspx), you can use Excel to test your translations.</span></span>  
  
 <span data-ttu-id="a3c8c-168">您可以手動編輯 .odc 檔案加入地區設定識別碼連接字串屬性，來執行這項操作。</span><span class="sxs-lookup"><span data-stu-id="a3c8c-168">You can do this by hand editing the .odc file to include the locale identifier connection string property.</span></span> <span data-ttu-id="a3c8c-169">請使用 Adventure Works 範例多維度資料庫來試試看。</span><span class="sxs-lookup"><span data-stu-id="a3c8c-169">Try this out with the Adventure Works sample multidimensional database.</span></span>  
  
-   <span data-ttu-id="a3c8c-170">搜尋現有的 .odc 檔案。</span><span class="sxs-lookup"><span data-stu-id="a3c8c-170">Search for existing .odc files.</span></span> <span data-ttu-id="a3c8c-171">當您找到 Adventure works 多維度的檔案時，請以滑鼠右鍵按一下檔案，在 [記事本] 中開啟檔案。</span><span class="sxs-lookup"><span data-stu-id="a3c8c-171">When you find the one for Adventure Works multidimensional, right-click the file to open it in Notepad.</span></span>  
  
-   <span data-ttu-id="a3c8c-172">將 `Locale Identifier=1036` 新增至連接字串。</span><span class="sxs-lookup"><span data-stu-id="a3c8c-172">Add `Locale Identifier=1036` to the connection string.</span></span> <span data-ttu-id="a3c8c-173">儲存並關閉檔案。</span><span class="sxs-lookup"><span data-stu-id="a3c8c-173">Save and close the file.</span></span>  
  
-   <span data-ttu-id="a3c8c-174">開啟 Excel |**資料**  | **現有的連接**。</span><span class="sxs-lookup"><span data-stu-id="a3c8c-174">Open Excel | **Data** | **Existing Connections**.</span></span> <span data-ttu-id="a3c8c-175">將清單篩選到只剩下這部電腦上的連接檔案。</span><span class="sxs-lookup"><span data-stu-id="a3c8c-175">Filter the list to just connections files on this computer.</span></span> <span data-ttu-id="a3c8c-176">尋找 Adventure Works 的連接 (請仔細查看名稱；您可能會有一個以上的連接)。</span><span class="sxs-lookup"><span data-stu-id="a3c8c-176">Find the connection for Adventure Works (look at the name carefully; you might have more than one).</span></span> <span data-ttu-id="a3c8c-177">開啟連線。</span><span class="sxs-lookup"><span data-stu-id="a3c8c-177">Open the connection.</span></span>  
  
     <span data-ttu-id="a3c8c-178">您應該會看到 Adventure Works 範例資料庫中的法文翻譯。</span><span class="sxs-lookup"><span data-stu-id="a3c8c-178">You should see the French translations from the Adventure Works sample database.</span></span>  
  
     <span data-ttu-id="a3c8c-179">![使用法文翻譯的 Excel 樞紐分析表](media/ssas-localetest-excel.png "使用法文翻譯的 Excel 樞紐分析表")</span><span class="sxs-lookup"><span data-stu-id="a3c8c-179">![Excel PivotTable with French translations](media/ssas-localetest-excel.png "Excel PivotTable with French translations")</span></span>  
  
 <span data-ttu-id="a3c8c-180">接著，您可以使用 SQL Server Profiler 來確認地區設定。</span><span class="sxs-lookup"><span data-stu-id="a3c8c-180">As a follow up, you can use SQL Server Profiler to confirm the locale.</span></span> <span data-ttu-id="a3c8c-181">按一下 `Session Initialize` 事件，然後查看下方文字區域中的屬性清單，尋找 `<localeidentifier>1036</localeidentifier>`。</span><span class="sxs-lookup"><span data-stu-id="a3c8c-181">Click a `Session Initialize` event and then look at the property list in the text area below to find `<localeidentifier>1036</localeidentifier>`.</span></span>  
  
 <span data-ttu-id="a3c8c-182">在 Management Studio 中，您可以指定伺服器連接的地區設定識別碼。</span><span class="sxs-lookup"><span data-stu-id="a3c8c-182">In Management Studio, you can specify Locale Identifier on a server connection.</span></span>  
  
-   <span data-ttu-id="a3c8c-183">在物件總管 |**連接**  | **Analysis Services**  | **選項**中，按一下 [**其他連接參數**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="a3c8c-183">In Object Explorer | **Connect** | **Analysis Services** | **Options**, click the **Additional Connection Parameters** tab.</span></span>  
  
-   <span data-ttu-id="a3c8c-184">輸入 `Local Identifier=1036` ，然後按一下 [連接] \*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="a3c8c-184">Enter `Local Identifier=1036` and then click **Connect**.</span></span>  
  
-   <span data-ttu-id="a3c8c-185">對 Adventure Works 資料庫執行 MDX 查詢。</span><span class="sxs-lookup"><span data-stu-id="a3c8c-185">Execute an MDX query against the Adventure Works database.</span></span> <span data-ttu-id="a3c8c-186">查詢結果應該是法文翻譯。</span><span class="sxs-lookup"><span data-stu-id="a3c8c-186">The query results should be the French translations.</span></span>  
  
     <span data-ttu-id="a3c8c-187">![SSMS 中使用法文翻譯的 MDX 查詢](media/ssas-localetest-ssms.png "SSMS 中使用法文翻譯的 MDX 查詢")</span><span class="sxs-lookup"><span data-stu-id="a3c8c-187">![MDX query with French translations in SSMS](media/ssas-localetest-ssms.png "MDX query with French translations in SSMS")</span></span>  
  
##  <a name="writing-mdx-queries-in-a-solution-containing-translations"></a><a name="bkmk_mdx"></a> <span data-ttu-id="a3c8c-188">在包含翻譯的方案中撰寫 MDX 查詢</span><span class="sxs-lookup"><span data-stu-id="a3c8c-188">Writing MDX queries in a solution containing Translations</span></span>  
 <span data-ttu-id="a3c8c-189">翻譯會提供 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 物件名稱的顯示資訊，但不會翻譯相同物件的識別碼。</span><span class="sxs-lookup"><span data-stu-id="a3c8c-189">Translations provide display information for the names of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] objects, but the identifiers for the same objects are not translated.</span></span> <span data-ttu-id="a3c8c-190">可能的話，請使用 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 物件的識別碼和索引鍵，而不要使用翻譯的標題和名稱。</span><span class="sxs-lookup"><span data-stu-id="a3c8c-190">Whenever possible, use the identifiers and keys for [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] objects instead of the translated captions and names.</span></span> <span data-ttu-id="a3c8c-191">例如，針對多維度運算式 (MDX) 陳述式和指令碼，請使用成員索引鍵而不要使用成員名稱，以確保多種語言的可攜性。</span><span class="sxs-lookup"><span data-stu-id="a3c8c-191">For example, use member keys instead of member names for Multidimensional Expressions (MDX) statements and scripts to ensure portability across multiple languages.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a3c8c-192">您應該記得，不論定序為何，表格式物件名稱一律不會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="a3c8c-192">Recall that tabular object names are always case-insensitive, regardless of collation.</span></span> <span data-ttu-id="a3c8c-193">相反地，多維度物件名稱會遵循定序的區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="a3c8c-193">Multidimensional object names, on the other hand, follow the case sensitivity of the collation.</span></span> <span data-ttu-id="a3c8c-194">由於只有多維度物件名稱會區分大小寫，因此請確定參考多維度物件之所有 MDX 查詢的大小寫都正確。</span><span class="sxs-lookup"><span data-stu-id="a3c8c-194">Since only multidimensional object names are case-sensitive make sure that all MDX queries referencing multidimensional objects are cased correctly.</span></span>  
  
##  <a name="writing-mdx-queries-containing-date-and-time-values"></a><a name="bkmk_datetime"></a> <span data-ttu-id="a3c8c-195">撰寫包含日期和時間值的 MDX 查詢</span><span class="sxs-lookup"><span data-stu-id="a3c8c-195">Writing MDX queries containing Date and Time Values</span></span>  
 <span data-ttu-id="a3c8c-196">下列建議可讓以日期和時間為基礎的 MDX 查詢在不同語言之間的可攜性更高：</span><span class="sxs-lookup"><span data-stu-id="a3c8c-196">The following suggestions to make your date and time-based MDX queries more portable across different languages:</span></span>  
  
1.  <span data-ttu-id="a3c8c-197">**使用數值部分進行比較和運算**</span><span class="sxs-lookup"><span data-stu-id="a3c8c-197">**Use numeric parts for comparisons and operations**</span></span>  
  
     <span data-ttu-id="a3c8c-198">當您執行月和週中的日比較和運算時，請使用日期和時間的數值部分，而不是對等字串 (例如使用 MonthNumberofYear 而不是 MonthName)。</span><span class="sxs-lookup"><span data-stu-id="a3c8c-198">When you perform month and day-of-week comparisons and operations, use the numeric date and time parts instead of the string equivalents (for example, use MonthNumberofYear instead of MonthName).</span></span> <span data-ttu-id="a3c8c-199">數值最不會受到語言翻譯差異的影響。</span><span class="sxs-lookup"><span data-stu-id="a3c8c-199">Numeric values are least affected by differences in language translations.</span></span>  
  
2.  <span data-ttu-id="a3c8c-200">**在結果集中使用對等字串**</span><span class="sxs-lookup"><span data-stu-id="a3c8c-200">**Use string equivalents in a result set**</span></span>  
  
     <span data-ttu-id="a3c8c-201">當建立向使用者顯示的結果集時，請考慮使用字串 (例如 MonthName)，如此一來您的多語系觀眾便可受益於您所提供的翻譯。</span><span class="sxs-lookup"><span data-stu-id="a3c8c-201">When building result sets seen by end-users, consider using the string (such as MonthName) so that your multi-lingual audience can benefit from the translations you've provided.</span></span>  
  
3.  <span data-ttu-id="a3c8c-202">**針對通用的日期和時間資訊使用 ISO 日期格式**</span><span class="sxs-lookup"><span data-stu-id="a3c8c-202">**Use ISO date formats for universal date and time information**</span></span>  
  
     <span data-ttu-id="a3c8c-203">某位 [Analysis Services 專家](http://geekswithblogs.net/darrengosbell/Default.aspx) 有這項建議：「針對要傳入 SQL 或 MDX 查詢的任何日期字串，我一律會使用 ISO 日期格式 yyyy-mm-dd，這樣做不僅可避免模擬兩可，且不論用戶端或伺服器的地區設定為何都有效。</span><span class="sxs-lookup"><span data-stu-id="a3c8c-203">One [Analysis Services expert](http://geekswithblogs.net/darrengosbell/Default.aspx) has this recommendation: "I always use the ISO date format yyyy-mm-dd for any date strings that I pass in to queries in SQL or MDX because it's unambiguous and will work regardless of the client or server's regional settings.</span></span> <span data-ttu-id="a3c8c-204">我同意當剖析模稜兩可的日期格式時，伺服器應該遵循其地區設定，但我也認為如果您已有一個不開放轉譯的選項時，何不選擇這個選項。」</span><span class="sxs-lookup"><span data-stu-id="a3c8c-204">I would agree that the server should defer to its regional settings when parsing an ambiguous date format, but I also think that if you've got an option that is not open to interpretation that you are better choosing that anyway".</span></span>  
  
4.  `Use the Format function to enforce a specific format, regardless of regional language settings`  
  
     <span data-ttu-id="a3c8c-205">下列取自論壇文章的 MDX 查詢說明如何使用 [格式]，來傳回特定格式的日期，而不論基礎地區設定為何。</span><span class="sxs-lookup"><span data-stu-id="a3c8c-205">The following MDX query, borrowed from a forum post, illustrates how to use Format to return dates in a specific format, irrespective of the underlying regional settings.</span></span>  
  
     <span data-ttu-id="a3c8c-206">請參閱 [SSAS 2012 generates invalid dates (forum post on Network Steve](http://www.networksteve.com/forum/topic.php/SSAS_2012_generates_invalid_dates/?TopicId=40504&Posts=2) (SSAS 2012 產生無效的日期 (Network Steve 上的論壇文章) 的原始文章。</span><span class="sxs-lookup"><span data-stu-id="a3c8c-206">See [SSAS 2012 generates invalid dates (forum post on Network Steve](http://www.networksteve.com/forum/topic.php/SSAS_2012_generates_invalid_dates/?TopicId=40504&Posts=2) for the original post.</span></span>  
  
    ```  
    WITH MEMBER [LinkTimeAdd11Date_Manual] as Format(dateadd("d",15,"2014-12-11"), "mm/dd/yyyy")  
    member [LinkTimeAdd15Date_Manual] as Format(dateadd("d",11,"2014-12-13"), "mm/dd/yyyy")  
    SELECT  
    { [LinkTimeAdd11Date_Manual]  
    ,[LinkTimeAdd15Date_Manual]  
    }  
    ON COLUMNS   
    FROM [Adventure Works]  
  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="a3c8c-207">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a3c8c-207">See Also</span></span>  
 <span data-ttu-id="a3c8c-208">[Analysis Services 多維度的全球化案例](globalization-scenarios-for-analysis-services-multiidimensional.md) </span><span class="sxs-lookup"><span data-stu-id="a3c8c-208">[Globalization scenarios for Analysis Services Multidimensional](globalization-scenarios-for-analysis-services-multiidimensional.md) </span></span>  
 [<span data-ttu-id="a3c8c-209">撰寫國際通用的 Transact-SQL 陳述式</span><span class="sxs-lookup"><span data-stu-id="a3c8c-209">Write International Transact-SQL Statements</span></span>](../relational-databases/collations/write-international-transact-sql-statements.md)  
