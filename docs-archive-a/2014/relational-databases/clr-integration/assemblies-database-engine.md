---
title: 元件 (資料庫引擎) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- assemblies [CLR integration]
- assemblies [CLR integration], about assemblies
- managed code [SQL Server], assemblies
ms.assetid: 4b146437-3061-47f6-9e8c-26eeea10b54e
author: rothja
ms.author: jroth
ms.openlocfilehash: 7edb18ccfa9954fe52093f87948f956c2eacc1b1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704194"
---
# <a name="assemblies-database-engine"></a><span data-ttu-id="c3d98-102">組件 (Database Engine)</span><span class="sxs-lookup"><span data-stu-id="c3d98-102">Assemblies (Database Engine)</span></span>
  <span data-ttu-id="c3d98-103">本節中的主題提供可協助您了解、設計和實作組件的資訊。</span><span class="sxs-lookup"><span data-stu-id="c3d98-103">The topics in this section provide information to help you understand, design, and implement assemblies.</span></span>  
  
 <span data-ttu-id="c3d98-104">元件是在實例中用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 來部署函式、預存程式、觸發程式、使用者定義匯總以及使用者定義型別（以 common language runtime 所裝載的其中一個 managed 程式碼語言所撰寫）的 DLL 檔案， [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 而不是中的 (CLR) [!INCLUDE[tsql](../../../includes/tsql-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="c3d98-104">Assemblies are DLL files used in an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] to deploy functions, stored procedures, triggers, user-defined aggregates, and user-defined types that are written in one of the managed code languages hosted by the [!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] common language runtime (CLR), instead of in [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="c3d98-105">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 中的組件是會參考 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] Common Language Runtime 中所建立 Managed 應用程式模組 (.dll 檔案) 的物件。</span><span class="sxs-lookup"><span data-stu-id="c3d98-105">An assembly in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] is an object that references a managed application module (.dll file) that was created in the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] common language runtime.</span></span> <span data-ttu-id="c3d98-106">組件包含類別中繼資料及 Managed 程式碼。</span><span class="sxs-lookup"><span data-stu-id="c3d98-106">An assembly contains class metadata and managed code.</span></span> <span data-ttu-id="c3d98-107">將組件上傳到 SQL Server 的執行個體是建立下列任何一個資料庫物件的首要步驟：</span><span class="sxs-lookup"><span data-stu-id="c3d98-107">Uploading an assembly to an instance of SQL Server is the first step toward creating any of the following database objects:</span></span>  
  
-   <span data-ttu-id="c3d98-108">CLR 函數。</span><span class="sxs-lookup"><span data-stu-id="c3d98-108">CLR functions.</span></span> <span data-ttu-id="c3d98-109">如需詳細資訊，請參閱[建立 CLR 函數](../user-defined-functions/create-clr-functions.md)。</span><span class="sxs-lookup"><span data-stu-id="c3d98-109">For more information, see [Create CLR Functions](../user-defined-functions/create-clr-functions.md).</span></span>  
  
-   <span data-ttu-id="c3d98-110">CLR 預存程序。</span><span class="sxs-lookup"><span data-stu-id="c3d98-110">CLR stored procedures.</span></span> <span data-ttu-id="c3d98-111">如需詳細資訊，請參閱[CLR 預存程式](../../database-engine/dev-guide/clr-stored-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="c3d98-111">For more information, see [CLR Stored Procedures](../../database-engine/dev-guide/clr-stored-procedures.md).</span></span>  
  
-   <span data-ttu-id="c3d98-112">CLR 觸發程序。</span><span class="sxs-lookup"><span data-stu-id="c3d98-112">CLR triggers.</span></span> <span data-ttu-id="c3d98-113">如需詳細資訊，請參閱[建立 CLR 觸發](../triggers/create-clr-triggers.md)程式。</span><span class="sxs-lookup"><span data-stu-id="c3d98-113">For more information, see [Create CLR Triggers](../triggers/create-clr-triggers.md).</span></span>  
  
-   <span data-ttu-id="c3d98-114">使用者自訂彙總函式。</span><span class="sxs-lookup"><span data-stu-id="c3d98-114">User-defined aggregate functions.</span></span> <span data-ttu-id="c3d98-115">如需詳細資訊，請參閱[建立使用者定義匯總](../user-defined-functions/create-user-defined-aggregates.md)。</span><span class="sxs-lookup"><span data-stu-id="c3d98-115">For more information, see [Create User-defined Aggregates](../user-defined-functions/create-user-defined-aggregates.md).</span></span>  
  
-   <span data-ttu-id="c3d98-116">使用者定義型別。</span><span class="sxs-lookup"><span data-stu-id="c3d98-116">User-defined types.</span></span> <span data-ttu-id="c3d98-117">如需詳細資訊，請參閱[使用使用者定義型別](../native-client/features/using-user-defined-types.md)。</span><span class="sxs-lookup"><span data-stu-id="c3d98-117">For more information, see [Using User-Defined Types](../native-client/features/using-user-defined-types.md).</span></span>  
  
 <span data-ttu-id="c3d98-118">組件在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 中會執行下列功能：</span><span class="sxs-lookup"><span data-stu-id="c3d98-118">Assemblies perform the following functions in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]:</span></span>  
  
-   <span data-ttu-id="c3d98-119">包含執行先前所列之一或多個 CLR 資料庫物件功能的 Managed 程式碼。</span><span class="sxs-lookup"><span data-stu-id="c3d98-119">Contain the managed code that runs the functionality of one or more of the CLR database objects previously listed.</span></span>  
  
-   <span data-ttu-id="c3d98-120">包含的中繼資料包括組件的版本號碼和文化特性、可唯一地識別組件之類別清單的選用公開金鑰、組件中定義的方法，以及組件的處理器架構。</span><span class="sxs-lookup"><span data-stu-id="c3d98-120">Contain metadata that includes the version number and culture of the assembly, an optional public key that uniquely identifies the list of classes of the assembly, the methods that are defined in the assembly, and the processor architecture of the assembly.</span></span>  
  
-   <span data-ttu-id="c3d98-121">透過調整程式碼存取權限，管理 Managed 程式碼可存取外部資源的程度。</span><span class="sxs-lookup"><span data-stu-id="c3d98-121">Manage the degree to which managed code can access outside resources by regulating code access permissions.</span></span>  
  
-   <span data-ttu-id="c3d98-122">包含組件所參考的其他組件之相依性的相關中繼資料。</span><span class="sxs-lookup"><span data-stu-id="c3d98-122">Contain metadata about dependencies on other assemblies that are referenced by the assembly.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c3d98-123">本節內容</span><span class="sxs-lookup"><span data-stu-id="c3d98-123">In This Section</span></span>  
  
|<span data-ttu-id="c3d98-124">主題</span><span class="sxs-lookup"><span data-stu-id="c3d98-124">Topic</span></span>|<span data-ttu-id="c3d98-125">描述</span><span class="sxs-lookup"><span data-stu-id="c3d98-125">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="c3d98-126">設計組件</span><span class="sxs-lookup"><span data-stu-id="c3d98-126">Designing Assemblies</span></span>](assemblies-designing.md)|<span data-ttu-id="c3d98-127">解釋在建立組件之前，您必須考慮的項目。</span><span class="sxs-lookup"><span data-stu-id="c3d98-127">Explains what you have to consider before creating an assembly.</span></span> <span data-ttu-id="c3d98-128">包括封裝組件、程式碼存取權限，以及其他的限制。</span><span class="sxs-lookup"><span data-stu-id="c3d98-128">This includes packaging assemblies, code access permissions, and other restrictions.</span></span>|  
|[<span data-ttu-id="c3d98-129">實作組件</span><span class="sxs-lookup"><span data-stu-id="c3d98-129">Implementing Assemblies</span></span>](assemblies-implementing.md)|<span data-ttu-id="c3d98-130">解釋如何建立和卸除組件、如何修改組件和修改組件的時機，以及如何擷取關於組件的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="c3d98-130">Explains how to create and drop assemblies, how and when to modify assemblies, and how to retrieve metadata about assemblies.</span></span>|  
|[<span data-ttu-id="c3d98-131">取得組件的相關資訊</span><span class="sxs-lookup"><span data-stu-id="c3d98-131">Getting Information About Assemblies</span></span>](assemblies-getting-information.md)|<span data-ttu-id="c3d98-132">列出可用來查詢組件相關中繼資料的目錄檢視和函數。</span><span class="sxs-lookup"><span data-stu-id="c3d98-132">Lists the catalog views and functions that can be queried for metadata about assemblies.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c3d98-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c3d98-133">See Also</span></span>  
 [<span data-ttu-id="c3d98-134">Common Language Runtime &#40;CLR&#41; 整合程式設計概念</span><span class="sxs-lookup"><span data-stu-id="c3d98-134">Common Language Runtime &#40;CLR&#41; Integration Programming Concepts</span></span>](common-language-runtime-clr-integration-programming-concepts.md)  
  
  
