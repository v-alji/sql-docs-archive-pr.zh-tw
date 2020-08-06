---
title: SQLProcedures |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLProcedures function
ms.assetid: ec41f017-f5e0-40ef-913a-65d206068631
author: rothja
ms.author: jroth
ms.openlocfilehash: e37f15841a36eb95c1e9263d137ba2734d622367
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606262"
---
# <a name="sqlprocedures"></a><span data-ttu-id="87e66-102">SQLProcedures</span><span class="sxs-lookup"><span data-stu-id="87e66-102">SQLProcedures</span></span>
  <span data-ttu-id="87e66-103">所有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 預存程序都會傳回值。</span><span class="sxs-lookup"><span data-stu-id="87e66-103">All [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] stored procedures return a value.</span></span> <span data-ttu-id="87e66-104">**SQLProcedures** PROCEDURE_TYPE 結果集資料行的報表 SQL_PT_FUNCTION。</span><span class="sxs-lookup"><span data-stu-id="87e66-104">**SQLProcedures** reports SQL_PT_FUNCTION for the result set column PROCEDURE_TYPE.</span></span>  
  
 <span data-ttu-id="87e66-105">**SQLProcedures**會傳回 SQL_SUCCESS *CatalogName、SchemaName*或*ProcName*參數的值是否存在。</span><span class="sxs-lookup"><span data-stu-id="87e66-105">**SQLProcedures** returns SQL_SUCCESS whether or not values exist for *CatalogName, SchemaName,* or *ProcName* parameters.</span></span> <span data-ttu-id="87e66-106">當這些參數中使用了不正確值時， **SQLFetch**會傳回 SQL_NO_DATA。</span><span class="sxs-lookup"><span data-stu-id="87e66-106">**SQLFetch** returns SQL_NO_DATA when invalid values are used in these parameters.</span></span>  
  
 <span data-ttu-id="87e66-107">**SQLProcedures**可以在靜態伺服器資料指標上執行。</span><span class="sxs-lookup"><span data-stu-id="87e66-107">**SQLProcedures** can be executed on a static server cursor.</span></span> <span data-ttu-id="87e66-108">嘗試在可更新的 (動態或索引鍵集) 資料指標上執行**SQLProcedures**時，將會傳回 SQL_SUCCESS_WITH_INFO，表示資料指標類型已變更。</span><span class="sxs-lookup"><span data-stu-id="87e66-108">An attempt to execute **SQLProcedures** on an updatable (dynamic or keyset) cursor will return SQL_SUCCESS_WITH_INFO, indicating that the cursor type has been changed.</span></span>  
  
 <span data-ttu-id="87e66-109">**SQLProcedures**會傳回名稱符合*ProcName*且可由目前使用者執行，或是目前使用者已被授與 VIEW DEFINITION 許可權之任何程式的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="87e66-109">**SQLProcedures** returns information about any procedures whose names match *ProcName* and can be executed by the current user, or for which the current user has been granted VIEW DEFINITION permission.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87e66-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="87e66-110">See Also</span></span>  
 <span data-ttu-id="87e66-111">[SQLProcedures 函式](https://go.microsoft.com/fwlink/?LinkId=59364) </span><span class="sxs-lookup"><span data-stu-id="87e66-111">[SQLProcedures Function](https://go.microsoft.com/fwlink/?LinkId=59364) </span></span>  
 [<span data-ttu-id="87e66-112">ODBC API 實作詳細資料</span><span class="sxs-lookup"><span data-stu-id="87e66-112">ODBC API Implementation Details</span></span>](odbc-api-implementation-details.md)  
  
  
