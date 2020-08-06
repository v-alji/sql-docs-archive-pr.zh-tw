---
title: 伺服器屬性 (歷程記錄頁面) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.swb.reportserver.serverproperties.history.f1
ms.assetid: be9d8018-a46f-4625-9ae1-138ebe6b38ba
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: df5ff9dc7a94431f8feec112d460938aa1631ef2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597012"
---
# <a name="server-properties-history-page"></a><span data-ttu-id="620eb-102">伺服器多個屬性 (記錄頁面)</span><span class="sxs-lookup"><span data-stu-id="620eb-102">Server Properties (History Page)</span></span>
  <span data-ttu-id="620eb-103">使用此頁面，即可設定要保留之報表記錄副本數目的預設值。</span><span class="sxs-lookup"><span data-stu-id="620eb-103">Use this page to set a default value for the number of copies of report history to retain.</span></span> <span data-ttu-id="620eb-104">預設值會提供建立所有報表之報表記錄限制的初始設定。</span><span class="sxs-lookup"><span data-stu-id="620eb-104">The default value provides an initial setting that establishes report history limits for all reports.</span></span> <span data-ttu-id="620eb-105">您可以針對個別報表更改這些設定。</span><span class="sxs-lookup"><span data-stu-id="620eb-105">You can vary these settings for individual reports.</span></span>  
  
 <span data-ttu-id="620eb-106">報表記錄是報表快照集的集合，包括在建立快照集時對於報表而言是最新的報表資料和配置。</span><span class="sxs-lookup"><span data-stu-id="620eb-106">Report history is a collection of report snapshots that include report data and layout that is current for the report at the time the snapshot is created.</span></span> <span data-ttu-id="620eb-107">您可以使用報表記錄來保留某份報表在特定日期或時間的副本。</span><span class="sxs-lookup"><span data-stu-id="620eb-107">You can use report history to keep a copy of a report as it was on a specific date or time.</span></span> <span data-ttu-id="620eb-108">您可以針對在原生模式報表伺服器上或設定為 SharePoint 整合模式之報表伺服器上執行的個別報表，建立和管理報表記錄。</span><span class="sxs-lookup"><span data-stu-id="620eb-108">You can create and manage report history for individual reports that run on a native mode report server or a report server that is configured for SharePoint integrated mode.</span></span>  
  
 <span data-ttu-id="620eb-109">報表記錄快照集會儲存在報表伺服器資料庫中。</span><span class="sxs-lookup"><span data-stu-id="620eb-109">Report history snapshots are stored in the report server database.</span></span> <span data-ttu-id="620eb-110">如果您保留無限數量的快照集，請務必定期檢查資料庫大小，以便確保它的成長速度不會過快或耗用過多磁碟空間。</span><span class="sxs-lookup"><span data-stu-id="620eb-110">If you keep an unlimited number of snapshots, be sure to periodically check the database size to ensure it is not growing too fast or consuming too much disk space.</span></span>  
  
 <span data-ttu-id="620eb-111">若要開啟此頁面，請啟動 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]、連接至報表伺服器執行個體、以滑鼠右鍵按一下報表伺服器名稱，然後選取 [屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="620eb-111">To open this page, start [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connect to a report server instance, right-click the report server name, and select **Properties**.</span></span> <span data-ttu-id="620eb-112">按一下 **[記錄]** ，即可開啟此頁面。</span><span class="sxs-lookup"><span data-stu-id="620eb-112">Click **History** to open this page.</span></span>  
  
## <a name="options"></a><span data-ttu-id="620eb-113">選項</span><span class="sxs-lookup"><span data-stu-id="620eb-113">Options</span></span>  
 <span data-ttu-id="620eb-114">**不限制報表記錄中的快照集數目**</span><span class="sxs-lookup"><span data-stu-id="620eb-114">**Keep an unlimited number of snapshots in report history**</span></span>  
 <span data-ttu-id="620eb-115">保留所有報表記錄快照集。</span><span class="sxs-lookup"><span data-stu-id="620eb-115">Retain all report history snapshots.</span></span> <span data-ttu-id="620eb-116">您必須手動刪除快照集以縮減報表記錄的大小。</span><span class="sxs-lookup"><span data-stu-id="620eb-116">You must manually delete snapshots to reduce the size of report history.</span></span>  
  
 <span data-ttu-id="620eb-117">**限制報表記錄的副本**</span><span class="sxs-lookup"><span data-stu-id="620eb-117">**Limit the copies of report history**</span></span>  
 <span data-ttu-id="620eb-118">保留固定數目的報表記錄快照集。</span><span class="sxs-lookup"><span data-stu-id="620eb-118">Retain a set number of report history snapshots.</span></span> <span data-ttu-id="620eb-119">當達到限制時，就會從報表記錄中移除較舊的複本，增加較新複本所需的空間。</span><span class="sxs-lookup"><span data-stu-id="620eb-119">When the limit is reached, older copies are removed from report history to make room for newer copies.</span></span>  
  
 <span data-ttu-id="620eb-120">如果稍後限制報表記錄，則當現有的報表記錄超過指定的限制時，報表伺服器會將現有的報表記錄縮減至低於新限制的量。</span><span class="sxs-lookup"><span data-stu-id="620eb-120">If you limit report history later, when the existing report history exceeds the limit you specify, the report server reduces the existing report history to the new limit.</span></span> <span data-ttu-id="620eb-121">會先刪除最舊的報表快照集。</span><span class="sxs-lookup"><span data-stu-id="620eb-121">The oldest report snapshots are deleted first.</span></span> <span data-ttu-id="620eb-122">如果報表記錄為空白或在限制以下，則會加入新報表快照集。</span><span class="sxs-lookup"><span data-stu-id="620eb-122">If report history is empty or below the limit, new report snapshots are added.</span></span> <span data-ttu-id="620eb-123">如果達到限制，加入新報表快照集時會刪除最舊的快照集。</span><span class="sxs-lookup"><span data-stu-id="620eb-123">When the limit is reached, the oldest snapshot is deleted when a new report snapshot is added.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="620eb-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="620eb-124">See Also</span></span>  
 <span data-ttu-id="620eb-125">[將報表伺服器屬性設定 &#40;Management Studio&#41;](set-report-server-properties-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="620eb-125">[Set Report Server Properties &#40;Management Studio&#41;](set-report-server-properties-management-studio.md) </span></span>  
 <span data-ttu-id="620eb-126">[連接到 Management Studio 中的報表伺服器](connect-to-a-report-server-in-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="620eb-126">[Connect to a Report Server in Management Studio](connect-to-a-report-server-in-management-studio.md) </span></span>  
 [<span data-ttu-id="620eb-127">Management Studio F1 說明中的報表伺服器</span><span class="sxs-lookup"><span data-stu-id="620eb-127">Report Server in Management Studio F1 Help</span></span>](report-server-in-management-studio-f1-help.md)  
  
  
