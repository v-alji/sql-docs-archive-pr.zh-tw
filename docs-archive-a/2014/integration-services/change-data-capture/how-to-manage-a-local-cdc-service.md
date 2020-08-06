---
title: 如何管理本機 CDC 服務 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 7f9be649-cd93-40c1-bc48-0480106f207c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 437590d4b91f2fc80d5bb8a90251bf0dc7c8e18a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686462"
---
# <a name="how-to-manage-a-local-cdc-service"></a><span data-ttu-id="f232e-102">如何管理本機 CDC 服務</span><span class="sxs-lookup"><span data-stu-id="f232e-102">How to Manage a Local CDC Service</span></span>
  <span data-ttu-id="f232e-103">此程序描述如何使用 CDC 服務組態主控台來管理特定的 CDC 服務。</span><span class="sxs-lookup"><span data-stu-id="f232e-103">This procedure describes how to use the CDC Service Configuration Console to manage specific CDC services.</span></span>  
  
### <a name="to-manage-a-specific-cdc-service"></a><span data-ttu-id="f232e-104">若要管理特定的 CDC 服務</span><span class="sxs-lookup"><span data-stu-id="f232e-104">To manage a specific CDC Service</span></span>  
  
1.  <span data-ttu-id="f232e-105">從 **[開始]** 功能表，選取 **[Oracle CDC 服務組態]** 。</span><span class="sxs-lookup"><span data-stu-id="f232e-105">From the **Start** menu, select the **CDC Service Configuration for Oracle**.</span></span>  
  
2.  <span data-ttu-id="f232e-106">從 CDC 服務組態主控台的左窗格中，展開 **[本機 CDC 服務]** 。</span><span class="sxs-lookup"><span data-stu-id="f232e-106">From the left pane in the CDC Service Configuration Console, expand **Local CDC Services**.</span></span>  
  
3.  <span data-ttu-id="f232e-107">選取您想要使用的 CDC 服務。</span><span class="sxs-lookup"><span data-stu-id="f232e-107">Select the CDC service you want to work with.</span></span>  
  
     <span data-ttu-id="f232e-108">您也可以用滑鼠右鍵按一下您想要使用的 CDC 服務，並選取所要的動作。</span><span class="sxs-lookup"><span data-stu-id="f232e-108">You can also right-click the CDC service you want to work with and select the desired action.</span></span>  
  
     <span data-ttu-id="f232e-109">**OR**</span><span class="sxs-lookup"><span data-stu-id="f232e-109">**OR**</span></span>  
  
     <span data-ttu-id="f232e-110">從 CDC 服務組態主控台的左窗格選取 **[本機 CDC 服務]** ，然後從 CDC 服務組態主控台的中間區段選取您想要使用的服務。</span><span class="sxs-lookup"><span data-stu-id="f232e-110">Select **Local CDC Services** from the left pane in the CDC Service Configuration Console then select the service you want to work with from the middle section of the CDC Service Configuration Console.</span></span>  
  
     <span data-ttu-id="f232e-111">您也可以用滑鼠右鍵按一下您想要使用的 CDC 服務，並選取所要的動作。</span><span class="sxs-lookup"><span data-stu-id="f232e-111">You can also right-click the CDC service you want to work with and select the desired action.</span></span>  
  
4.  <span data-ttu-id="f232e-112">當您使用 CDC 服務時，可以執行以下工作。</span><span class="sxs-lookup"><span data-stu-id="f232e-112">You can carry out the following tasks when working with a CDC service.</span></span>  
  
    -   <span data-ttu-id="f232e-113">**刪除服務**</span><span class="sxs-lookup"><span data-stu-id="f232e-113">**Delete the service**</span></span>  
  
         <span data-ttu-id="f232e-114">從 CDC 服務組態主控台右側的 **[動作]** 窗格中，按一下 **[刪除]** 刪除此服務。</span><span class="sxs-lookup"><span data-stu-id="f232e-114">From the **Actions** pane on the right side of the CDC Service Configuration Console, click **Delete** to delete the service.</span></span>  
  
         <span data-ttu-id="f232e-115">您也可以用滑鼠右鍵按一下您想要刪除的 CDC 服務，然後選取 [刪除]  。</span><span class="sxs-lookup"><span data-stu-id="f232e-115">You can also right-click the CDC service you want to delete and select **Delete**.</span></span>  
  
         <span data-ttu-id="f232e-116">**注意**：如果當您刪除此服務時，它正在執行中，在刪除此服務之前會先將它停止。</span><span class="sxs-lookup"><span data-stu-id="f232e-116">**Note**: If the service is running when deleting the service, the service is stopped before being deleted.</span></span>  
  
         <span data-ttu-id="f232e-117">若要刪除 Oracle CDC Windows 服務定義，此程式需要關聯 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體中 MSXDBCDC 資料庫的更新存取權。</span><span class="sxs-lookup"><span data-stu-id="f232e-117">To delete an Oracle CDC Windows Service definition, the program needs update access to the MSXDBCDC database in the associated [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span> <span data-ttu-id="f232e-118">當您按一下 **[確定]** 刪除此服務時，此程式會嘗試刪除 MSXDBCDC 資料庫中的 Oracle CDC 服務登錄。</span><span class="sxs-lookup"><span data-stu-id="f232e-118">When you click **OK** to delete the service, the program attempts to delete the Oracle CDC Service registration in the MSXDBCDC database.</span></span> <span data-ttu-id="f232e-119">如果它因為缺少權限而失敗，畫面上會出現一個對話方塊，提示使用者輸入具有 MSXDBCDC 資料庫之更新存取權的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登入。</span><span class="sxs-lookup"><span data-stu-id="f232e-119">If it fails due to lack of permissions, a dialog box is displayed to prompt the user to enter a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login with an update access to the MSXDBCDC database.</span></span>  
  
         <span data-ttu-id="f232e-120">如需有關您必須在 [連接到 SQL Server] 對話方塊中輸入之資料的詳細資訊，請參閱＜ [Manage an Oracle CDC Service](manage-an-oracle-cdc-service.md) ＞和＜ [Connection to SQL Server for Delete](connection-to-sql-server-for-delete.md)＞。</span><span class="sxs-lookup"><span data-stu-id="f232e-120">For information about the data you must enter in the Connect to SQL Server dialog box, see [Manage an Oracle CDC Service](manage-an-oracle-cdc-service.md) and [Connection to SQL Server for Delete](connection-to-sql-server-for-delete.md).</span></span>  
  
    -   <span data-ttu-id="f232e-121">**編輯 CDC 服務屬性**</span><span class="sxs-lookup"><span data-stu-id="f232e-121">**Edit the CDC Service Properties**</span></span>  
  
         <span data-ttu-id="f232e-122">從 CDC 服務組態主控台右側的 **[動作]** 窗格中，按一下 **[屬性]** 。</span><span class="sxs-lookup"><span data-stu-id="f232e-122">From the **Actions** pane on the right side of the CDC Service Configuration Console, click **Properties**.</span></span>  
  
         <span data-ttu-id="f232e-123">您也可以用滑鼠右鍵按一下您要編輯屬性的 CDC 服務，然後選取 [屬性]  。</span><span class="sxs-lookup"><span data-stu-id="f232e-123">You can also right-click the CDC service where you want to edit the properties and select **Properties**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f232e-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f232e-124">See Also</span></span>  
 [<span data-ttu-id="f232e-125">管理 Oracle CDC 服務</span><span class="sxs-lookup"><span data-stu-id="f232e-125">Manage an Oracle CDC Service</span></span>](manage-an-oracle-cdc-service.md)  
  
  
