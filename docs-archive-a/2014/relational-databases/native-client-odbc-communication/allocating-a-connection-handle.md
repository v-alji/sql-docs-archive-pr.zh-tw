---
title: 配置連接控制碼 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- ODBC applications, passwords
- ODBC applications, connections
- handles [SQL Server Native Client]
- expiration [SQL Server Native Client]
- passwords [SQL Server], modifying
- SQL Server Native Client ODBC driver, connection handles
- connection handles [SQL Server Native Client]
- modifying passwords
- SQLAllocHandle function
ms.assetid: 471d8a31-199c-4f92-bb10-004fc7733b35
author: rothja
ms.author: jroth
ms.openlocfilehash: d3cf84e541f114d527d9a00cd19bce705a09af30
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709394"
---
# <a name="allocating-a-connection-handle"></a><span data-ttu-id="55189-102">配置連接控制代碼</span><span class="sxs-lookup"><span data-stu-id="55189-102">Allocating a Connection Handle</span></span>
  <span data-ttu-id="55189-103">在應用程式可以連接到資料來源或驅動程式之前，必須配置連接控制代碼。</span><span class="sxs-lookup"><span data-stu-id="55189-103">Before the application can connect to a data source or driver, it must allocate a connection handle.</span></span> <span data-ttu-id="55189-104">這是藉由呼叫**SQLAllocHandle**並將*HandleType*參數設定為 SQL_HANDLE_DBC，並將*InputHandle*指向已初始化的環境控制碼來完成。</span><span class="sxs-lookup"><span data-stu-id="55189-104">This is done by calling **SQLAllocHandle** with the *HandleType* parameter set to SQL_HANDLE_DBC and *InputHandle* pointing to an initialized environment handle.</span></span>  
  
 <span data-ttu-id="55189-105">連接的特性是藉由設定連接屬性來控制。</span><span class="sxs-lookup"><span data-stu-id="55189-105">The characteristics of the connection are controlled by setting connection attributes.</span></span> <span data-ttu-id="55189-106">例如，因為交易發生在連接層級，所以交易隔離等級是連接屬性。</span><span class="sxs-lookup"><span data-stu-id="55189-106">For example, because transactions occur at the connection level, the transaction isolation level is a connection attribute.</span></span> <span data-ttu-id="55189-107">同樣地，登入逾時 (也就是要在嘗試連接時，在逾時之前等候的秒數) 也是連接屬性。</span><span class="sxs-lookup"><span data-stu-id="55189-107">Similarly, the login time-out, or number of seconds to wait while trying to connect before timing out, is a connection attribute.</span></span>  
  
 <span data-ttu-id="55189-108">連接屬性是以[SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md)設定，而且其目前的設定會使用[SQLGetConnectAttr](../native-client-odbc-api/sqlgetconnectattr.md)來抓取。</span><span class="sxs-lookup"><span data-stu-id="55189-108">Connection attributes are set with [SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md), and their current settings are retrieved with [SQLGetConnectAttr](../native-client-odbc-api/sqlgetconnectattr.md).</span></span> <span data-ttu-id="55189-109">如果在嘗試連接之前呼叫**SQLSetConnectAttr** ，則 ODBC 驅動程式管理員會將屬性儲存在其連接結構中，並在連接過程中將它們設定在驅動程式中。</span><span class="sxs-lookup"><span data-stu-id="55189-109">If **SQLSetConnectAttr** is called before a connection is attempted, the ODBC Driver Manager stores the attributes in its connection structure and sets them in the driver as part of the connection process.</span></span> <span data-ttu-id="55189-110">有些連接屬性必須在應用程式嘗試連接之前設定，其他的屬性則可以在連接完成之後設定。</span><span class="sxs-lookup"><span data-stu-id="55189-110">Some connection attributes must be set before the application attempts to connect; others can be set after the connection has completed.</span></span> <span data-ttu-id="55189-111">例如，SQL_ATTR_ODBC_CURSORS 必須在進行連接之前設定，但 SQL_ATTR_AUTOCOMMIT 可以在連接之後設定。</span><span class="sxs-lookup"><span data-stu-id="55189-111">For example, SQL_ATTR_ODBC_CURSORS must be set before a connection is made, but SQL_ATTR_AUTOCOMMIT can be set after connecting.</span></span>  
  
 <span data-ttu-id="55189-112">針對 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 7.0 版或更新版本執行的應用程式，有時可以藉由重設表格式資料流 (TDS) 網路封包大小來改善其效能。</span><span class="sxs-lookup"><span data-stu-id="55189-112">Applications running against [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] version 7.0 or later can sometimes improve their performance by resetting the tabular data stream (TDS) network packet size.</span></span> <span data-ttu-id="55189-113">預設封包大小是 4 KB，設定於伺服器。</span><span class="sxs-lookup"><span data-stu-id="55189-113">The default packet size is set at the server, at 4 KB.</span></span> <span data-ttu-id="55189-114">4 KB 到 8 KB 的封包大小一般可提供最佳效能。</span><span class="sxs-lookup"><span data-stu-id="55189-114">A packet size of 4 KB to 8 KB generally gives the best performance.</span></span> <span data-ttu-id="55189-115">如果測試顯示應用程式使用其他封包大小時效能較佳，則可以重設封包大小。</span><span class="sxs-lookup"><span data-stu-id="55189-115">If testing shows that it performs better with a different packet size, the application can reset the packet size.</span></span> <span data-ttu-id="55189-116">ODBC 應用程式可以藉由使用 SQL_ATTR_PACKET_SIZE 選項呼叫**SQLSetConnectAttr**來進行連接。</span><span class="sxs-lookup"><span data-stu-id="55189-116">ODBC applications can do this before connecting by calling **SQLSetConnectAttr** with the SQL_ATTR_PACKET_SIZE option.</span></span> <span data-ttu-id="55189-117">有些應用程式在使用較大封包大小時效能較佳，但一般而言，封包大小大於 8 KB 時所能改進的效能微乎其微。</span><span class="sxs-lookup"><span data-stu-id="55189-117">Some applications perform better with a larger packet size, but performance improvements are generally minimal for packet sizes larger than 8 KB.</span></span>  
  
 <span data-ttu-id="55189-118">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native CLIENT ODBC 驅動程式具有一些擴充連接屬性，可讓應用程式用來增加其功能。</span><span class="sxs-lookup"><span data-stu-id="55189-118">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver has a number of extended connection attributes that an application can use to increase its functionality.</span></span> <span data-ttu-id="55189-119">這其中有些屬性所控制的選項，可在資料來源中指定並用來覆寫資料來源中所設的任何選項。</span><span class="sxs-lookup"><span data-stu-id="55189-119">Some of these attributes control the same options that can be specified in data sources and used to override whatever option is set in a data source.</span></span> <span data-ttu-id="55189-120">例如，如果應用程式使用引號識別碼，則可以將驅動程式特定的屬性 SQL_COPT_SS_QUOTED_IDENT 設為 SQL_QI_ON，以確保一定可以設定此選項，不論資料來源中的設定為何。</span><span class="sxs-lookup"><span data-stu-id="55189-120">For example, if an application uses quoted identifiers, it can set the driver-specific attribute SQL_COPT_SS_QUOTED_IDENT to SQL_QI_ON to ensure this option is always set regardless of the setting in any data source.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55189-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="55189-121">See Also</span></span>  
 [<span data-ttu-id="55189-122">與 SQL Server &#40;ODBC&#41;通訊</span><span class="sxs-lookup"><span data-stu-id="55189-122">Communicating with SQL Server &#40;ODBC&#41;</span></span>](communicating-with-sql-server-odbc.md)  
  
  
