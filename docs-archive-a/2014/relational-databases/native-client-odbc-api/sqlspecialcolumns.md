---
title: SQLSpecialColumns |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLSpecialColumns function
ms.assetid: dffe02ed-8f79-4c9a-af34-98130bbe5462
author: rothja
ms.author: jroth
ms.openlocfilehash: c36ff73606e95ed7ee5e713b81acf7c177a42563
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595960"
---
# <a name="sqlspecialcolumns"></a><span data-ttu-id="8dbd7-102">SQLSpecialColumns</span><span class="sxs-lookup"><span data-stu-id="8dbd7-102">SQLSpecialColumns</span></span>
  <span data-ttu-id="8dbd7-103"> (*IdentifierType* SQL_BEST_ROWID) 要求資料列識別碼時， **SQLSpecialColumns**會針對) 以外的任何要求範圍，傳回空的結果集 (不 SQL_SCOPE_CURROW 任何資料列。</span><span class="sxs-lookup"><span data-stu-id="8dbd7-103">When requesting row identifiers (*IdentifierType* SQL_BEST_ROWID), **SQLSpecialColumns** returns an empty result set (no data rows) for any requested scope other than SQL_SCOPE_CURROW.</span></span> <span data-ttu-id="8dbd7-104">產生的結果集表示資料行只有在這個範圍中才是有效的。</span><span class="sxs-lookup"><span data-stu-id="8dbd7-104">The generated result set indicates that the columns are only valid within this scope.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="8dbd7-105">不支援識別碼的虛擬資料行。</span><span class="sxs-lookup"><span data-stu-id="8dbd7-105">does not support pseudocolumns for identifiers.</span></span> <span data-ttu-id="8dbd7-106">**SQLSpecialColumns**結果集會將所有資料行識別為 SQL_PC_NOT_PSEUDO。</span><span class="sxs-lookup"><span data-stu-id="8dbd7-106">The **SQLSpecialColumns** result set will identify all columns as SQL_PC_NOT_PSEUDO.</span></span>  
  
 <span data-ttu-id="8dbd7-107">**SQLSpecialColumns**可以在靜態資料指標上執行。</span><span class="sxs-lookup"><span data-stu-id="8dbd7-107">**SQLSpecialColumns** can be executed on a static cursor.</span></span> <span data-ttu-id="8dbd7-108">嘗試在可更新的 (索引鍵集驅動或動態) 上執行**SQLSpecialColumns**時，會傳回 SQL_SUCCESS_WITH_INFO 指出資料指標類型已變更。</span><span class="sxs-lookup"><span data-stu-id="8dbd7-108">An attempt to execute **SQLSpecialColumns** on an updatable (keyset-driven or dynamic) returns SQL_SUCCESS_WITH_INFO indicating the cursor type has been changed.</span></span>  
  
## <a name="sqlspecialcolumns-support-for-enhanced-date-and-time-features"></a><span data-ttu-id="8dbd7-109">增強型日期和時間功能的 SQLSpecialColumns 支援</span><span class="sxs-lookup"><span data-stu-id="8dbd7-109">SQLSpecialColumns Support for Enhanced Date and Time Features</span></span>  
 <span data-ttu-id="8dbd7-110">如需日期/時間類型 DATA_TYPE、TYPE_NAME、COLUMN_SIZE、BUFFER_LENGTH 和 DECIMAL_DIGTS 之資料行傳回值的相關資訊，請參閱[目錄中繼資料](../native-client-odbc-date-time/metadata-catalog.md)。</span><span class="sxs-lookup"><span data-stu-id="8dbd7-110">For information about the values returned for the columns DATA_TYPE, TYPE_NAME, COLUMN_SIZE, BUFFER_LENGTH, and DECIMAL_DIGTS for date/time types, see [Catalog Metadata](../native-client-odbc-date-time/metadata-catalog.md).</span></span>  
  
 <span data-ttu-id="8dbd7-111">如需更多一般資訊，請參閱[ODBC&#41;&#40;的日期和時間改善](../native-client-odbc-date-time/date-and-time-improvements-odbc.md)。</span><span class="sxs-lookup"><span data-stu-id="8dbd7-111">For more general information, see [Date and Time Improvements &#40;ODBC&#41;](../native-client-odbc-date-time/date-and-time-improvements-odbc.md).</span></span>  
  
## <a name="sqlspecialcolumns-support-for-large-clr-udts"></a><span data-ttu-id="8dbd7-112">大型 CLR UDT 的 SQLSpecialColumns 支援</span><span class="sxs-lookup"><span data-stu-id="8dbd7-112">SQLSpecialColumns Support for Large CLR UDTs</span></span>  
 <span data-ttu-id="8dbd7-113">**SQLSpecialColumns**支援 (udt) 的大型 CLR 使用者定義類型。</span><span class="sxs-lookup"><span data-stu-id="8dbd7-113">**SQLSpecialColumns** supports large CLR user-defined types (UDTs).</span></span> <span data-ttu-id="8dbd7-114">如需詳細資訊，請參閱[&#40;ODBC&#41;的大型 CLR 使用者定義類型](../native-client/odbc/large-clr-user-defined-types-odbc.md)。</span><span class="sxs-lookup"><span data-stu-id="8dbd7-114">For more information, see [Large CLR User-Defined Types &#40;ODBC&#41;](../native-client/odbc/large-clr-user-defined-types-odbc.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8dbd7-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8dbd7-115">See Also</span></span>  
 <span data-ttu-id="8dbd7-116">[SQLSpecialColumns 函式](https://go.microsoft.com/fwlink/?LinkId=59371) </span><span class="sxs-lookup"><span data-stu-id="8dbd7-116">[SQLSpecialColumns Function](https://go.microsoft.com/fwlink/?LinkId=59371) </span></span>  
 [<span data-ttu-id="8dbd7-117">ODBC API 實作詳細資料</span><span class="sxs-lookup"><span data-stu-id="8dbd7-117">ODBC API Implementation Details</span></span>](odbc-api-implementation-details.md)  
  
  
