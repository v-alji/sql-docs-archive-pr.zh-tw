---
title: 使用 Try 和 Catch 區塊 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- exceptions [Reporting Services], try/catch blocks
- try/catch blocks [Reporting Services]
ms.assetid: a7a9ef53-e3b6-4bf7-81f3-d85615954e6f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: a6aadb392fa4117484f3373ae232c3ed9c4b1d63
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707053"
---
# <a name="using-try-and-catch-blocks"></a><span data-ttu-id="0d51f-102">使用 Try 和 Catch 區塊</span><span class="sxs-lookup"><span data-stu-id="0d51f-102">Using Try and Catch Blocks</span></span>
  <span data-ttu-id="0d51f-103">在您將條件陳述式加入程式碼，以限制對報表伺服器的無效要求之後，應該透過使用 Try/Catch 區塊，來提供適當的例外狀況處理。</span><span class="sxs-lookup"><span data-stu-id="0d51f-103">After you limit invalid requests to the report server by adding conditional statements to your code, you should supply adequate exception handling through the use of try/catch blocks.</span></span> <span data-ttu-id="0d51f-104">這個技術可以針對無效的要求提供另一層的保護。</span><span class="sxs-lookup"><span data-stu-id="0d51f-104">This technique provides another layer of protection against requests that are not valid.</span></span> <span data-ttu-id="0d51f-105">如果對報表伺服器的要求是包含在 Try 區塊中，而且該要求造成報表伺服器擲回例外狀況，則在 Catch 區塊中會抓住例外狀況，因此可防止應用程式非預期地結束。</span><span class="sxs-lookup"><span data-stu-id="0d51f-105">If a request to the report server is encased in a try block and that request causes the report server to throw an exception, the exception is caught in the catch block, thus preventing your application from ending unexpectedly.</span></span> <span data-ttu-id="0d51f-106">一旦捕捉到例外狀況，您可以使用例外狀況來指示使用者執行不一樣的動作，或只是以適當的方式讓使用者知道已發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="0d51f-106">Once the exception is caught, you can use the exception to either instruct the user to do something differently, or just let the user know, in a friendly way, that an error has occurred.</span></span> <span data-ttu-id="0d51f-107">接著您可以使用 Finally 區塊來清除任何資源。</span><span class="sxs-lookup"><span data-stu-id="0d51f-107">You can then use a finally block to clean up any resources.</span></span> <span data-ttu-id="0d51f-108">理想上，您應該產生一般的例外狀況處理計劃，來避免 Try/Catch 區塊不必要的複製。</span><span class="sxs-lookup"><span data-stu-id="0d51f-108">Ideally, you should generate a general exception-handling plan to avoid unnecessary duplication of try/catch blocks.</span></span>  
  
 <span data-ttu-id="0d51f-109">下列範例使用 Try/Catch 區塊來增強例外狀況處理程式碼的可靠性。</span><span class="sxs-lookup"><span data-stu-id="0d51f-109">The following example uses try/catch blocks to enhance the reliability of the exception handling code.</span></span>  
  
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
         "consult the online documentation";  
  
      MessageBox.Show(message, "Invalid Input Error");  
   }  
   else // Publish the report  
   {  
      Byte[] definition = null;  
      Warning[] warnings = {};  
      string name = nameTextBox.Text;  
  
      try  
      {  
         FileStream stream = File.OpenRead("MyReport.rdl");  
         definition = new Byte[stream.Length];  
         stream.Read(definition, 0, (int) stream.Length);  
         stream.Close();  
         // Create report with user-defined name  
         rs.CreateCatalogItem("Report", name, "/Samples", false, definition, null, out warnings);  
         MessageBox.Show("Report: {0} created successfully", name);  
      }  
  
      // Catch expected exceptions beginning with the most specific,  
      // moving to the least specific  
      catch(IOException ex)  
      {  
         MessageBox.Show(ex.Message, "File IO Exception");  
      }  
  
      catch (SoapException ex)  
      {  
         // The exception is a SOAP exception, so use  
         // the Detail property's Message element.  
         MessageBox.Show(ex.Detail["Message"].InnerXml, "SOAP Exception");   
      }  
  
      catch (Exception ex)  
      {  
         MessageBox.Show(ex.Message, "General Exception");  
      }  
   }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="0d51f-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0d51f-110">See Also</span></span>  
 <span data-ttu-id="0d51f-111">[Reporting Services 中的例外狀況處理簡介](../introducing-exception-handling-in-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="0d51f-111">[Introducing Exception Handling in Reporting Services](../introducing-exception-handling-in-reporting-services.md) </span></span>  
 [<span data-ttu-id="0d51f-112">Reporting Services SoapException 類別</span><span class="sxs-lookup"><span data-stu-id="0d51f-112">Reporting Services SoapException Class</span></span>](../soapexception-class/reporting-services-soapexception-class.md)  
  
  
