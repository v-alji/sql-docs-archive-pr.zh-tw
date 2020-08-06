---
title: 資料列層級安全性 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- row level security described
- row level security
- access control predicates
- security [SQL Server], predicate based access control
- predicate based security
ms.assetid: 7221fa4e-ca4a-4d5c-9f93-1b8a4af7b9e8
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: c67f84723e79b66d0454fb509f2fa9ced03dac7c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87697705"
---
# <a name="row-level-security"></a><span data-ttu-id="f19c0-102">資料列層級安全性</span><span class="sxs-lookup"><span data-stu-id="f19c0-102">Row-Level Security</span></span>
  <span data-ttu-id="f19c0-103">資料列層級安全性讓客戶能夠根據執行查詢之使用者的特性 (例如，群組成員資格或執行內容) 來控制資料庫資料表中的資料列存取。</span><span class="sxs-lookup"><span data-stu-id="f19c0-103">Row-Level Security enables customers to control access to rows in a database table based on the characteristics of the user executing a query (e.g., group membership or execution context).</span></span> <span data-ttu-id="f19c0-104">目前資料列層級安全性在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2016 中已可供使用。</span><span class="sxs-lookup"><span data-stu-id="f19c0-104">Row-Level Security is now available in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2016.</span></span> <span data-ttu-id="f19c0-105">如需這項功能的目前描述，請參閱目前文件中的 [資料列層級安全性](https://msdn.microsoft.com/library/dn765131.aspx) 。</span><span class="sxs-lookup"><span data-stu-id="f19c0-105">See [Row-Level Security](https://msdn.microsoft.com/library/dn765131.aspx) in the current documentation for the current description of this feature.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f19c0-106">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f19c0-106">See Also</span></span>  
 <span data-ttu-id="f19c0-107">[建立安全性原則 &#40;Azure SQL Database&#41;](/sql/t-sql/statements/create-security-policy-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f19c0-107">[CREATE SECURITY POLICY &#40;Azure SQL Database&#41;](/sql/t-sql/statements/create-security-policy-transact-sql) </span></span>  
 <span data-ttu-id="f19c0-108">[改變安全性原則 &#40;Azure SQL Database&#41;](/sql/t-sql/statements/alter-security-policy-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f19c0-108">[ALTER SECURITY POLICY &#40;Azure SQL Database&#41;](/sql/t-sql/statements/alter-security-policy-transact-sql) </span></span>  
 <span data-ttu-id="f19c0-109">[捨棄安全性原則 &#40;Azure SQL Database&#41;](/sql/t-sql/statements/drop-security-policy-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f19c0-109">[DROP SECURITY POLICY &#40;Azure SQL Database&#41;](/sql/t-sql/statements/drop-security-policy-transact-sql) </span></span>  
 <span data-ttu-id="f19c0-110">[CREATE FUNCTION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-function-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f19c0-110">[CREATE FUNCTION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-function-transact-sql) </span></span>  
 <span data-ttu-id="f19c0-111">[security_policies &#40;Azure SQL Database&#41;](/sql/relational-databases/system-catalog-views/sys-security-policies-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f19c0-111">[sys.security_policies &#40;Azure SQL Database&#41;](/sql/relational-databases/system-catalog-views/sys-security-policies-transact-sql) </span></span>  
 <span data-ttu-id="f19c0-112">[security_predicates &#40;Azure SQL Database&#41;](/sql/relational-databases/system-catalog-views/sys-security-predicates-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f19c0-112">[sys.security_predicates &#40;Azure SQL Database&#41;](/sql/relational-databases/system-catalog-views/sys-security-predicates-transact-sql) </span></span>  
 [<span data-ttu-id="f19c0-113">建立使用者定義函式 &#40;資料庫引擎&#41;</span><span class="sxs-lookup"><span data-stu-id="f19c0-113">Create User-defined Functions &#40;Database Engine&#41;</span></span>](../user-defined-functions/create-user-defined-functions-database-engine.md)  
  
  
