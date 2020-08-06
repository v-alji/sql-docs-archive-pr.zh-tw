---
title: 警示屬性-新增警示 (回應頁面) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.ag.alert.response.f1
ms.assetid: 72daf008-f9ea-4077-b217-5048e7759d3e
author: stevestein
ms.author: sstein
ms.openlocfilehash: 34e7f11ff3210ec4fc1835751bc35b140d3fa0ef
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705902"
---
# <a name="alert-properties-new-alert-response-page"></a><span data-ttu-id="1491c-102">警示屬性-新增警示 (回應頁面) </span><span class="sxs-lookup"><span data-stu-id="1491c-102">Alert Properties-New Alert (Response Page)</span></span>
  <span data-ttu-id="1491c-103">使用此頁面來指定您想要執行的作業，以及取得要通知的操作員清單來回應 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 警示。</span><span class="sxs-lookup"><span data-stu-id="1491c-103">Use this page to specify a job that you want to run and to obtain a list of operators to be notified in response to a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent alert.</span></span>  
  
## <a name="options"></a><span data-ttu-id="1491c-104">選項</span><span class="sxs-lookup"><span data-stu-id="1491c-104">Options</span></span>  
 <span data-ttu-id="1491c-105">**執行作業**</span><span class="sxs-lookup"><span data-stu-id="1491c-105">**Execute job**</span></span>  
 <span data-ttu-id="1491c-106">啟用 [作業清單]\*\*\*\*、[新增作業]\*\*\*\* 和 [檢視作業]\*\*\*\* 選項。</span><span class="sxs-lookup"><span data-stu-id="1491c-106">Enables the **Job list**, **New job** and **View job** options.</span></span>  
  
 <span data-ttu-id="1491c-107">**新增作業**</span><span class="sxs-lookup"><span data-stu-id="1491c-107">**New job**</span></span>  
 <span data-ttu-id="1491c-108">開啟 [新增作業]\*\*\*\* 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="1491c-108">Open the **New Job** dialog box.</span></span> <span data-ttu-id="1491c-109">未選取 [執行作業]\*\*\*\* 時，無法使用這個按鈕。</span><span class="sxs-lookup"><span data-stu-id="1491c-109">This button is not available when **Execute job** is not selected.</span></span>  
  
 <span data-ttu-id="1491c-110">**檢視工作**</span><span class="sxs-lookup"><span data-stu-id="1491c-110">**View job**</span></span>  
 <span data-ttu-id="1491c-111">檢視或修改選取的作業。</span><span class="sxs-lookup"><span data-stu-id="1491c-111">View or modify the selected job.</span></span> <span data-ttu-id="1491c-112">未選取 [執行作業]\*\*\*\* 時，無法使用這個選項。</span><span class="sxs-lookup"><span data-stu-id="1491c-112">This option is not available when **Execute job** is not selected.</span></span>  
  
 <span data-ttu-id="1491c-113">**通知操作員**</span><span class="sxs-lookup"><span data-stu-id="1491c-113">**Notify operators**</span></span>  
 <span data-ttu-id="1491c-114">可啟用讓您加入、移除或變更操作員的控制項。</span><span class="sxs-lookup"><span data-stu-id="1491c-114">Enables the controls that allow you to add, remove, or change operators.</span></span>  
  
 <span data-ttu-id="1491c-115">**操作員清單**</span><span class="sxs-lookup"><span data-stu-id="1491c-115">**Operator list**</span></span>  
 <span data-ttu-id="1491c-116">列出發生警示時所要通知的操作員。</span><span class="sxs-lookup"><span data-stu-id="1491c-116">Lists the operators to notify when an alert occurs.</span></span> <span data-ttu-id="1491c-117">若要指定通知方法，請選取顯示於操作員名稱之後的 [電子郵件]\*\*\*\*、[呼叫器]\*\*\*\* 或 [Net Send]\*\*\*\* 核取方塊。未選取 [通知操作員]\*\*\*\* 時，無法使用這個選項。</span><span class="sxs-lookup"><span data-stu-id="1491c-117">To specify a notification method, select the **E-mail**, **Pager**, or **Net send** check box that is displayed after the operator name.This option not available when **Notify operators** is not selected.</span></span>  
  
 <span data-ttu-id="1491c-118">**位址**</span><span class="sxs-lookup"><span data-stu-id="1491c-118">**E-mail**</span></span>  
 <span data-ttu-id="1491c-119">使用電子郵件通知操作員。</span><span class="sxs-lookup"><span data-stu-id="1491c-119">Use e-mail to notify the operator.</span></span>  
  
 <span data-ttu-id="1491c-120">**呼叫器**</span><span class="sxs-lookup"><span data-stu-id="1491c-120">**Pager**</span></span>  
 <span data-ttu-id="1491c-121">使用呼叫器電子郵件地址通知操作員。</span><span class="sxs-lookup"><span data-stu-id="1491c-121">Use the pager e-mail address to notify the operator.</span></span>  
  
 <span data-ttu-id="1491c-122">**Net send**</span><span class="sxs-lookup"><span data-stu-id="1491c-122">**Net send**</span></span>  
 <span data-ttu-id="1491c-123">使用 **net send** 通知操作員。</span><span class="sxs-lookup"><span data-stu-id="1491c-123">Use **net send** to notify the operator.</span></span>  
  
 <span data-ttu-id="1491c-124">**New 運算子**</span><span class="sxs-lookup"><span data-stu-id="1491c-124">**New operator**</span></span>  
 <span data-ttu-id="1491c-125">顯示 [新增操作員]\*\*\*\* 對話方塊，可讓您建立新的操作員。</span><span class="sxs-lookup"><span data-stu-id="1491c-125">Displays the **New Operator** dialog box, which you can use to create a new operator.</span></span>  
  
 <span data-ttu-id="1491c-126">**檢視操作員**</span><span class="sxs-lookup"><span data-stu-id="1491c-126">**View operator**</span></span>  
 <span data-ttu-id="1491c-127">顯示目前選取之操作員的 [屬性]\*\*\*\* 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="1491c-127">Displays the **Properties** dialog box for the currently selected operator.</span></span> <span data-ttu-id="1491c-128">您可以在 [操作員屬性]\*\*\*\* 對話方塊上檢視及修改操作員屬性。</span><span class="sxs-lookup"><span data-stu-id="1491c-128">You can view and modified operator properties on the **Operator Properties** dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1491c-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1491c-129">See Also</span></span>  
 <span data-ttu-id="1491c-130">[警示](alerts.md) </span><span class="sxs-lookup"><span data-stu-id="1491c-130">[Alerts](alerts.md) </span></span>  
 <span data-ttu-id="1491c-131">[使用嚴重性層級建立警示](create-an-alert-using-severity-level.md) </span><span class="sxs-lookup"><span data-stu-id="1491c-131">[Create an Alert Using Severity Level](create-an-alert-using-severity-level.md) </span></span>  
 <span data-ttu-id="1491c-132">[警示](alerts.md) </span><span class="sxs-lookup"><span data-stu-id="1491c-132">[Alerts](alerts.md) </span></span>  
 <span data-ttu-id="1491c-133">[編輯警示](edit-an-alert.md) </span><span class="sxs-lookup"><span data-stu-id="1491c-133">[Edit an Alert](edit-an-alert.md) </span></span>  
 [<span data-ttu-id="1491c-134">Delete an Alert</span><span class="sxs-lookup"><span data-stu-id="1491c-134">Delete an Alert</span></span>](delete-an-alert.md)  
  
  
