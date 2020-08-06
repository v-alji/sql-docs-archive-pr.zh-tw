---
title: 使用彙總轉換來彙總資料集中的值 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Aggregate transformation [Integration Services]
- aggregate values [Integration Services]
- datasets [Integration Services], aggregate values
ms.assetid: 01b81c0f-d5e0-483b-81b2-73800a6945ac
author: chugugrace
ms.author: chugu
ms.openlocfilehash: de918c6c2adf194d5808ccd1b64c77a94a52e357
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687068"
---
# <a name="aggregate-values-in-a-dataset-by-using-the-aggregate-transformation"></a><span data-ttu-id="65f8f-102">使用彙總轉換來彙總資料集中的值</span><span class="sxs-lookup"><span data-stu-id="65f8f-102">Aggregate Values in a Dataset by Using the Aggregate Transformation</span></span>
  <span data-ttu-id="65f8f-103">若要加入及設定「彙總」轉換，封裝中必須已包含至少一個「資料流程」工作和一個來源。</span><span class="sxs-lookup"><span data-stu-id="65f8f-103">To add and configure an Aggregate transformation, the package must already include at least one Data Flow task and one source.</span></span>  
  
### <a name="to-aggregate-values-in-a-dataset"></a><span data-ttu-id="65f8f-104">若要彙總資料集中的值</span><span class="sxs-lookup"><span data-stu-id="65f8f-104">To aggregate values in a dataset</span></span>  
  
1.  <span data-ttu-id="65f8f-105">在 [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]中，開啟包含所需封裝的 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 專案。</span><span class="sxs-lookup"><span data-stu-id="65f8f-105">In [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="65f8f-106">在 [方案總管] 中，按兩下封裝將其開啟。</span><span class="sxs-lookup"><span data-stu-id="65f8f-106">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="65f8f-107">按一下 **[資料流程]** 索引標籤，然後從 **[工具箱]** 拖曳「彙總」轉換至設計介面。</span><span class="sxs-lookup"><span data-stu-id="65f8f-107">Click the **Data Flow** tab, and then, from the **Toolbox**, drag the Aggregate transformation to the design surface.</span></span>  
  
4.  <span data-ttu-id="65f8f-108">從來源或先前的轉換將連接子拖曳到彙總轉換，以便將彙總轉換連接到資料流程。</span><span class="sxs-lookup"><span data-stu-id="65f8f-108">Connect the Aggregate transformation to the data flow by dragging a connector from the source or the previous transformation to the Aggregate transformation.</span></span>  
  
5.  <span data-ttu-id="65f8f-109">按兩下該轉換。</span><span class="sxs-lookup"><span data-stu-id="65f8f-109">Double-click the transformation.</span></span>  
  
6.  <span data-ttu-id="65f8f-110">在 **[彙總轉換編輯器]** 對話方塊中，按一下 **[彙總]** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="65f8f-110">In the **Aggregate Transformation Editor** dialog box, click the **Aggregations** tab.</span></span>  
  
7.  <span data-ttu-id="65f8f-111">在 **[可用的輸入資料行]** 清單中，選取您要計算彙總值之資料行旁邊的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="65f8f-111">In the **Available Input Columns** list, select the check box by the columns on which you want to aggregate values.</span></span> <span data-ttu-id="65f8f-112">選取的資料行便會顯示在資料表中。</span><span class="sxs-lookup"><span data-stu-id="65f8f-112">The selected columns appear in the table.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="65f8f-113">您可以多次選取某個資料行，以套用多個轉換至該資料行。</span><span class="sxs-lookup"><span data-stu-id="65f8f-113">You can select a column multiple times, applying multiple transformations to the column.</span></span> <span data-ttu-id="65f8f-114">為了唯一識別彙總，會在資料行輸出別名的預設名稱後面附加一個數字。</span><span class="sxs-lookup"><span data-stu-id="65f8f-114">To uniquely identify aggregations, a number is appended to the default name of the output alias of the column.</span></span>  
  
8.  <span data-ttu-id="65f8f-115">(選擇性) 修改 **[輸出別名]** 資料行中的值。</span><span class="sxs-lookup"><span data-stu-id="65f8f-115">Optionally, modify the value in the **Output Alias** columns.</span></span>  
  
9. <span data-ttu-id="65f8f-116">若要變更預設彙總作業 **[群組依據]** ，請在 **[作業]** 清單中選取不同的作業。</span><span class="sxs-lookup"><span data-stu-id="65f8f-116">To change the default aggregation operation, **Group by**, select a different operation in the **Operation** list.</span></span>  
  
10. <span data-ttu-id="65f8f-117">若要變更預設比較，請選取 **[比較旗標]** 資料行中列出的個別比較旗標。</span><span class="sxs-lookup"><span data-stu-id="65f8f-117">To change the default comparison, select the individual comparison flags listed in the **Comparison Flags** column.</span></span> <span data-ttu-id="65f8f-118">依預設，比較會忽略大小寫、假名類型、不佔空間字元和字元寬度。</span><span class="sxs-lookup"><span data-stu-id="65f8f-118">By default, a comparison ignores case, kana type, non-spacing characters, and character width.</span></span>  
  
11. <span data-ttu-id="65f8f-119">(選擇性) 針對 **[計算相異]** 彙總，在 **[計算相異索引鍵]** 資料行中指定相異值的確實數目，或是在 **[計算相異小數位數]** 資料行中選取近似計數。</span><span class="sxs-lookup"><span data-stu-id="65f8f-119">Optionally, for the **Count distinct** aggregation, specify an exact number of distinct values in the **Count Distinct Keys** column, or select an approximate count in the **Count Distinct Scale** column.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="65f8f-120">提供相異值的數目 (不論是精確值或近似值) 可最佳化效能，因為轉換可以預先配置適當的記憶體容量來執行其工作。</span><span class="sxs-lookup"><span data-stu-id="65f8f-120">Providing the number of distinct values, exact or approximate, optimizes performance, because the transformation can preallocate an appropriate amount of memory to do its work.</span></span>  
  
12. <span data-ttu-id="65f8f-121">(選擇性) 按一下 **[進階]** ，並更新「彙總」轉換輸出的名稱。</span><span class="sxs-lookup"><span data-stu-id="65f8f-121">Optionally, click **Advanced** and update the name of the Aggregate transformation output.</span></span> <span data-ttu-id="65f8f-122">如果匯總包含作業 `Group By` ，您可以在 [索引**鍵小**數位數] 資料行中選取群組索引鍵值的近似計數，或是在 [索引**鍵**] 資料行中指定精確的群組索引鍵值數目。</span><span class="sxs-lookup"><span data-stu-id="65f8f-122">If the aggregations include a `Group By` operation, you can select an approximate count of grouping key values in the **Keys Scale** column or specify an exact number of grouping key values in the **Keys** column.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="65f8f-123">提供相異值的數目 (不論是精確值或近似值) 可最佳化效能，因為轉換可以預先配置適當的記憶體容量來執行其工作。</span><span class="sxs-lookup"><span data-stu-id="65f8f-123">Providing the number of distinct values, exact or approximate, optimizes performance, because the transformation can preallocate an appropriate amount of memory to do its work.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="65f8f-124">**[索引鍵小數位數]** 和 **[索引鍵]** 選項互斥。</span><span class="sxs-lookup"><span data-stu-id="65f8f-124">The **Keys Scale** and **Keys** options are mutually exclusive.</span></span> <span data-ttu-id="65f8f-125">如果您同時在兩個資料行中輸入值，將會使用 **[索引鍵小數位數]** 或 **[索引鍵]** 中較大的值。</span><span class="sxs-lookup"><span data-stu-id="65f8f-125">If you enter values in both columns, the larger value in either **Keys Scale** or **Keys** is used.</span></span>  
  
13. <span data-ttu-id="65f8f-126">(選擇性) 按一下 **[進階]** 索引標籤，並設定可以用來最佳化彙總轉換執行之所有作業的屬性。</span><span class="sxs-lookup"><span data-stu-id="65f8f-126">Optionally, click the **Advanced** tab and set the attributes that apply to optimizing all the operations that the Aggregate transformation performs.</span></span>  
  
14. <span data-ttu-id="65f8f-127">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="65f8f-127">Click **OK**.</span></span>  
  
15. <span data-ttu-id="65f8f-128">若要儲存已更新的封裝，請在 **[檔案]** 功能表上，按一下 **[儲存選取項目]** 。</span><span class="sxs-lookup"><span data-stu-id="65f8f-128">To save the updated package, click **Save Selected Items** on the **File** menu.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65f8f-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="65f8f-129">See Also</span></span>  
 <span data-ttu-id="65f8f-130">[彙總轉換](aggregate-transformation.md) </span><span class="sxs-lookup"><span data-stu-id="65f8f-130">[Aggregate Transformation](aggregate-transformation.md) </span></span>  
 <span data-ttu-id="65f8f-131">[Integration Services 轉換](integration-services-transformations.md) </span><span class="sxs-lookup"><span data-stu-id="65f8f-131">[Integration Services Transformations](integration-services-transformations.md) </span></span>  
 <span data-ttu-id="65f8f-132">[Integration Services 路徑](../integration-services-paths.md) </span><span class="sxs-lookup"><span data-stu-id="65f8f-132">[Integration Services Paths](../integration-services-paths.md) </span></span>  
 [<span data-ttu-id="65f8f-133">資料流程工作</span><span class="sxs-lookup"><span data-stu-id="65f8f-133">Data Flow Task</span></span>](../../control-flow/data-flow-task.md)  
  
  
