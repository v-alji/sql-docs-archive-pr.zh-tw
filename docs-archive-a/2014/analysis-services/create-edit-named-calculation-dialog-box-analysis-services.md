---
title: 建立-編輯命名計算對話方塊 (Analysis Services) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.dsveditor.createnamedcalculation.f1
helpviewer_keywords:
- Named Calculation dialog box
ms.assetid: 66fb30ae-f5c5-4bfc-80ca-8c8a3a9bb30d
author: minewiskan
ms.author: owend
ms.openlocfilehash: 0b6777feb47a1ce6b601d0190e413b4baae35f1f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584851"
---
# <a name="create-edit-named-calculation-dialog-box-analysis-services"></a><span data-ttu-id="10de0-102">建立-編輯命名計算對話方塊 (Analysis Services) </span><span class="sxs-lookup"><span data-stu-id="10de0-102">Create-Edit Named Calculation Dialog Box (Analysis Services)</span></span>
  <span data-ttu-id="10de0-103">使用 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 中的 [建立/編輯具名計算]\*\*\*\* 對話方塊，即可定義或修改資料來源檢視中之資料表的具名計算。</span><span class="sxs-lookup"><span data-stu-id="10de0-103">Use the **Create/Edit Named Calculation** dialog box in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] to define or modify a named calculation for a table in a data source view.</span></span> <span data-ttu-id="10de0-104">您可以執行下列動作來顯示 [建立/編輯具名計算]\*\*\*\* 對話方塊：</span><span class="sxs-lookup"><span data-stu-id="10de0-104">You can display the **Create/Edit Named Calculation** dialog box by:</span></span>  
  
-   <span data-ttu-id="10de0-105">在 [資料來源檢視設計師]\*\*\*\* 的 [工具列]\*\*\*\* 窗格中，按一下 [新增具名計算]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="10de0-105">Clicking **New Named Calculation** in the **Toolbar** pane of **Data Source View Designer**.</span></span>  
  
-   <span data-ttu-id="10de0-106">在 [資料來源檢視設計師]\*\*\*\* 的 [資料表]\*\*\*\* 或 [圖表]\*\*\*\* 窗格中，以滑鼠右鍵按一下資料表，然後選取 [新增具名計算]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="10de0-106">Right-clicking a table in either the **Tables** or **Diagram** pane of **Data Source View Designer** and selecting **New Named Calculation**.</span></span>  
  
-   <span data-ttu-id="10de0-107">在 [資料來源檢視設計師]\*\*\*\* 的 [圖表]\*\*\*\* 窗格中，以滑鼠右鍵按一下具名計算的名稱，然後選取 [編輯具名計算]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="10de0-107">Right-clicking the name of a named calculation in the **Diagram** pane of **Data Source View Designer** and selecting **Edit Named Calculation**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="10de0-108">選項</span><span class="sxs-lookup"><span data-stu-id="10de0-108">Options</span></span>  
 <span data-ttu-id="10de0-109">**資料行名稱**</span><span class="sxs-lookup"><span data-stu-id="10de0-109">**Column Name**</span></span>  
 <span data-ttu-id="10de0-110">輸入具名計算的名稱。</span><span class="sxs-lookup"><span data-stu-id="10de0-110">Type the name of the named calculation.</span></span>  
  
 <span data-ttu-id="10de0-111">**說明**</span><span class="sxs-lookup"><span data-stu-id="10de0-111">**Description**</span></span>  
 <span data-ttu-id="10de0-112">輸入具名計算的選擇性描述。</span><span class="sxs-lookup"><span data-stu-id="10de0-112">Type the optional description of the named calculation.</span></span>  
  
 <span data-ttu-id="10de0-113">**運算式**</span><span class="sxs-lookup"><span data-stu-id="10de0-113">**Expression**</span></span>  
 <span data-ttu-id="10de0-114">輸入傳回純量值的有效 SQL 運算式。</span><span class="sxs-lookup"><span data-stu-id="10de0-114">Type a valid SQL expression that returns a scalar value.</span></span> <span data-ttu-id="10de0-115">運算式會傳送給提供者，並在下列運算式中進行驗證：</span><span class="sxs-lookup"><span data-stu-id="10de0-115">The expression is sent to the provider, and validated in the following expression:</span></span>  
  
```  
SELECT <Table Name in Data Source>.* , <Expression> AS <Column Name> FROM <Table Name in Data Source>AS <Table Name in Data Source View>  
```  
  
 <span data-ttu-id="10de0-116">運算式可以透過子 SELECT 陳述式來包含其他資料表的參考。</span><span class="sxs-lookup"><span data-stu-id="10de0-116">The expression can contain references to other tables, by means of a sub-select statement.</span></span> <span data-ttu-id="10de0-117">如果運算式在 SELECT 陳述式中需要括號，則必須在輸入的運算式頭尾加上括號。</span><span class="sxs-lookup"><span data-stu-id="10de0-117">If the expression would require parentheses in a SELECT statement, the expression entered must be enclosed between parentheses.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10de0-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="10de0-118">See Also</span></span>  
 <span data-ttu-id="10de0-119">[Analysis Services 的設計工具和對話方塊 &#40;多維度資料&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="10de0-119">[Analysis Services Designers and Dialog Boxes &#40;Multidimensional Data&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="10de0-120">資料來源檢視設計工具 &#40;Analysis Services - 多維度資料&#41;</span><span class="sxs-lookup"><span data-stu-id="10de0-120">Data Source View Designer &#40;Analysis Services - Multidimensional Data&#41;</span></span>](data-source-view-designer-analysis-services-multidimensional-data.md)  
  
  
