---
title: ODBC) 的資料指標並行 (|Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- concurrency [ODBC]
- cursors [ODBC], concurrency
- ODBC cursors, concurrency
ms.assetid: 68228ece-cbf1-4f19-bfdc-053884c1af48
author: rothja
ms.author: jroth
ms.openlocfilehash: c47f24152978fedf8f2c3d49ec3b721969712814
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598344"
---
# <a name="cursor-concurrency-odbc"></a><span data-ttu-id="d49e7-102">資料指標並行 (ODBC)</span><span class="sxs-lookup"><span data-stu-id="d49e7-102">Cursor Concurrency (ODBC)</span></span>
  <span data-ttu-id="d49e7-103">資料指標作業跟資料指標類型一樣，會受到應用程式設定之並行選項的影響。</span><span class="sxs-lookup"><span data-stu-id="d49e7-103">Cursor operations, like cursor types, are affected by the concurrency options set by the application.</span></span> <span data-ttu-id="d49e7-104">並行選項是使用[SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md)的 SQL_ATTR_CONCURRENCY 選項來設定。</span><span class="sxs-lookup"><span data-stu-id="d49e7-104">Concurrency options are set using the SQL_ATTR_CONCURRENCY option of [SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md).</span></span> <span data-ttu-id="d49e7-105">並行類型為：</span><span class="sxs-lookup"><span data-stu-id="d49e7-105">The concurrency types are:</span></span>  
  
-   <span data-ttu-id="d49e7-106">唯讀 (SQL_CONCUR_READONLY)</span><span class="sxs-lookup"><span data-stu-id="d49e7-106">Read-only (SQL_CONCUR_READONLY)</span></span>  
  
-   <span data-ttu-id="d49e7-107">值 (SQL_CONCUR_VALUES)</span><span class="sxs-lookup"><span data-stu-id="d49e7-107">Values (SQL_CONCUR_VALUES)</span></span>  
  
-   <span data-ttu-id="d49e7-108">資料列版本 (SQL_CONCUR_ROWVER)</span><span class="sxs-lookup"><span data-stu-id="d49e7-108">Row version (SQL_CONCUR_ROWVER)</span></span>  
  
-   <span data-ttu-id="d49e7-109">鎖定 (SQL_CONCUR_LOCK)</span><span class="sxs-lookup"><span data-stu-id="d49e7-109">Lock (SQL_CONCUR_LOCK)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d49e7-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d49e7-110">See Also</span></span>  
 [<span data-ttu-id="d49e7-111">資料指標屬性</span><span class="sxs-lookup"><span data-stu-id="d49e7-111">Cursor Properties</span></span>](cursor-properties.md)  
  
  
