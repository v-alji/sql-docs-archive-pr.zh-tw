---
title: 新增或取代資料庫鏡像見證 (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- witness [SQL Server], establishing
- database mirroring [SQL Server], witness
ms.assetid: 4b5ecffd-f025-4ab7-b69d-8958c6477127
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 5dd14ace23956ceef114f1f032b5d4db5febcec7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593588"
---
# <a name="add-or-replace-a-database-mirroring-witness-sql-server-management-studio"></a><span data-ttu-id="f66a1-102">加入或取代資料庫鏡像見證 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="f66a1-102">Add or Replace a Database Mirroring Witness (SQL Server Management Studio)</span></span>
  <span data-ttu-id="f66a1-103">如果資料庫鏡像端點使用 Windows 驗證，您就可以使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 來加入或取代見證。</span><span class="sxs-lookup"><span data-stu-id="f66a1-103">If the database mirroring endpoints use Windows Authentication,, you can use [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to add or replace a witness.</span></span> <span data-ttu-id="f66a1-104">在 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 中加入見證也會將作業模式變更為具有自動容錯移轉的高安全性模式。</span><span class="sxs-lookup"><span data-stu-id="f66a1-104">Adding a witness in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] also changes the operating mode to high-safety mode with automatic failover.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f66a1-105">我們強烈建議見證應該位在任何夥伴的另一台電腦上。</span><span class="sxs-lookup"><span data-stu-id="f66a1-105">We strongly recommend that the witness reside on a separate computer from either of the partners.</span></span> <span data-ttu-id="f66a1-106">見證使用的服務帳戶必須與主體和鏡像伺服器執行個體使用的服務帳戶位於相同的網域中，否則此帳戶就必須位於受信任網域中。</span><span class="sxs-lookup"><span data-stu-id="f66a1-106">The service account used by the witness must be in the same domain as the service accounts used by the principal and mirror server instances, or it must be in a trusted domain.</span></span>  
  
### <a name="to-add-or-replace-a-witness"></a><span data-ttu-id="f66a1-107">若要加入或取代見證</span><span class="sxs-lookup"><span data-stu-id="f66a1-107">To Add or Replace a Witness</span></span>  
  
1.  <span data-ttu-id="f66a1-108">連接到主體伺服器執行個體後，在 [物件總管] 中按一下伺服器名稱，以展開伺服器樹狀目錄。</span><span class="sxs-lookup"><span data-stu-id="f66a1-108">After connecting to the principal server instance, in Object Explorer, click the server name to expand the server tree.</span></span>  
  
2.  <span data-ttu-id="f66a1-109">展開 **[資料庫]** ，然後選取您要加入或取代見證之工作階段的主體資料庫。</span><span class="sxs-lookup"><span data-stu-id="f66a1-109">Expand **Databases**, and select the principal database of the session to which you are adding or replacing a witness.</span></span>  
  
3.  <span data-ttu-id="f66a1-110">以滑鼠右鍵按一下資料庫，選取 [工作]，然後按一下 [鏡像]。</span><span class="sxs-lookup"><span data-stu-id="f66a1-110">Right-click the database, select **Tasks**, and then click **Mirror**.</span></span> <span data-ttu-id="f66a1-111">這將會開啟在 **[資料庫屬性]** 對話方塊中的 **[鏡像]** 頁面。</span><span class="sxs-lookup"><span data-stu-id="f66a1-111">This opens the **Mirroring** page of the **Database Properties** dialog box.</span></span>  
  
4.  <span data-ttu-id="f66a1-112">按一下 **[設定安全性]** 。</span><span class="sxs-lookup"><span data-stu-id="f66a1-112">Click **Configure Security**.</span></span>  
  
5.  <span data-ttu-id="f66a1-113">如果出現 **[設定資料庫鏡像安全性精靈]** 歡迎畫面，請按 **[下一步]** 。</span><span class="sxs-lookup"><span data-stu-id="f66a1-113">If the **Configure Database Mirroring Security Wizard** welcome screen appears, click **Next**.</span></span>  
  
6.  <span data-ttu-id="f66a1-114">在 **[包含見證伺服器]** 對話方塊中，按一下 **[是]** ，然後按 **[下一步]** 。</span><span class="sxs-lookup"><span data-stu-id="f66a1-114">In the **Include Witness Server** dialog box, click **Yes**, and then click **Next**.</span></span>  
  
7.  <span data-ttu-id="f66a1-115">在 **[選擇要設定的伺服器]** 對話方塊中，會自動核取 **[見證伺服器執行個體]** 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="f66a1-115">In the **Choose Servers to Configure** dialog box, the **Witness server instance** check box is automatically checked.</span></span> <span data-ttu-id="f66a1-116">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="f66a1-116">Click **Next**.</span></span>  
  
8.  <span data-ttu-id="f66a1-117">在 **[主體伺服器執行個體]** 對話方塊中，保留現有的通訊埠和端點。</span><span class="sxs-lookup"><span data-stu-id="f66a1-117">On the **Principal Server Instance** dialog box, keep the existing port and endpoint.</span></span> <span data-ttu-id="f66a1-118">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="f66a1-118">Click **Next**.</span></span>  
  
9. <span data-ttu-id="f66a1-119">在 **[見證伺服器執行個體]** 對話方塊中，按一下 **[連接]** 。</span><span class="sxs-lookup"><span data-stu-id="f66a1-119">On the **Witness Server Instance** dialog box, click **Connect**.</span></span>  
  
10. <span data-ttu-id="f66a1-120">在 [連接到伺服器] 對話方塊的 [伺服器名稱] 欄位中，指定見證伺服器執行個體，並使用 Windows 驗證 (預設值)。</span><span class="sxs-lookup"><span data-stu-id="f66a1-120">In the **Connect to Server** dialog box, specify the witness server instance in the **Server name** field, and use Windows Authentication (the default).</span></span> <span data-ttu-id="f66a1-121">按一下 [ **連接**]。</span><span class="sxs-lookup"><span data-stu-id="f66a1-121">Click **Connect**.</span></span>  
  
11. <span data-ttu-id="f66a1-122">一旦連接建立後， **[見證伺服器執行個體]** 對話方塊中就會顯示見證伺服器執行個體的接聽程式通訊埠和資料庫鏡像端點。</span><span class="sxs-lookup"><span data-stu-id="f66a1-122">Once a connection is established, the listener port and database mirroring endpoint of the witness server instance are displayed on the **Witness Server Instance** dialog box.</span></span> <span data-ttu-id="f66a1-123">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="f66a1-123">Click **Next**.</span></span>  
  
12. <span data-ttu-id="f66a1-124">**[服務帳戶]** 對話方塊會包含主體、鏡像及見證伺服器執行個體之網域服務帳戶的欄位。</span><span class="sxs-lookup"><span data-stu-id="f66a1-124">The **Service Accounts** dialog box contains fields for the domain service accounts of the principal, mirror, and witness server instances.</span></span>  
  
    -   <span data-ttu-id="f66a1-125">如果這些伺服器執行個體都使用相同的服務帳戶，請將這些欄位保留空白。</span><span class="sxs-lookup"><span data-stu-id="f66a1-125">If the server instances all use the same service account, leave the fields blank.</span></span>  
  
    -   <span data-ttu-id="f66a1-126">如果見證伺服器執行個體與其中一個夥伴使用不同的服務帳戶，請在 **[主體]** 、 **[鏡像]** 及 **[見證]** 欄位中填入帳戶名稱：</span><span class="sxs-lookup"><span data-stu-id="f66a1-126">If the witness server instance uses a different service account from either of the partners, fill in the **Principal**, **Mirror**, and **Witness** fields with the account name:</span></span>  
  
         <span data-ttu-id="f66a1-127">網域名稱 **\\** 使用者名稱</span><span class="sxs-lookup"><span data-stu-id="f66a1-127">*DOMAINNAME* **\\** *username*</span></span>  
  
         <span data-ttu-id="f66a1-128">網域名稱必須使用大寫。</span><span class="sxs-lookup"><span data-stu-id="f66a1-128">The domain name must be in upper case.</span></span>  
  
     <span data-ttu-id="f66a1-129">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="f66a1-129">Click **Next**.</span></span>  
  
13. <span data-ttu-id="f66a1-130">在 **[完成精靈]** 摘要畫面中，選擇性地驗證見證組態，然後按一下 **[完成]** 。</span><span class="sxs-lookup"><span data-stu-id="f66a1-130">On the **Complete the Wizard** summary screen, optionally, verify the witness configuration, and then click **Finish**.</span></span>  
  
14. <span data-ttu-id="f66a1-131">完成之後，精靈就會讓您返回 **[資料庫屬性]** 對話方塊，而且見證的伺服器網路位址現在會顯示在 **[見證]** 欄位中。</span><span class="sxs-lookup"><span data-stu-id="f66a1-131">On finishing, the wizard returns you to the **Database Properties** dialog box where the server network address of the witness now appears in **Witness** field.</span></span> <span data-ttu-id="f66a1-132">此外，會自動選取見證所需的 [具有自動容錯移轉的高安全性 (同步)]。</span><span class="sxs-lookup"><span data-stu-id="f66a1-132">Also, **High-safety mode with automatic failover (synchronous)**, which is required with a witness, is automatically selected.</span></span>  
  
     <span data-ttu-id="f66a1-133">若要啟用見證並將工作階段變更為具有自動容錯移轉的高安全性模式，請按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="f66a1-133">To enable the witness and change the session to high-safety mode with automatic failover, Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f66a1-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f66a1-134">See Also</span></span>  
 <span data-ttu-id="f66a1-135">[資料庫鏡像見證](database-mirroring-witness.md) </span><span class="sxs-lookup"><span data-stu-id="f66a1-135">[Database Mirroring Witness](database-mirroring-witness.md) </span></span>  
 <span data-ttu-id="f66a1-136">[資料庫鏡像 &#40;SQL Server&#41;](database-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="f66a1-136">[Database Mirroring &#40;SQL Server&#41;](database-mirroring-sql-server.md) </span></span>  
 <span data-ttu-id="f66a1-137">[資料庫屬性 &#40;鏡像頁面&#41;](../../relational-databases/databases/database-properties-mirroring-page.md) </span><span class="sxs-lookup"><span data-stu-id="f66a1-137">[Database Properties &#40;Mirroring Page&#41;](../../relational-databases/databases/database-properties-mirroring-page.md) </span></span>  
 <span data-ttu-id="f66a1-138">[使用 Windows 驗證建立資料庫鏡像工作階段 &#40;SQL Server Management Studio&#41;](establish-database-mirroring-session-windows-authentication.md) </span><span class="sxs-lookup"><span data-stu-id="f66a1-138">[Establish a Database Mirroring Session Using Windows Authentication &#40;SQL Server Management Studio&#41;](establish-database-mirroring-session-windows-authentication.md) </span></span>  
 [<span data-ttu-id="f66a1-139">資料庫鏡像見證</span><span class="sxs-lookup"><span data-stu-id="f66a1-139">Database Mirroring Witness</span></span>](database-mirroring-witness.md)  
  
  
