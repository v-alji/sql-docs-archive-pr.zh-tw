---
title: 第4課：以程式設計方式更新報表定義 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 1f0a1d46-6d6d-4f67-b51e-06dbbbffacf9
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: c090fc023e3ac47927b99ab61a45fd8ca2c79321
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594869"
---
# <a name="lesson-4-update-the-report-definition-programmatically"></a><span data-ttu-id="61b5f-102">第 4 課：以程式設計方式更新報表定義</span><span class="sxs-lookup"><span data-stu-id="61b5f-102">Lesson 4: Update the Report Definition Programmatically</span></span>
  <span data-ttu-id="61b5f-103">既然已經使用報表欄位從報表伺服器載入報表定義，並且您具有對它的參考，就必須更新報表定義。</span><span class="sxs-lookup"><span data-stu-id="61b5f-103">Now that the report definition has been loaded from the report server and you have a reference to it using the report field, you need to update the report definition.</span></span> <span data-ttu-id="61b5f-104">在此範例中，您將更新報表的 `Description` 屬性。</span><span class="sxs-lookup"><span data-stu-id="61b5f-104">For this example, you will update the `Description` property for the report.</span></span>  
  
### <a name="to-update-the-report-definition"></a><span data-ttu-id="61b5f-105">更新報表定義</span><span class="sxs-lookup"><span data-stu-id="61b5f-105">To update the report definition</span></span>  
  
1.  <span data-ttu-id="61b5f-106">使用下列程式碼，將 Program.cs 檔案中 UpdateReportDefinition ( # A1 方法的程式碼取代為 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) 的 (：</span><span class="sxs-lookup"><span data-stu-id="61b5f-106">Replace the code for the UpdateReportDefinition() method in the Program.cs file (Module1.vb for [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) with the following code:</span></span>  
  
    ```csharp  
    private void UpdateReportDefinition()  
    {  
        System.Console.WriteLine("Updating Report Definition");  
  
        // Create a list of the Items Choices for the Report. The   
        // ItemsChoiceType118 enum represents all the properties  
        // available in the report and the ItemsElementName   
        // represents the properties that exist in the current   
        // instance of the report.  
        List<ItemsChoiceType118> _reportItems =   
            new List<ItemsChoiceType118>(_report.ItemsElementName);  
  
        // Locate the index for the Description property  
        int index = _reportItems.IndexOf(  
            ItemsChoiceType118.Description);  
  
        // The Description item is of type StringLocIDType, so   
        // cast the item type first and then assign new value.  
        System.Console.WriteLine("- Old Description: " +   
            ((StringLocIDType)_report.Items[index]).Value );  
  
        // Update the Description for the Report  
        ((StringLocIDType)_report.Items[index]).Value =   
            "New Report Description";  
  
        System.Console.WriteLine("- New Description: " +   
            ((StringLocIDType)_report.Items[index]).Value );  
    }  
    ```  
  
    ```vb  
    Private Sub UpdateReportDefinition()  
  
        System.Console.WriteLine("Updating Report Definition")  
  
        'Create a list of the Items Choices for the Report. The   
        'ItemsChoiceType118 enum represents all the properties  
        'available in the report and the ItemsElementName   
        'represents the properties that exist in the current   
        'instance of the report.  
        Dim reportItems As List(Of ItemsChoiceType118) = _  
            New List(Of ItemsChoiceType118)(m_report.ItemsElementName)  
  
        'Locate the index for the Description property  
        Dim index As Integer = _  
            reportItems.IndexOf(ItemsChoiceType118.Description)  
  
        'The Description item is of type StringLocIDType, so   
        'cast the item type first and then assign new value.  
        System.Console.WriteLine("- Old Description: " & _  
            DirectCast(m_report.Items(index), StringLocIDType).Value)  
  
        'Update the Description for the Report  
        DirectCast(m_report.Items(index), StringLocIDType).Value = _  
            "New Report Description"  
  
        System.Console.WriteLine("- New Description: " & _  
            DirectCast(m_report.Items(index), StringLocIDType).Value)  
  
    End Sub  
    ```  
  
## <a name="next-lesson"></a><span data-ttu-id="61b5f-107">下一課</span><span class="sxs-lookup"><span data-stu-id="61b5f-107">Next Lesson</span></span>  
 <span data-ttu-id="61b5f-108">在下一課中，會將已更新的報表定義存回報表伺服器上。</span><span class="sxs-lookup"><span data-stu-id="61b5f-108">In the next lesson, you will save the updated report definition back to the report server.</span></span> <span data-ttu-id="61b5f-109">請參閱[第5課：將報表定義發行到報表伺服器](../../2014/tutorials/lesson-5-publish-the-report-definition-to-the-report-server.md)。</span><span class="sxs-lookup"><span data-stu-id="61b5f-109">See [Lesson 5: Publish the Report Definition to the Report Server](../../2014/tutorials/lesson-5-publish-the-report-definition-to-the-report-server.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61b5f-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="61b5f-110">See Also</span></span>  
 [<span data-ttu-id="61b5f-111">使用從 RDL 架構產生的類別更新報表 &#40;SSRS 教學課程&#41;</span><span class="sxs-lookup"><span data-stu-id="61b5f-111">Updating Reports Using Classes Generated from the RDL Schema &#40;SSRS Tutorial&#41;</span></span>](../../2014/tutorials/updating-reports-using-classes-generated-from-the-rdl-schema-ssrs-tutorial.md)  
  
  
