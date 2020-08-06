---
title: PowerPivot 資料重新整理 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- unattended data refresh [Analysis Services with SharePoint]
- scheduled data refresh [Analysis Services with SharePoint]
- data refresh [Analysis Services with SharePoint]
ms.assetid: ac8358a3-ee71-44c7-8ee6-ac7afe3ebaa4
author: minewiskan
ms.author: owend
ms.openlocfilehash: 6f7d5ed5c2f8882cbc0c47a1c711748d26e0193c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596331"
---
# <a name="powerpivot-data-refresh"></a><span data-ttu-id="0210c-102">PowerPivot 資料重新整理</span><span class="sxs-lookup"><span data-stu-id="0210c-102">PowerPivot Data Refresh</span></span>
  <span data-ttu-id="0210c-103">在建立包含 PowerPivot 資料的活頁簿之後，您可能會想要定期重新整理資料，其方式是重新執行查詢或命令，以取得您原先用來建立活頁簿之來源的更新資訊。</span><span class="sxs-lookup"><span data-stu-id="0210c-103">After you create a workbook that contains PowerPivot data, you might want to periodically refresh the data by rerunning a query or command to get updated information from the sources you used originally to create the workbook.</span></span> <span data-ttu-id="0210c-104">此處理序稱為 `data refresh`，而且您可以在 [!INCLUDE[ssGeminiClient](../../includes/ssgeminiclient-md.md)] 中視需要重新整理資料，或是將其當做已排程的作業，在 SharePoint 伺服器陣列中的應用程式伺服器上，以 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 處理序的方式執行。</span><span class="sxs-lookup"><span data-stu-id="0210c-104">This process is called `data refresh`, and you can refresh data on demand in [!INCLUDE[ssGeminiClient](../../includes/ssgeminiclient-md.md)], or as a scheduled operation that runs as an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] process on an application server in a SharePoint farm.</span></span> <span data-ttu-id="0210c-105">如需詳細資訊，請參閱</span><span class="sxs-lookup"><span data-stu-id="0210c-105">For more information, see:</span></span>  
  
-   [<span data-ttu-id="0210c-106">SharePoint 2010 中的 PowerPivot 資料重新整理</span><span class="sxs-lookup"><span data-stu-id="0210c-106">PowerPivot Data Refresh with SharePoint 2010</span></span>](../powerpivot-data-refresh-with-sharepoint-2010.md)  
  
-   [<span data-ttu-id="0210c-107">設定 PowerPivot 無人看管的資料重新整理帳戶 &#40;PowerPivot for SharePoint&#41;</span><span class="sxs-lookup"><span data-stu-id="0210c-107">Configure the PowerPivot Unattended Data Refresh Account &#40;PowerPivot for SharePoint&#41;</span></span>](../configure-unattended-data-refresh-account-powerpivot-sharepoint.md)  
  
-   [<span data-ttu-id="0210c-108">設定 PowerPivot 資料重新整理的預存認證 &#40;PowerPivot for SharePoint&#41;</span><span class="sxs-lookup"><span data-stu-id="0210c-108">Configure Stored Credentials for PowerPivot Data Refresh &#40;PowerPivot for SharePoint&#41;</span></span>](../configure-stored-credentials-data-refresh-powerpivot-sharepoint.md)  
  
-   [<span data-ttu-id="0210c-109">排程資料重新整理 &#40;PowerPivot for SharePoint&#41;</span><span class="sxs-lookup"><span data-stu-id="0210c-109">Schedule a Data Refresh &#40;PowerPivot for SharePoint&#41;</span></span>](../schedule-a-data-refresh-powerpivot-for-sharepoint.md)  
  
-   [<span data-ttu-id="0210c-110">查看資料重新整理記錄 &#40;PowerPivot for SharePoint&#41;</span><span class="sxs-lookup"><span data-stu-id="0210c-110">View Data Refresh History &#40;PowerPivot for SharePoint&#41;</span></span>](view-data-refresh-history-power-pivot-for-sharepoint.md)  
  
> [!NOTE]
>  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] <span data-ttu-id="0210c-111">和 SharePoint Server 2013 Excel Services 會使用不同的架構來進行 PowerPivot 資料模型的資料重新整理。</span><span class="sxs-lookup"><span data-stu-id="0210c-111">and SharePoint Server 2013 Excel Services use a different architecture for data refresh of PowerPivot data models.</span></span> <span data-ttu-id="0210c-112">SharePoint 2013 支援的架構會運用 Excel Services 做為主要元件來載入 PowerPivot 資料模型。</span><span class="sxs-lookup"><span data-stu-id="0210c-112">The SharePoint 2013 supported architecture utilizes Excel Services as the primary component to load PowerPivot data models.</span></span> <span data-ttu-id="0210c-113">先前的資料重新整理架構會使用並仰賴在 SharePoint 模式下執行 PowerPivot 系統服務和 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 的伺服器來載入資料模型。</span><span class="sxs-lookup"><span data-stu-id="0210c-113">The previous data refresh architecture used relied on a server running PowerPivot System Service and [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] in SharePoint mode to load data models.</span></span> <span data-ttu-id="0210c-114">如需詳細資訊，請參閱下列：</span><span class="sxs-lookup"><span data-stu-id="0210c-114">For more information, see the following:</span></span>  
> 
>  -   [<span data-ttu-id="0210c-115">SharePoint 2013 中的 PowerPivot 資料重新整理</span><span class="sxs-lookup"><span data-stu-id="0210c-115">PowerPivot Data Refresh with SharePoint 2013</span></span>](power-pivot-data-refresh-with-sharepoint-2013.md)  
> -   [<span data-ttu-id="0210c-116">&#40;SharePoint 2013&#41;升級活頁簿和排程的資料重新整理</span><span class="sxs-lookup"><span data-stu-id="0210c-116">Upgrade Workbooks and Scheduled Data Refresh &#40;SharePoint 2013&#41;</span></span>](../instances/install-windows/upgrade-workbooks-and-scheduled-data-refresh-sharepoint-2013.md)  
  
  
