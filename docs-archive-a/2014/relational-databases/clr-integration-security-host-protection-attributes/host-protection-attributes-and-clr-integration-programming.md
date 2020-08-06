---
title: 主機保護屬性和 CLR 整合程式設計 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- host protection attributes [CLR integration]
- HostProtectionAttribute [CLR integration]
- common language runtime [SQL Server], host protection attributes
- disallowed types and members [CLR integration]
- common language runtime [SQL Server], disallowed types and members
- HPAs [CLR integration]
ms.assetid: 268078df-63ca-4c03-a8e7-7108bcea9697
author: rothja
ms.author: jroth
ms.openlocfilehash: 16ca1e4734e66b0eca85523764739e8f8b32634a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704197"
---
# <a name="host-protection-attributes-and-clr-integration-programming"></a><span data-ttu-id="1947d-102">主機保護屬性和 CLR 整合程式設計</span><span class="sxs-lookup"><span data-stu-id="1947d-102">Host Protection Attributes and CLR Integration Programming</span></span>
  <span data-ttu-id="1947d-103">從 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 開始，Common Language Runtime (CLR) 提供了一個機制來使用 CLR (如 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]) 主機可能需要的某些屬性，為屬於 .NET Framework 之一部分的 Managed 應用程式開發介面 (API) 加註。</span><span class="sxs-lookup"><span data-stu-id="1947d-103">The common language runtime (CLR) provides a mechanism to annotate managed application programming interfaces (APIs) that are part of the .NET Framework with certain attributes that may be of interest to a host of the CLR, such as [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], beginning with [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].</span></span> <span data-ttu-id="1947d-104">這類主機保護屬性 (HPA) 的範例包括：</span><span class="sxs-lookup"><span data-stu-id="1947d-104">Examples of such host protection attributes (HPAs) include:</span></span>  
  
-   <span data-ttu-id="1947d-105">`SharedState`，它可指出 API 是否會公開用來建立或管理共用狀態 (如靜態類別欄位) 的功能。</span><span class="sxs-lookup"><span data-stu-id="1947d-105">`SharedState`, which indicates whether the API exposes the ability to create or manage shared state (for example, static class fields).</span></span>  
  
-   <span data-ttu-id="1947d-106">`Synchronization`，它可指出 API 是否會公開用來執行執行緒之間之同步處理的功能。</span><span class="sxs-lookup"><span data-stu-id="1947d-106">`Synchronization`, which indicates whether the API exposes the ability to perform synchronization between threads.</span></span>  
  
-   <span data-ttu-id="1947d-107">`ExternalProcessMgmt`，它可指出 API 是否會公開用來控制主機處理序的方法。</span><span class="sxs-lookup"><span data-stu-id="1947d-107">`ExternalProcessMgmt`, which indicates whether the API exposes a way to control the host process.</span></span>  
  
 <span data-ttu-id="1947d-108">當提供了這些屬性時，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 會指定 HPA 的清單，這些 HPA 是透過程式碼存取安全性 (CAS) 的主控環境內所不允許的。</span><span class="sxs-lookup"><span data-stu-id="1947d-108">Given these attributes, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] specifies a list of HPAs that are disallowed in the hosted environment through code access security (CAS).</span></span> <span data-ttu-id="1947d-109">CAS 需求是由以下三個 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 權限集合的其中一個所指定：`SAFE`、`EXTERNAL_ACCESS` 或 `UNSAFE`。</span><span class="sxs-lookup"><span data-stu-id="1947d-109">The CAS requirements are specified by one of three [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] permission sets: `SAFE`, `EXTERNAL_ACCESS`, or `UNSAFE`.</span></span> <span data-ttu-id="1947d-110">當使用 `CREATE ASSEMBLY` 陳述式在伺服器上註冊此組件時，便會指定這三個安全性層級的其中一個。</span><span class="sxs-lookup"><span data-stu-id="1947d-110">One of these three security levels is specified when the assembly is registered on the server, using the `CREATE ASSEMBLY` statement.</span></span> <span data-ttu-id="1947d-111">在 `SAFE` 或 `EXTERNAL_ACCESS` 權限集合內執行的程式碼必須避免某些已套用 `System.Security.Permissions.HostProtectionAttribute` 屬性的類型或成員。</span><span class="sxs-lookup"><span data-stu-id="1947d-111">Code executing within the `SAFE` or `EXTERNAL_ACCESS` permission sets must avoid certain types or members that have the `System.Security.Permissions.HostProtectionAttribute` attribute applied.</span></span> <span data-ttu-id="1947d-112">如需詳細資訊，請參閱[建立元件](../clr-integration/assemblies/creating-an-assembly.md)和[CLR 整合程式設計模型限制](../clr-integration/database-objects/clr-integration-programming-model-restrictions.md)。</span><span class="sxs-lookup"><span data-stu-id="1947d-112">For more information, see [Creating an Assembly](../clr-integration/assemblies/creating-an-assembly.md) and [CLR Integration Programming Model Restrictions](../clr-integration/database-objects/clr-integration-programming-model-restrictions.md).</span></span>  
  
 <span data-ttu-id="1947d-113">`HostProtectionAttribute` 並不是用來提升可靠性的一種安全性權限，因為它會識別主機可能不允許的特定程式碼建構 (類型或方法)。</span><span class="sxs-lookup"><span data-stu-id="1947d-113">The `HostProtectionAttribute` is not a security permission as much as a way to improve reliability, in that it identifies specific code constructs, either types or methods, that the host may disallow.</span></span> <span data-ttu-id="1947d-114">使用 `HostProtectionAttribute` 會強制使用有助於保護主機之穩定性的程式設計模型。</span><span class="sxs-lookup"><span data-stu-id="1947d-114">The use of the `HostProtectionAttribute` enforces a programming model that helps protect the stability of the host.</span></span>  
  
## <a name="host-protection-attributes"></a><span data-ttu-id="1947d-115">主機保護屬性</span><span class="sxs-lookup"><span data-stu-id="1947d-115">Host Protection Attributes</span></span>  
 <span data-ttu-id="1947d-116">HPA 可識別不適合主機程式設計模型以及代表下列可靠性威脅等級提高的類型或成員：</span><span class="sxs-lookup"><span data-stu-id="1947d-116">HPAs identify types or members that do not fit the host programming model and represent the following increasing levels of reliability threat:</span></span>  
  
-   <span data-ttu-id="1947d-117">否則為良性。</span><span class="sxs-lookup"><span data-stu-id="1947d-117">Are otherwise benign.</span></span>  
  
-   <span data-ttu-id="1947d-118">可能會導致受伺服器管理的使用者程式碼不穩定。</span><span class="sxs-lookup"><span data-stu-id="1947d-118">Could lead to destabilization of server-managed user code.</span></span>  
  
-   <span data-ttu-id="1947d-119">可能會導致伺服器處理序本身的不穩定。</span><span class="sxs-lookup"><span data-stu-id="1947d-119">Could lead to destabilization of the server process itself.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="1947d-120">不允許使用具有的類型或成員，其指定的列舉值為、、、、、、、 `HostProtectionAttribute` `System.Security.Permissions.HostProtectionResource` `ExternalProcessMgmt` `ExternalThreading` `MayLeakOnAbort` `SecurityInfrastructure` `SelfAffectingProcessMgmnt` `SelfAffectingThreading` `SharedState` `Synchronization` 或 `UI` 。</span><span class="sxs-lookup"><span data-stu-id="1947d-120">disallows the use of a type or member that has a `HostProtectionAttribute` that specifies a `System.Security.Permissions.HostProtectionResource` enumeration with a value of `ExternalProcessMgmt`, `ExternalThreading`, `MayLeakOnAbort`, `SecurityInfrastructure`, `SelfAffectingProcessMgmnt`, `SelfAffectingThreading`, `SharedState`, `Synchronization`, or `UI`.</span></span> <span data-ttu-id="1947d-121">這會讓組件無法呼叫可啟用共用狀態、執行同步處理、在終止時可能造成資源流失，或是會影響 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 處理序完整性的成員。</span><span class="sxs-lookup"><span data-stu-id="1947d-121">This prevents the assemblies from calling members that enable sharing state, perform synchronization, might cause a resource leak on termination, or affect the integrity of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] process.</span></span>  
  
### <a name="disallowed-types-and-members"></a><span data-ttu-id="1947d-122">不允許的類型和成員</span><span class="sxs-lookup"><span data-stu-id="1947d-122">Disallowed Types and Members</span></span>  
 <span data-ttu-id="1947d-123">下列主題將識別一些類型和成員，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 不允許使用它們的 `HostProtectionResource` 值。</span><span class="sxs-lookup"><span data-stu-id="1947d-123">The following topics identify types and members whose `HostProtectionResource` values are disallowed by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1947d-124">這些主題中的清單是根據支援的組件產生的。</span><span class="sxs-lookup"><span data-stu-id="1947d-124">The lists in these topics were generated from the supported assemblies.</span></span>  <span data-ttu-id="1947d-125">如需詳細資訊，請參閱[支援的 .NET Framework 程式庫](../clr-integration/database-objects/supported-net-framework-libraries.md)。</span><span class="sxs-lookup"><span data-stu-id="1947d-125">For more information, see [Supported .NET Framework Libraries](../clr-integration/database-objects/supported-net-framework-libraries.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1947d-126">本節內容</span><span class="sxs-lookup"><span data-stu-id="1947d-126">In This Section</span></span>  
 [<span data-ttu-id="1947d-127">Microsoft.VisualBasic.dll 中不允許的型別和成員</span><span class="sxs-lookup"><span data-stu-id="1947d-127">Disallowed Types and Members in Microsoft.VisualBasic.dll</span></span>](disallowed-types-and-members-in-microsoft-visualbasic-dll.md)  
 <span data-ttu-id="1947d-128">列出 Microsoft.VisualBasic.dll 中的一些類型和成員，這些類型和成員的 HPA 值是不被允許的。</span><span class="sxs-lookup"><span data-stu-id="1947d-128">Lists the types and members in Microsoft.VisualBasic.dll whose HPA values are disallowed.</span></span>  
  
 [<span data-ttu-id="1947d-129">在 mscorlib.dll 中不允許的類型和成員</span><span class="sxs-lookup"><span data-stu-id="1947d-129">Disallowed Types and Members in mscorlib.dll</span></span>](disallowed-types-and-members-in-mscorlib-dll.md)  
 <span data-ttu-id="1947d-130">列出 mscorlib.dll 中的一些類型和成員，這些類型和成員的 HPA 值是不被允許的。</span><span class="sxs-lookup"><span data-stu-id="1947d-130">Lists the types and members in mscorlib.dll whose HPA values are disallowed.</span></span>  
  
 [<span data-ttu-id="1947d-131">在 System.dll 中不允許的類型和成員</span><span class="sxs-lookup"><span data-stu-id="1947d-131">Disallowed Types and Members in System.dll</span></span>](disallowed-types-and-members-in-system-dll.md)  
 <span data-ttu-id="1947d-132">列出 System.dll 中的一些類型和成員，這些類型和成員的 HPA 值是不被允許的。</span><span class="sxs-lookup"><span data-stu-id="1947d-132">Lists the types and members in System.dll whose HPA values are disallowed.</span></span>  
  
 [<span data-ttu-id="1947d-133">在 System.Data.dll 中不允許的類型和成員</span><span class="sxs-lookup"><span data-stu-id="1947d-133">Disallowed Types and Members in System.Data.dll</span></span>](disallowed-types-and-members-in-system-data-dll.md)  
 <span data-ttu-id="1947d-134">列出 System.Data.dll 中的一些類型和成員，這些類型和成員的 HPA 值是不被允許的。</span><span class="sxs-lookup"><span data-stu-id="1947d-134">Lists the types and members in System.Data.dll whose HPA values are disallowed.</span></span>  
  
 [<span data-ttu-id="1947d-135">System.Core.dll 中不允許的類型和成員</span><span class="sxs-lookup"><span data-stu-id="1947d-135">Disallowed Types and Members in System.Core.dll</span></span>](disallowed-types-and-members-in-system-core-dll.md)  
 <span data-ttu-id="1947d-136">列出 System.Core.dll 中的一些類型和成員，這些類型和成員的 HPA 值是不被允許的。</span><span class="sxs-lookup"><span data-stu-id="1947d-136">Lists the types and members in System.Core.dll whose HPA values are disallowed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1947d-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1947d-137">See Also</span></span>  
 <span data-ttu-id="1947d-138">[CLR 整合代碼啟用安全性](../clr-integration/security/clr-integration-code-access-security.md) </span><span class="sxs-lookup"><span data-stu-id="1947d-138">[CLR Integration Code Access Security](../clr-integration/security/clr-integration-code-access-security.md) </span></span>  
 <span data-ttu-id="1947d-139">[CLR 整合程式設計模型限制](../clr-integration/database-objects/clr-integration-programming-model-restrictions.md) </span><span class="sxs-lookup"><span data-stu-id="1947d-139">[CLR Integration Programming Model Restrictions](../clr-integration/database-objects/clr-integration-programming-model-restrictions.md) </span></span>  
 [<span data-ttu-id="1947d-140">建立組件</span><span class="sxs-lookup"><span data-stu-id="1947d-140">Creating an Assembly</span></span>](../clr-integration/assemblies/creating-an-assembly.md)  
  
  
