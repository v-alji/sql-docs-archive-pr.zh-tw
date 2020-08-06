---
title: 自動定義新屬性 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- automatic attribute creation
- attributes [Analysis Services], creating
ms.assetid: 208a050a-5e2f-470c-b645-8d835e123db7
author: minewiskan
ms.author: owend
ms.openlocfilehash: 40f9ae1f00dd0a6520c6d1b06111864fba02e8f2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708809"
---
# <a name="define-a-new-attribute-automatically"></a><span data-ttu-id="9e7d6-102">自動定義新屬性</span><span class="sxs-lookup"><span data-stu-id="9e7d6-102">Define a New Attribute Automatically</span></span>
  <span data-ttu-id="9e7d6-103">您可以在 [維度設計師] 中使用拖放式編輯，在維度中建立新屬性。</span><span class="sxs-lookup"><span data-stu-id="9e7d6-103">You can create a new attribute in a dimension by using drag-and-drop editing in the Dimension Designer.</span></span>  
  
### <a name="to-create-a-new-attribute-automatically"></a><span data-ttu-id="9e7d6-104">自動建立新屬性</span><span class="sxs-lookup"><span data-stu-id="9e7d6-104">To create a new attribute automatically</span></span>  
  
1.  <span data-ttu-id="9e7d6-105">在維度設計師中，開啟您要在其中建立屬性的維度。</span><span class="sxs-lookup"><span data-stu-id="9e7d6-105">In Dimension Designer, open the dimension in which you want to create the attribute.</span></span>  
  
2.  <span data-ttu-id="9e7d6-106">在 **[維度結構]** 索引標籤上，從 **[資料來源檢視]** 窗格的資料表中選取想要繫結屬性的資料行，然後將該資料行拖曳至 **[屬性]** 窗格。</span><span class="sxs-lookup"><span data-stu-id="9e7d6-106">On the **Dimension Structure** tab, in the **Data Source View** pane, in the table to which you want to bind the attribute, select the column, and then drag the column to the **Attributes** pane.</span></span>  
  
     [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="9e7d6-107">就會建立與所繫結之資料行相同名稱的新屬性。</span><span class="sxs-lookup"><span data-stu-id="9e7d6-107">creates the new attribute that has the same name as the column to which it is bound.</span></span> <span data-ttu-id="9e7d6-108">如果有多個屬性使用相同資料行， [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 會在屬性名稱後面附加一個數字。</span><span class="sxs-lookup"><span data-stu-id="9e7d6-108">If there are multiple attributes that use the same column, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] appends a number to the attribute name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e7d6-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9e7d6-109">See Also</span></span>  
 <span data-ttu-id="9e7d6-110">[多維度模型中的維度](dimensions-in-multidimensional-models.md) </span><span class="sxs-lookup"><span data-stu-id="9e7d6-110">[Dimensions in Multidimensional Models](dimensions-in-multidimensional-models.md) </span></span>  
 [<span data-ttu-id="9e7d6-111">維度屬性 (attribute) 屬性 (property) 參考</span><span class="sxs-lookup"><span data-stu-id="9e7d6-111">Dimension Attribute Properties Reference</span></span>](dimension-attribute-properties-reference.md)  
  
  
