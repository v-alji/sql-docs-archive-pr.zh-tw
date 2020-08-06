---
title: 建立自訂連線管理員 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- custom connection managers [Integration Services], creating
ms.assetid: e83f8e02-ace4-42e0-b979-2f6be1460985
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 857efebbe311e5510e15cae9e78a2b424559ded7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709774"
---
# <a name="creating-a-custom-connection-manager"></a><span data-ttu-id="d0df2-102">建立自訂連接管理員</span><span class="sxs-lookup"><span data-stu-id="d0df2-102">Creating a Custom Connection Manager</span></span>
  <span data-ttu-id="d0df2-103">建立自訂連接管理員的步驟，與建立 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 之其他自訂物件的步驟類似：</span><span class="sxs-lookup"><span data-stu-id="d0df2-103">The steps that you must follow to create a custom connection manager are similar to the steps for creating any other custom object for [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]:</span></span>  
  
-   <span data-ttu-id="d0df2-104">建立繼承自基底類別的新類別。</span><span class="sxs-lookup"><span data-stu-id="d0df2-104">Create a new class that inherits from the base class.</span></span> <span data-ttu-id="d0df2-105">對於連接管理員而言，基底類別是 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase>。</span><span class="sxs-lookup"><span data-stu-id="d0df2-105">For a connection manager, the base class is <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase>.</span></span>  
  
-   <span data-ttu-id="d0df2-106">將可識別物件類型的屬性套用至類別。</span><span class="sxs-lookup"><span data-stu-id="d0df2-106">Apply the attribute that identifies the type of object to the class.</span></span> <span data-ttu-id="d0df2-107">對於連接管理員而言，屬性是 <xref:Microsoft.SqlServer.Dts.Runtime.DtsConnectionAttribute>。</span><span class="sxs-lookup"><span data-stu-id="d0df2-107">For a connection manager, the attribute is <xref:Microsoft.SqlServer.Dts.Runtime.DtsConnectionAttribute>.</span></span>  
  
-   <span data-ttu-id="d0df2-108">覆寫基底類別之方法與屬性的實作。</span><span class="sxs-lookup"><span data-stu-id="d0df2-108">Override the implementation of the methods and properties of the base class.</span></span> <span data-ttu-id="d0df2-109">對於連接管理員而言，這些包括 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.ConnectionString%2A> 屬性以及 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.AcquireConnection%2A> 與 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.ReleaseConnection%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="d0df2-109">For a connection manager, these include the <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.ConnectionString%2A> property and the <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.AcquireConnection%2A> and <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.ReleaseConnection%2A> methods.</span></span>  
  
-   <span data-ttu-id="d0df2-110">(選擇性) 開發自訂使用者介面。</span><span class="sxs-lookup"><span data-stu-id="d0df2-110">Optionally, develop a custom user interface.</span></span> <span data-ttu-id="d0df2-111">對於連接管理員而言，這需要實作 <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsConnectionManagerUI> 介面的類別。</span><span class="sxs-lookup"><span data-stu-id="d0df2-111">For a connection manager, this requires a class that implements the <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsConnectionManagerUI> interface.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d0df2-112">已經建置到 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 中的大多數工作、來源和目的地只能搭配特定類型的內建連接管理員一起使用。</span><span class="sxs-lookup"><span data-stu-id="d0df2-112">Most of the tasks, sources, and destinations that have been built into [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] work only with specific types of built-in connection managers.</span></span> <span data-ttu-id="d0df2-113">因此，不能使用內建工作和元件來測試這些範例。</span><span class="sxs-lookup"><span data-stu-id="d0df2-113">Therefore, these samples cannot be tested with the built-in tasks and components.</span></span>  
  
## <a name="getting-started-with-a-custom-connection-manager"></a><span data-ttu-id="d0df2-114">開始使用自訂連接管理員</span><span class="sxs-lookup"><span data-stu-id="d0df2-114">Getting Started with a Custom Connection Manager</span></span>  
  
### <a name="creating-projects-and-classes"></a><span data-ttu-id="d0df2-115">建立專案和類別</span><span class="sxs-lookup"><span data-stu-id="d0df2-115">Creating Projects and Classes</span></span>  
 <span data-ttu-id="d0df2-116">因為所有的 Managed 連接管理員都是從 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase> 基底類別衍生，所以建立自訂連接管理員的第一個步驟是以慣用的 Managed 程式語言建立類別庫專案，並建立繼承自基底類別的類別。</span><span class="sxs-lookup"><span data-stu-id="d0df2-116">Because all managed connection managers derive from the <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase> base class, the first step when you create a custom connection manager is to create a class library project in your preferred managed programming language and create a class that inherits from the base class.</span></span> <span data-ttu-id="d0df2-117">在此衍生的類別中，您將覆寫基底類別的方法與屬性，以實作自訂功能。</span><span class="sxs-lookup"><span data-stu-id="d0df2-117">In this derived class, you will override the methods and properties of the base class to implement your custom functionality.</span></span>  
  
 <span data-ttu-id="d0df2-118">在相同的方案中，為自訂使用者介面建立另一個類別庫專案。</span><span class="sxs-lookup"><span data-stu-id="d0df2-118">In the same solution, create a second class library project for the custom user interface.</span></span> <span data-ttu-id="d0df2-119">之所以建議您為使用者介面建立個別的組件，是因為它可讓您分別更新和重新部署連接管理員或其使用者介面，從而簡化部署的工作。</span><span class="sxs-lookup"><span data-stu-id="d0df2-119">A separate assembly for the user interface is recommended for ease of deployment because it lets you update and redeploy the connection manager or its user interface independently.</span></span>  
  
 <span data-ttu-id="d0df2-120">透過使用強式名稱金鑰檔案，將兩個專案都設定成簽署將在建立時期產生的組件。</span><span class="sxs-lookup"><span data-stu-id="d0df2-120">Configure both projects to sign the assemblies that will be generated at build time by using a strong name key file.</span></span>  
  
### <a name="applying-the-dtsconnection-attribute"></a><span data-ttu-id="d0df2-121">套用 DtsConnection 屬性</span><span class="sxs-lookup"><span data-stu-id="d0df2-121">Applying the DtsConnection Attribute</span></span>  
 <span data-ttu-id="d0df2-122">將 <xref:Microsoft.SqlServer.Dts.Runtime.DtsConnectionAttribute> 屬性套用至您已建立的類別，以便將它識別為連接管理員。</span><span class="sxs-lookup"><span data-stu-id="d0df2-122">Apply the <xref:Microsoft.SqlServer.Dts.Runtime.DtsConnectionAttribute> attribute to the class that you have created to identify it as a connection manager.</span></span> <span data-ttu-id="d0df2-123">此屬性會提供連接管理員的名稱、描述和連接類型等設計階段資訊。</span><span class="sxs-lookup"><span data-stu-id="d0df2-123">This attribute provides design-time information such as the name, description, and connection type of the connection manager.</span></span> <span data-ttu-id="d0df2-124"><xref:Microsoft.SqlServer.Dts.Runtime.DtsConnectionAttribute.ConnectionType%2A>和 `Description` 屬性會對應至**Type** `Description` [**加入 SSIS 連接管理員**] 對話方塊中顯示的類型和資料行，這會在中為封裝設定連接時顯示 [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="d0df2-124">The <xref:Microsoft.SqlServer.Dts.Runtime.DtsConnectionAttribute.ConnectionType%2A> and `Description` properties correspond to the **Type** and `Description` columns displayed in the **Add SSIS Connection Manager** dialog box, which is displayed when configuring connections for a package in [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="d0df2-125">使用 <xref:Microsoft.SqlServer.Dts.Runtime.DtsConnectionAttribute.UITypeName%2A> 屬性將連接管理員連結至其自訂使用者介面。</span><span class="sxs-lookup"><span data-stu-id="d0df2-125">Use the <xref:Microsoft.SqlServer.Dts.Runtime.DtsConnectionAttribute.UITypeName%2A> property to link the connection manager to its custom user interface.</span></span> <span data-ttu-id="d0df2-126">如需取得此屬性所需的公開金鑰權杖，可以使用 **sn.exe -t**，從要用於簽署使用者介面組件的金鑰組 (.snk) 檔案顯示公開金鑰權杖。</span><span class="sxs-lookup"><span data-stu-id="d0df2-126">To obtain the public key token that is required for this property, you an use **sn.exe -t** to display the public key token from the key pair (.snk) file that you intend to use to sign the user interface assembly.</span></span>  
  
```vb  
<DtsConnection(ConnectionType:="SQLVB", _  
  DisplayName:="SqlConnectionManager (VB)", _  
  Description:="Connection manager for Sql Server", _  
  UITypeName:="SqlConnMgrUIVB.SqlConnMgrUIVB,SqlConnMgrUIVB,Version=1.0.0.0,Culture=neutral,PublicKeyToken=<insert public key token here>")> _  
Public Class SqlConnMgrVB  
  Inherits ConnectionManagerBase  
  . . .  
End Class  
```  
  
```csharp  
[DtsConnection(ConnectionType = "SQLCS",  
  DisplayName = "SqlConnectionManager (CS)",  
  Description = "Connection manager for Sql Server",  
  UITypeName = "SqlConnMgrUICS.SqlConnMgrUICS,SqlConnMgrUICS,Version=1.0.0.0,Culture=neutral,PublicKeyToken=<insert public key token here>")]  
public class SqlConnMgrCS :  
ConnectionManagerBase  
{  
  . . .  
}  
```  
  
## <a name="building-deploying-and-debugging-a-custom-connection-manager"></a><span data-ttu-id="d0df2-127">建立、部署和偵錯自訂連接管理員</span><span class="sxs-lookup"><span data-stu-id="d0df2-127">Building, Deploying, and Debugging a Custom Connection Manager</span></span>  
 <span data-ttu-id="d0df2-128">在 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 中建立、部署和偵錯自訂連接管理員的步驟，類似於其他類型的自訂物件所需的步驟。</span><span class="sxs-lookup"><span data-stu-id="d0df2-128">The steps for building, deploying, and debugging a custom connection manager in [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] are similar to the steps for other types of custom objects.</span></span> <span data-ttu-id="d0df2-129">如需詳細資訊，請參閱[建立、部署和偵錯自訂物件](../building-deploying-and-debugging-custom-objects.md)。</span><span class="sxs-lookup"><span data-stu-id="d0df2-129">For more information, see [Building, Deploying, and Debugging Custom Objects](../building-deploying-and-debugging-custom-objects.md).</span></span>  
  
<span data-ttu-id="d0df2-130">![Integration Services 圖示 (小型) ](../../media/dts-16.gif "Integration Services 圖示 (小)")會**保持最**新狀態 Integration Services  </span><span class="sxs-lookup"><span data-stu-id="d0df2-130">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="d0df2-131">若要取得 Microsoft 的最新下載、文件、範例和影片以及社群中的精選解決方案，請瀏覽 MSDN 上的 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 頁面：</span><span class="sxs-lookup"><span data-stu-id="d0df2-131">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="d0df2-132">瀏覽 MSDN 上的 Integration Services 頁面</span><span class="sxs-lookup"><span data-stu-id="d0df2-132">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="d0df2-133">若要得到這些更新的自動通知，請訂閱該頁面上所提供的 RSS 摘要。</span><span class="sxs-lookup"><span data-stu-id="d0df2-133">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0df2-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d0df2-134">See Also</span></span>  
 <span data-ttu-id="d0df2-135">[撰寫自訂連線管理員的程式碼](coding-a-custom-connection-manager.md) </span><span class="sxs-lookup"><span data-stu-id="d0df2-135">[Coding a Custom Connection Manager](coding-a-custom-connection-manager.md) </span></span>  
 [<span data-ttu-id="d0df2-136">開發自訂連接管理員的使用者介面</span><span class="sxs-lookup"><span data-stu-id="d0df2-136">Developing a User Interface for a Custom Connection Manager</span></span>](developing-a-user-interface-for-a-custom-connection-manager.md)  
  
  
