---
title: 活動監視器 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Activity Monitor [SQL Server]
ms.assetid: 1e6c430d-3a2a-468e-a3d5-ef5459c36c15
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 71fd0d1172b4fcd5739a3af1a60246cc7dce3b93
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707414"
---
# <a name="activity-monitor"></a><span data-ttu-id="0ee36-102">活動監視器</span><span class="sxs-lookup"><span data-stu-id="0ee36-102">Activity Monitor</span></span>
  <span data-ttu-id="0ee36-103">活動監視器顯示有關 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 處理序以及這些處理序如何影響目前 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]執行個體的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="0ee36-103">Activity Monitor displays information about [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] processes and how these processes affect the current instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="benefits-of-activity-monitor"></a><span data-ttu-id="0ee36-104">活動監視器的優點</span><span class="sxs-lookup"><span data-stu-id="0ee36-104">Benefits of Activity Monitor</span></span>  
 <span data-ttu-id="0ee36-105">活動監視器是一個索引標籤式文件視窗，具有下列可擴充且可折迭的窗格：**總覽**、作用中**使用者**工作、**資源等候**、**資料檔案 i/o**和**最近的昂貴查詢**。</span><span class="sxs-lookup"><span data-stu-id="0ee36-105">Activity Monitor is a tabbed document window that has the following expandable and collapsible panes: **Overview**, **Active User Tasks**, **Resource Waits**, **Data File I/O**, and **Recent Expensive Queries**.</span></span> <span data-ttu-id="0ee36-106">展開任何窗格時，活動監視器會查詢執行個體以便取得相關資訊。</span><span class="sxs-lookup"><span data-stu-id="0ee36-106">When any pane is expanded, Activity Monitor queries the instance for information.</span></span> <span data-ttu-id="0ee36-107">摺疊某個窗格時，該窗格的所有查詢活動就會停止。</span><span class="sxs-lookup"><span data-stu-id="0ee36-107">When a pane is collapsed, all querying activity stops for that pane.</span></span> <span data-ttu-id="0ee36-108">您也可以同時展開一或多個窗格，以便檢視不同種類的執行個體活動。</span><span class="sxs-lookup"><span data-stu-id="0ee36-108">You can also expand one or more panes at the same time to view different kinds of activity on the instance.</span></span>  
  
 <span data-ttu-id="0ee36-109">針對 [作用中**使用者**工作]、[**資源等候**]、[**資料檔案 i/o**] 和 [最近的**昂貴查詢**] 窗格中所包含的資料行，您可以透過下列方式自訂顯示：</span><span class="sxs-lookup"><span data-stu-id="0ee36-109">For the columns that are included in the **Active User Tasks**, **Resource Waits**, **Data File I/O**, and **Recent Expensive Queries** panes, you can customize the display in the following ways:</span></span>  
  
1.  <span data-ttu-id="0ee36-110">若要重新排列資料行的順序，請按一下資料行標題並將它拖曳至標題功能區中的其他位置。</span><span class="sxs-lookup"><span data-stu-id="0ee36-110">To rearrange the order of the columns, click the column heading and drag it to another location in the heading ribbon.</span></span>  
  
2.  <span data-ttu-id="0ee36-111">若要排序資料行，請按一下資料行名稱。</span><span class="sxs-lookup"><span data-stu-id="0ee36-111">To sort a column, click the column name.</span></span>  
  
3.  <span data-ttu-id="0ee36-112">若要篩選一個或多個資料行，請按一下資料行標題中的下拉式箭頭，然後選取一個值。</span><span class="sxs-lookup"><span data-stu-id="0ee36-112">To filter on one or more columns, click the drop-down arrow in the column heading, and then select a value.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="0ee36-113">相關工作</span><span class="sxs-lookup"><span data-stu-id="0ee36-113">Related Tasks</span></span>  
 <span data-ttu-id="0ee36-114">若要開始使用 [活動監視器]，請使用下列工作：</span><span class="sxs-lookup"><span data-stu-id="0ee36-114">Use the following tasks to get started with Activity Monitor:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="0ee36-115">**說明**</span><span class="sxs-lookup"><span data-stu-id="0ee36-115">**Description**</span></span>|<span data-ttu-id="0ee36-116">**主題**</span><span class="sxs-lookup"><span data-stu-id="0ee36-116">**Topic**</span></span>|  
|<span data-ttu-id="0ee36-117">描述如何開啟 [活動監視器] 以及如何設定 [活動監視器] 的重新整理間隔。</span><span class="sxs-lookup"><span data-stu-id="0ee36-117">Describes how to open Activity Monitor and how to set the Activity Monitor refresh interval.</span></span>|[<span data-ttu-id="0ee36-118">開啟活動監視器 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="0ee36-118">Open Activity Monitor &#40;SQL Server Management Studio&#41;</span></span>](../performance-monitor/open-activity-monitor-sql-server-management-studio.md)|  
|<span data-ttu-id="0ee36-119">伺服器效能和活動監視主題的連結。</span><span class="sxs-lookup"><span data-stu-id="0ee36-119">Links to topics for server performance and activity monitoring.</span></span>|[<span data-ttu-id="0ee36-120">伺服器效能與活動監視</span><span class="sxs-lookup"><span data-stu-id="0ee36-120">Server Performance and Activity Monitoring</span></span>](../performance/server-performance-and-activity-monitoring.md)|  
  
  
