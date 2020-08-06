---
title: 透過個人化擴充 OLAP |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- Analysis Services, extensibility
ms.assetid: 348e49fc-4390-43c1-9b6c-61b386ff4373
author: minewiskan
ms.author: owend
ms.openlocfilehash: 93669980e989b1cb11673f45c111de3609bbe920
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708754"
---
# <a name="extending-olap-through-personalizations"></a><span data-ttu-id="05367-102">通過個人化擴充 OLAP</span><span class="sxs-lookup"><span data-stu-id="05367-102">Extending OLAP through personalizations</span></span>
  <span data-ttu-id="05367-103">Microsoft [!INCLUDE[ssASCurrent](../../../includes/ssascurrent-md.md)] 提供許多的內建函數，可搭配多維度運算式 (MDX) 和資料採礦延伸模組 (DMX) 語言使用。</span><span class="sxs-lookup"><span data-stu-id="05367-103">Microsoft  [!INCLUDE[ssASCurrent](../../../includes/ssascurrent-md.md)] supplies many intrinsic functions for use with the Multidimensional Expressions (MDX) and Data Mining Extensions (DMX) languages.</span></span> <span data-ttu-id="05367-104">這些函數是設計用來進行標準統計計算與階層中周遊成員間等工作。</span><span class="sxs-lookup"><span data-stu-id="05367-104">These functions are designed to accomplish everything from standard statistical calculations to traversing members in a hierarchy.</span></span> <span data-ttu-id="05367-105">不過，就如同其他複雜且功能強大的產品一樣，總是有進一步擴充產品功能的需求。</span><span class="sxs-lookup"><span data-stu-id="05367-105">However, as with any other complex and robust product, there is always the need to extend the functionality of such a product further.</span></span>  
  
 <span data-ttu-id="05367-106">因此，Analysis Services 可讓您將組件和個人化的延伸模組加入到服務的執行個體，在標準功能不足時，完成您的商務需求。</span><span class="sxs-lookup"><span data-stu-id="05367-106">Therefore, Analysis Services provides you with the ability to add assemblies and personalized extensions to an instance of the service, in order to complete your business needs whenever the standard functionality is not enough.</span></span>  
  
## <a name="assemblies"></a><span data-ttu-id="05367-107">組件</span><span class="sxs-lookup"><span data-stu-id="05367-107">Assemblies</span></span>  
 <span data-ttu-id="05367-108">組件可以讓您延伸 MDX 和 DMX 的商務功能。</span><span class="sxs-lookup"><span data-stu-id="05367-108">Assemblies enable you to extend the business functionality of MDX and DMX.</span></span> <span data-ttu-id="05367-109">您可以將想要的功能建立成程式庫 (例如動態連結程式庫 (DLL))，然後將該程式庫當成組件加入 Analysis Services 執行個體或 Analysis Services 資料庫中。</span><span class="sxs-lookup"><span data-stu-id="05367-109">You build the functionality that you want into a library, such as a dynamic link library (DLL), then add the library as an assembly to an instance of Analysis Services or to an Analysis Services database.</span></span> <span data-ttu-id="05367-110">程式庫中的公用方法便公開給 MDX 和 DMX 運算式、程序、計算、動作，以及用戶端應用程式，作為使用者自訂函數。</span><span class="sxs-lookup"><span data-stu-id="05367-110">The public methods in the library are then exposed as user-defined functions to MDX and DMX expressions, procedures, calculations, actions, and client applications.</span></span>  
  
## <a name="personalized-extensions"></a><span data-ttu-id="05367-111">個人化的延伸模組</span><span class="sxs-lookup"><span data-stu-id="05367-111">Personalized Extensions</span></span>  
 <span data-ttu-id="05367-112">SQL Server Analysis Services 個人化延伸模組是實作外掛程式架構之概念的基礎。</span><span class="sxs-lookup"><span data-stu-id="05367-112">SQL Server Analysis Services personalization extensions are the foundation of the idea of implementing a plug-in architecture.</span></span> <span data-ttu-id="05367-113">Analysis Services 個人化延伸模組是現有 managed 元件架構的簡單且簡潔的修改，而且會在整個 Analysis Services 的[AdomdServer](/previous-versions/sql/sql-server-2014/ms131779(v=sql.120))物件模型、多維度運算式 (MDX) 語法和架構資料列集公開。</span><span class="sxs-lookup"><span data-stu-id="05367-113">Analysis Services personalization extensions are a simple and elegant modification to the existing managed assembly architecture and are exposed throughout the Analysis Services [Microsoft.AnalysisServices.AdomdServer](/previous-versions/sql/sql-server-2014/ms131779(v=sql.120)) object model, Multidimensional Expressions (MDX) syntax, and schema rowsets.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05367-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="05367-114">See Also</span></span>  
 <span data-ttu-id="05367-115">[多維度模型元件管理](../multidimensional-model-assemblies-management.md) </span><span class="sxs-lookup"><span data-stu-id="05367-115">[Multidimensional Model Assemblies Management](../multidimensional-model-assemblies-management.md) </span></span>  
 [<span data-ttu-id="05367-116">Analysis Services 個人化延伸模組</span><span class="sxs-lookup"><span data-stu-id="05367-116">Analysis Services Personalization Extensions</span></span>](analysis-services-personalization-extensions.md)  
  
  
