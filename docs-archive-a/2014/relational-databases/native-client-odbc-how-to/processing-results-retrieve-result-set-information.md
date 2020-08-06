---
title: " (ODBC) 中取出結果集資訊 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- result sets [ODBC]
- result sets [ODBC], fetching
ms.assetid: 34f235e4-f80b-4123-8764-9deb18506f14
author: rothja
ms.author: jroth
ms.openlocfilehash: 0f7ed275eb9b6558a77160c3c7fb2fc233c199cc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594044"
---
# <a name="retrieve-result-set-information-odbc"></a><span data-ttu-id="e92e7-102">擷取結果集資訊 (ODBC)</span><span class="sxs-lookup"><span data-stu-id="e92e7-102">Retrieve Result Set Information (ODBC)</span></span>
    
### <a name="to-get-information-about-a-result-set"></a><span data-ttu-id="e92e7-103">取得結果集的相關資訊</span><span class="sxs-lookup"><span data-stu-id="e92e7-103">To get information about a result set</span></span>  
  
1.  <span data-ttu-id="e92e7-104">呼叫[SQLNumResultCols](../native-client-odbc-api/sqlnumresultcols.md)以取得結果集內的資料行數目。</span><span class="sxs-lookup"><span data-stu-id="e92e7-104">Call [SQLNumResultCols](../native-client-odbc-api/sqlnumresultcols.md) to get the number of columns in the result set.</span></span>  
  
2.  <span data-ttu-id="e92e7-105">對於結果集內的每個資料行：</span><span class="sxs-lookup"><span data-stu-id="e92e7-105">For each column in the result set:</span></span>  
  
    -   <span data-ttu-id="e92e7-106">呼叫[SQLDescribeCol](../native-client-odbc-api/sqldescribecol.md)以取得結果資料行的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="e92e7-106">Call [SQLDescribeCol](../native-client-odbc-api/sqldescribecol.md) to get information about the result column.</span></span>  
  
     <span data-ttu-id="e92e7-107">或者</span><span class="sxs-lookup"><span data-stu-id="e92e7-107">Or</span></span>  
  
    -   <span data-ttu-id="e92e7-108">呼叫[SQLColAttribute](../native-client-odbc-api/sqlcolattribute.md)以取得結果資料行的特定描述元資訊。</span><span class="sxs-lookup"><span data-stu-id="e92e7-108">Call [SQLColAttribute](../native-client-odbc-api/sqlcolattribute.md) to get specific descriptor information about the result column.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e92e7-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e92e7-109">See Also</span></span>  
 <span data-ttu-id="e92e7-110">[處理結果如何 &#40;ODBC&#41;的 how to 主題](../../database-engine/dev-guide/processing-results-how-to-topics-odbc.md) </span><span class="sxs-lookup"><span data-stu-id="e92e7-110">[Processing Results How-to Topics &#40;ODBC&#41;](../../database-engine/dev-guide/processing-results-how-to-topics-odbc.md) </span></span>  
 [<span data-ttu-id="e92e7-111">判斷結果集的特性 &#40;ODBC&#41;</span><span class="sxs-lookup"><span data-stu-id="e92e7-111">Determining the Characteristics of a Result Set &#40;ODBC&#41;</span></span>](../native-client-odbc-results/determining-the-characteristics-of-a-result-set-odbc.md)  
  
  
