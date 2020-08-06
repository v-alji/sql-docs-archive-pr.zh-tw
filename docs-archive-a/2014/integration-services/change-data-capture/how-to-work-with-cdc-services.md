---
title: 如何使用 CDC 服務 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: db5c718a-6e7f-48ec-82a3-9d5b131716e5
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7cfb5a0ed0e9ded8e0be118deb3c819626448896
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594639"
---
# <a name="how-to-work-with-cdc-services"></a><span data-ttu-id="071a8-102">如何使用 CDC 服務</span><span class="sxs-lookup"><span data-stu-id="071a8-102">How to Work with CDC Services</span></span>
  <span data-ttu-id="071a8-103">這個程序描述如何使用 CDC 服務組態主控台來準備 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體，以便使用 Oracle CDC 服務及建立新的 CDC 服務。</span><span class="sxs-lookup"><span data-stu-id="071a8-103">This procedure describes how to use the CDC Service Configuration Console to prepare a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance to work with Oracle CDC Services and to create a new CDC service.</span></span>  
  
### <a name="to-work-with-cdc-services"></a><span data-ttu-id="071a8-104">若要使用 CDC 服務</span><span class="sxs-lookup"><span data-stu-id="071a8-104">To work with CDC services</span></span>  
  
1.  <span data-ttu-id="071a8-105">從 **[開始]** 功能表，選取 **[Oracle CDC 服務組態]** 。</span><span class="sxs-lookup"><span data-stu-id="071a8-105">From the **Start** menu, select the **CDC Service Configuration for Oracle**.</span></span>  
  
2.  <span data-ttu-id="071a8-106">從左窗格選取 [本機 CDC 服務]  \ (根層級)。</span><span class="sxs-lookup"><span data-stu-id="071a8-106">From the left pane, select **Local CDC Services** (the root level).</span></span>  
  
3.  <span data-ttu-id="071a8-107">您會執行下列其中一項或兩項工作：</span><span class="sxs-lookup"><span data-stu-id="071a8-107">You carry out the one or both of the following tasks:</span></span>  
  
    -   <span data-ttu-id="071a8-108">**準備 SQL Server**</span><span class="sxs-lookup"><span data-stu-id="071a8-108">**Prepare SQL Server**</span></span>  
  
         <span data-ttu-id="071a8-109">從 CDC 服務組態主控台右側的 **[動作]** 窗格中選取這個選項。</span><span class="sxs-lookup"><span data-stu-id="071a8-109">Select this option from the **Actions** pane on the right side of the CDC Service Configuration Console.</span></span>  
  
         <span data-ttu-id="071a8-110">您也可以用滑鼠右鍵按一下 [本機 CDC 服務]  ，並選取 [準備 SQL Server]  。</span><span class="sxs-lookup"><span data-stu-id="071a8-110">You can also right-click **Local CDC Services** and select **Prepare SQL Server**.</span></span>  
  
         <span data-ttu-id="071a8-111">隨即開啟 [為 Oracle CDC 準備 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="071a8-111">The Preparing [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Instance for Oracle CDC dialog box opens.</span></span>  
  
         <span data-ttu-id="071a8-112">若要為 Oracle CDC 服務準備 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體，登入必須擁有具備 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 固定伺服器角色的 `dbcreator` 登入。</span><span class="sxs-lookup"><span data-stu-id="071a8-112">To prepare the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance for Oracle CDC services, the login must have a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login with the `dbcreator` fixed server role.</span></span> <span data-ttu-id="071a8-113">此登入是用來建立加入 Oracle CDC 服務以及之後加入 Oracle CDC 執行個體所需的 MSXDBCDC 資料庫。</span><span class="sxs-lookup"><span data-stu-id="071a8-113">This login is used to create the MSXDBCDC database that is required for adding Oracle CDC Services and, later on, Oracle CDC Instances.</span></span>  
  
         <span data-ttu-id="071a8-114">如需有關如何使用此對話方塊的詳細資訊，請參閱＜ [Prepare SQL Server for CDC](prepare-sql-server-for-cdc.md)＞。</span><span class="sxs-lookup"><span data-stu-id="071a8-114">For information on how to use this dialog box, see [Prepare SQL Server for CDC](prepare-sql-server-for-cdc.md).</span></span> <span data-ttu-id="071a8-115">如需如何針對 CDC 啟用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體的資訊，請參閱 [如何為 CDC 準備 SQL Server](how-to-prepare-sql-server-for-cdc.md)。</span><span class="sxs-lookup"><span data-stu-id="071a8-115">For information on how to enable a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance for CDC, see [How to Prepare SQL Server for CDC](how-to-prepare-sql-server-for-cdc.md).</span></span>  
  
    -   <span data-ttu-id="071a8-116">**建立新的 CDC 服務**</span><span class="sxs-lookup"><span data-stu-id="071a8-116">**Create a new CDC service**</span></span>  
  
         <span data-ttu-id="071a8-117">從 CDC 服務組態主控台右側的 **[動作]** 窗格中按一下 **[新增服務]** 。</span><span class="sxs-lookup"><span data-stu-id="071a8-117">Click **New Service** from the **Actions** pane on the right side of the CDC Service Configuration Console.</span></span>  
  
         <span data-ttu-id="071a8-118">您也可以用滑鼠右鍵按一下 [本機 CDC 服務]  ，並選取 [新增服務]  。</span><span class="sxs-lookup"><span data-stu-id="071a8-118">You can also right-Click **Local CDC Services** and select **New Service**.</span></span>  
  
         <span data-ttu-id="071a8-119">隨即開啟 [新增 Oracle CDC 服務] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="071a8-119">The New Oracle CDC Service dialog box opens.</span></span>  
  
         <span data-ttu-id="071a8-120">如需有關如何使用此對話方塊的詳細資訊，請參閱＜ [建立及編輯 Oracle CDC 服務](create-and-edit-an-oracle-cdc-service.md)＞。</span><span class="sxs-lookup"><span data-stu-id="071a8-120">For information on how to use this dialog box, see [Create and Edit an Oracle CDC Service](create-and-edit-an-oracle-cdc-service.md).</span></span> <span data-ttu-id="071a8-121">如需有關如何建立或編輯 CDC 服務的詳細資訊，請參閱＜ [如何建立及編輯 CDC 服務](how-to-create-and-edit-a-cdc-service.md)＞。</span><span class="sxs-lookup"><span data-stu-id="071a8-121">For information on how to create or edit a CDC service, see [How to Create and Edit a CDC Service](how-to-create-and-edit-a-cdc-service.md).</span></span>  
  
         <span data-ttu-id="071a8-122">Oracle CDC 服務所使用的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登入只要求它必須是 `public` 固定伺服器角色的成員，不需要其他權限。</span><span class="sxs-lookup"><span data-stu-id="071a8-122">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login used by the Oracle CDC Service only needs to be a member of the `public` fixed-server role, no other privileges are needed.</span></span> <span data-ttu-id="071a8-123">但是，若要建立 Oracle CDC 服務，此登入必須擁有 MSXDBCDC 資料庫的寫入權限，例如 **db_owner** 資料庫角色必須指派給此登入。</span><span class="sxs-lookup"><span data-stu-id="071a8-123">However, to create the Oracle CDC Service, the login must have write permission to the MSXDBCDC database, for example the **db_owner** database role must be assigned to the login.</span></span> <span data-ttu-id="071a8-124">當沒有 MSXDBDCDC 資料庫寫入權限的登入嘗試建立新的 Oracle CDC 執行個體時，便會顯示錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="071a8-124">When a login without write permission to the MSXDBDCDC database attempts to create a new Oracle CDC instance an error message is displayed.</span></span> <span data-ttu-id="071a8-125">在這個對話方塊中按一下 **[確定]** ，隨即顯示 [連接到 SQL Server] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="071a8-125">Click **OK** in that dialog box to display the Connect to SQL Server dialog box.</span></span>  
  
         <span data-ttu-id="071a8-126">如需如何輸入擁有 MSXDBCDC 資料庫寫入權限之登入認證的資訊，例如 **db_owner** 資料庫角色，請參閱 [建立及編輯 Oracle CDC 服務](create-and-edit-an-oracle-cdc-service.md) 和 [連接到 SQL Server](connection-to-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="071a8-126">For information on how to enter the credentials for a login that has write permission to the MSXDBCDC database, such the **db_owner** database role, see [Create and Edit an Oracle CDC Service](create-and-edit-an-oracle-cdc-service.md) and [Connection to SQL Server](connection-to-sql-server.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="071a8-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="071a8-127">See Also</span></span>  
 [<span data-ttu-id="071a8-128">使用 CDC 服務</span><span class="sxs-lookup"><span data-stu-id="071a8-128">Work with CDC Services</span></span>](work-with-cdc-services.md)  
  
  
