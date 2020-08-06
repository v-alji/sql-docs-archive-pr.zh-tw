---
title: 將 ODBC 中的資料列加上書簽 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- cursors [ODBC], fetching rows
- ODBC cursors, fetching rows
- cursors [ODBC], scrolling rows
- ODBC cursors, scrolling rows
- bookmarks [ODBC]
ms.assetid: 9cfcd243-c9d4-4c2a-abc4-399dbabe5f6b
author: rothja
ms.author: jroth
ms.openlocfilehash: def05f478c16dcbcdc91771925a11b0b91da2e9e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707525"
---
# <a name="bookmarking-rows-in-odbc"></a><span data-ttu-id="d25fe-102">在 ODBC 中的資料列上加上書籤</span><span class="sxs-lookup"><span data-stu-id="d25fe-102">Bookmarking Rows in ODBC</span></span>
  <span data-ttu-id="d25fe-103">書籤是用來識別資料列的值。</span><span class="sxs-lookup"><span data-stu-id="d25fe-103">A bookmark is a value used to identify a row of data.</span></span> <span data-ttu-id="d25fe-104">書籤值的意義僅適用於驅動程式或資料來源。</span><span class="sxs-lookup"><span data-stu-id="d25fe-104">The meaning of the bookmark value is known only to the driver or data source.</span></span> <span data-ttu-id="d25fe-105">例如，書籤可能跟資料列號碼一樣簡單，也可能跟磁碟位址一樣複雜。</span><span class="sxs-lookup"><span data-stu-id="d25fe-105">For example, it might be as simple as a row number or as complex as a disk address.</span></span> <span data-ttu-id="d25fe-106">在 ODBC 中，應用程式會要求特定資料列的書籤、將其儲存起來，然後將其傳回資料指標，即可傳回到資料列。</span><span class="sxs-lookup"><span data-stu-id="d25fe-106">In ODBC, the application requests a bookmark for a particular row, stores it, and passes it back to the cursor to return to the row.</span></span>  
  
 <span data-ttu-id="d25fe-107">使用[SQLFetchScroll](../native-client-odbc-api/sqlfetchscroll.md)來提取資料列時，應用程式可以使用書簽做為選取起始資料列的基礎。</span><span class="sxs-lookup"><span data-stu-id="d25fe-107">When fetching rows with [SQLFetchScroll](../native-client-odbc-api/sqlfetchscroll.md), an application can use a bookmark as a basis for selecting the starting row.</span></span> <span data-ttu-id="d25fe-108">這是一個絕對位址的形式，因為它不相依於目前的資料指標位置。</span><span class="sxs-lookup"><span data-stu-id="d25fe-108">This is a form of absolute addressing because it does not depend on the current cursor position.</span></span> <span data-ttu-id="d25fe-109">若要滾動到已加入書簽的資料列，應用程式會使用 SQL_FETCH_BOOKMARK 的*FetchOrientation*來呼叫**SQLFetchScroll** 。</span><span class="sxs-lookup"><span data-stu-id="d25fe-109">To scroll to a bookmarked row, the application calls **SQLFetchScroll** with a *FetchOrientation* of SQL_FETCH_BOOKMARK.</span></span> <span data-ttu-id="d25fe-110">此作業使用 SQL_ATTR_FETCH_BOOKMARK_PTR 選項屬性所指向的書籤。</span><span class="sxs-lookup"><span data-stu-id="d25fe-110">This operation uses the bookmark pointed to by the SQL_ATTR_FETCH_BOOKMARK_PTR option attribute.</span></span> <span data-ttu-id="d25fe-111">它會傳回資料列集，從該書籤識別的資料列開始。</span><span class="sxs-lookup"><span data-stu-id="d25fe-111">It returns the rowset starting with the row identified by that bookmark.</span></span> <span data-ttu-id="d25fe-112">應用程式可以在呼叫**SQLFetchScroll**的*FetchOffset*引數中，指定此作業的位移。</span><span class="sxs-lookup"><span data-stu-id="d25fe-112">An application can specify an offset for this operation in the *FetchOffset* argument of the call to **SQLFetchScroll**.</span></span> <span data-ttu-id="d25fe-113">指定位移時，所傳回之資料列集的第一個資料列會透過將 FetchOffset 引數中的數字加入到書籤所識別之資料列數目決定。</span><span class="sxs-lookup"><span data-stu-id="d25fe-113">When an offset is specified, the first row of the returned rowset is determined by adding the number in the FetchOffset argument to the number of the row identified by the bookmark.</span></span> <span data-ttu-id="d25fe-114">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC 驅動程式僅針對靜態和索引鍵集資料指標支援書籤。</span><span class="sxs-lookup"><span data-stu-id="d25fe-114">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver only supports bookmarks on static and keyset cursors.</span></span> <span data-ttu-id="d25fe-115">如果設定書籤開啟時要求動態資料指標，就會改為開啟索引鍵集。</span><span class="sxs-lookup"><span data-stu-id="d25fe-115">If a dynamic cursor is requested when bookmarks are set on, a keyset cursor is opened instead.</span></span>  
  
 <span data-ttu-id="d25fe-116">書簽也可以與**SQLBulkOperations**函式搭配使用，以便在從書簽開始的一組資料列上執行作業。</span><span class="sxs-lookup"><span data-stu-id="d25fe-116">Bookmarks can also be used with the **SQLBulkOperations** function to perform operations on a set of rows starting at the bookmark.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d25fe-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d25fe-117">See Also</span></span>  
 [<span data-ttu-id="d25fe-118">捲動與提取資料列</span><span class="sxs-lookup"><span data-stu-id="d25fe-118">Scrolling and Fetching Rows</span></span>](../native-client-ole-db-rowsets/fetching-rows.md)  
  
  
