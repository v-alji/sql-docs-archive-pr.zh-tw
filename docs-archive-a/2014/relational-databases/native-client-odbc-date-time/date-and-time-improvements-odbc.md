---
title: ODBC)  (的日期和時間改善 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- date/time [ODBC]
- ODBC, date/time improvements
ms.assetid: e31d5ca5-2103-498f-954c-1ee93e217186
author: rothja
ms.author: jroth
ms.openlocfilehash: 6ce8f906fc1949a80bfa8e5a541ecf1e83878775
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595941"
---
# <a name="date-and-time-improvements-odbc"></a><span data-ttu-id="0e0ff-102">日期和時間改善 (ODBC)</span><span class="sxs-lookup"><span data-stu-id="0e0ff-102">Date and Time Improvements (ODBC)</span></span>
  [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] <span data-ttu-id="0e0ff-103">導入了新的日期和時間資料類型。</span><span class="sxs-lookup"><span data-stu-id="0e0ff-103">introduced new date and time data types.</span></span> <span data-ttu-id="0e0ff-104">本章節描述如何將這些新類型公開為 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 中的延伸模組。</span><span class="sxs-lookup"><span data-stu-id="0e0ff-104">This section describes how these new types are exposed as extensions in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client.</span></span> <span data-ttu-id="0e0ff-105">如需 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 有關新日期和時間資料類型之 Native Client 支援的總覽，請參閱[日期和時間改善](../native-client/features/date-and-time-improvements.md)。</span><span class="sxs-lookup"><span data-stu-id="0e0ff-105">For an overview of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client support for the new date and time data types, see [Date and Time Improvements](../native-client/features/date-and-time-improvements.md).</span></span> <span data-ttu-id="0e0ff-106">如需示範 ODBC 日期/時間支援的範例，請參閱[使用日期和時間類型](../native-client-odbc-how-to/use-date-and-time-types.md)。</span><span class="sxs-lookup"><span data-stu-id="0e0ff-106">For a sample demonstrating ODBC date/time support, see [Use Date and Time Types](../native-client-odbc-how-to/use-date-and-time-types.md).</span></span>  
  
 <span data-ttu-id="0e0ff-107">如需更多日期和時間資料類型的一般資訊，請參閱 [datetime &#40;Transact-SQL&#41;](/sql/t-sql/data-types/datetime-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="0e0ff-107">For more general information about date and time data types, see [datetime &#40;Transact-SQL&#41;](/sql/t-sql/data-types/datetime-transact-sql).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0e0ff-108">本節內容</span><span class="sxs-lookup"><span data-stu-id="0e0ff-108">In This Section</span></span>  
 [<span data-ttu-id="0e0ff-109">資料類型對 ODBC 日期和時間支援的改善</span><span class="sxs-lookup"><span data-stu-id="0e0ff-109">Data Type Support for ODBC Date and Time Improvements</span></span>](../../relational-databases/native-client-odbc-date-time/data-type-support-for-odbc-date-and-time-improvements.md)  
 <span data-ttu-id="0e0ff-110">提供有關支援 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 日期和時間資料類型之 ODBC 類型的資訊。</span><span class="sxs-lookup"><span data-stu-id="0e0ff-110">Provides information about ODBC types that support [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] date and time data types.</span></span>  
  
 [<span data-ttu-id="0e0ff-111">&#40;ODBC&#41;的中繼資料</span><span class="sxs-lookup"><span data-stu-id="0e0ff-111">Metadata &#40;ODBC&#41;</span></span>](../../database-engine/dev-guide/metadata-odbc.md)  
 <span data-ttu-id="0e0ff-112">描述在實作參數描述項 (IPD) 和實作資料列描述項 (IRD) 欄位中傳回的資訊，以及 `SQLColumns` 和 `SQLProcedureColumns` 傳回的資料行中繼資料。</span><span class="sxs-lookup"><span data-stu-id="0e0ff-112">Describes information returned in the implementation parameter descriptor (IPD) and implementation row descriptor (IRD) fields, as well as column metadata returned by `SQLColumns` and `SQLProcedureColumns`.</span></span> <span data-ttu-id="0e0ff-113">也會描述 `SQLGetTypeInfo` 所傳回的資料類型中繼資料。</span><span class="sxs-lookup"><span data-stu-id="0e0ff-113">Also describes data type metadata returned by `SQLGetTypeInfo`.</span></span>  
  
 [<span data-ttu-id="0e0ff-114">&#40;ODBC&#41;的日期時間資料類型轉換</span><span class="sxs-lookup"><span data-stu-id="0e0ff-114">datetime Data Type Conversions &#40;ODBC&#41;</span></span>](datetime-data-type-conversions-odbc.md)  
 <span data-ttu-id="0e0ff-115">描述如何在 datetime 和 datetimeoffset 值之間轉換。</span><span class="sxs-lookup"><span data-stu-id="0e0ff-115">Describes how to convert between datetime and datetimeoffset values.</span></span>  
  
 [<span data-ttu-id="0e0ff-116">日期和時間類型的 sql_variant 支援</span><span class="sxs-lookup"><span data-stu-id="0e0ff-116">sql_variant Support for Date and Time Types</span></span>](sql-variant-support-for-date-and-time-types.md)  
 <span data-ttu-id="0e0ff-117">描述 SQL_VARIANT 函數對日期和時間增強功能的支援。</span><span class="sxs-lookup"><span data-stu-id="0e0ff-117">Describes SQL_VARIANT function support for enhanced date and time functionality.</span></span>  
  
 [<span data-ttu-id="0e0ff-118">增強型日期和時間類型的大量複製變更 &#40;OLE DB 和 ODBC&#41;</span><span class="sxs-lookup"><span data-stu-id="0e0ff-118">Bulk Copy Changes for Enhanced Date and Time Types &#40;OLE DB and ODBC&#41;</span></span>](../../relational-databases/native-client-odbc-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db-and-odbc.md)  
 <span data-ttu-id="0e0ff-119">描述可支援大量複製作業的日期/時間增強功能。</span><span class="sxs-lookup"><span data-stu-id="0e0ff-119">Describes date/time enhancements to support bulk copy operations.</span></span>  
  
 [<span data-ttu-id="0e0ff-120">舊版 SQL Server 版本的增強型日期和時間類型行為 &#40;ODBC&#41;</span><span class="sxs-lookup"><span data-stu-id="0e0ff-120">Enhanced Date and Time Type Behavior with Previous SQL Server Versions &#40;ODBC&#41;</span></span>](enhanced-date-and-time-type-behavior-with-previous-sql-server-versions-odbc.md)  
 <span data-ttu-id="0e0ff-121">描述當使用日期和時間增強功能的用戶端應用程式與舊版 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 進行通訊時，以及使用舊版 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 編譯的用戶端將命令傳送到支援日期和時間增強功能的伺服器時，將會發生的預期行為。</span><span class="sxs-lookup"><span data-stu-id="0e0ff-121">Describes the expected behavior when a client application using enhanced date and time features communicates with an older version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], and when a client compiled with an older version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client sends commands to a server that supports enhanced date and time features.</span></span>  
  
 [<span data-ttu-id="0e0ff-122">增強型日期和時間功能的 ODBC API 支援</span><span class="sxs-lookup"><span data-stu-id="0e0ff-122">ODBC API Support for Enhanced Date and Time Features</span></span>](odbc-api-support-for-enhanced-date-and-time-features.md)  
 <span data-ttu-id="0e0ff-123">列出支援日期和時間增強功能的 ODBC 函數。</span><span class="sxs-lookup"><span data-stu-id="0e0ff-123">Lists the ODBC functions that support enhanced date and time functionality.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e0ff-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0e0ff-124">See Also</span></span>  
 [<span data-ttu-id="0e0ff-125">SQL Server Native Client &#40;ODBC&#41;</span><span class="sxs-lookup"><span data-stu-id="0e0ff-125">SQL Server Native Client &#40;ODBC&#41;</span></span>](../../relational-databases/native-client/odbc/sql-server-native-client-odbc.md)  
  
  
