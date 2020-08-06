---
title: 管理 CDC 服務 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- manSer
ms.assetid: 645ae53f-f352-4d6a-9eb0-264e53a93a18
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7d630392216e51efd9ea64116d57b388202061ad
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687104"
---
# <a name="manage-a-cdc-service"></a><span data-ttu-id="7d707-102">管理 CDC 服務</span><span class="sxs-lookup"><span data-stu-id="7d707-102">Manage a CDC Service</span></span>
  <span data-ttu-id="7d707-103">您可以使用 CDC 設計工具主控台來檢視以 CDC 服務組態主控台建立的服務，並在 Oracle CDC 服務中管理所有執行個體。</span><span class="sxs-lookup"><span data-stu-id="7d707-103">You can use the CDC Designer Console to view the services you created with the CDC Service Configuration Console and manage all of the instances in the Oracle CDC Service.</span></span>  
  
 <span data-ttu-id="7d707-104">在左窗格中按一下服務名稱，以顯示有關此服務的資訊並加以管理。</span><span class="sxs-lookup"><span data-stu-id="7d707-104">Click the name of the service in the left pane to display information about the service and to manage it.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7d707-105">您必須先使用 CDC 服務組態主控台在此清單中加入服務，以建立服務。</span><span class="sxs-lookup"><span data-stu-id="7d707-105">You must first create a service using the CDC Service Configuration Console to add services to this list.</span></span> <span data-ttu-id="7d707-106">如需有關如何建立服務的詳細資訊，請參閱 CDC 服務組態主控台提供的線上說明。</span><span class="sxs-lookup"><span data-stu-id="7d707-106">For information on how to create a service, see the online help provided with the CDC Service Configuration Console.</span></span>  
  
## <a name="what-you-can-do-when-you-display-the-cdc-service-information"></a><span data-ttu-id="7d707-107">您在顯示 CDC 服務資訊時可以做什麼事</span><span class="sxs-lookup"><span data-stu-id="7d707-107">What you can do when you display the CDC service information</span></span>  
 <span data-ttu-id="7d707-108">當您顯示有關服務的資訊時，可以執行以下作業：</span><span class="sxs-lookup"><span data-stu-id="7d707-108">You can do the following when you display information about a service:</span></span>  
  
 <span data-ttu-id="7d707-109">**針對選取的服務建立新的 CDC 執行個體**</span><span class="sxs-lookup"><span data-stu-id="7d707-109">**Create a new CDC instance for the selected service**</span></span>  
  
 <span data-ttu-id="7d707-110">在右窗格中按一下 **[新增 Oracle CDC 執行個體]** ，建立該服務的新執行個體。</span><span class="sxs-lookup"><span data-stu-id="7d707-110">Click **New Oracle CDC Instance** in the right pane to create a new instance for that service.</span></span> <span data-ttu-id="7d707-111">隨即開啟新增執行個體精靈來建立執行個體。</span><span class="sxs-lookup"><span data-stu-id="7d707-111">The New Instance wizard opens to create the instance.</span></span> <span data-ttu-id="7d707-112">如需有關新增執行個體精靈的詳細資訊，請參閱＜ [Use the New Instance Wizard](use-the-new-instance-wizard.md)＞。</span><span class="sxs-lookup"><span data-stu-id="7d707-112">For more information about the New Instance wizard, see [Use the New Instance Wizard](use-the-new-instance-wizard.md).</span></span>  
  
 <span data-ttu-id="7d707-113">**在服務中啟動所有 CDC 執行個體**</span><span class="sxs-lookup"><span data-stu-id="7d707-113">**Start all CDC instances in the service**</span></span>  
  
 <span data-ttu-id="7d707-114">在右窗格中按一下 **[啟動所有執行個體]** ，開始從服務中定義的所有執行個體擷取資料。</span><span class="sxs-lookup"><span data-stu-id="7d707-114">Click **Start All Instances** in the right pane to begin capturing data from all the defined instances in the service.</span></span>  
  
 <span data-ttu-id="7d707-115">**在服務中停止所有 CDC 執行個體**</span><span class="sxs-lookup"><span data-stu-id="7d707-115">**Stop all CDC instances in the service**</span></span>  
  
 <span data-ttu-id="7d707-116">按一下 **[停止所有執行個體]** ，針對服務中的所有執行個體停止異動資料擷取。</span><span class="sxs-lookup"><span data-stu-id="7d707-116">Click **Stop All Instances** to stop the change data capture for all instances in the service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d707-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7d707-117">See Also</span></span>  
 <span data-ttu-id="7d707-118">[如何建立 SQL Server 變更資料庫執行個體](how-to-create-the-sql-server-change-database-instance.md) </span><span class="sxs-lookup"><span data-stu-id="7d707-118">[How to Create the SQL Server Change Database Instance](how-to-create-the-sql-server-change-database-instance.md) </span></span>  
 <span data-ttu-id="7d707-119">[如何從 CDC 設計工具主控台管理 CDC 服務](how-to-manage-a-cdc-service-from-the-cdc-designer-console.md) </span><span class="sxs-lookup"><span data-stu-id="7d707-119">[How to Manage a CDC Service from the CDC Designer Console](how-to-manage-a-cdc-service-from-the-cdc-designer-console.md) </span></span>  
 <span data-ttu-id="7d707-120">[使用 [新增執行個體精靈]](use-the-new-instance-wizard.md)</span><span class="sxs-lookup"><span data-stu-id="7d707-120">[Use the New Instance Wizard](use-the-new-instance-wizard.md)</span></span>  
  
  
