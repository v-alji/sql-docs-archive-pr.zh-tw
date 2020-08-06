---
title: 編寫擴充事件會話的腳本 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 80f9fdde-1f13-4292-a4fc-55da826be3b4
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 11adc60ae7c7e0f8b8012d06f56c83874d3708ba
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594672"
---
# <a name="script-an-extended-event-session"></a><span data-ttu-id="a9c69-102">編寫擴充事件工作階段的指令碼</span><span class="sxs-lookup"><span data-stu-id="a9c69-102">Script an Extended Event Session</span></span>
  <span data-ttu-id="a9c69-103">本主題說明如何編寫事件工作階段的指令碼。</span><span class="sxs-lookup"><span data-stu-id="a9c69-103">This topic describes how to script an event session.</span></span> <span data-ttu-id="a9c69-104">您可以匯出、更改或卸除事件工作階段，或是在以下目標中卸除及建立事件工作階段：</span><span class="sxs-lookup"><span data-stu-id="a9c69-104">You can export, alter, or drop the event session, or drop and create the event session to the following:</span></span>  
  
-   <span data-ttu-id="a9c69-105">**新增查詢編輯器視窗**</span><span class="sxs-lookup"><span data-stu-id="a9c69-105">**New Query Editor Window**</span></span>  
  
-   <span data-ttu-id="a9c69-106">**檔案**</span><span class="sxs-lookup"><span data-stu-id="a9c69-106">**File**</span></span>  
  
-   <span data-ttu-id="a9c69-107">**剪貼簿**</span><span class="sxs-lookup"><span data-stu-id="a9c69-107">**Clipboard**</span></span>  
  
-   <span data-ttu-id="a9c69-108">**代理程式作業**</span><span class="sxs-lookup"><span data-stu-id="a9c69-108">**Agent Job**</span></span>  
  
### <a name="to-script-an-existing-event-session"></a><span data-ttu-id="a9c69-109">若要編寫現有事件工作階段的指令碼</span><span class="sxs-lookup"><span data-stu-id="a9c69-109">To script an existing event session</span></span>  
  
1.  <span data-ttu-id="a9c69-110">在 [物件總管] 中，依序展開 **[管理]** 節點和 **[擴充事件]**。</span><span class="sxs-lookup"><span data-stu-id="a9c69-110">In Object Explorer, expand the **Management** node, and then expand **Extended Events**.</span></span>  
  
2.  <span data-ttu-id="a9c69-111">以滑鼠右鍵按一下您想要編寫指令碼的工作階段，並依序指向 **[編寫工作階段的指令碼為]** 和 **[CREATE 至]**，然後選取您想要編寫工作階段指令碼的地方。</span><span class="sxs-lookup"><span data-stu-id="a9c69-111">Right-click the session you want to script, point to **Script Session as**, point to **CREATE to**, and then select where you want to script the session.</span></span>  
  
### <a name="to-script-a-new-event-session"></a><span data-ttu-id="a9c69-112">若要編寫新的事件工作階段</span><span class="sxs-lookup"><span data-stu-id="a9c69-112">To script a new event session</span></span>  
  
1.  <span data-ttu-id="a9c69-113">在 [物件總管] 中，依序展開 **[管理]** 節點和 **[擴充事件]**。</span><span class="sxs-lookup"><span data-stu-id="a9c69-113">In Object Explorer, expand the **Management** node, and then expand **Extended Events**.</span></span>  
  
2.  <span data-ttu-id="a9c69-114">以滑鼠右鍵按一下 **[工作階段]**，然後按一下 **[新增工作階段]**。</span><span class="sxs-lookup"><span data-stu-id="a9c69-114">Right-click **Sessions**, and then click **New Session**.</span></span>  
  
3.  <span data-ttu-id="a9c69-115">在 **[新增工作階段]** UI 中，建立事件工作階段，然後從 **[指令碼]** 下拉式清單中選取您想要編寫事件工作階段指令碼的地方。</span><span class="sxs-lookup"><span data-stu-id="a9c69-115">In the **New Session** UI, create the event session, and then select where you want to script the event session from the **Script** drop-down list.</span></span>  
  
### <a name="to-script-a-modified-event-session"></a><span data-ttu-id="a9c69-116">若要編寫已修改之事件工作階段的指令碼</span><span class="sxs-lookup"><span data-stu-id="a9c69-116">To script a modified event session</span></span>  
  
1.  <span data-ttu-id="a9c69-117">在 [物件總管] 中，依序展開 **[管理]** 節點和 **[擴充事件]**。</span><span class="sxs-lookup"><span data-stu-id="a9c69-117">In Object Explorer, expand the **Management** node, and then expand **Extended Events**.</span></span>  
  
2.  <span data-ttu-id="a9c69-118">以滑鼠右鍵按一下您要修改的工作階段，然後按一下 **[屬性]**。</span><span class="sxs-lookup"><span data-stu-id="a9c69-118">Right-click the session you want to modify, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="a9c69-119">在 **[工作階段屬性]** 對話方塊中，修改事件工作階段，然後從 **[指令碼]** 下拉式清單中選取您想要編寫已修改之工作階段指令碼的地方。</span><span class="sxs-lookup"><span data-stu-id="a9c69-119">In the **Session Properties** dialog box, modify the event session, and then select where you want to script the modified session from the **Script** drop-down list.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9c69-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a9c69-120">See Also</span></span>  
 [<span data-ttu-id="a9c69-121">擴充事件</span><span class="sxs-lookup"><span data-stu-id="a9c69-121">Extended Events</span></span>](../relational-databases/extended-events/extended-events.md)  
  
  
