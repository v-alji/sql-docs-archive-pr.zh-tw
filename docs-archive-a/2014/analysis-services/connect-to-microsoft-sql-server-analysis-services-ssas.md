---
title: 連接到 Microsoft SQL Server Analysis Services (SSAS) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.connsqlserveras.f1
ms.assetid: 7f3244ee-b690-471c-893d-68e361c2d416
author: minewiskan
ms.author: owend
ms.openlocfilehash: 984979480e3ea54c86c986fa6dd9771aaf879cb1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593000"
---
# <a name="connect-to-microsoft-sql-server-analysis-services-ssas"></a><span data-ttu-id="b7c47-102">連接到 Microsoft SQL Server Analysis Services (SSAS)</span><span class="sxs-lookup"><span data-stu-id="b7c47-102">Connect to Microsoft SQL Server Analysis Services (SSAS)</span></span>
  <span data-ttu-id="b7c47-103">[**資料表匯入嚮導]** 的這個頁面可讓您指定從 SharePoint 上主控的 Microsoft SQL Server Analysis Services Cube 或 PowerPivot 活頁簿匯入資料的設定。</span><span class="sxs-lookup"><span data-stu-id="b7c47-103">This page of the **Table Import Wizard** enables you to specify settings to import data from a Microsoft SQL Server Analysis Services cube or a PowerPivot workbook that is hosted on SharePoint.</span></span> <span data-ttu-id="b7c47-104">若要從 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]存取精靈，請按一下 **[模型]** 功能表上的 **[從資料來源匯入]**。</span><span class="sxs-lookup"><span data-stu-id="b7c47-104">To access the wizard from the [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], on the **Model** menu, click **Import from Data Source**.</span></span>  
  
 <span data-ttu-id="b7c47-105">若要連接至資料來源，您必須先在電腦上安裝適當的提供者。</span><span class="sxs-lookup"><span data-stu-id="b7c47-105">To connect to a data source, you must have the appropriate provider installed on your computer.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b7c47-106">在這個頁面中選取資料庫時，會使用目前使用者的認證。</span><span class="sxs-lookup"><span data-stu-id="b7c47-106">The credentials of the current user are used when selecting a database in this page.</span></span> <span data-ttu-id="b7c47-107">不過，如果在 [模擬資訊] 頁面中指定的使用者未具備從所選取資料庫讀取的權限，則匯入將不會成功。</span><span class="sxs-lookup"><span data-stu-id="b7c47-107">However, import will not succeed if the user specified in the Impersonation Information page does not have sufficient privileges to read from the selected database.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="b7c47-108">UI 元素清單</span><span class="sxs-lookup"><span data-stu-id="b7c47-108">UI element list</span></span>  
 <span data-ttu-id="b7c47-109">**易記連接名稱**</span><span class="sxs-lookup"><span data-stu-id="b7c47-109">**Friendly connection name**</span></span>  
 <span data-ttu-id="b7c47-110">為此資料來源連接輸入唯一的名稱。</span><span class="sxs-lookup"><span data-stu-id="b7c47-110">Type a unique name for this data source connection.</span></span> <span data-ttu-id="b7c47-111">這是必要的欄位。</span><span class="sxs-lookup"><span data-stu-id="b7c47-111">This is a required field.</span></span>  
  
 <span data-ttu-id="b7c47-112">**伺服器或檔案名稱**</span><span class="sxs-lookup"><span data-stu-id="b7c47-112">**Server or File Name**</span></span>  
 <span data-ttu-id="b7c47-113">輸入下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="b7c47-113">Enter one of the following:</span></span>  
  
-   <span data-ttu-id="b7c47-114">輸入要連接之 SQL Server Analysis Services 伺服器的名稱或 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="b7c47-114">Type the name or IP address of the SQL Server Analysis Services server to connect to.</span></span>  
  
     <span data-ttu-id="b7c47-115">您可以使用句號 (.)、(local) 或 localhost 表示本機伺服器。</span><span class="sxs-lookup"><span data-stu-id="b7c47-115">You can use a period (.), (local), or localhost to indicate the local server.</span></span>  
  
-   <span data-ttu-id="b7c47-116">輸入發行至 SharePoint 之 PowerPivot 活頁簿的 URL。</span><span class="sxs-lookup"><span data-stu-id="b7c47-116">Type the URL of a PowerPivot workbook that is published to SharePoint.</span></span>  
  
 <span data-ttu-id="b7c47-117">**[使用 Windows 驗證]**</span><span class="sxs-lookup"><span data-stu-id="b7c47-117">**Use Windows Authentication**</span></span>  
 <span data-ttu-id="b7c47-118">指定是否使用 Windows 驗證來連接 SQL Server Analysis Services 伺服器。</span><span class="sxs-lookup"><span data-stu-id="b7c47-118">Specify whether Windows Authentication is used to connect to a SQL Server Analysis Services server.</span></span>  
  
 <span data-ttu-id="b7c47-119">Windows 驗證模式可讓使用者透過 Windows 使用者帳戶連接。</span><span class="sxs-lookup"><span data-stu-id="b7c47-119">Windows Authentication mode enables a user to connect through a Windows user account.</span></span> <span data-ttu-id="b7c47-120">可能的話，請使用 Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="b7c47-120">Whenever possible, use Windows Authentication.</span></span>  
  
 <span data-ttu-id="b7c47-121">如果使用 Windows 驗證，目前使用者的認證會在預覽和篩選 [資料表屬性] 視窗和 [匯入精靈] 中的資料時使用。</span><span class="sxs-lookup"><span data-stu-id="b7c47-121">When Windows Authentication is used, the credentials of the current user are used when previewing and filtering data in the Table Properties window and in the Import Wizard.</span></span> <span data-ttu-id="b7c47-122">這些認證不會用來匯入或重新整理資料，而是會使用 [模擬資訊] 頁面上指定的 Windows 認證。</span><span class="sxs-lookup"><span data-stu-id="b7c47-122">These credentials are not used to import or refresh data; the Windows credentials specified on the Impersonation Information page are used instead.</span></span>  
  
 <span data-ttu-id="b7c47-123">**[使用 SQL Server 驗證]**</span><span class="sxs-lookup"><span data-stu-id="b7c47-123">**Use SQL Server Authentication**</span></span>  
 <span data-ttu-id="b7c47-124">指定是否使用 SQL Server 驗證來連接 SQL Server Analysis Services 伺服器。</span><span class="sxs-lookup"><span data-stu-id="b7c47-124">Specify whether SQL Server Authentication is used to connect to a SQL Server Analysis Services server.</span></span>  
  
 <span data-ttu-id="b7c47-125">使用 SQL Server 驗證時，SQL Server 會查看是否已經設定 SQL Server 登入帳戶，以及指定的密碼是否符合先前記錄的密碼，藉以自行執行驗證。</span><span class="sxs-lookup"><span data-stu-id="b7c47-125">With SQL Server Authentication, SQL Server performs the authentication itself by checking to see if a SQL Server login account has been set up and if the specified password matches the one previously recorded.</span></span>  
  
 <span data-ttu-id="b7c47-126">SQL Server 驗證是用來建構資料來源的連接字串。</span><span class="sxs-lookup"><span data-stu-id="b7c47-126">SQL Server Authentication is used to construct the connection string for the data source.</span></span> <span data-ttu-id="b7c47-127">這些認證也會在預覽和篩選 [資料表屬性] 視窗和 [匯入精靈] 中的資料時使用。</span><span class="sxs-lookup"><span data-stu-id="b7c47-127">These credentials are also used when previewing and filtering data in the Table Properties window and in the Import Wizard.</span></span> <span data-ttu-id="b7c47-128">這些認證不會用來匯入或重新整理資料，而是會使用 [模擬資訊] 頁面上指定的 Windows 認證。</span><span class="sxs-lookup"><span data-stu-id="b7c47-128">These credentials are not used to import or refresh data; the Windows credentials specified on the Impersonation Information page are used instead.</span></span>  
  
 <span data-ttu-id="b7c47-129">**使用者名稱**</span><span class="sxs-lookup"><span data-stu-id="b7c47-129">**User name**</span></span>  
 <span data-ttu-id="b7c47-130">為資料庫連接指定使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="b7c47-130">Specify a user name for the database connection.</span></span> <span data-ttu-id="b7c47-131">只有在您選取使用 Windows 驗證連接時，才能使用此選項。</span><span class="sxs-lookup"><span data-stu-id="b7c47-131">This option is only available if you have selected to connect using Windows Authentication.</span></span>  
  
 <span data-ttu-id="b7c47-132">**密碼**</span><span class="sxs-lookup"><span data-stu-id="b7c47-132">**Password**</span></span>  
 <span data-ttu-id="b7c47-133">為資料庫連接指定密碼。</span><span class="sxs-lookup"><span data-stu-id="b7c47-133">Specify a password for the database connection.</span></span> <span data-ttu-id="b7c47-134">只有在您選擇使用 [SQL Server 驗證] 進行連接時，才能編輯此選項。</span><span class="sxs-lookup"><span data-stu-id="b7c47-134">This option is only editable if you have selected to connect using SQL Server Authentication.</span></span>  
  
 <span data-ttu-id="b7c47-135">**儲存密碼**</span><span class="sxs-lookup"><span data-stu-id="b7c47-135">**Save my password**</span></span>  
 <span data-ttu-id="b7c47-136">指定是否要儲存您在 **[密碼]** 方塊中輸入的密碼。</span><span class="sxs-lookup"><span data-stu-id="b7c47-136">Specify whether the password you have entered in the **Password** box is stored.</span></span> <span data-ttu-id="b7c47-137">只有在您選擇使用 [SQL Server 驗證] 進行連接時，才能使用此選項。</span><span class="sxs-lookup"><span data-stu-id="b7c47-137">This option is only available if you have selected to connect using SQL Server Authentication.</span></span>  
  
 <span data-ttu-id="b7c47-138">**資料庫名稱**</span><span class="sxs-lookup"><span data-stu-id="b7c47-138">**Database name**</span></span>  
 <span data-ttu-id="b7c47-139">從資料庫清單中選取資料庫。</span><span class="sxs-lookup"><span data-stu-id="b7c47-139">Select a database from the list of databases.</span></span>  
  
 <span data-ttu-id="b7c47-140">**進階**</span><span class="sxs-lookup"><span data-stu-id="b7c47-140">**Advanced**</span></span>  
 <span data-ttu-id="b7c47-141">使用 **[設定進階屬性]** 對話方塊設定其他連接屬性。</span><span class="sxs-lookup"><span data-stu-id="b7c47-141">Set additional connection properties by using the **Set Advanced Properties** dialog box.</span></span> <span data-ttu-id="b7c47-142">如需詳細資訊，請參閱[設定進階屬性 &#40;SSAS&#41;](set-advanced-properties-ssas.md)。</span><span class="sxs-lookup"><span data-stu-id="b7c47-142">For more information, see [Set Advanced Properties &#40;SSAS&#41;](set-advanced-properties-ssas.md).</span></span>  
  
 <span data-ttu-id="b7c47-143">**測試連接**</span><span class="sxs-lookup"><span data-stu-id="b7c47-143">**Test Connection**</span></span>  
 <span data-ttu-id="b7c47-144">嘗試使用目前的設定建立與資料來源之間的連接。</span><span class="sxs-lookup"><span data-stu-id="b7c47-144">Attempt to establish a connection to the data source using the current settings.</span></span> <span data-ttu-id="b7c47-145">顯示一則訊息，指出連接是否成功。</span><span class="sxs-lookup"><span data-stu-id="b7c47-145">A message is displayed indicating whether the connection is successful.</span></span>  
  
  
