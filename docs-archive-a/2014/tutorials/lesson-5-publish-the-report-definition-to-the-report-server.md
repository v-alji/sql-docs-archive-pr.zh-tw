---
title: 第5課：將報表定義發行到報表伺服器 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 57fab70f-4a72-4413-a0ad-d0525caca3f7
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 54c2bad9f5b11e5ea72036fed9f60371ba9c593c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593714"
---
# <a name="lesson-5-publish-the-report-definition-to-the-report-server"></a><span data-ttu-id="f6d1d-102">第 5 課：將報表定義發行到報表伺服器</span><span class="sxs-lookup"><span data-stu-id="f6d1d-102">Lesson 5: Publish the Report Definition to the Report Server</span></span>
  <span data-ttu-id="f6d1d-103">更新報表定義的最後步驟是將報表定義發行回到報表伺服器。</span><span class="sxs-lookup"><span data-stu-id="f6d1d-103">The last step for updating the report definition is to publish it back to the report server.</span></span>  
  
### <a name="to-publish-the-report-to-the-report-catalog"></a><span data-ttu-id="f6d1d-104">將報表發行到報表目錄</span><span class="sxs-lookup"><span data-stu-id="f6d1d-104">To publish the report to the report catalog</span></span>  
  
1.  <span data-ttu-id="f6d1d-105">將 Program.cs 檔案中方法的程式碼取代 `PublishReportDefinition()` 為 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] 使用下列程式碼的)  (Module1：</span><span class="sxs-lookup"><span data-stu-id="f6d1d-105">Replace the code for the `PublishReportDefinition()` method in your Program.cs file (Module1.vb for [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) with the following code:</span></span>  
  
    ```csharp  
    private void PublishReportDefinition()  
    {  
        System.Console.WriteLine("Publishing Report Definition");  
  
        string reportPath =  
            "/AdventureWorks 2012 Sample Reports/Company Sales 2012";  
  
        XmlSerializer serializer =  
            new XmlSerializer(typeof(Report));  
  
        using (MemoryStream stream = new MemoryStream())  
        {  
            // Serialize the report into the MemoryStream  
            serializer.Serialize(stream, _report);  
            stream.Position = 0;  
  
            byte[] bytes = stream.ToArray();  
  
            // Update the report on the report server  
            Warning[] warnings =   
                _reportService.SetItemDefinition(reportPath, bytes, null);  
        }  
    }  
    ```  
  
    ```vb  
    Private Sub PublishReportDefinition()  
  
        System.Console.WriteLine("Publishing Report Definition")  
  
        Dim reportPath As String = _  
            "/AdventureWorks 2012 Sample Reports/Company Sales 2012"  
        Dim serializer As XmlSerializer = _  
            New XmlSerializer(GetType(Report))  
  
        Using stream As MemoryStream = New MemoryStream  
  
            'Serialize the report into the MemoryStream  
            serializer.Serialize(stream, m_report)  
            stream.Position = 0  
  
            'Update the report on the report server  
            Dim bytes As Byte() = stream.ToArray  
            Dim warnings As Warning() = _  
                m_reportService.SetItemDefinition(reportPath, bytes, Nothing)  
  
        End Using  
  
    End Sub  
    ```  
  
## <a name="next-lesson"></a><span data-ttu-id="f6d1d-106">下一課</span><span class="sxs-lookup"><span data-stu-id="f6d1d-106">Next Lesson</span></span>  
 <span data-ttu-id="f6d1d-107">在下一課中，您將會編譯並執行 `SampleRDLSchema` 應用程式。</span><span class="sxs-lookup"><span data-stu-id="f6d1d-107">In the next lesson, you will compile and run the `SampleRDLSchema` application.</span></span> <span data-ttu-id="f6d1d-108">請參閱[第6課：執行 RDL 架構應用程式 &#40;VB-C&#35;&#41;](../../2014/tutorials/lesson-6-run-the-rdl-schema-application-vb-csharp.md)。</span><span class="sxs-lookup"><span data-stu-id="f6d1d-108">See [Lesson 6: Run the RDL Schema Application &#40;VB-C&#35;&#41;](../../2014/tutorials/lesson-6-run-the-rdl-schema-application-vb-csharp.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6d1d-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f6d1d-109">See Also</span></span>  
 <span data-ttu-id="f6d1d-110">[使用從 RDL 架構產生的類別更新報表 &#40;SSRS 教學課程&#41;](../../2014/tutorials/updating-reports-using-classes-generated-from-the-rdl-schema-ssrs-tutorial.md) </span><span class="sxs-lookup"><span data-stu-id="f6d1d-110">[Updating Reports Using Classes Generated from the RDL Schema &#40;SSRS Tutorial&#41;](../../2014/tutorials/updating-reports-using-classes-generated-from-the-rdl-schema-ssrs-tutorial.md) </span></span>  
 [<span data-ttu-id="f6d1d-111">報表定義語言 &#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="f6d1d-111">Report Definition Language &#40;SSRS&#41;</span></span>](../reporting-services/reports/report-definition-language-ssrs.md)  
  
  
