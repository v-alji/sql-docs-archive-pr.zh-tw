---
title: 格式化 Reporting Services 指令碼檔案 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- scripts [Reporting Services], formats
- formats [Reporting Services], script files
ms.assetid: 85a207dd-4e0f-4d40-a41e-0c75f65d719c
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c98a2f6561c3242fec34f7ca11c8304286ccebae
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87700726"
---
# <a name="format-a-reporting-services-script-file"></a><span data-ttu-id="e461b-102">格式化 Reporting Services 指令碼檔案</span><span class="sxs-lookup"><span data-stu-id="e461b-102">Format a Reporting Services Script File</span></span>
  <span data-ttu-id="e461b-103">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 指令碼是針對 Web Service Description Language (WSDL) 內建 Proxy 撰寫的 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic .NET 程式碼檔案，其中會定義 Reporting Services SOAP API。</span><span class="sxs-lookup"><span data-stu-id="e461b-103">A [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] script is a [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic .NET code file, written against a proxy that is built on Web Service Description Language (WSDL), which defines the Reporting Services SOAP API.</span></span> <span data-ttu-id="e461b-104">指令碼檔案會儲存為 Unicode 或 UTF-8 文字檔，且其副檔名為 .rss。</span><span class="sxs-lookup"><span data-stu-id="e461b-104">A script file is stored as a Unicode or UTF-8 text file with the extension .rss.</span></span>  
  
 <span data-ttu-id="e461b-105">指令碼檔案的用途如何 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 模組，而且可以包含使用者自訂程序和模組層次的變數。</span><span class="sxs-lookup"><span data-stu-id="e461b-105">The script file acts as a [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] module and can contain user-defined procedures and module-level variables.</span></span> <span data-ttu-id="e461b-106">若要讓指令碼檔案自動執行，則必須包含 Main 程序。</span><span class="sxs-lookup"><span data-stu-id="e461b-106">For the script file to run successfully, it must contain a Main procedure.</span></span> <span data-ttu-id="e461b-107">Main 程序是指令碼檔案執行時存取的第一個程序。</span><span class="sxs-lookup"><span data-stu-id="e461b-107">The Main procedure is the first procedure that is accessed when your script file runs.</span></span> <span data-ttu-id="e461b-108">Main 是您可以加入 Web 服務作業並執行使用者自訂子程序的地方。</span><span class="sxs-lookup"><span data-stu-id="e461b-108">Main is where you can add your Web service operations and run your user defined subprocedures.</span></span> <span data-ttu-id="e461b-109">下列程式碼會建立 Main 程序：</span><span class="sxs-lookup"><span data-stu-id="e461b-109">The following code creates a Main procedure:</span></span>  
  
```  
Public Sub Main()  
    ' Your code goes here.  
End Sub  
```  
  
 <span data-ttu-id="e461b-110">指令碼環境會自動連接到報表伺服器、建立 Web Proxy 類別，然後產生 Web 服務 Proxy 物件的參考變數 (*rs*)。</span><span class="sxs-lookup"><span data-stu-id="e461b-110">The script environment automatically connects to the report server, creates the Web proxy class, and generates a reference variable (*rs*) to the Web service proxy object.</span></span> <span data-ttu-id="e461b-111">您所建立的個別陳述式僅需要參考 *rs* 模組層次的變數，就能夠執行 Web 服務程式庫中提供的任何 Web 服務作業。</span><span class="sxs-lookup"><span data-stu-id="e461b-111">Individual statements that you create need only refer to the *rs* module-level variable to perform any of the Web service operations that are available in the Web service library.</span></span> <span data-ttu-id="e461b-112">下列 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 程式碼會從指令碼檔案內，呼叫 Web 服務的 <xref:ReportService2010.ReportingService2010.ListChildren%2A> 方法：</span><span class="sxs-lookup"><span data-stu-id="e461b-112">The following [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] code calls the Web service <xref:ReportService2010.ReportingService2010.ListChildren%2A> method from within a script file:</span></span>  
  
```  
Public Sub Main()  
    Dim items() As CatalogItem  
    items = rs.ListChildren("/", True)  
  
    Dim item As CatalogItem  
    For Each item In items  
        Console.WriteLine(item.Name)  
    Next item  
End Sub   
```  
  
> [!IMPORTANT]  
>  <span data-ttu-id="e461b-113">使用者認證會由指令碼環境所管理，並藉由使用 RS.exe，透過命令提示字元引數傳遞。</span><span class="sxs-lookup"><span data-stu-id="e461b-113">User credentials are managed by the script environment and passed through command prompt arguments through the use of RS.exe.</span></span> <span data-ttu-id="e461b-114">您可以使用 *rs* 變數來設定 Web 服務的驗證，但是建議您使用指令碼環境。</span><span class="sxs-lookup"><span data-stu-id="e461b-114">Although you can use the *rs* variable to set the authentication of the Web service, it is recommended that you use the script environment.</span></span> <span data-ttu-id="e461b-115">您不需要在指令碼檔案本身，驗證 Web 服務。</span><span class="sxs-lookup"><span data-stu-id="e461b-115">You do not need to authenticate the Web service in the script file itself.</span></span> <span data-ttu-id="e461b-116">如需有關驗證指令碼環境的詳細資訊，請參閱 [RS.exe 公用程式 &#40;SSRS&#41;](rs-exe-utility-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="e461b-116">For more information about authenticating the script environment, see [RS.exe Utility &#40;SSRS&#41;](rs-exe-utility-ssrs.md).</span></span>  
  
 <span data-ttu-id="e461b-117">您沒有宣告指令碼檔案內的命名空間。</span><span class="sxs-lookup"><span data-stu-id="e461b-117">You do not declare namespaces within the script file.</span></span> <span data-ttu-id="e461b-118">指令碼環境提供數個實用的 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 命名空間供您使用：**System.Web.Services**、**System.Web.Services.Protocols**、**System.Xml** 和 **System.IO**。</span><span class="sxs-lookup"><span data-stu-id="e461b-118">The scripting environment makes several useful [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] namespaces available to you: **System.Web.Services**, **System.Web.Services.Protocols**, **System.Xml**, and **System.IO**.</span></span>  
  
 <span data-ttu-id="e461b-119">如需指令碼範例，請參閱 [SQL Server Reporting Services 產品範例](https://go.microsoft.com/fwlink/?LinkId=177889)。</span><span class="sxs-lookup"><span data-stu-id="e461b-119">For script samples, see [SQL Server Reporting Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=177889).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e461b-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e461b-120">See Also</span></span>  
 <span data-ttu-id="e461b-121">[報表伺服器 Web 服務](../report-server-web-service/report-server-web-service.md) </span><span class="sxs-lookup"><span data-stu-id="e461b-121">[Report Server Web Service](../report-server-web-service/report-server-web-service.md) </span></span>  
 <span data-ttu-id="e461b-122">[技術參考 &#40;SSRS&#41;](../technical-reference-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="e461b-122">[Technical Reference &#40;SSRS&#41;](../technical-reference-ssrs.md) </span></span>  
 [<span data-ttu-id="e461b-123">RS.exe 公用程式 &#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="e461b-123">RS.exe Utility &#40;SSRS&#41;</span></span>](rs-exe-utility-ssrs.md)  
  
  
