---
title: CLR 整合安全性中的連結 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: reference
helpviewer_keywords:
- table-access links [CLR integration]
- security [CLR integration]
- invocation links [CLR integration]
- gated links [CLR integration]
ms.assetid: 168efd01-d12e-4bdf-a1b3-0b5c76474eaf
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 52a4f8084a8a90384c8916f2219faaf2c138b11c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709850"
---
# <a name="links-in-clr-integration-security"></a><span data-ttu-id="3e2bb-102">CLR 整合安全性中的連結</span><span class="sxs-lookup"><span data-stu-id="3e2bb-102">Links in CLR Integration Security</span></span>
  <span data-ttu-id="3e2bb-103">本節將描述使用者程式碼片段如何使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 或其中一種 Managed 語言在 [!INCLUDE[tsql](../../includes/tsql-md.md)] 中彼此呼叫。</span><span class="sxs-lookup"><span data-stu-id="3e2bb-103">This section describes how pieces of user code can call each other in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], either in [!INCLUDE[tsql](../../includes/tsql-md.md)] or in one of the managed languages.</span></span> <span data-ttu-id="3e2bb-104">這些物件之間的關聯性稱為連結。</span><span class="sxs-lookup"><span data-stu-id="3e2bb-104">These relationships between objects are referred to as links.</span></span>  
  
## <a name="invocation-links"></a><span data-ttu-id="3e2bb-105">引動過程連結</span><span class="sxs-lookup"><span data-stu-id="3e2bb-105">Invocation Links</span></span>  
 <span data-ttu-id="3e2bb-106">引動過程連結會對應至來自呼叫物件之使用者 (例如呼叫預存程序的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 批次) 或是 Common Language Runtime (CLR) 預存程序或函數的程式碼引動過程。</span><span class="sxs-lookup"><span data-stu-id="3e2bb-106">Invocation links correspond to a code invocation, either from a user calling an object (such as a [!INCLUDE[tsql](../../includes/tsql-md.md)] batch calling a stored procedure), or a common language runtime (CLR) stored procedure or function.</span></span> <span data-ttu-id="3e2bb-107">引動過程連結會導致系統檢查被呼叫者的 `EXECUTE` 權限。</span><span class="sxs-lookup"><span data-stu-id="3e2bb-107">Invocation links cause an `EXECUTE` permission on the callee to be checked.</span></span>  
  
## <a name="table-access-links"></a><span data-ttu-id="3e2bb-108">資料表存取連結</span><span class="sxs-lookup"><span data-stu-id="3e2bb-108">Table-Access Links</span></span>  
 <span data-ttu-id="3e2bb-109">資料表存取連結會對應至擷取或修改資料表、檢視表或資料表值函式中的值。</span><span class="sxs-lookup"><span data-stu-id="3e2bb-109">Table access links correspond to retrieving or modifying values in a table, view, or a table-valued function.</span></span> <span data-ttu-id="3e2bb-110">它們與引動過程連結類似，但它們在 SELECT、INSERT、UPDATE 及 DELETE 權限方面具有更精細的存取控制。</span><span class="sxs-lookup"><span data-stu-id="3e2bb-110">They are similar to invocation links, except that they have a finer-grained access control in terms of SELECT, INSERT, UPDATE, and DELETE permissions.</span></span>  
  
## <a name="gated-links"></a><span data-ttu-id="3e2bb-111">閘門守護式連結</span><span class="sxs-lookup"><span data-stu-id="3e2bb-111">Gated Links</span></span>  
 <span data-ttu-id="3e2bb-112">閘門守護式連結表示在執行期間，一旦建立了物件關聯性，就不會檢查該物件關聯性兩端的權限。</span><span class="sxs-lookup"><span data-stu-id="3e2bb-112">Gated links mean that during execution, permissions are not checked across the object relationship once it has been established.</span></span> <span data-ttu-id="3e2bb-113">當兩個物件之間有閘道連結 (例如，物件**x**和物件**y**) ，物件**y**的許可權和從物件**y**存取的其他物件，則只會在物件**x**的建立時間進行檢查。</span><span class="sxs-lookup"><span data-stu-id="3e2bb-113">When there is a gated link between two objects (for example, object **x** and object **y**), permissions on object **y** and other objects accessed from object **y** are checked only at the creation time of object **x**.</span></span> <span data-ttu-id="3e2bb-114">在物件**x**的建立時間， `REFERENCE` 會針對**x**的擁有者檢查**y**的許可權。</span><span class="sxs-lookup"><span data-stu-id="3e2bb-114">At the creation time of object **x**, `REFERENCE` permission is checked on **y** against the owner of **x**.</span></span> <span data-ttu-id="3e2bb-115">在執行時間， (例如，當有人呼叫 object **x**) 時，並不會針對**y**或其他以靜態方式參考的物件檢查許可權。</span><span class="sxs-lookup"><span data-stu-id="3e2bb-115">At execution time, (for example, when someone calls object **x**), there are no permissions checked against **y** or other objects it references statically.</span></span> <span data-ttu-id="3e2bb-116">在執行時間，將會針對物件**x**本身檢查適當的許可權。</span><span class="sxs-lookup"><span data-stu-id="3e2bb-116">At execution time, an appropriate permission will be checked against object **x** itself.</span></span>  
  
 <span data-ttu-id="3e2bb-117">閘門守護式連結一定會搭配兩個物件之間的中繼資料相依性使用。</span><span class="sxs-lookup"><span data-stu-id="3e2bb-117">Gated links are always used in conjunction with a metadata dependency between two objects.</span></span> <span data-ttu-id="3e2bb-118">這個中繼資料相依性就是在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 目錄中建立的關聯性，只要其他相依的物件存在，就可防止物件被卸除。</span><span class="sxs-lookup"><span data-stu-id="3e2bb-118">This metadata dependency is a relationship established in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] catalogs that prevents an object from being dropped as long as another object depends on it.</span></span>  
  
 <span data-ttu-id="3e2bb-119">當不適合進行或無法管理提供權限給許多相依物件的作業時，閘門守護式連結就很有用。</span><span class="sxs-lookup"><span data-stu-id="3e2bb-119">Gated links are useful when it is not appropriate or manageable to give permissions to many dependent objects.</span></span> <span data-ttu-id="3e2bb-120">閘門守護式連結會導入物件之間，以便定義 CLR 組件 (例如，CLR 程序、觸發程序、函數、類型和彙總) 與定義這些組件之來源組件的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 進入點。</span><span class="sxs-lookup"><span data-stu-id="3e2bb-120">Gated links are introduced between objects that define [!INCLUDE[tsql](../../includes/tsql-md.md)] entry points into CLR assemblies (for example, CLR procedures, triggers, functions, types, and aggregates) and the assemblies from which they are defined.</span></span> <span data-ttu-id="3e2bb-121">針對這些物件進行的閘門守護式安全性表示，若要叫用 CLR 組件中定義的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 進入點，呼叫者只需要該 [!INCLUDE[tsql](../../includes/tsql-md.md)] 進入點的適當權限。</span><span class="sxs-lookup"><span data-stu-id="3e2bb-121">Gated security against these objects implies that in order to invoke a [!INCLUDE[tsql](../../includes/tsql-md.md)] entry point defined in a CLR assembly, the caller only needs an appropriate permission on that [!INCLUDE[tsql](../../includes/tsql-md.md)] entry point.</span></span> <span data-ttu-id="3e2bb-122">呼叫者不需要擁有該組件或它以靜態方式參考之任何其他組件的權限。</span><span class="sxs-lookup"><span data-stu-id="3e2bb-122">The caller is not required to have permissions on that assembly or any other assemblies it statically references.</span></span> <span data-ttu-id="3e2bb-123">系統會在建立 [!INCLUDE[tsql](../../includes/tsql-md.md)] 進入點時檢查組件的權限。</span><span class="sxs-lookup"><span data-stu-id="3e2bb-123">The permissions on the assembly are checked at creation time of the [!INCLUDE[tsql](../../includes/tsql-md.md)] entry point.</span></span>  
  
## <a name="sql-server-authorization-based-security"></a><span data-ttu-id="3e2bb-124">以 SQL Server 授權為基礎的安全性</span><span class="sxs-lookup"><span data-stu-id="3e2bb-124">SQL Server Authorization-Based Security</span></span>  
 <span data-ttu-id="3e2bb-125">下面是以 CLR 為基礎之資料庫物件本身和之間之引動過程的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安全性檢查基本規則：前三項規則會定義要針對哪個物件檢查哪些權限，而第四項規則會定義要針對哪個執行內容檢查權限。</span><span class="sxs-lookup"><span data-stu-id="3e2bb-125">The following are the basic rules behind the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] security checks for invocations of and between CLR-based database objects; the first three rules define which permissions are checked and against which object; the fourth rule defines which execution context the permission is checked against.</span></span>  
  
1.  <span data-ttu-id="3e2bb-126">除非引動過程在相同的物件內部進行，否則所有引動過程都需要 `EXECUTE` 權限。這表示相同組件內部的呼叫不需要進行任何權限檢查。</span><span class="sxs-lookup"><span data-stu-id="3e2bb-126">All invocations require `EXECUTE` permission unless the invocations occur within the same object; this means that calls within the same assembly do not require any permission checks.</span></span> <span data-ttu-id="3e2bb-127">在執行時檢查權限。</span><span class="sxs-lookup"><span data-stu-id="3e2bb-127">The permission is checked at execution time.</span></span>  
  
2.  <span data-ttu-id="3e2bb-128">建立呼叫物件時，閘門守護式連結需要被呼叫者的 `REFERENCE` 權限。</span><span class="sxs-lookup"><span data-stu-id="3e2bb-128">Gated links require `REFERENCE` permission against the callee when the calling object is created.</span></span> <span data-ttu-id="3e2bb-129">當建立物件時，系統會檢查呼叫物件之擁有者的權限。</span><span class="sxs-lookup"><span data-stu-id="3e2bb-129">The permission is checked for the owner of the calling object when the object is created.</span></span>  
  
3.  <span data-ttu-id="3e2bb-130">針對要存取的資料表或檢視表，資料表存取連結需要對應的 `SELECT`、`INSERT`、`UPDATE` 或 `DELETE` 權限。</span><span class="sxs-lookup"><span data-stu-id="3e2bb-130">Table-access links require the corresponding `SELECT`, `INSERT`, `UPDATE`, or `DELETE` permission against the table or view being accessed.</span></span>  
  
4.  <span data-ttu-id="3e2bb-131">針對目前的執行內容，檢查權限。</span><span class="sxs-lookup"><span data-stu-id="3e2bb-131">The permission is checked against the current execution context.</span></span> <span data-ttu-id="3e2bb-132">您可以使用與呼叫者不同的執行內容來建立程序和函數。</span><span class="sxs-lookup"><span data-stu-id="3e2bb-132">Procedures and functions can be created with an execution context that is different from the caller.</span></span> <span data-ttu-id="3e2bb-133">不過，組件一定會使用針對它定義之程序、函數或觸發程序的執行內容建立。</span><span class="sxs-lookup"><span data-stu-id="3e2bb-133">Assemblies are always created with the execution context of the procedure, function, or trigger that is defined against it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e2bb-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3e2bb-134">See Also</span></span>  
 [<span data-ttu-id="3e2bb-135">CLR 整合安全性</span><span class="sxs-lookup"><span data-stu-id="3e2bb-135">CLR Integration Security</span></span>](../../relational-databases/clr-integration/security/clr-integration-security.md)  
  
  
