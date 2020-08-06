---
title: 繫結和轉換 (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- conversions [OLE DB]
- bindings [OLE DB]
- OLE DB, bindings and conversions
ms.assetid: c187df58-a8c8-4c74-a76f-663abbc5f0c1
author: rothja
ms.author: jroth
ms.openlocfilehash: 95c73bdad80b5f948a45235ad208ab307fcceff3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599507"
---
# <a name="bindings-and-conversions-ole-db"></a><span data-ttu-id="4c3ce-102">繫結和轉換 (OLE DB)</span><span class="sxs-lookup"><span data-stu-id="4c3ce-102">Bindings and Conversions (OLE DB)</span></span>
  <span data-ttu-id="4c3ce-103">本節討論如何在 `datetime` 和 `datetimeoffset` 值之間轉換。</span><span class="sxs-lookup"><span data-stu-id="4c3ce-103">This section discusses how to convert between `datetime` and `datetimeoffset` values.</span></span> <span data-ttu-id="4c3ce-104">本節中所描述的轉換已由 OLE DB 提供，或是一致的 OLE DB 延伸模組。</span><span class="sxs-lookup"><span data-stu-id="4c3ce-104">The conversions described in this section are either already provided by OLE DB or are a consistent extension of OLE DB.</span></span>  
  
 <span data-ttu-id="4c3ce-105">在 OLE DB 中，日期和時間之常值和字串的格式通常會遵循 ISO，而且不會相依於用戶端地區設定。</span><span class="sxs-lookup"><span data-stu-id="4c3ce-105">The format of literals and strings for dates and times in OLE DB generally follows ISO, and is not dependent on the client locale.</span></span> <span data-ttu-id="4c3ce-106">有一個例外是 DBTYPE_DATE，其中的標準為 OLE Automation。</span><span class="sxs-lookup"><span data-stu-id="4c3ce-106">One exception is DBTYPE_DATE, where the standard is OLE Automation.</span></span> <span data-ttu-id="4c3ce-107">不過，由於資料在用戶端來回傳輸時，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 只會在類型之間轉換，因此，應用程式無法強制 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 在 DBTYPE_DATE 和字串格式之間轉換。</span><span class="sxs-lookup"><span data-stu-id="4c3ce-107">However, because [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client only converts between types when data is transmitted to or from the client, there is no way for an application to force [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client to convert between DBTYPE_DATE and string formats.</span></span> <span data-ttu-id="4c3ce-108">否則，字串會使用下列格式 (以方括弧括住的文字表示選擇性的元素)：</span><span class="sxs-lookup"><span data-stu-id="4c3ce-108">Otherwise, strings use the following formats (text in brackets indicates an optional element):</span></span>  
  
-   <span data-ttu-id="4c3ce-109">`datetime` 和 `datetimeoffset` 字串的格式為：</span><span class="sxs-lookup"><span data-stu-id="4c3ce-109">The format of `datetime` and `datetimeoffset` strings is:</span></span>  
  
     <span data-ttu-id="4c3ce-110">*yyyy* -*mm* -*dd*[ *hh*：*mm*：*ss*[]。*9999999*] [？？</span><span class="sxs-lookup"><span data-stu-id="4c3ce-110">*yyyy*-*mm*-*dd*[ *hh*:*mm*:*ss*[.*9999999*][ ??</span></span> <span data-ttu-id="4c3ce-111">*hh*：*mm*]]</span><span class="sxs-lookup"><span data-stu-id="4c3ce-111">*hh*:*mm*]]</span></span>  
  
-   <span data-ttu-id="4c3ce-112">`time` 字串的格式為：</span><span class="sxs-lookup"><span data-stu-id="4c3ce-112">The format of `time` strings is:</span></span>  
  
     <span data-ttu-id="4c3ce-113">*hh*:*mm*:*ss*[.*9999999*]</span><span class="sxs-lookup"><span data-stu-id="4c3ce-113">*hh*:*mm*:*ss*[.*9999999*]</span></span>  
  
-   <span data-ttu-id="4c3ce-114">`date` 字串的格式為：</span><span class="sxs-lookup"><span data-stu-id="4c3ce-114">The format of `date` strings is:</span></span>  
  
     <span data-ttu-id="4c3ce-115">*yyyy*-*mm*-*dd*</span><span class="sxs-lookup"><span data-stu-id="4c3ce-115">*yyyy*-*mm*-*dd*</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4c3ce-116">如果標準轉換失敗，舊版 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 和 SQLOLEDB 會實作 OLE 轉換。</span><span class="sxs-lookup"><span data-stu-id="4c3ce-116">Earlier versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client and SQLOLEDB implemented OLE conversions, in case standard conversions failed.</span></span> <span data-ttu-id="4c3ce-117">因此，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 10.0 和更新版本所執行的某些轉換與 OLE DB 規格不同。</span><span class="sxs-lookup"><span data-stu-id="4c3ce-117">As a result, some conversions performed by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 10.0 and later differ from the OLE DB specification.</span></span>  
  
 <span data-ttu-id="4c3ce-118">字串的轉換在空白和欄位寬度上允許彈性。</span><span class="sxs-lookup"><span data-stu-id="4c3ce-118">Conversions from strings allow flexibility in white space and field width.</span></span> <span data-ttu-id="4c3ce-119">如需詳細資訊，請參閱資料類型支援中的「資料格式：字串和常值」一節，[以瞭解 OLE DB 日期和時間改善](data-type-support-for-ole-db-date-and-time-improvements.md)。</span><span class="sxs-lookup"><span data-stu-id="4c3ce-119">For more information, see the "Data Formats: Strings and Literals" section in [Data Type Support for OLE DB Date and Time Improvements](data-type-support-for-ole-db-date-and-time-improvements.md).</span></span>  
  
 <span data-ttu-id="4c3ce-120">下面是一般轉換規則：</span><span class="sxs-lookup"><span data-stu-id="4c3ce-120">The following are general conversion rules:</span></span>  
  
-   <span data-ttu-id="4c3ce-121">當字串轉換為日期/時間類型時，會先將字串剖析為 ISO 常值。</span><span class="sxs-lookup"><span data-stu-id="4c3ce-121">When a string is converted to a date/time type, the string is first parsed as an ISO literal.</span></span> <span data-ttu-id="4c3ce-122">如果失敗，則會將字串剖析為擁有日期元件的 OLE 日期常值。</span><span class="sxs-lookup"><span data-stu-id="4c3ce-122">If this fails, the string is parsed as an OLE date literal, which has time components.</span></span>  
  
-   <span data-ttu-id="4c3ce-123">如果沒有任何時間存在，但是接收者可以儲存時間，則時間會設定為零。</span><span class="sxs-lookup"><span data-stu-id="4c3ce-123">If no time is present but the receiver can store time, the time is set to zero.</span></span> <span data-ttu-id="4c3ce-124">如果沒有任何日期存在，但是接收者可以儲存日期，使用 ISO 轉換時，日期會設定為目前的日期，而使用 OLE 轉換時，則會設定為 1899-12-30。</span><span class="sxs-lookup"><span data-stu-id="4c3ce-124">If no date is present but the receiver can store a date, the date is set to the current date when ISO conversions are used and to 1899-12-30 when OLE conversions are used.</span></span>  
  
-   <span data-ttu-id="4c3ce-125">如果在資料類型中沒有用戶端所使用的時區存在，但是伺服器可以儲存時區，則會假設用戶端上的資料位於用戶端的時區中。</span><span class="sxs-lookup"><span data-stu-id="4c3ce-125">If no timezone is present in the data type that the client is using, but the server can store timezone, the data on the client is assumed to be in the client timezone.</span></span>  
  
-   <span data-ttu-id="4c3ce-126">如果在伺服器上沒有任何時區存在，但是用戶端擁有時區資訊，則會假設 UTC 時區。</span><span class="sxs-lookup"><span data-stu-id="4c3ce-126">If no timezone is present at the server but the client has timezone information, the UTC timezone is assumed.</span></span> <span data-ttu-id="4c3ce-127">這與伺服器行為不同。</span><span class="sxs-lookup"><span data-stu-id="4c3ce-127">This differs from server behavior.</span></span>  
  
-   <span data-ttu-id="4c3ce-128">如果有時間存在，但是接收者無法儲存時間，則會忽略時間元件。</span><span class="sxs-lookup"><span data-stu-id="4c3ce-128">If the time is present but the receiver cannot store time, the time component is ignored.</span></span>  
  
-   <span data-ttu-id="4c3ce-129">如果有日期存在，但是接收者無法儲存日期，則會忽略日期元件。</span><span class="sxs-lookup"><span data-stu-id="4c3ce-129">If the date is present but the receiver cannot store the date, the date component is ignored.</span></span>  
  
-   <span data-ttu-id="4c3ce-130">如果在從用戶端轉換為伺服器時發生秒或毫秒的截斷，就會傳回 DB_E_ERRORSOCCURRED，並設定 DBSTATUS_E_DATAOVERFLOW 狀態。</span><span class="sxs-lookup"><span data-stu-id="4c3ce-130">If truncation of seconds or fractional seconds occurs when converting from client to server, DB_E_ERRORSOCCURRED is returned and the status DBSTATUS_E_DATAOVERFLOW is set.</span></span>  
  
-   <span data-ttu-id="4c3ce-131">如果在從伺服器轉換為用戶端時發生秒或毫秒的截斷，就會設定 DBSTATUS_S_TRUNCATED。</span><span class="sxs-lookup"><span data-stu-id="4c3ce-131">If truncation of seconds or fractional seconds occurs when converting from server to client, DBSTATUS_S_TRUNCATED is set</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4c3ce-132">本節內容</span><span class="sxs-lookup"><span data-stu-id="4c3ce-132">In This Section</span></span>  
 [<span data-ttu-id="4c3ce-133">從用戶端到伺服器執行的轉換</span><span class="sxs-lookup"><span data-stu-id="4c3ce-133">Conversions Performed from Client to Server</span></span>](conversions-performed-from-client-to-server.md)  
 <span data-ttu-id="4c3ce-134">描述在使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 和 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] (或更新版本) 撰寫之用戶端應用程式之間執行的日期/時間轉換。</span><span class="sxs-lookup"><span data-stu-id="4c3ce-134">Describes date/time conversions performed between a client application written with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB and [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] (or later).</span></span>  
  
 [<span data-ttu-id="4c3ce-135">從伺服器到用戶端執行的轉換</span><span class="sxs-lookup"><span data-stu-id="4c3ce-135">Conversions Performed from Server to Client</span></span>](conversions-performed-from-server-to-client.md)  
 <span data-ttu-id="4c3ce-136">描述在 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] (或更新版本) 和使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 撰寫之用戶端應用程式之間執行的日期/時間轉換。</span><span class="sxs-lookup"><span data-stu-id="4c3ce-136">Describes date/time conversions performed between [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] (or later) and a client application written with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c3ce-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4c3ce-137">See Also</span></span>  
 [<span data-ttu-id="4c3ce-138">日期和時間改善 &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="4c3ce-138">Date and Time Improvements &#40;OLE DB&#41;</span></span>](date-and-time-improvements-ole-db.md)  
  
  
