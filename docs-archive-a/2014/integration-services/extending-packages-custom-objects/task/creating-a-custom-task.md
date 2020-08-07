---
title: 建立自訂工作 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- custom tasks [Integration Services], creating
ms.assetid: 42965c09-1782-4cdb-9ce1-216af4c23e0a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f752acad7a442a8e0aad2d24e94938c14195a35d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597222"
---
# <a name="creating-a-custom-task"></a><span data-ttu-id="c7d23-102">建立自訂工作</span><span class="sxs-lookup"><span data-stu-id="c7d23-102">Creating a Custom Task</span></span>
  <span data-ttu-id="c7d23-103">建立自訂工作的步驟，與建立 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 之其他自訂物件的步驟類似：</span><span class="sxs-lookup"><span data-stu-id="c7d23-103">The steps involved in creating a custom task are similar to the steps for creating any other custom object for [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]:</span></span>  
  
-   <span data-ttu-id="c7d23-104">建立繼承自基底類別的新類別。</span><span class="sxs-lookup"><span data-stu-id="c7d23-104">Create a new class that inherits from the base class.</span></span> <span data-ttu-id="c7d23-105">針對工作而言，基底類別是 [Microsoft.SqlServer.Dts.Runtime.Task](/dotnet/api/microsoft.sqlserver.dts.runtime.task)。</span><span class="sxs-lookup"><span data-stu-id="c7d23-105">For a task, the base class is [Microsoft.SqlServer.Dts.Runtime.Task](/dotnet/api/microsoft.sqlserver.dts.runtime.task).</span></span>  
  
-   <span data-ttu-id="c7d23-106">將可識別物件類型的屬性套用至類別。</span><span class="sxs-lookup"><span data-stu-id="c7d23-106">Apply the attribute that identifies the type of object to the class.</span></span> <span data-ttu-id="c7d23-107">對於工作而言，屬性是 <xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute>。</span><span class="sxs-lookup"><span data-stu-id="c7d23-107">For a task, the attribute is <xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute>.</span></span>  
  
-   <span data-ttu-id="c7d23-108">覆寫基底類別之方法與屬性的實作。</span><span class="sxs-lookup"><span data-stu-id="c7d23-108">Override the implementation of the base class's methods and properties.</span></span> <span data-ttu-id="c7d23-109">對於工作而言，這些包括 <xref:Microsoft.SqlServer.Dts.Runtime.Task.Validate%2A> 與 <xref:Microsoft.SqlServer.Dts.Runtime.Task.Execute%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="c7d23-109">For a task, these include the <xref:Microsoft.SqlServer.Dts.Runtime.Task.Validate%2A> and <xref:Microsoft.SqlServer.Dts.Runtime.Task.Execute%2A> methods.</span></span>  
  
-   <span data-ttu-id="c7d23-110">(選擇性) 開發自訂使用者介面。</span><span class="sxs-lookup"><span data-stu-id="c7d23-110">Optionally, develop a custom user interface.</span></span> <span data-ttu-id="c7d23-111">對於工作而言，這需要實作 <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsTaskUI> 介面的類別。</span><span class="sxs-lookup"><span data-stu-id="c7d23-111">For a task, this requires a class that implements the <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsTaskUI> interface.</span></span>  
  
## <a name="getting-started-with-a-custom-task"></a><span data-ttu-id="c7d23-112">自訂工作使用者入門</span><span class="sxs-lookup"><span data-stu-id="c7d23-112">Getting Started with a Custom Task</span></span>  
  
### <a name="creating-projects-and-classes"></a><span data-ttu-id="c7d23-113">建立專案和類別</span><span class="sxs-lookup"><span data-stu-id="c7d23-113">Creating Projects and Classes</span></span>  
 <span data-ttu-id="c7d23-114">因為所有的受控工作都是從 [Microsoft.SqlServer.Dts.Runtime.Task](/dotnet/api/microsoft.sqlserver.dts.runtime.task) 基底類別衍生，所以建立自訂工作時的第一個步驟是以慣用的受控程式設計語言建立類別庫專案，並建立從基底類別繼承的類別。</span><span class="sxs-lookup"><span data-stu-id="c7d23-114">Because all managed tasks derive from the [Microsoft.SqlServer.Dts.Runtime.Task](/dotnet/api/microsoft.sqlserver.dts.runtime.task) base class, the first step when you create a custom task is to create a class library project in your preferred managed programming language and create a class that inherits from the base class.</span></span> <span data-ttu-id="c7d23-115">在此衍生的類別中，您將覆寫基底類別的方法與屬性，以實作自訂功能。</span><span class="sxs-lookup"><span data-stu-id="c7d23-115">In this derived class you will override the methods and properties of the base class to implement your custom functionality.</span></span>  
  
 <span data-ttu-id="c7d23-116">在相同的方案中，為自訂使用者介面建立另一個類別庫專案。</span><span class="sxs-lookup"><span data-stu-id="c7d23-116">In the same solution, create a second class library project for the custom user interface.</span></span> <span data-ttu-id="c7d23-117">建議為使用者介面使用不同的組件以便能輕鬆地部署，因為它允許您獨立地更新和重新部署連接管理員或是其使用者介面。</span><span class="sxs-lookup"><span data-stu-id="c7d23-117">A separate assembly for the user interface is recommended for ease of deployment because it allows you to update and redeploy the connection manager or its user interface independently.</span></span>  
  
 <span data-ttu-id="c7d23-118">透過使用強式名稱金鑰檔案，將兩個專案都設定成簽署將在建立時期產生的組件。</span><span class="sxs-lookup"><span data-stu-id="c7d23-118">Configure both projects to sign the assemblies that will be generated at build time by using a strong name key file.</span></span>  
  
### <a name="applying-the-dtstask-attribute"></a><span data-ttu-id="c7d23-119">套用 DtsTask 屬性</span><span class="sxs-lookup"><span data-stu-id="c7d23-119">Applying the DtsTask Attribute</span></span>  
 <span data-ttu-id="c7d23-120">將 <xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute> 屬性套用至您已建立的類別，以便將它識別為工作。</span><span class="sxs-lookup"><span data-stu-id="c7d23-120">Apply the <xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute> attribute to the class that you have created to identify it as a task.</span></span> <span data-ttu-id="c7d23-121">此屬性提供如名稱、描述和工作類別等設計階段資訊。</span><span class="sxs-lookup"><span data-stu-id="c7d23-121">This attribute provides design-time information such as the name, description, and task type of the task.</span></span>  
  
 <span data-ttu-id="c7d23-122">使用 <xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute.UITypeName%2A> 屬性將工作連結至其自訂使用者介面。</span><span class="sxs-lookup"><span data-stu-id="c7d23-122">Use the <xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute.UITypeName%2A> property to link the task to its custom user interface.</span></span> <span data-ttu-id="c7d23-123">如需取得此屬性所需的公開金鑰權杖，可以使用 **sn.exe -t**，從要用於簽署使用者介面組件的金鑰組 (.snk) 檔案顯示公開金鑰權杖。</span><span class="sxs-lookup"><span data-stu-id="c7d23-123">To obtain the public key token that is required for this property, you an use **sn.exe -t** to display the public key token from the key pair (.snk) file that you intend to use to sign the user interface assembly.</span></span>  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Runtime;  
namespace Microsoft.SSIS.Samples  
{  
  [DtsTask  
  (  
   DisplayName = "MyTask",  
   IconResource = "MyTask.MyTaskIcon.ico",  
   UITypeName = "My Custom Task," +  
   "Version=1.0.0.0," +  
   "Culture = Neutral," +  
   "PublicKeyToken = 12345abc6789de01",  
   TaskType = "PackageMaintenance",  
   TaskContact = "MyTask; company name; any other information",  
   RequiredProductLevel = DTSProductLevel.None  
   )]  
  public class MyTask : Task  
  {  
    // Your code here.  
  }  
}  
```  
  
```vb  
Imports System  
Imports Microsoft.SqlServer.Dts.Runtime  
  
<DtsTask(DisplayName:="MyTask", _  
 IconResource:="MyTask.MyTaskIcon.ico", _  
 UITypeName:="My Custom Task," & _  
 "Version=1.0.0.0,Culture=Neutral," & _  
 "PublicKeyToken=12345abc6789de01", _  
 TaskType:="PackageMaintenance", _  
 TaskContact:="MyTask; company name; any other information", _  
 RequiredProductLevel:=DTSProductLevel.None)> _  
Public Class MyTask  
  Inherits Task  
  
  ' Your code here.  
  
End Class 'MyTask  
```  
  
## <a name="building-deploying-and-debugging-a-custom-task"></a><span data-ttu-id="c7d23-124">建置、部署和偵錯自訂工作</span><span class="sxs-lookup"><span data-stu-id="c7d23-124">Building, Deploying, and Debugging a Custom Task</span></span>  
 <span data-ttu-id="c7d23-125">在 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 中建立、部署和偵錯自訂工作的步驟，類似於其他類型的自訂物件所需的步驟。</span><span class="sxs-lookup"><span data-stu-id="c7d23-125">The steps for building, deploying, and debugging a custom task in [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] are similar to the steps required for other types of custom objects.</span></span> <span data-ttu-id="c7d23-126">如需詳細資訊，請參閱[建立、部署和偵錯自訂物件](../building-deploying-and-debugging-custom-objects.md)。</span><span class="sxs-lookup"><span data-stu-id="c7d23-126">For more information, see [Building, Deploying, and Debugging Custom Objects](../building-deploying-and-debugging-custom-objects.md).</span></span>  
  
<span data-ttu-id="c7d23-127">![Integration Services 圖示 (小型) ](../../media/dts-16.gif "Integration Services 圖示 (小)")會**保持最**新狀態 Integration Services  </span><span class="sxs-lookup"><span data-stu-id="c7d23-127">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="c7d23-128">若要取得 Microsoft 的最新下載、文件、範例和影片以及社群中的精選解決方案，請瀏覽 MSDN 上的 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 頁面：</span><span class="sxs-lookup"><span data-stu-id="c7d23-128">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="c7d23-129">瀏覽 MSDN 上的 Integration Services 頁面</span><span class="sxs-lookup"><span data-stu-id="c7d23-129">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="c7d23-130">若要得到這些更新的自動通知，請訂閱該頁面上所提供的 RSS 摘要。</span><span class="sxs-lookup"><span data-stu-id="c7d23-130">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7d23-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c7d23-131">See Also</span></span>  
 <span data-ttu-id="c7d23-132">[建立自訂工作](creating-a-custom-task.md) </span><span class="sxs-lookup"><span data-stu-id="c7d23-132">[Creating a Custom Task](creating-a-custom-task.md) </span></span>  
 <span data-ttu-id="c7d23-133">[撰寫自訂工作的程式碼](coding-a-custom-task.md) </span><span class="sxs-lookup"><span data-stu-id="c7d23-133">[Coding a Custom Task](coding-a-custom-task.md) </span></span>  
 [<span data-ttu-id="c7d23-134">開發自訂工作的使用者介面</span><span class="sxs-lookup"><span data-stu-id="c7d23-134">Developing a User Interface for a Custom Task</span></span>](developing-a-user-interface-for-a-custom-task.md)  
  
  
