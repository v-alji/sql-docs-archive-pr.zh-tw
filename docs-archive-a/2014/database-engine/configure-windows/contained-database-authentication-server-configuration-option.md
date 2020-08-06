---
title: 自主資料庫驗證伺服器組態選項 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
f1_keywords:
- contained_database_authentication_TSQL
- contained database authentication
helpviewer_keywords:
- contained database, enabling
- contained database authentication option
ms.assetid: b80768d2-ac20-4035-a335-d9adb74b3f6e
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: cf5bf07c8b0913ff81f31ff0ca64a18eee0f2ac2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597324"
---
# <a name="contained-database-authentication-server-configuration-option"></a><span data-ttu-id="2b7c8-102">自主資料庫驗證伺服器組態選項</span><span class="sxs-lookup"><span data-stu-id="2b7c8-102">contained database authentication Server Configuration Option</span></span>
  <span data-ttu-id="2b7c8-103">使用  [自主資料庫驗證] 選項，可在 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]執行個體上啟用自主資料庫。</span><span class="sxs-lookup"><span data-stu-id="2b7c8-103">Use the **contained database authentication** option to enable contained databases on the instance of [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].</span></span>  
  
 <span data-ttu-id="2b7c8-104">此伺服器選項可讓您控制 **自主資料庫驗證**。</span><span class="sxs-lookup"><span data-stu-id="2b7c8-104">This server option allows you to control **contained database authentication**.</span></span>  
  
-   <span data-ttu-id="2b7c8-105">當執行個體的  [自主資料庫驗證] 為關 (0) 時，自主資料庫便無法建立，或附加到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="2b7c8-105">When **contained database authentication** is off (0) for the instance, contained databases cannot be created, or attached to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
-   <span data-ttu-id="2b7c8-106">當執行個體的  [自主資料庫驗證] 為開 (1) 時，自主資料庫就可以建立，或附加到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="2b7c8-106">When **contained database authentication** is on (1) for the instance, contained databases can be created, or attached to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
 <span data-ttu-id="2b7c8-107">自主資料庫包含了定義資料庫所需的所有資料庫設定和中繼資料，而且對於已安裝資料庫的 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 執行個體沒有組態相依性。</span><span class="sxs-lookup"><span data-stu-id="2b7c8-107">A contained database includes all database settings and metadata required to define the database and has no configuration dependencies on the instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] where the database is installed.</span></span> <span data-ttu-id="2b7c8-108">使用者可以連接至資料庫，而不需要在 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 層級驗證登入。</span><span class="sxs-lookup"><span data-stu-id="2b7c8-108">Users can connect to the database without authenticating a login at the [!INCLUDE[ssDE](../../includes/ssde-md.md)] level.</span></span> <span data-ttu-id="2b7c8-109">將資料庫與 Database Engine 隔離，可讓您輕鬆地將資料庫移至另一個 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]執行個體。</span><span class="sxs-lookup"><span data-stu-id="2b7c8-109">Isolating the database from the Database Engine makes it possible to easily move the database to another instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="2b7c8-110">將所有資料庫設定包含在資料庫中，可讓資料庫擁有者管理該資料庫的所有組態設定。</span><span class="sxs-lookup"><span data-stu-id="2b7c8-110">Including all the database settings in the database enables database owners to manage all the configuration settings for the database.</span></span> <span data-ttu-id="2b7c8-111">如需自主資料庫的詳細資訊，請參閱 [自主資料庫](../../relational-databases/databases/contained-databases.md)。</span><span class="sxs-lookup"><span data-stu-id="2b7c8-111">For more information about contained databases, see [Contained Databases](../../relational-databases/databases/contained-databases.md).</span></span>  
  
 <span data-ttu-id="2b7c8-112">如果 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的執行個體具有任何自主資料庫，您就可以使用 **RECONFIGURE WITH OVERRIDE** 陳述式，將 [自主資料庫驗證]  設定設為 0。</span><span class="sxs-lookup"><span data-stu-id="2b7c8-112">If an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] has any contained databases the **contained database authentication** setting can be set to 0 by using the **RECONFIGURE WITH OVERRIDE** statement.</span></span> <span data-ttu-id="2b7c8-113">將 [自主資料庫驗證]  設為 0 將會停用自主資料庫的自主資料庫驗證。</span><span class="sxs-lookup"><span data-stu-id="2b7c8-113">Setting **contained database authentication** to 0 will disable contained database authentication for the contained databases.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="2b7c8-114">當啟用自主的資料庫時，具有 ALTER ANY USER 權限 (例如 db_owner 和 db_accessadmin 資料庫角色) 的資料庫使用者可以存取資料庫，且可藉此來存取 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="2b7c8-114">When contained databases are enabled, database users with the ALTER ANY USER permission, such as members of the db_owner and db_accessadmin database roles, can grant access to databases and by doing so, grant access to the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="2b7c8-115">這表示伺服器存取的控制權不再限於系統管理員和安全性管理員固定伺服器角色，且以具有 CONTROL SERVER和 ALTER ANY LOGIN 伺服器層級的權限來登入。</span><span class="sxs-lookup"><span data-stu-id="2b7c8-115">This means that control over access to the server is no longer limited to members of the sysadmin and securityadmin fixed server role, and logins with the server level CONTROL SERVER and ALTER ANY LOGIN permission.</span></span> <span data-ttu-id="2b7c8-116">在允許自主資料庫之前，您應該了解自主資料庫的相關風險。</span><span class="sxs-lookup"><span data-stu-id="2b7c8-116">Before allowing contained databases, you should understand the risks associated with contained databases.</span></span> <span data-ttu-id="2b7c8-117">如需詳細資訊，請參閱 [Security Best Practices with Contained Databases](../../relational-databases/databases/security-best-practices-with-contained-databases.md)。</span><span class="sxs-lookup"><span data-stu-id="2b7c8-117">For more information, see [Security Best Practices with Contained Databases](../../relational-databases/databases/security-best-practices-with-contained-databases.md).</span></span>  
  
## <a name="examples"></a><span data-ttu-id="2b7c8-118">範例</span><span class="sxs-lookup"><span data-stu-id="2b7c8-118">Examples</span></span>  
 <span data-ttu-id="2b7c8-119">下列範例會在 [!INCLUDE[ssDE](../../includes/ssde-md.md)]執行個體上啟用自主資料庫。</span><span class="sxs-lookup"><span data-stu-id="2b7c8-119">The following example enables contained databases on the instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
```sql  
sp_configure 'contained database authentication', 1;  
GO  
RECONFIGURE;  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="2b7c8-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2b7c8-120">See Also</span></span>  
 <span data-ttu-id="2b7c8-121">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="2b7c8-121">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span></span>  
 <span data-ttu-id="2b7c8-122">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="2b7c8-122">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span></span>  
 [<span data-ttu-id="2b7c8-123">伺服器組態選項 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="2b7c8-123">Server Configuration Options &#40;SQL Server&#41;</span></span>](server-configuration-options-sql-server.md)  
  
  
