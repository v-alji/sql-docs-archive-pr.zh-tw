---
title: 第1課：建立 RDL 架構 Visual Studio 專案 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: f420509c-51aa-4170-8c25-64c2954f4bb9
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: a8411e3f0458ccda8c291d5c86a4467bb051a263
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686569"
---
# <a name="lesson-1-create-the-rdl-schema-visual-studio-project"></a><span data-ttu-id="a12f1-102">第 1 課：建立 RDL 結構描述 Visual Studio 專案</span><span class="sxs-lookup"><span data-stu-id="a12f1-102">Lesson 1: Create the RDL Schema Visual Studio Project</span></span>
  <span data-ttu-id="a12f1-103">在這個教學課程中，您會建立簡單的主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="a12f1-103">For this tutorial, you will create a simple console application.</span></span> <span data-ttu-id="a12f1-104">本教學課程假設您是在中進行開發 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="a12f1-104">This tutorial assumes you are developing in [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)].</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a12f1-105">當您存取在 [!INCLUDE[ssExpress](../includes/ssexpress-md.md)] with Advanced Services 上執行的報表伺服器 Web 服務時，必須將 "_SQLExpress" 附加至 "ReportServer" 路徑。</span><span class="sxs-lookup"><span data-stu-id="a12f1-105">When accessing the Report Server Web service running on [!INCLUDE[ssExpress](../includes/ssexpress-md.md)] with Advanced Services, you must append "_SQLExpress" to the "ReportServer" path.</span></span> <span data-ttu-id="a12f1-106">例如：</span><span class="sxs-lookup"><span data-stu-id="a12f1-106">For example:</span></span>  
>   
>  `http://myserver/reportserver_sqlexpress/reportservice2010.asmx"`  
  
### <a name="to-create-the-web-service-proxy"></a><span data-ttu-id="a12f1-107">若要建立 Web 服務 Proxy</span><span class="sxs-lookup"><span data-stu-id="a12f1-107">To create the web service proxy</span></span>  
  
1.  <span data-ttu-id="a12f1-108">在 [**開始**] 功能表中，依序選取 [**所有程式**] 和 [Microsoft Visual Studio]，然後**Visual Studio Tools**]，然後**Visual Studio 2010 命令提示**字元]。</span><span class="sxs-lookup"><span data-stu-id="a12f1-108">From the **Start** menu, select **All Programs**, then Microsoft Visual Studio, then **Visual Studio Tools**, and then **Visual Studio 2010 Command Prompt**.</span></span>  
  
2.  <span data-ttu-id="a12f1-109">如果您是使用 C#，請在命令提示字元視窗中執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="a12f1-109">In the command prompt window, run the following command if you are using C#:</span></span>  
  
    ```  
    wsdl /language:CS /n:"ReportService2010" http://<Server Name>/reportserver/reportservice2010.asmx?wsdl  
    ```  
  
     <span data-ttu-id="a12f1-110">如果您是使用 Visual Basic，則請在執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="a12f1-110">If you are using Visual Basic, then run the following command:</span></span>  
  
    ```  
    wsdl /language:VB /n:"ReportService2010" http://<Server Name>/reportserver/reportservice2010.asmx?wsdl  
    ```  
  
     <span data-ttu-id="a12f1-111">這個命令會產生 .cs 或 .vb 檔案。</span><span class="sxs-lookup"><span data-stu-id="a12f1-111">This command generates a .cs or .vb file.</span></span> <span data-ttu-id="a12f1-112">您會將這個檔案加入應用程式中。</span><span class="sxs-lookup"><span data-stu-id="a12f1-112">You will add this file to your application.</span></span>  
  
### <a name="to-create-a-console-application"></a><span data-ttu-id="a12f1-113">若要建立主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="a12f1-113">To create a console application</span></span>  
  
1.  <span data-ttu-id="a12f1-114">在 [**檔案**] 功能表上，指向 [**新增**]，然後按一下 [**專案**] 以開啟 [**新增專案**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="a12f1-114">On the **File** menu, point to **New**, and then click **Project** to open the **New Project** dialog box.</span></span>  
  
2.  <span data-ttu-id="a12f1-115">在左窗格的 [**已安裝的範本**] 底下，按一下 [ **Visual Basic** ] 或 [ **Visual c #** ] 節點，然後從展開的清單中選取專案類型的類別。</span><span class="sxs-lookup"><span data-stu-id="a12f1-115">In the left pane, under **Installed Templates**, click either **Visual Basic** or the **Visual C#** node, and select a category of project types from the expanded list.</span></span>  
  
3.  <span data-ttu-id="a12f1-116">選擇 [**主控台應用程式**] 專案類型。</span><span class="sxs-lookup"><span data-stu-id="a12f1-116">Choose the **Console Application** project type.</span></span>  
  
4.  <span data-ttu-id="a12f1-117">在 [**名稱**] 方塊中，輸入專案的名稱。</span><span class="sxs-lookup"><span data-stu-id="a12f1-117">In the **Name** box, enter a name for your project.</span></span> <span data-ttu-id="a12f1-118">輸入 [名稱] `SampleRDLSchema` 。</span><span class="sxs-lookup"><span data-stu-id="a12f1-118">Type the name `SampleRDLSchema`.</span></span>  
  
5.  <span data-ttu-id="a12f1-119">在 [**位置**] 方塊中，輸入您要儲存專案的路徑，或按一下 **[流覽]** 以流覽至資料夾。</span><span class="sxs-lookup"><span data-stu-id="a12f1-119">In the **Location** box, type the path where you want to save your project, or click **Browse** to navigate to the folder.</span></span>  
  
6.  [!INCLUDE[clickOK](../includes/clickok-md.md)]<span data-ttu-id="a12f1-120">專案的折迭視圖會顯示在方案總管中。</span><span class="sxs-lookup"><span data-stu-id="a12f1-120">A collapsed view of your project appears in Solution Explorer.</span></span>  
  
7.  <span data-ttu-id="a12f1-121">在 [專案]\*\*\*\* 功能表上，按一下 [新增現有項目]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="a12f1-121">On the **Project** menu, click **Add Existing Item**.</span></span>  
  
8.  <span data-ttu-id="a12f1-122">流覽至您產生的 .cs 或 .vb 檔案的位置，然後選取該檔案，再按一下 [**新增**]。</span><span class="sxs-lookup"><span data-stu-id="a12f1-122">Navigate to the location for the .cs or .vb file you generated, then select the file, and then click **Add**.</span></span>  
  
     <span data-ttu-id="a12f1-123">您也必須加入 <xref:System.Web.Services> 命名空間的參考，才能讓 Web 參考運作。</span><span class="sxs-lookup"><span data-stu-id="a12f1-123">You will also need to add a reference to the <xref:System.Web.Services> namespace for your Web reference to work.</span></span>  
  
9. <span data-ttu-id="a12f1-124">在 [專案] 功能表上，按一下 [加入參考]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="a12f1-124">On the Project menu, click **Add Reference**.</span></span>  
  
     <span data-ttu-id="a12f1-125">在 [**加入參考**] 對話方塊的 [ **.net** ] 索引標籤中，選取 [ **System.web**]，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="a12f1-125">In the **Add Reference** dialog box, in the **.NET** tab, select **System.Web.Services**, then click **OK**.</span></span>  
  
     <span data-ttu-id="a12f1-126">如需如何連接到報表伺服器 Web 服務的詳細資訊，請參閱[使用 Web 服務和 .NET Framework 建立應用程式](../reporting-services/report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)。</span><span class="sxs-lookup"><span data-stu-id="a12f1-126">For more information about how to connect to the Report Server Web service, see [Building Applications Using the Web Service and the .NET Framework](../reporting-services/report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md).</span></span>  
  
10. <span data-ttu-id="a12f1-127">在 [方案總管] 中，展開專案節點。</span><span class="sxs-lookup"><span data-stu-id="a12f1-127">In Solution Explorer, expand the project node.</span></span> <span data-ttu-id="a12f1-128">您會看到含有預設名稱 Program.cs (在 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] 中則為 Module1.vb) 的程式碼檔案已加入專案中。</span><span class="sxs-lookup"><span data-stu-id="a12f1-128">You will see a code file with the default name of Program.cs (Module1.vb for [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) has been added to your project.</span></span>  
  
11. <span data-ttu-id="a12f1-129">開啟 Program.cs (在 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] 中為 Module1.vb) 檔案，然後將程式碼取代成下列項目：</span><span class="sxs-lookup"><span data-stu-id="a12f1-129">Open the Program.cs (Module1.vb for [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) file and replace the code with the following:</span></span>  
  
     <span data-ttu-id="a12f1-130">下列程式碼提供方法 stubs，我們將用來實作「載入」、「更新」和「儲存功能」。</span><span class="sxs-lookup"><span data-stu-id="a12f1-130">The following code provides the method stubs we will use to implement the Load, Update and Save functionality.</span></span>  
  
    ```csharp  
    using System;  
    using System.Collections.Generic;  
    using System.IO;  
    using System.Text;  
    using System.Xml;  
    using System.Xml.Serialization;  
    using ReportService2010;  
  
    namespace SampleRDLSchema  
    {  
        class ReportUpdater  
        {  
            ReportingService2010 _reportService;  
  
            static void Main(string[] args)  
            {  
                ReportUpdater reportUpdater = new ReportUpdater();  
                reportUpdater.UpdateReport();  
            }  
  
            private void UpdateReport()  
            {  
                try  
                {  
                    // Set up the Report Service connection  
                    _reportService = new ReportingService2010();  
                    _reportService.Credentials =  
                        System.Net.CredentialCache.DefaultCredentials;  
                    _reportService.Url =  
                       "http://<Server Name>/reportserver/" +  
                                       "reportservice2010.asmx";  
  
                    // Call the methods to update a report definition  
                    LoadReportDefinition();  
                    UpdateReportDefinition();  
                    PublishReportDefinition();  
                }  
                catch (Exception ex)  
                {  
                    System.Console.WriteLine(ex.Message);  
                }  
            }  
  
            private void LoadReportDefinition()  
            {  
                //Lesson 3: Load a report definition from the report   
                //          catalog  
            }  
  
            private void UpdateReportDefinition()  
            {  
                //Lesson 4: Update the report definition using the    
                //          classes generated from the RDL Schema  
            }  
  
            private void PublishReportDefinition()  
            {  
                //Lesson 5: Publish the updated report definition back   
                //          to the report catalog  
            }  
        }  
    }  
    ```  
  
    ```vb  
    Imports System  
    Imports System.Collections.Generic  
    Imports System.IO  
    Imports System.Text  
    Imports System.Xml  
    Imports System.Xml.Serialization  
    Imports ReportService2010  
  
    Namespace SampleRDLSchema  
  
        Module ReportUpdater  
  
            Private m_reportService As ReportingService2010  
  
            Public Sub Main(ByVal args As String())  
  
                Try  
                    'Set up the Report Service connection  
                    m_reportService = New ReportingService2010  
                    m_reportService.Credentials = _  
                        System.Net.CredentialCache.DefaultCredentials  
                    m_reportService.Url = _  
                        "http:// <Server Name>/reportserver/" & _  
                               "reportservice2010.asmx"  
  
                    'Call the methods to update a report definition  
                    LoadReportDefinition()  
                    UpdateReportDefinition()  
                    PublishReportDefinition()  
                Catch ex As Exception  
                    System.Console.WriteLine(ex.Message)  
                End Try  
  
            End Sub  
  
            Private Sub LoadReportDefinition()  
                'Lesson 3: Load a report definition from the report   
                '          catalog  
            End Sub  
  
            Private Sub UpdateReportDefinition()  
                'Lesson 4: Update the report definition using the   
                '          classes generated from the RDL Schema  
            End Sub  
  
            Private Sub PublishReportDefinition()  
                'Lesson 5: Publish the updated report definition back   
                '          to the report catalog  
            End Sub  
  
        End Module  
  
    End Namespace   
    ```  
  
## <a name="next-lesson"></a><span data-ttu-id="a12f1-131">下一課</span><span class="sxs-lookup"><span data-stu-id="a12f1-131">Next Lesson</span></span>  
 <span data-ttu-id="a12f1-132">在下一課，您將使用 XML 結構描述定義工具 (Xsd.exe)，從 RDL 結構描述產生類別，並將類別包含在專案之中。</span><span class="sxs-lookup"><span data-stu-id="a12f1-132">In the next lesson, you will use the XML Schema Definition Tool (Xsd.exe) to generate classes from the RDL schema and include them in your project.</span></span> <span data-ttu-id="a12f1-133">請參閱[第2課：使用 Xsd 工具，從 RDL 架構產生類別](../../2014/tutorials/lesson-2-generate-classes-from-the-rdl-schema-using-the-xsd-tool.md)。</span><span class="sxs-lookup"><span data-stu-id="a12f1-133">See [Lesson 2: Generate Classes from the RDL Schema using the xsd Tool](../../2014/tutorials/lesson-2-generate-classes-from-the-rdl-schema-using-the-xsd-tool.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a12f1-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a12f1-134">See Also</span></span>  
 <span data-ttu-id="a12f1-135">[使用從 RDL 架構產生的類別更新報表 &#40;SSRS 教學課程&#41;](../../2014/tutorials/updating-reports-using-classes-generated-from-the-rdl-schema-ssrs-tutorial.md) </span><span class="sxs-lookup"><span data-stu-id="a12f1-135">[Updating Reports Using Classes Generated from the RDL Schema &#40;SSRS Tutorial&#41;](../../2014/tutorials/updating-reports-using-classes-generated-from-the-rdl-schema-ssrs-tutorial.md) </span></span>  
 [<span data-ttu-id="a12f1-136">報表定義語言 &#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="a12f1-136">Report Definition Language &#40;SSRS&#41;</span></span>](../reporting-services/reports/report-definition-language-ssrs.md)  
  
  
