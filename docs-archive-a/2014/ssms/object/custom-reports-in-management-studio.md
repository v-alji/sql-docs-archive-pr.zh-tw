---
title: Management Studio 中的自訂報表 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.swb.summary.new.custom.report.f1
helpviewer_keywords:
- SQL Server Management Studio [SQL Server], custom reports
ms.assetid: 1ba3f758-f39b-4f5f-91ca-516cedc78979
author: stevestein
ms.author: sstein
ms.openlocfilehash: bc93157100738610c8576f0af40e75613c3cff62
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584259"
---
# <a name="custom-reports-in-management-studio"></a><span data-ttu-id="1aaee-102">Management Studio 中的自訂報表</span><span class="sxs-lookup"><span data-stu-id="1aaee-102">Custom Reports in Management Studio</span></span>
  <span data-ttu-id="1aaee-103">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中，許多物件總管節點會顯示一組由 [!INCLUDE[msCoName](../../includes/msconame-md.md)]建立的標準報表。</span><span class="sxs-lookup"><span data-stu-id="1aaee-103">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], many Object Explorer nodes display a set of standard reports that are created by [!INCLUDE[msCoName](../../includes/msconame-md.md)].</span></span> <span data-ttu-id="1aaee-104">這些報表會摘要列出經常要求的伺服器資訊。</span><span class="sxs-lookup"><span data-stu-id="1aaee-104">These reports summarize typically requested server information.</span></span> <span data-ttu-id="1aaee-105">從 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Service Pack 2 開始，管理員就可以從 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 執行在 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]中建立的自訂報表。</span><span class="sxs-lookup"><span data-stu-id="1aaee-105">Starting with [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Service Pack 2, administrators can run custom reports that were created in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] from [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].</span></span>  
  
## <a name="implementation"></a><span data-ttu-id="1aaee-106">實作</span><span class="sxs-lookup"><span data-stu-id="1aaee-106">Implementation</span></span>  
 <span data-ttu-id="1aaee-107">自訂報表會儲存成報表定義 (.rdl) 檔案，而且這些檔案是使用報表定義語言 (RDL) 所建立的。</span><span class="sxs-lookup"><span data-stu-id="1aaee-107">Custom reports are stored as report definition (.rdl) files and are created by using Report Definition Language (RDL).</span></span> <span data-ttu-id="1aaee-108">RDL 會包含 XML 格式之報表的資料擷取和配置資訊。</span><span class="sxs-lookup"><span data-stu-id="1aaee-108">RDL contains data retrieval and layout information for a report in an XML format.</span></span> <span data-ttu-id="1aaee-109">RDL 是一種開放式結構描述。</span><span class="sxs-lookup"><span data-stu-id="1aaee-109">RDL is an open schema.</span></span> <span data-ttu-id="1aaee-110">開發人員可以使用其他屬性和元素來擴充 RDL。</span><span class="sxs-lookup"><span data-stu-id="1aaee-110">Developers can extend RDL with additional attributes and elements.</span></span> <span data-ttu-id="1aaee-111">報表可以執行報表內的任何有效 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式。</span><span class="sxs-lookup"><span data-stu-id="1aaee-111">Reports can execute any valid [!INCLUDE[tsql](../../includes/tsql-md.md)] statement within the report.</span></span>  
  
 <span data-ttu-id="1aaee-112">如果 [物件總管] 連接至某部伺服器，而且自訂報表參考該節點的報表參數，則這些報表就可以在目前 [物件總管] 選取範圍的內容中執行。</span><span class="sxs-lookup"><span data-stu-id="1aaee-112">If Object Explorer is connected to a server, custom reports can execute in the context of the current Object Explorer selection if the reports reference report parameters of that node.</span></span> <span data-ttu-id="1aaee-113">這可讓報表使用目前的內容 (例如目前的資料庫) 或一致的內容 (例如將指派的資料庫指定為包含在自訂報表中之 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式的一部分)。</span><span class="sxs-lookup"><span data-stu-id="1aaee-113">This enables a report to use the current context, such as the current database; or a consistent context, such as specifying a designated database as part of the [!INCLUDE[tsql](../../includes/tsql-md.md)] statement that is contained in the custom report.</span></span>  
  
## <a name="running-a-custom-report"></a><span data-ttu-id="1aaee-114">執行自訂報表</span><span class="sxs-lookup"><span data-stu-id="1aaee-114">Running a Custom Report</span></span>  
 <span data-ttu-id="1aaee-115">您可以利用下列方式在 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 中執行自訂報表：</span><span class="sxs-lookup"><span data-stu-id="1aaee-115">You can run a custom report in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] in the following ways:</span></span>  
  
-   <span data-ttu-id="1aaee-116">以滑鼠右鍵按一下物件總管中的節點、指向 [報表]  ，然後以滑鼠左鍵按一下 [自訂報表]  。</span><span class="sxs-lookup"><span data-stu-id="1aaee-116">Right-click a node in Object Explorer, point to **Reports** and left-click **Custom Reports**.</span></span> <span data-ttu-id="1aaee-117">在 [開啟檔案]  對話方塊中，找出包含 .rdl 檔的資料夾，然後開啟適當的報表檔案。</span><span class="sxs-lookup"><span data-stu-id="1aaee-117">In the **Open File** dialog box, locate a folder that contains .rdl files, and then open the appropriate report file.</span></span>  
  
-   <span data-ttu-id="1aaee-118">以滑鼠右鍵按一下物件總管中的節點、指向 [報表]  、指向 [自訂報表]  ，然後從最近使用過的檔案清單中選取自訂報表。</span><span class="sxs-lookup"><span data-stu-id="1aaee-118">Right-click a node in Object Explorer, point to **Reports**, point to **Custom Reports**, and then select a custom report from the most recently used file list.</span></span>  
  
## <a name="limitations"></a><span data-ttu-id="1aaee-119">限制</span><span class="sxs-lookup"><span data-stu-id="1aaee-119">Limitations</span></span>  
 <span data-ttu-id="1aaee-120">當您使用自訂報表時，請考量下列限制：</span><span class="sxs-lookup"><span data-stu-id="1aaee-120">When you work with custom reports, consider the following limitations:</span></span>  
  
-   <span data-ttu-id="1aaee-121">為了防止意外執行惡意程式碼， [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 無法設定為自動執行報表，即使檔案系統設定為將 .rdl 檔與 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]產生關聯也一樣。</span><span class="sxs-lookup"><span data-stu-id="1aaee-121">To prevent the unintended execution of malicious code, [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] cannot be configured to automatically run a report, even if the file system is configured to associate .rdl files with [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].</span></span> <span data-ttu-id="1aaee-122">報表無法以程式設計方式在 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 中執行，而且無法透過 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]從命令列執行。</span><span class="sxs-lookup"><span data-stu-id="1aaee-122">Reports cannot be programmatically executed in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] and cannot run from the command line through [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].</span></span>  
  
-   <span data-ttu-id="1aaee-123">您可以在未產生預期值的內容中執行自訂報表。</span><span class="sxs-lookup"><span data-stu-id="1aaee-123">You can run custom reports in a context that does not produce the expected values.</span></span> <span data-ttu-id="1aaee-124">例如，您可以在未涉及複寫的資料庫內容中執行有關複寫的報表，也可以用無權存取產生正確報表所需之資訊的使用者身分來執行報表。</span><span class="sxs-lookup"><span data-stu-id="1aaee-124">For example, you can run a report about replication in the context of a database that is not involved in replication, or run a report as a user who does not have permission to access information that is required to generate an accurate report.</span></span> <span data-ttu-id="1aaee-125">自訂報表的建立者會負責報表結構及其內容的有效性。</span><span class="sxs-lookup"><span data-stu-id="1aaee-125">The creator of the custom report is responsible for the validity of the report structure and its context.</span></span>  
  
-   <span data-ttu-id="1aaee-126">您無法將自訂報表加入至標準報表的清單。</span><span class="sxs-lookup"><span data-stu-id="1aaee-126">You cannot add a custom report to the list of standard reports.</span></span>  
  
-   <span data-ttu-id="1aaee-127">報表所處理的程式碼可能會影響伺服器效能。</span><span class="sxs-lookup"><span data-stu-id="1aaee-127">The code processed by the report might affect server performance.</span></span>  
  
-   <span data-ttu-id="1aaee-128">自訂報表將無法支援子報表。</span><span class="sxs-lookup"><span data-stu-id="1aaee-128">Custom reports will not support subreports.</span></span>  
  
-   <span data-ttu-id="1aaee-129">報表中每個查詢的命令文字都不得透過運算式定義。</span><span class="sxs-lookup"><span data-stu-id="1aaee-129">The command text for each query within the report must not be defined through an expression.</span></span>  
  
-   <span data-ttu-id="1aaee-130">命令 (查詢) 中所使用的任何查詢參數只能參考單一報表參數，而無法使用任何運算式運算子。</span><span class="sxs-lookup"><span data-stu-id="1aaee-130">Any query parameter that is used in a command (query) can only reference a single report parameter and cannot use any expression operators.</span></span>  
  
-   <span data-ttu-id="1aaee-131">報表命令 (查詢) 只支援「文字」和「預存程序」命令類型。</span><span class="sxs-lookup"><span data-stu-id="1aaee-131">Only Text and Stored Procedure command types are supported for report commands (queries).</span></span>  
  
-   <span data-ttu-id="1aaee-132">報表架構不會提供任何逸出參數給查詢。</span><span class="sxs-lookup"><span data-stu-id="1aaee-132">The report framework does not provide any parameter escaping for the queries.</span></span> <span data-ttu-id="1aaee-133">查詢作者必須確定其查詢不會遭受 SQL 資料隱碼攻擊。</span><span class="sxs-lookup"><span data-stu-id="1aaee-133">Query authors must make sure that their queries are free from SQL injection attacks.</span></span>  
  
## <a name="managing-custom-reports"></a><span data-ttu-id="1aaee-134">管理自訂報表</span><span class="sxs-lookup"><span data-stu-id="1aaee-134">Managing Custom Reports</span></span>  
 <span data-ttu-id="1aaee-135">我們建議擁有許多自訂報表的使用者，最好使用具有適當 NTFS 檔案系統權限的檔案系統資料夾來組織這些報表。</span><span class="sxs-lookup"><span data-stu-id="1aaee-135">We recommend that users who have many custom reports organize them by using file system folders that have appropriate NTFS file system permissions.</span></span>  
  
## <a name="permissions"></a><span data-ttu-id="1aaee-136">權限</span><span class="sxs-lookup"><span data-stu-id="1aaee-136">Permissions</span></span>  
 <span data-ttu-id="1aaee-137">自訂報表會使用目前使用者的權限來執行。</span><span class="sxs-lookup"><span data-stu-id="1aaee-137">Custom reports run by using the permissions of the current user.</span></span> <span data-ttu-id="1aaee-138">若要防止惡意使用者變更報表所執行的查詢，包含報表檔案之檔案系統資料夾的權限應該要設定為限制存取。</span><span class="sxs-lookup"><span data-stu-id="1aaee-138">To prevent a malicious user from changing the queries run by the report, permissions on the file system folder that contains the report files should be set to restrict access.</span></span>  
  
 <span data-ttu-id="1aaee-139">使用者以及 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服務所使用的帳戶，都需要包含報表檔案之檔案系統資料夾的讀取權。</span><span class="sxs-lookup"><span data-stu-id="1aaee-139">Both the user and the account that is used by the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service require read access to the file system folder that contains the report files.</span></span>  
  
 <span data-ttu-id="1aaee-140">雖然您可以在報表中內嵌任何有效的 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 命令，但是此命令將不會執行。</span><span class="sxs-lookup"><span data-stu-id="1aaee-140">Any valid [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] command can be embedded in a report, but the command will not be executed.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="1aaee-141">您可以報表中內嵌任何有效 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式，然後從報表中執行。</span><span class="sxs-lookup"><span data-stu-id="1aaee-141">Any valid [!INCLUDE[tsql](../../includes/tsql-md.md)] statement can be embedded in and executed from a report.</span></span> <span data-ttu-id="1aaee-142">在高權限使用者帳戶底下執行報表可讓任何內嵌的指示執行，而不會受到挑戰。</span><span class="sxs-lookup"><span data-stu-id="1aaee-142">Running a report under a high-privileged user account makes it possible for any of these embedded instructions to execute without challenge.</span></span>  
  

  
## <a name="see-also"></a><span data-ttu-id="1aaee-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1aaee-143">See Also</span></span>  
 <span data-ttu-id="1aaee-144">[將自訂報表加入至 Management Studio](add-a-custom-report-to-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="1aaee-144">[Add a Custom Report to Management Studio](add-a-custom-report-to-management-studio.md) </span></span>  
 <span data-ttu-id="1aaee-145">[取消隱藏執行自訂報表警告](unsuppress-run-custom-report-warnings.md) </span><span class="sxs-lookup"><span data-stu-id="1aaee-145">[Unsuppress Run Custom Report Warnings](unsuppress-run-custom-report-warnings.md) </span></span>  
 [<span data-ttu-id="1aaee-146">使用自訂報表搭配物件總管節點屬性</span><span class="sxs-lookup"><span data-stu-id="1aaee-146">Use Custom Reports with Object Explorer Node Properties</span></span>](use-custom-reports-with-object-explorer-node-properties.md)  
  
  
