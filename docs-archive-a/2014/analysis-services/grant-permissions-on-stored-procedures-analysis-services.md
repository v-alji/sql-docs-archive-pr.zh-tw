---
title: 授與預存程式的許可權 (Analysis Services) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 01793166-a3e5-4856-8302-21b82d494e69
author: minewiskan
ms.author: owend
ms.openlocfilehash: 13d75ca8b6ff6e7d482e9d69894091518aa9469e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594258"
---
# <a name="grant-permissions-on-stored-procedures-analysis-services"></a><span data-ttu-id="47c97-102">授與預存程序 (Analysis Services) 的權限</span><span class="sxs-lookup"><span data-stu-id="47c97-102">Grant permissions on stored procedures (Analysis Services)</span></span>
  <span data-ttu-id="47c97-103">[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 中的預存程序 (或組件) 是以 [!INCLUDE[msCoName](../includes/msconame-md.md)] .NET 程式語言撰寫的外部常式，用於擴充 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 的功能。</span><span class="sxs-lookup"><span data-stu-id="47c97-103">Stored procedures, or assemblies, in [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] are external routines, written in a [!INCLUDE[msCoName](../includes/msconame-md.md)] .NET programming language, that extend the capabilities of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="47c97-104">組件可讓開發人員利用跨語言整合、例外狀況處理、版本控制支援、部署支援和偵錯支援等優點。</span><span class="sxs-lookup"><span data-stu-id="47c97-104">Assemblies let the developer take advantage of cross-language integration, exception handling, versioning support, deployment support, and debugging support.</span></span>  
  
 <span data-ttu-id="47c97-105">您必須是伺服器管理員，才能註冊組件。</span><span class="sxs-lookup"><span data-stu-id="47c97-105">You must be a Server Administrator to register an assembly.</span></span> <span data-ttu-id="47c97-106">請參閱[&#40;Analysis Services&#41;授與伺服器管理員許可權](instances/grant-server-admin-rights-to-an-analysis-services-instance.md)。</span><span class="sxs-lookup"><span data-stu-id="47c97-106">See [Grant Server Administrator Permissions &#40;Analysis Services&#41;](instances/grant-server-admin-rights-to-an-analysis-services-instance.md).</span></span>  
  
## <a name="security-context-for-stored-procedure-execution"></a><span data-ttu-id="47c97-107">預存程序執行的安全性內容</span><span class="sxs-lookup"><span data-stu-id="47c97-107">Security context for stored procedure execution</span></span>  
 <span data-ttu-id="47c97-108">所有使用者都可以呼叫預存程序。</span><span class="sxs-lookup"><span data-stu-id="47c97-108">Any user can call a stored procedure.</span></span> <span data-ttu-id="47c97-109">視預存程序的設定方式而定，程序可在呼叫程序之使用者的內容中，或是在匿名使用者的內容中執行。</span><span class="sxs-lookup"><span data-stu-id="47c97-109">Depending on how the stored procedure was configured, the procedure can run either in the context of the user calling the procedure or in the context of an anonymous user.</span></span> <span data-ttu-id="47c97-110">因為匿名使用者沒有安全性內容，請使用此功能及設定 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 的執行個體來允許匿名存取。</span><span class="sxs-lookup"><span data-stu-id="47c97-110">Because an anonymous user has no security context, use this capability together with configuring the instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] to permit anonymous access.</span></span>  
  
 <span data-ttu-id="47c97-111">在使用者呼叫預存程序之後，但在 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 執行預存程序之前，[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 會在預存程序內評估動作。</span><span class="sxs-lookup"><span data-stu-id="47c97-111">After the user calls a stored procedure but before [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] runs the stored procedure, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] evaluates the actions within the stored procedure.</span></span> [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] <span data-ttu-id="47c97-112">會根據已授與使用者的權限以及用來執行此程序的權限集合之間的交集，評估預存程序中的動作。</span><span class="sxs-lookup"><span data-stu-id="47c97-112">evaluates the actions in a stored procedure based on the intersection of the permissions granted to the user and the permission set used to run the procedure.</span></span> <span data-ttu-id="47c97-113">如果預存程序包含資料庫角色無法為使用者執行的動作，就不會執行該動作。</span><span class="sxs-lookup"><span data-stu-id="47c97-113">If the stored procedure contains any action that cannot be performed by the database role for the user, that action will not be performed.</span></span>  
  
 <span data-ttu-id="47c97-114">以下是用來執行預存程序的權限集合：</span><span class="sxs-lookup"><span data-stu-id="47c97-114">Following are the permission sets that are used to run stored procedures:</span></span>  
  
-   <span data-ttu-id="47c97-115">**安全**在安全許可權集合中，預存程式無法存取 .NET Framework 中受保護的資源 [!INCLUDE[msCoName](../includes/msconame-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="47c97-115">**Safe** With the Safe permission set, a stored procedure cannot access the protected resources in the [!INCLUDE[msCoName](../includes/msconame-md.md)] .NET Framework.</span></span> <span data-ttu-id="47c97-116">此權限集合只允許計算。</span><span class="sxs-lookup"><span data-stu-id="47c97-116">This permission set only allows for computations.</span></span> <span data-ttu-id="47c97-117">這是最安全的權限集合；資訊不會洩露到 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 之外，權限無法提高，使資料遭到竄改的風險降至最低。</span><span class="sxs-lookup"><span data-stu-id="47c97-117">This is the safest permission set; information does not leak outside [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], permissions cannot be elevated, and the risk of data tampering attacks is minimized.</span></span>  
  
-   <span data-ttu-id="47c97-118">**外部存取**使用外部存取權限集時，預存程式就可以使用受控碼來存取外部資源。</span><span class="sxs-lookup"><span data-stu-id="47c97-118">**External Access** With the External Access permission set, a stored procedure can access external resources by using managed code.</span></span> <span data-ttu-id="47c97-119">將預存程序設定為此權限集合不會造成可能導致伺服器不穩定的程式設計錯誤。</span><span class="sxs-lookup"><span data-stu-id="47c97-119">Setting a stored procedure to this permission set will not cause programming errors that could lead to server instability.</span></span> <span data-ttu-id="47c97-120">不過，此權限集合可能會導致資訊洩露到伺服器之外，而且權限有可能提高及資料遭到竄改的風險。</span><span class="sxs-lookup"><span data-stu-id="47c97-120">However, this permission set may result in information leaking outside the server, and the possibility of an elevation in permission and data tampering attacks.</span></span>  
  
-   <span data-ttu-id="47c97-121">不**受限制**有了不受限制的許可權集合，預存程式就可以使用任何程式碼來存取外部資源。</span><span class="sxs-lookup"><span data-stu-id="47c97-121">**Unrestricted** With the Unrestricted permission set, a stored procedure can access external resources by using any code.</span></span> <span data-ttu-id="47c97-122">使用此權限集合，就無法保證預存程序的安全性或可靠性。</span><span class="sxs-lookup"><span data-stu-id="47c97-122">With this permission set, there are no security or reliability guarantees for stored procedures.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47c97-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="47c97-123">See Also</span></span>  
 [<span data-ttu-id="47c97-124">多維度模型組件管理</span><span class="sxs-lookup"><span data-stu-id="47c97-124">Multidimensional Model Assemblies Management</span></span>](multidimensional-models/multidimensional-model-assemblies-management.md)  
  
  
