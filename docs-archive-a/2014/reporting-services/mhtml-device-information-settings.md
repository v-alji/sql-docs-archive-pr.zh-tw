---
title: MHTML 裝置資訊設定 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- device information settings [Reporting Services], MHTML rendering
- MHTML [Reporting Services]
ms.assetid: 60b85dd8-b4fb-4ad9-be6a-e7c89ac076fe
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 076a0179871775984799fc8ce5366a220f812867
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598246"
---
# <a name="mhtml-device-information-settings"></a><span data-ttu-id="231a8-102">MHTML 裝置資訊設定</span><span class="sxs-lookup"><span data-stu-id="231a8-102">MHTML Device Information Settings</span></span>
  <span data-ttu-id="231a8-103">下表列出以 Web 封存 (MHTML) 格式轉譯報表的裝置資訊設定。</span><span class="sxs-lookup"><span data-stu-id="231a8-103">The following table lists the device information settings for rendering reports in Web archive (MHTML) format.</span></span>  
  
|<span data-ttu-id="231a8-104">設定</span><span class="sxs-lookup"><span data-stu-id="231a8-104">Setting</span></span>|<span data-ttu-id="231a8-105">值</span><span class="sxs-lookup"><span data-stu-id="231a8-105">Value</span></span>|  
|-------------|-----------|  
|<span data-ttu-id="231a8-106">**JavaScript**</span><span class="sxs-lookup"><span data-stu-id="231a8-106">**JavaScript**</span></span>|<span data-ttu-id="231a8-107">指出在轉譯的報表中是否支援 JavaScript。</span><span class="sxs-lookup"><span data-stu-id="231a8-107">Indicates whether JavaScript is supported in the rendered report.</span></span>|  
|<span data-ttu-id="231a8-108">**OutlookCompat**</span><span class="sxs-lookup"><span data-stu-id="231a8-108">**OutlookCompat**</span></span>|<span data-ttu-id="231a8-109">指出是否要使用額外中繼資料轉譯，讓報表在 Outlook 中有較佳的外觀。</span><span class="sxs-lookup"><span data-stu-id="231a8-109">Indicates whether to render with extra metadata that makes the report look better in Outlook.</span></span> <span data-ttu-id="231a8-110">預設值是 `true`。</span><span class="sxs-lookup"><span data-stu-id="231a8-110">The default value is `true`.</span></span>|  
|<span data-ttu-id="231a8-111">**MHTML 片段**</span><span class="sxs-lookup"><span data-stu-id="231a8-111">**MHTML Fragment**</span></span>|<span data-ttu-id="231a8-112">指出是否建立 MHTML 片段來取代完整的 MHTML 文件。</span><span class="sxs-lookup"><span data-stu-id="231a8-112">Indicates whether an MHTML fragment is created in place of a full MHTML document.</span></span> <span data-ttu-id="231a8-113">MHTML 片段會在 TABLE 元素中包含報表內容，並省略 HTML 和 BODY 元素。</span><span class="sxs-lookup"><span data-stu-id="231a8-113">An MHTML fragment includes the report content in a TABLE element and omits the HTML and BODY elements.</span></span> <span data-ttu-id="231a8-114">預設值是 `false`。</span><span class="sxs-lookup"><span data-stu-id="231a8-114">The default value is `false`.</span></span>|  
|<span data-ttu-id="231a8-115">**DataVisualizationFitSizing**</span><span class="sxs-lookup"><span data-stu-id="231a8-115">**DataVisualizationFitSizing**</span></span>|<span data-ttu-id="231a8-116">指示資料在 Tablix 內的視覺效果調整行為。</span><span class="sxs-lookup"><span data-stu-id="231a8-116">Indicates data visualization fit behavior when inside a tablix.</span></span> <span data-ttu-id="231a8-117">其中包括圖表、量測計和地圖。</span><span class="sxs-lookup"><span data-stu-id="231a8-117">This includes chart, gauge, and map.</span></span><br /><br /> <span data-ttu-id="231a8-118">可能的值為 **[近似]** 和 **[精確]** 。</span><span class="sxs-lookup"><span data-stu-id="231a8-118">The possible values are **Approximate** and **Exact**.</span></span><br /><br /> <span data-ttu-id="231a8-119">預設值為 **[近似]** 。</span><span class="sxs-lookup"><span data-stu-id="231a8-119">The default value is **Approximate**.</span></span> <span data-ttu-id="231a8-120">如果從 **rsreportserver.config** 檔案中移除此設定，則預設行為是 **[精確]** 。</span><span class="sxs-lookup"><span data-stu-id="231a8-120">If the setting is removed from the **rsreportserver.config** file then the default behavior is **Exact**.</span></span><br /><br /> <span data-ttu-id="231a8-121">啟用 **[精確]** 可能會影響效能，因為判斷精確大小的處理所花的時間可能會比較長。</span><span class="sxs-lookup"><span data-stu-id="231a8-121">Enabling **Exact** may have performance impact because the processing to determine the exact size may take longer.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="231a8-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="231a8-122">See Also</span></span>  
 <xref:ReportExecution2005.ReportExecutionService.Render%2A>   
 <span data-ttu-id="231a8-123">[將裝置資訊設定傳遞至轉譯延伸模組](report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md) </span><span class="sxs-lookup"><span data-stu-id="231a8-123">[Passing Device Information Settings to Rendering Extensions](report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md) </span></span>  
 <span data-ttu-id="231a8-124">[在 RSReportServer.Config 中自訂轉譯延伸模組參數](customize-rendering-extension-parameters-in-rsreportserver-config.md) </span><span class="sxs-lookup"><span data-stu-id="231a8-124">[Customize Rendering Extension Parameters in RSReportServer.Config](customize-rendering-extension-parameters-in-rsreportserver-config.md) </span></span>  
 [<span data-ttu-id="231a8-125">技術參考 &#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="231a8-125">Technical Reference &#40;SSRS&#41;</span></span>](../../2014/reporting-services/technical-reference-ssrs.md)  
  
  
