---
title: 將目標伺服器編列至主要伺服器 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- enlisting target servers [SQL Server]
- SQL Server Agent jobs, target servers
- master servers [SQL Server], enlisting target servers
- SQL Server Agent jobs, master servers
- target servers [SQL Server], enlisting
ms.assetid: 7633adb5-d140-4e58-a8f2-5b4b50c2f95b
author: stevestein
ms.author: sstein
ms.openlocfilehash: 256f1a78d298d89a36412ee5689695f3ab3fde8e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584963"
---
# <a name="enlist-a-target-server-to-a-master-server"></a><span data-ttu-id="2587f-102">將目標伺服器編列至主要伺服器</span><span class="sxs-lookup"><span data-stu-id="2587f-102">Enlist a Target Server to a Master Server</span></span>
  <span data-ttu-id="2587f-103">此主題描述如何將目標伺服器新增至多伺服器管理組態。</span><span class="sxs-lookup"><span data-stu-id="2587f-103">This topic describes how to add target servers to a multiserver administration configuration.</span></span> <span data-ttu-id="2587f-104">從主要伺服器執行這個程序。</span><span class="sxs-lookup"><span data-stu-id="2587f-104">Run this procedure from the master server.</span></span> <span data-ttu-id="2587f-105">在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中，使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]、 [!INCLUDE[tsql](../../includes/tsql-md.md)]或 SQL Server 管理物件 (SMO)。</span><span class="sxs-lookup"><span data-stu-id="2587f-105">in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)], or SQL Server Management Objects (SMO).</span></span>  
  
 <span data-ttu-id="2587f-106">如需有關用於 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 服務之 Windows 帳戶如何影響多伺服器環境的詳細資訊，請參閱 [建立多伺服器環境](create-a-multiserver-environment.md)。</span><span class="sxs-lookup"><span data-stu-id="2587f-106">For information about how the Windows account used for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service affects a multiserver environment, see [Create a Multiserver Environment](create-a-multiserver-environment.md).</span></span>  
  
 <span data-ttu-id="2587f-107">依預設，主要伺服器和目標伺服器之間的連接會啟用完整的安全通訊端層 (SSL) 加密與憑證驗證。</span><span class="sxs-lookup"><span data-stu-id="2587f-107">Full Secure Sockets Layer (SSL) encryption and certificate validation is enabled for connections between master servers and target servers by default.</span></span> <span data-ttu-id="2587f-108">如需詳細資訊，請參閱 [在目標伺服器上設定加密選項](set-encryption-options-on-target-servers.md)。</span><span class="sxs-lookup"><span data-stu-id="2587f-108">For more information, see [Set Encryption Options on Target Servers](set-encryption-options-on-target-servers.md).</span></span>  
  
 <span data-ttu-id="2587f-109">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="2587f-109">**In This Topic**</span></span>  
  
-   <span data-ttu-id="2587f-110">**若要編列目標伺服器，使用：**</span><span class="sxs-lookup"><span data-stu-id="2587f-110">**To enlist a target server, using:**</span></span>  
  
     [<span data-ttu-id="2587f-111">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="2587f-111">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="2587f-112">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="2587f-112">Transact-SQL</span></span>](#TsqlProcedure)  
  
     [<span data-ttu-id="2587f-113">SMO</span><span class="sxs-lookup"><span data-stu-id="2587f-113">SMO</span></span>](#PowerShellProcedure)  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="2587f-114">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="2587f-114">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-enlist-a-target-server"></a><span data-ttu-id="2587f-115">若要編列目標伺服器</span><span class="sxs-lookup"><span data-stu-id="2587f-115">To enlist a target server</span></span>  
  
1.  <span data-ttu-id="2587f-116">在 **[物件總管]** 中，展開設定為主要伺服器的伺服器。</span><span class="sxs-lookup"><span data-stu-id="2587f-116">In **Object Explorer**, expand a server that is configured as a master server.</span></span>  
  
2.  <span data-ttu-id="2587f-117">以滑鼠右鍵按一下 **[SQL Server Agent]** ，指向 **[多伺服器管理]** ，然後按一下 **[新增目標伺服器]** 。</span><span class="sxs-lookup"><span data-stu-id="2587f-117">Right-click **SQL Server Agent**, point to **Multi Server Administration**, and then click **Add Target Servers**.</span></span>  
  
3.  <span data-ttu-id="2587f-118">完成「目標伺服器精靈」，精靈將引導您完成此程序。</span><span class="sxs-lookup"><span data-stu-id="2587f-118">Complete the Target Server Wizard, which guides you through the process.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="2587f-119">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="2587f-119">Using Transact-SQL</span></span>  
  
#### <a name="to-enlist-a-target-server"></a><span data-ttu-id="2587f-120">若要編列目標伺服器</span><span class="sxs-lookup"><span data-stu-id="2587f-120">To enlist a target server</span></span>  
  
1.  <span data-ttu-id="2587f-121">使用 `sp_msx_enlist` 預存程序。</span><span class="sxs-lookup"><span data-stu-id="2587f-121">Use the `sp_msx_enlist` stored procedure.</span></span>  <span data-ttu-id="2587f-122">如需詳細資訊，請參閱[sp_msx_enlist &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-msx-enlist-transact-sql)</span><span class="sxs-lookup"><span data-stu-id="2587f-122">For more information, see [sp_msx_enlist &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-msx-enlist-transact-sql)</span></span>  
  
##  <a name="using-sql-server-management-objects-smo"></a><a name="PowerShellProcedure"></a><span data-ttu-id="2587f-123">使用 SQL Server 管理物件 (SMO) </span><span class="sxs-lookup"><span data-stu-id="2587f-123">Using SQL Server Management Objects (SMO)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2587f-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2587f-124">See Also</span></span>  
 [<span data-ttu-id="2587f-125">將整個企業的管理自動化</span><span class="sxs-lookup"><span data-stu-id="2587f-125">Automated Administration Across an Enterprise</span></span>](automated-administration-across-an-enterprise.md)  
  
  
