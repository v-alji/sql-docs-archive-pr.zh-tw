---
title: 資料驅動訂閱 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- subscriptions [Reporting Services], data-driven
- data-driven subscriptions
ms.assetid: ba009f62-0d4f-45e7-a27c-36fd5f0cd3a8
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b59d5cc447191bef526d4cf4399a841d68932886
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594370"
---
# <a name="data-driven-subscriptions"></a><span data-ttu-id="d1e4a-102">資料驅動訂閱</span><span class="sxs-lookup"><span data-stu-id="d1e4a-102">Data-Driven Subscriptions</span></span>
  <span data-ttu-id="d1e4a-103">資料驅動訂閱會提供一個方式來使用在執行階段擷取自外部資料來源的動態訂閱資料，</span><span class="sxs-lookup"><span data-stu-id="d1e4a-103">A data-driven subscription provides a way to use dynamic subscription data that is retrieved from an external data source at run time.</span></span> <span data-ttu-id="d1e4a-104">資料驅動訂閱也可以使用在定義訂閱時所指定的靜態文字和預設值；</span><span class="sxs-lookup"><span data-stu-id="d1e4a-104">A data-driven subscription can also use static text and default values that you specify when the subscription is defined.</span></span> <span data-ttu-id="d1e4a-105">您可以使用資料驅動訂閱來執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="d1e4a-105">You can use data-driven subscriptions to do the following:</span></span>  
  
-   <span data-ttu-id="d1e4a-106">將報表散發給變動的訂閱者清單。</span><span class="sxs-lookup"><span data-stu-id="d1e4a-106">Distribute a report to a fluctuating list of subscribers.</span></span> <span data-ttu-id="d1e4a-107">例如，您可以使用資料驅動訂閱，將報表散發至每個月的訂閱者都不同的整個大型組織內，或者使用決定現有使用者集內群組成員資格的其他準則。</span><span class="sxs-lookup"><span data-stu-id="d1e4a-107">For example, you can use data-driven subscriptions to distribute a report throughout a large organization where subscribers vary from one month to the next, or use other criteria that determines group membership from an existing set of users.</span></span>  
  
-   <span data-ttu-id="d1e4a-108">使用執行階段所擷取的報表參數值來篩選報表輸出。</span><span class="sxs-lookup"><span data-stu-id="d1e4a-108">Filter the report output using report parameter values that are retrieved at run time.</span></span>  
  
-   <span data-ttu-id="d1e4a-109">讓每一個報表傳遞的報表輸出格式和傳遞選項有所差異。</span><span class="sxs-lookup"><span data-stu-id="d1e4a-109">Vary report output formats and delivery options for each report delivery.</span></span>  
  
 <span data-ttu-id="d1e4a-110">資料驅動訂閱是由多個部分所組成；</span><span class="sxs-lookup"><span data-stu-id="d1e4a-110">A data-driven subscription is composed of multiple parts.</span></span> <span data-ttu-id="d1e4a-111">當您建立資料驅動訂閱時，會定義此訂閱的固定層面，這些層面包含以下內容：</span><span class="sxs-lookup"><span data-stu-id="d1e4a-111">The fixed aspects of a data-driven subscription are defined when you create the subscription, and these include the following:</span></span>  
  
-   <span data-ttu-id="d1e4a-112">定義此訂閱所針對的報表 (訂閱一定會與單一報表有關聯)。</span><span class="sxs-lookup"><span data-stu-id="d1e4a-112">The report for which the subscription is defined (a subscription is always associated with a single report).</span></span>  
  
-   <span data-ttu-id="d1e4a-113">用來散發此報表的傳遞延伸模組。</span><span class="sxs-lookup"><span data-stu-id="d1e4a-113">The delivery extension used to distribute the report.</span></span> <span data-ttu-id="d1e4a-114">您可以指定報表伺服器電子郵件傳遞、檔案共用傳遞、用來預先載入快取的 Null 傳遞提供者或是自訂傳遞延伸模組，</span><span class="sxs-lookup"><span data-stu-id="d1e4a-114">You can specify report server e-mail delivery, file share delivery, the null delivery provider used for preloading the cache, or a custom delivery extension.</span></span> <span data-ttu-id="d1e4a-115">但是不能指定單一訂閱內的多個傳遞延伸模組。</span><span class="sxs-lookup"><span data-stu-id="d1e4a-115">You cannot specify multiple delivery extensions within a single subscription.</span></span>  
  
-   <span data-ttu-id="d1e4a-116">訂閱者資料來源。</span><span class="sxs-lookup"><span data-stu-id="d1e4a-116">The subscriber data source.</span></span> <span data-ttu-id="d1e4a-117">當您定義訂閱時，必須指定包含訂閱者資料之資料來源的連接字串；</span><span class="sxs-lookup"><span data-stu-id="d1e4a-117">You must specify a connection string to the data source that contains subscriber data when you define the subscription.</span></span> <span data-ttu-id="d1e4a-118">訂閱者資料來源不能在執行階段動態指定。</span><span class="sxs-lookup"><span data-stu-id="d1e4a-118">The subscriber data source cannot be specified dynamically at run time.</span></span>  
  
-   <span data-ttu-id="d1e4a-119">當您定義訂閱時，必須指定選取訂閱者資料所使用的查詢。</span><span class="sxs-lookup"><span data-stu-id="d1e4a-119">The query that you use to select subscriber data must be specified when you define the subscription.</span></span> <span data-ttu-id="d1e4a-120">您不能在執行階段變更此查詢。</span><span class="sxs-lookup"><span data-stu-id="d1e4a-120">You cannot change the query at run time.</span></span>  
  
 <span data-ttu-id="d1e4a-121">在處理訂閱時，會取得資料驅動訂閱中所用的動態值。</span><span class="sxs-lookup"><span data-stu-id="d1e4a-121">Dynamic values used in a data-driven subscription are obtained when the subscription is processed.</span></span> <span data-ttu-id="d1e4a-122">您可以在訂閱中使用的變動資料範例包括訂閱者名稱、電子郵件地址、慣用的報表輸出格式，或是對報表參數有效的任何值。</span><span class="sxs-lookup"><span data-stu-id="d1e4a-122">Examples of variable data that you might use in a subscription include the subscriber name, e-mail address, preferred report output format, or any value that is valid for a report parameter.</span></span> <span data-ttu-id="d1e4a-123">若要在資料驅動訂閱中使用動態值，您會在查詢中所傳回的欄位以及特定傳遞選項和報表參數之間定義對應。</span><span class="sxs-lookup"><span data-stu-id="d1e4a-123">To use dynamic values in a data-driven subscription, you define a mapping between the fields that are returned in the query to specific delivery options and to report parameters.</span></span> <span data-ttu-id="d1e4a-124">每當處理此訂閱時，會從訂閱者資料來源中擷取變動資料。</span><span class="sxs-lookup"><span data-stu-id="d1e4a-124">Variable data is retrieved from a subscriber data source each time the subscription is processed.</span></span>  
  
## <a name="requirements-for-using-data-driven-subscriptions"></a><span data-ttu-id="d1e4a-125">使用資料驅動訂閱的需求</span><span class="sxs-lookup"><span data-stu-id="d1e4a-125">Requirements for using Data-Driven Subscriptions</span></span>  
 <span data-ttu-id="d1e4a-126">並非所有版本中都可以使用資料驅動訂閱功能，</span><span class="sxs-lookup"><span data-stu-id="d1e4a-126">Data-driven subscription functionality is not available in all editions.</span></span> <span data-ttu-id="d1e4a-127">您在執行階段可用來擷取訂閱資料的資料來源種類也有一些限制；</span><span class="sxs-lookup"><span data-stu-id="d1e4a-127">There are also limitations on the kinds of data sources that you can use to retrieve subscription data at run time.</span></span> <span data-ttu-id="d1e4a-128">下列清單提供有關這些需求的詳細資訊：</span><span class="sxs-lookup"><span data-stu-id="d1e4a-128">The following list provides more information about the requirements:</span></span>  
  
-   <span data-ttu-id="d1e4a-129">如需 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 支援資料驅動訂閱功能之版本的詳細資訊，請參閱[SQL Server 2012 (版本支援的功能](https://go.microsoft.com/fwlink/?linkid=232473) https://go.microsoft.com/fwlink/?linkid=232473) 。</span><span class="sxs-lookup"><span data-stu-id="d1e4a-129">For more information about the editions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that support Data-driven subscription functionality, see [Features Supported by the Editions of SQL Server 2012](https://go.microsoft.com/fwlink/?linkid=232473) (https://go.microsoft.com/fwlink/?linkid=232473).</span></span>  
  
-   <span data-ttu-id="d1e4a-130">如果是訂閱資料，請選擇可以提供結構描述資訊給報表伺服器的資料來源；</span><span class="sxs-lookup"><span data-stu-id="d1e4a-130">For subscription data, choose a data source that can provide schema information to the report server.</span></span> <span data-ttu-id="d1e4a-131">支援資料來源類型的範例包括 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 關聯式資料、Oracle、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 資料庫、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 套件資料、ODBC 資料來源和 OLE DB 資料來源。</span><span class="sxs-lookup"><span data-stu-id="d1e4a-131">Examples of supported data source types include [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] relational data, Oracle, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] databases, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package data, ODBC data sources, and OLE DB data sources.</span></span> <span data-ttu-id="d1e4a-132">如需訂閱者資料來源需求的詳細資訊，請參閱 [使用外部資料來源以取得訂閱者資料 &#40;資料驅動訂閱&#41;](use-an-external-data-source-for-subscriber-data-data-driven-subscription.md)。</span><span class="sxs-lookup"><span data-stu-id="d1e4a-132">For more information about subscriber data source requirements, see [Use an External Data Source for Subscriber Data &#40;Data-Driven Subscription&#41;](use-an-external-data-source-for-subscriber-data-data-driven-subscription.md).</span></span>  
  
## <a name="working-with-data-driven-subscriptions"></a><span data-ttu-id="d1e4a-133">使用資料驅動訂閱</span><span class="sxs-lookup"><span data-stu-id="d1e4a-133">Working with Data-Driven Subscriptions</span></span>  
 <span data-ttu-id="d1e4a-134">下列主題提供有關資料驅動訂閱的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="d1e4a-134">The following topics provide more information about data-driven subscriptions.</span></span>  
  
|<span data-ttu-id="d1e4a-135">主題</span><span class="sxs-lookup"><span data-stu-id="d1e4a-135">Topics</span></span>|<span data-ttu-id="d1e4a-136">描述</span><span class="sxs-lookup"><span data-stu-id="d1e4a-136">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d1e4a-137">Create, Modify, and Delete a Data-Driven Subscription</span><span class="sxs-lookup"><span data-stu-id="d1e4a-137">Create, Modify, and Delete a Data-Driven Subscription</span></span>](data-driven-subscriptions.md)|<span data-ttu-id="d1e4a-138">說明如何建立、修改或刪除資料驅動訂閱。</span><span class="sxs-lookup"><span data-stu-id="d1e4a-138">Explains how to create, modify, or delete a data-driven subscription.</span></span>|  
|[<span data-ttu-id="d1e4a-139">使用外部資料來源以取得訂閱者資料 &#40;資料驅動訂閱&#41;</span><span class="sxs-lookup"><span data-stu-id="d1e4a-139">Use an External Data Source for Subscriber Data &#40;Data-Driven Subscription&#41;</span></span>](use-an-external-data-source-for-subscriber-data-data-driven-subscription.md)|<span data-ttu-id="d1e4a-140">提供有關在資料驅動訂閱所使用之資料來源的資訊。</span><span class="sxs-lookup"><span data-stu-id="d1e4a-140">Provides information about the data sources that you can use for a data-driven subscription.</span></span>|  
|[<span data-ttu-id="d1e4a-141">建立資料驅動訂閱 &#40;SSRS 教學課程&#41;</span><span class="sxs-lookup"><span data-stu-id="d1e4a-141">Create a Data-Driven Subscription &#40;SSRS Tutorial&#41;</span></span>](../create-a-data-driven-subscription-ssrs-tutorial.md)|<span data-ttu-id="d1e4a-142">提供逐步指示，以了解如何建立資料驅動訂閱。</span><span class="sxs-lookup"><span data-stu-id="d1e4a-142">Provides step-by-step instruction for learning how to create a data-driven subscription.</span></span>|  
|[<span data-ttu-id="d1e4a-143">快取報表 &#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="d1e4a-143">Caching Reports &#40;SSRS&#41;</span></span>](../report-server/caching-reports-ssrs.md)|<span data-ttu-id="d1e4a-144">描述如何使用 Null 傳遞提供者搭配資料驅動訂閱，以預先載入快取。</span><span class="sxs-lookup"><span data-stu-id="d1e4a-144">Describes how to use the Null Delivery Provider with a data-driven subscription to preload the cache.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d1e4a-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d1e4a-145">See Also</span></span>  
 <span data-ttu-id="d1e4a-146">[訂閱與傳遞 &#40;Reporting Services&#41;](subscriptions-and-delivery-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="d1e4a-146">[Subscriptions and Delivery &#40;Reporting Services&#41;](subscriptions-and-delivery-reporting-services.md) </span></span>  
 <span data-ttu-id="d1e4a-147">[建立資料驅動訂閱頁面 &#40;報表管理員&#41;](../create-data-driven-subscription-page-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="d1e4a-147">[Create Data-driven Subscription Page &#40;Report Manager&#41;](../create-data-driven-subscription-page-report-manager.md) </span></span>  
 [<span data-ttu-id="d1e4a-148">預先載入快取 &#40;報表管理員&#41;</span><span class="sxs-lookup"><span data-stu-id="d1e4a-148">Preload the Cache &#40;Report Manager&#41;</span></span>](../report-server/preload-the-cache-report-manager.md)  
  
  
