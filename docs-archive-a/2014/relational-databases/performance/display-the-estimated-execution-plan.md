---
title: 顯示估計的執行計畫 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- zoom [SQL Server]
- estimated execution plan [SQL Server]
- displaying execution plans
- viewing execution plans
- execution plans [SQL Server], displaying
- customizing execution plan display [SQL Server]
- modifying execution plan display
- custom zoom [SQL Server]
ms.assetid: e94aa576-4c0c-4c54-ad05-6c3432cc615b
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 79c0972661d40eb9e359cf43f7a1f0b1b2ae4b0c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87697987"
---
# <a name="display-the-estimated-execution-plan"></a><span data-ttu-id="3fc4d-102">顯示估計的執行計畫</span><span class="sxs-lookup"><span data-stu-id="3fc4d-102">Display the Estimated Execution Plan</span></span>
  <span data-ttu-id="3fc4d-103">此主題描述如何使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]產生圖形化的估計執行計畫。</span><span class="sxs-lookup"><span data-stu-id="3fc4d-103">This topic describes how to generate graphical estimated execution plans by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="3fc4d-104">產生估計執行計畫時，不會執行 [!INCLUDE[tsql](../../includes/tsql-md.md)] 查詢或批次。</span><span class="sxs-lookup"><span data-stu-id="3fc4d-104">When estimated execution plans are generated, the [!INCLUDE[tsql](../../includes/tsql-md.md)] queries or batches do not execute.</span></span> <span data-ttu-id="3fc4d-105">不過，所產生的執行計畫會顯示若是真的執行查詢， [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 最有可能使用的查詢執行計畫。</span><span class="sxs-lookup"><span data-stu-id="3fc4d-105">Instead, the execution plan that is generated displays the query execution plan that [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] would most probably use if the queries were actually executed.</span></span>  
  
 <span data-ttu-id="3fc4d-106">若要使用這個功能，使用者必須具有適當的權限來執行要產生圖形執行計畫的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 查詢，而且必須獲得查詢所參考的所有資料庫的 SHOWPLAN 權限。</span><span class="sxs-lookup"><span data-stu-id="3fc4d-106">To use this feature, users must have the appropriate permissions to execute the [!INCLUDE[tsql](../../includes/tsql-md.md)] query for which a graphical execution plan is being generated, and they must be granted the SHOWPLAN permission for all databases referenced by the query.</span></span>  
  
### <a name="to-display-the-estimated-execution-plan-for-a-query"></a><span data-ttu-id="3fc4d-107">若要顯示查詢的評估執行計畫</span><span class="sxs-lookup"><span data-stu-id="3fc4d-107">To display the estimated execution plan for a query</span></span>  
  
1.  <span data-ttu-id="3fc4d-108">在工具列上，按一下 [Database Engine 查詢]。</span><span class="sxs-lookup"><span data-stu-id="3fc4d-108">On the toolbar, click **Database Engine Query**.</span></span> <span data-ttu-id="3fc4d-109">您也可以按一下 [開啟檔案] 工具列按鈕並找出現有的查詢，以開啟現有的查詢並顯示估計的執行計畫。</span><span class="sxs-lookup"><span data-stu-id="3fc4d-109">You can also open an existing query and display the estimated execution plan by clicking the **Open File** toolbar button and locating the existing query.</span></span>  
  
2.  <span data-ttu-id="3fc4d-110">輸入您要顯示估計執行計畫的查詢。</span><span class="sxs-lookup"><span data-stu-id="3fc4d-110">Enter the query for which you would like to display the estimated execution plan.</span></span>  
  
3.  <span data-ttu-id="3fc4d-111">在 [查詢] 功能表上，按一下 [顯示估計執行計畫]，或按一下 [顯示估計執行計畫] 工具列按鈕。</span><span class="sxs-lookup"><span data-stu-id="3fc4d-111">On the **Query** menu, click **Display Estimated Execution Plan** or click the **Display Estimated Execution Plan** toolbar button.</span></span> <span data-ttu-id="3fc4d-112">估計執行計畫會顯示在結果窗格中的 [執行計畫] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="3fc4d-112">The estimated execution plan is displayed on the **Execution Plan** tab in the results pane.</span></span> <span data-ttu-id="3fc4d-113">若要檢視其他資訊，請將滑鼠暫時放在邏輯與實體運算子的圖示上，即可在顯示的 [工具提示] 中檢視運算子的說明與屬性。</span><span class="sxs-lookup"><span data-stu-id="3fc4d-113">To view additional information, pause the mouse over the logical and physical operator icons and view the description and properties of the operator in the displayed ToolTip.</span></span> <span data-ttu-id="3fc4d-114">或者，您可以在 [屬性] 視窗中檢視運算子屬性。</span><span class="sxs-lookup"><span data-stu-id="3fc4d-114">Alternatively, you can view operator properties in the Properties window.</span></span> <span data-ttu-id="3fc4d-115">如果沒有看到 [屬性] 視窗，請以滑鼠右鍵按一下運算子，然後按一下 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="3fc4d-115">If Properties is not visible, right-click an operator and click **Properties**.</span></span> <span data-ttu-id="3fc4d-116">選取運算子以檢視其屬性。</span><span class="sxs-lookup"><span data-stu-id="3fc4d-116">Select an operator to view its properties.</span></span>  
  
4.  <span data-ttu-id="3fc4d-117">若要改變執行計劃的顯示，請以滑鼠右鍵按一下 [執行計畫]，然後選取 [放大]、[縮小]、[自訂顯示比例] 或 [縮放至適當比例]。</span><span class="sxs-lookup"><span data-stu-id="3fc4d-117">To alter the display of the execution plan, right-click the execution plan and select **Zoom In**, **Zoom Out**, **Custom Zoom**, or **Zoom to Fit**.</span></span> <span data-ttu-id="3fc4d-118">[放大] 與 [縮小] 可讓您以固定量放大或縮小執行計畫。</span><span class="sxs-lookup"><span data-stu-id="3fc4d-118">**Zoom In** and **Zoom Out** allow you to magnify or reduce the execution plan by fixed amounts.</span></span> <span data-ttu-id="3fc4d-119">[自訂顯示比例] 可讓您定義自己的顯示倍率，例如縮放至百分之 80。</span><span class="sxs-lookup"><span data-stu-id="3fc4d-119">**Custom Zoom** allows you to define your own display magnification, such as zooming at 80 percent.</span></span> <span data-ttu-id="3fc4d-120">[縮放至適當比例] 會放大執行計畫，以符合結果窗格的大小。</span><span class="sxs-lookup"><span data-stu-id="3fc4d-120">**Zoom to Fit** magnifies the execution plan to fit the result pane.</span></span>  
  
  
