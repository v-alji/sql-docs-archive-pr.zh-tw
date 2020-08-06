---
title: 移除轉譯延伸模組 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- deleting rendering extensions
- removing rendering extensions
- rendering extensions [Reporting Services], removing
ms.assetid: 2abfebfb-065f-45cc-a904-c914394cf900
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 77a8a9ac44b35f338f978913985617e4f264ddb7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596531"
---
# <a name="removing-a-rendering-extension"></a><span data-ttu-id="6054c-102">移除轉譯延伸模組</span><span class="sxs-lookup"><span data-stu-id="6054c-102">Removing a Rendering Extension</span></span>
  <span data-ttu-id="6054c-103">若要移除轉譯 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 延伸模組，請直接 `Extension` 從 rsreportserver.config 檔案中移除轉譯延伸模組的元素，該檔案位於 **%ProgramFiles%\Microsoft SQL Server \ MSRS10_50 中。 \<Instance Name>\Reporting Services\ReportServer**資料夾。</span><span class="sxs-lookup"><span data-stu-id="6054c-103">To remove a [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] rendering extension, simply remove the `Extension` element for your rendering extension from the rsreportserver.config file, located in **%ProgramFiles%\Microsoft SQL Server\MSRS10_50.\<Instance Name>\Reporting Services\ReportServer** folder.</span></span> <span data-ttu-id="6054c-104">如果您是報表設計師和報表伺服器的專案，請一 `Extension` 並移除[Rsreportdesigner.config 設定檔](../../report-server/rsreportdesigner-configuration-file.md)中的元素。</span><span class="sxs-lookup"><span data-stu-id="6054c-104">If you made entries for a Report Designer as well as a report server, remove the `Extension` element from the [RSReportDesigner Configuration File](../../report-server/rsreportdesigner-configuration-file.md) as well.</span></span> <span data-ttu-id="6054c-105">在移除組態資訊之後，轉譯延伸模組將無法再供元件使用。</span><span class="sxs-lookup"><span data-stu-id="6054c-105">After the configuration information is removed, the rendering extension is no longer available to the component.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6054c-106">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6054c-106">See Also</span></span>  
 <span data-ttu-id="6054c-107">[Reporting Services 組態檔](../../report-server/reporting-services-configuration-files.md) </span><span class="sxs-lookup"><span data-stu-id="6054c-107">[Reporting Services Configuration Files](../../report-server/reporting-services-configuration-files.md) </span></span>  
 <span data-ttu-id="6054c-108">[實作轉譯延伸模組](implementing-a-rendering-extension.md) </span><span class="sxs-lookup"><span data-stu-id="6054c-108">[Implementing a Rendering Extension](implementing-a-rendering-extension.md) </span></span>  
 <span data-ttu-id="6054c-109">[轉譯延伸模組概觀](rendering-extensions-overview.md) </span><span class="sxs-lookup"><span data-stu-id="6054c-109">[Rendering Extensions Overview](rendering-extensions-overview.md) </span></span>  
 <span data-ttu-id="6054c-110">[實作 IRenderingExtension 介面](implementing-the-irenderingextension-interface.md) </span><span class="sxs-lookup"><span data-stu-id="6054c-110">[Implementing the IRenderingExtension Interface](implementing-the-irenderingextension-interface.md) </span></span>  
 <span data-ttu-id="6054c-111">[延伸模組的安全性考量](../security-considerations-for-extensions.md) </span><span class="sxs-lookup"><span data-stu-id="6054c-111">[Security Considerations for Extensions](../security-considerations-for-extensions.md) </span></span>  
 [<span data-ttu-id="6054c-112">部署轉譯延伸模組</span><span class="sxs-lookup"><span data-stu-id="6054c-112">Deploying a Rendering Extension</span></span>](deploying-a-rendering-extension.md)  
  
  
