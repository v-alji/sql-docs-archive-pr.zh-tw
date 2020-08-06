---
title: SQLEndTran |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLEndTran function
ms.assetid: 95cff841-c2d5-4e1e-a18d-f3d4696a5b85
author: rothja
ms.author: jroth
ms.openlocfilehash: e5d44756131b6133baec69e34da11055a965e2da
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87698182"
---
# <a name="sqlendtran"></a><span data-ttu-id="aa14f-102">SQLEndTran</span><span class="sxs-lookup"><span data-stu-id="aa14f-102">SQLEndTran</span></span>
  <span data-ttu-id="aa14f-103">根據預設， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 當**SQLEndTran**認可或回復作業時，Native Client ODBC 驅動程式會關閉語句的相關資料指標。</span><span class="sxs-lookup"><span data-stu-id="aa14f-103">By default, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver closes a statement's associated cursor when **SQLEndTran** commits or rolls back an operation.</span></span> <span data-ttu-id="aa14f-104">除非伺服器資料指標是靜態的，否則會關閉它們。</span><span class="sxs-lookup"><span data-stu-id="aa14f-104">Server cursors are closed unless they are static.</span></span> <span data-ttu-id="aa14f-105">當**SQLEndTran**認可或回復作業時，語句相關資料指標的行為是由驅動程式特定的 ODBC 連接屬性值所決定，SQL_COPT_SS_PRESERVE_CURSORS，由[SQLSetConnectAttr](sqlsetconnectattr.md)設定。</span><span class="sxs-lookup"><span data-stu-id="aa14f-105">When **SQLEndTran** commits or rolls back an operation, the behavior of the statement's associated cursor is determined by the value of the driver-specific ODBC connection attribute SQL_COPT_SS_PRESERVE_CURSORS, set by [SQLSetConnectAttr](sqlsetconnectattr.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa14f-106">另請參閱</span><span class="sxs-lookup"><span data-stu-id="aa14f-106">See Also</span></span>  
 <span data-ttu-id="aa14f-107">[ODBC API 的執行詳細資料](odbc-api-implementation-details.md) </span><span class="sxs-lookup"><span data-stu-id="aa14f-107">[ODBC API Implementation Details](odbc-api-implementation-details.md) </span></span>  
 [<span data-ttu-id="aa14f-108">SQLEndTran 函數</span><span class="sxs-lookup"><span data-stu-id="aa14f-108">SQLEndTran Function</span></span>](https://go.microsoft.com/fwlink/?LinkId=59342)  
  
  
