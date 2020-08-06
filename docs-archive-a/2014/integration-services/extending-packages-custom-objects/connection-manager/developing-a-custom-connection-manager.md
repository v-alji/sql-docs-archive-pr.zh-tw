---
title: 開發自訂連線管理員 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- packages [Integration Services], connections
- custom connection managers [Integration Services], about custom connection managers
- connection managers [Integration Services], custom
- Integration Services packages, connection managers
- SSIS packages, connection managers
- SQL Server Integration Services packages, connection managers
- custom connection managers [Integration Services]
ms.assetid: bda0b29e-57f5-4879-b04d-1396dc56daa8
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 19c5a9066db6542742537a41a7f567d1b4b1d23d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709765"
---
# <a name="developing-a-custom-connection-manager"></a><span data-ttu-id="9bd6f-102">開發自訂連接管理員</span><span class="sxs-lookup"><span data-stu-id="9bd6f-102">Developing a Custom Connection Manager</span></span>
  [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] <span data-ttu-id="9bd6f-103">會使用連接管理員封裝連接至外部資料來源所需的資訊。</span><span class="sxs-lookup"><span data-stu-id="9bd6f-103">uses connection managers to encapsulate the information needed to connect to an external data source.</span></span> [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] <span data-ttu-id="9bd6f-104">包含各種連接管理員，可以連接到最常使用的資料來源，包括企業資料庫、文字檔案與 Excel 工作表等。</span><span class="sxs-lookup"><span data-stu-id="9bd6f-104">includes a variety of connection managers that support connections to the most commonly used data sources, from enterprise databases to text files and Excel worksheets.</span></span> <span data-ttu-id="9bd6f-105">如果 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 支援的連接管理員和外部資料來源無法完全符合您的需求，可以建立自訂連接管理員。</span><span class="sxs-lookup"><span data-stu-id="9bd6f-105">If the connection managers and external data sources supported by [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] do not entirely meet your requirements, you can create a custom connection manager.</span></span>  
  
 <span data-ttu-id="9bd6f-106">若要建立自訂連接管理員，您必須建立繼承自 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase> 基底類別的類別、將 <xref:Microsoft.SqlServer.Dts.Runtime.DtsConnectionAttribute> 屬性 (Attribute) 套用至新類別，以及覆寫基底類別的重要方法與屬性 (Property)，包括 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.ConnectionString%2A> 屬性 (Property) 與 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.AcquireConnection%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="9bd6f-106">To create a custom connection manager, you have to create a class that inherits from the <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase> base class, apply the <xref:Microsoft.SqlServer.Dts.Runtime.DtsConnectionAttribute> attribute to your new class, and override the important methods and properties of the base class, including the <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.ConnectionString%2A> property and the <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.AcquireConnection%2A> method.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="9bd6f-107">已經建置到 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 中的大多數工作、來源和目的地只能搭配特定類型的內建連接管理員一起使用。</span><span class="sxs-lookup"><span data-stu-id="9bd6f-107">Most of the tasks, sources, and destinations that have been built into [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] work only with specific types of built-in connection managers.</span></span> <span data-ttu-id="9bd6f-108">在開發自訂連接管理員以搭配內建工作與元件使用時，請檢查這些元件是否將可用的連接管理員清單限制在特定類型的連接管理員。</span><span class="sxs-lookup"><span data-stu-id="9bd6f-108">Before developing a custom connection manager for use with built-in tasks and components, check whether those components restrict the list of available connection managers to those of a specific type.</span></span> <span data-ttu-id="9bd6f-109">如果您的解決方案需要自訂連接管理員，您可能也必須開發自訂工作或是自訂來源或目的地，以供連接管理員使用。</span><span class="sxs-lookup"><span data-stu-id="9bd6f-109">If your solution requires a custom connection manager, you might also have to develop a custom task, or a custom source or destination, for use with the connection manager.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9bd6f-110">本節內容</span><span class="sxs-lookup"><span data-stu-id="9bd6f-110">In This Section</span></span>  
 <span data-ttu-id="9bd6f-111">本章節描述如何建立和設定自訂連接管理員及其選用自訂使用者介面，以及如何撰寫它們的程式碼。</span><span class="sxs-lookup"><span data-stu-id="9bd6f-111">This section describes how to create, configure, and code a custom connection manager and its optional custom user interface.</span></span> <span data-ttu-id="9bd6f-112">在本章節中所顯示的程式碼片段是取自 SQL Server 自訂連接管理員範例。</span><span class="sxs-lookup"><span data-stu-id="9bd6f-112">The code snippets shown in this section are drawn from the Sql Server Custom Connection Manager Sample.</span></span>  
  
 [<span data-ttu-id="9bd6f-113">建立自訂連線管理員</span><span class="sxs-lookup"><span data-stu-id="9bd6f-113">Creating a Custom Connection Manager</span></span>](creating-a-custom-connection-manager.md)  
 <span data-ttu-id="9bd6f-114">描述如何為自訂連接管理員專案建立類別。</span><span class="sxs-lookup"><span data-stu-id="9bd6f-114">Describes how to create the classes for a custom connection manager project.</span></span>  
  
 [<span data-ttu-id="9bd6f-115">撰寫自訂連線管理員的程式碼</span><span class="sxs-lookup"><span data-stu-id="9bd6f-115">Coding a Custom Connection Manager</span></span>](coding-a-custom-connection-manager.md)  
 <span data-ttu-id="9bd6f-116">描述如何透過覆寫基底類別的方法與屬性，來實作自訂連接管理員。</span><span class="sxs-lookup"><span data-stu-id="9bd6f-116">Describes how to implement a custom connection manager by overriding the methods and properties of the base class.</span></span>  
  
 [<span data-ttu-id="9bd6f-117">開發自訂連線管理員的使用者介面</span><span class="sxs-lookup"><span data-stu-id="9bd6f-117">Developing a User Interface for a Custom Connection Manager</span></span>](developing-a-user-interface-for-a-custom-connection-manager.md)  
 <span data-ttu-id="9bd6f-118">描述如何實作使用者介面類別以及用以設定自訂連接管理員的表單。</span><span class="sxs-lookup"><span data-stu-id="9bd6f-118">Describes how to implement the user interface class and the form that is used to configure the custom connection manager.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="9bd6f-119">相關章節</span><span class="sxs-lookup"><span data-stu-id="9bd6f-119">Related Sections</span></span>  
  
### <a name="information-common-to-all-custom-objects"></a><span data-ttu-id="9bd6f-120">自訂物件的共通資訊</span><span class="sxs-lookup"><span data-stu-id="9bd6f-120">Information Common to all Custom Objects</span></span>  
 <span data-ttu-id="9bd6f-121">如需有關 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 中可以建立之所有類型自訂物件適用的共通資訊，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="9bd6f-121">For information that is common to all the type of custom objects that you can create in [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)], see the following topics:</span></span>  
  
 [<span data-ttu-id="9bd6f-122">開發 Integration Services 的自訂物件</span><span class="sxs-lookup"><span data-stu-id="9bd6f-122">Developing Custom Objects for Integration Services</span></span>](../developing-custom-objects-for-integration-services.md)  
 <span data-ttu-id="9bd6f-123">描述為 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 實作所有類型的自訂物件之基本步驟。</span><span class="sxs-lookup"><span data-stu-id="9bd6f-123">Describes the basic steps in implementing all types of custom objects for [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)].</span></span>  
  
 [<span data-ttu-id="9bd6f-124">保存自訂物件</span><span class="sxs-lookup"><span data-stu-id="9bd6f-124">Persisting Custom Objects</span></span>](../persisting-custom-objects.md)  
 <span data-ttu-id="9bd6f-125">描述自訂的持續性並解釋必須實作它的時機。</span><span class="sxs-lookup"><span data-stu-id="9bd6f-125">Describes custom persistence and explains when it is necessary.</span></span>  
  
 [<span data-ttu-id="9bd6f-126">自訂物件的建立、部署和偵錯</span><span class="sxs-lookup"><span data-stu-id="9bd6f-126">Building, Deploying, and Debugging Custom Objects</span></span>](../building-deploying-and-debugging-custom-objects.md)  
 <span data-ttu-id="9bd6f-127">描述建立、簽署、部署和偵錯自訂物件的技術。</span><span class="sxs-lookup"><span data-stu-id="9bd6f-127">Describes the techniques for building, signing, deploying, and debugging custom objects.</span></span>  
  
### <a name="information-about-other-custom-objects"></a><span data-ttu-id="9bd6f-128">其他自訂物件的相關資訊</span><span class="sxs-lookup"><span data-stu-id="9bd6f-128">Information about Other Custom Objects</span></span>  
 <span data-ttu-id="9bd6f-129">如需有關在 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 中可以建立之其他類型自訂物件的詳細資訊，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="9bd6f-129">For information on the other types of custom objects that you can create in [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)], see the following topics:</span></span>  
  
 [<span data-ttu-id="9bd6f-130">開發自訂工作</span><span class="sxs-lookup"><span data-stu-id="9bd6f-130">Developing a Custom Task</span></span>](../task/developing-a-custom-task.md)  
 <span data-ttu-id="9bd6f-131">討論如何進行自訂工作的程式設計。</span><span class="sxs-lookup"><span data-stu-id="9bd6f-131">Discusses how to program custom tasks.</span></span>  
  
 [<span data-ttu-id="9bd6f-132">開發自訂記錄提供者</span><span class="sxs-lookup"><span data-stu-id="9bd6f-132">Developing a Custom Log Provider</span></span>](../log-provider/developing-a-custom-log-provider.md)  
 <span data-ttu-id="9bd6f-133">討論如何進行自訂記錄提供者的程式設計。</span><span class="sxs-lookup"><span data-stu-id="9bd6f-133">Discusses how to program custom log providers.</span></span>  
  
 [<span data-ttu-id="9bd6f-134">開發自訂 Foreach 列舉程式</span><span class="sxs-lookup"><span data-stu-id="9bd6f-134">Developing a Custom ForEach Enumerator</span></span>](../foreach-enumerator/developing-a-custom-foreach-enumerator.md)  
 <span data-ttu-id="9bd6f-135">討論如何進行自訂列舉值的程式設計。</span><span class="sxs-lookup"><span data-stu-id="9bd6f-135">Discusses how to program custom enumerators.</span></span>  
  
 [<span data-ttu-id="9bd6f-136">開發自訂資料流程元件</span><span class="sxs-lookup"><span data-stu-id="9bd6f-136">Developing a Custom Data Flow Component</span></span>](../data-flow/developing-a-custom-data-flow-component.md)  
 <span data-ttu-id="9bd6f-137">討論如何進行自訂資料流程來源、轉換和目的地的程式設計。</span><span class="sxs-lookup"><span data-stu-id="9bd6f-137">Discusses how to program custom data flow sources, transformations, and destinations.</span></span>  
  
<span data-ttu-id="9bd6f-138">![Integration Services 圖示 (小型) ](../../media/dts-16.gif "Integration Services 圖示 (小)")會**保持最**新狀態 Integration Services  </span><span class="sxs-lookup"><span data-stu-id="9bd6f-138">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="9bd6f-139">若要取得 Microsoft 的最新下載、文件、範例和影片以及社群中的精選解決方案，請瀏覽 MSDN 上的 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 頁面：</span><span class="sxs-lookup"><span data-stu-id="9bd6f-139">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="9bd6f-140">瀏覽 MSDN 上的 Integration Services 頁面</span><span class="sxs-lookup"><span data-stu-id="9bd6f-140">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="9bd6f-141">若要得到這些更新的自動通知，請訂閱該頁面上所提供的 RSS 摘要。</span><span class="sxs-lookup"><span data-stu-id="9bd6f-141">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
  
