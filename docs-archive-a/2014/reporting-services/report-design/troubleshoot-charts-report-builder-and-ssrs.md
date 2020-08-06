---
title: 疑難排解圖表 (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 3a327ffa-3b69-40d6-8015-cc01cfae9161
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b931b50545ba2b8d7c4c06cc5c48d6415a05470a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87702438"
---
# <a name="troubleshoot-charts-report-builder-and-ssrs"></a><span data-ttu-id="c46b8-102">疑難排解圖表 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="c46b8-102">Troubleshoot Charts (Report Builder and SSRS)</span></span>
  <span data-ttu-id="c46b8-103">使用圖表時，這些問題很有協助。</span><span class="sxs-lookup"><span data-stu-id="c46b8-103">These issues can be helpful when working with charts.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="why-does-my-chart-count-not-sum-the-values-on-the-value-axis"></a><span data-ttu-id="c46b8-104">為什麼我的圖表計數不會針對值軸上的值加總？</span><span class="sxs-lookup"><span data-stu-id="c46b8-104">Why does my chart count, not sum, the values on the value axis?</span></span>  
 <span data-ttu-id="c46b8-105">大多數的圖表類型都需要沿著值軸 (通常為 Y 軸) 放置數值，才能正確繪製。</span><span class="sxs-lookup"><span data-stu-id="c46b8-105">Most chart types require numeric values along the value axis, which is typically the y-axis, in order to draw correctly.</span></span> <span data-ttu-id="c46b8-106">如果值欄位的資料類型為 `String`，即使欄位中有數字，圖表也無法顯示數值。</span><span class="sxs-lookup"><span data-stu-id="c46b8-106">If the data type of your value field is `String`, the chart cannot display a numeric value, even if there are numerals in the fields.</span></span> <span data-ttu-id="c46b8-107">但是，圖表會顯示在該欄位中包含值之資料列總數的計數。</span><span class="sxs-lookup"><span data-stu-id="c46b8-107">Instead, the chart displays a count of the total number of rows that contain a value in that field.</span></span> <span data-ttu-id="c46b8-108">若要避免發生這個問題，請確定您用於值數列的欄位具有數值資料類型，而不是包含格式化數字的字串。</span><span class="sxs-lookup"><span data-stu-id="c46b8-108">To avoid this behavior, make sure that the fields that you use for value series have numeric data types, as opposed to strings that contain formatted numbers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c46b8-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c46b8-109">See Also</span></span>  
 [<span data-ttu-id="c46b8-110">圖表 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="c46b8-110">Charts &#40;Report Builder and SSRS&#41;</span></span>](charts-report-builder-and-ssrs.md)  
  
  
