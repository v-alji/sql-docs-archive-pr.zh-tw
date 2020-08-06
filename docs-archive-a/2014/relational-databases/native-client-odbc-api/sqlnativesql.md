---
title: SQLNativeSql |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLNativeSql function
ms.assetid: 2d999fec-9e22-4514-ad5f-22a64b82f95b
author: rothja
ms.author: jroth
ms.openlocfilehash: 433b086dc36a79cb82868edebac9f0a4814c21fe
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606267"
---
# <a name="sqlnativesql"></a><span data-ttu-id="47ace-102">SQLNativeSql</span><span class="sxs-lookup"><span data-stu-id="47ace-102">SQLNativeSql</span></span>
  <span data-ttu-id="47ace-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native CLIENT ODBC 驅動程式會滿足**SQLNativeSql**要求，而不需造訪伺服器。</span><span class="sxs-lookup"><span data-stu-id="47ace-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver satisfies **SQLNativeSql** requests without visiting the server.</span></span> <span data-ttu-id="47ace-104">此函數可有效率地測試 SQL 陳述式的語法。</span><span class="sxs-lookup"><span data-stu-id="47ace-104">The function efficiently tests the syntax of SQL statements.</span></span> <span data-ttu-id="47ace-105">語法檢查不會判斷 SQL 語句中的識別碼或運算式結果是否有效，而且 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **SQLNativeSql**所傳回的原生 SQL 可能無法執行。</span><span class="sxs-lookup"><span data-stu-id="47ace-105">Syntax checking does not determine if identifiers or the results of expressions in the SQL statements are valid, and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] native SQL returned by **SQLNativeSql** can fail to run.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47ace-106">另請參閱</span><span class="sxs-lookup"><span data-stu-id="47ace-106">See Also</span></span>  
 <span data-ttu-id="47ace-107">[SQLNativeSql 函式](https://go.microsoft.com/fwlink/?LinkID=59358) </span><span class="sxs-lookup"><span data-stu-id="47ace-107">[SQLNativeSql Function](https://go.microsoft.com/fwlink/?LinkID=59358) </span></span>  
 [<span data-ttu-id="47ace-108">ODBC API 實作詳細資料</span><span class="sxs-lookup"><span data-stu-id="47ace-108">ODBC API Implementation Details</span></span>](odbc-api-implementation-details.md)  
  
  
