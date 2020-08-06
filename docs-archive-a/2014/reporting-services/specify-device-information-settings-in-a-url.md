---
title: 在 URL 中指定裝置資訊設定 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- device information settings [Reporting Services], URLs
- URL access [Reporting Services], device information settings
ms.assetid: cb7f7577-c6a8-4e6f-8e60-5ec0760f29c3
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 00cd1fdc3b5fbe129ae4d51b220a11bc48b4744c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703770"
---
# <a name="specify-device-information-settings-in-a-url"></a><span data-ttu-id="781d8-102">在 URL 中指定裝置資訊設定</span><span class="sxs-lookup"><span data-stu-id="781d8-102">Specify Device Information Settings in a URL</span></span>
  <span data-ttu-id="781d8-103">裝置資訊設定是傳遞給轉譯延伸模組的參數。</span><span class="sxs-lookup"><span data-stu-id="781d8-103">Device information settings are parameters that are passed to a rendering extension.</span></span> <span data-ttu-id="781d8-104">如果您使用 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 報表伺服器 Web 服務的方法來轉譯報表，則會將 `DeviceInfo` XML 元素以輸入參數來傳遞。</span><span class="sxs-lookup"><span data-stu-id="781d8-104">If you use the methods of the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Report Server Web service to render a report, a `DeviceInfo` XML element is passed as an input parameter.</span></span> <span data-ttu-id="781d8-105">`DeviceInfo` 元素的子元素是不同的轉譯延伸模組的裝置資訊設定所特有的。</span><span class="sxs-lookup"><span data-stu-id="781d8-105">Child elements of the `DeviceInfo` element are specific to the device information settings of different rendering extensions.</span></span> <span data-ttu-id="781d8-106">您可以使用 *rc:tag=value* 參數字串，來包括 URL 中的裝置資訊設定，其中 *tag* 是要存取之裝置資訊設定元素的名稱。</span><span class="sxs-lookup"><span data-stu-id="781d8-106">You can include device information settings in a URL by using the *rc:tag=value* parameter string, where *tag* is the name of the device information settings element being accessed.</span></span> <span data-ttu-id="781d8-107">如需 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 中裝置資訊設定的詳細資訊，請參閱[將裝置資訊設定傳遞至轉譯延伸模組](report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md)。</span><span class="sxs-lookup"><span data-stu-id="781d8-107">For more information about device information settings in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)], see [Passing Device Information Settings to Rendering Extensions](report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="781d8-108">範例</span><span class="sxs-lookup"><span data-stu-id="781d8-108">Example</span></span>  
 <span data-ttu-id="781d8-109">下列範例使用影像轉譯延伸模組的 *OutputFormat* 裝置資訊來設定，以將指定報表的格式設定為 JPEG (已加入分行符號以利閱讀)：</span><span class="sxs-lookup"><span data-stu-id="781d8-109">The following example sets the format of the specified report to JPEG by using the *OutputFormat* device information setting of the image rendering extension (the line breaks have been added for legibility):</span></span>  
  
```  
http://servername/reportserver?/SampleReports  
/Employee Sales Summary&EmployeeID=38&rs:  
Command=Render&rs:Format=IMAGE&rc:OutputFormat=JPEG  
```  
  
## <a name="see-also"></a><span data-ttu-id="781d8-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="781d8-110">See Also</span></span>  
 <span data-ttu-id="781d8-111">[URL 存取 &#40;SSRS&#41;](url-access-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="781d8-111">[URL Access &#40;SSRS&#41;](url-access-ssrs.md) </span></span>  
 [<span data-ttu-id="781d8-112">URL 存取參數參考</span><span class="sxs-lookup"><span data-stu-id="781d8-112">URL Access Parameter Reference</span></span>](url-access-parameter-reference.md)  
  
  
