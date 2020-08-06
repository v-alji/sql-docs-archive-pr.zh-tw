---
title: Database 事件類別目錄 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- event classes [SQL Server], Database event category
- Database event category [SQL Server]
- SQL Server event classes, Database event category
ms.assetid: b61af738-f144-4992-b0b2-d44cb7240991
author: stevestein
ms.author: sstein
ms.openlocfilehash: 2860e1434611393c941a639280343f736073c709
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597839"
---
# <a name="database-event-category"></a><span data-ttu-id="0848a-102">Database 事件類別目錄</span><span class="sxs-lookup"><span data-stu-id="0848a-102">Database Event Category</span></span>
  <span data-ttu-id="0848a-103">**Database** 事件類別目錄包含用來監視 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]的事件類別。</span><span class="sxs-lookup"><span data-stu-id="0848a-103">The **Database** event category contains event classes to monitor the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0848a-104">本節內容</span><span class="sxs-lookup"><span data-stu-id="0848a-104">In This Section</span></span>  
  
|<span data-ttu-id="0848a-105">主題</span><span class="sxs-lookup"><span data-stu-id="0848a-105">Topic</span></span>|<span data-ttu-id="0848a-106">描述</span><span class="sxs-lookup"><span data-stu-id="0848a-106">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="0848a-107">Data File Auto Grow 事件類別</span><span class="sxs-lookup"><span data-stu-id="0848a-107">Data File Auto Grow Event Class</span></span>](data-file-auto-grow-event-class.md)|<span data-ttu-id="0848a-108">表示資料檔案自動成長。</span><span class="sxs-lookup"><span data-stu-id="0848a-108">Indicates that the data file grew automatically.</span></span> <span data-ttu-id="0848a-109">如果以外顯方式透過 ALTER DATABASE 讓資料檔案成長，則不會觸發這個事件。</span><span class="sxs-lookup"><span data-stu-id="0848a-109">This event is not triggered if the data file is grown explicitly through ALTER DATABASE.</span></span>|  
|[<span data-ttu-id="0848a-110">Data File Auto Shrink 事件類別</span><span class="sxs-lookup"><span data-stu-id="0848a-110">Data File Auto Shrink Event Class</span></span>](data-file-auto-shrink-event-class.md)|<span data-ttu-id="0848a-111">指出資料檔案已壓縮。</span><span class="sxs-lookup"><span data-stu-id="0848a-111">Indicates that the data file has been shrunk.</span></span>|  
|[<span data-ttu-id="0848a-112">Database Mirroring Connection 事件類別</span><span class="sxs-lookup"><span data-stu-id="0848a-112">Database Mirroring Connection Event Class</span></span>](database-mirroring-connection-event-class.md)|<span data-ttu-id="0848a-113">為報告資料庫鏡像的傳輸連接狀態而產生的事件。</span><span class="sxs-lookup"><span data-stu-id="0848a-113">An event generated to report the status of a transport connection for database mirroring.</span></span>|  
|[<span data-ttu-id="0848a-114">Database Mirroring State Change 事件類別</span><span class="sxs-lookup"><span data-stu-id="0848a-114">Database Mirroring State Change Event Class</span></span>](database-mirroring-state-change-event-class.md)|<span data-ttu-id="0848a-115">指出鏡像資料庫的狀態何時變更。</span><span class="sxs-lookup"><span data-stu-id="0848a-115">Indicates when the state of a mirrored database changes.</span></span>|  
|[<span data-ttu-id="0848a-116">Database Suspect Data Page 事件類別</span><span class="sxs-lookup"><span data-stu-id="0848a-116">Database Suspect Data Page Event Class</span></span>](database-suspect-data-page-event-class.md)|<span data-ttu-id="0848a-117">指出頁面何時加入至 **msdb** 資料庫中的 **suspect_pages** 資料表。</span><span class="sxs-lookup"><span data-stu-id="0848a-117">Indicates when a page is added to the **suspect_pages** table in the **msdb** database.</span></span>|  
|[<span data-ttu-id="0848a-118">Log File Auto Grow 事件類別</span><span class="sxs-lookup"><span data-stu-id="0848a-118">Log File Auto Grow Event Class</span></span>](log-file-auto-grow-event-class.md)|<span data-ttu-id="0848a-119">表示記錄檔自動成長。</span><span class="sxs-lookup"><span data-stu-id="0848a-119">Indicates that the log file grew automatically.</span></span> <span data-ttu-id="0848a-120">如果以外顯方式透過 ALTER DATABASE 讓記錄檔增長，則不會觸發這個事件。</span><span class="sxs-lookup"><span data-stu-id="0848a-120">This event is not triggered if the log file is grown explicitly through ALTER DATABASE.</span></span>|  
|[<span data-ttu-id="0848a-121">Log File Auto Shrink 事件類別</span><span class="sxs-lookup"><span data-stu-id="0848a-121">Log File Auto Shrink Event Class</span></span>](log-file-auto-shrink-event-class.md)|<span data-ttu-id="0848a-122">表示記錄檔自動成長。</span><span class="sxs-lookup"><span data-stu-id="0848a-122">Indicates that the log file grew automatically.</span></span> <span data-ttu-id="0848a-123">如果透過 ALTER DATABASE 來明確壓縮記錄檔，則不會觸發此事件。</span><span class="sxs-lookup"><span data-stu-id="0848a-123">This event is not triggered if the log file shrinks explicitly through ALTER DATABASE.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0848a-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0848a-124">See Also</span></span>  
 [<span data-ttu-id="0848a-125">擴充事件</span><span class="sxs-lookup"><span data-stu-id="0848a-125">Extended Events</span></span>](../extended-events/extended-events.md)  
  
  
