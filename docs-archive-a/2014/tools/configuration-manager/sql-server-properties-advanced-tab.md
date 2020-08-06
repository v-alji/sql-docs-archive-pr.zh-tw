---
title: SQL Server 屬性 (進階索引標籤) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: 2ffd10fd-bac1-478f-9cff-96ed6c8b787f
author: stevestein
ms.author: sstein
ms.openlocfilehash: a9a77fd0a43627b49bb8719f6fa943408f64fcca
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584929"
---
# <a name="sql-server-properties-advanced-tab"></a><span data-ttu-id="961b1-102">SQL Server 屬性 (進階索引標籤)</span><span class="sxs-lookup"><span data-stu-id="961b1-102">SQL Server Properties (Advanced Tab)</span></span>
  <span data-ttu-id="961b1-103">下列屬性預設會出現在 **[進階]** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="961b1-103">The following properties appear on the **Advanced** tab by default.</span></span> <span data-ttu-id="961b1-104">如果定義了自訂屬性，這些屬性與其值也會在這個索引標籤上顯示。</span><span class="sxs-lookup"><span data-stu-id="961b1-104">If custom properties are defined, they also appear on this tab, with their values.</span></span>  
  
## <a name="options"></a><span data-ttu-id="961b1-105">選項。</span><span class="sxs-lookup"><span data-stu-id="961b1-105">Options</span></span>  
 <span data-ttu-id="961b1-106">**叢集**</span><span class="sxs-lookup"><span data-stu-id="961b1-106">**Clustered**</span></span>  
 <span data-ttu-id="961b1-107">指出這項服務是否安裝為叢集伺服器的資源。</span><span class="sxs-lookup"><span data-stu-id="961b1-107">Indicates if this service is installed as a resource of a clustered server.</span></span>  
  
 <span data-ttu-id="961b1-108">**客戶回函報表**</span><span class="sxs-lookup"><span data-stu-id="961b1-108">**Customer Feedback Reporting**</span></span>  
 <span data-ttu-id="961b1-109">指出是否已在這項服務上啟用「服務品質監控」。</span><span class="sxs-lookup"><span data-stu-id="961b1-109">Indicates whether Service Quality Monitoring has been enabled on this service.</span></span> <span data-ttu-id="961b1-110">如需有關客戶回函報表的詳細資訊，請搜尋「線上叢書」的＜錯誤報告和使用方式報告設定＞主題。</span><span class="sxs-lookup"><span data-stu-id="961b1-110">For more information on Customer Feedback Reporting, search Books Online for the topic, "Error and Usage Report Settings."</span></span>  
  
 <span data-ttu-id="961b1-111">**資料路徑**</span><span class="sxs-lookup"><span data-stu-id="961b1-111">**Data Path**</span></span>  
 <span data-ttu-id="961b1-112">顯示這個 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安裝之 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]二進位編碼檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="961b1-112">Displays the path to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] binaries for this installation of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="961b1-113">**傾印目錄**</span><span class="sxs-lookup"><span data-stu-id="961b1-113">**Dump Directory**</span></span>  
 <span data-ttu-id="961b1-114">顯示在發生錯誤時放置記憶體傾印的位置。</span><span class="sxs-lookup"><span data-stu-id="961b1-114">Displays the location where memory dumps are placed in case of an error.</span></span>  
  
 <span data-ttu-id="961b1-115">**錯誤報告**</span><span class="sxs-lookup"><span data-stu-id="961b1-115">**Error Reporting**</span></span>  
 <span data-ttu-id="961b1-116">若設定為 [是]  ，一旦發生嚴重錯誤，Dr. Watson 程式會將資訊轉送至 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 或您的錯誤伺服器。</span><span class="sxs-lookup"><span data-stu-id="961b1-116">When set to **Yes**, the Dr. Watson program forwards information to either [!INCLUDE[msCoName](../../includes/msconame-md.md)] or your error server if a serious failure occurs.</span></span> <span data-ttu-id="961b1-117">如需錯誤報表的詳細資訊，請搜尋《線上叢書》的＜錯誤報告和使用方式報告設定＞主題。</span><span class="sxs-lookup"><span data-stu-id="961b1-117">For more information on Error Reporting, search Books Online for the topic, "Error and Usage Report Settings."</span></span> <span data-ttu-id="961b1-118">若要變更此值，請在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 物件總管中，在伺服器上按一下滑鼠右鍵，然後依序按一下 [屬性]  **和 [其他伺服器設定]** 頁面。</span><span class="sxs-lookup"><span data-stu-id="961b1-118">To change this value, in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] Object Explorer, right-click your server, click **Properties**, and then click the **Misc. Server Settings** page.</span></span> <span data-ttu-id="961b1-119">這個選項會出現在 **[資訊報告]** 區域中。</span><span class="sxs-lookup"><span data-stu-id="961b1-119">The options are presented in the **Information Reporting** area.</span></span>  
  
 <span data-ttu-id="961b1-120">**檔案版本**</span><span class="sxs-lookup"><span data-stu-id="961b1-120">**File Version**</span></span>  
 <span data-ttu-id="961b1-121">顯示 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 可執行檔的版本。</span><span class="sxs-lookup"><span data-stu-id="961b1-121">Displays the version of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] executable.</span></span>  
  
 <span data-ttu-id="961b1-122">**安裝路徑**</span><span class="sxs-lookup"><span data-stu-id="961b1-122">**Install Path**</span></span>  
 <span data-ttu-id="961b1-123">顯示這個 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安裝之 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]二進位編碼檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="961b1-123">Displays the path to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] binaries for this installation of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="961b1-124">**執行個體識別碼**</span><span class="sxs-lookup"><span data-stu-id="961b1-124">**Instance ID**</span></span>  
 <span data-ttu-id="961b1-125">指出使用此服務的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="961b1-125">Indicates the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance that used this service.</span></span>  
  
 <span data-ttu-id="961b1-126">**語言**</span><span class="sxs-lookup"><span data-stu-id="961b1-126">**Language**</span></span>  
 <span data-ttu-id="961b1-127">顯示伺服器訊息的預設語言。</span><span class="sxs-lookup"><span data-stu-id="961b1-127">Displays the default language for server messages.</span></span>  
  
 <span data-ttu-id="961b1-128">**登錄根目錄**</span><span class="sxs-lookup"><span data-stu-id="961b1-128">**Registry Root**</span></span>  
 <span data-ttu-id="961b1-129">顯示此應用程式使用之登錄機碼的位置。</span><span class="sxs-lookup"><span data-stu-id="961b1-129">Displays the location of the registry keys used by this application.</span></span>  
  
 <span data-ttu-id="961b1-130">**Service Pack 層級**</span><span class="sxs-lookup"><span data-stu-id="961b1-130">**Service Pack Level**</span></span>  
 <span data-ttu-id="961b1-131">顯示這個 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]執行個體的 Service Pack 層級。</span><span class="sxs-lookup"><span data-stu-id="961b1-131">Displays the service pack level of this instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="961b1-132">**SKU 名稱**</span><span class="sxs-lookup"><span data-stu-id="961b1-132">**SKU Name**</span></span>  
 <span data-ttu-id="961b1-133">顯示產品存貨保持單元 (SKU)，有時也稱作產品版本 (product edition)。</span><span class="sxs-lookup"><span data-stu-id="961b1-133">Displays the product stock keeping unit (SKU), sometimes called the product edition.</span></span>  
  
 <span data-ttu-id="961b1-134">**啟動參數**</span><span class="sxs-lookup"><span data-stu-id="961b1-134">**Startup Parameters**</span></span>  
 <span data-ttu-id="961b1-135">列出這個 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]執行個體所使用的任何啟動參數。</span><span class="sxs-lookup"><span data-stu-id="961b1-135">Lists any startup parameters that are used by this instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="961b1-136">參數是由分號區隔開來的。</span><span class="sxs-lookup"><span data-stu-id="961b1-136">Parameters are separated by semi-colons.</span></span> <span data-ttu-id="961b1-137">預設的參數包含 master 資料庫 (`master.mdf`)、master 資料庫的記錄檔 (`mastlog.ldf`) 以及錯誤記錄檔的資料檔案路徑。</span><span class="sxs-lookup"><span data-stu-id="961b1-137">The default parameters include the paths to the data file for the master database (`master.mdf`), the log file for the master database (`mastlog.ldf`), and the error log file.</span></span> <span data-ttu-id="961b1-138">如需啟動參數的語法，請搜尋《線上叢書》的 **＜使用 SQL 伺服器啟動選項＞**主題。</span><span class="sxs-lookup"><span data-stu-id="961b1-138">For the syntax of startup parameters, search Books Online for the topic **Using the SQL Server Service Startup Options.**</span></span>  
  
 <span data-ttu-id="961b1-139">**存貨保持單元**</span><span class="sxs-lookup"><span data-stu-id="961b1-139">**Stock Keeping Unit**</span></span>  
 <span data-ttu-id="961b1-140">顯示產品存貨保持單元 (SKU) 號碼。</span><span class="sxs-lookup"><span data-stu-id="961b1-140">Displays the product stock keeping unit (SKU) number.</span></span>  
  
 <span data-ttu-id="961b1-141">**版本**</span><span class="sxs-lookup"><span data-stu-id="961b1-141">**Version**</span></span>  
 <span data-ttu-id="961b1-142">顯示這個 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]執行個體的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="961b1-142">Displays the version number of this instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="961b1-143">**虛擬伺服器名稱**</span><span class="sxs-lookup"><span data-stu-id="961b1-143">**Virtual Server Name**</span></span>  
 <span data-ttu-id="961b1-144">當**安裝在叢集伺服器時的** 虛擬伺服器名稱 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="961b1-144">**Virtual Server Name** when [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is installed on a clustered server.</span></span>  
  
  
