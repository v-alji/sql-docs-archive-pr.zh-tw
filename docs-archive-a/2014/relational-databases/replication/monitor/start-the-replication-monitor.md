---
title: 啟動複寫監視器 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- Replication Monitor, starting
ms.assetid: e037bd27-cc87-4ee9-9e5f-83f6d717cfa4
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: cff23206923825d0e86e47ad6921c19f45e68b35
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709186"
---
# <a name="start-the-replication-monitor"></a><span data-ttu-id="61768-102">啟動複寫監視器</span><span class="sxs-lookup"><span data-stu-id="61768-102">Start the Replication Monitor</span></span>
  <span data-ttu-id="61768-103">「複寫監視器」可以從任何 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 執行個體上的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]啟動，也可以從命令提示字元啟動。</span><span class="sxs-lookup"><span data-stu-id="61768-103">Replication Monitor can be started from [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] on any instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], or from the command prompt.</span></span> <span data-ttu-id="61768-104">啟動「複寫監視器」後，將一個或多個「發行者」新增至監視器。</span><span class="sxs-lookup"><span data-stu-id="61768-104">After starting Replication Monitor, add one or more Publishers to monitor.</span></span> <span data-ttu-id="61768-105">如需詳細資訊，請參閱 [從複寫監視器加入及移除發行者](add-and-remove-publishers-from-replication-monitor.md)。</span><span class="sxs-lookup"><span data-stu-id="61768-105">For more information, see [Add and Remove Publishers from Replication Monitor](add-and-remove-publishers-from-replication-monitor.md).</span></span>  
  
### <a name="to-start-replication-monitor-from-sql-server-management-studio"></a><span data-ttu-id="61768-106">從 SQL Server Management Studio 啟動複寫監視器</span><span class="sxs-lookup"><span data-stu-id="61768-106">To start Replication Monitor from SQL Server Management Studio</span></span>  
  
1.  <span data-ttu-id="61768-107">連接到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 中的 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]執行個體，然後展開伺服器節點。</span><span class="sxs-lookup"><span data-stu-id="61768-107">Connect to an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], and then expand the server node.</span></span>  
  
2.  <span data-ttu-id="61768-108">以滑鼠右鍵按一下 **[複寫]** 資料夾或其任何子資料夾，再按一下 **[啟動複寫監視器]** 。</span><span class="sxs-lookup"><span data-stu-id="61768-108">Right-click the **Replication** folder or any of its subfolders, and then click **Launch Replication Monitor**.</span></span>  
  
### <a name="to-start-replication-monitor-from-the-command-prompt"></a><span data-ttu-id="61768-109">從命令提示字元啟動複寫監視器</span><span class="sxs-lookup"><span data-stu-id="61768-109">To start Replication Monitor from the command prompt</span></span>  
  
1.  <span data-ttu-id="61768-110">在命令提示字元中，瀏覽至工具安裝目錄，</span><span class="sxs-lookup"><span data-stu-id="61768-110">From the command prompt, navigate to the tools installation directory.</span></span> <span data-ttu-id="61768-111">預設路徑為 [!INCLUDE[ssInstallPath](../../../includes/ssinstallpath-md.md)]Tools\Binn\。</span><span class="sxs-lookup"><span data-stu-id="61768-111">The default path is [!INCLUDE[ssInstallPath](../../../includes/ssinstallpath-md.md)]Tools\Binn\ .</span></span>  
  
2.  <span data-ttu-id="61768-112">執行 sqlmonitor.exe。</span><span class="sxs-lookup"><span data-stu-id="61768-112">Run sqlmonitor.exe.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61768-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="61768-113">See Also</span></span>  
 [<span data-ttu-id="61768-114">監視複寫</span><span class="sxs-lookup"><span data-stu-id="61768-114">Monitoring Replication</span></span>](../monitoring-replication.md)  
  
  
