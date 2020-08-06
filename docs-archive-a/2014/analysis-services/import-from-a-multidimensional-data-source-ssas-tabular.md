---
title: 從多維度資料來源匯入 (SSAS 表格式) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 7f0793ea-a4c7-42e9-b722-2164a454ebca
author: minewiskan
ms.author: owend
ms.openlocfilehash: 0b26cc8ed7237f87fa5e23c6a2fd47e18de2c165
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606477"
---
# <a name="import-from-a-multidimensional-data-source-ssas-tabular"></a><span data-ttu-id="282fd-102">從多維度資料來源匯入 (SSAS 表格式)</span><span class="sxs-lookup"><span data-stu-id="282fd-102">Import from a Multidimensional Data Source (SSAS Tabular)</span></span>
  <span data-ttu-id="282fd-103">您可以使用 Analysis Services Cube 資料庫做為表格式模型的資料來源。</span><span class="sxs-lookup"><span data-stu-id="282fd-103">You can use an Analysis Services cube database as a data source for a tabular model.</span></span> <span data-ttu-id="282fd-104">您必須定義 MDX 查詢選取要匯入的資料，才可以從 Analysis Services Cube 匯入資料。</span><span class="sxs-lookup"><span data-stu-id="282fd-104">In order to import data from an Analysis Services cube, you must define an MDX Query to select data to import.</span></span>  
  
 <span data-ttu-id="282fd-105">包含在 SQL Server Analysis Services 資料庫中的任何資料，都可以匯入至模型中。</span><span class="sxs-lookup"><span data-stu-id="282fd-105">Any data that is contained in a SQL Server Analysis Services database can be imported into a model.</span></span> <span data-ttu-id="282fd-106">您可以擷取部分或全部的維度，或是從 Cube 取得配量和彙總，例如目前年度每個月的銷售總和等。但是請注意，您從 Cube 匯入的所有資料都會扁平化。</span><span class="sxs-lookup"><span data-stu-id="282fd-106">You can extract all or part of a dimension, or get slices and aggregates from the cube, such as the sum of sales, month by month, for the current year, etc. However, you should keep in mind all data that you import from a cube is flattened.</span></span> <span data-ttu-id="282fd-107">因此，如果您定義擷取量值及多維度的查詢，匯入資料的每個維度都會在個別的資料行中。</span><span class="sxs-lookup"><span data-stu-id="282fd-107">Therefore, if you define a query that retrieves measures along multiple dimensions, the data will be imported with each dimension in a separate column.</span></span>  
  
 <span data-ttu-id="282fd-108">Analysis Services Cube 必須是 SQL Server 2005、SQL Server 2008、SQL Server 2008 R2、 [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]或 [!INCLUDE[ssSQL14](../includes/sssql14-md.md)]版。</span><span class="sxs-lookup"><span data-stu-id="282fd-108">Analysis Services cubes must be version SQL Server 2005, SQL Server 2008, SQL Server 2008 R2, [!INCLUDE[ssSQL11](../includes/sssql11-md.md)], or [!INCLUDE[ssSQL14](../includes/sssql14-md.md)].</span></span>  
  
### <a name="to-import-data-from-an-analysis-services-cube"></a><span data-ttu-id="282fd-109">若要從 Analysis Services Cube 匯入資料</span><span class="sxs-lookup"><span data-stu-id="282fd-109">To import data from an Analysis Services cube</span></span>  
  
1.  <span data-ttu-id="282fd-110">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中，按一下 **[模型]** 功能表，然後按一下 **[從資料來源匯入]**。</span><span class="sxs-lookup"><span data-stu-id="282fd-110">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], click the **Model** menu, and then click **Import from Data Source**.</span></span>  
  
2.  <span data-ttu-id="282fd-111">在 **[連接到資料來源]** 頁面上，選取 **[Microsoft Analysis Services]**，然後按 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="282fd-111">On the **Connect to a Data Source** page, select **Microsoft Analysis Services**, and then click **Next**.</span></span>  
  
3.  <span data-ttu-id="282fd-112">請遵循 [資料表匯入精靈] 中的步驟來進行。</span><span class="sxs-lookup"><span data-stu-id="282fd-112">Follow the steps in the Table Import Wizard.</span></span> <span data-ttu-id="282fd-113">您將能夠在 **[指定 MDX 查詢]** 頁面上，指定 MDX 查詢。</span><span class="sxs-lookup"><span data-stu-id="282fd-113">You will be able to specify an MDX query on the **Specify a MDX Query** page.</span></span> <span data-ttu-id="282fd-114">若要使用 MDX 查詢設計工具，請在 [指定 MDX 查詢] 頁面上，按一下 **[設計]**。</span><span class="sxs-lookup"><span data-stu-id="282fd-114">To use the MDX Query Designer, on the Specify a MDX Query page, click **Design**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="282fd-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="282fd-115">See Also</span></span>  
 <span data-ttu-id="282fd-116">[將資料匯入 &#40;SSAS 表格式&#41;](import-data-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="282fd-116">[Import Data &#40;SSAS Tabular&#41;](import-data-ssas-tabular.md) </span></span>  
 [<span data-ttu-id="282fd-117">支援的資料來源 &#40;SSAS 表格式&#41;</span><span class="sxs-lookup"><span data-stu-id="282fd-117">Data Sources Supported &#40;SSAS Tabular&#41;</span></span>](tabular-models/data-sources-supported-ssas-tabular.md)  
  
  
