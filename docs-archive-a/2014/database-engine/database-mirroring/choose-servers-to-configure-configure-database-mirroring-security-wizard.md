---
title: 選取要設定的伺服器 (設定資料庫鏡像安全性精靈) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.configdbmsecurwiz.choosesrvrs.f1
ms.assetid: 59e23ff3-d7ee-4e32-9629-0b54d3a258f7
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 18e36f5c8ec020b3859dc847d1bbfc019817bcd3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593583"
---
# <a name="choose-servers-to-configure-configure-database-mirroring-security-wizard"></a><span data-ttu-id="a11c7-102">選取要設定的伺服器 (設定資料庫鏡像安全性精靈)</span><span class="sxs-lookup"><span data-stu-id="a11c7-102">Choose Servers to Configure (Configure Database Mirroring Security Wizard)</span></span>
  <span data-ttu-id="a11c7-103">使用此頁面來指定現在要設定的伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="a11c7-103">Use this page to specify which server instances you want to configure now.</span></span> <span data-ttu-id="a11c7-104">您必須至少選取一個伺服器執行個體才能繼續執行精靈。</span><span class="sxs-lookup"><span data-stu-id="a11c7-104">You must select at least one server instance before continuing the wizard.</span></span>  
  
 <span data-ttu-id="a11c7-105">如果清除某個伺服器執行個體的核取方塊，則精靈將不會對其做任何變更。</span><span class="sxs-lookup"><span data-stu-id="a11c7-105">If you clear the check box for a server instance, the wizard will not make any changes to it.</span></span> <span data-ttu-id="a11c7-106">不過，精靈會要求您輸入有關該執行個體的資訊，並將此資訊另存為其他伺服器執行個體組態的一部分。</span><span class="sxs-lookup"><span data-stu-id="a11c7-106">The wizard, however, will ask you to enter information about that instance and save this information as part of the configuration of the other server instances.</span></span> <span data-ttu-id="a11c7-107">例如，若您清除見證伺服器執行個體的核取方塊，精靈將會要求您輸入該見證的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服務帳戶，因為必須將該帳戶的登入建立為安全性組態的一部分，並儲存在主體和鏡像伺服器執行個體中。</span><span class="sxs-lookup"><span data-stu-id="a11c7-107">For example, if you clear the check box for the witness server instance, the wizard will ask you to enter the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service account of the witness because a login for that account must be created as part of the security configuration saved at the principal and mirror server instances.</span></span>  
  
 <span data-ttu-id="a11c7-108">**若要使用 SQL Server Management Studio 設定資料庫鏡像**</span><span class="sxs-lookup"><span data-stu-id="a11c7-108">**To configure database mirroring by using SQL Server Management Studio**</span></span>  
  
-   [<span data-ttu-id="a11c7-109">使用 Windows 驗證建立資料庫鏡像工作階段 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="a11c7-109">Establish a Database Mirroring Session Using Windows Authentication &#40;SQL Server Management Studio&#41;</span></span>](establish-database-mirroring-session-windows-authentication.md)  
  
-   [<span data-ttu-id="a11c7-110">啟動設定資料庫鏡像安全性精靈 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="a11c7-110">Start the Configuring Database Mirroring Security Wizard &#40;SQL Server Management Studio&#41;</span></span>](start-the-configuring-database-mirroring-security-wizard.md)  
  
## <a name="options"></a><span data-ttu-id="a11c7-111">選項。</span><span class="sxs-lookup"><span data-stu-id="a11c7-111">Options</span></span>  
 <span data-ttu-id="a11c7-112">**主體伺服器執行個體**</span><span class="sxs-lookup"><span data-stu-id="a11c7-112">**Principal server instance**</span></span>  
 <span data-ttu-id="a11c7-113">選取以設定主體伺服器的安全性。</span><span class="sxs-lookup"><span data-stu-id="a11c7-113">Select to configure security for the principal server.</span></span>  
  
 <span data-ttu-id="a11c7-114">**鏡像伺服器執行個體**</span><span class="sxs-lookup"><span data-stu-id="a11c7-114">**Mirror server instance**</span></span>  
 <span data-ttu-id="a11c7-115">選取以設定鏡像伺服器的安全性。</span><span class="sxs-lookup"><span data-stu-id="a11c7-115">Select to configure security for the mirror server.</span></span>  
  
 <span data-ttu-id="a11c7-116">**見證伺服器執行個體**</span><span class="sxs-lookup"><span data-stu-id="a11c7-116">**Witness server instance**</span></span>  
 <span data-ttu-id="a11c7-117">選取以設定見證伺服器的安全性 (如果有的話)。</span><span class="sxs-lookup"><span data-stu-id="a11c7-117">Select to configure security for the witness server (if present).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a11c7-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a11c7-118">See Also</span></span>  
 <span data-ttu-id="a11c7-119">[資料庫屬性 &#40;鏡像頁面&#41;](../../relational-databases/databases/database-properties-mirroring-page.md) </span><span class="sxs-lookup"><span data-stu-id="a11c7-119">[Database Properties &#40;Mirroring Page&#41;](../../relational-databases/databases/database-properties-mirroring-page.md) </span></span>  
 [<span data-ttu-id="a11c7-120">資料庫鏡像 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="a11c7-120">Database Mirroring &#40;SQL Server&#41;</span></span>](database-mirroring-sql-server.md)  
  
  
