---
title: 從物件總管連接到執行個體 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
ms.assetid: 9803a8a0-a8f1-4b65-87b8-989b06850194
author: stevestein
ms.author: sstein
ms.openlocfilehash: 918dd3ed6e8eb765f2cb7077107407c324c51a4b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584270"
---
# <a name="connect-to-an-instance-from-object-explorer"></a><span data-ttu-id="430b8-102">從物件總管連接到執行個體</span><span class="sxs-lookup"><span data-stu-id="430b8-102">Connect to an Instance From Object Explorer</span></span>
  <span data-ttu-id="430b8-103">若要使用物件總管管理物件，您必須先將物件總管連接到包含物件的執行個體。</span><span class="sxs-lookup"><span data-stu-id="430b8-103">To manage objects by using Object Explorer, you must first connect Object Explorer to the instance that contains the objects.</span></span> <span data-ttu-id="430b8-104">您可以同時將物件總管連接到多個執行個體。</span><span class="sxs-lookup"><span data-stu-id="430b8-104">You can connect Object Explorer to multiple instances at the same time.</span></span>  
  
## <a name="connecting-object-explorer-to-a-server"></a><span data-ttu-id="430b8-105">將物件總管連接到伺服器</span><span class="sxs-lookup"><span data-stu-id="430b8-105">Connecting Object Explorer to a Server</span></span>  
 <span data-ttu-id="430b8-106">若要使用物件總管，您必須先連接到伺服器。</span><span class="sxs-lookup"><span data-stu-id="430b8-106">To use Object Explorer you must first connect to a server.</span></span> <span data-ttu-id="430b8-107">請在物件總管工具列上，按一下 [連接]\*\*\*\*，再從下拉式清單中選取伺服器類型。</span><span class="sxs-lookup"><span data-stu-id="430b8-107">Click **Connect** on the Object Explorer toolbar and choose the type of server from the drop-down list.</span></span> <span data-ttu-id="430b8-108">[連接到伺服器] 對話方塊隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="430b8-108">The **Connect to Server** dialog box opens.</span></span> <span data-ttu-id="430b8-109">若要連接，您至少必須先提供伺服器名稱以及正確的驗證資訊。</span><span class="sxs-lookup"><span data-stu-id="430b8-109">To connect, you must provide at least the name of the server and the correct authentication information.</span></span>  
  
## <a name="optional-object-explorer-connection-settings"></a><span data-ttu-id="430b8-110">選擇性的物件總管連接設定</span><span class="sxs-lookup"><span data-stu-id="430b8-110">Optional Object Explorer Connection Settings</span></span>  
 <span data-ttu-id="430b8-111">當連接到伺服器時，您可以在 [連接到伺服器]\*\*\*\* 對話方塊中，指定其他連接資訊。</span><span class="sxs-lookup"><span data-stu-id="430b8-111">When connecting to a server, you can specify additional connection information in the **Connect to Server** dialog box.</span></span> <span data-ttu-id="430b8-112">[連接到伺服器]\*\*\*\* 對話方塊會保留上次使用的設定，新的連接 (例如新的程式碼編輯器視窗) 將會使用這些設定。</span><span class="sxs-lookup"><span data-stu-id="430b8-112">The **Connect to Server** dialog box will retain the last used settings, and new connections, such as new code editor windows, will use those settings.</span></span>  
  
 <span data-ttu-id="430b8-113">若要指定選擇性的連接設定，請遵照下列步驟：</span><span class="sxs-lookup"><span data-stu-id="430b8-113">To specify optional connection settings, follow these steps:</span></span>  
  
1.  <span data-ttu-id="430b8-114">在物件總管工具列上，按一下 [連接]\*\*\*\*，再按一下要連接的伺服器類型。</span><span class="sxs-lookup"><span data-stu-id="430b8-114">Click **Connect** on the Object Explorer toolbar, and click the type of server to connect to.</span></span> <span data-ttu-id="430b8-115">[連線到伺服器] 對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="430b8-115">The **Connect to Server** dialog box appears.</span></span>  
  
2.  <span data-ttu-id="430b8-116">在 [伺服器名稱]\*\*\*\* 方塊中，輸入您的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體的名稱。</span><span class="sxs-lookup"><span data-stu-id="430b8-116">In the **Server Name** box, type the name of your [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span>  
  
3.  <span data-ttu-id="430b8-117">按一下 [選項]。</span><span class="sxs-lookup"><span data-stu-id="430b8-117">Click **Options**.</span></span> <span data-ttu-id="430b8-118">此時 [連接到伺服器]\*\*\*\* 對話方塊會顯示其他選項。</span><span class="sxs-lookup"><span data-stu-id="430b8-118">The **Connect to Server** dialog box displays additional options.</span></span>  
  
4.  <span data-ttu-id="430b8-119">按一下 [連接屬性]\*\*\*\* 索引標籤來設定其他設定。</span><span class="sxs-lookup"><span data-stu-id="430b8-119">Click the **Connection Properties** tab to configure the additional settings.</span></span> <span data-ttu-id="430b8-120">可用的設定會隨著伺服器類型而不同。</span><span class="sxs-lookup"><span data-stu-id="430b8-120">The settings that are available vary depending upon the server type.</span></span> <span data-ttu-id="430b8-121">[!INCLUDE[ssDE](../../includes/ssde-md.md)]可以使用下列設定。</span><span class="sxs-lookup"><span data-stu-id="430b8-121">The following settings are available for the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
    |<span data-ttu-id="430b8-122">設定</span><span class="sxs-lookup"><span data-stu-id="430b8-122">Setting</span></span>|<span data-ttu-id="430b8-123">描述</span><span class="sxs-lookup"><span data-stu-id="430b8-123">Description</span></span>|  
    |-------------|-----------------|  
    |<span data-ttu-id="430b8-124">**連線到資料庫**</span><span class="sxs-lookup"><span data-stu-id="430b8-124">**Connect to database**</span></span>|<span data-ttu-id="430b8-125">從伺服器的可用資料庫中進行選擇。</span><span class="sxs-lookup"><span data-stu-id="430b8-125">Choose from the available databases on the server.</span></span> <span data-ttu-id="430b8-126">這份清單只會顯示您有權檢視的資料庫。</span><span class="sxs-lookup"><span data-stu-id="430b8-126">This list will only show databases that you have permission to view.</span></span>|  
    |<span data-ttu-id="430b8-127">**網路通訊協定**</span><span class="sxs-lookup"><span data-stu-id="430b8-127">**Network protocol**</span></span>|<span data-ttu-id="430b8-128">從 [共用記憶體]、[TCP/IP] 或 [具名管道] 中進行選取。</span><span class="sxs-lookup"><span data-stu-id="430b8-128">Select from Shared Memory, TCP/IP, or Named Pipes.</span></span>|  
    |<span data-ttu-id="430b8-129">**網路封包大小**</span><span class="sxs-lookup"><span data-stu-id="430b8-129">**Network packet size**</span></span>|<span data-ttu-id="430b8-130">以位元組為單位來進行設定。</span><span class="sxs-lookup"><span data-stu-id="430b8-130">Configure in bytes.</span></span> <span data-ttu-id="430b8-131">預設值是 4096 位元組。</span><span class="sxs-lookup"><span data-stu-id="430b8-131">The default setting is 4096 bytes.</span></span>|  
    |<span data-ttu-id="430b8-132">**連接逾時**</span><span class="sxs-lookup"><span data-stu-id="430b8-132">**Connection timeout**</span></span>|<span data-ttu-id="430b8-133">以秒為單位來進行設定。</span><span class="sxs-lookup"><span data-stu-id="430b8-133">Configure in seconds.</span></span> <span data-ttu-id="430b8-134">預設值是 15 秒。</span><span class="sxs-lookup"><span data-stu-id="430b8-134">The default setting is 15 seconds.</span></span>|  
    |<span data-ttu-id="430b8-135">**執行超時**</span><span class="sxs-lookup"><span data-stu-id="430b8-135">**Execution timeout**</span></span>|<span data-ttu-id="430b8-136">以秒為單位來進行設定。</span><span class="sxs-lookup"><span data-stu-id="430b8-136">Configure in seconds.</span></span> <span data-ttu-id="430b8-137">預設值 (0) 表示執行動作將永不逾時。</span><span class="sxs-lookup"><span data-stu-id="430b8-137">The default setting (0) indicates that execution will never time out.</span></span>|  
    |<span data-ttu-id="430b8-138">**加密連線**</span><span class="sxs-lookup"><span data-stu-id="430b8-138">**Encrypt connection**</span></span>|<span data-ttu-id="430b8-139">強制加密。</span><span class="sxs-lookup"><span data-stu-id="430b8-139">Forces encryption.</span></span>|  
  
5.  <span data-ttu-id="430b8-140">若要將指定的伺服器加入已註冊的伺服器清單中，請按一下 [已註冊的伺服器]\*\*\*\* 索引標籤，按一下新伺服器將出現的位置，再完成連接。</span><span class="sxs-lookup"><span data-stu-id="430b8-140">To add the specified server to your list of registered servers, click the **Registered Server** tab, click on the location where you want the new server to appear, and then complete the connection.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="430b8-141">使用 [其他連接參數]\*\*\*\* 頁面可將更多連接參數新增到連接字串。</span><span class="sxs-lookup"><span data-stu-id="430b8-141">Use the **Additional Connection Parameters** page to add more connection parameters to the connection string.</span></span> <span data-ttu-id="430b8-142">如需詳細資訊，請參閱[連接到伺服器 &#40;其他連接參數頁面&#41;](../../database-engine/connect-to-server-additional-connection-parameters-page.md)。</span><span class="sxs-lookup"><span data-stu-id="430b8-142">For more information, see [Connect to Server &#40;Additional Connection Parameters Page&#41;](../../database-engine/connect-to-server-additional-connection-parameters-page.md).</span></span>  
  
  
