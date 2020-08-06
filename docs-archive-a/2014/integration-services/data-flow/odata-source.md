---
title: OData 來源 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- SQL12.DTS.DESIGNER.ODATASOURCE.F1
ms.assetid: cc9003c9-638e-432b-867e-e949d50cec90
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 98b14ef034597f6098f70386ca41c1b90be86500
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708498"
---
# <a name="odata-source"></a><span data-ttu-id="54898-102">OData 來源</span><span class="sxs-lookup"><span data-stu-id="54898-102">OData Source</span></span>
  <span data-ttu-id="54898-103">您可使用 SSIS 封裝中的 OData 來源元件，從開放式資料通訊協定 (OData) 服務取用資料。</span><span class="sxs-lookup"><span data-stu-id="54898-103">You use the OData Source component in an SSIS package to consume data from Open Data Protocol (OData) services.</span></span> <span data-ttu-id="54898-104">此元件支援 OData v2 和 v3 通訊協定以及 ATOM 和 JSON 資料格式。</span><span class="sxs-lookup"><span data-stu-id="54898-104">The component supports the OData v2 and v3 protocols, as well as the ATOM and JSON data formats.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="54898-105">OData 來源可用來從 SharePoint 清單讀取。</span><span class="sxs-lookup"><span data-stu-id="54898-105">The OData Source can be used to read from SharePoint lists.</span></span> <span data-ttu-id="54898-106">若要查看 SharePoint 伺服器上的所有清單，請使用下列 URL： HTTP:// \<server> /_vti_bin/listdata.svc。</span><span class="sxs-lookup"><span data-stu-id="54898-106">To see all lists on your SharePoint server, use the following URL: http://\<server>/_vti_bin/ListData.svc.</span></span> <span data-ttu-id="54898-107">如需 SharePoint URL 慣例的詳細資訊，請參閱 [SharePoint Foundation REST 介面](https://msdn.microsoft.com/library/ff521587.aspx)。</span><span class="sxs-lookup"><span data-stu-id="54898-107">For more information about SharePoint URL conventions, see [SharePoint Foundation REST Interface](https://msdn.microsoft.com/library/ff521587.aspx).</span></span>  
  
## <a name="odata-format"></a><span data-ttu-id="54898-108">OData 格式</span><span class="sxs-lookup"><span data-stu-id="54898-108">OData Format</span></span>  
 <span data-ttu-id="54898-109">大部分的 OData 服務都會傳回多種格式的結果。</span><span class="sxs-lookup"><span data-stu-id="54898-109">Most OData services return results in multiple formats.</span></span> <span data-ttu-id="54898-110">您可使用 $format 查詢選項來指定結果集的格式。</span><span class="sxs-lookup"><span data-stu-id="54898-110">You can specify the format of the result set by using the $format query option.</span></span> <span data-ttu-id="54898-111">類似 JSON 和 JSON Light 的格式要比 ATOM/XML 更有效率，而且在傳輸大量資料時可能會提供更好的效能。</span><span class="sxs-lookup"><span data-stu-id="54898-111">Formats such as JSON and JSON Light are more efficient than ATOM/XML, and may give you better performance when transferring large amounts of data.</span></span> <span data-ttu-id="54898-112">下表提供範例測試的結果。</span><span class="sxs-lookup"><span data-stu-id="54898-112">The following table provides results from sample tests.</span></span> <span data-ttu-id="54898-113">如您所見，當從 ATOM 切換到 JSON 時有 30-53% 的效能提升，而且當從 ATOM 切換到新的 JSON light 格式時有 67% 的效能提升 (適用於 WCF Data Services 5.1)。</span><span class="sxs-lookup"><span data-stu-id="54898-113">As you can see, there was a 30-53% performance gain when switching from ATOM to JSON and 67% performance gain when switching from ATOM to the new JSON light format (available in WCF Data Services 5.1).</span></span>  
  
|||||  
|-|-|-|-|  
|<span data-ttu-id="54898-114">資料列</span><span class="sxs-lookup"><span data-stu-id="54898-114">Rows</span></span>|<span data-ttu-id="54898-115">ATOM</span><span class="sxs-lookup"><span data-stu-id="54898-115">ATOM</span></span>|<span data-ttu-id="54898-116">JSON</span><span class="sxs-lookup"><span data-stu-id="54898-116">JSON</span></span>|<span data-ttu-id="54898-117">JSON (Light)</span><span class="sxs-lookup"><span data-stu-id="54898-117">JSON (Light)</span></span>|  
|<span data-ttu-id="54898-118">10000</span><span class="sxs-lookup"><span data-stu-id="54898-118">10000</span></span>|<span data-ttu-id="54898-119">113 秒</span><span class="sxs-lookup"><span data-stu-id="54898-119">113 seconds</span></span>|<span data-ttu-id="54898-120">74 秒</span><span class="sxs-lookup"><span data-stu-id="54898-120">74 seconds</span></span>|<span data-ttu-id="54898-121">68 秒</span><span class="sxs-lookup"><span data-stu-id="54898-121">68 seconds</span></span>|  
|<span data-ttu-id="54898-122">1000000</span><span class="sxs-lookup"><span data-stu-id="54898-122">1000000</span></span>|<span data-ttu-id="54898-123">1110 秒</span><span class="sxs-lookup"><span data-stu-id="54898-123">1110 seconds</span></span>|<span data-ttu-id="54898-124">853 秒</span><span class="sxs-lookup"><span data-stu-id="54898-124">853 seconds</span></span>|<span data-ttu-id="54898-125">665 秒</span><span class="sxs-lookup"><span data-stu-id="54898-125">665 seconds</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="54898-126">SSIS OData 來源會使用 ODataLib 5.5.0 來剖析 OData 摘要，而且它可以讀取此程式庫所支援的所有格式。</span><span class="sxs-lookup"><span data-stu-id="54898-126">The SSIS OData Source uses ODataLib 5.5.0 to parse OData feeds and it can read all formats supported by this library.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="54898-127">本節內容</span><span class="sxs-lookup"><span data-stu-id="54898-127">In This Section</span></span>  
  
-   [<span data-ttu-id="54898-128">安裝及解除安裝 OData 來源元件</span><span class="sxs-lookup"><span data-stu-id="54898-128">Install and Uninstall OData Source Component</span></span>](../install-and-uninstall-odata-source-component.md)  
  
-   [<span data-ttu-id="54898-129">教學課程：使用 &#91;SSIS 的 OData 來源&#93;</span><span class="sxs-lookup"><span data-stu-id="54898-129">Tutorial: Using the OData Source &#91;SSIS&#93;</span></span>](tutorial-using-the-odata-source.md)  
  
-   [<span data-ttu-id="54898-130">在執行階段修改 OData 來源查詢</span><span class="sxs-lookup"><span data-stu-id="54898-130">Modify OData Source Query at Runtime</span></span>](modify-odata-source-query-at-runtime.md)  
  
-   <span data-ttu-id="54898-131">[OData 來源編輯器 &#40;[連線] 頁面&#41;](../odata-source-editor-connection-page.md)</span><span class="sxs-lookup"><span data-stu-id="54898-131">[OData Source Editor &#40;Connection Page&#41;](../odata-source-editor-connection-page.md)</span></span>  
  
-   [<span data-ttu-id="54898-132">OData 來源編輯器 &#40;資料行頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="54898-132">OData Source Editor &#40;Columns Page&#41;</span></span>](../odata-source-editor-columns-page.md)  
  
-   <span data-ttu-id="54898-133">[OData 來源編輯器 &#40;[錯誤輸出] 頁面&#41;](../odata-source-editor-error-output-page.md)</span><span class="sxs-lookup"><span data-stu-id="54898-133">[OData Source Editor &#40;Error Output Page&#41;](../odata-source-editor-error-output-page.md)</span></span>  
  
-   [<span data-ttu-id="54898-134">OData 來源屬性</span><span class="sxs-lookup"><span data-stu-id="54898-134">OData Source Properties</span></span>](odata-source-properties.md)  
  
## <a name="see-also"></a><span data-ttu-id="54898-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="54898-135">See Also</span></span>  
 [<span data-ttu-id="54898-136">OData 連接管理員</span><span class="sxs-lookup"><span data-stu-id="54898-136">OData Connection Manager</span></span>](../connection-manager/odata-connection-manager.md)  
  
  
