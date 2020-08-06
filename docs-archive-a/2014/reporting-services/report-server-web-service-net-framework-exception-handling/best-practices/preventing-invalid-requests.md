---
title: 防止無效的要求 | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- invalid requests [Reporting Services]
- exceptions [Reporting Services], invalid requests
- valid requests [Reporting Services]
ms.assetid: 4a4a2d97-4c10-43a9-8298-ef5a820ea549
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 12343955c46fb98fea75048a38749b1db993fa11
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599344"
---
# <a name="preventing-invalid-requests"></a><span data-ttu-id="be79d-102">防止無效的要求</span><span class="sxs-lookup"><span data-stu-id="be79d-102">Preventing Invalid Requests</span></span>
  <span data-ttu-id="be79d-103">您可以防止擲回某些類型的例外狀況，方法是分析應用程式流程，並確保傳送到報表伺服器的要求是有效的。</span><span class="sxs-lookup"><span data-stu-id="be79d-103">You can prevent some types of exceptions from being thrown by analyzing your application flow and ensuring that the requests being sent to the report server are valid.</span></span> <span data-ttu-id="be79d-104">例如，在可讓使用者加入或更新報表名稱、資料來源或是其他報表伺服器項目的應用程式中，您應該驗證使用者可能輸入的文字。</span><span class="sxs-lookup"><span data-stu-id="be79d-104">For example, in applications that enable users to add or update the name of a report, data source, or other report server item, you should validate the text that a user might enter.</span></span> <span data-ttu-id="be79d-105">傳送要求到報表伺服器之前，請務必檢查保留字元。</span><span class="sxs-lookup"><span data-stu-id="be79d-105">You should always check for reserved characters before sending the request to a report server.</span></span> <span data-ttu-id="be79d-106">請使用 **if** 條件陳述式或程式碼中的其他邏輯建構來警示使用者，告知使用者他們未符合傳送要求到報表伺服器所需的條件。</span><span class="sxs-lookup"><span data-stu-id="be79d-106">Use conditional **if** statements or other logical constructs in your code to alert the user that they have not met the conditions necessary to send requests to the report server.</span></span>  
  
 <span data-ttu-id="be79d-107">在下列簡化的 C# 範例中，當使用者嘗試使用包含斜線 (/) 字元的名稱來建立報表時，會顯示易懂的錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="be79d-107">In the following, simplified C# example, users are presented with a friendly error message when they attempt to create a report with a name that contains a forward slash (/) character.</span></span>  
  
```  
// C#  
private void PublishReport()  
{  
   int index;  
   string reservedChar;  
   string message;  
  
   // Check the text value of the name text box for "/",  
   // a reserved character  
   index = nameTextBox.Text.IndexOf(@"/");  
  
   if ( index != -1) // The text contains the character  
   {  
      reservedChar = nameTextBox.Text.Substring(index, 1);  
      // Build a user-friendly error message  
      message = "The name of the report cannot contain the reserved character " +  
         "\"" + reservedChar + "\". " +  
         "Please enter a valid name for the report. " +  
         "For more information about reserved characters, " +  
         "see the help documentation";  
  
      MessageBox.Show(message, "Invalid Input Error");  
   }  
   else // Publish the report  
   {  
      Byte[] definition = null;  
      Warning[] warnings = {};  
      string name = nameTextBox.Text;  
  
      FileStream stream = File.OpenRead("MyReport.rdl");  
      definition = new Byte[stream.Length];  
      stream.Read(definition, 0, (int) stream.Length);  
      stream.Close();  
      // Create report with user-defined name  
      rs.CreateCatalogItem("Report", name, "/Samples", false, definition, null, out warnings);  
      MessageBox.Show("Report: {0} created successfully", name);  
   }  
}  
```  
  
 <span data-ttu-id="be79d-108">如需將要求傳送到報表伺服器之前可以避免之錯誤類型的詳細資訊，請參閱 [SoapException 錯誤資料表](../soapexception-class/soapexception-errors-table.md)。</span><span class="sxs-lookup"><span data-stu-id="be79d-108">For more information about the types of errors that can be prevented before requests are sent to the report server, see [SoapException Errors Table](../soapexception-class/soapexception-errors-table.md).</span></span> <span data-ttu-id="be79d-109">如需使用 Try/Catch 區塊進一步加強上述範例的詳細資訊，請參閱[使用 Try 和 Catch 區塊](using-try-and-catch-blocks.md)。</span><span class="sxs-lookup"><span data-stu-id="be79d-109">For more information about further enhancing the previous example using try/catch blocks, see [Using Try and Catch Blocks](using-try-and-catch-blocks.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be79d-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="be79d-110">See Also</span></span>  
 <span data-ttu-id="be79d-111">[Reporting Services 中的例外狀況處理簡介](../introducing-exception-handling-in-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="be79d-111">[Introducing Exception Handling in Reporting Services](../introducing-exception-handling-in-reporting-services.md) </span></span>  
 [<span data-ttu-id="be79d-112">Reporting Services SoapException 類別</span><span class="sxs-lookup"><span data-stu-id="be79d-112">Reporting Services SoapException Class</span></span>](../soapexception-class/reporting-services-soapexception-class.md)  
  
  
