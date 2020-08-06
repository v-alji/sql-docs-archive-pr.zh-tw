---
title: 安全性實體 | Microsoft Docs
ms.custom: ''
ms.date: 10/14/2015
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
f1_keywords:
- sql12.swb.roleproperties.selectobject.f1
helpviewer_keywords:
- securables [SQL Server]
- schemas [SQL Server], securables
- database securables [SQL Server]
- hierarchies [SQL Server], securables
- server securables [SQL Server]
ms.assetid: bfa748f0-70b0-453c-870a-04b7b205b9ff
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: ff2aaba72e2e5489694d31b35e594622c099acab
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688741"
---
# <a name="securables"></a><span data-ttu-id="63093-102">安全性實體</span><span class="sxs-lookup"><span data-stu-id="63093-102">Securables</span></span>
  <span data-ttu-id="63093-103">安全性實體是一種資源， [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 授權系統會管理其存取權。</span><span class="sxs-lookup"><span data-stu-id="63093-103">Securables are the resources to which the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] authorization system regulates access.</span></span> <span data-ttu-id="63093-104">例如，資料表是安全性實體。</span><span class="sxs-lookup"><span data-stu-id="63093-104">For example, a table is a securable.</span></span> <span data-ttu-id="63093-105">有些安全性實體可以包含在其他安全性實體內，因而建立稱為「範圍」的巢狀階層，以保護它們自己本身的安全。</span><span class="sxs-lookup"><span data-stu-id="63093-105">Some securables can be contained within others, creating nested hierarchies called "scopes" that can themselves be secured.</span></span> <span data-ttu-id="63093-106">安全性實體範圍為 **伺服器**、 **資料庫**以及 **結構描述**。</span><span class="sxs-lookup"><span data-stu-id="63093-106">The securable scopes are **server**, **database**, and **schema**.</span></span>  
  
## <a name="securable-scope-server"></a><span data-ttu-id="63093-107">安全性實體範圍：伺服器</span><span class="sxs-lookup"><span data-stu-id="63093-107">Securable scope: Server</span></span>  
 <span data-ttu-id="63093-108">**伺服器** 安全性實體範圍包含下列安全性實體：</span><span class="sxs-lookup"><span data-stu-id="63093-108">The **server** securable scope contains the following securables:</span></span>  
  
-   <span data-ttu-id="63093-109">可用性群組</span><span class="sxs-lookup"><span data-stu-id="63093-109">Availability group</span></span>  
  
-   <span data-ttu-id="63093-110">端點</span><span class="sxs-lookup"><span data-stu-id="63093-110">Endpoint</span></span>  
  
-   <span data-ttu-id="63093-111">登入</span><span class="sxs-lookup"><span data-stu-id="63093-111">Login</span></span>  
  
-   <span data-ttu-id="63093-112">伺服器角色</span><span class="sxs-lookup"><span data-stu-id="63093-112">Server role</span></span>  
  
-   <span data-ttu-id="63093-113">資料庫</span><span class="sxs-lookup"><span data-stu-id="63093-113">Database</span></span>  
  
## <a name="securable-scope-database"></a><span data-ttu-id="63093-114">安全性實體範圍：資料庫</span><span class="sxs-lookup"><span data-stu-id="63093-114">Securable scope: Database</span></span>  
 <span data-ttu-id="63093-115">**資料庫** 安全性實體範圍包含下列安全性實體：</span><span class="sxs-lookup"><span data-stu-id="63093-115">The **database** securable scope contains the following securables:</span></span>  
  
-   <span data-ttu-id="63093-116">應用程式角色</span><span class="sxs-lookup"><span data-stu-id="63093-116">Application role</span></span>  
  
-   <span data-ttu-id="63093-117">組件</span><span class="sxs-lookup"><span data-stu-id="63093-117">Assembly</span></span>  
  
-   <span data-ttu-id="63093-118">非對稱金鑰</span><span class="sxs-lookup"><span data-stu-id="63093-118">Asymmetric key</span></span>  
  
-   <span data-ttu-id="63093-119">憑證</span><span class="sxs-lookup"><span data-stu-id="63093-119">Certificate</span></span>  
  
-   <span data-ttu-id="63093-120">合約</span><span class="sxs-lookup"><span data-stu-id="63093-120">Contract</span></span>  
  
-   <span data-ttu-id="63093-121">FullText 目錄</span><span class="sxs-lookup"><span data-stu-id="63093-121">Fulltext catalog</span></span>  
  
-   <span data-ttu-id="63093-122">Fulltext 停用字詞表</span><span class="sxs-lookup"><span data-stu-id="63093-122">Fulltext stoplist</span></span>  
  
-   <span data-ttu-id="63093-123">訊息類型</span><span class="sxs-lookup"><span data-stu-id="63093-123">Message type</span></span>  
  
-   <span data-ttu-id="63093-124">遠端服務繫結</span><span class="sxs-lookup"><span data-stu-id="63093-124">Remote Service Binding</span></span>  
  
-   <span data-ttu-id="63093-125">(資料庫) 角色</span><span class="sxs-lookup"><span data-stu-id="63093-125">(Database) Role</span></span>  
  
-   <span data-ttu-id="63093-126">路由</span><span class="sxs-lookup"><span data-stu-id="63093-126">Route</span></span>  
  
-   <span data-ttu-id="63093-127">結構描述</span><span class="sxs-lookup"><span data-stu-id="63093-127">Schema</span></span>  
  
-   <span data-ttu-id="63093-128">搜尋屬性清單</span><span class="sxs-lookup"><span data-stu-id="63093-128">Search property list</span></span>  
  
-   <span data-ttu-id="63093-129">服務</span><span class="sxs-lookup"><span data-stu-id="63093-129">Service</span></span>  
  
-   <span data-ttu-id="63093-130">對稱金鑰</span><span class="sxs-lookup"><span data-stu-id="63093-130">Symmetric key</span></span>  
  
-   <span data-ttu-id="63093-131">User</span><span class="sxs-lookup"><span data-stu-id="63093-131">User</span></span>  
  
## <a name="securable-scope-schema"></a><span data-ttu-id="63093-132">安全性實體範圍：結構描述</span><span class="sxs-lookup"><span data-stu-id="63093-132">Securable scope: Schema</span></span>  
 <span data-ttu-id="63093-133">**結構描述** 安全性實體範圍包含下列安全性實體：</span><span class="sxs-lookup"><span data-stu-id="63093-133">The **schema** securable scope contains the following securables:</span></span>  
  
-   <span data-ttu-id="63093-134">類型</span><span class="sxs-lookup"><span data-stu-id="63093-134">Type</span></span>  
  
-   <span data-ttu-id="63093-135">XML 結構描述集合</span><span class="sxs-lookup"><span data-stu-id="63093-135">XML schema collection</span></span>  
  
-   <span data-ttu-id="63093-136">物件 - 物件類別有下列成員：</span><span class="sxs-lookup"><span data-stu-id="63093-136">Object - The object class has the following members:</span></span>  
  
    -   <span data-ttu-id="63093-137">Aggregate</span><span class="sxs-lookup"><span data-stu-id="63093-137">Aggregate</span></span>  
  
    -   <span data-ttu-id="63093-138">函式</span><span class="sxs-lookup"><span data-stu-id="63093-138">Function</span></span>  
  
    -   <span data-ttu-id="63093-139">程序</span><span class="sxs-lookup"><span data-stu-id="63093-139">Procedure</span></span>  
  
    -   <span data-ttu-id="63093-140">佇列</span><span class="sxs-lookup"><span data-stu-id="63093-140">Queue</span></span>  
  
    -   <span data-ttu-id="63093-141">同義字</span><span class="sxs-lookup"><span data-stu-id="63093-141">Synonym</span></span>  
  
    -   <span data-ttu-id="63093-142">Table</span><span class="sxs-lookup"><span data-stu-id="63093-142">Table</span></span>  
  
    -   <span data-ttu-id="63093-143">檢視</span><span class="sxs-lookup"><span data-stu-id="63093-143">View</span></span>  
  
## <a name="controlling-access-to-a-securable"></a><span data-ttu-id="63093-144">控制對安全性實體的存取權</span><span class="sxs-lookup"><span data-stu-id="63093-144">Controlling Access to a Securable</span></span>  
 <span data-ttu-id="63093-145">接收安全性實體權限的實體稱為主體。</span><span class="sxs-lookup"><span data-stu-id="63093-145">The entity that receives permission to a securable is called a principal.</span></span> <span data-ttu-id="63093-146">最常見的主體就是登入和資料庫使用者。</span><span class="sxs-lookup"><span data-stu-id="63093-146">The most common principals are logins and database users.</span></span> <span data-ttu-id="63093-147">安全性實體存取權的控制是透過授與或拒絕權限，或是將登入和使用者加入至具有存取權的角色。</span><span class="sxs-lookup"><span data-stu-id="63093-147">Access to securables is controlled by granting or denying permissions, or by adding logins and user to roles which have access.</span></span> <span data-ttu-id="63093-148">如需控制權限的資訊，請參閱 [GRANT &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-transact-sql)、[REVOKE &#40;Transact-SQL&#41;](/sql/t-sql/statements/revoke-transact-sql)、[DENY &#40;Transact-SQL&#41;](/sql/t-sql/statements/deny-transact-sql)、[sp_addrolemember &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addrolemember-transact-sql) 和 [sp_droprolemember &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-droprolemember-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="63093-148">For information about controlling permissions, see [GRANT &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-transact-sql), [REVOKE &#40;Transact-SQL&#41;](/sql/t-sql/statements/revoke-transact-sql), [DENY &#40;Transact-SQL&#41;](/sql/t-sql/statements/deny-transact-sql), [sp_addrolemember &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addrolemember-transact-sql), and [sp_droprolemember &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-droprolemember-transact-sql).</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="63093-149">在安裝時為系統物件授與的預設權限，經過仔細評估可能面臨的威脅，因此在強化 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 安裝的過程中無須改變。</span><span class="sxs-lookup"><span data-stu-id="63093-149">The default permissions that are granted to system objects at the time of setup are carefully evaluated against possible threats and need not be altered as part of hardening the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] installation.</span></span> <span data-ttu-id="63093-150">系統物件的任何權限變更，都可能會限制或破壞其功效，而可能會讓您的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 安裝處於不支援的狀態。</span><span class="sxs-lookup"><span data-stu-id="63093-150">Any changes to the permissions on the system objects could limit or break the functionality and could potentially leave your [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] installation in an unsupported state.</span></span>  
  
## <a name="related-content"></a><span data-ttu-id="63093-151">相關內容</span><span class="sxs-lookup"><span data-stu-id="63093-151">Related Content</span></span>  
 [<span data-ttu-id="63093-152">保護 SQL Server 的安全</span><span class="sxs-lookup"><span data-stu-id="63093-152">Securing SQL Server</span></span>](securing-sql-server.md)  
  
 [<span data-ttu-id="63093-153">sys.database_principals &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="63093-153">sys.database_principals &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-database-principals-transact-sql)  
  
 [<span data-ttu-id="63093-154">sys.database_role_members &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="63093-154">sys.database_role_members &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-database-role-members-transact-sql)  
  
 [<span data-ttu-id="63093-155">sys.server_principals &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="63093-155">sys.server_principals &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-server-principals-transact-sql)  
  
 [<span data-ttu-id="63093-156">sys.server_role_members &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="63093-156">sys.server_role_members &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-server-role-members-transact-sql)  
  
 [<span data-ttu-id="63093-157">sys.sql_logins &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="63093-157">sys.sql_logins &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-sql-logins-transact-sql)  
  
  
