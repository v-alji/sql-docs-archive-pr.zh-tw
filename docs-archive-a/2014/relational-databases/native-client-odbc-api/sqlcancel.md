---
title: SQLCancel |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQLCancel function
ms.assetid: d4c965ae-c1ac-4e9d-b4b9-32b561401106
author: rothja
ms.author: jroth
ms.openlocfilehash: dc3d86229501f80b25fb077788d1835a5f4f5c96
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594996"
---
# <a name="sqlcancel"></a><span data-ttu-id="f881d-102">SQLCancel</span><span class="sxs-lookup"><span data-stu-id="f881d-102">SQLCancel</span></span>
  <span data-ttu-id="f881d-103">[SQLCancel](https://go.microsoft.com/fwlink/?LinkId=203516)主題指出，在 ODBC 2.x 中，如果應用程式在 `SQLCancel` 未于語句上進行處理時呼叫，其效果與 `SQLCancel` `SQLFreeStmt` 選項相同 `SQL_CLOSE` ; 此行為只會針對完整性而定義，而應用程式應該呼叫 `SQLFreeStmt` 或 `SQLCloseCursor` 來關閉資料指標。</span><span class="sxs-lookup"><span data-stu-id="f881d-103">The [SQLCancel](https://go.microsoft.com/fwlink/?LinkId=203516) topic says that in ODBC 2.x, if an application calls `SQLCancel` when no processing is being done on the statement, `SQLCancel` has the same effect as `SQLFreeStmt` with the `SQL_CLOSE` option; this behavior is defined only for completeness and applications should call `SQLFreeStmt` or `SQLCloseCursor` to close cursors.</span></span> <span data-ttu-id="f881d-104">不過，即使您的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 應用程式將 ODBC API 版本設定為 3.5.x 或更新版本，`SQLCancel` 函數仍將使用 ODBC 2.x 行為。</span><span class="sxs-lookup"><span data-stu-id="f881d-104">But even if your [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client application sets the ODBC API version to be 3.5.x or later, the `SQLCancel` function will use the ODBC 2.x behavior.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f881d-105">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f881d-105">See Also</span></span>  
 <span data-ttu-id="f881d-106">[SQLCancel](https://go.microsoft.com/fwlink/?LinkId=203516) </span><span class="sxs-lookup"><span data-stu-id="f881d-106">[SQLCancel](https://go.microsoft.com/fwlink/?LinkId=203516) </span></span>  
 [<span data-ttu-id="f881d-107">ODBC API 實作詳細資料</span><span class="sxs-lookup"><span data-stu-id="f881d-107">ODBC API Implementation Details</span></span>](odbc-api-implementation-details.md)  
  
  
