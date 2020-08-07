---
title: 從 SQL Server 資料表中移除資料行 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- columns [OLE DB]
- removing columns
- DropColumn function
- SQL Server Native Client OLE DB provider, columns
ms.assetid: 210811b7-cbd6-421e-bc6e-df9482236768
author: rothja
ms.author: jroth
ms.openlocfilehash: 8f40c466910aae7e0d349cd4a65ab265282bc8eb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597084"
---
# <a name="removing-a-column-from-a-sql-server-table"></a><span data-ttu-id="5f002-102">從 SQL Server 資料表中移除資料行</span><span class="sxs-lookup"><span data-stu-id="5f002-102">Removing a Column from a SQL Server Table</span></span>
  <span data-ttu-id="5f002-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 提供者會公開**ITableDefinition：:D ropcolumn**函數。</span><span class="sxs-lookup"><span data-stu-id="5f002-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider exposes the **ITableDefinition::DropColumn** function.</span></span> <span data-ttu-id="5f002-104">如此可讓取用者從 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料表中移除資料行。</span><span class="sxs-lookup"><span data-stu-id="5f002-104">This allows consumers to remove a column from a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table.</span></span>  
  
 <span data-ttu-id="5f002-105">取用者會在 *pTableID* 參數中，將資料表名稱指定為 *uName* 聯集 *pwszName* 成員中的 Unicode 字元字串。</span><span class="sxs-lookup"><span data-stu-id="5f002-105">Consumers specify the table name as a Unicode character string in the *pwszName*member of the *uName* union in the *pTableID* parameter.</span></span> <span data-ttu-id="5f002-106">*pTableID* 的 *eKind* 成員必須是 DBKIND_NAME。</span><span class="sxs-lookup"><span data-stu-id="5f002-106">The *eKind*member of *pTableID* must be DBKIND_NAME.</span></span>  
  
 <span data-ttu-id="5f002-107">此取用者會在 *pColumnID* 參數內指示 *uName* 聯集之 *pwszName* 成員內的資料行名稱。</span><span class="sxs-lookup"><span data-stu-id="5f002-107">The consumer indicates a column name in the *pwszName*member of the *uName* union in the *pColumnID* parameter.</span></span> <span data-ttu-id="5f002-108">資料行名稱是一個 Unicode 字元字串。</span><span class="sxs-lookup"><span data-stu-id="5f002-108">The column name is a Unicode character string.</span></span> <span data-ttu-id="5f002-109">*pColumnID* 的 *eKind* 成員必須是 DBKIND_NAME。</span><span class="sxs-lookup"><span data-stu-id="5f002-109">The *eKind* member of *pColumnID* must be DBKIND_NAME.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5f002-110">範例</span><span class="sxs-lookup"><span data-stu-id="5f002-110">Example</span></span>  
  
### <a name="code"></a><span data-ttu-id="5f002-111">程式碼</span><span class="sxs-lookup"><span data-stu-id="5f002-111">Code</span></span>  
  
```  
DBID TableID;  
DBID ColumnID;  
HRESULT hr;  
  
TableID.eKind = DBKIND_NAME;  
TableID.uName.pwszName = L"MyTableName";  
  
ColumnID.eKind = DBKIND_NAME;  
ColumnID.uName.pwszName = L"MyColumnName";  
  
hr = m_pITableDefinition->DropColumn(&TableID, &ColumnID);  
```  
  
## <a name="see-also"></a><span data-ttu-id="5f002-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5f002-112">See Also</span></span>  
 [<span data-ttu-id="5f002-113">資料表和索引</span><span class="sxs-lookup"><span data-stu-id="5f002-113">Tables and Indexes</span></span>](tables-and-indexes.md)  
  
  
