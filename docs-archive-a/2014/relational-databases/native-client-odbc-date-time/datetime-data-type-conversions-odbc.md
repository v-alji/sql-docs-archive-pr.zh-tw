---
title: " (ODBC) 的日期時間資料類型轉換 |Microsoft Docs"
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- conversions [ODBC]
- bindings [ODBC]
- ODBC, bindings and conversions
ms.assetid: 66b9d282-c88d-40e5-93c2-fd5499a74458
author: rothja
ms.author: jroth
ms.openlocfilehash: 142e4388cb87055ddbc6faa7d5b1a92a627738c2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598334"
---
# <a name="datetime-data-type-conversions-odbc"></a><span data-ttu-id="7414d-102">datetime 資料類型轉換 (ODBC)</span><span class="sxs-lookup"><span data-stu-id="7414d-102">datetime Data Type Conversions (ODBC)</span></span>
  <span data-ttu-id="7414d-103">下列轉換已由 ODBC 定義，或為一致的 ODBC 延伸模組。</span><span class="sxs-lookup"><span data-stu-id="7414d-103">The following conversions are either already defined by ODBC or are a consistent extension of ODBC.</span></span> <span data-ttu-id="7414d-104">每個提供者所提供的轉換取決於提供者所服務的社群，因此在提供者之間通常會發生不一致。</span><span class="sxs-lookup"><span data-stu-id="7414d-104">The conversions supplied by each provider are determined by the community served by the provider, and there are often inconsistencies between providers as a result.</span></span> <span data-ttu-id="7414d-105">方括號中的值是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="7414d-105">Values in square brackets are optional.</span></span>  
  
-   <span data-ttu-id="7414d-106">datetime 字串的格式為 'yyyy-mm-dd[ hh:mm:ss[.9999999][ plus/minus hh:mm]]'</span><span class="sxs-lookup"><span data-stu-id="7414d-106">The format of datetime strings is 'yyyy-mm-dd[ hh:mm:ss[.9999999][ plus/minus hh:mm]]'</span></span>  
  
-   <span data-ttu-id="7414d-107">time 字串的格式是 'hh:mm:ss[.9999999]'</span><span class="sxs-lookup"><span data-stu-id="7414d-107">The format of time strings is 'hh:mm:ss[.9999999]'</span></span>  
  
-   <span data-ttu-id="7414d-108">date 字串的格式為 'yyyy-mm-dd'</span><span class="sxs-lookup"><span data-stu-id="7414d-108">The format of date strings is 'yyyy-mm-dd'</span></span>  
  
 <span data-ttu-id="7414d-109">字串的轉換在空白和欄位寬度上允許彈性。</span><span class="sxs-lookup"><span data-stu-id="7414d-109">Conversions from strings allow flexibility in white space and field width.</span></span> <span data-ttu-id="7414d-110">如需詳細資訊，請參閱[資料類型支援 ODBC 日期和時間改善](data-type-support-for-odbc-date-and-time-improvements.md)的「資料格式：字串和常值」一節。</span><span class="sxs-lookup"><span data-stu-id="7414d-110">For more information, see the "Data Formats: Strings and Literals" section of [Data Type Support for ODBC Date and Time Improvements](data-type-support-for-odbc-date-and-time-improvements.md).</span></span>  
  
 <span data-ttu-id="7414d-111">下面是一般轉換規則：</span><span class="sxs-lookup"><span data-stu-id="7414d-111">The following are general conversion rules:</span></span>  
  
-   <span data-ttu-id="7414d-112">如果沒有任何時間存在，但是接收者可以儲存時間，則時間會設定為零。</span><span class="sxs-lookup"><span data-stu-id="7414d-112">If no time is present but the receiver can store time, the time is set to zero.</span></span>  
  
-   <span data-ttu-id="7414d-113">如果沒有任何日期存在，但是接收者可以儲存日期，則會使用目前的日期。</span><span class="sxs-lookup"><span data-stu-id="7414d-113">If no date is present but the receiver can store date, the current date is used.</span></span>  
  
-   <span data-ttu-id="7414d-114">如果在資料類型中沒有用戶端所使用的時區存在，但是伺服器可以儲存時區，則會將日期儲存在用戶端的時區中。</span><span class="sxs-lookup"><span data-stu-id="7414d-114">If no timezone is present in the data type that the client is using but the server can store timezone, the date is stored in the client timezone.</span></span> <span data-ttu-id="7414d-115">請注意，這與伺服器行為不同。</span><span class="sxs-lookup"><span data-stu-id="7414d-115">Note that this differs from the server behavior.</span></span>  
  
-   <span data-ttu-id="7414d-116">如果在伺服器類型中沒有時區存在，但是用戶端類型擁有時區，則會先將時間轉換為 UTC，然後再儲存在伺服器上。</span><span class="sxs-lookup"><span data-stu-id="7414d-116">If no timezone is present in the server type but the client type has a timezone, time is converted to UTC before being stored on the server.</span></span>  
  
-   <span data-ttu-id="7414d-117">如果有時間存在，但是接收者無法儲存時間，則會忽略時間元件。</span><span class="sxs-lookup"><span data-stu-id="7414d-117">If time is present but the receiver cannot store time, the time component is ignored.</span></span>  
  
-   <span data-ttu-id="7414d-118">如果有日期存在，但是接收者無法儲存日期，則會忽略日期元件。</span><span class="sxs-lookup"><span data-stu-id="7414d-118">If a date is present but the receiver cannot store the date, the date component is ignored.</span></span>  
  
-   <span data-ttu-id="7414d-119">如果在從 C 轉換為 SQL 時發生秒或毫秒的截斷，就會產生包含 SQLSTATE 22008 以及「日期時間欄位溢位」訊息的診斷記錄。</span><span class="sxs-lookup"><span data-stu-id="7414d-119">If truncation of seconds or fractional seconds occurs when converting from C to SQL, a diagnostic record is generated with SQLSTATE 22008 and the message "Datetime field overflow".</span></span>  
  
-   <span data-ttu-id="7414d-120">如果在從 SQL 轉換為 C 時發生秒或毫秒的截斷，就會產生包含 SQLSTATE 01S07 以及「小數位數截斷」訊息的診斷記錄。</span><span class="sxs-lookup"><span data-stu-id="7414d-120">If truncation of seconds or fractional seconds occurs when converting from SQL to C, a diagnostic record is generated with SQLSTATE 01S07 and the message "Fractional truncation".</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7414d-121">本節內容</span><span class="sxs-lookup"><span data-stu-id="7414d-121">In This Section</span></span>  
 [<span data-ttu-id="7414d-122">從 C 轉換成 SQL</span><span class="sxs-lookup"><span data-stu-id="7414d-122">Conversions from C to SQL</span></span>](datetime-data-type-conversions-from-c-to-sql.md)  
 <span data-ttu-id="7414d-123">列出當您從 C 類型轉換成 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 日期/時間類型時應該考量的問題。</span><span class="sxs-lookup"><span data-stu-id="7414d-123">Lists issues to consider when you convert from C types to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data/time types.</span></span>  
  
 [<span data-ttu-id="7414d-124">從 SQL 轉換成 C</span><span class="sxs-lookup"><span data-stu-id="7414d-124">Conversions from SQL to C</span></span>](datetime-data-type-conversions-from-sql-to-c.md)  
 <span data-ttu-id="7414d-125">列出當您從 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 日期/時間類型轉換成 C 類型時應該考量的問題。</span><span class="sxs-lookup"><span data-stu-id="7414d-125">Lists issues to consider when you convert from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data/time types to C types.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7414d-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7414d-126">See Also</span></span>  
 [<span data-ttu-id="7414d-127">ODBC&#41;&#40;的日期和時間改善</span><span class="sxs-lookup"><span data-stu-id="7414d-127">Date and Time Improvements &#40;ODBC&#41;</span></span>](date-and-time-improvements-odbc.md)  
  
  
