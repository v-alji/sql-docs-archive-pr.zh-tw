---
title: 將資料行新增至 SQL Server 資料表 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- columns [OLE DB]
- AddColumn function
- SQL Server Native Client OLE DB provider, columns
- adding columns
ms.assetid: 22bae18a-bc9d-4617-8660-ed8b17a468d4
author: rothja
ms.author: jroth
ms.openlocfilehash: 97aa2656ccde662a34e1dd80fd662b22f601d4ec
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707442"
---
# <a name="adding-a-column-to-a-sql-server-table"></a><span data-ttu-id="02309-102">將資料行加入至 SQL Server 資料表</span><span class="sxs-lookup"><span data-stu-id="02309-102">Adding a Column to a SQL Server Table</span></span>
  <span data-ttu-id="02309-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 提供者會公開**ITableDefinition：： AddColumn**函數。</span><span class="sxs-lookup"><span data-stu-id="02309-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider exposes the **ITableDefinition::AddColumn** function.</span></span> <span data-ttu-id="02309-104">如此可讓取用者將資料行加入至 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料表。</span><span class="sxs-lookup"><span data-stu-id="02309-104">This allows consumers to add a column to a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table.</span></span>  
  
 <span data-ttu-id="02309-105">當您將資料行加入至 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料表時， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供者取用者的限制如下：</span><span class="sxs-lookup"><span data-stu-id="02309-105">When you add a column to a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider consumer is constrained as follows:</span></span>  
  
-   <span data-ttu-id="02309-106">如果 DBPROP_COL_AUTOINCREMENT 是 VARIANT_TRUE，DBPROP_COL_NULLABLE 就必須是 VARIANT_FALSE。</span><span class="sxs-lookup"><span data-stu-id="02309-106">If DBPROP_COL_AUTOINCREMENT is VARIANT_TRUE, DBPROP_COL_NULLABLE must be VARIANT_FALSE.</span></span>  
  
-   <span data-ttu-id="02309-107">如果資料行是使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **timestamp** 資料類型所定義，DBPROP_COL_NULLABLE 就必須是 VARIANT_FALSE。</span><span class="sxs-lookup"><span data-stu-id="02309-107">If the column is defined by using the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **timestamp** data type, DBPROP_COL_NULLABLE must be VARIANT_FALSE.</span></span>  
  
-   <span data-ttu-id="02309-108">如果是其他任何資料行定義，DBPROP_COL_NULLABLE 必須為 VARIANT_TRUE。</span><span class="sxs-lookup"><span data-stu-id="02309-108">For any other column definition, DBPROP_COL_NULLABLE must be VARIANT_TRUE.</span></span>  
  
 <span data-ttu-id="02309-109">取用者會在 *pTableID* 參數中，將資料表名稱指定為 *uName* 聯集之 *pwszName* 成員中的 Unicode 字元字串。</span><span class="sxs-lookup"><span data-stu-id="02309-109">Consumers specify the table name as a Unicode character string in the *pwszName* member of the *uName* union in the *pTableID* parameter.</span></span> <span data-ttu-id="02309-110">*pTableID* 的 *eKind* 成員必須是 DBKIND_NAME。</span><span class="sxs-lookup"><span data-stu-id="02309-110">The *eKind* member of *pTableID* must be DBKIND_NAME.</span></span>  
  
 <span data-ttu-id="02309-111">在 *pColumnDesc* 之 DBCOLUMNDESC 參數的 *dbcid* 成員中，新的資料行名稱會指定為 *uName* 聯集之 *pwszName* 成員內的 Unicode 字元字串。</span><span class="sxs-lookup"><span data-stu-id="02309-111">The new column name is specified as a Unicode character string in the *pwszName* member of the *uName* union in the *dbcid* member of the DBCOLUMNDESC parameter *pColumnDesc*.</span></span> <span data-ttu-id="02309-112">*eKind* 成員必須是 DBKIND_NAME。</span><span class="sxs-lookup"><span data-stu-id="02309-112">The *eKind* member must be DBKIND_NAME.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02309-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="02309-113">See Also</span></span>  
 <span data-ttu-id="02309-114">[資料表和索引](tables-and-indexes.md) </span><span class="sxs-lookup"><span data-stu-id="02309-114">[Tables and Indexes](tables-and-indexes.md) </span></span>  
 [<span data-ttu-id="02309-115">ALTER TABLE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="02309-115">ALTER TABLE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-table-transact-sql)  
  
  
