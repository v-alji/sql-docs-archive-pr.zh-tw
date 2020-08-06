---
title: 建立 Web 服務 Proxy | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- Report Server Web service, proxies
- proxies [Reporting Services]
- XML Web service [Reporting Services], proxies
- Web service [Reporting Services], proxies
- Web references [Reporting Services]
ms.assetid: b1217843-8d3d-49f3-a0d2-d35b0db5b2df
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 0d080b96fa29e906c044561a684d58275af9f61e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688541"
---
# <a name="creating-the-web-service-proxy"></a><span data-ttu-id="cd61a-102">建立 Web 服務 Proxy</span><span class="sxs-lookup"><span data-stu-id="cd61a-102">Creating the Web Service Proxy</span></span>
  <span data-ttu-id="cd61a-103">用戶端與 Web 服務可以使用 SOAP 訊息來進行通訊，這會以 XML 來封裝輸入與輸出參數。</span><span class="sxs-lookup"><span data-stu-id="cd61a-103">A client and a Web service can communicate using SOAP messages, which encapsulate the input and output parameters as XML.</span></span> <span data-ttu-id="cd61a-104">Proxy 類別會將參數對應至 XML 元素，然後透過網路傳送 SOAP 訊息。</span><span class="sxs-lookup"><span data-stu-id="cd61a-104">A proxy class maps parameters to XML elements and then sends the SOAP messages over a network.</span></span> <span data-ttu-id="cd61a-105">以此方式，Proxy 類別可讓您免於在 SOAP 層級與 Web 服務通訊，並可讓您在任何支援 SOAP 與 Web 服務 Proxy 的開發環境中，叫用 Web 服務方法。</span><span class="sxs-lookup"><span data-stu-id="cd61a-105">In this way, the proxy class frees you from having to communicate with the Web service at the SOAP level and allows you to invoke Web service methods in any development environment that supports SOAP and Web service proxies.</span></span>  
  
 <span data-ttu-id="cd61a-106">有兩種方式可以使用將 proxy 類別加入至您的開發專案 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] ：使用中的 WSDL 工具 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] ，以及在中加入 Web 參考 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="cd61a-106">There are two ways to add a proxy class to your development project using the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]: with the WSDL tool in the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)], and by adding a Web reference in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)].</span></span> <span data-ttu-id="cd61a-107">下列小節針對這個主題進行更詳細的討論。</span><span class="sxs-lookup"><span data-stu-id="cd61a-107">The following sections discuss this subject in further detail.</span></span>  
  
## <a name="adding-the-proxy-using-the-wsdl-tool"></a><span data-ttu-id="cd61a-108">使用 WSDL 工具加入 Proxy</span><span class="sxs-lookup"><span data-stu-id="cd61a-108">Adding the Proxy Using the WSDL Tool</span></span>  
 <span data-ttu-id="cd61a-109">[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] SDK 包含 Web 服務描述語言工具 (Wsdl.exe)，這可讓您在 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 開發環境中產生要使用的 Web 服務 Proxy。</span><span class="sxs-lookup"><span data-stu-id="cd61a-109">The [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] SDK includes the Web Services Description Language tool (Wsdl.exe), which enables you to generate a Web service proxy for use in the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] development environment.</span></span> <span data-ttu-id="cd61a-110">以支援 Web 服務的語言建立用戶端 proxy 的最常見方式， (目前的 c # 和 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) 是使用 WSDL 工具。</span><span class="sxs-lookup"><span data-stu-id="cd61a-110">The most common way to create a client proxy in languages that support Web services (currently C# and [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) is to use the WSDL tool.</span></span>  
  
 <span data-ttu-id="cd61a-111">**使用 Wsdl.exe 將 Proxy 類別新增至專案**</span><span class="sxs-lookup"><span data-stu-id="cd61a-111">**To add a proxy class to your project using Wsdl.exe**</span></span>  
  
1.  <span data-ttu-id="cd61a-112">從命令提示，使用 Wsdl.exe 來建立 Proxy 類別，(至少) 將 URL 指定為報表伺服器 Web 服務。</span><span class="sxs-lookup"><span data-stu-id="cd61a-112">From a command prompt, use Wsdl.exe to create a proxy class, specifying (at a minimum) the URL to the Report Server Web service.</span></span>  
  
     <span data-ttu-id="cd61a-113">例如，下列命令提示陳述式會為報表伺服器 Web 服務的管理端點指定 URL：</span><span class="sxs-lookup"><span data-stu-id="cd61a-113">For example, the following command prompt statement specifies a URL for the management endpoint of the Report Server Web service:</span></span>  
  
    ```  
    wsdl /language:CS /n:"Microsoft.SqlServer.ReportingServices2010" http://<Server Name>/reportserver/reportservice2010.asmx?wsdl  
    ```  
  
     <span data-ttu-id="cd61a-114">WSDL 工具會接受一些命令提示引數以產生 Proxy。</span><span class="sxs-lookup"><span data-stu-id="cd61a-114">The WSDL tool accepts a number of command-prompt arguments for generating a proxy.</span></span> <span data-ttu-id="cd61a-115">上述範例會指定 C# 語言，這是要在 Proxy 中使用的建議命名空間 (如果使用一個以上的 Web 服務端點，便可防止名稱衝突)，並產生稱為 ReportingService2010.cs 的 C# 檔案。</span><span class="sxs-lookup"><span data-stu-id="cd61a-115">The preceding example specifies the language C#, a suggested namespace to use in the proxy (to prevent name collision if using more than one Web service endpoint), and generates a C# file called ReportingService2010.cs.</span></span> <span data-ttu-id="cd61a-116">如果範例已指定 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]，則此範例將會產生名為 ReportingService2010.vb 的 Proxy 檔案。</span><span class="sxs-lookup"><span data-stu-id="cd61a-116">If the example had specified [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)], the example would have generated a proxy file with the name ReportingService2010.vb.</span></span> <span data-ttu-id="cd61a-117">這個檔案是在您執行命令的目錄中建立。</span><span class="sxs-lookup"><span data-stu-id="cd61a-117">This file is created in the directory from which you run the command.</span></span>  
  
2.  <span data-ttu-id="cd61a-118">將 Proxy 類別編譯為組件檔 (使用副檔名 .dll) 並在專案中參考它，或是將類別加入為專案項目。</span><span class="sxs-lookup"><span data-stu-id="cd61a-118">Compile the proxy class into an assembly file (with the extension .dll) and reference it in your project, or add the class as a project item.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="cd61a-119">當您手動將 Proxy 類別加入專案，需要將參考加入 System.Web.Services.dll。</span><span class="sxs-lookup"><span data-stu-id="cd61a-119">When you add a proxy class to your project manually, you need to add a reference to System.Web.Services.dll.</span></span> <span data-ttu-id="cd61a-120">如果您在 Visual Studio .NET 中使用 Web 參考加入 Proxy，則會為您自動建立參考。</span><span class="sxs-lookup"><span data-stu-id="cd61a-120">If you add the proxy using a Web reference in Visual Studio .NET, the reference is automatically created for you.</span></span> <span data-ttu-id="cd61a-121">如需詳細資訊，請參閱本主題稍後的「在 Visual Studio 中使用 Web 參考加入 Proxy」。</span><span class="sxs-lookup"><span data-stu-id="cd61a-121">For more information, see "Adding the Proxy Using a Web Reference in Visual Studio" later in this topic.</span></span>  
  
     <span data-ttu-id="cd61a-122">在將 Proxy 類別以項目的方式加入專案之後，相關聯的檔案會出現在 [方案總管] 中。</span><span class="sxs-lookup"><span data-stu-id="cd61a-122">After you add the proxy class as an item to your project, the associated file appears in Solution Explorer.</span></span>  
  
3.  <span data-ttu-id="cd61a-123">若要以程式設計的方式呼叫服務，請建立 Proxy 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="cd61a-123">To call the service programmatically, create an instance of the proxy class.</span></span>  
  
     <span data-ttu-id="cd61a-124">下列程式碼範例示範在專案中建立 <xref:ReportService2010.ReportingService2010> Proxy 類別之執行個體的語法：</span><span class="sxs-lookup"><span data-stu-id="cd61a-124">The following code example shows the syntax for creating an instance of the <xref:ReportService2010.ReportingService2010> proxy class in a project:</span></span>  
  
```vb  
Dim service As New ReportingService2010()  
```  
  
```csharp  
ReportingService2010 service = new ReportingService2010();  
  
```  
  
 <span data-ttu-id="cd61a-125">如需有關 Wsdl.exe 工具 (包括其完整的語法) 的詳細資訊，請參閱 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] SDK 文件集中的＜Web 服務描述語言工具＞。</span><span class="sxs-lookup"><span data-stu-id="cd61a-125">For more information about the Wsdl.exe tool, including its full syntax, see "Web Services Description Language Tool" in the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] SDK documentation.</span></span> <span data-ttu-id="cd61a-126">如需 Web 服務 Proxy 的完整說明，請參閱 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] SDK 文件集中的＜建立 XML Web 服務 Proxy＞。</span><span class="sxs-lookup"><span data-stu-id="cd61a-126">For a full explanation of Web service proxies, see "Creating an XML Web Service Proxy" in the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] SDK documentation.</span></span>  
  
## <a name="adding-the-proxy-using-a-web-reference-in-visual-studio"></a><span data-ttu-id="cd61a-127">使用 Visual Studio 中的 Web 參考來加入 Proxy</span><span class="sxs-lookup"><span data-stu-id="cd61a-127">Adding the Proxy Using a Web Reference in Visual Studio</span></span>  
 <span data-ttu-id="cd61a-128">Web 參考可讓專案取用一個或多個 Web 服務。</span><span class="sxs-lookup"><span data-stu-id="cd61a-128">A Web reference enables a project to consume one or more Web services.</span></span> [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] <span data-ttu-id="cd61a-129">可讓使用者遵循一些簡單的步驟，將 Web 服務參考加入專案中。</span><span class="sxs-lookup"><span data-stu-id="cd61a-129">enables users to add Web service references to projects by following a few simple steps.</span></span>  
  
 <span data-ttu-id="cd61a-130">**將 Web 參考新增至專案**</span><span class="sxs-lookup"><span data-stu-id="cd61a-130">**To add a Web reference to a project**</span></span>  
  
1.  <span data-ttu-id="cd61a-131">在**方案總管**中，選取將取用 Web 服務的專案。</span><span class="sxs-lookup"><span data-stu-id="cd61a-131">In **Solution Explorer**, select the project that will consume the Web service.</span></span>  
  
2.  <span data-ttu-id="cd61a-132">在 [專案]\*\*\*\* 功能表上，按一下 [新增 Web 參考]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="cd61a-132">On the **Project** menu, click **Add Web Reference**.</span></span>  
  
     <span data-ttu-id="cd61a-133">[新增 Web 參考]\*\*\*\* 對話方塊隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="cd61a-133">The **Add Web Reference** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="cd61a-134">在 [URL]\*\*\*\* 欄位中，輸入報表伺服器 Web 服務的完整路徑。</span><span class="sxs-lookup"><span data-stu-id="cd61a-134">In the **URL** field, enter the complete path to the Report Server Web service.</span></span>  
  
     <span data-ttu-id="cd61a-135">報表伺服器 Web 服務的報表執行端點之簡化的 URL，可能如下所示：</span><span class="sxs-lookup"><span data-stu-id="cd61a-135">A simplified URL for the report execution endpoint of the Report Server Web service might look like this:</span></span>  
  
    ```  
    http://<Server Name>/reportserver/reportexecution2005.asmx  
    ```  
  
     <span data-ttu-id="cd61a-136">這個 URL 包含部署報表伺服器 Web 服務的網域、包含服務的資料夾名稱，以及服務的探索檔名稱。</span><span class="sxs-lookup"><span data-stu-id="cd61a-136">The URL contains the domain in which the Report Server Web service is deployed, the name of the folder containing the service, and the name of the discovery file for the service.</span></span> <span data-ttu-id="cd61a-137">如需不同 URL 項目的完整描述，請參閱[存取 SOAP API](../accessing-the-soap-api.md)。</span><span class="sxs-lookup"><span data-stu-id="cd61a-137">For a complete description of the different URL elements, see [Accessing the SOAP API](../accessing-the-soap-api.md).</span></span>  
  
     <span data-ttu-id="cd61a-138">Web 服務提供的方法與屬性之描述會出現在左邊的 [瀏覽器] 窗格中。</span><span class="sxs-lookup"><span data-stu-id="cd61a-138">A description of the methods and properties provided by the Web service appears in the Browser pane on the left.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="cd61a-139">如需與報表伺服器 Web 服務建立關聯之項目的詳細資訊，請參閱[報表伺服器 Web 服務方法](../methods/report-server-web-service-methods.md)。</span><span class="sxs-lookup"><span data-stu-id="cd61a-139">For more information about the items associated with the Report Server Web service, see [Report Server Web Service Methods](../methods/report-server-web-service-methods.md).</span></span>  
  
4.  <span data-ttu-id="cd61a-140">請確認您的專案可以使用報表伺服器 Web 服務，而且您有適當的權限可以存取報表伺服器。</span><span class="sxs-lookup"><span data-stu-id="cd61a-140">Verify that your project can use the Report Server Web service, and that you have appropriate permission to access the report server.</span></span>  
  
5.  <span data-ttu-id="cd61a-141">在 [Web 參考名稱]\*\*\*\* 欄位中，輸入在程式碼中將以程式設計方式存取報表伺服器 Web 服務所使用的名稱。</span><span class="sxs-lookup"><span data-stu-id="cd61a-141">In the **Web reference name** field, enter a name that you will use in your code to access the Report Server Web service programmatically.</span></span>  
  
6.  <span data-ttu-id="cd61a-142">選取 [新增參考]\*\*\*\* 按鈕，在應用程式中建立對 Web 服務的參考。</span><span class="sxs-lookup"><span data-stu-id="cd61a-142">Select the **Add Reference** button to create a reference in your application to the Web service.</span></span>  
  
     <span data-ttu-id="cd61a-143">[Web 參考名稱]\*\*\*\* 欄位中所指定名稱的新參考，將出現於**方案總管**中使用中專案的 [Web 參考] 節點之下。</span><span class="sxs-lookup"><span data-stu-id="cd61a-143">The new reference appears in **Solution Explorer** under the Web References node for the active project, named as specified in the **Web reference name** field.</span></span>  
  
7.  <span data-ttu-id="cd61a-144">在**方案總管**中，展開 [Web 參考] 資料夾，以寫下在專案中項目的可用 Web 參考類別之命名空間。</span><span class="sxs-lookup"><span data-stu-id="cd61a-144">In **Solution Explorer**, expand the Web References folder to note the namespace for the Web reference classes that are available to the items in your project.</span></span>  
  
     <span data-ttu-id="cd61a-145">在將 Web 參考新增專案之後，會在**方案總管**的 [Web 參考] 資料夾的某個資料夾中顯示相關聯的檔案。</span><span class="sxs-lookup"><span data-stu-id="cd61a-145">After adding a Web reference to your project, the associated files are displayed in a folder within the Web References folder of **Solution Explorer**.</span></span>  
  
 <span data-ttu-id="cd61a-146">在加入 Web 參考之後，請使用下列語法建立 Proxy 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="cd61a-146">After you add the Web reference, use the following syntax to create an instance of the proxy class:</span></span>  
  
```vb  
Dim rs As New myNamespace.myReferenceName.ReportExecutionService()  
rs.Url = "http://<Server Name>/reportserver/reportexecution2005.asmx?wsdl"  
rs.Credentials = System.Net.CredentialCache.DefaultCredentials  
```  
  
```csharp  
myNamespace.myReferenceName.ReportExecutionService rs = new myNamespace.myReferenceName.ReportExecutionService();  
rs.Url = "http://<Server Name>/reportserver/reportexecution2005.asmx?wsdl"  
rs.Credentials = System.Net.CredentialCache.DefaultCredentials  
  
```  
  
 <span data-ttu-id="cd61a-147">您也可以將 **using** (在 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] 中為**匯入**) 指示詞新增報表伺服器 Web 服務參考。</span><span class="sxs-lookup"><span data-stu-id="cd61a-147">You can also add a **using** (**Import** in [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) directive to the Report Server Web service reference.</span></span> <span data-ttu-id="cd61a-148">如果您使用這個指示詞，就不需要完全符合命名空間的類型。</span><span class="sxs-lookup"><span data-stu-id="cd61a-148">If you use this directive, you do not need to fully qualify the types in the namespace.</span></span> <span data-ttu-id="cd61a-149">若要這樣做，請將下列程式碼加入檔案中：</span><span class="sxs-lookup"><span data-stu-id="cd61a-149">To do this, add the following code to your file:</span></span>  
  
```vb  
Import myNamespace.myReferenceName  
```  
  
```csharp  
using myNamespace.myReferenceName;  
```  
  
## <a name="see-also"></a><span data-ttu-id="cd61a-150">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cd61a-150">See Also</span></span>  
 <span data-ttu-id="cd61a-151">[報表伺服器 Web 服務](../report-server-web-service.md) </span><span class="sxs-lookup"><span data-stu-id="cd61a-151">[Report Server Web Service](../report-server-web-service.md) </span></span>  
 <span data-ttu-id="cd61a-152">[使用 Web 服務和 .NET Framework 建置應用程式](building-applications-using-the-web-service-and-the-net-framework.md) </span><span class="sxs-lookup"><span data-stu-id="cd61a-152">[Building Applications Using the Web Service and the .NET Framework](building-applications-using-the-web-service-and-the-net-framework.md) </span></span>  
 [<span data-ttu-id="cd61a-153">技術參考 &#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="cd61a-153">Technical Reference &#40;SSRS&#41;</span></span>](../../technical-reference-ssrs.md)  
  
  
