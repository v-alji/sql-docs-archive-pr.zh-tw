---
title: Reporting Services 延伸模組 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- SQL Server Reporting Services, extending
- extensions [Reporting Services], about extensions
- SSIS, extending
- Reporting Services, extending
- extensions [Reporting Services]
ms.assetid: 2bf17ae4-2292-4a58-a1f0-56e99abd9b69
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 7ac942147c75424dae46d9a8e35dc57fba50755f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596525"
---
# <a name="reporting-services-extensions"></a><span data-ttu-id="5808b-102">Reporting Services 延伸模組</span><span class="sxs-lookup"><span data-stu-id="5808b-102">Reporting Services Extensions</span></span>
  <span data-ttu-id="5808b-103">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 的模組化架構是針對擴充性所設計。</span><span class="sxs-lookup"><span data-stu-id="5808b-103">The modular architecture of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] is designed for extensibility.</span></span> <span data-ttu-id="5808b-104">現在可以使用 Managed 程式碼 API，這樣您就可以輕鬆地開發、安裝和管理許多 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 元件取用的延伸模組。</span><span class="sxs-lookup"><span data-stu-id="5808b-104">A managed code API is available so that you can easily develop, install, and manage extensions consumed by many [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] components.</span></span> <span data-ttu-id="5808b-105">您可以使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 建立私人或共用組件，並新增新 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 功能以滿足不斷成長的商務需求。</span><span class="sxs-lookup"><span data-stu-id="5808b-105">You can create private or shared assemblies using the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] and add new [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] functionality to meet your evolving business needs.</span></span>  
  
 <span data-ttu-id="5808b-106">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 獨特的擴充性架構可讓開發人員擴充產品及其元件的特定功能。</span><span class="sxs-lookup"><span data-stu-id="5808b-106">The unique extensibility architecture of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] enables developers to extend specific features of the product and its components.</span></span> <span data-ttu-id="5808b-107">目前，有許多方式可用來擴充 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 的資料處理功能。</span><span class="sxs-lookup"><span data-stu-id="5808b-107">Currently, broad support exists for extending the data processing capabilities of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="5808b-108">資料處理 API 包括熟悉的 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 資料提供者建構與慣例，可讓開發人員在 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 中建立其他的資料處理延伸模組。</span><span class="sxs-lookup"><span data-stu-id="5808b-108">The data processing API includes familiar, [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] data provider constructs and conventions that enable developers to build additional data processing into [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="5808b-109">這些資料處理延伸模組會將功能加入報表伺服器與報表設計師，以將自訂資料緊密整合到報表中。</span><span class="sxs-lookup"><span data-stu-id="5808b-109">These data processing extensions add functionality to both the Report Server and Report Designer, enabling seamless integration of custom data into reports.</span></span>  
  
 <span data-ttu-id="5808b-110">傳遞延伸模組為另一個支援的延伸模組。</span><span class="sxs-lookup"><span data-stu-id="5808b-110">Another supported extension is the delivery extension.</span></span> <span data-ttu-id="5808b-111">傳遞 API 會完整整合至 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 架構，以便在傳送報表通知給使用者時使用廣泛的傳遞機制。</span><span class="sxs-lookup"><span data-stu-id="5808b-111">The delivery API is fully integrated with the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] architecture, enabling a wide variety of delivery mechanisms to be used when sending report notifications to users.</span></span> <span data-ttu-id="5808b-112">您可以擴充報表伺服器以提供自訂傳遞給使用者，也能夠擴充報表管理員的訂閱管理頁面，以啟用使用自訂傳遞延伸模組的訂閱。</span><span class="sxs-lookup"><span data-stu-id="5808b-112">You can extend the Report Server to provide custom delivery to users and you can extend the subscription management pages of Report Manager to enable subscriptions that use custom delivery extensions.</span></span>  
  
 <span data-ttu-id="5808b-113">報表定義自訂延伸模組 (RDCE) 為另一個報表伺服器延伸模組，它可以動態地自訂報表定義，再將其傳遞至處理引擎。</span><span class="sxs-lookup"><span data-stu-id="5808b-113">Another report server extension, Report Definition Customization Extension (RDCE), can dynamically customize a report definition before it is passed to the processing engine.</span></span> <span data-ttu-id="5808b-114">您可以根據使用者或語言等因素來自訂報表。</span><span class="sxs-lookup"><span data-stu-id="5808b-114">You might customize reports based on factors such as users or languages.</span></span> <span data-ttu-id="5808b-115">例如，您可能會想要為各個使用者 (例如經理或是部門成員) 實作不同的檢視，或是自訂報表，讓報表在轉譯為法文或阿拉伯文時，可以具有不同的配置。</span><span class="sxs-lookup"><span data-stu-id="5808b-115">For example, you might want to implement different views for various users such as managers or members of a department, or you might want to customize a report to have a different layout when it is rendered in French or Arabic.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5808b-116">本節內容</span><span class="sxs-lookup"><span data-stu-id="5808b-116">In This Section</span></span>  
 [<span data-ttu-id="5808b-117">延伸模組的安全性考量</span><span class="sxs-lookup"><span data-stu-id="5808b-117">Security Considerations for Extensions</span></span>](security-considerations-for-extensions.md)  
 <span data-ttu-id="5808b-118">描述與開發和部署 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 延伸模組相關的安全性問題。</span><span class="sxs-lookup"><span data-stu-id="5808b-118">Describes security issues related to developing and deploying [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] extensions.</span></span>  
  
 [<span data-ttu-id="5808b-119">實作資料處理延伸模組</span><span class="sxs-lookup"><span data-stu-id="5808b-119">Implementing a Data Processing Extension</span></span>](data-processing/implementing-a-data-processing-extension.md)  
 <span data-ttu-id="5808b-120">描述實作 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 之資料處理延伸模組的需求與步驟。</span><span class="sxs-lookup"><span data-stu-id="5808b-120">Describes the requirements and steps for implementing a data processing extension for [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span>  
  
 [<span data-ttu-id="5808b-121">實作傳遞延伸模組</span><span class="sxs-lookup"><span data-stu-id="5808b-121">Implementing a Delivery Extension</span></span>](delivery-extension/implementing-a-delivery-extension.md)  
 <span data-ttu-id="5808b-122">描述實作 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 之傳遞延伸模組的需求與步驟。</span><span class="sxs-lookup"><span data-stu-id="5808b-122">Describes the requirements and steps for implementing a delivery extension for [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span>  
  
 [<span data-ttu-id="5808b-123">實作轉譯延伸模組</span><span class="sxs-lookup"><span data-stu-id="5808b-123">Implementing a Rendering Extension</span></span>](rendering-extension/implementing-a-rendering-extension.md)  
 <span data-ttu-id="5808b-124">包含開發轉譯延伸模組的簡介。</span><span class="sxs-lookup"><span data-stu-id="5808b-124">Contains an introduction to developing rendering extensions.</span></span>  
  
 [<span data-ttu-id="5808b-125">實作安全性延伸模組</span><span class="sxs-lookup"><span data-stu-id="5808b-125">Implementing a Security Extension</span></span>](security-extension/implementing-a-security-extension.md)  
 <span data-ttu-id="5808b-126">描述實作 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 安全性延伸模組的需求與步驟。</span><span class="sxs-lookup"><span data-stu-id="5808b-126">Describes the requirements and steps for implementing a [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] security extension.</span></span>  
  
 [<span data-ttu-id="5808b-127">Reporting Services 延伸模組程式庫</span><span class="sxs-lookup"><span data-stu-id="5808b-127">Reporting Services Extension Library</span></span>](reporting-services-extension-library.md)  
 <span data-ttu-id="5808b-128">包含 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 擴充性功能之延伸模組 API 程式庫的程式設計參考。</span><span class="sxs-lookup"><span data-stu-id="5808b-128">Contains the programming reference for the extension API library for the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] extensibility features.</span></span>  
  
  
