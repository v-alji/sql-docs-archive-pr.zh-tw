---
title: SQLTablePrivileges |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLTablePrivileges function
ms.assetid: 8cce22d5-28b1-4b50-a5bc-1de03e0ffd6b
author: rothja
ms.author: jroth
ms.openlocfilehash: 63298330d3f0ebf707dbb42c337553c1f363deab
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595959"
---
# <a name="sqltableprivileges"></a><span data-ttu-id="25e1a-102">SQLTablePrivileges</span><span class="sxs-lookup"><span data-stu-id="25e1a-102">SQLTablePrivileges</span></span>
  <span data-ttu-id="25e1a-103">**SQLTablePrivileges**可以在靜態資料指標上執行。</span><span class="sxs-lookup"><span data-stu-id="25e1a-103">**SQLTablePrivileges** can be executed on a static cursor.</span></span> <span data-ttu-id="25e1a-104">嘗試在可更新的 (索引鍵集驅動或動態) 上執行**SQLTablePrivileges**時，會傳回 SQL_SUCCESS_WITH_INFO 指出資料指標類型已變更。</span><span class="sxs-lookup"><span data-stu-id="25e1a-104">An attempt to execute **SQLTablePrivileges** on an updatable (keyset-driven or dynamic) returns SQL_SUCCESS_WITH_INFO indicating the cursor type has been changed.</span></span>  
  
 <span data-ttu-id="25e1a-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native CLIENT ODBC 驅動程式藉由接受*CatalogName*參數的兩部分名稱，支援連結伺服器上之資料表的報告資訊： *Linked_Server_Name. Catalog_Name*。</span><span class="sxs-lookup"><span data-stu-id="25e1a-105">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver supports reporting information for tables on linked servers by accepting a two-part name for the *CatalogName* parameter: *Linked_Server_Name.Catalog_Name*.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25e1a-106">另請參閱</span><span class="sxs-lookup"><span data-stu-id="25e1a-106">See Also</span></span>  
 <span data-ttu-id="25e1a-107">[SQLTablePrivileges 函式] (https://go.microsoft.com/fwlink/?LinkId=59373\)</span><span class="sxs-lookup"><span data-stu-id="25e1a-107">[SQLTablePrivileges Function](https://go.microsoft.com/fwlink/?LinkId=59373\)</span></span>   
 [<span data-ttu-id="25e1a-108">ODBC API 實作詳細資料</span><span class="sxs-lookup"><span data-stu-id="25e1a-108">ODBC API Implementation Details</span></span>](odbc-api-implementation-details.md)  
  
  
