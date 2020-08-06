---
title: 實作轉譯延伸模組 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- rendering extensions [Reporting Services]
- custom rendering extensions [Reporting Services]
- transformations [Reporting Services]
- extensions [Reporting Services], rendering
- rendering extensions [Reporting Services], implementing
ms.assetid: 4a5c64f5-2391-4597-ba3f-81d265b23703
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 03deb7c818de8d875f69b585ae6015fc178e707d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596533"
---
# <a name="implementing-a-rendering-extension"></a><span data-ttu-id="6983f-102">實作轉譯延伸模組</span><span class="sxs-lookup"><span data-stu-id="6983f-102">Implementing a Rendering Extension</span></span>
  <span data-ttu-id="6983f-103">轉譯延伸模組是報表伺服器的元件或模組，可將報表資料與配置資訊轉換成裝置特定的格式。</span><span class="sxs-lookup"><span data-stu-id="6983f-103">A rendering extension is a component or module of a report server that transforms report data and layout information into a device-specific format.</span></span> <span data-ttu-id="6983f-104">SQL Server Reporting Services 包含六個轉譯延伸模組：HTML、Excel、Word、CSV 或 Text、XML、Image 和 PDF。</span><span class="sxs-lookup"><span data-stu-id="6983f-104">SQL Server Reporting Services includes six rendering extensions: HTML, Excel, Word, CSV or Text, XML, Image, and PDF.</span></span> <span data-ttu-id="6983f-105">您可以建立其他轉譯延伸模組，以產生其他格式的報表。</span><span class="sxs-lookup"><span data-stu-id="6983f-105">You can create additional rendering extensions to generate reports in other formats.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6983f-106">若要決定可以使用哪些轉譯延伸模組，您可以檢視在 RSReportServer.config 檔案中已安裝的延伸模組清單。</span><span class="sxs-lookup"><span data-stu-id="6983f-106">To determine which rendering extensions are available, you can view the list of installed extensions in the RSReportServer.config file.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6983f-107">本節內容</span><span class="sxs-lookup"><span data-stu-id="6983f-107">In This Section</span></span>  
 [<span data-ttu-id="6983f-108">轉譯延伸模組概觀</span><span class="sxs-lookup"><span data-stu-id="6983f-108">Rendering Extensions Overview</span></span>](rendering-extensions-overview.md)  
 <span data-ttu-id="6983f-109">介紹如何撰寫 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 的自訂轉譯延伸模組。</span><span class="sxs-lookup"><span data-stu-id="6983f-109">Introduces how to write a custom rendering extension for [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].</span></span>  
  
 [<span data-ttu-id="6983f-110">實作 IRenderingExtension 介面</span><span class="sxs-lookup"><span data-stu-id="6983f-110">Implementing the IRenderingExtension Interface</span></span>](implementing-the-irenderingextension-interface.md)  
 <span data-ttu-id="6983f-111">描述轉譯延伸模組的屬性。</span><span class="sxs-lookup"><span data-stu-id="6983f-111">Describes the attributes of a rendering extension.</span></span>  
  
 [<span data-ttu-id="6983f-112">部署轉譯延伸模組</span><span class="sxs-lookup"><span data-stu-id="6983f-112">Deploying a Rendering Extension</span></span>](deploying-a-rendering-extension.md)  
 <span data-ttu-id="6983f-113">描述如何在報表伺服器上部署轉譯延伸模組。</span><span class="sxs-lookup"><span data-stu-id="6983f-113">Describes how to deploy a rendering extension on a report server.</span></span>  
  
 [<span data-ttu-id="6983f-114">移除轉譯延伸模組</span><span class="sxs-lookup"><span data-stu-id="6983f-114">Removing a Rendering Extension</span></span>](removing-a-rendering-extension.md)  
 <span data-ttu-id="6983f-115">描述如何從報表伺服器移除轉譯延伸模組。</span><span class="sxs-lookup"><span data-stu-id="6983f-115">Describes how to remove a rendering extension from a report server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6983f-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6983f-116">See Also</span></span>  
 <span data-ttu-id="6983f-117">[Reporting Services 延伸模組](../reporting-services-extensions.md) </span><span class="sxs-lookup"><span data-stu-id="6983f-117">[Reporting Services Extensions](../reporting-services-extensions.md) </span></span>  
 [<span data-ttu-id="6983f-118">Reporting Services 延伸模組程式庫</span><span class="sxs-lookup"><span data-stu-id="6983f-118">Reporting Services Extension Library</span></span>](../reporting-services-extension-library.md)  
  
  
