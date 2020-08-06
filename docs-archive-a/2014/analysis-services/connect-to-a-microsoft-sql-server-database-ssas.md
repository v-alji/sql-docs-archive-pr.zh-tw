---
title: 連接到 Microsoft SQL Server 的資料庫 (SSAS) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.connsqlserverdb.f1
ms.assetid: 6ebfe029-dbba-4f0d-a556-328e79ef629f
author: minewiskan
ms.author: owend
ms.openlocfilehash: 64267cd65836cf8e6c8d8b26a177de595894b601
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593023"
---
# <a name="connect-to-a-microsoft-sql-server-database-ssas"></a><span data-ttu-id="12130-102">連接到 Microsoft SQL Server 資料庫 (SSAS)</span><span class="sxs-lookup"><span data-stu-id="12130-102">Connect to a Microsoft SQL Server Database (SSAS)</span></span>
  <span data-ttu-id="12130-103">**[資料表匯入精靈]** 的這個頁面可讓您指定連接到 Microsoft SQL Server 資料庫的設定。</span><span class="sxs-lookup"><span data-stu-id="12130-103">This page of the **Table Import Wizard** enables you to specify settings to connect to a Microsoft SQL Server database.</span></span> <span data-ttu-id="12130-104">若要從 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]存取精靈，請按一下 **[模型]** 功能表上的 **[從資料來源匯入]**。</span><span class="sxs-lookup"><span data-stu-id="12130-104">To access the wizard from the [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], on the **Model** menu, click **Import from Data Source**.</span></span>  
  
 <span data-ttu-id="12130-105">若要連接至資料來源，您必須先在電腦上安裝適當的提供者。</span><span class="sxs-lookup"><span data-stu-id="12130-105">To connect to a data source, you must have the appropriate provider installed on your computer.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="12130-106">在這個頁面中選取資料庫時，會使用目前使用者的認證。</span><span class="sxs-lookup"><span data-stu-id="12130-106">The credentials of the current user are used when selecting a database in this page.</span></span> <span data-ttu-id="12130-107">不過，如果在 [模擬資訊] 頁面中指定的使用者未具備從所選取資料庫讀取的權限，則匯入將不會成功。</span><span class="sxs-lookup"><span data-stu-id="12130-107">However, import will not succeed if the user specified in the Impersonation Information page does not have sufficient privileges to read from the selected database.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="12130-108">UI 元素清單</span><span class="sxs-lookup"><span data-stu-id="12130-108">UI element list</span></span>  
 <span data-ttu-id="12130-109">**易記連接名稱**</span><span class="sxs-lookup"><span data-stu-id="12130-109">**Friendly connection name**</span></span>  
 <span data-ttu-id="12130-110">為此資料來源連接輸入唯一的名稱。</span><span class="sxs-lookup"><span data-stu-id="12130-110">Type a unique name for this data source connection.</span></span> <span data-ttu-id="12130-111">這是必要的欄位。</span><span class="sxs-lookup"><span data-stu-id="12130-111">This is a required field.</span></span>  
  
 <span data-ttu-id="12130-112">**伺服器名稱**</span><span class="sxs-lookup"><span data-stu-id="12130-112">**Server name**</span></span>  
 <span data-ttu-id="12130-113">選取要連接之 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 執行個體的名稱，或輸入它的名稱或 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="12130-113">Select the name, or type the name or IP address, of the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] instance to connect to.</span></span>  
  
 <span data-ttu-id="12130-114">您可以使用句號 (.)、(local) 或 localhost 表示本機伺服器。</span><span class="sxs-lookup"><span data-stu-id="12130-114">You can use a period (.), (local), or localhost to indicate the local server.</span></span>  
  
 <span data-ttu-id="12130-115">**[使用 Windows 驗證]**</span><span class="sxs-lookup"><span data-stu-id="12130-115">**Use Windows Authentication**</span></span>  
 <span data-ttu-id="12130-116">指定是否使用 Windows 驗證來連接 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="12130-116">Specify whether Windows Authentication is used to connect to an instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="12130-117">Windows 驗證模式可讓使用者透過 Windows 使用者帳戶進行連接。</span><span class="sxs-lookup"><span data-stu-id="12130-117">Windows Authentication mode enables a user to connect by using a Windows user account.</span></span> <span data-ttu-id="12130-118">可能的話，請使用 Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="12130-118">Whenever possible, use Windows Authentication.</span></span>  
  
 <span data-ttu-id="12130-119">如果使用 Windows 驗證，目前使用者的認證會在預覽和篩選 [資料表屬性] 視窗和 [匯入精靈] 中的資料時使用。</span><span class="sxs-lookup"><span data-stu-id="12130-119">When Windows Authentication is used, the credentials of the current user are used when previewing and filtering data in the Table Properties window and in the Import Wizard.</span></span> <span data-ttu-id="12130-120">這些認證不會用來匯入或重新整理資料，而是會使用 [模擬資訊] 頁面上指定的 Windows 認證。</span><span class="sxs-lookup"><span data-stu-id="12130-120">These credentials are not used to import or refresh data; the Windows credentials specified on the Impersonation information page are used instead.</span></span>  
  
 <span data-ttu-id="12130-121">**[使用 SQL Server 驗證]**</span><span class="sxs-lookup"><span data-stu-id="12130-121">**Use SQL Server Authentication**</span></span>  
 <span data-ttu-id="12130-122">指定是否使用 SQL Server 驗證來連接 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="12130-122">Specify whether SQL Server Authentication is used to connect to an instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="12130-123">使用 SQL Server 驗證時，SQL Server 會查看是否已經設定 SQL Server 登入帳戶，以及指定的密碼是否符合先前記錄的密碼，藉以自行執行驗證。</span><span class="sxs-lookup"><span data-stu-id="12130-123">With SQL Server Authentication, SQL Server performs the authentication itself by checking to see if a SQL Server login account has been set up and if the specified password matches the one previously recorded.</span></span>  
  
 <span data-ttu-id="12130-124">SQL Server 驗證是用來建構資料來源的連接字串。</span><span class="sxs-lookup"><span data-stu-id="12130-124">SQL Server Authentication is used to construct the connection string for the data source.</span></span> <span data-ttu-id="12130-125">這些認證也會在預覽和篩選 [資料表屬性] 視窗和 [匯入精靈] 中的資料時使用。</span><span class="sxs-lookup"><span data-stu-id="12130-125">These credentials are also used when previewing and filtering data in the Table Properties window and in the Import Wizard.</span></span> <span data-ttu-id="12130-126">這些認證不會用來匯入或重新整理資料，而是會使用 [模擬資訊] 頁面上指定的 Windows 認證。</span><span class="sxs-lookup"><span data-stu-id="12130-126">These credentials are not used to import or refresh data; the Windows credentials specified on the Impersonation Information page are used instead.</span></span>  
  
 <span data-ttu-id="12130-127">**使用者名稱**</span><span class="sxs-lookup"><span data-stu-id="12130-127">**User name**</span></span>  
 <span data-ttu-id="12130-128">為資料庫連接指定使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="12130-128">Specify a user name for the database connection.</span></span> <span data-ttu-id="12130-129">只有在您選擇使用 [SQL Server 驗證] 進行連接時，才能使用此選項。</span><span class="sxs-lookup"><span data-stu-id="12130-129">This option is only available if you have selected to connect using SQL Server Authentication.</span></span>  
  
 <span data-ttu-id="12130-130">**密碼**</span><span class="sxs-lookup"><span data-stu-id="12130-130">**Password**</span></span>  
 <span data-ttu-id="12130-131">為資料庫連接指定密碼。</span><span class="sxs-lookup"><span data-stu-id="12130-131">Specify a password for the database connection.</span></span> <span data-ttu-id="12130-132">只有在您選擇使用 [SQL Server 驗證] 進行連接時，才能編輯此選項。</span><span class="sxs-lookup"><span data-stu-id="12130-132">This option is only editable if you have selected to connect using SQL Server Authentication.</span></span>  
  
 <span data-ttu-id="12130-133">**儲存密碼**</span><span class="sxs-lookup"><span data-stu-id="12130-133">**Save my password**</span></span>  
 <span data-ttu-id="12130-134">指定是否要儲存您在 **[密碼]** 方塊中輸入的密碼。</span><span class="sxs-lookup"><span data-stu-id="12130-134">Specify whether the password you have entered in the **Password** box is stored.</span></span> <span data-ttu-id="12130-135">只有在您選擇使用 [SQL Server 驗證] 進行連接時，才能使用此選項。</span><span class="sxs-lookup"><span data-stu-id="12130-135">This option is only available if you have selected to connect using SQL Server Authentication.</span></span>  
  
 <span data-ttu-id="12130-136">**資料庫名稱**</span><span class="sxs-lookup"><span data-stu-id="12130-136">**Database name**</span></span>  
 <span data-ttu-id="12130-137">從資料庫清單中選取資料庫。</span><span class="sxs-lookup"><span data-stu-id="12130-137">Select a database from the list of databases.</span></span>  
  
 <span data-ttu-id="12130-138">**進階**</span><span class="sxs-lookup"><span data-stu-id="12130-138">**Advanced**</span></span>  
 <span data-ttu-id="12130-139">使用 **[設定進階屬性]** 對話方塊設定其他連接屬性。</span><span class="sxs-lookup"><span data-stu-id="12130-139">Set additional connection properties by using the **Set Advanced Properties** dialog box.</span></span> <span data-ttu-id="12130-140">如需詳細資訊，請參閱[設定進階屬性 &#40;SSAS&#41;](set-advanced-properties-ssas.md)。</span><span class="sxs-lookup"><span data-stu-id="12130-140">For more information, see [Set Advanced Properties &#40;SSAS&#41;](set-advanced-properties-ssas.md).</span></span>  
  
 <span data-ttu-id="12130-141">**測試連接**</span><span class="sxs-lookup"><span data-stu-id="12130-141">**Test Connection**</span></span>  
 <span data-ttu-id="12130-142">嘗試使用目前的設定建立與資料來源之間的連接。</span><span class="sxs-lookup"><span data-stu-id="12130-142">Attempt to establish a connection to the data source using the current settings.</span></span> <span data-ttu-id="12130-143">顯示一則訊息，指出連接是否成功。</span><span class="sxs-lookup"><span data-stu-id="12130-143">A message is displayed indicating whether the connection was successful.</span></span>  
  
  
