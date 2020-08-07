---
title: 使用 Detail 屬性處理特定的錯誤 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- exceptions [Reporting Services], Detail property
- Detail property
- InnerText property
ms.assetid: 4392633d-b46b-41e6-bc12-efb64e166704
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 4f8ac62dc381d8f665a44fc0897ba1f4215aa8e5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703833"
---
# <a name="using-the-detail-property-to-handle-specific-errors"></a><span data-ttu-id="070f2-102">使用詳細資料屬性來處理特定的錯誤</span><span class="sxs-lookup"><span data-stu-id="070f2-102">Using the Detail Property to Handle Specific Errors</span></span>
  <span data-ttu-id="070f2-103">若要進一步分類例外狀況，[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 會在 SOAP 例外狀況的 **Detail** 屬性中，於子項目的 **InnerText** 屬性中傳回其他錯誤資訊。</span><span class="sxs-lookup"><span data-stu-id="070f2-103">To further classify exceptions, [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] returns additional error information in the **InnerText** property of the child elements in the SOAP exception's **Detail** property.</span></span> <span data-ttu-id="070f2-104">因為 **Detail** 屬性是一種 **XmlNode** 物件，所以您可以使用下列程式碼來存取 **Message** 子項目的內部文字。</span><span class="sxs-lookup"><span data-stu-id="070f2-104">Because the **Detail** property is an **XmlNode** object, you can access the inner text of the **Message** child element using the following code.</span></span>  
  
 <span data-ttu-id="070f2-105">如需包含在 **Detail** 屬性中所有可用的子項目清單，請參閱 [Detail 屬性](../soapexception-class/detail-property.md)。</span><span class="sxs-lookup"><span data-stu-id="070f2-105">For a list of all of the available child elements contained in the **Detail** property, see [Detail Property](../soapexception-class/detail-property.md).</span></span> <span data-ttu-id="070f2-106">如需詳細資訊，請參閱 SDK 檔中的「詳細資料屬性」 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="070f2-106">For more information, see "Detail Property" in the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] SDK documentation.</span></span>  
  
```vb  
Try  
' Code for accessing the report server  
Catch ex As SoapException  
   ' The exception is a SOAP exception, so use  
   ' the Detail property's Message element.  
   Console.WriteLine(ex.Detail("Message").InnerXml)  
End Try  
```  
  
```csharp  
try  
{  
   // Code for accessing the report server  
}  
catch (SoapException ex)  
{  
   // The exception is a SOAP exception, so use  
   // the Detail property's Message element.  
   Console.WriteLine(ex.Detail["Message"].InnerXml);  
}  
```  
  
```vb  
Try  
' Code for accessing the report server  
Catch ex As SoapException  
   If ex.Detail("ErrorCode").InnerXml = "rsInvalidItemName" Then  
   End If ' Perform an action based on the specific error code  
End Try  
```  
  
```csharp  
try  
{  
   // Code for accessing the report server  
}  
catch (SoapException ex)  
{  
   if (ex.Detail["ErrorCode"].InnerXml == "rsInvalidItemName")  
   {  
      // Perform an action based on the specific error code  
   }  
}  
```  
  
 <span data-ttu-id="070f2-107">下列程式碼行會將在 SOAP 例外狀況中傳回的特定錯誤碼寫入主控台。</span><span class="sxs-lookup"><span data-stu-id="070f2-107">The following line of code writes the specific error code being returned in the SOAP Exception to the console.</span></span> <span data-ttu-id="070f2-108">另外，您可以評估錯誤碼並執行特定的動作。</span><span class="sxs-lookup"><span data-stu-id="070f2-108">You could also evaluate the error code and perform specific actions.</span></span>  
  
```vb  
Console.WriteLine(ex.Detail("ErrorCode").InnerXml)  
```  
  
```csharp  
Console.WriteLine(ex.Detail["ErrorCode"].InnerXml);  
```  
  
## <a name="see-also"></a><span data-ttu-id="070f2-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="070f2-109">See Also</span></span>  
 <span data-ttu-id="070f2-110">[Reporting Services 中的例外狀況處理簡介](../introducing-exception-handling-in-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="070f2-110">[Introducing Exception Handling in Reporting Services](../introducing-exception-handling-in-reporting-services.md) </span></span>  
 <span data-ttu-id="070f2-111">[Reporting Services SoapException 類別](../soapexception-class/reporting-services-soapexception-class.md) </span><span class="sxs-lookup"><span data-stu-id="070f2-111">[Reporting Services SoapException Class](../soapexception-class/reporting-services-soapexception-class.md) </span></span>  
 [<span data-ttu-id="070f2-112">SoapException 錯誤資料表</span><span class="sxs-lookup"><span data-stu-id="070f2-112">SoapException Errors Table</span></span>](../soapexception-class/soapexception-errors-table.md)  
  
  
