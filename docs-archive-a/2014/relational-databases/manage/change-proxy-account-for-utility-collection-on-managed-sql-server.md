---
title: 在 SQL Server (SQL Server 公用程式) 的受控執行個體上，變更公用程式收集組的 Proxy 帳戶 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: ff37ba8b-a08c-4109-b6e2-5748c995a52c
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 19f60c607ed661ef42c1c1c0e48854cdfd69a912
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592695"
---
# <a name="change-the-proxy-account-for-the-utility-collection-set-on-a-managed-instance-of-sql-server-sql-server-utility"></a><span data-ttu-id="da008-102">變更 SQL Server 受管理的執行個體上之公用程式收集組的 Proxy 帳戶 (SQL Server 公用程式)</span><span class="sxs-lookup"><span data-stu-id="da008-102">Change the Proxy Account for the Utility Collection Set on a Managed Instance of SQL Server (SQL Server Utility)</span></span>
  <span data-ttu-id="da008-103">此主題描述如何使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中變更 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]受管理的執行個體上公用程式收集組的 Proxy 帳戶。</span><span class="sxs-lookup"><span data-stu-id="da008-103">This topic describes how to change the proxy account for the Utility Collection Set on a managed instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="da008-104">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="da008-104">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-change-the-proxy-account-for-the-utility-collection-set-on-a-managed-instance-of-sql-server"></a><span data-ttu-id="da008-105">若要變更 SQL Server 受管理的執行個體上之公用程式收集組的 Proxy 帳戶</span><span class="sxs-lookup"><span data-stu-id="da008-105">To change the proxy account for the utility collection set on a managed instance of SQL Server</span></span>  
  
1.  <span data-ttu-id="da008-106">從 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 公用程式中移除 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的受管理的執行個體。</span><span class="sxs-lookup"><span data-stu-id="da008-106">Remove the managed instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] from the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility.</span></span>  
  
    -   <span data-ttu-id="da008-107">在 SSMS 內的 [公用程式總管] 中，按一下 [受管理的執行個體] 節點。</span><span class="sxs-lookup"><span data-stu-id="da008-107">In **Utility Explorer** in SSMS, click on the **Managed Instances** node.</span></span>  
  
    -   <span data-ttu-id="da008-108">在 [公用程式總管] 清單檢視中，以滑鼠右鍵按一下 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體名稱，然後選取 [移除受控執行個體...]。如需詳細資訊，請參閱 [從 SQL Server 公用程式中移除 SQL Server 執行個體](remove-an-instance-of-sql-server-from-the-sql-server-utility.md)。</span><span class="sxs-lookup"><span data-stu-id="da008-108">In the **Utility Explorer** list view, right-click the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance name, and select **Remove Managed Instance...**. For more information, see [Remove an Instance of SQL Server from the SQL Server Utility](remove-an-instance-of-sql-server-from-the-sql-server-utility.md).</span></span>  
  
2.  <span data-ttu-id="da008-109">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 公用程式內再次註冊 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="da008-109">Enroll the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility again.</span></span>  
  
    -   <span data-ttu-id="da008-110">在 SSMS 的 [公用程式總管] 中，以滑鼠右鍵按一下 [受控執行個體] 節點，然後選取 [新增受控執行個體...]。</span><span class="sxs-lookup"><span data-stu-id="da008-110">In **Utility Explorer** in SSMS, right-click on the **Managed Instances** node, and select **Add Managed Instance...**.</span></span>  
  
    -   <span data-ttu-id="da008-111">依照提示完成精靈，指定新的 Proxy 帳戶。</span><span class="sxs-lookup"><span data-stu-id="da008-111">Follow prompts to complete the wizard, specifying the new proxy account.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da008-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="da008-112">See Also</span></span>  
 <span data-ttu-id="da008-113">[SQL Server 公用程式的功能與工作](sql-server-utility-features-and-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="da008-113">[SQL Server Utility Features and Tasks](sql-server-utility-features-and-tasks.md) </span></span>  
 [<span data-ttu-id="da008-114">疑難排解 SQL Server 公用程式</span><span class="sxs-lookup"><span data-stu-id="da008-114">Troubleshoot the SQL Server Utility</span></span>](../../database-engine/troubleshoot-the-sql-server-utility.md)  
  
  
