---
title: 設定 GetProperties 方法的項目命名空間 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- item properties [Reporting Services]
- ItemNamespaceHeader SOAP header
- GetProperties method
ms.assetid: b0a08639-3101-40a2-abe2-3a41753826d1
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 14e8147a9a7639dd357077b5d881e2d4ed87fcc7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87702393"
---
# <a name="setting-the-item-namespace-for-the-getproperties-method"></a><span data-ttu-id="be497-102">設定 GetProperties 方法的項目命名空間</span><span class="sxs-lookup"><span data-stu-id="be497-102">Setting the Item Namespace for the GetProperties Method</span></span>
  <span data-ttu-id="be497-103">您可以使用 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 中的 <xref:ReportService2010.ItemNamespaceHeader> SOAP 標頭，根據兩個不同的項目識別碼來擷取項目屬性：項目的完整路徑或是項目的識別碼。</span><span class="sxs-lookup"><span data-stu-id="be497-103">You can use the <xref:ReportService2010.ItemNamespaceHeader> SOAP header in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] to retrieve item properties based on two different item identifiers: the full path of the item or the ID of the item.</span></span>  
  
 <span data-ttu-id="be497-104">當您呼叫 <xref:ReportService2010.ReportingService2010.GetProperties%2A> 方法時，通常會以引數傳遞您要擷取屬性的項目之完整路徑。</span><span class="sxs-lookup"><span data-stu-id="be497-104">When you make a call to the <xref:ReportService2010.ReportingService2010.GetProperties%2A> method, you normally pass as an argument the full path of the item for which you want to retrieve properties.</span></span> <span data-ttu-id="be497-105">您可以透過使用 <xref:ReportService2010.ItemNamespaceHeader>，傳遞項目的識別碼做為識別碼，為方法呼叫設定 SOAP 標頭，以便使用 <xref:ReportService2010.ReportingService2010.GetProperties%2A>。</span><span class="sxs-lookup"><span data-stu-id="be497-105">By using <xref:ReportService2010.ItemNamespaceHeader>, you can set the SOAP header for your method call to enable you to use <xref:ReportService2010.ReportingService2010.GetProperties%2A> by passing the ID of the item as an identifier.</span></span>  
  
 <span data-ttu-id="be497-106">下列程式碼範例會根據項目的識別碼來擷取項目屬性值。</span><span class="sxs-lookup"><span data-stu-id="be497-106">The following code sample retrieves the values for item properties based on the ID of the item.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="be497-107">依預設，如果您以項目識別碼傳遞完整路徑名稱給 <xref:ReportService2010.ItemNamespaceHeader> 方法，則不需要為 <xref:ReportService2010.ReportingService2010.GetProperties%2A> 設定值。</span><span class="sxs-lookup"><span data-stu-id="be497-107">By default, you do not need to set a value for the <xref:ReportService2010.ItemNamespaceHeader> if you pass to the <xref:ReportService2010.ReportingService2010.GetProperties%2A> method the full path name as the item identifier.</span></span>  
  
```vb  
Imports System  
Imports System.Collections  
  
Class Sample  
   Sub Main()  
      Dim rs As New ReportingService2010()  
      rs.Credentials = System.Net.CredentialCache.DefaultCredentials  
      rs.Url = "http://<Server Name>/reportserver/ReportService2010.asmx"  
  
      Dim items() As CatalogItem  
  
      Try  
         ' Need the ID property of items. Normally, you would already have   
         ' this stored somewhere.  
         items = rs.ListChildren("/AdventureWorks Sample Reports", False)  
  
         ' Set the item namespace header to be GUID-based  
         rs.ItemNamespaceHeaderValue = New ItemNamespaceHeader()  
         rs.ItemNamespaceHeaderValue.ItemNamespace = ItemNamespaceEnum.GUIDBased  
  
         ' Call GetProperties with item ID.  
         If Not (items Is Nothing) Then  
            Dim item As CatalogItem  
            For Each item In  items  
               Dim properties As [Property]() = rs.GetProperties(item.ID, Nothing)  
               Dim property As [Property]  
               For Each property In  properties  
                  Console.WriteLine(([property].Name + ": " + [property].Value))  
               Next property  
               Console.WriteLine()  
            Next item  
         End If  
  
      Catch e As Exception  
         Console.WriteLine((e.Message + ": " + e.StackTrace))  
      End Try  
   End Sub 'Main  
End Class 'Sample  
```  
  
```csharp  
using System;  
using System.Collections;  
  
class Sample  
{  
   static void Main()  
   {  
   ReportingService2010 rs = new ReportingService2010();  
      rs.Credentials = System.Net.CredentialCache.DefaultCredentials;  
      rs.Url = "http://<Server Name>/reportserver/ReportService2010.asmx";  
  
      CatalogItem[] items;  
  
      try  
      {  
         // Need the ID property of items. Normally, you would already have   
         // this stored somewhere.  
         items = rs.ListChildren("/AdventureWorks Sample Reports", false);  
  
         // Set the item namespace header to be GUID-based  
         rs.ItemNamespaceHeaderValue = new ItemNamespaceHeader();  
         rs.ItemNamespaceHeaderValue.ItemNamespace = ItemNamespaceEnum.GUIDBased;  
  
         // Call GetProperties with item ID.  
         if (items != null)  
         {  
            foreach( CatalogItem item in items)  
            {  
               Property[] properties = rs.GetProperties(item.ID, null);  
               foreach (Property property in properties)  
               {  
                  Console.WriteLine(property.Name + ": " + property.Value);  
               }  
               Console.WriteLine();  
            }  
         }  
      }  
  
      catch (Exception e)  
      {  
         Console.WriteLine(e.Message);  
      }  
   }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="be497-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="be497-108">See Also</span></span>  
 <span data-ttu-id="be497-109">[SSRS&#41;&#40;的技術參考](../technical-reference-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="be497-109">[Technical Reference &#40;SSRS&#41;](../technical-reference-ssrs.md) </span></span>  
 [<span data-ttu-id="be497-110">使用 Reporting Services SOAP 標頭</span><span class="sxs-lookup"><span data-stu-id="be497-110">Using Reporting Services SOAP Headers</span></span>](using-reporting-services-soap-headers.md)  
  
  
