---
title: 顯示並儲存執行計畫 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Showplan results
- execution plans [SQL Server]
- queries [SQL Server], tuning
- execution plans [SQL Server], how-to topics
- SQL Server Management Studio [SQL Server], execution plans
- tuning queries [SQL Server]
ms.assetid: bcd6f094-c613-4835-ae19-4caaadb4bb17
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: e236ed2a298bc8fc9a829948a864f6f5c27a2ba2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87698014"
---
# <a name="display-and-save-execution-plans"></a><span data-ttu-id="072f5-102">顯示並儲存執行計畫</span><span class="sxs-lookup"><span data-stu-id="072f5-102">Display and Save Execution Plans</span></span>
  <span data-ttu-id="072f5-103">本節將說明如何顯示執行計畫，以及如何使用 Microsoft [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]將執行計畫儲存到 XML 格式的檔案中。</span><span class="sxs-lookup"><span data-stu-id="072f5-103">This section explains how to display execution plans and how to save execution plans to a file in XML format by using Microsoft [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="072f5-104">執行計畫會以圖形化的方式，顯示 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 查詢最佳化工具所選擇的資料擷取方法。</span><span class="sxs-lookup"><span data-stu-id="072f5-104">Execution plans graphically display the data retrieval methods chosen by the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] query optimizer.</span></span> <span data-ttu-id="072f5-105">執行計畫會使用圖示來呈現 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中特定陳述式與查詢的執行成本，而不是使用 SET SHOWPLAN_ALL 或 SET SHOWPLAN_TEXT 陳述式所產生的表格呈現方式。</span><span class="sxs-lookup"><span data-stu-id="072f5-105">Execution plans represent the execution cost of specific statements and queries in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] using icons rather than the tabular representation produced by the SET SHOWPLAN_ALL or SET SHOWPLAN_TEXT statements.</span></span> <span data-ttu-id="072f5-106">這種圖形式的方法，對於了解查詢的效能特性非常有幫助。</span><span class="sxs-lookup"><span data-stu-id="072f5-106">This graphical approach is very useful for understanding the performance characteristics of a query.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="072f5-107">本節內容</span><span class="sxs-lookup"><span data-stu-id="072f5-107">In This Section</span></span>  
  
-   [<span data-ttu-id="072f5-108">顯示估計的執行計畫</span><span class="sxs-lookup"><span data-stu-id="072f5-108">Display the Estimated Execution Plan</span></span>](display-the-estimated-execution-plan.md)  
  
-   [<span data-ttu-id="072f5-109">顯示實際執行計畫</span><span class="sxs-lookup"><span data-stu-id="072f5-109">Display an Actual Execution Plan</span></span>](display-an-actual-execution-plan.md)  
  
-   [<span data-ttu-id="072f5-110">以 XML 格式儲存執行計畫</span><span class="sxs-lookup"><span data-stu-id="072f5-110">Save an Execution Plan in XML Format</span></span>](save-an-execution-plan-in-xml-format.md)  
  
  
