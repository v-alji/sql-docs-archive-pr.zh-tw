---
title: 日期和時間改善 (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- date/time [OLE DB]
- OLE DB, date/time improvements
ms.assetid: 71614aaf-0fa4-4fe0-b522-68e2e0b66f43
author: rothja
ms.author: jroth
ms.openlocfilehash: 16bb9e98691aea829eb71a16ddabddb371d7bcf3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707482"
---
# <a name="date-and-time-improvements-ole-db"></a><span data-ttu-id="356a6-102">日期和時間改善 (OLE DB)</span><span class="sxs-lookup"><span data-stu-id="356a6-102">Date and Time Improvements (OLE DB)</span></span>
  [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] <span data-ttu-id="356a6-103">導入了新的日期和時間資料類型。</span><span class="sxs-lookup"><span data-stu-id="356a6-103">introduces new date and time data types.</span></span> <span data-ttu-id="356a6-104">本章節描述如何將這些新類型公開為 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 中的延伸模組。</span><span class="sxs-lookup"><span data-stu-id="356a6-104">This section describes how these new types are exposed as extensions in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client.</span></span> <span data-ttu-id="356a6-105">如需有關 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 新日期和時間資料類型之 Native Client 支援的總覽，請參閱[日期和時間改善](../native-client/features/date-and-time-improvements.md)。</span><span class="sxs-lookup"><span data-stu-id="356a6-105">For an overview of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client support for the new date and time data types, see [Date and Time Improvements](../native-client/features/date-and-time-improvements.md).</span></span> <span data-ttu-id="356a6-106">如需範例，請參閱[使用增強型日期和時間功能 &#40;OLE DB&#41;](../native-client-ole-db-how-to/use-enhanced-date-and-time-features-ole-db.md)。</span><span class="sxs-lookup"><span data-stu-id="356a6-106">For a sample, see [Use Enhanced Date and Time Features &#40;OLE DB&#41;](../native-client-ole-db-how-to/use-enhanced-date-and-time-features-ole-db.md).</span></span>  
  
 <span data-ttu-id="356a6-107">如需更多日期和時間資料類型的一般資訊，請參閱 [datetime &#40;Transact-SQL&#41;](/sql/t-sql/data-types/datetime-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="356a6-107">For more general information about date and time data types, see [datetime &#40;Transact-SQL&#41;](/sql/t-sql/data-types/datetime-transact-sql).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="356a6-108">本節內容</span><span class="sxs-lookup"><span data-stu-id="356a6-108">In This Section</span></span>  
 [<span data-ttu-id="356a6-109">對 OLE DB 日期和時間改善的資料類型支援</span><span class="sxs-lookup"><span data-stu-id="356a6-109">Data Type Support for OLE DB Date and Time Improvements</span></span>](../../relational-databases/native-client-ole-db-date-time/data-type-support-for-ole-db-date-and-time-improvements.md)  
 <span data-ttu-id="356a6-110">提供有關 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 支援 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 日期和時間資料類型的 OLE DB (Native Client) 類型的資訊。</span><span class="sxs-lookup"><span data-stu-id="356a6-110">Provides information about OLE DB ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client) types that support [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] date and time data types.</span></span>  
  
 [<span data-ttu-id="356a6-111">中繼資料 &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="356a6-111">Metadata &#40;OLE DB&#41;</span></span>](../../database-engine/dev-guide/metadata-ole-db.md)  
 <span data-ttu-id="356a6-112">包含 DBBINDING 結構、、 `ICommandWithParameters::GetParameterInfo` `ICommandWithParameters::SetParameterInfo` 、 `IColumnsRowset::GetColumnsRowset` 和 I 的相關資訊 `ColumnsInfo::GetColumnInfo` 。也提供 OLE DB 架構資料列集之更新的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="356a6-112">Contains information about the DBBINDING structure, `ICommandWithParameters::GetParameterInfo`, `ICommandWithParameters::SetParameterInfo`, `IColumnsRowset::GetColumnsRowset`, and I`ColumnsInfo::GetColumnInfo`. Also provides information about updates to OLE DB schema rowsets.</span></span>  
  
 [<span data-ttu-id="356a6-113">繫結和轉換 &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="356a6-113">Bindings and Conversions &#40;OLE DB&#41;</span></span>](../../relational-databases/native-client-ole-db-date-time/conversions-ole-db.md)  
 <span data-ttu-id="356a6-114">描述在伺服器和用戶端之間，針對現有日期類型和新日期類型進行轉換的規則。</span><span class="sxs-lookup"><span data-stu-id="356a6-114">Describes the rules for conversion between server and client for both existing and new date types.</span></span>  
  
 [<span data-ttu-id="356a6-115">增強型日期和時間類型的大量複製變更 &#40;OLE DB 和 ODBC&#41;</span><span class="sxs-lookup"><span data-stu-id="356a6-115">Bulk Copy Changes for Enhanced Date and Time Types &#40;OLE DB and ODBC&#41;</span></span>](../../relational-databases/native-client-odbc-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db-and-odbc.md)  
 <span data-ttu-id="356a6-116">描述可支援大量複製作業的日期/時間增強功能。</span><span class="sxs-lookup"><span data-stu-id="356a6-116">Describes date/time enhancements to support bulk copy operations.</span></span>  
  
 [<span data-ttu-id="356a6-117">OLE DB API 對日期和時間增強功能的支援</span><span class="sxs-lookup"><span data-stu-id="356a6-117">OLE DB API Support for Date and Time Enhancements</span></span>](ole-db-api-support-for-date-and-time-enhancements.md)  
 <span data-ttu-id="356a6-118">描述支援日期/時間增強功能的 OLE DB API。</span><span class="sxs-lookup"><span data-stu-id="356a6-118">Describes the OLE DB APIs that support enhanced date/time features.</span></span>  
  
 [<span data-ttu-id="356a6-119">IRowsetFind 的相容性</span><span class="sxs-lookup"><span data-stu-id="356a6-119">Comparability for IRowsetFind</span></span>](../../relational-databases/native-client-ole-db-date-time/comparability-for-irowsetfind.md)  
 <span data-ttu-id="356a6-120">描述日期/時間類型和 `IRowsetFind`。</span><span class="sxs-lookup"><span data-stu-id="356a6-120">Describes date/time types and `IRowsetFind`.</span></span>  
  
 [<span data-ttu-id="356a6-121">先前 SQL Server 版本的新日期和時間功能 &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="356a6-121">New Date and Time Features with Previous SQL Server Versions &#40;OLE DB&#41;</span></span>](new-date-and-time-features-with-previous-sql-server-versions-ole-db.md)  
 <span data-ttu-id="356a6-122">描述使用日期和時間增強功能的應用程式與舊版 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 進行通訊時，以及使用舊版 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 編譯的用戶端將命令傳送到支援日期和時間增強功能的伺服器時的預期行為。</span><span class="sxs-lookup"><span data-stu-id="356a6-122">Describes the expected behavior when a client application that uses enhanced date and time features communicates with an older version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], and when a client compiled with an older version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client sends commands to a server that supports enhanced date and time features.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="356a6-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="356a6-123">See Also</span></span>  
 [<span data-ttu-id="356a6-124">SQL Server Native Client &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="356a6-124">SQL Server Native Client &#40;OLE DB&#41;</span></span>](../../relational-databases/native-client/ole-db/sql-server-native-client-ole-db.md)  
  
  
