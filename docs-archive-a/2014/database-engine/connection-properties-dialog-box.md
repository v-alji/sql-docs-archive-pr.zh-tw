---
title: 連接屬性對話方塊 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.connectionproperties.f1
helpviewer_keywords:
- Connection Properties dialog box
ms.assetid: 6df812ad-4d80-4503-8a23-47719ce85624
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: db2817ebaf3f1655f146c060fcb79d550ad0cc8b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707806"
---
# <a name="connection-properties-dialog-box"></a><span data-ttu-id="01cb7-102">連接屬性對話方塊</span><span class="sxs-lookup"><span data-stu-id="01cb7-102">Connection Properties Dialog Box</span></span>
  <span data-ttu-id="01cb7-103">使用此對話方塊來檢視目前的連接屬性。</span><span class="sxs-lookup"><span data-stu-id="01cb7-103">Use this dialog box to view the current connection properties.</span></span> <span data-ttu-id="01cb7-104">當您在各個物件總管對話方塊中按一下 [檢視連接屬性]\*\*\*\*，就會出現此對話方塊。</span><span class="sxs-lookup"><span data-stu-id="01cb7-104">This dialog box is available when you click **View connection properties** in various Object Explorer dialog boxes.</span></span> <span data-ttu-id="01cb7-105">此頁面上顯示的屬性是唯讀的。</span><span class="sxs-lookup"><span data-stu-id="01cb7-105">The properties displayed on this page are read-only.</span></span>  
  
 <span data-ttu-id="01cb7-106">若要變更屬性 (例如 [資料庫]\*\*\*\*)，請在開啟 [連接屬性]\*\*\*\* 對話方塊之前，先使用物件總管連接到想要的資料庫。</span><span class="sxs-lookup"><span data-stu-id="01cb7-106">To change properties such as **Database**, connect to the desired database with Object Explorer before opening the **Connection Properties** dialog box.</span></span>  
  
 <span data-ttu-id="01cb7-107">請注意，SQL Azure 的查詢逾時期限是 30 分鐘。</span><span class="sxs-lookup"><span data-stu-id="01cb7-107">Note that the query time-out period for SQL Azure is 30 minutes.</span></span>  
  
## <a name="authentication"></a><span data-ttu-id="01cb7-108">驗證</span><span class="sxs-lookup"><span data-stu-id="01cb7-108">Authentication</span></span>  
 <span data-ttu-id="01cb7-109">檢視目前連接的驗證屬性。</span><span class="sxs-lookup"><span data-stu-id="01cb7-109">View authentication properties for the current connection.</span></span> <span data-ttu-id="01cb7-110">驗證屬性是建立連接時的登入和驗證方法。</span><span class="sxs-lookup"><span data-stu-id="01cb7-110">Authentication properties are the login and authentication method when the connection was established.</span></span> <span data-ttu-id="01cb7-111">若要變更驗證屬性，請中斷與的連接 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ，然後使用所需的連線選項，再次將物件總管連接到伺服器。</span><span class="sxs-lookup"><span data-stu-id="01cb7-111">To change the authentication properties, disconnect from [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], and then connect Object Explorer to the server again, using the desired connection options.</span></span>  
  
 <span data-ttu-id="01cb7-112">**驗證方法**</span><span class="sxs-lookup"><span data-stu-id="01cb7-112">**Authentication Method**</span></span>  
 <span data-ttu-id="01cb7-113">目前連接所使用的驗證方法。</span><span class="sxs-lookup"><span data-stu-id="01cb7-113">The authentication method used for the current connection.</span></span>  
  
 <span data-ttu-id="01cb7-114">**使用者名稱**</span><span class="sxs-lookup"><span data-stu-id="01cb7-114">**User Name**</span></span>  
 <span data-ttu-id="01cb7-115">用於連接驗證之登入的使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="01cb7-115">The name of the user of login used for the connection authentication.</span></span>  
  
## <a name="connection-category"></a><span data-ttu-id="01cb7-116">連接類別目錄</span><span class="sxs-lookup"><span data-stu-id="01cb7-116">Connection Category</span></span>  
 <span data-ttu-id="01cb7-117">檢視目前連接的連接屬性。</span><span class="sxs-lookup"><span data-stu-id="01cb7-117">View connection properties for the current connection.</span></span> <span data-ttu-id="01cb7-118">在連接處理期間，大部份的連接屬性都已在 [連接到伺服器]\*\*\*\* 對話方塊的 [連接屬性]\*\*\*\* 索引標籤上選取。</span><span class="sxs-lookup"><span data-stu-id="01cb7-118">Most connection properties were selected on the **Connection Properties** tab of the **Connect to server** dialog box during the connection process.</span></span>  
  
 <span data-ttu-id="01cb7-119">**Database**</span><span class="sxs-lookup"><span data-stu-id="01cb7-119">**Database**</span></span>  
 <span data-ttu-id="01cb7-120">目前連接的資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="01cb7-120">The name of the database currently connected to.</span></span> <span data-ttu-id="01cb7-121">若要變更此設定，請使用 SQL 編輯器工具列。</span><span class="sxs-lookup"><span data-stu-id="01cb7-121">To change this use, the SQL Editor toolbar.</span></span>  
  
 <span data-ttu-id="01cb7-122">**SPID**</span><span class="sxs-lookup"><span data-stu-id="01cb7-122">**SPID**</span></span>  
 <span data-ttu-id="01cb7-123">伺服器指派給連接的系統處理序識別碼。</span><span class="sxs-lookup"><span data-stu-id="01cb7-123">The system process ID assigned by the server to the connection.</span></span> <span data-ttu-id="01cb7-124">此連接的這項設定無法變更。</span><span class="sxs-lookup"><span data-stu-id="01cb7-124">This cannot be changed for this connection.</span></span>  
  
 <span data-ttu-id="01cb7-125">**網路通訊協定**</span><span class="sxs-lookup"><span data-stu-id="01cb7-125">**Network Protocol**</span></span>  
 <span data-ttu-id="01cb7-126">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 連接的網路通訊協定。</span><span class="sxs-lookup"><span data-stu-id="01cb7-126">The network protocol of the [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] connection.</span></span> <span data-ttu-id="01cb7-127">若要變更這項設定，請使用所要的連接屬性重新連接。</span><span class="sxs-lookup"><span data-stu-id="01cb7-127">To change this, connect again with the desired connection properties.</span></span>  
  
 <span data-ttu-id="01cb7-128">**網路封包大小**</span><span class="sxs-lookup"><span data-stu-id="01cb7-128">**Network Packet Size**</span></span>  
 <span data-ttu-id="01cb7-129">與伺服器通訊時使用的封包大小。</span><span class="sxs-lookup"><span data-stu-id="01cb7-129">The packet size used when communicating with the server.</span></span> <span data-ttu-id="01cb7-130">若要變更這項設定，請使用所要的連接屬性重新連接。</span><span class="sxs-lookup"><span data-stu-id="01cb7-130">To change this, connect again with the desired connection properties.</span></span>  
  
 <span data-ttu-id="01cb7-131">**連接逾時**</span><span class="sxs-lookup"><span data-stu-id="01cb7-131">**Connection Timeout**</span></span>  
 <span data-ttu-id="01cb7-132">連接到 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 時，在逾時並傳回連接失敗的錯誤訊息給使用者之前，要等候時間量，以秒為單位。</span><span class="sxs-lookup"><span data-stu-id="01cb7-132">The amount of time is seconds to wait when connecting to [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] before timing out and returning a failure to connect error to the user.</span></span> <span data-ttu-id="01cb7-133">若要變更這項設定，請使用所要的連接屬性重新連接。</span><span class="sxs-lookup"><span data-stu-id="01cb7-133">To change this, connect again with the desired connection properties.</span></span>  
  
 <span data-ttu-id="01cb7-134">**執行超時**</span><span class="sxs-lookup"><span data-stu-id="01cb7-134">**Execution Timeout**</span></span>  
 <span data-ttu-id="01cb7-135">伺服器上的工作執行完成之前，要等候的時間量，以秒為單位。</span><span class="sxs-lookup"><span data-stu-id="01cb7-135">The amount of time in seconds to wait before execution of a task is completed on the server.</span></span> <span data-ttu-id="01cb7-136">若要變更這項設定，請使用所要的連接屬性重新連接。</span><span class="sxs-lookup"><span data-stu-id="01cb7-136">To change this, connect again with the desired connection properties.</span></span>  
  
 <span data-ttu-id="01cb7-137">**已加密**</span><span class="sxs-lookup"><span data-stu-id="01cb7-137">**Encrypted**</span></span>  
 <span data-ttu-id="01cb7-138">決定目前的連接是否加密。</span><span class="sxs-lookup"><span data-stu-id="01cb7-138">Whether the current connection is encrypted.</span></span> <span data-ttu-id="01cb7-139">若要變更這項設定，請使用所要的連接屬性重新連接。</span><span class="sxs-lookup"><span data-stu-id="01cb7-139">To change this, connect again with the desired connection properties.</span></span>  
  
## <a name="product-category"></a><span data-ttu-id="01cb7-140">產品類別</span><span class="sxs-lookup"><span data-stu-id="01cb7-140">Product Category</span></span>  
 <span data-ttu-id="01cb7-141">檢視目前連接的產品屬性。</span><span class="sxs-lookup"><span data-stu-id="01cb7-141">View product properties for the current connection.</span></span> <span data-ttu-id="01cb7-142">這些屬性會描述伺服器產品、版本、執行個體名稱和定序。</span><span class="sxs-lookup"><span data-stu-id="01cb7-142">These properties describe the server product, version, instance name, and collation.</span></span> <span data-ttu-id="01cb7-143">這些屬性會在 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 安裝時設定。</span><span class="sxs-lookup"><span data-stu-id="01cb7-143">The properties are set during [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] installation.</span></span>  
  
 <span data-ttu-id="01cb7-144">**產品名稱**</span><span class="sxs-lookup"><span data-stu-id="01cb7-144">**Product Name**</span></span>  
 <span data-ttu-id="01cb7-145">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 產品名稱。</span><span class="sxs-lookup"><span data-stu-id="01cb7-145">The [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] product name.</span></span>  
  
 <span data-ttu-id="01cb7-146">**產品版本**</span><span class="sxs-lookup"><span data-stu-id="01cb7-146">**Product Version**</span></span>  
 <span data-ttu-id="01cb7-147">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 產品版本。</span><span class="sxs-lookup"><span data-stu-id="01cb7-147">The [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] product version.</span></span>  
  
 <span data-ttu-id="01cb7-148">**伺服器名稱**</span><span class="sxs-lookup"><span data-stu-id="01cb7-148">**Server Name**</span></span>  
 <span data-ttu-id="01cb7-149">正在執行 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]的電腦名稱。</span><span class="sxs-lookup"><span data-stu-id="01cb7-149">The name of the computer running [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="01cb7-150">**實例名稱**</span><span class="sxs-lookup"><span data-stu-id="01cb7-150">**Instance Name**</span></span>  
 <span data-ttu-id="01cb7-151">伺服器的執行個體名稱。</span><span class="sxs-lookup"><span data-stu-id="01cb7-151">The instance name of the server.</span></span> <span data-ttu-id="01cb7-152">預設的執行個體為空白。</span><span class="sxs-lookup"><span data-stu-id="01cb7-152">The default instance is blank.</span></span>  
  
 <span data-ttu-id="01cb7-153">**語言**</span><span class="sxs-lookup"><span data-stu-id="01cb7-153">**Language**</span></span>  
 <span data-ttu-id="01cb7-154">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 產品的語言版本。</span><span class="sxs-lookup"><span data-stu-id="01cb7-154">The language version of the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] product.</span></span>  
  
 <span data-ttu-id="01cb7-155">**定序**</span><span class="sxs-lookup"><span data-stu-id="01cb7-155">**Collation**</span></span>  
 <span data-ttu-id="01cb7-156">伺服器的定序。</span><span class="sxs-lookup"><span data-stu-id="01cb7-156">The collation of the server.</span></span>  
  
## <a name="server-environment-category"></a><span data-ttu-id="01cb7-157">伺服器環境類別目錄</span><span class="sxs-lookup"><span data-stu-id="01cb7-157">Server Environment Category</span></span>  
 <span data-ttu-id="01cb7-158">針對目前的連接，檢視與伺服器硬體和作業系統相關的伺服器環境屬性。</span><span class="sxs-lookup"><span data-stu-id="01cb7-158">View server environment properties for the current connection related to the server hardware and operating system.</span></span> <span data-ttu-id="01cb7-159">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]無法設定這些屬性。</span><span class="sxs-lookup"><span data-stu-id="01cb7-159">The properties cannot be configured by [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="01cb7-160">**電腦名稱稱**</span><span class="sxs-lookup"><span data-stu-id="01cb7-160">**Computer Name**</span></span>  
 <span data-ttu-id="01cb7-161">正在執行 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]的伺服器電腦名稱。</span><span class="sxs-lookup"><span data-stu-id="01cb7-161">The name of the server computer that is running [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="01cb7-162">**平台**</span><span class="sxs-lookup"><span data-stu-id="01cb7-162">**Platform**</span></span>  
 <span data-ttu-id="01cb7-163">伺服器的作業系統名稱、製造商名稱及 CPU 家族。</span><span class="sxs-lookup"><span data-stu-id="01cb7-163">The operating system name, manufacturer name, and CPU family of the server.</span></span>  
  
 <span data-ttu-id="01cb7-164">**作業系統**</span><span class="sxs-lookup"><span data-stu-id="01cb7-164">**Operating System**</span></span>  
 <span data-ttu-id="01cb7-165">伺服器上安裝的 [!INCLUDE[msCoName](../includes/msconame-md.md)] Windows 版本。</span><span class="sxs-lookup"><span data-stu-id="01cb7-165">The [!INCLUDE[msCoName](../includes/msconame-md.md)] Windows version installed on the server.</span></span>  
  
 <span data-ttu-id="01cb7-166">**處理器**</span><span class="sxs-lookup"><span data-stu-id="01cb7-166">**Processors**</span></span>  
 <span data-ttu-id="01cb7-167">伺服器上的處理器數目。</span><span class="sxs-lookup"><span data-stu-id="01cb7-167">The number of processors on the server.</span></span>  
  
 <span data-ttu-id="01cb7-168">**作業系統記憶體**</span><span class="sxs-lookup"><span data-stu-id="01cb7-168">**Operating System Memory**</span></span>  
 <span data-ttu-id="01cb7-169">伺服器上實體記憶體的總數 (以 MB 表示)。</span><span class="sxs-lookup"><span data-stu-id="01cb7-169">The total amount of physical memory on the server, in megabytes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01cb7-170">另請參閱</span><span class="sxs-lookup"><span data-stu-id="01cb7-170">See Also</span></span>  
 <span data-ttu-id="01cb7-171">[SQL Server Management Studio 中的屬性頁](../ssms/property-pages-in-sql-server-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="01cb7-171">[Property Pages in SQL Server Management Studio](../ssms/property-pages-in-sql-server-management-studio.md) </span></span>  
 [<span data-ttu-id="01cb7-172">連接到伺服器 &#40;登入頁面&#41; Database Engine</span><span class="sxs-lookup"><span data-stu-id="01cb7-172">Connect to Server &#40;Login Page&#41; Database Engine</span></span>](../ssms/f1-help/connect-to-server-login-page-database-engine.md)  
  
  
