---
title: SQLGetCursorName |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLGetCursorName function
ms.assetid: 3a427a23-28ef-49aa-b9ec-6cab0914bdf3
author: rothja
ms.author: jroth
ms.openlocfilehash: 01ce6e42b4e8753d07309ec7ce298d4f743d4a6d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584494"
---
# <a name="sqlgetcursorname"></a><span data-ttu-id="05f04-102">SQLGetCursorName</span><span class="sxs-lookup"><span data-stu-id="05f04-102">SQLGetCursorName</span></span>
  <span data-ttu-id="05f04-103">如果應用程式未指定資料指標名稱， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native CLIENT ODBC 驅動程式會在資料指標產生時為應用程式產生一個。</span><span class="sxs-lookup"><span data-stu-id="05f04-103">If the application does not specify a cursor name, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver generates one for the application upon cursor generation.</span></span> <span data-ttu-id="05f04-104">應用程式可以使用**SQLGetCursorName**來抓取用於定位 UPDATE 和 DELETE 子句的驅動程式定義資料指標名稱。</span><span class="sxs-lookup"><span data-stu-id="05f04-104">The application can use **SQLGetCursorName** to retrieve the driver-defined cursor name for positioned UPDATE and DELETE statements.</span></span> <span data-ttu-id="05f04-105">應用程式不需要呼叫**SQLSetCursorName** ，即可利用定位的資料動作陳述式。</span><span class="sxs-lookup"><span data-stu-id="05f04-105">The application does not need to call **SQLSetCursorName** to take advantage of positioned data manipulation statements.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05f04-106">另請參閱</span><span class="sxs-lookup"><span data-stu-id="05f04-106">See Also</span></span>  
 <span data-ttu-id="05f04-107">[SQLGetCursorName 函式](https://go.microsoft.com/fwlink/?LinkId=59349) </span><span class="sxs-lookup"><span data-stu-id="05f04-107">[SQLGetCursorName Function](https://go.microsoft.com/fwlink/?LinkId=59349) </span></span>  
 [<span data-ttu-id="05f04-108">ODBC API 實作詳細資料</span><span class="sxs-lookup"><span data-stu-id="05f04-108">ODBC API Implementation Details</span></span>](odbc-api-implementation-details.md)  
  
  
