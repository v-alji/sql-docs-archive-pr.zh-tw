---
title: 使多個目標伺服器脫離主要伺服器 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent jobs, target servers
- target servers [SQL Server], defecting
- SQL Server Agent jobs, master servers
- master servers [SQL Server], defecting target servers
- defecting target servers
- multiple target server defections
ms.assetid: 61a3713b-403a-4806-bfc4-66db72ca1156
author: stevestein
ms.author: sstein
ms.openlocfilehash: b31a8bc38968733de0a23f67a71772721c8baedd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87699223"
---
# <a name="defect-multiple-target-servers-from-a-master-server"></a><span data-ttu-id="78575-102">Defect Multiple Target Servers from a Master Server</span><span class="sxs-lookup"><span data-stu-id="78575-102">Defect Multiple Target Servers from a Master Server</span></span>
  <span data-ttu-id="78575-103">本主題描述如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 從 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]的多伺服器管理組態中脫離多個目標伺服器。</span><span class="sxs-lookup"><span data-stu-id="78575-103">This topic describes how to defect multiple target servers from a multiserver administration configuration in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="78575-104">從主要伺服器執行這個程序。</span><span class="sxs-lookup"><span data-stu-id="78575-104">Run this procedure from the master server.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="78575-105">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="78575-105">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-defect-multiple-target-servers-from-a-master-server"></a><span data-ttu-id="78575-106">若要從主要伺服器脫離多個目標伺服器</span><span class="sxs-lookup"><span data-stu-id="78575-106">To defect multiple target servers from a master server</span></span>  
  
1.  <span data-ttu-id="78575-107">在 **[物件總管]** 中，展開設定為主要伺服器的伺服器。</span><span class="sxs-lookup"><span data-stu-id="78575-107">In **Object Explorer**, expand a server that is configured as a master server.</span></span>  
  
2.  <span data-ttu-id="78575-108">以滑鼠右鍵按一下 [SQL Server Agent]\*\*\*\*，指向 [多重伺服器管理]\*\*\*\*，然後按一下 [管理目標伺服器]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="78575-108">Right-click **SQL Server Agent**, point to **Multi Server Administration**, and then click **Manage Target Servers**.</span></span>  
  
3.  <span data-ttu-id="78575-109">按一下 **[公佈指示]**，然後在 **[指示類型]** 清單中選取 **[脫離]**。</span><span class="sxs-lookup"><span data-stu-id="78575-109">Click **Post Instructions**, and then in the **Instruction type** list, select **Defect**.</span></span>  
  
4.  <span data-ttu-id="78575-110">在 **[收件者]** 下，執行下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="78575-110">Under **Recipients**, do one of the following:</span></span>  
  
    -   <span data-ttu-id="78575-111">按一下 **[所有目標伺服器]** ，脫離此主要伺服器的所有目標伺服器。</span><span class="sxs-lookup"><span data-stu-id="78575-111">Click **All target servers** to defect all target servers of this master server.</span></span> <span data-ttu-id="78575-112">如果您要完整解除安裝目前的多伺服器管理組態，請使用此選項。</span><span class="sxs-lookup"><span data-stu-id="78575-112">Use this option if you want to completely uninstall the current multiserver administration configuration.</span></span>  
  
    -   <span data-ttu-id="78575-113">按一下 **[下列目標伺服器]**，然後按一下對應的 **[選取]** 方塊，脫離此主要伺服器的部份目標伺服器，但不是所有目標伺服器。</span><span class="sxs-lookup"><span data-stu-id="78575-113">Click **These target servers**, and then click the corresponding **Select** box, to defect some, but not all, target servers of this master server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78575-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="78575-114">See Also</span></span>  
 <span data-ttu-id="78575-115">[建立多伺服器環境](create-a-multiserver-environment.md) </span><span class="sxs-lookup"><span data-stu-id="78575-115">[Create a Multiserver Environment](create-a-multiserver-environment.md) </span></span>  
 <span data-ttu-id="78575-116">[將整個企業的管理自動化](automated-administration-across-an-enterprise.md) </span><span class="sxs-lookup"><span data-stu-id="78575-116">[Automated Administration Across an Enterprise](automated-administration-across-an-enterprise.md) </span></span>  
 [<span data-ttu-id="78575-117">使目標伺服器脫離主要伺服器</span><span class="sxs-lookup"><span data-stu-id="78575-117">Defect a Target Server from a Master Server</span></span>](defect-a-target-server-from-a-master-server.md)  
  
  
