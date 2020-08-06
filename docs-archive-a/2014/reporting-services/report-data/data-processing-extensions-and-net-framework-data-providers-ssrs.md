---
title: 資料處理延伸模組與 .NET Framework Data Provider (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- reports [Reporting Services], data
- data processing extensions [Reporting Services]
- data providers [Reporting Services]
- data retrieval [Reporting Services]
- Reporting Services, data sources
- report data [Report Builder], accessing
ms.assetid: 42a5afb5-f4c8-4957-b1fd-77bf39afa5be
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: fd84af68af54b165c75317280bc19bb23da53366
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687518"
---
# <a name="data-processing-extensions-and-net-framework-data-providers-ssrs"></a><span data-ttu-id="324cf-102">資料處理延伸模組與 .NET Framework Data Provider (SSRS)</span><span class="sxs-lookup"><span data-stu-id="324cf-102">Data Processing Extensions and .NET Framework Data Providers (SSRS)</span></span>
  <span data-ttu-id="324cf-103">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 資料處理延伸模組是與 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]一起安裝的元件，它的設計目的是要從特定類型的資料來源擷取資料，以及提供額外功能來支援報表設計和報表處理。</span><span class="sxs-lookup"><span data-stu-id="324cf-103">A [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] data processing extension is a component installed with [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], designed to retrieve data from a specific type of data source and to provide extra functionality to support report design and report processing.</span></span> <span data-ttu-id="324cf-104">[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 資料提供者是 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 或支援 <xref:System.Data> 介面的協力廠商所提供的元件，讓您可以從特定類型的資料來源擷取和修改資料。</span><span class="sxs-lookup"><span data-stu-id="324cf-104">A [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] data provider is a component available from [!INCLUDE[msCoName](../../includes/msconame-md.md)] or third-party sources that supports <xref:System.Data> interfaces that allow you to retrieve and to modify data from a specific type of data source.</span></span>  
  
## <a name="understanding-a-data-processing-extension"></a><span data-ttu-id="324cf-105">了解資料處理延伸模組</span><span class="sxs-lookup"><span data-stu-id="324cf-105">Understanding a Data Processing Extension</span></span>  
 <span data-ttu-id="324cf-106">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 資料處理延伸模組支援 <xref:System.Data> 介面的子集。</span><span class="sxs-lookup"><span data-stu-id="324cf-106">A [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] data processing extension supports a subset of the <xref:System.Data> interfaces.</span></span> <span data-ttu-id="324cf-107">資料處理延伸模組只需要資料來源的唯讀存取權限，因此不會實作寫入和更新的介面。</span><span class="sxs-lookup"><span data-stu-id="324cf-107">Data processing extensions require only read-only access to a data source, so the interfaces for write and update are not implemented.</span></span> <span data-ttu-id="324cf-108">每一個資料處理延伸模組都可以提供自訂功能來支援報表處理。</span><span class="sxs-lookup"><span data-stu-id="324cf-108">Each data processing extension can provide custom features to support report processing.</span></span> <span data-ttu-id="324cf-109">例如，資料處理延伸模組可支援以下類型的功能：</span><span class="sxs-lookup"><span data-stu-id="324cf-109">For example, a data processing extension might support the following types of features:</span></span>  
  
-   <span data-ttu-id="324cf-110">分開管理認證與連接字串</span><span class="sxs-lookup"><span data-stu-id="324cf-110">Managing credentials separately from the connection string</span></span>  
  
-   <span data-ttu-id="324cf-111">支援多重值參數</span><span class="sxs-lookup"><span data-stu-id="324cf-111">Supporting multivalue parameters</span></span>  
  
-   <span data-ttu-id="324cf-112">擷取資料來源上所計算的伺服器彙總</span><span class="sxs-lookup"><span data-stu-id="324cf-112">Retrieving server aggregates, which are calculated on the data source</span></span>  
  
-   <span data-ttu-id="324cf-113">從資料來源擷取資料屬性及資料值</span><span class="sxs-lookup"><span data-stu-id="324cf-113">Retrieving data properties as well as data values from the data source</span></span>  
  
## <a name="understanding-a-data-provider"></a><span data-ttu-id="324cf-114">了解資料提供者</span><span class="sxs-lookup"><span data-stu-id="324cf-114">Understanding a Data Provider</span></span>  
 <span data-ttu-id="324cf-115">[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 資料提供者 (有時稱為驅動程式) 可支援一組標準 <xref:System.Data> 介面來讀取、寫入及更新資料來源上的資料。</span><span class="sxs-lookup"><span data-stu-id="324cf-115">A [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] data provider (sometimes known as a driver) supports a standard set of <xref:System.Data> interfaces for reading, writing, and updating data on a data source.</span></span> <span data-ttu-id="324cf-116">當特定類型的資料來源沒有可用的資料處理延伸模組時，可以使用資料提供者。</span><span class="sxs-lookup"><span data-stu-id="324cf-116">A data provider can be used when there is no data processing extension available for a specific type of data source.</span></span> <span data-ttu-id="324cf-117">市面上有許多可用的協力廠商標準 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 資料提供者。</span><span class="sxs-lookup"><span data-stu-id="324cf-117">Many third-party standard [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] data providers are available.</span></span>  
  
 <span data-ttu-id="324cf-118">因為 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 具有可延伸的資料提供者架構，所以您可以建置自訂的資料處理延伸模組，以包含 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 資料處理延伸模組所提供的額外功能。</span><span class="sxs-lookup"><span data-stu-id="324cf-118">Because [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] has an extensible data provider architecture, you can build a custom data processing extension to include the extra functionality supplied by [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] data processing extensions.</span></span> <span data-ttu-id="324cf-119">如需詳細資訊，請參閱＜ [Implementing a Data Processing Extension](../extensions/data-processing/implementing-a-data-processing-extension.md)＞。</span><span class="sxs-lookup"><span data-stu-id="324cf-119">For more information, see [Implementing a Data Processing Extension](../extensions/data-processing/implementing-a-data-processing-extension.md).</span></span> <span data-ttu-id="324cf-120">如需協力廠商資料處理延伸模組的資訊，請參閱協力廠商資料處理延伸模組所隨附的文件。</span><span class="sxs-lookup"><span data-stu-id="324cf-120">For third-party data processing extensions, see the documentation that comes with the third-party data processing extension.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="324cf-121">[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 資料提供者或自訂的資料處理延伸模組必須經過安裝和註冊後，才能用來存取資料來源中的資料。</span><span class="sxs-lookup"><span data-stu-id="324cf-121">A [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] data provider or custom data processing extension must be installed and registered before it can be used to access data from a data source.</span></span> <span data-ttu-id="324cf-122">資料處理延伸模組必須在報表用戶端上安裝及註冊才能撰寫報表，而且必須安裝在報表伺服器上才能檢視發行的報表。</span><span class="sxs-lookup"><span data-stu-id="324cf-122">The data processing extension must be installed and registered both on the reporting client to author the report and on the report server to view the published report.</span></span> <span data-ttu-id="324cf-123">並非所有資料提供者的設計都是在伺服器環境下運作。</span><span class="sxs-lookup"><span data-stu-id="324cf-123">Not all data providers are designed to work in a server environment.</span></span> <span data-ttu-id="324cf-124">如需詳細資訊，請參閱[註冊標準 .NET Framework Data Provider &#40;SSRS&#41;](register-a-standard-net-framework-data-provider-ssrs.md) 和[部署資料處理延伸模組](../extensions/data-processing/deploying-a-data-processing-extension.md)。</span><span class="sxs-lookup"><span data-stu-id="324cf-124">For more information, see [Register a Standard .NET Framework Data Provider &#40;SSRS&#41;](register-a-standard-net-framework-data-provider-ssrs.md).and [Deploying a Data Processing Extension](../extensions/data-processing/deploying-a-data-processing-extension.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="324cf-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="324cf-125">See Also</span></span>  
 <span data-ttu-id="324cf-126">[資料處理延伸模組概觀](../extensions/data-processing/data-processing-extensions-overview.md) </span><span class="sxs-lookup"><span data-stu-id="324cf-126">[Data Processing Extensions Overview](../extensions/data-processing/data-processing-extensions-overview.md) </span></span>  
 [<span data-ttu-id="324cf-127">報表內嵌資料集和共用資料集 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="324cf-127">Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;</span></span>](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)  
  
  
