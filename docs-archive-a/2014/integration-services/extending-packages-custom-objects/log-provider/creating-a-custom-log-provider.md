---
title: 建立自訂記錄提供者 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom log providers [Integration Services], creating
ms.assetid: fc20af96-9eb8-4195-8d3f-8a4d7c753f24
author: chugugrace
ms.author: chugu
ms.openlocfilehash: c1efb736aece2cc8d118c81326989559f0d17a60
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87701299"
---
# <a name="creating-a-custom-log-provider"></a><span data-ttu-id="ac98f-102">建立自訂記錄提供者</span><span class="sxs-lookup"><span data-stu-id="ac98f-102">Creating a Custom Log Provider</span></span>
  <span data-ttu-id="ac98f-103">[!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 執行階段環境具有廣泛的記錄功能。</span><span class="sxs-lookup"><span data-stu-id="ac98f-103">The [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] run-time environment has extensive logging capabilities.</span></span> <span data-ttu-id="ac98f-104">用於擷取封裝執行期間所發生之事件的記錄檔。</span><span class="sxs-lookup"><span data-stu-id="ac98f-104">A log lets you capture events that occur during package execution.</span></span> [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] <span data-ttu-id="ac98f-105">包括各種記錄提供者，讓記錄可以多種格式，例如 XML、文字、資料庫或 Windows 事件記錄檔加以建立並儲存記錄檔。</span><span class="sxs-lookup"><span data-stu-id="ac98f-105">includes a variety of log providers that enable logs to be created and stored in multiple formats, such as XML, text, database, or in the Windows event log.</span></span> <span data-ttu-id="ac98f-106">如果這些提供者或輸出格式都不符合您的需求，可以建立自訂記錄提供者。</span><span class="sxs-lookup"><span data-stu-id="ac98f-106">If one of these providers or output formats does not fit your needs, you can create a custom log provider.</span></span>

 <span data-ttu-id="ac98f-107">建立自訂記錄提供者所需的步驟類似於為 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 建立任何其他自訂物件的步驟：</span><span class="sxs-lookup"><span data-stu-id="ac98f-107">The steps involved in creating a custom log provider are similar to the steps for creating any other custom object for [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]:</span></span>

-   <span data-ttu-id="ac98f-108">建立繼承自基底類別的新類別。</span><span class="sxs-lookup"><span data-stu-id="ac98f-108">Create a new class that inherits from the base class.</span></span> <span data-ttu-id="ac98f-109">對於記錄提供者而言，基底類別是 <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase>。</span><span class="sxs-lookup"><span data-stu-id="ac98f-109">For a log provider, the base class is <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase>.</span></span>

-   <span data-ttu-id="ac98f-110">將可識別物件類型的屬性套用至類別。</span><span class="sxs-lookup"><span data-stu-id="ac98f-110">Apply the attribute that identifies the type of object to the class.</span></span> <span data-ttu-id="ac98f-111">對於記錄提供者而言，屬性是 <xref:Microsoft.SqlServer.Dts.Runtime.DtsLogProviderAttribute>。</span><span class="sxs-lookup"><span data-stu-id="ac98f-111">For a log provider, the attribute is <xref:Microsoft.SqlServer.Dts.Runtime.DtsLogProviderAttribute>.</span></span>

-   <span data-ttu-id="ac98f-112">覆寫基底類別之方法與屬性的實作。</span><span class="sxs-lookup"><span data-stu-id="ac98f-112">Override the implementation of the base class's methods and properties.</span></span> <span data-ttu-id="ac98f-113">對於記錄提供者而言，這些包括 <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.ConfigString%2A> 屬性以及 <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.OpenLog%2A>、<xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.Log%2A> 和 <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.CloseLog%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="ac98f-113">For a log provider, these include the <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.ConfigString%2A> property and the <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.OpenLog%2A>, <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.Log%2A>, and <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.CloseLog%2A> methods.</span></span>

-   <span data-ttu-id="ac98f-114">在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 中並未實作自訂記錄提供者的自訂使用者介面。</span><span class="sxs-lookup"><span data-stu-id="ac98f-114">Custom user interfaces for custom log providers are not implemented in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)].</span></span>

## <a name="getting-started-with-a-custom-log-provider"></a><span data-ttu-id="ac98f-115">開始使用自訂記錄提供者</span><span class="sxs-lookup"><span data-stu-id="ac98f-115">Getting Started with a Custom Log Provider</span></span>

### <a name="creating-projects-and-classes"></a><span data-ttu-id="ac98f-116">建立專案和類別</span><span class="sxs-lookup"><span data-stu-id="ac98f-116">Creating Projects and Classes</span></span>
 <span data-ttu-id="ac98f-117">因為所有的 Managed 記錄提供者都是從 <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase> 基底類別衍生，所以在建立自訂記錄提供者時的第一個步驟是以慣用的 Managed 程式語言建立類別庫專案，然後建立繼承自基底類別的類別。</span><span class="sxs-lookup"><span data-stu-id="ac98f-117">Because all managed log providers derive from the <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase> base class, the first step when you create a custom log provider is to create a class library project in your preferred managed programming language, and then create a class that inherits from the base class.</span></span> <span data-ttu-id="ac98f-118">在此衍生的類別中，您將覆寫基底類別的方法與屬性，以實作自訂功能。</span><span class="sxs-lookup"><span data-stu-id="ac98f-118">In this derived class you will override the methods and properties of the base class to implement your custom functionality.</span></span>

 <span data-ttu-id="ac98f-119">設定專案以使用強式名稱金鑰檔案來簽署將產生的組件。</span><span class="sxs-lookup"><span data-stu-id="ac98f-119">Configure the project to sign the assembly that will be generated with a strong name key file.</span></span>

> [!NOTE]
>  <span data-ttu-id="ac98f-120">許多 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 記錄提供者都有自訂使用者介面，以實作 <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsLogProviderUI>，以及使用可用連線管理員的篩選下拉式清單，取代 [設定 SSIS 記錄] 對話方塊中的 [設定] 文字方塊。</span><span class="sxs-lookup"><span data-stu-id="ac98f-120">Many [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] log providers have a custom user interface that implements <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsLogProviderUI> and replaces the **Configuration** text box in the **Configure SSIS Logs** dialog box with a filtered dropdown list of available connection managers.</span></span> <span data-ttu-id="ac98f-121">不過，在 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 中並未實作自訂記錄提供者的自訂使用者介面。</span><span class="sxs-lookup"><span data-stu-id="ac98f-121">However custom user interfaces for custom log providers are not implemented in [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)].</span></span>

### <a name="applying-the-dtslogprovider-attribute"></a><span data-ttu-id="ac98f-122">套用 DtsLogProvider 屬性</span><span class="sxs-lookup"><span data-stu-id="ac98f-122">Applying the DtsLogProvider Attribute</span></span>
 <span data-ttu-id="ac98f-123">將 <xref:Microsoft.SqlServer.Dts.Runtime.DtsLogProviderAttribute> 屬性套用至您已建立的類別，以便將它識別為記錄提供者。</span><span class="sxs-lookup"><span data-stu-id="ac98f-123">Apply the <xref:Microsoft.SqlServer.Dts.Runtime.DtsLogProviderAttribute> attribute to the class that you have created to identify it as a log provider.</span></span> <span data-ttu-id="ac98f-124">此屬性會提供記錄提供者的名稱和描述等設計階段資訊。</span><span class="sxs-lookup"><span data-stu-id="ac98f-124">This attribute provides design-time information such as the name and description of the log provider.</span></span> <span data-ttu-id="ac98f-125">`DisplayName`屬性的和 `Description` 屬性會對應至 [設定 SSIS 記錄編輯器] 中所顯示的**名稱**和資料 `Description` 行，當您在中**設定**封裝的記錄時，就會顯示此編輯器 [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="ac98f-125">The `DisplayName` and `Description` properties of the attribute correspond to the **Name** and `Description` columns displayed in the **Configure SSIS Logs** editor, which is displayed when configuring logging for a package in [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)].</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="ac98f-126">未使用屬性 (Attribute) 的 <xref:Microsoft.SqlServer.Dts.Runtime.DtsLogProviderAttribute.LogProviderType%2A> 屬性 (Property)。</span><span class="sxs-lookup"><span data-stu-id="ac98f-126">The <xref:Microsoft.SqlServer.Dts.Runtime.DtsLogProviderAttribute.LogProviderType%2A> property of the attribute is not used.</span></span> <span data-ttu-id="ac98f-127">不過，您必須為它輸入值，否則自訂記錄提供者將不會顯示在可用記錄提供者的清單中。</span><span class="sxs-lookup"><span data-stu-id="ac98f-127">However, you must enter a value for it, or the custom log provider will not appear in the list of available log providers.</span></span>

> [!NOTE]
>  <span data-ttu-id="ac98f-128">既然在 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 中未實作自訂記錄提供者的自訂使用者介面，為 <xref:Microsoft.SqlServer.Dts.Runtime.DtsLogProviderAttribute.UITypeName%2A> 的 <xref:Microsoft.SqlServer.Dts.Runtime.DtsLogProviderAttribute> 屬性指定值並沒有作用。</span><span class="sxs-lookup"><span data-stu-id="ac98f-128">Since custom user interfaces for custom log providers are not implemented in [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)], specifying a value for the <xref:Microsoft.SqlServer.Dts.Runtime.DtsLogProviderAttribute.UITypeName%2A> property of the <xref:Microsoft.SqlServer.Dts.Runtime.DtsLogProviderAttribute> has no effect.</span></span>

```vb
<DtsLogProvider(DisplayName:="MyLogProvider", Description:="A simple log provider.", LogProviderType:="Custom")> _
Public Class MyLogProvider
     Inherits LogProviderBase
    ' TODO: Override the base class methods.
End Class
```

```csharp
[DtsLogProvider(DisplayName="MyLogProvider", Description="A simple log provider.", LogProviderType="Custom")]
public class MyLogProvider : LogProviderBase
{
    // TODO: Override the base class methods.
}
```

## <a name="building-deploying-and-debugging-a-custom-log-provider"></a><span data-ttu-id="ac98f-129">建立、部署和偵錯自訂記錄提供者</span><span class="sxs-lookup"><span data-stu-id="ac98f-129">Building, Deploying, and Debugging a Custom Log Provider</span></span>
 <span data-ttu-id="ac98f-130">在 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 中建立、部署和偵錯自訂記錄提供者的步驟，非常類似於其他類型的自訂物件所需的步驟。</span><span class="sxs-lookup"><span data-stu-id="ac98f-130">The steps for building, deploying, and debugging a custom log provider in [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] are very similar to the steps required for other types of custom objects.</span></span> <span data-ttu-id="ac98f-131">如需詳細資訊，請參閱[建立、部署和偵錯自訂物件](../building-deploying-and-debugging-custom-objects.md)。</span><span class="sxs-lookup"><span data-stu-id="ac98f-131">For more information, see [Building, Deploying, and Debugging Custom Objects](../building-deploying-and-debugging-custom-objects.md).</span></span>

<span data-ttu-id="ac98f-132">![Integration Services 圖示 (小型) ](../../media/dts-16.gif "Integration Services 圖示 (小)")會**保持最**新狀態 Integration Services  </span><span class="sxs-lookup"><span data-stu-id="ac98f-132">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="ac98f-133">若要取得 Microsoft 的最新下載、文件、範例和影片以及社群中的精選解決方案，請瀏覽 MSDN 上的 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 頁面：</span><span class="sxs-lookup"><span data-stu-id="ac98f-133">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="ac98f-134">瀏覽 MSDN 上的 Integration Services 頁面</span><span class="sxs-lookup"><span data-stu-id="ac98f-134">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="ac98f-135">若要得到這些更新的自動通知，請訂閱該頁面上所提供的 RSS 摘要。</span><span class="sxs-lookup"><span data-stu-id="ac98f-135">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>

## <a name="see-also"></a><span data-ttu-id="ac98f-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ac98f-136">See Also</span></span>
 <span data-ttu-id="ac98f-137">撰寫自訂記錄[提供者的程式碼](coding-a-custom-log-provider.md)[開發自訂記錄提供者的使用者介面](developing-a-user-interface-for-a-custom-log-provider.md)</span><span class="sxs-lookup"><span data-stu-id="ac98f-137">[Coding a Custom Log Provider](coding-a-custom-log-provider.md) [Developing a User Interface for a Custom Log Provider](developing-a-user-interface-for-a-custom-log-provider.md)</span></span>


