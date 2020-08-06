---
title: 開發人員&#39;s 指南 (Integration Services) |Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Integration Services, programming
- SSIS, programming
- SQL Server Integration Services, programming
- packages [Integration Services], programming
ms.assetid: 60fe148b-a7c4-4289-ae3e-2e949fc1886c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: c16ec1a21cf7ebb711f6d3996eb6239ea052c83c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599058"
---
# <a name="developer39s-guide-integration-services"></a><span data-ttu-id="0104f-102">開發人員&#39;s 指南 (Integration Services) </span><span class="sxs-lookup"><span data-stu-id="0104f-102">Developer&#39;s Guide (Integration Services)</span></span>
  [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] <span data-ttu-id="0104f-103">包括完全改寫的物件模型，已透過許多功能增強，這使得擴充封包和設計其程式更輕鬆、更彈性且更強大。</span><span class="sxs-lookup"><span data-stu-id="0104f-103">includes a completely rewritten object model, which has been enhanced with many features that make extending and programming packages easier, more flexible, and more powerful.</span></span> <span data-ttu-id="0104f-104">開發人員幾乎可以擴充和程式設計 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 封裝的每個層面。</span><span class="sxs-lookup"><span data-stu-id="0104f-104">Developers can extend and program almost every aspect of [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] packages.</span></span>  
  
 <span data-ttu-id="0104f-105">身為 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 開發人員，有兩種主要的方式可進行 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 的程式設計：</span><span class="sxs-lookup"><span data-stu-id="0104f-105">As an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] developer, there are two fundamental approaches that you can take to [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] programming:</span></span>  
  
-   <span data-ttu-id="0104f-106">您可以透過撰寫在 [!INCLUDE[ssIS](../includes/ssis-md.md)] 設計師中提供的元件，在封裝中提供自訂功能來擴充封包。</span><span class="sxs-lookup"><span data-stu-id="0104f-106">You can extend packages by writing components that become available within [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer to provide custom functionality in a package.</span></span>  
  
-   <span data-ttu-id="0104f-107">您可以從自己的應用程式以程式設計方式建立、設定和執行封裝。</span><span class="sxs-lookup"><span data-stu-id="0104f-107">You can create, configure, and run packages programmatically from your own applications.</span></span>  
  
 <span data-ttu-id="0104f-108">如果您發現 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 中的內建元件不符合需求，可以透過編寫自己的延伸模組，擴充 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 的功能。</span><span class="sxs-lookup"><span data-stu-id="0104f-108">If you find that the built-in components in [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] do not meet your requirements, you can extend the power of [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] by coding your own extensions.</span></span> <span data-ttu-id="0104f-109">在這種方法中，您有兩個完全不同的選項：</span><span class="sxs-lookup"><span data-stu-id="0104f-109">In this approach, you have two discrete options:</span></span>  
  
-   <span data-ttu-id="0104f-110">對於在單一封裝中的特定使用，您可以在指令碼工作中撰寫程式碼以建立自訂工作，或是在指令碼元件中撰寫程式碼以建立自訂資料流程元件，如此便可將其設定為來源、轉換或是目的地。</span><span class="sxs-lookup"><span data-stu-id="0104f-110">For ad hoc use in a single package, you can create a custom task by writing code in the Script task, or a custom data flow component by writing code in the Script component, which you can configure as a source, transformation, or destination.</span></span> <span data-ttu-id="0104f-111">這些強大的包裝函數會為您撰寫基礎結構程式碼，而且可讓您專門著重在開發自訂功能，不過，比較不容易在其他地方重複使用。</span><span class="sxs-lookup"><span data-stu-id="0104f-111">These powerful wrappers write the infrastructure code for you and let you focus exclusively on developing your custom functionality; however, they are not easily reusable elsewhere.</span></span>  
  
-   <span data-ttu-id="0104f-112">若要在多個封裝中使用，您可以建立自訂 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 延伸模組，例如連接管理員、工作、列舉值、記錄提供者以及資料流程元件。</span><span class="sxs-lookup"><span data-stu-id="0104f-112">For use in multiple packages, you can create custom [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] extensions such as connection managers, tasks, enumerators, log providers, and data flow components.</span></span> <span data-ttu-id="0104f-113">Managed [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 物件模型包含基底類別，可提供起點並使開發自訂延伸模組比以前更容易。</span><span class="sxs-lookup"><span data-stu-id="0104f-113">The managed [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] object model contains base classes that provide a starting point and make developing custom extensions easier than ever.</span></span>  
  
 <span data-ttu-id="0104f-114">如果您要動態建立封裝，或是要在開發環境以外的地方管理和執行 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 封裝，可以使用程式設計方式操作封裝。</span><span class="sxs-lookup"><span data-stu-id="0104f-114">If you want to create packages dynamically, or to manage and run [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] packages outside the development environment, you can manipulate packages programmatically.</span></span> <span data-ttu-id="0104f-115">您可以載入、修改和執行現有封裝，或是您可以用程式設計方式完全地建立和執行新封裝。</span><span class="sxs-lookup"><span data-stu-id="0104f-115">You can load, modify, and run existing packages, or you can create and run entirely new packages programmatically.</span></span> <span data-ttu-id="0104f-116">在這種方法中，您有連續範圍的選項：</span><span class="sxs-lookup"><span data-stu-id="0104f-116">In this approach, you have a continuous range of options:</span></span>  
  
-   <span data-ttu-id="0104f-117">在不須修改的情況下載入並執行現有的封裝。</span><span class="sxs-lookup"><span data-stu-id="0104f-117">Load and run an existing package without modification.</span></span>  
  
-   <span data-ttu-id="0104f-118">載入現有的封裝、重新設定 (例如，指定不同的資料來源) 然後加以執行。</span><span class="sxs-lookup"><span data-stu-id="0104f-118">Load an existing package, reconfigure it (for example, specify a different data source), and run it.</span></span>  
  
-   <span data-ttu-id="0104f-119">建立新封裝、加入和設定元件、逐物件和逐屬性地進行變更、儲存，然後加以執行。</span><span class="sxs-lookup"><span data-stu-id="0104f-119">Create a new package, add and configure components, making changes object by object and property by property, save it, and then run it.</span></span>  
  
 <span data-ttu-id="0104f-120">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 程式設計的這些方法將在本章節中說明並以範例示範。</span><span class="sxs-lookup"><span data-stu-id="0104f-120">These approaches to [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] programming are described in this section and demonstrated with examples.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0104f-121">本節內容</span><span class="sxs-lookup"><span data-stu-id="0104f-121">In This Section</span></span>  
 [<span data-ttu-id="0104f-122">Integration Services 程式設計概觀</span><span class="sxs-lookup"><span data-stu-id="0104f-122">Integration Services Programming Overview</span></span>](integration-services-programming-overview.md)  
 <span data-ttu-id="0104f-123">說明控制流程和資料流程在 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 開發工作中的角色。</span><span class="sxs-lookup"><span data-stu-id="0104f-123">Describes the roles of control flow and data flow in [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] development.</span></span>  
  
 [<span data-ttu-id="0104f-124">了解同步和非同步轉換</span><span class="sxs-lookup"><span data-stu-id="0104f-124">Understanding Synchronous and Asynchronous Transformations</span></span>](understanding-synchronous-and-asynchronous-transformations.md)  
 <span data-ttu-id="0104f-125">說明同步與非同步輸出之間的重要差別，以及會在資料流程中使用這些輸出的元件。</span><span class="sxs-lookup"><span data-stu-id="0104f-125">Describes the important distinction between synchronous and asynchronous outputs and the components that use them in the data flow.</span></span>  
  
 [<span data-ttu-id="0104f-126">以程式設計方式使用連線管理員</span><span class="sxs-lookup"><span data-stu-id="0104f-126">Working with Connection Managers Programmatically</span></span>](working-with-connection-managers-programmatically.md)  
 <span data-ttu-id="0104f-127">列出您可從 Managed 程式碼中使用的連接管理員，以及當程式碼呼叫 `AcquireConnection` 方法時，連接管理員所傳回的值。</span><span class="sxs-lookup"><span data-stu-id="0104f-127">Lists the connection managers that you can use from managed code, and the values that the connection managers return when the code calls the `AcquireConnection` method.</span></span>  
  
 [<span data-ttu-id="0104f-128">使用指令碼擴充套件</span><span class="sxs-lookup"><span data-stu-id="0104f-128">Extending Packages with Scripting</span></span>](extending-packages-scripting/extending-packages-with-scripting.md)  
 <span data-ttu-id="0104f-129">說明如何透過使用指令碼工作擴充控制流程，或是如何透過使用指令碼元件擴充資料流程。</span><span class="sxs-lookup"><span data-stu-id="0104f-129">Describes how to extend the control flow by using the Script task, or the data flow by using the Script component.</span></span>  
  
 [<span data-ttu-id="0104f-130">使用自訂物件擴充封裝</span><span class="sxs-lookup"><span data-stu-id="0104f-130">Extending Packages with Custom Objects</span></span>](extending-packages-custom-objects/extending-packages-with-custom-objects.md)  
 <span data-ttu-id="0104f-131">說明如何建立和程式設計自訂工作、資料流程元件以及其他封裝物件，以供在多個封裝中使用。</span><span class="sxs-lookup"><span data-stu-id="0104f-131">Describes how to create and program custom tasks, data flow components, and other package objects for use in multiple packages.</span></span>  
  
 [<span data-ttu-id="0104f-132">以程式設計方式建置套件</span><span class="sxs-lookup"><span data-stu-id="0104f-132">Building Packages Programmatically</span></span>](building-packages-programmatically/building-packages-programmatically.md)  
 <span data-ttu-id="0104f-133">描述如何以程式設計方式建立、設定和儲存 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 封裝。</span><span class="sxs-lookup"><span data-stu-id="0104f-133">Describes how to create, configure, and save [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] packages programmatically.</span></span>  
  
 [<span data-ttu-id="0104f-134">以程式設計方式執行及管理套件</span><span class="sxs-lookup"><span data-stu-id="0104f-134">Running and Managing Packages Programmatically</span></span>](run-manage-packages-programmatically/running-and-managing-packages-programmatically.md)  
 <span data-ttu-id="0104f-135">描述如何以程式設計方式列舉、執行和管理 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 封裝。</span><span class="sxs-lookup"><span data-stu-id="0104f-135">Describes how to enumerate, run, and manage [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] packages programmatically.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="0104f-136">參考</span><span class="sxs-lookup"><span data-stu-id="0104f-136">Reference</span></span>  
 [<span data-ttu-id="0104f-137">Integration Services 錯誤和訊息參考</span><span class="sxs-lookup"><span data-stu-id="0104f-137">Integration Services Error and Message Reference</span></span>](integration-services-error-and-message-reference.md)  
 <span data-ttu-id="0104f-138">列出預先定義的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 錯誤碼，以及其符號名稱與描述。</span><span class="sxs-lookup"><span data-stu-id="0104f-138">Lists the predefined [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] error codes, together with their symbolic names and descriptions.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="0104f-139">相關章節</span><span class="sxs-lookup"><span data-stu-id="0104f-139">Related Sections</span></span>  
 [<span data-ttu-id="0104f-140">套件開發的疑難排解工具</span><span class="sxs-lookup"><span data-stu-id="0104f-140">Troubleshooting Tools for Package Development</span></span>](troubleshooting/troubleshooting-tools-for-package-development.md)  
 <span data-ttu-id="0104f-141">描述 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 提供用以在開發期間疑難排解封裝的功能與工具。</span><span class="sxs-lookup"><span data-stu-id="0104f-141">Describes the features and tools that [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] provides for troubleshooting packages during development.</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="0104f-142">外部資源</span><span class="sxs-lookup"><span data-stu-id="0104f-142">External Resources</span></span>  
  
-   <span data-ttu-id="0104f-143">位於 www.codeplex.com/MSFTISProdSamples 的 CodePlex 範例：[Integration Services 產品範例](https://go.microsoft.com/fwlink/?LinkID=131204)</span><span class="sxs-lookup"><span data-stu-id="0104f-143">CodePlex samples, [Integration Services Product Samples](https://go.microsoft.com/fwlink/?LinkID=131204), on www.codeplex.com/MSFTISProdSamples</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0104f-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0104f-144">See Also</span></span>  
 [<span data-ttu-id="0104f-145">SQL Server Integration Services</span><span class="sxs-lookup"><span data-stu-id="0104f-145">SQL Server Integration Services</span></span>](sql-server-integration-services.md)  
  
  
