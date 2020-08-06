---
title: 定義篩選 | Microsoft 文件
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.replconflictviewer.definefilters.f1
helpviewer_keywords:
- Define Filters dialog box
ms.assetid: 1fa71d22-ce5a-4aae-ba05-4d755842aeac
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 5154f002c5a35bc78e2eb6777f2cc7bb3d56b635
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585883"
---
# <a name="define-filters"></a><span data-ttu-id="ed339-102">定義篩選</span><span class="sxs-lookup"><span data-stu-id="ed339-102">Define Filters</span></span>
  <span data-ttu-id="ed339-103">**[定義篩選]** 對話方塊可讓您定義篩選，然後套用至資料衝突，以在方格中檢視衝突的子集。</span><span class="sxs-lookup"><span data-stu-id="ed339-103">The **Define Filters** dialog box allows you to define filters that you then apply to data conflicts to see a subset of the conflicts in the grid.</span></span> <span data-ttu-id="ed339-104">若要定義篩選，請從 **[運算子]** 下拉式清單方塊選擇運算子，然後輸入一個值。</span><span class="sxs-lookup"><span data-stu-id="ed339-104">To define a filter, choose an operator from the **Operator** drop-down list box and then enter a value.</span></span> <span data-ttu-id="ed339-105">例如，若只要顯示衝突失敗者為 **ReplTest1**伺服器的衝突，請從 **[運算子]** 下拉式清單方塊選取 **[等於]** ，然後在 **[值]** 資料行輸入 **ReplTest1** 。</span><span class="sxs-lookup"><span data-stu-id="ed339-105">For example, to show only those conflicts in which the conflict loser is server **ReplTest1**, select **Equal to** from the **Operator** drop-down list box and enter **ReplTest1** in the first **Value** column.</span></span>  
  
## <a name="options"></a><span data-ttu-id="ed339-106">選項。</span><span class="sxs-lookup"><span data-stu-id="ed339-106">Options</span></span>  
 <span data-ttu-id="ed339-107">**運算子**</span><span class="sxs-lookup"><span data-stu-id="ed339-107">**Operator**</span></span>  
 <span data-ttu-id="ed339-108">選取篩選的運算子，例如 **[小於或等於]** 。</span><span class="sxs-lookup"><span data-stu-id="ed339-108">Select an operator for the filter, such as **Less than or Equal to**.</span></span>  
  
 <span data-ttu-id="ed339-109">**ReplTest1**</span><span class="sxs-lookup"><span data-stu-id="ed339-109">**Value**</span></span>  
 <span data-ttu-id="ed339-110">輸入篩選的值。</span><span class="sxs-lookup"><span data-stu-id="ed339-110">Enter a value for the filter.</span></span> <span data-ttu-id="ed339-111">大多數運算子只需要第一個 **[值]** 資料行的值，但 **[介於]** 和 **[不介於]** 運算子則需要兩個 **[值]** 資料行中都有值。</span><span class="sxs-lookup"><span data-stu-id="ed339-111">Most operators only require a value in the first **Value** column, but the **Between** and **Not Between** operators require a value in both of the **Value** columns.</span></span>  
  
 <span data-ttu-id="ed339-112">**Clear**</span><span class="sxs-lookup"><span data-stu-id="ed339-112">**Clear**</span></span>  
 <span data-ttu-id="ed339-113">按一下此按鈕即可清除先前已定義的所有篩選。</span><span class="sxs-lookup"><span data-stu-id="ed339-113">Click this button to clear all filters that have been previously defined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed339-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ed339-114">See Also</span></span>  
 <span data-ttu-id="ed339-115">[Microsoft 複寫衝突檢視器 &#40;合併式複寫&#41;](microsoft-replication-conflict-viewer-merge-replication.md) </span><span class="sxs-lookup"><span data-stu-id="ed339-115">[Microsoft Replication Conflict Viewer &#40;Merge Replication&#41;](microsoft-replication-conflict-viewer-merge-replication.md) </span></span>  
 [<span data-ttu-id="ed339-116">Microsoft 複寫衝突檢視器 &#40;異動複寫&#41;</span><span class="sxs-lookup"><span data-stu-id="ed339-116">Microsoft Replication Conflict Viewer &#40;Transactional Replication&#41;</span></span>](microsoft-replication-conflict-viewer-transactional-replication.md)  
  
  
