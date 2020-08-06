---
title: 選取來源對話方塊 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
f1_keywords:
- sql12.swb.dmf.selectsource.f1
ms.assetid: d664c2e5-dd0c-4da8-b27d-aa4ee4fc0ffd
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 535d211d6827477fcf029accc27a9000e8c695c4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708214"
---
# <a name="select-source-dialog-box"></a><span data-ttu-id="0d6d0-102">選取來源對話方塊</span><span class="sxs-lookup"><span data-stu-id="0d6d0-102">Select Source Dialog Box</span></span>
  <span data-ttu-id="0d6d0-103">使用此對話方塊可選取要執行之原則的來源。</span><span class="sxs-lookup"><span data-stu-id="0d6d0-103">Use this dialog box to select the source of the policies to be run.</span></span> <span data-ttu-id="0d6d0-104">若要選取一或多個包含原則的 XML 檔案，請選取 [檔案]  。</span><span class="sxs-lookup"><span data-stu-id="0d6d0-104">To select one or more XML files that contain policies, select **Files**.</span></span> <span data-ttu-id="0d6d0-105">若要執行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體上找到的原則，請選取 [伺服器]  。</span><span class="sxs-lookup"><span data-stu-id="0d6d0-105">To run the policies that are found on the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], select **Server**.</span></span>  
  
 <span data-ttu-id="0d6d0-106">您可以利用以下幾種方式來開啟這個對話方塊。</span><span class="sxs-lookup"><span data-stu-id="0d6d0-106">You can open this dialog box in several ways.</span></span>  
  
 <span data-ttu-id="0d6d0-107">**開啟這個對話方塊**</span><span class="sxs-lookup"><span data-stu-id="0d6d0-107">**To open this dialog box**</span></span>  
  
-   <span data-ttu-id="0d6d0-108">在 [已註冊的伺服器] 中，以滑鼠右鍵按一下 [本機伺服器群組]  或 [本機伺服器群組]  底下的任何伺服器，或是 [中央管理伺服器]  底下的任何伺服器，然後選取 [評估原則]  。</span><span class="sxs-lookup"><span data-stu-id="0d6d0-108">In Registered Servers, right-click **Local Server Groups** or any server under **Local Server Groups**, or any server under **Central Management Servers**, and then select **Evaluate Policies**.</span></span> <span data-ttu-id="0d6d0-109">在 [評估原則] 對話方塊的 [原則選取] 頁面中，按一下 [瀏覽]\(...) 按鈕。</span><span class="sxs-lookup"><span data-stu-id="0d6d0-109">In the **Policy Selection** page of the **Evaluate Policies** dialog box, click the Browse (**...**) button.</span></span>  
  
-   <span data-ttu-id="0d6d0-110">在物件總管中，依序展開 [管理]  和 [原則管理]  ，並以滑鼠右鍵按一下 [原則]  ，然後選取 [匯入原則]  。</span><span class="sxs-lookup"><span data-stu-id="0d6d0-110">In Object Explorer, expand **Management**, expand **Policy Management**, right-click **Policies**, and select **Import Policy**.</span></span> <span data-ttu-id="0d6d0-111">在 [匯入]  對話方塊中，按一下 [瀏覽]\(...)  按鈕。</span><span class="sxs-lookup"><span data-stu-id="0d6d0-111">In the **Import** dialog box, click the Browse (**...**) button.</span></span>  
  
-   <span data-ttu-id="0d6d0-112">在物件總管中，以滑鼠右鍵按一下伺服器、資料庫或資料庫物件，然後選取 [原則]  ，再選取 [評估]  。</span><span class="sxs-lookup"><span data-stu-id="0d6d0-112">In Object Explorer, right-click a server, database, or database object, select **Policies**, and then select **Evaluate**.</span></span> <span data-ttu-id="0d6d0-113">在 [評估原則] 對話方塊的 [原則選取] 頁面中，按一下 [瀏覽]\(...) 按鈕。</span><span class="sxs-lookup"><span data-stu-id="0d6d0-113">In the **Policy Selection** page of the **Evaluate Policies** dialog box, click the Browse (**...**) button.</span></span>  
  
## <a name="options"></a><span data-ttu-id="0d6d0-114">選項。</span><span class="sxs-lookup"><span data-stu-id="0d6d0-114">Options</span></span>  
 <span data-ttu-id="0d6d0-115">**檔案**</span><span class="sxs-lookup"><span data-stu-id="0d6d0-115">**Files**</span></span>  
 <span data-ttu-id="0d6d0-116">選取一或多個包含原則的 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="0d6d0-116">Select one or more XML files that contain policies.</span></span>  
  
 <span data-ttu-id="0d6d0-117">**Server**</span><span class="sxs-lookup"><span data-stu-id="0d6d0-117">**Server**</span></span>  
 <span data-ttu-id="0d6d0-118">可讓您選取包含您想要執行之原則的伺服器。</span><span class="sxs-lookup"><span data-stu-id="0d6d0-118">Enables you to select a server that contains the policies that you want to run.</span></span>  
  
 <span data-ttu-id="0d6d0-119">**伺服器類型**</span><span class="sxs-lookup"><span data-stu-id="0d6d0-119">**Server type**</span></span>  
 <span data-ttu-id="0d6d0-120">只有 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 伺服器才會包含原則。</span><span class="sxs-lookup"><span data-stu-id="0d6d0-120">Only [!INCLUDE[ssDE](../../includes/ssde-md.md)] servers contain policies.</span></span> <span data-ttu-id="0d6d0-121">這個方塊是唯讀的。</span><span class="sxs-lookup"><span data-stu-id="0d6d0-121">This box is read-only.</span></span>  
  
 <span data-ttu-id="0d6d0-122">**伺服器名稱**</span><span class="sxs-lookup"><span data-stu-id="0d6d0-122">**Server name**</span></span>  
 <span data-ttu-id="0d6d0-123">選取要連接的伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="0d6d0-123">Select the server instance to connect to.</span></span> <span data-ttu-id="0d6d0-124">依預設，會顯示上次連接的伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="0d6d0-124">By default, the server instance last connected to is displayed.</span></span>  
  
 <span data-ttu-id="0d6d0-125">**驗證**</span><span class="sxs-lookup"><span data-stu-id="0d6d0-125">**Authentication**</span></span>  
 <span data-ttu-id="0d6d0-126">當連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]執行個體時，有兩種可用的驗證模式。</span><span class="sxs-lookup"><span data-stu-id="0d6d0-126">Two authentication modes are available when you connect to an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
 <span data-ttu-id="0d6d0-127">**Windows 驗證模式 (Windows 驗證)**</span><span class="sxs-lookup"><span data-stu-id="0d6d0-127">**Windows Authentication Mode (Windows Authentication)**</span></span>  
 <span data-ttu-id="0d6d0-128">Windows 驗證模式允許使用者透過 Windows 使用者帳戶連接。</span><span class="sxs-lookup"><span data-stu-id="0d6d0-128">Windows Authentication mode allows for a user to connect through a Windows user account.</span></span>  
  
 <span data-ttu-id="0d6d0-129">**SQL Server 驗證**</span><span class="sxs-lookup"><span data-stu-id="0d6d0-129">**SQL Server Authentication**</span></span>  
 <span data-ttu-id="0d6d0-130">當使用者從非信任連接使用指定的登入名稱與密碼進行連接時， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 會查看是否已設定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登入帳戶，以及指定的密碼是否符合先前記錄的密碼，自行執行驗證。</span><span class="sxs-lookup"><span data-stu-id="0d6d0-130">When a user connects with a specified login name and password from a nontrusted connection, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] performs the authentication itself by checking whether a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login account has been set up and whether the specified password matches the one previously recorded.</span></span> <span data-ttu-id="0d6d0-131">如果 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 沒有登入帳戶集，驗證將失敗，而使用者會收到錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="0d6d0-131">If [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] does not have a login account set, authentication fails, and the user receives an error message.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="0d6d0-132">盡可能使用 Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="0d6d0-132">When possible, use Windows Authentication.</span></span>  
  
 <span data-ttu-id="0d6d0-133">**使用者名稱**</span><span class="sxs-lookup"><span data-stu-id="0d6d0-133">**User name**</span></span>  
 <span data-ttu-id="0d6d0-134">輸入要用來連接的使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="0d6d0-134">Enter the user name to connect with.</span></span> <span data-ttu-id="0d6d0-135">只有在您已選取使用 Windows 驗證進行連接時，才能使用此選項。</span><span class="sxs-lookup"><span data-stu-id="0d6d0-135">This option is available only if you have selected to connect by using Windows Authentication.</span></span>  
  
 <span data-ttu-id="0d6d0-136">**登入**</span><span class="sxs-lookup"><span data-stu-id="0d6d0-136">**Login**</span></span>  
 <span data-ttu-id="0d6d0-137">輸入要用來連接的登入。</span><span class="sxs-lookup"><span data-stu-id="0d6d0-137">Enter the login to connect with.</span></span> <span data-ttu-id="0d6d0-138">只有在您已選取使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 驗證進行連接時，才可以使用這個選項。</span><span class="sxs-lookup"><span data-stu-id="0d6d0-138">This option is available only if you have selected to connect by using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span>  
  
 <span data-ttu-id="0d6d0-139">**密碼**</span><span class="sxs-lookup"><span data-stu-id="0d6d0-139">**Password**</span></span>  
 <span data-ttu-id="0d6d0-140">輸入登入的密碼。</span><span class="sxs-lookup"><span data-stu-id="0d6d0-140">Enter the password for the login.</span></span> <span data-ttu-id="0d6d0-141">只有在您已選取使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 驗證進行連接時，才可編輯此選項。</span><span class="sxs-lookup"><span data-stu-id="0d6d0-141">This option is editable only if you have selected to connect by using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d6d0-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0d6d0-142">See Also</span></span>  
 <span data-ttu-id="0d6d0-143">[原則管理節點 &#40;物件總管&#41;](../../ssms/object/object-explorer.md) </span><span class="sxs-lookup"><span data-stu-id="0d6d0-143">[Policy Management Node &#40;Object Explorer&#41;](../../ssms/object/object-explorer.md) </span></span>  
 [<span data-ttu-id="0d6d0-144">使用原則式管理來管理伺服器</span><span class="sxs-lookup"><span data-stu-id="0d6d0-144">Administer Servers by Using Policy-Based Management</span></span>](administer-servers-by-using-policy-based-management.md)  
  
  
