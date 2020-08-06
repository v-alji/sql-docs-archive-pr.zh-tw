---
title: 運算式參考 (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: bb16e4ab-b13f-48f2-8cfe-1851656875ef
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 7854aa2cc256d63fe93ddb049486e782bfaa0e11
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594407"
---
# <a name="expression-reference-report-builder-and-ssrs"></a><span data-ttu-id="9ebab-102">運算式參考 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="9ebab-102">Expression Reference (Report Builder and SSRS)</span></span>
  <span data-ttu-id="9ebab-103">報表運算式支援各種內建函數與內建集合的參考。</span><span class="sxs-lookup"><span data-stu-id="9ebab-103">Report expressions support a variety of references to built-in functions and built-in collections.</span></span> <span data-ttu-id="9ebab-104">運算式必須具有有效的 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 語法，然後系統才能發行或處理報表。</span><span class="sxs-lookup"><span data-stu-id="9ebab-104">Expressions must have valid [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] syntax before a report can be published or processed.</span></span>  
  
 <span data-ttu-id="9ebab-105">若要開發複雜運算式或使用自訂程式碼或自訂組件的運算式，建議您使用 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中的報表設計師。</span><span class="sxs-lookup"><span data-stu-id="9ebab-105">To develop complex expressions or expressions that use custom code or custom assemblies, we recommend that you use Report Designer in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="9ebab-106">如需詳細資訊，請參閱 [報表設計師中運算式的自訂程式碼及組件參考 &#40;SSRS&#41;](custom-code-and-assembly-references-in-expressions-in-report-designer-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="9ebab-106">For more information, see [Custom Code and Assembly References in Expressions in Report Designer &#40;SSRS&#41;](custom-code-and-assembly-references-in-expressions-in-report-designer-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
 <span data-ttu-id="9ebab-107">使用本節的主題有助於在報表中撰寫簡單運算式。</span><span class="sxs-lookup"><span data-stu-id="9ebab-107">Use the topics in this section to help write simple expressions in a report.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9ebab-108">本節內容</span><span class="sxs-lookup"><span data-stu-id="9ebab-108">In This Section</span></span>  
 [<span data-ttu-id="9ebab-109">運算式中的資料類型 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="9ebab-109">Data Types in Expressions &#40;Report Builder and SSRS&#41;</span></span>](expressions-report-builder-and-ssrs.md)  
  
 [<span data-ttu-id="9ebab-110">運算式中的常數 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="9ebab-110">Constants in Expressions &#40;Report Builder and SSRS&#41;</span></span>](constants-in-expressions-report-builder-and-ssrs.md)  
  
 [<span data-ttu-id="9ebab-111">運算式中的運算子 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="9ebab-111">Operators in Expressions &#40;Report Builder and SSRS&#41;</span></span>](operators-in-expressions-report-builder-and-ssrs.md)  
  
 [<span data-ttu-id="9ebab-112">運算式中的內建集合 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="9ebab-112">Built-in Collections in Expressions &#40;Report Builder and SSRS&#41;</span></span>](built-in-collections-in-expressions-report-builder.md)  
  
 [<span data-ttu-id="9ebab-113">內建的全域和使用者參考 &#40;報表產生器和 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="9ebab-113">Built-in Globals and Users References &#40;Report Builder and SSRS&#41;</span></span>](built-in-collections-built-in-globals-and-users-references-report-builder.md)  
  
 [<span data-ttu-id="9ebab-114">參數集合參考 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="9ebab-114">Parameters Collection References &#40;Report Builder and SSRS&#41;</span></span>](built-in-collections-parameters-collection-references-report-builder.md)  
  
 [<span data-ttu-id="9ebab-115">資料集 Fields 集合參考 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="9ebab-115">Dataset Fields Collection References &#40;Report Builder and SSRS&#41;</span></span>](built-in-collections-dataset-fields-collection-references-report-builder.md)  
  
 [<span data-ttu-id="9ebab-116">DataSources 和 DataSets 集合參考 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="9ebab-116">DataSources and DataSets Collection References &#40;Report Builder and SSRS&#41;</span></span>](built-in-collections-datasources-and-datasets-references-report-builder.md)  
  
 [<span data-ttu-id="9ebab-117">報表和群組變數集合參考 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="9ebab-117">Report and Group Variables Collections References &#40;Report Builder and SSRS&#41;</span></span>](built-in-collections-report-and-group-variables-references-report-builder.md)  
  
 [<span data-ttu-id="9ebab-118">ReportItems 集合參考 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="9ebab-118">ReportItems Collection References &#40;Report Builder and SSRS&#41;</span></span>](built-in-collections-reportitems-collection-references-report-builder.md)  
  
## <a name="see-also"></a><span data-ttu-id="9ebab-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9ebab-119">See Also</span></span>  
 [<span data-ttu-id="9ebab-120">運算式 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="9ebab-120">Expressions &#40;Report Builder and SSRS&#41;</span></span>](expressions-report-builder-and-ssrs.md)  
  
  
