---
title: 資料表值參數 (SQL Server Native Client) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client, table-valued parameters
- table-valued parameters (SQL Server Native Client)
ms.assetid: 5ee6bdcd-0309-4a20-b5c2-0e6b6839f34f
author: rothja
ms.author: jroth
ms.openlocfilehash: 6af4979b9a77c94f52be5197b01179007a971283
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592661"
---
# <a name="table-valued-parameters-sql-server-native-client"></a><span data-ttu-id="0e9ee-102">資料表值參數 (SQL Server Native Client)</span><span class="sxs-lookup"><span data-stu-id="0e9ee-102">Table-Valued Parameters (SQL Server Native Client)</span></span>
  <span data-ttu-id="0e9ee-103">資料表值參數是在 [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] 中導入，而且會提供有效的方式將資料的多個資料列傳遞至伺服器。</span><span class="sxs-lookup"><span data-stu-id="0e9ee-103">Table-valued parameters were introduced in [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)], and provide an efficient way to pass multiple rows of data to the server.</span></span> <span data-ttu-id="0e9ee-104">資料表值參數會提供類似參數陣列的功能，但是提供了更多的彈性，並與 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 更緊密地整合在一起，而且時常可以增進效能。</span><span class="sxs-lookup"><span data-stu-id="0e9ee-104">Table-valued parameters provide functionality similar to parameter arrays, but they offer more flexibility and closer integration with [!INCLUDE[tsql](../../../includes/tsql-md.md)], and can frequently improve performance.</span></span> <span data-ttu-id="0e9ee-105">資料表值參數也可以參與以集合為基礎的作業，而參數陣列則不行。</span><span class="sxs-lookup"><span data-stu-id="0e9ee-105">Table-valued parameters can also participate in set-based operations, whereas parameter arrays cannot.</span></span>  
  
 <span data-ttu-id="0e9ee-106">如需有關資料表值參數和 ODBC 的詳細資訊，請參閱[odbc&#41;&#40;的資料表值參數](../../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)。</span><span class="sxs-lookup"><span data-stu-id="0e9ee-106">For information about table-valued parameters and ODBC, see [Table-Valued Parameters &#40;ODBC&#41;](../../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).</span></span>  
  
 <span data-ttu-id="0e9ee-107">如需有關資料表值參數和 OLE DB 的詳細資訊，請參閱[資料表值參數 &#40;OLE DB&#41;](../../native-client-ole-db-table-valued-parameters/table-valued-parameters-ole-db.md)。</span><span class="sxs-lookup"><span data-stu-id="0e9ee-107">For information about table-valued parameters and OLE DB, see [Table-Valued Parameters &#40;OLE DB&#41;](../../native-client-ole-db-table-valued-parameters/table-valued-parameters-ole-db.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e9ee-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0e9ee-108">See Also</span></span>  
 [<span data-ttu-id="0e9ee-109">SQL Server Native Client 功能</span><span class="sxs-lookup"><span data-stu-id="0e9ee-109">SQL Server Native Client Features</span></span>](sql-server-native-client-features.md)  
  
  
