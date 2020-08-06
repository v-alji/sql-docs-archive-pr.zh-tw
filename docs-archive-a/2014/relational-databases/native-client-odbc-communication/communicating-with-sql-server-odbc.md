---
title: 與 SQL Server (ODBC) 通訊 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, communicating with SQL Server
- ODBC applications, communicating with SQL Server
- ODBC, communicating with SQL Server
ms.assetid: cca3dcf0-2a7e-465a-84de-7ce055360eb6
author: rothja
ms.author: jroth
ms.openlocfilehash: c41ac2dcce9c5bdbdd351148d16bcaa8f067d22f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706489"
---
# <a name="communicating-with-sql-server-odbc"></a><span data-ttu-id="45a65-102">與 SQL Server 進行通訊 (ODBC)</span><span class="sxs-lookup"><span data-stu-id="45a65-102">Communicating with SQL Server (ODBC)</span></span>
  <span data-ttu-id="45a65-103">若要讓 ODBC 應用程式與的實例進行通訊 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，它必須配置環境和連接控制碼，並連接到資料來源。</span><span class="sxs-lookup"><span data-stu-id="45a65-103">For an ODBC application to communicate with an instance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], it must allocate environment and connection handles and connect to the data source.</span></span> <span data-ttu-id="45a65-104">建立連接之後，應用程式可以將查詢傳送到伺服器，並處理任何結果集。</span><span class="sxs-lookup"><span data-stu-id="45a65-104">After a connection is established, the application can send queries to the server and process any result sets.</span></span> <span data-ttu-id="45a65-105">當應用程式使用資料來源完畢時，它會中斷與資料來源的連接，並釋出連接控制代碼。</span><span class="sxs-lookup"><span data-stu-id="45a65-105">When the application has finished using the data source, it disconnects from the data source and frees the connection handle.</span></span> <span data-ttu-id="45a65-106">當應用程式釋出其所有連接控制代碼時，它會釋出環境控制代碼。</span><span class="sxs-lookup"><span data-stu-id="45a65-106">When the application has freed all its connection handles, it frees the environment handle.</span></span>  
  
 <span data-ttu-id="45a65-107">應用程式可以連接到任何數目的資料來源。</span><span class="sxs-lookup"><span data-stu-id="45a65-107">An application can connect to any number of data sources.</span></span> <span data-ttu-id="45a65-108">應用程式可以使用驅動程式與資料來源的組合、相同的驅動程式與資料來源組合，甚至相同驅動程式與相同資料來源的多個連接。</span><span class="sxs-lookup"><span data-stu-id="45a65-108">The application can use a combination of drivers and data sources, the same driver and a combination of data sources, or even the same driver and multiple connections to the same data source.</span></span>  
  
 <span data-ttu-id="45a65-109">您可以 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 從 MSDN 上的[SQL Server 下載](https://go.microsoft.com/fwlink/?LinkId=62796)] 頁面下載 Native Client ODBC 範例。</span><span class="sxs-lookup"><span data-stu-id="45a65-109">You can download [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC samples from the [SQL Server Downloads](https://go.microsoft.com/fwlink/?LinkId=62796) page on MSDN.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="45a65-110">本節內容</span><span class="sxs-lookup"><span data-stu-id="45a65-110">In This Section</span></span>  
  
-   [<span data-ttu-id="45a65-111">配置環境控制代碼</span><span class="sxs-lookup"><span data-stu-id="45a65-111">Allocating an Environment Handle</span></span>](allocating-an-environment-handle.md)  
  
-   [<span data-ttu-id="45a65-112">配置連接控制代碼</span><span class="sxs-lookup"><span data-stu-id="45a65-112">Allocating a Connection Handle</span></span>](allocating-a-connection-handle.md)  
  
-   [<span data-ttu-id="45a65-113">SQL Server Native Client ODBC 資料來源</span><span class="sxs-lookup"><span data-stu-id="45a65-113">SQL Server Native Client ODBC Data Sources</span></span>](../../integration-services/connection-manager/data-sources.md)  
  
-   [<span data-ttu-id="45a65-114">連接到 &#40;ODBC&#41;的資料來源</span><span class="sxs-lookup"><span data-stu-id="45a65-114">Connecting to a Data Source &#40;ODBC&#41;</span></span>](connecting-to-a-data-source-odbc.md)  
  
-   [<span data-ttu-id="45a65-115">從資料來源中斷連接</span><span class="sxs-lookup"><span data-stu-id="45a65-115">Disconnecting from a Data Source</span></span>](disconnecting-from-a-data-source.md)  
  
## <a name="see-also"></a><span data-ttu-id="45a65-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="45a65-116">See Also</span></span>  
 <span data-ttu-id="45a65-117">[SQL Server Native Client &#40;ODBC&#41;](../native-client/odbc/sql-server-native-client-odbc.md) </span><span class="sxs-lookup"><span data-stu-id="45a65-117">[SQL Server Native Client &#40;ODBC&#41;](../native-client/odbc/sql-server-native-client-odbc.md) </span></span>  
 [<span data-ttu-id="45a65-118">SQLSetEnvAttr</span><span class="sxs-lookup"><span data-stu-id="45a65-118">SQLSetEnvAttr</span></span>](../native-client-odbc-api/sqlsetenvattr.md)  
  
  
