---
title: 資料指標行為 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- scrollable cursors [SQL Server]
- SQL Server Native Client ODBC driver, cursors
- version-based optimistic concurrency
- cursors [ODBC], cursor behaviors
- ODBC applications, cursors
- SQL_ATTR_CURSOR_SENSITIVITY option
- SQL_ATTR_CURSOR_SCROLLABLE option
- sensitivity behavior of cursor
- ODBC cursors, cursor behaviors
ms.assetid: 742ddcd2-232b-4aa1-9212-027df120ad35
author: rothja
ms.author: jroth
ms.openlocfilehash: 89c7c4e9a8dcffe03dd12f8013d5ed43810547f3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595943"
---
# <a name="cursor-behaviors"></a><span data-ttu-id="799fe-102">資料指標行為</span><span class="sxs-lookup"><span data-stu-id="799fe-102">Cursor Behaviors</span></span>
  <span data-ttu-id="799fe-103">ODBC 透過指定資料指標的可捲動性和敏感度，支援指定其行為的 ISO 選項。</span><span class="sxs-lookup"><span data-stu-id="799fe-103">ODBC supports the ISO options for specifying the behavior of cursors by specifying their scrollability and sensitivity.</span></span> <span data-ttu-id="799fe-104">這些行為是藉由在[SQLSetStmtAttr](../native-client-odbc-api/sqlsetstmtattr.md)的呼叫上設定 SQL_ATTR_CURSOR_SCROLLABLE 和 SQL_ATTR_CURSOR_SENSITIVITY 選項來指定。</span><span class="sxs-lookup"><span data-stu-id="799fe-104">These behaviors are specified by setting the SQL_ATTR_CURSOR_SCROLLABLE and SQL_ATTR_CURSOR_SENSITIVITY options on a call to [SQLSetStmtAttr](../native-client-odbc-api/sqlsetstmtattr.md).</span></span> <span data-ttu-id="799fe-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC 驅動程式會要求包含下列特性的伺服器資料指標，藉以實作這些選項。</span><span class="sxs-lookup"><span data-stu-id="799fe-105">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver implements these options by requesting server cursors with the following characteristics.</span></span>  
  
|<span data-ttu-id="799fe-106">資料指標行為設定</span><span class="sxs-lookup"><span data-stu-id="799fe-106">Cursor behavior settings</span></span>|<span data-ttu-id="799fe-107">要求的伺服器資料指標特性</span><span class="sxs-lookup"><span data-stu-id="799fe-107">Server cursor characteristics requested</span></span>|  
|------------------------------|---------------------------------------------|  
|<span data-ttu-id="799fe-108">SQL_SCROLLABLE 和 SQL_SENSITIVE</span><span class="sxs-lookup"><span data-stu-id="799fe-108">SQL_SCROLLABLE and SQL_SENSITIVE</span></span>|<span data-ttu-id="799fe-109">索引鍵集驅動資料指標和以版本為基礎的開放式並行存取</span><span class="sxs-lookup"><span data-stu-id="799fe-109">Keyset-driven cursor and version-based optimistic concurrency</span></span>|  
|<span data-ttu-id="799fe-110">SQL_SCROLLABLE 和 SQL_INSENSITIVE</span><span class="sxs-lookup"><span data-stu-id="799fe-110">SQL_SCROLLABLE and SQL_INSENSITIVE</span></span>|<span data-ttu-id="799fe-111">靜態資料指標和唯讀並行存取</span><span class="sxs-lookup"><span data-stu-id="799fe-111">Static cursor and read-only concurrency</span></span>|  
|<span data-ttu-id="799fe-112">SQL_SCROLLABLE 和 SQL_UNSPECIFIED</span><span class="sxs-lookup"><span data-stu-id="799fe-112">SQL_SCROLLABLE and SQL_UNSPECIFIED</span></span>|<span data-ttu-id="799fe-113">靜態資料指標和唯讀並行存取</span><span class="sxs-lookup"><span data-stu-id="799fe-113">Static cursor and read-only concurrency</span></span>|  
|<span data-ttu-id="799fe-114">SQL_NONSCROLLABLE 和 SQL_SENSITIVE</span><span class="sxs-lookup"><span data-stu-id="799fe-114">SQL_NONSCROLLABLE and SQL_SENSITIVE</span></span>|<span data-ttu-id="799fe-115">順向資料指標和以版本為基礎的開放式並行存取</span><span class="sxs-lookup"><span data-stu-id="799fe-115">Forward-only cursor and version-based optimistic concurrency</span></span>|  
|<span data-ttu-id="799fe-116">SQL_NONSCROLLABLE 和 SQL_INSENSITIVE</span><span class="sxs-lookup"><span data-stu-id="799fe-116">SQL_NONSCROLLABLE and SQL_INSENSITIVE</span></span>|<span data-ttu-id="799fe-117">預設結果集 (順向、唯讀)</span><span class="sxs-lookup"><span data-stu-id="799fe-117">Default result set (forward-only, read-only)</span></span>|  
|<span data-ttu-id="799fe-118">SQL_NONSCROLLABLE 和 SQL_UNSPECIFIED</span><span class="sxs-lookup"><span data-stu-id="799fe-118">SQL_NONSCROLLABLE and SQL_UNSPECIFIED</span></span>|<span data-ttu-id="799fe-119">預設結果集 (順向、唯讀)</span><span class="sxs-lookup"><span data-stu-id="799fe-119">Default result set (forward-only, read-only)</span></span>|  
  
 <span data-ttu-id="799fe-120">以版本為基礎的開放式平行存取需要基礎資料表中的**timestamp**資料行。</span><span class="sxs-lookup"><span data-stu-id="799fe-120">Version-based optimistic concurrency requires a **timestamp** column in the underlying table.</span></span> <span data-ttu-id="799fe-121">如果在沒有**timestamp**資料行的資料表上要求以版本為基礎的開放式並行存取控制，伺服器就會使用以值為基礎的開放式平行存取。</span><span class="sxs-lookup"><span data-stu-id="799fe-121">If version-based optimistic concurrency control is requested on a table that does not have a **timestamp** column, the server uses values-based optimistic concurrency.</span></span>  
  
## <a name="scrollability"></a><span data-ttu-id="799fe-122">可捲動性</span><span class="sxs-lookup"><span data-stu-id="799fe-122">Scrollability</span></span>  
 <span data-ttu-id="799fe-123">當 SQL_ATTR_CURSOR_SCROLLABLE 設定為 SQL_SCROLLABLE 時，資料指標會針對[SQLFetchScroll](../native-client-odbc-api/sqlfetchscroll.md)的*FetchOrientation*參數支援所有不同的值。</span><span class="sxs-lookup"><span data-stu-id="799fe-123">When SQL_ATTR_CURSOR_SCROLLABLE is set to SQL_SCROLLABLE, the cursor supports all the different values for the *FetchOrientation* parameter of [SQLFetchScroll](../native-client-odbc-api/sqlfetchscroll.md).</span></span> <span data-ttu-id="799fe-124">當 SQL_ATTR_CURSOR_SCROLLABLE 設定為 SQL_NONSCROLLABLE 時，資料指標只支援 SQL_FETCH_NEXT 的*FetchOrientation*值。</span><span class="sxs-lookup"><span data-stu-id="799fe-124">When SQL_ATTR_CURSOR_SCROLLABLE is set to SQL_NONSCROLLABLE, the cursor only supports a *FetchOrientation* value of SQL_FETCH_NEXT.</span></span>  
  
## <a name="sensitivity"></a><span data-ttu-id="799fe-125">敏感度</span><span class="sxs-lookup"><span data-stu-id="799fe-125">Sensitivity</span></span>  
 <span data-ttu-id="799fe-126">當 SQL_ATTR_CURSOR_SENSITIVITY 設定為 SQL_SENSITIVE 時，資料指標會將目前使用者所進行或其他使用者所認可的資料修改反映出來。</span><span class="sxs-lookup"><span data-stu-id="799fe-126">When SQL_ATTR_CURSOR_SENSITIVITY is set to SQL_SENSITIVE, the cursor reflects data modifications made by the current user or committed by other users.</span></span> <span data-ttu-id="799fe-127">當 SQL_ATTR_CURSOR_SENSITIVITY 設定為 SQL_INSENSITIVE 時，資料指標不會反映資料修改。</span><span class="sxs-lookup"><span data-stu-id="799fe-127">When SQL_ATTR_CURSOR_SENSITIVITY is set to SQL_INSENSITIVE, the cursor does not reflect data modifications.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="799fe-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="799fe-128">See Also</span></span>  
 [<span data-ttu-id="799fe-129">&#40;ODBC&#41;使用資料指標</span><span class="sxs-lookup"><span data-stu-id="799fe-129">Using Cursors &#40;ODBC&#41;</span></span>](using-cursors-odbc.md)  
  
  
