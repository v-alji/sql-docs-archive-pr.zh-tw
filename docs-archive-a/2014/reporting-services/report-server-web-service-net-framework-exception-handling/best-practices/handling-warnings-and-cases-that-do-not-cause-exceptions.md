---
title: 處理未造成例外狀況的警告與案例 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- exceptions [Reporting Services], warnings that don't cause
- warnings [Reporting Services]
ms.assetid: 475c0713-6265-44e7-9ebc-ebdd1b89e0af
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 88d3daf63cf5f04975a2941d0634f357ce81456c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87702394"
---
# <a name="handling-warnings-and-cases-that-do-not-cause-exceptions"></a><span data-ttu-id="af30b-102">處理未造成例外狀況的警告與案例</span><span class="sxs-lookup"><span data-stu-id="af30b-102">Handling Warnings and Cases That Do Not Cause Exceptions</span></span>
  [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] <span data-ttu-id="af30b-103">不會擲回警告與某些錯誤的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="af30b-103">does not throw exceptions for warnings and certain errors.</span></span> <span data-ttu-id="af30b-104">例如，當您使用 <xref:ReportService2010.ReportingService2010.CreateCatalogItem%2A> 方法來將新報表發行到報表伺服器時，會以 <xref:ReportService2010.Warning> 物件的陣列傳回發生的任何警告。</span><span class="sxs-lookup"><span data-stu-id="af30b-104">For example, when you use the <xref:ReportService2010.ReportingService2010.CreateCatalogItem%2A> method to publish a new report to a report server, any warnings that occur are returned as an array of <xref:ReportService2010.Warning> objects.</span></span> <span data-ttu-id="af30b-105">應該處理和顯示這些警告，才能採取適當的動作。</span><span class="sxs-lookup"><span data-stu-id="af30b-105">These warnings should be handled and displayed so that appropriate action can be taken.</span></span>  
  
```vb  
Try  
   rs.CreateCatalogItem(name, parentFolder, False, definition, Nothing, warnings)  
  
   If Not (warnings.Length = 0) Then  
      Dim warning As Warning  
      For Each warning In warnings  
         Console.WriteLine(warning.Message)  
      Next warning  
   Else  
      Console.WriteLine("Report {0} created successfully with no warnings", name)  
   End If  
  
Catch ex As SoapException  
   Console.WriteLine(ex.Detail("Message").InnerXml)  
End Try  
```  
  
```csharp  
try  
{  
   rs.CreateCatalogItem("Report", name, parentFolder, false, definition, null, out warnings);  
  
   if (warnings.Length != 0)  
   {  
      foreach (Warning warning in warnings)  
      {  
         Console.WriteLine(warning.Message);  
      }  
   }  
   else  
      Console.WriteLine("Report {0} created successfully with no warnings", name);  
}  
  
catch (SoapException ex)  
{  
   Console.WriteLine(ex.Detail["Message"].InnerXml);  
}  
```  
  
 <span data-ttu-id="af30b-106">處理錯誤的另一項方法是評估某些方法的傳回值。</span><span class="sxs-lookup"><span data-stu-id="af30b-106">Another way to handle errors is to evaluate the return values of certain methods.</span></span> <span data-ttu-id="af30b-107">例如，<xref:ReportService2010.ReportingService2010.FindItems%2A> 方法可用以搜尋報表伺服器資料庫中的特定項目。</span><span class="sxs-lookup"><span data-stu-id="af30b-107">For example, the <xref:ReportService2010.ReportingService2010.FindItems%2A> method can be used to search for specific items in the report server database.</span></span> <span data-ttu-id="af30b-108">如果找不到符合搜尋準則的項目，則會傳回 <xref:ReportService2010.CatalogItem> 物件的 Null 陣列。</span><span class="sxs-lookup"><span data-stu-id="af30b-108">If no items are found that match the search criteria, a null array of <xref:ReportService2010.CatalogItem> objects is returned.</span></span> <span data-ttu-id="af30b-109">您應該評估陣列、檢查 `null`，而且如果找不到項目，應該讓使用者知道。</span><span class="sxs-lookup"><span data-stu-id="af30b-109">You should evaluate the array, check for `null`, and let the user know if no items were found.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af30b-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="af30b-110">See Also</span></span>  
 <xref:ReportService2010.CatalogItem>   
 <span data-ttu-id="af30b-111">[Reporting Services 中的例外狀況處理簡介](../introducing-exception-handling-in-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="af30b-111">[Introducing Exception Handling in Reporting Services](../introducing-exception-handling-in-reporting-services.md) </span></span>  
 [<span data-ttu-id="af30b-112">Reporting Services SoapException 類別</span><span class="sxs-lookup"><span data-stu-id="af30b-112">Reporting Services SoapException Class</span></span>](../soapexception-class/reporting-services-soapexception-class.md)  
  
  
