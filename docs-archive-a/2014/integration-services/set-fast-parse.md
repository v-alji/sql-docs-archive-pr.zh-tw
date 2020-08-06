---
title: 設定快速剖析 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: dcd1dc09-6eaf-440b-9ce6-fef779ff794f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e6ff2c6ecd536dd5ecc34dceb358ffcf578ff3a7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584641"
---
# <a name="set-fast-parse"></a><span data-ttu-id="b77c2-102">設定快速剖析</span><span class="sxs-lookup"><span data-stu-id="b77c2-102">Set Fast Parse</span></span>
  <span data-ttu-id="b77c2-103">使用快速剖析的來源或轉換，其每一個資料行都必須設定快速剖析屬性。</span><span class="sxs-lookup"><span data-stu-id="b77c2-103">The fast parse property must be set for each column of the source or transformation that uses fast parse.</span></span> <span data-ttu-id="b77c2-104">若要設定屬性，請使用「一般檔案」來源或「資料轉換」的進階編輯器。</span><span class="sxs-lookup"><span data-stu-id="b77c2-104">To set the property, use the Advanced editor of the Flat File source and Data Conversion transformation.</span></span>  
  
### <a name="to-set-fast-parse"></a><span data-ttu-id="b77c2-105">設定快速剖析</span><span class="sxs-lookup"><span data-stu-id="b77c2-105">To set fast parse</span></span>  
  
1.  <span data-ttu-id="b77c2-106">以滑鼠右鍵按一下 [一般檔案] 來源或 [資料轉換]，然後按一下 [顯示進階編輯器]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b77c2-106">Right-click the Flat File source or Data Conversion transformation, and then click **Show Advanced Editor**.</span></span>  
  
2.  <span data-ttu-id="b77c2-107">按一下 **[進階編輯器]** 對話方塊中的 **[輸入與輸出屬性]** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="b77c2-107">In the **Advanced Editor** dialog box, click the **Input and Output Properties** tab.</span></span>  
  
3.  <span data-ttu-id="b77c2-108">在 **[輸入及輸出]** 窗格中，按一下您要啟用快速剖析的資料行。</span><span class="sxs-lookup"><span data-stu-id="b77c2-108">In the **Inputs and Outputs** pane, click the column for which you want to enable fast parse.</span></span>  
  
4.  <span data-ttu-id="b77c2-109">在 [屬性視窗中，展開 [**自訂屬性**] 節點，然後將 `FastParse` 屬性設定為 `True` 。</span><span class="sxs-lookup"><span data-stu-id="b77c2-109">In the Properties window, expand the **Custom Properties** node, and then set the `FastParse` property to `True`.</span></span>  
  
5.  <span data-ttu-id="b77c2-110">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="b77c2-110">Click **OK**.</span></span>  
  
  
