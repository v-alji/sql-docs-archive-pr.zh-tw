---
title: 建立自訂 Foreach 列舉值 | Microsoft Docs
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
- custom foreach enumerators [Integration Services], creating
ms.assetid: 050e8455-2ed0-4b6d-b3ea-4e80e6c28487
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d99970d466aa53d25a80f0600f1fce7819e94956
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593454"
---
# <a name="creating-a-custom-foreach-enumerator"></a><span data-ttu-id="027ba-102">建立自訂 Foreach 列舉值</span><span class="sxs-lookup"><span data-stu-id="027ba-102">Creating a Custom Foreach Enumerator</span></span>
  <span data-ttu-id="027ba-103">建立自訂 Foreach 列舉值的步驟，與建立 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 之其他自訂物件的步驟類似：</span><span class="sxs-lookup"><span data-stu-id="027ba-103">The steps involved in creating a custom foreach enumerator are similar to the steps for creating any other custom object for [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]:</span></span>  
  
-   <span data-ttu-id="027ba-104">建立繼承自基底類別的新類別。</span><span class="sxs-lookup"><span data-stu-id="027ba-104">Create a new class that inherits from the base class.</span></span> <span data-ttu-id="027ba-105">對於 Foreach 列舉值而言，基底類別是 <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumerator>。</span><span class="sxs-lookup"><span data-stu-id="027ba-105">For a foreach enumerator, the base class is <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumerator>.</span></span>  
  
-   <span data-ttu-id="027ba-106">將可識別物件類型的屬性套用至類別。</span><span class="sxs-lookup"><span data-stu-id="027ba-106">Apply the attribute that identifies the type of object to the class.</span></span> <span data-ttu-id="027ba-107">對於 Foreach 列舉值而言，此屬性是 <xref:Microsoft.SqlServer.Dts.Runtime.DtsForEachEnumeratorAttribute>。</span><span class="sxs-lookup"><span data-stu-id="027ba-107">For a foreach enumerator, the attribute is <xref:Microsoft.SqlServer.Dts.Runtime.DtsForEachEnumeratorAttribute>.</span></span>  
  
-   <span data-ttu-id="027ba-108">覆寫基底類別之方法與屬性的實作。</span><span class="sxs-lookup"><span data-stu-id="027ba-108">Override the implementation of the base class's methods and properties.</span></span> <span data-ttu-id="027ba-109">對於 Foreach 列舉值而言，最重要的是 <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumerator.GetEnumerator%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="027ba-109">For a foreach enumerator, the most important is the <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumerator.GetEnumerator%2A> method.</span></span>  
  
-   <span data-ttu-id="027ba-110">(選擇性) 開發自訂使用者介面。</span><span class="sxs-lookup"><span data-stu-id="027ba-110">Optionally, develop a custom user interface.</span></span> <span data-ttu-id="027ba-111">對於 Foreach 列舉值而言，這需要實作 <xref:Microsoft.SqlServer.Dts.Runtime.IDTSForEachEnumeratorUI> 介面的類別。</span><span class="sxs-lookup"><span data-stu-id="027ba-111">For a foreach enumerator, this requires a class that implements the <xref:Microsoft.SqlServer.Dts.Runtime.IDTSForEachEnumeratorUI> interface.</span></span>  
  
 <span data-ttu-id="027ba-112">自訂列舉值是由 <xref:Microsoft.SqlServer.Dts.Runtime.ForEachLoop> 容器所裝載。</span><span class="sxs-lookup"><span data-stu-id="027ba-112">A custom enumerator is hosted by the <xref:Microsoft.SqlServer.Dts.Runtime.ForEachLoop> container.</span></span> <span data-ttu-id="027ba-113">在執行階段，<xref:Microsoft.SqlServer.Dts.Runtime.ForEachLoop> 容器會呼叫自訂列舉值的 <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumerator.GetEnumerator%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="027ba-113">At run time, the <xref:Microsoft.SqlServer.Dts.Runtime.ForEachLoop> container calls the <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumerator.GetEnumerator%2A> method of the custom enumerator.</span></span> <span data-ttu-id="027ba-114">自訂列舉值會傳回可實作 `IEnumerable` 介面的物件，例如 `ArrayList`。</span><span class="sxs-lookup"><span data-stu-id="027ba-114">The custom enumerator returns an object that implements the `IEnumerable` interface, such as an `ArrayList`.</span></span> <span data-ttu-id="027ba-115">然後，<xref:Microsoft.SqlServer.Dts.Runtime.ForEachLoop> 會逐一查看集合中的每一個元素、透過使用者定義的變數將目前元素的值提供給控制流程，然後在容器內執行此控制流程。</span><span class="sxs-lookup"><span data-stu-id="027ba-115">The <xref:Microsoft.SqlServer.Dts.Runtime.ForEachLoop> then iterates over each element in the collection, provides the value of the current element to the control flow through a user-defined variable, and executes the control flow in the container.</span></span>  
  
## <a name="getting-started-with-a-custom-foreach-enumerator"></a><span data-ttu-id="027ba-116">自訂 ForEach 列舉值使用者入門</span><span class="sxs-lookup"><span data-stu-id="027ba-116">Getting Started with a Custom ForEach Enumerator</span></span>  
  
### <a name="creating-projects-and-classes"></a><span data-ttu-id="027ba-117">建立專案和類別</span><span class="sxs-lookup"><span data-stu-id="027ba-117">Creating Projects and Classes</span></span>  
 <span data-ttu-id="027ba-118">因為所有的 Managed Foreach 列舉值都是從 <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumerator> 基底類別衍生，所以建立自訂 Foreach 列舉值的第一個步驟是以慣用的 Managed 程式語言建立類別庫專案，並建立繼承自此基底類別的類別。</span><span class="sxs-lookup"><span data-stu-id="027ba-118">Because all managed foreach enumerators derive from the <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumerator> base class, the first step when you create a custom foreach enumerator is to create a class library project in your preferred managed programming language and create a class that inherits from the base class.</span></span> <span data-ttu-id="027ba-119">在此衍生的類別中，您將覆寫基底類別的方法與屬性，以實作自訂功能。</span><span class="sxs-lookup"><span data-stu-id="027ba-119">In this derived class you will override the methods and properties of the base class to implement your custom functionality.</span></span>  
  
 <span data-ttu-id="027ba-120">在相同的方案中，為自訂使用者介面建立另一個類別庫專案。</span><span class="sxs-lookup"><span data-stu-id="027ba-120">In the same solution, create a second class library project for the custom user interface.</span></span> <span data-ttu-id="027ba-121">建議您針對使用者介面使用不同的組件以便能輕鬆地部署，因為它允許您獨立地更新和重新部署 Foreach 列舉值或是其使用者介面。</span><span class="sxs-lookup"><span data-stu-id="027ba-121">A separate assembly for the user interface is recommended for ease of deployment because it allows you to update and redeploy the foreach enumerator or its user interface independently.</span></span>  
  
 <span data-ttu-id="027ba-122">透過使用強式名稱金鑰檔案，將兩個專案都設定成簽署將在建立時期產生的組件。</span><span class="sxs-lookup"><span data-stu-id="027ba-122">Configure both projects to sign the assemblies that will be generated at build time by using a strong name key file.</span></span>  
  
### <a name="applying-the-dtsforeachenumerator-attribute"></a><span data-ttu-id="027ba-123">套用 DtsForEachEnumerator 屬性</span><span class="sxs-lookup"><span data-stu-id="027ba-123">Applying the DtsForEachEnumerator Attribute</span></span>  
 <span data-ttu-id="027ba-124">將 <xref:Microsoft.SqlServer.Dts.Runtime.DtsForEachEnumeratorAttribute> 屬性套用至您已建立的類別，以便將它識別為Foreach 列舉值。</span><span class="sxs-lookup"><span data-stu-id="027ba-124">Apply the <xref:Microsoft.SqlServer.Dts.Runtime.DtsForEachEnumeratorAttribute> attribute to the class that you have created to identify it as a foreach enumerator.</span></span> <span data-ttu-id="027ba-125">此屬性會提供設計階段資訊，例如 Foreach 列舉值的名稱和描述。</span><span class="sxs-lookup"><span data-stu-id="027ba-125">This attribute provides design-time information such as the name and description of the foreach enumerator.</span></span> <span data-ttu-id="027ba-126">`Name`屬性會出現在 [ **Foreach 迴圈編輯器**] 對話方塊之 [**集合**] 索引標籤上的可用列舉值下拉式清單中。</span><span class="sxs-lookup"><span data-stu-id="027ba-126">The `Name` property appears in the dropdown list of available enumerators on the **Collection** tab of the **Foreach Loop Editor** dialog box.</span></span>  
  
 <span data-ttu-id="027ba-127">使用 <xref:Microsoft.SqlServer.Dts.Runtime.DtsForEachEnumeratorAttribute.UITypeName%2A> 屬性將 Foreach 列舉值連結至其自訂使用者介面。</span><span class="sxs-lookup"><span data-stu-id="027ba-127">Use the <xref:Microsoft.SqlServer.Dts.Runtime.DtsForEachEnumeratorAttribute.UITypeName%2A> property to link the foreach enumerator to its custom user interface.</span></span> <span data-ttu-id="027ba-128">如需取得此屬性所需的公開金鑰權杖，可以使用 **sn.exe -t**，從要用於簽署使用者介面組件的金鑰組 (.snk) 檔案顯示公開金鑰權杖。</span><span class="sxs-lookup"><span data-stu-id="027ba-128">To obtain the public key token that is required for this property, you an use **sn.exe -t** to display the public key token from the key pair (.snk) file that you intend to use to sign the user interface assembly.</span></span>  
  
```vb  
Imports System  
Imports Microsoft.SqlServer.Dts.Runtime  
Namespace Microsoft.Samples.SqlServer.Dts  
    <DtsForEachEnumerator(DisplayName = "MyEnumerator", Description="A sample custom enumerator", UITypeName="FullyQualifiedTypeName,AssemblyName,Version=1.00.000.00,Culture=Neutral,PublicKeyToken=<publickeytoken>")> _   
    Public Class MyEnumerator  
     Inherits ForEachEnumerator  
        'Insert code here.  
    End Class  
End Namespace  
```  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Runtime;  
namespace Microsoft.Samples.SqlServer.Dts  
{  
    [DtsForEachEnumerator( DisplayName = "MyEnumerator", Description="A sample custom enumerator", UITypeName="FullyQualifiedTypeName,AssemblyName,Version=1.00.000.00,Culture=Neutral,PublicKeyToken=<publickeytoken>")]  
    public class MyEnumerator : ForEachEnumerator  
    {  
        //Insert code here.  
    }  
}  
```  
  
## <a name="building-deploying-and-debugging-a-custom-enumerator"></a><span data-ttu-id="027ba-129">建立、部署和偵錯自訂列舉值</span><span class="sxs-lookup"><span data-stu-id="027ba-129">Building, Deploying, and Debugging a Custom Enumerator</span></span>  
 <span data-ttu-id="027ba-130">在 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 中建立、部署和偵錯自訂 Foreach 列舉值的步驟，非常類似於其他類型的自訂物件所需的步驟。</span><span class="sxs-lookup"><span data-stu-id="027ba-130">The steps for building, deploying, and debugging a custom foreach enumerator in [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] are very similar to the steps required for other types of custom objects.</span></span> <span data-ttu-id="027ba-131">如需詳細資訊，請參閱[建立、部署和偵錯自訂物件](../building-deploying-and-debugging-custom-objects.md)。</span><span class="sxs-lookup"><span data-stu-id="027ba-131">For more information, see [Building, Deploying, and Debugging Custom Objects](../building-deploying-and-debugging-custom-objects.md).</span></span>  
  
<span data-ttu-id="027ba-132">![Integration Services 圖示 (小型) ](../../media/dts-16.gif "Integration Services 圖示 (小)")會**保持最**新狀態 Integration Services  </span><span class="sxs-lookup"><span data-stu-id="027ba-132">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="027ba-133">若要取得 Microsoft 的最新下載、文件、範例和影片以及社群中的精選解決方案，請瀏覽 MSDN 上的 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 頁面：</span><span class="sxs-lookup"><span data-stu-id="027ba-133">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="027ba-134">瀏覽 MSDN 上的 Integration Services 頁面</span><span class="sxs-lookup"><span data-stu-id="027ba-134">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="027ba-135">若要得到這些更新的自動通知，請訂閱該頁面上所提供的 RSS 摘要。</span><span class="sxs-lookup"><span data-stu-id="027ba-135">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="027ba-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="027ba-136">See Also</span></span>  
 <span data-ttu-id="027ba-137">[撰寫自訂 Foreach 列舉值的程式碼](coding-a-custom-foreach-enumerator.md) </span><span class="sxs-lookup"><span data-stu-id="027ba-137">[Coding a Custom Foreach Enumerator](coding-a-custom-foreach-enumerator.md) </span></span>  
 [<span data-ttu-id="027ba-138">開發自訂 ForEach 列舉值的使用者介面</span><span class="sxs-lookup"><span data-stu-id="027ba-138">Developing a User Interface for a Custom ForEach Enumerator</span></span>](developing-a-user-interface-for-a-custom-foreach-enumerator.md)  
  
  
