---
title: 中斷與資料來源的連線 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- ODBC data sources, connections
- data sources [SQL Server Native Client]
- disconnecting [ODBC]
- ODBC applications, disconnecting
- SQLDisconnect function
- ODBC applications, data sources
- connections [SQL Server Native Client]
- SQLFreeHandle function
- ODBC data sources, disconnecting
- SQL Server Native Client ODBC driver, data sources
- ODBC functions
- SQL Server Native Client ODBC driver, connections
ms.assetid: 65b0267d-b2ab-4a59-83f2-436d90cfbf79
author: rothja
ms.author: jroth
ms.openlocfilehash: 5db3b83ab65d854f3a4d2182d9a4a1314e097681
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595947"
---
# <a name="disconnecting-from-a-data-source"></a><span data-ttu-id="fce6c-102">從資料來源中斷連接</span><span class="sxs-lookup"><span data-stu-id="fce6c-102">Disconnecting from a Data Source</span></span>
  <span data-ttu-id="fce6c-103">當應用程式完成使用資料來源時，它會呼叫**SQLDisconnect**。</span><span class="sxs-lookup"><span data-stu-id="fce6c-103">When an application has finished using a data source, it calls **SQLDisconnect**.</span></span> <span data-ttu-id="fce6c-104">**SQLDisconnect**會釋放在連接上配置的任何語句，並中斷驅動程式與資料來源的連線。</span><span class="sxs-lookup"><span data-stu-id="fce6c-104">**SQLDisconnect** frees any statements that are allocated on the connection and disconnects the driver from the data source.</span></span> <span data-ttu-id="fce6c-105">中斷連線之後，應用程式可以呼叫[SQLFreeHandle](../native-client-odbc-api/sqlfreehandle.md)來釋放連接控制碼。</span><span class="sxs-lookup"><span data-stu-id="fce6c-105">After disconnecting, the application can call [SQLFreeHandle](../native-client-odbc-api/sqlfreehandle.md) to free the connection handle.</span></span> <span data-ttu-id="fce6c-106">在結束之前，應用程式也會呼叫**SQLFreeHandle**來釋放環境控制碼。</span><span class="sxs-lookup"><span data-stu-id="fce6c-106">Before exiting, an application also calls **SQLFreeHandle** to free the environment handle.</span></span>  
  
 <span data-ttu-id="fce6c-107">中斷連接之後，應用程式可以重複使用配置的連接控制代碼來連接到不同的資料來源或重新連接到相同的資料來源。</span><span class="sxs-lookup"><span data-stu-id="fce6c-107">After disconnecting, an application can reuse the allocated connection handle, either to connect to a different data source or reconnect to the same data source.</span></span> <span data-ttu-id="fce6c-108">選擇保持連接狀態，而非中斷連接並稍後再重新連接時，應用程式撰寫者必須考慮每個選擇的相對成本。</span><span class="sxs-lookup"><span data-stu-id="fce6c-108">The decision to remain connected instead of disconnecting and reconnecting later requires that the application writer consider the relative costs of each option.</span></span> <span data-ttu-id="fce6c-109">連接到資料來源並維持連接狀態可能相當昂貴，端視連接媒體而定。</span><span class="sxs-lookup"><span data-stu-id="fce6c-109">Connecting to a data source and remaining connected can be relatively costly, depending on the connection medium.</span></span> <span data-ttu-id="fce6c-110">進行取捨時，應用程式也必須假設在相同資料來源上進行額外作業的可能性和時機。</span><span class="sxs-lookup"><span data-stu-id="fce6c-110">In making a trade-off, the application must also make assumptions about the probability and timing of additional operations on the same data source.</span></span> <span data-ttu-id="fce6c-111">應用程式可能也必須使用多個連接。</span><span class="sxs-lookup"><span data-stu-id="fce6c-111">An application may also have to use more than one connection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fce6c-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fce6c-112">See Also</span></span>  
 [<span data-ttu-id="fce6c-113">與 SQL Server &#40;ODBC&#41;通訊</span><span class="sxs-lookup"><span data-stu-id="fce6c-113">Communicating with SQL Server &#40;ODBC&#41;</span></span>](communicating-with-sql-server-odbc.md)  
  
  
