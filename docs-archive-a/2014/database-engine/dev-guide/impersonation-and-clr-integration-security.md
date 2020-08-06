---
title: 模擬和 CLR 整合安全性 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: reference
helpviewer_keywords:
- impersonation [CLR integration]
- security [CLR integration]
- execution context [CLR integration]
- user impersonation [CLR integration]
- context [CLR integration]
ms.assetid: 1495a7af-2248-4cee-afdb-9269fb3a7774
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: a2313733c5a24f28c44571dd230ddc58fc9a1264
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709862"
---
# <a name="impersonation-and-clr-integration-security"></a><span data-ttu-id="d6b90-102">模擬和 CLR 整合安全性</span><span class="sxs-lookup"><span data-stu-id="d6b90-102">Impersonation and CLR Integration Security</span></span>
  <span data-ttu-id="d6b90-103">當 Managed 程式碼存取外部資源時，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 不會自動模擬用來執行常式的目前執行內容。</span><span class="sxs-lookup"><span data-stu-id="d6b90-103">When managed code accesses external resources, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] does not automatically impersonate the current execution context under which the routine is executing.</span></span> <span data-ttu-id="d6b90-104">`EXTERNAL_ACCESS` 和 `UNSAFE` 組件中的程式碼可以明確模擬目前的執行內容。</span><span class="sxs-lookup"><span data-stu-id="d6b90-104">Code in `EXTERNAL_ACCESS` and `UNSAFE` assemblies can explicitly impersonate the current execution context.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d6b90-105">如需模擬中行為變更的相關資訊，請參閱[SQL Server 2014 中資料庫引擎功能的重大變更](../breaking-changes-to-database-engine-features-in-sql-server-2016.md)。</span><span class="sxs-lookup"><span data-stu-id="d6b90-105">For information on behavior changes in impersonation, see [Breaking Changes to Database Engine Features in SQL Server 2014](../breaking-changes-to-database-engine-features-in-sql-server-2016.md).</span></span>  
  
 <span data-ttu-id="d6b90-106">同處理序資料存取提供者會提供應用程式開發介面 `SqlContext.WindowsIdentity`，可用來擷取與目前安全性內容相關聯的 Token。</span><span class="sxs-lookup"><span data-stu-id="d6b90-106">The in-process data access provider provides an application programming interface, `SqlContext.WindowsIdentity`, that can be used to retrieve the token associated with the current security context.</span></span> <span data-ttu-id="d6b90-107">`EXTERNAL_ACCESS` 和 `UNSAFE` 組件中的 Managed 程式碼可以使用這個方法來擷取此內容並使用 .NET Framework `WindowsIdentity.Impersonate` 方法來模擬該內容。</span><span class="sxs-lookup"><span data-stu-id="d6b90-107">Managed code in `EXTERNAL_ACCESS` and `UNSAFE` assemblies can use this method to retrieve the context and use the .NET Framework `WindowsIdentity.Impersonate` method to impersonate that context.</span></span> <span data-ttu-id="d6b90-108">使用者程式碼明確模擬時適用下列限制：</span><span class="sxs-lookup"><span data-stu-id="d6b90-108">The following restrictions apply when user code explicitly impersonates:</span></span>  
  
-   <span data-ttu-id="d6b90-109">當 Managed 程式碼處於模擬狀態時，不允許同處理序資料存取。</span><span class="sxs-lookup"><span data-stu-id="d6b90-109">In-process data access is not allowed when managed code is in an impersonated state.</span></span> <span data-ttu-id="d6b90-110">程式碼可以恢復模擬，然後呼叫同處理序資料存取。</span><span class="sxs-lookup"><span data-stu-id="d6b90-110">Code can undo impersonation and then call in-process data access.</span></span> <span data-ttu-id="d6b90-111">請注意，這樣做需要儲存原始 `WindowsImpersonationContext` 方法的傳回值 (`Impersonate` 物件)，以及針對這個 `Undo` 呼叫 `WindowsImpersonationContext` 方法。</span><span class="sxs-lookup"><span data-stu-id="d6b90-111">Note that this requires storing the return value (a `WindowsImpersonationContext` object) of the original `Impersonate` method, and calling the `Undo` method on this `WindowsImpersonationContext`.</span></span>  
  
     <span data-ttu-id="d6b90-112">這項限制表示進行同處理序資料存取時，一定會在適用於工作階段之目前安全性內容的內容中進行，</span><span class="sxs-lookup"><span data-stu-id="d6b90-112">This restriction means that when in-process data access occurs, it is always in the context of the current security context in effect for the session.</span></span> <span data-ttu-id="d6b90-113">無法由 Managed 程式碼內部的明確模擬所修改。</span><span class="sxs-lookup"><span data-stu-id="d6b90-113">It cannot be modified by explicit impersonation within managed code.</span></span>  
  
-   <span data-ttu-id="d6b90-114">若為以非同步方式執行的 Managed 程式碼 (例如，透過 `UNSAFE` 組件，建立執行緒並以非同步方式執行程式碼)，永遠不允許同處理序資料存取。</span><span class="sxs-lookup"><span data-stu-id="d6b90-114">For managed code executing asynchronously (for example, through `UNSAFE` assemblies creating threads and running code asynchronously), in-process data access is never allowed.</span></span> <span data-ttu-id="d6b90-115">不論是否存在模擬，這項限制都成立。</span><span class="sxs-lookup"><span data-stu-id="d6b90-115">This is true whether or not there is impersonation.</span></span>  
  
 <span data-ttu-id="d6b90-116">執行程式碼所在的模擬內容與 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 不同時，它就無法執行同處理序資料存取呼叫。它應該先恢復模擬內容，然後再進行同處理序資料存取呼叫。</span><span class="sxs-lookup"><span data-stu-id="d6b90-116">When code is running in an impersonated context that is different from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], it cannot perform in-process data access calls; it should undo the impersonation context before making in-process data access calls.</span></span> <span data-ttu-id="d6b90-117">從 Managed 程式碼進行同處理序資料存取時，進入 Managed 程式碼之 [!INCLUDE[tsql](../../includes/tsql-md.md)] 進入點的原始執行內容一定會用於授權。</span><span class="sxs-lookup"><span data-stu-id="d6b90-117">When in-process data access is made from managed code, the original execution context of the [!INCLUDE[tsql](../../includes/tsql-md.md)] entry point into the managed code is always used for authorization.</span></span>  
  
 <span data-ttu-id="d6b90-118">除非 `EXTERNAL_ACCESS` 組件和 `UNSAFE` 組件依照先前所述的方式主動模擬目前的安全性內容，否則它們會使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服務帳戶來存取作業系統資源。</span><span class="sxs-lookup"><span data-stu-id="d6b90-118">Both `EXTERNAL_ACCESS` assemblies and `UNSAFE` assemblies access operating system resources with the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service account, unless they voluntarily impersonate the current security context as previously described.</span></span> <span data-ttu-id="d6b90-119">因此，`EXTERNAL_ACCESS` 組件的作者比 `SAFE` 組件的作者需要更高的信任層級，而此信任層級是由 `EXTERNAL ACCESS` 登入層級權限所指定。</span><span class="sxs-lookup"><span data-stu-id="d6b90-119">Because of this, the authors of `EXTERNAL_ACCESS` assemblies require a higher level of trust than those of `SAFE` assemblies, which is specified by the `EXTERNAL ACCESS` login-level permission.</span></span> <span data-ttu-id="d6b90-120">只有受信任可在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服務帳戶底下執行程式碼的登入才應該被授與 `EXTERNAL ACCESS` 權限。</span><span class="sxs-lookup"><span data-stu-id="d6b90-120">Only logins who are trusted to run code under the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service account should be granted the `EXTERNAL ACCESS` permission.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6b90-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d6b90-121">See Also</span></span>  
 <span data-ttu-id="d6b90-122">[CLR 整合安全性](../../relational-databases/clr-integration/security/clr-integration-security.md) </span><span class="sxs-lookup"><span data-stu-id="d6b90-122">[CLR Integration Security](../../relational-databases/clr-integration/security/clr-integration-security.md) </span></span>  
 [<span data-ttu-id="d6b90-123">連接的模擬和認證</span><span class="sxs-lookup"><span data-stu-id="d6b90-123">Impersonation and Credentials for Connections</span></span>](../../relational-databases/clr-integration/data-access/impersonation-and-credentials-for-connections.md)  
  
  
