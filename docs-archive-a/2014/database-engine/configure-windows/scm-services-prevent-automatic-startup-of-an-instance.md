---
title: 防止自動啟動 SQL Server (SQL Server 組態管理員) 的實例 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- automatic SQL Server startup
- SQL Server, stopping
- SQL Server, automatic startup
- canceling automatic startup
- stopping SQL Server
- preventing automatic startups [SQL Server]
ms.assetid: 782663cf-f3d7-4cc6-b621-21e4550f0322
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 8f93f5abc749f589ab4208b3a4c9434ca63b8769
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596901"
---
# <a name="prevent-automatic-startup-of-an-instance-of-sql-server-sql-server-configuration-manager"></a><span data-ttu-id="6b3dd-102">避免自動啟動 SQL Server 的執行個體 (SQL Server 組態管理員)</span><span class="sxs-lookup"><span data-stu-id="6b3dd-102">Prevent Automatic Startup of an Instance of SQL Server (SQL Server Configuration Manager)</span></span>
  <span data-ttu-id="6b3dd-103">此主題描述如何使用 SQL Server 組態管理員，在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中防止 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 執行個體自動啟動。</span><span class="sxs-lookup"><span data-stu-id="6b3dd-103">This topic describes how prevent an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] from starting automatically in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using SQL Server Configuration Manager.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="6b3dd-104">通常會設定為自動啟動。</span><span class="sxs-lookup"><span data-stu-id="6b3dd-104">is normally configured to start automatically.</span></span> <span data-ttu-id="6b3dd-105">不過您也可以將該執行個體的啟動模式改設為手動。</span><span class="sxs-lookup"><span data-stu-id="6b3dd-105">You can change that by setting the start mode for the instance to manual.</span></span>  
  
##  <a name="using-sql-server-configuration-manager"></a><a name="SSMSProcedure"></a> <span data-ttu-id="6b3dd-106">使用 SQL Server 組態管理員</span><span class="sxs-lookup"><span data-stu-id="6b3dd-106">Using SQL Server Configuration Manager</span></span>  
  
#### <a name="to-prevent-automatic-startup-of-an-instance-of-sql-server"></a><span data-ttu-id="6b3dd-107">避免自動啟動 SQL Server 的執行個體</span><span class="sxs-lookup"><span data-stu-id="6b3dd-107">To prevent automatic startup of an instance of SQL Server</span></span>  
  
1.  <span data-ttu-id="6b3dd-108">指向 **[開始]** 功能表上的 **[所有程式]** ，然後依序指向 [ [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)]] 和 **[組態工具]** ，再按一下 **[SQL Server 組態管理員]** 。</span><span class="sxs-lookup"><span data-stu-id="6b3dd-108">On the **Start** menu, point to **All Programs**, point to [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)], point to **Configuration Tools**, and then click **SQL Server Configuration Manager**.</span></span>  
  
2.  <span data-ttu-id="6b3dd-109">在 [SQL Server 組態管理員] 中展開 [服務]，然後按一下 [SQL Server]。</span><span class="sxs-lookup"><span data-stu-id="6b3dd-109">In SQL Server Configuration Manager, expand **Services**, and then click **SQL Server**.</span></span>  
  
3.  <span data-ttu-id="6b3dd-110">在 [詳細資料] 窗格中，以滑鼠右鍵按一下 [MSSQLServer]，然後按一下 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="6b3dd-110">In the details pane, right-click **MSSQLServer**, and then click **Properties.**</span></span>  
  
4.  <span data-ttu-id="6b3dd-111">在 [ **SQL Server \<**_instancename_**> 屬性**] 對話方塊的 [**屬性**] 方塊中，將 [**啟動模式]** 的值設定為 [**手動**]。</span><span class="sxs-lookup"><span data-stu-id="6b3dd-111">In the **SQL Server \<**_instancename_**> Properties** dialog box, in the **Properties** box, set the value of **Start Mode** to **Manual**.</span></span>  
  
5.  <span data-ttu-id="6b3dd-112">按一下 [確定] 以關閉 [SQL Server \<**_instancename_**> 屬性] 對話方塊，然後關閉 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 組態管理員。</span><span class="sxs-lookup"><span data-stu-id="6b3dd-112">Click **OK** to close the **SQL Server \<**_instancename_**> Properties** dialog box, and then close [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b3dd-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6b3dd-113">See Also</span></span>  
 [<span data-ttu-id="6b3dd-114">啟動、停止、暫停、繼續、重新啟動 Database Engine、SQL Server Agent 或 SQL Server Browser 服務</span><span class="sxs-lookup"><span data-stu-id="6b3dd-114">Start, Stop, Pause, Resume, Restart the Database Engine, SQL Server Agent, or SQL Server Browser Service</span></span>](start-stop-pause-resume-restart-sql-server-services.md)  
  
  
