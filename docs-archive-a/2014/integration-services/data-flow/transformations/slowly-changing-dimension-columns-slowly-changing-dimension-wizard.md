---
title: 緩時變維度資料行 (緩時變維度精靈) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.loaddimwizard.scdsupport.f1
ms.assetid: 36de99d5-5368-48e0-b876-17e9c6862c6c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 6283887cbddb9844e0ac769281184f588dc2a94d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687060"
---
# <a name="slowly-changing-dimension-columns-slowly-changing-dimension-wizard"></a><span data-ttu-id="7165e-102">緩時變維度資料行 (緩時變維度精靈)</span><span class="sxs-lookup"><span data-stu-id="7165e-102">Slowly Changing Dimension Columns (Slowly Changing Dimension Wizard)</span></span>
  <span data-ttu-id="7165e-103">使用 **[緩時變維度資料行]** 對話方塊，以選取每個緩時變維度資料行的變更類型。</span><span class="sxs-lookup"><span data-stu-id="7165e-103">Use the **Slowly Changing Dimensions Columns** dialog box to select a change type for each slowly changing dimension column.</span></span>  
  
 <span data-ttu-id="7165e-104">若要深入了解這個精靈，請參閱＜ [Slowly Changing Dimension Transformation](slowly-changing-dimension-transformation.md)＞。</span><span class="sxs-lookup"><span data-stu-id="7165e-104">To learn more about this wizard, see [Slowly Changing Dimension Transformation](slowly-changing-dimension-transformation.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="7165e-105">選項。</span><span class="sxs-lookup"><span data-stu-id="7165e-105">Options</span></span>  
 <span data-ttu-id="7165e-106">**維度資料行**</span><span class="sxs-lookup"><span data-stu-id="7165e-106">**Dimension Columns**</span></span>  
 <span data-ttu-id="7165e-107">從清單中選取維度資料行。</span><span class="sxs-lookup"><span data-stu-id="7165e-107">Select a dimension column from the list.</span></span>  
  
 <span data-ttu-id="7165e-108">**變更類型**</span><span class="sxs-lookup"><span data-stu-id="7165e-108">**Change Type**</span></span>  
 <span data-ttu-id="7165e-109">選取 [固定屬性]  ，或選取兩種變更屬性類型的其中之一。</span><span class="sxs-lookup"><span data-stu-id="7165e-109">Select a **Fixed Attribute**, or select one of the two types of changing attributes.</span></span> <span data-ttu-id="7165e-110">資料行中的值不會變更時，請使用 **[固定屬性]** ； [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 會將變更視為錯誤。</span><span class="sxs-lookup"><span data-stu-id="7165e-110">Use **Fixed Attribute** when the value in a column should not change; [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] then treats changes as errors.</span></span> <span data-ttu-id="7165e-111">使用 **[變更屬性]** 以變更的值覆寫現有的值。</span><span class="sxs-lookup"><span data-stu-id="7165e-111">Use **Changing Attribute** to overwrite existing values with changed values.</span></span> <span data-ttu-id="7165e-112">使用 **[記錄屬性]** 在新記錄中儲存變更的值，同時將先前的記錄標示為過期。</span><span class="sxs-lookup"><span data-stu-id="7165e-112">Use **Historical Attribute** to save changed values in new records, while marking previous records as outdated.</span></span>  
  
 <span data-ttu-id="7165e-113">**移除**</span><span class="sxs-lookup"><span data-stu-id="7165e-113">**Remove**</span></span>  
 <span data-ttu-id="7165e-114">選取維度資料行，並按一下 [移除]  從對應資料行清單中將其移除。</span><span class="sxs-lookup"><span data-stu-id="7165e-114">Select a dimension column, and remove it from the list of mapped columns by clicking **Remove**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7165e-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7165e-115">See Also</span></span>  
 [<span data-ttu-id="7165e-116">使用緩時變維度精靈來設定輸出</span><span class="sxs-lookup"><span data-stu-id="7165e-116">Configure Outputs Using the Slowly Changing Dimension Wizard</span></span>](configure-outputs-using-the-slowly-changing-dimension-wizard.md)  
  
  
