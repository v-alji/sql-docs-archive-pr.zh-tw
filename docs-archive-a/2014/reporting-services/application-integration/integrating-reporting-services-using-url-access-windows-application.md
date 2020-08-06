---
title: 在 Windows 應用程式中使用 URL 存取 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- Windows applications [Reporting Services]
- Web Browser controls [Reporting Services]
- Windows Forms [Reporting Services]
- browser controls [Reporting Services]
- URL access [Reporting Services], Windows applications
ms.assetid: a4b222e5-0cbd-409c-92c4-046a674db8ac
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 8f8b901481b1d6fcc3cdd8626b43cd3a69174c1a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703961"
---
# <a name="using-url-access-in-a-windows-application"></a><span data-ttu-id="7f5c8-102">在 Windows 應用程式中使用 URL 存取</span><span class="sxs-lookup"><span data-stu-id="7f5c8-102">Using URL Access in a Windows Application</span></span>
  <span data-ttu-id="7f5c8-103">雖然會為 Web 環境最佳化報表伺服器的 URL 存取，不過，您也可以使用 URL 存取來將 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 報表內嵌到 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 應用程式。</span><span class="sxs-lookup"><span data-stu-id="7f5c8-103">Although URL access to a report server is optimized for a Web environment, you can also use URL access to embed [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] reports into a [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows application.</span></span> <span data-ttu-id="7f5c8-104">不過，需要 Windows Form 的 URL 存取仍然需要您使用網頁瀏覽器技術。</span><span class="sxs-lookup"><span data-stu-id="7f5c8-104">However, URL access that involves Windows Forms still requires that you use Web browser technology.</span></span> <span data-ttu-id="7f5c8-105">您可以透過 URL 存取與 Windows Form 使用下列整合案例：</span><span class="sxs-lookup"><span data-stu-id="7f5c8-105">You can use the following integration scenarios with URL access and Windows Forms:</span></span>  
  
-   <span data-ttu-id="7f5c8-106">透過以程式設計方式啟動網頁瀏覽器，來顯示 Windows Form 應用程式中的報表。</span><span class="sxs-lookup"><span data-stu-id="7f5c8-106">Display a report from a Windows Form application by starting a Web browser programmatically.</span></span>  
  
-   <span data-ttu-id="7f5c8-107">使用 Windows Form 上的 <xref:System.Windows.Forms.WebBrowser> 控制項顯示報表。</span><span class="sxs-lookup"><span data-stu-id="7f5c8-107">Use the <xref:System.Windows.Forms.WebBrowser> control on a Windows Form to display a report.</span></span>  
  
## <a name="starting-internet-explorer-from-a-windows-form"></a><span data-ttu-id="7f5c8-108">從 Windows Form 啟動 Internet Explorer</span><span class="sxs-lookup"><span data-stu-id="7f5c8-108">Starting Internet Explorer from a Windows Form</span></span>  
 <span data-ttu-id="7f5c8-109">您可以使用 <xref:System.Diagnostics.Process> 類別來存取正在電腦上執行的處理序。</span><span class="sxs-lookup"><span data-stu-id="7f5c8-109">You can use the <xref:System.Diagnostics.Process> class to access a process that is running on a computer.</span></span> <span data-ttu-id="7f5c8-110"><xref:System.Diagnostics.Process>類別是用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 來啟動、停止、控制和監視應用程式的實用結構。</span><span class="sxs-lookup"><span data-stu-id="7f5c8-110">The <xref:System.Diagnostics.Process> class is a useful [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] construct for starting, stopping, controlling, and monitoring applications.</span></span> <span data-ttu-id="7f5c8-111">若要監視在報表伺服器資料庫中的特定報表，您可以啟動 **IExplore** 處理序，將 URL 傳遞給報表。</span><span class="sxs-lookup"><span data-stu-id="7f5c8-111">To view a specific report in your report server database, you can start the **IExplore** process, passing in the URL to the report.</span></span> <span data-ttu-id="7f5c8-112">下列程式碼範例可用以啟動 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Internet Explorer，並在使用者按一下 Windows Form 上的按鈕時，傳遞特定的報表 URL。</span><span class="sxs-lookup"><span data-stu-id="7f5c8-112">The following code example can be used to start [!INCLUDE[msCoName](../../includes/msconame-md.md)] Internet Explorer and pass a specific report URL when the user clicks a button on a Windows Form.</span></span>  
  
```vb  
Private Sub viewReportButton_Click(ByVal sender As Object, ByVal e As System.EventArgs) Handles viewReportButton.Click  
   ' Build the URL access string based on values supplied by a user  
   Dim url As String = serverUrlTextBox.Text + "?" & reportPathTextBox.Text & _  
   "&rs:Command=Render" & "&rs:Format=HTML4.0"  
  
   ' If the user does not select the toolbar check box,  
   ' turn the toolbar off in the HTML Viewer  
   If toolbarCheckBox.Checked = False Then  
      url += "&rc:Toolbar=False"  
   End If  
   ' load report in the Web browser  
   Try  
      System.Diagnostics.Process.Start("IExplore", url)  
   Catch  
      MessageBox.Show("The system could not start the specified report using Internet Explorer.", _  
      "An error has occurred", MessageBoxButtons.OK, MessageBoxIcon.Error)  
   End Try  
End Sub 'viewReportButton_Click  
```  
  
```csharp  
// Sample click event for a Button control on a Windows Form  
private void viewReportButton_Click(object sender, System.EventArgs e)  
{  
   // Build the URL access string based on values supplied by a user  
   string url = serverUrlTextBox.Text + "?" + reportPathTextBox.Text +  
      "&rs:Command=Render" + "&rs:Format=HTML4.0";  
  
   // If the user does not check the toolbar check box,  
   // turn the toolbar off in the HTML Viewer  
   if (toolbarCheckBox.Checked == false)  
      url += "&rc:Toolbar=False";  
  
   // load report in the Web browser  
   try  
   {  
      System.Diagnostics.Process.Start("IExplore", url);  
   }  
  
   catch (Exception)  
   {  
      MessageBox.Show(  
         "The system could not open the specified report using Internet Explorer.",   
         "An error has occurred", MessageBoxButtons.OK, MessageBoxIcon.Error);  
   }  
}  
```  
  
## <a name="embedding-a-browser-control-on-a-windows-form"></a><span data-ttu-id="7f5c8-113">在 Windows Form 上內嵌瀏覽器控制項</span><span class="sxs-lookup"><span data-stu-id="7f5c8-113">Embedding a Browser Control on a Windows Form</span></span>  
 <span data-ttu-id="7f5c8-114">如果您不想在外部網頁瀏覽器中檢視報表，可以使用 <xref:System.Windows.Forms.WebBrowser> 控制項將網頁瀏覽器緊密地內嵌成為 Windows Form 的一部分。</span><span class="sxs-lookup"><span data-stu-id="7f5c8-114">If you do not want to view your report in an external Web browser, you can embed a Web browser seamlessly as part of your Windows Form using the <xref:System.Windows.Forms.WebBrowser> control.</span></span>  
  
###### <a name="to-add-the-webbrowser-control-to-your-windows-form"></a><span data-ttu-id="7f5c8-115">將 WebBrowser 控制項加入 Windows Form</span><span class="sxs-lookup"><span data-stu-id="7f5c8-115">To add the WebBrowser control to your Windows Form</span></span>  
  
1.  <span data-ttu-id="7f5c8-116">在或中建立新的 Windows 應用程式 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[csprcs](../../includes/csprcs-md.md)] [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="7f5c8-116">Create a new Windows application in either [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[csprcs](../../includes/csprcs-md.md)] or [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)].</span></span>  
  
2.  <span data-ttu-id="7f5c8-117">在 [工具箱]\*\*\*\* 對話方塊中找出 <xref:System.Windows.Forms.WebBrowser> 控制項。</span><span class="sxs-lookup"><span data-stu-id="7f5c8-117">Locate the <xref:System.Windows.Forms.WebBrowser> control in the **Toolbox** Dialog Box.</span></span>  
  
     <span data-ttu-id="7f5c8-118">如果看不到 [工具箱]\*\*\*\*，可以按一下 [檢視]\*\*\*\* 功能表項目，並選取 [工具箱]\*\*\*\* 來存取。</span><span class="sxs-lookup"><span data-stu-id="7f5c8-118">If the **Toolbox** is not visible you can access it by clicking the **View** menu item and selecting **Toolbox**.</span></span>  
  
3.  <span data-ttu-id="7f5c8-119">將 <xref:System.Windows.Forms.WebBrowser> 控制項拖曳至 Windows Form 的設計介面。</span><span class="sxs-lookup"><span data-stu-id="7f5c8-119">Drag the <xref:System.Windows.Forms.WebBrowser>control onto the design surface of your Windows Form.</span></span>  
  
     <span data-ttu-id="7f5c8-120">名為 webBrowser1 的 <xref:System.Windows.Forms.WebBrowser> 控制項會新增至 Form</span><span class="sxs-lookup"><span data-stu-id="7f5c8-120">The <xref:System.Windows.Forms.WebBrowser>control named webBrowser1 is added to the Form</span></span>  
  
 <span data-ttu-id="7f5c8-121">您可以呼叫其 **Navigate** 方法，將 <xref:System.Windows.Forms.WebBrowser> 控制項導向 URL。</span><span class="sxs-lookup"><span data-stu-id="7f5c8-121">You direct the <xref:System.Windows.Forms.WebBrowser> control to a URL by calling its **Navigate** method.</span></span> <span data-ttu-id="7f5c8-122">您可以在執行階段將特定的 URL 存取字串指派到 <xref:System.Windows.Forms.WebBrowser> 控制項，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="7f5c8-122">You can assign a specific URL access string to your <xref:System.Windows.Forms.WebBrowser> control at run time as shown in the following example.</span></span>  
  
```vb  
Dim url As String = "http://localhost/reportserver?/" & _  
                    "AdventureWorks2012 Sample Reports/" & _  
                    "Company Sales&rs:Command=Render"  
WebBrowser1.Navigate(url)  
```  
  
```csharp  
string url = "http://localhost/reportserver?/" +  
             "AdventureWorks2012 Sample Reports/" +  
             "Company Sales&rs:Command=Render";  
webBrowser1.Navigate(url);  
```  
  
## <a name="see-also"></a><span data-ttu-id="7f5c8-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7f5c8-123">See Also</span></span>  
 <span data-ttu-id="7f5c8-124">[將 Reporting Services 整合至應用程式](../application-integration/integrating-reporting-services-into-applications.md) </span><span class="sxs-lookup"><span data-stu-id="7f5c8-124">[Integrating Reporting Services into Applications](../application-integration/integrating-reporting-services-into-applications.md) </span></span>  
 <span data-ttu-id="7f5c8-125">[使用 URL 存取來整合 Reporting Services](integrating-reporting-services-using-url-access.md) </span><span class="sxs-lookup"><span data-stu-id="7f5c8-125">[Integrating Reporting Services Using URL Access](integrating-reporting-services-using-url-access.md) </span></span>  
 <span data-ttu-id="7f5c8-126">[使用 SOAP 整合 Reporting Services](integrating-reporting-services-using-soap.md) </span><span class="sxs-lookup"><span data-stu-id="7f5c8-126">[Integrating Reporting Services Using SOAP](integrating-reporting-services-using-soap.md) </span></span>  
 <span data-ttu-id="7f5c8-127">[使用 ReportViewer 控制項整合 Reporting Services](integrating-reporting-services-using-reportviewer-controls.md) </span><span class="sxs-lookup"><span data-stu-id="7f5c8-127">[Integrating Reporting Services Using the ReportViewer Controls](integrating-reporting-services-using-reportviewer-controls.md) </span></span>  
 [<span data-ttu-id="7f5c8-128">URL 存取 &#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="7f5c8-128">URL Access &#40;SSRS&#41;</span></span>](../url-access-ssrs.md)  
  
  
