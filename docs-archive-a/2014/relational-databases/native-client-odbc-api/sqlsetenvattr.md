---
title: SQLSetEnvAttr |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLSetEnvAttr function
ms.assetid: d4114571-feca-4330-b2e4-7bfd1050b812
author: rothja
ms.author: jroth
ms.openlocfilehash: f0dbd4d01de9ca769c46a93f810f0149f5b86981
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606245"
---
# <a name="sqlsetenvattr"></a><span data-ttu-id="dc412-102">SQLSetEnvAttr</span><span class="sxs-lookup"><span data-stu-id="dc412-102">SQLSetEnvAttr</span></span>
  <span data-ttu-id="dc412-103">Odbc 程式設計[人員參考](https://go.microsoft.com/fwlink/?LinkId=45250)會定義 odbc 驅動程式應該如何解讀寫入 odbc 2 之應用程式的**SQLSetEnvAttr**屬性規格。*x*或 ODBC 3。*x* API。</span><span class="sxs-lookup"><span data-stu-id="dc412-103">The [ODBC Programmer's Reference](https://go.microsoft.com/fwlink/?LinkId=45250) defines how ODBC drivers should interpret the **SQLSetEnvAttr** attribute specifications from applications written to either the ODBC 2.*x* or ODBC 3.*x* API.</span></span> <span data-ttu-id="dc412-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native CLIENT ODBC 驅動程式符合這些規則。</span><span class="sxs-lookup"><span data-stu-id="dc412-104">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver complies with those rules.</span></span>  
  
 <span data-ttu-id="dc412-105">**SQLSetEnvAttr**所控制的其中一個屬性就是是否要使用連接共用。</span><span class="sxs-lookup"><span data-stu-id="dc412-105">One of the attributes controlled by **SQLSetEnvAttr** is whether connection pooling is to be used.</span></span> <span data-ttu-id="dc412-106">如果連接共用與 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native CLIENT ODBC 驅動程式搭配使用，則在連接[SQLDriverConnect](sqldriverconnect.md)或**SQLConnect**時， *DriverCompletion*參數必須設定為 SQL_DRIVER_NOPROMPT。</span><span class="sxs-lookup"><span data-stu-id="dc412-106">If connection pooling is used with the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver, the *DriverCompletion* parameter must be set to SQL_DRIVER_NOPROMPT when connecting with either [SQLDriverConnect](sqldriverconnect.md) or **SQLConnect**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc412-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dc412-107">See Also</span></span>  
 <span data-ttu-id="dc412-108">[SQLSetEnvAttr 函式](https://go.microsoft.com/fwlink/?LinkId=59369) </span><span class="sxs-lookup"><span data-stu-id="dc412-108">[SQLSetEnvAttr Function](https://go.microsoft.com/fwlink/?LinkId=59369) </span></span>  
 [<span data-ttu-id="dc412-109">ODBC API 實作詳細資料</span><span class="sxs-lookup"><span data-stu-id="dc412-109">ODBC API Implementation Details</span></span>](odbc-api-implementation-details.md)  
  
  
