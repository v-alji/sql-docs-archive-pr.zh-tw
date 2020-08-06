---
title: " (SSAS 表格式) 的 Kpi |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: a0524602-5239-45a7-8c44-2477302a3637
author: minewiskan
ms.author: owend
ms.openlocfilehash: 54cc7341f2d0f002496c1936f2c4f0808cd5e243
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687214"
---
# <a name="kpis-ssas-tabular"></a><span data-ttu-id="a312d-102">KPI (SSAS 表格式)</span><span class="sxs-lookup"><span data-stu-id="a312d-102">KPIs (SSAS Tabular)</span></span>
  <span data-ttu-id="a312d-103">表格式模型中的「關鍵效能指標」(KPI)\*\* 可用來針對由量值或絕對值定義的「目標」\*\* 值，量測由「基底」\*\* 量值定義之值的績效。</span><span class="sxs-lookup"><span data-stu-id="a312d-103">A *KPI* (Key Performance Indicator), in a tabular model, is used to gauge performance of a value, defined by a *Base* measure, against a *Target* value, also defined by a measure or by an absolute value.</span></span> <span data-ttu-id="a312d-104">本主題為表格式模型作者提供對於表格式模型中 KPI 的基本了解。</span><span class="sxs-lookup"><span data-stu-id="a312d-104">This topic provides tabular model authors a basic understanding of KPIs in a tabular model.</span></span>  
  
 <span data-ttu-id="a312d-105">本主題的章節：</span><span class="sxs-lookup"><span data-stu-id="a312d-105">Sections in this topic:</span></span>  
  
-   [<span data-ttu-id="a312d-106">優點</span><span class="sxs-lookup"><span data-stu-id="a312d-106">Benefits</span></span>](#bkmk_benefits)  
  
-   [<span data-ttu-id="a312d-107">範例</span><span class="sxs-lookup"><span data-stu-id="a312d-107">Example</span></span>](#bkmk_example)  
  
-   [<span data-ttu-id="a312d-108">建立和編輯 Kpi</span><span class="sxs-lookup"><span data-stu-id="a312d-108">Create and Edit KPIs</span></span>](#bkmk_create)  
  
-   [<span data-ttu-id="a312d-109">相關工作</span><span class="sxs-lookup"><span data-stu-id="a312d-109">Related Tasks</span></span>](#bkmk_related_tasks)  
  
##  <a name="benefits"></a><a name="bkmk_benefits"></a> <span data-ttu-id="a312d-110">優點</span><span class="sxs-lookup"><span data-stu-id="a312d-110">Benefits</span></span>  
 <span data-ttu-id="a312d-111">在商務用語中，關鍵效能指標 (KPI) 是量測商務目標的可量化度量。</span><span class="sxs-lookup"><span data-stu-id="a312d-111">In business terminology, a Key Performance Indicator (KPI) is a quantifiable measurement for gauging business objectives.</span></span> <span data-ttu-id="a312d-112">KPI 通常會在一段時間內進行評估。</span><span class="sxs-lookup"><span data-stu-id="a312d-112">A KPI is frequently evaluated over time.</span></span> <span data-ttu-id="a312d-113">例如，組織的銷售部門可以使用 KPI，針對預計的毛利來測量每月的毛利。</span><span class="sxs-lookup"><span data-stu-id="a312d-113">For example, the sales department of an organization may use a KPI to measure monthly gross profit against projected gross profit.</span></span> <span data-ttu-id="a312d-114">會計部門可以針對營收測量每月支出，以評估成本，而人力資源部門可以測量每季員工營業額。</span><span class="sxs-lookup"><span data-stu-id="a312d-114">The accounting department may measure monthly expenditures against revenue to evaluate costs, and a human resources department may measure quarterly employee turnover.</span></span> <span data-ttu-id="a312d-115">每一個都是 KPI 的範例。</span><span class="sxs-lookup"><span data-stu-id="a312d-115">Each is an example of a KPI.</span></span> <span data-ttu-id="a312d-116">商務專業人員經常會使用在商務計分卡中分組的 KPI，以取得商務成就之快速與精確的記錄摘要，或識別趨勢。</span><span class="sxs-lookup"><span data-stu-id="a312d-116">Business professionals frequently consume KPIs that are grouped together in a business scorecard to obtain a quick and accurate historical summary of business success or to identify trends.</span></span>  
  
 <span data-ttu-id="a312d-117">表格式模型中的 KPI 包括：</span><span class="sxs-lookup"><span data-stu-id="a312d-117">A KPI in a tabular model includes:</span></span>  
  
 <span data-ttu-id="a312d-118">**基底值**</span><span class="sxs-lookup"><span data-stu-id="a312d-118">**Base Value**</span></span>  
 <span data-ttu-id="a312d-119">基底值是由解析為值的量值來定義。</span><span class="sxs-lookup"><span data-stu-id="a312d-119">A Base value is defined by a measure that resolves to a value.</span></span> <span data-ttu-id="a312d-120">例如，此值可以是實際銷售的彙總，也可以是指定期間內的導出量值，例如收益。</span><span class="sxs-lookup"><span data-stu-id="a312d-120">This value, for example, can be an aggregate of actual Sales or a calculated measure such as Profit for a given period.</span></span>  
  
 <span data-ttu-id="a312d-121">**目標值**</span><span class="sxs-lookup"><span data-stu-id="a312d-121">**Target value**</span></span>  
 <span data-ttu-id="a312d-122">目標值是由解析為值的量值或由絕對值來定義。</span><span class="sxs-lookup"><span data-stu-id="a312d-122">A Target value is defined by a measure that resolves to a value, or by an absolute value.</span></span> <span data-ttu-id="a312d-123">例如，目標值可能是組織業務經理想要提升銷售或利潤所用的量。</span><span class="sxs-lookup"><span data-stu-id="a312d-123">For example, a target value could be the amount by which the business managers of an organization want to increase sales or profit.</span></span>  
  
 <span data-ttu-id="a312d-124">**狀態臨界值**</span><span class="sxs-lookup"><span data-stu-id="a312d-124">**Status thresholds**</span></span>  
 <span data-ttu-id="a312d-125">狀態臨界值是由介於高低臨界值之間的範圍來定義，或由固定值來定義。</span><span class="sxs-lookup"><span data-stu-id="a312d-125">A Status threshold is defined by the range between a low and high threshold or by a fixed value.</span></span> <span data-ttu-id="a312d-126">狀態臨界值會顯示圖形，幫助使用者輕鬆地判斷基底值相較於目標值的狀態。</span><span class="sxs-lookup"><span data-stu-id="a312d-126">The Status threshold displays with a graphic to help users easily determine the status of the Base value compared to the Target value.</span></span>  
  
##  <a name="example"></a><a name="bkmk_example"></a> <span data-ttu-id="a312d-127">範例</span><span class="sxs-lookup"><span data-stu-id="a312d-127">Example</span></span>  
 <span data-ttu-id="a312d-128">任職於 Adventure Works 的銷售經理想要建立樞紐分析表，用來快速顯示銷售員工是否達成給定期間 (年份) 的銷售配額。</span><span class="sxs-lookup"><span data-stu-id="a312d-128">The sales manager at Adventure Works wants to create a PivotTable that she can use to quickly display whether or not sales employees are meeting their sales quota for a given period (year).</span></span> <span data-ttu-id="a312d-129">對於每個銷售員工，她要樞紐分析表顯示實際銷售金額 (美元)、銷售配額量 (美元)，以及顯示每個銷售員工狀態是低於、等於或高於其銷售配額的簡單圖形。</span><span class="sxs-lookup"><span data-stu-id="a312d-129">For each sales employee, she wants the PivotTable to display the actual sales amount in dollars, the sales quota amount in dollars, and a simple graphic display showing the status of whether or not each sales employee is below, at, or above their sales quota.</span></span> <span data-ttu-id="a312d-130">她希望能依年份配量這些資料。</span><span class="sxs-lookup"><span data-stu-id="a312d-130">She wants to be able to slice the data by year.</span></span>  
  
 <span data-ttu-id="a312d-131">為了達到此目的，銷售經理會登錄其組織 BI 解決方案開發人員的協助，以將銷售 KPI 加入至 AdventureWorks 表格式模型。</span><span class="sxs-lookup"><span data-stu-id="a312d-131">To do this, the sales manager enlists the help of her organization's BI solution developer to add a Sales KPI to the AdventureWorks Tabular Model.</span></span> <span data-ttu-id="a312d-132">然後銷售經理使用 [!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)] 連接至 Adventure Works 表格式模型做為資料來源，並建立具有欄位 (量值和 KPI) 和交叉分析篩選器的樞紐分析表，以分析銷售主力是否達成其配額。</span><span class="sxs-lookup"><span data-stu-id="a312d-132">The sales manager will then use [!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)] to connect to the Adventure Works Tabular Model as a data source and create a PivotTable with the fields (measures and KPI) and slicers to analyze whether or not the sales force is meeting their quotas.</span></span>  
  
 <span data-ttu-id="a312d-133">在模型中，FactResellerSales 資料表的 SalesAmount 資料行上建立了量值，提供每個銷售員工的實際銷售金額 (美元)。</span><span class="sxs-lookup"><span data-stu-id="a312d-133">In the model, a measure on the SalesAmount column in the FactResellerSales table, which gives the actual sales amount in dollars for each sales employee is created.</span></span> <span data-ttu-id="a312d-134">此量值會定義 KPI 的基底值。</span><span class="sxs-lookup"><span data-stu-id="a312d-134">This measure will define the Base value of the KPI.</span></span>  
  
 <span data-ttu-id="a312d-135">Sales 量值是以下列公式建立的：</span><span class="sxs-lookup"><span data-stu-id="a312d-135">The Sales measure is created with the following formula:</span></span>  
  
```  
Sales:=Sum(FactResellerSales[SalesAmount])  
```  
  
 <span data-ttu-id="a312d-136">FactSalesQuota 資料表的 SalesAmountQuota 資料行為每個員工定義了銷售量配額。</span><span class="sxs-lookup"><span data-stu-id="a312d-136">The SalesAmountQuota column in the FactSalesQuota table has a sales amount quota defined for each employee.</span></span> <span data-ttu-id="a312d-137">此資料行的值會做為 KPI 的目標量值 (值)。</span><span class="sxs-lookup"><span data-stu-id="a312d-137">The values in this column will serve as the Target measure (value) in the KPI.</span></span>  
  
 <span data-ttu-id="a312d-138">SalesAmountQuota 量值是以下列公式建立的：</span><span class="sxs-lookup"><span data-stu-id="a312d-138">The SalesAmountQuota measure is created with the following formula:</span></span>  
  
```  
Target SalesAmountQuota:=Sum(FactSalesQuota[SalesAmountQuota])  
```  
  
> [!NOTE]  
>  <span data-ttu-id="a312d-139">FactSalesQuota 資料表的 EmployeeKey 資料行和 DimEmployees 資料表的 EmployeeKey 之間有關聯性。</span><span class="sxs-lookup"><span data-stu-id="a312d-139">There is a relationship between the EmployeeKey column in the FactSalesQuota table and the EmployeeKey in the DimEmployees table.</span></span> <span data-ttu-id="a312d-140">此關聯性為必要項，因此 DimEmployee 資料表中的每個銷售員工才能顯示在 FactSalesQuota 資料表中。</span><span class="sxs-lookup"><span data-stu-id="a312d-140">This relationship is necessary so that each sales employee in the DimEmployee table is represented in the FactSalesQuota table.</span></span>  
  
 <span data-ttu-id="a312d-141">現在已建立量值做為 KPI 的基底值和目標值，Sales 量值就會延伸至新的銷售 KPI。</span><span class="sxs-lookup"><span data-stu-id="a312d-141">Now that measures have been created to serve as the Base value and Target value of the KPI, the Sales measure is extended to a new Sales KPI.</span></span> <span data-ttu-id="a312d-142">在銷售 KPI 中，目標 SalesAmountQuota 量值是定義為目標值。</span><span class="sxs-lookup"><span data-stu-id="a312d-142">In the Sales KPI, the Target SalesAmountQuota measure is defined as the Target value.</span></span> <span data-ttu-id="a312d-143">狀態臨界值是定義為範圍百分比，其目標為 100%，表示 Sales 量值所定義的實際銷售符合目標 SalesAmoutnQuota 量值所定義的配額量。</span><span class="sxs-lookup"><span data-stu-id="a312d-143">The Status threshold is defined as a range by percentage, the target of which is 100% meaning actual sales defined by the Sales measure met the quota amount defined in the Target SalesAmoutnQuota measure.</span></span> <span data-ttu-id="a312d-144">高低百分比定義於狀態列，而且選取圖形類型。</span><span class="sxs-lookup"><span data-stu-id="a312d-144">Low and High percentages are defined on the status bar, and a graphic type is selected.</span></span>  
  
 <span data-ttu-id="a312d-145">銷售經理現在可以建立樞紐分析表，將 KPI 的基底值、目標值和狀態新增至 [值] 欄位。</span><span class="sxs-lookup"><span data-stu-id="a312d-145">The sales manager can now create a PivotTable adding the KPI's Base value, Target value, and Status to the Values field.</span></span> <span data-ttu-id="a312d-146">Employees 資料行會加入至 RowLabel 欄位，而 CalendarYear 資料行則會加入為交叉分析篩選器。</span><span class="sxs-lookup"><span data-stu-id="a312d-146">The Employees column is added to the RowLabel field, and the CalendarYear column is added as a Slicer.</span></span>  
  
 <span data-ttu-id="a312d-147">銷售經理現在可以依年份來配量每個銷售員工的實際銷售金額、銷售配額量和狀態。</span><span class="sxs-lookup"><span data-stu-id="a312d-147">The sales manager can now slice by year the actual sales amount, sales quota amount, and status for each sales employee.</span></span> <span data-ttu-id="a312d-148">她可以分析數年來銷售趨勢，決定是否需要調整銷售員工的銷售配額。</span><span class="sxs-lookup"><span data-stu-id="a312d-148">She can analyze sales trends over years to determine whether or not she needs to adjust the sales quota for a sales employee.</span></span>  
  
##  <a name="create-and-edit-kpis"></a><a name="bkmk_create"></a><span data-ttu-id="a312d-149">建立和編輯 Kpi</span><span class="sxs-lookup"><span data-stu-id="a312d-149">Create and Edit KPIs</span></span>  
 <span data-ttu-id="a312d-150">若要建立 KPI，請使用模型設計師中的 [關鍵效能指標] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="a312d-150">To create KPIs, in the model designer, you will use the Key Performance Indicator dialog box.</span></span> <span data-ttu-id="a312d-151">由於 KPI 必須與量值關聯，因此您可以透過擴充判斷為基底值的量值，然後建立判斷為目標值的量值或輸入絕對值，來建立 KPI。</span><span class="sxs-lookup"><span data-stu-id="a312d-151">Since KPIs must be associated with a measure, you create a KPI by extending a measure that evaluates to a Base value, and then either creating a measure that evaluates to a Target value or by entering an absolute value.</span></span> <span data-ttu-id="a312d-152">定義基底量值 (基底值) 和目標值之後，即可定義基底值與目標值之間的狀態臨界值參數。</span><span class="sxs-lookup"><span data-stu-id="a312d-152">After the Base measure (value) and Target value is defined, you can then define the status threshold parameters between the Base and Target values.</span></span> <span data-ttu-id="a312d-153">此狀態會以圖形格式顯示 (使用可選取的圖示、橫條、圖形或色彩)。</span><span class="sxs-lookup"><span data-stu-id="a312d-153">The status is displayed in a graphical format using selectable icons, bars, graphs, or colors.</span></span> <span data-ttu-id="a312d-154">然後可將基底和目標值以及狀態，以可根據其他資料欄位分割的值形式加入報表或樞紐分析表。</span><span class="sxs-lookup"><span data-stu-id="a312d-154">The Base and Target values, as well as the Status can then be added to a report or PivotTable as values that can be sliced against other data fields.</span></span>  
  
 <span data-ttu-id="a312d-155">若要檢視 [關鍵效能指標] 對話方塊，請在資料表的量值方格中，以滑鼠右鍵按一下做為基底值的量值，然後按一下 **[建立 KPI]**。</span><span class="sxs-lookup"><span data-stu-id="a312d-155">To view the Key Performance Indicator dialog box, in the measure grid for a table, right click a measure that will serve as the Base value, and then click **Create KPI**.</span></span> <span data-ttu-id="a312d-156">將量值擴充至 KPI 做為基底值之後，量值方格中的量值名稱旁會出現圖示，指出量值與 KPI 相關聯。</span><span class="sxs-lookup"><span data-stu-id="a312d-156">After a measure has been extended to a KPI as a Base value, an icon will appear alongside the measure name in the measure grid identifying the measure as associated with a KPI.</span></span>  
  
##  <a name="related-tasks"></a><a name="bkmk_related_tasks"></a> <span data-ttu-id="a312d-157">相關工作</span><span class="sxs-lookup"><span data-stu-id="a312d-157">Related Tasks</span></span>  
  
|<span data-ttu-id="a312d-158">主題</span><span class="sxs-lookup"><span data-stu-id="a312d-158">Topic</span></span>|<span data-ttu-id="a312d-159">描述</span><span class="sxs-lookup"><span data-stu-id="a312d-159">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="a312d-160">建立及管理 KPI &#40;SSAS 表格式&#41;</span><span class="sxs-lookup"><span data-stu-id="a312d-160">Create and Manage KPIs &#40;SSAS Tabular&#41;</span></span>](kpis-ssas-tabular.md)|<span data-ttu-id="a312d-161">描述如何使用基底量值、目標量值及狀態臨界值建立 KPI。</span><span class="sxs-lookup"><span data-stu-id="a312d-161">Describes how to create a KPI with a Base measure, a Target measure, and status thresholds.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a312d-162">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a312d-162">See Also</span></span>  
 <span data-ttu-id="a312d-163">[&#40;SSAS 表格式&#41;的量值](measures-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="a312d-163">[Measures &#40;SSAS Tabular&#41;](measures-ssas-tabular.md) </span></span>  
 [<span data-ttu-id="a312d-164">檢視方塊 &#40;SSAS 表格式&#41;</span><span class="sxs-lookup"><span data-stu-id="a312d-164">Perspectives &#40;SSAS Tabular&#41;</span></span>](perspectives-ssas-tabular.md)  
  
  
