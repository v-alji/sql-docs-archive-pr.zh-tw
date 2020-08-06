---
title: 建立遞迴階層群組 (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 06eccab6-4089-46e8-a84f-5bf3bbe0c23b
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: aeb99e725c5c61a6dc66c83e53afbc43b1224582
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594411"
---
# <a name="creating-recursive-hierarchy-groups-report-builder-and-ssrs"></a><span data-ttu-id="f72c0-102">建立遞迴階層群組 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="f72c0-102">Creating Recursive Hierarchy Groups (Report Builder and SSRS)</span></span>
  <span data-ttu-id="f72c0-103">若要顯示遞迴資料，其中父代和子系之間的關聯性是以資料集中的欄位來表示，您可以根據子欄位設定資料區群組運算式，並根據父欄位來設定 Parent 屬性。</span><span class="sxs-lookup"><span data-stu-id="f72c0-103">To display recursive data where the relationship between parent and child is represented by fields in the dataset, you can set the data region group expression based on the child field and set the Parent property based on the parent field.</span></span>  
  
 <span data-ttu-id="f72c0-104">顯示階層式資料是遞迴階層群組的常見用法，例如組織圖中的員工。</span><span class="sxs-lookup"><span data-stu-id="f72c0-104">Displaying hierarchical data is a common use for recursive hierarchy groups, for example, employees in an organizational chart.</span></span> <span data-ttu-id="f72c0-105">此資料集包含員工和經理的清單，經理名稱也會出現在員工清單內。</span><span class="sxs-lookup"><span data-stu-id="f72c0-105">The dataset includes a list of employees and the managers, where the manager names also appear in the list of employees.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="creating-recursive-hierarchies"></a><span data-ttu-id="f72c0-106">建立遞迴階層</span><span class="sxs-lookup"><span data-stu-id="f72c0-106">Creating Recursive Hierarchies</span></span>  
 <span data-ttu-id="f72c0-107">若要在 Tablix 資料區中建立遞迴階層，您必須將群組運算式設定為指定子資料的欄位，並將此群組的 Parent 屬性設定為指定父資料的欄位。</span><span class="sxs-lookup"><span data-stu-id="f72c0-107">To build a recursive hierarchy in a tablix data region, you must set the group expression to the field that specifies the child data and the Parent property of the group to the field that specifies the parent data.</span></span> <span data-ttu-id="f72c0-108">例如，如果是包含員工識別碼和經理識別碼之欄位的資料集 (員工向經理報告)，請將群組運算式設定為員工識別碼，並將 Parent 屬性設定為經理識別碼。</span><span class="sxs-lookup"><span data-stu-id="f72c0-108">For example, for a dataset that includes fields for employee ID and manager ID where employees report to managers, set the group expression to employee ID and the Parent property to manager ID.</span></span>  
  
 <span data-ttu-id="f72c0-109">定義成遞迴階層的群組 (也就是使用 Parent 屬性的群組) 只能有單一群組運算式。</span><span class="sxs-lookup"><span data-stu-id="f72c0-109">A group that is defined as a recursive hierarchy (that is, a group that uses the Parent property) can have only one group expression.</span></span> <span data-ttu-id="f72c0-110">您可以在文字方塊填補中，利用 `Level` 函數，根據員工在階層內的層級來縮排員工名稱。</span><span class="sxs-lookup"><span data-stu-id="f72c0-110">You can use the `Level` function in text box padding to indent employee names based on their level in the hierarchy.</span></span>  
  
 <span data-ttu-id="f72c0-111">如需詳細資訊，請參閱[在資料區中新增或刪除群組 &#40;報表產生器及 SSRS&#41;](add-or-delete-a-group-in-a-data-region-report-builder-and-ssrs.md) 和[建立遞迴階層群組 &#40;報表產生器及 SSRS&#41;](create-a-recursive-hierarchy-group-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="f72c0-111">For more information, see [Add or Delete a Group in a Data Region &#40;Report Builder and SSRS&#41;](add-or-delete-a-group-in-a-data-region-report-builder-and-ssrs.md) and  [Create a Recursive Hierarchy Group &#40;Report Builder and SSRS&#41;](create-a-recursive-hierarchy-group-report-builder-and-ssrs.md).</span></span>  
  
### <a name="aggregate-functions-that-support-recursion"></a><span data-ttu-id="f72c0-112">支援遞迴的彙總函式</span><span class="sxs-lookup"><span data-stu-id="f72c0-112">Aggregate Functions that support Recursion</span></span>  
 <span data-ttu-id="f72c0-113">您可以使用接受 *Recursive* 參數的 Reporting Services 彙總函式，針對遞迴階層計算摘要資料。</span><span class="sxs-lookup"><span data-stu-id="f72c0-113">You can use Reporting Services aggregate functions that accept the parameter *Recursive* to calculate summary data for a recursive hierarchy.</span></span> <span data-ttu-id="f72c0-114">下列函數接受 `Recursive` 作為參數： [Sum](report-builder-functions-sum-function.md)、 [Avg](report-builder-functions-avg-function.md)、 [Count](report-builder-functions-count-function.md)、 [CountDistinct](report-builder-functions-countdistinct-function.md)、 [CountRows](report-builder-functions-countrows-function.md)、 [Max](report-builder-functions-max-function.md)、 [Min](report-builder-functions-min-function.md)、 [StDev](report-builder-functions-stdev-function.md)、 [StDevP](report-builder-functions-stdevp-function.md)、 [Sum](report-builder-functions-sum-function.md)、 [Var](report-builder-functions-var-function.md)和[VarP](report-builder-functions-varp-function.md)。</span><span class="sxs-lookup"><span data-stu-id="f72c0-114">The following functions accept `Recursive` as a parameter: [Sum](report-builder-functions-sum-function.md), [Avg](report-builder-functions-avg-function.md), [Count](report-builder-functions-count-function.md), [CountDistinct](report-builder-functions-countdistinct-function.md), [CountRows](report-builder-functions-countrows-function.md), [Max](report-builder-functions-max-function.md), [Min](report-builder-functions-min-function.md), [StDev](report-builder-functions-stdev-function.md), [StDevP](report-builder-functions-stdevp-function.md), [Sum](report-builder-functions-sum-function.md), [Var](report-builder-functions-var-function.md), and [VarP](report-builder-functions-varp-function.md).</span></span> <span data-ttu-id="f72c0-115">如需詳細資訊，請參閱 [彙總函式參考 &#40;報表產生器和 SSRS&#41;](report-builder-functions-aggregate-functions-reference.md)。</span><span class="sxs-lookup"><span data-stu-id="f72c0-115">For more information, see [Aggregate Functions Reference &#40;Report Builder and SSRS&#41;](report-builder-functions-aggregate-functions-reference.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f72c0-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f72c0-116">See Also</span></span>  
 <span data-ttu-id="f72c0-117">[資料表、矩陣和清單 &#40;報表產生器及 SSRS&#41;](tables-matrices-and-lists-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="f72c0-117">[Tables, Matrices, and Lists &#40;Report Builder and SSRS&#41;](tables-matrices-and-lists-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="f72c0-118">[Tablix 資料區 &#40;報表產生器及 SSRS&#41;](../tablix-data-region-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="f72c0-118">[Tablix Data Region &#40;Report Builder and SSRS&#41;](../tablix-data-region-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="f72c0-119">[彙總函式參考 &#40;報表產生器及 SSRS&#41;](report-builder-functions-aggregate-functions-reference.md) </span><span class="sxs-lookup"><span data-stu-id="f72c0-119">[Aggregate Functions Reference &#40;Report Builder and SSRS&#41;](report-builder-functions-aggregate-functions-reference.md) </span></span>  
 <span data-ttu-id="f72c0-120">[資料表 &#40;報表產生器及 SSRS&#41;](tables-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="f72c0-120">[Tables &#40;Report Builder  and SSRS&#41;](tables-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="f72c0-121">[矩陣 &#40;報表產生器及 SSRS&#41;](create-a-matrix-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="f72c0-121">[Matrices &#40;Report Builder and SSRS&#41;](create-a-matrix-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="f72c0-122">[清單 &#40;報表產生器及 SSRS&#41;](create-invoices-and-forms-with-lists-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="f72c0-122">[Lists &#40;Report Builder and SSRS&#41;](create-invoices-and-forms-with-lists-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="f72c0-123">資料表、矩陣和清單 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="f72c0-123">Tables, Matrices, and Lists &#40;Report Builder and SSRS&#41;</span></span>](tables-matrices-and-lists-report-builder-and-ssrs.md)  
  
  
