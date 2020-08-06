---
title: 開發自訂資料流程元件 | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data flow task [Integration Services], extending
- data flow [Integration Services], extending
- extending data flow task [Integration Services]
- components [Integration Services], data flow
ms.assetid: be126913-2a9a-41c9-9bf5-a7b0a0aea2f8
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7126129ede3f419c6fbdcae6245a47636e6e65ed
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703210"
---
# <a name="developing-a-custom-data-flow-component"></a><span data-ttu-id="beba0-102">開發自訂資料流程元件</span><span class="sxs-lookup"><span data-stu-id="beba0-102">Developing a Custom Data Flow Component</span></span>
  <span data-ttu-id="beba0-103">資料流程工作是由連接至各種資料來源然後以高速轉換和路由資料的元件組成。</span><span class="sxs-lookup"><span data-stu-id="beba0-103">The data flow task consists of components that connect to a variety of data sources and then transform and route that data at high speed.</span></span> [!INCLUDE[msCoName](../../../includes/msconame-md.md)] <span data-ttu-id="beba0-104">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 所提供可延伸物件模型可讓開發人員建立可在 [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] 及已部署套件中使用的自訂來源、轉換和目的地。</span><span class="sxs-lookup"><span data-stu-id="beba0-104">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] provides an extensible object model that lets developers create custom sources, transformations, and destinations that you can use in [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] and in deployed packages.</span></span> <span data-ttu-id="beba0-105">本章節包含將引導您開發自訂資料流程元件的主題。</span><span class="sxs-lookup"><span data-stu-id="beba0-105">This section contains topics that will guide you in developing custom data flow components.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="beba0-106">本節內容</span><span class="sxs-lookup"><span data-stu-id="beba0-106">In This Section</span></span>
 <span data-ttu-id="beba0-107">[建立自訂資料流程元件](creating-a-custom-data-flow-component.md)描述建立自訂資料流程元件的初始步驟。</span><span class="sxs-lookup"><span data-stu-id="beba0-107">[Creating a Custom Data Flow Component](creating-a-custom-data-flow-component.md) Describes the initial steps in creating a custom data flow component.</span></span>

 <span data-ttu-id="beba0-108">[資料流程元件的設計階段方法](design-time-methods-of-a-data-flow-component.md)描述要在自訂資料流程元件中執行的設計階段方法。</span><span class="sxs-lookup"><span data-stu-id="beba0-108">[Design-time Methods of a Data Flow Component](design-time-methods-of-a-data-flow-component.md) Describes the design-time methods to implement in a custom data flow component.</span></span>

 <span data-ttu-id="beba0-109">[資料流程元件的執行時間方法](run-time-methods-of-a-data-flow-component.md)描述要在自訂資料流程元件中執行的執行時間方法。</span><span class="sxs-lookup"><span data-stu-id="beba0-109">[Run-time Methods of a Data Flow Component](run-time-methods-of-a-data-flow-component.md) Describes the run-time methods to implement in a custom data flow component.</span></span>

 <span data-ttu-id="beba0-110">[執行計畫和緩衝區配置](execution-plan-and-buffer-allocation.md)說明資料流程執行計畫和資料緩衝區的配置。</span><span class="sxs-lookup"><span data-stu-id="beba0-110">[Execution Plan and Buffer Allocation](execution-plan-and-buffer-allocation.md) Describes the data flow execution plan and the allocation of data buffers.</span></span>

 <span data-ttu-id="beba0-111">[使用資料流程中的資料類型](working-with-data-types-in-the-data-flow.md)說明資料流程如何將 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 資料類型對應到 .NET Framework 的 managed 資料類型。</span><span class="sxs-lookup"><span data-stu-id="beba0-111">[Working with Data Types in the Data Flow](working-with-data-types-in-the-data-flow.md) Explains how the data flow maps [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] data types to .NET Framework managed data types.</span></span>

 <span data-ttu-id="beba0-112">[驗證資料流程元件](validating-a-data-flow-component.md)說明用來驗證元件設定以及重新設定元件中繼資料的方法。</span><span class="sxs-lookup"><span data-stu-id="beba0-112">[Validating a Data Flow Component](validating-a-data-flow-component.md) Explains the methods used to validate component configuration and to reconfigure component metadata.</span></span>

 <span data-ttu-id="beba0-113">[執行外部中繼資料](implementing-external-metadata.md)說明如何使用外部中繼資料行進行資料驗證。</span><span class="sxs-lookup"><span data-stu-id="beba0-113">[Implementing External Metadata](implementing-external-metadata.md) Explains how to use external metadata columns for data validation.</span></span>

 <span data-ttu-id="beba0-114">[在資料流程元件中引發和定義事件](raising-and-defining-events-in-a-data-flow-component.md)說明如何引發預先定義和自訂的事件。</span><span class="sxs-lookup"><span data-stu-id="beba0-114">[Raising and Defining Events in a Data Flow Component](raising-and-defining-events-in-a-data-flow-component.md) Explains how to raise predefined and custom events.</span></span>

 <span data-ttu-id="beba0-115">[在資料流程元件中記錄和定義記錄專案](logging-and-defining-log-entries-in-a-data-flow-component.md)說明如何建立和寫入自訂記錄專案。</span><span class="sxs-lookup"><span data-stu-id="beba0-115">[Logging and Defining Log Entries in a Data Flow Component](logging-and-defining-log-entries-in-a-data-flow-component.md) Explains how to create and write to custom log entries.</span></span>

 <span data-ttu-id="beba0-116">[在資料流程元件中使用錯誤輸出](using-error-outputs-in-a-data-flow-component.md)說明如何將錯誤資料列重新導向至替代輸出。</span><span class="sxs-lookup"><span data-stu-id="beba0-116">[Using Error Outputs in a Data Flow Component](using-error-outputs-in-a-data-flow-component.md) Explains how to redirect error rows to an alternative output.</span></span>

 <span data-ttu-id="beba0-117">[升級資料流程元件的版本](upgrading-the-version-of-a-data-flow-component.md)說明當第一次使用元件的新版本時，如何更新已儲存的元件中繼資料。</span><span class="sxs-lookup"><span data-stu-id="beba0-117">[Upgrading the Version of a Data Flow Component](upgrading-the-version-of-a-data-flow-component.md) Explains how to update saved component metadata when a new version of your component is first used.</span></span>

 <span data-ttu-id="beba0-118">[開發資料流程元件的使用者介面](developing-a-user-interface-for-a-data-flow-component.md)說明如何執行元件的自訂編輯器。</span><span class="sxs-lookup"><span data-stu-id="beba0-118">[Developing a User Interface for a Data Flow Component](developing-a-user-interface-for-a-data-flow-component.md) Explains how to implement a custom editor for a component.</span></span>

 <span data-ttu-id="beba0-119">[開發特定類型的資料流程元件](../../extending-packages-custom-objects-data-flow-types/developing-specific-types-of-data-flow-components.md)包含開發三種資料流程元件類型的相關資訊：來源、轉換和目的地。</span><span class="sxs-lookup"><span data-stu-id="beba0-119">[Developing Specific Types of Data Flow Components](../../extending-packages-custom-objects-data-flow-types/developing-specific-types-of-data-flow-components.md) Contains information about developing the three types of data flow components: sources, transformations, and destinations.</span></span>

## <a name="reference"></a><span data-ttu-id="beba0-120">參考</span><span class="sxs-lookup"><span data-stu-id="beba0-120">Reference</span></span>
 <span data-ttu-id="beba0-121"><xref:Microsoft.SqlServer.Dts.Pipeline>包含用來建立自訂資料流程元件的類別和介面。</span><span class="sxs-lookup"><span data-stu-id="beba0-121"><xref:Microsoft.SqlServer.Dts.Pipeline> Contains the classes and interfaces used to create custom data flow components.</span></span>

 <span data-ttu-id="beba0-122"><xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper>包含組成「資料流程」工作物件模型的類別和介面，可用來建立自訂資料流程元件或建立「資料流程」工作。</span><span class="sxs-lookup"><span data-stu-id="beba0-122"><xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper> Contains the classes and interfaces that make up the data flow task object model, and is used to create custom data flow components or build a data flow task.</span></span>

 <span data-ttu-id="beba0-123"><xref:Microsoft.SqlServer.Dts.Pipeline.Design>包含用來建立資料流程元件之使用者介面的類別和介面。</span><span class="sxs-lookup"><span data-stu-id="beba0-123"><xref:Microsoft.SqlServer.Dts.Pipeline.Design> Contains the classes and interfaces used to create the user interface for data flow components.</span></span>

 <span data-ttu-id="beba0-124">[Integration Services 錯誤和訊息參考](../../integration-services-error-and-message-reference.md)列出預先定義的 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 錯誤碼及其符號名稱和描述。</span><span class="sxs-lookup"><span data-stu-id="beba0-124">[Integration Services Error and Message Reference](../../integration-services-error-and-message-reference.md) Lists the predefined [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] error codes with their symbolic names and descriptions.</span></span>

## <a name="related-sections"></a><span data-ttu-id="beba0-125">相關章節</span><span class="sxs-lookup"><span data-stu-id="beba0-125">Related Sections</span></span>

### <a name="information-common-to-all-custom-objects"></a><span data-ttu-id="beba0-126">所有自訂物件的共通資訊</span><span class="sxs-lookup"><span data-stu-id="beba0-126">Information Common to All Custom Objects</span></span>
 <span data-ttu-id="beba0-127">如需有關 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 中可以建立之所有類型自訂物件適用的共通資訊，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="beba0-127">For information that is common to all the type of custom objects that you can create in [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)], see the following topics:</span></span>

 <span data-ttu-id="beba0-128">[開發 Integration Services 的自訂物件](../../extending-packages-custom-objects/developing-custom-objects-for-integration-services.md)說明為執行所有類型之自訂物件的基本步驟 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="beba0-128">[Developing Custom Objects for Integration Services](../../extending-packages-custom-objects/developing-custom-objects-for-integration-services.md) Describes the basic steps in implementing all types of custom objects for [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)].</span></span>

 <span data-ttu-id="beba0-129">[保存自訂物件](../../extending-packages-custom-objects/persisting-custom-objects.md)描述自訂持續性，並在必要時加以說明。</span><span class="sxs-lookup"><span data-stu-id="beba0-129">[Persisting Custom Objects](../../extending-packages-custom-objects/persisting-custom-objects.md) Describes custom persistence and explains when it is necessary.</span></span>

 <span data-ttu-id="beba0-130">[建立、部署和調試自訂物件](../../extending-packages-custom-objects/building-deploying-and-debugging-custom-objects.md)說明建立、簽署、部署和偵錯工具自訂物件的技術。</span><span class="sxs-lookup"><span data-stu-id="beba0-130">[Building, Deploying, and Debugging Custom Objects](../../extending-packages-custom-objects/building-deploying-and-debugging-custom-objects.md) Describes the techniques for building, signing, deploying, and debugging custom objects.</span></span>

### <a name="information-about-other-custom-objects"></a><span data-ttu-id="beba0-131">其他自訂物件的相關資訊</span><span class="sxs-lookup"><span data-stu-id="beba0-131">Information about Other Custom Objects</span></span>
 <span data-ttu-id="beba0-132">如需有關在 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 中可以建立之其他類型自訂物件的詳細資訊，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="beba0-132">For information on the other types of custom objects that you can create in [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)], see the following topics:</span></span>

 <span data-ttu-id="beba0-133">[開發自訂工作](../../extending-packages-custom-objects/task/developing-a-custom-task.md)討論如何編寫自訂工作的程式。</span><span class="sxs-lookup"><span data-stu-id="beba0-133">[Developing a Custom Task](../../extending-packages-custom-objects/task/developing-a-custom-task.md) Discusses how to program custom tasks.</span></span>

 <span data-ttu-id="beba0-134">[開發自訂連線管理員](../../extending-packages-custom-objects/connection-manager/developing-a-custom-connection-manager.md)討論如何編寫自訂連接管理員的程式。</span><span class="sxs-lookup"><span data-stu-id="beba0-134">[Developing a Custom Connection Manager](../../extending-packages-custom-objects/connection-manager/developing-a-custom-connection-manager.md) Discusses how to program custom connection managers.</span></span>

 <span data-ttu-id="beba0-135">[開發自訂記錄提供者](../../extending-packages-custom-objects/log-provider/developing-a-custom-log-provider.md)討論如何編寫自訂記錄提供者的程式。</span><span class="sxs-lookup"><span data-stu-id="beba0-135">[Developing a Custom Log Provider](../../extending-packages-custom-objects/log-provider/developing-a-custom-log-provider.md) Discusses how to program custom log providers.</span></span>

 <span data-ttu-id="beba0-136">[開發自訂 ForEach 列舉](../../extending-packages-custom-objects/foreach-enumerator/developing-a-custom-foreach-enumerator.md)值討論如何編寫自訂枚舉器的程式。</span><span class="sxs-lookup"><span data-stu-id="beba0-136">[Developing a Custom ForEach Enumerator](../../extending-packages-custom-objects/foreach-enumerator/developing-a-custom-foreach-enumerator.md) Discusses how to program custom enumerators.</span></span>

<span data-ttu-id="beba0-137">![Integration Services 圖示 (小型) ](../../media/dts-16.gif "Integration Services 圖示 (小)")會**保持最**新狀態 Integration Services  </span><span class="sxs-lookup"><span data-stu-id="beba0-137">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="beba0-138">若要取得 Microsoft 的最新下載、文件、範例和影片以及社群中的精選解決方案，請瀏覽 MSDN 上的 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 頁面：</span><span class="sxs-lookup"><span data-stu-id="beba0-138">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="beba0-139">瀏覽 MSDN 上的 Integration Services 頁面</span><span class="sxs-lookup"><span data-stu-id="beba0-139">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="beba0-140">若要得到這些更新的自動通知，請訂閱該頁面上所提供的 RSS 摘要。</span><span class="sxs-lookup"><span data-stu-id="beba0-140">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>

## <a name="see-also"></a><span data-ttu-id="beba0-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="beba0-141">See Also</span></span>
 <span data-ttu-id="beba0-142">[以腳本元件擴充資料流程] (.。/..[比較腳本解決方案和自訂物件的](../../extending-packages-scripting/comparing-scripting-solutions-and-custom-objects.md)/extending-packages-scripting/data-flow-script-component/extending-the-data-flow-with-the-script-component.md</span><span class="sxs-lookup"><span data-stu-id="beba0-142">[Extending the Data Flow with the Script Component](../../extending-packages-scripting/data-flow-script-component/extending-the-data-flow-with-the-script-component.md [Comparing Scripting Solutions and Custom Objects](../../extending-packages-scripting/comparing-scripting-solutions-and-custom-objects.md)</span></span>


