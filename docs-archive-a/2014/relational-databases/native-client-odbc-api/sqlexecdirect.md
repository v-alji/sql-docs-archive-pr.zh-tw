---
title: SQLExecDirect |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQLExecDirect function
ms.assetid: e7c2a5b5-83f4-4c72-9aca-7b9fb4748b11
author: rothja
ms.author: jroth
ms.openlocfilehash: 68188506546e7b4a5dd4c05bc9a94cbf34300001
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594994"
---
# <a name="sqlexecdirect"></a><span data-ttu-id="5bcb6-102">SQLExecDirect</span><span class="sxs-lookup"><span data-stu-id="5bcb6-102">SQLExecDirect</span></span>
  <span data-ttu-id="5bcb6-103">如果語句屬性 SQL_SOPT_SS_PARAM_FOCUS 不是0，則 SQLExecDirect 會傳回 SQL_ERROR 並產生含有 SQLSTATE = HY024 的診斷記錄，而在執行時，SQL_SOPT_SS_PARAM_FOCUS (必須為零，) 」的訊息。</span><span class="sxs-lookup"><span data-stu-id="5bcb6-103">If the statement attribute SQL_SOPT_SS_PARAM_FOCUS is not 0, SQLExecDirect will return SQL_ERROR and generate a diagnostic record with SQLSTATE=HY024 and the message "Invalid attribute value, SQL_SOPT_SS_PARAM_FOCUS (must be zero at execution time)".</span></span> <span data-ttu-id="5bcb6-104">如需 SQL_SOPT_SS_PARAM_FOCUS 的詳細資訊，請參閱[SQLSetStmtAttr](sqlsetstmtattr.md)。</span><span class="sxs-lookup"><span data-stu-id="5bcb6-104">For more information about SQL_SOPT_SS_PARAM_FOCUS, see [SQLSetStmtAttr](sqlsetstmtattr.md).</span></span>  
  
 <span data-ttu-id="5bcb6-105">如需資料表值參數的詳細資訊，請參閱[ODBC&#41;&#40;的資料表值參數](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)。</span><span class="sxs-lookup"><span data-stu-id="5bcb6-105">For more information about table-valued parameters, see [Table-Valued Parameters &#40;ODBC&#41;](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5bcb6-106">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5bcb6-106">See Also</span></span>  
 <span data-ttu-id="5bcb6-107">[SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=80709) </span><span class="sxs-lookup"><span data-stu-id="5bcb6-107">[SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=80709) </span></span>  
 [<span data-ttu-id="5bcb6-108">ODBC API 實作詳細資料</span><span class="sxs-lookup"><span data-stu-id="5bcb6-108">ODBC API Implementation Details</span></span>](odbc-api-implementation-details.md)  
  
  
