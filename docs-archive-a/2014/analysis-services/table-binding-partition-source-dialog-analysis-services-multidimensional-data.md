---
title: 資料表系結詳細資料 (分割區來源] 對話方塊)  (Analysis Services-多維度資料) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.partitions.partitiontableselection.f1
ms.assetid: 67d05389-81ae-4a6b-947b-986d37ec72b1
author: minewiskan
ms.author: owend
ms.openlocfilehash: 10845e18a2b7c74a8ed3aeec42f710b9706dc94a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594720"
---
# <a name="table-binding-detail-partition-source-dialog-box-analysis-services---multidimensional-data"></a><span data-ttu-id="85f26-102">資料表繫結詳細資料 (資料分割來源對話方塊) (Analysis Services - 多維度資料)</span><span class="sxs-lookup"><span data-stu-id="85f26-102">Table Binding Detail (Partition Source Dialog Box) (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="85f26-103">使用 **[資料分割來源]** 對話方塊中的 **[資料表繫結]** 選項，即可指定提供資料給資料分割的事實資料表。</span><span class="sxs-lookup"><span data-stu-id="85f26-103">Use the **Table Binding** option in the **Partition Source** dialog box to specify the fact table that provides the data for the partition.</span></span> <span data-ttu-id="85f26-104">您可以從 **[資料分割來源]** 對話方塊的 **[繫結類型]** 選項中，選取 **[資料表繫結]** 來顯示此窗格。</span><span class="sxs-lookup"><span data-stu-id="85f26-104">You can display this pane by selecting **Table Binding** from the **Binding type** option in the **Partition Source** dialog box.</span></span>  
  
## <a name="options"></a><span data-ttu-id="85f26-105">選項</span><span class="sxs-lookup"><span data-stu-id="85f26-105">Options</span></span>  
 <span data-ttu-id="85f26-106">**量值群組**</span><span class="sxs-lookup"><span data-stu-id="85f26-106">**Measure group**</span></span>  
 <span data-ttu-id="85f26-107">顯示此資料分割的量值群組。</span><span class="sxs-lookup"><span data-stu-id="85f26-107">Displays the measure group for this partition.</span></span>  
  
 <span data-ttu-id="85f26-108">[查詢]\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="85f26-108">**Look in**</span></span>  
 <span data-ttu-id="85f26-109">選取包含此資料分割之來源資料表的資料來源或資料來源檢視。</span><span class="sxs-lookup"><span data-stu-id="85f26-109">Select the data source or data source view that contains the source tables for this partition.</span></span> <span data-ttu-id="85f26-110">依預設，會選取所選量值群組使用的資料來源檢視。</span><span class="sxs-lookup"><span data-stu-id="85f26-110">The data source view used by the selected measure group is selected by default.</span></span>  
  
 <span data-ttu-id="85f26-111">**篩選資料表**</span><span class="sxs-lookup"><span data-stu-id="85f26-111">**Filter tables**</span></span>  
 <span data-ttu-id="85f26-112">輸入用於 (依資料表名稱) 限制 [可用的資料表]\*\*\*\* 中顯示之資料表的字串。</span><span class="sxs-lookup"><span data-stu-id="85f26-112">Type the string used to restrict, by table name, the tables displayed in **Available tables**.</span></span>  
  
 <span data-ttu-id="85f26-113">**尋找資料表**</span><span class="sxs-lookup"><span data-stu-id="85f26-113">**Find tables**</span></span>  
 <span data-ttu-id="85f26-114">選取即可重新整理 [可用的資料表]\*\*\*\* 中的資料表清單，如果在 [篩選資料表]\*\*\*\* 中指定了字串，就可以進一步限制清單。</span><span class="sxs-lookup"><span data-stu-id="85f26-114">Select to refresh the list of tables in **Available tables**, further restricting the list if a string was specified in **Filter tables**.</span></span>  
  
 <span data-ttu-id="85f26-115">**可用的資料表**</span><span class="sxs-lookup"><span data-stu-id="85f26-115">**Available tables**</span></span>  
 <span data-ttu-id="85f26-116">按一下即可選取資料表，用來作為資料分割的來源資料表。</span><span class="sxs-lookup"><span data-stu-id="85f26-116">Click to select the table to use as a source table for the partition.</span></span>  
  
 <span data-ttu-id="85f26-117">如果在 **[篩選資料表]** 中沒有指定篩選，就會列出在 **[查詢]** 中指定的資料來源或資料來源檢視內、結構與 **[量值群組]** 中所指定量值群組使用之事實資料表類似的所有資料表。</span><span class="sxs-lookup"><span data-stu-id="85f26-117">If no filter is specified in **Filter tables**, all tables in the data source or data source view specified in **Look in** that are similar in structure to the fact table used by the measure group specified in **Measure group** are listed.</span></span>  
  
 <span data-ttu-id="85f26-118">如果在 **[篩選資料表]** 中有指定篩選，將藉由比較篩選與符合上述準則的資料表名稱，來進一步限制清單。</span><span class="sxs-lookup"><span data-stu-id="85f26-118">If a filter is specified in **Filter tables**, the list is further restricted by comparing the filter against the table names that meet the above criteria.</span></span> <span data-ttu-id="85f26-119">顯示只有包含 **[篩選資料表]** 中指定之字串的資料表。</span><span class="sxs-lookup"><span data-stu-id="85f26-119">Only those tables that contain the string specified in **Filter tables** are displayed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85f26-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="85f26-120">See Also</span></span>  
 [<span data-ttu-id="85f26-121">資料分割來源對話方塊 &#40;Analysis Services-多維度資料&#41;</span><span class="sxs-lookup"><span data-stu-id="85f26-121">Partition Source Dialog Box &#40;Analysis Services - Multidimensional Data&#41;</span></span>](partition-source-dialog-box-analysis-services-multidimensional-data.md)  
  
  
