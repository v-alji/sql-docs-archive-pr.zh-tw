---
title: 開發自訂工作 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom tasks [Integration Services], about custom tasks
- Task class
- custom tasks [Integration Services]
- SSIS custom tasks
- SSIS custom tasks, about custom tasks
- IDtsTaskUI interface
- DtsTaskAttribute attribute
- tasks [Integration Services], custom
- TaskHost object
ms.assetid: dcbd8615-fa6d-4ddb-b8a5-0b19dddd6239
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d9d3446acff7ced73ab47014bec51708dba225b6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597959"
---
# <a name="developing-a-custom-task"></a><span data-ttu-id="c797e-102">開發自訂工作</span><span class="sxs-lookup"><span data-stu-id="c797e-102">Developing a Custom Task</span></span>
  [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] <span data-ttu-id="c797e-103">利用工作執行工作單位，以支援擷取、轉換及載入資料。</span><span class="sxs-lookup"><span data-stu-id="c797e-103">uses tasks to perform units of work in support of the extraction, transformation, and loading of data.</span></span> [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] <span data-ttu-id="c797e-104">包含各種可以執行最常使用之動作的工作，包括執行 SQL 陳述式、從 FTP 站台下載檔案等。</span><span class="sxs-lookup"><span data-stu-id="c797e-104">includes a variety of tasks that perform the most frequently used actions, from executing an SQL statement to downloading a file from an FTP site.</span></span> <span data-ttu-id="c797e-105">如果包含的工作與支援的動作未完全符合您的需求，可以建立自訂工作。</span><span class="sxs-lookup"><span data-stu-id="c797e-105">If the included tasks and supported actions do not completely meet your requirements, you can create a custom task.</span></span>  
  
 <span data-ttu-id="c797e-106">若要建立自訂工作，您必須建立繼承自 [Microsoft.SqlServer.Dts.Runtime.Task](/dotnet/api/microsoft.sqlserver.dts.runtime.task) 基底類別的類別、將 <xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute> 屬性 (Attribute) 套用至新類別，以及覆寫基底類別的重要方法與屬性 (Property)，包括 <xref:Microsoft.SqlServer.Dts.Runtime.Task.Execute%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="c797e-106">To create a custom task, you have to create a class that inherits from the [Microsoft.SqlServer.Dts.Runtime.Task](/dotnet/api/microsoft.sqlserver.dts.runtime.task) base class, apply the <xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute> attribute to your new class, and override the important methods and properties of the base class, including the <xref:Microsoft.SqlServer.Dts.Runtime.Task.Execute%2A> method.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c797e-107">本節內容</span><span class="sxs-lookup"><span data-stu-id="c797e-107">In This Section</span></span>  
 <span data-ttu-id="c797e-108">本章節描述如何建立和設定自訂工作及其選用自訂使用者介面，以及如何撰寫它們的程式碼。</span><span class="sxs-lookup"><span data-stu-id="c797e-108">This section describes how to create, configure, and code a custom task and its optional custom user interface.</span></span>  
  
 [<span data-ttu-id="c797e-109">建立自訂工作</span><span class="sxs-lookup"><span data-stu-id="c797e-109">Creating a Custom Task</span></span>](creating-a-custom-task.md)  
 <span data-ttu-id="c797e-110">描述第一個步驟：建立自訂工作。</span><span class="sxs-lookup"><span data-stu-id="c797e-110">Describes the first step, which is creating the custom task.</span></span>  
  
 [<span data-ttu-id="c797e-111">撰寫自訂工作的程式碼</span><span class="sxs-lookup"><span data-stu-id="c797e-111">Coding a Custom Task</span></span>](coding-a-custom-task.md)  
 <span data-ttu-id="c797e-112">描述如何撰寫自訂工作之主要方法的程式碼。</span><span class="sxs-lookup"><span data-stu-id="c797e-112">Describes how to code the principal methods of a custom task.</span></span>  
  
 [<span data-ttu-id="c797e-113">在自訂工作中連線至資料來源</span><span class="sxs-lookup"><span data-stu-id="c797e-113">Connecting to Data Sources in a Custom Task</span></span>](connecting-to-data-sources-in-a-custom-task.md)  
 <span data-ttu-id="c797e-114">描述如何將自訂工作連接到資料來源。</span><span class="sxs-lookup"><span data-stu-id="c797e-114">Describes how to connect a custom task to a data source.</span></span>  
  
 [<span data-ttu-id="c797e-115">在自訂工作中引發和定義事件</span><span class="sxs-lookup"><span data-stu-id="c797e-115">Raising and Defining Events in a Custom Task</span></span>](raising-and-defining-events-in-a-custom-task.md)  
 <span data-ttu-id="c797e-116">描述如何引發事件並從自訂工作定義自訂事件。</span><span class="sxs-lookup"><span data-stu-id="c797e-116">Describes how to raise events and define custom events from the custom task.</span></span>  
  
 [<span data-ttu-id="c797e-117">在自訂工作中為偵錯新增支援</span><span class="sxs-lookup"><span data-stu-id="c797e-117">Adding Support for Debugging in a Custom Task</span></span>](adding-support-for-debugging-in-a-custom-task.md)  
 <span data-ttu-id="c797e-118">描述如何在自訂工作中建立中斷點目標。</span><span class="sxs-lookup"><span data-stu-id="c797e-118">Describes how to create breakpoint targets in the custom task.</span></span>  
  
 [<span data-ttu-id="c797e-119">開發自訂工作的使用者介面</span><span class="sxs-lookup"><span data-stu-id="c797e-119">Developing a User Interface for a Custom Task</span></span>](developing-a-user-interface-for-a-custom-task.md)  
 <span data-ttu-id="c797e-120">描述如何建立顯示在 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 設計師中的使用者介面，以便在自訂工作上設定屬性。</span><span class="sxs-lookup"><span data-stu-id="c797e-120">Describes how to create a user interface that shows in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer to configure properties on the custom task.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="c797e-121">相關章節</span><span class="sxs-lookup"><span data-stu-id="c797e-121">Related Sections</span></span>  
  
### <a name="information-common-to-all-custom-objects"></a><span data-ttu-id="c797e-122">自訂物件的共通資訊</span><span class="sxs-lookup"><span data-stu-id="c797e-122">Information Common to all Custom Objects</span></span>  
 <span data-ttu-id="c797e-123">如需有關 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 中可以建立之所有類型自訂物件適用的共通資訊，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="c797e-123">For information that is common to all the type of custom objects that you can create in [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)], see the following topics:</span></span>  
  
 [<span data-ttu-id="c797e-124">開發 Integration Services 的自訂物件</span><span class="sxs-lookup"><span data-stu-id="c797e-124">Developing Custom Objects for Integration Services</span></span>](../developing-custom-objects-for-integration-services.md)  
 <span data-ttu-id="c797e-125">描述為 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 實作所有種類的自訂物件之基本步驟。</span><span class="sxs-lookup"><span data-stu-id="c797e-125">Describes the basic steps in implementing all kinds of custom objects for [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)].</span></span>  
  
 [<span data-ttu-id="c797e-126">保存自訂物件</span><span class="sxs-lookup"><span data-stu-id="c797e-126">Persisting Custom Objects</span></span>](../persisting-custom-objects.md)  
 <span data-ttu-id="c797e-127">描述自訂的持續性並解釋必須實作它的時機。</span><span class="sxs-lookup"><span data-stu-id="c797e-127">Describes custom persistence and explains when it is necessary.</span></span>  
  
 [<span data-ttu-id="c797e-128">自訂物件的建立、部署和偵錯</span><span class="sxs-lookup"><span data-stu-id="c797e-128">Building, Deploying, and Debugging Custom Objects</span></span>](../building-deploying-and-debugging-custom-objects.md)  
 <span data-ttu-id="c797e-129">描述建立、簽署、部署和偵錯自訂物件的技術。</span><span class="sxs-lookup"><span data-stu-id="c797e-129">Describes the techniques for building, signing, deploying, and debugging custom objects.</span></span>  
  
### <a name="information-about-other-custom-objects"></a><span data-ttu-id="c797e-130">其他自訂物件的相關資訊</span><span class="sxs-lookup"><span data-stu-id="c797e-130">Information about Other Custom Objects</span></span>  
 <span data-ttu-id="c797e-131">如需有關在 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 中可以建立之其他類型自訂物件的詳細資訊，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="c797e-131">For information about the other types of custom objects that you can create in [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)], see the following topics:</span></span>  
  
 [<span data-ttu-id="c797e-132">開發自訂連線管理員</span><span class="sxs-lookup"><span data-stu-id="c797e-132">Developing a Custom Connection Manager</span></span>](../connection-manager/developing-a-custom-connection-manager.md)  
 <span data-ttu-id="c797e-133">討論如何進行自訂連接管理員的程式設計。</span><span class="sxs-lookup"><span data-stu-id="c797e-133">Discusses how to program custom connection managers.</span></span>  
  
 [<span data-ttu-id="c797e-134">開發自訂記錄提供者</span><span class="sxs-lookup"><span data-stu-id="c797e-134">Developing a Custom Log Provider</span></span>](../log-provider/developing-a-custom-log-provider.md)  
 <span data-ttu-id="c797e-135">討論如何進行自訂記錄提供者的程式設計。</span><span class="sxs-lookup"><span data-stu-id="c797e-135">Discusses how to program custom log providers.</span></span>  
  
 [<span data-ttu-id="c797e-136">開發自訂 Foreach 列舉程式</span><span class="sxs-lookup"><span data-stu-id="c797e-136">Developing a Custom ForEach Enumerator</span></span>](../foreach-enumerator/developing-a-custom-foreach-enumerator.md)  
 <span data-ttu-id="c797e-137">討論如何進行自訂列舉值的程式設計。</span><span class="sxs-lookup"><span data-stu-id="c797e-137">Discusses how to program custom enumerators.</span></span>  
  
 [<span data-ttu-id="c797e-138">開發自訂資料流程元件</span><span class="sxs-lookup"><span data-stu-id="c797e-138">Developing a Custom Data Flow Component</span></span>](../data-flow/developing-a-custom-data-flow-component.md)  
 <span data-ttu-id="c797e-139">討論如何進行自訂資料流程來源、轉換和目的地的程式設計。</span><span class="sxs-lookup"><span data-stu-id="c797e-139">Discusses how to program custom data flow sources, transformations, and destinations.</span></span>  
  
<span data-ttu-id="c797e-140">![Integration Services 圖示 (小型) ](../../media/dts-16.gif "Integration Services 圖示 (小)")會**保持最**新狀態 Integration Services  </span><span class="sxs-lookup"><span data-stu-id="c797e-140">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="c797e-141">若要取得 Microsoft 的最新下載、文件、範例和影片以及社群中的精選解決方案，請瀏覽 MSDN 上的 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 頁面：</span><span class="sxs-lookup"><span data-stu-id="c797e-141">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="c797e-142">瀏覽 MSDN 上的 Integration Services 頁面</span><span class="sxs-lookup"><span data-stu-id="c797e-142">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="c797e-143">若要得到這些更新的自動通知，請訂閱該頁面上所提供的 RSS 摘要。</span><span class="sxs-lookup"><span data-stu-id="c797e-143">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c797e-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c797e-144">See Also</span></span>  
 <span data-ttu-id="c797e-145">[以指令碼工作擴充套件](../../extending-packages-scripting/task/extending-the-package-with-the-script-task.md) </span><span class="sxs-lookup"><span data-stu-id="c797e-145">[Extending the Package with the Script Task](../../extending-packages-scripting/task/extending-the-package-with-the-script-task.md) </span></span>  
 [<span data-ttu-id="c797e-146">比較指令碼解決方案和自訂物件</span><span class="sxs-lookup"><span data-stu-id="c797e-146">Comparing Scripting Solutions and Custom Objects</span></span>](../../extending-packages-scripting/comparing-scripting-solutions-and-custom-objects.md)  
  
  
