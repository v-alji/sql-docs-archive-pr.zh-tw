---
title: MSSQLSERVER_107 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 107 (Database Engine error)
ms.assetid: f33f514c-56aa-42e2-841b-e91244da90e2
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b9388bbda6f00b1aafd02caee1b6a7b8387564f9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598446"
---
# <a name="mssqlserver_107"></a><span data-ttu-id="3f101-102">MSSQLSERVER_107</span><span class="sxs-lookup"><span data-stu-id="3f101-102">MSSQLSERVER_107</span></span>
    
## <a name="details"></a><span data-ttu-id="3f101-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="3f101-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="3f101-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="3f101-104">Product Name</span></span>|<span data-ttu-id="3f101-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="3f101-105">SQL Server</span></span>|  
|<span data-ttu-id="3f101-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="3f101-106">Event ID</span></span>|<span data-ttu-id="3f101-107">107</span><span class="sxs-lookup"><span data-stu-id="3f101-107">107</span></span>|  
|<span data-ttu-id="3f101-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="3f101-108">Event Source</span></span>|<span data-ttu-id="3f101-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="3f101-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="3f101-110">元件</span><span class="sxs-lookup"><span data-stu-id="3f101-110">Component</span></span>|<span data-ttu-id="3f101-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="3f101-111">SQLEngine</span></span>|  
|<span data-ttu-id="3f101-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="3f101-112">Symbolic Name</span></span>|<span data-ttu-id="3f101-113">P_NOCORRMATCH</span><span class="sxs-lookup"><span data-stu-id="3f101-113">P_NOCORRMATCH</span></span>|  
|<span data-ttu-id="3f101-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="3f101-114">Message Text</span></span>|<span data-ttu-id="3f101-115">資料行前置詞 '%.\*ls' 與用於查詢中的資料表名稱或別名名稱不符。</span><span class="sxs-lookup"><span data-stu-id="3f101-115">The column prefix '%.\*ls' does not match with a table name or alias name used in the query.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="3f101-116">說明</span><span class="sxs-lookup"><span data-stu-id="3f101-116">Explanation</span></span>  
 <span data-ttu-id="3f101-117">查詢的選取清單包含以不正確方式使用資料行前置詞限定的星號 (\*)。</span><span class="sxs-lookup"><span data-stu-id="3f101-117">The select list of the query contains an asterisk (\*) that is incorrectly qualified with a column prefix.</span></span> <span data-ttu-id="3f101-118">這項錯誤可能會在下列情況下傳回：</span><span class="sxs-lookup"><span data-stu-id="3f101-118">This error can be returned under the following conditions:</span></span>  
  
-   <span data-ttu-id="3f101-119">資料行前置詞沒有對應至用於查詢中的任何資料表或別名名稱。</span><span class="sxs-lookup"><span data-stu-id="3f101-119">The column prefix does not correspond to any table or alias name used in the query.</span></span> <span data-ttu-id="3f101-120">例如，下列陳述式會使用別名名稱 (`T1`) 當做資料行前置詞，但是此別名並未定義於 FROM 子句中。</span><span class="sxs-lookup"><span data-stu-id="3f101-120">For example, the following statement uses an alias name (`T1`) as a column prefix, but the alias is not defined in the FROM clause.</span></span>  
  
    ```  
    SELECT T1.* FROM dbo.ErrorLog;  
    ```  
  
-   <span data-ttu-id="3f101-121">當您在 FROM 子句中提供資料表的別名名稱時，資料表名稱就會指定為資料行前置詞。</span><span class="sxs-lookup"><span data-stu-id="3f101-121">A table name is specified as a column prefix when an alias name for the table is supplied in the FROM clause.</span></span> <span data-ttu-id="3f101-122">例如，下列陳述式會使用資料表名稱 `ErrorLog` 當做資料行前置詞。不過，資料表具有在 FROM 子句中定義的別名 (`T1`)。</span><span class="sxs-lookup"><span data-stu-id="3f101-122">For example, the following statement uses the table name `ErrorLog` as the column prefix; however, the table has an alias (`T1`) defined in the FROM clause.</span></span>  
  
    ```  
    SELECT ErrorLog.* FROM dbo.ErrorLog AS T1;  
    ```  
  
     <span data-ttu-id="3f101-123">如果已經在 FROM 子句中提供資料表名稱的別名，您就只能使用此別名當做資料表中資料行的前置詞。</span><span class="sxs-lookup"><span data-stu-id="3f101-123">If an alias has been provided for a table name in the FROM clause, you can only use the alias to prefix columns from the table.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="3f101-124">使用者動作</span><span class="sxs-lookup"><span data-stu-id="3f101-124">User Action</span></span>  
 <span data-ttu-id="3f101-125">針對在查詢之 FROM 子句中指定的資料表名稱或別名名稱，比對資料行前置詞。</span><span class="sxs-lookup"><span data-stu-id="3f101-125">Match the column prefixes against the table names or alias names specified in the FROM clause of the query.</span></span> <span data-ttu-id="3f101-126">例如，您可以依照下列方式更正上述陳述式：</span><span class="sxs-lookup"><span data-stu-id="3f101-126">For example, the statements above can be corrected as follows:</span></span>  
  
```  
SELECT T1.* FROM dbo.ErrorLog AS T1;  
```  
  
 <span data-ttu-id="3f101-127">或</span><span class="sxs-lookup"><span data-stu-id="3f101-127">or</span></span>  
  
```  
SELECT ErrorLog.* FROM dbo.ErrorLog;  
```  
  
## <a name="see-also"></a><span data-ttu-id="3f101-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3f101-128">See Also</span></span>  
 [<span data-ttu-id="3f101-129">MSSQLSERVER_4104</span><span class="sxs-lookup"><span data-stu-id="3f101-129">MSSQLSERVER_4104</span></span>](mssqlserver-4104-database-engine-error.md)  
  
  
