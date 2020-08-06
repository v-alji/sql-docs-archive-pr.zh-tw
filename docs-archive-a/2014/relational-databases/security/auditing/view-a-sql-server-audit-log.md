---
title: 檢視 SQL Server Audit 記錄 | Microsoft 文件
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- audits [SQL Server], viewing logs
- viewing audit logs
- logs [SQL Server], audit
ms.assetid: e8feaca0-7852-422b-895a-319b965d8d9b
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 8f9902a4fc92ef0b35bae62eb80170762c52fdec
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592575"
---
# <a name="view-a-sql-server-audit-log"></a><span data-ttu-id="2ac73-102">檢視 SQL Server Audit 記錄</span><span class="sxs-lookup"><span data-stu-id="2ac73-102">View a SQL Server Audit Log</span></span>
  <span data-ttu-id="2ac73-103">本主題描述如何使用 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 登入 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]，以檢視 SQL Server 稽核記錄。</span><span class="sxs-lookup"><span data-stu-id="2ac73-103">This topic describes how to view a SQL Server audit log in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="2ac73-104">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="2ac73-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="2ac73-105">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="2ac73-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="2ac73-106">安全性</span><span class="sxs-lookup"><span data-stu-id="2ac73-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="2ac73-107">**若要使用下列項目檢視 SQL Server 稽核記錄：**</span><span class="sxs-lookup"><span data-stu-id="2ac73-107">**To view a SQL Server audit log, using:**</span></span>  
  
     [<span data-ttu-id="2ac73-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="2ac73-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="2ac73-109">開始之前</span><span class="sxs-lookup"><span data-stu-id="2ac73-109">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="2ac73-110">Security</span><span class="sxs-lookup"><span data-stu-id="2ac73-110">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="2ac73-111">權限</span><span class="sxs-lookup"><span data-stu-id="2ac73-111">Permissions</span></span>  
 <span data-ttu-id="2ac73-112">需要 `CONTROL SERVER` 權限。</span><span class="sxs-lookup"><span data-stu-id="2ac73-112">Requires the `CONTROL SERVER` permission.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="2ac73-113">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="2ac73-113">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-view-a-sql-server-audit-log"></a><span data-ttu-id="2ac73-114">若要檢視 SQL Server 稽核記錄</span><span class="sxs-lookup"><span data-stu-id="2ac73-114">To view a SQL Server audit log</span></span>  
  
1.  <span data-ttu-id="2ac73-115">在 [物件總管] 中，展開 **[安全性]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="2ac73-115">In Object Explorer, expand the **Security** folder.</span></span>  
  
2.  <span data-ttu-id="2ac73-116">展開 **[稽核]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="2ac73-116">Expand the **Audits** folder.</span></span>  
  
3.  <span data-ttu-id="2ac73-117">以滑鼠右鍵按一下您想要檢視的稽核記錄，然後選取 **[檢視稽核記錄]** 。</span><span class="sxs-lookup"><span data-stu-id="2ac73-117">Right-click the audit log that you want to view and select **View Audit Logs**.</span></span> <span data-ttu-id="2ac73-118">這會開啟 [**記錄檔檢視器-**_server_name_ ] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="2ac73-118">This opens the **Log File Viewer -**_server_name_ dialog box.</span></span> <span data-ttu-id="2ac73-119">如需詳細資訊，請參閱 [Log File Viewer F1 Help](../../logs/log-file-viewer-f1-help.md)。</span><span class="sxs-lookup"><span data-stu-id="2ac73-119">For more information, see [Log File Viewer F1 Help](../../logs/log-file-viewer-f1-help.md).</span></span>  
  
4.  <span data-ttu-id="2ac73-120">完成後，請按一下 **[關閉]** 。</span><span class="sxs-lookup"><span data-stu-id="2ac73-120">When finished, click **Close**.</span></span>  
  
 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] <span data-ttu-id="2ac73-121">建議使用記錄檔檢視器來檢視稽核記錄檔。</span><span class="sxs-lookup"><span data-stu-id="2ac73-121">recommends viewing the audit log by using the Log File Viewer.</span></span> <span data-ttu-id="2ac73-122">不過，如果您要建立自動化的監視系統，可以使用 [sys.fn_get_audit_file &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/sys-fn-get-audit-file-transact-sql) 函數直接讀取稽核檔案中的資訊。</span><span class="sxs-lookup"><span data-stu-id="2ac73-122">However, if you are creating an automated monitoring system, the information in the audit file can be read directly by using the [sys.fn_get_audit_file &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/sys-fn-get-audit-file-transact-sql) function.</span></span> <span data-ttu-id="2ac73-123">直接讀取檔案會傳回稍有不同的 (未處理的) 資料格式。</span><span class="sxs-lookup"><span data-stu-id="2ac73-123">Reading the file directly returns data in a slightly different (unprocessed) format.</span></span> <span data-ttu-id="2ac73-124">如需詳細資訊，請參閱**sys.databases fn_get_audit_file**</span><span class="sxs-lookup"><span data-stu-id="2ac73-124">See **sys.fn_get_audit_file** for more information</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ac73-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2ac73-125">See Also</span></span>  
 <span data-ttu-id="2ac73-126">[SQL Server Audit &#40;Database Engine&#41;](sql-server-audit-database-engine.md) </span><span class="sxs-lookup"><span data-stu-id="2ac73-126">[SQL Server Audit &#40;Database Engine&#41;](sql-server-audit-database-engine.md) </span></span>  
 [<span data-ttu-id="2ac73-127">將 SQL Server Audit 事件寫入安全性記錄檔</span><span class="sxs-lookup"><span data-stu-id="2ac73-127">Write SQL Server Audit Events to the Security Log</span></span>](write-sql-server-audit-events-to-the-security-log.md)  
  
  
