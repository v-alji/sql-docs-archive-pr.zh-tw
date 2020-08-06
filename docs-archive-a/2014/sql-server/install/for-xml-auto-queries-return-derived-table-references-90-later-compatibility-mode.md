---
title: FOR XML AUTO 查詢會傳回90（含）以後版本相容性模式中的衍生資料表參考 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- FOR XML AUTO [SQL Server]
ms.assetid: 10c32f06-f7e1-40e0-8f79-6d921f2bef1d
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 702cb2ca1d437dff03cee09c98d72082500709d2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87607249"
---
# <a name="for-xml-auto-queries-return-derived-table-references-in-90-or-later-compatibility-modes"></a><span data-ttu-id="d6e03-102">FOR XML AUTO 查詢在 90 或之後的相容性模式中，會傳回衍生的資料表參考</span><span class="sxs-lookup"><span data-stu-id="d6e03-102">FOR XML AUTO queries return derived table references in 90 or later compatibility modes</span></span>
  <span data-ttu-id="d6e03-103">當資料庫相容性層級設定為 90 或之後時，在 AUTO 模式中執行的 FOR XML 查詢會傳回衍生資料表別名的參考。</span><span class="sxs-lookup"><span data-stu-id="d6e03-103">When the database compatibility level is set to 90 or later, FOR XML queries that execute in AUTO mode return references to derived table aliases.</span></span> <span data-ttu-id="d6e03-104">當相容性層級設定為 80 時，FOR XML AUTO 查詢會傳回定義衍生資料表之基底資料表的參考。</span><span class="sxs-lookup"><span data-stu-id="d6e03-104">When the compatibility level is set to 80, FOR XML AUTO queries return references to the base tables that define a derived table.</span></span>  
  
## <a name="component"></a><span data-ttu-id="d6e03-105">元件</span><span class="sxs-lookup"><span data-stu-id="d6e03-105">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a><span data-ttu-id="d6e03-106">描述</span><span class="sxs-lookup"><span data-stu-id="d6e03-106">Description</span></span>  
 <span data-ttu-id="d6e03-107">例如，請考慮下表：</span><span class="sxs-lookup"><span data-stu-id="d6e03-107">For example, consider the following table:</span></span>  
  
```  
CREATE TABLE Test(id int);  
INSERT INTO Test VALUES(1);  
INSERT INTO Test VALUES(2);  
```  
  
 <span data-ttu-id="d6e03-108">下列查詢 (包括衍生資料表) 會在不同的相容性層級 (80、90 或之後) 底下產生不同的結果：</span><span class="sxs-lookup"><span data-stu-id="d6e03-108">The following query, which includes a derived table, produces different results under compatibility levels 80, 90, or later:</span></span>  
  
```  
SELECT * FROM   
   (SELECT a.id AS a, b.id AS b   
    FROM Test a JOIN Test b ON a.id=b.id)  
AS DerivedTest   
FOR XML AUTO;  
```  
  
 <span data-ttu-id="d6e03-109">在相容性層級 80 底下，此查詢會傳回下列結果。</span><span class="sxs-lookup"><span data-stu-id="d6e03-109">Under compatibility level 80, the query returns the following results.</span></span> <span data-ttu-id="d6e03-110">結果會參考衍生資料表的基底資料表別名 `a` 和 `b` 而非衍生資料表別名。</span><span class="sxs-lookup"><span data-stu-id="d6e03-110">The results reference the base table aliases `a` and `b` of the derived table instead of the derived table alias.</span></span>  
  
```  
<a a="1"><b b="1"/></a><a a="2"><b b="2"/></a>  
```  
  
 <span data-ttu-id="d6e03-111">在相容性層級 90 或之後底下，此查詢會傳回衍生資料表別名的參考 `DerivedTest` 而非衍生資料表之基底資料表的參考。</span><span class="sxs-lookup"><span data-stu-id="d6e03-111">Under compatibility level 90 or later, the query returns references to the derived table alias `DerivedTest` instead of to the derived table's base tables.</span></span>  
  
```  
<DerivedTest a="1" b="1"/><DerivedTest a="2" b="2"/>  
```  
  
## <a name="corrective-action"></a><span data-ttu-id="d6e03-112">更正動作</span><span class="sxs-lookup"><span data-stu-id="d6e03-112">Corrective Action</span></span>  
 <span data-ttu-id="d6e03-113">視需要修改您的應用程式，以便將包含衍生資料表且在相容性層級 90 或之後底下執行之 FOR XML AUTO 查詢所導致的變更納入考量。</span><span class="sxs-lookup"><span data-stu-id="d6e03-113">Modify your application as required to account for the changes in results of FOR XML AUTO queries that include derived tables and that run under compatibility level 90 or later.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6e03-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d6e03-114">See Also</span></span>  
 <span data-ttu-id="d6e03-115">[資料庫引擎升級問題](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="d6e03-115">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="d6e03-116">SQL Server 2014 Upgrade Advisor &#91;新的&#93;</span><span class="sxs-lookup"><span data-stu-id="d6e03-116">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  
