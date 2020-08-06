---
title: 更改擴充事件工作階段 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xevents
ms.topic: conceptual
ms.assetid: 114ec05b-7eca-4c87-b276-25e37b84be39
author: rothja
ms.author: jroth
ms.openlocfilehash: 14be41e48262bc7ebc8aeeaf55185f5e35d0c72e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584519"
---
# <a name="alter-an-extended-events-session"></a><span data-ttu-id="5f9c6-102">更改擴充事件工作階段</span><span class="sxs-lookup"><span data-stu-id="5f9c6-102">Alter an Extended Events Session</span></span>
  <span data-ttu-id="5f9c6-103">在您建立「擴充事件」工作階段之後，可以根據您的需求使用 **[SQL Server 擴充事件精靈]** 加以更改。</span><span class="sxs-lookup"><span data-stu-id="5f9c6-103">After you create an Extended Events session, you can alter it according to your needs using the **SQL Server Extended Events Wizard**.</span></span>  
  
## <a name="before-you-begin"></a><span data-ttu-id="5f9c6-104">開始之前</span><span class="sxs-lookup"><span data-stu-id="5f9c6-104">Before you Begin</span></span>  
 <span data-ttu-id="5f9c6-105">您不能更改使用中和非使用中工作階段的目標，而且不能更改使用中工作階段的進階屬性組態。</span><span class="sxs-lookup"><span data-stu-id="5f9c6-105">You cannot alter a target for active and inactive sessions, and you cannot change the advanced properties configurations for an active session.</span></span>  
  
 <span data-ttu-id="5f9c6-106">您可以對使用中和非使用中的事件工作階段進行以下更改：</span><span class="sxs-lookup"><span data-stu-id="5f9c6-106">You can make the following alterations to both active and inactive event sessions:</span></span>  
  
-   <span data-ttu-id="5f9c6-107">從工作階段加入或移除事件及更改事件組態，例如事件欄位、篩選和動作。</span><span class="sxs-lookup"><span data-stu-id="5f9c6-107">Add or remove events from the session, and alter the event configurations such as event fields, filters and actions.</span></span>  
  
-   <span data-ttu-id="5f9c6-108">從事件工作階段加入或移除目標。</span><span class="sxs-lookup"><span data-stu-id="5f9c6-108">Add or remove a target from the event session.</span></span>  
  
-   <span data-ttu-id="5f9c6-109">啟用 **[在伺服器啟動時啟動事件工作階段]** 選項。</span><span class="sxs-lookup"><span data-stu-id="5f9c6-109">Enable the **Start the event session on server startup** option.</span></span>  
  
 <span data-ttu-id="5f9c6-110">您可以對非使用中的事件工作階段進行以下的額外更改：</span><span class="sxs-lookup"><span data-stu-id="5f9c6-110">You can make the following additional alterations to an inactive event session:</span></span>  
  
-   <span data-ttu-id="5f9c6-111">啟用 **[追蹤事件之間的關聯性]** 選項。</span><span class="sxs-lookup"><span data-stu-id="5f9c6-111">Enable the **Track the relationship between events** option.</span></span>  
  
-   <span data-ttu-id="5f9c6-112">變更進階屬性組態。</span><span class="sxs-lookup"><span data-stu-id="5f9c6-112">Change the advanced properties configuration.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5f9c6-113">[SQL Server 擴充事件精靈]\*\*\*\* 不支援修改事件工作階段。</span><span class="sxs-lookup"><span data-stu-id="5f9c6-113">The **SQL Server Extended Events Wizard** does not support event session modification.</span></span>  
  
## <a name="how-to-alter-an-extended-events-session-using-the-sql-server-extended-events-wizard"></a><span data-ttu-id="5f9c6-114">如何使用 SQL Server 擴充事件精靈更改擴充事件工作階段</span><span class="sxs-lookup"><span data-stu-id="5f9c6-114">How to alter an Extended Events session using the SQL Server Extended Events Wizard</span></span>  
  
-   <span data-ttu-id="5f9c6-115">在物件總管中，依序展開 **[管理]**、 **[擴充事件]** 和 **[工作階段]**。</span><span class="sxs-lookup"><span data-stu-id="5f9c6-115">In Object Explorer, expand **Management**, expand **Extended Events**, and then expand **Sessions**.</span></span>  
  
-   <span data-ttu-id="5f9c6-116">以滑鼠右鍵按一下您要改變的工作階段，然後按一下 [屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="5f9c6-116">Right-click the session you want to alter, and then click **Properties**.</span></span>  
  
-   <span data-ttu-id="5f9c6-117">在 **[屬性]** 對話方塊中，進行適當的變更，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="5f9c6-117">In the **Properties** dialog box, make the appropriate changes, and then click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f9c6-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5f9c6-118">See Also</span></span>  
 <span data-ttu-id="5f9c6-119">[ALTER EVENT SESSION &#40;Transact-sql&#41;](/sql/t-sql/statements/alter-event-session-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="5f9c6-119">[ALTER EVENT SESSION &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-event-session-transact-sql) </span></span>  
 [<span data-ttu-id="5f9c6-120">使用查詢編輯器建立擴充事件工作階段</span><span class="sxs-lookup"><span data-stu-id="5f9c6-120">Create an Extended Events Session Using Query Editor</span></span>](../../database-engine/create-an-extended-events-session-using-query-editor.md)  
  
  
