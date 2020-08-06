---
title: 伺服器事件類別和屬性的 WMI 提供者 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
helpviewer_keywords:
- event classes [WMI]
- WMI Provider for Server Events, events listed
- classes [WMI]
ms.assetid: e2916cd7-a3ed-41e6-97b4-2ee060754cbe
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 471e77cb7afa4e6aed441dcbbc8b3b70064f6737
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707318"
---
# <a name="wmi-provider-for-server-events-classes-and-properties"></a><span data-ttu-id="6c39a-102">伺服器事件類別和屬性的 WMI 提供者</span><span class="sxs-lookup"><span data-stu-id="6c39a-102">WMI Provider for Server Events Classes and Properties</span></span>
  <span data-ttu-id="6c39a-103">下列伺服器事件會組成伺服器事件之 WMI 提供者的程式撰寫模型。</span><span class="sxs-lookup"><span data-stu-id="6c39a-103">The following server events make up the programming model for the WMI Provider for Server Events.</span></span> <span data-ttu-id="6c39a-104">有兩個主要類別目錄的事件，可以針對提供者發出 WQL 查詢來查詢這些事件。</span><span class="sxs-lookup"><span data-stu-id="6c39a-104">There are two main categories of events that can be queried by issuing WQL queries against the provider.</span></span> <span data-ttu-id="6c39a-105">這些是資料定義語言 (DDL) 事件和追蹤事件。</span><span class="sxs-lookup"><span data-stu-id="6c39a-105">These are data definition language (DDL) events and trace events.</span></span> <span data-ttu-id="6c39a-106">也可以查詢 QUEUE_ACTIVATION 和 BROKER_QUEUE_DISABLED Service Broker 事件。</span><span class="sxs-lookup"><span data-stu-id="6c39a-106">The QUEUE_ACTIVATION and BROKER_QUEUE_DISABLED service broker events can also be queried.</span></span> <span data-ttu-id="6c39a-107">請注意下列樹狀圖表的內含本質。</span><span class="sxs-lookup"><span data-stu-id="6c39a-107">Note the inclusive nature of the following tree diagrams.</span></span> <span data-ttu-id="6c39a-108">例如，DDL_ASSEMBLY_EVENTS 事件包含任何 ALTER_ASSEMBLY、CREATE_ASSEMBLY 和 DROP_ASSEMBLY 事件。</span><span class="sxs-lookup"><span data-stu-id="6c39a-108">The DDL_ASSEMBLY_EVENTS event, for example, includes any ALTER_ASSEMBLY, CREATE_ASSEMBLY, and DROP_ASSEMBLY event.</span></span> <span data-ttu-id="6c39a-109">同樣地，TRC_FULL_TEXT 事件包含任何 FT_CRAWL_ABORTED、FT_CRAWL_STARTED 和 FT_CRAWL_STOPPED 事件。</span><span class="sxs-lookup"><span data-stu-id="6c39a-109">Similarly, the TRC_FULL_TEXT event includes any FT_CRAWL_ABORTED, FT_CRAWL_STARTED, and FT_CRAWL_STOPPED event.</span></span> <span data-ttu-id="6c39a-110">ALL_EVENTS 涵蓋所有 DDL 事件、追蹤事件、QUEUE_ACTIVATION 和 BROKER_QUEUE_DISABLED。</span><span class="sxs-lookup"><span data-stu-id="6c39a-110">ALL_EVENTS covers all DDL events, trace events, QUEUE_ACTIVATION, and BROKER_QUEUE_DISABLED.</span></span>  
  
 <span data-ttu-id="6c39a-111">若要得知可以從事件或事件群組查詢哪些屬性，請參考事件結構描述。</span><span class="sxs-lookup"><span data-stu-id="6c39a-111">To learn which properties can be queried from an event or event group, refer to the event schema.</span></span> <span data-ttu-id="6c39a-112">根據預設，事件結構描述會安裝在以下目錄：[!INCLUDE[ssInstallPath](../../includes/ssinstallpath-md.md)]Tools\Binn\schemas\sqlserver\2006\11\events\events.xsd。</span><span class="sxs-lookup"><span data-stu-id="6c39a-112">By default, the event schema is installed in the following directory: [!INCLUDE[ssInstallPath](../../includes/ssinstallpath-md.md)]Tools\Binn\schemas\sqlserver\2006\11\events\events.xsd.</span></span>  
  
 <span data-ttu-id="6c39a-113">或者，您可以參考發佈于的事件架構 [https://schemas.microsoft.com/sqlserver](https://go.microsoft.com/fwlink/?linkid=43100) 。</span><span class="sxs-lookup"><span data-stu-id="6c39a-113">Alternatively, you can refer to the event schema published at [https://schemas.microsoft.com/sqlserver](https://go.microsoft.com/fwlink/?linkid=43100).</span></span>  
  
 <span data-ttu-id="6c39a-114">例如，藉由參考 ALTER_DATABASE 事件，您將會得知它的父事件為 DDL_SERVER_LEVEL_EVENTS，而它的屬性為 `TSQLCommand` 和 `DatabaseName`。</span><span class="sxs-lookup"><span data-stu-id="6c39a-114">For example, by referring to the ALTER_DATABASE event, you will learn that its parent event is DDL_SERVER_LEVEL_EVENTS and its properties are `TSQLCommand` and `DatabaseName`.</span></span> <span data-ttu-id="6c39a-115">此事件也會繼承 `SQLInstance`、`PostTime`、`ComputerName`、`SPID` 和 `LoginName` 屬性。</span><span class="sxs-lookup"><span data-stu-id="6c39a-115">The event also inherits the properties `SQLInstance`, `PostTime`, `ComputerName`, `SPID`, and `LoginName`.</span></span> <span data-ttu-id="6c39a-116">此事件沒有任何子事件。</span><span class="sxs-lookup"><span data-stu-id="6c39a-116">The event has no children events.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6c39a-117">執行類似 DDL 作業的系統預存程序也可以引發事件通知。</span><span class="sxs-lookup"><span data-stu-id="6c39a-117">System stored procedures that perform DDL-like operations can also fire event notifications.</span></span> <span data-ttu-id="6c39a-118">請測試事件通知以判斷它們對執行之系統預存程序的回應。</span><span class="sxs-lookup"><span data-stu-id="6c39a-118">Test your event notifications to determine their responses to system stored procedures that are run.</span></span> <span data-ttu-id="6c39a-119">例如，CREATE TYPE 語句和**sp_addtype**預存程式都會引發在 CREATE_TYPE 事件上建立的事件通知。</span><span class="sxs-lookup"><span data-stu-id="6c39a-119">For example, the CREATE TYPE statement and **sp_addtype** stored procedure will both fire an event notification that is created on a CREATE_TYPE event.</span></span> <span data-ttu-id="6c39a-120">如需詳細資訊，請參閱[DDL 事件](../../relational-databases/triggers/ddl-events.md)。</span><span class="sxs-lookup"><span data-stu-id="6c39a-120">For more information, see[DDL Events](../../relational-databases/triggers/ddl-events.md).</span></span>  
  
 <span data-ttu-id="6c39a-121">**資料定義語言事件和事件群組**</span><span class="sxs-lookup"><span data-stu-id="6c39a-121">**Data Definition Language Events and Event Groups**</span></span>  
  
 <span data-ttu-id="6c39a-122">![WMI Provider for Server Events 事件樹](../../../2014/database-engine/dev-guide/media/sql-wmi-ddl-events-ktm.gif "WMI Provider for Server Events 事件樹")</span><span class="sxs-lookup"><span data-stu-id="6c39a-122">![WMI Provider for Server Events Event Tree](../../../2014/database-engine/dev-guide/media/sql-wmi-ddl-events-ktm.gif "WMI Provider for Server Events Event Tree")</span></span>  
  
 <span data-ttu-id="6c39a-123">**追蹤事件和事件群組**</span><span class="sxs-lookup"><span data-stu-id="6c39a-123">**Trace Events and Event Groups**</span></span>  
  
 <span data-ttu-id="6c39a-124">![追蹤事件和事件群組](../../../2014/database-engine/dev-guide/media/sql-wmi-trc-all-events.gif "追蹤事件和事件群組")</span><span class="sxs-lookup"><span data-stu-id="6c39a-124">![Trace events and event groups](../../../2014/database-engine/dev-guide/media/sql-wmi-trc-all-events.gif "Trace events and event groups")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c39a-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6c39a-125">See Also</span></span>  
 <span data-ttu-id="6c39a-126">[伺服器事件的 WMI 提供者概念](../../relational-databases/wmi-provider-server-events/wmi-provider-for-server-events-concepts.md) </span><span class="sxs-lookup"><span data-stu-id="6c39a-126">[WMI Provider for Server Events Concepts](../../relational-databases/wmi-provider-server-events/wmi-provider-for-server-events-concepts.md) </span></span>  
 [<span data-ttu-id="6c39a-127">搭配伺服器事件的 WMI 提供者使用 WQL</span><span class="sxs-lookup"><span data-stu-id="6c39a-127">Using WQL with the WMI Provider for Server Events</span></span>](../../relational-databases/wmi-provider-server-events/using-wql-with-the-wmi-provider-for-server-events.md)  
  
  
