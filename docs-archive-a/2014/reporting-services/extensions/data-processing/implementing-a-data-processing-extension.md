---
title: 實作資料處理延伸模組 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- custom data processing extensions [Reporting Services]
- data sources [Reporting Services], data processing extensions
- data processing extensions [Reporting Services]
- extensions [Reporting Services], data processing
ms.assetid: 8dc2b44e-5ad9-411d-a29f-7213e29321a9
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 5a1b7668f2319e742dcf3f1969fc3c5cc85cd7eb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708950"
---
# <a name="implementing-a-data-processing-extension"></a><span data-ttu-id="7f979-102">實作資料處理延伸模組</span><span class="sxs-lookup"><span data-stu-id="7f979-102">Implementing a Data Processing Extension</span></span>
  <span data-ttu-id="7f979-103">在 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 中的資料處理延伸模組，可讓您連接到資料來源並擷取資料。</span><span class="sxs-lookup"><span data-stu-id="7f979-103">Data processing extensions in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] enable you to connect to a data source and retrieve data.</span></span> <span data-ttu-id="7f979-104">它們也可當做資料來源與資料集之間的橋樑。</span><span class="sxs-lookup"><span data-stu-id="7f979-104">They also serve as a bridge between a data source and a dataset.</span></span> <span data-ttu-id="7f979-105">因為 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 資料處理延伸模組是依照 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 資料提供者介面子集建立的。</span><span class="sxs-lookup"><span data-stu-id="7f979-105">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] data processing extensions are modeled after a subset of the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] data provider interfaces.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7f979-106">本節內容</span><span class="sxs-lookup"><span data-stu-id="7f979-106">In This Section</span></span>  
 [<span data-ttu-id="7f979-107">資料處理延伸模組概觀</span><span class="sxs-lookup"><span data-stu-id="7f979-107">Data Processing Extensions Overview</span></span>](data-processing-extensions-overview.md)  
 <span data-ttu-id="7f979-108">介紹如何為 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 撰寫自訂資料處理延伸模組。</span><span class="sxs-lookup"><span data-stu-id="7f979-108">Introduces how to write a custom data processing extension for [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].</span></span>  
  
 [<span data-ttu-id="7f979-109">準備實作資料處理延伸模組</span><span class="sxs-lookup"><span data-stu-id="7f979-109">Preparing to Implement a Data Processing Extension</span></span>](preparing-to-implement-a-data-processing-extension.md)  
 <span data-ttu-id="7f979-110">描述實作 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 資料處理延伸模組時可用的介面，以及您何時需要實作特定的介面。</span><span class="sxs-lookup"><span data-stu-id="7f979-110">Describes the interfaces available when implementing an [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] data processing extension, as well as when you are required to implement a particular interface.</span></span>  
  
 [<span data-ttu-id="7f979-111">建立資料處理延伸模組程式庫</span><span class="sxs-lookup"><span data-stu-id="7f979-111">Creating a Data Processing Extension Library</span></span>](creating-a-data-processing-extension-library.md)  
 <span data-ttu-id="7f979-112">描述為 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 資料處理延伸模組指派命名空間，以及將資料處理延伸模組編譯成為程式庫 DLL。</span><span class="sxs-lookup"><span data-stu-id="7f979-112">Describes assigning a namespace for your [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] data processing extension and compiling your data processing extension into a library DLL.</span></span>  
  
 [<span data-ttu-id="7f979-113">為資料處理延伸模組實作連接類別</span><span class="sxs-lookup"><span data-stu-id="7f979-113">Implementing a Connection Class for a Data Processing Extension</span></span>](implementing-a-connection-class-for-a-data-processing-extension.md)  
 <span data-ttu-id="7f979-114">描述連線的屬性，以及如何為您的資料處理延伸模組實作自己的 **Connection** 類別。</span><span class="sxs-lookup"><span data-stu-id="7f979-114">Describes the attributes of a connection and how to implement your own **Connection** class for your data processing extension.</span></span>  
  
 [<span data-ttu-id="7f979-115">為資料處理延伸模組實作命令類別</span><span class="sxs-lookup"><span data-stu-id="7f979-115">Implementing a Command Class for a Data Processing Extension</span></span>](implementing-a-command-class-for-a-data-processing-extension.md)  
 <span data-ttu-id="7f979-116">描述命令的屬性，以及如何為您的資料處理延伸模組實作自己的 **Command** 類別。</span><span class="sxs-lookup"><span data-stu-id="7f979-116">Describes the attributes of a command, and how to implement your own **Command** class for your data processing extension.</span></span>  
  
 [<span data-ttu-id="7f979-117">為資料處理延伸模組實作資料讀取元類別</span><span class="sxs-lookup"><span data-stu-id="7f979-117">Implementing a DataReader Class for a Data Processing Extension</span></span>](implementing-a-datareader-class-for-a-data-processing-extension.md)  
 <span data-ttu-id="7f979-118">描述資料讀取器的屬性，以及如何為您的資料處理延伸模組實作自己的 **DataReader** 類別。</span><span class="sxs-lookup"><span data-stu-id="7f979-118">Describes the attributes of a data reader and how to implement your own **DataReader** class for your data processing extension.</span></span>  
  
 [<span data-ttu-id="7f979-119">透過 Reporting Services 使用外部資料集</span><span class="sxs-lookup"><span data-stu-id="7f979-119">Using an External Dataset with Reporting Services</span></span>](using-an-external-dataset-with-reporting-services.md)  
 <span data-ttu-id="7f979-120">描述如何向要取用的報表伺服器公開自訂 **DataSet** 物件。</span><span class="sxs-lookup"><span data-stu-id="7f979-120">Describes how to expose your custom **DataSet** objects to the report server for consumption.</span></span>  
  
 [<span data-ttu-id="7f979-121">部署資料處理延伸模組</span><span class="sxs-lookup"><span data-stu-id="7f979-121">Deploying a Data Processing Extension</span></span>](deploying-a-data-processing-extension.md)  
 <span data-ttu-id="7f979-122">描述如何部署您的資料處理延伸模組。</span><span class="sxs-lookup"><span data-stu-id="7f979-122">Describes how to deploy your data processing extension.</span></span>  
  
 [<span data-ttu-id="7f979-123">對資料處理延伸模組程式碼進行偵錯</span><span class="sxs-lookup"><span data-stu-id="7f979-123">Debugging Data Processing Extension Code</span></span>](debugging-data-processing-extension-code.md)  
 <span data-ttu-id="7f979-124">描述如何在資料處理延伸模組中偵錯程式碼。</span><span class="sxs-lookup"><span data-stu-id="7f979-124">Describes how to debug code in your data processing extensions.</span></span>  
  
 [<span data-ttu-id="7f979-125">移除資料處理延伸模組</span><span class="sxs-lookup"><span data-stu-id="7f979-125">Removing a Data Processing Extension</span></span>](removing-a-data-processing-extension.md)  
 <span data-ttu-id="7f979-126">描述如何從報表伺服器或是報表設計師移除資料處理延伸模組。</span><span class="sxs-lookup"><span data-stu-id="7f979-126">Describes how to remove a data processing extension from a report server or Report Designer.</span></span>  
  
 <span data-ttu-id="7f979-127">如需完全實作的資料處理延伸模組的範例，請參閱 [SQL Server Reporting Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=177889) (SQL Server Reporting Services 產品範例)。</span><span class="sxs-lookup"><span data-stu-id="7f979-127">For a sample of a fully implemented data processing extension, see [SQL Server Reporting Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=177889).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f979-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7f979-128">See Also</span></span>  
 <span data-ttu-id="7f979-129">[Reporting Services 延伸模組](../reporting-services-extensions.md) </span><span class="sxs-lookup"><span data-stu-id="7f979-129">[Reporting Services Extensions](../reporting-services-extensions.md) </span></span>  
 [<span data-ttu-id="7f979-130">Reporting Services 延伸模組程式庫</span><span class="sxs-lookup"><span data-stu-id="7f979-130">Reporting Services Extension Library</span></span>](../reporting-services-extension-library.md)  
  
  
