---
title: 將量測計新增至報表 (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 45da4fef-2b02-40e1-977c-f8f80d87155e
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 7125080d95e9c7b882df8d715cce5c6cf8aa6344
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706246"
---
# <a name="add-a-gauge-to-a-report-report-builder-and-ssrs"></a><span data-ttu-id="34cf4-102">將量測計加入至報表 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="34cf4-102">Add a Gauge to a Report (Report Builder and SSRS)</span></span>
  <span data-ttu-id="34cf4-103">當您想要以視覺格式摘要列出資料時，可以使用量測計資料區域。</span><span class="sxs-lookup"><span data-stu-id="34cf4-103">When you want to summarize data in a visual format, you can use a Gauge data region.</span></span> <span data-ttu-id="34cf4-104">當您將量測計資料區加入至設計介面之後，就可以將報表資料集欄位拖曳到量測計的資料窗格。</span><span class="sxs-lookup"><span data-stu-id="34cf4-104">After you add a Gauge data region to the design surface, you can drag report dataset fields to a data pane on the gauge.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-a-gauge-to-your-report"></a><span data-ttu-id="34cf4-105">若要將量測計加入至報表</span><span class="sxs-lookup"><span data-stu-id="34cf4-105">To add a gauge to your report</span></span>  
  
1.  <span data-ttu-id="34cf4-106">建立報表或開啟現有的報表。</span><span class="sxs-lookup"><span data-stu-id="34cf4-106">Create a report or open an existing report.</span></span>  
  
2.  <span data-ttu-id="34cf4-107">在 [插入] 索引標籤上，按兩下 [量測計]。</span><span class="sxs-lookup"><span data-stu-id="34cf4-107">On the Insert tab, double-click Gauge.</span></span> <span data-ttu-id="34cf4-108">**[選取量測計類型]** 對話方塊隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="34cf4-108">The **Select Gauge Type** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="34cf4-109">選取您想要加入的量測計類型。</span><span class="sxs-lookup"><span data-stu-id="34cf4-109">Select the type of gauge you want to add.</span></span> [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
    > [!NOTE]  
    >  <span data-ttu-id="34cf4-110">與圖表不同的是，量測計只有兩種類型：線性和星形。</span><span class="sxs-lookup"><span data-stu-id="34cf4-110">Unlike Chart, Gauge has only two types: linear and radial.</span></span> <span data-ttu-id="34cf4-111">**[選取量測計類型]** 對話方塊中的可用量測計是這兩種量測計類型的範本。</span><span class="sxs-lookup"><span data-stu-id="34cf4-111">The available gauges in the **Select a Gauge Type** dialog box are templates for these two types of gauges.</span></span> <span data-ttu-id="34cf4-112">因此，當您將量測計加入至報表之後，就無法變更量測計類型。</span><span class="sxs-lookup"><span data-stu-id="34cf4-112">For this reason, you cannot change the gauge type after you add the gauge to your report.</span></span> <span data-ttu-id="34cf4-113">您必須刪除並重新加入量測計，才能變更其類型。</span><span class="sxs-lookup"><span data-stu-id="34cf4-113">You must delete and re-add a gauge to change its type.</span></span>  
  
     <span data-ttu-id="34cf4-114">如果報表沒有任何資料來源和資料集， **[資料來源屬性]** 對話方塊就會開啟並引導您完成建立這兩者的步驟。</span><span class="sxs-lookup"><span data-stu-id="34cf4-114">If the report has no data source and dataset the **Data Source Properties** dialog box opens and takes you through the steps to create both.</span></span> <span data-ttu-id="34cf4-115">如需詳細資訊，請參閱 [加入和驗證資料連線或資料來源 &#40;Report Builder 和 SSRS&#41;](../report-data/add-and-verify-a-data-connection-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="34cf4-115">For more information see, [Add and Verify a Data Connection or Data Source &#40;Report Builder and SSRS&#41;](../report-data/add-and-verify-a-data-connection-report-builder-and-ssrs.md).</span></span>  
  
     <span data-ttu-id="34cf4-116">如果報表具有資料來源，但是沒有任何資料集， **[資料集屬性]** 對話方塊就會開啟並引導您完成建立資料集的步驟。</span><span class="sxs-lookup"><span data-stu-id="34cf4-116">If the report has a data source, but no dataset the **Dataset Properties** dialog box opens and takes you through the steps to create one.</span></span> <span data-ttu-id="34cf4-117">如需詳細資訊，請參閱 [建立共用資料集或內嵌資料集 &#40;報表產生器及 SSRS&#41;](../report-data/create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="34cf4-117">For more information, see [Create a Shared Dataset or Embedded Dataset &#40;Report Builder and SSRS&#41;](../report-data/create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md).</span></span>  
  
4.  <span data-ttu-id="34cf4-118">按一下量測計，即可顯示資料窗格。</span><span class="sxs-lookup"><span data-stu-id="34cf4-118">Click the gauge to display the data pane.</span></span> <span data-ttu-id="34cf4-119">根據預設，量測計具有對應至某個值的單一指標。</span><span class="sxs-lookup"><span data-stu-id="34cf4-119">By default, a gauge has one pointer corresponding to one value.</span></span> <span data-ttu-id="34cf4-120">您還可以加入其他指標。</span><span class="sxs-lookup"><span data-stu-id="34cf4-120">You can add additional pointers.</span></span>  
  
5.  <span data-ttu-id="34cf4-121">將一個欄位從資料集加入至資料欄位放置區。</span><span class="sxs-lookup"><span data-stu-id="34cf4-121">Add one field from the dataset to the data field drop-zone.</span></span> <span data-ttu-id="34cf4-122">您只能加入一個欄位。</span><span class="sxs-lookup"><span data-stu-id="34cf4-122">You can add only one field.</span></span> <span data-ttu-id="34cf4-123">如果您想要顯示多個欄位，您必須加入其他指標 (每一個欄位一個指標)。</span><span class="sxs-lookup"><span data-stu-id="34cf4-123">If you want to display multiple fields, you must add additional pointers, one for each field.</span></span>  
  
     <span data-ttu-id="34cf4-124">以滑鼠右鍵按一下量測計標尺，然後選取 [標尺屬性]。</span><span class="sxs-lookup"><span data-stu-id="34cf4-124">Right-click the gauge scale, and select **Scale Properties**.</span></span> <span data-ttu-id="34cf4-125">針對標尺的 **[最小值]** 和 **[最大值]** 輸入值。</span><span class="sxs-lookup"><span data-stu-id="34cf4-125">Type a value for the **Minimum** and **Maximum** of the scale.</span></span> <span data-ttu-id="34cf4-126">如需詳細資訊，請參閱[設定量測計的最小值或最大值 &#40;報表產生器和 SSRS&#41;](set-a-minimum-or-maximum-on-a-gauge-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="34cf4-126">For more information, see [Set a Minimum or Maximum on a Gauge &#40;Report Builder and SSRS&#41;](set-a-minimum-or-maximum-on-a-gauge-report-builder-and-ssrs.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34cf4-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="34cf4-127">See Also</span></span>  
 <span data-ttu-id="34cf4-128">[巢狀資料區 &#40;報表產生器及 SSRS&#41;](nested-data-regions-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="34cf4-128">[Nested Data Regions &#40;Report Builder and SSRS&#41;](nested-data-regions-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="34cf4-129">量測計 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="34cf4-129">Gauges &#40;Report Builder and SSRS&#41;</span></span>](gauges-report-builder-and-ssrs.md)  
  
  
