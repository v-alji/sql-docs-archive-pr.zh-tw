---
title: 輸入搜尋值的規則 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- time [SQL Server], searches
- date searches
- dates [SQL Server], searches
- embedding apostrophes [SQL Server]
- logical value searches [SQL Server]
- case-sensitive search matches
- search criteria [SQL Server], rules
- text value searches [SQL Server]
- numeric value searches [SQL Server]
ms.assetid: 3c8134b7-83f4-41b4-99c8-e3949a685ff5
author: stevestein
ms.author: sstein
ms.openlocfilehash: 907bcac93863bc5660993e910b37e25e25a129b4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585744"
---
# <a name="rules-for-entering-search-values-visual-database-tools"></a><span data-ttu-id="17d9e-102">輸入搜尋值的規則 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="17d9e-102">Rules for Entering Search Values (Visual Database Tools)</span></span>
  <span data-ttu-id="17d9e-103">本主題會討論輸入下列搜尋條件的常值類型時必須使用的規格：</span><span class="sxs-lookup"><span data-stu-id="17d9e-103">This topic discusses the conventions you must use when entering the following types of literal values for a search condition:</span></span>  
  
-   <span data-ttu-id="17d9e-104">文字值</span><span class="sxs-lookup"><span data-stu-id="17d9e-104">Text values</span></span>  
  
-   <span data-ttu-id="17d9e-105">數字值</span><span class="sxs-lookup"><span data-stu-id="17d9e-105">Numeric values</span></span>  
  
-   <span data-ttu-id="17d9e-106">日期</span><span class="sxs-lookup"><span data-stu-id="17d9e-106">Dates</span></span>  
  
-   <span data-ttu-id="17d9e-107">邏輯值</span><span class="sxs-lookup"><span data-stu-id="17d9e-107">Logical values</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="17d9e-108">本主題中的資訊衍生自標準 SQL-92 的規則。</span><span class="sxs-lookup"><span data-stu-id="17d9e-108">The information in this topic is derived from the rules for standard SQL-92.</span></span> <span data-ttu-id="17d9e-109">不過，每一個資料庫都可以用自己的方式實作 SQL。</span><span class="sxs-lookup"><span data-stu-id="17d9e-109">However, each database can implement SQL in its own way.</span></span> <span data-ttu-id="17d9e-110">因此，這裡提供的準則不一定適用於所有的情況。</span><span class="sxs-lookup"><span data-stu-id="17d9e-110">Therefore, the guidelines provided here might not apply in every case.</span></span> <span data-ttu-id="17d9e-111">如果對於在特定資料庫輸入搜尋值有任何的疑問，請參考您所使用的資料庫文件。</span><span class="sxs-lookup"><span data-stu-id="17d9e-111">If you have questions about how to enter search values for a particular database, refer to the documentation for the database that you are using.</span></span>  
  
## <a name="searching-on-text-values"></a><span data-ttu-id="17d9e-112">搜尋文字值</span><span class="sxs-lookup"><span data-stu-id="17d9e-112">Searching on Text Values</span></span>  
 <span data-ttu-id="17d9e-113">下列準則適用於在搜尋條件中輸入文字值時：</span><span class="sxs-lookup"><span data-stu-id="17d9e-113">The following guidelines apply when you enter text values in search conditions:</span></span>  
  
-   <span data-ttu-id="17d9e-114">**引號** ：以單引號括住文字值，例如以下的姓氏範例：</span><span class="sxs-lookup"><span data-stu-id="17d9e-114">**Quotation marks** Enclose text values in single quotation marks, as in this example for a last name:</span></span>  
  
    ```  
    'Smith'  
    ```  
  
     <span data-ttu-id="17d9e-115">如果您是在 [準則窗格](visual-database-tools.md)中輸入搜尋條件，則可以只輸入文字值，查詢和檢視表設計工具會自動在前後加上單引號。</span><span class="sxs-lookup"><span data-stu-id="17d9e-115">If you are entering a search condition in the [Criteria Pane](visual-database-tools.md), you can simply type the text value and the Query and View Designer will automatically put single quotation marks around it.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="17d9e-116">在某些資料庫中，單引號中的詞會被視為常值，而雙引號中的詞會被視為資料行或資料表參考之類的資料庫物件。</span><span class="sxs-lookup"><span data-stu-id="17d9e-116">In some databases, terms in single quotation marks are interpreted as literal values, whereas terms in double quotation marks are interpreted as database objects such as column or table references.</span></span> <span data-ttu-id="17d9e-117">因此，即使 [查詢和檢視設計師] 可以接受以雙引號括住的詞，其解譯的結果可能會和您的預期不同。</span><span class="sxs-lookup"><span data-stu-id="17d9e-117">Therefore, even though the Query and View Designer can accept terms in double quotation marks, it might interpret them differently than you expect.</span></span>  
  
-   <span data-ttu-id="17d9e-118">**嵌入單引號** ：如果您要搜尋的資料包含單引號 (')，您可以輸入兩個單引號以表示您輸入的確實是單引號的常值，不是分隔符號。</span><span class="sxs-lookup"><span data-stu-id="17d9e-118">**Embedding apostrophes** If the data you are searching for contains a single quotation mark (an apostrophe), you can enter two single quotation marks to indicate that you mean the single quotation mark as a literal value and not a delimiter.</span></span> <span data-ttu-id="17d9e-119">例如，以下條件會搜尋「Swann's Way」這個值：</span><span class="sxs-lookup"><span data-stu-id="17d9e-119">For example, the following condition searches for the value "Swann's Way:"</span></span>  
  
    ```  
    ='Swann''s Way'  
    ```  
  
-   <span data-ttu-id="17d9e-120">**長度限制** ：輸入長字串時，不要超過您資料庫 SQL 陳述式的最大長度。</span><span class="sxs-lookup"><span data-stu-id="17d9e-120">**Length limits** Do not exceed the maximum length of the SQL statement for your database when entering long strings.</span></span>  
  
-   <span data-ttu-id="17d9e-121">**區分大小寫** ：遵照您使用的資料庫的區分大小寫規則。</span><span class="sxs-lookup"><span data-stu-id="17d9e-121">**Case sensitivity** Follow the case sensitivity rules for the database you are using.</span></span> <span data-ttu-id="17d9e-122">您使用的資料庫決定了文字搜尋是否區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="17d9e-122">The database you are using determines whether text searches are case sensitive.</span></span> <span data-ttu-id="17d9e-123">例如，有些資料庫將運算子「=」解譯為大小寫完全相符，但是有些資料庫則允許任何大小寫字元組合都相符。</span><span class="sxs-lookup"><span data-stu-id="17d9e-123">For example, some databases interpret the operator "=" to mean an exact case-sensitive match, but others will allow matches on any combination of uppercase and lowercase characters.</span></span>  
  
     <span data-ttu-id="17d9e-124">如果您不確定資料庫是否使用區分大小寫搜尋，可以在搜尋條件中使用 UPPER 或 LOWER 函數轉換搜尋資料的大小寫，如以下範例所示：</span><span class="sxs-lookup"><span data-stu-id="17d9e-124">If you are unsure about whether the database uses a case-sensitive search, you can use the UPPER or LOWER functions in the search condition to convert the case of the search data, as illustrated in the following example:</span></span>  
  
    ```  
    WHERE UPPER(lname) = 'SMITH'  
    ```  
  
## <a name="searching-on-numeric-values"></a><span data-ttu-id="17d9e-125">搜尋數字值</span><span class="sxs-lookup"><span data-stu-id="17d9e-125">Searching on Numeric Values</span></span>  
 <span data-ttu-id="17d9e-126">下列準則適用於在搜尋條件中輸入數字值時：</span><span class="sxs-lookup"><span data-stu-id="17d9e-126">The following guidelines apply when you enter numeric values in search conditions:</span></span>  
  
-   <span data-ttu-id="17d9e-127">**引號**：不要用引號括住數字。</span><span class="sxs-lookup"><span data-stu-id="17d9e-127">**Quotation marks** Do not enclose numbers in quotation marks.</span></span>  
  
-   <span data-ttu-id="17d9e-128">**非數字字元**：除了小數分隔符號 (在 Windows [控制台] 的 [地區設定]  對話方塊中所定義) 和負號 (-) 以外，不要包含非數字字元。</span><span class="sxs-lookup"><span data-stu-id="17d9e-128">**Non-numeric characters** Do not include non-numeric characters except the decimal separator (as defined in the **Regional Settings** dialog box of Windows Control Panel) and negative sign (-).</span></span> <span data-ttu-id="17d9e-129">不要包含數字分位符號 (例如千位用逗號分開) 或貨幣符號。</span><span class="sxs-lookup"><span data-stu-id="17d9e-129">Do not include digit grouping symbols (such as a comma between thousands) or currency symbols.</span></span>  
  
-   <span data-ttu-id="17d9e-130">**小數符號** ：如果是輸入整數，可以包含小數符號，不論您搜尋的值是整數或實數。</span><span class="sxs-lookup"><span data-stu-id="17d9e-130">**Decimal marks** If you are entering whole numbers, you can include a decimal mark, whether the value you are searching for is an integer or a real number.</span></span>  
  
-   <span data-ttu-id="17d9e-131">**科學記號** ：可以使用科學記號輸入非常大或非常小的數字，如以下例子所示：</span><span class="sxs-lookup"><span data-stu-id="17d9e-131">**Scientific notation** You can enter very large or very small numbers using scientific notation, as in this example:</span></span>  
  
    ```  
    > 1.23456e-9  
    ```  
  
## <a name="searching-on-dates"></a><span data-ttu-id="17d9e-132">搜尋日期</span><span class="sxs-lookup"><span data-stu-id="17d9e-132">Searching on Dates</span></span>  
 <span data-ttu-id="17d9e-133">用來輸入日期的格式是依您使用的資料庫和 [查詢和檢視設計師] 中是在哪個窗格輸入日期而定。</span><span class="sxs-lookup"><span data-stu-id="17d9e-133">The format you use to enter dates depends on the database you are using and in what pane of the Query and View Designer you are entering the date.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="17d9e-134">如果您不知道資料來源所用的格式為何，請在 [準則] 窗格的篩選條件資料行中，以任何您熟悉的格式輸入日期。</span><span class="sxs-lookup"><span data-stu-id="17d9e-134">If you don't know which format your data source uses, type a date into the filter column of the Criteria pane in any format familiar to you.</span></span> <span data-ttu-id="17d9e-135">設計工具會將大部份這類的輸入項目轉換成適當格式。</span><span class="sxs-lookup"><span data-stu-id="17d9e-135">The designer will convert most of such entries into the appropriate format.</span></span>  
  
 <span data-ttu-id="17d9e-136">[查詢和檢視設計師] 可以使用下列的日期格式：</span><span class="sxs-lookup"><span data-stu-id="17d9e-136">The Query and View Designer can work with the following date formats:</span></span>  
  
-   <span data-ttu-id="17d9e-137">**地區設定特性** (Locale-Specific)：在 [Windows 區域設定內容]  對話方塊中指定的日期格式。</span><span class="sxs-lookup"><span data-stu-id="17d9e-137">**Locale-specific** The format specified for dates in the **Windows Regional Settings Properties** dialog box.</span></span>  
  
-   <span data-ttu-id="17d9e-138">**資料庫特性**：資料庫能夠辨識的任何格式。</span><span class="sxs-lookup"><span data-stu-id="17d9e-138">**Database-specific** Any format understood by the database.</span></span>  
  
-   <span data-ttu-id="17d9e-139">**ANSI 標準日期** ：使用括號、標記「d」來指定日期和日期字串的格式，如以下例子所示：</span><span class="sxs-lookup"><span data-stu-id="17d9e-139">**ANSI standard date** A format that uses braces, the marker 'd' to designate the date, and a date string, as in the following example:</span></span>  
  
    ```  
    { d '1990-12-31' }  
    ```  
  
-   <span data-ttu-id="17d9e-140">**ANSI 標準日期時間** ：類似於 ANSI 標準日期，但是不用「d」，改用「ts」，並且在日期中加入時、分及秒 (使用 24 小時格式的時鐘)，例如以下例子的 1990 年 12 月 31 日：</span><span class="sxs-lookup"><span data-stu-id="17d9e-140">**ANSI standard datetime** Similar to ANSI-standard date, but uses 'ts' instead of 'd' and adds hours, minutes, and seconds to the date (using a 24-hour clock), as in this example for December 31, 1990:</span></span>  
  
    ```  
    { ts '1990-12-31 00:00:00' }  
    ```  
  
     <span data-ttu-id="17d9e-141">ANSI 標準日期格式通常是用於以真實日期資料類型代表日期的資料庫。</span><span class="sxs-lookup"><span data-stu-id="17d9e-141">In general, the ANSI standard date format is used with databases that represent dates using a true date data type.</span></span> <span data-ttu-id="17d9e-142">相較之下，日期時間格式則是用於支援日期時間資料類型的資料庫。</span><span class="sxs-lookup"><span data-stu-id="17d9e-142">In contrast, the datetime format is used with databases that support a datetime data type.</span></span>  
  
 <span data-ttu-id="17d9e-143">下表摘要了可以在 [查詢和檢視設計師] 不同窗格中使用的各種日期格式。</span><span class="sxs-lookup"><span data-stu-id="17d9e-143">The following table summarizes the date format that you can use in different panes of the Query and View Designer.</span></span>  
  
|<span data-ttu-id="17d9e-144">**窗格**</span><span class="sxs-lookup"><span data-stu-id="17d9e-144">**Pane**</span></span>|<span data-ttu-id="17d9e-145">**日期格式**</span><span class="sxs-lookup"><span data-stu-id="17d9e-145">**Date format**</span></span>|  
|--------------|---------------------|  
|<span data-ttu-id="17d9e-146">準則</span><span class="sxs-lookup"><span data-stu-id="17d9e-146">Criteria</span></span>|<span data-ttu-id="17d9e-147">地區設定特性 資料庫特性 ANSI 標準</span><span class="sxs-lookup"><span data-stu-id="17d9e-147">Locale-specific Database-specific ANSI standard</span></span><br /><br /> <span data-ttu-id="17d9e-148">在 [準則窗格](visual-database-tools.md) 中輸入的日期，會在 SQL 窗格中轉換為與資料庫相容的格式。</span><span class="sxs-lookup"><span data-stu-id="17d9e-148">Dates entered in the [Criteria Pane](visual-database-tools.md) are converted to a database-compatible format in the SQL pane.</span></span>|  
|<span data-ttu-id="17d9e-149">SQL</span><span class="sxs-lookup"><span data-stu-id="17d9e-149">SQL</span></span>|<span data-ttu-id="17d9e-150">資料庫特性 ANSI 標準</span><span class="sxs-lookup"><span data-stu-id="17d9e-150">Database-specific ANSI standard</span></span>|  
|<span data-ttu-id="17d9e-151">結果</span><span class="sxs-lookup"><span data-stu-id="17d9e-151">Results</span></span>|<span data-ttu-id="17d9e-152">地區設定特性</span><span class="sxs-lookup"><span data-stu-id="17d9e-152">Locale-specific</span></span>|  
  
## <a name="searching-on-logical-values"></a><span data-ttu-id="17d9e-153">搜尋邏輯值</span><span class="sxs-lookup"><span data-stu-id="17d9e-153">Searching on Logical Values</span></span>  
 <span data-ttu-id="17d9e-154">每一種資料庫的邏輯資料格式不同。</span><span class="sxs-lookup"><span data-stu-id="17d9e-154">The format of logical data varies from database to database.</span></span> <span data-ttu-id="17d9e-155">False 值常常會儲存為零 (0)。</span><span class="sxs-lookup"><span data-stu-id="17d9e-155">Very frequently, a value of False is stored as zero (0).</span></span> <span data-ttu-id="17d9e-156">True 值最常儲存為 1，偶爾會儲存為 -1。</span><span class="sxs-lookup"><span data-stu-id="17d9e-156">A value of True is most frequently stored as 1 and occasionally as -1.</span></span> <span data-ttu-id="17d9e-157">下列準則適用於在搜尋條件中輸入邏輯值時：</span><span class="sxs-lookup"><span data-stu-id="17d9e-157">The following guidelines apply when you enter logical values in search conditions:</span></span>  
  
-   <span data-ttu-id="17d9e-158">若要使用零搜尋 False 值，如以下例子所示：</span><span class="sxs-lookup"><span data-stu-id="17d9e-158">To search for a value of False, use a zero, as in the following example:</span></span>  
  
    ```  
    SELECT * FROM authors  
    WHERE contract = 0  
    ```  
  
-   <span data-ttu-id="17d9e-159">搜尋 True 值時如果不確定該使用什麼格式，可以像下面例子一樣用 1 試試看：</span><span class="sxs-lookup"><span data-stu-id="17d9e-159">If you are not sure what format to use when searching for a True value, try using 1, as in the following example:</span></span>  
  
    ```  
    SELECT * FROM authors  
    WHERE contract = 1  
    ```  
  
-   <span data-ttu-id="17d9e-160">或者可以搜尋任何非零值以擴大搜尋範圍，如以下例子所示：</span><span class="sxs-lookup"><span data-stu-id="17d9e-160">Alternatively, you can broaden the scope of the search by searching for any non-zero value, as in the following example:</span></span>  
  
    ```  
    SELECT * FROM authors  
    WHERE contract <> 0  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="17d9e-161">另請參閱</span><span class="sxs-lookup"><span data-stu-id="17d9e-161">See Also</span></span>  
 [<span data-ttu-id="17d9e-162">指定搜尋準則 &#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="17d9e-162">Specify Search Criteria &#40;Visual Database Tools&#41;</span></span>](specify-search-criteria-visual-database-tools.md)  
  
  
