---
title: 建立模型資料行的別名 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data mining [Analysis Services], how-to topics
- mining models [Analysis Services], columns
- column names [Analysis Services]
ms.assetid: c80ebe66-a8f8-4f24-9fe8-8288de9d13bc
author: minewiskan
ms.author: owend
ms.openlocfilehash: 908c0a8d8caa810badf4b82dc3dd3f411d09f323
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592330"
---
# <a name="create-an-alias-for-a-model-column"></a><span data-ttu-id="d9e2c-102">建立模型資料行的別名</span><span class="sxs-lookup"><span data-stu-id="d9e2c-102">Create an Alias for a Model Column</span></span>
  <span data-ttu-id="d9e2c-103">您可以在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]中為模型資料行建立別名。</span><span class="sxs-lookup"><span data-stu-id="d9e2c-103">In [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], you can create an alias for a model column.</span></span> <span data-ttu-id="d9e2c-104">當採礦結構名稱太長而不易處理，或者當您想要將資料行重新命名，以針對其內容或它在模型中的使用方式給予較為描述性的名稱時，這麼做很有用。</span><span class="sxs-lookup"><span data-stu-id="d9e2c-104">This might be useful when the mining structure name is too long to easily work with, or when you want to rename the column to be more descriptive of its contents or usage in the model.</span></span> <span data-ttu-id="d9e2c-105">例如，如果建立結構資料行的複本，然後再針對特定的模型以不同的方式分隔資料行，就可以將該資料行重新命名，以更為正確的方式來反映內容。</span><span class="sxs-lookup"><span data-stu-id="d9e2c-105">For example, if you make a copy of a structure column and then discretize the column differently for a particular model, you can rename the column to reflect the content more accurately.</span></span>  
  
 <span data-ttu-id="d9e2c-106">若要建立模型資料行的別名，可以使用 [屬性]\*\*\*\* 窗格，並設定資料行的 [Name](https://docs.microsoft.com/bi-reference/assl/properties/name-element-assl) 屬性。</span><span class="sxs-lookup"><span data-stu-id="d9e2c-106">To create an alias for a model column, you use the **Properties** pane and set the [Name](https://docs.microsoft.com/bi-reference/assl/properties/name-element-assl) property of the column.</span></span>  
  
 <span data-ttu-id="d9e2c-107">在資料採礦設計師的 [採礦模型]\*\*\*\* 索引標籤上，別名會顯示在資料行使用方式標籤旁的括弧中。</span><span class="sxs-lookup"><span data-stu-id="d9e2c-107">On the **Mining Models** tab of Data Mining Designer, the alias appears enclosed in parentheses next to the column usage label.</span></span>  
  
 <span data-ttu-id="d9e2c-108">如需如何在採礦模型中設定屬性的資訊，請參閱 [採礦模型資料行](mining-model-columns.md)。</span><span class="sxs-lookup"><span data-stu-id="d9e2c-108">For information about how to set the properties of a mining model, see [Mining Model Columns](mining-model-columns.md).</span></span>  
  
### <a name="to-add-an-alias-to-a-mining-model-column"></a><span data-ttu-id="d9e2c-109">若要將別名加入至採礦模型資料行</span><span class="sxs-lookup"><span data-stu-id="d9e2c-109">To add an alias to a mining model column</span></span>  
  
1.  <span data-ttu-id="d9e2c-110">在資料採礦設計師的 [採礦模型]\*\*\*\* 索引標籤上，以滑鼠右鍵在採礦模型中按一下要變更的採礦資料行的資料格，然後選取 [屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d9e2c-110">In the **Mining Models** tab in Data Mining Designer, right-click the cell in the mining model for the mining column that you want to change, and then select **Properties**.</span></span>  
  
2.  <span data-ttu-id="d9e2c-111">在畫面右側的 [屬性]\*\*\*\* 視窗中，按一下 [Name] 屬性旁的資料格，然後刪除目前的值。</span><span class="sxs-lookup"><span data-stu-id="d9e2c-111">In the **Properties** window on the right side of the screen, click the cell next to the Name property and delete the current value.</span></span> <span data-ttu-id="d9e2c-112">輸入資料行的新名稱。</span><span class="sxs-lookup"><span data-stu-id="d9e2c-112">Type a new name for the column.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9e2c-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d9e2c-113">See Also</span></span>  
 <span data-ttu-id="d9e2c-114">[採礦模型工作和操作說明](mining-model-tasks-and-how-tos.md) </span><span class="sxs-lookup"><span data-stu-id="d9e2c-114">[Mining Model Tasks and How-tos](mining-model-tasks-and-how-tos.md) </span></span>  
 [<span data-ttu-id="d9e2c-115">採礦模型屬性</span><span class="sxs-lookup"><span data-stu-id="d9e2c-115">Mining Model Properties</span></span>](mining-model-properties.md)  
  
  
