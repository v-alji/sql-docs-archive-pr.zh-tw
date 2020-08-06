---
title: 多執行緒應用程式 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- threads [SQL Server], multithreaded applications
- ODBC applications, multithreaded applications
- asynchronous operations [SQL Server Native Client]
- SQL Server Native Client ODBC driver, multithreaded applications
- multithreaded applications [SQL Server Native Client]
ms.assetid: d352c91a-6e08-4e50-9f3e-a37892d9c2cc
author: rothja
ms.author: jroth
ms.openlocfilehash: b680086f76e0c1a1e8c8cfc2f4ef82099957b3fd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598303"
---
# <a name="multithreaded-applications"></a><span data-ttu-id="55cea-102">多執行緒應用程式</span><span class="sxs-lookup"><span data-stu-id="55cea-102">Multithreaded Applications</span></span>
  <span data-ttu-id="55cea-103">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC 驅動程式是一個多執行緒的驅動程式。</span><span class="sxs-lookup"><span data-stu-id="55cea-103">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver is a multithreaded driver.</span></span> <span data-ttu-id="55cea-104">撰寫多執行緒應用程式是使用非同步呼叫處理多個 ODBC 呼叫的替代方式。</span><span class="sxs-lookup"><span data-stu-id="55cea-104">Writing a multithreaded application is an alternative to using asynchronous calls to process multiple ODBC calls.</span></span> <span data-ttu-id="55cea-105">執行緒可以進行非同步的 ODBC 呼叫，而其他執行緒可以在第一個執行緒遭到封鎖而等待回應其呼叫時處理。</span><span class="sxs-lookup"><span data-stu-id="55cea-105">A thread can make a synchronous ODBC call, and other threads can process while the first thread is blocked waiting for the response to its call.</span></span> <span data-ttu-id="55cea-106">此模式比進行非同步呼叫更有效率，因為它會排除網路流量之類的負擔，而且產生重複的 ODBC 函數會呼叫 SQL_STILL_EXECUTING 的測試。</span><span class="sxs-lookup"><span data-stu-id="55cea-106">This model is more efficient than making asynchronous calls because it eliminates overhead such as network traffic and making repeated ODBC function calls testing for SQL_STILL_EXECUTING.</span></span>  
  
 <span data-ttu-id="55cea-107">非同步模式仍然是處理的有效方法。</span><span class="sxs-lookup"><span data-stu-id="55cea-107">Asynchronous mode is still an effective method of processing.</span></span> <span data-ttu-id="55cea-108">多執行緒模型的效能改善還不足以免於重新撰寫非同步的應用程式。</span><span class="sxs-lookup"><span data-stu-id="55cea-108">The performance improvements of a multithreaded model are not enough to justify rewriting asynchronous applications.</span></span> <span data-ttu-id="55cea-109">如果使用者要轉換使用 DB-Library 非同步模型的 DB-Library 應用程式，將它們轉換為 ODBC 非同步模式更為容易。</span><span class="sxs-lookup"><span data-stu-id="55cea-109">If users are converting DB-Library applications that use the DB-Library asynchronous model, it is easier to convert them to the ODBC asynchronous model.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55cea-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="55cea-110">See Also</span></span>  
 [<span data-ttu-id="55cea-111">建立 SQL Server Native Client ODBC 驅動程式應用程式</span><span class="sxs-lookup"><span data-stu-id="55cea-111">Creating a SQL Server Native Client ODBC Driver Application</span></span>](creating-a-driver-application.md)  
  
  
