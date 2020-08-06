---
title: 訂用帳戶與傳遞方法 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- reports [Reporting Services], delivering
- delivery [Reporting Services]
- methods [Reporting Services], subscription and delivery
- subscriptions [Reporting Services], about subscriptions
ms.assetid: a8637501-1817-4ccc-b07d-dd9ed5608805
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c6ae92a6abd5c25b9ab1236a2b5b11429d210cba
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688538"
---
# <a name="subscription-and-delivery-methods"></a><span data-ttu-id="9c08f-102">訂閱與傳遞方法</span><span class="sxs-lookup"><span data-stu-id="9c08f-102">Subscription and Delivery Methods</span></span>
  <span data-ttu-id="9c08f-103">您可以使用這些方法來建立及管理目錄項目的訂閱與傳遞。</span><span class="sxs-lookup"><span data-stu-id="9c08f-103">You can use these methods to create and manage subscriptions and delivery of catalog items.</span></span>  
  
|<span data-ttu-id="9c08f-104">方法</span><span class="sxs-lookup"><span data-stu-id="9c08f-104">Method</span></span>|<span data-ttu-id="9c08f-105">動作</span><span class="sxs-lookup"><span data-stu-id="9c08f-105">Action</span></span>|  
|------------|------------|  
|<xref:ReportService2010.ReportingService2010.CreateDataDrivenSubscription%2A>|<span data-ttu-id="9c08f-106">建立指定之項目的資料驅動訂閱。</span><span class="sxs-lookup"><span data-stu-id="9c08f-106">Creates a data-driven subscription for a specified item.</span></span>|  
|<xref:ReportService2010.ReportingService2010.GetDataDrivenSubscriptionProperties%2A>|<span data-ttu-id="9c08f-107">傳回資料驅動訂閱的屬性。</span><span class="sxs-lookup"><span data-stu-id="9c08f-107">Returns the properties for a data-driven subscription.</span></span>|  
|<xref:ReportService2010.ReportingService2010.CreateSubscription%2A>|<span data-ttu-id="9c08f-108">在報表伺服器資料庫或 SharePoint 文件庫中，建立指定之項目的訂閱。</span><span class="sxs-lookup"><span data-stu-id="9c08f-108">Creates a subscription for the specified item in the report server database or SharePoint library.</span></span>|  
|<xref:ReportService2010.ReportingService2010.DeleteSubscription%2A>|<span data-ttu-id="9c08f-109">從報表伺服器資料庫刪除訂閱。</span><span class="sxs-lookup"><span data-stu-id="9c08f-109">Deletes a subscription from the report server database.</span></span>|  
|<xref:ReportService2010.ReportingService2010.GetSubscriptionProperties%2A>|<span data-ttu-id="9c08f-110">傳回訂閱的屬性。</span><span class="sxs-lookup"><span data-stu-id="9c08f-110">Returns the properties of a subscription.</span></span>|  
|<xref:ReportService2010.ReportingService2010.ListMySubscriptions%2A>|<span data-ttu-id="9c08f-111">擷取已由報表伺服器或給定目錄項目之 SharePoint 網站的目前使用者所建立的訂閱清單。</span><span class="sxs-lookup"><span data-stu-id="9c08f-111">Retrieves a list of subscriptions that have been created by the current user of the report server or SharePoint site for the given catalog item.</span></span>|  
|<xref:ReportService2010.ReportingService2010.ListSubscriptions%2A>|<span data-ttu-id="9c08f-112">擷取已為給定項目建立的訂閱清單。</span><span class="sxs-lookup"><span data-stu-id="9c08f-112">Retrieves a list of subscriptions that have been created for a given item.</span></span>|  
|<xref:ReportService2010.ReportingService2010.PrepareQuery%2A>|<span data-ttu-id="9c08f-113">傳回資料集，其中包含由資料驅動訂閱之傳遞查詢所擷取的欄位。</span><span class="sxs-lookup"><span data-stu-id="9c08f-113">Returns a data set containing the fields retrieved by the delivery query for a data-driven subscription.</span></span>|  
|<xref:ReportService2010.ReportingService2010.SetDataDrivenSubscriptionProperties%2A>|<span data-ttu-id="9c08f-114">設定資料驅動訂閱的屬性值。</span><span class="sxs-lookup"><span data-stu-id="9c08f-114">Sets the values of properties of a data-driven subscription.</span></span>|  
|<xref:ReportService2010.ReportingService2010.SetSubscriptionProperties%2A>|<span data-ttu-id="9c08f-115">設定訂閱的屬性值。</span><span class="sxs-lookup"><span data-stu-id="9c08f-115">Sets the values of properties of a subscription.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9c08f-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9c08f-116">See Also</span></span>  
 <span data-ttu-id="9c08f-117">[使用 Web 服務和 .NET Framework 建置應用程式](../net-framework/building-applications-using-the-web-service-and-the-net-framework.md) </span><span class="sxs-lookup"><span data-stu-id="9c08f-117">[Building Applications Using the Web Service and the .NET Framework](../net-framework/building-applications-using-the-web-service-and-the-net-framework.md) </span></span>  
 <span data-ttu-id="9c08f-118">[報表伺服器 Web 服務](../report-server-web-service.md) </span><span class="sxs-lookup"><span data-stu-id="9c08f-118">[Report Server Web Service](../report-server-web-service.md) </span></span>  
 <span data-ttu-id="9c08f-119">[報表伺服器 Web 服務方法](report-server-web-service-methods.md) </span><span class="sxs-lookup"><span data-stu-id="9c08f-119">[Report Server Web Service Methods](report-server-web-service-methods.md) </span></span>  
 [<span data-ttu-id="9c08f-120">技術參考 &#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="9c08f-120">Technical Reference &#40;SSRS&#41;</span></span>](../../technical-reference-ssrs.md)  
  
  
