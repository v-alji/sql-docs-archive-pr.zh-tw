---
title: 啟用 CLR 整合 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- clr enabled option
- common language runtime [SQL Server], enabling
ms.assetid: eb3e9c64-7486-42e7-baf6-c956fb311a2c
author: rothja
ms.author: jroth
ms.openlocfilehash: d7187906f1376deb81ca7ff4770af7b12b63c022
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704149"
---
# <a name="enabling-clr-integration"></a><span data-ttu-id="babb8-102">啟用 CLR 整合</span><span class="sxs-lookup"><span data-stu-id="babb8-102">Enabling CLR Integration</span></span>
  <span data-ttu-id="babb8-103">預設會停用 Common Language Runtime (CLR) 整合功能，且為了使用 CLR 整合所實作的物件，必須啟用這個功能。</span><span class="sxs-lookup"><span data-stu-id="babb8-103">The common language runtime (CLR) integration feature is off by default, and must be enabled in order to use objects that are implemented using CLR integration.</span></span> <span data-ttu-id="babb8-104">若要啟用 CLR 整合，請使用**sp_configure**預存程式的**clr enabled**選項：</span><span class="sxs-lookup"><span data-stu-id="babb8-104">To enable CLR integration, use the **clr enabled** option of the **sp_configure** stored procedure:</span></span>  
  
```  
  
sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE;  
GO  
sp_configure 'clr enabled', 1;  
GO  
RECONFIGURE;  
GO  
```  
  
 <span data-ttu-id="babb8-105">您可以將**clr enabled**選項設定為0，以停用 clr 整合。</span><span class="sxs-lookup"><span data-stu-id="babb8-105">You can disable CLR integration by setting the **clr enabled** option to 0.</span></span> <span data-ttu-id="babb8-106">當您停用 CLR 整合時，[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 會停止執行所有 CLR 常式，並卸載所有應用程式網域。</span><span class="sxs-lookup"><span data-stu-id="babb8-106">When you disable CLR integration, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] stops executing all CLR routines and unloads all application domains.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="babb8-107">若要啟用 CLR 整合，您必須擁有 ALTER SETTINGS 伺服器層級許可權，這會由**sysadmin**和**serveradmin**固定伺服器角色的成員隱含持有。</span><span class="sxs-lookup"><span data-stu-id="babb8-107">To enable CLR integration, you must have ALTER SETTINGS server level permission, which is implicitly held by members of the **sysadmin** and **serveradmin** fixed server roles.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="babb8-108">啟動伺服器時，以大量記憶體及大量處理器設定的電腦可能無法載入 SQL Server 的 CLR 整合功能。</span><span class="sxs-lookup"><span data-stu-id="babb8-108">Computers configured with large amounts of memory and a large number of processors may fail to load the CLR integration feature of SQL Server when starting the server.</span></span> <span data-ttu-id="babb8-109">若要解決此問題，請使用 **-gmemory_to_reserve** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 服務啟動選項來啟動伺服器，並指定夠大的記憶體值。</span><span class="sxs-lookup"><span data-stu-id="babb8-109">To address this issue, start the server by using the **-gmemory_to_reserve**[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] service startup option, and specify a memory value large enough.</span></span> <span data-ttu-id="babb8-110">如需詳細資訊，請參閱 [Database Engine Service Startup Options](../../database-engine/configure-windows/database-engine-service-startup-options.md)。</span><span class="sxs-lookup"><span data-stu-id="babb8-110">For more information, see [Database Engine Service Startup Options](../../database-engine/configure-windows/database-engine-service-startup-options.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="babb8-111">輕量型共用不支援 Common Language Runtime (CLR) 的執行。</span><span class="sxs-lookup"><span data-stu-id="babb8-111">Common language runtime (CLR) execution is not supported under lightweight pooling.</span></span> <span data-ttu-id="babb8-112">在啟用 CLR 整合以前，您必須停用輕量型共用。</span><span class="sxs-lookup"><span data-stu-id="babb8-112">Before enabling CLR integration, you must disable lightweight pooling.</span></span> <span data-ttu-id="babb8-113">如需詳細資訊，請參閱 [輕量型共用伺服器組態選項](../../database-engine/configure-windows/lightweight-pooling-server-configuration-option.md)。</span><span class="sxs-lookup"><span data-stu-id="babb8-113">For more information, see [lightweight pooling Server Configuration Option](../../database-engine/configure-windows/lightweight-pooling-server-configuration-option.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="babb8-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="babb8-114">See Also</span></span>  
 <span data-ttu-id="babb8-115">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="babb8-115">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span></span>  
 <span data-ttu-id="babb8-116">[CLR 已啟用伺服器組態選項](../../database-engine/configure-windows/clr-enabled-server-configuration-option.md) </span><span class="sxs-lookup"><span data-stu-id="babb8-116">[clr enabled Server Configuration Option](../../database-engine/configure-windows/clr-enabled-server-configuration-option.md) </span></span>  
 <span data-ttu-id="babb8-117">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="babb8-117">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span></span>  
 <span data-ttu-id="babb8-118">[GRANT &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="babb8-118">[GRANT &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-transact-sql) </span></span>  
 [<span data-ttu-id="babb8-119">伺服器層級角色</span><span class="sxs-lookup"><span data-stu-id="babb8-119">Server-Level Roles</span></span>](../security/authentication-access/server-level-roles.md)  
  
  
