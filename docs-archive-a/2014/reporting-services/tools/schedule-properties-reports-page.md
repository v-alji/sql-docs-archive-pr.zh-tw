---
title: 排程屬性 (報表頁面) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.swb.reportserver.scheduleproperties.reports.f1
ms.assetid: 7db728bd-4b08-43ef-a49a-e8dcdd37cf89
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: da0b5255e73522572fa22da8668329a28f108104
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594364"
---
# <a name="schedule-properties-reports-page"></a><span data-ttu-id="994f9-102">排程屬性 (報表頁面)</span><span class="sxs-lookup"><span data-stu-id="994f9-102">Schedule Properties (Reports Page)</span></span>
  <span data-ttu-id="994f9-103">使用此頁面，即可檢視使用此共用排程之所有報表的清單。</span><span class="sxs-lookup"><span data-stu-id="994f9-103">Use this page to view a list of all reports that use this shared schedule.</span></span> <span data-ttu-id="994f9-104">排程可用來重新整理報表快照集、產生報表記錄、觸發訂閱或使報表的快取副本過期。</span><span class="sxs-lookup"><span data-stu-id="994f9-104">Schedules can be used to refresh report snapshots, generate report history, trigger a subscription, or expire a cached copy of the report.</span></span> <span data-ttu-id="994f9-105">若要了解如何使用排程，請檢視報表的屬性和訂閱資訊。</span><span class="sxs-lookup"><span data-stu-id="994f9-105">To find out how the schedule is used, view the property and subscription information of the report.</span></span>  
  
 <span data-ttu-id="994f9-106">雖然這個頁面會顯示使用此共用排程的每份報表，但是它不會指出在該單一報表內使用此共用排程的次數。</span><span class="sxs-lookup"><span data-stu-id="994f9-106">Although this page shows each report that uses the shared schedule, it does not indicate how many times the shared schedule is used within that single report.</span></span> <span data-ttu-id="994f9-107">例如，假設 Company Sales 報表的 20 位不同訂閱者都使用相同的共用排程來觸發訂閱處理。</span><span class="sxs-lookup"><span data-stu-id="994f9-107">For example, suppose 20 different subscribers to the Company Sales report all use the same shared schedule to trigger subscription processing.</span></span> <span data-ttu-id="994f9-108">在此情況下，Company Sales 報表只會在此清單中顯示一次，即使報表具有共用排程的 20 個參考也一樣。</span><span class="sxs-lookup"><span data-stu-id="994f9-108">In this case, the Company Sales report will only appear once in this list, even though the report has 20 references to the shared schedule.</span></span>  
  
 <span data-ttu-id="994f9-109">若要開啟此頁面，請啟動 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 、連接至報表伺服器、開啟 [**共用**排程] 資料夾、以滑鼠右鍵按一下共用排程、選取 [**屬性**]，然後按一下 [**報表**]。</span><span class="sxs-lookup"><span data-stu-id="994f9-109">To open this page, start [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connect to a report server, open the **Shared Schedules** folder, right-click a shared schedule, select **Properties**, and then click **Reports**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="994f9-110">並非所有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]版本都提供此功能。</span><span class="sxs-lookup"><span data-stu-id="994f9-110">This feature is not available in every edition of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="994f9-111">如需版本支援的功能清單 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，請參閱[SQL Server 2012 (版本支援的功能](https://go.microsoft.com/fwlink/?linkid=232473) https://go.microsoft.com/fwlink/?linkid=232473) 。</span><span class="sxs-lookup"><span data-stu-id="994f9-111">For a list of features that are supported by the editions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], see [Features Supported by the Editions of SQL Server 2012](https://go.microsoft.com/fwlink/?linkid=232473) (https://go.microsoft.com/fwlink/?linkid=232473).</span></span>  
  
## <a name="options"></a><span data-ttu-id="994f9-112">選項。</span><span class="sxs-lookup"><span data-stu-id="994f9-112">Options</span></span>  
 <span data-ttu-id="994f9-113">**資料夾**</span><span class="sxs-lookup"><span data-stu-id="994f9-113">**Folder**</span></span>  
 <span data-ttu-id="994f9-114">指定報表的路徑。</span><span class="sxs-lookup"><span data-stu-id="994f9-114">Specifies the path of the report.</span></span>  
  
 <span data-ttu-id="994f9-115">**Report**</span><span class="sxs-lookup"><span data-stu-id="994f9-115">**Report**</span></span>  
 <span data-ttu-id="994f9-116">指定使用排程之報表的名稱。</span><span class="sxs-lookup"><span data-stu-id="994f9-116">Specifies the name of the report that uses the schedule.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="994f9-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="994f9-117">See Also</span></span>  
 <span data-ttu-id="994f9-118">[建立、修改和刪除共用排程](../subscriptions/create-modify-and-delete-schedules.md) </span><span class="sxs-lookup"><span data-stu-id="994f9-118">[Create, Modify, and Delete Schedules](../subscriptions/create-modify-and-delete-schedules.md) </span></span>  
 <span data-ttu-id="994f9-119">[[排程]](../subscriptions/schedules.md) </span><span class="sxs-lookup"><span data-stu-id="994f9-119">[Schedules](../subscriptions/schedules.md) </span></span>  
 <span data-ttu-id="994f9-120">[Management Studio F1 說明中的報表伺服器](report-server-in-management-studio-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="994f9-120">[Report Server in Management Studio F1 Help](report-server-in-management-studio-f1-help.md) </span></span>  
 <span data-ttu-id="994f9-121">[連接到 Management Studio 中的報表伺服器](connect-to-a-report-server-in-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="994f9-121">[Connect to a Report Server in Management Studio](connect-to-a-report-server-in-management-studio.md) </span></span>  
 [<span data-ttu-id="994f9-122">設定報表的一般屬性 &#40;報表管理員&#41;</span><span class="sxs-lookup"><span data-stu-id="994f9-122">Configure General Properties for a Report &#40;Report Manager&#41;</span></span>](../configure-general-properties-for-a-report-report-manager.md)  
  
  
