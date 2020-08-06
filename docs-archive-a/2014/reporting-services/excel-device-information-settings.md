---
title: Excel 裝置資訊設定 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- device information settings [Reporting Services], Excel rendering
- Excel [Reporting Services], rendering
ms.assetid: bb5f3566-f033-4470-be87-1f52fb7a4ab6
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d71c83195c8f91984bbbce95bd00402928fdb36e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703882"
---
# <a name="excel-device-information-settings"></a><span data-ttu-id="0c3e8-102">Excel 裝置資訊設定</span><span class="sxs-lookup"><span data-stu-id="0c3e8-102">Excel Device Information Settings</span></span>
  <span data-ttu-id="0c3e8-103">下表列出以 [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] 格式轉譯的裝置資訊設定。</span><span class="sxs-lookup"><span data-stu-id="0c3e8-103">The following table lists the device information settings for rendering in [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] format.</span></span>  
  
|<span data-ttu-id="0c3e8-104">設定</span><span class="sxs-lookup"><span data-stu-id="0c3e8-104">Setting</span></span>|<span data-ttu-id="0c3e8-105">值</span><span class="sxs-lookup"><span data-stu-id="0c3e8-105">Value</span></span>|  
|-------------|-----------|  
|<span data-ttu-id="0c3e8-106">**OmitDocumentMap**</span><span class="sxs-lookup"><span data-stu-id="0c3e8-106">**OmitDocumentMap**</span></span>|<span data-ttu-id="0c3e8-107">指出是否為支援它的報表省略文件引導模式。</span><span class="sxs-lookup"><span data-stu-id="0c3e8-107">Indicates whether to omit the document map for reports that support it.</span></span> <span data-ttu-id="0c3e8-108">預設值是 `false`。</span><span class="sxs-lookup"><span data-stu-id="0c3e8-108">The default value is `false`.</span></span>|  
|<span data-ttu-id="0c3e8-109">**OmitFormulas**</span><span class="sxs-lookup"><span data-stu-id="0c3e8-109">**OmitFormulas**</span></span>|<span data-ttu-id="0c3e8-110">指出是否從轉譯的報表省略公式。</span><span class="sxs-lookup"><span data-stu-id="0c3e8-110">Indicates whether to omit formulas from the rendered report.</span></span> <span data-ttu-id="0c3e8-111">預設值是 `false`。</span><span class="sxs-lookup"><span data-stu-id="0c3e8-111">The default value is `false`.</span></span>|  
|<span data-ttu-id="0c3e8-112">`SimplePageHeade`rs</span><span class="sxs-lookup"><span data-stu-id="0c3e8-112">`SimplePageHeade`rs</span></span>|<span data-ttu-id="0c3e8-113">指出是否將報表的頁首轉譯為 Excel 頁首。</span><span class="sxs-lookup"><span data-stu-id="0c3e8-113">Indicates whether the page header of the report is rendered to the Excel page header.</span></span> <span data-ttu-id="0c3e8-114">`false` 的值指出將頁首轉譯為工作表的第一列。</span><span class="sxs-lookup"><span data-stu-id="0c3e8-114">A value of `false` indicates that the page header is rendered to the first row of the worksheet.</span></span> <span data-ttu-id="0c3e8-115">預設值是 `false`。</span><span class="sxs-lookup"><span data-stu-id="0c3e8-115">The default value is `false`.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0c3e8-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0c3e8-116">See Also</span></span>  
 <xref:ReportExecution2005.ReportExecutionService.Render%2A>   
 <span data-ttu-id="0c3e8-117">[將裝置資訊設定傳遞至轉譯延伸模組](report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md) </span><span class="sxs-lookup"><span data-stu-id="0c3e8-117">[Passing Device Information Settings to Rendering Extensions](report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md) </span></span>  
 <span data-ttu-id="0c3e8-118">[在 RSReportServer.Config中自訂轉譯延伸模組參數](customize-rendering-extension-parameters-in-rsreportserver-config.md) </span><span class="sxs-lookup"><span data-stu-id="0c3e8-118">[Customize Rendering Extension Parameters in RSReportServer.Config](customize-rendering-extension-parameters-in-rsreportserver-config.md) </span></span>  
 [<span data-ttu-id="0c3e8-119">技術參考 &#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="0c3e8-119">Technical Reference &#40;SSRS&#41;</span></span>](../../2014/reporting-services/technical-reference-ssrs.md)  
  
  
