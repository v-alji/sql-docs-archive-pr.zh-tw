---
title: 變更資料分割來源以使用不同的事實資料表 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- fact tables [Analysis Services]
- partitions [Analysis Services], fact tables
ms.assetid: 5508312f-8e46-4802-9362-6688ca03d098
author: minewiskan
ms.author: owend
ms.openlocfilehash: 0063a6023d769dc6dccd616655d10e0bd3c65a98
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705678"
---
# <a name="change-a-partition-source-to-use-a-different-fact-table"></a><span data-ttu-id="d3984-102">變更分割區來源以使用不同的事實資料表</span><span class="sxs-lookup"><span data-stu-id="d3984-102">Change a partition source to use a different fact table</span></span>
  <span data-ttu-id="d3984-103">當您建立 Cube 的分割區時，您可以選擇要使用不同的事實資料表。</span><span class="sxs-lookup"><span data-stu-id="d3984-103">When you create a partition for a cube, you can choose to use a different fact table.</span></span> <span data-ttu-id="d3984-104">不同資料表可能來自單一資料來源檢視、來自不同資料來源檢視或來自不同資料來源。</span><span class="sxs-lookup"><span data-stu-id="d3984-104">Different tables may be from a single data source view, from different data source views, or from different data sources.</span></span> <span data-ttu-id="d3984-105">資料來源檢視也可能包含來自一個以上之資料來源的不同資料表。</span><span class="sxs-lookup"><span data-stu-id="d3984-105">A data source view may also contain different tables from more than one data source.</span></span>  
  
 <span data-ttu-id="d3984-106">Cube 分割區的所有事實資料表與維度，必須和 Cube 的事實資料表與維度具有相同結構。</span><span class="sxs-lookup"><span data-stu-id="d3984-106">All fact tables and dimensions for a cube's partitions must have the same structure as the fact table and dimensions of the cube.</span></span> <span data-ttu-id="d3984-107">例如，不同的事實資料表可以有相同結構但包含不同年份或不同產品線的資料。</span><span class="sxs-lookup"><span data-stu-id="d3984-107">For example, different fact tables can have the same structure but contain data for different years or different product lines.</span></span>  
  
 <span data-ttu-id="d3984-108">您可以在分割區精靈的 [指定來源資訊]\*\*\*\* 頁面上，指定事實資料表。</span><span class="sxs-lookup"><span data-stu-id="d3984-108">You specify a fact table on the **Specify Source Information** page of the Partition Wizard.</span></span> <span data-ttu-id="d3984-109">在這個頁面上，於 [查詢]\*\*\*\* 旁邊的分割區來源群組中，指定要查看的資料來源或資料來源檢視。</span><span class="sxs-lookup"><span data-stu-id="d3984-109">On this page, in the Partition Source group next to **Look in**, specify a data source or data source view in which to look.</span></span> <span data-ttu-id="d3984-110">接下來，按一下 [尋找資料表]\*\*\*\*，然後在 [可用的資料表]\*\*\*\* 之下，選取您要使用的資料表。</span><span class="sxs-lookup"><span data-stu-id="d3984-110">Next, click **Find Tables**, and then, under **Available Tables**, select the table you want to use.</span></span>  
  
 <span data-ttu-id="d3984-111">當您使用不同的事實資料表時，請確定分割區之間沒有重複資料。</span><span class="sxs-lookup"><span data-stu-id="d3984-111">When you use different fact tables, ensure that no data is duplicated among the partitions.</span></span> <span data-ttu-id="d3984-112">例如，若有一個事實資料表只包含 2012 的交易，而另一個事實資料表只包含 2013 的交易，則這些資料表包含獨立資料。</span><span class="sxs-lookup"><span data-stu-id="d3984-112">For example, if one fact table contains transactions for 2012 only, and another fact table contains transactions for 2013 only, these tables contain independent data.</span></span> <span data-ttu-id="d3984-113">同樣地，不同產品線或不同地理區域的事實資料表也是獨立的。</span><span class="sxs-lookup"><span data-stu-id="d3984-113">Similarly, fact tables for distinct product lines or distinct geographical areas are independent.</span></span>  
  
 <span data-ttu-id="d3984-114">您可以 (但不建議) 使用包含重複資料的不同事實資料表。</span><span class="sxs-lookup"><span data-stu-id="d3984-114">It is possible, but not recommended, to use different fact tables that contain duplicated data.</span></span> <span data-ttu-id="d3984-115">在此情況下，您必須在資料分割中使用篩選來確保某資料分割使用的資料不會被另一個資料分割使用。</span><span class="sxs-lookup"><span data-stu-id="d3984-115">In this case, you must use filters in the partitions to ensure that data used by one partition is not used by any other partition.</span></span> <span data-ttu-id="d3984-116">如需詳細資訊，請參閱 [建立及管理本機分割區 &#40;Analysis Services&#41;](create-and-manage-a-local-partition-analysis-services.md)。</span><span class="sxs-lookup"><span data-stu-id="d3984-116">For more information, see [Create and Manage a Local Partition &#40;Analysis Services&#41;](create-and-manage-a-local-partition-analysis-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3984-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d3984-117">See Also</span></span>  
 [<span data-ttu-id="d3984-118">建立及管理本機資料分割 &#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="d3984-118">Create and Manage a Local Partition &#40;Analysis Services&#41;</span></span>](create-and-manage-a-local-partition-analysis-services.md)  
  
  
