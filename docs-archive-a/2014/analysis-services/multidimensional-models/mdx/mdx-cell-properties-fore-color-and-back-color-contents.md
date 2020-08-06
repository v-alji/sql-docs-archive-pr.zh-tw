---
title: FORE_COLOR 和 BACK_COLOR 內容 (MDX) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- FORE_COLOR contents
- backgrounds [MDX]
- cells [MDX]
- colors [MDX]
- storing cell color information
- cell backgrounds
- BACK_COLOR contents
ms.assetid: ff8f40cb-2ac4-4fc2-9761-7f1b14c17c8c
author: minewiskan
ms.author: owend
ms.openlocfilehash: 748754ec3c90bb44392d7acb7de8f815be24086e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705605"
---
# <a name="fore_color-and-back_color-contents-mdx"></a><span data-ttu-id="46083-102">FORE_COLOR 及 BACK_COLOR 內容 (MDX)</span><span class="sxs-lookup"><span data-stu-id="46083-102">FORE_COLOR and BACK_COLOR Contents (MDX)</span></span>
  <span data-ttu-id="46083-103">`FORE_COLOR` 及 `BACK_COLOR` 資料格屬性是分別用來以 Microsoft Windows 作業系統的紅-綠-藍 (RGB) 格式，儲存某一資料格的文字與背景的色彩資訊。</span><span class="sxs-lookup"><span data-stu-id="46083-103">The `FORE_COLOR` and `BACK_COLOR` cell properties store color information for the text and the background of a cell, respectively, in the Microsoft Windows operating system red-green-blue (RGB) format.</span></span>  
  
 <span data-ttu-id="46083-104">一般 RGB 色彩的有效範圍介於零 (0) 到 16,777,215 (&H00FFFFFF)。</span><span class="sxs-lookup"><span data-stu-id="46083-104">The valid range for an ordinary RGB color is zero (0) to 16,777,215 (&H00FFFFFF).</span></span> <span data-ttu-id="46083-105">在這個範圍內的數字其高位元永遠等於 0；三個低位元，由最低位元到最高位元，分別決定了紅、綠和藍三種色彩。</span><span class="sxs-lookup"><span data-stu-id="46083-105">The high byte of a number in this range always equals 0; the lower 3 bytes, from least to most significant byte, determine the amount of red, green, and blue, respectively.</span></span> <span data-ttu-id="46083-106">紅、綠和藍三種元素分別由 0 到 255 (&HFF) 之間的數字表示。</span><span class="sxs-lookup"><span data-stu-id="46083-106">The red, green, and blue components are each represented by a number between 0 and 255 (&HFF).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46083-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="46083-107">See Also</span></span>  
 [<span data-ttu-id="46083-108">使用資料格屬性 &#40;MDX&#41;</span><span class="sxs-lookup"><span data-stu-id="46083-108">Using Cell Properties &#40;MDX&#41;</span></span>](mdx-cell-properties-using-cell-properties.md)  
  
  
