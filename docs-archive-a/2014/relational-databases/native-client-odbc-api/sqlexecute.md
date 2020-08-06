---
title: SQLExecute |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQLExecute function
ms.assetid: 4d7db8b6-611f-4fe4-be85-2a407059de45
author: rothja
ms.author: jroth
ms.openlocfilehash: 514436c65ef103cafae2189a03b560255b447eda
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594985"
---
# <a name="sqlexecute"></a><span data-ttu-id="ca764-102">SQLExecute</span><span class="sxs-lookup"><span data-stu-id="ca764-102">SQLExecute</span></span>
  <span data-ttu-id="ca764-103">如果 SQL_SOPT_SS_PARAM_FOCUS 的語句屬性未設定為0，則 SQLExecute 會傳回 SQL_ERROR，並產生含有 SQLSTATE = HY024 的診斷記錄，而在執行時，SQL_SOPT_SS_PARAM_FOCUS (必須為零) 」的訊息。</span><span class="sxs-lookup"><span data-stu-id="ca764-103">If the statement attribute SQL_SOPT_SS_PARAM_FOCUS is not set to 0, SQLExecute will return SQL_ERROR and generate a diagnostic record with SQLSTATE=HY024 and the message "Invalid attribute value, SQL_SOPT_SS_PARAM_FOCUS (must be zero at execution time)".</span></span> <span data-ttu-id="ca764-104">如需 SQL_SOPT_SS_PARAM_FOCUS 的詳細資訊，請參閱[SQLSetStmtAttr](sqlsetstmtattr.md)。</span><span class="sxs-lookup"><span data-stu-id="ca764-104">For more information about SQL_SOPT_SS_PARAM_FOCUS, see [SQLSetStmtAttr](sqlsetstmtattr.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ca764-105">備註</span><span class="sxs-lookup"><span data-stu-id="ca764-105">Remarks</span></span>  
 <span data-ttu-id="ca764-106">如需資料表值參數的詳細資訊，請參閱[ODBC&#41;&#40;的資料表值參數](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)。</span><span class="sxs-lookup"><span data-stu-id="ca764-106">For more information about table-valued parameters, see [Table-Valued Parameters &#40;ODBC&#41;](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca764-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ca764-107">See Also</span></span>  
 <span data-ttu-id="ca764-108">[SQLExecute](https://go.microsoft.com/fwlink/?LinkId=80708) </span><span class="sxs-lookup"><span data-stu-id="ca764-108">[SQLExecute](https://go.microsoft.com/fwlink/?LinkId=80708) </span></span>  
 [<span data-ttu-id="ca764-109">ODBC API 實作詳細資料</span><span class="sxs-lookup"><span data-stu-id="ca764-109">ODBC API Implementation Details</span></span>](odbc-api-implementation-details.md)  
  
  
