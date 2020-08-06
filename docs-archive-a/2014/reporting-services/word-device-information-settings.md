---
title: Word 裝置資訊設定 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- Word [Reporting Services]
- device information settings [Reporting Services], Word
ms.assetid: 28146498-fae7-4b13-b47f-6ec05aa8e057
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: ddd145c5073003a8dc189e3ed9b1bbb25dc11d09
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585002"
---
# <a name="word-device-information-settings"></a><span data-ttu-id="8130f-102">Word 裝置資訊設定</span><span class="sxs-lookup"><span data-stu-id="8130f-102">Word Device Information Settings</span></span>
  <span data-ttu-id="8130f-103">下表列出以 [!INCLUDE[ofprword](../includes/ofprword-md.md)] 格式轉譯的裝置資訊設定。</span><span class="sxs-lookup"><span data-stu-id="8130f-103">The following table lists the device information settings for rendering in [!INCLUDE[ofprword](../includes/ofprword-md.md)] format.</span></span>  
  
|<span data-ttu-id="8130f-104">設定</span><span class="sxs-lookup"><span data-stu-id="8130f-104">Setting</span></span>|<span data-ttu-id="8130f-105">值</span><span class="sxs-lookup"><span data-stu-id="8130f-105">Value</span></span>|  
|-------------|-----------|  
|`AutoFit`|<span data-ttu-id="8130f-106">`False`.</span><span class="sxs-lookup"><span data-stu-id="8130f-106">`False`.</span></span> <span data-ttu-id="8130f-107">在任何 Word 資料表上都會將 AutoFit 設定為 `false`。</span><span class="sxs-lookup"><span data-stu-id="8130f-107">AutoFit is set to `false` set on any Word table.</span></span><br /><br /> <span data-ttu-id="8130f-108">`True`.</span><span class="sxs-lookup"><span data-stu-id="8130f-108">`True`.</span></span> <span data-ttu-id="8130f-109">在每個 Word 資料表上都會將 AutoFit 設定為 `true`。</span><span class="sxs-lookup"><span data-stu-id="8130f-109">AutoFit is set to `true` on every Word table.</span></span><br /><br /> <span data-ttu-id="8130f-110">`Never`.</span><span class="sxs-lookup"><span data-stu-id="8130f-110">`Never`.</span></span> <span data-ttu-id="8130f-111">在任何 Word 資料表上未設定 AutoFit 值，而且會將行為轉換 Word 預設值。</span><span class="sxs-lookup"><span data-stu-id="8130f-111">AutoFit values are not set on any Word table and behavior reverts to the Word default.</span></span><br /><br /> <span data-ttu-id="8130f-112">`Default`.</span><span class="sxs-lookup"><span data-stu-id="8130f-112">`Default`.</span></span> <span data-ttu-id="8130f-113">在每個邏輯頁上，AutoFit 是設定在比實體繪製區域 (排除邊界的實體頁面寬度) 更狹窄的資料表上。</span><span class="sxs-lookup"><span data-stu-id="8130f-113">AutoFit is set on tables that are narrower than the physical drawing area (physical page width excluding margins) per logical page.</span></span>|  
|`ExpandToggles`|<span data-ttu-id="8130f-114">指出可以切換的所有項目是否應該以其完全展開的狀態來轉譯。</span><span class="sxs-lookup"><span data-stu-id="8130f-114">Indicates whether all items that can be toggled should render in their fully-expanded state.</span></span> <span data-ttu-id="8130f-115">預設值是 `false`。</span><span class="sxs-lookup"><span data-stu-id="8130f-115">The default value is `false`.</span></span>|  
|`FixedPageWidth`|<span data-ttu-id="8130f-116">指定寫入 DOC 檔案的「頁面寬度」是否將配合「報表主體」中最大頁面的寬度來增加。</span><span class="sxs-lookup"><span data-stu-id="8130f-116">Indicates whether the Page Width written to the DOC file will grow to accommodate the width of the largest page in the Report Body.</span></span> <span data-ttu-id="8130f-117">預設值是 `false`。</span><span class="sxs-lookup"><span data-stu-id="8130f-117">The default value is `false`.</span></span>|  
|<span data-ttu-id="8130f-118">**OmitHyperlinks**</span><span class="sxs-lookup"><span data-stu-id="8130f-118">**OmitHyperlinks**</span></span>|<span data-ttu-id="8130f-119">指定在設定 Hyperlink 動作的位置上，是否在所有的項目上省略該動作。</span><span class="sxs-lookup"><span data-stu-id="8130f-119">Indicates whether to omit the Hyperlink action on all items where it is set.</span></span> <span data-ttu-id="8130f-120">預設值為 `false`</span><span class="sxs-lookup"><span data-stu-id="8130f-120">The default value is `false`</span></span>|  
|`OmitDrillthroughs`|<span data-ttu-id="8130f-121">指定在設定 Drillthrough 動作的位置上，是否在所有的項目上省略該動作。</span><span class="sxs-lookup"><span data-stu-id="8130f-121">Indicates whether to omit the Drillthrough action on all items where it is set.</span></span> <span data-ttu-id="8130f-122">預設值為 `false`</span><span class="sxs-lookup"><span data-stu-id="8130f-122">The default value is `false`</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8130f-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8130f-123">See Also</span></span>  
 <span data-ttu-id="8130f-124">[將裝置資訊設定傳遞至轉譯延伸模組](report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md) </span><span class="sxs-lookup"><span data-stu-id="8130f-124">[Passing Device Information Settings to Rendering Extensions](report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md) </span></span>  
 <span data-ttu-id="8130f-125">[在 RSReportServer.Config中自訂轉譯延伸模組參數](customize-rendering-extension-parameters-in-rsreportserver-config.md) </span><span class="sxs-lookup"><span data-stu-id="8130f-125">[Customize Rendering Extension Parameters in RSReportServer.Config](customize-rendering-extension-parameters-in-rsreportserver-config.md) </span></span>  
 [<span data-ttu-id="8130f-126">技術參考 &#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="8130f-126">Technical Reference &#40;SSRS&#41;</span></span>](../../2014/reporting-services/technical-reference-ssrs.md)  
  
  
