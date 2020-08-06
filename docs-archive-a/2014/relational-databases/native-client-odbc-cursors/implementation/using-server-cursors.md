---
title: 使用伺服器資料指標 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- ODBC applications, cursors
- cursors [ODBC], server cursors
- ODBC cursors, server cursors
- server cursors [SQL Server]
ms.assetid: 8a6d99b7-10b8-4474-8639-4914b25ba170
author: rothja
ms.author: jroth
ms.openlocfilehash: e596af3c46849313d813ce2d7f1dab2a7425c090
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594067"
---
# <a name="using-server-cursors"></a><span data-ttu-id="b431f-102">使用伺服器資料指標</span><span class="sxs-lookup"><span data-stu-id="b431f-102">Using Server Cursors</span></span>
  <span data-ttu-id="b431f-103">如果 ODBC 應用程式將任何 ODBC 資料指標屬性設定為預設值以外的任何專案， [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native CLIENT ODBC 驅動程式會要求伺服器執行相同類型的 API 伺服器資料指標。</span><span class="sxs-lookup"><span data-stu-id="b431f-103">If an ODBC application sets any of the ODBC cursor attributes to anything other than the defaults, the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver requests the server to implement an API server cursor of the same type.</span></span> <span data-ttu-id="b431f-104">使用 API 伺服器資料指標可以釋放用戶端上的記憶體，而且可以大幅降低用戶端與伺服器之間的網路流量。</span><span class="sxs-lookup"><span data-stu-id="b431f-104">Using API server cursors frees memory on the client and can significantly reduce network traffic between the client and server.</span></span>  
  
 <span data-ttu-id="b431f-105">API 伺服端資料指標的潛在缺點是目前不支援所有 SQL 陳述式。</span><span class="sxs-lookup"><span data-stu-id="b431f-105">A potential drawback of API server cursors is that they currently do not support all SQL statements.</span></span> <span data-ttu-id="b431f-106">API 伺服端資料指標無法用來執行：</span><span class="sxs-lookup"><span data-stu-id="b431f-106">API server cursors cannot be used to execute:</span></span>  
  
-   <span data-ttu-id="b431f-107">傳回多個結果集的批次或預存程序。</span><span class="sxs-lookup"><span data-stu-id="b431f-107">Batches or stored procedures that return multiple result sets.</span></span>  
  
-   <span data-ttu-id="b431f-108">包含 COMPUTE、COMPUTE BY、FOR BROWSE 或 INTO 子句的 SELECT 陳述式。</span><span class="sxs-lookup"><span data-stu-id="b431f-108">SELECT statements that contain COMPUTE, COMPUTE BY, FOR BROWSE, or INTO clauses.</span></span>  
  
-   <span data-ttu-id="b431f-109">參考遠端預存程序的 EXECUTE 陳述式。</span><span class="sxs-lookup"><span data-stu-id="b431f-109">An EXECUTE statement referencing a remote stored procedure.</span></span>  
  
 <span data-ttu-id="b431f-110">連接到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 的執行個體時，使用伺服器資料指標執行包含這些特性的陳述式會使資料指標轉換為預設的結果集。</span><span class="sxs-lookup"><span data-stu-id="b431f-110">When connected to an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], executing a statement with these characteristics using a server cursor causes the cursor being converted to a default result set.</span></span> <span data-ttu-id="b431f-111">連接到舊版 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 時，它會導致錯誤。</span><span class="sxs-lookup"><span data-stu-id="b431f-111">When connected to earlier versions of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], it causes an error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b431f-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b431f-112">See Also</span></span>  
 [<span data-ttu-id="b431f-113">如何實作資料指標</span><span class="sxs-lookup"><span data-stu-id="b431f-113">How Cursors Are Implemented</span></span>](how-cursors-are-implemented.md)  
  
  
