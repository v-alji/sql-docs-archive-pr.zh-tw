---
title: 報表產生器 (SSRS) |Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 32be8fcc-e87d-4c45-a644-dff45776a981
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: dae43dd86cd6b02c81f0fc90a05292458eb87200
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87700687"
---
# <a name="report-builder-ssrs"></a><span data-ttu-id="b26e9-102">報表產生器 (SSRS)</span><span class="sxs-lookup"><span data-stu-id="b26e9-102">Report Builder (SSRS)</span></span>
  <span data-ttu-id="b26e9-103">報表產生器是一個報表撰寫環境，適合喜歡在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Office 環境中工作的商務使用者使用。</span><span class="sxs-lookup"><span data-stu-id="b26e9-103">Report Builder is a report authoring environment for business users who prefer to work in the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Office environment.</span></span> <span data-ttu-id="b26e9-104">當您設計報表時，可以指定要取得資料的位置、要取得的資料，以及要顯示資料的方式。</span><span class="sxs-lookup"><span data-stu-id="b26e9-104">When you design a report, you specify where to get the data, which data to get, and how to display the data.</span></span> <span data-ttu-id="b26e9-105">當您執行報表時，報表處理器會採用已指定的所有資訊、擷取資料，然後將它與報表配置結合，以便產生報表。</span><span class="sxs-lookup"><span data-stu-id="b26e9-105">When you run the report, the report processor takes all the information you have specified, retrieves the data, and combines it with the report layout to generate the report.</span></span>  
  
## <a name="benefits-of-report-builder"></a><span data-ttu-id="b26e9-106">報表產生器的優點</span><span class="sxs-lookup"><span data-stu-id="b26e9-106">Benefits of Report Builder</span></span>  
 <span data-ttu-id="b26e9-107">報表產生器讓您可以：</span><span class="sxs-lookup"><span data-stu-id="b26e9-107">Report Builder enables you to:</span></span>  
  
-   <span data-ttu-id="b26e9-108">使用報表產生器功能區快速加入報表、啟動表格、圖表及地圖精靈的項目，並格式化報表資料。</span><span class="sxs-lookup"><span data-stu-id="b26e9-108">Use the Report Builder ribbon to quickly add items your reports, launch table, chart, and map wizards, and format report data.</span></span>  
  
-   <span data-ttu-id="b26e9-109">使用查詢設計工具從內建資料提供者加入資料可協助您指定要包含在報表中的資料。</span><span class="sxs-lookup"><span data-stu-id="b26e9-109">Add data from built-in data providers by using query designers that help you specify which data to include in your report.</span></span>  
  
-   <span data-ttu-id="b26e9-110">建立及使用報表參數和其他互動式功能可讓您的報告讀取器自訂資料，以及改變報表的呈現方式。</span><span class="sxs-lookup"><span data-stu-id="b26e9-110">Create and use report parameters and other interactive features that enable your report readers to customize data and vary report presentation.</span></span>  
  
-   <span data-ttu-id="b26e9-111">建立來自於內建欄位、集合、運算子和函數的運算式。</span><span class="sxs-lookup"><span data-stu-id="b26e9-111">Create expressions from built-in fields, collections, operators, and functions.</span></span>  
  
-   <span data-ttu-id="b26e9-112">從報表伺服器直接開啟報表。</span><span class="sxs-lookup"><span data-stu-id="b26e9-112">Open reports directly from a report server.</span></span>  
  
-   <span data-ttu-id="b26e9-113">預覽使用本機或已發行共用資料來源和共用資料集的報表。</span><span class="sxs-lookup"><span data-stu-id="b26e9-113">Preview reports that use local or published shared data sources and shared datasets.</span></span>  
  
-   <span data-ttu-id="b26e9-114">預覽 HTML 格式的報表，或列印格式。</span><span class="sxs-lookup"><span data-stu-id="b26e9-114">Preview reports in HTML or print format.</span></span>  
  
-   <span data-ttu-id="b26e9-115">將報表匯出為其他檔案格式，例如 [!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="b26e9-115">Export reports to other file formats such as [!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)].</span></span>  
  
-   <span data-ttu-id="b26e9-116">將報表和相關項目儲存至報表伺服器、SharePoint 文件庫或本機電腦。</span><span class="sxs-lookup"><span data-stu-id="b26e9-116">Save your report and related items s to a SharePoint library, a report server, or your local computer.</span></span>  
  
 <span data-ttu-id="b26e9-117">報表產生器與報表設計師可共用許多功能。</span><span class="sxs-lookup"><span data-stu-id="b26e9-117">Report Builder and Report Designer share many features.</span></span> <span data-ttu-id="b26e9-118">如需報表產生器的詳細資訊，請參閱 msdn.microsoft.com 上的[報表產生器檔](https://go.microsoft.com/fwlink/?LinkId=154494)。</span><span class="sxs-lookup"><span data-stu-id="b26e9-118">For more information about Report Builder, see [Report Builder documentation](https://go.microsoft.com/fwlink/?LinkId=154494) on msdn.microsoft.com.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b26e9-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b26e9-119">See Also</span></span>  
 <span data-ttu-id="b26e9-120">[設定報表產生器存取](../report-server/configure-report-builder-access.md) </span><span class="sxs-lookup"><span data-stu-id="b26e9-120">[Configure Report Builder Access](../report-server/configure-report-builder-access.md) </span></span>  
 <span data-ttu-id="b26e9-121">[Reporting Services 工具](reporting-services-tools.md) </span><span class="sxs-lookup"><span data-stu-id="b26e9-121">[Reporting Services Tools](reporting-services-tools.md) </span></span>  
 [<span data-ttu-id="b26e9-122">使用報表設計師設計報表 &#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="b26e9-122">Design Reports with Report Designer &#40;SSRS&#41;</span></span>](design-reporting-services-paginated-reports-with-report-designer-ssrs.md)  
  
  
