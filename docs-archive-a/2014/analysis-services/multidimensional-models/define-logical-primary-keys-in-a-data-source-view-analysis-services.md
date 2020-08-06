---
title: 在資料來源視圖中定義邏輯主鍵 (Analysis Services) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- removing logical primary keys
- logical primary keys [SQL Server]
- deleting logical primary keys
- data source views [Analysis Services], logical primary keys
ms.assetid: 172bc267-c637-4caa-bf55-0ba198d30b1e
author: minewiskan
ms.author: owend
ms.openlocfilehash: 25092e5d754381c572dcdbfc03e5ee0f29c1df24
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596389"
---
# <a name="define-logical-primary-keys-in-a-data-source-view-analysis-services"></a><span data-ttu-id="4edd3-102">在資料來源檢視中定義邏輯主索引鍵 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="4edd3-102">Define Logical Primary Keys in a Data Source View (Analysis Services)</span></span>
  <span data-ttu-id="4edd3-103">[資料來源檢視精靈] 和資料來源檢視設計師會自動根據基礎資料庫資料表，針對加入到資料來源檢視中的資料表定義主索引鍵。</span><span class="sxs-lookup"><span data-stu-id="4edd3-103">The Data Source View Wizard and Data Source View Designer automatically define a primary key for a table that is added to a data source view based on underlying database table.</span></span>  
  
 <span data-ttu-id="4edd3-104">您有時候可能需要手動定義資料來源檢視中的主索引鍵。</span><span class="sxs-lookup"><span data-stu-id="4edd3-104">Occasionally, you may need to manually define a primary key in the data source view.</span></span> <span data-ttu-id="4edd3-105">例如，基於效能或設計考量，資料來源中的資料表可能並未明確定義主索引鍵資料行。</span><span class="sxs-lookup"><span data-stu-id="4edd3-105">For example, for performance or design reasons, tables in a data source may not have explicitly defined primary key columns.</span></span> <span data-ttu-id="4edd3-106">具名查詢和檢視也可能會省略資料表的主索引鍵資料行。</span><span class="sxs-lookup"><span data-stu-id="4edd3-106">Named queries and views may also omit the primary key column for a table.</span></span> <span data-ttu-id="4edd3-107">如果資料表、檢視或具名查詢沒有定義實體主索引鍵，您可以在資料來源檢視設計師中，以手動方式在資料表、檢視或具名查詢中定義邏輯主索引鍵。</span><span class="sxs-lookup"><span data-stu-id="4edd3-107">If a table, view, or named query does not have a physical primary key defined, you can manually define a logical primary key on the table, view or named query in Data Source View Designer.</span></span>  
  
## <a name="set-a-logical-primary-key"></a><span data-ttu-id="4edd3-108">設定邏輯主索引鍵</span><span class="sxs-lookup"><span data-stu-id="4edd3-108">Set a Logical Primary Key</span></span>  
 <span data-ttu-id="4edd3-109">在 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 中必須有主索引鍵，以唯一識別資料表中的記錄、識別維度資料表中的索引鍵資料行，並支援資料表、檢視及具名查詢之間的關聯性。</span><span class="sxs-lookup"><span data-stu-id="4edd3-109">Primary keys are required in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] to uniquely identify records in a table, identify key columns in dimension tables and to support relationships between tables, views and named queries.</span></span> <span data-ttu-id="4edd3-110">這些關聯性是用來建構一些查詢，以便擷取基礎資料來源中的資料和中繼資料，以及利用進階商業智慧的功能。</span><span class="sxs-lookup"><span data-stu-id="4edd3-110">These relationships are used to construct queries for retrieving data and metadata from underlying data sources, and to take advantage of advanced business intelligence features.</span></span>  
  
 <span data-ttu-id="4edd3-111">任何資料行皆可用於邏輯主索引鍵，包括具名計算。</span><span class="sxs-lookup"><span data-stu-id="4edd3-111">Any column can be used for the logical primary key, including a named calculation.</span></span> <span data-ttu-id="4edd3-112">當您建立邏輯主索引鍵時，唯一條件約束會建立在資料來源檢視中，並標示為主索引鍵條件約束。</span><span class="sxs-lookup"><span data-stu-id="4edd3-112">When you create a logical primary key, a unique constraint is created in the data source view and marked as a primary key constraint.</span></span> <span data-ttu-id="4edd3-113">在選取之資料表中指定的任何其他現有的邏輯主索引鍵會遭到刪除。</span><span class="sxs-lookup"><span data-stu-id="4edd3-113">Any other existing logical primary key specified in the selected table is deleted.</span></span>  
  
1.  <span data-ttu-id="4edd3-114">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中，開啟含有您想在其中設定邏輯主索引鍵之資料來源檢視的專案，或連接到包含此資料來源檢視的資料庫。</span><span class="sxs-lookup"><span data-stu-id="4edd3-114">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the project or connect to the database that contains the data source view in which you wish to set a logical primary key.</span></span>  
  
2.  <span data-ttu-id="4edd3-115">在方案總管中，展開 [資料來源檢視]\*\*\*\* 資料夾，然後按兩下資料來源檢視。</span><span class="sxs-lookup"><span data-stu-id="4edd3-115">In Solution Explorer, expand the **Data Source Views** folder, then double-click the data source view.</span></span>  
  
     <span data-ttu-id="4edd3-116">若要找出資料表或視圖，您可以按一下 [**資料來源視圖**] 功能表，或以滑鼠右鍵按一下 [**資料表]** 或 [**圖表**] 窗格的開放區域，即可使用 [**尋找資料表**] 選項。</span><span class="sxs-lookup"><span data-stu-id="4edd3-116">To locate a table or view, you can use the **Find Table** option by either clicking the **Data Source View**  menu or right-clicking in an open area of the **Tables** or **Diagram** panes.</span></span>  
  
3.  <span data-ttu-id="4edd3-117">在 [資料表]\*\*\*\* 或 [圖表]\*\*\*\* 窗格中，以滑鼠右鍵按一下您要用來定義邏輯主索引鍵的一或多個資料行，然後按一下 [設定邏輯主索引鍵]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4edd3-117">In either the **Tables** or the **Diagram** pane, right-click the column or columns that you want to use to define a logical primary key, and then click **Set Logical Primary Key**.</span></span>  
  
     <span data-ttu-id="4edd3-118">設定邏輯主索引鍵的選項只提供給沒有主索引鍵的資料表使用。</span><span class="sxs-lookup"><span data-stu-id="4edd3-118">The option to set a logical primary key is available only for tables that do not have a primary key.</span></span>  
  
     <span data-ttu-id="4edd3-119">請注意，在您設定主索引鍵後，索引鍵圖示即會識別主索引鍵資料行。</span><span class="sxs-lookup"><span data-stu-id="4edd3-119">Notice that after you set the key, a key icon now identifies the primary key columns.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4edd3-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4edd3-120">See Also</span></span>  
 <span data-ttu-id="4edd3-121">[多維度模型中的資料來源視圖](data-source-views-in-multidimensional-models.md) </span><span class="sxs-lookup"><span data-stu-id="4edd3-121">[Data Source Views in Multidimensional Models](data-source-views-in-multidimensional-models.md) </span></span>  
 [<span data-ttu-id="4edd3-122">在資料來源檢視中定義具名計算 &#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="4edd3-122">Define Named Calculations in a Data Source View &#40;Analysis Services&#41;</span></span>](define-named-calculations-in-a-data-source-view-analysis-services.md)  
  
  
