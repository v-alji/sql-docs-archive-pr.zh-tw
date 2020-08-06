---
title: 撰寫國際通用的 Transact-SQL 陳述式 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- writing international statements
- Transact-SQL international considerations
- international considerations [SQL Server], Transact-SQL
- Database Engine international considerations [SQL Server], Transact-SQL
- statements [SQL Server], international
- database international considerations [SQL Server], Transact-SQL
- dates [SQL Server], international considerations
ms.assetid: f0b10fee-27f7-45fe-aece-ccc3f63bdcdb
author: stevestein
ms.author: sstein
ms.openlocfilehash: 1888d1045e43e0a9839fd76a21c51500af63539a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606890"
---
# <a name="write-international-transact-sql-statements"></a><span data-ttu-id="70fe9-102">撰寫國際通用的 Transact-SQL 陳述式</span><span class="sxs-lookup"><span data-stu-id="70fe9-102">Write International Transact-SQL Statements</span></span>
  <span data-ttu-id="70fe9-103">如果遵循下列的指導方針，使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式的資料庫與資料庫應用程式將更能從一個語言移植至另一個語言，或可支援多種語言：</span><span class="sxs-lookup"><span data-stu-id="70fe9-103">Databases and database applications that use [!INCLUDE[tsql](../../includes/tsql-md.md)] statements will become more portable from one language to another, or will support multiple languages, if the following guidelines are followed:</span></span>  
  
-   <span data-ttu-id="70fe9-104">將所有使用 `char`、`varchar` 和 `text` 資料類型的地方換成 `nchar`、`nvarchar` 和 `nvarchar(max)`。</span><span class="sxs-lookup"><span data-stu-id="70fe9-104">Replace all uses of the `char`, `varchar`, and `text` data types with `nchar`, `nvarchar`, and `nvarchar(max)`.</span></span> <span data-ttu-id="70fe9-105">如此一來您就不需要考慮字碼頁轉換的問題。</span><span class="sxs-lookup"><span data-stu-id="70fe9-105">By doing this, you do not have to consider code page conversion issues.</span></span> <span data-ttu-id="70fe9-106">如需詳細資訊，請參閱 [Collation and Unicode Support](collation-and-unicode-support.md)。</span><span class="sxs-lookup"><span data-stu-id="70fe9-106">For more information, see [Collation and Unicode Support](collation-and-unicode-support.md).</span></span>  
  
-   <span data-ttu-id="70fe9-107">當您執行月份和週中日的比較和運算時，請使用數值的日期部分，而不要使用名稱字串。</span><span class="sxs-lookup"><span data-stu-id="70fe9-107">When you perform month and day-of-week comparisons and operations, use the numeric date parts instead of the name strings.</span></span> <span data-ttu-id="70fe9-108">不同的語言設定會傳回不同的月份和週中日名稱。</span><span class="sxs-lookup"><span data-stu-id="70fe9-108">Different language settings return different names for the months and weekdays.</span></span> <span data-ttu-id="70fe9-109">例如，語言設定為「英文 (美國)」時，DATENAME(MONTH,GETDATE()) 會傳回 May；當語言設定為「德文」時，會傳回 Mai；而當語言設定為「法文」時，會傳回 mai。</span><span class="sxs-lookup"><span data-stu-id="70fe9-109">For example, DATENAME(MONTH,GETDATE()) returns May when the language is set to U.S. English, returns Mai when the language is set to German, and returns mai when the language is set to French.</span></span> <span data-ttu-id="70fe9-110">請改用如 DATEPART 的函數，使用數字月份而不用名稱。</span><span class="sxs-lookup"><span data-stu-id="70fe9-110">Instead, use a function such as DATEPART that uses the number of the month instead of the name.</span></span> <span data-ttu-id="70fe9-111">當您要將結果集顯示給使用者時，請使用 DATEPART 名稱，因為日期名稱通常比數值表示法來得有意義。</span><span class="sxs-lookup"><span data-stu-id="70fe9-111">Use the DATEPART names when you build result sets to be displayed to a user, because the date names are frequently more meaningful than a numeric representation.</span></span> <span data-ttu-id="70fe9-112">但是，不要根據特定語言的顯示名稱來撰寫程式碼邏輯。</span><span class="sxs-lookup"><span data-stu-id="70fe9-112">However, do not code any logic that depends on the displayed names being from a specific language.</span></span>  
  
-   <span data-ttu-id="70fe9-113">當您在比較或輸入至 INSERT 或 UPDATE 陳述式中指定日期時，請使用所有語言設定都作相同解譯的常數：</span><span class="sxs-lookup"><span data-stu-id="70fe9-113">When you specify dates in comparisons or for input to INSERT or UPDATE statements, use constants that are interpreted the same way for all language settings:</span></span>  
  
    -   <span data-ttu-id="70fe9-114">ADO、OLE DB 和 ODBC 應用程式應該使用以下形式的 ODBC 時間戳記、日期和時間逸出子句：</span><span class="sxs-lookup"><span data-stu-id="70fe9-114">ADO, OLE DB, and ODBC applications should use the ODBC timestamp, date, and time escape clauses of:</span></span>  
  
         <span data-ttu-id="70fe9-115">**{ts '** yyyy **-** _mm_ **-** _ddhh_**：**_mm_**：**_ss_[**。**_fff_]**'}** 例如： **{ts '** 1998 **-** 09 **-** 24 10 **：** 02 **：** 20 **'}**</span><span class="sxs-lookup"><span data-stu-id="70fe9-115">**{ ts'** yyyy**-**_mm_**-**_ddhh_**:**_mm_**:**_ss_[**.**_fff_] **'}** such as: **{ ts'** 1998**-** 09**-** 24 10 **:** 02 **:** 20 **' }**</span></span>  
  
         <span data-ttu-id="70fe9-116">**{ d'** _yyyy_ **-** _mm_ **-** _dd_ **'}** 例如： **{ d'** 1998**-** 09**-** 24 **'}**</span><span class="sxs-lookup"><span data-stu-id="70fe9-116">**{ d'** _yyyy_ **-** _mm_ **-** _dd_ **'}** such as: **{ d'** 1998**-** 09**-** 24 **'}**</span></span>  
  
         <span data-ttu-id="70fe9-117">**{t '** _hh_ **：** _mm_ **：** _ss_ **'}** 例如： **{t '** 10:02:20 **'}**</span><span class="sxs-lookup"><span data-stu-id="70fe9-117">**{ t'** _hh_ **:** _mm_ **:** _ss_ **'}** such as: **{ t'** 10:02:20 **'}**</span></span>  
  
    -   <span data-ttu-id="70fe9-118">使用其他 API 或 [!INCLUDE[tsql](../../includes/tsql-md.md)] 指令碼、預存程序和觸發程序的應用程式，應該使用未分隔的數值字串。</span><span class="sxs-lookup"><span data-stu-id="70fe9-118">Applications that use other APIs, or [!INCLUDE[tsql](../../includes/tsql-md.md)] scripts, stored procedures, and triggers, should use the unseparated numeric strings.</span></span> <span data-ttu-id="70fe9-119">例如 *yyyymmdd* 為 19980924。</span><span class="sxs-lookup"><span data-stu-id="70fe9-119">For example, *yyyymmdd* as 19980924.</span></span>  
  
    -   <span data-ttu-id="70fe9-120">使用其他 api 或 [!INCLUDE[tsql](../../includes/tsql-md.md)] 腳本、預存程式和觸發程式的應用程式，應該對 `time` 、 `date` 、、 `smalldate` `datetime` 、 **datetime2**和 `datetimeoffset` 資料類型與字元字串資料類型之間的所有轉換使用明確樣式參數的 CONVERT 語句。</span><span class="sxs-lookup"><span data-stu-id="70fe9-120">Applications that use other APIs, or [!INCLUDE[tsql](../../includes/tsql-md.md)] scripts, stored procedures, and triggers should use the CONVERT statement with an explicit style parameter for all conversions between the `time`, `date`, `smalldate`, `datetime`, **datetime2**, and `datetimeoffset` data types and character string data types.</span></span> <span data-ttu-id="70fe9-121">例如，下列陳述式在所有日期格式連接設定下的解譯都是一樣的：</span><span class="sxs-lookup"><span data-stu-id="70fe9-121">For example, the following statement is interpreted in the same way for all language or date format connection settings:</span></span>  
  
        ```  
        SELECT *  
        FROM AdventureWorks2012.Sales.SalesOrderHeader  
        WHERE OrderDate = CONVERT(DATETIME, '20060719', 101)  
        ```  
  
         <span data-ttu-id="70fe9-122">如需詳細資訊，請參閱 [CAST 和 CONVERT &#40;Transact-SQL&#41;](/sql/t-sql/functions/cast-and-convert-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="70fe9-122">For more information, see [CAST and CONVERT &#40;Transact-SQL&#41;](/sql/t-sql/functions/cast-and-convert-transact-sql).</span></span>  
  
  
