---
title: 建立和管理 (SSAS 表格式) 的 Kpi |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.kpi.f1
ms.assetid: c96026c2-4394-4c3c-986b-4c95a4421900
author: minewiskan
ms.author: owend
ms.openlocfilehash: 8e9d7ef77939efe407ed6ab0d725a6d788c58b49
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594212"
---
# <a name="create-and-manage-kpis-ssas-tabular"></a><span data-ttu-id="b07a2-102">建立及管理 KPI (SSAS 表格式)</span><span class="sxs-lookup"><span data-stu-id="b07a2-102">Create and Manage KPIs (SSAS Tabular)</span></span>
  <span data-ttu-id="b07a2-103">本主題描述如何建立、編輯或刪除表格式模型中的 KPI (關鍵效能指標)。</span><span class="sxs-lookup"><span data-stu-id="b07a2-103">This topic describes how to create, edit, or delete a KPI (Key Performance Indicator) in a tabular model.</span></span> <span data-ttu-id="b07a2-104">若要建立 KPI，請選取評估為 KPI 基底值的量值。</span><span class="sxs-lookup"><span data-stu-id="b07a2-104">To create a KPI, you select a measure that evaluates to the KPI's Base value.</span></span> <span data-ttu-id="b07a2-105">然後使用 [關鍵效能指標] 對話方塊選取判斷為目標值的第二個量值或絕對值。</span><span class="sxs-lookup"><span data-stu-id="b07a2-105">You then use the Key Performance Indicator dialog box to select a second measure or an absolute value that evaluates to a target value.</span></span> <span data-ttu-id="b07a2-106">接著您可以定義測量基底和目標量值之間效能的狀態臨界值。</span><span class="sxs-lookup"><span data-stu-id="b07a2-106">You can then define status thresholds that measure the performance between the Base and Target measures.</span></span>  
  
 <span data-ttu-id="b07a2-107">本主題也包括下列工作：</span><span class="sxs-lookup"><span data-stu-id="b07a2-107">This topic includes the following tasks:</span></span>  
  
-   [<span data-ttu-id="b07a2-108">建立 KPI</span><span class="sxs-lookup"><span data-stu-id="b07a2-108">To create a KPI</span></span>](#bkmk_create_KPI)  
  
-   [<span data-ttu-id="b07a2-109">編輯 KPI</span><span class="sxs-lookup"><span data-stu-id="b07a2-109">To edit a KPI</span></span>](#bkmk_edit_KPI)  
  
-   [<span data-ttu-id="b07a2-110">若要刪除 KPI 和基底量值</span><span class="sxs-lookup"><span data-stu-id="b07a2-110">To delete a KPI and the base measure</span></span>](#bkmk_delete)  
  
-   [<span data-ttu-id="b07a2-111">刪除 KPI，但保留基底量值</span><span class="sxs-lookup"><span data-stu-id="b07a2-111">To delete a KPI, but keep the base measure</span></span>](#bkmk_delete_KPI)  
  
## <a name="tasks"></a><span data-ttu-id="b07a2-112">工作</span><span class="sxs-lookup"><span data-stu-id="b07a2-112">Tasks</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="b07a2-113">在建立 KPI 之前，您必須先建立判斷為值的基底量值。</span><span class="sxs-lookup"><span data-stu-id="b07a2-113">Before creating a KPI, you must first create a Base measure that evaluates to value.</span></span> <span data-ttu-id="b07a2-114">接著將此基底量值延伸至 KPI。</span><span class="sxs-lookup"><span data-stu-id="b07a2-114">You then extend the Base measure to a KPI.</span></span> <span data-ttu-id="b07a2-115">在另一個主題中將說明如何建立量值， [建立及管理量值 &#40;SSAS 表格式&#41;](measures-ssas-tabular.md)。</span><span class="sxs-lookup"><span data-stu-id="b07a2-115">How to create measures are described in another topic, [Create and Manage Measures &#40;SSAS Tabular&#41;](measures-ssas-tabular.md).</span></span> <span data-ttu-id="b07a2-116">KPI 也需要目標值。</span><span class="sxs-lookup"><span data-stu-id="b07a2-116">A KPI also requires a target value.</span></span> <span data-ttu-id="b07a2-117">此值可來自另一個預先定義的量值或絕對值。</span><span class="sxs-lookup"><span data-stu-id="b07a2-117">This value can be from another pre-defined measure or an absolute value.</span></span> <span data-ttu-id="b07a2-118">一旦將基底量值延伸至 KPI 之後，您就可以在 [關鍵效能指標] 對話方塊中選取目標值及定義狀態臨界值。</span><span class="sxs-lookup"><span data-stu-id="b07a2-118">Once you have extended a Base measure to a KPI, you can then select the target value and define status thresholds in the Key Performance Indicator dialog box.</span></span>  
  
###  <a name="to-create-a-kpi"></a><a name="bkmk_create_KPI"></a><span data-ttu-id="b07a2-119">建立 KPI</span><span class="sxs-lookup"><span data-stu-id="b07a2-119">To create a KPI</span></span>  
  
1.  <span data-ttu-id="b07a2-120">在量值方格中，以滑鼠右鍵按一下將作為基底量值 (值) 使用的量值，然後按一下 [建立 KPI]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b07a2-120">In the measure grid, right-click the measure that will serve as the Base measure (value), and then click **Create KPI**.</span></span>  
  
2.  <span data-ttu-id="b07a2-121">在 **[關鍵效能指標]** 對話方塊的 **[定義目標值]** 中，選取下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="b07a2-121">In the **Key Performance Indicator** dialog box, in **Define target value**, select from one of the following:</span></span>  
  
     <span data-ttu-id="b07a2-122">選取 **[量值]**，然後從清單方塊中選取目標量值。</span><span class="sxs-lookup"><span data-stu-id="b07a2-122">Select **Measure**, and then select a target measure from the listbox.</span></span>  
  
     <span data-ttu-id="b07a2-123">選取 **[絕對值]**，然後輸入數值。</span><span class="sxs-lookup"><span data-stu-id="b07a2-123">Select **Absolute value**, and then type a numerical value.</span></span>  
  
3.  <span data-ttu-id="b07a2-124">在 **[定義狀態臨界值]** 中，按一下並滑動高低臨界值。</span><span class="sxs-lookup"><span data-stu-id="b07a2-124">In **Define status thresholds**, click and slide the low and high threshold values.</span></span>  
  
4.  <span data-ttu-id="b07a2-125">在 **[選取圖示樣式]** 中，按一下影像類型。</span><span class="sxs-lookup"><span data-stu-id="b07a2-125">In **Select icon style**, click an image type.</span></span>  
  
5.  <span data-ttu-id="b07a2-126">按一下 **[描述]**，然後輸入 KPI、值、狀態和目標的描述。</span><span class="sxs-lookup"><span data-stu-id="b07a2-126">Click on **Descriptions**, and then type descriptions for KPI, Value, Status, and Target.</span></span>  
  
> [!TIP]  
>  <span data-ttu-id="b07a2-127">您可以使用 [在 Excel 中進行分析] 功能測試 KPI。</span><span class="sxs-lookup"><span data-stu-id="b07a2-127">You can use the Analyze in Excel feature to test your KPI.</span></span> <span data-ttu-id="b07a2-128">如需詳細資訊，請參閱本主題稍後的 [在 Excel 中進行分析 &#40;SSAS 表格式&#41;](analyze-in-excel-ssas-tabular.md)中的 [角色管理員] 對話方塊來定義角色的表格式模型作者。</span><span class="sxs-lookup"><span data-stu-id="b07a2-128">For more information, see [Analyze in Excel &#40;SSAS Tabular&#41;](analyze-in-excel-ssas-tabular.md).</span></span>  
  
###  <a name="to-edit-a-kpi"></a><a name="bkmk_edit_KPI"></a><span data-ttu-id="b07a2-129">編輯 KPI</span><span class="sxs-lookup"><span data-stu-id="b07a2-129">To edit a KPI</span></span>  
  
-   <span data-ttu-id="b07a2-130">在量值方格中，以滑鼠右鍵按一下作為 KPI 基底量值 (值) 的量值，然後按一下 [編輯 KPI 設定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b07a2-130">In the measure grid, right-click the measure that serves as the Base measure (value) of the KPI, and then click **Edit KPI Settings**.</span></span>  
  
###  <a name="to-delete-a-kpi-and-the-base-measure"></a><a name="bkmk_delete"></a> <span data-ttu-id="b07a2-131">刪除 KPI 和基底量值</span><span class="sxs-lookup"><span data-stu-id="b07a2-131">To delete a KPI and the base measure</span></span>  
  
-   <span data-ttu-id="b07a2-132">在量值方格中，以滑鼠右鍵按一下作為 KPI 基底量值 (值) 的量值，然後按一下 [刪除]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b07a2-132">In the measure grid, right-click the measure that serves as the Base measure (value) of the KPI, and then click **Delete**.</span></span>  
  
###  <a name="to-delete-a-kpi-but-keep-the-base-measure"></a><a name="bkmk_delete_KPI"></a><span data-ttu-id="b07a2-133">刪除 KPI，但保留基底量值</span><span class="sxs-lookup"><span data-stu-id="b07a2-133">To delete a KPI, but keep the base measure</span></span>  
  
-   <span data-ttu-id="b07a2-134">在量值方格中，以滑鼠右鍵按一下作為 KPI 基底量值 (值) 的量值，然後按一下 [刪除 KPI]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b07a2-134">In the measure grid, right-click the measure that serves as the Base measure (value) of the KPI, and then click **Delete KPI**.</span></span>  
  
## <a name="alt-shortcuts"></a><span data-ttu-id="b07a2-135">ALT 捷徑</span><span class="sxs-lookup"><span data-stu-id="b07a2-135">ALT Shortcuts</span></span>  
  
|<span data-ttu-id="b07a2-136">UI 區段</span><span class="sxs-lookup"><span data-stu-id="b07a2-136">UI section</span></span>|<span data-ttu-id="b07a2-137">按鍵命令</span><span class="sxs-lookup"><span data-stu-id="b07a2-137">Key command</span></span>|  
|----------------|-----------------|  
|<span data-ttu-id="b07a2-138">KPI 基準量值</span><span class="sxs-lookup"><span data-stu-id="b07a2-138">KPI base measure</span></span>|<span data-ttu-id="b07a2-139">ALT+B</span><span class="sxs-lookup"><span data-stu-id="b07a2-139">ALT+B</span></span>|  
|<span data-ttu-id="b07a2-140">KPI 狀態</span><span class="sxs-lookup"><span data-stu-id="b07a2-140">KPI Status</span></span>|<span data-ttu-id="b07a2-141">ALT+S</span><span class="sxs-lookup"><span data-stu-id="b07a2-141">ALT+S</span></span>|  
|<span data-ttu-id="b07a2-142">Measure</span><span class="sxs-lookup"><span data-stu-id="b07a2-142">Measure</span></span>|<span data-ttu-id="b07a2-143">ALT+M</span><span class="sxs-lookup"><span data-stu-id="b07a2-143">ALT+M</span></span>|  
|<span data-ttu-id="b07a2-144">[絕對值]</span><span class="sxs-lookup"><span data-stu-id="b07a2-144">Absolute value</span></span>|<span data-ttu-id="b07a2-145">ALT+A</span><span class="sxs-lookup"><span data-stu-id="b07a2-145">ALT+A</span></span>|  
|<span data-ttu-id="b07a2-146">[定義狀態臨界值]</span><span class="sxs-lookup"><span data-stu-id="b07a2-146">Define status thresholds</span></span>|<span data-ttu-id="b07a2-147">ALT+U</span><span class="sxs-lookup"><span data-stu-id="b07a2-147">ALT+U</span></span>|  
|<span data-ttu-id="b07a2-148">[選取圖示樣式]</span><span class="sxs-lookup"><span data-stu-id="b07a2-148">Select icon style</span></span>|<span data-ttu-id="b07a2-149">ALT+I</span><span class="sxs-lookup"><span data-stu-id="b07a2-149">ALT+I</span></span>|  
|<span data-ttu-id="b07a2-150">趨勢</span><span class="sxs-lookup"><span data-stu-id="b07a2-150">Trend</span></span>|<span data-ttu-id="b07a2-151">ALT+T</span><span class="sxs-lookup"><span data-stu-id="b07a2-151">ALT+T</span></span>|  
|<span data-ttu-id="b07a2-152">說明</span><span class="sxs-lookup"><span data-stu-id="b07a2-152">Descriptions</span></span>|<span data-ttu-id="b07a2-153">ALT+D</span><span class="sxs-lookup"><span data-stu-id="b07a2-153">ALT+D</span></span>|  
|<span data-ttu-id="b07a2-154">趨勢</span><span class="sxs-lookup"><span data-stu-id="b07a2-154">Trend</span></span>|<span data-ttu-id="b07a2-155">ALT+T</span><span class="sxs-lookup"><span data-stu-id="b07a2-155">ALT+T</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b07a2-156">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b07a2-156">See Also</span></span>  
 <span data-ttu-id="b07a2-157">[&#40;SSAS 表格式&#41;的 Kpi](kpis-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="b07a2-157">[KPIs &#40;SSAS Tabular&#41;](kpis-ssas-tabular.md) </span></span>  
 <span data-ttu-id="b07a2-158">[&#40;SSAS 表格式&#41;的量值](measures-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="b07a2-158">[Measures &#40;SSAS Tabular&#41;](measures-ssas-tabular.md) </span></span>  
 [<span data-ttu-id="b07a2-159">建立及管理量值 &#40;SSAS 表格式&#41;</span><span class="sxs-lookup"><span data-stu-id="b07a2-159">Create and Manage Measures &#40;SSAS Tabular&#41;</span></span>](create-and-manage-measures-ssas-tabular.md)  
  
  
