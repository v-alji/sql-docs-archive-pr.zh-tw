---
title: 在指令碼元件中引發事件 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- Script component [Integration Services], raising events
ms.assetid: bb389073-e1d0-4794-8d29-c8b293b6a5e3
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 78eb44239f4e58e43bdd65c41d5fdeb58d053a6c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597207"
---
# <a name="raising-events-in-the-script-component"></a><span data-ttu-id="80eb9-102">在指令碼元件中引發事件</span><span class="sxs-lookup"><span data-stu-id="80eb9-102">Raising Events in the Script Component</span></span>
  <span data-ttu-id="80eb9-103">事件會提供向包含封裝報告錯誤、警告和其他資訊 (例如工作進度或狀態) 的方法。</span><span class="sxs-lookup"><span data-stu-id="80eb9-103">Events provide a way to report errors, warnings, and other information, such as task progress or status, to the containing package.</span></span> <span data-ttu-id="80eb9-104">封裝提供管理事件通知的事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="80eb9-104">The package provides event handlers for managing event notifications.</span></span> <span data-ttu-id="80eb9-105">指令碼元件可以呼叫 `ScriptMain` 類別的 <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.ComponentMetaData%2A> 屬性上之方法以引發事件。</span><span class="sxs-lookup"><span data-stu-id="80eb9-105">The Script component can raise events by calling methods on the <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.ComponentMetaData%2A> property of the `ScriptMain` class.</span></span> <span data-ttu-id="80eb9-106">如需 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 套件如何處理事件的詳細資訊，請參閱 [Integration Services &#40;SSIS&#41; 事件處理常式](../../integration-services-ssis-event-handlers.md)。</span><span class="sxs-lookup"><span data-stu-id="80eb9-106">For more information about how [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] packages handle events, see [Integration Services &#40;SSIS&#41; Event Handlers](../../integration-services-ssis-event-handlers.md).</span></span>  
  
 <span data-ttu-id="80eb9-107">事件可以記錄到封裝中啟用的任何記錄提供者。</span><span class="sxs-lookup"><span data-stu-id="80eb9-107">Events can be logged to any log provider that is enabled in the package.</span></span> <span data-ttu-id="80eb9-108">記錄提供者會在資料存放區中儲存事件的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="80eb9-108">Log providers store information about events in a data store.</span></span> <span data-ttu-id="80eb9-109">指令碼元件也可以使用 <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.Log%2A> 方法將資訊記錄到記錄提供者，而不會引發事件。</span><span class="sxs-lookup"><span data-stu-id="80eb9-109">The Script component can also use the <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.Log%2A> method to log information to a log provider without raising an event.</span></span> <span data-ttu-id="80eb9-110">如需有關如何使用 <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.Log%2A> 方法的詳細資訊，請參閱下一節。</span><span class="sxs-lookup"><span data-stu-id="80eb9-110">For more information about how to use the <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.Log%2A> method, see the following section.</span></span>  
  
 <span data-ttu-id="80eb9-111">為了引發事件，指令碼工作會呼叫 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100> 屬性公開的 <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.ComponentMetaData%2A> 介面之下列其中一個方法：</span><span class="sxs-lookup"><span data-stu-id="80eb9-111">To raise an event, the Script task calls one of the following methods of the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100> interface exposed by the <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.ComponentMetaData%2A> property:</span></span>  
  
|<span data-ttu-id="80eb9-112">事件</span><span class="sxs-lookup"><span data-stu-id="80eb9-112">Event</span></span>|<span data-ttu-id="80eb9-113">描述</span><span class="sxs-lookup"><span data-stu-id="80eb9-113">Description</span></span>|  
|-----------|-----------------|  
|<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.FireCustomEvent%2A>|<span data-ttu-id="80eb9-114">引發封裝中使用者定義的自訂事件。</span><span class="sxs-lookup"><span data-stu-id="80eb9-114">Raises a user-defined custom event in the package.</span></span>|  
|<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.FireError%2A>|<span data-ttu-id="80eb9-115">通知封裝有關錯誤狀況。</span><span class="sxs-lookup"><span data-stu-id="80eb9-115">Informs the package of an error condition.</span></span>|  
|<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.FireInformation%2A>|<span data-ttu-id="80eb9-116">提供資訊給使用者。</span><span class="sxs-lookup"><span data-stu-id="80eb9-116">Provides information to the user.</span></span>|  
|<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.FireProgress%2A>|<span data-ttu-id="80eb9-117">通知封裝有關元件的進度。</span><span class="sxs-lookup"><span data-stu-id="80eb9-117">Informs the package of the progress of the component.</span></span>|  
|<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.FireWarning%2A>|<span data-ttu-id="80eb9-118">通知封裝元件是在需要使用者通知的狀態，但不是錯誤狀況。</span><span class="sxs-lookup"><span data-stu-id="80eb9-118">Informs the package that the component is in a state that warrants user notification, but is not an error condition.</span></span>|  
  
 <span data-ttu-id="80eb9-119">以下是引發 Error 事件的簡單範例：</span><span class="sxs-lookup"><span data-stu-id="80eb9-119">Here is a simple example of raising an Error event:</span></span>  
  
 `Dim myMetadata as IDTSComponentMetaData100`  
  
 `myMetaData = Me.ComponentMetaData`  
  
 `myMetaData.FireError(...)`  
  
<span data-ttu-id="80eb9-120">![Integration Services 圖示 (小型) ](../../media/dts-16.gif "Integration Services 圖示 (小)")會**保持最**新狀態 Integration Services  </span><span class="sxs-lookup"><span data-stu-id="80eb9-120">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="80eb9-121">若要取得 Microsoft 的最新下載、文件、範例和影片以及社群中的精選解決方案，請瀏覽 MSDN 上的 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 頁面：</span><span class="sxs-lookup"><span data-stu-id="80eb9-121">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="80eb9-122">瀏覽 MSDN 上的 Integration Services 頁面</span><span class="sxs-lookup"><span data-stu-id="80eb9-122">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="80eb9-123">若要得到這些更新的自動通知，請訂閱該頁面上所提供的 RSS 摘要。</span><span class="sxs-lookup"><span data-stu-id="80eb9-123">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80eb9-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="80eb9-124">See Also</span></span>  
 <span data-ttu-id="80eb9-125">[Integration Services &#40;SSIS&#41; 事件處理常式](../../integration-services-ssis-event-handlers.md) </span><span class="sxs-lookup"><span data-stu-id="80eb9-125">[Integration Services &#40;SSIS&#41; Event Handlers](../../integration-services-ssis-event-handlers.md) </span></span>  
 [<span data-ttu-id="80eb9-126">將事件處理常式新增至套件</span><span class="sxs-lookup"><span data-stu-id="80eb9-126">Add an Event Handler to a Package</span></span>](../../add-an-event-handler-to-a-package.md)  
  
  
