---
title: 第3課：從報表伺服器載入報表定義 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 5ad8b31c-43b0-4481-a31b-090cbed4a438
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: dc6ed26703599792b9c739f8d185ae4f190fc8be
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594882"
---
# <a name="lesson-3-load-a-report-definition-from-the-report-server"></a><span data-ttu-id="d43a7-102">第 3 課：從報表伺服器載入報表定義</span><span class="sxs-lookup"><span data-stu-id="d43a7-102">Lesson 3: Load a Report Definition from the Report Server</span></span>
  <span data-ttu-id="d43a7-103">在您建立專案並從 RDL 結構描述產生類別之後，就可以開始從報表伺服器載入報表定義。</span><span class="sxs-lookup"><span data-stu-id="d43a7-103">After you have created your project and generated the classes from the RDL schema, you are ready to load a report definition from the report server.</span></span>  
  
### <a name="to-load-a-report-definition"></a><span data-ttu-id="d43a7-104">載入報表定義</span><span class="sxs-lookup"><span data-stu-id="d43a7-104">To load a report definition</span></span>  
  
1.  <span data-ttu-id="d43a7-105">`ReportUpdater`如果您使用類別的) ，請在類別 (模組的頂端新增私用欄位 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] `Report` 。</span><span class="sxs-lookup"><span data-stu-id="d43a7-105">Add a private field at the top of the `ReportUpdater` class (module if you are using [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) for the `Report` class.</span></span> <span data-ttu-id="d43a7-106">此欄位將用來在應用程式使用期間，維護從報表伺服器載入的報表參考。</span><span class="sxs-lookup"><span data-stu-id="d43a7-106">This field will be used to maintain a reference to report that is loaded from the report server for the life of the application.</span></span>  
  
    ```csharp  
    private Report _report;  
    ```  
  
    ```vb  
    Private m_report As Report  
    ```  
  
2.  <span data-ttu-id="d43a7-107">以下列程式碼取代 Program.cs 檔案 (在 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] 中為 Module1.vb) 中 `LoadReportDefinition()` 方法的程式碼：</span><span class="sxs-lookup"><span data-stu-id="d43a7-107">Replace the code for the `LoadReportDefinition()` method in the Program.cs file (Module1.vb for [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) with the following code:</span></span>  
  
    ```csharp  
    private void LoadReportDefinition()  
    {  
        System.Console.WriteLine("Loading Report Definition");  
  
        string reportPath =   
            "/AdventureWorks 2012 Sample Reports/Company Sales 2012";  
  
        // Retrieve the report definition   
        // from the report server  
        byte[] bytes =   
            _reportService.GetItemDefinition(reportPath);  
  
        if (bytes != null)  
        {  
            XmlSerializer serializer =   
                new XmlSerializer(typeof(Report));  
  
            // Load the report bytes into a memory stream  
            using (MemoryStream stream = new MemoryStream(bytes))  
            {  
                // Deserialize the report stream to an   
                // instance of the Report class  
                _report = (Report)serializer.Deserialize(stream);  
            }  
        }  
    }  
    ```  
  
    ```vb  
    Private Sub LoadReportDefinition()  
  
        System.Console.WriteLine("Loading Report Definition")  
  
        Dim reportPath As String = _  
            "/AdventureWorks 2012 Sample Reports/Company Sales 2012"  
  
        'Retrieve the report definition   
        'from the report server  
        Dim bytes As Byte() = _  
            m_reportService.GetItemDefinition(reportPath)  
  
        If Not (bytes Is Nothing) Then  
  
            Dim serializer As XmlSerializer = _  
                New XmlSerializer(GetType(Report))  
  
            'Load the report bytes into a memory stream  
            Using stream As MemoryStream = New MemoryStream(bytes)  
  
                'Deserialize the report stream to an   
                'instance of the Report class  
                m_report = CType(serializer.Deserialize(stream), _  
                                 Report)  
  
            End Using  
  
        End If  
  
    End Sub  
    ```  
  
## <a name="next-lesson"></a><span data-ttu-id="d43a7-108">下一課</span><span class="sxs-lookup"><span data-stu-id="d43a7-108">Next Lesson</span></span>  
 <span data-ttu-id="d43a7-109">在下一課，您將撰寫程式碼，更新從報表伺服器載入的報表定義。</span><span class="sxs-lookup"><span data-stu-id="d43a7-109">In the next lesson, you will write code to update the report definition that was loaded from the report server.</span></span> <span data-ttu-id="d43a7-110">請參閱[第4課：以程式設計方式更新報表定義](../../2014/tutorials/lesson-4-update-the-report-definition-programmatically.md)。</span><span class="sxs-lookup"><span data-stu-id="d43a7-110">See [Lesson 4: Update the Report Definition Programmatically](../../2014/tutorials/lesson-4-update-the-report-definition-programmatically.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d43a7-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d43a7-111">See Also</span></span>  
 <span data-ttu-id="d43a7-112">[使用從 RDL 架構產生的類別更新報表 &#40;SSRS 教學課程&#41;](../../2014/tutorials/updating-reports-using-classes-generated-from-the-rdl-schema-ssrs-tutorial.md) </span><span class="sxs-lookup"><span data-stu-id="d43a7-112">[Updating Reports Using Classes Generated from the RDL Schema &#40;SSRS Tutorial&#41;](../../2014/tutorials/updating-reports-using-classes-generated-from-the-rdl-schema-ssrs-tutorial.md) </span></span>  
 [<span data-ttu-id="d43a7-113">報表定義語言 &#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="d43a7-113">Report Definition Language &#40;SSRS&#41;</span></span>](../reporting-services/reports/report-definition-language-ssrs.md)  
  
  
