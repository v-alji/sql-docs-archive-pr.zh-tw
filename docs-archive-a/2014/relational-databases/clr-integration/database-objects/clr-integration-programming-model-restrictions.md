---
title: CLR 整合程式設計模型限制 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- common language runtime [SQL Server], programming model restrictions
- assemblies [CLR integration], CREATE ASSEMBLY checks
- programming model restrictions [CLR integration]
- assemblies [CLR integration], runtime checks
ms.assetid: 2446afc2-9d21-42d3-9847-7733d3074de9
author: rothja
ms.author: jroth
ms.openlocfilehash: 01a32e1460ad9c49061b39b1bdc419c7cd2f1342
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584579"
---
# <a name="clr-integration-programming-model-restrictions"></a><span data-ttu-id="215c0-102">CLR 整合程式設計模型限制</span><span class="sxs-lookup"><span data-stu-id="215c0-102">CLR Integration Programming Model Restrictions</span></span>
  <span data-ttu-id="215c0-103">當您建立 managed 預存程式或其他 managed 資料庫物件時，會執行特定的程式碼檢查， [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 其會在第一次於資料庫中註冊、使用 `CREATE ASSEMBLY` 語句，以及在執行時間時，對 managed 程式碼元件執行檢查。</span><span class="sxs-lookup"><span data-stu-id="215c0-103">When you are building a managed stored procedure or other managed database object, there are certain code checks performed by [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] performs checks on the managed code assembly when it is first registered in the database, using the `CREATE ASSEMBLY` statement, and also at runtime.</span></span> <span data-ttu-id="215c0-104">也會在執行階段檢查 Managed 程式碼，因為在組件中，可能會有執行階段絕對無法到達的程式碼路徑。</span><span class="sxs-lookup"><span data-stu-id="215c0-104">The managed code is also checked at runtime because in an assembly there may be code paths that may never actually be reached at runtime.</span></span>  <span data-ttu-id="215c0-105">特別是這樣提供了註冊協力廠商組件的彈性，如此一來，當組件中的不安全程式碼設計為在用戶端環境中執行，但是絕對不會在主控的 CLR 內執行時，就不會封鎖該組件。</span><span class="sxs-lookup"><span data-stu-id="215c0-105">This provides flexibility for registering third party assemblies, especially, so that an assembly wouldn't be blocked where there is 'unsafe' code designed to run in a client environment but would never be executed in the hosted CLR.</span></span> <span data-ttu-id="215c0-106">Managed 程式碼必須符合的需求取決於元件是否註冊為 `SAFE` 、 `EXTERNAL_ACCESS` 、或，是否為 `UNSAFE` `SAFE` 最嚴格的，並且如下所示。</span><span class="sxs-lookup"><span data-stu-id="215c0-106">The requirements that the managed code must meet depend on whether the assembly is registered as `SAFE`, `EXTERNAL_ACCESS`, or `UNSAFE`, `SAFE` being the strictest, and are listed below.</span></span>  
  
 <span data-ttu-id="215c0-107">除了對 Managed 程式碼組件所加諸的限制以外，也有授與的程式碼安全性權限。</span><span class="sxs-lookup"><span data-stu-id="215c0-107">In addition to restrictions being placed on the managed code assemblies, there are also code security permissions that are granted.</span></span> <span data-ttu-id="215c0-108">Common Language Runtime (CLR) 支援稱為 Managed 程式碼之程式碼存取安全性 (CAS) 的安全性模型。</span><span class="sxs-lookup"><span data-stu-id="215c0-108">The common language runtime (CLR) supports a security model called code access security (CAS) for managed code.</span></span> <span data-ttu-id="215c0-109">在此模型中，將會根據程式碼的識別來授與權限給組件。</span><span class="sxs-lookup"><span data-stu-id="215c0-109">In this model, permissions are granted to assemblies based on the identity of the code.</span></span> <span data-ttu-id="215c0-110">`SAFE`、`EXTERNAL_ACCESS` 和 `UNSAFE` 組件有不同的 CAS 權限。</span><span class="sxs-lookup"><span data-stu-id="215c0-110">`SAFE`, `EXTERNAL_ACCESS`, and `UNSAFE` assemblies have different CAS permissions.</span></span> <span data-ttu-id="215c0-111">如需詳細資訊，請參閱[CLR 整合代碼啟用安全性](../security/clr-integration-code-access-security.md)。</span><span class="sxs-lookup"><span data-stu-id="215c0-111">For more information, see [CLR Integration Code Access Security](../security/clr-integration-code-access-security.md).</span></span>  
  
## <a name="create-assembly-checks"></a><span data-ttu-id="215c0-112">CREATE ASSEMBLY 檢查</span><span class="sxs-lookup"><span data-stu-id="215c0-112">CREATE ASSEMBLY Checks</span></span>  
 <span data-ttu-id="215c0-113">當執行 `CREATE ASSEMBLY` 陳述式時，將會針對每一個安全性層級執行下列檢查。</span><span class="sxs-lookup"><span data-stu-id="215c0-113">When the `CREATE ASSEMBLY` statement is run, the following checks are performed for each security level.</span></span>  <span data-ttu-id="215c0-114">如果任何檢查失敗，`CREATE ASSEMBLY` 將會失敗，並傳回錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="215c0-114">If any check fails, `CREATE ASSEMBLY` will fail with an error message.</span></span>  
  
### <a name="global-any-security-level"></a><span data-ttu-id="215c0-115">全域 (任何安全性層級)</span><span class="sxs-lookup"><span data-stu-id="215c0-115">Global (any security level)</span></span>  
 <span data-ttu-id="215c0-116">所有參考的組件都必須符合下列其中一個或多個準則：</span><span class="sxs-lookup"><span data-stu-id="215c0-116">All referenced assemblies must meet one or more of the following criteria:</span></span>  
  
-   <span data-ttu-id="215c0-117">此組件已經在資料庫中註冊。</span><span class="sxs-lookup"><span data-stu-id="215c0-117">The assembly is already registered in the database.</span></span>  
  
-   <span data-ttu-id="215c0-118">此組件是其中一個支援的組件。</span><span class="sxs-lookup"><span data-stu-id="215c0-118">The assembly is one of the supported assemblies.</span></span> <span data-ttu-id="215c0-119">如需詳細資訊，請參閱[支援的 .NET Framework 程式庫](supported-net-framework-libraries.md)。</span><span class="sxs-lookup"><span data-stu-id="215c0-119">For more information, see [Supported .NET Framework Libraries](supported-net-framework-libraries.md).</span></span>  
  
-   <span data-ttu-id="215c0-120">您正在使用 `CREATE ASSEMBLY FROM` \* \<location> ，\* 而且所有參考的元件及其相依性都可在中取得 *\<location>* 。</span><span class="sxs-lookup"><span data-stu-id="215c0-120">You are using `CREATE ASSEMBLY FROM`*\<location>,* and all the referenced assemblies and their dependencies are available in *\<location>*.</span></span>  
  
-   <span data-ttu-id="215c0-121">您使用的是 `CREATE ASSEMBLY FROM` \* \<bytes ...> ，\* 而且所有的參考都是透過以空格分隔的位元組來指定。</span><span class="sxs-lookup"><span data-stu-id="215c0-121">You are using `CREATE ASSEMBLY FROM`*\<bytes ...>,* and all the references are specified via space separated bytes.</span></span>  
  
### <a name="external_access"></a><span data-ttu-id="215c0-122">EXTERNAL_ACCESS</span><span class="sxs-lookup"><span data-stu-id="215c0-122">EXTERNAL_ACCESS</span></span>  
 <span data-ttu-id="215c0-123">所有 `EXTERNAL_ACCESS` 組件都必須符合下列準則：</span><span class="sxs-lookup"><span data-stu-id="215c0-123">All `EXTERNAL_ACCESS` assemblies must meet the following criteria:</span></span>  
  
-   <span data-ttu-id="215c0-124">靜態欄位無法用來儲存資訊。</span><span class="sxs-lookup"><span data-stu-id="215c0-124">Static fields are not used to store information.</span></span> <span data-ttu-id="215c0-125">允許唯讀靜態欄位。</span><span class="sxs-lookup"><span data-stu-id="215c0-125">Read-only static fields are allowed.</span></span>  
  
-   <span data-ttu-id="215c0-126">通過 PEVerify 測試。</span><span class="sxs-lookup"><span data-stu-id="215c0-126">PEVerify test is passed.</span></span> <span data-ttu-id="215c0-127">用來檢查 MSIL 程式碼及關聯的中繼資料確實符合類型安全需求的 PEVerify 工具 (peverify.exe) 隨附在 .NET Framework SDK 中。</span><span class="sxs-lookup"><span data-stu-id="215c0-127">The PEVerify tool (peverify.exe), which checks that the MSIL code and associated metadata meet type safety requirements, is provided with the .NET Framework SDK.</span></span>  
  
-   <span data-ttu-id="215c0-128">例如，將不會使用與 `SynchronizationAttribute` 類別的同步處理。</span><span class="sxs-lookup"><span data-stu-id="215c0-128">Synchronization, for example with the `SynchronizationAttribute` class, is not used.</span></span>  
  
-   <span data-ttu-id="215c0-129">不會使用 Finalizer 方法。</span><span class="sxs-lookup"><span data-stu-id="215c0-129">Finalizer methods are not used.</span></span>  
  
 <span data-ttu-id="215c0-130">`EXTERNAL_ACCESS` 組件中不允許下列自訂屬性：</span><span class="sxs-lookup"><span data-stu-id="215c0-130">The following custom attributes are disallowed in `EXTERNAL_ACCESS` assemblies:</span></span>  
  
-   <span data-ttu-id="215c0-131">System.ContextStaticAttribute</span><span class="sxs-lookup"><span data-stu-id="215c0-131">System.ContextStaticAttribute</span></span>  
  
-   <span data-ttu-id="215c0-132">System.MTAThreadAttribute</span><span class="sxs-lookup"><span data-stu-id="215c0-132">System.MTAThreadAttribute</span></span>  
  
-   <span data-ttu-id="215c0-133">System.Runtime.CompilerServices.MethodImplAttribute</span><span class="sxs-lookup"><span data-stu-id="215c0-133">System.Runtime.CompilerServices.MethodImplAttribute</span></span>  
  
-   <span data-ttu-id="215c0-134">System.Runtime.CompilerServices.CompilationRelaxationsAttribute</span><span class="sxs-lookup"><span data-stu-id="215c0-134">System.Runtime.CompilerServices.CompilationRelaxationsAttribute</span></span>  
  
-   <span data-ttu-id="215c0-135">System.Runtime.Remoting.Contexts.ContextAttribute</span><span class="sxs-lookup"><span data-stu-id="215c0-135">System.Runtime.Remoting.Contexts.ContextAttribute</span></span>  
  
-   <span data-ttu-id="215c0-136">System.Runtime.Remoting.Contexts.SynchronizationAttribute</span><span class="sxs-lookup"><span data-stu-id="215c0-136">System.Runtime.Remoting.Contexts.SynchronizationAttribute</span></span>  
  
-   <span data-ttu-id="215c0-137">System.Runtime.InteropServices.DllImportAttribute</span><span class="sxs-lookup"><span data-stu-id="215c0-137">System.Runtime.InteropServices.DllImportAttribute</span></span>  
  
-   <span data-ttu-id="215c0-138">System.Security.Permissions.CodeAccessSecurityAttribute</span><span class="sxs-lookup"><span data-stu-id="215c0-138">System.Security.Permissions.CodeAccessSecurityAttribute</span></span>  
  
-   <span data-ttu-id="215c0-139">System.Security.SuppressUnmanagedCodeSecurityAttribute</span><span class="sxs-lookup"><span data-stu-id="215c0-139">System.Security.SuppressUnmanagedCodeSecurityAttribute</span></span>  
  
-   <span data-ttu-id="215c0-140">System.Security.UnverifiableCodeAttribute</span><span class="sxs-lookup"><span data-stu-id="215c0-140">System.Security.UnverifiableCodeAttribute</span></span>  
  
-   <span data-ttu-id="215c0-141">System.STAThreadAttribute</span><span class="sxs-lookup"><span data-stu-id="215c0-141">System.STAThreadAttribute</span></span>  
  
-   <span data-ttu-id="215c0-142">System.ThreadStaticAttribute</span><span class="sxs-lookup"><span data-stu-id="215c0-142">System.ThreadStaticAttribute</span></span>  
  
### <a name="safe"></a><span data-ttu-id="215c0-143">SAFE</span><span class="sxs-lookup"><span data-stu-id="215c0-143">SAFE</span></span>  
  
-   <span data-ttu-id="215c0-144">所有 `EXTERNAL_ACCESS` 組件條件都會檢查。</span><span class="sxs-lookup"><span data-stu-id="215c0-144">All `EXTERNAL_ACCESS` assembly conditions are checked.</span></span>  
  
## <a name="runtime-checks"></a><span data-ttu-id="215c0-145">執行階段檢查</span><span class="sxs-lookup"><span data-stu-id="215c0-145">Runtime Checks</span></span>  
 <span data-ttu-id="215c0-146">執行階段會檢查程式碼組件是否有下列條件。</span><span class="sxs-lookup"><span data-stu-id="215c0-146">At runtime, the code assembly is checked for the following conditions.</span></span> <span data-ttu-id="215c0-147">如果找到這些條件的任何一個，將不允許執行 Managed 程式碼，而且將會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="215c0-147">If any of these conditions are found, the managed code will not be allowed to run and an exception will be thrown.</span></span>  
  
### <a name="unsafe"></a><span data-ttu-id="215c0-148">UNSAFE</span><span class="sxs-lookup"><span data-stu-id="215c0-148">UNSAFE</span></span>  
 <span data-ttu-id="215c0-149">不允許載入元件（不論是 `System.Reflection.Assembly.Load()` 從位元組陣列呼叫方法，或是透過使用 `Reflection.Emit` 命名空間隱含）。</span><span class="sxs-lookup"><span data-stu-id="215c0-149">Loading an assembly-either explicitly by calling the `System.Reflection.Assembly.Load()` method from a byte array, or implicitly through the use of `Reflection.Emit` namespace-is not permitted.</span></span>  
  
### <a name="external_access"></a><span data-ttu-id="215c0-150">EXTERNAL_ACCESS</span><span class="sxs-lookup"><span data-stu-id="215c0-150">EXTERNAL_ACCESS</span></span>  
 <span data-ttu-id="215c0-151">所有 `UNSAFE` 條件都會檢查。</span><span class="sxs-lookup"><span data-stu-id="215c0-151">All `UNSAFE` conditions are checked.</span></span>  
  
 <span data-ttu-id="215c0-152">不允許在支援的組件清單中使用下列主機保護屬性 (HPA) 值當做註解的所有類型和方法。</span><span class="sxs-lookup"><span data-stu-id="215c0-152">All types and methods annotated with the following host protection attribute (HPA) values in the supported list of assemblies are disallowed.</span></span>  
  
-   <span data-ttu-id="215c0-153">SelfAffectingProcessMgmt</span><span class="sxs-lookup"><span data-stu-id="215c0-153">SelfAffectingProcessMgmt</span></span>  
  
-   <span data-ttu-id="215c0-154">SelfAffectingThreading</span><span class="sxs-lookup"><span data-stu-id="215c0-154">SelfAffectingThreading</span></span>  
  
-   <span data-ttu-id="215c0-155">Synchronization</span><span class="sxs-lookup"><span data-stu-id="215c0-155">Synchronization</span></span>  
  
-   <span data-ttu-id="215c0-156">SharedState</span><span class="sxs-lookup"><span data-stu-id="215c0-156">SharedState</span></span>  
  
-   <span data-ttu-id="215c0-157">ExternalProcessMgmt</span><span class="sxs-lookup"><span data-stu-id="215c0-157">ExternalProcessMgmt</span></span>  
  
-   <span data-ttu-id="215c0-158">ExternalThreading</span><span class="sxs-lookup"><span data-stu-id="215c0-158">ExternalThreading</span></span>  
  
-   <span data-ttu-id="215c0-159">SecurityInfrastructure</span><span class="sxs-lookup"><span data-stu-id="215c0-159">SecurityInfrastructure</span></span>  
  
-   <span data-ttu-id="215c0-160">MayLeakOnAbort</span><span class="sxs-lookup"><span data-stu-id="215c0-160">MayLeakOnAbort</span></span>  
  
-   <span data-ttu-id="215c0-161">UI</span><span class="sxs-lookup"><span data-stu-id="215c0-161">UI</span></span>  
  
 <span data-ttu-id="215c0-162">如需 Hpa 的詳細資訊，以及支援的元件中不允許的類型和成員清單，請參閱[主控制項保護屬性和 CLR 整合程式設計](../../clr-integration-security-host-protection-attributes/host-protection-attributes-and-clr-integration-programming.md)。</span><span class="sxs-lookup"><span data-stu-id="215c0-162">For more information about HPAs and a list of disallowed types and members in the supported assemblies, see [Host Protection Attributes and CLR Integration Programming](../../clr-integration-security-host-protection-attributes/host-protection-attributes-and-clr-integration-programming.md).</span></span>  
  
### <a name="safe"></a><span data-ttu-id="215c0-163">SAFE</span><span class="sxs-lookup"><span data-stu-id="215c0-163">SAFE</span></span>  
 <span data-ttu-id="215c0-164">所有 `EXTERNAL_ACCESS` 條件都會檢查。</span><span class="sxs-lookup"><span data-stu-id="215c0-164">All `EXTERNAL_ACCESS` conditions are checked.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="215c0-165">另請參閱</span><span class="sxs-lookup"><span data-stu-id="215c0-165">See Also</span></span>  
 <span data-ttu-id="215c0-166">[支援的 .NET Framework 程式庫](supported-net-framework-libraries.md) </span><span class="sxs-lookup"><span data-stu-id="215c0-166">[Supported .NET Framework Libraries](supported-net-framework-libraries.md) </span></span>  
 <span data-ttu-id="215c0-167">[CLR 整合代碼啟用安全性](../security/clr-integration-code-access-security.md) </span><span class="sxs-lookup"><span data-stu-id="215c0-167">[CLR Integration Code Access Security](../security/clr-integration-code-access-security.md) </span></span>  
 <span data-ttu-id="215c0-168">[主機保護屬性和 CLR 整合程式設計](../../clr-integration-security-host-protection-attributes/host-protection-attributes-and-clr-integration-programming.md) </span><span class="sxs-lookup"><span data-stu-id="215c0-168">[Host Protection Attributes and CLR Integration Programming](../../clr-integration-security-host-protection-attributes/host-protection-attributes-and-clr-integration-programming.md) </span></span>  
 [<span data-ttu-id="215c0-169">建立組件</span><span class="sxs-lookup"><span data-stu-id="215c0-169">Creating an Assembly</span></span>](../assemblies/creating-an-assembly.md)  
  
  
