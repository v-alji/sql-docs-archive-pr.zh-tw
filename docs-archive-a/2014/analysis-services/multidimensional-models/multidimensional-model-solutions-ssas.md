---
title: " (SSAS) 的多維度模型方案 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- objects [Analysis Services], defining objects
- multidimensional data [Analysis Services], designing objects
ms.assetid: fbc0698f-93d3-4292-86cd-afe3a2ec5b0a
author: minewiskan
ms.author: owend
ms.openlocfilehash: a4f18f192ae86035d88618b3f7e2767cef06c792
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598604"
---
# <a name="multidimensional-model-solutions-ssas"></a><span data-ttu-id="cb3e0-102">多維度模型方案 (SSAS)</span><span class="sxs-lookup"><span data-stu-id="cb3e0-102">Multidimensional Model Solutions (SSAS)</span></span>
    
## <a name="in-this-section"></a><span data-ttu-id="cb3e0-103">本節內容</span><span class="sxs-lookup"><span data-stu-id="cb3e0-103">In This Section</span></span>  
 <span data-ttu-id="cb3e0-104">下列主題提供有關設計 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 多維度資料庫物件的指引。</span><span class="sxs-lookup"><span data-stu-id="cb3e0-104">The following topics provide guidance on designing [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] multidimensional database objects.</span></span>  
  
 [<span data-ttu-id="cb3e0-105">多維度模型資料庫 &#40;SSAS&#41;</span><span class="sxs-lookup"><span data-stu-id="cb3e0-105">Multidimensional Model Databases &#40;SSAS&#41;</span></span>](multidimensional-model-databases-ssas.md)  
 <span data-ttu-id="cb3e0-106">描述如何定義 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 資料庫。</span><span class="sxs-lookup"><span data-stu-id="cb3e0-106">Describes how to define an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database.</span></span>  
  
 [<span data-ttu-id="cb3e0-107">&#40;SSAS 多維度&#41;支援的資料來源</span><span class="sxs-lookup"><span data-stu-id="cb3e0-107">Data Sources Supported &#40;SSAS Multidimensional&#41;</span></span>](supported-data-sources-ssas-multidimensional.md)  
 <span data-ttu-id="cb3e0-108">描述如何定義 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 資料來源物件。</span><span class="sxs-lookup"><span data-stu-id="cb3e0-108">Describes how to define [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] data source objects.</span></span>  
  
 [<span data-ttu-id="cb3e0-109">多維度模型中的資料來源檢視</span><span class="sxs-lookup"><span data-stu-id="cb3e0-109">Data Source Views in Multidimensional Models</span></span>](data-source-views-in-multidimensional-models.md)  
 <span data-ttu-id="cb3e0-110">描述如何設計 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 資料來源檢視。</span><span class="sxs-lookup"><span data-stu-id="cb3e0-110">Describes how to design [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] data source views.</span></span>  
  
 [<span data-ttu-id="cb3e0-111">多維度模型中的維度</span><span class="sxs-lookup"><span data-stu-id="cb3e0-111">Dimensions in Multidimensional Models</span></span>](dimensions-in-multidimensional-models.md)  
 <span data-ttu-id="cb3e0-112">描述如何設計 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 維度物件。</span><span class="sxs-lookup"><span data-stu-id="cb3e0-112">Describes how to design [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] dimension objects.</span></span>  
  
 [<span data-ttu-id="cb3e0-113">多維度模型中的 Cube</span><span class="sxs-lookup"><span data-stu-id="cb3e0-113">Cubes in Multidimensional Models</span></span>](cubes-in-multidimensional-models.md)  
 <span data-ttu-id="cb3e0-114">描述如何設計 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Cube 物件。</span><span class="sxs-lookup"><span data-stu-id="cb3e0-114">Describes how to design [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] cube objects.</span></span>  
  
 [<span data-ttu-id="cb3e0-115">結構描述產生精靈 &#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="cb3e0-115">Schema Generation Wizard &#40;Analysis Services&#41;</span></span>](schema-generation-wizard-analysis-services.md)  
 <span data-ttu-id="cb3e0-116">描述如何在無現有的關聯式結構描述之下來設計多維度資料庫物件。</span><span class="sxs-lookup"><span data-stu-id="cb3e0-116">Describes how to design multidimensional database objects without an existing relational schema.</span></span>  
  
 [<span data-ttu-id="cb3e0-117">Analysis Services 個人化延伸模組</span><span class="sxs-lookup"><span data-stu-id="cb3e0-117">Analysis Services Personalization Extensions</span></span>](extending-olap/analysis-services-personalization-extensions.md)  
 <span data-ttu-id="cb3e0-118">描述如何設計的個人化延伸模組 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="cb3e0-118">Describes how to design Personalization Extensions for [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span>  
  
  
