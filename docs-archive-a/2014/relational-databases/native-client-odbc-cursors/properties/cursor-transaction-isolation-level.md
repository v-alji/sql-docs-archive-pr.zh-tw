---
title: 資料指標交易隔離等級 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- isolation levels [ODBC]
- ODBC applications, row versioning
- cursors [ODBC], isolation levels
- ODBC cursors, isolation levels
- row versioning [SQL Server], ODBC
ms.assetid: 0c6663a4-5a25-44aa-8fe4-e35af9bf4a83
author: rothja
ms.author: jroth
ms.openlocfilehash: 30f3dc8a9136a7cbe1d5897cb0bcc9fff8c35ab2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706485"
---
# <a name="cursor-transaction-isolation-level"></a><span data-ttu-id="47c73-102">資料指標交易隔離等級</span><span class="sxs-lookup"><span data-stu-id="47c73-102">Cursor Transaction Isolation Level</span></span>
  <span data-ttu-id="47c73-103">資料指標的完整鎖定行為是以並行屬性之間的互動以及用戶端所設定的交易隔離等級為基礎。</span><span class="sxs-lookup"><span data-stu-id="47c73-103">The complete locking behavior of cursors is based on an interaction between concurrency attributes and the transaction isolation level set by the client.</span></span> <span data-ttu-id="47c73-104">ODBC 用戶端會使用[SQLSetConnectAttr](../../native-client-odbc-api/sqlsetconnectattr.md) SQL_ATTR_TXN_ISOLATION 或 SQL_COPT_SS_TXN_ISOLATION 屬性來設定交易隔離等級。</span><span class="sxs-lookup"><span data-stu-id="47c73-104">ODBC clients set the transaction isolation level using the [SQLSetConnectAttr](../../native-client-odbc-api/sqlsetconnectattr.md) SQL_ATTR_TXN_ISOLATION or SQL_COPT_SS_TXN_ISOLATION attributes.</span></span> <span data-ttu-id="47c73-105">特定資料指標環境的鎖定行為藉由結合以下各項來決定：並行的鎖定行為，以及交易隔離層級選項。</span><span class="sxs-lookup"><span data-stu-id="47c73-105">The locking behavior of a specific cursor environment is determined by combining the locking behaviors of the concurrency and transaction isolation level options.</span></span>  
  
 <span data-ttu-id="47c73-106">Native Client ODBC 驅動程式支援下列資料指標交易隔離等級 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ：</span><span class="sxs-lookup"><span data-stu-id="47c73-106">The following cursor transaction isolation levels are supported by the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver:</span></span>  
  
-   <span data-ttu-id="47c73-107">讀取認可 (SQL_TXN_READ_COMMITTED)</span><span class="sxs-lookup"><span data-stu-id="47c73-107">Read committed (SQL_TXN_READ_COMMITTED)</span></span>  
  
-   <span data-ttu-id="47c73-108">讀取未認可 (SQL_TXN_READ_UNCOMMITTED)</span><span class="sxs-lookup"><span data-stu-id="47c73-108">Read uncommitted (SQL_TXN_READ_UNCOMMITTED)</span></span>  
  
-   <span data-ttu-id="47c73-109">可重覆讀取 (SQL_TXN_REPEATABLE_READ)</span><span class="sxs-lookup"><span data-stu-id="47c73-109">Repeatable read (SQL_TXN_REPEATABLE_READ)</span></span>  
  
-   <span data-ttu-id="47c73-110">可序列化 (SQL_TXN_SERIALIZABLE)</span><span class="sxs-lookup"><span data-stu-id="47c73-110">Serializable (SQL_TXN_SERIALIZABLE)</span></span>  
  
-   <span data-ttu-id="47c73-111">快照集 (SQL_TXN_SS_SNAPSHOT)</span><span class="sxs-lookup"><span data-stu-id="47c73-111">Snapshot (SQL_TXN_SS_SNAPSHOT)</span></span>  
  
 <span data-ttu-id="47c73-112">請注意，ODBC API 會指定其他交易隔離等級，但是 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 或 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] NATIVE Client ODBC 驅動程式不支援。</span><span class="sxs-lookup"><span data-stu-id="47c73-112">Note that the ODBC API specifies additional transaction isolation levels, but these are not supported by [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] or the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47c73-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="47c73-113">See Also</span></span>  
 [<span data-ttu-id="47c73-114">資料指標屬性</span><span class="sxs-lookup"><span data-stu-id="47c73-114">Cursor Properties</span></span>](cursor-properties.md)  
  
  
