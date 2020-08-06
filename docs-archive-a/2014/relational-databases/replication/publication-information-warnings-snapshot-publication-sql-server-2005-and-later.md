---
title: 發行集資訊、 (快照式發行集的警告 SQL Server 2005 和更新版本) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.monitor.publicationinfo.warningsandagents.snapshot.f1
ms.assetid: 7aa2eb52-b6b7-4dd3-8483-8ef00d9f0435
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: a3ae662a339e1e211ce4f46a588f4d7de65bf5e6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87702745"
---
# <a name="publication-information-warnings-snapshot-publication-sql-server-2005-and-later"></a><span data-ttu-id="fa25e-102">發行集資訊，警告 (快照式發行集，SQL Server 2005 和更新的版本)</span><span class="sxs-lookup"><span data-stu-id="fa25e-102">Publication Information, Warnings (Snapshot Publication, SQL Server 2005 and Later)</span></span>
  <span data-ttu-id="fa25e-103">執行 **和更新版本的散發者可以使用** [警告] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="fa25e-103">The **Warnings** tab is available for Distributors that are running [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] and later versions.</span></span> <span data-ttu-id="fa25e-104">**[警告]** 索引標籤可以讓您針對選取的發行集執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="fa25e-104">The **Warnings** tab allows you to perform the following tasks for the selected publication:</span></span>  
  
-   <span data-ttu-id="fa25e-105">啟用警告。</span><span class="sxs-lookup"><span data-stu-id="fa25e-105">Enable warnings.</span></span>  
  
-   <span data-ttu-id="fa25e-106">指定與警告相關聯的臨界值。</span><span class="sxs-lookup"><span data-stu-id="fa25e-106">Specify thresholds associated with warnings.</span></span>  
  
-   <span data-ttu-id="fa25e-107">定義與警告相關聯的警示。</span><span class="sxs-lookup"><span data-stu-id="fa25e-107">Define alerts associated with warnings.</span></span>  
  
## <a name="warnings-thresholds-and-alerts"></a><span data-ttu-id="fa25e-108">警告、臨界值和警示</span><span class="sxs-lookup"><span data-stu-id="fa25e-108">Warnings, Thresholds, and Alerts</span></span>  
 <span data-ttu-id="fa25e-109">根據預設，複寫監視器會針對未初始化的訂閱顯示警告： **[未初始化的訂閱]** 狀態會在包含訂閱資訊之頁面的 **[狀態]** 資料行中顯示為警告。</span><span class="sxs-lookup"><span data-stu-id="fa25e-109">By default, Replication Monitor displays warnings for uninitialized subscriptions: a status of **Uninitialized subscription** is displayed as a warning in the **Status** column of pages that include subscription information.</span></span> <span data-ttu-id="fa25e-110">針對快照式發行集，您也可以藉由設定 **[若訂閱將在臨界值內過期，就發出警告]** 選項，來指定即將發生訂閱逾期時會產生警告。</span><span class="sxs-lookup"><span data-stu-id="fa25e-110">For snapshot publications, you can also specify that imminent subscription expiration results in a warning by setting the option **Warn if a subscription will expire within the threshold**.</span></span> <span data-ttu-id="fa25e-111">如果達到或超出指定的臨界值，訂閱狀態會顯示為 **[即將過期/已過期]** (除非必須顯示具有更高優先權的問題)。</span><span class="sxs-lookup"><span data-stu-id="fa25e-111">If the specified threshold is met or exceeded, the subscription status is displayed as **Expiring soon/Expired** (unless an issue with a higher priority needs to be displayed).</span></span>  
  
 <span data-ttu-id="fa25e-112">除了在複寫監視器顯示警告外，達到臨界值也會觸發警示。</span><span class="sxs-lookup"><span data-stu-id="fa25e-112">In addition to displaying a warning in Replication Monitor, reaching a threshold can also trigger an alert.</span></span> <span data-ttu-id="fa25e-113">定義警示的方式，是按一下 **[設定警示]** ，並在 **[設定複寫警示]** 對話方塊中提供資訊。</span><span class="sxs-lookup"><span data-stu-id="fa25e-113">Alerts are defined by clicking **Configure Alerts** and providing information in the **Configure Replication Alerts** dialog box.</span></span>  
  
## <a name="options"></a><span data-ttu-id="fa25e-114">選項。</span><span class="sxs-lookup"><span data-stu-id="fa25e-114">Options</span></span>  
 <span data-ttu-id="fa25e-115">**已啟用**</span><span class="sxs-lookup"><span data-stu-id="fa25e-115">**Enabled**</span></span>  
 <span data-ttu-id="fa25e-116">選取以啟用警告，並指定臨界值。</span><span class="sxs-lookup"><span data-stu-id="fa25e-116">Select to enable a warning and specify a threshold.</span></span>  
  
 <span data-ttu-id="fa25e-117">**警告**</span><span class="sxs-lookup"><span data-stu-id="fa25e-117">**Warning**</span></span>  
 <span data-ttu-id="fa25e-118">與臨界值相關聯之警告的描述。</span><span class="sxs-lookup"><span data-stu-id="fa25e-118">A description of the warning associated with a threshold.</span></span>  
  
 <span data-ttu-id="fa25e-119">**閾值**</span><span class="sxs-lookup"><span data-stu-id="fa25e-119">**Threshold**</span></span>  
 <span data-ttu-id="fa25e-120">指定臨界值的值。</span><span class="sxs-lookup"><span data-stu-id="fa25e-120">Specify a value for the threshold.</span></span>  
  
 <span data-ttu-id="fa25e-121">**[設定警示]**</span><span class="sxs-lookup"><span data-stu-id="fa25e-121">**Configure Alerts**</span></span>  
 <span data-ttu-id="fa25e-122">在 **[警告]** 方格中選取一個資料列，然後按一下 **[設定警示]** 以啟動 **[設定複寫警示]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="fa25e-122">Select a row in the **Warnings** grid, and click **Configure Alerts** to launch the **Configure Replication Alerts** dialog box.</span></span> <span data-ttu-id="fa25e-123">此對話方塊可以讓您定義與選取的臨界值和警告相關聯的警示。</span><span class="sxs-lookup"><span data-stu-id="fa25e-123">The dialog box allows you to define an alert, which is associated with the selected threshold and warning.</span></span>  
  
 <span data-ttu-id="fa25e-124">**捨棄變更**</span><span class="sxs-lookup"><span data-stu-id="fa25e-124">**Discard Changes**</span></span>  
 <span data-ttu-id="fa25e-125">按一下即可捨棄對警告與臨界值所做的任何變更。</span><span class="sxs-lookup"><span data-stu-id="fa25e-125">Click to discard any changes to warnings and thresholds.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="fa25e-126">按一下 **[捨棄變更]** 不會影響在 **[設定複寫警示]** 對話方塊中定義的警示。</span><span class="sxs-lookup"><span data-stu-id="fa25e-126">Clicking **Discard Changes** does not affect alerts defined in the **Configure Replication Alerts** dialog box.</span></span>  
  
 <span data-ttu-id="fa25e-127">**儲存變更**</span><span class="sxs-lookup"><span data-stu-id="fa25e-127">**Save Changes**</span></span>  
 <span data-ttu-id="fa25e-128">按一下即可儲存對警告與臨界值所做的任何變更。</span><span class="sxs-lookup"><span data-stu-id="fa25e-128">Click to save any changes to warnings and thresholds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa25e-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fa25e-129">See Also</span></span>  
 <span data-ttu-id="fa25e-130">[啟動複寫監視器](monitor/start-the-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="fa25e-130">[Start the Replication Monitor](monitor/start-the-replication-monitor.md) </span></span>  
 <span data-ttu-id="fa25e-131">[使用複寫監視器來檢視資訊及執行工作](monitor/view-information-and-perform-tasks-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="fa25e-131">[View Information and Perform Tasks using Replication Monitor](monitor/view-information-and-perform-tasks-replication-monitor.md) </span></span>  
 [<span data-ttu-id="fa25e-132">監視複寫</span><span class="sxs-lookup"><span data-stu-id="fa25e-132">Monitoring Replication</span></span>](monitoring-replication.md)  
  
  
