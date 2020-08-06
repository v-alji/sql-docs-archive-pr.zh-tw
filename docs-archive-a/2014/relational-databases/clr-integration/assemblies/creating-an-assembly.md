---
title: 建立元件 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- creating assemblies
- UNSAFE assemblies
- CREATE ASSEMBLY statement
- SAFE assemblies
- EXTERNAL_ACCESS assemblies
- assemblies [CLR integration], creating
ms.assetid: a2bc503d-b6b2-4963-8beb-c11c323f18e0
author: rothja
ms.author: jroth
ms.openlocfilehash: 9dea1f8fe57691f05274cac353a1064420309e06
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704166"
---
# <a name="creating-an-assembly"></a><span data-ttu-id="a91db-102">建立組件</span><span class="sxs-lookup"><span data-stu-id="a91db-102">Creating an Assembly</span></span>
  <span data-ttu-id="a91db-103">預存程序或觸發程序之類的 Managed 資料庫物件會經過編譯，然後再稱為組件的單元中進行部署。</span><span class="sxs-lookup"><span data-stu-id="a91db-103">Managed database objects, such as stored procedures or triggers, are compiled and then deployed in units called an assembly.</span></span> <span data-ttu-id="a91db-104">Managed DLL 元件必須先在中註冊， [!INCLUDE[msCoName](../../../includes/ssnoversion-md.md)] 然後才能使用元件提供的功能。</span><span class="sxs-lookup"><span data-stu-id="a91db-104">Managed DLL assemblies must be registered in [!INCLUDE[msCoName](../../../includes/ssnoversion-md.md)] before the functionality the assembly provides can be used.</span></span> <span data-ttu-id="a91db-105">若要在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 資料庫中註冊組件，請使用 CREATE ASSEMBLY 陳述式。</span><span class="sxs-lookup"><span data-stu-id="a91db-105">To register an assembly in a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] database, use the CREATE ASSEMBLY statement.</span></span> <span data-ttu-id="a91db-106">本主題討論如何在資料庫中使用 CREATE ASSEMBLY 陳述式註冊組件，以及如何指定組件的安全性設定。</span><span class="sxs-lookup"><span data-stu-id="a91db-106">This topic discusses how to register an assembly in a database using the CREATE ASSEMBLY statement, and how to specify the security settings for the assembly.</span></span>  
  
## <a name="the-create-assembly-statement"></a><span data-ttu-id="a91db-107">CREATE ASSEMBLY 陳述式</span><span class="sxs-lookup"><span data-stu-id="a91db-107">The CREATE ASSEMBLY Statement</span></span>  
 <span data-ttu-id="a91db-108">CREATE ASSEMBLY 陳述式用於在資料庫中註冊組件。</span><span class="sxs-lookup"><span data-stu-id="a91db-108">The CREATE ASSEMBLY statement is used to create an assembly in a database.</span></span> <span data-ttu-id="a91db-109">範例如下：</span><span class="sxs-lookup"><span data-stu-id="a91db-109">Here is an example:</span></span>  
  
```  
CREATE ASSEMBLY SQLCLRTest  
FROM 'C:\MyDBApp\SQLCLRTest.dll';  
```  
  
 <span data-ttu-id="a91db-110">FROM 子句會指定要建立之組件的路徑名稱。</span><span class="sxs-lookup"><span data-stu-id="a91db-110">The FROM clause specifies the pathname of the assembly to create.</span></span> <span data-ttu-id="a91db-111">此路徑可以是通用命名慣例 (UNC) 路徑，或是本機電腦的實體檔案路徑。</span><span class="sxs-lookup"><span data-stu-id="a91db-111">This path can either be a Universal Naming Convention (UNC) path or a physical file path that is local to the machine.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="a91db-112">不允許註冊具有相同名稱、文化特性及公開金鑰之不同版本的組件。</span><span class="sxs-lookup"><span data-stu-id="a91db-112">does not allow registering different versions of an assembly with the same name, culture and public key.</span></span>  
  
 <span data-ttu-id="a91db-113">您可以建立參考其他組件的組件。</span><span class="sxs-lookup"><span data-stu-id="a91db-113">It is possible to create assemblies that reference other assemblies.</span></span> <span data-ttu-id="a91db-114">當中建立元件時 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ，如果參考的元件尚未建立到資料庫中，則也會建立根層級元件所參考的元件。</span><span class="sxs-lookup"><span data-stu-id="a91db-114">When an assembly is created in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] also creates the assemblies referenced by the root-level assembly, if the referenced assemblies are not already created into the database.</span></span>  
  
 <span data-ttu-id="a91db-115">資料庫使用者或使用者角色擁有建立並因而擁有資料庫中之組件的權限。</span><span class="sxs-lookup"><span data-stu-id="a91db-115">Database users or user roles are given permissions to create, and thereby own, assemblies in a database.</span></span> <span data-ttu-id="a91db-116">若要建立組件，資料庫使用者或角色應該擁有 CREATE ASSEMBLY 權限。</span><span class="sxs-lookup"><span data-stu-id="a91db-116">In order to create assemblies, the database user or role should have the CREATE ASSEMBLY permission.</span></span>  
  
 <span data-ttu-id="a91db-117">如果是下列狀況，組件只會成功參考其他組件：</span><span class="sxs-lookup"><span data-stu-id="a91db-117">An assembly can only succeed in referencing other assemblies if:</span></span>  
  
-   <span data-ttu-id="a91db-118">呼叫或參考的組件是由相同的使用者或角色所擁有。</span><span class="sxs-lookup"><span data-stu-id="a91db-118">The assembly that is called or referenced is owned by the same user or role.</span></span>  
  
-   <span data-ttu-id="a91db-119">呼叫或參考的組件是在相同的資料庫中所建立。</span><span class="sxs-lookup"><span data-stu-id="a91db-119">The assembly that is called or referenced was created in the same database.</span></span>  
  
## <a name="specifying-security-when-creating-assemblies"></a><span data-ttu-id="a91db-120">建立組件時指定安全性</span><span class="sxs-lookup"><span data-stu-id="a91db-120">Specifying Security When Creating Assemblies</span></span>  
 <span data-ttu-id="a91db-121">在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 資料庫中建立組件時，您可以在能夠執行程式碼的三個不同安全性層級中，指定一個安全性層級：`SAFE`、`EXTERNAL_ACCESS` 或 `UNSAFE`。</span><span class="sxs-lookup"><span data-stu-id="a91db-121">When creating an assembly into a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] database, you can specify one of three different levels of security in which your code can run: `SAFE`, `EXTERNAL_ACCESS`, or `UNSAFE`.</span></span> <span data-ttu-id="a91db-122">執行 `CREATE ASSEMBLY` 陳述式時，系統會在可能造成組件無法在伺服器上註冊的程式碼組件上執行某些檢查。</span><span class="sxs-lookup"><span data-stu-id="a91db-122">When the `CREATE ASSEMBLY` statement is run, certain checks are performed on the code assembly which may cause the assembly to fail to register on the server.</span></span> <span data-ttu-id="a91db-123">如需詳細資訊，請參閱[CodePlex](https://msftengprodsamples.codeplex.com/)上的模擬範例。</span><span class="sxs-lookup"><span data-stu-id="a91db-123">For more information, see the Impersonation sample on [CodePlex](https://msftengprodsamples.codeplex.com/).</span></span>  
  
 <span data-ttu-id="a91db-124">`SAFE` 是預設的權限集，而且適用於大部分的狀況。</span><span class="sxs-lookup"><span data-stu-id="a91db-124">`SAFE` is the default permission set and works for the majority of scenarios.</span></span> <span data-ttu-id="a91db-125">若要指定給定的安全性層級，您要修改 CREATE ASSEMBLY 陳述式的語法，如下所示：</span><span class="sxs-lookup"><span data-stu-id="a91db-125">To specify a given security level, you modify the syntax of the CREATE ASSEMBLY statement as follows:</span></span>  
  
```  
CREATE ASSEMBLY SQLCLRTest  
FROM 'C:\MyDBApp\SQLCLRTest.dll'  
WITH PERMISSION_SET = SAFE;  
```  
  
 <span data-ttu-id="a91db-126">只要省略上述程式碼的第三行，也可以建立包含 `SAFE` 權限集的組件：</span><span class="sxs-lookup"><span data-stu-id="a91db-126">It is also possible to create an assembly with the `SAFE` permission set by simply omitting the third line of code above:</span></span>  
  
```  
CREATE ASSEMBLY SQLCLRTest  
FROM 'C:\MyDBApp\SQLCLRTest.dll';  
```  
  
 <span data-ttu-id="a91db-127">當組件中的程式碼在 `SAFE` 權限集下執行時，只能在伺服器內透過同處理序 Managed 提供者進行計算與資料存取。</span><span class="sxs-lookup"><span data-stu-id="a91db-127">When code in an assembly runs under the `SAFE` permission set, it can only do computation and data access within the server through the in-process managed provider.</span></span>  
  
### <a name="creating-external_access-and-unsafe-assemblies"></a><span data-ttu-id="a91db-128">建立 EXTERNAL_ACCESS 和 UNSAFE 組件</span><span class="sxs-lookup"><span data-stu-id="a91db-128">Creating EXTERNAL_ACCESS and UNSAFE Assemblies</span></span>  
 <span data-ttu-id="a91db-129">`EXTERNAL_ACCESS` 會處理程序碼需要存取伺服器外部資源的狀況，例如，檔案、網路、登錄和環境變數。</span><span class="sxs-lookup"><span data-stu-id="a91db-129">`EXTERNAL_ACCESS` addresses scenarios in which the code needs to access resources outside the server, such as files, network, registry, and environment variables.</span></span> <span data-ttu-id="a91db-130">每當伺服器存取外部資源時，它會模擬呼叫 Managed 程式碼之使用者的安全性內容。</span><span class="sxs-lookup"><span data-stu-id="a91db-130">Whenever the server accesses an external resource, it impersonates the security context of the user calling the managed code.</span></span>  
  
 <span data-ttu-id="a91db-131">在組件不是可驗證的安全，或者需要對於 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Win32 API 之類的限制資源之額外存取時，可以使用 `UNSAFE` 程式碼權限。</span><span class="sxs-lookup"><span data-stu-id="a91db-131">`UNSAFE` code permission is for those situations in which an assembly is not verifiably safe or requires additional access to restricted resources, such as the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Win32 API.</span></span>  
  
 <span data-ttu-id="a91db-132">若要在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 中建立 `EXTERNAL_ACCESS` 或 `UNSAFE` 組件，必須符合下列其中一個條件：</span><span class="sxs-lookup"><span data-stu-id="a91db-132">To create an `EXTERNAL_ACCESS` or `UNSAFE` assembly in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], one of the following two conditions must be met:</span></span>  
  
1.  <span data-ttu-id="a91db-133">組件是用強式名稱簽署，或用包含憑證的 Authenticode 簽署。</span><span class="sxs-lookup"><span data-stu-id="a91db-133">The assembly is strong name signed or Authenticode signed with a certificate.</span></span> <span data-ttu-id="a91db-134">此強式名稱 (或憑證) 在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 中會當做非對稱金鑰 (或憑證) 建立，而且擁有包含 `EXTERNAL ACCESS ASSEMBLY` 權限 (用於外部存取組件) 或 `UNSAFE ASSEMBLY` 權限 (用於不安全的組件) 的對應登入。</span><span class="sxs-lookup"><span data-stu-id="a91db-134">This strong name (or certificate) is created inside [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] as an asymmetric key (or certificate), and has a corresponding login with `EXTERNAL ACCESS ASSEMBLY` permission (for external access assemblies) or `UNSAFE ASSEMBLY` permission (for unsafe assemblies).</span></span>  
  
2.  <span data-ttu-id="a91db-135">資料庫擁有者 (DBO) `EXTERNAL ACCESS ASSEMBLY` (具有元件 `EXTERNAL ACCESS`) 或 `UNSAFE ASSEMBLY` (的元件 `UNSAFE`) 許可權，而且資料庫的 [可信任的資料庫][屬性](../../security/trustworthy-database-property.md)設為 `ON` 。</span><span class="sxs-lookup"><span data-stu-id="a91db-135">The database owner (DBO) has `EXTERNAL ACCESS ASSEMBLY` (for `EXTERNAL ACCESS` assemblies) or `UNSAFE ASSEMBLY` (for `UNSAFE` assemblies) permission, and the database has the [TRUSTWORTHY Database Property](../../security/trustworthy-database-property.md) set to `ON`.</span></span>  
  
 <span data-ttu-id="a91db-136">以上列出的兩個條件也會在組件載入時間 (包括執行) 進行檢查。</span><span class="sxs-lookup"><span data-stu-id="a91db-136">The two conditions listed above are also checked at assembly load time (which includes execution).</span></span> <span data-ttu-id="a91db-137">若要載入組件，至少必須符合其中一個條件。</span><span class="sxs-lookup"><span data-stu-id="a91db-137">At least one of the conditions must be met in order to load the assembly.</span></span>  
  
 <span data-ttu-id="a91db-138">我們建議您不要將資料庫上的 [可[信任的資料庫] 屬性](../../security/trustworthy-database-property.md)設為 `ON` [僅]，以在伺服器進程中執行 common LANGUAGE runtime (CLR) 程式碼。</span><span class="sxs-lookup"><span data-stu-id="a91db-138">We recommend that the [TRUSTWORTHY Database Property](../../security/trustworthy-database-property.md) on a database not be set to `ON` only to run common language runtime (CLR) code in the server process.</span></span> <span data-ttu-id="a91db-139">但是，建議從 master 資料庫的組件檔中建立非對稱金鑰。</span><span class="sxs-lookup"><span data-stu-id="a91db-139">Instead, we recommend that an asymmetric key be created from the assembly file in the master database.</span></span> <span data-ttu-id="a91db-140">接著，必須建立對應到此非對稱金鑰的登入，並授與登入 `EXTERNAL ACCESS ASSEMBLY` 或 `UNSAFE ASSEMBLY` 權限。</span><span class="sxs-lookup"><span data-stu-id="a91db-140">A login mapped to this asymmetric key must then be created, and the login must be granted `EXTERNAL ACCESS ASSEMBLY` or `UNSAFE ASSEMBLY` permission.</span></span>  
  
 <span data-ttu-id="a91db-141">執行 [!INCLUDE[tsql](../../../includes/tsql-md.md)] CREATE ASSEMBLY 語句之前的下列語句。</span><span class="sxs-lookup"><span data-stu-id="a91db-141">The following [!INCLUDE[tsql](../../../includes/tsql-md.md)] statements before running the CREATE ASSEMBLY statement.</span></span>  
  
```  
USE master;   
GO    
  
CREATE ASYMMETRIC KEY SQLCLRTestKey FROM EXECUTABLE FILE = 'C:\MyDBApp\SQLCLRTest.dll'     
CREATE LOGIN SQLCLRTestLogin FROM ASYMMETRIC KEY SQLCLRTestKey     
GRANT EXTERNAL ACCESS ASSEMBLY TO SQLCLRTestLogin;   
GO   
```  
  
> [!NOTE]  
>  <span data-ttu-id="a91db-142">您必須建立一個新的登入，並和非對稱金鑰相關聯。</span><span class="sxs-lookup"><span data-stu-id="a91db-142">You must create a new login to associate with the asymmetric key.</span></span> <span data-ttu-id="a91db-143">這個登入只會用來授與權限，並不需要和使用者相關聯，也不需要在應用程式中使用。</span><span class="sxs-lookup"><span data-stu-id="a91db-143">This login is only used to grant permissions; it does not have to be associated with a user, or used within the application.</span></span>  
  
 <span data-ttu-id="a91db-144">若要建立 `EXTERNAL ACCESS` 組件，建立者必須擁有 `EXTERNAL ACCESS` 權限。</span><span class="sxs-lookup"><span data-stu-id="a91db-144">To create an `EXTERNAL ACCESS` assembly, the creator needs to have `EXTERNAL ACCESS` permission.</span></span> <span data-ttu-id="a91db-145">這是在建立組件時指定的：</span><span class="sxs-lookup"><span data-stu-id="a91db-145">This is specified when creating the assembly:</span></span>  
  
```  
CREATE ASSEMBLY SQLCLRTest  
FROM 'C:\MyDBApp\SQLCLRTest.dll'  
WITH PERMISSION_SET = EXTERNAL_ACCESS;  
```  
  
 <span data-ttu-id="a91db-146">執行 [!INCLUDE[tsql](../../../includes/tsql-md.md)] CREATE ASSEMBLY 語句之前的下列語句。</span><span class="sxs-lookup"><span data-stu-id="a91db-146">The following [!INCLUDE[tsql](../../../includes/tsql-md.md)] statements before running the CREATE ASSEMBLY statement.</span></span>  
  
```  
USE master;   
GO    
  
CREATE ASYMMETRIC KEY SQLCLRTestKey FROM EXECUTABLE FILE = 'C:\MyDBApp\SQLCLRTest.dll';     
CREATE LOGIN SQLCLRTestLogin FROM ASYMMETRIC KEY SQLCLRTestKey ;    
GRANT UNSAFE ASSEMBLY TO SQLCLRTestLogin ;  
GO  
```  
  
 <span data-ttu-id="a91db-147">若要指定組件以 `UNSAFE` 權限載入，您可以在將組件載入到伺服器時，指定 `UNSAFE` 權限集：</span><span class="sxs-lookup"><span data-stu-id="a91db-147">To specify that an assembly loads with `UNSAFE` permission, you specify the `UNSAFE` permission set when loading the assembly into the server:</span></span>  
  
```  
CREATE ASSEMBLY SQLCLRTest  
FROM 'C:\MyDBApp\SQLCLRTest.dll'  
WITH PERMISSION_SET = UNSAFE;  
```  
  
 <span data-ttu-id="a91db-148">如需每個設定之許可權的詳細資訊，請參閱[CLR Integration Security](../security/clr-integration-security.md)。</span><span class="sxs-lookup"><span data-stu-id="a91db-148">For more details about the permissions for each of the settings, see [CLR Integration Security](../security/clr-integration-security.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a91db-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a91db-149">See Also</span></span>  
 <span data-ttu-id="a91db-150">[管理 CLR 整合元件](managing-clr-integration-assemblies.md) </span><span class="sxs-lookup"><span data-stu-id="a91db-150">[Managing CLR Integration Assemblies](managing-clr-integration-assemblies.md) </span></span>  
 <span data-ttu-id="a91db-151">[改變元件](altering-an-assembly.md) </span><span class="sxs-lookup"><span data-stu-id="a91db-151">[Altering an Assembly](altering-an-assembly.md) </span></span>  
 <span data-ttu-id="a91db-152">[卸載元件](dropping-an-assembly.md) </span><span class="sxs-lookup"><span data-stu-id="a91db-152">[Dropping an Assembly](dropping-an-assembly.md) </span></span>  
 <span data-ttu-id="a91db-153">[CLR 整合代碼啟用安全性](../security/clr-integration-code-access-security.md) </span><span class="sxs-lookup"><span data-stu-id="a91db-153">[CLR Integration Code Access Security](../security/clr-integration-code-access-security.md) </span></span>  
 <span data-ttu-id="a91db-154">[TRUSTWORTHY 資料庫屬性](../../security/trustworthy-database-property.md) </span><span class="sxs-lookup"><span data-stu-id="a91db-154">[TRUSTWORTHY Database Property](../../security/trustworthy-database-property.md) </span></span>  
 [<span data-ttu-id="a91db-155">允許部分信任的呼叫端</span><span class="sxs-lookup"><span data-stu-id="a91db-155">Allowing Partially Trusted Callers</span></span>](../../../database-engine/dev-guide/allowing-partially-trusted-callers.md)  
  
