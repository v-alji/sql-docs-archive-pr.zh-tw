---
title: 如何管理 CDC 執行個體 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 5d9e677f-b872-497d-9cde-472184a214ab
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e387b9e1a75b7279a68d1c9c9b637f5473071013
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687109"
---
# <a name="how-to-manage-a-cdc-instance"></a><span data-ttu-id="d4f3a-102">How to Manage a CDC Instance</span><span class="sxs-lookup"><span data-stu-id="d4f3a-102">How to Manage a CDC Instance</span></span>
  <span data-ttu-id="d4f3a-103">此程序描述如何使用 CDC 設計工具主控台，於執行階段管理 CDC 執行個體操作。</span><span class="sxs-lookup"><span data-stu-id="d4f3a-103">This procedure describes how to use the CDC Designer Console to manage CDC instance operations at runtime.</span></span>  
  
### <a name="to-manage-cdc-instance-operations"></a><span data-ttu-id="d4f3a-104">若要管理 CDC 執行個體操作</span><span class="sxs-lookup"><span data-stu-id="d4f3a-104">To manage CDC instance operations</span></span>  
  
1.  <span data-ttu-id="d4f3a-105">從 **[開始]** 功能表選取 **[CDC 設計工具主控台]** 。</span><span class="sxs-lookup"><span data-stu-id="d4f3a-105">From the **Start** menu, select the **CDC Designer Console**.</span></span>  
  
2.  <span data-ttu-id="d4f3a-106">在左窗格中展開 **[異動資料擷取]** ，然後展開包含您要檢視之執行個體的服務。</span><span class="sxs-lookup"><span data-stu-id="d4f3a-106">In the left pane, expand **Change Data Capture** then expand the service that contains the instance you want to view.</span></span>  
  
3.  <span data-ttu-id="d4f3a-107">選取您要使用的執行個體名稱。</span><span class="sxs-lookup"><span data-stu-id="d4f3a-107">Select the name of an instance you want to work with.</span></span>  
  
4.  <span data-ttu-id="d4f3a-108">從 CDC 設計工具主控台右側的 **[動作]** 窗格中，按一下您想要執行的操作。</span><span class="sxs-lookup"><span data-stu-id="d4f3a-108">From the **Actions** pane on the right side of the CDC Designer Console, click on the operation you want to carry out.</span></span>  
  
     <span data-ttu-id="d4f3a-109">您也可以在左窗格中，以滑鼠右鍵按一下執行個體的名稱，並選取您想要執行的操作。</span><span class="sxs-lookup"><span data-stu-id="d4f3a-109">You can also right-click the name of the instance in the left pane and select the operation you want to carry out.</span></span>  
  
     <span data-ttu-id="d4f3a-110">您可以執行以下工作：</span><span class="sxs-lookup"><span data-stu-id="d4f3a-110">You can carry out the following tasks:</span></span>  
  
    -   <span data-ttu-id="d4f3a-111">**啟動**：開始擷取變更。</span><span class="sxs-lookup"><span data-stu-id="d4f3a-111">**Start**: To start capturing changes.</span></span>  
  
    -   <span data-ttu-id="d4f3a-112">**停止**：停止擷取變更</span><span class="sxs-lookup"><span data-stu-id="d4f3a-112">**Stop**: To stop capturing changes</span></span>  
  
    -   <span data-ttu-id="d4f3a-113">**重設**：按一下 [重設]  ，將 CDC 執行個體重設為初始 (空白) 狀態。</span><span class="sxs-lookup"><span data-stu-id="d4f3a-113">**Reset**: Click **Reset** to reset the CDC instance to its initial (empty) state.</span></span> <span data-ttu-id="d4f3a-114">當 CDC 執行個體停止時可以使用這個選項。</span><span class="sxs-lookup"><span data-stu-id="d4f3a-114">This option is available when the CDC instance is stopped.</span></span> <span data-ttu-id="d4f3a-115">變更資料表及 CDC 執行個體內部狀態的所有變更都會遭到刪除。</span><span class="sxs-lookup"><span data-stu-id="d4f3a-115">All changes in the change tables and the CDC instance internal state are deleted.</span></span> <span data-ttu-id="d4f3a-116">之後啟動 CDC 執行個體時，異動擷取將會從該時間點開始，而且只包含 CDC 執行個體啟動之後所開始的交易。</span><span class="sxs-lookup"><span data-stu-id="d4f3a-116">When the CDC instance is started later on, change capture will start from that point in time and only includes transactions that started after the CDC instance started.</span></span>  
  
    -   <span data-ttu-id="d4f3a-117">**刪除**：刪除 CDC 執行個體。</span><span class="sxs-lookup"><span data-stu-id="d4f3a-117">**Delete**: To delete the CDC instance.</span></span>  
  
    -   <span data-ttu-id="d4f3a-118">**Oracle 記錄指令碼**：按一下 [Oracle 記錄指令碼]  可顯示 [Oracle 記錄指令碼] 對話方塊，其中包含 Oracle 補充記錄指令碼。</span><span class="sxs-lookup"><span data-stu-id="d4f3a-118">**Oracle Logging Script**: Click **Oracle Logging Script** to display the Oracle Logging script dialog box with the Oracle supplemental-logging script.</span></span> <span data-ttu-id="d4f3a-119">如需有關您可以在此對話方塊中執行之操作的詳細資訊，請參閱＜ [Oracle Supplemental Logging Script](oracle-supplemental-logging-script.md)＞。</span><span class="sxs-lookup"><span data-stu-id="d4f3a-119">For information on what you can do in this dialog box, see [Oracle Supplemental Logging Script](oracle-supplemental-logging-script.md).</span></span>  
  
         <span data-ttu-id="d4f3a-120">**注意**：當您執行補充記錄指令碼時，將會開啟 [執行指令碼的 Oracle 認證] 對話方塊，您可以在此提供有效的 Oracle 使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="d4f3a-120">**Note**: When you run the supplemental logging scripts, the Oracle Credentials for Running Script dialog box opens where you provide a valid Oracle user name and password.</span></span> <span data-ttu-id="d4f3a-121">如需有關如何提供適當之 Oracle 認證的詳細資訊，請參閱＜ [Oracle Credentials for Running Script](oracle-credentials-for-running-script.md)＞。</span><span class="sxs-lookup"><span data-stu-id="d4f3a-121">For information on how to provide the proper Oracle credentials, see [Oracle Credentials for Running Script](oracle-credentials-for-running-script.md).</span></span>  
  
    -   <span data-ttu-id="d4f3a-122">**CDC 執行個體部署**：產生 CDC 執行個體的部署指令碼。</span><span class="sxs-lookup"><span data-stu-id="d4f3a-122">**CDC Instance Deployment**: To generate a deployment script for the CDC Instance.</span></span> <span data-ttu-id="d4f3a-123">如需有關此對話方塊的詳細資訊，請參閱＜ [CDC Instance Deployment Script](cdc-instance-deployment-script.md)＞。</span><span class="sxs-lookup"><span data-stu-id="d4f3a-123">For information about this dialog box, see [CDC Instance Deployment Script](cdc-instance-deployment-script.md).</span></span>  
  
     <span data-ttu-id="d4f3a-124">如需有關這些工作的詳細資訊，請參閱＜ [Manage a CDC Instance](manage-a-cdc-instance.md)＞。</span><span class="sxs-lookup"><span data-stu-id="d4f3a-124">For more information about these tasks, see [Manage a CDC Instance](manage-a-cdc-instance.md).</span></span>  
  
 <span data-ttu-id="d4f3a-125">您也可以選取 **[屬性]** 來編輯 CDC 執行個體組態屬性。</span><span class="sxs-lookup"><span data-stu-id="d4f3a-125">You can also select **Properties** to edit the CDC instance configuration properties.</span></span> <span data-ttu-id="d4f3a-126">如需有關編輯 CDC 執行個體屬性的詳細資訊，請參閱＜ [Edit Instance Properties](edit-instance-properties.md)＞。</span><span class="sxs-lookup"><span data-stu-id="d4f3a-126">For more information about editing the CDC instance properties, see [Edit Instance Properties](edit-instance-properties.md).</span></span>  
  
  
