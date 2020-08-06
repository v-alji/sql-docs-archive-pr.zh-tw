---
title: 使用自訂物件擴充封裝 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
ms.assetid: 26616eb8-9e80-434d-b22a-ece1b00f449d
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 0159983f518e51aa082ea23745663e7f09eee1fc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686450"
---
# <a name="extending-packages-with-custom-objects"></a><span data-ttu-id="46f46-102">使用自訂物件擴充封裝</span><span class="sxs-lookup"><span data-stu-id="46f46-102">Extending Packages with Custom Objects</span></span>
  <span data-ttu-id="46f46-103">如果發現 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 中提供的元件不符合需求，可以編寫自己的延伸模組，擴充 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 的功能。</span><span class="sxs-lookup"><span data-stu-id="46f46-103">If you find that the components provided in [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] do not meet your requirements, you can extend the power of [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] by coding your own extensions.</span></span> <span data-ttu-id="46f46-104">您有兩個完全不同的選項可擴充封裝：其一是在指令碼工作與指令碼元件所提供的強大包裝函數中撰寫程式碼；其二則是可以從 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 物件模型提供的基底類別衍生，從頭建立自訂 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 延伸模組。</span><span class="sxs-lookup"><span data-stu-id="46f46-104">You have two discrete options for extending your packages: you can write code within the powerful wrappers provided by the Script task and the Script component, or you can create custom [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] extensions from scratch by deriving from the base classes provided by the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] object model.</span></span>  
  
 <span data-ttu-id="46f46-105">本章節探索兩個選項當中更進階的部分：以自訂物件擴充封裝。</span><span class="sxs-lookup"><span data-stu-id="46f46-105">This section explores the more advanced of the two options - extending packages with custom objects.</span></span>  
  
 <span data-ttu-id="46f46-106">您的自訂 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 方案需要的彈性比指令碼工作和指令碼元件所提供的彈性還要大，或您需要可在多個封裝中重複使用的元件時，[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 物件模型可讓您從頭建立自訂工作、資料流程元件和 Managed 程式碼中的其他封裝物件。</span><span class="sxs-lookup"><span data-stu-id="46f46-106">When your custom [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] solution requires more flexibility than the Script task and the Script component provide, or when you need a component that you can reuse in multiple packages, the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] object model lets you build custom tasks, data flow components, and other package objects in managed code from the ground up.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="46f46-107">本節內容</span><span class="sxs-lookup"><span data-stu-id="46f46-107">In This Section</span></span>  
 [<span data-ttu-id="46f46-108">開發 Integration Services 的自訂物件</span><span class="sxs-lookup"><span data-stu-id="46f46-108">Developing Custom Objects for Integration Services</span></span>](developing-custom-objects-for-integration-services.md)  
 <span data-ttu-id="46f46-109">討論可以針對 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 建立的自訂物件以及摘要列出重要的步驟和設定。</span><span class="sxs-lookup"><span data-stu-id="46f46-109">Discusses the custom objects that can be created for [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], and summarizes the essential steps and settings.</span></span>  
  
 [<span data-ttu-id="46f46-110">保存自訂物件</span><span class="sxs-lookup"><span data-stu-id="46f46-110">Persisting Custom Objects</span></span>](persisting-custom-objects.md)  
 <span data-ttu-id="46f46-111">討論自訂物件的預設持續性及實作自訂持續性的程序。</span><span class="sxs-lookup"><span data-stu-id="46f46-111">Discusses the default persistence of custom objects, and the process of implementing custom persistence.</span></span>  
  
 [<span data-ttu-id="46f46-112">自訂物件的建立、部署和偵錯</span><span class="sxs-lookup"><span data-stu-id="46f46-112">Building, Deploying, and Debugging Custom Objects</span></span>](building-deploying-and-debugging-custom-objects.md)  
 <span data-ttu-id="46f46-113">討論建立、部署及測試各種類型之自訂物件的常用方法。</span><span class="sxs-lookup"><span data-stu-id="46f46-113">Discusses the common approaches to building, deploying and testing the various types of custom objects.</span></span>  
  
 [<span data-ttu-id="46f46-114">開發自訂工作</span><span class="sxs-lookup"><span data-stu-id="46f46-114">Developing a Custom Task</span></span>](task/developing-a-custom-task.md)  
 <span data-ttu-id="46f46-115">描述編寫自訂工作的程序。</span><span class="sxs-lookup"><span data-stu-id="46f46-115">Describes the process of coding a custom task.</span></span>  
  
 [<span data-ttu-id="46f46-116">開發自訂連線管理員</span><span class="sxs-lookup"><span data-stu-id="46f46-116">Developing a Custom Connection Manager</span></span>](connection-manager/developing-a-custom-connection-manager.md)  
 <span data-ttu-id="46f46-117">描述編寫自訂連接管理員的程序。</span><span class="sxs-lookup"><span data-stu-id="46f46-117">Describes the process of coding a custom connection manager.</span></span>  
  
 [<span data-ttu-id="46f46-118">開發自訂記錄提供者</span><span class="sxs-lookup"><span data-stu-id="46f46-118">Developing a Custom Log Provider</span></span>](log-provider/developing-a-custom-log-provider.md)  
 <span data-ttu-id="46f46-119">描述編寫自訂記錄提供者的程序。</span><span class="sxs-lookup"><span data-stu-id="46f46-119">Describes the process of coding a custom log provider.</span></span>  
  
 [<span data-ttu-id="46f46-120">開發自訂 Foreach 列舉程式</span><span class="sxs-lookup"><span data-stu-id="46f46-120">Developing a Custom ForEach Enumerator</span></span>](foreach-enumerator/developing-a-custom-foreach-enumerator.md)  
 <span data-ttu-id="46f46-121">描述編寫自訂列舉值的程序。</span><span class="sxs-lookup"><span data-stu-id="46f46-121">Describes the process of coding a custom enumerator.</span></span>  
  
 [<span data-ttu-id="46f46-122">開發自訂資料流程元件</span><span class="sxs-lookup"><span data-stu-id="46f46-122">Developing a Custom Data Flow Component</span></span>](data-flow/developing-a-custom-data-flow-component.md)  
 <span data-ttu-id="46f46-123">討論如何進行自訂資料流程來源、轉換和目的地的程式設計。</span><span class="sxs-lookup"><span data-stu-id="46f46-123">Discusses how to program custom data flow sources, transformations, and destinations.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="46f46-124">參考</span><span class="sxs-lookup"><span data-stu-id="46f46-124">Reference</span></span>  
 [<span data-ttu-id="46f46-125">Integration Services 錯誤和訊息參考</span><span class="sxs-lookup"><span data-stu-id="46f46-125">Integration Services Error and Message Reference</span></span>](../integration-services-error-and-message-reference.md)  
 <span data-ttu-id="46f46-126">列出預先定義的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 錯誤碼，以及其符號名稱與描述。</span><span class="sxs-lookup"><span data-stu-id="46f46-126">Lists the predefined [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] error codes with their symbolic names and descriptions.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="46f46-127">相關章節</span><span class="sxs-lookup"><span data-stu-id="46f46-127">Related Sections</span></span>  
 [<span data-ttu-id="46f46-128">使用指令碼擴充套件</span><span class="sxs-lookup"><span data-stu-id="46f46-128">Extending Packages with Scripting</span></span>](../extending-packages-scripting/extending-packages-with-scripting.md)  
 <span data-ttu-id="46f46-129">討論如何使用指令碼工作來擴充控制流程，或是如何使用指令碼元件來擴充資料流程。</span><span class="sxs-lookup"><span data-stu-id="46f46-129">Discusses how to extend the control flow by using the Script task, or extend the data flow by using the Script component.</span></span>  
  
 [<span data-ttu-id="46f46-130">以程式設計方式建置套件</span><span class="sxs-lookup"><span data-stu-id="46f46-130">Building Packages Programmatically</span></span>](../building-packages-programmatically/building-packages-programmatically.md)  
 <span data-ttu-id="46f46-131">描述如何以程式設計方式建立、設定、執行、載入、儲存和管理 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 封裝。</span><span class="sxs-lookup"><span data-stu-id="46f46-131">Describes how to create, configure, run, load, save, and manage [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages programmatically.</span></span>  
  
<span data-ttu-id="46f46-132">![Integration Services 圖示 (小型) ](../media/dts-16.gif "Integration Services 圖示 (小)")會**保持最**新狀態 Integration Services  </span><span class="sxs-lookup"><span data-stu-id="46f46-132">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="46f46-133">若要取得 Microsoft 的最新下載、文件、範例和影片以及社群中的精選解決方案，請瀏覽 MSDN 上的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 頁面：</span><span class="sxs-lookup"><span data-stu-id="46f46-133">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="46f46-134">瀏覽 MSDN 上的 Integration Services 頁面</span><span class="sxs-lookup"><span data-stu-id="46f46-134">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="46f46-135">若要得到這些更新的自動通知，請訂閱該頁面上所提供的 RSS 摘要。</span><span class="sxs-lookup"><span data-stu-id="46f46-135">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46f46-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="46f46-136">See Also</span></span>  
 <span data-ttu-id="46f46-137">[比較腳本解決方案和自訂物件](../extending-packages-scripting/comparing-scripting-solutions-and-custom-objects.md) </span><span class="sxs-lookup"><span data-stu-id="46f46-137">[Comparing Scripting Solutions and Custom Objects](../extending-packages-scripting/comparing-scripting-solutions-and-custom-objects.md) </span></span>  
 [<span data-ttu-id="46f46-138">SQL Server Integration Services</span><span class="sxs-lookup"><span data-stu-id="46f46-138">SQL Server Integration Services</span></span>](../sql-server-integration-services.md)  
  
  
