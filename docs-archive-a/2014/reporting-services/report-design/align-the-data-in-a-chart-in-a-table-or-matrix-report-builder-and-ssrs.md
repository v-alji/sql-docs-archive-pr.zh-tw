---
title: 在資料表或矩陣的圖表上對齊資料 (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 75137575-d1bf-46d6-8527-5afc85eea5e1
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 3e4278cd9f0dd5526770b43d2c6d94a8b87158cc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599383"
---
# <a name="align-the-data-in-a-chart-in-a-table-or-matrix-report-builder-and-ssrs"></a><span data-ttu-id="c0b6e-102">在資料表或矩陣的圖表上對齊資料 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="c0b6e-102">Align the Data in a Chart in a Table or Matrix (Report Builder and SSRS)</span></span>
  <span data-ttu-id="c0b6e-103">走勢圖和資料橫條很小，也就是以少量的外來細節傳達許多資訊的簡易圖表。</span><span class="sxs-lookup"><span data-stu-id="c0b6e-103">Sparklines and data bars are small, simple charts that convey a lot of information with little extraneous detail.</span></span> <span data-ttu-id="c0b6e-104">當您核取這個選項時，走勢圖和資料橫條中的值將會跨資料表或矩陣中的不同資料格對齊，即使它們在其依據的資料中有遺漏值也是一樣。</span><span class="sxs-lookup"><span data-stu-id="c0b6e-104">When you check this option, the values in your sparklines and data bars will align across the different cells in the table or matrix, even if there are missing values in the data they are based on.</span></span>  
  
 <span data-ttu-id="c0b6e-105">![rs_SparklineAlignData](../media/rs-sparklinealigndata.gif "rs_SparklineAlignData")</span><span class="sxs-lookup"><span data-stu-id="c0b6e-105">![rs_SparklineAlignData](../media/rs-sparklinealigndata.gif "rs_SparklineAlignData")</span></span>  
  
 <span data-ttu-id="c0b6e-106">在這個影像中，直條圖會顯示每一個員工的每天銷售量。</span><span class="sxs-lookup"><span data-stu-id="c0b6e-106">In this image, the column chart shows daily sales for each employee.</span></span> <span data-ttu-id="c0b6e-107">請注意，如果是員工沒有任何銷售量的日子，圖表就會留下空白，並將後續的日子水平對齊。</span><span class="sxs-lookup"><span data-stu-id="c0b6e-107">Note that for days that an employee has no sales, the chart leaves a blank and aligns subsequent days horizontally.</span></span> <span data-ttu-id="c0b6e-108">它也會使不同圖表的大小彼此相對，以垂直對齊圖表。</span><span class="sxs-lookup"><span data-stu-id="c0b6e-108">It also aligns the charts vertically by making the sizes of the different charts relative to each other.</span></span> <span data-ttu-id="c0b6e-109">如需詳細資訊，請參閱 [走勢圖和資料橫條 &#40;報表產生器及 SSRS&#41;](sparklines-and-data-bars-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="c0b6e-109">For more information, see [Sparklines and Data Bars &#40;Report Builder and SSRS&#41;](sparklines-and-data-bars-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="align-the-data-in-a-sparkline-or-data-bar"></a><span data-ttu-id="c0b6e-110">對齊走勢圖或資料橫條中的資料</span><span class="sxs-lookup"><span data-stu-id="c0b6e-110">Align the data in a sparkline or data bar</span></span>  
  
1.  <span data-ttu-id="c0b6e-111">在走勢圖或資料橫條中按一下，然後按一下 **[水平軸屬性]** 或 **[垂直軸屬性]**。</span><span class="sxs-lookup"><span data-stu-id="c0b6e-111">Click in the sparkline or data bar, and then click **Horizontal Axis Properties** or **Vertical Axis Properties**.</span></span>  
  
2.  <span data-ttu-id="c0b6e-112">在 **[軸選項]** 索引標籤上，核取 **[對齊軸]** 方塊，然後在下拉方塊中，選取要對齊軸的群組。</span><span class="sxs-lookup"><span data-stu-id="c0b6e-112">On the **Axis Options** tab, check the **Align axes in** box, and then in the dropdown box, select the group on which to align the axis.</span></span>  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="c0b6e-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c0b6e-113">See Also</span></span>  
 <span data-ttu-id="c0b6e-114">[圖表 &#40;報表產生器和 SSRS&#41;](charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="c0b6e-114">[Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="c0b6e-115">加入走勢圖和資料橫條 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="c0b6e-115">Add Sparklines and Data Bars &#40;Report Builder and SSRS&#41;</span></span>](add-sparklines-and-data-bars-report-builder-and-ssrs.md)  
  
  
