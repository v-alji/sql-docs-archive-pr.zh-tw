---
title: 執行元件 |Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- assemblies [CLR integration], implementing
ms.assetid: c228d7bf-a906-4f37-a057-5d464d962ff8
author: rothja
ms.author: jroth
ms.openlocfilehash: 3cb3818ed644eede3cf4f2c256a0dcb94ec58c3a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704182"
---
# <a name="implementing-assemblies"></a><span data-ttu-id="8230d-102">實作組件</span><span class="sxs-lookup"><span data-stu-id="8230d-102">Implementing Assemblies</span></span>
  <span data-ttu-id="8230d-103">本主題提供下列部分的資訊，協助您實作和使用資料庫中的組件：</span><span class="sxs-lookup"><span data-stu-id="8230d-103">This topic provides information about the following areas to help you implement and work with assemblies in the database:</span></span>  
  
-   <span data-ttu-id="8230d-104">建立組件</span><span class="sxs-lookup"><span data-stu-id="8230d-104">Creating assemblies</span></span>  
  
-   <span data-ttu-id="8230d-105">修改組件</span><span class="sxs-lookup"><span data-stu-id="8230d-105">Modifying assemblies</span></span>  
  
-   <span data-ttu-id="8230d-106">卸除、停用和啟用組件</span><span class="sxs-lookup"><span data-stu-id="8230d-106">Dropping, disabling, and enabling assemblies</span></span>  
  
-   <span data-ttu-id="8230d-107">管理組件版本</span><span class="sxs-lookup"><span data-stu-id="8230d-107">Managing assembly versions</span></span>  
  
## <a name="creating-assemblies"></a><span data-ttu-id="8230d-108">建立組件</span><span class="sxs-lookup"><span data-stu-id="8230d-108">Creating Assemblies</span></span>  
 <span data-ttu-id="8230d-109">組件是使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] CREATE ASSEMBLY 陳述式在 [!INCLUDE[tsql](../../includes/tsql-md.md)] 中建立，或使用 Assembly Assisted Editor 在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中建立。</span><span class="sxs-lookup"><span data-stu-id="8230d-109">Assemblies are created in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] by using the [!INCLUDE[tsql](../../includes/tsql-md.md)] CREATE ASSEMBLY statement, or in the [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] by using the Assembly Assisted Editor.</span></span> <span data-ttu-id="8230d-110">此外，在中部署 SQL Server 專案， [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 會在指定給專案的資料庫中註冊元件。</span><span class="sxs-lookup"><span data-stu-id="8230d-110">Additionally, deploying a SQL Server Project in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] registers an assembly in the database that was specified for the project.</span></span> <span data-ttu-id="8230d-111">如需詳細資訊，請參閱 [Deploying CLR Database Objects](deploying-clr-database-objects.md)。</span><span class="sxs-lookup"><span data-stu-id="8230d-111">For more information, see [Deploying CLR Database Objects](deploying-clr-database-objects.md).</span></span>  
  
 <span data-ttu-id="8230d-112">**若要使用 Transact-SQL 建立組件**</span><span class="sxs-lookup"><span data-stu-id="8230d-112">**To create an assembly by using Transact-SQL**</span></span>  
  
-   [<span data-ttu-id="8230d-113">CREATE ASSEMBLY &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="8230d-113">CREATE ASSEMBLY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-assembly-transact-sql)  
  
 <span data-ttu-id="8230d-114">**若要使用 SQL Server Management Studio 建立組件**</span><span class="sxs-lookup"><span data-stu-id="8230d-114">**To create an assembly by using SQL Server Management Studio**</span></span>  
  
-   [<span data-ttu-id="8230d-115">&#40;一般頁面的元件屬性&#41;</span><span class="sxs-lookup"><span data-stu-id="8230d-115">Assembly Properties &#40;General Page&#41;</span></span>](assemblies-properties.md)  
  
## <a name="modifying-assemblies"></a><span data-ttu-id="8230d-116">修改組件</span><span class="sxs-lookup"><span data-stu-id="8230d-116">Modifying Assemblies</span></span>  
 <span data-ttu-id="8230d-117">組件是使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ALTER ASSEMBLY 陳述式在 [!INCLUDE[tsql](../../includes/tsql-md.md)] 中修改，或使用 Assembly Assisted Editor 在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中修改。</span><span class="sxs-lookup"><span data-stu-id="8230d-117">Assemblies are modified in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] by using the [!INCLUDE[tsql](../../includes/tsql-md.md)] ALTER ASSEMBLY statement or in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] by using the Assembly Assisted Editor.</span></span> <span data-ttu-id="8230d-118">當您要執行下列動作時可以修改組件：</span><span class="sxs-lookup"><span data-stu-id="8230d-118">You can modify an assembly when you want to do the following:</span></span>  
  
-   <span data-ttu-id="8230d-119">上傳較新版的二進位編碼檔案組件，以變更組件的實作。</span><span class="sxs-lookup"><span data-stu-id="8230d-119">Change the implementation of the assembly by uploading a newer version of the binaries of the assembly.</span></span> <span data-ttu-id="8230d-120">如需詳細資訊，請參閱本主題稍後的[管理元件版本](#_managing)。</span><span class="sxs-lookup"><span data-stu-id="8230d-120">For more information, see [Managing Assembly Versions](#_managing) later in this topic.</span></span>  
  
-   <span data-ttu-id="8230d-121">變更組件的權限集。</span><span class="sxs-lookup"><span data-stu-id="8230d-121">Change the permission set of the assembly.</span></span> <span data-ttu-id="8230d-122">如需詳細資訊，請參閱[設計組件](../../relational-databases/clr-integration/assemblies-designing.md)。</span><span class="sxs-lookup"><span data-stu-id="8230d-122">For more information, see [Designing Assemblies](../../relational-databases/clr-integration/assemblies-designing.md).</span></span>  
  
-   <span data-ttu-id="8230d-123">變更組件的可見性。</span><span class="sxs-lookup"><span data-stu-id="8230d-123">Change the visibility of the assembly.</span></span> <span data-ttu-id="8230d-124">可見的組件可在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中用來參考。</span><span class="sxs-lookup"><span data-stu-id="8230d-124">Visible assemblies are available for referencing in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="8230d-125">看不見的組件則無法使用，即使已在資料庫中上傳它們也一樣。</span><span class="sxs-lookup"><span data-stu-id="8230d-125">Nonvisible assemblies are not available, even if they have been uploaded in the database.</span></span> <span data-ttu-id="8230d-126">依預設，上傳至 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體的組件是可見的。</span><span class="sxs-lookup"><span data-stu-id="8230d-126">By default, assemblies uploaded to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] are visible.</span></span>  
  
-   <span data-ttu-id="8230d-127">加入或卸除與組件關聯的偵錯或來源檔。</span><span class="sxs-lookup"><span data-stu-id="8230d-127">Add or drop a debug or source file associated with the assembly.</span></span>  
  
 <span data-ttu-id="8230d-128">**若要使用 Transact-SQL 修改組件**</span><span class="sxs-lookup"><span data-stu-id="8230d-128">**To modify an assembly by using Transact-SQL**</span></span>  
  
-   [<span data-ttu-id="8230d-129">ALTER ASSEMBLY &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="8230d-129">ALTER ASSEMBLY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-assembly-transact-sql)  
  
 <span data-ttu-id="8230d-130">**若要使用 SQL Server Management Studio 修改組件**</span><span class="sxs-lookup"><span data-stu-id="8230d-130">**To modify an assembly by using SQL Server Management Studio**</span></span>  
  
-   [<span data-ttu-id="8230d-131">&#40;一般頁面的元件屬性&#41;</span><span class="sxs-lookup"><span data-stu-id="8230d-131">Assembly Properties &#40;General Page&#41;</span></span>](assemblies-properties.md)  
  
## <a name="dropping-disabling-and-enabling-assemblies"></a><span data-ttu-id="8230d-132">卸除、停用和啟用組件</span><span class="sxs-lookup"><span data-stu-id="8230d-132">Dropping, Disabling, and Enabling Assemblies</span></span>  
 <span data-ttu-id="8230d-133">使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] DROP ASSEMBLY 陳述式或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 卸除組件。</span><span class="sxs-lookup"><span data-stu-id="8230d-133">Assemblies are dropped by using the [!INCLUDE[tsql](../../includes/tsql-md.md)] DROP ASSEMBLY statement or [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="8230d-134">**若要使用 Transact-SQL 卸除組件**</span><span class="sxs-lookup"><span data-stu-id="8230d-134">**To drop an assembly by using Transact-SQL**</span></span>  
  
-   [<span data-ttu-id="8230d-135">DROP ASSEMBLY &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="8230d-135">DROP ASSEMBLY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/drop-assembly-transact-sql)  
  
 <span data-ttu-id="8230d-136">**若要使用 SQL Server Management Studio 卸除組件**</span><span class="sxs-lookup"><span data-stu-id="8230d-136">**To drop an assembly by using SQL Server Management Studio**</span></span>  
  
-   [<span data-ttu-id="8230d-137">刪除物件</span><span class="sxs-lookup"><span data-stu-id="8230d-137">Delete Objects</span></span>](../../ssms/object/delete-objects.md)  
  
 <span data-ttu-id="8230d-138">依預設，在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中建立的所有組件都會停用執行。</span><span class="sxs-lookup"><span data-stu-id="8230d-138">By default, all assemblies that are created in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] are disabled from executing.</span></span> <span data-ttu-id="8230d-139">您可以使用**sp_configure**系統預存程式的**clr enabled**選項，來停用或啟用在中上傳的所有元件的執行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="8230d-139">You can use the **clr enabled** option of the **sp_configure** system stored procedure to disable or enable the execution of all assemblies that are uploaded in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="8230d-140">停用組件的執行可防止執行 Common Language Runtime (CLR) 函數、預存程序、觸發程序、彙總和使用者定義型別，並可停止那些正在執行的。</span><span class="sxs-lookup"><span data-stu-id="8230d-140">Disabling assembly execution prevents common language runtime (CLR) functions, stored procedures, triggers, aggregates, and user-defined types from executing, and stops those that are currently executing.</span></span> <span data-ttu-id="8230d-141">停用組件的執行並不會停用建立、修改或卸除組件的功能。</span><span class="sxs-lookup"><span data-stu-id="8230d-141">Disabling assembly execution does not disable the ability to create, alter, or drop assemblies.</span></span> <span data-ttu-id="8230d-142">如需詳細資訊，請參閱[clr 已啟用伺服器設定選項](../../database-engine/configure-windows/clr-enabled-server-configuration-option.md)。</span><span class="sxs-lookup"><span data-stu-id="8230d-142">For more information, see [clr enabled Server Configuration Option](../../database-engine/configure-windows/clr-enabled-server-configuration-option.md).</span></span>  
  
 <span data-ttu-id="8230d-143">**若要停用和啟用組件執行**</span><span class="sxs-lookup"><span data-stu-id="8230d-143">**To disable and enable assembly execution**</span></span>  
  
-   [<span data-ttu-id="8230d-144">sp_configure &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="8230d-144">sp_configure &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
##  <a name="managing-assembly-versions"></a><a name="_managing"></a><span data-ttu-id="8230d-145">管理元件版本</span><span class="sxs-lookup"><span data-stu-id="8230d-145">Managing Assembly Versions</span></span>  
 <span data-ttu-id="8230d-146">在將組件上傳至 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體時，組件是在資料庫系統目錄中儲存和管理。</span><span class="sxs-lookup"><span data-stu-id="8230d-146">When an assembly is uploaded to an instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the assembly is stored and managed within the database system catalogs.</span></span> <span data-ttu-id="8230d-147">在中對元件定義所做的任何變更，都 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 應該傳播至儲存在資料庫目錄中的元件。</span><span class="sxs-lookup"><span data-stu-id="8230d-147">Any changes made to the definition of the assembly in the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] should be propagated to the assembly that is stored in the database catalog.</span></span>  
  
 <span data-ttu-id="8230d-148">當您必須修改組件時，您必須發出 ALTER ASSEMBLY 陳述式來更新資料庫中的組件。</span><span class="sxs-lookup"><span data-stu-id="8230d-148">When you have to modify an assembly, you must issue an ALTER ASSEMBLY statement to update the assembly in the database.</span></span> <span data-ttu-id="8230d-149">這將會使組件更新至保存其實作的最新 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 模組副本。</span><span class="sxs-lookup"><span data-stu-id="8230d-149">This will update the assembly to the latest copy of [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] modules holding its implementation.</span></span>  
  
 <span data-ttu-id="8230d-150">ALTER ASSEMBLY 陳述式的 WITH UNCHECKED DATA 子句可指示 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 重新整理那些甚至是與在資料庫中的保存資料相依之組件。</span><span class="sxs-lookup"><span data-stu-id="8230d-150">The WITH UNCHECKED DATA clause of the ALTER ASSEMBLY statement instructs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to refresh even those assemblies upon which persisted data in the database is dependent.</span></span> <span data-ttu-id="8230d-151">特別是，如果下列任一項存在，您就必須指定 WITH UNCHECKED DATA：</span><span class="sxs-lookup"><span data-stu-id="8230d-151">Specifically, you must specify WITH UNCHECKED DATA if any of the following exist:</span></span>  
  
-   <span data-ttu-id="8230d-152">透過 [!INCLUDE[tsql](../../includes/tsql-md.md)] 函數或方法直接或間接參考組件中的方法之保存的計算資料行。</span><span class="sxs-lookup"><span data-stu-id="8230d-152">Persisted computed columns that reference methods in the assembly, either directly, or indirectly, through [!INCLUDE[tsql](../../includes/tsql-md.md)] functions or methods.</span></span>  
  
-   <span data-ttu-id="8230d-153">相依於組件的 CLR 使用者定義型別資料行，以及實作 **UserDefined** (非**原生**) 序列化格式之類型的資料行。</span><span class="sxs-lookup"><span data-stu-id="8230d-153">Columns of a CLR user-defined type that depend on the assembly, and the type implements a **UserDefined** (non-**Native**) serialization format.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="8230d-154">在未指定 WITH UNCHECKED DATA 的情況下，如果新組件版本影響資料表、索引或其他永續性站台中現有的資料，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 將嘗試阻止 ALTER ASSEMBLY 執行。</span><span class="sxs-lookup"><span data-stu-id="8230d-154">If WITH UNCHECKED DATA is not specified, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tries to prevent ALTER ASSEMBLY from executing if the new assembly version affects existing data in tables, indexes, or other persistent sites.</span></span> <span data-ttu-id="8230d-155">不過，當 CLR 組件更新時，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 並不保證計算資料行、索引、索引檢視或運算式都會與基礎常式及類型保持一致。</span><span class="sxs-lookup"><span data-stu-id="8230d-155">However, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] does not guarantee that computed columns, indexes, indexed views, or expressions will be consistent with the underlying routines and types when the CLR assembly is updated.</span></span> <span data-ttu-id="8230d-156">執行 ALTER ASSEMBLY 時請小心，以確定運算式結果與儲存在組件中以該運算式為基礎的值之間相符。</span><span class="sxs-lookup"><span data-stu-id="8230d-156">Be careful when you execute ALTER ASSEMBLY to make sure that there is no mismatch between the result of an expression and a value that is based on that expression stored in the assembly.</span></span>  
  
 <span data-ttu-id="8230d-157">只有**db_owner**和**db_ddlowner**固定資料庫角色的成員，才能使用 WITH UNCHECKED DATA 子句來執行 run ALTER ASSEMBLY。</span><span class="sxs-lookup"><span data-stu-id="8230d-157">Only members of the **db_owner** and **db_ddlowner** fixed database role can execute run ALTER ASSEMBLY by using the WITH UNCHECKED DATA clause.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="8230d-158">會在 Windows 應用程式事件記錄公佈訊息，說明已使用資料表中未檢查的資料修改過組件。</span><span class="sxs-lookup"><span data-stu-id="8230d-158">posts a message to the Windows application event log that the assembly has been modified with unchecked data in the tables.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="8230d-159">接著會在有未檢查的資料時，標示任何包含與組件相依的資料之資料表。</span><span class="sxs-lookup"><span data-stu-id="8230d-159">then marks any tables that contain data dependent on the assembly as having unchecked data.</span></span> <span data-ttu-id="8230d-160">**Sys.databases**目錄檢視的**has_unchecked_assembly_data**資料行包含值1，適用于包含未檢查資料的資料表，而0代表沒有未檢查資料的資料表。</span><span class="sxs-lookup"><span data-stu-id="8230d-160">The **has_unchecked_assembly_data** column of the **sys.tables** catalog view contains the value 1 for tables that contain unchecked data, and 0 for tables without unchecked data.</span></span>  
  
 <span data-ttu-id="8230d-161">若要解決未檢查資料的完整性，請針對未檢查資料的每個資料表執行 DBCC CHECKTABLE。</span><span class="sxs-lookup"><span data-stu-id="8230d-161">To resolve the integrity of unchecked data, run DBCC CHECKTABLE against each table that has unchecked data.</span></span> <span data-ttu-id="8230d-162">如果 DBCC CHECKTABLE 失敗，您必須刪除無效的資料表資料列或修改組件程式碼來處理問題，然後發出其他的 ALTER ASSEMBLY 陳述式。</span><span class="sxs-lookup"><span data-stu-id="8230d-162">If DBCC CHECKTABLE fails, you must either delete the table rows that are not valid or modify the assembly code to address problems, and then issue additional ALTER ASSEMBLY statements.</span></span>  
  
 <span data-ttu-id="8230d-163">ALTER ASSEMBLY 會變更組件版本。</span><span class="sxs-lookup"><span data-stu-id="8230d-163">ALTER ASSEMBLY changes the assembly version.</span></span> <span data-ttu-id="8230d-164">元件的文化特性和公開金鑰標記會保持不變。SQL Server 不允許註冊具有相同名稱、文化特性及公開金鑰之不同版本的元件。</span><span class="sxs-lookup"><span data-stu-id="8230d-164">The culture and public key token of the assembly remain the same.SQL Server does not allow registering different versions of an assembly with the same name, culture and public key.</span></span>  
  
### <a name="interactions-with-computer-wide-policy-for-version-binding"></a><span data-ttu-id="8230d-165">與版本繫結的電腦通用原則互動</span><span class="sxs-lookup"><span data-stu-id="8230d-165">Interactions with Computer-wide Policy for Version Binding</span></span>  
 <span data-ttu-id="8230d-166">如果儲存在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中的組件參考，使用簽發者原則或電腦通用管理原則重新導向至特定版本，您必須執行下列其中一個動作：</span><span class="sxs-lookup"><span data-stu-id="8230d-166">If references to assemblies stored in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] are redirected to specific versions by using publisher policy or computer-wide administrator policy, you must do either of the following:</span></span>  
  
-   <span data-ttu-id="8230d-167">請確定是在資料庫中執行導向至新版本。</span><span class="sxs-lookup"><span data-stu-id="8230d-167">Make sure the new version to which this redirection is made is in the database.</span></span>  
  
-   <span data-ttu-id="8230d-168">請修改任何對於電腦或簽發者原則的外部原則檔案之陳述式，以確定它們所參考的特定版本是在資料庫中。</span><span class="sxs-lookup"><span data-stu-id="8230d-168">Modify any statements to the external policy files of the computer or publisher policy to make sure that they reference the specific version that is in the database.</span></span>  
  
 <span data-ttu-id="8230d-169">否則，嘗試載入新組件版本至 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體將會失敗。</span><span class="sxs-lookup"><span data-stu-id="8230d-169">Otherwise, an attempt to load a new assembly version to the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] will fail.</span></span>  
  
 <span data-ttu-id="8230d-170">**更新組件的版本**</span><span class="sxs-lookup"><span data-stu-id="8230d-170">**To update the version of an assembly**</span></span>  
  
-   [<span data-ttu-id="8230d-171">ALTER ASSEMBLY &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="8230d-171">ALTER ASSEMBLY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-assembly-transact-sql)  
  
## <a name="see-also"></a><span data-ttu-id="8230d-172">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8230d-172">See Also</span></span>  
 <span data-ttu-id="8230d-173">[元件 &#40;資料庫引擎&#41;](../../relational-databases/clr-integration/assemblies-database-engine.md) </span><span class="sxs-lookup"><span data-stu-id="8230d-173">[Assemblies &#40;Database Engine&#41;](../../relational-databases/clr-integration/assemblies-database-engine.md) </span></span>  
 [<span data-ttu-id="8230d-174">取得組件的相關資訊</span><span class="sxs-lookup"><span data-stu-id="8230d-174">Getting Information About Assemblies</span></span>](../../relational-databases/clr-integration/assemblies-getting-information.md)  
  
  
