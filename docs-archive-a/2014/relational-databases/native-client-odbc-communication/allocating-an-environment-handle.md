---
title: 配置環境控制碼 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, environment handles
- ODBC applications, connections
- handles [SQL Server Native Client]
- environment handles [SQLNCLI]
ms.assetid: 15c1b428-ea6d-4672-894c-f0e289e2da3f
author: rothja
ms.author: jroth
ms.openlocfilehash: 1c655b5e9a406c3e1881c9dd199a92666377918f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597104"
---
# <a name="allocating-an-environment-handle"></a><span data-ttu-id="b1f1c-102">配置環境控制代碼</span><span class="sxs-lookup"><span data-stu-id="b1f1c-102">Allocating an Environment Handle</span></span>
  <span data-ttu-id="b1f1c-103">應用程式必須先初始化 ODBC 環境並配置環境控制代碼，然後才能呼叫任何 ODBC 函數。</span><span class="sxs-lookup"><span data-stu-id="b1f1c-103">Before an application can call any ODBC function, it must initialize the ODBC environment and allocate an environment handle.</span></span> <span data-ttu-id="b1f1c-104">在 ODBC 中，這是其他控制代碼的全域內容控制代碼和預留位置。</span><span class="sxs-lookup"><span data-stu-id="b1f1c-104">This is the global context handle and placeholder for the other handles in ODBC.</span></span> <span data-ttu-id="b1f1c-105">若要這麼做，您可以呼叫**SQLAllocHandle**並將*HandleType*參數設定為 SQL_HANDLE_ENV，並將*InputHandle*設定為 SQL_Null_HANDLE。</span><span class="sxs-lookup"><span data-stu-id="b1f1c-105">You do this by calling **SQLAllocHandle** with the *HandleType* parameter set to SQL_HANDLE_ENV and *InputHandle* set to SQL_NULL_HANDLE.</span></span>  
  
 <span data-ttu-id="b1f1c-106">配置環境控制代碼之後，應用程式必須設定環境屬性來指出它將使用的 ODBC 函數呼叫版本。</span><span class="sxs-lookup"><span data-stu-id="b1f1c-106">After allocating the environment handle, the application must set environment attributes to indicate which version of ODBC function calls it will be using.</span></span> <span data-ttu-id="b1f1c-107">使用 ODBC 3。*x*函式，請呼叫[SQLSetEnvAttr](../native-client-odbc-api/sqlsetenvattr.md)並將*Attribute*參數設定為 SQL_ATTR_ODBC_VERSION，並將*valueptr 是*設為 SQL_OV_ODBC3。</span><span class="sxs-lookup"><span data-stu-id="b1f1c-107">To use the ODBC 3.*x* functions, call [SQLSetEnvAttr](../native-client-odbc-api/sqlsetenvattr.md) with the *Attribute* parameter set to SQL_ATTR_ODBC_VERSION and *ValuePtr* set to SQL_OV_ODBC3.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1f1c-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b1f1c-108">See Also</span></span>  
 [<span data-ttu-id="b1f1c-109">與 SQL Server &#40;ODBC&#41;通訊</span><span class="sxs-lookup"><span data-stu-id="b1f1c-109">Communicating with SQL Server &#40;ODBC&#41;</span></span>](communicating-with-sql-server-odbc.md)  
  
  
