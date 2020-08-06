---
title: 排序資料行 | Microsoft 文件
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.monitor.sortcolumns.f1
ms.assetid: 66b44b6c-10a5-4e3f-a97b-7568609c88ac
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e5fe56688a009fd60a7731b199f32352d78bb5eb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710574"
---
# <a name="sort-columns"></a><span data-ttu-id="32e8e-102">排序資料行</span><span class="sxs-lookup"><span data-stu-id="32e8e-102">Sort Columns</span></span>
  <span data-ttu-id="32e8e-103">**[排序資料行]** 對話方塊可讓您根據一或多個資料行排序「複寫監視器」中的方格</span><span class="sxs-lookup"><span data-stu-id="32e8e-103">The **Sort Columns** dialog box lets you sort grids in Replication Monitor based on one or more columns.</span></span> <span data-ttu-id="32e8e-104">(您也可以按一下「複寫監視器」方格中的資料行標頭，針對單一資料行排序)。</span><span class="sxs-lookup"><span data-stu-id="32e8e-104">(You can also sort on a single column by clicking the column header in the Replication Monitor grid).</span></span> <span data-ttu-id="32e8e-105">例如，若要根據狀態和連接類型排序 **[所有訂閱]** 索引標籤中的訂閱，請遵循下列步驟進行：</span><span class="sxs-lookup"><span data-stu-id="32e8e-105">For example, to sort subscriptions on the **All Subscriptions** tab based on status and then connection type, follow these steps:</span></span>  
  
1.  <span data-ttu-id="32e8e-106">在方格的第一個資料列中，從 **[資料行名稱]** 資料行中選取 **[狀態]** ，然後從 **[排序順序]** 資料行中選取值。</span><span class="sxs-lookup"><span data-stu-id="32e8e-106">In the first row of the grid, select **Status** from the **Column Name** column and a value from the **Sort Order** column</span></span>  
  
2.  <span data-ttu-id="32e8e-107">在方格的第二個資料列中，從 **[資料行名稱]** 資料行中選取 **[連接類型]** ，然後從 **[排序順序]** 資料行中選取值。</span><span class="sxs-lookup"><span data-stu-id="32e8e-107">In the second row of the grid, select **Connection Type** from the **Column Name** column, and a value from the **Sort Order** column.</span></span>  
  
## <a name="options"></a><span data-ttu-id="32e8e-108">選項。</span><span class="sxs-lookup"><span data-stu-id="32e8e-108">Options</span></span>  
 <span data-ttu-id="32e8e-109">**資料行名稱**</span><span class="sxs-lookup"><span data-stu-id="32e8e-109">**Column Name**</span></span>  
 <span data-ttu-id="32e8e-110">您想要用來排序的資料行名稱。</span><span class="sxs-lookup"><span data-stu-id="32e8e-110">The name of the column on which you want to sort.</span></span> <span data-ttu-id="32e8e-111">您可以針對一或多個資料行進行排序。</span><span class="sxs-lookup"><span data-stu-id="32e8e-111">You can sort on one or more columns.</span></span> <span data-ttu-id="32e8e-112">不過，您無法針對 **[發行集]** 索引標籤上的 **[目前的平均效能]** 或 **[目前最差效能]** 資料行進行排序，因為這些資料行值的計算方式不同。</span><span class="sxs-lookup"><span data-stu-id="32e8e-112">You cannot sort on the **Current Average Performance** or **Current Worst Performance** columns on the **Publications** tab, because of the way in which these column values are calculated.</span></span>  
  
 <span data-ttu-id="32e8e-113">**排序次序**</span><span class="sxs-lookup"><span data-stu-id="32e8e-113">**Sort Order**</span></span>  
 <span data-ttu-id="32e8e-114">請指定 **[遞增]** 或 **[遞減]** 值。</span><span class="sxs-lookup"><span data-stu-id="32e8e-114">Specify a value of **Ascending** or **Descending**.</span></span>  
  
 <span data-ttu-id="32e8e-115">**全部清除**</span><span class="sxs-lookup"><span data-stu-id="32e8e-115">**Clear All**</span></span>  
 <span data-ttu-id="32e8e-116">從排序的方格中移除所有資料列。</span><span class="sxs-lookup"><span data-stu-id="32e8e-116">Remove all rows from the sorting grid.</span></span> <span data-ttu-id="32e8e-117">若要移除單一資料列，請選取該資料列並按下 Delete 鍵。</span><span class="sxs-lookup"><span data-stu-id="32e8e-117">To remove a single row, select the row and press the Delete key.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32e8e-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="32e8e-118">See Also</span></span>  
 [<span data-ttu-id="32e8e-119">監視複寫</span><span class="sxs-lookup"><span data-stu-id="32e8e-119">Monitoring Replication</span></span>](monitoring-replication.md)  
  
  
