---
title: " (分割區 Wizard) 指定來源資訊 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.partitionwizard.specifydsvandfacttables.f1
ms.assetid: b6c13587-c690-45d9-af90-b3d652afc55b
author: minewiskan
ms.author: owend
ms.openlocfilehash: 088a8abf7b143b68766f22af37f8ff4fa2065d65
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598549"
---
# <a name="specify-source-information-partition-wizard"></a><span data-ttu-id="70abe-102">指定來源資訊 (資料分割精靈)</span><span class="sxs-lookup"><span data-stu-id="70abe-102">Specify Source Information (Partition Wizard)</span></span>
  <span data-ttu-id="70abe-103">使用 [指定來源資訊]\*\*\*\* 頁面，即可選取要在其中建立資料分割 (以及該資料分割的資料來源檢視和篩選資料表) 的量值群組。</span><span class="sxs-lookup"><span data-stu-id="70abe-103">Use the **Specify Source Information** page to select the measure group in which to create the partition, and also the data source view and filter tables for your partition.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="70abe-104">如果您在另一個資料分割所用的 [可用的資料表]\*\*\*\* 中指定資料表，就必須在 [限制資料列]\*\*\*\* 頁面中提供查詢，或承擔 Cube 中有重複資料的風險。</span><span class="sxs-lookup"><span data-stu-id="70abe-104">If you specify a table in **Available Tables** that is used by another partition, you must provide a query in the **Restrict Rows** page or risk duplicating data in the cube.</span></span>  
  
## <a name="options"></a><span data-ttu-id="70abe-105">選項</span><span class="sxs-lookup"><span data-stu-id="70abe-105">Options</span></span>  
 <span data-ttu-id="70abe-106">**量值群組**</span><span class="sxs-lookup"><span data-stu-id="70abe-106">**Measure group**</span></span>  
 <span data-ttu-id="70abe-107">選取此分割區的量值群組。</span><span class="sxs-lookup"><span data-stu-id="70abe-107">Select a measure group for this partition.</span></span>  
  
 <span data-ttu-id="70abe-108">[查詢]\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="70abe-108">**Look in**</span></span>  
 <span data-ttu-id="70abe-109">選取包含此資料分割之來源資料表的資料來源或資料來源檢視。</span><span class="sxs-lookup"><span data-stu-id="70abe-109">Select the data source or data source view that contains the source tables for this partition.</span></span> <span data-ttu-id="70abe-110">依預設，會選取量值群組所用的資料來源檢視。</span><span class="sxs-lookup"><span data-stu-id="70abe-110">The data source view used by the measure group is selected by default.</span></span>  
  
 <span data-ttu-id="70abe-111">**篩選資料表**</span><span class="sxs-lookup"><span data-stu-id="70abe-111">**Filter tables**</span></span>  
 <span data-ttu-id="70abe-112">輸入用於 (依資料表名稱) 限制 [可用的資料表]\*\*\*\* 中顯示之資料表的字串。</span><span class="sxs-lookup"><span data-stu-id="70abe-112">Type the string used to restrict, by table name, the tables displayed in **Available tables**.</span></span>  
  
 <span data-ttu-id="70abe-113">**尋找資料表**</span><span class="sxs-lookup"><span data-stu-id="70abe-113">**Find tables**</span></span>  
 <span data-ttu-id="70abe-114">選取即可重新整理 [可用的資料表]\*\*\*\* 中的資料表清單，如果在 [篩選資料表]\*\*\*\* 中指定了字串，就可以進一步限制清單。</span><span class="sxs-lookup"><span data-stu-id="70abe-114">Select to refresh the list of tables in **Available tables**, further restricting the list if a string was specified in **Filter tables**.</span></span>  
  
 <span data-ttu-id="70abe-115">**可用的資料表**</span><span class="sxs-lookup"><span data-stu-id="70abe-115">**Available tables**</span></span>  
 <span data-ttu-id="70abe-116">選取用來作為資料分割之來源資料表的資料表。</span><span class="sxs-lookup"><span data-stu-id="70abe-116">Select the tables to use as source tables for partitions.</span></span> <span data-ttu-id="70abe-117">[資料分割精靈]\*\*\*\* 會為在 [可用的資料表]\*\*\*\* 中選取的每個資料表建立一個資料分割。</span><span class="sxs-lookup"><span data-stu-id="70abe-117">The **Partition Wizard** creates one partition for each table selected in **Available tables**.</span></span>  
  
 <span data-ttu-id="70abe-118">如果未在 [篩選資料表]\*\*\*\* 中指定篩選，此選項會列出在 [查詢]\*\*\*\* 中指定之資料來源或資料來源檢視中的所有資料表，其結構類似於在 [量值群組]\*\*\*\* 中指定之量值群組所用的事實資料表。</span><span class="sxs-lookup"><span data-stu-id="70abe-118">If no filter is specified in **Filter tables**, this option lists all tables in the data source or data source view that are specified in **Look in** and that are similar in structure to the fact table used by the measure group specified in **Measure group**.</span></span>  
  
 <span data-ttu-id="70abe-119">如果在 [篩選資料表]\*\*\*\* 中指定篩選，就會藉由比較篩選與符合先前準則的資料表名稱，來進一步限制此清單。</span><span class="sxs-lookup"><span data-stu-id="70abe-119">If a filter is specified in **Filter tables**, the list is further restricted by comparing the filter against the table names that meet the previous criteria.</span></span> <span data-ttu-id="70abe-120">顯示只有包含 **[篩選資料表]** 中指定之字串的資料表。</span><span class="sxs-lookup"><span data-stu-id="70abe-120">Only those tables that contain the string specified in **Filter tables** are displayed.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="70abe-121">如果選取一個以上的資料表，就無法顯示 [限制資料列]\*\*\*\* 頁面，而且無法限制從所選資料表建立之資料分割的資料列。</span><span class="sxs-lookup"><span data-stu-id="70abe-121">If more than one table is selected, the **Restrict Rows** page cannot be displayed and rows cannot be restricted for the partitions created from the selected tables.</span></span> <span data-ttu-id="70abe-122">若要限制每個資料分割的資料列，請為要建立資料分割的每個資料表執行一次資料分割精靈。</span><span class="sxs-lookup"><span data-stu-id="70abe-122">To restrict rows for each partition, run the Partition Wizard once for each table from which a partition is to be created.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70abe-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="70abe-123">See Also</span></span>  
 [<span data-ttu-id="70abe-124">資料分割 &#40;Analysis Services - 多維度資料&#41;</span><span class="sxs-lookup"><span data-stu-id="70abe-124">Partitions &#40;Analysis Services - Multidimensional Data&#41;</span></span>](multidimensional-models-olap-logical-cube-objects/partitions-analysis-services-multidimensional-data.md)  
  
  
