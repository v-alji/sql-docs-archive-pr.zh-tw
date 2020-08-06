---
title: SQLCloseCursor |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLCloseCursor function
ms.assetid: e7134d65-5c1c-4ae2-b119-d9b4b9a42483
author: rothja
ms.author: jroth
ms.openlocfilehash: 770a67432868516e5023d1cf0ff819501b4c130e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709382"
---
# <a name="sqlclosecursor"></a><span data-ttu-id="130c4-102">SQLCloseCursor</span><span class="sxs-lookup"><span data-stu-id="130c4-102">SQLCloseCursor</span></span>
  <span data-ttu-id="130c4-103">**SQLCloseCursor**會將[SQLFreeStmt](sqlfreestmt.md)取代為 SQL_CLOSE 的*選項*值。</span><span class="sxs-lookup"><span data-stu-id="130c4-103">**SQLCloseCursor** replaces [SQLFreeStmt](sqlfreestmt.md) with an *Option* value of SQL_CLOSE.</span></span> <span data-ttu-id="130c4-104">在收到**SQLCloseCursor**時， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC 驅動程式會捨棄暫止的結果集資料列。</span><span class="sxs-lookup"><span data-stu-id="130c4-104">On receipt of **SQLCloseCursor**, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver discards pending result set rows.</span></span> <span data-ttu-id="130c4-105">請注意， **SQLCloseCursor**不會改變語句的資料行和參數系結 (是否有任何) 。</span><span class="sxs-lookup"><span data-stu-id="130c4-105">Note that the statement's column and parameter bindings (if any exist) are left unaltered by **SQLCloseCursor**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="130c4-106">另請參閱</span><span class="sxs-lookup"><span data-stu-id="130c4-106">See Also</span></span>  
 <span data-ttu-id="130c4-107">[SQLCloseCursor](https://go.microsoft.com/fwlink/?LinkId=59331) </span><span class="sxs-lookup"><span data-stu-id="130c4-107">[SQLCloseCursor](https://go.microsoft.com/fwlink/?LinkId=59331) </span></span>  
 [<span data-ttu-id="130c4-108">ODBC API 實作詳細資料</span><span class="sxs-lookup"><span data-stu-id="130c4-108">ODBC API Implementation Details</span></span>](odbc-api-implementation-details.md)  
  
  
