---
title: 權限階層 (Database Engine) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
f1_keywords:
- sql12.swb.server.permissions.f1--May use common.permissions
helpviewer_keywords:
- security [SQL Server], denying access
- hierarchies [SQL Server], permissions
- securables [SQL Server]
- security [SQL Server], permissions
- permissions [SQL Server], hierarchy
- security [SQL Server], granting access
ms.assetid: f6d20a55-ef03-4e14-85f9-009902889866
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 9a04e5595e509de63b362b31b240e113e635581d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87697750"
---
# <a name="permissions-hierarchy-database-engine"></a><span data-ttu-id="42c19-102">權限階層 (Database Engine)</span><span class="sxs-lookup"><span data-stu-id="42c19-102">Permissions Hierarchy (Database Engine)</span></span>
  <span data-ttu-id="42c19-103">[!INCLUDE[ssDE](../../../includes/ssde-md.md)] 會管理階層式實體集合，這些實體可使用權限來確保安全性。</span><span class="sxs-lookup"><span data-stu-id="42c19-103">The [!INCLUDE[ssDE](../../../includes/ssde-md.md)] manages a hierarchical collection of entities that can be secured with permissions.</span></span> <span data-ttu-id="42c19-104">這些實體也稱為「安全性實體」。</span><span class="sxs-lookup"><span data-stu-id="42c19-104">These entities are known as *securables*.</span></span> <span data-ttu-id="42c19-105">最明顯的安全性實體為伺服器和資料庫，但是個別權限可以在更細微的層次進行設定。</span><span class="sxs-lookup"><span data-stu-id="42c19-105">The most prominent securables are servers and databases, but discrete permissions can be set at a much finer level.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="42c19-106">透過驗證主體是否已被授與適當的權限，進而規範主體在安全性實體上的動作。</span><span class="sxs-lookup"><span data-stu-id="42c19-106">regulates the actions of principals on securables by verifying that they have been granted appropriate permissions.</span></span>

 <span data-ttu-id="42c19-107">下圖顯示 [!INCLUDE[ssDE](../../../includes/ssde-md.md)] 權限階層之間的關係。</span><span class="sxs-lookup"><span data-stu-id="42c19-107">The following illustration shows the relationships among the [!INCLUDE[ssDE](../../../includes/ssde-md.md)] permissions hierarchies.</span></span>

 <span data-ttu-id="42c19-108">![資料庫引擎權限階層的圖表](../../database-engine/media/wj-security-layers.gif "資料庫引擎權限階層的圖表")</span><span class="sxs-lookup"><span data-stu-id="42c19-108">![Diagram of Database Engine permissions hierarchies](../../database-engine/media/wj-security-layers.gif "Diagram of Database Engine permissions hierarchies")</span></span>

## <a name="chart-of-sql-server-permissions"></a><span data-ttu-id="42c19-109">SQL Server 權限的圖表</span><span class="sxs-lookup"><span data-stu-id="42c19-109">Chart of SQL Server Permissions</span></span>
 <span data-ttu-id="42c19-110">如需所有 [!INCLUDE[ssDE](../../../includes/ssde-md.md)] 權限的 PDF 格式海報大小圖表，請參閱 [https://github.com/microsoft/sql-server-samples/blob/master/samples/features/security/permissions-posters/Microsoft_SQL_Server_2017_and_Azure_SQL_Database_permissions_infographic.pdf](https://github.com/microsoft/sql-server-samples/blob/master/samples/features/security/permissions-posters/Microsoft_SQL_Server_2017_and_Azure_SQL_Database_permissions_infographic.pdf)。</span><span class="sxs-lookup"><span data-stu-id="42c19-110">For a poster sized chart of all [!INCLUDE[ssDE](../../../includes/ssde-md.md)] permissions in pdf format, see [https://github.com/microsoft/sql-server-samples/blob/master/samples/features/security/permissions-posters/Microsoft_SQL_Server_2017_and_Azure_SQL_Database_permissions_infographic.pdf](https://github.com/microsoft/sql-server-samples/blob/master/samples/features/security/permissions-posters/Microsoft_SQL_Server_2017_and_Azure_SQL_Database_permissions_infographic.pdf).</span></span>

## <a name="working-with-permissions"></a><span data-ttu-id="42c19-111">使用權限</span><span class="sxs-lookup"><span data-stu-id="42c19-111">Working with Permissions</span></span>
 <span data-ttu-id="42c19-112">您可以透過常見的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 查詢 GRANT、DENY 與 REVOKE 來操控權限。</span><span class="sxs-lookup"><span data-stu-id="42c19-112">Permissions can be manipulated with the familiar [!INCLUDE[tsql](../../includes/tsql-md.md)] queries GRANT, DENY, and REVOKE.</span></span> <span data-ttu-id="42c19-113">您可以在 [sys.server_permissions](/sql/relational-databases/system-catalog-views/sys-server-permissions-transact-sql) 和 [sys.database_permissions](/sql/relational-databases/system-catalog-views/sys-database-permissions-transact-sql) 目錄檢視中查看權限的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="42c19-113">Information about permissions is visible in the [sys.server_permissions](/sql/relational-databases/system-catalog-views/sys-server-permissions-transact-sql) and [sys.database_permissions](/sql/relational-databases/system-catalog-views/sys-database-permissions-transact-sql) catalog views.</span></span> <span data-ttu-id="42c19-114">此外，也支援使用內建函數來查詢權限資訊。</span><span class="sxs-lookup"><span data-stu-id="42c19-114">There is also support for querying permissions information by using built-in functions.</span></span>

## <a name="see-also"></a><span data-ttu-id="42c19-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="42c19-115">See Also</span></span>
 <span data-ttu-id="42c19-116">[保護 SQL Server](securing-sql-server.md) [許可權 &#40;資料庫引擎&#41;](permissions-database-engine.md) [安全性實體](securables.md)[主體 &#40;資料庫引擎](authentication-access/principals-database-engine.md)&#41;sql [server 授與 &#40;](/sql/t-sql/statements/grant-transact-sql) transact-sql&#41;[撤銷 &#40;](/sql/t-sql/statements/revoke-transact-sql) transact-sql&#41;[&#40;transact-sql&#41;](/sql/t-sql/statements/deny-transact-sql) [HAS_PERMS_BY_NAME &#40;](/sql/t-sql/functions/has-perms-by-name-transact-sql) transact-sql&#41;[sys.](/sql/relational-databases/system-catalog-views/sys-server-permissions-transact-sql) [fn_builtin_permissions &#40;transact-sql](/sql/relational-databases/system-functions/sys-fn-builtin-permissions-transact-sql)&#41;server_permissions &#40;transact-sql&#41;。 database_permissions &#40;[transact-sql&#41;](/sql/relational-databases/system-catalog-views/sys-database-permissions-transact-sql)</span><span class="sxs-lookup"><span data-stu-id="42c19-116">[Securing SQL Server](securing-sql-server.md) [Permissions &#40;Database Engine&#41;](permissions-database-engine.md) [Securables](securables.md) [Principals &#40;Database Engine&#41;](authentication-access/principals-database-engine.md) [GRANT &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-transact-sql) [REVOKE &#40;Transact-SQL&#41;](/sql/t-sql/statements/revoke-transact-sql) [DENY &#40;Transact-SQL&#41;](/sql/t-sql/statements/deny-transact-sql) [HAS_PERMS_BY_NAME &#40;Transact-SQL&#41;](/sql/t-sql/functions/has-perms-by-name-transact-sql) [sys.fn_builtin_permissions &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/sys-fn-builtin-permissions-transact-sql) [sys.server_permissions &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-permissions-transact-sql) [sys.database_permissions &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-permissions-transact-sql)</span></span>


