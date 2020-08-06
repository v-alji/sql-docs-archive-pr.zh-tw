---
title: 書籤 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- bookmarks [OLE DB]
- SQL Server Native Client OLE DB provider, bookmarks
- rowsets [OLE DB], bookmarks
- OLE DB rowsets, bookmarks
ms.assetid: 7d9076f2-bf9c-452e-b816-70371a0c1644
author: rothja
ms.author: jroth
ms.openlocfilehash: be8e5486e5a442ddafa133a9cbd3f408d30a50d7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706413"
---
# <a name="bookmarks"></a><span data-ttu-id="d7078-102">書籤</span><span class="sxs-lookup"><span data-stu-id="d7078-102">Bookmarks</span></span>
  <span data-ttu-id="d7078-103">書籤可讓取用者快速地返回資料列。</span><span class="sxs-lookup"><span data-stu-id="d7078-103">Bookmarks let consumers quickly return to a row.</span></span> <span data-ttu-id="d7078-104">取用者可以利用書籤，根據書籤值隨機存取資料列。</span><span class="sxs-lookup"><span data-stu-id="d7078-104">With bookmarks, consumers can access rows randomly based on the bookmark value.</span></span> <span data-ttu-id="d7078-105">書籤資料行在資料列集中為資料行 0。</span><span class="sxs-lookup"><span data-stu-id="d7078-105">The bookmark column is column 0 in the rowset.</span></span> <span data-ttu-id="d7078-106">取用者會將繫結結構的 dwFlag 欄位值設定為 DBCOLUMNSINFO_ISBOOKMARK，表示該資料行會當做書籤使用。</span><span class="sxs-lookup"><span data-stu-id="d7078-106">The consumer sets the dwFlag field value of the binding structure to DBCOLUMNSINFO_ISBOOKMARK to indicate that the column is used as a bookmark.</span></span> <span data-ttu-id="d7078-107">取用者也會將資料列集屬性 DBPROP_BOOKMARKS 設定為 VARIANT_TRUE。</span><span class="sxs-lookup"><span data-stu-id="d7078-107">The consumer also sets the rowset property DBPROP_BOOKMARKS to VARIANT_TRUE.</span></span> <span data-ttu-id="d7078-108">這可讓資料行 0 出現在資料列集中。</span><span class="sxs-lookup"><span data-stu-id="d7078-108">This lets column 0 be present in the rowset.</span></span> <span data-ttu-id="d7078-109">然後使用 **IRowsetLocate::GetRowsAt** 方法來擷取資料列，從書籤中指定為位移的資料列開始。</span><span class="sxs-lookup"><span data-stu-id="d7078-109">The **IRowsetLocate::GetRowsAt** method is then used to fetch rows, starting with the row specified as an offset from a bookmark.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7078-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d7078-110">See Also</span></span>  
 [<span data-ttu-id="d7078-111">資料列集</span><span class="sxs-lookup"><span data-stu-id="d7078-111">Rowsets</span></span>](rowsets.md)  
  
  
