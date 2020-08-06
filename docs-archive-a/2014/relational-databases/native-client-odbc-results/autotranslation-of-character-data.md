---
title: 字元資料的自動轉譯 |Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- result sets [ODBC], autotranslating character data
- data types [ODBC], autotranslating character data
- ACPs
- SQL Server Native Client ODBC driver, result sets
- ODBC applications, result sets
- AutoTranslate feature
- ANSI code pages
- character data autotranslation [ODBC]
- autotranslating character data
- SQL Server Native Client ODBC driver, data types
- ODBC data types, autotranslating character data
ms.assetid: 86a8adda-c5ad-477f-870f-cb370c39ee13
author: rothja
ms.author: jroth
ms.openlocfilehash: 91dd1714d553f201c1cab78bbca77d2445b42923
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709342"
---
# <a name="autotranslation-of-character-data"></a><span data-ttu-id="ee2cd-102">字元資料的自動轉譯</span><span class="sxs-lookup"><span data-stu-id="ee2cd-102">Autotranslation of Character Data</span></span>
  <span data-ttu-id="ee2cd-103">字元資料（例如使用 SQL_C_CHAR 所宣告的 ANSI 字元變數，或 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 使用**CHAR**、 **Varchar**或**text**資料類型儲存在中的資料）只能代表有限的字元數。</span><span class="sxs-lookup"><span data-stu-id="ee2cd-103">Character data, such as ANSI character variables declared with SQL_C_CHAR or data stored in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] using the **char**, **varchar**, or **text** data types, can represent only a limited number of characters.</span></span> <span data-ttu-id="ee2cd-104">每個字元使用一個位元組儲存的字元資料僅能代表 256 個字元。</span><span class="sxs-lookup"><span data-stu-id="ee2cd-104">Character data stored using one byte per character can only represent 256 characters.</span></span> <span data-ttu-id="ee2cd-105">儲存在 SQL_C_CHAR 變數中的值會使用用戶端電腦的 ANSI 字碼頁 (ACP) 解譯。</span><span class="sxs-lookup"><span data-stu-id="ee2cd-105">The values stored in SQL_C_CHAR variables are interpreted using the ANSI code page (ACP) of the client computer.</span></span> <span data-ttu-id="ee2cd-106">在伺服器上使用**char**、 **Varchar**或**text**資料類型所儲存的值，會使用伺服器的 ACP 進行評估。</span><span class="sxs-lookup"><span data-stu-id="ee2cd-106">The values stored using **char**, **varchar**, or **text** data types on the server are evaluated using the ACP of the server.</span></span>  
  
 <span data-ttu-id="ee2cd-107">如果伺服器和用戶端都有相同的 ACP，就不會有任何問題解讀儲存在 SQL_C_CHAR、 **CHAR**、 **Varchar**或**text**物件中的值。</span><span class="sxs-lookup"><span data-stu-id="ee2cd-107">If both the server and the client have the same ACP, then they have no problems in interpreting the values stored in SQL_C_CHAR, **char**, **varchar**, or **text** objects.</span></span> <span data-ttu-id="ee2cd-108">如果伺服器和用戶端有不同的 Acp，SQL_C_CHAR 則如果在**CHAR**、 **Varchar**或**text**資料行、變數或參數中使用用戶端的資料，則可能會在伺服器上將其轉譯為不同的字元。</span><span class="sxs-lookup"><span data-stu-id="ee2cd-108">If the server and client have different ACPs, then SQL_C_CHAR data from the client may be interpreted as a different character on the server if it is used in **char**, **varchar**, or **text** columns, variables, or parameters.</span></span> <span data-ttu-id="ee2cd-109">例如，包含0xA5 值的字元位元組會解讀為字元？</span><span class="sxs-lookup"><span data-stu-id="ee2cd-109">For example, a character byte containing the value 0xA5 is interpreted as the character ??</span></span> <span data-ttu-id="ee2cd-110">在使用字碼頁437和的電腦上，會被解讀為日元符號 (？在執行字碼頁1252的電腦上 ) 。</span><span class="sxs-lookup"><span data-stu-id="ee2cd-110">on a computer using code page 437 and is interpreted as the yen sign (??) on a computer running code page 1252.</span></span>  
  
 <span data-ttu-id="ee2cd-111">Unicode 資料的每個字元會使用兩個位元組儲存。</span><span class="sxs-lookup"><span data-stu-id="ee2cd-111">Unicode data is stored using two bytes per character.</span></span> <span data-ttu-id="ee2cd-112">Unicode 規格包含所有擴充字元，因此所有電腦都會以相同方式解譯所有 Unicode 字元。</span><span class="sxs-lookup"><span data-stu-id="ee2cd-112">All extended characters are covered by the Unicode specification, so all Unicode characters are interpreted the same by all computers.</span></span>  
  
 <span data-ttu-id="ee2cd-113">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native CLIENT ODBC 驅動程式的 AutoTranslate 功能會嘗試將在具有不同字碼頁的用戶端與伺服器之間移動字元資料的問題降到最低。</span><span class="sxs-lookup"><span data-stu-id="ee2cd-113">The AutoTranslate feature of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver attempts to minimize the problems in moving character data between a client and a server that have different code pages.</span></span> <span data-ttu-id="ee2cd-114">AutoTranslate 可以在[SQLDriverConnect](../native-client-odbc-api/sqldriverconnect.md)的連接字串、 [SQLConfigDataSource](../native-client-odbc-api/sqlconfigdatasource.md)的設定字串或 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 使用 ODBC 管理員的 Native Client ODBC 驅動程式的資料來源中設定。</span><span class="sxs-lookup"><span data-stu-id="ee2cd-114">AutoTranslate can be set in the connect string of [SQLDriverConnect](../native-client-odbc-api/sqldriverconnect.md), in the configuration string of [SQLConfigDataSource](../native-client-odbc-api/sqlconfigdatasource.md), or when configuring data sources for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver using ODBC Administrator.</span></span>  
  
 <span data-ttu-id="ee2cd-115">當 AutoTranslate 設定為 "no" 時，在用戶端上的 SQL_C_CHAR 變數與資料庫中的**CHAR**、 **Varchar**或**text**資料行、變數或參數之間移動的資料，不會進行任何轉換 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="ee2cd-115">When AutoTranslate is set to "no", no conversions are done on data moved between SQL_C_CHAR variables on the client and **char**, **varchar**, or **text** columns, variables, or parameters in a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database.</span></span> <span data-ttu-id="ee2cd-116">如果資料包含擴充字元，而且用戶端電腦和伺服器電腦的字碼頁不同，則位元模式在兩部電腦上的解譯方式可能會不同。</span><span class="sxs-lookup"><span data-stu-id="ee2cd-116">The bit patterns may be interpreted differently on the client and server computers if the data contains extended characters and the two computers have different code pages.</span></span> <span data-ttu-id="ee2cd-117">如果兩部電腦的字碼頁相同，資料將會以相同的方式解譯。</span><span class="sxs-lookup"><span data-stu-id="ee2cd-117">The data will be interpreted the same if both computers have the same code page.</span></span>  
  
 <span data-ttu-id="ee2cd-118">當 AutoTranslate 設定為 "yes" 時， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native CLIENT ODBC 驅動程式會使用 Unicode 來轉換在用戶端上 SQL_C_CHAR 變數與資料庫中的**CHAR**、 **Varchar**或**text**資料行、變數或參數之間移動的資料 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ：</span><span class="sxs-lookup"><span data-stu-id="ee2cd-118">When AutoTranslate is set to "yes", the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver uses Unicode to convert data moved between SQL_C_CHAR variables on the client and **char**, **varchar**, or **text** columns, variables, or parameters in a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database:</span></span>  
  
-   <span data-ttu-id="ee2cd-119">當資料從用戶端上的 SQL_C_CHAR 變數傳送至資料庫中的**CHAR**、 **Varchar**或**text**資料行、變數或參數時 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，ODBC 驅動程式會先使用用戶端的 ACP，從 SQL_C_CHAR 轉換成 Unicode，然後使用伺服器的 ACP，從 unicode 還原成字元。</span><span class="sxs-lookup"><span data-stu-id="ee2cd-119">When data is sent from an SQL_C_CHAR variable on the client to a **char**, **varchar**, or **text** column, variable, or parameter in an [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database, the ODBC driver first converts from SQL_C_CHAR to Unicode using the ACP of the client, then from Unicode back to character using the ACP of the server.</span></span>  
  
-   <span data-ttu-id="ee2cd-120">將資料從**char**、 **Varchar**或**text**資料行、變數或資料庫中的參數傳送 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 到用戶端上的 SQL_C_CHAR 變數時， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native client ODBC 驅動程式會先使用伺服器的 ACP，從字元轉換成 Unicode，然後再從 Unicode 還原為使用用戶端 ACP 的 SQL_C_CHAR。</span><span class="sxs-lookup"><span data-stu-id="ee2cd-120">When data is sent from a **char**, **varchar**, or **text** column, variable, or parameter in a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database to a SQL_C_CHAR variable on the client, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver first converts from character to Unicode using the ACP of the server, then from Unicode back to SQL_C_CHAR using the ACP of the client.</span></span>  
  
 <span data-ttu-id="ee2cd-121">因為這些轉換都是由 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 用戶端上執行的 Native CLIENT ODBC 驅動程式所完成，所以伺服器 ACP 必須是安裝在用戶端電腦上的其中一個字碼頁。</span><span class="sxs-lookup"><span data-stu-id="ee2cd-121">Because all of these conversions are done by the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver executing on the client, the server ACP must be one of the code pages installed on the client computer.</span></span>  
  
 <span data-ttu-id="ee2cd-122">透過 Unicode 進行字元轉換可確保正確轉換同時存在兩個字碼頁上的所有字元。</span><span class="sxs-lookup"><span data-stu-id="ee2cd-122">Making the character conversions through Unicode ensures the proper conversion of all characters that exist in both code pages.</span></span> <span data-ttu-id="ee2cd-123">但是，如果字元存在於其中一個字碼頁，但不存在於另一個字碼頁，則無法在目標字碼頁中表示字元。</span><span class="sxs-lookup"><span data-stu-id="ee2cd-123">If a character exists in one code page but not another, however, then the character cannot be represented in the target code page.</span></span> <span data-ttu-id="ee2cd-124">例如，字碼頁1252具有已註冊商標符號 (？？) ，字碼頁437則不會。</span><span class="sxs-lookup"><span data-stu-id="ee2cd-124">For example, code page 1252 has the registered trademark symbol (??), while code page 437 does not.</span></span>  
  
 <span data-ttu-id="ee2cd-125">AutoTranslate 設定在進行下列轉換時沒有作用：</span><span class="sxs-lookup"><span data-stu-id="ee2cd-125">The AutoTranslate setting has no effect on these conversions:</span></span>  
  
-   <span data-ttu-id="ee2cd-126">在字元 SQL_C_CHAR 用戶端變數與 Unicode **Nchar**、 **Nvarchar**或**Ntext**資料行、變數或資料庫中的參數之間移動資料 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="ee2cd-126">Moving data between character SQL_C_CHAR client variables and Unicode **nchar**, **nvarchar**, or **ntext** columns, variables, or parameters in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases.</span></span>  
  
-   <span data-ttu-id="ee2cd-127">在 Unicode SQL_C_WCHAR 用戶端變數，以及資料庫中的字元**char**、 **Varchar**或**text**資料行、變數或參數之間移動資料 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="ee2cd-127">Moving data between Unicode SQL_C_WCHAR client variables and character **char**, **varchar**, or **text** columns, variables, or parameters in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases.</span></span>  
  
 <span data-ttu-id="ee2cd-128">從字元移到 Unicode 時，永遠必須轉換資料。</span><span class="sxs-lookup"><span data-stu-id="ee2cd-128">Data always must be converted when moved from character to Unicode.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee2cd-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ee2cd-129">See Also</span></span>  
 <span data-ttu-id="ee2cd-130">[&#40;ODBC&#41;處理結果](processing-results-odbc.md) </span><span class="sxs-lookup"><span data-stu-id="ee2cd-130">[Processing Results &#40;ODBC&#41;](processing-results-odbc.md) </span></span>  
 [<span data-ttu-id="ee2cd-131">定序與 Unicode 支援</span><span class="sxs-lookup"><span data-stu-id="ee2cd-131">Collation and Unicode Support</span></span>](../collations/collation-and-unicode-support.md)  
  
  
