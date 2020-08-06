---
title: 部署資料處理延伸模組 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- data processing extensions [Reporting Services], deploying
- Extension element
- deploying [Reporting Services], extensions
ms.assetid: e5c0b5a9-1386-47cb-aade-96653ecfaa54
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 84fc2d2853ce7a6aae77f313ef0f4026ad2f35cd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708965"
---
# <a name="deploying-a-data-processing-extension"></a><span data-ttu-id="e7666-102">部署資料處理延伸模組</span><span class="sxs-lookup"><span data-stu-id="e7666-102">Deploying a Data Processing Extension</span></span>
  <span data-ttu-id="e7666-103">一旦您撰寫 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 資料處理延伸模組並將其編譯成 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 程式庫之後，需要使該程式庫可供報表伺服器和報表設計師探索。</span><span class="sxs-lookup"><span data-stu-id="e7666-103">Once you have written and compiled your [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] data processing extension into a [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] library, you need to make it discoverable by the report server and by Report Designer.</span></span> <span data-ttu-id="e7666-104">完成此項動作很簡單，只要將伸模組複製到適當的目錄，並將項目加入適當的 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 組態檔即可。</span><span class="sxs-lookup"><span data-stu-id="e7666-104">This is as easy as copying the extension to the appropriate directories and adding entries to the appropriate [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] configuration files.</span></span>  
  
## <a name="configuration-file-extension-element"></a><span data-ttu-id="e7666-105">組態檔延伸模組元素</span><span class="sxs-lookup"><span data-stu-id="e7666-105">Configuration-File Extension Element</span></span>  
 <span data-ttu-id="e7666-106">部署到報表伺服器或是報表設計師的資料處理延伸模組，需要在設定檔中輸入成 **Extension** 項目。</span><span class="sxs-lookup"><span data-stu-id="e7666-106">Data processing extensions that you deploy to the report server or Report Designer need to be entered as **Extension** elements in the configuration files.</span></span> <span data-ttu-id="e7666-107">這些檔案在報表伺服器中為 RSReportServer.config，在報表設計師中為 RSReportDesigner.config。</span><span class="sxs-lookup"><span data-stu-id="e7666-107">These files are RSReportServer.config for the report server and RSReportDesigner.config for Report Designer.</span></span>  
  
 <span data-ttu-id="e7666-108">下表描述資料處理延伸模組之 **Extension** 項目的屬性。</span><span class="sxs-lookup"><span data-stu-id="e7666-108">The following table describes the attributes for the **Extension** element for data processing extensions.</span></span>  
  
|<span data-ttu-id="e7666-109">屬性</span><span class="sxs-lookup"><span data-stu-id="e7666-109">Attribute</span></span>|<span data-ttu-id="e7666-110">描述</span><span class="sxs-lookup"><span data-stu-id="e7666-110">Description</span></span>|  
|---------------|-----------------|  
|`Name`|<span data-ttu-id="e7666-111">例如，就延伸模組的維一名稱而言，"SQL" 為 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 資料處理延伸模組，或者 "OLEDB" 為 OLE DB 資料處理延伸模組。</span><span class="sxs-lookup"><span data-stu-id="e7666-111">A unique name for the extension, for example, "SQL" for the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] data processing extension or "OLEDB" for the OLE DB data processing extension.</span></span> <span data-ttu-id="e7666-112">`Name` 屬性的最大長度為 255 個字元。</span><span class="sxs-lookup"><span data-stu-id="e7666-112">The maximum length for the `Name` attribute is 255 characters.</span></span> <span data-ttu-id="e7666-113">該名稱在組態檔之 **Extension** 元素的所有元素中，必須是唯一的。</span><span class="sxs-lookup"><span data-stu-id="e7666-113">The name must be unique among all entries within the **Extension** element of a configuration file.</span></span>|  
|`Type`|<span data-ttu-id="e7666-114">以逗號分隔的清單，包括完整的命名空間以及組件的名稱。</span><span class="sxs-lookup"><span data-stu-id="e7666-114">A comma-separated list that includes the fully qualified namespace along with the name of the assembly.</span></span>|  
|`Visible`|<span data-ttu-id="e7666-115">`false` 的值指出在使用者介面中應該看不到資料處理延伸模組。</span><span class="sxs-lookup"><span data-stu-id="e7666-115">A value of `false` indicates that the data processing extension should not be visible in user interfaces.</span></span> <span data-ttu-id="e7666-116">如果沒有包括屬性，預設值是 `true`。</span><span class="sxs-lookup"><span data-stu-id="e7666-116">If the attribute is not included, the default value is `true`.</span></span>|  
  
 <span data-ttu-id="e7666-117">如需 RSReportServer.config 或 RSReportDesigner.config 檔的詳細資訊，請參閱 [Reporting Services 設定檔](../../report-server/reporting-services-configuration-files.md)。</span><span class="sxs-lookup"><span data-stu-id="e7666-117">For more information about the RSReportServer.config or RSReportDesigner.config files, see [Reporting Services Configuration Files](../../report-server/reporting-services-configuration-files.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e7666-118">本節內容</span><span class="sxs-lookup"><span data-stu-id="e7666-118">In This Section</span></span>  
  
|<span data-ttu-id="e7666-119">主題</span><span class="sxs-lookup"><span data-stu-id="e7666-119">Topic</span></span>|<span data-ttu-id="e7666-120">描述</span><span class="sxs-lookup"><span data-stu-id="e7666-120">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="e7666-121">如何：將資料處理延伸模組部署到報表伺服器</span><span class="sxs-lookup"><span data-stu-id="e7666-121">How to: Deploy a Data Processing Extension to a Report Server</span></span>](deploying-a-data-processing-extension-to-a-report-server.md)|<span data-ttu-id="e7666-122">描述如何將資料處理延伸模組部署到報表伺服器。</span><span class="sxs-lookup"><span data-stu-id="e7666-122">Describes how to deploy your data processing extension to a report server.</span></span>|  
|[<span data-ttu-id="e7666-123">如何：將資料處理延伸模組部署到報表設計師</span><span class="sxs-lookup"><span data-stu-id="e7666-123">How to: Deploy a Data Processing Extension to Report Designer</span></span>](deploying-a-data-processing-extension-to-report-designer.md)|<span data-ttu-id="e7666-124">描述如何將資料處理延伸模組部署到報表設計師。</span><span class="sxs-lookup"><span data-stu-id="e7666-124">Describes how to deploy your data processing extension to Report Designer.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e7666-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e7666-125">See Also</span></span>  
 <span data-ttu-id="e7666-126">[Reporting Services 延伸模組](../reporting-services-extensions.md) </span><span class="sxs-lookup"><span data-stu-id="e7666-126">[Reporting Services Extensions](../reporting-services-extensions.md) </span></span>  
 <span data-ttu-id="e7666-127">[執行資料處理延伸模組](implementing-a-data-processing-extension.md) </span><span class="sxs-lookup"><span data-stu-id="e7666-127">[Implementing a Data Processing Extension](implementing-a-data-processing-extension.md) </span></span>  
 [<span data-ttu-id="e7666-128">Reporting Services 延伸模組程式庫</span><span class="sxs-lookup"><span data-stu-id="e7666-128">Reporting Services Extension Library</span></span>](../reporting-services-extension-library.md)  
  
  
