---
title: 瞭解多維度模型的 Power View |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: d0558cae-8209-4242-80c5-2c95981b88b9
author: minewiskan
ms.author: owend
ms.openlocfilehash: 778bdb769238618e733e46f903cf70024cd27bff
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87700372"
---
# <a name="understanding-power-view-for-multidimensional-models"></a><span data-ttu-id="f9060-102">了解適用於多維度模型的 Power View</span><span class="sxs-lookup"><span data-stu-id="f9060-102">Understanding Power View for Multidimensional Models</span></span>
  <span data-ttu-id="f9060-103">本文描述 Microsoft SQL Server 2014 中的「多維度模型的 Power View」功能，並為想要在組織中實作 Power View 的 BI 專業人員和系統管理員提供重要資訊。</span><span class="sxs-lookup"><span data-stu-id="f9060-103">This article describes the Power View for Multidimensional Models feature in Microsoft SQL Server 2014, and provides important information for BI professionals and administrators who intend to implement Power View for Multidimensional Models in their organization.</span></span>  
  
 <span data-ttu-id="f9060-104">多維度模型提供領先業界的 OLAP 資料模型化、儲存體和分析解決方案。</span><span class="sxs-lookup"><span data-stu-id="f9060-104">Multidimensional models provide industry leading OLAP data modeling, storage, and analysis solutions.</span></span> <span data-ttu-id="f9060-105">SQL Server 2014 中的多維度模型透過 Microsoft Power View 支援特定資料分析、探索和視覺效果。</span><span class="sxs-lookup"><span data-stu-id="f9060-105">Multidimensional models in SQL Server 2014 support ad-hoc data analysis, exploration, and visualization by using Microsoft Power View.</span></span>  
  
 <span data-ttu-id="f9060-106">Power View 是一種精簡型 Web 用戶端，會在瀏覽器中從 SharePoint 文件庫的共用報表資料來源 (.rsds) 檔案啟動。</span><span class="sxs-lookup"><span data-stu-id="f9060-106">Power View is a thin web client that launches in the browser from a shared Report Data Source (.rsds) file in a SharePoint library.</span></span> <span data-ttu-id="f9060-107">報表資料來源會做為用戶端與後端資料來源之間的橋樑。</span><span class="sxs-lookup"><span data-stu-id="f9060-107">The Report Data Source acts as a bridge between the client and the back-end data source.</span></span> <span data-ttu-id="f9060-108">後端資料來源可以是 SharePoint 中的 PowerPivot 活頁簿、以表格式模式執行之 Analysis Services 伺服器上的表格式模型，或是以多維度模式執行之 Analysis Services 伺服器上的多維度模型。</span><span class="sxs-lookup"><span data-stu-id="f9060-108">The back-end data source can be a PowerPivot workbook in SharePoint, a Tabular model on an Analysis Services server running in Tabular mode, or a Multidimensional model on an Analysis Services server running in Multidimensional mode.</span></span> <span data-ttu-id="f9060-109">Power View 報表然後可以儲存至 SharePoint 文件庫或組件庫，與組織中的其他成員共用。</span><span class="sxs-lookup"><span data-stu-id="f9060-109">Power View reports can then be saved to a SharePoint library or gallery and shared with other members in your organization.</span></span>  
  
 <span data-ttu-id="f9060-110">**多維度模型架構的 Power View**</span><span class="sxs-lookup"><span data-stu-id="f9060-110">**Power View for Multidimensional Models architecture**</span></span>  
  
 <span data-ttu-id="f9060-111">![多維度模型架構的 Power View](../media/daxmd-architecture.gif "多維度模型架構的 Power View")</span><span class="sxs-lookup"><span data-stu-id="f9060-111">![Power View for Multidimensional Models Architecture](../media/daxmd-architecture.gif "Power View for Multidimensional Models Architecture")</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="f9060-112">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="f9060-112">Prerequisites</span></span>  
 <span data-ttu-id="f9060-113">**伺服器需求**</span><span class="sxs-lookup"><span data-stu-id="f9060-113">**Server Requirements**</span></span>  
  
-   <span data-ttu-id="f9060-114">SQL Server 2014 Enterprise 或 Business Intelligence 版本與以多維度模式執行的 Analysis Services。</span><span class="sxs-lookup"><span data-stu-id="f9060-114">SQL Server 2014 Enterprise or Business Intelligence edition with Analysis Services running in Multidimensional mode.</span></span>  
  
-   <span data-ttu-id="f9060-115">適用於 Microsoft SharePoint Server 2010 或 2013 Enterprise Edition 的 SQL Server 2014 Reporting Services 增益集。</span><span class="sxs-lookup"><span data-stu-id="f9060-115">SQL Server 2014 Reporting Services Add-in for Microsoft SharePoint Server 2010 or 2013 Enterprise Edition.</span></span>  
  
 <span data-ttu-id="f9060-116">**用戶端需求**</span><span class="sxs-lookup"><span data-stu-id="f9060-116">**Client Requirements**</span></span>  
  
-   <span data-ttu-id="f9060-117">Power View 用戶端功能需要 Microsoft Silverlight 5。</span><span class="sxs-lookup"><span data-stu-id="f9060-117">Power View client functionality requires Microsoft Silverlight 5.</span></span> <span data-ttu-id="f9060-118">如需詳細資訊，請參閱[規劃 Reporting Services 和 Power View 瀏覽器支援 &#40;Reporting Services 2014&#41;](../../reporting-services/browser-support-for-reporting-services-and-power-view.md)。</span><span class="sxs-lookup"><span data-stu-id="f9060-118">For more information, see [Planning for Reporting Services and Power View Browser Support &#40;Reporting Services 2014&#41;](../../reporting-services/browser-support-for-reporting-services-and-power-view.md).</span></span>  
  
## <a name="features"></a><span data-ttu-id="f9060-119">特性</span><span class="sxs-lookup"><span data-stu-id="f9060-119">Features</span></span>  
 <span data-ttu-id="f9060-120">**Power View 的原生支援**</span><span class="sxs-lookup"><span data-stu-id="f9060-120">**Native support for Power View**</span></span>  
  
 <span data-ttu-id="f9060-121">在此版本中，多維度模型透過 SharePoint 模式的 Power View，支援分析和視覺效果。</span><span class="sxs-lookup"><span data-stu-id="f9060-121">With this release, multidimensional models support analysis and visualization by using Power View in SharePoint mode.</span></span> <span data-ttu-id="f9060-122">您的多維度模型不需要特殊組態。</span><span class="sxs-lookup"><span data-stu-id="f9060-122">No special configuration of your multidimensional models is necessary.</span></span> <span data-ttu-id="f9060-123">不過，相較於其他用戶端工具，例如 Microsoft Excel 和 Microsoft Performance Point，Power View 顯示多維度模型物件的方式有些不同。</span><span class="sxs-lookup"><span data-stu-id="f9060-123">There are however some differences in how multidimensional model objects are displayed in Power View compared to other client tools such as Microsoft Excel and Microsoft Performance Point.</span></span> <span data-ttu-id="f9060-124">此版本不支援在 Excel 2013 中使用 Power View，進行多維度模型的分析和視覺效果。</span><span class="sxs-lookup"><span data-stu-id="f9060-124">This release does not support analysis and visualization of multidimensional models by using Power View in Excel 2013.</span></span>  
  
 <span data-ttu-id="f9060-125">**DAX 查詢的原生支援**</span><span class="sxs-lookup"><span data-stu-id="f9060-125">**Native support for DAX queries**</span></span>  
  
 <span data-ttu-id="f9060-126">在此版本中，除了比較傳統的 MDX 查詢之外，多維度模型還支援 DAX 查詢和函數。</span><span class="sxs-lookup"><span data-stu-id="f9060-126">With this release, multidimensional models support DAX queries and functions in addition to more traditional MDX queries.</span></span> <span data-ttu-id="f9060-127">有些 DAX 函數 (例如 PATH) 不適用於多維度模型。</span><span class="sxs-lookup"><span data-stu-id="f9060-127">Some DAX functions, such as PATH, are not applicable in multidimensional modeling.</span></span> <span data-ttu-id="f9060-128">若要進一步了解 DAX 及與 MDX 的比較，請參閱 [Data Analysis Expressions 和 MDX](https://msdn.microsoft.com/library/ff487170\(SQL.105\).aspx)。</span><span class="sxs-lookup"><span data-stu-id="f9060-128">For a better understanding of DAX and how it compares to MDX, see [Data Analysis Expressions and MDX](https://msdn.microsoft.com/library/ff487170\(SQL.105\).aspx).</span></span>  
  
## <a name="multidimensional-to-tabular-object-mapping"></a><span data-ttu-id="f9060-129">多維度與表格式物件的對應</span><span class="sxs-lookup"><span data-stu-id="f9060-129">Multidimensional to tabular object mapping</span></span>  
 <span data-ttu-id="f9060-130">Analysis Services 提供多維度模型的表格式模型中繼資料表示。</span><span class="sxs-lookup"><span data-stu-id="f9060-130">Analysis Services provides a tabular model metadata representation of a multidimensional model.</span></span> <span data-ttu-id="f9060-131">多維度模型的物件在 Power View 中以及在 CSDL 輸出 BI 註解中表示為表格式物件。</span><span class="sxs-lookup"><span data-stu-id="f9060-131">Objects in a multidimensional model are represented as tabular objects in Power View and in CSDL out with BI annotations.</span></span>  
  
 <span data-ttu-id="f9060-132">**物件對應摘要**</span><span class="sxs-lookup"><span data-stu-id="f9060-132">**Object mapping summary**</span></span>  
  
|<span data-ttu-id="f9060-133">多維度物件</span><span class="sxs-lookup"><span data-stu-id="f9060-133">Multidimensional Object</span></span>|<span data-ttu-id="f9060-134">表格式物件</span><span class="sxs-lookup"><span data-stu-id="f9060-134">Tabular Object</span></span>|  
|-----------------------------|--------------------|  
|<span data-ttu-id="f9060-135">Cube</span><span class="sxs-lookup"><span data-stu-id="f9060-135">Cube</span></span>|<span data-ttu-id="f9060-136">模型</span><span class="sxs-lookup"><span data-stu-id="f9060-136">Model</span></span>|  
|<span data-ttu-id="f9060-137">Cube 維度</span><span class="sxs-lookup"><span data-stu-id="f9060-137">Cube Dimension</span></span>|<span data-ttu-id="f9060-138">資料表</span><span class="sxs-lookup"><span data-stu-id="f9060-138">Table</span></span>|  
|<span data-ttu-id="f9060-139">維度屬性(索引鍵、名稱)</span><span class="sxs-lookup"><span data-stu-id="f9060-139">Dimension Attributes (Key(s), Name)</span></span>|<span data-ttu-id="f9060-140">資料行</span><span class="sxs-lookup"><span data-stu-id="f9060-140">Column</span></span>|  
|<span data-ttu-id="f9060-141">量值群組</span><span class="sxs-lookup"><span data-stu-id="f9060-141">Measure Group</span></span>|<span data-ttu-id="f9060-142">資料表</span><span class="sxs-lookup"><span data-stu-id="f9060-142">Table</span></span>|  
|<span data-ttu-id="f9060-143">Measure</span><span class="sxs-lookup"><span data-stu-id="f9060-143">Measure</span></span>|<span data-ttu-id="f9060-144">Measure</span><span class="sxs-lookup"><span data-stu-id="f9060-144">Measure</span></span>|  
|<span data-ttu-id="f9060-145">不含量值群組的量值</span><span class="sxs-lookup"><span data-stu-id="f9060-145">Measure without Measure Group</span></span>|<span data-ttu-id="f9060-146">在名為量值的資料表中</span><span class="sxs-lookup"><span data-stu-id="f9060-146">In a table named Measures</span></span>|  
|<span data-ttu-id="f9060-147">量值群組 Cube 維度關聯性</span><span class="sxs-lookup"><span data-stu-id="f9060-147">Measure Group Cube Dimension Relationship</span></span>|<span data-ttu-id="f9060-148">關聯性</span><span class="sxs-lookup"><span data-stu-id="f9060-148">Relationship</span></span>|  
|<span data-ttu-id="f9060-149">檢視方塊</span><span class="sxs-lookup"><span data-stu-id="f9060-149">Perspective</span></span>|<span data-ttu-id="f9060-150">檢視方塊</span><span class="sxs-lookup"><span data-stu-id="f9060-150">Perspective</span></span>|  
|<span data-ttu-id="f9060-151">KPI</span><span class="sxs-lookup"><span data-stu-id="f9060-151">KPI</span></span>|<span data-ttu-id="f9060-152">KPI</span><span class="sxs-lookup"><span data-stu-id="f9060-152">KPI</span></span>|  
|<span data-ttu-id="f9060-153">使用者/父子式階層</span><span class="sxs-lookup"><span data-stu-id="f9060-153">User/Parent-Child Hierarchies</span></span>|<span data-ttu-id="f9060-154">階層</span><span class="sxs-lookup"><span data-stu-id="f9060-154">Hierarchy</span></span>|  
|<span data-ttu-id="f9060-155">顯示資料夾</span><span class="sxs-lookup"><span data-stu-id="f9060-155">Display Folder</span></span>|<span data-ttu-id="f9060-156">顯示資料夾</span><span class="sxs-lookup"><span data-stu-id="f9060-156">Display Folder</span></span>|  
  
## <a name="measures-measure-groups-and-kpis"></a><span data-ttu-id="f9060-157">量值、量值群組和 KPI</span><span class="sxs-lookup"><span data-stu-id="f9060-157">Measures, measure groups, and KPIs</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f9060-158">本文中某些影像和文字參照 SQL Server 2012 範例資料庫 Adventure Works 多維度模型。</span><span class="sxs-lookup"><span data-stu-id="f9060-158">Some images and text in this article refer to the Adventure Works Multidimensional Model for SQL Server 2012 sample database.</span></span>  
  
 <span data-ttu-id="f9060-159">多維度 Cube 中的量值群組，在 Power View 欄位清單中顯示為含 Sigma (∑) 符號的資料表。</span><span class="sxs-lookup"><span data-stu-id="f9060-159">Measure groups in a multidimensional cube are seen in the Power View Field List as tables with the sigma (∑) sign.</span></span>  
  
 <span data-ttu-id="f9060-160">**Power View 欄位清單中的量值群組**</span><span class="sxs-lookup"><span data-stu-id="f9060-160">**Measure groups in the Power View Field List**</span></span>  
  
 <span data-ttu-id="f9060-161">![Power View 中的欄位清單](../media/daxmd-powerviewfieldlist.gif "Power View 中的欄位清單")</span><span class="sxs-lookup"><span data-stu-id="f9060-161">![Field List in Power View](../media/daxmd-powerviewfieldlist.gif "Field List in Power View")</span></span>  
  
 <span data-ttu-id="f9060-162">量值群組內的量值顯示為量值。</span><span class="sxs-lookup"><span data-stu-id="f9060-162">Measures within a measure group appear as measures.</span></span> <span data-ttu-id="f9060-163">如果有未與任何量值群組相關聯的導出量值，它們會分組在稱為「量值」的特殊資料表中。</span><span class="sxs-lookup"><span data-stu-id="f9060-163">If there are calculated measures that do not have an associated measure group, they will be grouped under a special table called Measures.</span></span>  
  
 <span data-ttu-id="f9060-164">為簡化複雜的多維度模型，模型作者可以在 Cube 中定義一組量值或 KPI，以便在顯示資料夾中找到。</span><span class="sxs-lookup"><span data-stu-id="f9060-164">To help simplify more complex multidimensional models, model authors can define a set of measures or KPIs in a cube to be located within a display folder.</span></span> <span data-ttu-id="f9060-165">Power View 可以顯示顯示資料夾和其中的量值和 KPI。</span><span class="sxs-lookup"><span data-stu-id="f9060-165">Power View can show display folders and the measures and KPIs in them.</span></span>  
  
 <span data-ttu-id="f9060-166">**量值群組中的量值和 KPI**</span><span class="sxs-lookup"><span data-stu-id="f9060-166">**Measures and KPIs in a measure group**</span></span>  
  
 <span data-ttu-id="f9060-167">![Power View 欄位清單中的量值群組](../media/daxmd-fieldlist-group.gif "Power View 欄位清單中的量值群組")</span><span class="sxs-lookup"><span data-stu-id="f9060-167">![Measure group in Power View Field List](../media/daxmd-fieldlist-group.gif "Measure group in Power View Field List")</span></span>  
  
### <a name="measures-as-variants"></a><span data-ttu-id="f9060-168">量值做為變化</span><span class="sxs-lookup"><span data-stu-id="f9060-168">Measures as variants</span></span>  
 <span data-ttu-id="f9060-169">多維度模型中的量值是變化。</span><span class="sxs-lookup"><span data-stu-id="f9060-169">Measures in multidimensional models are variants.</span></span> <span data-ttu-id="f9060-170">這表示，量值不是強型別，可以有不同的資料類型。</span><span class="sxs-lookup"><span data-stu-id="f9060-170">This means the measures are not strongly typed and can have different data types.</span></span> <span data-ttu-id="f9060-171">例如，在下圖中，財務報告資料表中的金額量值預設為 Currency 資料類型，但對於「統計帳戶」的子總計（也就是字串資料類型），也有字串值 "NA"。</span><span class="sxs-lookup"><span data-stu-id="f9060-171">For example, in the image below, the Amount measure in the Financial Reporting table by default is Currency data type, but also has a string value "NA" for the sub-total of "Statistical Accounts", which is String data type.</span></span> <span data-ttu-id="f9060-172">Power View 會將特定量值辨識為變化，並以不同的視覺效果顯示正確值和格式。</span><span class="sxs-lookup"><span data-stu-id="f9060-172">Power View recognizes certain measures as variants and shows the correct values and formatting in the different visualizations.</span></span>  
  
 <span data-ttu-id="f9060-173">**量值做為變化**</span><span class="sxs-lookup"><span data-stu-id="f9060-173">**Measure as variant**</span></span>  
  
 <span data-ttu-id="f9060-174">![Power View 中的非彙總階層](../media/daxmd-nonaggrattrib.gif "Power View 中的非彙總階層")</span><span class="sxs-lookup"><span data-stu-id="f9060-174">![Non-aggregatable hierarchy in Power View](../media/daxmd-nonaggrattrib.gif "Non-aggregatable hierarchy in Power View")</span></span>  
  
### <a name="implicit-measures"></a><span data-ttu-id="f9060-175">隱含量值</span><span class="sxs-lookup"><span data-stu-id="f9060-175">Implicit measures</span></span>  
 <span data-ttu-id="f9060-176">表格式模型讓使用者能夠建立「隱含」\*\* 量值，例如欄位的計數、加總或平均。</span><span class="sxs-lookup"><span data-stu-id="f9060-176">Tabular models provide users the ability to create *implicit* measures such as count, sum, or average on fields.</span></span> <span data-ttu-id="f9060-177">對於多維度模型，因為維度屬性資料的儲存方式不同，查詢隱含量值可能很耗時。</span><span class="sxs-lookup"><span data-stu-id="f9060-177">For multidimensional models, because dimension attribute data is stored is stored differently, querying implicit measures can take a long time.</span></span> <span data-ttu-id="f9060-178">因此，Power View 中無法使用隱含量值。</span><span class="sxs-lookup"><span data-stu-id="f9060-178">Because of this, implicit measures are not available in Power View.</span></span>  
  
## <a name="dimensions-attributes-and-hierarchies"></a><span data-ttu-id="f9060-179">維度、屬性和階層</span><span class="sxs-lookup"><span data-stu-id="f9060-179">Dimensions, attributes, and hierarchies</span></span>  
 <span data-ttu-id="f9060-180">Cube 維度在表格式中繼資料中公開為資料表。</span><span class="sxs-lookup"><span data-stu-id="f9060-180">Cube dimensions are exposed as tables in tabular metadata.</span></span> <span data-ttu-id="f9060-181">在 Power View 欄位清單中，維度屬性會顯示為顯示資料夾中的資料行。</span><span class="sxs-lookup"><span data-stu-id="f9060-181">In the Power View Field List, dimension attributes are shown as columns within display folders.</span></span>  <span data-ttu-id="f9060-182">AttributeHierarchyEnabled 屬性設為 false 的維度屬性，例如 Customer 維度中的 Birth Date 屬性，或是 AttributeHierarchyVisible 屬性設為 false 的維度屬性都不會出現在 Power View 欄位清單中。</span><span class="sxs-lookup"><span data-stu-id="f9060-182">The dimension attributes that have the AttributeHierarchyEnabled property set to false; for example: Birth Date attribute in Customer dimension, or AttributeHierarchyVisible property set to false will not appear in the Power View Field List.</span></span> <span data-ttu-id="f9060-183">多層級階層或使用者階層，例如 Customer 維度中的 Customer Geography，在 Power View 欄位清單中公開為階層。</span><span class="sxs-lookup"><span data-stu-id="f9060-183">Multi-level hierarchies or user hierarchies; for example Customer Geography in the Customer dimension, are exposed as hierarchies in the Power View Field List.</span></span> <span data-ttu-id="f9060-184">維度屬性的隱藏 UnknownMembers 會在 DAX 查詢和 Power View 中公開。</span><span class="sxs-lookup"><span data-stu-id="f9060-184">Hidden UnknownMembers of a dimension attribute are exposed in DAX Queries and in Power View.</span></span>  
  
 <span data-ttu-id="f9060-185">**SQL Server Data Tools (SSDT) 和 Power View 欄位清單中的維度、屬性和階層**</span><span class="sxs-lookup"><span data-stu-id="f9060-185">**Dimension, attributes and hierarchies in SQL Server Data Tools (SSDT) and Power View Field List**</span></span>  
  
 <span data-ttu-id="f9060-186">![SSDT 和 Power View 欄位清單中的維度](../media/daxmd-ssdt-dimensions.gif "SSDT 和 Power View 欄位清單中的維度")</span><span class="sxs-lookup"><span data-stu-id="f9060-186">![Dimensions in SSDT and in Power View Field List](../media/daxmd-ssdt-dimensions.gif "Dimensions in SSDT and in Power View Field List")</span></span>  
  
### <a name="dimension-attribute-type"></a><span data-ttu-id="f9060-187">維度屬性類型</span><span class="sxs-lookup"><span data-stu-id="f9060-187">Dimension attribute type</span></span>  
 <span data-ttu-id="f9060-188">多維度模型支援維度屬性與特定維度屬性類型產生關聯。</span><span class="sxs-lookup"><span data-stu-id="f9060-188">Multidimensional models support associating dimension attributes with specific dimension attribute types.</span></span> <span data-ttu-id="f9060-189">下圖顯示 Geography 維度中的 City、State-Province、Country 和 Postal Code 維度屬性與地理類型相關聯。</span><span class="sxs-lookup"><span data-stu-id="f9060-189">The image below shows the Geography dimension where the City, State-Province, Country and Postal Code dimension attributes have geography types associated with them.</span></span> <span data-ttu-id="f9060-190">這些是在表格式中繼資料中公開。</span><span class="sxs-lookup"><span data-stu-id="f9060-190">These are exposed in the tabular metadata.</span></span> <span data-ttu-id="f9060-191">Power View 會辨識中繼資料，讓使用者可以建立地圖視覺效果。</span><span class="sxs-lookup"><span data-stu-id="f9060-191">Power View recognizes the metadata enabling users to create map visualizations.</span></span> <span data-ttu-id="f9060-192">這是由 Power View 欄位清單中 Geography 資料表的 City、Country、Postal Code 和 State-Province 資料行旁邊的地圖圖示所表示。</span><span class="sxs-lookup"><span data-stu-id="f9060-192">This is indicated by the map icon next to the City, Country, Postal Code and State-Province columns in the Geography table in the Power View Field List.</span></span>  
  
 <span data-ttu-id="f9060-193">**SSDT 和 Power View 欄位清單中的維度屬性地理類型**</span><span class="sxs-lookup"><span data-stu-id="f9060-193">**Dimension attribute geography types in SSDT and Power View Field List**</span></span>  
  
 <span data-ttu-id="f9060-194">![維度屬性地理位置類型](../media/daxmd-ssdt-attribute-geog-types.gif "維度屬性地理位置類型")</span><span class="sxs-lookup"><span data-stu-id="f9060-194">![Dimension attribute geography types](../media/daxmd-ssdt-attribute-geog-types.gif "Dimension attribute geography types")</span></span>  
  
### <a name="dimension-calculated-members"></a><span data-ttu-id="f9060-195">維度導出成員</span><span class="sxs-lookup"><span data-stu-id="f9060-195">Dimension calculated members</span></span>  
 <span data-ttu-id="f9060-196">多維度模型支援含單一真實成員的 All 之子系導出成員。</span><span class="sxs-lookup"><span data-stu-id="f9060-196">Multidimensional models support calculated members for child of All with a single real member.</span></span> <span data-ttu-id="f9060-197">公開這類型的導出成員時，其他條件約束為：</span><span class="sxs-lookup"><span data-stu-id="f9060-197">Additional constraints while exposing this type of calculated member are:</span></span>  
  
-   <span data-ttu-id="f9060-198">當維度有一個以上的屬性時，必須是單一真實成員。</span><span class="sxs-lookup"><span data-stu-id="f9060-198">Must be a single real member when the dimension has more than one attribute.</span></span>  
  
-   <span data-ttu-id="f9060-199">包含導出成員的屬性不可以是維度的索引鍵屬性，除非它是唯一的屬性。</span><span class="sxs-lookup"><span data-stu-id="f9060-199">An attribute containing calculated members cannot be the key attribute of the dimension unless it is the only attribute.</span></span>  
  
-   <span data-ttu-id="f9060-200">包含導出成員的屬性不可以是父子式屬性。</span><span class="sxs-lookup"><span data-stu-id="f9060-200">An attribute containing calculated members cannot be a parent-child attribute.</span></span>  
  
 <span data-ttu-id="f9060-201">使用者階層的導出成員不會在 Power View 中公開，不過使用者仍然可以連接到包含使用者階層導出成員的 Cube。</span><span class="sxs-lookup"><span data-stu-id="f9060-201">Calculated members of user hierarchies are not exposed in Power View; however, end-users will still be able to connect to a cube containing calculated members on user hierarchies.</span></span>  
  
 <span data-ttu-id="f9060-202">下圖顯示的是 cube 的 Power View 報表，其中包含日期維度中維度屬性「會計日期計算」的時間智慧匯出成員。</span><span class="sxs-lookup"><span data-stu-id="f9060-202">The image below shows a Power View report for a cube that contains time-intelligence calculated members on dimension attribute "Fiscal Date Calculations" in the Date dimension.</span></span>  
  
 <span data-ttu-id="f9060-203">**含導出成員的 Power View 報表**</span><span class="sxs-lookup"><span data-stu-id="f9060-203">**Power View report with calculated members**</span></span>  
  
 <span data-ttu-id="f9060-204">![Power View 中的導出成員](../media/daxmd-calcmembersinpowerview.gif "Power View 中的導出成員")</span><span class="sxs-lookup"><span data-stu-id="f9060-204">![Calculated members in Power View](../media/daxmd-calcmembersinpowerview.gif "Calculated members in Power View")</span></span>  
  
### <a name="default-members"></a><span data-ttu-id="f9060-205">預設成員</span><span class="sxs-lookup"><span data-stu-id="f9060-205">Default members</span></span>  
 <span data-ttu-id="f9060-206">多維度模型支援維度屬性的預設成員。</span><span class="sxs-lookup"><span data-stu-id="f9060-206">Multidimensional models support default members for dimension attributes.</span></span> <span data-ttu-id="f9060-207">Analysis Services 彙總查詢資料時會使用預設成員。</span><span class="sxs-lookup"><span data-stu-id="f9060-207">The default member is used by Analysis Services when aggregating data for a query.</span></span> <span data-ttu-id="f9060-208">維度屬性的預設成員在表格式中繼資料中公開為對應資料行的預設值或篩選。</span><span class="sxs-lookup"><span data-stu-id="f9060-208">The default member of a dimension attribute is exposed as default value or filter for the corresponding column in the tabular metadata.</span></span>  
  
 <span data-ttu-id="f9060-209">套用屬性時，Power View 的行為模式與 Excel 樞紐分析表幾乎相同。</span><span class="sxs-lookup"><span data-stu-id="f9060-209">Power View behaves much the same as Excel PivotTables when attributes are applied.</span></span> <span data-ttu-id="f9060-210">當使用者將包含預設值的資料行加入至 Power View 視覺效果 (資料表、矩陣或圖表) 時，並不會套用預設值，而是會顯示所有可用值。</span><span class="sxs-lookup"><span data-stu-id="f9060-210">When a user adds a column to a Power View visualization (table, matrix, or chart) that contains a default value, the default value will not be applied and all available values are shown.</span></span> <span data-ttu-id="f9060-211">如果使用者將該資料行加入至 [篩選]，則會套用預設值。</span><span class="sxs-lookup"><span data-stu-id="f9060-211">If the user adds the column to Filters, the default value will be applied.</span></span>  
  
### <a name="dimension-security"></a><span data-ttu-id="f9060-212">維度安全性</span><span class="sxs-lookup"><span data-stu-id="f9060-212">Dimension security</span></span>  
 <span data-ttu-id="f9060-213">多維度模型透過角色支援維度和資料格層級安全性。</span><span class="sxs-lookup"><span data-stu-id="f9060-213">Multidimensional models support dimension and cell level security through roles.</span></span> <span data-ttu-id="f9060-214">透過使用 Power View 連接到 Cube 的使用者，會經過驗證並評估是否具備適當權限。</span><span class="sxs-lookup"><span data-stu-id="f9060-214">A user connecting to a cube by using Power View is authenticated and evaluated for appropriate permissions.</span></span> <span data-ttu-id="f9060-215">套用維度安全性時，使用者不會看到 Power View 中的個別維度成員，不過如果使用者的資料格層級安全性已定義為限制某些資料格，該使用者就無法透過 Power View 連接到 Cube。</span><span class="sxs-lookup"><span data-stu-id="f9060-215">When dimension security is applied, the respective dimension members will not be seen by the user in Power View; however if a user has a cell security permission defined where certain cells are restricted, then that user cannot connect to the cube with Power View.</span></span> <span data-ttu-id="f9060-216">在某些情況下，當該資料的部分是從安全資料計算出來時，使用者可以看到彙總資料。</span><span class="sxs-lookup"><span data-stu-id="f9060-216">In some cases, users can see aggregate data when portions of that data are calculated from secured data.</span></span>  
  
### <a name="non-aggregatable-attributeshierarchies"></a><span data-ttu-id="f9060-217">非彙總屬性/階層</span><span class="sxs-lookup"><span data-stu-id="f9060-217">Non-aggregatable attributes/hierarchies</span></span>  
 <span data-ttu-id="f9060-218">在多維度模型中，維度屬性 (Attribute) 的 IsAggregatable 屬性 (Property) 可設定為 false。</span><span class="sxs-lookup"><span data-stu-id="f9060-218">In a multidimensional model, attributes of a dimension can have the IsAggregatable property set to false.</span></span> <span data-ttu-id="f9060-219">這表示，模型作者已經指定用戶端應用程式在查詢資料時不應該跨階層 (屬性或多層級) 彙總資料。</span><span class="sxs-lookup"><span data-stu-id="f9060-219">This means the model author has specified client applications should not aggregate the data across hierarchies (attribute or multi-level) when they query the data.</span></span> <span data-ttu-id="f9060-220">在 Power View 中，此維度屬性是公開為沒有小計的資料行。</span><span class="sxs-lookup"><span data-stu-id="f9060-220">In Power View, this dimension attribute is exposed as a column for which sub-totals are not available.</span></span> <span data-ttu-id="f9060-221">在下圖，您可以看到非彙總階層範例：Accounts。</span><span class="sxs-lookup"><span data-stu-id="f9060-221">In the image below, you can see an example of a non-aggregatable hierarchy: Accounts.</span></span> <span data-ttu-id="f9060-222">Accounts 父子式階層的最頂層為非彙總，其他層級為可彙總的。</span><span class="sxs-lookup"><span data-stu-id="f9060-222">The top-most level of the Accounts parent-child hierarchy is non-aggregatable while other levels are aggregatable.</span></span> <span data-ttu-id="f9060-223">在 Accounts 階層的矩陣視覺效果 (前兩個層級) 中，您可以看到 Account Level 02 的小計，但是最頂層 Account Level 01 則沒有小計。</span><span class="sxs-lookup"><span data-stu-id="f9060-223">In a matrix visualization of the Accounts hierarchy (first two levels), you see sub-totals for Account Level 02 but not for the top-most level, Account Level 01.</span></span>  
  
 <span data-ttu-id="f9060-224">**Power View 中的非彙總階層**</span><span class="sxs-lookup"><span data-stu-id="f9060-224">**Non-aggregatable hierarchy in Power View**</span></span>  
  
 <span data-ttu-id="f9060-225">![Power View 中的非彙總階層](../media/daxmd-nonaggrattrib.gif "Power View 中的非彙總階層")</span><span class="sxs-lookup"><span data-stu-id="f9060-225">![Non-aggregatable hierarchy in Power View](../media/daxmd-nonaggrattrib.gif "Non-aggregatable hierarchy in Power View")</span></span>  
  
## <a name="images"></a><span data-ttu-id="f9060-226">影像</span><span class="sxs-lookup"><span data-stu-id="f9060-226">Images</span></span>  
 <span data-ttu-id="f9060-227">Power View 提供呈現影像的能力。</span><span class="sxs-lookup"><span data-stu-id="f9060-227">Power View provides the ability to render images.</span></span> <span data-ttu-id="f9060-228">在多維度模型中，提供影像給 Power View 的方法之一是公開包含影像 URL (統一資源定位器) 的資料行。</span><span class="sxs-lookup"><span data-stu-id="f9060-228">In multidimensional models, one of the ways you can provide images to Power View is to expose columns containing URLs (Uniform Resource Locator) of the images.</span></span> <span data-ttu-id="f9060-229">在此版本中，Analysis Services 支援維度屬性切換為 ImageURL 類型。</span><span class="sxs-lookup"><span data-stu-id="f9060-229">With this release, Analysis Services supports tagging dimension attributes as type ImageURL.</span></span> <span data-ttu-id="f9060-230">然後在表格式中繼資料中，提供此資料類型給 Power View。</span><span class="sxs-lookup"><span data-stu-id="f9060-230">This data type is then provided to Power View in the tabular metadata.</span></span> <span data-ttu-id="f9060-231">Power View 然後會下載 URL 中指定的影像，並在視覺效果中顯示影像。</span><span class="sxs-lookup"><span data-stu-id="f9060-231">Power View can then download and display the images specified in the URLs within visualizations.</span></span>  
  
 <span data-ttu-id="f9060-232">**SSDT 中的 ImageURL 維度屬性類型**</span><span class="sxs-lookup"><span data-stu-id="f9060-232">**ImageURL dimension attribute type in SSDT**</span></span>  
  
 <span data-ttu-id="f9060-233">![維度屬性內容](../media/daxmd-dimattribute-properties.gif "維度屬性內容")</span><span class="sxs-lookup"><span data-stu-id="f9060-233">![Dimension attribute properties](../media/daxmd-dimattribute-properties.gif "Dimension attribute properties")</span></span>  
  
## <a name="parent-child-hierarchies"></a><span data-ttu-id="f9060-234">父子式階層</span><span class="sxs-lookup"><span data-stu-id="f9060-234">Parent-child hierarchies</span></span>  
 <span data-ttu-id="f9060-235">多維度模型支援父子式階層，父子式階層在表格式中繼資料中公開為階層。</span><span class="sxs-lookup"><span data-stu-id="f9060-235">Multidimensional models support parent-child hierarchies, which are exposed as a hierarchy in the tabular metadata.</span></span> <span data-ttu-id="f9060-236">父子式階層的每個層級會公開為隱藏的資料行。</span><span class="sxs-lookup"><span data-stu-id="f9060-236">Each level of the parent-child hierarchy is exposed as a hidden column.</span></span> <span data-ttu-id="f9060-237">父子式維度的索引鍵屬性不會在表格式中繼資料中公開。</span><span class="sxs-lookup"><span data-stu-id="f9060-237">The key attribute of the parent-child dimension is not exposed in the tabular metadata.</span></span>  
  
 <span data-ttu-id="f9060-238">**Power View 中的父子式階層**</span><span class="sxs-lookup"><span data-stu-id="f9060-238">**Parent-child hierarchies in Power View**</span></span>  
  
 <span data-ttu-id="f9060-239">![父子式階層](../media/daxmd-ssdt-hierarchies.gif "父子式階層")</span><span class="sxs-lookup"><span data-stu-id="f9060-239">![Parent-child hierarchies](../media/daxmd-ssdt-hierarchies.gif "Parent-child hierarchies")</span></span>  
  
## <a name="perspectives-and-translations"></a><span data-ttu-id="f9060-240">檢視方塊和翻譯</span><span class="sxs-lookup"><span data-stu-id="f9060-240">Perspectives and translations</span></span>  
 <span data-ttu-id="f9060-241">檢視方塊是在用戶端工具中只看到某些維度或量值群組的 Cube 檢視。</span><span class="sxs-lookup"><span data-stu-id="f9060-241">Perspectives are views of cubes where only certain dimensions or measure groups are visible in client tools.</span></span> <span data-ttu-id="f9060-242">您可以將檢視方塊名稱指定為 Cube 連接字串屬性的值。</span><span class="sxs-lookup"><span data-stu-id="f9060-242">You can specify a perspective name as a value to the Cube connection string property.</span></span> <span data-ttu-id="f9060-243">例如，在下列連接字串中，「Direct Sales」是多維度模型中的一個觀點：</span><span class="sxs-lookup"><span data-stu-id="f9060-243">For example, in the following connection string, 'Direct Sales' is a perspective in the multidimensional model:</span></span>  
  
 `Data Source=localost;Initial Catalog=AdventureWorksDW-MD;Cube='Direct Sales'`  
  
 <span data-ttu-id="f9060-244">模型中，可以指定各種語言的 Cube 中繼資料和資料翻譯。</span><span class="sxs-lookup"><span data-stu-id="f9060-244">Cubes can have metadata and data translations specified for various Languages within the model.</span></span> <span data-ttu-id="f9060-245">若要查看翻譯 (的資料和中繼資料) 您必須將選擇性的 [地區設定識別碼] 屬性加入至 .RSDS 檔案中的連接字串，如下所示。</span><span class="sxs-lookup"><span data-stu-id="f9060-245">In order to see the translations (data and metadata) you need to add the optional "Locale Identifier" property to the connection string in the RSDS file as shown below.</span></span>  
  
 `Data Source=localost;Initial Catalog=AdventureWorksDW-MD;Cube='Adventure Works'; Locale Identifier=3084`  
  
 <span data-ttu-id="f9060-246">當 Power View 連接到 .rsds 檔案中有 Locale Identifier 屬性的多維度模型時，而且對應翻譯已包含在 Cube 時，使用者就會在 Power View 中看到翻譯。</span><span class="sxs-lookup"><span data-stu-id="f9060-246">When Power View connects to a multidimensional model with an .rsds file that has a Locale Identifier, and if a corresponding translation is contained in the cube, users will see the translations in Power View.</span></span>  
  
 <span data-ttu-id="f9060-247">如需詳細資訊，請參閱 [建立報表資料來源](create-a-report-data-source.md)。</span><span class="sxs-lookup"><span data-stu-id="f9060-247">For more information, see [Create a Report Data Source](create-a-report-data-source.md).</span></span>  
  
## <a name="power-view-pinned-filters"></a><span data-ttu-id="f9060-248">Power View 固定的篩選</span><span class="sxs-lookup"><span data-stu-id="f9060-248">Power View pinned filters</span></span>  
 <span data-ttu-id="f9060-249">Power View 報表可以包含多個檢視。</span><span class="sxs-lookup"><span data-stu-id="f9060-249">Power View reports can contain multiple views.</span></span> <span data-ttu-id="f9060-250">在此版本中，適用於表格式和多維度模型的「固定篩選」\*\* 功能，提供了建立套用到報表中所有檢視之篩選的功能。</span><span class="sxs-lookup"><span data-stu-id="f9060-250">With this release, the *Pin Filter* feature for both tabular and multidimensional models provides the ability to create filters that apply across all views in a report.</span></span> <span data-ttu-id="f9060-251">下圖顯示檢視篩選的 [固定篩選] 切換按鈕。</span><span class="sxs-lookup"><span data-stu-id="f9060-251">The image below shows the Pin filter toggle button for a view filter.</span></span> <span data-ttu-id="f9060-252">根據預設，檢視篩選為取消固定，只套用到該檢視。</span><span class="sxs-lookup"><span data-stu-id="f9060-252">By default, a view filter is unpinned and applies only to that view.</span></span> <span data-ttu-id="f9060-253">固定檢視篩選，會將篩選套用到所有檢視，取消固定篩選則會從其他檢視移除篩選。</span><span class="sxs-lookup"><span data-stu-id="f9060-253">Pinning a view filter applies it to all views; unpinning it removes it from other views.</span></span>  
  
 <span data-ttu-id="f9060-254">**固定的篩選**</span><span class="sxs-lookup"><span data-stu-id="f9060-254">**Pinned Filters**</span></span>  
  
 <span data-ttu-id="f9060-255">![固定的篩選](../media/daxmd-pinnedfilterinpowerview.gif "固定的篩選")</span><span class="sxs-lookup"><span data-stu-id="f9060-255">![Pinned Filter](../media/daxmd-pinnedfilterinpowerview.gif "Pinned Filter")</span></span>  
  
## <a name="unsupported-features"></a><span data-ttu-id="f9060-256">不支援的功能</span><span class="sxs-lookup"><span data-stu-id="f9060-256">Unsupported features</span></span>  
 <span data-ttu-id="f9060-257">**Excel 2013 中的 Power View** -不支援連接到多維度模型並建立報表。</span><span class="sxs-lookup"><span data-stu-id="f9060-257">**Power View in Excel 2013** - does not support connecting to and creating reports for multidimensional models.</span></span> <span data-ttu-id="f9060-258">多維度模型的 Power View 只支援以瀏覽器為基礎的 Power View 用戶端。</span><span class="sxs-lookup"><span data-stu-id="f9060-258">Power View for multidimensional models supports browser based Power View clients only.</span></span>  
  
 <span data-ttu-id="f9060-259">**動作** - 在 Power View 報表或多維度模型的 DAX 查詢中不支援此功能。</span><span class="sxs-lookup"><span data-stu-id="f9060-259">**Actions** - are not supported in Power View reports or in DAX queries against a multidimensional model.</span></span>  
  
 <span data-ttu-id="f9060-260">**命名集** - 在 Power View 報表或多維度模型的 DAX 查詢中不支援在多維度模型中使用命名集。</span><span class="sxs-lookup"><span data-stu-id="f9060-260">**Named sets** - in multidimensional models, are not supported in Power View or in DAX queries against a multidimensional model.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f9060-261">不支援的動作和命名集不會妨礙使用者使用 Power View 連接到多維度模型以及探索多維度模型。</span><span class="sxs-lookup"><span data-stu-id="f9060-261">Unsupported Actions and Named sets do not prevent users from connecting to and exploring multidimensional models using Power View.</span></span>  
  
 <span data-ttu-id="f9060-262">資料**格層級安全性**-在 Power View 報表中不受支援。</span><span class="sxs-lookup"><span data-stu-id="f9060-262">**Cell level security** - is not supported in Power View reports.</span></span>  
  
## <a name="csdlbi-annotations"></a><span data-ttu-id="f9060-263">CSDLBI 註解</span><span class="sxs-lookup"><span data-stu-id="f9060-263">CSDLBI Annotations</span></span>  
 <span data-ttu-id="f9060-264">多維度 Cube 中繼資料是由概念結構定義語言商業智慧註解 (CSDLBI) 公開為實體資料模型 (EDM) 概念模型。</span><span class="sxs-lookup"><span data-stu-id="f9060-264">Multidimensional cube metadata is exposed as an Entity Data Model (EDM) based conceptual model by Conceptual Schema Definition Language with Business Intelligence annotations (CSDLBI).</span></span>  
  
 <span data-ttu-id="f9060-265">當 DISCOVER_CSDL_METADATA 要求傳送至 Analysis Services 執行個體時，多維度中繼資料會表示為 CSDLBI 文件 (或 CSDL 輸出) 的表格式模型命名空間。</span><span class="sxs-lookup"><span data-stu-id="f9060-265">Multidimensional metadata is represented as a tabular model namespace in a CSDLBI document, or CSDL out, when a DISCOVER_CSDL_METADATA request is sent to the Analysis Services instance.</span></span>  
  
 <span data-ttu-id="f9060-266">**範例 DISCOVER_CSDL_METADATA 要求**</span><span class="sxs-lookup"><span data-stu-id="f9060-266">**Sample DISCOVER_CSDL_METADATA request**</span></span>  
  
```  
<Envelopexmlns="http://schemas.xmlsoap.org/soap/envelope/">  
   <Body>  
      <Discoverxmlns="urn:schemas-microsoft-com:xml-analysis">  
         <RequestType>DISCOVER_CSDL_METADATA</RequestType>  
         <Restrictions>  
            <RestrictionList>  
              <CATALOG_NAME>"catalogname"<CATALOG_NAME>  
            </RestrictionList>  
         </Restrictions>  
         <Properties>  
            <PropertyList>  
            </PropertyList>  
         </Properties>  
      </Discover>  
   </Body>  
</Envelope>  
  
```  
  
 <span data-ttu-id="f9060-267">DISCOVER_CSDL_METADATA 要求具有下列限制：</span><span class="sxs-lookup"><span data-stu-id="f9060-267">DISCOVER_CSDL_METADATA request has the following restrictions:</span></span>  
  
|<span data-ttu-id="f9060-268">名稱</span><span class="sxs-lookup"><span data-stu-id="f9060-268">Name</span></span>|<span data-ttu-id="f9060-269">必要</span><span class="sxs-lookup"><span data-stu-id="f9060-269">Required</span></span>|<span data-ttu-id="f9060-270">描述</span><span class="sxs-lookup"><span data-stu-id="f9060-270">Description</span></span>|  
|----------|--------------|-----------------|  
|<span data-ttu-id="f9060-271">CATALOG_NAME</span><span class="sxs-lookup"><span data-stu-id="f9060-271">CATALOG_NAME</span></span>|<span data-ttu-id="f9060-272">是</span><span class="sxs-lookup"><span data-stu-id="f9060-272">Yes</span></span>|<span data-ttu-id="f9060-273">目錄\資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="f9060-273">The catalog\database name.</span></span>|  
|<span data-ttu-id="f9060-274">PERSPECTIVE_NAME</span><span class="sxs-lookup"><span data-stu-id="f9060-274">PERSPECTIVE_NAME</span></span>|<span data-ttu-id="f9060-275">是，如果 Cube 包含一個以上的檢視方塊。</span><span class="sxs-lookup"><span data-stu-id="f9060-275">Yes, if the cube contains more than one perspective.</span></span> <span data-ttu-id="f9060-276">如果只有一個 Cube 或有預設檢視方塊，則為選擇性。</span><span class="sxs-lookup"><span data-stu-id="f9060-276">Optional if there is only one cube or there is a default perspective.</span></span>|<span data-ttu-id="f9060-277">多維度資料庫中的 Cube 名稱或檢視方塊名稱。</span><span class="sxs-lookup"><span data-stu-id="f9060-277">The cube name or perspective name in the multidimensional database.</span></span>|  
|<span data-ttu-id="f9060-278">VERSION</span><span class="sxs-lookup"><span data-stu-id="f9060-278">VERSION</span></span>|<span data-ttu-id="f9060-279">是</span><span class="sxs-lookup"><span data-stu-id="f9060-279">Yes</span></span>|<span data-ttu-id="f9060-280">用戶端要求的 CSDL 版本。</span><span class="sxs-lookup"><span data-stu-id="f9060-280">CSDL version requested by client.</span></span> <span data-ttu-id="f9060-281">2.0 版中支援多維度功能和建構。</span><span class="sxs-lookup"><span data-stu-id="f9060-281">Multidimensional features and constructs are supported in version 2.0.</span></span>|  
  
 <span data-ttu-id="f9060-282">傳回的 CSDL 輸出文件將模型表示為命名空間，其中包含實體、關聯和屬性。</span><span class="sxs-lookup"><span data-stu-id="f9060-282">The return CSDL out document represents the model as a namespace, containing entities, associations, and properties.</span></span>  
  
 <span data-ttu-id="f9060-283">如需表格式模型 CSDLBI 註解的詳細資訊，請參閱 MSDN 上的 [Technical Reference for BI Annotations to CSDL](/analysis-services/csdlbi/technical-reference-for-bi-annotations-to-csdl) (CSDL 的商業智慧註解技術參考) 和 [\[MS-CSDLBI\]: Conceptual Schema Definitions File Format with Business Intelligence Annotations](https://msdn.microsoft.com/library/jj161299\(SQL.105\).aspx)([MS-CSDLBI]：搭配商業智慧註解的概念性結構描述定義檔案格式)。</span><span class="sxs-lookup"><span data-stu-id="f9060-283">For more detailed information about CSDLBI annotations for tabular models, see [Technical Reference for BI Annotations to CSDL](/analysis-services/csdlbi/technical-reference-for-bi-annotations-to-csdl) on MSDN, and [\[MS-CSDLBI\]: Conceptual Schema Definitions File Format with Business Intelligence Annotations](https://msdn.microsoft.com/library/jj161299\(SQL.105\).aspx).</span></span>  
  
## <a name="client-help-on-officecom"></a><span data-ttu-id="f9060-284">Office.com 上的用戶端說明</span><span class="sxs-lookup"><span data-stu-id="f9060-284">Client Help on Office.com</span></span>  
 <span data-ttu-id="f9060-285">Office.com 提供下列文章，協助使用者了解多維度模型物件如何出現在 Power View 中，以及如何建立範例報表：</span><span class="sxs-lookup"><span data-stu-id="f9060-285">The following articles are provided on Office.com to help users learn about how Multidimensional Model objects appear in Power View and how to create a sample report:</span></span>  
  
 [<span data-ttu-id="f9060-286">了解 Power View 中的多維度模型物件</span><span class="sxs-lookup"><span data-stu-id="f9060-286">Understanding Multidimensional Model Objects in Power View</span></span>](https://office.microsoft.com/excel-help/understanding-multidimensional-model-objects-in-power-view-HA104018589.aspx)  
  
 [<span data-ttu-id="f9060-287">使用 Power View 探索 Adventure Works 多維度模型</span><span class="sxs-lookup"><span data-stu-id="f9060-287">Explore the Adventure Works Multidimensional Model by using Power View</span></span>](https://office.microsoft.com/excel-help/explore-the-adventure-works-multidimensional-model-by-using-power-view-HA104046830.aspx)  
  
