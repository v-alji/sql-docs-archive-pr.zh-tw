---
title: 將 HTML 新增至報表 (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 30bd631a-f774-48e7-a13a-b6c2eb54d9bb
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 605c84843d62fb664a8a665a3fc3b024f8f87186
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706214"
---
# <a name="add-html-into-a-report-report-builder-and-ssrs"></a><span data-ttu-id="fe938-102">將 HTML 加入至報表 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="fe938-102">Add HTML into a Report (Report Builder and SSRS)</span></span>
  <span data-ttu-id="fe938-103">您可以使用預留位置，從資料集的欄位匯入 HTML，以便用於報表中。</span><span class="sxs-lookup"><span data-stu-id="fe938-103">Using a placeholder, you can import HTML from a field in your dataset for use in the report.</span></span> <span data-ttu-id="fe938-104">根據預設，預留位置代表純文字，所以您必須將預留位置標記類型變更為 HTML。</span><span class="sxs-lookup"><span data-stu-id="fe938-104">By default, a placeholder represents plain text, so you will need to change the placeholder mark-up type to HTML.</span></span> <span data-ttu-id="fe938-105">如需詳細資訊，請參閱[將 HTML 匯入至報表 &#40;報表產生器及 SSRS&#41;](importing-html-into-a-report-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="fe938-105">For more information, see [Importing HTML into a Report &#40;Report Builder and SSRS&#41;](importing-html-into-a-report-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-html-from-a-field-in-your-dataset-into-a-text-box"></a><span data-ttu-id="fe938-106">若要將 HTML 從資料集的欄位加入至文字方塊</span><span class="sxs-lookup"><span data-stu-id="fe938-106">To add HTML from a field in your dataset into a text box</span></span>  
  
1.  <span data-ttu-id="fe938-107">在 **[插入]** 索引標籤上，按一下 **[清單]** 。</span><span class="sxs-lookup"><span data-stu-id="fe938-107">On the **Insert** tab, click **List**.</span></span> <span data-ttu-id="fe938-108">按一下設計介面，然後拖曳滑鼠來建立一個所需大小的方塊。</span><span class="sxs-lookup"><span data-stu-id="fe938-108">Click the design surface, and then drag to create a box that is the size you want.</span></span>  
  
     <span data-ttu-id="fe938-109">**[資料集屬性]** 對話方塊隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="fe938-109">The **Dataset Properties** dialog box opens.</span></span> <span data-ttu-id="fe938-110">您可以使用共用資料集或在報表中內嵌資料集。</span><span class="sxs-lookup"><span data-stu-id="fe938-110">You can use a shared dataset or a dataset embedded in your report.</span></span> <span data-ttu-id="fe938-111">如需詳細資訊，請按一下[資料集屬性對話方塊、查詢 &#40;報表產生器&#41;](../report-data/dataset-properties-dialog-box-query-report-builder.md) 或[資料集屬性對話方塊、查詢](../dataset-properties-dialog-box-query.md)。</span><span class="sxs-lookup"><span data-stu-id="fe938-111">For more information, click [Dataset Properties Dialog Box, Query &#40;Report Builder&#41;](../report-data/dataset-properties-dialog-box-query-report-builder.md) or [Dataset Properties Dialog Box, Query](../dataset-properties-dialog-box-query.md).</span></span>  
  
2.  <span data-ttu-id="fe938-112">在 **[插入]** 索引標籤上，按一下 **[文字方塊]** 。</span><span class="sxs-lookup"><span data-stu-id="fe938-112">On the **Insert** tab, click **Text Box**.</span></span> <span data-ttu-id="fe938-113">在清單中按一下，然後拖曳滑鼠來建立一個所需大小的方塊。</span><span class="sxs-lookup"><span data-stu-id="fe938-113">Click in the list, and then drag to create a box that is the size you want.</span></span>  
  
3.  <span data-ttu-id="fe938-114">將 HTML 欄位從資料集拖曳至文字方塊中。</span><span class="sxs-lookup"><span data-stu-id="fe938-114">Drag an HTML field from your dataset into the text box.</span></span> <span data-ttu-id="fe938-115">如此就會針對您的欄位建立預留位置。</span><span class="sxs-lookup"><span data-stu-id="fe938-115">A placeholder is created for your field.</span></span>  
  
4.  <span data-ttu-id="fe938-116">以滑鼠右鍵按一下預留位置，然後按一下 [預留位置屬性]  。</span><span class="sxs-lookup"><span data-stu-id="fe938-116">Right-click the placeholder, and then click **Placeholder Properties**.</span></span>  
  
5.  <span data-ttu-id="fe938-117">在 **[一般]** 索引標籤上，確認 **[值]** 方塊包含評估成您在步驟 3 中放置之欄位的運算式。</span><span class="sxs-lookup"><span data-stu-id="fe938-117">On the **General** tab, verify that the **Value** box contains an expression that evaluates to the field you dropped in step 3.</span></span>  
  
6.  <span data-ttu-id="fe938-118">按一下 [HTML - 將 HTML 標記解譯為樣式]  。</span><span class="sxs-lookup"><span data-stu-id="fe938-118">Click **HTML - Interpret HTML tags as styles**.</span></span> <span data-ttu-id="fe938-119">這樣就會讓欄位評估成 HTML。</span><span class="sxs-lookup"><span data-stu-id="fe938-119">This causes the field to be evaluated as HTML.</span></span>  
  
7.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="fe938-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fe938-120">See Also</span></span>  
 <span data-ttu-id="fe938-121">[格式化數字和日期 &#40;報表產生器及 SSRS&#41;](formatting-numbers-and-dates-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="fe938-121">[Formatting Numbers and Dates &#40;Report Builder and SSRS&#41;](formatting-numbers-and-dates-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="fe938-122">[格式化線條、色彩和影像 &#40;報表產生器及 SSRS&#41;](images-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="fe938-122">[Formatting Lines, Colors, and Images &#40;Report Builder and SSRS&#41;](images-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="fe938-123">預留位置屬性對話方塊、一般 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="fe938-123">Placeholder Properties Dialog Box, General &#40;Report Builder and SSRS&#41;</span></span>](../placeholder-properties-dialog-box-general-report-builder-and-ssrs.md)  
  
  
