---
title: 規劃地圖報表支援 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 5ddc97a7-7ee5-475d-bc49-3b814dce7e19
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f3d1e1774e44ae879b8c01e66289cefd4d42ee1c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707241"
---
# <a name="plan-for-map-report-support"></a><span data-ttu-id="4b282-102">對應報表支援規劃</span><span class="sxs-lookup"><span data-stu-id="4b282-102">Plan for Map Report Support</span></span>
  [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)]<span data-ttu-id="4b282-103">支援使用空間資料源的地圖報表。</span><span class="sxs-lookup"><span data-stu-id="4b282-103">supports map reports that use spatial data sources.</span></span> <span data-ttu-id="4b282-104">空間資料可以來自 SQL Server 資料庫、ESRI 形狀檔，或是隨著 Reporting Services 或報表產生器一起安裝的地圖庫。</span><span class="sxs-lookup"><span data-stu-id="4b282-104">Spatial data can come from SQL Server databases, from ESRI Shapefiles, or from the Map Gallery that is installed with either Reporting Services or Report Builder.</span></span> <span data-ttu-id="4b282-105">地圖也可以顯示 Bing 地圖底圖的背景。</span><span class="sxs-lookup"><span data-stu-id="4b282-105">A map can also display a background of Bing map tiles.</span></span> <span data-ttu-id="4b282-106">報表作者可以將指定空間資料或 Bing 地圖底圖的報表建立為動態報表並在執行階段擷取，或是指定為靜態報表並內嵌於報表定義中。</span><span class="sxs-lookup"><span data-stu-id="4b282-106">A report author can create a report that specifies spatial data or Bing map tiles as dynamic and retrieved at run time or as static and embedded in the report definition.</span></span>  
  
## <a name="support-for-bing-maps"></a><span data-ttu-id="4b282-107">Bing Map 的支援</span><span class="sxs-lookup"><span data-stu-id="4b282-107">Support for Bing Maps</span></span>  
 <span data-ttu-id="4b282-108">地圖可以包含顯示 Bing 地圖底圖的背景圖層。</span><span class="sxs-lookup"><span data-stu-id="4b282-108">Maps can include a background layer that displays Bing map tiles.</span></span> <span data-ttu-id="4b282-109">若要檢視具有地圖底圖圖層的已發行報表，報表伺服器必須設定為可從 Bing Maps Web 服務擷取圖格。</span><span class="sxs-lookup"><span data-stu-id="4b282-109">To view a published report that has a map tile layer, the report server must be configured to retrieve tiles from Bing Maps Web Services.</span></span> <span data-ttu-id="4b282-110">如需詳細資訊，請參閱 [RSReportServer Configuration File](report-server/rsreportserver-config-configuration-file.md)。</span><span class="sxs-lookup"><span data-stu-id="4b282-110">For more information, see [RSReportServer Configuration File](report-server/rsreportserver-config-configuration-file.md).</span></span>  
  
 <span data-ttu-id="4b282-111">在每個報表中，報表作者也可以指定是否要使用安全通訊端層 (SSL) 連線，自圖格伺服器擷取圖格。</span><span class="sxs-lookup"><span data-stu-id="4b282-111">In each report, report authors can specify whether to use a Secure Sockets Layer (SSL) connection to retrieve tiles from the tile server.</span></span> <span data-ttu-id="4b282-112">若要這樣做，您可以在圖格圖層的 [屬性] 窗格中，將布林值屬性 UseSecureConnection 設定為 `true` 。</span><span class="sxs-lookup"><span data-stu-id="4b282-112">To do this, in the Properties pane for the tile layer, they must set the Boolean property UseSecureConnection to `true`.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4b282-113">如需有關在報表中使用 Bing 地圖底圖的詳細資訊，請參閱 [其他使用規定](https://go.microsoft.com/fwlink/?LinkId=151371) 和 [隱私權聲明](https://go.microsoft.com/fwlink/?LinkId=151372)。</span><span class="sxs-lookup"><span data-stu-id="4b282-113">For more information about the use of Bing map tiles in your report, see [Additional Terms of Use](https://go.microsoft.com/fwlink/?LinkId=151371) and [Privacy Statement](https://go.microsoft.com/fwlink/?LinkId=151372).</span></span>  
  
## <a name="report-design-recommendations"></a><span data-ttu-id="4b282-114">報表設計建議</span><span class="sxs-lookup"><span data-stu-id="4b282-114">Report Design Recommendations</span></span>  
 <span data-ttu-id="4b282-115">好的地圖報表設計需要報表作者評估靜態與動態空間資料之間的權衡得失，並找出平衡點來服務報表使用者。</span><span class="sxs-lookup"><span data-stu-id="4b282-115">Good report design for map reports requires that the report author assess the trade-offs between static and dynamic spatial data and find a balance that serves the report users.</span></span> <span data-ttu-id="4b282-116">內嵌的地圖元素可能會大幅增加報表定義的大小，但是會減少檢視地圖報表所需的時間。</span><span class="sxs-lookup"><span data-stu-id="4b282-116">Embedded map elements can significantly increase the size of the report definition, but reduce the time that is required to view the map report.</span></span> <span data-ttu-id="4b282-117">動態地圖元素會減少報表定義的大小，但是會增加處理及檢視地圖所需的時間。</span><span class="sxs-lookup"><span data-stu-id="4b282-117">Dynamic map elements reduce the report definition size but increase the time that is required to process and view the map.</span></span> <span data-ttu-id="4b282-118">報表作者必須找到這些對立問題之間的平衡點。</span><span class="sxs-lookup"><span data-stu-id="4b282-118">The report author must find the right balance between these opposing issues.</span></span>  
  
 <span data-ttu-id="4b282-119">當報表定義大小是一個問題時，身為報表伺服器管理員的您可以鼓勵報表設計師減少報表定義中的空間資料數量。</span><span class="sxs-lookup"><span data-stu-id="4b282-119">When report definition size is an issue, as report server administrator, you can encourage report designers to reduce the amount of spatial data in a report definition.</span></span>  
  
 <span data-ttu-id="4b282-120">在下列情況下，地圖元素會內嵌在報表定義中：</span><span class="sxs-lookup"><span data-stu-id="4b282-120">Under the following conditions, map elements are embedded in the report definition:</span></span>  
  
-   <span data-ttu-id="4b282-121">建立報表時，空間資料來源位於本機檔案系統上。</span><span class="sxs-lookup"><span data-stu-id="4b282-121">When the report is created, the spatial data source is on the local file system.</span></span> <span data-ttu-id="4b282-122">其中包括來自地圖庫的空間資料，或是已經安裝在本機的 ESRI 形狀檔。</span><span class="sxs-lookup"><span data-stu-id="4b282-122">This includes spatial data from the Map Gallery or ESRI Shapefiles that have been installed locally.</span></span> <span data-ttu-id="4b282-123">根據預設，地圖精靈和地圖圖層精靈會內嵌本機檔案系統上資料來源中的空間資料。</span><span class="sxs-lookup"><span data-stu-id="4b282-123">By default, the map wizard and map layer wizard embed spatial data from data sources on the local file system.</span></span>  
  
-   <span data-ttu-id="4b282-124">報表作者可選擇以手動方式將空間資料內嵌在報表中。</span><span class="sxs-lookup"><span data-stu-id="4b282-124">The report author chooses the option to embed spatial data manually in the report.</span></span>  
  
 <span data-ttu-id="4b282-125">若要減少具有地圖的報表定義大小，報表作者可以使用下列其中一個或多個選項：</span><span class="sxs-lookup"><span data-stu-id="4b282-125">To help reduce the size of report definitions that have maps, report authors can use one or more of the following options:</span></span>  
  
-   <span data-ttu-id="4b282-126">從 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 中的報表設計師，將屬於 ESRI 形狀檔的空間資料來源加入至報表伺服器專案。</span><span class="sxs-lookup"><span data-stu-id="4b282-126">From Report Designer in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], add spatial data sources that are ESRI Shapefiles to the report server project.</span></span> <span data-ttu-id="4b282-127">當您部署此專案時，ESRI 形狀檔除了發行至報表中，也會發行至報表伺服器。</span><span class="sxs-lookup"><span data-stu-id="4b282-127">When you deploy the project, the ESRI Shapefiles are published to the report server in addition to the report.</span></span> <span data-ttu-id="4b282-128">當報表作者執行地圖精靈時，他們可以從報表伺服器專案指定空間資料來源，而地圖元素預設不會內嵌到報表定義中。</span><span class="sxs-lookup"><span data-stu-id="4b282-128">When the report author runs the Map wizard, they can specify a spatial data source from the Report Server project, and the map elements are not embedded in the report definitions by default.</span></span>  
  
-   <span data-ttu-id="4b282-129">在報表產生器中，從報表伺服器選取形狀檔，加入屬於 ESRI 形狀檔的空間資料來源。</span><span class="sxs-lookup"><span data-stu-id="4b282-129">From Report Builder, add spatial data sources that are ESRI Shapefiles by selecting Shapefiles from the report server.</span></span> <span data-ttu-id="4b282-130">當報表作者執行地圖精靈時，可以從報表伺服器瀏覽並選取空間資料來源，而地圖元素是預設為不會內嵌到報表定義中。</span><span class="sxs-lookup"><span data-stu-id="4b282-130">When the report author runs the Map wizard, they can browse to and select a spatial data source from the report server, and the map elements are not embedded in the report definitions by default.</span></span>  
  
-   <span data-ttu-id="4b282-131">當地圖資料必須為內嵌的地圖資料時，請調整檢視區置中與縮放比例，以便只包含報表所需的地圖資料。</span><span class="sxs-lookup"><span data-stu-id="4b282-131">When map data must be embedded map data, adjust the viewport center and zoom level to include just the map data that is needed for the report.</span></span>  
  
 <span data-ttu-id="4b282-132">如需詳細資訊，請[&#40;報表產生器和 SSRS&#41;對應](report-design/maps-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="4b282-132">For more information, [Maps &#40;Report Builder and SSRS&#41;](report-design/maps-report-builder-and-ssrs.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b282-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4b282-133">See Also</span></span>  
 [<span data-ttu-id="4b282-134">報表疑難排解：地圖報表 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="4b282-134">Troubleshoot Reports: Map Reports &#40;Report Builder and SSRS&#41;</span></span>](report-design/troubleshoot-reports-map-reports-report-builder-and-ssrs.md)  
  
  
