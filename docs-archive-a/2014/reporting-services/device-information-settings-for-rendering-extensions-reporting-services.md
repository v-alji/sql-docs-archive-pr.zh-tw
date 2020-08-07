---
title: 轉譯延伸模組的裝置資訊設定 (Reporting Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 947b0ee1-bb35-4b4e-9527-dc501566e7d1
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f15e27e01cd43bafda3aede3deca7729f2c89756
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703914"
---
# <a name="device-information-settings-for-rendering-extensions-reporting-services"></a><span data-ttu-id="f68d6-102">轉譯延伸模組的裝置資訊設定 (Reporting Services)</span><span class="sxs-lookup"><span data-stu-id="f68d6-102">Device Information Settings for Rendering Extensions (Reporting Services)</span></span>
  <span data-ttu-id="f68d6-103">在 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]中，裝置資訊設定會用於將轉譯參數傳遞給轉譯延伸模組。</span><span class="sxs-lookup"><span data-stu-id="f68d6-103">In [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)], device information settings are used to pass rendering parameters to a rendering extension.</span></span> <span data-ttu-id="f68d6-104">每一個轉譯延伸模組都會接受一組特定的設定。</span><span class="sxs-lookup"><span data-stu-id="f68d6-104">Each rendering extension accepts a specific set of settings.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f68d6-105">本節內容</span><span class="sxs-lookup"><span data-stu-id="f68d6-105">In This Section</span></span>  
  
|<span data-ttu-id="f68d6-106">主題</span><span class="sxs-lookup"><span data-stu-id="f68d6-106">Topic</span></span>|<span data-ttu-id="f68d6-107">描述</span><span class="sxs-lookup"><span data-stu-id="f68d6-107">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="f68d6-108">ATOM 裝置資訊設定</span><span class="sxs-lookup"><span data-stu-id="f68d6-108">ATOM Device Information Settings</span></span>](../../2014/reporting-services/atom-device-information-settings.md)|<span data-ttu-id="f68d6-109">描述與符合 Atom 之轉譯輸出相關聯的裝置資訊設定。</span><span class="sxs-lookup"><span data-stu-id="f68d6-109">Describes the device information settings that are associated with Atom compliant rendering output.</span></span>|  
|[<span data-ttu-id="f68d6-110">CSV 裝置資訊設定</span><span class="sxs-lookup"><span data-stu-id="f68d6-110">CSV Device Information Settings</span></span>](csv-device-information-settings.md)|<span data-ttu-id="f68d6-111">描述與 CSV 轉譯輸出相關聯的裝置資訊設定。</span><span class="sxs-lookup"><span data-stu-id="f68d6-111">Describes the device information settings that are associated with CSV rendering output.</span></span>|  
|[<span data-ttu-id="f68d6-112">Excel 裝置資訊設定</span><span class="sxs-lookup"><span data-stu-id="f68d6-112">Excel Device Information Settings</span></span>](excel-device-information-settings.md)|<span data-ttu-id="f68d6-113">描述與 Excel 轉譯輸出相關聯的裝置資訊設定。</span><span class="sxs-lookup"><span data-stu-id="f68d6-113">Describes the device information settings that are associated with Excel rendering output.</span></span>|  
|[<span data-ttu-id="f68d6-114">Word 裝置資訊設定</span><span class="sxs-lookup"><span data-stu-id="f68d6-114">Word Device Information Settings</span></span>](word-device-information-settings.md)|<span data-ttu-id="f68d6-115">描述與 Word 轉譯輸出相關聯的裝置資訊設定。</span><span class="sxs-lookup"><span data-stu-id="f68d6-115">Describes the device information settings that are associated with Word rendering output.</span></span>|  
|[<span data-ttu-id="f68d6-116">HTML 裝置資訊設定</span><span class="sxs-lookup"><span data-stu-id="f68d6-116">HTML Device Information Settings</span></span>](html-device-information-settings.md)|<span data-ttu-id="f68d6-117">描述與 HTML 轉譯輸出相關聯的裝置資訊設定。</span><span class="sxs-lookup"><span data-stu-id="f68d6-117">Describes the device information settings that are associated with HTML rendering output.</span></span>|  
|[<span data-ttu-id="f68d6-118">影像裝置資訊設定</span><span class="sxs-lookup"><span data-stu-id="f68d6-118">Image Device Information Settings</span></span>](image-device-information-settings.md)|<span data-ttu-id="f68d6-119">描述與 IMAGE 轉譯輸出相關聯的裝置資訊設定。</span><span class="sxs-lookup"><span data-stu-id="f68d6-119">Describes the device information settings that are associated with IMAGE rendering output.</span></span>|  
|[<span data-ttu-id="f68d6-120">MHTML 裝置資訊設定</span><span class="sxs-lookup"><span data-stu-id="f68d6-120">MHTML Device Information Settings</span></span>](mhtml-device-information-settings.md)|<span data-ttu-id="f68d6-121">描述與 MHTML 轉譯輸出相關聯的裝置資訊設定。</span><span class="sxs-lookup"><span data-stu-id="f68d6-121">Describes the device information settings that are associated with MHTML rendering output.</span></span>|  
|[<span data-ttu-id="f68d6-122">PDF 裝置資訊設定</span><span class="sxs-lookup"><span data-stu-id="f68d6-122">PDF Device Information Settings</span></span>](pdf-device-information-settings.md)|<span data-ttu-id="f68d6-123">描述與 PDF 轉譯輸出相關聯的裝置資訊設定。</span><span class="sxs-lookup"><span data-stu-id="f68d6-123">Describes the device information settings that are associated with PDF rendering output.</span></span>|  
|[<span data-ttu-id="f68d6-124">XML 裝置資訊設定</span><span class="sxs-lookup"><span data-stu-id="f68d6-124">XML Device Information Settings</span></span>](xml-device-information-settings.md)|<span data-ttu-id="f68d6-125">描述與 XML 轉譯輸出相關聯的裝置資訊設定。</span><span class="sxs-lookup"><span data-stu-id="f68d6-125">Describes the device information settings that are associated with XML rendering output.</span></span>|  
|[<span data-ttu-id="f68d6-126">RGDI 裝置資訊設定</span><span class="sxs-lookup"><span data-stu-id="f68d6-126">RGDI Device Information Settings</span></span>](rgdi-device-information-settings.md)|<span data-ttu-id="f68d6-127">描述與 RGDI 轉譯輸出相關聯的裝置資訊設定。</span><span class="sxs-lookup"><span data-stu-id="f68d6-127">Describes the device information settings that are associated with RGDI rendering output.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f68d6-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f68d6-128">See Also</span></span>  
 [<span data-ttu-id="f68d6-129">在 RSReportServer.Config 中自訂轉譯延伸模組參數</span><span class="sxs-lookup"><span data-stu-id="f68d6-129">Customize Rendering Extension Parameters in RSReportServer.Config</span></span>](customize-rendering-extension-parameters-in-rsreportserver-config.md)  
  
  
