---
title: 在管理中心將 PowerPivot 服務應用程式連接到 SharePoint Web 應用程式 |Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: a5da8e29-7ffd-44e7-bf61-344fa5bea8ce
author: minewiskan
ms.author: owend
ms.openlocfilehash: 5fc6dcde4cc2d18c3650adbab0ec71ef5c6265cb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598588"
---
# <a name="connect-a-powerpivot-service-application-to-a-sharepoint-web-application-in-central-administration"></a><span data-ttu-id="724e9-102">在管理中心將 PowerPivot 服務應用程式連接到 SharePoint Web 應用程式</span><span class="sxs-lookup"><span data-stu-id="724e9-102">Connect a PowerPivot Service Application to a SharePoint Web Application in Central Administration</span></span>
  <span data-ttu-id="724e9-103">PowerPivot 服務應用程式可由伺服陣列中任何數目的 SharePoint Web 應用程式使用。</span><span class="sxs-lookup"><span data-stu-id="724e9-103">A PowerPivot service application can be used by any number of SharePoint Web applications in the farm.</span></span> <span data-ttu-id="724e9-104">若要讓 PowerPivot 服務應用程式可用，請將它加入至服務關聯清單。</span><span class="sxs-lookup"><span data-stu-id="724e9-104">To make a PowerPivot service application available, you add it to a service association list.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="724e9-105">預設群組中必須有一個 PowerPivot 服務應用程式，才能確保 PowerPivot 管理儀表板能夠適當運作。</span><span class="sxs-lookup"><span data-stu-id="724e9-105">You must have one PowerPivot service application in the default group to ensure that PowerPivot Management Dashboard works properly.</span></span> <span data-ttu-id="724e9-106">請勿將多個 PowerPivot 服務應用程式加入到預設群組。</span><span class="sxs-lookup"><span data-stu-id="724e9-106">Do not add more than one PowerPivot service application to the default group.</span></span> <span data-ttu-id="724e9-107">加入相同服務應用程式類型的多個項目並不是支援的組態，而且可能會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="724e9-107">Adding multiple entries of the same service application type is not a supported configuration and might cause errors.</span></span> <span data-ttu-id="724e9-108">如果您要建立其他服務應用程式，請將它們加入到自訂清單。</span><span class="sxs-lookup"><span data-stu-id="724e9-108">If you are creating additional service applications, add them to custom lists.</span></span>  
  
 <span data-ttu-id="724e9-109">本主題包含下列幾節：</span><span class="sxs-lookup"><span data-stu-id="724e9-109">This topic contains the following sections:</span></span>  
  
 [<span data-ttu-id="724e9-110">將 PowerPivot 服務應用程式加入至預設群組</span><span class="sxs-lookup"><span data-stu-id="724e9-110">Add PowerPivot Services Application to the Default Group</span></span>](#default)  
  
 [<span data-ttu-id="724e9-111">將 PowerPivot 服務應用程式加入至自訂服務關聯清單</span><span class="sxs-lookup"><span data-stu-id="724e9-111">Add PowerPivot Services Application a Custom Service Association List</span></span>](#custom)  
  
##  <a name="add-powerpivot-services-application-to-the-default-group"></a><a name="default"></a><span data-ttu-id="724e9-112">將 PowerPivot 服務應用程式加入至預設群組</span><span class="sxs-lookup"><span data-stu-id="724e9-112">Add PowerPivot Services Application to the Default Group</span></span>  
 <span data-ttu-id="724e9-113">服務關聯清單是提供資源給伺服陣列中的其他 SharePoint Web 應用程式之共用服務清單。</span><span class="sxs-lookup"><span data-stu-id="724e9-113">A service association list is a list of shared services that provide resources to other SharePoint Web applications in the farm.</span></span> <span data-ttu-id="724e9-114">伺服陣列有一個預設的服務關聯群組。</span><span class="sxs-lookup"><span data-stu-id="724e9-114">There is one default group of service associations for the farm.</span></span>  
  
 <span data-ttu-id="724e9-115">若要在清單上，當您建立應用程式時或之後使用下列步驟時，會加入 PowerPivot 服務應用程式。</span><span class="sxs-lookup"><span data-stu-id="724e9-115">To be on the list, a PowerPivot service application can either be added when you create the application or afterwards by using the following steps.</span></span>  
  
1.  <span data-ttu-id="724e9-116">在 [管理中心] 的 [應用程式管理]\*\*\*\* 中，按一下 [設定服務應用程式關聯]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="724e9-116">In Central Administration, in **Application Management**, click **Configure service application associations**.</span></span>  
  
2.  <span data-ttu-id="724e9-117">在 [應用程式 Proxy 群組] 中，按一下 [預設值]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="724e9-117">In Application Proxy Group, click **default**.</span></span>  
  
3.  <span data-ttu-id="724e9-118">選取 PowerPivot 服務應用程式旁邊的核取方塊 (由類型名稱 `PowerPivot Service Application Proxy` 所指出)。</span><span class="sxs-lookup"><span data-stu-id="724e9-118">Select the checkbox next to the PowerPivot service application (indicated by type name `PowerPivot Service Application Proxy`).</span></span> <span data-ttu-id="724e9-119">如果您有一個以上的 PowerPivot 服務應用程式，請只選擇一個。</span><span class="sxs-lookup"><span data-stu-id="724e9-119">If you have more than one PowerPivot service application, choose just one.</span></span>  
  
4.  <span data-ttu-id="724e9-120">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="724e9-120">Click **OK**.</span></span>  
  
##  <a name="add-powerpivot-services-application-a-custom-service-association-list"></a><a name="custom"></a><span data-ttu-id="724e9-121">將 PowerPivot 服務應用程式加入至自訂服務關聯清單</span><span class="sxs-lookup"><span data-stu-id="724e9-121">Add PowerPivot Services Application a Custom Service Association List</span></span>  
 <span data-ttu-id="724e9-122">預設群組可由自訂清單取代。</span><span class="sxs-lookup"><span data-stu-id="724e9-122">The default group can be replaced by a custom list.</span></span> <span data-ttu-id="724e9-123">自訂清單是特別為單一 SharePoint Web 應用程式所建立。</span><span class="sxs-lookup"><span data-stu-id="724e9-123">A custom list is created specifically for a single SharePoint Web application.</span></span> <span data-ttu-id="724e9-124">它會覆寫預設的群組，並僅用伺服陣列或服務管理員指定的服務關聯來取代。</span><span class="sxs-lookup"><span data-stu-id="724e9-124">It overrides the default group and replaces it with only those service associations that a farm or service administrator specifies.</span></span> <span data-ttu-id="724e9-125">如果您建立了多個 PowerPivot 服務應用程式，必須使用自訂清單來指定要使用哪一個。</span><span class="sxs-lookup"><span data-stu-id="724e9-125">If you created multiple PowerPivot service applications, you must use a custom list to specify which one to use.</span></span> <span data-ttu-id="724e9-126">自訂清單無法由其他 Web 應用程式重複使用。</span><span class="sxs-lookup"><span data-stu-id="724e9-126">A custom list cannot be reused by other Web applications.</span></span> <span data-ttu-id="724e9-127">它只適用於建立它的 Web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="724e9-127">It applies only to the Web application for which it was created.</span></span>  
  
1.  <span data-ttu-id="724e9-128">在 [管理中心] 的 **[應用程式管理]** 中，按一下 **[管理 Web 應用程式]**。</span><span class="sxs-lookup"><span data-stu-id="724e9-128">In Central Administration, in **Application Management**, click **Manage web applications**.</span></span>  
  
2.  <span data-ttu-id="724e9-129">選取應用程式 (例如 SharePoint -80)。</span><span class="sxs-lookup"><span data-stu-id="724e9-129">Select the application (for example, SharePoint -80).</span></span>  
  
3.  <span data-ttu-id="724e9-130">在 [Web 應用程式] 的 [管理] 中，按一下 [服務連線]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="724e9-130">In Web Applications, in Manage, click **Service Connections**.</span></span>  
  
4.  <span data-ttu-id="724e9-131">在 [編輯下列連線群組]\*\*\*\* 中選取 [自訂]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="724e9-131">In **Edit the following group of connections**, select **[custom]**.</span></span>  
  
5.  <span data-ttu-id="724e9-132">選取您想要使用的每個服務應用程式連接旁邊的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="724e9-132">Select the checkbox next to each service application connection you want to use.</span></span> <span data-ttu-id="724e9-133">如果您具有多個 PowerPivot 服務應用程式 (由 [類型] 設定為 `PowerPivot Service Application Proxy` 來指出)，請務必只選擇一個。</span><span class="sxs-lookup"><span data-stu-id="724e9-133">If you have multiple PowerPivot service applications (indicated by Type set to `PowerPivot Service Application Proxy`), be sure to choose only one.</span></span>  
  
6.  <span data-ttu-id="724e9-134">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="724e9-134">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="724e9-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="724e9-135">See Also</span></span>  
 <span data-ttu-id="724e9-136">[在管理中心建立和設定 PowerPivot 服務應用程式](create-and-configure-power-pivot-service-application-in-ca.md) </span><span class="sxs-lookup"><span data-stu-id="724e9-136">[Create and Configure a PowerPivot Service Application in Central Administration](create-and-configure-power-pivot-service-application-in-ca.md) </span></span>  
 [<span data-ttu-id="724e9-137">初始設定 &#40;PowerPivot for SharePoint&#41;</span><span class="sxs-lookup"><span data-stu-id="724e9-137">Initial Configuration &#40;PowerPivot for SharePoint&#41;</span></span>](../../sql-server/install/initial-configuration-powerpivot-for-sharepoint.md)  
  
  
