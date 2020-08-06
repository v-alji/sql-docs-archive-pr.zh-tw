---
title: 連接的模擬和認證 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- impersonation [CLR integration]
- security [CLR integration]
- database objects [CLR integration], connections
- connections [CLR integration]
- authentication [CLR integration]
- user impersonation [CLR integration]
- credentials [CLR integration]
- database objects [CLR integration], security
ms.assetid: 293dce7d-1db2-4657-992f-8c583d6e9ebb
author: rothja
ms.author: jroth
ms.openlocfilehash: cdbc52e07f4502adda7301ce7f635c050ed9c3c1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597164"
---
# <a name="impersonation-and-credentials-for-connections"></a><span data-ttu-id="8ed19-102">連接的模擬和認證</span><span class="sxs-lookup"><span data-stu-id="8ed19-102">Impersonation and Credentials for Connections</span></span>
  <span data-ttu-id="8ed19-103">在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Common Language Runtime (CLR) 整合中，使用 Windows 驗證是很複雜的工作，但是要比使用 SQL Server 驗證來得安全。</span><span class="sxs-lookup"><span data-stu-id="8ed19-103">In the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] common language runtime (CLR) integration, using Windows Authentication is complex, but is more secure than using SQL Server Authentication.</span></span> <span data-ttu-id="8ed19-104">當使用 Windows 驗證時，請牢記以下的考量事項。</span><span class="sxs-lookup"><span data-stu-id="8ed19-104">When using Windows Authentication, keep in mind the following considerations.</span></span>  
  
 <span data-ttu-id="8ed19-105">根據預設，連接到 Windows 的 SQL Server 處理序需要 SQL Server Windows 服務帳戶的安全性內容。</span><span class="sxs-lookup"><span data-stu-id="8ed19-105">By default, a SQL Server process that connects out to Windows acquires the security context of the SQL Server Windows service account.</span></span> <span data-ttu-id="8ed19-106">但是，可將 CLR 函數對應到 Proxy 識別，好讓它的傳出連接具有與 Windows 服務帳戶不同的安全性內容。</span><span class="sxs-lookup"><span data-stu-id="8ed19-106">But it is possible to map a CLR function to a proxy identity, so that its outbound connections have a different security context than that of the Windows service account.</span></span>  
  
 <span data-ttu-id="8ed19-107">在某些情況下，您可能會想要使用 `SqlContext.WindowsIdentity` 屬性來模擬呼叫端，而不是以此服務帳戶的身分執行。</span><span class="sxs-lookup"><span data-stu-id="8ed19-107">In some cases, you may want to impersonate the caller by using the `SqlContext.WindowsIdentity` property instead of running as the service account.</span></span> <span data-ttu-id="8ed19-108">`WindowsIdentity` 執行個體代表叫用呼叫程式碼之用戶端的識別，而且只有當用戶端使用 Windows 驗證時才可使用。</span><span class="sxs-lookup"><span data-stu-id="8ed19-108">The `WindowsIdentity` instance represents the identity of the client that invoked the calling code, and is only available when the client used Windows Authentication.</span></span> <span data-ttu-id="8ed19-109">在您取得 `WindowsIdentity` 執行個體之後，您可以呼叫 `Impersonate` 來變更執行緒的安全性 Token，然後代表用戶端開啟 ADO.NET 連接。</span><span class="sxs-lookup"><span data-stu-id="8ed19-109">After you have obtained the `WindowsIdentity` instance, you can call `Impersonate` to change the security token of the thread, and then open ADO.NET connections on behalf of the client.</span></span>  
  
 <span data-ttu-id="8ed19-110">呼叫 SQLCoNtext WindowsIdentity 之後，您就無法存取本機資料，也無法存取系統資料。</span><span class="sxs-lookup"><span data-stu-id="8ed19-110">After you call SQLContext.WindowsIdentity.Impersonate, you cannot access local data and you cannot access system data.</span></span> <span data-ttu-id="8ed19-111">若要再次存取資料，您必須呼叫 WindowsImpersonationCoNtext。</span><span class="sxs-lookup"><span data-stu-id="8ed19-111">To access data again, you have to call WindowsImpersonationContext.Undo.</span></span>  
  
 <span data-ttu-id="8ed19-112">下列範例示範如何使用 `SqlContext.WindowsIdentity` 屬性來模擬呼叫端。</span><span class="sxs-lookup"><span data-stu-id="8ed19-112">The following example shows how to impersonate the caller by using the `SqlContext.WindowsIdentity` property.</span></span>  
  
 <span data-ttu-id="8ed19-113">Visual C#</span><span class="sxs-lookup"><span data-stu-id="8ed19-113">Visual C#</span></span>  
  
```  
WindowsIdentity clientId = null;  
WindowsImpersonationContext impersonatedUser = null;  
  
clientId = SqlContext.WindowsIdentity;  
  
// This outer try block is used to protect from   
// exception filter attacks which would prevent  
// the inner finally block from executing and   
// resetting the impersonation.  
try  
{  
   try  
   {  
      impersonatedUser = clientId.Impersonate();  
      if (impersonatedUser != null)  
         return GetFileDetails(directoryPath);  
         else return null;  
   }  
   finally  
   {  
      if (impersonatedUser != null)  
         impersonatedUser.Undo();  
   }  
}  
catch  
{  
   throw;  
}  
```  
  
> [!NOTE]  
>  <span data-ttu-id="8ed19-114">如需模擬中行為變更的相關資訊，請參閱[SQL Server 2014 中資料庫引擎功能的重大變更](../../../database-engine/breaking-changes-to-database-engine-features-in-sql-server-2016.md)。</span><span class="sxs-lookup"><span data-stu-id="8ed19-114">For information about behavior changes in impersonation, see [Breaking Changes to Database Engine Features in SQL Server 2014](../../../database-engine/breaking-changes-to-database-engine-features-in-sql-server-2016.md).</span></span>  
  
 <span data-ttu-id="8ed19-115">此外，如果您已經取得 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows 識別執行個體，在預設情況下您無法將該執行個體傳播至另一部電腦；Windows 安全性基礎結構會根據預設來限制這項作業。</span><span class="sxs-lookup"><span data-stu-id="8ed19-115">Furthermore, if you obtained the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows identity instance, by default you cannot propagate that instance to another computer; Windows security infrastructure restricts that by default.</span></span> <span data-ttu-id="8ed19-116">但是，有一項機制稱為「委派」，它可啟用多部受信任電腦之間的 Windows 識別傳播。</span><span class="sxs-lookup"><span data-stu-id="8ed19-116">There is, however, a mechanism called "delegation" that enables propagation of Windows identities across multiple trusted computers.</span></span> <span data-ttu-id="8ed19-117">您可以在 TechNet 文章「[Kerberos 通訊協定轉換和限制委派](https://go.microsoft.com/fwlink/?LinkId=50419)」中深入瞭解委派。</span><span class="sxs-lookup"><span data-stu-id="8ed19-117">You can learn more about delegation in the TechNet article, "[Kerberos Protocol Transition and Constrained Delegation](https://go.microsoft.com/fwlink/?LinkId=50419)".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ed19-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8ed19-118">See Also</span></span>  
 [<span data-ttu-id="8ed19-119">SqlContext 物件</span><span class="sxs-lookup"><span data-stu-id="8ed19-119">SqlContext Object</span></span>](../../clr-integration-data-access-in-process-ado-net/sqlcontext-object.md)  
  
  
