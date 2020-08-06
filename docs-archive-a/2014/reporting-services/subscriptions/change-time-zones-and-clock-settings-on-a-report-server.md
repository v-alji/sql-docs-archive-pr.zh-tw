---
title: 變更報表伺服器上的時區和時鐘設定 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- time zones [Reporting Services]
- clocks [Reporting Services]
- schedules [Reporting Services], clock settings
- schedules [Reporting Services], time zones
ms.assetid: 69a19468-baa1-40f6-b158-8afdab0f8968
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 566e421cd120010ea32f6936853e4319ec2efa11
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706998"
---
# <a name="change-time-zones-and-clock-settings-on-a-report-server"></a><span data-ttu-id="d2eee-102">變更報表伺服器上的時區和時鐘設定</span><span class="sxs-lookup"><span data-stu-id="d2eee-102">Change Time Zones and Clock Settings on a Report Server</span></span>
  <span data-ttu-id="d2eee-103">報表伺服器會永遠使用所安裝之電腦的本地時間。</span><span class="sxs-lookup"><span data-stu-id="d2eee-103">A report server always uses the local time of the computer on which it is installed.</span></span> <span data-ttu-id="d2eee-104">您無法設定使用不同時區。</span><span class="sxs-lookup"><span data-stu-id="d2eee-104">You cannot configure it to use a different time zone.</span></span> <span data-ttu-id="d2eee-105">如果用戶端應用程式指向不同時區的報表伺服器，就會使用該報表伺服器的時區來執行排程作業。</span><span class="sxs-lookup"><span data-stu-id="d2eee-105">If a client application points to a report server in a different time zone, the report server time zone is used to execute a scheduled operation.</span></span> <span data-ttu-id="d2eee-106">在報表管理員和 SharePoint 管理頁面中，每個排程頁面都會顯示時區設定，好讓您確實知道已排程作業將發生的時候。</span><span class="sxs-lookup"><span data-stu-id="d2eee-106">In Report Manager and SharePoint management pages, the time zone is indicated on each scheduling page so that you know exactly when a scheduled operation will occur.</span></span> <span data-ttu-id="d2eee-107">例如，用來建立自訂排程的頁面將會標示「時間是以 (UTC-08:00) 太平洋時間 (美國和加拿大) 格式表示」。</span><span class="sxs-lookup"><span data-stu-id="d2eee-107">For example, the page for creating custom schedules will note "Times are expressed in (UTC-08:00) Pacific time (US and Canada)."</span></span>  
  
## <a name="changing-the-time-zone-native-mode"></a><span data-ttu-id="d2eee-108">變更時區 (原生模式)</span><span class="sxs-lookup"><span data-stu-id="d2eee-108">Changing the Time Zone (Native Mode)</span></span>  
 <span data-ttu-id="d2eee-109">如果您變更了主控報表伺服器之電腦上的時區，就必須重新啟動報表伺服器服務，才能使時區變更生效。</span><span class="sxs-lookup"><span data-stu-id="d2eee-109">If you change the time zone on a computer hosting a report server, you must restart the Report Server service in order for the time zone change to take effect.</span></span>  
  
 <span data-ttu-id="d2eee-110">現有報表記錄快照集的時間戳記值會與新的時區設定進行同步處理。</span><span class="sxs-lookup"><span data-stu-id="d2eee-110">Timestamp values of existing report history snapshots are synchronized to the new time zone setting.</span></span> <span data-ttu-id="d2eee-111">若您在上午 9:00 產生一個報表記錄快照集，然後將時區重設為早一個時區，則已產生快照集上的時間戳記將會從上午 9:00</span><span class="sxs-lookup"><span data-stu-id="d2eee-111">If you generated a report history snapshot at 9:00 A.M., and then reset the time zone ahead one time zone, the timestamp on the generated snapshot will change from 9:00 A.M.</span></span> <span data-ttu-id="d2eee-112">變成上午 10:00。</span><span class="sxs-lookup"><span data-stu-id="d2eee-112">to 10:00 A.M.</span></span>  
  
 <span data-ttu-id="d2eee-113">排程會仍保留現有設定，除非有對應到新的時區。</span><span class="sxs-lookup"><span data-stu-id="d2eee-113">Schedules retain existing settings, except that they are mapped to the new time zone.</span></span> <span data-ttu-id="d2eee-114">例如，若排程在太平洋標準時間上午 2:00 執行，</span><span class="sxs-lookup"><span data-stu-id="d2eee-114">For example, if a schedule runs at 2:00 A.M.</span></span> <span data-ttu-id="d2eee-115">而您將時區變更為東澳標準時間，則排程就會在東澳標準時間</span><span class="sxs-lookup"><span data-stu-id="d2eee-115">Pacific Standard Time and you change the time zone to East Australia Standard Time, the schedule runs at 2:00 A.M.</span></span> <span data-ttu-id="d2eee-116">上午 2:00 執行。</span><span class="sxs-lookup"><span data-stu-id="d2eee-116">East Australia Standard Time.</span></span>  
  
 <span data-ttu-id="d2eee-117">屬性時間戳記值 (例如，資料夾或連結報表項目的建立時間) 則不會與新的時區設定進行同步處理。</span><span class="sxs-lookup"><span data-stu-id="d2eee-117">Property timestamp values (for example, the time at which a folder or linked report item is created) are not synchronized to a new time zone setting.</span></span> <span data-ttu-id="d2eee-118">如果您在 6 月 25 日的上午 9:00 建立一個項目，然後重設時區或時鐘，則時間戳記仍會保留為 6 月 25 日的上午 9:00。</span><span class="sxs-lookup"><span data-stu-id="d2eee-118">If you create an item on June 25 at 9:00 A.M., and then reset the time zone or clock, the timestamp remains June 25 at 9:00 A.M.</span></span>  
  
## <a name="changing-the-time-zone-sharepoint-mode"></a><span data-ttu-id="d2eee-119">變更時區 (SharePoint 模式)</span><span class="sxs-lookup"><span data-stu-id="d2eee-119">Changing the Time Zone (SharePoint Mode)</span></span>  
 <span data-ttu-id="d2eee-120">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint 模式的時區組態會當做 SharePoint 地區設定的一部分來管理。</span><span class="sxs-lookup"><span data-stu-id="d2eee-120">The time zone configuration for [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint mode is managed as part of the SharePoint regional settings.</span></span> <span data-ttu-id="d2eee-121">如需詳細資訊，請參閱[區域設定 (SharePoint Server 2010 (https://technet.microsoft.com/library/cc824907.aspx)](https://technet.microsoft.com/library/cc824907.aspx)。</span><span class="sxs-lookup"><span data-stu-id="d2eee-121">For more information, see [Regional settings (SharePoint Server 2010 (https://technet.microsoft.com/library/cc824907.aspx)](https://technet.microsoft.com/library/cc824907.aspx).</span></span>  
  
## <a name="changing-the-clock-settings"></a><span data-ttu-id="d2eee-122">變更時鐘設定</span><span class="sxs-lookup"><span data-stu-id="d2eee-122">Changing the Clock Settings</span></span>  
 <span data-ttu-id="d2eee-123">變更電腦時鐘不會影響現有的時間戳記值 (例如，若您將時間往前調一小時，報表記錄快照集的時間戳記並不會變更)。</span><span class="sxs-lookup"><span data-stu-id="d2eee-123">Changing the computer clock has no effect on existing timestamp values (for example, if you move the clock forward an hour, the timestamps of report history snapshots do not change).</span></span> <span data-ttu-id="d2eee-124">在排程與傳遞處理器使用新的設定以前，可能會有 10 秒的延遲。</span><span class="sxs-lookup"><span data-stu-id="d2eee-124">There may be a delay of 10 seconds before the Scheduling and Delivery Processor uses the new setting.</span></span> <span data-ttu-id="d2eee-125">如果您有在組態檔中修改輪詢間隔設定，實際的延遲就會因設定而異。</span><span class="sxs-lookup"><span data-stu-id="d2eee-125">The actual delay may vary if you modified polling interval settings in the configuration files.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2eee-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d2eee-126">See Also</span></span>  
 <span data-ttu-id="d2eee-127">[啟動與停止 Report Server 服務](../report-server/start-and-stop-the-report-server-service.md) </span><span class="sxs-lookup"><span data-stu-id="d2eee-127">[Start and Stop the Report Server Service](../report-server/start-and-stop-the-report-server-service.md) </span></span>  
 [<span data-ttu-id="d2eee-128">排程</span><span class="sxs-lookup"><span data-stu-id="d2eee-128">Schedules</span></span>](schedules.md)  
  
  
