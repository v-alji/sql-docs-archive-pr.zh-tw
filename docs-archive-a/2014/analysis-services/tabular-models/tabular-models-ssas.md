---
title: " (SSAS 表格式) 的表格式模型 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 80027288-c203-4667-a3e1-40fa572b4975
author: minewiskan
ms.author: owend
ms.openlocfilehash: 44f358f0f36e84ad903a0a4fcb0203291019e7aa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593611"
---
# <a name="tabular-modeling-ssas-tabular"></a><span data-ttu-id="8889c-102">表格式模型化 (SSAS 表格式)</span><span class="sxs-lookup"><span data-stu-id="8889c-102">Tabular Modeling (SSAS Tabular)</span></span>
  <span data-ttu-id="8889c-103">表格式模型是 Analysis Services 的記憶體中資料庫。</span><span class="sxs-lookup"><span data-stu-id="8889c-103">Tabular models are in-memory databases in Analysis Services.</span></span> <span data-ttu-id="8889c-104">xVelocity 記憶體中分析引擎 (VertiPaq) 採用最先進的壓縮演算法和多執行緒查詢處理器，可透過 Microsoft Excel 和 Microsoft [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] 等報表用戶端應用程式快速存取表格式模型物件和資料。</span><span class="sxs-lookup"><span data-stu-id="8889c-104">Using state-of-the-art compression algorithms and multi-threaded query processor, the xVelocity in-memory analytics engine (VertiPaq) delivers fast access to tabular model objects and data by reporting client applications such as Microsoft Excel and Microsoft [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)].</span></span>  
  
 <span data-ttu-id="8889c-105">表格式模型支援兩種模式的資料存取：快取模式和 DirectQuery 模式。</span><span class="sxs-lookup"><span data-stu-id="8889c-105">Tabular models support data access through two modes: Cached mode and DirectQuery mode.</span></span> <span data-ttu-id="8889c-106">在快取模式中，您可以整合來自多個來源的資料，包括關聯式資料庫、資料摘要及一般文字檔。</span><span class="sxs-lookup"><span data-stu-id="8889c-106">In cached mode, you can integrate data from multiple sources including relational databases, data feeds, and flat text files.</span></span> <span data-ttu-id="8889c-107">在 DirectQuery 模式，您可以略過記憶體中模型，讓用戶端應用程式可以直接在 (SQL Server 關聯式) 來源中查詢資料。</span><span class="sxs-lookup"><span data-stu-id="8889c-107">In DirectQuery mode, you can bypass the in-memory model, allowing client applications to query data directly at the (SQL Server relational) source.</span></span>  
  
 <span data-ttu-id="8889c-108">您可以使用新的表格式模型專案範本，在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 中撰寫表格式模型。</span><span class="sxs-lookup"><span data-stu-id="8889c-108">Tabular models are authored in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] using new tabular model project templates.</span></span> <span data-ttu-id="8889c-109">您可以從多個來源匯入資料，然後透過加入關聯性、導出資料行、量值、KPI 及階層，來充實模型。</span><span class="sxs-lookup"><span data-stu-id="8889c-109">You can import data from multiple sources, and then enrich the model by adding relationships, calculated columns, measures, KPIs, and hierarchies.</span></span> <span data-ttu-id="8889c-110">接著可將模型部署至 Analysis Services 的執行個體，再由其中的用戶端報表應用程式連接至模型。</span><span class="sxs-lookup"><span data-stu-id="8889c-110">Models can then be deployed to an instance of Analysis Services where client reporting applications can connect to them.</span></span> <span data-ttu-id="8889c-111">您可以在 SQL Server Management Studio 中管理已部署的模型，就像是管理多維度模型一樣。</span><span class="sxs-lookup"><span data-stu-id="8889c-111">Deployed models can be managed in SQL Server Management Studio just like multidimensional models.</span></span> <span data-ttu-id="8889c-112">您也可以對其進行資料分割以最佳化處理，並使用以角色為基礎的安全性提供資料列層級的安全性。</span><span class="sxs-lookup"><span data-stu-id="8889c-112">They can also be partitioned for optimized processing and secured to the row-level by using role based security.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8889c-113">本節內容</span><span class="sxs-lookup"><span data-stu-id="8889c-113">In This Section</span></span>  
 [<span data-ttu-id="8889c-114">表格式模型方案 &#40;SSAS 表格式&#41;</span><span class="sxs-lookup"><span data-stu-id="8889c-114">Tabular Model Solutions &#40;SSAS Tabular&#41;</span></span>](../tabular-model-solutions-ssas-tabular.md)  
  
 [<span data-ttu-id="8889c-115">表格式模型資料庫 &#40;SSAS 表格式&#41;</span><span class="sxs-lookup"><span data-stu-id="8889c-115">Tabular Model Databases &#40;SSAS Tabular&#41;</span></span>](tabular-model-databases-ssas-tabular.md)  
  
 [<span data-ttu-id="8889c-116">表格式模型資料存取</span><span class="sxs-lookup"><span data-stu-id="8889c-116">Tabular Model Data Access</span></span>](tabular-model-data-access.md)  
  
  
