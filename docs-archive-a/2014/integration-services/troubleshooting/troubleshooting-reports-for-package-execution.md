---
title: 針對套件執行的報告進行疑難排解 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 8fc476ac-bd69-434e-9636-70776e0b3b6c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b20d9c9c02af3f3df96e2ef46a7b25251793fa55
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597903"
---
# <a name="troubleshooting-reports-for-package-execution"></a><span data-ttu-id="78de9-102">疑難排解封裝執行的報表</span><span class="sxs-lookup"><span data-stu-id="78de9-102">Troubleshooting Reports for Package Execution</span></span>
  <span data-ttu-id="78de9-103">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]的目前版本中， [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 提供一些標準報表，可協助您監視和疑難排解已部署至 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 目錄的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 封裝。</span><span class="sxs-lookup"><span data-stu-id="78de9-103">In the current release of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], standard reports are available in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to help you monitor and troubleshoot [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages that have been deployed to the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] catalog.</span></span> <span data-ttu-id="78de9-104">其中兩份封裝報表特別有助於您檢視封裝執行狀態以及識別執行失敗的原因。</span><span class="sxs-lookup"><span data-stu-id="78de9-104">Two of these package reports in particular help you to view package execution status and identify the cause of execution failures.</span></span>  
  
-   <span data-ttu-id="78de9-105">**Integration Services 儀表板** - 這份報表會提供過去 24 小時內 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體上所有封裝執行的概觀。</span><span class="sxs-lookup"><span data-stu-id="78de9-105">**Integration Services Dashboard** - This report provides an overview of all the package executions on the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance in the past 24 hours.</span></span> <span data-ttu-id="78de9-106">此報表顯示每個封裝諸如狀態、作業類型、封裝名稱等資訊。</span><span class="sxs-lookup"><span data-stu-id="78de9-106">The report displays information such as Status, Operation Type, Package Name, etc., for each package.</span></span>  
  
     <span data-ttu-id="78de9-107">您可以依照下列方式解譯開始時間、結束時間和持續時間：</span><span class="sxs-lookup"><span data-stu-id="78de9-107">The Start Time, End Time, and Duration can be interpreted as follows:</span></span>  
  
    -   <span data-ttu-id="78de9-108">如果封裝仍在執行中，則持續時間 = 目前時間 - 開始時間</span><span class="sxs-lookup"><span data-stu-id="78de9-108">If the package is still running, then Duration = current time - Start Time</span></span>  
  
    -   <span data-ttu-id="78de9-109">如果封裝已完成，則持續時間 = 結束時間 - 開始時間</span><span class="sxs-lookup"><span data-stu-id="78de9-109">If the package has completed, then Duration = End Time - Start Time</span></span>  
  
     <span data-ttu-id="78de9-110">對於伺服器上已執行的每個封裝，儀表板可讓您放大報表，尋找可能發生之封裝執行錯誤的特定詳細資料。</span><span class="sxs-lookup"><span data-stu-id="78de9-110">For each package that has run on the server, the dashboard allows you to "zoom in" to find specific details on package execution errors that may have occurred.</span></span> <span data-ttu-id="78de9-111">例如，您可以按一下 [概觀]  顯示執行中工作狀態的高階概觀，或是按一下 [所有訊息]  顯示封裝執行過程中已擷取的詳細訊息。</span><span class="sxs-lookup"><span data-stu-id="78de9-111">For example, click **Overview** to display a high-level overview of the status of the tasks in the execution, or **All Messages** to display the detailed messages that were captured as part of the package execution.</span></span>  
  
     <span data-ttu-id="78de9-112">您可以按一下 [篩選]  ，然後選取 [篩選設定]  對話方塊中的準則，篩選任何頁面上顯示的資料表。</span><span class="sxs-lookup"><span data-stu-id="78de9-112">You can filter the table displayed on any page by clicking **Filter** and then selecting criteria in the **Filter Settings** dialog.</span></span> <span data-ttu-id="78de9-113">可用的篩選準則取決於顯示的資料。</span><span class="sxs-lookup"><span data-stu-id="78de9-113">The filter criteria available depends on the data being displayed.</span></span> <span data-ttu-id="78de9-114">您可以在 [篩選設定]  對話方塊中按一下排序圖示，以變更報表的排序次序。</span><span class="sxs-lookup"><span data-stu-id="78de9-114">You can change the sort order of the report by clicking the sort icon in the **Filter Settings** dialog.</span></span>  
  
-   <span data-ttu-id="78de9-115">**活動 - 所有執行報表** - 這份報表會顯示伺服器上已執行之所有 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 執行的摘要。</span><span class="sxs-lookup"><span data-stu-id="78de9-115">**Activity - All Executions Report** - This report displays a summary of all [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] executions that have been performed on the server.</span></span> <span data-ttu-id="78de9-116">此摘要會顯示每個執行的資訊，例如狀態、開始時間和結束時間。</span><span class="sxs-lookup"><span data-stu-id="78de9-116">The summary displays information for each execution such as status, start time, and end time.</span></span> <span data-ttu-id="78de9-117">每個摘要項目都包含執行詳細資訊的連結，包括執行期間產生的訊息以及效能資料。</span><span class="sxs-lookup"><span data-stu-id="78de9-117">Each summary entry includes links to more information about the execution including messages generated during execution and performance data.</span></span> <span data-ttu-id="78de9-118">就如同 Integration Services 儀表板一樣，您可以將篩選套用至資料表，以縮小顯示的資訊範圍。</span><span class="sxs-lookup"><span data-stu-id="78de9-118">As with the Integration Services Dashboard, you can apply a filter to the table to narrow down the information displayed.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="78de9-119">相關工作</span><span class="sxs-lookup"><span data-stu-id="78de9-119">Related Tasks</span></span>  
 [<span data-ttu-id="78de9-120">檢視 Integration Services 伺服器的報表</span><span class="sxs-lookup"><span data-stu-id="78de9-120">View Reports for the Integration Services Server</span></span>](../view-reports-for-the-integration-services-server.md)  
  
## <a name="related-content"></a><span data-ttu-id="78de9-121">相關內容</span><span class="sxs-lookup"><span data-stu-id="78de9-121">Related Content</span></span>  
 [<span data-ttu-id="78de9-122">Integration Services 伺服器的報表</span><span class="sxs-lookup"><span data-stu-id="78de9-122">Reports for the Integration Services Server</span></span>](../reports-for-the-integration-services-server.md)  
  
 [<span data-ttu-id="78de9-123">套件執行的疑難排解工具</span><span class="sxs-lookup"><span data-stu-id="78de9-123">Troubleshooting Tools for Package Execution</span></span>](troubleshooting-tools-for-package-execution.md)  
  
  
