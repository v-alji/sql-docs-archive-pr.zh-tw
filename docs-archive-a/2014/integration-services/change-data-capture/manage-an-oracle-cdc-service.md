---
title: 管理 Oracle CDC 服務 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- createSrv
ms.assetid: 5972cee3-b1a9-4c56-aed6-bdddf84af283
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f5fbe769980297a06b7958ecad04bfed85b9b714
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687102"
---
# <a name="manage-an-oracle-cdc-service"></a><span data-ttu-id="9233f-102">Manage an Oracle CDC Service</span><span class="sxs-lookup"><span data-stu-id="9233f-102">Manage an Oracle CDC Service</span></span>
  <span data-ttu-id="9233f-103">您可以使用 CDC 服務組態主控台來管理特定的 CDC 服務。</span><span class="sxs-lookup"><span data-stu-id="9233f-103">You can use the CDC Service Configuration Console to manage a specific CDC Service.</span></span>  
  
 <span data-ttu-id="9233f-104">**若要選取您想要使用的 CDC 服務**</span><span class="sxs-lookup"><span data-stu-id="9233f-104">**To select the CDC service you want to work with**</span></span>  
  
1.  <span data-ttu-id="9233f-105">從 CDC 服務組態主控台的左窗格中，展開 **[本機 CDC 服務]** 。</span><span class="sxs-lookup"><span data-stu-id="9233f-105">From the left pane in the CDC Service Configuration Console, expand **Local CDC Services**.</span></span>  
  
2.  <span data-ttu-id="9233f-106">選取您想要使用的 CDC 服務。</span><span class="sxs-lookup"><span data-stu-id="9233f-106">Select the CDC service you want to work with.</span></span>  
  
     <span data-ttu-id="9233f-107">您也可以用滑鼠右鍵按一下您想要使用的 CDC 服務，並選取所要的動作。</span><span class="sxs-lookup"><span data-stu-id="9233f-107">You can also right-click the CDC service you want to work with and select the desired action.</span></span> <span data-ttu-id="9233f-108">請參閱 [您可以使用 CDC 服務做什麼事](manage-an-oracle-cdc-service.md#BKMK_WhatcandowithCDCService)。</span><span class="sxs-lookup"><span data-stu-id="9233f-108">See [What can you do with a CDC Service](manage-an-oracle-cdc-service.md#BKMK_WhatcandowithCDCService).</span></span>  
  
 <span data-ttu-id="9233f-109">**OR**</span><span class="sxs-lookup"><span data-stu-id="9233f-109">**OR**</span></span>  
  
1.  <span data-ttu-id="9233f-110">從 CDC 服務組態主控台的左窗格選取 **[本機 CDC 服務]** 。</span><span class="sxs-lookup"><span data-stu-id="9233f-110">Select **Local CDC Services** from the left pane in the CDC Service Configuration Console.</span></span>  
  
2.  <span data-ttu-id="9233f-111">從 CDC 服務組態主控台的中間區段選取您想要使用的服務。</span><span class="sxs-lookup"><span data-stu-id="9233f-111">From the middle section of the CDC Service Configuration Console, select the service you want to work with.</span></span>  
  
     <span data-ttu-id="9233f-112">您也可以用滑鼠右鍵按一下您想要使用的 CDC 服務，並選取所要的動作。</span><span class="sxs-lookup"><span data-stu-id="9233f-112">You can also right-click the CDC service you want to work with and select the desired action.</span></span> <span data-ttu-id="9233f-113">請參閱 [您可以使用 CDC 服務做什麼事](manage-an-oracle-cdc-service.md#BKMK_WhatcandowithCDCService)。</span><span class="sxs-lookup"><span data-stu-id="9233f-113">See [What can you do with a CDC Service](manage-an-oracle-cdc-service.md#BKMK_WhatcandowithCDCService).</span></span>  
  
##  <a name="what-can-you-do-with-a-cdc-service"></a><a name="BKMK_WhatcandowithCDCService"></a> <span data-ttu-id="9233f-114">您可以使用 CDC 服務做什麼事</span><span class="sxs-lookup"><span data-stu-id="9233f-114">What can you do with a CDC Service</span></span>  
 <span data-ttu-id="9233f-115">當您使用 CDC 服務時，可以執行以下動作。</span><span class="sxs-lookup"><span data-stu-id="9233f-115">You can carry out the following actions when working with a CDC service.</span></span>  
  
### <a name="delete-the-service"></a><span data-ttu-id="9233f-116">刪除服務</span><span class="sxs-lookup"><span data-stu-id="9233f-116">Delete the service</span></span>  
 <span data-ttu-id="9233f-117">從 CDC 服務組態主控台右側的 **[動作]** 窗格中，按一下 **[刪除]** 刪除此服務。</span><span class="sxs-lookup"><span data-stu-id="9233f-117">From the **Actions** pane on the right side of the CDC Service Configuration Console, click **Delete** to delete the service.</span></span>  
  
 <span data-ttu-id="9233f-118">您也可以用滑鼠右鍵按一下您想要刪除的 CDC 服務，然後選取 [刪除]  。</span><span class="sxs-lookup"><span data-stu-id="9233f-118">You can also right-click the CDC service you want to delete and select **Delete**.</span></span>  
  
 <span data-ttu-id="9233f-119">**注意**：如果當您刪除此服務時，它正在執行中，在刪除此服務之前會先將它停止。</span><span class="sxs-lookup"><span data-stu-id="9233f-119">**Note**: If the service is running when deleting the service, the service is stopped before being deleted.</span></span>  
  
 <span data-ttu-id="9233f-120">若要刪除 Oracle CDC Windows 服務定義，此程式需要關聯 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體中 MSXDBCDC 資料庫的更新存取權。</span><span class="sxs-lookup"><span data-stu-id="9233f-120">To delete the Oracle CDC Windows Service definition, the program needs update access to the MSXDBCDC database in the associated [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span> <span data-ttu-id="9233f-121">當您按一下 [確定] 刪除此服務時，此程式會嘗試刪除 MSXDBCDC 資料庫中的 Oracle CDC 服務登錄。</span><span class="sxs-lookup"><span data-stu-id="9233f-121">When you click OK to delete the service, the program attempts to delete the Oracle CDC Service registration in the MSXDBCDC database.</span></span> <span data-ttu-id="9233f-122">如果此程式因為沒有適當的權限所以無法刪除 Oracle CDC 服務登錄，它會提示使用者輸入具有 MSXDBCDC 資料庫之更新權限的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登入。</span><span class="sxs-lookup"><span data-stu-id="9233f-122">If the program cannot delete the Oracle CDC Service registration because it does not have the proper permissions, it prompts the user to enter a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login with update permissions to the MSXDBCDC database.</span></span>  
  
 <span data-ttu-id="9233f-123">如需有關您必須在 [連接到 SQL Server] 對話方塊中輸入之資料的詳細資訊，請參閱＜ [Connection to SQL Server for Delete](connection-to-sql-server-for-delete.md)＞。</span><span class="sxs-lookup"><span data-stu-id="9233f-123">For information about the data you must enter in the Connect to SQL Server dialog box, see [Connection to SQL Server for Delete](connection-to-sql-server-for-delete.md).</span></span>  
  
### <a name="edit-the-cdc-service-properties"></a><span data-ttu-id="9233f-124">編輯 CDC 服務屬性</span><span class="sxs-lookup"><span data-stu-id="9233f-124">Edit the CDC Service Properties</span></span>  
 <span data-ttu-id="9233f-125">從 CDC 服務組態主控台右側的 **[動作]** 窗格中，按一下 **[屬性]** 。</span><span class="sxs-lookup"><span data-stu-id="9233f-125">From the **Actions** pane on the right side of the CDC Service Configuration Console, click **Properties**.</span></span>  
  
 <span data-ttu-id="9233f-126">您也可以用滑鼠右鍵按一下您要編輯屬性的 CDC 服務，然後選取 [屬性]  。</span><span class="sxs-lookup"><span data-stu-id="9233f-126">You can also right-click the CDC service where you want to edit the properties and select **Properties**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9233f-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9233f-127">See Also</span></span>  
 [<span data-ttu-id="9233f-128">如何管理本機 CDC 服務</span><span class="sxs-lookup"><span data-stu-id="9233f-128">How to Manage a Local CDC Service</span></span>](how-to-manage-a-local-cdc-service.md)  
