---
title: 地圖區屬性對話方塊、優化 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptdesigner.mapviewport.optimization.f1
- "10522"
ms.assetid: 8c0310ba-eedd-4c9f-95bd-1f9e2a1a8ed3
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 1adbeccdedb8d80900047790d94ff35568460ff4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708910"
---
# <a name="map-viewport-properties-dialog-box-optimization"></a><span data-ttu-id="5a50c-102">地圖檢視區屬性對話方塊、最佳化</span><span class="sxs-lookup"><span data-stu-id="5a50c-102">Map Viewport Properties Dialog Box, Optimization</span></span>
  <span data-ttu-id="5a50c-103">選取 **[地圖檢視區屬性]** 對話方塊的 **[最佳化]** 協助控制在報表中檢視地圖的解析度。</span><span class="sxs-lookup"><span data-stu-id="5a50c-103">Select **Optimization** for the **Map Viewport Properties** dialog box to help control the resolution for viewing a map in a report.</span></span>  
  
 <span data-ttu-id="5a50c-104">當空間資料內嵌在報表中時，解析度越高，表示儲存在報表中的資料越多。</span><span class="sxs-lookup"><span data-stu-id="5a50c-104">When spatial data is embedded in the report, higher resolution means more data is stored in the report.</span></span> <span data-ttu-id="5a50c-105">當空間資料沒有內嵌在報表中時，解析度越高，表示報表處理器建立地圖細節所花的時間越多。</span><span class="sxs-lookup"><span data-stu-id="5a50c-105">When spatial data is not embedded in the report, higher resolution means that the report processor spends more time creating the map details.</span></span> <span data-ttu-id="5a50c-106">解析度越低，則表示等待報表轉譯的時間越少。</span><span class="sxs-lookup"><span data-stu-id="5a50c-106">Lower resolution means less time waiting for the report to render.</span></span>  
  
 <span data-ttu-id="5a50c-107">按一下 **[運算式]** (*fx*) 按鈕來編輯設定選項值的運算式。</span><span class="sxs-lookup"><span data-stu-id="5a50c-107">Click the **Expression** (*fx*) button to edit an expression that sets the value of the option.</span></span>  
  
## <a name="options"></a><span data-ttu-id="5a50c-108">選項</span><span class="sxs-lookup"><span data-stu-id="5a50c-108">Options</span></span>  
 <span data-ttu-id="5a50c-109">**效能**</span><span class="sxs-lookup"><span data-stu-id="5a50c-109">**Performance**</span></span>  
 <span data-ttu-id="5a50c-110">將指標朝 **[效能]** 滑近一點來簡化地圖並顯示較少的細節。</span><span class="sxs-lookup"><span data-stu-id="5a50c-110">Slide the pointer closer to **Performance** to simplify the map and display less detail.</span></span>  
  
 <span data-ttu-id="5a50c-111">**品質**</span><span class="sxs-lookup"><span data-stu-id="5a50c-111">**Quality**</span></span>  
 <span data-ttu-id="5a50c-112">將指標朝 **[品質]** 滑近一點，以便更詳細地繪製地圖。</span><span class="sxs-lookup"><span data-stu-id="5a50c-112">Slide the pointer closer to **Quality** to draw the map with greater detail.</span></span>  
  
 <span data-ttu-id="5a50c-113">**地圖解析度**</span><span class="sxs-lookup"><span data-stu-id="5a50c-113">**Map resolution**</span></span>  
 <span data-ttu-id="5a50c-114">指定地圖解析度。</span><span class="sxs-lookup"><span data-stu-id="5a50c-114">Specify a map resolution.</span></span> <span data-ttu-id="5a50c-115">此值會指定您要在已轉譯之地圖中查看的最小細節 (以點為單位)。</span><span class="sxs-lookup"><span data-stu-id="5a50c-115">This value specifies the smallest detail that you want to see in the rendered map in points.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a50c-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5a50c-116">See Also</span></span>  
 <span data-ttu-id="5a50c-117">[地圖 &#40;報表產生器及 SSRS&#41;](report-design/maps-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="5a50c-117">[Maps &#40;Report Builder and SSRS&#41;](report-design/maps-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="5a50c-118">報表疑難排解：地圖報表 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="5a50c-118">Troubleshoot Reports: Map Reports &#40;Report Builder and SSRS&#41;</span></span>](report-design/troubleshoot-reports-map-reports-report-builder-and-ssrs.md)  
  
  
