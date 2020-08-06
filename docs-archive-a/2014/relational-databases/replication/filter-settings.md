---
title: 篩選設定 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.monitor.filtersettings.f1
ms.assetid: 1b401d7d-db8a-4ba1-acb1-b8dec14e3311
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d82d5f38eb460f392f1eb2ed3387ce3d97757db5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585844"
---
# <a name="filter-settings"></a><span data-ttu-id="1d914-102">篩選設定</span><span class="sxs-lookup"><span data-stu-id="1d914-102">Filter Settings</span></span>
  <span data-ttu-id="1d914-103">**[篩選設定]** 對話方塊可讓您針對「複寫監視器」中的方格定義篩選。</span><span class="sxs-lookup"><span data-stu-id="1d914-103">The **Filter Settings** dialog box lets you define filters for grids in Replication Monitor.</span></span> <span data-ttu-id="1d914-104">例如，若只要顯示在 **[所有訂閱]** 索引標籤中處於使用中狀態的訂閱，請依序選取 **[資料行名稱]** 資料行中的 **[狀態]** 、 **[運算子]** 資料行中的 **[等於]** ，以及 **[值1]** 資料行中的 **[使用中]** 。</span><span class="sxs-lookup"><span data-stu-id="1d914-104">For example, to show only those subscriptions that are active on the **All Subscriptions** tab, select **Status** from the **Column Name** column, **Equals** from the **Operator** column, and **Active** from the **Value1** column.</span></span> <span data-ttu-id="1d914-105">在您定義以一個或多個資料行為基礎的篩選之後，系統便套用此篩選，如此方格就只會顯示符合篩選準則的資料列子集。</span><span class="sxs-lookup"><span data-stu-id="1d914-105">After you define a filter that is based one or more columns, the filter is applied so that the grid displays only the subset of rows that match the filter criteria.</span></span>  
  
## <a name="options"></a><span data-ttu-id="1d914-106">選項。</span><span class="sxs-lookup"><span data-stu-id="1d914-106">Options</span></span>  
 <span data-ttu-id="1d914-107">**資料行名稱**</span><span class="sxs-lookup"><span data-stu-id="1d914-107">**Column Name**</span></span>  
 <span data-ttu-id="1d914-108">選取您想要用來篩選的資料行名稱。</span><span class="sxs-lookup"><span data-stu-id="1d914-108">Select the name of the column on which you want to filter.</span></span> <span data-ttu-id="1d914-109">您可以讓篩選以一個或多個資料行為基礎。</span><span class="sxs-lookup"><span data-stu-id="1d914-109">You can base a filter on one or more columns.</span></span>  
  
 <span data-ttu-id="1d914-110">**運算子**</span><span class="sxs-lookup"><span data-stu-id="1d914-110">**Operator**</span></span>  
 <span data-ttu-id="1d914-111">選取篩選的運算子，例如 **[小於或等於]** 。</span><span class="sxs-lookup"><span data-stu-id="1d914-111">Select an operator for the filter, such as **Less than or Equal to**.</span></span>  
  
 <span data-ttu-id="1d914-112">**值1** 和 **值2**</span><span class="sxs-lookup"><span data-stu-id="1d914-112">**Value1** and **Value2**</span></span>  
 <span data-ttu-id="1d914-113">輸入或選取篩選的值。</span><span class="sxs-lookup"><span data-stu-id="1d914-113">Enter or select a value for the filter.</span></span> <span data-ttu-id="1d914-114">大部分運算子只需要 **[值1]** 資料行的值，但 **[介於]** 和 **[不介於]** 運算子則需要 **[值2]** 資料行的值。</span><span class="sxs-lookup"><span data-stu-id="1d914-114">Most operators only require a value in the **Value1** column, but the **Between** and **Not Between** operators also require a value in the **Value2** column.</span></span>  
  
 <span data-ttu-id="1d914-115">**清除篩選**</span><span class="sxs-lookup"><span data-stu-id="1d914-115">**Clear Filter**</span></span>  
 <span data-ttu-id="1d914-116">按一下此按鈕即可清除已定義的所有篩選。</span><span class="sxs-lookup"><span data-stu-id="1d914-116">Click this button to clear all filters that have been defined.</span></span> <span data-ttu-id="1d914-117">若要移除單一篩選，請選取篩選資料列並按下 Delete 鍵。</span><span class="sxs-lookup"><span data-stu-id="1d914-117">To remove a single filter, select the filter row and press the Delete key.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d914-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1d914-118">See Also</span></span>  
 [<span data-ttu-id="1d914-119">監視複寫</span><span class="sxs-lookup"><span data-stu-id="1d914-119">Monitoring Replication</span></span>](monitoring-replication.md)  
  
  
