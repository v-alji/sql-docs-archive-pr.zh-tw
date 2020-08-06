---
title: 建立具有多維度資料來源的 Power View 報表 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: b9b6f4c9-7e1f-4f61-b657-8986e39a6af2
author: minewiskan
ms.author: owend
ms.openlocfilehash: 179bb9eed94cd0dbb579bdb06d630b213339d12f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705610"
---
# <a name="create-a-power-view-report-with-a-multidimensional-data-source"></a><span data-ttu-id="f0417-102">建立具有多維度資料來源的 Power View 報表</span><span class="sxs-lookup"><span data-stu-id="f0417-102">Create a Power View Report with a Multidimensional Data Source</span></span>
  <span data-ttu-id="f0417-103">根據多維度模型建立 Power View 報表與根據 PowerPivot 活頁簿或 Analysis Services 表格式模型建立報表並無不同之處。</span><span class="sxs-lookup"><span data-stu-id="f0417-103">Creating a Power View report based on a multidimensional model is no different than creating a report based on a PowerPivot workbook or an Analysis Services Tabular model.</span></span> <span data-ttu-id="f0417-104">Power View 報表是從 SharePoint 文件庫的報表資料來源連接檔案 (.rsds) 建立。</span><span class="sxs-lookup"><span data-stu-id="f0417-104">Power View reports are created from a Report Data Source connection file (.rsds) in a SharePoint library.</span></span> <span data-ttu-id="f0417-105">如需如何建立 .rsds 的詳細資訊，請參閱 [建立報表資料來源](create-a-report-data-source.md)。</span><span class="sxs-lookup"><span data-stu-id="f0417-105">For more information about how to create an .rsds, see [Create a Report Data Source](create-a-report-data-source.md).</span></span>  
  
 <span data-ttu-id="f0417-106">在開始進行之前，您需要先了解：</span><span class="sxs-lookup"><span data-stu-id="f0417-106">Before you begin, you need to know:</span></span>  
  
-   <span data-ttu-id="f0417-107">包含多維度模型之共用報表資料來源連接 (.rsds) 的 SharePoint 文件庫名稱和位置。</span><span class="sxs-lookup"><span data-stu-id="f0417-107">The name and location of the SharePoint library that contains a shared report data source connection (.rsds) to a multidimensional model.</span></span>  
  
#### <a name="create-a-new-blank-power-view-report"></a><span data-ttu-id="f0417-108">建立新的空白 Power View 報表</span><span class="sxs-lookup"><span data-stu-id="f0417-108">Create a new, blank Power View report</span></span>  
  
-   <span data-ttu-id="f0417-109">在 SharePoint 文件庫中，按一下 .rsds 共用報表資料來源連接 (連接到多維度模型的 .rsds) 旁邊的箭頭，然後按一下 [建立 Power View 報表]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f0417-109">In the SharePoint library, click the arrow next to the .rsds shared report data source connection (the .rsds that connects to the multidimensional model), and then click **Create Power View Report**.</span></span>  
  
  
