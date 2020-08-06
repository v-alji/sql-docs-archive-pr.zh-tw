---
title: 使用 [鑽取] 來抓取來源資料 (MDX) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- DRILLTHROUGH statement
- retrieving data
- queries [MDX], DRILLTHROUGH statement
- data retrieval [MDX]
ms.assetid: fe0ab170-25a9-45a8-a377-f71a67f77018
author: minewiskan
ms.author: owend
ms.openlocfilehash: 5601a3ddfa7075ed53330e12c260af88648db990
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596358"
---
# <a name="using-drillthrough-to-retrieve-source-data-mdx"></a><span data-ttu-id="8f0c1-102">使用 DRILLTHROUGH 擷取來源資料 (MDX)</span><span class="sxs-lookup"><span data-stu-id="8f0c1-102">Using DRILLTHROUGH to Retrieve Source Data (MDX)</span></span>
  <span data-ttu-id="8f0c1-103">多維度運算式 (MDX) 使用 [DRILLTHROUGH](/sql/mdx/mdx-data-manipulation-drillthrough)陳述式從來源資料擷取 Cube 資料格的資料列集。</span><span class="sxs-lookup"><span data-stu-id="8f0c1-103">Multidimensional Expressions (MDX) uses the [DRILLTHROUGH](/sql/mdx/mdx-data-manipulation-drillthrough)statement to retrieve a rowset from the source data for a cube cell.</span></span>  
  
 <span data-ttu-id="8f0c1-104">必須定義 Cube 的鑽研動作，才能在該 Cube 上執行 `DRILLTHROUGH` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="8f0c1-104">In order to run a `DRILLTHROUGH` statement on a cube, a drillthrough action must be defined for that cube.</span></span> <span data-ttu-id="8f0c1-105">若要定義鑽研動作，請在 [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] 的 Cube 設計師中，於 [動作]\*\*\*\* 窗格的工具列上，按一下 [新增鑽研動作]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="8f0c1-105">To define a drillthrough action, in [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)], in Cube Designer, on the **Actions** pane, on the toolbar, click **New Drillthrough Action**.</span></span> <span data-ttu-id="8f0c1-106">在新增的鑽研動作中，指定動作名稱、目標、條件，以及 `DRILLTHROUGH` 陳述式所傳回的資料行。</span><span class="sxs-lookup"><span data-stu-id="8f0c1-106">In the new drillthrough action, specify the action name, target, condition, and the columns that are returned by a `DRILLTHROUGH` statement.</span></span>  
  
## <a name="drillthrough-statement-syntax"></a><span data-ttu-id="8f0c1-107">DRILLTHROUGH 陳述式語法</span><span class="sxs-lookup"><span data-stu-id="8f0c1-107">DRILLTHROUGH Statement Syntax</span></span>  
 <span data-ttu-id="8f0c1-108">`DRILLTHROUGH` 陳述式使用以下語法：</span><span class="sxs-lookup"><span data-stu-id="8f0c1-108">The `DRILLTHROUGH` statement uses the following syntax:</span></span>  
  
```  
<drillthrough> ::= DRILLTHROUGH [<Max_Rows>] [<First_Rowset>] <MDX select> [<Return_Columns>]  
   < Max_Rows> ::= MAXROWS <positive number>  
   <First_Rowset> ::= FIRSTROWSET <positive number>  
   <Return_Columns> ::= RETURN <member or attribute> [, <member or attribute>]  
```  
  
 <span data-ttu-id="8f0c1-109">`SELECT` 子句可識別包含所要擷取之來源資料的 Cube 資料格。</span><span class="sxs-lookup"><span data-stu-id="8f0c1-109">The `SELECT` clause identifies the cube cell that contains the source data to be retrieved.</span></span> <span data-ttu-id="8f0c1-110">除了在 `SELECT` 子句中每個座標軸只能指定一個成員之外，此 `SELECT` 子句跟一般的 MDX `SELECT` 陳述式相同。</span><span class="sxs-lookup"><span data-stu-id="8f0c1-110">This `SELECT` clause is the same to an ordinary MDX `SELECT` statement, except that in the `SELECT` clause only one member can be specified on each axis.</span></span> <span data-ttu-id="8f0c1-111">如果在一個座標軸上指定多個成員，就會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="8f0c1-111">If more than one member is specified on an axis, an error occurs.</span></span>  
  
 <span data-ttu-id="8f0c1-112">`<Max_Rows>` 語法可指定每個傳回之資料列集中的最大資料列數目。</span><span class="sxs-lookup"><span data-stu-id="8f0c1-112">The `<Max_Rows>` syntax specifies the maximum number of the rows in each returned rowset.</span></span> <span data-ttu-id="8f0c1-113">如果用以連接資料來源的 OLE DB 提供者不支援 `DBPROP_MAXROWS`，就會忽略 `<Max_Rows>` 設定。</span><span class="sxs-lookup"><span data-stu-id="8f0c1-113">If the OLE DB provider that is used to connect to the data source does not support `DBPROP_MAXROWS`, the `<Max_Rows>` setting is ignored.</span></span>  
  
 <span data-ttu-id="8f0c1-114">`<First_Rowset>` 語法可識別最早將資料列集傳回的資料分割。</span><span class="sxs-lookup"><span data-stu-id="8f0c1-114">The `<First_Rowset>` syntax identifies the partition whose rowset is returned first.</span></span>  
  
 <span data-ttu-id="8f0c1-115">`<Return_Columns>` 語法可識別要傳回的基礎資料庫資料行。</span><span class="sxs-lookup"><span data-stu-id="8f0c1-115">The `<Return_Columns>` syntax identifies the underlying database columns to be returned.</span></span>  
  
## <a name="drillthrough-statement-example"></a><span data-ttu-id="8f0c1-116">DRILLTHROUGH 陳述式範例</span><span class="sxs-lookup"><span data-stu-id="8f0c1-116">DRILLTHROUGH Statement Example</span></span>  
 <span data-ttu-id="8f0c1-117">以下範例示範 `DRILLTHROUGH` 陳述式的用法。</span><span class="sxs-lookup"><span data-stu-id="8f0c1-117">The following example demonstrates the use of the `DRILLTHROUGH` statement.</span></span> <span data-ttu-id="8f0c1-118">在此範例中，DRILLTHROUGH 陳述式會沿著 Stores 維度 (Slicer 軸)，查詢 Store、Product 及 Time 維度的分葉，然後傳回部門量值群組、部門識別碼及員工的姓氏。</span><span class="sxs-lookup"><span data-stu-id="8f0c1-118">In this example, the DRILLTHROUGH statement queries the leaves of the Store, Product, and Time dimensions along the Stores dimension (the slicer axis), and then returns the department measure group, department ID, and employee's first name.</span></span>  
  
```  
DRILLTHROUGH  
Select {Leaves(Store), Leaves(Product), Leaves(Time),*} on 0  
From Stores  
RETURN [Department MeasureGroup].[Department Id], [Employee].[First Name]  
```  
  
## <a name="see-also"></a><span data-ttu-id="8f0c1-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8f0c1-119">See Also</span></span>  
 [<span data-ttu-id="8f0c1-120">操作資料 &#40;MDX&#41;</span><span class="sxs-lookup"><span data-stu-id="8f0c1-120">Manipulating Data &#40;MDX&#41;</span></span>](mdx-data-manipulation-manipulating-data.md)  
  
  
