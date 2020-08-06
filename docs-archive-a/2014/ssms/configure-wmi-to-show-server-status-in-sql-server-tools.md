---
title: 設定 WMI 以在 SQL Server 工具中顯示伺服器狀態 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- WMI Provider for Server Events, setting permissions
- WMI permissions [SQL Server]
ms.assetid: 7e97197b-ed4d-40d1-9a52-9ab1d92401d7
author: stevestein
ms.author: sstein
ms.openlocfilehash: 138abbe2b7b819d6afd6da62135f7cd7ce86496f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705857"
---
# <a name="configure-wmi-to-show-server-status-in-sql-server-tools"></a><span data-ttu-id="96441-102">設定 WMI 在 SQL Server 工具中顯示伺服器狀態</span><span class="sxs-lookup"><span data-stu-id="96441-102">Configure WMI to Show Server Status in SQL Server Tools</span></span>
  <span data-ttu-id="96441-103">此主題描述如何在 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]中設定 WMI，以在 SQL Server 工具中顯示伺服器狀態。</span><span class="sxs-lookup"><span data-stu-id="96441-103">This topic describes how to configure WMI to show the server status in SQL Server tools in [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="96441-104">連接到伺服器時， [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]的 [已註冊的伺服器] 和 [物件總管] 元件，以及「 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 組態管理員」，都會使用 Windows Management Instrumentation (WMI) 來取得 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] (MSSQLSERVER) 及 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent (MSSQLSERVER) 服務的狀態。</span><span class="sxs-lookup"><span data-stu-id="96441-104">When connecting to servers, both the Registered Servers and Object Explorer components of [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], as well as [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Configuration Manager, use Windows Management Instrumentation (WMI) to obtain the status of the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] (MSSQLSERVER) and [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent (MSSQLSERVER) services.</span></span> <span data-ttu-id="96441-105">若要顯示這些服務的狀態，使用者必須具有從遠端存取 WMI 物件的權限。</span><span class="sxs-lookup"><span data-stu-id="96441-105">To display the status of the service, the user must have rights to remotely access the WMI object.</span></span> <span data-ttu-id="96441-106">伺服器必須安裝 WMI，才能設定此權限。</span><span class="sxs-lookup"><span data-stu-id="96441-106">The server must have WMI installed to configure this permission.</span></span>  
  
##  <a name="to-configure-wmi-permission"></a><a name="SSMSProcedure"></a><span data-ttu-id="96441-107">設定 WMI 許可權</span><span class="sxs-lookup"><span data-stu-id="96441-107">To configure WMI permission</span></span>  
  
1.  <span data-ttu-id="96441-108">在遠端伺服器的 [開始]  功能表上按一下 [執行]  。</span><span class="sxs-lookup"><span data-stu-id="96441-108">On the **Start** menu on the remote server, click **Run**.</span></span>  
  
2.  <span data-ttu-id="96441-109">在 [**開啟**] 方塊中 `wmimgmt.msc` ，輸入，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="96441-109">In the **Open** box type `wmimgmt.msc`, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="96441-110">在 **Windows Management Infrastructure** 程式中，以滑鼠右鍵按一下 [WMI 控制 (本機)]  ，然後按一下[內容]  。</span><span class="sxs-lookup"><span data-stu-id="96441-110">In the **Windows Management Infrastructure** program, right-click **WMI Control (Local)**, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="96441-111">在 [WMI 控制 (本機) 內容]  對話方塊的 [安全性]  索引標籤上，展開 [Root]  ，然後按一下 [CIMV2]  。</span><span class="sxs-lookup"><span data-stu-id="96441-111">In the **WMI Control (Local) Properties** dialog box, on the **Security** tab, expand **Root**, and then click **CIMV2**.</span></span>  
  
5.  <span data-ttu-id="96441-112">按一下 [安全性]  以開啟 [安全性 ROOT\CIMV2]  對話方塊。</span><span class="sxs-lookup"><span data-stu-id="96441-112">Click **Security** to open the **Security for ROOT\CIMV2** dialog box.</span></span>  
  
6.  <span data-ttu-id="96441-113">新增群組或使用者至 [群組或使用者名稱]  方塊，然後選取此新增項目。</span><span class="sxs-lookup"><span data-stu-id="96441-113">Add a group or user to the **Group or user names** box and select it.</span></span>  
  
7.  <span data-ttu-id="96441-114">在 [_\<group or user>_ 的權限] 方塊中，針對想要遠端偵測其服務狀態的使用者，選取 [遠端啟用] 權限的 [允許] 資料行。</span><span class="sxs-lookup"><span data-stu-id="96441-114">In the **Permissions for**_\<group or user>_ box, select the **Allow** column, for the **Remote Enable** permission, for users whom you wish to remotely detect the service status.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96441-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="96441-115">See Also</span></span>  
 [<span data-ttu-id="96441-116">啟動、停止或暫停 SQL Server Agent 服務</span><span class="sxs-lookup"><span data-stu-id="96441-116">Start, Stop, or Pause the SQL Server Agent Service</span></span>](agent/start-stop-or-pause-the-sql-server-agent-service.md)  
  
  
