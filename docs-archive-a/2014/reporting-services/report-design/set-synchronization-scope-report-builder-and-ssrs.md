---
title: 設定同步處理範圍 （報表產生器及 SSRS） |Microsoft 文件
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 6f4a11e6-6151-47be-a43f-e3dbf6c0e737
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 3efbb7774d5116c9b3a18457291434f2a05aac7f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585030"
---
# <a name="set-synchronization-scope-report-builder-and-ssrs"></a><span data-ttu-id="6deda-102">設定同步處理範圍 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="6deda-102">Set Synchronization Scope (Report Builder and SSRS)</span></span>
  <span data-ttu-id="6deda-103">指標會在指定的範圍內，跨指標值的範圍進行同步處理，藉以傳達資料值。</span><span class="sxs-lookup"><span data-stu-id="6deda-103">Indicators convey data values by synchronizing across the range of indicator values within a specified scope.</span></span> <span data-ttu-id="6deda-104">根據預設，此範圍是指標的父容器，例如，包含指標的資料表或矩陣。</span><span class="sxs-lookup"><span data-stu-id="6deda-104">By default, the scope is the parent container of the indicator such as the table or matrix that contains the indicator.</span></span> <span data-ttu-id="6deda-105">您可以根據報表的版面配置來變更指標的同步處理。</span><span class="sxs-lookup"><span data-stu-id="6deda-105">You can change the synchronization of the indicator depending on the layout of your report.</span></span> <span data-ttu-id="6deda-106">例如，如果某個資料表之類的資料區有資料列群組，您可以將群組指定為指標範圍。</span><span class="sxs-lookup"><span data-stu-id="6deda-106">For example, if a data region such as a table has a row group, you can specify the group as the indicator scope.</span></span> <span data-ttu-id="6deda-107">指標也可以省略同步處理。</span><span class="sxs-lookup"><span data-stu-id="6deda-107">The indicator can also omit synchronization.</span></span>  
  
 <span data-ttu-id="6deda-108">您可以使用運算式來設定選項，如度量單位。</span><span class="sxs-lookup"><span data-stu-id="6deda-108">Options such as measurement units can be set by using expressions.</span></span> <span data-ttu-id="6deda-109">如需詳細資訊，請參閱[運算式 &#40;報表產生器及 SSRS&#41;](expressions-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="6deda-109">For more information, see [Expressions &#40;Report Builder and SSRS&#41;](expressions-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="6deda-110">如需了解和設定報表內範圍的一般資訊，請參閱[總計、彙總與內建集合的運算式範圍 &#40;報表產生器及 SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md)。</span><span class="sxs-lookup"><span data-stu-id="6deda-110">For general information about understanding and setting scope within reports, see [Expression Scope for Totals, Aggregates, and Built-in Collections &#40;Report Builder and SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-change-the-synchronization-scope-of-an-indicator"></a><span data-ttu-id="6deda-111">若要變更指標的同步處理範圍</span><span class="sxs-lookup"><span data-stu-id="6deda-111">To change the synchronization scope of an indicator</span></span>  
  
1.  <span data-ttu-id="6deda-112">以滑鼠右鍵按一下您要變更的指標，然後按一下 **[指標屬性]**。</span><span class="sxs-lookup"><span data-stu-id="6deda-112">Right click the indicator you want to change and click **Indicator Properties**.</span></span>  
  
2.  <span data-ttu-id="6deda-113">按一下左窗格中的 **[值和狀態]** 。</span><span class="sxs-lookup"><span data-stu-id="6deda-113">Click **Values and States** in the left pane.</span></span>  
  
3.  <span data-ttu-id="6deda-114">在 **[同步處理範圍]** 清單中，按一下您要套用的範圍。</span><span class="sxs-lookup"><span data-stu-id="6deda-114">In the **Synchronization scope** list, click the scope that you want to apply.</span></span>  
  
     <span data-ttu-id="6deda-115">[(無)]  選項 (會從指標移除同步處理範圍) 永遠可以使用。</span><span class="sxs-lookup"><span data-stu-id="6deda-115">The **(None)** option, which removes synchronization scope from the indicator, is always available.</span></span> <span data-ttu-id="6deda-116">其他選項則取決於您報表的版面配置。</span><span class="sxs-lookup"><span data-stu-id="6deda-116">Other options depend on the layout of your report.</span></span>  
  
     <span data-ttu-id="6deda-117">或者，按一下 [運算式]  \(*fx*) 按鈕來編輯設定範圍的運算式。</span><span class="sxs-lookup"><span data-stu-id="6deda-117">Optionally, click the **Expression** (*fx*) button to edit an expression that sets the scope.</span></span>  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="6deda-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6deda-118">See Also</span></span>  
 [<span data-ttu-id="6deda-119">指標 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="6deda-119">Indicators &#40;Report Builder and SSRS&#41;</span></span>](indicators-report-builder-and-ssrs.md)  
  
  
