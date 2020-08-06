---
title: SQLColumnPrivileges |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLColumnPrivileges function
ms.assetid: c78acd4e-8668-4abc-9bc9-6ad381965863
author: rothja
ms.author: jroth
ms.openlocfilehash: bf46fed47817ed94ea2382f2147df254f2986aec
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592681"
---
# <a name="sqlcolumnprivileges"></a><span data-ttu-id="08b80-102">SQLColumnPrivileges</span><span class="sxs-lookup"><span data-stu-id="08b80-102">SQLColumnPrivileges</span></span>
  <span data-ttu-id="08b80-103">**SQLColumnPrivileges**會傳回 SQL_SUCCESS*CatalogName*、 *SchemaName*、 *TableName*或*ColumnName*參數的值是否存在。</span><span class="sxs-lookup"><span data-stu-id="08b80-103">**SQLColumnPrivileges** returns SQL_SUCCESS whether or not values exist for the*CatalogName*, *SchemaName*, *TableName*, or *ColumnName* parameters.</span></span> <span data-ttu-id="08b80-104">當這些參數中使用了不正確值時， **SQLFetch**會傳回 SQL_NO_DATA。</span><span class="sxs-lookup"><span data-stu-id="08b80-104">**SQLFetch** returns SQL_NO_DATA when invalid values are used in these parameters.</span></span>  
  
 <span data-ttu-id="08b80-105">**SQLColumnPrivileges**可以在靜態伺服器資料指標上執行。</span><span class="sxs-lookup"><span data-stu-id="08b80-105">**SQLColumnPrivileges** can be executed on a static server cursor.</span></span> <span data-ttu-id="08b80-106">嘗試在可更新的 (動態或索引鍵集) 資料指標上執行**SQLColumnPrivileges**時，將會傳回 SQL_SUCCESS_WITH_INFO，表示資料指標類型已變更。</span><span class="sxs-lookup"><span data-stu-id="08b80-106">An attempt to execute **SQLColumnPrivileges** on an updatable (dynamic or keyset) cursor will return SQL_SUCCESS_WITH_INFO indicating that the cursor type has been changed.</span></span>  
  
 <span data-ttu-id="08b80-107">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native CLIENT ODBC 驅動程式藉由接受*CatalogName*參數的兩部分名稱，支援連結伺服器上之資料表的報告資訊： *Linked_Server_Name. Catalog_Name*。</span><span class="sxs-lookup"><span data-stu-id="08b80-107">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver supports reporting information for tables on linked servers by accepting a two-part name for the *CatalogName* parameter: *Linked_Server_Name.Catalog_Name*.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08b80-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="08b80-108">See Also</span></span>  
 <span data-ttu-id="08b80-109">[SQLColumnPrivileges 函式](https://go.microsoft.com/fwlink/?LinkId=59335) </span><span class="sxs-lookup"><span data-stu-id="08b80-109">[SQLColumnPrivileges Function](https://go.microsoft.com/fwlink/?LinkId=59335) </span></span>  
 [<span data-ttu-id="08b80-110">ODBC API 實作詳細資料</span><span class="sxs-lookup"><span data-stu-id="08b80-110">ODBC API Implementation Details</span></span>](odbc-api-implementation-details.md)  
  
  
