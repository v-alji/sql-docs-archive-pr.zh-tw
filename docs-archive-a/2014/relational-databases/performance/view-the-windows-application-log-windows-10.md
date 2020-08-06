---
title: 檢視 Windows 應用程式記錄檔 (Windows 10) | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- viewing logs
- application logs [SQL Server]
- logs [SQL Server], application
- monitoring Windows NT application log [SQL Server]
- Windows NT application logs [SQL Server]
- displaying logs
- monitoring [SQL Server], events
- logs [SQL Server], viewing
ms.assetid: 168a6c6e-12df-46a9-9904-55d63ca8fe14
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 1255e95833d9fc56abd1700f5acb0d2f49ebf77c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87699511"
---
# <a name="view-the-windows-application-log-windows"></a><span data-ttu-id="fcf97-102">檢視 Windows 應用程式記錄檔 (Windows)</span><span class="sxs-lookup"><span data-stu-id="fcf97-102">View the Windows Application Log (Windows)</span></span>
  <span data-ttu-id="fcf97-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 設定為使用 Windows 應用程式記錄檔時，每個 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 工作階段都會將新事件寫入該記錄檔。</span><span class="sxs-lookup"><span data-stu-id="fcf97-103">When [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is configured to use the Windows application log, each [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] session writes new events to that log.</span></span> <span data-ttu-id="fcf97-104">您每次啟動 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的執行個體時，並不會建立新的應用程式記錄檔，這和 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]錯誤記錄檔不同。</span><span class="sxs-lookup"><span data-stu-id="fcf97-104">Unlike the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log, a new application log is not created each time you start an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
### <a name="to-view-the-windows-application-log"></a><span data-ttu-id="fcf97-105">若要檢視 Windows 應用程式記錄檔</span><span class="sxs-lookup"><span data-stu-id="fcf97-105">To view the Windows application log</span></span>  
  
1.  <span data-ttu-id="fcf97-106">在 **[開始]** 功能表上，指向 **[所有程式]**，再指向 **[系統管理工具]**，然後按一下 **[事件檢視器]**。</span><span class="sxs-lookup"><span data-stu-id="fcf97-106">On the **Start** menu, point to **All Programs**, point to **Administrative Tools**, and then click **Event Viewer**.</span></span>  
  
2.  <span data-ttu-id="fcf97-107">在 [事件檢視器] 中，按一下 **[應用程式]**。</span><span class="sxs-lookup"><span data-stu-id="fcf97-107">In Event Viewer, click **Application**.</span></span>  
  
3.  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="fcf97-108">事件是以 [來源] 資料行的 **MSSQLSERVER** 項目識別 (具名執行個體則是以 **MSSQL$** _<執行個體名稱>_ 識別)。</span><span class="sxs-lookup"><span data-stu-id="fcf97-108">events are identified by the entry **MSSQLSERVER** (named instances are identified with **MSSQL$**_<instance_name>_) in the **Source** column.</span></span> <span data-ttu-id="fcf97-109">SQL Server Agent 事件是由 SQLSERVERAGENT 項目所識別 (對於 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的具名執行個體，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 事件是由 **SQLAgent$** \<*instance_name*> 加以識別)。</span><span class="sxs-lookup"><span data-stu-id="fcf97-109">SQL Server Agent events are identified by the entry SQLSERVERAGENT (for named instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent events are identified with **SQLAgent$**\<*instance_name*>).</span></span> <span data-ttu-id="fcf97-110">Microsoft Search 服務事件則以 **Microsoft Search**項目識別。</span><span class="sxs-lookup"><span data-stu-id="fcf97-110">Microsoft Search service events are identified by the entry **Microsoft Search**.</span></span>  
  
4.  <span data-ttu-id="fcf97-111">若要檢視不同電腦的記錄檔，請以滑鼠右鍵按一下 [事件檢視器]\*\*\*\*，按一下 [連線到另一台電腦]\*\*\*\*，然後完成 [選取電腦]\*\*\*\* 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="fcf97-111">To view the log of a different computer, right-click **Event Viewer**, click **Connect to another computer,** and complete the **Select Computer**dialog box.</span></span>  
  
5.  <span data-ttu-id="fcf97-112">(選擇性) 若只想顯示 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 事件，請在 **[檢視]** 功能表中按一下 **[篩選]**，然後在 **[事件來源]** 清單中選擇 **[MSSQLSERVER]**。</span><span class="sxs-lookup"><span data-stu-id="fcf97-112">Optionally, to display only [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] events, on the **View** menu click **Filter**, and in the **Event source** list, select **MSSQLSERVER**.</span></span> <span data-ttu-id="fcf97-113">若只想檢視 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 事件，請改在 **[事件來源]** 清單中選取 **[SQLSERVERAGENT]** 。</span><span class="sxs-lookup"><span data-stu-id="fcf97-113">To view only [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent events, instead select **SQLSERVERAGENT** in the **Event source** list.</span></span>  
  
6.  <span data-ttu-id="fcf97-114">若要檢視事件的詳細資訊，請按兩下該事件。</span><span class="sxs-lookup"><span data-stu-id="fcf97-114">To view more information about an event, double-click the event.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fcf97-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fcf97-115">See Also</span></span>  
 [<span data-ttu-id="fcf97-116">檢視 SQL Server 錯誤記錄檔 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="fcf97-116">View the SQL Server Error Log &#40;SQL Server Management Studio&#41;</span></span>](../../ssms/sql-server-management-studio-ssms.md)  
  
  
