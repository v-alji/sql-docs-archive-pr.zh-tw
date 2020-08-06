---
title: SQL 目的地編輯器 (Advanced Page) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.sqlserverdestadapter.advanced.f1
helpviewer_keywords:
- SQL Server Destination Editor
ms.assetid: 9b46bcf8-ddaf-4d7d-90a6-80bc19517e9b
author: chugugrace
ms.author: chugu
ms.openlocfilehash: ccf25ad888c93f694678a152417affe5c0e16091
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592753"
---
# <a name="sql-destination-editor-advanced-page"></a><span data-ttu-id="65d73-102">SQL 目的地編輯器 (進階頁面)</span><span class="sxs-lookup"><span data-stu-id="65d73-102">SQL Destination Editor (Advanced Page)</span></span>
  <span data-ttu-id="65d73-103">使用 [SQL 目的地編輯器]\*\*\*\* 對話方塊的 [進階]\*\*\*\* 頁面，即可指定進階大量插入選項。</span><span class="sxs-lookup"><span data-stu-id="65d73-103">Use the **Advanced** page of the **SQL Destination Editor** dialog box to specify advanced bulk insert options.</span></span>  
  
 <span data-ttu-id="65d73-104">若要深入了解 SQL Server 目的地，請參閱＜ [SQL Server Destination](data-flow/sql-server-destination.md)＞。</span><span class="sxs-lookup"><span data-stu-id="65d73-104">To learn more about the SQL Server destination, see [SQL Server Destination](data-flow/sql-server-destination.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="65d73-105">選項</span><span class="sxs-lookup"><span data-stu-id="65d73-105">Options</span></span>  
 <span data-ttu-id="65d73-106">**保留識別**</span><span class="sxs-lookup"><span data-stu-id="65d73-106">**Keep identity**</span></span>  
 <span data-ttu-id="65d73-107">指定工作是否應該將值插入識別欄位中。</span><span class="sxs-lookup"><span data-stu-id="65d73-107">Specify whether the task should insert values into identity columns.</span></span> <span data-ttu-id="65d73-108">此屬性的預設值為 `False`。</span><span class="sxs-lookup"><span data-stu-id="65d73-108">The default value of this property is `False`.</span></span>  
  
 <span data-ttu-id="65d73-109">**保留 Null**</span><span class="sxs-lookup"><span data-stu-id="65d73-109">**Keep nulls**</span></span>  
 <span data-ttu-id="65d73-110">指定工作是否應該保留 Null 值。</span><span class="sxs-lookup"><span data-stu-id="65d73-110">Specify whether the task should keep null values.</span></span> <span data-ttu-id="65d73-111">此屬性的預設值為 `False`。</span><span class="sxs-lookup"><span data-stu-id="65d73-111">The default value of this property is `False`.</span></span>  
  
 <span data-ttu-id="65d73-112">**資料表鎖定**</span><span class="sxs-lookup"><span data-stu-id="65d73-112">**Table lock**</span></span>  
 <span data-ttu-id="65d73-113">指定載入資料時是否鎖定資料表。</span><span class="sxs-lookup"><span data-stu-id="65d73-113">Specify whether the table is locked when the data is loaded.</span></span> <span data-ttu-id="65d73-114">此屬性的預設值為 `True`。</span><span class="sxs-lookup"><span data-stu-id="65d73-114">The default value of this property is `True`.</span></span>  
  
 <span data-ttu-id="65d73-115">**檢查條件約束**</span><span class="sxs-lookup"><span data-stu-id="65d73-115">**Check constraints**</span></span>  
 <span data-ttu-id="65d73-116">指定工作是否應該檢查條件約束。</span><span class="sxs-lookup"><span data-stu-id="65d73-116">Specify whether the task should check constraints.</span></span> <span data-ttu-id="65d73-117">此屬性的預設值為 `True`。</span><span class="sxs-lookup"><span data-stu-id="65d73-117">The default value of this property is `True`.</span></span>  
  
 <span data-ttu-id="65d73-118">**引發觸發程序**</span><span class="sxs-lookup"><span data-stu-id="65d73-118">**Fire triggers**</span></span>  
 <span data-ttu-id="65d73-119">指定大量插入是否應該引發資料表上的觸發程序。</span><span class="sxs-lookup"><span data-stu-id="65d73-119">Specify whether the bulk insert should fire triggers on tables.</span></span> <span data-ttu-id="65d73-120">此屬性的預設值為 `False`。</span><span class="sxs-lookup"><span data-stu-id="65d73-120">The default value of this property is `False`.</span></span>  
  
 <span data-ttu-id="65d73-121">**第一個資料列**</span><span class="sxs-lookup"><span data-stu-id="65d73-121">**First Row**</span></span>  
 <span data-ttu-id="65d73-122">指定要插入的第一個資料列。</span><span class="sxs-lookup"><span data-stu-id="65d73-122">Specify the first row to insert.</span></span> <span data-ttu-id="65d73-123">這個屬性的預設值為 **-1**，表示未指派任何值。</span><span class="sxs-lookup"><span data-stu-id="65d73-123">The default value of this property is **-1**, indicating that no value has been assigned.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="65d73-124">清除 [SQL 目的地編輯器]\*\*\*\* 中的文字方塊，以指出您不要指派此屬性的值。</span><span class="sxs-lookup"><span data-stu-id="65d73-124">Clear the text box in the **SQL Destination Editor** to indicate that you do not want to assign a value for this property.</span></span> <span data-ttu-id="65d73-125">在 [屬性]\*\*\*\* 視窗、[進階編輯器]\*\*\*\* 和物件模型中，請使用 -1。</span><span class="sxs-lookup"><span data-stu-id="65d73-125">Use -1 in the **Properties** window, the **Advanced Editor**, and the object model.</span></span>  
  
 <span data-ttu-id="65d73-126">**最後一個資料列**</span><span class="sxs-lookup"><span data-stu-id="65d73-126">**Last Row**</span></span>  
 <span data-ttu-id="65d73-127">指定要插入的最後一個資料列。</span><span class="sxs-lookup"><span data-stu-id="65d73-127">Specify the last row to insert.</span></span> <span data-ttu-id="65d73-128">這個屬性的預設值為 **-1**，表示未指派任何值。</span><span class="sxs-lookup"><span data-stu-id="65d73-128">The default value of this property is **-1**, indicating that no value has been assigned.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="65d73-129">清除 [SQL 目的地編輯器]\*\*\*\* 中的文字方塊，以指出您不要指派此屬性的值。</span><span class="sxs-lookup"><span data-stu-id="65d73-129">Clear the text box in the **SQL Destination Editor** to indicate that you do not want to assign a value for this property.</span></span> <span data-ttu-id="65d73-130">在 [屬性]\*\*\*\* 視窗、[進階編輯器]\*\*\*\* 和物件模型中，請使用 -1。</span><span class="sxs-lookup"><span data-stu-id="65d73-130">Use -1 in the **Properties** window, the **Advanced Editor**, and the object model.</span></span>  
  
 <span data-ttu-id="65d73-131">**錯誤數目上限**</span><span class="sxs-lookup"><span data-stu-id="65d73-131">**Maximum number of errors**</span></span>  
 <span data-ttu-id="65d73-132">指定停止大量插入之前可以發生的錯誤數目。</span><span class="sxs-lookup"><span data-stu-id="65d73-132">Specify the number of errors that can occur before the bulk insert stops.</span></span> <span data-ttu-id="65d73-133">這個屬性的預設值為 **-1**，表示未指派任何值。</span><span class="sxs-lookup"><span data-stu-id="65d73-133">The default value of this property is **-1**, indicating that no value has been assigned.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="65d73-134">清除 [SQL 目的地編輯器]\*\*\*\* 中的文字方塊，以指出您不要指派此屬性的值。</span><span class="sxs-lookup"><span data-stu-id="65d73-134">Clear the text box in the **SQL Destination Editor** to indicate that you do not want to assign a value for this property.</span></span> <span data-ttu-id="65d73-135">在 [屬性]\*\*\*\* 視窗、[進階編輯器]\*\*\*\* 和物件模型中，請使用 -1。</span><span class="sxs-lookup"><span data-stu-id="65d73-135">Use -1 in the **Properties** window, the **Advanced Editor**, and the object model.</span></span>  
  
 <span data-ttu-id="65d73-136">**逾時**</span><span class="sxs-lookup"><span data-stu-id="65d73-136">**Timeout**</span></span>  
 <span data-ttu-id="65d73-137">指定因逾時而停止大量插入之前要等候的秒數。</span><span class="sxs-lookup"><span data-stu-id="65d73-137">Specify the number of seconds to wait before the bulk insert stops because of a time-out.</span></span>  
  
 <span data-ttu-id="65d73-138">**排序資料行**</span><span class="sxs-lookup"><span data-stu-id="65d73-138">**Order columns**</span></span>  
 <span data-ttu-id="65d73-139">輸入排序資料行的名稱。</span><span class="sxs-lookup"><span data-stu-id="65d73-139">Type the names of the sort columns.</span></span> <span data-ttu-id="65d73-140">每個資料行都可依遞增或遞減順序來排序。</span><span class="sxs-lookup"><span data-stu-id="65d73-140">Each column can be sorted in ascending or descending order.</span></span> <span data-ttu-id="65d73-141">如果您使用多個排序資料行，請用逗號分隔此清單。</span><span class="sxs-lookup"><span data-stu-id="65d73-141">If you use multiple sort columns, delimit the list with commas.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65d73-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="65d73-142">See Also</span></span>  
 <span data-ttu-id="65d73-143">[Integration Services 錯誤和訊息參考](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="65d73-143">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="65d73-144">[SQL 目的地編輯器 &#40;連線管理員頁面&#41;](../../2014/integration-services/sql-destination-editor-connection-manager-page.md) </span><span class="sxs-lookup"><span data-stu-id="65d73-144">[SQL Destination Editor &#40;Connection Manager Page&#41;](../../2014/integration-services/sql-destination-editor-connection-manager-page.md) </span></span>  
 <span data-ttu-id="65d73-145">[[SQL 目的地編輯器 &#40;對應] 頁面&#41;](../../2014/integration-services/sql-destination-editor-mappings-page.md) </span><span class="sxs-lookup"><span data-stu-id="65d73-145">[SQL Destination Editor &#40;Mappings Page&#41;](../../2014/integration-services/sql-destination-editor-mappings-page.md) </span></span>  
 [<span data-ttu-id="65d73-146">使用 SQL Server 目的地來大量載入資料</span><span class="sxs-lookup"><span data-stu-id="65d73-146">Bulk Load Data by Using the SQL Server Destination</span></span>](data-flow/bulk-load-data-by-using-the-sql-server-destination.md)  
  
  
