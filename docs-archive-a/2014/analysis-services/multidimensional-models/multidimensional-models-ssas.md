---
title: " (SSAS) 的多維度模型 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 509df042-fdb3-4e2c-a6b8-86943ce1b0fc
author: minewiskan
ms.author: owend
ms.openlocfilehash: 7348a932eccb62f2e00c0b154ca9efc8086fcd1f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710930"
---
# <a name="multidimensional-modeling-ssas"></a><span data-ttu-id="8b113-102">多維度模型化 (SSAS)</span><span class="sxs-lookup"><span data-stu-id="8b113-102">Multidimensional Modeling (SSAS)</span></span>
  <span data-ttu-id="8b113-103">Analysis Services 多維度方案會使用 Cube 結構來分析跨多個維度的商務資料。</span><span class="sxs-lookup"><span data-stu-id="8b113-103">An Analysis Services multidimensional solution uses cube structures for analyzing business data across multiple dimensions.</span></span> <span data-ttu-id="8b113-104">多維度模式為 Analysis Services 的預設伺服器模式。</span><span class="sxs-lookup"><span data-stu-id="8b113-104">Multidimensional mode is the default server mode of Analysis Services.</span></span> <span data-ttu-id="8b113-105">它包含 OLAP 資料查詢及計算引擎，其 MOLAP、ROLAP 和 HOLAP 儲存模式可平衡效能與可擴充的資料需求。</span><span class="sxs-lookup"><span data-stu-id="8b113-105">It includes a query and calculation engine for OLAP data, with MOLAP, ROLAP, and HOLAP storage modes to balance performance with scalable data requirements.</span></span> <span data-ttu-id="8b113-106">Analysis Services OLAP 引擎是領先業界的 OLAP 伺服器，可與眾多 BI 工具搭配使用。</span><span class="sxs-lookup"><span data-stu-id="8b113-106">The Analysis Services OLAP engine is an industry leading OLAP server that works well with a broad range of BI tools.</span></span> <span data-ttu-id="8b113-107">大部分 Analysis Services 部署都是安裝為傳統 OLAP 伺服器。</span><span class="sxs-lookup"><span data-stu-id="8b113-107">Most Analysis Services deployments are installed as classic OLAP servers.</span></span>  
  
## <a name="benefits-of-using-multidimensional-solutions"></a><span data-ttu-id="8b113-108">使用多維度方案的優點</span><span class="sxs-lookup"><span data-stu-id="8b113-108">Benefits of Using Multidimensional Solutions</span></span>  
 <span data-ttu-id="8b113-109">建置 Analysis Services 多維度模型的主要原因是要達到針對商務資料進行隨選查詢的快速效能。</span><span class="sxs-lookup"><span data-stu-id="8b113-109">The primary reason for building an Analysis Services multidimensional model is to achieve fast performance of ad hoc queries against business data.</span></span> <span data-ttu-id="8b113-110">多維度模型是由 Cube 和維度組成，這些 Cube 和維度可加上註解並擴充以支援複雜查詢建構。</span><span class="sxs-lookup"><span data-stu-id="8b113-110">A multidimensional model is composed of cubes and dimensions that can be annotated and extended to support complex query constructions.</span></span> <span data-ttu-id="8b113-111">BI 開發人員會建立 Cube 以支援快速回應時間，以及提供商務報表的單一資料來源。</span><span class="sxs-lookup"><span data-stu-id="8b113-111">BI developers create cubes to support fast response times, and to provide a single data source for business reporting.</span></span> <span data-ttu-id="8b113-112">鑑於商業智慧的重要性在組織的所有層級之間逐漸提高，因此擁有分析資料的單一來源可確保不一致的情形保持在最低限度 (如果沒有完全刪除的話)。</span><span class="sxs-lookup"><span data-stu-id="8b113-112">Given the growing importance of business intelligence across all levels of an organization, having a single source of analytical data ensures that discrepancies are kept to a minimum, if not eliminated entirely.</span></span>  
  
 <span data-ttu-id="8b113-113">使用 Analysis Services 多維度資料庫的另一項重要優點是能夠與常用的 BI 報表工具整合，例如 Excel、Reporting Services 和 PerformancePoint，以及自訂應用程式和協力廠商解決方案。</span><span class="sxs-lookup"><span data-stu-id="8b113-113">Another important benefit to using Analysis Services multidimensional databases is integration with commonly used BI reporting tools such as Excel, Reporting Services, and PerformancePoint, as well as custom applications and third-party solutions.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8b113-114">本節內容</span><span class="sxs-lookup"><span data-stu-id="8b113-114">In This Section</span></span>  
 [<span data-ttu-id="8b113-115">多維度模型方案 &#40;SSAS&#41;</span><span class="sxs-lookup"><span data-stu-id="8b113-115">Multidimensional Model Solutions &#40;SSAS&#41;</span></span>](multidimensional-model-solutions-ssas.md)  
  
 [<span data-ttu-id="8b113-116">多維度模型資料庫 &#40;SSAS&#41;</span><span class="sxs-lookup"><span data-stu-id="8b113-116">Multidimensional Model Databases &#40;SSAS&#41;</span></span>](multidimensional-model-databases-ssas.md)  
  
 [<span data-ttu-id="8b113-117">多維度模型物件處理</span><span class="sxs-lookup"><span data-stu-id="8b113-117">Multidimensional Model Object Processing</span></span>](processing-a-multidimensional-model-analysis-services.md)  
  
 [<span data-ttu-id="8b113-118">角色與權限 &#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="8b113-118">Roles and Permissions &#40;Analysis Services&#41;</span></span>](roles-and-permissions-analysis-services.md)  
  
 [<span data-ttu-id="8b113-119">多維度模型的 Power View</span><span class="sxs-lookup"><span data-stu-id="8b113-119">Power View for Multidimensional Models</span></span>](power-view-for-multidimensional-models.md)  
  
 [<span data-ttu-id="8b113-120">多維度模型組件管理</span><span class="sxs-lookup"><span data-stu-id="8b113-120">Multidimensional Model Assemblies Management</span></span>](multidimensional-model-assemblies-management.md)  
  
  
