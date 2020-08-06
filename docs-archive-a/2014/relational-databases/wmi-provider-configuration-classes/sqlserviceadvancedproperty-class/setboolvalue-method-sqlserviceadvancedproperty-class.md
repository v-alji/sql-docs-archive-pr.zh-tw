---
title: 設定中斷點 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.setbreakpoints.f1
helpviewer_keywords:
- Set Breakpoints dialog box
ms.assetid: 876e61b7-875c-43f4-bbce-d7eeb90f6730
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 8115fcd845ee5ff415d13aa4fe36230234e33ca0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706318"
---
# <a name="set-breakpoints"></a><span data-ttu-id="c3f04-102">[設定中斷點]</span><span class="sxs-lookup"><span data-stu-id="c3f04-102">Set Breakpoints</span></span>
  <span data-ttu-id="c3f04-103">使用 **[設定中斷點]** 對話方塊，即可指定要啟用中斷點的事件並控制中斷點的行為。</span><span class="sxs-lookup"><span data-stu-id="c3f04-103">Use the **Set Breakpoints** dialog box to specify the events on which to enable breakpoints and to control the behavior of the breakpoint.</span></span>  
  
## <a name="options"></a><span data-ttu-id="c3f04-104">選項。</span><span class="sxs-lookup"><span data-stu-id="c3f04-104">Options</span></span>  
 <span data-ttu-id="c3f04-105">**已啟用**</span><span class="sxs-lookup"><span data-stu-id="c3f04-105">**Enabled**</span></span>  
 <span data-ttu-id="c3f04-106">選取即可在事件上啟用中斷點。</span><span class="sxs-lookup"><span data-stu-id="c3f04-106">Select to enable a breakpoint on an event.</span></span>  
  
 <span data-ttu-id="c3f04-107">**Break Condition**</span><span class="sxs-lookup"><span data-stu-id="c3f04-107">**Break Condition**</span></span>  
 <span data-ttu-id="c3f04-108">檢視要設定中斷點之可用事件的清單。</span><span class="sxs-lookup"><span data-stu-id="c3f04-108">View a list of available events on which to set breakpoints.</span></span>  
  
 <span data-ttu-id="c3f04-109">**Hit Count Type**</span><span class="sxs-lookup"><span data-stu-id="c3f04-109">**Hit Count Type**</span></span>  
 <span data-ttu-id="c3f04-110">指定中斷點生效的時間。</span><span class="sxs-lookup"><span data-stu-id="c3f04-110">Specify when the breakpoint takes effect.</span></span>  
  
|<span data-ttu-id="c3f04-111">值</span><span class="sxs-lookup"><span data-stu-id="c3f04-111">Value</span></span>|<span data-ttu-id="c3f04-112">描述</span><span class="sxs-lookup"><span data-stu-id="c3f04-112">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="c3f04-113">**永遠**</span><span class="sxs-lookup"><span data-stu-id="c3f04-113">**Always**</span></span>|<span data-ttu-id="c3f04-114">叫用中斷點時，一律暫停執行。</span><span class="sxs-lookup"><span data-stu-id="c3f04-114">Execution is always suspended when the breakpoint is hit.</span></span>|  
|<span data-ttu-id="c3f04-115">**叫用計數等於**</span><span class="sxs-lookup"><span data-stu-id="c3f04-115">**Hit count equals**</span></span>|<span data-ttu-id="c3f04-116">當中斷點發生的次數等於叫用計數時，暫停執行。</span><span class="sxs-lookup"><span data-stu-id="c3f04-116">Execution is suspended when the number of times the breakpoint has occurred is equal to the hit count.</span></span>|  
|<span data-ttu-id="c3f04-117">**叫用大於或等於**</span><span class="sxs-lookup"><span data-stu-id="c3f04-117">**Hit greater or equal**</span></span>|<span data-ttu-id="c3f04-118">當中斷點發生的次數大於或等於叫用計數時，暫停執行。</span><span class="sxs-lookup"><span data-stu-id="c3f04-118">Execution is suspended when the number of times the breakpoint has occurred is equal to or greater than the hit count.</span></span>|  
|<span data-ttu-id="c3f04-119">**叫用計數倍數**</span><span class="sxs-lookup"><span data-stu-id="c3f04-119">**Hit count multiple**</span></span>|<span data-ttu-id="c3f04-120">每當到達叫用計數的倍數時，暫停執行。</span><span class="sxs-lookup"><span data-stu-id="c3f04-120">Execution is suspended when a multiple of the hit count occurs.</span></span> <span data-ttu-id="c3f04-121">例如，若您將此選項設定為 5，則每到達五次叫用便會暫停執行。</span><span class="sxs-lookup"><span data-stu-id="c3f04-121">For example, if you set this option to 5, execution is suspended every fifth time.</span></span>|  
  
 <span data-ttu-id="c3f04-122">**叫用計數**</span><span class="sxs-lookup"><span data-stu-id="c3f04-122">**Hit Count**</span></span>  
 <span data-ttu-id="c3f04-123">指定觸發中斷的叫用次數。</span><span class="sxs-lookup"><span data-stu-id="c3f04-123">Specify the number of hits at which to trigger a break.</span></span> <span data-ttu-id="c3f04-124">如果中斷點永遠有效，則無法使用此選項。</span><span class="sxs-lookup"><span data-stu-id="c3f04-124">This option is not available if the breakpoint is always in effect.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3f04-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c3f04-125">See Also</span></span>  
 [<span data-ttu-id="c3f04-126">偵錯控制流程</span><span class="sxs-lookup"><span data-stu-id="c3f04-126">Debugging Control Flow</span></span>](../../../integration-services/troubleshooting/debugging-control-flow.md)  
  
  
