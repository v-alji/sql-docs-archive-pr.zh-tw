---
title: MSSQLSERVER_4104 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 4104 (Database Engine error)
ms.assetid: 52dc32d8-97ad-4ef0-834d-2e68f215d007
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: cbbc28a3e15af6fdc8fd44633ccbdfc46e49149d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598433"
---
# <a name="mssqlserver_4104"></a><span data-ttu-id="47d18-102">MSSQLSERVER_4104</span><span class="sxs-lookup"><span data-stu-id="47d18-102">MSSQLSERVER_4104</span></span>
    
## <a name="details"></a><span data-ttu-id="47d18-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="47d18-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="47d18-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="47d18-104">Product Name</span></span>|<span data-ttu-id="47d18-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="47d18-105">SQL Server</span></span>|  
|<span data-ttu-id="47d18-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="47d18-106">Event ID</span></span>|<span data-ttu-id="47d18-107">4104</span><span class="sxs-lookup"><span data-stu-id="47d18-107">4104</span></span>|  
|<span data-ttu-id="47d18-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="47d18-108">Event Source</span></span>|<span data-ttu-id="47d18-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="47d18-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="47d18-110">元件</span><span class="sxs-lookup"><span data-stu-id="47d18-110">Component</span></span>|<span data-ttu-id="47d18-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="47d18-111">SQLEngine</span></span>|  
|<span data-ttu-id="47d18-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="47d18-112">Symbolic Name</span></span>|<span data-ttu-id="47d18-113">ALG_MULTI_ID_BAD</span><span class="sxs-lookup"><span data-stu-id="47d18-113">ALG_MULTI_ID_BAD</span></span>|  
|<span data-ttu-id="47d18-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="47d18-114">Message Text</span></span>|<span data-ttu-id="47d18-115">無法繫結多重部分 (Multi-Part) 識別碼 "%.\*ls"。</span><span class="sxs-lookup"><span data-stu-id="47d18-115">The multi-part identifier "%.\*ls" could not be bound.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="47d18-116">說明</span><span class="sxs-lookup"><span data-stu-id="47d18-116">Explanation</span></span>  
 <span data-ttu-id="47d18-117">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中實體的名稱也稱為 *「識別碼」* (Identifier)。</span><span class="sxs-lookup"><span data-stu-id="47d18-117">The name of an entity in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is referred to as its *identifier*.</span></span> <span data-ttu-id="47d18-118">每當參考實體 (例如在查詢中指定資料行和資料表名稱) 時，您就可以使用識別碼。</span><span class="sxs-lookup"><span data-stu-id="47d18-118">You use identifiers whenever you reference entities, for example, by specifying column and table names in a query.</span></span> <span data-ttu-id="47d18-119">多重部分識別碼包含一個或多個限定詞，當做識別碼的前置詞。</span><span class="sxs-lookup"><span data-stu-id="47d18-119">A multi-part identifier contains one or more qualifiers as a prefix for the identifier.</span></span> <span data-ttu-id="47d18-120">例如，資料表識別碼的前置詞可能是包含此資料表之資料庫名稱和結構描述等限定詞，或者資料行識別碼的前置詞可能是資料表名稱或資料表別名等限定詞。</span><span class="sxs-lookup"><span data-stu-id="47d18-120">For example, a table identifier may be prefixed with qualifiers such as the database name and schema name in which the table is contained, or a column identifier may be prefixed with qualifiers such as a table name or table alias.</span></span>  
  
 <span data-ttu-id="47d18-121">錯誤 4104 表示指定的多重部分識別碼無法對應至現有的實體。</span><span class="sxs-lookup"><span data-stu-id="47d18-121">Error 4104 indicates that the specified multi-part identifier could not be mapped to an existing entity.</span></span> <span data-ttu-id="47d18-122">這項錯誤可能會在下列情況下傳回：</span><span class="sxs-lookup"><span data-stu-id="47d18-122">This error can be returned under the following conditions:</span></span>  
  
-   <span data-ttu-id="47d18-123">提供成為資料行名稱之前置詞的限定詞沒有對應至用於查詢中的任何資料表或別名名稱。</span><span class="sxs-lookup"><span data-stu-id="47d18-123">The qualifier supplied as a prefix for a column name does not correspond to any table or alias name used in the query.</span></span>  
  
     <span data-ttu-id="47d18-124">例如，下列陳述式會使用資料表別名 (`Dept`) 當做資料行前置詞，但是此資料表別名並未在 FROM 子句中參考。</span><span class="sxs-lookup"><span data-stu-id="47d18-124">For example, the following statement uses a table alias (`Dept`) as a column prefix, but the table alias is not referenced in the FROM clause.</span></span>  
  
    ```  
    SELECT Dept.Name FROM HumanResources.Department;  
    ```  
  
     <span data-ttu-id="47d18-125">在下列陳述式中，多重部分資料行識別碼 `TableB.KeyCol` 會在 WHERE 子句中指定成兩個資料表之間 JOIN 條件的一部分。不過，`TableB` 並未在查詢中明確參考。</span><span class="sxs-lookup"><span data-stu-id="47d18-125">In the following statements, a multi-part column identifier `TableB.KeyCol` is specified in the WHERE clause as part of a JOIN condition between two tables, however, `TableB` is not explicitly referenced in the query.</span></span>  
  
    ```  
    DELETE FROM TableA WHERE TableA.KeyCol = TableB.KeyCol;  
    ```  
  
    ```  
    SELECT 'X' FROM TableA WHERE TableB.KeyCol = TableA.KeyCol;  
    ```  
  
-   <span data-ttu-id="47d18-126">資料表的別名名稱提供在 FROM 子句，但是針對資料行所提供的限定詞就是資料表名稱。</span><span class="sxs-lookup"><span data-stu-id="47d18-126">An alias name for the table is supplied in the FROM clause, but the qualifier supplied for a column is the table name.</span></span> <span data-ttu-id="47d18-127">例如，下列陳述式會使用資料表名稱 `Department` 當做資料行前置詞。不過，資料表具有在 FROM 子句中參考的別名 (`Dept`)。</span><span class="sxs-lookup"><span data-stu-id="47d18-127">For example, the following statement uses the table name `Department` as the column prefix; however, the table has an alias (`Dept`) referenced in the FROM clause.</span></span>  
  
    ```  
    SELECT Department.Name FROM HumanResources.Department AS Dept;  
    ```  
  
     <span data-ttu-id="47d18-128">使用別名時，此資料表名稱就無法在陳述式中的其他位置使用。</span><span class="sxs-lookup"><span data-stu-id="47d18-128">When an alias is used, the table name cannot be used elsewhere in the statement.</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="47d18-129">無法判斷多重部分識別碼是參考前置詞為資料表的資料行，還是前置詞為資料行之 CLR 使用者定義資料類型 (UDT) 的屬性。</span><span class="sxs-lookup"><span data-stu-id="47d18-129">is unable to determine if the multi-part identifier refers to a column prefixed by a table or to a property of a CLR user-defined data type (UDT) prefixed by a column.</span></span> <span data-ttu-id="47d18-130">發生這種情況的原因是在資料行名稱和屬性名稱之間使用句號分隔字元 (.)，藉以參考 UDT 資料行的屬性，而這種方式就如同在資料行名稱前面加上資料表名稱。</span><span class="sxs-lookup"><span data-stu-id="47d18-130">This happens because properties of UDT columns are referenced by using the period separator (.) between the column name and the property name in the same way that a column name is prefixed with a table name.</span></span> <span data-ttu-id="47d18-131">下列範例會建立兩份資料表：`a` 和 `b`。</span><span class="sxs-lookup"><span data-stu-id="47d18-131">The following example creates two tables, `a` and `b`.</span></span> <span data-ttu-id="47d18-132">資料表 `b` 包含資料行 `a`，而且此資料行會使用 CLR UDT `dbo.myudt2` 當做其資料類型。</span><span class="sxs-lookup"><span data-stu-id="47d18-132">Table `b` contains column `a`, which uses a CLR UDT `dbo.myudt2` as its data type.</span></span> <span data-ttu-id="47d18-133">SELECT 陳述式包含多重部分識別碼 `a.c2`。</span><span class="sxs-lookup"><span data-stu-id="47d18-133">The SELECT statement contains a multi-part identifier `a.c2`.</span></span>  
  
    ```  
    CREATE TABLE a (c2 int);   
    GO  
    ```  
  
    ```  
    CREATE TABLE b (a dbo.myudt2);   
    GO  
    ```  
  
    ```  
    SELECT a.c2 FROM a, b;   
    ```  
  
     <span data-ttu-id="47d18-134">假設 UDT `myudt2` 沒有名為 `c2` 的屬性，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 無法判斷識別碼 `a.c2` 會參考資料表 `a` 中的資料行 `c2`，還是資料表 `b` 中屬性 `c2` 的資料行 `a`。</span><span class="sxs-lookup"><span data-stu-id="47d18-134">Assuming that the UDT `myudt2` does not have a property named `c2`, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] cannot determine whether identifier `a.c2`refers to column `c2` in table `a` or to the column `a`, property `c2` in table `b`.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="47d18-135">使用者動作</span><span class="sxs-lookup"><span data-stu-id="47d18-135">User Action</span></span>  
  
-   <span data-ttu-id="47d18-136">針對在查詢之 FROM 子句中指定的資料表名稱或別名名稱，比對資料行前置詞。</span><span class="sxs-lookup"><span data-stu-id="47d18-136">Match the column prefixes against the table names or alias names specified in the FROM clause of the query.</span></span> <span data-ttu-id="47d18-137">如果已經在 FROM 子句中定義資料表名稱的別名，您就只能使用此別名當做與該資料表相關聯之資料行的限定詞。</span><span class="sxs-lookup"><span data-stu-id="47d18-137">If an alias is defined for a table name in the FROM clause, you can only use the alias as a qualifier for columns associated with that table.</span></span>  
  
     <span data-ttu-id="47d18-138">您可以依照下列方式更正上述參考 `HumanResources.Department` 資料表的陳述式：</span><span class="sxs-lookup"><span data-stu-id="47d18-138">The statements above that reference the `HumanResources.Department` table can be corrected as follows:</span></span>  
  
    ```  
    SELECT Dept.Name FROM HumanResources.Department AS Dept;  
    GO  
    ```  
  
    ```  
    SELECT Department.Name FROM HumanResources.Department;  
    GO  
    ```  
  
-   <span data-ttu-id="47d18-139">確定所有資料表都指定在查詢中，而且資料表之間的 JOIN 條件已正確指定。</span><span class="sxs-lookup"><span data-stu-id="47d18-139">Ensure that all tables are specified in the query and that the JOIN conditions between tables are specified correctly.</span></span> <span data-ttu-id="47d18-140">您可以依照下列方式更正上述 DELETE 陳述式：</span><span class="sxs-lookup"><span data-stu-id="47d18-140">The DELETE statement above can be corrected as follows:</span></span>  
  
    ```  
    DELETE FROM dbo.TableA  
    WHERE TableA.KeyCol = (SELECT TableB.KeyCol   
                            FROM TableB   
                            WHERE TableA.KeyCol = TableB.KeyCol);  
    GO  
    ```  
  
     <span data-ttu-id="47d18-141">您可以依照下列方式更正 `TableA` 的上述 SELECT 陳述式：</span><span class="sxs-lookup"><span data-stu-id="47d18-141">The SELECT statement above for `TableA` can be corrected as follows:</span></span>  
  
    ```  
    SELECT 'X' FROM TableA, TableB WHERE TableB.KeyCol = TableA.KeyCol;  
    ```  
  
     <span data-ttu-id="47d18-142">或</span><span class="sxs-lookup"><span data-stu-id="47d18-142">or</span></span>  
  
    ```  
    SELECT 'X' FROM TableA INNER JOIN TableB ON TableB.KeyCol = TableA.KeyCol;  
    ```  
  
-   <span data-ttu-id="47d18-143">針對識別碼使用唯一且清楚定義的名稱。</span><span class="sxs-lookup"><span data-stu-id="47d18-143">Use unique, clearly defined names for identifiers.</span></span> <span data-ttu-id="47d18-144">這樣做可讓您的程式碼更容易讀取和維護，而且也會盡可能降低多個實體具有模稜兩可參考的風險。</span><span class="sxs-lookup"><span data-stu-id="47d18-144">Doing so makes your code easier to read and maintain, and it also minimizes the risk of ambiguous references to multiple entities.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47d18-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="47d18-145">See Also</span></span>  
 <span data-ttu-id="47d18-146">[MSSQLSERVER_107](mssqlserver-107-database-engine-error.md) </span><span class="sxs-lookup"><span data-stu-id="47d18-146">[MSSQLSERVER_107](mssqlserver-107-database-engine-error.md) </span></span>  
 [<span data-ttu-id="47d18-147">資料庫識別碼</span><span class="sxs-lookup"><span data-stu-id="47d18-147">Database Identifiers</span></span>](../databases/database-identifiers.md)  
  
  
