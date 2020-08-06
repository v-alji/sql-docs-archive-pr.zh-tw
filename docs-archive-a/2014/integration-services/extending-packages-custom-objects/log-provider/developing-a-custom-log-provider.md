---
title: 開發自訂記錄提供者 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- SSIS packages, log providers
- custom log providers [Integration Services]
- SQL Server Integration Services packages, log providers
- log providers [Integration Services]
- packages [Integration Services], logs
- Integration Services packages, log providers
ms.assetid: 3f715b95-7074-4f5c-8ae2-246998052e78
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 88d4f70fa9d50628b831b56f9fa22100648fce51
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592169"
---
# <a name="developing-a-custom-log-provider"></a><span data-ttu-id="ef8a4-102">開發自訂記錄提供者</span><span class="sxs-lookup"><span data-stu-id="ef8a4-102">Developing a Custom Log Provider</span></span>
  [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] <span data-ttu-id="ef8a4-103">具有多種記錄功能，可以擷取在封裝執行期間所發生的事件。</span><span class="sxs-lookup"><span data-stu-id="ef8a4-103">has extensive logging capabilities that make it possible to capture events that occur during package execution.</span></span> [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] <span data-ttu-id="ef8a4-104">包括各種記錄提供者，讓記錄可以 XML、文字、資料庫或 Windows 事件記錄檔格式加以建立並儲存記錄檔。</span><span class="sxs-lookup"><span data-stu-id="ef8a4-104">includes a variety of log providers that enable logs to be created and stored in formats such as XML, text, database, or in the Windows event log.</span></span> <span data-ttu-id="ef8a4-105">如果所提供的記錄提供者與輸出格式並未完全符合您的需求，可以建立自訂記錄提供者。</span><span class="sxs-lookup"><span data-stu-id="ef8a4-105">If the log providers and the output formats that are provided do not entirely meet your requirements, you can create a custom log provider.</span></span>

 <span data-ttu-id="ef8a4-106">若要建立自訂記錄提供者，您必須建立繼承自 <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase> 基底類別的類別、將 <xref:Microsoft.SqlServer.Dts.Runtime.DtsLogProviderAttribute> 屬性 (Attribute) 套用至新類別，以及覆寫基底類別的重要方法與屬性 (Property)，包括 <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.ConfigString%2A> 屬性 (Property) 與 <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.Log%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="ef8a4-106">To create a custom log provider, you have to create a class that inherits from the <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase> base class, apply the <xref:Microsoft.SqlServer.Dts.Runtime.DtsLogProviderAttribute> attribute to your new class, and override the important methods and properties of the base class, including the <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.ConfigString%2A> property and the <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.Log%2A> method.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="ef8a4-107">本節內容</span><span class="sxs-lookup"><span data-stu-id="ef8a4-107">In This Section</span></span>
 <span data-ttu-id="ef8a4-108">本節描述如何建立、設定和撰寫自訂記錄提供者的程式碼。</span><span class="sxs-lookup"><span data-stu-id="ef8a4-108">This section describes how to create, configure, and code a custom log provider.</span></span>

 <span data-ttu-id="ef8a4-109">[建立自訂記錄提供者](creating-a-custom-log-provider.md)描述如何建立自訂記錄提供者專案的類別。</span><span class="sxs-lookup"><span data-stu-id="ef8a4-109">[Creating a Custom Log Provider](creating-a-custom-log-provider.md) Describes how to create the classes for a custom log provider project.</span></span>

 <span data-ttu-id="ef8a4-110">撰寫[自訂記錄提供者的程式碼](coding-a-custom-log-provider.md)描述如何藉由覆寫基類的方法和屬性，來執行自訂記錄提供者。</span><span class="sxs-lookup"><span data-stu-id="ef8a4-110">[Coding a Custom Log Provider](coding-a-custom-log-provider.md) Describes how to implement a custom log provider by overriding the methods and properties of the base class.</span></span>

 <span data-ttu-id="ef8a4-111">[開發自訂記錄提供者的使用者介面](developing-a-user-interface-for-a-custom-log-provider.md)中不支援自訂記錄提供者的自訂使用者介面 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="ef8a4-111">[Developing a User Interface for a Custom Log Provider](developing-a-user-interface-for-a-custom-log-provider.md) Custom user interfaces for custom log providers are not supported in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)].</span></span>

## <a name="related-topics"></a><span data-ttu-id="ef8a4-112">相關主題</span><span class="sxs-lookup"><span data-stu-id="ef8a4-112">Related Topics</span></span>

### <a name="information-common-to-all-custom-objects"></a><span data-ttu-id="ef8a4-113">自訂物件的共通資訊</span><span class="sxs-lookup"><span data-stu-id="ef8a4-113">Information Common to all Custom Objects</span></span>
 <span data-ttu-id="ef8a4-114">如需有關 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 中可以建立之所有類型自訂物件適用的共通資訊，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="ef8a4-114">For information that is common to all the type of custom objects that you can create in [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)], see the following topics:</span></span>

 <span data-ttu-id="ef8a4-115">[開發 Integration Services 的自訂物件](../developing-custom-objects-for-integration-services.md)說明為執行所有類型之自訂物件的基本步驟 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="ef8a4-115">[Developing Custom Objects for Integration Services](../developing-custom-objects-for-integration-services.md) Describes the basic steps in implementing all types of custom objects for [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)].</span></span>

 <span data-ttu-id="ef8a4-116">[保存自訂物件](../persisting-custom-objects.md)描述自訂持續性，並在必要時加以說明。</span><span class="sxs-lookup"><span data-stu-id="ef8a4-116">[Persisting Custom Objects](../persisting-custom-objects.md) Describes custom persistence and explains when it is necessary.</span></span>

 <span data-ttu-id="ef8a4-117">[建立、部署和調試自訂物件](../building-deploying-and-debugging-custom-objects.md)說明建立、簽署、部署和偵錯工具自訂物件的技術。</span><span class="sxs-lookup"><span data-stu-id="ef8a4-117">[Building, Deploying, and Debugging Custom Objects](../building-deploying-and-debugging-custom-objects.md) Describes the techniques for building, signing, deploying, and debugging custom objects.</span></span>

### <a name="information-about-other-custom-objects"></a><span data-ttu-id="ef8a4-118">其他自訂物件的相關資訊</span><span class="sxs-lookup"><span data-stu-id="ef8a4-118">Information about Other Custom Objects</span></span>
 <span data-ttu-id="ef8a4-119">如需有關在 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 中可以建立之其他類型自訂物件的詳細資訊，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="ef8a4-119">For information on the other types of custom objects that you can create in [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)], see the following topics:</span></span>

 <span data-ttu-id="ef8a4-120">[開發自訂工作](../task/developing-a-custom-task.md)討論如何編寫自訂工作的程式。</span><span class="sxs-lookup"><span data-stu-id="ef8a4-120">[Developing a Custom Task](../task/developing-a-custom-task.md) Discusses how to program custom tasks.</span></span>

 <span data-ttu-id="ef8a4-121">[開發自訂連線管理員](../connection-manager/developing-a-custom-connection-manager.md)討論如何編寫自訂連接管理員的程式。</span><span class="sxs-lookup"><span data-stu-id="ef8a4-121">[Developing a Custom Connection Manager](../connection-manager/developing-a-custom-connection-manager.md) Discusses how to program custom connection managers.</span></span>

 <span data-ttu-id="ef8a4-122">[開發自訂 ForEach 列舉](../foreach-enumerator/developing-a-custom-foreach-enumerator.md)值討論如何編寫自訂枚舉器的程式。</span><span class="sxs-lookup"><span data-stu-id="ef8a4-122">[Developing a Custom ForEach Enumerator](../foreach-enumerator/developing-a-custom-foreach-enumerator.md) Discusses how to program custom enumerators.</span></span>

 <span data-ttu-id="ef8a4-123">[開發自訂資料流程元件](../data-flow/developing-a-custom-data-flow-component.md)討論如何程式設計自訂資料流程來源、轉換和目的地。</span><span class="sxs-lookup"><span data-stu-id="ef8a4-123">[Developing a Custom Data Flow Component](../data-flow/developing-a-custom-data-flow-component.md) Discusses how to program custom data flow sources, transformations, and destinations.</span></span>

<span data-ttu-id="ef8a4-124">![Integration Services 圖示 (小型) ](../../media/dts-16.gif "Integration Services 圖示 (小)")會**保持最**新狀態 Integration Services  </span><span class="sxs-lookup"><span data-stu-id="ef8a4-124">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="ef8a4-125">若要取得 Microsoft 的最新下載、文件、範例和影片以及社群中的精選解決方案，請瀏覽 MSDN 上的 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 頁面：</span><span class="sxs-lookup"><span data-stu-id="ef8a4-125">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="ef8a4-126">瀏覽 MSDN 上的 Integration Services 頁面</span><span class="sxs-lookup"><span data-stu-id="ef8a4-126">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="ef8a4-127">若要得到這些更新的自動通知，請訂閱該頁面上所提供的 RSS 摘要。</span><span class="sxs-lookup"><span data-stu-id="ef8a4-127">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>


