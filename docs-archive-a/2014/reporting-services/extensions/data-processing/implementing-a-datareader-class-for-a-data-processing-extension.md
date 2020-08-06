---
title: 為資料處理延伸模組實作 DataReader 類別 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- data processing extensions [Reporting Services], data readers
- data readers [Reporting Services]
- DataReader class
- read-only data
ms.assetid: 23e286e7-6074-4fbe-be29-203420d6c3d0
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 7c9e55741c72d624b7149435ced90550135d8b4a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708953"
---
# <a name="implementing-a-datareader-class-for-a-data-processing-extension"></a><span data-ttu-id="05fb2-102">為資料處理延伸模組實作 DataReader 類別</span><span class="sxs-lookup"><span data-stu-id="05fb2-102">Implementing a DataReader Class for a Data Processing Extension</span></span>
  <span data-ttu-id="05fb2-103">**DataReader** 物件允許用戶端從資料來源擷取唯讀、順向的資料流。</span><span class="sxs-lookup"><span data-stu-id="05fb2-103">The **DataReader** object enables a client to retrieve a read-only, forward-only stream of data from a data source.</span></span> <span data-ttu-id="05fb2-104">執行查詢時會傳回結果，並一直儲存於用戶端上的網路緩衝區中，直到您使用 **DataReader** 類別的 **Read** 方法要求它們為止。</span><span class="sxs-lookup"><span data-stu-id="05fb2-104">Results are returned as the query executes and are stored in the network buffer on the client until you request them using the **Read** method of the **DataReader** class.</span></span> <span data-ttu-id="05fb2-105">若要建立 **DataReader** 類別，請實作 <xref:Microsoft.ReportingServices.DataProcessing.IDataReader> 並選擇性地實作 <xref:Microsoft.ReportingServices.DataProcessing.IDataReaderExtension>。</span><span class="sxs-lookup"><span data-stu-id="05fb2-105">To create a **DataReader** class, implement <xref:Microsoft.ReportingServices.DataProcessing.IDataReader> and optionally implement <xref:Microsoft.ReportingServices.DataProcessing.IDataReaderExtension>.</span></span> <span data-ttu-id="05fb2-106">使用 **DataReader** 物件可以提高應用程式的效能，方法是在資料可用時立即擷取它，而不是等待傳回查詢的整個結果，以及 (依預設) 一次只將一個資料列儲存到記憶體中，進而減少系統負擔。</span><span class="sxs-lookup"><span data-stu-id="05fb2-106">Using a **DataReader** object increases application performance both by retrieving data as soon as it is available, rather than waiting for the entire results of the query to be returned, and (by default) storing only one row at a time in memory, reducing system overhead.</span></span>  
  
 <span data-ttu-id="05fb2-107">在建立 **Command** 類別的執行個體之後，可以呼叫 **Command.ExecuteReader** 從資料來源擷取資料列來建立 **DataReader** 物件。</span><span class="sxs-lookup"><span data-stu-id="05fb2-107">After creating an instance of your **Command** class, you create a **DataReader** object by calling **Command.ExecuteReader** to retrieve rows from the data source.</span></span> <span data-ttu-id="05fb2-108">**DataReader** 實作必須提供兩個基本功能：順向存取執行命令所擷取的結果集，並存取每個資料列中的資料行類型、名稱和值。</span><span class="sxs-lookup"><span data-stu-id="05fb2-108">The **DataReader** implementation must provide two basic capabilities: forward-only access over the result sets obtained by executing a command and access to the column types, names, and values within each row.</span></span> <span data-ttu-id="05fb2-109">用戶端使用 **DataReader** 物件的 **Read** 方法，從查詢結果取得資料列。</span><span class="sxs-lookup"><span data-stu-id="05fb2-109">Clients use the **Read** method of the **DataReader** object to obtain a row from the results of the query.</span></span>  
  
 <span data-ttu-id="05fb2-110">在報表設計師中，**DataReader** 物件是用以擷取欄位清單以及有關結果集的結構描述資訊。</span><span class="sxs-lookup"><span data-stu-id="05fb2-110">In Report Designer, your **DataReader** object is used to retrieve a list of fields as well as schema information about the result set.</span></span> <span data-ttu-id="05fb2-111">這是透過實作 <xref:Microsoft.ReportingServices.DataProcessing.IDataReader> 介面的 **GetName**、**GetValue**、**GetFieldType** 和 **GetOrdinal** 方法來完成。</span><span class="sxs-lookup"><span data-stu-id="05fb2-111">This is accomplished by implementing the **GetName**, **GetValue**, **GetFieldType,** and **GetOrdinal** methods of the <xref:Microsoft.ReportingServices.DataProcessing.IDataReader> interface.</span></span>  
  
 <span data-ttu-id="05fb2-112"><xref:Microsoft.ReportingServices.DataProcessing.IDataReaderExtension> 介面可讓您提供有關結果集的特定彙總資訊。</span><span class="sxs-lookup"><span data-stu-id="05fb2-112">The <xref:Microsoft.ReportingServices.DataProcessing.IDataReaderExtension> interface allows you to supply specific aggregation information about your result set.</span></span> <span data-ttu-id="05fb2-113">如需範例 **DataReader** 類別實作，請參閱 [SQL Server Reporting Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=177889) (SQL Server Reporting Services 產品範例)。</span><span class="sxs-lookup"><span data-stu-id="05fb2-113">For a sample **DataReader** class implementation, see [SQL Server Reporting Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=177889).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05fb2-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="05fb2-114">See Also</span></span>  
 <span data-ttu-id="05fb2-115">[Reporting Services 延伸模組](../reporting-services-extensions.md) </span><span class="sxs-lookup"><span data-stu-id="05fb2-115">[Reporting Services Extensions](../reporting-services-extensions.md) </span></span>  
 <span data-ttu-id="05fb2-116">[實作資料處理延伸模組](implementing-a-data-processing-extension.md) </span><span class="sxs-lookup"><span data-stu-id="05fb2-116">[Implementing a Data Processing Extension](implementing-a-data-processing-extension.md) </span></span>  
 [<span data-ttu-id="05fb2-117">Reporting Services 延伸模組程式庫</span><span class="sxs-lookup"><span data-stu-id="05fb2-117">Reporting Services Extension Library</span></span>](../reporting-services-extension-library.md)  
  
  
