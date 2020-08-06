---
title: 開發自訂 ForEach 列舉值 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- custom foreach enumerators [Integration Services]
- custom foreach enumerators [Integration Services], about custom foreach enumerators
- foreach enumerators [Integration Services]
ms.assetid: bffe26e0-1b9a-47ad-bae6-6b708cb4cf4f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: bc3d61f98266320f63d7ee56262b7c85dfb64d39
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596211"
---
# <a name="developing-a-custom-foreach-enumerator"></a><span data-ttu-id="1b68c-102">開發自訂 ForEach 列舉值</span><span class="sxs-lookup"><span data-stu-id="1b68c-102">Developing a Custom ForEach Enumerator</span></span>
  [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] <span data-ttu-id="1b68c-103">會使用 Foreach 列舉值在集合中反覆運算項目，並為每個元素執行相同的工作。</span><span class="sxs-lookup"><span data-stu-id="1b68c-103">uses foreach enumerators to iterate over the items in a collection and perform the same tasks for each element.</span></span> [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] <span data-ttu-id="1b68c-104">包括各種 Foreach 列舉值，可以支援最常使用的集合，例如在資料夾中的所有檔案、資料庫中的所有資料表，或是儲存在封裝變數中的清單之所有元素。</span><span class="sxs-lookup"><span data-stu-id="1b68c-104">includes a variety of foreach enumerators that support the most commonly used collections, such as all the files in a folder, all the tables in a database, or all the elements of a list stored in a package variable.</span></span> <span data-ttu-id="1b68c-105">如果提供的 Foreach 列舉值與集合並未完全符合您的需求，可以建立自訂 Foreach 列舉值。</span><span class="sxs-lookup"><span data-stu-id="1b68c-105">If the foreach enumerators and collections that are provided do not entirely meet your requirements, you can create a custom foreach enumerator.</span></span>  
  
 <span data-ttu-id="1b68c-106">若要建立自訂 Foreach 列舉值，您必須建立繼承自 <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumerator> 基底類別的類別、將 <xref:Microsoft.SqlServer.Dts.Runtime.DtsForEachEnumeratorAttribute> 屬性 (Attribute) 套用至新類別，以及覆寫基底類別的重要方法與屬性 (Property)，包括 <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumerator.GetEnumerator%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="1b68c-106">To create a custom foreach enumerator, you have to create a class that inherits from the <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumerator> base class, apply the <xref:Microsoft.SqlServer.Dts.Runtime.DtsForEachEnumeratorAttribute> attribute to your new class, and override the important methods and properties of the base class, including the <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumerator.GetEnumerator%2A> method.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1b68c-107">本節內容</span><span class="sxs-lookup"><span data-stu-id="1b68c-107">In This Section</span></span>  
 <span data-ttu-id="1b68c-108">本章節描述如何建立和設定自訂 Foreach 列舉值及其自訂使用者介面，以及如何撰寫它們的程式碼。</span><span class="sxs-lookup"><span data-stu-id="1b68c-108">This section describes how to create, configure, and code a custom foreach enumerator and its custom user interface.</span></span>  
  
 [<span data-ttu-id="1b68c-109">建立自訂 Foreach 列舉程式</span><span class="sxs-lookup"><span data-stu-id="1b68c-109">Creating a Custom Foreach Enumerator</span></span>](creating-a-custom-foreach-enumerator.md)  
 <span data-ttu-id="1b68c-110">描述如何為自訂 Foreach 列舉值專案建立類別。</span><span class="sxs-lookup"><span data-stu-id="1b68c-110">Describes how to create the classes for a custom foreach enumerator project.</span></span>  
  
 [<span data-ttu-id="1b68c-111">撰寫自訂 Foreach 列舉程式的程式碼</span><span class="sxs-lookup"><span data-stu-id="1b68c-111">Coding a Custom Foreach Enumerator</span></span>](coding-a-custom-foreach-enumerator.md)  
 <span data-ttu-id="1b68c-112">描述如何透過覆寫基底類別的方法與屬性，來實作自訂 Foreach 列舉值。</span><span class="sxs-lookup"><span data-stu-id="1b68c-112">Describes how to implement a custom foreach enumerator by overriding the methods and properties of the base class.</span></span>  
  
 [<span data-ttu-id="1b68c-113">開發自訂 Foreach 列舉程式的使用者介面</span><span class="sxs-lookup"><span data-stu-id="1b68c-113">Developing a User Interface for a Custom ForEach Enumerator</span></span>](developing-a-user-interface-for-a-custom-foreach-enumerator.md)  
 <span data-ttu-id="1b68c-114">描述如何實作用以設定自訂 Foreach 列舉值的使用者介面類別與表單。</span><span class="sxs-lookup"><span data-stu-id="1b68c-114">Describes how to implement the user interface class and the form that is used to configure the custom foreach enumerator.</span></span>  
  
## <a name="related-topics"></a><span data-ttu-id="1b68c-115">相關主題</span><span class="sxs-lookup"><span data-stu-id="1b68c-115">Related Topics</span></span>  
  
### <a name="information-common-to-all-custom-objects"></a><span data-ttu-id="1b68c-116">自訂物件的共通資訊</span><span class="sxs-lookup"><span data-stu-id="1b68c-116">Information Common to all Custom Objects</span></span>  
 <span data-ttu-id="1b68c-117">如需有關 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 中可以建立之所有類型自訂物件適用的共通資訊，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="1b68c-117">For information that is common to all the type of custom objects that you can create in [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)], see the following topics:</span></span>  
  
 [<span data-ttu-id="1b68c-118">開發 Integration Services 的自訂物件</span><span class="sxs-lookup"><span data-stu-id="1b68c-118">Developing Custom Objects for Integration Services</span></span>](../developing-custom-objects-for-integration-services.md)  
 <span data-ttu-id="1b68c-119">描述為 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 實作所有類型的自訂物件之基本步驟。</span><span class="sxs-lookup"><span data-stu-id="1b68c-119">Describes the basic steps in implementing all types of custom objects for [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)].</span></span>  
  
 [<span data-ttu-id="1b68c-120">保存自訂物件</span><span class="sxs-lookup"><span data-stu-id="1b68c-120">Persisting Custom Objects</span></span>](../persisting-custom-objects.md)  
 <span data-ttu-id="1b68c-121">描述自訂的持續性並解釋必須實作它的時機。</span><span class="sxs-lookup"><span data-stu-id="1b68c-121">Describes custom persistence and explains when it is necessary.</span></span>  
  
 [<span data-ttu-id="1b68c-122">自訂物件的建立、部署和偵錯</span><span class="sxs-lookup"><span data-stu-id="1b68c-122">Building, Deploying, and Debugging Custom Objects</span></span>](../building-deploying-and-debugging-custom-objects.md)  
 <span data-ttu-id="1b68c-123">描述建立、簽署、部署和偵錯自訂物件的技術。</span><span class="sxs-lookup"><span data-stu-id="1b68c-123">Describes the techniques for building, signing, deploying, and debugging custom objects.</span></span>  
  
### <a name="information-about-other-custom-objects"></a><span data-ttu-id="1b68c-124">其他自訂物件的相關資訊</span><span class="sxs-lookup"><span data-stu-id="1b68c-124">Information about Other Custom Objects</span></span>  
 <span data-ttu-id="1b68c-125">如需有關在 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 中可以建立之其他類型自訂物件的詳細資訊，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="1b68c-125">For information on the other types of custom objects that you can create in [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)], see the following topics:</span></span>  
  
 [<span data-ttu-id="1b68c-126">開發自訂工作</span><span class="sxs-lookup"><span data-stu-id="1b68c-126">Developing a Custom Task</span></span>](../task/developing-a-custom-task.md)  
 <span data-ttu-id="1b68c-127">討論如何進行自訂工作的程式設計。</span><span class="sxs-lookup"><span data-stu-id="1b68c-127">Discusses how to program custom tasks.</span></span>  
  
 [<span data-ttu-id="1b68c-128">開發自訂連線管理員</span><span class="sxs-lookup"><span data-stu-id="1b68c-128">Developing a Custom Connection Manager</span></span>](../connection-manager/developing-a-custom-connection-manager.md)  
 <span data-ttu-id="1b68c-129">討論如何進行自訂連接管理員的程式設計。</span><span class="sxs-lookup"><span data-stu-id="1b68c-129">Discusses how to program custom connection managers.</span></span>  
  
 [<span data-ttu-id="1b68c-130">開發自訂記錄提供者</span><span class="sxs-lookup"><span data-stu-id="1b68c-130">Developing a Custom Log Provider</span></span>](../log-provider/developing-a-custom-log-provider.md)  
 <span data-ttu-id="1b68c-131">討論如何進行自訂記錄提供者的程式設計。</span><span class="sxs-lookup"><span data-stu-id="1b68c-131">Discusses how to program custom log providers.</span></span>  
  
 [<span data-ttu-id="1b68c-132">開發自訂資料流程元件</span><span class="sxs-lookup"><span data-stu-id="1b68c-132">Developing a Custom Data Flow Component</span></span>](../data-flow/developing-a-custom-data-flow-component.md)  
 <span data-ttu-id="1b68c-133">討論如何進行自訂資料流程來源、轉換和目的地的程式設計。</span><span class="sxs-lookup"><span data-stu-id="1b68c-133">Discusses how to program custom data flow sources, transformations, and destinations.</span></span>  
  
<span data-ttu-id="1b68c-134">![Integration Services 圖示 (小型) ](../../media/dts-16.gif "Integration Services 圖示 (小)")會**保持最**新狀態 Integration Services  </span><span class="sxs-lookup"><span data-stu-id="1b68c-134">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="1b68c-135">若要取得 Microsoft 的最新下載、文件、範例和影片以及社群中的精選解決方案，請瀏覽 MSDN 上的 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 頁面：</span><span class="sxs-lookup"><span data-stu-id="1b68c-135">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="1b68c-136">瀏覽 MSDN 上的 Integration Services 頁面</span><span class="sxs-lookup"><span data-stu-id="1b68c-136">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="1b68c-137">若要得到這些更新的自動通知，請訂閱該頁面上所提供的 RSS 摘要。</span><span class="sxs-lookup"><span data-stu-id="1b68c-137">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
  
