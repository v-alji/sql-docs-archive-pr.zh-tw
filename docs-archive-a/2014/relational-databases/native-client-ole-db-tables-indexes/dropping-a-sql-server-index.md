---
title: 卸除 SQL Server 索引 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- removing indexes
- deleting indexes
- DropIndex function
- dropping indexes
- SQL Server Native Client OLE DB provider, indexes
- indexes [OLE DB]
ms.assetid: add3ba14-10b1-4723-b7c0-3e83689e9fdd
author: rothja
ms.author: jroth
ms.openlocfilehash: 1267cc92645ff8b28757ad2d266e58917fcb4b28
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597086"
---
# <a name="dropping-a-sql-server-index"></a><span data-ttu-id="b05ec-102">卸除 SQL Server 索引</span><span class="sxs-lookup"><span data-stu-id="b05ec-102">Dropping a SQL Server Index</span></span>
  <span data-ttu-id="b05ec-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 提供者會公開**IIndexDefinition：:D ropindex**函數。</span><span class="sxs-lookup"><span data-stu-id="b05ec-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider exposes the **IIndexDefinition::DropIndex** function.</span></span> <span data-ttu-id="b05ec-104">如此可讓取用者從 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料表中移除索引。</span><span class="sxs-lookup"><span data-stu-id="b05ec-104">This allows consumers to remove an index from a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table.</span></span>  
  
 <span data-ttu-id="b05ec-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 提供者會將一些 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 主鍵和唯一的條件約束公開為索引。</span><span class="sxs-lookup"><span data-stu-id="b05ec-105">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider exposes some [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PRIMARY KEY and UNIQUE constraints as indexes.</span></span> <span data-ttu-id="b05ec-106">資料表擁有者、資料庫擁有者以及某些系統管理角色成員都可以修改 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料表，卸除條件約束。</span><span class="sxs-lookup"><span data-stu-id="b05ec-106">The table owner, database owner, and some administrative role members can modify a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table, dropping a constraint.</span></span> <span data-ttu-id="b05ec-107">根據預設，只有資料表擁有者可以卸除現有的索引。</span><span class="sxs-lookup"><span data-stu-id="b05ec-107">By default, only the table owner can drop an existing index.</span></span> <span data-ttu-id="b05ec-108">因此，**DropIndex** 的成功或失敗，不但取決於應用程式使用者的存取權限，也取決於所指出之索引的類型。</span><span class="sxs-lookup"><span data-stu-id="b05ec-108">Therefore, **DropIndex** success or failure depends not only on the application user's access rights but also on the type of index indicated.</span></span>  
  
 <span data-ttu-id="b05ec-109">取用者會在 *pTableID* 參數中，將資料表名稱指定為 *uName* 聯集之 *pwszName* 成員中的 Unicode 字元字串。</span><span class="sxs-lookup"><span data-stu-id="b05ec-109">Consumers specify the table name as a Unicode character string in the *pwszName* member of the *uName* union in the *pTableID* parameter.</span></span> <span data-ttu-id="b05ec-110">*pTableID* 的 *eKind* 成員必須是 DBKIND_NAME。</span><span class="sxs-lookup"><span data-stu-id="b05ec-110">The *eKind* member of *pTableID* must be DBKIND_NAME.</span></span>  
  
 <span data-ttu-id="b05ec-111">取用者會在 *pIndexID* 參數中，將索引名稱指定為 *uName* 聯集之 *pwszName* 成員中的 Unicode 字元字串。</span><span class="sxs-lookup"><span data-stu-id="b05ec-111">Consumers specify the index name as a Unicode character string in the *pwszName* member of the *uName* union in the *pIndexID* parameter.</span></span> <span data-ttu-id="b05ec-112">*pIndexID* 的 *eKind* 成員必須是 DBKIND_NAME。</span><span class="sxs-lookup"><span data-stu-id="b05ec-112">The *eKind* member of *pIndexID* must be DBKIND_NAME.</span></span> <span data-ttu-id="b05ec-113">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]當*pIndexID*為 null 時，Native Client OLE DB 提供者不支援在資料表上卸載所有索引的 OLE DB 功能。</span><span class="sxs-lookup"><span data-stu-id="b05ec-113">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider does not support the OLE DB feature of dropping all indexes on a table when *pIndexID* is null.</span></span> <span data-ttu-id="b05ec-114">如果 *pIndexID* 為 Null，會傳回 E_INVALIDARG。</span><span class="sxs-lookup"><span data-stu-id="b05ec-114">If *pIndexID* is null, E_INVALIDARG is returned.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b05ec-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b05ec-115">See Also</span></span>  
 <span data-ttu-id="b05ec-116">[資料表和索引](tables-and-indexes.md) </span><span class="sxs-lookup"><span data-stu-id="b05ec-116">[Tables and Indexes](tables-and-indexes.md) </span></span>  
 <span data-ttu-id="b05ec-117">[ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="b05ec-117">[ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql) </span></span>  
 [<span data-ttu-id="b05ec-118">DROP INDEX &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="b05ec-118">DROP INDEX &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/drop-index-transact-sql)  
  
  
