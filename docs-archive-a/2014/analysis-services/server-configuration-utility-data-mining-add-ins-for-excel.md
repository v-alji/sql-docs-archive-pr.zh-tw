---
title: 適用于 Excel) 的 (資料採礦增益集的伺服器設定公用程式 |Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 28435f86-5cec-4a1e-9b7d-b2069c1ddddb
author: minewiskan
ms.author: owend
ms.openlocfilehash: f985338e44bf0f4b591fcb70a4e093901626149f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710870"
---
# <a name="server-configuration-utility-data-mining-add-ins-for-excel"></a><span data-ttu-id="12326-102">伺服器組態公用程式 (適用於 Excel 的資料採礦增益集)</span><span class="sxs-lookup"><span data-stu-id="12326-102">Server Configuration Utility (Data Mining Add-ins for Excel)</span></span>
  <span data-ttu-id="12326-103">當您安裝適用于 Excel 的資料採礦增益集時，也會一併安裝伺服器設定公用程式，而且會在您第一次開啟增益集時執行。本主題描述如何使用公用程式連接到的實例 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ，並設定資料庫以使用資料採礦模型。</span><span class="sxs-lookup"><span data-stu-id="12326-103">When you install the Data Mining Add-ins for Excel, a Server Configuration Utility is also installed, and will run the first time you open the add-ins. This topic describes how to use the utility to connect to an instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] and set up a database for working with data mining models.</span></span>  
  

  
##  <a name="step-1-connect-to-analysis-services"></a><a name="bkmk_step1"></a><span data-ttu-id="12326-104">步驟1：連接到 Analysis Services</span><span class="sxs-lookup"><span data-stu-id="12326-104">Step 1: Connect to Analysis Services</span></span>  
 <span data-ttu-id="12326-105">選擇提供資料採礦演算法並儲存資料採礦模型的 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 伺服器。</span><span class="sxs-lookup"><span data-stu-id="12326-105">Choose the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] server that provides the data mining algorithms and stores your data mining models.</span></span>  
  
 <span data-ttu-id="12326-106">當您建立啟用資料採礦的連接時，應該選擇可以試驗各種資料採礦模型的伺服器。</span><span class="sxs-lookup"><span data-stu-id="12326-106">When you create a connection to enable data mining, you should choose a server where you can experiment with data mining models.</span></span> <span data-ttu-id="12326-107">建議您在伺服器上建立新的資料庫，並且將其做為資料採礦專用的資料庫，或是請系統管理員為您準備資料採礦伺服器。</span><span class="sxs-lookup"><span data-stu-id="12326-107">We recommend that you create a new database on the server and dedicate the new database to data mining, or ask your administrator to prepare a data mining server for you.</span></span> <span data-ttu-id="12326-108">如此您就能在不影響其他服務之效能的情況下建立模型。</span><span class="sxs-lookup"><span data-stu-id="12326-108">That way you can build models without affecting the performance of other services.</span></span>  
  
 <span data-ttu-id="12326-109">請注意，用於資料採礦的 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 伺服器不需要與來源資料位於相同的伺服器上。</span><span class="sxs-lookup"><span data-stu-id="12326-109">Note that the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] server that you use for data mining does not need to be on the same server as your source data.</span></span>  
  
 <span data-ttu-id="12326-110">**伺服器名稱**</span><span class="sxs-lookup"><span data-stu-id="12326-110">**Server name**</span></span>  
 <span data-ttu-id="12326-111">輸入伺服器名稱，此伺服器包含將用於資料採礦的 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="12326-111">Type the name of the server that contains the instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] that you will use for data mining.</span></span>  
  
 <span data-ttu-id="12326-112">**驗證**</span><span class="sxs-lookup"><span data-stu-id="12326-112">**Authentication**</span></span>  
 <span data-ttu-id="12326-113">指定驗證方法。</span><span class="sxs-lookup"><span data-stu-id="12326-113">Specify the authentication methods.</span></span> <span data-ttu-id="12326-114">除非您的系統管理員已設定透過 HTTPPump 存取伺服器，否則需要使用 Windows 驗證才能連接到 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="12326-114">Windows Authentication is required for connections to [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], unless your administrator has configured access to the server via the HTTPPump.</span></span>  
  
##  <a name="step-2-allow-temporary-models"></a><a name="bkmk_step2"></a><span data-ttu-id="12326-115">步驟2：允許暫時模型</span><span class="sxs-lookup"><span data-stu-id="12326-115">Step 2: Allow Temporary Models</span></span>  
 <span data-ttu-id="12326-116">您必須先將 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 伺服器屬性變更為允許暫時性採礦模型，才能使用增益集。</span><span class="sxs-lookup"><span data-stu-id="12326-116">Before you can use the add-ins, an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] server property must be changed to permit the creation of temporary mining models.</span></span>  
  
 <span data-ttu-id="12326-117">暫時的採礦模型也稱為*會話模型*。</span><span class="sxs-lookup"><span data-stu-id="12326-117">Temporary mining models are also called *session models*.</span></span> <span data-ttu-id="12326-118">這是因為這些模型只能在您目前的工作階段開啟時儲存。</span><span class="sxs-lookup"><span data-stu-id="12326-118">This is because the models are stored only as long as your current session is open.</span></span> <span data-ttu-id="12326-119">當您關閉與伺服器的連接時，工作階段會結束，而工作階段期間所使用的任何模型都會遭到刪除。</span><span class="sxs-lookup"><span data-stu-id="12326-119">When you close your connection to the server, the session is ended and any models used during the session are deleted.</span></span>  
  
 <span data-ttu-id="12326-120">工作階段採礦模型的使用不會影響伺服器上的儲存空間，但與建立資料採礦模型相關的負擔可能會影響伺服器效能。</span><span class="sxs-lookup"><span data-stu-id="12326-120">The use of session mining models does not affect storage space on the server, but the overhead involved in creating data mining models may affect the performance of the server.</span></span>  
  
 <span data-ttu-id="12326-121">精靈首先會偵測您所指定之伺服器上的設定。</span><span class="sxs-lookup"><span data-stu-id="12326-121">The wizard first detects the settings on the server that you specified.</span></span> <span data-ttu-id="12326-122">如果伺服器已允許暫時性的採礦模型，您可以按 **[下一步]** 繼續進行。</span><span class="sxs-lookup"><span data-stu-id="12326-122">If the server already allows temporary mining models, you can click **Next** to continue.</span></span> <span data-ttu-id="12326-123">此精靈還提供如何在指定的 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 伺服器上啟用暫時性採礦模型的指示，或是如何對您的 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 系統管理員提出要求。</span><span class="sxs-lookup"><span data-stu-id="12326-123">The wizard also provides instructions for how to enable temporary mining models on the specified [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] server, or how to make a request to your [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] administrator.</span></span>  
  
##  <a name="step-3-create-database-for-add-in-users"></a><a name="bkmk_step3"></a><span data-ttu-id="12326-124">步驟3：為增益集使用者建立資料庫</span><span class="sxs-lookup"><span data-stu-id="12326-124">Step 3: Create Database for Add-in Users</span></span>  
 <span data-ttu-id="12326-125">在安裝和組態精靈的這個頁面上，您可以建立資料採礦專用的新資料庫，或選取現有的 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 資料庫。</span><span class="sxs-lookup"><span data-stu-id="12326-125">On this page of the setup and configuration wizard, you can create a new database that is dedicated to data mining, or select an existing [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="12326-126">資料採礦需要在多維度模式下執行的 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="12326-126">Data mining requires an instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] that is running in multidimensional mode.</span></span> <span data-ttu-id="12326-127">表格式模式不支援資料採礦。</span><span class="sxs-lookup"><span data-stu-id="12326-127">Tabular mode does not support data mining.</span></span>  
  
 <span data-ttu-id="12326-128">建議您建立資料採礦專用的個別資料庫。</span><span class="sxs-lookup"><span data-stu-id="12326-128">We recommend that you create a separate database dedicated to data mining.</span></span> <span data-ttu-id="12326-129">這可讓您試驗各種資料採礦模型，而不會影響其他方案物件。</span><span class="sxs-lookup"><span data-stu-id="12326-129">This lets you experiment with data mining models without affecting other solution objects.</span></span>  
  
 <span data-ttu-id="12326-130">如果您選擇 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 執行個體上現有的資料庫，請注意，如果您使用增益集建立模型，而已有該名稱的模型存在，則可能會覆寫現有的模型。</span><span class="sxs-lookup"><span data-stu-id="12326-130">If you choose an existing database on an instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], note that it is possible to overwrite existing models if you use the add-ins to create a model and a model of that name already exists.</span></span>  
  
 <span data-ttu-id="12326-131">**建立新的資料庫**</span><span class="sxs-lookup"><span data-stu-id="12326-131">**Create new database**</span></span>  
 <span data-ttu-id="12326-132">選取這個選項可在選取的伺服器上建立新的資料庫。</span><span class="sxs-lookup"><span data-stu-id="12326-132">Select this option to create a new database on the selected server.</span></span> <span data-ttu-id="12326-133">資料採礦資料庫將儲存您的資料來源、採礦結構和採礦模型。</span><span class="sxs-lookup"><span data-stu-id="12326-133">A data mining database will store your data sources, mining structures, and mining models.</span></span>  
  
 <span data-ttu-id="12326-134">**資料庫名稱**</span><span class="sxs-lookup"><span data-stu-id="12326-134">**Database name**</span></span>  
 <span data-ttu-id="12326-135">輸入新資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="12326-135">Type the name of the new database.</span></span> <span data-ttu-id="12326-136">如果此名稱尚未使用，則會自動建立。</span><span class="sxs-lookup"><span data-stu-id="12326-136">If the name is not already in use, it will be created for you.</span></span>  
  
 <span data-ttu-id="12326-137">**使用現有的資料庫**</span><span class="sxs-lookup"><span data-stu-id="12326-137">**Use existing database**</span></span>  
 <span data-ttu-id="12326-138">選取此選項可使用現有的 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 資料庫。</span><span class="sxs-lookup"><span data-stu-id="12326-138">Select this option to use an existing [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database.</span></span>  
  
 <span data-ttu-id="12326-139">**Database**</span><span class="sxs-lookup"><span data-stu-id="12326-139">**Database**</span></span>  
 <span data-ttu-id="12326-140">如果您已選擇此選項使用現有的資料庫，則必須從清單中選取資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="12326-140">If you chose the option to use an existing database, you must select the database name from the list.</span></span>  
  
##  <a name="step-4-give-add-in-users-appropriate-permissions"></a><a name="bkmk_step4"></a><span data-ttu-id="12326-141">步驟4：授與增益集使用者適當的許可權</span><span class="sxs-lookup"><span data-stu-id="12326-141">Step 4: Give Add-in Users Appropriate Permissions</span></span>  
 <span data-ttu-id="12326-142">您必須確定您 (和增益集的其他使用者) 必須具有必要的權限，才能瀏覽、編輯、處理或建立資料採礦結構和模型。</span><span class="sxs-lookup"><span data-stu-id="12326-142">You must ensure that you (and any other users of the add-ins) have the necessary permissions to browse, edit, process, or create data mining structures and models.</span></span>  
  
 <span data-ttu-id="12326-143">根據預設，使用增益集需要有整合式 Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="12326-143">By default, integrated Windows Authentication is required to use the add-ins.</span></span>  
  
 <span data-ttu-id="12326-144">**授與增益集使用者資料庫管理權限**</span><span class="sxs-lookup"><span data-stu-id="12326-144">**Give add-in users database administration permissions**</span></span>  
 <span data-ttu-id="12326-145">選取此選項，為列出的使用者提供資料庫的管理權限。</span><span class="sxs-lookup"><span data-stu-id="12326-145">Select this option to give the listed users administrative access to the database.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="12326-146">這些許可權僅適用于 [**資料庫名稱**] 方塊中所列的資料庫。</span><span class="sxs-lookup"><span data-stu-id="12326-146">These permissions apply only to the database listed in the **Database name** box.</span></span>  
  
 <span data-ttu-id="12326-147">**資料庫名稱**</span><span class="sxs-lookup"><span data-stu-id="12326-147">**Database name**</span></span>  
 <span data-ttu-id="12326-148">顯示選取之資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="12326-148">Displays the name of the selected database.</span></span>  
  
 <span data-ttu-id="12326-149">**指定要加入的使用者或群組**</span><span class="sxs-lookup"><span data-stu-id="12326-149">**Specify users or groups to add**</span></span>  
 <span data-ttu-id="12326-150">選取將可存取用於資料採礦之資料庫的登入帳戶。</span><span class="sxs-lookup"><span data-stu-id="12326-150">Select the logins that will have access to the database used for data mining.</span></span>  
  
 <span data-ttu-id="12326-151">**加入**</span><span class="sxs-lookup"><span data-stu-id="12326-151">**Add**</span></span>  
 <span data-ttu-id="12326-152">按一下此選項，開啟對話方塊並加入使用者或群組。</span><span class="sxs-lookup"><span data-stu-id="12326-152">Click to open a dialog box and add users or groups.</span></span>  
  
 <span data-ttu-id="12326-153">**移除**</span><span class="sxs-lookup"><span data-stu-id="12326-153">**Remove**</span></span>  
 <span data-ttu-id="12326-154">按一下此選項，從使用者清單中移除具有管理權限的使用者或群組。</span><span class="sxs-lookup"><span data-stu-id="12326-154">Click to remove the selected user or group from the list of users with administration permissions.</span></span>  
  
  
