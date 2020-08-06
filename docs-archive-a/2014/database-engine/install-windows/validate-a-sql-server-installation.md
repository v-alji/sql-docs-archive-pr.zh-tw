---
title: 驗證 SQL Server 安裝 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
helpviewer_keywords:
- validating installations [SQL Server]
ms.assetid: 1689af50-d2b8-4aa6-8f27-cc7127157fc8
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 8dd4e6ce7800c3a0a9db51f6c1a4bddfe7a188c3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87698512"
---
# <a name="validate-a-sql-server-installation"></a><span data-ttu-id="030d5-102">驗證 SQL Server 安裝</span><span class="sxs-lookup"><span data-stu-id="030d5-102">Validate a SQL Server Installation</span></span>
  <span data-ttu-id="030d5-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 探索報告可以用於驗證電腦上所安裝的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 版本與 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 功能。</span><span class="sxs-lookup"><span data-stu-id="030d5-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] discovery report can be used to verify the version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] features installed on the computer.</span></span> <span data-ttu-id="030d5-104">[**已安裝的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 功能探索報告**] 會顯示 [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 安裝在本機伺服器上之所有、、、、和 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 產品及功能的報告。</span><span class="sxs-lookup"><span data-stu-id="030d5-104">The **Installed [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] features discovery report** displays a report of all [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)], [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], and [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] products and features that are installed on the local server.</span></span> <span data-ttu-id="030d5-105">您可以從 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安裝中心的 **工具** 頁面存取 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 功能探索報告。</span><span class="sxs-lookup"><span data-stu-id="030d5-105">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] features discovery report is available on the **Tools** page on the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Installation center.</span></span>  
  
 <span data-ttu-id="030d5-106">**若要執行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 功能探索報告：**</span><span class="sxs-lookup"><span data-stu-id="030d5-106">**To run [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] features discovery report:**</span></span>  
  
 <span data-ttu-id="030d5-107">如果要啟動 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安裝中心，請使用 [開始] 功能表，並依序指向 [所有程式]、[[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \<Version Name>] 和 [組態工具]，然後按一下 [[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安裝中心]。</span><span class="sxs-lookup"><span data-stu-id="030d5-107">Launch the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Installation center, using the **Start** menu, point to **All Programs**, point to **[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \<Version Name>**, point to **Configuration Tools**, and click **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Installation Center**.</span></span> <span data-ttu-id="030d5-108">如果要執行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 功能探索報告，請按一下 [[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安裝中心] 左側導覽區域中的 [工具]，然後按一下 [已安裝的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 功能探索報告]。</span><span class="sxs-lookup"><span data-stu-id="030d5-108">To run the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] features discovery report, click **Tools** in the left-hand navigation area of **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Installation Center**, and then click **Installed [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] features discovery report**.</span></span>  
  
 <span data-ttu-id="030d5-109">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]探索報告已儲存至% ProgramFiles% \\ [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \120\Setup Bootstrap\Log \\<上一個安裝程式會話 \> 。</span><span class="sxs-lookup"><span data-stu-id="030d5-109">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] discovery report is saved to %ProgramFiles%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\120\Setup Bootstrap\Log\\<last Setup Session\>.</span></span>  
  
 <span data-ttu-id="030d5-110">您也可以從命令列產生探索報告。</span><span class="sxs-lookup"><span data-stu-id="030d5-110">You can also generate the discovery report through the command line.</span></span> <span data-ttu-id="030d5-111">從命令提示字元執行 "Setup.exe/Action = RunDiscovery"。如果您在上述命令列中新增 "/q"，則不會顯示 UI，但仍會在% ProgramFiles% \\ [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \120\Setup Bootstrap\Log \\<最後一個安裝程式會話 \> 中建立報表。</span><span class="sxs-lookup"><span data-stu-id="030d5-111">Run "Setup.exe /Action=RunDiscovery" from a command prompt If you add "/q" to the command line above no UI will be shown, but the report will still be created in %ProgramFiles%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\120\Setup Bootstrap\Log\\<last Setup Session\>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="030d5-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="030d5-112">See Also</span></span>  
 [<span data-ttu-id="030d5-113">檢視與讀取 SQL Server 安裝程式記錄檔</span><span class="sxs-lookup"><span data-stu-id="030d5-113">View and Read SQL Server Setup Log Files</span></span>](view-and-read-sql-server-setup-log-files.md)  
  
  
