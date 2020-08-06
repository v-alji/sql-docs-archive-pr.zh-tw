---
title: " (SSIS 封裝升級嚮導升級封裝) |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.is.upgradewizard.upgradingpackage.f1
ms.assetid: cdb842e3-2e59-4ede-b127-be4fde46875c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d13228dabc1566b592733da4afd8ebde3671ee0d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592741"
---
# <a name="upgrading-the-packages-ssis-package-upgrade-wizard"></a><span data-ttu-id="929c8-102">升級封裝 (SSIS 封裝升級精靈)</span><span class="sxs-lookup"><span data-stu-id="929c8-102">Upgrading the Packages (SSIS Package Upgrade Wizard)</span></span>
  <span data-ttu-id="929c8-103">使用 **[正在升級封裝]** 頁面，即可檢視封裝升級的進度，並在必要時中斷升級程序。</span><span class="sxs-lookup"><span data-stu-id="929c8-103">Use the **Upgrading the Packages** page to view the progress of package upgrade and to interrupt the upgrade process.</span></span> <span data-ttu-id="929c8-104">[!INCLUDE[ssIS](../includes/ssis-md.md)] 封裝升級精靈會逐一升級選取的封裝。</span><span class="sxs-lookup"><span data-stu-id="929c8-104">The [!INCLUDE[ssIS](../includes/ssis-md.md)] Package Upgrade Wizard upgrades the selected packages one by one.</span></span>  
  
 <span data-ttu-id="929c8-105">**檢視儲存到 SQL Server 資料庫或封裝存放區的升級封裝**</span><span class="sxs-lookup"><span data-stu-id="929c8-105">**To view upgraded packages that were saved to a SQL Server database or to the package store**</span></span>  
  
-   <span data-ttu-id="929c8-106">在 [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]的 [物件總管] 中，連接到 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]的本機執行個體，然後展開 **[存放的封裝]** 節點，查看已升級的封裝。</span><span class="sxs-lookup"><span data-stu-id="929c8-106">In [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)], in Object Explorer, connect to the local instance of [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)], and then expand the **Stored Packages** node to see the packages that were upgraded.</span></span>  
  
 <span data-ttu-id="929c8-107">**若要檢視從 SQL Server 資料工具升級的升級封裝**</span><span class="sxs-lookup"><span data-stu-id="929c8-107">**To view upgraded packages that were upgraded from SQL Server Data Tools**</span></span>  
  
-   <span data-ttu-id="929c8-108">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]的 [方案總管] 中，開啟 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 專案，然後展開 **[SSIS 封裝]** 節點，查看升級的封裝。</span><span class="sxs-lookup"><span data-stu-id="929c8-108">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], in Solution Explorer, open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project, and then expand the **SSIS Packages** node to see the upgraded packages.</span></span>  
  
## <a name="options"></a><span data-ttu-id="929c8-109">選項。</span><span class="sxs-lookup"><span data-stu-id="929c8-109">Options</span></span>  
 <span data-ttu-id="929c8-110">**訊息窗格**</span><span class="sxs-lookup"><span data-stu-id="929c8-110">**Message pane**</span></span>  
 <span data-ttu-id="929c8-111">在升級進行期間顯示進度訊息和摘要資訊。</span><span class="sxs-lookup"><span data-stu-id="929c8-111">Displays progress messages and summary information during the upgrade process.</span></span>  
  
 <span data-ttu-id="929c8-112">**動作**</span><span class="sxs-lookup"><span data-stu-id="929c8-112">**Action**</span></span>  
 <span data-ttu-id="929c8-113">檢視升級中的動作。</span><span class="sxs-lookup"><span data-stu-id="929c8-113">View the actions in the upgrade.</span></span>  
  
 <span data-ttu-id="929c8-114">**狀態**</span><span class="sxs-lookup"><span data-stu-id="929c8-114">**Status**</span></span>  
 <span data-ttu-id="929c8-115">檢視每個動作的結果。</span><span class="sxs-lookup"><span data-stu-id="929c8-115">View the result of each action.</span></span>  
  
 <span data-ttu-id="929c8-116">**訊息**</span><span class="sxs-lookup"><span data-stu-id="929c8-116">**Message**</span></span>  
 <span data-ttu-id="929c8-117">檢視每個動作所產生的錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="929c8-117">View the error messages that each action generates.</span></span>  
  
 <span data-ttu-id="929c8-118">**停止**</span><span class="sxs-lookup"><span data-stu-id="929c8-118">**Stop**</span></span>  
 <span data-ttu-id="929c8-119">停止封裝升級。</span><span class="sxs-lookup"><span data-stu-id="929c8-119">Stop the package upgrade.</span></span>  
  
 <span data-ttu-id="929c8-120">**Report**</span><span class="sxs-lookup"><span data-stu-id="929c8-120">**Report**</span></span>  
 <span data-ttu-id="929c8-121">選取您想要針對包含封裝升級結果的報表採取什麼動作：</span><span class="sxs-lookup"><span data-stu-id="929c8-121">Select what you want to do with the report that contains the results of the package upgrade:</span></span>  
  
-   <span data-ttu-id="929c8-122">線上檢視報表。</span><span class="sxs-lookup"><span data-stu-id="929c8-122">View the report online.</span></span>  
  
-   <span data-ttu-id="929c8-123">將報表儲存為檔案。</span><span class="sxs-lookup"><span data-stu-id="929c8-123">Save the report to a file.</span></span>  
  
-   <span data-ttu-id="929c8-124">將報表複製到剪貼簿。</span><span class="sxs-lookup"><span data-stu-id="929c8-124">Copy the report to the Clipboard</span></span>  
  
-   <span data-ttu-id="929c8-125">以電子郵件訊息傳送報表。</span><span class="sxs-lookup"><span data-stu-id="929c8-125">Send the report as an e-mail message.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="929c8-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="929c8-126">See Also</span></span>  
 [<span data-ttu-id="929c8-127">升級 Integration Services 套件</span><span class="sxs-lookup"><span data-stu-id="929c8-127">Upgrade Integration Services Packages</span></span>](install-windows/upgrade-integration-services-packages.md)  
  
  
