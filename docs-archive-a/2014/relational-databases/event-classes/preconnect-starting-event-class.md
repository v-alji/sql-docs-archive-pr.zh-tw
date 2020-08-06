---
title: PreConnect:Starting 事件類別 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- PreConnect:Starting Event Class
ms.assetid: d43ed0ad-3dbd-42e0-9cef-8320b8d87497
author: stevestein
ms.author: sstein
ms.openlocfilehash: 67b642d369c73cc144af31f835786613766045f9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597811"
---
# <a name="preconnectstarting-event-class"></a><span data-ttu-id="16067-102">PreConnect:Starting 事件類別</span><span class="sxs-lookup"><span data-stu-id="16067-102">PreConnect:Starting Event Class</span></span>
  <span data-ttu-id="16067-103">PreConnect:Starting 事件類別會指出 LOGON 觸發程序或資源管理員分類函數開始執行。</span><span class="sxs-lookup"><span data-stu-id="16067-103">The PreConnect:Starting event class indicates when a LOGON trigger or the Resource Governor classifier function starts execution.</span></span>  
  
## <a name="preconnectstarting-event-class-data-columns"></a><span data-ttu-id="16067-104">PreConnect:Starting 事件類別資料行</span><span class="sxs-lookup"><span data-stu-id="16067-104">PreConnect:Starting Event Class Data Columns</span></span>  
  
|<span data-ttu-id="16067-105">資料行名稱</span><span class="sxs-lookup"><span data-stu-id="16067-105">Data column name</span></span>|<span data-ttu-id="16067-106">資料類型</span><span class="sxs-lookup"><span data-stu-id="16067-106">Data type</span></span>|<span data-ttu-id="16067-107">描述</span><span class="sxs-lookup"><span data-stu-id="16067-107">Description</span></span>|<span data-ttu-id="16067-108">資料行識別碼</span><span class="sxs-lookup"><span data-stu-id="16067-108">Column ID</span></span>|<span data-ttu-id="16067-109">可篩選</span><span class="sxs-lookup"><span data-stu-id="16067-109">Filterable</span></span>|  
|----------------------|---------------|-----------------|---------------|----------------|  
|<span data-ttu-id="16067-110">EventClass</span><span class="sxs-lookup"><span data-stu-id="16067-110">EventClass</span></span>|`int`|<span data-ttu-id="16067-111">215</span><span class="sxs-lookup"><span data-stu-id="16067-111">215</span></span>|<span data-ttu-id="16067-112">27</span><span class="sxs-lookup"><span data-stu-id="16067-112">27</span></span>|<span data-ttu-id="16067-113">否</span><span class="sxs-lookup"><span data-stu-id="16067-113">No</span></span>|  
|<span data-ttu-id="16067-114">SPID</span><span class="sxs-lookup"><span data-stu-id="16067-114">SPID</span></span>|`int`|<span data-ttu-id="16067-115">引發此事件之伺服器處理序的識別碼。</span><span class="sxs-lookup"><span data-stu-id="16067-115">The ID of server process that fires this event.</span></span>|<span data-ttu-id="16067-116">12</span><span class="sxs-lookup"><span data-stu-id="16067-116">12</span></span>|<span data-ttu-id="16067-117">是</span><span class="sxs-lookup"><span data-stu-id="16067-117">Yes</span></span>|  
|<span data-ttu-id="16067-118">EventSubClass</span><span class="sxs-lookup"><span data-stu-id="16067-118">EventSubClass</span></span>|`int`|<span data-ttu-id="16067-119">1 代表使用者定義的分類函數。</span><span class="sxs-lookup"><span data-stu-id="16067-119">1 for the user-defined classifier function.</span></span>|<span data-ttu-id="16067-120">21</span><span class="sxs-lookup"><span data-stu-id="16067-120">21</span></span>|<span data-ttu-id="16067-121">是</span><span class="sxs-lookup"><span data-stu-id="16067-121">Yes</span></span>|  
|<span data-ttu-id="16067-122">StartTime</span><span class="sxs-lookup"><span data-stu-id="16067-122">StartTime</span></span>|`datetime`|<span data-ttu-id="16067-123">使用者定義分類函數啟動的時間。</span><span class="sxs-lookup"><span data-stu-id="16067-123">The time when the user-defined classifier function starts.</span></span>|<span data-ttu-id="16067-124">14</span><span class="sxs-lookup"><span data-stu-id="16067-124">14</span></span>|<span data-ttu-id="16067-125">是</span><span class="sxs-lookup"><span data-stu-id="16067-125">Yes</span></span>|  
|<span data-ttu-id="16067-126">ObjectID</span><span class="sxs-lookup"><span data-stu-id="16067-126">ObjectID</span></span>|`int`|<span data-ttu-id="16067-127">使用者定義之分類物件的識別碼。</span><span class="sxs-lookup"><span data-stu-id="16067-127">The ID of the user-defined classifier object.</span></span>|<span data-ttu-id="16067-128">22</span><span class="sxs-lookup"><span data-stu-id="16067-128">22</span></span>|<span data-ttu-id="16067-129">是</span><span class="sxs-lookup"><span data-stu-id="16067-129">Yes</span></span>|  
|<span data-ttu-id="16067-130">ObjectName</span><span class="sxs-lookup"><span data-stu-id="16067-130">ObjectName</span></span>|`nvarchar(256)`|<span data-ttu-id="16067-131">使用者定義之分類函數的兩段式名稱。</span><span class="sxs-lookup"><span data-stu-id="16067-131">The two-part name of the classifier user-defined function.</span></span> <span data-ttu-id="16067-132">例如，dbo.classifier。</span><span class="sxs-lookup"><span data-stu-id="16067-132">For example, dbo.classifier.</span></span>|<span data-ttu-id="16067-133">34</span><span class="sxs-lookup"><span data-stu-id="16067-133">34</span></span>|<span data-ttu-id="16067-134">是</span><span class="sxs-lookup"><span data-stu-id="16067-134">Yes</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="16067-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="16067-135">See Also</span></span>  
 <span data-ttu-id="16067-136">[擴充事件](../extended-events/extended-events.md) </span><span class="sxs-lookup"><span data-stu-id="16067-136">[Extended Events](../extended-events/extended-events.md) </span></span>  
 <span data-ttu-id="16067-137">[PreConnect： Completed 事件類別](preconnect-completed-event-class.md) </span><span class="sxs-lookup"><span data-stu-id="16067-137">[PreConnect:Completed Event Class](preconnect-completed-event-class.md) </span></span>  
 [<span data-ttu-id="16067-138">資源管理員</span><span class="sxs-lookup"><span data-stu-id="16067-138">Resource Governor</span></span>](../resource-governor/resource-governor.md)  
  
  
