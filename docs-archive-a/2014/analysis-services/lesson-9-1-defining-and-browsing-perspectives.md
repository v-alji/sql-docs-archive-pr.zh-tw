---
title: 定義和流覽透視圖 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 766004b9-6578-4914-a445-6f44843a5fb0
author: minewiskan
ms.author: owend
ms.openlocfilehash: c9658098180618c2d5d6d6d9e00e7a7e4a6c4231
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703381"
---
# <a name="defining-and-browsing-perspectives"></a><span data-ttu-id="d6cd5-102">定義和瀏覽檢視方塊</span><span class="sxs-lookup"><span data-stu-id="d6cd5-102">Defining and Browsing Perspectives</span></span>
  <span data-ttu-id="d6cd5-103">檢視方塊可以針對特定的用途，簡化 Cube 的檢視。</span><span class="sxs-lookup"><span data-stu-id="d6cd5-103">A perspective can simplify the view of a cube for specific purposes.</span></span> <span data-ttu-id="d6cd5-104">根據預設，使用者可以看到 Cube 中他們擁有權限的所有元素。</span><span class="sxs-lookup"><span data-stu-id="d6cd5-104">By default, users can see all of the elements in a cube to which they have permissions.</span></span> <span data-ttu-id="d6cd5-105">當使用者檢視整個 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Cube 時，他們所檢視的就是該 Cube 的預設檢視方塊。</span><span class="sxs-lookup"><span data-stu-id="d6cd5-105">What users are viewing when they view an entire [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] cube is the default perspective for the cube.</span></span> <span data-ttu-id="d6cd5-106">整個 Cube 的檢視可能非常複雜，讓使用者難以瀏覽，尤其有的使用者只需要與一小部分的 Cube 互動，即可滿足他們的商業智慧和報告需求。</span><span class="sxs-lookup"><span data-stu-id="d6cd5-106">A view of the whole cube can be very complex for users to navigate, especially for users who only need to interact with a small part of the cube to satisfy their business intelligence and reporting requirements.</span></span>  
  
 <span data-ttu-id="d6cd5-107">若要簡化 Cube 明顯的複雜性，您可以建立稱為 *「檢視方塊」*(Perspective) 的可檢視 Cube 子集，它只會讓使用者看到 Cube 中部分的量值群組、量值、維度、屬性、階層、關鍵效能指標 (KPI)、動作以及導出成員。</span><span class="sxs-lookup"><span data-stu-id="d6cd5-107">To reduce the apparent complexity of a cube, you can create viewable subsets of the cube, called *perspectives*, which show users only a part of the measure groups, measures, dimensions, attributes, hierarchies, Key Performance Indicators (KPIs), actions, and calculated members in the cube.</span></span> <span data-ttu-id="d6cd5-108">這對於使用針對舊版 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]所撰寫的用戶端應用程式特別有用。</span><span class="sxs-lookup"><span data-stu-id="d6cd5-108">This can be particularly useful for working with client applications that were written for a previous release of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="d6cd5-109">例如，雖然這些用戶端沒有顯示資料夾或檢視方塊的概念，但是對於舊版的用戶端而言，檢視方塊就像是 Cube 一樣。</span><span class="sxs-lookup"><span data-stu-id="d6cd5-109">These clients have no concept of display folders or perspectives, for example, but a perspective appears to older clients as if it were a cube.</span></span> <span data-ttu-id="d6cd5-110">如需詳細資訊，請參閱 [檢視方塊](multidimensional-models-olap-logical-cube-objects/perspectives.md)和 [多維度模型中的檢視方塊](multidimensional-models/perspectives-in-multidimensional-models.md)。</span><span class="sxs-lookup"><span data-stu-id="d6cd5-110">For more information, see [Perspectives](multidimensional-models-olap-logical-cube-objects/perspectives.md), and [Perspectives in Multidimensional Models](multidimensional-models/perspectives-in-multidimensional-models.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d6cd5-111">雖然檢視方塊不是安全性機制，不過這個工具卻可以提供更理想的使用者經驗。</span><span class="sxs-lookup"><span data-stu-id="d6cd5-111">A perspective is not a security mechanism, but instead is a tool for providing a better user experience.</span></span> <span data-ttu-id="d6cd5-112">檢視方塊的所有安全性，都是繼承自基礎 Cube。</span><span class="sxs-lookup"><span data-stu-id="d6cd5-112">All security for a perspective is inherited from the underlying cube.</span></span>  
  
 <span data-ttu-id="d6cd5-113">在這個主題的工作中，您要定義幾個不同的檢視方塊，然後透過每一個新檢視方塊來瀏覽 Cube。</span><span class="sxs-lookup"><span data-stu-id="d6cd5-113">In the tasks in this topic, you will define several different perspectives and then browse the cube through each of these new perspectives.</span></span>  
  
## <a name="defining-an-internet-sales-perspective"></a><span data-ttu-id="d6cd5-114">定義網際網路銷售檢視方塊</span><span class="sxs-lookup"><span data-stu-id="d6cd5-114">Defining an Internet Sales Perspective</span></span>  
  
1.  <span data-ttu-id="d6cd5-115">開啟 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 教學課程 Cube 的 [Cube 設計師]，然後按一下 [檢視方塊]\*\*\*\* 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="d6cd5-115">Open Cube Designer for the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube, and then click the **Perspectives** tab.</span></span>  
  
     <span data-ttu-id="d6cd5-116">所有物件和其物件類型都會顯示在 [檢視方塊]\*\*\*\* 窗格中，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="d6cd5-116">All the objects and their object types appear in the **Perspectives** pane, as shown in the following image.</span></span>  
  
     <span data-ttu-id="d6cd5-117">![Cube 設計師的檢視方塊窗格](../../2014/tutorials/media/l9-perspectives-1.gif "Cube 設計師的檢視方塊窗格")</span><span class="sxs-lookup"><span data-stu-id="d6cd5-117">![Perspectives pane of Cube Designer](../../2014/tutorials/media/l9-perspectives-1.gif "Perspectives pane of Cube Designer")</span></span>  
  
2.  <span data-ttu-id="d6cd5-118">在 [檢視方塊]\*\*\*\* 索引標籤的工具列上，按一下 [新增檢視方塊]\*\*\*\* 按鈕。</span><span class="sxs-lookup"><span data-stu-id="d6cd5-118">On the toolbar of the **Perspectives** tab, click the **New Perspective** button.</span></span>  
  
     <span data-ttu-id="d6cd5-119">新的檢視方塊便會出現在 [檢視方塊名稱]\*\*\*\* 資料行中，並顯示預設名稱 [檢視方塊]\*\*\*\*，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="d6cd5-119">A new perspective appears in the **Perspective Name** column with a default name of **Perspective**, as shown in the following image.</span></span> <span data-ttu-id="d6cd5-120">請注意，每一個物件的核取方塊都會選取；除非您特別清除某個物件的核取方塊，否則這個檢視方塊與這個 Cube 的預設檢視方塊完全一樣。</span><span class="sxs-lookup"><span data-stu-id="d6cd5-120">Notice that the check box for every object is selected; until you clear the check box for an object, this perspective is identical to the default perspective of this cube.</span></span>  
  
     <span data-ttu-id="d6cd5-121">![檢視方塊名稱資料行中的檢視方塊](../../2014/tutorials/media/l9-perspectives-2.gif "檢視方塊名稱資料行中的檢視方塊")</span><span class="sxs-lookup"><span data-stu-id="d6cd5-121">![New perspective in Perspective Name column](../../2014/tutorials/media/l9-perspectives-2.gif "New perspective in Perspective Name column")</span></span>  
  
3.  <span data-ttu-id="d6cd5-122">將 [觀點名稱] 變更為 `Internet Sales` 。</span><span class="sxs-lookup"><span data-stu-id="d6cd5-122">Change the perspective name to `Internet Sales`.</span></span>  
  
4.  <span data-ttu-id="d6cd5-123">在下一個資料列上，將 [DefaultMeasure] 設定為 [網際網路銷售 - 銷售量]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d6cd5-123">On the next row, set the DefaultMeasure to **Internet Sales-Sales Amount**.</span></span>  
  
     <span data-ttu-id="d6cd5-124">當使用者利用這個檢視方塊來瀏覽 Cube 時，這就是使用者會看到的量值 (除非他們另外指定其他量值)。</span><span class="sxs-lookup"><span data-stu-id="d6cd5-124">When users browse the cube by using this perspective, this will be the measure that the users see unless they specify some other measure.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="d6cd5-125">您也可以在 Cube 的 [Cube 結構]\*\*\*\* 索引標籤之 [屬性] 視窗中，為整個 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 教學課程 Cube 設定預設量值。</span><span class="sxs-lookup"><span data-stu-id="d6cd5-125">You can also set the default measure for the whole [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube in the Properties window on the **Cube Structure** tab for the cube.</span></span>  
  
5.  <span data-ttu-id="d6cd5-126">清除下列物件的核取方塊：</span><span class="sxs-lookup"><span data-stu-id="d6cd5-126">Clear the check box for the following objects:</span></span>  
  
    -   <span data-ttu-id="d6cd5-127">`Reseller Sales`量值群組</span><span class="sxs-lookup"><span data-stu-id="d6cd5-127">`Reseller Sales` measure group</span></span>  
  
    -   <span data-ttu-id="d6cd5-128">[銷售配額]\*\*\*\* 量值群組</span><span class="sxs-lookup"><span data-stu-id="d6cd5-128">**Sales Quotas** measure group</span></span>  
  
    -   <span data-ttu-id="d6cd5-129">[銷售配額 1]\*\*\*\* 量值群組</span><span class="sxs-lookup"><span data-stu-id="d6cd5-129">**Sales Quotas 1** measure group</span></span>  
  
    -   <span data-ttu-id="d6cd5-130">[轉售商]\*\*\*\* Cube 維度</span><span class="sxs-lookup"><span data-stu-id="d6cd5-130">**Reseller** cube dimension</span></span>  
  
    -   <span data-ttu-id="d6cd5-131">[轉售商地理位置]\*\*\*\* Cube 維度</span><span class="sxs-lookup"><span data-stu-id="d6cd5-131">**Reseller Geography** cube dimension</span></span>  
  
    -   <span data-ttu-id="d6cd5-132">[銷售領域]\*\*\*\* Cube 維度</span><span class="sxs-lookup"><span data-stu-id="d6cd5-132">**Sales Territory** cube dimension</span></span>  
  
    -   <span data-ttu-id="d6cd5-133">[員工]\*\*\*\* Cube 維度</span><span class="sxs-lookup"><span data-stu-id="d6cd5-133">**Employee** cube dimension</span></span>  
  
    -   <span data-ttu-id="d6cd5-134">[促銷]\*\*\*\* Cube 維度</span><span class="sxs-lookup"><span data-stu-id="d6cd5-134">**Promotion** cube dimension</span></span>  
  
    -   <span data-ttu-id="d6cd5-135">[轉售商收入]\*\*\*\* KPI</span><span class="sxs-lookup"><span data-stu-id="d6cd5-135">**Reseller Revenue** KPI</span></span>  
  
    -   <span data-ttu-id="d6cd5-136">[大型轉售商]\*\*\*\* 命名集</span><span class="sxs-lookup"><span data-stu-id="d6cd5-136">**Large Resellers** named set</span></span>  
  
    -   <span data-ttu-id="d6cd5-137">[總銷售量]\*\*\*\* 導出成員</span><span class="sxs-lookup"><span data-stu-id="d6cd5-137">**Total Sales Amount** calculated member</span></span>  
  
    -   <span data-ttu-id="d6cd5-138">[總產品成本]\*\*\*\* 導出成員</span><span class="sxs-lookup"><span data-stu-id="d6cd5-138">**Total Product Cost** calculated member</span></span>  
  
    -   <span data-ttu-id="d6cd5-139">[轉售商毛利率]\*\*\*\* 導出成員</span><span class="sxs-lookup"><span data-stu-id="d6cd5-139">**Reseller GPM** calculated member</span></span>  
  
    -   <span data-ttu-id="d6cd5-140">[總毛利率]\*\*\*\* 導出成員</span><span class="sxs-lookup"><span data-stu-id="d6cd5-140">**Total GPM** calculated member</span></span>  
  
    -   <span data-ttu-id="d6cd5-141">[轉售商銷售與所有產品的比率]\*\*\*\* 導出成員</span><span class="sxs-lookup"><span data-stu-id="d6cd5-141">**Reseller Sales Ratio to All Products** calculated member</span></span>  
  
    -   <span data-ttu-id="d6cd5-142">[總銷售與所有產品的比率]\*\*\*\* 導出成員</span><span class="sxs-lookup"><span data-stu-id="d6cd5-142">**Total Sales Ratio to All Products** calculated member</span></span>  
  
     <span data-ttu-id="d6cd5-143">這些物件與網際網路銷售無關。</span><span class="sxs-lookup"><span data-stu-id="d6cd5-143">These objects do not relate to Internet sales.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="d6cd5-144">您也可以在每個維度中，個別選取您要顯示在檢視方塊中的使用者定義階層和屬性。</span><span class="sxs-lookup"><span data-stu-id="d6cd5-144">Within each dimension, you can also individually select the user-defined hierarchies and attributes that you want to appear in a perspective.</span></span>  
  
## <a name="defining-a-reseller-sales-perspective"></a><span data-ttu-id="d6cd5-145">定義轉售商銷售檢視方塊</span><span class="sxs-lookup"><span data-stu-id="d6cd5-145">Defining a Reseller Sales Perspective</span></span>  
  
1.  <span data-ttu-id="d6cd5-146">在 [檢視方塊]\*\*\*\* 索引標籤的工具列上，按一下 [新增檢視方塊]\*\*\*\* 按鈕。</span><span class="sxs-lookup"><span data-stu-id="d6cd5-146">On the toolbar of the **Perspectives** tab, click the **New Perspective** button.</span></span>  
  
2.  <span data-ttu-id="d6cd5-147">將新觀點的名稱變更為 `Reseller Sales` 。</span><span class="sxs-lookup"><span data-stu-id="d6cd5-147">Change the name of the new perspective to `Reseller Sales`.</span></span>  
  
3.  <span data-ttu-id="d6cd5-148">將 [轉售商銷售 - 銷售量]\*\*\*\* 設為預設量值。</span><span class="sxs-lookup"><span data-stu-id="d6cd5-148">Set **Reseller Sales-Sales Amount** as the default measure.</span></span>  
  
     <span data-ttu-id="d6cd5-149">當使用者利用這個檢視方塊來瀏覽 Cube 時，這個量值就是使用者會看到的量值 (除非他們另外指定其他量值)。</span><span class="sxs-lookup"><span data-stu-id="d6cd5-149">When users browse the cube by using this perspective, this measure will be the measure that the users will see unless they specify some other measure.</span></span>  
  
4.  <span data-ttu-id="d6cd5-150">清除下列物件的核取方塊：</span><span class="sxs-lookup"><span data-stu-id="d6cd5-150">Clear the check box for the following objects:</span></span>  
  
    -   <span data-ttu-id="d6cd5-151">`Internet Sales`量值群組</span><span class="sxs-lookup"><span data-stu-id="d6cd5-151">`Internet Sales` measure group</span></span>  
  
    -   <span data-ttu-id="d6cd5-152">[網際網路銷售原因]\*\*\*\* 量值群組</span><span class="sxs-lookup"><span data-stu-id="d6cd5-152">**Internet Sales Reason** measure group</span></span>  
  
    -   <span data-ttu-id="d6cd5-153">[客戶]\*\*\*\* Cube 維度</span><span class="sxs-lookup"><span data-stu-id="d6cd5-153">**Customer** cube dimension</span></span>  
  
    -   <span data-ttu-id="d6cd5-154">[網際網路銷售訂單的詳細資料]\*\*\*\* Cube 維度</span><span class="sxs-lookup"><span data-stu-id="d6cd5-154">**Internet Sales Order Details** cube dimension</span></span>  
  
    -   <span data-ttu-id="d6cd5-155">[銷售原因]\*\*\*\* Cube 維度</span><span class="sxs-lookup"><span data-stu-id="d6cd5-155">**Sales Reason** cube dimension</span></span>  
  
    -   <span data-ttu-id="d6cd5-156">[網際網路銷售詳細資訊鑽研動作]\*\*\*\* 鑽研動作</span><span class="sxs-lookup"><span data-stu-id="d6cd5-156">**Internet Sales Details Drillthrough Action** drillthrough action</span></span>  
  
    -   <span data-ttu-id="d6cd5-157">[總銷售量]\*\*\*\* 導出成員</span><span class="sxs-lookup"><span data-stu-id="d6cd5-157">**Total Sales Amount** calculated member</span></span>  
  
    -   <span data-ttu-id="d6cd5-158">[總產品成本]\*\*\*\* 導出成員</span><span class="sxs-lookup"><span data-stu-id="d6cd5-158">**Total Product Cost** calculated member</span></span>  
  
    -   <span data-ttu-id="d6cd5-159">[網際網路毛利率]\*\*\*\* 導出成員</span><span class="sxs-lookup"><span data-stu-id="d6cd5-159">**Internet GPM** calculated member</span></span>  
  
    -   <span data-ttu-id="d6cd5-160">[總毛利率]\*\*\*\* 導出成員</span><span class="sxs-lookup"><span data-stu-id="d6cd5-160">**Total GPM** calculated member</span></span>  
  
    -   <span data-ttu-id="d6cd5-161">[網際網路銷售與所有產品的比率]\*\*\*\* 導出成員</span><span class="sxs-lookup"><span data-stu-id="d6cd5-161">**Internet Sales Ratio to All Products** calculated member</span></span>  
  
    -   <span data-ttu-id="d6cd5-162">[總銷售與所有產品的比率]\*\*\*\* 導出成員</span><span class="sxs-lookup"><span data-stu-id="d6cd5-162">**Total Sales Ratio to All Products** calculated member</span></span>  
  
     <span data-ttu-id="d6cd5-163">這些物件與轉售商銷售無關。</span><span class="sxs-lookup"><span data-stu-id="d6cd5-163">These objects do not relate to resellers sales.</span></span>  
  
## <a name="defining-a-sales-summary-perspective"></a><span data-ttu-id="d6cd5-164">定義銷售摘要檢視方塊</span><span class="sxs-lookup"><span data-stu-id="d6cd5-164">Defining a Sales Summary Perspective</span></span>  
  
1.  <span data-ttu-id="d6cd5-165">在 [檢視方塊]\*\*\*\* 索引標籤的工具列上，按一下 [新增檢視方塊]\*\*\*\* 按鈕。</span><span class="sxs-lookup"><span data-stu-id="d6cd5-165">On the toolbar of the **Perspectives** tab, click the **New Perspective** button.</span></span>  
  
2.  <span data-ttu-id="d6cd5-166">將新觀點的名稱變更為 `Sales Summary` 。</span><span class="sxs-lookup"><span data-stu-id="d6cd5-166">Change the name of the new perspective to `Sales Summary`.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="d6cd5-167">您不可以將導出量值指定為預設量值。</span><span class="sxs-lookup"><span data-stu-id="d6cd5-167">You cannot specify a calculated measure as the default measure.</span></span>  
  
3.  <span data-ttu-id="d6cd5-168">清除下列物件的核取方塊：</span><span class="sxs-lookup"><span data-stu-id="d6cd5-168">Clear the check box for the following objects:</span></span>  
  
    -   <span data-ttu-id="d6cd5-169">`Internet Sales`量值群組</span><span class="sxs-lookup"><span data-stu-id="d6cd5-169">`Internet Sales` measure group</span></span>  
  
    -   <span data-ttu-id="d6cd5-170">`Reseller Sales`量值群組</span><span class="sxs-lookup"><span data-stu-id="d6cd5-170">`Reseller Sales` measure group</span></span>  
  
    -   <span data-ttu-id="d6cd5-171">[網際網路銷售原因]\*\*\*\* 量值群組</span><span class="sxs-lookup"><span data-stu-id="d6cd5-171">**Internet Sales Reason** measure group</span></span>  
  
    -   <span data-ttu-id="d6cd5-172">[銷售配額]\*\*\*\* 量值群組</span><span class="sxs-lookup"><span data-stu-id="d6cd5-172">**Sales Quotas** measure group</span></span>  
  
    -   <span data-ttu-id="d6cd5-173">[銷售配額1]\*\*\*\* 量值群組</span><span class="sxs-lookup"><span data-stu-id="d6cd5-173">**Sales Quotas1** measure group</span></span>  
  
    -   <span data-ttu-id="d6cd5-174">[網際網路銷售訂單的詳細資料]\*\*\*\* Cube 維度</span><span class="sxs-lookup"><span data-stu-id="d6cd5-174">**Internet Sales Order Details** cube dimension</span></span>  
  
    -   <span data-ttu-id="d6cd5-175">[銷售原因]\*\*\*\* Cube 維度</span><span class="sxs-lookup"><span data-stu-id="d6cd5-175">**Sales Reason** cube dimension</span></span>  
  
    -   <span data-ttu-id="d6cd5-176">[網際網路銷售詳細資訊鑽研動作]\*\*\*\* 鑽研動作</span><span class="sxs-lookup"><span data-stu-id="d6cd5-176">**Internet Sales Details Drillthrough Action** drillthrough action</span></span>  
  
4.  <span data-ttu-id="d6cd5-177">選取下列物件的核取方塊：</span><span class="sxs-lookup"><span data-stu-id="d6cd5-177">Select the check box for the following objects:</span></span>  
  
    -   <span data-ttu-id="d6cd5-178">[網際網路銷售計數]\*\*\*\* 量值</span><span class="sxs-lookup"><span data-stu-id="d6cd5-178">**Internet Sales Count** measure</span></span>  
  
    -   <span data-ttu-id="d6cd5-179">[轉售商銷售計數]\*\*\*\* 量值</span><span class="sxs-lookup"><span data-stu-id="d6cd5-179">**Reseller Sales Count** measure</span></span>  
  
## <a name="browsing-the-cube-through-each-perspective"></a><span data-ttu-id="d6cd5-180">透過每一個檢視方塊來瀏覽</span><span class="sxs-lookup"><span data-stu-id="d6cd5-180">Browsing the Cube Through Each Perspective</span></span>  
  
1.  <span data-ttu-id="d6cd5-181">在 [建立]\*\*\*\* 功能表上，按一下 [部署 Analysis Services 教學課程]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d6cd5-181">On the **Build** menu, click **Deploy Analysis Services Tutorial**.</span></span>  
  
2.  <span data-ttu-id="d6cd5-182">順利完成部署之後，請切換至 [瀏覽器]\*\*\*\* 索引標籤，然後按一下 [重新連接]\*\*\*\* 按鈕。</span><span class="sxs-lookup"><span data-stu-id="d6cd5-182">When deployment has successfully completed, switch to the **Browser** tab, and then click the **Reconnect** button.</span></span>  
  
3.  <span data-ttu-id="d6cd5-183">啟動 Excel。</span><span class="sxs-lookup"><span data-stu-id="d6cd5-183">Start Excel.</span></span>  
  
4.  <span data-ttu-id="d6cd5-184">[在 Excel 中進行分析] 會提示您選擇在 Excel 中瀏覽模型時要使用的檢視方塊，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="d6cd5-184">Analyze in Excel prompts you to choose which perspective to use when browsing the model in Excel, as shown in the following image.</span></span>  
  
     <span data-ttu-id="d6cd5-185">![網際網路銷售額檢視方塊的物件](../../2014/tutorials/media/l9-perspectives-3.gif "網際網路銷售額檢視方塊的物件")</span><span class="sxs-lookup"><span data-stu-id="d6cd5-185">![Objects for the Internet Sales perspective](../../2014/tutorials/media/l9-perspectives-3.gif "Objects for the Internet Sales perspective")</span></span>  
  
5.  <span data-ttu-id="d6cd5-186">或者，您可以從 Windows 的 [開始] 功能表啟動 Excel、在 localhost 上定義與 Analysis Services Tutorial 資料庫的連接，然後在 [資料連接] 精靈中選擇檢視方塊，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="d6cd5-186">Alternatively, you can start Excel from the Windows Start menu, define a connection to the Analysis Services Tutorial database on localhost, and choose a perspective in the Data Connection wizard, as shown in the following image.</span></span>  
  
     <span data-ttu-id="d6cd5-187">![Excel 中的資料連線精靈](../../2014/tutorials/media/l9-perspectives-3b.gif "Excel 中的資料連線精靈")</span><span class="sxs-lookup"><span data-stu-id="d6cd5-187">![Data Connection wizard in Excel](../../2014/tutorials/media/l9-perspectives-3b.gif "Data Connection wizard in Excel")</span></span>  
  
6.  <span data-ttu-id="d6cd5-188">`Internet Sales`在 [**透視圖**] 清單中選取，然後在 [中繼資料] 窗格中檢查量值和維度。</span><span class="sxs-lookup"><span data-stu-id="d6cd5-188">Select `Internet Sales` in the **Perspective** list and then review the measures and dimensions in the metadata pane.</span></span>  
  
     <span data-ttu-id="d6cd5-189">請注意，只有那些針對 [網際網路銷售] 檢視方塊所指定的物件才會顯示出來。</span><span class="sxs-lookup"><span data-stu-id="d6cd5-189">Notice that only those objects that are specified for the Internet Sales perspective appear.</span></span>  
  
7.  <span data-ttu-id="d6cd5-190">在 [中繼資料] 窗格中，展開 [量值]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d6cd5-190">In the metadata pane, expand **Measures**.</span></span>  
  
     <span data-ttu-id="d6cd5-191">請注意，只有 `Internet Sales` 量值群組會出現，以及 [**網際網路毛利率**] 和 [**網際網路銷售與所有產品的比率**] 導出成員。</span><span class="sxs-lookup"><span data-stu-id="d6cd5-191">Notice that only the `Internet Sales` measure group appears, together with the **Internet GPM** and **Internet Sales Ratio to All Products** calculated members.</span></span>  
  
8.  <span data-ttu-id="d6cd5-192">在模型中，再次選取 Excel。</span><span class="sxs-lookup"><span data-stu-id="d6cd5-192">In the model, select Excel again.</span></span> <span data-ttu-id="d6cd5-193">選取 `Sales Summary`。</span><span class="sxs-lookup"><span data-stu-id="d6cd5-193">Select `Sales Summary`.</span></span>  
  
     <span data-ttu-id="d6cd5-194">請注意，每一個量值群組只會出現一個量值，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="d6cd5-194">Notice that in each of these measure groups, only a single measure appears, as shown in the following image.</span></span>  
  
     <span data-ttu-id="d6cd5-195">![網際網路銷售額和轉售商銷售額量值](../../2014/tutorials/media/l9-perspectives-4.gif "網際網路銷售額和轉售商銷售額量值")</span><span class="sxs-lookup"><span data-stu-id="d6cd5-195">![Internet Sales and Reseller Sales measures](../../2014/tutorials/media/l9-perspectives-4.gif "Internet Sales and Reseller Sales measures")</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="d6cd5-196">本課程的下一項工作</span><span class="sxs-lookup"><span data-stu-id="d6cd5-196">Next Task in Lesson</span></span>  
 [<span data-ttu-id="d6cd5-197">定義和瀏覽翻譯</span><span class="sxs-lookup"><span data-stu-id="d6cd5-197">Defining and Browsing Translations</span></span>](lesson-9-2-defining-and-browsing-translations.md)  
  
## <a name="see-also"></a><span data-ttu-id="d6cd5-198">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d6cd5-198">See Also</span></span>  
 <span data-ttu-id="d6cd5-199">[視角](multidimensional-models-olap-logical-cube-objects/perspectives.md) </span><span class="sxs-lookup"><span data-stu-id="d6cd5-199">[Perspectives](multidimensional-models-olap-logical-cube-objects/perspectives.md) </span></span>  
 [<span data-ttu-id="d6cd5-200">多維度模型中的檢視方塊</span><span class="sxs-lookup"><span data-stu-id="d6cd5-200">Perspectives in Multidimensional Models</span></span>](multidimensional-models/perspectives-in-multidimensional-models.md)  
  
  
