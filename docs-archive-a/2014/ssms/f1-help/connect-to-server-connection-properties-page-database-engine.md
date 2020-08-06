---
title: 連接到伺服器 (連接屬性頁面) 資料庫引擎 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.swb.connecttosqlserver.connectionproperties.f1
ms.assetid: edc1143c-6a47-4b02-92ab-441bdea8ea8a
author: stevestein
ms.author: sstein
ms.openlocfilehash: 41f2aa3fd5004a371515ee5d8905c7bb73699829
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706930"
---
# <a name="connect-to-server-connection-properties-page-database-engine"></a><span data-ttu-id="f9dbf-102">連接到伺服器 (連接屬性頁面) Database Engine</span><span class="sxs-lookup"><span data-stu-id="f9dbf-102">Connect to Server (Connection Properties Page) Database Engine</span></span>
  <span data-ttu-id="f9dbf-103">當您連接到 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 執行個體或在 [已註冊的伺服器]  中註冊 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 時，請使用這個索引標籤來檢視或指定選項。</span><span class="sxs-lookup"><span data-stu-id="f9dbf-103">Use this tab to view or specify options when connecting to an instance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] or registering [!INCLUDE[ssDE](../../includes/ssde-md.md)] in **Registered Servers**.</span></span> <span data-ttu-id="f9dbf-104">連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 執行個體時，[連接]  和 [選項]  才會出現在這個對話方塊中。</span><span class="sxs-lookup"><span data-stu-id="f9dbf-104">**Connect** and **Options** only appear in this dialog box when connecting to an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span> <span data-ttu-id="f9dbf-105">註冊 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 時，[測試]  和 [儲存]  才會出現在這個對話方塊中。</span><span class="sxs-lookup"><span data-stu-id="f9dbf-105">**Test** and **Save** only appear in this dialog box when registering [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
## <a name="options"></a><span data-ttu-id="f9dbf-106">選項</span><span class="sxs-lookup"><span data-stu-id="f9dbf-106">Options</span></span>  
 <span data-ttu-id="f9dbf-107">**連線到資料庫**</span><span class="sxs-lookup"><span data-stu-id="f9dbf-107">**Connect to database**</span></span>  
 <span data-ttu-id="f9dbf-108">從清單中選取要連接的資料庫。</span><span class="sxs-lookup"><span data-stu-id="f9dbf-108">Select a database to connect to from the list.</span></span> <span data-ttu-id="f9dbf-109">如果您選取 **\<default>** ，您將會連接到伺服器的預設資料庫。</span><span class="sxs-lookup"><span data-stu-id="f9dbf-109">If you select **\<default>**, you will be connected to the default database for the server.</span></span> <span data-ttu-id="f9dbf-110">如果您選取 **\<Browse server>** ，您可以流覽伺服器，尋找要連接的資料庫。</span><span class="sxs-lookup"><span data-stu-id="f9dbf-110">If you select **\<Browse server>**, you can browse the server for the database to which to connect.</span></span>  
  
 <span data-ttu-id="f9dbf-111">當您透過 [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] 連接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Database Engine 執行個體時，您必須使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 驗證，並在 [連接到伺服器]  對話方塊的 [連接屬性]  索引標籤上指定資料庫。請務必選取 [加密連接]  核取方塊。</span><span class="sxs-lookup"><span data-stu-id="f9dbf-111">When connecting to an instance of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Database Engine through [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)], you must use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication and specify a database in the **Connect to Server** dialog box, on the **Connection Properties** tab. Ensure that you select the **Encrypt connection** checkbox.</span></span>  
  
 <span data-ttu-id="f9dbf-112">根據預設， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 會連接到 **master**。</span><span class="sxs-lookup"><span data-stu-id="f9dbf-112">By default, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connects to **master**.</span></span> <span data-ttu-id="f9dbf-113">如果您指定使用者資料庫，您只會在物件總管中看到該資料庫與其物件。</span><span class="sxs-lookup"><span data-stu-id="f9dbf-113">If you specify a user database, you will only see that database and its objects in Object Explorer.</span></span> <span data-ttu-id="f9dbf-114">如果您連接到 **master**，您將能夠看到所有資料庫。</span><span class="sxs-lookup"><span data-stu-id="f9dbf-114">If you connect to **master**, you will be able to see all databases.</span></span> <span data-ttu-id="f9dbf-115">如需詳細資訊，請參閱[Azure SQL Database 總覽](/azure/sql-database/sql-database-technical-overview)。</span><span class="sxs-lookup"><span data-stu-id="f9dbf-115">For more information, see the [Azure SQL Database Overview](/azure/sql-database/sql-database-technical-overview).</span></span>  
  
 <span data-ttu-id="f9dbf-116">**網路通訊協定**</span><span class="sxs-lookup"><span data-stu-id="f9dbf-116">**Network protocol**</span></span>  
 <span data-ttu-id="f9dbf-117">從清單中選取通訊協定。</span><span class="sxs-lookup"><span data-stu-id="f9dbf-117">Select a protocol from the list.</span></span> <span data-ttu-id="f9dbf-118">可用的用戶端通訊協定就是您在 [電腦管理] 中使用 [用戶端網路組態] 所設定的通訊協定。</span><span class="sxs-lookup"><span data-stu-id="f9dbf-118">The available client protocols are those that you configured using the Client Network Configuration in Computer Management.</span></span>  
  
 <span data-ttu-id="f9dbf-119">**網路封包大小**</span><span class="sxs-lookup"><span data-stu-id="f9dbf-119">**Network packet size**</span></span>  
 <span data-ttu-id="f9dbf-120">輸入要傳送之網路封包的大小。</span><span class="sxs-lookup"><span data-stu-id="f9dbf-120">Enter the size of the network packets to be sent.</span></span> <span data-ttu-id="f9dbf-121">預設值是 4096 個位元組。</span><span class="sxs-lookup"><span data-stu-id="f9dbf-121">The default is 4096 bytes.</span></span>  
  
 <span data-ttu-id="f9dbf-122">**連接逾時**</span><span class="sxs-lookup"><span data-stu-id="f9dbf-122">**Connection timeout**</span></span>  
 <span data-ttu-id="f9dbf-123">輸入在超時之前，等候連線建立的秒數。預設值為15秒。</span><span class="sxs-lookup"><span data-stu-id="f9dbf-123">Enter the number of seconds to wait for a connection to be established before timing out. The default value is 15 seconds.</span></span>  
  
 <span data-ttu-id="f9dbf-124">**執行超時**</span><span class="sxs-lookup"><span data-stu-id="f9dbf-124">**Execution timeout**</span></span>  
 <span data-ttu-id="f9dbf-125">輸入在伺服器上執行的工作完成之前，所要等候的時間 (以秒為單位)。</span><span class="sxs-lookup"><span data-stu-id="f9dbf-125">Enter the amount of time in seconds to wait before execution of a task is completed on the server.</span></span> <span data-ttu-id="f9dbf-126">預設值為零秒，此值會指出沒有逾時。</span><span class="sxs-lookup"><span data-stu-id="f9dbf-126">The default value is zero seconds, which indicates there is no time-out.</span></span>  
  
 <span data-ttu-id="f9dbf-127">**加密連線**</span><span class="sxs-lookup"><span data-stu-id="f9dbf-127">**Encrypt connection**</span></span>  
 <span data-ttu-id="f9dbf-128">強制連接的加密。</span><span class="sxs-lookup"><span data-stu-id="f9dbf-128">Forces encryption of the connection.</span></span>  
  
 <span data-ttu-id="f9dbf-129">**使用自訂色彩**</span><span class="sxs-lookup"><span data-stu-id="f9dbf-129">**Use custom color**</span></span>  
 <span data-ttu-id="f9dbf-130">選取此選項可在 [!INCLUDE[ssDE](../../includes/ssde-md.md)] [查詢編輯器] 視窗中指定狀態列的背景色彩。</span><span class="sxs-lookup"><span data-stu-id="f9dbf-130">Select to specify the background color for the status bar in a [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor window.</span></span> <span data-ttu-id="f9dbf-131">若要指定色彩，請按一下 [選取]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f9dbf-131">To specify the color, click **Select**.</span></span> <span data-ttu-id="f9dbf-132">在 [色彩]\*\*\*\* 對話方塊中，從 [基本色彩]\*\*\*\* 方格選取預先定義的色彩，或是按一下 [定義自訂色彩]\*\*\*\* 來定義及使用自訂色彩。</span><span class="sxs-lookup"><span data-stu-id="f9dbf-132">In the **Color** dialog box, select a predefined color from the **Basic Colors** grid or click **Define Custom Colors** to define and use a custom color.</span></span>  
  
-   <span data-ttu-id="f9dbf-133">當您在 [物件總管]\*\*\*\* 窗格內指定伺服器項目的色彩時，該色彩會在開啟 [查詢編輯器] 視窗時使用。</span><span class="sxs-lookup"><span data-stu-id="f9dbf-133">When you specify a color for a server entry in the **Object Explorer** pane, that color is used when you open a Query Editor window.</span></span> <span data-ttu-id="f9dbf-134">若要開啟 [查詢編輯器] 視窗，請以滑鼠右鍵按一下伺服器項目並選取 [新增查詢]\*\*\*\*，或是在 [物件總管]\*\*\*\* 窗格為使用中而且在此伺服器上為焦點所在時，按一下工具列上的 [新增查詢]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f9dbf-134">To open a Query Editor window, either right-click the server entry and select **New Query**; or, when the **Object Explorer** pane is active and focused on this server, click **New Query** on the toolbar.</span></span>  
  
-   <span data-ttu-id="f9dbf-135">當您在 [已註冊的伺服器]\*\*\*\* 窗格內指定伺服器項目的色彩時，該色彩會在開啟 [查詢編輯器] 視窗時使用。</span><span class="sxs-lookup"><span data-stu-id="f9dbf-135">When you specify a color for a server entry in the **Registered Servers** pane, that color is used when you open a Query Editor window.</span></span> <span data-ttu-id="f9dbf-136">若要開啟 [查詢編輯器] 視窗，請以滑鼠右鍵按一下伺服器項目並選取 [新增查詢]\*\*\*\*，或是在 [已註冊的伺服器]\*\*\*\* 窗格為使用中而且在此伺服器上為焦點所在時，按一下工具列上的 [新增查詢]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f9dbf-136">To open a Query Editor window, either right-click the server entry and select **New Query**; or, when the **Registered Server** pane is active and focused on this server, click **New Query** on the toolbar.</span></span>  
  
-   <span data-ttu-id="f9dbf-137">在 [檔案]\*\*\*\* 功能表上，當您按一下 [新增]\*\*\*\* 然後按一下 [Database Engine 查詢]\*\*\*\* 時，您在 [連接到伺服器]\*\*\*\* 對話方塊內指定的色彩會套用到 [查詢編輯器] 視窗。</span><span class="sxs-lookup"><span data-stu-id="f9dbf-137">On the **File** menu, when you click **New** and then **Database Engine Query**, the color you that you specify in the **Connect to Server** dialog box applies to that Query Editor window.</span></span>  
  
 <span data-ttu-id="f9dbf-138">**全部重設**</span><span class="sxs-lookup"><span data-stu-id="f9dbf-138">**Reset All**</span></span>  
 <span data-ttu-id="f9dbf-139">將所有手動輸入的連接屬性值取代成預設值。</span><span class="sxs-lookup"><span data-stu-id="f9dbf-139">Replace all manually entered connection property values with their defaults.</span></span>  
  
 <span data-ttu-id="f9dbf-140">**[連接]**</span><span class="sxs-lookup"><span data-stu-id="f9dbf-140">**Connect**</span></span>  
 <span data-ttu-id="f9dbf-141">使用列出的值嘗試進行連接。</span><span class="sxs-lookup"><span data-stu-id="f9dbf-141">Attempt a connection using the listed values.</span></span>  
  
 <span data-ttu-id="f9dbf-142">**選項**</span><span class="sxs-lookup"><span data-stu-id="f9dbf-142">**Options**</span></span>  
 <span data-ttu-id="f9dbf-143">按一下即可變更對話方塊，並隱藏其他伺服器連接選項，例如記住密碼。</span><span class="sxs-lookup"><span data-stu-id="f9dbf-143">Click to change the dialog box and hide the additional server connection options, such as remembering the password.</span></span>  
  
 <span data-ttu-id="f9dbf-144">**Test**</span><span class="sxs-lookup"><span data-stu-id="f9dbf-144">**Test**</span></span>  
 <span data-ttu-id="f9dbf-145">在 [已註冊的伺服器]\*\*\*\* 中註冊 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 時，請按一下以測試連接。</span><span class="sxs-lookup"><span data-stu-id="f9dbf-145">When registering [!INCLUDE[ssDE](../../includes/ssde-md.md)] in **Registered Servers**, click to test the connection.</span></span>  
  
 <span data-ttu-id="f9dbf-146">**儲存**</span><span class="sxs-lookup"><span data-stu-id="f9dbf-146">**Save**</span></span>  
 <span data-ttu-id="f9dbf-147">儲存 [已註冊的伺服器]\*\*\*\* 中的設定。</span><span class="sxs-lookup"><span data-stu-id="f9dbf-147">Saves the settings in **Registered Servers**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9dbf-148">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f9dbf-148">See Also</span></span>  
 [<span data-ttu-id="f9dbf-149">連接屬性對話方塊</span><span class="sxs-lookup"><span data-stu-id="f9dbf-149">Connection Properties Dialog Box</span></span>](../../database-engine/connection-properties-dialog-box.md)  
  
  
