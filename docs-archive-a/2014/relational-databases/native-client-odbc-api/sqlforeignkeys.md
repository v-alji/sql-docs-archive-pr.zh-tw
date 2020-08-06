---
title: SQLForeignKeys |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLForeignKeys function
ms.assetid: 6c01ce0d-30d7-4c86-8705-3ab254d8a845
author: rothja
ms.author: jroth
ms.openlocfilehash: a61e80867abb8ecb4d2628b74dc9956051c8e4ce
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594080"
---
# <a name="sqlforeignkeys"></a><span data-ttu-id="7d9a4-102">SQLForeignKeys</span><span class="sxs-lookup"><span data-stu-id="7d9a4-102">SQLForeignKeys</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="7d9a4-103">支援串聯更新，而且會透過外部索引鍵條件約束機制刪除。</span><span class="sxs-lookup"><span data-stu-id="7d9a4-103">supports cascading updates and deletes through the foreign key constraint mechanism.</span></span> <span data-ttu-id="7d9a4-104">如果在 FOREIGN KEY 條件約束的 ON UPDATE 和/或 ON DELETE 子句上指定 CASCADE 選項，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 會針對 UPDATE_RULE 和/或 DELETE_RULE 資料行傳回 SQL_NO_ACTION。</span><span class="sxs-lookup"><span data-stu-id="7d9a4-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] returns SQL_CASCADE for UPDATE_RULE and/or DELETE_RULE columns if CASCADE option is specified on the ON UPDATE and/or ON DELETE clause of the FOREIGN KEY constraints.</span></span> <span data-ttu-id="7d9a4-105">如果在 FOREIGN KEY 條件約束的 ON UPDATE 和/或 ON DELETE 子句上指定 NO ACTION 選項，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 會針對 UPDATE_RULE 和/或 DELETE_RULE 資料行傳回 SQL_NO_ACTION。</span><span class="sxs-lookup"><span data-stu-id="7d9a4-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] returns SQL_NO_ACTION for UPDATE_RULE and/or DELETE_RULE columns if NO ACTION option is specified on the ON UPDATE and/or ON DELETE clause of the FOREIGN KEY constraints.</span></span>  
  
 <span data-ttu-id="7d9a4-106">當任何**SQLForeignKeys**參數中出現不正確值時， **SQLForeignKeys**會在執行時傳回 SQL_SUCCESS。</span><span class="sxs-lookup"><span data-stu-id="7d9a4-106">When invalid values are present in any **SQLForeignKeys** parameter, **SQLForeignKeys** returns SQL_SUCCESS on execution.</span></span> <span data-ttu-id="7d9a4-107">當這些參數中使用了不正確值時， **SQLFetch**會傳回 SQL_NO_DATA。</span><span class="sxs-lookup"><span data-stu-id="7d9a4-107">**SQLFetch** returns SQL_NO_DATA when invalid values are used in these parameters.</span></span>  
  
 <span data-ttu-id="7d9a4-108">**SQLForeignKeys**可以在靜態伺服器資料指標上執行。</span><span class="sxs-lookup"><span data-stu-id="7d9a4-108">**SQLForeignKeys** can be executed on a static server cursor.</span></span> <span data-ttu-id="7d9a4-109">嘗試在可更新的 (動態或索引鍵集上執行**SQLForeignKeys**) 資料指標會傳回 SQL_SUCCESS_WITH_INFO，表示資料指標類型已變更。</span><span class="sxs-lookup"><span data-stu-id="7d9a4-109">An attempt to execute **SQLForeignKeys** on an updatable (dynamic or keyset) cursor returns SQL_SUCCESS_WITH_INFO indicating that the cursor type has been changed.</span></span>  
  
 <span data-ttu-id="7d9a4-110">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native CLIENT ODBC 驅動程式藉由接受*FKCatalogName*和*sqlforeignkeys*參數的兩部分名稱，支援連結伺服器上之資料表的報告資訊： *Linked_Server_Name. Catalog_Name*。</span><span class="sxs-lookup"><span data-stu-id="7d9a4-110">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver supports reporting information for tables on linked servers by accepting a two-part name for the *FKCatalogName* and *PKCatalogName* parameters: *Linked_Server_Name.Catalog_Name*.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d9a4-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7d9a4-111">See Also</span></span>  
 <span data-ttu-id="7d9a4-112">[SQLForeignKeys 函式](https://go.microsoft.com/fwlink/?LinkId=59344) </span><span class="sxs-lookup"><span data-stu-id="7d9a4-112">[SQLForeignKeys Function](https://go.microsoft.com/fwlink/?LinkId=59344) </span></span>  
 [<span data-ttu-id="7d9a4-113">ODBC API 實作詳細資料</span><span class="sxs-lookup"><span data-stu-id="7d9a4-113">ODBC API Implementation Details</span></span>](odbc-api-implementation-details.md)  
  
  
