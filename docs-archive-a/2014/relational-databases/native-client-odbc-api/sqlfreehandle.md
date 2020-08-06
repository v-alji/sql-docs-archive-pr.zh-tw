---
title: SQLFreeHandle |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLFreeHandle function
ms.assetid: d374e5c8-ed35-43bf-8dd6-c37e38d9b5f1
author: rothja
ms.author: jroth
ms.openlocfilehash: f51f031bec05715e0345507278113f4f16179a77
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594517"
---
# <a name="sqlfreehandle"></a><span data-ttu-id="cf0bb-102">SQLFreeHandle</span><span class="sxs-lookup"><span data-stu-id="cf0bb-102">SQLFreeHandle</span></span>
  <span data-ttu-id="cf0bb-103">在手動認可模式中，使用開啟的交易在語句控制碼上呼叫**SQLFreeHandle** ，會導致資料庫的暫止變更回復。</span><span class="sxs-lookup"><span data-stu-id="cf0bb-103">In manual-commit mode, calling **SQLFreeHandle** on a statement handle with an open transaction causes a rollback of pending changes to the database.</span></span> <span data-ttu-id="cf0bb-104">在語句控制碼上呼叫**SQLFreeHandle**一律會關閉任何開啟的資料指標，並捨棄暫止的結果，釋放與語句控制碼相關聯的所有資源。</span><span class="sxs-lookup"><span data-stu-id="cf0bb-104">Calling **SQLFreeHandle** on a statement handle always closes any open cursors and discards pending results, freeing all resources associated with the statement handle.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf0bb-105">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cf0bb-105">See Also</span></span>  
 <span data-ttu-id="cf0bb-106">[SQLFreeHandle 函式](https://go.microsoft.com/fwlink/?LinkId=59345) </span><span class="sxs-lookup"><span data-stu-id="cf0bb-106">[SQLFreeHandle Function](https://go.microsoft.com/fwlink/?LinkId=59345) </span></span>  
 [<span data-ttu-id="cf0bb-107">ODBC API 實作詳細資料</span><span class="sxs-lookup"><span data-stu-id="cf0bb-107">ODBC API Implementation Details</span></span>](odbc-api-implementation-details.md)  
  
  
