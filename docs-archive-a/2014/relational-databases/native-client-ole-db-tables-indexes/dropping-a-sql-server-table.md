---
title: 卸除 SQL Server 資料表 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- tables [OLE DB]
- deleting tables
- SQL Server Native Client OLE DB provider, tables
- removing tables
- dropping tables
ms.assetid: b6d6c4de-43c6-473e-92aa-34ffddd58cbe
author: rothja
ms.author: jroth
ms.openlocfilehash: 4d7bea98a3afcd0022f66117b6bde2d968a866b7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597085"
---
# <a name="dropping-a-sql-server-table"></a><span data-ttu-id="ac7bc-102">卸除 SQL Server 資料表</span><span class="sxs-lookup"><span data-stu-id="ac7bc-102">Dropping a SQL Server Table</span></span>
  <span data-ttu-id="ac7bc-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 提供者會公開**ITableDefinition：:D roptable**函數。</span><span class="sxs-lookup"><span data-stu-id="ac7bc-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider exposes the **ITableDefinition::DropTable** function.</span></span> <span data-ttu-id="ac7bc-104">這可讓取用者 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 從資料庫中移除資料表。</span><span class="sxs-lookup"><span data-stu-id="ac7bc-104">This allows consumers to remove a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table from a database.</span></span>  
  
 <span data-ttu-id="ac7bc-105">取用者會在 *pTableID* 參數中，將資料表名稱指定為 *uName* 聯集之 *pwszName* 成員中的 Unicode 字元字串。</span><span class="sxs-lookup"><span data-stu-id="ac7bc-105">Consumers specify the table name as a Unicode character string in the *pwszName* member of the *uName* union in the *pTableID* parameter.</span></span> <span data-ttu-id="ac7bc-106">*pTableID* 的 *eKind* 成員必須是 DBKIND_NAME。</span><span class="sxs-lookup"><span data-stu-id="ac7bc-106">The *eKind* member of *pTableID* must be DBKIND_NAME.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac7bc-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ac7bc-107">See Also</span></span>  
 [<span data-ttu-id="ac7bc-108">資料表和索引</span><span class="sxs-lookup"><span data-stu-id="ac7bc-108">Tables and Indexes</span></span>](tables-and-indexes.md)  
  
  
