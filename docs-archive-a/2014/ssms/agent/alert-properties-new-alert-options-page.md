---
title: 警示屬性：新增警示 (選項頁面) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.ag.alert.options.f1
ms.assetid: 6e4f41aa-832d-46ba-b6b5-cf1d3b15d33f
author: stevestein
ms.author: sstein
ms.openlocfilehash: 4a1507372aa1516c2a88b8682faa77a7d57e58f9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705906"
---
# <a name="alert-properties-new-alert-options-page"></a><span data-ttu-id="6e240-102">警示屬性：新增警示 (選項頁面)</span><span class="sxs-lookup"><span data-stu-id="6e240-102">Alert Properties: New Alert (Options Page)</span></span>
  <span data-ttu-id="6e240-103">使用此頁面來查看及修改 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 警示的選項。</span><span class="sxs-lookup"><span data-stu-id="6e240-103">Use this page to view and modify options for [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent alerts.</span></span>  
  
## <a name="options"></a><span data-ttu-id="6e240-104">選項</span><span class="sxs-lookup"><span data-stu-id="6e240-104">Options</span></span>  
 <span data-ttu-id="6e240-105">**位址**</span><span class="sxs-lookup"><span data-stu-id="6e240-105">**E-mail**</span></span>  
 <span data-ttu-id="6e240-106">在電子郵件通知內包含事件中的錯誤文字 (如果有的話)。</span><span class="sxs-lookup"><span data-stu-id="6e240-106">Include error text from the event, if any, in e-mail notifications.</span></span>  
  
 <span data-ttu-id="6e240-107">**呼叫器**</span><span class="sxs-lookup"><span data-stu-id="6e240-107">**Pager**</span></span>  
 <span data-ttu-id="6e240-108">在呼叫器通知內包含事件中的錯誤文字 (如果有的話)。</span><span class="sxs-lookup"><span data-stu-id="6e240-108">Include error text from the event, if any, in pager notifications.</span></span>  
  
 <span data-ttu-id="6e240-109">**Net send**</span><span class="sxs-lookup"><span data-stu-id="6e240-109">**Net send**</span></span>  
 <span data-ttu-id="6e240-110">在 Net Send 通知內包含事件中的錯誤文字 (如果有的話)。</span><span class="sxs-lookup"><span data-stu-id="6e240-110">Include error text from the event, if any, in net send notifications.</span></span>  
  
 <span data-ttu-id="6e240-111">**要傳送的其他通知訊息**</span><span class="sxs-lookup"><span data-stu-id="6e240-111">**Additional notification message to send**</span></span>  
 <span data-ttu-id="6e240-112">鍵入要包含在通知訊息中的其他文字。</span><span class="sxs-lookup"><span data-stu-id="6e240-112">Type any additional text to include in notification messages.</span></span>  
  
 <span data-ttu-id="6e240-113">**回應間隔延遲**</span><span class="sxs-lookup"><span data-stu-id="6e240-113">**Delay between responses**</span></span>  
 <span data-ttu-id="6e240-114">指定事件重複發生的延遲。</span><span class="sxs-lookup"><span data-stu-id="6e240-114">Specify a delay for repeated occurrences of the event.</span></span> <span data-ttu-id="6e240-115">某些事件會在短期間內頻繁發生。</span><span class="sxs-lookup"><span data-stu-id="6e240-115">Some events may occur frequently during a short period of time.</span></span> <span data-ttu-id="6e240-116">在此情況下，您可能想要知道事件是否已經發生，但不要讓每個事件都產生回應。</span><span class="sxs-lookup"><span data-stu-id="6e240-116">In this case, you may want to know that the event has occurred, but you may not want a response for every event.</span></span> <span data-ttu-id="6e240-117">使用此選項來指定超時時間。若有延遲，在警示回應事件之後， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 會等候指定的延遲，然後再次回應，而不論事件是否發生在延遲期間。</span><span class="sxs-lookup"><span data-stu-id="6e240-117">Use this option to specify a time-out. With a delay, after the alert responds to an event, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent waits for the delay specified before responding again, regardless of whether the event occurs during the delay.</span></span>  
  
 <span data-ttu-id="6e240-118">**細節**</span><span class="sxs-lookup"><span data-stu-id="6e240-118">**Minutes**</span></span>  
 <span data-ttu-id="6e240-119">指定延遲，以分鐘為單位。</span><span class="sxs-lookup"><span data-stu-id="6e240-119">Specify a delay in minutes.</span></span> <span data-ttu-id="6e240-120">若要在每一次發生事件時產生回應，請指定 0 分和 0 秒。</span><span class="sxs-lookup"><span data-stu-id="6e240-120">To respond every time the event occurs, specify 0 minutes and 0 seconds.</span></span>  
  
 <span data-ttu-id="6e240-121">**表示**</span><span class="sxs-lookup"><span data-stu-id="6e240-121">**Seconds**</span></span>  
 <span data-ttu-id="6e240-122">指定延遲，以秒為單位。</span><span class="sxs-lookup"><span data-stu-id="6e240-122">Specify a delay in seconds.</span></span> <span data-ttu-id="6e240-123">若要在每一次發生事件時產生回應，請指定 0 分和 0 秒。</span><span class="sxs-lookup"><span data-stu-id="6e240-123">To respond every time the event occurs, specify 0 minutes and 0 seconds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e240-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6e240-124">See Also</span></span>  
 [<span data-ttu-id="6e240-125">警示</span><span class="sxs-lookup"><span data-stu-id="6e240-125">Alerts</span></span>](alerts.md)  
  
  
