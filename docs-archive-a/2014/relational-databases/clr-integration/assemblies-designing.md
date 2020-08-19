---
title: 設計元件 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- designing assemblies [SQL Server]
- assemblies [CLR integration], designing
ms.assetid: 9c07f706-6508-41aa-a4d7-56ce354f9061
author: rothja
ms.author: jroth
ms.openlocfilehash: 785ab80a529140a52ec18ef96ccaaeafd03698cd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704190"
---
# <a name="designing-assemblies"></a><span data-ttu-id="987ee-102">設計組件</span><span class="sxs-lookup"><span data-stu-id="987ee-102">Designing Assemblies</span></span>
  <span data-ttu-id="987ee-103">此主題描述以下在設計組件時應該考慮的因數：</span><span class="sxs-lookup"><span data-stu-id="987ee-103">This topic describes the following factors you should consider when you design assemblies:</span></span>  
  
-   <span data-ttu-id="987ee-104">封裝組件</span><span class="sxs-lookup"><span data-stu-id="987ee-104">Packaging assemblies</span></span>  
  
-   <span data-ttu-id="987ee-105">管理組件安全性</span><span class="sxs-lookup"><span data-stu-id="987ee-105">Managing assembly security</span></span>  
  
-   <span data-ttu-id="987ee-106">組件的限制</span><span class="sxs-lookup"><span data-stu-id="987ee-106">Restrictions on assemblies</span></span>  
  
## <a name="packaging-assemblies"></a><span data-ttu-id="987ee-107">封裝組件</span><span class="sxs-lookup"><span data-stu-id="987ee-107">Packaging Assemblies</span></span>  
 <span data-ttu-id="987ee-108">組件在其類別及方法中，可以包含多個 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 常式或類型的功能。</span><span class="sxs-lookup"><span data-stu-id="987ee-108">An assembly can contain functionality for more than one [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] routine or type in its classes and methods.</span></span> <span data-ttu-id="987ee-109">大部分的情況下，封裝會在相同組件內執行相關函數的常式功能很有用處，尤其如果這些常式共用會彼此呼叫的類別。</span><span class="sxs-lookup"><span data-stu-id="987ee-109">Most of the time, it makes sense to package the functionality of routines that perform related functions within the same assembly, especially if these routines share classes whose methods call one another.</span></span> <span data-ttu-id="987ee-110">例如，可為 Common Language Runtime (CLR) 觸發程序及 CLR 預存程序執行資料項目管理工作的類別，就可以封裝在相同的組件中。</span><span class="sxs-lookup"><span data-stu-id="987ee-110">For example, classes that perform data entry management tasks for common language runtime (CLR) triggers and CLR stored procedures can be packaged in the same assembly.</span></span> <span data-ttu-id="987ee-111">這是因為這些類別的方法跟較不相關的那些工作相比，比較可能會彼此呼叫。</span><span class="sxs-lookup"><span data-stu-id="987ee-111">This is because the methods for these classes are more likely to call each other than those of less related tasks.</span></span>  
  
 <span data-ttu-id="987ee-112">將程式碼封裝到組件時，應該要考慮以下事項：</span><span class="sxs-lookup"><span data-stu-id="987ee-112">When you are packaging code into assembly, you should consider the following:</span></span>  
  
-   <span data-ttu-id="987ee-113">CLR 使用者定義型別及相依於 CLR 使用者自訂函數的索引，會導致保留的資料放在相依於組件的資料庫中。</span><span class="sxs-lookup"><span data-stu-id="987ee-113">CLR user-defined types and indexes that depend on CLR user-defined functions can cause persisted data to be in the database that depends on the assembly.</span></span> <span data-ttu-id="987ee-114">資料庫中有相依於組件的保存資料時，修改組件的程式碼通常更為複雜。</span><span class="sxs-lookup"><span data-stu-id="987ee-114">Modifying the code of an assembly is frequently more complex when there is persisted data that depends on the assembly in the database.</span></span> <span data-ttu-id="987ee-115">因此，一般最好將保存資料相依性所依賴的程式碼 (例如，使用者定義型別及使用使用者自訂函數的索引)，跟沒有這類保存資料相依性的程式碼分開。</span><span class="sxs-lookup"><span data-stu-id="987ee-115">Therefore, it is generally better to separate code on which persisted data dependencies rely (such as user-defined types and indexes using user-defined functions) from code that does not have such persisted data dependencies.</span></span> <span data-ttu-id="987ee-116">如需詳細資訊，請參閱 [執行元件](assemblies-implementing.md) 和 [ALTER ASSEMBLY &#40;transact-sql&#41;](/sql/t-sql/statements/alter-assembly-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="987ee-116">For more information, see [Implementing Assemblies](assemblies-implementing.md) and [ALTER ASSEMBLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-assembly-transact-sql).</span></span>  
  
-   <span data-ttu-id="987ee-117">如果有段 Managed 程式碼需要更高的權限，最好將那個程式碼跟不需要較高權限的程式碼分隔，放在個別的組件。</span><span class="sxs-lookup"><span data-stu-id="987ee-117">If a piece of managed code requires higher permission, it is better to separate that code into a separate assembly from code that does not require higher permission.</span></span>  
  
## <a name="managing-assembly-security"></a><span data-ttu-id="987ee-118">管理組件安全性</span><span class="sxs-lookup"><span data-stu-id="987ee-118">Managing Assembly Security</span></span>  
 <span data-ttu-id="987ee-119">您可以控制在執行 Managed 程式碼時，可存取受到「.NET 程式碼存取安全性」保護之資源的組件多寡。</span><span class="sxs-lookup"><span data-stu-id="987ee-119">You can control how much an assembly can access resources protected by .NET Code Access Security when it runs managed code.</span></span> <span data-ttu-id="987ee-120">建立或修改組件時，指定三種權限集之一，就可以完成此動作：SAFE、EXTERNAL_ACCESS 或 UNSAFE。</span><span class="sxs-lookup"><span data-stu-id="987ee-120">You do this by specifying one of three permission sets when you create or modify an assembly: SAFE, EXTERNAL_ACCESS, or UNSAFE.</span></span>  
  
### <a name="safe"></a><span data-ttu-id="987ee-121">SAFE</span><span class="sxs-lookup"><span data-stu-id="987ee-121">SAFE</span></span>  
 <span data-ttu-id="987ee-122">SAFE 是預設的權限集，而且其限制最為嚴格。</span><span class="sxs-lookup"><span data-stu-id="987ee-122">SAFE is the default permission set and it is the most restrictive.</span></span> <span data-ttu-id="987ee-123">由具有 SAFE 權限的組件執行的程式碼，無法存取外部系統資源，例如，檔案、網路、環境變數或登錄。</span><span class="sxs-lookup"><span data-stu-id="987ee-123">Code run by an assembly with SAFE permissions cannot access external system resources such as files, the network, environment variables, or the registry.</span></span> <span data-ttu-id="987ee-124">SAFE 程式碼可以存取本機 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 資料庫的資料，或是執行不會存取本機資料庫以外資源的計算及商務邏輯。</span><span class="sxs-lookup"><span data-stu-id="987ee-124">SAFE code can access data from the local [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] databases or perform computations and business logic that do not involve accessing resources outside the local databases.</span></span>  
  
 <span data-ttu-id="987ee-125">執行計算及資料管理工作的大部分組件，不需要存取 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 外部的資源。</span><span class="sxs-lookup"><span data-stu-id="987ee-125">Most assemblies perform computation and data management tasks without having to access resources outside [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="987ee-126">因此，建議您將 SAFE 作為組件權限集。</span><span class="sxs-lookup"><span data-stu-id="987ee-126">Therefore, we recommend SAFE as the assembly permission set.</span></span>  
  
### <a name="external_access"></a><span data-ttu-id="987ee-127">EXTERNAL_ACCESS</span><span class="sxs-lookup"><span data-stu-id="987ee-127">EXTERNAL_ACCESS</span></span>  
 <span data-ttu-id="987ee-128">EXTERNAL_ACCESS 可讓組件存取特定的外部系統資源，例如，檔案、網路、Web 服務、環境變數及登錄。</span><span class="sxs-lookup"><span data-stu-id="987ee-128">EXTERNAL_ACCESS allows for assemblies to access certain external system resources such as files, networks, Web services, environmental variables, and the registry.</span></span> <span data-ttu-id="987ee-129">只有當 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 以 EXTERNAL ACCESS 權限登入時，才能建立 EXTERNAL_ACCESS 組件。</span><span class="sxs-lookup"><span data-stu-id="987ee-129">Only [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] logins with EXTERNAL ACCESS permissions can create EXTERNAL_ACCESS assemblies.</span></span>  
  
 <span data-ttu-id="987ee-130">SAFE 及 EXTERNAL_ACCESS 組件只能包含可驗證類型安全 (verifiably type-safe) 的程式碼。</span><span class="sxs-lookup"><span data-stu-id="987ee-130">SAFE and EXTERNAL_ACCESS assemblies can contain only code that is verifiably type-safe.</span></span> <span data-ttu-id="987ee-131">這代表如果這些組件要存取類別，只能透過定義完善、對該類型定義有效的進入點。</span><span class="sxs-lookup"><span data-stu-id="987ee-131">This means that these assemblies can only access classes through well-defined entry points that are valid for the type definition.</span></span> <span data-ttu-id="987ee-132">因此，他們不能任意存取不屬於該程式碼的記憶體緩衝區。</span><span class="sxs-lookup"><span data-stu-id="987ee-132">Therefore, they cannot arbitrarily access memory buffers not owned by the code.</span></span> <span data-ttu-id="987ee-133">此外，它們無法執行可能有損 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 處理序強固性的作業。</span><span class="sxs-lookup"><span data-stu-id="987ee-133">Additionally, they cannot perform operations that might have an adverse effect on the robustness of the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] process.</span></span>  
  
### <a name="unsafe"></a><span data-ttu-id="987ee-134">UNSAFE</span><span class="sxs-lookup"><span data-stu-id="987ee-134">UNSAFE</span></span>  
 <span data-ttu-id="987ee-135">UNSAFE 可讓組件無限制存取 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 內外部的資源。</span><span class="sxs-lookup"><span data-stu-id="987ee-135">UNSAFE gives assemblies unrestricted access to resources, both within and outside [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="987ee-136">由 UNSAFE 組件內執行的程式碼可以呼叫 Unmanaged 程式碼。</span><span class="sxs-lookup"><span data-stu-id="987ee-136">Code that is running from within an UNSAFE assembly can call unmanaged code.</span></span>  
  
 <span data-ttu-id="987ee-137">此外，指定 UNSAFE 可讓組件中的程式碼，執行 CLR 檢查器視為類型安全的作業。</span><span class="sxs-lookup"><span data-stu-id="987ee-137">Also, specifying UNSAFE allows for the code in the assembly to perform operations that are considered type-unsafe by the CLR verifier.</span></span> <span data-ttu-id="987ee-138">這些作業可能會以未受控制的方式，存取 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 處理序空間的記憶體緩衝區。</span><span class="sxs-lookup"><span data-stu-id="987ee-138">These operations can potentially access memory buffers in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] process space in an uncontrolled manner.</span></span> <span data-ttu-id="987ee-139">UNSAFE 組件也可能會破壞 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 或 Common Language Runtime 的安全性系統。</span><span class="sxs-lookup"><span data-stu-id="987ee-139">UNSAFE assemblies can also potentially subvert the security system of either [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] or the common language runtime.</span></span> <span data-ttu-id="987ee-140">UNSAFE 權限應只能由經驗豐富的開發人員或系統管理員，授與高度信任的組件。</span><span class="sxs-lookup"><span data-stu-id="987ee-140">UNSAFE permissions should be granted only to highly trusted assemblies by experienced developers or administrators.</span></span> <span data-ttu-id="987ee-141">只有 **系統管理員（sysadmin** ）固定伺服器角色的成員，才能夠建立 UNSAFE 元件。</span><span class="sxs-lookup"><span data-stu-id="987ee-141">Only members of the **sysadmin** fixed server role can create UNSAFE assemblies.</span></span>  
  
## <a name="restrictions-on-assemblies"></a><span data-ttu-id="987ee-142">組件的限制</span><span class="sxs-lookup"><span data-stu-id="987ee-142">Restrictions on Assemblies</span></span>  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="987ee-143">對組件中的 Managed 程式碼有特定限制，以確保能以可靠且可擴充的方式執行程式碼。</span><span class="sxs-lookup"><span data-stu-id="987ee-143">puts certain restrictions on managed code in assemblies to make sure that they can run in a reliable and scalable manner.</span></span> <span data-ttu-id="987ee-144">這代表不會允許在 SAFE 及 EXTERNAL_ACCESS 組件中，執行會危害伺服器強固性的特定作業。</span><span class="sxs-lookup"><span data-stu-id="987ee-144">This means that certain operations that can compromise the robustness of the server are not permitted in SAFE and EXTERNAL_ACCESS assemblies.</span></span>  
  
### <a name="disallowed-custom-attributes"></a><span data-ttu-id="987ee-145">不允許的自訂屬性</span><span class="sxs-lookup"><span data-stu-id="987ee-145">Disallowed Custom Attributes</span></span>  
 <span data-ttu-id="987ee-146">不能以下列自訂屬性註解組件：</span><span class="sxs-lookup"><span data-stu-id="987ee-146">Assemblies cannot be annotated with the following custom attributes:</span></span>  
  
```  
System.ContextStaticAttribute  
System.MTAThreadAttribute  
System.Runtime.CompilerServices.MethodImplAttribute  
System.Runtime.CompilerServices.CompilationRelaxationsAttribute  
System.Runtime.Remoting.Contexts.ContextAttribute  
System.Runtime.Remoting.Contexts.SynchronizationAttribute  
System.Runtime.InteropServices.DllImportAttribute   
System.Security.Permissions.CodeAccessSecurityAttribute  
System.STAThreadAttribute  
System.ThreadStaticAttribute  
```  
  
 <span data-ttu-id="987ee-147">此外，不能以下列自訂屬性註解 SAFE 和 EXTERNAL_ACCESS 組件：</span><span class="sxs-lookup"><span data-stu-id="987ee-147">Additionally, SAFE and EXTERNAL_ACCESS assemblies cannot be annotated with the following custom attributes:</span></span>  
  
```  
System.Security.SuppressUnmanagedCodeSecurityAttribute  
System.Security.UnverifiableCodeAttribute  
```  
  
### <a name="disallowed-net-framework-apis"></a><span data-ttu-id="987ee-148">不允許的 .NET Framework API</span><span class="sxs-lookup"><span data-stu-id="987ee-148">Disallowed .NET Framework APIs</span></span>  
 <span data-ttu-id="987ee-149">[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 使用其中一個不允許的**HostProtectionAttributes**標注的任何 API 都無法從 SAFE 和 EXTERNAL_ACCESS 元件中呼叫。</span><span class="sxs-lookup"><span data-stu-id="987ee-149">Any [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] API that is annotated with one of the disallowed **HostProtectionAttributes** cannot be called from SAFE and EXTERNAL_ACCESS assemblies.</span></span>  
  
```  
eSelfAffectingProcessMgmt  
eSelfAffectingThreading  
eSynchronization  
eSharedState   
eExternalProcessMgmt  
eExternalThreading  
eSecurityInfrastructure  
eMayLeakOnAbort  
eUI  
```  
  
### <a name="supported-net-framework-assemblies"></a><span data-ttu-id="987ee-150">支援的 .NET Framework 組件</span><span class="sxs-lookup"><span data-stu-id="987ee-150">Supported .NET Framework Assemblies</span></span>  
 <span data-ttu-id="987ee-151">您必須使用 CREATE ASSEMBLY，將自訂組件所參考的任何組件載入 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 中。</span><span class="sxs-lookup"><span data-stu-id="987ee-151">Any assembly that is referenced by your custom assembly must be loaded into [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] by using CREATE ASSEMBLY.</span></span> <span data-ttu-id="987ee-152">下列 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 組件已經載入 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]，因此不必使用 CREATE ASSEMBLY，就可以讓自訂組件參考這些組件。</span><span class="sxs-lookup"><span data-stu-id="987ee-152">The following [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] assemblies are already loaded into [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] and, therefore, can be referenced by custom assemblies without having to use CREATE ASSEMBLY.</span></span>  
  
```  
custommarshallers.dll  
Microsoft.visualbasic.dll  
Microsoft.visualc.dll  
mscorlib.dll  
system.data.dll  
System.Data.SqlXml.dll  
system.dll  
system.security.dll  
system.web.services.dll  
system.xml.dll  
System.Transactions  
System.Data.OracleClient  
System.Configuration  
```  
  
## <a name="see-also"></a><span data-ttu-id="987ee-153">另請參閱</span><span class="sxs-lookup"><span data-stu-id="987ee-153">See Also</span></span>  
 <span data-ttu-id="987ee-154">[元件 &#40;資料庫引擎&#41;](../../relational-databases/clr-integration/assemblies-database-engine.md) </span><span class="sxs-lookup"><span data-stu-id="987ee-154">[Assemblies &#40;Database Engine&#41;](../../relational-databases/clr-integration/assemblies-database-engine.md) </span></span>  
 [<span data-ttu-id="987ee-155">CLR 整合安全性</span><span class="sxs-lookup"><span data-stu-id="987ee-155">CLR Integration Security</span></span>](security/clr-integration-security.md)  
  
  
