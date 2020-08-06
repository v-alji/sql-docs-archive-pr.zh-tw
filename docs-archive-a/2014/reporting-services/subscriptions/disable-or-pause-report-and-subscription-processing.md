---
title: 暫停報表和訂閱處理 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- pausing schedules
- subscriptions [Reporting Services], pausing
- report processing [Reporting Services], pausing
- shared data sources [Reporting Services]
- pausing subscription processing
- pausing report processing
- temporarily stopping report processing
- disabling shared data sources
- roles [Reporting Services], modifying
- shared schedules [Reporting Services], pausing
ms.assetid: 3cf9a240-24cc-46d4-bec6-976f82d8f830
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 1607637630c507588602dd7e566917ce1eeb6080
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704842"
---
# <a name="pause-report-and-subscription-processing"></a><span data-ttu-id="95a58-102">暫停報表與訂閱處理</span><span class="sxs-lookup"><span data-stu-id="95a58-102">Pause Report and Subscription Processing</span></span>
  <span data-ttu-id="95a58-103">您無法直接暫停報表或訂閱。</span><span class="sxs-lookup"><span data-stu-id="95a58-103">You cannot pause a report or subscription directly.</span></span> <span data-ttu-id="95a58-104">但是，您可以在處理開始之前，或在進行資料來源連接時，中斷報表與訂閱處理。</span><span class="sxs-lookup"><span data-stu-id="95a58-104">However, you can interrupt report and subscription processing prior to the process starting or when a data source connection is made.</span></span> <span data-ttu-id="95a58-105">您也可以不讓使用者存取報表或訂閱，以禁止處理報表或訂閱。</span><span class="sxs-lookup"><span data-stu-id="95a58-105">You can also prevent a report or subscription from processing by making it inaccessible to users.</span></span>  
  
 <span data-ttu-id="95a58-106">下列策略可以用來暫時禁止進行處理。</span><span class="sxs-lookup"><span data-stu-id="95a58-106">The following strategies can be used to temporarily prevent a process from occurring.</span></span>  
  
## <a name="modify-role-assignments-to-prevent-access"></a><span data-ttu-id="95a58-107">修改角色指派來禁止存取</span><span class="sxs-lookup"><span data-stu-id="95a58-107">Modify Role Assignments to Prevent Access</span></span>  
 <span data-ttu-id="95a58-108">讓報表無法使用的最佳方法，是暫時移除可以提供存取報表的角色指派。</span><span class="sxs-lookup"><span data-stu-id="95a58-108">The best way to make a report unavailable is to temporarily remove the role assignment that provides access to the report.</span></span> <span data-ttu-id="95a58-109">無論建立資料來源連接的方式為何，此方法可以用於所有報表。</span><span class="sxs-lookup"><span data-stu-id="95a58-109">This approach can be used on all reports regardless of how the data source connection is made.</span></span> <span data-ttu-id="95a58-110">此方法僅會以報表為目標，不會影響其他報表或項目的作業。</span><span class="sxs-lookup"><span data-stu-id="95a58-110">This approach targets only the report, without affecting the operation of other reports or items.</span></span>  
  
 <span data-ttu-id="95a58-111">若要移除角色指派，請在報表管理員中，開啟報表的 [安全性屬性] 頁面。</span><span class="sxs-lookup"><span data-stu-id="95a58-111">To remove the role assignment, open the Security Properties page of the report in Report Manager.</span></span> <span data-ttu-id="95a58-112">如果報表從父系繼承安全性，您可以按一下 [編輯項目安全性]\*\*\*\* 來建立嚴格的安全性原則，省略提供普遍存取權的角色指派 (例如，您可以移除提供 Everyone 存取權的角色指派，保留提供一小組使用者存取權的角色指派，例如系統管理員)。</span><span class="sxs-lookup"><span data-stu-id="95a58-112">If the report inherits security from a parent, you can click **Edit Item Security** to create a restrictive security policy that omits role assignments that provide widespread access (for example, you can remove a role assignment that provides access to Everyone, and keep the role assignment that provides access to a small group of users, such as Administrators).</span></span>  
  
## <a name="disable-a-shared-data-source"></a><span data-ttu-id="95a58-113">停用共用資料來源</span><span class="sxs-lookup"><span data-stu-id="95a58-113">Disable a Shared Data Source</span></span>  
 <span data-ttu-id="95a58-114">使用共用資料來源的優點之一是您可以停用它，禁止執行報表或資料驅動訂閱。</span><span class="sxs-lookup"><span data-stu-id="95a58-114">One advantage to using shared data sources is that you can disable it to prevent a report or data-driven subscription from running.</span></span> <span data-ttu-id="95a58-115">停用共用資料來源會中斷報表與其外部來源的連接。</span><span class="sxs-lookup"><span data-stu-id="95a58-115">Disabling a shared data source disconnects the report from its external source.</span></span> <span data-ttu-id="95a58-116">停用時，資料來源無法供所有使用它的報表與訂閱使用。</span><span class="sxs-lookup"><span data-stu-id="95a58-116">While it is disabled, the data source is unavailable to all reports and subscriptions that use it.</span></span> <span data-ttu-id="95a58-117">若要停用共用資料來源，請在報表管理員中開啟資料來源，然後清除 **[啟用此資料來源]** 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="95a58-117">To disable a shared data source, open the data source in Report Manager and clear the **Enable this data source** check box.</span></span>  
  
 <span data-ttu-id="95a58-118">請注意，即使資料來源無法使用，報表仍然會載入。</span><span class="sxs-lookup"><span data-stu-id="95a58-118">Note that the report still loads even if the data source is unavailable.</span></span> <span data-ttu-id="95a58-119">報表不包含資料，但具備適當權限的使用者可以存取與報表相關聯的屬性頁面、安全性設定、報表記錄，以及訂閱資訊。</span><span class="sxs-lookup"><span data-stu-id="95a58-119">The report does not contain data, but users with appropriate permissions can access the property pages, security settings, report history, and subscription information associated with the report.</span></span>  
  
## <a name="pause-a-shared-schedule"></a><span data-ttu-id="95a58-120">暫停共用排程</span><span class="sxs-lookup"><span data-stu-id="95a58-120">Pause a Shared Schedule</span></span>  
 <span data-ttu-id="95a58-121">如果報表或訂閱從共用排程執行，您可以暫停排程來禁止處理。</span><span class="sxs-lookup"><span data-stu-id="95a58-121">If a report or subscription runs from a shared schedule, you can pause the schedule to prevent processing.</span></span> <span data-ttu-id="95a58-122">由排程驅動的所有報表與訂閱處理，會被延遲至排程繼續為止。</span><span class="sxs-lookup"><span data-stu-id="95a58-122">All report and subscription processing that is driven by the schedule is deferred until the schedule is resumed.</span></span> <span data-ttu-id="95a58-123">如需詳細資訊，請參閱[暫停和繼續共用](schedules.md)排程。</span><span class="sxs-lookup"><span data-stu-id="95a58-123">For more information, see [Pause and Resume Shared Schedules](schedules.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95a58-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="95a58-124">See Also</span></span>  
 <span data-ttu-id="95a58-125">[Reporting Services 報表伺服器 &#40;原生模式&#41;](../report-server/reporting-services-report-server-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="95a58-125">[Reporting Services Report Server &#40;Native Mode&#41;](../report-server/reporting-services-report-server-native-mode.md) </span></span>  
 <span data-ttu-id="95a58-126">[報表管理員 &#40;SSRS 原生模式&#41;](../report-manager-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="95a58-126">[Report Manager  &#40;SSRS Native Mode&#41;](../report-manager-ssrs-native-mode.md) </span></span>  
 [<span data-ttu-id="95a58-127">安全性屬性頁面，項目 &#40;報表管理員&#41;</span><span class="sxs-lookup"><span data-stu-id="95a58-127">Security Properties Page, Items &#40;Report Manager&#41;</span></span>](../security-properties-page-items-report-manager.md)  
  
  
