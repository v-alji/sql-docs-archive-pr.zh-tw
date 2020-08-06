---
title: " (SSAS 表格式) 的資料來源 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 6908998b-9302-4a90-976e-770106b48d18
author: minewiskan
ms.author: owend
ms.openlocfilehash: d686d8100e30d7608e8d90f135022bdf46785723
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87702109"
---
# <a name="data-sources-ssas-tabular"></a><span data-ttu-id="fe8b3-102">資料來源 (SSAS 表格式)</span><span class="sxs-lookup"><span data-stu-id="fe8b3-102">Data Sources (SSAS Tabular)</span></span>
  <span data-ttu-id="fe8b3-103">資料來源提供要包含在表格式模型方案中的資料。</span><span class="sxs-lookup"><span data-stu-id="fe8b3-103">Data sources provide the data to be included in a tabular model solution.</span></span> <span data-ttu-id="fe8b3-104">您可以從各種來源將資料匯入至模型中，例如關聯式資料庫、資料摘要、Analysis Services Cube 等多維度資料來源，以及 Microsoft Excel 活頁簿等文字檔。</span><span class="sxs-lookup"><span data-stu-id="fe8b3-104">You can import data into your model from a wide variety of sources such as relational databases, data feeds, multidimensional data sources such as an Analysis Services cube, and from text files such as a Microsoft Excel workbook.</span></span> <span data-ttu-id="fe8b3-105">本節中的主題提供下列詳細資訊：您可以匯入的資料來源類型、您可以匯入的各種資料類型，以及描述如何從這些來源匯入資料的工作。</span><span class="sxs-lookup"><span data-stu-id="fe8b3-105">Topics in this section provide information about the types of data sources you can import from, the various data types you can import, and tasks describing how to import data from those sources.</span></span>  
  
## <a name="related-topics-and-tasks"></a><span data-ttu-id="fe8b3-106">相關主題和工作</span><span class="sxs-lookup"><span data-stu-id="fe8b3-106">Related Topics and Tasks</span></span>  
  
|<span data-ttu-id="fe8b3-107">主題</span><span class="sxs-lookup"><span data-stu-id="fe8b3-107">Topic</span></span>|<span data-ttu-id="fe8b3-108">描述</span><span class="sxs-lookup"><span data-stu-id="fe8b3-108">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="fe8b3-109">支援的資料來源 &#40;SSAS 表格式&#41;</span><span class="sxs-lookup"><span data-stu-id="fe8b3-109">Data Sources Supported &#40;SSAS Tabular&#41;</span></span>](tabular-models/data-sources-supported-ssas-tabular.md)|<span data-ttu-id="fe8b3-110">本主題提供有關您可以匯入資料之不同資料來源的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="fe8b3-110">This topic provides information about the different data sources that you can import data from.</span></span>|  
|[<span data-ttu-id="fe8b3-111">支援的資料類型 &#40;SSAS 表格式&#41;</span><span class="sxs-lookup"><span data-stu-id="fe8b3-111">Data Types Supported &#40;SSAS Tabular&#41;</span></span>](tabular-models/data-types-supported-ssas-tabular.md)|<span data-ttu-id="fe8b3-112">本主題提供有關表格式模型支援之各種資料類型的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="fe8b3-112">This topic provides information about the various data types that are supported in a Tabular Model.</span></span>|  
|[<span data-ttu-id="fe8b3-113">模擬 &#40;SSAS 表格式&#41;</span><span class="sxs-lookup"><span data-stu-id="fe8b3-113">Impersonation &#40;SSAS Tabular&#41;</span></span>](tabular-models/impersonation-ssas-tabular.md)|<span data-ttu-id="fe8b3-114">本主題提供有關模擬的詳細資訊，模擬提供 Analysis Services 用來連接到資料來源，以匯入及重新整理資料的登入認證。</span><span class="sxs-lookup"><span data-stu-id="fe8b3-114">This topic provides information about impersonation, which provides logon credentials that are used by Analysis Services when connecting to a data source to import and refresh data.</span></span>|  
|[<span data-ttu-id="fe8b3-115">匯入資料 (SSAS 表格式)</span><span class="sxs-lookup"><span data-stu-id="fe8b3-115">Import Data &#40;SSAS Tabular&#41;</span></span>](import-data-ssas-tabular.md)|<span data-ttu-id="fe8b3-116">本節中的工作描述如何從不同的資料來源匯入資料。</span><span class="sxs-lookup"><span data-stu-id="fe8b3-116">Tasks in this section describe how to import data from different data sources.</span></span>|  
|[<span data-ttu-id="fe8b3-117">處理資料 &#40;SSAS 表格式&#41;</span><span class="sxs-lookup"><span data-stu-id="fe8b3-117">Process Data &#40;SSAS Tabular&#41;</span></span>](process-data-ssas-tabular.md)|<span data-ttu-id="fe8b3-118">本節中的工作描述如何處理 (重新整理) 或變更已匯入至模型中的資料。</span><span class="sxs-lookup"><span data-stu-id="fe8b3-118">Tasks in this section describe how to process (refresh) or change data that has already been imported into a model.</span></span>|  
|[<span data-ttu-id="fe8b3-119">編輯現有的資料來源連接 &#40;SSAS 表格式&#41;</span><span class="sxs-lookup"><span data-stu-id="fe8b3-119">Edit an Existing Data Source Connection &#40;SSAS Tabular&#41;</span></span>](edit-an-existing-data-source-connection-ssas-tabular.md)|<span data-ttu-id="fe8b3-120">描述如何編輯已建立而且用來從來源匯入資料的資料來源連接。</span><span class="sxs-lookup"><span data-stu-id="fe8b3-120">Describes how to edit a data source connection that has already been created and used to import data from a source.</span></span>|  
  
  
