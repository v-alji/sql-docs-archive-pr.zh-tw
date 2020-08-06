---
title: 操作員屬性和 New 運算子 (一般頁面) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.ag.operator.general.f1
ms.assetid: c036d1c9-83d1-4a95-b67e-29d283b1a046
author: stevestein
ms.author: sstein
ms.openlocfilehash: 11ffd4a604275153a2bfe7071c442cc110815f81
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594331"
---
# <a name="operator-properties-and-new-operator-general-page"></a><span data-ttu-id="5a2d0-102">操作員屬性及新增操作員 (一般頁面)</span><span class="sxs-lookup"><span data-stu-id="5a2d0-102">Operator Properties and New Operator (General Page)</span></span>
  <span data-ttu-id="5a2d0-103">使用此頁面來查看和修改 Agent 操作員的一般屬性 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="5a2d0-103">Use this page to view and modify the general properties of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent operators.</span></span>  
  
## <a name="options"></a><span data-ttu-id="5a2d0-104">選項。</span><span class="sxs-lookup"><span data-stu-id="5a2d0-104">Options</span></span>  
 <span data-ttu-id="5a2d0-105">**名稱**</span><span class="sxs-lookup"><span data-stu-id="5a2d0-105">**Name**</span></span>  
 <span data-ttu-id="5a2d0-106">變更操作員的名稱。</span><span class="sxs-lookup"><span data-stu-id="5a2d0-106">Change the name of the operator.</span></span>  
  
 <span data-ttu-id="5a2d0-107">**已啟用**</span><span class="sxs-lookup"><span data-stu-id="5a2d0-107">**Enabled**</span></span>  
 <span data-ttu-id="5a2d0-108">啟用操作員。</span><span class="sxs-lookup"><span data-stu-id="5a2d0-108">Enable the operator.</span></span> <span data-ttu-id="5a2d0-109">未啟用時，不會傳送通知給操作員。</span><span class="sxs-lookup"><span data-stu-id="5a2d0-109">When not enabled, no notifications are sent to the operator.</span></span>  
  
 <span data-ttu-id="5a2d0-110">**電子郵件名稱**</span><span class="sxs-lookup"><span data-stu-id="5a2d0-110">**E-mail name**</span></span>  
 <span data-ttu-id="5a2d0-111">指定操作員的電子郵件地址。</span><span class="sxs-lookup"><span data-stu-id="5a2d0-111">Specifies the e-mail address for the operator.</span></span>  
  
 <span data-ttu-id="5a2d0-112">**Net Send 位址**</span><span class="sxs-lookup"><span data-stu-id="5a2d0-112">**Net send address**</span></span>  
 <span data-ttu-id="5a2d0-113">指定用於 **net send**的位址。</span><span class="sxs-lookup"><span data-stu-id="5a2d0-113">Specify the address to use for **net send**.</span></span>  
  
 <span data-ttu-id="5a2d0-114">**呼叫器電子郵件名稱**</span><span class="sxs-lookup"><span data-stu-id="5a2d0-114">**Pager e-mail name**</span></span>  
 <span data-ttu-id="5a2d0-115">指定操作員呼叫器所用的電子郵件地址。</span><span class="sxs-lookup"><span data-stu-id="5a2d0-115">Specifies the e-mail address to use for the operator's pager.</span></span>  
  
 <span data-ttu-id="5a2d0-116">**傳呼待命排程**</span><span class="sxs-lookup"><span data-stu-id="5a2d0-116">**Pager on duty schedule**</span></span>  
 <span data-ttu-id="5a2d0-117">設定呼叫器使用中的時間。</span><span class="sxs-lookup"><span data-stu-id="5a2d0-117">Sets the times at which the pager is active.</span></span>  
  
 <span data-ttu-id="5a2d0-118">**星期一至星期日**</span><span class="sxs-lookup"><span data-stu-id="5a2d0-118">**Monday - Sunday**</span></span>  
 <span data-ttu-id="5a2d0-119">選取呼叫器使用中的日子。</span><span class="sxs-lookup"><span data-stu-id="5a2d0-119">Select the days that the pager is active.</span></span>  
  
 <span data-ttu-id="5a2d0-120">**工作日開始**</span><span class="sxs-lookup"><span data-stu-id="5a2d0-120">**Workday begin**</span></span>  
 <span data-ttu-id="5a2d0-121">選取時間，在該時間之後 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 就會傳送訊息給呼叫器。</span><span class="sxs-lookup"><span data-stu-id="5a2d0-121">Select the time of day after which [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent sends messages to the pager.</span></span>  
  
 <span data-ttu-id="5a2d0-122">**工作日結束**</span><span class="sxs-lookup"><span data-stu-id="5a2d0-122">**Workday end**</span></span>  
 <span data-ttu-id="5a2d0-123">選取時間，在該時間之後 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 就不再傳送訊息給呼叫器。</span><span class="sxs-lookup"><span data-stu-id="5a2d0-123">Select the time of day after which [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent no longer sends messages to the pager.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a2d0-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5a2d0-124">See Also</span></span>  
 [<span data-ttu-id="5a2d0-125">運算子</span><span class="sxs-lookup"><span data-stu-id="5a2d0-125">Operators</span></span>](operators.md)  
  
  
