---
title: 在原生編譯的預存程式中模擬 EXISTS 子句 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: c0e187c1-cbd9-463c-b417-8a734574f102
author: rothja
ms.author: jroth
ms.openlocfilehash: 7b16491b9a3729ad4df71c7ddceaee6db21777ff
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709414"
---
# <a name="simulating-an-exists-clause-in-a-natively-compiled-stored-procedure"></a><span data-ttu-id="64418-102">在原生編譯預存程序中模擬 EXISTS 子句</span><span class="sxs-lookup"><span data-stu-id="64418-102">Simulating an EXISTS Clause in a Natively Compiled Stored Procedure</span></span>
  <span data-ttu-id="64418-103">原生編譯預存程序不支援 `EXISTS` 子句，但是有解決方法：</span><span class="sxs-lookup"><span data-stu-id="64418-103">Natively compiled stored procedures do not support the `EXISTS` clause, but there is a workaround:</span></span>  
  
```sql  
DECLARE @exists BIT = 0  
SELECT TOP 1 @exists = 1 FROM MyTable WHERE ...  
IF @exists = 1  
```  
  
## <a name="see-also"></a><span data-ttu-id="64418-104">另請參閱</span><span class="sxs-lookup"><span data-stu-id="64418-104">See Also</span></span>  
 <span data-ttu-id="64418-105">[原生編譯預存程序的移轉問題](migration-issues-for-natively-compiled-stored-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="64418-105">[Migration Issues for Natively Compiled Stored Procedures](migration-issues-for-natively-compiled-stored-procedures.md) </span></span>  
 [<span data-ttu-id="64418-106">記憶體中的 OLTP 不支援 Transact-SQL 建構</span><span class="sxs-lookup"><span data-stu-id="64418-106">Transact-SQL Constructs Not Supported by In-Memory OLTP</span></span>](transact-sql-constructs-not-supported-by-in-memory-oltp.md)  
  
  
