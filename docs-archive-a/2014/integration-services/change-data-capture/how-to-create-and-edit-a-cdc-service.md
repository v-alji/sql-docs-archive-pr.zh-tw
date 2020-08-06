---
title: 如何建立及編輯 CDC 服務 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 1b3d47a5-dc89-482d-bbc7-fff04f194c43
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d90534b475901b08fcd2e09acdc0f7976f0fb6e9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687115"
---
# <a name="how-to-create-and-edit-a-cdc-service"></a><span data-ttu-id="8d7dd-102">如何建立及編輯 CDC 服務</span><span class="sxs-lookup"><span data-stu-id="8d7dd-102">How to Create and Edit a CDC Service</span></span>
  <span data-ttu-id="8d7dd-103">這些程序描述如何從 CDC 服務組態主控台來建立和編輯新的 Oracle CDC 服務。</span><span class="sxs-lookup"><span data-stu-id="8d7dd-103">These procedures describe how to create and edit a new Oracle CDC Service from the CDC Service Configuration Console.</span></span>  
  
 <span data-ttu-id="8d7dd-104">此程序要求在設定 Oracle CDC 服務的電腦上必須有系統管理員權限的 Windows 使用者。</span><span class="sxs-lookup"><span data-stu-id="8d7dd-104">This procedure requires a Windows user with administrator privileges on the computer where the Oracle CDC service is configured.</span></span>  
  
### <a name="to-create-a-new-cdc-service"></a><span data-ttu-id="8d7dd-105">若要建立新的 CDC 服務</span><span class="sxs-lookup"><span data-stu-id="8d7dd-105">To create a new CDC service</span></span>  
  
1.  <span data-ttu-id="8d7dd-106">從 **[開始]** 功能表，選取 **[Oracle CDC 服務組態]** 。</span><span class="sxs-lookup"><span data-stu-id="8d7dd-106">From the **Start** menu, select **CDC Service Configuration for Oracle**.</span></span>  
  
2.  <span data-ttu-id="8d7dd-107">您也可以從左窗格以滑鼠右鍵按一下 [本機 CDC 服務]，並選取 [新增服務]。</span><span class="sxs-lookup"><span data-stu-id="8d7dd-107">From the left pane, right click Local CDC Services and select New Service</span></span>  
  
     <span data-ttu-id="8d7dd-108">您也可以從 **[動作]** 窗格按一下 **[新增服務]** 。</span><span class="sxs-lookup"><span data-stu-id="8d7dd-108">You can also click **New Service** from the **Actions** pane.</span></span>  
  
3.  <span data-ttu-id="8d7dd-109">在 [新增 Oracle CDC 服務] 對話方塊中輸入必要的資訊。</span><span class="sxs-lookup"><span data-stu-id="8d7dd-109">Type or enter the required information in the New Oracle CDC Service dialog box.</span></span> <span data-ttu-id="8d7dd-110">如需有關如何在 [新增 Oracle CDC 服務] 對話方塊中輸入資訊的詳細資訊，請參閱＜ [Create and Edit an Oracle CDC Service](create-and-edit-an-oracle-cdc-service.md) ＞。</span><span class="sxs-lookup"><span data-stu-id="8d7dd-110">See [Create and Edit an Oracle CDC Service](create-and-edit-an-oracle-cdc-service.md) for information on how to enter information in the New Oracle CDC Service dialog box.</span></span>  
  
     <span data-ttu-id="8d7dd-111">當 Oracle CDC 服務執行時，此服務會使用在 [新增 Oracle CDC 服務] 對話方塊中所提供的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登入。</span><span class="sxs-lookup"><span data-stu-id="8d7dd-111">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login provided in the New Oracle CDC Service dialog box is used by the Oracle CDC Service when the service runs.</span></span> <span data-ttu-id="8d7dd-112">此登入只要求它必須是公用固定伺服器角色的成員，不需要其他權限。</span><span class="sxs-lookup"><span data-stu-id="8d7dd-112">This login only needs to be a member of the public fixed-server role, no other privileges are needed.</span></span> <span data-ttu-id="8d7dd-113">一旦加入新的 Oracle CDC 執行個體之後，該登入會收到關聯 **CDC 資料庫的** db_owner [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 存取權。</span><span class="sxs-lookup"><span data-stu-id="8d7dd-113">Once new Oracle CDC Instances are added, that login receives **db_owner** access to the associated [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] CDC databases.</span></span>  
  
4.  <span data-ttu-id="8d7dd-114">當您將所需的資訊輸入完畢時，請按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="8d7dd-114">When you finish entering the required information, click **OK**.</span></span>  
  
     <span data-ttu-id="8d7dd-115">若要建立 Oracle CDC Windows 服務定義，此程式需要關聯 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體中 MSXDBCDC 資料庫的更新存取權。</span><span class="sxs-lookup"><span data-stu-id="8d7dd-115">To create the Oracle CDC Windows Service definition, the program needs update access to the MSXDBCDC database in the associated [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span> <span data-ttu-id="8d7dd-116">當您按一下 **[確定]** 時，隨即出現一個對話方塊，提示使用者輸入具有 MSXDBCDC 資料庫之更新存取權的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登入。</span><span class="sxs-lookup"><span data-stu-id="8d7dd-116">When you click **OK**, a dialog box prompts the user to enter a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login with an update access to the MSXDBCDC database.</span></span>  
  
     <span data-ttu-id="8d7dd-117">如需有關您必須在 [連接到 SQL Server] 對話方塊中輸入之資料的詳細資訊，請參閱＜ [Connection to SQL Server](connection-to-sql-server.md)＞。</span><span class="sxs-lookup"><span data-stu-id="8d7dd-117">For information about the data you must type into the Connect to SQL Server dialog box, see [Connection to SQL Server](connection-to-sql-server.md).</span></span>  
  
5.  <span data-ttu-id="8d7dd-118">按一下 **[確定]** 關閉 [新增 Oracle CDC 服務] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="8d7dd-118">Click **OK** to close the New Oracle CDC Service dialog box.</span></span>  
  
### <a name="to-edit-a-cdc-service"></a><span data-ttu-id="8d7dd-119">若要編輯 CDC 服務</span><span class="sxs-lookup"><span data-stu-id="8d7dd-119">To edit a CDC service</span></span>  
  
1.  <span data-ttu-id="8d7dd-120">從 **[開始]** 功能表，選取 **[Oracle CDC 服務組態]** 。</span><span class="sxs-lookup"><span data-stu-id="8d7dd-120">From the **Start** menu, select **CDC Service Configuration for Oracle**.</span></span>  
  
2.  <span data-ttu-id="8d7dd-121">從左窗格選取 [Local CDC Services (本機 CDC 服務)]  ，然後以滑鼠右鍵按一下您想要編輯的本機服務，並選取 [屬性]  。</span><span class="sxs-lookup"><span data-stu-id="8d7dd-121">From the left pane, select **Local CDC Services** then right-click the local service you want to edit and select **Properties**.</span></span>  
  
     <span data-ttu-id="8d7dd-122">您也可以在中間選取您要使用的服務，然後從 **[動作]** 窗格按一下 **[屬性]** 。</span><span class="sxs-lookup"><span data-stu-id="8d7dd-122">You can also select the service you are working with in the middle and then from the **Actions** pane, click **Properties**.</span></span>  
  
3.  <span data-ttu-id="8d7dd-123">在 [CDC 服務屬性] 對話方塊中輸入必要的資訊。</span><span class="sxs-lookup"><span data-stu-id="8d7dd-123">Type or enter the required information in the CDC Service Properties dialog box.</span></span> <span data-ttu-id="8d7dd-124">如需有關如何在 [CDC 服務屬性] 對話方塊中輸入資訊的詳細資訊，請參閱＜ [Create and Edit an Oracle CDC Service](create-and-edit-an-oracle-cdc-service.md) ＞。</span><span class="sxs-lookup"><span data-stu-id="8d7dd-124">See [Create and Edit an Oracle CDC Service](create-and-edit-an-oracle-cdc-service.md) for information on how to enter information in the CDC Service Properties dialog box.</span></span>  
  
4.  <span data-ttu-id="8d7dd-125">當您將所需的資訊輸入完畢時，請按一下 **[確定]** ，隨即開啟 [連接到 SQL Server] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="8d7dd-125">When you finish entering the required information, Click **OK**, the Connect to SQL Server dialog box opens.</span></span>  
  
     <span data-ttu-id="8d7dd-126">當沒有 MSXDBDCDC 資料庫寫入權限的登入嘗試建立新的 Oracle CDC 執行個體時，便會顯示錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="8d7dd-126">When a login without write permission to the MSXDBDCDC database attempts to create a new Oracle CDC instance an error message is displayed.</span></span> <span data-ttu-id="8d7dd-127">在這個對話方塊中按一下 **[確定]** ，隨即顯示 [連接到 SQL Server] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="8d7dd-127">Click **OK** in that dialog box to display the Connect to SQL Server dialog box.</span></span> <span data-ttu-id="8d7dd-128">在此對話方塊中，您必須輸入擁有 MSXDBCDC 資料庫寫入權限之登入的認證，例如 **db_owner** 資料庫角色。</span><span class="sxs-lookup"><span data-stu-id="8d7dd-128">In this dialog box you must enter the credentials for a login that has write permission to the MSXDBCDC database, such the **db_owner** database role.</span></span>  
  
     <span data-ttu-id="8d7dd-129">如需有關您必須在 [連接到 SQL Server] 對話方塊中輸入之資料的詳細資訊，請參閱＜ [Connection to SQL Server](connection-to-sql-server.md)＞。</span><span class="sxs-lookup"><span data-stu-id="8d7dd-129">For information about the data you must type into the Connect to SQL Server dialog box, see [Connection to SQL Server](connection-to-sql-server.md).</span></span>  
  
5.  <span data-ttu-id="8d7dd-130">在 [連接到 Oracle] 對話方塊中按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="8d7dd-130">Click **OK** in the Connect to Oracle dialog box.</span></span> <span data-ttu-id="8d7dd-131">隨即關閉這兩個對話方塊，而且會更新及註冊此服務。</span><span class="sxs-lookup"><span data-stu-id="8d7dd-131">Both dialog boxes close and the service is updated and registered.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d7dd-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8d7dd-132">See Also</span></span>  
 <span data-ttu-id="8d7dd-133">[Attunity Oracle 異動資料擷取設計工具](change-data-capture-designer-for-oracle-by-attunity.md) </span><span class="sxs-lookup"><span data-stu-id="8d7dd-133">[Change Data Capture Designer for Oracle by Attunity](change-data-capture-designer-for-oracle-by-attunity.md) </span></span>  
 [<span data-ttu-id="8d7dd-134">建立及編輯 Oracle CDC 服務</span><span class="sxs-lookup"><span data-stu-id="8d7dd-134">Create and Edit an Oracle CDC Service</span></span>](create-and-edit-an-oracle-cdc-service.md)  
  
  
