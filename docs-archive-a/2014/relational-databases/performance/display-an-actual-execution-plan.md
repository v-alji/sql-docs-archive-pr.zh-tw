---
title: 顯示實際執行計畫 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- displaying execution plans
- actual execution plans
- viewing execution plans
- execution plans [SQL Server], displaying
ms.assetid: 9e583a18-5f4a-4054-bfe1-4b2a76630db6
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: f384e2d2752b7601fbb46b8ee7f7b56a2615651c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87698005"
---
# <a name="display-an-actual-execution-plan"></a><span data-ttu-id="28c11-102">顯示實際執行計畫</span><span class="sxs-lookup"><span data-stu-id="28c11-102">Display an Actual Execution Plan</span></span>
  <span data-ttu-id="28c11-103">此主題描述如何使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]產生實際的圖形執行計畫。</span><span class="sxs-lookup"><span data-stu-id="28c11-103">This topic describes how to generate actual graphical execution plans by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="28c11-104">產生實際執行計畫後，就會執行 [!INCLUDE[tsql](../../includes/tsql-md.md)] 查詢或批次。</span><span class="sxs-lookup"><span data-stu-id="28c11-104">When actual execution plans are generated, the [!INCLUDE[tsql](../../includes/tsql-md.md)] queries or batches execute.</span></span> <span data-ttu-id="28c11-105">所產生的執行計畫會顯示實際查詢執行計畫， [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 將用來執行查詢。</span><span class="sxs-lookup"><span data-stu-id="28c11-105">The execution plan that is generated displays the actual query execution plan that the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] uses to execute the queries.</span></span>  
  
 <span data-ttu-id="28c11-106">若要使用這個功能，使用者必須具有適當權限，以便執行將會產生圖形執行計畫的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 查詢，同時也需將查詢所參考之所有資料庫的 SHOWPLAN 權限，都授與給使用者。</span><span class="sxs-lookup"><span data-stu-id="28c11-106">To use this feature, users must have the appropriate permissions to execute the [!INCLUDE[tsql](../../includes/tsql-md.md)] queries for which a graphical execution plan is being generated, and they must be granted the SHOWPLAN permission for all databases referenced by the query.</span></span>  
  
### <a name="to-include-an-execution-plan-for-a-query-during-execution"></a><span data-ttu-id="28c11-107">若要在執行期間包括查詢的執行計畫</span><span class="sxs-lookup"><span data-stu-id="28c11-107">To include an execution plan for a query during execution</span></span>  
  
1.  <span data-ttu-id="28c11-108">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 工具列上，按一下 [Database Engine 查詢]。</span><span class="sxs-lookup"><span data-stu-id="28c11-108">On the [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] toolbar, click **Database Engine Query**.</span></span> <span data-ttu-id="28c11-109">您也可以按一下 [開啟檔案] 工具列按鈕並找出現有的查詢，以開啟現有的查詢並顯示估計的執行計畫。</span><span class="sxs-lookup"><span data-stu-id="28c11-109">You can also open an existing query and display the estimated execution plan by clicking the **Open File** toolbar button and locating the existing query.</span></span>  
  
2.  <span data-ttu-id="28c11-110">輸入您希望顯示其實際執行計畫的查詢。</span><span class="sxs-lookup"><span data-stu-id="28c11-110">Enter the query for which you would like to display the actual execution plan.</span></span>  
  
3.  <span data-ttu-id="28c11-111">在 [**查詢**] 功能表上，按一下 [**包括實際執行計畫**]，或按一下 [**包括實際執行計畫**] 工具列按鈕</span><span class="sxs-lookup"><span data-stu-id="28c11-111">On the **Query** menu, click **Include Actual Execution Plan** or click the **Include Actual Execution Plan** toolbar button</span></span>  
  
4.  <span data-ttu-id="28c11-112">按一下 [執行] 工具列按鈕執行查詢。</span><span class="sxs-lookup"><span data-stu-id="28c11-112">Execute the query by clicking the **Execute** toolbar button.</span></span> <span data-ttu-id="28c11-113">查詢最佳化工具所使用的計畫，會顯示在結果窗格的 [執行計畫] 索引標籤上。</span><span class="sxs-lookup"><span data-stu-id="28c11-113">The plan used by the query optimizer is displayed on the **Execution Plan** tab in the results pane.</span></span> <span data-ttu-id="28c11-114">將滑鼠游標暫時放在邏輯與實體運算子上，即可在顯示的 [工具提示] 中檢視運算子的說明與屬性。</span><span class="sxs-lookup"><span data-stu-id="28c11-114">Pause the mouse over the logical and physical operators to view the description and properties of the operators in the displayed ToolTip.</span></span>  
  
     <span data-ttu-id="28c11-115">或者，您可以在 [屬性] 視窗中檢視運算子屬性。</span><span class="sxs-lookup"><span data-stu-id="28c11-115">Alternatively, you can view operator properties in the Properties window.</span></span> <span data-ttu-id="28c11-116">如果沒有看到 [屬性] 視窗，請以滑鼠右鍵按一下運算子，然後選取 [屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="28c11-116">If Properties is not visible, right-click an operator and select **Properties**.</span></span> <span data-ttu-id="28c11-117">選取運算子以檢視其屬性。</span><span class="sxs-lookup"><span data-stu-id="28c11-117">Select an operator to view its properties.</span></span>  
  
5.  <span data-ttu-id="28c11-118">您可以用滑鼠右鍵按一下執行計畫，然後選取 [放大]、[縮小]、[自訂顯示比例] 或 [縮放至適當比例]，來改變執行計畫的顯示。</span><span class="sxs-lookup"><span data-stu-id="28c11-118">You can alter the display of the execution plan by right-clicking the execution plan and selecting **Zoom In**, **Zoom Out**, **Custom Zoom**, or **Zoom to Fit**.</span></span> <span data-ttu-id="28c11-119">[放大] 及 [縮小] 可讓您放大或縮小執行計畫，而 [自訂顯示比例] 則可讓您定義自己的顯示比例，如 80% 的顯示比例。</span><span class="sxs-lookup"><span data-stu-id="28c11-119">**Zoom In** and **Zoom Out** allow you to zoom in or out on the execution plan, while **Custom Zoom** allows you to define your own zoom, such as zooming at 80 percent.</span></span> <span data-ttu-id="28c11-120">[縮放至適當比例] 會放大執行計畫，以符合結果窗格的大小。</span><span class="sxs-lookup"><span data-stu-id="28c11-120">**Zoom to Fit** magnifies the execution plan to fit the result pane.</span></span>  
  
  
