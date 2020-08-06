---
title: 從 (SSAS 表格式) 的關聯式資料來源匯入 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 043201cc-fbef-4ed0-bde8-dc5e3a3e8bea
author: minewiskan
ms.author: owend
ms.openlocfilehash: 93bb9ba9ba8d40262e4e90e840dcd15ac6826df3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87605925"
---
# <a name="import-from-a-relational-data-source-ssas-tabular"></a><span data-ttu-id="49cf2-102">從關聯式資料來源匯入 (SSAS 表格式)</span><span class="sxs-lookup"><span data-stu-id="49cf2-102">Import from a Relational Data Source (SSAS Tabular)</span></span>
  <span data-ttu-id="49cf2-103">您可以使用 [資料表匯入精靈]，從各種關聯式資料庫匯入資料。</span><span class="sxs-lookup"><span data-stu-id="49cf2-103">You can import data from a variety of relational databases by using the Table Import Wizard.</span></span> <span data-ttu-id="49cf2-104">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]提供此精靈，位於 [模型] \*\*\*\* 功能表。</span><span class="sxs-lookup"><span data-stu-id="49cf2-104">The wizard is available in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], on the **Model** menu.</span></span> <span data-ttu-id="49cf2-105">若要連接至資料來源，您必須先在電腦上安裝適當的提供者。</span><span class="sxs-lookup"><span data-stu-id="49cf2-105">To connect to a data source, you must have the appropriate provider installed on your computer.</span></span> <span data-ttu-id="49cf2-106">如需支援的資料來源和提供者的詳細資訊，請參閱 [支援的資料來源 &#40;SSAS 表格式&#41;](tabular-models/data-sources-supported-ssas-tabular.md)(支援的資料來源 (SSAS 表格式))。</span><span class="sxs-lookup"><span data-stu-id="49cf2-106">For more information about supported data sources and providers, see [Data Sources Supported &#40;SSAS Tabular&#41;](tabular-models/data-sources-supported-ssas-tabular.md).</span></span>  
  
 <span data-ttu-id="49cf2-107">[資料表匯入精靈] 支援從下列資料來源匯入資料：</span><span class="sxs-lookup"><span data-stu-id="49cf2-107">The Table Import Wizard supports importing data from the following data sources:</span></span>  
  
 <span data-ttu-id="49cf2-108">**關係資料庫**</span><span class="sxs-lookup"><span data-stu-id="49cf2-108">**Relational Databases**</span></span>  
  
-   <span data-ttu-id="49cf2-109">Microsoft SQL Server 資料庫</span><span class="sxs-lookup"><span data-stu-id="49cf2-109">Microsoft SQL Server database</span></span>  
  
-   <span data-ttu-id="49cf2-110">Microsoft SQL Azure</span><span class="sxs-lookup"><span data-stu-id="49cf2-110">Microsoft SQL Azure</span></span>  
  
-   <span data-ttu-id="49cf2-111">Microsoft Access 資料庫</span><span class="sxs-lookup"><span data-stu-id="49cf2-111">Microsoft Access database</span></span>  
  
-   <span data-ttu-id="49cf2-112">Microsoft SQL Server Parallel Data Warehouse</span><span class="sxs-lookup"><span data-stu-id="49cf2-112">Microsoft SQL Server Parallel Data Warehouse</span></span>  
  
-   <span data-ttu-id="49cf2-113">Oracle</span><span class="sxs-lookup"><span data-stu-id="49cf2-113">Oracle</span></span>  
  
-   <span data-ttu-id="49cf2-114">Teradata</span><span class="sxs-lookup"><span data-stu-id="49cf2-114">Teradata</span></span>  
  
-   <span data-ttu-id="49cf2-115">Sybase</span><span class="sxs-lookup"><span data-stu-id="49cf2-115">Sybase</span></span>  
  
-   <span data-ttu-id="49cf2-116">Informix</span><span class="sxs-lookup"><span data-stu-id="49cf2-116">Informix</span></span>  
  
-   <span data-ttu-id="49cf2-117">IBM DB2</span><span class="sxs-lookup"><span data-stu-id="49cf2-117">IBM DB2</span></span>  
  
-   <span data-ttu-id="49cf2-118">OLE DB/ODBC</span><span class="sxs-lookup"><span data-stu-id="49cf2-118">OLE DB/ODBC</span></span>  
  
 <span data-ttu-id="49cf2-119">**多維度來源**</span><span class="sxs-lookup"><span data-stu-id="49cf2-119">**Multidimensional Sources**</span></span>  
  
-   <span data-ttu-id="49cf2-120">Microsoft SQL Server Analysis Services Cube</span><span class="sxs-lookup"><span data-stu-id="49cf2-120">Microsoft SQL Server Analysis Services cube</span></span>  
  
 <span data-ttu-id="49cf2-121">[資料表匯入精靈] 不支援從 [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] 活頁簿匯入資料做為資料來源。</span><span class="sxs-lookup"><span data-stu-id="49cf2-121">The Table Import Wizard does not support importing data from a [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] Workbook as a data source.</span></span>  
  
### <a name="to-import-data-from-a-database"></a><span data-ttu-id="49cf2-122">從資料庫匯入資料</span><span class="sxs-lookup"><span data-stu-id="49cf2-122">To import data from a database</span></span>  
  
1.  <span data-ttu-id="49cf2-123">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中，按一下 **[模型]** 功能表，然後按一下 **[從資料來源匯入]**。</span><span class="sxs-lookup"><span data-stu-id="49cf2-123">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], click the **Model** menu, and then click **Import from Data Source**.</span></span>  
  
2.  <span data-ttu-id="49cf2-124">在 **[連接到資料來源]** 頁面上，選取要連接的資料庫類型，然後按 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="49cf2-124">On the **Connect to a Data Source** page, select the type of database to connect to, and then click **Next**.</span></span>  
  
3.  <span data-ttu-id="49cf2-125">請遵循 [資料表匯入精靈] 中的步驟來進行。</span><span class="sxs-lookup"><span data-stu-id="49cf2-125">Follow the steps in the Table Import Wizard.</span></span> <span data-ttu-id="49cf2-126">在後續頁面中，您即可選取特定的資料表及檢視，或使用 **[選取資料表和檢視表]** 頁面，或在 **[指定 SQL 查詢]** 頁面上建立 SQL 查詢，以套用篩選。</span><span class="sxs-lookup"><span data-stu-id="49cf2-126">On subsequent pages, you will be able to select specific tables and views or apply filters by using the **Select Tables and Views** page or by creating a SQL query on **Specify a SQL Query** page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49cf2-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="49cf2-127">See Also</span></span>  
 <span data-ttu-id="49cf2-128">[將資料匯入 &#40;SSAS 表格式&#41;](import-data-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="49cf2-128">[Import Data &#40;SSAS Tabular&#41;](import-data-ssas-tabular.md) </span></span>  
 [<span data-ttu-id="49cf2-129">支援的資料來源 &#40;SSAS 表格式&#41;</span><span class="sxs-lookup"><span data-stu-id="49cf2-129">Data Sources Supported &#40;SSAS Tabular&#41;</span></span>](tabular-models/data-sources-supported-ssas-tabular.md)  
  
  
