---
title: 步驟 8：使第 1 課的封裝更容易了解 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: e3751e53-77c7-47d0-8fe8-73ed1a53413a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 67fb8e2adb9062b5b777acc14df0ddc5b45884ee
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596126"
---
# <a name="step-8-making-the-lesson-1-package-easier-to-understand"></a><span data-ttu-id="f5d99-102">步驟 8：使第 1 課的封裝更容易了解</span><span class="sxs-lookup"><span data-stu-id="f5d99-102">Step 8: Making the Lesson 1 Package Easier to Understand</span></span>
  <span data-ttu-id="f5d99-103">現在您已完成第 1 課封裝的組態，不妨整理一下封裝配置。</span><span class="sxs-lookup"><span data-stu-id="f5d99-103">Now that you have completed the configuration of the Lesson 1 package, it is a good idea to tidy up the package layout.</span></span> <span data-ttu-id="f5d99-104">如果控制流程配置和資料流程配置中的形狀是隨機大小，或形狀沒有對齊或分組，則封裝功能可能更難以了解。</span><span class="sxs-lookup"><span data-stu-id="f5d99-104">If the shapes in the control and data flow layouts are random sizes, or if the shapes are not aligned or grouped, the functionality of package can be more difficult to understand.</span></span>  
  
 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] <span data-ttu-id="f5d99-105">Data Tools 會提供方便而快速格式化封裝配置的工具。</span><span class="sxs-lookup"><span data-stu-id="f5d99-105">Data Tools provides tools that make it easy and quick to format the package layout.</span></span> <span data-ttu-id="f5d99-106">格式化功能包括使形狀變成相同大小、對齊形狀和操控形狀之間水平和垂直距離的能力。</span><span class="sxs-lookup"><span data-stu-id="f5d99-106">The formatting features include the ability to make shapes the same size, align shapes, and manipulate the horizontal and vertical spacing between shapes.</span></span>  
  
 <span data-ttu-id="f5d99-107">進一步了解封裝的另一個方法是加入描述封裝功能的註解。</span><span class="sxs-lookup"><span data-stu-id="f5d99-107">Another way to improve the understanding of package functionality is to add annotations that describe package functionality.</span></span>  
  
 <span data-ttu-id="f5d99-108">在這項工作中，您將使用 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Data Tools 中的格式化功能來加強資料流程的配置，以及將註解加入資料流程中。</span><span class="sxs-lookup"><span data-stu-id="f5d99-108">In this task, you will use the formatting features in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Data Tools to improve the layout of the data flow and also add an annotation to the data flow.</span></span>  
  
### <a name="to-format-the-layout-of-the-data-flow"></a><span data-ttu-id="f5d99-109">若要格式化資料流程的配置</span><span class="sxs-lookup"><span data-stu-id="f5d99-109">To format the layout of the data flow</span></span>  
  
1.  <span data-ttu-id="f5d99-110">如果第 1 課封裝尚未開啟，按兩下 [方案總管] 中的 Lesson 1.dtsx。</span><span class="sxs-lookup"><span data-stu-id="f5d99-110">If the Lesson 1 package is not already open, double-click Lesson 1.dtsx in Solution Explorer.</span></span>  
  
2.  <span data-ttu-id="f5d99-111">按一下 **[資料流程]** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="f5d99-111">Click the **Data Flow** tab.</span></span>  
  
3.  <span data-ttu-id="f5d99-112">將資料指標放到 [擷取範例貨幣] 轉換的上面和右邊、按一下滑鼠按鍵，然後在所有資料流程元件上拖曳資料指標。</span><span class="sxs-lookup"><span data-stu-id="f5d99-112">Place the cursor to the top and to the right of the Extract Sample Currency transformation, click, and then drag the cursor across all the data flow components.</span></span>  
  
4.  <span data-ttu-id="f5d99-113">在 **[格式]** 功能表上，指向 **[設定成相同大小]**，再按一下 **[兩者]**。</span><span class="sxs-lookup"><span data-stu-id="f5d99-113">On the **Format** menu, point to **Make Same Size**, and then click **Both**.</span></span>  
  
5.  <span data-ttu-id="f5d99-114">選取資料流程物件之後，在 **[格式]** 功能表上，指向 **[對齊]**，然後按一下 **[靠左]**。</span><span class="sxs-lookup"><span data-stu-id="f5d99-114">With the data flow objects selected, on the **Format** menu, point to **Align**, and then click **Lefts**.</span></span>  
  
### <a name="to-add-an-annotation-to-the-data-flow"></a><span data-ttu-id="f5d99-115">若要將註解加入資料流程中</span><span class="sxs-lookup"><span data-stu-id="f5d99-115">To add an annotation to the data flow</span></span>  
  
1.  <span data-ttu-id="f5d99-116">以滑鼠右鍵按一下資料流程設計介面背景中的任何位置，然後按一下 **[加入註解]**。</span><span class="sxs-lookup"><span data-stu-id="f5d99-116">Right-click anywhere in the background of the data flow design surface and then click **Add Annotation**.</span></span>  
  
2.  <span data-ttu-id="f5d99-117">在註解方塊中輸入或貼上下列文字。</span><span class="sxs-lookup"><span data-stu-id="f5d99-117">Type or paste the following text in the annotation box.</span></span>  
  
     <span data-ttu-id="f5d99-118">**資料流程會從檔案中擷取資料，在 DimCurrency 資料表的 CurrencyKey 資料行和 DimDate 資料表的 DateKey 資料行中查閱值，然後將資料寫入至 NewFactCurrencyRate 資料表中。**</span><span class="sxs-lookup"><span data-stu-id="f5d99-118">**The data flow extracts data from a file, looks up values in the CurrencyKey column in the DimCurrency table and the DateKey column in the DimDate table, and writes the data to the NewFactCurrencyRate table.**</span></span>  
  
     <span data-ttu-id="f5d99-119">若要使註解方塊中的文字換行，請將游標放在您要開始新行的位置，然後按 Enter 鍵。</span><span class="sxs-lookup"><span data-stu-id="f5d99-119">To wrap the text in the annotation box, place the cursor where you want to start a new line and press the Enter key.</span></span>  
  
     <span data-ttu-id="f5d99-120">如果您沒有將文字加入註解方塊中，則您在方塊之外按一下時，它就會消失不見。</span><span class="sxs-lookup"><span data-stu-id="f5d99-120">If you do not add text to the annotation box, it disappears when you click outside the box.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="f5d99-121">後續步驟</span><span class="sxs-lookup"><span data-stu-id="f5d99-121">Next Steps</span></span>  
 [<span data-ttu-id="f5d99-122">步驟 9：測試第 1 課的教學課程封裝</span><span class="sxs-lookup"><span data-stu-id="f5d99-122">Step 9: Testing the Lesson 1 Tutorial Package</span></span>](../integration-services/lesson-1-9-testing-the-lesson-1-tutorial-package.md)  
  
  
