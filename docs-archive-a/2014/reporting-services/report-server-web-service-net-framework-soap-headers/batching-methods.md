---
title: 批次方法 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- methods [Reporting Services], batches
- BatchHeader SOAP header
- Web service [Reporting Services], methods
- Report Server Web service, batching
- batches [Reporting Services]
- XML Web service [Reporting Services], methods
- locking [Reporting Services]
- multiple Web service methods
ms.assetid: 86435534-c9fe-4b49-b88c-7fb6d21976b0
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c778da186fdbbfaed17b9635d9ca7309a369552b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599339"
---
# <a name="batching-methods"></a><span data-ttu-id="608fe-102">批次方法</span><span class="sxs-lookup"><span data-stu-id="608fe-102">Batching Methods</span></span>
  <span data-ttu-id="608fe-103">在 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 中使用 SOAP 標頭可讓您在單一作業中包括多個 Web 服務方法。</span><span class="sxs-lookup"><span data-stu-id="608fe-103">The use of SOAP headers in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] enables you to include multiple Web service methods in a single operation.</span></span> <span data-ttu-id="608fe-104">方法會依呼叫它們的順序在單一資料庫交易的範圍中執行。</span><span class="sxs-lookup"><span data-stu-id="608fe-104">Methods run within the scope of a single database transaction, in the order in which they are called.</span></span>  
  
 <span data-ttu-id="608fe-105">交易回復是使用多個方法批次作業的其中一個優點。</span><span class="sxs-lookup"><span data-stu-id="608fe-105">Rollback is one advantage of using multiple-method batch operations.</span></span> <span data-ttu-id="608fe-106">如果在呼叫任何方法時發生錯誤，報表伺服器會停止執行批次，並回復任何之前的作業。</span><span class="sxs-lookup"><span data-stu-id="608fe-106">If an error occurs on any of the method calls while a batch is running, the report server stops running the batch and rolls back any previous operations.</span></span> <span data-ttu-id="608fe-107">當方法呼叫須視該批次中的其他方法呼叫是否成功完成時，這將會非常有用。</span><span class="sxs-lookup"><span data-stu-id="608fe-107">This is useful when a method call depends on the successful completion of other method calls in that batch.</span></span>  
  
 <span data-ttu-id="608fe-108">Web 服務並不會為多個方法批次作業提供鎖定語意。</span><span class="sxs-lookup"><span data-stu-id="608fe-108">The Web service does not provide locking semantics for multiple-method batch operations.</span></span> <span data-ttu-id="608fe-109">在將訊息傳送到伺服器以及呼叫 Execute 命令之前，在報表伺服器資料庫中的資料列不會鎖定更新。</span><span class="sxs-lookup"><span data-stu-id="608fe-109">Rows in the report server database are not locked for updating until the message is sent to the server and the Execute command is called.</span></span>  
  
 <span data-ttu-id="608fe-110">另外，也有並行控制項以保證資料庫自從上次讀取資料之後沒有任何變更。</span><span class="sxs-lookup"><span data-stu-id="608fe-110">There are also no concurrency controls to guarantee that the database has not changed since the data was last read.</span></span> <span data-ttu-id="608fe-111">如果有兩個用戶端修改相同的項目，當參數仍然有效 (例如，未重新命名項目) 時，則最後的更新會成功。</span><span class="sxs-lookup"><span data-stu-id="608fe-111">If two clients modify the same item, the last update succeeds if the parameters are still valid (for example, the item has not been renamed).</span></span>  
  
 <span data-ttu-id="608fe-112">下列範例會呼叫 <xref:ReportService2005.ReportingService2005.CreateFolder%2A> 方法三次，並將以單一批次執行這些呼叫。</span><span class="sxs-lookup"><span data-stu-id="608fe-112">The following example calls the <xref:ReportService2005.ReportingService2005.CreateFolder%2A> method three times and runs these calls as a single batch.</span></span> <span data-ttu-id="608fe-113">如果呼叫 <xref:ReportService2005.ReportingService2005.CreateFolder%2A> 失敗，則會取消整個批次。</span><span class="sxs-lookup"><span data-stu-id="608fe-113">If any of the calls to <xref:ReportService2005.ReportingService2005.CreateFolder%2A> fail, the entire batch is canceled.</span></span>  
  
```vb  
Imports System  
Imports System.Web.Services.Protocols  
Imports myNamespace.MyReferenceName  
  
Class Sample  
    Sub Main(args() As String)  
        Dim rs As New ReportingService2005()  
        rs.Credentials = System.Net.CredentialCache.DefaultCredentials  
      ' Set the base Web service URL of the source server  
      rs.Url = "http://<Server Name>/reportserver/ReportService2005.asmx"  
  
        Dim bh As New BatchHeader()  
  
        bh.BatchId = service.CreateBatch()  
        rs.BatchHeaderValue = bh  
        rs.CreateFolder("New Folder1", "/", Nothing)  
        rs.CreateFolder("New Folder2", "/", Nothing)  
        rs.CreateFolder("New Folder3", "/", Nothing)  
  
        Console.WriteLine("Creating folders...")  
        rs.BatchHeaderValue = bh  
        rs.ExecuteBatch()  
        Console.WriteLine("Folders created successfully.")  
  
        rs.BatchHeaderValue = Nothing  
    End Sub  
End Class  
```  
  
```csharp  
using System;  
using System.Web.Services.Protocols;   
using myNamespace.MyReferenceName;  
  
class Sample  
{  
    static void Main(string[] args)  
    {  
        ReportingService2005 rs = new ReportingService2005();  
        rs.Credentials = System.Net.CredentialCache.DefaultCredentials;  
      // Set the base Web service URL of the source server  
      rs.Url = "http://<Server Name>/reportserver/ReportService2005.asmx"  
  
        BatchHeader bh = new BatchHeader();  
  
        bh1.BatchID = service.CreateBatch();  
        rs.BatchHeaderValue = bh;  
        rs.CreateFolder("New Folder1", "/", null);  
        rs.CreateFolder("New Folder2", "/", null);  
        rs.CreateFolder("New Folder3", "/", null);  
  
        Console.WriteLine("Creating folders...");  
        rs.BatchHeaderValue = bh1;  
        rs.ExecuteBatch();  
        Console.WriteLine("Folders created successfully.");  
  
        rs.BatchHeaderValue = null;  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="608fe-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="608fe-114">See Also</span></span>  
 <xref:ReportService2005.ReportingService2005.CancelBatch%2A>   
 <xref:ReportService2005.ReportingService2005.CreateBatch%2A>   
 <span data-ttu-id="608fe-115">[SSRS&#41;&#40;的技術參考](../technical-reference-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="608fe-115">[Technical Reference &#40;SSRS&#41;](../technical-reference-ssrs.md) </span></span>  
 [<span data-ttu-id="608fe-116">使用 Reporting Services SOAP 標頭</span><span class="sxs-lookup"><span data-stu-id="608fe-116">Using Reporting Services SOAP Headers</span></span>](using-reporting-services-soap-headers.md)  
  
  
