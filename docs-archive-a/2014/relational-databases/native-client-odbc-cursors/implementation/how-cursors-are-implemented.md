---
title: 如何實作為資料指標 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, cursors
- ODBC cursors, about ODBC cursors
- ODBC applications, cursors
- cursors [ODBC], about ODBC cursors
ms.assetid: 2b1d7dd4-08a4-43fc-b3eb-70c183d0941f
author: rothja
ms.author: jroth
ms.openlocfilehash: 18995355b825d9cb1e62b4794429b5e98ef2b472
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594076"
---
# <a name="how-cursors-are-implemented"></a><span data-ttu-id="227eb-102">如何實作資料指標</span><span class="sxs-lookup"><span data-stu-id="227eb-102">How Cursors Are Implemented</span></span>
  <span data-ttu-id="227eb-103">ODBC 應用程式會在執行 SQL 陳述式之前設定一或多個陳述式屬性，藉此來控制資料指標的行為。</span><span class="sxs-lookup"><span data-stu-id="227eb-103">ODBC applications control the behavior of a cursor by setting one or more statement attributes before executing an SQL statement.</span></span> <span data-ttu-id="227eb-104">ODBC 有兩個不同的方法可指定資料指標的特性：</span><span class="sxs-lookup"><span data-stu-id="227eb-104">ODBC has two different ways to specify the characteristics of a cursor:</span></span>  
  
-   <span data-ttu-id="227eb-105">資料指標類型</span><span class="sxs-lookup"><span data-stu-id="227eb-105">Cursor type</span></span>  
  
     <span data-ttu-id="227eb-106">資料指標類型是使用[SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md)的 SQL_ATTR_CURSOR_TYPE 屬性來設定。</span><span class="sxs-lookup"><span data-stu-id="227eb-106">Cursor types are set using the SQL_ATTR_CURSOR_TYPE attribute of [SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md).</span></span> <span data-ttu-id="227eb-107">ODBC 資料指標類型為順向、靜態、索引鍵集驅動、混合式和動態。</span><span class="sxs-lookup"><span data-stu-id="227eb-107">The ODBC cursor types are forward-only, static, keyset-driven, mixed, and dynamic.</span></span> <span data-ttu-id="227eb-108">設定資料指標類型是在 ODBC 中指定資料指標的原始方法。</span><span class="sxs-lookup"><span data-stu-id="227eb-108">Setting the cursor type was the original method of specifying cursors in ODBC.</span></span>  
  
-   <span data-ttu-id="227eb-109">資料指標行為</span><span class="sxs-lookup"><span data-stu-id="227eb-109">Cursor behavior</span></span>  
  
     <span data-ttu-id="227eb-110">資料指標行為是使用**SQLSetStmtAttr**的 SQL_ATTR_CURSOR_SCROLLABLE 和 SQL_ATTR_CURSOR_SENSITIVITY 屬性來設定。</span><span class="sxs-lookup"><span data-stu-id="227eb-110">Cursor behavior is set using the SQL_ATTR_CURSOR_SCROLLABLE and SQL_ATTR_CURSOR_SENSITIVITY attributes of **SQLSetStmtAttr**.</span></span> <span data-ttu-id="227eb-111">這些屬性是根據 ISO 標準中針對 DECLARE CURSOR 陳述式定義的 SCROLL 和 SENSITIVE 關鍵字來模型化。</span><span class="sxs-lookup"><span data-stu-id="227eb-111">These attributes are modeled on the SCROLL and SENSITIVE keywords defined for the DECLARE CURSOR statement in ISO standards.</span></span> <span data-ttu-id="227eb-112">這兩個 ISO 選項是在 ODBC 3.0 版中導入。</span><span class="sxs-lookup"><span data-stu-id="227eb-112">These two ISO options were introduced in ODBC version 3.0.</span></span>  
  
 <span data-ttu-id="227eb-113">應該使用這兩個方法的其中一個來指定 ODBC 資料指標的特性，並將喜好設定設定為 ODBC 資料指標類型。</span><span class="sxs-lookup"><span data-stu-id="227eb-113">The characteristics of an ODBC cursor should be specified using either one or the other of these two methods, with the preference being to use the ODBC cursor types.</span></span>  
  
 <span data-ttu-id="227eb-114">除了設定資料指標的類型以外，ODBC 應用程式也會設定其他選項，例如每一個提取所傳回的資料列數、並行選項和交易隔離等級。</span><span class="sxs-lookup"><span data-stu-id="227eb-114">In addition to setting the type of a cursor, ODBC applications also set other options, such as the number of rows returned on each fetch, concurrency options, and transaction isolation levels.</span></span> <span data-ttu-id="227eb-115">可以針對 ODBC 樣式的資料指標 (順向、靜態、索引鍵集驅動、混合式和動態) 或 ISO 樣式的資料指標 (可捲動性和敏感性) 來設定這些選項。</span><span class="sxs-lookup"><span data-stu-id="227eb-115">These options can be set for either ODBC-style cursors (forward-only, static, keyset-driven, mixed, and dynamic) or ISO style cursors (scrollability and sensitivity).</span></span>  
  
 <span data-ttu-id="227eb-116">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native CLIENT ODBC 驅動程式支援數種實際執行各種類型資料指標的方式。</span><span class="sxs-lookup"><span data-stu-id="227eb-116">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver supports several ways to physically implement the various types of cursors.</span></span> <span data-ttu-id="227eb-117">此驅動程式會使用預設 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 結果集來實作某些類型的資料指標，並使用 ODBC 資料指標程式庫將其他類型實作為伺服器資料指標。</span><span class="sxs-lookup"><span data-stu-id="227eb-117">The driver implements some types of cursors using a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] default result set; it implements others as server cursors or by using the ODBC Cursor Library.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="227eb-118">本節內容</span><span class="sxs-lookup"><span data-stu-id="227eb-118">In This Section</span></span>  
  
-   [<span data-ttu-id="227eb-119">使用 QL Server 預設結果集</span><span class="sxs-lookup"><span data-stu-id="227eb-119">Using SQL Server Default Result Sets</span></span>](using-sql-server-default-result-sets.md)  
  
-   [<span data-ttu-id="227eb-120">使用伺服器資料指標</span><span class="sxs-lookup"><span data-stu-id="227eb-120">Using Server Cursors</span></span>](using-server-cursors.md)  
  
-   [<span data-ttu-id="227eb-121">ODBC 資料指標程式庫</span><span class="sxs-lookup"><span data-stu-id="227eb-121">ODBC Cursor Library</span></span>](odbc-cursor-library.md)  
  
## <a name="see-also"></a><span data-ttu-id="227eb-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="227eb-122">See Also</span></span>  
 [<span data-ttu-id="227eb-123">&#40;ODBC&#41;使用資料指標</span><span class="sxs-lookup"><span data-stu-id="227eb-123">Using Cursors &#40;ODBC&#41;</span></span>](../using-cursors-odbc.md)  
  
  
